---
title: Overview and Logs for the Dev Meeting Held on 2016-06-19
summary: C4, open PRs, and brief update on Ring CT and 0MQ
tags: [dev diaries, core, crypto, 0mq]
author: dEBRUYNE / fluffypony
---

### Overview (by Aerbax)

An overview [can be found on Hello Monero](https://hellomonero.com/article/monero-bi-weekly-dev-meeting-note-highlights-2016-06-19)

### Logs

<strong>\<fluffypony\></strong> ok  
<strong>\<fluffypony\></strong> hello and welcome  
<strong>\<tewinget\></strong> ack  
<strong>\<wallet42\></strong> Sup fluffypony  
<strong>\<fluffypony\></strong> so first things first  
<strong>\<meeting-bot\></strong> \[anonimal\] EinMByte: ^ Monero meeting now, Kovri in about an hour or so (just FYI)  
<strong>\<fluffypony\></strong> after the last meeting, which was mostly focused on C4, we bounced some of that around  
<strong>\<fluffypony\></strong> I think the spirit of C4 is good, and will help keep Monero inclusionary towards new contributors  
<strong>\<fluffypony\></strong> but moneromooo in particular disagreed with some of the specifics  
<strong>\<fluffypony\></strong> or where C4 is a little vague  
<strong>\<fluffypony\></strong> so what we’re going to do is fork C4 from Unprotocols / yrashk into the Monero repo  
<strong>\<meeting-bot\></strong> \[psi\] c4?  
<strong>\<fluffypony\></strong> and we’ll tweak it from there, keeping it in step with changes made upstream in Unprotocols  
<strong>\<fluffypony\></strong> psi: the Collaborative Code Construction Contract, see last meeting’s minutes for an intro and discussion  
<strong>\<meeting-bot\></strong> \[anonimal\] Or Kovri’s contributing guide.  
<strong>\<fluffypony\></strong> yup  
<strong>\<fluffypony\></strong> I think everyone is aware that this is security software we’re dealing with  
<strong>\<fluffypony\></strong> and we can’t be crazy and accept things that may contain backdoors  
<strong>\<fluffypony\></strong> but we also want some structure that makes contributors feel welcome, even if their contributions need some work and aren’t up to a standard we’d like  
<strong>\<fluffypony\></strong> somewhere inbetween being completely permissive and miring contributions in PR hell is a nice balance, and we’ll figure it out  
<strong>\<ArticMine\></strong> We need to balance security and making contributors welcome  
<strong>\<fluffypony\></strong> yup exactly  
<strong>\<fluffypony\></strong> ok so on to more fiddly code bits, less soft skills  
<strong>\<fluffypony\></strong> I was hoping tewinget could update us on the 0MQ work, which is about to go up on the forum for funding  
<strong>\<tewinget\></strong> ok  
<strong>\<moneromooo\></strong> My point was not security, it was more about the crazy wish to keep obvious crap in.  
<strong>\<tewinget\></strong> <https://www.github.com/tewinget/bitmonero/tree/zmq-dev> \<— there’s the branch, gimme one min to take care of something then I can brief  
<strong>\<fluffypony\></strong> ok  
<strong>\* fluffypony</strong> plays hold music  
<strong>\* tewinget</strong> is typing  
<strong>\* DaveyJones</strong> just watches  
<strong>\<tewinget\></strong> ok, so far I’ve got cryptonote::classes to/from json for a majority of what will need to be serialized for RPC. I have a couple of RPC calls actually written and working via ZMQ (get<em>height get\_transactions, and key\_images\_spent)  
<strong>\<tewinget\></strong> that’s more or less a summary of progress  
<strong>\<tewinget\></strong> as far as process  
<strong>\<tewinget\></strong> the idea is to try to create RPC as we want it to be, rather than trying to modify the existing structure, and then plug in backwards-compatibility later  
<strong>\<fluffypony\></strong> tewinget: so using the structure that is / was on the Wikia ?  
<strong>\<meeting-bot\></strong> \[psi\] to rehash, you are redoing monero’s wire protocol to use zmq correct?  
<strong>\<fluffypony\></strong> psi: no, not wire protocol, that will use ZMTP (a part of the 0MQ project) and come later  
<strong>\<tewinget\></strong> psi: more or less, but a bit more than just that  
<strong>\<tewinget\></strong> oh  
<strong>\<tewinget\></strong> I mean, kinda wire, but not p2p yet  
<strong>\<tewinget\></strong> rpc  
<strong>\<fluffypony\></strong> this is redoing the communication between the node and “clients” like miners / mining pool software / wallets / etc.  
<strong>\<meeting-bot\></strong> \[psi\] kk  
<strong>\<meeting-bot\></strong> \[psi\] zmtp is still being drafted correct?  
<strong>\<fluffypony\></strong> nope all done, afaik: <http://zmtp.org>  
<strong>\<tewinget\></strong> \<fluffypony\> tewinget: so using the structure that is / was on the Wikia ? \<— well, yes, but also I was hoping to get some input today (not necessarily now) from anyone who would like to comment on the future of RPC  
<strong>\<fluffypony\></strong> it’s already on v3  
<strong>\<fluffypony\></strong> ok so maybe one of the things we need to do now is move that design doc from the Wikia to the Github wiki  
<strong>\<fluffypony\></strong> wallet42: are you up to doing that, or busy travelling atm ?  
<strong>\<tewinget\></strong> I can say that the few commands I’ve done don’t necessarily conform to any spec like json-rpc, but that’s easy to change — structure is currently placeholder while functionality is implemented  
<strong>\<tewinget\></strong> oh, one important detail I left out  
<strong>\<tewinget\></strong> I think it’s best if the RPC is straight json. This comes at a very, very minor cost in speed, but means that implementation in other languages will be far less intimidating for new contributors  
<strong>\<tewinget\></strong> and I know I don’t personally plan to write libMonero for every language out there…  
<strong>\<fluffypony\></strong> oh I agree - the idea behind 0MQ is for a language to use 0MQ bindings and just be able to talk straight to the daemon  
<strong>\<tewinget\></strong> yup, and this way for any language that has json and zmq bindings, all one needs to do is give the language a cursory understanding of cryptonote structs  
<strong>\<fluffypony\></strong> if JSON is the way we want to do that that’s fine, we can always modify it later to support Google’s protobufs or something later on  
<strong>\<tewinget\></strong> <https://paste.fedoraproject.org/379294/14659488/> \<— there’s an example of get\_transactions  
<strong>\<tewinget\></strong> it’s also very nice to do ad-hoc testing via python :)  
<strong>\<fluffypony\></strong> cool  
<strong>\<tewinget\></strong> any thoughts, anyone?  
<strong>\<wallet42\></strong> fluffypony: In about 3 weeks im back in Berlin, right now i only have like 1 day a week. But yes the wiki will get more data as I am moving myself trough the code  
<strong>\<wallet42\></strong> Especially better wiki documentation of the datatypes/protocol  
<strong>\<wallet42\></strong> wiki.bitcoin.it/wiki/Protocol basically  
<strong>\<fluffypony\></strong> tewinget: how hard would it be to implement different schemes in future, like JSON / protobufs / ASN.1 BER ?  
<strong>\<fluffypony\></strong> wallet42: ok cool, thank you  
<strong>\<tewinget\></strong> fluffypony: wouldn’t be too bad, I’m trying to make things pretty modular. It wouldn’t be too bad to make it a bit more generic than json  
<strong>\<tewinget\></strong> it’s already 90% ready for that as-is  
<strong>\<fluffypony\></strong> kk  
<strong>\<fluffypony\></strong> alright, tewinget anything else or can we move on to the next thing ?  
<strong>\<tewinget\></strong> the ZMQ-side of things was pretty trivial tbh  
<strong>\<tewinget\></strong> oh, anyone averse to having a separate listening port for publish/subscribe such as “new\_block\_notify” etc?  
<strong>\<fluffypony\></strong> you mean a separate port for pub-sub than the IPC port ?  
<strong>\<tewinget\></strong> well, there will be a port for “request thing from daemon”  
<strong>\<tewinget\></strong> can’t use the same port for publish/subscribe, I’m pretty sure  
<strong>\<fluffypony\></strong> I don’t see a problem with that  
<strong>\<tewinget\></strong> without an unholy amount of added complexity that isn’t worth at all  
<strong>\<fluffypony\></strong> one thing you may want to do is also look at Bitcoin’s 0MQ effort  
<strong>\<fluffypony\></strong> I don’t think wumpus is around at the moment  
<strong>\<fluffypony\></strong> but they’ve been pecking away at 0MQ for some time  
<strong>\<moneromooo\></strong> Isn’t the point of 0MQ to abstract comms to allow things like that ?  
<strong>\<fluffypony\></strong> moneromooo: pub-sub is a different beast to control / request  
<strong>\<tewinget\></strong> 0MQ uses different socket types like Request-Reply, or Pub/Sub  
<strong>\<fluffypony\></strong> normally for pub-sub you’re sending a request once and then receiving “push” notifications forever  
<strong>\<tewinget\></strong> and one socket can only be one type, and I don’t think you can bind two sockets to the same port, as how would it route that?  
<strong>\<fluffypony\></strong> Bitcoin has walletnotify and blocknotify that work in that way  
<strong>\<tewinget\></strong> so using the same port for req-rep and pub-sub would require…well, no, just no  
<strong>\<fluffypony\></strong> it would end up looking gross like the RPC stuff at the moment  
<strong>\<tewinget\></strong> moreso, in fact  
<strong>\<fluffypony\></strong> different HTTP paths for the JSON and HTTP RPCs  
<strong>\<tewinget\></strong> \<fluffypony\> alright, tewinget anything else or can we move on to the next thing ? \<— happy to give a few minutes for any comments from anyone, but other than that I think that’s about it  
<strong>\<fluffypony\></strong> cool if anything pops up over the rest of the meeting then we can see  
<strong>\<tewinget\></strong> oh, and feel free to give feedback on the branch, I’ll repaste the link in a sec. Feedback here or via github is fine  
<strong>\<tewinget\></strong> <https://www.github.com/tewinget/bitmonero/tree/zmq-dev>  
<strong>\<fluffypony\></strong> ok next, moneromooo do you feel like giving an update on RingCT? looks like it’s making nice headway :)  
<strong>\<moneromooo\></strong> It kinda works. I’m fixing bugs now.  
<strong>\<fluffypony\></strong> moneromooo: is it going to be a hard fork where all new transactions are v3 / ringCT, but they can spend pre-ringCT outs?  
<strong>\<moneromooo\></strong> They  
<strong>\<fluffypony\></strong> they = transactions  
<strong>\<othe\></strong> coinbase will use non-ringct tho?  
<strong>\<fluffypony\></strong> othe: yes afaik  
<strong>\<moneromooo\></strong> They’ll be v2 and can spend either pre rct outputs or rct ones.  
<strong>\<fluffypony\></strong> moneromooo: ooooh, so a soft fork? :-P  
<strong>\<moneromooo\></strong> Hmm. I haven’t thought about the distinction tbh.  
<strong>\<moneromooo\></strong> Theoretically, coinbase might not even need to be in the clear I think. Though it’d require some shen magic.  
<strong>\<fluffypony\></strong> I think it’d be a hard fork, because old nodes won’t understand rct outs  
<strong>\<fluffypony\></strong> so we’d have to bump the block version anyway  
<strong>\<ArticMine\></strong> But will non RingCT other than coninbase transactions be valid?  
<strong>\<moneromooo\></strong> Oh they’d reject new txes, yes.  
<strong>\<yrashk\></strong> fluffypony: I’m thinking of an unprotocol for describing diverged unprotocols  
<strong>\<yrashk\></strong> So meta  
<strong>\<fluffypony\></strong> moneromooo: ok then that’s hard fork  
<strong>\<fluffypony\></strong> lol yrashk  
<strong>\<yrashk\></strong> But I’m actually serious  
<strong>\<yrashk\></strong> :)  
<strong>\<fluffypony\></strong> yrashk: what’s that Unprotocol for creating protocols with consensus?  
<strong>\<tewinget\></strong> ArticMine: I think post-fork that all non-coinbase tx will be ringCT, but I’m not sure.  
<strong>\<moneromooo\></strong> ArticMine: if you mean “will non RingCT outputs other than coninbase transactions be valid?”, then I’d choose no, but it could be made either way.  
<strong>\<yrashk\></strong> fluffypony: COSS? There’s nothing about consensus there  
<strong>\<fluffypony\></strong> yrashk: yes that - but it’s about creating new protocols as a group, right ?  
<strong>\<yrashk\></strong> Kind of but very very lightweight  
<strong>\<fluffypony\></strong> kk  
<strong>\<yrashk\></strong> Which is a good thing generally  
<strong>\<CFP\></strong> Greetings fellas  
<strong>\<fluffypony\></strong> moneromooo: I tend to agree with you - coinbase txs is fine, but after that it should be rct only  
<strong>\<CFP\></strong> Crazyflashpie stoping by to say hello  
<strong>\<yrashk\></strong> fluffypony: are you interested to collaborate on the protocol divergence protocol? (PDP)  
<strong>\<fluffypony\></strong> hi CFP  
<strong>\<CFP\></strong> Looks like the \# of nodes in China is climbing?  
<strong>\<fluffypony\></strong> yrashk: let’s chat after the meeting, definitely interested in discussing it, as it’s relevant to us  
<strong>\<yrashk\></strong> I can explain my motivations behind it  
<strong>\<yrashk\></strong> Today?  
<strong>\<yrashk\></strong> Ping me on telegram or here when ready  
<strong>\<fluffypony\></strong> kk  
<strong>\<fluffypony\></strong> ok next I just wanted to bounce through some open PRs  
<strong>\<fluffypony\></strong> \#818 is still open pending luigi1111w / luigi1112 coming up with those spec changes, no rush there  
<strong>\<ArticMine\></strong> moneromooo I would expect non RingCT outputs other than coinbase to be invalid after a given block  
<strong>\<fluffypony\></strong> \#775 is ready to be merged - moneromooo, just to double check, you’re fine with that, right ?  
<strong>\<ArticMine\></strong> With the 6 month upgrade cycle built in  
<strong>\<fluffypony\></strong> ArticMine: agreed  
<strong>\<luigi1112\></strong> Yes I’ll try to do that this week  
<strong>\<moneromooo\></strong> Yes. It’s a wee bit spammier now in the logs, but other than that it’s good to go.  
<strong>\<fluffypony\></strong> ok then \#810, the caching thing, I’m still confused as to whether we must merge or not  
<strong>\<moneromooo\></strong> Not sure. I think enough said no.  
<strong>\<fluffypony\></strong> ok I’ll close it, we can reopen later  
<strong>\<moneromooo\></strong> But then nobody patched the pool code :)  
<strong>\<fluffypony\></strong> and pools can manually pull that in if they need  
<strong>\<fluffypony\></strong> then the gcc 6.1 stuff - as I understand it there are more changes than what is covered in those two PRs  
<strong>\<fluffypony\></strong> so do we close the PRs and just note that “gcc 6.1 not supported yet”  
<strong>\<meeting-bot\> \[anonimal\]</strong> Noooooooo…  
<strong>\<fluffypony\></strong> or do we merge them in preparation for supporting 6.1 ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Please nooooooo…  
<strong>\<fluffypony\></strong> lol anonimal  
<strong>\<moneromooo\></strong> If they’ll be needed anyway…  
<strong>\<meeting-bot\> \[anonimal\]</strong> This also re: \#846?  
<strong>\<moneromooo\></strong> One of them is a superset of the other IIRC.  
<strong>\<fluffypony\></strong> anonimal: yeah, 846 and 845  
<strong>\<meeting-bot\> \[anonimal\]</strong> radfish’s work builds, so is the problem more eyes/more time to review?  
<strong>\<fluffypony\></strong> anonimal: it was more that I was travelling, so I don’t really know which is the superset of which, and which to close / merge / bail out of entirely :-P  
<strong>\<meeting-bot\> \[anonimal\]</strong> Oh, well I can spend some time this week giving input if that helps.  
<strong>\<moneromooo\></strong> 846 seems to be the superset.  
<strong>\<tewinget\></strong> PR X is a superset of PR Y seems like an odd situation to be in…  
<strong>\<tewinget\></strong> especially if both are open  
<strong>\<fluffypony\></strong> tewinget: quite  
\*\*\<neosilky</em>\>\*\* I had to merge them to get the repo to compile as GCC 6.1 is default for Arch  
<strong>\<fluffypony\></strong> kk  
<strong>\<meeting-bot\> \[anonimal\]</strong> re: that ^, I only merged \#846 and builds fine.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I see the issue of both PR’s being open, I can comment further this week after looking at them if they are still open by then.  
<strong>\<neosilky\_\></strong> Yep, only needed \#846. @tewinget should enable testing repo too :)  
<strong>\<fluffypony\></strong> ok then I’ll close 845 and merge 846  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok.  
<strong>\<fluffypony\></strong> then \#856 I’ve reviewed and will merge  
<strong>\<fluffypony\></strong> \#855 seems fine to me, I defer to hyc’s knowledge of his own product ;)  
<strong>\<fluffypony\></strong> \#863 seems fine too  
<strong>\<fluffypony\></strong> \#862 - luigi1112 can I take your comment as a review?  
<strong>\<moneromooo\></strong> Oh. Let me change it now…  
<strong>\<gingeropolous\></strong> tewinget, i may try and put this in a comment on the <https://www.github.com/tewinget/bitmonero/tree/zmq-dev> , but is this the space wherein the daemon could have multiple rpc ports with different characteristics?  
<strong>\<luigi1112\></strong> I think it’s fine yeah  
<strong>\<moneromooo\></strong> pushed  
<strong>\<fluffypony\></strong> k  
<strong>\<meeting-bot\> \[anonimal\]</strong> Has there been any definitive decisions re: C4 since previous meeting? I know there are differing arguments.  
<strong>\<fluffypony\></strong> anonimal - yes, my comments at the beginning of the meeting, will let you know when the log is up if you missed them  
<strong>\<tewinget\></strong> gingeropolous: not entirely sure what you mean to ask there  
<strong>\<meeting-bot\> \[anonimal\]</strong> “we’ll figure it out” \<— was that it?  
<strong>\<gingeropolous\></strong> i.e., port 18081 would be full access, and 18082 could be less access.  
<strong>\<fluffypony\></strong> anonimal: yes basically the next step is fork -\>\*\* adjust accordingly -\>\*\* decide to abandon or adopt the iteration  
<strong>\<gingeropolous\></strong> right now if you want different permissions for remote access to the daemon, you need multiple daemons and multiple databases  
<strong>\<othe\></strong> isnt an auth system with permissons better for this  
<strong>\<fluffypony\></strong> gingeropolous: I’m of a mind that we need a finer distinction than “trusted daemon” and “not trusted”  
<strong>\<fluffypony\></strong> we need a proper ACL  
<strong>\<fluffypony\></strong> what othe said  
<strong>\<fluffypony\></strong> so shelve it as a thing to do later on  
<strong>\<gingeropolous\></strong> word  
<strong>\<fluffypony\></strong> ok I think that’s it from my side - anything else before we move to the Kovri meeting?  
<strong>\<tewinget\></strong> glad someone else could answer that while I was rebooting. Stupid computer crashes frequently, pretty sure it’s hardware.  
<strong>\<fluffypony\></strong> tewinget: you should buy a Mac :-P  
<strong>\<ArticMine\></strong> No  
<strong>\<tewinget\></strong> fluffypony: I thought we were friends…  
<strong>\<tewinget\></strong> tbh if a newer Mac (not new, with that single port, but new-ish) landed on my lap I’d throw Linux on it and use it  
<strong>\<tewinget\></strong> but I’d never buy one, they’re way too expensive for what they are.  
<strong>\<othe\></strong> actually the macbook pro are good value for money compared to other ultrabooks; anyway kovir next :p  
<strong>\<fluffypony\></strong> Pro Retina is great, although I’ve switched my Purism Librem 13 + Qubes for anything remotely sensitive  
<strong>\<antanst1\></strong> Hackintosh user here :-) It’s pretty easy to install OSX if you choose hardware carefully.  
<strong>\<antanst1\></strong> works pretty much perfectly.  
<strong>\<othe\></strong> correct, also run a hackintosh desktop  
<strong>\<ArticMine\></strong> I see the software not the hardware as the issue with Mac  
<strong>\<meeting-bot\> \* anonimal</strong> has 8 year old hackbook pro running Arch :/  
<strong>\<meeting-bot\> \[anonimal\]</strong> Still alive, surprisingly.  
\*\*\<fluffypony\>\*\* nice
