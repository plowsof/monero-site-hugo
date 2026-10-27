---
title: Logs for the Community Meeting Held on 2020-01-18
tags: [dev diaries, crypto]
author: asymptotically / SamsungGalaxyPlayer
---

# Logs

<strong>\<sgp\_\></strong> 0. Introduction  
<strong>\<sgp\_\></strong> We would like to welcome everyone to this Monero Community Workgroup Meeting\!  
<strong>\<sgp\_\></strong> Link to agenda on GitHub: <https://github.com/monero-project/meta/issues/428>  
<strong>\<sgp\_\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community, including other Monero workgroups. We use meetings to encourage the community to share ideas and provide support.  
<strong>\<sgp\_\></strong> 1. Greetings  
<strong>\<ErCiccione\></strong> Ciao  
<strong>\<almutasim\></strong> Hi.  
<strong>\<sarang\></strong> Hello  
<strong>\<v1docq47\[m\]\></strong> Hi  
<strong>\<netrik182\></strong> hi  
<strong>\<sgp\_\></strong> ping rehrar  
<strong>\<sgp\_\></strong> welcome everyone  
<strong>\<sgp\_\></strong> thanks for showing up 30 minutes earlier than usual :)  
<strong>\<vtnerd\></strong> hi  
<strong>\<sgp\_\></strong> 2. Community highlights  
<strong>\<sgp\_\></strong> See Monero weekly highlights at <https://revuo-monero.com>  
<strong>\<rehrar\></strong> Present.  
<strong>\<sgp\_\></strong> A new edition was just out yesterday I believe  
<strong>\<sgp\_\></strong> The community planning for the Konferenco has been underway. Updates on that later.  
<strong>\<sgp\_\></strong> Does anyone have community (non-workgroup) updates to share?  
<strong>\<sgp\_\></strong> apparently not :)  
<strong>\<sgp\_\></strong> 3. CCS updates  
<strong>\<sgp\_\></strong> Funding required:  
<strong>\<sgp\_\></strong> 3 months part time work on Getmonero.org <https://ccs.getmonero.org/proposals/ErCiccione-website-jan-march.html> (92.42 / 174 XMR)  
<strong>\<sgp\_\></strong> Ideas (to be discussed):  
<strong>\<sgp\_\></strong> Locha Mesh, private transactions and sync over a resilient long-range radio mesh network <https://repo.getmonero.org/monero-project/ccs-proposals/merge_requests/115>  
<strong>\<rehrar\></strong> We're switching to Fridays.  
<strong>\<sgp\_\></strong> there were some concerns about the cost and project management (clear project milestrones) on this one  
\* binaryFate lurking  
<strong>\<sgp\_\></strong> the total amount was reduced to 150 xmr  
<strong>\<cankerwort\></strong> hola  
<strong>\<sgp\_\></strong> any other comments? thanks to everyone who left comments on gitlab  
<strong>\<vtnerd\></strong> yikes, is there any more technical details on what they plan to do?  
<strong>\<sgp\_\></strong> vtnerd: I am not sure, but I recommend asking on gitlab since they have been responsive so far  
<strong>\<binaryFate\></strong> do they plan to post an updated proposal soon?  
\* needmonero90 lurks while sleeping  
<strong>\<sgp\_\></strong> binaryFate: they already updated the amount  
<strong>\<vtnerd\></strong> ah crud yeah they have a link. I can't respond now because this is the first I've paid attention to it. My primary concern would be the in the routing code, its not trivial for this type of thing  
<strong>\<binaryFate\></strong> most comments were strongly suggesting to be more specific on milestones  
<strong>\<sgp\_\></strong> they focused a bit more on the goals and roadmap  
<strong>\<sgp\_\></strong> <https://repo.getmonero.org/monero-project/ccs-proposals/merge_requests/115/diffs?commit_id=1031a2e444255e5fa8138601ef746e8b37900a18>  
<strong>\<vtnerd\></strong> hmm its very much a wip I think  
<strong>\<vtnerd\></strong> my only comment is that this has more risk than the usual CCS for monero feature  
<strong>\<binaryFate\></strong> agree. On the other hand this will have visibility beyond Monero circles.  
<strong>\<sgp\_\></strong> thanks vtnerd, please ask specific questions on gitlab too so that the proposal can get better  
<strong>\<ErCiccione\></strong> I haven't had time to look at the proposal after mu last comment, but i see that one of the milestones is about getting the localization workgroup translate their docs  
<strong>\<ErCiccione\></strong> that's very unlikely to happen  
<strong>\<vtnerd\></strong> yes, if it works ... very awesome  
<strong>\<ErCiccione\></strong> i don't really think we have the resources for that, we already struggle for our own stuff  
<strong>\<rehrar\></strong> what would it mean to take this on as Monero Project project?  
<strong>\<sgp\_\></strong> rehrar: have they given any indication they have any interest in that?  
<strong>\<rehrar\></strong> If they haven't, then I wouldn't really be for funding this.  
<strong>\<sgp\_\></strong> explain please  
<strong>\<cankerwort\></strong> The tech sounds awesome but I'd be interested in practical limitation estimated like time to broadcast a transaction and range  
<strong>\<rehrar\></strong> explain? hmmm...  
<strong>\<cankerwort\></strong> although the name is not even in esperanto  
<strong>\<rehrar\></strong> Well, I can see how developing this tech might be good somewhat, but it's kind of general in its application (not really Monero-only focused) as I understand.  
<strong>\<rehrar\></strong> and if it's something that can benefit a lot of other projects, Monero is fronting a good amount of the bill instead of others.  
<strong>\<rehrar\></strong> So a way to offset this cost is to have it be a Monero Project project. Similar to OpenAlias. It benefits others if they want it, but it's distinctly "From Monero people"  
<strong>\<sgp\_\></strong> rehrar: : I think requiring that the CCS only gives $$$ to "Monero Project" projects is far too restrictive and is really a new precedent, so I'm curious if you're focused on that part or the main nature of the project's goal (Monero-focued or elsewhere with Monero as a feature)  
<strong>\<rehrar\></strong> the marketing aspect of that offset the cost of its creation.  
<strong>\<ArticMine\></strong> Bandwidth is my question  
<strong>\<sgp\_\></strong> my recommendation then is to ask if they want to do that, but I would personally understand if they don't want to  
<strong>\<needmonero90\></strong> I am against the proposal from a sustainability perspective. Funding a development \*team\* is not the goal imo, I think we should strive for funding key people for projects that already have a decentralized/communal ethos. If they can't get developers without paying them, we won't be able to bootstrap the system to work without money greasing the wheels constantly  
<strong>\<needmonero90\></strong> I've been trying to find a way to express the value of 'coordinators' in the ecosystem that are always available to manage/direct/help their particular corner, so that the people working on the actual open source part have low friction  
<strong>\<needmonero90\></strong> And that kind of position carries with it an expectation of availability  
<strong>\<needmonero90\></strong> So paying for that particular position, once it emerges, is warranted, but not a full team  
<strong>\<needmonero90\></strong> The MRL is a good example, they're pretty much always available to talk about stuff, which is a big deal. They buffer ideas and conversations for the actually decentralized research team  
<strong>\<needmonero90\></strong> Who has no expectation of availability  
<strong>\<sgp\_\></strong> in this case "a full team" is 2 people I believe  
<strong>\<cankerwort\></strong> maybe an element of availability and/or dedication to reddit posts and updates would help?  
<strong>\<needmonero90\></strong> I mean, the issue is more about being available (for a decentralized project)  
<strong>\<sgp\_\></strong> we've spent a good amount of time on this topic, so let's only give it another minute or two  
\* needmonero90 nods  
<strong>\<binaryFate\></strong> Seeing their interactions on twitter, they are getting \*a lot\* of praise from bitcoin/grin/cypherpunk larger crypto space.  
<strong>\<binaryFate\></strong> In their own answers I did not see Monero mentioned a single time.  
<strong>\<binaryFate\></strong> So on the plus side I see a lot of potential visible PR for Monero in return for contributing, on the minus side I fear lack of Monero-specific dedication from the project team  
<strong>\<sgp\_\></strong> looks like marketing is an important part to focus on more  
<strong>\<rehrar\></strong> binaryFate ^  
<strong>\<sgp\_\></strong> without overstepping into the whole thing, I think it's appropriate to expect some recognition  
<strong>\<ErCiccione\[m\]\></strong> i think if the proposal get approved, we should require recognition  
<strong>\<sgp\_\></strong> any final comments?  
<strong>\<ErCiccione\[m\]\></strong> like put it clearly in the website and everywhere else that part of the development is funded by Monero  
<strong>\<ArticMine\></strong> That is reasonable  
<strong>\<binaryFate\></strong> if we make it more explicit on either part that this project is also about marketing for Monero, then the proposal has more value as we don't just look at the neaty greaty technicals  
<strong>\<sgp\_\></strong> cool, moving on  
<strong>\<sgp\_\></strong> v1docq47: video creation / translations into russian (february - july 2020) <https://repo.getmonero.org/monero-project/ccs-proposals/merge_requests/116>  
<strong>\<sgp\_\></strong> in my personal opinion, this is a great proposal. I'm blown away by the amount of work they do  
<strong>\<sgp\_\></strong> and they recently made a Trello board so we can more easily see what they are working on  
<strong>\<sgp\_\></strong> I appreciate that a lot  
<strong>\<cankerwort\></strong> also, given grin/btc transactions are much smaller, their tech would work better with those coins  
<strong>\<ErCiccione\[m\]\></strong> yeah, they are also very responsive to reviews and they contact me privately sometimes to have clarifications on the localization process. It's a +1 from me  
<strong>\<sgp\_\></strong> cool, any other comments?  
<strong>\<sgp\_\></strong> A Monero-centric Merchant Marketplace <https://repo.getmonero.org/monero-project/ccs-proposals/merge_requests/117>  
<strong>\<sgp\_\></strong> I don't personally have any comments here yet  
<strong>\<rehrar\></strong> Ten hours. Quite new. Let's get them to hop on this channel to answer some questions.  
<strong>\<sgp\_\></strong> yeah, also Reddit, etc  
<strong>\<sgp\_\></strong> we can proceed then  
<strong>\<sgp\_\></strong> 4. Workgroup report  
<strong>\<sgp\_\></strong> a. Localization workgroup  
<strong>\<sgp\_\></strong> ErCiccione\[m\]: any update?  
<strong>\<ErCiccione\[m\]\></strong> Not really. Soon i will make a general refresh of the strings in gui and cli  
<strong>\<ErCiccione\[m\]\></strong> so that translators can work on the new merged stuff  
<strong>\<ErCiccione\[m\]\></strong> i just want to note  
<strong>\<ErCiccione\[m\]\></strong> that there are many suggested strings on weblate (translate.getmonero.org), but no reviewers to take a look at them,  
<strong>\<ErCiccione\[m\]\></strong> so, after the refresh, i will make a call for translators and i ask the community at large to spread it as much as possible, because there is a lot to do  
<strong>\<ErCiccione\[m\]\></strong> i will probably refresh the CLI first, because the GUI folks are changing a lot of strings and i want to wait for them to be finished first  
<strong>\<ErCiccione\[m\]\></strong> that's it  
<strong>\<almutasim\></strong> Sounds great.  
<strong>\<netrik182\></strong> ErCiccione\[m\]: you can ping me too for translations  
<strong>\<sgp\_\></strong> thanks ErCiccione\[m\]  
<strong>\<sgp\_\></strong> b. GUI workgroup  
<strong>\<sgp\_\></strong> There was a point release. Binaries are not out yet. <https://github.com/monero-project/monero-gui/releases/tag/v0.15.0.3>  
<strong>\<sgp\_\></strong> c. Outreach workgroup  
<strong>\<ErCiccione\[m\]\></strong> netrik182: Great to hear that. Keep an eye on \#monero-translations :)  
<strong>\<sgp\_\></strong> almutasim: can you give an update?  
<strong>\<almutasim\></strong> Sure. We put out a piece on Chinese perspective. We have a piece ready to go on RPC-Pay. But it is waiting on an infrastructure upgrade.  
<strong>\<netrik182\></strong> sgp: there's currently much effort being made to update server backends  
<strong>\<almutasim\></strong> We also have a piece started on paper wallets  
<strong>\<ErCiccione\></strong> About RPC-pay, would be great to have a moneropedia entry for that on getmonero.org  
<strong>\<sgp\_\></strong> <https://www.monerooutreach.org/monero-china-west.php>  
<strong>\<ErCiccione\></strong> or a dev guide  
<strong>\<almutasim\></strong> That’s a good idea.  
<strong>\<ErCiccione\></strong> basically, should be on the website one way or another  
<strong>\<sgp\_\></strong> 100%  
<strong>\<almutasim\></strong> Right  
<strong>\<almutasim\></strong> It is really neat. We have been testing it with our servers.  
<strong>\<sgp\_\></strong> I look forward to seeing your system where people can get paid, where you effectively serve as a mining pool for RPC-pay  
<strong>\<sgp\_\></strong> any other updates?  
<strong>\<almutasim\></strong> we are working with endogenic on a nice document he has on Wallet auditing.  
<strong>\<almutasim\></strong> That is about it.  
<strong>\<sgp\_\></strong> nice  
<strong>\<sgp\_\></strong> d. Hardware workgroup  
<strong>\<sgp\_\></strong> we can come back to this is msvb-lab is present  
<strong>\<sgp\_\></strong> e. Konferenco workgroup  
<strong>\<sgp\_\></strong> lots of work has been ongoing here  
<strong>\<sgp\_\></strong> weekly meetings on Wednesdays at this point  
<strong>\<sgp\_\></strong> tentative date June 13-14  
<strong>\<sgp\_\></strong> we have a tentative location, but there are many outstanding questions  
<strong>\<sgp\_\></strong> it will be in Berlin  
<strong>\<sgp\_\></strong> any really quick konferenco questions? you can help out in \#monero-konferenco  
<strong>\<sgp\_\></strong> events will be livestreamed as always  
<strong>\<sgp\_\></strong> ok, moving on then  
<strong>\<sgp\_\></strong> f. Monero Research Lab  
<strong>\<sarang\></strong> Hey there  
<strong>\<sgp\_\></strong> sarang: can you give a brief update please?  
<strong>\<sgp\_\></strong> :)  
<strong>\<sarang\></strong> Sure  
<strong>\<sarang\></strong> Over the past couple of weeks or so, the Triptych preprint was posted and got some good coverage  
<strong>\<sarang\></strong> It's undergone some updates as well  
<strong>\<sarang\></strong> That's a linkable ring signature construction that scales well  
<strong>\<sarang\></strong> sgp\_ and I worked up a blag post on supply auditing that will appear soon  
<strong>\<sarang\></strong> I worked up some material on hidden timelocks, which could be useful but need more analysis  
<strong>\<binaryFate\></strong> tldr hidden timelocks?  
<strong>\<sarang\></strong> I am still waiting on any final review notes from suraeNoether on the CLSAG overhaul  
<strong>\<sarang\></strong> binaryFate: it's possible to replace "plaintext" timelocks with commitments and clever range proofs  
<strong>\<sarang\></strong> So you can show that the timelock for an (unknown) input has passed without revealing it  
<strong>\<binaryFate\></strong> to avoid standing out?  
<strong>\<sarang\></strong> Yep  
<strong>\<binaryFate\></strong> gotcha  
<strong>\<sarang\></strong> It was designed for DLSAG, but also has more general applicability  
<strong>\<almutasim\></strong> That sounds awesome.  
<strong>\<sarang\></strong> And the new CLSAG security model is being ported to DLSAG as well, along with some key aggregation math  
<strong>\<needmonero90\></strong> Math wizards  
<strong>\<almutasim\></strong> That sounds awesome.  
<strong>\<sarang\></strong> It remains to be seen if the increase in tx size would justify hidden timelocks  
<strong>\<sgp\_\></strong> re auditability, I need help making a better auditability image still, so let me know if you have ideas <https://repo.getmonero.org/monero-project/monero-site/merge_requests/1207>  
<strong>\<sgp\_\></strong> I probably won't be able to personally work on this until Sunday or Monday  
<strong>\<sgp\_\></strong> g. Website workgroup  
<strong>\<sgp\_\></strong> ErCiccione: can we have another round of updates please? :)  
<strong>\<ErCiccione\></strong> gladly  
<strong>\<ErCiccione\></strong> so,  
<strong>\<almutasim\></strong> The wallet auditing document is related to that. A draft should go up on TAIGA tomorrow.  
<strong>\<ErCiccione\></strong> A lot is going on. We have a lot of pull requests ready to go and they should be merged at the beginning of next week  
<strong>\<ErCiccione\></strong> right now i'm focusing mostly on getting the website (at least the 'core' part of it) on Weblate, because right now making any change, means that that change needs to be ported to all languages  
<strong>\<ErCiccione\></strong> that results in a lot of time spent for that, which is very annoying for everybody and suck a lot of time that could be used for something more productive.  
<strong>\<ErCiccione\></strong> I'm running tests and Weblate seems to be reacting nicely, even if YAML files can be a bit troublesome and may happen that stuff don't get parsed  
<strong>\<ErCiccione\></strong> to avoid that i'm making extensive tests on my personal version, which is a copy of the instance hosted on translate.getmonero.org  
<strong>\<almutasim\></strong> That makes a lot of sense. I honestly don’t know how you handle the current situation.  
<strong>\<ErCiccione\></strong> almutasim: a lot of swearing  
<strong>\<almutasim\></strong> Ha\!  
<strong>\<ErCiccione\></strong> ;)  
<strong>\<ErCiccione\></strong> but yeah it's extremely annoying, especially now that we are updating a lot of stuff and all languages need to be up to date  
<strong>\<sgp\_\></strong> cool, thanks for your sacrifice  
<strong>\<ErCiccione\></strong> so, that's the priority for me at the moment. After that i will try to put other parts of the website on weblate (footers and others), which structure make much harder for weblate to parse them and could require some substantial changes to the structure of those documents  
<strong>\<ErCiccione\></strong> :P  
<strong>\<ErCiccione\></strong> beside that, next will be the roadmap and the FAQ section  
<strong>\<ErCiccione\></strong> ah  
<strong>\<ErCiccione\></strong> the onion mirror should be up at the end of this month according to pony  
<strong>\<sgp\_\></strong> oooh fancy  
<strong>\<ErCiccione\></strong> Yeah, everything is ready and some prep PR already got merged  
<strong>\<ErCiccione\></strong> if people are interested in the development of the website, please join \#monero-site and visit repo.getmonero.org  
<strong>\<ErCiccione\></strong> reviews of Pull requests and issues are very welcome  
<strong>\<sgp\_\></strong> I love the website workgroup since it's something anyone, regardless of skill, can help with. there are so many different things to do and an unlimited amount of necessary work  
<strong>\<sgp\_\></strong> thanks ErCiccione  
<strong>\<sgp\_\></strong> 5. Open ideas time  
<strong>\<almutasim\></strong> And with so much impact\!  
<strong>\<sgp\_\></strong> I'm going to extend the meeting 10 minutes to fit open ideas time in here  
<strong>\<sgp\_\></strong> It’s open ideas time\! Feel free to propose your ideas to this discussion group, and feel free to comment on others’ ideas. If you disagree with the idea, please reply with constructive criticism. Thank you\!  
<strong>\<ErCiccione\></strong> absolutely sgp\_. I will try to improve our docs to make easier for newcomers to contribute  
<strong>\<rottensox\></strong> totes missed it but caught up already.  
<strong>\<ErCiccione\></strong> I think we should talk about /r/moneromining folks, it's annoying i know, but it's a discussion that must happen  
<strong>\<ErCiccione\></strong> for reference: <https://repo.getmonero.org/monero-project/monero-site/merge\_requests/1195>  
<strong>\<sgp\_\></strong> ErCiccione: indeed, this is going to be a long discussion though  
<strong>\<rottensox\></strong> i am with needmonero90 on opposing Locha Mesh for XMR.  
<strong>\<ErCiccione\></strong> yeah i understand sgp\_.  
<strong>\<rottensox\></strong> speaking from experience, nobody uses locha mesh in venezuela. nobody.  
<strong>\<ErCiccione\></strong> Right now we are removing the mention from getmonero, but we should do more  
<strong>\<sgp\_\></strong> background context: lead mod is acting rash and making racist statements, calling other people who disagree "snowflakes." Basically using the subreddit for their own purposes rather than for Monero mining  
<strong>\<sgp\_\></strong> I still need to reach out to my Reddit contacts, can do that today after the coffee chat  
<strong>\<sgp\_\></strong> but they probably won't do anything  
<strong>\<asymptotically\></strong> they wouldn't de-mod him for putting that kind of stuff in the description?  
<strong>\<sgp\_\></strong> needmonero90 is sitting on a backup subreddit we can switch to with a good amount of effort  
<strong>\<sgp\_\></strong> asymptotically: not really, Reddit is weird like that  
<strong>\<ErCiccione\></strong> i think the idea of the migration to /r/monerominer or whatever was called, is the only option we have left  
<strong>\<sgp\_\></strong> ErCiccione: yes, I think we shoudl prepare to transition to that  
<strong>\<sgp\_\></strong> maybe we should set aside specific discussion time  
<strong>\<sgp\_\></strong> to plan the transition  
<strong>\<ErCiccione\></strong> Yeah, we should.  
<strong>\<lza\_menace\></strong> I made the "A Monero-centric Merchant Marketplace" MR - I'm usually not available during these community meeting time blocks. Long form discussion in Gitlab/Reddit would be better  
<strong>\<sgp\_\></strong> ErCiccione: can you and needmonero90 please coordinate a time and invite others as needed?  
<strong>\<needmonero90\></strong> Sure.  
<strong>\<sgp\_\></strong> lza<em>menace: cool, please share on Reddit too  
<strong>\<ErCiccione\></strong> maybe a dedicated meeting or something. I know binaryfate wants to talk about the fact that the chats are getting a bit bad lately, we could include that discussion as well  
<strong>\<sgp\_\></strong> will help kick off discussion  
<strong>\<ErCiccione\></strong> Sure thing  
<strong>\<lza\_menace\></strong> sgp</em>: :thumbsup: - will do - yall have a great weekend  
<strong>\<sgp\_\></strong> " the chats are getting a bit bad lately, we could include that discussion as well" what chats?  
<strong>\<asymptotically\></strong> \#monero-markets and \#monero-pools going off-topic i think  
<strong>\<sgp\_\></strong> ah, got it  
<strong>\<binaryFate\></strong> ah yes. The channels. -pools, -markes and even sometimes \#monero  
<strong>\<sgp\_\></strong> definitely a related item  
<strong>\<sgp\_\></strong> you all are welcome to use this channel for discussion. that's what it's for :)  
<strong>\<sgp\_\></strong> oh I have one thing I wanted to mention during open ideas time  
<strong>\<sgp\_\></strong> I have a self-hosted Wekan (open-source Trello copy) instance now available. I’m happy to add your project if you are interested. Please message me for details. I’ve found it more useful than Taiga for many project management needs.  
<strong>\<sgp\_\></strong> Here’s an example for the Konferenco: <https://monero.sandcats.io/shared/f6usdnbIFv3mGp09hTFRkEbz38CHn2KHyM04V-Nhmp->  
<strong>\<sgp\_\></strong> anyone else have an open ideas topic? we're nearly out of time  
<strong>\<sgp\_\></strong> 6. Confirm next meeting date/time  
<strong>\<sgp\_\></strong> The next community meeting will be in 2 weeks on 1 February at 17:00 UTC.  
<strong>\<sgp\_\></strong> A Coffee Chat begins shortly after this meeting: <https://youtu.be/YqMcz3XOS6M>  
<strong>\<sgp\_\></strong> please PM me ASAP if you can participate. I'll distribute Jitsi links right away  
<strong>\<sgp\_\></strong> The following Coffee Chat is on Saturday 8 February at 17:00 UTC.  
<strong>\<sgp\_\></strong> 7. Conclusion  
<strong>\<sgp\_\></strong> That’s all\! Thanks for attending this Monero Community meeting, and we hope to see you on r/MoneroCommunity and \#monero-community. Take care, and know that change starts with YOU.
