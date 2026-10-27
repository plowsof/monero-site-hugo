---
title: Logs for the Monero Research Lab Meeting Held on 2019-03-04
summary: Sarang work, Surae work, SamsungGalaxyPlayer proposal and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Shall we begin?  
<strong>\<sarang\></strong> 1. GREETINGS  
<strong>\<sarang\></strong> Hello everyone  
<strong>\<oneiric\_\></strong> hullo  
<strong>\<sarang\></strong> Let's go over our usual 2. ROUNDTABLE  
<strong>\<sarang\></strong> In the spirit of fairness and generosity, I will go first :D  
<strong>\<sarang\></strong> I posted my February monthly report (see agenda for link); comments welcome  
<strong>\<sarang\></strong> Besides the things listed there, I have initial working code for a Bulletproofs MPC (link in agenda also)  
<strong>\<sarang\></strong> moneromooo has been toying around with the idea of a coinjoin-type scheme, for which this MPC would be efficient and useful  
<strong>\<sarang\></strong> It still needs a lot of additional testing and work, but the initial code is operational  
<strong>\<sarang\></strong> And along with suraeNoether, still making edits and fixes to an upcoming paper in collaboration with other researchers for submission  
<strong>\<sarang\></strong> This week I'll be doing some MPC code cleanup and adversarial unit tests  
<strong>\<sarang\></strong> Any questions for me on these topics?  
<strong>\<suraeNoether\></strong> i have one  
<strong>\<oneiric\_\></strong> link for repo?  
<strong>\<sarang\></strong> Link at the agenda: <https://github.com/monero-project/meta/issues/309>  
<strong>\<oneiric\_\></strong> thanks :)  
<strong>\<sarang\></strong> the code is in super early stages  
<strong>\<suraeNoether\></strong> the bulletproof coinjoin-style mpc: is this described in any level of detail anywhere outside of the bulletproofs paper? i think i get how bulletproofed MPC works, but if they are intended for use in a coinjoin-style way with Monero, i would like to see an explanation of how  
<strong>\<sarang\></strong> Ah good point. The BP paper only described the MPC protocol, and hinted at applications  
<strong>\<sarang\></strong> moneromooo has been working on the Monero-specific coinjoin at his "multi" branch  
<strong>\<suraeNoether\></strong> has coinjoin ringct been described outside of code?  
<strong>\<sarang\></strong> Not that I know of. It's on my list :D  
<strong>\<suraeNoether\></strong> got it  
<strong>\<sarang\></strong> FWIW having the bulletproofs code refactored to allow for MPC is a good idea anyway  
<strong>\<suraeNoether\></strong> agreed  
<strong>\<sarang\></strong> It turns the usual multi-output proof into a trivial MPC with one player  
<strong>\<sarang\></strong> and of course the verifier is completely unchanged  
<strong>\<suraeNoether\></strong> i'm not trying to imply that the MPC work is not important or unrelated to monero; it is both important and related. i just wanted to see what had been written.  
<strong>\<suraeNoether\></strong> my update is simple, too.  
<strong>\<suraeNoether\></strong> I'm working on my February report right now. i am working on my funding request for next quarter. sarang and i are both working into our proposals one big change from previous proposals: primarily a pay-up-front clause to prevent MRL researchers from having their paychecks degrade over the funding period.  
<strong>\<sarang\></strong> Ooh good point on the new funding model  
<strong>\<sarang\></strong> We discussed this publicly a lot  
<strong>\<suraeNoether\></strong> in addition to that, i've passed the proofs-stuff back to our co-authors, who i'm chatting with almost daily on the publication; our deadlines have been pushed back twice now, so i asked for permission to explain what we are working on, and I got a "little bit" of consent, so  
<strong>\<suraeNoether\></strong> basically, sarang and i have been working with two authors on formalizing the DLSAG stuff, and i've been working on security proofs while sarang has been working on getting timing results for comparing to vanilla monero ringct  
<strong>\<sarang\></strong> Yeah, the paper has specific constructions for payment channels et al.  
<strong>\<suraeNoether\></strong> (one of the reasons i wanted a written description of bulletproof coinjoin is to see how well it will mesh with the new scheme  
<strong>\<sarang\></strong> Oh interesting. I hadn't thought of that part  
<strong>\<suraeNoether\></strong> yeah, long story short: the primitives required in monero for a lightning network  
<strong>\<sarang\></strong> The bulletproofs MPC protocol is independent of how the coinjoin signatures are done, FWIW  
<strong>\<suraeNoether\></strong> sarang: right, the bulletproofs mpc is merely to securely compute a range proof collaboratively, right, wihtout revealing your hidden values to your cosigners  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> But I get your point  
<strong>\<suraeNoether\></strong> in addition to that, my plate this week consists of 1) reading about flyclient and making a proposal (if any, even if it is to ignore flyclient), 2) matching simulations are finally moving a little bit after some late night saturday work, and 3) my feb report + next quarter funding request  
<strong>\<suraeNoether\></strong> that finishes up my brief roundtable update  
<strong>\<suraeNoether\></strong> i would love to hear from anyone else who has done any research this past week. isthmus is always on fire with productivity (poor guy has 3rd degree burns)  
<strong>\<suraeNoether\></strong> oh i'm looking at the agenda here and we have sgp\_  
<strong>\<suraeNoether\></strong> i believe sgp suggested a different input selection algorithm for pools: <https://github.com/monero-project/monero/issues/5222>  
<strong>\<sgp\_\></strong> yes, thanks suraeNoether for the link to the Github discussion  
<strong>\<sgp\_\></strong> this discussion is only around the public POOL selection algorithm, not the selection algorithm for other users  
<strong>\<sgp\_\></strong> I expect this to be non-controversial and to have no negative impact on any party, but if you feel otherwise, I'd love your comment in the issue  
<strong>\<sgp\_\></strong> Unless there are any questions, we can keep going  
<strong>\<suraeNoether\></strong> some of the thoughts presented in your github discussion reflect some of the thoughts that isthmus has had on the matter with multi-input transactions, so I actually think this discussion is a little more broad than you suspect  
<strong>\<suraeNoether\></strong> but also: since input selection isn't consensus, any pool could \*decide\* to do this  
<strong>\<sgp\_\></strong> it could be. this concept as I presented it has been thrown around since early 2018  
<strong>\<moneromooo\></strong> I'd like to have a confirmation that it does not harm anything else before I code it up.  
<strong>\<moneromooo\></strong> (from sarang and/or surae)  
<strong>\<suraeNoether\></strong> the problem as I see it is that it reduces things in the following way  
<strong>\<sarang\></strong> I have looked over it briefly this morning but want to think about it in more detail  
<strong>\<suraeNoether\></strong> if we have a ring size N\*M, and the average number of outputs per transaction is M, and ring members are selected by transaction instead of by input, there is a strong argument that this reduces the effective ring size to N.  
<strong>\<suraeNoether\></strong> the true ring size is N\*M, but there are only N transactions included as ring memb ers  
<strong>\<sarang\></strong> Right, it's a version of binning  
<strong>\<sarang\></strong> and if you can eliminate a bin provably or heuristically, it's a problem  
<strong>\<sgp\_\></strong> I argue the typical drawbacks of binning do not apply here, since the public pools make all of the transaction details public anyway  
<strong>\<sgp\_\></strong> Ring signatures could provide 0 protection and the pools wouldn't be worse off  
<strong>\<suraeNoether\></strong> uhm well  
<strong>\<suraeNoether\></strong> the concern isn't these public pool's privacy  
<strong>\<suraeNoether\></strong> it's their behavior negatively impacting the privacy of other participatns in the monero ecosystem  
<strong>\<sgp\_\></strong> The goal isn't to restore the effective ringsize of the pool rings. It's to preserve the integrity of the pool outputs used in other rings  
<strong>\<sarang\></strong> right  
<strong>\<suraeNoether\></strong> sgp\_: here's my problem, as i see it  
<strong>\<suraeNoether\></strong> another problem anyway  
<strong>\<suraeNoether\></strong> let's say i am a pool and i have 3 xmr and i want to send 1xmr each to: (1) miner alice and (2) miner bob and (3) myself as change  
<strong>\<suraeNoether\></strong> er... 3 outputs  
<strong>\<suraeNoether\></strong> assume each output is 1xmr  
<strong>\<sgp\_\></strong> got it :)  
<strong>\<suraeNoether\></strong> under your proposal, i construct 3 separate ring signatues, all of which contain all 3 of these outputs  
<strong>\<suraeNoether\></strong> moreover, i'm a public pool  
<strong>\<suraeNoether\></strong> anyone will be able to see that all 3 outputs have been spent  
<strong>\<sgp\_\></strong> wait a sec  
<strong>\<suraeNoether\></strong> i have outputs A, B, and C. I want to send A to alice, B to bob, and C to charlie. they all came from the same transaction, so i have to include A, B and C in my rings  
<strong>\<suraeNoether\></strong> if i want to send all 3, this guarantees anyone can see they have been spent  
<strong>\<sgp\_\></strong> this input selection algorithm proposal is meant to handle the change outputs, not the source (eg: coinbase). Those require another more aggressive change  
<strong>\<sgp\_\></strong> I'm slightly confused by how you are handling these outputs  
<strong>\<sgp\_\></strong> If you have 3 XMR in output A, you create a transaction to Alice, Bob, yourself with outputs B, C, D  
<strong>\<sgp\_\></strong> Then you create your next transaction with ring {B, C, D}  
<strong>\<sgp\_\></strong> to make unclear which of B,C,D is the change output  
<strong>\<suraeNoether\></strong> no, that's not what i mean, i misspoke, let me try again really quick  
<strong>\<sgp\_\></strong> under this current proposal, A is known to be spent still. it doesn't fix that problem  
<strong>\<suraeNoether\></strong> ughhhh you know what i need to think about this more, because the pool won't have 3 outputs from a single transaction. it's a pool, so it'll have a bunch of single outputs, each from individual transactions  
<strong>\<suraeNoether\></strong> so my example falls apart  
<strong>\<suraeNoether\></strong> but i think we should think about it a bit more  
<strong>\<suraeNoether\></strong> oh but i suppose it could have a bunch of change transactions  
<strong>\<suraeNoether\></strong> okay, i can manufature a problematic exmaple, but let's do it after the meeting  
<strong>\<sarang\></strong> roger  
<strong>\<sarang\></strong> Does anyone else have research of interest to share?  
<strong>\<sgp\_\></strong> sure, and I'm not saying this is a perfect solution that defends against all heuristics, but it's an incremental improvement over the status quo in every case I've found so far. doesn't mean there aren't more. move on :)  
<strong>\<sarang\></strong> We can also merge this with 3. QUESTIONS from anyone on any research-related topic  
<strong>\<oneiric\_\></strong> some questions on kdf interaction, but maybe off-topic  
<strong>\<sarang\></strong> Fire away; we have time  
<strong>\<oneiric\_\></strong> so, i2p is considering reddsa from zcash as an offline signing algo  
<strong>\<oneiric\_\></strong> reddsa has a unique way of generating blinding material 'alpha' to generate new blinded pravte key  
<strong>\<oneiric\_\></strong> other than that, identical to eddsa  
<strong>\<sarang\></strong> OK, I wasn't familiar with this construction  
<strong>\<oneiric\_\></strong> looking for a link to alpha generation, one moment  
<strong>\<oneiric\_\></strong> <https://geti2p.net/spec/proposals/123-new-netdb-entries#blinding-calculations>  
<strong>\<oneiric\_\></strong> and the proposed red25519: <https://geti2p.net/spec/proposals/146-red25519>  
<strong>\<suraeNoether\></strong> okay  
<strong>\<oneiric\_\></strong> is there anything obviously dangerous, or gotchas that you can see?  
<strong>\<sarang\></strong> So the difference is the deterministic derivation of the private key offset alpha  
<strong>\<oneiric\_\></strong> sarang yeah that's how i understand it  
<strong>\<sarang\></strong> Well if an adversary is able to gain any advantage in determining the hash inputs used to derive alpha, not good  
<strong>\<oneiric\_\></strong> they have control over the destination, but its hashed  
<strong>\<suraeNoether\></strong> oneiric\_: seems like the strength of it relies up on the "secret" input  
<strong>\<suraeNoether\></strong> someone who uses an empty secret (or just "0" or a badly selected password or something), then someone could brute force lots of destinations and datetimes and keep them all in a big table and look them up when needed  
<strong>\<oneiric\_\></strong> oh, yeah that's bad. totally undermines the point of the scheme  
<strong>\<suraeNoether\></strong> the next question down is whether they should switch to SHA256 and the answer is "no" because afaik hkdf is basically hmac used as a kdf, and that's what i've been advocating for about a year  
<strong>\<suraeNoether\></strong> wow "afaik hkdf hmac kdf"  
<strong>\<oneiric\_\></strong> what would you suggest as an alternative for alpha generation, or are there checks one could do to prevent bad selection?  
<strong>\<oneiric\_\></strong> blake2b sane alternative, yeah?  
<strong>\<suraeNoether\></strong> oneiric\_ i don't think there is a protection against using crappy randomness  
<strong>\<suraeNoether\></strong> the hash function selected isn't a big deal as long as HKDF is correctly implemented as an HMAC, even crappy hash functions can produce indistinguishable results  
<strong>\<suraeNoether\></strong> but let's say you got clever and you said  
<strong>\<suraeNoether\></strong> "instead of using secret, let's use HKDF(secret) or SHA256(secret)\!" but then you can still be brute forced and you need some salt... which kicks the randomness can down the road to the salt.  
<strong>\<sarang\></strong> In the interest of time, let's finish up and move discussion outside of the formal meeting time  
<strong>\<sarang\></strong> 4. ACTION ITEMS  
<strong>\<oneiric\_\></strong> absolutely appreciate both your inputs sarang and suraeNoether  
<strong>\<sarang\></strong> I will review sgp\_'s proposal in more detail, finish up MPC code and more robust tests, and hopefully get that DLSAG-related paper out the door so we can post publicly  
<strong>\<gingeropolous\></strong> so I'm curious on where MRL stands on SPECTRE and, in general, switching from nakamoto-consensus. Was there a write-up from the previous investigation? I'm particularly interested because if monero ever actually achieves a strong decentralized network with many miners, the existing consensus system could make things really unstable. So I guess one possible area of investigation is how capable is nakamoto-consensus in a strong  
<strong>\<gingeropolous\></strong> decentralized network? I.e., if we had 3k nodes, all solo mining at 200 h/s, with transactions coming randomly from all the nodes, how well would the network actually function? Would it just be reorging constantly, with broken ring sigs causing txs to drop from existence?  
<strong>\<sarang\></strong> Later this month I'll post my next funding request, which as suraeNoether will have upfront payment to hedge against volatility  
<strong>\<gingeropolous\></strong> sorry, was waiting for something and hit enter  
<strong>\<sarang\></strong> both SPECTRE and PHANTOM have scaling issues  
<strong>\<sarang\></strong> and different guarantees  
<strong>\<sarang\></strong> there was a proposal to do a sort of hybrid between them, but AFAIK it has not been formally analyzed  
<strong>\<suraeNoether\></strong> gingeropolous: spectre is neat for a few reasons but crappy for scaling (although that part is totally mitigatable with const-time spectre). the neat stuff about spectre is that it's robust against partitions of the network  
<strong>\<suraeNoether\></strong> in nakamoto consensus, if the network is split into two pieces, both sides continue on and write to their ledgers...  
<strong>\<suraeNoether\></strong> but when they re-merge, only the writes on one side of the split ever become final  
<strong>\<suraeNoether\></strong> (except for the non-conflicting ones)  
<strong>\<suraeNoether\></strong> in spectre, on the other hand, writes made on both sides of the split have a chance of being merged into the "complete" ledger  
<strong>\<suraeNoether\></strong> so in that sense, together with some probability arguments, it's more robust than nakamoto  
<strong>\<sarang\></strong> I still remain bullish on an eventual general graph-based consensus mechanism  
<strong>\<suraeNoether\></strong> same. as tony arcieraierhal on twitter likes to complain about, the nakamoto consensus isn't actually a very good "solution" to byzantine consensus because of the partitioning property described above.  
<strong>\<suraeNoether\></strong> <https://en.wikipedia.org/wiki/CAP\_theorem> : nakamoto scores low on the P in CAP  
<strong>\<sarang\></strong> suraeNoether: your action items for this week?  
<strong>\<suraeNoether\></strong> spectre sacrifices C for P, i think  
<strong>\<suraeNoether\></strong> 1) feb report. 2) FFS request for next quarter. 3) matching simulations. 4) dlsag paper modifications. 5) reading about flyclient and mmr. i've back-burnered const-time spectre  
<strong>\<suraeNoether\></strong> sarang: your action items?  
<strong>\<sarang\></strong> Sounds good  
<strong>\<sarang\></strong> Any final comments before we formally wrap up?  
<strong>\<sarang\></strong> Ah, I already stated mine\!  
<strong>\<sarang\></strong> I will review sgp\_'s proposal in more detail, finish up MPC code and more robust tests, and hopefully get that DLSAG-related paper out the door so we can post publicly  
<strong>\<suraeNoether\></strong> oh i see that at the top of the section now  
<strong>\<sarang\></strong> OK, thanks to everyone for attending. We are now adjourned\!  
<strong>\<suraeNoether\></strong> allrighty. same bat time, same bat place.
