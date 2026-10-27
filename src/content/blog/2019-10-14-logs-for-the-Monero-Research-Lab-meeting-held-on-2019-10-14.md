---
title: Logs for the Monero Research Lab Meeting Held on 2019-10-14
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> GREETINGS  
<strong>\<suraeNoether\></strong> howdy\!  
<strong>\<sgp\_\></strong> Hello  
<strong>\<sarang\></strong> Small crowd today, apparently  
<strong>\<sarang\></strong> Even so, we carry on  
<strong>\<sarang\></strong> Let's move to ROUNDTABLE  
<strong>\<sarang\></strong> I've been working on a few things this past week  
<strong>\<sarang\></strong> First is getting caught up with the usual literature review  
<strong>\<sarang\></strong> Second was finalizing things for World Crypto Conference and some background research associated to that  
<strong>\<sarang\></strong> Third was getting balance proofs working in Triptych, which is now successful  
<strong>\<xmrmatterbridge\> \<serhack\></strong> hello  
<strong>\<sarang\></strong> This means that Triptych now supports a single proof showing all spends, correct key image construction, and balance  
<strong>\<suraeNoether\></strong> nice\!  
<strong>\<sarang\></strong> How about you, suraeNoether?  
<strong>\<suraeNoether\></strong> i've been furiously debugging my matching code as my primary task. there are some persistent problems. i wanted to finish this weekend but it didn't happen  
<strong>\<sarang\></strong> Earlier you had indicated some known bugs... are these the same?  
<strong>\<suraeNoether\></strong> no... every problem i solve reveals like... a small handful of new bugs, but the newer and newer bugs are becoming less frequent and less severe  
<strong>\<suraeNoether\></strong> it \*feels\* like there's a single problem lurking that will cause the house of cards to stop falling down  
<strong>\<suraeNoether\></strong> i'm very close.  
<strong>\<suraeNoether\></strong> i really wanted it to be today  
<strong>\<suraeNoether\></strong> i'm taking a break later today to read sarang's WCC talk (sorry for the delay on that) and I am taking a break later today to work on \*literally anything else\*  
<strong>\<suraeNoether\></strong> i'm very frustrated with this project  
<strong>\<sarang\></strong> Are the known bugs documented anywhere, so others might assist you?  
<strong>\<suraeNoether\></strong> i'm sure a lot of community members are also frustrated, but i this is nearing completion  
<strong>\<suraeNoether\></strong> no  
<strong>\<suraeNoether\></strong> "test X not working for unknown reason" is not a helpful document to write  
<strong>\<sarang\></strong> Hmm ok  
<strong>\<sarang\></strong> Well, I selfishly hope you will take time off that project today and review my talk :D  
<strong>\<sarang\></strong> Perhaps it will also help you clear your head  
<strong>\<sarang\></strong> Does anyone else have interesting research to share as well?  
<strong>\<sarang\></strong> In that case, let's go ahead and discuss ACTION ITEMS first, and then any lingering questions  
<strong>\<sarang\></strong> First, I have an efficient verifier for the inner-product argument in IACR/944 that I've been meaning to implement in kenshamir\[m\]'s Rust code, which will be useful for benchmarking... that's in progress but with some algebra problems that I'm working out  
<strong>\<sarang\></strong> Second, Triptych needs plenty more work: key aggregation, better Fiat-Shamir challenges, and some questions on proof elements and efficiency  
<strong>\<sarang\></strong> Third, I want to see if it's possible to backport some of the new RCT3 changes to the older version without using spend aggregation, to check the resulting efficiency  
<strong>\<sarang\></strong> and that's about it for now  
<strong>\<sarang\></strong> suraeNoether: ?  
<strong>\<suraeNoether\></strong> pushing this commit once my code is flowing. reading your WCC talk. catching up on tryptychychch  
<strong>\<sarang\></strong> It definitely remains to be seen how efficient we can make Triptych... but as I mentioned last week, the underlying changes to the Groth proving system are very interesting regardless  
<strong>\<sarang\></strong> and, as before, there is no security model for it yet  
<strong>\<sarang\></strong> All righty, are there other questions on research?  
<strong>\<sarang\></strong> This meeting has gone quite quickly  
<strong>\<sarang\></strong> Oh, one note about what Isthmus brought up last week regarding transaction keys and subaddresses  
<strong>\<sarang\></strong> It is apparently still the case that transactions to only standard addresses retain a single transaction key  
<strong>\<sarang\></strong> Mandating separate transaction keys for all outputs would add 32 bytes to each additional output  
<strong>\<sgp\_\></strong> Standard = 4?  
<strong>\<sarang\></strong> but we're already saving \> 32 bytes per output after the last change to the Pedersen mask format anyway  
<strong>\<moneromooo\></strong> Could there be a way to deterministically generate keypairs in such a way that the sender generates the secret keys from a seed, the recipients generate the pubkeys ? I think Bitcoin has such a scheme for generating addresses.  
<strong>\<moneromooo\></strong> And hopefully the seed is \<= 32 bytes :)  
<strong>\<sarang\></strong> Well, a big selling point of subaddresses is the efficient scanning across all addresses at once  
<strong>\<sarang\></strong> Isthmus: only need to read up a few lines  
<strong>\<moneromooo\></strong> Would such a scheme invalidate the efficient scanning ? It seems doubtful since the tx keys are currently arbitrary.  
<strong>\<sgp\_\></strong> How much effort is it to scan and see what proportion of transactions are only to standard addresses?  
<strong>\<sarang\></strong> sgp\_: to get a distribution of how common subaddresses are?  
<strong>\<Isthmus\></strong> @sgp\_ I think that @n3ptune accidentally did that recently  
<strong>\<Isthmus\></strong> Lemme see if the plots are on GitHub anywhere  
<strong>\<sgp\_\></strong> sarang: essentially yes  
<strong>\<sarang\></strong> Presumably this would be affected by which large players (like exchanges) support them  
<strong>\<sgp\_\></strong> Thanks Isthmus  
<strong>\<Isthmus\></strong> <https://github.com/noncesense-research-lab/tx\_extra\_analysis/blob/master/tx\_extra\_viz.ipynb>  
<strong>\<sarang\></strong> 404  
<strong>\<Isthmus\></strong> Oh, private repo. Lemme grab the juicy parts  
<strong>\<Isthmus\></strong> This might be the relevant one  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/LgrrzOIS/image.png>  
<strong>\<Isthmus\></strong> I suspect the diagonal is transactions that include a subaddress, while the horizontal bands are primary-only  
<strong>\<Isthmus\></strong> Though I'm open to alternate interpretations  
<strong>\<moneromooo\></strong> Oh I get it. The fast lookup would still exist, but verifiers would have to generate pubkeys, and \*that\* might be slow.  
<strong>\<sgp\_\></strong> Thanks  
<strong>\<Isthmus\></strong> If that is the case, then I can slide a window over time and calculate fraction of transactions that appear to include no subaddresses  
<strong>\<sgp\_\></strong> I'm not the one who can say yes or no to that :/  
<strong>\<sarang\></strong> Probably worth bringing up at the next dev meeting to see what others think of it  
<strong>\<moneromooo\></strong> It is trivial to know whether \>= 1 subaddress was used as an output in a tx.  
<strong>\<moneromooo\></strong> If that was the question...  
<strong>\<moneromooo\></strong> Oh wait. Maybe not, there's some funky going on with change being treated differently...  
<strong>\<sgp\_\></strong> A more meta question: how did this happen? What could have been done differently to help prevent this from happening?  
<strong>\<sarang\></strong> That's probably a question for someone like stoffu who was more directly involved in the code  
<strong>\<sarang\></strong> I suspect space saving was one consideration  
<strong>\<sgp\_\></strong> knaccc too?  
<strong>\<sarang\></strong> but it's quite minor for the most part  
<strong>\<Isthmus\></strong> @sgp\_ meta answer: we rolled out a new feature that:  
<strong>\<Isthmus\></strong> 1) you could tell use from blockchain as external observer  
<strong>\<Isthmus\></strong> 2) was optional  
<strong>\<Isthmus\></strong> Either one of those alone is ok, but together we end up in this situation.  
<strong>\<sgp\_\></strong> I always assumed 1 wasnt the case. I was very misinformed and thus misinformed others  
<strong>\<Isthmus\></strong> Yeah, I think we're all just putting 2+2 together on that now  
<strong>\<sarang\></strong> OK, something to discuss at next dev meeting, then  
<strong>\<sarang\></strong> Are there any other topics to discuss for this meeting?  
<strong>\<Isthmus\></strong> Oh yea, lemme grab a link  
<strong>\<Isthmus\></strong> The CryptoEconSec paper by hasu and all is very interesting, and parts are relevant to both Monero and our lock time conversation  
<strong>\<Isthmus\></strong> \*et al  
<strong>\<Isthmus\></strong> I definitely recommend reading it. Very approachable.  
<strong>\<Isthmus\></strong> Here's the writeup: <https://uncommoncore.co/research-paper-a-model-for-bitcoins-security-and-the-declining-block-subsidy/>  
<strong>\<Isthmus\></strong> And here is my analysis: <https://twitter.com/Mitchellpkt0/status/1183581226357014528>  
<strong>\<Isthmus\></strong> I won't rehash it all here. Just take a pass through on your next commute. :- )  
<strong>\<sarang\></strong> Thanks Isthmus  
<strong>\<sarang\></strong> Any last questions before we adjourn and continue discussions?  
<strong>\<sarang\></strong> Righto, thanks to everyone for attending\!
