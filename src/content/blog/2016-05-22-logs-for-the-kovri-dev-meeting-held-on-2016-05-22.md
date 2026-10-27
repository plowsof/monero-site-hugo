---
title: Logs for the Kovri Dev Meeting Held on 2016-05-22
summary: GNU Social status, Kovri website, i2p StackExchange, Coverity for Kovri
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<fluffypony\></strong> ok starting the meeting relay for the Kovri meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hello.  
<strong>\<fluffypony\></strong> anonimal: all yours :)  
<strong>\<i2p-relay\> {-anonimal}</strong> From <https://github.com/monero-project/kovri/issues/177>  
<strong>\<i2p-relay\> {-anonimal}</strong> Proposed meeting items:  
<strong>\<i2p-relay\> {-anonimal}</strong> 17:00 (UTC)  
<strong>\<i2p-relay\> {-anonimal}</strong> 1. Review assigned open tickets: status, code ideas (if applicable), etc.  
<strong>\<i2p-relay\> {-anonimal}</strong> 2. Any additional meeting items  
<strong>\<i2p-relay\> {-anonimal}</strong> 3. Confirm next meeting date/time  
<strong>\<i2p-relay\> {-anonimal}</strong> Starting with 1., as discussed in private with fluffypony, let’s tackle <https://github.com/monero-project/kovri/issues/assigned/fluffypony>  
<strong>\<fluffypony\></strong> hokay - should we do them one at a time ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Sure, \#105.  
<strong>\<fluffypony\></strong> sec, just opening it up  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m more curious about status updates and if we’ll pursue some of these ideas.  
<strong>\<fluffypony\></strong> ok 107  
<strong>\<fluffypony\></strong> I asked dEBRUYNE and the rest of the social media guys about that in January last  
<strong>\<fluffypony\></strong> dEBRUYNE: have you guys looked at that at all ?  
<strong>\<dEBRUYNE\></strong> I think xmrpromotions was handling that  
<strong>\<meeting-bot\> \[anonimal\]</strong> JFTR: s/107/105/  
<strong>\<dEBRUYNE\></strong> I honestly cannot remember you asking me :-P  
<strong>\* fluffypony</strong> has the IRC logs to prove it :-P  
<strong>\<dEBRUYNE\></strong> regardless, I think xmrpromotions was handling most of that :-P  
<strong>\<fluffypony\></strong> ok - xmrpromotions, did you have a chance to look at GNU Social ?  
<strong>\<ArticMine\></strong> I am looking at GNU social right now  
<strong>\<xmrpromotions\></strong> I am sorry but I have not  
<strong>\<meeting-bot\> \[anonimal\]</strong> Can I ask everone, candidly, what they think of the idea?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Is it something worth pursuing?  
<strong>\<ArticMine\></strong> My initial instinct is yes  
<strong>\<fluffypony\></strong> tbh I had hardly heard about GNU Social till you brought it up  
<strong>\<xmrpromotions\></strong> Are there more details I can read about it? <https://github.com/monero-project/kovri/issues/105>  
<strong>\<fluffypony\></strong> but I think in terms of providing a more freedom-friendly social presence it’s advantageous  
<strong>\<fluffypony\></strong> plus if we can spend the energy maintaining a Facebook page we can definitely justify this… :-P  
<strong>\<ArticMine\></strong> Way better than a Facebook page  
<strong>\<ArticMine\></strong> There are many who dislike the corporate centralization of Facebook in social media  
<strong>\<meeting-bot\> \[anonimal\]</strong> xmrpromotions: A great example of a working instance is <https://quitter.se/>  
<strong>\<<strong>uguu</strong>\></strong> facebook is currently actively banning users that talk about the censorship too so…  
<strong>\<meeting-bot\> \[anonimal\]</strong> xmrpromortions: For technical details, <https://gnu.io/social/>  
<strong>\<meeting-bot\> \[anonimal\]</strong> lol, sorry, not auto-completion here  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yes, recent news items re: censorship just get crazier and crazier.  
<strong>\<xmrpromotions\></strong> Thank you I will read the details and be ready to comment later. It is too early for me to commit to anything quite yet  
<strong>\<meeting-bot\> \[anonimal\]</strong> And the social monopolies are finally showing their true colors.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so \#105 is on hold pending xmrpromotions’ review?  
<strong>\<fluffypony\></strong> yup  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, next ticket.  
<strong>\<fluffypony\></strong> ok  
<strong>\<meeting-bot\> \[anonimal\]</strong> \#46  
<strong>\<meeting-bot\> \[anonimal\]</strong> The Kovri website.  
<strong>\<fluffypony\></strong> \#46 - does anyone have any strong opinions on whether it should be a page on the Monero website, or a separate site that matches the Monero site’s look and feel (maybe with different colours), or a completely unrelated site ?  
<strong>\<fluffypony\></strong> anonimal: and your input on this would be appreciated too  
<strong>\<fluffypony\></strong> I think the relay is wonky  
<strong>\<meeting-bot\> \[anonimal\]</strong> What’s the time-cost in terms of managing two sites?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yes, missed almost everything it looks like.  
<strong>\<fluffypony\></strong> anonimal: it’s mostly just the initial work, after that I mostly go hands-off and let the community run with the content  
<strong>\<meeting-bot\> \[anonimal\]</strong> Can anyone read this?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so could we start small with a page on the website, or maybe subdomain/ and if things get bigger move onto another site?  
<strong>\<fluffypony\></strong> that would be my recommendation  
<strong>\<fluffypony\></strong> we start with a sub-section on the Monero site  
<strong>\<fluffypony\></strong> and forward the kovri site through to it  
<strong>\<fluffypony\></strong> if we feel the need later on we can create a separate site on its own  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, sounds good to me. Anyone else?  
<strong>\<xmrpromotions\></strong> Of the three options mentioned a separate site that matches the Monero site’s look and feel may help draw a wider audience than a page on the Monero site while at the same time anyone who visits the Kovri page knows that Monero is associated with it  
<strong>\<xmrpromotions\></strong> It seems like a judgement call to me. Either plan sounds reasonable  
<strong>\<fluffypony\></strong> restarting meeting bot  
<strong>\<fluffypony\></strong> in fact, if you want to write up some content for me I’ll do it on the plane on Tuesday  
<strong>\<fluffypony\></strong> in fact, I can probably take most of it from the readme  
<strong>\<fluffypony\></strong> in fact, if I say in fact again I’ll summon the in-fact-bot  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, ideas for content? I can blabber but ideas are welcome.  
<strong>\<meeting-bot\> \[anonimal\]</strong> ping in-fact-bot  
<strong>\<xmrpromotions\></strong> Any thoughts on creating a stackexchange proposal for I2P? Tor has a page now <https://area51.stackexchange.com/proposals/56447/tor> and we should be able to reach the commitment stage quickly with the same supporters behind the Monero proposal?  
<strong>\<fluffypony\></strong> xmrpromotions: we’d have to run it past zzz, at the very least  
<strong>\<meeting-bot\> \[fluffypony\]</strong> zzz ^^  
<strong>\<xmrpromotions\></strong> sorry for off topic idea. I can table it for later if appropriate  
\*\*\<fluffypony\> no I think it’s an excellent idea, if the i2p community at large is interested then now is definitely the time  
<strong>\<meeting-bot\> \[anonimal\]</strong> From what I’ve seen, alot of great ideas come and go through \#i2p-dev but it always comes down to resources.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I think we’d all love that but someone will have to take the initiative.  
<strong>\<xmrpromotions\></strong> I will take the initiative on that  
<strong>\<meeting-bot\> \[anonimal\]</strong> AFAICT all i2p-related dev (including Kovri) is in a bit of a dry spell so, priorities.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I like the idea though.  
<strong>\<fluffypony\></strong> anonimal: the advantage is that we can basically get everyone who’s committed to the Monero proposal to also back an i2p proposal  
<strong>\<fluffypony\></strong> but now is the time to do so  
<strong>\<fluffypony\></strong> whilst everyone’s excited  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so what’s the next step?  
<strong>\<xmrpromotions\></strong> If the I2P communty supports it. As fluffypony said now is the time as the synergy will help both I2P and Monero proposals pass faster for REP related reasons  
<strong>\<fluffypony\></strong> so basically next step on the website is let’s get a bit of content and I’ll put it together on the plane on Tuesday  
<strong>\<fluffypony\></strong> next step on the StackExchange proposal is to wait for feedback from zzz  
<strong>\<xmrpromotions\></strong> sounds good. I wont act until I hear confirmation that zzz is ready to proceed  
<strong>\<meeting-bot\> \[anonimal\]</strong> I dropped a line in \#i2p-dev.  
<strong>\<meeting-bot\> \[anonimal\]</strong> We’ll see who bites.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so \#46: 1) create content 2) On Tuesday, fluffypony will put something together 3) ETA after that?  
<strong>\<fluffypony\></strong> ok next ticket ?  
<strong>\<fluffypony\></strong> oh  
<strong>\<fluffypony\></strong> once it’s pushed to the repo it goes live  
<strong>\<fluffypony\></strong> there’s no ETA beyond that  
<strong>\<fluffypony\></strong> or no steps beyond pulling it and rebuilding the Jekyll site  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok great, I’ll paste a note in ticket.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Moving on, \#43.  
<strong>\<fluffypony\></strong> ok - can we just use the Monero addresses, or do we want separate addresses?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m fine with Monero addresses.  
<strong>\<fluffypony\></strong> ok then they’re avialable here, anonimal: <http://donate.getmonero.org>  
<strong>\<fluffypony\></strong> \*available  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok. Also, I can apply for FFS when needed or include my address somewhere or we can simply put a note in README to donate to either. Sound fair?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Or no?  
<strong>\<othe\></strong> ffs is prolly more efficient  
<strong>\<fluffypony\></strong> FFS is better than direct donations  
<strong>\<fluffypony\></strong> and it’s generally more trustworthy because you raise funds for a specific piece of work, and then get paid out on milestones  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, we should put a note in README directing to FFS and donation page or just FFS?  
<strong>\<fluffypony\></strong> the readme just needs the donation page  
<strong>\<fluffypony\></strong> if we get large donations we redistribute them to active FFS proposals anyway  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: Ok, would you like to add that with your wording to the README? Or should I?  
<strong>\<fluffypony\></strong> anonimal: I have to pack tomorrow, and have a bunch of things to do, so if you could that would be appreciated  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok  
<strong>\<meeting-bot\> \[anonimal\]</strong> Moving on, \#27  
<strong>\<fluffypony\></strong> ok \#27 is going to have to hold for a week or two, we’re busy moving email providers on getmonero.org so I’ll sort it out on the new provider  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, I’ll paste that note.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Onward to \#20.  
<strong>\<fluffypony\></strong> 20 - I can try Coverity again, let’s see if it gives me the same issue  
<strong>\<fluffypony\></strong> I’ve not heard from them despite opening tickets etc.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Links? Maybe I can comment/ping them too.  
<strong>\<fluffypony\></strong> anonimal: screenshots and process I followed is in that ticket  
<strong>\<fluffypony\></strong> issue I mean  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, well, it may come down to a phone call or two.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Is that something you’d be willing to do?  
<strong>\<meeting-bot\> \[anonimal\]</strong> If not, we can skip the integration and try to do it manually.  
<strong>\<fluffypony\></strong> sure  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, next. \#90 is not assigned to you but I remember you said you would assign yourself.  
<strong>\<fluffypony\></strong> one second just checking coverity  
<strong>\<meeting-bot\> \[anonimal\]</strong> Is \#90 still of interest?  
<strong>\<fluffypony\></strong> oooooh it works  
<strong>\<fluffypony\></strong> they must’ve fixed it and just not let us know  
<strong>\<fluffypony\></strong> anonimal: I’ll PM you with coverity details  
<strong>\<meeting-bot\> \[anonimal\]</strong> Fantastic\!  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yay, great. This should be interesting.  
<strong>\<gingeropolous\></strong> will I break things if I create a bridge by connecting simplewallet to the daemon over an i2p tunnel?  
<strong>\<fluffypony\></strong> doubtful  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: \#90?  
<strong>\<fluffypony\></strong> 90 will happen automagically when our GitLab mirror is up  
<strong>\<fluffypony\></strong> it’ll have clearnet / Tor / i2p mirrors  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok then. I’ve missed any discussions about that in the past, is there an ETA?  
<strong>\<fluffypony\></strong> not at the moment - it’s one of those “on the list” things, I lack the time to knuckle down and do it  
<strong>\<fluffypony\></strong> we need a devops team :-P  
<strong>\<meeting-bot\> \[anonimal\]</strong> Indeed. Ok, I’ll add a note in ticket.  
<strong>\<meeting-bot\> \[anonimal\]</strong> To whom should we assign \#90 then?  
<strong>\<fluffypony\></strong> me  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, will do.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yay, hour long of fluffypony tickets finally tackled\! I’m glad we finally had the time. Any other comments them?  
<strong>\<fluffypony\></strong> none from my side  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, since this was the “fluffypony show” meeting, for time-sake I’ll sum up my part of 1. with one line:  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m not working on any tickets ATM but what will most likely be a new ticket soon as I’m working on Transports (mostly NTCP, little SSU): debugging/refactoring/c++14 refactoring where appropriate/some rewrite/some new code/documentation/improved logging  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, that’s that for now, I’m sure more code talk can be at the next meeting.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Any additional meeting items (quickly)?  
<strong>\<fluffypony\></strong> nothing more from me  
<strong>\<meeting-bot\> \[anonimal\]</strong> Re: StackExchange, what tl;dr can I give to \#i2p-dev?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Aside from pointing a link to the meeting log.  
<strong>\<meeting-bot\> \[anonimal\]</strong> (I’ve been out of the loop re: the initiative)  
<strong>\<xmrpromotions\></strong> Just say that we are willing to cross promote it to XMR community and expect it to reach the commitment stage fairly fasy  
<strong>\<xmrpromotions\></strong> fast  
<strong>\<meeting-bot\> \[fluffypony\]</strong> just that it’s a proposal to have an i2p-specific StackExchange area  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, what should we expect from them?  
<strong>\<xmrpromotions\></strong> from there the I2P and XMR communities can help each other ensure both site reach beta  
<strong>\<xmrpromotions\></strong> Hard for me to make an ETA on that. End result would be an I2P site similar to what Tor has now  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: should we end meeting?  
<strong>\<meeting-bot\> \[anonimal\]</strong> (or has it ended?)  
<strong>\<meeting-bot\> \[fluffypony\]</strong> yes I think so  
<strong>\<meeting-bot\> \[fluffypony\]</strong> I’ll take the bot down  
<strong>\<xmrpromotions\></strong> We need I2P experts to appear during the proposal stage once created to ask good questions  
<strong>\<xmrpromotions\></strong> early questions attract a lot more votes and rise to the top, so quality matters  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, I’ll chat in \#monero-dev.  
<strong>\<i2p-relay\> {-anonimal}</strong> \* thinking  
<strong>\<i2p-relay\> {-anonimal}</strong> xmrpromotions: I can commit to both pages. How many I2P ‘experts’ would need to commit?  
<strong>\<xmrpromotions\></strong> well we need 40 good questions. each person can only ask 5  
<strong>\<fluffypony\></strong> well before commitment it’s just the voting section  
<strong>\<xmrpromotions\></strong> Our initial 40 questions will help with SEO after launch  
<strong>\<fluffypony\></strong> where we need not only good questions asked, but also good questions have to get 10 votes each  
<strong>\<xmrpromotions\></strong> Yes I mean we need to create quality questions to vote on  
<strong>\<xmrpromotions\></strong> If someone wants to create a list of 40 great questions that would be perfect  
<strong>\<i2p-relay\> {-anonimal}</strong> 40 great I2P questions, I could do that.  
<strong>\<fluffypony\></strong> they still have to post them though  
<strong>\<xmrpromotions\></strong> then we can divide it up and ask 5 each to make sure no silly questions gain a lot of votes early in the process  
<strong>\<xmrpromotions\></strong> we can find 8 people to post 5 questions each easily  
<strong>\<fluffypony\></strong> yup  
<strong>\<fluffypony\></strong> yeah, then we need a bunch of people to upvote :)  
<strong>\<xmrpromotions\></strong> I dont think voting will be a problem either. XMR users with no rep can be assigned to ask the questions… that will give them 5x10x5 rep (250 each)  
<strong>\<xmrpromotions\></strong> which will give them more than enough for the 200 rep area 51 cutoff for the SE 100 rep account association bonus  
<strong>\<fluffypony\></strong> strategyyyy  
<strong>\<xmrpromotions\></strong> 5q with 10 votes each will earn 5 rep per vote  
<strong>\<i2p-relay\> {-anonimal}</strong> Ok, sounds great. Right now, I need to finish post-meeting wrap-up, take a break, get my brain in order and bbl.  
<strong>\<fluffypony\></strong> ok cool  
<strong>\<xmrpromotions\></strong> I will make a post in the getmonero forums. Maybe we can create and agree on a list of 40 questions there before we start  
<strong>\<xmrpromotions\></strong> thanks everyone. have a great weekend  
\*\*\<fluffypony\>\*\* cheers
