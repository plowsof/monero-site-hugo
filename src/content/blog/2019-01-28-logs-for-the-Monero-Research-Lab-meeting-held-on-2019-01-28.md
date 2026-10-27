---
title: Logs for the Monero Research Lab Meeting Held on 2019-01-28
summary: Ongoing work, MRL going to SBC, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> allrighty, well, it's 17 UTC  
<strong>\<serhack\></strong> Hi\!  
<strong>\<suraeNoether\></strong> howdy everyone  
<strong>\<ardyfy\></strong> HI  
<strong>\<oneiric\_\></strong> ohiyo  
<strong>\<Xeagu\></strong> Hey  
<strong>\<learninandlurkin\></strong> Salutations  
<strong>\<ArticMine\></strong> hi  
<strong>\<suraeNoether\></strong> today, our agenda is here: <https://github.com/monero-project/meta/issues/302>  
<strong>\<Mochi101\></strong> woohoo\!  
<strong>\<suraeNoether\></strong> allrighty, so let's begin with payment ID deprecation  
<strong>\<Mochi101\></strong> Very sad.  
<strong>\<suraeNoether\></strong> my understanding is that some folks are opposed to the proposed timeline for switching over to subaddresses  
<strong>\<Mochi101\></strong> Don't you guys think that such drastic changes hurts Monero adoption?  
<strong>\<Xeagu\></strong> It is new information to me that this was not already default  
<strong>\<xiphon\></strong> Mochi101: payment id is actually what "hurts Monero adoption"  
<strong>\<xiphon\></strong> ^ standalone one  
<strong>\<suraeNoether\></strong> mochi101 what drastic change are you referring to? deprecating payment IDs? or enforcing subaddresses?  
<strong>\<Mochi101\></strong> Both actually.  
<strong>\<learninandlurkin\></strong> Drastic changes is what Monero is all about. 6 month forks and whatnot.  
<strong>\<ArticMine\></strong> I am in favor of this, the only possible issue I see is timing on which I am neutral  
<strong>\<suraeNoether\></strong> in my opinion, switching to a system with fewer moving parts with fewer ways for users or wallet developers to accidentally screw up, this is a net win for monero users, the ecosystem in general.  
<strong>\<gingeropolous\></strong> ^^  
<strong>\<Mochi101\></strong> Yes, Monero feels like a really high maintenance, needy girlfriend sometimes.  
<strong>\<suraeNoether\></strong> i don't know about you, but "idiot proof" cryptography is sort of a myth, but it'd be really really great if we could take incremental steps toward systems with fewer complications glued on top just to make it work  
<strong>\<Xeagu\></strong> In the unknown future, will Monero no longer require network upgrades every 6 months?  
<strong>\<suraeNoether\></strong> xeagu i believe we are intending on keeping 6 month network upgrade schedules for the foreseeable future, with the intention of \*eventually\* slowing them down  
<strong>\<suraeNoether\></strong> i don't know what timescale "eventually" means here, practically, though. fluffypony has mentioned it before but I don't recall the timescale  
<strong>\<Xeagu\></strong> Do you think a timeline would help those with concerns about that activity hurting adoption?  
<strong>\<learninandlurkin\></strong> The unknown future is unknown  
<strong>\<silur\></strong> I aggree that in the anctient security vs UX war we need to stick with security  
<strong>\<silur\></strong> and moving/changing parts is a golden rule in crypto  
<strong>\<silur\></strong> even if it's more surface for users to screw up  
<strong>\<suraeNoether\></strong> ArticMine: thank you for supporting the change. i'm with you on both timeline and supporting the upgrade. i'm asking if anyone here has specific timeline objections they want to bring up; last I recall, sgp\_ had a great chart, but perhaps the discussions have changed a bit since then?  
<strong>\<dEBRUYNE\></strong> UX issues stemming from payment IDs are predominantly caused by the long, unencrypted payment IDs. Thus, imo, it's imperative that we remove those  
<strong>\<suraeNoether\></strong> ^^  
<strong>\<Mochi101\></strong> As far as I know there's not even any real documentation on subaddress generation, identifying the last index which has been used, etc.  
<strong>\<Mochi101\></strong> That's pretty bad when you're going to force it.  
<strong>\<sgp\_\></strong> Mochi101: <https://github.com/monero-project/meta/issues/299>  
<strong>\<sgp\_\></strong> lots of details there, including a basic upgrade guide for services  
<strong>\<suraeNoether\></strong> thanks for the link to the previous PayID discussion, sgp\_ \! i am bookmarking that rn  
<strong>\<sgp\_\></strong> services have nearly half a year to upgrade, which is reasonable given the requirements. We have spoken to exchanges and payment processor services who think the timeline is aggressive but realistic  
<strong>\<sgp\_\></strong> Mochi101: the logs for the meeting are also available at the same link  
<strong>\<suraeNoether\></strong> sgp\_: cool\! personally, I think this is a win for monero users in terms of privacy, a win for developers in terms of elegance, and a win for the ecosystem in terms of efficiency  
<strong>\<sgp\_\></strong> I recommend you read them  
<strong>\<Xeagu\></strong> I admit I don't understand how subaddresses work  
<strong>\<suraeNoether\></strong> I don't want to speak for sarang; perhaps when he gets back he can jump in and provide an opinion.  
<strong>\<Xeagu\></strong> There is a need in the market for distributed education  
<strong>\<suraeNoether\></strong> Xeagu: the main idea is you take your wallet address (A,B) and you generate a family of addresses deterministically all sharing the same view key, and allowing you to mass-scan all the subaddresses simultaneously for incoming transactions  
<strong>\<suraeNoether\></strong> it's a little more complciated than that because they don't \*actually\* share a view key  
<strong>\<Mochi101\></strong> Thanks. But you're only seeing this from your "in the loop" perspective. I looked for information about this and couldn't find any in the places that I expected them to be. Really people using Monero should not have to search through GitHub to find this stuff. If it's a major issue like this it should be front and center on something like getmonero.org  
<strong>\<suraeNoether\></strong> but they can all be \*scanned\* with a single view key  
<strong>\<Xeagu\></strong> Yes I am confused on the order that subaddresses are selected during generation  
<strong>\<Xeagu\></strong> If they are deterministic, no?  
<strong>\<gingeropolous\></strong> is there anything research-y about payment IDs / encrypted / subaddresses at this point? I mean, its pretty solid that anything except subaddresses is sub-optimal, right?  
<strong>\<suraeNoether\></strong> you use deterministic nonces while hashing, so they appear random but always come up to be the same  
<strong>\<sgp\_\></strong> Xeagu: read this: <https://medium.com/@anhdres/how-moneros-accounts-and-subaddresses-work-in-monerujo-4fa7df0a58e4>  
<strong>\<selsta\></strong> Mochi101: You should subscribe to the newsletter.  
<strong>\<dEBRUYNE\></strong> Mochi101: It was announced on the mailing list  
<strong>\<sgp\_\></strong> Yes, please join that. It's essential for staying up-to-date  
<strong>\<Xeagu\></strong> Alright so basically I need to read through Mastering Monero again  
<strong>\<suraeNoether\></strong> gingeropolous: yeah. this is a question (subaddresses) about key infrastructures. not really in doubt that subaddresses are objectively superior in terms of engineering and in terms of simplicity. keeping around old systems for no good reason is not going to help adoption.  
<strong>\<suraeNoether\></strong> also as far as I understand it, the MRL contributors sgp and knaccc are both working on documentation  
<strong>\<gingeropolous\></strong> right. it just seems at this point we gotta bite the bullet and go through the suck.  
<strong>\<suraeNoether\></strong> we can continue this conversation after the meeting  
<strong>\<Xeagu\></strong> Subaddresses mean you only really need to memorize a single wallet seed, as I understand it.  
<strong>\<sgp\_\></strong> yes Xeagu, and best to table this discussion imo  
<strong>\<Xeagu\></strong> Let's move on  
<strong>\<suraeNoether\></strong> let's move along to the oh-so-contentious block size scaling discussion  
<strong>\<suraeNoether\></strong> articmine is currently validating some cost analyses by sarang  
<strong>\<OWLisFLOWN\></strong> Sup n00bs  
<strong>\<suraeNoether\></strong> i whipped up two ideas, one wacky and one not for block size debate, and i'll be contributing these two ideas to the mix to see about how it all fits together  
<strong>\<suraeNoether\></strong> in terms of cost analyses  
<strong>\<Xeagu\></strong> What are the two ideas?  
<strong>\<ArticMine\></strong> I presented my overall proposal  
<strong>\<suraeNoether\></strong> my first idea is a simple low-pass filter, and my complicated idea is inspired by some discontinuous reset models from neuroscience, which sounds fancy, but is in no way "modeling brains on the blockchain" or anything like that, please do not run away with my words  
<strong>\<suraeNoether\></strong> ArticMine: yeah, i thought you and sarang were working together to make sure cost analyses were apples-to-apples comparisons?  
<strong>\<ArticMine\></strong> <https://paste.debian.net/hidden/556a3a8a/>  
<strong>\<suraeNoether\></strong> aha\!  
<strong>\<suraeNoether\></strong> thanks articmine  
<strong>\<suraeNoether\></strong> that's articmine's proposal  
<strong>\<Xeagu\></strong> Interesting okay. Can you explain the low-pass filter? I'd like to discuss the brains on the blockchain idea later.  
<strong>\<ArticMine\></strong> There was one addition: We can use LongTermBlockWeight as opposed to BlockWeight in the fee calculation  
<strong>\<suraeNoether\></strong> xeagu essentially all our proposals revolve around discrete-time dynamical systems, including my discontinuous reset idea. so "how to update next\_max\_block\_size as a function of previous block sizes... so that the blockchain doesn't get caught in a feedback loop and blow up for a determined and moderately wealthy attacker?"  
<strong>\<Xeagu\></strong> This is trying to determine future dynamic block size scaling?  
<strong>\<suraeNoether\></strong> yep.  
<strong>\<silur\></strong> wait  
<strong>\<silur\></strong> I have a paper on this issue  
<strong>\<suraeNoether\></strong> great\!  
<strong>\<suraeNoether\></strong> please link\!  
<strong>\<silur\></strong> it's originally for PoS  
<strong>\<silur\></strong> but does address the problem  
<strong>\<suraeNoether\></strong> i believe articmine's approach is good in the sense that it forces an attacker attempting to force bloat to drag out an attack over a long timescale in order to have a decent influence, which costs more and more money.  
<strong>\<silur\></strong> of keeping this wealth blowup in check  
<strong>\<silur\></strong> <https://arxiv.org/abs/1809.07468v2>  
<strong>\<suraeNoether\></strong> interesting, thank you. i believe someone had an idea where miners vote on the max block size for the next N blocks using proof of work, but i haven't looked further into it yet  
<strong>\<suraeNoether\></strong> wb sarang  
<strong>\<Xeagu\></strong> I am not familiar with ArticMines proposal  
<strong>\<suraeNoether\></strong> xeagu he linked it a moment ago, and sarang has been running simulations and comparing costs  
<strong>\<silur\></strong> this one has a formula for how to calculate the next reward based on the current parameters  
<strong>\<silur\></strong> maybe we can generalize it for blocksize?  
<strong>\<Xeagu\></strong> I need it in ELI5 terms  
<strong>\<ArticMine\></strong> interesting, thank you. i believe someone had an idea where miners vote on the max block size for the next N blocks using proof of work, but i haven't looked further into it yet\] \<--- This is one of many failed Bitcoin proposals  
<strong>\<moneromooo\></strong> As long as we finalize ArticMine's proposal soon, before the fancy new stuff gets worked on :)  
<strong>\<Xeagu\></strong> How does the dynamic block size change from its current state?  
<strong>\<suraeNoether\></strong> ArticMine: also good to know  
<strong>\<suraeNoether\></strong> xeagu right now  
<strong>\<sarang\></strong> The newer proposals do away with the idea of a single median  
<strong>\<suraeNoether\></strong> we allow next max block size to be 2\*Median(last N blocks)  
<strong>\<suraeNoether\></strong> i forget N  
<strong>\<moneromooo\></strong> Xeagu: <https://paste.debian.net/hidden/556a3a8a/>  
<strong>\<moneromooo\></strong> 100000  
<strong>\<sarang\></strong> Details that have been previously reviewed can probably be discussed more deeply after meeting, IMO  
<strong>\<Xeagu\></strong> moneromooo: that's too high level for me  
<strong>\<moneromooo\></strong> And 1.4 IIRC, not 2.  
<strong>\<Xeagu\></strong> I'll review other notes sure  
<strong>\<suraeNoether\></strong> moneromooo: oh\! that's good :D  
<strong>\<suraeNoether\></strong> xeagu i'll get you after the meeting  
<strong>\<sarang\></strong> atm, I am waiting to see what cost details are added by ArticMine to ensure we understand the relative cost of bloat under the different options  
<strong>\<Xeagu\></strong> Okay  
<strong>\<suraeNoether\></strong> basically: block size scaling is still under discussion, we are working on formalizing articmine's proposal and comparing it to our present proposal as well as at least one other proposal.  
<strong>\<suraeNoether\></strong> and i think sarang and i can collaborate on a technical note describing all this  
<strong>\<suraeNoether\></strong> moving along to MRL 11's status update: MRL 11 is essentially about traceability and linkability in Monero, and comparing techniques across multiple blockchains like Zcash + Monero together  
<strong>\<suraeNoether\></strong> if you guys have seen matthew green and binaryfate and fluffypony sparring on twitter about ring sizes compared to the shielded pool in zcash  
<strong>\<suraeNoether\></strong> this is that  
<strong>\<Xeagu\></strong> Zcash doesn't scale  
<strong>\<silur\></strong> ah :D  
<strong>\<suraeNoether\></strong> the current status is that sarang passed it back to me more than a week ago, and i've been tinkering with simulations  
<strong>\<ArticMine\></strong> My proposal uses the current 2x maximum for the short term median and 1.4x for the long term median  
<strong>\<Xeagu\></strong> You can't let every transaction be shielded without huge data storage  
<strong>\<suraeNoether\></strong> i want to simulate something like the following, and it's quite challenging to formalize this (i'm bringing my hangup to the crowd so you guys know what i'm stuck on)... I want to create a formal statistical hypothesis, and it's eluding me...  
<strong>\<suraeNoether\></strong> essentially, i want to capture the EABE scenario that started this whole paper last year  
<strong>\<suraeNoether\></strong> and churn  
<strong>\<Xeagu\></strong> EABE scenario?  
<strong>\<sarang\></strong> Poisoned outputs  
<strong>\<Xeagu\></strong> Oh got it  
<strong>\<suraeNoether\></strong> I want to generate a random blockchain (somehow) and embed within it the spending behavior masking "churn" between receiving a possibly "marked note" and then later trying to cash it out at a KYC/AML exchange  
<strong>\<suraeNoether\></strong> then i want to apply our matching technique to see the probability that this behavior is caught, if someone is looking for it  
<strong>\<Xeagu\></strong> But as I understand if you just show view key, the exchange will accept it  
<strong>\<suraeNoether\></strong> xeagu that's the final vertex in the transaction graph  
<strong>\<suraeNoether\></strong> there may be many intermediate vertices as you churn  
<strong>\<suraeNoether\></strong> most importantly, we need somehow to gauge the entire confusion table; false positives, false negatives, true positives, and true negatives  
<strong>\<Xeagu\></strong> Like how far back do exchanges care about poisoned outputs?  
<strong>\<sarang\></strong> unknown  
<strong>\<suraeNoether\></strong> and i can do this \*under certain hypotheses\* but i can't do it in general. all i really i want is a practical comparison of our technique to a real world scenario like a miner trying to hide that he's depositing a mined coin on an exchange  
<strong>\<sarang\></strong> You should conservatively assume "all the way back"  
<strong>\<sarang\></strong> Anyway, feels like we're getting off topic somewhat  
<strong>\<Xeagu\></strong> Was regarding MRL 11  
<strong>\<Xeagu\></strong> Traceability comparison  
<strong>\<suraeNoether\></strong> so, to summarize MRL 11: we have an algorithm, we have timing estimates, we are working on simulations and comparisons of our technique across multiple blockchains at once, and we are basically gearing up to figure out how many churns is enough... or... alternatively... we are gearing up to figure out how to show the depth of the wastefulness of having a massive anonymity set like the whole zcash shielded  
<strong>\<suraeNoether\></strong> pool  
<strong>\<suraeNoether\></strong> sarang: think that was an okay summary? i don't want to speak for you  
<strong>\<sarang\></strong> Yes, the computational bounds are the most interesting part IMO  
<strong>\<suraeNoether\></strong> yeah, same actually  
<strong>\<sarang\></strong> they set a framework for analyzing certain behavior  
<strong>\<suraeNoether\></strong> the interesting thing to me is we were able to put lower bounds on how fast an attacker can generate a "guess" at a possible spend history  
<strong>\<suraeNoether\></strong> bad news: it's pretty fast. good news: there are lots and lots of possible spend histories, like cryptographically many  
<strong>\<suraeNoether\></strong> how much is the practical security compared to a zk-snark scenario? we'll find out  
<strong>\<sarang\></strong> So you earlier discussed block size scaling (waiting on cost analysis)... did I also miss anything on output selection?  
<strong>\<suraeNoether\></strong> spoiler: if both blockchains exist together at the same time, one with an opt-out transparent pool and both with users interacting at KYC/AML exchanges... then security on both are wildly compromised  
<strong>\<suraeNoether\></strong> sarang eek I forgot to add output selection to the agenda, that's my bad  
<strong>\<sarang\></strong> OK, is now a good time for this?  
<strong>\<suraeNoether\></strong> perfect time actually  
<strong>\<sarang\></strong> Great  
<strong>\<Xeagu\></strong> It's not on the agenda but I wanted to make sure we discussed the rumor of ASIC/FPGAS on the network.  
<strong>\<sarang\></strong> moneromooo had asked me earlier about reviewing our windowing approach to gamma selection  
<strong>\<sarang\></strong> He had an idea about further weighting selection probability of a block based on output count  
<strong>\<sarang\></strong> with a possible goal of reducing the coinbase-to-non-coinbase ratio in rings to that of the whole chain  
<strong>\<suraeNoether\></strong> xeagu we'll get to that in a sec, thanks for reminding me :\\  
<strong>\<sarang\></strong> e.g. 6-10% of outputs are coinbase, so 6-10% of a ring should be as well  
<strong>\<sarang\></strong> moneromooo can explain it better, but the idea would be to take the gamma probability of block selection and further weight by the block's output count, and then uniformly select within that block  
<strong>\<sarang\></strong> I'm working up some code based on chain stats  
<strong>\<sarang\></strong> but I'll put it out there for comment  
<strong>\<suraeNoether\></strong> sarang \#actually  
<strong>\<suraeNoether\></strong> the distribution in the ring should be "whatever the probability that the next transaction is a coinbase output."  
<strong>\<Xeagu\></strong> I think miners churning newly mined coins would help against poisoned outputs  
<strong>\<suraeNoether\></strong> so if miners typically hodl for long long long times, then mimicing the distribution of the outputs that care coinbases will drastically over-sample the coinbase outputs.  
<strong>\<suraeNoether\></strong> xeagu i agree  
<strong>\<gingeropolous\></strong> \<sarang\> e.g. 6-10% of outputs are coinbase, so 6-10% of a ring should be as well \>\>\>\>\> but 99% of coinbase outputs are owned by about 15 people  
<strong>\<suraeNoether\></strong> i think a lot of miners churn in order to mask that they are mining  
<strong>\<suraeNoether\></strong> gingeropolous: exactly\!  
<strong>\<sarang\></strong> I know, but we have no good metric for "how many coinbase in a ring is ok"  
<strong>\<suraeNoether\></strong> unfortunately we don't really have a way of estimating how often any given subsets of our blockchain are spent  
<strong>\<sarang\></strong> Currently it's 1-3 outputs per ring on average that are coinbase  
<strong>\<moneromooo\></strong> The idea I had is meant to (I think) make the selection process match the gamma from an ideal blockchain (ideal being, every block has the same number of outputs).  
<strong>\<moneromooo\></strong> And indeed, in that particular case, the two distributions match.  
<strong>\<moneromooo\></strong> The idea has two steps:  
<strong>\<sarang\></strong> Nice, did you run sims?  
<strong>\<moneromooo\></strong> - for each block, calculate its probability of being picked by the gamma distribution pick  
<strong>\<moneromooo\></strong> - for each block, multiply that number by the number of outputs in that block  
<strong>\<moneromooo\></strong> Then you just pick a random block from those weights using a discrete distribution.  
<strong>\<moneromooo\></strong> I did not run sims, because I do not know how to calculate the first step.  
<strong>\<suraeNoether\></strong> MOO  
<strong>\<suraeNoether\></strong> you brilliant bastard  
<strong>\<suraeNoether\></strong> you want to know why that works?  
<strong>\<sarang\></strong> moneromooo had pointed out earlier that this also solves the issue of a fixed window size  
<strong>\<moneromooo\></strong> Well, I see how it'd work by, er... intuition really. Why does it work ?  
<strong>\<suraeNoether\></strong> you are estimating an empirical distribution: when you multiply that number by the number of outputs in the block, you are computing the expected number of outputs to be selected from that block. then you built a histogram and selected from that\!  
<strong>\<sarang\></strong> Yeah  
<strong>\<suraeNoether\></strong> it's cool  
<strong>\<suraeNoether\></strong> expectation as a linear operator  
<strong>\<suraeNoether\></strong> fun stuff  
<strong>\<suraeNoether\></strong> \*ahem\*  
<strong>\<sarang\></strong> the scaling of coinbase outputs in this case is also independent of the gamma distribution, which I find neat  
<strong>\<suraeNoether\></strong> very frequentist. hem hem  
<strong>\<suraeNoether\></strong> yeah, you could use this with any underlying hypothetical distribution  
<strong>\<sarang\></strong> I'm confirming that it does so, and writing up some sims to convince myself of it  
<strong>\<suraeNoether\></strong> \\me eats oatmeal  
<strong>\<sarang\></strong> kudos moneromooo, it's a clever approach that fixes the issues with windowing  
<strong>\<gingeropolous\></strong> so there's still a probability that multiple coinbases will be selected, but because tiny blocks have low probability, we should expect less outputs selected from tiny blocks?  
<strong>\<suraeNoether\></strong> it actually fixes several other things i'd been thinking about  
<strong>\<suraeNoether\></strong> it's a great framework.  
<strong>\<moneromooo\></strong> Thanks. Still needs a way to compute the first number. I fear it might involve integrals.  
<strong>\<Xeagu\></strong> I don't understand :/  
<strong>\<sarang\></strong> moneromooo: probably not =p  
<strong>\<suraeNoether\></strong> gingeropolous: yeah, exactly. each output has a gamma age, and then you select from all outputs. rather than selecting an output age from a gamma and then selecting from all the outs with that age. subtle flipping of the order of things  
<strong>\<sarang\></strong> I believe it should reduce the ring ratio to that of the whole chain  
<strong>\<Xeagu\></strong> I don't know what gamma means  
<strong>\<sgp\_\></strong> In the most extreme case, we can say 0 coinbase are necessary and force independent miners to churn their received funds if they care. Pools don't care and are the main cause of this debate. But there doesn't seem to be enough support for this, and it comes with other tradeoffs. I just think it's important to keep mentioning  
<strong>\<moneromooo\></strong> A particular random distribution.  
<strong>\<sarang\></strong> the way we select ring members using math Xeagu  
<strong>\<gingeropolous\></strong> Xeagu, you can think of gamma as a droopy triangle  
<strong>\<suraeNoether\></strong> xeagu there is a long statistical background on the gamma distribution. we'll catch you up after the meeting  
<strong>\<gingeropolous\></strong> right triangle, 90 degrees on the right side. the hypotenuse is the droopy side  
<strong>\<sarang\></strong> sgp\_: we can enforce coinbase-only rings as a first churn, but that doesn't solve the heuristic of "coinbase are bad"  
<strong>\<sarang\></strong> it just moves it along the transaction graph a teeny bit  
<strong>\<sarang\></strong> so I feel ya  
<strong>\<suraeNoether\></strong> you flip a coin until you get a heads up and right down the number of flips. then you do that 10 times. then you add those wait-times-until-heads-up together  
<strong>\<sgp\_\></strong> sarang: this would just accept "coinbases are bad" and not touch them whenever possible  
<strong>\<Xeagu\></strong> So if gamma is a process (verb) how is it acting as an adjective modifying a noun (age)?  
<strong>\<gingeropolous\></strong> i dunno what parameters we use, but <https://en.wikipedia.org/wiki/Gamma\_distribution#/media/File:Gamma\_distribution\_pdf.svg>  
<strong>\<gingeropolous\></strong> i'd guess we look like the red line  
<strong>\<suraeNoether\></strong> and then you ask "what is the probability that i got wait times of 3, 2, 0, 1, 1, 0, 1, 2, 1, 0?" that's essentially a gamma distribution  
<strong>\<gingeropolous\></strong> Xeagu,  
<strong>\<sarang\></strong> The heuristic would move from "coinbase in a ring are decoys" to "outputs generated in a coinbase-only ring are decoys"  
<strong>\<suraeNoether\></strong> sarang i'm not sure i follow that  
<strong>\<sarang\></strong> unless you convince miners to churn more out of the goodness of their pooled hearts  
<strong>\<suraeNoether\></strong> oh i think i follow you  
<strong>\<sarang\></strong> Right now you might throw out all coinbase ring members as decoys  
<strong>\<sarang\></strong> Now you look back one step, and throw out an output generated from an obvious coinbase churn  
<strong>\<sarang\></strong> You gain very little from this  
<strong>\<suraeNoether\></strong> yeah, i think i follow yoiu  
<strong>\<sarang\></strong> So I like the idea of shooting for a ring member ratio matching the chain  
<strong>\<sarang\></strong> and this weighted approach should do that for us  
<strong>\<sarang\></strong> to be confirmed by sanity-check sims\!  
<strong>\<suraeNoether\></strong> okay, so the output selection method proposed by moneromooo is actually a really clever way of computing expectations, and as a consequence, gives us a better output selection method. we should glance through the code, but i'm happy with that  
<strong>\<suraeNoether\></strong> FPGA/ASIC stuff  
<strong>\<sarang\></strong> Neat  
<strong>\<suraeNoether\></strong> let's move along  
<strong>\<suraeNoether\></strong> i hear some nonce distributions are non-uniform  
<strong>\<sarang\></strong> and they recently changed as of the new year-ish  
<strong>\<suraeNoether\></strong> fun  
<strong>\<suraeNoether\></strong> so, i'm not really prepared to talk about monero POW and asic-resistance right now, tbqh  
<strong>\<suraeNoether\></strong> i happened upon some reading this weekend on sponge constructions, so i'm currently on the path toward learning more about hash functions and pseudorandom functions  
<strong>\<suraeNoether\></strong> but i don't have any thoughts i want to make public right now  
<strong>\<suraeNoether\></strong> sarang?  
<strong>\<suraeNoether\></strong> (i'm not keeping anything from anyone either, I harbor no secret opinions on this either)  
<strong>\<sarang\></strong> I have been working on sims relating to output selection and block size, and continue side work on bulletproofs MPC and related things  
<strong>\<sarang\></strong> I'll be attending the Stanford academic crypto conference this week  
<strong>\<suraeNoether\></strong> Yeah, sarang and endogenic and i and isthmus will all be there  
<strong>\<silur\></strong> \*not envy\*  
<strong>\<suraeNoether\></strong> CONVENIENTLY i found my LAST FOUR MRL shirts, so you know  
<strong>\<suraeNoether\></strong> i'll be forcing everyone to wear them for a photo  
<strong>\<sarang\></strong> Does anyone else have work to share before we review action items?  
<strong>\<Xeagu\></strong> I have to go  
<strong>\<suraeNoether\></strong> i have been doing some reading on alternatives to ring signatures  
<strong>\<Xeagu\></strong> Great meeting everyone  
<strong>\<suraeNoether\></strong> i plan on writing up a technical note summarizing different options in different cryptographic hardness settings, timing and space comparisons  
<strong>\<learninandlurkin\></strong> Alternatives without huge resource drain?  
<strong>\<suraeNoether\></strong> learninandlurkin: so, some of that is tricky  
<strong>\<sarang\></strong> that's always the kicker  
<strong>\<suraeNoether\></strong> for example, i came across some short-integer-solution methods with lattices that are FAST AS HECK but HUGE  
<strong>\<silur\></strong> oh yes  
<strong>\<suraeNoether\></strong> the tradeoff isn't there yet, but it's worth summarizing it all  
<strong>\<silur\></strong> my favorites  
<strong>\<silur\></strong> they are also good for accumulators  
<strong>\<silur\></strong> I have some demos on that  
<strong>\<silur\></strong> been working with SIS for long  
<strong>\<suraeNoether\></strong> silur ooh, i'd love to see a link of some sort  
<strong>\<silur\></strong> I've got really into noncommutative crypto recently  
<strong>\<suraeNoether\></strong> so i'll be summarizing i think four papers in the coming days, to communicate some of the options we have to the community  
<strong>\<silur\></strong> it feels like a graveyard because except for the primitives everything is broken  
<strong>\<sarang\></strong> Action items for this week?  
<strong>\<silur\></strong> but I asessed all attacks and stuff that are still holding in the recent months  
<strong>\<silur\></strong> main focus on zk stuff now  
<strong>\<sarang\></strong> I am looking forward to ArticMine's sim code updates to reflect rational miner costs, which will allow us to assess our options for next upgrade  
<strong>\<suraeNoether\></strong> my action items are: matching simulations and hypothesis testing, and my alternatives-to-ring-signatures-aren't-much-better technical note  
<strong>\<learninandlurkin\></strong> I'll look forward to that suraeNoether. With ringsigs being our main weakness and also the main missing component of Grin (as compared to XMR) I think this are of research will have big implications.  
<strong>\<silur\></strong> ringsigs are our main weakness?  
<strong>\<silur\></strong> what happenned with RTRS?  
<strong>\<sarang\></strong> It remains an option, but one that requires a lot of overhauling for still being ring sigs :.  
<strong>\<sarang\></strong> :/  
<strong>\<suraeNoether\></strong> silur: sarang has gotten them to be suitably fast with multiexponentiation so that we could, say, use ring sizes up to, say, 20-30. however, there are some other sublinear schemes that are available, each with their own trade-offs, which is why i'm writing my paper  
<strong>\<silur\></strong> wow  
<strong>\<suraeNoether\></strong> i was hoping that once we broke a certain speed barrier, the path forward would be a no-brainer  
<strong>\<silur\></strong> okay, I'll be waiting for it  
<strong>\<silur\></strong> the paper I mean  
<strong>\<suraeNoether\></strong> but we have certain issues we're dealing with and it's not totally clear whether overhauling the system for such a small ring size boost would be worth it if there could be another option with a relatively bigger boost eventually  
<strong>\<sarang\></strong> well said  
<strong>\<suraeNoether\></strong> replace that last word "eventually" with "presently"  
<strong>\<suraeNoether\></strong> cool, /meeting
