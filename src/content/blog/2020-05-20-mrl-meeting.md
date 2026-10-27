---
title: Logs for the MRL Meeting Held on 2020-05-20
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<sarang\></strong> hello  
<strong>\<sgp\_\></strong> hello  
<strong>\<dEBRUYNE\></strong> hi  
<strong>\<telapongo23\></strong> Hi guys, just eavesdropping here :-D  
<strong>\<hyc\></strong> hello  
<strong>\<sarang\></strong> Let's move to ROUNDTABLE, where anyone is welcome to share research topics of interest  
<strong>\<sarang\></strong> Who wishes to share something? (I saw Isthmus just posted to the agenda issue)  
<strong>\<ArticMine\></strong> Hi  
<strong>\<sarang\></strong> I suppose that I can share a few items  
<strong>\<sarang\></strong> First, I'll review some Arcturus numbers, some of which were presented last week  
<strong>\<sarang\></strong> Recall that Arcturus is a modification of Triptych that needs only one proof per transaction, instead of one proof per spend  
<strong>\<h4sh3d\[m\]\></strong> Hi  
<strong>\<sarang\></strong> (making it similar to RCT3's update and Omniring)  
<strong>\<sarang\></strong> I'll link some plots...  
<strong>\<sarang\></strong> Size data for 1 input: <https://usercontent.irccloud-cdn.com/file/DYMoX7jy/size-1.png>  
<strong>\<sarang\></strong> Size data for 2 inputs: <https://usercontent.irccloud-cdn.com/file/7Hw5Wnsv/size-2.png>  
<strong>\<sarang\></strong> Size data for 16 inputs: <https://usercontent.irccloud-cdn.com/file/QzJ03VBI/size-16.png>  
<strong>\<sarang\></strong> You can see the improvement as the number of inputs increases  
<strong>\<sarang\></strong> From last week, I'll re-post the timing data...  
<strong>\<sarang\></strong> Verification timing for 1-input/2-output transaction: <https://usercontent.irccloud-cdn.com/file/airMJ4pC/timing-1-2.png>  
<strong>\<sarang\></strong> Verification timing for 2-input/2-output transaction: <https://usercontent.irccloud-cdn.com/file/iZdBR8xe/timing-2-2.png>  
<strong>\<sarang\></strong> Related to this, I've been working on the Arcturus transaction security model, which uses an Omniring-style balance game/definition and applies it to the combination of Arcturus proofs and Bulletproof range proofs  
<strong>\<sarang\></strong> I'll post that update when I've finished typesetting it and reorganizing the preprint on IACR  
<strong>\<sarang\></strong> (but it's still in progress\!)  
<strong>\<sarang\></strong> Any questions for me on this material?  
<strong>\<hyc\></strong> Arcturus seems to blow away the other sig mechs  
<strong>\<fort3hlulz\></strong> What's the main drawback(s) of Arcturus compared to other sig mechs?  
<strong>\<fort3hlulz\></strong> Seems like a clear win, but maybe there is something I'm missing.  
<strong>\<sarang\></strong> The RCT3 update beats it for overall size (when looking at the whole chain), but that does very poorly in verification due to input padding  
<strong>\<sarang\></strong> Arcturus relies on a nonstandard cryptographic hardness assumption  
<strong>\<hyc\></strong> what are the implications of being nonstandard? needs further proofs?  
<strong>\<sarang\></strong> You can see the full-chain comparative estimates on page 12 of the Arcturus IACR preprint: <https://eprint.iacr.org/2020/312.pdf>  
<strong>\<sarang\></strong> note that in Figure 3, RCT3 wins, but in Figure 4, it loses  
<strong>\<sarang\></strong> (size vs time)  
<strong>\<sarang\></strong> It would need external study to see if it can either be reduced to more standard assumption, broken, or considered/tested enough to be considered reasonable  
<strong>\<sarang\></strong> Triptych does not have this limitation, and relies on only standard assumptions  
<strong>\<sarang\></strong> I'm submitting it to conference proceedings in the hope that it will get some quality review  
<strong>\<sarang\></strong> so I want to update the security model prior to that deadline at the end of this month  
<strong>\<hyc\></strong> the win on time is huge  
<strong>\<sarang\></strong> FWIW both Triptych and Arcturus are very similar for verification time  
<strong>\<sarang\></strong> that's because of how generators are batched similarly in both approaches  
<strong>\<hyc\></strong> triptych appears to be a constant factor larger in size  
<strong>\<hyc\></strong> well, nearly.  
<strong>\<sarang\></strong> It requires multiple proofs, and has some extra elements included (e.g. commitment offsets)  
<strong>\<sarang\></strong> Arcturus is a single proof, and does not require any commitment offsets  
<strong>\<sarang\></strong> (it does have proof elements that scale with the number of spends, but does so pretty darn well)  
<strong>\<hyc\></strong> at least all of the size plots are linear, no silly exponential growth  
<strong>\<hyc\></strong> probably an obvious statement but I would choose to optimize time  
<strong>\<sarang\></strong> In that case, Triptych and Arcturus are essentially comparable  
<strong>\<sarang\></strong> with small variations relating to how balances are checked  
<strong>\<sarang\></strong> and these variations disappear at higher ring sizes anyway  
<strong>\<hyc\></strong> and Triptych requires no nonstandard assumptions  
<strong>\<sarang\></strong> Nope  
\< ah thanks, I was wondering about this  
<strong>\<sarang\></strong> I could probably add the Arcturus-style balance security definition to Triptych as well  
<strong>\<sarang\></strong> Isthmus: balance checks in MLSAG/CLSAG/Triptych are identical... sum the commitment offsets and outputs to zero  
<strong>\<sarang\></strong> In Arcturus it's built in to the proving system directly  
<strong>\<sarang\></strong> At high ring sizes, the offset-based balance check is overshadowed by the large number of group operations required for the rest of the verification process  
<strong>\<hyc\></strong> this is some great stuff. Arcturus still grows in size more slowly than Triptych,  
<strong>\<sarang\></strong> At low ring sizes, they're more comparable and the difference is notable  
<strong>\<sarang\></strong> Yeah  
<strong>\<sarang\></strong> Its per-spend elements scale better  
<strong>\<sarang\></strong> What's nifty is they both use the same underlying Groth-style cryptographic plumbing, but in different ways  
<strong>\<sarang\></strong> (this is the same plumbing that Lelantus uses)  
<strong>\<sarang\></strong> Anyway, I've taken up enough of the roundtable time for one day\!  
<strong>\<sarang\></strong> Does anyone else have research they wish to share?  
<strong>\<Isthmus\></strong> TheCharlatan updated the encrypted unlock time research proposal with sarang's timing data: <https://github.com/insight-decentralized-consensus-lab/monero\_encrypted\_unlock\_time>  
<strong>\<sarang\></strong> s/Tryptich/Triptych/  
<strong>\<Isthmus\></strong> (based on feedback at previous MRL meeting, and input from sarang)  
<strong>\<Isthmus\></strong> Also, experimenting with a new application for surae's seashell avatars project. Essentially, each transaction fingerprint (behavior or metadata) is compared against the behavior of the core software and assigned a 0 if matching or 1 if deviating.  
<strong>\<Isthmus\></strong> Looping over fingerprints creates a fingerprint string that is ingested to produce a visual hash. These could be added to a research blockchain explorer so that it's easier to tell at a glance which transactions must have been generated by custom software.  
<strong>\<sarang\></strong> I'm glad the 3-CLSAG and 3-Triptych data was useful\!  
<strong>\<Isthmus\></strong> For example, the first image shows the avatar for transactions that are from (or mimic) the core GUI/CLI, which has fingerprint ...0000  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/vjCauM0y/image.png>  
<strong>\<Isthmus\></strong> The secnd image shows the avatar for transactions that included a juvenile ring member and thus produce a different signature (...0010)  
<strong>\<Isthmus\></strong> the bottom image shows the avatar for transactions that included a juvenile ring member and thus produce a different signature (...0010)  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/Lzt9vfyJ/image.png>  
<strong>\<Isthmus\></strong> (note that this particular issue was fixed in recent update)  
<strong>\<Isthmus\></strong> Anyways, still very early toy/prototype  
<strong>\<sarang\></strong> So the hash inputs are individually set bits? 1 = "basically the same as standard", 0 = "different enough"  
<strong>\<sarang\></strong> and this is done over different characteristics to build the input string?  
<strong>\<Isthmus\></strong> Yep  
<strong>\<Isthmus\></strong> 0 = "the core wallet would construct a transaction in this way"  
<strong>\<Isthmus\></strong> 1 = "the core wallet would never construct a transaction this way"  
<strong>\<Isthmus\></strong> e.g. the juvenile spend example  
<strong>\<sarang\></strong> got it  
<strong>\<Isthmus\></strong> Will spice it up a bit though, surae comments "The skin of the shells could be fractals dependent on the hash input visualized in 2d with \*color schemes\* selected from families of pleasing color triples based on hash input..."  
<strong>\<UkoeHB\_\></strong> What's a juvenile ring member,  
<strong>\<UkoeHB\_\></strong> ?  
<strong>\<Isthmus\></strong> Any transaction that includes a ring that includes a ring member less than 10 blocks old (based on the time it was mined)  
<strong>\<Isthmus\></strong> <https://github.com/monero-project/monero/issues/5712>  
<strong>\<UkoeHB\_\></strong> ah  
<strong>\<Isthmus\></strong> The core wallet has observed a 10-block lock time, so they must have been generated by custom software  
<strong>\<Isthmus\></strong> But now it's a consensus rule  
<strong>\<sarang\></strong> To what extent does the visual fingerprint identify the extent to which the transaction is nonstandard?  
<strong>\<sarang\></strong> e.g. can you look at a fingerprint and see "oof, this transaction is \_very\_ nonstandard\!"  
<strong>\<sarang\></strong> (obviously the Hamming weight of the input will tell you this by inspection)  
<strong>\<Isthmus\></strong> No, since the visual hash function is appropriately unstable  
<strong>\<UkoeHB\_\></strong> You could look at the fingerprint string itself to see how different, since more 1s = more different  
<strong>\<sarang\></strong> That's what I mean by the Hamming weight  
<strong>\<Isthmus\></strong> aaaactually if the hamming weigh was used to select the colorscale......  
<strong>\<Isthmus\></strong> Then it could be intuitively accomplished  
<strong>\<Isthmus\></strong> if colorscale(0) is greenish  
<strong>\<sarang\></strong> At that point, what's the usefulness of the fingerprint shape?  
<strong>\<sgp\_\></strong> going all the way back to the unlock time proposal, I still think the tradeoffs aren't worth it  
<strong>\<Isthmus\></strong> Because 0010 and 0001 are different  
<strong>\<sarang\></strong> True  
<strong>\<sarang\></strong> So it really only tells you if the actual strings are different  
<strong>\<sarang\></strong> I guess I figured the "more useful" component in general might be the Hamming weight  
<strong>\<sarang\></strong> since one goal is to minimize it  
<strong>\<Isthmus\></strong> It depends if 'degree of wrongness' is important  
<strong>\<UkoeHB\_\></strong> I agree sgp\_ it feels quite expensive  
<strong>\<Isthmus\></strong> From my perspective, 0010, 0001, and 0011 are 3 distinct signatures  
<strong>\<Isthmus\></strong> Even though 0011 is more worse :- P  
<strong>\<UkoeHB\_\></strong> ArticMine: how is it going with your penalty/fee proposal?  
<strong>\<sarang\></strong> While we wait to see if ArticMine is around, were there any other questions on the material Isthmus presented?  
<strong>\<sgp\_\></strong> none about the presented material, but I eventually have a question for Isthmus about the coinbase vs non-coinbase spend distributions  
<strong>\<Isthmus\></strong> Hey @sgp\_ what do you have in mind? :- )  
<strong>\<sarang\></strong> I would also be interested to see that for BTC  
<strong>\<sgp\_\></strong> heelo Isthmus :)  
<strong>\<sgp\_\></strong> s/heelo/hello  
<strong>\<monerobux\></strong> sgp\_ meant to say: hello Isthmus :)  
<strong>\<sgp\_\></strong> I really want to segregate coinbase outputs form other outputs  
<strong>\<sgp\_\></strong> to do this, I ideally would like to know what the independent spend distributions are for these two categories of outputs  
<strong>\<sgp\_\></strong> my suspicion is that coinbase outputs are spent faster on average  
<strong>\<Isthmus\></strong> We can ascertain this by subtracting the reference distribution from the observed ensemble distribution  
<strong>\<Isthmus\></strong> And split it by type:  
<strong>\<Isthmus\></strong> distribution(coinbase inclusion in rings) - reference\_distribution  
<strong>\<Isthmus\></strong> distribution(non-coinbase inclusion in rings) - reference\_distribution  
<strong>\<Isthmus\></strong> I think @binaryFate was going to present this type of analysis at Konferenco, though I don't know if was split up by output type (non/coinbaase)  
<strong>\<sarang\></strong> Having a direct measurement from something like BTC would be very helpful regardless  
<strong>\<sarang\></strong> ideally to follow the Miller et al. idea of comparing known-estimated Monero behavior to BTC  
<strong>\<Isthmus\></strong> I'll see about extracting true BTC spend times from Google's BigQuery dataset  
<strong>\<sarang\></strong> That'd be great  
<strong>\<Isthmus\></strong> There's probably some way to do it in a clever SQL one-liner  
<strong>\<Isthmus\></strong> But I can do it in 20 lines\!  
<strong>\<Isthmus\></strong> :- P  
<strong>\<sarang\></strong> Separately, it would also be interesting to see how/if overall BTC spend times have changed since Miller et al.'s paper  
<strong>\<sarang\></strong> They used two different large groups of blocks  
<strong>\<sgp\_\></strong> we need to have some selection for the coinbase-only rings in any case, though if the results show that the distributions are different, then that's even more reason to segregate  
\< this  
<strong>\<sgp\_\></strong> note I still support coinbase-only rings even if the distributions are exactly the same :p  
<strong>\<sarang\></strong> In the interest of time, were there any other topics to be brought up before moving on?  
<strong>\<sgp\_\></strong> that's all fro me, thanks Isthmus  
<strong>\<sgp\_\></strong> \*from  
<strong>\<UkoeHB\_\></strong> Any new comments on the Tx Supplement proposal?  
<strong>\<sarang\></strong> Restructuring for uniformity and Janus mitigation seems useful and reasonable to me, FWIW  
<strong>\<sgp\_\></strong> agreed  
<strong>\<sgp\_\></strong> costs are small  
<strong>\<sarang\></strong> Especially with the savings from CLSAG  
<strong>\<Isthmus\></strong> I'm in favor. Uniformity is the whole point.  
<strong>\<ArticMine\></strong> UkoeHB\_ It is almost done. I held it back to give ti ore thought especially with COVID-19 which is a perfect scenario for the issue  
<strong>\<ArticMine\></strong> I should have this in the next two weeks  
<strong>\<UkoeHB\_\></strong> Cool thanks :)  
<strong>\<sarang\></strong> OK, with the last few minutes of the hour, let's get to ACTION ITEMS  
<strong>\<sarang\></strong> I would like to finish the update of the Arcturus security model, to get the updated preprint submitted for review  
<strong>\<sarang\></strong> And will be discussing the CLSAG audit with Teserakt  
<strong>\<sarang\></strong> Anyone else?  
<strong>\<UkoeHB\_\></strong> In the tx supplement proposal I recommend moving to sorted TLV in the extra field. However, it's not completely solved. One option is to retain 'restricted tags' for core features (e.g. encrypted payment IDs, miner nonce). Are restricted tags worthwhile or too hands-on?  
<strong>\<sarang\></strong> Well, certain tags would be required by consensus... can you refresh us on your definitions here?  
<strong>\<UkoeHB\_\></strong> Moving to restricted tags might force more uniformity out of pool implementations, since there would be a fixed miner nonce size. However, they could just move their unique nonces to unrestricted tags.  
<strong>\<UkoeHB\_\></strong> Only encrypted payment IDs would remain in the extra field after the update  
<strong>\<UkoeHB\_\></strong> And miner extra nonce  
<strong>\<UkoeHB\_\></strong> So not much consensus left  
<strong>\<sarang\></strong> Oh, TLV for \_extra only\_... of course  
<strong>\<sarang\></strong> nvm  
<strong>\<sarang\></strong> I was thinking about fields in general, which is not correct  
<strong>\<UkoeHB\_\></strong> With a restricted miner nonce we (probably I) could release a miner nonce guideline for pool implementer to reference  
<strong>\<UkoeHB\_\></strong> If it's easy enough then hopefully most pools and solominers would be indistinguishable on-chain  
<strong>\<sarang\></strong> OK, any other questions, topics, or action items before we adjourn?  
<strong>\<h4sh3d\[m\]\></strong> I posted a proposal for the atomic swap, feedback are welcome  
<strong>\<sarang\></strong> Link?  
<strong>\<h4sh3d\[m\]\></strong> <https://repo.getmonero.org/monero-project/ccs-proposals/-/merge\_requests/145>  
<strong>\<sarang\></strong> thanks  
<strong>\<sarang\></strong> All right, let's adjourn in the interest of time (and for log posting purposes). Thanks to everyone for attending\!
