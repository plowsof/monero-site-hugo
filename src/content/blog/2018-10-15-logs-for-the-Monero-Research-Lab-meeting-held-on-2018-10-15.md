---
title: Logs for the Monero Research Lab Meeting Held on 2018-10-15
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> LET US BEGIN  
<strong>\<suraeNoether\></strong> yes hello  
<strong>\<sgp\_\></strong> Hello  
<strong>\<kovri-slack\> \<oneiric\></strong> hullo  
<strong>\<suraeNoether\></strong> today i want to chat about research and the monero konferenco, and… that’s my agenda. if folks want to add to the list, shout out\~  
<strong>\<sarang\></strong> hi  
<strong>\<sarang\></strong> Where to begin?  
<strong>\<suraeNoether\></strong> well, firstly  
<strong>\<suraeNoether\></strong> who wants to come give a 20-40 minute chat at the Monero Konferenco? I’d like each workgroup to have at least one representative  
<strong>\<hyc\></strong> when/where is that going to be?  
<strong>\<sarang\></strong> I’ll do one  
<strong>\<suraeNoether\></strong> Good question, hyc\! Right now it’s looking to be one of the weekends between April 27 and June 15 in Denver, Colorado. invited speakers will be reimbursed for their travel costs  
<strong>\<suraeNoether\></strong> assuming the community decides to fund my proposal, that is  
<strong>\<hyc\></strong> cool  
<strong>\<sarang\></strong> Can reimbursement be in XMR?  
<strong>\<suraeNoether\></strong> I’m leaning toward April 27, personally  
<strong>\<sarang\></strong> Or are there weird legally things with that  
<strong>\<kovri-slack\> \<oneiric\></strong> I could do one, or defer to anonimal if he wanted to do one  
<strong>\<suraeNoether\></strong> yes, reimbursement can be done in XMR, it just makes accounting moderately more annoying, but no legal issues  
<strong>\<sarang\></strong> cool  
<strong>\<suraeNoether\></strong> and i’m happy to do that  
<strong>\<sarang\></strong> Because fiat reimbursement is always a baffling and lengthy ordeal  
<strong>\<suraeNoether\></strong> well oneiric i wanted a session of several talks on networking privacy. i’d love to have both you and anonimal come speak  
<strong>\<kovri-slack\> \<oneiric\></strong> :)  
<strong>\<suraeNoether\></strong> i also want to invite people not directly related to the monero ecosystem  
<strong>\<parasew\[m\]\></strong> i will also try and come there\! as i could not make it to defcon sadly  
<strong>\<sarang\></strong> suraeNoether: are there plans to arrange for streaming or quality recording?  
<strong>\<sgp\_\></strong> Yeah, we need that  
<strong>\<suraeNoether\></strong> i really want to give folks who are up and coming a chance to speak at this event; we can invite really big name people to come talk, but i feel like their careers are already pretty well laid out before them, so it’d be nice to get some outside researchers who are more tangential to the crypto celebrity scene  
<strong>\<sarang\></strong> May I recommend hiring an outside group to handle that, and \_not\_ venue staff  
<strong>\<suraeNoether\></strong> sarang, one option laid out in the budget is a section on audio/visual rental and web streaming and costs; a local place that does webcast-style AV presentations regularly would charge around 5kUSD for such an event.  
<strong>\<sarang\></strong> Or at the very least getting someone with professional experience as an audio engineer  
<strong>\<sarang\></strong> cool\!  
<strong>\<suraeNoether\></strong> i posted last week on the forums for the FFS under ideas  
<strong>\<suraeNoether\></strong> i haven’t gotten comments. :P  
<strong>\<sarang\></strong> oops  
<strong>\<sarang\></strong> that’s my bad  
<strong>\<sarang\></strong> I thought I had read something on recording but it’s easier to just ask you and be lazy  
<strong>\<sarang\></strong> ty  
<strong>\<suraeNoether\></strong> not a problem, rehrar was mentioning something about cyphermarket and sponsorship and free toys and t-shirts  
<strong>\<suraeNoether\></strong> so i’m thinking we move the idea into “open discussion” and update from there  
<strong>\<suraeNoether\></strong> if folks have recommendations for speakers, we are assuming a decent travel cost on average for speakers, so if we can get a handful of relatively small-cost local-ish speakers, we can also have a decent budget for flying people out from further away  
<strong>\<parasew\[m\]\></strong> there are a lot of contacts from the open source hardware association in denver (open source hardware summit was there last year); i could reach out to ppl (audio engineer, etc.)  
<strong>\<sgp\_\></strong> Yeah, my RT Frontier flight is only \~$200 :)  
<strong>\<suraeNoether\></strong> i’m thinking a formal call for papers may be in order  
<strong>\<suraeNoether\></strong> sgp\_: excellente, come give a taaaaalk on blackballin brother  
<strong>\<suraeNoether\></strong> let us have a meeting of the minds  
<strong>\<suraeNoether\></strong> all the minds  
<strong>\<sarang\></strong> sgp\_: but you’re flying Frontier, so you’ll pay one way or another… =p  
<strong>\<suraeNoether\></strong> sarang zing  
<strong>\<suraeNoether\></strong> more like zi… ziring..  
<strong>\<suraeNoether\></strong> nah  
<strong>\<suraeNoether\></strong> okay, onto research  
<strong>\<sarang\></strong> Buy us a Monero jet and I’ll fly everyone there  
<strong>\<sgp\_\></strong> Lmao  
<strong>\<suraeNoether\></strong> last week, sarang and I concluded that, for now, RuPol may be too risky for us to implement, given the layers of development required  
<strong>\<suraeNoether\></strong> essentially un-vettable at this stage  
<strong>\<suraeNoether\></strong> once things are more clear, we can actually benchmark it  
<strong>\<sarang\></strong> The level of complexity required for verification computation is also unclear  
<strong>\<sarang\></strong> The authors left many, many implementation details out of their paper  
<strong>\<sarang\></strong> It suffices to say that there is a lot of annoying math still to be worked out  
<strong>\<suraeNoether\></strong> but for now, it relies on a previously described scheme that has it’s own typographical errors, etc, and at this point even workign out a single example by hand requires beautiful-mind-level of whiteboards on the walls  
<strong>\<suraeNoether\></strong> so we are falling back on ruffct for now to see how much the multiexp speedups we learned about during bulletproof implementations could help  
<strong>\<sarang\></strong> I’ve returned to our older RuffCT scheme, working to backport what we’ve learned from BPs about optimizations and batching  
<strong>\<sarang\></strong> jinx  
<strong>\<suraeNoether\></strong> im finna shutup now  
<strong>\<sarang\></strong> heh  
<strong>\<sarang\></strong> We can certainly speed up some operations on individual spend proofs, and that’s cool  
<strong>\<sarang\></strong> But  
<strong>\<sarang\></strong> The possibility of batching some parts of verification are quite intriguing  
<strong>\<sarang\></strong> especially relating to fixed group points  
<strong>\<sarang\></strong> I’m running some code and tests on this presently  
<strong>\<suraeNoether\></strong> in addition to all that, i’ve been working on the churn paper to formalize the threat model we discussed last week  
<strong>\<sarang\></strong> Also, I’ve finished some updated blackball testing  
<strong>\<suraeNoether\></strong> that’s going… really well, and i hope to have a draft to the community in a few days  
<strong>\<sarang\></strong> My hunch is that we’ll see those papers published with shitty information  
<strong>\<sarang\></strong> and the associated bad press  
<strong>\<suraeNoether\></strong> sarang i will want to dip into your blackball info in writing this to illustrate the negligibility of the gains from heuristic methods  
<strong>\<suraeNoether\></strong> i disagree, i think the papers weren’t sufficiently FUD-dy to really be worried about it, as long as they clarify “newly found” versus “total found”  
<strong>\<sgp\_\></strong> Sounds like a good co-op  
<strong>\<suraeNoether\></strong> but, you know, matt green says we have “fake privacy” so  
<strong>\<suraeNoether\></strong> :P  
<strong>\<kovri-slack\> \<oneiric\></strong> lol, really?  
<strong>\<suraeNoether\></strong> yeah some tweet from awhile ago \*shrug\*  
<strong>\<sarang\></strong> The Zcash mentality is that we offer shitty obfuscation  
<strong>\<sarang\></strong> I tend to not really pay attention to it  
<strong>\<suraeNoether\></strong> we happen to agree that ring signatures suck and they need to be replaced with something with larger anonymity set sizes  
<strong>\<gingeropolous\></strong> when ringsize 42  
<strong>\<suraeNoether\></strong> which is why sarang and I never really let go of the sublinear  
<strong>\<sarang\></strong> Those papers did a terrible job of differentiating things that are time-based or blockheight-based  
<strong>\<suraeNoether\></strong> no big deal  
<strong>\<sgp\_\></strong> Has anyone seen this new paper? <https://eprint.iacr.org/2018/962>  
<strong>\<suraeNoether\></strong> we saw a draft, not the final thing, i’m withholding judgement  
<strong>\<suraeNoether\></strong> sgp\_: i have seen this thing, but i have not yet read that thing  
<strong>\<suraeNoether\></strong> i need to learn about aurora and this thing  
<strong>\<sgp\_\></strong> Basically Zerocash applied to computations, no?  
<strong>\<sarang\></strong> trusted setup  
<strong>\<sgp\_\></strong> Just call them “trusted computations” :p  
<strong>\<sarang\></strong> lol  
<strong>\<hyc\></strong> still quite expensive, \<2 minutes generation time  
<strong>\<sarang\></strong> the setup is buried deep w/in the paper  
<strong>\<sarang\></strong> gmaxwell noted it in p15  
<strong>\<hyc\></strong> pls ignore the men behind the curtain  
<strong>\<sgp\_\></strong> Sounds like a typical trusted setup response  
<strong>\<suraeNoether\></strong> trusted setup reminds me of the phrase “military grade encryption”  
<strong>\<kovri-slack\> \<oneiric\></strong> lol, shady indeed  
<strong>\<sarang\></strong> Nah  
<strong>\<sarang\></strong> People brag about military encryption  
<strong>\<suraeNoether\></strong> no no  
<strong>\<sarang\></strong> They hide the setup deep within a definition  
<strong>\<suraeNoether\></strong> the phrase military grade encryption is usually a tongue-in-cheek reference to a plaintext message  
<strong>\<sarang\></strong> =p  
<strong>\<hyc\></strong> lol  
<strong>\<sarang\></strong> rot26  
<strong>\<hyc\></strong> smeaphore at least  
<strong>\<kinghat\></strong> are we military grade? or moar better?  
<strong>\<hyc\></strong> semaphore, or morse  
<strong>\<suraeNoether\></strong> sarang that reminds me  
<strong>\<sarang\></strong> ?  
<strong>\<sgp\_\></strong> We used a Caesar’s Cypher, totally secure. Roman military-grade  
<strong>\<suraeNoether\></strong> i really really want to create a cryptocurrency like monero but replacing the bernstein group with an absurdly small group, like order 7000-ish or something, and with a tiny-output hash function  
<strong>\<suraeNoether\></strong> just let people go wild in forging signatures  
<strong>\<suraeNoether\></strong> just see what happens  
<strong>\<suraeNoether\></strong> “when forgecoin moon?”  
<strong>\<suraeNoether\></strong> etc  
<strong>\<sarang\></strong> I’d like to see a version that uses a curve group with cofactor 1  
<strong>\<suraeNoether\></strong> ring size 2  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<sarang\></strong> yeah  
<strong>\<hyc\></strong> that can be the next generation of useless ethereum token  
<strong>\<suraeNoether\></strong> so, that’s my life for this week: ruffct with sarang and the churn paper, and fantasizing about rubiks-cubes-sized groups as a joke cryptocurrency  
<strong>\<suraeNoether\></strong> ohhhh man implementing a rubiks cube on top of ethereum would be \*such a waste of resources you guys\*  
<strong>\<sarang\></strong> Yup, I’ll be finishing up unit tests on optimized ruffct to get a better idea of batching  
<strong>\<suraeNoether\></strong> proving you are making each permutation omg  
<strong>\<suraeNoether\></strong> put it on the ledger forever man  
<strong>\<sarang\></strong> There was a neat paper I linked earlier about some optimized curve operations  
<strong>\<sarang\></strong> they found some better EC formulas in certain special cases  
<strong>\<sgp\_\></strong> Ethereum Plays Rubik’s Cube  
<strong>\<hyc\></strong> hm… rubkis cube solvers are pretty fast these days. would be funny to advertise a rubiks cube-based key system  
<strong>\<suraeNoether\></strong> oh yes, i am eager to read that. it seems to be strictly related to optimizations obtained from utilizing analytic formula/expressions for multiexp  
<strong>\<suraeNoether\></strong> for example, if you have point P = (x, y) and point Q = (z, w) on the ed25519 curve, we define P+Q using the equations of the elliptic curve, the twisted edwards polynomial equations  
<strong>\<sarang\></strong> They discuss some neat work on better addition chains  
<strong>\<suraeNoether\></strong> so if you want something like 3P + 4Q very often, you can expand that polynomial expression and exploit the structure within those analytic expressions to speed up the computations  
<strong>\<sarang\></strong> Goes to show that this is not a totally solved area of research  
<strong>\<sarang\></strong> I don’t see it being terribly useful here, mind you  
<strong>\<sarang\></strong> Anyone else with something fun to share about recent work, questions, ideas?  
<strong>\<sarang\></strong> Here’s a link to my quick port of ruffct to my python library: <https://github.com/SarangNoether/research-lab/tree/pyruff>  
<strong>\<sarang\></strong> It’s more or less a direct port of the java stuff that will be refactored as needed  
<strong>\<sarang\></strong> prototyping only; don’t use it anywhere that counts  
<strong>\<suraeNoether\></strong> oh, I wanted to point out: Vtnerd is asking for a very reasonable amount of USD/hour to construct a tor-based RPC tool for monero (or something like that), and his FFS is under “ideas” right now  
<strong>\<suraeNoether\></strong> i wanted to express my support for that proposal  
<strong>\<sarang\></strong> Tell me more about this in relation to kovri  
<strong>\<sarang\></strong> ELI5  
<strong>\<rehrar\></strong> Would RuffCT be pretty drop in as well? Or would it take large amounts of work to get it in?  
<strong>\<sarang\></strong> It’d be some work to safely transition old outputs  
<strong>\<sarang\></strong> that’s part of the prototyping process  
<strong>\<suraeNoether\></strong> afaict this is going to be a parallel thing, independent of kovri  
<strong>\<suraeNoether\></strong> but also since it’s not inventing new protocols, it should proceed with easier-to-anticipate milestones  
<strong>\<suraeNoether\></strong> some folks are of the opinion that multiple tools are beneficial; when it comes to tor, i2p, kovri… i tend to think the most beneficial tools will eventually see the most use  
<strong>\<sarang\></strong> rehrar: actual practical ruffct is still a bit pie-in-the-sky; but that’s part of our job  
<strong>\<sarang\></strong> it has implications on things like address size, for example  
<strong>\<sarang\></strong> but we’re learning what we can from it  
<strong>\<sgp\_\></strong> Only point I need to make is that if we want to get anywhere with blackball research, someone needs to update the pool tool and sneurlax is busy  
<strong>\<rehrar\></strong> regarding Tor, I think it would be beneficial to Monero to have the option to run over Tor  
<strong>\<sarang\></strong> MRL: Putting The Skunk In Skunkworks  
<strong>\<sarang\></strong> sgp\_: link to current work?  
<strong>\<suraeNoether\></strong> rehrar: ruffct as-is requires an additional user key, which would bring us to either 3 group elements as your public key, or 4, depending on how you interpret the ruffct paper, and so we may end up doubling our key length (which doubles verification time from loading keys\!)  
<strong>\<suraeNoether\></strong> sgp\_: any ideas? or does anyone want to help sgp\_ out with the pool tool?  
<strong>\<gmaxwell\></strong> suraeNoether: you can change the constants in the curve equation and get a tiny group with basically no other changes in the code, there are tests in libsecp256k1 that work that way.  
<strong>\<sgp\_\></strong> <https://github.com/sneurlax/xmreuse>  
<strong>\<suraeNoether\></strong> gmaxwell: delightful :)  
<strong>\<kovri-slack\> \<oneiric\></strong> yeah, having a public node over tor would be nice. even a hybrid of p2p over tor, rpc over i2p would be sweet  
<strong>\<sarang\></strong> gmaxwell: you are referring to a cofactor-1 curve?  
<strong>\<sarang\></strong> oh nvm, you mean group size  
<strong>\<hyc\></strong> we have moneroworld nodes on tor  
<strong>\<rehrar\></strong> Of course it’s possible to run Monero over Tor with some finagling. But how cool would it be to run over tor with a command or button press?  
<strong>\<rehrar\></strong> Qubes-Whonix is a good way right now btw  
<strong>\<sarang\></strong> perhaps we first get the moneroworld nodes upgraded at all…  
<strong>\<suraeNoether\></strong> okay, for me, final thoughts… please make comments on the Denver Monero Konferenco FFS here, and we will move it up to Open Discussion: <https://forum.getmonero.org/6/ideas/90909/surae-noether-first-denver-monero-konferenco-spring-2019> and for this conference, PLEASE please let me know if you know of someone who I absolutely MUST INVITE TO SPEAK. If you have a favorite speaker, let me know by emailing  
<strong>\<suraeNoether\></strong> <surae.noether@protonmail.com>  
<strong>\<suraeNoether\></strong> I’ll be sending out first-round invitation emails in the next week or so  
<strong>\<suraeNoether\></strong> or just email me because i’m lonely  
<strong>\<hyc\></strong> lol. I can cook up a talk  
<strong>\<hyc\></strong> by next spring we should have a much better idea of whether/how well randomJS will work  
<strong>\<sarang\></strong> If there isn’t a talk on RandomJS there will be riots  
<strong>\<rehrar\></strong> heck, I may start a Riot anyways  
<strong>\<hyc\></strong> lol  
<strong>\<rehrar\></strong> it’s a decent little app on the Matrix protocol  
<strong>\<rehrar\></strong> \#nerdjokes  
<strong>\<suraeNoether\></strong> cool, we can have a session on hardware and proof of work and maybe invite some asic or fpga manufacturers  
<strong>\<hyc\></strong> ah a mini-track, yeah  
<strong>\<kovri-slack\> \<oneiric\></strong> head-to-head debate hyc v. timolson?  
<strong>\<sarang\></strong> Other questions or research topics?  
<strong>\<hyc\></strong> though if we’ve done our work right, no asic/fpga guys will want to speak to us ever again  
<strong>\<sarang\></strong> heh  
<strong>\<kovri-slack\> \<oneiric\></strong> was reading up on ML techniques, would LSTM/regression be helpful for blackball analysis?  
<strong>\<sarang\></strong> I don’t think so  
<strong>\<sarang\></strong> Given our ring sizes and the actual risks involved, we understand it decently well  
<strong>\<sarang\></strong> Things like forks will always be more of an issue than random selection errors  
<strong>\<sarang\></strong> if that’s what you mean oneiric  
<strong>\<sarang\></strong> Even a deterministic approach to identify spent rings reveals relatively few, and each of these has a negligible effect on other rings  
<strong>\<kovri-slack\> \<oneiric\></strong> kind of, I meant applying the learning algo to new forks rather than tuning by hand. I might be misunderstanding blackballing though  
<strong>\<sarang\></strong> The risk from forks is spending on both forks, which reveals your spend  
<strong>\<sarang\></strong> on-chain risks involve things like pool outputs and set-theoretic analysis  
<strong>\<sarang\></strong> The goal of blackballing is to identify \_definitely\_ spent outs  
<strong>\<sarang\></strong> and that’s a hard game to play that gives you progressively lesser benefits over time  
<strong>\<sarang\></strong> I suppose we can begin to wrap up the official meeting  
<strong>\<kovri-slack\> \<oneiric\></strong> ok, thanks sarang  
<strong>\<sarang\></strong> Thoughts on anything that people would like to see investigated for this next week?  
<strong>\<sarang\></strong> oneiric: I think some people worry that their outputs can get “caught up” in a blackball list, but this isn’t the case  
<strong>\<sarang\></strong> The methods we use only determine if it’s provable that an output is already spent, which does not affect anyone’s funds  
<strong>\<gmaxwell\></strong> (the name ‘blackball’ is really kind of unfortunate.)  
<strong>\<sarang\></strong> gmaxwell: agreed  
<strong>\<sarang\></strong> I’ve been using the term “spent note” in my paper drafts  
<strong>\<sarang\></strong> I’d prefer something like that or “dead output”  
<strong>\<gmaxwell\></strong> Spent Note List (SNL) would hae been much better.  
<strong>\<sarang\></strong> We could update it each week, in a Weekend Update  
<strong>\<kovri-slack\> \<oneiric\></strong> Live from New York..  
<strong>\<gmaxwell\></strong> Well, sunday is a day of rest so one should do it on saturday, but perhaps as late as possible..  
<strong>\<gmaxwell\></strong> :P  
<strong>\<sarang\></strong> Well, thanks to everyone for participating in our meeting; we are now adjourned, and informal convos shall continue
