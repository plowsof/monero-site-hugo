---
title: Logs for the Monero Research Lab Meeting Held on 2018-07-30
summary: Sarang work, others work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> We can start now  
<strong>\<sarang\></strong> Greetings  
<strong>\<sarang\></strong> This will be a brief meeting to catch up on recent research  
<strong>\<sarang\></strong> All bulletproof audits have completed  
<strong>\<sarang\></strong> Kudelski's final report is posted. QuarksLab is updating theirs with our responses before releasing their final version. Benedikt Bunz is updating his similarly with our feedback.  
<strong>\<silur\></strong> yaay  
<strong>\<sarang\></strong> I continue to work on some new ring signature algos from Ruffing et al.  
<strong>\<oneiric\_\></strong> very nice, excited to read the most recent reports  
<strong>\<sarang\></strong> lots of fun building blocks with that scheme  
<strong>\<sarang\></strong> and suraeNoether has provided a multisig paper for me to review  
<strong>\<sarang\></strong> that is also in progress  
<strong>\<sarang\></strong> any questions on these things in particular?  
<strong>\<silur\></strong> let's collaborate on that I have an implemaentation on the first paper version  
<strong>\<silur\></strong> C, openssl  
<strong>\<sarang\></strong> silur: sure, the initial parts of the prototype are on my repo, rupol branch, in python  
<strong>\<silur\></strong> been working on rtrs for a long time  
<strong>\<silur\></strong> okay, will write you after the meeting  
<strong>\<sarang\></strong> anything in particular to share regarding your rtrs silur ?  
<strong>\<silur\></strong> well we just have to update it to the new-new-new construction  
<strong>\<silur\></strong> I only have the unpublished internal version of the first paper  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> We shall talk afterward  
<strong>\<sarang\></strong> Any other interesting work to be shared?  
<strong>\<endogenic\></strong> anyone see a problem with running openssl transpiled via emscripten in a browser?  
<strong>\<sarang\></strong> I feel extremely not qualified to answer that properly  
<strong>\<andytoshi\></strong> endogenic: openssl, transpiling, emscripten, and browsers are all bad for security  
<strong>\<endogenic\></strong> yep, no worries, just throwing it out there  
<strong>\<sarang\></strong> lol  
<strong>\<endogenic\></strong> then why does monero use it lol  
<strong>\<silur\></strong> where?  
<strong>\<andytoshi\></strong> monero is writtcen in C++  
<strong>\<endogenic\></strong> common/util.cpp (LOL) \#include \<openssl/sha.h\>... ringct/bulletproofs.cc \#include \<openssl/ssl.h\> ...  
<strong>\<silur\></strong> yea but where do we transpile it with emscripten?  
<strong>\<endogenic\></strong> just asking  
<strong>\<silur\></strong> I don't really recommend that  
<strong>\<endogenic\></strong> any specific reason?  
<strong>\<silur\></strong> don't know about emscripten internals but we used to have a thing called openssl code health tuesdays  
<strong>\<silur\></strong> after a month we eliminated 40K dead lines and 8 dead platforms  
<strong>\<silur\></strong> I think that's a reason not to include it in browsers  
<strong>\<endogenic\></strong> emscripten handles that sort of stuff  
<strong>\<andytoshi\></strong> there are lots of reasons that projects might have an openssl dep (bitcoin had one for a while). it takes time to eliminate it as other options are developed  
<strong>\<silur\></strong> also it has lots of inline ASM stuff how does emscripten handle that?  
<strong>\<andytoshi\></strong> but in all seriousness, if you're doing crypto in a browser, you should stop, because it's snake oil. a browser cannot run code in a secure environment.  
<strong>\<needmoney90\></strong> Did anyone check out the paper I posted last week?  
<strong>\<needmoney90\></strong> <https://arxiv.org/abs/1702.07588>  
<strong>\<andytoshi\></strong> <http://matasano.com/articles/javascript-cryptography/>  
<strong>\<endogenic\></strong> andytoshi: people are going to run worse web wallets if we don't  
<strong>\<endogenic\></strong> run one that is  
<strong>\<needmoney90\></strong> I'm curious if FHE can be used for remote node syncing, to allow us to make queries on encrypted data  
<strong>\<endogenic\></strong> silur: 1sec  
<strong>\<andytoshi\></strong> needmoney90: you want PIR for that, not FHE. and there are existing PIR primitives that are actually implemented and usable (see percy++)  
<strong>\<needmoney90\></strong> It's possible that due to our static append only data set that we can't actually hide access patterns  
<strong>\<silur\></strong> needmoney90 thanks a lot, it seems super interesting  
<strong>\<needmoney90\></strong> Never heard of PIR, got a paper for me?  
<strong>\<needmoney90\></strong> Maybe I just don't know the acronym  
<strong>\<sarang\></strong> private information retrieval  
<strong>\<silur\></strong> lots of stuff on PIR  
<strong>\<silur\></strong> thanks for percy++, i'm working with pir a lot for riffle  
<strong>\<silur\></strong> where do we need that btw?  
<strong>\<silur\></strong> in monero?  
<strong>\<endogenic\></strong> silur: emscripten might not be able to handle it, depending on exactly what's there. i guess maybe an alternative implementation exists  
<strong>\<endogenic\></strong> people seem to have been able to do it , in any case  
<strong>\<endogenic\></strong> 🤞  
<strong>\<oneiric\_\></strong> is boringssl an option for you?  
<strong>\<endogenic\></strong> oh  
<strong>\<endogenic\></strong> ./configure --no-asm  
<strong>\<endogenic\></strong> of course  
<strong>\<endogenic\></strong> oneiric\_: not to ignore you - i'll investigate if it becomes necessary  
<strong>\<sarang\></strong> Anyone else wish to share something intriguing on their minds?  
<strong>\<sarang\></strong> Also welcome andytoshi  
<strong>\<isthmuscrypto\></strong> Oh, I can give a \#noncense-research-lab summary  
<strong>\<sarang\></strong> please  
<strong>\<isthmuscrypto\></strong> Lots of action in the Monero Archival Project this week. @n3ptune released a new version of our custom archival daemon, and @serhack has been working wonders, configuring and maintaining our network of global VPS-based nodes.  
<strong>\<isthmuscrypto\></strong> I have been playing around with temporal analysis of the blockchain. Miner-reported timestamps were shown to be very unreliable, since 2% of blocks include a timestamp that is \*before\* the timestamp of the block prior.  
<strong>\<isthmuscrypto\></strong> These time-traveling Merlin blocks showed up while scoping out the distribution of wait times. <https://usercontent.irccloud-cdn.com/file/tLUEZ9aU/ttblocks.png> // Looking at the wait times for the block above and below the Merlin blocks themselves, we see that it is skewed toward a longer interval afterward, suggesting that they are actually being retroactively timestamped.  
<strong>\<isthmuscrypto\></strong> Our new daemon (upgraded last night) records the node-receipt timestamp(s) in addition to the miner-reported timestamp, so expect some way more detailed analysis of that soon.  
<strong>\<isthmuscrypto\></strong> I'm a little exploratory study of how fast the blockchain syncs at each height. It's mostly a cute novelty, but if there are interesting features (e.g. discontinuities around introduction of new tech), or notable conclusions about empirical scaling, I'll share back here.  
<strong>\<isthmuscrypto\></strong> (/end)  
<strong>\<isthmuscrypto\></strong> Whoops, here's the second link, showing the skew in wait times before and after Merlin blocks: <https://usercontent.irccloud-cdn.com/file/f46p6Ddd/merlin\_parent\_child>  
<strong>\<sarang\></strong> this is very interesting work  
<strong>\<andytoshi\></strong> sarang: we've made a lot of progress on musig recently; you can see <https://github.com/apoelstra/secp256k1/blob/2018-04-taproot/src/modules/musig/musig.md> for our current API. may have insights valuable to monero in future when you guys support arbitrary multisigs  
<strong>\<sarang\></strong> oh excellent, thanks  
<strong>\<isthmuscrypto\></strong> Shoot, I gave the wrong channel above. \#noncesense-research-lab  
<strong>\<sarang\></strong> andytoshi: what are the overall plans for musig?  
<strong>\<andytoshi\></strong> sarang: well, musig signatures verify identically to schnorr..  
<strong>\<andytoshi\></strong> so the goal is for bitcoin to support schnorr as part of taproot  
<strong>\<andytoshi\></strong> and then wallets would implement musig if they're doing multisig stuff  
<strong>\<andytoshi\></strong> since the resulting multisigs would be smaller/more private than ones using CHECKMULTISIG  
<strong>\<sarang\></strong> Great, so laying the groundwork for future wallet code  
<strong>\<sarang\></strong> cool  
<strong>\<sarang\></strong> It seems fairly quiet here otherwise today, so any other material to share?  
<strong>\<andytoshi\></strong> not really, i've mostly been doing rust-bitcoin ecosystem work  
<strong>\<endogenic\></strong> yknow people have been transpiling rust to JS too :P  
<strong>\<silur\></strong> and wasm :D  
<strong>\<endogenic\></strong> well that's what i mean :P  
<strong>\<silur\></strong> wasm openssl is not a bad idea tho  
<strong>\<silur\></strong> looks like I have a new sideproject  
<strong>\<endogenic\></strong> oh that's just what i'm talking about...  
<strong>\<endogenic\></strong> whoever beats the other to it i guess  
<strong>\<endogenic\></strong> it's easy enough  
<strong>\<endogenic\></strong> i have instructions.. :P  
<strong>\<endogenic\></strong> i have boost transpiled already..  
<strong>\<sarang\></strong> Well, I think we can safely call the meeting then, everyone can continue performing admirably
