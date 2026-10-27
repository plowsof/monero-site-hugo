---
title: Logs for the Kovri Dev Meeting Held on 2016-07-31
summary: Brief review of what has been completed since last meeting, and Kovri Logo
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Logs

<strong>\<anonimal\></strong> ping fluffypony we missed you in \#monero-dev  
<strong>\<anonimal\></strong> I'll proceed with the meeting as planned but the bulk of the agenda is picking on your assigned issues.  
<strong>\<anonimal\></strong> <https://github.com/monero-project/kovri/issues/216>  
<strong>\<anonimal\></strong> Meeting Agenda: Sunday, July 31st, 17:00 UTC  
<strong>\<anonimal\></strong> 1. Greetings  
<strong>\<anonimal\></strong> 2. Brief review of what's been completed since the previous meeting  
<strong>\<anonimal\></strong> 3. Discuss Kovri logo  
<strong>\<anonimal\></strong> 4. Closing \#271  
<strong>\<anonimal\></strong> 5. Closing \#226  
<strong>\<anonimal\></strong> 6. Closing \#105  
<strong>\<anonimal\></strong> 7. Closing \#46  
<strong>\<anonimal\></strong> 8. Closing \#27  
<strong>\<anonimal\></strong> 9. Any additional meeting items  
<strong>\<anonimal\></strong> 10. Confirm next meeting date/time  
<strong>\<anonimal\></strong> Hi.  
<strong>\<i2p-relay\> {-needmoney90}</strong> \_ walks into the room and sits in the nearest available seat  
<strong>\<i2p-relay\> {-needmoney90}</strong> Just watching for today  
<strong>\<anonimal\></strong> Is anyone freenode side? This meeting is not being relayed to \#monero-dev. I'll hop onto slack to see if the relay is working.  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> It appears so  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> I2P, Slack, and IRC are all relaying  
<strong>\<anonimal\></strong> K, thanks.  
<strong>\<anonimal\></strong> Onto point 2.  
<strong>\<anonimal\></strong> $ git log --no-merges --pretty=oneline --since=1.month \| wc -l  
<strong>\<anonimal\></strong> 72  
<strong>\<anonimal\></strong> Code highlights include:  
<strong>\<anonimal\></strong> - Mem leak fixes  
<strong>\<anonimal\></strong> - New constant-time comparison for ed25519  
<strong>\<anonimal\></strong> - Two new contributors: moneromooo and rakhimov  
<strong>\<anonimal\></strong> (hopefully will see more from both devs)  
<strong>\<anonimal\></strong> - regex fix, clang fixes  
<strong>\<anonimal\></strong> - A whole lot of build/repo work  
<strong>\<anonimal\></strong> - We officially build with clang  
<strong>\<anonimal\></strong> - We officially build on OSX again  
<strong>\<anonimal\></strong> - Two new submodules: cpp-netlib, cryptopp  
<strong>\<anonimal\></strong> - New URI parsing implementation courtesy of cpp-netlib  
<strong>\<anonimal\></strong> - New clang-format config (still in development)  
<strong>\<anonimal\></strong> - Updated style guide + building instructions + docs  
<strong>\<anonimal\></strong> - Upstream bug hunting/fixing (huge time-suck)  
<strong>\<anonimal\></strong> - Coverity's website finally works (for me)  
<strong>\<anonimal\></strong> - Misc fixes, enhancements  
<strong>\<anonimal\></strong> Project highlights include:  
<strong>\<anonimal\></strong> - Kovri End-User Documentation Proposal - \#256  
<strong>\<anonimal\></strong> - 9 new opened issues, 7 new closed issues  
<strong>\<anonimal\></strong> - Creation of @<kovri@quitter.se>  
<strong>\<anonimal\></strong> - I've also spent some time with bitmonero/monero-project  
<strong>\<anonimal\></strong> That's all from me for 2. Anyone else?  
<strong>\<anonimal\></strong> Ok, guess not.  
<strong>\<anonimal\></strong> fluffypony fluffypony fluffypony fluffypony  
<strong>\<i2p-relay\> {-needmoney90}</strong> \_ summons fluffypony from the depths  
<strong>\<anonimal\></strong> 2nd meeting in a row he's missed. I hope he's alive.  
<strong>\<i2p-relay\> {-needmoney90}</strong> D:  
<strong>\<anonimal\></strong> I know this is opensource and volunteer but I'm getting a bit irritated.  
<strong>\<anonimal\></strong> Being stood up is not very respectful.  
<strong>\<i2p-relay\> {-needmoney90}</strong> oh he isnt in this room  
<strong>\<i2p-relay\> {-needmoney90}</strong> summoning wont work from here  
<strong>\<anonimal\></strong> lol needmoney90  
<strong>\<i2p-relay\> {-needmoney90}</strong> He isn’t even on IRC it seems  
<strong>\<i2p-relay\> {-needmoney90}</strong> hm  
<strong>\<i2p-relay\> {-needmoney90}</strong> thats strange, Im used to him being always on/ide  
<strong>\<i2p-relay\> {-needmoney90}</strong> idle  
<strong>\<anonimal\></strong> He's on irc2p side.  
<strong>\<anonimal\></strong> Is dEBRUYNE on freenode side? Is this meeting even being logged?  
<strong>\<i2p-relay\> {-needmoney90}</strong> Well, Slack is certainly logging it  
<strong>\<i2p-relay\> {-needmoney90}</strong> and my client possibly is  
<strong>\<i2p-relay\> {-needmoney90}</strong> havent checked logging settings  
<strong>\<Zenified\></strong> so is my client  
<strong>\<anonimal\></strong> Ok.  
<strong>\<anonimal\></strong> Moving on to 3.  
<strong>\<anonimal\></strong> "Discuss Kovri logo"  
<strong>\<anonimal\></strong> Who did Monero's logo?  
<strong>\* anonimal:</strong> asked in \#monero-dev, no response  
<strong>\<anonimal\></strong> Any thoughts on a logo for Kovri?  
<strong>\<anonimal\></strong> How about a nude porn star holding a letter 'K'?  
<strong>\<i2p-relay\> {-needmoney90}</strong> I've been thinking about it  
<strong>\<i2p-relay\> {-needmoney90}</strong> and….I don’t think that will get us corporate/mainstream usage  
<strong>\<i2p-relay\> {-needmoney90}</strong> then again, maybe it will  
<strong>\<i2p-relay\> {-needmoney90}</strong> keep it on the backburner  
<strong>\<anonimal\></strong> lol  
<strong>\* anonimal:</strong> was joking  
<strong>\<i2p-relay\> {-needmoney90}</strong> I’ve been thinking some kind of K made of nodes (like the Ethereum Classic logo), but fading out on half  
<strong>\<i2p-relay\> {-needmoney90}</strong> though its probably too complex  
<strong>\<i2p-relay\> {-needmoney90}</strong> <https://camo.githubusercontent.com/eec95efca3ae789116e4557656898ab52ca74cba/687474703a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f3830302f312a6e4955617a775f75334b436843583839664c674c44672e706e67>  
<strong>\<anonimal\></strong> Sounds cool.  
<strong>\<anonimal\></strong> DaveyJones pointed this out <https://99designs.de/logo-design/contests/monero-mro-cryptocurrency-logo-design-contest-382486>  
<strong>\<anonimal\></strong> needmoney90: could that url get any longer?...  
<strong>\<anonimal\></strong> Ah, I see. Interesting idea needmoney90  
<strong>\<anonimal\></strong> Maybe we should hold a contest and reward the winner with XMR?  
<strong>\<i2p-relay\> {-needmoney90}</strong> Sorry about the URL length, I copypasta’d without minifying  
<strong>\<anonimal\></strong> Np.  
<strong>\<anonimal\></strong> Where would be a good place to host a Kovri logo contest?  
<strong>\<anonimal\></strong> (XMR friendly place)  
<strong>\<anonimal\></strong> I'll open a ticket and we can deal with it later  
<strong>\<anonimal\></strong> Points 4-8 are all fluffypony  
<strong>\<anonimal\></strong> 9. Any addition meeting items  
<strong>\<i2p-relay\> {-needmoney90}</strong> None here  
<strong>\<anonimal\></strong> EinMByte is MIA. SSU still not finished. From what I've worked on, debugging the rest to get it merged will require motivation on my part.  
<strong>\<i2p-relay\> {-needmoney90}</strong> SSU?  
<strong>\<anonimal\></strong> No shows at meetings + no pay \!= motivation for me to do lifting beyond what I'm doing.  
<strong>\* anonimal:</strong> grabs link for needmoney90  
<strong>\<anonimal\></strong> needmoney90: \#140  
<strong>\<i2p-relay\> {-needmoney90}</strong> tanks  
<strong>\<anonimal\></strong> I'll make myself available for the next 30 minutes and then paste a link to the meeting log in \#216  
<strong>\<i2p-relay\> {-needmoney90}</strong> I’m really curious where fluffy got off to..  
<strong>\<anonimal\></strong> We were chatting about an hour before monero's meeting was supposed to start  
<strong>\<anonimal\></strong> Maybe he simply forget. This has happened several times in the past.  
<strong>\<i2p-relay\> {-needmoney90}</strong> :(  
<strong>\<i2p-relay\> {-\_Slack} \<anonimal\></strong> needmoney90: is there a way to easily export channel logs here?  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> hrmmm  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> I just exported  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> should have the logs (from all channels) in my email soon  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> barring that, someone's IRC client logs will work  
<strong>\<i2p-relay\> {-\_Slack} \<anonimal\></strong> Nice. Would it be easy to fpaste a private paste of just our meeting? e.g., do they do any formatting or just lump everything into an email?  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> no idea  
<strong>\<i2p-relay\> {-\_Slack} \<needmoney90\></strong> ill let you know  
<strong>\<i2p-relay\> {-\_Slack} \<anonimal\></strong> Thanks. For the time being I'll just do a quick format of my logs to takeout timestamps and paste the meeting.
