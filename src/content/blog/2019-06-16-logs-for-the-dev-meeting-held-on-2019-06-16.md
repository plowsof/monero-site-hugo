---
title: Overview and Logs for the Dev Meeting Held on 2019-06-16
summary: Development status, Code & ticket discussion, payment ID, CLSAG, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<rehrar\></strong> Meeting time\! Who all is here?  
<strong>\<rbrunner\></strong> Hi all  
<strong>\<hyc\></strong> hey  
<strong>\<fullmetalScience\></strong> Hi  
<strong>\<dEBRUYNE\></strong> Here  
<strong>\<rehrar\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<hyc\></strong> v0.14.1.0 is out in the world  
<strong>\<rbrunner\></strong> CLI so far, yes …  
<strong>\<rehrar\></strong> so I hear. And I even hear deterministic builds are doing their thing ok  
<strong>\<jtgrassie\></strong> hi  
<strong>\<hyc\></strong> they are being deterministic now, yes  
<strong>\<dEBRUYNE\></strong> Some small improvements still for deterministic builds, but I’d argue it was a excellent first round :P  
<strong>\<rehrar\></strong> nothing left to be done on the CLI front then for this little release?  
<strong>\<rehrar\></strong> but then also, looking to the next release, what’s going on, do we know?  
<strong>\<rehrar\></strong> for 0.15  
<strong>\<rbrunner\></strong> little release is actually a pretty big release  
<strong>\<rbrunner\></strong> feature-wise  
<strong>\<hyc\></strong> there may be a few small bug reports for v0.14.1. might want a v0.14.1.1  
<strong>\<dEBRUYNE\></strong> I think the intention was to release it way earlier this time, because we can already add all the consensus changes early on  
<strong>\<dEBRUYNE\></strong> Unless CLSAG is also going to go in I guess  
<strong>\<moneromooo\></strong> It’ll depend on whether it gets a review I think.  
<strong>\<hyc\></strong> Is 0.15 the October release?  
<strong>\<moneromooo\></strong> (in time)  
<strong>\<rehrar\></strong> sarang suraeNoether, can you speak to the potential timeline of review for CLSAG?  
<strong>\<dEBRUYNE\></strong> hyc: Yeah  
<strong>\<rehrar\></strong> dsc\_ selsta dEBRUYNE anything from GUI?  
<strong>\<dEBRUYNE\></strong> hyc: So we have about four months left I guess  
<strong>\<dEBRUYNE\></strong> GUI v0.14.1.0 has been tagged and fluffypony is working on the builds  
<strong>\<hyc\></strong> so when are we expecting to freeze 0.15 ?  
<strong>\<dEBRUYNE\></strong> rehrar: Some new stuff for the GUI:  
<strong>\<dEBRUYNE\></strong> - White theme  
<strong>\<dEBRUYNE\></strong> - Addressbook redesign  
<strong>\<dEBRUYNE\></strong> - History redesign  
<strong>\<dEBRUYNE\></strong> - Trezor and Ledger Nano X support  
<strong>\<dEBRUYNE\></strong> - Fiat price conversion  
<strong>\<dEBRUYNE\></strong> - macOS fullscreen support  
<strong>\<dEBRUYNE\></strong> Also an update checker + Hindi translation  
<strong>\<dEBRUYNE\></strong> And xiphon did a lot of work on improving the communication between the (integrated) daemon and the GUI  
<strong>\<rehrar\></strong> oooooh. Looks juicy. thanks dEBRUYNE  
<strong>\<rehrar\></strong> so it’ll be faster?  
<strong>\<dEBRUYNE\></strong> hyc: I guess that is going to depend on whether we want to add CLSAG. If not, we could do a first 0.15 release after RandomX has been merged (e.g. in August)  
<strong>\<dEBRUYNE\></strong> And then another point release a month before the fork  
<strong>\<dEBRUYNE\></strong> rehrar: Yes and less ‘laggy’  
<strong>\<moneromooo\></strong> Does someone want to review the share-rpc (pay for RPC service) branch ? :)  
<strong>\<moneromooo\></strong> It goes well with a CPU friendly PoW…  
<strong>\<hyc\></strong> I may take a look after I get back from konferenco  
<strong>\<rehrar\></strong> I assume we don’t have any core team here?  
<strong>\<moneromooo\></strong> \\o/  
<strong>\<rehrar\></strong> but if not, we can still kind of talk about Payment ID stuff  
<strong>\<dEBRUYNE\></strong> Btw moneromooo, you already coded up a rough implementation of CLSAG right?  
<strong>\<rehrar\></strong> which is number 4.  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<moneromooo\></strong> Well, sarang did, and I plugged it in.  
<strong>\<dEBRUYNE\></strong> rehrar: That’s kind of my fault, I forgot to ping them in advance (I did earlier today, but probably too late :/)  
<strong>\<dEBRUYNE\></strong> Anyway, we can still discuss it, as there is plenty of opinions on the meta ticket  
<strong>\<hyc\></strong> rough? is it something you’d deploy for real, and what we’d submit to auditors to review?  
<strong>\<moneromooo\></strong> Both, assuming the review passes.  
<strong>\<hyc\></strong> ok  
<strong>\<dEBRUYNE\></strong> hyc: With ‘rough’ I kind of meant that, as far as I could see, it wasn’t fully finished yet  
<strong>\<moneromooo\></strong> If you have suggestions for changes, go for it.  
<strong>\<dEBRUYNE\></strong> moneromooo: I just thought it wasn’t fully finished yet, if it is I stand corrected :-P  
<strong>\<moneromooo\></strong> Well, I don’t know what you’ve seen before, but AFAIK it is finished now, unless comments.  
<strong>\<rehrar\></strong> alright, let’s discuss the whole PID thing then, if we can, with the people represented here giving their opinions as well.  
<strong>\<dEBRUYNE\></strong> I see, thanks for clarifying  
<strong>\<rehrar\></strong> dEBRUYNE: is correct that actually many of core had made their opinions known on the meta discussion  
<strong>\<rehrar\></strong> can you link that real fast dEBRUYNE ?  
<strong>\<moneromooo\></strong> Did any exchange/merchant switch from long payment ids since… half a year ago, say ?  
<strong>\<dEBRUYNE\></strong> I think some smaller ones did, but the big ones (Bittrex, Bitfinex, Binance) did not  
<strong>\<dEBRUYNE\></strong> rehrar: sure  
<strong>\<dEBRUYNE\></strong> smooth: <https://github.com/monero-project/meta/issues/356#issuecomment-500187077> &amp; <https://github.com/monero-project/meta/issues/356#issuecomment-501168062>  
<strong>\<dEBRUYNE\></strong> binaryFate: <https://github.com/monero-project/meta/issues/356#issuecomment-499968785>  
<strong>\<rehrar\></strong> at the end of the thread in particular, ArticMine brings up his revised opinion about potentially looking at removing tx\_extra  
<strong>\<dEBRUYNE\></strong> ArticMine: <https://github.com/monero-project/meta/issues/356#issuecomment-501347185>  
<strong>\<ErCiccione\[m\]\></strong> some big ones like kraken already use subadresses moneromooo, iirc somebody as a list of the status of some exhanges and services  
<strong>\<dEBRUYNE\></strong> <https://github.com/monero-project/meta/issues/356#issuecomment-499936642> &amp; <https://github.com/monero-project/meta/issues/356#issuecomment-499948904>  
<strong>\<rbrunner\></strong> Yeah, but it would be interesting to see whether somebody \*switched\*  
<strong>\<ErCiccione\[m\]\></strong> maybe sgp\_?  
<strong>\<dEBRUYNE\></strong> rehrar: As far as I can see, people don’t like temporary banning payment IDs by parsing tx\_extra  
<strong>\<dEBRUYNE\></strong> As it is essentially a slippery slope  
<strong>\<dEBRUYNE\></strong> So that leaves us with (i) Phase them out by removing all support from the official software or (ii) banning the tx\_extra field entirely  
<strong>\<rehrar\></strong> dEBRUYNE: agreed. I see that reflected as well.  
<strong>\<rehrar\></strong> yes ^  
<strong>\<sgp\_\></strong> I had a list in January, not sure if it is up-to-date anymore  
<strong>\<rehrar\></strong> can I ask people to give opinions on the above two options presented by dEBRUYNE?  
<strong>\<dEBRUYNE\></strong> rbrunner: The announcement has only been up for 10 days though  
<strong>\<rehrar\></strong> I particularly want to hear arguments for or against removing tx\_extra  
<strong>\<rbrunner\></strong> dEBRUYNE: Yes, saw it, but we make noises a lot longer :)  
<strong>\<sgp\_\></strong> rehrar: I have personally head some arguments against removing tx\_extra from legacy financial services  
<strong>\<dEBRUYNE\></strong> The arguments for are, for example, (i) a clean and definitive way to phase out long payment IDs and (ii) improves fungibility  
<strong>\<sgp\_\></strong> Zcash has an encrypted memo field that they use to claim support for many traditional remittance services  
<strong>\<rehrar\></strong> dEBRUYNE: I think (ii) is kind of massive, given that’s our shtick  
<strong>\<dEBRUYNE\></strong> moneromooo: I vaguely remember you working on some kind of encrypted memo field too, is that correct?  
<strong>\<sgp\_\></strong> ftr I only support parsing for current payment ID behavior to force services to switch. I am not for the removal of tx\_extra in its entirety  
<strong>\<dsc\_\></strong> \< rehrar\> dsc\_ selsta dEBRUYNE anything from GUI? \<== Past 4 days been working on development related tooling to support QML development, this is unrelated to my CCS  
<strong>\<moneromooo\></strong> I have a partial patch for this somewhere. I stopped because it’s a bit chicken and egg since you need tx tx key to decrypt the rest and I was not sure what to do yet.  
<strong>\<rbrunner\></strong> Likewise. Erasing tx\_extra completey is going overboard somehow for me  
<strong>\<rehrar\></strong> sgp\_ rbrunner are there any other reasons for keeping it around?  
<strong>\<sgp\_\></strong> rehrar: mostly flexibility  
<strong>\<dEBRUYNE\></strong> sgp\_: How is that field used exactly in that context?  
<strong>\<rehrar\></strong> and is there a good reason why something like it can’t be kept track of externally via third party, and why it needs to be on the base currency?  
<strong>\<rbrunner\></strong> Up to a point, it should be possible for the users of the currency to do like they want … to a certain degree, with a single field  
<strong>\<sgp\_\></strong> See “what people will do with this” <https://electriccoin.co/blog/encrypted-memo-field/>  
<strong>\<dEBRUYNE\></strong> On the other hand, do we want to give people the ability to potentially hurt privacy of other participants on the network?  
<strong>\<rbrunner\></strong> And who knows, maybe one day we will have some emergency and want to put something in there ourselves. A currency with exactly zero flexibility … I don’t know  
<strong>\<sgp\_\></strong> When I was doing payment ID research back in January, someone specifically asked that tx\_extra remained for this flexibility  
<strong>\<rehrar\></strong> let me look at the dollar. Does the dollar have this field?  
<strong>\<rbrunner\></strong> Marking one’s own txs is quite a small privacy risks for others, if you ask me  
<strong>\<rehrar\></strong> or are memos and stuff kept and integrated in dollar management software?  
<strong>\<rbrunner\></strong> Yes, bank transfers have something like a short memo, right?  
<strong>\<sgp\_\></strong> rehrar: I’m not an expert here, I’m just relaying some information to say the flexibility could be useful  
<strong>\<rehrar\></strong> rbrunner: sure, but that isn’t built into the dollar bill itself  
<strong>\<rehrar\></strong> which is my point  
<strong>\<rehrar\></strong> is this necessary as a part of Monero itself? Or can monero management software be built to have these memos?  
<strong>\<rehrar\></strong> My initial thoughts are the latter  
<strong>\<rbrunner\></strong> Hmm, I think that comparison limps a little ..  
<strong>\<sgp\_\></strong> my personal opinion is that the flexibility shouldn’t be removed unless there’s a problem, and we should try to address that more head-on. If we already tried to kill payment IDs and they used a different format in tx\_extra, that would be one thing. But we’re in a situation now where we are trying it for the first time and I think a simple parsing would be successful at making people switch over  
<strong>\<rbrunner\></strong> Uh, no, several incompatible memo transfer systems will crop up for sure  
<strong>\<rbrunner\></strong> Why not fill \*every\* tx\_extra with fake data, if that’s such a problem?  
<strong>\<rehrar\></strong> hyc, dEBRUYNE, moneromooo? care to chime in at all?  
<strong>\<moneromooo\></strong> Not really.  
<strong>\<sgp\_\></strong> rbrunner: that’s basically what zcash does with the encrypted memo field  
<strong>\<moneromooo\></strong> We’ve gone over that enough for me.  
<strong>\<rbrunner\></strong> Yes, and we now with the short payment ids, right?  
<strong>\<hyc\></strong> as a protocol guy I tend to favor having extensiblity  
<strong>\<hyc\></strong> there’s certainly a risk of dumping tons of spam into the chain with a totally open-ended extention field  
<strong>\<hyc\></strong> might want to constrain it to “any individual tx\_extra can’t be greater than N bytes” etc  
<strong>\<moneromooo\></strong> That could be made to weigh extra for the fee fwiw.  
<strong>\<hyc\></strong> N=512, 1024, dunno  
<strong>\<rehrar\></strong> isn’t that what minergate does when they find a block or is that somethign different?  
<strong>\<rehrar\></strong> I recall somebody saying they add a bunch of weird data  
<strong>\<moneromooo\></strong> They did.  
<strong>\<dEBRUYNE\></strong> sgp\_: Lots of people are opposed to parsing though, I don’t think that is going to find consensus  
<strong>\<rehrar\></strong> alright well, anything else to say on this topic?  
<strong>\<rehrar\></strong> we can continue in the issue  
<strong>\<dEBRUYNE\></strong> rehrar: In general I am kind of ambivalent, I think we can achieve a lot by removing all functionality from the software  
<strong>\<sgp\_\></strong> dEBRUYNE: I understand, I just personally think there is some middle ground that doesn’t need to include full tx\_extra. I think we’ve exhausted this topic for now  
<strong>\<dEBRUYNE\></strong> Currently, we removed it, but it is easily to reenable  
<strong>\<sgp\_\></strong> \*full tx\_extra removal  
<strong>\<luigi1111\></strong> instead of command line, move to compile time  
<strong>\<dEBRUYNE\></strong> Next step could be that they need to add code theirselves for payment ID support  
<strong>\<hyc\></strong> VARIANT\_TAG(binary\_archive, cryptonote::tx\_extra\_merge\_mining\_tag, TX\_EXTRA\_MERGE\_MINING\_TAG);  
<strong>\<rbrunner\></strong> But the code would be missing at the people’s systems, where the exchanges could not get it in again  
<strong>\<hyc\></strong> if tx\_extra is needed to support merge mining then removing it is kinda out of the question, no?  
<strong>\<dEBRUYNE\></strong> rbrunner: Yes, that as well  
<strong>\<dEBRUYNE\></strong> But there may be some third party wallets that retain support  
<strong>\<rbrunner\></strong> As long as they don’t threaten to fork and come up with MoneroLPID (long payment id variant) …  
<strong>\<rehrar\></strong> alright, let’s go ahead and move along  
<strong>\<rehrar\></strong> there is also discussion blocked out for this meeting  
<strong>\<rehrar\></strong> but we talked about it a bit, and I don’t see any MRL people here  
<strong>\<hyc\></strong> seems like there are a lot of current valid uses for tx\_extra, so you can’t remove it outright  
<strong>\<rehrar\></strong> still want to discuss, or table?  
<strong>\<hyc\></strong> CLSAG can wait for next meeting I think  
<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> any additional items?  
<strong>\<hyc\></strong> surae is busy taking care of konferenco now anyway  
<strong>\<rehrar\></strong> code/ticket discussion?  
<strong>\<moneromooo\></strong> Anyone else than hyc wants to review share-rpc ? :)  
<strong>\<moneromooo\></strong> Or even use it as backend to add pay-for-downloading-torrents or whatever.  
<strong>\<rehrar\></strong> I lack the skills :)  
<strong>\<rehrar\></strong> \*:(  
<strong>\<rehrar\></strong> alright everyone, I think we can call it here  
<strong>\<rehrar\></strong> two weeks from now?  
<strong>\<rehrar\></strong> thanks for coming\! have a good couple weeks.
