---
title: Logs for the Monero Research Lab Meeting Held on 2019-09-02
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Agenda: <https://github.com/monero-project/meta/issues/388>  
<strong>\<sarang\></strong> (logs posted there afterward)  
<strong>\<suraeNoether\></strong> good morning everyone  
<strong>\<sarang\></strong> GREETINGS  
<strong>\<rottensox\></strong> Hola.  
<strong>\<sarang\></strong> Happy Labor Day to those celebrating it  
<strong>\<sarang\></strong> Happy Monday to all others  
<strong>\<sarang\></strong> Let's do our ROUNDTABLE  
<strong>\<sarang\></strong> suraeNoether: care to go first?  
<strong>\<suraeNoether\></strong> sure. This past week i've been coding my economarkov chain simulating a fake Monero economy to apply matching to. this is slow-going, but steady progress. in addition to that, I started reading 3 separate papers for a new-ish idea...  
<strong>\<suraeNoether\></strong> <https://eprint.iacr.org/2016/583.pdf> , <https://www.microsoft.com/en-us/research/wp-content/uploads/2008/02/tcc2008.pdf> , and <https://link.springer.com/chapter/10.1007/3-540-36413-7\_20>  
<strong>\<suraeNoether\></strong> the idea is new-ish to me but not the e-cash community, which is to demonstrate not a valid signature on a public message m, but \*knowledge of\* a valid signature on a public message m, without revealing the signature information like signer  
<strong>\<suraeNoether\></strong> that 583 paper presents a trustless way of doing so with hash functions that can be described with a boolean circuit, and presents zk proofs of knowledge of RSA, DSA, and ECDSA signatures  
<strong>\<suraeNoether\></strong> the idea is to replace ring signatures with something that is trustless and signer ambiguous  
<strong>\<sarang\></strong> Interesting  
<strong>\<suraeNoether\></strong> that way, instead of saying "Either A, B, or C signed this m with key image J," the statement being proven is "I have seen a valid signature on m with key image J"  
<strong>\<sarang\></strong> Requires efficient trustless accumulator?  
<strong>\<suraeNoether\></strong> coupling this together with a zk proof of membership in a strong dynamic accumulator allows for a "signature" scheme that does away with the explicit anonymity sets of ring signatures  
<strong>\<suraeNoether\></strong> i think i'm onto a method for doing this with key images that are compatible with our current approaches  
<strong>\<sarang\></strong> Nice\!  
<strong>\<suraeNoether\></strong> but I need, probably, 2-3 additional pairs of eyes helping me out, so I'll be writing some stuff up and possibly starting a github issue for discussion on the matter  
<strong>\<sarang\></strong> roger  
<strong>\<suraeNoether\></strong> other than that, i've been offline with family for a reunion + a 100-years-olds birthday party :D  
<strong>\<sarang\></strong> My monthly report details my recent activities, and is available now: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/77#note\_7105>  
<strong>\<sarang\></strong> Matching simulation review, updating papers, etc.  
<strong>\<sarang\></strong> Nothing earth-shattering over the past few days  
<strong>\<sarang\></strong> Very neat to hear about kenshamir\[m\]'s work on IACR/944  
<strong>\<suraeNoether\></strong> yes, i would like to hear more about that  
<strong>\<sarang\></strong> Is kenshamir\[m\] still here?  
<strong>\<kenshamir\[m\]\></strong> Hi  
<strong>\<kenshamir\[m\]\></strong> I’m here  
<strong>\<sarang\></strong> Anything specific you'd be interested to share about your recent work on proving systems?  
<strong>\<sarang\></strong> (no obligation to do so)  
<strong>\<kenshamir\[m\]\></strong> I think the most notable contribution from 944 that can be applied to bulletproofs straight away is the improved inner product argument  
<strong>\<kenshamir\[m\]\></strong> There are benchmarks which show that it gives significant improvements in verifier and prover efficiency  
<strong>\<mikerah\></strong> Is there no meeting today?  
<strong>\<sarang\></strong> In the general circuit case, correct?  
<strong>\<sarang\></strong> (the meeting is happening now)  
<strong>\<sarang\></strong> Not the optimized range proof application AFAICT  
<strong>\<kenshamir\[m\]\></strong> Yeah for 944s proving system it was the general case  
<strong>\<kenshamir\[m\]\></strong> I think if that if we tailored the proof to be specific for 944s proving system, we may be able to get a more efficient rangeproof. This is only a conjecture though and I’m unsure of how to do it at the moment  
<strong>\<sarang\></strong> The general case remains extremely interesting  
<strong>\<sarang\></strong> since the range proofs are quite efficient  
<strong>\<kenshamir\[m\]\></strong> For the general case asymptotically it is the same as the tailored bulletproofs rangeproofs from what I’ve seen  
<strong>\<kenshamir\[m\]\></strong> Yeah I agree. It will be really interesting to see what optimisations can be made with this language  
<strong>\<kenshamir\[m\]\></strong> \*Quadratic Equation Sat  
<strong>\<kenshamir\[m\]\></strong> That’s all I’ve discovered so far from 944  
<strong>\<sarang\></strong> Thanks kenshamir\[m\]  
<strong>\<sarang\></strong> Does anyone else have interesting work to share?  
<strong>\<sarang\></strong> Or, for that matter, general questions  
<strong>\<sarang\></strong> Righto\!  
<strong>\<sarang\></strong> We can also move to ACTION ITEMS, if there's nothing else urgent to discuss  
<strong>\<suraeNoether\></strong> my action items are short and simple. economarkov chain work, reading more on proofs of knowledge of valid signatures (which i'm considering calling redacted signatures), and my end of month work report.  
<strong>\<sarang\></strong> I will be doing some code review, continued work on proving systems, and ongoing work with suraeNoether on his recent updates to graph matching as needed  
<strong>\<sarang\></strong> Well, a short meeting today, but that's ok  
<strong>\<sarang\></strong> Anything final before we formally adjourn?  
<strong>\<sarang\></strong> Adjourned\! Thanks to everyone for participating
