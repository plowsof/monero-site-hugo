---
title: Overview and Logs for the Dev Meeting Held on 2019-07-28
summary: Development status, Code & ticket discussion, Moving off GitHub, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<rehrar\></strong> Alright, it's time to start ladies and gentlemen.  
<strong>\<rehrar\></strong> 1. Greetings  
<strong>\<rehrar\></strong> Anybody out there?  
<strong>\<rbrunner\></strong> Nope. All people on holiday.  
<strong>\<rbrunner\></strong>  
<strong>\<vtnerd\_\_\></strong> yes  
<strong>\<rehrar\></strong> well, the three of us can have a grant ol time then  
<strong>\<rehrar\></strong> just pinging hyc moneromooo dsc\_ selsta and dEBRUYNE also  
<strong>\<rehrar\></strong> maybe a luigi1111 and fluffypony in the mix too, who knows  
<strong>\<rehrar\></strong> either way  
<strong>\<rehrar\></strong> 2. What's been completed since last meeting?  
<strong>\<dsc\_\></strong> dont ping me broooo  
<strong>\<rehrar\></strong> \_csd  
<strong>\<rehrar\></strong> there, I took it back  
<strong>\<dEBRUYNE\></strong> CLI v0.14.1.2 has been released  
<strong>\<dEBRUYNE\></strong> Which is mostly bug fixes I guess  
<strong>\<dEBRUYNE\></strong> mooo is holding a vacation, but he provided me a list of stuff that is ready to be merged  
<strong>\<dEBRUYNE\></strong> So I am working with luigi to get the merge queue relatively empty  
<strong>\<kinghat\></strong> 🙏  
<strong>\<rehrar\></strong> ah, did not know mooo was on vacation  
<strong>\<rehrar\></strong> I hope he ignores my ping then. Sorry\!  
<strong>\<dEBRUYNE\></strong> For the GUI, we tagged 0.14.1.2 and we're waiting on pony to finish the builds  
<strong>\<dsc\_\></strong> I'm more than half way into integrating i2p-zero and tor into GUI  
<strong>\<dEBRUYNE\></strong> Main new feature is optimized Tails support  
<strong>\<dEBRUYNE\></strong> Perhaps dsc\_ can share a bit more detail  
<strong>\<dsc\_\></strong> Sure thing.  
<strong>\<rehrar\></strong> dsc\_: that's actually super exciting  
<strong>\<dsc\_\></strong> So Tails integration is a collection of improvements that improve user experience for our Tails users  
<strong>\<dsc\_\></strong> You would be suprised how big the audience is there  
<strong>\<dsc\_\></strong> So, starting from 0.14.1.2 it will be very easy to use GUI on Tails  
<strong>\<dsc\_\></strong> As for i2p-zero, I need a couple of days then that's done too  
<strong>\<dsc\_\></strong> I suggest to package i2p-zero with the GUI release  
<strong>\<dsc\_\></strong> Which can pose problems for our reproducible build efforts  
<strong>\<dEBRUYNE\></strong> I don't see much harm in packaging it with the GUI, especially if the user first has to check a checkbox to turn it on  
<strong>\<dsc\_\></strong> but that's a problem for later  
<strong>\<dsc\_\></strong> That also  
<strong>\<rbrunner\></strong> Shouldn't the CLI pack it also then?  
<strong>\<dEBRUYNE\></strong> I think most CLI users are able to download the package themselves  
<strong>\<dEBRUYNE\></strong> And get it running (especially given the instructions present on Github)  
<strong>\<dEBRUYNE\></strong> By contrast, GUI users need a checkbox and not tons of steps  
<strong>\<rbrunner\></strong> Ok, makes sense, more or less ...  
<strong>\<dsc\_\></strong> The fact we package i2p-zero is a convienence feature. I'm also 'integrating' support for Tor but we wont be packaging that. That's basically running Tor and using socks proxy at :9050  
<strong>\<rehrar\></strong> we GUI people are scrubs  
<strong>\<xmrmatterbridge\> \<xmr-romine\></strong> is there already some doc about running monerod over tor ?  
<strong>\<dsc\_\></strong> <https://github.com/monero-project/monero/blob/master/ANONYMITY\_NETWORKS.md>  
<strong>\<dEBRUYNE\></strong> <https://github.com/monero-project/monero/blob/master/ANONYMITY\_NETWORKS.md> &amp; <https://github.com/monero-project/monero#using-tor>  
<strong>\<xmrmatterbridge\> \<xmr-romine\></strong> thanks guys  
<strong>\<rehrar\></strong> hyc any update on randomx audit?  
<strong>\<rehrar\></strong> The last one?  
<strong>\<dsc\_\></strong> One more thing regarding i2p-zero.. It can take up to 1-2 minute(s) for the local socks proxy to become 'active' which means, if the user has i2p-zero enabled and starts up the GUI to create a quick tx ... might have to wait a minute or two  
<strong>\<dsc\_\></strong> This is related to how i2p-zero works  
<strong>\<dsc\_\></strong> so beware of that limitation  
<strong>\<rbrunner\></strong> So it's i2p-two, from "two minutes"?  
<strong>\<kinghat\></strong> can it check if i2p is currently running?  
<strong>\<dsc\_\></strong> rbrunner: haha  
<strong>\<rehrar\></strong> it's how i2p works in general, no? Getting bootstrapped into the network, I mean.  
<strong>\<dsc\_\></strong> rehrar: most likely  
<strong>\<dsc\_\></strong> kinghat: it can  
<strong>\<rehrar\></strong> under bad circumstances it can take even longer  
<strong>\<rehrar\></strong> I wonder if there can be some kind of notification to let users know this  
<strong>\<vtnerd\_\_\></strong> tor should have similar issue iirc, building circuits isn't immediate  
<strong>\<kinghat\></strong> also, are we still going to do the beta builds for the gui?  
<strong>\<dsc\_\></strong> vtnerd\_\_: Sure, but not 1-2 minutes?  
<strong>\<dsc\_\></strong> kinghat: yes  
<strong>\<kinghat\></strong> 👌  
<strong>\<vtnerd\_\_\></strong> I think it might be longer than that, at least it seemed like forever yesterday when I was testing  
<strong>\<vtnerd\_\_\></strong> actually no, I've run tails once before, it takes some amount of minutes, just don't remember the exact time frame  
<strong>\<dsc\_\></strong> vtnerd\_\_:  
<strong>\<dsc\_\></strong> $ time (sudo service tor restart &amp;&amp; sleep 2 &amp;&amp; torify curl icanhazip.com)  
<strong>\<dsc\_\></strong> 171.25.193.77  
<strong>\<dsc\_\></strong> real0m2.759s  
<strong>\<vtnerd\_\_\></strong> if your not using outbound connections tor destroys the circuits and goes into an idle mode too, which isn't a problem if "noise" is enabled (because its always sending)  
<strong>\<rehrar\></strong> there goes dsc\_ bragging about his internet again  
<strong>\<dsc\_\></strong> yes, my internet.  
<strong>\<vtnerd\_\_\></strong> it keeps state in a file that it might re-use, so you'd have to a cold restart  
<strong>\<dsc\_\></strong> vtnerd\_\_: fair enough  
<strong>\<rehrar\></strong> alright, anything else?  
<strong>\<dEBRUYNE\></strong> vtnerd\_\_: I was wondering if you intend to pick this up somewhere in the future? <https://github.com/monero-project/monero/pull/2317>  
<strong>\<vtnerd\_\_\></strong> see <https://github.com/monero-project/supercop/pull/2>  
<strong>\<vtnerd\_\_\></strong> this one and the next one after that PR is a bit rough because its x86 ASM  
<strong>\<rehrar\></strong> that was a hilarious conversation to witness  
<strong>\<rehrar\></strong> person 1: i was wondering if git link  
<strong>\<rehrar\></strong> person 2: Well you see it's like git link  
<strong>\<dEBRUYNE\></strong> Thanks  
<strong>\<vtnerd\_\_\></strong> Im also not certain that having a separate repo for this is beneficial, but I guess some other project could make use of the custom hooks  
<strong>\<vtnerd\_\_\></strong> my original code should need some re-working since the device/ledger stuff got slammed in, but I look at recently and I think its possible to rebase/update that without crying  
<strong>\<vtnerd\_\_\></strong> Im also not certain whether that supercop repo should be an external git thing, or something that you manually have to do  
<strong>\<vtnerd\_\_\></strong> I'm thinking the latter, since people are blasted without another submodule  
<strong>\<vtnerd\_\_\></strong> \*are not  
<strong>\<dEBRUYNE\></strong> I see, seems like a thing that warrants more in depth discussion in a future dev meeting  
<strong>\<rehrar\></strong> With more attendees?  
<strong>\<rehrar\></strong> serious question  
<strong>\<rbrunner\></strong> And maybe some more background info to prepare  
<strong>\<rehrar\></strong> who should be present for such a discussion?  
<strong>\<rehrar\></strong> we can add it to next meeting as an item and try to ping the people to be there  
<strong>\<vtnerd\_\_\></strong> the background is either the supercop code goes as a submodule and it must be synced by every person  
<strong>\<vtnerd\_\_\></strong> or only those that which to accelerate wallet scanning drop the repo into a folder and toggle a cmake bit  
<strong>\<rbrunner\></strong> So that's not something for the normal, general release then?  
<strong>\<vtnerd\_\_\></strong> its not needed for testing, unless you need to test the feature specifically  
<strong>\<vtnerd\_\_\></strong> no, likely it would be in the normal general release, but I suppose it doesn't have to be  
<strong>\<vtnerd\_\_\></strong> this came up because ryo recently added support for basically the same thing, and it should cut wallet-scanning time in half  
<strong>\<vtnerd\_\_\></strong> although its probably dependent on your HD speeds too  
<strong>\<rehrar\></strong> alright, any more discussion on this?  
<strong>\<hyc\></strong> re: randomx audit, Quarkslab are finalizing their report, said we may get it by middle of next week  
<strong>\<rehrar\></strong> nice\!  
<strong>\<rehrar\></strong> does anyone have anything else that they want to discuss?  
<strong>\<hyc\></strong> since they've been opening github issues as they arose, there's not likely to be anything in the report we haven't already seen  
<strong>\<ErCiccione\></strong> yep\! <https://github.com/monero-project/meta/issues/236#issuecomment-515669422>  
<strong>\<ErCiccione\></strong> GitHub is starting to censor people coming from countries under US sanctions, we should definitely migrate away  
<strong>\<ErCiccione\></strong> i don't know how the core team feel about it  
<strong>\<rehrar\></strong> do people here have any thoughts about the Github/Gitlab thing, especially in light of the recent Github things?  
<strong>\<vtnerd\_\_\></strong> those countries listed probably require some vpn/tor/i2p opsec to contribute anyway ... ? I'm certainly not attempting to stop a switch to a self-hosted gitlab, but meh  
<strong>\<rbrunner\></strong> If such a switch was so easy it would probably have happened already, I think, after the Microsoft acquisition ...  
<strong>\<vtnerd\_\_\></strong> or maybe not, but they would have to after that hammer that was thrown  
<strong>\<rbrunner\></strong> With all submodules still on GitHub, for example  
<strong>\<vtnerd\_\_\></strong> the support team for the gitlab instance are probably the most relevant for this  
<strong>\<ErCiccione\></strong> rbrunner: the point was to test monero-site on the self-hosted gitlab first, and then see what to do with the other repos. But has been almost an year now  
<strong>\<hyc\></strong> I've always favored moving to self-hosted gitlab and away from github  
<strong>\<rbrunner\></strong> Yeah, I remember. But I think the site is a particularly simple case  
<strong>\<vtnerd\_\_\></strong> I mean most devs should have a copy of the code and history luckily, but its the discussions that can get purged if not backed up properly  
<strong>\<hyc\></strong> but this particular issue only affected private, paid github accts  
<strong>\<hyc\></strong> (i.e., github closing off accts from sanctioned countries)  
<strong>\<ErCiccione\></strong> hyc: i guess that depends by how they are forced to enforce the sanctions  
<strong>\<hyc\></strong> <https://twitter.com/natfriedman/status/1155533738278699008>  
<strong>\<hyc\></strong> <https://twitter.com/natfriedman/status/1155311121038864384>  
<strong>\<hyc\></strong> they're splitting some hairs I guess. trade sanctions only affect commerce. if you paid for a private acct, you're affected.  
<strong>\<rbrunner\></strong> Has any other notable cryptocurrency team already made such a switch?  
<strong>\<hyc\></strong> if you're on a public/free acct, you're not affected  
<strong>\<rehrar\></strong> rbrunner: define notable?  
<strong>\<rbrunner\></strong> I mean, some "interesting" team. Top 100 coin, maybe? Sizeable community, I mean  
<strong>\<ErCiccione\></strong> thanks for the links. it's still a very precarious situation.  
<strong>\<ErCiccione\></strong> rbrunner: sia  
<strong>\<rbrunner\></strong> And complexity of the code  
<strong>\<hyc\></strong> ErCiccione: agreed. as I already said, I'm in favor of moving off.  
<strong>\<kinghat\></strong> i think ppl are worried about contributions after moving off github. i dont think it would make a difference.  
<strong>\<hyc\></strong> again, just my perspective: the OpenLDAP Project maintains our own repo. we only mirror to github, because it seems you're not a real project these days if you're not on github  
<strong>\<hyc\></strong> out github mirror is read-only  
<strong>\<hyc\></strong> our\*  
<strong>\<ErCiccione\></strong> kinghat: i agree.  
<strong>\<dsc\_\></strong> I keep repeating myself but I question people whose first thought is 'gitlab' when thinking of a git alternative  
<strong>\<dsc\_\></strong> There is more\! Noooo.. Yes\!\!  
<strong>\<dsc\_\></strong> Consider it...  
<strong>\<hyc\></strong> gitea?  
<strong>\<dsc\_\></strong> for example, yep  
<strong>\<hyc\></strong> I don't really care which alternative is used. all I care is self-hosted.  
<strong>\<ErCiccione\></strong> iirc gitea was considered  
<strong>\<hyc\></strong> you could make an argument that being off github adds a barrier to entry - people don't like having to create accounts just to interact with another project  
<strong>\<rehrar\></strong> In favor of gitea  
<strong>\<dsc\_\></strong> Even more so when considered gitlab is a company, enterprise, they have funding, maybe they have shareholders - and capitalism is evil. Therefor, gitea  
<strong>\<rehrar\></strong> hyc which is why I am arguing for a federated git ecosystem  
<strong>\<rehrar\></strong> open issues on another git based project management site from yours, etc  
<strong>\<ErCiccione\></strong> let's not forget that we already have half repos on github and half on gitlab. That's not ideal  
<strong>\<hyc\></strong> rehrar: agree, federated identity would be preferable  
<strong>\<rehrar\></strong> let's build it  
<strong>\<rehrar\></strong> we can have it out by Wednesday at the latest  
<strong>\<hyc\></strong> +1  
<strong>\<dsc\_\></strong> ok sounds good  
<strong>\<ErCiccione\></strong> i want 2  
<strong>\<rehrar\></strong> that'll take an extra day  
<strong>\<hyc\></strong> this could be a long conversation, but totally - we need to rethink the notion of accounts and identities  
<strong>\<rehrar\></strong> But for reals though this is an ongoing discussion and...  
<strong>\<rehrar\></strong> ^ hyc  
<strong>\<rehrar\></strong> we have the issue open about this that ErCiccione  
<strong>\<rehrar\></strong> although that one is about moving to gitlab, I think  
<strong>\<rehrar\></strong> so maybe another one can be opened for discussion on which platform?  
<strong>\<dsc\_\></strong> +1 for centralized authentication service  
<strong>\<dsc\_\></strong> (hosted by monero)  
<strong>\<rbrunner\></strong> Oh the added complexity  
<strong>\<dsc\_\></strong> rbrunner: for whom?  
<strong>\<rbrunner\></strong> The system in general, I mean.  
<strong>\<dsc\_\></strong> It could simplify things  
<strong>\<hyc\></strong> not quite centralized authent. just public key based.  
<strong>\<rbrunner\></strong> Something more that can go wrong  
<strong>\<ErCiccione\></strong> rehrar it is yes, as hyc says for me the important is to move away from a centralized place. I think gitlab is the best choice because we have been testing it for an year, but sure let's discuss alternatives  
<strong>\<hyc\></strong> we could use monero wallet addresses as our identities  
<strong>\<rehrar\></strong> hyc I've been thinking of using Monero signatures as password alternatives  
<strong>\<dsc\_\></strong> thats a cool idea  
<strong>\<rehrar\></strong> public key as ID  
<strong>\<rehrar\></strong> signature from private key as password  
<strong>\<kinghat\></strong> does that work with subaddys or am i missing something?  
<strong>\<rehrar\></strong> but then losing your seed is even a bigger deal  
<strong>\<rehrar\></strong> or getting it stolen  
<strong>\<hyc\></strong> good point  
<strong>\<rehrar\></strong> as long as there are standard ways of resetting or something  
<strong>\<rehrar\></strong> it's no more annoying than losing or getting your regular password stolen  
<strong>\<hyc\></strong> having a reset facility implies a centralized admin authority  
<strong>\<dsc\_\></strong> Call the Monero helpdesk and provide them your miaden name, your first car brand and your date of birth  
<strong>\<hyc\></strong> ^  
<strong>\<rehrar\></strong> enforced 2/3 MFA then  
<strong>\<hyc\></strong> should we wrap up the mtg before continiung this conv?  
<strong>\<rehrar\></strong> but yeah, we'll call it here  
<strong>\<rehrar\></strong> unless anyone has any last minute things?  
<strong>\<vtnerd\_\_\></strong> I hope to finally issuing some PRs related to the i2p/tor white noise stuff, took some time to architect this bt hopefully. nothing else needs to be reported by that really other than look for more stuff to review  
<strong>\<rehrar\></strong> cool deal\!  
<strong>\<rehrar\></strong> well everyone, thanks for making the time today.  
<strong>\<rehrar\></strong> You're all free to disperse. Coffee on the little table outside the meeting room.
