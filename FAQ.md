Frequently Asked Questions
--------------------------

Why should I choose InspIRCd over some other IRC server?
--------------------------------------------------------

There are several reasons to choose InspIRCd over some other IRC server. These are:

* InspIRCd is totally modular -- add and remove features as YOU please, not as we tell you to. This
modular design also allows you to upgrade most parts (including but not limited to core commands,
server linking and SSL support) without rebooting the IRC server.

* InspIRCd offers its own free (as in beer *and* freedom) implementation of many features which
developers of certain other IRC servers want to charge you for.

* InspIRCd has a highly scalable ''non-blocking'' SQL API, supporting, MySQL, PostgreSQL, SQL
Server and SQLite -- unseen in any other IRC server.

* InspIRCd has high-performance socket engines such as epoll and kqueue, whereas other IRC servers
with the same feature set do not. We also have some socket engines that no other IRC server has
currently, such as Windows I/O Completion Ports, which increases the performance of our Windows
builds beyond most other Windows IRC servers.

* The InspIRCd development team welcome third party contributions, suggestions and criticism whereas
many of the developers of alternative IRC servers do not.

How much memory does InspIRCd use?
----------------------------------

A network with 3000-4000 locally connected clients and 10000 open channels experiences a constant
1-4% CPU use with 70MB of RAM use. This won't go up drastically, but it will go up. Around 40000
local clients means you'll be expecting some 500MB of RAM.

How do I start InspIRCd?
------------------------

Navigate to the directory in which you installed InspIRCd and issue the following command:

    ./inspircd start

Note: these instructions only apply if you installed InspIRCd from source on a UNIX-like operating
system. If you installed InspIRCd from a package manager it will probably not use this method.

Can my network be the "official" InspIRCd network?
--------------------------------------------------

Sorry, no. That privilege is reserved for our own network at [irc.chatspike.net](irc://irc.chatspike.net/).

What services package should I choose?
--------------------------------------

This is an extremely subjective question. It is advised that you trial multiple different packages
and use the one that you feel fits your needs.

Popular IRC services packages used with InspIRCd include:

* [Anope](http://www.anope.org/)
* [Atheme](http://www.atheme.net/)

Use of [IRCServices](http://achurch.org/services/) is not recommended due to it being unsupported.

Where should I report a bug/suggest a feature?
----------------------------------------------

On the appropriate issue tracker:

* [Main](https://github.com/inspircd/inspircd/issues)
* [Extras](https://github.com/inspircd/inspircd-extras/issues)
* [Website](https://github.com/inspircd/inspircd.github.com/issues)
* [Wiki](https://github.com/inspircd/wiki/issues)

How can I contribute to InspIRCd?
---------------------------------

Take a look at our [Contributing](https://github.com/inspircd/wiki/blob/master/Contributing.md)
page.

Can I use InspIRCd on my large network?
---------------------------------------

Feel free! We have tested InspIRCd up to 80000 clients on a single server. If you have any
statistics on performance you would like to share, then get in touch.

Do any large networks use InspIRCd?
-----------------------------------

To our knowledge, the largest networks using InspIRCd are:

* [IrCQ-Net](irc://irc.icq.com/) with 4000-6000 users
* [Barafranca](irc://irc.barafranca.com/) with 1400-3500 users
* [Chatspike](irc://irc.chatspike.net) with 600-1400 users

Which socket engines are supported by InspIRCd?
-----------------------------------------------

The following high performance socket engines are supported:

* **select** on all operating systems
* **poll** on all UNIX-like operating systems
* **kqueue** on BSD and Mac OS X
* **epoll** on Linux.
* **iocp** on Windows

Please note that the performance improvements given by use of kqueue, iocp or epoll are very large
performance gains over select(), and should be used wherever they are available. If you do not have
any of these socket engines, you should seriously consider upgrading your operating system or kernel
before running an IRC server.

What IRCd is InspIRCd based on?
-------------------------------

None. Yes that's right, None. We didn't start from anyone else's code, at all. It is not based on
Unreal, it is not based on Bahamut, nor is it based on any other IRCd. This is what makes it unique.

Can I run InspIRCd as root?
---------------------------

You could run the InspIRCd binary with the --runasroot parameter, but we will not provide any
support for doing this. If you want to bind InspIRCd to a privileged port, you should instead
use a port forwarding rule in your firewall. For example, if you are using Linux with iptables:

    iptables -t nat -A PREROUTING -p tcp -i eth0 -d 127.0.0.1 --dport 194 -j DNAT --to 127.0.0.1:6667
    iptables -A FORWARD -p tcp -i eth0 -d 127.0.0.1 --dport 194 -j ACCEPT

This will forward all traffic on port 194 to port 6667, on the IP 127.0.0.1. You should change this
IP and port numbers as appropriate.

If you are running Linux, another solution is to enable [file system capabilities](http://www.friedhoff.org/fscaps.html)
in your kernel, which allows you to grant specific privileges (e.g. the ability to bind to ports
under 1024) to any process without having to run it as root.

On FreeBSD and similar systems, there is a sysctl OID for this, which you can set:

    net.inet.ip.portrange.reservedlow=1
    net.inet.ip.portrange.reservedhigh=1

This will allow non-root processes to bind any ports which are above port 1, essentially all
available port numbers.

How do I run InspIRCd when the system starts?
---------------------------------------------

To launch InspIRCd when your system starts, you should place the following line into the crontab for
your IRCd user (crontab -e):

    @reboot cd /home/user/inspircd; ./inspircd start

How do I get prefixes like `@`, `~` and `&`?
-------------------------------------------

If you are using InspIRCd 1.2, load [m_customprefix](https://github.com/inspircd/wiki/blob/master/Modules/customprefix.md).

If you are using InspIRCd 2.0 or newer, load [m_halfop](https://github.com/inspircd/wiki/blob/master/Modules/halfop.md)
and [m_chanprotect](https://github.com/inspircd/wiki/blob/master/Modules/halfop.md).

Why does my server have none of the advertised features?
--------------------------------------------------------

By default, InspIRCd only supports features specified in [RFC 1459](http://tools.ietf.org/html/rfc1459).
If you want to add extra features then you must load the correct modules. A list of modules can be
found in `docs/inspircd.conf.example`.

Why do I get a 'Loader/Linker' error when loading a module?
-----------------------------------------------------------

The version of InspIRCd which the module was compiled for is different to your server. Run
`make clean` and then `make install` to rebuild everything on the same version.

When I run my IRC server it exits saying 'Failed to write PID-file'
-------------------------------------------------------------------

There is a syntax error in your configuration file. To show the real error, move the \<pid\> tag to
the top of your configuration.

How can I use channel admin commands such as kick/mode without having op?
-------------------------------------------------------------------------

Load [m_override](https://github.com/inspircd/wiki/blob/master/Modules/override.md).

Please note that this module must be loaded on all servers of your network or your mode changes may
be reversed and/or you may cause desyncs.

When users connect, InspIRCd never resolves their ident
-------------------------------------------------------

Ident lookups on InspIRCd are provided by [m_ident](https://github.com/inspircd/wiki/blob/master/Modules/ident.md).
You must load this module for them to be resolved.

Can InspIRCd make cheese sandwiches?
------------------------------------

Yes, providing that you load the [m_cheesesandwich](https://github.com/inspircd/wiki/blob/master/Modules/m_cheesesandwich.md)
module.