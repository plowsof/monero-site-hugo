---
title: Logs for the Kovri Dev Meeting Held on 2016-10-02
summary: Brief review of what has been completed since last meeting, Salti (a Firefox extension similiar to the Tor Browser Bundle), Kovri Logo, code & open tickets discussion, Kovri API discussion, Kovri and Monero integration
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

### Overview

An overview [can be found on Hello Monero](https://hellomonero.com/article/monero-and-kovri-dev-meeting-note-highlights-2016-10-02)

### Logs

<strong>\<fluffypony\></strong> anonimal: all yours :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. ∫alti <https://github.com/EinMByte/salti>  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. “Kovri Garlic Router Project” + logo  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. \#46  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. \#337 <https://geti2p.net/en/docs/naming>  
<strong>\<meeting-bot\> \[anonimal\]</strong> 7. API discussion with `#monero-dev` (\#350 \#351)  
<strong>\<meeting-bot\> \[anonimal\]</strong> 8. Code + ticket discussion / Q &amp; A  
<strong>\<meeting-bot\> \[anonimal\]</strong> 9. Any additional meeting items  
<strong>\<meeting-bot\> \[anonimal\]</strong> 10. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anonimal\]</strong> 1. Greetings  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> UDP meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Hi  
<strong>\<meeting-bot\> \[anonimal\]</strong> 2. Brief review of what’s been completed since the previous meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> Areas of work done or completed since last meeting 3 weeks ago:  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Transports improvements/fixes and EinMByte’s SSU branch was merged\!  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Client/app improvements/fixes and client-crypto related (client signing type, https ciphers, etc.)  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Almost all Coverity issues resolved, still a handful left  
<strong>\<meeting-bot\> \[anonimal\]</strong> - Fixes/enhancements and more  
<strong>\<meeting-bot\> \[anonimal\]</strong> - pero’s fantastic work with the logo  
<strong>\<meeting-bot\> \[anonimal\]</strong> Oh, .ny new open issues - that’s a good thing though, right? ;)  
<strong>\<fluffypony\></strong> lol  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else did I miss for 2. or move onto 3.?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> No, go ahead. I have only limited time so let’s be productive  
<strong>\<fluffypony\></strong> 3 plz  
<strong>\<meeting-bot\> \* anonimal</strong> having hard time keeping track of all the work that passes over several weeks; its usually a very broad range of areas  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3. ∫alti <https://github.com/EinMByte/salti>  
<strong>\<meeting-bot\> \[anonimal\]</strong> So, EinMByte and I are starting preliminary work on a firefox extension that will tremendously help Kovri and I2P  
<strong>\<meeting-bot\> \[anonimal\]</strong> I just want to mention this here in case there are any interested webdevs  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything you want to add EinMByte?  
<strong>\<fluffypony\></strong> Salti is basically like the Kovri GUI :-P  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony: No it isn’t  
<strong>\<meeting-bot\> \[EinMByte\]</strong> The kovri GUI is called qtoopie  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: no, the GUI does not exist yet.  
<strong>\<meeting-bot\> \[anonimal\]</strong> qtoopie is an i2pcontrol client.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Salti is a firefox add-on similar to Tor browser bundle  
<strong>\<fluffypony\></strong> lol  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Yes (but see also the relevant zzz.i2p thread from long ago)  
<strong>\* fluffypony</strong> was making a joke  
<strong>\<meeting-bot\> \* anonimal</strong> doesn’t have time to search zzz.i2p, link appreciated  
<strong>\<meeting-bot\> \[anonimal\]</strong> Any webdevs present?  
<strong>\<meeting-bot\> \* EinMByte</strong> doesn’t have time to find zzz.i2p topic  
<strong>\<patthehuman\></strong> i could technically be a webdev  
<strong>\<patthehuman\></strong> im c/c++ swift/obj-c nodejs/MEAN stack  
<strong>\<meeting-bot\> \[anonimal\]</strong> Hi patthehuman. Have you done any work with firefox add-ons?  
<strong>\<patthehuman\></strong> no, however, i dont think it would be very difficult  
<strong>\<meeting-bot\> \[EinMByte\]</strong> We won’t be needing very complex stuff by the way, just using the webextensions API  
<strong>\<patthehuman\></strong> would it be chrome and firefox..?  
<strong>\<meeting-bot\> \[anonimal\]</strong> patthehuman: webext I believe could support both? but we’re aiming for firefox.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (we’ll be setting a few settings and intercepting a few requests)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> patthehuman: yes  
<strong>\<patthehuman\></strong> mk  
<strong>\<meeting-bot\> \[anonimal\]</strong> patthehuman: we can give more details after the meeting if you idle \#kovri-dev  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (although initially firefox, but the API should be mostly the same)  
<strong>\<patthehuman\></strong> ok  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 3.?  
<strong>\<patthehuman\></strong> ill stick around, interested in hearing full scale  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Let’s move to 4  
<strong>\<meeting-bot\> \[anonimal\]</strong> 4. “Kovri Garlic Router Project” + logo  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: you there?  
<strong>\<pero\></strong> yep  
<strong>\<pero\></strong> want me to take over?  
<strong>\<meeting-bot\> \[anonimal\]</strong> What do you have for us today?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Let’s spend very little time with the visual aspect, we have bigger issues to tackle with kovri  
<strong>\<meeting-bot\> \[anonimal\]</strong> Just a run down so everyone knows where we are  
<strong>\<meeting-bot\> \[anonimal\]</strong> And links if possible  
<strong>\<pero\></strong> <http://imgur.com/a/ptOHb>  
<strong>\<pero\></strong> after a ‘long’ process we’re down to 3 fonts  
<strong>\<pero\></strong> the idea is to pick the font with the best looking letters that comprise the word kovri  
<strong>\<meeting-bot\> \[anonimal\]</strong> And what about <https://i.imgur.com/UDsSuTg.png>  
<strong>\<pero\></strong> and/or eliminate some concepts  
<strong>\<meeting-bot\> \[anonimal\]</strong> I guess Coral is out of the question  
<strong>\<patthehuman\></strong> lato second from bottom  
<strong>\<pero\></strong> yea coral was cut  
<strong>\<pero\></strong> work sans is largely similar and coral seemed inferior on some letters as well as less versatile at smaller font sizes iirc  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I’d also drop open sans  
<strong>\<pero\></strong> in the ‘a’ system  
<strong>\<pero\></strong> exo 2 is the logo font - but it doesn’t work as well for text  
<strong>\<pero\></strong> so i chose open sans to complement it  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Sorry, I mean the exp 2 / open sans combination  
<strong>\<pero\></strong> a5 features exo2 as subtext so you can see how that would look like  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But overall, the differences are really minor. Just trying to reduce the search space  
<strong>\<pero\></strong> i personally think not going with A or B would be a mistake  
<strong>\<pero\></strong> their K is really nice and adds a subtle touch of personality  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: its unfair because I can’t accurately compare c4 because of orange subtext  
<strong>\<pero\></strong> hmm  
<strong>\<meeting-bot\> \[anonimal\]</strong> I prefer work sans because the k contracts with the orange curve in the garlic  
<strong>\<meeting-bot\> \[anonimal\]</strong> So is our next step font?  
<strong>\<pero\></strong> <http://imgur.com/a/DOcyy>  
<strong>\<meeting-bot\> \[anonimal\]</strong> Is subtext really that thick with work sans? Eww  
<strong>\* fluffypony</strong> isn’t wild about the orange subtext  
<strong>\<pero\></strong> yea the orange subtext sucks imo  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok, let’s handle this another time  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (or use a random number generator)  
<strong>\<pero\></strong> no it could be thinner  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Let’s go with column b then  
<strong>\<meeting-bot\> \[anonimal\]</strong> lol no way on the random gen  
<strong>\<fluffypony\></strong> lol random number gen could be fun  
<strong>\<pero\></strong> imgur is also ‘optimizing’ the png  
<strong>\<fluffypony\></strong> “best of 3?”  
<strong>\<pero\></strong> keep in mind ^^^  
<strong>\<endogenic\></strong> just my two cents - you probably want the text to be relatively heavier than the logo so it jumps out because it’s not an english or otherwise generally known word, and so the logo imo should be visually secondary when composed with the name. think about readability, especially if the user doesn’t have 20/20 vision or is in a hurry  
<strong>\<endogenic\></strong> the actual face itself is not a huge issue imo  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: let’s narrow down our options to rows 2, 4, and 6  
<strong>\<meeting-bot\> \[anonimal\]</strong> Can you throw those onto a page?  
<strong>\<pero\></strong> there probably will be instances where the ‘router project’ text is unnecessary  
<strong>\<fluffypony\></strong> I think rows 3 and 4 won’t work because, as endogenic pointed out, kovri is not an English word  
<strong>\<fluffypony\></strong> looks like kavri  
<strong>\<pero\></strong> and just the logo and kovri would suffice  
<strong>\<meeting-bot\> \[anonimal\]</strong> Are we all talking about <https://i.imgur.com/Ge1FZTp.png> ?  
<strong>\<pero\></strong> ideally as a brand it should be able to stand out on its own  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, the garlic as an “o” could be confusing  
<strong>\<fluffypony\></strong> anonimal no, I’m looking at <http://imgur.com/a/DOcyy>  
<strong>\<meeting-bot\> \[anonimal\]</strong> Same thing  
<strong>\<endogenic\></strong> pero: for that reason consider favoring options with tighter kerning  
<strong>\<fluffypony\></strong> oh  
<strong>\<fluffypony\></strong> lol  
<strong>\<meeting-bot\> \[anonimal\]</strong> Who in their right mind things that garlic is an ‘A’?  
<strong>\<pero\></strong> another thing to add  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So let’s narrow it down to 2 and 6  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> 2 in Open Sans is the most readable  
<strong>\<pero\></strong> the garlic wasn’t designed with this use in mind  
<strong>\<pero\></strong> the garlic could be optimized down the road  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Remember that the spectator potentially doesn’t know “kovri”  
<strong>\<pero\></strong> ideally after a font has been chosen  
<strong>\<pero\></strong> to more resemble an o and to slide seamlessly into the font  
<strong>\<meeting-bot\> \[EinMByte\]</strong> At least it might add additional confusion, which is bad  
<strong>\<endogenic\></strong> EinMByte: exactly. the question is how it could be confirmed it’s not an A  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, all in favor of exo2  
<strong>\<pero\></strong> i’m however not qualified to do that  
<strong>\<meeting-bot\> \[anonimal\]</strong> Any votes for exo2/open sans?  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> Yes  
<strong>\<meeting-bot\> \[EinMByte\]</strong> exo2 is fine for me, but I also agree that the “Garlic Routing Project” text should be optional  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> exo2 is fine  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (So on the website, for example, we should have the text. But potentially not everywhere)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Any objections against exo2?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I count 2 votes for exo2/open sans.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Any votes for Lato?  
<strong>\<pero\></strong> i vote lato  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Any votes for work sans?  
<strong>\<endogenic\></strong> i also like lato  
<strong>\<fluffypony\></strong> lato from my side  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok, let’s eliminate work sans.  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3 votes for Lato.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Any votes for Work Sans?  
<strong>\<meeting-bot\> \[anonimal\]</strong> 0 votes for Work Sans  
<strong>\<meeting-bot\> \[anonimal\]</strong> I haven’t voted  
<strong>\<meeting-bot\> \* anonimal</strong> looks  
<strong>\<patthehuman\></strong> i vote for Lato  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Are we going to decide on the logo today or not? If so, we should hurry (if we want to discuss API still)  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: why does a6 look so fat?  
<strong>\<pero\></strong> shouldn’t be that difficult to throw up exo2 versions of lato variants in the future  
<strong>\<pero\></strong> in case that’s still up for debatable  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte that’s up to moneromooo because I really don’t think anyone else there is interested in API chat (afaict)  
<strong>\<pero\></strong> because it is fat :P  
<strong>\<patthehuman\></strong> yb  
<strong>\<meeting-bot\> \[i2p-relay\] {-ArticMine}</strong> I have to leave  
\*\*\<patthehuman\> im interested in api cha  
<strong>\<endogenic\></strong> maybe we should have a \#monero-design? :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte if we don’t decide soon, website doesn’t get done  
<strong>\<pero\></strong> i went with a heavier weight for that variant arbitrarily  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I have no particular wish about that, don’t mind me.  
<strong>\<fluffypony\></strong> let’s move ahead  
<strong>\<fluffypony\></strong> the logo already took up the entire last meeting  
<strong>\<meeting-bot\> \[anonimal\]</strong> 3 minutes  
<strong>\<meeting-bot\> \[anonimal\]</strong> Let me vote please\!  
<strong>\<meeting-bot\> \[EinMByte\]</strong> We should at least plan when to discuss the API, so let’s decide quickly on the logo :)  
<strong>\<patthehuman\></strong> LATO  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: why should I choose exo2  
<strong>\<pero\></strong> its advantage seems to be technological look  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Please decide, we’re moving too slowly here  
<strong>\<pero\></strong> a secondary adv is that we can pair with open sans which is extremely versatile  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte, we have 30 minutes, please be patient.  
<strong>\<pero\></strong> can be used at extremely small sizes for things like massive tables of data  
<strong>\<pero\></strong> whereas using open sans to complement a lato branding scheme wouldn’t make much sense  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: how about this: can you whip up another sample for after the meeting but <em>only</em> exo2 and lato and doing various sizes that you think are appropriate?  
<strong>\<pero\></strong> i think that makes the most sense as a next step  
<strong>\<meeting-bot\> \[anonimal\]</strong> We can probably come to a final conclusion post-meeting or sometime this week.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, thanks pero.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Moving on,  
<strong>\<meeting-bot\> \[anonimal\]</strong> 5. \#46  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: ^  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony…  
<strong>\<pero\></strong> did you skip over the ‘garlic router’ discussion?  
<strong>\<fluffypony\></strong> ok - got a first draft to push up, but need to finish fixing the forum first  
<strong>\<meeting-bot\> \[anonimal\]</strong> pero: just go with it for now but also do without subtext too please  
<strong>\<meeting-bot\> \[EinMByte\]</strong> ETA?  
<strong>\<patthehuman\></strong> whats wrong with the forum?  
<strong>\<pero\></strong> ok  
<strong>\<fluffypony\></strong> EinMByte: no clue  
<strong>\<fluffypony\></strong> patthehuman: PHP7 broke a bunch of stuff  
<strong>\<meeting-bot\> \[anonimal\]</strong> patthehuman: fluffypony is fixing it  
\*\*\<patthehuman\> ok  
<strong>\<fluffypony\></strong> some of it was non-obvious until we had a new dep and composer wrecked everything  
<strong>\<patthehuman\></strong> ill be around if you need help  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Let’s not discuss the monero forum here  
<strong>\<patthehuman\></strong> php7 wrecked a lot of my shit at work so ive been down this path  
<strong>\<patthehuman\></strong> sure  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: should EinMByte and I not ask for ETA for website?  
<strong>\<fluffypony\></strong> anonimal: I’ll push my changes once the forum is back up, since all static objects are served off that repo anyway  
<strong>\<meeting-bot\> \[anonimal\]</strong> Worst case scenario, we release with just a repo and wiki.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, moving on  
<strong>\<meeting-bot\> \[anonimal\]</strong> 6. \#337 <https://geti2p.net/en/docs/naming>  
<strong>\<meeting-bot\> \[anonimal\]</strong> What happens is that any addresses that are saved with an addresshelper are simply inserted into ./addressbook but not user<em>hosts.txt (or similar)  
<strong>\<meeting-bot\> \[anonimal\]</strong> There are also various other issues, let me pull up the ticket  
<strong>\<meeting-bot\> \[anonimal\]</strong> “For this ticket, we should discuss if we’re to have separate subscription files because we currently only use hosts.txt. Also, if we hand edit the file, it will be overridden upon next fetch from a any publisher.  
<strong>\<meeting-bot\> \[anonimal\]</strong> With a little design work, we can easily implement other files that won’t be overridden. There’s also the question of whether we want to have separate files for separate publishers.”  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Easiest would be to add an additional file that’s user-configurable, but maybe it’s nicer to just update incrementally  
<strong>\<meeting-bot\> \[anonimal\]</strong> hosts.txt is updated every 12 hours. I think we should have user-configurable too.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (although that prings additonal problems)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> \*brings additional  
<strong>\<meeting-bot\> \[Zenified\]</strong> \>prings?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So lets have “hosts.txt” and several other files for the different subscriptions?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yes, that was the idea. I guess the question was how many:  
<strong>\<meeting-bot\> \[EinMByte\]</strong> one for each subscription  
<strong>\<meeting-bot\> \[EinMByte\]</strong> If there’s conflicts, they would ideally be reported to the user  
<strong>\<meeting-bot\> \[anonimal\]</strong> That’ll be tricky if each publisher calls their subscription hosts.txt, we can rename/adjust as needed or concatenate it into on user\_hosts.txt  
<strong>\<meeting-bot\> \[anonimal\]</strong> \*a user\_hosts.txt  
<strong>\<meeting-bot\> \[anonimal\]</strong> And duplicates would be wasteful  
<strong>\<meeting-bot\> \[anonimal\]</strong> (this whole I2P naming scheme is annoying)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> We should rename the files locally  
<strong>\<meeting-bot\> \[anonimal\]</strong> You mean expect the user to call it whatever they want?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> The only hosts.txt file would be the one that the user can change?  
<strong>\<meeting-bot\> \[anonimal\]</strong> No, hosts.txt would always be static and provided upstream, always overridden every 12 hours  
<strong>\<meeting-bot\> \[EinMByte\]</strong> No, when downloading a subscription, put it in a dedicated file?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’m not sure what you’re getting at  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok, so you want “user\_hosts.txt” to be a wile with custom hosts?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> \*file  
<strong>\<meeting-bot\> \[EinMByte\]</strong> That would also work, sure.  
<strong>\<meeting-bot\> \[anonimal\]</strong> We only need 2: one that’s always clobbered every 12 hours, and one that’s never clobbered  
<strong>\<meeting-bot\> \[anonimal\]</strong> The one that’s never clobbered needs a name. It’s “custom” and “private” though.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Also, should every address added with i2paddresshelper \*also\* be inserted into said custom file.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, but we want multiple subscriptions right?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I don’t even think java i2p does that, but I think it should be done.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But not all publishers provide the same set of hosts  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Hence, the need for several hosts.txt files that care clobbered every 12 hours  
<strong>\<meeting-bot\> \[EinMByte\]</strong> \*are  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, we’ll just have to name subscriptions by uri.host()  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, I guess so  
<strong>\<meeting-bot\> \[anonimal\]</strong> and make a private\_hosts.txt that is <em>never</em> clobbered  
<strong>\<meeting-bot\> \[anonimal\]</strong> That actually makes the most sense now, imho.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, that or have an actual database of hosts rather than a bunch of files  
<strong>\<meeting-bot\> \[anonimal\]</strong> We can deal with duplicates and effiency later unless it becomes a massively huge issue.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yeah, a <em>real</em> Db  
<strong>\<meeting-bot\> \[anonimal\]</strong> While we’re at it we can consider that for ./NetDb  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But if we get a real database, it should also be used for profiles etc  
<strong>\<meeting-bot\> \[anonimal\]</strong> Didn’t i2pcpp do something like that?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, it used sqlite  
<strong>\<meeting-bot\> \[anonimal\]</strong> Why was that not continued/exploited?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Was it not ‘efficient’ enough for the magician?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> For the same reason that i2pcpp was not continued  
<strong>\<fluffypony\></strong> you can always use LMDB  
<strong>\<meeting-bot\> \[EinMByte\]</strong> i2pd isn’t based on i2pcpp at all  
<strong>\<meeting-bot\> \[anonimal\]</strong> I know, but he obviously looked at it.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I don’t like how one can’t use network filesystems with LMDB  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes, but decided not add the dependency or so  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So let’s create an issue for using an actual database?  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte then I think we should research sqlite or LMDB or some other option for a longterm database solution. Sound reasonable?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Yes  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, anything else on addressbook?  
<strong>\<fluffypony\></strong> I think it’s all been addressed  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Can you create the issue? If so, let’s move on to 7  
<strong>\<meeting-bot\> \[anonimal\]</strong> Done, \#385  
<strong>\<meeting-bot\> \[anonimal\]</strong> 7. API discussion with \#monero-dev (\#350 \#351)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Monero developers here?  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Yes  
<strong>\<meeting-bot\> \[EinMByte\]</strong> What I mainly want is a clear set of requirements for the API  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Oh I see. Oh. Hmm.  
<strong>\<fluffypony\></strong> yes  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Well, I’m not very much acquainted with the way CN P2P works in the first place…  
<strong>\<meeting-bot\> \[EinMByte\]</strong> e.g. do you want to use streaming, I2NP directly, datagrams…?  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> It’s all TCP, with a simple HTTP server at hte moment.  
<strong>\<meeting-bot\> \[Zenified\]</strong> LMDB is the the real deal  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Doesn’t mean it has to stay that way though.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So you need connections? Probably streaming then  
<strong>\<meeting-bot\> \[anonimal\]</strong> Question: how is monero-core currently talking with monerod?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> The main question to ask is whether you need 1) reliability 2) connections  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> fluffypony: did you intend to replace the P2P stuff with 0MQ ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte I thought we discussed not doing network-based API  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> anonimal: JSON RPC AFAIK.  
<strong>\<fluffypony\></strong> anonimal: JSON RPC API, but we’re replacing that with 0MQ  
<strong>\<fluffypony\></strong> but Kovri will serve the p2p layer  
<strong>\<fluffypony\></strong> not the RPC layer  
<strong>\<fluffypony\></strong> moneromooo: yes with ZMTP  
<strong>\<fluffypony\></strong> <http://zmtp.org>  
<strong>\<fluffypony\></strong> maybe we bundle the ZMTP change and Kovri integration together ?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: No, but we need to know what aspects of the API are most important  
<strong>\<meeting-bot\> \[EinMByte\]</strong> e.g. do we need to focus on making I2NP accessible, or on making streaming accessible  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Or does monero want to be able to create tunnels, etc.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I think monero wants something as simple as a SOCKS proxy  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> We need to be able to find peers without knowing their address in advance.  
<strong>\<meeting-bot\> \[anonimal\]</strong> If connection isn’t made, tough luck and try again later  
<strong>\<meeting-bot\> \[anonimal\]</strong> Oh, nevermind then  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> At the moment, this is done by bootstrapping from a seed server.  
<strong>\<fluffypony\></strong> moneromooo: DNS seeds  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So 0MQ would be TCP-based, so would use streaming  
<strong>\<fluffypony\></strong> yeah so we can do the same  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> That… might be DNS ? I’m not sure.  
<strong>\<fluffypony\></strong> we get seed nodes from DNS seeds with hardcoded fallbacks  
<strong>\<fluffypony\></strong> and then we connect to their .i2p address on the appropriate port  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> And all the DNSSEC or DNScrypt that fluffypony knows about.  
<strong>\<fluffypony\></strong> and request peers  
<strong>\<fluffypony\></strong> and we get a list of .i2p addresses and ports  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Do you want to create a tunnel and then connect to that, or do you want to have a C++ API to also send messages?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Has monero-side drawn up any diagrams for these ideas?  
<strong>\<fluffypony\></strong> anonimal: that’s how it currently works, not ideas  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Is there a concept of “multicast”, where we could send a query to “whomever it may concern” ?  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: you currently get a list of .i2p address and ports?  
<strong>\<fluffypony\></strong> EinMByte: we can do either  
<strong>\<meeting-bot\> \[EinMByte\]</strong> moneromooo: No, don’t think so  
<strong>\<fluffypony\></strong> anonimal: we currently get ipv4 addresses, but we’d perform exactly the same function to get i2p-based peers  
<strong>\<meeting-bot\> \[EinMByte\]</strong> moneromooo: But I can think about multicast in future I2P and even get a proposal going, but it would take years before we actually get it  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> The intent, in this case, would be to request replies from peers that run monero.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> (without having to rely on centralized seeds)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So for DNS, you could use repliable datagrams or streaming.  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte moneromooo: multicast is mentioned in future work <https://geti2p.net/en/docs/how/garlic-routing>  
<strong>\<fluffypony\></strong> DNS seed nodes work, I really don’t think we need to replace that  
<strong>\<fluffypony\></strong> but what we would do on first sync is get both ipv4 <em>and</em> i2p peers  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: Yes, but there’s no decent proposal right now. I also need to check out the LS2 proposal, it somewhat relates  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony: Ok, assuming you can store I2P addresses in DNS records  
<strong>\<meeting-bot\> \[anonimal\]</strong> moneromooo: proposals also sit there for years so I wouldn’t expect anything to happen anytime soon  
<strong>\<fluffypony\></strong> after that a node maintains its own white / black / gray lists, and gets a peerlist every time it connects to a new peer  
<strong>\<fluffypony\></strong> EinMByte: TXT records :)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> fluffypony: Ok.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> It’s something that seems fairly self contained anyway, so could be changed at a later date.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So you need to decide between 1) use I2P direcly with a C++ API 2) create tunnels using a C++ API and then connect to them with SOCKS or so  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I don’t know the difference between these options.  
<strong>\<meeting-bot\> \[anonimal\]</strong> I don’t think they need to care about creating tunnels  
<strong>\<meeting-bot\> \[EinMByte\]</strong> In any case kovri wants to provide the API to do 1  
<strong>\<fluffypony\></strong> yes - and I’d probably lean towards the C++ API  
<strong>\<meeting-bot\> \[anonimal\]</strong> They need to know if they can get through or not, that’s a given though.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> So it looks like monero would be using esentially use the streaming API?  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I’d imagine something that looks like a socket API, just using I2P addresses instead of IP:port :)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> s/use//  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> By streaming, do you mean TCP ?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But maybe for DNS you’d also want repliable datagrams  
<strong>\<meeting-bot\> \[anonimal\]</strong> I can’t answer for them until one of them sits down and reads the spec  
<strong>\<meeting-bot\> \[EinMByte\]</strong> moneromooo: streaming is something that looks a lot like TCP but over I2P  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Then that’s what we’d use in a straight port, modulo the seed stuff.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Most applications use streaming one way or another  
<strong>\<meeting-bot\> \[EinMByte\]</strong> I don’t know your architecture, but it may be simpler to create a tunnel if you want to route everything to I2P  
<strong>\<meeting-bot\> \[EinMByte\]</strong> \*through  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony moneromooo: what were the arugments against using SOCKS proxy?  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> By creating a tunnel, do you mean selecting the hoops directly ?  
<strong>\<fluffypony\></strong> no arguments - we have no idea what you’d recommend :)  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: KISS  
<strong>\<meeting-bot\> \[EinMByte\]</strong> moneromooo: using tunnel in the client-like context here, like a local SOCKS proxy which delivers to a dedicated I2P endpoint  
<strong>\<meeting-bot\> \[anonimal\]</strong> monero: we have to meet half-way somehow. I’ll try to dig into more monero if you guys can dig into more kovri.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> SOCKS seems overly complicaed  
<strong>\<meeting-bot\> \[EinMByte\]</strong> \*complicated  
<strong>\<meeting-bot\> \[anonimal\]</strong> IMHO, we should be more on a level playing field at least term wise by now.  
<strong>\<fluffypony\></strong> anonimal: we’ll implement whatever you guys recommend  
<strong>\<meeting-bot\> \[EinMByte\]</strong> If you need many connections, you can’t use the “create a local SOCKS proxy” or so  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte: how so? In terms of providing useful feedback and control, yes.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> We need several, yes. They’re fairly long term. Some will go down, and will be replaced.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Then it would be a lot easier to create tunnels (which use e.g. the streaming protocol) using the C++ API  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Both directions, btw. No client/server.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Streaming is both ways, sure  
<strong>\<meeting-bot\> \[EinMByte\]</strong> datagrams can also be (if repliable)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, so easiest for us is C++ API but is ZMTP worth the extra work?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> anonimal: I don’t think ZMTP matters to us.  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I’d imagine ZMTP is a layer above, and kovri would be oblivious to it.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Good.  
<strong>\<meeting-bot\> \[anonimal\]</strong> So streaming or datagrams or both?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Question is whether using ZMTP would actually be useful when used above I2P, but I’ll leave that to monero devs  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Both, please :)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> But let’s focus on streaming  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (since most I2P applications currently use streaming)  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> But streaming first, yes. We can hardcode peer ids to start with.  
<strong>\<fluffypony\></strong> I guess parts of ZMTP would be useless (eg. end-to-end encryption)  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, C++ API for streaming. That’s entirely on us then, for starters.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Is this written in stone now EinMByte moneromooo fluffypony?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Let’s say it is and move to 8  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> To the extent I know of how CN uses the network… -</em>- :D  
<strong>\<fluffypony\></strong> yes  
<strong>\<meeting-bot\> \[anonimal\]</strong> Yay, big decision step done.  
<strong>\<yardman\></strong> whats set in stone?  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else on 7.?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I have one question:  
<strong>\<fluffypony\></strong> nope  
<strong>\<fluffypony\></strong> yardman: using the i2p C++ API for streaming  
<strong>\<meeting-bot\> \[anonimal\]</strong> What homework can we all do so our next API meeting is more productive?  
<strong>\<meeting-bot\> \[anonimal\]</strong> kovri c++ API  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Design it  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> Well, I have that feeling that the next month or two will be spent on rct performance from my side…  
<strong>\<fluffypony\></strong> anonimal: we haven’t really focused on our current p2p layer because of the ZMTP plan  
<strong>\<meeting-bot\> \[anonimal\]</strong> moneromooo: you mentioned I should look at networking code?  
<strong>\<yardman\></strong> thanks  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> I didn’t, I think. I mentioned I should :D  
<strong>\<meeting-bot\> \[anonimal\]</strong> Oh, lol ok  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> IIRC that p2p code is also kinda new and unfinished.  
<strong>\<fluffypony\></strong> so I don’t know if we should waste much time on analysis of it, or rather look at i2p as a ZMTP transport  
<strong>\<fluffypony\></strong> which could be a VERY nice generalised solution  
<strong>\<fluffypony\></strong> that isn’t Monero-specific  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, I’ll add API for first thing next meeting.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Anything else for 7.?  
<strong>\<fluffypony\></strong> nope  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Nope, 8 please (need to leave soon)  
<strong>\<meeting-bot\> \[anonimal\]</strong> 8. Code + ticket discussion / Q &amp; A  
<strong>\<meeting-bot\> \[anonimal\]</strong> We’re in overtime, I have nothing to say at the moment really.  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony I think there’s an assigned ticket you can easily close  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Me neither, let’s discuss when appropriate  
<strong>\<meeting-bot\> \[anonimal\]</strong> (the codedocs one)  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Will see how much time I get to do v6 peer testing  
<strong>\<fluffypony\></strong> ok will do  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’ll get to more assigned tickets as well.  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, moving on.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Also not sure if \#187 should still be open  
<strong>\<meeting-bot\> \[anonimal\]</strong> 9. Any additional meeting items  
<strong>\<meeting-bot\> \[anonimal\]</strong> EinMByte, ok I’ll take a look after the meeting.  
<strong>\<meeting-bot\> \[EinMByte\]</strong> Ok, no additional meeting items from me  
<strong>\<meeting-bot\> \[anonimal\]</strong> Nor I. fluffypony?  
<strong>\<meeting-bot\> \[anonimal\]</strong> moneromooo?  
<strong>\<fluffypony\></strong> nope  
<strong>\<meeting-bot\> \[anonimal\]</strong> \#monero-dev?  
<strong>\<meeting-bot\> \[i2p-relay\] {-moneromooo}</strong> No  
<strong>\<meeting-bot\> \[anonimal\]</strong> 10. Confirm next meeting date/time  
<strong>\<meeting-bot\> \[anonimal\]</strong> Next week or two weeks?  
<strong>\<meeting-bot\> \[EinMByte\]</strong> 2  
<strong>\<meeting-bot\> \[EinMByte\]</strong> (if we want the API on the list of topics)  
<strong>\<fluffypony\></strong> 2 weeks  
<strong>\<fluffypony\></strong> Oct 16  
<strong>\<meeting-bot\> \[anonimal\]</strong> Same for \#monero-dev?  
<strong>\<meeting-bot\> \[anonimal\]</strong> I’d like to coincide  
<strong>\<meeting-bot\> \[anonimal\]</strong> fluffypony: ^  
<strong>\<fluffypony\></strong> yes  
<strong>\<meeting-bot\> \[anonimal\]</strong> Ok, 2 weeks works for me.  
<strong>\<meeting-bot\> \[anonimal\]</strong> THANKS EVERYONE\!  
<strong>\<fluffypony\></strong> shutting meeting bot down
