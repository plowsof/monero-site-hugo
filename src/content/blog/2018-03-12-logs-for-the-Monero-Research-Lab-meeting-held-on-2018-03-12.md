---
title: Logs for the Monero Research Lab Meeting Held on 2018-03-12
summary: BP audit, Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<suraeNoether\></strong> So, greetings everyone\!  
<strong>\<MoroccanMalinois\></strong> Hi  
<strong>\<iDunk\></strong> Hi  
<strong>\<sarang\></strong> yo  
<strong>\<suraeNoether\></strong> Agenda today is 1) hello, 2) BP audit update 3) other stuff Sarang has been reading/working on, 4) stuff I've been working on, 5) obligatory update on MAGIC, 6) anything anyone else wanna talk about?  
<strong>\<suraeNoether\></strong> oh, I also want to talk about: how to educate our users about proper key usage and proper privacy practices  
<strong>\<ArticMine\></strong> hi  
<strong>\<endogenic\></strong> o/  
<strong>\<suraeNoether\></strong> so, sarang: BP audit update? you gave us a brief one earlier  
<strong>\<suraeNoether\></strong> but let's recap for folks who weren't here  
<strong>\<sarang\></strong> sure thing  
<strong>\<sarang\></strong> We have raised funds for 3 audits: Benedikt Bunz, QuarksLab, Kudelski  
<strong>\<sarang\></strong> I'm finalizing contracts with them  
<strong>\<sarang\></strong> We will likely need to do supplemental funding later due to market tomfoolery  
<strong>\<sarang\></strong> I will be working with the groups during their audits, which will take place between this months and June  
<strong>\<sarang\></strong> That's the brief version  
<strong>\<endogenic\></strong> may i ask a question regarding our auditing efforts in general?  
<strong>\<sarang\></strong> plz  
<strong>\<endogenic\></strong> or should i wait til end?  
<strong>\<sarang\></strong> fire away  
<strong>\<endogenic\></strong> so i'm also wondering about vulnerabilities in the code in general - i know we have the bounty system for that but it's not got quite the same incentive system  
<strong>\<endogenic\></strong> just wondering if it makes sense to apply this model to other parts of the code  
<strong>\<sarang\></strong> Hiring auditors, you mean?  
<strong>\<endogenic\></strong> yeah  
<strong>\<sarang\></strong> I'm seeing more and more support for it, yes  
<strong>\<endogenic\></strong> or an FFS for an auditor  
<strong>\<suraeNoether\></strong> endogenic: so there is this clever idea  
<strong>\<sarang\></strong> At least for components of the code, like multisig or BPs that have a defined scope  
<strong>\<suraeNoether\></strong> that greg maxwell and blockstream are using for their libsecp256k1 library  
<strong>\<suraeNoether\></strong> which has a badass test suite  
<strong>\<endogenic\></strong> sarang: right i suppose i'm thinking more from the security and cracking standpoint .. like, can we confirm what % of data input fuzzing we've done and where / if / how the code fails  
<strong>\<endogenic\></strong> etc  
<strong>\<suraeNoether\></strong> where they aren't providing bug bounties for the actual library, but for the unit test suite: if you can upload a new unit test that the current system fails, and yet still passes all current unit tests, you get the bounty  
<strong>\<sarang\></strong> That's more of a question for moneromooo I think  
<strong>\<endogenic\></strong> that sounds interesting surae  
<strong>\<suraeNoether\></strong> it incentivizes things very nicely  
<strong>\<suraeNoether\></strong> but it requires a really great test suite  
<strong>\<sarang\></strong> yes indeed  
<strong>\<moneromooo\></strong> I don't think we can easily determine a percentage of inputs for fuzzing.  
<strong>\<endogenic\></strong> well that was just one example  
<strong>\<endogenic\></strong> i cant take responsibility to define all the jobs an expert cracker would do :P  
<strong>\<suraeNoether\></strong> if we are going to start putting money into auditors, then we should consider putting a proportion of that toward beefing up our test suites. perhaps require that auditors propose new unit tests, or something along those lines, in addition to a thumbs up/down and a list of recommended changes  
<strong>\<endogenic\></strong> yeah  
<strong>\<endogenic\></strong> i mean we want to record the work which was done  
<strong>\<endogenic\></strong> and tests can be nice way to do that  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> and that way, perhaps after a year or two, we will have a test suite sufficiently beefy to incentivize properly  
<strong>\<suraeNoether\></strong> i know its' kind of a long-term plan  
<strong>\<sarang\></strong> Too bad it's sexier to run an FFS for an auditor than for writing test suites :(  
<strong>\<suraeNoether\></strong> short of paying some smart people to audit our whole lie-berry and come up with test suites across the board  
<strong>\<suraeNoether\></strong> yeah, no kidding  
<strong>\<endogenic\></strong> sarang it can be pitched in the same way  
<strong>\<endogenic\></strong> they audit by the very activity  
<strong>\<rehrar\></strong> do unit tests require coding? (sorry if this is a stupid question)  
<strong>\<endogenic\></strong> yep  
<strong>\<sarang\></strong> yes  
<strong>\<rehrar\></strong> blerg  
<strong>\<endogenic\></strong> it's not that bad tho rehrar  
<strong>\<endogenic\></strong> it's more about understanding what you are testing for  
<strong>\<sarang\></strong> The goal is to have complete scope  
<strong>\<rehrar\></strong> it is when my coding is 1/10 :D  
<strong>\<sarang\></strong> Any questions on the current audit that anyone has?  
<strong>\<sarang\></strong> Kudelski will be the first to go  
<strong>\<moneromooo\></strong> When does the C++ based one start ?  
<strong>\<sarang\></strong> They're available this month  
<strong>\<moneromooo\></strong> More precisely ?  
<strong>\<sarang\></strong> TBD once we sign with them, but I can check on more specific dates if you need them  
<strong>\<sarang\></strong> Anything in particular?  
<strong>\<suraeNoether\></strong> ok, well  
<strong>\<ArticMine\></strong> are all the audits going through ostif?  
<strong>\<sarang\></strong> Two of them are  
<strong>\<sarang\></strong> Benedikt will be paid directly in XMR  
<strong>\<suraeNoether\></strong> ArticMine: I believe Buenz is independent  
<strong>\<suraeNoether\></strong> ^  
<strong>\<sarang\></strong> OSTIF's role is just to handle the payment  
<strong>\<sarang\></strong> They'd appreciate being thanked in our materials for helping to organize the groups and handle the exchange  
<strong>\<suraeNoether\></strong> okay, if there are no more questions on BPs  
<strong>\<sarang\></strong> So this will be an ongoing process over the next few months  
<strong>\<sarang\></strong> expect little news until someone finishes  
<strong>\<suraeNoether\></strong> Sarang: what else have you been reading/doing?  
<strong>\<sarang\></strong> I've been reviewing the latest multisig draft from suraeNoether  
<strong>\<suraeNoether\></strong> ok in that case we will stop bringing it up every meeting for 3 weeks or so :P  
<strong>\<sarang\></strong> prepping a submission for defcon china  
<strong>\<suraeNoether\></strong> that's cool  
<strong>\<sarang\></strong> prepping a talk in portland on monero security  
<strong>\<sarang\></strong> reading up on some papers involving mixing and ring representations  
<strong>\<sarang\></strong> hoping to get back to some math shortly for pippenger's algorithm  
<strong>\<sarang\></strong> for speedier multiexp  
<strong>\<sarang\></strong> more administrative work lately, unfortunately  
<strong>\<sarang\></strong> I submitted a monthly report recently that details other efforts  
<strong>\<sarang\></strong> linky linky <https://forum.getmonero.org/9/work-in-progress/89005/funding-for-sarang-at-mrl-for-q1-2018?page=&noscroll=1#post-94324>  
<strong>\<suraeNoether\></strong> any other questions for sarang?  
<strong>\<suraeNoether\></strong> I'd like to remind the crowd that sarang's FFS funding round I believe has been posted, although I'm not sure if it's moved to Funding Required yet  
<strong>\<rehrar\></strong> There's quite a few things that need to be moved to funding required  
<strong>\<rehrar\></strong> we should all poke fluffypony and luigi1111  
<strong>\<sarang\></strong> Mine is still in Open and not in Funding yet  
<strong>\<sarang\></strong> There hasn't been much activity regarding it anyway  
<strong>\<sarang\></strong> Not a huge rush. I write them in advance to allow for discussion if needed  
<strong>\<sarang\></strong> How about suraeNoether? Your turn  
<strong>\<suraeNoether\></strong> 4) Stuff I've been working on. Multisig paper, formal documentation work for monero, and a formal description of EABE attacks.  
<strong>\<suraeNoether\></strong> For the multisig paper, I just received notes from sarang and I'll be composing a draft for review by someone outside of MRL.  
<strong>\<sarang\></strong> suraeNoether: I'll have remaining notes added to your doc this afternoon  
<strong>\<suraeNoether\></strong> right now I need to copy-paste some intro/notation stuff from a previous version of the paper, fix some references, stuff like that, and then take sarang's changes into account  
<strong>\<suraeNoether\></strong> great thanks  
<strong>\<suraeNoether\></strong> Once the document is a little less ugly, i'll link to it again  
<strong>\<sarang\></strong> Now on to MAGIC per the agenda?  
<strong>\<suraeNoether\></strong> I've been attempting to write up a formal description of the statement being proven in a given monero ringCT authentication, for two reasons. For one thing, I think that our approach for threshold multisig could be generalizable in a way that may make it fun to publish. But I'm not sure if this description has appeared before in the literature, so I'm looking around and contacting some folks  
<strong>\<suraeNoether\></strong> For another reason, because I haven't seen it written out explicitly before.  
<strong>\<suraeNoether\></strong> And the EABE attack is concerning enough to me to be writing up some statistical arguments about churn (sgp\_\[m\] ping)  
<strong>\<suraeNoether\></strong> i'll be linking all these documents in the next week  
<strong>\<suraeNoether\></strong> so far it looks like 3 sketches of possible papers for publication, even if not as peer reviews, as whitepapers  
<strong>\<suraeNoether\></strong> after multisig is running  
<strong>\<suraeNoether\></strong> anyway, onto MAGIC  
<strong>\<suraeNoether\></strong> i feel like folks have a lot of questions about MAGIC, so I'll ask if anyone has any questions  
<strong>\<sarang\></strong> Question I've seen is: what types of things will it fund, and how will they be determined?  
<strong>\<luigi1111w\></strong> sarang moved  
<strong>\<luigi1111w\></strong> moneromooo ready for funding  
<strong>\<rehrar\></strong> thanks luigi  
<strong>\<sarang\></strong> ty luigi1111w  
<strong>\<suraeNoether\></strong> Good question. The overall scope will be: 1) scholarships to undergraduates in the US 2) grants to graduate students in the US, 3) grants to researchers in the US, 4) grants to schools globally with an emphasis on secondary and tertiary education  
<strong>\<suraeNoether\></strong> how much of that we can actually do depends on our funding  
<strong>\<suraeNoether\></strong> oh 5) sponsoring tehcnical conferences in cryptocurrencies is also on that list  
<strong>\<sarang\></strong> suraeNoether: why restrict scholarships and grad grants to US?  
<strong>\<suraeNoether\></strong> so our first year, my goal is to provide a few scholarships, sponsor the first monero conference, and fix up a school in south africa  
<strong>\<rehrar\></strong> what other ways of funding are you searching for besides FFS stuff?  
<strong>\<endogenic\></strong> do you have any criteria to decide what is good research that gets funded?  
<strong>\<suraeNoether\></strong> sarang: because i feel like we already are going to have lots of applications  
<strong>\<endogenic\></strong> will decision making ever get delegated?  
<strong>\<sarang\></strong> The org will need established principles for determining its choices  
<strong>\<sarang\></strong> to stay transparent and accountable to its donors  
<strong>\<suraeNoether\></strong> rehrar: we'll be soliciting funding and grants from as many places as possible. one delightful property of non-profits in america: anything they spend that isn't on overhead must go to charitable purposes or other non-profits. so non-profits like the bill &amp; melinda gates foundation give lots of money to other non-profits.  
<strong>\<sarang\></strong> rehrar: I mentioned the kernel of this idea to some fund managers, who said their groups were interested in supporting nonprofits; this may lead to new funding avenues  
<strong>\<rehrar\></strong> that's pretty awesome  
<strong>\<suraeNoether\></strong> endogenic: I haven't started thinking about the research end of MAGIC yet because i'm assumign the first year we won't necessarily get enough money to manage to give out substantial research grants  
<strong>\<endogenic\></strong> sorry replace research with project  
<strong>\<endogenic\></strong> i misspoke  
<strong>\<sarang\></strong> Sounds like there would be a clear delineation between scholarships and grants  
<strong>\<suraeNoether\></strong> ah yeah well in general, like sarang says, we need established principles for determing our choices, and this is something that needs to be discussed at our board meetings. we want to be very public, and i want to make our board meetings available as youtube videos or whatever... pending agreement by the other board members (some of whom have not yet been picked)  
<strong>\<suraeNoether\></strong> sarang yes  
<strong>\<sarang\></strong> Grants would have the expectation of deliverables  
<strong>\<sarang\></strong> Scholarships are to increase the talent pool and help perhaps underrepresented student groups become involved in the space  
<strong>\<suraeNoether\></strong> scholarships for undergrads, it is my intention, to mainly be aimed at folks in law or economics or computer science or math. Not exactly the traditional STEM mix. however, i don't want an undergrad to worry about losing their money if they decide to study graph theory instead of bitcoin  
<strong>\<suraeNoether\></strong> sarang ^ yep  
<strong>\<suraeNoether\></strong> i kind of want the schoalrships nearly strings-free  
<strong>\<sarang\></strong> However, the devil's in the details  
<strong>\<suraeNoether\></strong> as far as funding goes, though, i'm matching up to 5% of donations up to 50 XMR for this venture. If we manage to get 1000 XMR, I donate 50 XMR to the cause and we'll have 1050 XMR for the first year  
<strong>\<sgp\_\[m\]\></strong> suraeNoether a little late to chime in, but I would love to help you with the EAE paper if there's any way I can  
<strong>\<suraeNoether\></strong> sgp\_\[m\]: PM me  
<strong>\<suraeNoether\></strong> and if we can manage that much XMR the first year, we can pay for like 5 scholarships for undergrads, 2 grad student grants, fix up a school or two in ZA, and host the first monero conference (with no entry fee)  
<strong>\<sarang\></strong> This is an interesting pilot project that could take many different directions  
<strong>\<suraeNoether\></strong> and still have some XMR leftover for the next year  
<strong>\<sarang\></strong> I think it'll important to keep the scope balanced between too narrow and too broad  
<strong>\<suraeNoether\></strong> my primary concern right now is determining criteria for handing out scholarships  
<strong>\<sarang\></strong> An established mission is gonna be essential to establishing and maintaining this direction  
<strong>\<suraeNoether\></strong> personally i think the best students are the ones who sucked the first year or three and then completely turn around, but that's just rewarding students with a past similar to myself  
<strong>\<rehrar\></strong> how many board members and who is under consideration?  
<strong>\<rehrar\></strong> will you guys need a website?  
<strong>\<suraeNoether\></strong> yes  
<strong>\<sarang\></strong> You'll need to use the application process to determine who is excited about the crypto space and not just eager to hop on a money train  
<strong>\<rehrar\></strong> msvb-lab will get mad at me if I talk about other people's websites before I finish Kastelo  
<strong>\<sarang\></strong> I wouldn't expect the model student to know everything about this space, but I want to ensure that the recipients are those with a strong desire to succeed in it for good reasons  
<strong>\<msvb-lab\></strong> rehrar: Yes, very mad. It's our nature.  
<strong>\<suraeNoether\></strong> me, sarang, the operations manager from Globee, my advisor at Clemson university (Jim Coykendall), my wife are going to be the first board members.  
<strong>\<sarang\></strong> rehrar: we'll advertise with hip videos on FaceSpace and SnapTime and InstantGram where students like to hang  
<strong>\<suraeNoether\></strong> if anyone has an issue with my wife on the board, MAGIC was partly her idea, she has 7 years experience teaching in higher education, and she isnt' being paid  
<strong>\<sarang\></strong> Should there be broader representation?  
<strong>\<suraeNoether\></strong> I'd be happy including more board members  
<strong>\<sarang\></strong> Or is this sufficient?  
<strong>\<rehrar\></strong> I'm a Mexican if we need diversity :P  
<strong>\<sarang\></strong> I'm not leaning one way or another, just wondering if it is  
<strong>\<suraeNoether\></strong> rehrar: you are also in NM yeah?  
<strong>\<rehrar\></strong> I am  
<strong>\<suraeNoether\></strong> and NM has liiiike some serious education problems  
<strong>\<suraeNoether\></strong> iirc  
<strong>\<rehrar\></strong> Come down and we'll have a party trip to Juarez  
<strong>\<rehrar\></strong> yes  
<strong>\<rehrar\></strong> we really do  
<strong>\<suraeNoether\></strong> WELCOME ABOARD REHRAR  
<strong>\<rehrar\></strong> I'm working on this myself actually in my free time  
<strong>\<rehrar\></strong> We're like the second worst in the nation  
<strong>\<suraeNoether\></strong> cool email me at <surae@getmonero.org> so I can get you on a list  
<strong>\<suraeNoether\></strong> okay, lastly  
<strong>\<rehrar\></strong> I'm on a lot of NSA lists already, but sure.  
<strong>\<endogenic\></strong> yes NM does  
<strong>\<endogenic\></strong> rehrar is the only beacon  
<strong>\<rehrar\></strong> endogenic came here and saw the people sobbing in the streets  
<strong>\<suraeNoether\></strong> okay, lastly: I wanted to talk about how to educate the community about key safety with MoneroV and best practices (currently, I'm not convinced churn is non-negligibly helpful under a very specific threat model)  
<strong>\<rehrar\></strong> What about a short one minute video?  
<strong>\<suraeNoether\></strong> would be very convenient to link to  
<strong>\<rehrar\></strong> We can put it on our soon-to-come media.getmonero.org as well as youtube and stuff  
<strong>\<suraeNoether\></strong> i've been thinking about starting whiteboard youtube videos explaining how cryptocurrencies work. this could be the first one.  
<strong>\<rehrar\></strong> suraeNoether, talk with me later about Privacademy.  
<strong>\<nioc\></strong> something that would allow an idiot like me to know exactly what to do  
<strong>\<sarang\></strong> Just paste your private keys here. We'll print them out and put them in a safe for you  
<strong>\<Osiris1\></strong> ;)))  
<strong>\<sarang\></strong> OR DON'T  
<strong>\<Osiris1\></strong> nice  
<strong>\<nioc\></strong> thx  
<strong>\<ArticMine\></strong> My concern with this is that we do not end up protecting MoneroV from the claws of the bear  
<strong>\<suraeNoether\></strong> nioc, looks to me like you're a pretty smart fella, if the past few years have shown us anything about anticipating change. :P ok. Does nayone have any questions, concerns, comments? I'll be posting my next funding request this afternoon. I have a hard time gauging the mood of an IRC chat room  
<strong>\<suraeNoether\></strong> ArticMine: care to elaborate?  
<strong>\<endogenic\></strong> i heard nioc is a cabbage  
<strong>\<endogenic\></strong> literally  
<strong>\<sarang\></strong> I don't have a good sense for how many users will fall for V  
<strong>\<ArticMine\></strong> Basically i see MoneroV as an economic attack. If nobody claims their MoneroV then it price will be significantly inflated  
<strong>\<ArticMine\></strong> So we need a process for people to claim, their MoneroV safely and without impacting their own and other's privacy and to be blunt at the appropriate time dump the MoneroV on the market  
<strong>\<ArticMine\></strong> That is where the claws of the bear come in  
<strong>\<sarang\></strong> What do you mean ArticMine? Spending an existing output on the V chain with random ring is immediately deanon  
<strong>\<sarang\></strong> and contributes to the eventual deanon of your ringmates  
<strong>\<rehrar\></strong> I see what he's saying though. If not a lot of people claim theirs, then it's a lot of immediate 'holders' which might artificalily inflate the price  
<strong>\<ArticMine\></strong> The only way I can see this working is a spend on both chains with a significant number of overlapping rings  
<strong>\<rehrar\></strong> which in turn, might make it seem like MoneroV was somewhat successful  
<strong>\<rehrar\></strong> which also in turn might make other people try to do something similar with Monero  
<strong>\<ArticMine\></strong> If the price of MoneroV crashes then this becomes a powerful deterrent for the future  
<strong>\<suraeNoether\></strong> ArticMine: i disagree. airdrops are designed to crash like that  
<strong>\<sarang\></strong> Tough part is that a given user might not care about their transaction being deanon. But it's convincing them that it contributes to others that's trickyy  
<strong>\<suraeNoether\></strong> they aren't designed for egalitarian long-term pegs  
<strong>\<Olufunmilayo\></strong> sarang, I thought (mind you I am late to the party), that spending a output on both chains with the same ring was theoretically "safe-ish" to some extent  
<strong>\<suraeNoether\></strong> Olufunmilayo: only if all your ringmates do the same, and all their ringmates, etc  
<strong>\<sarang\></strong> And their code needs to support it  
<strong>\<ArticMine\></strong> It is but trike to do  
<strong>\<sarang\></strong> they've shown they don't GAF  
<strong>\<ArticMine\></strong> Then we will have to release a patched Monerov  
<strong>\<ArticMine\></strong> It does not have to be "official"  
<strong>\<sarang\></strong> One idea I like is making it easier to fork the Monero codebase and blockchain safely  
<strong>\<rehrar\></strong> \*shrug\* I may be thinking a bit casually here, but since this is the first time something like this is happening, and we're already going to be getting our upped ringsize before the fork, I think we can somewhat safely wait this one out and see how it plays  
<strong>\<sarang\></strong> So for future attempts, they'd have to actively break that safety  
<strong>\<sarang\></strong> and then we can give them bad publicity for actively hurting users  
<strong>\<suraeNoether\></strong> i wonder if they doubly-hash their key images. so you check if pHp(P) is in the key image set or if pHp(pHp(P))  
<strong>\<suraeNoether\></strong> or if they could rather  
<strong>\<ArticMine\></strong> By the way the network effect is less because of spent RingCT ouputs that will not be compromised  
<strong>\<rehrar\></strong> Alright, I gotta split. Thanks for the meeting. Catch you guys later  
<strong>\<Olufunmilayo\></strong> ArticMine, what good would a patched monerov be if the core team is not behind monerov? Also, suraeNoether, time would also be a factor yes? both have to be done simultaneously  
<strong>\<ArticMine\></strong> The trouble is that the same keys are used on both chains  
<strong>\<ArticMine\></strong> It will allow those who wish to claim and sell their MoneroV to do so safely.  
<strong>\<suraeNoether\></strong> oh no the double hash doesn't work unless all previous ring sigs do it that way. bah.  
<strong>\<ArticMine\></strong> Not all but enough to provide a good mix  
<strong>\<ArticMine\></strong> and that means pre fork mixins will only work  
<strong>\<Olufunmilayo\></strong> ArticMine, you will then have two competing versions of monerov competing against each other. I do see the benefit but \*shrug\*  
<strong>\<suraeNoether\></strong> okay, well, unless folks have more questions or suggestions, i think our best bet is simply to put out a video that says "don't claim your MoneroV, here is why."  
<strong>\<ArticMine\></strong> No the patch can be compatible with the MoneroV consensus  
<strong>\<suraeNoether\></strong> because the math to patch monerov or to protect monero isn't obvious to me right now  
<strong>\<ArticMine\></strong> I am not sure if there is a solution  
<strong>\<iDunk\></strong> It's mooo's code to make it use the ringdb, AFAIUI.  
<strong>\<Olufunmilayo\></strong> suraeNoether, only other thing would be to I guess track monerov tx's to see just how bad it is haha  
<strong>\<sarang\></strong> We will  
<strong>\<suraeNoether\></strong> Okay, well  
<strong>\<suraeNoether\></strong> good meeting everyone  
<strong>\<suraeNoether\></strong> 1h10 minutes, not too bad  
<strong>\<suraeNoether\></strong> OH OH  
<strong>\<sarang\></strong> oh  
<strong>\<hyc\></strong> oh?  
<strong>\<suraeNoether\></strong> anyone want to volunteer to make PRs to my github with meeting logs? I'm literally never going to do it  
<strong>\<suraeNoether\></strong> i intend to every week, but i think i need to practically accept that it's not going to happen. :P  
<strong>\<sarang\></strong> <https://www.youtube.com/watch?v=ZXsQAXx\_ao0>  
<strong>\<suraeNoether\></strong> ok  
<strong>\<suraeNoether\></strong> fine  
<strong>\<suraeNoether\></strong> lol  
<strong>\<suraeNoether\></strong> \\meeting  
<strong>\<sarang\> \</meeting\></strong>  
<strong>\<suraeNoether\></strong> <https://github.com/b-g-goodell/research-lab/tree/master/meta/research-meeting-logs>  
<strong>\<suraeNoether\></strong> just started a folder called meta rather than cloning the meta repo for The Monero Project.  
<strong>\<suraeNoether\></strong> i suppose i should clone it and make pushes appropriately  
<strong>\<suraeNoether\></strong> but i'll dot hat later  
<strong>\<suraeNoether\></strong> ack its not complete  
<strong>\<suraeNoether\></strong> ok there we go: <https://github.com/b-g-goodell/research-lab/blob/master/meta/research-meeting-logs/ResMeetLogs-12-Mar-2018.txt>  
<strong>\<suraeNoether\></strong> bbl yall\~
