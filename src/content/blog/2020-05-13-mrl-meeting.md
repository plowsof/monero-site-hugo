---
title: Logs for the MRL Meeting Held on 2020-05-13
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> First, GREETINGS  
<strong>\<sarang\></strong> Hi  
<strong>\<binaryFate\></strong> hello\!  
<strong>\<Isthmus\></strong> Heyo  
<strong>\<h4sh3d\[m\]\></strong> Hello  
<strong>\<ArticMine\></strong> Hi  
<strong>\<sarang\></strong> Next up is ROUNDTABLE  
<strong>\<rehrar\></strong> hi  
<strong>\<sarang\></strong> Does anyone have research of interest to share with the group?  
<strong>\<sarang\></strong> I know Isthmus just mentioned something before we started  
<strong>\<Isthmus\></strong> Hey everybody. I incorporated y'all's feedback on the research proposal (thanks for your input), updated version here: <https://repo.getmonero.org/monero-project/ccs-proposals/-/merge\_requests/142>  
<strong>\<Isthmus\></strong> Most of the changes are in the Roadmap section  
<strong>\<Isthmus\></strong> For phase 1 we've switched to a very formal enumeration of adversary capabilities and Monero features of interest, and will document possible issues and solutions along the lines of:  
<strong>\<Isthmus\></strong> "Monero's \[component\] is vulnerable to \[impact\] by a hypothetical adversary that can leverage \[algorithm\]. In general, the solution must meet \[requirements\]. Current relevant methods include \[cryptosystem\] which would require \[migration process\] and has \[tradeoffs\] that would prevent implementation until \[device bandwidth/resource threshold\] is widely available."  
<strong>\<Isthmus\></strong> Throughout this entire project, the community will receive updates during the weekly \#monero-research-lab meetings. During phase 3 however, several specific documents (the key deliverables from this research) will be freely published:  
<strong>\<Isthmus\></strong> 1. User-friendly writeup: This community-facing writeup will provide an approachable explanation of how hypothetical quantum computers may impact Monero, and possible future mitigations. The writeup should minimize FUD and provide the context that these vulnerabilities apply to almost all cryptocurrencies (not only Monero).  
<strong>\<Isthmus\></strong> 2. Technical documentation: An MRL position paper to distill key information for (current and future) researchers and developers. The writeup should formally describe vulnerabilities, and highlight potential strategies and solutions, noting their tradeoffs. Code snippets may be included if appropriate for pedagogical purposes or clarity.  
<strong>\<Isthmus\></strong> 3. Non-technical 1-pager: An ELI5 / TL;DR summary will be provided for journalists, Monero Outreach, etc. This blurb will discuss risks and myths with no technical jargon, with key takeaways that a broad audience will appreciate.  
<strong>\<Isthmus\></strong> Results and updates will be also disseminated via Twitter threads, Reddit posts, and Breaking Monero videos. :- )  
<strong>\<Isthmus\></strong> (ends notes)  
<strong>\<Isthmus\></strong> Oh, I'll X-post the proposal to Reddit today  
<strong>\<sarang\></strong> I like the change in scope, particularly focusing on communicating the current state of the protocol  
<strong>\<sarang\></strong> Moving away from specific things like implementations and proofs-of-concept for changes seems wise, especially considering that the state of the art will change  
<strong>\<Isthmus\></strong> ^ yep  
<strong>\<Isthmus\></strong> It's important to note that many current post-quantum cryptography candidates require large proofs and significant computational resources, and will thus not be suitable for immediate deployment. For this reason, understanding broad strategies and their tradeoff will be more useful than specific implementations. Thankfully, consumer device capabilities increase over time, and researchers continue to  
<strong>\<Isthmus\></strong> discover new faster/smaller proving systems, so these practical barriers are temporary.  
<strong>\<sarang\></strong> Were there any questions for Isthmus about this proposal? (Comments could also be made on the proposal itself to reach a wider audience)  
<strong>\<rehrar\></strong> nop  
<strong>\<sarang\></strong> OK, does anyone else wish to share research of interest?  
<strong>\<sarang\></strong> If not, I have a few items to share  
<strong>\<h4sh3d\[m\]\></strong> Yes, I have something  
<strong>\<h4sh3d\[m\]\></strong> Earlier someone posted this: <https://gist.github.com/RubenSomsen/8853a66a64825716f51b409be528355f>  
<strong>\<sarang\></strong> Ah yes, the atomic swap idea  
<strong>\<h4sh3d\[m\]\></strong> I had a closer look. The interesting part is the usage of ECDSA adaptor signature  
<strong>\<sarang\></strong> Avoids the use of hash preimage proofs IIRC?  
<strong>\<sarang\></strong> (I have yet to examine it in detail)  
<strong>\<h4sh3d\[m\]\></strong> Yes, the protocol is very close what I already shared here  
<strong>\<h4sh3d\[m\]\></strong> But with the idea of using a cross group dl-proof with an ECDSA adaptor signature might work  
<strong>\<sarang\></strong> At the very least, a cross-group DL equivalence proof is very straightforward  
<strong>\<sarang\></strong> and exists today  
<strong>\<h4sh3d\[m\]\></strong> Yes, that's why it's interesting =)  
<strong>\<h4sh3d\[m\]\></strong> The new part for me is this: <https://lists.linuxfoundation.org/pipermail/lightning-dev/2019-November/002316.html>  
<strong>\<sarang\></strong> Is that link related to the gist?  
<strong>\<Isthmus\></strong> Very cool  
<strong>\<sarang\></strong> Ah, the link is from the gist  
<strong>\<h4sh3d\[m\]\></strong> Yes, it's the first link "single signer ECDSA adaptor signatures" in the Gist  
<strong>\<sarang\></strong> got it  
<strong>\<sarang\></strong> I'm excited to work it out in detail\!  
<strong>\<h4sh3d\[m\]\></strong> With this, we can put one half of the monero key as the adaptor `Y` (or the other half depending if the swap succeed or not)  
<strong>\<h4sh3d\[m\]\></strong> I'd be happy to work on this too. As zkao mentioned it earlier we are thinking about a proposal if it make sense  
<strong>\<sarang\></strong> Having more eyes on ideas like this is definitely a good thing  
<strong>\<sarang\></strong> Thanks for sharing this h4sh3d\[m\] (and zkao earlier as well\!)  
<strong>\<sarang\></strong> Were there any questions for h4sh3d\[m\] ?  
<strong>\<h4sh3d\[m\]\></strong> Cool, I'll continue posting my findings here in the next days.  
<strong>\<sarang\></strong> Thanks, please do  
<strong>\<sarang\></strong> I wanted to finish up some work on next-gen transaction protocols, so I wrote up a proof-of-concept C++ implementation of Arcturus: <https://github.com/SarangNoether/monero/tree/arcturus>  
<strong>\<rehrar\></strong> weeeeee\!\!\!\!  
<strong>\<sarang\></strong> The usual disclaimer that it has not undergone any kind of review, and should be considered unsafe for production use  
<strong>\<sarang\></strong> However, I got timing data from it  
<strong>\<sarang\></strong> I had to rewrite the performance tests for Triptych, MLSAG, and CLSAG for better comparison since Arcturus integrates balance checking directly into the proof (and the others do not)  
<strong>\<sarang\></strong> The results, which I'll paste in just a sec, show that transaction input/output structure plays a role in the overall timing results  
<strong>\<sarang\></strong> Here is data for 1-in-2-out transactions: <https://usercontent.irccloud-cdn.com/file/KZxENlzN/timing-1-2.png>  
<strong>\<sarang\></strong> Here is data for 2-in-2-out transactions: <https://usercontent.irccloud-cdn.com/file/Ww2hDEbo/timing-2-2.png>  
<strong>\<sarang\></strong> These account for the total verification time for signature/proof verification and balance checks  
<strong>\<sarang\></strong> but does not include range proof verification (that's the same for all protocols)  
<strong>\<sarang\></strong> You can get the same data by choosing the appropriate performance test parameters on my `clsag-device` branch (for MLSAG \_and\_ CLSAG), `triptych` branch (for Triptych), and `arcturus` branch (for Arcturus)  
<strong>\<sarang\></strong> The grey lines are centered at the 11-MLSAG point to show the current timing  
<strong>\<binaryFate\></strong> it looks super close to Triptych, any hunch how it would look like for more-inputs and/or more-outputs?  
<strong>\<sarang\></strong> At higher ring sizes, Triptych and Arcturus should stay very close, as the balance check component becomes less relevant overall  
<strong>\<sarang\></strong> The difference mainly arises from whether the balance check group operations are separated (in Triptych) or included in a single multiscalar multiscalar operation with the rest of the proof (in Arcturus)  
<strong>\<sarang\></strong> and that difference goes away at higher ring sizes  
<strong>\<sarang\></strong> The real benefit is in transaction size  
<strong>\<sarang\></strong> I thought I already had Arcturus included in plot data, but it turns out I don't... I'll work that out right after the meeting and post it here  
<strong>\<sarang\></strong> Unrelated to this, I'm coordinating a statement of work for the CLSAG audit with OSTIF and Teserakt, the audit firm that the audit workgroup recommended  
<strong>\<sarang\></strong> Were there any other questions for me on these topics?  
<strong>\<moneromooo\></strong> Oooooh ^\_^  
<strong>\<sarang\></strong> Does anyone else have topics to discuss for the roundtable, before we move on?  
<strong>\<Isthmus\></strong> Hmm, I just remembered a showerthought to generate seashell avatars based on transforming heterogeneously-structured transaction metadata into a signature string, and then running that through surae's visual hash function...  
<strong>\<Isthmus\></strong> I'll try to prototype it this weekend so I can share examples next week (kind of hard to describe abstractly)  
<strong>\<sarang\></strong> Oh man, I remember that seashell work\! It's been a while  
<strong>\<Isthmus\></strong> Yeah, that's a throwback. I forked Surae's repo back in 2018 and turned it into a notebook, but never connected it to Monero input data. <https://github.com/Mitchellpkt/seashells/blob/master/seashells\_notebook.ipynb>  
<strong>\<sarang\></strong> I suppose we can move on to ACTION ITEMS and finish up the meeting if there isn't anything else to discuss  
<strong>\<selsta\></strong> I wish we could display seashells in CLI wallet.  
<strong>\<sarang\></strong> I'll be incorporating some changes to my in-memory key encryption PR, looking into that swap proposal in greater detail, and updating the Arcturus security model for conference submission  
<strong>\<sarang\></strong> Anyone else?  
<strong>\<h4sh3d\[m\]\></strong> I'll study more in details adaptor for ECDSA and rewrite the concerned parts of the atomic swap paper.  
<strong>\<sarang\></strong> You mean updating your original write-up?  
<strong>\<h4sh3d\[m\]\></strong> yes  
<strong>\<sarang\></strong> Excellent  
<strong>\<sarang\></strong> All right, I suppose we can adjourn; thanks to everyone for participating\!  
<strong>\<sarang\></strong> Logs will be posted shortly to the agenda issue
