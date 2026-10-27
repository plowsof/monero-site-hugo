---
title: Overview and Logs for the Dev Meeting Held on 2017-12-17
summary: Discussion of open PRs and issues, Bulletproofs, March HF, dedicated HW wallet, and miscellaneous
tags: [dev diaries, core, crypto]
author: dEBRUYNE / fluffypony
---

# Overview

An overview can be found on [MoneroBase](https://monerobase.com/wiki/DevMeeting_2017-12-17).

# Logs

<strong>\<fluffypony\></strong> 1. Greetings  
<strong>\<fluffypony\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<fluffypony\></strong> 3. March hardfork items + code freeze  
<strong>\<fluffypony\></strong> 4. Code + ticket discussion / Q &amp; A  
<strong>\<fluffypony\></strong> 5. Any additional meeting items  
<strong>\<fluffypony\></strong> 6. Confirm next meeting date/time  
<strong>\<fluffypony\></strong> I think we’ve done 1. so we’ll skip it  
<strong>\<fluffypony\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<fluffypony\></strong> well Bulletproofs went live on testnet  
<strong>\<fluffypony\></strong> so there’s that  
<strong>\<fluffypony\></strong> and we merged some stuff  
<strong>\<fluffypony\></strong> moneromooo: anything in particular you want to highlight?  
<strong>\<moneromooo\></strong> Ah, whether to enable them for v7 or v8 on mainnet.  
<strong>\<fluffypony\></strong> that’s the next point  
<strong>\<fluffypony\></strong> I meant anything in 2. you want to highlight :)  
<strong>\<moneromooo\></strong> Not in particular, no.  
<strong>\<HUCK45\></strong> Hey all, I just saw that awesome project recently and a question came to my mind- why there isn’t any option for GPU mining instead of CPU? Browsers these days allow that, by webgl for example (depending on the user settings, but on default it uses gpu)  
<strong>\<fluffypony\></strong> HUCK45: we’re in a meeting - feel free to take that to \#monero  
<strong>\<rehrar\></strong> HUCK45 we’re in a dev meeting right now. :) This’ll have to wait.  
<strong>\<suraeNoether\></strong> as far as MRL is concerned: the math on bulletproofs seems tight, but the best test for cryptography is time  
<strong>\<fluffypony\></strong> ok so I’ll highlight a few PRs  
<strong>\<fluffypony\></strong> suraeNoether: not there yet  
<strong>\<suraeNoether\></strong> oh woops  
<strong>\<fluffypony\></strong> \#2878 tightens up —offline mode by disabling DNS lookups  
<strong>\<fluffypony\></strong> \#2877 refactors a bunch of p2p stuff  
<strong>\<fluffypony\></strong> and then the obvious bug fixes and improvements  
<strong>\<fluffypony\></strong> Bulletproofs on testnet is in \#2883  
<strong>\<fluffypony\></strong> which brings us to 3. March hardfork items + code freeze  
<strong>\<fluffypony\></strong> so v7 already has sorted inputs  
<strong>\<fluffypony\></strong> moneromooo: do you want to explain that?  
<strong>\<moneromooo\></strong> Sorted inputs? Or bp ?  
<strong>\<moneromooo\></strong> I assume bp. They’re just a smaller sized range proof system.  
<strong>\<fluffypony\></strong> sorted inputs  
<strong>\<fluffypony\></strong> I assume everyone knows what BP is  
<strong>\<moneromooo\></strong> Well, just… sort inputs by their key image. Nothing more.  
<strong>\<iDunk\></strong> Is it like unsorted inputs, but sorted ?  
<strong>\<fluffypony\></strong> iDunk: kinda  
<strong>\<gingeropolous\></strong> and why sort?  
<strong>\<moneromooo\></strong> Kinda :)  
<strong>\<fluffypony\></strong> gingeropolous: that’s the big question  
<strong>\<iDunk\></strong> Cool :)  
<strong>\<gingeropolous\></strong> :)  
<strong>\<fluffypony\></strong> it’s to prevent metadata leaking  
<strong>\<fluffypony\></strong> eg. the specific wallet used for a tx  
<strong>\<moneromooo\></strong> To avoid broken implementations leak stuff. It’d be better for outputs (ie, always put change last, etc), but unfortunately it doesn’t work for outputs as the keys depend on their index.  
<strong>\<moneromooo\></strong> It has become hairy after subaddresses unfortunately, at least for the small benefit.  
<strong>\<luigi1111w\></strong> which?  
<strong>\<moneromooo\></strong> What is the question ?  
<strong>\<luigi1111w\></strong> what is “it”  
<strong>\<fluffypony\></strong> ordering outputs  
<strong>\<moneromooo\></strong> inputs.  
<strong>\<luigi1111w\></strong> subaddress or multisig?  
<strong>\<moneromooo\></strong> I’ll rephrase:  
<strong>\<moneromooo\></strong> The input sorting code has become hairy after subaddresses unfortunately, at least for the small benefit.  
<strong>\<luigi1111w\></strong> yes that was clear, just not why  
<strong>\<luigi1111w\></strong> well was clear after \<moneromooo\> inputs.  
<strong>\<moneromooo\></strong> Because the sorting was internal to construct\_tx before, now it’s changed in the caller as well.  
<strong>\<luigi1111w\></strong> ok  
<strong>\<moneromooo\></strong> So that means you have to order selected\_transfers too, and possible something else, can’t recall exactly.  
<strong>\<moneromooo\></strong> Anyway, it’s just minutiae particular to our wallet code.  
<strong>\<luigi1111w\></strong> btw, change being last doesn’t leak metadata  
<strong>\<moneromooo\></strong> It doesn’t leak that change is that ?  
<strong>\<moneromooo\></strong> It doesn’t leak that change is last ?  
<strong>\<luigi1111w\></strong> right  
<strong>\<luigi1111w\></strong> or what wallet was used  
<strong>\<moneromooo\></strong> OK, it leaks that change is more likely to be last than otherwise.  
<strong>\<luigi1111w\></strong> is it?  
<strong>\<luigi1111w\></strong> what if a popular wallet puts it first  
<strong>\<moneromooo\></strong> x+epsilon \> x, even if epsilon is very small.  
<strong>\<moneromooo\></strong> (assuming epsilon is positive)  
<strong>\<fluffypony\></strong> luigi1111w: the onus is on wallets to follow the pattern  
<strong>\<luigi1111w\></strong> what pattern  
<strong>\<luigi1111w\></strong> why is there a pattern  
<strong>\<moneromooo\></strong> I’m lost here, I’ll wait.  
<strong>\<luigi1111w\></strong> me too :)  
<strong>\<moneromooo\></strong> Maybe ask your question again, rephrased :)  
<strong>\<pigeons\></strong> I guess if there is an intentional pattern, there won’t be several accidental identifying ones  
<strong>\<rbrunner\></strong> Fingerprinting wallets?  
<strong>\<luigi1111w\></strong> my point is chnage isn’t a fingerprinting pattern for wallets  
<strong>\<luigi1111w\></strong> well my new point, whatever  
<strong>\<luigi1111w\></strong> anyway it doesn’t really matter as we’re not doing it anyway  
<strong>\<fluffypony\></strong> ok let’s talk about Bulletproofs then  
<strong>\<fluffypony\></strong> suraeNoether: your turn :)  
<strong>\<suraeNoether\></strong> whelp, i pretty much had my piece in terms of bulletproofs: there isn’t a research-oriented approach to answer if they are ready for implementation.  
<strong>\<suraeNoether\></strong> the best test for crypto is use and time.  
<strong>\<suraeNoether\></strong> the math has been reviewed, looks tight. it may feel like it’s being put into production too soon, but…  
<strong>\<suraeNoether\></strong> any time we implement something new, we take some risks in that regard  
<strong>\<suraeNoether\></strong> it looks to me like a no-brainer drop-in replacement for our current range proofs, and to sarang it seems fine. the coding is done.  
<strong>\<msvb-mob\></strong> suraeNoether: Is there a way to merge new features on testnet only?  
<strong>\<msvb-mob\></strong> Maybe a risk reduction strategy I mean?  
<strong>\<suraeNoether\></strong> afaik BP is already on testnet as of … today?  
<strong>\<moneromooo\></strong> As of a week back or so.  
<strong>\<suraeNoether\></strong> ah there you go  
<strong>\<msvb-mob\></strong> So we have at least that granularity, okay.  
<strong>\<luigi1111w\></strong> I’m going through the code and have some questions  
<strong>\<suraeNoether\></strong> yeah, i mean  
<strong>\<suraeNoether\></strong> luigi1111w: sarang will be able to answer them tomorrow afaik.  
<strong>\<rehrar\></strong> Is the chance of finding meaningful vulnerabilities that much greater if we extend it out to September hard fork? Like, would the extra six months be an adequate amount of time if it was determined that the three months between now and March hardfork wasn’t sufficient?  
<strong>\<suraeNoether\></strong> ^ this is actually sort of the tough spot we find ourselves in  
<strong>\<suraeNoether\></strong> thing is, there isn’t a real monetary incentive to attack something like BP while its on testnet  
<strong>\<luigi1111w\></strong> attacking it on mainnet is catastrophic, however  
<strong>\<suraeNoether\></strong> yep  
<strong>\<suraeNoether\></strong> its like designing a new parachute  
<strong>\<rbrunner\></strong> Well, we could put bounties for Testnet attacks, no?  
<strong>\<luigi1111w\></strong> meh  
<strong>\<rehrar\></strong> It’s simple. We make testnetcoin a 3B dollar project.  
<strong>\<fluffypony\></strong> sure, but then we shouldn’t ever deploy anything  
<strong>\<fluffypony\></strong> :-P  
<strong>\<fluffypony\></strong> LOL rehrar  
<strong>\<suraeNoether\></strong> lol  
<strong>\<suraeNoether\></strong> eventually someone has to strap it onto their own backs and jump  
<strong>\<suraeNoether\></strong> is what i mean  
<strong>\<fluffypony\></strong> yes  
<strong>\<fluffypony\></strong> so here’s my thinking  
<strong>\<luigi1111w\></strong> the people that could review and attack are pretty small in number  
<strong>\<fluffypony\></strong> we code freeze via a 0.12 branch in the next 2-ish weeks  
<strong>\<fluffypony\></strong> we include BP for the March HF  
<strong>\<fluffypony\></strong> we release test bins in Jan  
<strong>\<fluffypony\></strong> we re-measure our confidence towards the end of Jan / beginning of Feb  
<strong>\<fluffypony\></strong> if we’re not happy with it we change it to v8  
<strong>\<fluffypony\></strong> or the opposite - put it in v8 and move it to v7 towards the end of Jan if we’re confident  
<strong>\<luigi1111w\></strong> much more comfortable with the latter  
<strong>\<luigi1111w\></strong> though there’s plenty of support for delaying v7 as well  
<strong>\<rehrar\></strong> I think delaying v7 by a couple months would be well worth it?  
<strong>\<rehrar\></strong> and even if the next fork is still held to September, we will still have the multi-input BP to merge, which is exciting, no?  
<strong>\<fluffypony\></strong> I don’t think we should move fork dates  
<strong>\<rehrar\></strong> or were both single and multi output BPs being discussed right now?  
<strong>\<moneromooo\></strong> Single only.  
<strong>\<fluffypony\></strong> it’s becoming increasingly difficult, and sticking to the predictable fork schedule is advantageous for exchanges, merchants, and pools  
<strong>\<fluffypony\></strong> (emergency hard forks aside)  
<strong>\<moneromooo\></strong> I’m reasonably sure most don’t know in advance when the fork is supposed to be anyway.  
<strong>\<luigi1111w\></strong> ^^  
<strong>\<rehrar\></strong> other loser coins: “oh btw mister exchange, we’re forking in like two weeks, please update software”  
<strong>\<fluffypony\></strong> moneromooo: they’re starting to know  
<strong>\<dEBRUYNE\></strong> As long as they are notified well in advance I don’t see a problem with pushing it back 1-2 months  
<strong>\<dEBRUYNE\></strong> Like moneromooo says, most probably don’t even know we have one scheduled for march  
<strong>\<fluffypony\></strong> pushing it back by 1-2 months isn’t enough time  
<strong>\<luigi1111w\></strong> it might be  
<strong>\<luigi1111w\></strong> although  
<strong>\<fluffypony\></strong> imho we’re either happy with March or we need 6 additional months of testing  
<strong>\<moneromooo\></strong> How about 12 ?  
<strong>\<rehrar\></strong> It may be that in the future FP you might be right, but I think we’re still small enough that we can pull a stunt like this without too many consequences  
<strong>\<fluffypony\></strong> moneromooo: we might need that, if our confidence level is low  
<strong>\<moneromooo\></strong> The confidence will stay low until 3 months before the fork, when people will start looking.  
<strong>\<moneromooo\></strong> Before 3 months, (almost) nobody will look.  
<strong>\<suraeNoether\></strong> if we give ourselves 6 months of testing for BPs  
<strong>\<suraeNoether\></strong> i’ll tell you what’ll happen  
<strong>\<fluffypony\></strong> lol  
<strong>\<suraeNoether\></strong> 5 months an 2 weeks will go by  
<strong>\<fluffypony\></strong> so then March it is?  
<strong>\<moneromooo\></strong> Now, if people did look for 6 months… then yes.  
<strong>\<suraeNoether\></strong> and then testing will begin  
<strong>\<dEBRUYNE\></strong> Pushing it back 6 months might perhaps result in it going down the priority list  
<strong>\<moneromooo\></strong> I’m ready to go for september if there is a good reason (ie, someone says they need the 6 months).  
<strong>\<dEBRUYNE\></strong> And then we just get the same \# of months of review  
<strong>\<fluffypony\></strong> I’m happy with March, but I’m also open to having my mind changed  
<strong>\<fluffypony\></strong> I’m also reaching out to the paper authors to see if any of them are able to do an implementation review  
<strong>\<moneromooo\></strong> smooth thinks it’s too early, for the record.  
<strong>\<rbrunner\></strong> Main argument?  
<strong>\<moneromooo\></strong> At 9 txes per block (monthly average now), I think BPs save \~ 2 GB per month.  
<strong>\<dEBRUYNE\></strong> I think you’ll see more transactions once fees drop to an acceptable level though  
<strong>\<dEBRUYNE\></strong> So savings might be even more  
<strong>\<Vespco\></strong> March with aggressive promotion of testnet usage starting now. We can highlight the need on reddit and provide clear stack exchange instructions and .bins to attract more users  
<strong>\<luigi1111w\></strong> I don’t think that helps  
<strong>\<luigi1111w\></strong> you need math and code people  
<strong>\<luigi1111w\></strong> we may have enough (not now, I mean within the next 3 months)  
<strong>\<rehrar\></strong> Ok, just so the discussion doesn’t go on forever, and to summarize for anyone reading logs afterwards, there’s three main camps here: 1. Launch BPs in March HF, 2. Launch BP’s in September HF, 3. Delay March HF to something like a May HF and launch BPs then.  
<strong>\<rehrar\></strong> Of those three, I’d say 3 is reasonable  
<strong>\<luigi1111w\></strong> there are two other non-forking changes that people would like to see in a release too, subaddresses and multisig  
<strong>\<luigi1111w\></strong> former is in already  
<strong>\<dEBRUYNE\></strong> As the fork height isn’t set yet, can’t we reasses in 2 months?  
<strong>\<luigi1111w\></strong> latter “should” be (IMO) in the next release  
<strong>\<dEBRUYNE\></strong> And see if there has been adequate review  
<strong>\<fluffypony\></strong> luigi1111w: agreed  
<strong>\<luigi1111w\></strong> dEBRUYNE no we are trying to get releases out in reasonable time  
<strong>\<luigi1111w\></strong> ie, not the week before  
<strong>\<moneromooo\></strong> MS is going in soon. Just after I fix the core tests after last rebase :)  
<strong>\<dEBRUYNE\></strong> No I meant whether BP go in or not  
<strong>\<dEBRUYNE\></strong> ^ luigi1111w  
<strong>\<Vespco\></strong> Is GUI ready for multisig and subaaddresses?  
<strong>\<dEBRUYNE\></strong> Or is two months to late for that to decide?  
<strong>\<luigi1111w\></strong> yes  
<strong>\<dEBRUYNE\></strong> too\*  
<strong>\<dEBRUYNE\></strong> Ok  
<strong>\<fluffypony\></strong> dEBRUYNE: basically-final bins need to be out by Feb  
<strong>\<fluffypony\></strong> beginning-ish of Feb  
<strong>\<luigi1111w\></strong> by the time you decide and build the release you’re at like one week  
<strong>\<luigi1111w\></strong> agree  
<strong>\<dEBRUYNE\></strong> But also, if we push back the fork 1-2 months, we have more time to release basically-final bins  
<strong>\<luigi1111w\></strong> well 2 months imo  
<strong>\<luigi1111w\></strong> so whenever in march  
<strong>\<suraeNoether\></strong> i think MRL’s opinion is 2 1 3, to vote for a september hard fork. because if we are wrong, the cost is large. if we are correct, we save 12 G  
<strong>\<suraeNoether\></strong> grand scheme of things  
<strong>\<luigi1111w\></strong> in grand scheme you don’t really save anything  
<strong>\<dEBRUYNE\></strong> If we don’t include BP in March 2018, I suppose we can at least fix the fees :-P  
<strong>\<luigi1111w\></strong> since we “might as well” prune that data  
<strong>\<luigi1111w\></strong> later  
<strong>\<suraeNoether\></strong> luigi1111w: yeah, on a long enough time horizon  
<strong>\<vtnerd\></strong> prune the range proofs?  
<strong>\<luigi1111w\></strong> yes  
<strong>\<fluffypony\></strong> if we did 2, any opinions on reducing the base fee in the March HF? we can increase it again later if we need  
<strong>\<vtnerd\></strong> how would some future user verify inflation?  
<strong>\<luigi1111w\></strong> vtnerd if you desire to do that for your trust model, of course you don’t prune  
<strong>\<dEBRUYNE\></strong> fluffypony: we need to tweak the penalty  
<strong>\<vtnerd\></strong> oh so this is like the bitcoin prune old blocks option  
<strong>\<luigi1111w\></strong> well you don’t lose the hashability  
<strong>\<suraeNoether\></strong> fluffypony: I think dEBRUYNE may have thought about fee structures more than anyone else  
<strong>\<fluffypony\></strong> yes  
<strong>\<luigi1111w\></strong> JollyMort\[m\] :)  
<strong>\<dEBRUYNE\></strong> ^ would certainly beat me :P  
<strong>\<suraeNoether\></strong> fair  
<strong>\<endogenic\></strong> is it worth writing a paper on fee structure modeling etc?  
<strong>\<luigi1111w\></strong> longer term I think yes  
<strong>\<luigi1111w\></strong> but we certainly don’t have time for march  
<strong>\<dEBRUYNE\></strong> Perhaps we could change the penalty exponent to ^3 instead of ^2  
<strong>\<fluffypony\></strong> suraeNoether: what would your comfort level change to if one or more of the paper’s authors reviewed the implementation?  
<strong>\<suraeNoether\></strong> fluffypony: no, the implementation isn’t the concern at all, in my mind at least  
<strong>\<suraeNoether\></strong> assuming it’s passing unit tests  
<strong>\<suraeNoether\></strong> (which i think it is, iirc)  
<strong>\<moneromooo\></strong> It is.  
<strong>\<dEBRUYNE\></strong> What if the paper itself is “broken”? Only time will tell that I guess  
<strong>\<suraeNoether\></strong> there ya go. the question is whether or not someone clever can divide by zero and cause a big monero bang with bullet proofs .  
<strong>\<suraeNoether\></strong> dEBRUYNE: ^ exactly  
<strong>\<suraeNoether\></strong> the best test for crypto is time  
<strong>\<rehrar\></strong> will an aggressive ‘test bps on testnet’ campaign do anything?  
<strong>\<luigi1111w\></strong> no  
<strong>\<suraeNoether\></strong> i don’t think so  
<strong>\<suraeNoether\></strong> if someone found something  
<strong>\<rehrar\></strong> so then that’s points for March HF isn’t it?  
<strong>\<suraeNoether\></strong> it would be worht more for them to wait until it was implemented than to report it  
<strong>\<rbrunner\></strong> I think with no high-value target to attack nobody will aim at BP  
<strong>\<luigi1111w\></strong> I disagree with suraeNoether and would like the implementation reviewed  
<strong>\<rehrar\></strong> if we gain little value for waiting, then we shouldn’t wait  
<strong>\<suraeNoether\></strong> luigi1111w: I dind’t say i dind’t want the implementation reviewed. fluffypony asked me if such a review would make me more comfortable with a March HF  
<strong>\<luigi1111w\></strong> then we still disagree  
<strong>\<luigi1111w\></strong> so it’s fine :)  
<strong>\<suraeNoether\></strong> heh, okay. well at least we can agree that we both want the implementation reviewed one way or another  
<strong>\<moneromooo\></strong> (thanks stoffu btw, who did review it well)  
<strong>\<suraeNoether\></strong> stoffu is a silent hero  
<strong>\<rehrar\></strong> Meeting is coming to a close. Not necessarily to decide right now, but just to see where everyone is, can we have everyone that was in this conversation verbally state whether they prefer March or September for BPs?  
<strong>\<fluffypony\></strong> in terms of someone finding an issue in the math itself, I don’t think that 6 months is a macro-enough timescale for that  
<strong>\<fluffypony\></strong> my preference would be March, pending peer review, or September + fee reduction failing that  
<strong>\<rbrunner\></strong> March: Only with BP live on mainnet you would ever get bright and bad people interested to break something  
<strong>\<suraeNoether\></strong> i have the reversed preference as fluffypony, plus i would like the authors to review the implementation in either case  
<strong>\<suraeNoether\></strong> i think sarang has the same preference as fluffypony though  
<strong>\<vtnerd\></strong> uh, so before meeting adjourns I’d like to prod <https://github.com/monero-project/supercop/pull/1>  
<strong>\<moneromooo\></strong> What we’d need is for people who may review it to tell is now when they would, and how much time they’d need… Not gonna happen most likely.  
<strong>\<vtnerd\></strong> unedited supercop code is all that is now  
<strong>\<luigi1111w\></strong> cool  
<strong>\<pigeons\></strong> pre-borromean ringct signature issue was found by 3rd party (and/after the monero team), so people do look at non-mainnet code. and also that incident shows how short timelines are scary  
<strong>\<endogenic\></strong> ^  
<strong>\<fluffypony\></strong> also msvb-mob wanted to say a couple of things about the HW wallet  
<strong>\<suraeNoether\></strong> pigeons: that’s an extremely good point  
<strong>\<msvb-mob\></strong> Hardware team achieved a breakthrough today in manipulating the MCU factory bootloader without programming.  
<strong>\<msvb-mob\></strong> That means that future firmware developers can flash boards using DFU over USB.  
<strong>\<msvb-mob\></strong> DFU == Device Firmware Upgrade  
<strong>\<fluffypony\></strong> pigeons: good point  
<strong>\<fluffypony\></strong> msvb-mob: nice one\!  
<strong>\<msvb-mob\></strong> In the near future we will ask for in depth advice from core development and MRL to confirm our design is on track.  
<strong>\<msvb-mob\></strong> Any questions? You can ask about 34C3 assembly as well.  
<strong>\<moneromooo\></strong> There is a factory bootloader ? As in, code you did not write ?  
<strong>\<msvb-mob\></strong> moneromooo: Yes, most hardware manufacturers (Nordic, STM, Maxim, TI) supply a default bootloader you can’t get rid of.  
<strong>\<msvb-mob\></strong> And when they’re nice, it’s full of USB and DFU.  
<strong>\<luigi1111w\></strong> pigeons thanks, and that memory pushes me towards the wait camp  
<strong>\<moneromooo\></strong> That sounds like a great idea :/  
<strong>\<msvb-mob\></strong> Next topic.  
<strong>\<luigi1111w\></strong> meeting is basically over afaik  
<strong>\<rbrunner\></strong> Please don’t forget the GUI wallet Windows installer and put it into service sometime after busy Christmas. I have a PR waiting that gives the last polish to the installer script, and after that it’s really, really ready  
<strong>\<fluffypony\></strong> yep that’s it  
<strong>\<fluffypony\></strong> one last thing  
<strong>\<fluffypony\></strong> next meeting would be Dec 31  
<strong>\<fluffypony\></strong> but I don’t think anyone wants that  
<strong>\<fluffypony\></strong> so push out to Jan 14?  
<strong>\<rehrar\></strong> Monero New Year party?  
<strong>\<msvb-mob\></strong> If we do one week later, we synced again with community meetings.  
<strong>\<luigi1111w\></strong> is that what we want?  
<strong>\<luigi1111w\></strong> ok with both  
<strong>\<rehrar\></strong> you guys don’t go anyways :P  
<strong>\<luigi1111w\></strong> and by ok I mean as not ok as normal  
<strong>\<fluffypony\></strong> msvb-mob: I’d prefer us unsynced, otherwise it’s just too much on a weekend  
<strong>\<fluffypony\></strong> wife will murder me :-P  
<strong>\<moneromooo\></strong> Technically, that’s still synced, but out of phase…  
<strong>\* moneromooo</strong> steps back  
<strong>\<msvb-mob\></strong> Nobody is protesting 14 Jan. I’m not opinionated, just wanted to mention the sync aspect.  
<strong>\<fluffypony\></strong> lol moneromooo  
<strong>\<rehrar\></strong> Ok 14 Jan it is
