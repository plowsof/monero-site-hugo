---
title: Logs for the Kovri Dev Meeting Held on 2016-10-30
summary: Brief review of what has been completed since last meeting, Kovri Logo, Salti, and code & open tickets discussion
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<fluffypony\></strong> alright anonimal, the floor is yours  
<strong>\<meeting-bot\> \[anonimal\]</strong> Proposed meeting items:  
<strong>\<meeting-bot\> \[anonimal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what's been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. @fluffypony's request for finished logo  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. ∫alti as Monero project  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. [libqtoopie](https://github.com/EinMByte/qtoopie/issues/1)  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. Preparing for pre-alpha release  
<strong>\<meeting-bot\> \[anonimal\]</strong> 7. Code + ticket discussion / Q &amp; A  
<strong>\<meeting-bot\> \[anonimal\]</strong> 8. Any additional meeting items  
<strong>\<meeting-bot\> \[anonimal\]</strong> 9. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Hi  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Hi  
<strong>\<meeting-bot\> \[i2p-relay\] {-pero}</strong> hi  
<strong>\<meeting-bot\> \[olark\]</strong> Greetings.  
<strong>\<boomlol23\></strong> hi  
<strong>\<fluffypony\></strong> ola  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> hi  
<strong>\<maoam\></strong> hi  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what's been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> Lots of refactoring, some fixes.  
<strong>\<meeting-bot\> \[anonimal\]</strong> New contributor olark/olarks\!  
<strong>\<meeting-bot\> \[anonimal\]</strong> Welcome olark\!  
<strong>\<meeting-bot\> \[olark\]</strong> o/  
<strong>\<fluffypony\></strong> welcome olark  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 2.?  
<strong>\<meeting-bot\> \[anonimal\]</strong> (olark has been doing great work + tackling a huge learning curve. very cool)  
<strong>\<fluffypony\></strong> olark  
<strong>\<meeting-bot\> \[olark\]</strong> lots of refactoring ;)  
<strong>\<fluffypony\></strong> maybe you can give us a brief background on you  
<strong>\<meeting-bot\> \[i2p-relay\] {-Slack} \<nanoakron\></strong> How’s the documentation looking to make that learning curve more shallow for future developers?  
<strong>\<meeting-bot\> \[anonimal\]</strong> (e.g., favourite book, long walks on the beach, etc.)  
<strong>\<meeting-bot\> \[anonimal\]</strong> nanoakron: moneropedia. We can talk more about that at the end of the meeting too.  
<strong>\<meeting-bot\> \[olark\]</strong> Have been programming for the last 3-4 years on and off. Just getting back into C++ have followed Monero and Kovri for the last year or so and figured I should stop procrastinating and help move things forward.  
<strong>\<fluffypony\></strong> olark: <https://i.imgur.com/9AQYqBr.png>  
<strong>\<meeting-bot\> \[olark\]</strong> Also long time i2p user, so I know what's up.  
<strong>\<meeting-bot\> \[anonimal\]</strong> lol, badge of honor.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Alright, well we're glad to have more hands on deck.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else before moving onto 3.?  
<strong>\<meeting-bot\> \[olark\]</strong> Haha thanks fluffypony  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. fluffypony's request for finished logo  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: ^  
<strong>\<fluffypony\></strong> yes  
<strong>\<fluffypony\></strong> ok this logo has taken WAY too much time  
<strong>\<fluffypony\></strong> I know that logos are kinda-permanent, but it's holding other stuff up  
<strong>\<boomlol23\></strong> why are all msgs going through meetingbot..  
<strong>\<fluffypony\></strong> boomlol23: because we're spread out over multiple networks  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: what's the best solution for now?  
<strong>\<boomlol23\></strong> ok  
<strong>\<fluffypony\></strong> I'd like to have the logo by the end of the meeting  
<strong>\<fluffypony\></strong> if colours are an issue let's just stick with the original colours  
<strong>\<fluffypony\></strong> we can ALWAYS change it later  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Wait, we still haven't decided on the logo?  
<strong>\<fluffypony\></strong> EinMByte: we have  
<strong>\<fluffypony\></strong> but then there were font and kerning and colour changes  
<strong>\<ontario\></strong> new monero logo?  
<strong>\<meeting-bot\> \[anonimal\]</strong> ontario: kovri logo  
<strong>\<fluffypony\></strong> ontario: no Kovri logo, we're in the Kovri meeting now  
<strong>\<ontario\></strong> k sry  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, can pero send you the finished work then?  
<strong>\<fluffypony\></strong> np :)  
<strong>\<fluffypony\></strong> yes please  
<strong>\<sornros\></strong> may I ask if I understood correctly that the i2p code will be rewritten in c++?  
<strong>\<meeting-bot\> \* anonimal</strong> has to move onto next item....  
<strong>\<fluffypony\></strong> either uploading somewhere or <ric@getmonero.org>  
<strong>\<pero\></strong> i thought i 'submitted' the final one last weekend - i'd like to make one tiny half pixel change if i can  
<strong>\<meeting-bot\> \[anonimal\]</strong> sornros: we can answer more after the meeting  
<strong>\<fluffypony\></strong> sornros: it already is being - <https://github.com/monero-project/kovri>  
<strong>\<pero\></strong> i'll email it to both fluffypony and anonimal shortly  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 3.?  
<strong>\<sornros\></strong> thanks  
<strong>\<pero\></strong> with the monero colors  
<strong>\<fluffypony\></strong> no that's anonimal, tks  
<strong>\<pero\></strong> <http://imgur.com/a/xCaZV> fyi  
<strong>\<fluffypony\></strong> that's it  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. ∫alti as Monero project  
<strong>\<fluffypony\></strong> pero: ok perfect - if you can send it to me after the pixel change  
<strong>\<meeting-bot\> \[EinMByte\]</strong> sure  
<strong>\<pero\></strong> half-pixel :P  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: I had some thoughts unless you wanted to dive into anything first  
<strong>\<sornros\></strong> thats a nice logo, I like the font too  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: No go ahead  
<strong>\<meeting-bot\> \[anonimal\]</strong> We've moved on sornros.  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: since I haven't spent any time researching webextensions, can we <em>for sure</em> do what we want to achieve with XUL/XPCOM?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I'm thinking we consider brushing aside the deprecation issue for now and someone can pick it up in the future?  
<strong>\<PowerFlower\></strong> hi sorry for being late -\_- I hope its not too late. Simple question: Will be the GUI released before the next XMR core release in ?Januaray?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> It depends what exactly we want to achieve  
<strong>\<meeting-bot\> \[anonimal\]</strong> If we <em>can</em> do that now, we could move it into monero-project and it will gain more attention.  
<strong>\<fluffypony\></strong> PowerFlower: this is the Kovri meeting, you'll have to hold that question for later  
<strong>\<PowerFlower\></strong> okay :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: well, the easy stuff for starters re: profile. We can do that, right?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: If we accept that the user will have to use the plugin with a separate profile, then we can do everything we need with webextensions I guess  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Can we create the profile using webextensions? Probably not  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Then again, people are apparently smart enough to run TBB, so if necessary we can create a script to create the firefox profile  
<strong>\<meeting-bot\> \[anonimal\]</strong> I think that was what we were going for  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Problem with XUL is that 1) it's deprecated so development will only get worse for us 2) harder to port to other browsers (contrary to webextensions)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> It seems like a bad idea to start creating a plugin with deprecated technology  
<strong>\<meeting-bot\> \[anonimal\]</strong> Where's the definite deprecation date though?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> There is none (very vague, IIRC)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> It's also not clear if e.g. it will be deprecated for firebird  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (in fact, does anyone know if firebird itself is (going to be) deprecated?)  
<strong>\<meeting-bot\> \* anonimal</strong> doesn't know  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, we are in a good position to influence webext development: they are still taking feature requests, etc. If we get <em>something</em> going now, there is a far better likely hood of a webdev coming along to contribute than if we have a mostly empty repo.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And I can't find a date for deprecation, should we really base a great idea on what-if's?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, I agree. My spare time does not though  
<strong>\<meeting-bot\> \[anonimal\]</strong> I know, nor mine, but I've semi-frequently seen people popping in and out of \#monero-dev wanting to contribute to non-c++ projects.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Well, we know for sure it will be deprecated. Just not when. That sounds bad to me, so better try and do it with webext imho  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so maybe what we should do now then is write a definite roadmap/readme that will give others a better understanding of wth we are talking about.  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> I have to leave  
<strong>\<meeting-bot\> \[anonimal\]</strong> s/definite/definitive/  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: I think we can easily do that for now. Then, once we are more certain about our webext strategy, bring up this topic at another meeting?  
<strong>\<meeting-bot\> \[anonimal\]</strong> If roadmap is too much, at least improve our readme.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: That's probably a good idea.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Sure.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I agree that we should first see if we can actually do what we want to do, so for example: can we change all of the necessary settings  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, sounds great. Anything else on 4.?  
<strong>\<maoam\></strong> a short readme would be nice  
<strong>\<realsony\></strong> EinMbyte may i ask for your GIT repository name i couldn't find it  
<strong>\<meeting-bot\> \[EinMByte\]</strong> realsony: EinMByte/salti  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. [libqtoopie](https://github.com/EinMByte/qtoopie/issues/1)  
<strong>\<realsony\></strong> ty  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: did you get a chance to review \#1?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I read it  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Not sure if I can agree with converting it to a library  
<strong>\<meeting-bot\> \[EinMByte\]</strong> It should be the other way around, IMHO  
<strong>\<meeting-bot\> \[EinMByte\]</strong> qtoopie is based on I2PControl, with the idea of making it router-agnostic  
<strong>\<meeting-bot\> \[anonimal\]</strong> As it, you don't think it's possible or don't think it <em>should</em> be done or don't want it to be done?  
<strong>\<meeting-bot\> \[anonimal\]</strong> So what part would you rather see as the lib?  
<strong>\<meeting-bot\> \[anonimal\]</strong> If monero's gui needs it's own i2pcontrol then that's fine; I'm just trying to avoid repetition.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> It depends on what we want: if we want to build a router-agnostic GUI, I think I2PControl is the best option. In that case we could simply bundle qtoopie + kovri router and release this as an easy-to-use router package  
<strong>\<meeting-bot\> \[EinMByte\]</strong> If we want to build a GUI specifically for kovri, then we can rely on the (currently not existing) kovri API (libcore/libclient)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But in that case too, it would not really make sense for it to be a library. Instead, it would be comparable to what kovri-app currently is, except that it would be a GUI rather than CLI  
<strong>\<meeting-bot\> \[anonimal\]</strong> re: API, that's what the monero gui will be using, but where could we eliminate redundancy if the API and i2pcontrol would also do some of the more basic things that i2pcontrol provides?  
<strong>\<fluffypony\></strong> I2PControl would be able to control Kovri + Java i2p etc. right?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> My original idea for qtoopie is that it would fork for all exiting I2P routers that support I2PControl.  
<strong>\<fluffypony\></strong> oh I missed the "based on"  
<strong>\<fluffypony\></strong> ok makes sense  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So the redundancy is not eliminated at the level of the kovri implementation, but instead at all implementations (no need for a specific GUI)  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: Ok, that I understand. But there's really no way to create libqtoopie so the monero gui can use it <em>now</em> (even in it's current state)?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Why create extra monero gui code and i2pcontrol impl when that's already done?  
<strong>\<meeting-bot\> \[anonimal\]</strong> This doesn't change the functionality of qtoopie. I'm just basing this off what you said when I brought up the lib idea a while ago.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Sure, monero can use qtoopie directly  
<strong>\<meeting-bot\> \[anonimal\]</strong> If it's more work than not, and adversely effects qtoopie, then I understand.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> at least in the sense "you can display the windows defined in the qtoopie project"  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I guess that would classify as a library.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> The question is why you would want to bundle it like that  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (you could also just provide the executable with the monero executables, and then open this from the monero GUI, there would be little difference to the end use)  
<strong>\<meeting-bot\> \[anonimal\]</strong> To save redundant code so people don't have to install qtoopie to use qtoopie; and so it's integrated with the monero gui.  
<strong>\<fluffypony\></strong> can't we have our own controls in the GUI  
<strong>\<fluffypony\></strong> with bindings to libqtoopie functions ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: own controls to API, sure.  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: libqtoopie, EinMByte would know; I imagined yes.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> By the way, for reference on i2pcontrol: <http://zzz.i2p/topics/2030-proposal-bundle-i2pcontrol>, <http://zzz.i2p/topics/1942-i2pcontrol-for-generic-user-interfaces>  
<strong>\<meeting-bot\> \[EinMByte\]</strong> If you want to have your own controls, there's not much point in using all of qtoopie  
<strong>\<meeting-bot\> \[EinMByte\]</strong> then you just need to use i2pcontrol  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (which is very simple to implement; or you could use the part of qtoopie that deals with this)  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte I think you're missing the point but I'm probably not explaining my intentions well.  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, libqtoopie: not needed. qtoopie: agnostic but will not be in library form.  
<strong>\<meeting-bot\> \[anonimal\]</strong> We will create our own controls that use the API  
<strong>\<meeting-bot\> \[EinMByte\]</strong> qtoopie is an end-user program, hence why I'd say "not in library form"  
<strong>\<meeting-bot\> \[anonimal\]</strong> I know EinMByte, I'm just trying to save time and code.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> We could take some of the code in qtoopie and put it in a library "libi2pcontrol-client"  
<strong>\<meeting-bot\> \[EinMByte\]</strong> This library could then be used by e.g. monero  
<strong>\<meeting-bot\> \[anonimal\]</strong> i2pcontrol is insanely overrated, seriously overrated in relation to as much time as we're talking about it.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But this is assuming that monero would be using i2pcontrol at all  
<strong>\<meeting-bot\> \[anonimal\]</strong> I don't see the point if there are API's in place.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And i2pcontrol is limited in its own right.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, i2pcontrol has severe limitations  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, unless that entire spec is worked on, I have nothing more to say on the subject for now.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (even the proposed version 2)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so we'll learn from the mistakes of others and try not to make our own.  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: does that makes sense? anyone need a tl;dr?  
<strong>\<fluffypony\></strong> yes it does  
<strong>\<fluffypony\></strong> tl;dr for the log  
<strong>\<meeting-bot\> \[anonimal\]</strong> tl;dr qtoopie is great. We won't be using qtoopie in lib or bundled form because of severe limitations in i2pcontrol. We will be using GUI controls via the kovri API(s).  
<strong>\<meeting-bot\> \[EinMByte\]</strong> What is important to understand is that I2PControl is intended to create high-level control programs  
<strong>\<meeting-bot\> \[EinMByte\]</strong> It isn't designed to deal with lower-level configuration that monero might need  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 5.?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> One of the main limitations, in case anyone is wondering, is that i2pcontrol has to serialize everything and send it over the network  
<strong>\<meeting-bot\> \[EinMByte\]</strong> There's no possiblity of handlers or anything like that too  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (you have to continuously request updates)  
<strong>\<meeting-bot\> \[anonimal\]</strong> yes.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, 8 minutes  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. Preparing for pre-alpha release  
<strong>\<meeting-bot\> \[EinMByte\]</strong> For a simple GUI, that's probably good enough but it doesn't work when you want to integrate kovri with something like monero  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yay\! Nov. 1st pre-alpha will not happen, nooo way. I've been busy this month with non-code work; only recently with more code.  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte has been very busy too.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> :\|  
<strong>\<fluffypony\></strong> no problemo - let's get it right instead of getting it rushed :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: realistically, I think we should push the date to Dec. 1st or later.  
<strong>\<meeting-bot\> \[anonimal\]</strong> It's never going to perfect in my eyes, but...  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Sure  
<strong>\<meeting-bot\> \[EinMByte\]</strong> dont' expect more activity from me though  
<strong>\<meeting-bot\> \[anonimal\]</strong> You mean ever or temporary?  
<strong>\<meeting-bot\> \* anonimal</strong> hopes temporary  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I mean before december the first  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok. I'll set a tentative date for dec. 1st; no later than 33c3.  
<strong>\<meeting-bot\> \[anonimal\]</strong> (which is not dec. 1st of course)  
<strong>\<meeting-bot\> \[anonimal\]</strong> I'll have to adjust the milestone date on github and roadmap etc.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Any other thoughts on 6.?  
<strong>\<meeting-bot\> \[anonimal\]</strong> This coming month should be far more productive code-wise than in october.  
<strong>\<meeting-bot\> \[anonimal\]</strong> We'll see what we can knock-out before december.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2 minutes to spare  
<strong>\<meeting-bot\> \[anonimal\]</strong> Skipping 7. Code + ticket discussion / Q &amp; A unless anyone wants to say something?  
<strong>\<meeting-bot\> \[anonimal\]</strong> 8. Any additional meeting items  
<strong>\<fluffypony\></strong> nope that's it from my side  
<strong>\<fluffypony\></strong> glad to see the refactoring efforts  
<strong>\<fluffypony\></strong> will make stuff easier to work on later on  
<strong>\<meeting-bot\> \[iDunk\]</strong> head works now, thanks anonimal  
<strong>\<PowerFlower\></strong> oberservers can now ask questions?  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: yes indeedy  
<strong>\<meeting-bot\> \[anonimal\]</strong> iDunk: you're welcome, thanks for the notice and for actively testing :)  
<strong>\<meeting-bot\> \[iDunk\]</strong> np :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> PowerFlower: kovri questions, yes  
<strong>\<fluffypony\></strong> ok let's close up the Kovri meeting and then PowerFlower can ask their Monero question :-P  
<strong>\<meeting-bot\> \[anonimal\]</strong> Oh, those kinds of questions.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, 9. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anonimal\]</strong> Same time, two weeks?  
<strong>\<meeting-bot\> \[olark\]</strong> Sounds good.  
<strong>\<fluffypony\></strong> yes  
<strong>\<meeting-bot\> \[anonimal\]</strong> Alright, thank you EinMByte and everyone else here for making the meeting.  
<strong>\<fluffypony\></strong> meeting bot going down to switch back to the Monero stuf  
<strong>\<meeting-bot\> \[anonimal\]</strong> Thanks fluffypony
