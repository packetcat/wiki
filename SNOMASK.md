# InspIRCd Wiki &raquo; SNOMASKs

## Configuring SNOMASKs

To set SNOMASKs, set user mode +s with the server notice masks you want as a parameter to the mode.
For example, to see local and remote connections and quit notices, execute the following command:

`/MODE YourNick +s +cCqQ`

To enable automatic setting of SNOMASKs upon opering, load [m_opermodes](https://github.com/inspircd/wiki/blob/master/Modules/opermodes.md)
and set the modes in `<type:automodes>`. For example:

```XML
<type name="GlobalOp" 
  classes="OperChat BanControl HostCloak Modular" 
  host="globalop.chatspike.net" 
  automodes="+s +cCqQ">
```

To remove a SNOMASK, set user mode +s again, but remove masks by sending a 'negative' change. For
example, to disable remote connection and quit notices, execute the following command:

`/MODE YourNick +s -CQ`

To disable all server notice masks, simply remove user mode +s entirely:

`/MODE YourNick -s`

A list of the valid server notice masks and what they do is listed below. 

## Channel Logging

You can use the [m_chanlog](https://github.com/inspircd/wiki/blob/master/Modules/chanlog.md) module
to send messages to a channel of your choice. You can even have multiple channels for different
masks. Use local masks on every server to the same channel to receive messages globally in the
channel.

## Valid Server Notice Masks

### Core Server Notice Masks

These are the server notice masks implemented by the core. Modules (table #2) may implement extra
notice masks.


SNOTICE Mask | Version | Function
------------ | ------- | --------
a            | 1.2+    | Allows receipt of local announcement messages
A            | 1.2+    | Allows receipt of global announcement messages
c            | 1.2+    | Allows receipt of local connection messages
C            | 1.2+    | Allows receipt of remote connection messages
d            | 1.2+    | Allows receipt of general and sometimes random debug messages
f            | 1.2+    | Allows receipt of flooding notices
k            | 1.2+    | Allows receipt of local kill messages
K            | 1.2+    | Allows receipt of remote kill messages
l            | 1.2+    | Allows receipt of local linking related messages
L            | 1.2+    | Allows receipt of remote linking related messages
o            | 1.2+    | Allows receipt of local oper up, oper down, and oper failure messages
O            | 1.2+    | Allows receipt of remote oper up, oper down, and oper failure messages
q            | 1.2+    | Allows receipt of local quit messages
Q            | 1.2+    | Allows receipt of remote quit messages
t            | 1.2+    | Allows receipt of attempts to use /STATS (local and remote)
x            | 1.2+    | Allows receipt of XLine notices (E/G/K/Q/Z as well as those provided by modules)
x            | 2.0+    | Allows receipt of local XLine notices (E/G/K/Q/Z as well as those provided by modules)
X            | 2.0+    | Allows receipt of remote XLine notices (E/G/K/Q/Z as well as those provided by modules)

### Module Server Notice Masks

SNOTICE Mask | Version | Module       | Function
------------ | ------- | ------------ | -------- 
g            | 1.2+    | m_globops    | Allows receipt of local globops
G            | 1.2     | m_glopops    | Allows receipt of remote globops
G            | 2.0+    | m_override   | Allows receipt of use of oper override
J            | 1.2+    | m_chancreate | Allows receipt of remote channel creation notices
j            | 1.2     | m_chancreate | Allows receipt of local channel creation notices
n            | 1.2+    | m_seenicks   | See local nickname changes
N            | 1.2+    | m_seenicks   | See remote nickname changes
v            | 2.0+    | m_override   | Allows receipt of use of oper override