---
title: Logs for the Monero Research Lab Meeting Held on 2019-01-21
summary: Ongoing work, New work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<sarang\></strong> FYI meeting begins shortly  
<strong>\<sarang\></strong> Current agenda: <https://github.com/monero-project/meta/issues/301>  
<strong>\<sarang\></strong> Shall we begin?  
<strong>\<suraeNoether\></strong> sure  
<strong>\<sarang\></strong> Greetings, everyone  
<strong>\<suraeNoether\></strong> letsdothis.gif  
<strong>\<oneiric\_\></strong> o/  
<strong>\<sarang\></strong> I dislike mass pings, but given certain topics, a special ping to sgp\_ ArticMine moneromooo knaccc  
<strong>\<sarang\></strong> First, ONGOING WORK  
<strong>\<ArticMine\></strong> Hi  
<strong>\<sarang\></strong> Much discussion about payment ID deprecation has occurred  
<strong>\<sarang\></strong> sgp\_ is holding an open meeting to discuss this, on 25 January: <https://github.com/monero-project/meta/issues/299>  
<strong>\<sarang\></strong> THe current proposal intends to discuss is a deprecation of unencrypted pIDs at next upgrade, followed by a ban on all payment IDs in fall  
<strong>\<sarang\></strong> The main source of contention at this point seems to be whether keeping encrypted pIDs around, whether or not the wallet supports them by default, is necessary or desired  
<strong>\<sarang\></strong> Unless there's something important to talk about regarding this, and its relationship to the upcoming fork, we can table it until sgp\_'s meeting  
<strong>\<suraeNoether\></strong> i think it's wise to table the discussion until the meeting  
<strong>\<sarang\></strong> moneromooo has been working on wallet handling of payment IDs, as well as the use of default payment IDs for transaction indistinguishability  
<strong>\<sarang\></strong> ok\!  
<strong>\<sarang\></strong> Next is block size scaling  
<strong>\<sarang\></strong> ArticMine recently posted a new proposal \\  
<strong>\<sarang\></strong> So the two on the table right now are the dual-median option (presented last time) and ArticMine's new one  
<strong>\<ArticMine\></strong> I can go over the details and answer questions  
<strong>\<sarang\></strong> ty ArticMine  
<strong>\<sarang\></strong> Here is the paste on this idea, linked earlier: <http://paste.debian.net/hidden/50f142a6/>  
<strong>\<lurkinandlearnin\></strong> To confirm, the old proposal is this? <https://github.com/noncesense-research-lab/Blockchain\_big\_bang/blob/master/models/Isthmus\_Bx\_big\_bang\_model.ipynb>  
<strong>\<ArticMine\></strong> The key part of my proposal is to separate the block weight into a long term portion LongTermBlockWeight and the balance  
<strong>\<ArticMine\></strong> LongTermBlockWeight - BlockWeight  
<strong>\<sarang\></strong> lurkinandlearnin: look at notebook line \[3\]  
<strong>\<ArticMine\></strong> LongTermBlockWeight does not include the burst potion that can go up to 50x  
<strong>\<ArticMine\></strong> So the LongTermMedianBlockWeight does not compound at 50x  
<strong>\<suraeNoether\></strong> fwiw for the folks in the audience: one of the reasons block size based on medians is a difficult question is the way medians behave...  
<strong>\<suraeNoether\></strong> most equations that have been proposed here introduce an effective time delay between how max block size is responding to previous block sizes... and it's a difference equation... and introducing time delay to difference equations can introduce very strange behavior like chaos. (example: <https://advancesindifferenceequations.springeropen.com/articles/10.1186/s13662-015-0374-1> )  
<strong>\<suraeNoether\></strong> chaos is bad  
<strong>\<suraeNoether\></strong> so most of these proposals are most easily analyzed with simulations, which provide no guarantee that things won't go crazy. i've been looking into mean-based appraoches instead of median-based approaches; this introduces the possibility that outliers become disproportionately important, but it removes chaos from the equations, so we may be able to design a globally stable approach.  
<strong>\<suraeNoether\></strong> in addition to evaluating articmine's proposal  
<strong>\<ArticMine\></strong> This is the key difference with the prior proposal that compounds the LongTermMedianBlockWeight using the entire block  
<strong>\<ArticMine\></strong> the  
<strong>\<sarang\></strong> Including the simple two-median approach, right ArticMine ?  
<strong>\<ArticMine\></strong> Yes the simple two median approach fails  
<strong>\<suraeNoether\></strong> i'm still not clear on the properties we want out of max block size adjustments  
<strong>\<ArticMine\></strong> Since it either compounds the 50x burst (my initial version) or kills the burst over time (smooth's version)  
<strong>\<sarang\></strong> ArticMine: is that paste complete as written?  
<strong>\<suraeNoether\></strong> beyond "ability to go 50x over a slow day to accommodate a christmas day, and to not allow a big bang"  
<strong>\<ArticMine\></strong> Yes  
<strong>\<sarang\></strong> Isthmus and I plan to work this in to our existing simulations  
<strong>\<sarang\></strong> His is more complete, but I am doing one for my own education and as a separate check  
<strong>\<sarang\></strong> We shall need to make a decision by freeze time  
<strong>\<sarang\></strong> ArticMine: there are a few subtleties that I'll want to ask you about later  
<strong>\<sarang\></strong> But I also would like to hear the answer to suraeNoether's question  
<strong>\<nioc\></strong> I did not see any response to smooth's comment.....  
<strong>\<nioc\></strong> you can avoid any sort of consensus issues on \*1.4 by making it 1.375 which is adding 3/8  
<strong>\<nioc\></strong> 10:50 PM or some such, but that should be close enough  
<strong>\<nioc\></strong> 10:56 PM overall looks good to me at first reading  
<strong>\<nioc\></strong> 11:02 PM i guess 4/10 is fine too, just slower (but not significant)  
<strong>\<sarang\></strong> that was a rounding issue, I suppose  
<strong>\<moneromooo\></strong> If people will fuck up with 1.4, they will fuck up with 1.375.  
<strong>\<moneromooo\></strong> For interested people, the amp branch has ArticMine's change (untested).  
<strong>\<suraeNoether\></strong> we should just pick a number that can be represented exactly in a computer  
<strong>\<moneromooo\></strong> (just the top patch)  
<strong>\<moneromooo\></strong> Better to pick one that can't. You don't want people to use floating point and think they did it right bevause the number was chosen to make things look right.  
<strong>\<sarang\></strong> branch link: <https://github.com/moneromooo-monero/bitmonero/commit/f1ee51c55963d05a78db916d41da7dc5948bb05a>  
<strong>\<suraeNoether\></strong> representing 1.4 in a computer is inexact and will cause floating point rounding problems in different pieces of software, but i think 1.375 can be represented in binary exactly and so there is no roundoff problem in that regard...  
<strong>\<sarang\></strong> also, hot dang that was fast moneromooo  
<strong>\<suraeNoether\></strong> one of the things i, personally, would like out of the block size adjustment is this  
<strong>\<ArticMine\></strong> smooth's comment would e an improvement if the BlockWeight were a factor of 8 in bytes, but it is not. So in reality it is not a material change  
<strong>\<suraeNoether\></strong> moneromooo: that's a strong argument actually  
<strong>\<suraeNoether\></strong> so, i think block size adjustment can benefit from: forcing the marginal cost of adding an additional transaction in terms of block reward penalty to be greater than the standard fees gained by including that transaction  
<strong>\<suraeNoether\></strong> even if we pick some exotic max\_block\_size calculation, we should also be changing the block reward penalty this way  
<strong>\<ArticMine\></strong> Still I see as an improvement. As per suraeNoether comment above. So we can make the change from 1.4 to 1.375  
<strong>\<suraeNoether\></strong> of course, if the block is nearly full and the block reward is almost zero, adding almost any transaction fees will make up for it  
<strong>\<suraeNoether\></strong> ArticMine: moneromooo just made a strong argument \*against\* that  
<strong>\<suraeNoether\></strong> so this marginal cost approach will be most effective when block sizes are nowhere near the big bang levels  
<strong>\<suraeNoether\></strong> which is good: providing an incentive to stay reasonable when they are already reasonable  
<strong>\<ArticMine\></strong> No When block weight is close to big bang levels LongTermBlockWeight is \<\< BlockWeight  
<strong>\<suraeNoether\></strong> i'm not talking about your block size proposal; i'm talking about block reward penalty as a function of block size  
<strong>\<lurkinandlearnin\></strong> Has any thought been given towards an incentive for miners to create smaller blocks when transaction volume is low? To slow blockchain growth  
<strong>\<suraeNoether\></strong> that's what i was just talking about lurkinandlearnin  
<strong>\<pigeons\></strong> lower blockchain growth is probably less important than quicker validation and propogation but the same point applies  
<strong>\<sarang\></strong> lurkinandlearnin: all txns get added eventually if the fee market allows  
<strong>\<suraeNoether\></strong> something isthmus brought up to me: there are only about 150,000 blocks between us and the next hard fork. with the \*simple\* two-median method will forbid a blowup before the next hard fork.  
<strong>\<suraeNoether\></strong> woops i mean between March and October hard forks  
<strong>\<moneromooo\></strong> Yes, starting the penalty before 100% (idea from smooth).  
<strong>\<suraeNoether\></strong> we should consider implementing the simple method \*first\* and spending time thinking about a more optimal solution, rather than trying to go for broke  
<strong>\<lurkinandlearnin\></strong> moneromooo: that sounds like a great idea  
<strong>\<suraeNoether\></strong> moneromooo: yep, smooth had the initial idea of sub-100%-median block penalty; my idea is to make the drop-off nonlinear so that it's more expensive to push block sizes larger in the absence of a healthy fee market  
<strong>\<sarang\></strong> Well, simulations will shortly be done for ArticMine's proposal compared to the current approach and the simple two-median  
<strong>\<sarang\></strong> Presumably the next upgrade will do one of the two options  
<strong>\<suraeNoether\></strong> okay, i don't think we're going to come to any conclusions on this, but it's been a good update  
<strong>\<suraeNoether\></strong> let's move past scaling  
<strong>\<sarang\></strong> Sure thing. We'll talk after simulation data are available  
<strong>\<sarang\></strong> Next is transaction size reduction, for which there is a PR from moneromooo  
<strong>\<sarang\></strong> AFAIK there are no new updates on this otherwise  
<strong>\<sarang\></strong> unless moneromooo you wish to say anything about it?  
<strong>\<moneromooo\></strong> I'd just like one of you Noethers to review the code before it goes in.  
<strong>\<moneromooo\></strong> suraeNoether said he'd have a look.  
<strong>\<suraeNoether\></strong> sarang let's do that \*together\* tomorrow morning? we can do it over a vidchat since we were going to meet tomorrow anyway  
<strong>\<sarang\></strong> Roger; the math looked correct to me, but I may have neglected to add a comment  
<strong>\<sarang\></strong> ok suraeNoether can do  
<strong>\<suraeNoether\></strong> fun  
<strong>\<suraeNoether\></strong> as for the semi-final point on the agenda... what's the deal with bulletproofs, anyway? seinfeld.gif  
<strong>\<sarang\></strong> lol  
<strong>\<suraeNoether\></strong> DID YOU GUYS MAKE THINGS FASTER AGAIN  
<strong>\<sarang\></strong> Only a brief update that some BP verifier optimizations didn't make it into the 0.13 release  
<strong>\<sarang\></strong> a very unscientific test on my box resulted in a 64-batch of 2-proofs verifying 60% faster  
<strong>\<sarang\></strong> kudos to moneromooo for continuing to squeeze speed out of those suckers  
<strong>\<lurkinandlearnin\></strong> holy smokes  
<strong>\<lurkinandlearnin\></strong> 60% faster than current impl or than pre-BP?  
<strong>\<sarang\></strong> than the 0.13 release code  
<strong>\<suraeNoether\></strong> jeez  
<strong>\<sarang\></strong> that is, 0.13 vs master  
<strong>\<sarang\></strong> as of a few days ago  
<strong>\<suraeNoether\></strong> where did this speedup come from?  
<strong>\<sarang\></strong> Folding in some multiexponentiation operations, as well a host of other voodoo moneromooo can dooo  
<strong>\<sarang\></strong> So we can brag about the next release making txns smaller and faster again :D  
<strong>\<moneromooo\></strong> I did not keep track of which change sped up by how much. I think sarang's single multiexp change is probably the biggest one though.  
<strong>\<sarang\></strong> Let's now discuss NEW WORK  
<strong>\<suraeNoether\></strong> cool\!  
<strong>\<sarang\></strong> suraeNoether: your personal updates?  
<strong>\<suraeNoether\></strong> personally, this past week was largely a konferenco administration week for me, contacting speakers and vendors and getting my bank compliant with me  
<strong>\<suraeNoether\></strong> i did research on bulletproofs, linear algebra in cryptography, and our matching paper  
<strong>\<sarang\></strong> I'm sooper excited for this conference  
<strong>\<suraeNoether\></strong> but a lot of my work this week was contacting possible speakers  
<strong>\<sarang\></strong> sounds like we'll have some big names joining us  
<strong>\<suraeNoether\></strong> yes, it's pretty great so far; we are adding more names this week  
<strong>\<sarang\></strong> Any updates on the matching paper suraeNoether ?  
<strong>\<suraeNoether\></strong> my simulations aren't passing unit tests  
<strong>\<suraeNoether\></strong> once they do, i'm making a commit  
<strong>\<suraeNoether\></strong> and then collecting data  
<strong>\<suraeNoether\></strong> so: it's moving forward  
<strong>\<sarang\></strong> excellent  
<strong>\<sarang\></strong> Any questions for suraeNoether ?  
<strong>\<sarang\></strong> OK, I'll go next  
<strong>\<suraeNoether\></strong> oh i had one more thing to bring up  
<strong>\<suraeNoether\></strong> sorry sarang, i don't want to interrupt  
<strong>\<sarang\></strong> np go ahead  
<strong>\<lurkinandlearnin\></strong> is there a list of speakers for the conference?  
<strong>\<suraeNoether\></strong> i found all those old Monero Protocol Standards documents I started writing last year, and I'm wondering if folks still want me to compose the v0.1 versions of these rather short text documents into something to put up on our github  
<strong>\<lurkinandlearnin\></strong> or not official yet?  
<strong>\<suraeNoether\></strong> lurkinandlearnin: check out konferenco.xyz  
<strong>\<suraeNoether\></strong> the benefit of having the standards instead of a single big zero-to-monero document is this:  
<strong>\<suraeNoether\></strong> we can update each one piecemeal and only update it if something has changed. this reduces overhead work on documentation. and if it's on github, anyone can update them, we don't have to go find kurt magnus or koe  
<strong>\<sarang\></strong> FWIW the ZtM doc is on github and can be PRed  
<strong>\<sarang\></strong> but I see the point about modularity  
<strong>\<sarang\></strong> My pessimistic side worries that updates would fall behind, as they already have on ZtM  
<strong>\<lurkinandlearnin\></strong> What aspects of the protocol are covered? Could be something useful to incorporate into the often neglected wiki  
<strong>\<lurkinandlearnin\></strong> as they both sound modular  
<strong>\<suraeNoether\></strong> lurkinandlearnin: essentially similar to the cryptonote standards they released after i reviewed their whitepaper years ago, like this: <https://cryptonote.org/cns/cns006.txt>  
<strong>\<suraeNoether\></strong> (my whitepaper review would have been moderately better if they wrote those standards before the whitepaper, but hey)  
<strong>\<suraeNoether\></strong> sarang your points are valid  
<strong>\<suraeNoether\></strong> which is why i'm not sure if it's a good idea to devote time to it  
<strong>\<Isthmus\></strong> Wiki is a good idea, specs are a good idea. Having experience as a book editor, people making random PRs is a huge nightmare to text style and continuity and often took 4x as long to polish then if SerHack and I had written ourselves.  
<strong>\<suraeNoether\></strong> okay, how about this  
<strong>\<sarang\></strong> Whatever is made available, whether ZtM or wiki or standards, keeping up to date is the most important aspect IMO  
<strong>\<sarang\></strong> I cringe at "text-rendered math" though...  
<strong>\<Isthmus\></strong> Maybe we should pick one to be the "reference" documentation and the others follow suite?  
<strong>\<sarang\></strong> Who's responsible for maintenance of each one?  
<strong>\<lurkinandlearnin\></strong> Well as long as the version at time of writing is very clear keeping it updated is not so critical  
<strong>\<suraeNoether\></strong> sarang who's responsbile for maintaining anything around here?  
<strong>\<sarang\></strong> lurkinandlearnin: I disagree  
<strong>\<suraeNoether\></strong> how about i just post what i have after making it a little more readable, and if someone wants to run with it they can  
<strong>\<lurkinandlearnin\></strong> nice, but not disastrous. If anything having info about how things used to work out there is also useful.  
<strong>\<suraeNoether\></strong> i can post it on my personal github to avoid cluttering the primary\\  
<strong>\<sarang\></strong> suraeNoether: I think that'd be useful, to get a better sense of scope of audience  
<strong>\<suraeNoether\></strong> sarang: we can always label them clearly DEPRECATED AND NOT USEFUL. but i think it'd be better to have them out there  
<strong>\<sarang\></strong> good point  
<strong>\<suraeNoether\></strong> okay handing it back to sarang  
<strong>\<sarang\></strong> As long as it's clear what can be considered "closer to canonical"  
<strong>\<sarang\></strong> So I've had some testing and minor optimizations to BPs for the next release, as mentioned earlier  
<strong>\<sarang\></strong> Minor work on simulating block size changes to confirm work by Isthmus on scaling etc.  
<strong>\<sarang\></strong> Recording of new Breaking Monero episodes with sgp\_  
<strong>\<sarang\></strong> The usual new lit and project review  
<strong>\<sarang\></strong> and some work on a safe MPC protocol for Bulletproofs for future use  
<strong>\<sarang\></strong> as well as a lot of back-and-forth administrivia on the topics for the Boron upgrade  
<strong>\<sarang\></strong> I am personally in favor of either Boron Betelgeuse or Boron Bellatrix  
<strong>\<sarang\></strong> (as far as names go)  
<strong>\<sarang\></strong> and of course the math for graph matchings, which has been passed back to suraeNoether for simulation data that he is obtaining  
<strong>\<lurkinandlearnin\></strong> Betelgeuse will lead to a schism in the community over pronounciation  
<strong>\<sarang\></strong> precisely  
<strong>\<sarang\></strong> It's like the naming of iPhone X... by making it hard to get right, it forces you to think it's better than you are  
<strong>\<sarang\></strong> humbles us all  
<strong>\<lurkinandlearnin\></strong> "It gets the people going\!"  
<strong>\<sarang\></strong> Any questions for me?  
<strong>\<lurkinandlearnin\></strong> what's the next breaking monero topic?  
<strong>\<moneromooo\></strong> Hmm... Lightning network things ?  
<strong>\<sarang\></strong> moneromooo: what questions on that?  
<strong>\<Isthmus\></strong> "Boron borealis" ?? I think there's a Harry Potter character called Bellatrix, which could get confusing with all the HP-themed MimbleWimble names.  
<strong>\<sarang\></strong> lurkinandlearnin: we have several topics in the lineup, to be arranged  
<strong>\<Isthmus\></strong> Also, Breaking Monero = awesome, thanks for all the time going into that series :- D  
<strong>\<moneromooo\></strong> Was anything done or thought about recently about anything monero needs for LN or LN style system ?  
<strong>\<sarang\></strong> moneromooo: some of it was an efficient and fungible way to handle protocol aborts, a la noninteractive refunds  
<strong>\<sarang\></strong> that was quietly tabled as several proposals for interactive refunds were thrown around  
<strong>\<moneromooo\></strong> Ah yes. It would be nice to see a list of things that are needed in monero as building blocks. In terms of parenthesized AND/OR. I always forget. Or never knew.  
<strong>\<sarang\></strong> That's a good point. Having a well-considered status update will be useful for longer-term planning  
<strong>\<sarang\></strong> Does anyone else have updates to share, before we adjourn?  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> Thanks to everyone for joining  
<strong>\<sarang\></strong> Our current action items:  
<strong>\<sarang\></strong> (a) simulation data for block size proposals, to make a decision before freeze  
<strong>\<sarang\></strong> (b) final review of transaction size reduction PR  
<strong>\<sarang\></strong> (c) meeting to decide on payment ID deprecation (PLEASE attend or comment on github issue if you have an opinion on this, with justification/data)  
<strong>\<sarang\></strong> at ease, soldiers
