---
title: Overview and Logs for the Dev Meeting Held on 2018-02-11
summary: Discussion of open PRs and issues, Bulletproofs and auditing, March HF, slight PoW tweak, dedicated Monero hardware wallet, and miscellaneous
tags: [dev diaries, core, crypto]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<rehrar\></strong> ArticMine luigi1111 luigi1111w fluffypony smooth hyc moneromooo anonimal vtnerd pigeons endogenic ErCiccione  
<strong>\<vtnerd\></strong> present  
<strong>\<ArticMine\></strong> Hi  
<strong>\<msvb-mob\></strong> Hello.  
<strong>\<ErCiccione\></strong> hi folks  
<strong>\<vtnerd\></strong> jtgrassie  
<strong>\<sgp\></strong> Hi  
<strong>\<rehrar\></strong> Agenda: <https://github.com/monero-project/meta/issues/174>  
<strong>\<rehrar\></strong> Jaquee medusa dsc  
<strong>\<rehrar\></strong> kenshi84 MoroccanMalinois anyone else?  
<strong>\<MoroccanMalinois\></strong> hi  
<strong>\<rehrar\></strong> We’ve already kind of start on 1. Greetings  
<strong>\<rehrar\></strong> If you’re still hanging out in the peanut gallery, throw a hello on by to us.  
<strong>\<rehrar\></strong> Heck, if you don’t plan on participating, but just want to watch, we’d still appreciate a hello. :)  
<strong>\<Vespco\></strong> Hello  
<strong>\<endogenic\></strong> hello  
<strong>\<endogenic\></strong> this is dog  
<strong>\<rehrar\></strong> As you guys probably see, it’s not 17 UTC. We’re trying out an hour earlier by request of last meeting. We can decide today whether it was a good idea or not.  
<strong>\<pigeons\></strong> hi  
<strong>\<rehrar\></strong> suraeNoether sarang  
<strong>\<rehrar\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<rehrar\></strong> Anyone have anything to report?  
<strong>\<moneromooo\></strong> DB crash fix. Misc minor fixes found by coverity. Pool max size. Fluffy blocks on by default. I think that’s the main ones.  
<strong>\<moneromooo\></strong> And I just PR’d my “store prunable and unprunable data separately” patch.  
<strong>\<moneromooo\></strong> Oh, and the —testnet-xxx options are gone now. No more duplication.  
<strong>\<moneromooo\></strong> None of that is merged yet, but nothing got merged in two weeks I think.  
<strong>\<rehrar\></strong> Thanks moneromooo\! You are a shining star. Take a bow.  
<strong>\<rehrar\></strong> Anyone else have anything to report? If not we can move on.  
<strong>\<moneromooo\></strong> Not all by me.  
<strong>\<vtnerd\></strong> I guess I will report for jtgrassie, who looked at the echo off permanently issue with the wallet  
<strong>\<rehrar\></strong> a bow for your presentation ;)  
<strong>\<vtnerd\></strong> he has a fix that is similar to moneromooo ‘s patch, but does trigger immediate shutdown on ctrl-c still  
<strong>\<luigi1111\></strong> Does that need a resync?  
<strong>\<vtnerd\></strong> there are still underlying issues in the signal handler, and if I can’t figure out a way to unbreak that code easily we may have to go with the somewhat-hack approach until that gets worked out  
<strong>\<iDunk\></strong> luigi1111: It will convert the db from v1 to v2, AFAIU.  
<strong>\<moneromooo\></strong> no resync  
<strong>\<luigi1111\></strong> Perfect  
<strong>\<vtnerd\></strong> and I’m still interested in wallet scanning perf (as usual), and figure out how to do atomic swapping … if anyone has thoughts on the latter let me know privately for now  
<strong>\<vtnerd\></strong> or what this is the whats been completed section, whoops  
<strong>\<endogenic\></strong> i have a question for later rehrar  
<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> Alright, we ready to push forward?  
<strong>\<sarang\></strong> Hullo, sorry for delay, was filing taxes :/  
<strong>\<rehrar\></strong> Any dev stuff to report for the last two weeks?  
<strong>\<rehrar\></strong> sarang ^  
<strong>\<sarang\></strong> It’s just about the most fun you can have while still wearing pants  
<strong>\<sarang\></strong> Yes, a few quick thing  
<strong>\<sarang\></strong> The BP paper was massively updated to reflect a lot of the optimizations we’ve been including  
<strong>\<sarang\></strong> I’m running final checks against that paper (and made a few corrections to the updated paper that have been sent to the authors)  
<strong>\<moneromooo\></strong> Oh good point, I forgot about more BP stuff ^\_^  
<strong>\<sarang\></strong> I had also worked up a BP technical note, but the paper update makes that obsolete  
<strong>\<endogenic\></strong> mooo same  
<strong>\<sarang\></strong> However, I think we’ve made all the optimizations that we want  
<strong>\<sarang\></strong> On the audit front, OSTIF groups are slow to provide SoW but apparently that’s happening early this week  
<strong>\<sarang\></strong> Benedikt Buenz (BP author) wants to review as well  
<strong>\<sarang\></strong> Thoughts on how much to offer Benedikt?  
<strong>\<sarang\></strong> Having both him and an audit group review will be good: he’ll confirm our math, and the audit group will check our final code for holes  
<strong>\<rehrar\></strong> Make him an offer he can’t refuse  
<strong>\<sarang\></strong> lol  
<strong>\<sgp\></strong> I don’t really know what the right amount is  
<strong>\<endogenic\></strong> no pony heads though pls  
<strong>\<sarang\></strong> I’m thinking a rate of 800 USD per day would be competitive if it only takes him \~5 days or so  
<strong>\<sarang\></strong> He’s the most qualified person to do this  
<strong>\<endogenic\></strong> then that’s cheap  
<strong>\<endogenic\></strong> we’re lucky  
<strong>\<ErCiccione\></strong> that’s less than i expected  
<strong>\<sarang\></strong> Yeah, I’d go higher if no objections  
<strong>\<sarang\></strong> I asked what his rate is, and am waiting to hear back  
<strong>\<ArticMine\></strong> It is on the low end  
<strong>\<endogenic\></strong> well ErCiccione do keep in mind we benefit from addtl reviewers  
<strong>\<endogenic\></strong> so frugality is useful there  
<strong>\<rehrar\></strong> 20 XMR bam  
<strong>\<sarang\></strong> So I’ll do a combined FFS once we’ve confirmed the OSTIF rate and Benedikt’s rate  
<strong>\<endogenic\></strong> thanks sarang :)  
<strong>\<sarang\></strong> Separarely, I’ve been working with suraeNoether on some multisig developments from BPASE  
<strong>\<sarang\></strong> curriculum development for 3-week summer course  
<strong>\<sarang\></strong> Will be speaking at a Portland crypto conference about privacy (funded by the organizers, no FFS needed)  
<strong>\<sarang\></strong> and the paper on PHANTOM (related to SPECTRE) just came out, so I’m on top of that  
<strong>\* sarang</strong> is done talking now  
<strong>\<rehrar\></strong> woohoo, sounds awesome  
<strong>\<sarang\></strong> questions welcome  
<strong>\<endogenic\></strong> awesome  
<strong>\<sarang\></strong> read the new BP paper if it interests you  
<strong>\<rehrar\></strong> alright let’s jump into the big one: 3. March hardfork items + code freeze  
<strong>\<rehrar\></strong> So… code freeze has been “close” for a couple months now  
<strong>\<rehrar\></strong> when is it? :P  
<strong>\<moneromooo\></strong> When we pushed all we need,  
<strong>\<moneromooo\></strong> We need pony back, so we can’t discuss this if we don’t know that.  
<strong>\<moneromooo\></strong> One thing we need to discuss before we do though:  
<strong>\<moneromooo\></strong> We discussed changing PoW slightly, and periodically, in order to further our goal of decentralization - to deter ASIC creation some more.  
<strong>\<moneromooo\></strong> So we’re planning to change PoW before the fork, if the community agrees.  
<strong>\<rehrar\></strong> before March?  
<strong>\<moneromooo\></strong> Yes. We’re still planning on a march fork.  
<strong>\<pigeons\></strong> i would expect changing the PoW before this fork to be at least slightly controversial  
<strong>\<rehrar\></strong> This seems a bit sudden and soon  
<strong>\<moneromooo\></strong> Emphasis on <em>slightly</em> btw. It’s still mostly Cryptonight.  
<strong>\<rehrar\></strong> ah, makes more sense  
<strong>\<sgp\></strong> I would like to hear a lot more about the changes and what they mean  
<strong>\<rehrar\></strong> ^  
<strong>\<rehrar\></strong> can you explain moneromooo?  
<strong>\<endogenic\></strong> what deters ASICs?  
<strong>\<ErCiccione\></strong> sgp: +1  
<strong>\<iDunk\></strong> Is this about the parameters tweaks othe suggested ?  
<strong>\<pigeons\></strong> endogenic: having the work and investment they put in invalidated  
<strong>\<moneromooo\></strong> Just a few more simple ops in the inner loop. They mean… different hashes.  
<strong>\<endogenic\></strong> pigeons: how to detect their work?  
<strong>\<ArticMine\></strong> It keeps ASIC developers off balance  
<strong>\<endogenic\></strong> or what is it :p  
<strong>\<moneromooo\></strong> endogenic: it doesn’t need to. I have patches for most miners ready.  
<strong>\<moneromooo\></strong> Those (software) miners just update. Any ASIC can’t.  
<strong>\<endogenic\></strong> even if it’s modular?  
<strong>\<moneromooo\></strong> What is a modular ASIC ?  
<strong>\<endogenic\></strong> it -\> asic  
<strong>\<msvb-mob\></strong> pigeons moneromooo: We in the hardware team are onboard with PoW changes but cannot recall all hardware wallets worldwide to swap chips.  
<strong>\<endogenic\></strong> modular hardware  
<strong>\<moneromooo\></strong> You have hardware mining ?  
<strong>\<pigeons\></strong> msvb-mob: I wouldn’t expect hardware wallets to need to mine or validate PoW  
<strong>\<msvb-mob\></strong> Not to make the debate a can of worms, but if anybody has a strategy idea for us hardware folks, let’s please consider the probloem offline.  
<strong>\<pigeons\></strong> just sign i would think  
<strong>\<rehrar\></strong> msvb-mob, why does a hardware wallet need to do anything with PoW?  
<strong>\<msvb-mob\></strong> pigeons: Okay, but changing the Cryptonote PoW wouldn’t that mean changing transaction operations as well?  
<strong>\<moneromooo\></strong> No.  
<strong>\<pigeons\></strong> transactions don’t use PoW  
<strong>\<pigeons\></strong> bundling them in blocks do  
<strong>\<msvb-mob\></strong> pigeons rehrar moneromooo: Okay, that’s the answer I wanted to hear, thanks.  
<strong>\<rehrar\></strong> you sign the tx and broadcast them to the network, then the miners (separate entities) mine and put them in blocks  
<strong>\<rehrar\></strong> so you’re good, unaffected :)  
<strong>\<rehrar\></strong> well then, it seems we don’t have a lot to discuss on point 3 without the horsey  
<strong>\<rehrar\></strong> seeing as how Core Team has more or less delegated to him to handle releases and stuff  
<strong>\<rehrar\></strong> though I hope he may show up soon, as…it’s getting close to March  
<strong>\<rehrar\></strong> Any final thoughts on 3?  
<strong>\<endogenic\></strong> we could just ask him lol  
<strong>\<endogenic\></strong> that usually works  
<strong>\<moneromooo\></strong> I did. It didn’t.  
<strong>\<endogenic\></strong> “we” :p  
<strong>\<luigi1111\></strong> He should be home by now  
<strong>\<moneromooo\></strong> Might still think 5 GMT though.  
<strong>\<endogenic\></strong> fluffypony:  
<strong>\<rehrar\></strong> I let him know yesterday about the time change  
<strong>\<moneromooo\></strong> Did he reply ? He’s been mostly AFK for days.  
<strong>\<rehrar\></strong> and he responded. Got the message.  
<strong>\<rehrar\></strong> “ok cool”  
<strong>\<rehrar\></strong> we can break that down and analyze that sentence if we want  
<strong>\<rehrar\></strong> Alright, maybe he’ll show up and we can come back to this  
<strong>\<rehrar\></strong> meantime, let’s move on to 4. Code + ticket discussion / Q &amp; A  
<strong>\<endogenic\></strong> ooh me me  
<strong>\<rehrar\></strong> go endogenic  
<strong>\<endogenic\></strong> no sorry my mistake  
<strong>\<endogenic\></strong> ticket discussion first?  
<strong>\<endogenic\></strong> i would step on that otherwise  
<strong>\<rehrar\></strong> yeah, if you don’t mind. Next is ‘any other meeting items’  
<strong>\<rehrar\></strong> and you can go crazy there :)  
<strong>\<endogenic\></strong> well i thought it was q&amp;a but yeah  
<strong>\<rehrar\></strong> ah, I see. I thought it was unrelated.  
<strong>\<rehrar\></strong> <em>shrug</em> for lack of other people piping up with discussion, go ahead  
<strong>\<endogenic\></strong> hah ok  
<strong>\<endogenic\></strong> so i want to beef up our code review capabilities  
<strong>\<endogenic\></strong> the reason is that i found some code got merged without it really having been verified  
<strong>\<endogenic\></strong> which in some cases is necessary  
<strong>\<endogenic\></strong> i mean it’s not in everyone’s interest to verify every single special case code branch  
<strong>\<endogenic\></strong> except  
<strong>\<endogenic\></strong> when it becomes a problem for the codebase  
<strong>\<endogenic\></strong> problem is  
<strong>\<endogenic\></strong> we cant just say “who is the best reviewer… vtnerd… you are now responsible for reviewing all code”  
<strong>\<endogenic\></strong> first no one man can take responsibility for that  
<strong>\<endogenic\></strong> for everyone  
<strong>\<endogenic\></strong> second what if something happens .. bus effect etc  
<strong>\<endogenic\></strong> so i wanted to ask. can we figure out a system for this? like sarang’s work but we must understand imho he has to be involved to vet the vetter  
<strong>\<endogenic\></strong> or it would be the blind leading the blind  
<strong>\<endogenic\></strong> in a manner of speaking  
<strong>\<moneromooo\></strong> You just need people to review, don’t you. So review, or find people to review.  
<strong>\<endogenic\></strong> no  
<strong>\<moneromooo\></strong> To the first part ?  
<strong>\<rehrar\></strong> It’s tough on an open source project. People do many stuff in their free time and aren’t getting paid. Perhaps it would be beneficial to get an FFS proposal by some volunteer coders (two or three) to review all PRs?  
<strong>\<endogenic\></strong> basically. but to both… it is not able to be the solution  
<strong>\<ErCiccione\></strong> i think the problem here is the same the GUI has. We need more people…  
<strong>\<endogenic\></strong> we have people  
<strong>\<endogenic\></strong> they exist  
<strong>\<endogenic\></strong> do they have the incentives?  
<strong>\<rehrar\></strong> this is true  
<strong>\<endogenic\></strong> rehrar sort of in that direction  
<strong>\<endogenic\></strong> but there needs to be a mediator who is technically qualified imo  
<strong>\<endogenic\></strong> and there are other problems  
<strong>\<endogenic\></strong> vtnerd just pinged me privately with one  
<strong>\<endogenic\></strong> imo we have to sort of standardize the effort  
<strong>\<endogenic\></strong> working group?  
<strong>\<endogenic\></strong> that’s one part  
<strong>\<vtnerd\></strong> whoa, standardize? not something I would make claims to. I’ve never seen an effective way to do that  
<strong>\<endogenic\></strong> that’s not what i mean  
<strong>\<rehrar\></strong> what we also need to realize and people and incentives, is that throwing money at people doesn’t always make them want to do something  
<strong>\<rehrar\></strong> If they work full time, they may not want to come home and be obligated to continue working (as opposed to contributing when they want)  
<strong>\<endogenic\></strong> we ourselves already have the right incentives  
<strong>\<endogenic\></strong> but disinterested parties may just gloss over lines of code  
<strong>\<endogenic\></strong> which look innocent  
<strong>\<endogenic\></strong> when i say standardize i mean we should take the fact that such problems exist and make them visible to the community  
<strong>\<vtnerd\></strong> ahh ok, interesting.  
<strong>\<rehrar\></strong> Well, there is a Skepticism Sunday going on right now  
<strong>\<endogenic\></strong> no  
<strong>\<endogenic\></strong> we want a working group with a document of problems that happen such as what i mentioned above  
<strong>\<rehrar\></strong> Ah, I see.  
<strong>\<rehrar\></strong> Would you be willing to head this group then?  
<strong>\<endogenic\></strong> i cant rn  
<strong>\<rehrar\></strong> Well, you and I can talk later after the meeting, and I’ll see what I can do.  
<strong>\<endogenic\></strong> vtnerd might be  
<strong>\<endogenic\></strong> he is an expert  
<strong>\<rehrar\></strong> I’ll be down to give whatever help I can to whoever heads up this group.  
<strong>\<endogenic\></strong> and he\*  
<strong>\<endogenic\></strong> i appreciate that :)  
<strong>\<rehrar\></strong> I think everyone agrees that more thorough review of the code can only be a good thing, it’s just a matter of people, time, and actually getting it done  
<strong>\<rehrar\></strong> Alright, msvb-mob wanted some time for a few hardware things if that’s ok with everyone.  
<strong>\<msvb-mob\></strong> Yes please, but just short.  
<strong>\<rehrar\></strong> floor is yours  
<strong>\<msvb-mob\></strong> I’ll be advertising planning work for the Las Vegas events of August once in a while, anyone interested can look at:  
<strong>\<msvb-mob\></strong> <https://taiga.getmonero.org/project/michael-vegas-august-2018>  
<strong>\<msvb-mob\></strong> m2049r\[m\] made a more or less incredible contribution to the greater Monero community by a first release (today) of a Monerujo-hw firmware.  
<strong>\<msvb-mob\></strong> <https://github.com/m2049r/monerujo-hw/>  
<strong>\<rehrar\></strong> woohoo\!  
<strong>\<msvb-mob\></strong> We want to do the most we can with the firmware (on our own self grown hardware) and a few questions are arising about how far we can take a testnet approach to new users.  
<strong>\<msvb-mob\></strong> New hardware users, that is. Since we can’t recommend using the wallet for real funds.  
<strong>\<msvb-mob\></strong> So if it would be okay to recommend trading testnet funds for a free t-shirt at events, for example.  
<strong>\<msvb-mob\></strong> The last question on my agenda, is if anybody knows of the chance to insert a hardware wallet request to the group making videos (Savandra.)  
<strong>\<msvb-mob\></strong> That’s all for me.  
<strong>\<msvb-mob\></strong> fluffypony focused discussion on a vulnerability mitigation group last meeting, is that a topic we want to follow up on?  
<strong>\<ArticMine\></strong> Yes  
<strong>\<msvb-mob\></strong> ArticMine: Yes to which question?  
<strong>\<ArticMine\></strong> To the vulnerability mitigation group  
<strong>\<rehrar\></strong> As far as I know, savandra’s last video is focusing on the community and that ends his FFS. We can ask him if he’d be willing to do another FFS to make another video for Hardware.  
<strong>\<rehrar\></strong> alright, any last minute meeting items?  
<strong>\<rehrar\></strong> alright, next meeting time  
<strong>\<moneromooo\></strong> No talk about the vulnerability mitigation group ?  
<strong>\<rehrar\></strong> oh, sorry. I may have misread all that  
<strong>\<rehrar\></strong> I thought it was a simple question/answer  
<strong>\<rehrar\></strong> To follow up on that topic, the Vulnerabliity Mitigation Group is headed by sgp and is on mattermost  
<strong>\<moneromooo\></strong> What does this do ?  
<strong>\<rehrar\></strong> sgp, you around?  
<strong>\<moneromooo\></strong> Try to devise workarounds till a fix is in, etc ?  
<strong>\<sgp\></strong> Yeah, but are you sure this is the same? Ours is the “malware response workgroup”  
<strong>\<rehrar\></strong> I think…this is the same, yes.  
<strong>\<rehrar\></strong> But…maybe not? :P  
<strong>\<ArticMine\></strong> It is a different issue  
<strong>\<rehrar\></strong> then disregard me completely  
<strong>\<rehrar\></strong> who is qualified to speak on that?  
<strong>\<msvb-mob\></strong> sgp: The ‘malware response workgroup’ is what I meant when contorting the words above.  
<strong>\<sgp\></strong> The scope of “my” workgroup is to help those whose computers have been exploited for mining or ransomware  
<strong>\<msvb-mob\></strong> sgp: Sounds like most primary things about the workgroup have been decided then, good work.  
<strong>\<endogenic\></strong> sgp: i’ve been curious about the personal network security consequences of operating a monero node too. would be nice to talk with you about that sometime  
<strong>\<rehrar\></strong> Alright. We’re over the designated time. So let’s confirm next day:  
<strong>\<rehrar\></strong> February 25th. Did this new time work for people?  
<strong>\<rehrar\></strong> we were short dEBRUYNE and gingeropolous today. :’(  
<strong>\<rehrar\></strong> but it may be for other reasons  
<strong>\<rehrar\></strong> We can keep 16 UTC for next meeting unless there are great objections.  
<strong>\<rehrar\></strong> If not, meeting over. :) Thanks everyone for coming.  
<strong>\<ArticMine\></strong> I would suggest also keeping it through the time changes  
<strong>\<msvb-mob\></strong> rehrar: Most excellent moderation, thank you.  
<strong>\<sgp\></strong> Not really meeting-worthy, but I would like to add the Monero Coffee Chats to the getmonero website  
<strong>\<msvb-mob\></strong> rehrar: If possible, would you please fork and pull request your source logos to the /documents/graphics/logo/ directory?  
<strong>\<msvb-mob\></strong> rehrar: Logo sources, as long as their formats are Opensource we don’t need bitmaps.  
<strong>\<rehrar\></strong> Ok, I’ll get to that as soon as I can  
<strong>\<sgp\></strong> Are people against me uploading compressed versions of the coffee chats to the site? Or are people concerned they will be too large  
<strong>\<rehrar\></strong> an hour is kind of long and would make having a fork on your local machine a big pain  
<strong>\<rehrar\></strong> especially as there will be more and more of them  
<strong>\<rehrar\></strong> Perhaps links would be better?  
<strong>\<msvb-mob\></strong> sgp: Same consideration we have with large promotional photos of PCBs, which don’t belong in revision control for obvious reasons.  
<strong>\<vtnerd\></strong> articmine : canada does that crap too (arbitary timezone changes)?  
<strong>\<vtnerd\></strong> ahh they do too, I hate timezones altogether actually, as stated previously  
<strong>\<sgp\></strong> @rehrar does the website allow me to embed YouTube videos, or would I have to do a simple link?  
<strong>\<ArticMine\></strong> Different countries do it at different times in the year . Even within a country there a all sorts of differences  
<strong>\<ArticMine\></strong> So for something where there are people all over the world it is best to stick with one time at UTC  
<strong>\<rehrar\></strong> I don’t see why not an embedded video  
<strong>\<rehrar\></strong> except that people with javascript shut down won’t be able to see it  
<strong>\<rehrar\></strong> I think we should keep the website free from the necessity to turn on Javascript for anything, so I would advocate for a link, but that’s just me.
