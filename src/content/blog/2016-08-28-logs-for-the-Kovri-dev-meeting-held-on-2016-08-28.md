---
title: Logs for the Kovri Dev Meeting Held on 2016-08-28
summary: Brief review of what has been completed since last meeting, Kovri Logo, code & open tickets discussion
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<fluffypony\></strong> anonimal: all yours  
<strong>\<tewinget\></strong> in the meantime, for those not interested (or relevant to) the kovri meeting, anyone wanna help me test the zmq wallet\<-\>daemon interactions?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Proposed meeting items:  
<strong>\<tewinget\></strong> oh  
<strong>\<tewinget\></strong> shit  
<strong>\<meeting-bot\> \[anonimal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. Code + ticket discussion / Q &amp; A  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. Discuss \#282  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. Closing \#226  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. Closing \#105  
<strong>\<meeting-bot\> \[anonimal\]</strong> 7. Closing \#46  
<strong>\<meeting-bot\> \[anonimal\]</strong> 8. Closing \#27  
<strong>\<meeting-bot\> \[anonimal\]</strong> 9. Any additional meeting items  
<strong>\<meeting-bot\> \[anonimal\]</strong> 10. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anonimal\]</strong> btw, twinget, you are \*all\* relevant to the meeting and you \*ALL\* should be interested.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Its that kind of attitude that is preventable advancing kovri development within monero.  
<strong>\<fluffypony\>\></strong> +100  
<strong>\<meeting-bot\> \[anonimal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi, I’m here.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> me three  
<strong>\<tewinget\>\></strong> anonimal (I’m not relevant in the sense that I have no context, need to learn more about it :))  
<strong>\<i2p-relay\> {-solmar}\></strong> we need all the help we can get  
<strong>\<meeting-bot\> \[fluffypony\]</strong> EinMByte ?  
<strong>\<ArticMine\>\></strong> I will stay for another 20 min then I have to leave.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> tks ArticMine  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi ArticMine.  
<strong>\<ArticMine\>\></strong> Hi  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi solmar, EinMByte, fluffypony.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> $ git checkout master &amp;&amp; git log —pretty=oneline —no-merges —since=2016-07-31 \| wc -l  
<strong>\<meeting-bot\> \[anonimal\]</strong> 55  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Lots of build work  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Reinstate FreeBSD build  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Reinstate Clang support  
<strong>\<meeting-bot\> \[anonimal\]</strong> - New config features  
<strong>\<meeting-bot\> \[anonimal\]</strong> - New logging features  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Implemented SNI (part of cpp-netlib)  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m doing work in branch fix-305, not detailed here.  
<strong>\<meeting-bot\> \[anonimal\]</strong> We have a new member onbard, ‘solmar’. guzzi is back with us too.  
<strong>\<meeting-bot\> \[anonimal\]</strong> rakhimov is becoming more active, all great.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I hope EinMByte’s travels have been well and has returned.  
<strong>\<meeting-bot\> \[solmar\]</strong> hey all ;)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Did I miss anything for point 2.?  
<strong>\<fluffypony\></strong> well  
<strong>\<fluffypony\></strong> is it worth discussing \#325 now?  
<strong>\<meeting-bot\> \[solmar\]</strong> the quality assurance document is note worthy but i think you got everything  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: no not yet.  
<strong>\<fluffypony\></strong> ok  
<strong>\<meeting-bot\> \[anonimal\]</strong> solmar: thanks, good point. Yes solmar and I reworked \#58 and introduced it into a tangible guide.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything on 2. before moving onto 3.?  
<strong>\<fluffypony\></strong> nothing more on 2  
<strong>\<meeting-bot\> \[anonimal\]</strong> Before 3., did solmar want to formally introduce themself?  
<strong>\<meeting-bot\> \[solmar\]</strong> sure i can quickly introduce  
<strong>\<meeting-bot\> \[solmar\]</strong> you guys may have seen me kicking around the various monero-related channels in the past few weeks. monero has peaked great interest in me and moving forward will be quite powerful  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Welcome :)  
<strong>\<meeting-bot\> \[solmar\]</strong> i am switching focus to kovri because of how unmanned the team is but in the next week i would gladly help test ringct code on the testnet  
<strong>\<meeting-bot\> \[fluffypony\]</strong> +1  
<strong>\<tewinget\></strong> s/peaked/piqued/ \<— fuck English sometimes  
<strong>\<meeting-bot\> \[solmar\]</strong> in the meantime i will continue to learn the kovri code to hopefully in the near future begin to make tangible contributions to the code  
<strong>\<meeting-bot\> \[fluffypony\]</strong> awesome, everyone should dabble in both  
<strong>\<meeting-bot\> \[solmar\]</strong> any interest and help with kovri is greatly appreciated  
<strong>\<meeting-bot\> \[solmar\]</strong> i think we can move along to 3. now thanks anominal ;)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Alright, thanks solmar.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. Code + ticket discussion / Q &amp; A  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ll open  
<strong>\<meeting-bot\> \[fluffypony\]</strong> some of the design decisions in Kovri were influenced by Monero, so no getting away from it, Monero devs ;)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Question: WHEN WILL MONERO DEVS START TAKING KOVRI SERIOUSLY?  
<strong>\<meeting-bot\> \[anonimal\]</strong> 10 months in now since our november 1st meeting,  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Define “taking seriously” ? Send patches ?  
<strong>\<tewinget\></strong> anonimal: I take it just as seriously as, say, RingCT, I just haven’t had/taken the time to dig into either yet :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> As a whole, if I could quantify contributions, I’d say kovri is getting \~5% attention to what bitmonero and ecosystem is getting.  
<strong>\<meeting-bot\> \[anonimal\]</strong> moneromooo: anything.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> OK, fair enough. A new codebase appearing like that is going to be not so easy to jump back and forth for coders. But I hear your point.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I will try to get into kovri a bit once rct is all done.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I understand all the arguments, and I know what sacrifices would need to be made, so I question when and if they will be made.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Thanks moneromooo.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> the easiest way to get hyc involved it for us to use LMDB for storage of something :-P  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> (and feel free to remind me of it if I don’t :P)  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Nah, use liblber for network.  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: this goes for you too, as we’ll see with the remaining agenda items.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Make us fast and secure comms\!  
<strong>\<tewinget\></strong> fluffypony: in the same way as with hyc, the easiest way to get me involved is something needing refactored \>\_\>  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anyone else over there have a response beside moneromooo and tewinget?  
<strong>\<meeting-bot\> \[anonimal\]</strong> If not, we should move onto other Q &amp; A.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> is this still the ticket discussion part?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Point 3.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> yes - but I mean ticket discussion is part of Q&amp;A or can I bring up a ticket now?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I have library questions I would want to debate with EinMByte but I don’t think he’s around.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Sure but that’s least priority at the moment.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And should be 9.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’d rather move onto 4. if no one has any questions.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> kk  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. Discuss \#282  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok so  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> There was a designer guy asking whether help was wanted. He seemed to be after paid work though.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> with the Monero logo we used 99designs  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> eherdesign in \#monero  
<strong>\<meeting-bot\> \[fluffypony\]</strong> moneromooo: I looked at his stuff, it wasn’t mind-blowing  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’d like to move to use 99designs again  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ref: <https://99designs.com/logo-design/contests/monero-mro-cryptocurrency-logo-design-contest-382486>  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’m happy to put the $500 up for that, and then use the FFS to get it back  
<strong>\<meeting-bot\> \[fluffypony\]</strong> unless anyone feel we must go for a higher 99designs reward  
<strong>\<othe\></strong> i would also sponsor that  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> \_ hopes it won’t be some shady looking concept  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> It worked very well for Monero so I say yeas with the same package  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> yes  
<strong>\<meeting-bot\> \[solmar\]</strong> maidsafe also appears to be having success with 99designs so i think it is a good idea  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok - I’ll set that up now - do we have any ideas as to what we want to convey?  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> Well I have to leave now  
<strong>\<meeting-bot\> \[fluffypony\]</strong> do we want it to be inspired by the Monero logo, like the MRL logo is?  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> The essential qualities of garlic.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> (ref: <https://lab.getmonero.org/logo.png>)  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> ^ great logo  
<strong>\<groeg\></strong> (noob here …) A podcast I follow have a promo code för 99designs. Interesting?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> groeg: yes plz, can you PM it to me?  
<strong>\<cjd\></strong> you’ll want to pm it to fluffypony, not to the bot  
<strong>\<cjd\></strong> he’s in this irc  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Actually… you could rotate the Monero logo 90% clockwise and arrange colors a bit so it looks like a K. With kind of a hidden M.  
<strong>\<groeg\></strong> newbie using IRC, looking up how to pm …  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> groeg: /query NICKHERE  
<strong>\<meeting-bot\> \[fluffypony\]</strong> thanks groeg, got it  
<strong>\<meeting-bot\> \[solmar\]</strong> conveying a “veil”-ish esque style to it could be interesting, since kovri means veil in esperanto afaik  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> 90 degrees, not %, of course -\_-  
<strong>\<meeting-bot\> \[fluffypony\]</strong> solmar that’s pretty much what I was thinking, something along the lines of a network, but it’s private  
<strong>\<meeting-bot\> \[fluffypony\]</strong> or something  
<strong>\<meeting-bot\> \[fluffypony\]</strong> doesn’t have to be a “veil” in the literal sense  
<strong>\<meeting-bot\> \[solmar\]</strong> ya  
<strong>\<meeting-bot\> \[solmar\]</strong> i agree  
<strong>\<meeting-bot\> \[solmar\]</strong> ya exactly  
<strong>\<meeting-bot\> \[anonimal\]</strong> Sorry, unexpected AFK emergency, unavoidable.  
\*\*\<meeting-bot\> \_ anonimal\*\* reading  
<strong>\<meeting-bot\> \[anonimal\]</strong> moneromooo: cool idea, maybe someone can run with that.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> anonimal: the rotated K thing?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I can suggest that in the 99designs description  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yeah, but maybe not literally, just an artistic motive I guess.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> yeah  
<strong>\<meeting-bot\> \[anonimal\]</strong> But also garlic is a good point as solmar pointed out.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> isn’t garlic very Tor?  
<strong>\<meeting-bot\> \[anonimal\]</strong> So a rotated K inside a garlic clove  
<strong>\<meeting-bot\> \[anonimal\]</strong> No, they’re onion.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> oh yes  
<strong>\<meeting-bot\> \[fluffypony\]</strong> my bad  
<strong>\<meeting-bot\> \[anonimal\]</strong> onion router similar to garlic routing.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Meh, its practically the same vegetable.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> lo  
<strong>\<meeting-bot\> \[fluffypony\]</strong> lol  
<strong>\<meeting-bot\> \[fluffypony\]</strong> we should go wild and create spinach routing  
<strong>\<meeting-bot\> \[anonimal\]</strong> lol  
<strong>\<meeting-bot\> \[anonimal\]</strong> “Kovri provides essential iron and vitamins”  
<strong>\<meeting-bot\> \[fluffypony\]</strong> <http://paulkieschedesign.com/blog/wp-content/uploads/2011/12/shandong-logo.jpg> \<- perfect  
<strong>\<meeting-bot\> \[anonimal\]</strong> “Eat kovri today”  
<strong>\<meeting-bot\> \[fluffypony\]</strong> the name, not the logo  
<strong>\<meeting-bot\> \[fluffypony\]</strong> so for a previous April 1 we renamed Monero to DarkFlarb, so I move that for next year April 1 we rename Kovri to Shandong  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ShanDong  
<strong>\<meeting-bot\> \[anonimal\]</strong> The ShanDong I2P Router project… hmm…  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: how do we keep track of \#282?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> lol  
<strong>\<meeting-bot\> \[fluffypony\]</strong> anonimal: othe and I will set it up and update in-ticket  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: thanks.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on \#282?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> nada  
<strong>\<meeting-bot\> \[anonimal\]</strong> If we use a dog somewhere in there, and Shandong, we should go with a pug.  
<strong>\<groeg\></strong> shandong = 山东 = mountain east  
<strong>\<meeting-bot\> \[fluffypony\]</strong> TIL  
<strong>\<meeting-bot\> \[anonimal\]</strong> The eastside rugged pug.  
<strong>\<groeg\></strong> (literal meaning of the characters)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> east mountain pugs unite  
<strong>\<meeting-bot\> \_ anonimal</strong> see dog flip gang symbol with fingers  
<strong>\<meeting-bot\> \[fluffypony\]</strong> DogeI2P  
<strong>\<meeting-bot\> \[anonimal\]</strong> Here we go, lol  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, 5. Closing \#226  
<strong>\<meeting-bot\> \[anonimal\]</strong> This is useful when: 1) i2p-relay is down 2) slack is not available or people aren’t signed up nor want to sign up  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ve registered the channels and am idling.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok so  
<strong>\<meeting-bot\> \[fluffypony\]</strong> are we happy running this under the core relay and not the community relay?  
<strong>\<meeting-bot\> \[anonimal\]</strong> By community you mean the one in \#monero/\#monero-dev?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> the community one is the one that needmoney90 runs, to Slack / Telegram etc.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> the core one is i2p-relay  
<strong>\<meeting-bot\> \[fluffypony\]</strong> anonimal: is there a \#tahoe-lafs on OFTC?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> because I don’t want to take tahoe-lafs out the relay list, necessarily  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: yes, with 4 people, no channel topic. Doesn’t look official.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok then I’ll just relay it, tough for them  
<strong>\<meeting-bot\> \[anonimal\]</strong> They will probably enjoy it.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> indeed  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok I’ll do that right now  
<strong>\<meeting-bot\> \[anonimal\]</strong> So this would be for i2p-relay?  
<strong>\<meeting-bot\> \_ anonimal</strong> so many relays, so confused  
<strong>\<meeting-bot\> \[fluffypony\]</strong> lol  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> What’s \#tahoe-lafs relation with kovri btw ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> moneromooo: Nothing really aside from an i2p plugin available to use with tahoe-lafs, AFAIK  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: if you’re doing it right now, I’ll wait.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> moneromooo: they asked me to run a relay, as their relay has disappeared  
<strong>\<meeting-bot\> \[anonimal\]</strong> Damn, it’s been an hour. Do we continue?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> yes - we started late  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I think it’s mostly up to you, the main kovri person.  
<strong>\<meeting-bot\> \_ anonimal</strong> didn’t want to stop on necessary bitmonero business  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: do you have to restart the relay? Is \#226 resolved?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> the bouncer is connected  
<strong>\<meeting-bot\> \[fluffypony\]</strong> sec  
<strong>\<theRelay\_\_\> \<fluffypony&#64;OFTC\></strong> testing  
<strong>\<fluffypony\></strong> testing back  
<strong>\<meeting-bot\> \[fluffypony\]</strong> and from here  
<strong>\<meeting-bot\> \[fluffypony\]</strong> meeting-bot might be interfering with it a little, so I’ll fiddle with it after I’ve killed meeting-bot  
<strong>\<meeting-bot\> \[anonimal\]</strong> It’s only me and the bot on OFTC  
<strong>\<meeting-bot\> \[anonimal\]</strong> Is fluffypony&#64;OFTC actually fluffypony&#64;Freenode ?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> no I don’t know - I need to check if it’s relaying between all 3, and can’t do that with meeting-bot online  
<strong>\<meeting-bot\> \[fluffypony\]</strong> coz meeting bot is also relaying  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, can we quickly review the remaining items?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> sure  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. Closing \#105  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hmm, tricky.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> sorry internet is slow  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok so  
<strong>\<meeting-bot\> \[fluffypony\]</strong> the moneroworld instance is up  
<strong>\<meeting-bot\> \[anonimal\]</strong> <https://social.moneroworld.com> went online but admin has not responded to anything in a month  
<strong>\<meeting-bot\> \[fluffypony\]</strong> hmmm  
<strong>\<meeting-bot\> \[anonimal\]</strong> There were multiple issues, probably still are, that would need to be resolved before we go officially public.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok then I think leave it open  
<strong>\<meeting-bot\> \[anonimal\]</strong> But it’s not kovri-related.  
<strong>\<meeting-bot\> \[anonimal\]</strong> That’s what annoys me. We have a forum post open for it.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And there’s also that /bitmonero ticket open  
<strong>\<meeting-bot\> \_ anonimal</strong> fetches  
<strong>\<meeting-bot\> \[anonimal\]</strong> \#903  
<strong>\<DaveyJones\></strong> gingeropolous aint that your site?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> anonimal: do we want a common gnu-social for the two?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> or separate?  
<strong>\<gingeropolous\></strong> wut?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I thought it would be an umbrella instance, more of a ‘pro-decentralization’ initiative not specific to kovri or bitmonero.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> <https://social.moneroworld.com> \<- your site ?  
<strong>\<gingeropolous\></strong> oh, DaveyJones , no… i just pay for the domain name and put it on afraid.org so anyone can create subdomains for free  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ve already signed up for @kovri and @anonimal at quitter.se in case this issue was never resolved.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Oh, that’s nice idea.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok  
<strong>\<meeting-bot\> \[fluffypony\]</strong> let’s leave it open and prod the guy again  
<strong>\<meeting-bot\> \[fluffypony\]</strong> if we hear nothing by next dev meeting we re-host from scratch  
<strong>\<meeting-bot\> \[anonimal\]</strong> quitter.se is nice aside from the psychopath/bot with the sickle and hammer avatar that spams the feed like there is no tomorrow.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, I’ll make a note.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 7. Closing \#46  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’m moving registrars for all critical domains, including getkovri.org  
<strong>\<meeting-bot\> \[fluffypony\]</strong> which is affecting that and the other one  
<strong>\<meeting-bot\> \[fluffypony\]</strong> (the increased attention means an increase of people poking at our infrastructure, hence the move)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ah, ok. How is content coming along? Did you get that rough draft finished?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> should be done by next meeting, and I’ll push the Kovri page to the Monero website in the next week so that we can open it up to the community to work on it  
<strong>\<meeting-bot\> \[fluffypony\]</strong> it’s in a sub-section of its own  
<strong>\<meeting-bot\> \[fluffypony\]</strong> so it can have as much content as required  
<strong>\<meeting-bot\> \[EinMByte\]</strong> nice, didn’t know we were getting a website  
<strong>\<meeting-bot\> \[anonimal\]</strong> Alright, I’ll make a note.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> EinMByte: I was going to do it in Geocities, but anonimal convinced me not to  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (then again, I probably missed a lot)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> snow flake mouse cursors are the bomb  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yeah, fluffypony has yet to learn the finer points of 90’s webdev.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> fo sho  
<strong>\<meeting-bot\> \[anonimal\]</strong> We’re working on that.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> Backstreet Boys backgrounds everywhere  
<strong>\<meeting-bot\> \[anonimal\]</strong> Once we get a logo, the site should look snazzy.  
<strong>\<meeting-bot\> \[anonimal\]</strong> ‘Kovri’s back, alright\!’  
<strong>\<meeting-bot\> \[fluffypony\]</strong> hah hah  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, 8. Closing \#27  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ah, looks like we’ve had some activity there lately.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Looks like two issues now. So, 1) updates on zoho? 2) should we ever have a mailing list?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> can’t proceed with Zoho till the domain move is done, but that’s basically setup  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I don’t think mailing lists are necessary  
<strong>\<meeting-bot\> \[fluffypony\]</strong> we already have stuff scattered everywhere, another avenue will just make dissipate it more  
<strong>\<meeting-bot\> \[anonimal\]</strong> Agreed.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> ever ? maybe, now ? no  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: ETA on domain move completion (or did you already say?… /me reads)?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> anonimal: by next meeting  
<strong>\<meeting-bot\> \[fluffypony\]</strong> if it’s done sooner then great  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, great. Once that’s resolved we can resolve the HackerOne issue.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Which will be another avenue for more attention.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ll make a note in \#27.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on \#27?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> nope that’s it for now  
<strong>\<meeting-bot\> \[anonimal\]</strong> 9. Any additional meeting items  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte, how goes it?  
<strong>\<guzzi\></strong> present fgi  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi guzzi.  
<strong>\<meeting-bot\> \[anonimal\]</strong> guzzi: anything you wanted to add to the meeting?  
<strong>\<guzzi\></strong> glad to be a back. learning a lot.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Hopefully some work on SSU soon  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: I had thoughts and questions on library design if you’re around after the meeting  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Sure  
<strong>\<guzzi\></strong> looking to focus more on kovri since it has the least devs and is more easy to peneatrate into development.  
<strong>\<guzzi\></strong> still getting up to speed.  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: nice, I look forward to the day we merge that branch.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> guzzi: If you’re looking for easy stuff to get used to the code, tests and documentation are very much needed so that might be a good idea  
<strong>\<meeting-bot\> \[anonimal\]</strong> guzzi: ok, if you have any questions, feel free to shout out.  
<strong>\<meeting-bot\> \[anonimal\]</strong> solmar: ^ what EinMByte said too if interested.  
<strong>\<guzzi\></strong> EinMByte, thanks on it.  
<strong>\<guzzi\></strong> i will look for todos.  
<strong>\<guzzi\></strong> an prs on that  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: you wanted to talk about \#325?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> oh - not necessarily, it was more to find out if it needed discussion  
<strong>\<meeting-bot\> \[solmar\]</strong> i’ll check it out thanks ;)  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: I think \#325 is more of a ‘po-tey-to’ ‘po-tah-to’ kind of issue  
<strong>\<meeting-bot\> \[anonimal\]</strong> and a possible solution is ‘let’s call the whole thing off’.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ll figure itself out.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 9.? Any more meeting items?  
<strong>\<meeting-bot\> \[anonimal\]</strong> With organizational things out of the way, the next meeting can be far more codebase-orieted.  
<strong>\<meeting-bot\> \[anonimal\]</strong> \*oriented  
<strong>\<meeting-bot\> \[fluffypony\]</strong> kk  
<strong>\<meeting-bot\> \[anonimal\]</strong> 10. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[fluffypony\]</strong> <https://99designs.com/logo-design/contests/create-beautiful-logo-kovri-privacy-enhancing-open-source-652257/entries>  
<strong>\<meeting-bot\> \[fluffypony\]</strong> <https://99designs.com/logo-design/contests/create-beautiful-logo-kovri-privacy-enhancing-open-source-652257/brief> that thing  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: nice  
<strong>\<meeting-bot\> \[fluffypony\]</strong> k next meeting, same time, same place, 2 weeks  
<strong>\<meeting-bot\> \[anonimal\]</strong> Where’s the ‘optional dog’ button?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> Two Weeks (tm)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Do we have to do 2 weeks?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> you want to do longer?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> or shorter?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I mean, I guess it depends on who is involved. If it’s the usual, then I’d say 1 month.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> guzzi / solmar / EinMByte - thoughts ?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> We can discuss some of the more technical things separately  
<strong>\<guzzi\></strong> 1 mo fine. i will be on irc for technical things. still playing catch up.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> ok  
<strong>\<meeting-bot\> \[fluffypony\]</strong> then we do it in 4 weeks, same time as the meeting after next Monero dev meeting?  
<strong>\<meeting-bot\> \[solmar\]</strong> 1 month is fine  
<strong>\<meeting-bot\> \[solmar\]</strong> i’ll be around as often as i can  
<strong>\<meeting-bot\> \[anonimal\]</strong> Same time is fine with me.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> thankyouverymuch\!  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, thanks everyone.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> can I kill meeting-bot?  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: swift and painless if possible.  
\*\*\<meeting-bot\> \[anonimal\]\*\* She need not suffer.
