---
title: Logs for the MRL Meeting Held on 2020-03-11
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> OK, let's begin the meeting\!  
<strong>\<sarang\></strong> Agenda is here: <https://github.com/monero-project/meta/issues/445>  
<strong>\<sarang\></strong> Logs will be posted there after the meeting  
<strong>\<suraeNoether\></strong> good morning  
<strong>\<sarang\></strong> First on the list, GREETINGS  
<strong>\<sarang\></strong> hi  
<strong>\<sarang\></strong> Note that because of a recent time change for the United States and elsewhere, these meetings will take place at 17:00 UTC instead of 18:00 UTC  
<strong>\<ArticMine\></strong> hi  
<strong>\<Isthmus\></strong> heya sarang and artic  
<strong>\<sarang\></strong> I suppose we can move on to ROUNDTABLE  
<strong>\<sarang\></strong> Who wishes to share research topics of interest?  
<strong>\<vtnerd\></strong> hi  
<strong>\<UkoeHB\_\></strong> Hi  
<strong>\<suraeNoether\></strong> well  
<strong>\<suraeNoether\></strong> i want to give a brief two-part update  
<strong>\<sarang\></strong> Go ahead suraeNoether\!  
<strong>\<suraeNoether\></strong> firstly, personally: i'm going to have to take a break from monero for a few weeks while i get this medical stuff figured out. importantly: i'm not stopping work. I just don't know how much time i can actually contribute practically.  
<strong>\<sarang\></strong> Oof, sorry to hear this. I hope everything goes well for you suraeNoether  
<strong>\<ArticMine\></strong> sorry to hear this. I hope all goes well  
<strong>\<suraeNoether\></strong> secondly: my research into matching is a hydra where fixing one bug is revealing handfuls of more bugs, and i'm getting super frustrated with it. this is particularly important work for a few reasons, but for right now i don't anticipate movement any time soon. one of the reasons that this has become so frustrating to me is that certain threats to monero that are going to become more likely over the  
<strong>\<suraeNoether\></strong> next several years to be presenting themselves that make the answers that lie within this work \*lower priority\* than other things. i mean this very specifically in the following sense  
<strong>\<suraeNoether\></strong> everyone should know that our anonymity reduces to something like the one-more decisional diffie hellman problem, and our unforgeability reduces to something like one-more discrete logarithm  
<strong>\<suraeNoether\></strong> both of these are known to not be hard for quantum adversaries, and while quantum computers are not yet practical...  
<strong>\<suraeNoether\></strong> it doesn't matter what ring size we use if china goes "manhattan project" on quantum computers and turns their resulting computing power on de-anonymizing privacy coins in secret.  
<strong>\<suraeNoether\></strong> my work on matching would give us answers to questions like "how large should ring sizes be \*assuming the underlying problem that our anonymity rests upon is hard to solve\*" but we know that this problem is only going to be hard over the short term  
<strong>\<sarang\></strong> FWIW such a "quantum adversary" could wreak havoc on basically the entire global internet  
<strong>\<suraeNoether\></strong> indeed ^ but that's in fact exactly all the more reason to become resistant to a quantum adversary sooner rather than later  
<strong>\<UkoeHB\_\></strong> How realistic is a quantum adversary?  
<strong>\<ArticMine\></strong> ^ I agree  
<strong>\<suraeNoether\></strong> if it takes 3 years to migrate to a quantum-secure system, and we hope something like clsag or triptych has a 3 year shelf life, then we should be looking at what will be practical 6 years from now  
<strong>\<sarang\></strong> In the shorter term, understanding the effects of ring size on matching-type analysis is useful for knowing how large to make ring size for a next-gen protocol  
<strong>\<Isthmus\></strong> Uhm  
<strong>\<Isthmus\></strong> Would an adversary with a quantum computer break ring signatures or just decrypt the transactions?  
<strong>\<suraeNoether\></strong> both: they can compute the discrete log of every one-time key and then they just own all of monero  
<strong>\<Isthmus\></strong> Yeah, I'd just do that.  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<suraeNoether\></strong> so like  
<strong>\<sarang\></strong> Once you have key discrete logs, you can check key images  
<strong>\<suraeNoether\></strong> matching: important. investigating quantum-secure schemes: higher priority, even over a relatively short 3-year term  
<strong>\<suraeNoether\></strong> so every time i kill a bug in my matching code, i become more painfully aware: i'm fighting the wrong hydra  
<strong>\<sarang\></strong> I still think it's very valuable  
<strong>\<Isthmus\></strong> Yeah, we've been doing some quantum vs crypto experiments at Insight lately  
<strong>\<suraeNoether\></strong> long story short, i'm prsently working on a summary-of-knowledge of quantum-resistant RingCT-type protocols, 3 of which have been proposed in the past 3 years  
<strong>\<sarang\></strong> Otherwise, "bigger rings are better" is a qualitative statement  
<strong>\<suraeNoether\></strong> just for community education reasons  
<strong>\<suraeNoether\></strong> sarang: absolutely agreed  
<strong>\<sarang\></strong> My recent work on Triptych-2 and chain simulations shows, as expected, that ring size has a large effect on verification complexity  
<strong>\<UkoeHB\_\></strong> Can you also evaluate how realistic a quantum adversary is? I recall general skepticism of them ever materializing  
<strong>\<sarang\></strong> So choosing the smallest rings that do the job is important  
<strong>\<suraeNoether\></strong> UkoeHB\_: yeah, so basically here's a qualitative answer to that question  
<strong>\<Isthmus\></strong> We're already working on 5 \[actual\] qbits  
<strong>\<Isthmus\></strong> (Insight working on IBM equipment)  
<strong>\<Isthmus\></strong> Expecting this to scale in the next few years  
<strong>\<suraeNoether\></strong> you may recall the sensationalist headlines a few months ago: <https://www.eurekalert.org/pub\_releases/2020-02/aps-teo022720.php>  
<strong>\<suraeNoether\></strong> quantum supremacy is probably a bad term but  
<strong>\<suraeNoether\></strong> before these researchers did what they did, the \*fastest way to figure out what a quantum computer can do\* would be to \*simulate it on a classical computer\*  
<strong>\<sarang\></strong> Quantum supremacy is a poor metric for usefulness IMO  
<strong>\<sarang\></strong> Such problems are typically highly contrived  
<strong>\<suraeNoether\></strong> because of these guys' work, that is no longer the case: there now exist quantum computers that cannot be simulated more quickly than they can operate. this is a critical benchmark for scaling quantum  
<strong>\<Isthmus\></strong> @surae should I just loop in my quantum/crypto engineer for a few weeks, so you can focus on the matching hydra?  
<strong>\<Isthmus\></strong> They're already looking into the schemes, and would probably be happy to work on Monero  
<strong>\<suraeNoether\></strong> google's bristlecone has 72 qubits running  
<strong>\<suraeNoether\></strong> isthmus: let's set up a call for later this week  
<strong>\<vtnerd\></strong> well I have to say it ... quantum computers are BS, they just spin hyperbole but go nowhere. There was a discussion about this on metzdowd  
<strong>\<Isthmus\></strong> Given retroactive denonymization doesn't really matter if they're 5 or 15 years off, we gotta hustle to protect Monero users in 2020  
<strong>\<suraeNoether\></strong> do you mean like computers based on quantum principles will never work, vtnerd? can you clarify?  
<strong>\<suraeNoether\></strong> isthmus ^ bingo  
<strong>\<vtnerd\></strong> someone discussed the progress made on metzdowd. Its been very little over 25+ years  
<strong>\<vtnerd\></strong> the researchers have alwasy been just on the edge of making it a reality  
<strong>\<suraeNoether\></strong> okay well  
<strong>\<suraeNoether\></strong> the researchers into QC i've spoken with disagree  
<strong>\<suraeNoether\></strong> and that's an appeal to authority  
<strong>\<vtnerd\></strong> admitedly this isn't my expertise, but theres time tradeoffs investigating these QC resitistent systems  
<strong>\<suraeNoether\></strong> but i think it's absolutely silly to say that very little progress has occurred over 25 years, and it's even sillier to assume that no progress will be made ala cold fusion, and i think it's even sillier to propose that we, say, avoid quantum-secure implementations rather than looking into the costs and benefits and time horizons of implementing them  
<strong>\<vtnerd\></strong> and the one thing thats bizarre, is when someone builds a QC system, we basically ahve to reboot on general purpose computing projects, no? Like one year out are they even cracking crypto?  
<strong>\<suraeNoether\></strong> well, i don't want to take more time on this: my update is that i have to step back from monero for awhile, and i'm looking into RLWE-based ring signatures  
<strong>\<Isthmus\></strong> Y'all know the tech cycle. Many-year winters leads to the most exciting explosions. AI, crypto, quantum... the pattern repeats  
<strong>\<suraeNoether\></strong> i'll still be presenting at meetings and coming by and stuff  
<strong>\<suraeNoether\></strong> for folks who are interested, the wikipedia article on the timeline of quantum computing has lots of good info  
<strong>\<sarang\></strong> OK thanks suraeNoether  
<strong>\<sarang\></strong> I have a few things to share  
<strong>\<sarang\></strong> First, CLSAG  
<strong>\<sarang\></strong> I've completed review of suraeNoether's security model updates  
<strong>\<sarang\></strong> suraeNoether: I've left several Overleaf review comments for you  
<strong>\<sarang\></strong> Along with that, I migrated some recent CLSAG verification optimization code to moneromooo's branch, along with relevant unit and performance tests  
<strong>\<sarang\></strong> Saves about 5% on verification, which seemed worth it  
<strong>\<sarang\></strong> Relating to Triptych: I made a minor update to the original Triptych-1 preprint for readability, but also completed the Triptych-2 preprint  
<strong>\<sarang\></strong> Here is a link to the Triptych-2 preprint on Overleaf: <https://www.overleaf.com/read/ynfkhykjfvrd>  
<strong>\<sarang\></strong> I'd appreciate any review on it prior to posting to the IACR archive  
<strong>\<sarang\></strong> Unrelated to these, I've been catching up with literature review  
<strong>\<sarang\></strong> and, as a program committee member for the IEEE S&amp;B conference, I'm reviewing submissions  
<strong>\<suraeNoether\></strong> i'll take a look at your comments and read through triptych 2: electric bugaloo  
<strong>\<sarang\></strong> Thanks suraeNoether  
<strong>\<sarang\></strong> IMO the CLSAG review is top priority  
<strong>\<selsta\></strong> Did you contact Teserakt?  
<strong>\<sarang\></strong> I'd like to wait on confirming a schedule until we have this paper done  
<strong>\<sarang\></strong> Otherwise we risk losing the availability again due to delays  
<strong>\<sarang\></strong> Anyone who wants to review the CLSAG optimizations can see this branch: <https://github.com/SarangNoether/monero/commits/clsag-mooo>  
<strong>\<sarang\></strong> Finally, my funding proposal needs feedback on GitLab before it's decided whether to open it: <https://repo.getmonero.org/monero-project/ccs-proposals/-/merge\_requests/131>  
<strong>\<sarang\></strong> That's all for me today  
<strong>\<sarang\></strong> Does anyone else wish to present, or have questions?  
<strong>\<suraeNoether\></strong> i propose that we fund sarang  
<strong>\<suraeNoether\></strong> but no  
<strong>\<suraeNoether\></strong> no questions  
<strong>\<Isthmus\></strong> I propose that we fund surae  
<strong>\<sarang\></strong> Heh, then leave a reaction or comment on gitlab\!  
<strong>\<Isthmus\></strong> I've been wrestling with a weird conundrum  
<strong>\<sarang\></strong> Go on  
<strong>\<Isthmus\></strong> I'm thinking about modifying my wallet to only select decoys from transactions generated by the core wallet  
<strong>\<Isthmus\></strong> But then that in and of itself becomes a subtle heuristic  
<strong>\<sarang\></strong> Ah, so using fingerprinting to pick the most "standard" decoys?  
<strong>\<Isthmus\></strong> Not "most"  
<strong>\<Isthmus\></strong> Something either looks like the core wallet, or provably isn't  
<strong>\<sarang\></strong> Heh, yeah, it kicks the fingerprinting can slightly down the road  
<strong>\<Isthmus\></strong> I guess if almost everybody used only outputs generated by the core wallet, then it wouldn't be a heuristic to fingerprint me  
<strong>\<Isthmus\></strong> \*outputs that cannot be proven to have not originated from the core wallet  
<strong>\<Isthmus\></strong> ^ to be very specific  
<strong>\<sarang\></strong> got it  
<strong>\<Isthmus\></strong> Eh, I dunno. Don't really have a solution. It was just funny that I worked on it for a it before realizing that it becomes its own heuristic xD  
<strong>\<Isthmus\></strong> Anyways, nothing much from me. I've had about 20 minutes per week for Monero lately  
<strong>\<Isthmus\></strong> But in May, we're gonna have some long talks and clean house  
<strong>\<sarang\></strong> ?  
<strong>\<Isthmus\></strong> Have 7 heuristics that have now partitioned out upwards of 20 different implementations.  
<strong>\<Isthmus\></strong> Most of which I've shared in MRL already  
<strong>\<UkoeHB\_\></strong> 20 sounds like a lot  
<strong>\<UkoeHB\_\></strong> monero is really doing well if there are 20  
<strong>\<Isthmus\></strong> That's unfiltered for time.  
<strong>\<Isthmus\></strong> Going to clean it to recent blocks and see what's in the wild \*now\*  
<strong>\<sarang\></strong> So some might be updates to the same implementations?  
<strong>\<Isthmus\></strong> It's at least 3 right now,  
<strong>\<Isthmus\></strong> Yeah, that's why I'm not really sweating the 20  
<strong>\<Isthmus\></strong> I think it's 3-5 in current era  
<strong>\<Isthmus\></strong> Which is pleasantly(?) surprising  
<strong>\<Isthmus\></strong> But yea, with absolutely no time to work on it now, hard to put together a full writeup  
<strong>\<Isthmus\></strong> But will definitely circle back in the next 2 months  
<strong>\<sarang\></strong> Sounds good\!  
<strong>\<sarang\></strong> Anyone else wish to share any research?  
<strong>\<UkoeHB\_\></strong> hi, ztm2 proofreading draft is updated (with feedback from sarang about bulletproofs, and also the clawback formula regarding tx weights) <https://www.pdf-archive.com/2020/03/11/zerotomoneromaster-v1-1-1/zerotomoneromaster-v1-1-1.pdf>  
<strong>\<UkoeHB\_\></strong> 2 more weeks for proofreading  
<strong>\<sarang\></strong> Good feedback so far overall?  
<strong>\<UkoeHB\_\></strong> also, looked into next-gen tx key image generation for multisig (sarang has a solution for it), and it seems like inversion key images wont greatly disrupt multisig transaction flows (especially escrowed markets, which is a big deal)  
<strong>\<UkoeHB\_\></strong> Not much feedback so far  
<strong>\<UkoeHB\_\></strong> But it's 152 pages so not surprising  
<strong>\<UkoeHB\_\></strong> that's all from me  
<strong>\<sarang\></strong> OK, let's move on to ACTION ITEMS for the next week or so  
<strong>\<sarang\></strong> I'll await final word on my CLSAG review notes  
<strong>\<UkoeHB\_\></strong> wondering if ArticMine has progress on fees  
<strong>\<sarang\></strong> Continue working on Triptych  
<strong>\<Isthmus\></strong> Why did it switch from 02 to 20?  
<strong>\<Isthmus\></strong> oops  
<strong>\<ArticMine\></strong> Yes I do  
<strong>\<Isthmus\></strong> ignore that  
<strong>\<sarang\></strong> Go ahead ArticMine\!  
<strong>\<ArticMine\></strong> I am looking at making the penalty free one also dynamic and using the long term median to control it  
<strong>\<ArticMine\></strong> Also slowing down the fall in the long term median to match the constraint on the rise  
<strong>\<sgp\_\></strong> just got caught up  
<strong>\<ArticMine\></strong> So it does not go from say 3000000 bytes 300000 bytes in one shot  
<strong>\<ArticMine\></strong> The new dynamic penalty free one would track the long term median at say 20 - 25% of the long term median  
<strong>\<Isthmus\></strong> Ooh interesting  
<strong>\<ArticMine\></strong> This will provide predictable fee over time  
<strong>\<sarang\></strong> Will you have a specific proposal for this, intended for a network upgrade?  
<strong>\<ArticMine\></strong> The models I am looking at is a sharp drop, followed by a fiat banking crisis that creates a very sharp rise  
<strong>\<ArticMine\></strong> Yes  
<strong>\<sarang\></strong> OK, any final thoughts or topics before we wrap up this hour?  
<strong>\<suraeNoether\></strong> be kind to each other  
<strong>\<suraeNoether\></strong> just be excellent  
<strong>\<suraeNoether\></strong> you animals  
<strong>\<sarang\></strong> All right, thanks to everyone for attending. Adjourned\!
