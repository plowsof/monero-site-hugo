---
title: Overview and Logs for the Dev Meeting Held on 2019-03-10
summary: March 9th HF feedback, Point release discussions, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<hyc\></strong> ding  
<strong>\<rbrunner\></strong> dong  
<strong>\<rehrar\></strong> oyo  
<strong>\<moneromooo\></strong> The witch.  
<strong>\<rehrar\></strong> 1. Greetings  
<strong>\<el00ruobuob\_\[m\]\></strong> Hi guys\!  
<strong>\<ArticMine\></strong> hi  
<strong>\<endogenic\></strong> sup y'all  
<strong>\<rbrunner\></strong> Hi  
<strong>\<ErCiccione\[m\]\></strong> Hi  
<strong>\<rehrar\></strong> 2. Fork Discussions  
<strong>\<rehrar\></strong> Is there anything that anyone present would like to discuss regarding the previous fork? We'll get to next point release items soon.  
<strong>\<hyc\></strong> looks like all quiet  
<strong>\<rehrar\></strong> it all went smooth as a baby's skin  
<strong>\<rehrar\></strong> Yay. It looks like this meeting will be short indeed.  
<strong>\<rbrunner\></strong> Just the first block was a real cliffhanger, right?  
<strong>\<el00ruobuob\_\[m\]\></strong> it's been a long first block, besides that all's fine  
<strong>\<ErCiccione\[m\]\></strong> I take advantage of the quietness to say that i hope we will introduce a strict(er) release cycle for next release  
<strong>\<sarang\></strong> At some point the goal is to move to a longer cycle, no?  
<strong>\<hyc\></strong> maybe we should focus on making reproducible builds work  
<strong>\<ErCiccione\[m\]\></strong> i recently took a look at how nextcloud does, they release every 4 months, so it's somehow usable for us  
<strong>\<ErCiccione\[m\]\></strong> hyc: solid +1 for that  
<strong>\<ErCiccione\[m\]\></strong> sarang: i hope so, afaik we never really had a proper discussion about that  
<strong>\<sarang\></strong> As long as PoW tweaks are in the cards, I presume we'll stick to 6 months though  
<strong>\<WoomyZoomy\></strong> Why the use of "goto" in bulletproof\_PROVE instead of more common flow controls?  
<strong>\<sarang\></strong> that's a question for moneromooo  
<strong>\<moneromooo\></strong> Ah, simplicity.  
<strong>\<rehrar\></strong> 3. Upcoming point release discussions  
<strong>\<ErCiccione\[m\]\></strong> sarang: sure, i was just pointing out that the timing is similar, so we could look at their system for inspiration. I can't find the page right now, but it was very solid, with planty of time for development, freeze and RC releases  
<strong>\<moneromooo\></strong> They presumably don't have to have misc other software update in sync.  
<strong>\<WoomyZoomy\></strong> Thanks  
<strong>\<rehrar\></strong> I know I had some questions, and the community at large is a little confused what is coming in the next point release, and if we have a timeline for that or not  
<strong>\<moneromooo\></strong> Everything that's on master, probably all/most of what's currnetly PRed and that's not super old.  
<strong>\<moneromooo\></strong> Except maybe the 128 bit diff change.  
<strong>\<hyc\></strong> \* current master crashes  
<strong>\<moneromooo\></strong> Well, nohting says we can't add \*more\* fixes :)  
<strong>\<ErCiccione\[m\]\></strong> (nextcloud's release schedule: <https://docs.nextcloud.com/server/stable/admin\_manual/release\_schedule.html>)  
<strong>\<rehrar\></strong> because I know some features people are excited about (like Trezor, no?) are coming out with that?  
<strong>\<rehrar\></strong> we just going with "soon"?  
<strong>\<sarang\></strong> Better faster stronger bulletproofs :D  
<strong>\<el00ruobuob\_\[m\]\></strong> not too soon, we need a proper code freeze for this point release  
<strong>\<ErCiccione\[m\]\></strong> I would love to just have that week of freeze for the GUI this time  
<strong>\<el00ruobuob\_\[m\]\></strong> yeah me too  
<strong>\<moneromooo\></strong> Did the GUI not choose to do a full release already ?  
<strong>\<rbrunner\></strong> Should be easier now, with the threat of ASIC domination gone  
<strong>\<hyc\></strong> yeah, it would be simpler if it was only the monero project. but we have to coordinate with exchanges/mining pools/3rd party miner developers/ etc  
<strong>\<rbrunner\></strong> I think so, GUI was fully released  
<strong>\<ErCiccione\[m\]\></strong> moneromooo: yes, but would be good to have always that week for every release. I really need it to sync translations  
<strong>\<sarang\></strong> Is the intention to have new output selection for the point release?  
<strong>\<moneromooo\></strong> If you and suraeNoether are happy with the details, sure.  
<strong>\<sarang\></strong> It would be nice to have a rough deadline for freeze set  
<strong>\<sarang\></strong> (and we can discuss output selection at tomorrow's MRL meeting 17:00 UTC)  
<strong>\<rehrar\></strong> unfortunately hard to do without core?  
<strong>\<rbrunner\></strong> Maybe also depends on when master will be able to work with the 3 Monero nets again, because basically testing can start only then  
<strong>\<rehrar\></strong> Alright, was there any other meeting items that someone wanted to discuss?  
<strong>\<rehrar\></strong> now that we at the other side?  
<strong>\<rbrunner\></strong> The second hardfork will hardly give any problems, being rather trivial, right?  
<strong>\<moneromooo\></strong> Likely.  
<strong>\<sarang\></strong> If this is a good avenue for it, I'd like any opinions on output selection since it is likely to change at the next point release (non consensus, of course)  
<strong>\<sarang\></strong> We've discussed in MRL at length  
<strong>\<pigeons\></strong> oh the point release will be a hardfork also?  
<strong>\<rbrunner\></strong> No, I mean the second hardfork in what, 2 hours or so?  
<strong>\<pigeons\></strong> when was the first?  
<strong>\<moneromooo\></strong> Yesterday.  
<strong>\<rbrunner\></strong> er .. yesterday  
<strong>\<el00ruobuob\_\[m\]\></strong> most likely 22h rbrunner  
<strong>\<pigeons\></strong> ok i see i thought i was reading things wrong  
<strong>\<rbrunner\></strong> Ah, ok, 2 days  
<strong>\<hyc\></strong> more than 2 days, at the current rate  
<strong>\<ArticMine\></strong> 0.9 days based upon 2 min blocks  
<strong>\<ArticMine\></strong> We are more like 15 in blocks now  
<strong>\<ArticMine\></strong> 15min  
<strong>\<rbrunner\></strong> But with nicely falling difficulty  
<strong>\<moneromooo\></strong> If someone can get the master daemon to crash in debug mode with log level 2 and a core, that'd be great :)  
<strong>\<rehrar\></strong> does anyone have any comments for sarang?  
<strong>\<moneromooo\></strong> Because mine ain't.  
<strong>\<el00ruobuob\_\[m\]\></strong> is it the output selection about coinbase transactions highlight by sgp\_ ?  
<strong>\<hyc\></strong> took quite a while for my debug build to crash but it eventually did. before I removed the ssl patches  
<strong>\<sarang\></strong> el00ruobuob\_\[m\]: it will help to address that, but in a more general sense  
<strong>\<moneromooo\></strong> Did you have a better stack trace, and logs showing what was being done in other threads ?  
<strong>\<sarang\></strong> where output selection is poorly weighted by block "density"  
<strong>\<hyc\></strong> moneromooo: I gave you the stack trace, didn't check other threads unfortunately. I can try spinning that up again.  
<strong>\<el00ruobuob\_\[m\]\></strong> i have to confess i don't understand very well this subject sarang  
<strong>\<moneromooo\></strong> Logs will help here.  
<strong>\<rehrar\></strong> sarang, maybe discuss tomorrow at the MRL meeting  
<strong>\<moneromooo\></strong> If another thread deleted some object, it might not show up on the stack trace if it's already done.  
<strong>\<rehrar\></strong> I think we can end here and business as usual can commence if that's alright with everyone.  
<strong>\<rehrar\></strong> Next weeks is community meeting, and we want to be desynced from them, so next meeting two weeks?  
<strong>\<hyc\></strong> rehrar: sounds good  
<strong>\<rehrar\></strong> thanks for coming, and everyone was here with the new time (stupid DST)  
<strong>\<rbrunner\></strong> Over here in Europe we will soon stop that DST nonsense  
<strong>\<el00ruobuob\_\[m\]\></strong> thank you all\!  
<strong>\<rbrunner\></strong> Maybe last change next year  
<strong>\<rbrunner\></strong> Likewise\!
