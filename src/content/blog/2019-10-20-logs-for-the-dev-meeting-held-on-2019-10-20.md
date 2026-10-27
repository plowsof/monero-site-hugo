---
title: Overview and Logs for the Dev Meeting Held on 2019-10-20
summary: Development status, 0.15 release discussion, Network upgrade naming, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<rehrar\></strong> Alright everyone. 17 UTC.  
<strong>\<rehrar\></strong> Meeting time.  
<strong>\<rehrar\></strong> 1. Greetings  
<strong>\<hyc\></strong> hey  
<strong>\<rbrunner\></strong> Hi  
<strong>\<kinghat\></strong> \\o/  
<strong>\<rehrar\></strong> small crowd today?  
<strong>\<sech1\></strong> hi  
<strong>\<rehrar\></strong> well, perhaps people will trickle in.  
<strong>\<rehrar\></strong> Two weeks ago I was at HCPP, so I wasn't able to be here for a meeting. Was there one?  
<strong>\<dEBRUYNE\></strong> I am here  
<strong>\<rbrunner\></strong> No, neither 1 week ago  
<strong>\<dEBRUYNE\></strong> I think we decided to postpone it  
<strong>\<rehrar\></strong> ok, so  
<strong>\<rehrar\></strong> 2. What's been completed since the previous meeting (a month ago)  
<strong>\<hyc\></strong> a lot of PRs got merged  
<strong>\<hyc\></strong> has the v12 forkheight been merged?  
<strong>\<moneromooo\></strong> You can now sync off pruned nodes.  
<strong>\<moneromooo\></strong> Not yet.  
<strong>\<dEBRUYNE\></strong> I think that will probably be on the last merge list before we branch  
<strong>\<dEBRUYNE\></strong> ^ rehrar  
<strong>\<moneromooo\></strong> vtnerd\_\_: do you intend your latest network changes to go in for the fork ?  
<strong>\<vtnerd\_\_\></strong> the one that is up for review, yes that would be the hope (provided its determined to be ready)  
<strong>\<vtnerd\_\_\></strong> its not needed for the hardfork, so if you feel it should wait, then my recommendation would be to wait for a point release  
<strong>\<vtnerd\_\_\></strong> the problem is that re-testing some of your recommendations are likely to take up time before the upcoming branch, but I will try  
<strong>\<moneromooo\></strong> I think that and pay-for-service are the only large ones left.  
<strong>\<moneromooo\></strong> Oh, and the defer tx verification one. Not huge either but a bit substantial.  
<strong>\<rehrar\></strong> are either of those expected to be in?  
<strong>\<moneromooo\></strong> Hopefully all of them.  
<strong>\<moneromooo\></strong> pay-for-service goes next, I've kept it waiting for long enough.  
<strong>\<hyc\></strong> sounds good  
<strong>\<rbrunner\></strong> Did I get that right that a PR is waiting in that batch that will cause testnet to reorg back to some much earlier blockheight?  
<strong>\<hyc\></strong> not that I've seen  
<strong>\<hyc\></strong> ?  
<strong>\<rbrunner\></strong> Maybe I misunderstood then, while reading something up here  
<strong>\<moneromooo\></strong> I said so, but I was wrong. The rules are different, but actually coincide in practice.  
<strong>\<rbrunner\></strong> Surprising  
<strong>\<rbrunner\></strong> All the better  
<strong>\<moneromooo\></strong> They'll stop conciding whe nthe block size shoots up.  
<strong>\<rbrunner\></strong> So we only need some seed nodes working for testnet ... caugh ... caugh  
<strong>\<moneromooo\></strong> gingeropolous added one, that'll be merged soon.  
<strong>\<rbrunner\></strong> Nice  
<strong>\<hyc\></strong> dEBRUYNE: didn't you get hold of fluffypony regarding seed nodes?  
<strong>\<dEBRUYNE\></strong> He posted an update here 1-2 days ago  
<strong>\<dEBRUYNE\> \<fluffypony\></strong> re: testnet nodes, I've been having some issues with the boxes I run, but there are other people running testnet nodes besides me  
<strong>\<hyc\></strong> ah, I missed that. ok  
<strong>\<rbrunner\></strong> Especially nice that stagenet gets a third seed node, with the only two so far probably just sitting side-by-side and offering zero redundancy  
<strong>\<rbrunner\></strong> well, not zero, but you get what I mean ...  
<strong>\<rehrar\></strong> Anything else of note to discuss on what's been done this past month?  
<strong>\<hyc\></strong> sounds like not  
<strong>\<rehrar\></strong> Alrighty.  
<strong>\<rehrar\></strong> 3. Fork related things  
<strong>\<rehrar\></strong> is there anything that is needed, desired, wanted, or otherwise needs to be discussed regarding the upcoming fork.  
<strong>\<tevador\></strong> FYI, there will be probably RandomX 1.1.5 with some OpenBSD-related fixes  
<strong>\<tevador\></strong> but best if 1.1.4 is merged first (1.1.5 doesn't need any changes in monero code)  
<strong>\<hyc\></strong> that's PR\#5980 for v1.1.4  
<strong>\<tevador\></strong> yes  
<strong>\<rehrar\></strong> ok, no other fork related topics? If not we can move on.  
<strong>\<rehrar\></strong> Zipping through this meeting.  
<strong>\<rehrar\></strong> is anyone from GUI here? dsc\_ selsta  
<strong>\<selsta\></strong> yes we only had bug fixes recently  
<strong>\<selsta\></strong> GUI is ready for v0.15  
<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> 4. Any Ticket/PR related questions?  
<strong>\<rbrunner\></strong> By the way, is there already a final name for the release? I could use it for adjusting the Windows installer. Is it now crab something?  
<strong>\<hyc\></strong> carbon crab?  
<strong>\<hyc\></strong> I don't recall a final name decision  
<strong>\<rbrunner\></strong> Yeah, that one  
<strong>\<rehrar\></strong> Where was the discussion?  
<strong>\<rbrunner\></strong> Me neither, that's why I ask for sure  
<strong>\<rehrar\></strong> We can make a decision here.  
<strong>\<rbrunner\></strong> I think there was some chatter in a Reddit thread once  
<strong>\<hyc\></strong> I think some names got tossed around in this channel a few weeks ago. but nothing decided.  
<strong>\<moneromooo\></strong> camelopardalis is satifyingly complicated.  
<strong>\<rehrar\></strong> you guys want to decide now? Or not urgent?  
<strong>\<hyc\></strong> oh yeah, that was my suggestion  
<strong>\<moneromooo\></strong> I think pony likes to leave it for a reddit vote where people can't break things  
<strong>\<hyc\></strong> we can do it now, there seems to be enough people present  
<strong>\<hyc\></strong> ah  
<strong>\<dEBRUYNE\></strong> Pony usually makes a Github thread and links that to reddit iirc  
<strong>\<rbrunner\></strong> I would also prefer a Reddit thread, more fun for the fans, so to say  
<strong>\<dEBRUYNE\></strong> (re: name)  
<strong>\<rbrunner\></strong> But why not soon, e.g. tomorrow  
<strong>\<tevador\></strong> does the 24th Oct code freeze still apply?  
<strong>\<tevador\></strong> (it should)  
<strong>\<hyc\></strong> there was a mention of name on reddit <https://www.reddit.com/r/Monero/comments/d884zt/preliminary\_information\_thread\_regarding\_the/f2zfmr1/>  
<strong>\<hyc\></strong> but pretty sure that was just relaying a suggestion from here on IRC  
<strong>\<rehrar\></strong> I can make a meta issue and link to it on the Reddit  
<strong>\<hyc\></strong> cool  
<strong>\<rbrunner\></strong> Yeah that was me, but I forgot where I got that Carbon Crab  
<strong>\<rbrunner\></strong> Yes, do go ahead  
<strong>\<dEBRUYNE\></strong> rehrar: should I ask pony first if he wants to uphold the tradition?  
<strong>\<hyc\></strong> (I have the previous discussion in chat logs, was in this channel a couple weeks ago)  
<strong>\<moneromooo\></strong> Callisto alliterates nicely too fwiw.  
<strong>\<rehrar\></strong> sure  
<strong>\<rbrunner\></strong> Hmm, yes indeed  
<strong>\<rbrunner\></strong> "Crab" is very short  
<strong>\<rehrar\></strong> Is there anything else to discuss besides the naming?  
<strong>\<rehrar\></strong> Kind of a free for all time.  
<strong>\<hyc\></strong> that's always the hardest problem in computing...  
<strong>\<rbrunner\></strong> So it looks surprisingly good for this code-freeze  
<strong>\<rehrar\></strong> it's because we extended it out an extra month?  
<strong>\<rehrar\></strong> Alright, well if there's nothing else to discuss, then we can go ahead and break. Doughnuts are on the table on your way out.
