---
title: Logs for the Monero Research Lab Meeting Held on 2018-11-26
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<sarang\></strong> It's just about time to begin our meeting  
<strong>\<rehrar\></strong> hope you're having all of the fun  
<strong>\<sarang\></strong> all ofit  
<strong>\<suraeNoether\></strong> allllright everyone, let's begin  
<strong>\<suraeNoether\></strong> Greetings from MRL.  
<strong>\<sarang\></strong> heyo  
<strong>\<suraeNoether\></strong> before we really get rolling, does anyone have any questions to open the meeting wiht?  
<strong>\<IRS\></strong> o/  
<strong>\<sarang\></strong> I assume this meeting will be reasonably short, given U.S. Thanksgiving was last week and some of our folks are from U.S.  
<strong>\<suraeNoether\></strong> fire away  
<strong>\<suraeNoether\></strong> okay  
<strong>\<endogenic\></strong> the IRS will never call or IRC you  
<strong>\<suraeNoether\></strong> assuming no questions, let's get going I guess. sarang, want to share what you worked on for the past week or so?  
<strong>\<sarang\></strong> Sure  
<strong>\<sarang\></strong> I have a few things  
<strong>\<sarang\></strong> First, there was interest expressed in possibly getting another researcher on board  
<strong>\<sarang\></strong> It would get funded, but we'd need someone qualified and available  
<strong>\<sarang\></strong> So this is more of a "if you know people, send them our way"  
<strong>\<sarang\></strong> The second thing is that I'm working with those outside researchers from Australia on their spent-output stuff  
<strong>\<sarang\></strong> Turns out they didn't invent the ideas on their papers :/ but it's good formalization  
<strong>\<suraeNoether\></strong> (to be clear, sarang means an outside group has approached us offering to fund a new researcher)  
<strong>\<gingeropolous\></strong> ^ wow  
<strong>\<Inge-\></strong> sweet  
<strong>\<sarang\></strong> Third, still working more on cross-curve discrete log stuff  
<strong>\<rehrar\></strong> what level of researcher are you looking for? full time?  
<strong>\<sarang\></strong> We could easily fund full time, but part time is better than no time  
<strong>\<spaced0ut\></strong> an academic group?  
<strong>\<sarang\></strong> No, it's a foundation  
<strong>\<sarang\></strong> Anyway, just throwing a line out there  
<strong>\<suraeNoether\></strong> rehrar: take what we can get? we have a huge list of todos and all of us have full plates.  
<strong>\<rehrar\></strong> well that's awesome  
<strong>\<suraeNoether\></strong> I kind of feel like research does the following  
<strong>\<suraeNoether\></strong> if human knowledge is a circle (think venn diagram), then the circumference is the interface with the unknown, and adding to the circle of knowledge just makes the circumference bigger  
<strong>\<suraeNoether\></strong> so the problem is that if we add additional people without a firmly defined scope, I fear we will have a mission creep sort of thing happening  
<strong>\<suraeNoether\></strong> i'm eager to have more hands and eyes on our project, for sure  
<strong>\<sarang\></strong> Sure, but that doesn't mean we can't set a reasonable number of desired peeps  
<strong>\<suraeNoether\></strong> ^ yep  
<strong>\<sarang\></strong> For the limited current scope we have, I think at least one more person would be very useful  
<strong>\<sarang\></strong> But again, cart before the horse  
<strong>\<suraeNoether\></strong> I just think we should kick some ideas around on coming up with a more concrete scope  
<strong>\<suraeNoether\></strong> so let's chat about that later, maybe? we have time to chat about it, for sure  
<strong>\<sarang\></strong> First, does evenlessmoney (stick with a handle, dude\!) want to talk about bloat?  
<strong>\<evenlessmoney\></strong> yes, let me repost my message  
<strong>\<sarang\></strong> ty  
<strong>\<suraeNoether\></strong> so we can move on for now, but this has come up in several research meetings before, the prospect of adding to the MRL crew... so we should formalize our ideas about it this week  
<strong>\<sarang\></strong> ArticMine chimed in earlier about it, FWW  
<strong>\<sarang\></strong> FWIW  
<strong>\<evenlessmoney\></strong> The block size adjustment algorithm has been on my mind in recent weeks. I was asked in another chat what the biggest caveats were with the dynamic block size, and after thinking about it, I concluded that a motivated attacker could pay the extra fee to bump the block size, and then maintain a perpetual low cost flood of transactions to bloat the utxo set.  
<strong>\<evenlessmoney\></strong> <https://link.medium.com/OrG5th051R>  
<strong>\<evenlessmoney\></strong> This article underscores the need for our nodes to remain syncable to the masses, it is doubly important that Monero remains syncable on commodity hardware long run, considering the privacy implications a remote node brings.  
<strong>\<evenlessmoney\></strong> After some deliberation, I think capping block size in the code may be necessary, and that allowing it to be dynamic with no upper bound is dangerous. I would love to hear some input from people who are more informed than me on the matter.  
<strong>\<evenlessmoney\></strong> articmine mentioned that he doesnt think that this is an issue, but I had a second question afterwards  
<strong>\<suraeNoether\></strong> one moment let me process this  
<strong>\<ArticMine\></strong> Reading the article  
<strong>\<evenlessmoney\></strong> which involved the centralization of nodes - if our block size has too quick a growth rate, nodes cant sync on commodity hardware  
<strong>\<evenlessmoney\></strong> which is what that article points out  
<strong>\<evenlessmoney\></strong> most of the network would be forced to use remote nodes, unless I'm misunderstanding  
<strong>\<gingeropolous\></strong> its a long article. TL/DR is ethereum is becoming unsyncable and therefore will become centralized  
<strong>\<spaced0ut\></strong> at first glance. if possible to make the attack more expensive is an option it might be worth looking at vs capping the block size. does anyone really want to go there right now?  
<strong>\<evenlessmoney\></strong> its worse for Monero IMO, because we really want to stress users running their own nodes  
<strong>\<gingeropolous\></strong> and any network that becomes unsyncable becomes centralized  
<strong>\<evenlessmoney\></strong> for privacy's sake, not even decentralization  
<strong>\<suraeNoether\></strong> spaced0ut: one option is to add a nonlinear term to fees. another option is to add a momentum term to block size adjustment, or a resistance term, so to speak. however...  
<strong>\<suraeNoether\></strong> evenlessmoney: when we changed our fees, we did make such an attack much less expensive to carry out, but I don't think it's particularly an issue... if folks think it is, we can maybe consider some simulations, etc, and add a resistance term to dynamic block size. this would prevent the block size from responding extremely elastically to network demand...  
<strong>\<suraeNoether\></strong> but we can all see how that leads to an opposite problem, right, where the block size is too rigid and can't change with demand?  
<strong>\<ArticMine\></strong> First unlike Ethereum and Bitcoin Cash there is a cost to bloating the Monero blockchain that is comparable to a 51% attack  
<strong>\<evenlessmoney\></strong> Not on a continuous basis  
<strong>\<evenlessmoney\></strong> only to raise the block size  
<strong>\<evenlessmoney\></strong> once the size is up, you can perpetually fill those blocks with bloat txes for cheap  
<strong>\<ArticMine\></strong> You havee to get it there in the first place  
<strong>\<ArticMine\></strong> have  
<strong>\<gingeropolous\></strong> and any pool can mine those txs in  
<strong>\<evenlessmoney\></strong> You can do a couple percent a block  
<strong>\<evenlessmoney\></strong> its not very expensive when you ratchet it over a few days  
<strong>\<suraeNoether\></strong> evenlessmoney: cheaper than before, but not free, and maintaining a long-term flood is non-trivially expensive, even for super cheap monero fees  
<strong>\<evenlessmoney\></strong> I'm more worried about baseline activity being that high  
<strong>\<evenlessmoney\></strong> and cheap  
<strong>\<evenlessmoney\></strong> in this situation  
<strong>\<evenlessmoney\></strong> if Monero becomes the de facto BTC alternative  
<strong>\<suraeNoether\></strong> in my mind, I don't see this as a practical attack. people have to blow their Monero in order to drag monero's blockchain down... seems like an incentivization problem, not a security problem. and going the opposite direction, by making monero block size more rigid, presents other scaling problems  
<strong>\<spaced0ut\></strong> can we calculate the cost to double the size over time periods in between hard forks? or even calculate the cost to add a terabyte to the size?  
<strong>\<ArticMine\></strong> The cost of bloating to a given size is close to independent of the rate of bloat. One can pay all at once or over time  
<strong>\<suraeNoether\></strong> there are a few options to address this, that don't require deep changes nor totally fixed block sizes, i'm just not convinced of the power of an attacker, and ArticMine's fact re: cost of bloating is a really important factor  
<strong>\<gingeropolous\></strong> well one thing to point out is that the median 100 is a parameter from the original implementation  
<strong>\<suraeNoether\></strong> one option: momentum/resistance term, so that increasing block size is harder the further it is away from some fixed "ideal", which we can always change later  
<strong>\<gingeropolous\></strong> and those guys didn't think some things through fully, so I think its fine to question the block growth rate  
<strong>\<suraeNoether\></strong> another option: coupling block size with past block sizes in a moving average sort of way. similar to the momentum trick  
<strong>\<suraeNoether\></strong> gingeropolous: I agree with that statement  
<strong>\<rehrar\></strong> evenlessmoney: if this attack does turn out to be practical though, would a solution be to have to continue to pay a fee to keep the block size above default?  
<strong>\<evenlessmoney\></strong> its not even an 'attack' so much as popularity  
<strong>\<suraeNoether\></strong> another option: change the timescale of blocksize adjustment so that going up in block size requires a lot of statsitical evidence and, lacking htat, we have a rapid exponential decay back to baseline, or something like that  
<strong>\<gingeropolous\></strong> ^^  
<strong>\<suraeNoether\></strong> rehrar: yeah, having a fee penalty proportional to the difference between the current block size and the "resting" size would do the trick  
<strong>\<rehrar\></strong> I think the biggest issue here is that one you pay the fee to bump the blocksize, as long as the block remains full, it's free to keep it at that blocksize, correct?  
<strong>\<ArticMine\></strong> In creasing the median to more that 100 block will make this attack way more expensive and if the new median is chosen carefully will have little impact overall  
<strong>\<evenlessmoney\></strong> there is no additional cost that I am aware of rehrar  
<strong>\<suraeNoether\></strong> rehrar: that summarizes the potential issue. i'm not sure if it's an issue. :P  
<strong>\<suraeNoether\></strong> after all, there's an argument: if they are paying fees, it ain't spam  
<strong>\<rehrar\></strong> so my suggestion of miners having to continuously pay a fee for any blocksize above default is I think beneficial from a incentivization perspective, because it makes sure that blocks absolutely need to be that large  
<strong>\<rehrar\></strong> or they start slipping back down  
<strong>\<gingeropolous\></strong> rehrar, but that kind of breaks the scaling  
<strong>\<spaced0ut\></strong> does anyone have some idea how how much money we're talking to perform this attack? are we looking to be safe vs nation states?  
<strong>\<gingeropolous\></strong> someone ran some python on this recently  
<strong>\<ArticMine\></strong> That is actually the case now since one does not get a rebate for mining below the effective median  
<strong>\<gingeropolous\></strong> Isthmus, where u at  
<strong>\<suraeNoether\></strong> i would like us to stop calling this an attack. It's not like a DOS attack or something like that.  
<strong>\<spaced0ut\></strong> well it actually could be a DOS if well funded enough and nodes can't sync right?  
<strong>\<ArticMine\></strong> I agree.  
<strong>\<suraeNoether\></strong> how could you distinguish it from healthy usage without a lot of real-life extra information?  
<strong>\<rehrar\></strong> this is the big issue, and where a lot of criticism of Bitcoin comes in  
<strong>\<ArticMine\></strong> A DDOS against node is actually a weakness of fixed blocksize coins such as Bitcoin  
<strong>\<rehrar\></strong> if Bitcoin tx goes up, some will say it's a spam attack, and some will say it's adoption  
<strong>\<rehrar\></strong> and we simply do not have an oracle able to differentiate  
<strong>\<suraeNoether\></strong> okay, let's do this  
<strong>\<rehrar\></strong> and even if there was a reliable one, it would probably not be a decentralized one  
<strong>\<ArticMine\></strong> There were spam attacks in Bitcoin to drive up fees. This works if hte block are full since most of the spam ts are not mined  
<strong>\<ArticMine\></strong> But they cost andwith to the nodes  
<strong>\<gingeropolous\></strong> to me it seems there is a small list of useful information needed to address the issue: 1) cost of attack, in XMR, to get to 3 GB / block in one day per Isthmus "\<Isthmus\> 00:44 By the end of the 1st day: 3 goddamn GB per block"  
<strong>\<ArticMine\></strong> bandwith  
<strong>\<suraeNoether\></strong> let's just do some back of the napkin calculations today and see what we see. then we can talk about it more. :P  
<strong>\<suraeNoether\></strong> why 3 GB/block?  
<strong>\<rehrar\></strong> yes, concrete numbers are needed  
<strong>\<ArticMine\></strong> Compare the cost to a 51% attack  
<strong>\<gingeropolous\></strong> 2) current node processing ability. What is the existing blocksize tipping point for processing  
<strong>\<sarang\></strong> Yes, without numbers or simulations (e.g. the work Isthmus and others have done) in this discussion, all this is speculation without data  
<strong>\<rehrar\></strong> we may not be "academics" like Zcash (according to Snowden)  
<strong>\<gingeropolous\></strong> suraeNoether, 3 GB / block because thats what Isthmus ran if you do the maximum possible expansion  
<strong>\<rehrar\></strong> but we can still pretend to math, at least  
<strong>\<suraeNoether\></strong> gingeropolous: wait do you mean "by the end of one day, block sizes could be 3Gb?"  
<strong>\<gingeropolous\></strong> i.e., if you max out the equation, you can get to 3 GB / block in 1 day  
<strong>\<suraeNoether\></strong> hmm  
<strong>\<suraeNoether\></strong> yeah, let's merely estimate how much that would literally cost someone  
<strong>\<sarang\></strong> I'd like to see this done on testnet  
<strong>\<suraeNoether\></strong> ooooh  
<strong>\<suraeNoether\></strong> yeah, why simulate it if you can just simulate it? :P  
<strong>\<sarang\></strong> we literally have a toy network available  
<strong>\<ArticMine\></strong> Sure and pay 4x the reward. Why not just do a 51% attack?  
<strong>\<sarang\></strong> that we can nuke  
<strong>\<gingeropolous\></strong> im just parroting Isthmus 's work  
<strong>\<moneromooo\></strong> Don't spam testnet.  
<strong>\<gingeropolous\></strong> <https://usercontent.irccloud-cdn.com/file/UHG4yi8G/image.png>  
<strong>\<sarang\></strong> make a new testnet, toynet  
<strong>\<gingeropolous\></strong> axis lbels be damned apaprently  
<strong>\<endogenic\></strong> spamnet  
<strong>\<suraeNoether\></strong> we need a testtestnet?  
<strong>\<spaced0ut\></strong> do it on wow  
<strong>\<endogenic\></strong> we shall have our own testnet\! with spam, and DOS attacks\!  
<strong>\<rehrar\></strong> ^  
<strong>\<evenlessmoney\></strong> ooh, yes  
<strong>\<evenlessmoney\></strong> wownero pls  
<strong>\<rehrar\></strong> let's finally make them useful for something  
<strong>\<evenlessmoney\></strong> they're good for memes..  
<strong>\<sarang\></strong> Anyway, this discussion hasn't really produced much IMO  
<strong>\<ArticMine\></strong> In any case the parameter I would look at if this is an issue is the median number of blocks.  
<strong>\<gingeropolous\></strong> ^^  
<strong>\<ArticMine\></strong> for an increase  
<strong>\<evenlessmoney\></strong> We can look into running some simulations  
<strong>\<evenlessmoney\></strong> anyone got a cache of testnero?  
<strong>\<evenlessmoney\></strong> needtestnero90  
<strong>\<gingeropolous\></strong> ugh, lets not make testnet a pain to use  
<strong>\<Isthmus\></strong> Hey, sorry for belated response. I'm on phone, at work, can't really hang in meeting, but just saw all the pings  
<strong>\<Isthmus\></strong> <https://github.com/noncesense-research-lab/Blockchain\_big\_bang/blob/master/Isthmus\_Bx\_big\_bang\_model.ipynb>  
<strong>\<Isthmus\></strong> Updated simulations are there  
<strong>\<evenlessmoney\></strong> I'll speak with isthmus (we can maybe get together), we can talk about simulations and stuff  
<strong>\<ArticMine\></strong> But keep in mind if a 51% attack is cheaper then what is the point of this attack?  
<strong>\<evenlessmoney\></strong> and report back next meeting or something  
<strong>\<suraeNoether\></strong> ArticMine: medians require 50% violation of data before the median shifts (breakdown point... <https://en.wikipedia.org/wiki/Robust\_statistics> )  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/EziXrd38/image.png>  
<strong>\<gingeropolous\></strong> a 51% attack costs energy, this attack costs units of account  
<strong>\<suraeNoether\></strong> ArticMine: i don't think it's cheaper  
<strong>\<moneromooo\></strong> smooth had a good suggestion, to have the penalty start before the median, so you'd get penalty free till, say, 90% of the median. This would cause a natural shrinking if the txpool is full of low fee txes.  
<strong>\<evenlessmoney\></strong> oh  
<strong>\<evenlessmoney\></strong> thats smart too  
<strong>\<evenlessmoney\></strong> I like that one, one of my big issues has been that its basically free (base tx cost) to keep block sizes up atm  
<strong>\<suraeNoether\></strong> isthmus, the axes of your graph are transparent on my computer and i can't read them. :P  
<strong>\<gingeropolous\></strong> hell, someone could find a flaw in monero, print a bajillion monero, and then bring the network to its knees for nothin  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/X1So57dJ/image.png>  
<strong>\<Isthmus\></strong> Sorry, is that legiblbe?  
<strong>\<evenlessmoney\></strong> ginger thats a threat if they get infinite monero no matter what our algo is  
<strong>\<Isthmus\></strong> 51% and bloat are two totally unrelated attacks that accomplish different things. It's an apples/oranges comparison  
<strong>\<suraeNoether\></strong> is graph over a day? Isthmus  
<strong>\<suraeNoether\></strong> yeah i can read it now  
<strong>\<Isthmus\></strong> Or maybe that was already discussed more earlier, I'm not caught up on scrollback and need to hop back to work  
<strong>\<ArticMine\></strong> ut unites of account translate into energy via the lock reward  
<strong>\<suraeNoether\></strong> ArticMine: the 51% attack requires hardware/POW. this bloat issue requires only cash, like a POS attack  
<strong>\<suraeNoether\></strong> you can attack the network without being a miner if you have the capital using this approach  
<strong>\<ArticMine\></strong> It is not like a POS attack because in this case hte cash is burned  
<strong>\<suraeNoether\></strong> true, but it is like a POS attack because all it requires is capital  
<strong>\<suraeNoether\></strong> not hardware  
<strong>\<spaced0ut\></strong> wow 200k eur for 10TB in 2 days  
<strong>\<Isthmus\></strong> Ok, I gotta bounce back to work. All of the info &amp; FAQ are in that notebook, although it's a very rough draft that I had written up for internal use.  
<strong>\<ArticMine\></strong> POS can use borrowed capital  
<strong>\<Isthmus\></strong> There are probably some small bugs, feel free to fix it. :- 0  
<strong>\<gingeropolous\></strong> thanks Isthmus  
<strong>\<suraeNoether\></strong> Isthmus: sorry to bother you, i just want to make sure i understand: does that mean 1 million euros can drive the monero blockchain to be more than 1 million gigs in size?  
<strong>\<suraeNoether\></strong> within a DAY?  
<strong>\<Isthmus\></strong> I think it might take 2 days to get to 10 TB  
<strong>\<Isthmus\></strong> But essentially.  
<strong>\<Isthmus\></strong> This is taking into account the exponential accumulation  
<strong>\<suraeNoether\></strong> wow. thanks  
<strong>\<ArticMine\></strong> You are maxing out the penalty?  
<strong>\<suraeNoether\></strong> okay, let me think about this more, but now I've shifted my opinion  
<strong>\<Isthmus\></strong> Yes, totally override the penalty to make block \~2\*(median of last 100) for every block. It's very petal to the metal, deliberately sized attack  
<strong>\<gingeropolous\></strong> yes, median 10k  
<strong>\<ArticMine\></strong> Then it is 4x the lock reward  
<strong>\<ArticMine\></strong> block  
<strong>\<suraeNoether\></strong> I think we should have a term in our fees that is proportional to a super-linear function of the difference between current block size and a "target" block size, say 1MB right now  
<strong>\<spaced0ut\></strong> what about raising the cost to increase again if the block size has recently increased in X amount of blocks?  
<strong>\<spaced0ut\></strong> drastically raising maybe  
<strong>\<ArticMine\></strong> Fees are driven by the penalty  
<strong>\<rehrar\></strong> spaced0ut: in the event of rapid adption (should it ever happen), this would cripple the network for quite some time  
<strong>\<ArticMine\></strong> So one needs to look at the penalty function.  
<strong>\<ArticMine\></strong> The simplest an lees disruptive is to increase the 100 block median  
<strong>\<ArticMine\></strong> less  
<strong>\<spaced0ut\></strong> well assuming this hasn't happened before we can probably get pretty good data (maybe even from btc also) on the upper bound of how rapid real adoption could be. just a thought  
<strong>\<spaced0ut\></strong> the size shouldnt need to double 10 times in a row  
<strong>\<evenlessmoney\></strong> we risk the BTC people moving here en masse  
<strong>\<evenlessmoney\></strong> or the ecosystem moving in  
<strong>\<gingeropolous\></strong> and i ultimately think increase the 100 block median won't affect UX drastically. It will actually drive a fee market. Current activity is very burst-like.  
<strong>\<gingeropolous\></strong> so delays will eventually clear  
<strong>\<gingeropolous\></strong> and those needing priority can get it  
<strong>\<gingeropolous\></strong> but if the network actually demonstrates a need for larger blocks, they come into existence  
<strong>\<gingeropolous\></strong> and we somehow work a long tail into the decay  
<strong>\<lurkinandlearnin\></strong> surely rapid adoption shouldn't be catered to above long term survivability against this type of attack  
<strong>\<ArticMine\></strong> The only downside to increasing the median I can see is that the network may not e able to adapt to seasonal changes such as December  
<strong>\<evenlessmoney\></strong> its not even an attack, if we get too popular and fees are too cheap for large blocks, we risk nodes becoming unsyncable  
<strong>\<evenlessmoney\></strong> the unbounded block size is concerning imo  
<strong>\<suraeNoether\></strong> increasing sample size for the median over 100 blocks will make such a drift attack slower (and therefore cost a lot more, because you have to do it over more and more blocks) but linearly slower. and is a rigid sort of decision, as ArticMine mentions re: December. Adding a nonlinear term to our fees seems sensible to me.  
<strong>\<evenlessmoney\></strong> forcing average users to sync against remote nodes due to bandwidth constraints is dangerous  
<strong>\<sarang\></strong> Yes evenlessmoney that's the whole point of Isthmus's posting  
<strong>\<spaced0ut\></strong> if anyone needs to be secure against nation states it's XMR  
<strong>\<gingeropolous\></strong> im interested to see what Isthmus 's multistate memory thing is  
<strong>\<rehrar\></strong> but...and I hate to say it like this, hasn't this already been kinda known for a while?  
<strong>\<ArticMine\></strong> Yes ut how do you enforce non linear fees?  
<strong>\<rehrar\></strong> Because we have a dynamic blocksize, we can scale with adoptin  
<strong>\<suraeNoether\></strong> multi-term memory sounds like moving averages of different spans of time to me  
<strong>\<moneromooo\></strong> "secure against nation states" is ridiculous. They could fuck with us anytime they wanted to already.  
<strong>\<ArticMine\></strong> That is the whole point  
<strong>\<rehrar\></strong> although taht would mean maybe going up to several GB block sizes.  
<strong>\<spaced0ut\></strong> moneromooo, fair enough but shouldn't that be the goal?  
<strong>\<suraeNoether\></strong> rehrar: yeah, but just like a lot of other monero problems, we are learning about the size/scale of the issue.  
<strong>\<suraeNoether\></strong> i agree with moneromooo :P  
<strong>\<sarang\></strong> rehrar: yes, this has been known for a while  
<strong>\<evenlessmoney\></strong> we didnt have hard numbers from isthmus until recently either  
<strong>\<evenlessmoney\></strong> its been a bit more nebulous  
<strong>\<ArticMine\></strong> A fixed block size has been proven to be a disaster for Bitcoin and as recent events have demonstrated for Bitcoin cash  
<strong>\<evenlessmoney\></strong> Time will tell whether Bitcoin's decision was a disaster. I think the jury is still out.  
<strong>\<gingeropolous\></strong> my thinking is, there is a hard cap. Its 2X the current blocksize. I really think we need a long perspective on the median. Like 6 months. however many blocks that is  
<strong>\<spaced0ut\></strong> +  
<strong>\<suraeNoether\></strong> gingeropolous what if we have a dynamic soft cap that is determined by a long time-scale measurement? :P  
<strong>\<gingeropolous\></strong> thats prolly the multistate thing :)  
<strong>\<ArticMine\></strong> My take is that increasing the median is the way to address this concern provided it is legitimate.  
<strong>\<ArticMine\></strong> By legitimate I mean a cost comparison with a 51% attack  
<strong>\<lurkinandlearnin\></strong> That sounds good to me. I would rather the network slow down in the rare december-like situation that someone being able to inflate the blockchain to unusable levels for less than the "cost" (however you quantify that because they are different) of a 51% attack  
<strong>\<spaced0ut\></strong> definitely  
<strong>\<ArticMine\></strong> Long medians with say a 6 month time frame will not lead to Bitcoin's problems  
<strong>\<moneromooo\></strong> A 51% attack is recoverable from. That one seems not.  
<strong>\<ArticMine\></strong> It depends on what the 51% attack does  
<strong>\<gingeropolous\></strong> i think the problem, like the 51%, is that the cost is dynamic and unpredictable. I.e., it cost less to 51% the monero network 3 years ago. We don't know what the hardware will be in 5 years, or the state of network. The protocol needs to be hardware agnostic as much as it can  
<strong>\<rehrar\></strong> with the volatility of Monero, this thing is unpredictable too  
<strong>\<rehrar\></strong> since it requiers unit of account, this "attack" can be done while Monero is dirt cheap, and the effects stick around  
<strong>\<rehrar\></strong> even if Monero goes way up and this isn't feasible anymore  
<strong>\<ArticMine\></strong> ^^ es it has to be hardware agnostic  
<strong>\<ArticMine\></strong> Yes  
<strong>\<suraeNoether\></strong> i'm in agreement with articmine for now. both: 1) we need to estimate costs for 51% vs. bloat and 2) a long-time-scale soft cap seems super smart, especially considering how bursty the network is in general  
<strong>\<lurkinandlearnin\></strong> Also because this resembles a PoS attack, you have to remember that it could be done for "free" if people/whales/exchanges are stolen/compromised  
<strong>\<sarang\></strong> Sounds like a long-scale median increase is an adjustment that, while probably suboptimal, is better understood  
<strong>\<suraeNoether\></strong> we can make it even softer by using that long-time-scale soft cap as the anchor point for a nonlinear penalty term  
<strong>\<gingeropolous\></strong> so we gonna use a magic number or see if we can get an emergent one  
<strong>\<rehrar\></strong> and even softer if we wrap the solution in fur  
<strong>\<ArticMine\></strong> There is a lot of room between 3.4 hours and 6 months to tune the median  
<strong>\<ArticMine\></strong> and make it optimmal  
<strong>\<suraeNoether\></strong> ArticMine: given the 50% breakdwon point of medians...  
<strong>\<suraeNoether\></strong> if we did 6 months, that implies that at least 3 months of \*all monero transactions\* would have to be bloat transactions  
<strong>\<suraeNoether\></strong> for someone to raise the soft cap over time  
<strong>\<sarang\></strong> Isthmus: would be nice to see the effects of a long-term median in your sims  
<strong>\<sarang\></strong> IMO that's the best approach to this analysis right now  
<strong>\<suraeNoether\></strong> moreover, if we don't actually cap anything but add a nonlinear penalty to block reward for block sizes above the "soft cap" chosen by a long-time-scale-median, temporary fluctuations in economic activity would be handled relatively easily  
<strong>\<suraeNoether\></strong> we'll seek out more information  
<strong>\<suraeNoether\></strong> and try to come up with a write-up  
<strong>\<suraeNoether\></strong> after isthmus and noncesense have had their way with some analyses  
<strong>\<rehrar\></strong> that's smart suraeNoether  
<strong>\<lurkinandlearnin\></strong> Maybe finding medians/"target values" and softcaps might be an actual legitimate application of some TA haha  
<strong>\<suraeNoether\></strong> lurkinandlearnin: other way around :D  
<strong>\<suraeNoether\></strong> there are no legitimate applications of TA, but there are legitimate applications of statistics \*for use in\* TA :P hehe  
<strong>\<ArticMine\></strong> A hybrid approach could be used to deal with seasonal issue. Essentially a stiff penalty over the long term median  
<strong>\<suraeNoether\></strong> shit, we can easily do a seasonal model, too  
<strong>\<suraeNoether\></strong> <https://machinelearningmastery.com/sarima-for-time-series-forecasting-in-python/>  
<strong>\<suraeNoether\></strong> we wouldn't be using this for forecasting  
<strong>\<endogenic\></strong> sarima noether  
<strong>\<ArticMine\></strong> That implies baking in an eternal event  
<strong>\<lurkinandlearnin\></strong> Yes that's what I mean. The whole point of the TA bullshit is to find patterns which would "look" reasonable given past results (and to claim this somehow predicts them). Whereas we want to put limits on what "looks reasonable" to apply incentives. Right?  
<strong>\<gingeropolous\></strong> ima throw it out there... i think we should target this for protocol change spring 2019 fork  
<strong>\<gingeropolous\></strong> if we have something fancy, great. If not, we just pick a larger median.  
<strong>\<suraeNoether\></strong> gingeropolous: i'm fine with that. i think the large sample size median is going ot have some rigidity problems with the network, i'll work with isthmus to write something up maybe  
<strong>\<sarang\></strong> Cool, I think that sums things up nicely for now, until we have data on this  
<strong>\<gingeropolous\></strong> a rigid network is more useful than a broken one :)  
<strong>\<sarang\></strong> In the interest of time, any other topics to discuss with the whole group?  
<strong>\<suraeNoether\></strong> gingeropolous: sure :D  
<strong>\<suraeNoether\></strong> okay, other than that  
<strong>\<suraeNoether\></strong> over thanksgiving: i read papers on accumulators and learned some more about STARKs  
<strong>\<suraeNoether\></strong> and sarang is still running some matching code for timing purposes  
<strong>\<suraeNoether\></strong> my matching paper is coming along :D  
<strong>\<suraeNoether\></strong> aaaand I don't have anythign else to talk about  
<strong>\<suraeNoether\></strong> sarang? anything else? does anyone else have interesting projects they want to chat about? even if its not formally for MRL or kovri or monero specifically  
<strong>\<sarang\></strong> Perhaps to sum up our meeting, does anyone have goals for the next network upgrade? This ties in with our earlier discussion  
<strong>\<suraeNoether\></strong> ^ good question\!  
<strong>\<endogenic\></strong> ring size increase?  
<strong>\<suraeNoether\></strong> hold on that until i have more information from matching. :P  
<strong>\<sarang\></strong> Seems like a change to handle bloat would be good, PoW tweak...  
<strong>\<hyc\></strong> everyone here following tevador's RandomX ?  
<strong>\<sarang\></strong> and any recommendations from the matching that are urgent  
<strong>\<lurkinandlearnin\></strong> IMO goals should be getting rid of the payment ID/integrated address/subaddress confusion and what was discussed today  
<strong>\<sarang\></strong> Nuking payment IDs is a longer-term issue IMO  
<strong>\<sarang\></strong> Setting a timeline is more reasonable  
<strong>\<gingeropolous\></strong> its just standing up to exchanges  
<strong>\<sarang\></strong> RIght  
<strong>\<endogenic\></strong> we should deprecate and kill long pids for sure  
<strong>\<gingeropolous\></strong> i think a timeline was proposed but never agreed on  
<strong>\<lurkinandlearnin\></strong> exchanges laziness shouldn't slow down the improvement of the network  
<strong>\<gingeropolous\></strong> ^^  
<strong>\<sarang\></strong> But if we don't set a timeline, we become Zcash with their "deprecate transparent addresses SOMEDAY"  
<strong>\<moneromooo\></strong> Whether or not to add IPv6 connectivity might be relevant. IPv4 scarcity is said to be a barrier to Sybils. How much though, I don't know.  
<strong>\<lurkinandlearnin\></strong> is it reasonable to have a goal of having only subaddresses by the next September upgrade?  
<strong>\<hyc\></strong> as an enforced consensus rule?  
<strong>\<sarang\></strong> I don't have enough knowledge of exchange timelines to say  
<strong>\<sarang\></strong> hyc: yes  
<strong>\<gingeropolous\></strong> imo, deprecating pids isn;t an MRL thing  
<strong>\<sarang\></strong> We've already said "please don't use them"  
<strong>\<pigeons\></strong> the client could just make choices about how to diversify its connections if IPv6 is used  
<strong>\<sarang\></strong> gingeropolous: yeah, only bringing it up because I asked about upgrade goals :D  
<strong>\<moneromooo\></strong> Only works for outgoing connections.  
<strong>\<suraeNoether\></strong> i feel like you are correct gingeropolous but I want to shy away from the "not my problem" effect  
<strong>\<hyc\></strong> doesn't adopting i2p expose us to the same Sybil possibilities?  
<strong>\<moneromooo\></strong> I don't know enough to say.  
<strong>\<suraeNoether\></strong> okay, so it seems like we have hit all our major points  
<strong>\<hyc\></strong> very long addresses, and you have no way to know where they originate from  
<strong>\<hyc\></strong> worse than IPv6 in that regard  
<strong>\<suraeNoether\></strong> and we can continue chatting about ipv4 and ipv6 and medians for the rest of the day  
<strong>\<suraeNoether\></strong> but i think that's sufficient for our meeting today :D  
<strong>\<sarang\></strong> Great, so action items are to get Isthmus and friends to examine median changes, and be thinking about upgrade  
<strong>\<moneromooo\></strong> Oh. One other thing that's related:  
<strong>\<sarang\></strong> sure  
<strong>\<moneromooo\></strong> If the blockchain is split in N stripes, such that every peer selects a random stripe (that is, 4096 blocks every N\*4096). What is the optimal value of N (too small means you save less storage, too large means it gets harder to find the data you need to sync).  
<strong>\<evenlessmoney\></strong> Do we use Bitcoin's default peer limit of 8?  
<strong>\<evenlessmoney\></strong> If so, that should be factored in to n  
<strong>\<moneromooo\></strong> 8 outgoing peers, unlimited incoming IIRC.  
<strong>\<sarang\></strong> The optimal value depends on our metric, I suppose  
<strong>\<moneromooo\></strong> OK. That was a bad question. A better question was "what is the best metric".  
<strong>\<suraeNoether\></strong> hmm  
<strong>\<hyc\></strong> I think it's just a question of, how much space do you need to save  
<strong>\<suraeNoether\></strong> moneromooo: i feel like N \< 3 risks byzantine consensus problems  
<strong>\<gingeropolous\></strong> well, the goal is to save space, but the problem is that is a dynamic question for each user  
<strong>\<sarang\></strong> If we assume good connectivity and number of peers, the number could be decently high  
<strong>\<hyc\></strong> yes, and dynamic for the overall chain too since it continues to grow  
<strong>\<gingeropolous\></strong> someone thats not gonna run software that takes up 80 gigs probably still won't run it if it takes up 40  
<strong>\<moneromooo\></strong> suraeNoether: I do not understand.  
<strong>\<hyc\></strong> In my blocktree ramblings I was envisioning 256-way branching  
<strong>\<suraeNoether\></strong> moneromooo: i'm imagining each miner as being a member of one of N coalitions of possibly dishonest participants  
<strong>\<moneromooo\></strong> Ah, one thing I neglected to mention: the pruned data is just range proofs and smaller bits. Not the whole chain.  
<strong>\<suraeNoether\></strong> if everyone in control of one strip is totally dishonest, that information is no longer really accessible  
<strong>\<suraeNoether\></strong> hmm  
<strong>\<suraeNoether\></strong> this is a nontrivial problem  
<strong>\<sarang\></strong> Yeah moneromooo brings up the question of "is old enough prunable data \_safe\_ to remove"  
<strong>\<sarang\></strong> which is related  
<strong>\<suraeNoether\></strong> moneromooo: I don't think we can pick a number without some knowledge of the underlying network topology  
<strong>\<gingeropolous\></strong> this type of thing is ... unprecedented, right? Therefore, it might be the kind of thing that requires measurement. Once implemented, will nodes advertise which portions of the chain they keep?  
<strong>\<gingeropolous\></strong> and therefore, the network could be crawled to obtain a census of adoption of this approach?  
<strong>\<moneromooo\></strong> Yes, nodes adertise. And don't have to stripe if they want to keep all.  
<strong>\<gingeropolous\></strong> right.  
<strong>\<hyc\></strong> ... I would deterministically automate it. e.g., MAC address of first network interface &amp; MASK = stripe \#  
<strong>\<gingeropolous\></strong> so, the thing we may want to measure is how many nodes join the network with N.  
<strong>\<hyc\></strong> or some other already-visible node ID.  
<strong>\<gingeropolous\></strong> so, say we start with N of 8, we could measure the increase nodecount that are using 8. Or maybe start with 4.  
<strong>\<gingeropolous\></strong> because thats the goal, right? increase number of nodes?  
<strong>\<hyc\></strong> back to moneromoo's clarification - this isn't striping the entire blockchain. just the prunable stuff, range proofs.  
<strong>\<hyc\></strong> so aside from someone bootstrapping a new node, this has no real impact on data availability  
<strong>\<hyc\></strong> wallets talking to nodes that they trust won't see any change at all  
<strong>\<suraeNoether\></strong> i have a question for moneromooo : if we pick N = 8 and six months later want to change it to N = 11 or something weird, how much of a PITA is that? it means that miners need to pull a different stripe, that means a lot of data can be deleted and some new data needs to be downloaded...  
<strong>\<suraeNoether\></strong> i guess my question is: what's the cost of picking a \*bad\* N for implementation?  
<strong>\<hyc\></strong> there are consistent hashing algorithms to minimize that problem  
<strong>\<moneromooo\></strong> It'd be kinda of a pita. Changing to 16 would be less so, as it's kinda made to allow this (would need some extra code though).  
<strong>\<hyc\></strong> minimize the amount of reshuffling needed when N changes  
<strong>\<suraeNoether\></strong> moneromooo: that's why i picked 11 :P coprime. heh  
<strong>\<moneromooo\></strong> Also, picking 11 means divisions all the time.  
<strong>\<suraeNoether\></strong> let's tell wownero to pick 24, and we pick 6, and we figure out the difference :P  
<strong>\<hyc\></strong> stick to powers of 2  
<strong>\<suraeNoether\></strong> (bad approach)  
<strong>\<suraeNoether\></strong> hyc: or at least prime powers of some sort. makes changing it easier  
<strong>\<moneromooo\></strong> BTW, if anyone wants to try a sync from scratch using the crash branch (which simulates this) is welcome ^\_^  
<strong>\<suraeNoether\></strong> carbon crab incoming. :P  
<strong>\<suraeNoether\></strong> cesium crab  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<sarang\></strong> OK, I think we can officially call the meeting
