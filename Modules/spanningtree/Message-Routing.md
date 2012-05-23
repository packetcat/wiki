InspIRCd has four behaviours when it routes a message. These four behaviours are chosen dependent
upon the message and the target and source of that message individually. These behaviours are:

One To One Routing (Directed)
-----------------------------
This is used to route a message from one server directly to another server, taking a route only
through servers which need to process the message in order to pass it straight to its destination.
Examples of this are PRIVMSG and NOTICE direct to a user (not to a channel) and any messages
exchanged during the initial burst and authentication phase.

One to all (Broadcast)
----------------------

This is used to broadcast a message to all servers, and each server which receives such a message
will then pass it on to its peers using "one to all-but-one" as shown below. This is used for
messages which the entire network must see to remain synchronized, e.g. NICK and QUIT.

One to all-but-one
------------------

This is used to pass on a "one to all" message which has originated from another server. The message
may not be passed on via a second "one to all" message, because doing so would bounce the message
back along the network to its source and cause a desync.

One to group
------------

This is used only by channel PRIVMSG and NOTICE. To cut down on bandwidth, channel PRIVMSG and
NOTICE are not broadcast. To achieve routing for these types of message, a list is compiled
consisting only of locally connected servers the PRIVMSG or NOTICE must be sent to in order to
reach all of its recipients. Each recipient is then responsible for running the message against
this algorithm again to ensure it eventually reaches all intended recipients, and no extra servers
which do not have users on the channel will receive the message or act upon it.
