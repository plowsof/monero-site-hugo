---
title: Overview and Logs for the Dev Meeting Held on 2019-09-22
summary: Development status, 0.15 release discussion, Network upgrade planning, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> it's time  
<strong>\<rehrar\></strong> 1. Greetings  
<strong>\<rehrar\></strong> who all is here?  
<strong>\<sgp\_\></strong> hello :)  
<strong>\<needmonero90\></strong> Hi  
<strong>\<xmrscott\[m\]\></strong> Hey hey hey  
<strong>\<rbrunner\></strong> Hi  
<strong>\<tevador\></strong> hey  
<strong>\<sech1\></strong> \\o/  
<strong>\<ErCiccione\[m\]\></strong> Hi  
<strong>\<ferretinjapan\></strong> so everyone except the people rehrar pinged are here, nice.  
<strong>\<rehrar\></strong> it would seem so  
<strong>\<rehrar\></strong> moneromooo: do we have you at least? :P  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<rehrar\></strong> one last round for fluffypony luigi1111 ArticMine binaryFate  
<strong>\<rehrar\></strong> please join us ASAP  
<strong>\<rehrar\></strong> in the meantime, we can move on to 2. What's been completed since last meeting?  
<strong>\<vtnerd\_\_\></strong> here  
<strong>\<sech1\></strong> I've finished RandomX JIT compiler for ARM CPUs. Verification time is even better than CN/R on ARM.  
<strong>\<moneromooo\></strong> Pretty good stuff here.  
<strong>\<rbrunner\></strong> Nice  
<strong>\<ArticMine\></strong> Hi  
<strong>\<dEBRUYNE\></strong> I am here  
<strong>\<meksi\></strong> Hi  
<strong>\<tevador\></strong> so I guess we are including the ARM JIT in the release?  
<strong>\<tevador\></strong> probably no reason not to  
<strong>\<moneromooo\></strong> It can be disabled with an env var AFAIK so sure.  
<strong>\<tevador\></strong> just it hasn't been heavily tested as the x86 JIT  
<strong>\<SoiMatter\></strong> Sirs\! ferretinjapan asked moi to join.  
<strong>\<hyc\></strong> since it's easily toggled off, I'd say we run with it  
<strong>\<jtgrassie\></strong> hi  
<strong>\<SoiMatter\></strong> o7 I will keep still :)  
<strong>\<moneromooo\></strong> monerod can now synced from pruned blocks (optional). I'd like this to go in before release if reviewed.  
<strong>\<rehrar\></strong> Honest question to everyone, now that CLI has reproducible builds, can we as a community decide on a date without input from Core?  
<strong>\<selsta\></strong> GUI?  
<strong>\<rehrar\></strong> that's next selsta :P  
<strong>\<selsta\></strong> yes but it would be nice to release both the CLI and GUI at the same time and that depends on core  
<strong>\<moneromooo\></strong> Pony still controls the website (for binaries to be uploaded), and the DNS records (for the hashes of the binaries).  
<strong>\<rehrar\></strong> ok so there's distribution and GUI to consider  
<strong>\<dEBRUYNE\></strong> Pony said he'd be around for the CLI &amp; GUI release  
<strong>\<rehrar\></strong> I mean, ultimately we want to go along this road at some point to reduce centralization anyways, no?  
<strong>\<moneromooo\></strong> Also needs people to build for random OSes. Does Windows have repro builds too ?  
<strong>\<ArticMine\></strong> Do we have a release date in mind?  
<strong>\<dEBRUYNE\></strong> moneromooo: Yes  
<strong>\<dEBRUYNE\></strong> At least for the CLI  
<strong>\<ErCiccione\[m\]\></strong> ArticMine: i think the idea was to set a date today  
<strong>\<rehrar\></strong> so let's set one  
<strong>\<rehrar\></strong> ArticMine can represent the core team here  
<strong>\<sgp\_\></strong> October 26?  
<strong>\<rehrar\></strong> Are we thinking mid-October? End of October?  
<strong>\<dEBRUYNE\></strong> I would personally prefer a bit more towards the end of October, as that gives us a bit more leeway  
<strong>\<ArticMine\></strong> I do not ave an issue with setting a release date at this meeting  
<strong>\<ErCiccione\[m\]\></strong> i agree  
<strong>\<hyc\></strong> Let's go with October 31, Halloween  
<strong>\<tevador\></strong> is this the release date of the fork date?  
<strong>\<tevador\></strong> or\*  
<strong>\<hyc\></strong> it'll be scary  
<strong>\<moneromooo\></strong> I have some reservations about the stability of randomx-in-monerod. Bugs are still coming in fast.  
<strong>\<needmonero90\></strong> Monero's spoopy fork  
<strong>\<rehrar\></strong> tevador: fork date  
<strong>\<dEBRUYNE\></strong> tevador: fork date  
<strong>\<sech1\></strong> October 31 is a bit too late  
<strong>\<moneromooo\></strong> So pushing back would be good in my view :)  
<strong>\<ArticMine\></strong> and code freeze?  
<strong>\<rehrar\></strong> if mooo has reservations then maybe 31 is a decent date?  
<strong>\<rehrar\></strong> sech1: what's your reasoning?  
<strong>\<tevador\></strong> so better to not do it in the middle of the week  
<strong>\<luigi1111\></strong> I'm sorta here  
<strong>\<sech1\></strong> October 31 is kind of an edge of publicly promised "fork in October"  
<strong>\<sech1\></strong> October 26 sounds better  
<strong>\<moneromooo\></strong> I don't anyone (who counts) ever promised.  
<strong>\<hyc\></strong> assuming it's actually ready by then  
<strong>\<needmonero90\></strong> Welcome to decentralization sech1.  
<strong>\<rehrar\></strong> I am fine with 26th  
<strong>\<tevador\></strong> yeah, 26 October would be better if it's doable  
<strong>\<needmonero90\></strong> Community won't be too mad if we don't hit deadlines  
<strong>\<SoiMatter\></strong> Go with the date of the next UK election  
<strong>\<hyc\></strong> testnet has been disturbingly unstable the past few weeks.  
<strong>\<hyc\></strong> but most of the problems were unrelated to randomX  
<strong>\<Inge-\></strong> Better a safe launch than an october launch.  
<strong>\<ArticMine\></strong> One key point is the time between release and fork date  
<strong>\<rbrunner\></strong> Normal testnet or the RandomX testnet?  
<strong>\<hyc\></strong> randomX testnet  
<strong>\<hyc\></strong> but the issues with peers being disconnected and banned would have happened on public testnet too if anyone bothered to exercise that  
<strong>\<hyc\></strong> basically current git master is unstable, recent changes to the networking code broke a lot.  
<strong>\<sech1\></strong> if fork is October 26 (4 weeks), would 2 weeks be enough to fix all that?  
<strong>\<sech1\></strong> and would additional 5 days help?  
<strong>\<ErCiccione\[m\]\></strong> i'm starting to think would be better to posticipate to after october  
<strong>\<tevador\></strong> so it looks more like November  
<strong>\<ArticMine\></strong> Release and fork date ware very different  
<strong>\<dEBRUYNE\></strong> hyc: Those recent changes will be reverted by 5905 right?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<ArticMine\></strong> We need to give people time to update  
<strong>\<ErCiccione\[m\]\></strong> if there are so many doubts i would just wait. No reason to rush it, this is a big fork  
<strong>\<hyc\></strong> agreed, safer to wait  
<strong>\<rehrar\></strong> so really all of this should have been discussed two weeks to a month ago  
<strong>\<sgp\_\></strong> I don't think the optics of a "late" Oct 31 date will be terrible. We can get ahead of it with the Halloween marketing. If people prefer November, then I think we should still pick a date  
<strong>\<M5M400\></strong> will this release discontinue legacy payment IDs?  
<strong>\<rehrar\></strong> so for next time we really need to start seriously discussing the fork two months prior to "planned" date  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<moneromooo\></strong> Though currently not banned, just code removed.  
<strong>\<dEBRUYNE\></strong> rehrar: I don't think we could have foreseen the issues arosen on testnet  
<strong>\<moneromooo\></strong> Are any large exchanges still using them ?  
<strong>\<ArticMine\></strong> I suggest an October 31 release date with a fork date 4 weeks later  
<strong>\<luigi1111\></strong> late is far better than broken  
<strong>\<sgp\_\></strong> I can try to compile a list  
<strong>\<sech1\></strong> We still need to decide fork date and release schedule today  
<strong>\<rehrar\></strong> dEBRUYNE: literally every single fork there is a "I don't think we could have foreseen" situation?  
<strong>\<needmonero90\></strong> What happened to move fast and break things? This is tech\!  
<strong>\<dEBRUYNE\></strong> Yes because there will simply be things that cannot be foreseen  
<strong>\<dEBRUYNE\></strong> You cannot perfectly plan such a thing  
<strong>\<luigi1111\></strong> I too enjoy breaking money when possible  
<strong>\<rehrar\></strong> ok, ArticMine has made a concrete suggestion  
<strong>\<rehrar\></strong> 31st release date, one month later fork date  
<strong>\<sgp\_\></strong> one month? why one month?  
<strong>\<needmonero90\></strong> I think its reasonable.  
<strong>\<needmonero90\></strong> No objection here.  
<strong>\<ferretinjapan\></strong> luigi1111, I agree, late and working is far better than on time and buggy...  
<strong>\<hyc\></strong> is that the same offset we used in previous releases?  
<strong>\<M5M400\></strong> moneromooo: i have about 330 miners still mining to payment\_id addresses. that's 5 %  
<strong>\<sgp\_\></strong> no, closer to two weeks I think  
<strong>\<ArticMine\></strong> To give people proper notice to upgrade  
<strong>\<luigi1111\></strong> that's what it ended up being  
<strong>\<needmonero90\></strong> We were pushing to the wire last time  
<strong>\<needmonero90\></strong> To be fair  
<strong>\<luigi1111\></strong> we never targeted two weeks that's simply not ideal  
<strong>\<needmonero90\></strong> Two weeks was cutting it close  
<strong>\<ArticMine\></strong> This has been an issue many times before  
<strong>\<ErCiccione\[m\]\></strong> yeah, one month seems fair  
<strong>\<sech1\></strong> October 31st release and November 30th fork then?  
<strong>\<luigi1111\></strong> yes we've always pushed releases to late but doesn't mean we shouldn't try to do better  
<strong>\<ArticMine\></strong> sounds fine to me  
<strong>\<sgp\_\></strong> So what specific fork date?  
<strong>\<tevador\></strong> 30th Nov  
<strong>\<rbrunner\></strong> November 30 is again Saturday, which is nice  
<strong>\<sech1\></strong> let's hope CN/R holds without ASICs until then :)  
<strong>\<ArticMine\></strong> So when is code freeze?  
<strong>\<moneromooo\></strong> Whenever we don't have anything left we want to merge :)  
<strong>\<ErCiccione\[m\]\></strong> now with reproducible build releases should be much faster, at least for CLI. We rarely managed to release at the time we decided  
<strong>\<needmonero90\></strong> October 31st makes sense imo  
<strong>\<sgp\_\></strong> I think having a release in October will help with optics. And a 31st update is easy to brand  
<strong>\<rehrar\></strong> alright, it looks like we have a loose consensus, unless anyone would like to speak now  
<strong>\<ArticMine\></strong> Sure but how much time is needed between code freeze and release?  
<strong>\<rehrar\></strong> in opposition  
<strong>\<luigi1111\></strong> like a week  
<strong>\<luigi1111\></strong> but fluffy fluffy fluffy  
<strong>\<selsta\></strong> +1  
<strong>\<selsta\></strong> long code freezes never work  
<strong>\<rehrar\></strong> luigi1111: did not show  
<strong>\<dEBRUYNE\></strong> We only need fluffy to upload the bins though for the CLI release  
<strong>\<dEBRUYNE\></strong> (and do the website)  
<strong>\<luigi1111\></strong> I know but if he's building he has to be able to commit to a schedule  
<strong>\<sgp\_\></strong> so Thanksgiving weekend hardfork (Nov 30)  
<strong>\<sech1\></strong> yes, better safe than sorry  
<strong>\<hyc\></strong> since we have reproducible builds we don't need him to build  
<strong>\<dEBRUYNE\></strong> rehrar: He said he'd be available for the release (he'd prefer to have a timeline a bit in advance though)  
<strong>\<rehrar\></strong> luigi1111: if he's unable to commit to a schedule, then we can do the deterministic builds thing, and just make sure they get uploaded  
<strong>\<luigi1111\></strong> ok cool  
<strong>\<luigi1111\></strong> then just gooey  
<strong>\<rehrar\></strong> which is you  
<strong>\<ArticMine\></strong> The time between code freeze and release need to be set buy those closest to the code  
<strong>\<rehrar\></strong> can you commit to this schedule?  
<strong>\<dEBRUYNE\></strong> GUI gets build by pony  
<strong>\<rehrar\></strong> oof  
<strong>\<needmonero90\></strong> Speaking of build privs, I would like to formally propose that some of the GUI repo privileges be transferred to dsc (the non deterministic build part at the very least)  
<strong>\<M5M400\></strong> how can fluffy still be the only person able to do some vital things?  
<strong>\<luigi1111\></strong> I'm the one going to be doing all the merges in both projects so heh  
<strong>\<dEBRUYNE\></strong> rehrar: Third time and last time I will say -\> He said he'd be available for the release  
<strong>\<rehrar\></strong> M5M400: that's why deterministic builds is top priority  
<strong>\<rehrar\></strong> dEBRUYNE: ok  
<strong>\<ferretinjapan\></strong> M5M400, mainly because reproducible builds were never a thing before now.  
<strong>\<needmonero90\></strong> luigi1111: we really should move some of those responsibilities to dsc.  
<strong>\<dEBRUYNE\></strong> needmonero90: I disagree, then we would have coders merging their own stuff  
<strong>\<needmonero90\></strong> He would be the new maintainer/lead of gui  
<strong>\<needmonero90\></strong> Or something  
<strong>\<rehrar\></strong> ok, any other questions in regards to the set dates? October 31st release, November 30th fork.  
<strong>\<moneromooo\></strong> So what do we need for the release ? readline fixes for repro builds, randomx. The pay-for-service stuff. Payment ID changes. Hopefully the sync-pruned-blocks. Anything else that's large or really needed ?  
<strong>\<ferretinjapan\></strong> freeze date?  
<strong>\<rehrar\></strong> needmonero90: that would be the first time a non-core team member will have done this. Not impossible, but certainly unprecedented and worthy of a bigger discussion which we don't have time for here in this meeting  
<strong>\<dEBRUYNE\></strong> Once we branch the code is basically frozen right? Because then only fixes go in  
<strong>\<ErCiccione\[m\]\></strong> one week code freeze would be appreciated. Let's remember that there are the translation to deal with (and i beg for a code freeze since ever :D)  
<strong>\<needmonero90\></strong> Okay, tabled for now rehrar  
<strong>\<moneromooo\></strong> vtnerd\_\_: are you planning to have some more network stuff ready for the release ?  
<strong>\<ferretinjapan\></strong> I guess the \#monero-pow guys would have a better idea when to freeze...  
<strong>\<ArticMine\></strong> Oct 24th as per luigi1111 selsta?  
<strong>\<luigi1111\></strong> he's not the only one with access to a couple things but the only one that actively used his access  
<strong>\<dEBRUYNE\></strong> moneromooo: The readline fix is 5892 right?  
<strong>\<selsta\></strong> ArticMine: yes  
<strong>\<luigi1111\></strong> until recently where him and pigeons have both not been to active  
<strong>\<moneromooo\></strong> Could be. Depends on what people who have the problem say after testing it :)  
<strong>\<dEBRUYNE\></strong> ArticMine: I think we can branch earlier, but moneromooo probably has a better view on that  
<strong>\<ArticMine\></strong> moneromooo does Oct 24 work for code freeze?  
<strong>\<ErCiccione\[m\]\></strong> pigeons is active. I asked him to update the server of getmonero last time  
<strong>\<moneromooo\></strong> That sounds plausible to me.  
<strong>\<M5M400\></strong> moneromooo: it appears bittrex and binance still use payment\_id's  
<strong>\<ErCiccione\[m\]\></strong> and he also gave me a hand with weblate  
<strong>\<moneromooo\></strong> Thanks.  
<strong>\<vtnerd\_\_\></strong> moneromooo : yes, the split mempool is jst about done (finishing core tests nows)  
<strong>\<rehrar\></strong> wow  
<strong>\<dEBRUYNE\></strong> M5M400: Binance is working on upgrading their system, needmonero90 is in touch with them  
<strong>\<rehrar\></strong> vtnerd\_\_: so your stuff will make it in this one?  
<strong>\<vtnerd\_\_\></strong> and the dandelion++ remnants \_shouldn't\_ be too painful - although I always say that :/  
<strong>\<M5M400\></strong> dEBRUYNE: saifu. great.  
<strong>\<needmonero90\></strong> Binance indicated they should be ready by fork in October. Pushing the date back shouldnt hurt the timeline.  
<strong>\<M5M400\></strong> anyone in touch with bittrex?  
<strong>\<dEBRUYNE\></strong> They are aware as far as I know  
<strong>\<vtnerd\_\_\></strong> I can't say whether it will "make it in", because theres always a chance something comes up during review, etc  
<strong>\<vtnerd\_\_\></strong> but the split mempool for the i2p/tor is close to ready. my concern is that its kind of tough the way it got shoved in  
<strong>\<rbrunner\></strong> You mean in a technical sense?  
<strong>\<vtnerd\_\_\></strong> I took hyc's approach of adding a tag to the metadata, but I had to inspect a bunch of code paths to make sure stuff didn't leak  
<strong>\<binaryFate\></strong> hi all, sorry got late to the party  
<strong>\<vtnerd\_\_\></strong> ultimately a true "physical" or "logical" split would be ideal, but it seemed kind of tough at the momnent when I tried to think about hwo to do it  
<strong>\<moneromooo\></strong> Oh so it's a single txpool, just txes have a flag ?  
<strong>\<vtnerd\_\_\></strong> yeah, unfortunately  
<strong>\<M5M400\></strong> are we aware of any GPU miner in the works for randX that will be ready in time for spork?  
<strong>\<moneromooo\></strong> That's what I did for the sync-from-pruned :)  
<strong>\<hyc\></strong> M5M400: xmrig is ready  
<strong>\<luigi1111\></strong> 24th and 31st targets are good with me for 30th fork  
<strong>\<sech1\></strong> M5M400 xmrig 4.0 is combined CPU + OpenCL miner  
<strong>\<vtnerd\_\_\></strong> if thats worth a reject, then I can go back and try again, but its a little dicey otherwise (it requires a slightly larger refactor and possibly a second lmdb database)  
<strong>\<luigi1111\></strong> mostly afk now  
<strong>\<rehrar\></strong> vtnerd\_\_: if this does make it in this time, it can be iterated on in the future no?  
<strong>\<M5M400\></strong> hyc: sech1: nice  
<strong>\<moneromooo\></strong> It's not IMHO. I'd have done that too.  
<strong>\<moneromooo\></strong> But then I tend to shove things in :)  
<strong>\<vtnerd\_\_\></strong> yes, I don't think the patch makes it harder to refactor, its probably neutral from that perspective  
<strong>\<hyc\></strong> I don't really see other approaches to that as being a good idea  
<strong>\<tevador\></strong> btw, fork height could be 1978433, which is exactly the start of a RandomX epoch and should be in the afternoon CET on Nov 30th  
<strong>\<vtnerd\_\_\></strong> as an example of what I mean - one of the weird cases is that fluffy blocks request can leak the anonymity channel, etc, so yeah  
<strong>\<dEBRUYNE\></strong> tevador: Afternoon CET would allow most people to be online, because it would basically be late evening for Asia and morning for US  
<strong>\<moneromooo\></strong> And let's reset testnet to fork on an epoch boundary too ?  
<strong>\<tevador\></strong> dEBRUYNE: yeah, nice coincidence  
<strong>\<ErCiccione\[m\]\></strong> i guess we have a fork height. Nice  
<strong>\<rbrunner\></strong> With a testnet fork around release, end of October?  
<strong>\<hyc\></strong> sounds good  
<strong>\<dEBRUYNE\></strong> To summarize the timeline, this is approximately correct right? Branch within 2-3 weeks, freeze October 24, release October 31, fork November 30  
<strong>\<moneromooo\></strong> I think we have everything we need for v12 now, apart from randomx, so we can fork the real testnet as soon as it gets merged.  
<strong>\<rbrunner\></strong> Even better then  
<strong>\<tevador\></strong> that looks like a sensible schedule  
<strong>\<sech1\></strong> yes, plenty of time to iron out all issues  
<strong>\<rbrunner\></strong> Famous last words :)  
<strong>\<dEBRUYNE\></strong> It at least feels we are better prepared now than last time :-P  
<strong>\<tevador\></strong> someone should strictly enforce code freeze this time  
<strong>\<rehrar\></strong> penalty of death  
<strong>\<ErCiccione\[m\]\></strong> tevador: i strongly agree  
<strong>\<dEBRUYNE\></strong> moneromooo: Do we need pony around to fork the real testnet?  
<strong>\<PauleBert\></strong> can we reset stagenet too? it is getting quite huge  
<strong>\<moneromooo\></strong> Yes, the miner's one of his nodes, and seed nodes need updating too.  
<strong>\<moneromooo\></strong> The former's not a big problem, but the latter kinda is.  
<strong>\<needmonero90\></strong> Don't reset stagenet :(  
<strong>\<dEBRUYNE\></strong> Ok, I will send him a message then  
<strong>\<needmonero90\></strong> Telegram tipbot uses it  
<strong>\<rbrunner\></strong> "Reset" means here dropping a few hundreds of blocks probably, no new genesis block  
<strong>\<needmonero90\></strong> It'll wipe all our balances ;\_;  
<strong>\<rbrunner\></strong> Back to the latest epoc date, that is  
<strong>\<needmonero90\></strong> (yes, I know, it's stagenet)  
<strong>\<rbrunner\></strong> Or a few thousands ...  
<strong>\<M5M400\></strong> are we in any way concerned about the probably 10x hashrate post fork and the amount of blocks being spit out quickly? might it be a good idea to set a ballpark initial diff?  
<strong>\<hyc\></strong> I'm guessing that will be offset by the typical hashrate drop due to not everyone updating  
<strong>\<moneromooo\></strong> I am not.  
<strong>\<sech1\></strong> I don't think so. It'll rather grow slowly.  
<strong>\<rbrunner\></strong> I think to remember from earlier forks that "doctoring" the diff is not trivial  
<strong>\<sech1\></strong> Even with higher hashrate from CPUs, hard fork drop in hashrate will make initial diff roughly the same as now  
<strong>\<ferretinjapan\></strong> I wouldn't be worried un less ASICs were currently saturating the network, but by the sounds of it, theres been no indication of that being the case...  
<strong>\<M5M400\></strong> I've seen a few big miners on the pool that are most likely CPU based. one instance of 17MH cn/r. these operations don't miss forks, as opposed to casual miners  
<strong>\<sech1\></strong> No signs of ASICs  
<strong>\<ferretinjapan\></strong> thats good.  
<strong>\<rehrar\></strong> alright, is there anything else of note to discuss?  
<strong>\<ErCiccione\[m\]\></strong> minor: is it fine for everybody if we take down the current warning on getmonero, it's there since last fork  
<strong>\<needmonero90\></strong> We need to talk about extending the Monero Foundation's Dev tax, and the Monero name trademark issue  
<strong>\<ErCiccione\[m\]\></strong> i want to avoid people not reading it because they are used to it when we put up the new one  
<strong>\<needmonero90\></strong> Oh wait wrong coin  
<strong>\<needmonero90\></strong> We good  
<strong>\<hyc\></strong> ErCiccione\[m\]: good idea  
<strong>\<rbrunner\></strong> Yeah, take it down before it gets a running gag or something  
<strong>\<rbrunner\></strong> "Monero mixes up its hardforks"  
<strong>\<rehrar\></strong> alright  
<strong>\<ErCiccione\[m\]\></strong> alright, will open a PR tomorrow  
<strong>\<rehrar\></strong> alright friends, it would seem we're all good  
<strong>\<needmonero90\></strong> Is Gui considered core?  
<strong>\<needmonero90\></strong> Or is it it's own thing  
<strong>\<hyc\></strong> dEBRUYNE: now that randomx has quieted down I'll get to rebasing that gitian PR of mine  
<strong>\<ErCiccione\[m\]\></strong> needmonero90: that's actually a good question. See <https://github.com/monero-project/meta/issues/384>  
<strong>\<selsta\></strong> Please no renaming discussion.  
<strong>\<selsta\></strong> The github issue is a better place for that.  
<strong>\<rehrar\></strong> alright everyone, we'll officially break for today  
<strong>\<rehrar\></strong> thanks for coming. Good discussion, and got a lot done.  
<strong>\<hyc\></strong> who's posting meeting logs?  
<strong>\<rehrar\></strong> We can continue on a two weeks schedule for now? Or want to go to one week mini-check in on off weeks?  
<strong>\<ErCiccione\[m\]\></strong> hyc: el00ruobuob, usually  
<strong>\<hyc\></strong> ok.  
<strong>\<hyc\></strong> I think next mtg in 2 weeks is fine. after that, we can decide again  
<strong>\<rehrar\></strong> ok  
<strong>\<ErCiccione\[m\]\></strong> unles you didn't mean on getmonero  
<strong>\<rehrar\></strong> sounds good  
<strong>\<dEBRUYNE\></strong> hyc: Thanks  
<strong>\<dEBRUYNE\></strong> ErCiccione\[m\]: I'd prefer to update it with a general information thread regarding the upcoming fork  
<strong>\<dEBRUYNE\></strong> I can have that ready next week  
<strong>\<ErCiccione\[m\]\></strong> dEBRUYNE: sure\! will you PR it on repo.getmonero?  
<strong>\<IRC-Source\_89\></strong> guys sorry for the question , but i missed the begining of the discussion... Have you already choosen a block height for the fork?  
<strong>\<scoobybejesus\></strong> tevador\> btw, fork height could be 1978433, which is exactly the start of a RandomX epoch and should be in the afternoon CET on Nov 30th  
<strong>\<dEBRUYNE\></strong> ErCiccione\[m\]: Sure  
<strong>\<scoobybejesus\></strong> there seemed to be rough consensus on that  
<strong>\<IRC-Source\_89\></strong> thank you  
<strong>\<ErCiccione\[m\]\></strong> dEBRUYNE: great, thank you. Ping el00ruobuob\_ so he remembers to not PR it  
<strong>\<dEBRUYNE\></strong> I don't mind if he PRs it  
<strong>\<ErCiccione\[m\]\></strong> he usally PR them after more than one week, should be fine  
<strong>\<dEBRUYNE\></strong> Are we talking about the same thing? :P  
<strong>\<dEBRUYNE\></strong> I was referring to the new information thread regarding the fork  
<strong>\<ErCiccione\[m\]\></strong> I was talking about the logs :P i understood you wanted to include them in the thread.  
<strong>\<ErCiccione\[m\]\></strong> but anyway, we should really make a blog post about it.  
<strong>\<sech1\></strong> So will the schedule be officially announced soon?  
<strong>\<rbrunner\></strong> sgp\_ was fast: <https://old.reddit.com/r/Monero/comments/d7twle/tentative\_monero\_015\_release\_schedule/>  
<strong>\<hyc\></strong> sgp already announced it  
<strong>\<dEBRUYNE\></strong> sgp\_: Perhaps worthwhile to mention in the comments why there is a bit of a delay  
<strong>\<sgp\_\></strong> I don't know what happened with testnet  
<strong>\<ErCiccione\[m\]\></strong> el00ruobuob\_ ignore what i said earlier, we need the logs :P
