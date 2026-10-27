---
title: Logs for the Kovri Dev Meeting Held on 2016-10-16
summary: Brief review of what has been completed since last meeting, Kovri API discussion, Kovri Logo, and code & open tickets discussion
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<i2p-relay\> {-anonimal}</strong> 17:00\!  
<strong>\<moneromooo\></strong> Go go go\!  
<strong>\<ArticMine\></strong> Let’s start  
<strong>\<i2p-relay\> {-anonimal}</strong> I can’t copy/paste as quickly as usual so here’s in bits:  
<strong>\<i2p-relay\> {-anonimal}</strong> 1. Greetings  
<strong>\<i2p-relay\> {-anonimal}</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<i2p-relay\> {-anonimal}</strong> 3. libclient API discussion (\#351)  
<strong>\<i2p-relay\> {-anonimal}</strong> 4. logo  
<strong>\<i2p-relay\> {-anonimal}</strong> 5. Code + ticket discussion / Q &amp; A  
<strong>\<i2p-relay\> {-anonimal}</strong> 6. Any additional meeting items  
<strong>\<i2p-relay\> {-anonimal}</strong> 7. Confirm next meeting date/time  
<strong>\<i2p-relay\> {-EinMByte}</strong> Hi  
<strong>\<i2p-relay\> {-anonimal}</strong> Hello  
<strong>\<i2p-relay\> {-anonimal}</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<i2p-relay\> {-anonimal}</strong> Very little on the codebase work this period because I’ve been busy with getting the full-time prop ready/funded and working on the documentation prop:  
<strong>\<i2p-relay\> {-anonimal}</strong> - Tons of work on \#256 (see my monero-site fork for details)  
<strong>\<i2p-relay\> {-anonimal}</strong> - Minor AES-NI impl fixes/refactor  
<strong>\<i2p-relay\> {-anonimal}</strong> - Client fix to allow saving privates when behind a transproxy  
<strong>\<i2p-relay\> {-anonimal}</strong> - Bump dependency versions in submodules  
<strong>\<i2p-relay\> {-anonimal}</strong> (the issue is probably <em>when client doesn’t have everything it wants when router expects inbound peers</em>)  
<strong>\<i2p-relay\> {-anonimal}</strong> - REMOVED TRAVIS-CI\! YAY\! We now have all-platform build support thanks to pigeons  
<strong>\<i2p-relay\> {-anonimal}</strong> - Minor things and some doc fixes  
<strong>\<i2p-relay\> {-anonimal}</strong> - New contributor dadude (welcome, dadude)  
<strong>\<i2p-relay\> {-anonimal}</strong> One more note:  
<strong>\<i2p-relay\> {-anonimal}</strong> My full-time funding proposal was fully funded in a record \~2-3 days <https://forum.getmonero.org/9/work-in-progress/86967/anonimal-s-kovri-full-time-development-funding-thread>  
<strong>\<i2p-relay\> {-anonimal}</strong> Absolutely unbelievable and I’m so thankful and proud to be a part of this community. The latest reddit thread I think is here <https://www.reddit.com/r/Monero/comments/579t3a/kovri_dev_funded_congrats_everyone/>  
<strong>\<i2p-relay\> {-anonimal}</strong> Huge note: this doesn’t mean we don’t need more contributors, so please let’s continue to get the word out there about kovri and get more people on board so we can grow stronger.  
<strong>\<i2p-relay\> {-anonimal}</strong> Anything else on 2.?  
<strong>\<\_Slack\></strong> Action: anonimal sees dadude typing  
<strong>\<\_Slack\> {dadude}</strong> thank you. And congrats on that anonimal\! that’s actually pretty amazing.  
<strong>\<imans\></strong> reading…  
<strong>\<i2p-relay\> {-anonimal}</strong> Thanks dadude, its really the community to thank; such a great crowd.  
<strong>\<i2p-relay\> {-EinMByte}</strong> Good to see you’re funded now, anonimal  
<strong>\<\_Slack\> {dadude}</strong> yep\! and ‘by word out there about kovri’ you mean in monero community or just more people in general?  
<strong>\<i2p-relay\> {-EinMByte}</strong> That gives me a good excuse to do little development :)  
<strong>\<i2p-relay\> {-anonimal}</strong> s/saving privates/saving private keys/ \<— lol, oops  
<strong>\<i2p-relay\> {-anonimal}</strong> Thanks EinMByte. If an FFS would help you put more time in, I’ll be the first to donate (or will try to be unless someone else beats me to it).  
<strong>\<i2p-relay\> {-anonimal}</strong> dadude: all humans on the planet if possible (preferably with internet availability)  
<strong>\<\_Slack\> {dadude}</strong> got it :slightly\_smiling\_face:  
<strong>\<i2p-relay\> {-anonimal}</strong> Anything else on 2. or dare we dive into API chat?  
<strong>\<sdgsdug9sd\></strong> whats the expected date for release of i2p?  
<strong>\<i2p-relay\> {-anonimal}</strong> sdgsdug9sd: checkout our roadmap  
<strong>\<sdgsdug9sd\></strong> link?  
<strong>\<i2p-relay\> {-anonimal}</strong> github.com/monero-project/kovri/wiki \<—something like that, whatever wiki url is  
<strong>\<i2p-relay\> {-anonimal}</strong> We set a date of nov. 1st for first pre-alpha release. I’d rather push the date to the 0.1.1 release and move 0.1.1 to next year.  
<strong>\<\_Slack\> {dadude}</strong> <https://github.com/monero-project/kovri/wiki/Roadmap>  
<strong>\<ArticMine\></strong> <https://github.com/monero-project/kovri/wiki/Roadmap>  
<strong>\<i2p-relay\> {-anonimal}</strong> (like I said, barely any codebase work in 2 weeks)  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, let’s move to 3. and we can add other items/open questions to 6.  
<strong>\<i2p-relay\> {-anonimal}</strong> 3. libclient API discussion (\#351)  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: did you get a chance to research my question(s)?  
<strong>\* moneromooo</strong> suddenly appears very busy with somehting else  
<strong>\<moneromooo\></strong> … no. Sorry…  
<strong>\<moneromooo\></strong> Many bugs…  
<strong>\<sdgsdug9sd\></strong> lol is this real? i hardly believe those target dates  
<strong>\<imans\></strong> seems codebase is very weak at this time. Needs of lot of testing I think  
<strong>\<i2p-relay\> {-anonimal}</strong> Guys, we’re on API discussion now, we’ll chat more later in the meeting.  
<strong>\<imans\></strong> okay  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: I’ll try to rephrase then  
<strong>\<moneromooo\></strong> There is talk of switching the P2P API to zmtp too (I know nothing about it).  
<strong>\<moneromooo\></strong> Should still be mostly streaming thoug.h  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: I’m betting most of my questions can be answered with more research on my end  
<strong>\<moneromooo\></strong> OK, I think maybe ask questions here, and I will try to answer with what I can.  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: where can I get a good tl;dr of how monero handles timeouts?  
<strong>\<moneromooo\></strong> From what I can tell, it uses boost’s asio system for this.  
<strong>\<moneromooo\></strong> Then you get a callback with a “cancelled” state IIRC.  
<strong>\<i2p-relay\> {-anonimal}</strong> by ‘handle’ I mean internally (if something needs to get to blockchain but doesn’t quickly enough)  
<strong>\<moneromooo\></strong> (from boost)  
<strong>\<i2p-relay\> {-anonimal}</strong> That’s too obvious moneromooo :) I mean purely internally  
<strong>\<moneromooo\></strong> to blockchain ? I’m talking avbout the P2P comms here.  
<strong>\<moneromooo\></strong> Hmm, well, I don’t know more about timeouts, sorry.  
<strong>\<i2p-relay\> {-anonimal}</strong> I’ll try to rephrase again, if a node’s internet connection is unreliabe, is behaviour undefined?  
<strong>\<imans\></strong> it will not get a proper sync simple  
<strong>\<moneromooo\></strong> Hopefully not. Connections to a peer are dropped if “weird” stuff is received, but to what extent this is pervasive, I’m not sure.  
<strong>\<moneromooo\></strong> There’s a query/reply system, with a handful of possible messages IIRC.  
<strong>\* pero</strong> will brb 5min - knows he’s next up on agenda  
<strong>\<moneromooo\></strong> This seems rather high level though.  
<strong>\<i2p-relay\> {-anonimal}</strong> \* is thinking ahead, wants to know how a node will deal with dropped tunnels on a noticeable scale  
<strong>\<i2p-relay\> {-EinMByte}</strong> anonimal: backup tunnels like java i2p could work  
<strong>\<moneromooo\></strong> Well, it should be resistant to that. If it’s not, we’ll have to make it.  
<strong>\<moneromooo\></strong> I2P can keep a tunnel for a few minutes reliably enough, right ?  
<strong>\<i2p-relay\> {-anonimal}</strong> EinMByte: good point.  
<strong>\<i2p-relay\> {-EinMByte}</strong> But AFAIK, we still aren’t sure that monero actually needs connections?  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: technically, any tunnel and blow at any moment IIRC  
<strong>\<i2p-relay\> {-anonimal}</strong> s/and/can/  
<strong>\<moneromooo\></strong> At any moment is fine, but monero would need to be at least one of high enough duration to reveive a chunk of blokcs when syncing.  
<strong>\<i2p-relay\> {-anonimal}</strong> If Joe shuts off his router unexpectedly, we have to wait to build a new tunnel from the pool (IIRC)  
<strong>\<i2p-relay\> {-anonimal}</strong> How big are those chunks usually?  
<strong>\<moneromooo\></strong> Again, this is fine. As long as we can get a minute of comms at one point.  
<strong>\<moneromooo\></strong> Currently, 200 times the size of a block, which is… hmm… from 250 bytes to 60 kB.  
<strong>\<moneromooo\></strong> That 200 can be changed when running with kovri if needed.  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: ok, scenario question: what if we <em>can</em> get a reliable connection but syncing has to wait for it but will be notified “try again in X minutes”. Will that break monero?  
<strong>\<i2p-relay\> {-EinMByte}</strong> with streaming it doesn’t really matter  
<strong>\<i2p-relay\> {-EinMByte}</strong> datagrams are limited in size, though  
<strong>\<ArticMine\></strong> but does this set a limit on the blocksize in Monero?  
<strong>\<moneromooo\></strong> I think that, for now, that connection will be dropped, and another attempted. But that doesn’t seem too hard to change.  
<strong>\<moneromooo\></strong> ArticMine: no, the 200 is the number of blocks. Though if one block is 100 MB in the future… I guess it needs to be downloaded without interruption.  
<strong>\<i2p-relay\> {-EinMByte}</strong> dropping and re-attempting sounds like a good strategy  
<strong>\<moneromooo\></strong> The re-attempt would be to another random peer.  
<strong>\<i2p-relay\> {-anonimal}</strong> \* eek  
<strong>\<moneromooo\></strong> (currently anyway)  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, well what I’m poking at I think is for more in the future (and based on passing thoughts this week).  
<strong>\<i2p-relay\> {-anonimal}</strong> \* was not prepared for API chat this week because of point 2.  
<strong>\<i2p-relay\> {-anonimal}</strong> EinMByte: any other questions/thoughts?  
<strong>\<i2p-relay\> {-anonimal}</strong> ^ moneromooo  
<strong>\<moneromooo\></strong> Not from me.  
<strong>\<i2p-relay\> {-EinMByte}</strong> Just that I don’t think disconnections would be that much of an issue  
<strong>\<i2p-relay\> {-anonimal}</strong> I have been envisioning more of the API on our end though, but purely in my head.  
<strong>\<i2p-relay\> {-EinMByte}</strong> but let’s move on  
<strong>\<ArticMine\></strong> I have to leave now.  
<strong>\<i2p-relay\> {-anonimal}</strong> \_ one more thing  
<strong>\<i2p-relay\> {-anonimal}</strong> Actually, nevermind because I don’t want to put dadude on the spot and it’s probably unrelated  
<strong>\<\_Slack\> {dadude\>}</strong> well if I left the node on and the connection is bad, I wouldn’t want it to stop, as bad as mightbe. I’ll probably be thinking that its syncing. So what about an timed retry till the network gets back on? If it is very bad, then you can set up an option like —retry x-times  
<strong>\<i2p-relay\> {-anonimal}</strong> dadude if you have API questions as related to torrenting, now’s the chance  
<strong>\<\_Slack\> {dadude\>}</strong> Oh, I  
<strong>\<i2p-relay\> {-anonimal}</strong> (no rush, there are plenty more meetings to be had)  
<strong>\<\_Slack\> {dadude\>}</strong> I’ll read up on how vuze does it and get back to you guys if I have any questions  
<strong>\<i2p-relay\> {-anonimal}</strong> dadude: good point, I’m sure the API will cover that  
<strong>\<i2p-relay\> {-anonimal}</strong> dadude: we can explain how vuze does it after the meeting if you’d like  
<strong>\<moneromooo\></strong> A torrent based syncing process was suggested before. It’d be quite a departure from what we have now, but would be a good thing I guess.  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, nothing else on 3.?  
<strong>\<\_Slack\> {dadude\>}</strong> thanks. unrelated: How does relay handle edits to a post here on slack  
<strong>\<i2p-relay\> {-anonimal}</strong> dadude: let’s save that until later in the meeting  
<strong>\<moneromooo\></strong> (for initial sync anyway)  
<strong>\<\_Slack\> {dadude\>}</strong> Oh I wasn’t talking about to sync the blockchain, I was talking about torrenting inside the i2p netowkr  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: is there a post or link re: that proposal?  
<strong>\<moneromooo\></strong> It was mentioned in one of the MRL papers IIRC. No details, but I can find you the one.  
<strong>\<i2p-relay\> {-anonimal}</strong> Thank you moneromooo.  
<strong>\<i2p-relay\> {-anonimal}</strong> \_ would navigate but you know MRL better than I  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, moving on  
<strong>\<i2p-relay\> {-anonimal}</strong> 4. logo  
<strong>\<i2p-relay\> {-anonimal}</strong> pero: all you if you’re here\!  
<strong>\<pero\></strong> yes hi  
<strong>\<pero\></strong> ok so we’re down to 2 fonts  
<strong>\<i2p-relay\> {-anonimal}</strong> Let’s decide now then  
<strong>\<pero\></strong> each came with 6-8 weights and i’ve cut that down to 2 for exo2 and 3 for lato  
<strong>\<pero\></strong> <https://a.pomf.cat/gyzaxi.png>  
<strong>\<pero\></strong> 1b and 1c are the same weight with different kerning  
<strong>\<pero\></strong> the ‘garlic-integrated’ variants are interesting but will require rework of the garlic  
<strong>\<pero\></strong> for record keeping purposes this is v8  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, we’re throwing out the garlic as ‘o’ idea because: 1. doesn’t look like garlic 2. doesn’t look like an ‘o’ 3. not intended for that purpose  
<strong>\<i2p-relay\> {-anonimal}</strong> Any objections?  
<strong>\<moneromooo\></strong> My subjective opinion is that the “garlic as dot in the i” is too small to not feel weird.  
<strong>\<i2p-relay\> {-anonimal}</strong> \* agreeing with moneromooo, it looks like a flame  
<strong>\<pero\></strong> yes i agree - is viable but needs rework  
<strong>\<imans\></strong> instead put garlic for o kovri  
<strong>\<moneromooo\></strong> I thought the flame thing was intended :P  
<strong>\<i2p-relay\> {-anonimal}</strong> imans: see my comment above  
<strong>\<\_Slack\> {dadude}</strong> just a small question. wait, so are we 1. pushing kovri as a ‘project’ on its own (apart from geti2p.net) or 2. just an alternative router to the java i2p one. Because if it is 2, shouldn’t it way only ‘garlic router’? and not add the project?  
<strong>\<imans\></strong> okay  
<strong>\<i2p-relay\> {-anonimal}</strong> dadude: 1.  
<strong>\<pero\></strong> imans - the problem with that is that the garlic wasn’t intended for such usage  
<strong>\<pero\></strong> and makes the text imbalanced  
<strong>\<i2p-relay\> {-anonimal}</strong> Alright, everyone pick their favorite font now please (we need to decide on logo today, final decision this week - not waiting until next meeting)  
<strong>\<imans\></strong> fine. pero  
<strong>\<pero\></strong> e.g., the space between the upper portion of the K and the black part of the garlic is smaller than the whitespace on the right side  
<strong>\<pero\></strong> and the small lines at the bottom and top of garlic aren’t optimal  
<strong>\<imans\></strong> I see it there  
<strong>\<imans\></strong> My choice is the 6th one  
<strong>\<imans\></strong> for font  
<strong>\<moneromooo\></strong> I’d pick one of the ones on the right, just because they’re fatter, and so easier to read.  
<strong>\<imans\></strong> and bold  
<strong>\<i2p-relay\> {-EinMByte}</strong> I’d go for lato  
<strong>\<i2p-relay\> {-EinMByte}</strong> (b1?)  
<strong>\<pero\></strong> yea i’m in the lato camp as well  
<strong>\<i2p-relay\> {-anonimal}</strong> pero: I like lato, X coord 1, Y coord b  
<strong>\<imans\></strong> seems everyone picks up the second  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, 3 votes for b1, 1 vore for ‘the 6th one’ (I have no idea what that is)  
<strong>\<\_Slack\> {dadude}</strong> yep b1  
<strong>\<pero\></strong> i’m either b2 or b3  
<strong>\<pero\></strong> 6th one was b3  
<strong>\<i2p-relay\> {-anonimal}</strong> Alright, 4 votes b1, 2 for b3, 1 for b2  
<strong>\<moneromooo\></strong> If I had to choose one, I’d say bottom right, but there’s really not much difference and I might pick another one tomorrow :)  
<strong>\<i2p-relay\> {-anonimal}</strong> b1 one is the winner, any objections?  
<strong>\<i2p-relay\> {-anonimal}</strong> lol  
<strong>\<pero\></strong> well that’s for b3 now ;p  
<strong>\<pero\></strong> 3  
<strong>\<moneromooo\></strong> Ignore me :)  
<strong>\<i2p-relay\> {-anonimal}</strong> \* looks different depending on mood  
<strong>\<i2p-relay\> {-EinMByte}</strong> 3/3, let’s toss a coin  
<strong>\<i2p-relay\> {-anonimal}</strong> pero: also, let’s try steching that subtext all the way to the left  
<strong>\<i2p-relay\> {-anonimal}</strong> to the end of the garlic  
<strong>\<i2p-relay\> {-anonimal}</strong> Does that effect your decision?  
<strong>\<pero\></strong> yea that variant was included before - it was just a time saving consideration to not include it  
<strong>\<i2p-relay\> {-anonimal}</strong> \* wonders how to coin toss over IRC  
<strong>\<moneromooo\></strong> There were some with that system on one of the previous images. It looked odd. Maybe instead scale the garlic up to go tho the bottonm of the subtext.  
<strong>\<pero\></strong> as a rule of thumb you want heavier type for the logo  
<strong>\<pero\></strong> moneromooo that looked even weirder :)  
<strong>\<moneromooo\></strong> So there’s no hole, but it doesn’t also feel like the subtext is running away from the main text.  
<strong>\<i2p-relay\> {-anonimal}</strong> b2 b3 looks overpowering compared to that logo IMHO  
<strong>\<moneromooo\></strong> Hmm, ok.  
<strong>\<i2p-relay\> {-anonimal}</strong> We have 7 minutes to decide, I’d like to save room for other topics.  
<strong>\<i2p-relay\> {-anonimal}</strong> 6 minutes now  
<strong>\<imans\></strong> I stick with the last one on the right  
<strong>\<pero\></strong> i think you should be focusing on the largest variant  
<strong>\<pero\></strong> and the variant with only the garlic on the left  
<strong>\<pero\></strong> when deciding  
<strong>\<endogenic\></strong> lol you valuable guys/gals are spending too much time on it imo and may end up getting sucked down a depth first search rather than seeing the whole picture. this is just my humble opinion but it’s better to find a designer to own it (and prevent design by committee)  
<strong>\<pero\></strong> don’t worry about the others  
<strong>\<endogenic\></strong> but i might regret having opened my mouth :P  
<strong>\<pero\></strong> endogenic - this is how the ‘design process’ works  
<strong>\<i2p-relay\> {-anonimal}</strong> pero: 5 minutes, why?  
<strong>\<moneromooo\></strong> They all look so similar anyway.  
<strong>\<pero\></strong> this is ‘client feedback’  
<strong>\<i2p-relay\> {-anonimal}</strong> I like the balance of b1  
<strong>\<pero\></strong> you don’t just present a finished logo to a client and say ‘here, take this’  
<strong>\<i2p-relay\> {-anonimal}</strong> b2 b3 are too strong  
<strong>\<imans\></strong> okay  
<strong>\<i2p-relay\> {-EinMByte}</strong> I though we were going to toin coss  
<strong>\<endogenic\></strong> <http://www.logodesignlove.com/next-logo-paul-rand>  
<strong>\<i2p-relay\> {-EinMByte}</strong> \*thought  
<strong>\<moneromooo\></strong> I vote for toin coss.  
<strong>\<i2p-relay\> {-anonimal}</strong> Who has the coin?  
<strong>\<endogenic\></strong> but i’m not disagreeing that market research is important  
<strong>\<endogenic\></strong> talking to users is basically \#1 next to building  
<strong>\<i2p-relay\> {-anonimal}</strong> And is that coin CSPRNG, lol  
<strong>\<i2p-relay\> {-EinMByte}</strong> Let’s do this right and use a bit commitment scheme  
<strong>\<i2p-relay\> {-anonimal}</strong> 3 minutes  
<strong>\<i2p-relay\> {-EinMByte}</strong> (unfortunately we don’t have secure timestamping available for the commitment scheme)  
<strong>\<pero\></strong> yea ok pay someone 100k and after 6 months they’ll narrow it down to 1 almost scientifically  
<strong>\<i2p-relay\> {-anonimal}</strong> 2 minutes  
<strong>\<moneromooo\></strong> OK, so, if the number of letters in “anonimal” is even, b1, if it’s odd then b3. OK ?  
<strong>\<pero\></strong> i’m in the not b1 camp  
<strong>\<i2p-relay\> {-anonimal}</strong> \* bribes moneromooo behind closed doors  
<strong>\<pero\></strong> mostly because it looks close to just regular text  
<strong>\<i2p-relay\> {-anonimal}</strong> I think b2 b3 are ugly, I don’t want to see this everytime I look at the readme  
<strong>\<i2p-relay\> {-anonimal}</strong> \* don’t forget the devs  
<strong>\<moneromooo\></strong> A graphical README ?  
<strong>\<i2p-relay\> {-anonimal}</strong> 1 minute to flip coin  
<strong>\<pero\></strong> just bigger and with tighter kerning  
<strong>\<i2p-relay\> {-anonimal}</strong> \* will pull executive order if someone can’t flip a coin  
<strong>\<i2p-relay\> {-iDunk}</strong> we can pick anything as long as it’s b1 :)  
<strong>\<moneromooo\></strong> SOLD\!  
<strong>\<i2p-relay\> {-anonimal}</strong> pero: will b2 look better when subtext is streched across to the left  
<strong>\<i2p-relay\> {-anonimal}</strong> \* trusted pero so far, no reason to stop trusting  
<strong>\<i2p-relay\> {-iDunk}</strong> btw, i’m also for b3  
<strong>\<pero\></strong> well i’d show you but i’m in wayland atm with no screenshot support  
<strong>\<i2p-relay\> {-anonimal}</strong> I’d like EinMByte to be the tie-breaker if he’s up for it  
<strong>\<i2p-relay\> {-EinMByte}</strong> With iDunk’s vote, let’s say the choice is b3  
<strong>\<pero\></strong> but no it doesn’t look any better than it does now  
<strong>\<i2p-relay\> {-anonimal}</strong> b3 it is\!  
<strong>\<i2p-relay\> {-anonimal}</strong> Congrats to b3  
<strong>\<i2p-relay\> {-iDunk}</strong> \* hides from anonimal  
<strong>\<i2p-relay\> {-anonimal}</strong> \* says eww but oh well  
<strong>\<i2p-relay\> {-anonimal}</strong> lol iDunk  
<strong>\<moneromooo\></strong> eww well  
<strong>\<i2p-relay\> {-anonimal}</strong> \* looking forward to a kovri PR from iDunk some day  
<strong>\<i2p-relay\> {-iDunk}</strong> :D  
<strong>\<i2p-relay\> {-anonimal}</strong> Moving on,  
<strong>\<imans\></strong> congrats  
<strong>\<i2p-relay\> {-anonimal}</strong> 5. Code + ticket discussion / Q &amp; A  
<strong>\<imans\></strong> ask  
<strong>\<i2p-relay\> {-anonimal}</strong> 8 minutes left, I want to actually move to 6.  
<strong>\<i2p-relay\> {-anonimal}</strong> Any objections?  
<strong>\<imans\></strong> no  
<strong>\<i2p-relay\> {-EinMByte}</strong> No objections  
<strong>\<i2p-relay\> {-anonimal}</strong> 6. Any additional meeting items  
<strong>\<i2p-relay\> {-anonimal}</strong> {-imans} seems codebase is very weak at this time. Needs of lot of testing I think  
<strong>\<i2p-relay\> {-anonimal}</strong> imans: have you spent time with this codebase?  
<strong>\<imans\></strong> Just trying to install  
<strong>\<imans\></strong> My ubuntu is hanging. I have to try another time.  
<strong>\<i2p-relay\> {-EinMByte}</strong> \* afk  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, so you haven’t then.  
<strong>\<i2p-relay\> {-anonimal}</strong> {-sdgsdug9sd} lol is this real? i hardly believe those target dates  
<strong>\<imans\></strong> yes  
<strong>\<i2p-relay\> {-iDunk}</strong> i installed it yesterday and it seemed to run just fine until a few hours ago  
<strong>\<moneromooo\></strong> That’s for “kovri runs and does things”, not “monero uses kovri”, fwiw.  
<strong>\<i2p-relay\> {-anonimal}</strong> sdgsdug9sd: then you probably wouldn’t believe that what we forked from actually had a release and you should be thankful we’ve not repeated that same mistake  
<strong>\<moneromooo\></strong> What was the mistake ?  
<strong>\<i2p-relay\> {-anonimal}</strong> sdgsdug9sd: also, see pre-alpha <https://en.wikipedia.org/wiki/Pre-alpha>  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: calling that router a year ago “releaseable”  
<strong>\<moneromooo\></strong> Ah…  
<strong>\<i2p-relay\> {-iDunk}</strong> i got disconnected from irc, couldn’t connect any more, tried to exit from kovri but had to kill it  
<strong>\<i2p-relay\> {-iDunk}</strong> restarted and it runs fine again  
<strong>\<i2p-relay\> {-anonimal}</strong> 2 minutes. Any questions/comments/new items?  
<strong>\<i2p-relay\> {-anonimal}</strong> imans sdgsdug9sd: ^  
<strong>\<imans\></strong> I will ask more in next meeting. I need to brainstorm myself  
<strong>\<moneromooo\></strong> anonimal: <https://lab.getmonero.org/pubs/MRL-0004.pdf> — the torrent suggestion was not about initial sync actually, but about sending new txes.  
<strong>\<moneromooo\></strong> (I had misremembered)  
<strong>\<i2p-relay\> {-anonimal}</strong> I’m available for tech support after the meeting  
<strong>\<i2p-relay\> {-anonimal}</strong> 2 weeks, same time?  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: ah, ok, thanks I’ll give it a read  
<strong>\<i2p-relay\> {-anonimal}</strong> imans: if you need help just ask in \#kovri or \#kovri-dev after the meeting  
<strong>\<i2p-relay\> {-anonimal}</strong> 7. Confirm next meeting date/time  
<strong>\<i2p-relay\> {-anonimal}</strong> \* moving on  
<strong>\<i2p-relay\> {-anonimal}</strong> No objections? 2 weeks same time then.  
<strong>\<imans\></strong> Okay anonimal. I’m in another stuff I will get in technical touch tomorrow  
<strong>\<i2p-relay\> {-iDunk}</strong> yep  
<strong>\<imans\></strong> so, the date and time is?  
<strong>\<i2p-relay\> {-anonimal}</strong> Thank you everybody. Thank you dEBRUYNE for logging these meetings :)
