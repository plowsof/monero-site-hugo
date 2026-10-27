---
title: Logs for the MRL Meeting Held on 2020-04-01
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<ArticMine\></strong> Hi  
<strong>\<Isthmus\></strong> Heya  
<strong>\<Isthmus\></strong> Sorry I fell asleep last week  
<strong>\<sarang\></strong> I'm feeling a bit under the weather today, so I'll try to keep things short and sweet if possible  
<strong>\<sarang\></strong> No problem Isthmus  
<strong>\<sarang\></strong> Let's move on to ROUNDTABLE  
<strong>\<sarang\></strong> My list is short but hopefully interesting  
<strong>\<sarang\></strong> The CLSAG preprint has been revised and updated on the IACR archive  
<strong>\<sarang\></strong> Link: <https://eprint.iacr.org/2019/654>  
<strong>\<sarang\></strong> New security model and proofs  
<strong>\<UkoeHB\_\></strong> Oh hi forgot about this :p  
<strong>\<sarang\></strong> Alongside this, the code has been updated to make it easier to include trezor/ledger support  
<strong>\<sarang\></strong> Plumbing for device support: <https://github.com/SarangNoether/monero/commit/94a7daad0f53074a28dbfb39c0ed1d68d5c40e86>  
<strong>\<sarang\></strong> Support for ledger, courtesy of cslashm: <https://github.com/SarangNoether/monero/pull/1>  
<strong>\<sarang\></strong> Smaller items are proofreading for UkoeHB\_'s Zero to Monero update, and finalizing a PR for hash function domain separation, along with the usual literature review  
<strong>\<sarang\></strong> Does anyone have particular questions, or otherwise have research of interest to share?  
<strong>\<sarang\></strong> I see that Isthmus has just added to the agenda issue  
<strong>\<Isthmus\></strong> <https://user-images.githubusercontent.com/21246742/78165574-c14f9500-7408-11ea-8ae5-7d695b4321d3.png>  
<strong>\<Isthmus\></strong> n3ptune and I have been exploring tx\_extra some more  
<strong>\<sarang\></strong> neat  
<strong>\<Isthmus\></strong> A few months ago @UkoeHB\_ suggested that the \*ordering\* of tags might leak some information  
<strong>\<Isthmus\></strong> This intuition turned out to be correct  
<strong>\<n3ptune\></strong> link to the issue: <https://github.com/monero-project/research-lab/issues/61>  
<strong>\<Isthmus\></strong> If we look at tx\_extra in the wild since 1978433 (v12) we see 8 different ways that tags are assembled  
<strong>\<sarang\></strong> Enforcing an ordering and certain fields makes sense for uniformity; I wonder what the added time complexity would be for parsing overall  
<strong>\<sarang\></strong> This also ties in with an idea for Janus mitigation, which would enforce a per-transaction Janus transaction key and per-output tx pubkeys  
<strong>\<Isthmus\></strong> +1  
<strong>\<sarang\></strong> And, FWIW, there was a PR yesterday from moneromooo with an idea for an encrypted-memo-type addition to extra: <https://github.com/monero-project/monero/pull/6410>  
<strong>\<sarang\></strong> (I have concerns about that one)  
<strong>\<Isthmus\></strong> I would support encrypted memo if \*length\* and \*inclusion\* enforced in protocol. :- )  
<strong>\<Isthmus\></strong> Zcash has a 512 byte encrypted memo on all z2z transactions, and people are having a lot of fun with it  
<strong>\<Isthmus\></strong> (mostly whimsical fun at the moment, but I expect fun applications to follow)  
<strong>\<sarang\></strong> Of course, this seems to overlap in functionality somewhat with encrypted pIDs  
<strong>\<Isthmus\></strong> Oh yea, could just roll the PID into the memo  
<strong>\<sarang\></strong> But yes, I agree that if included, length should be enforced for uniformity  
<strong>\<Isthmus\></strong> Would it be per txn or per output?  
<strong>\<UkoeHB\_\></strong> Im a bit skeptical about scope creep, since Monero is money, not random messages  
<strong>\<ArticMine\></strong> and kept small  
<strong>\<UkoeHB\_\></strong> or email  
<strong>\<ArticMine\></strong> or a replacement for twitter  
<strong>\<sarang\></strong> AIUI that PR requires a single non-change output  
<strong>\<sarang\></strong> at least from my initial read of the code  
<strong>\<sarang\></strong> Its use in Zcash is per-output, I believe  
<strong>\<ArticMine\></strong> Can we actually do away with this messaging entirely?  
<strong>\<sarang\></strong> ?  
<strong>\<UkoeHB\_\></strong> Isthmus's research indicates that even though the extra field is technically open ended, in practice people arent implementing random things  
<strong>\<UkoeHB\_\></strong> supporting random messages with core code would directly lead to more random things in the chain  
<strong>\<Isthmus\></strong> Wait can we clarify "random"  
<strong>\<Isthmus\></strong> Do we mean a fixed tag that supports arbitrary payload  
<strong>\<UkoeHB\_\></strong> non-standard  
<strong>\<UkoeHB\_\></strong> I guess 'memo field' implies to me 'any random message you feel like'  
<strong>\<Isthmus\></strong> Ideally encrypted  
<strong>\<sarang\></strong> To clarify, this PR uses chacha to encrypt with the DH shared secret, including padding as needed to hit certain size resolution  
<strong>\<atoc\></strong> what are pros of including memo field?  
<strong>\<sarang\></strong> but it's not possible to enforce that the data are actually encrypted  
<strong>\<UkoeHB\_\></strong> does chacha index each chunk in some way (so no two chunks are likely to be the same)?  
<strong>\<ArticMine\></strong> That is my question  
<strong>\<sarang\></strong> I think the goal was to enable encrypted recipient data as desired, to reduce the likelihood of non-standard inclusion of data in extra  
<strong>\<sarang\></strong> UkoeHB\_: the chunks are appended before passing to chacha  
<strong>\<sarang\></strong> If I'm reading the PR correctly, the chunking is just to enforce size resolution  
<strong>\<Isthmus\></strong> From a technical/statistical info leak standpoint, we should either have \*no\* messages, or an encrypted message on \*every\* transactions. Which option we choose is partially a UX/design conversation.  
<strong>\<sarang\></strong> And at that point, you basically have a larger pID setup  
<strong>\<Isthmus\></strong> Yea  
<strong>\<sarang\></strong> Which was part of my concern  
<strong>\<Isthmus\></strong> Is there no way to mathematically verify that a field is encrypted?  
<strong>\<sarang\></strong> Not for the network AFAIK  
<strong>\<sarang\></strong> Nor is it possible in Zcash either  
<strong>\<sarang\></strong> It is possible to assure the \_recipient\_ that if they can decrypt properly, the data were encrypted as expected  
<strong>\<Isthmus\></strong> Ohhh yea that's how that works  
<strong>\<sarang\></strong> But otherwise, it's just uniformly distributed data  
<strong>\<UkoeHB\_\></strong> I think that encryption or not isn't a concern, since implementers should want to harmonize with other implementations. The core impl would encrypt, so others would too  
<strong>\<ArticMine\></strong> All of this begs the question do we need this memo filed and even extra  
<strong>\<sarang\></strong> So the worst case in Zcash is that you throw a bunch of unencrypted junk into a tx that gets accepted by the network, but that the recipient won't properly decrypt  
\< I would be very happy to do away with both  
<strong>\<UkoeHB\_\></strong> ArticMine: I think ultimately the extra field is useful when/if hard forks are no longer feasible.  
<strong>\<sarang\></strong> At the very least, enforcing ordering as UkoeHB\_ listed in their issue would help a lot of this  
<strong>\<sarang\></strong> certainly not all cases though  
<strong>\<UkoeHB\_\></strong> Imagine if Janus attack wasn't discovered until after hard forks stopped happening. We'd be in Bitcoin's situation of absolute chaos  
<strong>\<UkoeHB\_\></strong> (i.e. if no extra field for wiggle room)  
<strong>\<ArticMine\></strong> How would extra help  
<strong>\<Isthmus\></strong> Geez, if that happened I think the issue is ossification  
<strong>\<UkoeHB\_\></strong> wallets can implement janus mitigation on their own, since it's technically unverifiable anyway  
<strong>\<Isthmus\></strong> I'd like to proactively avoid a situation like that by keeping an agile codebase, not having an anything-goes tx\_extra field  
<strong>\<Isthmus\></strong> Anyways, lots of different pros &amp; cons to consider for each possibility  
<strong>\<sarang\></strong> The question at this point, I think, is to decide whether doing order enforcement (e.g. TLV) is something that a develop wishes to take on  
<strong>\<sarang\></strong> Which ties in to whether enforcement of a consistent Janus mitigation is desirable (I think yes, it is)  
<strong>\<UkoeHB\_\></strong> After next gen tx protocol gets implemented, I imagine the stuff that can go in a hard fork will drop off quite a bit. Rather than losing the ability to make hard forks, we might just run out of hard forks to make. Once the expectation of making periodic hard forks fades away, subsequent hard forks will become much more difficult (also the case if adoption rises concurrently).  
<strong>\<sarang\></strong> Network upgrades also have the probable advantage of encouraging client upgrades  
<strong>\<Isthmus\></strong> Yeah "we might just run out of hard forks to make" is a different situation from encountering an issue (e.g. Janus) and not forking  
<strong>\<sarang\></strong> which provide other non-consensus fixes and benefits  
<strong>\<Isthmus\></strong> Regardless, let's separate the metadata question (should we enforce ordered TLV) from feature questions (should we have a memo field)  
<strong>\<sarang\></strong> Well, TLV enforcement has a big effect on non-standard data, since it requires a stated type  
<strong>\<UkoeHB\_\></strong> I did make pseudo code for enforced sorted TLV, about 200lines  
<strong>\<sarang\></strong> yes  
<strong>\<sarang\></strong> But I mean that the features and the layout enforcement are closely intertwined here  
<strong>\<UkoeHB\_\></strong> Current code already mostly does sorted tlv by default  
<strong>\<UkoeHB\_\></strong> So all that needs to change is in tx validation  
<strong>\<Isthmus\></strong>  
<strong>\<atoc\></strong> nice  
<strong>\<sarang\></strong> OK, so I think what should be brought up in -dev is a well-considered position for 3 things related to extra  
<strong>\<sarang\></strong> 1. Decision on TLV enforcement, and responsibility for implementation  
<strong>\<atoc\></strong> koe, what's your github  
<strong>\<sarang\></strong> 2. Decision on Janus mitigation, and implementation  
<strong>\<sarang\></strong> 3. Musings on the new encrypted-memo idea  
<strong>\<UkoeHB\_\></strong> atoc <https://github.com/monero-project/research-lab/issues/61>  
<strong>\<sarang\></strong> My position is 1: yes, 2: yes, 3: not unless enforced uniformly (and then it runs up against ePIDs)  
<strong>\<Isthmus\></strong> 1: agree, 2: agree, 3: agree  
<strong>\<sarang\></strong> Anyway, good things to consider here  
<strong>\<gingeropolous\></strong> is the janus mitigation the thing with the subaddresses?  
<strong>\<sarang\></strong> Yes  
<strong>\<UkoeHB\_\></strong> Janus <https://github.com/monero-project/research-lab/issues/62>  
<strong>\<sarang\></strong> Enforcing a mitigation has the added advantage of making the number of tx pubkeys uniform  
<strong>\<Isthmus\></strong> \!\!\!  
<strong>\<Isthmus\></strong> yesplz  
<strong>\<gingeropolous\></strong> ima just throw it out there to play devils advocate, dunno if its been stated before. What about reverting to not having subaddresses?  
<strong>\<sarang\></strong> So you have one Janus-specific tx pubkey per transaction, and a separate additional pubkey per output  
<strong>\<fuwa\></strong> is it possible to replace tx extra completely with memo, so you don't need to sort anything  
<strong>\<sarang\></strong> You'd need to remove all non-recipient-specific data from memo  
<strong>\<sarang\></strong> Which IIRC moneromooo said would be a significant engineering effort  
<strong>\<sarang\></strong> Extra isn't an inherent problem if uniformity is reasonably enforced  
<strong>\<Isthmus\></strong> Oh, I was wondering something actually  
<strong>\<Isthmus\></strong> Suppose we decide that each transaction should contain X, Y, and Z  
<strong>\<UkoeHB\_\></strong> gingeropolous: then Janus would no longer be a problem. That's about it afaik  
<strong>\<Isthmus\></strong> What's the performance difference between having 3 separate fields versus having 1 field with 3 enforced objects  
<strong>\<sarang\></strong> That's a good question, and I'm not sure  
<strong>\<gingeropolous\></strong> right. so i guess the underlying question is whether subaddresses are worth it.  
<strong>\<sarang\></strong> The scanning benefit is huge for large sets of addresses  
<strong>\<sarang\></strong> Hash lookups are much faster than doing multiple scans of all transactions per address  
<strong>\<sarang\></strong> and Janus checks are only needed for transactions that are already identified as being destined for you  
<strong>\<sarang\></strong> (and those checks are quite fast anyway)  
<strong>\<sarang\></strong> Also note that MLSAG -\> CLSAG drops average tx size by 600 bytes already  
<strong>\<sarang\></strong> s/average/typical  
<strong>\<ArticMine\></strong> Like 2 in 2 out  
<strong>\<sarang\></strong> Yes, a 2-2 tx drops already from \~2.5 kB to \~1.9 kB  
<strong>\<sarang\></strong> So Janus mitigation adds something like about 64 bytes back in  
<strong>\<sarang\></strong> (more for multi-output)  
<strong>\<sarang\></strong> Meaning there's already plenty of wiggle room  
<strong>\<gingeropolous\></strong> well here's hoping its the last mitigation for subaddresses.  
<strong>\<atoc\></strong> that's a pretty good drop  
<strong>\<ArticMine\></strong> We can increase the ring size  
<strong>\<UkoeHB\_\></strong> meeting is getting toward the end, so Ill add my update here: ztm2 should be ready to publish this weekend, I'm finishing up my last proofreading atm  
<strong>\<sarang\></strong> UkoeHB\_: great\!  
<strong>\<UkoeHB\_\></strong> might take a bit for getmonero to update though, so we will see when I post about it  
<strong>\<atoc\></strong> koe - i sent you an email but to reiterate it's looking really good  
<strong>\<UkoeHB\_\></strong> yeah saw that :)  
<strong>\<sarang\></strong> Since the hour is indeed almost up, does anyone else wish to share any topics of interest?  
<strong>\<Isthmus\></strong> <https://www.reddit.com/r/Monero/comments/fnhm6u/maam\_monero\_ask\_anything\_monday\_march\_23\_2020/flbbt45?utm\_source=share&utm\_medium=web2x>  
<strong>\<Isthmus\></strong> ^ thoughts?  
<strong>\<Isthmus\></strong> I'm looking for projects for Fellows to work on, wondering if that seems like a good candidate  
<strong>\<sarang\></strong> That sounds like a question for -dev or -gui TBH\!  
<strong>\<Isthmus\></strong> I could also have one of the software engineers implement ordered TLV if -dev wants somebody else to tackle it  
<strong>\<Isthmus\></strong> Oh yea, good point  
<strong>\<Isthmus\></strong> Any wish list projects for MRL? I have 2 software engineers, 1 mathematician, and some data scientists that are open to working on Monero stuff  
<strong>\<atoc\></strong> Isthmus this seems good. i am willing to help but probably can't commit too much atm  
<strong>\<sarang\></strong> Isthmus: perhaps pop over to -dev after meeting and let the channel know that a Fellow might be able to tackle TLV  
<strong>\<sarang\></strong> see what the responses are  
<strong>\<sarang\></strong> I bet moneromooo will have better knowledge of the effects that parsing would have on performance overall  
<strong>\<UkoeHB\_\></strong> well this never got much traction but Im still a fan <https://github.com/monero-project/research-lab/issues/59> could be a lot of work idk  
<strong>\<sarang\></strong> Isthmus: I know this important PR needed review... <https://github.com/monero-project/supercop/pull/3>  
<strong>\<sarang\></strong> and if any Fellows have sufficient interest, the new CLSAG security model in the paper could use some eyes  
<strong>\<sarang\></strong> Anyway, let's start to wrap up  
<strong>\<ArticMine\></strong> I'll cover the fee, penalty and median proposal in the next meeting. By then I'll have most of this finalized  
<strong>\<sarang\></strong> Any ACTION ITEMS to share?  
<strong>\<sarang\></strong> Great ArticMine  
<strong>\<atoc\></strong> @sarang i'll probably ping you tomorrow to go over some zkp ideas for atomic swap  
<strong>\<sarang\></strong> I'll be doing some work on an older preprint, reviewing some ideas in a draft preprint that were sent to me by another researcher, and returning to some Triptych code  
<strong>\<UkoeHB\_\></strong> there are two other big projects: fully-formed audit functionality, and extensive updates to multisig; mentioned those to TheCharlatan but they really are beasts I expect  
<strong>\<atoc\></strong> i have some resources i'd like to share  
<strong>\<sarang\></strong> for sure  
<strong>\<Isthmus\></strong> We can close up the meeting, but I'm curious later if anybody has speculation around what's going on with <https://xmrchain.net/search?value=f6cff1edd1a7861ed13d494dd4ae7c4a7f42b5c3bf91457310d2166722c1316f>  
<strong>\<Isthmus\></strong> It has an unknown tag type, and the length is recorded incorrectly  
<strong>\<UkoeHB\_\></strong> are you sure it's a length and not a value byte?  
<strong>\<Isthmus\></strong> Not sure, that's why I'm asking  
<strong>\<sarang\></strong> All right, let's go ahead and adjourn for timing purposes, but discussions can of course continue  
<strong>\<sarang\></strong> Thanks to everyone for attending\!  
<strong>\<sarang\></strong> Logs posted shortly on the GitHub agenda issue
