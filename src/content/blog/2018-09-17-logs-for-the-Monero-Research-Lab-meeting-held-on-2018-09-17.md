---
title: Logs for the Monero Research Lab Meeting Held on 2018-09-17
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> welcome to the \#monero-research-lab meeting for 17 September 2018  
<strong>\<sarang\></strong> Hullo  
<strong>\<silur\></strong> hi  
<strong>\<suraeNoether\></strong> we didn't meet last week because Sarang and I were meeting in person for some productivity turned up to 11, enabled partly by endogenic  
<strong>\<sarang\></strong> When snarks  
<strong>\<sarang\></strong> Or at least snark  
<strong>\<suraeNoether\></strong> today's agenda is only 1) greetings is 2) a brief update on what folks have been working on and what they see coming up next  
<strong>\<suraeNoether\></strong> we got 1) out of the way so efficiently, i'm just blown away, look at you guys, you are rock stars  
<strong>\<dog\\\></strong> lol  
<strong>\<sarang\></strong> Shine on suraeNoether  
<strong>\<silur\></strong> ^  
<strong>\<suraeNoether\></strong> sarang has recently been doing some digging into view key solutions for additional functionality like balance-proving or proofs-of-reserve; is there anything you want to bring up publicly about those for now sarang?  
<strong>\<suraeNoether\></strong> since you have like 3minutes  
<strong>\<sarang\></strong> Just that the nature of our txn model means balance proofs open up knapsack style problems, are not efficient, and therefore I think not something of great priority  
<strong>\<suraeNoether\></strong> yeah, and we can elaborate on that for folks who are interested as the week goes on  
<strong>\<sarang\></strong> Sure  
<strong>\<suraeNoether\></strong> or just later today :D  
<strong>\<suraeNoether\></strong> earlier this week, I discussed some stuff regarding finding provably spent subsets of output keys  
<strong>\<sarang\></strong> Oh and they're likely always going to be interactive, which is a bad ux  
<strong>\<suraeNoether\></strong> sarang and i worked some of this out in person  
<strong>\<sarang\></strong> Aye  
<strong>\<suraeNoether\></strong> essentially the take-away is this:  
<strong>\<suraeNoether\></strong> let's say some entity like the Monero Project wants to keep a blackball list of provably spent outputs  
<strong>\<suraeNoether\></strong> to avoid mixing with future ring signatures  
<strong>\<suraeNoether\></strong> let's say a user doesn't trust the Monero Project  
<strong>\<suraeNoether\></strong> this user wants to verify all the computations used in computing that blackball list, to verify that the list is a complete list of all provably spent outputs  
<strong>\<suraeNoether\></strong> the user loses trust in the Monero project if any provably spent set is found that is not on the list, or if any set on the list is not actually provably spent  
<strong>\<suraeNoether\></strong> how long does the user need to take to verify a small section of the list? let's say only for transactions created in a single day?  
<strong>\<gingeropolous\></strong> tree fitty  
<strong>\<suraeNoether\></strong> well, the answer to that is in the binomial coefficient: to completely verify a day's worth of transactions (between 10^3 and 10^4 presently), with a ring size of r=7, requires presently at least 1000-choose-7 checks. this is... around 2e17 things to check. even in constant time, that takes a loooong time to check  
<strong>\<suraeNoether\></strong> it's maybe doable, but to verify even a month's of transactions is like 4e27, and there's a certain point where verifiers can no longer check the list for completeness  
<strong>\<binaryFate\></strong> I disagree the user loses trust if a provably spent set is not on the list (assuming he uses his own method, not the public sources for determining blackball list). The opposite would be more devastating.  
<strong>\<sarang\></strong> I agree  
<strong>\<sarang\></strong> We just want the user to trust that nobody is being censored  
<strong>\<sarang\></strong> And verifying the list will be easy  
<strong>\<suraeNoether\></strong> binaryFate: that's fair, what i mean is if the Monero Project is acting like a curating party for this blackball list, they are acting as a trusted third party, so there is a risk to the user if that third party is acting dishonestly  
<strong>\<sarang\></strong> Each item can also have its rings listed  
<strong>\<sarang\></strong> So the user checks her own copy of the chain  
<strong>\<binaryFate\></strong> I think it's fine as long as it's advertise as a "best effort" and not claiming to be exhaustive.  
<strong>\<suraeNoether\></strong> right, checking small pieces of this list for provable spent-ness is easy: verifying that the list is \*complete\* can be made "essentially impossible" by picking larger rings; and using this sort of heuristic, we (sarang and I) determined anything above ring size 45-ish is wasteful in this regard  
<strong>\<sarang\></strong> You're all in luck. My plane is delayed  
<strong>\<gingeropolous\></strong> is there a way to distribute the computation BOINC style? decentralize all the things and all  
<strong>\<sarang\></strong> The initial computation  
<strong>\<sarang\></strong> Yes  
<strong>\<binaryFate\></strong> I would be way more comfortable to give up completely on the idea to claim we're exhaustive.  
<strong>\<sarang\></strong> Then everyone can check their peers work  
<strong>\<suraeNoether\></strong> but the key take-away here is that checking our blackball list for ring sizes beyond 3 is impractical for our project. we kicked the idea around of a sidechain that rewards finding provably spent sets on the main chain and proving their spent-ness on the side-chain to earn a PoW reward :D  
<strong>\<binaryFate\></strong> There might be more tricks we did not realize yet.  
<strong>\<sarang\></strong> We can do a small ring complete subset analysis once  
<strong>\<sarang\></strong> And hardcode it  
<strong>\<suraeNoether\></strong> yep  
<strong>\<sarang\></strong> Optional user verification  
<strong>\<binaryFate\></strong> Better to go with "best effort given computational ressources used and state of our understanding; anyone welcome to improve it"  
<strong>\<sarang\></strong> Yes  
<strong>\<suraeNoether\></strong> binaryFate: for sure, for sure  
<strong>\<sarang\></strong> We will have the complete list for those small rings  
<strong>\<gingeropolous\></strong> also seems reasonable given our constant releases and forks and checkpoints  
<strong>\<sarang\></strong> We don't need to run it further  
<strong>\<sarang\></strong> But I'm writing up a quick thing on it  
<strong>\<suraeNoether\></strong> right, point is now we have a reasonable expectation of when to stop increasing our curation of the blackball list: ring size 4 is pretty much impractical already, ring size 5 is going to be... a... loooong.... wait...  
<strong>\<binaryFate\></strong> that's totally ok  
<strong>\<suraeNoether\></strong> on other fronts, I've been looking into zk-snarks and starks as a sidechain on monero, with no transparent pool (the "transparent" pool would be monero's base layer, and this starky side-chain would be the optional "shielded" pool on top of it). i'm looking into trust-free accumulators; i think there's actually a "whole new protocol" sort of thing going on using certain accumulator constructions (see  
<strong>\<suraeNoether\></strong> <https://link.springer.com/chapter/10.1007/978-3-642-31284-7\_14> for example)  
<strong>\<IsthmusCrypto\></strong> Can these calculations be parallelized/cluster-ified?  
<strong>\<IsthmusCrypto\></strong> (the blackball)  
<strong>\<suraeNoether\></strong> yes they can  
<strong>\<gingeropolous\></strong> im curious - is this calculation / processing done on a given state? Or is it done while building the blockchain? i.e., you could imagine a Sync 2.0 where the monero blockchain takes even LONGER because while your synchronizing, your own computer is curating its own blackball  
<strong>\<suraeNoether\></strong> very parallelizable  
<strong>\<suraeNoether\></strong> but huuuuge search space  
<strong>\<sarang\></strong> Worth noting that verification is fast for the user  
<strong>\<sarang\></strong> gingeropolous: I don't think we'd need to do a live version during sync  
<strong>\<sarang\></strong> Damn. Planes radar altimeter is busted :(  
<strong>\<sarang\></strong> No bueno  
<strong>\<suraeNoether\></strong> gingeropolous: there are ways to make it faster to blackball in a rolling computation like that, but even for a single day's worth of blocks per batch, you end up having a huge space to search (which is why i selected a day above)  
<strong>\<gingeropolous\></strong> and if the blacksync indeed does work, you could just prune them from the blockchain and the network eventually reaches a blackballed consensus because those outputs just don't exist... hrmmmm  
<strong>\<gingeropolous\></strong> but it doesn't matter because once we're at ringsize 21 we can all go on vacation  
<strong>\<suraeNoether\></strong> yeah, and syncing from scratch doesn't really solve the problem, because even short periods of time end up with huge search spaces  
<strong>\<suraeNoether\></strong> if i had a single transaction to the blockchain with a single output, i need to check every known subset to see which share ring members with the new transaction  
<strong>\<IsthmusCrypto\></strong> \>\_\<  
<strong>\<sarang\></strong> But that also means an attacker would have to do that too  
<strong>\<suraeNoether\></strong> yes, precisely  
<strong>\<sarang\></strong> So it becomes nbd  
<strong>\<sarang\></strong> Under a certain threat set  
<strong>\<binaryFate\></strong> If ultimately we're facing an NP-complete/NP-hard problem, we could quantify it and demonstrate no attacker can go beyond rings N, no more than we can.  
<strong>\<suraeNoether\></strong> for complete lists, that is correct; a ring size of, say, 45-ish gets us close to "you have to brute force more things than particles in the universe" territory  
<strong>\<sarang\></strong> Yeah that's the reasonable approach idea  
<strong>\<suraeNoether\></strong> but you still have heuristic linkability; all this is merely to discuss proven spent-ness  
<strong>\<binaryFate\></strong> This is all theoretical fun anyway, in practice it's assumed all this has no bearings on post-ringct tx anyway  
<strong>\<sarang\></strong> Given high ring sizes yes  
<strong>\<binaryFate\></strong> suraeNoether Monero always has heuristic linkability anyway... we're only very good at plausible deniablity  
<strong>\<suraeNoether\></strong> yeah, the likelihood this happens on accident is vanishingly small, so someone would have to be doing it on purpose for it to really be a problem  
<strong>\<suraeNoether\></strong> binaryFate: absolutely correct  
<strong>\<sarang\></strong> And this is a fairly easy way to improve safety  
<strong>\<sarang\></strong> Therefore worth doing  
<strong>\<suraeNoether\></strong> ok, so this week i am finally going to pick a journal for peer review for thring signatures  
<strong>\<sarang\></strong> And even doing it on purpose requires collusion anyway  
<strong>\<sarang\></strong> And then the attacker can just outputs they control anyway  
<strong>\<IsthmusCrypto\></strong> That would be an interesting idea, if a hostile node just returns outputs off the blackball list whenever queried for decoys  
<strong>\<suraeNoether\></strong> IsthmusCrypto: yeah but why would it do that instead of using its own outputs? :P  
<strong>\<suraeNoether\></strong> sarang and i go back and forth on it  
<strong>\<IsthmusCrypto\></strong> Depends if the node is lawful evil or chaotic evil  
<strong>\<IsthmusCrypto\></strong> lawful might use own outputs. Chaotic might just ruin it for everybody.  
<strong>\<needmoney90\></strong> It would get noticed immediately  
<strong>\<needmoney90\></strong> Or fairly quickly  
<strong>\<needmoney90\></strong> If they used known black balled outputs  
<strong>\<needmoney90\></strong> Exclusively  
<strong>\<IsthmusCrypto\></strong> Is somebody watching out for that, or should MAP set it up?  
<strong>\<IsthmusCrypto\></strong> Oh  
<strong>\<IsthmusCrypto\></strong> because they're all so old  
<strong>\<IsthmusCrypto\></strong> yeah, that would be obvious  
<strong>\<IsthmusCrypto\></strong> smh  
<strong>\<IsthmusCrypto\></strong> sorry, continue  
<strong>\<suraeNoether\></strong> anyway, i don't think provably spentness is really the issue  
<strong>\<suraeNoether\></strong> i believe that if you take the bipartite graph model and weight edges by output key age at the time of the transaction used it, we would re-attain the monerolink heuristic linkability model; what's funny about that, though, is that even if you were to optimize that guy to look for "probably" not provably spent outputs, you would still have such a large space to search through, you'd never quite be sure if  
<strong>\<suraeNoether\></strong> there wasn't a more likely solution right around the corner  
<strong>\<suraeNoether\></strong> i want to quantify that  
<strong>\<suraeNoether\></strong> because i think heuristic linkability is more a danger issue for monero  
<strong>\<suraeNoether\></strong> thank accidentally using provably spent ring members  
<strong>\<IsthmusCrypto\></strong> ^^ agree  
<strong>\<suraeNoether\></strong> later this week, i'll be reviewing the general M/N multisig thing  
<strong>\<suraeNoether\></strong> is there anything else that folks want MRL to work on, bring up, discuss, etc? There will be news about the Denver Monero Conference later this week, I think.  
<strong>\<suraeNoether\></strong> IsthmusCrypto and silur you guys have been working on stuff  
<strong>\<suraeNoether\></strong> would you care to discuss it?  
<strong>\<IsthmusCrypto\></strong> I can give a quick update on some of the \#noncesense-research-lab projects  
<strong>\<IsthmusCrypto\></strong> 1) Working on ways to automate identification of selfish/stubborn mining, since I have been doing it by visual inspection so far. One example written up so far.  
<strong>\<IsthmusCrypto\></strong> 2) Doing a small study of nodes doubled up on IP addresses. Checked peer lists and found duplicates. This is a subtle type of centralization - if 20% of our nodes/miners are showing up over a handful of ProtonVPN addresses, then another DoS on the VPN would have the side effect of knocking a disproportional number of machines off the network.   
<strong>\<IsthmusCrypto\></strong> 3)Vanity stealth addresses generation. If all of your personal outgoing transactions have the same prefix, then they will be indistinguishable from each other. This maximizes fungibility and eliminates headaches caused by how difficult it is to link your transactions on the blockchain. When you restore your wallet, use the same vanity code - the initial sync time decreases by orders of magnitude when your  
<strong>\<IsthmusCrypto\></strong> wallet only needs to check outputs that obviously belong to it\! /s  
<strong>\<IsthmusCrypto\></strong> 4) Blockchain analysis to identify all MyMonero.com transactions that used high or paranoid mode. Partial writeup, but porting over to unsupervised ML methods to automatically pick out all the MyMonero txns from the main fungible cluster.  
<strong>\<IsthmusCrypto\></strong> 5) A lot of work on MAP infrastructure by @n3ptune - both backend database work and some slick UI/visualization  
<strong>\<IsthmusCrypto\></strong> And a misc pet project on timing how long it takes to sync the blockchain on different machines.  
<strong>\<IsthmusCrypto\></strong> (end)  
<strong>\<suraeNoether\></strong> \#4 will be a paper that will be used as FUD; want to collab on an MRL bulletin and use our header and stuff so it's clear it's coming from MRL?  
<strong>\<silur\></strong> quantum-vrf is on it's way I had major advances and even figured out that i can do it in a designated verifier setup. also I've sent you my slides on RTRS for HCPP prague, did you have time to review it?  
<strong>\<suraeNoether\></strong> no, i have not, did you email it or mention it in chat?  
<strong>\<silur\></strong> you = suraeNoether &amp; sarang  
<strong>\<silur\></strong> email it for both of you  
<strong>\<silur\></strong> on your protonmail addr  
<strong>\<needmoney90\></strong> IsthmusCrypto: for number 3, the vanity prefix can be deterministic with the private key as the seed, right?  
<strong>\<suraeNoether\></strong> just found it; when is the talk?  
<strong>\<needmoney90\></strong> So every new stealth address has a new prefix that can't be determined ahead of time without the private key  
<strong>\<silur\></strong> october 3  
<strong>\<suraeNoether\></strong> ok i will review it this week  
<strong>\<needmoney90\></strong> That's actually super cool  
<strong>\<silur\></strong> thanks  
<strong>\<suraeNoether\></strong> for \#3 that forbids sending to a subaddress  
<strong>\<suraeNoether\></strong> since the subaddress recipient has to ask for a specific basepoint on the transaction key  
<strong>\<suraeNoether\></strong> which sucks  
<strong>\<suraeNoether\></strong> silur i am more interested in your quantum vrf to be honest :D hehe  
<strong>\<IsthmusCrypto\></strong> @suraeNoether - yea RE \#4 I’ll keep you in the loop. Don’t want to give FUD fodder, so I am really hoping that MyMonero will fix it soon....  
<strong>\<silur\></strong> and I'd like your review on that I could send you the draft and we can eliminate my probably countless mistakes :)  
<strong>\<IsthmusCrypto\></strong> \#3 was just a joke, although it does reflect a real threat model (using a few digits to encode which output is the true spender, or maybe use a few digits to mark part of a hash of the private key to deterministically fingerprint transactions \*from\* the same account.  
<strong>\<IsthmusCrypto\></strong> (would be malicious wallet software trying to communicate with no telemetry besides what is on the blockchain)  
<strong>\<needmoney90\></strong> I think it could actually be used for fast sync  
<strong>\<needmoney90\></strong> Without fungibility concerns  
<strong>\<suraeNoether\></strong> endogenic ^ can't really do anything about the older choices, but we can patch that up moving forward  
<strong>\<sarang\></strong> Hooray fixed plane. TTYL. Will be on after landing  
<strong>\<suraeNoether\></strong> prefixing keys makes them distinguishable by prefix, so i'm not sure what the goal of the idea is :P  
<strong>\<needmoney90\></strong> Surae, make the prefix deterministic  
<strong>\<needmoney90\></strong> Increment private key by 1 every tx, hash it, truncate, and use that as the prefix  
<strong>\<needmoney90\></strong> Without the private key you can't fingerprint the txes  
<strong>\<binaryFate\></strong> I think you still get a different prefix for each output no?  
<strong>\<needmoney90\></strong> That's a super naive method of course  
<strong>\<needmoney90\></strong> You do binaryfate, but when scanning the chain you can look for the next prefix  
<strong>\<needmoney90\></strong> Every time you find one, you increment and look for the next  
<strong>\<binaryFate\></strong> I mean within the same transaction  
<strong>\<binaryFate\></strong> And as you don't know the order, you can miss some  
<strong>\<needmoney90\></strong> Ah, yes  
<strong>\<needmoney90\></strong> If it's the same tx you can have a lookback  
<strong>\<needmoney90\></strong> That's not a huge deal imo  
<strong>\<binaryFate\></strong> true  
<strong>\<needmoney90\></strong> Sorry for doing research stuff in the meeting, carry on guys. I'll bring this to the lounge.  
<strong>\<suraeNoether\></strong> needmoney90: interesting... i need to thinka bout that. :P actually needmoney90 this is what the research meeting is for :D  
<strong>\<binaryFate\></strong> I've been finally getting to work on an idea I had since a long time, I think I mentioned it here a couple of times.  
<strong>\<suraeNoether\></strong> please go ahead\!  
<strong>\<silur\></strong> yea I missed that and interested :D  
<strong>\<binaryFate\></strong> Broad idea is to study the age distribution of \*actual\* spendings of Monero users, with ultimately maybe proposing a better decoy output selection algorithm  
<strong>\<sarang\></strong> Go on  
<strong>\<needmoney90\></strong> If it's opt in, wouldn't the set of data we collect be skewed away from those who are super cautious about privacy?  
<strong>\<binaryFate\></strong> Maybe best to explain the approach is a simplified example: imagine all rings are of size 2 (one real + one decoy). The "real" distribution is unknown, but the "decoy" one is known from what the wallet software is doing (restricted to certain block ranges where we are confident an overly large percentage of users are using the same version)  
<strong>\<binaryFate\></strong> The result is a mixture, or (simplified) a weighted distribution. This is observable in the blockchain.  
<strong>\<binaryFate\></strong> By using the observable bit, and the known part of the weighted distribution, I want to estimate the unknown one, aka the real spending habits  
<strong>\<binaryFate\></strong> I'm writing an R package to do this, with an emphasis on graphically comparing what we should expect if users were spending "as we think" versus what we actually see from the blockchain  
<strong>\<binaryFate\></strong> so whatever results I get be done again in the future with the same procedure  
<strong>\<binaryFate\></strong> First results expecting soon (this week hopefully)  
<strong>\<binaryFate\></strong> This will also allow to check the Miller et al. gamma distribution fitting btw, which afaik nobody really cross-checked (even though it will make it into the next hard fork)  
<strong>\<binaryFate\></strong> (end)  
<strong>\<gingeropolous\></strong> so is this asking which inputs are outliers of the distribution the wallet is using?  
<strong>\<binaryFate\></strong> no, it's about the distributions, not the level of inputs. It's comparing "the situation we are modelling using \[triangular/gamma\] distribution" and "what we see in the blockchain"  
<strong>\<gingeropolous\></strong> gotcha  
<strong>\<binaryFate\></strong> Think of it as cutting through the noise to estimate the real spending habits, but it only gives you the distribution of it, no info on a single input  
<strong>\<binaryFate\></strong> We rank highly on plausible deniablity :) I'm trying to improve on the distribution/heuristic thing. There was very little studies to come up with first the triangular one then the gamma one.  
<strong>\<binaryFate\></strong> Anyway, I'll probably have a draft report in week or two to circulate.  
<strong>\<suraeNoether\></strong> this is a very interesting idea  
<strong>\<suraeNoether\></strong> i'm a little confused; where are you getting your data? your own wallet?  
<strong>\<IsthmusCrypto\></strong> It doesn't need a ground truth. It's just actual distribution minus decoy selection algorithm expectation, right?  
<strong>\<endogenic\></strong> IsthmusCrypto: fix the ability to use different ring sizes? the new apps and new web wallet do not allow you to pick, for that reason. i didn't expect we'd still have the old mymonero.com wallet up til now and totally forgot we have the mixin select there  
<strong>\<endogenic\></strong> just let me know next time :)  
<strong>\<endogenic\></strong> got so many things going on :  
<strong>\<binaryFate\></strong> IsthmusCrypto correct  
<strong>\<endogenic\></strong> will start to settle down soon i hope  
<strong>\<suraeNoether\></strong> IsthmusCrypto: ahhhhh i see, yeah, if i understand it correctly, that's a wonderful treasure trove of useful data. :P  
<strong>\<suraeNoether\></strong> oh man  
<strong>\<endogenic\></strong> anyway IsthmusCrypto can you really tell they are -MyMonero- transactions?  
<strong>\<suraeNoether\></strong> binaryFate: good freaking idea\!  
<strong>\<endogenic\></strong> or just that they have a high ring size?  
<strong>\<IsthmusCrypto\></strong> The MyMonero fingerprint is based on the ringsize AND the decoy selection algorithm  
<strong>\<binaryFate\></strong> suraeNoether simplified example again (ring size 2): wallet is known to use unifom for decoy. Blockchain shows distribution X (and we know it's 0.5 wallet distrib + 0.5 user real spending). We can compare the two and infere a lot about real user spending  
<strong>\<IsthmusCrypto\></strong> The first is a good signpost to find candidates, then the second is the actual give-away  
<strong>\<binaryFate\></strong> I'm just getting interesting results as we speak, but prefer to clear things a bit before sending to anyone  
<strong>\<endogenic\></strong> IsthmusCrypto: just want you to know i've been motivating for the decoy selection algo change for a long time,  
<strong>\<endogenic\></strong> i'm discussing it internally again to get it done ...  
<strong>\<endogenic\></strong> we hve work on it  
<strong>\<endogenic\></strong> need to stabilize and deploy..  
<strong>\<IsthmusCrypto\></strong> Cool @edogenic. I haven't worried about it too much or rushed the research because the impending fixed ring size will remove half of the heuristic.  
<strong>\<suraeNoether\></strong> binaryFate: more generally: if we use a distribution F to pick ring members, the extent to which ring members on the blockchain vary from F is directly related to the true signers... really great approach  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<suraeNoether\></strong> okay, anyone else have anything they want to chat about?  
<strong>\<suraeNoether\></strong> it's been a few weeks  
<strong>\<binaryFate\></strong> yep, and it's directly quantifiable by the ring sizes too  
<strong>\<IsthmusCrypto\></strong> Last thought - can we start recording MRL meetings alongside the other dev diaries? It would be good for accessibility and showcasing some of the best people/conversations in our community  
<strong>\<IsthmusCrypto\></strong> If somebody can show me where/how, I can take care of uploading them.  
<strong>\<selsta\></strong> IsthmusCrypto: they used to get uploaded  
<strong>\<selsta\></strong> or did they?  
<strong>\<selsta\></strong> anyway I plan on creating a IRC bot that auto uploads the meetings  
<strong>\<suraeNoether\></strong> IsthmusCrypto: i usually throw the logs up on my github, but i have been lazy lately; i'll set aside an hour later today to upload all the ones I have  
<strong>\<suraeNoether\></strong> if anyone wants to put them anywhere else, feel free, maybe we could throw them up on the getmonero.org page or something like that. i'll look into a few options  
<strong>\<IsthmusCrypto\></strong> 👍 I started thinking about this when the person showed up claiming that fixed ring sizes hadn't been publicly discussed  
<strong>\<suraeNoether\></strong> if anyone wants to take initiative and upload meeting logs that are missing before i get to them, that'd be a great contribution to MRL  
<strong>\<suraeNoether\></strong> only so many hours in a day :D  
<strong>\<suraeNoether\></strong> either way, i'll try to organize what i see available later today. my github is a mess  
<strong>\<IsthmusCrypto\></strong> Cool, I was thinking I could upload them here? (If that seems alright and somebody shows me how or wants to take initiative and do it themselves)  
<strong>\<binaryFate\></strong> go for it  
<strong>\<endogenic\></strong> good idea  
<strong>\<IsthmusCrypto\></strong> Do I just PR it to here? <https://github.com/monero-project/monero-site/tree/master/\_posts>  
<strong>\<suraeNoether\></strong> i believe that is correct; moneromooo or luigi1111 ?  
<strong>\<selsta\></strong> IsthmusCrypto: yes, but you have to convert the logs to markdown  
<strong>\<suraeNoether\></strong> ok, I believe we are over an hour here, so we'll wrap this up  
<strong>\<suraeNoether\></strong> any last notes/comments/concerns/questions?  
<strong>\<suraeNoether\></strong> i'm expecting my cross-chain paper to be done by the end of the month, i think; it's actually a lot simpler than the multisig paper  
<strong>\<silur\></strong> the cross-chain atomic swaps?  
<strong>\<silur\></strong> not quite, I remember it had a much cooler name  
<strong>\<silur\></strong> ring-confidential atomic swaps or something  
<strong>\<moneromooo\></strong> No, to <https://repo.getmonero.org/>  
<strong>\<silur\></strong> oh didn't even know about that thx
