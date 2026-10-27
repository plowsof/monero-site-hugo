---
title: Logs for the GUI Meeting Held on 2019-04-23
summary: Pending PRs, Issues, past week development, coming week development and miscellaneous
tags: [gui, dev diaries]
author: el00ruobuob / dsc
---

# Logs

<strong>\<dsc\_\></strong> Meeting started  
<strong>\<dsc\_\></strong> Welcome all  
<strong>\<dsc\_\></strong> I plan to do this every week since development is going so fast nowadays, we'll have a chance to reflect on what has been worked on, what is being worked on and what should be worked on and also what should not be worked on. Greetings to all who showed up.  
<strong>\<dsc\_\></strong> Yes, I copy pasted that  
<strong>\<selsta\></strong> hi  
<strong>\<xiphon\></strong> hi  
<strong>\<dsc\_\></strong> hi  
<strong>\<ErCiccione\[m\]\></strong> Hello  
<strong>\<dsc\_\></strong> - Discuss pending PRs  
<strong>\<dsc\_\></strong> Seeing as release is soon, we should merge current PRs ASAP, in addition also rebase &amp; merge all PRs that have \[Qt 5.9\] in the title, in light of pigeons success regarding updating the buildbots. After this is done, we have time for testing and translations.  
<strong>\<dsc\_\></strong> From my side of things, for this release I want to include my IPC PR (both \#2029 and \#2041 from rbrunner), the white-theme PR and the wallet explorer PR (\#2068) and all PRs marked Qt 5.9.  
<strong>\<ErCiccione\[m\]\></strong> yay  
<strong>\<dsc\_\></strong> If anyone wants to discuss any particular PR in-depth, go for it.  
<strong>\<selsta\></strong> I think QR code stuff should not be included in the next release.  
<strong>\<selsta\></strong> Not enough time to test this.  
<strong>\<selsta\></strong> Also requiring buildbot changes.  
<strong>\<selsta\></strong> (\#1816)  
<strong>\<ErCiccione\></strong> I agree with selsta. A lot of changes will go in for this release already, and some big ones are not merged yet.  
<strong>\<dsc\_\></strong> Yes that one is tricky. We already have enough on our plate  
<strong>\<dsc\_\></strong> lets summon luigi while we're at it  
<strong>\<dsc\_\></strong> .summon  
<strong>\<xmr-pr\></strong> luigi1111 luigi1111w luigi1113 luigi1112 luigi1114 ༼つ ◕\_◕ ༽つ  
<strong>\<dsc\_\></strong> Could you merge current list, soon? Thanks  
<strong>\<dEBRUYNE\></strong> selsta: What kind of buildbot changes does 1816 require?  
<strong>\<selsta\></strong> dEBRUYNE: zbar library has to get installed and to get 1816 to build on macOS seems hacky.  
<strong>\<dEBRUYNE\></strong> Ah I see, let's not merge that then  
<strong>\<selsta\></strong> see <https://github.com/monero-project/monero-gui/pull/1816#issuecomment-448998772>  
<strong>\<dEBRUYNE\></strong> Should we merge the QT 5.9 PRs?  
<strong>\<selsta\></strong> yes  
<strong>\<dEBRUYNE\></strong> Pigeons had success on the Linux buildbots, but has yet to finalize building on mac os x and windows  
<strong>\<dsc\_\></strong> Should not matter imo, we should merge so we have some time to test properly  
<strong>\<xiphon\></strong> yep, pigeons provided me an access to mac buildbot, i will take a look  
<strong>\<dsc\_\></strong> Seeing as buildbots will be migrated sooner or later  
<strong>\<dsc\_\></strong> thanks for your help on this BTW xiphon  
<strong>\<dEBRUYNE\></strong> Ok, then let's add the ones that are ready and reviewed to the merge list  
<strong>\<dsc\_\></strong> dEBRUYNE: I propose to first get rid of the current list  
<strong>\<dsc\_\></strong> Due to the rebases that will are required for the Qt 5.9 PRs  
<strong>\<dsc\_\></strong> .merges  
<strong>\<dsc\_\></strong> already quite long  
<strong>\<dEBRUYNE\></strong> Ah right  
<strong>\<dEBRUYNE\></strong> Perhaps we should try to semi code freeze at the end of this week?  
<strong>\<dEBRUYNE\></strong> i.e. ensure all necessary PRs are merged and then test a lot  
<strong>\<dsc\_\></strong> Yes, assuming luigi has time to merge today and tomorow  
<strong>\<dsc\_\></strong> if luigi is busy we might not make end of week  
<strong>\<ErCiccione\></strong> Yes please. Longer it is, happier i will be :D  
<strong>\<ErCiccione\></strong> there is also the GUI guide to update after all the merges  
<strong>\<dsc\_\></strong> Next agenda item?  
<strong>\<dsc\_\></strong> - Discuss pending issues  
<strong>\<dsc\_\></strong> as in, github issues.  
<strong>\<selsta\></strong> Anyone experienced <https://github.com/monero-project/monero-gui/issues/2074> ?  
<strong>\<dsc\_\></strong> We're you using the debugger from within QtCreator?  
<strong>\<dsc\_\></strong> Never happened to me  
<strong>\<selsta\></strong> No debugger.  
<strong>\<dsc\_\></strong> I want to discuss <https://github.com/monero-project/monero-gui/issues/2024>  
<strong>\<luigi1113\></strong> so much text  
<strong>\<dsc\_\></strong> <https://twitter.com/Ben\_Sharp\_/status/1119273759125299200>  
<strong>\<dsc\_\></strong> Complaint from some is "dark mode is to dark"  
<strong>\<dsc\_\></strong> Discuss.  
<strong>\<dsc\_\></strong> too dark\*  
<strong>\<dsc\_\></strong> Also, the question wether or not we'd want white theme as a default  
<strong>\<dEBRUYNE\></strong> I wonder whether it would be futile to try to find the right shade of dark whilst we have a white theme  
<strong>\<charuto\></strong> i'd like it even darker tbh  
<strong>\<dEBRUYNE\></strong> Most websites use white as default, black (night) as option  
<strong>\<dEBRUYNE\></strong> ^ dsc\_  
<strong>\<dsc\_\></strong> True  
<strong>\<ErCiccione\></strong> I think people got used to the black theme now. I would keep that as default  
<strong>\<xiphon\></strong> i would like dark theme as default  
<strong>\<dsc\_\></strong> Personally I'd like the black theme to be default, but I'd like to see what others think.  
<strong>\<dEBRUYNE\></strong> I am kind of ambivalent :P  
<strong>\<dsc\_\></strong> Ok. As for that Github issue. a redesign will take up loads of resources. That's why I did not comment there.  
<strong>\<selsta\></strong> White theme should get some feedback first. We can decide in a later release if we want it to be default.  
<strong>\<dsc\_\></strong> But I applaud any effort in thinkering with new designs  
<strong>\<selsta\></strong> There are some ideas we can use from \#2024 though.  
<strong>\<dEBRUYNE\></strong> I think a full redesign is too time consuming and too risky  
<strong>\<selsta\></strong> ^  
<strong>\<dEBRUYNE\></strong> But like selsta said, we can indeed reuse some stuff  
<strong>\<dEBRUYNE\></strong> make use of\*  
<strong>\<dsc\_\></strong> Yes, lets keep \#2024 in mind going forward  
<strong>\<dsc\_\></strong> After we've cleared the pending PRs, we should relook at the issues, I think we can close a few  
<strong>\<dsc\_\></strong> ErCiccione: Are you still making an effort to report our binaries to anti-virus vendors?  
<strong>\<ErCiccione\></strong> dsc\_: I stopped when all of them basically replied "our system catch it, so it's malware". Also, with the cli now having the background miner option as default, i see even more difficult to get delisted from their lists  
<strong>\<dsc\_\></strong> Hmm, was afraid of that. Please update \#1747 and/or close the issue :)  
<strong>\<ErCiccione\></strong> I think the only way to not get flagged would be to remove the miner from the GUI, or detach it somehow  
<strong>\<moneromooo\></strong> Maybe we can detect those and report them to the user as crapware.  
<strong>\<moneromooo\></strong> Fair's fair/.  
<strong>\<xiphon\></strong> I think the only way to not get flagged would be to remove the AV  
<strong>\<ErCiccione\></strong> dsc\_: will do.  
<strong>\<dsc\_\></strong> moneromooo: Agreed 100%  
<strong>\<dsc\_\></strong> ridiculous stuff  
<strong>\<dEBRUYNE\></strong> Speaking of background mining, anyone know how to disable it? <https://bitcointalk.org/index.php?topic=583449.msg50721098#msg50721098>  
<strong>\<ErCiccione\></strong> yeah, lots of big ones tho  
<strong>\<moneromooo\></strong> So next time someone asks, please ask them to list a file specific to that AV. I'll add some code to check and warn if found.  
<strong>\<xiphon\></strong> moneromooo: doesn't make a sense  
<strong>\<xiphon\></strong> your binary won't run  
<strong>\<xiphon\></strong> if the user have the AV that reports this binary  
<strong>\<moneromooo\></strong> Ah, it sees it before it gets run ? That's annoying indeed.  
<strong>\<kinghat\></strong> i think the gui should match the website, so light theme and dark theme option. i only use dark themes if theres an option btw.  
<strong>\<ErCiccione\></strong> some do, yes, but not all of them  
<strong>\<ErCiccione\></strong> (for the records: the issue about AV: <https://github.com/monero-project/monero-gui/issues/1747>)  
<strong>\<dsc\_\></strong> I guess it's a bad idea to have some code in main{} that checks the integrity of the local installation, in order to detect if files imperative to GUIs/CLIs operation have been altered or quarantined, which implies AV fucked with it.  
<strong>\<moneromooo\></strong> Then maybe we can piss them off by making a "warning" page in the GUI to warn people not use this list of shit AVs ^\_^  
<strong>\<dsc\_\></strong> Bad idea in the sense that you don't want to waste time on creating such a mechanism.  
<strong>\<dEBRUYNE\></strong> moneromooo: Yes, files get quarantined upon extraction of the binaries (according to users)  
<strong>\<xiphon\></strong> i think we shoun'd not care about this particular issue  
<strong>\<moneromooo\></strong> I don't mind spending time writing code that pisses off assholes.  
<strong>\<xiphon\></strong> AV behaviour is not under our control  
<strong>\<ErCiccione\></strong> xiphon: i disagree. It's bad UX  
<strong>\<xiphon\></strong> it is bad AV  
<strong>\<xiphon\></strong> is not our issue  
<strong>\<dsc\_\></strong> It is \*kinda\* our issue, as dEBRUYNE has to deal with users with an incomplete installation  
<strong>\<dsc\_\></strong> but we should ignore this issue anyhow  
<strong>\<dEBRUYNE\></strong> Sure, but there is little we can do at this point :P  
<strong>\<ErCiccione\></strong> btw, that list of AVs is from november, don't know how the situation is now with the last binaries  
<strong>\<moneromooo\></strong> Oh, it only removes part of the code ?  
<strong>\<dsc\_\></strong> Yes only certain files AFAIK.  
<strong>\<dEBRUYNE\></strong> Yeah not all of them  
<strong>\<selsta\></strong> AV on macOS blocks it completely.  
<strong>\<moneromooo\></strong> Is there a list of what it removes and does not remove ?  
<strong>\<dEBRUYNE\></strong> Tbh I think it gets quarantined due to integrated miner, but not entirely sure  
<strong>\<dEBRUYNE\></strong> moneromooo: differs per av -\_-  
<strong>\<moneromooo\></strong> I could do with a list for all.  
<strong>\<xiphon\></strong> Any AV works on the file basis  
<strong>\<ErCiccione\></strong> dEBRUYNE: yes, it's definitely the miner. That's what i was told when i contacted many AV companies (details in the issue)  
<strong>\<moneromooo\></strong> So we'll have a binary that just does the check, then runs the main one.  
<strong>\<xiphon\></strong> so it removes the whole binary file it thinks is a malware  
<strong>\<xiphon\></strong> yep, that would work  
<strong>\<moneromooo\></strong> and if they remove THAT one, it'll obviously look bad since it's just a "warn about crapware" one ^\_^  
<strong>\<xiphon\></strong> but i realyl a bad idea  
<strong>\<moneromooo\></strong> I'm not asking you to do it of course, I will :)  
<strong>\<xiphon\></strong> it will still complicate the stuff no matter who will do that  
<strong>\<selsta\></strong> Probably best to add a warning on the download page.  
<strong>\<selsta\></strong> And not bother further.  
<strong>\<dEBRUYNE\></strong> I have to agree with xiphon here  
<strong>\<dEBRUYNE\></strong> selsta: Yeah perhaps a popup on the website that links to the guide I created  
<strong>\<dsc\_\></strong> AV: waste precious CPU cycles on placebo protection. Enrich your desktop experience with totally-not-annoying popups.  
<strong>\<ErCiccione\></strong> dEBRUYNE\> fwiw there are warnings in the GUI guide as well, we could be more verbose or integrate your guide.  
<strong>\<dEBRUYNE\></strong> Both should work too :P  
<strong>\<ErCiccione\></strong> True :)  
<strong>\<dEBRUYNE\></strong> Can we talk about \#2100 for a bit?  
<strong>\<dsc\_\></strong> Go for it  
<strong>\<dEBRUYNE\></strong> I quite like it, but my only worry is that the DNS involved causes some issues on startup  
<strong>\<dEBRUYNE\></strong> In the past, we had it enabled and, for some users, the GUI would show a black screen upon startup  
<strong>\<dEBRUYNE\></strong> Relevant issue -\> <https://github.com/monero-project/monero-gui/issues/761>  
<strong>\<dsc\_\></strong> Someone needs to test \#2100. I'm not sure how to. The DNS check always returns empty for me.  
<strong>\<dsc\_\></strong> I can, however, confirm it does indeed do a DNS request  
<strong>\<dsc\_\></strong> and it always has done this, in the past, as long as I can remember  
<strong>\<dsc\_\></strong> I just never saw that popup  
<strong>\<xiphon\></strong> \#761 doesn't seem to be DNS - related  
<strong>\<dEBRUYNE\></strong> Because it was disabled  
<strong>\<dsc\_\></strong> it was never disabled  
<strong>\<dsc\_\></strong> Unless it was disabled over at core (wallet api)  
<strong>\<dsc\_\></strong> which afaik. it has not  
<strong>\<dEBRUYNE\></strong> What is this PR doing then? <https://github.com/monero-project/monero-gui/pull/777>  
<strong>\<dEBRUYNE\></strong> :-P  
<strong>\<dsc\_\></strong> That PR disables a message handler registration :P  
<strong>\<dsc\_\></strong> which is logging related  
<strong>\<dEBRUYNE\></strong> I see  
<strong>\<dsc\_\></strong> Regardless I will look into it, it's a feature that should work properly. Regarding \#2100, what do you think about linking directly to the site?  
<strong>\<dEBRUYNE\></strong> Is the link actually clickable?  
<strong>\<dsc\_\></strong> Does not seem so.  
<strong>\<dEBRUYNE\></strong> should we make it clickable?  
<strong>\<dsc\_\></strong> Hmm yeah, I'm wondering that.  
<strong>\<dsc\_\></strong> We can decide later. If nobody looks at \#2100 I will, but I don't think it will make next release.  
<strong>\<dsc\_\></strong> Ill prioritize it  
<strong>\<dsc\_\></strong> Next agenda point, before people fall asleep  
<strong>\<dsc\_\></strong> - Discuss developments past week  
<strong>\<dsc\_\></strong> Past week I've been working 1) a CMake recipe (I'm stuck) 2) Support for database pruning 3) Updating `qml-xmr` to work with our latest changes 4) Kneuffelbund's new seed page for in the wizard (Japenese layout).  
<strong>\<dsc\_\></strong> Anyone have an update what he/she has been working on?  
<strong>\<ErCiccione\></strong> all translations for the GUI are reviewed and merged on Pootle. I'm waiting for the next big round of merges, then i will make a call for translators  
<strong>\<ErCiccione\></strong> as i said before, would be great to have the mergeable merged asap, so to have time to review/submit translations and update the guide  
<strong>\<ErCiccione\></strong> for the distracted, the guide is here: <https://github.com/monero-ecosystem/monero-GUI-guide>  
<strong>\<ErCiccione\></strong> and help is always appreciated :)  
<strong>\<selsta\></strong> I’m currently only reviewing PRs.  
<strong>\<xiphon\></strong> was looking into hardware wallet restorate height bug (already sent a PR)  
<strong>\<xiphon\></strong> s/restorate/restore  
<strong>\<dEBRUYNE\></strong> dsc\_: Including it in the next release seems a bit hasty, yes, as we've had issues with it in the past  
<strong>\<dEBRUYNE\></strong> Therefore it needs to be thorougly checked and tested  
<strong>\<dsc\_\></strong> Ok guys  
<strong>\<dsc\_\></strong> Next agenda point would be developments for the coming week, but it is clear, that is, we go into ship-mode and merge all the things.  
<strong>\<dsc\_\></strong> and test afterwards.  
<strong>\<dsc\_\></strong> I call the meeting finished  
<strong>\<dsc\_\></strong> thanks  
<strong>\<dsc\_\></strong> ErCiccione: It could occur that we merge after you've already started translations, please don't get mad :-P  
<strong>\<xiphon\></strong> Ah, almost forgot to mention  
<strong>\<xiphon\></strong> Had an idea regarding the issue with exchanges the still use long payment id  
<strong>\<ErCiccione\></strong> if it's not big stuff i will be just moderately mad. Will pray the gods of the code freeze once again :P  
<strong>\<xiphon\></strong> Have to say that i don't like the approach, but still want to mention it  
<strong>\<xiphon\></strong> We can hardcode the deposit addresses of the exchanges that are using long payment ids  
<strong>\<xiphon\></strong> And warn a user or explicitly show the pamyne id field for that addresses  
<strong>\<dsc\_\></strong> What if those exchanges have a pool of wallets?  
<strong>\<xiphon\></strong> It will still be an improvement  
<strong>\<xiphon\></strong> Even if we don't catch all the cases  
<strong>\<selsta\></strong> I thought about this too while doing the PID in description PR but I’m not sure if it would be a good idea to do address specific code.  
<strong>\<xiphon\></strong> think they don't use multiple wallets, but i didn't check that  
<strong>\<dsc\_\></strong> It's not a bad idea xiphon, in the sense that it is a bad idea, but I would approve such PR  
<strong>\<xiphon\></strong> yeah, like i said, i don't like to have a particular service - specific code (hardcoded lsit of deposit addresses to check though), but it might somehow improve the situation with missing deposits until long payment ids get consensus banned  
<strong>\<dsc\_\></strong> Would this be something you could pick up or would you rather have someone else research those addresses and implement it?  
<strong>\<dsc\_\></strong> In any case, feel free to create an issue  
<strong>\<xiphon\></strong> Which services still use long payment ids? Bittrex, binance, and other?  
<strong>\<dsc\_\></strong> xmr.to I think/  
<strong>\<xiphon\></strong> "would you rather have someone else research those addresses" \<- at least this  
<strong>\<xiphon\></strong> i'm fine with implementing it  
<strong>\<moneromooo\></strong> Tippero :D  
<strong>\<selsta\></strong> xmr.to uses integrated or subaddress  
<strong>\<ErCiccione\></strong> is Tippero still alive?  
<strong>\<dsc\_\></strong> selsta: Ha\! busted.  
<strong>\<dsc\_\></strong> Why are you selling Monero?  
<strong>\<dsc\_\></strong> (joking :P)  
<strong>\<moneromooo\></strong> Yes, I just checked.  
<strong>\<scoobybejesus\></strong> dsc\_\> Complaint from some is "dark mode is too dark" \<\<\< FWIW, i agree. black and white are both harsh/extremes. instead of white and black themes, i'd suggest light and dark. could potentially avoid inverting images across themes by doing so.  
<strong>\<selsta\></strong> dsc\_: :P  
<strong>\<xiphon\></strong> moneromooo: what are your thoughts on having such a temporal check in the monero core wallet codebase?  
<strong>\<xiphon\></strong> that way both cli and gui wallets will act the same in this case  
<strong>\<xiphon\></strong> or we can expect that monero cli users are more experienced that gui users and have this check only in the gui code  
<strong>\<xiphon\></strong> s/that/than  
<strong>\<moneromooo\></strong> What temporal check ?  
<strong>\<moneromooo\></strong> You mean checking a list of known addresses that want a long payment id ?  
<strong>\<xiphon\></strong> yep  
<strong>\<moneromooo\></strong> I think it's a bit shit but maybe the lesser evil.  
<strong>\<moneromooo\></strong> Though we already talked about this long ago and did not do it, so...  
<strong>\<xiphon\></strong> alright, i think we can do this only on the gui side
