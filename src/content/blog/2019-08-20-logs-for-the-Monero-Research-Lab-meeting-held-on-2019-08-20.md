---
title: Logs for the Monero Research Lab Meeting Held on 2019-08-20
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> OK, let's get started with our meeting  
<strong>\<sarang\></strong> Agenda here: <https://github.com/monero-project/meta/issues/383>  
<strong>\<sarang\></strong> Logs posted there afterward  
<strong>\<sarang\></strong> GREETINGS  
<strong>\<sarang\></strong> hello  
<strong>\<suraeNoether\></strong> howdy  
<strong>\<gingeropolous\></strong> heya  
<strong>\<sarang\></strong> It's been two weeks since the last meeting... plenty to discuss\!  
<strong>\<sarang\></strong> In the spirit of fairness and teamwork, I'll go first :D  
<strong>\<sarang\></strong> The DEF CON village, despite having a poor location, was well attended  
<strong>\<sarang\></strong> I did a talk, a workshop, a CTF, and a panel discussion  
<strong>\<suraeNoether\></strong> how did the attendance compare to last year?  
<strong>\<sarang\></strong> I would estimate higher  
<strong>\<suraeNoether\></strong> nice\!  
<strong>\<sarang\></strong> I've written up a brief spacetime analysis of Omniring in its current form: <https://github.com/SarangNoether/skunkworks/blob/sublinear/omniring.md>  
<strong>\<sarang\></strong> It does not presently support batching, but the authors have a couple of ideas on how to do so safely that are forthcoming  
<strong>\<sarang\></strong> I'll be discussing with them this week  
<strong>\<sarang\></strong> On a related note, the RCT3 construction has a flaw that would be exploitable in practice  
<strong>\<sarang\></strong> The authors of that paper, I'm told, also have a fix forthcoming that may relate to the Omniring batching enhancement  
<strong>\<sarang\></strong> Made a quick PR to fix a bias in Schnorr signatures: <https://github.com/monero-project/monero/pull/5807>  
<strong>\<endogenic\></strong> o/  
<strong>\<sarang\></strong> Cleaned up an MLSAG improvement PR: <https://github.com/monero-project/monero/pull/5707>  
<strong>\<sarang\></strong> Made some updates to Zero to Monero (see topic branches): <https://github.com/SarangNoether/zero-to-monero/>  
<strong>\<sarang\></strong> And I'm working on getting CLSAG and thring sigs submitted to conference proceedings (a tiresome and lengthy process)  
<strong>\<sarang\></strong> That's my two cents  
<strong>\<endogenic\></strong> damn, son  
<strong>\<suraeNoether\></strong> yeah, that was a damn mic drop brother  
<strong>\<sarang\></strong> Anything to share with the class, suraeNoether ?  
<strong>\<suraeNoether\></strong> as for me, I've been on vacation and just got back. I'm still going to be only half-on today because I have some personal business I have to attend. it was an eventful vacation. for one thing, I was able to prove a few theorems for my graph matching paper that are necessary for publication. based on a conversation I had with sgp\_ right before I left, I spent a lot of time thinking about experimental  
<strong>\<suraeNoether\></strong> design, and I'm starting to discuss this with sarang.  
<strong>\<suraeNoether\></strong> in addition to that, I was contacted by Astral, the team working on bullet-proof monero-mining drones, re: an unfortunately urgent funding matter.  
<strong>\<luigi1111w\></strong> sarang what happened to reusing existing functions or adding it as a function instead of inline?  
<strong>\<luigi1111w\></strong> not that it matters that much I guess  
<strong>\<sarang\></strong> There were some silly issues with includes and having access to the right underlying functions  
<strong>\<sarang\></strong> It seemed simpler to do it as is  
<strong>\<suraeNoether\></strong> i would urge folks in the audience to watch OhGodAGirl\_\_'s talk from teh Konferenco here (<https://www.youtube.com/watch?v=jDSKIr5EPiU> ) or Leah's interview wiht monerotalk <https://www.youtube.com/watch?v=jl1w6VDEWq4> to refresh themselves on the project  
<strong>\<endogenic\></strong> meaning they need funding?  
<strong>\<suraeNoether\></strong> if anyone is interested in assisting Astral in composing a CCS, I've been pinging some ideas back and forth with Leah  
<strong>\<suraeNoether\></strong> yes, and some of the funding needs are rather urgent; I spoke with OhGodAGirl\_\_ and OpenSourceress about this in person at the Konferenco and we have been kicking some ideas around  
<strong>\<suraeNoether\></strong> i anticipate a vigorous discussion on the matter, because the community funding sources, in my mind, should be a source of funding of last resort  
<strong>\<suraeNoether\></strong> the folks who contribute to the monero community are people who care about privacy and they want to see the project advance in a healthy direction, and without them, all of this falls apart  
<strong>\<sarang\></strong> Probably a good discussion for -community?  
<strong>\<sarang\></strong> Unless there's a technical/research component to it?  
<strong>\<suraeNoether\></strong> well, it's a nascent funding request for a hardware project with a timeliness component that recently presented at our conference, but going into further detail during the meeting is certainly unnecessary  
<strong>\<sarang\></strong> got it  
<strong>\<suraeNoether\></strong> and full disclosure: i am not yet in any way financially linked with Astral, although that may eventually change  
<strong>\<suraeNoether\></strong> i.e. this isn't for me  
<strong>\<sarang\></strong> Anyone else wish to share research work of interest?  
<strong>\<sarang\></strong> I'm excited to take a look at the current state of the matching simulations suraeNoether  
<strong>\<suraeNoether\></strong> that's all I have for the round table this week, but I'll also be playing catch-up on the lelantus vs. omni vs. rct3 cage match that's been going on these past few weeks  
<strong>\<gingeropolous\></strong> may eventually change? hamster.gif  
<strong>\<sarang\></strong> OK, so after the brief ROUNDTABLE is GENERAL QUESTIONS... anyone?  
<strong>\<sarang\></strong> I have a general question  
<strong>\<suraeNoether\></strong> i have one, too  
<strong>\<sarang\></strong> The proceedings/journals under consideration for CLSAG (thanks also to some outside advice) are Financial Cryptography, PETS, ACM TOPS, and ANCS  
<strong>\<sarang\></strong> Any other suggestions that I may have missed, that could be in scope?  
<strong>\<sarang\></strong> It's tough in the CLSAG case since it's an improvement over earlier work, but not earth-shattering  
<strong>\<sarang\></strong> and that always seems to be a tricky place to be in the publishing world  
<strong>\<sarang\></strong> I plan to highlight the improvements and generalize it a bit for submission  
<strong>\<suraeNoether\></strong> are you strictly considering conference proceedings or are you open to journal-only suggestions?  
<strong>\<sarang\></strong> Journals are fine too (ACM TOPS, e.g.)  
<strong>\<sarang\></strong> But since submissions are typically one-at-a-time, there's no real rush to add to the list  
<strong>\<sarang\></strong> But obviously prioritizing is useful to avoid submitting for delayed rejections  
<strong>\<suraeNoether\></strong> fair enough. I thought ACM TOPS was a conference, silly me. :P  
<strong>\<sarang\></strong> Anyway, that's my question  
<strong>\<sarang\></strong> suraeNoether: yours?  
<strong>\<suraeNoether\></strong> some of the biggest improvements that have come out of MRL this year have involved efficiency improvements, ranging from bulletproofs optimizations to compressed signature schemes. Only some of these improvements will carry on to the "next version" of monero, especially if we end up having to migrate our transaction model to something like one of the Big Three...  
<strong>\<dEBRUYNE\></strong> suraeNoether: Don't they have other options than to tend to the CSS?  
<strong>\<dEBRUYNE\></strong> I genuinely think this is not appropriate for it  
<strong>\<suraeNoether\></strong> so my question is: what sort of improvements would you like to see from the Monero Research Lab in the next year, keeping in mind that we will want to migrate to a different scheme sooner or later?  
<strong>\<suraeNoether\></strong> dEBRUYNE: i'll start a conversation about this over in -community  
<strong>\<rehrar\></strong> I would definitely like some research into ring sig alternatives.  
<strong>\<sarang\></strong> That's very much in progress rehrar  
<strong>\<suraeNoether\></strong> do you mean ring confidential transactions?  
<strong>\<rehrar\></strong> from the ground plebs, we're never quite sure how much progress and when and why and stuff  
<strong>\<suraeNoether\></strong> because lelantus, omni, and rct3 are each replacements for ring sigs  
<strong>\<suraeNoether\></strong> in a certain sense  
<strong>\<suraeNoether\></strong> but they are still ring confidential transaction schemes  
<strong>\<sarang\></strong> Yeah, my analyses try to give a reasonable spacetime estimate for those protocols  
<strong>\<rehrar\></strong> I wonder if a bimonthly MRL bulletin would be helpful to the masses  
<strong>\<rehrar\></strong> or a monthly one  
<strong>\<rehrar\></strong> I can assist in getting it out  
<strong>\<dEBRUYNE\></strong> suraeNoether: OK  
<strong>\<sarang\></strong> Any other general questions?  
<strong>\<suraeNoether\></strong> sarang, do you have an answer to my question?  
<strong>\<suraeNoether\></strong> rehrar answered and this was something i was happy to see  
<strong>\<suraeNoether\></strong> usually it's the noethers talking at everyone else during these meetings :D  
<strong>\<suraeNoether\></strong> but i am curious  
<strong>\<sarang\></strong> I think determining the real viability of newer transaction protocols is a priority for my research  
<strong>\<suraeNoether\></strong> okay. my personal white whale has always been to replace linearly-sized RCT with something sublinear but sufficiently fast to not drag down the network, so i'm happy to have such an embarassment of schemes to work through  
<strong>\<suraeNoether\></strong> anywya, no other questions from me  
<strong>\<sarang\></strong> Yeah, once the RCT3 fix and Omniring batch issues are solved, there will be a much clearer view of what's reasonable IMO  
<strong>\<sarang\></strong> Anyway, on to ACTION ITEMS  
<strong>\<sarang\></strong> I'll be discussing protocol details with some other researchers this week, to gain some better information on these changes  
<strong>\<sarang\></strong> Getting the preprints sorted out for edits and submission  
<strong>\<dEBRUYNE\></strong> If any of you feels like leaving a brief comment here btw -\> <https://www.reddit.com/r/Monero/comments/ct29nx/spectre\_protocol\_update/>  
<strong>\<sarang\></strong> and catching up on a backlog of other preprints that have come out  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<suraeNoether\></strong> working with you on matching code and experimental design, and backlog reading on the work Sarang has done over the past 2 months comparing these three sublinear protocols  
<strong>\<sarang\></strong> neat  
<strong>\<sarang\></strong> OK, any final questions or comments before adjourning?  
<strong>\<sarang\></strong> going once  
<strong>\<sarang\></strong> going twice  
<strong>\<sarang\></strong> Adjourned\! Logs will be posted shortly
