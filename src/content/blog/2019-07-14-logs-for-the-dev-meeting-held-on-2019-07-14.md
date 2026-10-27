---
title: Overview and Logs for the Dev Meeting Held on 2019-07-14
summary: Development status, Code & ticket discussion, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<dEBRUYNE\></strong> Guess we can start, anyone else here? ping moneromooo, rbrunner, selsta, dsc\_, vtnerd, woodser, hyc, jtgrassie, fluffypony, luigi1111, smooth  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Yes meeting. IRC problems. Sec.  
<strong>\<dEBRUYNE\></strong> probably forgot some people  
<strong>\<fluffypony\></strong> here  
<strong>\<dEBRUYNE\></strong> sarang and suraeNoether of course  
<strong>\<moneromooo\></strong> I am.  
<strong>\<rbrunner\></strong> Here of course, where else  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Tor rejecting my login attempts.  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> But present.  
<strong>\<dEBRUYNE\></strong> rehrar, you may lead  
<strong>\<moneromooo\></strong> If ypu have a "tor account", that was some phishing site ^\_^  
<strong>\<italocoin\></strong> :))  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> moneromooo, it's my SASL. Broken for some reason. Will fix later.  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Anyways. Greetings is done.  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> So 2. What's been completed since previous meeting.  
<strong>\<jtgrassie\></strong> woodser: inc/exc PR moneromooo mentioned <https://github.com/monero-project/monero/pull/5598>  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Anyone have an update? CLI stuff? GUI stuff?  
<strong>\<dsc\_\></strong> This week ill work closely with Selsta on things concerning GUI  
<strong>\<moneromooo\></strong> More work on share-rpc. More work on banning subnets. Mostly.  
<strong>\<rbrunner\></strong> I had a little success today, with making Windows GUI installer builds reproducible, with several people confirming the same hash: <https://old.reddit.com/r/Monero/comments/cd0snl/help\_test\_reproducible\_windows\_gui\_installer/>  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> dsc\_ as opposed to other weeks when you don't work closely with selsta on things concerning GUI?  
<strong>\<dEBRUYNE\></strong> To add to the GUI, dsc\_ opened a few pull request to improve Tails support  
<strong>\<italocoin\></strong> dsc\_ i've tested GUI and works well, any known bugs?  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> rbrunner what's the time frame you want for that? I can put it in the next Revuo as a volunteer opportunity, but they come out on Thursdays.  
<strong>\<dEBRUYNE\></strong> xiphon made a pull request to properly store the integrated address (previously it was stored as plain address + short encrypted payment ID)  
<strong>\<rbrunner\></strong> Not sure what you mean about volunteers. I think confirmation is already here, see the posts in that thread  
<strong>\<dsc\_\></strong> italocoin: There are always some bugs but must say latest release was a solid one. For problems best to visit our issue tracker.  
<strong>\<dsc\_\></strong> rehrar: Yes, exactly  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> rbrunner, noted. Thanks for the info.  
<strong>\<italocoin\></strong> dsc\_ one thing that i think we should worok on, is that when you send yourself a payment, it should be a small note there that was sent to yourself, if not you get sent 0  
<strong>\<dsc\_\></strong> italocoin: this has been reported by kico earlier, I believe  
<strong>\<italocoin\></strong> that confuses some people  
<strong>\<italocoin\></strong> Oh kk  
<strong>\<rbrunner\></strong> I think the CLI does the same  
<strong>\<italocoin\></strong> true  
<strong>\<rbrunner\></strong> also a little confusing, at least at first  
<strong>\<moneromooo\></strong> It is impossible to distinguish change from non change, so if you rescan, the amount would change.  
<strong>\<italocoin\></strong> for regular people it is confusing for sure, my idea would be just to add a note that was sent to yourself and just show the fee or someting like that  
<strong>\<moneromooo\></strong> Though... stoffu made some change to the derivations when he introduced subaddresses, and it might be that they can be distinguished nowadays...  
<strong>\<italocoin\></strong> moneromooo: if its sent to subaddress i think you are right, but if the wallet gets rescaned or created again, the 0 its unavoidable i think  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Alright nothing else?  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Oops. Stupid delay.  
<strong>\<rehrar\></strong> from the ashes I rise  
<strong>\<rehrar\></strong> ok, next topic  
<strong>\<fluffypony\></strong> release?  
<strong>\<moneromooo\></strong> Oh yes please  
<strong>\<rehrar\></strong> sure  
<strong>\<rehrar\></strong> fluffypony: take it away?  
<strong>\<moneromooo\></strong> Are you still waiting on the bsd patch, or can that be left out for now ?  
<strong>\<fluffypony\></strong> I mean, it would be advantageous to have it  
<strong>\<fluffypony\></strong> but if it's going to take more than a few days let's just leave it  
<strong>\<moneromooo\></strong> IIRC TheCharlatan said it was a non trivial amount of work.  
<strong>\<moneromooo\></strong> Dunno how far it is though.  
<strong>\<fluffypony\></strong> ok maybe he comments in the next 24 hours  
<strong>\<rbrunner\></strong> "Release" would be already 0.14.1.1 then?  
<strong>\<fluffypony\></strong> yes  
<strong>\<fluffypony\></strong> would the GUI need a point release too?  
<strong>\<dsc\_\></strong> Don't think so. Selsta: ping  
<strong>\<selsta\></strong> yes  
<strong>\<dsc\_\></strong> yes?  
<strong>\<selsta\></strong> I mean yes GUI would need a point release too.  
<strong>\<selsta\></strong> We embed the daemon so all the bugs that get fixed on CLI side effects us too.  
<strong>\<rehrar\></strong> Ok, anything else you want for the discussion on the point release fluffypony?  
<strong>\<dsc\_\></strong> Ah ok, I was more thinking about any death threatening GUI bugs.  
<strong>\<fluffypony\></strong> moneromooo: what merges are you waiting for?  
<strong>\<moneromooo\></strong> I think they're all merged by luigi1111w now. The one I had been thinking about was 5363, but given I've just had to rewrite a fair bit of it, I think I'll leave it.  
<strong>\<moneromooo\></strong> So from my side, we have all we need.  
<strong>\<fluffypony\></strong> ok so just version bump?  
<strong>\<moneromooo\></strong> And maybe some more hashes (with a bit more slack than last time maybe).  
<strong>\<fluffypony\></strong> kk  
<strong>\<rehrar\></strong> Is it possible for us to discuss the October fork?  
<strong>\<fluffypony\></strong> should we set a threshold?  
<strong>\<rehrar\></strong> Just like, prelim stuff  
<strong>\<fluffypony\></strong> for hashes I mean  
<strong>\<moneromooo\></strong> Last time was a day IIRC, that seemed little to me.  
<strong>\<moneromooo\></strong> I suppose we should not see a day's reorg but still  
<strong>\<fluffypony\></strong> ok let's say 48 hours from the time of the commit  
<strong>\<fluffypony\></strong> that gives us a buffer coz it still needs to be built by a bunch of people etc  
<strong>\<moneromooo\></strong> OK.  
<strong>\<rehrar\></strong> gucci?  
<strong>\<dEBRUYNE\></strong> I guess once fluffypony sets the 0.14.1.1 tag, people can already start their determinisitc build processes and publish the hashes  
<strong>\<moneromooo\></strong> versace.  
<strong>\<dEBRUYNE\></strong> The more results the better  
<strong>\<fluffypony\></strong> yes  
<strong>\<fluffypony\></strong> balenciaga  
<strong>\<dsc\_\></strong> louie  
<strong>\<dsc\_\></strong> -e +s  
<strong>\<moneromooo\></strong> To be clear, I was talking about the embedded block hashes, not gitian hashes.  
<strong>\<rehrar\></strong> If so,  
<strong>\<dEBRUYNE\></strong> moneromooo: Yes, my comment was unrelated to that, should have clarified that  
<strong>\<rehrar\></strong> Do we have a rough estimate for when "code freeze" is for this upcoming fork?  
<strong>\<rehrar\></strong> also, I don't know if hyc is around, but with the glowing reviews of RandomX, it's looking almost positive that it's going in, yeah?  
<strong>\<rehrar\></strong> one more to go in regards to audits  
<strong>\<dEBRUYNE\></strong> Not sure about code freeze, but the general idea was to publish binaries way in advance of the fork right (e.g. 4-6 weeks)  
<strong>\<dEBRUYNE\></strong> As the consensus changes are soon ready and we don't have to perform last minute tweaks  
<strong>\<rehrar\></strong> and sarang hasn't mentioned anything about CLSAG audits, right?  
<strong>\<rehrar\></strong> most definitely going in the fork after this one  
<strong>\<dEBRUYNE\></strong> Yeah October seems too short for CLSAG  
<strong>\<rehrar\></strong> alright, if no other comments, are there any other meeting items?  
<strong>\<moneromooo\></strong> I've had people reviewing share-rpc (thanks vtnerd and stoffu), please feel free anyone else ^\_^  
<strong>\<dEBRUYNE\></strong> I kind of wanted to ask everyone's opinion on switching to a 12 month schedule after April 2020 (so once RandomX and CLSAG are in)  
<strong>\<dEBRUYNE\></strong> So we'd essentially only have one HF each year around Monero's birthday  
<strong>\<moneromooo\></strong> We'll only know if we have new stuff we want to add when we get to it.  
<strong>\<sarang\></strong> I am still in (slow) talks with potential auditors  
<strong>\<sarang\></strong> Nobody's biting for the math review part, only implementation  
<strong>\<sarang\></strong> So I am not expecting things will be ready for fall 2019  
<strong>\<dEBRUYNE\></strong> moneromooo: So you'd like to retain the 6 month schedule and skip a HF if there are no consensus changes basically?  
<strong>\<dEBRUYNE\></strong> Or if they can wait  
<strong>\<rehrar\></strong> RandomX will have just been implemented for six months at that part. Is that enough time to gauge it? Becasuse if not, and we move to a year schedule, then that means we wait a full year if something meh happens.  
<strong>\<moneromooo\></strong> I find it annoying to say in advance "we'll wait that long" when we have no clue yet whether that predefined delay will be appropriate.  
<strong>\<rbrunner\></strong> Er, that sounds a little too much theory. I don't think we would wait and not emergency-HF  
<strong>\<rehrar\></strong> it's true that it is a year away at least, so it's hard to gauge. A lot can happen in a year. But I can appreciate dEBRUYNE just putting the feelers out  
<strong>\<moneromooo\></strong> Oh, anyone knows of any merchant/exchange/whatever that's switched from long payment ids recently ?  
<strong>\<rehrar\></strong> no  
<strong>\<dEBRUYNE\></strong> A bit unrelated, but I plan to contact some staff from Bitfinex, Binance, and Bittrex on Reddit to have a chat with them about switching  
<strong>\<dEBRUYNE\></strong> Those are basically the largest 'offenders'  
<strong>\<moneromooo\></strong> Thanks  
<strong>\<italocoin\></strong> RandomX: is experimental, do we have reviews from outsiders?  
<strong>\<moneromooo\></strong> Yes, three.  
<strong>\<moneromooo\></strong> See hyc's "RandomxAudits" github repo.  
<strong>\<rehrar\></strong> with a fourth on the way  
<strong>\<italocoin\></strong> trustworthy?  
<strong>\<moneromooo\></strong> That's what you decide after reading them.  
<strong>\<rehrar\></strong> it wasn't my grandma who audited the thing, if that helps  
<strong>\<rehrar\></strong> either way, I think we can call it here.  
<strong>\<italocoin\></strong> That is great news  
<strong>\<rehrar\></strong> Discussion may, of course, continue after the fact.  
<strong>\<italocoin\></strong> hhaha rehrar  
<strong>\<rehrar\></strong> Thanks for attending the meeting everyone\!  
<strong>\<rehrar\></strong> have nice lives
