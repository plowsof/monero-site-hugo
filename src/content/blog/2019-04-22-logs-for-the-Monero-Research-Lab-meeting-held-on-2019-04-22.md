---
title: Logs for the Monero Research Lab Meeting Held on 2019-04-22
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> OK, let’s begin. Logs of this meeting will be posted to the GitHub link afterward  
<strong>\<sarang\></strong> 1. GREETINGS  
<strong>\<sarang\></strong> hello  
<strong>\<sgp\_\></strong> hello\!  
<strong>\<sarang\></strong> I assume suraeNoether is also here  
<strong>\<sarang\></strong> I suppose we can move to 2. ROUNDTABLE  
<strong>\<sarang\></strong> The new output selection algorithm was put into a PR by moneromooo with some additional tests added; many thanks to moneromooo for that work  
<strong>\<sarang\></strong> and it’s now merged  
<strong>\<sarang\></strong> This helps to mitigate the block weighting issues and provide better selection  
<strong>\<sarang\></strong> The attempted CLSAG proof reduction to LSAG was not successful because of the way key images are computed, unfortunately  
<strong>\<sarang\></strong> However, I’ve been working on applying the MLSAG proof techniques more directly  
<strong>\<suraeNoether\></strong> howdy, sorry  
<strong>\<suraeNoether\></strong> distrated  
<strong>\<suraeNoether\></strong> I’m here  
<strong>\<sarang\></strong> I’m still working with the Lelantus paper author, a Zcoin cryptographer, to offer some collaborative insight on efficiency gains  
<strong>\<sarang\></strong> Just about finished with test code refactoring, and some additional fixes  
<strong>\<suraeNoether\></strong> what sort of gains are you talking about there?  
<strong>\<suraeNoether\></strong> what is lelantus, and why is it interesting?  
<strong>\<sarang\></strong> It’s a transaction protocol produced by a Zcoin researcher that uses some of the techniques that StringCT also used  
<strong>\<sarang\></strong> but with a more direct balance proof  
<strong>\<sarang\></strong> The paper suggested some batching speedups, but I observed that you could apply them much more broadly to the entire set of transaction proofs (there are several)  
<strong>\<suraeNoether\></strong> neat\! are you two narrowing down on some concrete numbers for comparison in efficiency?  
<strong>\<suraeNoether\></strong> what sort of work remains, in that regard?  
<strong>\<sarang\></strong> A lot of the batching gains depend heavily on the anonymity set used  
<strong>\<sarang\></strong> and there are plenty of open questions about that  
<strong>\<sarang\></strong> But, for example, the bulk of a spend proof (ignoring balance proof and range proofs) for a 1024-size anonymity set is probably about 100 ms using Monero timing operations  
<strong>\<suraeNoether\></strong> wow  
<strong>\<suraeNoether\></strong> wowow  
<strong>\<sarang\></strong> This is purely back-of-the-envelope  
<strong>\<suraeNoether\></strong> for those in the audience, i tend to think of 50 ms is on the border of too slow  
<strong>\<suraeNoether\></strong> does 512 anon set take 50 ms?  
<strong>\<suraeNoether\></strong> is it logarithmic?  
<strong>\<sarang\></strong> mostly linear  
<strong>\<sarang\></strong> keep in mind that batching verification reduces the cost per proof  
<strong>\<suraeNoether\></strong> oh man, we should talk about the space-time tradeoff  
<strong>\<sarang\></strong> I don’t have good numbers for that yet  
<strong>\<suraeNoether\></strong> asymptotically  
<strong>\<sarang\></strong> Yeah, I’ll be working up a set of charts for this  
<strong>\<suraeNoether\></strong> fantastic.  
<strong>\<sarang\></strong> For reference, an MLSAG verification with 1024 ringsize takes 1.2 s  
<strong>\<sarang\></strong> Also the kind of batching that I’m thinking of as being most useful requires the batch to use the same decoy anonymity set  
<strong>\<suraeNoether\></strong> oh that’s sort of an omniring property  
<strong>\<sarang\></strong> You still get some gains without this assumption, but not nearly to the same degree  
<strong>\<suraeNoether\></strong> which we’ll be learning about at the konferenco, apparently :) real\_or\_random  
<strong>\<sarang\></strong> Using a common set means your multiexp operation uses the same generators across proofs (mostly)  
<strong>\<suraeNoether\></strong> of course, i haven’t seen omniring yet…  
<strong>\<sarang\></strong> Anyway, other questions for me?  
<strong>\<suraeNoether\></strong> Good recap, sarang, thanks for describing it to us  
<strong>\<suraeNoether\></strong> \*claps\*  
<strong>\<sarang\></strong> Over to you suraeNoether  
<strong>\<suraeNoether\></strong> well, the past week has been busy for surae  
<strong>\<sarang\></strong> <https://www.youtube.com/watch?v=0TeFrpLL4-E>  
<strong>\<suraeNoether\></strong> MRL 11 update: I finally found the problem with my simulation code, which had to do with passing around an identity for objects like nodes and edges that can be used to retrieve the object, versus passing around the object itself. it’s a silly and embarassing mistake, and it took me way too much time to figure out why things were going wrong. :P  
<strong>\<suraeNoether\></strong> I made a push this morning to my mrl-skunkworks powerpuff branch after finally realizing the problem  
<strong>\<suraeNoether\></strong> that includes the new experimenter class that is actually generating confusion tables… the data it spits out (information for a confusion table) is junk and incorrect, but it doesn’t break anything, so I pushed it… The overall infrastructure is at the point where it may be of interest to \#noncesense-research-lab and Isthmus for independent work.  
<strong>\<suraeNoether\></strong> or anyone else who is interested  
<strong>\<suraeNoether\></strong> <https://github.com/b-g-goodell/mrl-skunkworks/tree/matching-powerpuff/Matching>  
<strong>\<sarang\></strong> What are your next steps for this (jumping ahead a bit)?  
<strong>\<suraeNoether\></strong> the main idea is this  
<strong>\<suraeNoether\></strong> how accurate is the matching approach as ring size scales up? how accurate is the matching approach as churn number increases? how can we use the answers to these questions to formulate best practices for monero churners?  
<strong>\<sarang\></strong> for sure  
<strong>\<suraeNoether\></strong> is there a way we can define some concrete threshold we want to attain?  
<strong>\<sarang\></strong> Understanding how ring size and some specified churn behaviors affect these matching heuristics can give a much clearer picture of what it would take to hit certain thresholds  
<strong>\<suraeNoether\></strong> anyway, that’s my progress update on MRL11: soon^TM. I’m actually getting results without breaking anything, and now it’s a matter of debugging the code and writing new tests to ensure that the results I’m getting are consistent  
<strong>\<suraeNoether\></strong> but I also have a collaborative update, as described in the agenda  
<strong>\<suraeNoether\></strong> long story short: Clemson University’s School of Mathematical and Statistical Sciences is interested in starting a general center for blockchain and cryptocurrency studies.  
<strong>\<suraeNoether\></strong> and they are interested in involving Monero Research Lab in their efforts.  
<strong>\<endogenic\></strong> coolio  
<strong>\<suraeNoether\></strong> we have a few interesting research collaboration possibilities with clemson just stand-alone, new shiny blockchain center notwithstanding  
<strong>\<suraeNoether\></strong> mainly: Professor Shuhong Gao is in the middle of writing several papers that promise to be rather groundbreaking  
<strong>\<suraeNoether\></strong> one of these is reporting a purported attack upon two of the post-quantum nist candidate encryption algorithms  
<strong>\<suraeNoether\></strong> one of these is a new approach to fully homomorphic encryption  
<strong>\<sarang\></strong> sounds very interesting  
<strong>\<suraeNoether\></strong> previous attempts at FHE suffer weird problems. if you want to add two ciphertexts together, it’s easy to retain the number of bits. but to do something like multiplication, you need a larger number of bits than either ciphertext… and so previous approahces sort of use this expanding scratchpad of bits and take up lots of space to perform a computation  
<strong>\<suraeNoether\></strong> gao has developed a way that improves the space efficiency by several orders of magnitude, bringing \*practical\* FHE into reality  
<strong>\<suraeNoether\></strong> his approaches use the RLWE cryptographic setting, which I’ve been looking into recently due to its speed (big keys but very fast algorithms)  
<strong>\<sarang\></strong> sounds suspiciously interesting  
<strong>\<suraeNoether\></strong> yeah, no kidding  
<strong>\<suraeNoether\></strong> he has four visiting scholars interested in blockchain and a handful of students, and the next thing on their plate is RLWE-based STARKs efficient enough for use in something like Monero  
<strong>\<suraeNoether\></strong> so, basically: I’m super excited about the possibility of collaborating with these folks\!  
<strong>\<sarang\></strong> Nice  
<strong>\<suraeNoether\></strong> conflict of interest disclosure: Clemson flew me out to South Carolina last week and put me up in a hotel and fed me. I gave a talk. I received a per diem for food. This is all rather ordinary in that regard.  
<strong>\<suraeNoether\></strong> so, i’m encouraging that Clemson have a presence at the Monero Konferenco, to come meet members of the monero community in person  
<strong>\<suraeNoether\></strong> and I’m encouraging their graduate students to jump in on our research meetings  
<strong>\<endogenic\></strong> awesome\!  
<strong>\<sarang\></strong> Totally; getting more researchers involved is great for the project  
<strong>\<suraeNoether\></strong> I want them to come to the Konferenco, meet some of the folks in the Monero community face to face, and contribute to Monero’s development. I think this is a good thing both for Monero and Clemson University, and I think a more formal academic collaboration with Monero Research Lab is long overdue.  
<strong>\<suraeNoether\></strong> also, for what it’s worth  
<strong>\<suraeNoether\></strong> the last time I was at clemson, speaking with people about cryptocurrency or privacy as a human right was a hard conversation to have  
<strong>\<suraeNoether\></strong> this time, the conversations went… very… very … differently.  
<strong>\<suraeNoether\></strong> a lot changes in 3 years.  
<strong>\<suraeNoether\></strong> people are excited about this.  
<strong>\<endogenic\></strong> what would you say is the origin of the change in their reactoin?  
<strong>\<endogenic\></strong> fungibility?  
<strong>\<suraeNoether\></strong> uhm  
<strong>\<endogenic\></strong> cause the Snowden disclosures etc came out a long time ago  
<strong>\<suraeNoether\></strong> actually, i think it’s structural  
<strong>\<suraeNoether\></strong> meaning: the right people are in control right now for this to move, if that makes sense  
<strong>\<endogenic\></strong> gotcha  
<strong>\<sarang\></strong> Any other new work to share suraeNoether ?  
<strong>\<suraeNoether\></strong> different people standing between the department and their goals than last time, like deans and provosts…  
<strong>\<suraeNoether\></strong> uhm, also, on a totally wild and weird research note  
<strong>\<suraeNoether\></strong> it turns out a homological algebra construction called Ext that Sarang and I studied in grad school together may be the key to forcing my silly signature scheme using commutative/cartesian squares from last year to work  
<strong>\<suraeNoether\></strong> so I’m discussing a paper with another clemson professor  
<strong>\<sarang\></strong> very clever  
<strong>\<suraeNoether\></strong> that’s pretty close to the “pure math” end of the spectrum for this room, so i’m not sure whether i should talk about it before we have some more results  
<strong>\<suraeNoether\></strong> it turns out that Ext can be used to parameterize the zero function between two modules (like, for example, elliptic curve groups)  
<strong>\<suraeNoether\></strong> so we are trying to use that to hide information in a function from one to the other  
<strong>\<suraeNoether\></strong> it’s… bizarre, and it might just work\!  
<strong>\<suraeNoether\></strong> and tha’ts all I have other than action items  
<strong>\<sarang\></strong> neato  
<strong>\<suraeNoether\></strong> but this is round-table and perhaps andytoshi or real\_or\_random or ArticMine have some thoughts on stuff they’ve been working o.  
<strong>\<sarang\></strong> Does anyone else have research work of interest to share?  
<strong>\<suraeNoether\></strong> or anyone else, for that matter  
<strong>\<sarang\></strong> righto  
<strong>\<sarang\></strong> I guess we can move to 3. QUESTIONS and/or 4. ACTION ITEMS  
<strong>\<endogenic\></strong> eyyyyy  
<strong>\<Isthmus\></strong> \*late  
<strong>\<suraeNoether\></strong> oooh isthmus  
<strong>\<suraeNoether\></strong> do you have an update beefore we move onto 3?  
<strong>\<Isthmus\></strong> Been working on playing around with camel emission curves, though that window has probably shut for Monero  
<strong>\<Isthmus\></strong> Also, @n3ptune and I looked at single-transaction outputs in recentish history. There are O(1000) of them  
<strong>\<Isthmus\></strong> <https://github.com/monero-project/monero/issues/5399>  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/YyM3h9KG/image.png>  
<strong>\<Isthmus\></strong> TL;DR:  
<strong>\<Isthmus\></strong> There have been over 2500+ single-output transactions since 2017  
<strong>\<Isthmus\></strong> Single-output transactions (1OTXs) are a persistent intermittent phenomen  
<strong>\<Isthmus\></strong> \*phenomena  
<strong>\<Isthmus\></strong> There was a surge of 1OTXs around height 1562000  
<strong>\<Isthmus\></strong> 1OTXs are observed to this day (data includes 2019)  
<strong>\<suraeNoether\></strong> hm  
<strong>\<sarang\></strong> Could be made consensus, which has been brought up before without any movement  
<strong>\<Isthmus\></strong> They’re also linked to a lot of other nasty heuristics - odd ring sizes, fees that stick out by an order of magnitude, etc.  
<strong>\<sarang\></strong> that spike is crazy  
<strong>\<Isthmus\></strong> Yeah, epic churn event. Should be pretty easy to dissect and trace, but I left that as an exercise for the reader.  
<strong>\<endogenic\></strong> bet that was sgp  
<strong>\<sarang\></strong> All right, let’s go to action items  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<sgp\_\></strong> This should be consensus. Isthmus opened a GitHub issue, and I don’t think anyone has voiced opposition to it  
<strong>\<luigi1111w\></strong> 2 output min is good  
<strong>\<sarang\></strong> absolutely  
<strong>\<Isthmus\></strong> Oh yea, if you have thoughts, leave them here: <https://github.com/monero-project/monero/issues/5399>  
<strong>\<Isthmus\></strong> Otherwise, good to move on  
<strong>\<charuto\></strong> could the spike on 1output transactions be somehow related to monero classic/original ? date seems to almost coincide.  
<strong>\<sarang\></strong> OK, in the interest of hitting our 1-hour target, I’ll work up numbers for batch Lelantus verification at varying anonymity set sizes, and finish up some example code refactoring to complete that project  
<strong>\<sarang\></strong> I’m also looking into how a new transaction type could be used to transition RingCT outputs to this  
<strong>\<sarang\></strong> Submission of the DLSAG paper is finally happening  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<suraeNoether\></strong> woops, sorry, my action items all revolve around getting my simulations done and some confusion tables pushed out  
<strong>\<sarang\></strong> great, thanks  
<strong>\<suraeNoether\></strong> after that i can go do other things  
<strong>\<sarang\></strong> Thanks to Isthmus for opening that issue and getting the conversation started again on 1-out txns  
<strong>\<Isthmus\></strong> 👍  
<strong>\<sarang\></strong> Any other final thoughts before we adjourn and return to general discussion?  
<strong>\<Isthmus\></strong> Also, interesting hypothesis @charuto - might be connected. XMC forked off at 1546000 and the 1OTX spike is around 1560000  
<strong>\<sarang\></strong> OK, we are now adjourned\! Logs will be posted to the GitHub issue shortly. Thanks to everyone for attending; let the discussions continue
