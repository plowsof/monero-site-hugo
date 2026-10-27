---
title: Overview and Logs for the Dev Meeting Held on 2019-04-07
summary: Point release discussions, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<hyc\></strong> so, no meeting today?  
<strong>\<hyc\></strong> gingeropolous: you there?  
<strong>\<rehrar\></strong> I know you gys had a meeting last week  
<strong>\<rehrar\></strong> but it was impromptu, correct?  
<strong>\<rehrar\></strong> if we want dev meetings to stay on the weeks that community ones are not, then it should be today, since community meeting is next week  
<strong>\<rehrar\></strong> we can do a short one if there's not much to discuss  
<strong>\<rehrar\></strong> thoughts hyc?  
<strong>\<rehrar\></strong> the choice is up to you  
<strong>\<hyc\></strong> short meeting is prob a good idea just to touch base  
<strong>\<hyc\></strong> see how the point release is shaping up  
<strong>\<rehrar\></strong> hyc has spoken  
<strong>\<rehrar\></strong> we'll wait until designated time  
<strong>\<hyc\></strong> would be good to get back onto regular schedule  
<strong>\<dEBRUYNE\></strong> I did kind of announce it on github :P  
<strong>\<dEBRUYNE\></strong> So not sure if it is impromptu  
<strong>\<rehrar\></strong> then I was just out of it that week and didn't notice  
<strong>\<rehrar\></strong> but I prefer to fault others than myself, so if you could take the blame dEBRUYNE I'd appreciate that  
<strong>\<dEBRUYNE\></strong> :D  
<strong>\<hyc\></strong> anything else for today's agenda?  
<strong>\<rehrar\></strong> 1. Greetings? :D  
<strong>\<hyc\></strong> oh yeah, I always forget the social conventions  
<strong>\<rehrar\></strong> 2. Point release items  
<strong>\<rehrar\></strong> moneromooo around? dsc\_ too  
<strong>\<rehrar\></strong> ping the other peoples  
<strong>\<vtnerd\_\_\></strong> hello  
<strong>\<selsta\></strong> GUI is almost ready for 0.14.1  
<strong>\<rehrar\></strong> bam, thanks selsta  
<strong>\<rehrar\></strong> and that will have Trezor, yeah?  
<strong>\<selsta\></strong> yes  
<strong>\<rehrar\></strong> I don't own one, so it's not a big deal for me, but I'll have an answer for people  
<strong>\<rehrar\></strong> anyone to do a quick update on Monero Core?  
<strong>\<rehrar\></strong> also, what is the name for the core software? Can we name it?  
<strong>\<rehrar\></strong> We've had this discussion a lot of times.  
<strong>\<jwinterm\></strong> monerod and monero-wallet-cli?  
<strong>\<rehrar\></strong> yes  
<strong>\<rehrar\></strong> alright, good talk everyone  
<strong>\<sgp\_\></strong> hello everyone  
<strong>\<hyc\></strong> point release doesn't get a new name  
<strong>\<hyc\></strong> it's still Bron Butterfly  
<strong>\<hyc\></strong> Boron  
<strong>\<rehrar\></strong> I meant monero core software hc  
<strong>\<rehrar\></strong> \*hyc  
<strong>\<hyc\></strong> oh  
<strong>\<sgp\_\></strong> More than the "daemon" and "CLI"?  
<strong>\<hyc\></strong> what's wrong with calling it core?  
<strong>\<rehrar\></strong> nothing, I guess. I just don't know that there's one thing that people agree on.  
<strong>\<rehrar\></strong> well, doesn't seem there's anyone around to update on Monero core  
<strong>\<rehrar\></strong> selsta: anything else on the GUI. When expected to be done?  
<strong>\<rehrar\></strong> if someone wants to update on core whenever they have the time, that'd be cool.  
<strong>\<hyc\></strong> looks like nothing else then  
<strong>\<moneromooo\></strong> By core, you mean the GUI or not the GUI ?  
<strong>\<moneromooo\></strong> It's confusing because some people mean not the GUI now.  
<strong>\<dEBRUYNE\></strong> the 'monero' repository I guess :P  
<strong>\<ErCiccione\[m\]\></strong> well, with rights, since the GUI was called monero-corefor long time  
<strong>\<dEBRUYNE\></strong> ^ moneromooo  
<strong>\<hyc\></strong> but it's called monero-gui now so ...  
<strong>\<rehrar\></strong> it made no sense that the GUI was ever called core  
<strong>\<hyc\></strong> god only knows why someone thought "hey let's make a gui but not call it the gui\!"  
<strong>\<dEBRUYNE\></strong> I can give some further updates on the GUI once mooo is done with the core stuff :p  
<strong>\<rehrar\></strong> Can we all agree between us present that core means CLI tools and daemon?  
<strong>\<ErCiccione\[m\]\></strong> isn't just linked hyc? IIRC it should still take you to the GUI if you look for monero-project/monero-core  
<strong>\<rehrar\></strong> and GUI means GUI?  
<strong>\<jwinterm\></strong> most applications with GUIs are not called by their function+GUI, probably  
<strong>\<ErCiccione\[m\]\></strong> i confirm monero-core still points to monero-gui  
<strong>\<rehrar\></strong> oof. I'll restart the conversation again on github issue or something in regards to naming  
<strong>\<rehrar\></strong> either way, moneromooo is it possible to tell us where point release is at for CLI/core stufs?  
<strong>\<dEBRUYNE\></strong> moneromooo: My intention was to let you go first :-P  
<strong>\<hyc\></strong> jwinterm: do you find that's true for apps that have both GUI and CLI? particularly if only a CLI existed for a long time?  
<strong>\<moneromooo\></strong> We've started merging stuff before the customary 10 days wait now. I expect we'll branch soonish.  
<strong>\<moneromooo\></strong> The only thing I know of that's really needed before a branch is the new fake out selection.  
<strong>\<moneromooo\></strong> And that's PRed.  
<strong>\<moneromooo\></strong> A few nice to have are the SSL changes, the second part of the RPC tests, and possibly the pay-for-service but I think that one's unlikely to happen now.  
<strong>\<rehrar\></strong> cool, thanks  
<strong>\<ErCiccione\[m\]\></strong> i will push some translations for the CLI next week, we should have a new language available (hindi)  
<strong>\<moneromooo\></strong> So if anyone wants something in before the branch, be fast.  
<strong>\<moneromooo\></strong> And this time, there should be lots of time for translations ^\_^  
<strong>\<rehrar\></strong> maybe I'll PR a pleasant message when opening the wallet so I can get a "contributor" flair or the reddits  
<strong>\<selsta\></strong> 19:13 \<rehrar\> well, doesn't seem there's anyone around to update on Monero core \<-- All features are PRed, only missing review.  
<strong>\<ErCiccione\[m\]\></strong> moneromooo: yep, not complaining this time (yet) :D  
<strong>\<rehrar\></strong> nice  
<strong>\<rehrar\></strong> dEBRUYNE: all you  
<strong>\<dEBRUYNE\></strong> Let's see  
<strong>\<hyc\></strong> btw I hope \#5376 makes it in this round, it'll be helpful for the solo mining code  
<strong>\<jwinterm\></strong> hyc: not too many apps spring to mind that meet that criterion  
<strong>\<dEBRUYNE\></strong> Like selsta said, we should be ready in time for 0.14.1.0  
<strong>\<dEBRUYNE\></strong> There will be a revamped history page as well as a revamped address book  
<strong>\<dEBRUYNE\></strong> Xiphon has also posted a ffs to work on some stuff such as optimizing the communication between the wallet and the daemon and implementing a decentralized remote node scanner -\> <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/55>  
<strong>\<dEBRUYNE\></strong> For the latter feature, we'll have to wait a bit before nodes will start using the --public-node flag  
<strong>\<dEBRUYNE\></strong> Oh there will also be fiat pricing (the feature will be turned off by default)  
<strong>\<dEBRUYNE\></strong> And we've started discussing how to easily integrate i2p-zero and tor  
<strong>\<dEBRUYNE\></strong> ^ If anyone has suggestion on a design, feel free to list them  
<strong>\<rehrar\></strong> integrate in terms of design, yes dEBRUYNE ?  
<strong>\<dEBRUYNE\></strong> wrt i2p, I think the easiest would be the bundle the i2p binary with the GUI binary and then have a checkbox on the settings page to start it  
<strong>\<dEBRUYNE\></strong> Yeah  
<strong>\<dEBRUYNE\></strong> The new white theme may also be included in the point release btw (vid from dsc here -\> <https://www.youtube.com/watch?v=gTLNwRaoa4s>)  
<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> ooh, that's kind of cool  
<strong>\<dEBRUYNE\></strong> That's it basically :-P  
<strong>\<rehrar\></strong> cool  
<strong>\<rehrar\></strong> anything else from anyone?  
<strong>\<rehrar\></strong> I said we could keep it short. :)  
<strong>\<hyc\></strong> let's call it  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Cool. Two weeks from now. Same time. See you all then.  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Oh, those who have used the new CCS. How was it?  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> To donate or to put up a proposal?  
<strong>\<ErCiccione\[m\]\></strong> just quickly:  
<strong>\<ErCiccione\[m\]\></strong> The guide for the GUI is completed, thanks to el00ruobuob, it only needs to be built and translated, but it can be included with next release :)  
<strong>\<ErCiccione\[m\]\></strong> <https://github.com/monero-ecosystem/monero-GUI-guide>  
<strong>\<ErCiccione\[m\]\></strong> reviews and features/suggestions are always welcome  
<strong>\<ErCiccione\[m\]\></strong> rehrar: I think it's a great improvement in terms of usability for the community, still needs some tweaking, but i think it's a huge improvement  
<strong>\<dEBRUYNE\></strong> ErCiccione\[m\]: Doesn't the ecosystem repo already have the Monero heart logo btw? :P  
<strong>\<ErCiccione\[m\]\></strong> dEBRUYNE: yes, but i thought would be cool to have a personalized logo. I'd like the Ecosystem Project to grow with time  
<strong>\<dEBRUYNE\></strong> The hear tlogo kind of grew on me :-P  
<strong>\<ErCiccione\[m\]\></strong> eheh i can't deny i would miss it
