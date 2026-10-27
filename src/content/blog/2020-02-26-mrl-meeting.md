---
title: Logs for the MRL Meeting Held on 2020-02-26
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> Hello all, and welcome to the weekly research meeting  
<strong>\<sarang\></strong> First, GREETINGS  
<strong>\<sarang\></strong> Hi  
<strong>\<UkoeHB\_\></strong> hi  
<strong>\<ArticMine\></strong> hi  
<strong>\<sarang\></strong> \*others  
<strong>\<cankerwort\></strong> Peanut gallery quickly checking in to ask what the latest is on return addresses. Last I remember there was an idea to include a subaddress in the tx as a return address. Is that still being being considered?  
<strong>\<sarang\></strong> It’s always possible to include in tx\_extra, which is not consensus  
<strong>\<sarang\></strong> and there was a space-minimizing proposal as well  
<strong>\<sarang\></strong> AFAIK no one has coded such a thing yet  
<strong>\<sarang\></strong> As always, there’s a consideration of how optional behavior is bad for indistinguishability  
<strong>\<sarang\></strong> Let’s go ahead and start the ROUNDTABLE  
<strong>\<sarang\></strong> Does anyone have research topics of interest to share?  
<strong>\<sarang\></strong> I’ll go ahead, then  
<strong>\<sarang\></strong> First, the Stanford Blockchain Conference was held this past week  
<strong>\<sarang\></strong> Here is a link to the schedule and recordings of talks for each day: <https://cbr.stanford.edu/sbc20/>  
<strong>\<sarang\></strong> Second, a small PR on hash function domain separation was updated, and could always use extra eyes for review: <https://github.com/monero-project/monero/pull/6338>  
<strong>\<sarang\></strong> Third, I made some updates to the structure of CLSAG signature verification code… by reducing the modularity of the signature verification routine to specifically include some commitment offsets, I was able to shave about 5% off the verification time  
<strong>\<sarang\></strong> See this branch for details: <https://github.com/SarangNoether/monero/tree/clsag-optimized>  
<strong>\<Isthmus\></strong> Any particular talks that you recommend from SBC?n  
<strong>\<sgp\_\></strong> hello everyone, catching up on the chat so far  
<strong>\<sarang\></strong> Florian’s talk about Monero and Zcash side-channel analysis on Wednesday’s stream is very good  
<strong>\<sarang\></strong> All of session 4 on Wednesday is interesting  
<strong>\<sarang\></strong> As is session 5 on Thursday  
<strong>\<sarang\></strong> Fourth, I worked on similar improvements for MLSAG… however, this is trickier, since verification requires particular byte-representation hash inputs for backwards compatibility  
<strong>\<sarang\></strong> The results for that aren’t great: <https://github.com/SarangNoether/monero/tree/mlsag-optimized>  
<strong>\<Isthmus\></strong> Ah I loved that paper  
<strong>\<sarang\></strong> Yeah, kudos to Florian and collaborators for great work and responsible disclosure  
<strong>\<sarang\></strong> Finally, another researcher contacted me with an idea for atomic swaps that might remove the need for a SHA-256 preimage proof  
<strong>\<sarang\></strong> We’re still working out the details, but it’s an intriguing idea for which the necessary building blocks already exist  
<strong>\<sarang\></strong> More information as we work on it\!  
<strong>\<UkoeHB\_\></strong> interesting, haven’t heard from atoc in a while who was looking into that  
<strong>\<sarang\></strong> Yeah… I don’t want to provide more information until the researcher and I have discussed it (as a courtesy to them)  
<strong>\<sarang\></strong> sorry  
<strong>\<Isthmus\></strong> Respecting privacy is good ;- )  
<strong>\<sarang\></strong> Anyway, those are my updates\! Mostly code updates and testing  
<strong>\<sarang\></strong> Does anyone else wish to share research of interest?  
<strong>\<UkoeHB\_\></strong> thanks to sarang ‘s initial draft, tx knowledge proofs chapter is done (wip tag is off) for ztm2  
<strong>\<UkoeHB\_\></strong> <https://www.pdf-archive.com/2020/02/26/zerotomoneromaster-v1-0-30/zerotomoneromaster-v1-0-30.pdf>  
<strong>\<UkoeHB\_\></strong> chapter 9  
<strong>\<Isthmus\></strong> Nice\!  
<strong>\<Isthmus\></strong> “An Axiomatic Approach to Block Rewards” <https://arxiv.org/pdf/1909.10645.pdf>  
<strong>\<UkoeHB\_\></strong> sgp\_ may be interested in section 9.3 for audits  
<strong>\<UkoeHB\_\></strong> reader beware various things arent implemented and are just theoretical  
<strong>\<sarang\></strong> Yeah, the idea for a general audit framework is super interesting to me  
<strong>\<sarang\></strong> and could be useful to reduce confusion about what proof types provide what information  
<strong>\<sarang\></strong> Right now, it’s sort of ad-hoc  
<strong>\<cankerwort\></strong> ZtoM will contain unimplemented features and ideas from the roadmap?  
<strong>\<sarang\></strong> Isthmus: that paper is on my literature review list\!  
<strong>\<UkoeHB\_\></strong> also made some updates/fixes to minimum fee change idea <https://github.com/monero-project/research-lab/issues/70> @ArticMine  
<strong>\<sgp\_\></strong> thanks for sharing\! I will see if I can get feedback on it  
<strong>\<UkoeHB\_\></strong> cankerwort part 2 ‘extensions’ contains unimplemented features; saying they are roadmap is quite ambitious  
<strong>\<sarang\></strong> One thing to note about the audit idea from UkoeHB\_ is that it requires proofs applying to \_all\_ transactions for which a given output appears in rings  
<strong>\<sarang\></strong> which I suspect may require substantial engineering effort (as a guess)  
<strong>\<UkoeHB\_\></strong> also proofs for every single tx in the chain  
<strong>\<UkoeHB\_\></strong> for each normal address you own  
<strong>\<sarang\></strong> but the benefits of this approach are worth investigation  
<strong>\<sarang\></strong> IMO  
<strong>\<UkoeHB\_\></strong> audits arent trivial for sure  
<strong>\<cankerwort\></strong> Should be called “ZtoM… and beyond\!”  
<strong>\<UkoeHB\_\></strong> lol yeah  
<strong>\<sgp\_\></strong> I’m familiar with some people who do Monero audits for businesses so I’ll try and get their feedback  
<strong>\<sarang\></strong> UkoeHB\_: fortunately the proofs are all off-chain anyway  
<strong>\<sarang\></strong> So efficiency is much less of a consideration  
<strong>\<UkoeHB\_\></strong> Id refrain from expecting anything in ZtM that isnt implemented to actually get implemented. They are just ideas  
<strong>\<sarang\></strong> UkoeHB\_ and I had discussed this very topic earlier… about the intended purpose of ZtM  
<strong>\<sarang\></strong> e.g. protocol spec, or something else  
<strong>\<Isthmus\></strong> I think that flavoring it with the latest ideas and discussions will convey the lively R &amp; D, provide helpful context, and leave an important historical record  
<strong>\<Isthmus\></strong> In 10 years I want to sit down and nostalgically re-read the old “future work” sections  
<strong>\<sarang\></strong> heh  
<strong>\<sarang\></strong> Anything else to share UkoeHB\_?  
<strong>\<sarang\></strong> (just to keep the meeting on track)  
<strong>\<UkoeHB\_\></strong> dont think so  
<strong>\<sarang\></strong> Cool, thanks for the update  
<strong>\<sarang\></strong> Isthmus: you had chimed in earlier  
<strong>\<sarang\></strong> Did you wish to continue with anything else?  
<strong>\<Isthmus\></strong> Life has been hectic, so haven’t had many Monero moments lately.  
<strong>\<Isthmus\></strong> However  
<strong>\<Isthmus\></strong> n3ptune was doing some data QC/QA and noticed that in a recent preliminary figure I had missed 100 recent transactions with no payment id (encrypted nor unencrypted)  
<strong>\<Isthmus\></strong> But that’s a minor difference  
<strong>\<sarang\></strong> How recent is “recent”?  
<strong>\<sarang\></strong> If you recall  
<strong>\<Isthmus\></strong> Probably this version, but idk  
<strong>\<Isthmus\></strong> It’s only like a 0.5% change over the previously presented data  
<strong>\<Isthmus\></strong> I’ve been working on a little design thought experiment, but it’s still rough and maybe more -lounge appropriate  
<strong>\<Isthmus\></strong> Otherwise, nothing else to report, that I can think of  
<strong>\<sarang\></strong> Got it, thanks  
<strong>\<sarang\></strong> I know suraeNoether said he was unavailable, but would provide an update later today on his recent work  
<strong>\<sarang\></strong> He’s been working on some interesting updates to linkable ring signature security models  
<strong>\<sarang\></strong> I’ve been reviewing those as well  
<strong>\<sarang\></strong> Does anyone else wish to share ongoing research?  
<strong>\<sarang\></strong> Either specific to something mentioned here, or more generally  
<strong>\<sarang\></strong> If not, we can move on to QUESTIONS  
<strong>\<sarang\></strong> OK, looks like no questions so far  
<strong>\<sarang\></strong> Let’s move to ACTION ITEMS before closing the meeting  
<strong>\<ArticMine\></strong> Feasibility of child pas for parent in Monero (child has parent as one of the mixins)  
<strong>\<sarang\></strong> ?  
<strong>\<ArticMine\></strong> pays  
<strong>\<sarang\></strong> Can you elaborate, ArticMine ?  
<strong>\<ArticMine\></strong> In Bitcoin a tx in the tx pool has to low a fee  
<strong>\<sarang\></strong> “has to low a fee”?  
<strong>\<ArticMine\></strong> A second tx is sent using the tx with to low a fee as an input  
<strong>\<sarang\></strong> Sorry, I’m not following  
<strong>\<sarang\></strong> ah  
<strong>\<ArticMine\></strong> The miner miones both txs in a block  
<strong>\<ArticMine\></strong> In the Monero case the child has the tx output of the parent as one of the mixins  
<strong>\<ArticMine\></strong> can be real or fake  
<strong>\<sarang\></strong> What is the specific question you’re getting to?  
<strong>\<Isthmus\></strong> Interesting interesting  
<strong>\<ArticMine\></strong> Can this e done in Monero  
<strong>\<ArticMine\></strong> be  
<strong>\<UkoeHB\_\></strong> oh is it about what can be done if a tx is stuck since its fee is too low?  
<strong>\<UkoeHB\_\></strong> e.g. make a new tx with more fee for it  
<strong>\<ArticMine\></strong> Yes this can e part of the toolkit  
<strong>\<ArticMine\></strong> be  
<strong>\<ArticMine\></strong> but in addition to what I am looking at with the fees, etc  
<strong>\<UkoeHB\_\></strong> we do have 10block lock time atm, so tx spending other tx output doesn’t quite work, though there could be new rules around ‘in the same block’  
<strong>\<Isthmus\></strong> I actually think this seems very plausible  
<strong>\<Isthmus\></strong> You wouldn’t mine only the bump  
<strong>\<Isthmus\></strong> And once the transaction is mined, the bump is unnecessary  
<strong>\<Isthmus\></strong> The bump transaction should have exactly 2 outputs: a plaintext fee and an encrypted change output  
<strong>\<Isthmus\></strong> And reference the first transaction by hash  
<strong>\<UkoeHB\_\></strong> yeah  
<strong>\<sarang\></strong> hmm  
<strong>\<UkoeHB\_\></strong> Im wondering why not just remake the same tx  
<strong>\<UkoeHB\_\></strong> with more fee  
<strong>\<ArticMine\></strong> because of multi sig  
<strong>\<UkoeHB\_\></strong> ah yeah  
<strong>\<sarang\></strong> Huh, that’s a very interesting question  
<strong>\<Isthmus\></strong> Oh, and only 1 bump per transaction  
<strong>\<Isthmus\></strong> You can broadcast more if you want, obviously  
<strong>\<Isthmus\></strong> But only one bump can be claimed by the miner  
<strong>\<Isthmus\></strong> So if you bump with 0.2 XMR then change your mind and send a 0.5 XMR bump, a miner would just ignore the smaller bump  
<strong>\<ArticMine\></strong> Yes  
<strong>\<ArticMine\></strong> but anyone can do the bump in Monero unlike Bitcoin  
<strong>\<cankerwort\></strong> Why “becauae of multisig”?  
<strong>\<Isthmus\></strong> You could design it either way: allow anybody to bump, or require a signature from the original sender to bump  
<strong>\<Isthmus\></strong> (one of the original senders)  
<strong>\<UkoeHB\_\></strong> sounds like it’s possible, although would require protocol level changes (new transaction type, etc)  
<strong>\<midipoet\></strong> wouldn’t being able to do that (child pays for parent) drastically decrease the overall cost of the chain reaction attack?  
<strong>\<ArticMine\></strong> You include the parent as one of the mixins  
<strong>\<Isthmus\></strong> @UkoeHB\_ I’m only here for the protocol level changes :- P  
<strong>\<cankerwort\></strong> Also the big bang attack presumably  
<strong>\<ArticMine\></strong> The miner does know if the parent is real or not  
<strong>\<UkoeHB\_\></strong> ArticMine I don’t know if the parent needs to be a mixin, just include the parent tx hash as part of bump tx, an additional data field  
<strong>\<ArticMine\></strong> That does not mine the parent  
<strong>\<UkoeHB\_\></strong> It would be a new tx type  
<strong>\<UkoeHB\_\></strong> ‘bump tx’  
<strong>\<ArticMine\></strong> Not really  
<strong>\<UkoeHB\_\></strong> RCTTypeBumpIt  
<strong>\<Isthmus\></strong> heh  
<strong>\<sarang\></strong> lol  
<strong>\<ArticMine\></strong> The point of child pays for parent is that in order to mine the child one has to mine the parent  
<strong>\<sarang\></strong> right  
<strong>\<sarang\></strong> But that seems straightforward to enforce, no?  
<strong>\<ArticMine\></strong> In Bitcoin that means spending the output of the parent in the child  
<strong>\<UkoeHB\_\></strong> I think you might get into weird 0-conf territory if can spend an output with 0-block lock time  
<strong>\<Isthmus\></strong> @cankerwort yeah, though as long as the bump density \[XMR per kB\] is higher than transaction density \[XMR per kB\] then they would effectively take up less space (be less effective) for a big bang attack  
<strong>\<UkoeHB\_\></strong> the 10block lock is there for a reason afaik  
<strong>\<UkoeHB\_\></strong> just willy nilly  
<strong>\<ArticMine\></strong> in Monero it means including it in the ring real or fake. The miner does no know  
<strong>\<Isthmus\></strong> Yeah, I think the “bump” transaction needs to be a new type with exactly \[fee delta + change\] outputs and a new field referencing the transaction hash of the transaction to be accelerated  
<strong>\<Isthmus\></strong> And everything is subject to the 10-block lock  
<strong>\<UkoeHB\_\></strong> or you could make it an optional field in normal tx type, to reduce complexity  
<strong>\<ArticMine\></strong> Both are mined in the same block so there is no issue with orphans  
<strong>\<sarang\></strong> UkoeHB\_: not in extra, right?  
<strong>\<sarang\></strong> for parsing etc.  
<strong>\<UkoeHB\_\></strong> no, unless we start enforcing it  
<strong>\<sarang\></strong> aye  
<strong>\<UkoeHB\_\></strong> interesting idea articmine  
<strong>\<cankerwort\></strong> Surely the delta could be as small as you like though? So it could be used to make big bang attack cheaper  
<strong>\<UkoeHB\_\></strong> big bang is about total block weight  
<strong>\<UkoeHB\_\></strong> still have to pay fee for bump tx too  
<strong>\<cankerwort\></strong> Ie you are adding 2 transactions for one fee?  
<strong>\<Isthmus\></strong> The fee in the bump has to cover both the weight of the bump itself and the original transaction  
<strong>\<cankerwort\></strong> Ah  
<strong>\<Isthmus\></strong> So if I have a 5 kB txn and a 2 kB bump, then the total fee has to incentivize the miner to include 7 kB  
<strong>\<ArticMine\></strong> Yes enough to provide an incentive the miner  
<strong>\<ArticMine\></strong> That is the point of child pas for parent also in Bitcoin  
<strong>\<sarang\></strong> Quick note that we should try to finish up soon, since Konferenco has a meeting in a few minutes  
<strong>\<ArticMine\></strong> pays  
<strong>\<sarang\></strong> May we quickly review action items, and then continue discussion?  
<strong>\<ArticMine\></strong> Yes of course  
<strong>\<sarang\></strong> I’ll be working on some review for vtnerd’s 64-bit operation code  
<strong>\<sarang\></strong> as well as some Triptych coding for timing purposes  
<strong>\<sarang\></strong> Others?  
<strong>\<sarang\></strong> OK, then let’s formally adjourn for log posting purposes… please continue discussion\!  
<strong>\<sarang\></strong> Thanks to everyone for attending
