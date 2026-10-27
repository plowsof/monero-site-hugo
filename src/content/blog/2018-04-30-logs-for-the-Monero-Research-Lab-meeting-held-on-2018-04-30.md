---
title: Logs for the Monero Research Lab Meeting Held on 2018-04-30
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / surae
---

# Logs

<strong>\<sarang\></strong> dingdingding  
<strong>\<sarang\></strong> it's time  
<strong>\<rehrar\></strong> h'lo  
<strong>\<suraeNoether\></strong> Hi everyone\~  
<strong>\<suraeNoether\></strong> Welcome to our research meeting  
<strong>\<UkoeHB\></strong> g day  
<strong>\<suraeNoether\></strong> One week ago today, Sarang and I were in London  
<strong>\<midipoet\></strong> hello  
<strong>\<suraeNoether\></strong> thanks to this generous community  
<strong>\<sarang\></strong> It seems as if it were only a week ago  
<strong>\<suraeNoether\></strong> heh  
<strong>\<sarang\></strong> It was highly productive  
<strong>\<sgp\_\[m\]\></strong> Hello  
<strong>\<sarang\></strong> We got to meet some London meetup organizers before the event, which was great  
<strong>\<suraeNoether\></strong> yes, this is where we spoke with Pedro Moren-Sanchez, who together with his student (who goes by donut in here) invented refund adresses for Monero  
<strong>\<sarang\></strong> I'm analyzing some preliminary material from them  
<strong>\<sarang\></strong> There's some question about the applicability of hiding block heights  
<strong>\<sarang\></strong> and whether this provides sufficiently better information obscurity to make it worthwhile  
<strong>\<sgp\_\[m\]\></strong> Great sarang\! Glad you could make that work  
<strong>\<suraeNoether\></strong> Since then, other than recovering from jetlag, I've been working non-stop on the multisig paper, which has come a long way... but I've run into a roadblock on the proof of unforgeability, involving the key image, the signing oracle, and access to a discrete logarithm oracle  
<strong>\<sarang\></strong> it involves a change to the ring signatures and key images  
<strong>\<suraeNoether\></strong> in addition to that, I brought rehrar, sgp\_\[m\], and sarang out to Denver to meet with me and my wife about MAGIC, Multidisciplinary Academic Grants in Cryptocurrencies  
<strong>\<midipoet\></strong> whats MAGIC?  
<strong>\<midipoet\></strong> or rather, can you elaborate..  
<strong>\<suraeNoether\></strong> MAGIC is (or will be) a 501(c)3 non-profit based in Colorado, USA  
<strong>\<sarang\></strong> a Colorado nonprofit organization dedicated to empowering the next generation of people in this space  
<strong>\<midipoet\></strong> nice  
<strong>\<suraeNoether\></strong> our goal is to promote education and scientific research, as well as community and educational outreach, in privacy infrastructure for the public good  
<strong>\<midipoet\></strong> that is actually pretty awesome  
<strong>\<suraeNoether\></strong> the basic idea will be to take some of the capital flowing into cryptocurrencies and close the loop back toward education. provide scholarships, provide research grants to researchers and infrastructure grants to schools, and to host conferences on privacy enhancing technologies  
<strong>\<sarang\></strong> It will help boost education (which is great for many reasons) and also can help to promote privacy in the eyes of the public  
<strong>\<sarang\></strong> I'm not one for focusing solely on PR, but it could help  
<strong>\<suraeNoether\></strong> \*nod\*  
<strong>\<sarang\></strong> Kudos to suraeNoether for all the planning on this  
<strong>\<sarang\></strong> it's a ton of work  
<strong>\<suraeNoether\></strong> well, so is math, and this is a way for me to procrastinate on one by being productive in another, and vice versa. :P  
<strong>\<midipoet\></strong> i think if you can redirect some of the capital flows alone towards solid scientific research you are doing a great service already  
<strong>\<midipoet\></strong> there is a lof of greed in crypto  
<strong>\<suraeNoether\></strong> thanks midipoet  
<strong>\<sarang\></strong> Our goal is focus first on education, and then on research  
<strong>\<sarang\></strong> The research side overlaps a bit with some other groups (which is totally fine and beneficial)  
<strong>\<rehrar\></strong> MAGIC focuses on ecological conservation and saving the whales  
<strong>\<midipoet\></strong> lol  
<strong>\<sarang\></strong> hehe  
<strong>\<rehrar\></strong> oh wait, I think I dreamed that (no joke) after our meeting  
<strong>\<suraeNoether\></strong> our first year we don't expect to get enough money to provide a substantial amount towards research, which is pretty expensive. the first year we are going to focus on scholarships, hosting a conference, and hopefully building a computer lab or a library for some impoverished primary schools  
<strong>\<sarang\></strong> Hopefully the 501(c)(3) process goes smoothly. It's very... federal  
<strong>\<suraeNoether\></strong> I'll have more info on that later this week  
<strong>\<suraeNoether\></strong> tomorrow, it's lawyer meetin' time  
<strong>\<sarang\></strong> excellent  
<strong>\<midipoet\></strong> nice  
<strong>\<sarang\></strong> It's worth noting that donors are free to remain anonymous, in the spirit of Monero  
<strong>\<sarang\></strong> but the 501 status will allow donations to be tax-deductible in the U.S. if donors reveal themselves  
<strong>\<midipoet\></strong> creating goodwill around crypto is needed. a lot of people have a very strange view of it, especially since the whole ICO thing  
<strong>\<sarang\></strong> midipoet: definitely  
<strong>\<sarang\></strong> The only other group I know of trying a similar-ish thing is the Zcash Foundation  
<strong>\<sarang\></strong> We'll certainly apply for one of their grants if possible  
<strong>\<sarang\></strong> This work transcends silly interproject politics  
<strong>\<midipoet\></strong> i could tell you a sad story about what computer science kids thought crypto is about in nigeria  
<strong>\<madLyfe\></strong> yay\!  
<strong>\<sarang\></strong> crypto = ca$hmoney  
<strong>\<madLyfe\></strong> <https://i.imgur.com/J2Vyl27.png>  
<strong>\<midipoet\></strong> pretty much sarang  
<strong>\<suraeNoether\></strong> So, from sarang's research we've been looking at refund addresses. from mine, I'm struggling with signing oracles, key images, and discrete logarithms in our unforgeability proofs of multisig (ahem). from educational outreach, we have several folks from the monero research lab and the monero community participating. We even got dinner with Zooko to get ideas on including more independent folks, and I'm  
<strong>\<suraeNoether\></strong> reaching out to two possible additional board members later today  
<strong>\<hyc\></strong> ... silly politics is based on technological assessment tho  
<strong>\<madLyfe\></strong> wrong channel. sorry.  
<strong>\<sarang\></strong> hyc: I totally see that side of it  
<strong>\<sarang\></strong> But for the purposes of this organization it's all silly  
<strong>\<sarang\></strong> I should have clarified  
<strong>\<sarang\></strong> We'll take donations where we can find them if it means helping more students and communities  
<strong>\<suraeNoether\></strong> on another note, a representative from the ZCash foundation asked if we know of anyone in the Monero community who would be willing to serve on the ZCash Foundation board of directors. Because ZCash Foundation, despite the name, is independent of ZCashCo, is a non-profit focused on internet payment and privacy infrastructure also, even if one disagrees with the zcash design philosophy (which is totally fair)  
<strong>\<suraeNoether\></strong> you could still contribute to the privacy community as a whole  
<strong>\<suraeNoether\></strong> hyc maybe you should do it :D  
<strong>\<suraeNoether\></strong> of course, no one from Monero \*needs\* to go and attempt that, but I think it's nice that they reached out  
<strong>\<midipoet\></strong> would you not lose some street cred sitting on that board?  
<strong>\<rehrar\></strong> I second hyc  
<strong>\<rehrar\></strong> he has the good looks and charisma necessary  
<strong>\<suraeNoether\></strong> midipoet: almost certainly.  
<strong>\<suraeNoether\></strong> rehrar: and the fiddlin' talent  
<strong>\<sarang\></strong> midipoet: maybe, but that's up to the individual  
<strong>\<rehrar\></strong> midipoet: street cred is for shmuks  
<strong>\<suraeNoether\></strong> rehrar: ^ +1  
<strong>\<midipoet\></strong> schmuks in Zcash suits  
<strong>\<sarang\></strong> It's worth noting their organization documents include language specifically mentioning supporting the Zcash network  
<strong>\<sarang\></strong> FWIW  
<strong>\<rehrar\></strong> I don't agree with many things of the Zcash implementation, but they're pushing the privacy scene forward  
<strong>\<rehrar\></strong> in a similar way that we are as well with our work  
<strong>\<sarang\></strong> I choose to believe that better research and public perception of privacy will help us all  
<strong>\<rehrar\></strong> right, even if this whole cryptocurrency experiment fails, the world can learn  
<strong>\<midipoet\></strong> yeah, i agree as well. just sceptical  
<strong>\<sarang\></strong> and they're literally making free money available for research and other helpful projects  
<strong>\<suraeNoether\></strong> personally, i think that in 20 years or so, we'll look at the different currency teams in the same way we look at IBM vs. microsoft. it's not weird for IBM guys to get lunch with microsoft guys, or for them to do business together, and probably any market forces that improve one will lead to improving the other.  
<strong>\<suraeNoether\></strong> i mean  
<strong>\<suraeNoether\></strong> there's a positive covariance in market performance across most of the big cryptocurrencies, so high tides lift all the boats, so to speak  
<strong>\<sarang\></strong> It's like commercial airlines... the management types see each other as the devil, but the pilots all help each other out since they're out to get people there safely  
<strong>\<sarang\></strong> maybe  
<strong>\<suraeNoether\></strong> lol maybe  
<strong>\<rehrar\></strong> that said: <https://www.youtube.com/watch?v=A51Bl3jkF0c>  
<strong>\<sneurlax\></strong> to continue that analogy, it's like Google using Java for Android, which was made (or maybe its IP is just now owned) by Oracle  
<strong>\<rehrar\></strong> ^ continues to be one of my favorite videos (10 seconds long)  
<strong>\<suraeNoether\></strong> sneurlax: sure lol  
<strong>\<sarang\></strong> anyway  
<strong>\<midipoet\></strong> aha  
<strong>\<suraeNoether\></strong> ok, so that covers the basic research from the last week, and our educational outreach, and the various political-ish connections MRL has made with other projects  
<strong>\<sarang\></strong> My monthly report details a few other things we've been doing: <https://www.reddit.com/r/Monero/comments/8fzfzx/april\_monthly\_report\_from\_sarang\_noether/>  
<strong>\<suraeNoether\></strong> has anyone done anything else they want to chat about? interesting simulations? I know silur has expressed some interest in getting more involved at MRL, but he is suffering under the delusion that one of us is in charge  
<strong>\<sarang\></strong> The audit has begun for the two larger groups  
<strong>\<suraeNoether\></strong> oh\! audit\! yeah\!  
<strong>\<sarang\></strong> Nothing to report there, just reviewers getting their hands dirty  
<strong>\<sarang\></strong> but it's good news  
<strong>\<suraeNoether\></strong> good, good, it's before May so that's pretty good  
<strong>\<sneurlax\></strong> uh, yeah, what's your favorite programming language with which to verify claims/reports? Python?  
<strong>\<midipoet\></strong> i want to signpost the research i am doing. some of you will have heard it a million times, but formal requests for interviews with devs/cryptographers will be coming very soon. so warning\!  
<strong>\<sarang\></strong> sneurlax: I dig Python for tools  
<strong>\<sarang\></strong> We also need to have fee structure discussions sooner rather than later  
<strong>\<sarang\></strong> and decide precisely how that will change with the BP deployment  
<strong>\<rehrar\></strong> oh shoot, that's a big conversation that we don't want to leave for the last minute  
<strong>\<sarang\></strong> yes  
<strong>\<sarang\></strong> We keep almost having the conversation  
<strong>\<sarang\></strong> Fees are probably the most publicly-visible part of the BP thing  
<strong>\<rehrar\></strong> as well, would there be work for an undergrad mathematician (well versed in statistics)? I know of one that would probably want to get involved over the summer. Would be at the disposal of our MRL PhDs  
<strong>\<sarang\></strong> One thing I would like is a clean Python library giving data structure access to transaction trees  
<strong>\<suraeNoether\></strong> sarang let's talk about fees later today or tomorrow?  
<strong>\<suraeNoether\></strong> rehrar: what sarang said: visualization of transaction histories  
<strong>\<sarang\></strong> i.e. this transaction has these inputs in its ring, and those trace back to other rings, etc.  
<strong>\<sarang\></strong> not even visualizations  
<strong>\<sarang\></strong> just a library giving clean data structures  
<strong>\<sarang\></strong> we can do all sorts of things with that  
<strong>\<sneurlax\></strong> sarang: suraeNoether: that is the basis of my tool  
<strong>\<suraeNoether\></strong> yeah, fair enough, i'm more interested in various statistical properties of those things  
<strong>\<sarang\></strong> Yeah I wanted to ask about details with that  
<strong>\<suraeNoether\></strong> sneurlax: want to talk about it, since it came up?  
<strong>\<sneurlax\></strong> I can port that to Python. the more information/specs you can proivide, the less questions I'll have later  
<strong>\<sarang\></strong> Sure, let's chat after the meeting sneurlax  
<strong>\<sneurlax\></strong> perfect  
<strong>\<sarang\></strong> Even if it's not Python, having something easy to implement will be great  
<strong>\<suraeNoether\></strong> yeah, i mean from my point of view  
<strong>\<nioc\></strong> always check with ArticMine when it comes to fees  
<strong>\<suraeNoether\></strong> i'm interested in things like the distribution of sizes of transaction trees, how often outputs are re-used within the same, tree, stuff like that  
<strong>\<sarang\></strong> Yes, it's a discussion for many people  
<strong>\<suraeNoether\></strong> nioc: yeah, he has something written up already  
<strong>\<sarang\></strong> but one that needs to be had  
<strong>\<suraeNoether\></strong> iirc  
<strong>\<sarang\></strong> Any other interesting work lately?  
<strong>\<sarang\></strong> (BTW we should arrange some time in -dev meeting for fee talks)  
<strong>\<nioc\></strong> should be a dev meeting this coming Sun  
<strong>\<nioc\></strong> rehrar: ^^^ ??  
<strong>\<rehrar\></strong> yes nioc  
<strong>\<sgp\_\[m\]\></strong> Was this discussed? <https://github.com/moneroexamples/key\_images\_comparison>  
<strong>\<suraeNoether\></strong> it has not been  
<strong>\<suraeNoether\></strong> wow\!  
<strong>\<suraeNoether\></strong> much smaller numbers than I was expecting  
<strong>\<suraeNoether\></strong> you know, endogenic earlier asked about the plausibility of long-term blackballing  
<strong>\<suraeNoether\></strong> and I responded with a silly analogy, comparing the monero blockchain to a pile of radioactive material: outputs have half-lives of their anonymity as bad actors perform more and more blockchain forensics, they expose more and more old outputs...  
<strong>\<sgp\_\[m\]\></strong> Thoughts on the proportion used, and the proportion that used the tool? I actually felt that 10% of reused key images using a special tool to pair outputs was unusually high  
<strong>\<hyc\></strong> lol pretty sure Zcash team has me blacklisted  
<strong>\<suraeNoether\></strong> i meant the % that have at least one re-used key  
<strong>\<suraeNoether\></strong> hyc it's what you get for being such a lovely violinist  
<strong>\<hyc\></strong> harhar  
<strong>\<sneurlax\></strong> @sgp\_:matrix.org would you mind linking your previous work on key image reuse impacts at ... what was it, % reuse?  
<strong>\<suraeNoether\></strong> if we make it clear which outputs are provably spent, then what we are doing is relying on economic activity frontloading this radioactive decay process, hoping that a big mass of anonymous outputs stand between us and the back end, as blockchain forensics unravel the blockchain from the genesis block moving forward. so the only way this sort of thing is sustainable is if we have economic activity outpacing  
<strong>\<suraeNoether\></strong> forensics efforts  
<strong>\<midipoet\></strong> thats quite interesting  
<strong>\<sneurlax\></strong> I just ask because I liked the work, sqp  
<strong>\<suraeNoether\></strong> it highlights that ring sigs, or at least "small anon set" methods, need to be replaced  
<strong>\<sneurlax\></strong> that big mass probably has a lot of dead ends that'll confound that unravelling. who knows how many keys have been lost.  
<strong>\<sgp\_\[m\]\></strong> sneurlax here's the Google Sheet (logout of Google): <https://docs.google.com/spreadsheets/d/1iLa\_yklutjHqn\_DrOlO\_eTb00l4YDAezijX2J5r6P14/edit?usp=sharing>  
<strong>\<midipoet\></strong> or there is some critical mass of privacy enaction that provides protection...  
<strong>\<sneurlax\></strong> there are definitely outputs which will never be reused because their owners forgot about them, lost their keys, etc.  
<strong>\<sneurlax\></strong> thank you\!  
<strong>\<suraeNoether\></strong> okay, does anyone else have any questions, concerns? i need to bother andytoshi about key images and this discrete log problem I'm having before I'm more comfortable with where our multisig scheme is at  
<strong>\<hyc\></strong> so those outputs will always be ambiguous, never proven spent  
<strong>\<UkoeHB\></strong> they could be proven unspent  
<strong>\<suraeNoether\></strong> hyc unless all outputs that refer to it can be proven to be linked to another output  
<strong>\<suraeNoether\></strong> right  
<strong>\<hyc\></strong> ok  
<strong>\<sarang\></strong> OK, meeting is officially adjourned, but feel free to stick around for further discussion
