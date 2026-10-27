---
title: Overview and Logs for the Dev Meeting Held on 2017-11-19
summary: Discussion of open PRs and issues, Bulletproofs, Monero Research Lab, Monero integrations, dedicated Monero hardware wallet, multisig, and miscellaneous
tags: [dev diaries, core, crypto]
author: dEBRUYNE / fluffypony
---

# Overview

An overview can be found on [MoneroBase](https://monerobase.com/wiki/DevMeeting_2017-11-19).

# Logs

<strong>\<rehrar\></strong> Hey everyone\! I don’t know if fluffypony will be here today, but let’s see about getting this thing started.  
<strong>\<rehrar\></strong> Hello to everyone idling in the peanut gallery  
<strong>\<msvb-lab\></strong> Hello.  
<strong>\<rehrar\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<rehrar\></strong> Can we get a mini-update from dev, gui, hardware, and mrl?  
<strong>\<sarang\></strong> I can speak for MRL  
<strong>\<sarang\></strong> We’ve been thoroughly investigated bulletproofs, a new form of CT range proofs  
<strong>\<hyc\></strong> is moneromooo here?  
<strong>\<moneromooo\></strong> Yes  
<strong>\<endogenic\></strong> have one thing to bring up  
<strong>\<endogenic\></strong> when there’s time  
<strong>\<sarang\></strong> They should function as essentially a drop-in replacement that is 10% the size of the original proofs (for one output; even smaller for multiple outputs)  
<strong>\<sarang\></strong> with about the same verification time; possibly a teensy bit faster  
<strong>\<sarang\></strong> Kudos to andytoshi for a lot of great help on those, and others  
<strong>\<hyc\></strong> it’s like a TARDIS\! the bigger the input the smaller the output\! /s  
<strong>\<rehrar\></strong> So it’s looking really promising that it’d be good for us?  
<strong>\<sarang\></strong> yes  
<strong>\<sarang\></strong> We’ll start translating the Java test code over to C/C++ for more detailed work  
<strong>\<suraeNoether\></strong> it’s a win-win: smaller-spaced range-proofs, with the same verification time  
<strong>\<sarang\></strong> There were some doubts about ver time, but we literally just had a convo over in MRL that pointed out a simple caching that helps us  
<strong>\<rehrar\></strong> MRL, folks. Let’s give ‘em a hand.  
<strong>\<sarang\></strong> It was pointed out, though, that there’s very little randomness hanging around, which could affect storing stuff “in the randomness”  
<strong>\<sarang\></strong> That may be a deepe discussion for later  
<strong>\<suraeNoether\></strong> yeah, using these range proofs makes encrypting messages with range proofs far less do-able  
<strong>\<sarang\></strong> \*deeper  
<strong>\<gingeropolous\></strong> eh who cares  
<strong>\<msvb-lab\></strong> MRL is excellent, nice.  
<strong>\<suraeNoether\></strong> andytoshi is really the one who nailed it, btw  
<strong>\<sarang\></strong> aye  
<strong>\<suraeNoether\></strong> aaaaand all his co-authors  
<strong>\<rehrar\></strong> Can we send them a fruit basket?  
<strong>\<endogenic\></strong> +1  
<strong>\<suraeNoether\></strong> which has included, for a second time, Jonathan Bootle  
<strong>\<sarang\></strong> rehrar set up an FFS for it  
<strong>\<sarang\></strong> 0.2 XMR  
<strong>\<suraeNoether\></strong> and for the N^th time, greg maxwell  
<strong>\<rehrar\></strong> 100 XMR requested  
<strong>\<rehrar\></strong> biggest fruit basket ever  
<strong>\<sarang\></strong> Anyhoo, that’s the big news from MRL right now, I suppose  
<strong>\<rehrar\></strong> awesome. Thanks so much.  
<strong>\<suraeNoether\></strong> multisig is looking like i will be ready to hand it off to sarang by the end of the month, as hoped.  
<strong>\<suraeNoether\></strong> and thats it for now  
<strong>\<rehrar\></strong> Anyone else have an update since the last meeting two weeks ago?  
<strong>\<ArticMine\></strong> This is huge from a scaling perspective  
<strong>\<hyc\></strong> absolutely  
<strong>\<hyc\></strong> dev has done a tone of PR merges latelt  
<strong>\<hyc\></strong> lately  
<strong>\<rehrar\></strong> can you summarize them?  
<strong>\<hyc\></strong> there’s still been build issues with readline dependencies but I think they’re pretty much sorted by now  
<strong>\<hyc\></strong> we’ve isolated readline from GUI dependencies, etc.  
<strong>\<hyc\></strong> mooo can probably summarize better  
<strong>\<endogenic\></strong> vtnerd says “oh good”  
<strong>\<endogenic\></strong> “woo”  
<strong>\<moneromooo\></strong> Hmm. I can go look at github:  
<strong>\<moneromooo\></strong> (mostly small things anyway)  
<strong>\<rehrar\></strong> FP confirmed he can’t make it today. He sends his apologies.  
<strong>\<moneromooo\></strong> disguising password length in prompt I guess is still a small thing, but user visible  
<strong>\<moneromooo\></strong> less unnecessary locking in some DB readers, which should speed up some RPC  
<strong>\<moneromooo\></strong> Fixes for BSD build  
<strong>\<moneromooo\></strong> The wallet does not fetch unneeded hashes anymore (ie, starts direct from 1.4e6)  
<strong>\<moneromooo\></strong> CORS (for those who know what it is)  
<strong>\<moneromooo\></strong> A fix for show\_transfers missing more than one incoming input in a tx  
<strong>\<moneromooo\></strong> And I think the rest is either prior to last meeting, or small/internal stuff.  
<strong>\<hyc\></strong> yeah but it comprises a couple dozen PRs between then and now  
<strong>\<rehrar\></strong> Alright, awesome. Thanks moneromooo.  
<strong>\<rehrar\></strong> hardware, I know you give updates in community, but I think most of us that know are excited about the rapid progress you’re making  
<strong>\<rehrar\></strong> care to share something small about what’s been going down?  
<strong>\<msvb-lab\></strong> Hardware; we’ve settled our initial workflows and have built a twenty strong team. Journals are taking notice (see press) and the project is moving along.  
<strong>\<msvb-lab\></strong> <https://taiga.getmonero.org/project/michael-rfc-hwallet-1-implementation/wiki/press/>  
<strong>\<msvb-lab\></strong> I’ll mark our forum proposal milestone 1 as concluded today probably.  
<strong>\<msvb-lab\></strong> We now have an open call to any interested in a hardware wallet, become part of the project and possibly test a prototype. See:  
<strong>\<msvb-lab\></strong> <https://taiga.getmonero.org/project/michael-rfc-hwallet-1-implementation/wiki/preview/>  
<strong>\<msvb-lab\></strong> I’ll demonstrate our two current working protoypes at this week’s first ever Monero Munich meeting.  
<strong>\<msvb-lab\></strong> That’s all, any questions?  
<strong>\<sgp\></strong> What do you expect those who receive the prototypes to test?  
<strong>\<msvb-lab\></strong> Very weak expectations, hopefully each finds their own way to contribute and strengthen the project.  
<strong>\<msvb-lab\></strong> There’s a test plan page, where people can make comments while testing.  
<strong>\<msvb-lab\></strong> But that is just one of many choices, each individual can make on their own.  
<strong>\<msvb-lab\></strong> Pretty lame answer no?  
<strong>\<rehrar\></strong> Alright, thanks msvb-lab\!  
<strong>\<msvb-lab\></strong> Thanks for the opportunity.  
<strong>\<moneromooo\></strong> Sounds like pretty nice stuff is going on there, congrats :)  
<strong>\<hyc\></strong> (I counted 72 PRs merged since last dev meeting)  
<strong>\<msvb-lab\></strong> hyc: Who make most of the merges, fluffy?  
<strong>\<rehrar\></strong> So, we’ve got Code + ticket discussion / Q &amp; A time available for the devs to discuss dev-y things. But all the mergy stuff may have to wait because of FP absence, but if there’s other business to take care of, devs you have the floor  
<strong>\<hyc\></strong> yes he does all the merges  
<strong>\<hyc\></strong> we didn’t get a report from GUI  
<strong>\<rehrar\></strong> oh, right\! so sorry.  
<strong>\<rehrar\></strong> Anybody working on GUI have stuff to talk about.  
<strong>\<unknownids\></strong> ping Jaquee ?  
<strong>\<endogenic\></strong> so i’ve been chatting with mooo, Jaquee, and vtnerd recently about integrating MyMonero with the native mainline libwallet  
<strong>\<Jaquee\></strong> sorry. i’m on the run  
<strong>\<endogenic\></strong> signs point to integrating with wallet\_api  
<strong>\<endogenic\></strong> I may end up tackling a small portion of factoring wallet2  
<strong>\<rehrar\></strong> ok, no worries Jaquee.  
<strong>\<moneromooo\></strong> As long as not too many gratuitous changes ^\_^  
<strong>\<endogenic\></strong> 100% mooo  
<strong>\<hyc\></strong> all variable and class names being filtered thru pig-latin  
<strong>\<gingeropolous\></strong> dsc, in here :)  
<strong>\<dsc\></strong> :)  
<strong>\<msvb-lab\></strong> Is our GUI crew considered only monero-gui, or are mymonero.com and Moneruj (Android) included as well?  
<strong>\<dsc\></strong> has it started?  
<strong>\<endogenic\></strong> lol hyc  
<strong>\<rehrar\></strong> I think GUI crew is people who work on the monero-gui repo  
<strong>\<rehrar\></strong> mymonero and Monerujo are their own thing  
<strong>\<rehrar\></strong> dsc has what started?  
<strong>\<dsc\></strong> the meeting :D  
<strong>\<rehrar\></strong> oh, yeah. We’re about half hour in. :)  
<strong>\<hyc\></strong> oh - that’s worth mentioning too - the repo is now properly named monero-gui, no longer monero-core  
<strong>\<msvb-lab\></strong> rehrar: So Monerujo communicate on a different channel, right?  
<strong>\<rbrunner\></strong> That rename is a milestone :)  
<strong>\<rehrar\></strong> Monerujo utilizes the Mattermost where they have a private channel for the devs and core team, and a public channel for questions. They’ve also got a Taiga to track progress.  
<strong>\<dsc\></strong> aight, so I’m working on a black theme for `monero-gui` (qt5) .. learning QML in the process. Trying to get some more UX developers involved and generally just trying to document things as I go  
<strong>\<rehrar\></strong> I can rep Monerujo though, as I’m heavily involved with them  
<strong>\<rehrar\></strong> they’ve got some exciting stuff coming  
<strong>\<rehrar\></strong> yes, can you link your thread dsc?  
<strong>\<dsc\></strong> sure  
<strong>\<rehrar\></strong> The one you made a few days ago.  
<strong>\<dsc\></strong> <https://www.reddit.com/r/Monero/comments/7dvwq0/contributing_to_monero_as_an_ux_developer_short/>  
<strong>\<rehrar\></strong> in the comments there are the various proposals for redesigning the GUI. Are there any thoughts on any of those?  
<strong>\<rehrar\></strong> well, first dsc you wanted to say something, go ahead. :)  
<strong>\<dsc\></strong> No I was finished :P  
<strong>\<dsc\></strong> but to answer your question: There are 3 UI proposals of which I picked the one that was most trivial to implement  
<strong>\<dsc\></strong> seeing as I’m just one guy with zero QML experience, hehe.  
<strong>\<dEBRUYNE\></strong> rehrar: Basically we’re first kind of going for the dark theme, which will have a light mode as well  
<strong>\<dEBRUYNE\></strong> Because it’s most trivial to implement  
<strong>\<dEBRUYNE\></strong> (only requires minor changes to the current design)  
<strong>\<rehrar\></strong> <https://github.com/monero-project/monero-core/issues/419>  
<strong>\<rehrar\></strong> <https://github.com/monero-project/monero-core/issues/869>  
<strong>\<rehrar\></strong> <https://github.com/monero-project/monero-core/issues/949>  
<strong>\<dEBRUYNE\></strong> Some screenshots -\> <https://i.imgur.com/89YFUj7.png>  
<strong>\<rehrar\></strong> for those interested  
<strong>\<rehrar\></strong> Ok. Cool deal\!  
<strong>\<dEBRUYNE\></strong> To clarify, the dark theme is \#949  
<strong>\<hyc\></strong> cool  
<strong>\<dEBRUYNE\></strong> dsc also made a PR which should make the GUI more responsive  
<strong>\<dsc\></strong> cant make any predictions as to when I have some tangible, taking quite some time…\!  
<strong>\<dsc\></strong> s/some/something/  
<strong>\<dEBRUYNE\></strong> Also, we’re aiming to include subaddresses and multisig somewhere in the future^tm  
<strong>\<dEBRUYNE\></strong> And, once there is a core appstore account, we’ll start testing the ios port of the GUI  
<strong>\<dEBRUYNE\></strong> There’ll be an android port as well, fwiw  
<strong>\<msvb-lab\></strong> dEBRUYNE: Is Qt5 easy to port to mobile?  
<strong>\<sgp\></strong> Is there a new android APK to test? I last saw one months ago  
<strong>\<dEBRUYNE\></strong> sgp: Buildbot produces APKs iirc  
<strong>\<dEBRUYNE\></strong> Let me check  
<strong>\<pigeons\></strong> No that isn’t setup now  
<strong>\<dEBRUYNE\></strong> msvb-lab: Jaquee did it, so better to ask him :P  
<strong>\<pigeons\></strong> I can’t promise next week even, very busy  
<strong>\<dsc\></strong> rehrar: To give you an idea, right now I have this: <https://i.imgur.com/iLwupdB.png>  
<strong>\<dsc\></strong> or to give anyone an idea for that matter :)  
<strong>\<serhack\></strong> Hello  
<strong>\<rehrar\></strong> looks pretty chill imo :D  
<strong>\<dsc\></strong> aye aye  
<strong>\<dsc\></strong> WIP ofc :)  
<strong>\<rehrar\></strong> I personally think there needs to be a bit of a restructuring of some info, but this is a good meantime  
<strong>\<dsc\></strong> agreed  
<strong>\<hyc\></strong> good stuff  
<strong>\<hyc\></strong> would be nice to get a more recent android build up for people to test  
<strong>\<rehrar\></strong> Alright. That’s it from GUI? No other opinions on dEBRUYNE and dsc stuff either?  
<strong>\<hyc\></strong> looks like we can move on to ticket Q/A  
<strong>\<rehrar\></strong> ok Code + ticket discussion / Q &amp; A  
<strong>\<rehrar\></strong> hyc moneromooo can you two take the lead for this?  
<strong>\<moneromooo\></strong> Well, if anyone has questions about them, please ask.  
<strong>\<hyc\></strong> I’d leave it to mooo. I’m not aware of any open questions  
<strong>\<hyc\></strong> ^^  
<strong>\<dsc\></strong> ticket Q/A \!= discussing open PR’s, right?  
<strong>\<hyc\></strong> sure  
<strong>\<hyc\></strong> ask away  
<strong>\<dsc\></strong> low hanging fruit PRs (that can probably be merged): \#919, \#954, \#963 on monero-gui  
<strong>\<dsc\></strong> not so much a question ^\_^  
<strong>\<hyc\></strong> probably ask luigi to merge them if fluffy is unavailable  
<strong>\<iDunk\></strong> luigi merges GUI PRs anyway :)  
<strong>\<dsc\></strong> alright  
<strong>\<rehrar\></strong> I think luigi is out for a few days, so be patient. (:  
<strong>\<rehrar\></strong> Alrighty, shall we move on?  
<strong>\<rehrar\></strong> FFS Formalization: <https://github.com/monero-project/meta/pull/87>  
<strong>\<serhack\></strong> Is there meeting?  
<strong>\<hyc\></strong> serhack started 40 minutes ago  
<strong>\<rehrar\></strong> we probably don’t have time for a large discussion (if at all), but I just wanted to encourage the devs to take a look at the PR  
<strong>\<serhack\></strong> Oh  
<strong>\<serhack\></strong> I forgot it  
<strong>\<rehrar\></strong> The idea of having a set of formalized guidelines for FFS proposals going forward has been thrown around a lot. It’d be good to get some opinions on how this is laid out and any concerns that may arise from it.  
<strong>\<serhack\></strong> I didn’t understand well: is the project funded by ffs an Official project?  
<strong>\<ArticMine\></strong> Does the current system work?  
<strong>\<rehrar\></strong> There’s been hiccups ArticMine. fireice and guzzi come to mind.  
<strong>\<endogenic\></strong> those seem like complete outliers :P  
<strong>\<endogenic\></strong> not exactly legit claims to issues imo  
<strong>\<rehrar\></strong> Largely based on de facto expectations that are not actually formalized.  
<strong>\<msvb-lab\></strong> How do we learn about the hickups mentioned (in order to understand context?)  
<strong>\<endogenic\></strong> but proposals could stand to be more concrete, specific, detailed,  
<strong>\<endogenic\></strong> rehrar: formalization can be a bit of a rabbit hole as well  
<strong>\<endogenic\></strong> sometimes humans need to be involved  
<strong>\<endogenic\></strong> ppl need to recognize the situation before a formal plan can be applied  
<strong>\<hyc\></strong> indeed. current US political situation reflects this - institutions are designed assuming good faith in all participants  
<strong>\<endogenic\></strong> but if the situation is not able to be recognized by ppl then how can it be applied for the desired result?  
<strong>\<hyc\></strong> nobody can take all the time needed to identify every possible abusable loophole  
<strong>\<rehrar\></strong> What we have currently is a Core Team centered way of resolving disputes that, to my knowledge, hasn’t really been utilized since I’ve been here  
<strong>\<rehrar\></strong> since we’ve got that right now, maybe we stick with it?  
<strong>\<endogenic\></strong> but identifying loopholes and plugging them is not a bad thing  
<strong>\<endogenic\></strong> it’s just that they need to be done by humans imo  
<strong>\<ArticMine\></strong> We may need some tweaking to deal with the hiccups; but as afar as I can see at a fundamental level the system is working  
<strong>\<rehrar\></strong> don’t know where else the graphic is, so I’ll just link it here: <https://getkovri.org/contributing.html>  
<strong>\<rehrar\></strong> bottom of the page  
<strong>\<rehrar\></strong> This has not been formally replaced, so it is currently active. We can discuss that at a later time though. Let’s move on.  
<strong>\<rehrar\></strong> 5. Any additional meeting items  
<strong>\<rehrar\></strong> If anyone has anything, speak up. :)  
<strong>\<moneromooo\></strong> If anyone wants to test multisig, feel free. PR 2134.  
<strong>\<gingeropolous\></strong> is there a set date for the next code freeze?  
<strong>\<serhack\></strong> A little update by me about Monero Integrations  
<strong>\<rehrar\></strong> go for it serhack  
<strong>\<serhack\></strong> So we (I and cryptochangements) are going to release Magento Plugin, In the past few weeks, we worked on a new cool payment box for Monero Integrations.  
<strong>\<serhack\></strong>  
<strong>\<serhack\></strong> I am currently working on OpenCart too so I think we can release Magento payment box the next week..  
<strong>\<serhack\></strong>  
<strong>\<serhack\></strong> I have talked to OpenBazaar too and they have told me that Monero + Openbazaar would be nice.. it will be a difficult task but I think I can do it  
<strong>\<serhack\></strong> you can go on, rehrar  
<strong>\<moneromooo\></strong> Everytime I read OpenBazaar, it makes me want to punch that scammer from a few years back…  
<strong>\<rehrar\></strong> alright, thanks man :)  
<strong>\<rehrar\></strong> atrides?  
<strong>\<moneromooo\></strong> That’s the one.  
<strong>\<rehrar\></strong> doesn’t he still run Dwarfpool?  
<strong>\<gingeropolous\></strong> yeah, and ppl still mine on it  
<strong>\<rehrar\></strong> We should encourage them not to  
<strong>\<rehrar\></strong> Either way: 6. Confirm next meeting date/time  
<strong>\<rehrar\></strong> December 3rd? Same time?  
<strong>\<gingeropolous\></strong> so no freeze date, eh?  
<strong>\<rehrar\></strong> Should we move time because daylight savings?  
<strong>\<moneromooo\></strong> About mid december  
<strong>\<gingeropolous\></strong> word.  
<strong>\<ArticMine\></strong> Please do not move the time  
<strong>\<moneromooo\></strong> Or january. Unclear.  
<strong>\<rehrar\></strong> ok, time not moved  
<strong>\<rehrar\></strong> FP would have a better answer?  
<strong>\<hyc\></strong> isn’t a release due in January?  
<strong>\<hyc\></strong> and we’re supposed to freeze a month before  
<strong>\<iDunk\></strong> March  
<strong>\<gingeropolous\></strong> well dec or jan gives us 3 months  
<strong>\<hyc\></strong> ok  
<strong>\<rehrar\></strong> There’s a new freeze/release schedule isn’t there?  
<strong>\<hyc\></strong> mebbe someone can open a meta issue and set some dates into it  
<strong>\<gingeropolous\></strong> i thought we had 3 months of freeze for more testing / fixing than before …  
<strong>\<moneromooo\></strong> 3 months of freeze is gonna make me punch someone else :P  
<strong>\<moneromooo\></strong> It’s branch, then release from the brnch aftrer 2-3 months.  
<strong>\<moneromooo\></strong> It’s already painful when stuff doens’t get merged after a month.  
<strong>\<ArticMine\></strong> The big one is the bullet proofs  
<strong>\<gingeropolous\></strong> right. i thought branch is a freeze… i.e., feature freeze… i.e., freeze on adding wacky new stuff that requires bandaloots and warples  
<strong>\<moneromooo\></strong> That’s not likely to be ready by then.  
<strong>\<gingeropolous\></strong> but yeah… perhaps that should be documented somewhere  
<strong>\<rehrar\></strong> (Not to interrupt, but meeting is over for those who need to go, discussion can of course continue)  
<strong>\<rehrar\></strong> Alright. You guys are the best\! thanks for being a part of this community, and developing the software we all know and love as Morono  
<strong>\<msvb-lab\></strong> rehrar: Thanks, good flow of topics, great moderation.
