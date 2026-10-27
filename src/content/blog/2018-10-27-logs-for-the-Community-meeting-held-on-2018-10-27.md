---
title: Logs for the Community Meeting Held on 2018-10-27
summary: Community highlights, Forum Funding System updates, Workgroup report, and miscellaneous
tags: [dev diaries, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<rehrar\></strong> 0. Introduction  
<strong>\<rehrar\></strong> We would like to welcome everyone to this Monero Community Meeting\!  
<strong>\<rehrar\></strong> ink to agenda on GitHub: <https://github.com/monero-project/meta/issues/286>  
<strong>\<rehrar\></strong> \*Link  
<strong>\<rehrar\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community, including other Monero workgroups. We use meetings to encourage the community to share ideas and provide support. Stay up to date with the latest events by subscribing to this calendar:  
<strong><rehrar></strong> <https://xmr.ncrypt.sh/index.php/apps/calendar/p/8dP6z6XQDnkPREo4/Monero-Meetings>  
<strong>\<rehrar\></strong> 1. Greetings  
<strong>\<rehrar\></strong> heyo  
<strong>\<serhack\></strong> Hi\!  
<strong>\<ErCiccione\></strong> Ciao  
<strong>\<midipoet\></strong> ola  
<strong>\<vp11\></strong> Olá everyone  
<strong>\<hrumag\></strong> Ciao\!  
<strong>\<rehrar\></strong> sgp is gone at a place with sarang  
<strong>\<el00ruobuob\_\[m\]\></strong> hello  
<strong>\<rehrar\></strong> doing some Monero representation or whatever.  
<strong>\<vp11\></strong> cool  
<strong>\<midipoet\></strong> bigging up the m to the o  
<strong>\<xmrmatterbridge\> \<xmrscott\></strong> Hola  
<strong>\<rehrar\></strong> 2. Community highlights  
<strong>\<rehrar\></strong> You can now read the Monero Moon, a curated weekly newsletter regarding all things Monero. Here is the latest issue which covers October 16-22: <https://medium.com/@johnfoss/the-monero-moon-issue-7-b44cf6afd655>  
<strong>\<rehrar\></strong> Does anyone else have community updates to share?  
<strong>\<ErCiccione\></strong> yep  
<strong>\<rehrar\></strong> go  
<strong>\<el00ruobuob\_\[m\]\></strong> yes  
<strong>\<ErCiccione\></strong> the guide for the GUI is now cooooool: we have a great template that builds it in PDF HTML and epub  
<strong>\<ErCiccione\></strong> it also make possible to translate it in different languages, but i will talk about this in the workgroup update  
<strong>\<ErCiccione\></strong> the coolest thing is that the integration with the gui itself will be easier  
<strong>\<ErCiccione\></strong> ah, it was already included in the archive for gui 0.13 and it will also be in 0.13.04  
<strong>\<rehrar\></strong> nice  
<strong>\<ErCiccione\></strong> there is is: <https://github.com/monero-ecosystem/monero-GUI-guide>  
<strong>\<ErCiccione\></strong> for now only the PDF is implemented in the GUI  
<strong>\<ErCiccione\></strong> but i plan to make it builds automatically in HTML to a github page  
<strong>\<ErCiccione\></strong> ah, soon it will have CI, probably with travis  
<strong>\<ErCiccione\></strong> that’s it about the guide  
<strong>\<el00ruobuob\_\[m\]\></strong> cool\!  
<strong>\<el00ruobuob\_\[m\]\></strong> on my side, i started 0.13 / cnv2 related updates on the website  
<strong>\<el00ruobuob\_\[m\]\></strong> inlcuding moneropedia bulletproof article and other user guides updates  
<strong>\<ArticMine\></strong> hi  
<strong>\<ErCiccione\></strong> saw the ping about that el00ruobuob\*, will review it when i can. Thanks a lot for doing it btw. Very useful  
<strong>\<rehrar\></strong> moneropedia really does need a good amount of work. Great job el00ruobuob\*\[m\]  
<strong>\<el00ruobuob\_\[m\]\></strong> yeah, a review will be very helpfull for this  
<strong>\<el00ruobuob\_\[m\]\></strong> i based my work on surae bulletproof chat this week  
<strong>\<hrumag\></strong> Does moneropedia work out now? I knew there where problems  
<strong>\<hrumag\></strong> To translate it I mean  
<strong>\<ErCiccione\></strong> hrumag: yes that’s fixed. thanks to el00ruobuob\*  
\*\*\<el00ruobuob\*\[m\]\>\*\* since i correct the glitches i introduces with the relocalization, it seems to work fine now  
<strong>\<hrumag\></strong> Thanks man\!  
<strong>\<rehrar\></strong> no, we need a Ruby coder to help solve that  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* you’re welcome  
<strong>\<rehrar\></strong> whaaaaa?  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* to solve what rehrar?  
<strong>\<ErCiccione\></strong> rehrar: it is solved now  
<strong>\<rehrar\></strong> when did this happen?  
<strong>\<rehrar\></strong> oh wait  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* i am the ruby coder :D  
<strong>\<rehrar\></strong> never mind, ignore me. I remember this going down. :P  
<strong>\<rehrar\></strong> I’m such a dork  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* well, i try to be  
<strong>\<rehrar\></strong> were you finished with your update el00ruobuob\_\[m\] ?  
<strong>\<ErCiccione\></strong> don’t remember the PR now, it was a couple fo months ago IIRC  
<strong>\<ErCiccione\></strong> el00ruobuob\_ ^  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* yeah it is finished  
<strong>\<xmrmatterbridge\> \<msvb-lab\></strong> Testing relay.  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* it just had a glitch introduced that i fixed by adding the articles manes to the yml language files  
<strong>\<rehrar\></strong> it’s up msvb-lab  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* So in any case, if there is anything going wrong with moneropedia translation, let me know  
<strong>\<rehrar\></strong> 3. FFS updates  
<strong>\<rehrar\></strong> FFS proposals still needing funding:  
<strong>\<rehrar\></strong> dsc full-time GUI coding: <https://forum.getmonero.org/8/funding-required/90931/full-time-gui-coding>  
<strong>\<rehrar\></strong> Zero to Monero: Second Edition: <https://forum.getmonero.org/8/funding-required/90940/zero-to-monero-second-edition>  
<strong>\<rehrar\></strong> ErCiccione: Coordinator of the Localization Workgroup: <https://forum.getmonero.org/8/funding-required/90800/erciccione-coordinator-of-the-localization-workgroup-translations-another-quarter>  
<strong>\<rehrar\></strong> The Monero Moon Weekly Newsletter: <https://forum.getmonero.org/8/funding-required/90902/the-monero-moon-a-new-weekly-newsletter-regarding-all-things-monero>  
<strong>\<rehrar\></strong> el00ruobuob: part time for a new quarter (October - December) <https://forum.getmonero.org/8/funding-required/90757/el00ruobuob-part-time-for-a-new-quarter-october-december>  
<strong>\<rehrar\></strong> Proposals in ideas:  
<strong>\<rehrar\></strong> Surae Nother Monero Konferenco: <https://forum.getmonero.org/6/ideas/90909/surae-noether-first-denver-monero-konferenco-spring-2019>  
<strong>\<rehrar\></strong> Needs more feedback to move: Lee Clagett (vtnerd) Broadcast Transactions Over Tor: <https://forum.getmonero.org/6/ideas/90923/lee-clagett-vtnerd-broadcast-transactions-over-tor-hidden-service>  
<strong>\<rehrar\></strong> has everyone looked at vtnerd’s proposal?  
<strong>\<rehrar\></strong> we should try to reach a small consensus within our group here about whether or not it should be moved, because I think it desperately needs to be moved  
<strong>\<ErCiccione\></strong> i think it should be moved  
<strong>\<parasew\[m\]\></strong> hi everyone, sorry late to the meeting  
<strong>\<parasew\[m\]\></strong> also think it should be moved\!  
<strong>\<vp11\></strong> yes, vtnerd’s proposal should be moved to the next step.  
<strong>\<ErCiccione\></strong> i mean, broadcasting transactions through tor is useful and will also prepare people to kovri  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* yeah both should be moved  
<strong>\<vp11\></strong> as far as I can see there are only benefits to the Monero ecosystem and infrastructure  
<strong>\<rehrar\></strong> perfect, that’s a lot of “Aye”s  
<strong>\<rehrar\></strong> I’ll talk to the core team  
<strong>\<ErCiccione\></strong> haven’t take a look at suare’s proposal yet, but i approve it blindly  
<strong>\<rehrar\></strong> Does anyone else have a FFS update, or comments about any of these FFS proposals?  
<strong>\<vp11\></strong> me  
<strong>\<rehrar\></strong> go  
<strong>\<vp11\></strong> I’d like to thank everyone who funded my proposal for the translation of part of the ecosystem to Brazilian Portuguese.  
<strong>\<vp11\></strong> I’ve recently translated Monerujo, the PR is already up  
<strong>\<vp11\></strong> and will dedicate extra time during weekends to get things going. I also intend to pass part of the payouts to those who are helping me with the reviews.  
<strong>\<vp11\></strong> that’s all, thanks again  
<strong>\<parasew\[m\]\></strong> vp11 (IRC) amazing work\! thanks\!  
<strong>\<rehrar\></strong> great\! thanks vp11  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* thanks for being awsome vp11  
<strong>\<rehrar\></strong> 4. Workgroup report  
<strong>\<rehrar\></strong> This is a new separate section where other workgroups can report on all that they are working on. If you would like for your workgroup to be represented, please contact me or sgp at least a few hours before the meeting.  
<strong>\<rehrar\></strong> a. Localization workgroup  
<strong>\<rehrar\></strong> ErCiccione  
<strong>\<ErCiccione\></strong> thanks rehrar  
<strong>\<ErCiccione\></strong> so  
<strong>\<ErCiccione\></strong> major news are:  
<strong>\<ErCiccione\></strong> - The major release of the GUI saw a lot of activity from translators. I’m really thankfull for that. 26 of the 32 languages got updated and a new one was added (bulgarian, but not available yet). It was a long and stressful work, but i’m very proud of the outcome  
<strong>\<rehrar\></strong> and I’m proud of your pride  
<strong>\<ErCiccione\></strong> i’m proud that your are proud of my pride  
<strong>\<ErCiccione\></strong> - Some time ago i started taking care of the translations of the outreach workgroup with lh1008. I also managed the whole repo for them since they had some problems with git’s workflow  
<strong>\<ErCiccione\></strong> we got some trnaslations and other are in progress. The repo with the instructions is here: <https://github.com/monero-ecosystem/outreach-docs>  
<strong>\<ErCiccione\></strong> - As i said earlier, the Guide for the GUI wallet has now a new template and it’s possible to translate in multiple languages. I wrote the instructions in the readme for both contributors who would like to help improve it and translators. The repo, again is here: <https://github.com/monero-ecosystem/monero-GUI-guide>  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* ^ i saw this, and will start working on it soon  
<strong>\<ErCiccione\></strong> - The documentation of Kovri is getting updated, that means that new parts will be available soon (first, when <https://gitlab.com/kovri-project/kovri-docs/merge_requests/107> will be merged)  
<strong>\<ErCiccione\></strong> thanks el00ruobuob\_, i’m not spreading much the news because i still think it need some tweaking. When i’m done with those i will spread the news all over the internettt\!  
<strong>\<hrumag\></strong> is there any plan to start translation activity on kovri docs?  
<strong>\<hrumag\></strong> Or there are other translation that have to be addressed with a major priority?  
<strong>\<ErCiccione\></strong> hrumag: i was talking about kovri-docs  
<strong>\<rehrar\></strong> alright, is there any other workgroup present that wants to report?  
<strong>\<rehrar\></strong> I should work on getting Monerujo here. They’re doing some exciting stuff.  
<strong>\<ErCiccione\></strong> - Finally, I’m keep testing pootle and it will be ready before the end of my FFS (beginning of december), i consider it my last milestone. I’m in contact with pigeons for that, but no major issues at the moment  
<strong>\<rehrar\></strong> oops sorry  
<strong>\<ErCiccione\></strong> so. I’m done. I remind that my FFS is still not completely funded, and i would really appreciate if it will be :P  
<strong>\<ErCiccione\></strong> no problem rehrar. I’m done now  
<strong>\<rehrar\></strong> ok. Now is there anything from anyone else?  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* anything to say about mrw or r/monero-support rehrar?  
<strong>\<ErCiccione\></strong> hrumag: right now the priority are the documents of the outreach group. But we have so much stuff to do that everything can considered a priority :)  
<strong>\<rehrar\></strong> regarding mrw I have a guy working on the livechat and ticketing integration system. He’ll be reporting to me soon.  
<strong>\<ErCiccione\></strong> (sorry for the overlap, but if somebody have question about the work of the localization workgroup, just ask. Here or on \#monero-translations)  
<strong>\<rehrar\></strong> The Monero Games (and subsequent push to /r/MoneroSupport) has been going pretty good. I’ve got a couple people revealing their FFS donations and getting points for it.  
<strong>\<rehrar\></strong> This Games is more of a beta to see what can be done and what can be improved for next time.  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* what is the process to reveal the FFS donation?  
<strong>\<rehrar\></strong> New FFS still in the works  
<strong>\<rehrar\></strong> \#oneday  
<strong>\<rehrar\></strong> both the CLI and the GUI have commands to reveal to another person and prove your transaction  
<strong>\<rehrar\></strong> we have a tutorial on it on the website  
<strong>\<vp11\></strong> rehrar, you already have the script that counts the upvotes in place?  
<em><em>\<el00ruobuob</em>\[m\]\></em>\* are you the one to prove them to?  
<strong>\<rehrar\></strong> not yet, sgp and I are working on that but he went to rep Monero  
<strong>\<rehrar\></strong> if you’d like to help with that vp11 let me know  
<em><em>\<rehrar\>\*\* el00ruobuob</em>\[m\]: yes  
<strong>\<el00ruobuob\_\[m\]\></strong> ok, will do it soon then  
<strong>\<rehrar\></strong> Alright, anything else?  
<strong>\<rehrar\></strong> so…  
<strong>\<rehrar\></strong> Ideas have run thin in Monero. That’s fine.  
<strong>\<rehrar\></strong> It’s not like we’re trying to change the world or anything.  
<strong>\<rehrar\></strong> I kid. But for real, if we want to end early we can. :)  
<strong>\<dog\\\></strong> I’d like to share the idea of creating a page on the getmonero website with a partial infrastructure representation.  
<strong>\<rehrar\></strong> Cool. Can you elaborate dog\\?  
<strong>\<el00ruobuob\_\[m\]\></strong> a partial infrastructure representation?  
<strong>\<dog\\\></strong> I think it might be cool to have a visually interesting page where users can explore the infrastructure around Monero — not only merchants, but blockchain explorers, payment gateways, interesting libraries, etc.  
<strong>\<dog\\\></strong> if someone is completely new about Monero, where one would go to see how big is the infrastructure around the protocol?  
<strong>\<rehrar\></strong> the current Merchants page has all of those things  
<strong>\<dog\\\></strong> Just a random idea  
<strong>\<rehrar\></strong> perhaps it is poorly named  
<strong>\<rehrar\></strong> Maybe it can be named to “Ecosystem” or something  
<strong>\<ErCiccione\></strong> ecosystem is taken\! :P  
<strong>\<rehrar\></strong> find me a synonym  
<strong>\<el00ruobuob\_\[m\]\></strong> or perhaps does it need a refresh to be more readable  
<strong>\<ErCiccione\></strong> (for who don’t know what the Monero Ecosystem Project is: <https://github.com/monero-ecosystem>)  
<strong>\<dog\\\></strong> Maybe even remove it from the website, to a new home where people can easily contribute and share places accepting / using XMR. I don’t know, I’m just throwing ideas.  
<strong>\<dog\\\></strong> it’s open ideas time anywya  
<strong>\<rehrar\></strong> true  
<strong>\<rehrar\></strong> I’ve always thought the on-site directory will eventually be pretty unsustainable  
<strong>\<midipoet\></strong> an infographic that shows how all elements of the ecosystem are related/connected and who is in charge would be cool  
<strong>\<rehrar\></strong> if Monero ever catches on, it would be massive  
<strong>\<rehrar\></strong> and worth a site all by itself  
<strong>\<ErCiccione\></strong> dog\\: you actually have a point, i was working on something like that in past (a github repo), maybe i should give it some love. Would you like to contribute to create something like that?  
<strong>\<dog\\\></strong> midipoet: this as well, I’d like that. so people can understand how the infrastructure is organized (e.g. showing how merchants have to go through a few available payment gateways etc)  
<strong>\<dog\\\></strong> ErCiccione: yes, I’d gladly help albeit my lack of good tech skills.  
<strong>\<ErCiccione\></strong> my idea was to create a page called ‘awesome-monero’, on the same line of ‘awesome-infosec’ ‘awesome-movies’ and all that stuff  
<strong>\<ErCiccione\></strong> \<dog  
<strong>\<ErCiccione\></strong> dog\\: no skills needed, would be enough to have a list of all monero-related projects existent and then put it on a formatted markdown page  
<strong>\<el00ruobuob\_\[m\]\></strong> imho, this does not need to replace the merchant page, but it could complete it nicely  
<strong>\<ErCiccione\></strong> i already collected some, but then i stopped because i had no time  
<strong>\<rehrar\></strong> el00ruobuob</em>\[m\]: as it is, the merchant page is still poorly named since it has libraries and gateways as well  
<strong>\<dog\\\></strong> I like these lists, but they’re very textual and would be maybe a small improvement of the current merchants page.  
<strong>\<midipoet\></strong> i see your vision dog\\  
<strong>\<dog\\\></strong> and just a few (very) interested people really take the time to read mountains of text  
<strong>\<rehrar\></strong> yep, I do too, and it’s a great idea  
\*\*\<el00ruobuob\*\[m\]\>\*\* rehrar, i don’t disagree, we have to find a synonym  
<strong>\<dog\\\></strong> if I can convince someone that Monero is actually good money that provides freedom, the next reasonable question is: “what can I do with it?”. I have trouble giving precise information on that.  
<strong>\<ErCiccione\></strong> dog\\: make sense, an infographic sounds like a good option, but requires a lot of work  
<strong>\<ErCiccione\></strong> maybe the outreach workgroup could help with that  
<strong>\<dog\\\></strong> it’s just an idea, maybe we can think about it and discuss more the next week. maybe invite some people who might be interested in helping like the outreach group, as you mentioned.  
<strong>\<midipoet\></strong> like this <https://blockgeeks.com/wp-content/uploads/2016/11/image-1-1024x936.png> except Monero Ecosystem related  
<strong>\<dog\\\></strong> something like that midipoet, but taken to the next level  
<strong>\<dog\\\></strong> meaning people can actually propose contributions on what to add/remove  
<strong>\<dog\\\></strong> making it the ultimate web directory for the monero infrastructure  
<strong>\<dog\\\></strong> but we can start small :)  
<strong>\<midipoet\></strong> and yes i think O &amp; E would be the people. yes, if it was interactive, in like some 3D web based model that you could zoom in and out of  
<strong>\<ErCiccione\></strong> could just be a .sla document where people can edit adding their contributes using scribus, and then it gets build into a pdf  
<strong>\<ErCiccione\></strong> that’s how the documents of the outreach workgroup work  
<strong>\<midipoet\></strong> pdfs are so static though  
<strong>\<ErCiccione\></strong> true. HTML page?  
<strong>\<midipoet\></strong> an interactive .swf might be better  
<strong>\<midipoet\></strong> though i havent a clue about security aspects of a flash document  
<strong>\<ErCiccione\></strong> i would happily host that on the Monero Ecosystem Project tho  
<strong>\<ErCiccione\></strong> mmmh  
<strong>\<dog\\\></strong> could be a HTML page mirrored on a github repo (ecosystem)  
<strong>\<midipoet\></strong> you could make a public Prezi that is shared and editable by anyone  
<strong>\<midipoet\></strong> that would give you the int eractivity if anyone wanted to view it  
<strong>\<dog\\\></strong> I prefer to leave it out of closed systems like Prezi.  
<strong>\<ErCiccione\></strong> dog\\: yes, that’s what i was thinking. Similar to the way i want to build the Guide of the GUI (edited on github -\> pushed on github pages)  
<strong>\<midipoet\></strong> yes, there are FLOSS alternatives  
<strong>\<rehrar\></strong> ^  
<strong>\<dog\\\></strong> it has to be sustainable. I like HTML based with some interactivity done by HTML 5. could even be without any JS to be tor-friendly.  
<strong>\<midipoet\></strong> <http://sozi.baierouge.fr/>  
<strong>\<dog\\\></strong> a concise, simple and graphical directory of the infrastructure  
<strong>\<dog\\\></strong> where people can easily suggest the removal or addition of anything and the repo maintainers can approve or deny.  
<strong>\<rehrar\></strong> I’ll check out Sozi  
<strong>\<rehrar\></strong> yep, sounds like a fun project.  
<strong>\<rehrar\></strong> Alright all, four minutes left.  
<strong>\<rehrar\></strong> Anything else?  
<strong>\<ErCiccione\></strong> i like that, we should definitely talk about it in the next meeting. In the meantime we can check the best options to make it real dog\\  
<strong>\<rehrar\></strong> 6. Confirm next meeting date/time  
<strong>\<dog\\\></strong> yep  
<strong>\<rehrar\></strong> The next community meeting will be two weeks from today on 10 November at 17:00 UTC. When in doubt, use the calendar: <https://xmr.ncrypt.sh/index.php/apps/calendar/p/8dP6z6XQDnkPREo4/Monero-Meetings>  
<strong>\<rehrar\></strong> 7. Conclusion  
<strong>\<rehrar\></strong> That’s all\! Thanks for attending this Monero Community meeting, and we hope to see you on /r/MoneroCommunity and \#monero-community. Take care, and know that change starts with YOU.  
<strong>\<el00ruobuob\_\[m\]\></strong> thank you all for being awesome\!  
<strong>\<ArticMine\></strong> Thank you  
\*\*\<ErCiccione\>\*\* Thanks everybody. Thanks rehrar for the moderation
