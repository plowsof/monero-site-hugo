---
title: Logs for the MRL Meeting Held on 2020-01-15
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<sgp\_\></strong> hello  
<strong>\<almutasim\></strong> Hi.  
<strong>\<ArticMine\></strong> Hi  
<strong>\<koe\></strong> hi  
<strong>\<vtnerd\></strong> hi  
<strong>\<suraeNoether\></strong> Wow what a turnout\!  
<strong>\<atoc\></strong> Hello  
<strong>\<rehrar\></strong> hi  
<strong>\<sarang\></strong> Let’s continue with ROUNDTABLE discussion  
<strong>\<sarang\></strong> suraeNoether: anything of research interest to share?  
<strong>\<ajs\></strong> ajs archived the channel.  
<strong>\<sgp\_\></strong> um… is the channel now gone on Mattermost?  
<strong>\<suraeNoether\></strong> not yet… Right now I’m just copy editing CL sag, working on matching code, and looking into possible speedups for triptych  
<strong>\<ajs\[m\]\></strong> ?  
<strong>\<suraeNoether\></strong> I expect about an hour before clsag is done  
<strong>\<ajs\[m\]\></strong> I thought it was just for me  
<strong>\<atoc\></strong> I noticed it disappeared too.  
<strong>\<sgp\_\></strong> it’s gone  
<strong>\<rehrar\></strong> lol  
<strong>\<rehrar\></strong> give me a sec  
<strong>\<suraeNoether\></strong> Hmm. Who was running it?  
<strong>\<sgp\_\></strong> sorry for derailing, something to fix later  
<strong>\<suraeNoether\></strong> Oh  
<strong>\<suraeNoether\></strong> Moving along :) what about you, Sarang?  
<strong>\<sarang\></strong> Sure  
<strong>\<koe\></strong> for those who want to access logs later: <https://monerologs.net>  
<strong>\<ajs\[m\]\></strong> lol  
<strong>\<sarang\></strong> The Triptych preprint has been updated with new efficiency data and some minor typo corrections (IACR 2020/018)  
<strong>\<sarang\></strong> It will appear on monero-site as MR 1197  
<strong>\<sarang\></strong> The DLSAG paper is being revised for its publication in the FC 2020 proceedings  
<strong>\<sarang\></strong> and we’re working on updating the security model for later journal submission  
<strong>\<sarang\></strong> I have a monero-site MR ready to go for the CLSAG updates (MR 1202) as soon as suraeNoether’s review is complete  
<strong>\<sarang\></strong> (and I get it updated on IACR)  
<strong>\<sarang\></strong> I did some major overhauls on the curve libraries that I use for ed25519 and ed448 testing (for prototyping only; don’t use them in production)  
<strong>\<sarang\></strong> That included porting them to a bunch of other research projects  
<strong>\<sarang\></strong> I also did some updates on my Lelantus code to fix some Fiat-Shamir transcript issues  
<strong>\<sarang\></strong> And that’s about it  
<strong>\<sarang\></strong> Does anyone else have research to share?  
<strong>\<sarang\></strong> We can also have any questions as well  
<strong>\<atoc\></strong> Currently I have been just familiarizing myself with Monero Research  
<strong>\<atoc\></strong> I have read quite a bit of Zero to Monero, and I also looked at the bipartite matching project: <https://github.com/b-g-goodell/mrl-skunkworks/tree/matching-buttercup/Matching>  
<strong>\<atoc\></strong> I did have some questions, but I can go through them later with surae perhaps?  
<strong>\<suraeNoether\></strong> Sure, now is fine with me too  
<strong>\<suraeNoether\></strong> It’s on topic :P  
<strong>\<sarang\></strong> Sure, go ahead  
<strong>\<koe\></strong> speaking of ZtM, thanks to Articmine the dynamic fee section has been greatly elaborated; anyone curious about all the justifications and derivation and analysis can find it in the latest draft; all that remains before I can publish are multisigs, bulletproofs, and proofreading (each of which will take a long time admittedly)  
<strong>\<koe\></strong> <https://www.pdf-archive.com/2020/01/15/zerotomoneroebookmaster-v1-0-17/zerotomoneroebookmaster-v1-0-17.pdf>  
<strong>\<atoc\></strong> Ok cool, well can you briefly give a high level description of this project? From what I understand so far is that this project will be used for user analysis along with statistical models, but hearing an overview from in your words would be nice.  
<strong>\<rehrar\></strong> it’s good to see ZtM getting the update :)  
<strong>\<suraeNoether\></strong> Gotcha okay so first think about the Monero blockchain using two columns. List all of the one-time output keys from coinbases and from other transactions on the left and list all ring signatures or if you like key images on the right-hand column  
<strong>\<suraeNoether\></strong> You can then go and draw edges between one time keys and ring signatures indicating ring membership. So if I publish a ring signature with ring members a b and c, my ring signature on the right would have edges connecting it to the outputs a, b, and c on the left  
<strong>\<suraeNoether\></strong> These are what I call red edges in my code, and I also indicate blue edges connecting ring signatures on the right with the new fresh transaction one time keys that are output from their respective transactions on the left  
<strong>\<sarang\></strong> koe: I asked this before, but how detailed are you looking to get with bulletproofs?  
<strong>\<sarang\></strong> I fear you may end up essentially rewriting their entire paper, with little benefit to the typical reader  
<strong>\<suraeNoether\></strong> So the Monero blockchain can be visualized as this two-colored bipartite graph with one-time keys on the left, ring signatures on the right, red edges indicating ring membership, and blue edges indicating output relationships  
<strong>\<Isthmus\></strong> Hey @koe I owe you an email. I have some protocol notes, but have just been super swamped.  
<strong>\<atoc\></strong> Cool cool, I  
<strong>\<Isthmus\></strong> I’ll try to get the email out in the next few days  
<strong>\<atoc\></strong> I’m with you\*  
<strong>\<scoobybejesus\></strong> i am sort of busy, but wanted to throw out a question (in other words, don’t let this question interrupt the current line of talk). a response anytime would be great, though  
<strong>\<scoobybejesus\></strong> I was thinking about how people complain about outputs getting locked up for 10 blocks. Consequently one must send to themself a multi-out txn to prevent that from happening. What if we made the standard tx 2-in and 3-out (2 change)? And maybe set them to send to different accounts, so they take on independent/divergent decedent txn histories. Was curious if MRL had thoughts/impressions  
<strong>\<Isthmus\></strong> I also got halfway through updating Big Bang paper, but then got distracted. Hoping to finish that this weekend or next.  
<strong>\<suraeNoether\></strong> The ground truth of the situation is that each ring signature has a ring member that is the true signer of the signature, so for every ring signature with a bunch of red edges leading to a bunch of one-time output keys, somebody who’s trying to track transactions is trying to pick the true spender from these red edges  
<strong>\<suraeNoether\></strong> And this is called the matching problem in the graph theory world, sometimes also called the assignment problem, sometimes called the assigned marriage problem lol  
<strong>\<suraeNoether\></strong> So somebody who is trying to track transactions on the Monero blockchain is really trying to find a maximum matching on the Monero blockchain, linking signatures to true spenders  
<strong>\<sgp\_\></strong> scoobybejesus: I’d rather find ways to reduce the lock time  
<strong>\<koe\></strong> no worries Isthmus :); sarang that’s a valid concern and Im really not sure since I don’t actually understand bulletproofs yet; I think if the bulletproofs paper is clear enough it will be fine to point people in that direction; I dislike the idea of leaving things open ended, but maybe it’s just a useless hangup ^.^  
<strong>\<suraeNoether\></strong> The signatures themselves give nothing away about which edge is supposed to be the true spender, so without any additional information the attacker just has to guess, and so every possible maximum matching is equivalently good in this world  
<strong>\<atoc\></strong> Ah okay, I see. It seemed as if you were trying to find out if there was a way to trace back transactions.  
<strong>\<suraeNoether\></strong> I am kinda  
<strong>\<suraeNoether\></strong> So my graph theory python code allows you to build a graph, and then find maximum matchings, and if you wait the edges, it’ll find the heaviest weight matching so that somebody using extra metadata can do better than just guessing at random  
<strong>\<suraeNoether\></strong> Weight\*  
<strong>\<almutasim\></strong> How do you assign weights?  
<strong>\<suraeNoether\></strong> Right so that’s outside of the scope of graph theory and in the scope of my simulations…  
<strong>\<almutasim\></strong> Ah. Are they probabilities?  
<strong>\<atoc\></strong> Is this where statistical models come into play/  
<strong>\<suraeNoether\></strong> Yep. The way that I’m trying to do this is I’m simulating an economy between Alice, Eve and exchange with KYC information, and Bob representing all background players in the Monero economy. I’m even telling Eve the information about the Markov chain from the beginning, which models eves perfect ability to learn your habits.  
<strong>\<suraeNoether\></strong> So this Eve is able to wait the graph using some null hypothesis about user behavior  
<strong>\<suraeNoether\></strong> once she does this, even though she doesn’t know the ground truth reality of the blockchain, she can find a maximum likelihood estimate which corresponds to a maximum weight matching  
<strong>\<sarang\></strong> s/wait/weight/ ?  
<strong>\<suraeNoether\></strong> Weight\* sorry I’m on voice to text  
<strong>\<suraeNoether\></strong> So the simulator simulates an economy, strips information out of the graph that Eve doesn’t know, hands the blockchain to Eve, Eve weights the graph and compute some maximum likelihood estimate, and this maximum likelihood estimate is compared to the simulators ground truth  
<strong>\<suraeNoether\></strong> When things are working I get preliminary data that suggests that Eve is really really bad at this game Even though she’s given perfect information about Alice’s habits  
<strong>\<suraeNoether\></strong> But that’s all preliminary because my code is only intermittently working and I am currently in the midst of refactoring it to be simpler.  
<strong>\<almutasim\></strong> That’s encouraging.  
<strong>\<atoc\></strong> Quite interesting surae. I understood about half of it before, but given you’re description I see the goal of the project now.  
<strong>\<atoc\></strong> Ah I see, was MoneroLink done by the Monero community or third-party?  
<strong>\<surae\></strong>: The fact that it was written by people who had a financial interest in succeeding compared to Monero was viewed as very suspicious by a lot of folks.  
<strong>\<koe\></strong> suraeNoether have you collected a list of tracability analysis papers? for example sarang mentioned a preprint earlier; or maybe Isthmus has that list  
<strong>\<surae\></strong>: Andrew Miller from Zcash and a couple of other folks who were involved with Zcash were authors  
<strong>\<surae\></strong>: Actually you know, Sarang may have a better list than I would… A paper came out last year describing a game not dissimilar from my graph theory game and they named it after sun tzu. But I can be more helpful in finding background papers. Basically any papers on the traceability of anonymous communication networks has some degree of applicability to the Monero blockchain  
<strong>\<surae\></strong>: “perfect matching disclosure attacks” is a general paper that was critical in the construction of the matching stuff  
<strong>\<atoc\></strong> I see I see. So I see a couple of todos listed (unity tests and another). What are some important priorities for this project? I feel I can contribute to this project as a start.  
<strong>\<atoc\></strong> Just a little background about myself: I’m an academic researcher in theoretical computer science (neural algorithms).  
<strong>\<surae\></strong>: Let’s talk about that after the meeting  
<strong>\<atoc\></strong> sure  
<strong>\<Isthmus�\></strong> Dang, I got bumped off IRC  
<strong>\<Isthmus�\></strong> Can’t log back in  
<strong>\<surae\></strong>: speaking of the meeting, isthmus tells me that he has lost access to IRC… And I also happened to lose access to IRC and I’m just using the keybase bridge  
<strong>\<Isthmus�\></strong> \*IRCcloud  
<strong>\<surae\></strong>: it looks to me like IRC cloud has gone down which means the vast majority of the people in this room are probably not here anymore  
<strong>\<Isthmus�\></strong> @atoc nice to meet you, excited to contribute  
<strong>\<Isthmus�\></strong> \*to collaborate  
<strong>\<Isthmus�\></strong> Sorry, I’m in a meatspace meeting too  
<strong>\<surae\></strong>: So we’ll give it a few more minutes and if I receive cloud doesn’t come back or if nobody else speaks up, I say we adjourn the meeting  
<strong>\<surae\></strong>: If irccloud\*  
<strong>\<Isthmus�\></strong> So I just realized that we aren’t fully utilizing the archival network data. But I’ll wait for our IRCcloud comrades to return  
<strong>\<sgp\_\></strong> yes, irccloud seems to be down for everyone  
<strong>\<surae\></strong>: I had a question for isthmus about the archival network and lock times  
<strong>\<Isthmus�\></strong> sup  
<strong>\<surae\></strong>: I want to know the distribution of fork lengths observed so far, and I also want to know the distribution of forklengths experienced by a new node syncing  
<strong>\<atoc\></strong> isthmus nice to meet you as well.  
<strong>\<atoc\></strong> hmm okay and sorry what do you mean fork lengths?  
<strong>\<surae\></strong>: As in Nakamura consensus resolving a fork  
<strong>\<surae\></strong>: Nakamoto  
<strong>\<surae\></strong>: WTF that was autocorrect too not voice to text  
<strong>\<almutasim\></strong> It should be correcting the other way.  
<strong>\<atoc\></strong> I see, alright I will begin looking into this.  
<strong>\<surae\></strong>: Isthmus actually specifically I want an estimate of the parameter r under the null hypothesis that fork lengths are negbinom(p, r)  
<strong>\<surae\></strong>: I think lock time has to be proportional to r to protect most transactions from most rollbacks  
<strong>\<surae\></strong>: Okay since irccloud is now fartcloud, I say this meeting is adjourned.  
<strong>\<koe\></strong> good meeting\! happy day to yall  
<strong>\<surae\></strong>: Good seeing you around koe  
<strong>\<sgp\_\></strong> thanks  
<strong>\<almutasim\></strong> Thanks. Good meeting.
