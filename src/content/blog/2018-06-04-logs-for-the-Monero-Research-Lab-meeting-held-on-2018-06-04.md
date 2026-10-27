---
title: Logs for the Monero Research Lab Meeting Held on 2018-06-04
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<sarang\></strong> I can stay <del>15 min today  
<strong>\<sarang\></strong> poor cat  
<strong>\<unknownids\></strong> :)  
<strong>\<sarang\></strong> Coco hates car rides, needles, and strange places. This’ll go great  
<strong>\<philkode\></strong> Hey guys  
<strong>\<sarang\></strong> yo  
<strong>\<suraeNoether\></strong> so we’ll go with 1. greetings, 2. give sarang a brief platform to talk with us about what he’ll be up to before he has to dip out, 3. i’ll give the community an update on the unforgeability of LSTAGs, 3. we’ll bring up churning and best practices infographics, 4. any other projects anyone wants to talk about  
<strong>\<philkode\></strong> Will be keeping one eye on the Apple WWDC keynote and one eye here  
<strong>\<suraeNoether\></strong> philkode: i’ll post transcript after the meeting so no worries there  
<strong>\<suraeNoether\></strong> so, howdy everyone  
<strong>\<sarang\></strong> heyo  
<strong>\<suraeNoether\></strong> sarang, take it away</del>  
<strong>\<sarang\></strong> As has been discussed elsewhere, BP reviews are humming along  
<strong>\<sarang\></strong> moneromooo and I worked up the last big optimization we had hoped to get done for them  
<strong>\<sarang\></strong> increasing verification speed  
<strong>\<sarang\></strong> While I’m away I’ll continue managing the review process as needed  
<strong>\<sarang\></strong> Everything is coming up Milhouse for the next upgrade  
<strong>\<suraeNoether\></strong> what’s our “overall” verification speed improvement looking like, and do your changes only apply to the BP code for now?  
<strong>\<suraeNoether\></strong> i recall around 50% improvement in total? or am i misremembering?  
<strong>\<sarang\></strong> We’re looking at up to \>90% size benefits and \>85% speed benefits for transactions  
<strong>\<sarang\></strong> depending on batching, size, etc.  
<strong>\<suraeNoether\></strong> freaking fantastic  
<strong>\<suraeNoether\></strong> you win the internet  
<strong>\<sarang\></strong> We’ll get some “official” stats for public-facing publicity stuff  
<strong>\<sarang\></strong> And yes, this only applies to BPs for now  
<strong>\<sarang\></strong> but in theory any multiexp operation (besides aX+bY simple terms) could probably benefit from this  
<strong>\<sarang\></strong> But BPs are the big use case right now  
<strong>\<suraeNoether\></strong> this makes me want us to write our own 25519 library with pippinger and blackjack  
<strong>\<sarang\></strong> nopenopenope  
<strong>\<suraeNoether\></strong> i know, never roll your own crypto  
<strong>\<suraeNoether\></strong> it may be worth incentivizing the creation of test suites, though  
<strong>\<sarang\></strong> This was a case of good algorithm deployment, nothing more  
<strong>\<suraeNoether\></strong> not libraries themselves, but test suites for libraries  
<strong>\<sarang\></strong> but one that was on the back burner for a while  
<strong>\<suraeNoether\></strong> but that’s another discussion  
<strong>\<sarang\></strong> Anyway, that’s my Big News for today  
<strong>\<suraeNoether\></strong> gratzo  
<strong>\<sarang\></strong> Tests are available on mooo’s branch  
<strong>\<suraeNoether\></strong> anyone have any questions for sarang?  
<strong>\<sarang\></strong> for anyone wanting to play with them  
<strong>\<sarang\></strong> <https://github.com/moneromooo-monero/bitmonero/tree/bp-multi-aggregation-pippenger>  
<strong>\<sarang\></strong> thanks to mooo for fast coding of my shit Python prototypes  
<strong>\<sarang\></strong> =p  
<strong>\<suraeNoether\></strong> mooo is actually seven dudes in singapore  
<strong>\<sarang\></strong> I often agree with this hypothesis  
<strong>\<suraeNoether\></strong> okay, if no one has any questions, i’ll bring up a discovery i’ve made  
<strong>\<iDunk\></strong> That would explain memory lapses.  
<strong>\<suraeNoether\></strong> in terms of LSTAGs and unforgeability  
<strong>\<philkode\></strong> Those are amazing size and speed up figures, really well done guys  
<strong>\<sarang\></strong> ty philkode  
<strong>\<suraeNoether\></strong> yes, sarang and moneromooo are MVPs of the … year so far  
<strong>\<suraeNoether\></strong> so, unforgeability: the Musig paper uses a double fork to accomplish their proof of unforgeability. while working through a ring-signature version of the same approach, i realized something  
<strong>\<sarang\></strong> suraeNoether: wasn’t it three forks?  
<strong>\<sarang\></strong> or was that changed with the fixes  
<strong>\<suraeNoether\></strong> it was 2 before and after the changes, whereas i initially thought we would need 3 for the ring signatures  
<strong>\<sarang\></strong> oh ok, must be thinking of something else, nvm  
<strong>\<suraeNoether\></strong> but, i was not just trying to do a ring signature version of the proof, but also a recursive-aggregation version, where keys have trees of family members, and as long as everyone is participating, they can cooperate to construct a signature simultaneously, in a big recursive signing party  
<strong>\<suraeNoether\></strong> now, one fact about unforgeability proofs is that they often use rewinding-on-success or forking to prove their unforgeability, and every time you do this, the security bound gets looser and looser  
<strong>\<suraeNoether\></strong> what i realized is that forking ring signatures the way i’ve been trying to do it, with trees of family histories of keys… the bound gets so freaking loose that you lose non-negligibility \*if the size of the family histories is a security parameter\*  
<strong>\<suraeNoether\></strong> in other words: the forking approach to proving unforgeability, afaik one of the only real ways to prove equivalence wiht the DL hardness problem, \*seems to not be sufficient to allow an attacker to get the DL\*  
<strong>\<suraeNoether\></strong> this \*suggests\* that violating the unforgeability of ring signatures is much harder than regular signatures  
<strong>\<suraeNoether\></strong> it’s not a proof on the relation between hardness, but it means that classic proof techniques \*may fail\* to prove unforgeability for arbitrary recursive key aggregation  
<strong>\<suraeNoether\></strong> so, in other words: we have to fork once for each use of the honest key in the family history, which could be a big tree of re-uses of the same key, and in this case, the attacker can’t present a forgery…  
<strong>\<suraeNoether\></strong> so, long story short: i’m looking into merely restricting things to the non-recursive case, proving it secure in that case and remarking on the crappiness of the bound (instead of forking twice as in musig, we have to fork 2+ringSize times in this case, so you have a really really loose security bound, but you still hav ea non-negligible advantage  
<strong>\<suraeNoether\></strong> and that’s what i’ve been working on  
<strong>\<suraeNoether\></strong> I wanted to be explicit about this particular fact, because it may end up being useful later: rewind/forking lemmas applied recursively cause adversaries to lose non-negligible advantages very quickly  
<strong>\<suraeNoether\></strong> any questions in that regard before we start talking about churning and infographics and microsoft and github?  
<strong>\<UkoeHB\></strong> jw about your eta for the paper  
<strong>\<sgp\_\[m\]\></strong> That all went way over my head, but hopefully I can understand your work with churning\!  
<strong>\<UkoeHB\></strong> Sounds like you have some interesting stuff to work with  
<strong>\<suraeNoether\></strong> UkoeHB: if i restrict the scope of this thing appropriately, i’ll be posting a version of it later today that is a sketch of my intentions and then a more correct version of it later this week. I don’t want this thing to take more time than the remainder of June.  
<strong>\<UkoeHB\></strong> Cool :)  
<strong>\<suraeNoether\></strong> and i’ve really pared this thing down, it’s a lot smaller and more clear at this point  
<strong>\<suraeNoether\></strong> now churn  
<strong>\<suraeNoether\></strong> the biggest concern is that you receive some money from or send some money to an adversary (or first one then the other). if someone is “watching you,” so to speak, then even if your transactions appear to look like background noise to the average observer and match the statistical pattern of the monero economy (somehow), the “watcher” can still sort of tell you are churning. they can look at an AML/KYC  
<strong>\<suraeNoether\></strong> exchange’s records with a warrant, for example, and see that an abnormal \*number\* of your transactions reference one of their poison outputs, even if the depths and distribution of those references appear to look like background noise  
<strong>\<suraeNoether\></strong> to avoid this, even innocent parties have to reference these poison outputs \*quite often\*  
<strong>\<suraeNoether\></strong> one solution is that \*everyone always does a lot of churning.\*  
<strong>\<suraeNoether\></strong> not just people who care about securtiy  
<strong>\<suraeNoether\></strong> sort of like ring size minimums  
<strong>\<suraeNoether\></strong> i don’t know how one could enforce that, thoguh  
<strong>\<sgp\_\></strong> I think the only way would be a large minimum (likely impractical) ringsize, yeah  
<strong>\<sgp\_\></strong> Difficult to force people to send transactions  
<strong>\<suraeNoether\></strong> not just a minimum ring size that is large, but some sort of structure that requires “you can send this to (A,B), but only if you send it through (X,Y) and (W,Z) first”  
<strong>\<suraeNoether\></strong> but if we do that  
<strong>\<suraeNoether\></strong> we’re talking about a massive blockchain blowup  
<strong>\<sgp\_\></strong> hmm  
<strong>\<sgp\_\></strong> The input selection algorithm can’t help with this?  
<strong>\<erciccione\_\[m\]\></strong> maybe a timed pop-up on the GUI-CLI saying: churning help your privacy, do you want to churn now? every week or so (i don’t know how stupid this can sound)  
<strong>\<suraeNoether\></strong> input selection could be tweaked so that inputs are chosen with a probability that is inversely proportional to the number of references that have been made (so that no output goes long without being referenced a few times)  
<strong>\<sgp\_\></strong> I think that’s more reasonable  
<strong>\<suraeNoether\></strong> erciccione\_\[m\]: we have to weigh the benefits of security against the increased weight of our blockchain in the long term, if we are going to go down that route  
<strong>\<suraeNoether\></strong> so, i’m going to write up a proposal on input selection algorithms  
<strong>\<sgp\_\></strong> Do you have an idea how many times you want each output referenced? Obviously the more the better all else being equal  
<strong>\<suraeNoether\></strong> simply the more the better  
<strong>\<UkoeHB\></strong> Outputs can’t be referenced more than ringsize number of times on average  
<strong>\<erciccione\_\[m\]\></strong> shouldn’t the ringsize become larger anyway after BP get implemented?  
<strong>\<sgp\_\></strong> It sounds like you’re hoping for a ringsize increase too then  
<strong>\<suraeNoether\></strong> UkoeHB: \*can’t\* be, or under mild assumptions, will asymptotically tend toward the ring size?  
<strong>\<sgp\_\></strong> Well, the average number of references depends on the average number of inputs and outputs in transactions  
<strong>\<sgp\_\></strong> There are likely more outputs than inputs on average, meaning that the references should be less than the ringsize over a long term  
<strong>\<suraeNoether\></strong> each output can be referenced at most R\*number of transactions ahead of it in the blockchain. so the total number of references would be R\*N + R\*N-1 + … + R\*2 + R, so the maximum average would be R\*(N-1)/2 references (although the true average would be much smaller in general)  
<strong>\<UkoeHB\></strong> How could the average output be referenced more or less than ringsize, if total number of references is ringsize\*numouts?  
<strong>\<sgp\_\></strong> Of course there could be periods of mass consolidation where it could be the opposite  
<strong>\<suraeNoether\></strong> anyway, this is all a bit accessory to the point, which is that the probability that an output is selected should be jointly proportional to (1) 1/\# of references that already exist and (2) the gamma distribution from bitcoin’s age data (although combining data from litecoin would be helpful)  
<strong>\<suraeNoether\></strong> and probably only from the non-blackballed list  
<strong>\<m2049r\[m\]\></strong> dynamic ringsize is not an option based on which inputs are actually used?  
<strong>\<UkoeHB\></strong> It makes sense. Reduce reference spread  
<strong>\<suraeNoether\></strong> m2049r\[m\]: eh, I usually think about ring size only in terms of the minimum, because people really shouldn’t be advertising their behavior by selecting out-of-the-ordinary ring sizes  
<strong>\<sgp\_\></strong> those two sound good suraeNoether  
<strong>\<suraeNoether\></strong> the question earlier about larger ring sizes  
<strong>\<sgp\_\></strong> and hope that people do the third  
<strong>\<UkoeHB\></strong> Could you poison outputs? Simply reference one a bunch of times so it becomes extremely improbable. Then, when you spend it, it’s probably real  
<strong>\<dEBRUYNE\></strong> because people really shouldn’t be advertising their behavior by selecting out-of-the-ordinary ring sizes \<= A good argument to enforce static ring sizes after the next HF  
<strong>\<suraeNoether\></strong> UkoeHB: yes, you could, actually\! nuts. that’s the consequence of using things like temporal heuristics and selection frequency to try to mask erratic human behavior :(  
<strong>\<dEBRUYNE\> \<UkoeHB\></strong> Could you poison outputs? Simply reference one a bunch of times so it becomes extremely improbable. Then, when you spend it, it’s probably real \<= You could still reference it after spending it?  
<strong>\<UkoeHB\></strong> dEBRUYNE: if selection probability is 1/(prev references), someone can reference an output many times  
<strong>\<UkoeHB\></strong> reduces likelihood future references ARENT real  
<strong>\<suraeNoether\></strong> dEBRUYNE: NSA wants to know if an output has been spent. So they manufacture 1000 ring signatures referencing it. almost no one except the true spender will include it in any future ring signatures because it is 1000 times less likely to be selected at random. so after the nsa do this experiment, the first time the output in question appears on the blockchain is very likely a true spend  
<strong>\<sgp\_\></strong> “I send money to you, knowing which output I give you. Then I make 100 transactions with this output as a decoy, meaning the only likely other transaction that will include it is the real one”  
<strong>\<suraeNoether\></strong> it’s real bad  
<strong>\<suraeNoether\></strong> it’s a \*real bad idea.\*  
<strong>\<UkoeHB\></strong> maybe we just triple ring size after BP  
<strong>\<dEBRUYNE\></strong> sgp\_: But an observer doesn’t know when it is used as decoy and when it is actually spent  
<strong>\<suraeNoether\></strong> it reverses the “guess newest” rule from monerolink and turns it into a “guess the last possible spender”  
<strong>\<sgp\_\></strong> dEBRUYNE right, but if the input selection algorithm is tweaked to prefer lesser-used outputs, then it may not be used outside of the actual transaction  
<strong>\<suraeNoether\></strong> dEBRUYNE: no, but an observer can be pretty sure that the output has been spent. besides, if 1000 transactions referencing an output P occur in a single block, and then a week later a single transaction with P occurs, that is strong circumstantial evidence that this attack occurred and the single lonely P from later in the week is likely the true spender  
<strong>\<needmoney90\></strong> Why not choose probabalistically between different selection algos  
<strong>\<UkoeHB\></strong> Or define a ‘ring sig ambiguity tree’ factor, analyze as function of ring size, and select a new ring size w/ justification. Instead of arbitrarily increasing  
<strong>\<needmoney90\></strong> One which prioritizes unused outputs, one which chooses uniformly  
<strong>\<hyc\></strong> why wouldn’t attacker spread txs across many blocks?  
<strong>\<needmoney90\></strong> For example  
<strong>\<dEBRUYNE\></strong> suraeNoether: Why wouldn’t he spend it in one of those 1000 transactions and reference it as decoy a week later?  
<strong>\<sgp\_\></strong> Some may be stronger than others. A uniform one falls under the shortfall where the newest is typically the real one, and this phenomemon will get worse over time  
<strong>\<dEBRUYNE\></strong> You have to account for the alternative scenario here as well  
<strong>\<suraeNoether\></strong> hyc \*shrug\* they may be impatient, or they may want to expose the true spender to the whole community maliciously instead of keeping the information to themselves. there are other attack models  
<strong>\<UkoeHB\></strong> I mean, new ring size that synergizes with a churn strat  
<strong>\<needmoney90\></strong> Sgp\_ the point was to have multiple selection strategies, where one is randomly chosen, and some of them have a chance to use a ring member previously used 100x  
<strong>\<suraeNoether\></strong> dEBRUYNE: the point is merely that this could be exploited to make it easier for an attacker to tell if a given output they don’t control has been spent. that’s all. the specific threat models aren’t as important as the observation that it can be exploited \*somehow.\*  
<strong>\<suraeNoether\></strong> in other words: since output reference frequency can be adversarially controlled, we can’t use it as part of our input selection method  
<strong>\<needmoney90\></strong> So someone using a ring member you poisoned by including it in a ring a lot doesn’t mean they’re the real spender  
<strong>\<needmoney90\></strong> They could have just used a selection algo that chose it  
<strong>\<sgp\_\></strong> I still think it is good to adapt the selection algorithm with this criteria in mind, perhaps only to a small extent though. Maybe a 10-20% preference  
<strong>\<suraeNoether\></strong> it does if all wallet software selects outputs \*in inverse proportion\* to frequency of spending  
<strong>\<suraeNoether\></strong> which is what we are talking about needmoney90  
<strong>\<needmoney90\></strong> Yes surae, I’m saying we can add multiple selection algos, where one of them doesn’t choose with inverse proportion  
<strong>\<needmoney90\></strong> Even if a given tx only has a 10% chance of using it  
<strong>\<UkoeHB\></strong> sgp\_: even in that case, it gives block chain analysts more power to reduce effective ring sizes  
<strong>\<needmoney90\></strong> It adds plausible deniability  
<strong>\<suraeNoether\></strong> needmoney90: yes, okay, but to give you an idea of the challenges we face here, let’s reduce it to a simple case where we have two algorithms, A1 and A2  
<strong>\<suraeNoether\></strong> and we pick one with probability p and the other with probabiltiy 1-p  
<strong>\<UkoeHB\></strong> Any programmatic deviation from natural distribution can be analyzed  
<strong>\<sgp\_\></strong> Yeah, but only by \~1 or 2 UkoeHB. May be less than the reduced risk of some outputs being referenced few times  
<strong>\<needmoney90\></strong> It will be apparent which was used  
<strong>\<needmoney90\></strong> For sure  
<strong>\<needmoney90\></strong> Hm  
<strong>\<suraeNoether\></strong> now an attacker who has success with algorihtm A1 just needs to make the attack 1/p times  
<strong>\<suraeNoether\></strong> instead of only once  
<strong>\<suraeNoether\></strong> so, this brings us back towards plausible deniability, which is good  
<strong>\<suraeNoether\></strong> but it still isn’t protection against the attack  
<strong>\<needmoney90\></strong> We can continue in lounge after the meeting, sorry to derail  
<strong>\<suraeNoether\></strong> if you have many algorithms, this increases the sample size the attacker needs to attack any one of them  
<strong>\<UkoeHB\></strong> sgp\_: it might ok if we increase ring size dramatically  
<strong>\<suraeNoether\></strong> which is that plausible deniability, which is good, but still gamable  
<strong>\<suraeNoether\></strong> UkoeHB: any deviation from “natural” is identifiable, you are right, and the problem is we have small anonymity subsets chosen from a (still unfortunately rather small) anonymity superset  
<strong>\<suraeNoether\></strong> there merely isn’t a good statistical mask for behavior here, the fix has to be to replace ring sizes  
<strong>\<ArticMine\></strong> You mean increase ring size  
<strong>\<UkoeHB\></strong> Any good prospects for escaping ring sigs?  
<strong>\<suraeNoether\></strong> erg… replace ring signatures\*  
<strong>\<ArticMine\></strong> with …  
<strong>\<sgp\_\></strong> Is there anything else that works without trust?  
<strong>\<suraeNoether\></strong> whatever comes next :)  
<strong>\<suraeNoether\></strong> there are untrusted stark set-ups that are slow  
<strong>\<suraeNoether\></strong> or use weird pairings  
<strong>\<suraeNoether\></strong> i’m looking into options  
<strong>\<suraeNoether\></strong> but the fact of the matter is, small anon sets will need to go for this problem to really be solved  
<strong>\<suraeNoether\></strong> in the meantime, churning isn’t going to help you if all the transactions you deposit on your AML/KYC exchange originated somehow from a malicious watcher like the DEA or NSA or something  
<strong>\<suraeNoether\></strong> and churning more than 3-4 times is probably overkill if all you are worried about is helping flesh out our anonymity sets  
<strong>\<gingeropolous\></strong> so … what should we put on getmonero.org regarding churning… ? :)  
<strong>\<suraeNoether\></strong> gingeropolous: give us a few days to write up a formal thing  
<strong>\<gingeropolous\></strong> cool  
<strong>\<suraeNoether\></strong> gingeropolous: because i want some specific numbers on how much you are really exposing yourself  
<strong>\<sgp\_\></strong> Can you give us a hint on the relationship between churning and ringsize? How significant is it?  
<strong>\<UkoeHB\></strong> exponential?  
<strong>\<suraeNoether\></strong> well, the naively computed anonymity set of a monero transaction tree of depth H with ring size R is approxiamtely O(R^H)  
<strong>\<suraeNoether\></strong> so  
<strong>\<suraeNoether\></strong> the question is “how many times are you going to pull a poison jelly bean out of this jar with R^H jelly beans in it, only one of which is poison?”  
<strong>\<suraeNoether\></strong> oh, “while grabbing R jelly beans at a handful?”  
<strong>\<suraeNoether\></strong> and these answers require some statistics involving the hypergeometric distribution, or binomial approximations…  
<strong>\<UkoeHB\></strong> I’m having flashbacks  
<strong>\<suraeNoether\></strong> hahah  
<strong>\<suraeNoether\></strong> let me summarize: churning 80 times wiht ring size 10 gives you more possibilities than the number of fundamental particles in teh universe  
<strong>\<UkoeHB\></strong> Ok we are at end of meeting so I’ll jump in  
<strong>\<suraeNoether\></strong> churning 7 or 8 times with ring size 10 gives you more possibilities than the monero blockchain  
<strong>\<suraeNoether\></strong> but a lot of these are collisions  
<strong>\<UkoeHB\></strong> Final draft: open for edits and feedback. Plan to publish in 2 weeks  
<strong>\<UkoeHB\></strong> <https://www.pdf-archive.com/2018/06/04/zero-to-monero-first-edition-v0-20/zero-to-monero-first-edition-v0-20.pdf>  
<strong>\<suraeNoether\></strong> by “collisions” i mean ‘the true anonymity set is much smaller.’  
<strong>\<UkoeHB\></strong> sarang will be happy to see pg 50 (57 of pdf)  
<strong>\<suraeNoether\></strong> if everyone on the network churned 2-3 times, we’d all be better off. anyone who lives in a sensitive land of security nightmares should churn maybe 8 times, but definitely shouldn’t be using AML/KYC exchanges, and if they do, the vast majority of their deposits at those exchanges should \*not\* be sensitive.  
<strong>\<sgp\_\></strong> makes sense suraeNoether, given the selection algorithm  
<strong>\<suraeNoether\></strong> UkoeHB: good job, i’ll try to read it before the end of the week  
<strong>\<UkoeHB\></strong> awesome thanks :)  
<strong>\<suraeNoether\></strong> i wanted to ask if folks were worried about github and microsoft and alternatives we may want to look into, but i think that can wait till later  
<strong>\<suraeNoether\></strong> anyone have any last questions before we finish up?  
<strong>\<needmoney90\></strong> Any official status updates on atomic swaps?  
<strong>\<suraeNoether\></strong> needmoney90: dual output ring signatures for refund transactions should enable atomic swaps, but there are some security concerns involved with those that will make it easier to determine spent outputs  
<strong>\<suraeNoether\></strong> so, there has been progress made, sarang wrote a technical note on the dual output sigs… but we are examining “what it means” for us to have two outputs with a differentiating/trigger block height.  
<strong>\<suraeNoether\></strong> it is too easy to see if one or the other has been spent based on block height, and introduces some temporal stuff: if a transaction happens right after a trigger block height for a ring member, that ring member is likely to be the true spender in a refund  
<strong>\<ArticMine\></strong> UkoeHB Great job. I was looking at the block size scaling part  
<strong>\<suraeNoether\></strong> if the block height is encrypted, there are different problems that show up  
<strong>\<ArticMine\></strong> This is on my reading list for this week  
<strong>\<suraeNoether\></strong> oooh, i like reading lists  
<strong>\<suraeNoether\></strong> okay, any other questions?  
<strong>\<UkoeHB\></strong> oops mistake in range proof verification. 63 is for A+B  
<strong>\<suraeNoether\></strong> okay, \</meeting\> :D
