---
title: Overview and Logs for the Dev Meeting Held on 2019-08-11
summary: Development status, Code & ticket discussion, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / dEBRUYNE
---

# Logs

<strong>\<dEBRUYNE\></strong> so dev meeting? :P  
<strong>\<jtgrassie\></strong> hi\!  
<strong>\<dEBRUYNE\></strong> Who's here? hyc, vtnerd, sarang, suraeNoether, moneromooo, jtgrassie, luigi1111, fluffypony  
<strong>\<rbrunner\></strong> Certainly\!  
<strong>\<dEBRUYNE\></strong> Probably forgetting a lot of people  
<strong>\<dEBRUYNE\></strong> Guess it's vacation time for a lot of people :-P  
<strong>\<Guest16177\></strong> here more or less  
<strong>\<dEBRUYNE\></strong> So what should we discuss?  
<strong>\<kinghat\></strong> o/  
<strong>\<jtgrassie\></strong> testnet-\>rx ?  
<strong>\<jtgrassie\></strong> as in when can we fork testnet to RandomX  
<strong>\<rbrunner\></strong> Maybe that would be good with moneromooo back from "frolocking amoung cows" or so  
<strong>\<sarang\></strong> Here, live from def con  
<strong>\<rbrunner\></strong> Def con party then? :)  
<strong>\<sarang\></strong> Very good attendance at the def con village this weekend, for sure  
<strong>\<kinghat\></strong> even being off the beaten path?  
<strong>\<rbrunner\></strong> Anyway, concerning RandomX: The reviews are all through, right?  
<strong>\<sarang\></strong> Yes, for sure  
<strong>\<sarang\></strong> Having free badges was a huge help  
<strong>\<vtnerd\_\_\></strong> ... present (too busy too lock at clock) ...  
<strong>\<sarang\></strong> <https://ostif.org/four-audits-of-randomx-for-monero-and-arweave-have-been-completed-results/>  
<strong>\<dEBRUYNE\></strong> I think what is left is to merge the RandomX PR from hyc and set a testnet fork date  
<strong>\<hyc\></strong> hey sorry, was afk. but yes  
<strong>\<rbrunner\></strong> Yes, nice to see all those "fixed" and "solved"  
<strong>\<dEBRUYNE\></strong> As a side note, thoughts on releasing 0.15 binaries in early september already?  
<strong>\<dEBRUYNE\></strong> Or would that be too short  
<strong>\<hyc\></strong> would probably need mooo's opinion there  
<strong>\<hyc\></strong> what's our outstanding PR count look like anyway?  
<strong>\<dEBRUYNE\></strong> I am thinking that we have freedom to release early as we do not have any last minute consensus changes  
<strong>\<dEBRUYNE\></strong> Quite a lot, but I am working with luigi to get the queue down :P  
<strong>\<dEBRUYNE\></strong> luigi &amp; mooo\*  
<strong>\<hyc\></strong> cool  
<strong>\<hyc\></strong> a mid-Sept release date sounds plausible. basically 1 month from now?  
<strong>\<dEBRUYNE\></strong> Sounds like a decent target  
<strong>\<dEBRUYNE\></strong> It also gives services, users etc. a larger time frame to prepare  
<strong>\<dEBRUYNE\></strong> The forks with binaries 1 week in advance were admittedly quite hectic :-P  
<strong>\<hyc\></strong> so we would expect testnet to switch to randomx on that mid-Sept date  
<strong>\<hyc\></strong> on or around...  
<strong>\<jtgrassie\></strong> it would be nice to have testnet fork a little earlier to randomx imo  
<strong>\<sarang\></strong> There was some issue with another project's switch to RandomX, right?  
<strong>\<sarang\></strong> Was that an issue with a miner implementation?  
<strong>\<hyc\></strong> Loki. xmrig bug  
<strong>\<hyc\></strong> there are no issues with the monerod integration  
<strong>\<dEBRUYNE\></strong> What was the effect of the bug?  
<strong>\<dEBRUYNE\></strong> (in the miner that is)  
<strong>\<hyc\></strong> jtgrassie: so, switch over testnet earlier, but on self-compiled binaries maybe?  
<strong>\<hyc\></strong> dEBRUYNE: the miner didn't reinitialize the dataset when seed epoch changed  
<strong>\<jtgrassie\></strong> yes  
<strong>\<hyc\></strong> all blocks mined after that point were invalid, rejected by daemons  
<strong>\<hyc\></strong> restarting the miner would get it working until the next epoch  
<strong>\<hyc\></strong> but it was patched pretty quickly  
<strong>\<dEBRUYNE\></strong> Ah I see, so part of the network hashrate basically disappeared because they were mining invalid blocks  
<strong>\<hyc\></strong> yes  
<strong>\<rbrunner\></strong> So will those mid-September binaries now be the ones that do not support \*long\* payment id's anymore? I lost a little the overview  
<strong>\<hyc\></strong> no idea, haven't followed payment ID discussion  
<strong>\<dEBRUYNE\></strong> needmonero90: did Binance provide you with a timeline?  
<strong>\<needmonero90\></strong> <https://usercontent.irccloud-cdn.com/file/IA4ai9LF/Screenshot\_20190811-102559\_Telegram.jpg>  
<strong>\<needmonero90\></strong> <https://usercontent.irccloud-cdn.com/file/eo22z2BE/Screenshot\_20190811-102608\_Telegram.jpg>  
<strong>\<needmonero90\></strong> <https://usercontent.irccloud-cdn.com/file/YcXsymNo/Screenshot\_20190811-102612\_Telegram.jpg>  
<strong>\<needmonero90\></strong> There was the latest.  
<strong>\<needmonero90\></strong> I can upload the full convo to pastebin if you want it  
<strong>\<sarang\></strong> neat  
<strong>\<rbrunner\></strong> Yeah, sounds good  
<strong>\<tat\></strong> moneromooo: are there any infos on which exchanges would be able to receive/send to subaddresses after the mid September fork?  
<strong>\<tat\></strong> sorry i meant needmonero90  
<strong>\<dEBRUYNE\></strong> Anyone got contacts at bittrex or bitfinex? I tried reaching out to them on reddit, but did not get a response  
<strong>\<needmonero90\></strong> Bittrex can be contacted over their slack iirc  
<strong>\<needmonero90\></strong> At least a year and a half ago that was the case.  
<strong>\<rbrunner\></strong> Well, they also could contact \*us\*, at least in theory :)  
<strong>\<tat\></strong> would be good to create a list, i guess some exchanges will be concerned if removing the ability to use payment ids cribles them to get transactions from other exchanges  
<strong>\<needmonero90\></strong> Tat: I just took up the discussion with binance because someone had to do it, I don't have the list of other exchanges.  
<strong>\<tat\></strong> needmonero90: thx  
<strong>\<needmonero90\></strong> I will happily talk to whoever if we get a contact  
<strong>\<needmonero90\></strong> Just ping me their details  
<strong>\<bibble\></strong> Kraken important  
<strong>\<needmonero90\></strong> Kraken will be fine  
<strong>\<bibble\></strong> oh, great :)  
<strong>\<needmonero90\></strong> Least of our concerns on the exchange front  
<strong>\<tat\></strong> i think if at least 3-5 big exchanges would move to subaddresses, that would put some pressure on the rest and they probably follow within a reasonable timeframe  
<strong>\<rbrunner\></strong> Well, "reasonable timeframe" is almost over, with hardfork in mid-October, wouldn't you say?  
<strong>\<rbrunner\></strong> Maybe they are pretty quiet because they don't want let people look into their cards ...  
<strong>\<tat\></strong> rbrunner: we are talking of not using long payment id's anymore, integrated addresses would still work i guess, so most of the exchanges will still be able to work with that as is  
<strong>\<rbrunner\></strong> Ah, ok, right, misunderstood you  
<strong>\<dEBRUYNE\></strong> The most important thing is to get them off long payment IDs imo  
<strong>\<rbrunner\></strong> Certainly, if we don't support them anymore in 2 months  
<strong>\<hyc\></strong> so these exchanges aren't supporting integrated addrs yet?  
<strong>\<tat\></strong> hyc: it depends, i think poloniex uses integrated addresses, bitfinex uses 64 char payent id's  
<strong>\<hyc\></strong> yes, polo uses integrated  
<strong>\<tat\></strong> dEBRUYNE: do you think receiving of transactions with long payment id's will be still supported by the wallet  
<strong>\<rbrunner\></strong> Who would send those, and how?  
<strong>\<tat\></strong> i mean in theory you need to be able to resync, so to prevent that, the wallet would have to ignore all long payment id's from block height X  
<strong>\<rbrunner\></strong> Yes, the code is full of such switches "Starting from height x stop to do X and start do to Y"  
<strong>\<rbrunner\></strong> Daily business, so to say  
<strong>\<tat\></strong> rbrunner: is there really only one source for code of the monero wallet, is there any wallet implementation that isn't using monero c++ wallet core?  
<strong>\<rbrunner\></strong> I would guess that starting with the fork height the long payment just does not get decoded / delivered to the wallet anymore  
<strong>\<rbrunner\></strong> tat: Not sure about MyMonero's code  
<strong>\<moneromooo\></strong> I'm happy with testnet switching to randomx as soon as a patch is made fwiw.  
<strong>\<rbrunner\></strong> Otherwise I think it's pretty much a monoculture  
<strong>\<moneromooo\></strong> Pony's the one to get on board since seed nodes and his mining node will need to be updated then.  
<strong>\<tat\></strong> i mean if there is any wallet that will still send with long payment id's, it wont be too bad, since funds will still arrive but if you rely on that id to track incoming setlements you are screwed  
<strong>\<moneromooo\></strong> The wallet will ignore the payment id IIRC. It'll still get the money of course.  
<strong>\<dEBRUYNE\></strong> hyc: The big ones are binance, bittrex, bitfinex  
<strong>\<dEBRUYNE\></strong> needmonero90 is currently working with binance, I will try to get ahold of the other two somehow  
<strong>\<hyc\></strong> moneromooo: all that's needed before merging the existing randomX integration patch, then, is setting the block height for the testnet fork  
<strong>\<moneromooo\></strong> IIRC I put a command line switch somehwere to enable something there.  
<strong>\<moneromooo\></strong> (about payment id decoding)  
<strong>\<tat\></strong> i would say if an exchange is still using long payment id's and he switches within one month, and he is not able to process long payment id's anymore he will have two years of still receiving to those long payment'id since not all users get that change immediately  
<strong>\<hyc\></strong> they should've switched to integrated addrs 2 years ago ...  
<strong>\<tat\></strong> i think a command line switch would be pretty fair, with the emphasis on this feature will be deprecated, that would send the right signal  
<strong>\<rbrunner\></strong> What do you mean with "not all users get that change immediately"? Your software will stop to work after the hardfork, no?  
<strong>\<hyc\></strong> and it's their own obligation to notify their users if deposit addresses change  
<strong>\<rbrunner\></strong> Maybe I misunderstand, but this is not Bitcoin where the move to SegWit takes 5 years or so ...  
<strong>\<moneromooo\></strong> The wallet has been warning it's deprecated for a while.  
<strong>\<tat\></strong> hyc: so you are full positive that sending out with long payment ids will be impossible after the next hard fork  
<strong>\<moneromooo\></strong> It will likely be still possible.  
<strong>\<jtgrassie\></strong> fwiw, we have been stating long payment ids are deprcated for ages now. they are a problem for privacy and IMO removed asap.  
<strong>\<moneromooo\></strong> But if several large exchanges still use long payment ids close to the fork, I might be convinced to consensus ban them.  
<strong>\<rbrunner\></strong> "Close to the fork" ... being ... about today :)  
<strong>\<moneromooo\></strong> Oh.  
<strong>\<needmonero90\></strong> To elaborate, using them has required going to advanced settings and toggling a box saying "don't do this" before you could send for ages.  
<strong>\<moneromooo\></strong> Is there fork soon ? I missed the talk.  
<strong>\<hyc\></strong> mid-OCtober presumably  
<strong>\<moneromooo\></strong> We're liky july, no ?  
<strong>\<rbrunner\></strong> No, I mean, as far as big projects are concerned, 2 months pass in a blink of an eye  
<strong>\<moneromooo\></strong> August. Close enough.  
<strong>\<moneromooo\></strong> OK, true.  
<strong>\<needmonero90\></strong> I did give binance until October, so it would be nice not to go faster than that  
<strong>\<moneromooo\></strong> So "binance, bittrex, bitfinex" sounds like a lot indeed.  
<strong>\<needmonero90\></strong> Or I'll have to backpedal and apologize and politick  
<strong>\<tat\></strong> i totally support that point, but for the poor souls that use still long payment ids and continue to receive payments, after the fork with long payment ids, since some users/exchanges will still do so it will be case for customer suport every single time  
<strong>\<rbrunner\></strong> "Possible" does not mean "easy to do". Maybe would need your own doctored self-compiled software  
<strong>\<jtgrassie\></strong> exchanges and users won't ever stop using payment ids while they are still possible.  
<strong>\<rbrunner\></strong> Which would work because \*consensus\* would still allow the long id's  
<strong>\<vtnerd\_\_\></strong> to the above: mymonero is indeed not using the monero core wallet - it simply cannot actually  
<strong>\<vtnerd\_\_\></strong> the light wallet server and openmonero implementations are using parts but not the whole as well for the same reason  
<strong>\<vtnerd\_\_\></strong> but the payment id stuff is client side which has already moved away from long ids  
<strong>\<tat\></strong> i think making it impossible to send long payment ids, but have a switch that still allows to decode them would be a good move, possible fading that switch out over time  
<strong>\<endogenic\></strong> yeah our pure fns for long payment ids were actually deleted in mymonero core iirc  
<strong>\<endogenic\></strong> fwiw monero core can adopt that code  
<strong>\<rbrunner\></strong> I think long payment id's still floating around after the work is much less probable than some poor exchange not being able to receive payments at all  
<strong>\<rbrunner\></strong> s/work/fork  
<strong>\<tat\></strong> rbrunner: could be true, there is only a few wallets, if they all disallow that, and there is no hand woven code that push transactions to the network  
<strong>\<hyc\></strong> we have certainly seen oddball txns on the network before, which probably came from custom wallet code  
<strong>\<hyc\></strong> but I don't see that as our problem to manage  
<strong>\<jtgrassie\></strong> except it potentially weakens other users privacy  
<strong>\<jtgrassie\></strong> (e.g. if those odd tx outputs get used as decoys)  
<strong>\<jtgrassie\></strong> which is why i favor banning long payent ids at protocol level  
<strong>\<hyc\></strong> I'm a bit reluctant to do that since we still are keeping extradata itself  
<strong>\<dEBRUYNE\></strong> Banning in october seems a bit optimistic imo  
<strong>\<hyc\></strong> but if the official wallets have already disabled generating them by default, seems OK to me  
<strong>\<rbrunner\></strong> You do mean the long payment id's? Well, backing down now could set a bad precedent  
<strong>\<moneromooo\></strong> FWIW, to see what I've done: <https://github.com/moneromooo-monero/bitmonero/commits/crash>  
<strong>\<hyc\></strong> yes  
<strong>\<moneromooo\></strong> I don't remember exactly so can't give a tl;dr :)  
<strong>\<moneromooo\></strong> (grep for "payment" in the commit title)  
<strong>\<hyc\></strong> this? <https://github.com/moneromooo-monero/bitmonero/commit/0951c3a9ad0c8376b8abd8908603166d7ffc174d>  
<strong>\<jtgrassie\></strong> that one looks good to me  
<strong>\<moneromooo\></strong> Yes. There's at least another one a few commits earlier.  
<strong>\<hyc\></strong> I also see ignoring receivedo nes <https://github.com/moneromooo-monero/bitmonero/commit/6aad370708c0c06c1091912fcc97dceaa09d5b75>  
<strong>\<rbrunner\></strong> So standalone \*short\* id's are gone also, at least over RPC, if I read that code correctly.  
<strong>\<rbrunner\></strong> Only integrated over RPC  
<strong>\<hyc\></strong> yeah that all looks good to me  
<strong>\<moneromooo\></strong> Yes. They were never supposed to be supported. I added them because I'm an idiot. luigi was right.  
<strong>\<rbrunner\></strong> Now we just wait what bittrex, bitfinex say :)  
<strong>\<rbrunner\></strong> I still count on them not being stupid, just not noisy - working on it for quite some time already  
<strong>\<hyc\></strong> back to randomx - any suggestions for testnet fork date? 1 week from today? sooner? later?  
<strong>\<moneromooo\></strong> Whenever pony can be certain to have his nodes updated.  
<strong>\<moneromooo\></strong> So... mid november ?  
<strong>\<hyc\></strong> sigh...  
<strong>\<rbrunner\></strong> 2 weeks, for the next meeting?  
<strong>\<moneromooo\></strong> Oh. I did have some minor stuff I wanted to add for v12.
