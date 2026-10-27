---
title: Logs for the Kovri Dev Meeting Held on 2016-07-03
summary: Brief review of what has been completed since last meeting, SSU refactoring, closed and open issues
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<fluffypony\></strong> ok I guess we move on to Kovri - anonimal, the floor is yours  
<strong>\* fluffypony:</strong> ding dings  
<strong>\<meeting-bot\> \[anonimal\]</strong> Meeting Agenda: Sunday, July 3rd, 17:00 UTC  
<strong>\<meeting-bot\> \[anonimal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. Discuss SSU: status of \#140 and <https://github.com/EinMByte/kovri/pull/1> (if applicable), ideas, problems, and solutions (note: ask if @EinMByte will allow issues tracking within his repo)  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. Discuss commit message labeling, e.g., how to organize first line of commits. Touch-up on C4.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. Review open tickets (assigned and/or unassigned): status, code ideas (if applicable), etc.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. Discuss any pertinent TODO’s  
<strong>\<meeting-bot\> \[anonimal\]</strong> 7. Any additional meeting items  
<strong>\<meeting-bot\> \[anonimal\]</strong> 8. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anonimal\]</strong> — 1. Greetings  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi  
<strong>\<moneromooo\></strong> hi  
<strong>\<fluffypony\></strong> hi  
<strong>\<meeting-bot\> \[anonimal\]</strong> I know Ein is irc2p side waiting for me to move on :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’m on this side too  
<strong>\<meeting-bot\> \* anonimal</strong> wishes this was automated. /pulse only does so much  
<strong>\<meeting-bot\> \[anonimal\]</strong> 28 commits (not including merges), 2 new issues open, 0 issues closed  
<strong>\<meeting-bot\> \[anonimal\]</strong> All new commits in <https://github.com/einmbyte/kovri/tree/ssu>  
<strong>\<meeting-bot\> \[anonimal\]</strong> I ended up diving into SSU with EinMByte this week. Much fun.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Teamwork-teamwork: within the past hour, we had figured out that the HMAC digest impl was segfaulting because GetHeader-\>GetMAC() was not initialized, so the segfault is fixed for now.  
<strong>\<meeting-bot\> \[anonimal\]</strong> But that’s just a small portion of what’s been completed since previous meeting, and more issues abound. More to discuss in 3.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anyone else re: completed work since previous meeting?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’ve been focused on the OTF funding stuff, so I haven’t had a chance to finish the website work  
<strong>\<meeting-bot\> \[fluffypony\]</strong> pushing that out till the next meeting, unless we have to prepare more stuff for the OTF  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok. Any new issues re: OTF?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Seems like they’ve had a few lately.  
<strong>\<meeting-bot\> \[anonimal\]</strong> i.e., did we get confirmation that they received our request?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> no I think the next step is we’ll receive a pass / fail on the concept note  
<strong>\<meeting-bot\> \[fluffypony\]</strong> yes we did  
<strong>\<meeting-bot\> \[\_trump2016\]</strong> OTF will make kovri great again\!  
<strong>\<meeting-bot\> \[anonimal\]</strong> Confirmation, good.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anyone freenode-side? Is xmrpromotions there?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> so if we receive a pass we have to prepare an actual proposal  
<strong>\<meeting-bot\> \[fluffypony\]</strong> but let’s see when we get there  
<strong>\<meeting-bot\> \[fluffypony\]</strong> (if)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> they were on Reddit the other day, they seem to be busy at the moment  
<strong>\<meeting-bot\> \[fluffypony\]</strong> they’ve asked for assistance on the gnu-social thing  
<strong>\<meeting-bot\> \[anonimal\]</strong> Link? What kind of assistance? I’d be happy to help.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’ll have to find it and send it to you post-meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok. Anything else on 2.?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> oh found it, nevermind: <https://www.reddit.com/r/Monero/comments/4qywbx/what_are_moneros_pain_points_marketing_design/d4x34p3>  
<strong>\<meeting-bot\> \[fluffypony\]</strong> nein  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: Thanks, I’ll look into it later.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Moving on,  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. Discuss SSU: status of \#140 and <https://github.com/EinMByte/kovri/pull/1> (if applicable), ideas, problems, and solutions (note: ask if @EinMByte will allow issues tracking within his repo)  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, <https://github.com/EinMByte/kovri/pull/1> has been merged  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: will you allow issues tracking within your repo? It would help with this bug we’re hunting.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Oops, old paste, we fixed the bug,  
<strong>\<meeting-bot\> \[anonimal\]</strong> but are still dealing with related issues.  
<strong>\<meeting-bot\> \* anonimal</strong> knows Ein is somewhere, we were chatting elsewhere during the bitmonero meeting  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Hi  
<strong>\<meeting-bot\> \[anonimal\]</strong> Maybe he still thinks its the previous meeting…  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, I will allow all contributions to my repo  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Latest issue is: we are sending out broken packets  
<strong>\<meeting-bot\> \[fluffypony\]</strong> issue tracking has to be explicitly enabled for the repo, EinMByte  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (but at least the segfault is fixed)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> it’s a setting in github somewhere  
<strong>\<meeting-bot\> \[anonimal\]</strong> ^ what fluffypony said  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: are we in a committable stage for the segfault fix? So I can see where we stand?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Already committed  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony: somewhere where  
<strong>\<meeting-bot\> \[anonimal\]</strong> I imagine we’re sending bogus packets in SessionRequest  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’ll check  
<strong>\<meeting-bot\> \* anonimal</strong> fetching  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony: Never mind, I think I got it  
<strong>\<meeting-bot\> \[fluffypony\]</strong> if there’s time, anonimal, can you please explain what SSU is for those who are observing the meeting ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, latest commit makes sense.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yes,  
<strong>\<meeting-bot\> \[anonimal\]</strong> tl;dr, in plain english,  
<strong>\<meeting-bot\> \[anonimal\]</strong> it is one of two transport mechanisms closest to the IP layer:  
<strong>\<meeting-bot\> \[anonimal\]</strong> NTCP is for TCP, SSU is for UDP.  
<strong>\<meeting-bot\> \[anonimal\]</strong> SSU essentially takes care of encryption and negotiation with peers at the UDP level.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Does that make sense, or should I explain more?  
<strong>\<meeting-bot\> \* anonimal</strong> fetches link  
<strong>\<meeting-bot\> \[anonimal\]</strong> Specification here: <https://geti2p.net/spec/ssu>  
<strong>\<meeting-bot\> \[anonimal\]</strong> Overview here: <https://geti2p.net/en/docs/transport/ssu>  
<strong>\<meeting-bot\> \[EinMByte\]</strong> In case anyone is really listening: we are rewriting the SSU implementation because  
<strong>\<meeting-bot\> \[EinMByte\]</strong> 1) It doesn’t allow for unit tests  
<strong>\<<strong>uguu</strong>\></strong> i2p needs a better udp transport  
<strong>\<meeting-bot\> \[EinMByte\]</strong> 2) The design is bad, because separate concepts are not separated in code (packet parsing was done in the same functions as dealing with networking etc)  
<strong>\<meeting-bot\> \[anonimal\]</strong> X) it was an unmaintainable nightmare, like much of the codebase that we have yet to refactor.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> <strong>uguu</strong>: It probably does, so let’s hope SSU2 will be better  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (I’m not sure what the satus on SSU2 is, AFAIK there’s not even a spec yet)  
<strong>\<meeting-bot\> \[anonimal\]</strong> I had some ideas/problems/solutions when working on everything this week,  
<strong>\<meeting-bot\> \[anonimal\]</strong> but I need more time to flesh out tangible thought.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I think we’re on the right track, as we discussed earlier.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok, no problem. Maybe write everything down on github?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Sure, I’ll comment more in \#140 or open an issue in your repo.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Essentially, I want to take a closer look at design this week as I said I would stay away when we last spoke.  
<strong>\<meeting-bot\> \[anonimal\]</strong> e.g., what we discussed earlier about MAC buffer, etc.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, in terms of design many things are currently undecided  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I’ve mentioned before that this is more of a refactoring than a rewrite  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hmm… maybe I have a different vision of end-result then.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> At least for now, I do want design changes in the end  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But I wanted to make it less crappy first, and then make it good  
<strong>\<meeting-bot\> \[anonimal\]</strong> I think I need to get my hands dirty and get more intimate with your new changes.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I understand, as I said in \#1 I completely understand and agree.  
<strong>\<meeting-bot\> \* anonimal</strong> no complaints here  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, long story short, I’d like to get more involved. Any objections EinMByte?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Of course not, I can use all help  
<strong>\<meeting-bot\> \* anonimal</strong> could work in another branch, but I think our conflicts result in better code  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, I’ll comment more in \#140, etc. as things progress.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 3.?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Not from me  
<strong>\<meeting-bot\> \* anonimal</strong> prepares for more pasting  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anyone here have more SSU questions?  
<strong>\<meeting-bot\> \* anonimal</strong> will work on refining better responses to such questions  
<strong>\<meeting-bot\> \[fluffypony\]</strong> no that’s perfect, thanks  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, moving on  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. Discuss commit message labeling, e.g., how to organize first line of commits. Touch-up on C4.  
<strong>\<meeting-bot\> \[anonimal\]</strong> To preface, before discussing commit titles, none of this can really be enforced at the moment because there is no payout hanging over anyone’s head.  
<strong>\<meeting-bot\> \[anonimal\]</strong> But our guide does ask to reference applicable ticket numbers in commit bodies - and its incredibly helpful.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m trying to be better about doing this and I hope EinMByte would also consider doing this too.  
<strong>\<meeting-bot\> \[anonimal\]</strong> It should be noted that there is no mention in the guide or C4 about commit title.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ve been using a rough system of prepending titles with class or aspect of project worked on.  
<strong>\<meeting-bot\> \[anonimal\]</strong> It does help for quick git-log searches. Again, not enforceable, but it does help IMHO.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Thoughts? Objections to adding to guide?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> can you give me an example of the prepending?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yes, one moment.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: I’ve noticed that you tend to include a longer summary  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: Basically what’s before the colon <https://github.com/EinMByte/kovri/pull/1>  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I currently don’t do that, but if you think it’s worth it, I can start doing that  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Other than that, the main thing should be that it should be reasonably clear what the commit is about  
<strong>\<meeting-bot\> \[fluffypony\]</strong> oh yeah that’s cool  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But we all do that already  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I’m fine with stricter rules, just don’t shout at me too much when I forget about them :p  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I tend to do short summaries too, but I like the prepending thing  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: I agree. If I were to ask of anything, it would be to references issues that commit addresses.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Other than that, I personally couldn’t ask you to write longer summaries. Honestly, most of what you commit I understand anyway because its well-written IMHO - but that’s just me.  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, as usual, I think about everyone else who isn’t knee-deep in our mess.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And maybe longer summaries would help?  
<strong>\<meeting-bot\> \[anonimal\]</strong> But 4. for me was more about commit title.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok, I’ll try to reference issues more often  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I don’t think longer summaries are massively necessary as long as the commits show the route taken to get there, referencing issues is definitely helpful  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (not in the title, though)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok. So shall we take a vote on adding ‘prepend class or project aspect into title of commit’ into contributing guide?  
<strong>\<meeting-bot\> \[anonimal\]</strong> (again, at this time not enforceable - just helpful)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’m fine with it  
<strong>\<meeting-bot\> \[anonimal\]</strong> + me = 2 yes. Anyone else?  
<strong>\<meeting-bot\> \[anonimal\]</strong> As fluffypony pointed out long ago, its not like anyone reads contributing guides anyway ;)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> hah hah yeah  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Sure  
<strong>\<meeting-bot\> \[fluffypony\]</strong> but at least it’s there and we can encourage it  
<strong>\<meeting-bot\> \[EinMByte\]</strong> ^  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, good point on the encouragement.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> hey - we managed to get most Monero contributors to GPG sign commits, so it is doable :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Great, done.  
<strong>\<meeting-bot\> \[anonimal\]</strong> While we’re on 4., this is off-the-cuff,  
<strong>\<meeting-bot\> \[anonimal\]</strong> but bitmonero is working with only 1 branch now.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And, C4 kind of dictates that (IIRC).  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, do we scrap branch development and work solely in master?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> note that we have a use-case for moving back to the dev branch setup, because people just pull and compile  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ve also used arguments for two branches. I’m curious to hear EinMByte’s opinion.  
<strong>\<meeting-bot\> \* anonimal</strong> sigh, I2P lag  
<strong>\<meeting-bot\> \* anonimal</strong> doesn’t want to move on yet, running out of time though  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Not sure, I think it’s good to have a stable branch  
<strong>\<meeting-bot\> \[EinMByte\]</strong> also, it doesn’t hurt anyone? (I think)  
<strong>\<meeting-bot\> \[anonimal\]</strong> The argument is to instead warn users that anything that is built outside of a tagged version is… well, unpredictable.  
<strong>\<meeting-bot\> \[anonimal\]</strong> But, since we don’t have any releases yet…  
<strong>\<meeting-bot\> \[EinMByte\]</strong> There’s “unpredictable” and there’s “possibly broken”  
<strong>\<meeting-bot\> \[EinMByte\]</strong> In my opinion those are not really the same  
<strong>\<meeting-bot\> \[anonimal\]</strong> Good point. I imagine though that broken branches would stay in forks and then, when fleshed out, could be sent to 1 branch master.  
<strong>\<meeting-bot\> \[anonimal\]</strong> But then that would require more work maintainer-side.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ay, too many options.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I vote to keep two branches for now.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yea or Nay?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> ok, let’s keep the branches and move on :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, moving on.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. Review open tickets (assigned and/or unassigned): status, code ideas (if applicable), etc.  
<strong>\<meeting-bot\> \[anonimal\]</strong> My hands have been tied to SSU as we’ve discussed. I did hack a fix for the massive leak in \#191.  
<strong>\<meeting-bot\> \[anonimal\]</strong> It appears to be related to LogPrint and possibly GetFormattedSessionInfo(). I need more time with it and to produce a smoother fix.  
<strong>\<meeting-bot\> \[anonimal\]</strong> But it doesn’t address a few smaller leaks related to \#191.  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, between now and next meeting, I’m somewhat sure I’ll focus on SSU, \#191, and getting a windows build in working order.  
<strong>\<meeting-bot\> \[anonimal\]</strong> And in that order.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok  
<strong>\<meeting-bot\> \[anonimal\]</strong> <em>but</em> I also may start drafting a FFS proposal for a chunk of that time (I said I would last meeting). We’ll see.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> +1, FFS proposals are welcome  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: do you think you’ll be around sometime this coming week or the following week? Or are weekends better?  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: would you please refresh my memory on the zoho/fastmail decision (my brain is scattered at the moment)?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I’ll be around a few hours a day, but more actively in weekends  
<strong>\<meeting-bot\> \[fluffypony\]</strong> started the process a few days ago, we’re doing Zoho  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: sounds great.  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: sounds great.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Many great sounds\!  
<strong>\<meeting-bot\> \[fluffypony\]</strong> everyone can independently forward their mails to tutanota or i2pmail, or just use the Zoho mailbox  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m looking forward to zoho’s /projects, especially time-management.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Kimai is a horrid <em>\#()</em>@\#)$@\#$\#@  
<strong>\<meeting-bot\> \[anonimal\]</strong> If anyone has experience using it…  
<strong>\<meeting-bot\> \[fluffypony\]</strong> never heard of it, will take a look  
<strong>\<meeting-bot\> \[fluffypony\]</strong> or not if it’s horrible  
<strong>\<meeting-bot\> \* anonimal</strong> surprised at the lack of free, personal, opensource, time-management/billable hours solutions out there  
<strong>\<meeting-bot\> \[fluffypony\]</strong> MS Project  
<strong>\<meeting-bot\> \[anonimal\]</strong> IMHO you should, it may be humorous.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> :-P  
<strong>\<meeting-bot\> \[anonimal\]</strong> I can’t knock their work though, I applaud what they’re doing, I just wish I had more time to contribute to their project.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> is it meeting.end time?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Eek, one more thing.  
<strong>\<meeting-bot\> \* anonimal</strong> one more paste coming  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. Discuss any pertinent TODO’s  
<strong>\<meeting-bot\> \[anonimal\]</strong> In SSU: we’re closer to resolving \#119 with our new design. I’ve noted a few spots of missing implementation that I think will be resolved during the refactor.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I had mentioned in the most recent PR my interest in more sanity tests, and EinMByte did note a few overflow checks.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I think we’re still discussing design though, so that would come a little later.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Thoughts?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, we have many places where we need more checks  
<strong>\<meeting-bot\> \[EinMByte\]</strong> at least we won’t leak if we throw errors etc due smart pointer usage  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Eventually I want to rely on exception for error handling, and I want to use the error information for peer profiling  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ooooooooooooooo, I like that…  
<strong>\<meeting-bot\> \[anonimal\]</strong> I like that ALOT.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yes, smart pointers: something the previous project had very little interest in;  
<strong>\<meeting-bot\> \[anonimal\]</strong> despite the standard having been out for years.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anyway, I won’t start bashing as we’re out of time (I love a good bashing).  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 6.?  
<strong>\<meeting-bot\> \[anonimal\]</strong> If not, then 7.?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> nothing else from my side  
<strong>\<meeting-bot\> \[fluffypony\]</strong> next meeting same time, same place, two weeks?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Works for me.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Should be fine  
<strong>\<meeting-bot\> \[fluffypony\]</strong> sehr gut  
<strong>\<meeting-bot\> \[zzz\]</strong> will we see any kovri ppl at HOPE in 3 weeks?  
<strong>\<meeting-bot\> \[fluffypony\]</strong> zzz: unfortunately not me, need to do no travelling for a little bit  
<strong>\<meeting-bot\> \[fluffypony\]</strong> got too much work to do, lol  
<strong>\<meeting-bot\> \[EinMByte\]</strong> not me either  
<strong>\<meeting-bot\> \[anonimal\]</strong> I had planned late last year but things took a completely different turn so, nope, not this time around.  
<strong>\<meeting-bot\> \[zzz\]</strong> ok, I believe echelon still has a ticket to sell, if anybody needs it  
<strong>\<meeting-bot\> \[anonimal\]</strong> Thanks zzz. That echelon, quite the organizer :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else? Meeting?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I want to also thank fluffypony and dEBRUYNE and anyone else for their work on getting these logs up on the site.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> it’s mostly dEBRUYNE, I just add spaces in at the end  
<strong>\<meeting-bot\> \[anonimal\]</strong> lol, nice.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, thanks everyone for the great meeting.  
<strong>\<meeting-bot\> \[fluffypony\]</strong> thanks everyone  
<strong>\<meeting-bot\> \[fluffypony\]</strong> meeting-bot going offline
