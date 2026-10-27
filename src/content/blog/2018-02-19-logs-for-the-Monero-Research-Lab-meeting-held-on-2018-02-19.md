---
title: Logs for the Monero Research Lab Meeting Held on 2018-02-19
summary: Multisig (paper), chain split (e.g. MoneroV), anonymity set, auditing options, and miscellaneous
tags: [dev diaries, crypto, research]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<suraeNoether\></strong> allrighty, howdy everyone  
<strong>\<suraeNoether\></strong> topic Research meeting now  
<strong>\<suraeNoether\></strong> awww  
<strong>\<sarang\></strong> hullo  
<strong>\<rehrar\></strong> yeah\!  
<strong>\<suraeNoether\></strong> so  
<strong>\<sarang\></strong> indeed  
<strong>\<suraeNoether\></strong> before we get going, does anyone have any questions?  
<strong>\<rehrar\></strong> pertaining to?  
<strong>\<suraeNoether\></strong> anything, really. :P  
<strong>\<rehrar\></strong> Are pancakes better with or without chocolate chips?  
<strong>\<sarang\></strong> Well, I see the two big topics right now are output identification (a la MoneroV) and PoW change  
<strong>\<sarang\></strong> at least for immediacy  
<strong>\<rehrar\></strong> <em>shuts up to let smart people talk</em>  
<strong>\<suraeNoether\></strong> oh, i think blueberries are better  
<strong>\<suraeNoether\></strong> but that’s none of my business  
<strong>\<suraeNoether\></strong> yeah, i imagine at least some people have questions about how to keep their outputs safe with MoneroV and our PoW change discussion  
<strong>\<sarang\></strong> I think a related question that’s valid is “what do we plan to do about this?”  
<strong>\<suraeNoether\></strong> but we can maybe hold that until the end of the discussion: basically, “what i’ve done this week” has been multisig. i have the paper down to low 20s pages, and i have one security proof left to complete, and i need to clean up the appendix describing our code.  
<strong>\<suraeNoether\></strong> sarang before we move onto the more obvious stuff, want to give us a brief review of your week?  
<strong>\<sarang\></strong> Sure, some course planning for the summer, reviewing SoWs and discussing with Benedikt, some paper reading  
<strong>\<rehrar\></strong> Sorry, couple questions on multisig paper. 1. ETA? 2. Submit for peer review?  
<strong>\<sarang\></strong> A lighter week than last  
<strong>\<sarang\></strong> Oh, and writing up a talk on privacy coins for next month  
<strong>\<sarang\></strong> (due this week)  
<strong>\<suraeNoether\></strong> 1) ETA … i am hoping to finish it today. so quadruple that and maybe i’ll be 10% correct. :P  
<strong>\<suraeNoether\></strong> we are definitely submitting it for peer review  
<strong>\<rehrar\></strong> Nice\! It will be ‘White’ no more  
<strong>\<suraeNoether\></strong> i’m so close to finishign this thing, i’m hoping for mid-week to release the whitepaper version of it to the community and upload it (perhaps) to arxiv or something, after i get a brief review by sarang  
<strong>\<sarang\></strong> Yeah, BPASE work threw a temporary wrench at it  
<strong>\<suraeNoether\></strong> does anyone want to describe their work this week? I know chachasmooth has been learning about elliptic curves  
<strong>\<sarang\></strong> but that’s the nature of research  
<strong>\<sarang\></strong> Well I am finalizing my privacy talk, which focuses on some definitions of privacy and compares privacy techologies used in coins today  
<strong>\<sarang\></strong> It focuses heavily on Monero but tries to do a fair assessment of the playing field  
<strong>\<suraeNoether\></strong> nice, i want to actually talk about a simplification of the EABE attack that is concerning to me  
<strong>\<sarang\></strong> I was also asked to lead a one-day short course on data analysis at the SciPy conference this year, so I’m using blockchain data as the project  
<strong>\<sarang\></strong> Some good PR and hopefully some interesting analysis we hadn’t thought of before  
<strong>\<sarang\></strong> Anyway, go ahead suraeNoether  
<strong>\<suraeNoether\></strong> I’m thinking perhaps we need to put out a statement, because there is at least one very common scenario in which people think Monero is protecting them with signer ambiguity, but it really isn’t  
<strong>\<suraeNoether\></strong> and it’s the EAE attack, actually, where someone buying something from you is colluding with a KYC exchange  
<strong>\<suraeNoether\></strong> in this case, it should be obvious: Alice is surrounded by the KYC exchange, who knows her personal identity, address, etc, and also knows the one-time destination keys being used by Alice for these purchases they are making from you  
<strong>\<suraeNoether\></strong> once the KYC exchange has collected a sample size of deposits from Alice, that KYC exchange can look into the history of these deposits and identify one-time keys that were flagged from earlier.  
<strong>\<sarang\></strong> right  
<strong>\<suraeNoether\></strong> unless alice makes an extremely expensive churn, the appearance of these flagged outputs will occur in the history of these deposits more often than chance would dictate if the ring signatures were being randomly created by other users  
<strong>\<suraeNoether\></strong> there isn’t a quick and easy solution to this, and users who are very concerned about their privacy should not send their monero to KYC exchanges  
<strong>\<sarang\></strong> I think it brings us back to the nature of ring signatures in general  
<strong>\<sarang\></strong> They’re to offer plausible deniability  
<strong>\<sarang\></strong> but statistics will always be a problem unless ring sizes are very large  
<strong>\<suraeNoether\></strong> yes. it’s objectively better than using something like bitcoin due to plausible deniability, but it’s still concerning  
<strong>\<rehrar\></strong> does this potentially point to, somewhere down the line in the future, moving to a more bullet proof (pardon the pun) scheme?  
<strong>\<sarang\></strong> I think it has to  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<sarang\></strong> Full anonymity set is the only guaranteed way to thwart statistical analysis  
<strong>\<sarang\></strong> This, the MoneroV thing, they all tie in to ring intersections and statistics  
<strong>\<rehrar\></strong> does STARKS also have full anonymity set?  
<strong>\<suraeNoether\></strong> one of the things fluffypony asked me to look into when i first began this was looking into things like zk-snark sidechains, so we have been considering this for awhile  
<strong>\<suraeNoether\></strong> they allegedly do, yes  
<strong>\<andytoshi\></strong> rehrar: STARKs is just a tech  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> ?  
<strong>\<andytoshi\></strong> it’s for zero knowledge proofs  
<strong>\<sarang\></strong> The goal is just to prove the output is valid  
<strong>\<andytoshi\></strong> “full anonymity set” applies to some specific system  
<strong>\<sarang\></strong> right  
<strong>\<rehrar\></strong> ah, apologies  
<strong>\<suraeNoether\></strong> yeah, the implicit quesiton is “would we be using starks to implement a full anon set”  
<strong>\<andytoshi\></strong> the answer to that is no, it’s not feasible. bulletproofs would be faster for that  
<strong>\<andytoshi\></strong> and smaller  
<strong>\<andytoshi\></strong> and BPs aren’t quite there i think  
<strong>\<sarang\></strong> I mean, this problem isn’t limited to us  
<strong>\<suraeNoether\></strong> starks is new, but so are BPs. i think BPs will allow us to get some impressively large anonymity sets  
<strong>\<sarang\></strong> There is not a good, efficient way to handle it… zcash has the same problem with different sacrifices  
<strong>\<andytoshi\></strong> yeah..pretty sure BPs have a faster prover than SNARKs  
<strong>\<suraeNoether\></strong> sarang ^ this is also correct, most users who use zcash make transactions they wish to be kept private as a z-transaction, but they end up depositing to KYC exchanges as t-transactions  
<strong>\<rehrar\></strong> so the answer is almost a social one, wherein people don’t need to trade to KYC exchange, because they can purchase whatever they want in Monero  
<strong>\<rehrar\></strong> \*one of the answers  
<strong>\<suraeNoether\></strong> so, this is an <em>open problem</em> in some senses, but my point is this: the current wisdom about best practices is to churn a lot and you’re good. but that’s not the case without impractically large churns, and the best practice is merely to avoid KYC exchanges  
<strong>\<andytoshi\></strong> KYC has nothing to do with whether you publish your transaction data on a blockchain, think exchanges are just too lazy to implement z-transaction support  
<strong>\<sarang\></strong> Part of the social problem is an identification of what exactly you’re trying to accomplish with hiding transactions  
<strong>\<sarang\></strong> At what point does “plausible deniability” fall apart in the face of ring statistics?  
<strong>\<suraeNoether\></strong> in general, if a business is a KYC business (say a local coffee shop who happens to know you), you still have a similar problem while using Monero. really the best advice is: if you like your privacy in Monero, don’t send Monero to people who know your name  
<strong>\<sarang\></strong> that’s not clear  
<strong>\<suraeNoether\></strong> sarang with a sufficiently large sample size, after the “attacker” has made a sufficiently large number of controlled purchass  
<strong>\<rehrar\></strong> I guess it may be more of a economics question, but is plausible deniability enough for fungibility than absolute anonymity? Because to answer sarang’s question: for the common folk, fungibility would be what they’re after  
<strong>\<suraeNoether\></strong> purchass = purchases, but purchass sounds like a really great stripper name  
<strong>\<sarang\></strong> rehrar: sure, but an exchange or police or whatever can decide when their analysis reveals a “probably bad” output  
<strong>\<rehrar\></strong> even if they don’t know the word fungiblity :P No merchant or individual wants to go through the headache of checking each received coin for ‘taintedness’  
<strong>\<sarang\></strong> it’s the same issue with burden of proof in the court system, IMHO  
<strong>\<suraeNoether\></strong> rehrar: I believe plausible deniability with a large enough scope is fine.  
<strong>\<sarang\></strong> Right, but there is not a definition of “large enough”  
<strong>\<sarang\></strong> depends on the context  
<strong>\<sarang\></strong> nor is there a good definition of “plausible deniability”  
<strong>\<gsee\></strong> When Fluffy spoke at Coinbase, he suggested that maybe they would be more comfortable listing monero and meeting their KYC/AML requirements if they required users to provide their view keys. Would that damage privacy of others?  
<strong>\<suraeNoether\></strong> gsee not at all, and in fact that’s what the view key is sort of for  
<strong>\<gsee\></strong> what if they also required users to provide key images so to prove a wallet balance?  
<strong>\<suraeNoether\></strong> that would have pretty nasty consequences: coinbase would have a list of proven-spent transactions, reducing the effective ring sizes of all outputs  
<strong>\<rehrar\></strong> What would it take to get some good research done on ‘large enough’ and ‘plausible deniability’ definitions, or at least try to get ballpark stuff?  
<strong>\<rehrar\></strong> I think that’s some pretty important stuff to be able to define within reason  
<strong>\<suraeNoether\></strong> well, my working definition of “large enough” works like this  
<strong>\<gsee\></strong> thanks suraeNoether, that’s what I was thinking. Just wanted to doublecheck.  
<strong>\<suraeNoether\></strong> let’s say you churn N times with ring size R  
<strong>\<gsee\></strong> On a similar note, I have to prove our balances to auditors once a year. Showing them view keys and key images might be a bad idea then.  
<strong>\<suraeNoether\></strong> this means you have R^(N-1) independent ring signatures, each with R members. and the question is: if Eve knows Alice has A different outputs on the whole blockchain, whcih has B outputs, and if all outputs are selected for ring signatures at uniform randomly, <em>how likely is it that we see one of Alice’s suspicious one-time keys appear in one of these R^(N-1) ring signatures?</em>  
<strong>\<suraeNoether\></strong> how hard is it to <em>look like a random sequence of transactions?</em>  
<strong>\<suraeNoether\></strong> anyway rehrar, i’ve been looking into it for awhile  
<strong>\<suraeNoether\></strong> but for now i think we need to put out a statement that monero user keys interested in privacy should not be shared with a KYC exchange in any way  
<strong>\<rehrar\></strong> logistics question for me, the website guy: Do we want to put this and any future bulletins under the MRL page on the website?  
<strong>\<rehrar\></strong> Or just the repo is good enough with a link to it?  
<strong>\<scoobybejesus\></strong> When is it time for MoneroV talk? I have a question. Sort of a two-parter.  
<strong>\<sarang\></strong> Well, MoneroV is related  
<strong>\<suraeNoether\></strong> essentially, if we want like… concrete cryptographic security, we would need to churn… a lot  
<strong>\<scoobybejesus\></strong> Question: MoneroV key images. Let’s say the MoneroV team chooses to acquiesce and change their key image by hashing another parameter (or something)…  
<strong>\<scoobybejesus\></strong> If their key images are a Monero-key-image-hashed-with-something-else, does that mean there is no way (discrete log-wise) to “tie” pre-fork Monero key images to their respective key images in MoneroV?  
<strong>\<scoobybejesus\></strong> Or - maybe a better way to ask - is there even a way to take an existing Monero key image, do something to it, have it be useful on the MoneroV chain as double-spend prevention, while still not being “tied” to the Monero key image from whence it came?  
<strong>\<suraeNoether\></strong> rehrar I’m unsure on that  
<strong>\<suraeNoether\></strong> scoobybejesus: we thought at first monerov could compute key images differently, but the algebra doesn’t appear to work out without allowing double spends  
<strong>\<suraeNoether\></strong> without some sort of wizardry anyway  
<strong>\<sarang\></strong> Well with a hash scheme there would be no way to link them, no  
<strong>\<sarang\></strong> But ^ to what suraeNoether sez  
<strong>\<suraeNoether\></strong> the only way i know of to safely claim your monerov is to try to fashion the same ring on both chains  
<strong>\<suraeNoether\></strong> hmm, what about doubly hashing the point P?  
<strong>\<suraeNoether\></strong> nope, still have the double spend problem  
<strong>\<sarang\></strong> yup  
<strong>\<sgp\></strong> ^ assuming no chain reactions  
<strong>\<andytoshi\></strong> you can hash every known key image with a per-chain salt, then require users reveal only the hashed key image for future spends (and BP that they hashed the key image correctly)  
<strong>\<andytoshi\></strong> but that’s waay more work than we can expect scammers to do  
<strong>\<suraeNoether\></strong> oh yeah, i suppose you are also assuming your fellow ring members are also computing identical rings on both chains  
<strong>\<sarang\></strong> oh andytoshi so you mean go back and retroactively update the used image list?  
<strong>\<sarang\></strong> interesting  
<strong>\<suraeNoether\></strong> andytoshi i almost feel like we should make it an easy to use utility so we can point to unsafe projects and say “how come they aren’t using our safe-to-use BP utility to ensure they don’t shit in the punchbowl”?  
<strong>\<sarang\></strong> suraeNoether: I don’t think you can shame them like that  
<strong>\<gsee\></strong> should users consolidate outputs before the fork? just in case they’re going to try to create the same ring on both chain, it would be easier to do with fewer outputs, right?  
<strong>\<suraeNoether\></strong> feels like an easy public relations way to deal with malicious shit in the future like this  
<strong>\<suraeNoether\></strong> gsee: sure, but you are (see above) relying on any ring members to do the same as you  
<strong>\<sgp\></strong> Perhaps, it is a social attack after all  
<strong>\<suraeNoether\></strong> if half of your ring members don’t know what to do and spend their shit on both forks in a sloppy way, then your effective ring size shrinks in a chain reaction  
<strong>\<suraeNoether\></strong> because their output is now provably spent and can be removed from any rings referencing it  
<strong>\<sgp\></strong> And with ringsize 5, you would have to expect \~2/3 of transactions on MoneroV to use that tool  
<strong>\<suraeNoether\></strong> sounds about correct. seems like a real easy way to part fools from their money. fluffypony don’t we have a public relations firm now?  
<strong>\<suraeNoether\></strong> monerov is a pretty brilliant social attack. probably not state actors because the result is a public de-anonymization instead of secretly gathering intel, but pretty brilliant  
<strong>\<suraeNoether\></strong> i could be convinced its the cryptonote guys  
<strong>\<suraeNoether\></strong> anyway, it is unsafe to use your key images on another chain, period  
<strong>\<suraeNoether\></strong> if you broadcast your key images in general, you are also opening yourself up to transaction censorship  
<strong>\<gsee\></strong> MoneroV might not be state sponsored, but the next one might be. Or a state may decide to bid up the price of moneroV in order to entice people to spend their moneroV  
<strong>\<suraeNoether\></strong> yeah, maybe  
<strong>\<suraeNoether\></strong> it’s just, in general, key images are sort of like commitments to a transaction. Opening the commitment, sharing the key image, is part of broadcasting a transaction. it shouldn’t be seen as a standalone piece that can be treated separately like a view key  
<strong>\<suraeNoether\></strong> okay, so today we’ve spoken about my and sarang’s work from this past week briefly, and we discussed the EAE attack (rehrar, pm me, don’t make any changes until we’ve chatted with fluffypony and luigi1111 and moneromooo and others), and the MoneroV airdrop  
<strong>\<rehrar\></strong> no changes will be made  
<strong>\<sgp\></strong> I suppose now’s a good time for me to ask if you think it’s prudent to increase the ringsize to mitigate the damage of a chain split attack. If the costs are minimal compared to the benefits  
<strong>\<sarang\></strong> any other updates or questions about other non-pants-on-fire things?  
<strong>\<suraeNoether\></strong> I believe we can summarize the EAE attack as: don’t use private money with non-private businesses (KYC exchanges in particular). in the meantime, I’m going to think about a threat model. and we can summarize the MoneroV airdrop as: don’t use your Monero key images on the MoneroV blockchain. period.  
<strong>\<andytoshi\></strong> sgp: to increase the ringsize dramatically will require new tech (RTRS or BPs)  
<strong>\<andytoshi\></strong> just doubling it or something won’t really help i think  
<strong>\<suraeNoether\></strong> to increase the ringsize moderately will not be a sufficient protection against the EAE problem  
<strong>\<suraeNoether\></strong> ^  
<strong>\<gsee\></strong> i have a question. Not sure if this is the best place/time to ask, so we can take it offline if necessary. Is there any way to prove what my wallet’s balance was on Dec 31st to an auditor if I have made transactions since then?  
<strong>\<suraeNoether\></strong> i believe we don’t see a lot of benefit until we get ring sizes in the 20s, last time I ran computations, but don’t quote me  
<strong>\<sgp\></strong> Won’t help EAE, but would help chain split issue  
<strong>\<andytoshi\></strong> gsee: yes but you’ll need provisions or something  
<strong>\<andytoshi\></strong> oh, no, just a view key + the public blockchain will be enough  
<strong>\<suraeNoether\></strong> it would probably be sufficient to reveal to an auditor the private transaction key for each transaction, but that reveals a lot more information to the auditor than if you reveal the key images that you’ve spent  
<strong>\<moneromooo\></strong> You see all incoming monero along with block heights, and you can scan the chain for the height a key image was spent, if any. So yes. The DB has no index for key image -\> height-or-tx though, so slow.  
<strong>\<iDunk\></strong> If he spent from tha wallet, then change would appear as new income.  
<strong>\<suraeNoether\></strong> i imagine in most <em>legal</em> situations gsee, you could merely present a screenshot of your wallet balance  
<strong>\<suraeNoether\></strong> tbh  
<strong>\<gsee\></strong> that’s what we’re leaning towards right now. Actually having someone stand over my shoulder while I show the balance  
<strong>\<suraeNoether\></strong> but if you reveal your key images, again, you are proving some outputs as spent to an auditor, which reduces the effective ring size of any other signatures depending on your keys  
<strong>\<suraeNoether\></strong> gsee if that’s an option, do it that way  
<strong>\<suraeNoether\></strong> requires no cryptographic trickery  
<strong>\<suraeNoether\></strong> meatspace is like… the best at keeping secrets  
<strong>\<suraeNoether\></strong> in practice, most cryptographic protocols can be broken with a hammer or a 4 dollar wrench in a rather nasty sidechannel attack. :P  
<strong>\<sarang\></strong> So, what’s everyone’s priorities for the next week?  
<strong>\<gsee\></strong> ok. would be great if we could create better tools for the future that would let them verify independently. Maybe that’s not possible without leaking too much info; especially if one auditor becomes widely used.  
<strong>\<sarang\></strong> Since it’s 18:00 now  
<strong>\<suraeNoether\></strong> mmmultisig brother. talking with a few venues for the monero conference this week.  
<strong>\<suraeNoether\></strong> oh i have an idea  
<strong>\<sarang\></strong> Does anyone see any immediate action items regarding MoneroV etc?  
<strong>\<suraeNoether\></strong> i feel like we need to put out a formal announcement on reddit or something  
<strong>\<sarang\></strong> So we have no formal suggestion on ringsize re: monerov?  
<strong>\<suraeNoether\></strong> ring size isn’t going to help the monerov airdrop problem  
<strong>\<sarang\></strong> Yes just confirming  
<strong>\<sarang\></strong> So our messaging is consistent  
<strong>\<suraeNoether\></strong> i know we just put out a joint statement on PoW and key re-use  
<strong>\<suraeNoether\></strong> but i feel like MRL could write a reddit post like “Here’s how to claim your Monerov safely: DON’T.”  
<strong>\<sarang\></strong> But I’ll get 10x the money\!\!111\!\!\!  
<strong>\<sarang\></strong> While we’re at it, I’ll give you two shiny new nickels for that quarter you’ve got there  
<strong>\<suraeNoether\></strong> gsee: to prove to an auditor you have spent some transactions you can (in terms of easy and insecure to hard and secure): 1) hand them your view and spend private keys. after the audit is over, send yourself money to a new pair of keys so you don’t have to worry about the old ones being used to spend. rely on meatspace legal structure to protect you from theft by the auditor. this degrades not only  
<strong>\<suraeNoether\></strong> your security but the security of all ring signatures dependent on your outputs. 2) hand them the key images of your spent outputs. you don’t need to worry about the auditor spending your money, but this still degrades both your security and other folks’ security. 3) ??  
<strong>\<scoobybejesus\></strong> If there were a tool to produce identical rings… I haven’t decided whether I’d take advantage. Without that tool, I’m definitely not interested.  
<strong>\<suraeNoether\></strong> scoobybejesus: even then, if your other ring members go cash in and <em>don’t</em> use that tool, your ring size just shrunk brother  
<strong>\<scoobybejesus\></strong> true that ;)  
<strong>\<suraeNoether\></strong> okay, until next week
