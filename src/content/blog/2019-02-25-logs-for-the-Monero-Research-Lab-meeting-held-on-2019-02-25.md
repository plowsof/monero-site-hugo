---
title: Logs for the Monero Research Lab Meeting Held on 2019-02-25
summary: Output Selection, MRL work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> We'll start momentarily; see agenda in topic  
<strong>\<suraeNoether\></strong> good mooooorning mrl  
<strong>\<sarang\></strong> Hullo all  
<strong>\<sarang\></strong> Let's get started\!  
<strong>\<ArticMine\></strong> hi  
<strong>\<sarang\></strong> 1. Greetings  
<strong>\<sarang\></strong> A very talkative bunch we are today  
<strong>\<suraeNoether\></strong> howdy :D  
<strong>\<vtnerd\></strong> hello  
<strong>\<moneromooo\></strong> Mooooo.  
<strong>\<sarang\></strong> A particular topic I added to the agenda is 2. Output selection  
<strong>\<sarang\></strong> I have a short writeup and some sim results on the agenda issue: <https://github.com/monero-project/meta/issues/307#issuecomment-466514757>  
<strong>\<sarang\></strong> The problem is that our current algo overselects outputs from small blocks  
<strong>\<suraeNoether\></strong> Sarang and I last week in person nailed down some distributional stuff for output selection and coded up a few different ways of assessing the results.  
<strong>\<sarang\></strong> You'll see 4 different algos tested, each for 4 different chain output density scenarios  
<strong>\<suraeNoether\></strong> each of these scenarios represents a different plausible situation our economy could undergo  
<strong>\<suraeNoether\></strong> a feast scenario is one in which we get popular, a famine scenario is one in which monero usage drops  
<strong>\<sarang\></strong> Under normal chain conditions, each of the 3 alternatives (the fourth is the current method) does a better job than what we have now  
<strong>\<sgp\_\></strong> o/  
<strong>\<sarang\></strong> Under extreme conditions, there are tradeoffs  
<strong>\<sarang\></strong> Here is what I want to know from this group:  
<strong>\<sarang\></strong> if the chain density hits a low point, what should selection do?  
<strong>\<sarang\></strong> If it stays true to chain condition, we'll overselect (for example) coinbase... but if we skew to older outputs, we maintain a better weighted ratio  
<strong>\<suraeNoether\></strong> so, here is my thinking  
<strong>\<suraeNoether\></strong> if chain density is dropping, then spend-times are getting longer and longer  
<strong>\<sarang\></strong> yep  
<strong>\<suraeNoether\></strong> that's economicalliy a depression  
<strong>\<suraeNoether\></strong> so the average age of ring members should also increase to reflect the "true" spend-time distribution  
<strong>\<suraeNoether\></strong> on the other hand, during a feast scenario, the opposite is happening  
<strong>\<sarang\></strong> Based on that, the output-lineup algo does a better job  
<strong>\<suraeNoether\></strong> in that regard, it seems like the lineup method performs better htan others  
<strong>\<suraeNoether\></strong> yep  
<strong>\<sarang\></strong> under those extreme densities, it skews the ages  
<strong>\<suraeNoether\></strong> btw i look at geometric as a flavor of the famine scenario  
<strong>\<suraeNoether\></strong> oh wait, feast i mean  
<strong>\<sarang\></strong> Geometric was intended as a 0-order approximation of real conditions; it's not very good but it's something to use for comparison  
<strong>\<suraeNoether\></strong> in addition to comparing these different sampling methods, a method of directly estimating our true spend-time distribution occurred to me last night, and i'm writing it up now  
<strong>\<sarang\></strong> Does anyone else have any thoughts on these?  
<strong>\<sarang\></strong> RandomRun made a good suggestion for a more general set of quantities to test, that I'll write up and add to the table  
<strong>\<moneromooo\></strong> Did you try the gamma \* num-outs-per-block combo ?  
<strong>\<sarang\></strong> (see their comment on the issue)  
<strong>\<sarang\></strong> suraeNoether worked up a version of that but was not happy with its outcome  
<strong>\<suraeNoether\></strong> moneromooo: the lineup and bias methods are designed to estimate that method moneromooo since computing it directly runs into certain numerical problems  
<strong>\<ArticMine\></strong> If I understand correctly chain density is a measure of velocity  
<strong>\<sarang\></strong> chain density = distribution of number of outputs per block  
<strong>\<sarang\></strong> I don't know how much this applies to velocity if amounts and destinations cannot be known  
<strong>\<ArticMine\></strong> Which given a fixed money supply is a measure of velocity.  
<strong>\<sarang\></strong> ok  
<strong>\<suraeNoether\></strong> ArticMine: yes, although the specific interpretation of velocity is tricky in this context  
<strong>\<sarang\></strong> Does this lead you to conclusions about how the selection should behave?  
<strong>\<ArticMine\></strong> It relates it to market conditions  
<strong>\<suraeNoether\></strong> yes  
<strong>\<ArticMine\></strong> and also block weight  
<strong>\<suraeNoether\></strong> a long spend-time distribution is a recession. a short spend-time distribution is a boom.  
<strong>\<sarang\></strong> Unless the results from RandomRun's suggestion indicate otherwise, I'll recommend moving to the output-lineup algorithm at an upcoming release  
<strong>\<suraeNoether\></strong> I'm also going to mess around with sampling methods, but I'm not expecting to get something that appears to perform better than the lineup method before the next fork  
<strong>\<sarang\></strong> OK, moving on for now... related to this, from time to time there have been suggestions of whether to treat coinbase outputs differently for the purposes of decoy selection  
<strong>\<ArticMine\></strong> My question is outliers in the spends  
<strong>\<sarang\></strong> ArticMine: in what way  
<strong>\<ArticMine\></strong> Namely spend that are very different from the norm at a given point in time  
<strong>\<suraeNoether\></strong> articmine: this is the classic(tm) problem with spend-time distributions  
<strong>\<sarang\></strong> Selecting from the best known distribution is intended to account for this as much as is reasonable  
<strong>\<sarang\></strong> Of course, multiple rings spending outliers from the same point in time are problematic for different reasons  
<strong>\<sarang\></strong> Any, back to the previous statement I made about coinbase outputs...  
<strong>\<sarang\></strong> It is probable that they are spent with a different distribution that is (as of now) not tested  
<strong>\<sarang\></strong> I don't support treating them differently  
<strong>\<sarang\></strong> But I thought that I would mention it in the context of output selection anyway  
<strong>\<sarang\></strong> Using a properly weighted selection algorithm will reduce their occurrence in rings as a consequence, which seems reasonable to me  
<strong>\<ArticMine\></strong> but not their elimination  
<strong>\<sarang\></strong> No, of course not  
<strong>\<ArticMine\></strong> good  
<strong>\<sarang\></strong> With the proposed algo change, their selection will be reduced toward the fraction of their occurrence on the chain  
<strong>\<sarang\></strong> and will do the same for all outputs based on how dense their blocks are, of course  
<strong>\<sarang\></strong> Anyway, please comment after the meeting or on the GitHub agenda issue with any other thoughts on output selection  
<strong>\<suraeNoether\></strong> i don't support treating coinbase differently because then the next question is whether we should treat rings with ring members that come from coinbase transactions differently. and so on; the natural conclusion is to ensure transaction trees are sort of homogeneous in their depth and stuff, and that partitions the entire space way too much. it's an over-optimization with dubious benefits, imo  
<strong>\<sgp\_\></strong> It's my opinion that coinbase outputs will never be spent in the incredible vast majority of transactions of normal users. A heuristic to eliminate the coinbase has high accuracy for anyone not suspected of mining  
<strong>\<suraeNoether\></strong> sgp\_: high sensitivity but awful specificity  
<strong>\<sarang\></strong> ^  
<strong>\<sgp\_\></strong> Under normal Monero network conditions, over 75% of the hashrate is allocated to public pools. These are all transparent  
<strong>\<ArticMine\></strong> Who then promptly spend the coinbase  
<strong>\<sgp\_\></strong> yes, and it's clear which transactions spend the coinbase too  
<strong>\<sgp\_\></strong> so these outputs are effectively dead  
<strong>\<sarang\></strong> Like I said, there is probably a different spend pattern that would be interesting to examine, both in Bitcoin and in our older discernible spends  
<strong>\<sarang\></strong> and of course the pool issue that sgp\_ mentions  
<strong>\<sarang\></strong> Requiring a mix of coinbase-only in rings moves the problem up one level in the txn graph  
<strong>\<suraeNoether\></strong> sgp\_: protecting coinbase transactions when miners can merely churn for almost no fees is not super rational. there will always be some effectively dead outputs. i'm much more concened about the privacy problems induced b y multiple-input trnasactions that are all spending inputs from similar time periods.  
<strong>\<sgp\_\></strong> yes, that one level doesn't eliminate the problem, but it makes it much better than it is today  
<strong>\<suraeNoether\></strong> sgp\_: i don't think that's been quantified, though  
<strong>\<ArticMine\></strong> Yes but overall there is merit to including coinbase because of outliers  
<strong>\<ArticMine\></strong> among coinbase  
<strong>\<sgp\_\></strong> suraeNoether: I argue against protecting coinbase outputs. I want to call them all essentially transparent  
<strong>\<suraeNoether\></strong> sgp\_: ah, i'm okay with that  
<strong>\<suraeNoether\></strong> sgp\_: hmm wait  
<strong>\<sgp\_\></strong> Since in most cases, the vast majority are already  
<strong>\<suraeNoether\></strong> sgp\_: let me think about that  
<strong>\<ArticMine\></strong> I am not so sure. In most but not all cases  
<strong>\<sgp\_\></strong> Public pools don't care since they make the info transparent anyway. We don't need to "protect" them  
<strong>\<suraeNoether\></strong> sgp\_: i disagree that they are essentially transparent  
<strong>\<sgp\_\></strong> suraeNoether: why, because it's a pool-reported heuristic?  
<strong>\<suraeNoether\></strong> no no; i mean i disagree that coinbase transactions are essentially transparent despite the public information posted by pools  
<strong>\<suraeNoether\></strong> i can still manage to spend coinbase transactions with a high degree of plausible deniability  
<strong>\<sarang\></strong> If their payout txns are reported...  
<strong>\<sgp\_\></strong> Perhaps it's more accurate for me to say: we know exactly what transactions these coinbase outputs are spent in  
<strong>\<sgp\_\></strong> Which pronounces them dead in other transactions  
<strong>\<sgp\_\></strong> known decoys  
<strong>\<suraeNoether\></strong> yes; i thought you were tr ying to apply the blanket term to \*all\* coinbase transactions. \#notallcoinbases  
<strong>\<sgp\_\></strong> no, only public pool transactions spending coinbase outputs  
<strong>\<suraeNoether\></strong> o kay, so is \*anyone\* in favor of treating coinbase transactions differently?  
<strong>\<sarang\></strong> To sum up: sgp\_ had previously advocated for a default/rule that a ring with a coinbase must contain only coinbase  
<strong>\<ArticMine\></strong> It comes down to the outliers issue. Not all coinbase outputs are dead. With a ring size of 11 we can afford to spend 1 ring on this  
<strong>\<ArticMine\></strong> If the ring size were say 3 I would support sgp\_s position  
<strong>\<moneromooo\></strong> If you want to avoid pool coinbase outs as fake outs, use a blackball list with them.  
<strong>\<sgp\_\></strong> ArticMine: in my opinion, the cost of wasting 1 ouptput per tx is worse than the harm' to solo miners if we avoid coinbase outputs entirely  
<strong>\<sgp\_\></strong> moneromooo: we want to avoid interactivity. That's really cumbersome to expect of users, and it allows for pool fuckery if they report bad info to wallet clients  
<strong>\<sarang\></strong> I assume moneromooo meant a blackball list with sources chosen by the user  
<strong>\<moneromooo\></strong> People don't have to do anything. They only do anything if they want to avoid those outputs.  
<strong>\<sarang\></strong> not some global version that can be DoS  
<strong>\<ArticMine\></strong> But you agree tat the issue is way less wit ring 11 tan say ring 3  
<strong>\<sgp\_\></strong> ArticMine: yes, a larger ringsize mitigates these issues  
<strong>\<sarang\></strong> I think that the idea of coinbase-only rings deserves more careful analysis to numerically examine the benefits and chain costs  
<strong>\<sgp\_\></strong> But I still advocate for this at any feasible ringsize  
<strong>\<moneromooo\></strong> If it was automated and everyone was magically using that system, non pool miners would be spenidng at effective mixin 0.  
<strong>\<sgp\_\></strong> moneromooo: yes  
<strong>\<sgp\_\></strong> problem is unless we avoid the coinbase outputs, wallets will select this "0-mixin" outputs in their rings  
<strong>\<sarang\></strong> I recommend we table this in the absence of any numerical evidence  
<strong>\<sarang\></strong> but that we obtain this evidence if it exists  
<strong>\<ArticMine\></strong> I agree  
<strong>\<sarang\></strong> And we can discuss after the meeting (but I wish to respect our 1-hour goal and others' time)  
<strong>\<sarang\></strong> On to 3. Other work  
<strong>\<sgp\_\></strong> I understand your point of view sarang, but the main concept isn't very difficult. You see x% of public pools which also mine and make transparent x% of new coinbase outputs  
<strong>\<sgp\_\></strong> but we can move on sure  
<strong>\<sarang\></strong> I have been working on output selection, finalizing data on block size algos, gave a talk in Nashville to a meetup  
<strong>\<sarang\></strong> One meta-item: the Loki Foundation wishes to fund me and/or suraeNoether in part for the next funding round  
<strong>\<sarang\></strong> but it comes with a contract  
<strong>\<endogenic\></strong> sarang's talk: <https://www.youtube.com/watch?v=H8ijX02J7Y0>  
<strong>\<endogenic\></strong> surae's talk: <https://www.youtube.com/watch?v=9srtIk9M2yg>  
<strong>\<sarang\></strong> I'm hesitant because I'm sure the contract terms could be abused if they were out for PR or other ends  
<strong>\<sarang\></strong> I am going to request that the contract terms be made public, since I am not a lawyer  
<strong>\<suraeNoether\></strong> i think that's true of any contract  
<strong>\<moneromooo\></strong> I don't remember them as PR whores fwiw.  
<strong>\<sarang\></strong> cool  
<strong>\<moneromooo\></strong> I didn't exactly look for it though.  
<strong>\<suraeNoether\></strong> however, i think we could propose amendments re: anticipated problems  
<strong>\<sarang\></strong> I'm trying to maintain healthy skepticism while appreciating their offer  
<strong>\<sarang\></strong> Yeah. If we can publish the contract and there are no serious objections, it reduces the community funding burden while not changing our research goals  
<strong>\<ArticMine\></strong> Making te contract public is a reasonable approach  
<strong>\<sarang\></strong> the total would be 15K USD, split between 1 or 2 people  
<strong>\<endogenic\></strong> i'd suggest consulting with a lawyer about assignment of IP, non disclosure, requirements to execute things for them, etc  
<strong>\<sarang\></strong> Yeah, they specifically don't take ownership of any research product  
<strong>\<ArticMine\></strong> Assignment of IP?  
<strong>\<endogenic\></strong> as mentioned when a contract is couched in consulting language they can say they had expectations of certain things  
<strong>\<moneromooo\></strong> One fairly easy way to prevent most of that is to say "sarang can stop this contract at any time, and the pro rata is due".  
<strong>\<sarang\></strong> but do state that if they share confidential info with researchers, it can't be discussed  
<strong>\<sarang\></strong> So if they knew about some kind of bug, they could disclose under the contract's NDA clause  
<strong>\<moneromooo\></strong> That is a massive no.  
<strong>\<moneromooo\></strong> It allows them to control what you can do open source.  
<strong>\<sarang\></strong> that's my fear  
<strong>\<sarang\></strong> If they'll alter or remove that, it takes away most of my concern  
<strong>\<sarang\></strong> I'll discuss with them and get the contract posted publicly  
<strong>\<moneromooo\></strong> If they know of a bug, htey can use H1.  
<strong>\<sarang\></strong> exactly  
<strong>\<sarang\></strong> I wonder if it's for a bug in \_their\_ software  
<strong>\<sarang\></strong> but anyway  
<strong>\<sarang\></strong> This week, I'll be finishing up additional output selection tests, doing some lit review backlog, bulletproofs MPC, etc.  
<strong>\<sarang\></strong> How about suraeNoether ?  
<strong>\<suraeNoether\></strong> Sarang and I have a deadline of March 1 for this paper we are writing; it was previously Feb 18 but it has moved. I'm finishin g up three proofs of security for that paper, and I believe we will be making the details public soon.  
<strong>\<suraeNoether\></strong> sarang: have we talked with our co-authors about when we can talk about this?  
<strong>\<sarang\></strong> Ah yes, I forgot to mention that  
<strong>\<sarang\></strong> Once it's submitted I'm sure they'll post to IACR  
<strong>\<suraeNoether\></strong> this paper we think is rather competitive, it's proposing something novel with immediate applicability, so it should be a shoe-in for publication.  
<strong>\<koracain\></strong> loki... wait jeff's project? oh lol that's a safe bet  
<strong>\<sarang\></strong> Yep\! Relates to the DLSAG construction but with much more on applications  
<strong>\<suraeNoether\></strong> in addition to that, i'm simulating blockchain stuff for the matching paper to try to get that out the door  
<strong>\<suraeNoether\></strong> i actually have a quiet week of writing for once, which is nice  
<strong>\<suraeNoether\></strong> konferenco stuff will have some more announcmeents later this week  
<strong>\<suraeNoether\></strong> if anyone wishes to submit an abstract to come speak, please drop one on us at <https://konferenco.xyz>  
<strong>\<suraeNoether\></strong> we are working to accommodate speaker travel costs, too  
<strong>\<suraeNoether\></strong> oh, and before I forget: the scholarship applications at MAGIC are now live, so anyone in the US, EU, or ZA who want a small scholarship to mitigate the costs of their books or whatever, swing on by <https://magicgrants.org>  
<strong>\<suraeNoether\></strong> and i think that's it\!  
<strong>\<endogenic\></strong> thanks as always guys  
<strong>\<sarang\></strong> koracain: you personally believe accepting Loki funding is a good bet? Or sarcasm?  
<strong>\<endogenic\></strong> you're both rockstars..  
<strong>\<sarang\></strong> Also: any other work for anyone to report?  
<strong>\<koracain\></strong> i know one of their devs  
<strong>\<sarang\></strong> cool  
<strong>\<suraeNoether\></strong> oh yeah, the most interesting part of these research meetings, to me, is the folks who aren't sarang and i  
<strong>\<sarang\></strong> Their foundation is a legally-established foundation in Australia  
<strong>\<moneromooo\></strong> From experience, knowing a dev at one company does not mean you know what the boss will do when possible.  
<strong>\<suraeNoether\></strong> i'm interested in how wallet dev is coming from endogenic, i'm interested in what hyc has been working on with moneroR, i want to hear from isthmus but he's usually in meetings around now  
<strong>\<koracain\></strong> he's legit i havn't looked very hard at the project but yah lol he'd probably blow them up if they broke monero  
<strong>\<sarang\></strong> FWIW foundation funding wouldn't change our research goals or agenda in any way  
<strong>\<sarang\></strong> They require monthly reports, but we already do that  
<strong>\<sarang\></strong> I'm optimistic that they just want to support Monero research since it would also benefit their project  
<strong>\<endogenic\></strong> also when Samsung Noether  
<strong>\<sarang\></strong> heh  
<strong>\<sarang\></strong> that falls under 5. Questions  
<strong>\<endogenic\></strong> :P  
<strong>\<koracain\></strong> look hard at it but jeff is in the i2p channels on here via a relay bot  
<strong>\<sarang\></strong> My question for moneromooo et al: when do non-consensus decisions like output selection need to be in place for an upcoming release?  
<strong>\<moneromooo\></strong> If it's the output lining thing, I can have it done pretty quick given it's very similar to what we already have.  
<strong>\<sarang\></strong> What is the expected timeline for a point release after the network upgrade?  
<strong>\<sarang\></strong> A month? Two?  
<strong>\<moneromooo\></strong> I don't think anything was even really talked about yet.  
<strong>\<sarang\></strong> ok, wasn't sure  
<strong>\<moneromooo\></strong> But that sounds plausible.  
<strong>\<sarang\></strong> Well, at least the algorithm is coded up in Python already (link in agenda writeup)  
<strong>\<sarang\></strong> so anyone can play around or test them  
<strong>\<sarang\></strong> Real chain data is included (thanks to moneromooo for pulling that)  
<strong>\<sarang\></strong> Other questions before we wrap up and return to informal discussion?  
<strong>\<sarang\></strong> Righto\!  
<strong>\<sarang\></strong> 6. Action items  
<strong>\<sarang\></strong> I will complete additional output selection testing and consider the possibilities for coinbase more thoroughly  
<strong>\<sarang\></strong> as well as get the Loki contract squared away and the other items I listed above  
<strong>\<sarang\></strong> suraeNoether?  
<strong>\<sarang\></strong> Ah, and an urgent call for translations was just made: <https://www.reddit.com/r/Monero/comments/auo078/urgentcall\_for\_translators\_we\_have\_two\_days\_to/>  
<strong>\<sarang\></strong> Quiet times... well, thanks to everyone for joining. We'll formally adjourn now, but feel free to continue any discussions about previous topics. I'll post logs on the GitHub issue later today
