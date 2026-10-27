---
title: Overview and Logs for the Dev Meeting Held on 2016-10-30
summary: Fluffy blocks, crypto libs
tags: [dev diaries, core, crypto, 0mq]
author: dEBRUYNE / fluffypony
---

### Overview

An overview [can be found on Hello Monero](https://hellomonero.com/article/monerokovri-dev-meeting-note-highlights-2016-10-30).

### Logs

<strong>\<Jaquee\></strong> it takes quite long time to open/close wallets with this mempool size. Could the mempool be saved in wallet cache?  
<strong>\<Jaquee\></strong> or is that a bad idea?  
<strong>\<Jaquee\></strong> doesnt really affect closing wallets. my bad. but opening takes longer than normal i think?  
<strong>\<realsony\></strong> test  
<strong>\<moneromooo\></strong> You can test that easily by logging something before and after loading.  
<strong>\<moneromooo\></strong> It's in src/cryptonote\*core/tx\_pool.cpp  
<strong>\<hyc\></strong> is it mtg time yet?  
<strong>\<moneromooo\></strong> Yes  
<strong>\<pero\></strong> romero dev conference  
<strong>\<Jaquee\></strong> all right. the gui def takes longer time top open because of mempool. And it also waits for mempool to be synced before closing.  
<strong>\<hyc\></strong> why is that different from CLI behavior?  
<strong>\<Jaquee\></strong> not sure yet  
<strong>\<Jaquee\></strong> opening seems the same  
<strong>\<pero\></strong> mooo you're a whitespace nazi  
<strong>\<Slack\> \<nanoakron\></strong> Is there a way that git PRs could be run through a common parser on the server-side to standardise any whitespace?  
<strong>\<moneromooo\></strong> Not really, since it'll invariably try to reformat irrelevant stuff.  
<strong>\<moneromooo\></strong> That said, if it could run on the diffs, it might work.  
<strong>\<Slack\> \<nanoakron\></strong> And WRT mempool size - would fluffy blocks as standard across the network (e.g. if included in HF4) make things better?  
<strong>\<revler1082\></strong> i don't think so, it just helps with not sending txs again when a block is found, the mempool size is unaffected  
<strong>\<moneromooo\></strong> So... if the pony isn't here... anyone wants to say something dev related ?  
<strong>\<Slack\> \<nanoakron\></strong> OK yes I see. But it should allow us to avoid some of the issues that bitcoin is having - if all mempools are synched and a miner wants to eat all the transactions into a single megablock, it would propagate much more quickly than without  
<strong>\<Slack\> \<nanoakron\></strong> I’m a tinkerer rather than a dev :slightly\_smiling\_face:  
<strong>\<revler1082\></strong> yea so the bigger the blocks (assuming mempools are aligned), the greater the savings  
<strong>\<Slack\> \<nanoakron\></strong> Which would be an extra cool reason for making fluffy blocks compulsory in a hard fork  
<strong>\<revler1082\></strong> hmm, I saw monero-moo's latest comments on the fluffy-block stuff, so I was going to go through those, but I don't have much else.  
<strong>\<revler1082\></strong> if you guys would like me to change anything, etc, feel free to ask/comment  
<strong>\<Slack\> \<nanoakron\></strong> My only ‘dev issue’ is with the growing number of dead issues on github  
<strong>\<Slack\> \<nanoakron\></strong> We should probably only be at 60 or so live issues  
<strong>\<moneromooo\></strong> I think at this point, it's testing. Especially that one about the array of txes noit in the pool but not requested again.  
<strong>\<realsony\></strong> may i as what a dead issue is?  
<strong>\<realsony\></strong> ask  
<strong>\<Slack\> \<nanoakron\></strong> One that’s been solved  
<strong>\<realsony\></strong> ty  
<strong>\<dEBRUYNE\></strong> monero-core has a lot of those too fwiw  
<strong>\<dEBRUYNE\></strong> I can give you a list for monero-core fluffypony  
<strong>\<hyc\></strong> typically I would not close an issue until the fix is in a tagged release  
<strong>\<hyc\></strong> (at least, on other projects.)  
<strong>\<pero\></strong> ^ +1  
<strong>\<Slack\> \<nanoakron\></strong> Or where the codebase has evolved onwards but the original person who has raised the issue has not tested to see if it’s still active  
<strong>\<pero\></strong> or at the very least merged  
<strong>\<Slack\> \<nanoakron\></strong> @hyc can I ask - completely separate issue, have you considered offering your skills to port Bitcoin Unlimited to LMDB? They’ve got $500k in the bank...  
<strong>\<hyc\></strong> I hadn't heard anything about that nanoakron  
<strong>\<Slack\> \<nanoakron\></strong> @hyc ask around - I’m sure their users would want to offer an even better reason to switch their node software away from core  
<strong>\<ArticMine\></strong> Bitcoin unlimited will be insecure once the emission runs out  
<strong>\<Slack\> \<nanoakron\></strong> And I think the entire ecosystem will benefit  
<strong>\<Slack\> \<nanoakron\></strong> As for dead issues - there are still ones hanging around from before 0.10.0 which either haven’t been updated by their issuers or have been addressed  
<strong>\<hyc\></strong> would definitely be a good idea to go thru and close any that havve been fixed  
<strong>\<revler1082\></strong> @moneromooo i had left a comment in the code about whether I was double verifying since all the transactions were already in the pool, anything on that?  
<strong>\<revler1082\></strong> could speed things up a bit  
<strong>\<moneromooo\></strong> I'll have a look soon. String to grep for ?  
<strong>\<revler1082\></strong> "Do I need to do this" lol  
<strong>\<moneromooo\></strong> ok  
<strong>\<Slack\> \<nanoakron\></strong> lol  
<strong>\<Slack\> \<malmen\></strong> How is 0qm work?  
<strong>\<moneromooo\></strong> proxmr: you'll know in \~30 min when anonimal's around for the kovri meeting.  
<strong>\<moneromooo\></strong> tewinget: around ?  
<strong>\<Slack\> \<nanoakron\></strong> So the big themes I see in current development are: ZMQ, GUI, final touches to RingCT (?), changing the crypto library, changing the logging system and fluffy blocks. Any others?  
<strong>\<Slack\> \<malmen\></strong> What is fluffy blocks? I am missing something here  
<strong>\<iDunk\></strong> dynamic fees  
<strong>\<revler1082\></strong> @mailmen just a compact block implementation for monero  
<strong>\<moneromooo\></strong> It's just sending txes from a block only if a peer doens't have them already.  
<strong>\<Slack\> \<malmen\></strong> Hmmmm, so, instead of sending all tx the block will contain only the reference of the tx that is in another block?  
<strong>\<Slack\> \<nanoakron\></strong> No, reference to the local mempool  
<strong>\<Slack\> \<malmen\></strong> Ahh  
<strong>\<revler1082\></strong> no, it just sends the tx hashes, and since most nodes have the transactions in the mempool, it just gets the full tx from there  
<strong>\<Slack\> \<nanoakron\></strong> And if it’s not in there then you receive the missing Tx  
<strong>\<revler1082\></strong> if it's missing any, it'll ask for those  
<strong>\<Slack\> \<malmen\></strong> Nice  
<strong>\<Slack\> \<nanoakron\></strong> Really nice :slightly\_smiling\_face:  
<strong>\<Slack\> \<malmen\></strong> It is implemented in any place already or we will be the first ones to have it?  
<strong>\<Slack\> \<nanoakron\></strong> Bitcoin has it  
<strong>\<revler1082\></strong> yep, multiple implementations, xthin/compact blocks  
<strong>\<Slack\> \<nanoakron\></strong> but because they’re a dirty mix of hard and soft forked rules, and have a stupid mempool policy preventing network-wide synchronisation, they won’t see as much benefit as we will  
<strong>\<revler1082\></strong> there's some way to save even more space based on some of the stuff you guys shared with me, where you send just some prefix of the tx\_hash since there's unlikely to be collisions, but I think sacrificing some space to keep things simple is ok  
<strong>\<Slack\> \<malmen\></strong> Hmmm, nice... And about the way the db save the blocks, I was thinking in the other day  
<strong>\<Slack\> \<nanoakron\></strong> @revler1082 you should contact the original devs of XThin and ask them about those issues :slightly\_smiling\_face:  
<strong>\<moneromooo\></strong> I don't know how the bitcoin ones work, but given what you wrote, I'd send the index of the tx you don't have. Possibly differential encoded.  
<strong>\<Slack\> \<nanoakron\></strong> @hyc is your db guy  
<strong>\<Slack\> \<malmen\></strong> Instead of the block on the the database save the full tx, can it be save the reference to other block with tx? It will use more disk io and cpu, but can save space  
<strong>\<revler1082\></strong> thanks @moneromooo that's a good one  
<strong>\<moneromooo\></strong> I'm guessing there might be a good reason why they don't do that though.  
<strong>\<Slack\> \<nanoakron\></strong> Well that’s an interesting point - if you’re pulling in other transactions to build your ring signature, do you do that from the mempool or from historic data stored in the local db? I’m not sure myself  
<strong>\<ArticMine\></strong> The idea if I understand this is to save bandwidth  
<strong>\<revler1082\></strong> @ArticMine correct  
<strong>\<revler1082\></strong> not much difference now, but when monero takes over the world, savings should increase  
<strong>\<ArticMine\></strong> You pull from the historic data not the mempool  
<strong>\<Slack\> \<nanoakron\></strong> So not many dev issues today which is good. Just really revler and moneromooo co-reviewing fluffy block code, and maybe closing old issues?  
<strong>\<moneromooo\></strong> We can't close old issues. We can just make lists and wait for fluffypony to have time :)  
<strong>\<Slack\> \<nanoakron\></strong> True  
<strong>\<revler1082\></strong> What's the crypto-lib replacement? I could maybe help with that, I mean my crypto skills are le garbage, but I can change function calls, lol  
<strong>\<Slack\> \<nanoakron\></strong> Would you think about the logging system in that case? The crypto currently works well enough  
<strong>\<moneromooo\></strong> The main problem is choosing the best one. And that needs people who know them. The pony does I think.  
<strong>\<revler1082\></strong> logging or crypto? or both?  
<strong>\<Slack\> \<nanoakron\></strong> Moneromooo, do you have any thoughts on where revler can best help after fluffy blocks are finished?  
<strong>\<moneromooo\></strong> We'll need some crypto lib with a good PRNG, to replace the keccak construction we use now.  
<strong>\<Slack\> \<nanoakron\></strong> <https://github.com/monero-project/monero/issues/1271>  
<strong>\<Slack\> \<nanoakron\></strong> That’s what we’re referencing here revler - already some good discussion to review there  
<strong>\<moneromooo\></strong> Wherever revler1082 is comfortable, really. If the previous bit changed was network stuff, then maybe more of it ?  
<strong>\<Slack\> \<nanoakron\></strong> What do you think the issues are with current network code?  
<strong>\<moneromooo\></strong> fluffypony wanted to switch the P2P protocol to... er... something... name escapes me.  
<strong>\<Slack\> \<nanoakron\></strong> ;)  
<strong>\<moneromooo\></strong> ZMTP.  
<strong>\<Slack\> \<nanoakron\></strong> ooh…sounds fancy. How about maybe helping with ZMQ??  
<strong>\<iDunk\></strong> jesus  
<strong>\<moneromooo\></strong> It's based on epee, from the CN people.  
<strong>\<Slack\> \<nanoakron\></strong> @iDunk you rang?  
<strong>\<revler1082\></strong> all sounds good, i'll look into it and help where I can  
<strong>\<moneromooo\></strong> The P2P code is really hard to understand, though that is subjective, mayube others like it more.  
<strong>\<iDunk\></strong> yeah, I'm on the verge of really saying something  
<strong>\<moneromooo\></strong> There are a few bugs, mainly that it leaks sockets.  
<strong>\<revler1082\></strong> if i ever get my spaces and tabs passed @moneromooo  
<strong>\<Slack\> \<nanoakron\></strong> hehe  
<strong>\<Slack\> \<nanoakron\></strong> What’s up iDunk?  
<strong>\<moneromooo\></strong> Well, it boils down to "don't change what you don't change".  
<strong>\<iDunk\></strong> nanoakron: take it easy, man  
<strong>\<moneromooo\></strong> But I agree I may be a bit too sold on clean diffs without extraneous stuff.  
<strong>\<moneromooo\></strong> Those things are easy to fix though.  
<strong>\<revler1082\></strong> lol, @moneromooo just messin, I want to kick myself when I push and see those in the diff, like mother ..  
<strong>\<Slack\> \<nanoakron\></strong> Revler wants to help with network related stuff and I’m just saying what’s in the codebase that is being worked on  
<strong>\<moneromooo\></strong> And maybe helping with 0MQ, I guess it'll need some testing and fixing once tewinget's done with it to a point where it can be merged.  
<strong>\<fluffypony\></strong> yes ZMTP  
<strong>\<moneromooo\></strong> pony\!  
<strong>\<Slack\> \<nanoakron\></strong> Woo\!  
<strong>\<fluffypony\></strong> apologies  
<strong>\<fluffypony\></strong> had the meeting down for 7pm not 6pm  
<strong>\<Slack\> \<nanoakron\></strong> Do you guys change your clocks today down there in SA?  
<strong>\<Slack\> \<nanoakron\></strong> Ours went back last night. It’s now dark at 5pm. Misery.  
<strong>\<fluffypony\></strong> no, we don't do DST  
<strong>\<fluffypony\></strong> OH that's why  
<strong>\<fluffypony\></strong> everything is confusing  
<strong>\<DaveyJones\></strong> thought sth like this :p  
<strong>\<fluffypony\></strong> re: closing issues  
<strong>\<fluffypony\></strong> I'm happy to close them from lists  
<strong>\<fluffypony\></strong> and I don't think we need to wait for them to be in a tagged release per se  
<strong>\<Slack\> \<nanoakron\></strong> Cool  
<strong>\<fluffypony\></strong> have we discussed the compact blocks thing ?  
<strong>\<fluffypony\></strong> I see there's some backlog on it  
<strong>\<Slack\> \<nanoakron\></strong> Briefly  
<strong>\<pero\></strong> what prevents dupes then?  
<strong>\<pero\></strong> might be better to tag issues with 'fixed in next release' or something and keep them open?  
<strong>\<revler1082\></strong> all the verification is the asme, it's just saving from re-sending txs?  
<strong>\<fluffypony\></strong> pero: dupe issues?  
<strong>\<revler1082\></strong> oh  
<strong>\<pero\></strong> yea  
<strong>\<fluffypony\></strong> lol  
<strong>\<fluffypony\></strong> revler1082: I was also confused  
<strong>\<pero\></strong> sorry =/  
<strong>\<fluffypony\></strong> np  
<strong>\<fluffypony\></strong> pero raises a good point  
<strong>\<fluffypony\></strong> I can flag them instead  
<strong>\<moneromooo\></strong> If people don't search the bugs list, they'll file a dupe whether it's closed or open, no ?  
<strong>\<Slack\> \<nanoakron\></strong> Take <https://github.com/monero-project/monero/issues/1256> as an example  
<strong>\<Slack\> \<nanoakron\></strong> May be a dupe, may not be...  
<strong>\<moneromooo\></strong> I'm fine with bugs being opened when in doubt.  
<strong>\<Slack\> \<nanoakron\></strong> @moneromooo - yes they will  
<strong>\<dEBRUYNE\></strong> \<fluffypony\> everything is confusing \<= Oh I didn't notice too  
<strong>\<pero\></strong> but they likely won't experience the issue if it's in a release  
<strong>\<dEBRUYNE\></strong> That link I posted on reddit says 17:00 Europe time lol  
<strong>\<fluffypony\></strong> lol  
<strong>\<fluffypony\></strong> ok so re: compact blocks  
<strong>\<revler1082\></strong> got some fixes and ideas from @moneromooo that i'm gonna try  
<strong>\<fluffypony\></strong> do we put it in a fork wrapper so that it only activates in Jan? or are we using the versionbits and making it available from now?  
<strong>\<revler1082\></strong> only big thing is do we want backwards compatibility and a little messier code, or alter existing stuff/cleaner?  
<strong>\<Slack\> \<nanoakron\></strong> The good thing about hard forks is that we don’t need backwards compatibility  
<strong>\<moneromooo\></strong> I'd rather have it in testnet first.  
<strong>\<Slack\> \<nanoakron\></strong> Yes  
<strong>\<revler1082\></strong> definitely  
<strong>\<fluffypony\></strong> ok let's finish the compact blocks discussion  
<strong>\<fluffypony\></strong> PowerFlower: pleasure :)  
<strong>\<moneromooo\></strong> I'd like to know what the changes are going to be with sodium/NaCl/cryptocpp/whatever. I don't know them, so I don't have useful input.  
<strong>\<Jaquee\></strong> PowerFlower: Thank you. bye  
<strong>\<moneromooo\></strong> Compact blocks: pretty good, not much to change, will need lots of testing though.  
<strong>\<revler1082\></strong> yep  
<strong>\<fluffypony\></strong> re: backwards compatibility, I don't think we need to support an environment where compact blocks isn't supported - a node that doesn't want to use it can just never claim to already have txs  
<strong>\<dEBRUYNE\></strong> revler1082: Have you tested it on a personal private testnet?  
<strong>\<revler1082\></strong> yea, and on mainnet with the backwards stuff  
<strong>\<dEBRUYNE\></strong> oh cool  
<strong>\<fluffypony\></strong> since we have a testnet reorg coming up we can use the opportunity to test wrapping it in a fork  
<strong>\<moneromooo\></strong> We need to have both block types in the code at the same time though.  
<strong>\<moneromooo\></strong> So if we do, conditional use isn't much more.  
<strong>\<moneromooo\></strong> BTW, syncing from scratch uses a different set of messages, right ?  
<strong>\<revler1082\></strong> yes i believe so  
<strong>\<moneromooo\></strong> A possible optimization would be to always include txes with too low fee, since these would have been mined by the local host.  
<strong>\<realsony\></strong> So men i read everything, didnt understand 97% :) convinces me that XMR has the best alt dev team :)  
<strong>\<moneromooo\></strong> But that's really not needed now.  
<strong>\<revler1082\></strong> yea, there's a few tweaks we can make, i like your send tx index instead of hash for missing  
<strong>\<moneromooo\></strong> Yes, it sounds like a no brainer, so I'm suspicious that bitcoin is not doing it for non obvious reasons...  
<strong>\<moneromooo\></strong> fluffypony: do you know why they use siphash hashes and not indices in the block ?  
<strong>\<moneromooo\></strong> (since you linked to that doc, I think you might know :P)  
<strong>\<fluffypony\></strong> moneromooo: I have no idea  
<strong>\<ontario\></strong> noob suggestion: for the next meeting how about disabling other chat unless dev when the meeting bot started?  
<strong>\<fluffypony\></strong> btcdrak might have an idea  
<strong>\<fluffypony\></strong> ontario: if the room goes +m then only people with +v can speak, and then it becomes a closed meeting  
<strong>\<fluffypony\></strong> better for it to stay open, we can handle the occasional interruption  
<strong>\<btcdrak\></strong> yeah that's what to do  
<strong>\<ontario\></strong> lol sry dont know much about irc things  
<strong>\<fluffypony\></strong> btcdrak: moneromooo had a question about compact blocks, and why it uses siphash hashes instead of indices  
<strong>\<moneromooo\></strong> (note, I know very little about bitcoin, so it could be tx indices don't make sense in bitcoin)  
<strong>\<btcdrak\></strong> moneromooo: ask in \#bitcoin-core-dev  
<strong>\<moneromooo\></strong> OK, I will, thanks.  
<strong>\<i2p-relay\> {-anonimal}</strong> moneromooo: re: crypto, <https://cryptopp.com/> has a list of all supported schemes. I know monero will have to keep supercop/ref10 impl but most others look covered (though I can't say <em>all</em> because I haven't yet looked at all monero crypto yet)  
<strong>\<fluffypony\></strong> my thinking is that we can offload the sensitive stuff to TweetNaCl (ie. crypto\_ops), as it's currently using SUPERCOP ref10  
<strong>\<fluffypony\></strong> then we offload everything else to cryptocpp, including random  
<strong>\<fluffypony\></strong> and then <em>if</em> we're seeing performance bottlenecking in something specific, we can use ASM implementations <em>only</em> in the places it's bottlenecking  
<strong>\<moneromooo\></strong> Since we use part of... libsodium ? Does this not do everything we need ?  
<strong>\<fluffypony\></strong> moneromooo: the libsodium source isn't even complete, so we'd have to make changes anyway  
<strong>\<fluffypony\></strong> libsodium isn't as full-featured as cryptocpp anyway  
<strong>\<fluffypony\></strong> and not as audited as TweetNaCl  
<strong>\<moneromooo\></strong> Anything else to talk about ?  
<strong>\<fluffypony\></strong> well  
<strong>\<i2p-relay\> {-anonimal}</strong> So there won't be a one-size-fits-all crypto solution, eh?  
<strong>\<fluffypony\></strong> btw moneromooo  
<strong>\<fluffypony\></strong> <https://en.wikipedia.org/wiki/NaCl*(software)>  
<strong>\<fluffypony\></strong> so TweetNaCl implements all of those  
<strong>\<fluffypony\></strong> as does libsodium  
<strong>\<fluffypony\></strong> that libsodium can do a handful of extra things is neither here nor there  
<strong>\<fluffypony\></strong> <https://en.wikipedia.org/wiki/Comparison_of_cryptography_libraries>  
<strong>\<moneromooo\></strong> I'm curious to know why they made many versions of hte same thing.  
<strong>\<fluffypony\></strong> the advantage is that cryptocpp can do a TON of stuff, it's FIPS 140 validates, and it uses the Boost license  
<strong>\<moneromooo\></strong> That sounds like a recipe for pita.  
<strong>\<fluffypony\></strong> moneromooo: of NaCl?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<fluffypony\></strong> they only made NaCl, and then they made TweetNaCl specifically to be extremely simple and auditable (so that it could be formally verified)  
<strong>\<fluffypony\></strong> NaCl was forked and thus begat libsodium  
<strong>\<fluffypony\></strong> so the original NaCl reference implementation has been replaced by libsodium, effectively  
<strong>\<moneromooo\></strong> crypto++ is the same as cryptopp ?  
<strong>\<fluffypony\></strong> yes  
<strong>\<fluffypony\></strong> also has AES-NI support, which is great  
<strong>\<fluffypony\></strong> doesn't have ARMv8 crypto support yet  
<strong>\<fluffypony\></strong> "Unix (OpenBSD, Linux, OS X, etc.), Win32, Win64, Android, iOS, ARM"  
<strong>\<Slack\> \<nanoakron\></strong> Not may Cortex-A53 ARMv8 systems in the wild seem to have hardware crypto so far…apparently they need to pay for an extra license to enable it  
<strong>\<Slack\> \<nanoakron\></strong> Pine64 may do, but I’ve not bought one yet  
<strong>\<pero\></strong> pine64 does  
<strong>\<moneromooo\></strong> So if we were to switch to cryptopp, would be still keep the existing low level crypto code, or just use for new stuff ?  
<strong>\<moneromooo\></strong> Though I guess we have a readily available test suite actually :)  
<strong>\<i2p-relay\> {-anonimal}</strong> fluffypony: I believe there is limited(?) armv8 support, or do you mean specifically aes-ni?  
<strong>\<i2p-relay\> {-anonimal}</strong> \* going off of memory, would need to confirm  
<strong>\<fluffypony\></strong> anonimal: it's not NB right now  
<strong>\<fluffypony\></strong> moneromooo: we'd switch  
<strong>\<fluffypony\></strong> even if it's piecemeal  
<strong>\<Slack\> \<nanoakron\></strong> Sorry to ask about stuff that’s already been covered - what’s the final decision for integrating fluffy blocks? Implement as-is on testnet, then with version flags for 0.10.0, then with forking code for January, then finally abandon backwards compatible code at HF 5?  
<strong>\<Slack\> \<nanoakron\></strong> So that all nodes at HF5 will use compact blocks (of whatever improved flavour comes along in the interim)  
<strong>\<pigeons\></strong> its not "forking code" though right?  
<strong>\<fluffypony\></strong> no it's not  
<strong>\<Slack\> \<nanoakron\></strong> So it could in fact be made compulsory at HF 4 without backwards compatible code?  
<strong>\<fluffypony\></strong> and I mistakenly forgot that we need to keep both block formats anyway for sync up  
<strong>\<fluffypony\></strong> so not worth putting it in an HF wrapper  
<strong>\<Slack\> \<nanoakron\></strong> Unless we checkpoint at the next HF...  
<strong>\<moneromooo\></strong> Not for 4. Seriously...
