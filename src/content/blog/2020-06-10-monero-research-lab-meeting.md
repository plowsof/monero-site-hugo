---
title: Logs for the MRL Meeting Held on 2020-06-10
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> OK, just about time to start the meeting  
<strong>\<sarang\></strong> First, greetings\!  
<strong>\<ArticMine\></strong> Hi  
<strong>\<sgp\_\></strong> hello  
<strong>\<Isthmus\></strong> Heya  
<strong>\<sarang\></strong> I suppose we can move to the roundtable, where anyone is welcome to share research of interest  
<strong>\<sarang\></strong> Does anyone want to go first?  
<strong>\<sarang\></strong> If not, I can share a few things  
<strong>\<sarang\></strong> Teserakt has sent me a draft of their analysis of the CLSAG preprint  
<strong>\<monerobux\></strong> Test failed  
<strong>\<sarang\></strong> bad bot  
<strong>\<sarang\></strong> The draft report indicates they did not find any major issues with the construction, but they had some comments and suggestions on the formalization that I'm working to update  
<strong>\<sarang\></strong> This shouldn't result in any changes to the code  
<strong>\<sarang\></strong> Separately from this, I started working on some output merging analysis on the Monero chain  
<strong>\<h4sh3d\[m\]\></strong> Hello  
<strong>\<sarang\></strong> I have preliminary data but am still checking it for a few questions I have  
<strong>\<sarang\></strong> I'll post a plot here, but note that it should not be relied on until checked more thoroughly  
<strong>\<sarang\></strong> <https://usercontent.irccloud-cdn.com/file/EHmFolZV/data\_all.png>  
<strong>\<sarang\></strong> An explanation...  
<strong>\<sarang\></strong> I look for "zero-hop" possible merges, where outputs from the same source transaction appear in separate rings in a later destination transaction, and filter only by post-CT confidential transactions  
<strong>\<sarang\></strong> Then, for each such possible merge, I look at the height difference of the source and destination transaction, and plot them here  
<strong>\<sarang\></strong> The x-axis represents block height difference, and the y-axis is fractional occurrence (note the log scale\!)  
<strong>\<kiwi\_87\></strong> Hi. What you think about interoperability on Monero?  
<strong>\<sarang\></strong> kiwi\_87: one sec  
<strong>\<Isthmus\></strong> 👀  
<strong>\<Isthmus\></strong> Very interesting  
<strong>\<sarang\></strong> <https://usercontent.irccloud-cdn.com/file/UPSZyk6P/data\_1k.png>  
<strong>\<sarang\></strong> Here is the same data, but zoomed (and rescaled) to the low end of the x-axis  
<strong>\<sarang\></strong> Now, these are only possible merges; there's no good ground-truth data set on chain for post-CT confidential transactions  
<strong>\<atoc\></strong> hi  
<strong>\<sarang\></strong> So I'm going to run a simulation using the same input/output structure and the current decoy selection algorithm  
<strong>\<sarang\></strong> and see if/where the distributions diverge  
<strong>\<sarang\></strong> kiwi\_87: what do you mean by interoperability  
<strong>\<sarang\></strong> Oh, and for this data... about 2.3% of post-CT confidential transactions contained at least one possible merge  
<strong>\<sarang\></strong> (this data shows all such possible merges, not just a unique one from each transaction)  
<strong>\<Isthmus\></strong> @sarang if you want to go deep into the Bayesian weeds, could calculate the probability (always positive, but varying in magnitude) that a pair(+) of these ring members would be selected together if sampled from the standard algo  
<strong>\<UkoeHB\_\></strong> Isthmus: do you recall what proportion of transactions don't use the standard gamma distribution (approximately)?  
<strong>\<sarang\></strong> UkoeHB\_: note that this is \_all\_ post-CT confidential transactions, regardless of likely selection method  
<strong>\<sarang\></strong> I did a filter for that but may have a minor indexing issue that threw off the data  
<strong>\<sarang\></strong> Isthmus: yeah, I thought about that too (but didn't run the analysis)  
<strong>\<sarang\></strong> The distribution difference is intended to give a very rough idea of how non-ideal this distribution is  
<strong>\<ArticMine\></strong> The other question is ring size  
<strong>\<Isthmus\></strong> @UkoeHB\_ as of Konferenco (last June) about 1% of transactions used obviously uniform selection algorithm  
<strong>\<Isthmus\></strong> I haven't updated the analysis pipeline, so can't speak to recent months.  
<strong>\<UkoeHB\_\></strong> ah if sarang is already filtering those out it's not a big deal  
<strong>\<sarang\></strong> I'm not at the moment  
<strong>\<sarang\></strong> This is all post-CT confidential transactions  
<strong>\<Isthmus\></strong> @sarang what are you coding this in? I have python code to strip those out  
<strong>\<sarang\></strong> This is Python as well  
<strong>\<sarang\></strong> If you can link the code that'd be great, or I can write something up  
<strong>\<sarang\></strong> But uniform selection seems very unlikely to cause the long tail  
<strong>\<sarang\></strong> Anyway, this is the start of analysis that I hope will be useful to inform safer output selection  
<strong>\<UkoeHB\_\></strong> very cool thanks for you effort sarang :)  
<strong>\<sarang\></strong> Once I verify this indexing issue, I'll post both the analysis code and the data set  
<strong>\<Isthmus\></strong> <https://www.irccloud.com/pastebin/BChX6gR9/>  
<strong>\<sarang\></strong> I can't post \_all\_ the data (block, transaction, ring, ...) since it's far too big for GitHub  
<strong>\<kiwi\_87\></strong> @sarang, I mean the interoperability, if it can be made between Monero and other chains, there would be more room for the adoption of XMR. I learn about this from the fact that Bitcoin is entering Ethereum network with the amount that is way larger than which on the layer 2 of Bitcoin. It helps BTC to join the DeFi and increase the adoption for  
<strong>\<kiwi\_87\></strong> such crypto. Same thing can also happen with XMR, don’t you think?  
<strong>\<sarang\></strong> But I can post the resulting possible merges, which are of reasonable size  
<strong>\<sarang\></strong> Thanks Isthmus  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/fZgJlX2o/image.png>  
<strong>\<sarang\></strong> kiwi\_87: operating between Monero and other chains is surprisingly tricky, and even moreso if the goal is to maintain uniformity of transactions  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/aQVzvAAq/image.png>  
<strong>\<sarang\></strong> Isthmus: what are these plots?  
<strong>\<Isthmus\></strong> Let ring\_member\_ages be an array of ring member ages \[0.5d, 0.7d, ...\]  
<strong>\<Isthmus\></strong> offset-corrected median age = median(ring\_member\_ages - min(ring\_member\_ages)  
<strong>\<Isthmus\></strong> The correct decoy algorithm produces OCMA's around 100 - 10000 blocks  
<strong>\<Isthmus\></strong> I used 370000 as a conservative "absurdity limit"  
<strong>\<sarang\></strong> Small sample =\> high variance, I assume?  
<strong>\<Isthmus\></strong> Might also have to do with fact that algo reacts to txn vol changes  
<strong>\<Isthmus\></strong> Anyways, anything above 10^5 is suspect  
<strong>\<Isthmus\></strong> Red line is 370000 blolcks  
<strong>\<Isthmus\></strong> Anything above that is absolutely not from the correct decoy algo  
<strong>\<sarang\></strong> Examining the distribution with that filter will be very interesting  
<strong>\<Isthmus\></strong> And in most cases, when I spot checked, were due to apparent uniform decoy selectioin algo  
<strong>\<sarang\></strong> I'd expect that it wouldn't change much, but I like being proven wrong  
<strong>\<sarang\></strong> Any other speculation about the effects of these selections? (just curious)  
<strong>\<Isthmus\></strong> Hmm, I'm interested in the Bayesian analysis, which will tell us whether this is a novelty with 10% predictive power, or a damning tell with 95% predictive power  
<strong>\<sarang\></strong> Oh and Isthmus: what transactions does this account for? The entire chain?  
<strong>\<Isthmus\></strong> From introduction of RingCT until Konferenco  
<strong>\<sarang\></strong> Does it filter out non-CT transactions after the CT cutoff?  
<strong>\<sarang\></strong> These are low quantity, but are still present  
<strong>\<sarang\></strong> and have very different selection of course  
<strong>\<Isthmus\></strong> I usually ignore non-RingCT since I'm more interested in optimizing current privacy than studying historical easter eggs  
<strong>\<sarang\></strong> yeah  
<strong>\<Isthmus\></strong> I'll have to work my way back in the analysis pipeline to check  
<strong>\<sarang\></strong> I also filtered those in the plots above  
<strong>\<Isthmus\></strong> Sorry, by "ignore" RingCT, I mean "exclude them from my data set before analyzing"  
<strong>\<sarang\></strong> roger  
<strong>\<Isthmus\></strong> s/RingCT/non-RingCT  
<strong>\<monerobux\></strong> Isthmus meant to say: Sorry, by "ignore" non-RingCT, I mean "exclude them from my data set before analyzing"  
<strong>\<sarang\></strong> Oh, and I might have mentioned this last week (don't recall), but I'm still working with those CMU student researchers to confirm some updated deducibility analysis  
<strong>\<sarang\></strong> They plan to revise their preprint once again  
<strong>\<sarang\></strong> This is especially nice given that their "30% traceable" (or whatever it was) conclusion regarding spend age heuristics is incorrect  
<strong>\<kiwi\_87\></strong> @sarang. Yeah I know it’s the hardest part. Actually our research at Incognito project is currently on this direction.  
<strong>\<kiwi\_87\></strong> We have the idea of building a privacy chain learning the technology from Monero, thus allowing the high level of privacy for the chain.  
<strong>\<kiwi\_87\></strong> Then build a Portal connecting to Monero with a group of decentralized custodians holding &amp; releasing XMR when users going in &amp; going out the layer 2. The same design can be applied to BTC, which brings XMR &amp; BTC to the same privacy layer.  
<strong>\<kiwi\_87\></strong> What do you guys all think?  
<strong>\<sarang\></strong> This might be a better conversation for after the meeting kiwi\_87 if it mainly concerns research for another project  
<strong>\<sarang\></strong> Unless the group disagrees  
<strong>\<moneromooo\></strong> Not this silent part of the group.  
<strong>\<sarang\></strong> Were there any other questions on the deducibility or output merging data?  
<strong>\<sarang\></strong> If not, does anyone else wish to present research of interest for this group?  
<strong>\<Isthmus\></strong> @kiwi\_87 cool, I like seeing these types of projects. 👍  
<strong>\<h4sh3d\[m\]\></strong> I can give some updates about the swap  
<strong>\<sarang\></strong> Please do  
<strong>\<sarang\></strong> (this may be relevant to you kiwi\_87)  
<strong>\<h4sh3d\[m\]\></strong> I started working on it, I plan to have an updated version of the paper next week  
<strong>\<h4sh3d\[m\]\></strong> So, the idea is still the same as before  
<strong>\<kiwi\_87\></strong> @sarang yeah sure. I’ll talk more about what we are doing in the after-meeting time. Still, I think interoperability on XMR could be a very bright way to increase the Monero adoption. Would love to talk to other researchers who are also diving in the same direction  
<strong>\<h4sh3d\[m\]\></strong> split the monero spending key in two halfs, and "sell" one half or the other on the bitcoin chain depending if the swap success or not  
<strong>\<sarang\></strong> via multisig, I assume  
<strong>\<sarang\></strong> "You get the even bytes, and I keep the odd bytes\!"  
<strong>\<h4sh3d\[m\]\></strong> Yes, kind of. Before there was the generic zkp for the hash preimage  
<strong>\<kiwi\_87\></strong> @Isthmus sure. Would love to share more in the after-meeting time. Now let’s make the convo laser-focused on Monero  
<strong>\<sarang\></strong> h4sh3d\[m\]: but you're replacing with a cross-group DL equivalence proof via side channel, correct?  
<strong>\<kiwi\_87\></strong> @h4sh3d\[m\] would love to hear about this. Really want to know what’s going on there with the cryptography challenge. Please update us :D  
<strong>\<h4sh3d\[m\]\></strong> Now, by combining dl equality across group + ECDSA one-time VES, we should be able to achieve the same  
<strong>\<h4sh3d\[m\]\></strong> ECDSA one-time VES: <https://github.com/LLFourn/one-time-VES/blob/master/main.pdf>  
<strong>\<h4sh3d\[m\]\></strong> (it's an ECDSA "adaptor signatures")  
<strong>\<sarang\></strong> Remind me: does this approach assume/require any particular timelock capability on the Monero side?  
<strong>\<sarang\></strong> If so, to what extent?  
<strong>\<h4sh3d\[m\]\></strong> No, nothing is required on the Monero side, that's the cool part  
<strong>\<sarang\></strong> OK, thanks  
<strong>\<sarang\></strong> Monero supports a very simple timelock of course  
<strong>\<sarang\></strong> but it's a bit inconsistent at the moment, and apparently infrequently used  
<strong>\<sarang\></strong> so if it were required, this could present a uniformity issue  
<strong>\<h4sh3d\[m\]\></strong> We create an address where Spend = Spend\_alice + Spend\_bob (same for view)  
\<Spend, View\> corresponding address  
<strong>\<sarang\></strong> Does the address protocol have issues with key cancellation?  
<strong>\<h4sh3d\[m\]\></strong> Each participant has his own half, and one will get the second one  
<strong>\<sarang\></strong> Or is there precommitment to address parts?  
<strong>\<h4sh3d\[m\]\></strong> Not sure if I understand what you mean by key cancellation  
<strong>\<sarang\></strong> If you hand me a part of a key, maybe I maliciously generate my own "key" such that the sum is any value I want  
<strong>\<h4sh3d\[m\]\></strong> Ah yes, I thought about that  
<strong>\<sarang\></strong> If this is problematic, we can each commit to our key portions first, and then check that the keys received match the commitments  
<strong>\<sarang\></strong> it ensures that neither party change their mind  
<strong>\<sarang\></strong> Adds a communication round  
<strong>\<sarang\></strong> There are other methods involving random-oracle linear combinations too, depending on what you need  
<strong>\<h4sh3d\[m\]\></strong> I thought about the commit, but that also mean you don't know your correct "half" (only the destiantion priv/pub), and without priv half, you are not able to continue the protocol  
<strong>\<sarang\></strong> But sorry, I'm digressing here  
\<\>other cryptos, we will need more atomic swap designs and Portal designs connecting layer 2 and Monero chain  
<strong>\<h4sh3d\[m\]\></strong> No, it's a good one  
<strong>\<sarang\></strong> kiwi\_87: let's discuss after the meeting  
<strong>\<sarang\></strong> h4sh3d\[m\]: ok, as long as it's either not necessary or taken care of via a communication round, I suppose  
<strong>\<sarang\></strong> But certainly worth a close eye after the paper is updated  
<strong>\<h4sh3d\[m\]\></strong> when we get the address, and the initialization phase is done (with zkp dl equality e.g.), one send Monero into it  
<strong>\<kiwi\_87\></strong> @sarang sure  
<strong>\<h4sh3d\[m\]\></strong> at the end, Alice or Bob, will learn the full private spend key = priv\_spend\_alice + priv\_spend\_bob  
<strong>\<h4sh3d\[m\]\></strong> So no, nothing fancy required on the Monero side  
<strong>\<atoc\></strong> nice  
<strong>\<h4sh3d\[m\]\></strong> You will import the full keys in you wallet and do a regular transaction  
<strong>\<sarang\></strong> Definitely look forward to seeing the updated paper h4sh3d\[m\]\!  
<strong>\<atoc\></strong> same  
<strong>\<h4sh3d\[m\]\></strong> (keys that are generated withou a seed and a derivation function, so wallet must support "raw" keys)  
<strong>\<h4sh3d\[m\]\></strong> Right now, I'm in the one-time VES paper, and your MRL-0010 one  
<strong>\<sarang\></strong> got it  
<strong>\<h4sh3d\[m\]\></strong> \* I'm done, thanks for your inputs  
<strong>\<sarang\></strong> I might update MRL-0010 to specify that the Pedersen generators need an unknown DL relationship  
<strong>\<sarang\></strong> Apparently that wasn't listed specifically, but is generally true for Pedersen commitment security  
<strong>\<sarang\></strong> In the interest of time, were there any other research topics that need to be presented before the hour is up?  
<strong>\<Isthmus\></strong> Quick update: I’m really happy to share that we’re officially beginning our audit of monero’s security and privacy mechanisms against algorithms that could be exploited by hypothetical quantum adversaries. Thank you to everybody who contributed feedback or funds to our CCS 🙏  
<strong>\<Isthmus\></strong> The first step is a formalizing our adversary model and enumerating of mechanisms of interest.  
<strong>\<Isthmus\></strong> Right now the attack surface list looks like {Ring Signatures, RingCT, One-time "Stealth" Addresses, Pubkey derivation, Forge amounts?, Bulletproofs, RandomX proof-of-work, Block / Transaction hashing}.  
<strong>\<Isthmus\></strong> Please suggest other pieces that you’d like to see audited. :- )  
<strong>\<Isthmus\></strong> Earlier I was looking at the wallet generation schematic shared to Reddit, and it has me pondering visual ways to communicate results. <https://www.reddit.com/r/Monero/comments/gy0m1u/i\_made\_an\_infographic\_on\_how\_a\_monero\_wallet\_is/>  
<strong>\<monerobux\></strong> \[REDDIT\] I made an infographic on how a Monero wallet is generated. Can you find any mistakes? (<https://i.redd.it/tv98m10mbd351.png>) to r/Monero \| 163 points (100.0%) \| 18 comments \| Posted by Krakataua314 \| Created at 2020-06-06 - 22:42:54  
<strong>\<Isthmus\></strong> <https://i.redd.it/tv98m10mbd351.png>  
<strong>\<Isthmus\></strong> For example, the ed25519 scalarmult (used for private view key → public viewkey) is a one-way function for traditional computers (assuming hardness of the discrete log problem) but can be reversed if you can apply Shor’s algorithm.  
<strong>\<Isthmus\></strong> So perhaps this could be visually annotated with directional arrow for traditional adversaries and bidirectional arrow for hypothetical quantum adversaries. Would that be an intuitive approach?  
<strong>\<sarang\></strong> I like that idea  
<strong>\<sarang\></strong> that's very clever  
<strong>\<sarang\></strong> Can you remind us of the expected timeline Isthmus?  
<strong>\<Isthmus\></strong> Will be working on this full time for the next 3 months  
<strong>\<sarang\></strong> (with the understanding that research often takes unexpected twists)  
<strong>\<Isthmus\></strong> Phase 1 should be quick  
<strong>\<sarang\></strong> The scope was modified to focus less on deliverable code, right?  
<strong>\<sarang\></strong> And more on solid understanding, possible mitigations and relevant work, and communication?  
<strong>\<Isthmus\></strong> Just setting the stage for our object of study and attacker, hoping to have a first "final draft" of that done by next MRL meeting  
<strong>\<sarang\></strong> Oh nice  
<strong>\<Isthmus\></strong> Yep  
<strong>\<sarang\></strong> That'll be great to see  
<strong>\<Isthmus\></strong> And then working systemically through the cross sections  
<strong>\<Isthmus\></strong> (table where each column is a quantum adversary and each row is a piece of Monero tech)  
<strong>\<Isthmus\></strong> My guess is that we'll be able to fill 80% of the squares in 20% of the time  
<strong>\<Isthmus\></strong> And then 20% of the squares will take 80% of the time  
<strong>\<sarang\></strong> Do you expect that the final results will be suitable for broader distribution? Like to journals, refereed conferences, or simply IACR archive?  
<strong>\<Isthmus\></strong> Throughout this entire project, the community will receive updates during the weekly \#monero-research-lab meetings. During phase 3 however, several specific documents (the key deliverables from this research) will be freely published  
<strong>\<Isthmus\></strong> 1. User-friendly writeup: This community-facing writeup will provide an approachable explanation of how hypothetical quantum computers may impact Monero, and possible future mitigations. The writeup should minimize FUD and provide the context that these vulnerabilities apply to almost all cryptocurrencies (not only Monero).  
<strong>\<Isthmus\></strong> 2. Technical documentation: An MRL position paper to distill key information for (current and future) researchers and developers. The writeup should formally describe vulnerabilities, and highlight potential strategies and solutions, noting their tradeoffs. Code snippets may be included if appropriate for pedagogical purposes or clarity.  
<strong>\<Isthmus\></strong> 3. Non-technical 1-pager: An ELI5 / TL;DR summary will be provided for journalists, Monero Outreach, etc. This blurb will discuss risks and myths with no technical jargon, with key takeaways that a broad audience will appreciate.  
<strong>\<Isthmus\></strong> (Results and updates will be also disseminated via Twitter threads, Reddit posts, and Breaking Monero videos.)  
<strong>\<Isthmus\></strong> And yea, hopefully we can get a paper or two out of this  
<strong>\<Isthmus\></strong> Much of the research will be broadly applicable  
<strong>\<sarang\></strong> Great\!  
<strong>\<atoc\></strong> Nice  
<strong>\<sarang\></strong> Getting a better sense of research trends in this direction, even if not presently applicable, will be intriguing to see  
<strong>\<sarang\></strong> e.g. there are plenty of ideas for post-quantum constructions, but there are generally huge barriers in efficiency that render them unusable  
<strong>\<atoc\></strong> btw Isthmus, this may be off topic but can you talk a little more about the Insight program?  
<strong>\<sarang\></strong> OK, we're just about out of time  
<strong>\<sarang\></strong> atoc: perhaps for right after the meeting?  
<strong>\<atoc\></strong> yes  
<strong>\<sarang\></strong> Are there any other last questions or comments about these research topics before adjourning?  
<strong>\<sarang\></strong> If not, thanks to everyone for attending and participating\!
