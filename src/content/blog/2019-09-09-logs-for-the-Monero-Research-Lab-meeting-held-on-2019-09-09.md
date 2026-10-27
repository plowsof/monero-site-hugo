---
title: Logs for the Monero Research Lab Meeting Held on 2019-09-09
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<suraeNoether\></strong> howdy\!  
<strong>\<ArticMine\></strong> Hi  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Hello  
<strong>\<sarang\></strong> For our ROUNDTABLE, I can go first  
<strong>\<sarang\></strong> A meta-note is that my next funding request needs feedback to determine if/when it should be opened: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/96>  
<strong>\<sarang\></strong> Aside from that, I've been working on inner-product proofs from IACR 944, which I know kenshamir\[m\] has also been working on  
<strong>\<sarang\></strong> Some neat efficiency things going on with those: <https://github.com/SarangNoether/skunkworks/tree/944-ipa-nozk/ipa-nozk>  
<strong>\<sarang\></strong> I've received plenty of edits/feedback to get the CLSAG paper submitted by its deadline  
<strong>\<suraeNoether\></strong> \*thumbs up for clsag\*  
<strong>\<sarang\></strong> And our friend RandomRun had a neat idea for applying a Groth proving system to transactions, detailed in a GitHub issue: <https://github.com/monero-project/research-lab/issues/56>  
<strong>\<suraeNoether\></strong> that proving system is also the basis for bootle's sublinear ring signatures, which was the basis for RTRS once upon a time  
<strong>\<sarang\></strong> The sizes are pretty big, but it may be possible to use some tricks from another paper to shrink them down  
<strong>\<suraeNoether\></strong> it's a strong foundational paper  
<strong>\<sarang\></strong> Yeah, it's used in Lelantus too  
<strong>\<sarang\></strong> That's my two cents so far  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<mikerah\></strong> Hello  
<strong>\<suraeNoether\></strong> my updates involve 1) matching, 2) proof of knowledge of signatures, and 3) looking at omniring as a general proving system for various uses  
<strong>\<suraeNoether\></strong> re: 1) i've made a bunch of local commits that i'll be squashing and pushing in a day or so  
<strong>\<suraeNoether\></strong> re: 2) i've identified a few of the foundational papers i'll be using to make my argument  
<strong>\<suraeNoether\></strong> re: 3) is a lot of reading and asking sarang questions  
<strong>\<sarang\></strong> neat  
<strong>\<sarang\></strong> Before we do questions and discussion, any other interesting work to share?  
<strong>\<suraeNoether\></strong> that's pretty much it so far; i have a stack of papers i've annihilated in the past few weeks, ranging from BOLT to bilinear pairings papers, but a lot of it has been background reading  
<strong>\<sarang\></strong> All right, we can also do QUESTIONS now  
<strong>\<sarang\></strong> suraeNoether: sounded from earlier like the PoKoS would likely require pairing operations?  
<strong>\<mikerah\></strong> I have a question. A few weeks back, I came on here asking about minimal smart contracts. I'm still doing some thinking about this. It doesn't seem like monero has any form of storage. Is this correct?  
<strong>\<sarang\></strong> What do you mean by storage?  
<strong>\<suraeNoether\></strong> yeah, all the foundational stuff i've found ranges from "easy" to "moderate" in the pairings setting, but has zero solutions at all for the DL setting. so i'm looking sort of into how to solve some of these problems in the DL setting. If i make progress on that front, it'd be of independent interest to the larger research community \*AND\* it would allow for some weeeeird stuff in Monero  
<strong>\<kenshamir\[m\]\></strong> suraeNoether: I was reading the bulletin and saw this issue: "Tech note/MRL bulletin on placing STARKs inside bulletproofs"  
<strong>\<kenshamir\[m\]\></strong> Is there anymore information regarding this?  
<strong>\<kenshamir\[m\]\></strong> Issue: 43  
<strong>\<mikerah\></strong> @kenshamir: How would fitting a STARK inside a bulletproof work? I can see the opposite working, though.  
<strong>\<suraeNoether\></strong> kenshamir\[m\]: I wanted to write a technical note re: that topic, or i want someone else to write it. i'm interested in the details behind placing a Sapling-style statement inside of a bulletproof. this is work that the zcash folks have done already, apparently, but i want a formal write-up. it's a common idea a lot of folks have, so it'd be nice to have a document to point to re: efficiency etc  
<strong>\<sarang\></strong> AFAIK the zcash-related work was simply estimating sizes/times based on circuit complexity  
<strong>\<suraeNoether\></strong> mikerah: a bulletproof can prove statements about inner products about vectors. so you can take a Sapling-style statement and formalize it in a bulletproof  
<strong>\<suraeNoether\></strong> sarang: indeedily do, neighborino, that's my recollection as well  
<strong>\<sarang\></strong> Well, bulletproofs can prove things about circuits natively :)  
<strong>\<sarang\></strong> The range proofs that are commonly used are a less general application  
<strong>\<suraeNoether\></strong> \*nod\*  
<strong>\<sarang\></strong> (but are more efficient)  
<strong>\<mikerah\></strong> @sarang: storage as in extra space in a transaction that one can take advantage of for random stuff. Bitcoin blocks have extra space that people have used in the past to store messages. In Ethereum, there's calldata.  
<strong>\<mikerah\></strong> \*extra space in a block  
<strong>\<sarang\></strong> There's an arbitrary data field that's also used to store certain transaction information and payment IDs  
<strong>\<sarang\></strong> tx\_extra  
<strong>\<suraeNoether\></strong> we have tx\_extra, but storing anything but uniform random data in it can lead to de-anonymization  
<strong>\<sarang\></strong> aye  
<strong>\<sarang\></strong> (or if not uniform random, "typical" data)  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<suraeNoether\></strong> i should caveat that  
<strong>\<sarang\></strong> There have been ideas in the past for things like return addresses etc  
<strong>\<suraeNoether\></strong> if any data is stored in tx\_extra, it should be encrypted  
<strong>\<mikerah\></strong> I see. I will continue thinking about this see if I can come up with something, eventually  
<strong>\<ArticMine\></strong> This begs the question how does one enforce encryption for tx\_extra?  
<strong>\<sarang\></strong> should \!= must  
<strong>\<Inge-\></strong> What is the length limitation of tx\_extra?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Have you looked into dual outputs for Lelantus? Maybe if instead using the hash of the signing key, it took the hash of two signing keys S = Hs(P\|\|Q), then also perhaps the commitments for the timelock could be stored in triple commitment? I haven't thought much about it though.  
<strong>\<sarang\></strong> Inge-: AFAIK there is no hard cap (aside from any block-specific limits etc.)  
<strong>\<sarang\></strong> worriedrise: interesting, but why a triple commitment?  
<strong>\<sarang\></strong> That commitment could be stored as a standard Pedersen commitment along with the new outputs, could it not?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> It could indeed. It would be one more point to store is all  
<strong>\<suraeNoether\></strong> "This begs the question how does one enforce encryption for tx\_extra?" \<-- add a tx\_extra\_valid field, change tx\_extra to a pair of group elements, use switch commitments in tx\_extra and in tx\_extra\_valid store a proof of knowledge of the opener of the commitment. if you stash plaintext in tx\_extra, you won't be able to open it as a commitment... that'd be one way. but i don't think enforcing it is  
<strong>\<suraeNoether\></strong> necessarily a good idea...  
<strong>\<suraeNoether\></strong> ArticMine: ^  
<strong>\<ArticMine\></strong> There is a possible attack vector if unencrypted data in tx\_extra is enforced or an incentive is provided. This came up in the payment id discussion  
<strong>\<suraeNoether\></strong> \*nod\* but enforcing that stuff in tx\_extra "looks uniform" can only go so far before head-meets-brick-wall  
<strong>\<kenshamir\[m\]\></strong> Reading a bit slow; sarang For rangeproofs, are you looking to switch out the inner product argument being used currently in bulletproofs for the one being used in 944?  
<strong>\<sarang\></strong> Oh, I was just tooling around with it  
<strong>\<kenshamir\[m\]\></strong> For the record, I think previously I mentioned 944 modifying bulletproofs inner product proof�, but bulletproofs is an inner product argument� also  
<strong>\<kenshamir\[m\]\></strong> Oh right  
<strong>\<sarang\></strong> ?  
<strong>\<kenshamir\[m\]\></strong> \<sarang "?"\> In case I said it in a previous monero meeting, not sure  
<strong>\<sarang\></strong> Yeah, I was playing around with the algebra needed to get the 944 IPA playing nicely with the optimized verification in BP  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> It sounds like the 944 authors did implementations of the BP range proofs with both inner product arguments, and claimed a fairly substantial speedup, if I'm reading correctly  
<strong>\<sarang\></strong> A much bigger speedup than I'd expect  
<strong>\<ArticMine\></strong> suraeNoether Right one can enforce encryption but one cannot prevent out of bounds publication of the decryption key  
<strong>\<kenshamir\[m\]\></strong> \<sarang "It sounds like the 944 authors d"\> Yep, I am trying to verify this against Dalek's implementation, but I have paused as something in the paper does not make sense to me at the moment  
<strong>\<sarang\></strong> kenshamir\[m\]: what's that?  
<strong>\<kenshamir\[m\]\></strong> Hopefully, I can get an asnwer on it and benchmark against Dalek's optimised implementation  
<strong>\<kenshamir\[m\]\></strong> \<sarang "kenshamir: what's that?"\> The \\Gamma\_{i} that is mentioned multiple times  
<strong>\<kenshamir\[m\]\></strong> Which is of size n-2 x n-2  
<strong>\<sarang\></strong> I assume, for example, that the 944 authors didn't unroll the IPA recursion in verification  
<strong>\<kenshamir\[m\]\></strong> Only holds on quadratic equation  
<strong>\<kenshamir\[m\]\></strong> I originally thought that it would hold n-2 quadratic equations  
<strong>\<sarang\></strong> Why would this be important for the underlying non-zk IPA?  
<strong>\<kenshamir\[m\]\></strong> \<sarang "I assume, for example, that the "\> Yep, I will need to implement your code in order to make the benchmarks fair because Dalek's code does this  
<strong>\<sarang\></strong> My suspicion is that the unrolled recursion wipes out almost all of the speedup  
<strong>\<sarang\></strong> Since most of the optimizations appear to be in scalar operations only  
<strong>\<kenshamir\[m\]\></strong> \<sarang "Why would this be important for "\> It does not make sense to me that a matrice only holds one equation, unless there is something I have misunderstand  
<strong>\<sarang\></strong> But this doesn't affect any uses of \_only\_ the underlying non-zk IPA, correct?  
<strong>\<sarang\></strong> So you don't mean that misunderstanding is a holdup for testing of the IPA for rangeproofs alone?  
<strong>\<kenshamir\[m\]\></strong> \<sarang "My suspicion is that the unrolle"\> Plus Dalek use a batch\_invert function for Scalars, so this may absolutely be the case  
<strong>\<sarang\></strong> Yeah, we also batch the inversions  
<strong>\<sarang\></strong> so it's really just a single inversion and some scalar-scalar multiplications (which are essentially free)  
<strong>\<kenshamir\[m\]\></strong> \<sarang "So you don't mean that misunders"\> I implemented the code using dense matrices, which is really in-efficient. I think there will be a big difference if we can store n-2 equations in one matrice, versus storing n-2 matrices of size `n-2 x n-2`  
<strong>\<sarang\></strong> Right, but if you're only testing a swap of the inner product argument in the bulletproofs rangeproof, you don't need any of the "higher-level" protocols  
<strong>\<sarang\></strong> the non-zk IPA stands on its own  
<strong>\<kenshamir\[m\]\></strong> \<sarang "Right, but if you're only testin"\> Oh right, I get what you mean  
<strong>\<sarang\></strong> This is what I assume that table at the end of 944 was doing  
<strong>\<sarang\></strong> For the general applications, totally  
<strong>\<sarang\></strong> I think we're on the same page :D  
<strong>\<kenshamir\[m\]\></strong> I was thinking of benchmarking 944 rangeproof vs bulletproofs. But you are correct, in that we also need to benchmark 944s IPA\_Nozk vs bulletproofs IPA  
<strong>\<sarang\></strong> The paper seems to have both  
<strong>\<sarang\></strong> Perhaps the latter benchmarks were only in the extended 944 paper (I'd have to check)  
<strong>\<sarang\></strong> but no matter reallly  
<strong>\<sarang\></strong> AFAICT the last timing table is just swapping the non-zk IPA  
<strong>\<kenshamir\[m\]\></strong> Yeah it had both, the benchmarks show that they are basically the same once bulletproofs uses IPA\_NoZK  
<strong>\<kenshamir\[m\]\></strong> Yeah  
<strong>\<sarang\></strong> Although the speedup was still impressive from just IPA\_NoZK (hence wanting to know if unrolling makes it irrelevant)  
<strong>\<sarang\></strong> something like \~30% IIRC?  
<strong>\<sarang\></strong> which seems absurd  
<strong>\<kenshamir\[m\]\></strong> Yeah, it was in that ballpark  
<strong>\<sarang\></strong> Still, worth a shot anyway to confirm :)  
<strong>\<sarang\></strong> Probably will be worth writing to the authors to note this  
<strong>\<kenshamir\[m\]\></strong> I will also test the normal IPA\_NOZK without multi-exp versus bulletproofs with multiexp  
<strong>\<sarang\></strong> I'll send them my unrolling algorithm too, to provide better benchmarks  
<strong>\<sarang\></strong> Multiexp will be huge, of course, in any of the applications  
<strong>\<sarang\></strong> when the size gets large  
<strong>\<kenshamir\[m\]\></strong> They used a generic library too, so this could play a role in the benchmarks  
<strong>\<kenshamir\[m\]\></strong> Not sure how/if though  
<strong>\<kenshamir\[m\]\></strong> \<sarang "when the size gets large"\> Yep  
<strong>\<sarang\></strong> Yeah, but that shouldn't matter, ideally, if they did parallel implementations  
<strong>\<sarang\></strong> But hey, that's part of the point of a preprint, I suppose  
<strong>\<sarang\></strong> Get feedback and additional info\!  
<strong>\<sarang\></strong> Perhaps we can collaborate on feedback to the authors, kenshamir\[m\]  
<strong>\<sarang\></strong> once we have numbers on this stuff  
<strong>\<sarang\></strong> I think it would be useful in their paper to note these things  
<strong>\<kenshamir\[m\]\></strong> \<sarang "Perhaps we can collaborate on fe"\> Yep that would be great  
<strong>\<sarang\></strong> awesome  
<strong>\<kenshamir\[m\]\></strong> Yeah, because this was one of the more important contributions of the paper  
<strong>\<sarang\></strong> for sure  
<strong>\<kenshamir\[m\]\></strong> The proof system was also great  
<strong>\<sarang\></strong> 10/10 would verify?  
<strong>\<sarang\></strong> =p  
<strong>\<kenshamir\[m\]\></strong> :D  
<strong>\<sarang\></strong> In the interest of time, are there other questions?  
<strong>\<sarang\></strong> OK\!  
<strong>\<sarang\></strong> On to ACTION ITEMS before we close  
<strong>\<sarang\></strong> I'll be continuing several things: proving systems, benchmarks, paper submission  
<strong>\<sarang\></strong> Feel free to comment on the proposed funding request, to determine if it should be opened  
<strong>\<sarang\></strong> suraeNoether: your action items?  
<strong>\<suraeNoether\></strong> ah, yes, sorry about that: squashing a bunch of commits for matching, to whip thring signatures into shape for the FC conference, and to start putting my ideas on POKOS down  
<strong>\<suraeNoether\></strong> but mainly matching, because that is so close to giving good results  
<strong>\<sarang\></strong> Awesome\! Any other action items to share before we close?  
<strong>\<suraeNoether\></strong> just that i love all of you  
<strong>\<suraeNoether\></strong> be sure to comment on sarang's proposal request/comment period  
<strong>\<kenshamir\[m\]\></strong> 😳  
<strong>\<sarang\></strong> Aw shucks  
<strong>\<sarang\></strong> Thanks to everyone for participating\! Logs will be posted to GitHub shortly
