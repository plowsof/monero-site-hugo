---
title: Logs for the Monero Research Lab Meeting Held on 2018-11-05
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Right right, let's begin our meeting now  
<strong>\<sarang\></strong> First, GREETINGS to/from all  
<strong>\<sarang\></strong> hello  
<strong>\<sgp\_\></strong> hello  
<strong>\<sarang\></strong> ping binaryFate dEBRUYNE endogenic hyc IsthmusCrypto gmaxwell gingeropolous moneromooo parasew\[m\] rehrar rrol\[m\] stoffu smooth UkoeHB etc  
<strong>\<sarang\></strong> small crowd today  
<strong>\<parasew\[m\]\></strong> hi  
<strong>\<sarang\></strong> Even so, RESEARCH UPDATE time  
<strong>\<sarang\></strong> I've done some rearranging with the Lab's public-facing presentation  
<strong>\<sarang\></strong> We'll be routing the old lab.getmonero.org to the new getmonero.org MRL landing page  
<strong>\<sgp\_\></strong> nice  
<strong>\<rehrar\></strong> I'm here  
<strong>\<sarang\></strong> This allows for translations of things like abstracts, and lets us PR new papers  
<strong>\<sarang\></strong> Once this gets merged over on monero-site (hint hint nudge nudge), the three newest MRL publications will appear there  
<strong>\<sarang\></strong> English translations only for those papers' abstracts, for the moment  
<strong>\<sarang\></strong> Anyway, PR is open there: <https://repo.getmonero.org/monero-project/monero-site/merge\_requests/950>  
<strong>\<sarang\></strong> Some format changes too; review if you like  
<strong>\<sarang\></strong> I've tossed a basic noninteractive musig implementation over to the sublinear prototyping code for testing purposes  
<strong>\<sarang\></strong> The usual lit review  
<strong>\<sarang\></strong> And a lot of investigations on output selection since the upgrade  
<strong>\<sarang\></strong> Any questions/comments on these items?  
<strong>\<sgp\_\></strong> do you think it would be useful to have another bulletproof-type video talking about the recent selection changes and possible options going forward? It could be much shorter, perhaps 20-30 minutes  
<strong>\<sarang\></strong> I don't consider there to be consensus on the best way to iterate on that  
<strong>\<sarang\></strong> so it's not clear what user benefit there would be, except "it's better than before, and we're working on it"  
<strong>\<sarang\></strong> :/  
<strong>\<sgp\_\></strong> it could be useful just to get the info out there. depends on user feedback I suppose  
<strong>\<sgp\_\></strong> most people probably don't care  
<strong>\<sarang\></strong> We certainly could, but I also don't want to cause unnecessary FUD  
<strong>\<sarang\></strong> My standard line has become "output selection is one layer we use to keep transactions safe; it's been iterated many times over the project's history, and continues to be"  
<strong>\<sgp\_\></strong> all right, we can move on then  
<strong>\<sarang\></strong> as with many heuristics, a suboptimal selection algorithm is not a spend proof  
<strong>\<sarang\></strong> ring signatures continue to do exactly what it says on the box  
<strong>\<sarang\></strong> I'm running a workshop in Chicago later this week, offering hands-on coding with some basic crypto constructions in Python, practicing RPC calls and explorer APIs, and maybe writing some C++ unit tests  
<strong>\<sgp\_\></strong> I'm really interested to hear how these technical workshops go  
<strong>\<parasew\[m\]\></strong> very nice, sarang.  
<strong>\<sarang\></strong> Folks will get a chance to implement Schnorr sigs and some commitment code  
<strong>\<sarang\></strong> Otherwise, I continue to move forward on ring sig code/tests, some graph analysis that moves our spent-output work forward to examine complexity, etc  
<strong>\<sarang\></strong> Does anyone else have topics of interest to discuss or ask about? Or doing some work that's of interest to the group?  
<strong>\<suraeNoether\></strong> hey everyone, sorry for my delay  
<strong>\<sarang\></strong> np  
<strong>\<sarang\></strong> I just finished my brief updates  
<strong>\<sarang\></strong> This is a good place to jump in  
<strong>\<suraeNoether\></strong> well, this weekend I spent time on matching and churn and benchmarking the known traceability attacks on monero, and how to translate similar attacks on zcash into this framework  
<strong>\<suraeNoether\></strong> worked on the paper for that a bit  
<strong>\<suraeNoether\></strong> chatted with rehrar on the phone regarding the monero konferenco  
<strong>\<suraeNoether\></strong> i'm starting to reach out to speakers for formal invitations  
<strong>\<suraeNoether\></strong> aaaand yeah, slow weekend, i've been ill :(  
<strong>\<suraeNoether\></strong> i'll hopefully be pushing a bipartite graph-theoretic benchmarking tool some time this week  
<strong>\<suraeNoether\></strong> hopefully first draft of this benchmark paper will be available by end of november  
<strong>\<sarang\></strong> This graph matching work is quite excellent  
<strong>\<sarang\></strong> It links the complexity of determining possible spends with computational problems in graph theory  
<strong>\<suraeNoether\></strong> yeah, we're getting very good information on the raw computational effort and time an adversary would have to spend to "unravel" monero  
<strong>\<sarang\></strong> Can you elaborate on the tool?  
<strong>\<suraeNoether\></strong> sur  
<strong>\<suraeNoether\></strong> sure\*  
<strong>\<suraeNoether\></strong> the tool is essentially going to compute maximal matchings on randomly generated graphs of specified properties (like number of nodes, connectivity, etc) with the intent of estimating, ballpark, the constants associated with big-oh timing  
<strong>\<suraeNoether\></strong> for those of you unfamiliar: <https://en.wikipedia.org/wiki/Big\_O\_notation>  
<strong>\<sarang\></strong> Which algorithm(s) in particular?  
<strong>\<suraeNoether\></strong> <https://en.wikipedia.org/wiki/Hopcroft%E2%80%93Karp\_algorithm>  
<strong>\<sarang\></strong> great  
<strong>\<suraeNoether\></strong> so, essentially, finding an optimal matching under some null model is the same as finding a maximal matching of a related graph, which is the same as finding augmenting paths for existing matching, and all that boils down to...  
<strong>\<suraeNoether\></strong> breadth-first searches  
<strong>\<rehrar\></strong> you guys are the bees knees  
<strong>\<suraeNoether\></strong> so the idea is this  
<strong>\<sarang\></strong> Oh, a quick housekeeping note (lest I forget) that suraeNoether and I have an open funding request for an upcoming Stanford academic conference... and there are other open requests in need of support too: <https://forum.getmonero.org/8/funding-required>  
<strong>\<suraeNoether\></strong> if we can estimate a ballpark constant k such that it takes, worst-case, k\*r\*n^1.5 units of time to find a maximal matching on an r-regular bipartite graph with 2n nodes in it, using a dumb computer with a dumb algorithm that isn't parallelized, we can begin estimating what a large-scale perfect matching disclosure attack would do to Monero. (see here:  
<strong>\<suraeNoether\></strong> <https://link.springer.com/chapter/10.1007/978-3-540-70630-4\_2> )  
<strong>\<suraeNoether\></strong> this literally quantifies the urgency with which we need to replace ring signatures  
<strong>\<suraeNoether\></strong> i have some expectations of the results, but we'll see how it all unrolls  
<strong>\<suraeNoether\></strong> \*and for those who are interested\* that paper above is not one-to-one directly correlatable with Monero. comparing the results from that paper to our system is inappropriate for a handful of reasons  
<strong>\<suraeNoether\></strong> if anything, that paper seems more related to "what would happen if we did a fluffypony styled 30-day timed zcash sidechain?"  
<strong>\<sarang\></strong> but it's a great first approach  
<strong>\<suraeNoether\></strong> yeah, and i'm eager to apply the results therein with the zcash turnstile  
<strong>\<fluffypony\></strong> what's the zcash turnstile? I haven't been following recently with the CLI and GUI releases  
<strong>\<sarang\></strong> You can't go sprout to sapling  
<strong>\<sarang\></strong> you have to sent to transparent, and then to sapling  
<strong>\<suraeNoether\></strong> yep: sprout -\> transparent -\> sapling  
<strong>\<sarang\></strong> They plan to release a tool to help users not fuck it up, but I hear it won't be out for a couple months  
<strong>\<sarang\></strong> IMO it's a terrible idea to do it this way  
<strong>\<sarang\></strong> They call it "turnstile" to make it seem like Fancy Moon Math  
<strong>\<suraeNoether\></strong> nah, they called it that for auditing reasons  
<strong>\<sarang\></strong> Oh, I know why they want it  
<strong>\<suraeNoether\></strong> they want to demonstrate exactly as many zcash exist as intended  
<strong>\<sarang\></strong> but it's a terrible idea and the name softens it  
<strong>\<suraeNoether\></strong> security be damned, i guess. :P  
<strong>\<sarang\></strong> Not offering users help in doing it safely is dumb as rocks  
<strong>\<binaryFate\></strong> auditing reasons is an admission you don't trust your math/implementation  
<strong>\<gmaxwell\></strong> it's an implicit admission that they could be inflated...  
<strong>\<sarang\></strong> I did hear that they're backing off the "eventually make sprout unspendable" bandwagon  
<strong>\<sarang\></strong> so that's good  
<strong>\<sarang\></strong> (that was also dumb as rocks IMO)  
<strong>\<suraeNoether\></strong> agreed  
<strong>\<suraeNoether\></strong> anyway  
<strong>\<sgp\_\></strong> I offered to help them mitigate turnstile privacy loss. We'll see how good we can get, but it will be a bloodbath no matter what, especially since many people have already transitioned  
<strong>\<gmaxwell\></strong> thats a pretty big albatross though... an extra gigabyte of key data wallets need ot have to support it?  
<strong>\<sarang\></strong> They should have released the tool and clear instructions to use it  
<strong>\<sarang\></strong> gmaxwell: I consider deprecation of spend ability to be a huge violation of the "social contract" of the asset  
<strong>\<suraeNoether\></strong> sarang i'm not sure if they've backed off of that. saw zooko brag about backwards incompatibility on twitter. :P  
<strong>\<sarang\></strong> Ugh, I had read that they were \_not\_ looking toward deprecation. Boo  
<strong>\<binaryFate\></strong> ring signatures for turnstile would help and keep auditing possible :P  
<strong>\<suraeNoether\></strong> anyway, this is off-topic for the research meeting BUT point of the matter is that a modified version of the matching game applies to zcash and it's made more interesting by adding the existence of a second shielded pool  
<strong>\<suraeNoether\></strong> binaryFate: +1  
<strong>\<suraeNoether\></strong> i would invest in zcash and put it all into the sapling shielded pool, but i wouldn't be able to be confident they'll deprecate \*that\* shielded pool and force me through a transparent pool again in the future  
<strong>\<suraeNoether\></strong> they can promise that they are abandoning their transparent pool all they like  
<strong>\<suraeNoether\></strong> i'll believe it when i see it  
<strong>\<sarang\></strong> sure  
<strong>\<suraeNoether\></strong> seriously off topic  
<strong>\<sarang\></strong> But good to keep in mind our goals relative to what's happening in this space  
<strong>\<sarang\></strong> noooo  
<strong>\<sarang\></strong> -lounge  
<strong>\<sarang\></strong> Anyone else with Fun Things to share?  
<strong>\<rehrar\></strong> \#monero-too-many-rooms-discussion  
<strong>\<sarang\></strong> stahp  
<strong>\<suraeNoether\></strong> i tried to get \#monero-recipes off the ground, but noooo  
<strong>\<suraeNoether\></strong> ok, i guess unless folks have more to talk about  
<strong>\<suraeNoether\></strong> we can call this a /meeting
