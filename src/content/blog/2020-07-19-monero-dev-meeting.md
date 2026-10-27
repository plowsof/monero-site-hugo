---
title: Logs for the Dev Meeting Held on 2020-07-19
tags: [dev diaries, core, crypto]
author: asymptotically / ErCiccione
---

# Logs

<strong>\<ErCiccione\[m\]\></strong> Ok everybody let's start this meeting. This is an important one since we should decide the date for the upcoming network upgrade and what consensus changes should be included. The agenda is here: <https://github.com/monero-project/meta/issues/485>  
<strong>\<ErCiccione\[m\]\></strong> Let's have a round of greetings to get an idea of who is here  
<strong>\<SerHack\></strong> Hi  
<strong>\<sgp\_\></strong> Hello  
<strong>\<ErCiccione\[m\]\></strong> Hi everybody  
<strong>\<sarang\></strong> Hello  
<strong>\<Snipa\></strong> Good morning.  
<strong>\<sethsimmons\></strong> Hi all :)  
<strong>\<rbrunner\></strong> Grüezi  
<strong>\<ErCiccione\[m\]\></strong> So the main point is to decide what are we going to include in the next release, but before that, would be great to have an overview of the status of CLSAG and related audits.  
<strong>\<ErCiccione\[m\]\></strong> Sarang, go ahead please  
<strong>\<ErCiccione\[m\]\></strong> :)  
<strong>\<sarang\></strong> Sure  
<strong>\<sarang\></strong> JP and Antony (the reviewers) have completed their audit of the preprint and code  
<strong>\<sarang\></strong> They're finalizing the report for public release  
<strong>\<sarang\></strong> The preprint has already been updated, and the code does not require any security updates  
<strong>\<sarang\></strong> moneromooo is in the process of rebasing the code  
<strong>\<sarang\></strong> I've been in contact with folks on the Ledger and Trezor teams throughout the process, since they have their own development and release timelines  
<strong>\<moneromooo\></strong> in the process of preparing to get ready to start rebasing the code  
<strong>\<sarang\></strong> :)  
<strong>\<ErCiccione\[m\]\></strong> What's the ETA for having it PRd and ready for final reviews?  
<strong>\<sarang\></strong> Trezor is pretty much ready to go; they'll need the fork height and can then update firmware, but the Monero-specific development is done  
<strong>\<sarang\></strong> Ledger has done most of the work already and has code ready for integration on their side, but it hasn't been completed yet  
<strong>\<sarang\></strong> The person I've been working with (Francois) said the team that does the firmware integrations does \_not\_ have this on their 2-month timeline for some reason  
<strong>\<sarang\></strong> and that Francois would not be able to do the integration until after September 21 due to scheduling  
<strong>\<sarang\></strong> They're check to see if the Ledger integration team can prioritize this if needed  
<strong>\<sarang\></strong> Further, they want a couple of weeks to test after the integration is complete  
<strong>\<sarang\></strong> and then can set the fork height and release on whatever timeline they choose  
<strong>\<sarang\></strong> Is there a general opinion of when the upgrade should be, ideally?  
<strong>\<rbrunner\></strong> Personally I don't see much more argument than "Why wait with improvements" ...  
<strong>\<sarang\></strong> It seems like Ledger is the biggest unknown right now  
<strong>\<sgp\_\></strong> Annoying that Ledger can't do any work for 2 months  
<strong>\<sethsimmons\></strong> I'm all for pushing this ASAP once code is ready to go, but if Ledger is \#soon we could wait for that.  
<strong>\<sarang\></strong> Francois asked for 4 weeks between release and the upgrade height, presumably for prioritizing testing  
<strong>\<ErCiccione\[m\]\></strong> I guess ledger will have to adapt their schedule.  
\<sgp\_ "Annoying that Ledger can't do an"\> Yeah no kidding...  
<strong>\<rbrunner\></strong> "on whatever timeline they choose" sounds a little, well, harsh  
<strong>\<sarang\></strong> but they are unavailable until September 21 to do the rebase and integration  
<strong>\<ErCiccione\[m\]\></strong> Sarang: that's a good idea reguardless and we usually do it afaik  
<strong>\<sarang\></strong> rbrunner: I didn't mean that to sound harsh  
<strong>\<sethsimmons\></strong> Do we have a "release checklist" for this including these items?  
<strong>\<sarang\></strong> I just meant that I don't know what's required for their releases  
<strong>\<rbrunner\></strong> Alright :)  
<strong>\<ErCiccione\[m\]\></strong> sethsimmons: the checklist is something good to have. We can discuss that once we have a date :)  
<strong>\<sethsimmons\></strong> Ok, I'll start capturing some items for it to circle back to later.  
<strong>\<ArticMine\></strong> So we are looking realistically at the end of October?  
<strong>\<sarang\></strong> If the Ledger timeline works as I understand it from Francois, it sounds like end of October would be the soonest they could support  
<strong>\<sarang\></strong> but it's unclear if that's guaranteed to work for the Ledger team  
<strong>\<sethsimmons\></strong> What can we do to get a clearer timeline for them?  
<strong>\<rbrunner\></strong> We all on ourselves could do this probably a month earlier, right?  
<strong>\<sgp\_\></strong> 3 months of notice is extremely generous time  
<strong>\<sarang\></strong> sethsimmons: I'm not sure  
<strong>\<sarang\></strong> Francois is reaching out to the coin integration team to get a better sense of their prioritization  
<strong>\<sarang\></strong> I haven't heard back about this yet  
<strong>\<ErCiccione\[m\]\></strong> It is extremely generous. I wouldn't go beyond three months  
<strong>\<sarang\></strong> But part of this seems to be that Francois is not available to do the necessary rebase until after Sep 21 for other reasons  
<strong>\<sethsimmons\></strong> And there isn't anyone else at Ledger that can do it?  
<strong>\<sarang\></strong> I do not know  
<strong>\<sarang\></strong> Someone else previously worked on Monero support with Ledger, but recently passed this on to Francoid  
<strong>\<sarang\></strong> \*Francois  
<strong>\<sethsimmons\></strong> Ah, yes, forgot about that.  
<strong>\<sgp\_\></strong> What about tentatively saying Oct 1?  
<strong>\<ErCiccione\[m\]\></strong> Sounds good to me  
<strong>\<sarang\></strong> I don't think that works  
<strong>\<rbrunner\></strong> Maybe depends on Ledger's reaction to that.  
<strong>\<dEBRUYNE\></strong> Seems too early  
<strong>\<dEBRUYNE\></strong> We also have to account for other wallet providers such as MyMonero  
<strong>\<ArticMine\></strong> I would suggest October 31  
<strong>\<UkoeHB\_\></strong> Spooky  
<strong>\<sarang\></strong> If Francois can start the integration right away on Sep 21 and Ledger prioritizes it on their timeline, they'd still want a couple of weeks to test their release with updated Monero code before releasing firmware with the block height  
<strong>\<ErCiccione\[m\]\></strong> I wouldn't base the timeline on ledger's needs. We are giving them planty of time to adapt  
<strong>\<sarang\></strong> I agree that at some point the release needs to happen, but I hope there can be as much support as is possible in a reasonable timeline  
<strong>\<dEBRUYNE\></strong> I am all for allotting time for third-party wallets etc., but due to Ledger we're basically frozen for 2 months  
<strong>\<ErCiccione\[m\]\></strong> They are a company that makes money on Monero. They ahould adapt on us, not the other way round  
<strong>\<ErCiccione\[m\]\></strong> \*should  
<strong>\<rbrunner\></strong> I tend to agree. If some entity cannot live with 3 months of advance warning, well, tough.  
<strong>\<ErCiccione\[m\]\></strong> Giving plenty of time is fine. Adapting to their priorities is not  
<strong>\<rbrunner\></strong> That's half of our "old" hardfork schedule, after all  
<strong>\<UkoeHB\_\></strong> There have also been months of advance warning. The code was written a while ago  
<strong>\<sarang\></strong> Well, they were also presumably waiting to know of any changes  
<strong>\<ErCiccione\[m\]\></strong> Thanks for the thumbs up on matrix but those don't show up on IRC, please write what's in your mind :)  
<strong>\<sarang\></strong> I know that Francois was unavailable to join this meeting today (but said they would read the logs later), but I can present the October 31 and get their thoughts  
<strong>\<sgp\_\></strong> I still would rather present Oct 1  
<strong>\<sethsimmons\></strong> As much as leaving Ledger users out to dry sucks (that includes me), if we give 3m and thats not enough with a lot of extra runway before now I'm not sure thats something we can wait even longer for.  
<strong>\<sarang\></strong> Perhaps someone else can do the necessary rebase  
<strong>\<sgp\_\></strong> Oct 31 is the absolute latest and is very non-ideal  
<strong>\<sethsimmons\></strong> Yeah I'd love to hear if anyone else at Ledger can step in  
<strong>\<sarang\></strong> They made it sound like rebase and working with Ledger integration team was all that was left to do  
<strong>\<sethsimmons\></strong> 2mo without a way to rebase is.. odd  
<strong>\<ErCiccione\[m\]\></strong> I tend to agree woth sgp  
<strong>\<ArticMine\></strong> I would make October 31 firm, or maybe something like Oct 20  
<strong>\<ArticMine\></strong> but make it firm  
<strong>\<sarang\></strong> OK, so working backward from there  
<strong>\<sarang\></strong> October 1 is the ideal \_fork height\_?  
<strong>\<sarang\></strong> Not release  
<strong>\<sgp\_\></strong> Coffee Chat planned on Oct 17. We can make another update edition  
<strong>\<ErCiccione\[m\]\></strong> Oct 17 sounds like a good compromise.  
<strong>\<ArticMine\></strong> Yes that seems reasonable  
<strong>\<sethsimmons\></strong> That gives them 3+ weeks to rebase/test after their 9/21 date  
<strong>\<sethsimmons\></strong> Hopefully that is plenty.  
<strong>\<sarang\></strong> So I'd like to know what the proposed dates would be for (a) setting the block height, (b) releasing code, (c) the upgrade height occurring  
<strong>\<sgp\_\></strong> b) Sept 17  
<strong>\<sarang\></strong> Of course, once the Monero code is rebased, they can build and test on a private testnet as they wish  
<strong>\<ErCiccione\[m\]\></strong> Block height 17 oct release one month before?  
<strong>\<dEBRUYNE\></strong> sethsimmons: We need a release at least a few weeks in advance of the height  
<strong>\<sgp\_\></strong> There will need to be another release for Ledger but that's only impactful to Ledger users, not consensus  
<strong>\<dEBRUYNE\></strong> Preferably a month or so  
<strong>\<sethsimmons\></strong> For sure  
<strong>\<sarang\></strong> Note that there's already Ledger-specific code in the current Monero CLSAG branch  
<strong>\<rbrunner\></strong> Yes, that would speak for a September 17 release, right?  
<strong>\<ErCiccione\[m\]\></strong> Release 17 sept, hard fork 17 october?  
<strong>\<ErCiccione\[m\]\></strong> Are people ok with that?  
<strong>\<kinghat\[m\]\></strong> does monero have a list of commandments? 11. thou shalt not hold releases for outside entities.  
<strong>\<ArticMine\></strong> That makes sense  
<strong>\<kinghat\[m\]\></strong> amen  
<strong>\<rbrunner\></strong> And maybe merged our changes into master on August 17? With time to play around on Testnet  
<strong>\<sarang\></strong> OK, so when would the height be finalized?  
<strong>\<sarang\></strong> Since that needs to go into their dev cycle  
<strong>\<sarang\></strong> (this is where a release checklist would be \_very\_ helpful...)  
<strong>\<ErCiccione\[m\]\></strong> I guess even now if we have a date for the hf.  
\<sarang "(this is where a release checkli"\> I'm compiling a starter as we speak :)  
<strong>\<rbrunner\></strong> Seems so, the hardfork height should the be least problem if we have a date :)  
<strong>\<sarang\></strong> rbrunner: right, but it needs to happen :D  
<strong>\<sethsimmons\></strong> It could vary slightly in timing depending on HR changes, but we could set it now  
<strong>\<sarang\></strong> sethsimmons: block times are pretty consistent overall  
<strong>\<sethsimmons\></strong> Generally, yes, I wouldn't expect much variance.  
<strong>\<sgp\_\></strong> Why not pick the exact height shortly before the Sept \~17 release  
<strong>\<sgp\_\></strong> We did the important part of choosing the date today  
<strong>\<ErCiccione\[m\]\></strong> Does anybody have anything against 17 september release, 17 october hard fork? Otherwise we can officialize it as decided  
<strong>\<sethsimmons\></strong> Sounds good to me.  
<strong>\<sarang\></strong> OK, so to recap... the intent is to merge all changes by August 17 for testnet, release on September 17, and fork on October 17?  
<strong>\<ArticMine\></strong> The release need to have the fork hard coded?  
<strong>\<rbrunner\></strong> I think it better has it, yes  
<strong>\<sgp\_\></strong> Yeah  
<strong>\<sarang\></strong> moneromooo: since you're getting all the CLSAG stuff rebased and updated, does that sound reasonable?  
<strong>\<moneromooo\></strong> I can do it in time yes.  
<strong>\<sarang\></strong> I'll reach out to Francois again with this timeline and see what the Ledger team can prioritize  
<strong>\<sarang\></strong> and will reach out to the Trezor team too  
<strong>\<sarang\></strong> Trezor basically said "let us know when your code is done and the height is set, and we're good"  
<strong>\<ErCiccione\[m\]\></strong> Nice. Let's keep going then  
<strong>\<sgp\_\></strong> Trezor sounds awesome haha  
<strong>\<ErCiccione\[m\]\></strong> What other consensus changes do we want in?  
<strong>\<rbrunner\></strong> Are there any waiting?  
<strong>\<sethsimmons\></strong> Only potential one is BP+, correct?  
<strong>\<sgp\_\></strong> There were a few more things included in the logs I posted in the meeting issue  
<strong>\<ArticMine\></strong> and issue 70 in MRL  
<strong>\<sgp\_\></strong> Coinbase rings is one I'm pushing for  
<strong>\<moneromooo\></strong> I want to straightn out some unlock time stuff, technically a consensus change, but no functional change.  
<strong>\<moneromooo\></strong> I've been meaning to do that for a long while.  
<strong>\<sarang\></strong> If the freeze deadline is mid-August, I doubt BP+ could safely make it in  
<strong>\<sgp\_\></strong> moneromooo: sounds good to me :)  
\<sgp\_ "Coinbase rings is one I'm pushin"\> What is needed for that?  
<strong>\<sarang\></strong> but TBH the size savings aren't so significant as to make that a huge loss  
<strong>\<sethsimmons\></strong> AKA could coinbase rings easily make it in in time?  
<strong>\<sgp\_\></strong> BP+ would also need more review/audit right?  
\<sarang "but TBH the size savings aren't "\> Yeah no need to rush that at all.  
<strong>\<sarang\></strong> sgp\_: I personally think so, but part of it depends on what the actual diffs from the current code end up being  
<strong>\<sgp\_\></strong> So no BP+ then  
<strong>\<sarang\></strong> When I brought up BP+ earlier (when the preprint came out), the reaction seemed quite "meh"  
<strong>\<sarang\></strong> and only now seems to have come up again with the new CCS  
<strong>\<sarang\></strong> But no, I would not plan on BP+ for the fall upgrade  
<strong>\<sarang\></strong> and certainly don't block for it  
<strong>\<ArticMine\></strong> How big are the savings?  
<strong>\<sarang\></strong> Something like 90 bytes per single proof  
<strong>\<sarang\></strong> Not massive, but not trivial either  
<strong>\<ErCiccione\[m\]\></strong> Ok, so seems that consensus is to keep bp+ out for now.  
<strong>\<ErCiccione\[m\]\></strong> What abut coinbase rings? Do we need more discussion about that?  
<strong>\<sgp\_\></strong> For coinbase-only rings, luigi supports reducing the coinbase ringsize to only 1  
<strong>\<sethsimmons\></strong> I'm still not sure whats still needed for that/how feasible it is to make it into the HF  
<strong>\<sethsimmons\></strong> sgp\_: can you speak to that?  
<strong>\<sethsimmons\></strong> I'm for the change overall, just not sure on details  
<strong>\<sgp\_\></strong> I can't speak to moo and others' ability to code it in time  
<strong>\<sethsimmons\></strong> moneromooo: any idea on timelines for that/is anyone else helping with coding that?  
<strong>\<moneromooo\></strong> Nobody is doing this AFAIK. I won't unless MRL clearly says it should be done.  
<strong>\<moneromooo\></strong> In which case it's an easy change I think.  
<strong>\<rbrunner\></strong> Yeah, reading the IRC notes on the meta issue I was wondering whether there is already our famous "loose consensus" about this, or quite diverging opinions  
<strong>\<sethsimmons\></strong> sarang: any feedback on that overall?  
<strong>\<sethsimmons\></strong> I've seen back and forth but no clear decision.  
<strong>\<rbrunner\></strong> After all it's again some step up in protocol complexity.  
<strong>\<ErCiccione\[m\]\></strong> rbrunner: my feeling too  
<strong>\<ArticMine\></strong> I see the question being consensus rather than coding time  
<strong>\<sethsimmons\></strong> Appears so :)  
<strong>\<sarang\></strong> I marginally support such a change, but it would require pretty hefty testing  
<strong>\<sarang\></strong> Since it would affect how outputs are selected in the distribution  
<strong>\<sgp\_\></strong> This doesn't require a consensus change, but it's related to <https://github.com/monero-project/monero/issues/5222>  
<strong>\<sethsimmons\></strong> coinbase rings requires consensus change, correct?  
<strong>\<sgp\_\></strong> Yeah  
<strong>\<moneromooo\></strong> Yes, if you want nodes to reject those that don't behave.  
<strong>\<sethsimmons\></strong> Figured, just wanted to make sure.  
<strong>\<sethsimmons\></strong> The main reason I'd like to see it in this upgrade (if we can reach rough consensus) is because its not worth its own HF so would have to wait for another down the line  
<strong>\<sethsimmons\></strong> Which could be a while.  
<strong>\<sethsimmons\></strong> Would it be worthwhile to separate out a meeting for that discussion?  
<strong>\<sarang\></strong> sethsimmons: for which proposal exactly?  
<strong>\<sarang\></strong> (too many things flying back and forth)  
<strong>\<sethsimmons\></strong> coinbase ring changes  
<strong>\<sethsimmons\></strong> SOrry :)  
<strong>\<ErCiccione\[m\]\></strong> I would say let's wait for clear consensus before deciding about coinbase rings in the october hard fork. It's not super urgent anyway and we don't have to decide now.  
<strong>\<sarang\></strong> Rushing output selection changes seems unwise  
<strong>\<sarang\></strong> but that's not a reason not to do them if desired, of course  
<strong>\<rbrunner\></strong> Well, if we want to be able to play with the release on Testnet in 1 month, that's not much time left.  
<strong>\<sethsimmons\></strong> True, especially since it seems to need a good bit of testing/verification even after code release  
<strong>\<hyc\></strong> you can always setup private testnets  
<strong>\<sarang\></strong> The CLSAG changes are significant enough that I think delaying for smaller changes is not worth it  
<strong>\<sarang\></strong> Having plenty of time to test CLSAG will be important  
<strong>\<sethsimmons\></strong> Definitely agree.  
<strong>\<sgp\_\></strong> I don't think this would cause a delay; rather no one else seems enthusiastic about it  
<strong>\<sethsimmons\></strong> I'm enthusiastic about it :P But there certainly doesn't seem to be strong consensus  
<strong>\<rbrunner\></strong> I would rather wait a little and wait for 50+ rings, with Triptych, making some such problems marginal as I see it  
<strong>\<hyc\></strong> no clear benefit, nobody knows what the risks actually are. sounds like a bad idea  
<strong>\<sethsimmons\></strong> Hmm, hadn't thought about what effect increased ringsizes would have on it in future.  
<strong>\<sgp\_\></strong> The problem stays and scales, but the convincing ringsize is still larger  
<strong>\<ErCiccione\[m\]\></strong> Alright. I think the general feeling is to not include coinbase rings in the upcoming release. Let's not go in depth about it now, it can be discussed in another meeting :)  
<strong>\<sgp\_\></strong> Sure, no one else really cares so pass  
<strong>\<ErCiccione\[m\]\></strong> Anything else that we want in? Or any blockers that should be resolved?  
<strong>\<rbrunner\></strong> Well, not care sounds harsh, just different weighting of trade-offs maybe  
<strong>\<sarang\></strong> sgp\_: I do care, and would support a change if implemented and tested carefully  
<strong>\<sarang\></strong> I think it's somewhat marginal for heuristics, as I've said elsewhere  
<strong>\<ErCiccione\[m\]\></strong> As far as i understood there shouldn't be blockers, right? The biggest issue right now seems to be ledger that cpuld be late  
<strong>\<sarang\></strong> Right, it's not clear when the Ledger release would be available  
<strong>\<rbrunner\></strong> Let's see what they come up if a little gentle pressure  
<strong>\<sarang\></strong> Yeah, now that there's a date in mind, I'll let them know and see what could be done  
<strong>\<rbrunner\></strong> Of an October 17 hardfork  
<strong>\<sarang\></strong> Perhaps they hadn't prioritized because no date was known  
<strong>\<sarang\></strong> which is understandable  
<strong>\<sarang\></strong> And if there are useful coinbase changes and/or BP+, that would make for a nice subsequent release at some point  
<strong>\<sethsimmons\></strong> Good point on the subsequent release :)  
<strong>\<rbrunner\></strong> So we won't run out of hardforks anytime soon :)  
<strong>\<sethsimmons\></strong> Gotta keep the FUD alive :D  
<strong>\<ErCiccione\[m\]\></strong> Alright. So, let's start talking about splitting duties. Wpuld be good to have a checklist of stuff that needs to be done and people willing to take care of it  
<strong>\<sarang\></strong> Yeah, a while back I brought up the idea of a checklist  
<strong>\<ErCiccione\[m\]\></strong> We don't necessarely have to decide everything now, but wpuld be good to start  
<strong>\<sarang\></strong> Where assignments can be made for who is responsible, and when, etc.  
\<ErCiccione\[m\] "Alright. So, let's start talking"\> I have a WIP checklist I can share if you'd like.  
<strong>\<sarang\></strong> and hopefully avoid a lot of the small errors and problems that happen from time to time  
<strong>\<sarang\></strong> e.g. "the hashes don't match" etc.  
<strong>\<sethsimmons\></strong> And I'm happy to own some of the administrative tasks (contacting entities, etc.)  
<strong>\<rbrunner\></strong> Didn't fluffypony hand over something a while ago?  
<strong>\<ErCiccione\[m\]\></strong> sethsimmons: yes please we can then integrate it with some that are already around (fluffypony has one)  
<strong>\<sarang\></strong> rbrunner: he had a few things, yes  
<strong>\<sarang\></strong> Having an ongoing list would be great, and any issues that arise can be added to avoid in future releases  
<strong>\<sethsimmons\></strong> Let me post to a pastebin site  
<strong>\<sethsimmons\></strong> Copy paste will end poorly for you IRCers  
<strong>\<sarang\></strong> yeahhhhh  
<strong>\<sethsimmons\></strong> <https://paste.centos.org/view/84f18a65>  
<strong>\<sethsimmons\></strong> Initial list  
<strong>\<sethsimmons\></strong> Very WIP  
<strong>\<hyc\></strong> hmmm. Can post an instance of the checklist for each release  
<strong>\<hyc\></strong> on gitlab  
<strong>\<sethsimmons\></strong> I'm sure I have some steps out of order etc  
<strong>\<hyc\></strong> and make each point an unresolved thread  
\<hyc "on gitlab"\> Yeah that would be the intent  
<strong>\<hyc\></strong> and then resolve them as they are taken care of  
<strong>\<sethsimmons\></strong> Host it in an issue perhaps with MD checklist  
<strong>\<sarang\></strong> something something gantt chart  
<strong>\<sethsimmons\></strong> \*meta issue  
<strong>\<rbrunner\></strong> Soon we will end up on JIRA  
<strong>\<sethsimmons\></strong> I'm a JIRA admin dont tempt me  
<strong>\<hyc\></strong> JIRA - where software projects go to die  
<strong>\<sethsimmons\></strong> :P  
<strong>\<sarang\></strong> GitHub supports basic kanban boards  
<strong>\<ErCiccione\[m\]\></strong> I would say a basic kanban on github would do it. We could link issues to it and assign issues to prople  
<strong>\<sethsimmons\></strong> Should I open a meta issue to work through the creation of the checklist?  
<strong>\<sethsimmons\></strong> So we can have discussion/updates/etc.  
<strong>\<rbrunner\></strong> Sounds good  
<strong>\<sarang\></strong> Ah, a checklist checklist  
<strong>\<sethsimmons\></strong> XD  
<strong>\<sethsimmons\></strong> We've gone too deep  
<strong>\<ErCiccione\[m\]\></strong> Lol, but i do think would be useful  
<strong>\<sethsimmons\></strong> Any initial feedback on the first stab at the list?  
<strong>\<sgp\_\></strong> I have a self-hosted Wekan available (Trello clone)  
<strong>\<sethsimmons\></strong> If not I'll open the issue now and we can iterate as needed.  
<strong>\<sarang\></strong> Ledger/Trezor coding is a bit more abstract  
<strong>\<sarang\></strong> Unless you mean "on the Monero codebase"  
<strong>\<ErCiccione\[m\]\></strong> sgp\_: i would keep it simple and just create one on github. Also much more visible  
<strong>\<sarang\></strong> e.g. there's Ledger-specific code in Monero  
<strong>\<sarang\></strong> as a device option  
<strong>\<sethsimmons\></strong> I'll break that into our end and their end  
<strong>\<sethsimmons\></strong> \< <https://matrix.org/\_matrix/media/r0/download/matrix.org/ioQposdWvgLsHrglHKedyYMn> \>  
<strong>\<sethsimmons\></strong> Oof that didn't paste well  
<strong>\<sethsimmons\></strong> <https://paste.centos.org/view/29c74c53> \<- Better?  
<strong>\<sarang\></strong> Wallets should be informed as early as possible IMO  
<strong>\<sarang\></strong> As should exchanges  
<strong>\<sethsimmons\></strong> Right after fork height, or tagging?  
<strong>\<sarang\></strong> Seems that exchanges operate at the speed of a glacier as it is  
<strong>\<sarang\></strong> I'd say right at fork height, so they can plan for it  
<strong>\<sethsimmons\></strong> done.  
<strong>\<sarang\></strong> Even if they don't start working right away, then they at least know when to expect the release and the upgrade  
<strong>\<sethsimmons\></strong> Any last updates? Don't wanna derail this meeting too much with the first take on it.  
<strong>\<ErCiccione\[m\]\></strong> Alright. I would say we can conclude the meeting  
<strong>\<ErCiccione\[m\]\></strong> The discussion about the checklist can continue after or directly on the meta issue  
<strong>\<sarang\></strong> OK, what are action items on this?  
<strong>\<sarang\></strong> I'm going to contact Trezor and Ledger folks ASAP with these dates  
<strong>\<ErCiccione\[m\]\></strong> Nope, we are done.  
<strong>\<ErCiccione\[m\]\></strong> Thanks everybody for participating. You are free to go back to your sundays :)
