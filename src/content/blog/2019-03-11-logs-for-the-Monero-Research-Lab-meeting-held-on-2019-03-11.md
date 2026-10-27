---
title: Logs for the Monero Research Lab Meeting Held on 2019-03-11
summary: Network upgrade, Point release discussions, MRL work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Our meeting begins presently  
<strong>\<sarang\></strong> Let's go ahead and get started. Agenda is here: <https://github.com/monero-project/meta/issues/314>  
<strong>\<suraeNoether\></strong> howdy everyone  
<strong>\<sarang\></strong> 1. GREETINGS  
<strong>\<sarang\></strong> hi  
<strong>\<MRL-discord\> \<Isthmus\></strong> Hello\! Biking, in soon.  
<strong>\<parasew\[m\]\></strong> hello\!  
<strong>\<sarang\></strong> Let's recap 2. NETWORK UPGRADE  
<strong>\<sarang\></strong> Kudos to everyone for a successful first upgrade  
<strong>\<sarang\></strong> I don't recall when the second was slated to occur, since block arrival was stunted  
<strong>\<sarang\></strong> Any thoughts on the upgrade after the fact?  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Hi  
<strong>\<sarang\></strong> I believe it was dEBRUYNE who wanted an upcoming meeting specifically to talk more deeply about the future of PoW  
<strong>\<parasew\[m\]\></strong> anyone monitored the "old chain"? if there have been this large amount of asics on there, and not turned off it should be visible  
<strong>\<sarang\></strong> I believe sgp\_ ran some blackball numbers on it  
<strong>\<sarang\></strong> and found essentially nothing of interest  
<strong>\<sarang\></strong> but as far as hashrate, I am not sure  
<strong>\<sgp\_\></strong> yeah, no chain reactions so far, very few known spent outputs through reused key images  
<strong>\<sgp\_\></strong> impact on network privacy so far is essentially 0  
<strong>\<sarang\></strong> sgp\_: were the key image reuse numbers for only v9 and v10?  
<strong>\<sgp\_\></strong> yes, just those two  
<strong>\<sarang\></strong> great, thanks  
<strong>\<sarang\></strong> Relating to this, we can also introduce 3. NEXT POINT RELEASE  
<strong>\<sarang\></strong> Not all desired non-consensus changes made it in to this release, so Sometime Soon (tm) will be a point release  
<strong>\<sarang\></strong> BP optimizations will be one nice addition  
<strong>\<sarang\></strong> I would like output selection to also be included... we talked about it at length at an earlier meeting  
<strong>\<dEBRUYNE\></strong> sarang: Correct. It's a topic with a lot of depth that requires an extensive discussion imo  
<strong>\<sarang\></strong> suraeNoether: do you have a current recommendation for output selection?  
<strong>\<suraeNoether\></strong> i'm running into problems testing the matching code, based on this problem too  
<strong>\<sarang\></strong> Here is a discussion of the different algorithms: <https://github.com/monero-project/meta/issues/307#issuecomment-466514757>  
<strong>\<suraeNoether\></strong> iirc the output lineup method performs quite well  
<strong>\<sarang\></strong> I prefer it among the others that were tested  
<strong>\<sarang\></strong> But it's a change that deserves more than two thumbs-up :)  
<strong>\<suraeNoether\></strong> there is no optimal solution, but some solutions are better than others and the output lineup method is more reasonable than the other proposals, and i have no new proposals to make (yet)  
<strong>\<sarang\></strong> I updated the sim code (link in agenda) to examine the output weighting in more details  
<strong>\<sarang\></strong> Hopefully the BP optimizations are less contenious  
<strong>\<suraeNoether\></strong> uhm i think i have one possible proposal that i want to chat about with you by side channel to hash out some details  
<strong>\<sarang\></strong> sure  
<strong>\<sarang\></strong> We should have a formal recommendation before whatever date is set for the point release code freeze  
<strong>\<sarang\></strong> Anything else relating to the point upgrade that ought to be discussed?  
<strong>\<sarang\></strong> ping moneromooo perhaps  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> I just want timelines. Nothing to say on content.  
<strong>\<moneromooo\></strong> hi  
<strong>\<moneromooo\></strong> What's the question ? :)  
<strong>\<moneromooo\></strong> I don't know about any date. Depends when we get all the stuff on master ready really.  
<strong>\<sarang\></strong> Anything relating to the next point release you'd like us to discuss?  
<strong>\<moneromooo\></strong> None that come to mind right now.  
<strong>\<sarang\></strong> ty  
<strong>\<sarang\></strong> In that case, let's move to 4. ROUNDTABLE  
<strong>\<sarang\></strong> suraeNoether: care to go first?  
<strong>\<sarang\></strong> OK, I can go first instead  
<strong>\<suraeNoether\></strong> ok  
<strong>\<sarang\></strong> aha, go ehead  
<strong>\<suraeNoether\></strong> heh  
<strong>\<suraeNoether\></strong> Well, my simulations for the matching code are to the point where i'm running a matching on some test data now to generate a confusion matrix.  
<strong>\<suraeNoether\></strong> i'm also editing the manuscript describing the whole process  
<strong>\<suraeNoether\></strong> one of the problems i'm running into is actually simulating our output selection in part because it's not clear which direction we are going yet  
<strong>\<suraeNoether\></strong> and it occurred to me that this could help inform our choice of output selection by seeing if one of these possibilities makes matching easier or harder  
<strong>\<sarang\></strong> IMO matching expect spend with proper weighting seems optimal enough from a purely timing perspective  
<strong>\<sarang\></strong> (leaving out questions of binning etc)  
<strong>\<suraeNoether\></strong> when i say easy or hard i don't mean in terms of time, because as we've seen matching is essentially super duper fast  
<strong>\<suraeNoether\></strong> i mean in terms of false negative and false positive rates  
<strong>\<suraeNoether\></strong> but you are 100% on that  
<strong>\<sarang\></strong> aw shucks  
<strong>\<suraeNoether\></strong> i'm working on a variety of other side things but i'm shooting for this matching paper to be complete and published some time in the next 2 months  
<strong>\<sarang\></strong> Excellent  
<strong>\<suraeNoether\></strong> if we get more speakers for the konferenco, then i won't be speaking, but otherwise i will probably be presenting on this at the konferenco  
<strong>\<sarang\></strong> Neat; anything else of interest to share?  
<strong>\<suraeNoether\></strong> that's all i have today, thanks\!  
<strong>\<sarang\></strong> Righto  
<strong>\<sarang\></strong> I have a few things  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> The line up is looking great btw\! Fantastic effort for a first konferenco  
<strong>\<suraeNoether\></strong> catching up on lots of reaidng in algebraic geometry :D  
<strong>\<sarang\></strong> First, my next FFS/CCS will be posted soon  
<strong>\<sarang\></strong> As was discussed here, in -community, and elsewhere, the request will be for immediate payout  
<strong>\<sarang\></strong> This means both donors and I know the actual value of the donations  
<strong>\<sarang\></strong> Since this is a big change, any questions or comments on it?  
<strong>\<sarang\></strong> (presumably suraeNoether will be doing the same arrangement)  
<strong>\<suraeNoether\></strong> i'm in support of this, and i will indeed be mimicking this  
<strong>\<sarang\></strong> Folks who do not trust us to run with the money should, of course, not donate  
<strong>\<sarang\></strong> But my hope is that our records have shown we're good for it :D  
<strong>\<binaryFate\></strong> happy we came to that solution eventually, hopefully will be better for your guys  
<strong>\<sarang\></strong> Thanks to binaryFate and others for agreeing to this change  
<strong>\<binaryFate\></strong> yes the idea is that donors being careful should discourage randomers to do the same  
<strong>\<sarang\></strong> The CCS posting will \_very\_ clearly state the arrangement, so there is no confusion  
<strong>\<binaryFate\></strong> If you figure out the markdown  
<strong>\<sarang\></strong> Yes indeed  
<strong>\<moneromooo\></strong> Technically, it's within the existing rules as stated: one milestone, which consists of "sarang starts working" :)  
<strong>\<sarang\></strong> Second, the paper that suraeNoether and I have been collaborating with external researchers on (DLSAG et al.) is in final review now  
<strong>\<sarang\></strong> We've been asked not to share it before it's released as a preprint, as a courtesy to all authors  
<strong>\<suraeNoether\></strong> \*nod\*  
<strong>\<sarang\></strong> It has some great details on useful constructions that I'm sure we'll discuss at length after the preprint goes to IACR  
<strong>\<sarang\></strong> it'll be submitted for a conference as well  
<strong>\<sarang\></strong> Third, I wrote up some additional tests and code for Bulletproofs MPC  
<strong>\<dEBRUYNE\></strong> sarang: How does this work if the proposal is not fully funded yet when your period starts?  
<strong>\<sarang\></strong> Two options: either the bulk is paid out and it stays open until filled  
<strong>\<sarang\></strong> or it all sits there until fully funded  
<strong>\<sarang\></strong> I prefer the first, but am open to discussion  
<strong>\<sarang\></strong> Regarding Bulletproofs MPC, real\_or\_random had some great thoughts on this before the meeting (but I won't put him on the spot)  
<strong>\<suraeNoether\></strong> i imagine that the important part is laying out which way it goes in the proposal  
<strong>\<sarang\></strong> the question has to do with what a malicious player can do  
<strong>\<sarang\></strong> We chatted about the fact that an evil player could try to pull what amounts to a cancellation of partial proof elements, effectively setting the inputs to the hash that generates a F-S challenge  
<strong>\<sarang\></strong> I couldn't find a way that this could be used as an exploit, aside from obviously generated an invalid proof  
<strong>\<sarang\></strong> but the security proofs for BPs do require that F-S challenges are uniform  
<strong>\<sarang\></strong> I had neglected that point when I had thought about this earlier  
<strong>\<sarang\></strong> My strong suspicion is that proof elements are still uniformly distributed in the presence of a dishonest challenge due to the prover's randomness, and that you still get zk in this case (but not provably)  
<strong>\<sarang\></strong> Moral: if we do anything in the future that requires/desires this scheme, these things would need to be considered  
<strong>\<sarang\></strong> Any questions/comments relating to this?  
<strong>\<sarang\></strong> allrightythen  
<strong>\<suraeNoether\></strong> i think we should continue to ponder it and write something up formally about the BP MPC schemes  
<strong>\<sarang\></strong> Well that's the thing... there's really nothing to write formally  
<strong>\<sarang\></strong> You can probably solve all the theoretical woes by having all players commit to their proof elements before multicasting them  
<strong>\<sarang\></strong> then an honest prover is guaranteed uniform F-S challenges  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> Sorry but I'm a little out of the loop here. What exactly are BP MPC for? something to do with multisig with BP?  
<strong>\<suraeNoether\></strong> it's nice to think about collectively computing BP range proofs, but I'm still v curious about the coinjoin approach that we are considering on the larger scale.  
<strong>\<sarang\></strong> Ideally, untrusted parties could generate single BPs for outputs  
<strong>\<suraeNoether\></strong> after all, it's hard to even think about threat models unless we know how these things will be used in practice  
<strong>\<sarang\></strong> Sure, this is all pie-in-the-sky right now  
<strong>\<suraeNoether\></strong> learninandlurkin: collaborating with friends to compute a range proof for a coinjoin style transaction, so that the participants don't reveal their amounts to each other  
<strong>\<sarang\></strong> But yes, the threat model would be very different depending on how the rounds go  
<strong>\<sarang\></strong> Finally, suraeNoether had shown me this a while back: <https://lelantus.io/lelantus.pdf>  
<strong>\<suraeNoether\></strong> agreed on the commit-and-reveal; expensive but usually does the trick to ensure participants can't be rewound inappropriately  
<strong>\<sarang\></strong> An interesting application of some of the fundamentals behind Bulletproofs and the old StringCT scheme  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> So... allowing multi-input transactions where each user doesn't know the amounts of the other inputs? Sounds useful  
<strong>\<suraeNoether\></strong> learninandlurkin hence our interest in nailing down threat models \*nod\*  
<strong>\<sarang\></strong> I've been playing around with some of the math in that paper to see what nuggets could be extracted  
<strong>\<suraeNoether\></strong> oh i had a brief thing to point out: isthmus and n3ptune at noncesense-research-lab answered one of my requests and we now have a complete empirical distribution of number of inputs and outputs per transaction  
<strong>\<suraeNoether\></strong> forgot to mention this:  
<strong>\<sarang\></strong> Neato, where is this distribution to be found?  
<strong>\<suraeNoether\></strong> <https://github.com/noncesense-research-lab/tx\_in\_out\_distribution>  
<strong>\<suraeNoether\></strong> the data surprised me  
<strong>\<dEBRUYNE\> \<sarang\></strong> I prefer the first, but am open to discussion \<= I'd be OK with the first, but perhaps it would be most convenient to use a rounded number  
<strong>\<dEBRUYNE\></strong> e.g. if 211 XMR is funded, pay out 200  
<strong>\<sarang\></strong> You won't believe what's in tx\_distribution\_in.csv\!  
<strong>\<dEBRUYNE\></strong> Mebbe malware  
<strong>\<dEBRUYNE\></strong> :P  
<strong>\<suraeNoether\></strong> super heavy tails for one thing, and a rootkit for another  
<strong>\<sarang\></strong> dEBRUYNE: perhaps a full payout at date X, and then a second payout at either date Y or completion, whichever comes first  
<strong>\<binaryFate\> \<sarang\></strong> I prefer the first, but am open to discussion \<-- donors will have no incentive to fund in time, it will drag till the end of the period  
<strong>\<sarang\></strong> binaryFate: how would you do it?  
<strong>\<binaryFate\></strong> I like the incentive to donors of you proposing something and getting to work on it only if funded  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> I imagine coinjoining going on would really complicate output selection. Or is there some idea where they work off each other to get rid of heuristics?  
<strong>\<sarang\></strong> Depends on how timely it is  
<strong>\<suraeNoether\></strong> learningandlurkin coinjoin brings a whole new nightmare to the party. does everyone bring their own mix-ins? certainly nothing is to stop a malicious party from coinjoining with a bunch of badly selected mix-ins  
<strong>\<moneromooo\></strong> A ring is one person only. Fake output selection is untouched.  
<strong>\<sarang\></strong> Well each input signs with its own ring  
<strong>\<sarang\></strong> ^  
<strong>\<moneromooo\></strong> That person makes their own ring, yes. Otherwise others would know which is the real out.  
<strong>\<sarang\></strong> The benefit is breaking the assumption of one-party control of outputs and the link to the input rings  
<strong>\<binaryFate\></strong> What about simple attack of using the same 10 decoys as one of the other participants?  
<strong>\<suraeNoether\></strong> ^  
<strong>\<msvb-mob\></strong> Is parasew, nevvton, or txmr in the channel?  
<strong>\<binaryFate\></strong> mmm you don't know which are decoys, nevermind ^^  
<strong>\<sarang\></strong> If this moves forward, hopefully we can determine the necessary practical security for BPs  
<strong>\<sarang\></strong> If we can't aggregate, they'd have to be separate for each output  
<strong>\<suraeNoether\></strong> my beard is getting very thoroughly stroked this morning. much to think about...  
<strong>\<sarang\></strong> I believe we'd get practical security without player commitments, but not provable  
<strong>\<sarang\></strong> Anyway: does anyone else wish to share interesting research before we close?  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> Yes it sounds like the interplay between coinjoin and ringsigs will require some diagrams for me to ever understand. Could get complicated.  
<strong>\<suraeNoether\></strong> i think you would want a commit-and-reveal stage for everyone to see the ring members to prevent malicious ring intersection in the coinjoin  
<strong>\<sarang\></strong> MoneroCoinJoin: an easy 14-round process\!  
<strong>\<suraeNoether\></strong> isthmus and i have been chatting about methods of extracting the true spend-time distribution from the monero blockchain without knowing exactly which outputs have been spent  
<strong>\<suraeNoether\></strong> that's a very nascent conversation, though I think it'll end up being a very straightforward project  
<strong>\<sarang\></strong> Discussions in \#noncesense-research-lab I presume?  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> so, truish spend-time distribution  
<strong>\<binaryFate\></strong> Are there regular meetings on this or just continuous discussion? I had been working on this at some point and have some code around aiming to graphically show the real spend distribution  
<strong>\<sarang\></strong> I've seen a few informal conversations in \#noncesense-research-lab but didn't know if suraeNoether had something more formal  
<strong>\<suraeNoether\></strong> binaryFate: ah, no, this has been a casual conversation by side channel, but there is clearly interest  
<strong>\<suraeNoether\></strong> i'll start blabbing about it in here more publicly  
<strong>\<sarang\></strong> In the interest of time, let's review 6. ACTION ITEMS and then close to continue discussion afterword  
<strong>\<binaryFate\></strong> Ok don't hesitate to ping me on this  
<strong>\<sarang\></strong> I will be posting my CCS request soon, tidying up the output selection stuff for a recommendation, getting the DLSAG application paper reviewed and out the door, and playing around with that Lelantus paper when/if I get a chance  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<suraeNoether\></strong> CCS request, working on simulations and measurable numbers for matching, and looking into using our matching code to answer questions about output selection  
<strong>\<sarang\></strong> excellent  
<strong>\<suraeNoether\></strong> also casual github maintenance  
<strong>\<sarang\></strong> Any final questions or remarks before we adjourn?  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> once you guys have made a recommendation for output selection  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> and it gets implemented, what's the next big focus?  
<strong>\<sarang\></strong> There will be much to consider in the realm of refund and payment channels  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> Ooh yes the refund ideas from a while back were really interesting  
<strong>\<sarang\></strong> and some aspects of output selection, like linking spends across rings in txns, is not solved yet  
<strong>\<xmrmatterbridge\> \<learninandlurkin\></strong> Seems like a logical next area of research  
<strong>\<sarang\></strong> and if coinjoin works out, there will be a lot to consider with that  
<strong>\<sarang\></strong> Also transaction relay and network-level anonymity stuff that's still in progress  
<strong>\<sarang\></strong> To quote the Simpsons: "like the cleaning of a house... IT NEVER ENDS"  
<strong>\<sarang\></strong> But on that note, our meeting does end  
<strong>\<sarang\></strong> Thanks to everyone for attending. We're adjourned; let the conversations continue
