---
title: Overview and Logs for the Dev Meeting Held on 2019-06-30
summary: Development status, Code & ticket discussion, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<rehrar\></strong> hey guys  
<strong>\<rehrar\></strong> it's time for a meeting  
<strong>\<rehrar\></strong> as always, we'll try not to drag and make this longer then it needs to be.  
<strong>\<rehrar\></strong> 1. Greetings  
<strong>\<sarang\></strong> Hi  
<strong>\<rbrunner\></strong> Hi\!  
<strong>\<vtnerd\_\_\></strong> Hi  
<strong>\<kinghat\></strong> shalom  
<strong>\<rehrar\></strong> Alright. 2. What's been completed since last meeting.  
<strong>\<rehrar\></strong> Anyone have an update on stuff?  
<strong>\<rehrar\></strong> dsc\_ selsta dEBRUYNE for GUI people?  
<strong>\<rehrar\></strong> moneromooo TheCharlatan CLI?  
<strong>\<dsc\_\></strong> thecharlatan working on reproducible builds for GUI  
<strong>\<rehrar\></strong> fluffypony luigi1111 smooth for Core Team?  
<strong>\<dsc\_\></strong> I'm working on better tails integration  
<strong>\<dEBRUYNE\></strong> GUI v0.14.1.0 is around the corner  
<strong>\<rbrunner\></strong> Ah, that corner?  
<strong>\<dsc\_\></strong> I've updated <https://autonode.xmr.pm/> to show more remote nodes  
<strong>\<moneromooo\></strong> I did some more work on share-rpc, seeing someone's started reviewing.  
<strong>\<moneromooo\></strong> It would be nice if more people reviewed, and if someone did something with it  
<strong>\<sarang\></strong> moneromooo: do you consider the CLSAG implementation branch suitable for PR/review (not to merge yet, just for review)  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<moneromooo\></strong> It doens't have your latest changes though.  
<strong>\<sarang\></strong> Right, and I plan to update 5707 (and its CLSAG equivalent) again soon  
<strong>\<sarang\></strong> those are pretty minor overall  
<strong>\<moneromooo\></strong> Then it might not be be ready.  
<strong>\<luigi1111\></strong> I don't have an update  
<strong>\<dsc\_\></strong> thanks for the update luigi1111  
<strong>\<rehrar\></strong> luigi1111: you can update us on the brand of soda the core team drinks as the relax in the lounge  
<strong>\<dEBRUYNE\></strong> With respect to a timeline for CLSAG, is October too optimistic? We must also take into account third party wallet providers, which will have to make changes too  
<strong>\<rehrar\></strong> thanks everyone for the updates  
<strong>\<rehrar\></strong> dEBRUYNE: this is going to be unpopular to say, as it's been discussed before, but if we're "right on the edge" with CLSAG, then why not just push the fork back a month?  
<strong>\<sarang\></strong> dEBRUYNE: No final word from potential reviewers yet... I reached out again  
<strong>\<sarang\></strong> So I do not have a timeline for CLSAG review  
<strong>\<rehrar\></strong> 25% savings in ring sigs is kind of cool and nice to have.  
<strong>\<dEBRUYNE\></strong> rehrar: So push the October fork back to November?  
<strong>\<rehrar\></strong> if it'd give us the breathing room that would make enough people more comfortable with the timing, then yes  
<strong>\<sarang\></strong> Why not wait until spring?  
<strong>\<rehrar\></strong> Ah, wait no. we want RandomX in ASAP, huh?  
<strong>\<vtnerd\_\_\></strong> This is 25% savings just for the ring sigs portion, not the entire tx, right? I don't see the reason for the push  
<strong>\<rehrar\></strong> so pushing it back maybe isn't great  
<strong>\<sarang\></strong> vtnerd\_\_: a 2-2 txn shrinks by 25% overall  
<strong>\<sarang\></strong> not just sigs  
<strong>\<sarang\></strong> (ring sigs themselves shrink by approx 50%)  
<strong>\<rehrar\></strong> oof  
<strong>\<rbrunner\></strong> My gut feeling tells me that RandomX and those CLSAG thing together will be a bit too much ...  
<strong>\<vtnerd\_\_\></strong> Hmm need to read the paper then, didn't realize it dropped that much  
<strong>\<sarang\></strong> you save 320 bytes per spent input  
<strong>\<sarang\></strong> and about 20% on sig verification time  
<strong>\<vtnerd\_\_\></strong> They are separate things entirely  
<strong>\<vtnerd\_\_\></strong> They are either ready independently or not  
<strong>\<sarang\></strong> And to clarify, there's working code already that anyone is free to review  
<strong>\<sarang\></strong> (verification code will be tweaked a bit still)  
<strong>\<vtnerd\_\_\></strong> Yeah the issue was a math review though ... ?  
<strong>\<sarang\></strong> Yes, and a formal code review  
<strong>\<sarang\></strong> But getting early internal review would be useful  
<strong>\<rehrar\></strong> even though waiting on bulletproofs was a good idea, it was still painful to have that six months of big big transactions  
<strong>\<vtnerd\_\_\></strong> Oh you wanted both for this too? Ok  
<strong>\<rehrar\></strong> that we forever carry  
<strong>\<sarang\></strong> vtnerd\_\_: it's important enough that I think both math/code review are important  
<strong>\<sarang\></strong> esp. since MLSAG never got a formal audit  
<strong>\<vtnerd\_\_\></strong> I mean its either that or risk an entire blow up of the coin  
<strong>\<vtnerd\_\_\></strong> In response to rehrar  
<strong>\<dEBRUYNE\></strong> sarang: I'd be fine with spring, that at least gives third wallet providers plenty of time to work on it  
<strong>\<luigi1111\></strong> I think spring yes  
<strong>\<luigi1111\></strong> for clsag  
<strong>\<rehrar\></strong> yes, but my suggestion was pushign back a month for audits  
<strong>\<rehrar\></strong> which lessens chance of coin blow up  
<strong>\<sarang\></strong> Well, I can let everyone know when I hear back from our potential reviewers  
<strong>\<sarang\></strong> OSTIF are also putting out feelers  
<strong>\<dEBRUYNE\> \<rehrar\></strong> yes, but my suggestion was pushign back a month for audits \<= Can you elaborate?  
<strong>\<dsc\_\></strong> Has anyone heard from fluffy regarding GUI release?  
<strong>\<dsc\_\></strong> Has he arrived home yet?  
<strong>\<rehrar\></strong> if someone could see into the future, we can both see the outcome of the audits as well as save money by not paying for them  
<strong>\<rbrunner\></strong> If we wait with CLSAG until spring, will there be time to build something nice on top of it until then in addition?  
<strong>\<sarang\></strong> Also: earlier internal code review may reveal bugs that we can fix before sending code off to the reviewers  
<strong>\<sarang\></strong> rbrunner: ?  
<strong>\<rehrar\></strong> dEBRUYNE: it's just pushing this fall fork back one month to give some breathing room to get some CLSAG audits in  
<strong>\<rbrunner\></strong> Like those famous atomic swaps, or whatever  
<strong>\<rehrar\></strong> but as I said I see reasons not to do that. It was more in response to vtnerd\_\_  
<strong>\<dEBRUYNE\></strong> dsc\_: <https://www.reddit.com/r/Monero/comments/c6y542/any\_news\_on\_the\_gui\_release/esc02my/>  
<strong>\<sarang\></strong> DLSAG's key image issue makes it unsuitable for implementation just yet, IMO  
<strong>\<sarang\></strong> CLSAG is basically ready without such (known) problems  
<strong>\<dEBRUYNE\></strong> rehrar: Seems like a bit of a slippery slope  
<strong>\<dEBRUYNE\></strong> Seems safer and more prudent to wait six months  
<strong>\<dEBRUYNE\></strong> In the grand scheme of things six months isn't that much anyway  
<strong>\<rehrar\></strong> I don't disagree, dEBRUYNE  
<strong>\<rehrar\></strong> proving alternative viewpoints  
<strong>\<rehrar\></strong> although how long six months is in tech and blockchain relatively is much bigger  
<strong>\<sarang\></strong> It's pretty moot at this point anyway  
<strong>\<sarang\></strong> Until we hear about audits  
<strong>\<rbrunner\></strong> Well, I think that "blockchain relative time" has slowed considerably lately  
<strong>\<rehrar\></strong> true. So maybe move on.  
<strong>\<sarang\></strong> It's a moo point. Like a cow's opinion  
<strong>\<rehrar\></strong> rbrunner: not with fireice and ryo nipping at our heels.  
<strong>\<sarang\></strong> Doesn't matter  
<strong>\<rbrunner\></strong> Lol  
<strong>\<rehrar\></strong> Pretty soon we'll be doing coordinated, organized attacks out of fear  
<strong>\<rehrar\></strong> alright, moving on  
<strong>\<rehrar\></strong> 3. Code/Ticket discussion  
<strong>\<rbrunner\></strong> I have used the Go RPC bindings: <https://github.com/monero-ecosystem/go-monero-rpc-client>  
<strong>\<rbrunner\></strong> My 2 PR's to improve on that were just merged today.  
<strong>\<rbrunner\></strong> Can confirm that the bloody thing works.  
<strong>\<dEBRUYNE\></strong> rbrunner: Have you spent any work (or chatted with the team about it) on OB lately?  
<strong>\<rbrunner\></strong> Yes, and the ball is definitely in their court now: <https://github.com/OpenBazaar/openbazaar-go/issues/1638>  
<strong>\<moneromooo\></strong> That sounds like a lot of nice work there.  
<strong>\<rehrar\></strong> much applause\!  
<strong>\<rehrar\></strong> Is that something Revuo worthy, you think?  
<strong>\<rehrar\></strong> Go RPC stuffs?  
<strong>\<rbrunner\></strong> Ah, hmmm, maybe not yet the OpenBazaar stuff, quite early yet.  
<strong>\<rbrunner\></strong> RPC is of course ok to mention, maybe other people will use it  
<strong>\<rehrar\></strong> Alright, if there's nothing else we can move on  
<strong>\<dEBRUYNE\></strong> Nice work rbrunner  
<strong>\<rbrunner\></strong> Thanks\!  
<strong>\<rehrar\></strong> I'm assuming in "Old Business" we don't need to continue discussion on Payment IDs?  
<strong>\<dsc\_\></strong> very nice rbrunner  
<strong>\<moneromooo\></strong> Only if there are new arguments.  
<strong>\<rehrar\></strong> going once  
<strong>\<rehrar\></strong> going twicee  
<strong>\<dEBRUYNE\></strong> rbrunner: "and no support for moderation" \<= Is that even feasible at this point?  
<strong>\<rehrar\></strong> hearing none, I think we can move on from PIDs  
<strong>\<rbrunner\></strong> Doubtful, unfortunately.  
<strong>\<rehrar\></strong> Ok, any other meeting items?  
<strong>\<rehrar\></strong> Just as kind of announcement. People going to Vegas for Defcon, some of us are going a couple days early (starting monday the 5th) to hang out and chill. All are invited and welcome.  
<strong>\<dEBRUYNE\></strong> rbrunner: I guess they could apply a similar process as bisq for moderation  
<strong>\<dEBRUYNE\> \<rehrar\></strong> I'm assuming in "Old Business" we don't need to continue discussion on Payment IDs? \<= I think the rough consensus was that we should start with a full software removal first  
<strong>\<dEBRUYNE\></strong> (please correct me if I am wrong)  
<strong>\<rbrunner\></strong> Don't remember exactly, isn't Bisq multisig-based as well?  
<strong>\<dEBRUYNE\></strong> Partly (for the BTC part)  
<strong>\<rehrar\></strong> dEBRUYNE: every core team member that spoke up (in the issue) was very against that. Smooth, ArticMine, binaryFate  
<strong>\<moneromooo\></strong> I'll keep the parsing code with an opt-in flag in monerod I think.  
<strong>\<rbrunner\></strong> to hang out and chill \<- is that even allowed for Monero people?  
<strong>\<dEBRUYNE\></strong> rehrar: No?  
<strong>\<rehrar\></strong> ohhhh wait  
<strong>\<rehrar\></strong> never mind, I'm speaking of PID removal in general  
<strong>\<rehrar\></strong> not long  
<strong>\<dEBRUYNE\></strong> They were against parsing tx\_extra / temporary ban  
<strong>\<rehrar\></strong> I got confused cuz you said "software removal 'first' "  
<strong>\<rehrar\></strong> and thought you were hinting at the reversal later  
<strong>\<rehrar\></strong> my bad  
<strong>\<dEBRUYNE\></strong> Hmm no  
<strong>\<dEBRUYNE\></strong> As far as I know, no one was against a full software removal  
<strong>\<rehrar\></strong> cool  
<strong>\<dEBRUYNE\></strong> There were people opposed against (i) temporary banning the tx\_extra field, (ii) permanently banning the tx\_extra field, (iii) parsing the tx\_extra field to disallow long payment IDs  
<strong>\<rehrar\></strong> then we gucci  
<strong>\<sarang\></strong> Define "full software removal" for clarity, plz?  
<strong>\<sarang\></strong> As in, no GUI option to add one for outgoing?  
<strong>\<rehrar\></strong> as I understand, Isthmus says he has some very interesting research going on about "treasures" found in th tx\_extra field  
<strong>\<rehrar\></strong> I'd like to see that research when it happens, and we can discuss the pros and cons afterwards  
<strong>\<rbrunner\></strong> Huh? Really?  
<strong>\<moneromooo\></strong> In fact, I already made that code. I have shitloads of stuff that's not being PRed just because it conflicts due to merging being stalled now  
<strong>\<rbrunner\></strong> That does not sound too good ...  
<strong>\<dEBRUYNE\></strong> moneromooo: Do you have a list for luigi that he can merge?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<dEBRUYNE\></strong> Could you post it here too?  
<strong>\<moneromooo\></strong> Sure. One moment...  
<strong>\<dEBRUYNE\></strong> sarang: removal from both CLI and GUI  
<strong>\<sarang\></strong> With no option to enable via flags?  
<strong>\<moneromooo\></strong> 5647/5666, 5650/5651, 5663/5664, 5668/5669, 5675/5676, 5678/5684 (there's more)  
<strong>\<dEBRUYNE\></strong> That was my idea kind of  
<strong>\<moneromooo\></strong> and 5690/5694, 5681/5708.  
<strong>\<sarang\></strong> Note that this could cause some exchanges/services to recommend specific wallets (that do continue to support) to their users  
<strong>\<sarang\></strong> which could be good or bad, depending on the wallets  
<strong>\<dEBRUYNE\></strong> That's a potential risk, yes  
<strong>\<dEBRUYNE\></strong> I deem it more likely that they will simply switch though  
<strong>\<moneromooo\></strong> I could keep the --enable-paymend-id-bad-for-privacy, and instead of enabling them, it prints "lolno".  
<strong>\<dEBRUYNE\></strong> moneromooo: Will send luigi the list in PM as a reminder  
<strong>\<moneromooo\></strong> Oh I did  
<strong>\<rehrar\></strong> dEBRUYNE sarang this is all one big experiment. I'd say let's try it this way and see how the exchanges react  
<strong>\<moneromooo\></strong> I just don;t want to annoy him too much.  
<strong>\<rehrar\></strong> if they don't do as we hope, then we learn from that next time we have to make a decision like this  
<strong>\<rehrar\></strong> but this is all hypothetical at this time. Let's see what happens.  
<strong>\<rbrunner\></strong> I really doubt that the exchanges have time on their hands to work against the community, but who knows  
<strong>\<rehrar\></strong> well, we do have LiveCoin  
<strong>\<moneromooo\></strong> If they recommend other wallets, I won't have any regret in breaking those in next fork ^\_^  
<strong>\<rehrar\></strong> either way  
<strong>\<rehrar\></strong> 4. Any last meeting items?  
<strong>\<sarang\></strong> 5707 speeds up MLSAG, and will be sped up a bit more  
<strong>\<moneromooo\></strong> Does anyoine want to review share-rpc ? Or did I mention that already...  
<strong>\<sarang\></strong> review will be welcome  
<strong>\<dEBRUYNE\></strong> rehrar: Should we perhaps discuss v0.14.1.1?  
<strong>\<dEBRUYNE\> \<rehrar\></strong> dEBRUYNE sarang this is all one big experiment. I'd say let's try it this way and see how the exchanges react \<= Yes  
<strong>\<dEBRUYNE\></strong> To be fair, it is mostly the big ones that are remaining that we need to get on board  
<strong>\<rehrar\></strong> moneromooo: I'll put it in the REvuo volunteer opportunities (for all the good that will do)  
<strong>\<moneromooo\></strong> AFAIK it's waiting for a freebsd patch from TheCharlatan.  
<strong>\<dEBRUYNE\></strong> Bittrex, Bitfinex, and Binance  
<strong>\<rehrar\></strong> moneromooo: can you PM me a link to it  
<strong>\<vtnerd\_\_\></strong> moneromooo: I will look at it this week  
<strong>\<moneromooo\></strong> <https://github.com/monero-project/monero/pull/5357>  
<strong>\<moneromooo\></strong> Thanks  
<strong>\<rehrar\></strong> thank you  
<strong>\<rehrar\></strong> dEBRUYNE: what do you want to discuss regarding 0.14.1.1?  
<strong>\<rehrar\></strong> the floor is yours  
<strong>\<dEBRUYNE\></strong> Timeline kind of, what do the devs prefer?  
<strong>\<dEBRUYNE\></strong> We can move a bit faster now that we have deterministic builds  
<strong>\<moneromooo\></strong> As soon as the bsd patch is in.  
<strong>\<moneromooo\></strong> (and the patches above)  
<strong>\<rehrar\></strong> I may be getting confused because of the numbers, but didn't pony do builds already?  
<strong>\<rehrar\></strong> or this is new? what's going into it?  
<strong>\<moneromooo\></strong> The BSD patch and the patch list above.  
<strong>\<rehrar\></strong> ah, k  
<strong>\<dEBRUYNE\></strong> moneromooo: All right. Does this need a release v0.14 equivalent? <https://github.com/monero-project/monero/pull/5705>  
<strong>\<dEBRUYNE\></strong> rehrar: new release  
<strong>\<moneromooo\></strong> I dunno, ask TheCharlatan about this one.  
<strong>\<dEBRUYNE\></strong> All right  
<strong>\<rehrar\></strong> ok, anything else to discuss about this release?  
<strong>\<moneromooo\></strong> The GUI I suppose ^\_^  
<strong>\<rehrar\></strong> by all means, moneromooo. Take it away.  
<strong>\<moneromooo\></strong> I don't have anything to say about it.  
<strong>\<dEBRUYNE\></strong> GUI will follow CLI for v0.14.1.1  
<strong>\<dEBRUYNE\></strong> First have to wait for pony to finish the v0.14.1.0 builds though  
<strong>\<moneromooo\></strong> There are missing builds for .0 ? I didn't even realize...  
<strong>\<rehrar\></strong> pony is traveling again  
<strong>\<rehrar\></strong> he does that  
<strong>\<dEBRUYNE\></strong> Yes  
<strong>\<dEBRUYNE\></strong> Also we kind of had to retag, which has delayed the release a bit  
<strong>\<moneromooo\></strong> Gonna run out of places to go soon.  
<strong>\<rehrar\></strong> he's running from the community methinks.  
<strong>\<vtnerd\_\_\></strong> Me? Lol I'm in a car on lte so I dropped service once and hit leave once stupidly  
<strong>\<dEBRUYNE\></strong> rehrar: He provided an update yesterday  
<strong>\<dEBRUYNE\></strong> Anyway, vtnerd\_\_ I wanted to ask you if you had already started some work on dandelion++ ?  
<strong>\<rehrar\></strong> dEBRUYNE: link?  
<strong>\<dEBRUYNE\></strong> <https://www.reddit.com/r/Monero/comments/c6y542/any\_news\_on\_the\_gui\_release/esc02my/>  
<strong>\<rehrar\></strong> alright, if there's nothign else, I think we can call it here.  
<strong>\<rehrar\></strong> discussion can obviously continue after the fact  
<strong>\<vtnerd\_\_\></strong> I started to look into it. At this point my ffs pt 2 is hopefully going to make that transition easier (but it won't be a complete d++ implementation)  
<strong>\<rehrar\></strong> Two weeks from now is the 14th of July. Same time.
