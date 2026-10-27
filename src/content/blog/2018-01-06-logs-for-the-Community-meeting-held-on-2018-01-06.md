---
title: Logs for the Community Meeting Held on 2018-01-06
summary: Community highlights, Forum Funding System updates, RFC-HWALLET-1, Rehrar's Kovri proposal, Serhack's integrations, Fondajo, community materials, and miscellaneous
tags: [dev diaries, crypto]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<sgp\></strong> 0. Introduction  
<strong>\<sgp\></strong> We would like to welcome everyone to this Monero Community Meeting\!  
<strong>\<sgp\></strong> Link to agenda on GitHub: <https://github.com/monero-project/meta/issues/155>  
<strong>\<sgp\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community. We use meetings to encourage the community to share ideas and provide support.  
<strong>\<sgp\></strong> 1. Greetings  
<strong>\<rehrar\></strong> oy  
<strong>\<ErCiccione\></strong> Hi folks  
<strong>\<ordtrogen\></strong> yo  
<strong>\<xmrscott\[m\]\></strong> Salutations  
<strong>\<Xil3\></strong> hello  
<strong>\<sarang\></strong> yo  
<strong>\<msvb-lab\></strong> Oops, I was on the wrong channel. Hi folks.  
<strong>\<sgp\></strong> 2. Community highlights  
<strong>\<sgp\></strong> For a great weekly summary, please read the Monero Observer: <http://monero-observer.com/>  
<strong>\<sgp\></strong> 3. FFS updates  
<strong>\<sgp\></strong> There are several FFS updates.  
<strong>\<sgp\></strong> a. RFC-HWALLET-1 project progress  
<strong>\<sgp\></strong> @msvb-lab, your turn 😅  
<strong>\<ArticMine\></strong> Hi  
<strong>\<msvb-lab\></strong> Cool.  
<strong>\<msvb-lab\></strong> The Monero Hardware had a nice meeting yesterday of our own.  
<strong>\<msvb-lab\></strong> We chatted on \#monero-hardware for about an hour on seventeen topics.  
<strong>\<msvb-lab\></strong> Highlights of the past couple weeks are:  
<strong>\<msvb-lab\></strong> Our hardware wallet GitHub repository ‘sekura’ will be renamed to ‘kastelo’.  
<strong>\<msvb-lab\></strong> That’s with a ‘elo’ not ‘kastratelo’.  
<strong>\<msvb-lab\></strong> ;)  
<strong>\<msvb-lab\></strong> We delivered about thirty (?) holiday divident prototype boards.  
<strong>\<msvb-lab\></strong> Via post and face to face meetings, like for example at 34C3 in Leipzig.  
<strong>\<msvb-lab\></strong> …and are working on the next prototype(s) design now.  
<strong>\<msvb-lab\></strong> That’s about all, any questions?  
<strong>\<msvb-lab\></strong> A firmware effort is underway, I guess we’ll have a more unique device than planned.  
<strong>\<msvb-lab\></strong> There is a lot of interest in the group to attract more people that know cryptography and can code.  
<strong>\<msvb-lab\></strong> Volunteers?  
<strong>\<msvb-lab\></strong> Crickets.  
<strong>\<rehrar\></strong> I can neither code, nor know cryptography well  
<strong>\<msvb-lab\></strong> sgp: Next topic.  
<strong>\<sarang\></strong> MRL remains available with any questions that come up  
<strong>\<rehrar\></strong> but I’ll jump right on it  
<strong>\<msvb-lab\></strong> sarang: That’s excellent, very generous as usual of MRL.  
<strong>\<sgp\></strong> Thanks msvb-lab  
<strong>\<sgp\></strong> b. Monero Integrations  
<strong>\<sgp\></strong> Serhack and cryptochangements posted an update: <https://www.reddit.com/r/Monero/comments/7o3rx6/serhack_updates_for_the_ebook_and_integrations/>  
<strong>\<sgp\></strong> Do any of them want to speak about this now?  
<strong>\<cryptochangements\></strong> oh crap im late  
<strong>\<cryptochangements\></strong> is serhack here?  
<strong>\<rehrar\></strong> doesn’t seem so. It’s all you cryptochangements  
<strong>\<sgp\></strong> I haven’t seen him here today  
<strong>\<sgp\></strong> Is there anything you want to mention cryptochangements?  
<strong>\<cryptochangements\></strong> ok, pretty much all I have to say is that the opencart plugin, the third milestone, is being worked on and is on it’s way  
<strong>\<sgp\></strong> Great, thanks for your work  
<strong>\<cryptochangements\></strong> you can see the code here: <https://github.com/monero-integrations/monerocart>  
<strong>\<sgp\></strong> Anything else cryptochangements?  
<strong>\<cryptochangements\></strong> nope, that’s all  
<strong>\<sgp\></strong> c. Rehrar’s Kovri proposal  
<strong>\<sgp\></strong> Rehrar’s Kovri proposal has moved to funding required: <https://forum.getmonero.org/8/funding-required/89677/rehrar-s-2018-q1-kovri-proposal>  
<strong>\<sgp\></strong> Anything to add rehrar?  
<strong>\<rehrar\></strong> fudn it  
<strong>\<rehrar\></strong> \*fund  
<strong>\<rehrar\></strong> <em>bows</em> thank you  
<strong>\<rehrar\></strong> jk, thing is, I’m working on Kovri regardless, so work is not slowing in any capacity  
<strong>\<rehrar\></strong> even while this waits for funding  
<strong>\<sgp\></strong> Thanks rehrar. It means a lot for the project  
<strong>\<sgp\></strong> Does anyone else have a FFS update?  
<strong>\<ErCiccione\></strong> nothing from me but if anybody has question, here to answer about localizations  
<strong>\<sgp\></strong> I’ll proceed then onto the next topic  
<strong>\<ordtrogen\></strong> I have a comment on localization, when topic’s up  
<strong>\<ordtrogen\></strong> <em>the topic</em>  
<strong>\<sgp\></strong> @ordtrogen you can ask it now  
<strong>\<ErCiccione\></strong> sure, go ahead ordtrogen  
<strong>\<ordtrogen\></strong> (pasting some pre-written text …)  
<strong>\<ordtrogen\></strong> I’ve only recently gotten more involved in translation/localization but pretty quickly I have discovered a couple of issues with the localizable strings, both in the CLI and GUI project. So I think it needs some polishing to look proper. (I am filing issues as we speak) There also doesn’t seem to exist much in the way of help documentation. I know there is some texts on getmonero.org, but I’d argue there should fir  
comes with the installation, such as a man file for unix and maybe some other formats for Mac and Windows. Which makes me think we should spend a little more time on the “foundations” of the texts we write. Like improving the UI English. While @ercicciones work on the localization project obviously is fantastic, I’m thinking, what quality can the translations have unless the source (en) is correct?  
<strong>\<rehrar\></strong> Agree wholeheartedly.  
<strong>\<rehrar\></strong> As I work on the website here and there, most of the text is not written by me, except for the newer pages (and even that should be reviewed). Some of the copy does not read well, or is over flowery in some places, or other issues.  
<strong>\<ErCiccione\></strong> yes, a lot of good points. the source file has been polished not a month ago, but would be great to have a clean and reviewed text to work on  
<strong>\<sgp\></strong> I think most people agree documentation needs to be improved across the board  
<strong>\<ErCiccione\></strong> about documentation  
<strong>\<ordtrogen\></strong> I’m thinking a man file for monerod would be in order. Need not be too extensive  
<strong>\<ordtrogen\></strong> (linux)  
<strong>\<ordtrogen\></strong> And I’m not sure, what is displayed by $monerod —help is not localizable, right?  
<strong>\<ErCiccione\></strong> i’m working in creating a wiki with everything necessary for a translator, it can be found here <https://taiga.getmonero.org/project/erciccione-monero-localization/wiki/home> it need some improving, but following translators can take days some times, and i actually have no time, would be great to have some help on that side  
<strong>\<ErCiccione\></strong> @ordtrogen it is actually, you can find the references to the code in the .ts files  
<strong>\<ordtrogen\></strong> ok. I just wanted to bring up the issue. As soon as I have to write something, I will.  
<strong>\<ErCiccione\></strong> iirc a man file was partially done few days ago, but yes, there  
<strong>\<ordtrogen\></strong> Will try to finish the testing and issue reporting first  
<strong>\<ErCiccione\></strong> \* there is needing of a lot of clean documentation, thank you for bringing that up  
<strong>\<ordtrogen\></strong> Oh, a man file is somewhere in the repos?  
<strong>\<ordtrogen\></strong> CLI or GUI\`?  
<strong>\<dEBRUYNE\></strong> Just dropping this here: <https://www.reddit.com/r/Monero/comments/7nl38w/technical_documentation_for_monero/ds2nkfu/>  
<strong>\<ordtrogen\></strong> Oh, great  
<strong>\<ordtrogen\></strong> I don’t have time to follow r/monero too much  
<strong>\<ErCiccione\></strong> dEBRUYNE, uh that looks very good  
<strong>\<sgp\></strong> Anything else we need to discuss on this topic?  
<strong>\<dEBRUYNE\></strong> Perhaps reach out to the owner to collaborate  
<strong>\<ordtrogen\></strong> Oh, man, That site looks great\!  
<strong>\<sgp\></strong> Ok, I’m going to move on. Thanks @dEBRUYNE @ErCiccione  
<strong>\<sgp\></strong> 4. Fondajo  
<strong>\<sgp\></strong> After months of progress, I am pleased to announce that I am proceeding with a 501(c)3 nonprofit cryptocurrency foundation called “Fondajo”. I have a great workgroup of people who are helping organize all the documents.  
<strong>\<sgp\></strong> This cryptocurrency nonprofit will promote education, research, and development. One of its values will be to promote privacy projects. The foundation will still be completely separate from Monero.  
<strong>\<sgp\></strong> When the nonprofit is officially incorporated, I will hand over the responsibilities of this workgroup to rehrar. I’m sure that we can use some help from other members who have been active these past several months.  
<strong>\<sgp\></strong> To be clear, this is not a Monero-specific foundation, but it will support many of Monero’  
<strong>\<sgp\></strong> \*many of Monero’s projects  
<strong>\<ArticMine\></strong> This is a US base non profit?  
<strong>\<sgp\></strong> Yes, US-based  
<strong>\<sgp\></strong> Which will allow people in the US to make tax-deductible donations  
<strong>\<ordtrogen\></strong> TAlk about the name Fondajo  
<strong>\<ordtrogen\></strong> (now I see the meaning in espreanto)  
<strong>\<sgp\></strong> If you are interested in helping with the nonprofit, let me know in PM  
<strong>\<sarang\></strong> What are the practical types of projects/goals related to the mission?  
<strong>\<sarang\></strong> or some examples?  
<strong>\<sgp\></strong> Any published research in cryptocurrencies is fair game  
<strong>\<sgp\></strong> Educational outreach is prioritized for grants too  
<strong>\<sgp\></strong> I’m still seeing what can be done for development, but I’d like to support this as much as possible  
<strong>\<sarang\></strong> Nice, so it’d issue grants from its asset pool of donations?  
<strong>\<sgp\></strong> Exactly  
<strong>\<sarang\></strong> Excellent  
<strong>\<dEBRUYNE\></strong> As long as it doesn’t end up like the Bitcoin foundation lol  
<strong>\<sarang\></strong> I assume the nonprofit status might make it easier to help support students as well  
<strong>\<sgp\></strong> It will be very different from the Bitcoin Foundation, even by registration  
<strong>\<sgp\></strong> Bitcoin Foundation is not a 501(c)3  
<strong>\<dEBRUYNE\></strong> I am just talking about their endeavors etc.  
<strong>\<sgp\></strong> Since this is a 501(c)3, the focus will be entirely on education, research, and (hopefully) development  
<strong>\<cwcopz\></strong> “Fondajo” sounds like an intersting project. Is there more information available? Is there a official homepage?  
<strong>\<sgp\></strong> I think it will really help raise money for projects that can benefit Monero and other privacy projects  
<strong>\<sarang\></strong> I know suraeNoether has toyed around with the idea of a nonprofit too, so I’ll page him here  
<strong>\<rehrar\></strong> Privacy advocacy\!  
<strong>\<sgp\></strong> cwcopz I have the domain but haven’t made a website yet  
<strong>\<rehrar\></strong> Monero is just one tool in the opsec of a privacy focused person  
<strong>\<cwcopz\></strong> Is there a way to stay up to date? I would like to donate to this project as well.  
<strong>\<sgp\></strong> Any other questions?  
<strong>\<sgp\></strong> I want to assure everyone that Fondajo will remain completely separate from Monero itself  
<strong>\<ordtrogen\></strong> Did you get the .co domain?  
<strong>\<dEBRUYNE\></strong> Is anyone getting paid?  
<strong>\<sgp\></strong> @cwcopz I’ll put all major updates in /r/Monero and /r/MoneroCommunity  
<strong>\<cwcopz\></strong> Okay, thanks. Sounds promising\!  
<strong>\<sgp\></strong> @dEBRUYNE it’s likely there will be overhead for some positions, but I want to keep it minimal  
<strong>\<dEBRUYNE\></strong> I am personally not a fan of people getting paid in a nonprofit, it should be done altruistically  
<strong>\<sarang\></strong> I think it depends on the level of work. If it’s your full-time job, you should get compensated  
<strong>\<sarang\></strong> peeps gotta eat  
<strong>\<sgp\></strong> @dEBRUYNE it’s sometimes better to be able to pay people to allow them to spend all their time working on improving the cryptocurrency ecosystem  
<strong>\<rehrar\></strong> what if they are paid in love?  
<strong>\<sarang\></strong> Will my landlord accept love as rent?  
<strong>\<sarang\></strong> That might be illegal  
<strong>\<rehrar\></strong> well, as in crypto, consensus is mandatory  
<strong>\<rehrar\></strong> moving on :P  
<strong>\<ordtrogen\></strong> Can’t an organization be non-profit as a whole but still pay for services?  
<strong>\<sgp\></strong> Ok sarang, you’re up  
<strong>\<sarang\></strong> 501(c)(3) orgs can pay their staff  
<strong>\<sarang\></strong> I thought I’d mention one FFS that’s sorta kinda community related  
<strong>\<sarang\></strong> It was suggested that we send a couple of folks to some academic conferences for knowledge gains and community representation  
<strong>\<sarang\></strong> suraeNoether and I wish to attend the BPASE18 conference at Stanford later this month  
<strong>\<sarang\></strong> and suraeNoether plans to attend the RWC conference in Zurich with fluffypony  
<strong>\<sarang\></strong> So we have an open FFS for the usual expenses  
<strong>\<rehrar\></strong> 5 star hotel, caviar every night, the works  
<strong>\<sarang\></strong> I’m mainly looking for input from the group about how important y’all feel conferences are for the Monero group  
<strong>\<sarang\></strong> and if FFS should be the preferred way of sending folks to conferences that we agree are worthwhile  
<strong>\<dEBRUYNE\></strong> sgp, sarang: Let’s discuss that another time :P  
<strong>\<dEBRUYNE\></strong> sarang: conferences are one of the main ways to network  
<strong>\<sarang\></strong> OK, wasn’t sure if this was a good place for that discussion  
<strong>\<dEBRUYNE\></strong> As long as they aren’t detrimental for day-to-day work  
<strong>\<dEBRUYNE\></strong> i.e. it leaves no time to work on “normal” stuff  
<strong>\<rehrar\></strong> To answer the first question: extremely important  
<strong>\<rehrar\></strong> The Monero Project needs to be a part of a larger conversation  
<strong>\<sarang\></strong> dEBRUYNE: the conference schedules are usually pretty packed, but BPASE is only 3 days  
<strong>\<rehrar\></strong> a conversation about privacy, human rights, cryptography, and more  
<strong>\<rehrar\></strong> going to these conferences is a way for representatives of The Monero Project to be a part of that conversation  
<strong>\<rehrar\></strong> I think The Monero Project has a unique voice, and unique things to add to such conversations as well, and our perspective will be helpful  
<strong>\<ErCiccione\></strong> sarang: link of the FFS?  
<strong>\<sarang\></strong> OK thanks for this perspective  
<strong>\<rehrar\></strong> <https://forum.getmonero.org/8/funding-required/89695/funding-for-noether-brothers-to-attend-stanford-bpase18-conference>  
<strong>\<sarang\></strong> We used a single FFS but listed the separate costs for reference: <https://forum.getmonero.org/8/funding-required/89695/funding-for-noether-brothers-to-attend-stanford-bpase18-conference>  
<strong>\<ErCiccione\></strong> uw… double, nice. Thanks guys  
<strong>\<sarang\></strong> I agree with rehrar that this should be part of a larger discussion about our involvement in the broader academic community  
<strong>\<sarang\></strong> I recommend interested persons take a look at the conference schedules and programs. Lots of excellent talks  
<strong>\<sgp\></strong> Anything else sarang? I have no issue with this FFS proposal  
<strong>\<sarang\></strong> Nope, just wanted to open the broader conversation  
<strong>\<sarang\></strong> Appreciate the insights from all of you  
<strong>\<sgp\></strong> 5. Community materials  
<strong>\<sgp\></strong> This section of the meeting was inspired by this post: <https://www.reddit.com/r/Monero/comments/7obquf/wake_up_we_need_better_marketing_and_better/>  
<strong>\<sgp\></strong> Let’s discuss how the Monero community can better market itself to others and what materials could be beneficial to newcomers.  
<strong>\<sgp\></strong> Anyone want to begin?  
<strong>\<cryptochangements\></strong> yesterday i saw a youtube ad for Bitcoin. I think we need one for monero with fluffypony in a lambo  
<strong>\<cryptochangements\></strong> \\s  
<strong>\<ordtrogen\></strong> I keep seeing them for Dash\!\!\!  
<strong>\<ordtrogen\></strong> yuck  
<strong>\<Guest93332\></strong> I want to know why is this community not communicated more on the official channels? i only heard about it as an comment on an reddit thread? This here should be more public.  
<strong>\<sarang\></strong> I find it interesting to watch the top coins by cap… so many that seem to rely on marketing  
<strong>\<Guest93332\></strong> \*this community chat not ..  
<strong>\<sgp\></strong> @guest93332 this is a workgroup. You can see what it does in /r/MoneroCommunity  
<strong>\<rehrar\></strong> It’s on the Hangouts page and the Footer of the website also  
<strong>\<sgp\></strong> You’re right though that we should probably encourage more people in /r/Monero and elsewhere to participate  
<strong>\<Guest93332\></strong> yeah for example - it should be on r/monero  
<strong>\<rehrar\></strong> like…the Community meeting announcement should be on /r/monero?  
<strong>\<sgp\></strong> I still think the best marketing is good documentation and beginner resources  
<strong>\<sgp\></strong> At least for now  
<strong>\<cryptochangements\></strong> well as people have discussed before, if we are going to market monero it has to be based on education. not stupid hype  
<strong>\<rehrar\></strong> agree cryptochangements, but we all have to recognize one thing  
<strong>\<rehrar\></strong> we can’t tell anyone what to do, so if one person was to start a ‘hype’ focused marketing thing, we can’t stop them  
<strong>\<cryptochangements\></strong> fair enough  
<strong>\<rehrar\></strong> And the clock is ticking until some initiative-filled person will do it  
<strong>\<rehrar\></strong> so the best way to prevent it  
<strong>\<Guest93332\></strong> i have another question, for beginners it is very hard to find out about irc and that stuff. could the whole communication change from irc to discord or is it like monero is for the cryptogeeks?  
<strong>\<rehrar\></strong> is to get a marketing team together that will focus on education and awareness  
<strong>\<rehrar\></strong> that way, when said initiative-filled person comes in  
<strong>\<rehrar\></strong> we can funnel him into the already underway marketing effort  
<strong>\<rehrar\></strong> and his/her skills will be with the community  
<strong>\<rehrar\></strong> the longer we wait for some form of marketing workgroup, the more likely it is that somebody that doesn’t believe what we do about hype and education will start it  
<strong>\<msvb-lab\></strong> Guest93332: Discord would be nice to have. My impression is that the folks moderating the dozen or so current channels and bridges to channels aren’t able to keep up.  
<strong>\<cryptochangements\></strong> Guest93332: can this be discussed after the meeting in open discussion in a few minutes?  
<strong>\<msvb-lab\></strong> There may not be a volunteer to configure and moderate Discord.  
<strong>\<rehrar\></strong> Guest93332: we have slack and mattermost connections also  
<strong>\<rehrar\></strong> mattermost.getmonero.org  
<strong>\<Guest93332\></strong> ok  
<strong>\<ErCiccione\></strong> and riot/matrix  
<strong>\<rehrar\></strong> believe me, I’m not a geek. :P Which is why I worked on getting other non-IRC things up here also so people like me could participate  
<strong>\<cryptochangements\></strong> i remember a r/moneromarketing did exist at one point, but then turned into monerocommintu  
<strong>\<sgp\></strong> Formalizing an actual marketing campaign is a topic for another day, but how can we encourage people to make these helpful user guides, videos, infographics, etc?  
<strong>\<rehrar\></strong> I still own it cryptochangements  
<strong>\<cryptochangements\></strong> and then the marketing ideas all kinda got shunned  
<strong>\<sarang\></strong> There’s a saying that it’s orders of magnitude harder to refute BS than to spew it  
<strong>\<sarang\></strong> We’ll always have that working against us for hype  
<strong>\<rehrar\></strong> I think if we get some Monero merch  
<strong>\<rehrar\></strong> and have some giveaways based on competition of content creation  
<strong>\<rehrar\></strong> then that’d be a fun way to both engage the community, get some Monero marketing type merch out there, and incentivize quality content creation  
<strong>\<cryptochangements\></strong> sgp: i think we have to figure out what kind of marketing we want to encourage before we can start encouraging marketing at all  
<strong>\<cryptochangements\></strong> ooo good idea rehrar  
<strong>\<sgp\></strong> @rehrar I like that idea  
<strong>\<ErCiccione\></strong> I don’t know if i like it, it’s not ideal to compensate people for something they should do because they believe in it  
<strong>\<sgp\></strong> I think a Monero webcam cover is a good incentive. People seem to love them  
<strong>\<rehrar\></strong> ErCiccione this is indeed the balance of initiative-based projects  
<strong>\<rehrar\></strong> people with the most initiative will be (usually) people who believe in the project  
<strong>\<cwcopz\></strong> sgp Agree. Would buy one as well.  
<strong>\<rehrar\></strong> this will mean that the 98% who are on board for other reasons will rarely do something that requires their own initiative  
<strong>\<cryptochangements\></strong> ErCiccione a t-shirt or some webcam covers isnt like a fat cash prize. people who participate would still probably do it bc they like Monero. the incentives just kinda get the ball rolling and make it a little bit more fun  
<strong>\<rehrar\></strong> and make no mistake, while I do think Monero has a higher number of idealists, as the days pass, and more people join, Monero will be overrun by people who don’t see the vision  
<strong>\<cwcopz\></strong> I’ve created a homepage to show some monero artwork. Can I post the link? It is WIP and at the moment a little bit outdated.  
<strong>\<rehrar\></strong> in a sense, we have to woo those people to the vision. In part by being a friendly-community and making them want to stick and around and stay, and the more they stay, the more they listen, the more they listen, the more they learn  
<strong>\<sgp\></strong> Sure  
<strong>\<cwcopz\></strong> WIP <https://monero.gallery/>  
<strong>\<ErCiccione\></strong> cryptochangements: yes, in those terms sounds fair, but i don’t love it anyway :P  
<strong>\<rehrar\></strong> community engagement is the start of the process I just described  
<strong>\<cwcopz\></strong> Focus: Art, what is monero?, speading the word, privacy …  
<strong>\<cwcopz\></strong> Do you think it is worth to work on in the future?  
<strong>\<rehrar\></strong> <em>shrug</em> we never know what will grab the community  
<strong>\<ErCiccione\></strong> rehrar: yes, but i want to make sure we don’t push monero engagement giving for granted a future downfall of its community  
<strong>\<rehrar\></strong> I think it’d be a fun way for designers to hop on board, so why not cwcopz?  
<strong>\<sgp\></strong> @ErCiccione I obviously prefer if everyone does something for free, but if all they need is a free little piece of merch to contribute, it’s probably worth it  
<strong>\<cryptochangements\></strong> unfortunatly rehrar is right. with the huge price pumps most people are here for the money, not the ideals. but im gonna share a secret: I found monero bc it was easy to mine and i was gonna convert it all to BTC. but once i found out monero is way better than BTC i kept my monero and eventually got more involved in the community. Like rehrar said, you kinda gotta woo people over to the id  
<strong>\<ErCiccione\></strong> i agree @sgp i only want to avoid it becomes a strategy, when we can also make promotional video to ask people to contribute, hackatons and stuff like that  
<strong>\<rehrar\></strong> there are human elements to the Monero community, and I realize the ideal is that we won’t hvae to play to those human elements and the technology will speak for itself  
<strong>\<rehrar\></strong> this is honestly a kind of thinking that conveys a lack of understanding and appreciation for the intricacies of handling the social part of a project  
<strong>\<cwcopz\></strong> @rehrar I think the same. I am not a coder but possible a way to contribute to monero at all  
<strong>\<rehrar\></strong> many great projects break down for social reasons  
<strong>\<sgp\></strong> Does anyone else have marketing-specific discussion, or should I open it to the broader open ideas time?  
<strong>\<rehrar\></strong> we’ve kind of melded the two :P  
<strong>\<sgp\></strong> Ok, let’s continue with open ideas time  
<strong>\<sgp\></strong> What does everyone think of the Coffee Chats? We often have a hard time getting enough people to join  
<strong>\<cwcopz\></strong> Coffee Chats?  
<strong>\<cryptochangements\></strong> I think that it is an awesome idea. But I don’t think enough people know about them  
<strong>\<rehrar\></strong> these things start and gain momentum slowly  
<strong>\<sgp\></strong> <https://www.youtube.com/watch?v=EcKgnjqSXpA&list=PLsSYUeVwrHBnzudI3KSSW4aVa_4Ty1Kew>  
<strong>\<cryptochangements\></strong> they usually have great discussion, but have a turnout of like 60 viewers  
<strong>\<Guest93332\></strong> thats the problem. we need more commuication penetration in all activities  
<strong>\<rehrar\></strong> keep a schedule, and they will grow. imo, even if we help bring just one person closer to the vision, it was well worth it :D  
<strong>\<cwcopz\></strong> Thanks for the link. Didnt know that this exists.  
<strong>\<sgp\></strong> Since the next one is on the 20, how should I promote it differently to attract more viewers?  
<strong>\<cryptochangements\></strong> sgp: the coffechat seems like something r/cryptocurrency would go nuts over  
<strong>\<Guest93332\></strong> you should use all officials account with social media  
<strong>\<sarang\></strong> Remind me, are they advertised on places like r/monero or r/xmrtrader?  
<strong>\<sgp\></strong> I typically post on /r/monero yes  
<strong>\<sgp\></strong> I haven’t posted about it in /r/xmrtrader before  
<strong>\<ErCiccione\></strong> sgp: i think it needs some more scheduled advertising, like 24 hours earlier and then a couple of hours before starting. And a massive use of social accounts a couple of hours before the chat  
<strong>\<cryptochangements\></strong> Personally, i think the coffechats are something that should be advertised everywhere  
<strong>\<rehrar\></strong> sarang: you should join up on this one  
<strong>\<sgp\></strong> We had the most views when fluffypony posted it on his Twitter  
<strong>\<sarang\></strong> Sure, I’d be glad to  
<strong>\<Guest93332\></strong> or the official @monerocurrency account  
<strong>\<cryptochangements\></strong> who is in the lineup for this next one?  
<strong>\<sarang\></strong> Oh yeah, an fp twitter post would be great  
<strong>\<sgp\></strong> @cryptochangements any active community member who wants to participate can  
<strong>\<cryptochangements\></strong> ok cool  
<strong>\<rehrar\></strong> the more the better. We just hang out and be losers together  
<strong>\<cryptochangements\></strong> sounds lit 👍  
<strong>\<sgp\></strong> Ok, I’ll try to make sure the event has more 24 hr exposure  
<strong>\<Guest93332\></strong> who controls the official accounts? its all about being present and penetration. Especially in crypto - you have to be heard  
<strong>\<sgp\></strong> How much of the time should be dedicated to audience Q&amp;A?  
<strong>\<ordtrogen\></strong> What about inviting a known guest  
<strong>\<cryptochangements\></strong> tbh i think it should just depend on audience turnout/how many questions people actually have  
<strong>\<ordtrogen\></strong> Like brighton36  
<strong>\<sgp\></strong> @ordtrogen I’m open to that idea  
<strong>\<ordtrogen\></strong> Or someone else favorable to our cause  
<strong>\<rehrar\></strong> alright, I gotta split  
<strong>\<rehrar\></strong> talk to you guys later :)  
<strong>\<ErCiccione\></strong> @sgp: i’d say as much as it takes, once you understand the discussion is not “spicy” anymore. I also like @ordtrogen idea, but i think sarang’s presence will catch a lot of interest, if advertised before  
<strong>\<sarang\></strong> aw shucks  
<strong>\<sarang\></strong> I’m just a simple guy with a simple message  
<strong>\<sarang\></strong> <https://media.giphy.com/media/A7WK7FddTxKfu/giphy.gif>  
<strong>\<ordtrogen\></strong> my idea came just now. no thinking thru  
<strong>\<sgp\></strong> Thanks for the input everyone. I’d like to leverage this as much as possible  
<strong>\<ordtrogen\></strong> but maybe that person would bring part of her/his audience along?  
<strong>\<sgp\></strong> @ordtrogen let’s come up with a list of possible people after the meeting  
<strong>\<ordtrogen\></strong> ok  
<strong>\<sgp\></strong> I imagine they would bring some of their audience on, yes  
<strong>\<ErCiccione\></strong> sarang: you are a monero research lab master\! deal with it\! lol for the gif  
<strong>\<sgp\></strong> 7. Confirm next meeting date/time  
<strong>\<sgp\></strong> The next community meeting will be two weeks from today on 20 January. The next Coffee Chat will be next week on 13 January: <https://github.com/monero-project/meta/issues/156>  
<strong>\<sgp\></strong> 8. Conclusion  
<strong>\<sgp\></strong> That’s all\! Thanks for attending this Monero Community meeting, and we hope to see you on /r/MoneroCommunity and \#monero-community. Take care, and know that change starts with YOU.  
<strong>\<sgp\></strong> I hope eveyone was ok with a longer meeting this time. People were open to it in previous meetings  
<strong>\<sarang\></strong> sgp: please send me a reminder for the chat =p
