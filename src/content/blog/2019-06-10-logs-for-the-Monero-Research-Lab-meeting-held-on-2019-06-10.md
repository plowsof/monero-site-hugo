---
title: Logs for the Monero Research Lab Meeting Held on 2019-06-10
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Shall we begin the meeting?  
<strong>\<sarang\></strong> GREETINGS  
<strong>\<rehrar\></strong> hi  
<strong>\<sarang\></strong> Who's present?  
<strong>\<kinghat\></strong> ✋  
<strong>\<rehrar\></strong> rehrar is present  
<strong>\<sarang\></strong> I added a special agenda item to discuss CLSAG  
<strong>\<sarang\></strong> Here's the status of it...  
<strong>\<sarang\></strong> the preprint is finished and is posted (with identical content) in the MRL archive and the IACR archive  
<strong>\<sarang\></strong> This does \_not\_ mean it has received formal peer review, because it hasn't  
<strong>\<suraeNoether\></strong> ^  
<strong>\<sarang\></strong> Our friend moneromooo has made excellent progress on a full codebase integration  
<strong>\<sarang\></strong> I'm assisting as needed  
<strong>\<sarang\></strong> I have also reached out to potential auditors to get both the crypto and the implementation checked  
<strong>\<suraeNoether\></strong> preprints like IACR and arxiv are not peer reviewed articles, but they are often treated that way  
<strong>\<sarang\></strong> and am waiting to hear back with details  
<strong>\<rehrar\></strong> anyone who doesn't understand the concept of peer-reviewed doesn't understand science  
<strong>\<sarang\></strong> In theory, if audits happened speedy quick and the code is ready, it \_could\_ be an October thing, but I consider that unlikely  
<strong>\<sarang\></strong> In the meantime, we'll forge ahead and see where the timeline takes us  
<strong>\<sarang\></strong> But barring any big revelations in the process, it's looking good for being integrated into the protocol and code  
<strong>\<rehrar\></strong> sarang: I don't think people like smooth would go for that anyways. There were people that when bps came out, wanted it to exist in the wild a little longer before implementation  
<strong>\<rehrar\></strong> CLSAG is similar. It's existence is young.  
<strong>\<sarang\></strong> Having the preprint out longer doesn't really do much unless it receives implementation  
<strong>\<sarang\></strong> Random thorough review by a qualified person is unlikely, IMO  
<strong>\<rehrar\></strong> and thus we circle back to the same conversation as bps :D  
<strong>\<suraeNoether\></strong> step one: convince wownero to install it wholesale  
<strong>\<needmoney90\></strong> I was about to say that  
<strong>\<wowario\></strong> we can do it, np  
<strong>\<sarang\></strong> Fortunately, the math behind CLSAG is \_much\_ simpler than that of BPs  
<strong>\<sarang\></strong> by a long shot  
<strong>\<suraeNoether\></strong> won't mitigate the need for an audit  
<strong>\<rehrar\></strong> coo'  
<strong>\<suraeNoether\></strong> yeah, i think unlike bulletproofs, this is still an LSAG-based signature, which have been around for awhile  
<strong>\<rehrar\></strong> sarang: is there any way to follow up on the audit requests then? Who knows. Maybe we can speed this along indeed.  
<strong>\<sarang\></strong> The informal review that I have received (won't name names, to avoid the appearance of endorsement) has all been positive  
<strong>\<sarang\></strong> rehrar: I made the requests over the weekend  
<strong>\<sarang\></strong> I'll give a few days :D  
<strong>\<rehrar\></strong> Minko.to should fund the audits since they're single handedly responsible for larger blocks :P  
<strong>\<sarang\></strong> heh  
<strong>\<sarang\></strong> Any other questions on CLSAG?  
<strong>\<sarang\></strong> Otherwise, I'll carry on with audit SoW requests and assisting moneromooo with implementation  
<strong>\<sarang\></strong> Let us move to ROUNDTABLE  
<strong>\<sarang\></strong> suraeNoether: care to go first?  
<strong>\<suraeNoether\></strong> well, my live has turned temporarily into konferenco administrivia  
<strong>\<suraeNoether\></strong> life\*  
<strong>\<suraeNoether\></strong> badges have been ordered, swag bags have been ordered, etc  
<strong>\<sarang\></strong> nice  
<strong>\<suraeNoether\></strong> i'm scrambling behind the scenes to finish up some reimbursement of speakers, etc.  
<strong>\<suraeNoether\></strong> everything is going smoothly and no catastrophes yet to report  
<strong>\<suraeNoether\></strong> we are 12 days out from the event, and i'm eager to start doing non-administrative stuff after the conference  
<strong>\<sarang\></strong> <https://www.youtube.com/watch?v=7trn91xkJ0w>  
<strong>\<suraeNoether\></strong> 14 days from now, my schedule is wiiiiide open  
<strong>\<sarang\></strong> Any questions for suraeNoether ?  
<strong>\<suraeNoether\></strong> my action items for MRL specifically that are not konferenco-related are urgent, though: finish up my research reports and begin my request for funding for the next quarter  
<strong>\<suraeNoether\></strong> these are both on my plate \*as we speak\*  
<strong>\<sarang\></strong> I've begun comparative analysis of sublinear transaction protocols  
<strong>\<sarang\></strong> In particular, did a prototype integration of Monero-to-Lelantus output migration to get better numbers on it  
<strong>\<sarang\></strong> I have to modify my Omniring analysis a bit once I realized that the protocol doesn't natively support plaintext fees  
<strong>\<sarang\></strong> it's a simple change to include them as a separate account, and perhaps built-in support can be made more efficient  
<strong>\<sarang\></strong> (I've brought this up to the authors)  
<strong>\<sarang\></strong> Otherwise, my monthly report for May has been up for a bit: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/34#note\_6373>  
<strong>\<sarang\></strong> and my 2019 Q3 funding request is also open now: <https://ccs.getmonero.org/proposals/sarang-2019-q3.html>  
<strong>\<sarang\></strong> (note that this request, like the 2019 Q2 request, will be paid out immediately when funded)  
<strong>\<rehrar\></strong> how'd that work out for you this time sarang?  
<strong>\<sarang\></strong> I am also working on my Konferenco presentation, of course, on transaction efficiency  
<strong>\<rehrar\></strong> pleased with that?  
<strong>\<sarang\></strong> rehrar: it has gone very well  
<strong>\<sarang\></strong> I think that method of payout provides the most fair value to donors and recipients, provided the trust is there  
<strong>\<sarang\></strong> One last item: there were suggestions to have MRL-type people write up summaries of some of the methods of attack and analysis presented in Breaking Monero  
<strong>\<sarang\></strong> including an assessment of risk  
<strong>\<sarang\></strong> This could provide good information to people who want to know such things  
<strong>\<sarang\></strong> I'm always wary of making claims regarding risk that might not apply to a particular individual's threat model  
<strong>\<sarang\></strong> but posting these as summaries of Breaking Monero topics makes a lot of sense  
<strong>\<sarang\></strong> thoughts on this from the room?  
<strong>\<suraeNoether\></strong> i think it's a good outreach project that augments breaking monero, which is, in turn, a good outreach project  
<strong>\<dEBRUYNE\></strong> sarang: As long as you lay out the risks and what mitigations users can utilize then it should be fine  
<strong>\<sarang\></strong> Right  
<strong>\<dEBRUYNE\></strong> ^ for that we don't need to specify a risk level imo  
<strong>\<suraeNoether\></strong> i feel like this would be a good project for someone interested in learning more about Monero  
<strong>\<sarang\></strong> The complication is that the overall risk depends heavily on what different types of information/ability an adversary has  
<strong>\<sarang\></strong> Modifying the assumptions on your adversary can change a lot  
<strong>\<sarang\></strong> so in no way can this be completely comprehensive  
<strong>\<suraeNoether\></strong> the drawback to that is the delicacy of the various ideas involved, but maybe we could have someone work on some blog post summaries in a back-and-forth workshop style approach, someone who is interested in getting more involved at MRL  
<strong>\<dEBRUYNE\></strong> We can list the assumptions needed to potentially weaken privacy right?  
<strong>\<sarang\></strong> Sure, but a full assessment of the risks of every combination of analysis/attack methods is infeasible  
<strong>\<rehrar\></strong> Perhaps one day somebody can make three common threat models, and look at risk for each of those defined three?  
<strong>\<rehrar\></strong> and people can decide if they fall within or without  
<strong>\<sarang\></strong> If Entity X and Entity Y collude and the user has Z transaction types and computation is very strong...  
<strong>\<rehrar\></strong> and we can have tables and graphs and other science-y stuf  
<strong>\<sarang\></strong> A big issue is always that you don't know what heuristics are "bad enough" for a given use case  
<strong>\<dEBRUYNE\></strong> sarang: Yes, I understand it is a bit of a slippery slope  
<strong>\<sarang\></strong> But anyway, presenting the analysis methods is, at its heart, a good thing  
<strong>\<sarang\></strong> provided it's done very carefully and as honestly as possible  
<strong>\<sarang\></strong> The goal is neither to scare people away nor try to push aside all claims of weaknesses  
<strong>\<sarang\></strong> Any questions on my recent work?  
<strong>\<sarang\></strong> Or, alternatively, does anyone else have other work to present?  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> Well, on to ACTION ITEMS perhaps  
<strong>\<sarang\></strong> suraeNoether already provided his  
<strong>\<suraeNoether\></strong> \<3  
<strong>\<sarang\></strong> Mine are to complete my Konferenco presentation on transaction efficiency, continue assisting with final CLSAG codebase integration, and continue with sublinear transaction protocol analysis  
<strong>\<sarang\></strong> I just read that the Lelantus author had made some changes to make transaction proving more efficient, but didn't see any details... so I'd also like to find out more about that for my analysis  
<strong>\<sarang\></strong> The author and I have had some great discussions so far about making the protocol more efficient  
<strong>\<sarang\></strong> in particular about making batching speedyfast  
<strong>\<sarang\></strong> OK, any last thoughts, questions, or comments before we formally adjourn?  
<strong>\<rehrar\></strong> nah  
<strong>\<sarang\></strong> going once  
<strong>\<sarang\></strong> going twice  
<strong>\<sarang\></strong> adjourned\!  
<strong>\<sarang\></strong> Logs will be posted shortly to the agenda issue on github  
<strong>\<sarang\></strong> Thanks to everyone for joining in
