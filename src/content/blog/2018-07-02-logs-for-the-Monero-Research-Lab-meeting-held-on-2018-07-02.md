---
title: Logs for the Monero Research Lab Meeting Held on 2018-07-02
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> First, greetings  
<strong>\<needmoney90\></strong> Yawns\*  
<strong>\<sarang\></strong> well, greetings  
<strong>\<needmoney90\></strong> Hopefully a little more people than the Dev meeting, but prolly not, because of the holidays  
<strong>\<sarang\></strong> For my sake at least, I'm very interested in the current state of folks' projects or undertakings  
<strong>\<needmoney90\></strong> Does Merkato count?  
<strong>\<serhack\></strong> Hi :)  
<strong>\<serhack\></strong> Does Mastering Monero count?  
<strong>\<sarang\></strong> fo sho  
<strong>\<needmoney90\></strong> Currently one of the next steps for Merkato is calculating the optimal spread, which is some fun math that scares me  
<strong>\<sarang\></strong> elaborate?  
<strong>\<sneurlax\></strong> Hi all, small update and that's it, I quit my job so I'm resuming work on my small project related to scraping mining pools. I apologize it took so long, but my job got incredibly demanding incredibly quickly... So I quit\!  
<strong>\<luigi1111w\></strong> that's what I do when the going gets tough  
<strong>\<needmoney90\></strong> <https://arxiv.org/pdf/1606.07381.pdf>  
<strong>\<needmoney90\></strong> Starts on describing the optimal spread Calc  
<strong>\<needmoney90\></strong> I need to dive into it  
<strong>\<sarang\></strong> interesting\!  
<strong>\<sarang\></strong> I finished up my teaching and also worked with the auditors more  
<strong>\<sarang\></strong> QL and Kudelski are finishing up reports  
<strong>\<sarang\></strong> There was, of course, also the twitteresearcher  
<strong>\<hyc\></strong> all hail twitter  
<strong>\<sarang\></strong> His notes about subgroup checking were also identified by our audit  
<strong>\<sarang\></strong> and will be incorporated into some easy checks on the code  
<strong>\<silur\></strong> as far for me on RTRS-StringCT I didn't have any advance on testing for the last 2 weeks :(  
<strong>\<silur\></strong> neither on Lattice-based bulletproofs  
<strong>\<sarang\></strong> suraeNoether sent me more details on sublinear ring sigs but that was just yesterday  
<strong>\<sarang\></strong> I'm sure he will have more to say on this  
<strong>\<serhack\></strong> I just need a technical feedback because I am not sure I wrote anything correctly in Mastering Monero. You can read by viewing this pdf <https://masteringmonero.com/book/preview.pdf> . Thanks\! :) Feel free to message me for any inputs\!  
<strong>\<silur\></strong> yea that's why RTRS is on hold now, the scheme changed a lot since I started implementing  
<strong>\<sarang\></strong> yes indeedy  
<strong>\<suraeNoether\></strong> eek, time got away from me. sorry about that everyone\! i'm here, i swear, i'm writing a document on blockdags and got excited :(  
<strong>\<sarang\></strong> The incorporation of an internal range proof is intriguing  
<strong>\<sarang\></strong> suraeNoether: what about blockdags?  
<strong>\<sarang\></strong> go on  
<strong>\<suraeNoether\></strong> oh, i think i have a "fast" version of a blockdag based approach to transactions sort of similar to spectre  
<strong>\<suraeNoether\></strong> i'm looking at convergence rates and such  
<strong>\<sarang\></strong> Ah, new work?  
<strong>\<suraeNoether\></strong> yeah. going into details, the problem with blockdag schemes is ordering blocks that aren't linked to each other (so-called "antichains")  
<strong>\<sarang\></strong> correct  
<strong>\<sarang\></strong> that's the hangup in computation  
<strong>\<suraeNoether\></strong> and i think I realized a structure built into the blockdag approach that allows for a rather fast linear ordering of otherwise unordered blocks  
<strong>\<sarang\></strong> that would be hugely useful\!  
<strong>\<suraeNoether\></strong> in the end, if all these different metrics end up being equal, you end up hashing block headers either way, so the probability of two blocks having the same place in the line is negligible either way, and it should be quick  
<strong>\<sarang\></strong> What other projects have kept you busy during my absence suraeNoether ?  
<strong>\<suraeNoether\></strong> oh gosh, i made commits to my PoissonGraphs project, which allegedly spits out a human-readable cryptocurrency network simulation's transcript... and i've been communicating with tim ruffing about his new sublinear ring signature scheme...and I've been trying to get a handle on the multisig KOSK setting and UkoeHB's rewind/replay problem.  
<strong>\<sarang\></strong> excellent  
<strong>\<sarang\></strong> Anyone else with news or updates? I have a month of "lack of knowledge" to account for\!  
<strong>\<silur\></strong> @suraeNoether pls relay any info on RTRS from ruffiing if available\!  
<strong>\<suraeNoether\></strong> i believe we've spoken about the twitterstorm "problems with bulletproofs and ed25519" thing?  
<strong>\<sarang\></strong> yes  
<strong>\<sarang\></strong> Here's the lowdown  
<strong>\<sarang\></strong> I thought we were performing key checks at a lower level already, but I was mistaken  
<strong>\<sarang\></strong> After speaking with the auditors (who also noticed this), they recommended adding some checks  
<strong>\<sarang\></strong> for subgroup membership and point-at-infinity  
<strong>\<sarang\></strong> as well as checking for null scalars  
<strong>\<sarang\></strong> However  
<strong>\<sarang\></strong> They, like us, were unable to identify any way that the absence of such checks could be exploited  
<strong>\<sarang\></strong> But this is precisely why we audit  
<strong>\<suraeNoether\></strong> long story short: the bulletproof method uses a group of prime order. we use a group of composite order, and while we restrict all our keys to the prime order subgroup, we didn't have checks to guarantee that someone wasn't feeding non-subgroup elements into the bulletproof as inputs  
<strong>\<sarang\></strong> So, once we deploy bulletproofs, we can get to RTRS and make bulletproofs obsolete =p  
<strong>\<sarang\></strong> basically, yes  
<strong>\<sarang\></strong> it's an easy and fairly cheap thing to check  
<strong>\<suraeNoether\></strong> this leaves open the logical possibility that someone coudl produce a bulletproof that passes the verification algorithm correctly, but does not present a valid proof of the range of the argument. as sarang said, \*there is no way we have yet identified to do this.\* but \*it's a logical possibility\* and we deal in the realm of provable security in this here lab  
<strong>\<sarang\></strong> On a more irritating note, Benedikt indicated on twitter that he had not yet begun his review, which was not indicated in his communications to me, and I've been unable to reach him for details  
<strong>\<suraeNoether\></strong> sarang: the new RTRS scheme with bulletproofs is faster than the scheme with their "included" range proofs  
<strong>\<suraeNoether\></strong> ...  
<strong>\<sarang\></strong> suraeNoether: ok, haven't looked into newRTRS at all  
<strong>\<silur\></strong> which new? :D  
<strong>\<moneromooo\></strong> By RTRS, you mean the new paper by Ruffing et al ?  
<strong>\<silur\></strong> there's like new-new-new-RTRS :D  
<strong>\<sarang\></strong> lol, the internal paper suraeNoether showed me  
<strong>\<suraeNoether\></strong> let's say RTRS2  
<strong>\<suraeNoether\></strong> it's actually... one sec  
<strong>\<sarang\></strong> the paper was marked to be for internal review only  
<strong>\<suraeNoether\></strong> LRRSTW signatures now. :D  
<strong>\<sarang\></strong> omg no more  
<strong>\<suraeNoether\></strong> different authors than RTRS  
<strong>\<ArticMine\></strong> What are the implications if any for verification cost vs 1) number of outputs, 2) number of rings?  
<strong>\<suraeNoether\></strong> ArticMine: number of rings = ring members?  
<strong>\<sarang\></strong> TBD  
<strong>\<silur\></strong> LRRSTW is even new for me  
<strong>\<sarang\></strong> they have some data  
<strong>\<ArticMine\></strong> yes  
<strong>\<suraeNoether\></strong> ArticMine: eyeballing their results, it looks like we can have 2.4kb, ring-sized 64 signatures that take as much time to verify as (approximately) one of our current ring signatures with ring size 16...  
<strong>\<suraeNoether\></strong> BUT  
<strong>\<suraeNoether\></strong> it's POSSIBLE that the verification time there needs to double  
<strong>\<suraeNoether\></strong> in which case we could go for 2.0kb, ring sized 32 signatures that take as much time to verify as one of our MLSAGs at ring size 8-10  
<strong>\<sarang\></strong> My view is that once we prototype it, we'll get a better sense of the op counts  
<strong>\<suraeNoether\></strong> note: these are actually really huge signatures  
<strong>\<sarang\></strong> and that will tell us verification times  
<strong>\<sarang\></strong> suraeNoether: agree?  
<strong>\<suraeNoether\></strong> sarang: sure, although there is a table of op counts in the back  
<strong>\<ArticMine\></strong> Is there a scaling issue when compared to tx size with increasing the number of ring members?  
<strong>\<suraeNoether\></strong> we can literally compute whether it's worth it to even prototype it  
<strong>\<suraeNoether\></strong> (and i'm doing that calculation this afternoon)  
<strong>\<suraeNoether\></strong> ArticMine: yes, these signatures are sublinear, are almost as fast as our current signatures... but their size constants are bigger than ours, and the sublinearity doesn't become worth it in terms of size until 10-12 ring members  
<strong>\<ArticMine\></strong> Subliner with tx size?  
<strong>\<suraeNoether\></strong> oh i thought you meant by ring member, excuse me  
<strong>\<suraeNoether\></strong> i'm not sure what you mean, then. signature size is related to both the number of inputs and outputs.  
<strong>\<sarang\></strong> Whats the level of incompatibility with what we're doing now?  
<strong>\<iDunk\></strong> 1 sig for all inputs (and outputs), IIRC from yesterday.  
<strong>\<suraeNoether\></strong> unsure yet, i'm optimistic that it doesn't requrie, for example, more group elements in the public key or antyhing like that  
<strong>\<ArticMine\></strong> My question relates to a possible attack by increasing the number of ring members where we are only measuring tx size  
<strong>\<suraeNoether\></strong> oh, if we made a decision like moving to these signatures, i would strongly recommend a fixed ring size, if that helps your thought process on the matter  
<strong>\<sarang\></strong> What would it take to allow \_either\_ signature type, depending on size, if the size were not fixed?  
<strong>\<suraeNoether\></strong> considering this as an option boils down to considering whether or not we are willing to commit to having large, slowish, but rather efficient (with respect to privacy) sigs  
<strong>\<sarang\></strong> just as a thought experiment  
<strong>\<suraeNoether\></strong> no idea  
<strong>\<sarang\></strong> OK  
<strong>\<ArticMine\></strong> Yes that would simplify the issue; however we could also add a weight parameter to increasing the number of ring members  
<strong>\<sarang\></strong> I'll be interested to actually look into this  
<strong>\<sarang\></strong> Moving forward for this month, what's everyone's priorities?  
<strong>\<suraeNoether\></strong> (i think in general keeping around multiple signature schemes is bad business)  
<strong>\<sarang\></strong> Mine are to finalize BPs and then move on to RTRS, while finishing up a few other writeups  
<strong>\<silur\></strong> @sarang it shouldn't take much effort in my opinion  
<strong>\<sarang\></strong> suraeNoether: sure, just a thought experiment  
<strong>\<silur\></strong> to support both  
<strong>\<suraeNoether\></strong> every time i need something to do for an afternoon, i look at the MRL roadmap  
<strong>\<sarang\></strong> I mean a bit longer-term  
<strong>\<sarang\></strong> to help long-range planning  
<strong>\<sarang\></strong> and help us complete things  
<strong>\<silur\></strong> as long as the implementation keeps it's orthogonal design it can be an opt-in  
<strong>\<sarang\></strong> it's easy to get sidetracked with fun new projects  
<strong>\<silur\></strong> temptation of math\!  
<strong>\<suraeNoether\></strong> other than my weird blockdag approach, which i'll be sharing with sarang eventually, and my poissongraphs simulations, and multisig + kosk setting stuff... actually, i'm pretty full up. :P  
<strong>\<sarang\></strong> Nice\!  
<strong>\<suraeNoether\></strong> and i'll talk about the blockdag stuff after the meeting in some more detail  
<strong>\<sarang\></strong> Yeah I'm interested  
<strong>\<sarang\></strong> dags are at the top of my "I wish I had more time to do this" list  
<strong>\<suraeNoether\></strong> it's not clever, which is my strongest argument in its favor  
<strong>\<sarang\></strong> being not clever often means "easier to prove"  
<strong>\<suraeNoether\></strong> yep, and more secure, and lots of other things  
<strong>\<sarang\></strong> suraeNoether: what do you intend to do with RTRS2 this month?  
<strong>\<sarang\></strong> If the op counts they provide make sense, I'd be interested in prototyping to help my understanding better  
<strong>\<suraeNoether\></strong> step 1: understand how it works  
<strong>\<sarang\></strong> ^  
<strong>\<suraeNoether\></strong> step 2: if it's like RTRS1, step 2 is "abandon the project."  
<strong>\<silur\></strong> T\_T  
<strong>\<silur\></strong> RIP silur :D  
<strong>\<sarang\></strong> lolol  
<strong>\<suraeNoether\></strong> i regret to inform yall but i'm guessing 1) this scheme is as good as it gets without pairings based crypto or a weird RLWE scheme or something, and 2) i still think it's too slow for a mandatory every-transaction sort of deployment and 3) i don't think it's worth deploying without the always-on protection of 64-member rings. maybe. i don't know.  
<strong>\<silur\></strong> we talked about an RLWE-generalization months ago  
<strong>\<silur\></strong> so more likely ruffing found that too  
<strong>\<sarang\></strong> Well, we can use this month to find out  
<strong>\<suraeNoether\></strong> i think the variability in ring sizes is... well, it's not the biggest vulnerability, right, but it's a vulnerability and it's super low-hanging fruit: we should be mandating ring sizes to avoid inter-signature linking  
<strong>\<suraeNoether\></strong> i love my cat, and you should love my cat too. i got nothing else to contribute to this meeting except CAT LOVE.  
<strong>\<sarang\></strong> My cat is sitting on my lap with his paw on the keyboard  
<strong>\<sarang\></strong> ready to jump in should he become necessary here  
<strong>\<sarang\></strong> hyc: any developments on asic resistance?  
<strong>\<sarang\></strong> I have not been following that stuff this past month  
<strong>\<sarang\></strong> (or anyone else involved in this)  
<strong>\<sarang\></strong> (please chime in)  
<strong>\<silur\></strong> my last info on that is that cuckoo-cycle doesn't work for some reason  
<strong>\<silur\></strong> last time I got into that, it was the best known stuff  
<strong>\<silur\></strong> \*sad\*  
<strong>\<suraeNoether\></strong> silur hyc has been working on a proof of random code project  
<strong>\<silur\></strong> VRF? \*-\*  
<strong>\<hyc\></strong> sorry was on another call  
<strong>\<suraeNoether\></strong> i suppose one could imagine it as a VRF. some random code is generated from a nonce, excecuted, the final state is hashed, and that's the nonce for the proof of work game. puts the burden not on hashing the final output for PoW, but in executing random code  
<strong>\<hyc\></strong> silur you can catch up here <https://www.reddit.com/r/Monero/comments/8bshrx/what\_we\_need\_to\_know\_about\_proof\_of\_work\_pow/>  
<strong>\<suraeNoether\></strong> hyc its ok we still love you  
<strong>\<hyc\></strong> my prototype is here github.com/hyc/randprog but already superseded by tevador's  
<strong>\<hyc\></strong> <https://github.com/tevador/RandomJS>  
<strong>\<silur\></strong> thanx hyc  
<strong>\<hyc\></strong> cuckoo-cycle breaks down because of some memory/time tradeoff  
<strong>\<suraeNoether\></strong> hyc when did tevador start working on that? haha  
<strong>\<hyc\></strong> e.g. double memory gives superlinear time acceleration  
<strong>\<silur\></strong> oh  
<strong>\<hyc\></strong> suraeNoether: shortly after I published PoC ;)  
<strong>\<silur\></strong> what about a VRF or rather VDF-based approach?  
<strong>\<hyc\></strong> VDF ? what are these acronyms  
<strong>\<silur\></strong> verifiable random/delay function  
<strong>\<hyc\></strong> I don't know of any good examples.  
<strong>\<silur\></strong> I have a DH and EC demo on VRF in a jupyter notebook I can upload it into the lab  
<strong>\<silur\></strong> repo  
<strong>\<hyc\></strong> cool  
<strong>\<hyc\></strong> Also, Wolf's colleagues have another variation on my idea, but tuned to GPUs  
<strong>\<silur\></strong> but it kind of sidetracks a lot from "asic-resistant pows" since it's not a pow  
<strong>\<hyc\></strong> <https://github.com/ifdefelse/ProgPOW>  
<strong>\<hyc\></strong> we had a good couple days' worth of email conversations leading into that one  
<strong>\<hyc\></strong> I'm disinclined to adopt it because I think it leaves CPUs out, and ignores the prevalence of smartphones in the userbase these days  
<strong>\<sarang\></strong> In the interest of time, are there any other updates before we officially close and continue discussion of these topics?  
<strong>\<sarang\></strong> I'll be giving a presentation in Portland in a couple of weeks on the importance of fungibility, so hopefully some good PR from that  
<strong>\<hyc\></strong> nice  
<strong>\<sarang\></strong> The usual disclosure that my travel/hotel are covered, so I'm not requesting any community funding for this  
<strong>\<sarang\></strong> I'll be glad to share the presentation here for comments  
<strong>\<sarang\></strong> OK, looks like the official topics list is exhausted, so I suppose we can officially adjourn and continue talking here  
<strong>\<sarang\></strong> keep up the good fight  
<strong>\<suraeNoether\></strong> \<3 cool  
<strong>\<sarang\></strong> I'd be glad to hear more from hyc or suraeNoether about PoW and/or fun DAG stuff  
<strong>\<suraeNoether\></strong> \</meeting\>
