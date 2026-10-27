---
title: Overview and Logs for the Dev Meeting Held on 2017-07-23
summary: Discussion of open PRs and issues, 0MQ, MyMonero/OpenMonero daemon integration, Surae's research, multisig, and miscellaneous
tags: [dev diaries, core, crypto]
author: dEBRUYNE / fluffypony
---

# Overview

There is no overview for this week.

# Logs

<strong>\<serhack\></strong> Oh  
<strong>\<serhack\></strong> Where is meeting? Here?  
<strong>\<pigeons1\[m\]\></strong> Should be yea  
<strong>\<Jaquee\></strong> anyone else noticed a memory leak in monerod from master?  
<strong>\<balambala\></strong> Hello there  
<strong>\<moneromooo\></strong> erikd did.  
<strong>\<serhack\></strong> Jaquee: oh, is memory leak dangerous?  
<strong>\<moneromooo\></strong> If you have hints, they’re welcome.  
<strong>\<rehrar\></strong> so…  
<strong>\<tewinget\></strong> talkaboutdangedol…yo, man  
<strong>\<Jaquee\></strong> no hints unfortunately. got an OOM crash after running for an hour or two. could’ve been something else  
<strong>\<Jaquee\></strong> i will find out soon enough  
<strong>\<rehrar\></strong> fluffypony ArticMine luigi1111 othe luigi1114 moneromooo hyc anonimal tewinget pigeons Jaquee  
<strong>\<Jaquee\></strong> did i hear meeting?  
<strong>\<Jaquee\></strong> o/  
<strong>\<ArticMine\></strong> Hi  
<strong>\<rbrunner\></strong> Grüezi mitenand  
<strong>\<rehrar\></strong> it seems fluffypony isn’t here to run the meeting, or he’s on his way. Anyone heard from him?  
<strong>\<tewinget\></strong> negative  
<strong>\<rehrar\></strong> well, I’m obviously not a dev, so I can’t help with the conversation, but the agenda is here: <https://github.com/monero-project/meta/issues/97> it’s pretty normal  
<strong>\<vtnerd\></strong> fluffypony is in las vegas according to his tweets  
<strong>\<rehrar\></strong> right, he’s at defcon  
<strong>\<rehrar\></strong> probably gambling  
<strong>\<vtnerd\></strong> or no wait, was a few days ago have kept up with that  
<strong>\<rehrar\></strong> I’m obviously not qualified to facilitate the things in this meeting, but I can just put each item to discuss, unless someone wants to volunteer  
<strong>\* pero</strong> volunteers moneromooo  
<strong>\<rehrar\></strong> do it\!  
<strong>\<tewinget\></strong> I would, but I’ve tried and I’m shite at it \>\_\>  
<strong>\<tewinget\></strong> pero: didn’t you say you wouldn’t be present for the meeting?  
<strong>\<vtnerd\></strong> moneromooo is usually the backup bot  
<strong>\<pero\></strong> yea but my plans changed  
<strong>\<moneromooo\></strong> So… ladies and gentlemen… let’s start with…  
<strong>\<moneromooo\></strong> tewinget  
<strong>\<moneromooo\></strong> :)  
<strong>\<tewinget\></strong> lol, ok  
<strong>\<moneromooo\></strong> 0MQ’s kinda ready now, right ?  
<strong>\<tewinget\></strong> the daemon’s rpc server stuff should be ready to merge, yes  
<strong>\<serhack\></strong> Hello  
<strong>\<pero\></strong> what’s still outstanding if that’s ready?  
<strong>\<tewinget\></strong> it’s not perfect, but “the great is the enemy of the good” and I’ve structured it such that it doesn’t affect anything if something’s wonky unless it’s crashy…which I haven’t seen any evidence of  
<strong>\<serhack\></strong> Point 1? Greetings?  
<strong>\<moneromooo\></strong> That’s good. Can you put a “how to start monerod with 0MQ RPC” in the PR ?  
<strong>\<unknownids\></strong> lol serhack  
<strong>\<tewinget\></strong> I still need to do testing on the wallet modifications and the rpc client interface.  
<strong>\<tewinget\></strong> moneromooo: if it builds, it runs the server :)  
<strong>\<tewinget\></strong> the cli flags are self-explanatory  
<strong>\<moneromooo\></strong> Ah, then “how to start monerod with original RPC” :)  
<strong>\<tewinget\></strong> also the same  
<strong>\<tewinget\></strong> hence it’s fine to merge  
<strong>\<moneromooo\></strong> It runs both at once ?  
<strong>\<tewinget\></strong> yes.  
<strong>\<moneromooo\></strong> Cool. OK.  
<strong>\<tewinget\></strong> this is to avoid really really messy backwards compatibility  
<strong>\<tewinget\></strong> later there may be a translation process that can receive old rpc requests and translate/forward them, but for now I think this is good.  
<strong>\<moneromooo\></strong> And the missing bits and bobs are fixed (for example, random stuff in getinto) ?  
<strong>\<tewinget\></strong> yeah, there’s one thing I needed to get clarity on, but it’s not a big deal  
<strong>\<moneromooo\></strong> Shoot.  
<strong>\<tewinget\></strong> that’s the get peers bit, as you seemed to imply that this should be changed, but afaict I’ve mirrored the old/existing RPC in this and it hasn’t changed. I mean, I haven’t implemented the call anyway, but the struct for the RPC message is what I’m talking about.  
<strong>\<tewinget\></strong> may as well have that be what it should in case some intrepid young lad gets bored and wants to add that call.  
<strong>\<tewinget\></strong> I’ve focused on the calls that the wallet uses for now, hence that one’s been left for later.  
<strong>\<moneromooo\></strong> Ah, peers used to be uint32\_t (IP) and uint16\_t (port) but they’re not something (host) and uint16\_t (port).  
<strong>\<moneromooo\></strong> OK, sounds good. The missing calls can be added later, that’s fine.  
<strong>\<pero\></strong> so wallet mods/client interface are largely done too?  
<strong>\<tewinget\></strong> right, but if you look at the GET\_PEERS call in the old RPC it’s still using uint32\_t IP and uint16\_t port, unchanged.  
<strong>\<tewinget\></strong> pero: yeah, it’s “done” but I found an issue with synching a testnet wallet around block 900k or so, so there’s a bit of debugging to do  
<strong>\<tewinget\></strong> but the code is in place, just needs testing.  
<strong>\<tewinget\></strong> \#2044 doesn’t need <em>as</em> much testing before merge (just make sure it doesn’t crash the daemon) because it only adds optional functionality, it doesn’t change any existing functionality  
<strong>\<tewinget\></strong> but \#2185 needs more testing because I completely refactored how the wallet uses the RPC  
<strong>\<moneromooo\></strong> OK, I will check the old GET\_PEERS.  
<strong>\<tewinget\></strong> that’s why I structured the PRs the way I did :)  
<strong>\<Jaquee\></strong> there’s some fuckery going on around 900k on testnet  
<strong>\<Jaquee\></strong> lots of reorgs  
<strong>\<tewinget\></strong> Jaquee: yeah, I noticed that, and one of the chunks of blocks during sync seemed to break things. It’ll take me a good bit of time to track it down because it’s such a weird bug.  
<strong>\<tewinget\></strong> what I really need to do is figure out how to configure gdb to actually print things…I hate it when shit’s inlined so gdb can’t print it. or optimized out (I need to verify that debug builds are -O0)  
<strong>\<pero\></strong> would zmq even be responsible for a sync-related bug?  
<strong>\<tewinget\></strong> pero: no, the wallet on that branch bugs out in synching using the old RPC  
<strong>\<tewinget\></strong> it’s something related to my refactor of how it uses the rpc.  
<strong>\<pero\></strong> gotcha  
<strong>\<sgp\></strong> Any other questions or should we move on?  
<strong>\<tewinget\></strong> oh  
<strong>\<pero\></strong> yes i’d like to know what the next steps are here  
<strong>\<tewinget\></strong> right  
<strong>\<pero\></strong> i was alarmed to see that 10 days passed without zmq-related github activity  
<strong>\<tewinget\></strong> so I think merging \#2184 and then \#2044 now would be good.  
<strong>\<tewinget\></strong> \#2185 will follow as soon as it’s tested and working. all the code is “done” just gotta test it.  
<strong>\<moneromooo\></strong> Anyone wants to ask anything else about 0MQ ?  
<strong>\<moneromooo\></strong> Next: Jaquee ?  
<strong>\<tewinget\></strong> if anyone has questions in the future, just ask whenever  
<strong>\<Jaquee\></strong> what?  
<strong>\<tewinget\></strong> well, after the dev meeting. carry on :)  
<strong>\<moneromooo\></strong> Anything about the GUI or light wallet you want to talk about ?  
<strong>\<Jaquee\></strong> ah =)  
<strong>\<pero\></strong> does zmq have impact to the gui?  
<strong>\<tewinget\></strong> pero: the refactor of how the wallet uses the rpc does  
<strong>\<Jaquee\></strong> well. i’ve been working on openmonero support the last days. making the wallet compatible with both mymonero and openmonero  
<strong>\<Jaquee\></strong> there are a lot of new commits in the lightwallet PR  
<strong>\<pero\></strong> thats outside of your scope too, i believe, tewinget  
<strong>\<Jaquee\></strong> haven’t squashed them yet  
<strong>\<moneromooo\></strong> Yeah, all this reviewing is starting to kill me, there’s a lot of stuff :D  
<strong>\<Jaquee\></strong> understandable  
<strong>\<moneromooo\></strong> Good stuff though.  
<strong>\<moneromooo\></strong> Especially that lovely subaddress stuff…  
<strong>\<pero\></strong> there will be a new gui release for september hardfork, Jaquee ?  
<strong>\<Jaquee\></strong> the cli and gui releases are supposed to be aligned, so yes.  
<strong>\<tewinget\></strong> remind me after the meeting, there’s one other thing that we’ll need to think about before merging \#2044 but we can talk about it later.  
<strong>\<pero\></strong> i am wondering if zmq making it into the cli codebase has been identified as work effort for the gui  
<strong>\<pero\></strong> potential work effort\*  
<strong>\<endogenic\></strong> Hey guys, fluffy got caught by timezone difference. Think he may be slammed at the moment but he may pop in to say what’s up. Just fyi  
<strong>\<pero\></strong> and if some attention needs to be paid into that as the clock is ticking down  
<strong>\<endogenic\></strong> Did not mean to interrupt you  
<strong>\<endogenic\></strong> Pero  
<strong>\* tewinget</strong> gives fluffypony some hair of the dog  
<strong>\<pero\></strong> s’ok :)  
<strong>\<Jaquee\></strong> i haven’t really looked at tewingets new stuff, but afaik it shouldnt affect the gui that much.  
<strong>\<serhack\></strong> Hey, I’m developing prestashop plugins  
<strong>\<Jaquee\></strong> there are some rpc stuff in wallet api, but most of it arent used  
<strong>\<pero\></strong> ok cool just putting it out there  
<strong>\<serhack\></strong> I dont know if after that I will write another ffs  
<strong>\<tewinget\></strong> I’ve refactored those bits as well :)  
<strong>\<Jaquee\></strong> great =)  
<strong>\<moneromooo\></strong> anything else, Jaquee ?  
<strong>\<Jaquee\></strong> yes. but i guess i need fluffy to answer it  
<strong>\<Jaquee\></strong> i was thinking about mobile release and testing  
<strong>\<moneromooo\></strong> OK, we’ll be back to you when/if he’s around then ?  
<strong>\<Jaquee\></strong> if someone is working on apple store and play store stuff  
<strong>\<Jaquee\></strong> yes. i’ll ping him  
<strong>\<moneromooo\></strong> OK. Thanks.  
<strong>\<Jaquee\></strong> ok. that’s all  
<strong>\<moneromooo\></strong> serhack: so, tell us more about what you’re doing and what’s your progress :)  
<strong>\<Jaquee\></strong> oh. one more thing. sorry  
<strong>\<moneromooo\></strong> Sure  
<strong>\<moneromooo\></strong> one minute serhack please :)  
<strong>\<Jaquee\></strong> vtnerd: what’s the status on the openmonero/mymonero integration?  
<strong>\<Jaquee\></strong> in monerod  
<strong>\<Jaquee\></strong> do we have a plan for that?  
<strong>\<vtnerd\></strong> not yet really  
<strong>\<Jaquee\></strong> ok  
<strong>\<vtnerd\></strong> other than I would like to have multiple processes for this for security purposes  
<strong>\<vtnerd\></strong> which is what the backend is doing, but I need to make IPC between them easy  
<strong>\<Jaquee\></strong> sounds like a good idea  
<strong>\<Jaquee\></strong> iirc fluffy said in then january meetup that the backend was going to be open sourced. Any timeline for that?  
<strong>\<vtnerd\></strong> not at all, that has not been my direct focus  
<strong>\<vtnerd\></strong> I suppose whenever the backend is in better shape :/  
<strong>\<Jaquee\></strong> all right. thanks =)  
<strong>\<Jaquee\></strong> moneromooo: done  
<strong>\<vtnerd\></strong> more recently I’ve been working on the serialization explosions  
<strong>\<Jaquee\></strong> sounds fun  
<strong>\<Jaquee\></strong> :P  
<strong>\<vtnerd\></strong> so I’ll have to make a push to start encoding a version in the archive header so we dont have this issue again  
<strong>\<moneromooo\></strong> Would be nice to get them fixed, or at least ensure they’re not exploitable, since cold wallet comms use that.  
<strong>\<vtnerd\></strong> and try to convince the serialization author to merge something before the 1.65 release  
<strong>\<vtnerd\></strong> eh, thats the issue I would to see corrected with serialization. I dont see another way to handle it  
<strong>\<vtnerd\></strong> basically with better versioning in the header we get less bug defects, but crafting a file is problematic without changes within boost  
<strong>\<Jaquee\></strong> i’ve missed this. what’s the issue?  
<strong>\<moneromooo\></strong> Crafting would likely not be defeated by versioning though.  
<strong>\<moneromooo\></strong> Jaquee: a crash in boost loading a serialized file.  
<strong>\<vtnerd\></strong> <https://svn.boost.org/trac10/ticket/9370>  
<strong>\<Jaquee\></strong> ah. thanks  
<strong>\<vtnerd\></strong> our situation is very similar, except its boost::multi\_index is doing it internally. a change by moo on 5/27 changed the serialization type  
<strong>\<vtnerd\></strong> moneromooo : that sentence was worded similar. if you meant that its still possible to craft a file if we reject \_newer\_ versions, then I agree  
<strong>\<vtnerd\></strong> \*worded strangely  
<strong>\<moneromooo\></strong> I just meant a crafted file would claim whatever version leads to the exploit, which is likely whjayt you also meant.  
<strong>\<vtnerd\></strong> right you can pretty much do whatever if you can modify the file being read  
<strong>\<moneromooo\></strong> OK, we’re done on this ?  
<strong>\<Jaquee\></strong> yes  
<strong>\<moneromooo\></strong> serhack: go ahead then, tell is about your plugins work :)  
<strong>\<vtnerd\></strong> as far as mymonero goes, the focus is not yet open sourcing but since its on my mind during the refactor it shouldnt be hell  
<strong>\<vtnerd\></strong> hopefully  
<strong>\<endogenic\></strong> Vtnerd… a silent hero of monero…  
<strong>\<moneromooo\></strong> Hmm, he seemed keen, but also seems not around now.  
<strong>\<moneromooo\></strong> endogenic: do you have something you want to talk about ?  
<strong>\<endogenic\></strong> Nah not as yet. Soon(tm)  
<strong>\<moneromooo\></strong> Alright, thank you.  
<strong>\<sgp\></strong> @serhack can always talk about it later, but I know he may want to discuss a way of covering plugin maintenance costs  
<strong>\<endogenic\></strong> Really pleased about the lightwallet support  
<strong>\<moneromooo\></strong> So, mooo now:  
<strong>\<Jaquee\></strong> endogenic: is the mymonero backend issues holding back the mobile/desktop releases currently  
<strong>\<Jaquee\></strong> that can wait. go moo  
<strong>\<endogenic\></strong> Nah it’s not  
<strong>\<Jaquee\></strong> k  
<strong>\<moneromooo\></strong> I worked on faster/leaner node sync (sync branch) as well as multisig (multisig2 branch right now)  
<strong>\<moneromooo\></strong> Both welcome testing :)  
<strong>\<moneromooo\></strong> multisig2 has RPC, but that’s not been tested much yet, so don’t really expect it to work. Wallet commands are what’s ready.  
<strong>\<moneromooo\></strong> Next… who could have somehting to say…  
<strong>\<moneromooo\></strong> Anyone ?  
<strong>\<rbrunner\></strong> I have something  
<strong>\<rbrunner\></strong> Is something planned already about putting the Windows installer for the GUI wallet into service i.e. at the end offering the Setup.exe as a download on getmonero.org?  
<strong>\<moneromooo\></strong> knaccc: kenshi84 ?  
<strong>\<Jaquee\></strong> rbrunner: yes, most likely in next release  
<strong>\<rbrunner\></strong> September then, right?  
<strong>\<Jaquee\></strong> which will happen somewhere between now and hardfork  
<strong>\<Jaquee\></strong> yes, around sept  
<strong>\<rbrunner\></strong> Ok. I hold my breath :)  
<strong>\<Jaquee\></strong> :D  
<strong>\<pero\></strong> does the mooning network hash warrant any discussion  
<strong>\<moneromooo\></strong> If you have something to say about it… sure.  
<strong>\<pero\></strong> eh  
<strong>\<pero\></strong> was hoping someone else might have some insight  
<strong>\<pero\></strong> :)  
<strong>\<Jaquee\></strong> i’ve noticed the block time has been pretty inconsistent lately  
<strong>\<Jaquee\></strong> was thinking it was because the variance in hash  
<strong>\<Jaquee\></strong> lot’s of 5-10 mins gaps  
<strong>\<pero\></strong> it seems to me that botnets could very well be pricing out ‘regular’ miners  
<strong>\<moneromooo\></strong> As long as it’s several distinct ones…  
<strong>\<pero\></strong> right  
<strong>\<pero\></strong> can we tell how centralized the mining is? real centralization could be obfuscated by pools  
<strong>\<sgp\></strong> @pero ideally the discovered botnets can have the addresses searched in the pools to determine the hashrate  
<strong>\<moneromooo\></strong> Pools might be able to tell, since they know source IPs (unless proxied). You’d have to trust the pools to tell you the truth though :)  
<strong>\<pero\></strong> yea…food for thought i guess…  
<strong>\<tewinget\></strong> dammit, now I have thought for food…  
<strong>\<moneromooo\></strong> Though if hash is from a botnet, IPs don’t really give you much.  
<strong>\<sgp\></strong> One question: the release is in September. What window do you want to give everyone to upgrade?  
<strong>\<moneromooo\></strong> I’d been wondering whether some non-profit oriented large miner might want to crowd out miners.  
<strong>\<sgp\></strong> \*hardfork  
<strong>\<moneromooo\></strong> Undecided yet. But hopefully more than a week :/  
<strong>\<knaccc\></strong> not sure if this is the right time to suggest it, but in preparation for subaddresses, the GUI and CLI should probably recognize the subaddress and integrated subaddress prefixes and display a message that subaddresses are not supported yet, and that they need to upgrade to send to such addresses  
<strong>\<moneromooo\></strong> There’s not much that needs to go in next fork, so that should not be much trouble.  
<strong>\<sgp\></strong> Did we ever agree on the new minimum ringsize?  
<strong>\<moneromooo\></strong> That’s not a bad idea at all.  
<strong>\<moneromooo\></strong> No.  
<strong>\<moneromooo\></strong> kenshi84: do you want to make a preliminary patch for this ? It’d include your existing parsing changes, plus error messages on use.  
<strong>\<moneromooo\></strong> I don’t think kenshi84’s around now.  
<strong>\<moneromooo\></strong> suraeNoether: what about you ? Tell us about your research.  
<strong>\<suraeNoether\></strong> ah, well, good timing actually  
<strong>\<sgp\></strong> How should we actually reach consensus on the new minimum number? Running out of time to decide.  
<strong>\<sgp\></strong> @surae I don’t mean to interrupt you though, carry on :)  
<strong>\<suraeNoether\></strong> np, as far as minimum ring size goes, and mitigating EABE… a lot of this would be solved with efficient ring signatures and range proofs.  
<strong>\<suraeNoether\></strong> today, I’m coding up some examples of O(sqrt(n)) ring sigs and some efficient range proof algorithms to compare sizes with current set-ups  
<strong>\<suraeNoether\></strong> the idea is, if we can manage to fit a ring size of, say, 150, in with each transaction, I don’t care how much computing power you have, you’re going to be spending a lot of time analyzing monero’s blockchain  
<strong>\<sgp\></strong> 150? Wow  
<strong>\<moneromooo\></strong> Kovri meeting starting in \#kovri-dev for those who want to follow both.  
<strong>\<suraeNoether\></strong> i would prefer orders of magnitude  
<strong>\<suraeNoether\></strong> i would <em>prefer</em> a quarter million or more signatories per transaction  
<strong>\<ArticMine\></strong> any idea on the trade off ring size, range proof efficiency vs tx size?  
<strong>\<moneromooo\></strong> All depends on the constants, doesn’t it :)  
<strong>\<knaccc\></strong> \\o/  
<strong>\<suraeNoether\></strong> that’s what i’m looking into today, arcticmine and moneromooo, there’s a cost to everything  
<strong>\<vtnerd\></strong> lol @ that compute time  
<strong>\<pigeons1\[m\]\></strong> Similarly I’m interested in exploring potential privacy drawbacks of not having a fixed uniform ring size  
<strong>\<suraeNoether\></strong> so, I have some attack models for EABE. First order estimates suggest a min ring size of like 30 is necessary with 7 churns. Second order estimates suggest as low as 15 is good with a single churn. my third order estimate looks to be somewhere between those two? possibly with more in the ring size.  
<strong>\<suraeNoether\></strong> pigeons1\[m\] this is absolutely something i’m also looking into  
<strong>\<suraeNoether\></strong> i like the idea of a uniform ring size if the ring size is very large, say more than 10^2  
<strong>\<suraeNoether\></strong> in a world where choices are allowable, a random (with minimum) ring size is preferable to any other given strategy  
<strong>\<Jaquee\></strong> disrupting with a question: how do i run monerod with valgrind? i’m getting an “invalid argument” error on startup.  
<strong>\<sgp\></strong> @surae do you think a ringsize of 10 is far too low? I didn’t expect to consider a jump from 5 to 150/100  
<strong>\<Jaquee\></strong> src/blockchain\_db/lmdb/db\_lmdb.cpp:71 Failed to open lmdb environment: Invalid argument  
<strong>\<Jaquee\></strong> trying: valgrind /path/to/monerod  
<strong>\<Jaquee\></strong> no args. blockchain in default location  
<strong>\<moneromooo\></strong> Should work that way.  
<strong>\<Jaquee\></strong> that’s what i thought too  
<strong>\<JollyMort\[m\]\></strong> in lieu of more research, enforcing some min. in the upcoming HF would be beneficial, no? 5 or 10?  
<strong>\<Jaquee\></strong> moneromooo: <https://paste.fedoraproject.org/paste/liZxIo25sun2z8d9YTDLbw/raw>  
<strong>\<suraeNoether\></strong> sgp : in terms of security alone, min ring size 10 would be “safe” for a year or two. but would have \*how much\* cost on the blockchain, and how much cost in terms of adoption? in lieu of more research, a larger ringsize is only preferably in terms of security, not necessarily in terms of adoptions  
<strong>\<pero\></strong> we already enforce a minimum i believe  
<strong>\<suraeNoether\></strong> yep, 2  
<strong>\<JollyMort\[m\]\></strong> 3, no? “mixin of 2” iirc  
<strong>\<suraeNoether\></strong> oh ringsize 3, mixin 2  
<strong>\<suraeNoether\></strong> sorry, terminology  
<strong>\<sgp\></strong> @surae do you have any major current concerns with 10? Do you think it is reasonable for now pending research?  
<strong>\<suraeNoether\></strong> my concerns come from the cost to the size of the blockchain  
<strong>\<suraeNoether\></strong> and hence adoptoin  
<strong>\<suraeNoether\></strong> adoption\*  
<strong>\<sgp\></strong> afaik the difference between 10 and 5 is very small  
<strong>\<suraeNoether\></strong> i advocated large ring sizes years ago, but there is a cost to the blockchain, a huge cost  
<strong>\<suraeNoether\></strong> we aren’t discussing 10 vs. 5 we are discussing 10 vs. 2  
<strong>\<pigeons1\[m\]\></strong> Better to wait for research instead of arbitrary change  
<strong>\<suraeNoether\></strong> er. 3 i suppose  
<strong>\<sgp\></strong> Ok, still between 10 and 3 is small  
<strong>\<JollyMort\[m\]\></strong> when the whole discussion started the first idea was to increase to 5 iirc  
<strong>\<JollyMort\[m\]\></strong> so might as well make it 5 vs 3 :)  
<strong>\<suraeNoether\></strong> i think the security gain from 3 to 5 is not huge. the security gain from 3 to 10 is much more measurable  
<strong>\<endogenic\></strong> I’m with pigeons in that one  
<strong>\<endogenic\></strong> On  
<strong>\<moneromooo\></strong> You’re on pigeons in that one ?  
<strong>\<endogenic\></strong> Yeah  
<strong>\<pigeons1\[m\]\></strong> Oh baby  
<strong>\<endogenic\></strong> I’m one with pigeons on that too  
<strong>\<endogenic\></strong> Two\*  
<strong>\<unknownids\></strong> ( ͡° ͜ʖ ͡°)  
<strong>\<pero\></strong> will there be a security hit if we enforce 10 for a while and then switch to random?  
<strong>\<pero\></strong> random as in potentially \<10  
<strong>\<suraeNoether\></strong> i’m in agreement with pigeons1\[m\] and endogenic … especially if these O(sqrt(n)) signatures end up being nice. because knaccc was talking about n=30 ringsize being relatively reasonable in terms of cost to the blockchain today, and i know the max ringsize demonstrated so far is around 10^3. for the same cost, we could get 900 to 10^6 signatories per ring signature if O(sqrt(n)) hits the shelves, and i’ll  
<strong>\<suraeNoether\></strong> tell you what: in that scenario, i’d absolutely advocate a minimum 150, and let users decide above and beyond that  
<strong>\<endogenic\></strong> There may be a public education issue with switching all around w/o research too  
<strong>\<suraeNoether\></strong> pero when i say random i mean “random above a certain minimum”  
<strong>\<pero\></strong> gotcha  
<strong>\<knaccc\></strong> yeah if a ring size 400 transaction is the same size as a ring size 20 transaction, that’d be incredible  
<strong>\<suraeNoether\></strong> right now, the best hope for anonymity is simply more efficient ring sigs, and this set-up is extremely extremely promising  
<strong>\<endogenic\></strong> Not that you didnt research it jolly  
<strong>\<suraeNoether\></strong> actually we’ve researched the crap out of htis  
<strong>\<endogenic\></strong> Btw jolly i guess that means i have to bump “ringsize” on the mm tx details page by 1 :p  
<strong>\<suraeNoether\></strong> we just haven’t come up with a formal model of security yet that provides a tractable answer “go with 17, child”  
<strong>\<endogenic\></strong> Need more tea leaves  
<strong>\<gingeropolous\></strong> well in september we’ll at least get ringsize = 5  
<strong>\<moneromooo\></strong> Make sure to list any extra crypto assumptions over what monero already assumes.  
<strong>\<sgp\></strong> Right now I’m most concerned what we will do for September  
<strong>\<suraeNoether\></strong> i’m not totally concerned. i’m… really… really excited about small ring sizes  
<strong>\<suraeNoether\></strong> okay, i’ll be back later, i’m really glad i could hop in with such good timing on this  
<strong>\<moneromooo\></strong> thanks suraeNoether  
<strong>\<moneromooo\></strong> anyone else ?  
<strong>\<gingeropolous\></strong> oh is it meeting time?  
<strong>\<moneromooo\></strong> kovri’s  
<strong>\<ArticMine\></strong> So next meeting in two weeks?  
<strong>\<serhack\></strong> Moneromoo  
<strong>\<serhack\></strong> Sorry  
<strong>\<serhack\></strong> I was eating  
<strong>\<serhack\></strong> Okay  
<strong>\<serhack\></strong> Then  
<strong>\<moneromooo\></strong> np, go ahead :)  
<strong>\<serhack\></strong> My progress are: wordpress plugin is almost completed, I’m developing the verifying (if transaction is okay), I’m also starting the development of Prestashop plugins  
<strong>\<serhack\></strong> After that, I will write another FFS (I will request like 40 xmr or less)  
<strong>\<serhack\></strong> I would create some stickers based on <https://m.imgur.com/QcdyyWn>  
<strong>\<serhack\></strong> I will publish plugins on codecanyon.com, every funds will be helpful for Monero Project  
<strong>\<serhack\></strong> What do you think moneromoo?  
<strong>\<moneromooo\></strong> Cool, thanks for the overview  
<strong>\<pero\></strong> dEBRUYNE: was it codecanyon.com you blacklisted from the subreddit? ;p  
<strong>\<dEBRUYNE\></strong> .net I think, but that probably doesn’t matter haha  
<strong>\<serhack\></strong> Your welcome, moneromoo  
<strong>\<dEBRUYNE\></strong> I can unblacklist it  
<strong>\<serhack\></strong> Everyone should know Monero Community  
<strong>\<serhack\></strong> Fantastic community\!  
<strong>\<gingeropolous\></strong> opinions? If I could even figure out how to code into monero a “remote node” support flag, would it be merged? it would be a daemon load flag that would do the appropriate rpc stuff and also modify some p2p metadata to essentially broadcast its openness  
<strong>\<serhack\></strong> Cheers\!  
<strong>\<serhack\></strong> Please pm me for more information on slack or mail me <support@monerointegrations.com>  
<strong>\<Jaquee\></strong> so, “valgrind /path/to/monerod” works for everyone else except me?  
<strong>\<moneromooo\></strong> Worked for me last time I tried. Try running with strace too, see what syscall barfs.  
<strong>\* iDunk</strong> can’t run valgrind because of TBM in his CPU.  
<strong>\<moneromooo\></strong> Too Big Munchkins ?  
<strong>\<iDunk\></strong> Trailing Bit Manipulation, IIRC :)  
<strong>\<iDunk\></strong> One of AMD’s FMA additions, I think.  
<strong>\<pero\></strong> so…follow up q…will there be a period of time during which gui master will be broken because of zmq  
<strong>\<endogenic\></strong> iDunk: is that similar to a FML addition?  
<strong>\<pero\></strong> tewinget Jaquee ^  
<strong>\<tewinget\></strong> pero: there shouldn’t be.  
<strong>\<moneromooo\></strong> tewinget says the daemon runs both 0MQ and JSON/HTTP server, so shouldn’t be.  
<strong>\<pero\></strong> thx  
<strong>\<tewinget\></strong> won’t merge the zmq rpc wallet stuff until it’s tested working, and at that point the gui wallet will be unaffected  
<strong>\<Jaquee\></strong> speaking of testing. is someone working on fixing the failed tests on buildbot builds?  
<strong>\<Jaquee\></strong> pigeons1\[m\]: ^  
<strong>\<Jaquee\></strong> and if you’re around pigeons1\[m\]. How’s the tagging bot coming along?  
<strong>\<pigeons1\[m\]\></strong> Bot is working in meta repo. I’ll talk with fluffy and we’ll add it to gui repo.  
<strong>\<moneromooo\></strong> What failing tests ? The DNS ones ?  
<strong>\<moneromooo\></strong> pigeons1\[m\]: does it do closes yet ? :)  
<strong>\<pigeons1\[m\]\></strong> I was tracking down lots of my own bugs so switched to an opensource bot i linked to in the meta issue. Seems to work well  
<strong>\<pigeons1\[m\]\></strong> Yes +resolved on a line by itself by someone authorized closes the issue  
<strong>\<moneromooo\></strong> Great, thanks :)  
<strong>\<pigeons1\[m\]\></strong> And moo yes i think he means the dns ones  
<strong>\<moneromooo\></strong> I’ve looked at the DNS stuff today, but I’m still flummoxed.  
<strong>\<moneromooo\></strong> Redoing manually what libunbound is supposed to do seems… not right :/  
<strong>\<moneromooo\></strong> Not to mention a huge amount of work.  
<strong>\<moneromooo\></strong> And if libunbound’s not doing it right, surely it’d be best to fix it, not do it manually.  
<strong>\<moneromooo\></strong> I feel like I’m missing something here :/  
<strong>\<moneromooo\></strong> We don’t have a coder who knows about DNS already, do we ? :)  
<strong>\<tewinget\></strong> I don’t know your exact headache, but I remember when I first implemented that shit using libunbound. Just about the only lib I could find that would serve our purposes, but…not without pain.  
<strong>\<moneromooo\></strong> Mine is to first find the algorithm to verify a chain. Just that seems to be a lot of cases.  
<strong>\<pigeons1\[m\]\></strong> Dnssec validation locally instead of trusting the server response is part of the pain i think tewinget  
<strong>\<moneromooo\></strong> But libnubound claims to do validation.  
<strong>\<tewinget\></strong> pigeons1\[m\]: yeah…I seem to remember that being one of the pain points.  
<strong>\<moneromooo\></strong> (and it fails to do so if I give it a bad key, which seems to confirm)  
<strong>\<pigeons1\[m\]\></strong> Yeah we’re missing something…  
<strong>\<tewinget\></strong> well I gotta afk for a bit. The last step before merging \#2044 is to make sure it builds properly on all the things where it needs to, including deciding how to deal with the zmq dependency itself. I hesitate to make a decision there, as I’m ambivalent.  
<strong>\<moneromooo\></strong> Probably a submodule.
