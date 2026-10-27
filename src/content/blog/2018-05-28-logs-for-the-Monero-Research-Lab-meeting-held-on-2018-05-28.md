---
title: Logs for the Monero Research Lab Meeting Held on 2018-05-28
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> sure\~  
<strong>\<suraeNoether\></strong> Greetings everyone  
<strong>\<suraeNoether\></strong> welcome to the MRL Research meeting for the week  
<strong>\<rbrunner\></strong> Hi. Lurking for one here :)  
<strong>\<sarang\></strong> yo  
<strong>\<suraeNoether\></strong> mostly an informal discussion of what we've all been getting up to for the past week  
<strong>\<ArticMine\></strong> hi  
<strong>\<jwinterm\></strong> o/  
<strong>\<sarang\></strong> Happy Memorial Day to those who celebrate it today\!  
<strong>\<suraeNoether\></strong> i know sarang has been discussing fees with myself and ArticMine, and we both have been talking about multisig with each other... does anyone want to put an item on the agenda?  
<strong>\<suraeNoether\></strong> otherwise, sarang and I can just describe what we've done this past week and get on to it, but i know some folks have been working on a lot of stuff  
<strong>\<suraeNoether\></strong> oh, man i forgot to ping UkoeHB  
<strong>\<endogenic\></strong> ya if i may, you should ping ppl at the start of the mtg  
<strong>\<sarang\></strong> Yes there is plenty to discuss for BPs, fees, and optimizations  
<strong>\<suraeNoether\></strong> endogenic: I pinged people about 20 minutes ago  
<strong>\<suraeNoether\></strong> but point taken  
<strong>\<suraeNoether\></strong> Sarang, how about you go first  
<strong>\<sarang\></strong> I worked with moneromooo to speed up BPs  
<strong>\<suraeNoether\></strong> we can let people jump in with questions  
<strong>\<sarang\></strong> Here is timing data for the expensive multiexp operations they use, to illustrate: <https://imgur.com/a/rZB0vin>  
<strong>\<sarang\></strong> The green bar, Pippenger, is the new one  
<strong>\<sarang\></strong> BPs start at 256 points, on the x-axis  
<strong>\<suraeNoether\></strong> cool\!  
<strong>\<endogenic\></strong> suraeNoether: think both can be helpful  
<strong>\<sarang\></strong> Once we finish up some testing, BPs will use a combination of algorithms. The speedup on the operations has been clocked at 40% of the original  
<strong>\<sarang\></strong> The audits continue  
<strong>\<sarang\></strong> What really remains is determining fees, as was discussed last week  
<strong>\<suraeNoether\></strong> fluffypony knaccc luigi1111 anonimal andytoshi ArticMine binaryFate chachasmooth dEBRUYNE endogenic gingeropolous hyc iDunk IsthmusCrypto john\_alan JollyMort\[m\] jwinterm kenshi84 medusa\_ moneromooo MoroccanMalinois needmoney90 nioc nioc\_ othe philkode rehrar rrol\[m\] sgp\_\[m\] smooth sneurlax\[m\]1 stoffu TheCharlatan unknownids vtnerd waxwing  
<strong>\<suraeNoether\></strong> okay, so let's talk about fees really quick  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> since verification times are roughly constant across powers of 2 (in terms of number of outputs) and the space is proportional to the number of outputs, we can get a good simple fee model going  
<strong>\<sarang\></strong> This chart shows timings \_before\_ the new Pippenger optimizations: <https://docs.google.com/spreadsheets/d/1HPk2a0atBqLqUlxQqBLiQXEJi-e1egIMYu3tS1NGHUo/edit#gid=0>  
<strong>\<sarang\></strong> It's the same chart as I presented last week, but gives an idea of timings  
<strong>\<suraeNoether\></strong> say N = \# outputs, and 2^(m-1) \< N \<= 2^m. then space is approximately N and verification time is approximately m = round(lg2(N)).  
<strong>\<sarang\></strong> The timings also do \_not\_ account for batch verification, since that depends on what size proofs a client has  
<strong>\<sarang\></strong> suraeNoether: space does not scale linearly with the \# of outputs  
<strong>\<ArticMine\></strong> It essentially forces verification time as the major pricing element when comparing a 2 output proof with 2^N output proof  
<strong>\<sarang\></strong> Yes. Compared to Borromean, space is basically constant  
<strong>\<sarang\></strong> at least across the ranges we deal with  
<strong>\<ArticMine\></strong> 64 bytes for each additional factor of 2  
<strong>\<ArticMine\></strong> From the table  
<strong>\<sarang\></strong> yes, it's a very small increase  
<strong>\<sarang\></strong> but among all costs to consider, it's the smallest  
<strong>\<suraeNoether\></strong> wait, sarang, verificaiton time is O(N) and space is lg(N), right? according to that table we glanced at earlier  
<strong>\<sarang\></strong> For single verification, yes, but it scales with the next power of 2 from N  
<strong>\<suraeNoether\></strong> right  
<strong>\<sarang\></strong> We don't have the more general BPs that can handle any number of outputs cleanly  
<strong>\<sarang\></strong> (and we'd never get that change audited since it's tricky and not published)  
<strong>\<suraeNoether\></strong> so, my point is: if we consider space to be wasted download time, then everything is about time, not space-and-time  
<strong>\<suraeNoether\></strong> and so for fees  
<strong>\<sarang\></strong> more or less  
<strong>\<suraeNoether\></strong> we can either do space+time, and pick some constants a, b and charge fees a\*lg(N) + b\*N  
<strong>\<suraeNoether\></strong> or we can do space\*time and pick some constant a and charge fees a\*N\*lg(N)  
<strong>\<ArticMine\></strong> Yes we can convert between space and time. The question becomes the conversion factor  
<strong>\<suraeNoether\></strong> so, for a 2-in-2-out transaction  
<strong>\<suraeNoether\></strong> lg(N) = 1, N=2, so we charge a base fee of 2\*a  
<strong>\<suraeNoether\></strong> whatever we think is fair for that, say a = 1 piconero  
<strong>\<ArticMine\></strong> We have to modify the penalty formula this is critical  
<strong>\<ArticMine\></strong> To reflect the time component  
<strong>\<ArticMine\></strong> So converting time back to space is the simplest way  
<strong>\<rehrar\></strong> ok here  
<strong>\<suraeNoether\></strong> ArticMine: the time component is linear in number of outputs, and I think the penalty formula is already linear in the number of outputs?  
<strong>\<ArticMine\></strong> We can use the 2 output proof ans the starting point. Then add a space weight linear to the number of outputs to account for the time  
<strong>\<suraeNoether\></strong> wait, i'm getting myself confused here  
<strong>\<sarang\></strong> Are we accounting for the fact that a 9-proof and a 15-proof take the same verification time, roughly?  
<strong>\<suraeNoether\></strong> that's a hugely important observation  
<strong>\<ArticMine\></strong> The penalty formula is size based and includes all the transaction inputs  
<strong>\<suraeNoether\></strong> ArticMine: okay, so check this out  
<strong>\<ArticMine\></strong> We have to price 9 and 16 the same  
<strong>\<suraeNoether\></strong> ArticMine: the time to verify is approximately linear in size  
<strong>\<suraeNoether\></strong> ArticMine: in number of outputs i mean  
<strong>\<ArticMine\></strong> Time to verify is linear in outputs for each 2^N  
<strong>\<ArticMine\></strong> so 9 and 16 is the same  
<strong>\<sarang\></strong> It's linear in the number of outputs used, but we pad to ensure there are always 2^m  
<strong>\<sarang\></strong> We'd need the unpublished BP modifications to get rid of that requirement  
<strong>\<ArticMine\></strong> because of padding  
<strong>\<suraeNoether\></strong> assuming everything is being rounded up to the nearest power of 2, time = O(N outs). space = O(log(N outs)), essentially. so fees can be a\*N + b\*log(N). agreed or disagreed? if measured in atomic units of monero, we can write this as N + c\*log(N) if we like and if we want to pick c carefully.  
<strong>\<sarang\></strong> We do get much smoother time changes if we use separate proofs  
<strong>\<sarang\></strong> but at the cost of greater size  
<strong>\<sarang\></strong> This discussion is all assuming we require a single proof  
<strong>\<suraeNoether\></strong> i am not assuming that at all  
<strong>\<suraeNoether\></strong> i'm going proof-by-proof  
<strong>\<sarang\></strong> Well  
<strong>\<sarang\></strong> If we split proofs, each proof is an optimal size from a verification perspective  
<strong>\<suraeNoether\></strong> if every proof pays fees in proportion to both space and time, then there's an economic incentive for wallet software to find the best solutions for output management  
<strong>\<sarang\></strong> If we round, some are more optimal than others  
<strong>\<suraeNoether\></strong> if someone wants to make a sloppy BP, then \*fine\* let them pay for it by simply charging in proportion to number of outputs. is what i'm saying  
<strong>\<ArticMine\></strong> suraeNoether Yes size which determines penalty which in turn sets fees would follow a\*N + b\*log2(N)  
<strong>\<suraeNoether\></strong> ok so next question: how many fees should a 2-in, 2-out transaction incur? what about a 2-in, 4-out transaction?  
<strong>\<ArticMine\></strong> Though given the data I suspect that a\*N will be dominant  
<strong>\<suraeNoether\></strong> ArticMine: it will be  
<strong>\<suraeNoether\></strong> but since most txns are 2-in, 2-out, we're really over-optimizing the crap out of this  
<strong>\<jwinterm\></strong> is it only the number of outputs that affects the verification time for BPs?  
<strong>\<suraeNoether\></strong> all we need is a quick metric that asymptotically matches the cost in space and time. that's all we need. :P  
<strong>\<ArticMine\></strong> For 2 in 2 out there is not change from the current formula  
<strong>\<sarang\></strong> jwinterm: yes  
<strong>\<ArticMine\></strong> Since this will be used as the base tx size  
<strong>\<suraeNoether\></strong> okay, so call that fee F  
<strong>\<suraeNoether\></strong> and we set F = a\*2 + b\*1  
<strong>\<sarang\></strong> ArticMine: but I assume the prefactor will be smaller than currently  
<strong>\<sarang\></strong> Since we're dropping both verification time and space from the current txns  
<strong>\<suraeNoether\></strong> now for a 2-in 4-out transaction  
<strong>\<suraeNoether\></strong> oh, we don't want to do that one  
<strong>\<suraeNoether\></strong> we need linearly independent choices  
<strong>\<suraeNoether\></strong> so what about a 1-in, 2-out transaction?  
<strong>\<suraeNoether\></strong> ah, the fees will be the same  
<strong>\<suraeNoether\></strong> heh  
<strong>\<suraeNoether\></strong> okay, so what about a 3-output transaction?  
<strong>\<suraeNoether\></strong> for a 4-output transaction, they'll pay double, so we may as well make a 3-output transaction 50% more  
<strong>\<ArticMine\></strong> 3 out same as 4 out  
<strong>\<suraeNoether\></strong> oh ok  
<strong>\<suraeNoether\></strong> that works too  
<strong>\<ArticMine\></strong> The will pay double on the proof  
<strong>\<ArticMine\></strong> very likely but not on the rest of the tx  
<strong>\<moneromooo\> \<@suraeNoether\></strong> but since most txns are 2-in, 2-out, we're really over-optimizing the crap out of this  
<strong>\<moneromooo\></strong> No, because this is a defense against attacks.  
<strong>\<moneromooo\></strong> So you have to consider the worst case here.  
<strong>\<UkoeHB\></strong> jumping in: yay new chapter  
<strong>\<UkoeHB\></strong> <https://www.pdf-archive.com/2018/05/28/zero-to-monero-first-edition-v0-17/zero-to-monero-first-edition-v0-17.pdf>  
<strong>\<ArticMine\></strong> Which is why we have to add a space penalty term for the spoace gains in say 2 out to 4 out 8 out etc  
<strong>\<suraeNoether\></strong> thanks UkoeHB  
<strong>\<suraeNoether\></strong> okay, so ArticMine and sarang, let's talk about fees after the meeting  
<strong>\<ArticMine\></strong> Sure  
<strong>\<suraeNoether\></strong> i don't want to waste a bunch of folks' time, but I think I have a formula  
<strong>\<suraeNoether\></strong> sarang, my understanding is you are taking June off to teach, correct? and that during that time you'll be volunteering your time at MRL to complete, for example, the bulletproof audit  
<strong>\<sarang\></strong> Yes, I'll be teaching a crypto course for Duke  
<strong>\<sarang\></strong> w/o FFS pay  
<strong>\<sarang\></strong> I'll be volunteering time to manage the BP udit  
<strong>\<sarang\></strong> \*audit  
<strong>\<sarang\></strong> If it ends up being more time than expected, I can adjust the next FFS accordingly  
<strong>\<sarang\></strong> The first week of June is BS training, so I'll be partially available  
<strong>\<suraeNoether\></strong> cool. UkoeHB care to share/describe your newest chapter in zero-to-monero?  
<strong>\<UkoeHB\></strong> blockchain  
<strong>\<sarang\></strong> lol  
<strong>\<suraeNoether\></strong> "blockchain" he said, with stars in his eyes  
<strong>\<sarang\></strong> short and sweet  
<strong>\<UkoeHB\></strong> and two new appendices: block content, genesis block  
<strong>\<sarang\></strong> If I were a VC, that statement alone would get you funding  
<strong>\<UkoeHB\></strong> lol  
<strong>\<suraeNoether\></strong> sarang i should have asked: do you have anything else you want to talk about before we move on?  
<strong>\<sarang\></strong> Did a little timing on the noninteractive refund stuff, turns out they're a little faster than typical signatures  
<strong>\<sarang\></strong> finished up the tech note, hoping for internal review before we release  
<strong>\<suraeNoether\></strong> oh yeah, i wanted to ask: think there's a way we could compute \*all\* our key image basepoints in a way that can exploit the speed-up you discovered?  
<strong>\<suraeNoether\></strong> sarang, can you also give us a link to your dual output tech note?  
<strong>\<sarang\></strong> <https://www.sharelatex.com/read/vcyxgpntfsgz>  
<strong>\<sarang\></strong> I don't know a great way to do it safely with just the single pubkey value  
<strong>\<suraeNoether\></strong> k  
<strong>\<sarang\></strong> If anything I'd rather find a way to reconstruct MLSAG to use other speedups  
<strong>\<sarang\></strong> but I've given almost zero thought to that  
<strong>\<suraeNoether\></strong> so, in the past week I've read this paper in detail (<https://scholar.google.com/scholar?cluster=15619301617669058049&hl=en&as\_sdt=0,6>) and this paper in detail (<https://arxiv.org/abs/1503.08768>) and this paper in detail (<https://scholar.google.com/scholar?hl=en&as\_sdt=0%2C6&q=okamoto+beats+schnorr&btnG=>) and this paper in detail (<https://eprint.iacr.org/2018/068>) to get to the bottom of this multisig  
<strong>\<suraeNoether\></strong> unforgeability proof  
<strong>\<suraeNoether\></strong> the long story short: I believe that by adding the commit-and-reveal phase of the musig appraoch to our ring signatures will result in a provably unforgeable scheme  
<strong>\<sarang\></strong> too bad they couldn't fix it without that phase  
<strong>\<suraeNoether\></strong> it's fine, i like that phase in general  
<strong>\<sarang\></strong> but it also improves the security assumptions  
<strong>\<suraeNoether\></strong> commitment isnt' scary, sarang  
<strong>\<suraeNoether\></strong> yes, it does  
<strong>\<suraeNoether\></strong> unfortunately, we fork all over the place  
<strong>\<suraeNoether\></strong> and depending on the constructions, things can get out of hand rather quickly  
<strong>\<suraeNoether\></strong> on the plus side, the paper is, once again... smaller than it was. :D  
<strong>\<suraeNoether\></strong> unfortunately i'm debugging some latex code so it's not viewable right now  
<strong>\<suraeNoether\></strong> that has basically been my whole life this past week, although I spent some time looking into what it would take for a zk-ledger-based sidechain to work merge-mined with monero  
<strong>\<suraeNoether\></strong> i believe a very private "banking system" with off-chain transaction processing through semi-trusted third parties could be a second layer on top of monero  
<strong>\<suraeNoether\></strong> but that's not where my mind has really been at, which has been on multisignature unforgeability proofs  
<strong>\<suraeNoether\></strong> sarang, I believe, will be posting his monthly report, as will I...  
<strong>\<suraeNoether\></strong> and later today, I'm helping advise zcash foundation on how to spend a quarter million of their dollars on grants  
<strong>\<suraeNoether\></strong> anyone have any questions?  
<strong>\<sarang\></strong> Yep, my report will go up later today, once I again remind myself how markdown works on various platforms  
<strong>\<sarang\></strong> I love how it's different EVERYWHERE  
<strong>\<suraeNoether\></strong> oh, and we have formalized our research roadmap from our meeting last week\! i can't believe I forgot to metnion that  
<strong>\<sarang\></strong> aye  
<strong>\<suraeNoether\></strong> <https://github.com/monero-project/research-lab/issues/29>  
<strong>\<suraeNoether\></strong> if anyone has questions or concerns or comments, that's a good place to throw them  
<strong>\<UkoeHB\></strong> oh you can update z-to-m link with new draft :)  
<strong>\<suraeNoether\></strong> yay  
<strong>\<IsthmusCrypto\></strong> Nice roadmap. I'll definitely want to be in the loop for item 4, the "research infrastructure" - and I'll try to contribute myself.  
<strong>\<suraeNoether\></strong> good to hear :D  
<strong>\<suraeNoether\></strong> allright, well, let's finish this \</meeting\> and talk about fees
