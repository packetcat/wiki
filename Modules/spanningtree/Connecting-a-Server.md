# InspIRCd Wiki &raquo; Modules &raquo; m_spanningtree &raquo; Connecting a Server

To connect to a server we first proceed with the authentication phase, as detailed in the section
below.

## The Authentication Phase

During the authentication phase, a three-way handshake is performed where both servers exchange
their passwords. Unlike most IRC servers, the notable exception being ircu, this must be done in
lock-step fashion, e.g. one server sends a request then waits for the other server to reply before
sending another. Note that once the authentication phase is complete, the data flow moves to being
full duplex and no such restrictions apply once the `BURST` command is received.

### Step One - Connection

Server A, wishing to connect to the network, connects to a TCP port which server B is listening on.
When the connection is established, it immediately sends the `CAPAB` and `SERVER` commands to server
B which is waiting for inbound traffic. Up until this point, server B will do nothing but accept the
connection and reply with its `CAPAB`.

#### Transport-Layer Handshakes

If there are any transport modules attached to the connection, such as GnuTLS, then this is the
point where they perform their handshakes. The server should wait before sending anything to ensure
the handshake has completed. The details of what is sent at the transport layer are dependent upon
the module, and outside the scope of this page.

### Step Two - Inbound Authentication

Server B, after receiving server A's `SERVER` command, analyzes the parameters (namely server name
and password) and if it is not happy with the credentials, should instantly send a suitable `ERROR`
reply, and close its connection. However, if server B deems the credentials correct for server A,
server B then sends its own SERVER command, with its own credentials in to authenticate to server A.

### Step Three - Outbound Authentication

Server A, upon receiving server B's credentials, analyzes them (again, namely the server name and
password), and again, if it is not happy, it can send an `ERROR` reply, and close its connection. If
the details are correct however, server A now sends a `BURST` command (see the commands list below)
and begins its network burst.

### Step Four - Network Burst

Upon receiving server A's network burst, server B also sends its own network burst, preceded again
by the `BURST` command. When both servers have finished bursting, they send the `ENDBURST` command.
`BURST` and `ENDBURST` are sent both for local, and for remote bursts. In the case of remote bursts,
the `BURST` and `ENDBURST` command must be correctly prefixed with the server ID they originate
from.

The order which data is sent during the burst is important, and must be:

1. The names of any servers connected to this one, directly or otherwise, with relative hop counts,
   1 being a direct connection (these will be re-calculated by the receiving side). The server names
   should be introduced using recursion or similar so that each server only appears after its parent
   server in the list.

2. The nicknames of any users, sent using `UID`, their `OPERTYPE` if they are an oper.

3. The membership and privileges of all channels using `FJOIN` (see the commands list) and the modes
   (sent using `FMODE`), topics (sent using `FTOPIC`) and bans (again, sent using `FMODE`) for each
   channel in turn (no specific order of channels).

4. Any module specific data (which may be a combination of FMODE and any other module-specific
   commands).

### Example Authentication Phase

This is an example of a successful authentication using plaintext password authentication:

```
>> SERVER services-dev.chatspike.net password 0 666 :Description here
<< SERVER test.chatspike.net password 0 491 :ChatSpike InspIRCd test server
>> :066 BURST 1176144272
<< :491 BURST 1176144273
```

Both servers now operate in duplex mode sending data freely

### Challenge-Response and HMAC authentication

InspIRCd also supports challenge-response HMAC authentication for server passwords. This ensures
that the password itself is never transmitted in any usable form across the server link.

To facilitate this in a backwards compatible manner, the challenge string is placed into the `CAPAB
CAPABILITIES` line of the servers which support it and have it enabled. The CHALLENGE string should
be sufficiently random to prevent brute-forcing and mathematical attacks against it. The current
InspIRCd implementation collects entropy from /dev/urandom.

A challenge should never be sent to the other server if:

1. HMAC is disabled
2. The m_sha256 module, required for the cryptographic hash, is not loaded

Here is an example of a HMAC enabled authentication phase, which is described in greater detail
below the example:

```
-> CAPAB START
-> CAPAB MODULES m_alltime.so,m_banexception.so,m_blockcaps.so,m_blockcolor.so,m_botmode.so,m_censor.so
-> CAPAB CAPABILITIES :NICKMAX=32 HALFOP=1 CHANMAX=65 MAXMODES=20 IDENTMAX=12 MAXQUIT=255 PROTOCOL=1105 CHALLENGE=egykq)9ae)ms#se?;gi%
-> CAPAB END
<- CAPAB START
<- CAPAB MODULES m_alltime.so,m_banexception.so,m_blockcaps.so,m_blockcolor.so,m_botmode.so,m_censor.so
<- CAPAB CAPABILITIES :NICKMAX=32 HALFOP=1 CHANMAX=65 MAXMODES=20 IDENTMAX=12 MAXQUIT=255 PROTOCOL=1105 CHALLENGE=yyks7-#c5kwuaqyi-e19
<- CAPAB END
-> SERVER test2.chatspike.net HMAC-SHA256:185ea67956256a3703bae0cb9324a655180f5b7089224539e08cf1003b296f9c 0 666 :Test server
<- SERVER test.chatspike.net HMAC-SHA256:76a7d469c3dcab86067495d1b3407720fce9f7286400835baa2972e75e891a65 0 491 :"Bollocks" Said pooh, as he caught his testicles in the vice.
-> :666 BURST 1176144272
<- :491 BURST 1176144273
```

When authenticating via HMAC, both sides of the connection should wait for the complete `CAPAB`
information before sending their SERVER line. This is to allow for both sides to send their
challenge, which is encapsulated in the `CAPAB CAPABILITIES` as shown above.

#### HMAC implementation details

The challenge string is hashed against the password using a simple HMAC algorithm, as shown below,
before being sent back to the other side in the password section:

`sha256( (p xor 0x5C) + sha256((p xor 0x36) + m) )`

Where 'm' is the challenge string given in the other side's CAPAB, and 'p' is the password you wish
to send. Each character of 'p' should be exclusive-or'ed against 0x5C or 0x36, and in the above
equation, + indicates string concatenation, not integer addition.

Due to limitations inherent in the protocol and CAPAB notation, the equals (=) symbol may not form
part of the CHALLENGE value. Any equals symbols should be translated to non-equals, in the current
implementation, they are translated to an underscore (_).

IMPORTANT NOTE: In the current implementation, the SHA256 output is ASCII text, e.g. the hexadecimal
hash value and not raw binary data.

When the server replies with its calculated HMAC, it should prepend the value "HMAC-SHA256:" to the
hash. This is to distinguish it from a plaintext password, and allow servers which do not support
HMAC, such as services and past versions of InspIRCd, to link correctly.

When checking the HMAC against what is expected, the checking server should fall back to plaintext
authentication if:

1. The sender has not sent a HMAC password
2. We never sent or received a CHALLENGE
3. HMAC is disabled
4. The m_sha256 module, required for the cryptographic hash, is not loaded
