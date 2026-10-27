---
title: Overview and Logs for the Kovri Dev Meeting Held on 2018-06-07
summary: Discussion of the latest Kovri development updates and the alpha release
tags: [dev diaries, i2p, crypto]
author: selsta / anonimal
---

# Logs

<strong>\<anonimal\></strong> 1. Greetings  
<strong>\<anonimal\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<anonimal\></strong> 3. Contributor FFS check-in / status  
<strong>\<anonimal\></strong> 4. Alpha release discussion  
<strong>\<anonimal\></strong> 5. Public relations discussion  
<strong>\<anonimal\></strong> 6. Code + ticket discussion / Q &amp; A  
<strong>\<anonimal\></strong> 7. Any additional meeting items  
<strong>\<anonimal\></strong> 8. Confirm next meeting date/time  
<strong>\<anonimal\></strong> Hi  
<strong>\<oneiric\_\></strong> Hi  
<strong>\<rehrar\></strong> Heyo  
<strong>\<rehrar\></strong> \#kovrifam  
<strong>\<rehrar\></strong> stolen from Verge  
<strong>\<anonimal\></strong> I don’t think fluffypony has been to a kovri meeting since at least 2016.  
<strong>\<\_Slack\> \<sean\></strong> Hey  
<strong>\<anonimal\></strong> He name-drops kovri/kovri-related in interviews all the time and shows up to monero meetings.  
<strong>\<anonimal\></strong> Hi sean  
<strong>\<rehrar\></strong> like the Queen of England  
<strong>\<rehrar\></strong> shall I ping him?  
<strong>\<\_Slack\> \<sean\></strong> Hey anonimal.  
<strong>\<anonimal\></strong> rehrar: you already did, during the prep  
<strong>\<rehrar\></strong> he’s not in the room, and I guess he doesn’t have any other IRC bridges  
<strong>\<anonimal\></strong> Anyone else here? Big channel, lots of lurkers  
<strong>\<anonimal\></strong> NSA bots, how’s it going?  
<strong>\<oneiric\_\></strong> lol +badbot  
<strong>\<anonimal\></strong> Hi iDunk  
<strong>\<iDunk\></strong> o/  
<strong>\<rottensalty07\></strong> I’m here, but I’m not a three-lettered botnet.  
<strong>\<anonimal\></strong> Damn  
<strong>\<anonimal\></strong> They could at least speak up more  
<strong>\<anonimal\></strong> We know you’re there  
<strong>\<anonimal\></strong> Some poor sap sitting behind a monitor sifting through regexps  
<strong>\<anonimal\></strong> Oh well  
<strong>\<anonimal\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<anonimal\></strong> If you look at the old logs, I used to prepare very detailed records for item 2.  
<strong>\<rottensalty07\></strong> Lol.  
<strong>\<anonimal\></strong> I then realized that A) most people didn’t care B) the people who did care already knew what I was going to say.  
<strong>\<anonimal\></strong> So, I stopped preparing for item 2 :)  
<strong>\<anonimal\></strong> Here’s a recent item I can easily grab:  
<strong>\<anonimal\></strong> <https://twitter.com/getkovri/status/1004568146139865089>  
<strong>\<anonimal\></strong> Which links to <https://t.co/7fDhUBt75d>  
<strong>\<anonimal\></strong> Oops  
<strong>\<anonimal\></strong> <http://forum.getmonero.org/6/ideas/90300/oneiric-june-august-part-time-kovri-junior-developer>  
<strong>\<rottensalty07\></strong> Those t.co shady links. Shame.  
<strong>\<anonimal\></strong> The tco link points to the forum link  
<strong>\<rottensalty07\></strong> I’m reading through.  
<strong>\<anonimal\></strong> So that needs more input and should be moved to funding.  
<strong>\<anonimal\></strong> Alex058 responded with thumbs up  
<strong>\<anonimal\></strong> I’ll go ahead and retweet the getkovri tweet  
<strong>\<oneiric\_\></strong> Much appreciation anonimal and Alex058 :)  
<strong>\<rottensalty07\></strong> Retweeted by wheel too.  
<strong>\<anonimal\></strong> No problem  
<strong>\<rehrar\></strong> I support oneiric\_, but I’m biased since he is bae  
<strong>\<rottensalty07\></strong> oneiric\_: I’m happy to see others coming out to help rehrar and anonimal labor. We are nothing but a community.  
<strong>\<rottensalty07\></strong> rehrar: No homo.  
<strong>\<rehrar\></strong> all the homo  
<strong>\<oneiric\_\></strong> lol rehrar  
<strong>\<anonimal\></strong> oneiric\_ is British Aerospace?  
<strong>\<oneiric\_\></strong> ?  
<strong>\<anonimal\></strong> “bae” ;)  
<strong>\<oneiric\_\></strong> lol  
<strong>\<anonimal\></strong> Anyway, aside from that, lots has happened between now and the previous meeting. Lots of development.  
<strong>\<anonimal\></strong> Anything else on point 2.?  
<strong>\<rehrar\></strong> not sure if I should report here  
<strong>\<rehrar\></strong> or in 3.  
<strong>\<rehrar\></strong> they kinda bleed together  
<strong>\<anonimal\></strong> 3. Contributor FFS check-in / status  
<strong>\<anonimal\></strong> Go  
<strong>\<rehrar\></strong> I been working  
<strong>\<rehrar\></strong> end  
<strong>\<rehrar\></strong> no but really  
<strong>\<rehrar\></strong> so my last payout was delayed because kovri died down for about a month or two. So rather than try to just do busywork that wouldn’t help anyone, I decided to delay my work and payment until we got the band back together so we can make sure we’re all working toward a common goal  
<strong>\<anonimal\></strong> A month or two?\! Umm, no.  
<strong>\<rehrar\></strong> but I was doing some build work with oneiric, particularly documenting  
<strong>\<anonimal\></strong> When was this?  
<strong>\<rehrar\></strong> \*a month  
<strong>\<anonimal\></strong> Two weeks is a month now?  
<strong>\<rehrar\></strong> intermittent people in \#kovri from mid April to near end of May?  
<strong>\<anonimal\></strong> What does \#kovri have to do with your FFS?  
<strong>\<rehrar\></strong> ummm…I’m just explaining why I felt it would be better to hold up on the work :/  
<strong>\<anonimal\></strong> If I can’t make it for \~2 weeks, that’s when other people are needed most; not the other way around.  
<strong>\<anonimal\></strong> Well, whatever your rationale, I don’t think anyone else cares if you weren’t working on your FFS so, you probably won’t hear any other complaints.  
<strong>\<rehrar\></strong> I have been working on my FFS. In fact it should be done today or tomorrow.  
<strong>\<anonimal\></strong> Sucks for me though because I get the brunt of it.  
<strong>\<anonimal\></strong> You just said you delayed your work, and now you’re telling me you’ve been working…  
<strong>\<anonimal\></strong> Which one is it?  
<strong>\<rehrar\></strong> …  
<strong>\<rehrar\></strong> it hasn’t been delayed the entire time anonimal  
<strong>\<rottensalty07\_\></strong> anonimal: I believe you got twisted there…  
<strong>\<rottensalty07\_\></strong> He didn’t work on the main thing for few days, but was working documenting under the table…  
<strong>\<rehrar\></strong> I was working on it for a couple weeks, then took a break while things died down, and then resumed recently when things picked back up  
<strong>\<anonimal\></strong> If your last payout was 2 months ago, and you said you delayed your work for 2 months, that equals 0 work if I understand correctly that 2 - 2 = 0  
<strong>\<anonimal\></strong> Ok  
<strong>\<rehrar\></strong> yes, but as you corrected, it wasn’t two months, and my “month or two” comment wasn’t correct as you said  
<strong>\<anonimal\></strong> I can’t account for under the table work.  
<strong>\<rehrar\></strong> excuse me for speaking flippantly  
<strong>\<rehrar\></strong> I can PR the documentation work that I’ve done, but you had said that you weren’t liking the whole “DO NOT MERGE” culture that had happened last time I did a PR to prove work  
<strong>\<anonimal\></strong> So what’s been done.  
<strong>\<rehrar\></strong> this is what I have been trying to explain :P  
<strong>\<anonimal\></strong> DO NOT MERGE equals not complete so why be paid for something that hasn’t been completed.  
<strong>\<anonimal\></strong> WIP is one thing, but you’re off the hook after this FFS.  
<strong>\<anonimal\></strong> So, is it done?  
<strong>\<anonimal\></strong> You set the deadlines of Q1, not me. I just want to see where we are.  
<strong>\<rehrar\></strong> Documenation with oneiric\_, which is in progress, sent a PR with the recent multilingual changes that were on the getmonero.og site, lots and lots of logo work, fielding a few dev people that contacted out of interest, serhack collab for Mastering Monero, kovri defcon work  
<strong>\<rehrar\></strong> documentation is not done, but fairly far along. oneiric\_ can attest that we spent quite some time working through various OS’s, as not all the instrutions worked 100% and there was a large amount of trouble shooting  
<strong>\<rehrar\></strong> \*instructions  
<strong>\<oneiric\_\></strong> That’s true, we worked on Debian builds, and a couple of the build options.  
<strong>\<anonimal\></strong> Ok  
<strong>\<rehrar\></strong> the OS specific documentation also requires a custom HTML/CSS scheme for the Get Started page, which I have experimented with and not found a solution for  
<strong>\<anonimal\></strong> I don’t think all of this is needed though.  
<strong>\<oneiric\_\></strong> I was a bit unsure of a couple flags, and why the build was failing without them.  
<strong>\<anonimal\></strong> We have a table in the readme  
<strong>\<anonimal\></strong> What’s the goal?  
<strong>\<rehrar\></strong> one of the things we discussed was the rewrite the kovri docs  
<strong>\<rehrar\></strong> and to do it in a more user friendly wa  
<strong>\<rehrar\></strong> \*way  
<strong>\<rehrar\></strong> I do indeed have a table as well, sitting in my branch of kovri docs  
<strong>\<rehrar\></strong> I can PR it right this second for proof  
<strong>\<anonimal\></strong> I ended up having to do the docs myself. <https://github.com/monero-project/kovri-docs/pull/48>  
<strong>\<anonimal\></strong> It’s June. This kind of stuff needed to be done Q1.  
<strong>\<anonimal\></strong> The user-guide could use improving though.  
<strong>\<anonimal\></strong> Anyway, whatever. What’s done is done.  
<strong>\<rehrar\></strong> the new multilingual scheme also requires different stuff for the way the site is handled  
<strong>\<rehrar\></strong> PR sent  
<strong>\<anonimal\></strong> Ok  
<strong>\<rehrar\></strong> the Kovri site is quite different from the Monero site, in that it relies on the pulled docs, which has pros and cons. Simplifies some things and complicates others.  
<strong>\<anonimal\></strong> Yes, but this doesn’t change that I’m having to do things myself; things you said you would do.  
<strong>\<anonimal\></strong> Also, what have you done with r/kovri?  
<strong>\<anonimal\></strong> AFAICT nothing for this FFS.  
<strong>\<anonimal\></strong> In fact, someone else had to come and moderate because of spam.  
<strong>\<anonimal\></strong> Have you done any r/kovri work that I’m unaware of?  
<strong>\<rehrar\></strong> no  
<strong>\<anonimal\></strong> “/r/Kovri design moderation and upkeep” \<— <https://forum.getmonero.org/9/work-in-progress/89677/rehrar-s-2018-q1-kovri-proposal>  
<strong>\<anonimal\></strong> Ok  
<strong>\<anonimal\></strong> Anything else for point 3. Contributor FFS check-in / status ?  
<strong>\<oneiric\_\></strong> We already talked about mine, nothing else from me  
<strong>\<anonimal\></strong> 4. Alpha release discussion  
<strong>\<anonimal\></strong> The date is by defcon.  
<strong>\<anonimal\></strong> I have no clue where pigeons is.  
<strong>\<anonimal\></strong> I can’t develop on BSD nor windows. These meta issue tickets are piling up.  
<strong>\<anonimal\></strong> The alpha will be a sum result of what the community can handle.  
<strong>\<anonimal\></strong> s/I can’t develop on BSD nor windows/I can’t develop on BSD nor windows because of <https://github.com/monero-project/meta/issues/178> and <https://github.com/monero-project/meta/issues/238>  
<strong>\<rehrar\></strong> I’ll ping pigeons right now  
<strong>\<anonimal\></strong> These shouldn’t be issues. This is why we need to move on <https://github.com/monero-project/meta/issues/237>  
<strong>\<anonimal\></strong> I’m already donating my time. If I wasn’t donating that, then I’d be donating my money.  
<strong>\<rehrar\></strong> hmmm…ok. Do you think it’s worthwhile to have us kovri people set up some stuff and maintain them?  
<strong>\<anonimal\></strong> That’s the point of \#237, or at least one of the points.  
<strong>\<anonimal\></strong> We’re running out of time, anything else on 4. Alpha release discussion?  
<strong>\<rehrar\></strong> right, but we can get an action item on that in that we can have someone do it specifically for Kovri. Other workgroups can follow suit as they want.  
<strong>\<anonimal\></strong> Moving the issue from Monero Project Meta to Monero Project Taiga defeats the purpose of decentralization.  
<strong>\<anonimal\></strong> But no one is stopping you from doing that.  
<strong>\<rehrar\></strong> I can set up a Kovri taiga :)  
<strong>\<rehrar\></strong> and we can have our various Kovri related tasks on there instead of on the getmonero one  
<strong>\<anonimal\></strong> That won’t work, because you’re paid by Ric do work for Monero Project.  
<strong>\<anonimal\></strong> Me or someone else would need to host it.  
<strong>\<anonimal\></strong> But you can do whatever you want.  
<strong>\<anonimal\></strong> 10 minutes left, we need to move on.  
<strong>\<anonimal\></strong> 5. Public relations discussion  
<strong>\<anonimal\></strong> \_4matter is doing some great work behind the scenes in this area.  
<strong>\<anonimal\></strong> He couldn’t make the meeting but I’m assuming he’ll make the next one.  
<strong>\<anonimal\></strong> I like his ideas/approach. He can speak more when he returns.  
<strong>\<anonimal\></strong> I advised him that he shouldn’t repeat the work that rehrar’s done. rehrar did a ton of work in the outreach area and, no fault of his own, it had mixed results.  
<strong>\<rehrar\></strong> it was an eye opening experience :D  
<strong>\<anonimal\></strong> I’ll add an item to the next meeting regarding public relations.  
<strong>\<anonimal\></strong> rehrar got to learn that developers are like violinists:  
<strong>\<anonimal\></strong> they all think they’re hot shit or that they are soloist material - but many are not :)  
<strong>\<anonimal\></strong> s/violinists/young classical violinists/  
<strong>\<anonimal\></strong> Anyway, inside classical humor.  
<strong>\<anonimal\></strong> I watched rehrar’s jitsi meeting recently. I think you have a penchant for sales.  
<strong>\<anonimal\></strong> If you haven’t successfully done that, I wouldn’t be surprised if you do more of that.  
<strong>\<rehrar\></strong> sales? Like selling stuff?  
<strong>\<rehrar\></strong> Selling people on stuff, I guess.  
<strong>\<anonimal\></strong> Yeah, and PR.  
<strong>\<rehrar\></strong> <em>shrug</em> not really one of my interests, but thanks.  
<strong>\<rehrar\></strong> :)  
<strong>\<ErCiccione\></strong> sorry, just finished to read the logs, i’m a bit late to the party. anything you guys want to tell me about translating getkovri?  
<strong>\<anonimal\></strong> Well it’s come in handy.  
<strong>\<anonimal\></strong> Hi ErCiccione  
<strong>\<rehrar\></strong> PR sent ErCiccione with the newest updates similar to getmonero.org  
<strong>\<ErCiccione\></strong> hello :)  
<strong>\<rehrar\></strong> but since getkovri is set up differently, there is still a substantial amount that is not done via tags  
<strong>\<rehrar\></strong> handled via kovri-docs  
<strong>\<ErCiccione\></strong> seen it, tomorrow i will give it a better look and i will change the instructions on taiga if needed  
<strong>\<rehrar\></strong> I’m updating the README for the site after this meeting  
<strong>\<ErCiccione\></strong> ok, perfect will read the workflow changes from there  
<strong>\<anonimal\></strong> Thanks for all the work you’ve done too, ErCiccione.  
<strong>\<\_4matter\></strong> anonimal: saw the ping above. On mobile and out of town for a wedding, but I will read through the above.  
<strong>\<\_4matter\></strong> :)  
<strong>\<anonimal\></strong> \_4matter: ok, I said that you weren’t around and other things. No rush.  
<strong>\<anonimal\></strong> ErCiccione: anything else?  
<strong>\<rehrar\></strong> question: should we have a Kovri defcon meeting on the weekday so it’s easier to attend? Separate from the overall defcon meeting on Saturdays?  
<strong>\<ErCiccione\></strong> anonimal: happy to help. no, not from me. Will try to find some more contributors for translations in future. didn’t have much luck with that last reddit post  
<strong>\<anonimal\></strong> Yes, or move the defcon meetings to a later time on Saturdays.  
<strong>\<rehrar\></strong> I can request it. What time is good?  
<strong>\<rehrar\></strong> This time?  
<strong>\<anonimal\></strong> Good luck ErCiccione, you’ll find them.  
<strong>\<ErCiccione\></strong> :)  
<strong>\<anonimal\></strong> I know where michael is geographically so I understand 15:00 UTC. It’s really up to him since he’s heading the show.  
<strong>\<rehrar\></strong> alright, I’ll send him a message.  
<strong>\<anonimal\></strong> But if the community wants me involved, then they’ll have to budge just a little.  
<strong>\<anonimal\></strong> If not, then they’ll be leaving me out and a big chunk of the project.  
<strong>\<anonimal\></strong> Which has been the case.  
<strong>\<rehrar\></strong> Honestly, Kovri is one of the bigger things that should be at Defcon, at least imo.  
<strong>\<anonimal\></strong> Even though I repeatedly asked if the community meetings could be moved slightly.  
<strong>\<anonimal\></strong> For months. And months.  
<strong>\<anonimal\></strong> But here we are.  
<strong>\<rehrar\></strong> And I’ll fight to make sure you and Kovri are fairly represented there.  
<strong>\<rehrar\></strong> For community meetings, would an hour or two later be better?  
<strong>\<rehrar\></strong> my client refuses to respond  
<strong>\<anonimal\></strong> 17:00 UTC if possible, but that conflicts with the community meetings.  
<strong>\<anonimal\></strong> sgp has always been pretty staunch about that timeslot.  
<strong>\<rehrar\></strong> I’ll tweak a few nipples and see what I can’t get done  
<strong>\<anonimal\></strong> ouch  
<strong>\<rehrar\></strong> sometimes you gotta pull out the big guns  
<strong>\<anonimal\></strong> tweezers  
<strong>\<anonimal\></strong> If they won’t budge, whatever we did worked last time rehrar  
<strong>\<anonimal\></strong> Was it a Tuesday at 20:00 or around there  
<strong>\<anonimal\></strong> Yeah, that.  
<strong>\<rehrar\></strong> after the meeting, we can discuss your meta issues for decentralization. I’ve got a few ideas (that don’t involve me or Core Team).  
<strong>\<anonimal\></strong> Defcon is a lot of work, that’s for sure.  
<strong>\<rehrar\></strong> or whenever you have the time  
<strong>\<rehrar\></strong> dude, what makes defcon a bigger headache is that BCOS won’t communicate with us :(  
<strong>\<anonimal\></strong> I don’t have any time for anything. I don’t even have time to get to “6. Code + ticket discussion / Q &amp; A”  
<strong>\<anonimal\></strong> Ideas are welcome though, of course.  
<strong>\<rehrar\></strong> ok. I’ll put it in the Issue  
<strong>\<anonimal\></strong> What’s the deal with BCOS?  
<strong>\<rehrar\></strong> they…aren’t responding to emails in a timely manner (or at all)  
<strong>\<\_Slack\> \<sean\></strong> background Seinfeld music  
<strong>\<anonimal\></strong> Or you can paste here if you want and I’ll respond  
<strong>\<anonimal\></strong> lol sean  
<strong>\<anonimal\></strong> “So what’s the deal with BCOS?\!”  
<strong>\<rehrar\></strong> Alright, i will be fairly unavailable starting tomorrow and through the 14th  
<strong>\<anonimal\></strong> “Can the NOT afford to communicate with Monero?\!”  
<strong>\<rehrar\></strong> fyi for everyone here :)  
<strong>\<rehrar\></strong> will respond to Wire or Signal if need be, but limited IRC  
<strong>\<anonimal\></strong> Sorry sean, I can’t top your line with anything funnier.  
<strong>\<\_Slack\> \<sean\></strong> BCOS.  
<strong>\<\_Slack\></strong> Command sent from Slack by sean:  
<strong>\<\_Slack\></strong> …that’s the joke.  
<strong>\<anonimal\></strong> Ok. Thanks for the headsup rehrar.  
<strong>\<rehrar\></strong> it’s crazy that nobody’s ever heard of them before this  
<strong>\<anonimal\></strong> lol sean  
<strong>\<rehrar\></strong> but they got such a prominent spot at Defcon  
<strong>\<rehrar\></strong> <em>shrug</em> oh well  
<strong>\<anonimal\></strong> rehrar: and will anyone ever hear about them after defcon…  
<strong>\<rehrar\></strong> evidently they were at last defcon in a village or something  
<strong>\<rehrar\></strong> disappeared for a y ear  
<strong>\<rehrar\></strong> then came back for the next one :D  
<strong>\<\_Slack\> \<sean\></strong> They did post that Coinbase is a sponsor, so I’m wondering why they’re so damn disorganized.  
<strong>\<anonimal\></strong> I don’t know.  
<strong>\<rehrar\></strong> anyways  
<strong>\<oneiric\_\></strong> For 6, I spent most of late-April to May working on multiple subscriptions. Few unit tests left, break it up into smaller chunks for review, and it should be ready.  
<strong>\<anonimal\></strong> Ok, anything else before we move on? We’re in overdrive.  
<strong>\<anonimal\></strong> Thank you oneiric\_, keeping us on track.  
<strong>\<anonimal\></strong> 6. Code + ticket discussion / Q &amp; A  
<strong>\<anonimal\></strong> Ok  
<strong>\<anonimal\></strong> Oh, I didn’t mention, for this and for the FFS check-in, I’ll be submitting the next milestone too.  
<strong>\<rehrar\></strong> woohoo\!  
<strong>\<rehrar\></strong> you pushing the limits, man  
<strong>\<anonimal\></strong> lol, I’m glad <em>someone</em> is excited, haha  
<strong>\<anonimal\></strong> Well at close to 180 hours, yes, I’ll be submitting.  
<strong>\<rehrar\></strong> for real, the community doesn’t appreciate the stupid amounts of work you put in to this project  
<strong>\<anonimal\></strong> I’m tired of the free handouts and I also just want this FFS done as I’m sure everyone else wants too.  
<strong>\<anonimal\></strong> Thanks rehrar.  
<strong>\<anonimal\></strong> Yes, they don’t.  
<strong>\<anonimal\></strong> And most people also think fluffypony is the CEO and lead developer of Monero.  
<strong>\<anonimal\></strong> As seen in every recent interview.  
<strong>\<rehrar\></strong> isn’t that the most bizarre thing?  
<strong>\<anonimal\></strong> Or post somewhere.  
<strong>\<rehrar\></strong> I see a lot of people post that he started monero too  
<strong>\<anonimal\></strong> I think he’s given up on correcting them.  
<strong>\<anonimal\></strong> Anyway, so I’m the CEO and lead developer of Monero too.  
<strong>\<rehrar\></strong> Creator, lead dev, and CEO. Must be nice. :P  
<strong>\<anonimal\></strong> And I have several lambos and boats.  
<strong>\<anonimal\></strong> Hey, this fantasy land is pretty sweet.  
<strong>\<rehrar\></strong> let me in :(  
<strong>\<oneiric\_\></strong> Any jets flown by unicorns?  
<strong>\<anonimal\></strong> 7. Any additional meeting items  
<strong>\<anonimal\></strong> rehrar: it’s simple: just say it and it appears.  
<strong>\<anonimal\></strong> oneiric\_: yes. As many as you want.  
<strong>\<rehrar\></strong> No other items from me.  
<strong>\<anonimal\></strong> Nothing from me but I’m on autopilot right now anyway. If I missed something, please yell.  
<strong>\<anonimal\></strong> Shall we schedule a kovri defcon meeting and if the community channel agrees to be flexible, we just cancel the kovri defcon meeting, rehrar?  
<strong>\<oneiric\_\></strong> Same, anything else I have can be discussed outside meeting, or wait until the next one.  
<strong>\<rehrar\></strong> that sounds like a sane thing to do  
<strong>\<rehrar\></strong> pinging sgp\_\[m\] now  
<strong>\<anonimal\></strong> I’ll open the github issue.  
<strong>\<anonimal\></strong> 8. Confirm next meeting date/time  
<strong>\<rehrar\></strong> Google calendar knows all  
<strong>\<anonimal\></strong> July 5th?  
<strong>\<anonimal\></strong> Or sooner?  
<strong>\<anonimal\></strong> I can’t do 21st but can do 14th and 28th.  
<strong>\<anonimal\></strong> rehrar probably can’t do the 14th  
<strong>\<rehrar\></strong> can’t do 14th as stated, but can do 28th  
<strong>\<rehrar\></strong> ^ mind reader  
<strong>\<anonimal\></strong> oneiric\_: 28th?  
<strong>\<oneiric\_\></strong> 28th works for me too  
<strong>\<sgp\_\[m\]\></strong> anonimal I must have missed your repeated desire to move the commubity meetings. I didn’t realize they conflicted with your schedule, especially since there was a significant period without kovri meetings. I’m open to working out a schedule that works for everyone  
<strong>\<anonimal\></strong> sgp\_\[m\]: this goes back to the beginning of the year if not later  
<strong>\<anonimal\></strong> Whenever you started the community channel.  
<strong>\<anonimal\></strong> It’s all on github and/or irc logs.  
<strong>\<anonimal\></strong> I just gave up complaining.  
<strong>\<anonimal\></strong> rehrar: oneiric\_ I’ll open a new issue for the next kovri meeting  
<strong>\<rehrar\></strong> ok, great  
<strong>\<anonimal\></strong> I do look forward to resolving the Meeting Solutions issue though.  
<strong>\<oneiric\_\></strong> right on  
<strong>\<anonimal\></strong> One simple solution is a meeting bot which uploads logs to a website automatically.  
<strong>\<anonimal\></strong> This is old-school, done-to-death solution and works well.  
<strong>\<anonimal\></strong> And when you want to know the next meeting: \!meeting  
<strong>\<rehrar\></strong> that’s pretty neat  
<strong>\<anonimal\></strong> supybot did/does this, as did others  
<strong>\<anonimal\></strong> I have no idea who’s doing what anymore  
<strong>\<anonimal\></strong> I haven’t been to a Tor meeting in ages but they had their bot the last I saw.  
<strong>\<anonimal\></strong> Anyway, simple solution; but doesn’t satisfy the modern age very well afaict  
<strong>\<rehrar\></strong> ICO a solution  
<strong>\<anonimal\></strong> That’s always the solution  
<strong>\<rehrar\></strong> it’s never not the solution  
<strong>\<anonimal\></strong> “Honey can you grab me milk from the store?” “Sure, startup an ICO.”  
<strong>\<anonimal\></strong> Alright, meeting done?  
<strong>\<rehrar\></strong> Ye  
<strong>\<rehrar\></strong> bai everyone  
<strong>\<rehrar\></strong> kisses for all  
<strong>\<anonimal\></strong> Thanks everyone
