---
title: Logs for the Dev Meeting Held on 2019-03-03
summary: March 9th Network Upgrade, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<xmrmatterbridge\> \<rehrar\></strong> 1. Greetings  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Who all is out there?  
<strong>\<rbrunner\></strong> Hoy zäme  
<strong>\<ErCiccione\[m\]\></strong> Hi  
<strong>\<sarang\></strong> Here, partially (in two meetings at once)  
<strong>\<rehrar\></strong> So it's been a while since I led a meeting, but maybe you guys had some in my absence.  
<strong>\<rehrar\></strong> Even so, 2. What's been done since the previous meeting?  
<strong>\<oneiric\_\></strong> o/  
<strong>\<rbrunner\></strong> Don't think so. Last week was no one  
<strong>\<rehrar\></strong> Obviously the release of the CLI and the GUI is upcoming. I think we should kind of skip 2  
<strong>\<rehrar\></strong> or at least switch it  
<strong>\<rehrar\></strong> 2. Fork Items  
<strong>\<rehrar\></strong> Anything anyone wants to talk about regarding the upcoming fork?  
<strong>\<rehrar\></strong> it'd be great if we got fluffypony luigi1111 and moneromooo in here  
<strong>\<moneromooo\></strong> I am here.  
<strong>\<moneromooo\></strong> Not much to say about the fork I think.  
<strong>\<moneromooo\></strong> We're a bit busy atm with an exploit patch to come soon.  
<strong>\<moneromooo\></strong> Some jerk posted about it publicly so we have to release now.  
<strong>\<moneromooo\></strong> pony finishing up the version PR and we can go.  
<strong>\<rehrar\></strong> oof, ok.  
<strong>\<rehrar\></strong> anyone else have something they wanted to discuss regarding the fork? Questions? Comments?  
<strong>\<sgp\_\></strong> hello  
<strong>\<ErCiccione\[m\]\></strong> moneromooo: so, 0.14.0 will include the patch i guess  
<strong>\<hyc\></strong> moneromooo is too polite, "Some jerk" is too subtle  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<sarang\></strong> Was it disclosed non-publicly first somewhere?  
<strong>\<moneromooo\></strong> On H1.  
<strong>\<ErCiccione\[m\]\></strong> alright  
<strong>\<rbrunner\></strong> Someone unrelated?  
<strong>\<oneiric\_\></strong> how long did it sit in h1 before the public asshattery?  
<strong>\<moneromooo\></strong> Well, I wouldn't know, but I think we can fairly assume so since the reporter was very nice and hlepful :)  
<strong>\<rbrunner\></strong> :)  
<strong>\<moneromooo\></strong> I saw it \~3 days after filed. That was... 2 days ago I think.  
<strong>\<oneiric\_\></strong> wow, yeah that is shitty  
<strong>\<moneromooo\></strong> Well, given I have no reason to think the jerk is the reported, that's unrelated.  
<strong>\<kinghat\></strong> what will the subsequent HF release be numbered and has there been talk on its timeline? 1m?  
<strong>\<moneromooo\></strong> \*reporter  
<strong>\<moneromooo\></strong> You mean not the one in a week ? We don't know yet.  
<strong>\<oneiric\_\></strong> true, weird that two independent parties would find the same bugs so close to each other  
<strong>\<moneromooo\></strong> From what I've been told, the jerk knew about it, and was keeping it for reasons unknown.  
<strong>\<kinghat\></strong> ya the one after mar 9  
<strong>\<rbrunner\></strong> The "jerk" stumbled over it a few months ago  
<strong>\<oneiric\_\></strong> ah, then extra shittiness  
<strong>\<rbrunner\></strong> Extra drama :)  
<strong>\<oneiric\_\></strong> seem to know a lot about what the jerk knew, was that disclosed in the public posting?  
<strong>\<moneromooo\></strong> But hey, we need reviewers :) Please, if you're a coder, feel free :)  
<strong>\<moneromooo\></strong> I was told about it like an hour ago...  
<strong>\<moneromooo\></strong> Maybe two.  
<strong>\<oneiric\_\></strong> by?  
<strong>\<moneromooo\></strong> Private.  
<strong>\<oneiric\_\></strong> k  
<strong>\<moneromooo\></strong> (that person might decide to say)  
<strong>\<rbrunner\></strong> <https://github.com/ryo-currency/ryo-currency/blame/f698e11c88be33aaf89c316ac68baa0cb80a9c91/src/cryptonote\_core/blockchain.cpp#L1194>  
<strong>\<fluffypony\></strong> it was posted in \#monero-research-lab by unknownids\_ an hour and a half ago  
<strong>\<moneromooo\></strong> That's pretty much my patch (though that part will go up later, for october).  
<strong>\<rehrar\></strong> and what's the timeline for getting that patch out?  
<strong>\<moneromooo\></strong> (or whenever the next fork is decided to be)  
<strong>\<rehrar\></strong> ASAP?  
<strong>\<moneromooo\></strong> The wallet patch is going out as soon as pony's ready to merge and have a new release.  
<strong>\<fluffypony\></strong> also I don't think fireice\_uk is trying to be a jerk, I think he just cares very much about his altcoin, and he thinks that the only way it succeeds is for Monero to fail, so he bashes Monero every chance he gets. I can totally understand that approach. If I had the same set of facts, and told myself the same stories, then I might also reach the same conclusion.  
<strong>\<fluffypony\></strong> it's probably best if we just leave him to do his thing, mud-slinging in public isn't going to help anything  
<strong>\<oneiric\_\></strong> wounds run deep  
<strong>\<hyc\></strong> note that nobody invited the CN-GPU mudslinging  
<strong>\<hyc\></strong> they threw that into /r/monero all by themselves, twice  
<strong>\<sgp\_\></strong> imo, just remove it and move on  
<strong>\<rbrunner\></strong> It's more like a divorce story between him and us, with a common child still to keep caring fore (CryptoNight technology)  
<strong>\<oneiric\_\></strong> grand censor sgp\_ to the rescue  
<strong>\<hyc\></strong> since the vuln is now totally public why not also patch monerod now?  
<strong>\<moneromooo\></strong> Because it'd be a consensus change there.  
<strong>\<moneromooo\></strong> And lots of people are not going to update in time.  
<strong>\<rbrunner\></strong> But itsn't the whole think clearly consensus abuse?  
<strong>\<rbrunner\></strong> \*thin  
<strong>\<rbrunner\></strong> \*thing  
<strong>\<moneromooo\></strong> Not really.  
<strong>\<moneromooo\></strong> It's a bit of a grey area here I think.  
<strong>\<rbrunner\></strong> Ok  
<strong>\<moneromooo\></strong> It can be consensus rejected, since there's no good reason to allow it. And will be later.  
<strong>\<fluffypony\></strong> it's trivially done as a soft-fork  
<strong>\<fluffypony\></strong> (since, as long as miners don't mine these coinbases, they don't exist)  
<strong>\<rehrar\></strong> well all of this is a bummer anyhow. thank you moneromooo for being on top of this and working on it so quickly  
<strong>\<moneromooo\></strong> Are you saying you'd rather add the daemon side of the patch now too ?  
<strong>\<moneromooo\></strong> Thanks to the reporter too, the report was very clear and detailed :)  
<strong>\<fluffypony\></strong> moneromooo: no, we don't really have a soft-fork voting system in place, so more engineering effort than it's worth right now  
<strong>\<moneromooo\></strong> k  
<strong>\<hyc\></strong> if the binaries are going to be available ASAP, why not. we still have 1 week to go.  
<strong>\<fluffypony\></strong> hyc: I don't think it's a good idea this close to the fork, especially since it's trivially patched at the wallet level  
<strong>\<hyc\></strong> ok  
<strong>\<rehrar\></strong> so just roll this in with 0.1 along with a lot of the other big upgrades, which should get most people to upgrade?  
<strong>\<moneromooo\></strong> BTW, once it's patched, if many people can rescan their wallets and make sure all is A-OK, that'd be great :)  
<strong>\<moneromooo\></strong> Since this is so close etc.  
<strong>\<ErCiccione\[m\]\></strong> could it be included in next release? people aleady know it's about too happen and should be soon enough.  
<strong>\<fluffypony\></strong> rehrar: we don't have a soft fork mechanism in place right now, and I don't think it's worth the engineering effort between now and the 0.14.1 release  
<strong>\<fluffypony\></strong> I totally support adding such a mechanism for future things  
<strong>\<rehrar\></strong> so then we're playing this by ear then? Or can you elaborate on the process?  
<strong>\<moneromooo\></strong> Soft fork just means people on the wrong side get orphaned and it stil works, right ? So no need for any further code ?  
<strong>\<rehrar\></strong> basically, how will this patch practically get out to the masses?  
<strong>\<rehrar\></strong> what's the timeline?  
<strong>\<fluffypony\></strong> moneromooo: you need the fork to activate once some threshold of miners are voting to say they are ready for the new minor version  
<strong>\<fluffypony\></strong> rehrar: it'll be part of 0.14.0.1, which will be the version included with the GUI  
<strong>\<fluffypony\></strong> and will be the point release we'll put out ASAP  
<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> understood, thank you.  
<strong>\<rbrunner\></strong> So the GUI will arrive a few days later than planned, I guess?  
<strong>\<fluffypony\></strong> rbrunner: yes  
<strong>\<rbrunner\></strong> No problem yet  
<strong>\<rehrar\></strong> is there anyone from the GUI here? dEBRUYNE? medusa\_?  
<strong>\<rehrar\></strong> dsc\_?  
<strong>\<ErCiccione\[m\]\></strong> or selsta  
<strong>\<ErCiccione\[m\]\></strong> AFAIK GUI is tagged and ready to be built  
<strong>\<selsta\></strong> yes  
<strong>\<rehrar\></strong> yeah, I'd just like to hear a mini-report if someone wanted to give it  
<strong>\<rehrar\></strong> it can get into the meeting logs and normies can review them alter for funsies  
<strong>\<selsta\></strong> <https://github.com/monero-project/monero-gui/releases/tag/v0.14.0.0>  
<strong>\<ErCiccione\[m\]\></strong> most important thing is that looks and feels great  
<strong>\<ErCiccione\[m\]\></strong> the new wizards and mode are great  
<strong>\<rehrar\></strong> ok, great  
<strong>\<ErCiccione\[m\]\></strong> you can get the binaries from buildbot in my last PR, which was the last one with all the translations  
<strong>\<ErCiccione\[m\]\></strong> <https://github.com/monero-project/monero-gui/pull/1991>  
<strong>\<rbrunner\></strong> Nice  
<strong>\<rehrar\></strong> Was there any other comments about the lead up to this fork at all? GUI? CLI? Testing? Other?  
<strong>\<selsta\></strong> sorry, I’m kinda busy. Basically what ErCiccione\[m\] said. Release notes that I posted above are a good overview of what’s new.  
<strong>\<rehrar\></strong> Ok.  
<strong>\<rehrar\></strong> is needmoney90 around? He wanted this meeting and had something to say, as I recall  
<strong>\<needmoney90\></strong> Hey there  
<strong>\<rehrar\></strong> ^ this kid  
<strong>\<needmoney90\></strong> tat: you there?  
<strong>\<oneiric\_\></strong> ...  
<strong>\<needmoney90\></strong> The kraken Dev was supposed to be here, but I may have missed mentioning it  
<strong>\<needmoney90\></strong> I believe they were all on board though  
<strong>\<needmoney90\></strong> After chatting  
<strong>\<needmoney90\></strong> So it may not be necessary  
<strong>\<rehrar\></strong> ok, well  
<strong>\<rehrar\></strong> If there's nothing else, I think we can conclude here.  
<strong>\<rehrar\></strong> Should we have another informal meeting next week after the fork occurs, just in case?  
<strong>\<tat\></strong> @needmoney90 i am here  
<strong>\<oneiric\_\></strong> hats will be on fire, grab the buckets rehrar  
<strong>\<needmoney90\></strong> Oh perfect  
<strong>\<rehrar\></strong> ok, ceding the floor again to tat and needmoney90 real fast  
<strong>\<moneromooo\></strong> (I'll have one more point actually when they're done)  
<strong>\<needmoney90\></strong> Tat, for the logs, let's talk quickly about the timeline for payment ID deprecation, and Kraken's needs here  
<strong>\<rehrar\></strong> ok, sure  
<strong>\<needmoney90\></strong> Difficulty of implementation, how long you feel is reasonable before deprecating, etc  
<strong>\<sgp\_\></strong> expect a Github issue from me soon-ish on how to handle public pool output selection in the wallet. I expect this to be non-controversial, but keep an eye out for the discussion  
<strong>\<sgp\_\></strong> this would only apply for the public pool wallet specifically  
<strong>\<needmoney90\></strong> We don't want to rush the deprecation, but improving privacy is one of our primary goals, and we cannot wait forever  
<strong>\<tat\></strong> well, i think going to deprecate them by the fork in october is very reasonable, and informing people about clear decisions 6 month ahead would be great also from a users perspective, to make the transformation as smooth as possible  
<strong>\<moneromooo\></strong> Is that about short or long ones ?  
<strong>\<tat\></strong> i will say both, if you guys go for that, either way, 6 month is a good window  
<strong>\<sarang\></strong> Also please be very clear about wallet deprecation vs something like a consensus ban  
<strong>\<rehrar\></strong> have you guys toyed with the idea of moving to subaddresses?  
<strong>\<sarang\></strong> The talk about \_how\_ to wallet-deprecate in GUI and CLI has also been more contentious than I had expected  
<strong>\<rbrunner\></strong> There is nothing else to move to, no?  
<strong>\<moneromooo\></strong> Long ones have been warned about since last fork in the wallet.  
<strong>\<moneromooo\></strong> So it's deprecated in my book :)  
<strong>\<moneromooo\></strong> So yes, clear definitions will help.  
<strong>\<sgp\_\></strong> moneromooo: yes, long are "soft" non-consensus deprecated with the 0.14 update. Moreso than before  
<strong>\<sarang\></strong> Some argued that "deprecated" in GUI should mean "only available via a special flag or crazy advanced option", but others said it should mean "available by a simple toggle on a main page"  
<strong>\<sarang\></strong> IMO the latter option is not a deprecation at all  
<strong>\<sgp\_\></strong> the latter is what MyMonero and others do  
<strong>\<moneromooo\></strong> Well, you can't run: firefox --long-payment-id-support so... :)  
<strong>\<fluffypony\></strong> not yet  
<strong>\<needmoney90\></strong> When Firefox partnership  
<strong>\<sarang\></strong> If it's easy to use, then we really haven't deprecated anything  
<strong>\<dEBRUYNE\></strong> fluffypony: As a side note, did you start the GUI builds already?  
<strong>\<sarang\></strong> saying "plz don't use" is what we have already  
<strong>\<fluffypony\></strong> dEBRUYNE: yes, but I killed them already when this came out  
<strong>\<fluffypony\></strong> s/came out/was disclosed  
<strong>\<sgp\_\></strong> sarang: I think we should focus on consensus deprecation. The other wallets are mostly out of our control  
<strong>\<sarang\></strong> I also support (at least temporary) consensus ban, but I know this is not a popular opinion  
<strong>\<dEBRUYNE\></strong> Because you want them to include the fix or?  
<strong>\<dEBRUYNE\></strong> The fork is only 6 days away and presumably the fix won't be posted until 6 march  
<strong>\<dEBRUYNE\></strong> Add to that 1 day of building  
<strong>\<dEBRUYNE\></strong> We can't release a binary 2 days in advance imo  
<strong>\<rbrunner\></strong> I think the fix is "ASAP" now  
<strong>\<rbrunner\></strong> After that very public disclosure  
<strong>\<rbrunner\></strong> And nice explanation how to exploit :)  
<strong>\<moneromooo\></strong> The fix is up. 521\[67\]  
<strong>\<fluffypony\></strong> plz review  
<strong>\<rehrar\></strong> coo'  
<strong>\<moneromooo\></strong> I'll have to be out for like 40 minutes maybe. Please test (ie, rescan\_bc), and let me know if anything breaks.  
<strong>\<rehrar\></strong> moneromooo, you said you had something real quick, yeah?  
<strong>\<moneromooo\></strong> Yes:  
<strong>\<moneromooo\></strong> for some time now, guidov has been asking me about the new FFS, and I've been giving the poor guy the old runaround, with "it's ready, just needs to be pushed to live".  
<strong>\<moneromooo\></strong> (sorry guidov :P)  
<strong>\<rehrar\></strong> I have set up a meeting with Shay to meet with fluffypony tomorrow and finish this up  
<strong>\<moneromooo\></strong> He's offering to make new fuzz tests and have them run on google infrastructure.  
<strong>\<rehrar\></strong> it is semi-live right now and you can view it at ccs.getmoenro.org  
<strong>\<sarang\></strong> I noticed an HTTP link to the CCS wasn't redirected  
<strong>\<binaryFate\></strong> moenro ftw  
<strong>\<fluffypony\></strong> Mo-Enro  
<strong>\<moneromooo\></strong> I think this would be a very good thing because the only fuzz tests we have are the ones I've written, and they're not routinly run. And I'm not a fuzz test master at all.  
<strong>\<rehrar\></strong> there's just one bug with the generation of the donation pages being a little funky, and that requires access to the server, which only pony does  
<strong>\<rehrar\></strong> hopefully we can work that out by tomorrow  
<strong>\<rehrar\></strong> Be warned Ricarrrod, I have you tomorrow for a bit  
<strong>\<moneromooo\></strong> He also said he could do the fuzz tests for free, but report anything they find to H1 for bounties.  
<strong>\<dEBRUYNE\> \<rbrunner\></strong> I think the fix is "ASAP" now \<= If the fix is about to be reviewed + merged soon I guess it is okay  
<strong>\<dEBRUYNE\></strong> fluffypony: will you resume GUI builds once the fix is merged into the branch?  
<strong>\<rehrar\></strong> a thousand apologies for the delay moneromoooo  
<strong>\<moneromooo\></strong> So what to do is community preference, but having comprehensive fuzz tests running all the time would be great IMHO.  
<strong>\<moneromooo\></strong> I just wanted it out before he gets bored and walks away ^\_^  
<strong>\<binaryFate\></strong> yes we want we want  
<strong>\<rehrar\></strong> I say if tomorrow proves to be a bust for some reason, then have him do H1  
<strong>\<fluffypony\></strong> dEBRUYNE: no, I have to build binaries  
<strong>\<fluffypony\></strong> for CLI  
<strong>\<rehrar\></strong> if tomorrow is not a bust (fingers crossed) then you believe me, I will be screaming to every Monero IRC chat channel that it's live  
<strong>\<rehrar\></strong> so people will leave me alone :D  
<strong>\<moneromooo\></strong> For the record, he's already postred a H1 report, which is all fixed, but unreleased yet, because it'll be after the fork (no consensus bug, no money poppoing up in wallets, etc, don't worry).  
<strong>\<sarang\></strong> Is there a mechanism in place to prevent DoS generation of subaddresses?  
<strong>\<moneromooo\></strong> Not really.  
<strong>\<sarang\></strong> OK, we should expect such a thing then  
<strong>\<moneromooo\></strong> Feel free to file a bug about it's not forgot.  
<strong>\<sgp\_\></strong> tat: can you speak to what the upgrade timeline for you to move to subaddresses looks like?  
<strong>\<dEBRUYNE\></strong> fluffypony: Ok, could you give me a timeline on the GUI though?  
<strong>\<fluffypony\></strong> dEBRUYNE: as soon as the CLI bins are out I can start on the GUI bins  
<strong>\<fluffypony\></strong> re-start  
<strong>\<dEBRUYNE\></strong> All right  
<strong>\<dEBRUYNE\></strong> ty  
<strong>\<rehrar\></strong> bye moneromooo  
<strong>\<moneromooo\></strong> (yes, I tested it too)  
<strong>\<rehrar\></strong> and unless anyone has anythign else, we can call it here  
<strong>\<rehrar\></strong> discussion can, of course, continue to take place  
<strong>\<rehrar\></strong> informal meeting next week  
<strong>\<rehrar\></strong> just to check up on fork stuff progress  
<strong>\<rehrar\></strong> thanks for coming everyone. Have nice lives.
