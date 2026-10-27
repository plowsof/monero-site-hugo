---
title: Overview and Logs for the Dev Meeting Held on 2016-08-28
summary: Trezor and other hardware wallets for Monero, brief update on 0MQ and the official GUI, hardfork schedule
tags: [dev diaries, core, crypto, 0mq]
author: dEBRUYNE / fluffypony
---

### Overview

An overview [can be found on Hello Monero](https://hellomonero.com/article/monero-bi-weekly-dev-meeting-note-highlights-2016-08-28)

### Logs

<strong>\<hyc\></strong> ding ding ding  
<strong>\<fluffypony\></strong> hello meeting-bot\!  
<strong>\<meeting-bot\> \[fluffypony\]</strong> hello from the other side\!  
<strong>\<fluffypony\></strong> ok we’re on  
<strong>\<fluffypony\></strong> ArticMine / luigi1111w / othe / smooth / hyc / moneromooo / tewinget / redfish / NoodleDoodle / anyoen I forgot  
<strong>\<moneromooo\></strong> There’s an article about fraud in crypto on the bytecoin blog. Chutzpah, got to admit.  
<strong>\<fluffypony\></strong> welcome to the annual “Devs who Drink whilst Developing” meeting  
<strong>\<fluffypony\></strong> moneromooo: brave of them  
<strong>\<hyc\></strong> lol. I’m on cider today  
<strong>\<fluffypony\></strong> ok so  
<strong>\<fluffypony\></strong> in today’s news  
<strong>\<fluffypony\></strong> nothing happened with the Monero price  
<strong>\<fluffypony\></strong> and so we focus on dev  
<strong>\<hyc\></strong> lol  
<strong>\<fluffypony\></strong> let’s start with a quick check of open PRs  
<strong>\<fluffypony\></strong> except for RingCT which we’ll get to  
<strong>\<fluffypony\></strong> redfish: how goes the CMake stuff?  
<strong>\<NoodleDoodle\></strong> I alive today.  
<strong>\<moneromooo\></strong> hey :)  
<strong>\<fluffypony\></strong> and a warm welcome to our special guest, NoodleDoodle  
<strong>\<fluffypony\></strong> :-P  
<strong>\<fluffypony\></strong> whilst we wait for the redfishes  
<strong>\<fluffypony\></strong> NoodleDoodle: do you want to talk about Trezor at all?  
<strong>\<fluffypony\></strong> ok good chat  
<strong>\<hyc\></strong> heh  
<strong>\<fluffypony\></strong> :-P  
<strong>\<NoodleDoodle\></strong> Sure :P  
<strong>\<fluffypony\></strong> yay, take it away  
<strong>\<hyc\></strong> redfish doesn’t appear to be answering either  
<strong>\<NoodleDoodle\></strong> I’m about 1296 behind in commits. Rebasing is pretty much out of the question. Have to manually merge then release.  
<strong>\<fluffypony\></strong> NoodleDoodle: do you want any help with that?  
<strong>\<NoodleDoodle\></strong> The trezor firmware itself should be easier, except it’s split into 5 or 6 repos  
<strong>\<fluffypony\></strong> ok cool  
<strong>\<NoodleDoodle\></strong> I should be able to do it.  
<strong>\<fluffypony\></strong> NoodleDoodle: do you want us to host it on the monero-project Github in its own repo, obvs giving you collab access, to make it more “formal” and part of the core project?  
<strong>\<tewinget\></strong> late, but here  
<strong>\<NoodleDoodle\></strong> Sure, anything. I actually started on keepkey awhile back as well, although it’s not as complete as trezor.  
<strong>\<fluffypony\></strong> ok cool  
<strong>\<fluffypony\></strong> I’ve been fiddling with Ledger Blue, as I have the Blue and the Nano S  
<strong>\<fluffypony\></strong> I have a feeling they’ll be a cinch after Trezor / Keepkey  
<strong>\<fluffypony\></strong> and, hopefully, we can PR it in to be part of the default firmware on these devices  
<strong>\<fluffypony\></strong> if they’ll have us  
<strong>\<fluffypony\></strong> ok so next up  
<strong>\<fluffypony\></strong> hyc has a small PR to ease up our LMDB speed after you’re caught up with the network  
<strong>\<fluffypony\></strong> which should lead to an even more robust blockchain DB, not that I’ve had anything resembling a corruption in ages  
<strong>\<fluffypony\></strong> and I kill daemons like I’m playing Doom  
<strong>\<fluffypony\></strong> tewinget, would you like to update us on 0MQ plx?  
<strong>\<tewinget\></strong> sure  
<strong>\<tewinget\></strong> so far, all of the daemon RPC calls pertaining to the wallet are good to go, as well as several others  
<strong>\<tewinget\></strong> the wallet is good to go for using the new daemon rpc library  
<strong>\<tewinget\></strong> oh, the new daemon rpc has a library, rather than just calling out to networking things directly. \>\*\*\_\>\*\*  
<strong>\<tewinget\></strong> (I only got \~1 hr sleep, minor rambling will happen)  
<strong>\<fluffypony\></strong> tewinget: do you think it’s PR-able now, and then subsequent updates to follow, or is it still too fast-and-loose to be used in “production”?  
<strong>\<tewinget\></strong> let’s see…next things I need to do are basically polish: make command line flags / parametrize port bind options, and so on. Documentation (both code and RPC spec)  
<strong>\<tewinget\></strong> well, as of right now because of how cryptocurrencies work, if it cocks up it’ll just…fail? As in, not in a destructive, send all coins to the void way, but in a boring “the tx failed to go to the daemon” or w/e way  
<strong>\<tewinget\></strong> that said, I should probably put a bit more time into polish with command line flags and such first, as it currently has hard-coded binding and so on, and I need to doc the API  
<strong>\<fluffypony\></strong> ok because that brings us on to the next topic  
<strong>\<hyc\></strong> the PR I’ve submitted actually only changes the default db mode at startup. we didn’t quite figure out how to adjust it after sync finished  
<strong>\<tewinget\></strong> afaik (as in, if I’ve done it right) it’s JSON-RPC compliant as well, apart from the http layer  
<strong>\<fluffypony\></strong> and tewinget maybe you can think about it in this context  
<strong>\<fluffypony\></strong> the RingCT PR is now post-review, at least by me, with multiple others having reviewed parts of it  
<strong>\<fluffypony\></strong> so it’s merge time  
<strong>\<fluffypony\></strong> we haven’t set fork heights yet  
<strong>\<moneromooo\></strong> Wait till I signed commits first.  
<strong>\<fluffypony\></strong> moneromooo: yes  
<strong>\<fluffypony\></strong> but basically the idea is to run through the testnet forks next week  
<strong>\<fluffypony\></strong> which means testnet will do the equivalent of September <em>and</em> March 2017 forks  
<strong>\<fluffypony\></strong> in one week  
<strong>\<fluffypony\></strong> testnet will then have RingCT live  
<strong>\<fluffypony\></strong> and we’ll be able to focus on efficiency improvements, further testing, and so on  
<strong>\<fluffypony\></strong> in the meantime, it will let us code freeze sometime into September  
<strong>\<fluffypony\></strong> a little later than we’d have liked, but a necessity to get RingCT in to this freeze instead of only in March  
<strong>\<fluffypony\></strong> now here’s the nice thing  
<strong>\<fluffypony\></strong> old daemons only know about the fork in September, and will only start nagging about that one  
<strong>\<fluffypony\></strong> so we can set the subsequent fork to something earlier than March  
<strong>\<fluffypony\></strong> but we’d have to make that decision by the next dev meeting pretty much at the latest  
<strong>\<fluffypony\></strong> which means  
<strong>\<fluffypony\></strong> next week Tue / Wed or so we’ll push out binaries for 0.10-beta  
<strong>\<fluffypony\></strong> 0.10 will be called Wolfram Warptangent, in honour of the Monero contributor that passed away  
<strong>\<tewinget\></strong> well the 6-month window is a “no earlier than”, but at the same time since it’s basically just miners doing the voting, idk how doing it earlier pans out.  
<strong>\* tewinget</strong> approves the name.  
<strong>\<ArticMine\></strong> Does that include the GUI?  
<strong>\<fluffypony\></strong> ArticMine: no, this is core only  
<strong>\<tewinget\></strong> ArticMine: We can tag a release with GUI at any time, no forking and such  
<strong>\<tewinget\></strong> same with ZMQ  
<strong>\<fluffypony\></strong> but it includes the GUI lib changes that are needed  
<strong>\<fluffypony\></strong> so anyone compiling the GUI will have working beta bins to play with  
<strong>\<fluffypony\></strong> so I’d please like commitments from as many people as possible to participate in testnet next week  
<strong>\* moneromooo</strong> commits fluffypony  
<strong>\<fluffypony\></strong> lol  
<strong>\* tewinget</strong> rejects the unsigned commit  
<strong>\* iDunk</strong> sees travis ci build fail  
<strong>\<fluffypony\></strong> git commit -S -am “loony bin”  
<strong>\<moneromooo\></strong> OK. I’ll put in a Pedersen commitment to… something.  
<strong>\<moneromooo\></strong> When do we set the forks then ?  
<strong>\<tewinget\></strong> at dinner?  
<strong>\* fluffypony</strong> giggles  
<strong>\<moneromooo\></strong> For v3, ok. v4 (rct) on monday lunchtime.  
<strong>\<fluffypony\></strong> moneromooo: for testnet?  
<strong>\<moneromooo\></strong> Obviously :P  
<strong>\<moneromooo\></strong> And v5 (rct only) on tuesday.  
<strong>\<fluffypony\></strong> you mean Monday tomorrow, or Monday next week?  
<strong>\<moneromooo\></strong> Fine ?  
<strong>\<moneromooo\></strong> Tomorrow.  
<strong>\<fluffypony\></strong> hmmm  
<strong>\<moneromooo\></strong> Too fast ?  
<strong>\<fluffypony\></strong> yes actually good idea - the actual fork process has been tested on private testnet, and in the previous fork  
<strong>\<fluffypony\></strong> so we push bins out after the fork  
<strong>\<fluffypony\></strong> then people can play without needing to fiddle  
<strong>\<gingeropolous\></strong> and this is still a no-vote fork?  
<strong>\<moneromooo\></strong> Yes. Screw votes, they were coded by an idiot.  
<strong>\<fluffypony\></strong> LOL\!  
<strong>\<fluffypony\></strong> gingeropolous: yeah - we can re-address that in the next 6-12 months, but at the moment it’s move-it-or-lose-it  
<strong>\<gingeropolous\></strong> yeah absolutely  
<strong>\<fluffypony\></strong> also the schedule is pretty widely known, except for ShapeShift who we’ll email and then they’ll claim they have no knowledge of the update  
<strong>\<tewinget\></strong> gingeropolous: plus it’s technically never a no-vote fork, as if the miners get pissed off and don’t want it, well, they just won’t. \>\*\*\_\>\*\*  
<strong>\<gingeropolous\></strong> lol fluffypony  
<strong>\<fluffypony\></strong> ok so moneromooo, your fork points are fine  
<strong>\<moneromooo\></strong> So will you merge the PR then build off that, or build off my branch ?  
<strong>\<moneromooo\></strong> (for the test builds)  
<strong>\<fluffypony\></strong> no, merge  
<strong>\<moneromooo\></strong> OK  
<strong>\<fluffypony\></strong> people must be able to build head on their boxes if they want  
<strong>\<moneromooo\></strong> (oh, the supreme importance of punctuation)  
<strong>\* gingeropolous</strong> hides  
<strong>\<fluffypony\></strong> lol  
<strong>\<fluffypony\></strong> ok  
<strong>\<fluffypony\></strong> I think that’s it from my side  
<strong>\<fluffypony\></strong> does anyone have any questions or thoughts or anything?  
<strong>\<gingeropolous\></strong> im still not super clear on the fork schedule… but it could be sleep dep  
<strong>\<gingeropolous\></strong> for mainnet  
<strong>\<fluffypony\></strong> for mainnet it’s still the September v3 fork, as expected  
<strong>\<fluffypony\></strong> if we want we can have the v4 and v5 forks at any point after that, even though March would be the “expected” date  
<strong>\<hyc\></strong> iDunk: build log shows no errors, just too slow to build  
<strong>\<tewinget\></strong> I have a few questions, but I’ll wait for others’ for a few minutes first.  
<strong>\<hyc\></strong> testnet sched sounds good  
<strong>\<hyc\></strong> 0.10-beta sounds fine  
<strong>\<iDunk\></strong> hyc: was a joke  
<strong>\<hyc\></strong> iDunk: but it’s unfortunately true :P  
<strong>\<fluffypony\></strong> so even though we wouldn’t normally push a fork forward, we have to consider the influx of new users, and maybe we feel that the added privacy is essential enough to do v4 end of Oct, v5 in Dec  
<strong>\<fluffypony\></strong> something like that  
<strong>\<gingeropolous\></strong> gotcha.  
<strong>\<fluffypony\></strong> so we start 2017 with RingCT as the only way to transact  
<strong>\<gingeropolous\></strong> is there a place where the fork plan /etc is laid out?  
<strong>\<gingeropolous\></strong> maybe the readme of the github is a good home  
<strong>\<fluffypony\></strong> gingeropolous: this one, or generally?  
<strong>\<gingeropolous\></strong> generally  
<strong>\<gingeropolous\></strong> and this one  
<strong>\<fluffypony\></strong> generally, the Monero Forum post + all other posts that talk about the mandatory hard forks  
<strong>\<tewinget\></strong> gingeropolous: plans are probably in /usr/share/doc, not in /etc  
<strong>\<fluffypony\></strong> I agree that the Readme shoudl include it  
<strong>\<hyc\></strong> seems to me like we have a lot of profiling and tuning to do before ringCT will play for real  
<strong>\<hyc\></strong> october might be too soon  
<strong>\<gingeropolous\></strong> its gonna be a helluva fall  
<strong>\<fluffypony\></strong> this one is dev meeting specific, we’ll have a summary post after that and solicit feedback from the non-dev community  
<strong>\<fluffypony\></strong> hyc: we do have new contributors, so we might be able to get through the tuning stuff faster  
<strong>\<hyc\></strong> cool  
<strong>\<fluffypony\></strong> I’m no fan of pushing it too hard, because it means I have to get MyMonero working with RingCT, but it’s doable  
<strong>\<gingeropolous\></strong> yeah, I know there’s the forum posts.. but considering fork early, fork often is kind of our thing, it should / could be … more prominent  
<strong>\<gingeropolous\></strong> ah screw it. time to by moneroforks.whatever  
<strong>\<fluffypony\></strong> gingeropolous: do you want to PR a change to the readme?  
<strong>\<fluffypony\></strong> it’ll take you from troll-dev status to readme-dev  
<strong>\<fluffypony\></strong> :-P  
<strong>\<gingeropolous\></strong> :)  
<strong>\<fluffypony\></strong> ok tewinget  
<strong>\<fluffypony\></strong> before we run out of time  
<strong>\<fluffypony\></strong> ask away  
<strong>\<tewinget\></strong> ok  
<strong>\<tewinget\></strong> so for one thing, I haven’t seen a GUI progress update today, figured I’d ask if we have a tentative timeline?  
<strong>\<fluffypony\></strong> othe: any thoughts?  
<strong>\<fluffypony\></strong> ^^  
<strong>\<othe\></strong> sorry was busy drinking  
<strong>\<othe\></strong> yeah so ilya is traveling but back next week, we hope to fix all small reamaining issues till the week after  
<strong>\<fluffypony\></strong> ok  
<strong>\<othe\></strong> and then we can release a beta  
<strong>\<tewinget\></strong> awesome  
<strong>\<othe\></strong> together with a new tagged rls  
<strong>\<fluffypony\></strong> othe is there any way he can stop submitting huge PRs  
<strong>\<othe\></strong> and then whats following is mostly advanced settings and stuff like that  
<strong>\<fluffypony\></strong> it’s killing it for other potential contributors  
<strong>\<othe\></strong> yeah i can tell him  
<strong>\<tewinget\></strong> if there’s desire for it and nobody else takes up the task, I may sign up to do a plugin system (unless that’s already in place?)  
<strong>\<fluffypony\></strong> he needs to PR on a feature / fix by feature basis  
<strong>\<othe\></strong> oh thats not in the place but something that would be cool to have tewinget  
<strong>\<hyc\></strong> yeah, narrow scope PRs  
<strong>\<fluffypony\></strong> yeah definitely, hyc  
<strong>\<moneromooo\></strong> And move the twitter stuff in there, just to be sure.  
<strong>\<fluffypony\></strong> OH\!  
<strong>\<fluffypony\></strong> before I forget  
<strong>\<fluffypony\></strong> the big thing I wanted to discuss  
<strong>\<fluffypony\></strong> <https://github.com/monero-project/bitmonero/issues/80>  
<strong>\<fluffypony\></strong> that’s going to happen before the bins are pushed  
<strong>\<fluffypony\></strong> so if anyone has any final thoughts on that, you’d best comment on the issue, else suck it up later :-P  
<strong>\<fluffypony\></strong> I’d also like us to start refactoring the parts that have CryptoNote in the name to be Monero instead  
<strong>\<tewinget\></strong> something something \`sed\`  
<strong>\<fluffypony\></strong> as RingCT + several thousand commits puts us quite far beyond the reference protocol  
<strong>\<moneromooo\></strong> Renaming things for the fun of it ? I’d rather not.  
<strong>\<moneromooo\></strong> (in the code, I mean. I’m ok with the binaries thing)  
<strong>\<tewinget\></strong> btw fluffypony, I \*think\* that the zmq-dev branch is PR-ready, but I’m not comfortable making that call without some testing, so if anyone would like to give it a go (testnet and mainnet are affected identically, so testnet is 100% fine for, well, testing)  
<strong>\<ArticMine\></strong> It simple reflects the reality of how much the code has changed from the original Cryptonote implementation  
<strong>\<tewinget\></strong> as I said before, I’d like to polish it up a bit first, but that’s not a blocking issue for PR-ing  
<strong>\<fluffypony\></strong> tewinget: if you’re of the opinion it can go into a mid-Sept code freeze / release then sure, else leave it till after the release because it’s not HF worthy  
<strong>\<fluffypony\></strong> your call  
<strong>\<tewinget\></strong> I’m reluctantly okay with doing merges on my end before a PR, so it can wait, just figured I’d give the option. Testing would still be great though…I need to sync the testnet chain on my VPS but then I’ll badger you for some testnet moneyz  
<strong>\<tewinget\></strong> I’ll need to discuss with someone(s) how “blocknotify” should work, and perhaps about doing something similar for miners (call it templatenotify if you like)  
<strong>\<fluffypony\></strong> oh that could be interesting  
<strong>\<fluffypony\></strong> the templatenotify I mean  
<strong>\<hyc\></strong> yeah templatenotify would make an immediate difference for miners  
<strong>\<tewinget\></strong> yea, I’m thinking a configurable parameter that is like “if there is 20% more value to be had via tx fees by changing the block template, notify the miner to update its block template with the new transactions included”  
<strong>\<tewinget\></strong> plus the obvious implications of changing when a new block is learned about  
<strong>\<hyc\></strong> right  
<strong>\<tewinget\></strong> but that can be done with the blocknotify that the wallet wants anyway  
<strong>\<gingeropolous\></strong> ooh we talkin dynamic fees?  
<strong>\<tewinget\></strong> at any rate, that’s a design discussion for another time.  
<strong>\<fluffypony\></strong> tewinget: I’d prefer earlier PRs  
<strong>\<fluffypony\></strong> I mean  
<strong>\<tewinget\></strong> fluffypony: yes, yes, I meant for after that PR  
<strong>\<fluffypony\></strong> if it’s properly borked by mid-September we can revert 0MQ for release  
<strong>\<meeting-bot\> \[anonimal\]</strong> 17:06  
<strong>\<fluffypony\></strong> tewinget: so what I’m saying is PR soon, plx  
<strong>\<fluffypony\></strong> anonimal apologies  
<strong>\<fluffypony\></strong> is there anything else or can we call it?  
<strong>\<hyc\></strong> think that’s good for today  
<strong>\<tewinget\></strong> I’d say go nuts for your kovri meeting, we’re not going anywhere  
<strong>\<fluffypony\></strong> yay, nuts  
<strong>\<tewinget\></strong> so if something else comes up, address it after that meeting  
<strong>\<fluffypony\></strong> kk
