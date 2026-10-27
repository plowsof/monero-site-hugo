---
title: Logs for the Monero Research Lab Meeting Held on 2019-06-03
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> OK, let's begin our meeting  
<strong>\<sarang\></strong> Hello  
<strong>\<sarang\></strong> Or rather, GREETINGS (according to the agenda)  
<strong>\<suraeNoether\></strong> howdydoodily neighborini  
<strong>\<sarang\></strong> Lots to talk about today  
<strong>\<sarang\></strong> Anyone else around today?  
<strong>\<suraeNoether\></strong> hrmm. :P we need a publicist, it seems  
<strong>\<sarang\></strong> Well, let's go ahead with ROUNDTABLE anyway  
<strong>\<sarang\></strong> The DLSAG paper is now on IACR as a preprint: <https://eprint.iacr.org/2019/595>  
<strong>\<suraeNoether\></strong> whoooo  
<strong>\<sarang\></strong> (the usual reminder that preprints are \_not\_ peer reviewed as a prereq to being on the archive)  
<strong>\<needmoney90\></strong> is this thing on  
<strong>\<sarang\></strong> yo  
<strong>\<suraeNoether\></strong> needmoney90: welcome  
<strong>\<needmoney90\></strong> I dont have much to say, but ill watch intently  
<strong>\<sarang\></strong> CLSAG is also available, currently in a monero-site MR: <https://repo.getmonero.org/monero-project/monero-site/merge\_requests/1080>  
<strong>\<sarang\></strong> It will be submitted to IACR once suraeNoether gives it one last read-through  
<strong>\<wow-discord\></strong> \<Crappyrules Ⓤ\> lurking intensifies  
<strong>\<suraeNoether\></strong> ^ i'm reading through this sucker one more time before we submit to IACR, i'll be done later this afternoon  
<strong>\<sarang\></strong> Those are two big projects that we'll be glad to receive feedback on  
<strong>\<suraeNoether\></strong> not wow-discord, but the paper before it :P  
<strong>\<sarang\></strong> lol  
<strong>\<sarang\></strong> Any questions on DLSAG or CLSAG before we move on?  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> A new sublinear transaction protocol, Omniring, was posted: <https://eprint.iacr.org/2019/580>  
<strong>\<sarang\></strong> suraeNoether and I had been looking over early versions of it, courtesy of the authors  
<strong>\<sarang\></strong> It's a very clever construction, but note that the batching numbers are incorrect  
<strong>\<sarang\></strong> I'm told those will be updated in a later revision  
<strong>\<suraeNoether\></strong> I spent this weekend on real\_or\_random et al's omniring paper, which is really elegant, imo. i'm also reading more about ringct3.0, lelantus, and spartan. sarang and i have our eyes on a comparison/state-of-the-art paper describing these different approaches and looking at concrete impacts on the monero chain if we upgrade protocols  
<strong>\<Isthmus\></strong> Hey, I’m intermittently here  
<strong>\<suraeNoether\></strong> neat, while we have you, do you want to jump in on the round table and describe what you've been working on?  
<strong>\<sarang\></strong> Yes, I've begun running the numbers we need for Lelantus, using my toy implementation of it  
<strong>\<suraeNoether\></strong> sarang is anyone working on a python implementation of omni for comparison purposes afayk?  
<strong>\<Isthmus\></strong> I’m just making new transaction tree tracing heuristics  
<strong>\<sarang\></strong> Isthmus: nice\!  
<strong>\<sarang\></strong> Anything to share at this point?  
<strong>\<Isthmus\></strong> Step 1) Have gotten to the point of identifying wonky txns  
<strong>\<Isthmus\></strong> Step 2) upcoming: look for wonky transactions who contain similarly wonky ring members  
<strong>\<Isthmus\></strong> Which implies following true spend path with high probability  
<strong>\<Isthmus\></strong> Step 3) fix it so we don’t leak this info moving forward  
<strong>\<sarang\></strong> Are some of these heuristics a result of protocol choices?  
<strong>\<sarang\></strong> Or bad user behavior?  
<strong>\<Isthmus\></strong> Bad wallet behavior - wrong decoy Alto, etc  
<strong>\<Isthmus\></strong> Ooh gotta run into a meeting, back in a bit probably  
<strong>\<sarang\></strong> np  
<strong>\<sarang\></strong> To your question, suraeNoether  
<strong>\<Isthmus\></strong> \*algo  
<strong>\<sarang\></strong> it's probably not necessary to do a full implementation of Omniring to assess its complexity  
<strong>\<sarang\></strong> For Lelantus it was, since many building blocks were unspecified  
<strong>\<sarang\></strong> e.g. signatures  
<strong>\<sarang\></strong> Oh, another note... my research report for the previous month is available: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/34#note\_6373>  
<strong>\<suraeNoether\></strong> I'm still drafting my research report, and I apologize to the community for the delay. Now that DLSAG and CLSAG are both "out the door," i'm summarizing my work immediately  
<strong>\<sarang\></strong> So yeah, a lot of joint work between suraeNoether and me, for getting CLSAG and DLSAG out the door  
<strong>\<sarang\></strong> and assessing these new sublinear proposals  
<strong>\<sarang\></strong> Does anyone else have research to share?  
<strong>\<sarang\></strong> or suraeNoether, if you have other things to share?  
<strong>\<suraeNoether\></strong> The next 20 days or so are going to come quickly with the konferenco. other than reviewing CLSAG later today, I'm putting paper-writing down until after the conference. the next few weeks will be conference planning primarily and coding for mrl12 secondarily (and keeping up on reading new research as it comes out), with the hopes of finishing mrl12 before the conference.  
<strong>\<sarang\></strong> Excellent  
<strong>\<sarang\></strong> I'm really excited for the conference  
<strong>\<suraeNoether\></strong> but i'm still going to be reading these sublinear protocol proposals and tinkerrrrring  
<strong>\<sarang\></strong> Neato  
<strong>\<suraeNoether\></strong> oh by the way  
<strong>\<suraeNoether\></strong> if you are speaking at the konferenco, please make sure you get your slides to me by June 20 so we can work them into a common slide deck  
<strong>\<sarang\></strong> Cool kids use PDFs for slides :D  
<strong>\<suraeNoether\></strong> and if any speakers have any questions, please feel free to shoot me emails.. I'm catching up on a konferenco backlog  
<strong>\<sarang\></strong> So, this moves to ACTION ITEMS already  
<strong>\<sarang\></strong> suraeNoether will be working to run the conference smoothly, giving the ok for CLSAG to be submitted to IACR, and doing MRL-12 stuffs  
<strong>\<sarang\></strong> (to summarize)  
<strong>\<sarang\></strong> I will be getting those papers up-to-date (on the MRL archive and on IACR), continuing sublinear assessment, and beginning some investigation into ristretto implementation details  
<strong>\<suraeNoether\></strong> yes, and konferenco speakers should make sure they get slides to me before June 20th. many of you hang out in this room :P  
<strong>\<sarang\></strong> I shall submit them to you once I write them :D  
<strong>\<sarang\></strong> but well in advance of the deadline  
<strong>\<sarang\></strong> Despite having many things to discuss, this meeting is going quite quickly  
<strong>\<sarang\></strong> Is there anything to discuss regarding sublinear schemes so far?  
<strong>\<sarang\></strong> One thing to note is that I haven't identified a way to make RCT3 compatible with our key images  
<strong>\<sarang\></strong> Omniring describes a way to do this, and I have a method for Lelantus  
<strong>\<sarang\></strong> Note that Lelantus (like DLSAG) would require a self-spend (i.e. a single churn) to avoid spend tracing  
<strong>\<sarang\></strong> Omniring does not have such a limitation  
<strong>\<suraeNoether\></strong> my understanding is that spartan lacks any transaction structure  
<strong>\<suraeNoether\></strong> so it'd be a ground-up protocol design  
<strong>\<sarang\></strong> Spartan is only a proving system, right  
<strong>\<suraeNoether\></strong> omniring surprised me about how simple it was, considering the heft of the paper, but most of it lies in new rigorous definitions of security, etc  
<strong>\<sarang\></strong> We do not have any kind of circuit-optimized Monero-specific transaction protocol at this time  
<strong>\<sarang\></strong> All of Lelantus, Omniring, and RCT3 provide a full transaction structure  
<strong>\<rehrar\></strong> I have a question for MRL after current discussion ends  
<strong>\<sarang\></strong> Sure, go ahead  
<strong>\<suraeNoether\></strong> well, i don't have more research to discuss, so fire away rehrar  
<strong>\<sarang\></strong> If it's not research related, we can adjourn first  
<strong>\<rehrar\></strong> my issue is with view keys, and while I suspect it's a UX issue, I just wanted to verify that by having MRL confirm my thoughts (or disconfirm them if it is MRL related)  
<strong>\<suraeNoether\></strong> in the words of sarang, 0\_o  
<strong>\<rehrar\></strong> One of the things that's not discussed much is the fact that "view keys" don't live up to their name and are fairly useless in their current form.  
<strong>\<sarang\></strong> In that you only inherently get incoming information?  
<strong>\<rehrar\></strong> Giving just a view key to someone doesn't do much in terms of accounting purposes.  
<strong>\<rehrar\></strong> yes  
<strong>\<sarang\></strong> Yes, it's a limitation for sure  
<strong>\<rehrar\></strong> you need key images  
<strong>\<rehrar\></strong> and I'm not aware of any tool that allows easy import/export of key images  
<strong>\<moneromooo\></strong> monero-wallet-cli  
<strong>\<rehrar\></strong> to make a REAL view key wallet  
<strong>\<rehrar\></strong> moneromooo: for non-nerds  
<strong>\<rehrar\></strong> I'm talking about Small Business Man Billy who wants to show his books to his accountant  
<strong>\<rehrar\></strong> I'm talking about Farmer Joe who needs to prove to the IRS something or other  
<strong>\<rehrar\></strong> these guys aren't going to use CLI  
<strong>\<sarang\></strong> So what you're asking for is a good user-friendly way to export the information that Billy's accountant can import to verify details?  
<strong>\<moneromooo\></strong> They're not going to use Monero in the first place :)  
<strong>\<rehrar\></strong> now, as I said, this may just be a UX thing, and only a matter of time until someone makes it easy, similar to exa wallet multi sig thing today  
<strong>\<rehrar\></strong> sarang: or if this is a limitation that must be adhered to period  
<strong>\<rehrar\></strong> moneromooo: it's a catch 22 bro, one of the reasons they may not use monero is because of stuff like this, but stuff like this doesn't get fixed because they won't use monero  
<strong>\<moneromooo\></strong> Someone posted a way to make the view key also view outgoing txes IIRC. It's way down in the issues list in the monero repo.  
<strong>\<sarang\></strong> What limitation exactly?  
<strong>\<sarang\></strong> The need for key images at all?  
<strong>\<sarang\></strong> Or how convenient the software makes it to import/export?  
<strong>\<rehrar\></strong> sarang: more like what moneromooo is saying  
<strong>\<sarang\></strong> The key image requirement is currently a protocol limitation, for sure  
<strong>\<rehrar\></strong> a way to make view key also viewing outgoing  
<strong>\<suraeNoether\></strong> moneromooo: if there is a way to make the viewkey outgoing also, i haven't seen it and i'd love to. i've been thinking about it for awhile  
<strong>\<rehrar\></strong> without key images  
<strong>\<sarang\></strong> Yes, that's been a discussion over time, but hasn't been brought up in a while  
<strong>\<sarang\></strong> I recall seeing an idea (perhaps the one moneromooo is talking about)  
<strong>\<sarang\></strong> If anyone has the link, I'd like to refresh my understanding of it  
<strong>\<ArticMine\></strong> This if I recall came up last year over AML / KNC  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> i had this idea the other day: SBMB could publish an accumulator that contains his key images, in a way that allows the auditor to check if a given key image is in the accumulator, but the auditor has to trust that the accumulator was constructed faithfully (unless some protocol is used to prove fairness). that plus the view key of the wallet allows the auditor to determine 1) all incoming XMR to that wallet  
<strong>\<suraeNoether\></strong> and 2) any outgoing viewkeys included, allowing the auditor to determine anupper bound remaining in the wallet  
<strong>\<rehrar\></strong> this would (imo) single-handedly would shoot Monero's real world use up incredibly  
<strong>\<moneromooo\></strong> <https://github.com/monero-project/monero/issues/1070>  
<strong>\<suraeNoether\></strong> for some auditors this would be enough, after all you have to trust that the client has actually provided access to all his wallets anyway  
<strong>\<suraeNoether\></strong> thanks moneromooo  
<strong>\<sarang\></strong> Yes, I believe this was the idea that I was vaguely remembering :)  
<strong>\<sarang\></strong> It would be very interesting to reconsider such an idea now that we have multiple ways to make signatures smaller  
<strong>\<suraeNoether\></strong> hmm  
<strong>\<suraeNoether\></strong> that's... very promising.  
<strong>\<rehrar\></strong> as a business man, something like this would be invaluable  
<strong>\<moneromooo\></strong> Note that smooth (IIRC) had misgivings since this gives more spying power to people with the view key.  
<strong>\<suraeNoether\></strong> but it would require a change to the transaction structure  
<strong>\<rehrar\></strong> and would make posting a view key for something like general fund and/or CCS wallet actually useful  
<strong>\<suraeNoether\></strong> unless the extra group element is stashed into tx\_extra and then... well, anyone can put anything in there so  
<strong>\<sarang\></strong> Right, there were concerns about how this affect other users' privacy in practice  
<strong>\<suraeNoether\></strong> wait, i'm not sure about this method  
<strong>\<sfhi\></strong> I agree with rehrar that this would be really valuable for accounting purposes  
<strong>\<rehrar\></strong> obviously if the reduction in privacy heavily outweights the benefits, then perhaps it should be solved on a UX level  
<strong>\<ArticMine\></strong> Can this not be brute forced by using all the existing key images in the blockchain?  
<strong>\<sarang\></strong> Well, regardless of the implications of the linked suggestion, broader thoughts about privacy-aware auditing should be ongoing  
<strong>\<sarang\></strong> Anything else specific to discuss while the meeting is ongoing?  
<strong>\<sarang\></strong> Righto  
<strong>\<sarang\></strong> Well, let's go ahead and adjourn, and let the general discussion continue  
<strong>\<sarang\></strong> Thanks to everyone for attending; logs will be posted to GitHub shortly
