Configuring SNOMASKs
--------------------

To set SNOMASKs, set user mode +s with the server notice masks you want as a parameter to the mode. For example, to see local and remote connections and quit notices, execute the following command:

    /MODE YourNick +s +cCqQ

To enable automatic setting of SNOMASKs upon opering, load [m_opermodes](https://github.com/inspircd/wiki/blob/master/Modules/opermodes.md) and set the modes in the type block. For example:

    <type name="GlobalOp" classes="OperChat BanControl HostCloak Modular" host="globalop.chatspike.net" automodes="+s +cCqQ">

To remove a SNOMASK, set user mode +s again, but remove masks by sending a 'negative' change. For example, to disable remote connection and quit notices, execute the following command:

    /MODE YourNick +s -CQ

To disable all server notice masks, simply remove user mode +s entirely:

    /MODE YourNick -s

A list of the valid server notice masks and what they do is listed below. 

Channel Logging
---------------

You can use the [m_chanlog](https://github.com/inspircd/wiki/blob/master/Modules/chanlog.md) module to send messages to a channel of your choice. You can even have multiple channels for different masks. Use local masks on every server to the same channel to receive messages globally in the channel.

Valid Server Notice Masks
-------------------------

### Core Server Notice Masks

These are the server notice masks implemented by the core. Modules (table #2) may implement extra notice masks.


SNOTICE Mask | Function
------------ | --------
A            | Allows receipt of global announcement messages
a            | Allows receipt of local announcement messages 
C            | Allows receipt of remote connection messages
c            | Allows receipt of local connection messages
Q            | Allows receipt of remote quit messages 
q            | Allows receipt of local quit messages 
k            | Allows receipt of local kill messages
K            | Allows receipt of remote kill messages
L            | Allows receipt of linking related messages from other servers
l            | Allows receipt of linking related messages 
O            | Allows receipt of remote oper-up, oper-down, and oper-failure messages 
o            | Allows receipt of local oper-up, oper-down, and oper-failure messages 
d            | Allows receipt of general (and sometimes random) debug messages 
X            | Allows receipt of remote XLine notices (E/G/K/Q/Z as well as those provided by modules)
x            | Allows receipt of local XLine notices (E/G/K/Q/Z as well as those provided by modules) 
t            | Allows receipt of attempts to use /STATS (local and remote)
f            | Allows receipt of flooding notices

### Module Server Notice Masks

SNOTICE Mask | Module       | Function
------------ | ------------ | -------- 
g            | m_globops    | Allows receipt of local globops 
G            | m_glopops    | Allows receipt of remote globops 
n            | m_seenicks   | See local nickname changes 
N            | m_seenicks   | See remote nickname changes 
J            | m_chancreate | Allows receipt of remote channel creation notices 
j            | m_chancreate | Allows receipt of local channel creation notices 
v            | m_override   | Allows receipt of use of oper override
