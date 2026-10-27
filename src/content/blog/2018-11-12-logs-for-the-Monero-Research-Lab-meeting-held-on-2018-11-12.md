---
title: Logs for the Monero Research Lab Meeting Held on 2018-11-12
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> howdy everyone\!  
<strong>\<nioc\></strong> meow  
<strong>\<OpenSorceress\></strong> :D  
<strong>\<sarang\></strong> hiyo  
<strong>\<TheFuzzStone\[m\]\></strong> Sup\!  
<strong>\<rehrar\></strong> hiyo  
<strong>\<rehrar\></strong> …to quote sarang  
<strong>\<suraeNoether\></strong> so, let’s flip the usual order of the meeting to allow for questions at the beginning  
<strong>\<suraeNoether\></strong> i like that  
<strong>\<suraeNoether\></strong> in fact, i’m going to call THAT the new “usual order”  
<strong>\<suraeNoether\></strong> so, the agenda today is 1) questions, 2) sarang’s research this week and last, 3) mine, and 4) any other project discussion that’s remotely relevant to research  
<strong>\<sarang\></strong> roger  
<strong>\<suraeNoether\></strong> so, someone give me and sarang your top two questions :D  
<strong>\<nioc\></strong> any updates on Konferemco preparations?  
<strong>\<rehrar\></strong> I should have a logo and branding guidelines today  
<strong>\<rehrar\></strong> in regards to MRL, where are we in the churn and privacy formalizations?  
<strong>\<rehrar\></strong> although I assume this will be talked about with your report of the week suraeNoether  
<strong>\<suraeNoether\></strong> that is precisely the case  
<strong>\<suraeNoether\></strong> i’m in the midst of getting hard numbers for a timing for a practical attack  
<strong>\<suraeNoether\></strong> sarang and i have discovered an anonymity metric that could give us a guideline for “how rapidly we need to chagne our ring size with respect to blockchain size to maintain our current levels of anonymity.”  
<strong>\<suraeNoether\></strong> this is a very useful metric, but it’s dangerous to misinterpret it  
<strong>\<sarang\></strong> Let us shift that to the later agendum  
<strong>\<suraeNoether\></strong> so we’re avoiding making formal proclamations about it, but we are going to use it as a rough guideline for future ring size increases  
<strong>\<suraeNoether\></strong> agreed  
<strong>\<suraeNoether\></strong> nioc our conference organizer has been checking out a few alternative venues, and we have already identified some vendors for things like catering  
<strong>\<sarang\></strong> I have a question… how the hell do I build the dalek bulletproof rust implementation for timing testing??\!?\!?\!?\!  
<strong>\<sarang\></strong> I know jack shiz about rust  
<strong>\<suraeNoether\></strong> that’s an excellent question that occurred to me yesterday afternoon\!  
<strong>\<sarang\></strong> they claim to be bonkers fast, even compared to libsecp256k1 (which seems nutso to me)  
<strong>\<suraeNoether\></strong> they are claiming some mad speed gainz on top of your already mad speed gainz  
<strong>\<sarang\></strong> They don’t have batch verification yet tho  
<strong>\<sarang\></strong> (it’s on their issue list)  
<strong>\<suraeNoether\></strong> jfc  
<strong>\<sarang\></strong> So I want to run timing tests myself to see  
<strong>\<suraeNoether\></strong> if that’s the case, then… man that implementation is bonker fast like what-what  
<strong>\<sarang\></strong> I don’t think they’re lying, but I’m also naturally skeptical  
<strong>\<sarang\></strong> I don’t find it terribly relevant since we’re already pretty fast  
<strong>\<suraeNoether\></strong> i suspect that bulletproofs are going to benefit from 40 years of optimizations in linear algebra and ECC very very quickly  
<strong>\<sarang\></strong> and any changes specific to underlying curve architecture aren’t useful for us ATM  
<strong>\<rehrar\></strong> sarang: what if it’s so fast it can reverse the blackchain continuum?  
<strong>\<rehrar\></strong> somethign to look into  
<strong>\<sarang\></strong> Ah yes, the chain shrinks over time  
<strong>\<sarang\></strong> negachain  
<strong>\<suraeNoether\></strong> the blackchain continuum hypothesis, by tom clancy  
<strong>\<suraeNoether\></strong> or dan brown  
<strong>\<sarang\></strong> Anyway, it won’t build for me, but I’ll verify timings once I get it figured out  
<strong>\<rehrar\> \<sarang\></strong> Ah yes, the chain shrinks over time \<— it will give extra space to your computer when it goes negative  
<strong>\<sarang\></strong> However, they also have ideas for non-power-of-2 stuff, which was on the back burner for me  
<strong>\<sarang\></strong> if it proves useful for them in a way that translates to us, great  
<strong>\<suraeNoether\></strong> nioc i believe we already have enough funding availalbe to put a deposit down on a location, and I would like to do that before the end of 2018. email invitations to speakers will be start being setn out this week  
<strong>\<sarang\></strong> nice  
<strong>\<sarang\></strong> Also our other conference FFS (Stanford) was funded recently, so many thanks on that front  
<strong>\<suraeNoether\></strong> in general: thank you to all contributors who make Monero Research Lab a funded thing  
<strong>\<sarang\></strong> suraeNoether and I will learn next month if either of us will be speaking there  
<strong>\<sarang\></strong> anyway, other questions for us?  
<strong>\<rehrar\></strong> ne  
<strong>\<sarang\></strong> In the absence of further questions, we can talk recent research  
<strong>\<sarang\></strong> This past week, I did two events in Chicago  
<strong>\<sarang\></strong> one was a hands-on Monero development workshop  
<strong>\<sarang\></strong> the other was a more general talk on privacy tech  
<strong>\<sarang\></strong> both videos are on YouTube, linked from the Monero Moon posting  
<strong>\<sarang\></strong> thanks to the Chicago Bitcoin and Open Blockchains group for hosting me  
<strong>\<suraeNoether\></strong> Did you have a good time? think you’ll do something like that again?  
<strong>\<sarang\></strong> Yeah, I think it was very valuable  
<strong>\<sarang\></strong> They had good turnout and excellent questions  
<strong>\<sarang\></strong> I really like the workshop idea especially  
<strong>\<sarang\></strong> Aside from that work, I did a good amount of lit review to support suraeNoether’s work (discussed shortly) on graph matchings, which was an extension of some earlier analysis we did on spent output analysis  
<strong>\<suraeNoether\></strong> what was the demographic of the crowd like?  
<strong>\<sarang\></strong> The workshop was smaller (due to scheduling shenanigans for some participants) but had folks interested in math/CS/development  
<strong>\<sarang\></strong> The talk had a good mix of technical folks and well-wishers  
<strong>\<sarang\></strong> It’d be cool to find a way to host an interactive online workshop  
<strong>\<OpenSorceress\></strong> what would that entail?  
<strong>\<sarang\></strong> Well, one set of tasks I had them do was use a simple Python ed25519 library to build some constructions  
<strong>\<sarang\></strong> like Pedersen commitments and Schnorr sigs  
<strong>\<rehrar\></strong> lol, love the name OpenSorceress. That’s funny.  
<strong>\<sarang\></strong> So being able to do video w/ slides for introductory work would be good  
<strong>\<sarang\></strong> as well as interactive stuff to help the participants write code  
<strong>\<sarang\></strong> Then we did some basic RPC stuff  
<strong>\<OpenSorceress\></strong> like remote pairing?  
<strong>\<sarang\></strong> OpenSorceress: some situation where the workshoppers could do in-browser code, perhaps, and then let me assist interactively if needed  
<strong>\<sarang\></strong> I don’t know if there is such a thing already  
<strong>\<sarang\></strong> just spitballing here  
<strong>\<suraeNoether\></strong> that is pretty awesome, sarang\! i’m glad it’s online.  
<strong>\<OpenSorceress\></strong> there is  
<strong>\<sarang\></strong> orly  
<strong>\<OpenSorceress\></strong> yeppers  
<strong>\<OpenSorceress\></strong> -\> floobits pops to mind  
<strong>\<sarang\></strong> Cool, let’s discuss after meeting  
<strong>\<OpenSorceress\></strong> :) ok  
<strong>\<sarang\></strong> I’ve also been working to integrate stealth addresses into the RTRSRingStringRuffCT optimizations  
<strong>\<sarang\></strong> and other minor tasks, etc  
<strong>\<suraeNoether\></strong> allrighty  
<strong>\<sarang\></strong> How about you suraeNoether? The graph matching, perhaps  
<strong>\<suraeNoether\></strong> well, i’ve been doing the churn and graph theoretic stuff  
<strong>\<suraeNoether\></strong> as I mentioned earlier, sarang and I have stumbled upon a class of anonymity metrics for graphs such as ours, and this will give us a quantitative basis for maintaining at least our current levels of anonymity as the blockchain gets larger  
<strong>\<sarang\></strong> It’s worth noting that this isn’t even new analysis  
<strong>\<sarang\></strong> But a really clever interpretation of older stuff that suraeNoether came up with  
<strong>\<sarang\></strong> which is always great in math  
<strong>\<suraeNoether\></strong> correct, in fact several of these were proposed right around the time Bitcoin was proposed, which amuses me  
<strong>\<suraeNoether\></strong> 2007, 2008, 2009  
<strong>\<rehrar\></strong> so are you saying that as the blockchain gets larger, anonymity decreases?  
<strong>\<suraeNoether\></strong> well, consider the following situation  
<strong>\<suraeNoether\></strong> let’s say something ridiculous like “tomororw Monero goes back to ring size 1”  
<strong>\<sarang\></strong> It’s important to note that “anonymity” here means “anonymity according to a very specific metric formulation that may or may not correspond to a particular threat model”  
<strong>\<suraeNoether\></strong> what happens? a bunch of blocks are added to the monero blockchain, all of which are totally linkable  
<strong>\<suraeNoether\></strong> this is an edge case of the following idea:  
<strong>\<notmike\></strong> Even I could link them\!  
<strong>\<suraeNoether\></strong> heh  
<strong>\<suraeNoether\></strong> if we take our present system and add a bunch of non-anonymous stuff, we aren’t improving our anonymity  
<strong>\<suraeNoether\></strong> in fact, we are decreasing our anonymity, by essentially diluting our nice big fat blockchain filled with fat ring sigs with non-anonymous data  
<strong>\<sarang\></strong> At their heart, these metrics use numbers of matchings to relate to some idea of anonymity  
<strong>\<sarang\></strong> a graph matching is a possible global spend history, of which there will be many  
<strong>\<sarang\></strong> Think of it as being a guess about true spends that’s at least \_consistent\_, but of course not provable  
<strong>\<sarang\></strong> My current view of this type of analysis is that, being only a heuristic that could be combined with things like output age, it provides the same types of plausible deniability that ring sigs have always offered  
<strong>\<sarang\></strong> however  
<strong>\<sarang\></strong> what suraeNoether was saying about it being useful to examine proposed changes is a good idea  
<strong>\<sarang\></strong> So you can say “if we increase ring size to X given usage patterns Y, this metric implies that anonymity gets better”  
<strong>\<sarang\></strong> it’s not possible to say things like “anonymity gets Z% better” though  
<strong>\<suraeNoether\></strong> so, to answer your question rehrar: the Edman anonymity level is \*negatively\* related to overall graph size and \*positively\* related to ring size. so we can say “okay, if our blockchain was \*this\* big, how big of a ring size would we need to have similar EAL to today?”  
<strong>\<suraeNoether\></strong> the fact of the matter is, though, it very slowly changes with respect to graph size at these levels  
<strong>\<rehrar\></strong> got it  
<strong>\<suraeNoether\></strong> to maintain an EAL similar ot what we have today, the blockchain could be 10x larger  
<strong>\<suraeNoether\></strong> and we might need a ring size of like 15 at that point, or something like that, to make it equal exactly  
<strong>\<sarang\></strong> I have the same types of broad, non-mathematical questions about global anonymity that I do about rings in general  
<strong>\<sarang\></strong> If there are 2^64 possible spend histories, is that good enough for our threat models? What if there were only 2^4? I don’t know  
<strong>\<suraeNoether\></strong> sarang actually we can sort of answer that question quantitatively  
<strong>\<sarang\></strong> Well, for some threat models, “good enough” means “enough reasonable doubt to avoid someone getting in trouble for a spend history they weren’t actually involved in”  
<strong>\<sarang\></strong> and that depends on how your legal system works  
<strong>\<sarang\></strong> What types were you considering?  
<strong>\<suraeNoether\></strong> the question an attacker needs to answer is “out of all possible spend histories with a likelihood greater than some C of being the true spend history, what % of these is a specific edge traced?” for example, if in 95% of all plausible and likely histories, edge e sending monero from address X to address Y is included in the matching, we conclude that edge e is the true spender.  
<strong>\<suraeNoether\></strong> we may be able to quantify our security on an individual level that way, and see how it is sensitive to game parameters  
<strong>\<suraeNoether\></strong> anyway, 100% of my MRL attention is on this paper right now  
<strong>\<sarang\></strong> A lot of this (not just graph metrics) seems to be chasing after specific heuristics (some unknown) without a real fundamental idea of what guarantees we want to be able to offer  
<strong>\<sarang\></strong> Subtly moving from “not provable spending” to “not heuristically-guessable spending” seems like a generally good idea, but it’s like swiss cheese  
<strong>\<suraeNoether\></strong> all of my work so far is highlighting, essentially, the urgency with which we need to replace ring signatures  
<strong>\<sarang\></strong> true  
<strong>\<suraeNoether\></strong> and the fundamental problem with using KYC exchanges  
<strong>\<sarang\></strong> Well, those aren’t going anywhere  
<strong>\<sarang\></strong> and if anything, more people will move to them  
<strong>\<hyc\></strong> as opposed to DEXs?  
<strong>\<sarang\></strong> Do you know of any usable ones?  
<strong>\<hyc\></strong> I assume Bisq works  
<strong>\<gingeropolous\></strong> bisq .. ?  
<strong>\<hyc\></strong> haven’t used it  
<strong>\<rehrar\></strong> question on replacing ring signatures…is there any sort of tech (eevn un battle tested) that exists at the moment?  
<strong>\<sarang\></strong> nor have I  
<strong>\<sarang\></strong> rehrar: no  
<strong>\<suraeNoether\></strong> i hear bisq is good, but i haven’t used it yet  
<strong>\<suraeNoether\></strong> rehrar: yes and no  
<strong>\<sarang\></strong> not without sacrificing trust  
<strong>\<suraeNoether\></strong> or speed/efficiency  
<strong>\<sarang\></strong> correct  
<strong>\<suraeNoether\></strong> there are some trustless set-ups that are unreasonably slow  
<strong>\<hyc\></strong> if we could do cross-chain atomic swaps with BTC that would eliminate a huge chunk of exchange usecases  
<strong>\<suraeNoether\></strong> or big  
<strong>\<sarang\></strong> IMO the goal of the graph matching analysis should be to at least get an order-of-magnitude estimate on Monero global spend histories  
<strong>\<suraeNoether\></strong> hyc that is 100% correct, and we have all the theoretical framework for that except SPV at this point, but the recent nipopow paper and another recent paper may fix that too  
<strong>\<sarang\></strong> I’m not convinced this provides an adversary with remarkably more actionable data than existing heuristics  
<strong>\<OpenSorceress\></strong> how would you go about sussing that out?  
<strong>\<sarang\></strong> And while it should push us toward better non-ring-sig solutions, I also don’t want to FUD our users in the same way that all the other Monero tracking papers have  
<strong>\<suraeNoether\></strong> it should provide literally the same amount of data, just one is a global approach and one is a txn-by-txn approach  
<strong>\<sarang\></strong> OpenSorceress: run the analysis on at least a portion of the chain  
<strong>\<sarang\></strong> suraeNoether: implementing nipopow is a huge undertaking  
<strong>\<suraeNoether\></strong> yes  
<strong>\<sarang\></strong> suraeNoether: what do you see as the goal of the analysis?  
<strong>\<suraeNoether\></strong> provide actionable advice for the monero community on how to mitigate the worst known traceability chainalsysis attack. ultimately  
<strong>\<sarang\></strong> in terms of ring size specifically?  
<strong>\<sarang\></strong> given that the EAL is sensitive to it?  
<strong>\<suraeNoether\></strong> not necessarily, although that is presently a facet of the analysis, yeah.  
<strong>\<suraeNoether\></strong> i mean, at this point, I think that further increases in ring size without order-of-magnitude increases… i’m not convinced of their efficacy, but i can’t say either way at this point  
<strong>\<sarang\></strong> What’s the takeaway from all of this, for the folks in this meeting?  
<strong>\<suraeNoether\></strong> research is ongoing into the matter  
<strong>\<suraeNoether\></strong> progress is being made in terms of making actionable recommendations to the community  
<strong>\<suraeNoether\></strong> but we aren’t announcing them yet, until after more consideration  
<strong>\<suraeNoether\></strong> i’m not sure what you mean  
<strong>\<rehrar\></strong> good enough for me  
<strong>\<sarang\></strong> Do you view this a fundamentally new form of analysis that provides adversaries with a lot of new damaging information?  
<strong>\<sarang\></strong> (as opposed to, for example, the closed-set attack, which really gave marginal information)  
<strong>\<suraeNoether\></strong> there is no practical way i can answer that question, sarang  
<strong>\<sarang\></strong> ok  
<strong>\<suraeNoether\></strong> i’m telling you it’s the worst-known traceability attack  
<strong>\<suraeNoether\></strong> i’m estimating how bad it is  
<strong>\<suraeNoether\></strong> that’s my job right now  
<strong>\<sarang\></strong> ok  
<strong>\<sarang\></strong> Anything else of note to share from your side regarding recent stuff?  
<strong>\<suraeNoether\></strong> not with respeect to MRL, no  
<strong>\<sarang\></strong> kk  
<strong>\<suraeNoether\></strong> and i have an appointment i need to get to you guys, so.. peach out  
<strong>\<suraeNoether\></strong> imagine whirled peas  
<strong>\<suraeNoether\></strong> etc  
<strong>\<sarang\></strong> np  
<strong>\<suraeNoether\></strong> love you guys \*smooches\*  
<strong>\<sarang\></strong> Anyone else wish to bring up something they’ve been working on?  
<strong>\<sarang\></strong> crickets\!  
<strong>\<hyc\></strong> if you’re bothered by blockchain sync speed, get your hands on Optane SSDs  
<strong>\<sarang\></strong> yeah?  
<strong>\<OpenSorceress\></strong> Optane SSDs?  
<strong>\<endogenic\></strong> SSDs?  
<strong>\<sarang\></strong> Ds?  
<strong>\<endogenic\></strong> ??  
<strong>\<OpenSorceress\></strong>  
<strong>\<sarang\></strong> I store the chain in RAM  
<strong>\<hyc\></strong> yeah <http://www.lmdb.tech/bench/optanessd>  
<strong>\<endogenic\></strong> LOL  
<strong>\<sarang\></strong> I build a new ASIC for each block that gets added  
<strong>\<hyc\></strong> Real Men store the blockchain in RAM :P  
<strong>\<sarang\></strong> Well, I’ll officially adjourn today’s meeting; thanks to all for attending  
<strong>\<sarang\></strong> Next week, same bat-time, same bat-channel  
<strong>\<hyc\></strong> ttyl  
<strong>\<rehrar\></strong> bai
