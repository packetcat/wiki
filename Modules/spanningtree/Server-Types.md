# InspIRCd Wiki &raquo; Modules &raquo; m_spanningtree &raquo; Server Types

InspIRCd has three types of server. Although the same in design, and speaking the same protocol,
their behaviours are different due to the roles they play in maintaining the network. These are:

Hub
---

A hub is categorized as any server which has more than one locally connected server. A hub differs
from normal operation in that the bandwidth passing through a hub is usually much greater than that
passing through a leaf, and it may expend more computing power to run a hub.

Leaf
----

A leaf is categorized as any server which has only one, or no connected servers. A leaf does not
have to route as much information as a hub (see above) but usually because of this is configured to
hold many more clients as it has the spare computer power to hold the users.

U-Line
------

A U-lined server is usually a leaf server, however in InspIRCd, a hub may also be U-lined. U-lined
servers have many extra privileges, which are required for example to operate a services server or
similar. U-lines must be individually configured on all servers to work, and all servers must be in
agreement about the names of the U lined servers. If they are not in agreement, mode changes will be
dropped and commands forbidden which should operate normally.
