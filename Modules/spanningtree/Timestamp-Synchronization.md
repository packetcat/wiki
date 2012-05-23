# InspIRCd Wiki &raquo; Modules &raquo; m_spanningtree &raquo; Timestamp Synchronization

Because the InspIRCd Spanning Tree Protocol operates using UNIX timestamps, you must ensure that the
system clocks on all of your servers are synchronized. This is best done with ntpd or ntpdate. If
you do not synchronize the clocks on your servers, you will find that timestamp calculations will
exhibit strange results, and users will be randomly deopped in new channels.
