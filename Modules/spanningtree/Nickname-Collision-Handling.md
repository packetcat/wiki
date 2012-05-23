# InspIRCd Wiki &raquo; Modules &raquo; m_spanningtree &raquo; Nickname Collision Handling

The InspIRCd 1.2+ spanningtree protocol adopts a TS6-like nickname collision algorithm which
minimises the impact of nickname collisions and prevents most if not all KILLs when a collision
does occur.

The rules for nickname collision are as follows:

**If the user@ip of the two colliding users are equal:** Force nick change on OLDER client which
changed their nickname first (this is to prevent penalizing users who have reconnected, so that
their 'ghost' does not win the collision).

**If the user@ip of the two colliding users differ:** Force nick change on NEWER client which
changed their nickname last (this is to help prevent users camping on nicknames, causing a
collision and stealing that nickname during the resync).

**If the timestamps of the clients are equal**: Force a nick change on both.

Where nickname changes are enforced by this algorithm, the nickname is changed to the users UUID.
Because the user's UUID contains a leading digit, it is impossible for any user to NICK to their
UUID or anyone elses UUID and 'camp' on it. Only a server may force a nick change to such an
'illegal' nickname.

IMPORTANT NOTE: In a vanilla install of InspIRCd, there is no KILL message here for any collision
scenario. However, it is possible that a third party module may deny the nickname change to UID,
which will cause a last-resort Nickname collision KILL. Understandably, this is not a desirable
situation, so care should be taken not to run such modules if this bothers you.
