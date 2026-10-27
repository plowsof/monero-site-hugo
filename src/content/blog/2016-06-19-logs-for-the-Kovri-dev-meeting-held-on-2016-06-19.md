---
title: Logs for the Kovri Dev Meeting Held on 2016-06-19
summary: Brief review of what has been completed since last meeting, C++ specific discussion, closed and open issues
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<fluffypony\></strong> ok I guess we move on to Kovri - anonimal, the floor is yours  
<strong>\<meeting-bot\> \[anominal\]</strong> From agenda <https://github.com/monero-project/kovri/issues/192>  
<strong>\<meeting-bot\> \[anominal\]</strong> 17:00 (UTC)  
<strong>\<meeting-bot\> \[anominal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anominal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anominal\]</strong> 3. C++ specific discussion (carried over from June 5th meeting)  
<strong>\<meeting-bot\> \[anominal\]</strong> 4. Review open tickets (assigned and/or unassigned): status, code ideas (if applicable), etc.  
<strong>\<meeting-bot\> \[anominal\]</strong> 5. Discuss any pertinent TODO’s  
<strong>\<meeting-bot\> \[anominal\]</strong> 6. Any additional meeting items  
<strong>\<meeting-bot\> \[anominal\]</strong> 7. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anominal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anominal\]</strong> Hi  
<strong>\<meeting-bot\> \[anominal\]</strong> EinMByte: present?  
<strong>\<fluffypony\></strong> there’s 2x greetings?  
<strong>\<fluffypony\></strong> best meeting ever  
<strong>\<meeting-bot\> \[anominal\]</strong> lol  
<strong>\<meeting-bot\> \[anominal\]</strong> Well, EinMByte is here but not present.  
<strong>\<fluffypony\></strong> k  
<strong>\<meeting-bot\> \[anominal\]</strong> Moving on,  
<strong>\<meeting-bot\> \[anominal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anominal\]</strong> A somewhat productive two weeks in contrasting areas. Highlights include:  
<strong>\<meeting-bot\> \[anominal\]</strong> - New —log-levels runtime feature  
<strong>\<meeting-bot\> \[anominal\]</strong> - Security fix in Garlic/ElGamal  
<strong>\<meeting-bot\> \[anominal\]</strong> - New user-agent scrubber  
<strong>\<meeting-bot\> \[anominal\]</strong> - Bump to 0.9.26  
<strong>\<meeting-bot\> \[anominal\]</strong> - Coverity coverage via travis-ci (though problematic, see \#209)  
<strong>\<meeting-bot\> \[anominal\]</strong> - Design refactoring, misc. refactoring, code documentation  
<strong>\<meeting-bot\> \[anominal\]</strong> 6 closed issues  
<strong>\<meeting-bot\> \[anominal\]</strong> 2 new standing issues  
<strong>\<meeting-bot\> \[anominal\]</strong> fluffypony: have you had a chance to complete anything since previous meeting?  
<strong>\<fluffypony\></strong> anonimal: like 80%-ish done with the Kovri page on the site, per the info you gave me + the docs  
<strong>\<fluffypony\></strong> s/page/section  
<strong>\<meeting-bot\> \[anominal\]</strong> Great, I’m looking forward to it.  
<strong>\<meeting-bot\> \[anominal\]</strong> Do you think it will be finished before next meeting?  
<strong>\<fluffypony\></strong> yes definitely  
<strong>\<meeting-bot\> \[anominal\]</strong> Yay, sounds exciting.  
<strong>\<meeting-bot\> \[anominal\]</strong> Anything else on 2.?  
<strong>\<meeting-bot\> \[anominal\]</strong> Going once… going twice…  
<strong>\<meeting-bot\> \[anominal\]</strong> 3. C++ specific discussion (carried over from June 5th meeting)  
<strong>\<meeting-bot\> \[anominal\]</strong> Well, I was hoping to merge this in with 4. and chat with EinMByte since he said he’d be here.  
<strong>\<fluffypony\></strong> is this wrt the C++ standard ?  
<strong>\<fluffypony\></strong> or the style guide stuff?  
<strong>\<meeting-bot\> \[anominal\]</strong> Anything C++, I imagined.  
<strong>\<meeting-bot\> \[anominal\]</strong> I was hoping to focus on C++ related to \#187, but I haven’t looked at \#187 since it was opened.  
<strong>\<meeting-bot\> \[anominal\]</strong> Have any bitmonero devs taken an interest in Kovri yet?  
<strong>\<meeting-bot\> \[anominal\]</strong> Its quite the beast, and needs much taming.  
<strong>\<fluffypony\></strong> I don’t think anyone has yet  
<strong>\<tewinget\></strong> anonimal: passing interest at best for me  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok, good to know.  
<strong>\<tewinget\></strong> I more or less know what it is, but I haven’t looked into tinkering with it yet.  
<strong>\<moneromooo\></strong> I think the problem is that the time I’d spend hacking on anything, I wouldn’t spend on monero anymore :)  
<strong>\<fluffypony\></strong> s’true  
<strong>\<meeting-bot\> \[anominal\]</strong> I totally understand.  
<strong>\<fluffypony\></strong> there will be a bleed area between the two when integration happens  
<strong>\<meeting-bot\> \[anominal\]</strong> That makes, so patience and persistence seems to be the key.  
<strong>\<meeting-bot\> \[anominal\]</strong> \*makes sense  
<strong>\<meeting-bot\> \[anominal\]</strong> Well, anonymity has a certain taste too. Maybe I’m one of the few fanatics who enjoy working on it ;)  
<strong>\<fluffypony\></strong> I think most of us are here because we’re pro-privacy  
<strong>\<meeting-bot\> \[anominal\]</strong> Anyway, I look forward to the meeting of the minds, I like what I’ve seen in bitmonero dev.  
<strong>\<meeting-bot\> \[anominal\]</strong> Yes, good point.  
<strong>\<fluffypony\></strong> which is awesome :)  
<strong>\<meeting-bot\> \[anominal\]</strong> Anything else on 3.? Any questions?  
<strong>\<meeting-bot\> \[anominal\]</strong> Alrighty, moving on,  
<strong>\<meeting-bot\> \[anominal\]</strong> 4. Review open tickets (assigned and/or unassigned): status, code ideas (if applicable), etc.  
<strong>\<meeting-bot\> \[anominal\]</strong> Let’s see,  
<strong>\<fluffypony\></strong> anonimal, also, if EinMbyte can’t make the meeting maybe we must collate stuff and raise it on his behalf ?  
<strong>\<meeting-bot\> \[anominal\]</strong> How so?  
<strong>\<fluffypony\></strong> like if he just adds to the agenda then we can discuss it without him needing to be here  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok, well he’s welcome to do that.  
<strong>\<meeting-bot\> \[anominal\]</strong> But he and I are great at bouncing ideas off each other and getting to core issues, so I wish he would be present more often.  
<strong>\<meeting-bot\> \[anominal\]</strong> I see, so we’ll send him a note to add to the agenda regardless of his attending?  
<strong>\<fluffypony\></strong> yes I think that would help, he lacks time at the moment  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok.  
<strong>\<meeting-bot\> \* anonimal</strong> back to 4.  
<strong>\<meeting-bot\> \[anominal\]</strong> \#210 might be an easy fix, if any bitmonero devs want to take a peek.  
<strong>\<fluffypony\></strong> once you go Kovri you never go…uh…something that rhymes with Kovri  
<strong>\<meeting-bot\> \[anominal\]</strong> lol  
<strong>\<meeting-bot\> \[anominal\]</strong> That’s a tough one…  
<strong>\<fluffypony\></strong> <https://github.com/monero-project/kovri/issues/210> \<- for reference  
<strong>\<meeting-bot\> \[anominal\]</strong> Remaining tickets are mostly all hard-core. I’ll see what I can get into before the next meeting. Obviously the big ones would be nice if I can make the time.  
<strong>\<meeting-bot\> \[anominal\]</strong> I may pick at \#191 or \#187 because I get irritated with severely broken things.  
<strong>\<meeting-bot\> \[anominal\]</strong> Or who knows what, the world is full of mysterious and discovery.  
<strong>\<fluffypony\></strong> lol  
<strong>\<meeting-bot\> \[anominal\]</strong> \*mystery  
<strong>\<meeting-bot\> \[anominal\]</strong> lol  
<strong>\<fluffypony\></strong> invent a time machine \!  
<strong>\<meeting-bot\> \[anominal\]</strong> pffffffffff  
<strong>\<meeting-bot\> \[anominal\]</strong> That would be fun.  
<strong>\<fluffypony\></strong> :-P  
<strong>\<meeting-bot\> \[anominal\]</strong> Does anyone here work with Debian Jessie often?  
<strong>\<fluffypony\></strong> tewinget is an Arch user  
<strong>\<fluffypony\></strong> moneromooo wrote his own OS from scratch I’m sure  
<strong>\<fluffypony\></strong> osensei maybe  
<strong>\<fluffypony\></strong> but he’s not around atm  
<strong>\<moneromooo\></strong> I use a pretty common one nowdays actually.  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok just curious. Arch here so \#210 will probably take more than a few moments.  
<strong>\<fluffypony\></strong> moneromooo: Windows XP ?  
<strong>\<meeting-bot\> \[anominal\]</strong> ^ Windows 98  
<strong>\<moneromooo\></strong> Good point. I guess it’s not that common. I forgot about windows.  
<strong>\<meeting-bot\> \[anominal\]</strong> 95 was better at breaking.  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok, well re: 4., fluffypony have you see \#209?  
<strong>\<fluffypony\></strong> probably  
<strong>\<meeting-bot\> \[anominal\]</strong> 50% yay because we solved the coverity/travis issue\!  
<strong>\<fluffypony\></strong> oh yes the Coverity thing  
<strong>\<fluffypony\></strong> ok so plz update me - Travis builds are now work  
<strong>\<fluffypony\></strong> \*working  
<strong>\<fluffypony\></strong> but Coverity isn’t triggering ?  
<strong>\<meeting-bot\> \[anominal\]</strong> No, we are \*finally\* triggering, but now coverity says build is failing on their end.  
<strong>\<meeting-bot\> \[anominal\]</strong> So, travis says “we’re fine”, coverity says “you’re not fine but neither is most of my site”.  
<strong>\<meeting-bot\> \[anominal\]</strong> Because they really do have some issues there and support is… meh.  
<strong>\<fluffypony\></strong> LOL  
<strong>\<fluffypony\></strong> considering how long it took for their site to pick Travis up I’m not even surprised  
<strong>\<fluffypony\></strong> do we wait until they’ve fixed it, or keep pushing  
<strong>\<meeting-bot\> \[anominal\]</strong> Seriously, and their “community” site is still offline despite “we’ll be back in early 2016\!”.  
<strong>\<meeting-bot\> \[anominal\]</strong> It’s June already…  
<strong>\<meeting-bot\> \[anominal\]</strong> Good question,  
<strong>\<meeting-bot\> \[anominal\]</strong> I can review \*why\* they think our build failed, I could even try to do it manually.  
<strong>\<meeting-bot\> \[anominal\]</strong> I may have to do it manually just to get things going \*or\*, it could be another travis/coverity issue (or just pure coverity).  
<strong>\<fluffypony\></strong> maybe we must switch to manual Coverity  
<strong>\<fluffypony\></strong> and just do it once every two weeks  
<strong>\<meeting-bot\> \[anominal\]</strong> Sounds fair, I’ll give it shot before next meeting.  
<strong>\<meeting-bot\> \* anonimal</strong> before I forget, opens <https://github.com/monero-project/kovri/issues/assigned/fluffypony>  
<strong>\<meeting-bot\> \[anominal\]</strong> fluffypony: Any updates on \#27?  
<strong>\<meeting-bot\> \* anonimal</strong> knows you’ve been busy, simply curious  
<strong>\<fluffypony\></strong> anonimal: no - also, we’re switching providers  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok.  
<strong>\<fluffypony\></strong> debating Zoho vs. FastMail  
<strong>\<fluffypony\></strong> ProtonMail doesn’t do multiple users on a domain, unfortunately  
<strong>\<meeting-bot\> \[anominal\]</strong> Hmmm…  
<strong>\<meeting-bot\> \[anominal\]</strong> Pros/Cons so far re: providers?  
<strong>\<fluffypony\></strong> well they’re mostly doing forwarding and SMTP, so it’s pretty open  
<strong>\<fluffypony\></strong> part of the decision making is cost, part is also reliability and if they feature reasonable web interfaces for those inevitable users that don’t want to use a mail client  
<strong>\<fluffypony\></strong> will wrap that up soon, it’s on my short list  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok, good to know.  
<strong>\<meeting-bot\> \[anominal\]</strong> I don’t have an opionion so far. If I do I’ll be sure to chip in.  
<strong>\<meeting-bot\> \[anominal\]</strong> Is xmrpromotions there? re: \#105  
<strong>\<fluffypony\></strong> no not online atm  
<strong>\<fluffypony\></strong> I’ll prod them for that when I see them next  
<strong>\<meeting-bot\> \[anominal\]</strong> K.  
<strong>\<meeting-bot\> \* anonimal</strong> typing  
<strong>\<meeting-bot\> \[anominal\]</strong> I’ll most likely take a look at bitmonero’s 0MQ work too before next meeting (thinking of \#53).  
<strong>\<meeting-bot\> \[anominal\]</strong> Other than that, I may just grab some low hanging fruit before next meeting and work on the mingw build and other smaller tickets.  
<strong>\<tewinget\></strong> anonimal, feel free to direct any 0mq questions at <del>fluffypony</del> me  
<strong>\<meeting-bot\> \[anominal\]</strong> Thanks tewinget.  
<strong>\<fluffypony\></strong> oh yeah speaking of  
<strong>\<tewinget\></strong> sad that my IRC client doesn’t support strikeout…hoping someone else’s does  
<strong>\<fluffypony\></strong> the Windows test box is borked  
<strong>\<fluffypony\></strong> msys2 decided to give up the ghost  
<strong>\<fluffypony\></strong> so doing a complete reinstall of it  
<strong>\<meeting-bot\> \[anominal\]</strong> Yeah, so what happened? Any idea?  
<strong>\<fluffypony\></strong> no clue  
<strong>\<meeting-bot\> \[anominal\]</strong> (very strange)  
<strong>\<tewinget\></strong> On a scale from 1 to I hate compiling anything on Windows: I hate compiling anything on Windows.  
<strong>\<tewinget\></strong> it’s a binary scale.  
<strong>\<meeting-bot\> \[anominal\]</strong> Oh windows, you never cease to disappoint me.  
<strong>\<meeting-bot\> \[anominal\]</strong> Anything else on 4.?  
<strong>\<meeting-bot\> \* anonimal</strong> quick reviewing  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Hi, I’m late sorry  
<strong>\<meeting-bot\> \[anominal\]</strong> EinMByte\! Welcome back.  
<strong>\<fluffypony\></strong> wb EinMByte  
<strong>\<fluffypony\></strong> still 15 minutes left :)  
<strong>\<meeting-bot\> \[anominal\]</strong> With 15 minutes or so to spare, any input? (much backlog)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Something about \#210 maybe: I’ll provide some more information  
<strong>\<meeting-bot\> \[anominal\]</strong> EinMByte: before I forget and while you’re here: what is your preferred/most-reliable public contact method?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> public as in to put on a website or so, or as in where you guys can contact me  
<strong>\<meeting-bot\> \[anominal\]</strong> So we can contact you.  
<strong>\<meeting-bot\> \[anominal\]</strong> And would you be interested in leaving agenda TODO’s/notes in meeting tickets in case you can’t make a meeting that you’d hope to make?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Well I’ll be on IRC, or else <einmbyte@mail.i2p> or github  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> sure  
<strong>\<meeting-bot\> \[anominal\]</strong> fluffypony: did I word that correctly?  
<strong>\<meeting-bot\> \[anominal\]</strong> EinMByte: we’re still on point 4. “reviewing tickets”, etc.  
<strong>\<meeting-bot\> \[anominal\]</strong> Is there anything you wanted to add re: SSU?  
<strong>\<meeting-bot\> \* anonimal</strong> knows you just got back to working on it  
<strong>\<fluffypony\></strong> yes I think so  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Well I can give you a quick status update  
<strong>\<meeting-bot\> \[anominal\]</strong> Awesome.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So SSUSession.cpp is now using the new parsing code, except for the fragments  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (I have the code to parse data packets, just not using it yet)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I am slowed down right now due to a bug, with the header I suspect  
<strong>\<meeting-bot\> \[anominal\]</strong> Grrr… bugs…  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (Rekey options being set etc when this shouldn’t happen, I think it’s all related)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Well, I’ll try to fix it in the next days  
<strong>\<meeting-bot\> \[anominal\]</strong> bitmonero devs: FYI, SSU is the ugly High School girl standing in the corner of the dance hall that no one will dance with because she is awkward and is a very mean person.  
<strong>\<fluffypony\></strong> lol  
<strong>\<meeting-bot\> \[anominal\]</strong> In other words, SSU has needed much love and I’m glad EinMByte has tackled the challenge.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Hah, nice comparison - although it does make me seem quite desperate :P  
<strong>\<meeting-bot\> \[anominal\]</strong> lol, oops. Sorry EinMByte, I didn’t mean it that way :(  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Once the parsing part is done, I’ll do something similar to build the packets  
<strong>\<meeting-bot\> \[anominal\]</strong> Sounds great.  
<strong>\<meeting-bot\> \[anominal\]</strong> How about, EinMByte dances with her because he is a leader and willing to show great sympathy to those who need it most.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I’ll write some tests, but don’t expect full coverage just yet. I don’t think that’s a priority right now.  
<strong>\<meeting-bot\> \[anominal\]</strong> And turns down the more promising dancers to make SSU work well.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (I want to get the API started too)  
<strong>\<meeting-bot\> \* anonimal</strong> sorry, I’m getting carried away  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok.  
<strong>\<meeting-bot\> \[anominal\]</strong> Do you have an idea of schedule coming up?  
<strong>\<meeting-bot\> \[anominal\]</strong> (as in availability)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: You’re making a lot of assumptions about my gender here :). But let’s see how well that dance turns out  
<strong>\<meeting-bot\> \[anominal\]</strong> I know, again my apologies.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, next week I’ll be mostly available (several hours per day)  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok. I’ll check my IRC more frequently then.  
<strong>\<meeting-bot\> \[anominal\]</strong> Anything else on 4.?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Well as I said I’ll put up more info for \#210  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Seems like 2 tests are failing  
<strong>\<meeting-bot\> \[anominal\]</strong> Since we’re out of time, I don’t see much on 5. except for a couple of quirky core ones that I may get to before next meeting.  
<strong>\<meeting-bot\> \[anominal\]</strong> Any comments on 5.?  
<strong>\<fluffypony\></strong> EinMByte: well you can dance with SSUzy regardless of your gender  
<strong>\<meeting-bot\> \[anominal\]</strong> SSUzy, lol.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony: or my ability to dance :p  
<strong>\<fluffypony\></strong> everyone can dance, it’s just a matter of how badly (or well)  
<strong>\<meeting-bot\> \[anominal\]</strong> Paraplegics?  
<strong>\<meeting-bot\> \* anonimal</strong> doesn’t do off-topic very often, quite the release.  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok so if no thoughts on 5.,  
<strong>\<fluffypony\></strong> LOL  
<strong>\<fluffypony\></strong> nobody is going to attend the Kovri meeting in future :-P  
<strong>\<meeting-bot\> \[anominal\]</strong> LMAO  
<strong>\<meeting-bot\> \* anonimal</strong> watches ship sailing away, burning in the distance  
<strong>\<meeting-bot\> \[EinMByte\]</strong> See you all next time in \#dancing  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok, last call for 5. Discuss any pertinent TODO’s  
<strong>\<fluffypony\></strong> I think that’s it from my side  
<strong>\<fluffypony\></strong> lol EinMByte  
<strong>\<meeting-bot\> \[anominal\]</strong> lol, or \#dancing-dev  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Well, for 5: If anyone wants to start on the API, you’re welcome  
<strong>\<meeting-bot\> \[EinMByte\]</strong> This also applies to all (any?) monero people reading this  
<strong>\<meeting-bot\> \[anominal\]</strong> Good point, that’s another big item to tackle.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Since you’re going to be the people using the API, making up a list of requirements would be nice  
<strong>\*\<fluffypony\></strong> kk  
<strong>\<meeting-bot\> \[anominal\]</strong> 6. Any additional meeting items  
<strong>\<meeting-bot\> \[anominal\]</strong> Just one from me, briefly,  
<strong>\<fluffypony\></strong> I think we’ve already discussed EinMByte’s dancing enough, so nothing more from me on 6  
<strong>\<meeting-bot\> \[anominal\]</strong> Forum Funding. I plan on writing up some proposals within the next month or so.  
<strong>\<fluffypony\></strong> kk  
<strong>\<meeting-bot\> \[anominal\]</strong> EinMByte: if you were crowdfunded on FFS, would you be able to devote any more dev time?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I’ve already told fluffypony, not really  
<strong>\<meeting-bot\> \[anominal\]</strong> Ok.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> If you can build me a time machine, yes  
<strong>\<meeting-bot\> \* anonimal</strong> was planning proposals to fund my work  
<strong>\<meeting-bot\> \[anominal\]</strong> Funny, fluffypony mentioned that earlier (time machine).  
<strong>\<fluffypony\></strong> lol  
<strong>\<meeting-bot\> \[anominal\]</strong> We should invest in one. The writing is on the wall.  
<strong>\<meeting-bot\> \[anominal\]</strong> Last call for 6.  
<strong>\<fluffypony\></strong> new project for the Monero Research Lab to tackle  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But, as I’ve also told fluffypony, please do fund other programmers  
<strong>\<meeting-bot\> \[anominal\]</strong> Agreed.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Apparently you first need the programmer (before getting the money) so let’s go find some C++ programmers  
<strong>\<meeting-bot\> \[anominal\]</strong> fluffypony: ^ we should devote an entire meeting to that IMHO sometime within the next few months.  
<strong>\<fluffypony\></strong> yeah definitely  
<strong>\<grimpants\></strong> would love to see a FFS proposal for kovri/i2p dev  
<strong>\<fluffypony\></strong> grimpants: we’ve had open-ended stuff before, the funds just sit there and no dev comes along - we need to first find someone interested that can price in their work, even if it’s on a full time commitment for X long  
<strong>\<meeting-bot\> \[EinMByte\]</strong> By the way, we don’t need only expert C++ programmers  
<strong>\<fluffypony\></strong> and then we can raise funds accordingly  
<strong>\<grimpants\></strong> i see  
<strong>\<grimpants\></strong> been a while since ive check tbh  
<strong>\<meeting-bot\> \[EinMByte\]</strong> We can use people who just write documentation / tests too  
<strong>\<meeting-bot\> \[anominal\]</strong> ^ which is a great way for newcomers to learn the codebase.  
<strong>\<fluffypony\></strong> this may not be an honourable line of thought, but I’ve been wondering if there’s any fall-out from the issues Tor are facing that might lead to some new contributors looking at Kovri  
<strong>\<meeting-bot\> \[anominal\]</strong> Good concern, I think that’s very plausible.  
<strong>\<meeting-bot\> \[anominal\]</strong> But the devoted C person usually scoffs at C++ and turn their nose at Java.  
<strong>\<fluffypony\></strong> like hyc :-P  
<strong>\<meeting-bot\> \[anominal\]</strong> I’ve become spoiled with STL so, I can’t vouch for C devotees on more complex apps like Kovri.  
<strong>\<meeting-bot\> \[anominal\]</strong> But bigger point:  
<strong>\<meeting-bot\> \[anominal\]</strong> The world needs more options, so if Tor starts to burn, another ship will be ready.  
<strong>\<meeting-bot\> \[anominal\]</strong> Some great minds there, so I’m not concerned about the near future.  
<strong>\<meeting-bot\> \[anominal\]</strong> But that was a hefty loss on their end with the one who shall remain nameless.  
<strong>\<fluffypony\></strong> yeah, and the larger loss is how much emotional damage it did to people during the time it was kept hidden  
<strong>\<fluffypony\></strong> as a community I hope we can learn from that and call people out when they’re out of line  
<strong>\<meeting-bot\> \[anominal\]</strong> Yeah, everyone involved seems to have taken a loss.  
<strong>\<meeting-bot\> \[anominal\]</strong> So, regarding that in relation to ship-jumpers: I think we should continue on our track of availability, professionalism, quality, code correctness and maintainability,  
<strong>\<fluffypony\></strong> 100%  
<strong>\<meeting-bot\> \[anominal\]</strong> But,  
<strong>\<meeting-bot\> \[EinMByte\]</strong> let’s first get some people :)  
<strong>\<meeting-bot\> \[anominal\]</strong> devs can be strong in their ways, so being malleable is also important (but that’s a given). Constant ebb and flow.  
<strong>\<meeting-bot\> \[anominal\]</strong> Anything else on 6.?  
<strong>\<fluffypony\></strong> that’s it from my side  
<strong>\<meeting-bot\> \[anominal\]</strong> 7. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anominal\]</strong> Same time in two weeks?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Nothing else from me  
<strong>\<fluffypony\></strong> yes same time in two weeks  
<strong>\<meeting-bot\> \[anominal\]</strong> Alright. A million thanks to everyone.  
<strong>\<fluffypony\></strong> taking meeting-bot down
