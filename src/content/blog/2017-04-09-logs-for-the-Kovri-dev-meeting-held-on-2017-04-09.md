---
title: Logs for the Kovri Dev Meeting Held on 2017-04-09
summary: Brief review of what has been completed since last meeting, Monero HackerOne Bounty, website discussion, and code & open tickets discussion
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<anonimal\></strong> 1. Greetings  
<strong>\<anonimal\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<anonimal\></strong> 3. Preparation for [96boards.org OpenHours showcase for Kovri / Monero](https://github.com/monero-project/meta/issues/46)  
<strong>\<anonimal\></strong> 4. Status of [Monero HackerOne umbrella and bounty](https://github.com/monero-project/meta/issues/39)  
<strong>\<anonimal\></strong> 5. Code + ticket discussion / Q &amp; A  
<strong>\<anonimal\></strong> 6. Any additional meeting items  
<strong>\<anonimal\></strong> 7. Confirm next meeting date/time  
<strong>\<anonimal\></strong> Hellloooo  
<strong>\<i2p-relay\> {-olark}</strong> Hello party people  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> howdy\!  
<strong>\<guzzi\></strong> Hello  
<strong>\<moroccanmalinois\></strong> hi  
<strong>\<rehrar\></strong> Hi (observing excitedly)  
<strong>\<i2p-relay\> {-iDunk}</strong> Hi  
<strong>\* moneromooo</strong> greets again  
<strong>\<i2p-relay\> \[endogenic\]</strong> no excitement allowed rehrar  
<strong>\<bigreddmachine\></strong> hi  
<strong>\<rehrar\></strong> I’ll see myself out then.  
<strong>\<anonimal\></strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<anonimal\></strong> For me, the past two weeks have spent focusing on 4 things: fixing the OpenBSD dynamic build, PR review/fixes/collaboration, NTCP, and RI (router info).  
<strong>\<anonimal\></strong> a. Jeff at crypto++ has not been responsive lately so my CMake fix for their dynamic OpenBSD is still sitting in PR hell.  
<strong>\<anonimal\></strong> b. Both moroccanmalinois and rakhimov have been PR’ing some great work  
<strong>\<anonimal\></strong> c. Over time I’ve done bits and pieces of work on the NTCP implementation but hadn’t had the chance to do a full study in java I2P’s implementation until recently.  
<strong>\<anonimal\></strong> Combined with more spec review (forunately, the spec is small) I’ve come up with 33 questions/TODOs specifically about, and for, our implementation.  
<strong>\<anonimal\></strong> Once that was done, it turned out that I couldn’t move forward until I worked out any potential RI issues.  
<strong>\<anonimal\></strong> d. That lead me to the unmaintainable mess of our forked RI implementation, which has been neglected, so now at a minimum I’m working on a RI parser/reader/writer refactor. From there, unit-test <em>and then</em> back to NTCP so I can close that damn milestone issue \>:\|  
<strong>\<anonimal\></strong> So, that’s just on my end. Anyone else?  
<strong>\<anonimal\></strong> I know guzzi is doing study for RAII refactoring.  
<strong>\<bigreddmachine\></strong> Salti’s holding pattern for webextensions in FF is making progress  
<strong>\<anonimal\></strong> Oooo cool  
<strong>\<anonimal\></strong> How are they doing on that front?  
<strong>\<bigreddmachine\></strong> 1 of two issues i’m tracking are finished, second is still a ways off  
<strong>\<guzzi\></strong> Review client context implimenting raii  
<strong>\<bigreddmachine\></strong> and no dev docs yet  
<strong>\<moroccanmalinois\></strong> Looking at reload server tunnels <https://github.com/monero-project/kovri/blob/master/src/client/context.cc#L321>  
<strong>\<anonimal\></strong> Excellent, that all sounds good. Anything else before we move onto 3.?  
<strong>\<i2p-relay\> {-olark}</strong> I have been slowly evaluating what will be needed to replace supercop with tweetnacl  
<strong>\<anonimal\></strong> (well, I’m hoping FF will move faster but it sounds like they’re at least <em>moving</em>)  
<strong>\<i2p-relay\> {-olark}</strong> Can rip out all the ecdsa sig types at the same time to work towards the identity refactor work  
<strong>\<bigreddmachine\></strong> anonimal: yes. progress is progress.  
<strong>\<anonimal\></strong> olark: ok this is for \#485, sounds good. Would you be able to resolve \#345 in the mean time?  
<strong>\<i2p-relay\> {-olark}</strong> For EdDSA  
<strong>\<i2p-relay\> \[fluffypony\]</strong> major thunderstorm here, so if I don’t respond it’s because I’ve been struck by lightning (or my house has)  
<strong>\<anonimal\></strong> Eeek\! No charred pony\!  
<strong>\<i2p-relay\> {-olark}</strong> anonimal: Sure  
<strong>\<anonimal\></strong> fluffypony can you see the meeting or is internet intermittent?  
<strong>\<anonimal\></strong> olark: nice\!  
<strong>\<anonimal\></strong> Ok, moving forward,  
<strong>\<i2p-relay\> {-olark}</strong> I will find the time. I have been neglecting kovri :(  
<strong>\<anonimal\></strong> Yes, come back soon ;)  
<strong>\<anonimal\></strong> 3. Preparation for [96boards.org OpenHours showcase for Kovri / Monero](https://github.com/monero-project/meta/issues/46)  
<strong>\<anonimal\></strong> Speaking of neglecting, I hope we don’t let this opportunity slip by ^  
<strong>\<anonimal\></strong> Does anyone know of any effect voice masking software? Military grade (if there is such a thing).  
<strong>\<anonimal\></strong> \*effective  
<strong>\<i2p-relay\> \[fluffypony\]</strong> anonimal: nothing I know of, but I also don’t know if that would be worthwhile or weird  
<strong>\<i2p-relay\> \* fluffypony</strong> tries to convince anonimal to come out the pseudonymous closet  
<strong>\<i2p-relay\> {-pigeons}</strong> yeah its annoying as hell to listen to  
<strong>\<i2p-relay\> {-pigeons}</strong> mouthful of marbles works ok though  
<strong>\<anonimal\></strong> I hear that Barry Manilow recently came out of the closet.  
<strong>\<guzzi\></strong> Pennies  
<strong>\* anonimal</strong> not that I’m a fan, nor am I in that sort of closet  
<strong>\<anonimal\></strong> Well, I’m curious to hear the public’s opinion on whether I should de-anon. Thoughts?  
<strong>\<i2p-relay\> \[endogenic\]</strong> yes\!  
<strong>\<anonimal\></strong> moneromooo ^ \#monero-dev  
<strong>\<i2p-relay\> \[endogenic\]</strong> i will be your bodyguard  
<strong>\<anonimal\></strong> lol awesome\! X)  
<strong>\<i2p-relay\> \[fluffypony\]</strong> anonimal: only reason I suggest it is because Kovri does need a voice, but ultimately it’s your call  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> weren’t you already on the monero missives?  
<strong>\<i2p-relay\> \[fluffypony\]</strong> gingeropolous: no, that was jeff  
<strong>\<moneromooo\></strong> What ? What’s in \#monero-dev ?  
<strong>\<i2p-relay\> \[endogenic\]</strong> anonimal: just think… we can hang out at meetups and such :)  
<strong>\<i2p-relay\> {-olark}</strong> Ultimately your choice anonimal.  
<strong>\<i2p-relay\> {-olark}</strong> Don’t feel pressured to come out becuase people want you to ;)  
<strong>\<sgp\></strong> ^ seconded  
<strong>\<anonimal\></strong> gingeropolous: ^ not Jeff at crypto++, Jeff a former problem contributor who, as he said, has family in U.S. intelligence.  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> he’s satoshi.  
<strong>\<anonimal\></strong> moneromooo I meant ‘what’s your opinion if any?’  
<strong>\* anonimal</strong> and also threw question at \#monero-dev in same line, sorry  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> my apologies. I obviously know whos who here.  
<strong>\<moneromooo\></strong> Of whether you should de-anon ? I wouldn’t want to influence you to.  
<strong>\<anonimal\></strong> Oh np, just clarifying since I said “Jeff” earlier.  
<strong>\<moneromooo\></strong> My view is that the more people actively keep their privacy, the less the massive pressure on everyone else to shed their privacy is.  
<strong>\<anonimal\></strong> Hmm, good point.  
<strong>\<moneromooo\></strong> Not really related to this particular case, but having 99% of people not care about their privacy means that companies and everyone can just screw privacy and not get any noticeable blowback.  
<strong>\<i2p-relay\> \[endogenic\]</strong> think only anonimal’s in the position anonimal’s in as kovri lead tho  
<strong>\<moneromooo\></strong> So I use Tor for random run off the mill browsing partly for that reason too.  
<strong>\<i2p-relay\> \[fluffypony\]</strong> moneromooo: yes, but this is about his status as a contributor and maintainer  
<strong>\<i2p-relay\> \[fluffypony\]</strong> after all, things get really boring if I’m the only one talking at conferences  
<strong>\<moneromooo\></strong> Well, his choice, and I don’t want to interfere in it. But thanks for asking :)  
<strong>\<i2p-relay\> \[endogenic\]</strong> \<3  
<strong>\<i2p-relay\> \[endogenic\]</strong> i wouldn’t go that far fluffy  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> you could just “hire” a spokesperson to be your IRL talking head  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> and they <em>just</em> happen to know a <em>whole</em> lot about everything  
<strong>\<i2p-relay\> \[endogenic\]</strong> rent-a-body  
<strong>\<anonimal\></strong> Ok, so I’m hearing that if I de-anon I get a free(?) bodyguard and can freely promote more-so than what I can do now. I’m also hearing that no one wants to put that kind of pressure of a decision on me.  
<strong>\<anonimal\></strong> I have to say though, I’m wearing more than 1 cap at any given time. Maybe one-too-many? It was a relief to finally sit down and write some code this week. It had been way too long since I’ve done that and I’m ALWAYS HERE working on kovri\!  
<strong>\<iDunk\></strong> I think gingeropolous suggested you should invent an alter ego for public appearances :)  
<strong>\<i2p-relay\> \[endogenic\]</strong> you can choose when to do talks and when to reply to ppl imo  
<strong>\<i2p-relay\> \[endogenic\]</strong> and i bet others will jump in to help  
<strong>\<i2p-relay\> \[fluffypony\]</strong> “I’m fluffy…errrr…fluffynonimal, and I’m a Kovri developer”  
<strong>\<i2p-relay\> \[endogenic\]</strong> just a question of letting us know how we can help  
<strong>\<i2p-relay\> {-pigeons}</strong> even if you do come out, still consider the marbles for talks  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> well iDunk now its ruined  
<strong>\<iDunk\></strong> Damn  
<strong>\<anonimal\></strong> lol, I’ll just show up with marbles in my mouth.  
<strong>\<anonimal\></strong> I must say that, adding public-relations, I love the thought, but I do also love writing code.  
<strong>\<anonimal\></strong> And people love targets, so that’s always something to concern myself with.  
<strong>\<sgp\></strong> You can still do both. Choose the proportion you want  
<strong>\<anonimal\></strong> “just a question of letting us know how we can help” \<— thanks endogenic. I think what will help are 2 things:  
<strong>\<anonimal\></strong> sgp good point  
<strong>\<i2p-relay\> \[fluffypony\]</strong> anonimal: I think that there’s probably less scope to talk about Kovri at conferences right now anyway, but it would be nice for someone to do some podcasts etc. in future  
<strong>\<i2p-relay\> \[endogenic\]</strong> podcasts are a great idea. i honestly doubt most ppl who want to use something like tor even know tor needs an alternative  
<strong>\<i2p-relay\> \[endogenic\]</strong> and i’d enjoy learning more about the kovri tech in that format  
<strong>\<anonimal\></strong> What would help: 1. more people get more familiar with kovri technology so they can answer questions and promote too. And 2. maybe everyone present can give me a solid “yes” or “no” on if they want me to de-anon (i.e., putting aside any other thoughts and responding purely on instinctual feelings)  
<strong>\<anonimal\></strong> bigreddmachine: ^ re: podcast, my decision sooner than later will effect that  
<strong>\<i2p-relay\> \[gingeropolous\]</strong> just go full Mr. Robot. Loose touch with reality, veer into psychosis, and then even <em>you</em> don’t know who you are.  
<strong>\<anonimal\></strong> lololol gingeropolous X)  
<strong>\<sgp\></strong> I just started watching that show. 1 season in. No spoilers please\!  
<strong>\<ArticMine\></strong> To de-anon should be personal chice in my opinion  
<strong>\<anonimal\></strong> Ok I’d say we’re on a tangent for point 3 but this kind of needs to be done IMHO.  
<strong>\<ArticMine\></strong> choice  
<strong>\<anonimal\></strong> All in favor of me de-anoning: yay or nay?  
<strong>\* anonimal</strong> don’t be shy\!  
<strong>\<i2p-relay\> \[endogenic\]</strong> i personally agree it must be personal too. sry to be difficult. there are tradeoffs for sure  
<strong>\<sgp\></strong> Pros: can talk about it more openly, attract new talent with greater outreach, better inform community about developments. Cons: more likely to be a target, maybe you’re really ugly  
<strong>\<i2p-relay\> \[endogenic\]</strong> it’s a kind of burden i think  
<strong>\<sgp\></strong> (just kidding on second con)  
<strong>\<i2p-relay\> \[fluffypony\]</strong> anonimal: I don’t know if we should vote for that, it’s your call  
<strong>\<anonimal\></strong> lol sgp maybe I’m missing a face entirely…  
<strong>\<anonimal\></strong> fluffypony ok  
<strong>\<anonimal\></strong> So resolving 3., fluffypony + pigeons, how’s your schedule lately?  
<strong>\<i2p-relay\> \[fluffypony\]</strong> pigeons is down my side of the world for a couple of weeks, so we can make time around that  
<strong>\<anonimal\></strong> Oh neat\! Should I contact Robert to schedule a definitive date now?  
<strong>\<i2p-relay\> \[fluffypony\]</strong> well it depends on if you want to do me + pigeons or you + pigeons  
<strong>\<bigreddmachine\></strong> anonimal: soory, was afk. re the podcast bit, if you do decide to de-anon yourself, i’d be happy to host your coming out of the closet party\! but garbling voice is doable too.  
<strong>\<i2p-relay\> \[fluffypony\]</strong> or all 3 of us  
<strong>\<anonimal\></strong> fluffypony: I would think either all 3 (or at minimum just you 2). bigreddmachine I’d like to hear/learn more about any garble tech available, even if it’s annoying.  
<strong>\<i2p-relay\> \[fluffypony\]</strong> anonimal: ok let’s talk afterwards, and we can schedule it with them  
<strong>\<anonimal\></strong> Ok will do  
<strong>\<anonimal\></strong> bigreddmachine: I’ll PM you later too  
<strong>\<anonimal\></strong> Anything else on 3.?  
<strong>\<moneromooo\></strong> Voice garbling sounds very reversible (unless it’s voice recogniation plus text to speech).  
<strong>\<bigreddmachine\></strong> TTS certainly would work.  
<strong>\* anonimal</strong> considered TTS, maybe I should learn to type faster first  
<strong>\<anonimal\></strong> (or prepared statements?)  
<strong>\<anonimal\></strong> (defeats the fun of interviews/speeches/conferences?)  
<strong>\<anonimal\></strong> Ok, we’ll talk more later.  
<strong>\<i2p-relay\> \[endogenic\]</strong> hehe seems a little creepy  
<strong>\<anonimal\></strong> 4. Status of [Monero HackerOne umbrella and bounty](https://github.com/monero-project/meta/issues/39)  
<strong>\<moneromooo\></strong> Copy and “paste” words from movies, paste them one by one to make up sentences. Like the old words cut off from a newspaper :D  
<strong>\<anonimal\></strong> lol moneromooo, not serial-killer-like in any way whatsoever…  
<strong>\<anonimal\></strong> re: 4. We have hackerone.com/monero \!  
<strong>\<i2p-relay\> \[fluffypony\]</strong> anonimal: has anything for 4. been written up in the style of an FFS proposal or not yet?  
<strong>\* anonimal</strong> grabs only FFS for 4.  
<strong>\<anonimal\></strong> Links is in the meta issue, one moment.  
<strong>\<anonimal\></strong> <https://forum.getmonero.org/6/ideas/87597/monero-bounty-for-hackerone>  
<strong>\<anonimal\></strong> Is that what you mean?  
<strong>\<i2p-relay\> \[fluffypony\]</strong> ok - do you want me to move that to Funding Required in its current form?  
<strong>\<anonimal\></strong> Eek, I should update?  
<strong>\<anonimal\></strong> The prop looks unclear as-is  
<strong>\<i2p-relay\> \[fluffypony\]</strong> probably worthwhile  
<strong>\<anonimal\></strong> We decided on 500 to start  
<strong>\<anonimal\></strong> Ok, I’ll edit after the meeting or do you need me to do that now?  
<strong>\<i2p-relay\> \[fluffypony\]</strong> no after is fine  
<strong>\<anonimal\></strong> Ok  
<strong>\<anonimal\></strong> So for 4, I still have to PR VRP’s to the various repos.  
<strong>\<anonimal\></strong> Also invite the appropriate people to H1. But fluffypony I think you’ll want to do that?  
<strong>\<i2p-relay\> \[fluffypony\]</strong> sure  
<strong>\<anonimal\></strong> moneromooo is already in there. luigi is not yet though.  
<strong>\<anonimal\></strong> Alright. From there we should raise the funds first and <em>then</em> start inviting hackers on H1.  
<strong>\<anonimal\></strong> Any agreements/disagreements?  
<strong>\<sgp\></strong> I agree  
<strong>\<anonimal\></strong> Btw, many hackers are already <em>on</em> H1, by invite I mean invite to start looking at our projects.  
<strong>\<anonimal\></strong> Ok. Anything else on 4.?  
<strong>\<anonimal\></strong> 5. Code + ticket discussion / Q &amp; A  
<strong>\<i2p-relay\> \[fluffypony\]</strong> nothing else from my side on 4  
<strong>\* anonimal</strong> takes peek  
<strong>\<anonimal\></strong> re: website issue, is ajs here?  
<strong>\<ajs\></strong> present  
<strong>\<anonimal\></strong> Hi\!  
<strong>\<anonimal\></strong> Any news the website front?  
<strong>\<i2p-relay\> {-pigeons}</strong> No I am the holdup there  
<strong>\<anonimal\></strong> Ok. ETA on resolving any holdups?  
<strong>\<bigreddmachine\></strong> shoot, i was just about to ask about that. didn’t realize we had monero-project/kovri-site. how can i help?  
<strong>\<ajs\></strong> have backed up work that has been done and waiting for access to a server  
<strong>\<anonimal\></strong> Btw rehrar popped in recently and said him and/or his wife would give a try a logo redesign.  
<strong>\<rehrar\></strong> Hi. Yes. :D  
<strong>\<i2p-relay\> {-pigeons}</strong> i’ll try to set something up in 24 hours or so  
<strong>\<anonimal\></strong> Wow, that fast? Cool.  
<strong>\<i2p-relay\> \[pero\]</strong> so what happened to the logo i did  
<strong>\<anonimal\></strong> pero: it was NACK’ed. This was clearly stated in github issue that I posted in the previous meeting.  
<strong>\<rehrar\></strong> I’d also like to give the Kovri website a go, pending on the logo and branding. :)  
<strong>\<i2p-relay\> \[pero\]</strong> why?  
<strong>\<anonimal\></strong> pero: I don’t have the files though if that’s what you mean.  
<strong>\<anonimal\></strong> fluffypony: ^  
<strong>\<i2p-relay\> \[pero\]</strong> you were sent the files  
<strong>\<i2p-relay\> \[pero\]</strong> so as i see it, a contributor contributed a bunch of time and spiffied up the previous logo  
<strong>\<anonimal\></strong> Not anymore. Tis’ the magic of deleted emails.  
<strong>\<i2p-relay\> \[pero\]</strong> the community was involved too…  
<strong>\<i2p-relay\> \[pero\]</strong> then it unilaterally ‘nack’d’  
<strong>\<anonimal\></strong> Yes. This was all clearly stated in the github PR.  
<strong>\<anonimal\></strong> Where is your logo work PR?  
<strong>\<i2p-relay\> \[pero\]</strong> wow what a shitty way to waste contributor’s time  
<strong>\<anonimal\></strong> You PR’d nothing. Community opinion does not equal final decision.  
<strong>\<anonimal\></strong> Off you go pero, the resident troll.  
<strong>\<i2p-relay\> \[pero\]</strong> lol?  
<strong>\<anonimal\></strong> You knew from the start that fluffypony and I would make a final decision. Do I really need to bring up logs from months ago?  
<strong>\<i2p-relay\> \[pero\]</strong> the logo assets were emailed to you and pony  
<strong>\<i2p-relay\> \[pero\]</strong> there was no request to pr anything  
<strong>\<ajs\></strong> rehrar bigreddmachine - I made a very basic Jekyll site.. files at: <https://github.com/anonimal/kovri-site>  
<strong>\<i2p-relay\> \[pero\]</strong> the request was for the files to be emailed  
<strong>\<i2p-relay\> \[pero\]</strong> and your ‘troll’ remark is uncalled for and rude?  
<strong>\<i2p-relay\> \[pero\]</strong> wtf is that  
<strong>\<anonimal\></strong> pero you have two options: 1. being kicked from this channel for disrupting a meeting or 2. venting into <https://github.com/monero-project/kovri/pull/488> for all the world to see.  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> ty ajs. will this be affected by the re-design that rehrar is doing?  
<strong>\<rehrar\></strong> Well, I think ideally the redesign that is done for getmonero.org should have an influence on the Kovri website (just influence, not dictate)  
<strong>\<rehrar\></strong> and the logo redesign I will propose (just a proposal) I think definitely should have a larger influence on the website  
<strong>\<i2p-relay\> \[pero\]</strong> whats so hard about contacting the person that did the work?  
<strong>\<anonimal\></strong> rehrar: that sounds good  
<strong>\<rehrar\></strong> So before I start working on anything Kovri website related, we’re going to try to get a logo to you guys before this week is over.  
<strong>\<rehrar\></strong> I’ll drop it on here and the Kovri repo as an issue to look over when it’s done.  
<strong>\<rehrar\></strong> And it is obviously open to suggestions or tweaks when we show it  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> ty rehrar - but from a content standpoint, the re-design is sort-of content agnostic, right? as in, i could write a page and the formatting might change but if it’s in a markdown file jekyll will just ingest it and reformat, right?  
<strong>\<rehrar\></strong> for Kovri, not getmonero.org, right?  
<strong>\<anonimal\></strong> Did you have any plans to re-use material from monero site (as to save time, etc.)?  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> well, both i suppose, but kovri specifically  
<strong>\<ajs\></strong> bigreddmachine: site design is rudimentary and could be easily changed if need be  
<strong>\<rehrar\></strong> The content is going to be restructured for getmonero.org, I’m not going to do a lot of work on copy, unless people think it’s really needed.  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> (sorry, i got us off topic)  
<strong>\* anonimal</strong> whatever is easiest to maintain IMHO  
<strong>\<rehrar\></strong> Pages will be shuffled around, and some things within pages will be shuffled around (all of this will be submitted in designs prior to everything being built)  
<strong>\<rehrar\></strong> as for Kovri, it won’t have nearly as much content yet, so I don’t think it’ll be a huge issue.  
<strong>\<rehrar\></strong> does that answer your question?  
<strong>\<rehrar\></strong> If not, the short answer is yes, it should be content agnostic, and I will work with you guys in the rare cases where it is not.  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> not entirely but close enough, thanks.  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> ahh, yeah that last bit helps  
<strong>\<rehrar\></strong> great\!  
<strong>\<anonimal\></strong> Question:  
<strong>\<anonimal\></strong> rehrar: IMHO, from the work of yours I’ve seen, since you’re an actual designer/creator/implementer, I’m wondering if you, bigreddmachine, ajs and pigeons would consider being the ‘website team’ to get this up-and-running. I can move the repo when we’re online. Does this sound fair or something of interest?  
<strong>\<anonimal\></strong> It sounds like you’re already doing that, I’m just wondering for my own piece of mind (e.g. do I need to re-schedule my work load for website work, etc.)  
<strong>\<i2p-relay\> \[endogenic\]</strong> But not both\!  
<strong>\<rehrar\></strong> That sounds fine with me. Pardon me for my ignorance, but what will be bigredmachine, ajs, and pigeons roles?  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> i’m happy to help with some content, as i am trying to learn about the tech anyway so documenting it is an obvious step.  
<strong>\<anonimal\></strong> endogenic too, hop on the site train\!  
<strong>\<rehrar\></strong> if you can focus more on Kovri, I would do it.  
<strong>\<anonimal\></strong> rehrar: re: bigreddmachine ajs and pigeons, let’s chat after the meeting since we’re out of time  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> design-wise, i can give my two cents but i’d like to be hands off there. just more of a feedback guy, like “hey, this isn’t intuative” or whatever  
<strong>\<rehrar\></strong> I don’t think any of us have a problem bugging you if we need something.  
<strong>\<rehrar\></strong> I’m not able to stick around for much longer, actually.  
<strong>\<rehrar\></strong> We can set up a meeting time for alter this week?  
<strong>\<rehrar\></strong> \*later  
<strong>\<anonimal\></strong> rehrar: just pop in anytime if you want to make an official website meeting  
<strong>\<rehrar\></strong> sounds good  
<strong>\<rehrar\></strong> gotta split. Seeya homes.  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> i can’t, but just summarize discussions on github issue and tag me  
<strong>\<anonimal\></strong> bigreddmachine: that’s right, you’re not always irc’able.  
<strong>\<i2p-relay\> \[fluffypony\]</strong> Can I take the bot down? I’m in a YouTube show mow  
<strong>\<i2p-relay\> \[fluffypony\]</strong> Now  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> anonimal: i try to stay off during week to stay focused on my job.  
<strong>\<i2p-relay\> \[endogenic\]</strong> anonimal: oh no not me, i was just trolling about “fair or of interest”  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> meow\*  
<strong>\<anonimal\></strong> Ok, moving on 6. Any additional meeting items  
<strong>\<anonimal\></strong> None from me. guzzi said like 2 lines.  
<strong>\<i2p-relay\> \[endogenic\]</strong> I think pero could be of help on the site too as i think he has lots of exp there  
<strong>\<anonimal\></strong> 7. Confirm next meeting date/tim  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> just that i’ll keep tracking FF proxy and looking for alternatives.  
<strong>\<i2p-relay\> \[bigreddmachine\]</strong> 23 Apr?  
<strong>\<anonimal\></strong> Yes, same time in two weeks.  
<strong>\<i2p-relay\> \[fluffypony\]</strong> Yep  
<strong>\<anonimal\></strong> Thank you everybody\!
