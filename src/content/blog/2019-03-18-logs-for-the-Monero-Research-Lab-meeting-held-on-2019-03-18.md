---
title: Logs for the Monero Research Lab Meeting Held on 2019-03-18
summary: Sarang work, Surae work, Output distribution and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> 1. GREETINGS  
<strong>\<sarang\></strong> Hello all  
<strong>\<suraeNoether\></strong> greetings\!  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Hello  
<strong>\<xmrmatterbridge\> \<oneiric\></strong> hidere  
<strong>\<suraeNoether\></strong> worriedrise: i'm pretty sure i can prove that it's an interaction-free instantiation of thring signatures without much effort at all. i spent about an hour working on that proof this weekend, but i haven't uploaded it anywhere yet  
<strong>\<sarang\></strong> Let's discuss it shortly per the agenda  
<strong>\<sarang\></strong> Since it should warrant plenty of discussion  
<strong>\<sarang\></strong> 2. ROUNDTABLE  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I am looking forward to seeing it  
<strong>\<sarang\></strong> We have been discussing output selection quite a bit, and should prepare to make a recommendation for the next point release  
<strong>\<sarang\></strong> The output age distribution for selections made by the different options are reasonably close to each other under usual chain conditions  
<strong>\<sarang\></strong> At this point I'm going to recommend the output-lineup method  
<strong>\<sarang\></strong> Any thoughts on this?  
<strong>\<suraeNoether\></strong> for now, i favor the lineup method, until we have established a better alternative, or better metrics for analysis  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I am fine with that  
<strong>\<sarang\></strong> Neat  
<strong>\<moneromooo\></strong> For the output lineup method, the parameters (assuming you still use a gamma) are going to be very different.  
<strong>\<sarang\></strong> They use the same 2-day mean, but with an average output age determined by the chain (or some portion thereof)  
<strong>\<moneromooo\></strong> And they depend on how many outputs there are in the blocks. That seems to be fundamentally wrong to me, even though it seems to work in practice...  
<strong>\<moneromooo\></strong> I feels like overfitting/  
<strong>\<sarang\></strong> I don't know a better approach that meets our needs  
<strong>\<sarang\></strong> The point is they use averaging to smooth out density fluctuations  
<strong>\<suraeNoether\></strong> whatever method we end up selecting, we will have to re-estimate our selection parameters, since the distribution technically won't be gamma, for sure  
<strong>\<suraeNoether\></strong> the sensitivity to blockchain density is actually a feature not a bug imho  
<strong>\<sarang\></strong> Under the famine condition, for example, the averaging means that older outputs are favored more than the 2-day mean would currently do  
<strong>\<moneromooo\></strong> I had expected gamma to stay.  
<strong>\<sarang\></strong> The exp-gamma selection would stya  
<strong>\<sarang\></strong> but the parameters use an average output age  
<strong>\<suraeNoether\></strong> to sarang's point about famine: real-life spend-time distributions are very much sensitive to blockchain density and vice versa. a famine condition as sarang describes is "what happens if people start spending less and less, or with greater intervals of time between spends?" the answer \*should\* be that older outputs appear in ring signatures more often  
<strong>\<sarang\></strong> I invite people to play around with the algorithms and chain conditions with my simulation code  
<strong>\<suraeNoether\></strong> to moo's point: we are still trying to approximate a gamma distribution in terms of the age of one of the next outputs to be confirmed on-chain.  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Is anyone looking into the metrics of how many times an output is used in a ring? That should give us soe good insights  
<strong>\<suraeNoether\></strong> but either way, we should probably run our own analysis on spend-times and see if the parameters reported in the monerolink paper are sitll reasonable  
<strong>\<sarang\></strong> IIRC the statistical average tends toward the fixed ringsize  
<strong>\<sarang\></strong> At any rate, if people want to do more analysis, now is the time so we have a solid scheme ready for next release  
<strong>\<sarang\></strong> Otherwise: there's working bulletproofs MPC test code now, but the security guarantees depend heavily on the number of rounds and the presence or absence of player precommitments to their values to avoid cancellations  
<strong>\<suraeNoether\></strong> worriedrise and sarang: the average number of uses per key with a fixed ring size of R and N total ring signatures is \<= R. Why? assume each ring signature has R members, and there are N ring signatures in total. There are at least N keys (one for each ring signature) so the average number of uses per key is total number of uses (N\*R) divided by total number of keys (there are N or more of these). So the  
<strong>\<suraeNoether\></strong> average uses per key is at most R.  
<strong>\<suraeNoether\></strong> gratz on working bulletproofs MPC; to be precise you mean "bulletproofed range proof MPCs" correct? not arbitrary bulletproofed statements?  
<strong>\<sarang\></strong> range proofs  
<strong>\<suraeNoether\></strong> neat  
<strong>\<sarang\></strong> but the idea extends to general proofs  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Average, yes. But the question is are there rings being over/under-selected?  
<strong>\<sarang\></strong> for sure  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> And how bad is the problem  
<strong>\<suraeNoether\></strong> so sarang you've been reading more on lelantus?  
<strong>\<sarang\></strong> Yes, and playing around with some of the schemes they use  
<strong>\<sarang\></strong> Modifications to BPs and a Groth sigma protocol  
<strong>\<sarang\></strong> Nothing to report except that  
<strong>\<sarang\></strong> My funding request is open for funding now, and is about 1/3 complete\!  
<strong>\<suraeNoether\></strong> do you have plans or ideas on how to assess scaling of the lelantus ringct versus ours?  
<strong>\<sarang\></strong> Yes, more careful op counts and a better understanding of how to handle commitments in the Groth protocol  
<strong>\<sarang\></strong> it's still very pie-in-the-sky at this point  
<strong>\<suraeNoether\></strong> okay; need anything from me in your reading about it?  
<strong>\<sarang\></strong> suraeNoether: your updates?  
<strong>\<sarang\></strong> not at this point  
<strong>\<suraeNoether\></strong> okay, so my work this past week has revolved primarily around simulations for my matching code, which i want to describe briefly  
<strong>\<suraeNoether\></strong> basically, i'm trying to simulate a blockchain under "realistic enough" circumstances and embed within this simulation some abnormal behavior that an analyzer may be interested in seeking out with machine learning or something like that  
<strong>\<suraeNoether\></strong> for example, if we want to model the classic EABE controlled purchase weekly of some illicit stuff, this would correspond to embedding a periodic signal into this blockchain  
<strong>\<suraeNoether\></strong> for another example, what if a specific vendor is merely impatient and spends more rapidly than other vendors? drawing from an exponential distribution instead of a gamma, or something along those lines  
<strong>\<suraeNoether\></strong> the goal is for my matching algorithm to try to find this embedded signal and see how good it is at this task, both in terms of false positives and false negatives  
<strong>\<suraeNoether\></strong> this can be loosely compared to the methods used in monerolink for testing those approaches, with a major exception: the goal here is to estimate the power of the statistical test over a wide range of hypotheses, while all the "background noise" is behaving \*just as one would expect with our wallet distributions.\*  
<strong>\<suraeNoether\></strong> so i want to sit down with sarang later today to discuss output selection simulation methods. after all, if we suspect we'll be implementing one of four different schemes, it makes sense to implement these in the simulations and test their performance... but it's very easy to go overboard with such tests and over-engineering a big experiment  
<strong>\<suraeNoether\></strong> i want to come up with a very precise set of tests to get to the heart of what we want to test and what information we need in order to make informed decisions and move forward  
<strong>\<suraeNoether\></strong> on teh plus side, we are ending up with a pretty rigorous simulation suite for simulating monero blockchains.  
<strong>\<sarang\></strong> nice  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Could we keep track of a counter to keep track of how outputs may be over/under-selected, as I mentioned before?  
<strong>\<suraeNoether\></strong> my other updates involve dlsag security stuff and reading about generalizations of the keccak sponge construction to the family of parazoa hash functions. but those are less interesting: the first paper is nearing completion, and the second is pie-in-the-sky  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I believe this may be a good goal  
<strong>\<moneromooo\></strong> I think you can do that with one of the tools in src/blockchain\_utilities  
<strong>\<sarang\></strong> worriedrise: how would this data affect your opinion on output selection?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> If we can find certain outputs that are consistently being under selected, that is more likely to be the true soender  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> spender  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> And conversely  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I believe that might be already happening with the approach of choosing uniformly on small blocks, not just to coinbase outputs  
<strong>\<sarang\></strong> We're certainly seeing outputs being selected with improper weighting based on block size, no doubt  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Coinbase outputs are just easy to spot, which is why people noticed them  
<strong>\<sarang\></strong> The numbers for output-lineup are much better on that  
<strong>\<sarang\></strong> My sim tool can provide those numbers  
<strong>\<suraeNoether\></strong> so, that's an interesting heuristic, actually, worriedrise, but i'm not too worried about it for the following reason  
<strong>\<sarang\></strong> e.g. how often are outputs in blocks of size X selected relative to their occurrence on the chain  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Yes, but we should check if further methods don't do that as well inadvertently  
<strong>\<sarang\></strong> What do you mean? We can check those numbers for all the proposed methods  
<strong>\<sarang\></strong> just run the sim tool, choosing your preferred selection method and preferred chain density condition  
<strong>\<sarang\></strong> (including the real chain)  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I believe we can. I was not sure we were  
<strong>\<sarang\></strong> Ah ok  
<strong>\<sarang\></strong> I added that functionality a week or two ago to the tool  
<strong>\<sarang\></strong> Feel free to run it if you want to play around with the results  
<strong>\<sarang\></strong> (link in agenda)  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Thanks. I hadn't seen it  
<strong>\<sarang\></strong> np  
<strong>\<suraeNoether\></strong> so, basically my primary lack of concern comes from variance  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> How about for the actual blockchain, do we have that data?  
<strong>\<suraeNoether\></strong> if average ring use is \<= 11 when we have a fixed ring size 11, the variance in use per output is going to be \*huge\* compared to 11  
<strong>\<sarang\></strong> worriedrise: that data meaning...  
<strong>\<suraeNoether\></strong> the power of that heuristic would be absolutely awful  
<strong>\<sarang\></strong> The chain density, or the frequency of selections based on poor weighting?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Agreed. But we can see the problem with coinbase outputs. Maybe looking at the data we can see it with other outputs too  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> The data of outputs use in the actual blockchain. Maybe you have that already  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Not just for the simulations  
<strong>\<sarang\></strong> I don't have data for how frequently outputs from small blocks are overselected  
<strong>\<sarang\></strong> I have data for how the current selection scheme performs under simulated selections from the actual chain  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> That should be good enough for now. I am still curious though :)  
<strong>\<suraeNoether\></strong> we can chase heuristics all day long; let's move along for now  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Okay  
<strong>\<suraeNoether\></strong> worriedrise: nothing stopping you from compiling some data and taking a gander and seeing if any conclusions can be drawn  
<strong>\<suraeNoether\></strong> i'm in favor of more data, generally  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I don't know how to do that, but I will look into it and see what I can do.  
<strong>\<sarang\></strong> suraeNoether: anything else to report from your update?  
<strong>\<suraeNoether\></strong> nothing to report yet, although I suspect a draft of the matching paper is incoming some time this week (but i said that last week too)  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> worriedrise/randomrun had an idea for making MLSAGs shorter: <https://github.com/monero-project/research-lab/issues/52>  
<strong>\<sarang\></strong> This has grown into an idea for general MLSAGs that applies a kind of key aggregation  
<strong>\<sarang\></strong> Care to comment or discuss worriedrise?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Sure  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> That is just something that seemed reasonable, but I have no security proofs at this time  
<strong>\<suraeNoether\></strong> for simple ringct transactions, the approach uses a Musig-style key aggregation with LSAG signatures to construct a RingCT, instead of using MLSAG signatures to construct RingCT. The overall size of the signatures are smaller, although verification time takes as much time (roughly) as previously.  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> The idea is to use a hashed linear combination to aggregate keys  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> into a single signing key  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Linkability is harder  
<strong>\<sarang\></strong> right  
<strong>\<sarang\></strong> at worst, it would require a new image format  
<strong>\<sarang\></strong> at best, a second image-style point, correct?  
<strong>\<suraeNoether\></strong> the unforgeability proof because of the structure of this, essentially boils down to a very similar proof to the proof of security for the thring signatures paper (<https://eprint.iacr.org/2018/774.pdf>)  
<strong>\<suraeNoether\></strong> linkability \*is\* harder  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Correct, but that may work well with the previous one  
<strong>\<suraeNoether\></strong> \*nod\*  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Have you been able to write down how that would work, without changing the key image?  
<strong>\<sarang\></strong> You mean the general form?  
<strong>\<sarang\></strong> I have not  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I would love to see that bc it would work for DLSAGs s well  
<strong>\<sarang\></strong> The specific initial form would work with the existing key image, by adding the second point as you mentioned in the post  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I see  
<strong>\<sarang\></strong> But I have only just started examining the scheme in detail today\!  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Yes, but just for aggregating the amount component  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> It seems to me that we need different sets of constants for different key images, as it stands  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> But with the change to the key image, they all aggregate together  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> The problem is that that doesn't work for DLSAGs as they are right now  
<strong>\<sarang\></strong> right  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Since their key images are not defined over a common point  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I am trying to see a way  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Would love suggestions :)  
<strong>\<sarang\></strong> It is a very clever idea regardless  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Thanks  
<strong>\<sarang\></strong> Once this meeting is over, I will be continuing to review it  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> It still looks too good to be true. Please double chack that carefully  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Great  
<strong>\<sarang\></strong> Any questions for worriedrise on this?  
<strong>\<sarang\></strong> We will certainly continue to keep investigating it  
<strong>\<suraeNoether\></strong> Brief update on Konferenco: we are beginning to purchase travel tickets for speakers  
<strong>\<suraeNoether\></strong> tickets to the konferenco will be on sale soon(tm)  
<strong>\<suraeNoether\></strong> if anyone wants to submit an abstract, please don't hesitate\! konferenco.xyz  
<strong>\<sarang\></strong> very excited\!  
<strong>\<suraeNoether\></strong> we have a great lineup of speakers, and we need more\!  
<strong>\<sarang\></strong> Perhaps we can convince worriedrise/randomrun :D  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I saw you will be in NY in May too  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Another conference  
<strong>\<h4sh3d\[m\]\></strong> What kind of speaker are you looking for?  
<strong>\<suraeNoether\></strong> we are having more speakers added later today, by the way; i believe we may have someone from the human rights foundation and/or an activist working in venezuela to come speak, and we are having the executive director at coincenter, Jerry Brito, come speak, too  
<strong>\<suraeNoether\></strong> h4sh3d\[m\]: any technical content related to monero or privacy enhancing technologies in general are welcome  
<strong>\<suraeNoether\></strong> we are having some speakers on the social impacts of these technologies too; scholarly work only, no ICOs, a gathering of intelleckshuals  
<strong>\<suraeNoether\></strong> basically: if you have an idea for an abstract, you may as well submit it  
<strong>\<suraeNoether\></strong> worriedrise: i will be at MCC yes  
<strong>\<sarang\></strong> lucky suraeNoether \!  
<strong>\<suraeNoether\></strong> i have a feeling i'll be put to work organizing. :P  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Since we are talking about other technologies, what do you think of the idea of having monero addresses as Bitmessage addresses, as I proposed  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> <https://github.com/monero-project/research-lab/issues/51>  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I saw that there is an issue with the order of encryption and authentication  
<strong>\<sarang\></strong> Seems clever if used correctly\!  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> But assuming we get over that  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Thank  
<strong>\<suraeNoether\></strong> yeah, it shouldnt' be too rough, i just haven't sat down and thought about it yet  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Would you care to explain what the problem is  
<strong>\<suraeNoether\></strong> the easy way to fix it is with a tailored key structure  
<strong>\<suraeNoether\></strong> okay, so basically  
<strong>\<suraeNoether\></strong> when you are encrypting and authenticating, you don't want to authenticate-and-then-encrypt, followed by verification-then-decryption  
<strong>\<suraeNoether\></strong> er.. followed by decryption-then-verification i mean  
<strong>\<sarang\></strong> (swap the latter version)  
<strong>\<sarang\></strong> yeah  
<strong>\<suraeNoether\></strong> this is a bad way to do things because you end up decrypting something without knowing who it came from  
<strong>\<suraeNoether\></strong> if, on the other hand, the ciphertext is signed by the authenticating key, you know whoever signed it approves of the ciphertext  
<strong>\<suraeNoether\></strong> so first you check the signature, then you decrypt  
<strong>\<nioc\></strong> no idea if it has any relevance but I believe it was rbrunner that was using bitmessage for his multisig scheme (MMS)  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> What is wrong with not knowing who it came from?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Can't you stablish that later?  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> Once you see the key?  
<strong>\<suraeNoether\></strong> well, here's an example  
<strong>\<sarang\></strong> You wouldn't know if the encrypted message had been altered  
<strong>\<suraeNoether\></strong> of why the implementation is dangerous  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I would know that is was signed by the accompanying key. Are you saying I wouldn't know if the key was switched?  
<strong>\<suraeNoether\></strong> the extreme and silly example is "what if an app developer decrypts the ciphertext and starts executing it as code while checking in parallel that the signature is valid? then you are running arbitrary code without knowledge of what's in it or whatever." and this seems like it has an easy fix, right, is that the developer should be doing things in the other order...  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> At first contact, I would just have to take wahtever key it was given, but from that point on, I would know whether further messges are signed by the same person  
<strong>\<suraeNoether\></strong> but actually, the answer is no, the encrypt/decrypt should be going in the other order so a bad developer can't make that mistake  
<strong>\<suraeNoether\></strong> this is using a silly but very malicious example  
<strong>\<suraeNoether\></strong> there are more harmless examples like sarang's mention that you don't know if the ciphertext is actually going to decrypt to the intended plaintext.  
<strong>\<suraeNoether\></strong> and to be frank, that's the root of the problem  
<strong>\<moneromooo\></strong> What is an app developer fails to check for signature check fail and starts executing the ciphertext as code ?  
<strong>\<suraeNoether\></strong> ciphertext is indistinguishable from white noise, so their code would do nothing with high probability :D  
<strong>\<sarang\></strong> what a ride that would be  
<strong>\<moneromooo\></strong> The ciphertext is under attacker control.  
<strong>\<suraeNoether\></strong> <https://link.springer.com/chapter/10.1007/3-540-44448-3\_41> worriedrise this paper is pretty seminal in the area  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> I see. I have to think more about that one. I wonder how that problem is handled in Bitmessage currently  
<strong>\<suraeNoether\></strong> moneromooo: ah yeah, that's true, but at that point your developer is merely executing random code it's received from an extra party  
<strong>\<moneromooo\></strong> That was what you assumed too :)  
<strong>\<sarang\></strong> In the interest of time, let's review action items and then continue further discussion  
<strong>\<sarang\></strong> I will keep talking with suraeNoether about output selection if he has additional thoughts/concerns, will review the MLSAG change in detail, and continue toying around with Lelantus  
<strong>\<sarang\></strong> and watch my funding request =p  
<strong>\<suraeNoether\></strong> hm moneromooo no, in my example, the developer decrypts first :D  
<strong>\<sarang\></strong> suraeNoether: your action items for the week?  
<strong>\<suraeNoether\></strong> 1) funding request, 2) monthly report for last month, 3) simulations, 4) dlsag security, 5) reduced mlsag security  
<strong>\<suraeNoether\></strong> oh and fun reading on parazoa  
<strong>\<sarang\></strong> Neato  
<strong>\<sarang\></strong> Any final questions or remarks before we formally adjourn?  
<strong>\<sarang\></strong> Thanks for joining us worriedrise today  
<strong>\<xmrmatterbridge\> \<worriedrise\></strong> My pleasure. Thnks for having me  
<strong>\<sarang\></strong> Thanks to everyone for attending. We are now adjourned\!
