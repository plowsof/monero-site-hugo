---
title: Overview and Logs for the Dev Meeting Held on 2019-05-19
summary: Development status, Code & ticket discussion, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<xmrmatterbridge\> \<rehrar\></strong> Meeting\!\!  
<strong>\<ferretinjapan\></strong> rehrar, o/  
<strong>\<moneromooo\></strong> rehrar: btw, did you get any new info from purism ?  
<strong>\<jwinterm\></strong> \\o  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Yes. Will update. Did update in -community  
<strong>\<hyc\></strong> time  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> Hello guys. Let’s start the meeting.  
<strong>\<xmrmatterbridge\> \<rehrar\></strong> 1. Greetings  
<strong>\<ErCiccione\></strong> Hi  
<strong>\<rbrunner\></strong> Hi  
<strong>\<vtnerd\></strong> hi  
<strong>\<hyc\></strong> hi  
<strong>\<jwinterm\></strong> so long rbrunner  
<strong>\<rbrunner\></strong> Connection problems … back again  
<strong>\<rehrar\></strong> Alright  
<strong>\<rehrar\></strong> 2. What’s been done since previous meeting?  
<strong>\<rehrar\></strong> right, well, let’s jump to that then. It’s what we’re all anxious to hear about anyways.  
<strong>\<hyc\></strong> OK, so we have 4 SoWs from audit teams, we had an unexpected bonus from Arweave.org agreeing to pay for the TrailofBits audit  
<strong>\<hyc\></strong> the vote on auditor selection is closed and tallied, Kudelski is the clear first choice  
<strong>\<hyc\></strong> Quarkslab and X41 nearly tied for 2nd choice but QL slightly ahead  
<strong>\<hyc\></strong> and majority voted for 3 choices, so it seems we are going to submit all 3 in CCS  
<strong>\<hyc\></strong> randomX integration in monerod is mostly there, we have some bug with reorg handling at the moment  
<strong>\<rehrar\></strong> What’s the cost of all three, hyc?  
<strong>\<hyc\></strong> but otherwise the patch has all the functionality we seem to need, including support for mining RPCs so pools and solo miners can work  
<strong>\<tevador\></strong> \~$120K  
<strong>\<hyc\></strong> rehrar, let me get back to you in a few minutes. move on to next topic till I tally  
<strong>\<hyc\></strong> ^^ there you go  
<strong>\<rehrar\></strong> ok  
<strong>\<rehrar\></strong> Standard CCS concerns, since Defcon will be putting up a couple of CCS stuff too here not so far from now  
<strong>\<rehrar\></strong> I’ll contact Outreach workgroup to try to do something to get everyone on board and donating, but sure.  
<strong>\<rehrar\></strong> Anything else on that hyc?  
<strong>\<hyc\></strong> I would structure it in priority order, and if we don’t get full funds, we just omit the last choice  
<strong>\<hyc\></strong> I think that covers it for me, yeah  
<strong>\<rehrar\></strong> awesome, thanks for all of your guys’ work on this. It’s exciting stuff.  
<strong>\<rehrar\></strong> Anyone else have anything that’s been done past couple of weeks?  
<strong>\<moneromooo\></strong> monerod can now sync on big endian ^\_^  
<strong>\<hyc\></strong> woohoo\!  
<strong>\<rbrunner\></strong> Wow. Is that still a thing?  
<strong>\<hyc\></strong> IBM POWER, Fujitsu / oracle SPARC  
<strong>\<hyc\></strong> big datacenter boxes, sure  
<strong>\<rbrunner\></strong> Nice to have anyway\!  
<strong>\<rehrar\></strong> the improvements that really matter  
<strong>\<rehrar\></strong> :P anyways, I can also give an update regarding Purism if desired.  
<strong>\<rehrar\></strong> I had a meeting with Todd, the CEO a few days ago.  
<strong>\<rbrunner\></strong> Please do  
<strong>\<rehrar\></strong> They’re still just as excited about Monero. They aren’t really interested in other cryptocurrencies, because only Monero has the ideology of privacy by default, similar to them. They’re still very excited about integrating Moenro into Librem Pay  
<strong>\<rehrar\></strong> so one can theoretically pay using Monero anywhere at any merchant, and merchant settles in fiat.  
<strong>\<rehrar\></strong> still want to ship Monero by default on all of their systems, mobile and desktop.  
<strong>\<rehrar\></strong> They don’t have any available dev kits for the Librem5 phone for the devs to mess around with, but they are going to get me emulators for their PureOS stuffs.  
<strong>\<rehrar\></strong> And we can start playing with the GUI and stuff on there and make it adaptive, if possible, and the like  
<strong>\<rehrar\></strong> They’re willing to do a matching thing on a CCS proposal that we do  
<strong>\<rehrar\></strong> As in, if we raise x amount of money, they’ll put in x as well (up to some upper limit for them) for a dev to work on this stuff.  
<strong>\<jtgrassie\></strong> By “ship Monero by default”, do they mean ship with full-node + wallet?  
<strong>\<rehrar\></strong> dsc\_ has expressed a willingness, but I’m not going to put words in his mouth, so you can talk to him for more info  
<strong>\<rehrar\></strong> jtgrassie: that’s for us to figure otu  
<strong>\<rehrar\></strong> \*out  
<strong>\<rehrar\></strong> the Librem5 phone is indeed a phone, but you will be able to connect it to a monitor and use it as a desktop also, as the OS itself will be adaptive.  
<strong>\<rbrunner\></strong> Nice that things seem to get moving, they seem excited already for quite some time …  
<strong>\<rehrar\></strong> So we can choose how we want the GUI to be put on there.  
<strong>\<vtnerd\></strong> yeah the light-wallet-server setup is probably more appropriate, but people have synced the chain to their phone  
<strong>\<rehrar\></strong> Obviously, since there is the idea that you can do whatever you want on their phone with no abritrary restrictions, the idea that someone can theoretically run a full node on their phone should not be overlooked  
<strong>\<hyc\></strong> are they using a micro-HDMI port, or just something like chromecast to use external monitor? just curious, not important  
<strong>\<jtgrassie\></strong> Having purism simply accept Monero as a payment method first would be nice  
<strong>\<vtnerd\></strong> the issue might be storage on that sucker, I dont see sd card listed … ?  
<strong>\<moneromooo\></strong> They do.  
<strong>\<moneromooo\></strong> Or did, at least.  
<strong>\<rehrar\></strong> jtgrassie: they do accept Monero  
<strong>\<jwinterm\></strong> hyc: it looks like it will go usb-c to hdmi or display port (tbd)  
<strong>\<jtgrassie\></strong> moneromooo: not an option at checkout  
<strong>\<jtgrassie\></strong> rehrar: ^  
<strong>\<hyc\></strong> jwinterm thanks  
<strong>\<rehrar\></strong> there is “Cryptocurrencies” option  
<strong>\<jtgrassie\></strong> Oh, my bad, Globee  
<strong>\<rehrar\></strong> and it’s done via Globee  
<strong>\<rehrar\></strong> anyways, that’s it from me. I’ll ping them in this upcoming week about the emulators  
<strong>\<rehrar\></strong> and discussion may pop up from time to time in -gui  
<strong>\<rehrar\></strong> and maybe here  
<strong>\<rehrar\></strong> we’ll be in contact with you mooo, if things need to happen on the core side  
<strong>\<rehrar\></strong> but PureOS is Debian-based, so I don’t think anything crazy will need to happen  
<strong>\<hyc\></strong> rehrar tell them they need a -Pro model with landscape aspect slideout qwerty keyboard  
<strong>\<rehrar\></strong> I’ll see what I can do to pass that along. :P  
<strong>\<jtgrassie\></strong> I guess shipping the wallet by default would be nice. Easy to do.  
<strong>\<rbrunner\></strong> Hmmm, yes, like Psion 5mx  
<strong>\<rehrar\></strong> Yes, that’s the plan. It’s one of the default softwares on their phone  
<strong>\<endogenic\></strong> hi all  
<strong>\<rehrar\></strong> \*it’d be  
<strong>\<rehrar\></strong> anyone else have something to report or talk about?  
<strong>\<ErCiccione\></strong> I have a quick update. The Monero Ecosystem has a new member: go-monero-rpc-client. The repo is not transferred yet, but it has been approved: <https://github.com/monero-ecosystem/meta/issues/35>. We didn’t have anything in golang before, so i think it’s cool to have it.  
<strong>\<rehrar\></strong> That’s pretty neat.  
<strong>\<hyc\></strong> I wonder if the RandomX repo should be in Ecosystem  
<strong>\<rehrar\></strong> I would think it’d be better suited for Monero Project?  
<strong>\<ErCiccione\></strong> hyc: it would be more than welcome  
<strong>\<hyc\></strong> I guess it’s up to tevador to decide where he wants it to live  
<strong>\<rehrar\></strong> Ecosystem is typically Monero-only things, and while RandomX is be built by Monero for Monero  
<strong>\<rehrar\></strong> it should be agnostic in theory, no?  
<strong>\<rehrar\></strong> as in, other coins can adopt it?  
<strong>\<hyc\></strong> and we already have a 3rd party Arweave planning to use it  
<strong>\<rehrar\></strong> Similar to OpenAlias in that respect.  
<strong>\<rehrar\></strong> So my suggestion to tevador would be in the Monero Project set of repos  
<strong>\<hyc\></strong> ok  
<strong>\<ErCiccione\></strong> Well, was created by monero developers for Monero. I think hosting it on a Monero “place” is apropriate  
<strong>\<rehrar\></strong> on the “new” repo.getmonero.org  
<strong>\<rehrar\></strong> Alright, any code discussion to happen as a 3 or 4 or whatever?  
<strong>\<rehrar\></strong> If not, we can adjourn and go to markets to speculate on the rise of the market.  
<strong>\<rehrar\></strong> unless someone had other meeting items?  
<strong>\<hyc\></strong> anything more to say on next point release?  
<strong>\<rehrar\></strong> ooooh yes plz  
<strong>\<hyc\></strong> moneromooo ?  
<strong>\<moneromooo\></strong> Waiting on pony to build binaries AFAIK.  
<strong>\<ErCiccione\></strong> core is branched and GUI is waiting for core. Translations for GUI are being submitted, but we are having a lot less contributors than the last release  
<strong>\<sarang\></strong> When is freeze for the Carbon Crab update?  
<strong>\<rehrar\></strong> \*Crap  
<strong>\<sarang\></strong> MRL is feverishly working on CLSAG  
<strong>\<endogenic\></strong> an MRL workshop is occurring this week. any requests as to topics of discussion  
<strong>\<moneromooo\></strong> Lightning/Bolt building blocks ^\_^  
<strong>\<sarang\></strong> Fo sho  
<strong>\<rehrar\></strong> so…  
<strong>\<rehrar\></strong> we gucci?  
<strong>\<sarang\></strong> When is the freeze?  
<strong>\<sarang\></strong> For Carbon  
<strong>\<moneromooo\></strong> Whenever we’re done :)  
<strong>\<sarang\></strong> Lol  
<strong>\<rehrar\></strong> I think it’s quite dependent on the audits  
<strong>\<rehrar\></strong> no?  
<strong>\<rehrar\></strong> if we’re planning on getting them in, that is  
<strong>\<sarang\></strong> For randomx?  
<strong>\<hyc\></strong> freeze for October hardfork you mean?  
<strong>\<sarang\></strong> Goal is to finish by July IIRC  
<strong>\<sarang\></strong> Ya  
<strong>\<sarang\></strong> If we choose to get CLSAG audited that adds time  
<strong>\<rehrar\></strong> Monero is technically made of money  
<strong>\<rehrar\></strong> so I don’t see a huge problem  
<strong>\<endogenic\></strong> it’s people  
<strong>\<rehrar\></strong> so, question answered then?  
<strong>\<rehrar\></strong> regardless of how unsatisfactory  
<strong>\<sarang\></strong> Not really, but ok  
<strong>\<endogenic\></strong> how about, when will we know when the freeze will be?  
<strong>\<rbrunner\></strong> In the two years I am here now I never saw a real freeze happen :)  
<strong>\<rbrunner\></strong> Only attempts …  
<strong>\<rbrunner\></strong> Not that there was a real problem with this  
<strong>\<ErCiccione\></strong> so true.. i’ve been begging for one for a long time  
<strong>\<hyc\></strong> one could say the code is currently in a frozen state, since nothing can be merged until fluffy resurfaces  
<strong>\<rbrunner\></strong> lol  
<strong>\<sarang\></strong> What a time to be alive  
<strong>\<ErCiccione\></strong> hyc: luigi got the power now. HE is the leader of Monero afterall  
<strong>\<ErCiccione\></strong> at least according to wikipedia  
<strong>\<hyc\></strong> oho  
<strong>\<rehrar\></strong> alright, I think we’re pretty much done then. :)  
<strong>\<hyc\></strong> sounds like it  
<strong>\<hyc\></strong> adios  
<strong>\<rehrar\></strong> Two weeks from now? The second?  
<strong>\<rehrar\></strong> cya guys
