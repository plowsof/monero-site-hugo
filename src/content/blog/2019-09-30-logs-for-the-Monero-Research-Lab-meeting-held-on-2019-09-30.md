---
title: Logs for the Monero Research Lab Meeting Held on 2019-09-30
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Let's start\! Agenda here: <https://github.com/monero-project/meta/issues/395> (logs posted there after the meeting)  
<strong>\<sarang\></strong> GREETINGS  
<strong>\<mikerah\></strong> Hello  
<strong>\<silur\></strong> hi  
<strong>\<gingeropolous\></strong> hewro  
<strong>\<sarang\></strong> Is suraeNoether here?  
<strong>\<suraeNoether\></strong> howdy  
<strong>\<suraeNoether\></strong> hi, sorry, i'm going to be in and out this morning  
<strong>\<kinghat\></strong> o/  
<strong>\<sarang\></strong> ok  
<strong>\<suraeNoether\></strong> i can do a real quick rundown, but i have to go :(  
<strong>\<charuto\></strong> o/  
<strong>\<sarang\></strong> In that case, let's jump into the ROUNDTABLE with suraeNoether  
<strong>\<suraeNoether\></strong> okay, so  
<strong>\<suraeNoether\></strong> matching  
<strong>\<suraeNoether\></strong> i've been working on the code, and there were some structural problems, and then a failure-to-push-my-damn-commits failure of my local harddrive  
<strong>\<suraeNoether\></strong> it's proceeding... slowly  
<strong>\<suraeNoether\></strong> i've been sick a lot :(  
<strong>\<suraeNoether\></strong> other than that, i don't have anything to chat about right now  
<strong>\<sarang\></strong> What would you say the current state of matching simulations is?  
<strong>\<suraeNoether\></strong> i'm hoping to push some code later today on my simulations  
<strong>\<suraeNoether\></strong> non-functional  
<strong>\<sarang\></strong> And is there any part of it that could/should be worked on by others as well?  
<strong>\<sarang\></strong> Or of the corresponding theory?  
<strong>\<suraeNoether\></strong> the paper has been available and the codebase is available. the matching code itself is working, but my method of comparing it to some simulated ledger is what is taking awhile.  
<strong>\<sgp\_\></strong> I'm here from where Sarang should be :)  
<strong>\<sarang\></strong> \>\_\>  
<strong>\<suraeNoether\></strong> anyone can choose to simulate a ledger \*some other way\* and run my code  
<strong>\<sarang\></strong> Ah ok, got it  
<strong>\<suraeNoether\></strong> we even have speed numbers for our matching code from you  
<strong>\<suraeNoether\></strong> literally, it's a sanity check and comparing against known churn behaviors  
<strong>\<sarang\></strong> Righto, any questions for suraeNoether before he must go?  
<strong>\<suraeNoether\></strong> okay guys i have to go. expect a push later today. i'm also going back on solid food later today so who knows, maybe i'll have some burst of inspiration  
<strong>\<sarang\></strong> Feel better plz  
<strong>\<sarang\></strong> I've been working on several things this past week  
<strong>\<charuto\></strong> may good health and good fortune go your way mr surae  
<strong>\<sarang\></strong> First, the CLSAG paper is now submitted to Financial Cryptography 2020  
<strong>\<sarang\></strong> The preprints on the MRL archive and on IACR are updated  
<strong>\<sarang\></strong> Or rather, IACR has been updated and an MR exists for the MRL archive  
<strong>\<sarang\></strong> The DLSAG paper was also updated and submitted to the same conference  
<strong>\<xmrmatterbridge\> \<sgp\_\></strong> <https://eprint.iacr.org/2019/654>  
<strong>\<sarang\></strong> Second, I'm still working with the author of Lelantus on some modifications to avoid its linking problem  
<strong>\<sarang\></strong> We'll have a short writeup soon about one possible way, but it doesn't work cleanly with one-time addresses in the way you might want it to  
<strong>\<sarang\></strong> There are some techniques involving Schnorr proofs that we still want to investigate  
<strong>\<sarang\></strong> Third, I am finalizing proof-of-concept code and spacetime analysis for the updated RCT3 preprint, which has interesting tradeoffs from the earlier version  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> exciting\!  
<strong>\<silur\></strong> is the PoC code available somewhere?  
<strong>\<sarang\></strong> Besides fixing a big flaw, it aggregates proofs together... this means very small proofs at the expense of some verification  
<strong>\<sarang\></strong> Code (danger: not for production) is here: <https://github.com/SarangNoether/skunkworks/tree/rct3/rct3>  
<strong>\<silur\></strong> thanks  
<strong>\<sarang\></strong> I'll also run numbers on doing non-aggregated proofs, since that would effectively reverse the spacetime tradeoff  
<strong>\<hyc\></strong> ^ bets on which xmr fork deploys it first ...  
<strong>\<sgp\_\></strong> What is "some verification"?  
<strong>\<sarang\></strong> My initial estimates suggest a drop in size from 3.1 kB to perhaps 2.3 kB (2-in-2-out)  
<strong>\<sarang\></strong> Verification numbers TBD, but not too bad... considering the original 2-2 single verification estimate was 39 ms on a test machine, batched down to 13 ms  
<strong>\<sarang\></strong> Back-of-the-envelope is that batched 2-2 txns will see maybe 5% increase from the old version's time  
<strong>\<sarang\></strong> but again, you save 25% on space from the old version  
<strong>\<sarang\></strong> Pulling apart the aggregation will improve batching time by reusing generators  
<strong>\<sarang\></strong> but then space is back up again  
<strong>\<sarang\></strong> There are also some structural differences to the proofs that will mean somewhat higher times regardless  
<strong>\<sarang\></strong> More details once I have the actual numbers finished  
<strong>\<sarang\></strong> Fourth, my monthly report is posted here: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/77#note\_7393>  
<strong>\<sarang\></strong> Fifth, I'll be joining rehrar and Daniel Kim to speak at World Crypto Conference later this month  
<strong>\<sarang\></strong> My talk is about the history of cryptographic constructions toward privacy-preserving transactions, and future research directions  
<strong>\<sarang\></strong> I'm starting it early to meet their particular deadlines  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> woot\!  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> WCC represent  
<strong>\<sarang\></strong> I'm trying to think of some good analogies for why terms like "privacy coin" set the wrong baseline  
<strong>\<sarang\></strong> For example, you wouldn't visit someone's house and say "oh, you have one of those bathrooms with a door"  
<strong>\<mikerah\></strong> Try to frame it in terms of cash  
<strong>\<sarang\></strong> It should be the default\!  
<strong>\<xmrmatterbridge\> \<sgp\_\></strong> "This is a safe car"?  
<strong>\<mikerah\></strong> Cash is anonymous, debit/credit cards are tracked by your bank  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> the bathroom door is spot on  
<strong>\<sarang\></strong> Anyway, the talk is mainly about cryptography, but I like setting the stage briefly to give motivation for the cryptography  
<strong>\<sarang\></strong> And I'm a terrible designer, so I always take longer than expected to make presentations look not-too-horrible :/  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> sarang, bro just send to me?  
<strong>\<sarang\></strong> in all its TeX goodness :)  
<strong>\<xmrmatterbridge\> \<sgp\_\></strong> your plain presentations are ok imo  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> test, is MM working in this room?  
<strong>\<sarang\></strong> hi rehrar  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> bloof  
<strong>\<sarang\></strong> So yeah, that's what I've been working on  
<strong>\<sarang\></strong> Any particular questions on those items?  
<strong>\<xmrmatterbridge\> \<serhack\></strong> In my opinion, this should depend on audience sarang  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> nah  
<strong>\<sarang\></strong> serhack: how so?  
<strong>\<sarang\></strong> It's an audience of developers  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> though I have a Research Request (tm) for MRL as a whole  
<strong>\<silur\></strong> I'm so missing an audience of developers :D  
<strong>\<sarang\></strong> rehrar: go on  
<strong>\<xmrmatterbridge\> \<sgp\_\></strong> I have a point to mention after  
<strong>\<sarang\></strong> ok  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> It's be asked before with varying degrees of intensity, but I'd like some research done on the 10 confirmation unlock time.  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> 10 confs was kinda chosen arbitrarily? Or did it have reasoning? Research on if this is the ideal number.  
<strong>\<dEBRUYNE\></strong> sarang: Have there been any noteworthy developments regarding the CLSAG audits?  
<strong>\<sarang\></strong> I see that as really being a question of network topology and propagation, as it relates to reorgs  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Obviously the hope is to get the conf time down for spendable funds, but if research shows 10 is good (or even increase), well at least we have numbers to back it up  
<strong>\<sarang\></strong> I don't have particular data on this... best candidates for that are the noncesense folks  
<strong>\<sarang\></strong> dEBRUYNE: OSTIF is working to get the first code audit number (24750 USD) down  
<strong>\<sarang\></strong> the math audit number is currently 7200 USD  
<strong>\<dEBRUYNE\></strong> OK  
<strong>\<dEBRUYNE\></strong> Do we have only one offer for a code audit btw?  
<strong>\<xmrmatterbridge\> \<serhack\></strong> sarang: probably you know this suggestion but I will never tire of repeating it. You have to capture attention of people, in any possible way. So, if you think the presentation graphic could be changed to improve the readability, go for it. If you think you have to remove text and to add more images, go for it.  
<strong>\<nioc\></strong> rehrar if you reduce the time to 5 minutes won't you just get questions like, why I need to wait 5 minutes?  
<strong>\<sarang\></strong> AFAIK there is only the single code audit offer right now, but OSTIF is working on this  
<strong>\<sarang\></strong> Both to allow the possibility of multiple reviews (if desired) and to promote competition that could reduce the cost of each review  
<strong>\<xmrmatterbridge\> \<sgp\_\></strong> This isn't high priority, but I'd like to see an analysis of the number of coinbase outputs in rings on average over time  
<strong>\<sarang\></strong> Ah, over the different selection algorithms?  
<strong>\<sarang\></strong> I agree that it would be interesting. I ran some numbers on super small datasets and it was a spread that maxed at 1-in-11 IIRC  
<strong>\<sarang\></strong> There is always the question of whether a consensus rule of "any ring w/ coinbase must be all coinbase" would be a net benefit  
<strong>\<sarang\></strong> I still hold that it shifts the resulting heuristic down the transaction graph one hop, but overall it's probably not a bad idea  
<strong>\<xmrmatterbridge\> \<sgp\_\></strong> You know my view is that it's a net positive, but most people don't agree yet  
<strong>\<silur\></strong> I don't get the assumptions itself, aren't coinbases in rings can be used as inputs to any other tx?  
<strong>\<silur\></strong> won't making "any ring with coinbase must be all coinbase" that property nonexistent?  
<strong>\<sarang\></strong> One claim is that coinbase can be excluded as the true spend for "average transactiosn"  
<strong>\<sarang\></strong> as well as questions of pool behavior  
<strong>\<sarang\></strong> Prior to the last selection change, coinbase were being overselected as part of a broader weighting issue  
<strong>\<sarang\></strong> Now they're selected according to their on-chain frequency, but are otherwise not selected differently  
<strong>\<sarang\></strong> Of course, making all-coinbase rings means that you could now identify the outputs of those transactions as heuristically not true spenders where they are used  
<strong>\<silur\></strong> on firsth thought that doesn't seem too much of a practical privacy leak  
<strong>\<sarang\></strong> It was not good when they were being overselected, but in fact the over/underselection was technically occurring for all selection regions where block density was varied  
<strong>\<sarang\></strong> It was just that coinbase were far more visible as an effect of this  
<strong>\<silur\></strong> I see  
<strong>\<sarang\></strong> So right now you'll usually see 0-1 coinbase or so per ring, but there are certainly outliers with more  
<strong>\<sarang\></strong> Anyway, certainly something to keep thinking about. As with most things, it's probably a bit more subtle than it seems at first glance  
<strong>\<sarang\></strong> Back to the agenda... did anyone else have research to share?  
<strong>\<sarang\></strong> Or other questions?  
<strong>\<sarang\></strong> Right, then on to ACTION ITEMS  
<strong>\<mikerah\></strong> I have some questions related to what was discussed last week  
<strong>\<sarang\></strong> sure mikerah  
<strong>\<sarang\></strong> go ahead  
<strong>\<mikerah\></strong> Have you considered using Polynomial commitments  
<strong>\<sarang\></strong> For what?  
<strong>\<mikerah\></strong> In order to get a SNARK without trusted setup for ring signatures  
<strong>\<sarang\></strong> How so?  
<strong>\<mikerah\></strong> Current schemes that are coming out are using polynomial commitments in such a way that you can eliminate the need for a trusted setup  
<strong>\<mikerah\></strong> Halo and DARKs come to mine.  
<strong>\<silur\></strong> afaik those are more generic schemes than what's needed in practice here  
<strong>\<sarang\></strong> Well, Halo's big goal is recursive evaluation  
<strong>\<mikerah\></strong> These schemes aren't quantum secure and you get larger proof verification sizes as usual  
<strong>\<sarang\></strong> and it's not even close in terms of desired efficiency yet; early stages  
<strong>\<kenshamir\[m\]\></strong> \<mikerah "Halo and DARKs come to mine."\> DARKs can be used, but the polynomial commitment scheme in Halo cannot from what I’ve read and tried  
<strong>\<mikerah\></strong> isn't halo's big goal recursive composition + no trusted setup  
<strong>\<sarang\></strong> yes  
<strong>\<silur\></strong> mikerah: quantum secure schemes have even larger proofs  
<strong>\<silur\></strong> usually 2kb+  
<strong>\<silur\></strong> at best  
<strong>\<mikerah\></strong> kenshamir: If I understand correctly, the polynomial commitment scheme in Halo is derived from Sonic.  
<strong>\<mikerah\></strong> silur: There's a lot of research going into quantum secure zk-SNARKs. Although proofs are prohibitely expensive, even more so than current schemes, I expected it to get better in the next 5-10 years  
<strong>\<kenshamir\[m\]\></strong> The paper on the commitment scheme for DARKs is not out yet, it uses class groups, so group sizes will be roughly the same as RSA, but verifier asymptotics will be sublinear  
<strong>\<silur\></strong> mikerah: I'm mainly into quantum-safe crypto so I also follow these researches. I'm more optimistic on the matter and expect that breaktrough much sooner :P  
<strong>\<sarang\></strong> In the interest of time, let's go ahead and wrap up this meeting; discussions can of course continue after  
<strong>\<kenshamir\[m\]\></strong> \<mikerah "kenshamir: If I understand corre"\> I read it as a modification of inner product argument that is similar to bulletproofs, I’d need to read sonic though haha, only have ever skimmed it  
<strong>\<kenshamir\[m\]\></strong> The polynomial commitment scheme used in sonic is KZG10 IIRC  
<strong>\<mikerah\></strong> kenshamir: I also read it as that but if you skim through Halo, they present Sonic and then give the modifications to the sonic scheme in order to achieve amortized succintness  
<strong>\<sarang\></strong> I'll be working on WCC prep, RCT3 proof review and analysis numbers, and an idea RandomRun had for modifying the Triptych proof to support multiple inputs natively  
<strong>\<sarang\></strong> For log posting purposes, let's adjourn here and let conversations continue :D
