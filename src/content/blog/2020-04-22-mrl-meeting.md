---
title: Logs for the MRL Meeting Held on 2020-04-22
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> First, GREETINGS  
<strong>\<sarang\></strong> hi  
<strong>\<sgp\_\></strong> Hello  
<strong>\<moneromooo\></strong> .time localtime  
<strong>\<monerobux\></strong> Could not find timezone localtime.  
<strong>\<sgp\_\></strong> .time cdt  
<strong>\<monerobux\></strong> Could not find timezone cdt.  
<strong>\<Isthmus\></strong> First agenda item is trolling the monerobux bot  
<strong>\<sarang\></strong> naturally  
<strong>\<sarang\></strong> Well, let's move to ROUNDTABLE  
<strong>\<atoc\></strong> ooh  
<strong>\<ArticMine\></strong> Hi  
<strong>\<sarang\></strong> I assume Isthmus would like to share the material he posted on the agenda issue?  
<strong>\<sarang\></strong> <https://github.com/monero-project/meta/issues/456>  
<strong>\<sarang\></strong> Specifically: <https://github.com/monero-project/meta/issues/456#issuecomment-617883059>  
<strong>\<Isthmus\></strong> Sure  
<strong>\<sarang\></strong> Go ahead\!  
<strong>\<UkoeHB\_\></strong> hi  
<strong>\<Isthmus\></strong> Just completed a study quantifying the impact of exchange rate volatility for Monero-denominated delayed payouts.  
<strong>\<Isthmus\></strong> Normally I consider exchange rate stuff out of scope for MRL but this is relevant to all CCS-funded contributors  
<strong>\<Isthmus\></strong> Hm, I was going to cut and paste from the GitHub issue but everything is slightly too long for IRC  
<strong>\<Isthmus\></strong> Basically, I put together a sliding window statistical analysis of the XMR price timeseries to create a framework for volatility risk management  
<strong>\<Isthmus\></strong> The TL;DR is this:  
<strong>\<Isthmus\></strong> \[INPUTS:\] X% confidence that a Y-month payout will cover the quote (based on the last Z months of data) can be achieved with an \[OUTPUT:\] V% volatility buffer.  
<strong>\<Isthmus\></strong> Suppose we want to look at the last 24 months of data  
<strong>\<Isthmus\></strong> And consider a 4-month sliding window (1 month to fundraise on CCS + 3 months to execute)  
<strong>\<Isthmus\></strong> Here are the outcomes based on historical data  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/tbl4tkZn/image.png>  
<strong>\<Isthmus\></strong> We observe an unfortunate asymmetry over the past two years, for example: contributors to projects with a 4-month timeline were more than twice as likely to experience a 50% decrease in compensation value (red line) than a 50% increase in compensation value (green line).  
<strong>\<sarang\></strong> That's quite the asymmetry  
<strong>\<Isthmus\></strong> That's the probability distribution function, the cumulative version is helpful too:  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/2UBTfPI7/image.png>  
<strong>\<Isthmus\></strong> The red cross highlights that USD/XMR decreased over 65% of sliding 4-month windows (i.e. only 35% of contributors would receive payouts worth the quote price). The orange cross shows that an 80% likelihood of receiving a sufficient payout would be achieved with a +35% buffer.  
<strong>\<Isthmus\></strong> Explaining the orange cross in the framework described above: 80% confidence that a 4-month payout will cover the quote (based on the last 24 months of data) can be achieved with a 35% volatility buffer.  
<strong>\<Isthmus\></strong> Now, let's consider what happens if we double the timeframe (so that the data include a bull market as well as cryptowinter). The previous plots spanned the last 2 years (blue dots); now let's extend this to 4 years (blue &amp; green dots).  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/aCapoFx3/image.png>  
<strong>\<Isthmus\></strong> oops transparent background, ssorry  
<strong>\<Isthmus\></strong> Now that our we include both the bull run leading up to the all time high and the subsequent decay, the extended data set contains new outcomes on both sides of the red breakeven line (+ a few outliers omitted on this plot that are shown in the next).  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/kiCGTbDh/image.png>  
<strong>\<Isthmus\></strong> Over the 4 year history, we see that about 60% of the windows receive a payout covering the quoted value (red cross). Since the data set now includes an 8x bubble in its entirety, the volatility insurance rate for 80% confidence rises to a 170% buffer (orange cross).  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/le8lMFik/image.png>  
<strong>\<Isthmus\></strong> I'm hoping that having a volatility risk management framework like this will increase funding accessibility for people/businesses that want to contribute but cannot afford speculate on income.  
<strong>\<sarang\></strong> This is great data  
<strong>\<sarang\></strong> Any questions for Isthmus?  
<strong>\<sgp\_\></strong> Volatility is expensive  
<strong>\<sgp\_\></strong> No questions, but thanks for doing this  
<strong>\<Isthmus\></strong> ty :)  
<strong>\<sarang\></strong> I can share next, if there are no other questions for Isthmus  
<strong>\<ArticMine\></strong> More of a comment.  
<strong>\<ArticMine\></strong> Thanks for the work  
<strong>\<atoc\></strong> Yeah thanks, just for more clarity: what are Monero-denominated delayed payouts?  
<strong>\<ArticMine\></strong> What we are dealing with is more like a two bear market as opposed to volatility  
<strong>\<UkoeHB\_\></strong> It seems like long delays in payouts are not worthwhile. Either donators or donation recipients will lose on fiat-equivalent purchasing power with a good probability  
<strong>\<ArticMine\></strong> With the bear trend longer than the term of the typical CCS  
<strong>\<atoc\></strong> ah I see what this is now  
<strong>\<atoc\></strong> I actually wondered about this previously too. This is definitely good info  
<strong>\<moneromooo\></strong> Donators can't lose. They get exactly what they intend in terms of exchange rate. Recipients can lose or win. Other market participants (which could also be the donators or recipients if they choose to play the markets in the meantime) will win or lose.  
<strong>\<UkoeHB\_\></strong> Donators can lose if recipients justifiably ask for premiums in the name of volatility, so donators are paying for the volatility  
<strong>\<sarang\></strong> At any rate, it provides useful information for proposers and potential donors to assess the impacts of volatility  
<strong>\<sarang\></strong> Isthmus: did you want to also discuss TheCharlatan's possible work on timelocks?  
<strong>\<sarang\></strong> (you just posted to the agenda on it)  
<strong>\<ArticMine\></strong> I think volatility is the wrong term here  
<strong>\<Isthmus\></strong> @ArticMine yeah, there may be a more precise way to phrase it. Let me know if you have ideas  
<strong>\<Isthmus\></strong> @sarang sure  
<strong>\<Isthmus\></strong> We discovered a few months ago that Monero's plaintext unlock time leaks information and presents a transaction linkability risk  
<strong>\<Isthmus\></strong> An encrypted unlock time is possible and would solve privacy issues, however the design and performance characteristics must be carefully considered.  
<strong>\<sarang\></strong> Right  
<strong>\<ArticMine\></strong> The issue is a systematic downward trend during the term of the particular CCS  
<strong>\<sarang\></strong> We investigated this with the DLSAG preprint  
<strong>\<Isthmus\></strong> Insight has put together a proposal for Isthmus &amp; TheCharlatan to research solutions over the summer. Looking for feedback on the plan here: <https://github.com/insight-decentralized-consensus-lab/monero\_encrypted\_unlock\_time>  
<strong>\<Isthmus\></strong> Our goals are:  
<strong>\<sarang\></strong> The method from the DLSAG preprint works even without the dual-key output structure, and I have some code demonstrating both the general method and how various LRS constructions could be used for this  
<strong>\<Isthmus\></strong> Detailed system design decisions (e.g. unlock\_time per output or per transaction?)  
<strong>\<Isthmus\></strong> Prototype code to quickly test different approaches , including simulating transaction construction, signing and verification  
<strong>\<Isthmus\></strong> Report of quantified space/time/privacy tradeoffs with each mitigation strategy  
<strong>\<Isthmus\></strong> Implementation code for Monero source tree, for at least one of the chosen approaches  
<strong>\<Isthmus\></strong> Comprehensive research analysis writeup , cross-referenced with code and documentation  
<strong>\<Isthmus\></strong> Oh sorry Sarang, go ahead  
<strong>\<sarang\></strong> Oh no, just providing some background; please continue  
<strong>\<Isthmus\></strong> Oh, that was the end of the list :- )  
<strong>\<sarang\></strong> Ha got it\!  
<strong>\<sarang\></strong> Yeah, so there was already some work on this  
<strong>\<sarang\></strong> and I've been discussing it with TheCharlatan  
<strong>\<sarang\></strong> Basically you can follow an approach similar to that in DLSAG using any d-LRS construction  
<strong>\<sarang\></strong> Meaning MLSAG, CLSAG, Triptych can be used  
<strong>\<sarang\></strong> Obviously the scaling will be different in size/time  
<strong>\<sarang\></strong> But essentially you increase from a 2-LRS (signing key, amount key) to a 3-LRS (signing key, amount key, timelock key)  
<strong>\<sarang\></strong> You also need to change how range proofs are structured, in a nontrivial way  
<strong>\<sgp\_\></strong> Does unlock time per transaction mean all outputs have the same unlock time?  
<strong>\<sarang\></strong> In theory, yes  
<strong>\<sarang\></strong> But it would depend on how it's designed  
<strong>\<Isthmus\></strong> Yep @sgp\_ that's how it works currently  
<strong>\<sarang\></strong> Anyway, there's a marginal increase in transaction size to include the necessary auxiliary commitment data  
<strong>\<sarang\></strong> But more notably, there's a time cost that scales linearly with the ring size  
<strong>\<sgp\_\></strong> Maybe market research some come first to see if there's a demand for per-output. Has this been done at all?  
<strong>\<sgp\_\></strong> \*should come  
<strong>\<sarang\></strong> This time cost exists regardless of whether the locks are per-output or per-transaction  
<strong>\<sarang\></strong> I have C++ timing data for CLSAG to show this, and could modify the new Triptych code similarly  
<strong>\<sarang\></strong> (no point doing it for MLSAG)  
<strong>\<sarang\></strong> Before there's too much time/effort invested in this, I think it'd be useful to determine what costs people think are acceptable to introduce this  
<strong>\<sarang\></strong> The signature stuff is pretty straightforward (from 2-LRS to 3-LRS), but there's additional engineering work for a much different handling of range proofs, which would also need to change the fee structure due to Bulletproofs DoS scaling  
<strong>\<sgp\_\></strong> Does this impact transactions that use the locks only or all of them?  
<strong>\<sarang\></strong> and, of course, the timing hit needs to be considered  
<strong>\<sarang\></strong> Well, for maximum uniformity all outputs would need locks  
<strong>\<sarang\></strong> The lock could be set to 0  
<strong>\<sarang\></strong> but the time cost is the same  
<strong>\<sarang\></strong> Since for every ring member, you need to process its lock data  
<strong>\<sarang\></strong> and the verifier can't tell which locks are 0 due to the commitment structure  
<strong>\<UkoeHB\_\></strong> I feel like knaccc since I can't imagine what utility timelocks have  
<strong>\<Isthmus\></strong> Crossing borders  
<strong>\<moneromooo\></strong> Would encrypting lock times prevent it from being used as a second layer building block ?  
<strong>\<sarang\></strong> Constructions involving cross-chain and off-chain channels would need them  
<strong>\<sgp\_\></strong> Isthmus: how many transactions use these locks again? I lean towards not pursuing this unless there's a known demand  
<strong>\<sarang\></strong> moneromooo: encrypting timelocks were originally designed for 2nd layer stuff in DLSAG  
<strong>\<gingeropolous\></strong> i thought the second chain requires the kind of time locks that we don';t have yet  
<strong>\<sarang\></strong> They aren't required for DLSAG, but they are useful to avoid spend heuristics  
<strong>\<gingeropolous\></strong> second layer, sorry  
<strong>\<sarang\></strong> e.g. ring members whose locks have just expired may be more likely to be true signers, etc.  
<strong>\<gingeropolous\></strong> but i guess both types would need encryption  
<strong>\<sarang\></strong> Anyway, if the decision is to support timelocks, requiring the commitment structure is good for mitigating heuristics, but it comes at a definite cost  
<strong>\<sarang\></strong> and this cost scales with the ring size  
<strong>\<moneromooo\></strong> I'd be ok with a fair cost if it is instrumental having a good second layer, but not really otherwise.  
<strong>\<gingeropolous\></strong> it seems pretty integral if we want monero to be programmatic money  
<strong>\<sarang\></strong> To be clear, a solution like DLSAG requires timelocks, but does not require encrypted timelocks  
<strong>\<sarang\></strong> It is highly beneficial for uniformity if the timelocks are encrypted, however  
<strong>\<UkoeHB\_\></strong> Isthmus it might help the proposal if there were some basic estimates of costs related to timelocks (storage requirements, additional EC ops), for both CLSAG and then for Triptych.  
<strong>\<sarang\></strong> UkoeHB\_: I already have this data for CLSAG, and presented it quite a while ago  
<strong>\<sarang\></strong> For Triptych there are estimates (the C++ code didn't exist at the time)  
<strong>\<UkoeHB\_\></strong> ah, in which case a link would be nice  
<strong>\<sarang\></strong> I can dig it up after the meeting  
<strong>\<TheCharlatan\></strong> That's only the costs for the signature and commitments though, right sarang?  
<strong>\<sarang\></strong> FWIW the branch is here for 3-CLSAG: <https://github.com/SarangNoether/monero/tree/3-clsag>  
<strong>\<sarang\></strong> TheCharlatan: the range proof wouldn't necessarily incur any extra costs  
<strong>\<sarang\></strong> Depending on if/how the limits are changed  
<strong>\<sarang\></strong> If desired, I can update the new Triptych C++ code to support timelocks, for data on performance differences  
<strong>\<sarang\></strong> it'd be pretty straightforward to do  
<strong>\<sarang\></strong> Anyway, I support the idea if it's based on a solid understanding of the costs, and has general consensus  
<strong>\<sgp\_\></strong> I only really support the research if we know there's a solution on the table that Monero will use for second layer stuff. The "how to encrypt" question will be answered faster than the audit process. Maybe I'm not understanding the application, but I perceive this bug hurdle as needing to come first  
<strong>\<sarang\></strong> sgp\_: we know exactly \_how\_ to do it  
<strong>\<sarang\></strong> (in terms of signature handling)  
<strong>\<sgp\_\></strong> I meant selecting which is best  
<strong>\<sarang\></strong> What's not known are specifics related to range proofs, fee structure, etc.  
<strong>\<UkoeHB\_\></strong> fee would be pretty simple to update afaik  
<strong>\<sarang\></strong> Perhaps. What changes is that the aggregated range proof now needs to account for newly-generated outputs, as well as a proof for each timelock input  
<strong>\<sarang\></strong> But it's still something that would need to be considered and completed in the design/deployment process  
<strong>\<UkoeHB\_\></strong> right  
<strong>\<sarang\></strong> and it also complicates things since there are currently no specific input limits  
<strong>\<sarang\></strong> whereas Bulletproofs have a ceiling-power-of-2 verification cost, which is why we limit the output count  
<strong>\<sarang\></strong> Having a separate bulletproof makes little sense from a size perspective  
<strong>\<UkoeHB\_\></strong> ah hm  
<strong>\<UkoeHB\_\></strong> per-input timelocks may be expensive, but I defer to the estimates /o\\  
<strong>\<Isthmus\></strong> Could we have 1 time per transaction, and an encrypted bit with each output  
<strong>\<Isthmus\></strong> 1 = use encrypted timelock  
<strong>\<Isthmus\></strong> 0 = default (10 blocks)  
<strong>\<sarang\></strong> Isthmus: you still need the signature and range components  
<strong>\<sarang\></strong> How you assign timelock commitments to outputs isn't really relevant there  
<strong>\<Isthmus\></strong> Mmkay, was just trying to think of a way to bee able to lock 1+ outputs without locking your change (without having an encrypted timelock for each output)  
<strong>\<sarang\></strong> That's a pretty minimal size cost  
<strong>\<sarang\></strong> The real kicker is verification  
<strong>\<sarang\></strong> and the specifics on range proof structure  
<strong>\<Isthmus\></strong> Yep, those are key things to nail down first  
<strong>\<sarang\></strong> Well, we have CLSAG code to give real numbers on that cost  
<strong>\<sarang\></strong> and it's easy to modify Triptych to give its costs  
<strong>\<sarang\></strong> What is not known is what time hit is considered reasonable  
<strong>\<sarang\></strong> "as low as possible" isn't a design decision  
<strong>\<sgp\_\></strong> Can I step in since I really need to make sure I understand the big picture here  
<strong>\<sarang\></strong> sure  
<strong>\<sarang\></strong> of course  
<strong>\<sgp\_\></strong> In order to add a feature, there should be at least some stated use for it, especially if there are costs  
<strong>\<UkoeHB\_\></strong> nvm per-output timelocks would be cheap at 8 bytes per additional output, most cost is on input proving side  
<strong>\<sgp\_\></strong> So the main benefit is the ability to add things like DLSAG and other related protocols that could allow second-layer right? That time locks are necessary for second-layer solutions we know about?  
<strong>\<sarang\></strong> Well, and we allow timelocks right now; but they have multiple accepted specifications, and likely introduce spend heuristics  
<strong>\<Isthmus\></strong> s/likely/do/  
<strong>\<sarang\></strong> So their presence and optionality introduce fingerprinting  
<strong>\<sgp\_\></strong> right but they aren't used as far as we know for anything in particular?  
<strong>\<sarang\></strong> ^^ good point  
<strong>\<Isthmus\></strong> Not only are timelocks used  
<strong>\<Isthmus\></strong> 5 different formats are used  
<strong>\<Isthmus\></strong> See the documentation linked above  
<strong>\<sarang\></strong> that's what I meant  
<strong>\<Isthmus\></strong> So SOMEBODY is using them  
<strong>\<Isthmus\></strong> They're anonymous, unfortunately, so I don't know their use case  
<strong>\<sarang\></strong> Requiring a uniform format is an obvious first step  
<strong>\<UkoeHB\_\></strong> what fraction of all tx have non-zero timelocks?  
<strong>\<TheCharlatan\></strong> sgp\_ they are also useful for atomic swap purposes, if you are looking for specific features.  
<strong>\<jwinterm\></strong> was about to ask same UkoeHB\_  
<strong>\<sgp\_\></strong> <https://usercontent.irccloud-cdn.com/file/xIfs2dFC/table>  
<strong>\<jwinterm\></strong> TheCharlatan, but not in the state that they currently exist, right? I thought atomic swaps require the kind of time locks that bitcoin has - i.e., this tx can't be mined until certain time  
<strong>\<gingeropolous\></strong> yeah right now its payment channels (lightning network) and atomic swaps, for the most relevant application of timelocks (i think)  
<strong>\<Isthmus\></strong> They're not super widely used, on the order of 10k nonzero locktimes  
<strong>\<Isthmus\></strong> Of course, neither are subaddresses ;- )  
<strong>\<jwinterm\></strong> total number of txs is 10M order of magnitude?  
<strong>\<Isthmus\></strong> 6M  
<strong>\<Isthmus\></strong> Almos 7M  
<strong>\<Isthmus\></strong> \*almost  
<strong>\<jwinterm\></strong> .c 1e4/7e6  
<strong>\<monerobux\></strong> jwinterm: 0.001428571429  
<strong>\<sgp\_\></strong> dumb idea: why not threaten to remove this feature entirely unless someone justifies the need?  
<strong>\<jwinterm\></strong> 0.1% more than I would've guessed  
<strong>\<TheCharlatan\></strong> since we are spitballing a bit, Istmus and I also discussed introducing a more compact format. So if encrypting them is deemed undesirable, I believe we should still change their current behaviour to something more sane and less dangerous.  
<strong>\<sgp\_\></strong> if these are caused by someone fucking around for no purpose, then why bother having them  
<strong>\<UkoeHB\_\></strong> compact format?  
<strong>\<sarang\></strong> Do you mean supporting only a single uniform format?  
<strong>\<sarang\></strong> Because this seems like a natural first step  
<strong>\<UkoeHB\_\></strong> iirc they are varints atm, so at most 9 bytes  
<strong>\<sarang\></strong> At least removing the fingerprinting possible within the use of timelocks  
<strong>\<sgp\_\></strong> in order for the \*cool\* time-lock applications to come around, we need to agree to implement something else which would come with a large advance notice. This hasn't happened obviously  
<strong>\<sarang\></strong> Well, and there is no DLSAG-type payment channel use currently available  
<strong>\<Isthmus\></strong> @UkoeHB\_ I thought it was uint64. I got a few outputs locked until 18446744073709551614 (about 500 billion years) over the weekend :- P  
<strong>\<sarang\></strong> Isthmus: something something store of value  
<strong>\<ArticMine\></strong> Using a single format for timelocks seems a sensible first step to me  
<strong>\<UkoeHB\_\></strong> varints have up to 63 bits of information from what I understand  
<strong>\<Isthmus\></strong> oh yea  
<strong>\<sarang\></strong> OK, so in the interest of time, what's a good next step in this design process?  
<strong>\<UkoeHB\_\></strong> cost estimates  
<strong>\<sarang\></strong> Isthmus TheCharlatan: let's discuss that after the meeting  
<strong>\<TheCharlatan\></strong> Exactly, but a varint for a timelock is completely overblown. There have been a lot of discussions on this in Bitcoin as well, for example to restrict the size to a 1 byte value that is then interpreted as a power of time.  
<strong>\<ArticMine\></strong> single format  
<strong>\<sgp\_\></strong> I say the cost estimate of only the cheapest option to begin with to see if that action is warranted  
<strong>\<TheCharlatan\></strong> Personally I would get rid of time based lock times entirely.  
<strong>\<Isthmus\></strong> That introduces a correction term when blocktime changes  
<strong>\<Isthmus\></strong> But that's easy enough to do  
<strong>\<sgp\_\></strong> TheCharlatan: haha exactly, or at least aggressively ask for justification from people who use them  
<strong>\<sarang\></strong> OK, so beyond investigating optimal single-format cleartext use and updated cost estimates, anything else on this topic for right now?  
<strong>\<sarang\></strong> (otherwise we could discuss it for hours...)  
<strong>\<sarang\></strong> going once  
<strong>\<sarang\></strong> going twice  
<strong>\<sarang\></strong> sold  
<strong>\<sgp\_\></strong> nope, I just want to stress that we need to know why they are used before slowing down transactions  
<strong>\<sarang\></strong> I can briefly share a couple things in the time we have left  
<strong>\<sarang\></strong> I overhauled Triptych verification to support common-key batching  
<strong>\<TheCharlatan\></strong> and s/time/two - deleted the wrong word :(  
<strong>\<sarang\></strong> New timing data: <https://usercontent.irccloud-cdn.com/file/TWAkCeJJ/timing.png>  
<strong>\<sarang\></strong> This data represents the input-amortized verification cost for a 2-input set of signatures  
<strong>\<sarang\></strong> Assuming the same ring is used across both inputs for Triptych  
<strong>\<sarang\></strong> (for MLSAG/CLSAG it doesn't matter)  
<strong>\<sarang\></strong> I also overhauled the MLSAG tests for better consistency with the other series  
<strong>\<UkoeHB\_\></strong> wait isnt that way faster?  
<strong>\<sarang\></strong> It should be  
<strong>\<selsta\></strong> What are amortized inputs?  
<strong>\<sarang\></strong> If you have a 2-input transaction, you need to compute 2 signatures  
<strong>\<sarang\></strong> For MLSAG/CLSAG, this takes twice the time as one signature  
<strong>\<sarang\></strong> For Triptych, if you use the same ring, you get huge batching benefits  
<strong>\<sarang\></strong> So this is the per-input cost for a 2-input transaction  
<strong>\<sarang\></strong> For higher-input-count txs that would share rings, the benefits get even better  
<strong>\<UkoeHB\_\></strong>  
<strong>\<sarang\></strong> The gray crossed lines are centered at the current N=11 MLSAG point  
<strong>\<sarang\></strong> This implies that Triptych becomes slower than right now (for 2-input txs) between N=64 and N=128  
<strong>\<sarang\></strong> (but you can't split the difference... you need to pick a power of 2)  
<strong>\<sarang\></strong> Anyway, hopefully this gives more realistic timing data, at least across 2-input txs  
<strong>\<sgp\_\></strong> is 128 about the same time as DLSAG 12? 13?  
<strong>\<sarang\></strong> You can use my `triptych` branch and `clsag-device` branch to construct this data for yourself  
<strong>\<sarang\></strong> I don't have C++ data for DLSAG  
<strong>\<sgp\_\></strong> soory I meant MLSAG  
<strong>\<sarang\></strong> I'd have to run some quick MLSAG tests on those intermediate numbers  
<strong>\<sarang\></strong> I can have that shortly after the meeting (need to do a new build)  
<strong>\<sgp\_\></strong> it's fine, not that important  
<strong>\<sarang\></strong> It's easy, just takes a few minutes  
<strong>\<sarang\></strong> Anyway, that's what I wanted to share  
<strong>\<sgp\_\></strong> cool stuff  
<strong>\<sarang\></strong> Does anyone else have research to share (we're running a little long, but that's ok)  
<strong>\<UkoeHB\_\></strong> very cool  
<strong>\<UkoeHB\_\></strong> hi yes, this proposal went up this week <https://github.com/monero-project/monero/issues/6456>  
<strong>\<UkoeHB\_\></strong> it's a synthesis of discussion and research from IRC over the past months  
<strong>\<sarang\></strong> It's very comprehensive :)  
<strong>\<sarang\></strong> I admit that I haven't had a chance to sit down and devote time to it :/  
<strong>\<sarang\></strong> However, do you have any concrete suggestions at this point UkoeHB\_?  
<strong>\<UkoeHB\_\></strong> there needs some debate about whether to pursue Janus, and which solution to adopt, but otherwise tx structure recommendations, sorted tlv, and view tag all seem concrete to me  
<strong>\<sarang\></strong> Neat  
<strong>\<sarang\></strong> I'll devote time to it before the next meeting for sure  
<strong>\<UkoeHB\_\></strong> also moving to mandating 1 tx pub key for 2-out tx, and 1 key per output for \>2 out tx  
<strong>\<sarang\></strong> Many thanks for continuing work on that  
<strong>\<sarang\></strong> OK, let's briefly review ACTION ITEMS before we adjourn  
\< is that assuming that every 2-output txn has a change output?  
<strong>\<Isthmus\></strong> \*change or dummy  
<strong>\<UkoeHB\_\></strong> we only have to make that assumption if Janus is implemented  
<strong>\<Isthmus\></strong> Ok, so then if there's a txn being split between 2 (non-change) recipients, it must be constructed as a 3-output txn with a dummy output, right?  
<strong>\<UkoeHB\_\></strong> right  
<strong>\<Isthmus\></strong> Eh that seems harmless. Is a corner case anyways.  
<strong>\<Isthmus\></strong> Sorry @sarang go ahead  
<strong>\<sarang\></strong> Someone volunteered to do a review of the CLSAG code, which was very helpful... they also recommended adding Poly1305 authentication to wallet encryption, which is a good idea to prevent chosen-ciphertext adversaries  
<strong>\<sarang\></strong> Aside from that, I'll pull up some 3-CLSAG and 3-Triptych data to help the timelock discussion, as well as some stuff on Arcturus  
<strong>\<sarang\></strong> that's all for me :)  
<strong>\<sarang\></strong> Anyone else?  
<strong>\<Isthmus\></strong> I'll expand the timelock proposal with some more references/data/use cases  
<strong>\<Isthmus\></strong> And I'll probably finish another quantum-resistance proposal today or tomorrow, currently incorporating feedback into the first draft  
<strong>\<sarang\></strong> great  
<strong>\<sarang\></strong> Any other final action items before we adjourn?  
<strong>\<Isthmus\></strong> Oh yea, and I'll read UkoeHB\_ 's epic github issue :- )  
<strong>\<sarang\></strong> Righto, we are now adjourned\! Thanks to everyone for a great meeting
