---
title: Logs for the Hardware Firmware Meeting Held on 2018-01-12
summary: Discussion of the firmware for the dedicated hardware wallet and a discussion of Ledger's approach
tags: [dev diaries, crypto]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<i-a\></strong> Hello all, it is time for our firmware meeting to start. I am not sure if it is not too early to have a meeting like this, but let’s see.  
<strong>\<i-a\></strong> Strange, there were so many people saying they have questions about code and now nobody is here:) So I will give a quick update on our project:  
<strong>\<i-a\></strong> Ok here is the quick update: USB communications is working, alse we can generate wallet by using internal random number generator (thanks god for m2049r, nice job)  
<strong>\<i-a\></strong> Maybe you have some recommendation how to move from here? My questions could look silly, but thats because I am personally just learning monero.  
<strong>\<m2049r\[m\]\></strong> :)  
<strong>\<i-a\></strong> On the other hand, there are other people working and maybe my questions could help also to them.  
<strong>\<m2049r\[m\]\></strong> is there anyone here who is actually taking part in this meeting besides us two?  
<strong>\<hotoatmeal\></strong> is the plan to use the same strategy that the ledger guy came up with, where private keys are sent (encrypted) from the device to the wallet?  
<strong>\<qqitty\></strong> CS noob looking to study xmr code this weekend. any design books/web guides to read like Huang’s dissecting BTC?  
<strong>\<hotoatmeal\></strong> m2049r\[m\]: I’m mostly passively participating, until that question  
<strong>\<dEBRUYNE\></strong> m2049r\[m\]: Most people will probably just read until they want to say something :p  
<strong>\<i-a\></strong> hotoatmeal: We are here to speak about the plan.. I think if we want to do all the signing stuff in the device, we would need more memory.In case we need more memory, we will just setup a new device with bigger mcu.  
<strong>\<m2049r\[m\]\></strong> i would like an implementation where the keys never ever leave the device - we have to see if thats possible with the hardware constraints we have.  
<strong>\<hotoatmeal\></strong> I would like that too\!  
<strong>\<i-a\></strong> It is still organic and you have perfect opportunity to bend the way how it is being developped:)  
<strong>\<i-a\></strong> Me too.  
<strong>\<m2049r\[m\]\></strong> there may be multiple implementations, with different roads to success.  
<strong>\<hotoatmeal\></strong> I don’t yet understand how to find transaction outputs without revealing the view key  
<strong>\<m2049r\[m\]\></strong> without having studies the code i think it should be possible to hook into the code and have the device take over when keys are in play.  
<strong>\<hotoatmeal\></strong> if that’s not possible, then the entire blockchain would have to be fed through the device over usb… might be quite slow.  
<strong>\<m2049r\[m\]\></strong> (into the wallet client code)  
<strong>\<m2049r\[m\]\></strong> yes - but thats probably not a good idea - and were back to sending the keys to the client  
<strong>\<hotoatmeal\></strong> yeah :/  
<strong>\<hotoatmeal\></strong> too bad homeomorphic encryption systems are so slow  
<strong>\<hotoatmeal\></strong> otherwise you could trustlessly give the client an encrypted version of your view key, let it scan the blockchain for you, and provide the relevant txo’s (also encrypted)  
<strong>\<hotoatmeal\></strong> and have the device decrypt the computed result  
<strong>\<m2049r\[m\]\></strong> i need to read up on how exactly the keys are used in the clients - any specific hint on where to get started?  
<strong>\<hotoatmeal\></strong> cryptonote paper is where I got started  
<strong>\<hotoatmeal\></strong> also looking at the ledger guy’s patch  
<strong>\<m2049r\[m\]\></strong> i am not sure the communication to &amp; from the device needs to be encrypted - are you worried about usb sniffers?  
<strong>\<jbdatko\></strong> hotoatmeal, can you link that patch?  
<strong>\<m2049r\[m\]\></strong> and if yes, whats the attack?  
<strong>\<hotoatmeal\></strong> so two separate things, both with different reasons for encryption  
<strong>\<qqitty2\></strong> Thanks @hotoatmeal. I’ll go dive into the cryptonote WP  
<strong>\<m2049r\[m\]\></strong> cryptonote paper seems mostly vague  
<strong>\<hotoatmeal\></strong> ledger guy’s patch encrypts the communication because it’s transferring raw key data  
<strong>\<hotoatmeal\></strong> should be a no-brainer that that should be encrypted  
<strong>\<luigi1111\></strong> Paper is pretty clear unless you want implementation specifics  
<strong>\<m2049r\[m\]\></strong> heh yes  
<strong>\<hotoatmeal\></strong> this other thing about H-E, is a separate idea, and that’s to allow someone else to scan the blockchain on your behalf, without revealing your view key to them (losing your privacy)  
<strong>\<m2049r\[m\]\></strong> paper is clear - i meant vague in the sense of implementation specifics  
<strong>\<m2049r\[m\]\></strong> H-E?  
<strong>\<luigi1111\></strong> I think you pretty much have to have client do the scanning  
<strong>\<luigi1111\></strong> Not the hw  
<strong>\<hotoatmeal\></strong> homeomorphic encryption  
<strong>\<dEBRUYNE\></strong> jbdatko: It’s under open PRs on the monero repository  
<strong>\<luigi1111\></strong> Unless you have some hw acceleration it’s just too slow  
<strong>\<i-a\></strong> luigi1111: yes but is there a way how to do it?  
<strong>\<luigi1111\></strong> How to do which  
<strong>\<hotoatmeal\></strong> i.e. someone else performs math on encrypted values that they can’t see, and returns the result to you  
<strong>\<i-a\></strong> how to let PC scan the whole blockchain and prepare outgoing tx in a way, that the are sent to device just for signing.  
<strong>\<luigi1111\></strong> Sure  
<strong>\<luigi1111\></strong> The cold wallet signing basically does this already  
<strong>\<hotoatmeal\></strong> the problem is that H-E implementations of crypto algos are really really really slow  
<strong>\<hotoatmeal\></strong> like hours for a single round of AES  
<strong>\<luigi1111\></strong> That’d probably be slower than the device doing the scanning ^^  
<strong>\<luigi1111\></strong> :)  
<strong>\<hotoatmeal\></strong> yeah  
<strong>\<i-a\></strong> :(  
<strong>\<hotoatmeal\></strong> but in terms of mathematical purity / elegance… I really want that kind of solution to work :)  
<strong>\<hotoatmeal\></strong> jbdatko: <https://github.com/monero-project/monero/pull/3095>  
<strong>\<i-a\></strong> Ok, another question: If device did he whole scanning. How much memory we need on the device? I think that downlink from peers is usually slower than USB, so limitations is more in memory requirement at the device.  
<strong>\<m2049r\[m\]\></strong> how big of a problem would it be to reveal the viewkey to the client?  
<strong>\<luigi1111\></strong> Not memory  
<strong>\<luigi1111\></strong> Cpu  
<strong>\<luigi1111\></strong> I don’t think it’s an issue  
<strong>\<luigi1111\></strong> I mean it isn’t perfect  
<strong>\<luigi1111\></strong> But it has the benefit of being workable  
<strong>\<hotoatmeal\></strong> revealing to the client just means that you can’t have a non-daemon client  
<strong>\<luigi1111\></strong> Sure you can  
<strong>\<i-a\></strong> yes but it is fine for now I think.  
<strong>\<luigi1111\></strong> You could have a remote node  
<strong>\<hotoatmeal\></strong> well, yeah  
<strong>\<luigi1111\></strong> All the way to mymonero  
<strong>\<m2049r\[m\]\></strong> the client wallet cache - is that encrypted?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<m2049r\[m\]\></strong> thought so - so the device would need to do that as well.  
<strong>\<hotoatmeal\></strong> is it possible to give the client an image of the view key, and then have it search the blockchain for some subset of txo’s that /might/ match (as a coarse filter)?  
<strong>\<endogenic\></strong> vtnerd  
<strong>\<jbdatko\></strong> hotoatmeal, thank you  
<strong>\<hotoatmeal\></strong> (reducing the amount of work the device has to do, but not giving up the full key data?)  
<strong>\<m2049r\[m\]\></strong> how would that work?  
<strong>\<jbdatko\></strong> AES accelerators on MCU are pretty good now, so depending on the MCU it might not be completely horrible (sorry I’m jumping in w/o knowing the full context)  
<strong>\<endogenic\></strong> hotoatmeal: mrl has been workin on this problem for some time  
<strong>\<hotoatmeal\></strong> endogenic: anything I’m saying known not to be worth pursuing? (by proofs that it doesn’t work, or somesuch)  
<strong>\<m2049r\[m\]\></strong> we have space for secure elements on the board - things which can do aes and other things in hardware.  
<strong>\<luigi1111w\></strong> you need ed25519 acceleration  
<strong>\<luigi1111w\></strong> which I doubt exists  
<strong>\<m2049r\[m\]\></strong> yeah, except that.  
<strong>\<hotoatmeal\></strong> heh. now it needs an fpga  
<strong>\<luigi1111w\></strong> I don’t really see any way around it  
<strong>\<luigi1111w\></strong> mymonero as a hw client would actually be quite desirable  
<strong>\<luigi1111w\></strong> and quite an upgrade  
<strong>\<luigi1111w\></strong> well it all depends on perspective :)  
<strong>\<endogenic\></strong> :)  
<strong>\<luigi1111w\></strong> the most secure/private arrangement would be user owned daemon -\> wallet/client -\> hw  
<strong>\<luigi1111w\></strong> but you can delegate the first two for privacy loss  
<strong>\<luigi1111w\></strong> well the first one isn’t really privacy loss  
<strong>\<i-a\></strong> our nordic semiconductor candidate has ed25519 hw block, but we still didnt get them.  
<strong>\<luigi1111w\></strong> or a different type or of privacy  
<strong>\<luigi1111w\></strong> i-a that’s interesting  
<strong>\<luigi1111w\></strong> I’d be curious to see perf numbers  
<strong>\<m2049r\[m\]\></strong> i-a but thats with an nda so we cant be open source, no?  
<strong>\<luigi1111w\></strong> for some usable ed25519 operation  
<strong>\<i-a\></strong> luigi1111w: nRF52840, it has secure crypto cell or something like that.  
<strong>\<i-a\></strong> Of course there are other problems, like a non open design and so on.  
<strong>\<msvb-mob\></strong> cryptocell is available without nda.  
<strong>\<luigi1111w\></strong> I mean something like signatures/sec  
<strong>\<i-a\></strong> another question is if this cryptocell ed25519 is fast enough to be usable.  
<strong>\<luigi1111w\></strong> that was my only question :)  
<strong>\<i-a\></strong> Unfortunately I dont know now. But I will try to find out. It seems like as-fast-as-possibe ed25529 od device is a must.  
<strong>\<hotoatmeal\></strong> do you have a ballpark for how fast it would have to be to be usable?  
<strong>\<msvb-mob\></strong> cec1702 has the cuve too.  
<strong>\<i-a\></strong> msvb-mob: nice, can we somehow determine their performance?  
<strong>\<m2049r\[m\]\></strong> they sortof claim its 10x a software solution but dont show numbers  
<strong>\<luigi1111w\></strong> software solution on that power of hw?  
<strong>\<luigi1111w\></strong> IDK, something similar to an older cpu  
<strong>\<msvb-mob\></strong> i-a: I don’t know how to measure performance without testing the devices on real hardware, unfortunately.  
<strong>\<i-a\></strong> <https://www.microchip.com/wwwproducts/en/CEC1702>  
<strong>\<i-a\></strong> this is it ^  
<strong>\<m2049r\[m\]\></strong> thats the question luigi - its blabla  
<strong>\<m2049r\[m\]\></strong> can we GET real hardware?  
<strong>\<luigi1111w\></strong> :)  
<strong>\<i-a\></strong> msvb-mob: hmm:( are we going to have cec1702 to do some testing?  
<strong>\<luigi1111w\></strong> I think it would be really cool if such a device could be made  
<strong>\<luigi1111w\></strong> but I’m skeptical  
<strong>\<msvb-mob\></strong> m2049r\[m\]: I can send you a nRF52840-DK if you want.  
<strong>\<luigi1111w\></strong> we know the viewkey delegation works, at least  
<strong>\<msvb-mob\></strong> i-a: The nRF is easy (there’s a devkit for that) but to test the CEC1702 we must make the boards ourselves first.  
<strong>\<luigi1111w\></strong> (mymonero and openmonero both use the exact same idea already)  
<strong>\<msvb-mob\></strong> I think the MCUs are already in my lab.  
<strong>\<i-a\></strong> msvb-mob: that is not a big deal, if you know the are comming, i can send you a board asap.  
<strong>\<i-a\></strong> (lets say gerbers on monday/tuesday)  
<strong>\<i-a\></strong> msvb-mob: what about nda on this cec1702? Or do they have some problem?  
<strong>\<msvb-mob\></strong> The CEC1702 is not NDA encumbered.  
<strong>\<i-a\></strong> perfect candidate -\_-  
<strong>\<msvb-mob\></strong> Yes, I think so too.  
<strong>\<m2049r\[m\]\></strong> the CEC1702 &amp; the nRF52840 would replace our MCU?  
<strong>\<i-a\></strong> m2049r\[m\]: I think yes, because our mcu is lacking ed25519  
<strong>\<msvb-mob\></strong> m2049r\[m\]: They are both Cortex-M4 MCUs so they could do so. If they aren’t large enough to contain transactions in memory or code in program storage we could use them as coprocessors probably.  
<strong>\<msvb-mob\></strong> Would be a bit weird.  
<strong>\<m2049r\[m\]\></strong> we have to see what they mean by ed25519. do we need just signing &amp; verifying or do we also need curve arithmetic luigi1111w  
<strong>\<luigi1111w\></strong> signing and verifying sorta-mostly-ish include all the operations needed  
<strong>\<luigi1111w\></strong> I guess that’s not really true  
<strong>\<luigi1111w\></strong> but the operations that need accelerated would be, mostly  
<strong>\<m2049r\[m\]\></strong> the data sheets says:  
<strong>\<m2049r\[m\]\></strong> Elliptic Curve point multiply with Curve25519  
<strong>\<m2049r\[m\]\></strong> The Edwards-curve Digital Signature Algorithm (EdDSA), using Curve25519  
<strong>\<m2049r\[m\]\></strong> (CEC1702)  
<strong>\<iDunk\></strong> ed25519 \!= Curve25519.  
<strong>\<i-a\></strong> nRF does both i think  
<strong>\<i-a\></strong> yes  
<strong>\<i-a\></strong> but cec1702 doesn’t have ed25519:( or I cannot find it in datasheet.  
<strong>\<m2049r\[m\]\></strong> the nrf can create keys, sign &amp; verify. “The generation is performed using EC Edwards ed25519 algorithm.”  
<strong>\<i-a\></strong> cec1702 has only Curve25519  
<strong>\<luigi1111w\></strong> if they are going off of nacl or similar they have both  
<strong>\<luigi1111w\></strong> the signing is ed  
<strong>\<luigi1111w\></strong> and the box stuff is curve255  
<strong>\<msvb-mob\></strong> i-a: No ECDSA on CEC1702? I don’t have the documents with me now.  
<strong>\<i-a\></strong> ok so to be clear:  
<strong>\<i-a\></strong> The Elliptic Curve Digital Signature Algorit  
<strong>\<i-a\></strong> hm (ECDSA), using all supported NIST curves  
<strong>\<i-a\></strong> he Edwards-curve Digital Signatur  
<strong>\<i-a\></strong> e Algorithm (EdDSA), using Curve25519  
<strong>\<luigi1111w\></strong> that could be naming issues though :)  
<strong>\<i-a\></strong> maybe ed25519 is hidden somewhere, but it isn explicitly mentioned, Curve25519 is mentioned.  
<strong>\<i-a\></strong> \*isnt  
<strong>\<luigi1111w\></strong> yeah they are often bundled together  
<strong>\<m2049r\[m\]\></strong> so you are saying we need new hardware in any case?  
<strong>\<luigi1111w\></strong> to attempt to “do everyone on device”, yes (and I’m doubtful it’s possible)  
<strong>\<luigi1111w\></strong> to do a client-delegated arrangement, no  
<strong>\<hotoatmeal\></strong> these slides say they can do \~1400 ECDH’s /s on a cortex A8: <https://cr.yp.to/talks/2012.11.29/slides.pdf>  
<strong>\<msvb-mob\></strong> i-a: The ED25519 API is on pages 60-61 of the CEC/MEC Family Devices ROM API Users Guide.  
<strong>\<i-a\></strong> msvb-mob: thank you,)  
<strong>\<msvb-mob\></strong> For example ed25519\_valid\_sig (validate signature) is a function.  
<strong>\<hotoatmeal\></strong> and Ed25519 was only a bit slower  
<strong>\<hotoatmeal\></strong> what’s the rough size of the blockchain, counted in txo’s?  
<strong>\<luigi1111w\></strong> total size isn’t that useful  
<strong>\<luigi1111w\></strong> size over past month much more so  
<strong>\<hotoatmeal\></strong> growth rate too  
<strong>\<luigi1111w\></strong> yeah with some assumed groth  
<strong>\<luigi1111w\></strong> growth  
<strong>\<luigi1111w\></strong> 200k txs last month  
<strong>\<luigi1111w\></strong> so maybe 450k outputs  
<strong>\<luigi1111w\></strong> double that at least gets you 1mi/mo  
<strong>\<luigi1111w\></strong> checking an output is something like 2x ECDH  
<strong>\<hotoatmeal\></strong> so it’ll get slower by 20 mins, every month  
<strong>\<hotoatmeal\></strong> ouch  
<strong>\<luigi1111w\></strong> if you don’t use it  
<strong>\<luigi1111w\></strong> but yeah  
<strong>\<hotoatmeal\></strong> (assuming you need to re-scan the entire chain each time… but maybe that can be cached)  
<strong>\<luigi1111w\></strong> there would be quite some catchup time  
<strong>\<i-a\></strong> not sure if relevant, but this could be ECDSA performance on CEC device: <https://imgur.com/a/WQKqp> ?  
<strong>\<luigi1111w\></strong> if you leave it unplugged for some time  
<strong>\<luigi1111w\></strong> oh  
<strong>\<luigi1111w\></strong> I would sure assume you cache  
<strong>\<luigi1111w\></strong> if you don’t it  
<strong>\<luigi1111w\></strong> it’s pretty unworkable  
<strong>\<hotoatmeal\></strong> yeah  
<strong>\<luigi1111w\></strong> you’d have to leave it plugged in a few hours before you could spend each time :)  
<strong>\<hotoatmeal\></strong> the worst case of initializing a new device though is pretty bad  
<strong>\<hotoatmeal\></strong> though I guess you could just sweep everything to it, and ignore all of the chain that happened before then  
<strong>\<luigi1111w\></strong> restored device  
<strong>\<luigi1111w\></strong> new device has no txs  
<strong>\<hotoatmeal\></strong> right  
<strong>\<hotoatmeal\></strong> at least the restore point is something you can make note of, encrypt, and then store like any other backup  
<strong>\<m2049r\[m\]\></strong> are you suggesting we keep the chain/cache on the device?  
<strong>\<luigi1111w\></strong> no  
<strong>\<luigi1111w\></strong> definitely not the chain  
<strong>\<luigi1111w\></strong> I’m still skeptical it’s workable at all, just exploring the idea  
<strong>\<m2049r\[m\]\></strong> gottit  
<strong>\<hotoatmeal\></strong> do bulletproofs change the costs here?  
<strong>\<hotoatmeal\></strong> s.do.will.  
<strong>\<m2049r\[m\]\></strong> do we have constraints about how big the device may be?  
<strong>\<endogenic\></strong> yes  
<strong>\<luigi1111w\></strong> hotoatmeal no  
<strong>\<endogenic\></strong> :P  
<strong>\<luigi1111w\></strong> m2049r\[m\] just tote a computer around  
<strong>\<luigi1111w\></strong> NP  
<strong>\<luigi1111w\></strong> “this is my hardware wallet”  
<strong>\<m2049r\[m\]\></strong> what if we use a rpi3 to do all the work &amp; store the caches for all the wallets onboard?  
<strong>\<m2049r\[m\]\></strong> :)  
<strong>\<endogenic\></strong> now we’re cookin with gas  
<strong>\<luigi1111w\></strong> it’s pretty slow too  
<strong>\<luigi1111w\></strong> normal client scanning on computer seems pretty ok to me  
<strong>\<m2049r\[m\]\></strong> how fast does it need to be? do we want full USB3 speeds?  
<strong>\<luigi1111w\></strong> by compromising your computer, the hacker now compromises just your privacy  
<strong>\<luigi1111w\></strong> rather than  
<strong>\<luigi1111w\></strong> you know  
<strong>\<luigi1111w\></strong> all your money  
<strong>\<i-a\></strong> you can run node on rp3, so it probably isnt so slow..?  
<strong>\<hotoatmeal\></strong> m2049r\[m\]: delegating the viewkey to the computer means it doesn’t have to be very quick at all  
<strong>\<luigi1111w\></strong> i-a how long does initial sync take  
<strong>\<hotoatmeal\></strong> (the device / usb, that is)  
<strong>\<luigi1111w\></strong> how long would it take to scan a restored wallet  
<strong>\<m2049r\[m\]\></strong> that would have been the first path to explore  
<strong>\<i-a\></strong> luigi1111w: ok, got it:/  
<strong>\<endogenic\></strong> i-a no no that’s just bc node is fast… because it’s asynchronous (now it’s my turn to troll)  
<strong>\<luigi1111w\></strong> is an rpi significantly better than a normal computer?  
<strong>\<luigi1111w\></strong> m2049r\[m\] if you slim the data down to close to minimum I don’t think bandwidth is much concern  
<strong>\<luigi1111w\></strong> lemme see  
<strong>\<m2049r\[m\]\></strong> so bottleneck is always computation then. and we want it fast so we dont take forever to sync up again.  
<strong>\<luigi1111w\></strong> I’d guess around 240 bytes per tx  
<strong>\<m2049r\[m\]\></strong> if we keep cache on device (sdcard or whatnot) then it can be shared between clients.  
<strong>\<luigi1111w\></strong> so even .25MBps would overwhelm the device most likely  
<strong>\<m2049r\[m\]\></strong> 240 either way?  
<strong>\<luigi1111w\></strong> no just computer-\>\*\*device  
<strong>\<hotoatmeal\></strong> another idea: put the viewkey on a separate device that’s always connected to a computer  
<strong>\<msvb-mob\></strong> There have been some requests for SD cards, so it would be nice to try to put one on at least the developer edition board (since it has more space.)  
<strong>\<m2049r\[m\]\></strong> yes - use a viewonly wallet.  
<strong>\<msvb-mob\></strong> m2049r\[m\]: Shift devices makes quite a nice hardware wallet (Bitbox) with a SD card.  
<strong>\<endogenic\></strong> do you guys suppose there’s any reason why this isn’t a match for the mymonero lightwallet server you run alongside the daemon?  
<strong>\<luigi1111w\></strong> I don’t  
<strong>\<endogenic\></strong> i might be misunderstanding  
<strong>\<luigi1111w\></strong> I think it’s great  
<strong>\<luigi1111w\></strong> it’s also great for existing mymonero users (privacy issues notwithstanding, of course)  
<strong>\<luigi1111w\></strong> but I guess we’re discussing the edge of what’s possible  
<strong>\<luigi1111w\></strong> for having a device that does basically no delegation for maximal security and privacy in all cases  
<strong>\<m2049r\[m\]\></strong> you are saying to have the device connect to an openmonero instance?  
<strong>\<luigi1111w\></strong> or maybe just rainbows and unicorns  
<strong>\<endogenic\></strong> m2049r\[m\]: no  
<strong>\<endogenic\></strong> i was envisioning some sort of stripped down protocol…vtnerd and i are working on that anyway in the api overhaul  
<strong>\<m2049r\[m\]\></strong> ok, what are you saying?  
<strong>\<luigi1111w\></strong> he’s talking about mymonero not openmonero  
<strong>\<endogenic\></strong> so if you’re running your own local server  
<strong>\<luigi1111w\></strong> though in theory they are similar  
<strong>\<endogenic\></strong> which is written in C++ and in the monero-cli repo alongside the official daemon  
<strong>\<endogenic\></strong> it almost seems like it’s more a question of protocol and transport  
<strong>\<endogenic\></strong> that is  
<strong>\<endogenic\></strong> if we really are talking about delegating scanning  
<strong>\<endogenic\></strong> of course you have the view key disclosure tradeoff but that’s why you run your own server locally  
<strong>\<m2049r\[m\]\></strong> i thought mymonero was closed source and not for anyone to run their own?  
<strong>\<luigi1111w\></strong> it is  
<strong>\<luigi1111w\></strong> but it won’t be for much longer  
<strong>\<luigi1111w\></strong> supposedly :)  
<strong>\<endogenic\></strong> yep  
<strong>\<endogenic\></strong> vtnerd’s prioritized it recently  
<strong>\<m2049r\[m\]\></strong> heh  
<strong>\<endogenic\></strong> he hadnt been able to before  
<strong>\<endogenic\></strong> too many pesky users\!  
<strong>\<endogenic\></strong> but anyway  
<strong>\<endogenic\></strong> this idea does seem to overlap with simplewallet/monero-gui’s job too  
<strong>\<luigi1111w\></strong> the theory of mymonero locally vs gui/cli is pretty similar  
<strong>\<luigi1111w\></strong> yes  
<strong>\<endogenic\></strong> does that count as a jinx?  
<strong>\<luigi1111w\></strong> slow motion  
<strong>\<endogenic\></strong> mm  
<strong>\<endogenic\></strong> anyway, whatever software we need, we can build  
<strong>\<endogenic\></strong> might be a good idea to just ask what the ideal situation is for the capabilities we have on the hardware side then fill the gaps  
<strong>\<m2049r\[m\]\></strong> we agree that we need lots of well-performing ed25519 operations on the device - no matter which road is taken?  
<strong>\<m2049r\[m\]\></strong> and possibly some form of storage (sdcard,eMMC?)  
<strong>\<luigi1111w\></strong> m2049r\[m\] more is better  
<strong>\<luigi1111w\></strong> but it doesn’t need to be “a lot” for the delegated road  
<strong>\<luigi1111w\></strong> which includes basically everything that’s not “do it all on device”  
<strong>\<luigi1111w\></strong> whether local client or some mymonero type  
<strong>\<m2049r\[m\]\></strong> signing would be on device for example - how large are the messages to be signed / verified?  
<strong>\<luigi1111w\></strong> it does need to be able to hash some KBs yes  
<strong>\<luigi1111w\></strong> 50 max, maybe  
<strong>\<luigi1111w\></strong> theoretically more, but shouldn’t really happen anymore, in most cases  
<strong>\<m2049r\[m\]\></strong> the cec1702 has 24k of “cryptographic ram” which seems to be the ram where cryptomagic happens.  
<strong>\<m2049r\[m\]\></strong> “in most cases” - one case is enough to break it though - so for such cases we would need a software solution to kick in and have the hardware do 99% of cases.  
<strong>\<m2049r\[m\]\></strong> (this is not a problem)  
<strong>\<m2049r\[m\]\></strong> do you have a particular testcase i could run just to see how slow the current device is performing?  
<strong>\<luigi1111w\></strong> no I mean you can just disallow  
<strong>\<luigi1111w\></strong> would need some research to really know how annoying that would be though  
<strong>\<luigi1111w\></strong> (problem comes from having many inputs)  
<strong>\<luigi1111w\></strong> ((I guess mining to the wallet could cause it))  
<strong>\<luigi1111w\></strong> m2049r\[m\] well if you have ed25519 code working on it  
<strong>\<m2049r\[m\]\></strong> i do  
<strong>\<luigi1111w\></strong> a simple scalarmult  
<strong>\<m2049r\[m\]\></strong> regardless of parameters?  
<strong>\<luigi1111w\></strong> random secret key  
<strong>\<luigi1111w\></strong> public key needs to be valid at least  
<strong>\<luigi1111w\></strong> or a simple scalarmult\_base if you have that  
<strong>\<m2049r\[m\]\></strong> including convesion from/to 256-bit scalars or the mult by itself?  
<strong>\<luigi1111w\></strong> including  
<strong>\<cslashm\></strong> m2049r\[m\]: hotoatmeal: Yes All secret value are passed encrypted from device to PC. When PC need perform operation with those values, there are retransmitted to the device  
<strong>\<luigi1111w\></strong> <https://github.com/monero-project/monero/blob/master/src/crypto/crypto.cpp#L127>  
<strong>\<luigi1111w\></strong> if you can match that  
<strong>\<m2049r\[m\]\></strong> ok - like the operation need to make a public key out of a secret key (eg. viewkey)?  
<strong>\<luigi1111w\></strong> yes  
<strong>\<luigi1111w\></strong> that includes a conversion from fe to bytes at the end  
<strong>\<m2049r\[m\]\></strong> i can do that. need to add time measuring stuff.  
<strong>\<m2049r\[m\]\></strong> will do that tomorrow and get back with results.  
<strong>\<luigi1111w\></strong> cool  
<strong>\<luigi1111w\></strong> might as well do arbitrary base too if it’s not much more work  
<strong>\<luigi1111w\></strong> <https://github.com/monero-project/monero/blob/master/src/crypto/crypto.cpp#L127>  
<strong>\<luigi1111w\></strong> you can use any valid point for the pubkey param  
<strong>\<luigi1111w\></strong> I can give you one in hex if you want  
<strong>\<luigi1111w\></strong> or you can just gen one from the above function  
<strong>\<m2049r\[m\]\></strong> will pm you for more details  
<strong>\<m2049r\[m\]\></strong> cslashm: what encryption is used for the transmission of the keys over usb?  
<strong>\<cslashm\></strong> It will be AES128  
<strong>\<cslashm\></strong> the key will new at each app usage and dedicated to session when transfer is performed  
<strong>\<cslashm\></strong> But I try to send even encrypted the view and spend key  
<strong>\<cslashm\></strong> <em>not send</em>  
<strong>\<m2049r\[m\]\></strong> and the key exchange is DH?  
<strong>\<cslashm\></strong> which DH? The AES key never leave the device  
<strong>\<m2049r\[m\]\></strong> maybe i dont understand aes. isnt that symmetric? how does the pc decode the ciphertext?  
<strong>\<cslashm\></strong> PC never decode, I try to explain  
<strong>\<luigi1111w\></strong> he’s using the pc for encrypted cache only it sounds like  
<strong>\<luigi1111w\></strong> but I don’t think you need to send spend key ever  
<strong>\<luigi1111w\></strong> device has enough memory for that, surely  
<strong>\<cslashm\></strong> voila. PC is just a encrypted holder  
<strong>\<cslashm\></strong> The advantage is that it keep the secret at the right place  
<strong>\<m2049r\[m\]\></strong> a storage.  
<strong>\<cslashm\></strong> for exemple in RCT, it request n secret key, store in the right vector place, and when it use it, it resend the encrypted secret key to device, which decrypt and do the op  
<strong>\<cslashm\></strong> @luigi1111w: yes spend/view key never leave the device  
<strong>\<cslashm\></strong> I use special value 00..00 and FF…FF for them on PC side  
<strong>\<m2049r\[m\]\></strong> ok, gotta go - it’s been great :)  
<strong>\<cslashm\></strong> basic idea is to hav no memory restriction, on easly follow the PC code evolution with minimal code device modification  
<strong>\<cslashm\></strong> <em>and easly</em> (end of day in FR :) )  
<strong>\<dEBRUYNE\></strong> cslashm: I’ve been wondering. Did you run any performance tests? For example, how long does it take to scan / refresh 10k blocks?  
<strong>\<cslashm\></strong> for now it’s a OMG part  
<strong>\<cslashm\></strong> I start some perf test yes but didnot remenber  
<strong>\<dEBRUYNE\></strong> Approximately? :p  
<strong>\<cslashm\></strong> It is just impossible to rescan the whole blockchain  
<strong>\<cslashm\></strong> holdon, deep search in paper on my desk  
<strong>\<dEBRUYNE\></strong> Yeah, but that won’t be necessary for 99% of the users :P  
<strong>\<cslashm\></strong> 10 min for 20 000 block, but app in -0O and level 4 log  
<strong>\<cslashm\></strong> wallet cli also in O0  
<strong>\<dEBRUYNE\></strong> I see, that doesn’t seem too bad tbh  
<strong>\<luigi1111w\></strong> that is scanning by cli, not ledger, right?  
<strong>\<cslashm\></strong> Its acceptable if you dont move in vacation for 1 month without refresh :D  
<strong>\<cslashm\></strong> no wallet cli scan the bc but delegate all keyderivation/keyimage computation to ledger to no disclose the view key  
<strong>\<dEBRUYNE\></strong> well, 1 month is 22k blocks give or take  
<strong>\<cslashm\></strong> So for each block, device compute some scalmul and hash  
<strong>\<dEBRUYNE\></strong> So that’d be 10 minutes wait  
<strong>\<luigi1111w\></strong> you can’t really use blocks  
<strong>\<luigi1111w\></strong> you have to use txs  
<strong>\<luigi1111w\></strong> are those current numbers  
<strong>\<luigi1111w\></strong> what will it look like if usage goes up (which it historically has)  
<strong>\<luigi1111w\></strong> I personally don’t really see a lot of benefit for disclosing the viewkey  
<strong>\<cslashm\></strong> yes for each txes. basically scan involves get\_key\_derivation and generate\_key\_image, those two op are done by the device. The rest is done by the PC as usual  
<strong>\<cslashm\></strong> view key is so never disclose  
\*\*\<cslashm\>\*\* So, I need to leave. Be back on monday. you can mail, PM reddit or put githib issue if you need long tech desc
