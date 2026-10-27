---
title: Logs for the MRL Meeting Held on 2019-10-28
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<sgp\_\></strong> hello\!  
<strong>\<sarang\></strong> I’ll give a few moments for others who wish to join  
<strong>\<sarang\></strong> OK then  
<strong>\<sarang\></strong> Since suraeNoether is unavailable for this meeting due to an appointment, I’ll share my recent work  
<strong>\<sarang\></strong> I’ve been working on algorithms and proofs for Triptych, a new transaction protocol  
<strong>\<sarang\></strong> The goal is to use a single proof to represent multiple inputs at the same time, including balance proving and linking tags  
<strong>\<sarang\></strong> Everything works great with completeness, zero knowledge, and soundness except for one proof component (the linking tags)  
<strong>\<sarang\></strong> There’s a less efficient version that operates on single inputs, but can be combined for general transactions  
<strong>\<sarang\></strong> For this single-input version, modified proofs of security seem to work just fine  
<strong>\<sarang\></strong> For this reason, I’ll finalize work on the single-input proving system while considering alternate approaches to finalizing the soundness proof for the multi-input version  
<strong>\<sarang\></strong> Separately from this, I have a small pull request (PR 6049) for a minor speedup and simplification to the Bulletproofs prover  
<strong>\<sarang\></strong> Also separately from this, Derek at OSTIF informs me that an audit group is willing to complete the CLSAG review  
<strong>\<sarang\></strong> JP Aumasson has offered to complete a review of the math and proofs for $7200 (USD), and his new company Teserakt has offered to then complete a code review for as little as $4800  
<strong>\<sarang\></strong> He says that including dependencies would increase the time (and therefore the cost), possibly significantly  
<strong>\<sarang\></strong> But the timeline could be before the end of this year, if there are no changes required to the algorithms after the math review  
<strong>\<moneromooo\></strong> Dependencies, like the src/crypto code ?  
<strong>\<sarang\></strong> Presumably. I do not have specific details on what his scope is (but will get this information)  
<strong>\<sarang\></strong> One approach might be to review all the changes \_from MLSAG\_, to show that CLSAG is no less secure as a whole than MLSAG  
<strong>\<sarang\></strong> These changes are fairly minor in the grand scope of the codebase  
<strong>\<sarang\></strong> I see there being efficiency advantages to having JP (and colleagues) doing both types of review, but this also reduces the total number of eyes on the combined math+code  
<strong>\<sarang\></strong> That being said, JP knows his stuff  
<strong>\<sarang\></strong> (he was formerly with Kudelski)  
<strong>\<moneromooo\></strong> Adding eyes by having Alice do the math and Bob do the code does not provide anything of value over Alice doing both IMHO.  
<strong>\<moneromooo\></strong> Assuming Alice and Bob have similar eyes and brains and proficiency in the relevant fields etc etc etc.  
<strong>\<sarang\></strong> So that’s my report  
<strong>\<moneromooo\></strong> Is any of the new protocols being considered still compatible with multisig ?  
<strong>\<sarang\></strong> Aside from CLSAG, you mean?  
<strong>\<sarang\></strong> None of them specifically consider it in either algorithms or security model  
<strong>\<sarang\></strong> but it’s on my list for analysis on RCT3 and (eventually) Triptych, since there are some modifications to RCT3 that I wish to consider (more on this later)  
<strong>\<moneromooo\></strong> I mean tryptich, rct3 and… and… the other the name of which escapes me.  
<strong>\<moneromooo\></strong> lelantus  
<strong>\<sarang\></strong> Omniring?  
<strong>\<moneromooo\></strong> Also :)  
<strong>\<sarang\></strong> Omniring and Lelantus both suffer from some drawbacks at present… Omniring does not support batching, and Lelantus still has a tracing issue unless you remove stealth addressing  
<strong>\<sarang\></strong> Looking into batch-compatible Omniring-style constructions with other proving systems is a topic for more investigation down the road that is nontrivial  
<strong>\<sarang\></strong> Is there other research that anyone wishes to present, or other questions?  
<strong>\<moneromooo\></strong> Also, rather selfishly, would any of them avoid the public-a issue we had for multi user txes ?  
<strong>\<moneromooo\></strong> (if known offhand)  
<strong>\<sarang\></strong> public-a?  
<strong>\<moneromooo\></strong> The problem where users would have to make their a values known to other signers.  
<strong>\<sarang\></strong> Ah, that’s very unclear to me  
<strong>\<sarang\></strong> FWIW: RCT3, Omniring, and Triptych are agnostic to how output keys are generated (though their security models address particular constructions)  
<strong>\<sarang\></strong> So my ACTION ITEMS for this week are a bit in flux, mainly because I’ll be at World Crypto Conference giving a talk on transaction protocols  
<strong>\<sarang\></strong> But aside from that, I want to finish the proof modifications (completeness, SHVZK, special soundness) for the single-input version of Triptych (which can be used in a larger protocol to support multi-input transactions), as well as a more efficient linking tag construction that matches what RCT3 and Omniring propose  
<strong>\<sarang\></strong> I also want to backport some of the ideas from the latest RCT3 update to their older version to compare efficiency  
<strong>\<sarang\></strong> It’s unclear if this could easily be proven secure, or what the efficiency gains would be  
<strong>\<sarang\></strong> Their update did essentially two things: fix an exploitable flaw due to a particular discrete log relation, and allow for aggregated proofs of multiple inputs  
<strong>\<sarang\></strong> Unfortunately, the latter means potentially large padding requirements that would also incur computational cost to the verifier  
<strong>\<sarang\></strong> I want to see how easily the exploit fix could be included in the non-aggregated version… which would avoid this potential verification bloat at the cost of proof size  
<strong>\<sarang\></strong> I probably won’t have time to do so this week, but it’s on my list  
<strong>\<sarang\></strong> Anything else of note to cover before we formally adjourn?  
<strong>\<sarang\></strong> All right\! Thanks to everyone for attending  
<strong>\<sarang\></strong> Logs will be posted shortly to the GitHub agenda issue
