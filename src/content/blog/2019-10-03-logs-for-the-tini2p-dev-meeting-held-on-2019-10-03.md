---
title: Overview and Logs for the tini2p Dev Meeting Held on 2019-10-03
summary: Current project status, Roadmap, Meta issues, and miscellaneous
tags: [dev diaries, i2p, crypto]
author: el00ruobuob / oneiric
---

# Logs

<strong>\<tini2p\_gitlab\></strong> meet time  
<strong>\<tini2p\_gitlab\></strong> 0: Greetings  
<strong>\<tini2p\_gitlab\></strong> hi all  
<strong>\<tini2p\_gitlab\></strong> 1: What's been done  
<strong>\<tini2p\_gitlab\></strong> an incredible amount of refactoring, and router context impl  
<strong>\<tini2p\_gitlab\></strong> a lot of the early code that I wrote in the first months of the project has returned to bite me  
<strong>\<tini2p\_gitlab\></strong> I've spent a good amount of time correcting early design and implementation mistakes  
<strong>\<tini2p\_gitlab\></strong> work remains on the refactoring front, but it works  
<strong>\<tini2p\_gitlab\></strong> the real test will come with cross-implementation integration tests (post-alpha)  
<strong>\<tini2p\_gitlab\></strong> you can see my progress in the `context` branch: <https://gitlab.com/tini2p/tini2p/tree/context>  
<strong>\<tini2p\_gitlab\></strong> I have a bit more work to do cleaning things up, and making the context work without so much manual interaction  
<strong>\<tini2p\_gitlab\></strong> but tunnel messages, and end-to-end ECIES messaging works over localhost\!  
<strong>\<tini2p\_gitlab\></strong> you can see for yourself here: <https://gitlab.com/tini2p/tini2p/blob/context/tests/net\_tests/router/context.cc>  
<strong>\<tini2p\_gitlab\></strong> notably, this test shows an end-to-end ECIES session over inbound and outbound tunnels: <https://gitlab.com/tini2p/tini2p/blob/context/tests/net\_tests/router/context.cc#L402>  
<strong>\<tini2p\_gitlab\></strong> you can also see that I'm manually adding tunnels, selecting which router infos are used for tunnel hops, and manually creating the LeaseSet  
<strong>\<tini2p\_gitlab\></strong> so all that needs to be automated, and wrapped in functions inside the router context itself  
<strong>\<tini2p\_gitlab\></strong> I'll be working on that for the remainder of today, and pushing an alpha release candidate today or tomorrow  
<strong>\<tini2p\_gitlab\></strong> I'll leave the alpha candidate open for review for one week before merging into master  
<strong>\<tini2p\_gitlab\></strong> I've also updated my ECIES impl to \*mostly\* match what is in the current revision of [144](https://geti2p.net/spec/proposals/144-ecies-x25519-aead-ratchet)  
<strong>\<tini2p\_gitlab\></strong> where there are TODOs and otherwise murky content, I've filled in the gaps  
<strong>\<tini2p\_gitlab\></strong> the proposal is still highly in flux, and I will continue to update my impl until we reach a stable spec  
<strong>\<tini2p\_gitlab\></strong> over the last few meetings, zzz, orignal, the rest of the I2P devs, and I have been making a lot of progress  
<strong>\<tini2p\_gitlab\></strong> zzz is dedicating time to the next I2P release, and will return focus to 144 afterward  
<strong>\<tini2p\_gitlab\></strong> they have stated an estimate for end-of-year for a stable spec/rollout in Java I2P impl code  
<strong>\<tini2p\_gitlab\></strong> I'm hoping to also be ready with some client code (I2CP, SAMv3, Reseed) around that time to do full integration tests with Java I2P and i2pd  
<strong>\<tini2p\_gitlab\></strong> (ire too if str4d is ready :)  
<strong>\<tini2p\_gitlab\></strong> after alpha, I'll also be implementing ElGamal tunnel building, so that tini2p users will be able to build tunnels through existing Java I2P and i2pd routers  
<strong>\<tini2p\_gitlab\></strong> after that, Reseed  
<strong>\<tini2p\_gitlab\></strong> between now and next week, I'll be working on more bug fixes, the automation of router context stuffs, and trying to put together instructions for running tini2p routers over a docker testnet  
<strong>\<tini2p\_gitlab\></strong> docker testnet may wait until after alpha release, since I have net-tests that show full end-to-end communication (even if it is only over localhost)  
<strong>\<tini2p\_gitlab\></strong> that was 2: What's next  
<strong>\<tini2p\_gitlab\></strong> :0  
<strong>\<tini2p\_gitlab\></strong> 3: Comments / questions  
<strong>\<tini2p\_gitlab\></strong> then that leaves  
<strong>\<tini2p\_gitlab\></strong> 4: Next meeting  
<strong>\<tini2p\_gitlab\></strong> will be a short update next week for alpha release: 2019-10-10 18:00 UTC  
<strong>\<tini2p\_gitlab\></strong> thanks for reading  
<strong>\<tini2p\_gitlab\></strong> @tini2p\_gitlab kick juggles the gaffer like a hacky-sack
