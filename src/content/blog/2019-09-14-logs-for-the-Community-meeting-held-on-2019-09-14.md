---
title: Logs for the Community Meeting Held on 2019-09-14
summary: Community highlights, CCS updates, Workgroup report, and miscellaneous
tags: [dev diaries, crypto]
author: el00ruobuob / SamsungGalaxyPlayer
---

# Logs

<strong>\<sgp\_\></strong> 0. Introduction  
<strong>\<sgp\_\></strong> We would like to welcome everyone to this Monero Community Workgroup Meeting\!  
<strong>\<sgp\_\></strong> Link to agenda on GitHub: <https://github.com/monero-project/meta/issues/391>  
<strong>\<rehrar\></strong> I will be in and out  
<strong>\<sgp\_\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community, including other Monero workgroups. We use meetings to encourage the community to share ideas and provide support.  
<strong>\<sgp\_\></strong> 1. Greetings  
<strong>\<sgp\_\></strong> do we have more than 3 people today?  
<strong>\<dginovker\></strong> Heylo  
<strong>\<needmonero90\></strong> Hey  
<strong>\<sgp\_\></strong> welcome everyone  
<strong>\<sgp\_\></strong> 2. Community highlights  
<strong>\<sgp\_\></strong> See Monero weekly highlights at <https://revuo-monero.com/>  
<strong>\<sgp\_\></strong> notably: many updates to the website <https://www.reddit.com/r/Monero/comments/d35ift/getmoneroorg\_updated\_updated\_guides\_new/>  
<strong>\<monerobux\></strong> \[REDDIT\] Getmonero.org updated: Updated guides, new "Announcements" section, some consensus changes, meeting logs and more (self.Monero) \| 72 points (93.0%) \| 12 comments \| Posted by ErCiccione \| Created at 2019-09-12 - 09:44:01  
<strong>\<sgp\_\></strong> also Daniel Kim, PhD, MBA gave the opening keynote at Monero DefCon 27 Village - watch his presentation “Foundations of Digital Money” on YouTube: <https://youtu.be/r-FkL5eXam8>  
<strong>\<sgp\_\></strong> Does anyone have community (non-workgroup) updates to share?  
<strong>\<dginovker\></strong> Been working on the MoneroTipsBot  
<strong>\<dginovker\></strong> It's working now, redesigned the security, but want to get a few more UX changes out  
<strong>\<sgp\_\></strong> cool  
<strong>\<el00ruobuob\_\[m\]\></strong> Hi\!  
<strong>\<sgp\_\></strong> cool  
<strong>\<sgp\_\></strong> hello  
<strong>\<dginovker\></strong> Also fyi the bug was multiple processes talking to the same port :\<  
<strong>\<dginovker\></strong> Don't do that, make sure your RPCs exit correctly.  
<strong>\<sgp\_\></strong> 3. CCS updates  
<strong>\<needmonero90\></strong> Subreddit mods modified rule 6 from a vague rule about downvotes to needing service operators to disclose  
<strong>\<needmonero90\></strong> Oh  
<strong>\<sgp\_\></strong> needmonero90: I see, it already has impacted some advertising posts  
<strong>\<needmonero90\></strong> We'll see how it turns out  
<strong>\<sgp\_\></strong> There is a partially-filled CCS proposal I want to mention for completeness, but we do not need to discuss it in my opinion since it is incomplete: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/97>  
<strong>\<sgp\_\></strong> on a related payment gateway note, there were recent updates to btcpayserver for monero  
<strong>\<sgp\_\></strong> none live yet, but work is ongoing :)  
<strong>\<dginovker\></strong> Just used btcpayserver for the first time today. It's very good :O  
<strong>\<sgp\_\></strong> i was going to use it to make a donation from monerujo, but I'm in the US so you know how that turned out....  
<strong>\<sgp\_\></strong> can't use xmr.to  
<strong>\<sgp\_\></strong> anyway, other CCS stuff  
<strong>\<sgp\_\></strong> Funding required:  
<strong>\<sgp\_\></strong> New Localization platform: Weblate (6.5/11 XMR): <https://ccs.getmonero.org/proposals/ErCiccione-weblate.html>  
<strong>\<sgp\_\></strong> Sarang: research funding for 2019 Q4 (4.05/417 XMR): <https://ccs.getmonero.org/proposals/sarang-2019-q4.html>  
<strong>\<sgp\_\></strong> Does anyone else have a CCS update, or comments about any of these CCS proposals?  
<strong>\<rehrar\></strong> fund\!  
<strong>\<rehrar\></strong> next  
<strong>\<rehrar\></strong> ?  
<strong>\<sgp\_\></strong> looks like ti  
<strong>\<sgp\_\></strong> \*it  
<strong>\<sgp\_\></strong> 4. Workgroup report  
<strong>\<sgp\_\></strong> a. Daemon/CLI workgroup  
<strong>\<sgp\_\></strong> There were some discussions about how to handle lightweight server code. Users should ideally be able to connect to their own lightweight server for efficiency  
<strong>\<sgp\_\></strong> are others aware of large discussions?  
<strong>\<sgp\_\></strong> ok, we can move on then  
<strong>\<sgp\_\></strong> b. Localization workgroup  
<strong>\<rehrar\></strong> Minecraft discussion  
<strong>\<rehrar\></strong> oh  
<strong>\<needmonero90\></strong> Lol  
<strong>\<sgp\_\></strong> The Chinese Mastering Monero translation discussion is ongoing but making good progress. I expect that a free and print version will be available soon  
<strong>\<sgp\_\></strong> ErCiccione has been working on the new Weblate translation platform  
<strong>\<sgp\_\></strong> unless he wants to chime in with more, I'll continue on  
<strong>\<sgp\_\></strong> is dsc\_ here and can talk about the GUI?  
<strong>\<dsc\_\></strong> I'm here, can't talk about the GUI  
<strong>\<dsc\_\></strong> As I've only been working on i2p  
<strong>\<dsc\_\></strong> not sure when fluffy is building  
<strong>\<sgp\_\></strong> how is progress coming along there? what's the most difficult part?  
<strong>\<kinghat\></strong> pretty impressive we cant get updated gooeys built  
<strong>\<dsc\_\></strong> most difficult part for me is figuring out with -dev how to handle seed nodes :D  
<strong>\<dsc\_\></strong> But I think we came to a solution  
<strong>\<sgp\_\></strong> can you summarize it? I missed that discussion and I'm interested  
<strong>\<dsc\_\></strong> We need i2p seed nodes (mipseeds)  
<strong>\<dsc\_\></strong> else peers cant find eachother whilst using i2p  
<strong>\<dsc\_\></strong> since inter-network peer exchange is not taking place  
<strong>\<dsc\_\></strong> not sure how to best summarize it, it's a complicated subject  
<strong>\<sgp\_\></strong> it's cool though  
<strong>\<dsc\_\></strong> we'll end up hosting some i2p nodes ourselves :P (me knaccc jtgrassie)  
<strong>\<sgp\_\></strong> cool  
<strong>\<sgp\_\></strong> any other gui updates/questions?  
<strong>\<dsc\_\></strong> Which means we hardcode some i2p nodes inside GUI  
<strong>\<dsc\_\></strong> yes  
<strong>\<dsc\_\></strong> I have 2 months left on my CCS  
<strong>\<kinghat\></strong> v0.14.1.1 and v0.14.1.2 were tagged july 17 and 23.  
<strong>\<dsc\_\></strong> ill be picking up some easier stuff after this, design proposals etc  
<strong>\<dsc\_\></strong> kinghat: Yes, sucks.  
<strong>\<dginovker\></strong> Can we get someone else to run the builds?  
<strong>\<kinghat\></strong> you can get unofficial builds from the build bots or build yourself. only one can release official builds afaik.  
<strong>\<dginovker\></strong> Right, but I mean could we delegate the task of making official builds to someone else?  
<strong>\<el00ruobuob\_\[m\]\></strong> Or better, to a group of people, with a new gpg key  
<strong>\<dginovker\></strong> As long as it's done with reproducable builds, I don't see a problem with that.  
<strong>\<kinghat\></strong> no idea about that. repro builds for gooey are a thing but not sure where they at. probably wont be here for the HF, though.  
<strong>\<el00ruobuob\_\[m\]\></strong> IMO, all the core team should have a gpg key issued to <core@getmonero.org>, and should be able to release official builds on the website  
<strong>\<kinghat\></strong> tbh i dont know why more ppl arent talking about it. its kind of a bottleneck.  
<strong>\<dsc\_\></strong> I'm most interested in a release right now because of the Tails support I've coded  
<strong>\<dsc\_\></strong> granted, people who really want that feature will compile themselves  
<strong>\<xmrscott\[m\]\></strong> I agree, so long as it's repducible, it shouldn't be an issue if it's signed by someone on the core team  
<strong>\<xmrscott\[m\]\></strong> We really shouldn't have single points of failure anyways to begin with  
<strong>\<el00ruobuob\_\[m\]\></strong> +1  
<strong>\<dsc\_\></strong> the nature of Monero is such that you can decide to make your own GUI releases  
<strong>\<dsc\_\></strong> pack them, distribute them  
<strong>\<dsc\_\></strong> if you are trusted in the community you'll even get some downloads :)  
<strong>\<dsc\_\></strong> Just mentioning it as an option  
<strong>\<dginovker\></strong> I'  
<strong>\<dginovker\></strong> I'd rather keep it simple and have it be on getmonero.org/downloads  
<strong>\<xmrscott\[m\]\></strong> Yes, but exchanges, etc may not download unless it's signed by someone from core  
<strong>\<sgp\_\></strong> xmrscott\[m\]: doesn't really apply to the GUI  
<strong>\<xmrscott\[m\]\></strong> Ah, trues  
<strong>\<sgp\_\></strong> that's a horrifying thought though :)  
<strong>\<sgp\_\></strong> but indeed, waiting 2 months for builds isn't ideal  
<strong>\<kinghat\></strong> still sucks. ppl complain about usability of xmr, we get crackerjack gooey team together and we cant even get releases out.  
<strong>\<xmrscott\[m\]\></strong> Agreed, releases really shouldn't be held because out on vacation, etc by a single person, however awesome they may be  
<strong>\<dEBRUYNE\></strong> Lol, it's not due to vacation  
<strong>\<sgp\_\></strong> There are many things related to releases that need improving. Would it be useful to schedule a meeting related to just this? Or this + planning?  
<strong>\<kinghat\></strong> anyways ill step off the milk crate.  
<strong>\<dginovker\></strong> Yes please  
<strong>\<dginovker\></strong> I think it's due some attention  
<strong>\<dEBRUYNE\></strong> Meeting would be kind of useless  
<strong>\<kinghat\></strong> probably. the cli guys seem like they are on the ball for the HF if anyone is following that.  
<strong>\<sgp\_\></strong> I think it could be useful, even if only to come up with a wish list  
<strong>\<dEBRUYNE\></strong> There's a reason this build is delayed, that's all I can say. Going forward we'll be seeking a backup builder  
<strong>\<dsc\_\></strong> While releases are nice, I see it more as a convience feature :P Because you are too lazy\! You can compile yourself\!  
<strong>\<dEBRUYNE\></strong> kinghat: Are you implying the GUI team is not?  
<strong>\<rehrar\></strong> tagging is still delayed many times  
<strong>\<dEBRUYNE\></strong> rehrar: can you elaborate?  
<strong>\<rehrar\></strong> well, the builds aren't the only thing pony does  
<strong>\<rehrar\></strong> he also does the tag no?  
<strong>\<sgp\_\></strong> I'll explore what a meeting could look like. Maybe it's creating a wish-list, seeing how many of these goals are met for sept/oct, then building action plans for the most important ones  
<strong>\<rehrar\></strong> and if he's gone, that has also been delayed in the past  
<strong>\<kinghat\></strong> dEBRUYNE: not in the slightest. was saying they are awesome and have held up their proverbial end of the bargain.  
<strong>\<dEBRUYNE\></strong> rehrar: luigi can set tags if needed  
<strong>\<dEBRUYNE\></strong> He normally does for the GUI  
<strong>\<kinghat\></strong> dEBRUYNE: i should have been fair and added that with previous gooey delays there was some underlying issue. 2 months though?  
<strong>\<dEBRUYNE\></strong> \<dEBRUYNE\> There's a reason this build is delayed, that's all I can say. Going forward we'll be seeking a backup builder  
<strong>\<rehrar\></strong> oko  
<strong>\<kinghat\></strong> i read im just life lagging atm  
<strong>\<sgp\_\></strong> well as long as we all agree the status quo is unacceptable, we have some reason to work towards something better  
<strong>\<sgp\_\></strong> with any luck I'll get a copy of my upgrade cycle defcon talk recording later this month  
<strong>\<dEBRUYNE\></strong> What we need is a backup builder in case fluffypony is unavailable  
<strong>\<dEBRUYNE\></strong> for the GUI that is  
<strong>\<dEBRUYNE\></strong> At least until we have deterministic builds  
<strong>\<dEBRUYNE\></strong> for the CLI there is no build issue, as those are already built deterministically  
<strong>\<rehrar\></strong> is deterministic builds a one and done?  
<strong>\<sgp\_\></strong> we'll see how this new upgrade goes  
<strong>\<xmrscott\[m\]\></strong> Out of curiosity how close is the GUI to getting deterministic builds?  
<strong>\<kinghat\></strong> until you add extras like i2pz and such.  
<strong>\<dEBRUYNE\></strong> xmrscott\[m\]: Probably still quite some time out  
<strong>\<sgp\_\></strong> i2p-zero has reproduceable builds luckily (experimental)  
<strong>\<sgp\_\></strong> let me get part d) of updates out, then we can be in open ideas  
<strong>\<sgp\_\></strong> d. Monero Research Lab  
<strong>\<sgp\_\></strong> Sarang opened his most recent funding proposal. Surae Noether published his monthly update. <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/89#note\_7255>  
<strong>\<sgp\_\></strong> we should see more work from surae since he is back from vacation now  
<strong>\<sgp\_\></strong> with any luck, another episode of breaking monero if we get our acts together  
<strong>\<sgp\_\></strong> 5. Open ideas time  
<strong>\<sgp\_\></strong> It’s open ideas time\! Feel free to propose your ideas to this discussion group, and feel free to comment on others’ ideas. If you disagree with the idea, please reply with constructive criticism. Thank you\!  
<strong>\<xmrscott\[m\]\></strong> Rebranding of "GUI" to something else: <https://github.com/monero-project/meta/issues/384>  
<strong>\<rehrar\></strong> yes  
<strong>\<xmrscott\[m\]\></strong> This was discussed for about an hour roughly a month ago, the issue contains a rough form of going about making that happen  
<strong>\<sgp\_\></strong> blockfolio could be used for unofficial polling, but we need a selection of names first for people to choose from  
<strong>\<msvb-mob\></strong> Does anyone have questions about Monero Hardware activities?  
<strong>\<msvb-mob\></strong> I missed putting the section in the agenda.  
<strong>\<sgp\_\></strong> msvb-mob: I have a million questions but not much time. Would you consider making a Reddit update explaining what you did for Defcon and what your next steps are?  
<strong>\<msvb-mob\></strong> There are no reddit posts to update, but I'm hoping to clean up the repositories, merge code, and make the already published sources more accessible.  
<strong>\<dginovker\></strong> xmrscott, I would rather tuck away the CLI tools more and just call the GUI "The" official wallet  
<strong>\<msvb-mob\></strong> Let's try for a real section in the next meeting.  
<strong>\<msvb-mob\></strong> sgp: I'll put the time for distributing more information into the location pointed to by the QR code of the Defcon village badges.  
<strong>\<sgp\_\></strong> I can't think of any good names. Maybe start with Twitter and Reddit open comments?  
<strong>\<el00ruobuob\_\[m\]\></strong> biletujo  
<strong>\<el00ruobuob\_\[m\]\></strong> esperanto for wallet  
<strong>\<xmrscott\[m\]\></strong> Well the thing is I want to make sure the process is largely sound, and people are in agreement here, so I don't get any backlash if I move on process  
<strong>\<sgp\_\></strong> el00ruobuob\_\[m\]: I kindly disagree with that name, too hard to spell :)  
<strong>\<nioc\></strong> please no esperanto as nobody can pronounce those words  
<strong>\<msvb-mob\></strong> xmrscott: Good luck with choosing a good name, that's quite difficult.  
<strong>\<el00ruobuob\_\[m\]\></strong> :(  
<strong>\<sgp\_\></strong> xmrscott\[m\]: thanks for sharing again, I also think esperanto needs to be considered extremely carefully  
<strong>\<xmrscott\[m\]\></strong> Honestly, I'll probably have to highlight it in a -dev meeting as well as that's where a good number of stakeholders are that don't attend -community meetings  
<strong>\<sgp\_\></strong> at some point yes, but I still think an open poll for ideas is useful now  
<strong>\<sgp\_\></strong> thanks for keeping this initiative alive  
<strong>\<xmrscott\[m\]\></strong> Sure  
<strong>\<dginovker\></strong> This might be more suitable for a research meeting, but I was talking to an IOTA guy and they were saying they had QC resistance through Lamport signatures. Does anyone have thoughts on this? <https://crypto.stackexchange.com/questions/8931/quantum-resistance-of-lamport-signatures>  
<strong>\<sgp\_\></strong> definitely seems like an MRL open ideas question dginovker :)  
<strong>\<sgp\_\></strong> this was merged during the meeting btw: <https://github.com/monero-project/monero-gui/pull/2370>  
<strong>\<sgp\_\></strong> 6. Confirm next meeting date/time  
<strong>\<sgp\_\></strong> The next community meeting will be in 2 weeks on 28 September at 17:00 UTC. The next Coffee Chat will be on 21 September at 16:00 UTC.  
<strong>\<sgp\_\></strong> 7. Conclusion  
<strong>\<sgp\_\></strong> That’s all\! Thanks for attending this Monero Community meeting, and we hope to see you on r/MoneroCommunity and \#monero-community. Take care, and know that change starts with YOU.  
<strong>\<sgp\_\></strong> As I mentioned, I'll look for a time to schedule an upgrade process meeting  
<strong>\<msvb-mob\></strong> sgp: Good meeting, thanks.  
<strong>\<el00ruobuob\_\[m\]\></strong> thanks, bye\!
