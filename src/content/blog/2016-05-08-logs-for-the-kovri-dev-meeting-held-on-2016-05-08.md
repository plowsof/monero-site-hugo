---
title: Logs for the Kovri Dev Meeting Held on 2016-05-08
summary: Mac / BSD support moving forward
tags: [dev diaries, i2p, crypto]
author: dEBRUYNE / fluffypony
---

# Logs

<strong>\<anonimal\></strong> Hi fluffypony  
<strong>\<fluffypony\></strong> hiiii  
<strong>\<fluffypony\></strong> was just about to check if you're around :)  
<strong>\<anonimal\></strong> Hi everyone, I think meeting-bot is still online  
<strong>\<fluffypony\></strong> yes it is  
<strong>\<fluffypony\></strong> coming through loud and clear on this side  
<strong>\* anonimal</strong> reading backlog  
<strong>\<anonimal\></strong> Hi moneromoo.  
<strong>\<anonimal\></strong> Hi psi, uncrustify configs? Can you explain?  
<strong>\<psi\></strong> uncrustify is a code styler for c/c++  
<strong>\<fluffypony\></strong> I've never heard of it, plz tell me more psi?  
<strong>\<psi\></strong> it auto formats the code  
<strong>\* psi</strong> gets relevant links  
<strong>\<psi\></strong> <https://github.com/uncrustify/uncrustify>  
<strong>\<anonimal\></strong> I know that psi, but why for \_.conf?  
<strong>\<psi\></strong> i don;t understand?  
<strong>\<psi\></strong> what about \_.conf?  
<strong>\<fluffypony\></strong> oh anonimal  
<strong>\<fluffypony\></strong> not for \*.conf  
<strong>\<fluffypony\></strong> he means conf file for uncrustify matching our coding style  
<strong>\<psi\></strong> damn lag  
<strong>\* psi</strong> waits to catch up  
<strong>\<psi\></strong> fluffypony: right  
<strong>\* anonimal</strong> back  
<strong>\<fluffypony\></strong> wb  
<strong>\<anonimal\></strong> To answer the question, no I don't have an uncrustify config for kovri.  
<strong>\<anonimal\></strong> Just a simple .vimrc.  
<strong>\<anonimal\></strong> I can take a look at creating a config after \#174 is resolved.  
<strong>\<anonimal\></strong> fluffypony: I saw your comment in \#56, what system are you runnning?  
<strong>\<fluffypony\></strong> anonimal: Ubuntu 14.04  
<strong>\<fluffypony\></strong> and there's no Boost 1.59 / 1.60 available  
<strong>\<fluffypony\></strong> but that little hack worked  
<strong>\<anonimal\></strong> 1.54 should work though  
<strong>\* anonimal</strong> triple checks  
<strong>\<fluffypony\></strong> I can't use 1.54  
<strong>\<fluffypony\></strong> incompatible with Monero  
<strong>\<psi\></strong> monero needs .56 or higher ?  
<strong>\<fluffypony\></strong> .55 or higher  
<strong>\<psi\></strong> kk  
<strong>\<fluffypony\></strong> so basically .59 or higher if you want both  
<strong>\<anonimal\></strong> I need about 5-15 minutes to build on bsd and osx so I can open the new linkage error tickets I talked about in \#174  
<strong>\<fluffypony\></strong> kk  
<strong>\<psi\></strong> :\\  
<strong>\* anonimal</strong> the only time I have is now and a bit later but the meeting is now so I want to throw it into the topic  
<strong>\* anonimal</strong> still compiling, should be done in 5 or so  
<strong>\<anonimal\></strong> \#monero-dev, FYI, our meetings have always been more organized, on-point, and I've almost always been prepared.  
<strong>\<anonimal\></strong> This one caught me off guard.  
<strong>\<anonimal\></strong> (last minute suggestion by fluffypony)  
<strong>\<anonimal\></strong> Sorry for the wait.  
<strong>\<fluffypony\></strong> don't stress, ours are always by the seat of our pants  
<strong>\* anonimal</strong> opening tickets  
<strong>\<anonimal\></strong> Hmf, I need to work with the bsd a bit more before posting.  
<strong>\<anonimal\></strong> Anyway, <https://github.com/monero-project/kovri/issues/175>  
<strong>\<anonimal\></strong> I'm only sitting with this again since I left off \< 24 hours or so ago so,  
<strong>\<anonimal\></strong> I haven't drawn any conclusions yet.  
<strong>\<anonimal\></strong> Has anyone seen this before? \#monero-dev?  
<strong>\* fluffypony</strong> clicks  
<strong>\<fluffypony\></strong> moneromooo: seen anything like that before ?  
<strong>\<fluffypony\></strong> "Undefined symbols for architecture x86\_64"  
<strong>\<anonimal\></strong> The usual 'Undefined symbols for architecture x86\_64' has been an osx complaint on this machine in the past.  
<strong>\<moneromooo\></strong> Not as such. I've seen plenty of really annoying linking issues though.  
<strong>\<fluffypony\></strong> this is gcc on OS X tho, right ?  
<strong>\<anonimal\></strong> fluffypony: Yes.  
<strong>\<fluffypony\></strong> maybe we're chasing our tails on that  
<strong>\<anonimal\></strong> I don't have time to deal with clang. If we want multi-distro builds, I need to streamline our process.  
<strong>\<anonimal\></strong> for macosx, clang won't build because it doesn't like the things I did for the reseed rewrite and,  
<strong>\<anonimal\></strong> I don't have time to keep-up with llvm development.  
<strong>\<anonimal\></strong> So, thoughts?  
<strong>\<fluffypony\></strong> rewrite everything in C :-P  
<strong>\<anonimal\></strong> lol  
<strong>\<fluffypony\></strong> ok my suggestion is that we eschew OS X / BSD compatibility for the moment  
<strong>\<fluffypony\></strong> until we can fix Clang support  
<strong>\<anonimal\></strong> Thanks moneromoo. I'm glad this isn't just a kovri thing.  
<strong>\<fluffypony\></strong> rather than trying to fudge it  
<strong>\<anonimal\></strong> Well that's the problem, this won't be the only issue.  
<strong>\<fluffypony\></strong> yeah I know  
<strong>\<anonimal\></strong> And I'll end up wasting time juggling compilers instead of working on other things.  
<strong>\<fluffypony\></strong> I mean that can be a later piece of work  
<strong>\<fluffypony\></strong> let's focus on getting it working on one Linux and Windows, where we're running gcc and it's fine  
<strong>\<anonimal\></strong> fluffypony: what part will be the later piece of work?  
<strong>\<fluffypony\></strong> anonimal: fixing Clang incompatibilities  
<strong>\<moneromooo\></strong> I don't use OSX btw, so kinda ignore what I said above.  
<strong>\<anonimal\></strong> Ok sounds great, I'll focus on linux/win building.  
<strong>\<anonimal\></strong> Should we remove osx/bsd build instructions from BUILDING.md?  
<strong>\<anonimal\></strong> Or I'll just open the bsd ticket and maybe someone will see it?  
<strong>\<fluffypony\></strong> yeah, I think let's make a note that it's broken on OS X / BSD for the moment, and that contributors are welcome to fix  
<strong>\<fluffypony\></strong> kk  
<strong>\<anonimal\></strong> Ok, I'll add the note.  
<strong>\<anonimal\></strong> Any other questions/comments on \#175?  
<strong>\<fluffypony\></strong> no not yet  
<strong>\<fluffypony\></strong> I mean no not atm, lol  
<strong>\<anonimal\></strong> Ok, I'll add a note in \#174 about what we discussed.  
<strong>\<anonimal\></strong> And part 1) in \#174, apparently there is an env variable I can set to get it to work.  
<strong>\<anonimal\></strong> Not the first travis issue I've had to deal with.  
<strong>\<anonimal\></strong> Oh well, they are growing quite nicely IMHO.  
<strong>\<fluffypony\></strong> travis issues are growing quite nicely ?  
<strong>\<anonimal\></strong> lol, yes, and I meant their project as a whole.  
<strong>\<fluffypony\></strong> lol  
<strong>\<anonimal\></strong> Ok, hour is up. Anything else pressing?  
<strong>\<fluffypony\></strong> I don't think so - this was kinda an interim meeting because Kovri's was last week  
<strong>\<fluffypony\></strong> so this brings them into line  
<strong>\<fluffypony\></strong> next one on May 22nd, same time  
<strong>\<anonimal\></strong> Ok, I'll mark the calendar.  
<strong>\<anonimal\></strong> Thanks everyone.  
<strong>\<fluffypony\></strong> thank you
