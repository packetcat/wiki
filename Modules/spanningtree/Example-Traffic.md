Example Traffic
---------------

This is an example of a netburst and some random traffic between two 1.2.0 (Alpha 7) servers. Outbound traffic is indicated with a "->", inbound traffic is marked with "<-".

<pre>
-> CAPAB START
-> CAPAB MODULES m_allowinvite.so,m_alltime.so,m_auditorium.so,m_banexception.so,m_blockcaps.so,m_blockcolor.so,m_botmode.so,m_callerid.so,m_cban.so,m_censor.so,m_chanfilter.so, m_chanprotect.so,m_chghost.so,m_chgident.so,m_chgname.so,m_cloaking.so,m_commonchans.so,m_dccallow.so,m_deaf.so,m_delayjoin.so,m_filter.so,m_globalload.so,m_globops.so, m_hidechans.so,m_hideoper.so,m_invisible.so,m_inviteexception.so,m_joinflood.so,m_kicknorejoin.so,m_knock.so,m_messageflood.so,m_nickflood.so,m_nicklock.so,m_noctcp.so
-> CAPAB MODULES m_nokicks.so,m_nonicks.so,m_nonotice.so,m_operchans.so,m_permchannels.so,m_redirect.so,m_remove.so,m_sajoin.so,m_samode.so,m_sanick.so,m_sapart.so,m_saquit.so, m_services_account.so,m_servprotect.so,m_sethost.so,m_setident.so,m_setname.so,m_showwhois.so,m_shun.so,m_silence.so,m_stripcolor.so,m_svshold.so,m_swhois.so,m_timebans.so, m_watch.so
-> CAPAB CAPABILITIES :NICKMAX=32 HALFOP=1 CHANMAX=65 MAXMODES=20 IDENTMAX=12 MAXQUIT=256 MAXTOPIC=308 MAXKICK=256 MAXGECOS=129 MAXAWAY=201 IP6NATIVE=0 IP6SUPPORT=1 PROTOCOL=1201 CHALLENGE=a%'ski?#-uo1y5u'kka PREFIX=(qaohv)~&@%+ CHANMODES=Ibeg,k,FJLfjl,ABCDGKMNOPQRSTcimnpstu SVSPART=1
-> CAPAB END
<- CAPAB START
<- CAPAB MODULES m_allowinvite.so,m_alltime.so,m_auditorium.so,m_banexception.so,m_blockcaps.so,m_blockcolor.so,m_botmode.so,m_callerid.so,m_cban.so,
m_censor.so,m_chanfilter.so,m_chanprotect.so,m_chghost.so,m_chgident.so,m_chgname.so,m_cloaking.so,m_commonchans.so,m_dccallow.so,m_deaf.so,m_delayjoin.so, m_filter.so,m_globalload.so,m_globops.so,m_hidechans.so,m_hideoper.so,m_invisible.so,m_inviteexception.so,m_joinflood.so,m_kicknorejoin.so,m_knock.so,m_messageflood.so, m_nickflood.so,m_nicklock.so,m_noctcp.so
<- CAPAB MODULES m_nokicks.so,m_nonicks.so,m_nonotice.so,m_operchans.so,m_permchannels.so,m_redirect.so,m_remove.so,m_sajoin.so,m_samode.so,m_sanick.so,m_sapart.so,m_saquit.so, m_services_account.so,m_servprotect.so,m_sethost.so,m_setident.so,m_setname.so,m_showwhois.so,m_shun.so,m_silence.so,m_stripcolor.so,m_svshold.so,m_swhois.so, m_timedbans.so,m_watch.so
<- CAPAB CAPABILITIES :NICKMAX=32 HALFOP=1 CHANMAX=65 MAXMODES=20 IDENTMAX=12 MAXQUIT=256 MAXTOPIC=308 MAXKICK=256 MAXGECOS=129 MAXAWAY=20 IP6NATIVE=0 IP6SUPPORT=1 PROTOCOL=1201 CHALLENGE=5g3#e/{kq5e-s5oo}a{ PREFIX=(qaohv)~&@%+ CHANMODES=Ibeg,k,FJLfjl,ABCDGKMNOPQRSTcimnpstu SVSPART=1
<- CAPAB END
-> SERVER test2.chatspike.net HMAC-SHA256:723921e3721e2a36a2a472c53c4773a0838eeb28e46a73f361eb2da9b61e9c22 0 751 :Test server
<- SERVER test.chatspike.net HMAC-SHA256:8dfe2320a73ca5c8a7a95f2eceb9f8c1ebfd1e067dd28471c30f10abfe8ed8f0 0 037 :"Bollocks" Said pooh, as he caught his testicles in the vice.
-> :751 BURST 1220196382
-> :751 VERSION :InspIRCd-1.2 test2.chatspike.net :Linux brainwave 2.6.23-gentoo-r6 (InspIRCd-1.2.0a5+GreatCowGuru) [FLAGS=10222,epoll,751]
-> :751 UID 751AAAAAA 1220196319 Brain brainwave.brainbox.cc netadmin.chatspike.net brain 192.168.1.10 1220196324 +Siosw +ACKNOQcdfgklnoqtx :Craig Edwards
-> :751AAAAAA OPERTYPE NetAdmin
-> :751 FJOIN #test 1220196321 +nt :o,751AAAAAA
-> :751 ADDLINE E *@ircop.host.com <Config> 1220196315 0 :Opers hostname
-> :751 ADDLINE Q *[rxHO]* <Config> 1220196315 0 :Script kiddiot.
-> :751 ADDLINE Q ChanServ <Config> 1220196315 0 :Reserved For Services
-> :751 ADDLINE Q MemoServ <Config> 1220196315 0 :Reserved For Services
-> :751 ADDLINE Q NickServ <Config> 1220196315 0 :Reserved For Services
-> :751 ADDLINE Q OperServ <Config> 1220196315 0 :Reserved For Services
-> :751 ADDLINE Z 66.66.66.66 <Config> 1220196315 0 :This is the devils ip. You cannot use it.
-> :751 ADDLINE Z 69.69.69.69 <Config> 1220196315 0 :No porn here thanks.
-> :751 METADATA * filter :*BANTHIS* gline * 10 :Banned text
-> :751 METADATA * filter :*BLOCKTHIS* block * 0 :Blocked text
-> :751 METADATA * filter :*KILLTHIS* kill * 0 :Killed text
-> :751 ENDBURST
<- :037 BURST 1220196382
<- :037 VERSION :InspIRCd-1.2 test.chatspike.net :FreeBSD neuron.brainbox.cc 5.4-RELEASE (InspIRCd-1.2.0a6+Tuxer) [FLAGS=10352,kqueue,037]
<- :037 UID 037AAAAAA 1220196029 BrainNeuron synapse.brainbox.cc netadmin.chatspike.net brain 10.0.0.2 1220196034 +Sioswx +COQcdfkloqtx :Craig Edwards
<- :037AAAAAA OPERTYPE NetAdmin
<- :037 FJOIN #test 1220196030 +nt :o,037AAAAAA
<- :037 ADDLINE E *@ircop.host.com <Config> 1220196025 0 :Opers hostname
<- :037 ADDLINE Q *[rxHO]* <Config> 1220196025 0 :Script kiddiot.
<- :037 ADDLINE Q ChanServ <Config> 1220196025 0 :Reserved For Services
<- :037 ADDLINE Q MemoServ <Config> 1220196025 0 :Reserved For Services
<- :037 ADDLINE Q NickServ <Config> 1220196025 0 :Reserved For Services
<- :037 ADDLINE Q OperServ <Config> 1220196025 0 :Reserved For Services
<- :037 ADDLINE Z 66.66.66.66 <Config> 1220196025 0 :This is the devils ip. You cannot use it.
<- :037 ADDLINE Z 69.69.69.69 <Config> 1220196025 0 :No porn here thanks.
<- :037 ENDBURST
</pre>
