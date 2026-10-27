---
title: Logs for the Community Meeting Held on 2019-08-31
summary: Community highlights, CCS updates, Workgroup report, Action Items, and miscellaneous
tags: [dev diaries, crypto]
author: el00ruobuob / SamsungGalaxyPlayer
---

# Logs

<strong>\<sgp\_\></strong> 0. Introduction  
<strong>\<sgp\_\></strong> We would like to welcome everyone to this Monero Community Workgroup Meeting\!  
<strong>\<sgp\_\></strong> Link to agenda on GitHub: <https://github.com/monero-project/meta/issues/387>  
<strong>\<sgp\_\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community, including other Monero workgroups. We use meetings to encourage the community to share ideas and provide support.  
<strong>\<sgp\_\></strong> 1. Greetings  
<strong>\<ErCiccione\[m\]\></strong> Hi folks  
<strong>\<xmrscott\[m\]\></strong> Hola  
<strong>\<sgp\_\></strong> thanks for joining  
<strong>\<sgp\_\></strong> 2. Community highlights  
<strong>\<sgp\_\></strong> See Monero weekly highlights at <https://revuo-monero.com/>  
<strong>\<sgp\_\></strong> I was mostly off this week at the BTC2019 conference. I spoke about the dangers of transparency and the need for mandatory privacy in decentralized cryptocurrencies. I think it went well, and I can request a copy of my video recordings  
<strong>\<sgp\_\></strong> I used an activity which went quite well:  
<strong>\<sgp\_\></strong> I gave each person a notecard, which sorta represented an output. Then I asked people to trade cards, writing a record of the "transactions" on the card. Then I asked for a volunteer to be "suspicious" and finally debriefed by asking who accepted the "tainted" cards  
<strong>\<sgp\_\></strong> You should be able to see how it went in the recording, which I will hopefully receive soon  
<strong>\<sgp\_\></strong> Does anyone have community (non-workgroup) updates to share?  
<strong>\<DiegorehrarSalaz\></strong> Sorry. IRC issues. Matrix coming through?  
<strong>\<ErCiccione\></strong> Somebody is finally working on an integration Bisq-Monero, should be ready in some weeks according to the guy. See <https://github.com/bisq-network/proposals/issues/110>  
<strong>\<sgp\_\></strong> DiegorehrarSalaz: yes I see you now  
<strong>\<sgp\_\></strong> has niyid done any Monero work before?  
<strong>\<kinghat\></strong> yep, been following ErCiccione, very cool.  
<strong>\<ErCiccione\></strong> sgp\_: not that i'm aware of  
<strong>\<ErCiccione\></strong> kinghat: cool indeed. Monero and bisq are a perfect match  
<strong>\<sgp\_\></strong> Anything else worthy of mention before proceeding? Thanks for sharing  
<strong>\<sgp\_\></strong> 3. CCS updates  
<strong>\<sgp\_\></strong> ErCiccione posted a new idea:  
<strong>\<sgp\_\></strong> “ErCiccione: Installation and configuration of Weblate, the new localization platform” <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/94>  
<strong>\<sgp\_\></strong> thanks for being here ErCiccione to discuss it  
<strong>\<ErCiccione\></strong> :)  
<strong>\<ErCiccione\></strong> it's the proposal i made some time ago during a community meeting (after a dedicated localization workgroup meeting). Now weblate is basically ready. I only need a merged pr then we will start with the testing  
<strong>\<ErCiccione\></strong> within the localization workgroup, after that will be ready for anybody to use.  
<strong>\<ErCiccione\></strong> we will use it to translate next release, that's sure  
<strong>\<ErCiccione\></strong> (unless something crazy happens obviously :P)  
<strong>\<ErCiccione\></strong> thanks a lot to the people who already submitted their support. If anybody have questions i'm happy to answer  
<strong>\<endogenic\></strong> hey, all  
<strong>\<nioc\></strong> I have no been able to voice my support on GitLab for ErCiccione's proposal so I am doing so here  
<strong>\<ErCiccione\></strong> thank you nioc :)  
<strong>\<sgp\_\></strong> looks like a reasonable direction to me  
<strong>\<sgp\_\></strong> I'm going to take the silence as general agreement :)  
<strong>\<sgp\_\></strong> All other proposals previously in funding required are now funded :D  
<strong>\<sgp\_\></strong> Any final CCS comments before we move on to another section?  
<strong>\<sgp\_\></strong> 4. Workgroup report  
<strong>\<sgp\_\></strong> a. Daemon/CLI workgroup  
<strong>\<sgp\_\></strong> vtnerd’s Tor/i2p noise PR was recently merged  
<strong>\<sgp\_\></strong> moneromooo is back from vacation, and many miscellaneous bug fixes and improvements have been made since last meeting  
<strong>\<sgp\_\></strong> any other dev updates?  
<strong>\<sgp\_\></strong> b. Localization workgroup  
<strong>\<sgp\_\></strong> I received a full Chinese-translated copy of Mastering Monero. We’re discussing internally on how we would like to proceed with it. We want to make it available, but we need to work out the terms.  
<strong>\<sgp\_\></strong> We're considering options that will make PDFs available for free, but we need to determine how to handle the paid sales  
<strong>\<ErCiccione\></strong> isn't the book already available for free?  
<strong>\<sgp\_\></strong> We also need to review the translation to assess the quality  
<strong>\<sgp\_\></strong> ErCiccione: the English version is yes  
<strong>\<ErCiccione\></strong> what's the problem with publishing the translated version? the license allows it right?  
<strong>\<sgp\_\></strong> the license doesn't allow derivatives  
<strong>\<sgp\_\></strong> since we have the license, we can grant exceptions. but I just need to make sure everyone who contributed is ok with that  
<strong>\<ErCiccione\></strong> got it. I think make it freely translatable is extremely important  
<strong>\<ErCiccione\></strong> so, i hope it will happen :)  
<strong>\<sgp\_\></strong> we're working on it :)  
<strong>\<sgp\_\></strong> c. GUI workgroup  
<strong>\<sgp\_\></strong> dsc\_ has been working on the wallet i2p integration. It has been decided for now that the wallet will only support broadcasting transactions over i2p, not full sync. This will not impact most users' privacy a lot. The broadcast is the most important part  
<strong>\<sgp\_\></strong> dsc\_: does it allow i2p connections when using a remote node?  
<strong>\<sgp\_\></strong> I don't recall if a decision was made there yet  
<strong>\<ErCiccione\></strong> dsc\_ mentioned earlier he wouldn't make it for this meeting  
<strong>\<dEBRUYNE\></strong> dsc is afk as far as I know, but initially it will only be for tx broadcast as far as I can see  
<strong>\<sgp\_\></strong> oh yes, I'll need to follow up later  
<strong>\<sgp\_\></strong> beyond the networking settings, the design is being simplified, while adding new features including sending to multiple recipients  
<strong>\<sgp\_\></strong> d. Monero Research Lab  
<strong>\<dEBRUYNE\></strong> I think that is a good way to put it :)  
<strong>\<sgp\_\></strong> Sarang recently posted his monthly update: <https://www.reddit.com/r/Monero/comments/cx3gxp/august\_monthly\_report\_from\_sarang\_noether/>  
<strong>\<sgp\_\></strong> Surae has been working on matching and churning analysis. There has been some development progress. He finally has a working model to play with  
<strong>\<sgp\_\></strong> stop by the meeting Monday in \#monero-research-lab to learn more and ask questions  
<strong>\<sgp\_\></strong> before open ideas time, I want to test out a new section on the fly:  
<strong>\<sgp\_\></strong> 5. Action Items  
<strong>\<sgp\_\></strong> In this section, please outline some of the tasks you would like to work on before the next meeting  
<strong>\<sgp\_\></strong> Here's mine for example:  
<strong>\<sgp\_\></strong> 1. work on the networking press release explaining what happened to Kovri and documenting the progress of i2p-zero and tini2p 2. wrap up the StackExchange moderator election 3. publish the conference talk recording I gave yesterday  
<strong>\<sgp\_\></strong> would anyone else like to share?  
<strong>\<ErCiccione\></strong> cool  
<strong>\<ErCiccione\></strong> i'm making some very needed changes and updates to the website, don't know what will be new for next update but i will write a post on reddit.  
<strong>\<ErCiccione\></strong> some of the MR still need to be reviewed, so please take a look at <https://repo.getmonero.org/monero-project/monero-site/merge\_requests>  
<strong>\<ErCiccione\></strong> i also want to introduce a labelling system i had in mind to prioritize issues.  
<strong>\<ErCiccione\></strong> oh, since we are all here, would be ok for everybody if the "meeting logs" link of the website shows all meting log and not just dev meetings?  
<strong>\<sgp\_\></strong> imo yes  
<strong>\<sgp\_\></strong> come on, someone else has a list of things they want to work on :)  
<strong>\<DiegorehrarSalaz\></strong> Busy. Sorry. :(  
<strong>\<DiegorehrarSalaz\></strong> Will come back after meeting for logs and action item.  
<strong>\<sgp\_\></strong> ok, we have 2, maybe 3 people who work on stuff :p  
<strong>\<sgp\_\></strong> we can move on to open ideas time  
<strong>\<sgp\_\></strong> 6. Open ideas time  
<strong>\<sgp\_\></strong> It’s open ideas time\! Feel free to propose your ideas to this discussion group, and feel free to comment on others’ ideas. If you disagree with the idea, please reply with constructive criticism. Thank you\!  
<strong>\<sgp\_\></strong> I watched a talk about customer support at the conference, and it reminded me that we have been kinda trying to get one started for some time to supplement r/monerosupport and \#monero-support  
<strong>\<sgp\_\></strong> there are only 3 accounts in \#monero-support right now, which is a testament to the fact no one uses it  
<strong>\<sgp\_\></strong> having a training process for volunteers to provide live support could be a great way for people to get more involved. It would teach them the main pain points people have, and it would allow them to become even more familiar with Monero and how people use it  
<strong>\<sgp\_\></strong> the infrastructure is something I need to talk about with Diego on though, but I'd like to keep working on this project  
<strong>\<sgp\_\></strong> that's my idea. does anyone have others?  
<strong>\<midipoet\></strong> can we discuss konferenco 2019 (europe)?  
<strong>\<sgp\_\></strong> sure  
<strong>\<midipoet\></strong> i know there was discussions at DefCon surrounding holding it in conjunction with RIAT  
<strong>\<midipoet\></strong> but i haven't heard anything, and was wondering if anybody else had. As it is something that will need to start planning at some point  
<strong>\<needmonero90\></strong> Did I miss it  
<strong>\<sgp\_\></strong> I have not heard much in that regard. But I think that hosting it at a university makes a LOT of sense  
<strong>\<midipoet\></strong> was that their plan?  
<strong>\<sgp\_\></strong> I don't know  
<strong>\<midipoet\></strong> anyway, i wanted to just say (as i mentioned potentially helping with organisation) Provenance Events were asking if there was an update from the community with regards to what they thought  
<strong>\<sgp\_\></strong> keep it cheap  
<strong>\<midipoet\></strong> so i guess i wanted to say that the offer from Provenence is still there. but i thnk that RIAT is a better first option (provided they are still interested)  
<strong>\<needmonero90\></strong> OK I'm caught up  
<strong>\<needmonero90\></strong> Hey guys, sorry for the late entrance.  
<strong>\<midipoet\></strong> but as surae nor anybody from RIAT is here, i guess we can't discuss much right now  
<strong>\<needmonero90\></strong> Ive got a few items to discuss  
<strong>\<midipoet\></strong> that's all from me  
<strong>\<sgp\_\></strong> midipoet: want to make a list of student cryptocurrency clubs in Europe? They are our best "in" to the area and would know about planning, booking rooms, etc  
<strong>\<needmonero90\></strong> First would be the recent rule change on /r/Monero. Minor, but should be brought up here for logging purposes.  
<strong>\<needmonero90\></strong> Rule 6 was modified from disallowing downvotes, to making people self-identify if they have a conflict of interest on a particular product or service  
<strong>\<needmonero90\></strong> Additionally, I discovered new and old reddit have discrete rulesets, and the rules between the two versions were misordered. I imagine this led to some confusion. I fixed that up, the two should show the same rulesets now.  
<strong>\<needmonero90\></strong> Let's see what else  
<strong>\<needmonero90\></strong> Oh, the community has a minecraft server we've been hanging/chatting on. That's been cool. I think this is the right place to mention it.  
<strong>\<sgp\_\></strong> oh that's pretty cool. I only like to play in creative though :/  
<strong>\<sgp\_\></strong> I like building things  
<strong>\<needmonero90\></strong> I can get you all the materials you need :D  
<strong>\<needmonero90\></strong> I strip mine  
<strong>\<needmonero90\></strong> Anyways  
<strong>\<needmonero90\></strong> Uhm what else  
<strong>\<sgp\_\></strong> midipoet: here is an example for the US: <https://medium.com/michiganfintech/the-15-us-student-organizations-leading-fintech-movements-at-their-universities-fa2543cdcbd8>  
<strong>\<needmonero90\></strong> Oh, xmrtrader had a rule change too  
<strong>\<midipoet\></strong> sgp\_: yes, i think that a Uni might be a good idea. i don't think finding a host would be difficult, but i don't want to give go ahead for planning, if RIAT are serious about hosting, as they have their own venue  
<strong>\<needmonero90\></strong> Altcoin talk is no longer entirely banned  
<strong>\<needmonero90\></strong> You can speak about the top 20 now, just keep opinion out of it. Which has really been nice  
<strong>\<sgp\_\></strong> midipoet: their venue is a little small for a conference setting. Great for a meetup setting  
<strong>\<sgp\_\></strong> finally I can shill XLM  
<strong>\<midipoet\></strong> sgp\_: ah, i haven't seen it. but they said they had a newer space. but i may be incorrect about this  
<strong>\<dEBRUYNE\></strong> midipoet, sgp\_: RIAT is Vienna right?  
<strong>\<sgp\_\></strong> yes  
<strong>\<sgp\_\></strong> We're over, so leave any final thoughts that you would like added to the logs  
<strong>\<dEBRUYNE\></strong> As capital of Austria it should be relatively easy to access, might want to check in advance though  
<strong>\<dEBRUYNE\></strong> We preferably want a city that is directly accessible for Americans too  
<strong>\<needmonero90\></strong> sgp\_ thanks as always for hosting, you do a fantastic job.  
<strong>\<dEBRUYNE\></strong> +1  
<strong>\<dEBRUYNE\></strong> needmonero90: How many people are on the server?  
<strong>\<sgp\_\></strong> "for the record, I think needmonero90 is ugly" :)  
<strong>\<needmonero90\></strong> :'(  
<strong>\<midipoet\></strong> dEBRUYNE: yes, at the moment it seems to be either Vienna (RIAT), or Dublin (Provenance Events)  
<strong>\<needmonero90\></strong> 6 I think that you would know  
<strong>\<needmonero90\></strong> Me included  
<strong>\<needmonero90\></strong> So far  
<strong>\<needmonero90\></strong> Make that 7 when lh joins today  
<strong>\<dEBRUYNE\></strong> Vienna in summer should be decent weather too I guess  
<strong>\<dEBRUYNE\></strong> Perhaps we should add a location near the sea though? May be more attractive for people  
<strong>\<DiegorehrarSalaz\></strong> dEBRUYNE join us\!\!\!  
<strong>\<dEBRUYNE\> \<needmonero90\></strong> 6 I think that you would know \<= How would I know?  
<strong>\<dEBRUYNE\></strong> :D  
<strong>\<dEBRUYNE\></strong> :-P\*  
<strong>\<DiegorehrarSalaz\></strong> sgp too  
<strong>\<DiegorehrarSalaz\></strong> And midipoet  
<strong>\<DiegorehrarSalaz\></strong> And erciccione  
<strong>\<DiegorehrarSalaz\></strong> It's just to chill and have fun.  
<strong>\<DiegorehrarSalaz\></strong> Which we don't do enough of.  
<strong>\<midipoet\></strong> minecraft?  
<strong>\<DiegorehrarSalaz\></strong> Yes.  
<strong>\<needmonero90\></strong> Yes  
<strong>\<sgp\_\></strong> I will do some digging this afternoon to see if there are any universities that could be open to hosting  
<strong>\<ErCiccione\></strong> i would, but my laptop would fry  
<strong>\<midipoet\></strong> can you get mincraft for Linux?  
<strong>\<needmonero90\></strong> We have a server sgp  
<strong>\<needmonero90\></strong> Oh wait  
<strong>\<DiegorehrarSalaz\></strong> Dude, the graphics don't require much.  
<strong>\<needmonero90\></strong> Dero  
<strong>\<dEBRUYNE\></strong> sgp\_: I guess using an university should also significantly reduce the cost?  
<strong>\<needmonero90\></strong> It's literally blocks  
<strong>\<sgp\_\></strong> ErCiccione: I've played Minecraft on laptops \>5 years old  
<strong>\<DiegorehrarSalaz\></strong> midipoet, yes.  
<strong>\<midipoet\></strong> sgp\_: you can try - but i think the pressing issue is more who will organise - not where  
<strong>\<needmonero90\></strong> Dero = ignore me  
<strong>\<needmonero90\></strong> Screw autocorrect  
<strong>\<needmonero90\></strong> Idk how it got that out of what I typed  
<strong>\<sgp\_\></strong> 7. Confirm next meeting date/time  
<strong>\<sgp\_\></strong> The next community meeting will be in 2 weeks on 14 September at 17:00 UTC. The next Coffee Chat will be on 21 September at 16:00 UTC.  
<strong>\<ErCiccione\></strong> sgp\_: i have a much older 2nd hand lenovo :P  
<strong>\<sgp\_\></strong> 8. Conclusion  
<strong>\<sgp\_\></strong> That’s all\! Thanks for attending this Monero Community meeting, and we hope to see you on r/MoneroCommunity and \#monero-community. Take care, and know that change starts with YOU.
