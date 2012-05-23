# InspIRCd Wiki &raquo; Modules &raquo; m_spanningtree &raquo; Protocol

## Introduction to the Spanning Tree Protocol

InspIRCd's protocol is a UID/SID based protocol similar in behaviour to the [TS6 protocol](http://hg.atheme.org/charybdis/file/tip/doc/technical/ts6-protocol.txt)
used by some other IRC servers. Linking a server using the InspIRCd Spanning Tree Protocol is
relatively straightforward for anyone who's handled IRC servers and their protocols before.

Protocol changes will be generally backwards-compatible with previous major versions. Major version
changes (e.g. 1.1 to 1.2) usually mean major protocol changes. Any changes to the protocol in minor
releases will not usually break previous releases unless absolutely necessary (e.g. to fix an
exploit or race condition).

Please note that the InspIRCd Spanning Tree Protocol is not related in any way to the CISCO
Spanning Tree Protocol used in local area networks. The name of our protocol comes from the
mathematical name for the tree structure it represents, similar to the reason for their naming.

## Protocol Documentation

Due to the advanced and detailed nature of the InspIRCd Spanning Tree Protocol, the documentation is
split into multiple sections for easier searching and readability. Please choose the section you
require from the list below:

* [Connecting a Server](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Connecting-a-Server.md)
&mdash; guide to connecting two servers together, authentication mechanisms and handshake protocols.

* [Commands](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Commands.md) &mdash;
a list of commands supported by the InspIRCd Spanning Tree Protocol.

* [UUIDs](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/UUIDs.md) &mdash; a
guide to UUIDs (Universally Unique Identifiers) used to identify users and servers.

* [Nickname Collision Handling](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Nickname-Collision-Handling.md)
&mdash; a guide to collision handling and prevention of unnecessary nickname collision kills.

* [Message Routing](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Message-Routing.md)
&mdash; a guide to message routing in the InspIRCd Spanning Tree Protocol.

* [Server Types](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Server-Types.md)
&mdash; a guide to different types of server in the InspIRCd Spanning Tree Protocol.

* [Timestamp Synchronization](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Timestamp-Synchronization.md)
&mdash; a guide to keeping your clocks correct: Important for IRC as a whole.

* [Example Traffic](https://github.com/inspircd/wiki/blob/master/Modules/spanningtree/Example-Traffic.md)
&mdash; an example conversation between two InspIRCd 1.2 servers.
