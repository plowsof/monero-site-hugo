---
title: Overview and Logs for the tini2p Dev Meeting Held on 2019-09-05
summary: Current project status, Roadmap, Meta issues, and miscellaneous
tags: [dev diaries, i2p, crypto]
author: el00ruobuob / oneiric
---

# Logs

<strong>\<tini2p\_gitlab\></strong> meeting time\!  
<strong>\<tini2p\_gitlab\></strong> 0: Greetings  
<strong>\<tini2p\_gitlab\></strong> l  
<strong>\<DavidBurkett\></strong> :wave:  
<strong>\<tini2p\_gitlab\></strong> :)  
<strong>\<tini2p\_gitlab\></strong> 1: What's been done  
<strong>\<tini2p\_gitlab\></strong> opened merge request for tunnels implementation: <https://gitlab.com/tini2p/tini2p/merge\_requests/15>  
<strong>\<tini2p\_gitlab\></strong> it's a large amount of work (around a month's worth), so I'm going to leave it up for a bit (few days)  
<strong>\<tini2p\_gitlab\></strong> going to take a day away from that code, and come back to it for manual review  
<strong>\<DavidBurkett\></strong> Awesome\! Is there anyone from i2p actively reviewing it? If not, I'll review with what little knowledge I have  
<strong>\<tini2p\_gitlab\></strong> remember how I said "hopefully, no more major refactors", well so much for that. I overlooked some parts of OutboundEndpoint and InboundGateway processing, and had to refactor how I extract I2NP fragments from tunnel messages  
<strong>\<tini2p\_gitlab\></strong> @DavidBurkett many thanks\! I'm the only active reviewer, so any input from you is very welcome  
<strong>\<tini2p\_gitlab\></strong> fresh eyes are always helpful  
<strong>\<DavidBurkett\></strong> :thumbsup: I'll take a look  
<strong>\<tini2p\_gitlab\></strong> there are still some aspects of peer selection that remain, mostly around restrictions of peers from the same /16 IPv4, and any given peer only participating in \~33% of active tunnels  
<strong>\<tini2p\_gitlab\></strong> not sure what layer of abstraction I should enforce those restrictions. right now, those restrictions make sense at the RouterContext layer for my impl, but TBD  
<strong>\<tini2p\_gitlab\></strong> the RouterContext will ultimately be pulling peers from NetDB, and feeding them into the PoolManager  
<strong>\<tini2p\_gitlab\></strong> so the work in that PR represents what I've been working since last meeting  
<strong>\<tini2p\_gitlab\></strong> a lot of time was spent on peer profiling and tunnel testing  
<strong>\<tini2p\_gitlab\></strong> and the refactors for the OutboundEndpoint sending a TunnelGateway message when the delivery is to another tunnel  
<strong>\<tini2p\_gitlab\></strong> from the existing I2P docs, it's not very clear when the different tunnel delivery types are used (Local, Router, Tunnel)  
<strong>\<tini2p\_gitlab\></strong> it took me implementing the things, and thinking about how the pieces fit together to really make sense of it  
<strong>\<tini2p\_gitlab\></strong> basically, afaiu, Local is used by the InboundGateway to tell the InboundEndpoint, "this message is for you"  
<strong>\<tini2p\_gitlab\></strong> Router is used by the OutboundGateway to tell the OutboundEndpoint (and maybe IBGW to IBEP) that the I2NP message should be directly delivered to a router  
<strong>\<tini2p\_gitlab\></strong> e.g. for DatabaseStore and DatabaseLookup messages  
<strong>\<tini2p\_gitlab\></strong> Tunnel delivery is used by the OutboundGateway to tell the OutboundEndpoint (and maybe IBGW to IBEP) that the I2NP message should be delivered to the InboundGateway of another tunnel  
<strong>\<tini2p\_gitlab\></strong> Router and Tunnel don't make sense to me for inbound tunnels, unless some form of chaining is used. not clear that it ever is from the specs  
<strong>\<tini2p\_gitlab\></strong> for example, if Alice sends an I2NP message through an outbound tunnel to the IBGW of another tunnel (with some indicator for chaining), and that IBGW uses Router or Tunnel delivery to tell the IBEP to deliver the I2NP message to the IBGW of yet another tunnel  
<strong>\<tini2p\_gitlab\></strong> maybe that exists, but I've implemented IBGW only using Local delivery to send I2NP messages to the IBEP  
<strong>\<tini2p\_gitlab\></strong> Local delivery is never used for outbound tunnels  
<strong>\<tini2p\_gitlab\></strong> anyway, figuring all that out took a bit of time, and I may send spec diffs upstream to clarify the use of the different delivery types  
<strong>\<tini2p\_gitlab\></strong> 2: What's next  
<strong>\<tini2p\_gitlab\></strong> RouterContext  
<strong>\<tini2p\_gitlab\></strong> and associated classes  
<strong>\<tini2p\_gitlab\></strong> this set of classes will be the main brains tying everything together  
<strong>\<tini2p\_gitlab\></strong> RouterContext will use the transport (NTCP2) to talk directly to other routers  
<strong>\<tini2p\_gitlab\></strong> it will use an I2NP handler to either pass messages to the NetDB or Tunnel PoolManager for further processing  
<strong>\<tini2p\_gitlab\></strong> similarly, resulting messages from NetDB and Tunnel processing will be returned to the RouterContext, and sent back out over NTCP2 to the appropriate router  
<strong>\<tini2p\_gitlab\></strong> the RouterContext will also be the main owner of the router's RouterInfo  
<strong>\<tini2p\_gitlab\></strong> LeaseSets for local InboundTunnels will also be compiled by the RouterContext, and stored in the NetDB  
<strong>\<tini2p\_gitlab\></strong> setting a goal for myself to have the RouterContext finished (in a minimally working sense) by next Thursday (2019-09-12)  
<strong>\<tini2p\_gitlab\></strong> with RouterContext finished/merged, I will tag a release candidate  
<strong>\<tini2p\_gitlab\></strong> I will be implementing a Docker/container test network for integration/end-to-end testing, to ensure all the pieces work together  
<strong>\<tini2p\_gitlab\></strong> I will also make changes to match the latest updates to ECIES-X25519, posted by zzz this past weekend  
<strong>\<tini2p\_gitlab\></strong> ECIES-X25519 changes will also go into the alpha release candidate  
<strong>\<tini2p\_gitlab\></strong> with RouterContext and ECIES-X25519 changes in place, tini2p will have an internally consistent implementation of I2P  
<strong>\<tini2p\_gitlab\></strong> and I will tag the alpha release a week after the release candidate  
<strong>\<tini2p\_gitlab\></strong> after alpha release, I will focus on ElGamal tunnel building, and integration tests with Java I2P and i2pd  
<strong>\<tini2p\_gitlab\></strong> end-to-end sessions will still be tini2p-to-tini2p, but tunnel building should be possible through Java I2P and i2pd  
<strong>\<tini2p\_gitlab\></strong> the Docker/container setup should be a nice testbed for inter-implementation testing, so hopefully it will be useful for other implementations as well  
<strong>\<tini2p\_gitlab\></strong> TBD  
<strong>\<tini2p\_gitlab\></strong> post-alpha release will also get some (a huge amount) of fuzz tests  
<strong>\<tini2p\_gitlab\></strong> basically every class with a `deserialize`method or buffer input interface, will be getting a fuzz driver attached to it  
<strong>\<tini2p\_gitlab\></strong> I may also be taking a small break from tini2p post-alpha release to preemptively prevent burnout  
<strong>\<tini2p\_gitlab\></strong> these past nine months have been basically coding tini2p everyday, often 10-12+ hours a day  
<strong>\<tini2p\_gitlab\></strong> 3: Questions/comments  
<strong>\<DavidBurkett\></strong> This project structure is really clean, and code easy to follow. Working on building now. You're doing great work  
<strong>\<tini2p\_gitlab\></strong> aww :3 thanks @DavidBurkett that means a lot, very kind  
<strong>\<tini2p\_gitlab\></strong> still needs a lot of work to be production-ready, but I'm doing my best to code well  
<strong>\<tini2p\_gitlab\></strong> some of the structure is heavily influenced by portions of Java I2P, i2pd and ire. there are some really good bits in those codebases  
<strong>\<DavidBurkett\></strong> Well I'm just talking your cmake files, your handling of dependencies, etc. Very clean  
<strong>\<DavidBurkett\></strong> And I've seen i2pd. This is night and day better (although i2pd is pretty easy to work with)  
<strong>\<DavidBurkett\></strong> \[edit\] And I've seen i2pd. This is night and day better (although i2pd is also pretty easy to work with)  
<strong>\<tini2p\_gitlab\></strong> i2pd has very different project goals and design. i2pd aims to be a one-stop-shop router, tini2p aims for use as an I2P library by other projects  
<strong>\<DavidBurkett\></strong> Ah, that makes sense  
<strong>\<DavidBurkett\></strong> I assumed i2pd was also meant to be used as a library  
<strong>\<tini2p\_gitlab\></strong> the CMake and dependencies took influence from Kovri (and by extension i2pd)  
<strong>\<tini2p\_gitlab\></strong> i2pd can also be used as a library  
<strong>\<tini2p\_gitlab\></strong> what I mean is that i2pd contains an HTTP server, router console, bundled client, all-in-one. somewhat similar to Java I2P, though with less apps bundled in  
<strong>\<DavidBurkett\></strong> :thumbsup: Understood  
<strong>\<tini2p\_gitlab\></strong> tini2p moves away from that singleton design, into something highly modular  
<strong>\<tini2p\_gitlab\></strong> a future goal is to split tini2p up further, having common structures be its own repo, with separate core and client libs  
<strong>\<DavidBurkett\></strong> Makes sense. Yea, I pulled i2pd into Grin++ at one point, but I had to decouple a bunch of things to be able to just pull in what I want. It wasn't a straightforward task  
<strong>\<tini2p\_gitlab\></strong> that's somewhat far down the line though, but it would support stuff like pluggable end-to-end and signing crypto  
<strong>\<DavidBurkett\></strong> That's awesome, you'll get there for sure.  
<strong>\<tini2p\_gitlab\></strong> :) thank you  
<strong>\<tini2p\_gitlab\></strong> alright, think that's about all for this meeting. unless you have something else @DavidBurkett?  
<strong>\<DavidBurkett\></strong> Nothing from me  
<strong>\<tini2p\_gitlab\></strong> for sure  
<strong>\<tini2p\_gitlab\></strong> 4: Next meeting  
<strong>\<tini2p\_gitlab\></strong> 2019-09-19 18:00 UTC  
<strong>\<tini2p\_gitlab\></strong> thanks all for attending (that means you @DavidBurkett ;)  
<strong>\<DavidBurkett\></strong> :smile:  
<strong>\<tini2p\_gitlab\></strong> @tini2p\_gitlab stares intently at the gaffer, wondering if it feels
