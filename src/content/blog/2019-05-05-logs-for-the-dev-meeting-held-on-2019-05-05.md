---
title: Overview and Logs for the Dev Meeting Held on 2019-05-05
summary: Development status, Code & ticket discussion, and miscellaneous
tags: [dev diaries, core, crypto]
author: el00ruobuob / rehrar
---

# Logs

<strong>\<xmrmatterbridge\> \<rehrar\></strong> Meeting?  
<strong>\<rbrunner\></strong> It would be time for one, yes  
<strong>\<rehrar\></strong> 1. Meetings Greetings  
<strong>\<rehrar\></strong> h'lo  
<strong>\<moneromooo\></strong> We're waiting for 5509 to be finished before branching.  
<strong>\<rehrar\></strong> that's how moneromooo always says hello, don't worry  
<strong>\<hyc\></strong> hi  
<strong>\<rehrar\></strong> 2. What's been done since the previous meeting?  
<strong>\<rbrunner\></strong> ... a month ago, if I remember correctly  
<strong>\<rehrar\></strong> Something like that. :P So in theory at least a few things got done.  
<strong>\<rehrar\></strong> is dsc\_ dEBRUYNE selsta around give a gui update?  
<strong>\<rehrar\></strong> and maybe moneromooo can say something, although he kind of did already  
<strong>\<moneromooo\></strong> hi  
<strong>\<dEBRUYNE\></strong> I am here  
<strong>\<dEBRUYNE\></strong> Suppose I can give a quick GUI update  
<strong>\<rehrar\></strong> please do  
<strong>\<dEBRUYNE\></strong> The white theme got merged finally\! It also includes a lot of other UI improvements  
<strong>\<dEBRUYNE\></strong> Trezor support has been finalized  
<strong>\<dEBRUYNE\></strong> We've also updated the QT version to 5.9.7, because QT 5.7 was kind of holding us back due to a few bugs being present in it  
<strong>\<dEBRUYNE\></strong> Also QT 5.9.7 allows us to use more features etc.  
<strong>\<dEBRUYNE\></strong> An update popup was also implemented, it basically checks whether a new version is available and shows a little pop up if yes  
<strong>\<dEBRUYNE\></strong> Fiat pricing will also be merged soon^tm, note that it will be turned off by default  
<strong>\<dEBRUYNE\></strong> Update popup can be seen here fwiw -\> <https://github.com/monero-project/monero-gui/pull/2100>  
<strong>\<dEBRUYNE\></strong> Other than that, the usual lots of optimizations and bug fixes :P  
<strong>\<dEBRUYNE\></strong> We're essentially ready for the upcoming release too  
<strong>\<dEBRUYNE\></strong> Just need to merge a few remaining PRs, wait for the translations, and do some testing  
<strong>\<dEBRUYNE\></strong> That's kind of it I guess :p  
<strong>\<dEBRUYNE\></strong> Oh one more thing, for 0.15 we'll be revamping the send page / flow to make it more intuitive -\> <https://github.com/monero-project/monero-gui/issues/2148>  
<strong>\<rbrunner\></strong> Looks like it will be a interesting release  
<strong>\<rehrar\></strong> Awesome. And where's the core software in the process of point release? they are planning to have one, right?  
<strong>\<rehrar\></strong> oh, well moneromooo did kind of state at the start  
<strong>\<dEBRUYNE\></strong> Yeah after 5509 is resolved we're branching as far as I know  
<strong>\<moneromooo\></strong> It just needs vtnerd to review (and hopefully not say it's total shite and needs rewriting :P)  
<strong>\<rehrar\></strong> and then waiting on pony shenanigans?  
<strong>\<rbrunner\></strong> Is it sure already that it will have the version 0.14.1.0?  
<strong>\<rbrunner\></strong> If yes, I can make the few trivial updates for the installer for that  
<strong>\<moneromooo\></strong> Almost certainly.  
<strong>\<moneromooo\></strong> But there will likely be 0.14.0.1 etc soon afterwards.  
<strong>\<rbrunner\></strong> You mean 0.14.1.1?  
<strong>\<dsc\_\></strong> Ill focus on: pruning/moneroseed handler/automatic mining from within the GUI next, after that TOR/I2P  
<strong>\<moneromooo\></strong> Yes, I do, thanks.  
<strong>\<rehrar\></strong> sad dsc\_. Mobile one day?  
<strong>\<dEBRUYNE\></strong> moneromooo: Are we building directly after branching or will there be some time for testing first?  
<strong>\<dsc\_\></strong> rehrar: Where's my Librem dev kit? :)  
<strong>\<moneromooo\></strong> Both I think.  
<strong>\<dEBRUYNE\></strong> Oki  
<strong>\<dEBRUYNE\></strong> Anyone from the RandomX team here to provide an update?  
<strong>\<dEBRUYNE\></strong> tevador, sech1, hyc?  
<strong>\<rehrar\></strong> dsc\_: I'll literally beg on the streets for you to get one  
<strong>\<selsta\></strong> 19:15 \<rehrar\> sad dsc\_. Mobile one day? \<-- We don’t really have resources for mobile atm.  
<strong>\<hyc\></strong> sure  
<strong>\<hyc\></strong> randomx code freeze was april39  
<strong>\<hyc\></strong> 30  
<strong>\<hyc\></strong> we have 2 review proposals and a 3rd team isprepping one  
<strong>\<hyc\></strong> I have a preliminary randomx integration with monerod in my github repo  
<strong>\<hyc\></strong> tevador is still playing with cpu optimizations  
<strong>\<rehrar\></strong> the review proposals will require XMR, yes?  
<strong>\<rehrar\></strong> via CCS?  
<strong>\<hyc\></strong> sech1 has nearly finished a CUDAversion  
<strong>\<hyc\></strong> yes  
<strong>\<rehrar\></strong> let me know if you guys require any help getting the CCS proposal up for them  
<strong>\<rbrunner\></strong> Will be intesting to see how fast CUDA will be  
<strong>\<hyc\></strong> thanks. waiting for 3rd proposal  
<strong>\<sech1\></strong> I estimate CUDA version will have the same hashrate on RandomX as with Cryptonight, maybe even faster  
<strong>\<sech1\></strong> It's like 80% complete now  
<strong>\<rehrar\></strong> this is kind of really exciting stuff, and I'm super giddy that Monero (via you guys) are on the forefront of this  
<strong>\<rbrunner\></strong> Is that earlier than originally feared / planned?  
<strong>\<hyc\></strong> rbrunner wdy mean  
<strong>\<rbrunner\></strong> The CUDA version. I am a little surprised it's almost ready already  
<strong>\<sech1\></strong> It's not hard to implement  
<strong>\<rbrunner\></strong> But somebody must do it :)  
<strong>\<sech1\></strong> But the remaining 20% might take longer, it's the hardest part to do without losing much hashrate  
<strong>\<hyc\></strong> yes, so it's beingdone  
<strong>\<hyc\></strong> lol. the last 20% always takes the most time...  
<strong>\<rbrunner\></strong> True that  
<strong>\<rehrar\></strong> hyc any time frame on the 3rd team proposal?  
<strong>\<rehrar\></strong> and kind of the CCS in general?  
<strong>\<rehrar\></strong> this probably won't get in this upcoming fork, correct?  
<strong>\<hyc\></strong> I suppose we'll see the 3rd proposal this week  
<strong>\<hyc\></strong> we'll present all 3 for discussion in this channel, decide what to move forward on  
<strong>\<sech1\></strong> You can watch my progress with CUDA version here: <https://github.com/SChernykh/RandomX\_CUDA/>  
<strong>\<hyc\></strong> if we have reviews completed by July I think we can roll out in October  
<strong>\<hyc\></strong> I expect to have fully working testnet monerod in time for monerokon  
<strong>\<dEBRUYNE\></strong> rehrar: I don't see why not if we have integration ready + reviews finished by the end of June  
<strong>\<rehrar\></strong> That's awfully exciting. Thanks for sharing the news on this.  
<strong>\<dEBRUYNE\></strong> The october fork is then still \~3.5 months away  
<strong>\<rehrar\></strong> so I guess I shouldn't buy any more GPUs at the moment for my little 2 GPU miner  
<strong>\<hyc\></strong> as sech1 noted, GPU hashrate will be comparable to cryptonight  
<strong>\<hyc\></strong> but CPU rate is much higher than cryptonight  
<strong>\<dEBRUYNE\></strong> I guess we'll see GPU mining as long as it is profitable  
<strong>\<hyc\></strong> yeah, no reason why not  
<strong>\<hyc\></strong> anyone interested in writing minig  
<strong>\<hyc\></strong> mining code can get current rev from randomx repo  
<strong>\<hyc\></strong> final docs/specs arethere now  
<strong>\<sech1\></strong> actually, it's the dev branch of randomx repo which is up to date  
<strong>\<hyc\></strong> ^ tevador says all merged to master now  
<strong>\<sech1\></strong> nice  
<strong>\<rehrar\></strong> I have a mac (for website testing). Maybe I can give it a shot.  
<strong>\<rehrar\></strong> But I'd have to build from source, right?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<moneromooo\></strong> Or I guess you can grab a binary from that PR.  
<strong>\<dsc\_\></strong> what does 'SSL' between wallet and daemon mean?  
<strong>\<dsc\_\></strong> between monero-wallet-cli and monerod?  
<strong>\<moneromooo\></strong> Data sent back and forth gets encrypted.  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<vtnerd\_\></strong> moneromooo : I have a mac for testing too  
<strong>\<dsc\_\></strong> gotcha. Ill try to test..  
<strong>\<vtnerd\_\></strong> the issue is that I think I have a custom openssl build instead of whatever comes with the system, which is probably what you want to be tested ?  
<strong>\<moneromooo\></strong> Well, mostly, but a custom one can't be bad either. Might find some corner case.  
<strong>\<rehrar\></strong> moneromooo: I'll put it in the Revuo as well as a volunteer opportunity?  
<strong>\<rehrar\></strong> though it'd help to have instructions on how to test  
<strong>\<rehrar\></strong> maybe I can talk with you later and do a write up  
<strong>\<moneromooo\></strong> Well, I kinda hope it'll be done and merged within a day now that vtnerd's around to review ^\_^  
<strong>\<rehrar\></strong> ah, I see.  
<strong>\<rehrar\></strong> no worries then  
<strong>\<moneromooo\></strong> Thanks though  
<strong>\<rehrar\></strong> alright, any other meeting items?  
<strong>\<rehrar\></strong> Just the logs of this meeting (if/when posted) will be enough to excite the community I think  
<strong>\<rehrar\></strong> pump back up to 500 dollah  
<strong>\<rehrar\></strong> jk jk don't ban  
<strong>\<rehrar\></strong> Alright, if there's nothing else, I think we can call it here. thanks for the check in everyone.  
<strong>\<hyc\></strong> byebye  
<strong>\<rbrunner\></strong> Thanks
