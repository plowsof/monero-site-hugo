---
title: Logs for the Community Meeting Held on 2018-04-28
summary: Community highlights, Forum Funding System updates, Localization workgroup Q&A, Monero Integrations, Monero QR GUI discussion, and miscellaneous
tags: [dev diaries, crypto]
author: el00ruobuob / SamsungGalaxyPlayer
---

# Logs

<strong>\<ErCiccione\></strong> It's meeting time\!  
<strong>\<endogenic\></strong> what up y'all  
<strong>\<ErCiccione\></strong> ping sarang  
<strong>\<Osiris1\></strong> poc poc  
<strong>\<sarang\></strong> yo yo  
<strong>\<ErCiccione\></strong> 0. Introduction  
<strong>\<midipoet\></strong> hey hey  
<strong>\<ErCiccione\></strong> Welcome everyone to this Monero Community Meeting\!  
<strong>\<ErCiccione\></strong> Link to agenda on GitHub: <https://github.com/monero-project/meta/issues/214>  
<strong>\<ErCiccione\></strong> Monero Community meetings are a discussion place for anything going on in the Monero Community. We use meetings to encourage the community to share ideas and provide support, so... let's begin\!  
<strong>\<ErCiccione\></strong> 1. Greetings  
<strong>\<msvb-lab\></strong> Hello.  
<strong>\<ArticMine\></strong> Hi  
<strong>\<cryptochangement\></strong> hello everyone  
<strong>\<Osiris1\></strong> hello  
<strong>\<sarang\></strong> heyo  
<strong>\<\_Slack\> \<sean\></strong> Hello  
<strong>\<\_Slack\> \<alexmu\></strong> Hi  
<strong>\<serhack\></strong> Hi :)  
<strong>\<nasawelder\></strong> hi (QR GUI guy)  
<strong>\<gingeropolous\></strong> hi  
<strong>\<onodera\></strong> hello  
<strong>\<xmrscott\[m\]\></strong> Hello  
<strong>\<onodera\></strong> can anyone tell me what kind of stuff gets discussed here?  
<strong>\<midipoet\></strong> hi everyone  
<strong>\<ErCiccione\></strong> onodera: agenda on GitHub: <https://github.com/monero-project/meta/issues/214>  
<strong>\<serhack\></strong> onodera: this is the community meeting for the Monero Community workgroup. Here we are going to discuss about community updates and ideas\!  
<strong>\<ErCiccione\></strong> lot of people today. good\!  
<strong>\<endogenic\></strong> onodera: exactly\!  
<strong>\<onodera\></strong> interesting, thanks ErCiccione and serhack  
<strong>\<ErCiccione\></strong> 2. Community highlights  
<strong>\<ErCiccione\></strong> m2049r's FFS proposal has been completely funded, this means 3 more months of Monerujo developing\! Congratulations\!  
<strong>\<ErCiccione\></strong> Link to the FFS proposal: <https://forum.getmonero.org/8/funding-required/90038/m2049r-part-time-for-3-months>  
<strong>\<ErCiccione\></strong> also, fluffypony merged a lot of PRs few hours ago, new cool stuff for the next release\!  
<strong>\<ErCiccione\></strong> Anybody have updates to share? don't be shy\!  
<strong>\<cryptochangement\></strong> me me  
<strong>\<cryptochangement\></strong> oh wait not yet lol  
<strong>\<endogenic\></strong> too late  
<strong>\<cryptochangement\></strong> well if nobody else has something to mention...  
<strong>\<onodera\></strong> I've been working on a self-hosted web-wallet for Monero the past few months: it's really not anything usable yet but it's starting to take shape: <https://github.com/onodera-punpun/sako>  
<strong>\<ErCiccione\></strong> let's wait a minute cryptochangement :)  
<strong>\<onodera\></strong> dont' know if this is relevant to what should be discussed here? :)  
<strong>\<cryptochangement\></strong> agreed ErCiccione  
<strong>\<midipoet\></strong> i have something to mention, but was going to wait till 'ideas' time  
<strong>\<cryptochangement\></strong> onodera: that sounds interesting. how does it differ from say openmonero?  
<strong>\<onodera\></strong> cryptochangement: the idea is that it's self hosted, so you don't depend on a third party  
<strong>\<endogenic\></strong> onodera: same with openmonero  
<strong>\<ErCiccione\></strong> midipoet: noted for open ideas later  
<strong>\<onodera\></strong> so kind of like the transmission (torrent client) web interface  
<strong>\<onodera\></strong> ah I suppose that I made it myself hehe  
<strong>\<onodera\></strong> I mainly just started this project to learn more about Go and the monero RPC methods  
<strong>\<endogenic\></strong> good way to learn those  
<strong>\<serhack\></strong> +1 onodera :)  
<strong>\<ErCiccione\></strong> well, the more the better. Looking forward to see some updates on that onodera  
<strong>\<hrumag\></strong> OT: Guys, relay on mattermost does not work  
<strong>\<ErCiccione\></strong> hrumag: thanks, can you write that on mattermost, so who wants to attend the meeting can use another platform  
<strong>\<ErCiccione\></strong> any other question for onodera and his self hosted web wallet?  
<strong>\<hrumag\></strong> erciccione: of course  
<strong>\<ErCiccione\></strong> 3. FFS updates  
<strong>\<ErCiccione\></strong> There are several Forum Funding System updates today:  
<strong>\<ErCiccione\></strong> a. Monero Integrations  
<strong>\<ErCiccione\></strong> serhack and cryptochangement asked to reserve some time to discuss their integrations, so please guys go ahead :)  
<strong>\<cryptochangement\></strong> ok cool  
<strong>\<cryptochangement\></strong> so basically our Opencart payment gateway is complete  
<strong>\<cryptochangement\></strong> you can find it here <https://github.com/monero-integrations.com/monerocart>  
<strong>\<endogenic\></strong> 404  
<strong>\<cryptochangement\></strong> that also completes the final milestone of our FFS  
<strong>\<endogenic\></strong> <https://github.com/monero-integrations/monerocart>  
<strong>\<serhack\></strong> ty endogenic\!  
<strong>\<endogenic\></strong> np  
<strong>\<cryptochangement\></strong> oops thanks  
<strong>\<cryptochangement\></strong> any questions?  
<strong>\<endogenic\></strong> cryptochangement with the php-fu  
<strong>\<cryptochangement\></strong> :p  
<strong>\<cryptochangement\></strong> if nobody has questions we can move on :)  
<strong>\<endogenic\></strong> clear you guys did a lot of work on this  
<strong>\<serhack\></strong> endogenic: I can confirm. Cryptochangements and sneurlax did a lot of work on php library\!  
<strong>\<endogenic\></strong> oh would it be possible to https-ify <http://monerointegrations.com>?  
<strong>\<endogenic\></strong> serhack: srsly..  
<strong>\<cryptochangement\></strong> it should have ssl  
<strong>\<cryptochangement\></strong> <https://monerointegrations.com>  
<strong>\<endogenic\></strong> your github profile link lacks ssl, fyi  
<strong>\<serhack\></strong> it is :/ I have to redirect, thanks endogenic\!  
<strong>\<endogenic\></strong> ah ok  
<strong>\<ErCiccione\></strong> let's move on\!  
<strong>\<ErCiccione\></strong> b. IEEE Security &amp; Privacy on the Blockchain workshop  
<strong>\<sarang\></strong> yes  
<strong>\<ErCiccione\></strong> sarang attended the SPB in London, an event focused on scaling, privacy, and applications of blockchain technologies and distributed ledgers, focusing particularly on the security and efficiency of current and future implementations. He is going to give us a brief update.  
<strong>\<ErCiccione\></strong> link to the funded FFS proposal: <https://forum.getmonero.org/9/work-in-progress/90165/noether-brothers-ieee-workshop>  
<strong>\<sarang\></strong> Thanks to the community for funding my presence (and Surae's) at the workshop  
<strong>\<endogenic\></strong> serhack: i think it could be cool to show on your homepage shops which are using the libs  
<strong>\<sarang\></strong> There was a great audience of academics here, and two talks directly addressing Monero  
<strong>\<sarang\></strong> One was an update on a paper discussing ways to efficiently describe ring members, which could be useful if/when we move to much larger ring sizes  
<strong>\<sarang\></strong> had some great discussions with the author  
<strong>\<cryptochangement\></strong> endogenic: that's a good idea  
<strong>\<sarang\></strong> the other was a talk on possible attacks by a malicious remote node  
<strong>\<sarang\></strong> the ideas had been disclosed to us  
<strong>\<sarang\></strong> We have some reasonable mitigations in place, but it highlights the importance of trusting a remote node anyway  
<strong>\<sarang\></strong> Between talks, we spoke with a Purdue researcher whose student has a proposal for altering our ring sigs to support refund txns  
<strong>\<endogenic\></strong> serhack: you can just put a note saying "tell us if you use the lib and we'll feature you" so you can avoid some kind of contact info collection  
<strong>\<sarang\></strong> There's a preprint draft not publicly available, and we're working on the math/security of it all  
<strong>\<endogenic\></strong> whoa neat  
<strong>\<serhack\></strong> great suggestion endogenic  
<strong>\<sarang\></strong> It would be a great step to side payment channels  
<strong>\<nasawelder\></strong> refund txs ELi5?  
<strong>\<endogenic\></strong> sarang what's the gist of how that would work?  
<strong>\<sarang\></strong> I send two outputs instead of one... one directed to you, one directed elsewhere, and a trigger block height  
<strong>\<sarang\></strong> only one output is usable at a time, depending on the current block height  
<strong>\<sarang\></strong> It required a modification to our key images  
<strong>\<endogenic\></strong> ah  
<strong>\<sarang\></strong> We have a way to do it that allows for combining refund outputs and standard outputs in the same ring sig  
<strong>\<sarang\></strong> As always, conferences are great both for the presentations and for the discussions with other researchers  
<strong>\<endogenic\></strong> i wonder if there's an attack lurking there with refunds :P  
<strong>\<sarang\></strong> The increase in third-party Monero research is also welcome  
<strong>\<sarang\></strong> endogenic: it's the same style of output generation  
<strong>\<sarang\></strong> the only real trick is in the key image  
<strong>\<sarang\></strong> and that uses a common DHKE method that's well understood  
<strong>\<sarang\></strong> No guarantee this will be implemented, but it's well worth the study  
<strong>\<endogenic\></strong> i'm just thinking back to zerocoin's recent thing  
<strong>\<sarang\></strong> We'll have a writeup later on the method  
<strong>\<sarang\></strong> It's a small tweak to the signature scheme  
<strong>\<sarang\></strong> quite elegant  
<strong>\<sarang\></strong> and it's optional  
<strong>\<sarang\></strong> if you don't want refund outputs, nothing changes  
<strong>\<sarang\></strong> and for payment channels, refund outs are only used if something hits the fan  
<strong>\<sarang\></strong> Anyway, that's my update\! My thanks for the support  
<strong>\<ErCiccione\></strong> questions for sarang?  
<strong>\<sarang\></strong> I can't share the preprint yet but it'll come out eventually  
<strong>\<ErCiccione\></strong> c. Monero QR GUI discussion  
<strong>\<ErCiccione\></strong> About a month ago, nasawelder introduced Lunlumo, a method of using a series of QR codes to send funds from an airgapped computer. See the original discussion here: <https://www.reddit.com/r/Monero/comments/81tjrg/introducing\_lunlumo\_send\_monero\_from\_an\_airgapped/>  
<strong>\<monerobux\></strong> \[REDDIT\] Introducing Lunlumo, send Monero from an air-gapped computer via QR codes (self.Monero) \| 100 points (98.0%) \| 57 comments \| Posted by NASA\_Welder \| Created at 2018-03-03 - 22:33:35  
<strong>\<ErCiccione\></strong> Since they are still interested in pursuing this idea, I offered to reserve some meeting time to get more community consensus. Sometimes ideas need persistence to move to funding required. Here is the FFS link: <https://forum.getmonero.org/7/open-tasks/89997/lunlumo-cold-signing-automation-via-qr-code-full-gui-python-cli-wrapper-library>  
<strong>\<ErCiccione\></strong> nasawelder, the floor is yours  
<strong>\<sarang\></strong> I must take off now... cheers to all  
<strong>\<ErCiccione\></strong> thanks sarang\!  
<strong>\<nasawelder\></strong> My interests are in automation and security  
<strong>\<endogenic\></strong> see you, sarang  
<strong>\<nasawelder\></strong> Lunlumo currently can do tx's from cold computer  
<strong>\<nasawelder\></strong> i want to add multisig support  
<strong>\<nasawelder\></strong> it will be easy to bolt on features since it wraps the CLI  
<strong>\<nasawelder\></strong> for instance, wallet address book transfer, other minor stuff  
<strong>\<nasawelder\></strong> it could also be used to keep harware wallet itself cold  
<strong>\<nasawelder\></strong> not sure what else to say...  
<strong>\<nasawelder\></strong> it's a raspberry pi GUI, also, which doesn't exist  
<strong>\<\_Slack\> \<alexmu\></strong> Do the cold and hot computers look at each other screens?  
<strong>\<nasawelder\></strong> Yes they looki at each others screens via webcam  
<strong>\<\_Slack\> \<alexmu\></strong> Cool.  
<strong>\<nasawelder\></strong> ideal use case would be raspi to android phone  
<strong>\<\_Slack\> \<alexmu\></strong> Makes sense.  
<strong>\<nasawelder\></strong> like a checking account to back-pocket wallet withdrawal/top-up  
<strong>\<ErCiccione\></strong> That sounds cool, i would love to see the proposal moved to funding required  
<strong>\<endogenic\></strong> nasawelder: can you build it as an embeddable library?  
<strong>\<endogenic\></strong> transfer via qr code is common among ecosystem apps  
<strong>\<nasawelder\></strong> the CLI backend is a standalone library (API not stable  
<strong>\<endogenic\></strong> i meant the QR streaming stuff  
<strong>\<nasawelder\></strong> endogenic: explain a bot more your question  
<strong>\<nasawelder\></strong> bit  
<strong>\<nasawelder\></strong> i plan to make a standalone QR com library to  
<strong>\<endogenic\></strong> are you writing it so that others can use your code?  
<strong>\<nasawelder\></strong> if that is what you meant  
<strong>\<nasawelder\></strong> yes  
<strong>\<nasawelder\></strong> it's all open source  
<strong>\<endogenic\></strong> cool. mymonero i don't think is interested in it at the moment but i think others are  
<strong>\<nasawelder\></strong> source: <https://github.com/nasaWelder/lunlumo>  
<strong>\<endogenic\></strong> yes  
<strong>\<endogenic\></strong> perhaps you can get a partnership going  
<strong>\<nasawelder\></strong> I've reached out to monerujo, cake and Xwallet  
<strong>\<nasawelder\></strong> and provided interface spec (see source)  
<strong>\<nasawelder\></strong> ope to establish a formal protocol  
<strong>\<nasawelder\></strong> (explained therin)  
<strong>\<nasawelder\></strong> hope\*  
<strong>\<msvb-lab\></strong> nasawelder: We're using qr in the hardware wallet firmware as well.  
<strong>\<nasawelder\></strong> (not that we talk about exchange rates) I'm working on adding air gapp to trading bot  
<strong>\<endogenic\></strong> you could try asking at a monero-dev meeting whether it makes sense to integrate into the official codebase somehow  
<strong>\<endogenic\></strong> aside from that, how can the community help you?  
<strong>\<nasawelder\></strong> endogenic: originally this was an idea i had for monero codebase proper, but I just decided to make it with everyone being so busy, and i only know python  
<strong>\<nasawelder\></strong> I know how to complete my roadmap, the only thing I don'y know how to do is bundle all dependencies with my source  
<strong>\<nasawelder\></strong> it uses some "sudo apt-get install" dependencies  
<strong>\<nasawelder\></strong> msvb-lab: have I made something redundant?  
<strong>\<msvb-lab\></strong> nasawelder: I didn't mean redundancy, instead I would like to indicate interest in having a good QR library available for firmware as well.  
<strong>\<nasawelder\></strong> (also) lunlumo itself is pure python, so no need to install it compiled, (transparency +1)  
<strong>\<endogenic\></strong> the streaming is not redundant aside from other people having implemented it  
<strong>\<endogenic\></strong> in other projects  
<strong>\<nasawelder\></strong> msvb-lab: I'm interested in helping  
<strong>\<endogenic\></strong> nasawelder: go for it in c++ i say. someone is working on it in monero gui right now  
<strong>\<nasawelder\></strong> endo: i gotcha, well the streaming is automated within tx workflow which is like 5 steps, so that's what I'm selling : user experience  
<strong>\<endogenic\></strong> people will support you  
<strong>\<msvb-lab\></strong> nasawelder: If you want to help in firmware, please become a team member to make communication easier:  
<strong>\<msvb-lab\></strong> taiga.getmonero.org/project/michael-rfc-hwallet-1-implementation/  
<strong>\<nasawelder\></strong> will do  
<strong>\<endogenic\></strong> nasawelder: any reason it cant be done in the gui?  
<strong>\<nasawelder\></strong> the official monero gui?  
<strong>\<endogenic\></strong> yes. a build variant  
<strong>\<nasawelder\></strong> no, just I don't know c++ so i made it in python  
<strong>\<endogenic\></strong> i mean the codebase is large  
<strong>\<endogenic\></strong> and so many different ppl work on it  
<strong>\<nasawelder\></strong> original goal was to inspire it into the official GUI,k hopefully I've blazed a trail, at least  
<strong>\<endogenic\></strong> but i'm certain we can work it out modularly  
<strong>\<endogenic\></strong> nasawelder: think it's all you bro  
<strong>\<endogenic\></strong> but hey there's always hope  
<strong>\<endogenic\></strong> the c++ has examples in the codebase already  
<strong>\<endogenic\></strong> you know python so you're fine  
<strong>\<endogenic\></strong> i believe in you  
<strong>\<nasawelder\></strong> anyways, thanks y'all  
<strong>\<ErCiccione\></strong> anything you want to add nasawelder?  
<strong>\<nasawelder\></strong> CLI features can be added to lunlumo very quickly as they come out  
<strong>\<nasawelder\></strong> so that's why i like python  
<strong>\<nasawelder\></strong> that's all  
<strong>\<endogenic\></strong> i rly meant it fwiw  
<strong>\<nasawelder\></strong> it's ok, I have a toddler, so someone else can pick up the c++ torch  
<strong>\<ErCiccione\></strong> ok, let's see if there are further questions and then we can move on to open ideas time  
<strong>\<ErCiccione\></strong> no wait, there's my update before open ideas :P  
<strong>\<msvb-lab\></strong> My idea is to upload a video of the latest status of the hardware wallet, but I don't know how to find the right place.  
<strong>\<msvb-lab\></strong> ...in open ideas, but possibly my question came too early?  
<strong>\<endogenic\></strong> youtube? or are they evil  
<strong>\<endogenic\></strong> and does it matter  
<strong>\<endogenic\></strong> :p  
<strong>\<msvb-lab\></strong> endogenic: There is a media.getmonero.org or something.  
<strong>\<ErCiccione\></strong> msvb-lab: one last FFS update then we can move on, but before you midipoet had something to say  
<strong>\<ErCiccione\></strong> d. Localization workgroup Q&amp;A  
<strong>\<msvb-lab\></strong> ErCiccione: Yes, thanks. No problem.  
<strong>\<midipoet\></strong> thanks\!  
<strong>\<ErCiccione\></strong> ok, about localization  
<strong>\<ErCiccione\></strong> the localization of monerujo is going very well, you can see on taiga what's in progress and ready.. a lot of stuff:  
<strong>\<ErCiccione\></strong> <https://taiga.getmonero.org/project/erciccione-monero-localization/us/163?milestone=28>  
<strong>\<endogenic\></strong> msvb-lab: seems long lived for transient media  
<strong>\<endogenic\></strong> msvb-lab: plus hosting there will burden server - may want to find a CDN  
<strong>\<endogenic\></strong> msvb-lab: but maybe ask rehrar  
<strong>\<ErCiccione\></strong> endogenic: please, let's wait for that  
<strong>\<ErCiccione\></strong> the monero GUI is being refactored so we will need to refresh it again, this will happen probably next week during a code freeze. i will open an issue on github when the time will come  
<strong>\<ErCiccione\></strong> nothing more to add  
<strong>\<ErCiccione\></strong> any question?  
<strong>\<ErCiccione\></strong> ooook  
<strong>\<hrumag\></strong> yeah, i've got one. the refreshing of the original strings of monero GUI is the same of monerujo?  
<strong>\<ErCiccione\></strong> hrumag: no it works quite differently, it will be easier 'cause i will make the refresh and translators will only need to translate the new strings  
<strong>\<hrumag\></strong> erciccione: good to know  
<strong>\<ErCiccione\></strong> Does anyone else have a FFS update or any last question?  
<strong>\<Alex\_LocalMonero\></strong> Workgroup meeting still on?  
<strong>\<endogenic\></strong> you know it  
<strong>\<msvb-lab\></strong> endogenic: Is there a media server or not? I'm confused.  
<strong>\<endogenic\></strong> no idea  
<strong>\<endogenic\></strong> ErCiccione: when monero ffs ico?  
<strong>\<msvb-lab\></strong> I thought there was something like media.getmonero.org, I'm just getting the URL name wrong  
<strong>\<ErCiccione\></strong> msvb-lab: endogenic: there is, don't remember the exact link now, but i'm sure it exists  
<strong>\<msvb-lab\></strong> ErCiccione: Same with me, I saw the URL in some place, but have forgotten it.  
<strong>\<msvb-lab\></strong> Nobody here knows the media server URL?  
<strong>\<ErCiccione\></strong> let's finish the meeting first msvb-lab then we can investigate :)  
<strong>\<ErCiccione\></strong> 4. Open ideas time  
<strong>\<ErCiccione\></strong> It’s open ideas time\! Feel free to propose your ideas to this discussion group, and feel free to comment on others’ ideas. If you disagree with the idea, please reply with constructive criticism. Thank you\!  
<strong>\<ErCiccione\></strong> midipoet, you first. msvb-lab then  
<strong>\<midipoet\></strong> great thanks\!  
<strong>\<midipoet\></strong> I am going to try and keep this relatively short, but am open to any follow on questions through here, through email, or through reddit (same username).  
<strong>\<midipoet\></strong> I am currently involved in an academic research project. Its concern is Privacy, and more specifically, perspectives of privacy within blockchain.  
<strong>\<midipoet\></strong> I have proposed to use the Monero community to gather qualitative data (through semi-structured anonymous interviews - probably over some text based platform). This is mainly because a number of key groups can be found here (users, cryptographers, protocol designers), and i know this community, and some know me.  
<strong>\<endogenic\></strong> midipoet: what field of academia? sociology sort of thing?  
<strong>\<midipoet\></strong> Information Science  
<strong>\<midipoet\></strong> Researching emerging financial technology  
<strong>\<midipoet\></strong> so probably more soft science, than hard....  
<strong>\<midipoet\></strong> From the interviews, perspectives will be compared with others from the industry (corporate blockchain architects, legislators, and regulators). With the help of university i am based at (University College Cork, Ireland) i have access to a lot of these groups. Mainly HyperLedger developers, employees at the Central Bank of Ireland, and some members from the GDPR committee.  
<strong>\<midipoet\></strong> The idea is to try and figure out what different groups actually think Privacy is or is not, and then compare them.  
<strong>\<midipoet\></strong> It’s all well and good that all these different groups approach and negotiate aspects of privacy through blockchain, but most of the time groups (or individuals) don’t actually know what others think privacy is, or is not (and it often changes from individual to individual, context to context, culture to culture, etc etc).  
<strong>\<endogenic\></strong> lol  
<strong>\<midipoet\></strong> (yeah these are all pre-typed to save time)  
<strong>\<endogenic\></strong> do people really differ on defining the term privacy?  
<strong>\<midipoet\></strong> yes, i think there is massive spectrum  
<strong>\<midipoet\></strong> certainly my initial research has shown this  
<strong>\<endogenic\></strong> curious to hear two of your datapoints  
<strong>\<midipoet\></strong> I have written two papers already. one is theory lite  
<strong>\<endogenic\></strong> what is the range?  
<strong>\<midipoet\></strong> <https://pastebin.com/QirgSE1b>  
<strong>\<midipoet\></strong> and one is theory heavy  
<strong>\<midipoet\></strong> <https://pastebin.com/7r0RR0rr>  
<strong>\<midipoet\></strong> it depends your perspective on what privacy is. some people see it as right, some as value based commodity, some as cognitive concept  
<strong>\<midipoet\></strong> and so on...  
<strong>\<midipoet\></strong> some a mixture of all the above  
<strong>\<endogenic\></strong> you said definition of privacy though  
<strong>\<midipoet\></strong> the core differences come (and most interestingly) on what levels of privacy should be afforded  
<strong>\<endogenic\></strong> ok  
<strong>\<midipoet\></strong> and also, whether its state or system that should protect it (if its a right)  
<strong>\<midipoet\></strong> I have mentioned this research to the MRL, and they have been supportive. I am hoping members of the dev team and cryptographers will engage with the qualitative interview process (i will also be in the MRL meeting on the 30th to talk further with them)  
<strong>\<midipoet\></strong> What i am hoping is that members of the wider community will also get involved. And this is why i am here….basically to ask if anyone is interested in talking about what they believe privacy is, why it is important, what the context is, who should protect it, what system should protect it, is it a right, etc etc etc.  
<strong>\<endogenic\></strong> dont think anyone here is interested in privacy  
<strong>\<midipoet\></strong> lol  
<strong>\<midipoet\></strong> i think that's kind of it. i know that's a barrage of info, and i apologise. but any questions?  
<strong>\<ErCiccione\></strong> this is extremely interesting, i would love to participate and i'm sure also many community members will  
<strong>\<midipoet\></strong> thanks  
<strong>\<ErCiccione\></strong> contact rehrar, he would love this  
<strong>\<ErCiccione\></strong> \*will  
<strong>\<endogenic\></strong> midipoet: do you use surveys, mainly?  
<strong>\<midipoet\></strong> i also think its really interesting. I am aiming for top level journals and conferences, as i think Monero deserves it.  
<strong>\<midipoet\></strong> endogenic: it is semi structured interviews, in an explorative study  
<strong>\<midipoet\></strong> mainly using Monero as a sort of 'index case'  
<strong>\<midipoet\></strong> or the Monero community, i should say  
<strong>\<xmrmatterbridge\> \<cypherperro\></strong> I would also love to contribute  
<strong>\<midipoet\></strong> Personally i think it is important that we negotiate the ideological aspects of privacy as a community, together. Especially as legislation and regulation is bound to appear in the future (and has started to already).  
<strong>\<ErCiccione\></strong> ^^ +1  
<strong>\<serhack\></strong> Privacy is fundamental.  
<strong>\<serhack\></strong> Nobody can stop us\!  
<strong>\<midipoet\></strong> I think if we are able to put forward and compare and contrast across social groups/stakeholders, privacy rights can be negotiated  
<strong>\<UkoeHB\></strong> I think Olufunmilayo would like to get that interview. You can find in \#monero sometimes  
<strong>\<endogenic\></strong> midipoet: what principle do you use in interpreting and organizing answers?  
<strong>\<midipoet\></strong> endogenic: i am not sure i understand the question. If you are asking what methodology for interpreting? The IS literature points to open axial coding  
<strong>\<midipoet\></strong> to be honest, IS methodology is not my strong point (but is my supervisors), who is an old friend of mine  
<strong>\<midipoet\></strong> as its an exploratory study, i think strong methodology can emerge as i go  
<strong>\<midipoet\></strong> as i am sure themes will emerge as i go  
<strong>\<midipoet\></strong> so can i ask, for whoever wants to contribute to email me? is that fair?  
<strong>\<midipoet\></strong> if more anonymity is required, you can also contact me on Reddit.  
<strong>\<midipoet\></strong> i can also provide a PGP key if needed  
<strong>\<endogenic\></strong> well this is no longer relevant but i'm curious about IS and would expect there was some way to confirm the precision of identification of codes in the first place  
<strong>\<ErCiccione\></strong> sure it is midipoet, leave here your contacts if you wish,  
<strong>\<endogenic\></strong> good luck  
<strong>\<midipoet\></strong> <rrenwick01@qub.ac.uk>  
<strong>\<midipoet\></strong> u/midipoet on Reddit  
<strong>\<midipoet\></strong> Thanks for listening....  
<strong>\<ErCiccione\></strong> perfect, it's getting late now, you can keep talking about this after the meeting if you want  
<strong>\<endogenic\></strong> longest community mtg ever :P  
<strong>\<ErCiccione\></strong> thank you midipoet  
<strong>\<midipoet\></strong> thankyou  
<strong>\<ErCiccione\></strong> msvb-lab: so, about this video.. :)  
<strong>\<ErCiccione\></strong> endogenic: yep, lot of stuff today :P  
<strong>\<msvb-lab\></strong> Yes.  
<strong>\<ErCiccione\></strong> we will have to ask to rehrar for that link, what was your idea btw?  
<strong>\<ErCiccione\></strong> well, the 30 minutes for the open ideas time are over folks, let's wrap this meeting up  
<strong>\<ErCiccione\></strong> 5. Confirm next meeting date/time  
<strong>\<ErCiccione\></strong> The next community meeting will be two weeks from today on 28 April.  
<strong>\<ErCiccione\></strong> 6. Conclusion  
<strong>\<ErCiccione\></strong> That’s all\! Thanks for attending this Monero Community meeting, we hope to see you on /r/MoneroCommunity and \#monero-community. Take care and remember there is only one Monero, stay away from all those scammy forks\!  
<strong>\<ErCiccione\></strong> See you around\!  
<strong>\<ErCiccione\></strong> the meeting is over, but please, don't let the discussion die, if you have anything you want to talk about... please do\!  
<strong>\<serhack\></strong> thank you Erciccione\!  
<strong>\<midipoet\></strong> yes, thank you Erciccione  
<strong>\<serhack\></strong> <https://www.reddit.com/r/Monero/comments/8flnzi/finally\_released\_monero\_payment\_gateway\_for/>  
<strong>\<monerobux\></strong> \[REDDIT\] Finally released Monero Payment Gateway for OpenCart (self.Monero) \| 2 points (100.0%) \| 0 comments \| Posted by serhack \| Created at 2018-04-28 - 18:15:41  
<strong>\<ErCiccione\></strong> whoo, this was a long one still within the 1.5 hrs tho :P  
<strong>\<ErCiccione\></strong> thank you guys :)  
<strong>\<\_Slack\> \<alexmu\></strong> Long and great. Thank you.
