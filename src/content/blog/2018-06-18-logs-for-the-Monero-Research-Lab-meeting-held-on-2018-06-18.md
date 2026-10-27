---
title: Logs for the Monero Research Lab Meeting Held on 2018-06-18
summary: MRL work, DefCon plans, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> fluffypony knaccc luigi1111 anonimal binaryFate chachasmooth dEBRUYNE endogenic erciccione\_\[m\] gingeropolous hyc iDunk isthmuscrypto john\_alan JollyMort\[m\] jwinterm kenshi84 kerber m2049r\[m\] moneromooo MoroccanMalinois needmoney90 nioc othe philkode pigeons rehrar rrol\[m\] sarang sgp\_\[m\] stoffu unknownids vtnerd waxwing, research meeting in three minutes\~  
<strong>\<suraeNoether\></strong> and of course UkoeHB who is already here and aware :D  
<strong>\<silur\></strong> it’s time \\o/  
<strong>\<ArticMine\></strong> Hi  
<strong>\<rehrar\></strong> hi  
<strong>\<suraeNoether\></strong> 1. Greetings\! 2. Work from this past week. I was hoping to chat about BP fees and where they are currently at, i wanted to update folks on the multisignature paper and literature review, I wanted to share a few links to papers I’m reading… and open up the floor to anyone else doing anything fun and math and crypto related. 3. Plans for this upcoming week and defcon?  
<strong>\<suraeNoether\></strong> So, hi everyone :D  
<strong>\<suraeNoether\></strong> does anyone want to add anything to our little makeshift agenda before we get goin?  
<strong>\<suraeNoether\></strong> okay, cool  
<strong>\<suraeNoether\></strong> as far as bulletproofs go, apparently Quarkslab will be done by the end of the week and Benedikt has begun work (I think). Quarkslab has apparently found a few small optimizations, but no bugs so far (but that could be outdated info)  
<strong>\<suraeNoether\></strong> ArticMine: do you want to bring the community up to speed on where we are currently sitting in terms of bulletproofs fees? you’ve led the charge for a lot of that discussion  
<strong>\<rehrar\></strong> yay ArticMine  
<strong>\<ArticMine\></strong> I have the basic concept down  
<strong>\<ArticMine\></strong> Replacement of the blcoksize with block weight  
<strong>\<ArticMine\></strong> That is linear with an increase in verification time  
<strong>\<suraeNoether\></strong> i believe the last time we talked about this, taking space and time together into account led to a formula that was like n + log(n) in number of outputs. by picking fees based on n only, this means we are slightly under-compensating miners for large bulletproofs and slightly overcompensating them for smaller ones, leading to a weak batching incentivization without distorting our ideas of cost paid by the  
<strong>\<suraeNoether\></strong> miner in both space and time. since the space paid is logarithmic, its impact is rather small, even for large bulletproofs.  
<strong>\<ArticMine\></strong> This will replace the blocksize in the determination of the penalty. Fees then follow from the penalty based weight calculation using the current formula  
<strong>\<suraeNoether\></strong> \*nod\* are we not modifying the current formula to make overall fees lower?  
<strong>\<ArticMine\></strong> We are not modifying the formula however the weight will be a lot lower than our current blocksize  
<strong>\<ArticMine\></strong> So we still have to change the minimum fee  
<strong>\<ArticMine\></strong> For a 2 output transaction the block weight will equal the block size  
<strong>\<suraeNoether\></strong> ah i see  
<strong>\<suraeNoether\></strong> we should get a formal description of our proposed bulletproof fee structure out to the community so they can start discussing it soon  
<strong>\<suraeNoether\></strong> so I’ll try to put 2-3 hours into that this week  
<strong>\<ArticMine\></strong> What really matters is that as the number of outputs the weight scales linearly with number of outputs  
<strong>\<ArticMine\></strong> I expect to have a formal description out by the middle to the end of next week  
<strong>\<suraeNoether\></strong> cool, let us know if you need more hands  
<strong>\<ArticMine\></strong> After the weekend I expect to have 2-3 days I can dedicate to this  
<strong>\<ArticMine\></strong> There are a lot of details  
<strong>\<suraeNoether\></strong> we have some folks who are interested in contributing to MRL but don’t necessarily have a project, so there are lots of eyes we can put on it as well  
<strong>\<suraeNoether\></strong> Allright, moving on  
<strong>\<suraeNoether\></strong> I’ve been discussing our multisig scheme with UkoeHB and a few other folks. I have contacted one of the musig authors about an issue UkoeHB brought up. It’s… causing me sufficient pause to reach out. Essentially, my first (and second and third) reading of the scheme seems to allow for a replay attack  
<strong>\<silur\></strong> our multisig scheme ?= RTRS multisig?  
<strong>\<moneromooo\></strong> no, threshold sigs.  
<strong>\<suraeNoether\></strong> the musig scheme + our scheme. it \*seems\* to allow an honest adversary to be cloned or rewound in a way that may be dangerous. of course, in the musig paper there is a whole section on derandomization and not re-using signature data… this is a \*known issue\* but I’m not sure if their security model is sufficient.  
<strong>\<suraeNoether\></strong> our threshold scheme, not RTRS  
<strong>\<suraeNoether\></strong> so, due to this, i’ve gone back to some older papers on multisignatures and simulation theory to look into it  
<strong>\<suraeNoether\></strong> right now i’m reading a primer on simulation theory by Lindell, who is a good author and has written a rather comprehensive document on the matter (pdf link <https://eprint.iacr.org/2016/046.pdf>)  
<strong>\<suraeNoether\></strong> and i’ve gone back to some of the original certificate authority and/or KOSK assumption papers because their security models are highly relevant  
<strong>\<suraeNoether\></strong> <https://hovav.net/ucsd/dist/agg-sig.pdf>  
<strong>\<suraeNoether\></strong> during all this, by the way, I’m taking copious notes on multisignature schemes and old papers for a future literature review  
<strong>\<dEBRUYNE\></strong> ArticMine: Great to hear (about the fee stuff). I, however, hope we’re not making it unnecessarily complex  
<strong>\<ArticMine\></strong> The concepts are very simple and elegant if we work at the protocol level and change the penalty from block size to block weight  
<strong>\<suraeNoether\></strong> dEBRUYNE: eh, essentially we are merely changing the fee structure to count the outputs in a block instead of absolute size in bits, or bytes, or kb, or what have you, that’s the core idea of the change  
<strong>\<ArticMine\></strong> Strictly speaking we are changing the penalty formula to take into account ^  
<strong>\<suraeNoether\></strong> other than that (deep diving into the simulation theory and the dark corners of the multisig world), I wanted to see what other folks are working on (silur?), and maybe chat about defcon first, a monero conference second, and a MAGIC conference in privacy technologies third. things seem so quiet around here without sarang  
<strong>\<ArticMine\></strong> The fees then follow with essentially no change other than the minimum fee to account fro the much lower overall weight  
<strong>\<rehrar\></strong> sarang was the heart and soul of MRL  
<strong>\<ArticMine\></strong> A very important distinction is that the penalty formula is consensus while the fees are not  
<strong>\<rehrar\></strong> read: was  
<strong>\<ArticMine\></strong> was?  
<strong>\<silur\></strong> I’m continuing my RTRS implementation  
<strong>\<rehrar\></strong> was talking to suraeNoether, ArticMine  
<strong>\<silur\></strong> HCPP invited me to make a demo there  
<strong>\<suraeNoether\></strong> silur are you implementing that on github? have a link?  
<strong>\<silur\></strong> RTRS still needs heavy testing, i kinda tend to do ‘if it compiles it’s ready’  
<strong>\<silur\></strong> sure  
<strong>\<silur\></strong> <https://github.com/Silur/libstringct>  
<strong>\<suraeNoether\></strong> tim ruffing contacted me, their scheme has been modified and they are coming out with a newer version of it. as a sample, their signatures are about 1.12 kb for a ring size of 64  
<strong>\<suraeNoether\></strong> thanks silur  
<strong>\<rehrar\></strong> how long is verification for that ring size?  
<strong>\<silur\></strong> great to hear, although the current docs are already outdated  
<strong>\<silur\></strong> would be nice to have that paper out :D  
<strong>\<silur\></strong> are there any sketches on the mods?  
<strong>\<suraeNoether\></strong> he has been loose with details silur, but he contacted me about it tuesday last week and he said he’d get me the paper this week. maybe, maybe not. :P it’s how research goes, even at universities like saarlang  
<strong>\<suraeNoether\></strong> rehrar: no idea, i don’t wnat to speculate  
<strong>\<suraeNoether\></strong> rehrar but my knee jerk instinct is “about as much time as an LSAG with 128 ring members”  
<strong>\<ArticMine\></strong> Also are there any non linear with size verification times  
<strong>\<suraeNoether\></strong> or “no less than” instead of “about as much time as”  
<strong>\<suraeNoether\></strong> ArticMine: not with a usual ring signature model. technically you could count zk-snarks as sublinear verification time ring signatures that require a trusted set-up, but htere is nothing in the chasm/gulf between our untrusted set-up hash-based ring signatures and the zk-snark world  
<strong>\<suraeNoether\></strong> everything with RTRS has to take around double the amount of time for each group operation, since keys are double in length… and our hash-based set-up is pretty much as close to an information-theoretic minimum allowable in terms of “number of group operations” in order to compute a ring signature, we are very optimal in that regard, very few wasted computations… so “best case” RTRS will be double the  
<strong>\<suraeNoether\></strong> verification time of an LSAG  
<strong>\<suraeNoether\></strong> so, uh… what’s up with defcon  
<strong>\<ArticMine\></strong> The bottom line we do not have to deal with a situation similar with bulletproof verification times  
<strong>\<suraeNoether\></strong> who all is going to be at defcon?  
<strong>\<ArticMine\></strong> I am  
<strong>\<ArticMine\></strong> I am alos giving a talk related to the fee question  
<strong>\<ArticMine\></strong> also  
<strong>\<suraeNoether\></strong> nice  
<strong>\<suraeNoether\></strong> i heard something about a booth  
<strong>\<suraeNoether\></strong> i believe that sarang and I both declined actually having an MRL booth, but I’m happy to sit around at the monero booth for awhile, presuming… we have a booth (and now the word booth is meaningless, it’s been said too much. like the word kiosk)  
<strong>\<rehrar\></strong> hmmm…then there was a misunderstanding  
<strong>\<rehrar\></strong> I thought it was “we’d man the booth if there was one, but not for the whole time cuz we want to enjoy the conference”  
<strong>\<rehrar\></strong> I’ll communicate and change that right away if I was incorrect.  
<strong>\<suraeNoether\></strong> oh, no, i think i’m mis-remembering  
<strong>\<suraeNoether\></strong> we can totally do a booth  
<strong>\<suraeNoether\></strong> i need to make a t-shirt or something  
<strong>\<rehrar\></strong> it’d probably be split with Kovri temporally  
<strong>\<suraeNoether\></strong> turf warrrrr  
<strong>\<rehrar\></strong> I don’t think MRL needs to prepare anything special unless you guys want to  
<strong>\<rehrar\></strong> just sitting at the table and fielding questions would be sufficient  
<strong>\<suraeNoether\></strong> but i want a t shirt ;(  
<strong>\<suraeNoether\></strong> wait that’s winking  
<strong>\<suraeNoether\></strong> i meant :\*(  
<strong>\<suraeNoether\></strong> semicolons are so hard to use correctly  
<strong>\<rehrar\></strong> we’ll get you a tshirt, but it may not be what you expect  
<strong>\<rehrar\></strong> ;P  
<strong>\<rehrar\></strong> anyways, nothing else regarding defcon as far as I know  
<strong>\<suraeNoether\></strong> okay, so, in terms of other conferences, we originally had this idea to have the first Monero conference in Denver next spring, perhaps funded or hosted by the MAGIC non-profit (me, rehrar, sgp, and sarang and some non-monero-related people)  
<strong>\<suraeNoether\></strong> but we are trying to keep MAGIC more or less separate from Monero, (we are looking for some non-monero members to be on the board) becuase it’s an educational organization, not a project-oriented one  
<strong>\<suraeNoether\></strong> so we are going to host the MAGIC conference as a general privacy enhancing technology conference instead  
<strong>\<suraeNoether\></strong> and all funding for that will be through MAGIC, we won’t be starting an FFS for that  
<strong>\<suraeNoether\></strong> totally independent  
<strong>\<suraeNoether\></strong> BUT  
<strong>\<suraeNoether\></strong> the monero community deserves a freaking technical conference\!  
<strong>\<suraeNoether\></strong> so i wanted to get the community’s thoughts on starting a Monero conference-specific FFS. If I took charge of this, I would hire an event organizer to take care of a lot of it and spend time trying to get speakers for the conference.  
<strong>\<silur\></strong> FFS?  
<strong>\<suraeNoether\></strong> forum funding system  
<strong>\<silur\></strong> oooh  
<strong>\<endogenic\></strong> cool, go for it  
<strong>\<silur\></strong> great  
<strong>\<silur\></strong> really sorry I gotta run  
<strong>\<silur\></strong> best to y’all  
<strong>\<suraeNoether\></strong> ta silur  
<strong>\<suraeNoether\></strong> okay, the way i figure it, the monero conference is a good use of MRL resources and time, so I’ll post it under ideas with the current estimated price tag and we’ll see what happens from there. i think anything over-funded should go to the general fund  
<strong>\<suraeNoether\></strong> well, we’re rounding up on the hour here  
<strong>\<suraeNoether\></strong> does anyone have any questions?  
<strong>\<suraeNoether\></strong> maybe about the proceedings at MRL, what’s going on recently and what’s going to be going on over the next few weeks, any other general questions?  
<strong>\<suraeNoether\></strong> (my favorite color is blue and i’m probably a taurus and i like long walks on the beach)  
<strong>\<rehrar\></strong> hmmm…  
<strong>\<rehrar\></strong> I think I’m a gemini, would we work well together?  
<strong>\<rehrar\></strong> Or am I a something else?  
<strong>\<dEBRUYNE\></strong> ArticMine: Sounds interesting. Looking forward to the details of your fee proposal  
<strong>\<nioc\_\></strong> a question earlier from the lounge \>\> \<lenovuh\> some while ago, was there a discussion about letting new nodes bootstrap the blockchain quickly, that required new crypto techniques, afaik? i might have this completely wrong, but think i read about it in the research-lab channel  
<strong>\<m2049r\[m\]\></strong> if the meeting is over i would like to get back to the topic of exposing the index of a subaddress - from what i understood there are mixed statements about this. it may be a problem and it may not be. ??\!?  
<strong>\<suraeNoether\></strong> nioc\_: not sure about htat  
<strong>\<suraeNoether\></strong> yeah, we can call this meeting over :D  
<strong>\<suraeNoether\></strong> thanks everyone \</meeting\>
