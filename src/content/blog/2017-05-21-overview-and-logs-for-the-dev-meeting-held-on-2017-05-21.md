---
title: Overview and Logs for the Dev Meeting Held on 2017-05-21
summary: Sub / disposable addresses, new website, CLI/GUI lightwallet integration
tags: [dev diaries, core, crypto]
author: dEBRUYNE / fluffypony
---

# Overview

An overview [can be found on MoneroBase](https://monerobase.com/wiki/DevMeeting_2017-05-21).

# Logs

<strong>\<endogenic\></strong> we have to do the dev meeting really quietly so the pony can get some sleep  
<strong>\<moneromooo\></strong> 1. Greetings  
<strong>\<moneromooo\></strong> 2. Brief review of what's been completed since the previous meeting  
<strong>\<moneromooo\></strong> 3. Code + ticket discussion / Q &amp; A  
<strong>\<moneromooo\></strong> 4. Any additional meeting items  
<strong>\<moneromooo\></strong> 5. Confirm next meeting date/time  
<strong>\<moneromooo\></strong> (no relay bot btw)  
<strong>\<moneromooo\></strong> So, since last time, I'm not sure what's been merged. Not much I think ? There was the key image flaw made public too.  
<strong>\<moneromooo\></strong> I'm working on abstracting network addresses. Mostly works, but serialization is being a massive pain.  
<strong>\<moneromooo\></strong> Anyone else want to say anything about what they're working on ?  
<strong>\<vtnerd\></strong> eventually I hope to have the amd64-51-30k speedups in wallet2.cpp (assuming fluffy approves)  
<strong>\<vtnerd\></strong> and improve the hex -\> bin performance would be nice too (not nearly ready for a merge though)  
<strong>\<moneromooo\></strong> What is that short for ?  
<strong>\<vtnerd\></strong> oh sorry, the ASM for wallet scanning  
<strong>\<moneromooo\></strong> What are the 51 and 30k short for ?  
<strong>\<vtnerd\></strong> its already written so that it can be removed by cmake, and does not touch the consensus code <em>at all</em>  
<strong>\<vtnerd\></strong> 51-bit limbs and 30k tables  
<strong>\<vtnerd\></strong> 30k table singular, sorry  
<strong>\<moneromooo\></strong> Anyone else doing something nice ? hyc, LMDB wallet code maybe ? :)  
<strong>\<moneromooo\></strong> Nobody else ? tewinget ?  
<strong>\<vtnerd\></strong> everyone is out spending bytecoins  
<strong>\<moneromooo\></strong> Alright. Ticket discussion. The only thing I know is people reporting sync stopping. Some of them are user error, some are corrupt db, but I think there may be something else. I'd need to see good logs for both sides though.  
<strong>\<moneromooo\></strong> Anyone wants to say anything about pending bugs ?  
<strong>\<iDunk\></strong> Testing related... your 1982 works nicely, with no apparent issues after several days. That on a daemon with none to very light load, fwiw.  
<strong>\<moneromooo\></strong> Cool, thanks.  
<strong>\<moneromooo\></strong> About pending bugs: we're still waiting for finalization of the disposable address theory, IIRC RandomRun and knacc were discussing a change recently.  
<strong>\<moneromooo\></strong> knaccc: any comment about this ?  
<strong>\<iDunk\></strong> I'm syncing on Windows right now, albeit with non-default settings. Will report if it gets wedged.  
<strong>\<vtnerd\></strong> change to which portion, disposable addresses or sub-addresses?  
<strong>\<vtnerd\></strong> or I guess you specifically said disposable address  
<strong>\<moneromooo\></strong> I don't remember. It's 1753.  
<strong>\<moneromooo\></strong> I did, but not on purpose :)  
<strong>\<moneromooo\></strong> I have a feeling it'll be a fast meeting.  
<strong>\<moneromooo\></strong> luigi1112: anything new about smaller range proofs ?  
<strong>\<endogenic\></strong> he's out spending bytecoin too  
<strong>\<jollymort\></strong> happened to me today (sync); it just hanged; killed the process and restarted monerod; continued seamlessly  
<strong>\<jollymort\></strong> can re-sync with different loglvl to see if it happens again  
<strong>\<moneromooo\></strong> Next time, don't kill it before you've looked at the thread stack traces.  
<strong>\<moneromooo\></strong> Anything else someone wants to say in the meeting ?  
<strong>\<rehrar\></strong> Kovri test site? :D Not super dev-y, but nobody else says anything.  
<strong>\<moneromooo\></strong> Kovri meeting is in 48 minutes.  
<strong>\<rehrar\></strong> there is no kovri meeting today  
<strong>\<moneromooo\></strong> aw... then feel free.  
<strong>\<moneromooo\></strong> anonimal: around ?  
<strong>\<luigi1112\></strong> moneromooo sorry no. will update soooooon  
<strong>\<moneromooo\></strong> ty  
<strong>\<moneromooo\></strong> Hmm.  
<strong>\<luigi1112\></strong> next meeting will be exciting :-)  
<strong>\<moneromooo\></strong> Well, no test site either then.  
<strong>\<unknownids\></strong> oh baby i know what that means  
<strong>\<unknownids\></strong> i think  
<strong>\<moneromooo\></strong> Next meeting: in two weeks, same time.  
<strong>\<moneromooo\></strong> Done. The only good meetings are short meetings.  
<strong>\<luigi1112\></strong> am I doing this right  
<strong>\<luigi1112\></strong> ann of ann  
<strong>\<jollymort\></strong> mooo, how to use stacktrace?  
<strong>\<moneromooo\></strong> Oh he's back now :)  
<strong>\<moneromooo\></strong> jollymort: gdb /path/to/monerod `pidof monerod`  
<strong>\<moneromooo\></strong> thread apply all bt  
<strong>\<jollymort\></strong> so i can do it while it's running  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<jollymort\></strong> no need to start it in some special way?  
<strong>\<jollymort\></strong> ok  
<strong>\<jollymort\></strong> i'll set loglvl to max also  
<strong>\<jollymort\></strong> and start sync from 0  
<strong>\<moneromooo\></strong> I wouldn't.  
<strong>\<jollymort\></strong> ok, so just restart and wait for it to hang?  
<strong>\<moneromooo\></strong> 3 and 4 are toop spammy for being much use in general usage.  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<moneromooo\></strong> rehrar: free free if you have something to say/show.  
<strong>\<rehrar\></strong> Anyways, Monero test site here: <http://45.32.161.183/> mobile responsive now and a brand new mobile navigation.  
<strong>\<rehrar\></strong> Kovri test site: <http://45.32.171.42/> completely integrated into the Jekyll. The custom CSS framework was ported without issue. This bodes well for my further work on getmonero.org.  
<strong>\<moneromooo\></strong> Looks clean.  
<strong>\<Jaquee\></strong> hi. a bit late to meeting. i'm working on lightwallet integration in cli and gui  
<strong>\<Jaquee\></strong> or wallet2 mostly  
<strong>\<moneromooo\></strong> You mean mymonero ?  
<strong>\<rehrar\></strong> We scrubbed it down.  
<strong>\<Jaquee\></strong> yeah. and openmonero  
<strong>\<Jaquee\></strong> should work with both backends  
<strong>\<Jaquee\></strong> and should be switchable from full wallet to light wallet. vtnerd. would you consider implementing input/output import in mymonero api?  
<strong>\<Jaquee\></strong> <https://github.com/moneroexamples/openmonero/issues/21>  
<strong>\<Jaquee\></strong> would make it possible to switch from full wallet to light wallet without a rescan  
<strong>\<endogenic\></strong> not clear how the mobile experience would go  
<strong>\<endogenic\></strong> just an initial impression  
<strong>\<Jaquee\></strong> ?  
<strong>\<Jaquee\></strong> experience of what?  
<strong>\<endogenic\></strong> as in how user gets wallet file on their mobile and how they pick it  
<strong>\<vtnerd\></strong> I don't know what you mean Jacquee  
<strong>\<vtnerd\></strong> you want to import an existing wallet quickly from a local DB to a mymonero backend ?  
<strong>\<vtnerd\></strong> and also the other direction ?  
<strong>\<luigi1112\></strong> that would be cool. maybe :-)  
<strong>\<Jaquee\></strong> yeah. if i have a full wallet on my desktop and want to use the same wallet on my mobile. I could convert my full wallet to lightwallet by sending my inputs/outputs to mymonero/openmonero backend. And then login as usual on my phone  
<strong>\<Jaquee\></strong> with seed  
<strong>\<Jaquee\></strong> without paying the 1 xmr rescan fee  
<strong>\<Jaquee\></strong> that was my idea  
<strong>\<Jaquee\></strong> so the magic happens in desktop wallet.  
<strong>\<Jaquee\></strong> on mobile you only login as usual  
<strong>\<vtnerd\></strong> yeah, but its doable but I would have to think about it a bit  
<strong>\<vtnerd\></strong> the backend would still want to verify correctness, so its not stomping on someone elses coins, etc  
<strong>\<vtnerd\></strong> but it would be doing much less work  
<strong>\<Jaquee\></strong> ok. yeah backend could verify with view key  
<strong>\<Jaquee\></strong> that's probably best  
<strong>\<vtnerd\></strong> yes. but it would only be looking at the set of outputs specified in the RPC call which will be much faster  
<strong>\<Jaquee\></strong> exactly  
<strong>\<endogenic\></strong> Jaquee: ic  
<strong>\<vtnerd\></strong> yeah so the import out will be much easier, and you can almost do it with unspent\_outs call  
<strong>\<vtnerd\></strong> \*export I think is what normal people say  
<strong>\<Jaquee\></strong> yeah. i'm almost done with that  
<strong>\<Jaquee\></strong> i'm trying to make wallet2 fully compatible so i can switch between light wallet and using a normal node  
<strong>\<vtnerd\></strong> well I meant but the export from the backend side, but ok interesting that you've already started the wallet side  
<strong>\<vtnerd\></strong> yup, understood  
<strong>\<zueore\></strong> how monero is configured to only cpu/gpu mining?  
<strong>\<Jaquee\></strong> so, to summarize. if i create the mymonero wallet first i can already switch between full and light wallet mode. This import call i'm suggesting also makes it possible to switch from an old full wallet never initialized on mymonero.  
<strong>\<vtnerd\></strong> ok
