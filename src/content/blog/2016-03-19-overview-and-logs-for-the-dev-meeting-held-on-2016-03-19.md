---
title: Overview and Logs for the Dev Meeting Held on 2016-03-19
summary: Open PRs, GUI commits, app/add-on infrastructure, versioning
tags: [dev diaries, core, crypto]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<dEBRUYNE\></strong> dev meeting in 5 min, FYI  
<strong>\<hyc\></strong> dingdong  
<strong>\<gingeropolous\></strong> hello  
<strong>\<dEBRUYNE\></strong> fluffypony, smooth, othe, ArticMine, luigiw, NoodleDoodle, tewinget, moneromooo  
<strong>\<floofypony\></strong> there we go  
<strong>\<dEBRUYNE\></strong> did I forget anyone?  
<strong>\<tewinget\></strong> oh, hello  
<strong>\<luigi\></strong> is warptangent around?  
<strong>\<ArticMine\></strong> Hello  
<strong>\<hyc\></strong> he’s been fighting a flu last we heard  
<strong>\<moneromooo\></strong> hi  
<strong>\<NoodleDoodle\></strong> Hello. I’m here but I’m fighting the apocalypse.  
<strong>\<NoodleDoodle\></strong> of flus.  
<strong>\<luigi\></strong> keep doing it  
<strong>\<luigi\></strong> wait you’re alive that’s good to hear  
<strong>\<dEBRUYNE\></strong> fluffypony seems ded  
<strong>\<fluffypony\></strong> sorry  
<strong>\<fluffypony\></strong> was eating  
<strong>\<fluffypony\></strong> welcome everyone  
<strong>\<fluffypony\></strong> so as you know we pushed out 0.9.2  
<strong>\<fluffypony\></strong> however, there are some nagging issues from the ReadTXN work  
<strong>\<fluffypony\></strong> hyc has nailed a major one as of a few hours ago  
<strong>\<fluffypony\></strong> so we’ll probably do a point release on Monday or so  
<strong>\<fluffypony\></strong> also that means that the way we use LMDB has changed a bit  
<strong>\<fluffypony\></strong> hyc can you tell us briefly how we should wrapping access to LMDB, both read and write operations?  
<strong>\<hyc\></strong> Are you talking about the CRITICAL\_REGION stuff?  
<strong>\<fluffypony\></strong> yes, and the cursors vs. txns stuff  
<strong>\<hyc\></strong> ok, the critical\_region stuff actually is not a change at all.  
<strong>\<hyc\></strong> basically, when you’re setting up to do a write, you need exclusive access to the DB  
<strong>\<hyc\></strong> this appears to have been a long-standing bug, unrelated to the readtxn changes  
<strong>\<hyc\></strong> so as for reads - there is now a long-lived read txn per thread  
<strong>\<hyc\></strong> and a set of read cursors to go with each  
<strong>\<hyc\></strong> the TXN\_PREFIX\_RDONLY macro sets that up in a particular function, grabbing the thread-local-storage for it  
<strong>\<hyc\></strong> and RCURSOR(dbname) sets up a read cursor for a particular DB  
<strong>\<hyc\></strong> these are analogous to the CURSOR(dbname) macro for getting a write cursor to a DB  
<strong>\<hyc\></strong> the point of all this is to avoid a bunch of malloc/free/seek when accessing a DB  
<strong>\<hyc\></strong> the old code was allocating a readtxn and cursors inside each function  
<strong>\<hyc\></strong> likewise for writes  
<strong>\<hyc\></strong> by reusing the same cursors acros a set oof functions we get a pretty good performance gain  
<strong>\<hyc\></strong> ok?  
<strong>\<fluffypony\></strong> neat  
<strong>\<fluffypony\></strong> also on the topic of stuff-hyc-did-lately  
<strong>\<fluffypony\></strong> if anyone missed it, we now have a win environment guide up on forum.getmonero.org  
<strong>\<dEBRUYNE\></strong> ^ https//forum.getmonero.org/5/support//building-monero-v0-9-2-on-winMonero  
<strong>\<fluffypony\></strong> so that should get us all on the same page with testing etc.  
<strong>\<hyc\></strong> and one success story replied to it already ;)  
<strong>\<fluffypony\></strong> we’ve also dropped support for BDB as the default database, and switched to LMDB as the default  
<strong>\<fluffypony\></strong> including on -bit and ARM  
<strong>\<fluffypony\></strong> BDB will remain supported for the moment, primarily as a mechanism for contributors to understand how to build out DB support  
<strong>\<fluffypony\></strong> krongle)  
<strong>\<fluffypony\></strong> shew we have the entire xmr.to team here today, that’s awesome  
<strong>\<binaryFate\></strong> fluffypony good memory P  
<strong>\<fluffypony\></strong> we shared a podcast together, binaryFate -P  
<strong>\<krongle\></strong> yes - impressive nick-name recollection  
<strong>\<fluffypony\></strong> hah hah  
<strong>\<fluffypony\></strong> while we have you guys here, are you guys doing anything cool you want to talk about?  
<strong>\<binaryFate\></strong> we’re doing many cool things, but nothing we can talk about at this stage  
<strong>\<fluffypony\></strong> hah hah  
<strong>\<fluffypony\></strong> it does lead to an interesting point of conversation  
<strong>\<binaryFate\></strong> seriously considering btc -\> xmr direction  
<strong>\<fluffypony\></strong> plugins  
<strong>\<iam6yearsold\></strong> If NobleSir or xmr.to team could talk more about xmr.to integration at MiniNero that would be great… also are 2 way conversions coming to xmr.to soon?  
<strong>\<fluffypony\></strong> iam6yearsold Shen’s offline at the moment, I’ll ask him to update the Reddit thread with some info )  
<strong>\<fluffypony\></strong> re plugins, we’ve spoken briefly about options for the GUI  
<strong>\<dEBRUYNE\></strong> iam6yearsold There is a bit of info here -\> https//imgur.com/a/HZL7k  
<strong>\<binaryFate\></strong> iam6yearsold for MiniNero integration you’d have to see with NobleSir. The API doc is at http//xmrto-api.readthedocs.org/en/latest/  
<strong>\<fluffypony\></strong> but I guess we could have “plugins”, of a sort, that add functionality  
<strong>\<fluffypony\></strong> like xmr.to or shapeshift integration right in wallet2 / wallet2\_api  
<strong>\<dEBRUYNE\></strong> I think we should be fairly strict on which plugins to allow  
<strong>\<binaryFate\></strong> fluffypony we wanted to discuss that plugin integration soon in fact )  
<strong>\<arnuschky\></strong> we’re quite interested to all secondary questions related to plugins  
<strong>\<fluffypony\></strong> I guess the major question becomes  
<strong>\<arnuschky\></strong> so plugin repository/db, packaging, distribution etc  
<strong>\<fluffypony\></strong> do we allow “permissionless” plugin development, or do we just have a central repo that we git submodule in?  
<strong>\<ArticMine\></strong> The main question I see with plugins is trust  
<strong>\<fluffypony\></strong> ArticMine exactly  
<strong>\<arnuschky\></strong> yes. It puts quite a bit responsibility on the dev team  
<strong>\<gingeropolous\></strong> well no ones going to trust anything that doesn;t come from core  
<strong>\<tewinget\></strong> \<fluffypony\> we shared a podcast together, binaryFate -P \<— wasn’t I there for that?  
<strong>\<fluffypony\></strong> considering the recent Google Chrome Bitcoin stealing malware I think that premissionless plugins are dangerous  
<strong>\<gingeropolous\></strong> as we’ve seen with 3rd party GUIs  
<strong>\<luigi\></strong> you obviously can’t stop permissionless dev, you can discourage users from trusting it I guess  
<strong>\<hyc\></strong> we can start signing binaries, ohjoy  
<strong>\<dEBRUYNE\></strong> I would prefer the latter  
<strong>\<fluffypony\></strong> luigi I mean permissionless within core  
<strong>\<luigi\></strong> oh  
<strong>\<luigi\></strong> I think no  
<strong>\<arnuschky\></strong> it’s related to how plugins are written. If it’s binary blobs, it’s a) hard to build, distribute etc, and b) hard to examine  
<strong>\<binaryFate\></strong> fluffypony I’d see both possible all together. Unpermissioned scale and central repo for a selected subset would ease experience and trust for user  
<strong>\<arnuschky\></strong> so if plugins are interpreted (eg python), things become a whole lot easier  
<strong>\<iam6yearsold\></strong> for the record I hated the twittter plugin idea I saw a while back  
<strong>\<ArticMine\></strong> My take permissionless has to be allowed. The end user has to be made aware who is signing and if to trust the plugin  
<strong>\<fluffypony\></strong> well the Electrum model works well  
<strong>\<moneromooo\></strong> I agree with ArticMine  
<strong>\<arnuschky\></strong> (inspection in case of central repo, but also self-distribution by plugin devs)  
<strong>\<fluffypony\></strong> ThomasV will merge basically any plugin, as long as it’s not malicious  
<strong>\<fluffypony\></strong> and plugins are part of the core code, effectively just in a subfolder  
<strong>\<fluffypony\></strong> I think it’s a testament to Electrum that they haven’t had a malicious plugin ever  
<strong>\<arnuschky\></strong> how do they deal with the upgrade/maintenance workload? Or do they just disable broken plugins?  
<strong>\<dEBRUYNE\></strong> Is there a way to make a subfolder in the subfolder? i.e. (1) signed and approved by core-team, (2) optional  
<strong>\<fluffypony\></strong> arnuschky yeah they just disable broken plugins, and eventually they get deprecated out  
<strong>\<ArticMine\></strong> We should allow self distribution with appropriate warning  
<strong>\<fluffypony\></strong> ArticMine anyone can compile their own build, which would be the same thing  
<strong>\<arnuschky\></strong> are you planning for compiled plugins or interpreted ones? that’s quite a differens IMHO  
<strong>\<fluffypony\></strong> arnuschky so  
<strong>\<arnuschky\></strong> self-distribution is a mess for compiled ones…  
<strong>\<fluffypony\></strong> I was thinking we have a repo, say it’s called monero-plugins  
<strong>\<arnuschky\></strong> audit as well  
<strong>\<fluffypony\></strong> and then anyone can PR to that repo  
<strong>\<fluffypony\></strong> and that repo is pulled into the main Monero source as a git submodule  
<strong>\<fluffypony\></strong> there are two advantages to this  
<strong>\<fluffypony\></strong> 1. as it gets bigger and harder to deal with, we can step back and other known members of the community can manage that repo  
<strong>\<fluffypony\></strong> 2. if we come up with a standard set of functionality hooks, then other projects can pull that same repo in  
<strong>\<fluffypony\></strong> eg. jwinterm’s lightwallet  
<strong>\<fluffypony\></strong> also it means that the compiled Monero binaries have those plugins baked in, and you can’t add extra plugins post-compile  
<strong>\<fluffypony\></strong> so no need to deal with interpreted code and securing that on disk and in memory  
<strong>\<hyc\></strong> baked in means no dynamic loading?  
<strong>\<tewinget\></strong> \<fluffypony\> so no need to deal with interpreted code and securing that on disk \<— if securing an interpreted plugin on disk became an issue, securing the binary would be an issue anyway, so I don’t know of that bit matters  
<strong>\<binaryFate\></strong> Sounds all good to us. If distribution is done through official channels it’s great.  
<strong>\<fluffypony\></strong> hyc yes  
<strong>\<fluffypony\></strong> no dynamic loading  
<strong>\<hyc\></strong> cool  
<strong>\<fluffypony\></strong> tewinget I mean we can’t secure it in the path from random-site-on-the-web down to random-download-folder and eventually into secure-disk-location  
<strong>\<arnuschky\></strong> fluffypony that would be really great.  
<strong>\<fluffypony\></strong> ok - I think next steps would be to consider some of the hooks we need to provide to add functionality  
<strong>\<fluffypony\></strong> we can use the Monero wikia as a collaboration area for that  
<strong>\<ArticMine\></strong> It is a good balance for plugins  
<strong>\<fluffypony\></strong> and then we’ll just update the Monero Slack  
<strong>\<arnuschky\></strong> well securing the plugins can always happen by signature - no matter if interpreted or binary  
<strong>\<fluffypony\></strong> I’m kidding, we don’t have a Slack  
<strong>\<fluffypony\></strong> we’re not that cool  
<strong>\<aerbax\></strong> Would these plugins allow for interpreted languages like Lua or Python?  
<strong>\<arnuschky\></strong> :)  
<strong>\<fluffypony\></strong> aerbax I don’t see why not, individual CMake files in each plugin folder that allow it to produce a library fix everything  
<strong>\<binaryFate\></strong> We could financially support development of plugin architecture if xmr.to is the first instanciation of those plugins.  
<strong>\<fluffypony\></strong> if it spits out a .so / .a / .dll with the right hooks then it’s fine  
<strong>\<tewinget\></strong> fluffypony\> tewinget I mean we can’t secure it in the path from random-site-on-the-web down to random-download-folder and eventually into secure-disk-location \<— and yet, we provide binary downloads…so “random site on the web” could be managed the same as said binary downloads  
<strong>\<tewinget\></strong> just like any random site on the web can offer binaries for download and we can’t secure that either  
<strong>\<tewinget\></strong> caveat emptor has to come into play at some point, I think  
<strong>\<fluffypony\></strong> the binaries present a single attack surface, and there’s GPG-signed hashes  
<strong>\<fluffypony\></strong> if we have to do GPG-signed hashes for a bunch of .py files I think I’ll go mad -P  
<strong>\<tewinget\></strong> I’m not saying I think it should be one way or another, I’m merely pointing out flaws in your argument P  
<strong>\<fluffypony\></strong> fair enough  
<strong>\<fluffypony\></strong> binaryFate I think the stumbling block will be that somebody needs to champion this and run with it, and I won’t be able to lead it due to travelling in a week  
<strong>\<ArticMine\></strong> As long as people can compile their own version with non permissioned plugins this can work  
<strong>\<luigi\></strong> they can always do that  
<strong>\<fluffypony\></strong> yep  
<strong>\<fluffypony\></strong> and in fact that would be the testing model  
<strong>\<luigi\></strong> we’re not apple )  
<strong>\<fluffypony\></strong> fork the repo, and build a binary to test your new plugin  
<strong>\<iam6yearsold\></strong> asking noobs to compile will limit adoption  
<strong>\<ArticMine\></strong> luigi Exactly  
<strong>\<fluffypony\></strong> iam6yearsold why would noobs be writing their own plugins?  
<strong>\<gingeropolous\></strong> for security  
<strong>\<dEBRUYNE\></strong> lol gingeropolous  
<strong>\<fluffypony\></strong> lol  
<strong>\<arnuschky\></strong> fluffypony championing the first plugin or the whole infrastructure?  
<strong>\<tewinget\></strong> What about a curated repo of plugins (as suggested) but with those plugins written in python/lua? Someone modifying the python/lua on a target’s disk is the same as someone modifying the binary anyway, and python/lua plugins would be far easier to develop and audit I think  
<strong>\<fluffypony\></strong> arnuschky championing the design, I guess  
<strong>\<arnuschky\></strong> tewinget I would prefer that.  
<strong>\<iam6yearsold\></strong> how about 1 version with binaries and gpg sig and no plugins? caveat emptor for the rest  
<strong>\<arnuschky\></strong> mostly due to auditing, and there’s no build/distribution mess attached  
<strong>\<fluffypony\></strong> I would prefer we remain language agnostic  
<strong>\<fluffypony\></strong> iam6yearsold that’s what we already have  
<strong>\<tewinget\></strong> fluffypony language-agnostic is fine, but…well, how do you imagine that will work out?  
<strong>\<iam6yearsold\></strong> thanks pony. I like the current situation then  
<strong>\<fluffypony\></strong> tewinget read up  
<strong>\<arnuschky\></strong> ah even language agnostic. I thought up to now it’s supposed to be a C++ only API  
<strong>\<tewinget\></strong> as in, how do we become language-agnostic so that we can remain so?  
<strong>\<fluffypony\></strong> \[\] \<aerbax\> Would these plugins allow for interpreted languages like Lua or Python?  
<strong>\<fluffypony\></strong> \[\] \<fluffypony\> aerbax I don’t see why not, individual CMake files in each plugin folder that allow it to produce a library fix everything  
<strong>\<fluffypony\></strong> ^^  
<strong>\* smooth</strong> is here  
<strong>\<fluffypony\></strong> also what if a plugin wants to call a function in the core crypto library, for instance?  
<strong>\<arnuschky\></strong> design-wise, that’s sounds like a nightmare, no?  
<strong>\<moneromooo\></strong> Oh, so linked directly ? I kinda assumed it was gointg to be RPC based.  
<strong>\<fluffypony\></strong> ok well I think we’re getting into an implementation discussion that’s outside of the scope of this meeting  
<strong>\<arnuschky\></strong> I mean, if you don’t have a small and defined API, every bigger change in the wallet will break plugins  
<strong>\<arnuschky\></strong> true )  
<strong>\<fluffypony\></strong> after the dev meeting we can continue this conversation if you guys want  
<strong>\<fluffypony\></strong> but let’s first circle back around  
<strong>\<luigi\></strong> this deserves some kind of design thread like ringct imo  
<strong>\<moneromooo\></strong> Oh, link ?  
<strong>\<fluffypony\></strong> moneromooo: “this deserves”  
<strong>\<fluffypony\></strong> so nothing yet  
<strong>\<moneromooo\></strong> “like ringct”  
<strong>\<fluffypony\></strong> oh  
<strong>\<fluffypony\></strong> I see what you were asking  
<strong>\<luigi\></strong> oh  
<strong>\<moneromooo\></strong> Oh  
<strong>\<fluffypony\></strong> OH  
<strong>\<luigi\></strong> “like ringct is supposed to get”  
<strong>\<moneromooo\></strong> Fair enough.  
<strong>\<fluffypony\></strong> so basically this is all luigi’s fault  
<strong>\<luigi\></strong> warp was gonna go it\!@  
<strong>\<gingeropolous\></strong> its true. i mis-called out luigi on that one  
<strong>\<fluffypony\></strong> warptangent is off sick at the moment  
<strong>\<luigi\></strong> yes  
<strong>\<luigi\></strong> so I blame that  
<strong>\<fluffypony\></strong> I blame Canada  
<strong>\<fluffypony\></strong> ok back on track  
<strong>\<fluffypony\></strong> since the last meeting the bulk of the PRs have been bug fixes  
<strong>\<fluffypony\></strong> and changes to the way we access the DB as discussed at the beginning  
<strong>\<fluffypony\></strong> we also had a huge discussion about how to handle mixins below the minimum in the RPC call  
<strong>\<fluffypony\></strong> which was then implemented in \#715  
<strong>\<fluffypony\></strong> I’m also going to try to personally spend some time on the text that users see, things like the level 0 logging output and the CLI flag help  
<strong>\<luigi\></strong> oh I was gonna do that  
<strong>\<luigi\></strong> but then I didn’t  
<strong>\<fluffypony\></strong> luigi we can do it together  
<strong>\<luigi\></strong> awwww  
<strong>\<fluffypony\></strong> I can show you the world, shining shimmering splendid  
<strong>\<gingeropolous\></strong> take you wonder by wonder  
<strong>\<fluffypony\></strong> lol  
<strong>\<fluffypony\></strong> also \#728 was a little contentious  
<strong>\<fluffypony\></strong> so we created a company called Mixinstream that has hired all the contributors  
<strong>\<palexander\></strong> heh heh  
<strong>\<fluffypony\></strong> and gingeropolous has launched Monero Classic  
<strong>\<gingeropolous\></strong> ( sorry )  
<strong>\<fluffypony\></strong> -P  
<strong>\<fluffypony\></strong> ok so \#728 is Ilya’s work as part of the GUI effort  
<strong>\<dEBRUYNE\></strong> Can I launch unlimited?  
<strong>\<fluffypony\></strong> he was struggling with wallet2, and decided to break it out into something more logical and usable  
<strong>\<fluffypony\></strong> (to him at any rate)  
<strong>\<ArticMine\></strong> What makes it contentious?  
<strong>\<fluffypony\></strong> ArticMine I’ll get to that now  
<strong>\<fluffypony\></strong> he’s unintuitively called it wallet2\_api, which is a little confusing  
<strong>\<fluffypony\></strong> but basically a lot of it is a wallet2\_api call which then does little additional logic, and mainly just passes stuff back to wallet2  
<strong>\<fluffypony\></strong> and there’s a lot of DRY-violating code because of it  
<strong>\<fluffypony\></strong> obviously there was some push back, not to prevent merging it  
<strong>\<fluffypony\></strong> but more to understand the thought process  
<strong>\<moneromooo\></strong> Define DRY ?  
<strong>\<iam6yearsold\></strong> DRY violating scares the shit out of me  
<strong>\<gingeropolous\></strong> https//en.wikipedia.org/wiki/Don%t\_repeat\_yourself  
<strong>\<gingeropolous\></strong> maybe  
<strong>\<fluffypony\></strong> yes  
<strong>\<fluffypony\></strong> iam6yearsold DRY violations are just where you have a piece of code in two places  
<strong>\<fluffypony\></strong> so any changes have to happen in both  
<strong>\<fluffypony\></strong> we can treat the DRY-violating code as a temporary issue, though  
<strong>\<iam6yearsold\></strong> two places = more opportunity for error  
<strong>\<fluffypony\></strong> as we’re going to wait until Ilya is done with it  
<strong>\<ArticMine\></strong> Which makes maintenance much harder  
<strong>\<fluffypony\></strong> and then we’ll either drop wallet2 and replace it with the new wallet API  
<strong>\<fluffypony\></strong> (ie. replace the simplewallet calls as well)  
<strong>\<fluffypony\></strong> or if it’s just a pointless layer we’ll have to go the opposite route  
<strong>\<fluffypony\></strong> and change his Qt callers to use wallet2  
<strong>\<fluffypony\></strong> as it stands it’s kinda undecided and we’ll have to see how Ilya goes  
<strong>\<ArticMine\></strong> Is Ilya aware of the concern?  
<strong>\<fluffypony\></strong> ArticMine yes, we had some discussion on the PR, and othe has also spoken to him afaik  
<strong>\<fluffypony\></strong> he was responsive on the PR comments, but this isn’t Bitcoin  
<strong>\<fluffypony\></strong> we don’t ACK NACK utACK for years before merging somethingm  
<strong>\<fluffypony\></strong> aintnobodygottimeforthat.gif  
<strong>\<luigi\></strong> utNACK  
<strong>\<fluffypony\></strong> luigi \#networknerd  
<strong>\<moneromooo\></strong> utACK was not a typo ?  
<strong>\<luigi\></strong> no  
<strong>\<luigi\></strong> means untested  
<strong>\<luigi\></strong> conceptACK or similar  
<strong>\<fluffypony\></strong> yeah  
<strong>\<fluffypony\></strong> moneromooo https//lists.linuxfoundation.org/pipermail/bitcoin-dev/-December/71.html  
<strong>\<fluffypony\></strong> if you’re interested  
<strong>\<hyc\></strong> crap  
<strong>\<fluffypony\></strong> LOL  
<strong>\<fluffypony\></strong> PasteGate 2.0  
<strong>\<gingeropolous\></strong> internets  
<strong>\<othe\></strong> ur pasting skills suck  
<strong>\<dEBRUYNE\></strong> Hahah  
<strong>\<fluffypony\></strong> othe pasting is a scam  
<strong>\<hyc\></strong> that’s how I write all my patches  
<strong>\<fluffypony\></strong> I just copy-and-paste code from StackExchange  
<strong>\<gingeropolous\></strong> thats my job  
<strong>\<fluffypony\></strong> heh  
<strong>\<fluffypony\></strong> ok so anyone who can reproduce the 0.9.2 segfault please try latest master  
<strong>\<fluffypony\></strong> and if you’re still segfaulting let us know  
<strong>\<fluffypony\></strong> else we’re going to do a point release on Monday  
<strong>\<fluffypony\></strong> 0.9.3, I guess?  
<strong>\<luigi\></strong> hrm  
<strong>\<fluffypony\></strong> or 0.9.2.1  
<strong>\<luigi\></strong> we’re gonna run out of numbers at this rate  
<strong>\<fluffypony\></strong> yeah we are  
<strong>\<luigi\></strong> oh wait  
<strong>\<hyc\></strong> 0921  
<strong>\<luigi\></strong> we have 0.10  
<strong>\<luigi\></strong> nevermind  
<strong>\<iam6yearsold\></strong> will there be multiple devs in IRC at time of hard fork this week just in case? I see a few pools still on old cold and probably a few users too  
<strong>\<fluffypony\></strong> yes we just do a Bitcoin  
<strong>\<moneromooo\></strong> No chance, there’s an infinity of those.  
<strong>\<fluffypony\></strong> 0.11  
<strong>\<fluffypony\></strong> iam6yearsold yes, and we’ve reached out to as many of them as we can  
<strong>\<luigi\></strong> is 0.10 supposed to be for next hard fork?  
<strong>\<fluffypony\></strong> luigi fork that  
<strong>\<fluffypony\></strong> when warptangent is back we’ll see how it goes on ringCT  
<strong>\<fluffypony\></strong> and make a more concrete decision as to the timing of the next fork  
<strong>\<dEBRUYNE\></strong> iam6yearsold The hardfork will approximately take place at 13:00 UTC, so both US and Europe will probably be awake  
<strong>\<dEBRUYNE\></strong> and Asia of course  
<strong>\<luigi\></strong> everyone will be awake  
<strong>\<fluffypony\></strong> even me  
<strong>\<dEBRUYNE\></strong> hawaii will probably be asleep  
<strong>\<dEBRUYNE\></strong> -P  
<strong>\<fluffypony\></strong> heh  
<strong>\<dEBRUYNE\></strong> fwiw\!  
<strong>\<luigi\></strong> wat  
<strong>\<Wolf\`\></strong> lol  
<strong>\<smooth\></strong> we should also consider what else we should go in the next major version besides ringct (doesn’t need to be discussed now)  
<strong>\<dEBRUYNE\></strong> uh I meant UTC btw  
<strong>\<dEBRUYNE\></strong> you muricans with AM/PM  
<strong>\<Wolf\`\></strong> who got drunk and posted about a party in \#monero-dev  
<strong>\<luigi\></strong> oh  
<strong>\<luigi\></strong> then america won’t be up  
<strong>\<moneromooo\></strong> The db reorg seems like a good candidate.  
<strong>\<luigi\></strong> oh well  
<strong>\<fluffypony\></strong> smooth agreed  
<strong>\<dEBRUYNE\></strong> east coast will right?  
<strong>\<luigi\></strong> sure ish  
<strong>\<dEBRUYNE\></strong> You better set your alarm luigi  
<strong>\<dEBRUYNE\></strong> :-P  
<strong>\<fluffypony\></strong> Surae is also going to be picking up MRL-6 in the summer  
<strong>\<fluffypony\></strong> he has some ideas about how to complete that  
<strong>\<dEBRUYNE\></strong> MRL-6 is multisig?  
<strong>\<iam6yearsold\></strong> I will party hard if fork happens with no drama  
<strong>\<fluffypony\></strong> dEBRUYNE: no  
<strong>\<fluffypony\></strong> https//github.com/monero-project/research-lab/tree/master/publications/MRL-%-%Difficulty%Adjustment%Algorithms%in%Cryptocurrency%Protocols  
<strong>\<dEBRUYNE\></strong> oh cool, thanks  
<strong>\<moneromooo\></strong> How do get cmake to tell you the commands it’s running ?  
<strong>\<luigi\></strong> we have diff, we have db stuff, we have fee stuff  
<strong>\<fluffypony</strong>\> moneromooo: I normally make VERBOSE=1  
<strong>\<moneromooo\></strong> Thanks, I was trying V=1  
<strong>\<luigi\></strong> I like my V=2  
<strong>\<fluffypony\></strong> ok - any last things to add  
<strong>\<fluffypony\></strong> or can we call it?  
<strong>\<luigi\></strong> call it
