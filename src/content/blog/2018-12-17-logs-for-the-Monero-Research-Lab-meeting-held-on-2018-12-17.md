---
title: Logs for the Monero Research Lab Meeting Held on 2018-12-17
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> howdy everyone  
<strong>\<sarang\></strong> heyo  
<strong>\<suraeNoether\></strong> i've been sick all weekend  
<strong>\<suraeNoether\></strong> I'M BACK THO  
<strong>\<suraeNoether\></strong> not really  
<strong>\<suraeNoether\></strong> still exhausted but INCREMENTALLY GETTING BETTER  
<strong>\<sarang\></strong> just like monero  
<strong>\<suraeNoether\></strong> heh  
<strong>\<suraeNoether\></strong> allrighty everyone: as usual, we'll open with questions, then discuss the work we've done the past weeks since our last update  
<strong>\<suraeNoether\></strong> does anyone have any questions before we open up?  
<strong>\<suraeNoether\></strong> okay. cool :) we'll ask for questions as we go  
<strong>\<suraeNoether\></strong> since last we met I received and started reviewing sarang's version of the matching paper, and I attended the coincenter workshop in san fransisco, and I met isthmus in person  
<strong>\<suraeNoether\></strong> i paid for that trip out of pocket to not burden the community, fwiw  
<strong>\<sarang\></strong> Anything more about the coincenter workshop? You had mentioned it a bit before  
<strong>\<suraeNoether\></strong> so, to refresh the audience, coincenter writes policy reports to help inform lawmakers and regulators about cryptocurrency technologies, their true capabilities, and to advocate on behalf of financial privacy, to try to persuade lawmakers to not make stupid decisions  
<strong>\<suraeNoether\></strong> if anyone saw the CFTC commissioner's speech in october: there was a small freakout that the CFTC may be prosecuting developers of smart contracts eventually: these are the sorts of things that coincenter is trying to advocate \*against\*  
<strong>\<suraeNoether\></strong> the reports are extremely well written and contain some of the best arguments, in my mind, that financial privacy is necessary for an open society and that large-scale surveillance of financial transactions is basically antithetical to a free and open society  
<strong>\<sarang\></strong> What did you bring to the table from your perspective?  
<strong>\<suraeNoether\></strong> i brought a few arguments favoring privacy that i like a lot, tbh  
<strong>\<suraeNoether\></strong> for example  
<strong>\<kayront\></strong> clearly preserving financial privacy is a step in the right direction, but how to reconciliate regulator acceptance of something like monero, in a world of guilty by default, aml/kyc, FATCA and CRS? if you were to transpose the banking rules as they stand today to the crypto space, then it seems evident (unfortunately) that the general population having access to the famous swiss bank account in their pocket would go against the  
<strong>\<kayront\></strong> direction of the last decade or two, which is granting government the ability to track anything and everything digital (specifically in regards to money flows in this discussion)  
<strong>\<suraeNoether\></strong> i love it when fluffypony talks about how monero can be used to buy banned books in totalitarian regimes like north korea, for example, because it illustrates that \*using a technology that is morally neutral, and can be used for good or for evil\* is not inherently wrong or criminal, and can be used to do ostensibly "good" things for society  
<strong>\<suraeNoether\></strong> kayront: actually  
<strong>\<suraeNoether\></strong> not to hashtag-actually yoiu  
<strong>\<suraeNoether\></strong> the thing is that the banking rules as they stand today give exhcanges like coinbase plenty of power and ability to comply  
<strong>\<sarang\></strong> Exchanges are waiting for super-conservative Coinbase  
<strong>\<sarang\></strong> I'm not convinced that accepting Zcash was a step in the right direction or not  
<strong>\<suraeNoether\></strong> every single cryptocurrency, zcash and monero included, if you are using KYC/AML exchanges, can totally de-anonymize you. so you may ask a better question which is: "why are law enforcement asking for MORE power and control over this new technology?"  
<strong>\<sarang\></strong> lol because they can  
<strong>\<suraeNoether\></strong> for example kayront  
<strong>\<suraeNoether\></strong> sarang: yeah the answer is obvious  
<strong>\<suraeNoether\></strong> hence the political pushback and advocacy  
<strong>\<suraeNoether\></strong> so, for example kayront, a bank today only needs to file a suspicious activity report about information that's happening inside their own bank  
<strong>\<kayront\></strong> suraeNoether: "totally"? sure, they'll be able to track when you get in and out of monero, but after that, the ship has sailed  
<strong>\<suraeNoether\></strong> the guys at Chase arent' responsible for filing an SAR about stuff that happened on Wells Fargo accounts, and vice versa  
<strong>\<kayront\></strong> transfer to your own wallet, churn as you please for increased peace of mind, do whatever you want  
<strong>\<sarang\></strong> I think he's saying that you give them your name and address and bank info, so of course the exchange knows who you are  
<strong>\<kayront\></strong> i think this sort of thing scares the regulator  
<strong>\<sarang\></strong> Sure it does  
<strong>\<suraeNoether\></strong> so the recent trend where pols and law enforcement officials are asking for additional view key access is in contradiction with their current ability to comply  
<strong>\<suraeNoether\></strong> with classic/traditional assets  
<strong>\<suraeNoether\></strong> if Chase doesn't need to report anything beyond one hop outside their bank, why should Monero give outgoing view key access, for example? stuff like that  
<strong>\<sarang\></strong> We need to convince exchanges that they can already comply  
<strong>\<suraeNoether\></strong> so the coincenter workshop was a day of very smart and stimulating people from various coin projects and various non-profits around the world discussing how to convince lawmakers of stuff like this  
<strong>\<sarang\></strong> but regulators are being super cagey about specifics  
<strong>\<kayront\></strong> i find the whole argument very fallible, so don't misunderstand, of course I don't stand for that .. i don't quite understand how sending money to anyone you want to without asking for permission isn't basically the same as chatting up anyone online as you please without permission  
<strong>\<sarang\></strong> kayront: ?  
<strong>\<kayront\></strong> in fact, if you ask me, it opens up a whole new ocean of possibilities  
<strong>\<kayront\></strong> i mean the "guilty until proven innocent" spin on things  
<strong>\<suraeNoether\></strong> kayront there is a strong argumetn from the 1st and 4th amendment right that these financial transactions are free speech and demanding financial histories doesn't jive with the 4th amendment  
<strong>\<sarang\></strong> That's much broader than financial regulation  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<suraeNoether\></strong> not totally relevant  
<strong>\<sarang\></strong> ya  
<strong>\<suraeNoether\></strong> it's interesting  
<strong>\<sarang\></strong> So... good meeting, I take it?  
<strong>\<oneiric\_\></strong> what does MRL think about using hashcash or a reduced monero PoW (like pool mining shares) to secure anonymity networks for p2p?  
<strong>\<suraeNoether\></strong> and political science-y, so we can call it research :D  
<strong>\<sarang\></strong> And you had said that the documents will be published?  
<strong>\<kayront\></strong> :D  
<strong>\<sarang\></strong> oneiric\_: what does that mean exactly?  
<strong>\<suraeNoether\></strong> yeah, sarang, i walked away feeling like it was a room full of allies both for financial privacy in general and for the twin monero-zcash ecosystems. i wasn't expecting that at all, tbqh  
<strong>\<sarang\></strong> nice  
<strong>\<suraeNoether\></strong> sarang: yes, all the reports will be made public on coincenter.org soon  
<strong>\<suraeNoether\></strong> oneiric\_: if you elaborate i could form an opinion :D  
<strong>\<sarang\></strong> In the meantime, anything else to share suraeNoether of interest?  
<strong>\<lurkinandlearnin\></strong> Sounds really interesting. I'll look into those reports when they drop  
<strong>\<suraeNoether\></strong> oneiric\_: i know that stellar uses a weird concensus mechanism involving picking neighbors to form a quorum vote, but rather than being a networking tool, it's intended to replace POW/POS  
<strong>\<lurkinandlearnin\></strong> Hadn't even heard of coincenter until now  
<strong>\<suraeNoether\></strong> sarang: I read the recent andrew miller paper on probing network topology blindly in bitcoin  
<strong>\<oneiric\_\></strong> so, anonymity networks (and ipv6) make it much easier for attackers to perform sybil attacks by spinning up many addresses (nodes) for little cost. adding some form of PoW would help mitigate that possibility by adding some effort to spinning up a node  
<strong>\<sarang\></strong> Interesting, I'd be interested to see how that would work  
<strong>\<sarang\></strong> and how a PoW integrates to it  
<strong>\<suraeNoether\></strong> sarang which is SUPER clever and it could be used similarly for boostrapping blockchain downloads or kovri networking or something like that, if a similar sort of feature can be exploited as in that paper  
<strong>\<sarang\></strong> suraeNoether: link?  
<strong>\<sarang\></strong> Not sure I saw that paper  
<strong>\<suraeNoether\></strong> <https://www.cs.umd.edu/projects/coinscope/coinscope.pdf>  
<strong>\<sarang\></strong> How new is it? Didn't see on IACR  
<strong>\<suraeNoether\></strong> i saw it tweeted end of last week iirc  
<strong>\<sarang\></strong> word  
<strong>\<suraeNoether\></strong> it's clever: it uses inputs with no known outputs and a bitcoin node's behavior when it receives such an input  
<strong>\<suraeNoether\></strong> it can't be relayed because it doesn't appear valid  
<strong>\<sarang\></strong> Huh, I shall read it today, thanks  
<strong>\<suraeNoether\></strong> yeha, they use a purposeful double spend attempt to suss out which nodes you are \*really\* connected to  
<strong>\<suraeNoether\></strong> anyway: that paper, plus sarang and my matching paper, comprise most of my time last week and this week other htan the workshop  
<strong>\<suraeNoether\></strong> (surae is done now)\\  
<strong>\<sarang\></strong> The matching paper is under its reasonably final review  
<strong>\<sarang\></strong> we'll post here for internal review soon, and then off to the presses  
<strong>\<suraeNoether\></strong> although at the end of the meeting i have a small community announcement  
<strong>\<suraeNoether\></strong> sarang we should also consider whether we want to publish our matching paper \*specifically in a journal\* or leave it as an MRL bulletin  
<strong>\<sarang\></strong> I also spent a good deal of time on that, but kudos to surae for a lot of work on it  
<strong>\<sarang\></strong> Right  
<strong>\<suraeNoether\></strong> i feel like it would be valuable to publish in an applied graph theory journal  
<strong>\<lurkinandlearnin\></strong> Sorry to interupt but could you explain what exactly "matching" means in this context?  
<strong>\<sarang\></strong> And it opens up to additional matching/weighting work too  
<strong>\<suraeNoether\></strong> lurkinandlearnin: ah, good question  
<strong>\<sarang\></strong> lurkinandlearnin: you can apply graph theory to a transaction graph  
<strong>\<sarang\></strong> and this means questions of Monero analysis can be reframed to known graph theory problems  
<strong>\<suraeNoether\></strong> lurkinandlearnin: the idea is basically to link transactions in a transaction graph. if it's just a plain old graph with no additional information, mathematicians call it a "matching problem" or an "assignment problem" or sometimes a "marriage problem"  
<strong>\<sarang\></strong> suraeNoether formalizes this  
<strong>\<sarang\></strong> soon (tm)  
<strong>\<suraeNoether\></strong> lurkinandlearnin: so we are applying known techniques to our graph, to get an overall sense of "how bad" our linkability really is, disregarding less complete approaches previous researchers have used  
<strong>\<sarang\></strong> Once again, a "please stop publishing on this" to others =p  
<strong>\<lurkinandlearnin\></strong> I see. So it's to abstract the data we can get from the blockchain to a form where these established techniques and theories can be applied?  
<strong>\<sarang\></strong> Right, we don't have to reinvent the graph-theoretic wheel  
<strong>\<sarang\></strong> and it also provides bounds  
<strong>\<suraeNoether\></strong> yeah, the number one problem with ring signatures and monero going back years is small anon set sizes. fluffypony makes this an important part of almost every talk he gives, but people still regularly publish papers that re-invent the wheel over and over again. "look, if two signatures have the same ring, you can ... you can... oh boy\! i'ma publish\!"  
<strong>\<suraeNoether\></strong> the novelty of our approach is we are able to find a lower bound on some specific instances of the matching problem  
<strong>\<sarang\></strong> It's basically how other types of security proofs go... if you could break X, it'd mean you would have solved Famous Math Problem Y  
<strong>\<suraeNoether\></strong> previous approaches have been able to say "well, matching monero is \*no worse\* than sharp P. <https://en.wikipedia.org/wiki/%E2%99%AFP>  
<strong>\<lurkinandlearnin\></strong> Interesting. So is the paper "groundwork" towards using these techniques or have you already got findings?  
<strong>\<suraeNoether\></strong> but that's like saying "it's no worse than the worst possible problemt hat God himself couldn't solve"  
<strong>\<suraeNoether\></strong> lurkinandlearnin: we are sort of generalizing many previous techniques at once and showing how they fit under a common umbrella  
<strong>\<sarang\></strong> We have some algorithmic findings  
<strong>\<sarang\></strong> Again, it'll be posted here for internal review soon  
<strong>\<suraeNoether\></strong> yerp  
<strong>\<suraeNoether\></strong> it's a good paper  
<strong>\<suraeNoether\></strong> i like it a lot  
<strong>\<suraeNoether\></strong> it really highlights how linkable Monero will be until we get larger anon set authentications  
<strong>\<sarang\></strong> Aside from that, Badass Benedikt Bunz put out a new paper on batching in accumulators: <https://eprint.iacr.org/2018/1188>  
<strong>\<sarang\></strong> Unfortunately it applies most directly to RSA accumulators, which are a no-go for us  
<strong>\<lurkinandlearnin\></strong> Thanks for the explanations. I'll look forward to it.  
<strong>\<sarang\></strong> np  
<strong>\<sarang\></strong> I'm working a ZtM update regarding spend proofs, which I realized are useful but missing from the tech documentation  
<strong>\<sarang\></strong> as well as some arithmetic circuit research  
<strong>\<sarang\></strong> Otherwise, just trucking along with lit review and code  
<strong>\<sarang\></strong> A side note that several funding requests are open, including those that fund MRL and other developers: <https://forum.getmonero.org/8/funding-required>  
<strong>\<sarang\></strong> In a bear market, pockets tend to shrink unfortunately :(  
<strong>\<sarang\></strong> (disclaimer: one of those requests is for me)  
<strong>\<lurkinandlearnin\></strong> Ain't that the truth  
<strong>\<sarang\></strong> Loki Foundation is still willing to help fund one of us  
<strong>\<sarang\></strong> to the tune of 15K USD total  
<strong>\<sarang\></strong> If the funding requests don't complete, I would consider accepting the fiat donation under the right conditions  
<strong>\<kayront\></strong> the bear spares no one  
<strong>\<lurkinandlearnin\></strong> Loki Foundation?  
<strong>\<sarang\></strong> Foundation associated to this group: <https://loki.network/>  
<strong>\<sarang\></strong> Monero-based, so they wish to support researchers (and no doubt it's good PR too)  
<strong>\<sarang\></strong> The Foundation as a legal entity is not allowed to donate in cryptoassets  
<strong>\<sarang\></strong> so they'd have to donate directly in fiat  
<strong>\<lurkinandlearnin\></strong> haha I searched before you answered and only found a german record label  
<strong>\<sarang\></strong> Anyway, I welcome comments on such an arrangement  
<strong>\<sarang\></strong> I would insist that there be no additional strings that wouldn't apply to any other FFS donor  
<strong>\<sarang\></strong> to ensure research independence  
<strong>\<lurkinandlearnin\></strong> Well I've never heard of them but if it can be guaranteed no strings then I don't see the problem  
<strong>\<sarang\></strong> My goal would be to ensure that it doesn't change the nature of MRL's support  
<strong>\<sarang\></strong> It wouldn't become MRL Brought To You By Loki Foundation  
<strong>\<sarang\></strong> Anyway, it could be a moo point if the FFS are funded; then Loki would be interested in supporting a new researcher if one came around  
<strong>\<sarang\></strong> Anyone else have interesting work to share with the group?  
<strong>\<ilyaAldanov\></strong> I do\!  
<strong>\<sarang\></strong> carry on  
<strong>\<ilyaAldanov\></strong> But I guess the important stuff should go first.  
<strong>\<ilyaAldanov\></strong> I can go on after the meeting.  
<strong>\<sarang\></strong> Nonsense, all researchers are welcome here  
<strong>\<sarang\></strong> I'm finished with my update, please go ahead  
<strong>\<sarang\></strong> This is the point of the meeting  
<strong>\<ilyaAldanov\></strong> Today I want to present the return addresses.  
<strong>\<ilyaAldanov\></strong> Return address is a GREAT idea.  
<strong>\<ilyaAldanov\></strong> It's also MY idea, but that is unrelated.  
<strong>\<ilyaAldanov\></strong> It's quite simple: include sender's subaddress to every transaction header.  
<strong>\<ilyaAldanov\></strong> To make transactions unlinkable generate the subaddress from transaction's public key and sender's private key.  
<strong>\<ilyaAldanov\></strong> This way it's trivial to generate corresponding private key even after wallet restore.  
<strong>\<sarang\></strong> I was thinking about this earlier in the context of other timelock schemes  
<strong>\<ilyaAldanov\></strong> What good a return addresses for?  
<strong>\<ilyaAldanov\></strong> Many things\!  
<strong>\<ilyaAldanov\></strong> The most obvious one: a full or partial refund (interactive).  
<strong>\<ilyaAldanov\></strong> A merchant can send you funds back without asking for your address.  
<strong>\<kayront\></strong> i'm sodl  
<strong>\<ilyaAldanov\></strong> Another one: an exchange can return funds that it can't bind to any account.  
<strong>\<ilyaAldanov\></strong> the famous PaymentID problem.  
<strong>\<ilyaAldanov\></strong> Or if the account is closed for some reason.  
<strong>\<ilyaAldanov\></strong> There can be non-interactive services.  
<strong>\<ArticMine\></strong> or AML / KYC  
<strong>\<ilyaAldanov\></strong> Like micro-credits.  
<strong>\<kayront\></strong> .. or returning unused FFS monies to their owners  
<strong>\<ilyaAldanov\></strong> You send a coin to the public address and get two in a month.  
<strong>\<ilyaAldanov\></strong> But even more\!  
<strong>\<kayront\></strong> more, you say\!  
<strong>\<ilyaAldanov\></strong> You send money to a specific address and receive a password to something in the dust.  
<strong>\<sarang\></strong> It'd be \~2% increase in a 2-2 txn size  
<strong>\<ilyaAldanov\></strong> Yes. But it's per-transaction, not per-output or per-input.  
<strong>\<suraeNoether\></strong> ilyaAldanov: it's a very interesting idea. if it works out, that means we have two possible ways of going about doing some sort of return functionality  
<strong>\<ilyaAldanov\></strong> It's the only 100% reliable link back to transaction owner.  
<strong>\<lurkinandlearnin\></strong> This is a 10/10 idea. The usefulness of these features could help push the more general adoption of subaddresses (which imo is a urgent goal).  
<strong>\<sarang\></strong> It'd be a fingerprinting method, as usual  
<strong>\<ilyaAldanov\></strong> Yes, but I want to stress out that my return addresses is not limited to refunds.  
<strong>\<ilyaAldanov\></strong> sarang ?  
<strong>\<sarang\></strong> Anytime some transactions include data that not all do, it distinguishes them  
<strong>\<suraeNoether\></strong> it'd be easy to discern who is using these return addresses and who isn't  
<strong>\<ilyaAldanov\></strong> Every transaction should have one.  
<strong>\<ilyaAldanov\></strong> No exceptions.  
<strong>\<suraeNoether\></strong> i can see why you would say that  
<strong>\<suraeNoether\></strong> or suggest it i mean  
<strong>\<sarang\></strong> Yes, but of course you can't make randomness enforced  
<strong>\<lurkinandlearnin\></strong> yes but you could see that the subaddress in the header has received funds in a future transaction, correct?  
<strong>\<suraeNoether\></strong> its essentially, what, 32 Bytes additional per transaction? not so bad at all given the functionality that would come out of it  
<strong>\<sarang\></strong> lurkinandlearnin: no, but you'd see an output in a ring  
<strong>\<sarang\></strong> 64 bytes  
<strong>\<sarang\></strong> 2% add-on to a 2-2 txn  
<strong>\<suraeNoether\></strong> rihgt  
<strong>\<ilyaAldanov\></strong> The return address is just a subaddress - nobody sees when it is used except the owner.  
<strong>\<lurkinandlearnin\></strong> yes sorry that's what I meant  
<strong>\<suraeNoether\></strong> i think we need a write-up before we can really judge how it's supposed to work, but it's v promising  
<strong>\<sarang\></strong> There is one  
<strong>\<sarang\></strong> not published tho  
<strong>\<ilyaAldanov\></strong> I don't publish it because a) it's a draft b) don't want the coins I don't like to implement it first.  
<strong>\<sarang\></strong> The construction of the subaddress is clever ilyaAldanov  
<strong>\<sarang\></strong> Heh, Monero doesn't need to be first, just best  
<strong>\<suraeNoether\></strong> sarang: there's a write-up for ilyaAldanov's idea?  
<strong>\<sarang\></strong> It was sent privately during discussions  
<strong>\<kayront\></strong> fwiw i find this a very interesting idea as well  
<strong>\<sarang\></strong> The more we discuss it, the more I like it  
<strong>\<kayront\></strong> opens up a lot of functionality  
<strong>\<ilyaAldanov\></strong> I sent it to Sarang and Isthmus. Can send to you as well.  
<strong>\<suraeNoether\></strong> seems less disruptive than DLSAG  
<strong>\<kayront\></strong> if it can be made to work without meta/data leakage, sounds like a no brainer  
<strong>\<sarang\></strong> Yes, but doesn't solve the same problems  
<strong>\<oneiric\_\></strong> +1 sounds like a great improvment over payment id  
<strong>\<suraeNoether\></strong> sarang: right, no timelock/block height stuff built in  
<strong>\<sarang\></strong> oneiric\_: it doesn't really solve payment ID either  
<strong>\<sarang\></strong> it acts as a band-aid for when they require payment ID and you forget it  
<strong>\<sarang\></strong> also it's interactive  
<strong>\<sarang\></strong> I'm just saying this is orthogonal to DLSAG  
<strong>\<suraeNoether\></strong> would they be do-able together or would it be one or the other only?  
<strong>\<kayront\></strong> DLSAG = ?  
<strong>\<sarang\></strong> You could probably do a separate return subaddress per output address  
<strong>\<sarang\></strong> MRL-0008: <https://ww.getmonero.org/resources/research-lab/>  
<strong>\<ilyaAldanov\></strong> If you ask me, I came up with many more use cases for return addresses.  
<strong>\<sarang\></strong> I definitely see the usefulness  
<strong>\<suraeNoether\></strong> DLSAG = dual-output linkable spontaneous anonymous group signatures  
<strong>\<sarang\></strong> But it's our job to rip every idea apart  
<strong>\<ilyaAldanov\></strong> I want to talk about one exceptionally useful case tomorrow.  
<strong>\<sarang\></strong> Not today?  
<strong>\<ilyaAldanov\></strong> One feature per day\!  
<strong>\<suraeNoether\></strong> i.e.: usual ringCT but with two output keys and a trigger block before which the recipient of the first can spend the first and after which the recipient of the second can spend the second.  
<strong>\<ilyaAldanov\></strong> There was Hybrid Mining and Emission Curve days already.  
<strong>\<sarang\></strong> ilyaAldanov: it would be necessary to post the construction here for review  
<strong>\<sarang\></strong> this would need to be public, of course  
<strong>\<ilyaAldanov\></strong> Yes, of course.  
<strong>\<sarang\></strong> After you'd brought it up earlier, I started considering the effects this would have if it were optional (or effectively optional), especially on fake selections  
<strong>\<ilyaAldanov\></strong> But right now it's a draft. I really appreciate some comments, especially negative.  
<strong>\<sarang\></strong> This is an important consideration  
<strong>\<sarang\></strong> Even if it's mandatory, you should assume that wallets not using the functionality would be stupid and include all zeros or something  
<strong>\<ilyaAldanov\></strong> It'd be useless if optional.  
<strong>\<lurkinandlearnin\></strong> I like the fact that subaddresses have found another potential use.  
<strong>\<sarang\></strong> and determine what an adversary would do if it saw ring inputs from txns that include a "fake" return address vs a "true" one  
<strong>\<sarang\></strong> ilyaAldanov: I know, but you can't make randomness a consensus issue  
<strong>\<ilyaAldanov\></strong> That's a perspective I didn't think about. Thanks.  
<strong>\<sarang\></strong> It came up with payment IDs a while ago  
<strong>\<suraeNoether\></strong> ilyaAldanov: think about it this way: someone publishes a txn with the return key 000000000000001  
<strong>\<suraeNoether\></strong> how can you tell that's not genuinely random?  
<strong>\<suraeNoether\></strong> should it be blacklisted and not propagated?  
<strong>\<suraeNoether\></strong> what about 000..0?  
<strong>\<ilyaAldanov\></strong> Yep, I get the idea.  
<strong>\<suraeNoether\></strong> or what about 10101110010100111?  
<strong>\<suraeNoether\></strong> coolio  
<strong>\<sarang\></strong> The goal would be to ensure that even if wallets do this, it doesn't affect other users' rings  
<strong>\<ilyaAldanov\></strong> But there're many places where wallets can misbehave.  
<strong>\<sarang\></strong> Yes  
<strong>\<ilyaAldanov\></strong> Like in the change output.  
<strong>\<sarang\></strong> So we should assume they'll be awful and minimize the damage  
<strong>\<sarang\></strong> ilyaAldanov: if you approve, I can send your document to suraeNoether  
<strong>\<ilyaAldanov\></strong> I approve.  
<strong>\<suraeNoether\></strong> or just email it to me at <surae@getmonero.org>  
<strong>\<ilyaAldanov\></strong> But I want feedback\!  
<strong>\<sarang\></strong> Sure; you'll get the best feedback if/when you release the draft publicly, tho  
<strong>\<ilyaAldanov\></strong> Are there any spies of the coins I don't like here?  
<strong>\<suraeNoether\></strong> ilyaAldanov: probably, but they also are not very good at their jobs :D  
<strong>\<sarang\></strong> probably  
<strong>\<ilyaAldanov\></strong> I don't like coins with premines, developer's rewards and obnoxious leaders.  
<strong>\<sarang\></strong> Welcome to Club Monero  
<strong>\<sarang\></strong> I assume Monono will steal this, but I'm ok with that  
<strong>\<sarang\></strong> So our time is nearly up... anyone else have info to share?  
<strong>\<nioc\></strong> a while ago there was a request for a recommended ring size for the next hard fork which is April and the code freeze is Jan. I know research has been done to address this request. Where do we stand in regards to a possible ring size increase?  
<strong>\<sarang\></strong> suraeNoether: you'd indicated you had a community announcement  
<strong>\<lurkinandlearnin\></strong> I am a spy  
<strong>\<ilyaAldanov\></strong> I'll publish it, just to put one more section about Shared Secret.  
<strong>\<sarang\></strong> cool  
<strong>\<lurkinandlearnin\></strong> oh wait I wasn't meant to say that out loud  
<strong>\<sarang\></strong> I do not see a reason to increase at this time  
<strong>\<nioc\></strong> but more is better :D  
<strong>\<suraeNoether\></strong> nioc: recent research suggests that increasing ring size \*may not\* be super helpful, even though \*the min time required\* to generate a guess at the true Monero transaction history is proportional to r: double r and you double that min time required  
<strong>\<suraeNoether\></strong> which sounds great  
<strong>\<suraeNoether\></strong> but it's not very efficient  
<strong>\<suraeNoether\></strong> i would rather: increase r by 1 and the difficulty doubles  
<strong>\<sarang\></strong> suraeNoether: your community annoucement? (I don't want to go over if people need to leave)  
<strong>\<sarang\></strong> Hmm he has vanished  
<strong>\<lurkinandlearnin\></strong> Community announcement: <https://www.youtube.com/watch?v=CiRu\_W9tzM8>
