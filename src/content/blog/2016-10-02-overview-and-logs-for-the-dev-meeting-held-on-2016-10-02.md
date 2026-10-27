---
title: Overview and Logs for the Dev Meeting Held on 2016-10-02
summary: Review and discussion of Open PRs, brief update on Ring CT, the official GUI, and Trezor for Monero
tags: [dev diaries, core, crypto, 0mq]
author: dEBRUYNE / fluffypony
---

### Overview

An overview [can be found on Hello Monero](https://hellomonero.com/article/monero-and-kovri-dev-meeting-note-highlights-2016-10-02)

### Logs

<strong>\<fluffypony\></strong> Hi all  
<strong>\<fluffypony\></strong> starting meeting bot  
<strong>\<moneromooo\></strong> I’m none of them.  
<strong>\<dEBRUYNE\></strong> I am here  
<strong>\<fluffypony\></strong> moneromooo: I know you’re here :)  
<strong>\<fluffypony\></strong> ok meeting bot is up  
<strong>\<dnaleor\></strong> watching  
<strong>\<fluffypony\></strong> so  
<strong>\<meeting-bot\> \[anonimal\]</strong> \#kovri-dev too?  
<strong>\<fluffypony\></strong> kovri-dev is roped in too  
<strong>\<othe\></strong> k  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> o  
<strong>\<fluffypony\></strong> this is our first post-0.10.0 meeting  
<strong>\<fluffypony\></strong> the 0.10.0 release went fairly smoothly  
<strong>\<fluffypony\></strong> apart from the boost oddities  
<strong>\<fluffypony\></strong> on the Boost serialisation stuff  
<strong>\<fluffypony\></strong> it’s not really feasible to do a point release just for that just yet - in a few weeks I’ll have local build infrastructure that will make releases a lot easier on me  
<strong>\<fluffypony\></strong> since I can secure local machines far more easily than Internet-facing machines at a DC  
<strong>\<fluffypony\></strong> in the interim, if anyone is struggling with it the easiest thing for them to do is recover their wallet from the seed / keys  
<strong>\<moneromooo\></strong> And keep the old cache if they have tx keys they want to keep.  
<strong>\<fluffypony\></strong> ^^  
<strong>\<fluffypony\></strong> I’d also like to welcome all the new contributors  
<strong>\<fluffypony\></strong> even if it’s just correcting a spelling error, all contributions are valuable  
<strong>\<fluffypony\></strong> and very much appreciated  
<strong>\<fluffypony\></strong> one thing I would like to encourage with the new contributors is to submit your GPG key via PR  
<strong>\<fluffypony\></strong> and side-channel it to myself or moneromooo or someone so we can independently verify the correct key goes in  
<strong>\<fluffypony\></strong> they live in utils/gpg<em>keys/  
<strong>\<meeting-bot\> \[anonimal\]</strong> and if moneromooo says “ok” in your PR, that’s a GOOD thing\!  
<strong>\<fluffypony\></strong> and then once you’ve done that you can GPG sign your commits with -S  
<strong>\<fluffypony\></strong> eg. git commit -S -am “meaningful commit message”  
<strong>\<moneromooo\></strong> Only if it’s at the start.  
<strong>\<patthehuman\></strong> Is there anything that needs to be made for iOS  
<strong>\<fluffypony\></strong> lol anonimal  
<strong>\<fluffypony\></strong> patthehuman: it’s an open-source project, so if you want to build something for iOS then please do  
<strong>\<fluffypony\></strong> no need to ask permission or anyway  
<strong>\<fluffypony\></strong> I’d be interested to see if we could package a full node for iOS (without the wallet, lest it get removed from the app store)  
<strong>\<patthehuman\></strong> sure, i guess i’m wondering more along the lines of what needs to be built  
<strong>\<patthehuman\></strong> can you outline how that would work?  
<strong>\<fluffypony\></strong> and then an old iPhone or iPod Touch would work as a full node on wifi  
<strong>\<fluffypony\></strong> well we have native ARMv8 builds  
<strong>\<fluffypony\></strong> and interacting with the daemon over RPC isn’t hard  
<strong>\<ArticMine\></strong> Why not just go with Cydia on jailbroken iOS?  
<strong>\<fluffypony\></strong> but I have no idea if an iOS app would let you arbitrarily launch a process  
<strong>\<endogenic\></strong> ArticMine: too few jailbreak their devices, no?  
<strong>\<fluffypony\></strong> ArticMine: absolutely - would be nice to be able to launch it as an app tho  
<strong>\<patthehuman\></strong> generally apps get removed from the app store if they are simple “remotes”  
<strong>\<endogenic\></strong> fluffypony: iOS does not allow you to spawn processes… no NSTask etc equivalent  
<strong>\<fluffypony\></strong> ah  
<strong>\<TedTheFicus\></strong> ArcticMine: I think Cydia is a good plan B. Not many non tech people are going to have jail broken phones  
<strong>\<patthehuman\></strong> right, they have a list of closed API’s that will get you banned  
<strong>\<fluffypony\></strong> does Objective-C let you also run native C / C++ code?  
<strong>\<endogenic\></strong> fluffypony: yep as long as you can compile for an ARM target  
<strong>\<endogenic\></strong> compile it</em>  
<strong>\<MK\_\_\></strong> ArticMine : A good idea and a lot of IOS devices have Jailbreak , Remember that XMR are used in the DNM as well  
<strong>\<fluffypony\></strong> yeah we have ARMv8 support across the board  
<strong>\<endogenic\></strong> Objective-C is a strict superset of C, so any C is good, and C++ can be compiled too  
<strong>\<ArticMine\></strong> Net applications Android 69.18% IOS 25.02% market share  
<strong>\<fluffypony\></strong> anyway we’re getting side-tracked a little - patthehuman feel free to play around with it, if you feel like it  
<strong>\<patthehuman\></strong> sure  
<strong>\<fluffypony\></strong> so  
<strong>\<fluffypony\></strong> ringCT is live in testnet, and more testing would be appreciated  
<strong>\<fluffypony\></strong> mWo12’s testnet block explorer is helpful  
<strong>\<fluffypony\></strong> but performance testing is also immensely useful  
<strong>\<fluffypony\></strong> see what cracks under pressure  
<strong>\<fluffypony\></strong> we have a short window until the January hard fork, so we need to hammer testnet as much as possible  
<strong>\<trustedsetup\></strong> is there a testnet faucet somewhere? or is mining or irc begging for testnet xmr recommended?  
<strong>\<fluffypony\></strong> just ask me and I’ll send testnet XMR your way  
<strong>\<patthehuman\></strong> are there any automation processes that can hammer on testnet?  
<strong>\<patthehuman\></strong> i have access to a lot of r510 servers that i could potentially mirror some script to hammer on it  
<strong>\<fluffypony\></strong> patthehuman: you could pretty much just write a bash script to send to yourself once a second  
<strong>\<fluffypony\></strong> and cycle it that way  
<strong>\<patthehuman\></strong> cool  
<strong>\<fluffypony\></strong> and then see how your testnet node(s) handle catch ups, and if they keep up with testnet when blocks are bigger  
<strong>\<fluffypony\></strong> we also have our new buildbots ticking along nicely  
<strong>\<fluffypony\></strong> so we’ll be killing off Travis at some point in the coming weeks  
<strong>\<fluffypony\></strong> build bot output has been relegated to \#monero-bots  
<strong>\<fluffypony\></strong> and that channel is relayed to irc2p  
<strong>\<meeting-bot\> \[anonimal\]</strong> Thanks pigeons  
<strong>\<meeting-bot\> \[anonimal\]</strong> monero-build.i2p is also online  
<strong>\<fluffypony\></strong> yeah pigeons has done great work  
<strong>\<fluffypony\></strong> at the moment we’re building for a ton of platforms  
<strong>\<fluffypony\></strong> including macOS 10.9, 10.10, 10.11  
<strong>\<fluffypony\></strong> so we should pick up PRs that break compilation more rapidly  
<strong>\<fluffypony\></strong> how we handle testing is a bit harder  
<strong>\<fluffypony\></strong> especially since some of the tests take several hours to run  
<strong>\<fluffypony\></strong> my current leaning is towards nightly builds + tests  
<strong>\<fluffypony\></strong> (of master)  
<strong>\<fluffypony\></strong> that way we’ll catch tests that are broken by any merged PRs  
<strong>\<moneromooo\></strong> Daily core\_tests would be useful.  
<strong>\<fluffypony\></strong> performance\_tests would also be useful  
<strong>\<fluffypony\></strong> that way we can track anything that has a huge impact on performance  
<strong>\<moneromooo\></strong> As long as the outcome can be seen without too many hoops (ie, javacrsipt)  
<strong>\<fluffypony\></strong> moneromooo: we’ll probably just grab the output, parse it, and shove it in a database  
<strong>\<fluffypony\></strong> then we can create a profiler for the site without too many issues  
<strong>\<fluffypony\></strong> on the PR side  
<strong>\<fluffypony\></strong> has anyone looked at 1082?  
<strong>\<patthehuman\></strong> no my apologies for being new but can you elaborate on what 1082 is  
<strong>\<fluffypony\></strong> or actually moneromooo: can you give everyone a brief overview of what 1082 does  
<strong>\<fluffypony\></strong> oh sorry patthehuman - PR = pull request  
<strong>\<fluffypony\></strong> so PR 1082 = <https://github.com/monero-project/monero/pull/1082>  
<strong>\<patthehuman\></strong> yeah im familiar with PR’s (worst part of my work day lol)  
<strong>\<moneromooo\></strong> Ah, as the comment says, really.  
<strong>\<moneromooo\></strong> It just tries to avoid the case where someone sends money just after receiving it.  
<strong>\<moneromooo\></strong> That’s a common enough case.  
<strong>\<fluffypony\></strong> “25% of the outputs are selected from the last 5 days (if possible), in order to avoid the common case of sending recently received outputs again. 25% and 5 days are subject to review later, since it’s just a wallet level change.”  
<strong>\<trustedsetup\></strong> where did the 25% come from? 25% seems somewhat arbitrary. did MRL have input on this number?  
<strong>\<moneromooo\></strong> They’re aribtrary.  
<strong>\<fluffypony\></strong> trustedsetup: the MRL is of the opinion that we’re never going to find a “perfect” distribution, and that distribution should be re-evaluated regularly  
<strong>\<luigi1112\></strong> Will look at it  
<strong>\<fluffypony\></strong> 25% would only be a single output at minimum mixin  
<strong>\<trustedsetup\></strong> ok thanks  
<strong>\<moneromooo\></strong> It’s actually 25%, except if that gives 0, in which case it uses 1.  
<strong>\<fluffypony\></strong> moneromooo: and it’s 25% including the “real” output, right?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<moneromooo\></strong> See line 2744 in wallet2.cpp  
<strong>\<fluffypony\></strong> kk  
<strong>\<fluffypony\></strong> as to the other open PRs  
<strong>\<fluffypony\></strong> most of them are not merged yet due to their being unreviewed  
<strong>\<fluffypony\></strong> I try give PRs a little while before reviewing them myself, otherwise I end up being the only reviewer, which is bad for security obvs  
<strong>\<fluffypony\></strong> bear in mind that a review is <em>not\* in-depth line-by-line analysis  
<strong>\<patthehuman\></strong> pr is just a quick overview  
<strong>\<moneromooo\></strong> I’d hope the review does look at all lines.  
<strong>\<fluffypony\></strong> yup  
<strong>\<fluffypony\></strong> it’s a sanity check, and a check for obvious screw-ups, and a check for snuck-in backdoors  
<strong>\<fluffypony\></strong> moneromooo: the key there was in-depth, not line-by-line ;)  
<strong>\<moneromooo\></strong> OK, that’s fine.  
<strong>\<fluffypony\></strong> medusa</em>: are you around?  
<strong>\<fluffypony\></strong> ok in the absence of medusa\* being around, dEBRUYNE have you been following Ilya’s progress on medusa\*‘s issues?  
<strong>\<dEBRUYNE\></strong> Yeah, he has fixed all issues opened by medusa\* as far as I know  
<strong>\<fluffypony\></strong> ok great  
\*\*\<medusa\*\>\*\* yes im here  
<strong>\<dEBRUYNE\></strong> Except -\> <https://github.com/monero-project/monero-core/issues/29>  
<strong>\<dEBRUYNE\></strong> but that’s more of a feature, which should be implemented later  
<strong>\<fluffypony\></strong> oh cool - medusa\_ how are you finding it now that most of the issues have been fixed?  
<strong>\<dEBRUYNE\></strong> could\*  
<strong>\<TedTheFicus\></strong> MK\_ + Others who are wondering, the monero-core project that is being discussed now is the GUI  
<em><em>\<medusa</em>\></em>\* i think we need more feedback regarding the performance difference between gui wallet creation time and CLI wallet creation time  
<em><em>\<medusa</em>\></em>\* and i dont know of any major bugs that would be dangerous  
<strong>\<fluffypony\></strong> medusa\_: there’s a PR that’s supposed to fix that  
<strong>\<fluffypony\></strong> I haven’t merged it yet, but it’s gone through review  
<strong>\<dEBRUYNE\></strong> Ilya merged jacquee’s PR as well  
<strong>\<dEBRUYNE\></strong> he noticed a significant improvement  
<em><em>\<medusa</em>\></em>\* so my opinion is merge all to monero-core project master, test there again and if its good we build the bins  
<strong>\<dEBRUYNE\></strong> ^ +1  
<strong>\<dEBRUYNE\></strong> Beta binaries will also bring more testers, who possibly could notice something we might have overlooked  
<strong>\<fluffypony\></strong> ok  
<strong>\<TedTheFicus\></strong> Im down to test once the Betas are out  
<strong>\<fluffypony\></strong> we’ll need a point release of 0.10 to go with it  
<strong>\<fluffypony\></strong> so we should at least get through the current group of pending PRs before we do that  
<em><em>\<medusa</em>\></em>\* but we must communicate its for testing, since the seed is nowhere displayed after creation we dont want people to lose money  
<strong>\<moneromooo\></strong> It creates a keys file, right ?  
<strong>\<fluffypony\></strong> medusa\_: well that’s a pretty big issue :-P  
<em><em>\<medusa</em>\></em>\* yes  
<strong>\<fluffypony\></strong> ah ok  
<strong>\<fluffypony\></strong> so monero-wallet-cli could be shipped with it for recovery  
<strong>\<TedTheFicus\></strong> Good idea  
<strong>\<moneromooo\></strong> Well, you do need the daemon anyway, don’t you.  
<em><em>\<medusa</em>\></em>\* yes  
<strong>\<dEBRUYNE\></strong> \<fluffypony\> so monero-wallet-cli could be shipped with it for recovery \<= It’s able to recover seeds  
<strong>\<dEBRUYNE\></strong> It’s just that only in the wizard the seed is shown once  
<strong>\<dEBRUYNE\></strong> oh wait, you mean restore with the .keys file?  
<strong>\<fluffypony\></strong> yes I meant recovery as in “recover my seed from the .keys file”  
<strong>\<ArticMine\></strong> Recovery from seed is the issue with the GUI?  
<strong>\<dEBRUYNE\></strong> ah gotcha  
<strong>\<dEBRUYNE\></strong> No ArticMine, there isn’t a window yet to see your seed  
<strong>\<dEBRUYNE\></strong> after the initial wizard  
<strong>\<fluffypony\></strong> ArticMine: no - it just doesn’t display the seed again after the wizard  
<strong>\<fluffypony\></strong> and given how many MyMonero support emails I get where people didn’t write down their seed…  
<strong>\<dEBRUYNE\></strong> Should be fairly trivial to add though  
<strong>\<fluffypony\></strong> ok so that’s about it from my side - tewinget isn’t around to give us a 0MQ update  
<strong>\<fluffypony\></strong> hyc I don’t think has started tinkering with the walletDB stuff  
<strong>\<fluffypony\></strong> also the forum - I know, I’m working on it, moved all broken deps into monero-project repos to better manage them and am fixing the last few niggly issues  
<strong>\<dEBRUYNE\></strong> fluffypony: re: GUI, preferably we would have a tab that displays viewkey/seed/spendkey, the tab could be named Private Keys or something, with a big fat warning label :P  
<strong>\<dEBRUYNE\></strong> Like I said, should be fairly trivial to add  
<strong>\<fluffypony\></strong> dEBRUYNE: good idea - open an issue for it and let Ilya do it asap :)  
<strong>\<fluffypony\></strong> ok so we have 7 minutes before the Kovri meeting, any other things to discuss?  
<strong>\<dEBRUYNE\></strong> fluffypony: will do  
<strong>\<dEBRUYNE\></strong> NoodleDoodle isn’t here right?  
<strong>\<moneromooo\></strong> Who wants to volunteer to review some patches from time to time ? :)  
<strong>\<dEBRUYNE\></strong> moneromooo: Similiarly, would you be able to glance over / review the trezor XMR code?  
<strong>\<moneromooo\></strong> Where is it ?  
<strong>\<fluffypony\></strong> on NoodleDoodle’s computer  
<strong>\<dEBRUYNE\></strong> <https://github.com/NoodleDoodleNoodleDoodleNoodleDoodleNoo>  
<strong>\<dEBRUYNE\></strong> ^ moneromooo  
<strong>\<dEBRUYNE\></strong> he has some commits in his monero repository and in trezor-xmr  
<strong>\<fluffypony\></strong> :-P  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: I review many of them but I don’t spend enough time with the codebase to ack/nack  
<strong>\<moneromooo\></strong> anonimal, thanks :)  
<strong>\<moneromooo\></strong> dEBRUYNE: Do you know which one of the three repos is the right one ?  
<strong>\<moneromooo\></strong> xmr, common, mcu. xmr seems likely to be one at least.  
<strong>\<dEBRUYNE\></strong> oh trezor-xmr  
<strong>\<dEBRUYNE\></strong> and monero  
<strong>\<dEBRUYNE\></strong> So his commits here -\> <https://github.com/NoodleDoodleNoodleDoodleNoodleDoodleNoo/monero/commits/master?author=NoodleDoodleNoodleDoodleNoodleDoodleNoo>  
<strong>\<moneromooo\></strong> OK, I’ll keep that in mind then.  
<strong>\<dEBRUYNE\></strong> &amp; here -\> <https://github.com/NoodleDoodleNoodleDoodleNoodleDoodleNoo/trezor-xmr>  
<em><em>\<medusa</em>\></em>\* i can not review the code, but i can test specific pull requests if you guys explain me what you changed  
<strong>\<dEBRUYNE\></strong> trezor-mcu / trezor-common has no commits from NoodleDoodle moneromooo  
<em><em>\<moneromooo\>\*\* medusa</em>: 1082 and 1121 could do with some testing if you feel like it.  
<strong>\<moneromooo\></strong> And 1140 :)  
<strong>\<moneromooo\></strong> 1082 changes the way fake outs are selected  
<strong>\<cryptotekk\></strong> wow in this pace i see GUI by tonight lol  
<strong>\<moneromooo\></strong> 1121 replaces the sweep</em>unmixable code to be more stable and, well, better  
<strong>\<moneromooo\></strong> 1141 adds cold wallet signing  
\*\*\<medusa\*\>\*\* oh i can test 1141  
<em><em>\<medusa</em>\></em>\* i still have the setip from the —offline thing  
<strong>\<moneromooo\></strong> 1140, sorry. Off by one…  
<strong>\<fluffypony\></strong> oh no off by one bug\!  
<em><em>\<medusa</em>\></em>\* will have a look, thanks  
<strong>\<moneromooo\></strong> Mac, Linux, and Plan9.  
<strong>\<cryptotekk\></strong> android please  
<strong>\<liberte\></strong> lol  
<strong>\<fluffypony\></strong> hokay  
\*\*\<fluffypony\>\*\* that’s the end of that
