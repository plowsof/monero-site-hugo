---
title: Logs for the MRL Meeting Held on 2020-01-08
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS to everyone  
<strong>\<almutasim\></strong> Hi.  
<strong>\<binaryFate\></strong> hi hi  
<strong>\<sarang\></strong> Let's start with ROUNDTABLE  
<strong>\<sarang\></strong> The preprint for Triptych, a new linkable ring signature construction that can be extended for use in transactions, is on the IACR archive  
<strong>\<sarang\></strong> Link: <https://eprint.iacr.org/2020/018>  
<strong>\<sarang\></strong> CoinTelegraph just released an article about it (but note there are some errors in the data presented there, that I'm told will be fixed)  
<strong>\<sarang\></strong> I plan to make an update on the size and time data, to properly account for batch verification and ensure fair comparison  
<strong>\<sarang\></strong> More work was done on the multi-index version of Triptych, fixing soundness in exchange for a separate proof relation that we need to show is equivalent to another proof relation  
<strong>\<sarang\></strong> This would allow even better performance  
<strong>\<sarang\></strong> I worked out an MPC for that version of Triptych as well, which would be useful for multisig  
<strong>\<sarang\></strong> And I'm presently working on some questions relating to Omniring math that I've brought up with that paper's authors  
<strong>\<sarang\></strong> Does anyone else wish to share interesting research work?  
<strong>\<almutasim\></strong> When the time is right, at a key juncture, we could have a press release on Triptych. Monero Outreach could support that. Maybe when it is established that it is going into a release.  
<strong>\<sarang\></strong> To be clear, there are no guarantees that Triptych, or any presently-known construction, is fit for deployment  
<strong>\<almutasim\></strong> Right.  
<strong>\<Isthmus\></strong> I've got some fingerprinting stuff, and n3ptune just completed a pretty cool network analysis  
<strong>\<sarang\></strong> Ooh  
<strong>\<sarang\></strong> Isthmus: what sort of data have you uncovered?  
<strong>\<Isthmus\></strong> Ah my fingerprinting notes are nothing new or exciting, just an idea that might make data presentation more intuitive. So, I tend to think about wallet fingerprinting in a kind of abstract way - every transaction sits at some corner of a hypercube in a high-dimensional space made of different heuristics yadda yaddaaa yadda  
<strong>\<Isthmus\></strong> So even though I work with sets of boolean features on the backend, wanted a good way to show results  
<strong>\<Isthmus\></strong> This is my first attempt: <https://mitchellpkt.github.io/fingerprint.html>  
<strong>\<sarang\></strong> What, you can't accurately present visualizations of high-dimensional hypercubes? =p  
<strong>\<Isthmus\></strong> llol  
<strong>\<Isthmus\></strong> This is somewhat by @suraeNoether adding human-interpretable output to the graph matching  
<strong>\<sarang\></strong> I like the idea of enumeration like that  
<strong>\<Isthmus\></strong> thanks\! It figure it's also an easy way to pass around data in a 2-column CSV chart, and researchers can do substring matching on portions that they find relevant to a given analysis  
<strong>\<suraeNoether\></strong> Ack sorry\! I'm here\! Time change got me unawares  
<strong>\<sarang\></strong> Isthmus: is there anything to share about the network analysis you mentioned?  
<strong>\<n3ptune\></strong> Re: questions on block propagation timing asked last month, I've collected and analyzed block receipt timing data from our global nodes recorded during the past 6 months  
<strong>\<sarang\></strong> Nice\!  
<strong>\<sarang\></strong> What conclusions?  
<strong>\<n3ptune\></strong> Isthmus has notes about interpretation and I have more to write but you can look at the graphs here <https://github.com/noncesense-research-lab/archival\_network/wiki/Block-propogation-time>  
<strong>\<Isthmus\></strong> This was RE a question that @moneromooo asked, right?  
<strong>\<Isthmus\></strong> Units are size in bytes and timestamps in milliseconds, right?  
<strong>\<suraeNoether\></strong> that was my question ^  
<strong>\<n3ptune\></strong> we used this formula where NRT is Node Received Timestamp: prop\_time\_lower\_bound(h) = MAX\[NRT(h,1), NRT(h,2), NRT(h,3)\] - MIN\[NRT(h,1), NRT(h,2), NRT(h,3)\]  
<strong>\<sarang\></strong> What are the changing indices there?  
<strong>\<sarang\></strong> Different nodes?  
<strong>\<sgp\_\></strong> hello  
<strong>\<n3ptune\></strong> yeah, that goes up to 3 but there are 4 nodes total  
<strong>\<sarang\></strong> got it  
<strong>\<suraeNoether\></strong> so block prop time is reliably at least 0.1s. interesting.  
<strong>\<Isthmus\></strong> Oh scatter heatmap is height from dark=old to light=new  
<strong>\<Isthmus\></strong> ^ color scale  
<strong>\<sarang\></strong> And those are the differences between the miner-reported timestamp and the node's wall clock upon receipt?  
<strong>\<Isthmus\></strong> Miner reported timestamps are not considered anywhere in this study  
<strong>\<Isthmus\></strong> But we did that elsewhere  
<strong>\<suraeNoether\></strong> hm then what is being measured for prop time?  
<strong>\<sarang\></strong> So these are blocks only passed between your nodes?  
<strong>\<sarang\></strong> Where you look at local times on send and receipt?  
<strong>\<Snipa\></strong> ^ Was going to ask that, as the min propogation time seems particularly low, as 100msec is quite low in our experience to cross the globe.  
<strong>\<sarang\></strong> Or better question: how is NRT computed  
<strong>\<n3ptune\></strong> it's the difference in timing between different nodes receiving the same blocks  
<strong>\<sarang\></strong> Ah, ok  
<strong>\<Isthmus\></strong> Yea, not passing between our nodes, but passing through our nodes  
<strong>\<n3ptune\></strong> NRT is recorded from the node system time when a block arrives  
<strong>\<sarang\></strong> Independent of the peer from which they receive  
<strong>\<sarang\></strong> (which would differ)  
<strong>\<sarang\></strong> Seeing the difference between miner-reported time (which could be inaccurate) and wall-clock receipt time would also be interesting  
<strong>\<suraeNoether\></strong> hmmmm  
<strong>\<endogenic\></strong> o/  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/brPsQyeU/image.png>  
<strong>\<Isthmus\></strong> @sarang just for you  
<strong>\<sarang\></strong> So what we're really seeing here is not propagation time directly, but variability in one layer of propagation time  
<strong>\<sarang\></strong> here = the initial plots, not this one  
<strong>\<Snipa\></strong> I'll have to check pool log data, as I might be able to give some extra data points if you're interested. We started to log the time in which a pool node finds a block, versus when that block is stored into our database, which means it's been processed by the local node, as we skip all monerod timings on the pool itself.  
<strong>\<suraeNoether\></strong> oooop  
<strong>\<suraeNoether\></strong> that's cool  
<strong>\<sarang\></strong> Very high times  
<strong>\<Isthmus\></strong> @Snipa very nice\!  
\< can you elaborate?  
<strong>\<suraeNoether\></strong> isthmus well it's how long it takes for the block to propagate from one of your nodes to another of your nodes; not time it takes to propagate from a miner to one of your nodes  
<strong>\<sarang\></strong> I mean that for the initial plots you showed, you can't directly interpret the time for the block to reach your node after it's mined  
<strong>\<sarang\></strong> suraeNoether: no  
<strong>\<suraeNoether\></strong> no?  
<strong>\<Isthmus\></strong> Yea, we very deliberately labeled all of the axes "prop time lower bound" for that reason  
<strong>\<Isthmus\></strong> Also, we could always posit that there is an old PC on dialup somewhere in Nebraska with a 4 minute prop time, but that's not meaningful  
<strong>\<sarang\></strong> suraeNoether: it's looking at the difference in receipt time, whichever path the block took in total propagation  
<strong>\<Snipa\></strong> Hrm, auctually, I can provide a data stream of our global block propgations, as every node has a local reporter that we can hook.  
<strong>\<Isthmus\></strong> @Snipa yes please\!  
<strong>\<suraeNoether\></strong> sarang that's true also  
<strong>\<n3ptune\></strong> that data would be awesome to work with  
<strong>\<Isthmus\></strong> I'll posit something that might be wrong:  
<strong>\<Isthmus\></strong> It's a hacky data science way of thinking -  
<strong>\<Snipa\></strong> Hit me up a bit later and we can discuss how to get it to you, and go over data formats.  
<strong>\<Isthmus\></strong> Shoot, I gotta get off the bus  
<strong>\<suraeNoether\></strong> isthmus: you have two sensors set up to detect propagation time. but you need 3 to triangulate, ala seismic detection of epicenters  
<strong>\<sarang\></strong> Don't leave us with that cliffhanger Isthmus\!  
<strong>\<suraeNoether\></strong> i'm on the edge of my seat  
<strong>\<suraeNoether\></strong> i spilled my tea  
<strong>\<suraeNoether\></strong> i'm so upset at isthmus right now i could just light myself on fire  
<strong>\<sarang\></strong> Stay on the bus Isthmus... it'll loop back around to your stop eventually  
<strong>\<sarang\></strong> In the meantime, any other interesting tidbits on this work?  
<strong>\<sarang\></strong> This is very interesting data  
<strong>\<suraeNoether\></strong> while we are waiting on Isthmus, I'll give my super-brief update: after some discussions with endo, my matching code has been made significantly more efficient, easy to understand, and easier to debug; i'll be making a push later today. my two categories of work today are re-reviewing CLSAG and working on matching  
<strong>\<n3ptune\></strong> that's it for now, we will update  
<strong>\<endogenic\></strong> his pseudocode now fits onto one sheet of notepad paper..  
<strong>\<suraeNoether\></strong> isthmus and i also technically had a conversation about writing up a proposal to encrypt and enforce all lock times, but we haven't gotten details worked out yet  
<strong>\<sarang\></strong> You mean using DLSAG-style commitments?  
<strong>\<sarang\></strong> We'd discussed it earlier in a meeting  
<strong>\<suraeNoether\></strong> yep, last meeting iirc. but i actually had a call with isthmus about it. i view this move as a very good boost in privacy in the sense that it covers up a source of non-randomness in the large data sets that isthmus likes to comb through.  
<strong>\<sarang\></strong> I can work out the size and time implications on that if you like  
<strong>\<suraeNoether\></strong> i'm not convinced it is worth the additional cost to our txn sizes, but we'll see how it shakes out  
<strong>\<sarang\></strong> Since it could be bundled into the existing bulletproof  
<strong>\<suraeNoether\></strong> ^ ah  
<strong>\<sarang\></strong> Yeah, size is not the issue here due to the logarithmic scaling  
<strong>\<suraeNoether\></strong> yeah, and verification times are speedy as a cheetah's balls  
<strong>\<suraeNoether\></strong> pardon me, this is a public meeting, i should be less vulgar. please accept my apologies.  
<strong>\<sarang\></strong> Right... there's a linear increase in verification time, but with the benefits of multiexp that's reduced a bit  
<strong>\<sarang\></strong> CoinTelegraph has updated their article: <https://cointelegraph.com/news/moneros-triptych-research-could-vastly-improve-its-anonymity>  
<strong>\<sarang\></strong> Thanks to the author for taking care of that so quickly  
<strong>\<almutasim\></strong> A press release could get more coverage, when and if it is desired.  
<strong>\<sarang\></strong> suraeNoether: interestingly, due to bulletproof padding, for many transactions there would be no size increase aside from the space taken up by the commitment data  
<strong>\<suraeNoether\></strong> good on cointelegraph  
<strong>\<sarang\></strong> (as opposed to a smaller plaintext representation)  
<strong>\<suraeNoether\></strong> sarang: could a similar approach be used to include a ciphertext of a message?  
<strong>\<suraeNoether\></strong> ie moneroMail  
<strong>\<Isthmus\></strong> Sorry somebody got in a fight with the bus driver right before my stop  
<strong>\<sarang\></strong> Not really... there's some spare space in bulletproofs that could hold something 1-2 proof elements of arbitrary data by controlling randomness (I'd need to check the details)  
<strong>\<Isthmus\></strong> Sigh San Francisco  
<strong>\<sarang\></strong> Welcome back Isthmus  
<strong>\<Isthmus\></strong> Ok lemme whiteboard some stuff 1 sex  
<strong>\<Isthmus\></strong> n3ptune: do you want to share the padding?  
<strong>\<Isthmus\></strong> In the blocks  
<strong>\<n3ptune\></strong> sure  
<strong>\<suraeNoether\></strong> sarang so enough for a key exchange but unlikely enough for a ciphertext?  
<strong>\<sarang\></strong> Well, you're limited by space  
<strong>\<n3ptune\></strong> Is there a known purpose for the null padding tag in tx\_extra?  
<strong>\<sarang\></strong> I don't remember if Poelstra and friends found 32 or 64 bytes of space  
<strong>\<sarang\></strong> n3ptune: good question for moneromooo et al.  
<strong>\<sarang\></strong> While we await Isthmus' continued update, anything else of interest to share?  
<strong>\<sarang\></strong> Or ACTION ITEMS, according to the agenda?  
<strong>\<suraeNoether\></strong> i want to provide final comments to you on clsag but i'm very unlikely to get that finished today  
<strong>\<suraeNoether\></strong> but it's on my mind for this week  
<strong>\<Isthmus\></strong> Back  
<strong>\<suraeNoether\></strong> Front  
<strong>\<sarang\></strong> Mine are to get CLSAG submitted (after review), to hopefully nail down this Omniring issue and pass it to the authors, work on a few EC curve library updates for proof of concept code, and get preprint stuff taken care of via monero-site MR  
<strong>\<sarang\></strong> Isthmus: please go ahead  
<strong>\<sarang\></strong> (oh, and update the Triptych preprint performance data with better clarity)  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/gAM3VbDV/1578508953.JPG>  
<strong>\<sarang\></strong> wat dis  
<strong>\<Isthmus\></strong> So let's say that we have 100 of n3ptune/NRL's archival nodes running  
<strong>\<Isthmus\></strong> If we have only 2 nodes, then our propagation envelope will have a lot of variability, be topology dependent (assume archival nodes don't connect to each other), and just t\_second - t\_first  
<strong>\<Isthmus\></strong> As we add a 3rd node, it has the possibility of increasing the measured prop time (since it could hear before or after) but can't decrease the prop time since it's max-min  
<strong>\<Isthmus\></strong> As we get up to 100 nodes, the variability will probably smooth out and we approach the true reasonable prop time (from miner to global nodes with broadband internet)  
<strong>\<sarang\></strong> Doesn't prop time depend on max/min among all nodes? So the third node could fall outside the envelope of the other two and affect the value?  
<strong>\<Isthmus\></strong> Yeah, that's the point  
<strong>\<sarang\></strong> OK, I must have misinterpreted  
<strong>\<sarang\></strong> Oh, can't \_decrease\_  
<strong>\<sarang\></strong> nvm  
<strong>\<Isthmus\></strong> Painting very broadly, when we adad the 3rd node there's a 2/3 chance that it'll fall outside the N=2 and increase the prop time, and a 1/3 chance that it'll be between the first 2 nodes.  
<strong>\<Isthmus\></strong> Sorry, I'm giving a kind of scattered description cuz I just realized this on the bus  
<strong>\<almutasim\></strong> Max-Min is a very sensitive metric, sensitive to outliers.  
<strong>\<Isthmus\></strong> Hmm lemme ponder on that  
<strong>\<Isthmus\></strong> Skipping over that for now  
<strong>\<Snipa\></strong> How're you pulling the time in which the block is received? Tweaked monerod/using it's logs or polling on the RPC interface to determine when it's auctually viably added to the box?  
<strong>\<Isthmus\></strong> That's a n3ptune question, they do all the DevOps and data engineering. All ended up in a SQL database by the time I got to it  
<strong>\<n3ptune\></strong> tweaked monerod  
<strong>\<Snipa\></strong> On P2P receive then?  
<strong>\<Isthmus\></strong> So for each height we have epsilon (green line) which our many-node approximation of global prop time  
<strong>\<n3ptune\></strong> you can also use monerod --block-notify, if you point that to a shell script that writes the timestamp  
<strong>\<Snipa\></strong> --block-notify waits until the block is committed, which is why I ask, because nodes that do not use NVMe have much slower propagation times in general, as you're waiting on disks to write.  
<strong>\<n3ptune\></strong> i like that better because then you can use the stock daemon. but we don't use that yet  
<strong>\<sarang\></strong> OK, so using the max-min metric, assuming relatively even node placement across the network topology?  
<strong>\<Isthmus\></strong> Yeah, though after @almutasim I'm considering a few other less sensitive metrics  
<strong>\<Isthmus\></strong> slap all those epsilons into a histogram, and that's the plot on the right.  
<strong>\<sarang\></strong> The outliers being nodes close to the miner and far from it, topologically  
<strong>\<Isthmus\></strong> Uhm, the outlier might be only 2 hops away but one of the hops is really slow  
<strong>\<n3ptune\></strong> P2P Receive: no it happens when it adds it to the blockchain, after it determines whether or not it's an alt block. this was because we had another original goal to capture alt blocks data. the daemon patch is shared here <https://github.com/neptuneresearch/monerod-archive>  
<strong>\<Isthmus\></strong> @sarang so it depends if topological distance definition is just the p2p connectivity graph or takes into account time between vertices  
<strong>\<sarang\></strong> right  
<strong>\<Isthmus\></strong> And that epsilon plot is basically what n3ptune shared earlier except instead of "max-min with 4 nodes" it is "asymptotic approximation of global prop time"  
<strong>\<Isthmus\></strong> ^talking about x-axis of histogram  
<strong>\<n3ptune\></strong> --block-notify waits until the block is committed \>\> oh then i guess this method of doing it in blockchain::add\_new\_block() at least occurs before block-notify would. but yes it isn't \*immediately\* on receive  
<strong>\<sarang\></strong> Since we're just about out of time, any last bits of information before adjourning (discussion can of course continue) for log purposes?  
<strong>\<Isthmus\></strong> Oh yea  
<strong>\<Isthmus\></strong> just a quick note that tx\_padding is used in the wild, but unclear why  
<strong>\<Isthmus\></strong> In the scatter plot showed earlier, the vertical bands from left to right are empty blocks and then N=1,2,3... transaactions  
<strong>\<sarang\></strong> That's a question for someone like moneromooo  
<strong>\<Isthmus\></strong> Of course there's variability in the horizontal width of the vertical bands due to transaction size differences, but the variability in coinbase-only blocks was straange  
<strong>\<Isthmus\></strong> <https://xmrchain.net/tx/acdf8eac41a7a76fd899e09640db34023abff66b3ae2c9ea86e49f19c0720af4>  
<strong>\<Snipa\></strong> Not really, coinbase only blocks are quite common due to pool design.  
<strong>\<Isthmus\></strong> No no, the size\*variability\* in coinbase-only was strange  
<strong>\<Isthmus\></strong> Turns out some (now fingerprinted) miners are using lots of null padding, check out the tx\_extra for this coinbase  
<strong>\<sarang\></strong> gadzooks  
<strong>\<Snipa\></strong> Not super surprising.  
<strong>\<Isthmus\></strong> Looks like bloat to me  
<strong>\<Isthmus\></strong> Bunch of blocks waste space with nulls in tx\_extra  
<strong>\<Snipa\></strong> Possibly, it's also something that can be requested by a pool.  
<strong>\<Snipa\></strong> As that's the block padding that we use for extra nonce storage space.  
<strong>\<Isthmus\></strong> "As that's the block padding that we use for extra nonce storage space." block nonce or transaction nonce? This is padding in the coinbase transaction  
<strong>\<Snipa\></strong> Oh sorry, txn, my bad.  
<strong>\<Isthmus\></strong> Do you know why some miners use the padding and some don't?  
<strong>\<Snipa\></strong> Lemme look through some of my decoding code I wrote for that.  
<strong>\<Isthmus\></strong> I'd been comparing:  
<strong>\<Isthmus\></strong> <https://xmrchain.net/search?value=1988283>  
<strong>\<Isthmus\></strong> and  
<strong>\<Isthmus\></strong> <https://xmrchain.net/search?value=1985042>  
<strong>\<Isthmus\></strong> Since they seem to be exactly the same besides different padding  
<strong>\<Isthmus\></strong> Anyways, thanks for letting me ramble and shifting meeting time  
<strong>\<Snipa\></strong> For quick reference: The block's CB TXN contains an "extras" section, which is requested from Monerod as the extra space in which arbitary data can be written. This data is used by pool implementations to implement the per-pool nonces as well as any custom nonce data used by more advanced techniques.  
<strong>\<Isthmus\></strong> "extra space in which arbitrary data can be written"  
<strong>\<Snipa\></strong> You can use this data in a number of ways, particularly with knowledge of pool design, as the two main pool implementations use this space similarly, but have different sizes based on various addon support.  
<strong>\<Isthmus\></strong> Ooh, what are the current use cases?  
<strong>\<Snipa\></strong> You also can identify what pool instances are submitting blocks, as pools use unique identifiers in particular bytes.  
<strong>\<Isthmus\></strong> (I have no knowledge of pool design)  
<strong>\<Snipa\></strong> <https://github.com/Snipa22/nodejs-pool/blob/master/lib/coins/xmr.js#L115>  
<strong>\<suraeNoether\></strong> For those of you who are interested in helping out with Monero Kon 2020 in Berlin, there is a meeting happening right now for prospective volunteers. This is research related, but otherwise off-topic, so I'm just dropping this here.  
<strong>\<Snipa\></strong> ^ is the implementation you'll find on pools that support the XNP extensions I wrote awhile ago.  
<strong>\<sarang\></strong> Yeah, we can formally adjourn the meeting, but carry on the conversation  
<strong>\<sarang\></strong> Thanks to everyone for attending
