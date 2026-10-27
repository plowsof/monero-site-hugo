---
title: Logs for the Monero Research Lab Meeting Held on 2018-06-25
summary: MRL work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> let's get this partay starteeeeed  
<strong>\<suraeNoether\></strong> Agenda today: 1. Greetings. 2. Brief MRL update. 3. Show and tell\! 4. Who's going to defcon?  
<strong>\<suraeNoether\></strong> hi everyone  
<strong>\<oneiric\_\></strong> hullo  
<strong>\<suraeNoether\></strong> Okay, 2. I have finally posted all our meetings logs here: <https://github.com/b-g-goodell/research-lab/tree/master/meta/research-meeting-logs>  
<strong>\<suraeNoether\></strong> I didn't want to fork the whole meta repo just to keep track of our research meeting logs, so I just started a folder  
<strong>\<isthmuscrypto\></strong> Greetings\!  
<strong>\<suraeNoether\></strong> if anyone objects or wants to make PRs to monero-project's meta repo to track our logs, I'm fine with that, too, but this is easiest for me to deal with.  
<strong>\<needmoney90\></strong> Morning all  
<strong>\<sgp\_\[m\]\></strong> Hello  
<strong>\<suraeNoether\></strong> morning isthmuscrypto and needmoney90  
<strong>\<suraeNoether\></strong> Another update, Sarang will be back next week I believe  
<strong>\<suraeNoether\></strong> Other than that, Sarang and I will be at defcon, and we are excited to meet up with folks  
<strong>\<sgp\_\[m\]\></strong> They're more accessible if they are posted as a blog post on getmonero. Probably some value there  
<strong>\<suraeNoether\></strong> sgp\_\[m\]: would I make a PR to the monero-site repo then?  
<strong>\<binaryFate\></strong> hello  
<strong>\<sgp\_\[m\]\></strong> There are some open PRs now for the community meetings. Best to use those as a template  
<strong>\<suraeNoether\></strong> so the answer is yes, and to use those as a template? I haven't done any blog posts through the repo before, so I'm not sure exactly what the procedure is. :P  
<strong>\<selsta\></strong> they require markdown change  
<strong>\<suraeNoether\></strong> I'll look around and take care of it later today  
<strong>\<sgp\_\[m\]\></strong> Basically yes. It's not very difficult  
<strong>\<suraeNoether\></strong> cool, then easy thing to check off my list later  
<strong>\<suraeNoether\></strong> So, 3. Show and tell. Silur is here, isthmuscrypto is here, and both of them are working on rather interesting projects I'd like to hear about.  
<strong>\<silur\></strong> I'm struggling with testing my RTRS lib, and now got into VDFs, verifiable delay functions and trying to generalize them for lattices  
<strong>\<suraeNoether\></strong> i didn't catch isthmuscrypto's original description of his generalized adversarial networks, when he mentioned it for the first time a few weeks ago  
<strong>\<silur\></strong> and of course as usual lattices are more interesting than testing but I need to have RTRS done for HCPP :/  
<strong>\<suraeNoether\></strong> oooh VDFs are super super interesting to me  
<strong>\<isthmuscrypto\></strong> Hi @suraeNoether <https://github.com/Mitchellpkt/BlockchainAnalysisGAN>  
<strong>\<silur\></strong> I have a general VRF construction for DH and EC, PoC ready (I can share the notebook) and a blockchain is already adapting it, working on the lattice VRF now  
<strong>\<isthmuscrypto\></strong> I'm tied up in a meeting for the next 50 minutes and sneaking the MRL meeting on the side, so I'll be intermittent in responding.  
<strong>\<suraeNoether\></strong> ah silur, that's a conference I would have loved to attend if I had heard of it a few months earlier.  
<strong>\<silur\></strong> so my next step is to make the same for VDFs  
<strong>\<suraeNoether\></strong> that's awesome, silur\!  
<strong>\<silur\></strong> I'm sure we can figure something out  
<strong>\<silur\></strong> about HCPP  
<strong>\<suraeNoether\></strong> oh, no, i literally can't attend, but maybe next year.  
<strong>\<suraeNoether\></strong> oh that brings up something: I was thinking maybe we could start taking issues out on the monero-project/research-lab repo for conferences that the community might want us to attend  
<strong>\<suraeNoether\></strong> a lot of them I'm willing to go to out of pocket because they are great experiences, but keeping track of the wide world of conference calendars can be challenging  
<strong>\<isthmuscrypto\></strong> " track of the wide world of conference calendars can be challenging" \< sounds like we need a decentralized solution xD  
<strong>\<silur\></strong> MARKET GAP\! :D  
<strong>\<suraeNoether\></strong> tokenize it\!  
<strong>\<silur\></strong> ICO it  
<strong>\<oneiric\_\></strong> lol  
<strong>\<rehrar\></strong> hi  
<strong>\<suraeNoether\></strong> is it unreasonable to ask: if folks hear about a technical conference, literally anywhere in the world, at which MRL should have a presence, open up an issue about it on the monero-project/research-lab repo?  
<strong>\<suraeNoether\></strong> hi rehrar  
<strong>\<silur\></strong> so brings me back to a interesting bottleneck I can't overcome for weeks for all my current work  
<strong>\<silur\></strong> VDF, IVC, VRF, Bulletproofs....  
<strong>\<silur\></strong> ACs  
<strong>\<silur\></strong> I don't have any experience for arithmetization of boolean circuits  
<strong>\<silur\></strong> anyone willing to help out on that?  
<strong>\<silur\></strong> maybe not a meeting subject, let's go on with the agenda and get back on it later :D  
<strong>\<suraeNoether\></strong> well funny thing about that silur  
<strong>\<suraeNoether\></strong> boolean circuits are arithmetic circuits already, just not contrariwise  
<strong>\<suraeNoether\></strong> which is one of my favorite -wise suffixed words  
<strong>\<silur\></strong> well in Gf(2)  
<strong>\<silur\></strong> but most protocols need a galois field with a large prime base so I thought bulletproofs won't work ever on Gf(2)  
<strong>\<suraeNoether\></strong> ah that's what you meant  
<strong>\<silur\></strong> anyway I'm stuck now with QSP-s and a little less-efficient snark stuff to experiment with BPs  
<strong>\<suraeNoether\></strong> well, we'll chat about it later  
<strong>\<silur\></strong> yea sorry for holdin' the meeting :D  
<strong>\<suraeNoether\></strong> does anyone else have any interesting work they want to talk about? My work this past week has been into zero knowledge proofs and extractability requirements and schnorr signatures. primary reference of the week is this one (pdf link <https://link.springer.com/content/pdf/10.1007/3-540-48071-4\_28.pdf>)  
<strong>\<suraeNoether\></strong> primarily, I'm thinking it's possible we don't need to worry about the KOSK setting with only minor adjustments to our current scheme, and if that's the case, all the musig key computation and all the commit-and-reveal nonsense just goes away  
<strong>\<suraeNoether\></strong> in which case the whole paper will \*AGAIN\* collapse to something smaller  
<strong>\<suraeNoether\></strong> but I need some sanity checks from folks with more knowledge in the field of complexity theory  
<strong>\<suraeNoether\></strong> Other than that, I recently finished advising the ZCash Foundation in giving out 250kUSD in grants, I'm working on encrypted memo fields in Monero transactions, and I've been writing up my backlog statements of work. I've already broken 160 hours this month, but I like this job a whole lot so I'm not really taking weekends until I start feeling burnt out.  
<strong>\<silur\></strong> usual cryptographer's calendar :D  
<strong>\<suraeNoether\></strong> oh, earlier this week I made some commits to my PoissonGraph simulations (see here <https://github.com/b-g-goodell/research-lab/tree/simple/source-code/Poisson-Graphs/new>) which are \*inches\* away from successfully producing human-readable transcripts describing cryptocurrency network simulations.  
<strong>\<suraeNoether\></strong> The sim suite is for testing difficulty algorithms, consensus algorithms, and dynamical properties of the network.  
<strong>\<suraeNoether\></strong> a friend who just got a job at the university of Exeter (inspiration for Hogwarts) is interested in writing a population ecology-inspired paper demonstrating how ethereum can effectively prey upon bitcoin's hashrate by rewarding bitcoin block-withholding attacks using ethereum smart contracts.  
<strong>\<silur\></strong> wow this is awesome  
<strong>\<isthmuscrypto\></strong> o\_0  
<strong>\<suraeNoether\></strong> <https://arxiv.org/abs/1805.08832>  
<strong>\<suraeNoether\></strong> this paper is sort of the foundation of that idea  
<strong>\<suraeNoether\></strong> well  
<strong>\<suraeNoether\></strong> one part of the foundation  
<strong>\<oneiric\_\></strong> +1000 on the sim network research suraeNoether\!  
<strong>\<silur\></strong> oh yea I saw a paper based on this .... "vulnerability"?  
<strong>\<silur\></strong> <https://eprint.iacr.org/2018/581>  
<strong>\<suraeNoether\></strong> yes, exactly  
<strong>\<suraeNoether\></strong> that's another part of the foundation, but i haven't been able to find the reference recently, thank you  
<strong>\<suraeNoether\></strong> i forgot that was mccrory  
<strong>\<suraeNoether\></strong> also a nice guy  
<strong>\<suraeNoether\></strong> hmm, published june 6  
<strong>\<suraeNoether\></strong> i must have seen him talk about this  
<strong>\<suraeNoether\></strong> Allright, next meeting agenda point: who's going to defcon?  
<strong>\<rehrar\></strong> I am  
<strong>\<rehrar\></strong> and all of you should also  
<strong>\<suraeNoether\></strong> yay, i think most of the board of directors of MAGIC will be there, if not all of us  
<strong>\<suraeNoether\></strong> we should all go out for a dinner  
<strong>\<silur\></strong> but... it's in the... USA :'(  
<strong>\<suraeNoether\></strong> ugh, no kidding  
<strong>\<rehrar\></strong> 'murica  
<strong>\<suraeNoether\></strong> who wants to start a sea-cooled, solar-powered mining farm with me on the pacific coast of Costa Rica?  
<strong>\<oneiric\_\></strong> yes please  
<strong>\<oneiric\_\></strong> :)  
<strong>\<suraeNoether\></strong> who wants to fund it?  
<strong>\<oneiric\_\></strong> Elon Musk  
<strong>\<suraeNoether\></strong> good ole' elon  
<strong>\<suraeNoether\></strong> okay  
<strong>\<silur\></strong> i'm still thinking about defcon, also I have another blockchain security conf in vegas in october that I'm invited as a speaker but still couldn't get my head over getting into US  
<strong>\<silur\></strong> last year I think 2 ppl got arrested at defcon?  
<strong>\<silur\></strong> the wannacry and the election machine guy  
<strong>\<sgp\_\[m\]\></strong> ooh what conference?  
<strong>\<rehrar\></strong> just surround them so po po can't get to them  
<strong>\<rehrar\></strong> civil disobedience of whatever  
<strong>\<suraeNoether\></strong> if you are invited as a speaker, the conference should be able to write you a letter requesting a temporary visa for your visit, but i'm not sure if hungary is on the list of countries that need temporary visas even for a conference visit. i would assume so, because we have shut our borders to friggin canada  
<strong>\<silur\></strong> it's more complicated than that, I'm stateless  
<strong>\<suraeNoether\></strong> \!  
<strong>\<suraeNoether\></strong> good freaking luck  
<strong>\<silur\></strong> <https://www.hoshocon.com/>  
<strong>\<rehrar\></strong> does being stateless suck?  
<strong>\<rehrar\></strong> it sucks that you wouldn't be able to get into USA :/  
<strong>\<suraeNoether\></strong> being stateless is a desirable state for a hash-based signature scheme.  
<strong>\<rehrar\></strong> they should see about holding Defcon in Canada  
<strong>\<sgp\_\[m\]\></strong> Ugh Tues-Thurs  
<strong>\<suraeNoether\></strong> should we hold the monero conference in another country?  
<strong>\<silur\></strong> HCPP last year had a "secret" monero meeting, I met a dev guy there  
<strong>\<silur\></strong> he was giving away SO MANY stickers  
<strong>\<silur\></strong> so I guess HCPP is ideal :P  
<strong>\<suraeNoether\></strong> Okay, so anyway  
<strong>\<suraeNoether\></strong> :D  
<strong>\<oneiric\_\></strong> hold monero conf in Liberland: <http://www.liberland.org/>  
<strong>\<suraeNoether\></strong> Let's call this meeting what it is: done  
<strong>\<suraeNoether\></strong> \</meeting\>
