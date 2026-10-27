---
title: Logs for the Monero Research Lab Meeting Held on 2019-07-22
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> OK, let's get started  
<strong>\<sarang\></strong> GREETINGS  
<strong>\<suraeNoether\></strong> hello fellow not-robots  
<strong>\<sarang\></strong> Let's move on to ROUNDTABLE  
<strong>\<sarang\></strong> suraeNoether: care to begin?  
<strong>\<suraeNoether\></strong> sure  
<strong>\<suraeNoether\></strong> so this weekend i finally posted the konferenco post mortem report, the budget, and markdown'd all the things: <https://www.reddit.com/r/Monero/comments/cfsc2m/suraes\_content\_dump\_konferenco\_post\_morto\_budget/>  
<strong>\<suraeNoether\></strong> this includes my research report for the last quarter and my request for funding for Aug, Sep, Oct.  
<strong>\<suraeNoether\></strong> And isthmus pointed out a property of zcash's shielded pool that i am capable of modeling with my matching simulations, so i've spent a few hours this past weekend trying to get those working (still a wip)  
<strong>\<suraeNoether\></strong> that's all  
<strong>\<suraeNoether\></strong> sarang?  
<strong>\<sarang\></strong> Nice\!  
<strong>\<sarang\></strong> I've posted the handout and some sample code for my upcoming DEF CON workshop  
<strong>\<suraeNoether\></strong> nice\! thatsafineoutreach.gif  
<strong>\<sarang\></strong> (note that you should not use the handout or sample code in production environments, of course... only for playing around)  
<strong>\<sarang\></strong> And I have incomplete work on an RCT3 proof of concept implementation  
<strong>\<sarang\></strong> with some efficiency improvements  
<strong>\<sarang\></strong> the batching opportunities for RCT3 are quite nice  
<strong>\<sarang\></strong> as is the fact that the prover and verifier are relatively straightforward  
<strong>\<sarang\></strong> also also it can take advantage of any existing rangeproof implementation  
<strong>\<sarang\></strong> Any questions on these?  
<strong>\<kenshamir\[m\]\></strong> Hi Sarang, yes  
<strong>\<kenshamir\[m\]\></strong> Do you believe that all of the alternatives; omniring, ringct and lelantus would be a better alternative to the current ringCT even with cLSAG?  
<strong>\<kenshamir\[m\]\></strong> Are you waiting for a feature or an event before choosing a specific alternative?  
<strong>\<kenshamir\[m\]\></strong> better in terms of performance, space savings and anonymity set  
<strong>\<sarang\></strong> In terms of practical anonymity set, the sublinear schemes are an improvement at first glance  
<strong>\<sarang\></strong> but  
<strong>\<sarang\></strong> Lelantus requires a separate output pool and self-spends to avoid tracing  
<strong>\<sarang\></strong> Omniring does not support efficient batching  
<strong>\<sarang\></strong> RCT3 requires a separate output pool  
<strong>\<sarang\></strong> and in all cases, larger anonymity sets require a careful look at handling ring representation, which can become substantial  
<strong>\<kenshamir\[m\]\></strong> Hmm, so is it fair to say that in their infancy, they are not ready to take over the current ringCT?  
<strong>\<sarang\></strong> IMO not without a lot of careful thought on implementation details  
<strong>\<sarang\></strong> That being said, I'm looking at two particular things regarding that:  
<strong>\<kenshamir\[m\]\></strong> Do you think it would be better to move away from hiding users in a set of users, to hiding coins in a set of coins?  
<strong>\<sarang\></strong> One is determining if/how to efficiently split the rangeproof from Omniring for better verification  
<strong>\<kenshamir\[m\]\></strong> Similar to zcash  
<strong>\<sarang\></strong> Two is figuring out if it's possible to use the same key image format with RCT3  
<strong>\<sarang\></strong> Full anonymity would be great if we could do it efficiently  
<strong>\<dEBRUYNE\></strong> And without a trusted setup :P  
<strong>\<kenshamir\[m\]\></strong> \> Two is figuring out if it's possible to use the same key image format with RCT3  
<strong>\<kenshamir\[m\]\></strong> This is very interesting  
<strong>\<suraeNoether\></strong> "Do you think it would be better to move away from hiding users in a set of users, to hiding coins in a set of coins?" \<-- what's the difference?  
<strong>\<suraeNoether\></strong> at a KYC exchange, the exchange knows your personal details and which coins are yours. same same as far as the most common threat model is concerned... unless i'm missing something  
<strong>\<sarang\></strong> Oh I totally missed that distinction in what kenshamir\[m\] said  
<strong>\<sarang\></strong> In all cases, users are used to derive coin data  
<strong>\<sarang\></strong> Anon sets are considered by coins, not by users  
<strong>\<sarang\></strong> Does that answer your question kenshamir\[m\] ?  
<strong>\<kenshamir\[m\]\></strong> Yep, I was re-reading it to make sure I understood  
<strong>\<kenshamir\[m\]\></strong> \<dEBRUYNE "And without a trusted setup :P"\> yes this too :)  
<strong>\<sarang\></strong> This actually leads neatly into my ACTION ITEMS  
<strong>\<sarang\></strong> I'm working on including proper batch verification in the proof of concept code, and integrating into the test transaction flows  
<strong>\<sarang\></strong> Then I want to dive more deeply into the two things I mentioned to kenshamir\[m\]  
<strong>\<sarang\></strong> 1. splitting Omniring proofs for better batching  
<strong>\<sarang\></strong> 2. determining the feasibility/security of retaining key image structure in RCT3 to avoid an output pool split  
<strong>\<sarang\></strong> And finalizing DEF CON material, of course  
<strong>\<sarang\></strong> I'll be giving a talk and leading a workshop in the Monero village, as well as staffing an information table  
<strong>\<sarang\></strong> and also doing a panel discussion in the blockchain village  
<strong>\<sarang\></strong> suraeNoether: your action items?  
<strong>\<suraeNoether\></strong> uhm just working on sims  
<strong>\<suraeNoether\></strong> i want to finish the matching stuff soonish to start answering questions rigorously  
<strong>\<suraeNoether\></strong> and i want to catch up on your work on the Big Three Trustless Protocols, which is what i'm calling them in my head  
<strong>\<sarang\></strong> Yes, IMO the matching stuff is a priority in terms of getting results  
<strong>\<sarang\></strong> Moving back in the agenda slightly, does anyone else have either research to present or general questions to ask?  
<strong>\<kenshamir\[m\]\></strong> What was the matching stuff, you guys are referring to?  
<strong>\<sarang\></strong> Treating possible spend histories in the tx graph as a graph matching problem  
<strong>\<sarang\></strong> and analyzing the structure and complexity  
<strong>\<sarang\></strong> In an ideal tx graph, the number of valid matchings (under any data you might already have) should be very high, to provide useful anonymity  
<strong>\<kenshamir\[m\]\></strong> \<sarang "Treating possible spend historie"\> ohh right, this is very cool research  
<strong>\<sarang\></strong> It's one possible metric to examine anonymity  
<strong>\<sarang\></strong> (but certainly not a complete one)  
<strong>\<kenshamir\[m\]\></strong> right, it would be interesting to see how much certainty you can produce from such a graph in terms of monero  
<strong>\<sarang\></strong> Initial estimates show that it's extremely low  
<strong>\<sarang\></strong> but that assumes no external knowledge  
<strong>\<suraeNoether\></strong> depends on the size, really.  
<strong>\<kenshamir\[m\]\></strong> I don't know much about it, however I am assuming that it can be used to show how certain one can be that two outputs are linked  
<strong>\<suraeNoether\></strong> i mean, a graph where everyone churns 100 times before spending... huge graph... obviously going to have a ton of false results  
<strong>\<sarang\></strong> Right, but if done poorly, you can develop heuristics on partial matchings  
<strong>\<kenshamir\[m\]\></strong> I wonder how external data influences the graph, and what type of external data  
<strong>\<sarang\></strong> That's the big question on this research  
<strong>\<sarang\></strong> Without that, it's purely academic  
<strong>\<kenshamir\[m\]\></strong> As in a real-world scenario, an adversary will have access to external data. I believe the strongest adversary would be an exchange  
<strong>\<kenshamir\[m\]\></strong> oh right  
<strong>\<sarang\></strong> Exchanges, governments, entities with broad access to network data  
<strong>\<sarang\></strong> It's a big part of why these sublinear schemes are so critical in research  
<strong>\<sarang\></strong> At some point, any useful graph data gets lost in the noise of large anon sets  
<strong>\<sarang\></strong> (this does not eliminate all types of analysis, of course)  
<strong>\<kenshamir\[m\]\></strong> So the strongest type of external data, would be to know who owns some percentage of outputs and who they are?  
<strong>\<suraeNoether\></strong> kenshamir\[m\]: that's part of it  
<strong>\<kenshamir\[m\]\></strong> \<sarang "At some point, any useful graph "\> Yep right  
<strong>\<suraeNoether\></strong> kenshamir\[m\]: periodicity can be used to great effect, too  
<strong>\<sarang\></strong> True, timing can play a large role  
<strong>\<sarang\></strong> both in anon set selection and tx operations  
<strong>\<kenshamir\[m\]\></strong> \<suraeNoether "kenshamir: periodicity can be us"\> Could you explain?  
<strong>\<suraeNoether\></strong> IP data from the network when you ctrl-v your txnid into a block explorer without tor immediately after the transaction is relayed  
<strong>\<kenshamir\[m\]\></strong> Is that "I see a payment being sent every monday at 7pm"  
<strong>\<kenshamir\[m\]\></strong> \* Is that "I see a payment being sent every monday at 7pm"?  
<strong>\<suraeNoether\></strong> kenshamir\[m\]: okay well, imagine you are a churner with a superstitious streak and you like to churn every 88 minutes  
<strong>\<suraeNoether\></strong> that chain of churns will stick out like a sore thumb  
<strong>\<sgp\_\></strong> Joining now and caught up, hello everyone. I agree this matching paper is top priority right now  
<strong>\<suraeNoether\></strong> a smart churner selects the age they wait between churns from the wallet distribution. then all the outputs in the ring are drawn from the wallet distribution and no timing data is leaked at all  
<strong>\<kenshamir\[m\]\></strong> Right, that makes sense  
<strong>\<suraeNoether\></strong> but any sort of additional data like IP address or timing can be merged together into a big bayesian updating machine and you can develop pretty good (if probabilistic) behavior profiles of users. and this applies to zcash and monero  
<strong>\<kenshamir\[m\]\></strong> suraeNoether: do you mind going into some detail on how you are simulating?  
<strong>\<sarang\></strong> So right now it's a balance between determining how many times to churn (to diffuse the graph) and how not to do it badly  
<strong>\<sarang\></strong> To do this, we need better data (e.g. matching)  
<strong>\<suraeNoether\></strong> kenshamir\[m\]: sure, let's do it after the meeting though because it's a little involved  
<strong>\<sarang\></strong> OK, any other questions or work to present for this meeting?  
<strong>\<sarang\></strong> going once  
<strong>\<sarang\></strong> twice  
<strong>\<sarang\></strong> OK, we are adjourned\! Thanks to everyone for joining us. Logs will be posted to GitHub shortly
