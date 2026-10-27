---
title: Logs for the Monero Research Lab Meeting Held on 2018-03-05
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> howdy everyone\~  
<strong>\<endogenic\></strong> hello  
<strong>\<suraeNoether\></strong> Agenda is, as usual: I describe what I’ve done for the past week or so, and field questions, and Sarang does the same. If anyone else is working on projects, we want to hear about other people’s contributions, too\!  
<strong>\<suraeNoether\></strong> at any time, feel free to jump in and ask questions  
<strong>\<sgp\_\[m\]\></strong> hey  
<strong>\<suraeNoether\></strong> if it gets too chaotic, we’ll try to rein it in  
<strong>\<suraeNoether\></strong> oh fluffypony forgot him  
<strong>\<sarang\></strong> Shall we begin?  
<strong>\<suraeNoether\></strong> Yep. How about you go first, brother noether  
<strong>\<sarang\></strong> Sure  
<strong>\<sarang\></strong> The BP audit fundraising FFS is ready and in Open Tasks, waiting for an admin to move to Funding Required  
<strong>\<sarang\></strong> We’re setting a stretch goal of 3 auditors, and will fund as many as we raise funds for  
<strong>\<sarang\></strong> Kudelski is pushing back on payment in XMR, but I’m trying to get them to work with OSTIF  
<strong>\<sarang\></strong> If they do, we can pay OSTIF in XMR and they’ll convert to USD and pay the auditor  
<strong>\<fluffypony\></strong> FFS has been moved  
<strong>\<sarang\></strong> Thanks fluffypony  
<strong>\<sarang\></strong> Otherwise we have to ensure that we can legally do the exchange to USD and pay them ourselves  
<strong>\<sarang\></strong> As soon as we have enough XMR for Bunz, we’ll hire him  
<strong>\<sarang\></strong> then QuarksLab, then Kudelski  
<strong>\<sarang\></strong> If we can’t reach an arrangement with Kudelski, we can replace them with X41, which will work with OSTIF for payment  
<strong>\<sarang\></strong> Other than that, working on some Pippenger stuff for fast multiexponentiation, reviewed a few papers regarding RingCT  
<strong>\<sarang\></strong> Posted my monthly report on r/Monero  
<strong>\<sarang\></strong> Those are the big things\!  
<strong>\<suraeNoether\></strong> nice. Does anyone have any questions?  
<strong>\<rehrar\></strong> hiya  
<strong>\<rehrar\></strong> We’re now in Funding Required btw  
<strong>\<sarang\></strong> yup yup  
<strong>\<rehrar\></strong> oh, didn’t see fp’s comment there  
<strong>\<sarang\></strong> <https://giphy.com/gifs/excited-ron-paul-its-happening-rl0FOxdz7CcxO>  
<strong>\<sarang\></strong> I’ll be working with each auditor throughout the process, so this will occupy an known amount of my time for the next couple of months  
<strong>\<suraeNoether\></strong> I have a question, sarang, which is: what are you excited to work on now that the bulletproof range proof audit stuff is going to be spread around a bit?  
<strong>\<sarang\></strong> ah yes  
<strong>\<sarang\></strong> I’m looking forward to doing a more thorough analysis of operation optimization in our current stuff and in proposals like RingCT replacements  
<strong>\<sarang\></strong> and interested in RingCT futures in general  
<strong>\<sarang\></strong> Now that the blockchain will be smaller and verifications faster, anonymity has been moving to the forefront  
<strong>\<suraeNoether\></strong> neat. that leads me to questions about multi-exp optimization in our current scheme  
<strong>\<suraeNoether\></strong> like, in general, it seems like all our EC operations could be made much more speedy  
<strong>\<suraeNoether\></strong> across the board  
<strong>\<sarang\></strong> Depends on what types of operations you mean  
<strong>\<sarang\></strong> Multiexp? Sure  
<strong>\<sarang\></strong> The precise way depends on the size of the operations and curvepoints involved  
<strong>\<sarang\></strong> There’s no single silver bullet that’s always better  
<strong>\<suraeNoether\></strong> ah i see  
<strong>\<sarang\></strong> Using a combo of Bos-Coster and Straus handles a lot of cases  
<strong>\<sarang\></strong> Pippenger is next up, based on results from andytoshi et al. on their curve  
<strong>\<suraeNoether\></strong> I’d be very curious to see how much faster MLSAGs can get with more efficient operations  
<strong>\<sarang\></strong> The nice thing is that multiexp is probably biggest opportunity for savings, since the current scaling is so bad  
<strong>\<sarang\></strong> I’m pretty much done if someone else wishes to speak now  
<strong>\<sarang\></strong> I just like listening to the sound of my own keyboard  
<strong>\<suraeNoether\></strong> Well, this past week I got the multisig paper to the point where I am seeking feedback/corrections from community members. You can read the current version (main.tex) here. <https://www.sharelatex.com/read/bfjfkdgnhgvh>  
<strong>\<suraeNoether\></strong> I am confident that the bones of the thing are correct, but details need to be fleshed out  
<strong>\<suraeNoether\></strong> the C++ code appendix must still be reviewed  
<strong>\<suraeNoether\></strong> so i’m not seeking feedback on the appendix yet: i know it’s wrong, and I have a list of ways its wrong  
<strong>\<sarang\></strong> There were a few rumblings on whether or not we’d like to take this audit momentum and keep applying it elsewhere, like to multisig  
<strong>\<sarang\></strong> Thoughts?  
<strong>\<rehrar\></strong> \*cough\*RingCT?\*cough\*  
<strong>\<sarang\></strong> I believe it’d be good for security and also excellent PR  
<strong>\<sarang\></strong> Ha yes rehrar that was also brought up for sure  
<strong>\<suraeNoether\></strong> I didn’t know there were rumblings on that. i think a weak point of my presentation is the C++ code review, for sure  
<strong>\<sarang\></strong> informal rumblings  
<strong>\<suraeNoether\></strong> i actually think I have a pretty clever proof structure that I’m attempting this afternoon that may make things even smaller  
<strong>\<rehrar\></strong> rumblings sans top hats  
<strong>\<andytoshi\></strong> re BPs. in libsecp we use strauss then pippinger. we changed our prover from doing the recursive scheme to one that directly computes L and R with a big multiexp at each iteration, and got an almost 2x speedup  
<strong>\<suraeNoether\></strong> but, again, that’s the \*theoretical\* end of the review  
<strong>\<suraeNoether\></strong> andytoshi dayumn brother  
<strong>\<sarang\></strong> andytoshi: nice\!  
<strong>\<andytoshi\></strong> i think i can get a bit more by combining generators at some levels  
<strong>\<sarang\></strong> We did basically zero optimizations to the prover, since that’s done once  
<strong>\<sarang\></strong> suraeNoether: auditing the implementation would be key  
<strong>\<suraeNoether\></strong> if we have money left over from the BP audit, I would be happy sitting on the leftover XMR for a month to see if we can get an audit of multi-ringCT out of a single funding round  
<strong>\<sarang\></strong> I very much doubt we’d have enough to fund another complete audit  
<strong>\<sarang\></strong> Might depend on price movement  
<strong>\<suraeNoether\></strong> eh, who knows where the market will be in a month  
<strong>\<suraeNoether\></strong> rihgt  
<strong>\<suraeNoether\></strong> that’s all i’m saying  
<strong>\<sarang\></strong> But we could combine leftovers with a new FFS and ride the wave of support for audits  
<strong>\<suraeNoether\></strong> after reading through the C++ code, the only real complaint I had was to increase the \# of rounds of chacha encryption  
<strong>\<suraeNoether\></strong> on another note, I’m writing up a brief technical note on sublinear ring signatures.  
<strong>\<suraeNoether\></strong> and why we haven’t implemented them yet  
<strong>\<suraeNoether\></strong> or, to be more specific  
<strong>\<suraeNoether\></strong> The idea is this: (i) small anonymity sets are worse than large anonymity sets, (ii) authentication still requires touching all keys in the anonymity set at least once, leading to linear verification times, and (iii) improving the space-efficiency of a blockchain therefore interacts with this linear verification time in a way that produces a space-time trade-off, leading to (iv) a trade-off between  
<strong>\<suraeNoether\></strong> traceability and the space-time efficiency of the blockchain… and I want to discuss (v) several ways that several different currencies have handled this trade-off, and (vi) implications from cost of running an untraceable cryptocurrency network at scale on this time-space trade-off.  
<strong>\<suraeNoether\></strong> Other than working with sarang to get the multisig paper up to peer review shape, soliciting comments from the community on that, and working on this trade-off technical note, I’ve also been reading papers like Sarang.  
<strong>\<sgp\_\[m\]\></strong> What other currenices of notehave handled this tradeoff with ring signatures?  
<strong>\<suraeNoether\></strong> none, but other currencies have hadnled it without ring signatures, i.e. zcash  
<strong>\<sarang\></strong> The tradeoff I see is a replacement with proof structures requiring trusted setup  
<strong>\<sarang\></strong> yeah ^  
<strong>\<sarang\></strong> There was a paper out with suggestions for Monero, but they too involved a trusted-setup accumulator  
<strong>\<sarang\></strong> (and this fact was buried within the paper…)  
<strong>\<andytoshi\></strong> yeah, trusted setups are often really hard to find in papers  
<strong>\<andytoshi\></strong> academics seem to think it’s not an important thing  
<strong>\<andytoshi\></strong> some academics\*  
<strong>\<sarang\></strong> I was surprised since the paper was specifically about Monero  
<strong>\<sarang\></strong> And our views on trust are pretty clear  
<strong>\<andytoshi\></strong> yeah that’s weird  
<strong>\<sarang\></strong> I expect that’s \_why\_ they buried it  
<strong>\<andytoshi\></strong> :\|  
<strong>\<sarang\></strong> anyhoo  
<strong>\<sarang\></strong> suraeNoether: carry on…  
<strong>\<suraeNoether\></strong> So, papers: 1) Matthew Green shared his “squeezing crowds” paper, which is a constant-space way of describing the complete set of ring members in a transaction. Link here: <https://isi.jhu.edu/~mgreen/mixing.pdf> This is a non-trivial result that will help Monero scale eventually… but it solves a problem that isn’t yet a problem and may not be for a long while  
<strong>\<rehrar\></strong> that new paper by Green?  
<strong>\<suraeNoether\></strong> great minds brother  
<strong>\<sarang\></strong> I know moneromooo had some concerns about transaction height in general  
<strong>\<sarang\></strong> but I can’t speak for him  
<strong>\<rehrar\></strong> Does it have drawbacks if it was theoretically implemented tomorrow (i.e. not large ringsizes yet)?  
<strong>\<moneromooo\></strong> Oh that wasn’t about the paper itself, just general about when I thought about this.  
<strong>\<sarang\></strong> right  
<strong>\<sarang\></strong> I’m working through the Green paper as well  
<strong>\<suraeNoether\></strong> rehrar literally all it does is \*describe the public keys for use in the signature.\* you still need to pull the public keys out of the blockchain and plug them into the verification equation.  
<strong>\<moneromooo\></strong> But in retrospect, if you include the height at which you make the sampling, it all goes away.  
<strong>\<suraeNoether\></strong> so this own’t help us get larger rings.  
<strong>\<moneromooo\></strong> Given fake out list size is not our bottleneck, no. Maybe later.  
<strong>\<sgp\_\[m\]\></strong> Can you elaborate a little more on what the paper says?  
<strong>\<suraeNoether\></strong> sure, so they define a Recoverable Sampling Scheme  
<strong>\<sarang\></strong> It says you can use a keyed hash function to succinctly describe the ring members to be used in a transaction  
<strong>\<suraeNoether\></strong> so, say you want to construct a ring {A, B, C}  
<strong>\<suraeNoether\></strong> rather than sending keys A, B, and C along with the transaction, you send information for constructing a hash function  
<strong>\<suraeNoether\></strong> if you compute a quick hash of the blockchain using that information, out pops the keys you want to use in the ring signature  
<strong>\<luigi1111\></strong> Sender grinds or what  
<strong>\<sgp\_\[m\]\></strong> All right, with you so far. Why does this have relatively small impact?  
<strong>\<suraeNoether\></strong> and their approach scales with the number of outputs, not the number of inputs. So \*describing\* a transaction with 1000 ring members and five outputs is 99% more efficient with an RSS than with our current scheme  
<strong>\<suraeNoether\></strong> but you still need the signature  
<strong>\<suraeNoether\></strong> and yous till need to verify it  
<strong>\<suraeNoether\></strong> and verifying the signature takes O(N) time. in this case, with 1000 ring members, it’s implausible  
<strong>\<suraeNoether\></strong> well except for weirdos  
<strong>\<moneromooo\></strong> Should not need to grind, make a random + offset should be enough.  
<strong>\<suraeNoether\></strong> in general, you need ring sizes around 10-15 before the RSS scheme actually saves space  
<strong>\<suraeNoether\></strong> one may consider it a database trick for accessing keys efficiently, perhaps, rather than a privacy-enhancing thing  
<strong>\<suraeNoether\></strong> unless i’ve wholly misunderstood their paper  
<strong>\<luigi1111\></strong> Hmm moneromooo but that doesn’t sound like a hash function  
<strong>\<luigi1111\></strong> Anyway doesn’t matter  
<strong>\<sgp\_\[m\]\></strong> ok, thanks for the info  
<strong>\<suraeNoether\></strong> yeah  
<strong>\<suraeNoether\></strong> SO  
<strong>\<sarang\></strong> Yes suraeNoether it’s just about descriptors for bandwidth savings over large sample sets  
<strong>\<sarang\></strong> and the use of a hash function means they get proofs of security out of it  
<strong>\<sarang\></strong> not privacy  
<strong>\<suraeNoether\></strong> in addition to that, I’ve been reading about arithmetic circuits, idly tinkering with my cryptocurrency network simulation tool, thinking about large anonymity sets  
<strong>\<suraeNoether\></strong> but Sarang and I kind of have an announcement, I guess. We are starting an educational non-profit called Multidisciplinary Academic Grants in Cryptocurrency. Our primary goal will be to provide scholarships to students, research grants to researchers, and infrastructure grants to schools.  
<strong>\<rehrar\></strong> whoa. And this is a ‘separate from MRL’ type thing?  
<strong>\<sarang\></strong> Legally separate, yah  
<strong>\<suraeNoether\></strong> yep. The original idea was to start a pipeline between the research world and the cryptocurrency world  
<strong>\<binaryFate\></strong> Nice\! Do you see possible ties to the Monero FFS for scholarships and grants?  
<strong>\<sarang\></strong> We’ll get the benefits of being a U.S. registered nonprofit  
<strong>\<sarang\></strong> binaryFate: abso-freaking-lutely  
<strong>\<suraeNoether\></strong> See, after attending several schools that seemed so resistant to cryptocurrencies, I think it’s a shame that a lot of students won’t be getting a decent education in cryptocurrencies, especially when we’re talking about the future world economy  
<strong>\<suraeNoether\></strong> and after speakign with fluffypony and a partner in South Africa, I realized… like… for the cost of a year of college here in the US, that’s… an entire schoolteacher’s salary in South Africa  
<strong>\<suraeNoether\></strong> Chile has a similar situation going on  
<strong>\<binaryFate\></strong> cool idea  
<strong>\<suraeNoether\></strong> and if we can manage to encourage education in financial privacy, improve cryptocurrency literacy, etc etc, these are all good things for the economy as a whole…  
<strong>\<sarang\></strong> It also has the side benefit of helping Monero’s image  
<strong>\<sarang\></strong> and letting community members give back in a different way  
<strong>\<suraeNoether\></strong> and not to mention: Monero’s image as a contributor to education would be an extremely valuable thing for the future of Monero, in terms of development, interest, research, etc. HOW COOL will it be when the first principal investigator who received a MAGIC grant gets tenure or gets an award for a paper they wrote while being funded by us?  
<strong>\<suraeNoether\></strong> ha  
<strong>\<suraeNoether\></strong> again, great minds  
<strong>\<sarang\></strong> jinx  
<strong>\<binaryFate\></strong> Missed “MAGIC”. Just do it already\! :)  
<strong>\<sarang\></strong> The idea is that it’s legally not tied to Monero (to keep things simple) but can be heavily funded anonymously by Monero community members  
<strong>\<sarang\></strong> and the 501(c)(3) structure will help integrate with institutions and schools better than some random group  
<strong>\<sarang\></strong> kudos to suraeNoether for doing all the legwork on this  
<strong>\<sarang\></strong> I’m just along for the ride  
<strong>\<sarang\></strong> binaryFate: yeah, MAGIC internet money…  
<strong>\<sarang\></strong> Worth noting for the scrupulous among us that donations may be tax-deductible if you’re in the U.S.  
<strong>\<suraeNoether\></strong> Thing is, if you go visit a college campus, you’ll notice something: the really sweet campuses, the beautiful ones, the country-club campuses… those are the ones that get funding from alumni. you would think that schools that are dumps, the president house is on fire and the dorms are rioting, these are the schools that should get funding. not how it usually goes. i would love it if MAGIC started  
<strong>\<suraeNoether\></strong> funding folks to go to community college and some of those folks ended up building world-changing stuff out of Monero.  
<strong>\<suraeNoether\></strong> and I would love it if the Monero community was responsible for building a library for some disadvantaged kids in south africa. :P  
<strong>\<suraeNoether\></strong> Not to mention, this gives us a legal vehicle to fund academic conferences for Monero  
<strong>\<sarang\></strong> ^^ yesss  
<strong>\<suraeNoether\></strong> So, that’s the educational outreach “secrets in the works” that I’ve been keeping under my hat for a few weeks  
<strong>\<sarang\></strong> It definitely felt like accepting anonymous crypto to fund a nonprofit would rile up the government, but apparently not if you do it correctly  
<strong>\<rehrar\></strong> accept XVG?  
<strong>\<sarang\></strong> -\_\_\_\_\_-  
<strong>\<sarang\></strong> sure  
<strong>\<suraeNoether\></strong> Currently we have a partner in ZA and a partner at Clemson University who are interested in being board members, for the two very different ends of the spectrum  
<strong>\<suraeNoether\></strong> I am filing the paperwork to incorporate today  
<strong>\<sarang\></strong> MAGIC doesn’t need to GAF about crypto politics  
<strong>\<sarang\></strong> If someone wants to donate to help students, awesome  
<strong>\<sarang\></strong> too bad zcash just announced their grant program too  
<strong>\<sarang\></strong> we want the spotlight =p  
<strong>\<rehrar\></strong> well that’s all super cool. Glad that you guys are doing awesome things.  
<strong>\<suraeNoether\></strong> Oh, and one last thing: this paper was just put out only a few days ago. Has anyone read it yet? <https://eprint.iacr.org/2018/241>  
<strong>\<rehrar\></strong> easy sarang. Just make your grant program more grant-ier  
<strong>\<rehrar\></strong> and have free pizza. Spotlight all yours.  
<strong>\<sarang\></strong> suraeNoether: I have not yet  
<strong>\<sarang\></strong> Naturally suraeNoether will also be on the board?  
<strong>\<andytoshi\></strong> oof neha asked me to read that quite a while ago (before publication) and i forgot  
<strong>\<suraeNoether\></strong> ok, well is anyone else working on anything interesting they want to share? andytoshi i know you aren’t a direct MRL contributor, but I’m certainly curious about what yall have been up to  
<strong>\<andytoshi\></strong> BP optimizations mainly  
<strong>\<sarang\></strong> I think he puts blocks into a stream or something  
<strong>\<andytoshi\></strong> lol  
<strong>\<sarang\></strong> but in very efficient ways  
<strong>\<andytoshi\></strong> i implemented an optimization from benedikt where we do one less recursion (so we expose two more scalars but save one L/R pair so it’s a wash)  
<strong>\<andytoshi\></strong> this gives us a \~8% speedup in batch verification of single-range rangeproofs  
<strong>\<sarang\></strong> andytoshi: that’s the one you discussed with me earlier?  
<strong>\<andytoshi\></strong> yeah i think so  
<strong>\<rehrar\></strong> So, I obviously have zero idea about this, but how long does an audit take to do?  
<strong>\<sarang\></strong> We’re looking at up to a month each  
<strong>\<sarang\></strong> but the times overlap  
<strong>\<rehrar\></strong> Right.  
<strong>\<sarang\></strong> maybe a little more, maybe a little less  
<strong>\<rehrar\></strong> I ask this for two reasons, 1. for BP audits  
<strong>\<rehrar\></strong> but 2. what would it look like to devote a bit of MRL time to help audit codebases of other security-focused projects in the privacy space  
<strong>\<rehrar\></strong> i.e. Veracrypt, KeepassXC, etc.  
<strong>\<rehrar\></strong> it may not be at all feasible, obviously. But just thought I’d ask  
<strong>\<sarang\></strong> That’s a huge undertaking  
<strong>\<rehrar\></strong> That’s what I figured.  
<strong>\<sarang\></strong> and I think it’s outside the scope of our intent  
<strong>\<sarang\></strong> Plus we’re hardly an independent group  
<strong>\<sarang\></strong> so our results might be viewed as inherently biased  
<strong>\<sarang\></strong> That’s really what groups like OSTIF are for  
<strong>\<sarang\></strong> Organizing audits of important tech  
<strong>\<sarang\></strong> (and it’s why we’re working with them now)  
<strong>\<rehrar\></strong> ok :)  
<strong>\<sarang\></strong> We’re approaching the end time, and suraeNoether had to leave a bit early  
<strong>\<sarang\></strong> Any other topics of interest to bring up?  
<strong>\<sarang\></strong> OK\!  
<strong>\<sarang\></strong> Thanks to everyone for joining in
