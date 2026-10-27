---
title: Logs for the Monero Research Lab Meeting Held on 2018-10-08
summary: Surae work, Sarang work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Let’s begin\!  
<strong>\<suraeNoether\></strong> fluffypony knaccc luigi1111 luigiafk sarang andytoshi anonimal ArticMine binaryFate dEBRUYNE endogenic ErCiccione ferretinjapan gingeropolous gmaxwell hyc iDunk IsthmusCrypto john\_alan jwinterm kenshi84 kerber\_ medusa\_ moneromooo MoroccanMalinois naughtyfox needmoney90 oneiric\_ OhGodAGirl philkode pigeons rehrar rrol\[m\] sgp\_ smooth sneurlax stoffu unknownids vtnerd waxwing  
<strong>\<suraeNoether\></strong> meeting time\! woo\! i’ll get banned from freenode eventually by calling everyone’s name  
<strong>\<rehrar\></strong> just in time  
<strong>\<suraeNoether\></strong> So, greetings everyone  
<strong>\<rehrar\></strong> got back from the dentist  
<strong>\<suraeNoether\></strong> gross  
<strong>\<kovri-slack\> \<oneiric\></strong> hallo  
<strong>\<suraeNoether\></strong> did you bring snakes and butter  
<strong>\<sgp\_\></strong> hello  
<strong>\<rehrar\></strong> wat?  
<strong>\<laXity\></strong> Im just lurking  
<strong>\<suraeNoether\></strong> rehrar: adventure time reference, nothing to see here  
<strong>\<suraeNoether\></strong> okay, so today I want sarang and myself to discuss what we’re working on presently, and then i want to chat about the topics i mentioned before: 1) research, 2) conferences, 3) collaboration, 4) funding  
<strong>\<sarang\></strong> righto  
<strong>\<suraeNoether\></strong> 5) privacy/efficiency tradeoffs  
<strong>\<suraeNoether\></strong> before we begin, though  
<strong>\<suraeNoether\></strong> I like the idea that we employed last time where people can be free to ask questions before we begin  
<strong>\<suraeNoether\></strong> (i mean in general, you are free to ask questions)  
<strong>\<suraeNoether\></strong> but, before we start: who has questions in general for MRL?  
<strong>\<rehrar\></strong> When Monero scale?  
<strong>\<gingeropolous\></strong> when GUI?  
<strong>\<suraeNoether\></strong> how much does a piconero weigh  
<strong>\<sarang\></strong> when 0.13  
<strong>\<suraeNoether\></strong> oooh that’s a better question  
<strong>\<sarang\></strong> But anyway  
<strong>\<sarang\></strong> Shall I talk research?  
<strong>\<rehrar\></strong> yes  
<strong>\<suraeNoether\></strong> yep, fire away sarang  
<strong>\<sarang\></strong> Well, suraeNoether and I were sent a couple of draft papers from some researchers regarding spent outputs and blackballing  
<strong>\<sarang\></strong> There’s some formalization of the set theory that we already developed  
<strong>\<sarang\></strong> and some parts of the results that are presented in a way that is FUD-inducing  
<strong>\<sarang\></strong> “XX% of outputs are traceable\!\!\!\!1\!”  
<strong>\<suraeNoether\></strong> of course, 99% of those were announced in monerolink. :P  
<strong>\<sarang\></strong> So we worked through those, offered to work with the researchers, no word back from them except “we will look into it”  
<strong>\<suraeNoether\></strong> or 100\*(1-p) for some reasonably small p, i believe they managed to find an additional, … I think about a single day’s worth of transactions in total, from teh whole blockchain, iirc  
<strong>\<sarang\></strong> I’m working to get some updated blackball stats on our own to compare  
<strong>\<sarang\></strong> they have an O(N^2) method for identifying more outputs, but this is negligible as always  
<strong>\<sarang\></strong> At the very least, we’ll have up to date data to refute if they publish their work as-is  
<strong>\<sarang\></strong> Aside from that, suraeNoether and I have been continuing work on sublinear ring sigs for feasibility  
<strong>\<suraeNoether\></strong> they reinvented several wheels that we’ve worked on in the past 3 months here at MRL, which is actually a good thing, because it lends credence to our results to have some independent and similar results pop up  
<strong>\<rehrar\></strong> like RuffCT type stuff?  
<strong>\<sarang\></strong> yiss  
<strong>\<sarang\></strong> I have a shitty version of their clustering algo on my repo  
<strong>\<suraeNoether\></strong> well, RuPol. RuffCT was the first one we had presented to us (also by Ruffing et al, but with a different “et al”)  
<strong>\<suraeNoether\></strong> the clustering algorithm has to do with this blackball paper, not sublinear ring sigs  
<strong>\<sarang\></strong> yes  
<strong>\<sarang\></strong> As sgp\_ has mentioned before, forks and pools will be the BB things to focus on anyway  
<strong>\<rehrar\></strong> so is the new sublinear stuff looking more promising than the Ruff Stuff?  
<strong>\<sarang\></strong> unfortunately those are not verifiable by the user  
<strong>\<sarang\></strong> rehrar: unclear  
<strong>\<sarang\></strong> it’s clever but very complex  
<strong>\<suraeNoether\></strong> that’s what we are trying to figure out: it appears to be more efficient, asymptotically, but until we have a working implementation, it’s hard to tell  
<strong>\<rehrar\></strong> like me  
<strong>\<suraeNoether\></strong> yes  
<strong>\<sarang\></strong> heh  
<strong>\<sarang\></strong> There is a lot of math left out of the paper, so it’s a thing we’re working on in parallel to other things that come up  
<strong>\<rehrar\></strong> cool. Sounds lit.  
<strong>\<rehrar\></strong> \#litmaths  
<strong>\<suraeNoether\></strong> last week I split our MRL research roadmap into a sequence of separate github issues (\#30 and higher I believe) <https://github.com/monero-project/research-lab/issues>  
<strong>\<suraeNoether\></strong> nope, \#31 and higher  
<strong>\<suraeNoether\></strong> and I’ve spent a bit of time on my lightning-for-monero paper, but not nearly enough, as this RuPol thing is a nasty rabbit hole  
<strong>\<rehrar\></strong> is MRL going to transition to gitlab also?  
<strong>\<IsthmusCrypto\></strong> I’m at the SF Blockchain Week Epicenter today &amp; tomorrow on behalf of \#noncesense-research-lab — ping me if you’re around and want to meet up for coffee/drink/chat. I’ll be back with a million new ideas soon.  
<strong>\<sarang\></strong> rehrar: I have no big preference  
<strong>\<suraeNoether\></strong> rehrar: i have no control over the research-lab git, actually. :P  
<strong>\<suraeNoether\></strong> so if all workgroups migrate, we’ll presumably migrate too? \*shrug\*  
<strong>\<rehrar\></strong> also personal repos, but that can be after the meeting  
<strong>\<sgp\_\></strong> yeah sarang and I have been talking about blackball, and it’s my opinion that we need the public pool data working with the blackball tool to test for chain reactions before we proceed further  
<strong>\<equim\[m\]\></strong> I have a question. Would the blackball cause such kind of attack? Mallory knows an output belongs to Alice and wants to trace when it is spent. He makes N transactions with each of them exactly N ring members, and each of them contains Alice’s target output as decoy. If the blackball get in effects, then the next time the target output apears, it must be Alice’s real output.  
<strong>\<sarang\></strong> One conclusion sgp\_ and I share is that understanding the statistics can help guide best practices going forward  
<strong>\<sgp\_\></strong> if pool transactions are mostly unimportant, then we probably only need to use the blackball tool as an indicator of netowkr health. no one would use it typically  
<strong>\<sarang\></strong> equim\[m\]: the on-chain set theory stuff is for provably spent outs  
<strong>\<sarang\></strong> it’s not possible to “get caught” with that  
<strong>\<sarang\></strong> Mallory couldn’t make those signatures anyway  
<strong>\<sgp\_\></strong> if pool transactions ARE important, we need to bump ringsize, avoid coinbase decoys by default in wallet clients, or have everyone use a blackball list  
<strong>\<sgp\_\></strong> you can see our recommendations hinge on the importance of pool data  
<strong>\<sarang\></strong> option 1 is expensive, option 2 is possible (but could fingerprint), and option 3 is not verifiable  
<strong>\<sgp\_\></strong> (or at least mine do, I don’t mean to speak for sarang)  
<strong>\<suraeNoether\></strong> equim\[m\]: short answer is no, long answer requires more explanation, but primarily: the probability that allice \*happens\* to select all used up ring members is very low unless someone was flooding the network with transactions, and at that point, the attack is costly  
<strong>\<sarang\></strong> My opinion is that we need the data for this  
<strong>\<sarang\></strong> and moving toward getting that data is the first step  
<strong>\<suraeNoether\></strong> i think the blackball thing is a big red herring waste of time, and i’ve said this beforfe  
<strong>\<sarang\></strong> it is for set theory stuff  
<strong>\<sarang\></strong> for pools it is unclear until we have data to show one way or another  
<strong>\<suraeNoether\></strong> i think i’ve sketched out my argument about how, even in the next 10 years, it’s unlikely to impact even a single ring signature, so i’m still highly skeptical  
<strong>\<sarang\></strong> Hence getting pool chain rxn data  
<strong>\<sarang\></strong> then we can lay it to rest one way or the other  
<strong>\<suraeNoether\></strong> if the back of the napkin is that pessimistic, i think spending even an hour collecting data is wasting time, but i’ve said that before too  
<strong>\<suraeNoether\></strong> i disagree: this shit will never be laid to rest until people just admit that it has no practical impact  
<strong>\<nioc\></strong> AIUI mooo thinks it’s bad to include pool txs in the BB list  
<strong>\<suraeNoether\></strong> the EAE attack and ring sizes in general are far more fearsome  
<strong>\<suraeNoether\></strong> and far more worthy places for us to spend our limited time  
<strong>\<suraeNoether\></strong> nioc: do you recall moneromooo’s justificaiton for that?  
<strong>\<sarang\></strong> Not saying we should add them. Saying that we should see what effect they have so we can decide if/how to move forward  
<strong>\<suraeNoether\></strong> sgp\_: i heard a rumor that you had started including heuristically linked outputs in the blackball list, or outputs that aren’t necessarily \*provably\* spent. is that true?  
<strong>\<nioc\></strong> sarang: yes  
<strong>\<moneromooo\></strong> I don’t really like this. (1) they’re not proven spent, (2) it means it strips away non pool miners’ ring signaturity when they spend.  
<strong>\<suraeNoether\></strong> sarang: would you mind opening an issue up on the research-lab git on this topic so we can have a public discussion about it that is referrable later without combing through meeting logs?  
<strong>\<sarang\></strong> I’ll defer to sgp\_ since this is really his baby. I’m just an interested party who would like to know the results of the analysis  
<strong>\<sgp\_\></strong> moneromooo we can talk about the implications, but the effectiveness of these pool ring signatures is already 0  
<strong>\<suraeNoether\></strong> sgp\_ any word on my previous question?  
<strong>\<suraeNoether\></strong> re: blackball list and non-provably spent outputs?  
<strong>\<sgp\_\></strong> suraeNoether sneurlax’s tool looks at coinbase outputs and the sent transactions to see which outptus could have been spent in the transaction  
<strong>\<sarang\></strong> the current codebase’s bb tool will not do heuristics on its own  
<strong>\<sgp\_\></strong> I believe it’s a heuristic using data the pool provides, and it takes this data with the assumption it’s correct  
<strong>\<suraeNoether\></strong> so… \*yes\* the tool blackballs outputs that are not provably spent?  
<strong>\<sgp\_\></strong> so if a pool mis-reported, the tool would report different results  
<strong>\<sarang\></strong> sgp\_: he’s asking if your hosted list contains any non-proven  
<strong>\<sgp\_\></strong> the current tool that ships with Monero now does not  
<strong>\<suraeNoether\></strong> i strongly recommend against any blackballing for any outputs that are not provably spent  
<strong>\<sgp\_\></strong> right now, the site has 3 list categories  
<strong>\<equim\[m\]\></strong> So if everyone is using blackball, then one can easily make others mark a target output as spent (N transactions with N ring size) that is actually not spent?  
<strong>\<suraeNoether\></strong> it is critical that the blackball list be independently verifiable  
<strong>\<sgp\_\></strong> one for all chain data with chain splits, another with only rct data with chain splits, and a third separate category for pool data  
<strong>\<sarang\></strong> equim\[m\]: you cannot generate signatures that blackball another person’s output  
<strong>\<equim\[m\]\></strong> Yes that’s my point  
<strong>\<suraeNoether\></strong> equim\[m\] I’m not understanding your question  
<strong>\<suraeNoether\></strong> would you mind clarifying?  
<strong>\<sgp\_\></strong> a user could verify the first two by running XMR, XMO, XMV nodes locally  
<strong>\<equim\[m\]\></strong> Okay, I think I need to read up more first.  
<strong>\<sarang\></strong> equim\[m\]: if you generate N identical rings of N outputs with valid sigs, it means you controlled all N of them  
<strong>\<sgp\_\></strong> fwiw I don’t recommend a user should use a blackball list. I think we should use the findings of the blackball list to pursue other options to mitigate the data that would need to potentially be stored there  
<strong>\<moneromooo\></strong> equim\[m\]: you cannot make N rings with N outputs, one of which being not yours.  
<strong>\<equim\[m\]\></strong> Oh I got it, just missed that.  
<strong>\<equim\[m\]\></strong> rings need to be identical  
<strong>\<sgp\_\></strong> sneurlax’s tool essentially creates a list of outputs that the pool controls at any one given time, then sees if it can attribute these outputs to specific ring signatures  
<strong>\<sgp\_\></strong> I still think we need to table this discussion until we can test for possible chain reactions with pool data, which means updating the output format for sneurlax’s tool  
<strong>\<sarang\></strong> Yes, I think a useful action item is to get this data, run rxns, and compare to our base data to see what the effects might be  
<strong>\<sarang\></strong> just like it’s useful to have data on previous forks to better understand what, if any, risk is present  
<strong>\<sgp\_\></strong> yeah, and if the impact is small, we forget about it. if it’s large, we need to discuss options  
<strong>\<sarang\></strong> Yep, use the data to inform best practices  
<strong>\<sarang\></strong> So  
<strong>\<sarang\></strong> suraeNoether: any research to report in addition to what’s been discussed?  
<strong>\<suraeNoether\></strong> sorry, had to get the door  
<strong>\<suraeNoether\></strong> So, other than a modest amount of progress on my lightning paper, and workign with Sarang on this sublinear RuPol scheme, I have done a lot more administrative stuff this week  
<strong>\<suraeNoether\></strong> so i want to move onto a bit of that adminstrative crap regarding conferences  
<strong>\<suraeNoether\></strong> actually  
<strong>\<suraeNoether\></strong> collaboration is a bit more research themed  
<strong>\<suraeNoether\></strong> so, there is some good news and bad news on the collaboration/grant front  
<strong>\<suraeNoether\></strong> the short summary is this: after speaking with three separate univeristy research foundations on Friday  
<strong>\<suraeNoether\></strong> there simply is not a structure in place for universities to accept research funding from a crowdfunded animal like our own  
<strong>\<suraeNoether\></strong> this is both good news and bad news  
<strong>\<suraeNoether\></strong> the bad news is it’ll be six months at least, if not longer, before we can start interacting wtih universities in a way that requires funding  
<strong>\<suraeNoether\></strong> the good news is that all three of those universities are extremely eager to start working these things into their foundation’s policies  
<strong>\<suraeNoether\></strong> so, for example, the researcher Gao at Clemson: even if we wanted to, we couldn’t really offer any money (beyond bug bounties, etc) for their collaboration  
<strong>\<endogenic\></strong> is it really a good idea for MRL to be in the grant giving business? is there anything the FFS system could not accomplish for such candidates?  
<strong>\<rehrar\></strong> endogenic: being actually funded for one  
<strong>\<rehrar\></strong> ba dum tsh  
<strong>\<suraeNoether\></strong> this relieves a possible burden on the community; in the meantime, CURF (clemosn university research foundation) is going to start working (partly with me at MAGIC) doing research on how to start making this a thing, because everyone at these universities agree this is not going away any time soon  
<strong>\<sarang\></strong> I thought the Clemson group might be interested in non-funded collaboration  
<strong>\<sarang\></strong> thereby removing the burden from the community  
<strong>\<suraeNoether\></strong> and that’s the best news, is that they are  
<strong>\<sarang\></strong> and the PITA of funding  
<strong>\<endogenic\></strong> rehrar: why does everyone keep saying that  
<strong>\<suraeNoether\></strong> endogenic: the best jokes require explanation  
<strong>\<rehrar\></strong> cuz funding is taking a while for other stuff. It’s just cuz people are funded out after funding mooo, sarang, and suraeNoether  
<strong>\<suraeNoether\></strong> of course, providing some incentives for that research like travel funding,e tc, these things can be accomplished through the FFS, endogenic… kinda\! but not really… because every single university requires a cut of all such funding, and they refuse to accept such funding from a crowdfunded anon crowd style animal  
<strong>\<rehrar\></strong> admittedly, those are our greatest assets, but they require good amounts of Momos, so the other ones are struggling a bti atm  
<strong>\<rehrar\></strong> \*bit  
<strong>\<sarang\></strong> yep  
<strong>\<sarang\></strong> I think the correct avenue is non-funded collab  
<strong>\<suraeNoether\></strong> so the short answer is that right now, it doesn’t matter if it’s in MRL’s best interest to be a source of funding, because we literally can’t do it  
<strong>\<sarang\></strong> We already have university groups publishing on Monero  
<strong>\<suraeNoether\></strong> yep  
<strong>\<rehrar\></strong> I’m going to make it my personal mission to make Momos a thing for Monero in the same way bucks and paper is for dollars  
<strong>\<suraeNoether\></strong> all about the momos  
<strong>\<endogenic\></strong> i think.. it does matter.. because if it’s not in mrl’s interest then we don’t have to become nonprofit administrators with the ffs funding we have.  
<strong>\<suraeNoether\></strong> so, that actually puts a nail in a coffin that i very much wanted to either be nailed shut or aired out in the daylight, i was uncomfortable with whatever was inside banging on a loose lid  
<strong>\<suraeNoether\></strong> so to speak  
<strong>\<endogenic\></strong> “every single university requires a cut of all such funding, and they refuse to accept such funding from a crowdfunded anon crowd style animal” hmm  
<strong>\<endogenic\></strong> how about from individuals?  
<strong>\<suraeNoether\></strong> that’s a different animal  
<strong>\<endogenic\></strong> we just have individuals who are willing to deanonymize themselves say who they are  
<strong>\<suraeNoether\></strong> well  
<strong>\<endogenic\></strong> you can even feature ‘em  
<strong>\<suraeNoether\></strong> another option is, for example, OSTIF  
<strong>\<suraeNoether\></strong> but for now, adding this layer of grief I think is not worth it, even if there are interested parties who could throw their weight toward our project; MRL has other goals and priorities and we don’t want to spread ourselves too thin… and the answers I got from the foundations I spoke with are good enough reasons to abandon the idea for at least a few semesters  
<strong>\<sarang\></strong> Keep in mind that whoever is giving the grant is paying a lot extra for administration  
<strong>\<suraeNoether\></strong> 50% in fact  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> well, between 33% and 50% depending on the university  
<strong>\<sarang\></strong> researchers don’t see a dime of that  
<strong>\<suraeNoether\></strong> yep  
<strong>\<suraeNoether\></strong> heh  
<strong>\<suraeNoether\></strong> so, that’s going on a longer-term back burner  
<strong>\<suraeNoether\></strong> another thing I wanted to talk about is the Monero Konferenco  
<strong>\<sarang\></strong> So I agree with the sentiment that FFS shouldn’t fund university grants, but we should be receptive to helping good researchers apply for funding, and also keep collaborating for free with groups we know are interested  
<strong>\<suraeNoether\></strong> especially researchers who have contributed to the project already  
<strong>\<endogenic\></strong> sarang: if ffs proposals for grants had more trouble getting funded than those which didnt have admin fees attached then i think that could create a market to lower admin fees  
<strong>\<suraeNoether\></strong> endogenic: my experience, to be frank, is that almost any university will climb over their own grandmother, so to speak, for more funding, so you may not be wrong. however, these institutions are oftentimes very… slow… to… make… decisions… regarding new technology especially  
<strong>\<suraeNoether\></strong> but anyway, unless folks have questions, let’s move along to conference talk  
<strong>\<suraeNoether\></strong> re: the Monero Konferenco, I finally have all the quotes for costs that I need to post the funding request, and I want everyone’s advice on how to proceed  
<strong>\<rehrar\></strong> MoneroKon\!  
<strong>\<suraeNoether\></strong> long story short I’ve boiled down our possibilities to at least two, if not three possible locations, all that are roughly within the same range of price and amenities. However, one of those locations is the University of Colorado in Denver, which has some… interesting requirements… for the events held there. And there is a possiblity that they have to turn us down if we are not a “society” like SIAM or  
<strong>\<suraeNoether\></strong> AMS (for the same reason that grants can’t be accepted)  
<strong>\<suraeNoether\></strong> all that needs to happen there is one professor decide to “sponsor” the event, but then there are issues with a public university endorsing our little conference, and whether that is even allowed  
<strong>\<rehrar\></strong> so…probably best not to do it there then? Or is that the best of the bunch price-wise?  
<strong>\<suraeNoether\></strong> so, depending on my communications with them this week, it may simply not be possible to do it there. I’ve already gotten proposals from the Colorado Convention Center and the University of Denver, both of which have some sub-optimal properties  
<strong>\<suraeNoether\></strong> it’s not only the best of the bunch price-wise, I think, but also: you can take the lightrail from the airport to the location, which is embedded in the 16th street mall, which is a bit of a tourist location. lots of restaurants and hotels, etc  
<strong>\<suraeNoether\></strong> and there are bike share stations all around, etc  
<strong>\<endogenic\></strong> rehrar thinking about your previous mention of people being funded-out .. tbh we have a lot more funding sources than those who are aware of the ffs system but they cant donate monero because they dont have any. we need to open the funding platform to those who visit then drop off  
<strong>\<suraeNoether\></strong> this meeting is not about the FFS  
<strong>\<suraeNoether\></strong> and I would really like to move on  
<strong>\<suraeNoether\></strong> we are coming up on an hour already. :P  
<strong>\<suraeNoether\></strong> but i guess the meeting really IS about FFS  
<strong>\<endogenic\></strong> it’s my fault  
<strong>\<rehrar\></strong> so maybe THEY might not be able to market our event  
<strong>\<rehrar\></strong> but can WE do it?  
<strong>\<rehrar\></strong> is there a cryptocurrency club in that university?  
<strong>\<suraeNoether\></strong> oh, marketing is totally aside; the issue is that by sponsoring the event (which they require for the event to be held on their campus) is an implicit endorsement BUT THAT’S A REALLY GOOD QUESTION REHRAR\!  
<strong>\<sgp\_\></strong> +1 rehrar  
<strong>\<suraeNoether\></strong> i know that three professors there are currently chatting with each other about this to decide how to approach the topic  
<strong>\<suraeNoether\></strong> they haven’t contacted me directly yet, though, and I will email the chair of their department back  
<strong>\<suraeNoether\></strong> however, locations aside: we have numbers for funding requests, and I want folks’ advice on moving forward for this  
<strong>\<rehrar\></strong> My honest opinion is, if this can be hammered out relatively quickly, then let’s try for there. If not, then we should find another place. The truth is so much depends on the venue that it’s super hard, if not impossible in some areas, to plan further without knowing the venue  
<strong>\<suraeNoether\></strong> I feel like having more than one funding round would be wise, where we can cash out as we go. this could prevent something like asking for the single big chunk all at once and then failign to fund the entire thing, even though we could still throw a kcikass event for 80% of funding, or even 60%, as long as we plan around it  
<strong>\<suraeNoether\></strong> has that sort of thing been done through the Monero FFS yet?  
<strong>\<suraeNoether\></strong> also, if we can get a sponsorship, say from Cake Wallet or Tari or something like that, over-funding could be returned to the community through the general fund or whatever  
<strong>\<sarang\></strong> what is the amount of the “big chunk”  
<strong>\<rehrar\></strong> I 100% support those terms  
<strong>\<rehrar\></strong> The idea that you ask for 100% of what is needed, and then ask for sponsors after.  
<strong>\<rehrar\></strong> And specify in the FFS that any extra funding will be kept for next year’s conference  
<strong>\<rehrar\></strong> there is no guarantee of sponsors  
<strong>\<gingeropolous\></strong> this may or may not have been thought of or talked about above, but if MRL can’t do university stuff because its a total PITA etc, one resource that could be created is a research facilitator  
<strong>\<rehrar\></strong> that’s just my opinion though  
<strong>\<suraeNoether\></strong> my initial numbers were 54,150 USD to 72,900 USD, but i was assuming wedding-level costs of a venue. with our newest numbers, the cost will be closer to 52k USD to 59k USD  
<strong>\<gingeropolous\></strong> i.e., if there’s a researcher at a university who wants to do monero research, we can provide grant templates or boilerplate crap or letters of support  
<strong>\<rehrar\></strong> I’m not sure how wise several funding rounds is though  
<strong>\<gingeropolous\></strong> for the university researchers grant application etc  
<strong>\<suraeNoether\></strong> gingeropolous: that’s a very interesting idea that we can start looking at over the next few months  
<strong>\<rehrar\></strong> depending on how quickly it moves through the system and gets funded each time, it might be too long to get stuff done  
<strong>\<sarang\></strong> I still think we need to do a better job of reaching out to groups that have already done Monero research  
<strong>\<gingeropolous\></strong> yeah, it shouldn’t hit any beaurocratic nightmare hurdles  
<strong>\<suraeNoether\></strong> rehrar: that’s a fair point  
<strong>\<rehrar\></strong> I think make an FFS for 65k  
<strong>\<gingeropolous\></strong> bureaucratic  
<strong>\<rehrar\></strong> roughly 10% of wiggle room there for price movements  
<strong>\<suraeNoether\></strong> okay, and we can make it clear that excess funding will be used for next year’s conference  
<strong>\<suraeNoether\></strong> now, for transparency reasons  
<strong>\<suraeNoether\></strong> I’ll be throwing this conference, contacting speakers, hiring the conference coordinator, etc  
<strong>\<suraeNoether\></strong> the coordinator will be taking care of most of the grunt work  
<strong>\<rehrar\></strong> I’m down to help in whatever capacity (management, coordination, or otherwise) that you need me for  
<strong>\<rehrar\></strong> as well as design, obviously  
<strong>\<suraeNoether\></strong> in order to avoid liability, I’ve started an LLC called colorado crypto conferences LLC, so that I can distribute funds to organizers, venues, etc, without it coming out of my personal bank accounts, etc  
<strong>\<suraeNoether\></strong> thanks for volunteering for this rehrar\!  
<strong>\<suraeNoether\></strong> we’ll definitely take you up on that. I wouldn’t mind having t-shirts or shwag bags  
<strong>\<suraeNoether\></strong> so, does anyone object to me opening an FFS for 65kUSD for this? I can post 100% of all bookkeeping information for CCCLLC for transparency  
<strong>\<suraeNoether\></strong> and comply with any other wishes the community has for transparency  
<strong>\<rehrar\></strong> start there, and get feedback. I think it should be more than fine. :)  
<strong>\<kovri-slack\> \<oneiric\></strong> sounds like a great idea, +1  
<strong>\<suraeNoether\></strong> fantastic  
<strong>\<sarang\></strong> How much does the coordinator get paid?  
<strong>\<sarang\></strong> (due to the conflict of interest there)  
<strong>\<suraeNoether\></strong> 9000 USD. Approximately 100 man-hours of work. Justification: Typical per-hour fees for event organization at a firm are between 125-250 USD per hour. The project organizer is low-balling herself for this cost specifically because she is related to me. Around 10 of these hours she anticipates can be spent seeking out sponsors for the conference to mitigate our costs, as well.  
<strong>\<suraeNoether\></strong> she just finished organizing a conference for Johnson and Johnson and she received over 20 for the same amount of time and work she expects for this.  
<strong>\<rehrar\></strong> I think all that is needed for this justification is quotes from a couple other people of the same job  
<strong>\<endogenic\></strong> ^ that doesnt work  
<strong>\<rehrar\></strong> no?  
<strong>\<endogenic\></strong> at least not without showing their work will turn out just as well  
<strong>\<endogenic\></strong> yup  
<strong>\<endogenic\></strong> i say leave it to the community to ask  
<strong>\<rehrar\></strong> ok  
<strong>\<suraeNoether\></strong> it’s not a complete look, but it’s fairly standard to find 3-4 quotes from several parties as an investigation into “fair market value” and then select from there  
<strong>\<endogenic\></strong> of course  
<strong>\<endogenic\></strong> not sure why youre on the hook to justify it though if youve done your research and are doing something for the community  
<strong>\<endogenic\></strong> it’s an easy thing to find a quote for  
<strong>\<sarang\></strong> I’ll have a couple of quick unrelated blackball stats when we’re finished up here  
<strong>\<sarang\></strong> endogenic: I think it’s ethically important because he’s related to the organizer he currently plans to hire  
<strong>\<endogenic\></strong> how does showing quotes ameliorate that? :P  
<strong>\<suraeNoether\></strong> endogenic: it’s a good faith thing  
<strong>\<sarang\></strong> yeah  
<strong>\<endogenic\></strong> you’re not recommending her rate imo  
<strong>\<suraeNoether\></strong> i’m not, she selected her rate  
<strong>\<rehrar\></strong> this is true, endogenic.  
<strong>\<rehrar\></strong> And if another coordinator wants to come in, prove their past work, and undercut, nothing is stopping them.  
<strong>\<rehrar\></strong> but onus on them  
<strong>\<suraeNoether\></strong> the fact is: it’s a very easy thing to temper any appearance of impropriety, and so we should  
<strong>\<sarang\></strong> suraeNoether: what does the total estimate assume about entry fees?  
<strong>\<suraeNoether\></strong> I assumed nothing about fees.  
<strong>\<suraeNoether\></strong> here is the section I was going to include on that.  
<strong>\<sarang\></strong> Cool, so it assumes people show up fo free?  
<strong>\<suraeNoether\></strong> \*Registration fees.\* Charging attendees is optional here and we should discuss the benefits (free and open access to Monero conferences is something we value?) and the costs (random crazy people and ICO shillsters will almost certainly walk in off the street\!). It’s worth pointing out that the event will \*not\* pay for itself unless we charge more than 1000 USD per ticket and we have full attendance.  
<strong>\<suraeNoether\></strong> currently looking at 50-70 attendees, so charging, say, 40 bucks for entry would only partially mitigate our total costs  
<strong>\<sarang\></strong> Does the LLC’s tax burden come into play with any of this?  
<strong>\<rehrar\></strong> We can discuss what it would look like to charge a small amount to partially mitigate costs, and give tickets for free to anyone who asks nicely.:D  
<strong>\<suraeNoether\></strong> sarang: if the LLC makes any profit, it passes through to me and i pay personal taxes on it; my goal is to save a bit of cash for next year’s conference, extract taxes from that part set aside, and then ensure that the remainder is spent on expenses for this year, so that i personally never feel any burden or liability from this.  
<strong>\<nioc\></strong> you will get more than 50-70 attendees and there should be some cost for them  
<strong>\<sarang\></strong> OK, so charging entry fees doesn’t mess with that  
<strong>\<suraeNoether\></strong> nioc not if i only sell 70 tickets :)  
<strong>\<suraeNoether\></strong> sarang correct  
<strong>\<sarang\></strong> got it  
<strong>\<suraeNoether\></strong> all my venue costs look at around 600-650 a day, but are based on no more than 150 people  
<strong>\<sarang\></strong> how many days?  
<strong>\<rehrar\></strong> are we only planning for 50-70 because that’s the sizes of the veue  
<strong>\<suraeNoether\></strong> 1.5  
<strong>\<rehrar\></strong> \*venue  
<strong>\<sarang\></strong> Will there be a story about the afterparty on mashable?  
<strong>\<suraeNoether\></strong> 50-70 for measuring interest the first year, and to keep the topics and audience in the technical, rather than ICO/business end… also because it’s easier to scale a small event up than throw a big event htat no one shows up to… not to mention, fluffypony has discussed with me throwing a monero conference preceding the magical crypto friends conference he is planning in NY, and I \*imagine\* that’s going to  
<strong>\<suraeNoether\></strong> be a larger scale event.  
<strong>\<suraeNoether\></strong> most of these universities have so much room for events like these we can scale up relatively easily without paying \*too much\* more  
<strong>\<rehrar\></strong> interesting  
<strong>\<rehrar\></strong> if we get flooded with people, we can see about just purchasing a bit more space? :D  
<strong>\<rehrar\></strong> anyways, let’s do what you’ve planned. See how it goes.  
<strong>\<suraeNoether\></strong> especially at a university, yes  
<strong>\<suraeNoether\></strong> but we would need several months lead time on estimates of crowd sizes  
<strong>\<suraeNoether\></strong> okay, rehrar’s opinion is good enough for me  
<strong>\<suraeNoether\></strong> :D  
<strong>\<suraeNoether\></strong> okay, any last questions before I pivot to a controversial opinion I’m strongly interested in peddling on everyone here?  
<strong>\<sarang\></strong> Sure, but let’s speedy things up  
<strong>\<sarang\></strong> we’re way over  
<strong>\<rehrar\></strong> no questions, give opinion  
<strong>\<suraeNoether\></strong> okay, the main thing is this: we have a responsibility to our users. they use our currency in some cases to protect their own livelihoods from tyrannical etc etc  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> in some cases, monero is a matter of life and death  
<strong>\<suraeNoether\></strong> due to this, I believe we need to start shifting our attitude about development at Monero away from efficiency and towards security  
<strong>\<suraeNoether\></strong> and due to this, I believe we should move to a fixed but large ring size, like 45.  
<strong>\<sarang\></strong> Do we have data to back up such a choice?  
<strong>\<sarang\></strong> I believe our job is to provide users the best efficiency for what we see as reasonable and necessary security/privacy  
<strong>\<suraeNoether\></strong> if it turns out that, in 6 months time, a more efficient scheme comes along, then we would see a drop in our sizes and verification times, similar to our bulletproof thing, which is a PR win for us, and in the meantime, we would be taking the cautious route.  
<strong>\<suraeNoether\></strong> short answer to that sarang is: kinda  
<strong>\<sarang\></strong> If users who need us can’t join the network reasonably, we’ve failed them  
<strong>\<suraeNoether\></strong> yes, if we go too large, network security is compromised by new nodes choosing other coins  
<strong>\<sarang\></strong> “The chain is now 400 GB” is a bad statement to give them  
<strong>\<sarang\></strong> I think this hearkens back to the need for a better understanding of threat models  
<strong>\<suraeNoether\></strong> so we are stuck between a rock (loose security with efficiency and speed, lots of network security but weaker untraceability claims) vs. a hard place (tight secuirty for a coin that no one uses properly, a la pre-sapling zcash)  
<strong>\<sarang\></strong> If ring size is made less relevant by a better understanding of, e.g. churn and controlled spends under certain threat models, that’s good data  
<strong>\<suraeNoether\></strong> yeah, but what about users who don’t churn?  
<strong>\<sarang\></strong> That’s the need for understanding our threat models better  
<strong>\<rehrar\></strong> churning is an active choice to protect yourself  
<strong>\<gingeropolous\></strong> i like the idea of shifting focus towards security… but that seems to go hand-in-hand with efficiency.  
<strong>\<rehrar\></strong> every step you make a user take for themselves, you will see significant drop off in people who do it  
<strong>\<gingeropolous\></strong> then again, monero (the entity) didn’t give two shits about efficiency when it went to RingCT  
<strong>\<sarang\></strong> What I mean is that if we can establish that a large ring increase has measurable benefits for users under reasonable threat models, that’s a conversation worth having  
<strong>\<suraeNoether\></strong> actually gingeropolous that is one of hte best points: we added these huge slow range proofs without hesitation, and then we had a big PR win for making them more efficient.  
<strong>\<suraeNoether\></strong> we should just assume the following threat model: anyone we transact with is transacting with an AML/KYC exchange, who can be assumed to have godlike, state-level computational power because a government serving them a warrant leads to that  
<strong>\<sarang\></strong> There was a big benefit to CT… can we point to such a benefit with a large increase?  
<strong>\<suraeNoether\></strong> now, if you are pinned, EAE style, between two adversaries, ain’t no ring size that will help  
<strong>\<suraeNoether\></strong> so the only reasonable threat model we can really work with is EBABE where you may not be transacting directly with AML/KYC but people on either side of you are  
<strong>\<rehrar\></strong> I think the assumption of EABE for current standard use is not unfounded  
<strong>\<suraeNoether\></strong> ^ bingo  
<strong>\<rehrar\></strong> and I think a threat model of EABE is probably the one to operate under  
<strong>\<rehrar\></strong> BUT  
<strong>\<rehrar\></strong> since we cannot see Monero’s stuff  
<strong>\<rehrar\></strong> we should analyze how people use altcoins  
<strong>\<rehrar\></strong> like Litecoin or Dash  
<strong>\<rehrar\></strong> see if it tends to go EABE  
<strong>\<nioc\></strong> wownero just forked and their static ringsize is now 22. Don’t know if they will have any stats that would be of interest to “us”  
<strong>\<rehrar\></strong> and extrapolate from that to Monero  
<strong>\<kovri-slack\> \<oneiric\></strong> what do EAE and EABE stand for?  
<strong>\<sarang\></strong> That use could be waaaay different  
<strong>\<rehrar\></strong> sarang: we do the same for sending patterns and selecting ring members though  
<strong>\<sarang\></strong> Eve-Alice-Eve and Eve-Alice-Bob-Eve  
<strong>\<suraeNoether\></strong> oneiric\_: EAE is “eve-alice-eve” where eve is an evil exchange and you are alice. other non-E letters are other users who may or may not be malicious  
<strong>\<sarang\></strong> rehrar: we have some Monero data for that too  
<strong>\<rehrar\></strong> ok  
<strong>\<sarang\></strong> based on deduced spends  
<strong>\<kovri-slack\> \<oneiric\></strong> ok, thanks sarang and suraeNoether  
<strong>\<sarang\></strong> but something like exchange interaction might be way different for a private coin  
<strong>\<suraeNoether\></strong> so sarang keeps asking “can we point to a benefit” and the answer is “we can point to a point at which ring size increases are no longer helpful, which is around 45, and we can point to some weak results on, say, how many transaction histories exist.” for example, I just found a theorem that proves that there must be twice as many transaction histories as their are output keys, but finding all of them is  
<strong>\<suraeNoether\></strong> progressively harder and harder as ring sizes increase  
<strong>\<sarang\></strong> OK, let’s formalize this, determine how exchange interactions affect it (to the extent that we can), and then go from there  
<strong>\<rehrar\></strong> ^  
<strong>\<sarang\></strong> The question of formalization and hard numbers always comes up when this gets discussed  
<strong>\<rehrar\></strong> see the mathz  
<strong>\<sarang\></strong> but it hasn’t happened yet  
<strong>\<suraeNoether\></strong> okay; i’m not trying to convince people today, i just want our community to start thinking about the formalization components of this and longer-term thinking for the safety of our users  
<strong>\<sarang\></strong> This has been on our radar for a long time  
<strong>\<sarang\></strong> Until we have the math for it, I think it’s a very hard sell  
<strong>\<rehrar\></strong> perhaps one of you community paid MRL researchers should get this formalization done ;)  
<strong>\<sarang\></strong> ikr  
<strong>\<suraeNoether\></strong> that’s one of my in-prep papers  
<strong>\<sarang\></strong> suraeNoether: it was my understanding that you already had informal versions of this  
<strong>\<suraeNoether\></strong> ^  
<strong>\<sarang\></strong> I think it should be a priority  
<strong>\<suraeNoether\></strong> yeah, that’s where my priorities are shifting, but that also includes looking at the sublinear papers  
<strong>\<suraeNoether\></strong> because if they are sufficiently efficient (heh) we don’t actually even have an argument, y’know?  
<strong>\<sarang\></strong> Yeah, they go hand-in-hand  
<strong>\<rehrar\></strong> the sublinear papers are for increasing efficiency of larger ringsizes though, correct?  
<strong>\<sarang\></strong> But I consider this more important than, say, lightning and cross-chain stuff  
<strong>\<sarang\></strong> rehrar: size efficiency, yes  
<strong>\<rehrar\></strong> I understand they go together, but I think priority should be on establishing usage patterns to establish a threat model  
<strong>\<sarang\></strong> agreed  
<strong>\<rehrar\></strong> I believe Monero has been operating for a dangerously long time without a specified threat model  
<strong>\<sarang\></strong> Well, and our ring increases have to some extent been based on “bigger is better”  
<strong>\<sarang\></strong> we’re long past the point of chain reaction style threats  
<strong>\<rehrar\></strong> and so, while efficiencies to ring sizes are good, I think the establishment of the threat model is imperative to all future research in this area  
<strong>\<sarang\></strong> (exactly 5 post-CT outputs are blackball-worthy from on-chain analysis)  
<strong>\<rehrar\></strong> as a community member, I would propose that both sarang and suraeNoether work together on hammering out this formalization before further work proceeds  
<strong>\<rehrar\></strong> this will further legitimize Monero in the privacy/security industry.  
<strong>\<gingeropolous\></strong> i mean we could just go to 45, and then let optimization take its natural course  
<strong>\<rehrar\></strong> At the moment, I can see the criticisms from other people that see the lack of a defined threat model as proof that we are flying by the seat of our pants  
<strong>\<gingeropolous\></strong> ala RingCT  
<strong>\<suraeNoether\></strong> my primary concern is that repeated analyses of a system that uses small anonymity set sizes (sub-millions) can be very powerful in reducing effective anonymity set sizes, regardless of the threat model  
<strong>\<sarang\></strong> We could also require users to use a different burner laptop from a different IP for every transaction, but that doesn’t mean it’s necessarily helpful  
<strong>\<rehrar\></strong> gingeropolous: doesn’t solve the problem of threat modeling and formalization. and Monero is better than that  
<strong>\<suraeNoether\></strong> and the “sub-millions” thing is essentially a non-starter for obvious reasons  
<strong>\<gingeropolous\></strong> “who needs action when you’ve got words”  
<strong>\<suraeNoether\></strong> heh  
<strong>\<rehrar\></strong> who needs either when you have math  
<strong>\<rehrar\></strong> which guides the action and discussion  
<strong>\<sarang\></strong> A good start will be formalizing the ring size informal stuff, hammering out churn wait times as a heuristic killer, and going from there, perhaps?  
<strong>\<rehrar\></strong> right now we have not the math  
<strong>\<rehrar\></strong> yes ^  
<strong>\<rehrar\></strong> for me, as a recommendation from a community member, this is priority number 1  
<strong>\<rehrar\></strong> can’t speak for others obviously  
<strong>\<sarang\></strong> I think it answers “how can we use Monero safely right now” so we can move to “how can we make Monero better for tomorrow”  
<strong>\<suraeNoether\></strong> okay, I’m going to formalize a single-hop (EABE) and double-hop (EBABE) pair of threat models, write up my formal definition of fungibility, demonstrate it implies anonymity, show that neither zcash nor monero satisfy my definition of fungibility, demonstrate a churn model that brings us closer to fungibility, and i’ll share that document with the community. that will be my top priority this week  
<strong>\<rehrar\></strong> thank you suraeNoether  
<strong>\<sarang\></strong> baller  
<strong>\<rehrar\></strong> from a research perspective  
<strong>\<suraeNoether\></strong> also, can we change the term “blackball” to “marked notes?” :P  
<strong>\<sarang\></strong> This doesn’t even need to be journal-worthy  
<strong>\<rehrar\></strong> to me, this is even bigger than BPs  
<strong>\<rehrar\></strong> and will be the biggest thign to come out of MRL this year  
<strong>\<sarang\></strong> but we need a base for our recommendations  
<strong>\<kovri-slack\> \<oneiric\></strong> serious win  
<strong>\<sarang\></strong> Let’s collaborate as much as is useful, suraeNoether  
<strong>\<scoobybejesus\></strong> i’m sure the formalization will pretty much write itself… /s  
<strong>\<suraeNoether\></strong> allright, before we end the meeting: any final questions, comments, concerns? I need to write my summary of my september work and post it, so I apologize to the community for my delay (again)  
<strong>\<sarang\></strong> I ran some new blackball stats to compare to our author friends  
<strong>\<rehrar\></strong> nope. Great meeting. Gotta split. Bai.  
<strong>\<sarang\></strong> Finding their results are comparable to ours  
<strong>\<sarang\></strong> Importantly, our analysis methods show exactly 5 post-CT outputs are bad  
<strong>\<sarang\></strong> whereas about 68% of pre-CT outputs are bad  
<strong>\<suraeNoether\></strong> good to know :D  
<strong>\<sarang\></strong> this accounts only for on-chain stuff (no forks, pools, etc)  
<strong>\<sarang\></strong> I’m going to add this to our tech note to shut people up about “OMG OUTPUTS ARE TRACED”  
<strong>\<gingeropolous\></strong> yeah 5 of them\!  
<strong>\<sarang\></strong> modern transactions are not vulnerable to this crap  
<strong>\<gingeropolous\></strong> and like all of pre-ct  
<strong>\<suraeNoether\></strong> on a totally different note, i’m in a weird funding trap because I was an idiot earlier this year, and I don’t have funding for december. sarang and I were going to request funding for Jan-March simultaneously: do you guys think I should ask for Dec-March or should I request december separately, or what? I tried to get back on the quarter system earlier this year and then idiotically got back off it again. :\\  
<strong>\<rehrar\></strong> just do four months  
<strong>\<rehrar\></strong> now I really gotta split  
<strong>\<sarang\></strong> bai  
<strong>\<suraeNoether\></strong> ok \<3 rehrar
