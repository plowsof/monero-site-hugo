---
title: Logs for the MRL Meeting Held on 2020-02-19
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> OK, let’s get started with the meeting  
<strong>\<sarang\></strong> GREETINGS  
<strong>\<sgp\_\></strong> hello :)  
<strong>\<n3ptune\></strong> Hello  
<strong>\<needmonero90\></strong> I caught the meeting\!  
<strong>\<needmonero90\></strong> I would like to note that the meetings are not listed in the calendar  
<strong>\<needmonero90\></strong> idk if thats intentional  
<strong>\<sarang\></strong> Which calendar?  
<strong>\<UkoeHB\_\></strong> Hi  
<strong>\<sarang\></strong> And how are meetings applied to it?  
<strong>\<ArticMine\></strong> Hi  
<strong>\<sarang\></strong> Meeting times/agendas are always listed as meta repo github issues  
<strong>\<sarang\></strong> Anyway, does anyone wish to begin the ROUNDTABLE with research topics of interest?  
<strong>\<UkoeHB\_\></strong> Yes  
<strong>\<sarang\></strong> Take it away UkoeHB\_  
<strong>\<UkoeHB\_\></strong> I finished designing an escrowed marketplace ‘protocol’ which hopefully solves issues encountered by rbrunner in his openbazaar integration analysis. Also, multisig and txtangle have been finalized.  
<strong>\<UkoeHB\_\></strong> <https://www.pdf-archive.com/2020/02/19/zerotomoneromaster-v1-0-28/zerotomoneromaster-v1-0-28.pdf>  
<strong>\<sarang\></strong> Neat  
<strong>\<UkoeHB\_\></strong> Finally, I had an idea for reducing minimum fee variability, and likewise for putting antispam directly in the protocol instead of relying on minimum fee  
<strong>\<sarang\></strong> Are you seeking analysis on those?  
<strong>\<UkoeHB\_\></strong> Which is issue \#70  
<strong>\<UkoeHB\_\></strong> They are open for comments any time anywhere  
<strong>\<UkoeHB\_\></strong> Ah and sarang provided a draft for a tx knowledge proof chapter  
<strong>\<sarang\></strong> aye  
<strong>\<UkoeHB\_\></strong> (not really my research :p)  
<strong>\<sarang\></strong> Heh, it’s more of a summary of what’s in the codebase (and some changes)  
<strong>\<sarang\></strong> I look forward to reading the update draft you linked  
<strong>\<UkoeHB\_\></strong> A number of topics here are lonely and want attention btw <https://github.com/monero-project/research-lab/issues>  
<strong>\<UkoeHB\_\></strong> \\end  
<strong>\<sarang\></strong> Thanks UkoeHB\_  
<strong>\<sarang\></strong> Any questions or comments on those topics from anyone?  
<strong>\<ArticMine\></strong> Yes  
<strong>\<sarang\></strong> Please go ahead\!  
<strong>\<ArticMine\></strong> I have taken a look at issue 70  
<strong>\<ArticMine\></strong> It actually has serious implications  
<strong>\<ArticMine\></strong> When the LT medium increases substantially  
<strong>\<ArticMine\></strong> I do have an idea for a solution  
<strong>\<ArticMine\></strong> Very preliminary at this stage  
<strong>\<ArticMine\></strong> As for an interim fix  
<strong>\<ArticMine\></strong> The est is to pay the high or at least normal fee for escrows that are expected to last past the next hard fork  
<strong>\<ArticMine\></strong> I will have comments on the issue in the next two weeks  
<strong>\<ArticMine\></strong> end  
<strong>\<sarang\></strong> Thanks ArticMine  
<strong>\<sarang\></strong> Any other questions/comments from the topics presented by UkoeHB\_?  
<strong>\<sarang\></strong> Righto  
<strong>\<sarang\></strong> I’ll share a few things  
<strong>\<sarang\></strong> First, the Stanford Blockchain Conference is happening right now (and the next couple of days), and has streaming available: <https://cbr.stanford.edu/sbc20/>  
<strong>\<sarang\></strong> Second, I did some math/code related to multiparty stuff for next-gen protocols  
<strong>\<sarang\></strong> Third, I worked on code and write-ups for transaction proofs, both for an updated PR and for inclusion in Zero to Monero for better documentation  
<strong>\<sarang\></strong> Fourth, I used chain data from n3ptune and friends to do better estimates of the cumulative effects of next-gen protocols  
<strong>\<sarang\></strong> both in chain growth and verification time  
<strong>\<sarang\></strong> Major caveat: these assume the same input/output distribution as the current chain, and are \_estimates\_only\_  
<strong>\<sarang\></strong> and apply to post-bulletproof chain data only  
<strong>\<sarang\></strong> <https://usercontent.irccloud-cdn.com/file/ijaEAI7m/size.png>  
<strong>\<sarang\></strong> ^ this link shows the total chain growth estimates for various protocols with varying ring size  
<strong>\<sarang\></strong> namely, from 16 to 1024 in powers of 2 (lines for visual aid only)  
<strong>\<UkoeHB\_\></strong> Sarang would you mind adding an indicator for MLSAG and CLSAG at the 11 ring size ‘point’? For reference  
<strong>\<sarang\></strong> Sure, let me grab that data from my spreadsheet  
<strong>\<sarang\></strong> hold please  
<strong>\<UkoeHB\_\></strong> Or the super steep slope from 11 to 20 lol that goes off that chart  
<strong>\<sarang\></strong> Heh, I had that data but didn’t include it since it’s crazy linear  
<strong>\<sarang\></strong> I’m running the N=11 code for MLSAG/CLSAG, which I don’t have handy  
<strong>\<sarang\></strong> Anyway, I’ll pull up the time data while we wait  
<strong>\<sarang\></strong> <https://usercontent.irccloud-cdn.com/file/T7uWoFEp/time.png>  
<strong>\<sarang\></strong> ^ verification time estimate for \_group\_operations\_only\_ at varying ring sizes  
<strong>\<UkoeHB\_\></strong> I think it’s interesting that all these protocols/signature schemes are similar size on the small end  
<strong>\<sarang\></strong> All the verification times are linear (up to a logarithmic term due to multiexp)  
<strong>\<UkoeHB\_\></strong> Where is tryptich multi hiding?  
<strong>\<sarang\></strong> It’s underneath Triptych-single  
<strong>\<sarang\></strong> They’re essentially indistinguishable  
<strong>\<selsta\></strong> Does Triptych single have advantages over multi?  
<strong>\<sarang\></strong> RCT3-multi suffers due to input padding requirements that still have a linear verification effect  
<strong>\<sarang\></strong> selsta: a complete soundness proof :)  
<strong>\<sarang\></strong> Update on MLSAG/CLSAG size estimates…  
<strong>\<UkoeHB\_\></strong> Could you make a smaller graph from 0 to 128 ring size? Since those large ones seem pretty unreasonable  
<strong>\<sarang\></strong> At N=11, MLSAG for that chain range is 7.84 GB, while CLSAG is 5.84 GB  
<strong>\<sarang\></strong> (the actual size of that chain range is 7.9 GB)  
<strong>\<sarang\></strong> <https://usercontent.irccloud-cdn.com/file/DFhClmEe/time-small.png>  
<strong>\<sarang\></strong> ^ same time data, zoomed in  
<strong>\<UkoeHB\_\></strong> Perfect thanks :) are time estimates for CLSAG/MLSAG available?  
<strong>\<sarang\></strong> Heh, just writing that out  
<strong>\<sarang\></strong> I have very early estimates on that, which are tricky since multiexp doesn’t apply, and hashing is nontrivial  
<strong>\<sarang\></strong> MLSAG N=11 estimate is 29.9 hours for that chain range (but I have \_not\_ double-checked it)  
<strong>\<ArticMine\></strong> What hardware was used for the verification time calculations?  
<strong>\<sarang\></strong> It’s a single core on a 2.1 GHz Opteron machine, with a bonkers amount of RAM  
<strong>\<sarang\></strong> I would rely on the timing data only for comparisons, not absolute values  
<strong>\<ArticMine\></strong> age of CPU?  
<strong>\<sarang\></strong> I am still in the process of getting CLSAG data, which requires additional test code  
<strong>\<sarang\></strong> It’s a gen-3 Opteron, if that’s what you mean  
<strong>\<UkoeHB\_\></strong> Is there a way others could run the same tests?  
<strong>\<sarang\></strong> Again, only estimates using performance test code  
<strong>\<sarang\></strong> For next-gen protocols, it’s quite easy  
<strong>\<ArticMine\></strong> Yes great it does give an idea thanks  
<strong>\<sarang\></strong> Well, somewhat easy  
<strong>\<sarang\></strong> You need to get multiexp performance timing data and use a linear interpolation that you plug into the simulator  
<strong>\<sarang\></strong> For MSLAG/CLSAG you need to run more operation performance data  
<strong>\<sarang\></strong> This is the simulator, which is still WIP: <https://github.com/SarangNoether/skunkworks/blob/sublinear/estimate.py>  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/HuPcfLdT/image.png>  
<strong>\<sarang\></strong> But again, it’s tricky to do comparisons between MLSAG/CLSAG and the next-gens  
<strong>\<Isthmus\></strong> (drive by data)  
<strong>\<sarang\></strong> Wow, that’s quite low  
<strong>\<Isthmus\></strong> Oh yeah, the numbers are one thing. But moreso, we should all be more alarmed that analyzing something like this is possible for an outside observer  
<strong>\<Isthmus\></strong> ;-)  
<strong>\<sarang\></strong> Yep, and has certainly been a topic of interest\!  
<strong>\<Isthmus\></strong> It’s a privacy risk to use subaddresses right now…  
<strong>\<Isthmus\></strong> Anyways, I gotta bounce, sorry to spam n run  
<strong>\<sarang\></strong> OK thanks for sharing the data Isthmus  
<strong>\<sarang\></strong> Another good reminder that I/O structure reveals some information about subaddress use  
<strong>\<sarang\></strong> Since Isthmus had to leave, were there other questions/comments on the data that I shared above?  
<strong>\<sarang\></strong> UkoeHB\_: if you want to run tests as well, let me know after the meeting and I can let you know how to get the numbers you’ll need  
<strong>\<UkoeHB\_\></strong> My computer is quite weak, was just asking for viewers :)  
<strong>\<sgp\_\></strong> sarang: can you remind us on the plans to fix this subaddress thing?  
<strong>\<sarang\></strong> ah ok  
<strong>\<sarang\></strong> Requiring separate tx keys per output is a good idea, but IIRC didn’t have a huge amount of support when last brought up  
<strong>\<sarang\></strong> FWIW the size data that I presented for next-gens assumes a separate tx key per output  
<strong>\<UkoeHB\_\></strong> Is that necessary for the protocols?  
<strong>\<sarang\></strong> For the proving systems, you mean? No, not at all  
<strong>\<sarang\></strong> They don’t care how you get signing keys  
<strong>\<UkoeHB\_\></strong> Can you estimate the amount of additional pub key data? Num outs \* 32 and num tx \* 32?  
<strong>\<sgp\_\></strong> sarang: why did it not get support now? complexity? size? verification time?  
<strong>\<sarang\></strong> My numbers for MLSAG/CLSAG include separate tx keys too\!  
<strong>\<sarang\></strong> Also: n3ptune’s dataset includes the pubkey counts  
<strong>\<sarang\></strong> So I could run that separately for a more direct count  
<strong>\<UkoeHB\_\></strong> With only 3% subaddress adoption, the difference is likely on the order of 100MB  
<strong>\<UkoeHB\_\></strong> Or 2% of total size I think  
<strong>\<sarang\></strong> that’s probably a good order-of-magnitude estimate  
<strong>\<sarang\></strong> But IIRC scanning requires checking all pubkeys  
<strong>\<sarang\></strong> So either there needs to be a specified correlation, or there’s added complexity in scanning  
<strong>\<UkoeHB\_\></strong> I think it costs \~1GB for 30mill pub keys btw  
<strong>\<sarang\></strong> I think moneromooo had a better idea of the impacts, when it was brought up earlier  
<strong>\<sarang\></strong> FWIW I think it’s a good idea unless it’s very compelling not to due to complexity  
<strong>\<sarang\></strong> OK, we’re running up to the one-hour mark…  
<strong>\<sgp\_\></strong> obviously without this change, the impacts are quite negative for network privacy…  
<strong>\<sarang\></strong> It’s differentiated data, but it doesn’t leak \_which\_ outputs are subaddress-destined  
<strong>\<sarang\></strong> (not that I’m saying that’s a good reason to keep the current approach)  
<strong>\<UkoeHB\_\></strong> It’s quite a lot of unused data, I’m a bit skeptical  
<strong>\<sgp\_\></strong> just reveals “one of this outputs goes to a subaddres?”  
<strong>\<sarang\></strong> UkoeHB\_:?  
<strong>\<UkoeHB\_\></strong> A lot of dummy data  
<strong>\<sarang\></strong> sgp\_: it reveals the number of subaddress outputs  
<strong>\<UkoeHB\_\></strong> sarang all it reveals is at least one of the outputs must be to a subaddress  
<strong>\<sarang\></strong> Doesn’t it reveal the total number of sub outs?  
<strong>\<UkoeHB\_\></strong> No  
<strong>\<sarang\></strong> orly  
<strong>\<UkoeHB\_\></strong> How would it?  
<strong>\<UkoeHB\_\></strong> Number of additional pub keys always equals number of outs  
<strong>\<UkoeHB\_\></strong> Even if nonsubaddress  
<strong>\<UkoeHB\_\></strong> How is the CLSAG paper going?  
<strong>\<sarang\></strong> Hmm, for some reason I thought otherwise; noted  
<strong>\<sarang\></strong> I’m still waiting for suraeNoether  
<strong>\<sarang\></strong> He wanted to continue working on his ideas for the security model  
<strong>\<sarang\></strong> So unfortunately I am not the one to ask  
<strong>\<sarang\></strong> OK, is there anything else of interest to share?  
<strong>\<sarang\></strong> (Would be a good idea to continue discussing this after meeting, or on an issue, to keep it alive)  
<strong>\<sgp\_\></strong> definitely need an issue for it  
<strong>\<sarang\></strong> All righty then; thanks to everyone for attending today  
<strong>\<sarang\></strong> We are adjourned\!
