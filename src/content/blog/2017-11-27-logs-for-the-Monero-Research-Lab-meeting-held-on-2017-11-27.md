---
title: Logs for the Monero Research Lab Meeting Held on 2017-11-27
summary: SPECTRE, multisig, Bulletproofs (range proofs), ZKStarks, ASIC resistance, and miscellaneous
tags: [dev diaries, crypto, research]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<suraeNoether\></strong> anyway, agenda for the day: 1) Greetings, 2) Sarang's work 3) my work 4) open discussion. The new zksnark paper will presumably take up some of 4. :P  
<strong>\<suraeNoether\></strong> 1) is done i guess. :\\  
<strong>\<suraeNoether\></strong> 2) Sarang want to bring us up to speed?  
<strong>\<sarang\></strong> roger  
<strong>\<sarang\></strong> I have working code for both linear and logarithmic bulletproofs that tests correctly  
<strong>\<sarang\></strong> I'm finishing up a few small optimizations to reduce the curve op count  
<strong>\<suraeNoether\></strong> nice  
<strong>\<sarang\></strong> and then it'll be ready for C++  
<strong>\<sarang\></strong> moneromooo already has the linear version up and running  
<strong>\<suraeNoether\></strong> fantastic\!  
<strong>\<sarang\></strong> That's been my big project  
<strong>\<suraeNoether\></strong> page 8 of the new zksnark paper talks about dot product proof protocols  
<strong>\<sarang\></strong> orly  
<strong>\<sarang\></strong> That's the big shiny toy of bulletproofs  
<strong>\<suraeNoether\></strong> literally caught my eye  
<strong>\<suraeNoether\></strong> or rather  
<strong>\<suraeNoether\></strong> metaphorically? well  
<strong>\<suraeNoether\></strong> anyway, my point is i have done nothing but skim the paper (in the past 10 minutes) and that popped out at me  
<strong>\<suraeNoether\></strong> you have also been helping me on multisig, as well, don't discount that  
<strong>\<sarang\></strong> I shan't  
<strong>\<suraeNoether\></strong> anything else?  
<strong>\<suraeNoether\></strong> gratz on getting it working  
<strong>\<sarang\></strong> Thanks to everyone who offered support in the most recent fund drive  
<strong>\<sarang\></strong> I remain humbled  
<strong>\<suraeNoether\></strong> thank you, sarang\! thanks again  
<strong>\* sarang</strong> takes a small bow  
<strong>\<suraeNoether\></strong> As for my work, I've been working on the multisig paper, which is intended to 1) present a formal model of our threshold ringct, and 2) show how our current implementation compares to that formal model. there are differences that i'm hunting down one by one  
<strong>\<suraeNoether\></strong> JollyMort\[m\] has found several already, and we've been having discussions about it the past few days  
<strong>\<suraeNoether\></strong> That has represented the vast majority of my time  
<strong>\<suraeNoether\></strong> In addition to that, I believe I may have a problematic example case of SPECTRE. the original authors sweep my concern aside, but i wanted to bring it up and see if anyone had any thoughts  
<strong>\<sarang\></strong> I'm intrigued  
<strong>\<suraeNoether\></strong> if two transactions using the same input are relayed nearly simultaneously, they will find their way into two separate blocks. they will appear as conflicting transactions until the spectre algorithm arranges one block to precede the other  
<strong>\<suraeNoether\></strong> or stay conflicting forever if spectre can never linearly order them  
<strong>\<suraeNoether\></strong> this can happen with a simple example of a "mostly linear" blockchain, except with a single block in the chain replaced with a pair of blocks like a diamond shape:  
<strong>\<suraeNoether\></strong> \_\_\_/\\\_\_\_  
<strong>\<suraeNoether\></strong> /  
<strong>\<suraeNoether\></strong> something that looks like that  
<strong>\<suraeNoether\></strong> then any transactions that conflict in the pair of non-linearly-ordered blocks will appear to conflict forever  
<strong>\<suraeNoether\></strong> this allows a clumsy user who re-sends a transaction twice becuase he's foolish to lose his funds.  
<strong>\<sarang\></strong> Can we back this up with a simulation?  
<strong>\<suraeNoether\></strong> i mean, we could, but there's a solid chain of lemmas that lead to a theorem i can write up later if you like  
<strong>\<suraeNoether\></strong> using the theorems about how rapidly sets in spectre get finalized  
<strong>\<sarang\></strong> Even better  
<strong>\<sarang\></strong> \*lemmata  
<strong>\<suraeNoether\></strong> now, the spectre authors said "the only reason someone would relay two transactions like this is to attempt a double spend, so it's okay that the funds are lost."  
<strong>\<sarang\></strong> lolwut  
<strong>\<suraeNoether\></strong> well  
<strong>\<suraeNoether\></strong> the idea is that htey are <em>two</em> transactions with valid signatures using the same input  
<strong>\<suraeNoether\></strong> or rather, using at least one of the same inputs  
<strong>\<suraeNoether\></strong> so by definition, it's a double spend  
<strong>\<suraeNoether\></strong> and i can't really think of a scenario where someone would compute two signatures separately like that, then relay them nearly simultaneously like that... on accident  
<strong>\<suraeNoether\></strong> BUT  
<strong>\<suraeNoether\></strong> it's enough of a leap for me to be concerned  
<strong>\<suraeNoether\></strong> moreover  
<strong>\<suraeNoether\></strong> i'm not sure if that sort of "double spend implies money lost forever instead of "eventually one of the two spends is accepted."  
<strong>\<suraeNoether\></strong> and what's really crazy  
<strong>\<suraeNoether\></strong> is that if block arrival times are very fast, like 10/s as in the original spectre paper... this problem is solved <em>with high probability</em>  
<strong>\<suraeNoether\></strong> so, that's where SPECTRE is sitting.  
<strong>\<suraeNoether\></strong> and lastly, my viewkey proposal  
<strong>\<suraeNoether\></strong> s/lost forever/lost forever" philosophy instead of...  
<strong>\<scoobybejesus\></strong> I own address A, B, and C. I simultaneously send the same output as an input in txns A -\>\*\* B and A -\>\*\* C. Free coins? Or B and C each now have unspendable outputs?  
<strong>\<suraeNoether\></strong> a miner would see two conflicting transactions, so neither would be considered valid  
<strong>\<suraeNoether\></strong> and constructing another transaction later A-\>\*\*D will also be considered invalid  
<strong>\<scoobybejesus\></strong> Ah. Thanks.  
<strong>\<suraeNoether\></strong> so until spectre re-orgs the block-DAG so that the transaction A-\>\*\*B precedes A-\>\*\*C or vice versa, it's locked forever  
<strong>\<gingeropolous\></strong> right, i was wondering that... i though eventually it resolves to a bloclchain  
<strong>\<gingeropolous\></strong> or blockchain  
<strong>\<suraeNoether\></strong> actually, that's the problem: if block arrival rate is slow and you have a fork  
<strong>\<suraeNoether\></strong> the next block to arrive will point to both blocks as parents  
<strong>\<sarang\></strong> yeah  
<strong>\<suraeNoether\></strong> and if all blocks from there on out point to that common child block, those two blocks will never be linearly ordered  
<strong>\<suraeNoether\></strong> so, this would also be solved by simply telling people to try to avoid making more than 1 transaction per target block arrival rate <em>personally</em>  
<strong>\<suraeNoether\></strong> otherwise they are burning their own money, in a sense  
<strong>\<sarang\></strong> that's quite the kludge  
<strong>\<gingeropolous\></strong> so dbl spends are punished... kinda  
<strong>\<suraeNoether\></strong> gingeropolous: yes, it provides a strong incentive against making a double spend attack  
<strong>\<suraeNoether\></strong> which is nice  
<strong>\<suraeNoether\></strong> i just don't want to make it so that badly informed users of Monero don't accidentally burn their money  
<strong>\<gingeropolous\></strong> i wonder if we could protocolize an incubate function, where a tx has to sit in the txpool for n blocks  
<strong>\<suraeNoether\></strong> sarang it's not too much of a kludge, if our block arrival rate is 1/second or something  
<strong>\<sarang\></strong> hmm  
<strong>\<suraeNoether\></strong> gingeropolous: ooooh  
<strong>\<gingeropolous\></strong> kind of a bitch because timestamping and all..  
<strong>\<suraeNoether\></strong> it's worth thinking about though\!  
<strong>\<suraeNoether\></strong> that's a good idea  
<strong>\<suraeNoether\></strong> okay, so does anyone else have anything they want to share about their work?  
<strong>\<sarang\></strong> I could add that I've posted my monthly report: <https://www.reddit.com/r/Monero/comments/7frn7i/november_monthly_report_from_sarang_noether/>  
<strong>\<sarang\></strong> Comments welcome  
<strong>\<suraeNoether\></strong> Also, I'd like to thank the community for funding me as well  
<strong>\<suraeNoether\></strong> It's astonishing  
<strong>\<suraeNoether\></strong> In other announcements....  
<strong>\<suraeNoether\></strong> rehrar is working on the next Monero Revuo  
<strong>\<suraeNoether\></strong> I'm not sure what the publication timeline on that is supposed to be  
<strong>\<suraeNoether\></strong> but it's the quarterly newsletter wherein he sort of interviews the teams at MRL in charge of various projects  
<strong>\<sarang\></strong> Any other discussion items?  
<strong>\<suraeNoether\></strong> he and Sarang and I are going to have a sit-down and talk about the direction MRL is heading. I am interested in writing up current standards for Monero, I know Sarang is also, and I want to start on that as soon as Multisig is done.  
<strong>\<sarang\></strong> ah yes  
<strong>\<suraeNoether\></strong> For each Monero standard, I also want to write up at least one proposal for replacing the standard in the case that the security of that standard is compromised  
<strong>\<suraeNoether\></strong> I also want to compile arguments for and against replacing certain standards sooner rather than later, for example, our "nonstandard" hash function  
<strong>\<suraeNoether\></strong> oh man, i should ping andytoshi too  
<strong>\<suraeNoether\></strong> this includes our proof of work standard  
<strong>\<sarang\></strong> That strikes me as our least-standard "thing"  
<strong>\<suraeNoether\></strong> cryptonight has some value, but it's as homebrew as can be  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<suraeNoether\></strong> i wouldn't mind putting up a portion of my funding for this period toward a Proof of Work contest for Monero's replacement proof of work scheme  
<strong>\<suraeNoether\></strong> hmm  
<strong>\* iDunk</strong> reaches for a pitchfork  
<strong>\<suraeNoether\></strong> ?  
<strong>\<suraeNoether\></strong> cryptonight has value because of asic resistance. i'm okay with asics if they are commoditized. i'm not married to cryptonight in any way  
<strong>\<suraeNoether\></strong> i'm in a non-monogamous relationship with cryptonight  
<strong>\<suraeNoether\></strong> ok, well  
<strong>\<suraeNoether\></strong> anything else to discuss?  
<strong>\<dEBRUYNE\></strong> suraeNoether: i wouldn't mind putting up a portion of my funding for this period toward a Proof of Work contest for Monero's replacement proof of work scheme \<= I think othe already has some back up plans  
<strong>\<silur\></strong> apparently V wants ringCT in EVM2  
<strong>\<dEBRUYNE\></strong> You might want to talk to him about it  
<strong>\<suraeNoether\></strong> othe are you around?  
<strong>\<othe\></strong> Yes  
<strong>\<suraeNoether\></strong> silur V = vitalik?  
<strong>\<silur\></strong> yep  
<strong>\<suraeNoether\></strong> othe you've been thinking about POW?  
<strong>\<othe\></strong> Yea  
<strong>\<othe\></strong> Slight changes we can implement will break all asics  
<strong>\<silur\></strong> I introduced stringCT/ruffCT PoC code in our research channel hope it will go somewhere  
<strong>\<othe\></strong> Trivial to implement in cpu and gpu  
<strong>\<suraeNoether\></strong> oooh, that's fantastic\! fluffypony sent me at least one recommendation for that a few weeks ago  
<strong>\<suraeNoether\></strong> but i haven't had time to look into it  
<strong>\<othe\></strong> Yeah that one is an example  
<strong>\<silur\></strong> what is this new POW?  
<strong>\<suraeNoether\></strong> ok, but you aren't talking about <em>replacing cryptonight</em> but modifying it  
<strong>\<suraeNoether\></strong> silur othe has apparently been looking at the cryptonight code very closely and determining how to swap bits around or mess with the implementation to improve asic resistance without harming gpu or cpu performance  
<strong>\<othe\></strong> Just modifying it randomly  
<strong>\<silur\></strong> I thought cryptonight is asic resistant by design O.o  
<strong>\<othe\></strong> Takes like 5 lines of code in gpu miner  
<strong>\<silur\></strong> I knew that it's not like... cuckoo cycle hard but still  
<strong>\<othe\></strong> Cuckoo is not hard at all  
<strong>\<suraeNoether\></strong> yeah cuckoo isn't asic resistant at all  
<strong>\<suraeNoether\></strong> i have a paper around here about it  
<strong>\<silur\></strong> dayum  
<strong>\<suraeNoether\></strong> silur cryptonight takes up L3 cache like crazy, so the asic resistance comes from forcing it through a bottleneck  
<strong>\<suraeNoether\></strong> but you could still have an asic on the back end of the bottleneck  
<strong>\<othe\></strong> There's really nothing asic resistant if u hsve money  
<strong>\<suraeNoether\></strong> so if someone creatively designed a computer with a huge L3 cache or something like that...  
<strong>\<suraeNoether\></strong> which normally you wouldn't have to worry about for something like SHA256  
<strong>\<suraeNoether\></strong> then the asic is still technically possible, we're just... resistant to it  
<strong>\<suraeNoether\></strong> because it requires novel computer architecture and design  
<strong>\<suraeNoether\></strong> othe i'm very glad to hear you have been working on this  
<strong>\<suraeNoether\></strong> ended the meeting a little too early, sarang. :\\  
<strong>\<sarang\></strong> I'm following along on the bus  
<strong>\<sarang\></strong> The bus smells like ass today  
<strong>\<suraeNoether\></strong> <http://www.cs.cmu.edu/~dga/crypto/cuckoo/analysis.pdf>  
<strong>\<othe\></strong> Well i don't have a problem with asics but sth like shitmain has to be killed of when trying  
<strong>\<suraeNoether\></strong> nope, that's not the paper i was looking at  
<strong>\<suraeNoether\></strong> othe my primary concern is decentralization, whether it's through asic resistance or asic commoditization. the idea of cpu mining is great in some ways, but i like andytoshi's paper on the thermodynamic minimum <em>a whole lot.</em>  
<strong>\<suraeNoether\></strong> like, his paper made me realize that proof-of-storage or something like that? the universal minimum will be determined by the speed of light  
<strong>\<suraeNoether\></strong> so instead of commoditized hardware mining, you would see massive massive data centers all with fiber optic cables of <em>exactly the same length</em> to avoid time effects from light speed, etc etc  
<strong>\<suraeNoether\></strong> so anyway  
<strong>\<unknownids\></strong> this is probably useless info at this point as its all rumors, but <https://rmc.one/> has said they are working on a cryptonight asic  
<strong>\<suraeNoether\></strong> oh yes, that is the paper. :P <http://www.cs.cmu.edu/~dga/crypto/cuckoo/analysis.pdf>  
<strong>\<suraeNoether\></strong> unknownids: eh, the minute they blow a million on taping out a few asics, we'll implement the first of othe's list of changes. :P they'll have to retape, best case scenario... and then we do it again...  
<strong>\<othe\></strong> Rmc one are idiots but rwal companies might be  
<strong>\<suraeNoether\></strong> it's easier for us to change the algo than it is for them to pump out asics  
<strong>\<suraeNoether\></strong> tbh if i were in the asic business i wouldn't make a move without blessings and guidance from the developers of the coin  
<strong>\<unknownids\></strong> good to know othe  
<strong>\<suraeNoether\></strong> because they'll just change their code if they don't like what you are doing  
<strong>\<silur\></strong> ^  
<strong>\<suraeNoether\></strong> whoever is designing asics for monero are preparing to burn their fiat. but hey, they probably have fiat to burn  
<strong>\<suraeNoether\></strong> joker.jpg  
<strong>\<suraeNoether\></strong> ok guys  
<strong>\<suraeNoether\></strong> i'll be back later today  
\*\*\<JollyMort\[m\]\>\*\* entrepreneurs will always find a way to get above others; be it ASIC or botnets or webminers; what's important is that there's no barrier to entry for new players so that nobody's position is forever assured
