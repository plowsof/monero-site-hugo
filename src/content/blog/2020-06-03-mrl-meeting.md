---
title: Logs for the MRL Meeting Held on 2020-06-03
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> OK, let's get started\!  
<strong>\<sarang\></strong> First, GREETINGS  
<strong>\<sarang\></strong> hello  
<strong>\<ArticMine\></strong> Hi  
<strong>\<dEBRUYNE\></strong> hi  
<strong>\<hyc\></strong> hey  
<strong>\<Isthmus\></strong> Heyo  
<strong>\<sarang\></strong> Next up, ROUNDTABLE, where anyone is welcome to share research of general interest  
<strong>\<sarang\></strong> I have a few topics of interest  
<strong>\<sarang\></strong> The recent preprint from CMU student researchers on transaction tracing has been updated to reflect suggestions and corrections: <https://eprint.iacr.org/2020/593>  
<strong>\<binaryFate\></strong> hello  
<strong>\<sarang\></strong> The researchers still claim that a small but nonzero number of post-changeover (i.e. the RingCT protocol switch) transactions were traceable, which didn't correspond with other numbers I'd found  
<strong>\<sarang\></strong> So I decided to independently run the same analysis and compare  
<strong>\<sarang\></strong> I ran updated numbers that account for all transactions up to the beginning of this week  
<strong>\<sarang\></strong> If you run a full chain-reaction-type analysis, there are 7303 transactions after the changeover containing at least one deducible input  
<strong>\<sarang\></strong> However  
<strong>\<sarang\></strong> All of those transactions spend pre-changeover outputs  
<strong>\<sarang\></strong> So if you filter out all transactions that aren't CT-in-CT-out, there are still precisely 0 deducible transactions/inputs  
<strong>\<sarang\></strong> But wait, there's more\!  
<strong>\<sarang\></strong> The preprint also tries to determine how effective the guess-newest age heuristic is against modern transactions  
<strong>\<sarang\></strong> Unfortunately, it uses those 7303 (or however many were in their block range) deducible post-changeover transactions as ground truth  
<strong>\<sarang\></strong> and assumes that holds for all post-changeover transactions  
<strong>\<binaryFate\></strong> huh that's pretty dumb  
<strong>\<sarang\></strong> I wouldn't say it's dumb; it just failed to account for transaction types  
<strong>\<ArticMine\></strong> So the key here is RingCT  
<strong>\<sarang\></strong> Because there are "full-CT" transactions post-changeover that are deducible, the entirety of their ground-truth data set is based on spends of old funds, for which the modern selection algorithm does not apply  
<strong>\<sarang\></strong> But there is an interesting twist  
<strong>\<dEBRUYNE\></strong> To be clear, it concerns transactions were non-RingCT outputs are essentially converted to RingCT outputs, right?  
<strong>\<sarang\></strong> Among that ground-truth data set, the researchers find those transactions are \_still\_ twice as good against guess-newest from Miller et al.\!  
<strong>\<sarang\></strong> dEBRUYNE: yes, or that aren't converted to CT at all  
<strong>\<sarang\></strong> (very limited cases involving single inputs)  
<strong>\<moneromooo\></strong> \> Because there are "full-CT" transactions post-changeover that are deducible,  
<strong>\<moneromooo\></strong> Forgot a no, right ?  
<strong>\<sarang\></strong> Correct, thank you  
<strong>\<sarang\></strong> because there are NO full-CT post-changeover that are deducible (typo)  
<strong>\<dEBRUYNE\></strong> sarang: Thanks, I guess those are dust outputs then that first have to be converted to standardized outputs  
<strong>\<dEBRUYNE\></strong> dust or non-mixable  
<strong>\<sarang\></strong> So the conclusions presented in the paper about transaction counts aren't wrong, but don't differentiate between type, which I think is very important  
<strong>\<sarang\></strong> The conclusions about guess-newest are only valid for their ground-truth set, and cannot be extrapolated to CT transactions  
<strong>\<binaryFate\></strong> The wallet warns you when you spend old outputs that privacy is lessen and it's known you should churn in that case. It should absolutely be mentioned in their paper that these transactions are particular and users are fully informed of the risk  
<strong>\<sarang\></strong> I'm drafting an email to the authors to let them know of this, should they wish to revise again  
<strong>\<sarang\></strong> They were very prompt in responding to my earlier email, and very quickly revised, which was great  
<strong>\<sarang\></strong> Now that I have a complete deduced data set, I'm checking their results on effective anonymity sets of non-deduced transactions  
<strong>\<sarang\></strong> I want to separate those by transaction type as well  
<strong>\<sarang\></strong> Even though the preprint had errors, I'm glad they did the research  
<strong>\<sarang\></strong> We should encourage student researchers  
<strong>\<binaryFate\></strong> I'm unclear on the guess-newhest on this dataset  
<strong>\<sarang\></strong> How so?  
<strong>\<binaryFate\></strong> Since this dataset is specifically about real output being old, shouldn't that give very specific results when seeing how the heuristic performs, that can't be extended to other transactions?  
<strong>\<sarang\></strong> Yes  
<strong>\<sarang\></strong> That's what I was saying earlier  
<strong>\<sarang\></strong> They assumed their ground-truth post-changeover dataset was representative of all post-changeover transactions, which is entirely false  
<strong>\<UkoeHB\_\></strong> pre-ringCT inputs could be used in rings just like modern coinbase outputs are, which makes me sad  
\<= Yes, because uninformed readers may infer that it concerns full RingCT transactions  
<strong>\<binaryFate\></strong> IIRC the decoy selection algorithm is very different for these transactions, only selecting non-ringct. Since all of them are very old, they are old on the tail of the gamma distribution, very different from recent one  
<strong>\<moneromooo\></strong> Using pre-ringct outs as fake outs would help shortly after ringct, but would otherwise introduce a number of known spent outs in rings.  
<strong>\<binaryFate\></strong> \*they are all  
<strong>\<sarang\></strong> When I finish the effective anonymity data, it should give a much more clear picture of the status of modern transactions (before and after ring increases too)  
<strong>\<sarang\></strong> The code still needs some cleanup to make it easier for others to run this analysis, either now or in the future  
<strong>\<UkoeHB\_\></strong> interesting point moneromooo  
<strong>\<sarang\></strong> thanks to gingeropolous for the use of a fast machine for this analysis  
<strong>\<sarang\></strong> If the researchers choose not to revise, I can always write a new preprint that presents this data  
<strong>\<sarang\></strong> but I strongly suspect the researchers will revise again, since they did a very prompt first revision  
<strong>\<binaryFate\></strong> super cool that you checked all these results  
<strong>\<hyc\></strong> sounds great  
<strong>\<sarang\></strong> I can also post the raw data for the post-changeover deducible transactions, in case anyone wants to specifically analyze them  
<strong>\<hyc\></strong> super cool that their work is pulblicly reproducible  
<strong>\<sarang\></strong> Again, I'm really glad they did the analysis  
<strong>\<sarang\></strong> Yeah, I didn't end up using their Java code though  
<strong>\<sarang\></strong> I wanted some extra data they didn't provide, so I rewrote  
<strong>\<sarang\></strong> but kudos to them for making all their code public, for sure  
<strong>\<UkoeHB\_\></strong> I'd like to see if the code can be adapted to a certain analysis I have in mind, so I'm looking forward to it  
<strong>\<moneromooo\></strong> Not really. More like negative kudos for those that don't.  
<strong>\<sarang\></strong> What analysis is that UkoeHB\_?  
<strong>\<hyc\></strong> moneromooo: yes but that still tends to be the majority these days  
<strong>\<moneromooo\></strong> Papers without it are really hearsay. Should never be published.  
<strong>\<UkoeHB\_\></strong> getting data on ring loops, and comparing to a purely randomly generated ring db  
<strong>\<sarang\></strong> Define ring loop  
<strong>\<hyc\></strong> moneromooo: agreed  
<strong>\<moneromooo\></strong> A ring is a circular construct. A loop is.... a.......  
<strong>\<UkoeHB\_\></strong> e.g. two outputs are owned by the same person, a loop is when their descendents intersect in the same tx  
<strong>\<sarang\></strong> Oh, output merging  
<strong>\<sarang\></strong> ?  
<strong>\<moneromooo\></strong> Can happen by chance too (from fake outs).  
<strong>\<sarang\></strong> yes  
<strong>\<UkoeHB\_\></strong> yeah basically, so I want to see the probability of given loop sizes happening randomly  
<strong>\<sarang\></strong> I think the question is how likely it is to occur in practice vs not  
<strong>\<Isthmus\></strong> @UkoeHB\_ important research. Results will be probably be depressing :- (  
<strong>\<moneromooo\></strong> If it was super fast, it'd be nice for the wallet to try and pick fake outs that generate "false positives".  
<strong>\<sarang\></strong> There's code that will do forms of merge analysis, and it's something I have to add specifically to my check code  
<strong>\<sarang\></strong> The graphs involved are likely quite large, so it isn't clear what the complexity of this is  
\<  
<strong>\<sarang\></strong> FWIW the early analysis on output merging used deducible transactions only  
<strong>\<UkoeHB\_\></strong> right, I have some ideas about limiting the output range to first estimate exactly how long such analysis would take; can also limit the maximum loop size considered  
<strong>\<Isthmus\></strong> UkoeHB\_: to generate random data set, will have to select guesstimates for parameters like number of transactions per wallet. (really, would be a distribution, not single value)  
<strong>\<sarang\></strong> yes  
<strong>\<Isthmus\></strong> The interesting thing is that we may be able to establish statistical estimates of these parameterss based on the real blockchain data  
<strong>\<UkoeHB\_\></strong> Isthmus we can just use the transactions that already exist, but make the input rings randomly selected; this provides a direct comparison with the real ring db  
<strong>\<Isthmus\></strong> Especially if rare "natural" occurrence, i.e. low false positive rate  
<strong>\<sarang\></strong> This sort of analysis was considered as a major part of the churn framework as well  
<strong>\<UkoeHB\_\></strong> and do the randomly generated analysis multiple times for variance  
<strong>\<Isthmus\></strong> Makes sense  
<strong>\<sarang\></strong> Anyway, I've taken up a lot of time on that  
<strong>\<sarang\></strong> Was there other research of interest to discuss from anyone?  
<strong>\<Isthmus\></strong> I'll be interested in seeing plots where x-axis is \# of txns made within a given wallet, and y-axis is statistical measures, like precision/accuracy/etc  
<strong>\<Isthmus\></strong> I have a few quick updates  
<strong>\<Isthmus\></strong> I’ve been doing some p2p network scalability research, creating some testing suites, etc. Still very early reading/planning, but hopefully will have some actionable insights for Monero.  
<strong>\<UkoeHB\_\></strong> yes it's a big project and might be worthy of a paper if it goes somewhere, we will see; I also want to see how well the gamma distribution is working by subtracting the theoretical distribution from what we have in reality  
\< YES PLEASE  
<strong>\<Isthmus\></strong> @UkoeHB\_ I have some algorithms floating around GitHub to identify and filter txns that use uniform decoy selection instead of correct algo. If you don't strip those out, it will introduce a bias in your results towards older oututs  
<strong>\<Isthmus\></strong> I'll dig those up and send links  
<strong>\<UkoeHB\_\></strong> cool thanks  
<strong>\<sarang\></strong> Yeah, trying to exclude old software will be important  
<strong>\<sarang\></strong> since there's no consensus enforcement  
<strong>\<UkoeHB\_\></strong> I think ring analysis is too scary for anyone to tackle alone, so a collaborative and incremental effort seems reliable  
<strong>\<Isthmus\></strong> Software can't be any older than the last ring size change, right?  
<strong>\<sarang\></strong> Sorry, I meant software using old/incorrect methods  
<strong>\<sarang\></strong> "nonstandard" is a better term  
<strong>\<sarang\></strong> A big reason why deterministic input sets are intriguing is because they're likely to contain many outputs from the same transactions  
<strong>\<sarang\></strong> and therefore are included as a "standard feature" of all rings  
<strong>\<binaryFate\></strong> "see how well the gamma distribution is working by subtracting the theoretical distribution from what we have in reality" I was doing stuff in that direction too, exciting\!  
<strong>\<UkoeHB\_\></strong> I think I missed the last meeting. The Janus proposal was updated a week ago (<https://github.com/monero-project/monero/issues/6456>), and now the Janus mitigation is to encode the tx private key for recipients. For 2-out tx where there will only be 1 tx pub key, the 'change output' would use a 'hidden tx pub key' derived from the non-change recipient's encoded tx private key. An alternative would be for the  
<strong>\<UkoeHB\_\></strong> change output to use a unique 'derivation to scalar', however I am concerned that affects too much protocol-level code (could be wrong).  
<strong>\<binaryFate\></strong> What happens where there is a 2-out tx but none of them is change?  
<strong>\<Isthmus\></strong> I think you have to make a 3  
<strong>\<Isthmus\></strong> 3-output then?  
<strong>\<UkoeHB\_\></strong> The proposal is to enforce 1 tx pub key for 2-outs, and 1 key per output for \>2-outs. All tx with no change output would have to be \>2-out, even if it means adding a dummy output.  
<strong>\<moneromooo\></strong> A 0 change is automatically added \*only\* if there's one output otherwise.  
<strong>\<UkoeHB\_\></strong> Right, and following the proposal there would be a very rare case of 2 non-change outs needing a dummy  
<strong>\<Isthmus\></strong> It's an edge case, so I perceive this as a reasonable solution  
<strong>\<UkoeHB\_\></strong> Originally encoding the tx private key was disregarded since current tx share tx pub keys, but since we'd start enforcing more tx pub keys that problem is solved.  
<strong>\<UkoeHB\_\></strong> i.e. as a solution for Janus\*  
<strong>\<UkoeHB\_\></strong> Well, the hidden tx pub key might be unnecessary now that I think about it.. anyway that's my dusty update.  
<strong>\<ArticMine\></strong> but does this means that a 2 out tx always has change real or dummy  
<strong>\<UkoeHB\_\></strong> yes  
<strong>\<ArticMine\></strong> Can this then be attacked?  
<strong>\<UkoeHB\_\></strong> the idea that there is always a change output in 2-out tx? that assumption can be made today already  
<strong>\<Isthmus\></strong> Oh no wait, it would just move the issue to n+1  
<strong>\<sarang\></strong> Sorry, connection problems; back now  
<strong>\<ArticMine\></strong> but not with 100% certainty  
<strong>\<UkoeHB\_\></strong> well the shenanigans around 2-out tx are mostly to optimize scanning and tx sizes, since 2-out tx are \~95% of tx  
<strong>\<UkoeHB\_\></strong> that's true ArticMine  
<strong>\<luigi1111w\></strong> one can assume with high certainty that every transaction contains a change output. I don't understand why that's a significant observation.  
<strong>\<Isthmus\></strong> Most txns. Churn doesn't, for example.  
<strong>\<sarang\></strong> ^  
<strong>\<moneromooo\></strong> Why does it not ?  
<strong>\<sarang\></strong> Doesn't have to  
<strong>\<sarang\></strong> And would affect output merging later  
<strong>\<moneromooo\></strong> Well, that's circular reasoning then.  
<strong>\<Isthmus\></strong> Churning with change creates the loops UkoeHB\_ mentioned earlier  
<strong>\<luigi1111w\></strong> churn has two change outputs, no?  
<strong>\<ArticMine\></strong> It can  
<strong>\<luigi1111w\></strong> or one and a fake one  
<strong>\<UkoeHB\_\></strong> churn has an 'output to yourself' and a 'change output'; change outputs are handled differently in the code  
<strong>\<luigi1111w\></strong> sure but this is from a network perspective  
<strong>\<UkoeHB\_\></strong> yeah  
<strong>\<ArticMine\></strong> Or a split 2 separate wallets under the control of one person  
<strong>\<ArticMine\></strong> It introduces uncertainty  
<strong>\<luigi1111w\></strong> but why does it matter?  
<strong>\<ArticMine\></strong> because even a small bias can grow.  
<strong>\<sarang\></strong> Given the time, is there other research that needs to be brought up before adjourning?  
<strong>\<Isthmus\></strong> I've got 2 updates, will keep brief for sake of time:  
<strong>\<Isthmus\></strong> Our CCS for researching Monero’s post-quantum security is sooooooo close. Only 7% left, less than 40 XMR needed. <https://ccs.getmonero.org/proposals/research-post-quantum-monero.html>  
<strong>\<Isthmus\></strong> If that could get topped off today, we’ll dive in immediately and have our first update at next week’s MRL meeting. :- )  
<strong>\<Isthmus\></strong> Unrelated - I also have one of Insight’s DistSys engineers buildling “speedup” networks, i.e. highly-connected peers with high bandwidth to propagate blocks/txns through the ad hoc network faster than organic propagation. Main goal is to eliminate the long tail in block propagation times.  
<strong>\<Isthmus\></strong> The codebase is very modular with Terraform/ansible deployment and control scripts, so could be configured to spin up a Monero speedup network in the future.  
<strong>\<Isthmus\></strong> That's all from me.  
<strong>\<sarang\></strong> Nice\!  
<strong>\<sarang\></strong> I suppose I should mention that I welcome/request comments/questions/emoji on my funding proposal as well, so a decision can be made whether to open it: <https://repo.getmonero.org/monero-project/ccs-proposals/-/merge\_requests/148>  
<strong>\<luigi1111w\></strong> thanks for opening it well in advance  
<strong>\<sarang\></strong> OK, I suppose we can formally adjourn for the sake of logging  
<strong>\<sarang\></strong> Thanks to everyone for joining in today  
<strong>\<sarang\></strong> Discussion can of course continue\!
