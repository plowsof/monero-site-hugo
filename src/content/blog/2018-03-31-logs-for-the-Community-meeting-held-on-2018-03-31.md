---
title: Logs for the Community Meeting Held on 2018-03-31
summary: Community highlights, Forum Funding System updates, RFC-HWALLET-1, Localization workgroup, RIAT Monero workgroup, and miscellaneous
tags: [dev diaries, crypto]
author: el00ruobuob / SamsungGalaxyPlayer
---

# Logs

<strong>\<sgp\_\></strong> All right, meeting time  
<strong>\<sgp\_\></strong> 0. Introduction  
<strong>\<sgp\_\></strong> We would like to welcome everyone to this Monero Community Meeting\!  
<strong>\<sgp\_\></strong> Link to agenda on GitHub: <https://github.com/monero-project/meta/issues/199>  
<strong>\<sgp\_\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community. We use meetings to encourage the community to share ideas and provide support.  
<strong>\<sgp\_\></strong> 1. Greetings  
<strong>\<serhack\></strong> Hi  
<strong>\<msvb-lab\></strong> Hello.  
<strong>\<ArticMine\></strong> Hi  
<strong>\<ErCiccione\></strong> Hola  
<strong>\<cryptochangement\></strong> hola amigos de privacidad  
<strong>\<xmrmatterbridge\> \<hrumag\></strong> Buonasera a tutti\!  
<strong>\<xmrscott\[m\]\></strong> Salutations  
<strong>\<freelikeinfreedo\></strong> Hello 🙂  
<strong>\<parasew\[m\]\></strong> hello\!  
<strong>\<sgp\_\></strong> looks like we have a good crowd today  
<strong>\<sgp\_\></strong> 2. Community highlights  
<strong>\<sgp\_\></strong> Monero 0.12.0.0 is released. The GUI is still forthcoming. You must update your software by April 6 to continue spending funds. You can download a copy of it here: <https://github.com/monero-project/monero/releases/tag/v0.12.0.0>  
<strong>\<sgp\_\></strong> I published a response to “An Empirical Analysis of Traceability in the Monero Blockchain”, version 2: <https://getmonero.org/2018/03/29/response-to-an-empirical-analysis-of-traceability.html>  
<strong>\<sgp\_\></strong> dsc\_\_ shared a preview of the GUI black theme: <https://www.reddit.com/r/Monero/comments/86l3km/gui\_black\_theme\_preview/>  
<strong>\<monerobux\></strong> \[REDDIT\] GUI - Black theme preview (self.Monero) \| 104 points (98.0%) \| 29 comments \| Posted by dsc\_\_ \| Created at 2018-03-23 - 14:36:17  
<strong>\<sgp\_\></strong> Does anyone else have community updates to share?  
<strong>\<xmrscott\[m\]\></strong> DefCon workgroup created  
<strong>\<serhack\></strong> Mastering Monero released a preview of the first chapter. If you want to contribute, <https://github.com/monerobook/monerobook>  
<strong>\<xmrscott\[m\]\></strong> First meeting a Saturday from now  
<strong>\<serhack\></strong> The preview of the first chapter is available on <https://masteringmonero.com>  
<strong>\<KnifeOfPi\_\></strong> hello\!  
<strong>\<ErCiccione\></strong> The GUI is basically ready, binaries will be probably built within the weekend  
<strong>\<KnifeOfPi\_\></strong> we’re working on getting cakewallet ready  
<strong>\<sgp\_\></strong> ah yes xmrscott, link to the thread about DefCon here: <https://www.reddit.com/r/Monero/comments/87uy99/the\_monero\_project\_defcon\_26\_aug\_912\_in\_las\_vegas/>  
<strong>\<monerobux\></strong> \[REDDIT\] The Monero Project @ DefCon 26 (Aug 9-12 in Las Vegas)\! Looking for volunteers\! First DefCon workgroup meeting 4/7\! (self.Monero) \| 15 points (74.0%) \| 11 comments \| Posted by xmrscott \| Created at 2018-03-28 - 19:50:11  
<strong>\<sgp\_\></strong> serhack I should have time to review the book this weekend  
<strong>\<serhack\></strong> A lot of updates today\! Nice\!  
<strong>\<m2049r\[m\]\></strong> monerujo beta is 0.12 ready (and on play store &amp; github)  
<strong>\<cryptochangement\></strong> are exchanged and such all aware of the new release? the fork is in a week and we dont want them left behind  
<strong>\<sgp\_\></strong> dEBRUYNE will you make a list of pools and exchanges that have updated as you have done in the past?  
<strong>\<ErCiccione\></strong> sgp\_: +1 i wasabout to ask that  
<strong>\<dEBRUYNE\></strong> I guess I could, but the ecosystem has grown substantially  
<strong>\<dEBRUYNE\></strong> Not sure if it'd be feasible to maintain or even create such a list  
<strong>\<KnifeOfPi\_\></strong> I’m not sure if it’s necessary - most major pools that aren’t botnet or bitmain pools probably know  
<strong>\<ErCiccione\></strong> dEBRUYNE: what if we make in on etherpad? so anybody can update it  
<strong>\<dEBRUYNE\></strong> sgp\_: I'll ask fluffypony to send a reminder email to all pools though  
<strong>\<cryptochangement\></strong> at the lease it would be nice to pin a thread on reddit where people can confirm/verify that their pool/exchange/service has updated  
<strong>\<rehrar\></strong> or delete it D:  
<strong>\<dEBRUYNE\></strong> ErCiccione: I guess that could work  
<strong>\<sgp\_\></strong> cryptochangement I think that would be especially helpful for r/MoneroMining  
<strong>\<dEBRUYNE\></strong> But may be susceptible to fraud  
<strong>\<cryptochangement\></strong> I dont see why somebody would lie about having updated or not  
<strong>\<m2049r\[m\]\></strong> if a pool doesnt update, they are effectively mining monero0?  
<strong>\<ErCiccione\></strong> true. we can create a workgroup on taiga  
<strong>\<dEBRUYNE\></strong> m2049r\[m\]: yes  
<strong>\<xmrmatterbridge\> \<hrumag\></strong> ErCiccione: +1  
<strong>\<ArticMine\></strong> if a pool doesnt update, they are effectively mining monero0? \<--- If they do not change the seed nodes I suspect not  
<strong>\<sgp\_\></strong> ErCiccione would you mind creating that then and adding me as a contributor? I would like to get the pool list in r/MoneroMining  
<strong>\<dEBRUYNE\></strong> ArticMine: Seed nodes are only relevant for the initial connection  
<strong>\<dEBRUYNE\></strong> sgp\_: You can use my table from the old thread I guess?  
<strong>\<ErCiccione\></strong> sure, doing it now  
<strong>\<ErCiccione\></strong> sgp\_ ^  
<strong>\<sgp\_\></strong> dEBRUYNE yes, I'll start there  
<strong>\<dEBRUYNE\></strong> <https://www.reddit.com/r/Monero/comments/6yuv2s/psa\_users\_solominers\_exchangesmerchantsservices/>  
<strong>\<monerobux\></strong> \[REDDIT\] PSA: Users, (solo)miners, exchanges/merchants/services, and pool operators must be on CLI v0.11.0.0 or GUI v0.11.0.0 in advance of the scheduled protocol upgrade otherwise you will get booted off the network. Miners, please contact your pool operator to ask them if they have upgraded\! (self.Monero) \| 143 points (99.0%) \| 189 comments \| Posted by dEBRUYNE\_1 \| Created at 2017-09-08 - 13:47:34  
<strong>\<dEBRUYNE\></strong> I'll PM you the markup  
<strong>\<sgp\_\></strong> I should be able to view the source  
<strong>\<sgp\_\></strong> Just verified, can view. No PM for that necessary  
<strong>\<xmrmatterbridge\> \<hrumag\></strong> \* CLI v0.12.0.0 or GUI v.0.12.0.0  
<strong>\<sgp\_\></strong> All right, I think we should move on to the next section. If there are still discussions, we can have them during open ideas time  
<strong>\<sgp\_\></strong> 3. FFS updates  
<strong>\<sgp\_\></strong> There are several Forum Funding System updates.  
<strong>\<sgp\_\></strong> m2049r has opened a proposal to raise funds to work on Monerujo: <https://forum.getmonero.org/6/ideas/90038/m2049r-part-time-for-3-months>  
<strong>\<sgp\_\></strong> The community funded suraeNoether for Q2: <https://forum.getmonero.org/8/funding-required/90057/funding-for-surae-at-mrl-q2-2018>  
<strong>\<sgp\_\></strong> The community funded sarangNoether for Q2: <https://forum.getmonero.org/8/funding-required/90028/sarang-funding-for-april-may-2018>  
<strong>\<sgp\_\></strong> The community funded erciccione for the localization workgroup: <https://forum.getmonero.org/8/funding-required/90000/monero-localizations-coordinator-2nd-ffs>  
<strong>\<sgp\_\></strong> The community funded moneromooo to work on Monero from April to June: <https://forum.getmonero.org/8/funding-required/89998/moar-mooo-coding-april-june>  
<strong>\<sgp\_\></strong> The community funded serhack to continue working on Mastering Monero: <https://forum.getmonero.org/8/funding-required/89797/mastering-monero-ffs>  
<strong>\<suraeNoether\></strong> thanks everyone\!  
<strong>\<sgp\_\></strong> It seems that further discussion is necessary on the Ruby implementation: <https://forum.getmonero.org/6/ideas/89913/a-native-ruby-implementation-of-the-monero-wallet>  
<strong>\<sgp\_\></strong> I have opened a new Reddit discussion thread for this here: <https://www.reddit.com/r/Monero/comments/88jlqc/other\_discussions\_on\_monero\_ruby\_ffs\_proposal/>  
<strong>\<monerobux\></strong> \[REDDIT\] Other Discussions on Monero Ruby FFS Proposal (self.Monero) \| 9 points (100.0%) \| 8 comments \| Posted by SamsungGalaxyPlayer \| Created at 2018-03-31 - 16:05:30  
<strong>\<serhack\></strong> Thank Community\!  
<strong>\<sgp\_\></strong> Does anyone know if the development team got wind of this, and what their recommendation is?  
<strong>\<rehrar\></strong> We should also talk about that MoneroCat series proposal :D  
<strong>\<ErCiccione\></strong> thanks a lot folks\!  
<strong>\<rehrar\></strong> the dev team's opinion shouldn't matter in any special way in this matter  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> I want to see it  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> More for education purposes than anything  
<strong>\<rehrar\></strong> alternative implementations have been discussed before, and the only thing that they generally say is something to the effect of: "Make sure they know the amount of work involved"  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> Like that guy that implemented cryptonight in Pythob  
<strong>\<rehrar\></strong> wrappers ultimately fall back on the work of the C++ dev team, so not a ton of extra work involved.  
<strong>\<rehrar\></strong> But an alternative implementation must keep pace with C++ development (which has many contributors)  
<strong>\<rehrar\></strong> so if it's just one person, they'd be doing the job of moneromooo plus everyone else contributing  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> Even a wrapper has to be maintained to a degree. I just don't want to see the FFS for this gut funded, payed out, then never maintained  
<strong>\<rehrar\></strong> this is the biggest issue for the community, yes  
<strong>\<rehrar\></strong> the amount of maintenance for another implementation is orders of magnitude higher, so the odds of it not being maintained really skyrocket  
<strong>\<rehrar\></strong> I may be speaking like a downer here, but if you read my comment on the thread, I really do think it's incredibly necessary to have stuff like this  
<strong>\<sgp\_\></strong> All right, glad we could re-open discussion on other implementations  
<strong>\<parasew\[m\]\></strong> there is an existing gem, but the original dev stopped communicating a while ago.  
<strong>\<m2049r\[m\]\></strong> plus: maintenance is boring  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> I still think it would nice to have for educational purposes. It also opens doors to get integrated with other things so if somebody picks it up for that use they could be motivated to help maintain it  
<strong>\<rehrar\></strong> this is admittedly one weakness in the FFS  
<strong>\<sgp\_\></strong> Do we know of any services that would want to use a Ruby implementation? If we know of groups, it has the highest chance of being maintained  
<strong>\<rehrar\></strong> if a person begins the project for money, but then money dries out, they are more likely to leave as well  
<strong>\<rehrar\></strong> whereas if there are passion projects of alternative implementations, the money is nice (if funded), but they're more likely to continue  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> Somebody mentioned shopify  
<strong>\<parasew\[m\]\></strong> there are parallel efforts on this gem, the meetup organiser of the ruby meetup in vienna was also expressing interest. i guess it needs somebody to coordinate this, so the FFS proposal is needed, but it needs multiple devs/oversight imho  
<strong>\<rehrar\></strong> agreed parasew\[m\]  
<strong>\<rehrar\></strong> the take away for this (for me) is: this is a great idea, and I support it whole heartedly  
<strong>\<rehrar\></strong> but it's not as simple as some in the community might think  
<strong>\<sgp\_\></strong> Any other thoughts on the Ruby implementation?  
<strong>\<sgp\_\></strong> Or can we discuss MoneroCat: <https://forum.getmonero.org/6/ideas/89764/i-d-like-to-develop-a-new-webcomic-series-starring-monerocat-and-the-justice-league-of-crypto>  
<strong>\<rehrar\></strong> move it, fund it  
<strong>\<parasew\[m\]\></strong> move it?  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> Tbh I think another issue with thr fork schedule is that forking 6 months not only bricks ASICs but alternative implementations too :/ thats a discussion for another time tho  
<strong>\<sgp\_\></strong> All right, thanks for the discussion on these everyone  
<strong>\<xmrmatterbridge\> \<cryptochangements\></strong> IIRC the XMR figure for that was put together when the market price was significantly higher. Is 150 XMR stilo enough for Monero Cat?  
<strong>\<rehrar\></strong> move the Monero Cat proposal I mean parasew\[m\]  
<strong>\<sgp\_\></strong> cryptochangements we can sort that out with the author  
<strong>\<sgp\_\></strong> a. RFC-HWALLET-1 project progress  
<strong>\<msvb-lab\></strong> Hello folks, today is the last day of RFC-HWALLET-1.  
<strong>\<parasew\[m\]\></strong> i suggest to discuss ruby implementation next time, or at least get all the people working on it on a table. i can organise an irc-discussion specifically on this topic, as i also talked to a few people interesting in helping.  
<strong>\<msvb-lab\></strong> Celebrate or cry.  
<strong>\<parasew\[m\]\></strong> this could solve the problem with "single point of maintainance" fails  
<strong>\<sgp\_\></strong> parasaw noted, we can add it to next meeting's agenda  
<strong>\<msvb-lab\></strong> According to the roadmap and project plan.  
<strong>\<msvb-lab\></strong> The good news is that it is ending due to meeting almost all requirements, namely 43 of 46 nonfunctional and functional requirements.  
<strong>\<msvb-lab\></strong> The results are in the GitHub repository, and docs in Taiga mostly:  
<strong>\<msvb-lab\></strong> <https://github.com/monero-project/kastelo/>  
<strong>\<msvb-lab\></strong> There will be some clean up, but I'll tag the sources today or soon and build tarballs for easy upload to fabricators.  
<strong>\<rehrar\></strong> cray cray  
<strong>\<rehrar\></strong> so the open spec is done and works?  
<strong>\<msvb-lab\></strong> In case anybody is curious what kind of activity follows, the end of RFC-HWALLET-1 does not mean the end of anything other than project structure and announcement that requirements were met.  
<strong>\<msvb-lab\></strong> rehrar: The open spec?  
<strong>\<msvb-lab\></strong> You mean schematic or?  
<strong>\<rehrar\></strong> nvm, I may just be an idiot. We'll talk later.  
<strong>\<msvb-lab\></strong> The design includes, schematic, layout, and bill of materials files.  
<strong>\<msvb-lab\></strong> That's the archive that usually gets sent to a PCBA or PCB fabricator.  
<strong>\<sgp\_\></strong> Thanks msvb-lab\!  
<strong>\<rehrar\></strong> HOPEFULLY sometime soon I can zap the spam away  
<strong>\<msvb-lab\></strong> parasew\[m\]: We can copy to several places in fact, yes I just need some examples after the meeting or something.  
<strong>\<sgp\_\></strong> msvb-lab is there anything you are waiting for before your new proposal is moved to funding required? <https://forum.getmonero.org/7/open-tasks/90126/advancing-monero-hardware-wallet>  
<strong>\<parasew\[m\]\></strong> msvb-lab: ping me, i can also help with content-reformatting if needed\!  
<strong>\<msvb-lab\></strong> sgp\_: I need to make sure the injection molding bids that have come in are good for the budget, and yes a few other changes before bumping 0.9 to 1.0 (the proposal.)  
<strong>\<msvb-lab\></strong> sgp\_: I'm also waiting for MoneroV, because it's possible they will want to fund the wallet instead.  
<strong>\<msvb-lab\></strong> Bad joke  
<strong>\<sgp\_\></strong> lmao  
<strong>\<sgp\_\></strong> All right thanks msvb-lab. I'm really looking forward to v1.0 of your proposal  
<strong>\<msvb-lab\></strong> sgp\_: Cool, thanks. Next toopic.  
<strong>\<sgp\_\></strong> b. Localization workgroup Q&amp;A  
<strong>\<ErCiccione\></strong> sooo  
<strong>\<ErCiccione\></strong> m2049r: of course, that would be super. is monerujo already set for localizations?  
<strong>\<rehrar\></strong> erciccione, you've done great work.  
<strong>\<m2049r\[m\]\></strong> yes, we have english &amp; spanish for now  
<strong>\<ErCiccione\></strong> thanks rehrar :)  
<strong>\<xmrmatterbridge\> \<hrumag\></strong> bravo\!  
<strong>\<serhack\></strong> Great idea m2049r :)  
<strong>\<serhack\></strong> Good job erciccione  
<strong>\<ErCiccione\></strong> great, so let's talk about that after the meeting, i'm honestly not familiar with monerujo's codebase, i need to check it out  
<strong>\<ErCiccione\></strong> thanks guys :)  
<strong>\<m2049r\[m\]\></strong> i'll get in touch with you  
<strong>\<sgp\_\></strong> Last chance for questions for ErCiccione  
<strong>\<ErCiccione\></strong> btw beside the GUI i haven't big updates. any question?curiosity?  
<strong>\<rehrar\></strong> ne  
<strong>\<sgp\_\></strong> All right ErCiccione, your work seems to speak for itself. Thanks for keeping us all updated  
<strong>\<sgp\_\></strong> 4. RIAT Monero workgroup  
<strong>\<sgp\_\></strong> The RIAT team would like to discuss the status of their projects for the year.  
<strong>\<ErCiccione\></strong> thank you sgp\_  
<strong>\<rehrar\></strong> RIAT?  
<strong>\<parasew\[m\]\></strong> The Monero Workgroup at RIAT has been working since 2017, we organised community workshops in dec 2017 and also hosted the team of the monero hardware wallet in vienna. We are mixed from Monero Austria meetup and have connections to other meetups as well. A meetup in Hongkong is currently also discussed.  
<strong>\<sgp\_\></strong> rehrar <https://riat.at/>  
<strong>\<parasew\[m\]\></strong> Some involved people are around here in the irc i guess, @m2049r, @nevvton\_, FreeAsInFreedom (txmr) and ofc others (you know who you are) :)  
<strong>\<msvb-lab\></strong> Hong Kong.  
<strong>\<parasew\[m\]\></strong> We also helped organise the assembly at the 34c3 in leipzig and we are looking forward to help spread the word with events throughout 2018. Especially now focusing on Defcon and starting with early planning on 35c3.  
<strong>\<parasew\[m\]\></strong> yes, thats us  
<strong>\<rehrar\></strong> noice  
<strong>\<ArticMine\></strong> So RIAT will be working of DefCON in Vegas  
<strong>\<parasew\[m\]\></strong> msvb-lab: i was visiting in hongkong and there are interested students who want to set up a meetup, first meetup planned between 15-30 july  
<strong>\<parasew\[m\]\></strong> ArticMine: yes we will support and help; is there a separate irc channel or should we discuss here?  
<strong>\<ArticMine\></strong> Excellent  
<strong>\<rehrar\></strong> there;s a meeting next Saturday for Defcon stuff  
<strong>\<parasew\[m\]\></strong> very good\! will there be the main focus on the hardware wallet or can we also do more?  
<strong>\<rehrar\></strong> the Monero village that we are sharing with BCOS has quite a bit in the works so far  
<strong>\<msvb-lab\></strong> It will be a lot of topics all at once.  
<strong>\<msvb-lab\></strong> The meeting.  
<strong>\<rehrar\></strong> some presentations we've discussed, workshops,  
<strong>\<rehrar\></strong> msvb-lab, can you grab the pad link?  
<strong>\<parasew\[m\]\></strong> very nice\!  
<strong>\<freelikeinfreedo\></strong> where is the meeting? in this channel?  
<strong>\<freelikeinfreedo\></strong> and which time?  
<strong>\<rehrar\></strong> I think so, let me grab the link  
<strong>\<rehrar\></strong> v  
<strong>\<rehrar\></strong> <https://github.com/monero-project/meta/issues/200>  
<strong>\<rehrar\></strong> lel  
<strong>\<rehrar\></strong> good to have more people on board  
<strong>\<rehrar\></strong> if you look in the backlog, there was quite a bit of discussion yesterday  
<strong>\<freelikeinfreedo\></strong> thanks  
<strong>\<parasew\[m\]\></strong> very nice, will check and also discuss with the others later; will also join next saturday.  
<strong>\<parasew\[m\]\></strong> workgroup at RIAT will also now meet in person more often,  
<strong>\<parasew\[m\]\></strong> The workgroup will now be meeting every monday IRL starting from april 9, and we will also be in \#monero-community to discuss our progress.  
<strong>\<parasew\[m\]\></strong> m2049r: do you want to talk a bit on the monerujo plans?  
<strong>\<m2049r\[m\]\></strong> working on some tweaks for the v0.12 release  
<strong>\<m2049r\[m\]\></strong> managed to set up f-droid environment yesterday ...  
<strong>\<m2049r\[m\]\></strong> and we have a huge backlog of cool functions on taiga :)  
<strong>\<m2049r\[m\]\></strong> but i will be going for the CRAZYpass next  
<strong>\<xmrmatterbridge\> \<hrumag\></strong> @erciccione when you're done you can come to mattermost. i've got updates and a question  
<strong>\<m2049r\[m\]\></strong> (generating secure passwords with RSA as in my published paper)  
<strong>\<freelikeinfreedo\></strong> \> managed to set up f-droid environment yesterday ...  
<strong>\<freelikeinfreedo\></strong> nice\! 😃  
<strong>\<ErCiccione\></strong> @hrumag coming\!  
<strong>\<parasew\[m\]\></strong> so the workgroup will be helping in growing the userbase of monerujo , FreeAsInFreedom (txmr) had the idea for a workshop with lineage+monerujo for legacy android devices  
<strong>\<rehrar\></strong> woot\!  
<strong>\<rehrar\></strong> copperhead \> lineage though  
<strong>\<rehrar\></strong> (don't kill me)  
<strong>\<parasew\[m\]\></strong> other tasks are ofc to support msvb-lab and team to spread the word on the open hw wallet and to possibly get more attention from the open hardware communities  
<strong>\<sgp\_\></strong> Sounds like an awesome idea  
<strong>\<msvb-lab\></strong> That would be great, thanks parasew\[m\].  
<strong>\<parasew\[m\]\></strong> and to create workshops and other formats to bring more people to monero.  
<strong>\<ArticMine\></strong> copperhead is not FLOSS it is semi free  
<strong>\<ArticMine\></strong> since it does not allow commercial use  
<strong>\<ArticMine\></strong> That being said there is no reason to not support it  
<strong>\<rehrar\></strong> it's further removed from Google  
<strong>\<sgp\_\></strong> Thanks parasew for the updates\! Any final thoughts?  
<strong>\<parasew\[m\]\></strong> just wanted to introduce that we will be active, anyone who wants to join physically, there is a flat in vienna we can use for guests. ping me or nevvton\_  
<strong>\<sgp\_\></strong> All right, thanks parasew\! Always great to hear about your efforts  
<strong>\<sgp\_\></strong> 5. Open ideas time  
<strong>\<sgp\_\></strong> This meeting is going over an hour to accommodate for open ideas time  
<strong>\<sgp\_\></strong> Feel free to propose your ideas to this discussion group, and feel free to comment on others’ ideas. If you disagree with the idea, please reply with constructive criticism. Thank you\!  
<strong>\<sgp\_\></strong> crickets...  
<strong>\<rehrar\></strong> I have an idea  
<strong>\<rehrar\></strong> to end the meeting  
<strong>\<rehrar\></strong> open for discussion  
<strong>\<sgp\_\></strong> Considering no one is feeling creative today, we can close the meeting  
<strong>\<sgp\_\></strong> 6. Confirm next meeting date/time  
<strong>\<sgp\_\></strong> The next community meeting will be two weeks from today on 14 April. The Coffee Chat will be next Saturday on 7 April.  
<strong>\<sgp\_\></strong> 7. Conclusion  
<strong>\<sgp\_\></strong> That’s all\! Thanks for attending this Monero Community meeting, and we hope to see you on /r/MoneroCommunity and \#monero-community. Take care, and know that change starts with YOU.  
<strong>\<rehrar\></strong> ME?  
<strong>\<sgp\_\></strong> Yes, YOU  
<strong>\<rehrar\></strong> \!\!\!\!\!  
<strong>\<msvb-lab\></strong> sgp\_: Good one this time, last week was no good. Thanks a lot.  
<strong>\<m2049r\[m\]\></strong> and thanks sgp\_ for organizing\!  
<strong>\<msvb-lab\></strong> Last time sgp was not with us == bad time.  
<strong>\<parasew\[m\]\></strong> thanks sgp\_  
<strong>\<rehrar\></strong> ye. whoever ran the last meeting was an idiot  
<strong>\<ErCiccione\></strong> so, sgp\_ i made the workgroup on taiga <https://taiga.getmonero.org/project/erciccione-organization-pre-upgrade/>  
<strong>\<parasew\[m\]\></strong> msvb-lab: are you planning some publicity for the hw-wallet or are you waiting until the proposal is done?  
<strong>\<ErCiccione\></strong> if anyone want to help tracking if pools and exchanges are ready for the next upgrade, contact me or sgp\_ and we will add you on the workgroup  
<strong>\<msvb-lab\></strong> parasew\[m\]: Publicity is good at any time, in fact a radio broadcast featuring us is appearing very soon on BR Bayerische Rundfunk.  
<strong>\<sgp\_\></strong> ErCiccione thanks, do you think we should make separate wiki pages for each type of ecosystem type? Eg: exchanges, pools, service providers, merchants, etc?  
<strong>\<freelikeinfreedo\></strong> \> parasew\[m\]: Publicity is good at any time, in fact a radio broadcast featuring us is appearing very soon on BR Bayerische Rundfunk.  
<strong>\<freelikeinfreedo\></strong> do you know when exactly?  
<strong>\<msvb-lab\></strong> The reporter is still working on slicing up the two (\!) hours of interview.  
<strong>\<msvb-lab\></strong> I have no idea when it will be ready, but I was his last interview so it could come in a couple weeks?  
<strong>\<ErCiccione\></strong> yes, i think that's a good way to do it sgp\_ . do you want to include merchants as well? that would be a looot of people  
<strong>\<sgp\_\></strong> That will be a stretch goal lol  
<strong>\<msvb-lab\></strong> parasew\[m\] pablonero\[m\]: Very nice that so much interest is centered in Vienna, and that you welcome visits like that.  
<strong>\<sgp\_\></strong> Eg: if huge merchants like Amazon took Monero, we would want to know :p  
<strong>\<m2049r\[m\]\></strong> oh - and support my FFS :)  
<strong>\<rehrar\></strong> no  
<strong>\<rehrar\></strong> ArticMine, COS is ideal for the common person since it really works for security.  
<strong>\<rehrar\></strong> I agree that Lineage is better for the enthusiast (people that'd be into Monero)  
<strong>\<rehrar\></strong> but I'd probably recommend COS for people that aren't as versed int his stuff, like family  
<strong>\<m2049r\[m\]\></strong> my understand is that copperhead is for more modern devices, no?  
<strong>\<ArticMine\></strong> I took a good look at COS. The common person run into an issue the moment they do anything commercial  
<strong>\<rehrar\></strong> I've used it, although not super extensively.  
<strong>\<rehrar\></strong> I will defer to you on this.  
<strong>\<ArticMine\></strong> I mean as simple as a kid that mows neighbor's lawn or shovels the neighbor's snow  
<strong>\<ArticMine\></strong> Then there are in violation of the license  
<strong>\<ArticMine\></strong> In my opinion Copperhead did something very stupid. They could have gone with a strong copyleft and avoided this mess  
<strong>\<rehrar\></strong> see, this is why I talk to ou  
<strong>\<rehrar\></strong> \*you  
<strong>\<rehrar\></strong> you have all the licensing knowledge  
<strong>\<ArticMine\></strong> It gets interesting like doing a software audit, to remove pirated proprietary software by replacing it with FLOSS  
<strong>\<ArticMine\></strong> Non commercial clauses is one of my favorites  
<strong>\<rehrar\></strong> consider me learned for this instance  
<strong>\<ArticMine\></strong> I always wonder if the % of GNU/Linux users that have read Windows EULA is greater than the % of Windows users  
<strong>\<sgp\_\></strong> ErCiccione I made the first version of the list but haven't contacted anyone yet  
<strong>\<ErCiccione\></strong> looks perfect sgp\_, what if we make the merchant section input based. We tell people that if they want they can communicate us they have upgraded, then we put them on the list  
<strong>\<sgp\_\[m\]\></strong> I haven't made the merchant list yet., though it could look similar  
<strong>\<ErCiccione\></strong> ah ok, i though was harder to get all the merchants. but now that i think about it we have a list on the website  
<strong>\<sneurlax\></strong> ArticMine, that's why we're GNU/Linux users...  
<strong>\<vp11\></strong> ArticMine, answer is yes in both relative and direct sense.
