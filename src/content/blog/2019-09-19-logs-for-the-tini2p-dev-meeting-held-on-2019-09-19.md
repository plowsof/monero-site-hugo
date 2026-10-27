---
title: Overview and Logs for the tini2p Dev Meeting Held on 2019-09-19
summary: Current project status, Roadmap, Meta issues, and miscellaneous
tags: [dev diaries, i2p, crypto]
author: el00ruobuob / oneiric
---

# Logs

<strong>\<tini2p\_gitlab\></strong> time of the meet  
<strong>\<tini2p\_gitlab\></strong> 0: Greetings  
<strong>\<tini2p\_gitlab\></strong> h  
<strong>\<tini2p\_gitlab\></strong> 1: What's been done  
<strong>\<tini2p\_gitlab\></strong> A lot  
<strong>\<tini2p\_gitlab\></strong> Finished tunnels impl, and merged into master  
<strong>\<tini2p\_gitlab\></strong> (with helpful review from @DavidBurkett)  
<strong>\<tini2p\_gitlab\></strong> I'm still used to being the only person working on the project, so have to habituate myself to a workflow that includes other people  
<strong>\<tini2p\_gitlab\></strong> started work on the router context (what ties all the pieces together)  
<strong>\<DavidBurkett\></strong> Don't change anything because of me. I'm slow and unreliable  
<strong>\<DavidBurkett\></strong> I'll catch up eventually, just keep doing what you're doing :)  
<strong>\<tini2p\_gitlab\></strong> in the process, came across some impl bugs in NTCP2 (fixed), updated NTCP2 to include a testnet v. mainnet netID, and started working on ECIES updates  
<strong>\<tini2p\_gitlab\></strong> no worries, I just meant that you're the first other than me to review my code :)  
<strong>\<DavidBurkett\></strong> Haha, got it  
<strong>\<tini2p\_gitlab\></strong> for the ECIES updates: there has been a lot of them  
<strong>\<tini2p\_gitlab\></strong> zzz pushed updates to move us to something much closer to standard Noise, and I love the changes  
<strong>\<tini2p\_gitlab\></strong> it's a bit of work to change my impl, but all the changes are for the better  
<strong>\<tini2p\_gitlab\></strong> the code is looking much cleaner now  
<strong>\<tini2p\_gitlab\></strong> the cryptographic guarantees are stronger and more clear as well, which is the bigger win imo  
<strong>\<DavidBurkett\></strong> :rocket: Do you have a link to zzz's updates?  
<strong>\<tini2p\_gitlab\></strong> you can follow my work in my context branch: <https://gitlab.com/tini2p/tini2p/tree/context>  
<strong>\<DavidBurkett\></strong> Ah perfect  
<strong>\<tini2p\_gitlab\></strong> yeah, zzz's updates are pushed to the main 144 proposal: <https://geti2p.net/spec/proposals/144-ecies-x25519-aead-ratchet>  
<strong>\<tini2p\_gitlab\></strong> we're still working out some kinks in the handshake, and will need to update the ratchet KDFs afterwards  
<strong>\<tini2p\_gitlab\></strong> we are getting \*\*much\*\* closer to finalizing the spec though, which is awesome  
<strong>\<tini2p\_gitlab\></strong> so, my impl may deviate from the spec a bit until we get everything figured out  
<strong>\<tini2p\_gitlab\></strong> we're trying to get as close to standard Noise as possible, while maintaining the necessary properties for ECIES-X25519 stated goals  
<strong>\<DavidBurkett\></strong> That's great news  
<strong>\<tini2p\_gitlab\></strong> definitely  
<strong>\<tini2p\_gitlab\></strong> :smile\_cat:  
<strong>\<tini2p\_gitlab\></strong> the downside to all that is I've spent a good amount of time refactoring, so don't have code that is ready for a release candidate  
<strong>\<tini2p\_gitlab\></strong> long-term it's for the best, in the short-term it's a slog to get to alpha release  
<strong>\<tini2p\_gitlab\></strong> which leads to the next item  
<strong>\<tini2p\_gitlab\></strong> 2: What's next  
<strong>\<tini2p\_gitlab\></strong> continue the refactors for ECIES-X25519  
<strong>\<tini2p\_gitlab\></strong> get something working for end-to-end crypto sessions, and work with zzz on fixing spec bugs (if/when they come up)  
<strong>\<tini2p\_gitlab\></strong> finish the context impl  
<strong>\<tini2p\_gitlab\></strong> create the docker testnet for local integration testing  
<strong>\<tini2p\_gitlab\></strong> idk how long the docker testnet will take, but I'm hoping something minimal will be fairly easy to setup  
<strong>\<tini2p\_gitlab\></strong> if it takes more than a day or two, I'll push an alpha release candidate without the testnet  
<strong>\<tini2p\_gitlab\></strong> the biggest hurdle I see for the testnet is populating the NetDB of the routers with the RouterInfos of the other routers in the testnet  
<strong>\<tini2p\_gitlab\></strong> I don't have reseed impled, so I'll have to do something manual  
<strong>\<zlatinb\></strong> you may find this useful: <http://zzz.i2p/topics/2756-testnet-with-lxc-instructions>  
<strong>\<tini2p\_gitlab\></strong> really hoping this is the last time I'll have to say this: pushing the alpha release date back another two weeks  
<strong>\<tini2p\_gitlab\></strong> awesome\! thank you @zlatinb :)  
<strong>\<zlatinb\></strong> also talk to "obscuratus" on Irc2P, he has a mixed i2pd/java i2p testnet, also with lxc  
<strong>\<tini2p\_gitlab\></strong> right on, I'm hoping to do it with docker for eventual windows support  
<strong>\<tini2p\_gitlab\></strong> right now, tini2p only builds on linux. will be working on cross-platform builds post-alpha  
<strong>\<tini2p\_gitlab\></strong> there's probably a lot of crossover in approach to lxc, so I appreciate the resources. will definitely be reaching out to obscuratus  
<strong>\<DavidBurkett\></strong> Builds on mac also  
<strong>\<DavidBurkett\></strong> But of course, that's based on linux  
<strong>\<DavidBurkett\></strong> I nearly had it building on windows, but I got frustrated and quit :)  
<strong>\<tini2p\_gitlab\></strong> haha wow, thanks for build testing  
<strong>\<tini2p\_gitlab\></strong> yeah, I imagine the windows experience is pretty hellish atm  
<strong>\<DavidBurkett\></strong> np, wasn't intentional. I'm the 0.1% of devs who prefers windows  
<strong>\<DavidBurkett\></strong> So I tried there first  
<strong>\<DavidBurkett\></strong> It wasn't quite as bad as you might think, but 1 of the dependencies was pissing me off lol  
<strong>\<tini2p\_gitlab\></strong> noise-c?  
<strong>\<DavidBurkett\></strong> Yes, that's the one  
<strong>\<tini2p\_gitlab\></strong> yup  
<strong>\<tini2p\_gitlab\></strong> that's a bear  
<strong>\<tini2p\_gitlab\></strong> I'll be moving all the noise stuff into the project proper, and remove the noise-c lib  
<strong>\<tini2p\_gitlab\></strong> it's a great reference, but making it cross-platform is such a pain  
<strong>\<DavidBurkett\></strong> Excellent. Let me know when you want me to try building again  
<strong>\<tini2p\_gitlab\></strong> will do, I appreciate the offer  
<strong>\<DavidBurkett\></strong> :thumbsup:  
<strong>\<tini2p\_gitlab\></strong> long-term I hope to contribute a CMake build system to noise-c  
<strong>\<tini2p\_gitlab\></strong> atm that's low priority though  
<strong>\<tini2p\_gitlab\></strong> that will be extremely time-consuming, but I want to give something back to the project  
<strong>\<tini2p\_gitlab\></strong> rweather did a lot to help me understand Noise :)  
<strong>\<tini2p\_gitlab\></strong> so, that's more-or-less what I'll be working on: router context, ECIES updates, some NetDB stuff, docker testnet  
<strong>\<tini2p\_gitlab\></strong> 3: Questions/comments  
<strong>\<tini2p\_gitlab\></strong> alright, so that's the meeting  
<strong>\<tini2p\_gitlab\></strong> will do my best to get a release candidate out by next Thursday, and alpha release the following week  
<strong>\<DavidBurkett\></strong> Looking forward to it  
<strong>\<tini2p\_gitlab\></strong> :+1:  
<strong>\<tini2p\_gitlab\></strong> 4: Next meeting  
<strong>\<tini2p\_gitlab\></strong> 2019-10-03 18:00 UTC  
<strong>\<tini2p\_gitlab\></strong> holy shit, we're already almost in October  
<strong>\<tini2p\_gitlab\></strong> thanks all for attending  
<strong>\<tini2p\_gitlab\></strong> @tini2p\_gitlab twirls the gavel
