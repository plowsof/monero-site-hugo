---
title: Logs for the Monero Research Lab Meeting Held on 2018-01-29
summary: MRL direction, ideas for research, and miscellaneous
tags: [dev diaries, crypto, research]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<sarang\></strong> Let us begin  
<strong>\<suraeNoether\></strong> howdy everyone\!  
<strong>\<suraeNoether\></strong> maybe we should ping people  
<strong>\<endogenic\></strong> vtnerd smooth fluffypony othe stoffu knaccc ArticMine kenshi84 pigeons gingeropolous dEBRUYNE  
<strong>\<endogenic\></strong> :P  
<strong>\<endogenic\></strong> ferretinjapan  
<strong>\<endogenic\></strong> silur (absent?)  
<strong>\<endogenic\></strong> hyc  
<strong>\<endogenic\></strong> endogenic  
<strong>\<suraeNoether\></strong> fluffypony luigi1111 andytoshi anonimal dEBRUYNE endogenic ErCiccione gingeropolous hyc vtnerd smooth othe stoffu silur ArticMine kenshi84 pigeons john\_alan medusa Mouchicc nioc unknownids  
<strong>\* andytoshi</strong> breakfast meeting, afk, sorry  
<strong>\<anonimal\></strong> Hello  
<strong>\<ErCiccione\></strong> Hi\! (thanks for the ping)  
<strong>\<suraeNoether\></strong> So, today I want Sarang and I to give an account of our experience at BPASE18, and then talk about the January roadmap  
<strong>\<hyc\></strong> hey  
<strong>\<suraeNoether\></strong> and our overall work for this year  
<strong>\<suraeNoether\></strong> if anyone is curious, I live-tweeted the majority of talks at BPASE  
<strong>\<sarang\></strong> Several talks highlighted topics relating to smart contracts that have little relevance to us  
<strong>\<sarang\></strong> However, there were talks on SPECTRE/PHANTOM and bulletproofs that were well presented and well received  
<strong>\<sarang\></strong> among many others  
<strong>\<sarang\></strong> We’ll be able to integrate a brand-new batch verification technique for bulletproofs  
<strong>\<suraeNoether\></strong> yes, that was big news  
<strong>\<suraeNoether\></strong> PHANTOM is sort of an interesting layer on top of SPECTRE, which leads to probabilistically picking only honest blocks, interesting analysis led to that  
<strong>\<suraeNoether\></strong> also, it turns out bulletproofs are crazy adaptible  
<strong>\<suraeNoether\></strong> like, you can put SHA256 into a bulletproof and proof that you know the pre-image to a hash  
<strong>\<suraeNoether\></strong> without revealing the pre-image  
<strong>\<suraeNoether\></strong> etc  
<strong>\<suraeNoether\></strong> very interesting stuff  
<strong>\<sarang\></strong> Mhmm, it’s a general tool for arithmetic circuits  
<strong>\<sarang\></strong> Anyone else working on fun research they wish to share as well?  
<strong>\<hyc\></strong> very cool… all of this raises a question in my mind - when do we consider “new” technology to be “mature” ?  
<strong>\<hyc\></strong> we’re taking extra care integrating BPs because they’re “new”  
<strong>\<anonimal\></strong> When we stop saying sha256 ;)  
<strong>\<anonimal\></strong> How does sha384/512 fit into the picture?  
<strong>\<sarang\></strong> Maybe when people stop being excited about it and consider it just a tool?  
<strong>\<suraeNoether\></strong> that’s a good question hyc  
<strong>\<suraeNoether\></strong> here’s the thing: our current impelmentation of bullet proofs is specifically a range proof implementation  
<strong>\<suraeNoether\></strong> iirc  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> so in order ot make it to other things, we need to make new implementations  
<strong>\<suraeNoether\></strong> so the failure model or threat model for each implementation will be different  
<strong>\<sarang\></strong> Not necessarily. The security model for ACs is pretty well defined  
<strong>\<sarang\></strong> We just happen to only be using these for range proof  
<strong>\<suraeNoether\></strong> the reason it is so important to validate our implemenation of BP-range-proofs is because if that breaks, then people can mint money. but if we implement some other NIZK proof of knowledge with a BP, we may not need to be so nervous, because the failure of the new implementation may be small in scale, as opposed to “free-mint-ALLTHEMONEY” sort of failure model  
<strong>\<suraeNoether\></strong> sarang yeah: for a general AC the implementation analysis i usppose will boil down to analyzing the AC  
<strong>\<sarang\></strong> yes  
<strong>\<hyc\></strong> ok, makes sense. thanks surae  
<strong>\* suraeNoether</strong> thumbs up  
<strong>\<suraeNoether\></strong> In addition to that, gmaxwell had a brilliant idea on bug bounties  
<strong>\<suraeNoether\></strong> but it only kind of works for their implementation of libsecp256k1, because they have a super robust test suite  
<strong>\<suraeNoether\></strong> the idea is to put a bug bounty up for altering the test suite in a way such that all current tests <em>still pass</em> but you have uploaded some sort of other test that fails despite that  
<strong>\<suraeNoether\></strong> so if I can put a new test into the test suite, call it D, and the test suite already has tests A, B, and C… if D is a failure but A,B,C still pass, then you essentially found a new test and a new weakness, so boom, you get the bug bounty  
<strong>\<suraeNoether\></strong> not super helpful in our situation because our test suites are not yet robust  
<strong>\<suraeNoether\></strong> but it’s an interesting model of bug bounties and unit tests  
<strong>\<sarang\></strong> Perhaps we should move on to the roadmap to allow plenty of time to discuss?  
<strong>\<suraeNoether\></strong> yep  
<strong>\<suraeNoether\></strong> So, here’s the deal  
<strong>\<suraeNoether\></strong> well one of many deals  
<strong>\<suraeNoether\></strong> sarang and I are sort of trying to figure out which direction MRL should go over the next year  
<strong>\<suraeNoether\></strong> and we need input. Other htan writing up the Monero Standards, and finishing the multisig paper… we sort of suffer a problem where work is done in jerks and starts  
<strong>\<sarang\></strong> It’s partly the unfortunate nature of research  
<strong>\<suraeNoether\></strong> like a few weeks will go by with apparently not too much to get done, then BOOM all of a sudden it’s time to implement and review bulletproofs or BOOM, rtrs ringct or whatever  
<strong>\<sarang\></strong> I mean, I want to continue a deeper investigation of DAG structures and consensus models  
<strong>\<suraeNoether\></strong> and that makes it feel like we’re <em>reactive</em> instead of proactive  
<strong>\<sarang\></strong> I think that will become increasingly more important  
<strong>\<suraeNoether\></strong> yeah, i do too  
<strong>\<suraeNoether\></strong> i’ve been working on an adaptable population-driven model of a cryptocurrency network to assess dynamics and how various algorithms affect them. for example, if we want to study a different consensus model or a different PoW algorithm or if we want to study how difficulty metrics respond to changes in hashrate, etc  
<strong>\<suraeNoether\></strong> so we can model long-term scaling issues on a controlled simulation  
<strong>\<sarang\></strong> Smaller things include broader implementation of curve/scalar optimizations, but that’s just housekeeping stuff  
<strong>\<suraeNoether\></strong> I also have been working on SPECTRE and finishing up the multisig paper  
<strong>\<sarang\></strong> Developing outreach curricula is a non-research side of things, of course, but I believe still important for this group  
<strong>\<suraeNoether\></strong> which, btw, after speaking with pietr wuille in Zurich and Stanford, two separate routes an attacker could take have been made clear to me. One of them our code already accounts for. The other is something I need to speak with luigi1111 and moneromooo about  
<strong>\<sarang\></strong> In what regard?  
<strong>\<hyc\></strong> multisig?  
<strong>\<suraeNoether\></strong> yes for multisig i mean  
<strong>\<suraeNoether\></strong> there is a simple-ish fix too  
<strong>\<suraeNoether\></strong> it’s not a huge deal, but it’s a big enough deal that I want to speak in private with folks about it before proceeding  
<strong>\<gingeropolous\></strong> would it be worth investing time in a network simulator? i know there are various blockchain / p2p sims out there, and it might be more of a technical issue (more admin than research) …  
<strong>\<sarang\></strong> Depends on what we want to model  
<strong>\<suraeNoether\></strong> gingeropolous: that’s sort of what i’m coding. i’m dissatisfied with several of the other pieces of simulation software out there  
<strong>\<hyc\></strong> are you talking open source projects that we can tweak to suit ourselves?  
<strong>\<suraeNoether\></strong> of course  
<strong>\<hyc\></strong> ^ to ginger actually  
<strong>\<suraeNoether\></strong> oh i see what you mean hyc  
<strong>\<suraeNoether\></strong> yeah my mistake  
<strong>\<gingeropolous\></strong> im imagining something public facing, with a GUI so an average user can go “oh lets drop the fee to 0.0001 and see what happens”  
<strong>\<gingeropolous\></strong> some web interface  
<strong>\<suraeNoether\></strong> ah so gingeropolous  
<strong>\<gingeropolous\></strong> but that could be phase 2  
<strong>\<suraeNoether\></strong> forget about fees, because i’m oinly looking at block dynamics  
<strong>\<sarang\></strong> You’d need a much deeper understanding of how nodes/users respond to such factors though?  
<strong>\<suraeNoether\></strong> not transaction dynamics  
<strong>\<suraeNoether\></strong> but the point is to eventually build it up to do that sort of thing  
<strong>\<gingeropolous\></strong> cool  
<strong>\<hyc\></strong> quite a lot of variables to model  
<strong>\<suraeNoether\></strong> animate it with ggplot or something to make pretty videos  
<strong>\<suraeNoether\></strong> hyc yep, it’s a very general model, makes it suitable for arbitrary plug-n-play sort of analyses  
<strong>\<suraeNoether\></strong> but back to the roadmap  
<strong>\<suraeNoether\></strong> i guess what i’m asking is:  
<strong>\<suraeNoether\></strong> what do people want to see out of MRL over the next 6 months?  
<strong>\<suraeNoether\></strong> other than the completed multisig paper  
<strong>\<sarang\></strong> To be honest, I don’t think the broader Monero community really has specific opinions on research directions, if that’s what you mean  
<strong>\<suraeNoether\></strong> hyc you are never opinion-less  
<strong>\<hyc\></strong> lol  
<strong>\<hyc\></strong> All the things you already outlined sound like important goals to me. some of it sounds like we need more people.  
<strong>\<moneromooo\></strong> Modelling of spent output age. Take real distribution since last release, subtract the distribution we use, get the real distribution. See if it matches miller et al.  
<strong>\<hyc\></strong> “get the real distribution” —\> how?  
<strong>\<moneromooo\></strong> Then try to do that at several historical times, every month maybe. And then deduce a formula to vary gamma function over time to use a new fake outdistribution.  
<strong>\<moneromooo\></strong> By subtracting the fake outs distribution from the real+fake one.  
<strong>\<moneromooo\></strong> May or may not be good enough, I don’t know.  
<strong>\<suraeNoether\></strong> moneromooo: if we can get a bayesian estimate that updates each hard fork, that’d be great, but it requires being able to “unmask” transactions to see their real spendable output, or to base the estimate on transactions that have already been “unmasked”, or to base the estimate on another currency. Each of these have obstacles, obviously  
<strong>\<suraeNoether\></strong> we need some ground truth underlying data to make an estimate, and monero doesn’t really allow for that  
<strong>\<ErCiccione\></strong> The community is pushing a lot the “fee are too high” thing and i feel will be worst with time passing. Is it possible to produce some documentation to instruct people about how Monero fees work and what are the plans for the future on this matter?  
<strong>\<moneromooo\></strong> I was suggesting deducing the real outs distribution.  
<strong>\<ErCiccione\></strong> i also agree with hyc, er should search fore more researchers  
<strong>\<sarang\></strong> I hear gmaxwell is unattached =p  
<strong>\<moneromooo\></strong> This would be assuming all txes since last release use our fake outs distribution, though, which mymonero might not. Damn.  
<strong>\<hyc\></strong> to some extent, that’s all good news - it means the system is no longer analyzable.  
<strong>\<dEBRUYNE\></strong> ErCiccione: I wrote a blog about it, you can link that  
<strong>\<suraeNoether\></strong> so, ErCiccione: yes, fees are an important part of the discussion around bulletproofs. you are corredct that we should at least put out a statement  
<strong>\<suraeNoether\></strong> hyc: without access to KYC/AML data from an exchange, anyway :D  
<strong>\<suraeNoether\></strong> i suppose we could ask for some sanitized data from one of the exchanges…  
<strong>\<suraeNoether\></strong> actually that’s the first time that i’ve been hopeful about deducing true age distribution  
<strong>\<suraeNoether\></strong> but here’s the REAL problem  
<strong>\<ferretinjapan\></strong> does the current research on multisig cover more complex things like assurance contracts? I think people would definitely be keen to help fund research in enabling those types of things.  
<strong>\<suraeNoether\></strong> ferretinjapan: the current paper will not cover that except lightly, but i would loooove to write up a document on “applications of multisig in nearly-smart contracts.”  
<strong>\<suraeNoether\></strong> let’s say there’s a really massive anonymity set: the probability of picking any one of them out for usage in a ring is really really small  
<strong>\<ferretinjapan\></strong> Because that could mean 100% decentralised FFS :)  
<strong>\<suraeNoether\></strong> and if you pulled randomly from the whole blockchain…  
<strong>\<suraeNoether\></strong> then the true output you are signing with <em>probably</em> hasn’t been used in a signature before  
<strong>\<suraeNoether\></strong> and more people got into monero recently rather than in 2014  
<strong>\<suraeNoether\></strong> so the output being spent is <em>probably</em> the youngest one  
<strong>\<hyc\></strong> true  
<strong>\<suraeNoether\></strong> and this will <em>always</em> be the case, unless we make wallet software actively try to de-anonymize the blockchain and we publish a blacklist of known-spent outputs  
<strong>\<suraeNoether\></strong> or unless we make wallet software that tries to pick as many transactions from “recently” that have not yet been used in any ring signature  
<strong>\<suraeNoether\></strong> another way of looking at this: the first ring signature an output appears in <em>is likely</em> to be the one that actually spends it  
<strong>\<suraeNoether\></strong> it’s not so much a matter of the age of the output  
<strong>\<ErCiccione\></strong> dEBRUYNE: right, i forgot about that, but i still think we should be more informative about fees, i see a lot of confusion in the average user, at least on reddit,  
<strong>\<suraeNoether\></strong> but how many other ring signatures already reference it  
<strong>\<suraeNoether\></strong> ErCiccione: absolutely +1  
<strong>\<suraeNoether\></strong> okay, so fees are going on my list  
<strong>\<suraeNoether\></strong> for analysis and a nice big public explanation, probably drawing heavily on the blog post by dEBRUYNE  
<strong>\<suraeNoether\></strong> speaking of which dEBRUYNE send us all a link :D  
<strong>\<dEBRUYNE\></strong> <https://getmonero.org/2017/12/11/A-note-on-fees.html>  
<strong>\<suraeNoether\></strong> awesome thanks  
<strong>\<dEBRUYNE\></strong> re: spent age of outputs, perhaps we could take a look at other chains as well?  
<strong>\<suraeNoether\></strong> silur has been working on a C implementation of RTRS ringct  
<strong>\<ferretinjapan\></strong> dEBRUYNE, aeon could be a decent model, unless it requires 100% transparency…  
<strong>\<suraeNoether\></strong> dEBRUYNE: that comes with its own set of assumptions. i’m actually (I think) more comfortable asking “how long does an average 50 euro bill stay in someone’s wallet before being spent?” than “bitcoin”  
<strong>\<suraeNoether\></strong> ferretinjapan: aeon suffers the same problem we do i think  
<strong>\<ferretinjapan\></strong> ah  
<strong>\<suraeNoether\></strong> has anyone else been working on anything they want to talk about?  
<strong>\<dEBRUYNE\></strong> ferretinjapan: was more thinking about LTC, BTC  
<strong>\<dEBRUYNE\></strong> suraeNoether: whislt that it true, it may be good for pointers  
<strong>\<ferretinjapan\></strong> yeah, LTC is actually a good one, had a similar mining start to monero.  
<strong>\<suraeNoether\></strong> even if we had a good estimate of true velocity of money, it changes over time so we would need something like a bayesian updating. <https://en.wikipedia.org/wiki/Velocity_of_money>  
<strong>\<suraeNoether\></strong> sarang, do you have anything else you want to chat about?  
<strong>\<ferretinjapan\></strong> suraeNoether, true, but I’d wager that LTC and XMR’s normal distribution after a year is probably very similar. It’s probably clsest you’d get without cracking open monero proper and looking inside.  
<strong>\<sarang\></strong> Assembling the formal audit materials as they become available  
<strong>\<sarang\></strong> I still wish we had a more concrete guideline for if/when/how we’ll do such things in the future  
<strong>\<sarang\></strong> But for now this is a Good Thing  
<strong>\<suraeNoether\></strong> ferretinjapan: you are assuming it’s normal… it isn’t, it’s heavy-tailed and possibly non-unimodal. :D but you are probably correct that LTC would be a better metric than BTC imho  
<strong>\<suraeNoether\></strong> i am curious about one thing  
<strong>\<suraeNoether\></strong> Up to your concerns about opsec/privacy, gimme a +1 if you are currently an undergraduate university student  
<strong>\<ferretinjapan\></strong> yeah, I’m definitely not saying it’s perfect just close-ish compared to the rest of the premined coins out there ;)  
<strong>\<suraeNoether\></strong> ferretinjapan: i agree that litecoin could be a good proxy for monero for estimating otherwise unestimable statistics  
<strong>\<suraeNoether\></strong> i’d also be in favor of doing it for all transparent coins and obtaining a confidence interval  
<strong>\* anonimal</strong> question regarding the MRL over the next 6 months  
<strong>\<anonimal\></strong> I first got in contact with sarang back in late August about kovri work but nothing came of it.  
<strong>\<anonimal\></strong> That then lead to a late October chat about said kovri work but nothing came of it.  
<strong>\<anonimal\></strong> Should I just not count any kovri collaboration from the Noethers? I understand, no hard feelings.  
<strong>\<anonimal\></strong> We simply need more researchers.  
<strong>\<ferretinjapan\></strong> yeah, do some box plots on a couple dozen and you might get a ballpark figure that helps.  
<strong>\<sarang\></strong> anonimal to be honest I didn’t think we’d have so much work with RingCT and BPs occupying time  
<strong>\<suraeNoether\></strong> i think you are right anonimal  
<strong>\<sarang\></strong> It has nothing to do with lack of interest  
<strong>\<suraeNoether\></strong> i recall that contact  
<strong>\<sarang\></strong> but I apologize if it seemed that way  
<strong>\<suraeNoether\></strong> anonimal: is there either an explanatory text or a link or something you would you mind giving us for a look?  
<strong>\<suraeNoether\></strong> depending on exactly what sort of questions you are asking, there may be intersection with other work we are doing  
<strong>\<anonimal\></strong> What explanatory text would you like exactly?  
<strong>\<suraeNoether\></strong> is there a thread someplace that birthed the idea behind kovri?  
<strong>\<anonimal\></strong> Oh. Well those IRC logs were unfortunately pasted to a now-defunct website. I can give TL;DRs if needed though.  
<strong>\<anonimal\></strong> Ideally our website/docs would explain everything you need to know but rehrar and I are still WIP with them.  
<strong>\<suraeNoether\></strong> ok, so i’ll devote a few hours this week to learning about kovri to see <em>whether</em> i can help  
<strong>\<suraeNoether\></strong> keeping in mind the halting problem  
<strong>\<suraeNoether\></strong> (can never really know how long something is going to take until you do it).  
<strong>\<anonimal\></strong> How realistic/effective would a noether tweetnacl review be?  
<strong>\<anonimal\></strong> tweetnacl has had a lot of eyes  
<strong>\<sarang\></strong> You want additional eyes on it?  
<strong>\<anonimal\></strong> (relatively speaking, imo)  
<strong>\<anonimal\></strong> No, just asking your professional opinion on if that would be a cost-effective use of your time.  
<strong>\<anonimal\></strong> IIRC fluffypony wanted teetnacl in monero as some point. I’m not sure where that conversation ended though.  
<strong>\<selsta\></strong> some other “news”. Sumokoin team member confirmed me today that they will donate to the BP audit with some of the premine money. i don’t really believe it yet though lol  
<strong>\<anonimal\></strong> Crypto++ has recently implemented tweetnacl and, once they implement a crypto++-friendly interface, kovri will drop ref10 supercop for tweetnacl.  
<strong>\<suraeNoether\></strong> let me learn a little about tweetnacl, and then i can assess wheter going deeper will be a rabbit hole or … not  
<strong>\<anonimal\></strong> ok  
<strong>\<suraeNoether\></strong> i haven’t tried to ignore it  
<strong>\<suraeNoether\></strong> squeaky wheels and all that  
<strong>\<suraeNoether\></strong> i’m curious about how it works  
<strong>\<suraeNoether\></strong> but i don’t want to go on a two month bender learning a new tech while current projects languish either  
<strong>\<suraeNoether\></strong> i think hiring an additional person would be fantastic, for the record  
<strong>\<sarang\></strong> Well it does the basic ed25519 operations suraeNoether as well as hashing operations  
<strong>\<suraeNoether\></strong> we could get a mathjobs.org employer account and put out a <em>real</em> call for applications  
<strong>\<suraeNoether\></strong> sarang: well that’s nice  
<strong>\<suraeNoether\></strong> ok, anonimal thank you so much for bringing this up  
<strong>\<suraeNoether\></strong> one hard part about this job  
<strong>\<sarang\></strong> yes indeed  
<strong>\<anonimal\></strong> You’re welcome. I’m just really excited to finally get to use it.  
<strong>\<suraeNoether\></strong> is that everyone has their personal pet project they want to see analyzed, some of them are important like multisig and kovri and some not so much, and so it’s difficult to figure out where priorities should go to avoid context-switching, etc  
<strong>\<suraeNoether\></strong> sometimes it feels like no one knows what job sarang and i have. :P  
<strong>\<suraeNoether\></strong> we need a suresh noether  
<strong>\<suraeNoether\></strong> Okay, well  
<strong>\<anonimal\></strong> I think this tweetnacl business would come at the end of 6 months if even within the next 6 months. Too many other priorities imho  
<strong>\<suraeNoether\></strong> any other concerns, questions, gentle or not so gentle priority nudges folks want to bring up?  
<strong>\<sarang\></strong> If anything I’d like to devote time to a review of existing analyses of tweetnacl anonimal  
<strong>\<sarang\></strong> to at least get a better sense of its current place  
<strong>\<anonimal\></strong> ok awesome  
<strong>\<dEBRUYNE\></strong> \<suraeNoether\> we could get a mathjobs.org employer account and put out a <em>real</em> call for applications \<= I don’t think this will be efficient  
<strong>\<dEBRUYNE\></strong> Preferably you need someone that already has a passion for Monero  
<strong>\<ferretinjapan\></strong> I’ll just say you guys are doing a great job keeping up with all these moving targets :)  
<strong>\<suraeNoether\></strong> dEBRUYNE: true  
<strong>\<suraeNoether\></strong> thanks ferretinjapan  
<strong>\<suraeNoether\></strong> oh my god tweetnacl is kind of crazy, i like it …just reading a quick description  
<strong>\<suraeNoether\></strong> i love the idea of a hyper compact auditable li-berry  
<strong>\<anonimal\></strong> +1  
<strong>\<sarang\></strong> Yeah the key is auditable  
<strong>\<suraeNoether\></strong> well, we probably can’t hire andytoshi out from under blockstream. :P  
<strong>\<suraeNoether\></strong> or rather, i’d rather not attempt that sort of game  
<strong>\<suraeNoether\></strong> i’d rather find someone who is very interested in monero and may be late grad school  
<strong>\<suraeNoether\></strong> hmm  
<strong>\<suraeNoether\></strong> i can construct a call for applications e-mail and send it to a few specific departments that are crypto + CS heavy in their math programs  
<strong>\<ErCiccione\></strong> suraeNoether: can you make a post somwhere public with the skills you guys need from a researcher? so i can directly link that to people who may be interested  
<strong>\<suraeNoether\></strong> yeah, i will make the call for applications public, probably, ErCiccione  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<suraeNoether\></strong> I am probably going to hold off on that for at least two weeks, though  
<strong>\<ErCiccione\></strong> ok thanks  
<strong>\<suraeNoether\></strong> to think about what it is we will need 6 months from now  
<strong>\<suraeNoether\></strong> in a new researcher  
<strong>\<suraeNoether\></strong> it’s a tough question, and if anyone has any thoughts, shoot me a line at <suraeNoether@gmail.com>  
<strong>\<ErCiccione\></strong> ok, so, in case, will directly give your contact for now  
<strong>\<suraeNoether\></strong> okay, so without further ado, I suppose we can bid adieu on this meeting.  
<strong>\* suraeNoether</strong> cringes  
<strong>\<anonimal\></strong> Thanks noethers, thanks everyone.  
<strong>\<ErCiccione\></strong> thank you for the updates guys, and awesome job as always :)  
<strong>\<ferretinjapan\></strong> same ^
