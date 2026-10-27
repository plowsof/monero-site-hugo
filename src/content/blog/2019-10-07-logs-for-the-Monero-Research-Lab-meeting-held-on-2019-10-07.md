---
title: Logs for the Monero Research Lab Meeting Held on 2019-10-07
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<suraeNoether\></strong> howdy\!  
<strong>\<ArticMine\></strong> hi  
<strong>\<sarang\></strong> I suppose we can jump into ROUNDTABLE discussion  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<suraeNoether\></strong> sure; I've been working on my matching code. I fixed a few bad unit tests, i fixed a problem that was making the code take O(n^2) time and now it takes O(n) time... the challenger code and the parameter space explorer code are nearing completion, and my simulations are still misbehaving  
<strong>\<sarang\></strong> Any ideas what exactly is misbehaving?  
<strong>\<suraeNoether\></strong> i'm also beginning to read about an idea by randomrun and thinkinga bout security proofs for it  
<strong>\<suraeNoether\></strong> well, no, that's what's strange. i have unit tests that check things like "check that the correct number of nodes are added to the graph", and they all pass those things... but then the integrated simulation as a whole produces a bad output file  
<strong>\<suraeNoether\></strong> which is why i posted the stupid gif the other day of "two unit tests, no integration test"  
<strong>\<sarang\></strong> I see  
<strong>\<suraeNoether\></strong> but i'm working on it, and i have a few clues... and six more unit tests i'm coding up this afternoon  
<strong>\<sarang\></strong> excellent  
<strong>\<suraeNoether\></strong> i also want to bring up the topics that isthmus posted on github  
<strong>\<sarang\></strong> Let's save those until he returns  
<strong>\<suraeNoether\></strong> but we should hold off till the end of the meeting to chat about those  
<strong>\<suraeNoether\></strong> \*nod\* he may not return, though, and we should chat about it in public today eventually either way  
<strong>\<sarang\></strong> I've worked on a few things this past week  
<strong>\<sarang\></strong> I collaborated with Aram on a Lelantus update: <https://lelantus.io/enabling-untraceable-anonymous-payments.pdf>  
<strong>\<sarang\></strong> It seems to solve the sender tracing issue, but at the cost of proper one-time addressing  
<strong>\<suraeNoether\></strong> hmm \*taps chin\*  
<strong>\<sarang\></strong> Trying to fix both at the same time keeps running into a wall involving Pedersen generators  
<strong>\<suraeNoether\></strong> i'm very interested to spend some time catching up on that trade-off  
<strong>\<sarang\></strong> So we're looking at possible ways to use Schnorr representation proof tricks here... nothing so far though  
<strong>\<sarang\></strong> Aside from that, I updated the RCT3 proof-of-concept code and spacetime analysis to reflect the new version of the preprint that was released  
<strong>\<sarang\></strong> They compress the spend proof across inputs, but this incurs some major cost in padding inputs  
<strong>\<sarang\></strong> Unfortunately, undoing that compression doesn't play nicely with their integrated balance proof  
<strong>\<sarang\></strong> As in, (number of spends)\*(size of anonymity set) must be a power of 2, or padded to one  
<strong>\<suraeNoether\></strong> iirc lelantus originally used a tree structure, yeah? is that why?  
<strong>\<sarang\></strong> Is what why?  
<strong>\<suraeNoether\></strong> is that why they require padding inputs to powers of two?  
<strong>\<sarang\></strong> RCT3, not Lelantus  
<strong>\<sarang\></strong> It has to do with the inner-product argument that it uses for compression  
<strong>\<suraeNoether\></strong> gack, got them confused\~ nevermind, i retract my question  
<strong>\<suraeNoether\></strong> ah, that makes sense too  
<strong>\<sarang\></strong> It would be nice to get separate spend proofs if only to avoid this padding issue  
<strong>\<sarang\></strong> but that would require redoing security proofs etc.  
<strong>\<sarang\></strong> Finally, I've been working more on some ideas RandomRun had for Triptych involving balance proofs and multiple spends  
<strong>\<sarang\></strong> I have a simple version of the Groth proving system that supports proving knowledge of multiple commitment openings to zero, along with linking  
<strong>\<sarang\></strong> but haven't done any security proofs (in particular, I have some questions about the uniqueness requirements on certain proof elements)  
<strong>\<sarang\></strong> Getting balance integrated is tricky, and that's what I'm working on now  
<strong>\<suraeNoether\></strong> is there any write-up anywhere you and/or RR are willing to share with the public, or is this still too much "in prep"?  
<strong>\<sarang\></strong> His ideas are listed in the GitHub issue here: <https://github.com/monero-project/research-lab/issues/56>  
<strong>\<sarang\></strong> and the work-in-progress code is here, but very unfinished: <https://github.com/SarangNoether/skunkworks/tree/lrs/lrs>  
<strong>\<suraeNoether\></strong> gotcha  
<strong>\<sarang\></strong> and very probably insecure as written  
<strong>\<sarang\></strong> Right now it's just at the playing-around-with-the-algebra stage, to see what's useful/possible  
<strong>\<suraeNoether\></strong> it's good to clarify that before some other coin goes and implements it :P  
<strong>\<sarang\></strong> Anyway, kudos to RandomRun on some really clever ideas to extend that Groth proving system  
<strong>\<sarang\></strong> TBH it's probably worth a short paper on its own  
<strong>\<sarang\></strong> Right now (if proven secure, mind you) it turns Groth's idea for a ring signature into a linkable ring signature  
<strong>\<sarang\></strong> If the balance proof extension works, then we're really cooking  
<strong>\<sarang\></strong> Efficiency TBD  
<strong>\<sarang\></strong> While we wait for Isthmus to return, I can wrap up by saying my ACTION ITEMS for the week are trying to get balances working in Triptych, finishing a presentation on transaction protocols, and getting caught up on some lit review  
<strong>\<suraeNoether\></strong> good timing bruh  
<strong>\<sarang\></strong> Isthmus: we didn't talk about your items at all  
<strong>\<sarang\></strong> Care to go over them now?  
<strong>\<Isthmus\></strong> Sure  
<strong>\<Isthmus\></strong> One of the things I've been pondering about is how to assess the appropriate (safe) lock time  
<strong>\<Isthmus\></strong> Here is one possible framework for the conversation: <https://github.com/noncesense-research-lab/lock\_time\_framework/blob/master/writeup/lock\_time\_framework.pdf>  
<strong>\<Isthmus\></strong> Since the lock time only needs to be longer than reorg events, we can approach the question systematically by enumerating the list of things that cause alternative blocks, assessing the maximum plausible length of alternative chains that they could produce, and buffer that with a safety term  
<strong>\<sarang\></strong> Enumerating the expected sources of reorganizations is a good idea, now that you have some empirical data on latency-based reorgs  
<strong>\<Isthmus\></strong> My goal is to take the conversation out of the realm of intuition, towards addressing specific things that we can model/discuss/etc. :- )  
<strong>\<sarang\></strong> I seem to recall some talk a long while ago about individual nodes that had observed much longer reorgs, but I assume these were not global?  
<strong>\<sarang\></strong> (for some definition of global)  
<strong>\<Isthmus\></strong> Well, that was back when there were ASICs on the network  
<strong>\<suraeNoether\></strong> i'm inclined toward T2 or T3. the selection of an enforced lock time to ban inarguably-too-short txn times is easy and has an immediate benefit to the system. analysis paralysis while selecting an "optimal" lock time isn't desirable, and having the enforced lock time in place - even if we don't change the current lock time - is critically important  
<strong>\<Isthmus\></strong> Yeah, (should we enforce lock time?) and (how long should lock time be?) are two distinct questions  
<strong>\<suraeNoether\></strong> so, here's the deal  
<strong>\<sarang\></strong> There seemed to be good support for consensus enforcement of whatever value is chosen  
<strong>\<sgp\_\></strong> Is it worth exploring privacy implications as well? It could be that the longer the lock time, the better it is for network privacy to some extent  
<strong>\<suraeNoether\></strong> sgp\_: this is especially true if the lock time is longer than the median spend-time  
<strong>\<suraeNoether\></strong> but that's not a desirable lock time  
<strong>\<suraeNoether\></strong> for obvious reasons  
<strong>\<suraeNoether\></strong> so, the deal i'm thinking is that it's easy to discern what is \*unacceptably long\* or short in lock times  
<strong>\<suraeNoether\></strong> a lock time of two blocks is too short, a lock time of 90 days is too long, for sure  
<strong>\<sgp\_\></strong> I don't think it needs to be the main topic (chain re-orgs are more important imo), but it's worth considering  
<strong>\<sgp\_\></strong> I think we will have a tough time reducing it from 10 honestly for UX reasons  
<strong>\<suraeNoether\></strong> i guess my question is  
<strong>\<suraeNoether\></strong> does anyone have an argument in favor of using a value \*other than 10\*  
<strong>\<sgp\_\></strong> \*tough time increasing it  
<strong>\<sgp\_\></strong> suraeNoether: I would like to justify a smaller number for UX reasons if possible  
<strong>\<suraeNoether\></strong> i wouldn't dare lower it further than 10  
<strong>\<sgp\_\></strong> Isthmus's document outlines a basic framework for coming up with a number  
<strong>\<sgp\_\></strong> suraeNoether: based on what though?  
<strong>\<suraeNoether\></strong> or let me rephrase that, because "i wouldn't dare" is a bit dramatic  
<strong>\<suraeNoether\></strong> sgp\_: well, we've witnessed many re-orgs length longer than 10. they are downright \*common\*  
<strong>\<suraeNoether\></strong> moreover, spend-times that are lower than 20 minutes are \*extremely\* noticable in a txn graph  
<strong>\<suraeNoether\></strong> if a sequence of very fast chained txns occur in a row, you can almost bet your ass that they're the same person churning.  
<strong>\<ArticMine\></strong> The question in my mind is what is an acceptable risk probability for T2, and T3  
<strong>\<suraeNoether\></strong> ArticMine: that was the question that popped into my mind  
<strong>\<sgp\_\></strong> that's what I was referring to from the privacy angle  
<strong>\<suraeNoether\></strong> \*nod\*  
<strong>\<sarang\></strong> Do you happen to know the corresponding threshold for Bitcoin's choice of typical lock time?  
<strong>\<sarang\></strong> I don't, off the top of my head  
<strong>\<suraeNoether\></strong> ^ sgp\_ or ArticMine or isthmus?  
<strong>\<sgp\_\></strong> nope  
<strong>\<suraeNoether\></strong> hm  
<strong>\<Isthmus\></strong> I'm avoiding commenting on any particular numbers until we decide on a framework for discussing  
<strong>\<suraeNoether\></strong> personally i would find it helpful to have those numbers in deciding the framework  
<strong>\<sarang\></strong> Here's a writeup that I'd seen before: <https://bitcoil.co.il/Doublespend.pdf>  
<strong>\<dEBRUYNE\></strong> sarang: Bitcoin has no lock time for normal transactions  
<strong>\<dEBRUYNE\></strong> You can essentially chain unconfirmed transactions  
<strong>\<suraeNoether\></strong> dEBRUYNE: thanks that's important to know, too. :P  
<strong>\<sarang\></strong> Page 8 shows some example data based on hashrate and confirmations using Bitcoin as an example  
<strong>\<Isthmus\></strong> Chicken/egg, don't need numbers for the framework  
<strong>\<sgp\_\></strong> I see your point Isthmus  
<strong>\<Isthmus\></strong> Does buffering the lock time to be greater than the worst case plausible scenario make sense as a framework?  
<strong>\<sarang\></strong> dEBRUYNE: but most clients use the 6-confirmation rule for "confirmed" transactions  
<strong>\<suraeNoether\></strong> Isthmus: if we did this, our lock time would have to be \>\> 23  
<strong>\<sarang\></strong> I was curious about that particular choice's assumptions  
<strong>\<suraeNoether\></strong> iirc we saw a 23-block reorg recently  
<strong>\<dEBRUYNE\></strong> It is a soft rule essentially  
<strong>\<dEBRUYNE\></strong> You can easily overrule it  
<strong>\<sgp\_\></strong> Let's consider a 3 standard deviation scenario  
<strong>\<sarang\></strong> dEBRUYNE: right, but I'm simply curious to make a comparison  
<strong>\<Isthmus\></strong> Lock\_time = Safety\*(max(len\_latency, len\_51%, len\_selfish...))  
<strong>\<Isthmus\></strong> So if you're saying that would be 23  
<strong>\<Isthmus\></strong> You're saying lock  
<strong>\<Isthmus\></strong> lock\_time = 23  
<strong>\<Isthmus\></strong> What are you using as your value for the Safety term?  
<strong>\<Isthmus\></strong> And which term in the max are you looking at?  
<strong>\<suraeNoether\></strong> ah, good questions  
<strong>\<Isthmus\></strong> I never suggested any value for the safety term, so I'm trying to figure out how we got to 23 :- P  
<strong>\<suraeNoether\></strong> no no  
<strong>\<suraeNoether\></strong> that's not the 23  
<strong>\<suraeNoether\></strong> i'm saying max(...) \> 23, because we've seen 23 within the last year  
<strong>\<Isthmus\></strong> Woah, I totally missed that  
<strong>\<Isthmus\></strong> When?  
<strong>\<suraeNoether\></strong> so whatever number we select needs to be \> safety\*23  
<strong>\<Isthmus\></strong> We can fish it out of the NRL logs  
<strong>\<sarang\></strong> That was from a single node report, no?  
<strong>\<suraeNoether\></strong> sarang: \*shrug\* even if it was 15, or 12, safety\*12 for any safety \> 1 is going to be bigger than 20, generally  
<strong>\<sgp\_\></strong> That's why I think looking at all reogs and using 3sd longer than normal or something like that is a more practical number  
<strong>\<suraeNoether\></strong> my point is: if we look at how common re-orgs are, and if we want to protect against those, we need unreasonably long lock times that risk slowing down the monero economy  
<strong>\<sarang\></strong> sgp\_: all observed reorgs, regardless of assumed origin (latency, high-hashpower entity, etc.)?  
<strong>\<sgp\_\></strong> sarang: I would need to go deeper into the numbers, but I just want to see what the numbers are without some of the outliers  
<strong>\<Isthmus\></strong> I've been out of the loop, so I'm not disagreeing. But wowza, I hadn't seen anything \*global\* greater than length 2 since we switched to CryptoNoteR  
<strong>\<suraeNoether\></strong> sgp\_: \*nod\* we should look at the distribution of re-org times, though, and decide on a rigorous statistic instead of picking 3\*stdev, but your point is 100% correct  
<strong>\<sgp\_\></strong> that's the overall point I want to convey  
<strong>\<ArticMine\></strong> I suggest a risk based approach. Starting with who bears the risk?  
<strong>\<sgp\_\></strong> eg: if there was 1 reog at 20 and every other one is \<3, that's important to know  
<strong>\<sarang\></strong> I think using data and methods from the Bitcoin community for risk estimates of high-hashpower entities would be useful as one data point  
<strong>\<sgp\_\></strong> Isthmus: in terms of the framework however, I think we need to add some privacy implications  
<strong>\<Isthmus\></strong> True, though the Gini coefficient for BTC hashrate is probably much more lopsided that Monero's distribution  
<strong>\<sgp\_\></strong> shrinking the lock time likely has adverse privacy implications  
<strong>\<sgp\_\></strong> and it also have positive UX implications  
<strong>\<ArticMine\></strong> There are some significant differences in Bitcoin: 1) Great Firewall of China 2) 10 min blocks  
<strong>\<Inge-\></strong> Better UX at the cost of privacy sounds like ... not-Monero.  
<strong>\<Isthmus\></strong> I suspect (and I may totally backtrack this later...) that the fact we flip coins every 2 minutes rather than every 10 minutes may mean we reach stable equilibrium faster  
<strong>\<sgp\_\></strong> Inge-: it's about the tradeoff. No one would use a coin with a lock time of 100 days  
<strong>\<Isthmus\></strong> SLOWNERO  
<strong>\<Isthmus\></strong> YESSSS  
<strong>\<suraeNoether\></strong> ^ nah, it's like using a smooth/exponential curve for a mortgage versus discretized timesteps using monthly annualization formulas: one approximates the other, but you converge at the same rate  
<strong>\<suraeNoether\></strong> wrt 2 minus vs 10  
<strong>\<suraeNoether\></strong> okay, let's operate briefly assuming that the longest reasonable "natural" re-org is 6 blocks. it's smaller than our current lock time, longer htan isthmus' global data, and matches satoshi's arbitrary selection.  
<strong>\<suraeNoether\></strong> if we pick safety = 2 or 3, we are still looking at 12 or 18 lock time, not shorter than 10.  
<strong>\<suraeNoether\></strong> now, if we recall, block re-orgs don't always happen naturally and can take place due to adversarial behavior, using the longest one in history is incomplete  
<strong>\<suraeNoether\></strong> why? the attacker may hold off, biding their time on a real attack, until their attack power is most likely to lead to success. Seeing only a few re-orgs of length 2-6 in the entire history of monero doesn't mean that an adversary can't force a 30-length re-org, as an example, so while the monero archival stuff that isthmus has been running is helpful  
<strong>\<suraeNoether\></strong> i dunno, i feel like this is an unnecessary rabbit hole  
<strong>\<sgp\_\></strong> "past performance does not indicate future results." But I still like seeing how the network performs under normal scenarios  
<strong>\<suraeNoether\></strong> or at least: why try to select a number other than 10 before the next hard fork?  
<strong>\<suraeNoether\></strong> sgp\_: well... \*historical\* scenarios anyway  
<strong>\<ArticMine\></strong> So do we just stay with 10?  
<strong>\<sgp\_\></strong> let's agree on the framework first :)  
<strong>\<sgp\_\></strong> if we don't agree on anything, the status quo will remain (10)  
<strong>\<Isthmus\></strong> Oh totally NOT trying to adjust this by the next fork  
<strong>\<Isthmus\></strong> This is going to take us like 3 months to discuss  
<strong>\<suraeNoether\></strong> oh, then if that's the case  
<strong>\<Isthmus\></strong> I was just responding to the ping from last meeting  
<strong>\<Isthmus\></strong> I think enforce at 10 for this upcoming upgrade  
<strong>\<Isthmus\></strong> Ahhahaha  
<strong>\<Isthmus\></strong> Re @suraeNoether "this is an unnecessary rabbit hole", As MRL, if we are going to inform lock time, we HAVE to go down three rabbit holes. 1) What's the longest plausible natural reorg, 2) What's the longest plausible attack, 3) what margin of error do we want?  
<strong>\<Isthmus\></strong> I literally don't think there's a way to address the question if we're not willing to consider these  
<strong>\<Isthmus\></strong> (I think... there may be some clever way to circumvent this...)  
<strong>\<suraeNoether\></strong> i'm saying there is not a way to address this problem  
<strong>\<Isthmus\></strong> What do you think about additive safety term versus multiplicative?  
<strong>\<sgp\_\></strong> suraeNoether: I agree on a theory level, but not on a practical level  
<strong>\<suraeNoether\></strong> sgp\_: yeah, i'm saying theoretically, there is no optimal solution. in practice, there will be a whole host of solutions that are "good enough" that have different tradeoffs between them depending on threat models  
<strong>\<sgp\_\></strong> ....have you worked on Monero before? lol  
<strong>\<suraeNoether\></strong> this is why isthmus is using the word plausible here  
<strong>\<suraeNoether\></strong> ...  
<strong>\<sgp\_\></strong> yeah it's a tradeoff, but we need to pick one, and there's potential reason to believe (with evidence) that a number other than 10 is best  
<strong>\<suraeNoether\></strong> \*cough\* there is no best solution  
<strong>\<sgp\_\></strong> I'm open to changing the number with the right evidence  
<strong>\<Isthmus\></strong> Maybe we can circle back to this next week with more recent numbers from the archival network regarding global events  
<strong>\<ArticMine\></strong> Is it not possible to take a risk based approach for a framework?  
<strong>\<Isthmus\></strong> @ArticMine yes, please share ideas :- )  
<strong>\<ArticMine\></strong> 1) % hashrate of attacker  
<strong>\<ArticMine\></strong> 2) Who bears the impact  
<strong>\<ArticMine\></strong> 3) Type of impact ie double spend, privacy  
<strong>\<ArticMine\></strong> One should be able to derive risk provabilities  
<strong>\<Isthmus\></strong> Some of \#1 may be captured in Eq 3. Or at least I tried.  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/iRNSWEPW/image.png>  
<strong>\<sarang\></strong> Again, that Bitcoin-related paper does this type of hashrate-threshold analysis  
<strong>\<ArticMine\></strong> Yes this is the type of analysis I mean  
<strong>\<suraeNoether\></strong> 1) lock times \> 50 or \< 10 are extremely bad ideas for opposing reasons.  
<strong>\<suraeNoether\></strong> 2) This leaves a narrow band of a half of a single order of magnitude. not a lot of wiggle room.  
<strong>\<suraeNoether\></strong> 3) going from 10 to 15 is extremely unlikely to have a dramatic or concrete impact on privacy; this is a 10 minute difference when we are speaking of distributions with medians around a day and a half  
<strong>\<suraeNoether\></strong> 4) Going from 10 to 40 is going to have huge impacts on our economy, and would have to be justified by a veritable mountain of evidence  
<strong>\<suraeNoether\></strong> i look at this as willfully entering into analysis paralysis just because we have the data to answer questions about some very specific hypotheses  
<strong>\<sarang\></strong> In the interest of time, may we table this and return when folks have had a chance to review the relevant analysis?  
<strong>\<sgp\_\></strong> yes please  
<strong>\<sarang\></strong> Isthmus had one other item to discuss  
<strong>\<Isthmus\></strong> So, I might not have 100% of the technical details right, so feel free to jump in with corrections:  
<strong>\<sarang\></strong> It was the question of tx pubkey representation, since its use is different between primary and subaddresses  
<strong>\<Isthmus\></strong> Yes, that.  
<strong>\<Isthmus\></strong> The ability for an external observer to ascertain whether there were any subaddresses included in the construction of a transaction  
<strong>\<Isthmus\></strong> Leaks information about the recipient  
<strong>\<moneromooo\></strong> Or sender.  
<strong>\<sarang\></strong> For some reason I thought that unique pubkeys were always used now, regardless of address type, to reduce distinguishability... but I need to check this  
<strong>\<Isthmus\></strong> Yes, and/or sender  
<strong>\<dEBRUYNE\></strong> sarang: Sure, that is fair, but in that instance I would set it to zero  
<strong>\<sgp\_\></strong> This is the first I am hearing of this  
<strong>\<moneromooo\></strong> Actually... I'm not sure. The logic is a bit different for change IIRC...  
<strong>\<suraeNoether\></strong> i'm a bit confused...  
<strong>\<moneromooo\></strong> I hit that when I tried to add custom change addresses.  
<strong>\<suraeNoether\></strong> isthmus do you have a small toy example you could show us?  
<strong>\<Isthmus\></strong> Nope, I have no clue how the constructions differ  
<strong>\<sarang\></strong> suraeNoether: for subaddress destinations, you use a unique tx pubkey  
<strong>\<Isthmus\></strong> Well wait  
<strong>\<Isthmus\></strong> Maybe I can fish up an example  
<strong>\<Isthmus\></strong> Does tx\_extra = (empty) imply no subaddresses were involved?  
<strong>\<Isthmus\></strong> In that case I can just hit a block explorer  
<strong>\<sarang\></strong> tx\_extra stores tx pubkey, which is always included  
<strong>\<suraeNoether\></strong> sarang: do you mean the tx pubkey is encoded differently?  
<strong>\<suraeNoether\></strong> oh oh  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> aha  
<strong>\<Isthmus\></strong> Mmmmm  
<strong>\<sarang\></strong> It's derived differently for primary and subaddresses  
<strong>\<sarang\></strong> It's possible to use only one pubkey for multiple non-subaddress destinations  
<strong>\<sarang\></strong> but this implies distinguishability  
<strong>\<Isthmus\></strong> ^^^^  
<strong>\<suraeNoether\></strong> hmm  
<strong>\<sarang\></strong> I thought this had been changed to be unique per destination all the time, for this reason  
<strong>\<suraeNoether\></strong> sarang i am beginning to recall this conversation and using a unique key per destination, and we didn't like that it revaled the number of dest addresses, or something...  
<strong>\<sarang\></strong> Unique per output, is what I should have said  
<strong>\<sgp\_\></strong> why would the \# of dest addresses be different than the number f outputs, unless someone is doing terrible churn?  
<strong>\<suraeNoether\></strong> \*shrug\* users do dumb stuff all the time for dumb reasons  
<strong>\<sarang\></strong> I will confer with moneromooo and examine code to see what the current default behavior is  
<strong>\<Isthmus\></strong> +1  
<strong>\<moneromooo\></strong> I purposefully shut up after what I said above since stoffu will know for sure, and I don't.  
<strong>\<Isthmus\></strong> Cool, I think we can probably stick a pin in this, research over the week, and circle back with more concrete details about distinguishability under the current design.  
<strong>\<ArticMine\></strong> +1  
<strong>\<sarang\></strong> OK, any other action items before we adjourn?  
<strong>\<sarang\></strong> Righto, thanks to everyone for participating
