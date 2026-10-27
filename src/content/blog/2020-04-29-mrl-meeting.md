---
title: Logs for the MRL Meeting Held on 2020-04-29
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> OK, let’s get started with the research meeting\!  
<strong>\<sarang\></strong> First, GREETINGS  
<strong>\<sarang\></strong> hi  
<strong>\<ArticMine\></strong> hi  
\<\[keybase\] unseddd\>: o7  
<strong>\<UkoeHB\_\></strong> hi  
<strong>\<sarang\></strong> Let’s go ahead and continue with the ROUNDTABLE  
<strong>\<sarang\></strong> Anyone is welcome to share research topics of interest  
<strong>\<sarang\></strong> I suppose that I can share a few things  
<strong>\<sarang\></strong> Relating to timelocks, I extended CLSAG and Triptych to support them  
<strong>\<sarang\></strong> CLSAG: <https://github.com/SarangNoether/monero/commit/28f098260c5bb4da57bb78ebc885fe27c9f10c39>  
<strong>\<sarang\></strong> Triptych: <https://github.com/SarangNoether/monero/commit/ed48ab1686b7e7405bd6656c18e37ea21e01fe05>  
<strong>\<sarang\></strong> Here is corresponding timing data: <https://usercontent.irccloud-cdn.com/file/dQXuFH2U/timing.png>  
<strong>\<sarang\></strong> 3-CLSAG and 3-Triptych are the timelock-friendly data series  
<strong>\<sarang\></strong> The other data series are unchanged from when I first shared them  
<strong>\<sarang\></strong> I suspect that 3-CLSAG could be optimized by perhaps another 10% or so from what appears on the plot  
<strong>\<sarang\></strong> Unrelated to this, I’m updating how in-memory key encryption is handled, which is taking a bit longer than expected  
<strong>\<sarang\></strong> and am reviewing the new CLSAG fuzzer tool that unseddd provided  
<strong>\<sarang\></strong> That’s about it from me\!  
<strong>\<sarang\></strong> Are there any questions that I can answer?  
<strong>\<Isthmus\></strong> Nice work  
<strong>\<sarang\></strong> Thanks\!  
<strong>\<ArticMine\></strong> CLSAG optimization in verification time, size or both  
\<\[keybase\] unseddd\>: seconded, nice stuff sarang  
<strong>\<sarang\></strong> ArticMine: in verification time, and only for the new 3-CLSAG variant that would apply to encrypted timelocks  
<strong>\<ArticMine\></strong> Great work by the way  
<strong>\<ArticMine\></strong> Thanks  
<strong>\<sarang\></strong> When I wrote 3-CLSAG, I used a particular multiscalar multiplication that could likely be made faster for this particular case  
<strong>\<sarang\></strong> Also, huge thanks to unseddd for reviewing CLSAG and writing the fuzzer tool  
\<\[keybase\] unseddd\>: is 3-CLSAG limiting the multisig to three parties?  
\<\[keybase\] unseddd\>: np :)  
<strong>\<sarang\></strong> No, it adds another key component that would be used for timelocks  
<strong>\<sarang\></strong> Right now we have two key components: one for the usual signing, and the other for balance purposes  
\<\[keybase\] unseddd\>: ah, thanks for the clarification  
<strong>\<sarang\></strong> Does anyone else wish to share research of interest?  
<strong>\<UkoeHB\_\></strong> it seems like 3-triptych would reduce the ringsize likely to be selected by a power of 2  
\<\[keybase\] unseddd\>: not much interesting on my end. just reading formal verification papers + some pq-crypto stuff from Mike Hamburg  
<strong>\<sarang\></strong> Adding encrypted timelocks is a nontrivial verification hit  
<strong>\<ArticMine\></strong> What is the time ans size cost  
<strong>\<sarang\></strong> What might be interesting as an alternative would be to allow cleartext timelocks, but update decoy selection to account for known spend patterns  
<strong>\<sarang\></strong> It would not eliminate fingerprinting, but could help to mitigate age-related selection heuristics  
\<\[keybase\] unseddd\>: are there any leakage issues having the timelock in the clear?  
<strong>\<sarang\></strong> ArticMine: going from CLSAG to 3-CLSAG is about 1.4x increase in verification time  
<strong>\<sarang\></strong> Which could probably be reduced slightly with some extra work  
<strong>\<sarang\></strong> In terms of size it’s fairly trivial… adding an extra auxiliary key image (this does not account for other non-signature data)  
<strong>\<sarang\></strong> unseddd: for sure  
<strong>\<sarang\></strong> I’m not saying that I advocate for such an approach, only that it could be an option  
<strong>\<sarang\></strong> and would not imply any size/time hits  
<strong>\<UkoeHB\_\></strong> it’s a ways down the road, but I’d like to mention it now; when deciding ring sizes for next gen tx protocol I feel it should be based on a broader analysis of theoretical maximum tx throughput of the network; this is because the max tx volume is when rings are \_least\_ useful to defend against non-scaling graph heuristics, and because larger ring sizes actually reduce the max tx volume; it’s an optimization  
<strong>\<UkoeHB\_\></strong> problem  
\<\[keybase\] unseddd\>: right, from a naive perspective, triptych seems like it has enough savings for the hit from timelocks  
<strong>\<sgp\_\></strong> sorry I’m late. catching up  
<strong>\<ArticMine\></strong> UkoeHB\_ The maximum tx throughput is also dependent on external factor tat keep improving over time  
<strong>\<UkoeHB\_\></strong> unfortunately that optimization depends on the efficacy of ring sizes.. which we don’t have a complete understanding of; I hope suraeNoether can return to that topic at some point  
<strong>\<UkoeHB\_\></strong> ArticMine: true, there are a lot of factors to consider\!  
<strong>\<sarang\></strong> At the very least, we now have concrete numbers for the spacetime effects of ring size increases  
<strong>\<atoc\></strong> hi  
<strong>\<sgp\_\></strong> the cost of encrypted timelocks seems extreme to me tbh. I don’t want to go there unless we know we need to support them for a good use-case  
<strong>\<sarang\></strong> Getting timelock-related spend age data from transparent chains might be helpful if it’s decided to continue to allow cleartext timelocks  
<strong>\<sarang\></strong> Then output selection could be improved to account for it, and reduce the usefulness of spend-age heuristics  
\<\[keybase\] unseddd\>: use-case: timelocks necessary for atomic swap, encrypting is the most private  
\<\[keybase\] unseddd\>: could also see the counter-point for clear timelocks if they are necessary for atomic swaps (interop w/ clear chains maybe)  
<strong>\<sgp\_\></strong> sarang: I agree, but given the current low utilization, I consider this low priority. The impact to the wider network is negligible  
<strong>\<ArticMine\></strong> Payment channels come to mind here  
<strong>\<ArticMine\></strong> also escrow  
<strong>\<sarang\></strong> Getting that kind of transparent chain data seems pretty straightforward  
<strong>\<sgp\_\></strong> if there’s a payment channel, then we can move to make encrypted mandatory. when that happens  
<strong>\<Isthmus\></strong> @sarang, it’s on my to-do list for XMR and BTC  
<strong>\<sarang\></strong> :D  
<strong>\<sarang\></strong> How do you plan to examine spend-age data for XMR?  
<strong>\<sarang\></strong> It was examined in Miller for “deducible” outputs (pretty sure that’s the term they used) that were the result of chain reactions, which we find don’t occur anymore  
<strong>\<Isthmus\></strong> Oh, I just meant comparing the unlock time height to block height to see how many of them even make sense  
<strong>\<Isthmus\></strong> Not that current usage tells us much about future applications.  
<strong>\<sarang\></strong> Ah, got it  
<strong>\<Isthmus\></strong> What is it that you were interested in?  
<strong>\<atoc\></strong> Isthmus are you thinking about atomic swaps these days at all/  
<strong>\<Isthmus\></strong> @sarang sorry I’m in a zoom call and IRC meeting at the same time, and missing little pieces of both  
<strong>\<sarang\></strong> I’d like to see the age distribution of spent outputs in a transparent asset (like BTC) relative to lock expiration, to see if it differs substantially from the overall age distribution  
<strong>\<sarang\></strong> No problem Isthmus\!  
<strong>\<Isthmus\></strong> ahhh, yea I can’t officially do that for Monero yet. I’ll pull it for BTC though.  
<strong>\<UkoeHB\_\></strong> can’t officially? it’s possible?  
<strong>\<sarang\></strong> Thanks\! The overall distribution likely is still similar to the Miller data  
<strong>\<sarang\></strong> (for BTC, of course)  
<strong>\<sarang\></strong> and having that data would be an interesting check of that  
<strong>\<Isthmus\></strong> @UkoeHB\_ yeah, I mean my research over the past few years reveals anonymity puddles covering like 20% of transactions. Then change outputs bleed everything, so there’s a ton of data on obviously real spend times. BUT no guarantee that it’s representative.  
<strong>\<Isthmus\></strong> I’ll be supper curious to see the BTC distributions, will try to get that in the next week or so.  
<strong>\<Isthmus\></strong> \*super  
<strong>\<sarang\></strong> Yeah, Miller’s team used two different large sets of blocks in BTC for their analysis  
<strong>\<sarang\></strong> and found the distributions to be similar  
<strong>\<sarang\></strong> but it doesn’t appear they accounted for locks  
<strong>\<sarang\></strong> OK, did anyone else have a topic to discuss?  
<strong>\<Isthmus\></strong> Insight is interested in researching practical post-quantum cryptography for Monero, especially privacy features that will remain secure against retrospective deanonymization by future adversaries that can utilize Shor’s algorithm, Grover’s algorithm, etc. I want to know what our options are, and their costs (complexity, proof size, generation/verification time, etc)  
<strong>\<Isthmus\></strong> <https://github.com/insight-decentralized-consensus-lab/post-quantum-monero/blob/master/README.md>  
<strong>\<Isthmus\></strong> Looking for feedback on the research plan.  
<strong>\<Isthmus\></strong> Our goals are to (1) study and simulate the threats listed above to assess vulnerability to quantum computers, (2) evaluate post-quantum cryptography scheme candidates to create a roadmap for hardening Monero against quantum adversaries, and (3) provide open-source proof-of-concept code and demos where applicable.  
\<\[keybase\] unseddd\>: i like pq stuff :) will take a look  
<strong>\<sarang\></strong> Sounds like a fascinating project  
<strong>\<sarang\></strong> I’d be very curious to see what exactly the Phase 3 deliverables would look like  
<strong>\<Isthmus\></strong> Me too\! ^\_^  
<strong>\<sarang\></strong> and I think it’d be important to assess any transtion points between constructions/protocols  
<strong>\<sarang\></strong> e.g. it was possible to transition from pre-CT to post-CT  
<strong>\<Isthmus\></strong> Yeah, we’ll have to document both the transition and post-transition costs/tradeoffs  
<strong>\<sarang\></strong> New constructions are great, but if it’s not possible/feasible to transition on the same chain, that’s a sticking point  
\<\[keybase\] unseddd\>: here is the Hamburg paper i am reading through: <https://www.shiftleft.org/papers/qromcca/>  
<strong>\<ArticMine\></strong> Yes this is a very interesting project  
<strong>\<sarang\></strong> Are you confident about the timeline?  
<strong>\<sarang\></strong> Particularly surrounding the Phase 3 stuff  
<strong>\<sarang\></strong> (not that practical quantum computers are expected by the end of summer…)  
<strong>\<Isthmus\></strong> There’s two types of things we could prototype  
<strong>\<UkoeHB\_\></strong> it does say May - June, only a couple days away, not sure if a CCS could be approved and funded in time  
\<\[keybase\] unseddd\>: ten million qubits by fall\!\!\!  
<strong>\<Isthmus\></strong> (1) demo of a quantum computer breaking a Monero encryption feature (at a reduced keysize, or something like that)  
<strong>\<UkoeHB\_\></strong> s/June/July  
<strong>\<monerobux\></strong> UkoeHB\_ meant to say: it does say May - July, only a couple days away, not sure if a CCS could be approved and funded in time  
<strong>\<Isthmus\></strong> Adam did this before, got an IBM quantum computer mining bitcoin at shorter hash length  
<strong>\<Isthmus\></strong> So that’s demo breaking classical crypto  
<strong>\<Isthmus\></strong> (2) prototype a possible solution  
<strong>\<Isthmus\></strong> (so we’d use traditional computers and prototype a future solution)  
\<\[keybase\] unseddd\>: \_thoroughly impressed\_  
<strong>\<Isthmus\></strong> Now honestly, I think that \#2 would be way cooler. But it also may be hopeful thinking  
<strong>\<Isthmus\></strong> I’ve seen Adam rapidly convert math papers to code before, but this is going to be a pretty serious endeavor  
<strong>\<sarang\></strong> Either way, would be fascinating  
<strong>\<Isthmus\></strong> here was my note in the writeup  
<strong>\<Isthmus\></strong> “Phase 3 deliverables: The best use of time during this final stage depends strongly on results from the exploratory research. Likely deliverables are a proof of concept or prototype tooling for demonstrating a vulnerability or potential solution”  
<strong>\<UkoeHB\_\></strong> would (1) also include a comparison with a classical computer on the same task? at reduced keysizes, the encryption is weaker on classical computers too  
\<\[keybase\] unseddd\>: Isthmus: are Adam and you regularly in IRC? what is best communication channel?  
<strong>\<Isthmus\></strong> @UkoeHB\_ exactly  
<strong>\<Isthmus\></strong> Adam’ll be on IRC shortly :- )  
<strong>\<Isthmus\></strong> We’ll probably do a lot of the research in this room, if that’s okay with people?  
<strong>\<Isthmus\></strong> Or could make \#pq-mrl  
<strong>\<sarang\></strong> Up to you\!  
<strong>\<Isthmus\></strong>  
<strong>\<sarang\></strong> OK, any other topics to address before finishing up the meeting?  
<strong>\<UkoeHB\_\></strong> does anyone have new thoughts on <https://github.com/monero-project/monero/issues/6456>?  
\<\[keybase\] unseddd\>: UkoeHB\_: unfortunately no, have been consumed elsewhere. many apologies  
<strong>\<sarang\></strong> UkoeHB\_: I got unexpectedly caught up in other coding, and didn’t review in detail yet :/  
<strong>\<Isthmus\></strong> Oh\! Yeah, I’ll look at that by Monday. Hopefullly today  
<strong>\<sarang\></strong> my aopologies  
<strong>\<sarang\></strong> s/aopologies/apologies  
<strong>\<monerobux\></strong> sarang meant to say: my apologies  
<strong>\<sarang\></strong> All righty, any ACTION ITEMS for the next week to share?  
<strong>\<sarang\></strong> I will be reviewing 6456, reviewing some CLSAG tests, updating some in-memory encryption code, etc.  
<strong>\<Isthmus\></strong> I’ll probably bump the pq-monero proposal over to CCS by EOW, so shoot me a message (irc or <isthmus@getmonero.org> works) if you have any suggestions for updates or additions  
<strong>\<UkoeHB\_\></strong> on a certain level I have nothing else to contribute to the proposal; whether it gets implemented or not is out of my control; keep in mind it likely won’t be superseded by anything, so for ‘tx extra’, ‘janus mitigation’, ‘tx pub keys’, and ‘view tag’, that’s the ‘final answer’ for the forseeable future  
<strong>\<atoc\></strong> I’m working on some slides (summary) that details how Grin does their grin-btc atomic swap  
<strong>\<atoc\></strong> looking to see if we can get some insight for xmr-btc swaps  
<strong>\<hyc\></strong> Iǘe become convinced that itś never in any XMR holders’interest to swap for BTC, due to BTC taint issues  
<strong>\<hyc\></strong> but I’d be curious to see how it can work, for future XMR(earth)/XMR(mars) swaps  
\<\[keybase\] unseddd\>: hyc: even for true DEX scenario?  
\<\[keybase\] unseddd\>: marsero  
<strong>\<hyc\></strong> especially for true DEX, wher eyou can’t vet the BTC  
<strong>\<hyc\></strong> the benefits are all one-sided, in favor of the BTC seller  
<strong>\<Isthmus\></strong> Eh if I’ve got a wallet full of Monero, but the sandwich shop I’m standing in only takes BTC, I might find that swap useful.  
<strong>\<ArticMine\></strong> I have to agree with hyc Selling XMR for BTC on a swap is very dangerous  
\<\[keybase\] unseddd\>: yeah, i see your point. do you have the same opinion for other swap pairs?  
<strong>\<hyc\></strong> if the other pairs also involve transparent coins, yes  
<strong>\<sgp\_\></strong> +1 concern here  
<strong>\<sarang\></strong> Well, in the interest of time (our hour is up), I’ll adjourn the meeting for log purposes, but discussion can of course continue
