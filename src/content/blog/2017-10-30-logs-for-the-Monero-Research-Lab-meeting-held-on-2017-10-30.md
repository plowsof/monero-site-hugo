---
title: Logs for the Monero Research Lab Meeting Held on 2017-10-30
summary: Multisig, hash-based accumulators, blockchain protocols, quantum-hard shuffle PRNG, educational outreach, and miscellaneous
tags: [dev diaries, crypto, research]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<sarang\></strong> Let’s go  
<strong>\<suraeNoether\></strong> Welcome everyone, to our second official (third unofficial) research meeting. fluffypony dEBRUYNE luigi1111 knaccc  
<strong>\<suraeNoether\></strong> uhm… ArcticMine… uhm… who else should we ping? moneromooo  
<strong>\<luigi1111w\></strong> official counts toward unofficial?  
<strong>\<suraeNoether\></strong> endogenic  
<strong>\<suraeNoether\></strong> is an official meeting also unofficial? is it a subset relation? anyway  
<strong>\<suraeNoether\></strong> kenshi84 too  
<strong>\<suraeNoether\></strong> ok so, I don’t really have an agenda. I want me and sarang to share with the group what we’ve been doing these past few weeks, and if anyone else has been doing any interesting research, let’s talk about it  
<strong>\<suraeNoether\></strong> sarang, you wanna go first?  
<strong>\<sarang\></strong> Sure  
<strong>\<sarang\></strong> I’ve been working a lot of readings mainly on some interesting new stuff  
<strong>\<sarang\></strong> Hash-based accumulators are becoming a thing  
<strong>\<sarang\></strong> where you can use interesting pairing relations to prove membership or nonmembership in a set  
<strong>\<sarang\></strong> the nifty part is that the manager of the set is untrusted  
<strong>\<suraeNoether\></strong> you’ve mentioned those several times. are all hash-based accumulators based on pairings crypto?  
<strong>\<suraeNoether\></strong> or are you using pairing differently  
<strong>\<sarang\></strong> Oh, I mean the structure involves pairs of elements as opposed to single elements  
<strong>\<suraeNoether\></strong> ah, ok  
<strong>\<sarang\></strong> This is a newer structure that gives nice efficiencies  
<strong>\<suraeNoether\></strong> so can we use a hash-based accumulator without a trusted set-up to do something <em>akin</em> to ring signatures?  
<strong>\<sarang\></strong> That’s my interest  
<strong>\<sarang\></strong> The security models would have to be analyzed in that new context  
<strong>\<silur\></strong> sarang does the order of these pairs have any effect on the security?  
<strong>\<sarang\></strong> None  
<strong>\<silur\></strong> okay  
<strong>\<sarang\></strong> What it does  
<strong>\<sarang\></strong> is give you a fast way of demonstrating membership or nonmembership  
<strong>\<sarang\></strong> by using the pairings akin to an ordering  
<strong>\<hyc\></strong> … reminds me of bloom filters, fast set membership  
<strong>\<suraeNoether\></strong> hyc i’m sorry i forgot to ping you  
<strong>\<hyc\></strong> no prob  
<strong>\<sarang\></strong> I’ve also been continuing investigations into aggregate signatures, something surae brought to my attention a while back  
<strong>\<sarang\></strong> the idea being that you can compress a set of signatures down to a single one  
<strong>\<suraeNoether\></strong> hyc bloom filters do fast set non-membership, not fast set membership, but both are based on hashes  
<strong>\<sarang\></strong> Verification is still linear  
<strong>\<sarang\></strong> but space is constant  
<strong>\<sarang\></strong> There is of course a downside, which is that it requires a bilinear map between groups with particular properties  
<strong>\<sarang\></strong> It’s apparently still an open question whether it’s possible to construct an aggregate that doesn’t require full linear verification  
<strong>\<suraeNoether\></strong> i didn’t realize agg sigs used pairings  
<strong>\<sarang\></strong> The ones I’ve seen use bilinear maps to allow for third-party verification  
<strong>\<sarang\></strong> It’s a clever and fairly simple setup  
<strong>\<suraeNoether\></strong> i found a few new sorts of signatures we maybe could look into, i have a list  
<strong>\<sarang\></strong> What gets into the weeds is the way the security models account for it all  
<strong>\<sarang\></strong> And there are some caveats dealing with repeated messages  
<strong>\<sarang\></strong> Of course, subaddys went out already  
<strong>\<sarang\></strong> SPECTRE is something that’s on the radar for surae and I  
<strong>\<suraeNoether\></strong> andytoshi linked his slides about atomic swaps and at least one type of sig i’m not totally familiar with was mentioned, and I forget what it’s called. Aggregator signatures? or something like that.  
<strong>\<sarang\></strong> And I’m still working on new work on proofs of proof-of-work  
<strong>\<sarang\></strong> that, if implemented ideally, could offer significant savings in blockchain space/analysis  
<strong>\<sarang\></strong> Logarithmically  
<strong>\<suraeNoether\></strong> the past several weeks, i’ve been putting several hours a day into multisig… current version I will link tomorrow. I have had to modify the scheme to take into account multiple outputs, which isn’t a huge deal, but changed notation throughout the paper pretty significantly, so  
<strong>\<sarang\></strong> It’s an ever-moving target  
<strong>\<suraeNoether\></strong> i will link the current version tomorrow after i give it yet another read-through  
<strong>\<suraeNoether\></strong> yeah, ring multisignatures are delicate  
<strong>\<suraeNoether\></strong> but i’ve also been looking into spectre, as sarang mentioned  
<strong>\<suraeNoether\></strong> i have a current working implementation on my github… but it takes quadratic time N^2 to organize N blocks  
<strong>\<suraeNoether\></strong> which is not scalable  
<strong>\<sarang\></strong> You wanna mention that email?  
<strong>\<suraeNoether\></strong> i contacted Sompolinsky, one of the authors  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<suraeNoether\></strong> I asked about the constant-time implementation they claim, and he got back to me  
<strong>\<suraeNoether\></strong> my intuition about how to make this constant time was correct… the algorithm can determine the order of leaves without any input from parents, grandparents, or grand\*parents of those leaves  
<strong>\<suraeNoether\></strong> so working from the leaves backwards, and only organizing a constant number of blocks is sufficient to get computation time down to constant  
<strong>\<sarang\></strong> But at a yet-to-be-analyzed cost  
<strong>\<suraeNoether\></strong> which is sort of a cheat  
<strong>\<suraeNoether\></strong> yes  
<strong>\<suraeNoether\></strong> there is an attack where someone purposely chooses a block deep into the blockDAG  
<strong>\<suraeNoether\></strong> this forces each node on the network to organize deeply into the blockDAG, which best case is a quadratic experience. pretty nasty.  
<strong>\<suraeNoether\></strong> my first thought was our traditional split between full nodes and lightweight nodes  
<strong>\<sarang\></strong> So it struck me as basically a DoS?  
<strong>\<suraeNoether\></strong> uhm… kinda. it’s DoS in the sense that ostensibly <em>honest</em> blocks can be used in the attack  
<strong>\<suraeNoether\></strong> and it’s not really an attack in a security sense, it’s an attack that forces miners to blow CPU power  
<strong>\<sarang\></strong> Right  
<strong>\<sarang\></strong> That’s what I mean  
<strong>\<suraeNoether\></strong> so my first thought was full nodes that organize the top 2% of the blockDAG all the time, and lightweight nodes that only go back a certain \# of generations from the leaves and avoid blocks too close to the genesis block  
<strong>\<suraeNoether\></strong> both sorts of nodes can do their thing in constant time. the full nodes will have larger constants, the lightweights will have smaller constants  
<strong>\<sarang\></strong> So this reminded me of the discussion from a while back about ignoring blocks that are old enough  
<strong>\<sarang\></strong> and the pros and cons of doing so…  
<strong>\<suraeNoether\></strong> well we already reject blocks if their timestamps are outliers  
<strong>\<sarang\></strong> So you think maybe the attack is irrelevant due to the time constraint?  
<strong>\<suraeNoether\></strong> the timestamp isn’t really the problem, it’s where the block is placed in the tree. and we can’t really reject blocks that are too deep into the blockDAG, because I don’t see a good way for two different miners to agree what “too deep” means  
<strong>\<suraeNoether\></strong> i think doing a full/light sort of split as above will avoid the attack for the most part, but it will tweak incentives  
<strong>\<suraeNoether\></strong> but it’s … tricky  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<suraeNoether\></strong> that’s what i’ve been doing  
<strong>\<suraeNoether\></strong> oh, on multisig, I mentioned this earlier this week, but i’m getting quite confident we’ll be done with it pretty soon. code review is moving forward bit by bit (heh)  
<strong>\<suraeNoether\></strong> is anyone else working on any interesting projects? i know that we’ve had discussions in here recently about PRNG and such, and I’m curious about what people are working on  
<strong>\<sarang\></strong> Oooh yes, PRNG  
<strong>\<sarang\></strong> I have no further updates, since I’m not sure if the devs took any definitive action it  
<strong>\<sarang\></strong> There was also an observation about the use of keccak vs. SHA-3  
<strong>\<silur\></strong> I’m working on a quantum-hard shuffle that can be used to construct PRNG-s  
<strong>\<suraeNoether\></strong> silur: freaking awesome. by “working on” do you mean… writing a paper? working on code?  
<strong>\<silur\></strong> writing a paper  
<strong>\<suraeNoether\></strong> and what makes a shuffle “hard”? trying to un-shuffle?  
<strong>\<sarang\></strong> Determining the end state w/o going through all steps?  
<strong>\<silur\></strong> trying to reveal the previous state of the elements of the set  
<strong>\<silur\></strong> or “peeking under the cards”  
<strong>\<sarang\></strong> Nice, so it’s a one-way function  
<strong>\<suraeNoether\></strong> yup  
<strong>\<suraeNoether\></strong> very cool  
<strong>\<suraeNoether\></strong> are you a student, a professor, a hobbyist, silur?  
<strong>\<suraeNoether\></strong> i still haven’t read that shuffle paper you sent me :(  
<strong>\<silur\></strong> I’ll be a prof from next september on crypto  
<strong>\<sarang\></strong> Congrats\!  
<strong>\<suraeNoether\></strong> congratulations\!  
<strong>\<silur\></strong> I’m at the edge of leaving ethereum foundation currently  
<strong>\<silur\></strong> thanks :)  
<strong>\<sarang\></strong> Any other interesting projects?  
<strong>\<sarang\></strong> Or suggestions on directions to go?  
<strong>\<unknownids\></strong> congrats\!  
<strong>\<suraeNoether\></strong> i’m also reading up on succinct posets, which are … a new datastructure. btw for anyone curious, every DAG induces a poset and every poset is a DAG  
<strong>\<suraeNoether\></strong> data structure\*  
<strong>\<sarang\></strong> Yeah, that poset paper looks quite interesting  
<strong>\<suraeNoether\></strong> they are significantly more compact than representing a DAG using upper triangular matrices, and they allow for constant time to determine whether one item precedes another  
<strong>\<sarang\></strong> I find the tradeoffs between storage and time to be always fascinating  
<strong>\<suraeNoether\></strong> so using those instead of the data structures i was coidng is going to lead to about a 75% reduction in computation time (but that’s still quadratic…)  
<strong>\<silur\></strong> wow  
<strong>\<suraeNoether\></strong> <https://arxiv.org/pdf/1204.1957.pdf>  
<strong>\<suraeNoether\></strong> and lastly, one more thing i’m kind of casually thinking about is andytoshi’s idea for outputs where “addresses change.” my best idea so far is to have each output be addressed to a <em>set</em> of destination addresses, each with their own timelock, but all sharing a key image (somehow)(  
<strong>\<suraeNoether\></strong> really the challenge is to come up with a representation of a single key image for a single output but with multiple destination addresses each with their own timelock  
<strong>\<suraeNoether\></strong> or rather: this would be one possible solution to the atomic swap refund transaction problem andytoshi brought up the other day.  
<strong>\<suraeNoether\></strong> and that’s all i have been working on  
<strong>\<suraeNoether\></strong> other than silur, is anyone working on anything fun?  
<strong>\<suraeNoether\></strong> or not fun as the case may be  
<strong>\<sarang\></strong> <http://nick.mtvnimages.com/nick/promos-thumbs/videos/spongebob-squarepants/spongebob-squarepants-fun-song-16x9.jpg?maxdimension=&quality=0.60>  
<strong>\<suraeNoether\></strong> okay  
<strong>\<moneromooo\></strong> About PRNG: I ported the Bitcoin PRNG to monero, it’s on github if anyone is curious.  
<strong>\<moneromooo\></strong> I added a contentious patch, so that one will either go, or be modified.  
<strong>\<suraeNoether\></strong> is the PRNG the contentious part or?  
<strong>\<moneromooo\></strong> I added seeding from /dev/random at startup.  
<strong>\<sarang\></strong> Can you link moneromooo ?  
<strong>\<suraeNoether\></strong> oh i see heh  
<strong>\<moneromooo\></strong> smooth thinks it should only be done if getrandom is not used, so I’ll probably do this.  
<strong>\<suraeNoether\></strong> i don’t know enough about the various pros and cons of that approach to have an opinion  
<strong>\<suraeNoether\></strong> on an administrative level, sarang: any word on the weekend course for talented high school students thing? i’m going to contact folks at the local universities around me this week to feel out the possibilities for a 2018 1-week summer workshop for undergraduates.  
<strong>\<moneromooo\></strong> <https://github.com/monero-project/monero/pull/2731>  
<strong>\<suraeNoether\></strong> thanks moneromooo  
<strong>\<sarang\></strong> Ah yes, thanks for the reminder surae  
<strong>\<sarang\></strong> So there has been interest expressed in two school programs  
<strong>\<suraeNoether\></strong> if you want we can collab on the proposal for the springtime one  
<strong>\<sarang\></strong> One would be a longer-term effort to work with North Carolina STEM students  
<strong>\<sarang\></strong> A shorter but logistically-simpler one is with Duke University for a spring weekend course for gifted high schoolers  
<strong>\<sarang\></strong> That’s a bit tougher due to the extremely short course time  
<strong>\<suraeNoether\></strong> yeah, i like the idea of spending a week or three with undergrads to teach them about crypto and maybe fork bitcoin or monero and mess with the code or something… but i’m not so sure how much we can even do over one weekend with high school students  
<strong>\<sarang\></strong> So maybe it’s better to nix the weekend course idea and try for the longer course?  
<strong>\<sarang\></strong> I don’t have a good sense of the logistics required for that  
<strong>\<sarang\></strong> But I’m investigating still  
<strong>\<sarang\></strong> Another option is to do a Duke summer program that’s 3 weeks long  
<strong>\<suraeNoether\></strong> sarang let’s try to set aside a few hours this week to figure out logistics of this. i would love for the monero community to fund up some education programs. that’s good PR for everyone, and starts a pipeline of education into the cryptocurrency world… but i don’t want to burden the monero community unnecessarily (for one thing) and if we can get a university to devote some money to this too, it  
<strong>\<suraeNoether\></strong> adds legitimacy  
<strong>\<sarang\></strong> The Duke summer one wouldn’t require any funding from the community  
<strong>\<sarang\></strong> since students are paying to go to it  
<strong>\<suraeNoether\></strong> ok, so we have the Duke TIPP thing as a possibility there to reduce the burden on the community  
<strong>\<sarang\></strong> Yep, and because they already have a supply of gifted students identified  
<strong>\<suraeNoether\></strong> and maybe the first summer we should do something like that rather than taking point ourselves on organizing the program  
<strong>\<sarang\></strong> Let’s talk about that option  
<strong>\<suraeNoether\></strong> cool  
<strong>\<sarang\></strong> I’ve proposed new summer courses before. It’s more involved than the weekend ones, but not bad at all  
<strong>\<sarang\></strong> We both meet the instructor qualifications  
<strong>\<suraeNoether\></strong> can you put out feelers in that direction and then we can talk about the responses you receive later this week?  
<strong>\<sarang\></strong> Can do  
<strong>\<suraeNoether\></strong> cool  
<strong>\<sarang\></strong> I need to find the timeline for new course proposals for the summer. We may have missed it already  
<strong>\<suraeNoether\></strong> oh, that would suck  
<strong>\<sarang\></strong> Yeah, I’ll check  
<strong>\<sarang\></strong> They’re always hunting for new STEM courses though  
<strong>\<sarang\></strong> So they might make an exception  
<strong>\<sarang\></strong> especially for me :D  
<strong>\<suraeNoether\></strong> ok, maybe make a call or shoot an email today then, keep me updated  
<strong>\<suraeNoether\></strong> okay, anyone else have anything they want to discuss?  
<strong>\<sarang\></strong> Just emailed the bosses  
<strong>\<suraeNoether\></strong> cool  
<strong>\<suraeNoether\></strong> Okay, well if no one has anything else for now  
<strong>\<knaccc\></strong> I was kinda wondering if you could give a brief explanation of whether bileanear pairings might be good for the future, for people like me who have no idea what it means  
<strong>\<suraeNoether\></strong> aha  
<strong>\<sarang\></strong> Surae, wanna take this?  
<strong>\<suraeNoether\></strong> actually not at all  
<strong>\<knaccc\></strong> hehe  
<strong>\<suraeNoether\></strong> ha  
<strong>\<suraeNoether\></strong> okay i will  
<strong>\<sarang\></strong> lol  
<strong>\<suraeNoether\></strong> ok knaccc so… bilinear crypto is essentially a way of taking an easy group and gluing it with hard group into a pair. And you do operations on the pair of curve points instead of an individual curve point. tthis is on it’s own, useless  
<strong>\<silur\></strong> surae you just opened a world before me saying that posets are isomorphic to DAGs how I didn’t notice this \<3  
<strong>\<suraeNoether\></strong> silur my dissertation is aaaaaal about po-groups  
<strong>\<suraeNoether\></strong> if, however, you have a “bilinear pairing”  
<strong>\<suraeNoether\></strong> you can move stuff from one of these two groups to the other  
<strong>\<knaccc\></strong> so bilinear pairingss still use e.g. curve25519/ed25519?  
<strong>\<sarang\></strong> One useful case is aggregate signatures that use exponentiation  
<strong>\<suraeNoether\></strong> afaik there are not many curves compatible with bilinear pairing  
<strong>\<sarang\></strong> The transfer between groups is what allows for verification  
<strong>\<suraeNoether\></strong> hence CSW’s weird meltdown on twitter  
<strong>\<knaccc\></strong> ah so it’d be a diffferent curve that would have to be used then?  
<strong>\<sarang\></strong> Yeah, it’s an idealization right now  
<strong>\<suraeNoether\></strong> so, a really dumb way to describe it is: if i need to know something about (A,B+C), I can hit it with the bilinear pairing e and treat that like (A+C,B)  
<strong>\<suraeNoether\></strong> or rather  
<strong>\<knaccc\></strong> and what’s an easy group vs hard group?  
<strong>\<suraeNoether\></strong> oh, like Zq versus X25519  
<strong>\<knaccc\></strong> oh i see  
<strong>\<suraeNoether\></strong> with bilinear pairings, the DDH problem is trivial to solve  
<strong>\<sarang\></strong> You can also look at hardness as meaning hardness assumptions of problems  
<strong>\<sarang\></strong> yeah  
<strong>\<suraeNoether\></strong> <em>nod</em>  
<strong>\<sarang\></strong> So the security definitions get really picky, for good reason  
<strong>\<knaccc\></strong> are you aware of any performance implications of bilinear pairings  
<strong>\<suraeNoether\></strong> yeah so, a linear function is one that behaves like this: f(a\*X + b\*Y) = a\*f(X) + b\*f(Y). a <em>bilinear</em> function has two inputs instead of one, (a\*X+b\*Y, c\*Z + d\*W), and it behaves linearly in each coordinate  
<strong>\<suraeNoether\></strong> knaccc i am not  
<strong>\<sarang\></strong> It would depend on the groups and the mapping  
<strong>\<sarang\></strong> I think the current implementation limitations mean there hasn’t been solid analysis on that yet  
<strong>\<suraeNoether\></strong> did everyone see Craig Wright embarassing himself about this stuff, btw? on reddit and twitter  
<strong>\<sarang\></strong> Also depends on our use case  
<strong>\<sarang\></strong> Signature aggregation is just one application that sparked our interest  
<strong>\<sarang\></strong> No\!  
<strong>\<sarang\></strong> Link plz surae  
<strong>\<knaccc\></strong> can you define signature aggregation?  
<strong>\<suraeNoether\></strong> oh haha  
<strong>\<suraeNoether\></strong> <https://www.reddit.com/r/Bitcoin/comments/79bnox/vitalik_and_uandytoshi_calling_out_csw_for_his/?utm_term=7fd17439-49d1-4d0f-90c7-a42272b3f896&utm_medium=search&utm_source=reddit&utm_name=frontpage&utm_content=1>  
<strong>\<suraeNoether\></strong> CSW claims he invented bitcoin and he used the secp256k1 curve because it’s compatible with bilinear pairings  
<strong>\<silur\></strong> ahahhaha :D  
<strong>\<suraeNoether\></strong> and while that is kind of technically true, you need to store 10^70 or more bits, you know, a number comparable to the number of particles in the universe  
<strong>\<suraeNoether\></strong> very entertaining read  
<strong>\<suraeNoether\></strong> knaccc sig aggregation is a way of taking one or more signatures and combining them into a single signature, aggregating them  
<strong>\<knaccc\></strong> for the purposes of saving space, verification time, both?  
<strong>\<sarang\></strong> knaccc you save space  
<strong>\<sarang\></strong> it’s constant in the \# of sigs  
<strong>\<sarang\></strong> verification is currently linear  
<strong>\<sarang\></strong> there are implications for things like certificate chains etc.  
<strong>\<knaccc\></strong> ah that leads me to my last quick question: i think someone mentioned that it was ‘provable’ that verification time had to be always linear  
<strong>\<suraeNoether\></strong> well, ruffing proved that a ring sig scheme is linear in verification time  
<strong>\<sarang\></strong> Agg. sigs are not ring sigs  
<strong>\<knaccc\></strong> ah ok that was my question. it’s ring signature specific then  
<strong>\<knaccc\></strong> aha  
<strong>\<sarang\></strong> They can be completely independent sigs  
<strong>\<silur\></strong> do we have the updated ruffCT paper?  
<strong>\<knaccc\></strong> i see  
<strong>\<sarang\></strong> and in fact the messages have to be distinct  
<strong>\<knaccc\></strong> cool thanks sarang suraeNoether  
<strong>\<silur\></strong> I started on overview on that but sarang and surae told me it’s outdated  
<strong>\<suraeNoether\></strong> silur i can email you the copy i received from ruffing, but the bootle paper isn’t private and ruffing’s scheme is “Bootle + regular old multisig”  
<strong>\<suraeNoether\></strong> <https://eprint.iacr.org/2015/643>  
<strong>\<suraeNoether\></strong> silur the ruffCT scheme basically does this: for each output used in the signature, build a row of a matrix, entries are ring members. for each column of your resulting matrix, you should have a commitment to an amount, and the signature is essentially proving with an NIZK proof that you can open one of the commitments to zero  
<strong>\<suraeNoether\></strong> the idea is that you know the actual keys in one of those columns  
<strong>\<suraeNoether\></strong> but the code on the github is functional and up to date, and if you compare it to the bootle paper i’m pretty sure you’ll be able to figure it out without me needing to ask ruffing for more permission to share his paper that says “DO NOT SHARE” on the top lol  
<strong>\<silur\></strong> okay thanks  
<strong>\<suraeNoether\></strong> okay, everyone, I think I’m going to call this meeting (seems like knaccc ran out of questions)
