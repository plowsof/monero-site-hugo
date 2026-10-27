---
title: Logs for the Monero Research Lab Meeting Held on 2018-02-12
summary: Bulletproofs, auditing Bulletproofs, dedicated Monero conference, and miscellaneous
tags: [dev diaries, crypto, research]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<suraeNoether\></strong> Allrighty everybody  
<strong>\<sarang\></strong> Gather ‘round, everyone; it’s almost time  
<strong>\<suraeNoether\></strong> Welcome welcome  
<strong>\<ErCiccione\></strong> hi research lab folks\!  
<strong>\<MoroccanMalinois\></strong> hi  
<strong>\<suraeNoether\></strong> So we don’t really have an agenda. I want to sort of go around the circle and see what folks have been working on. Sarang and I blabbed a lot last week, so we can go last.  
<strong>\<sarang\></strong> Someone\! Anyone\!  
<strong>\<serhack\></strong> Hello\!  
<strong>\<ArticMine\></strong> hi  
<strong>\<sarang\></strong> Orrrrr one of us can go if nobody volunteers?  
<strong>\<ArticMine\></strong> Please  
<strong>\<gingeropolous\></strong> i discovered “R shiny”, a package that’ll let me turn my R sims into little webpages so ppl can fiddle with them. Still working on wrapping it into my “code”  
<strong>\<sarang\></strong> Oh nice  
<strong>\<suraeNoether\></strong> oh actually  
<strong>\<suraeNoether\></strong> gingeropolous we should talk about that  
<strong>\<suraeNoether\></strong> because I have these simulations of a cryptocurrency network, blocks being propagated, each node tracks its own local blockchain and computes difficulty, modulating its own local block arrival rate  
<strong>\<suraeNoether\></strong> i built it so that i can test consensus rules like spectre or phantom or nakamoto, or difficulty computations, stuff like that  
<strong>\<gingeropolous\></strong> cool.  
<strong>\<suraeNoether\></strong> it’d be fantastic for that to fit into a webpage with animations  
<strong>\<gingeropolous\></strong> there have been a couple of cryptocurrency network simulators over the years… did u roll your own?  
<strong>\<suraeNoether\></strong> does your package take R code and execute it in the browser clientside? or does it take a transcript of a simulation from R and animates it?  
<strong>\<suraeNoether\></strong> yeah, i rolled my own  
<strong>\<suraeNoether\></strong> a lot of the simulators out there don’t do what i want them to do, or do way too much  
<strong>\<gingeropolous\></strong> i honestly don’t know if it’ll do what I want yet. Generally, there’s a web page where a user can plug in parameters and hit “go”. Then the R script runs on the server, and when done, delivers the results  
<strong>\<gingeropolous\></strong> so it may not do a live animation, where u can tweak params on the fly  
<strong>\<suraeNoether\></strong> aaaah interesting, mine doesn’t either, but you can program the parameters to change dynamically  
<strong>\<gingeropolous\></strong> but you could set timeframes and get output for a given timeframe  
<strong>\<suraeNoether\></strong> that’s fantastic, we should talk more about that later  
<strong>\<gingeropolous\></strong> cool. i’ll let u know when i get my dyn blocksize one wrapped  
<strong>\* suraeNoether</strong> thumbs up  
<strong>\<suraeNoether\></strong> cool, sarang, want to bring us up to speed on how your last week unrolled?  
<strong>\<sarang\></strong> Sure, plenty to discuss  
<strong>\<sarang\></strong> First up, BPs  
<strong>\<sarang\></strong> Updated paper was released that talks optimizations  
<strong>\<sarang\></strong> We’ve implemented them already (the ones we intended to, at least)  
<strong>\<sarang\></strong> I had worked up a BP tech note discussing how we differed from the original paper, but the new paper makes that obsolete  
<strong>\<sarang\></strong> I checked the new paper against our code and we’re golden  
<strong>\<sarang\></strong> This will help the audit  
<strong>\<sarang\></strong> For the audit, Benedikt Buenz is interested and will be available soon  
<strong>\<sarang\></strong> Waiting on OSTIF SoWs from this week… other groups were less willing to share data publicly, which I do not like  
<strong>\<sarang\></strong> I’ll put up an FFS to fund Benedikt and a pro group, with overruns going toward conferences or to general fund  
<strong>\<sarang\></strong> I’ll be speaking at an intro cryptocurrency conference in Portland next month; funded by the organizers, so no FFS needed  
<strong>\<sarang\></strong> Either suraeNoether or I will likely speak at a large TEDx youth event in April  
<strong>\<sarang\></strong> PHANTOM paper (cousin to SPECTRE) was released and is under review  
<strong>\<sarang\></strong> Finally, summer course…  
<strong>\<sarang\></strong> there’s an option for a single 3-week course or two 3-week courses. It’d be a full-time role, so I’m weighing the options for which to accept  
<strong>\<sarang\></strong> Opinions/comments/questions welcome for all of these things  
<strong>\* sarang</strong> drops the microphone  
<strong>\<suraeNoether\></strong> wow. any questions?  
<strong>\<ErCiccione\></strong> a ton of good news :)  
<strong>\<sarang\></strong> Soooooo how long should I be away this summer =p  
<strong>\<sarang\></strong> It’s a lot of work to teach these intensive courses, but I’ve had a lot of students go on to do math/CS because of their summer course participation, so it works  
<strong>\<serhack\></strong> whoa, a lot of activities\! amazing\!  
<strong>\<sarang\></strong> Yeah, a busy month\!  
<strong>\<suraeNoether\></strong> It’ll probably be a nice 3-week break from directly working on bulletproofs, you’ll enjoy having that intellectual shift in gears  
<strong>\<ArticMine\></strong> One the optimizations what is the good news bottom line on tx size and verification time? Since this affects fees blocksize etc  
<strong>\<sarang\></strong> So txn size is unchanged from the initial multi-output stuff we worked on  
<strong>\<sarang\></strong> For verification time I’ll have to check the benchmarks… there are basically two classes of speedups there  
<strong>\<sarang\></strong> One is for established nodes… they’ll use the multiexp operations we’ve introduced, which lead to much faster verification than the Borromeans  
<strong>\<sarang\></strong> The second is for new nodes… they can batch verify as many txns as they want very quickly  
<strong>\<moneromooo\></strong> It’s set up to batch per block fwiw, so current nodes also benefit.  
<strong>\<sarang\></strong> Sure, but I assume much less  
<strong>\<sarang\></strong> I’ve considered the batch verification to really be for the new nodes, since they have a lot to work on  
<strong>\<moneromooo\></strong> Well, it’s not set up to batch across blocks :)  
<strong>\<sarang\></strong> Did not know that\!  
<strong>\<suraeNoether\></strong> on another note, someone brought up the question: why do our range proofs cover such a large size? which made me think of some of my own questions: isn’t verification time for a range proof linear in the size of the set? And if so, would it really be 2^-32 times faster to validate a range proof on \[0, …, 2^32\] than \[0, …, 2^64\]? i realized i have some gaps in my range proof knowledge  
<strong>\<sarang\></strong> Fortunately that’s not a consensus thing, so a client could do that later  
<strong>\<sarang\></strong> moneromooo: why not batch across blocks for new nodes?  
<strong>\<moneromooo\></strong> More complicated.  
<strong>\<sarang\></strong> Ha, fair answer  
<strong>\<moneromooo\></strong> Besides, range proofs are only checked since last end of known hash data.  
<strong>\<hyc\></strong> (Hi all. just dropped in. Just finished giving a Monero lecture here at Ulster University in Belfast. So far doesn’t look like I hooked any aspiring graduates…)  
<strong>\<sarang\></strong> hyc: still worth it\!  
<strong>\<suraeNoether\></strong> hyc so i take it the fiddle is only <em>mythically</em> hypnotic, not literally, then?  
<strong>\<suraeNoether\></strong> so what’s with the range proof set size? sarang? thoughts?  
<strong>\<sarang\></strong> So ArticMine the optimizations are for the verifier time, not for txn size in this case  
<strong>\<sarang\></strong> Well the only requirement is that the \# of bits be a power of 2  
<strong>\<hyc\></strong> lol. I screwed up, played at end of talk instead of beginning ;)  
<strong>\<sarang\></strong> txn size is basically unaffected by this  
<strong>\<sarang\></strong> So it comes down to the increase in verifier time  
<strong>\<sarang\></strong> and the complexity of making the range size be height-dependent  
<strong>\<ArticMine\></strong> and verification still scales linearly with number of outputs so no real changes on fees ,, block weight / size etc  
<strong>\<sarang\></strong> Right, just with faster constants  
<strong>\<ErCiccione\></strong> uuh belfast, tiocfaidh ár lá hyc\!  
<strong>\<suraeNoether\></strong> ok, so anyway  
<strong>\<suraeNoether\></strong> :)  
<strong>\<sarang\></strong> So  
<strong>\<sarang\></strong> Questions on the audit?  
<strong>\<sarang\></strong> Or speaking engagements?  
<strong>\<sarang\></strong> Or summer teaching?  
<strong>\<sarang\></strong> 3 weeks vs 6 weeks?  
<strong>\<moneromooo\></strong> I’d like to know when’s the deadline to have a cleaned up patchset for BPs for the review. I’ve been busy elsewhere and kinda left it lying as is for the last… week or two.  
<strong>\<moneromooo\></strong> I lose track of time.  
<strong>\<suraeNoether\></strong> i haven’t the foggiest idea, you’re the person i would have asked. :P  
<strong>\<sarang\></strong> Well  
<strong>\<suraeNoether\></strong> oh actually  
<strong>\<suraeNoether\></strong> you meant for the code review  
<strong>\<sarang\></strong> Benedikt will be reviewing the Java code, so no worries there  
<strong>\<sarang\></strong> I want to have the other audit started within a month  
<strong>\<moneromooo\></strong> Yes. When do I need to have it ready and cleaned up :)  
<strong>\<moneromooo\></strong> OK.  
<strong>\<sarang\></strong> There’s no real deadline; they’ll start when we’re ready  
<strong>\<sarang\></strong> But the OSTIF groups are being slow on SoW  
<strong>\<sarang\></strong> I’ve been told this week  
<strong>\<sarang\></strong> and then time to review, raise funds, and give them the go-ahead  
<strong>\<sarang\></strong> hence the month  
<strong>\<hyc\></strong> wait, auditing the java code? so we still need someone to verify that the C++ impl matches the java  
<strong>\<sarang\></strong> The only other change to be ported from Java since the last code I sent is just the code comments referencing paper lines, which are changed now  
<strong>\<sarang\></strong> hyc yes  
<strong>\<sarang\></strong> We’re doing both  
<strong>\<suraeNoether\></strong> benedikt is doing the java, i believe OSTIF was going to do the C++  
<strong>\<sarang\></strong> Benedikt will verify that the Java matches the math  
<strong>\<sarang\></strong> since he did the math  
<strong>\<hyc\></strong> ok  
<strong>\<sarang\></strong> OSTIF group will do the C++ to the Java  
<strong>\<sarang\></strong> and the paper, to the extent they can  
<strong>\<sarang\></strong> I wanted overlap  
<strong>\<suraeNoether\></strong> there is some fault-tolerance value in checking two implementations instead of one  
<strong>\<sarang\></strong> Well, and Benedikt knows the math better than anybody, and had already done a separate more general Java working  
<strong>\<suraeNoether\></strong> Anyway, at my end of MRL, my work this past week was largely focused on multisig and musig. I expressed concern last week that our current multisig scheme is vulnerable to key cancellation. since then, luigi1111 has proven me wrong, which is fantastic: when we compute keys, we use an authentication procedure that ensures that a key-cancelling adversary can’t both cancel keys and pass authentication  
<strong>\<suraeNoether\></strong> without violating the discrete log assumption.  
<strong>\<suraeNoether\></strong> but i’m still looking into musig’s manner of computing keys, which is a way of computing aggregate keys without an authentication procedure in one step, which is nice, but not necessary  
<strong>\<suraeNoether\></strong> for our purposes  
<strong>\<suraeNoether\></strong> in addition to that, I’ve been communicating with Tim Ruffing and his colleague Russel Lai about an upcoming paper on their sublinear ring signatures that re-uses group elements and integers to reduce signature space and verification time, which is neat  
<strong>\<suraeNoether\></strong> more generally for sublinear ring signatures, though, I’ve been sort of casually looking into how one would implement a ring signature with an arithmetic circuit. so we can exploit the goodness of bulletproofs for our signatures also  
<strong>\<sarang\></strong> Yeah, revisiting that with the addition of some group operation optimizations will be intriguing  
<strong>\<suraeNoether\></strong> yeah, actually that brings up the following point  
<strong>\<suraeNoether\></strong> all the multi-exp optimizations that we have been enjoying with bulletproofs will make RTRS RingCT much faster as it is  
<strong>\<suraeNoether\></strong> we may need to do some benchmarking. no matter what, this sublinear ring signature idea seems to not want to die. :)  
<strong>\<hyc\></strong> yay, nice. and I suspected bulletproofs would do more for us, that’s very interesting  
<strong>\<sarang\></strong> BPs have a lot of potential  
<strong>\<suraeNoether\></strong> knowing blockstream, they’ll beat us to it, but hey  
<strong>\<sarang\></strong> Blockstream is working on the AC stuff quite heavily  
<strong>\<sarang\></strong> but their work is on a different curve and a different codebase  
<strong>\<sarang\></strong> a beautiful synergy  
<strong>\<sarang\></strong> plenty of upward mobility  
<strong>\<sarang\></strong> other business lingo like that  
<strong>\<sarang\></strong> Any other topics of interest?  
<strong>\<sarang\></strong> I think I’ve covered the major ones for m  
<strong>\<sarang\></strong> \*me  
<strong>\<suraeNoether\></strong> I already mentioned my cryptocurrency network simulation, which is a sort of sandbox to test things like SPECTRE and PHANTOM and variations in difficulty computations, and to test things like how network topology influence security of various proposals under various attack scenarios  
<strong>\<suraeNoether\></strong> which if anyone is interested, is here: <https://github.com/b-g-goodell/research-lab/tree/master/source-code/Poisson-Graphs>  
<strong>\<sarang\></strong> Poison graphs, eh?  
<strong>\<sarang\></strong> deadly  
<strong>\<suraeNoether\></strong> currently produces a transcript of events as the network evolves. the code needs better commetns and more detailed reports, and there is one known bug, but  
<strong>\<suraeNoether\></strong> and i took an issue out already with that bug  
<strong>\<suraeNoether\></strong> In addition to all that and the educational outreach Sarang mentioned, I’ve also been looking into the first monero conference idea more deeply  
<strong>\<sarang\></strong> I love the idea  
<strong>\<gingeropolous\></strong> any thoughts on difficulty algo?  
<strong>\<ArticMine\></strong> Excellent idea  
<strong>\<sarang\></strong> gingeropolous: let’s chat about the state of that  
<strong>\<suraeNoether\></strong> I am scoping out a handful of locations this week. Most of the venues I’ve looked at cost between 7500 USD and 10k USD for two days. Catering would cost around 3k for two days, AV equipment will be at most a 3-4k, which is probably an over-estimate  
<strong>\<suraeNoether\></strong> if we provide travel support to, say, 9 speakers, and take them all out to dinner, that’s an additional 4k or so  
<strong>\<suraeNoether\></strong> in total, not including web presence and advertising and printing up programs and stuff, we’re looking at under 25k for the entire event  
<strong>\<sarang\></strong> How does that compare to the earlier estimates you had?  
<strong>\<suraeNoether\></strong> cheaper by a few thousand  
<strong>\<sarang\></strong> Nice  
<strong>\<sarang\></strong> Will you charge for tickets?  
<strong>\<sarang\></strong> to offset?  
<strong>\<ArticMine\></strong> What locations are you considering?  
<strong>\<suraeNoether\></strong> ArticMine: All the locations I’m looking into are in the Denver area  
<strong>\<scoobybejesus\></strong> How many potential attendees?  
<strong>\<gingeropolous\></strong> the right place for paranoia  
<strong>\<suraeNoether\></strong> initial numbers were 75-100, but i’m terrified of mis-estimating that  
<strong>\<suraeNoether\></strong> if this were a pharmaceutical conference, to get 100 attendees, you need to send out 3000 invitations or more  
<strong>\<suraeNoether\></strong> any cost above what I just quoted would be marketing costs  
<strong>\<sarang\></strong> I expect a lot of people will want to go, but travel will be their deciding factor  
<strong>\<hyc\></strong> lol. Who is the target audience, devs, general user community?  
<strong>\<suraeNoether\></strong> and I would prefer this to be a small technical sort of thing rather than a big flashy Dash-funded concert  
<strong>\<suraeNoether\></strong> i want folks to present technical talks on privacy-enhancing technologies in cryptocurrencies  
<strong>\<sarang\></strong> That part sounds like a lot of overlap with the Redacted conference that the Portland group is planning  
<strong>\<gingeropolous\></strong> can i pump my ico?  
<strong>\<suraeNoether\></strong> gingeropolous: I love Ice Cream Offerings, brother, you are more than welcome  
<strong>\<gingeropolous\></strong> please dedicate many thousands to ice cream catering  
<strong>\<sarang\></strong> Actually nvm suraeNoether, they’ve tooled their conference to be general/business privacy  
<strong>\<ArticMine\></strong> The question of protocol scaling in Monero vs virtually an other coin is significant  
<strong>\<ArticMine\></strong> any other  
<strong>\<suraeNoether\></strong> ArticMine: agreed, and we face some very unique challenges specific to our protocol  
<strong>\<ArticMine\></strong> and some significant advantages  
<strong>\<suraeNoether\></strong> So after I take a look at actual venues, I’ll have it narrowed down to a few specific locations.  
<strong>\<suraeNoether\></strong> Does anyone have any questions for either me or Sarang, or did anyone hop in late and want to describe a project they’ve been working on?  
<strong>\<sarang\></strong> What’s the event name?  
<strong>\<suraeNoether\></strong> i’m sure someone will come up with a good acronym  
<strong>\<oneiric\></strong> what is rough estimate for a date?  
<strong>\<suraeNoether\></strong> Summer 2019  
<strong>\<sarang\></strong> Kunvenante  
<strong>\<sarang\></strong> “gathering”  
<strong>\<gingeropolous\></strong> so… i think this conference is great… is there any chance we could get an event planner to do this? U two are way too overqualified and valuable, timewise…  
<strong>\<gingeropolous\></strong> unless this is a nice mental bikeride  
<strong>\<suraeNoether\></strong> I’ve been speaking with an event planner pro-bono actually  
<strong>\<shillobear\></strong> will carlos matos be a guest speaker?  
<strong>\<suraeNoether\></strong> all the numbers I gave you are from an e-mail form her  
<strong>\<hyc\></strong> nice  
<strong>\<sarang\></strong> gingeropolous: I absolutely do not want to plan a conference 0\_0  
<strong>\<suraeNoether\></strong> sarang ^  
<strong>\<gingeropolous\></strong> noice  
<strong>\<suraeNoether\></strong> and if we decide to go forward with it (it seems like everyone is okay with that) we’ll contract out with her directly once things are a little more finalized  
<strong>\<hyc\></strong> sounds like a great idea.  
<strong>\<hyc\></strong> on that note I gotta bug out. ttyl  
<strong>\<sarang\></strong> Yeah we’re just about at 18:00 now  
<strong>\<sarang\></strong> Last remarks?  
<strong>\<suraeNoether\></strong> good night and good luck\!  
<strong>\<suraeNoether\></strong> or good morning\!  
<strong>\<oneiric\></strong> sorry if dumb question, is the revised bulletproofs paper up somewhere?  
<strong>\<sgp\></strong> Sorry for missing the meeting. I read the logs and everything looks good to me :)  
<strong>\<sarang\></strong> oneiric: <https://eprint.iacr.org/2017/1066.pdf>  
<strong>\<oneiric\></strong> thanks sarang :)  
<strong>\<sarang\></strong> np  
<strong>\<suraeNoether\></strong> Kongreso Monero 2019  
<strong>\<suraeNoether\></strong> Monero Kongreso? :P  
<strong>\<gingeropolous\></strong> Kongrenero  
<strong>\<gingeropolous\></strong> portmanteau all the things  
<strong>\<gingeropolous\></strong> and then we can have an intro video to the tune of “Canyanero”  
<strong>\<sarang\></strong> excellent reference  
<strong>\<suraeNoether\></strong> Kongreso Monero Barolo?  
<strong>\<gingeropolous\></strong> i;ll work on organizing an overnight hackathon dj’d by boris brejcha, 10 PM to 6 AM.
