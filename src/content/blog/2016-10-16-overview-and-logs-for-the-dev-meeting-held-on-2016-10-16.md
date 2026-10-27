---
title: Overview and Logs for the Dev Meeting Held on 2016-10-16
summary: Review and discussion of Open PRs, contribution guidelines, and official GUI
tags: [dev diaries, core, crypto, 0mq]
author: dEBRUYNE / fluffypony
---

### Overview

An overview [can be found on Hello Monero](https://hellomonero.com/article/monero-dev-meeting-note-highlights-2016-10-16).

### Logs

<strong>\<moneromooo\></strong> So, fluffypony asked if I could talk. I have no relay bot, so \#kovri-dev will have to be here to listen.  
<strong>\<moneromooo\></strong> He suggested I talk about guidelines for submitting patches. So we’ll see if everyone mostly agrees.  
<strong>\<+hyc\></strong> cool  
<strong>\<moneromooo\></strong> I would like to encourage people to make clean changes, which mean:  
<strong>\<moneromooo\></strong> - try to keep patches self contained where appropriate  
<strong>\<moneromooo\></strong> - no random whitespace changes interspersed with other changes  
<strong>\<moneromooo\></strong> - sensible commit message (ie, no “update wallet.cpp”)  
<strong>\<moneromooo\></strong> - properly rebased patches (ie, if you authored three patches in a PR, don’t send 20 patches from someone else at the same time, so “git rebase master” first)  
<strong>\<+hyc\></strong> that all makes sense  
<strong>\<moneromooo\></strong> If you make a buggy patch and then fix it in a second patch, squash those (see git rebase -i, but that starts being a bit complex)  
<strong>\<moneromooo\></strong> Does anyone disagree ?  
<strong>\<\_Slack\> \<nanoakron\></strong> Nope  
<strong>\<Jaquee\_\></strong> nope  
<strong>\<tompole\></strong> nope  
<strong>\<+hyc\></strong> no disagreement here. that’s standard stuff.  
<strong>\<\_Slack\> \<nanoakron\></strong> Can I ask a little more about what you mean by ‘self contained’  
<strong>\<moneromooo\></strong> (We’ll make an exception for tewinget who’s got a massive non rebased patchset for 0mq though)  
<strong>\<+hyc\></strong> sure, patches of such large scope are going to have their exceptions  
<strong>\<moneromooo\></strong> I mean, if you’ve got two changes, make them two patches. I like small patches, one per “logical change”.  
<strong>\<\_Slack\> \<nanoakron\></strong> Makes sense. Single-issue patches.  
<strong>\<moneromooo\></strong> It’s easier to review, to debug, to revert it necessary.  
<strong>\<+hyc\></strong> but usually PRs should be one issue per patch, one patch per issue  
<strong>\<moneromooo\></strong> Yes. However, when in the middle of a large thing, you sometimes see something that needs fixing and would otherwise conflict. That can go (as a separate patch) in that PR, depends on the circumstances.  
<strong>\<moneromooo\></strong> especially for those PRs that can take weeks to be merged.  
<strong>\<+hyc\></strong> sure  
<strong>\<\_Slack\> \<nanoakron\></strong> OK  
<strong>\<moneromooo\></strong> But yes, 1/1 in general.  
<strong>\<moneromooo\></strong> So, nobody seems to disagree, I’ll write a little thingie about this for the repo. Thanks.  
<strong>\<moneromooo\></strong> So, I guess… anyone has anything to say about progress, or other dev related stuff ? :)  
<strong>\<Fireice\></strong> I’ve got a question to the devs - do you think Monero is mature enough for applications improving usability? I’m an independent software dev, and I’m thinking of committing about 6 months of full-time work on Monero. First application that I’m thinking of is a lightweight Windows GUI wallet for Monero.  
<strong>\<moneromooo\></strong> Another one, yay\! :)  
<strong>\<moneromooo\></strong> First, read up on what lightweight may involve for monero.  
<strong>\<\_Slack\> \<nanoakron\></strong> Do we have a common wiki or other info page for devs to describe things like prefixes e.g. m\* and others  
<strong>\<TedTheFicus\></strong> Yes, this is needed  
<strong>\<\_Slack\> \<nanoakron\></strong> stuff  
<strong>\<moneromooo\></strong> And mature enough is pretty subjective. It can be used, for sure.  
<strong>\<Fireice\></strong> lol, bazaar project usually have a lot of traffic  
<strong>\<moneromooo\></strong> There is none. Some people use m\* for class data members.  
<strong>\<hiall\></strong> hi all  
<strong>\<\_Slack\> \<nanoakron\></strong> What would you think about standardising that aspect of development? Variable/class/etc. nomenclature?  
<strong>\<moneromooo\></strong> Fireice: also, ask athan (or ethan), he’s got a wallte in development which you might want to have a look at.  
<strong>\<hiall\></strong> when is meeting starting?  
<strong>\<dEBRUYNE\></strong> it already started  
<strong>\<+hyc\></strong> nanoakron: that sounds like a lot of busywork  
<strong>\<hiall\></strong> where is it?  
<strong>\<moneromooo\></strong> Well, my opinion on that is to follow the existing, but I’m not super bothered about it. I certaonly don’t subscribe to the minutiae crap. But I know many disagree :)  
<strong>\<Fireice\></strong> ok will do, how do i get hold of him?  
<strong>\<\_Slack\> \<nanoakron\></strong> Fireice: Take a look at how the existing GUI wallet is coming along at <https://github.com/monero-project/monero-core> - maybe integration into an existing service such as open bazaar would be cool  
<strong>\<moneromooo\></strong> Fireice: he’s around on IRC pretty often.  
<strong>\<\_Slack\> \<nanoakron\></strong> hyc: I know :( But standards can be good too  
<strong>\<moneromooo\></strong> integration would need th plugin system first. That is yet to be design.  
<strong>\<moneromooo\></strong> designed.  
<strong>\<dEBRUYNE\></strong> Fireice: His contact details are on Github too: <https://github.com/athanclark>  
<strong>\<imans\></strong> There is no instruction for windows compilation in the github  
<strong>\<endogenic\></strong> I tend to agree with nanoakron in the sense that changes to the API, especially w/o corresponding documentation updates, makes integration pretty darn tough and not necessarily viable for third parties  
<strong>\<moneromooo\></strong> Well, that’s true. It’s not API stable, that’s certain.  
<strong>\<dEBRUYNE\></strong> imans: <https://monero.stackexchange.com/questions/2346/compiling-gui-from-source-differences-by-os>  
<strong>\<+hyc\></strong> not at the binary level, and not even at the RPC level  
<strong>\<moneromooo\></strong> The RPC is <em>mostly</em> backward compatible though.  
<strong>\<endogenic\></strong> Fireice: that may be your answer then :)  
<strong>\<imans\></strong> ty dEBRUYNE  
<strong>\<\_Slack\> \<nanoakron\></strong> @hyc or @moneromooo on a similar note, is there a list of all available functions? E.g. call tools::simplewallet::is<em>it\_true() to clean true/false user inputs  
<strong>\<+hyc\></strong> I think it’s OK to establish guidelines now for future development  
<strong>\<Fireice\></strong> ty for your help, do you know if the qt wallet targets win and linux systems or just linux?  
<strong>\<+hyc\></strong> but it’s too early to make hard rules  
<strong>\<hiall\></strong> is this the meeting?  
<strong>\<pero\></strong> conference, dev conference  
<strong>\<moneromooo\></strong> A list of all available functions, beyond the source ?  
<strong>\<jaquee\></strong> Fireice: the official targets linux, osx and windows  
<strong>\<dEBRUYNE\></strong> Fireice: The official GUI will be available for Linux, os x, and windows  
<strong>\<moneromooo\></strong> That sounds like it’d go stale pretty fast.  
<strong>\<moneromooo\></strong> But no, there is none.  
<strong>\<endogenic\></strong> perhaps the API documentation stuff should wait until the 0mq changes have been made?  
<strong>\<+hyc\></strong> at least that, yes  
<strong>\<+hyc\></strong> (endogenic)  
<strong>\<\_Slack\> \<nanoakron\></strong> @moneromooo yes. I don’t think you’re going to find key functions going stale that fast, so long as you require people who update or add functions to make corresponding changes to the documentation before their PR gets accepted.  
<strong>\<moneromooo\></strong> I think tewinget is doing doc as he codes.  
<strong>\<imans\></strong> IMO third party integrations must be made simple and easy to plug with any kind of party or platform  
<strong>\<moneromooo\></strong> I’m not sure holding PRs for documentation is best, but I’m a bit on the fence tbh.  
<strong>\<moneromooo\></strong> What do people think ?  
<strong>\<+hyc\></strong> sounds like a Would Be Nice when there is a larger developer base  
<strong>\<+hyc\></strong> and the dev base is certainly growing now  
<strong>\<\_Slack\> \<nanoakron\></strong> Documentation is boring bullshit but necessary to make it easier for new devs to get involved. We don’t want to get into a situation like a certain other coin where only an inner cabal actually knows the code without deep reading  
<strong>\<TedTheFicus\></strong> If documentation is going to make it easier to attract API + other users than I think we need it up to date always  
<strong>\<endogenic\></strong> moneromooo: documentation should be done by particularly able people IMHO  
<strong>\<gingeropolous\></strong> so, not accepting a pull request because of poor documentation?  
<strong>\<xmrcoma\></strong> tewinget practice of documenting while coding is a best practice  
<strong>\<endogenic\></strong> and it can degrade in quality if an owner or class of developer is not designated  
<strong>\<imans\></strong> I do agree with that. good documentation can seemlessly help new devs get involved easily  
<strong>\<\_Slack\> \<nanoakron\></strong> @gingeropoulos I mean something like ‘I’ve written this new function to calculate X but haven’t given any documentation’ and then 2 months later someone new comes along, never realised that function existed because there was no documentation, and then just trying to rewrite their own version.  
<strong>\<moneromooo\></strong> But how would you find it in the doc, if you don’t find it in the source ?  
<strong>\<\_Slack\> \<nanoakron\></strong> What we need is a common documentation site and to pay someone to do about a week’s work to pore over the code and fully document every function  
<strong>\<+hyc\></strong> exactly  
<strong>\<+hyc\></strong> new devs must search, regardless.  
<strong>\<moneromooo\></strong> (not saying it’s a bad idea here, mind)  
<strong>\<gingeropolous\></strong> nanoakron, i think thats what tewinget was up to at one point :)  
<strong>\<+hyc\></strong> on the other hand, I like tools like doxygen, document as you code is always a good approach  
<strong>\<\_Slack\> \<nanoakron\></strong> Would be easier to search a wiki for ‘check hard fork version’ and get a bunch of matching functions from which you can pick  
<strong>\<moneromooo\></strong> I do: git grep check.<em>hard.<em>fork :)  
<strong>\<moneromooo\></strong> But ok, fair enough.  
<strong>\<moneromooo\></strong> I think encouraging doc is good, ust not sure it should be enforced, at least for now.  
<strong>\<\_Slack\> \<nanoakron\></strong> But again, it’s a bit chicken and egg - good documentation begets good documentation. It’s getting over that original hurdle to actually make it happen  
<strong>\<gingeropolous\></strong> yeah I think its a “Would Be Nice” thing, and during a PR review, it would be noted - like “hey, you should totally comment this up”  
<strong>\<gingeropolous\></strong> and then if the dev doesn’t comment it up, then its a judgement call over how important the feature is  
<strong>\<\_Slack\> \<nanoakron\></strong> I agree moneromooo, we can’t enforce without a good standard or common place to record the documentation  
<strong>\<endogenic\></strong> nanoakron: +1  
<strong>\<+hyc\></strong> I’m cool with mandating Doxygen comments, moving forward.  
<strong>\<moneromooo\></strong> I agree than modifying a function with a doxygen doc thing should also change to doc thing to match. That’s a NAK offense :)  
<strong>\<endogenic\></strong> another thing to consider is that git commit messages are a kind of documentation. maybe we need to codify the standards in a public official place  
<strong>\<moneromooo\></strong> So I’ll add language to encourage documenting stuff.  
<strong>\<\_Slack\> \<nanoakron\></strong> Starting off a forum funding goal for someone to pull together all the function, variable and class lists would be worthwhile  
<strong>\<+hyc\></strong> nanoakron: I disagree.  
<strong>\<\_Slack\> \<nanoakron\></strong> Could you also add language telling us how to do the documentation - I’ve never used doxygen  
<strong>\<+hyc\></strong> lots of effort to maintain a moving target.  
<strong>\<moneromooo\></strong> I just copy/paste an existing one and adapt.  
<strong>\<TedTheFicus\></strong> Yes, I’d contribute funding to that  
<strong>\<+hyc\></strong> but that’s the sort of thing doxygen already takes care of  
<strong>\<moneromooo\></strong> And I agree with hyc here. An inventory now would be wasted, mostly.  
<strong>\<+hyc\></strong> so if we start using it now, then over time it will build itself  
<strong>\<\_Slack\> \<nanoakron\></strong> The target won’t move though. Let me choose a random example. Do you really think cryptonote\_core::blockchain::pop\_block\_from\_blockchain is going to be deprecated any time soon?  
<strong>\<\_Slack\> \<nanoakron\></strong> Someone had to write the domesday book…  
<strong>\<imans\></strong> But, this is going to be a big sub project if you document everything. You need lot of time and effort  
<strong>\<moneromooo\></strong> Unlikely. I would look suspiciously at a patch using it though :P  
<strong>\<\_Slack\> \<nanoakron\></strong> In which case the person patching could just fix up the doc at the same time :slightly\_smiling\_face:  
<strong>\<+hyc\></strong> indeed, most of the existing functions only have legitimate use internally, not by 3rd parties  
<strong>\<imans\></strong> If you add use cases it would be very much helpful  
<strong>\<moneromooo\></strong> But hey, if you want to do that, feel free. Maybe it will turn out to be a great idea in retrospect.  
<strong>\<endogenic\></strong> what are the problems for which we need to provide documentation at this moment? if we categorize the instances of those problems we might find that it can work quite well to have task- or case-based documentation as a distinct project from going through the source and applying doxygen comments to everything for a whole-API reference  
<strong>\<\_Slack\> \<nanoakron\></strong> Do we have anywhere common where I can read about doxygen or using doxygen wrt monero now?  
<strong>\<moneromooo\></strong> Well, applying doxygen comments is, by itself, pointless (even worse, as it makes it harder to read the API). Semantics in the doxygen comments are what’s good, and that needs understanding of the code.  
<strong>\<imans\></strong> An errata list is good which will help people to trace out the errors they meet  
<strong>\<+hyc\></strong> what errata list? the github issues list?  
<strong>\<imans\></strong> Also, a stackexchange like documentation system which will enable users to post their comments and also raise issues they face.  
<strong>\<imans\></strong> Yes, hyc similar to that  
<strong>\<moneromooo\></strong> endogenic: I think nanoakron originally wanted a map from “I want to do that” to “use this”. I think.  
<strong>\<\_Slack\> \<nanoakron\></strong> @moneromooo yes  
<strong>\<\_Slack\> \<nanoakron\></strong> @imans Not entirely sure how that would be different from the existing github  
<strong>\<imans\></strong> It will not be different. But it aids new comers and users to interact more closely  
<strong>\<\_Slack\> \<nanoakron\></strong> @imans …  
<strong>\<endogenic\></strong> imans: thought we already have a SE?  
<strong>\<imans\></strong> I mean it for API + third party integrations  
<strong>\<endogenic\></strong> why not just create a new category?  
<strong>\<+hyc\></strong> yes, at a certain point, new devs are just going to have to learn to use the tools that already exist  
<strong>\<imans\></strong> yes, the same I say  
<strong>\<+hyc\></strong> otherwise we spin our wheels adding infrastructure instead of functionality  
<strong>\<\_Slack\> \<nanoakron\></strong> @hyc That’s absolutely fine…so long as those tools themselves are well documented :slightly\_smiling\_face:  
<strong>\<gingeropolous\></strong> well the github wiki was requested for (i think) something related to this purpose, and it hasn’t received any attention  
<strong>\<\_Slack\> \<nanoakron\></strong> afk 10 mins  
<strong>\<moneromooo\></strong> That sounds like a good idea. Start with a “list of useful functions someone may need” in that wiki. See how it goes.  
<strong>\<moneromooo\></strong> And it doesn’t seem like a huge waste of time.  
<strong>\<gingeropolous\></strong> yeah, i mean if a random dev stumbles into monero, presumably they goto the github for code, so that wiki is probably where they’ll go first  
<strong>\<+hyc\></strong> I’ve never seen it… :P  
<strong>\<moneromooo\></strong> I’ve only seen it because I was given alink to it :D  
<strong>\<gingeropolous\></strong> hehehe. at the minimu, I can dump the rpc documentation thats on getmonero.org into it via the power of copy and paste  
<strong>\<+hyc\></strong> sounds like a good start  
<strong>\<+hyc\></strong> most 3rd party integrations should be RPC anyway  
<strong>\<gingeropolous\></strong> so i missed the beginning. is this the general topic of “where’s the docs?”  
<strong>\<imans\></strong> If development work for API is finished and you want it to take to third parties. Create illustrations about integration for every industry you want to focus or you think monero should be a partner with. Attach it to the wiki  
<strong>\<moneromooo\></strong> And that’s going to totally change soon.  
<strong>\<gingeropolous\></strong> right.  
<strong>\<moneromooo\></strong> Anyway, any other arguments/ideas about documentation ?  
<strong>\<gingeropolous\></strong> well the 2 will co-exist for a while, right?  
<strong>\<moneromooo\></strong> Yes.  
<strong>\<imans\></strong> I think documentation is not the main focus for this meeting? What is aimed to discuss today?  
<strong>\<moneromooo\></strong> Whatever development related stuff people want to talk about.  
<strong>\<pero\></strong> the documentary i think  
<strong>\<imans\></strong> nice  
<strong>\<moneromooo\></strong> hyc: have you had some more thoughts about how to make a lmdb based wallet data file ?  
\*\*\<medusa</em>\></em></em> i have nothing to say about documentation, but i want to encourage everybody to build and try the gui :-)  
<em><em>\<dEBRUYNE\>\*</em> <strong>\<moneromooo\></strong> Whatever development related stuff people want to talk about. \<= jaquee and I can give a few GUI updates soon^tm  
<strong>\<+hyc\></strong> I’ve been thinking about how to integrate encryption, yes  
<strong>\<+hyc\></strong> but no new code written yet  
<strong>\<pero\></strong> soon is a little ambiguous - closer to 10min or 10weeks?  
<strong>\<dEBRUYNE\></strong> pero: whenever the current topic of the meeting is finished :P  
<strong>\<moneromooo\></strong> Well, let’s have dEBRUYNE and jaquee then.  
<strong>\<dEBRUYNE\></strong> So right now  
<strong>\<dEBRUYNE\></strong> Ok so, fluffypony is in the process of building beta binaries  
<strong>\<dEBRUYNE\></strong> Building went fine, but there is a little issue on windows with hardware acceleration, i.e., the GUI won’t run if that is disabled  
<strong>\<dEBRUYNE\></strong> However, we suspect that on “normal” systems it won’t be an issue, because it’s enabled by default there  
<strong>\<moneromooo\></strong> Mesa might help ?  
<strong>\<dEBRUYNE\></strong> luigi and Articmine are going to test this tomorrow when Fluffypony returns  
<strong>\<moneromooo\></strong> Cool, thanks all :)  
<strong>\<+hyc\></strong> sheesh, it’s a wallet nota videogame. what acceleration does it want…  
<strong>\<xmrcoma\></strong> lets waive a magic want that will cause all windows users worldwide to swtich to linux overnight. issue solved  
<strong>\<moneromooo\></strong> It’s using OpenGL for its widget set apparently.  
<strong>\<dEBRUYNE\></strong> It’s fairly trivial to enable too on windows systems  
<strong>\<moneromooo\></strong> Got had by this when I tried it a few days back.  
<strong>\<dEBRUYNE\></strong> Fluffypony ran into the issue because he was building on a windows server  
<strong>\<@ArticMine\></strong> Basically Windows computers with really ancient graphics and certain virtual machine implementations of Windows have this hardware acceleration issue  
<strong>\<eyejay\></strong> a clear deal breaker. it’s ded  
<strong>\<jaquee\></strong> exactly. so it’s not a really big issue imo  
<strong>\<+hyc\></strong> QT is requiring this dependency?  
<strong>\<@ArticMine\></strong> Windows server is the other case since it uses very minimal graphics by design  
<strong>\<jaquee\></strong> yes some QT widgets requires it  
<strong>\<@ArticMine\></strong> Yes the dependency is from QT on Windows  
<strong>\<moneromooo\></strong> <http://stackoverflow.com/questions/18794201/using-qt-without-opengl> seems to imply Qt can be built without opengl.  
<strong>\<+hyc\></strong> nuts… I mean, OpenGL isn’t even intended for 2D graphics. It’s 3D gaming stuff.  
<strong>\<gingeropolous\></strong> based on my statistical analysis of the clouds I’m sure 95% of people requiring windows GUI are running windows 10 because they upgrade because it told them to  
<strong>\<gingeropolous\></strong> that said, the remaining 5% will be the loudest  
<strong>\<medusa\_\></strong> i bet its that truning thing when refreshing  
<strong>\<moneromooo\></strong> AFAICT, 2D acceleration in new GPUs is a bit shit, and using 3D with orthonormal projection is actually faster.  
<strong>\<imans\></strong> isn’t it designed to support all windows version?  
<strong>\<@ArticMine\></strong> Windows 10 is not an issue unless some very special customization’s are made  
<strong>\<iDunk\></strong> but all windows versions are not designed to support it  
<strong>\<imans\></strong> Haha, iDunk clever  
<strong>\<iDunk\></strong> ;)  
<strong>\<imans\></strong> Enable switches or options to turn on/off opengl support and its related stuff in the wallet.  
<strong>\<dEBRUYNE\></strong> I think realistically speaking, only a negligible percentage of users will run into the issue  
<strong>\<@ArticMine\></strong> Well XP will support it on most later XP computers  
<strong>\<dEBRUYNE\></strong> And they can turn it on fairly easy  
<strong>\<dEBRUYNE\></strong> (in the rare case it’s disabled by default)  
<strong>\<moneromooo\></strong> Anything else about the GUI ?  
<strong>\<pero\></strong> i was hoping the default file path -related issues on linux would be fixed before any binaries got into the wild - the github issues are still open so i take it that hasn’t happened?  
<strong>\<dEBRUYNE\></strong> <strong>\<moneromooo\></strong> Anything else about the GUI ? \<= I think jaquee wanted to tell a bit on what he is working on and what he’ll be working on in the future  
<strong>\<jaquee\></strong> yes  
<strong>\<moneromooo\></strong> jaquee: please do :)  
<strong>\<imans\></strong> Well, I would also like to add another option. Add an option to sync from the local blockchain or simply act as a light wallet. This will help the gui to both work as light or core wallet.  
<strong>\<moneromooo\></strong> (14 minutes till kovri meeting)  
<strong>\<imans\></strong> okay, waiting  
<strong>\<TedTheFicus\></strong> Yes, that is a good idea  
<strong>\<jaquee\></strong> i’m currently working on the wallet selector issue  
<strong>\<jaquee\></strong> open wallet form file… switch wallet etc  
<strong>\<imans\></strong> good to hear  
<strong>\<jaquee\></strong> and i will also fix the default path on linux  
<strong>\<imans\></strong> fine.  
<strong>\<jaquee\></strong> hower i won’t be finished today  
<strong>\<pero\></strong> o/  
<strong>\<jaquee\></strong> so it has ot wait until next release  
<strong>\<imans\></strong> It won’t be an issue  
<strong>\<xmrcoma\></strong> no neeed to finish today jaquee. thanks for your hard work. From a strategic point of view GUI release before Oct 28 (zcash release) would be helpful  
<strong>\<jaquee\></strong> if the windows binaries gets built tomorrow  
<strong>\<jaquee\></strong> and after that i’m gonna work on whatever the commuity feels most prioritized  
<strong>\<moneromooo\></strong> That’s cool, thanks jaquee.  
<strong>\<jaquee\></strong> like the plugin system or better integration with daemon  
<strong>\<TedTheFicus\></strong> Can anyone in the know comment on (xmrcomas) statement?  
<strong>\<moneromooo\></strong> If we’re going to have binaries flying around, I think things like validation, avoiding user being dumb, etc, are a good thing to focus on.  
<strong>\<jaquee\></strong> yes. we could improve the ux with better validation  
<strong>\<moneromooo\></strong> About what ? Wanting binaries before 28 ?  
<strong>\<imans\></strong> Create use cases  
<strong>\<medusa\_\></strong> yes personally i think all the dangerous stuff is fixed, at least im not aware of any  
<strong>\<endogenic\></strong> i was also concerned to see that someone attempting to run a macos binary of the gui wallet the other day got a crash about a dynamic library not having been able to be loaded — and i believe we found out that it was boost which wasn’t installed — for the gui release, will there be an installer for mac os to take care of such dependencies?  
<strong>\<medusa\_\></strong> the mian thing is that the “open from keys file” usecase is missing and windows suers chan not easily switch wallets  
<strong>\<moneromooo\></strong> Niece. Thanks for testing medusa</em> :)  
<strong>\<moneromooo\></strong> Probably just build boost statically.  
<strong>\<jaquee\></strong> endogenic: I think that’s a build issue. Won’t affect the binaries afaik  
<strong>\<+hyc\></strong> shouldn’t we be building this with statically linked libboost?  
<strong>\<endogenic\></strong> jaquee: ok, excellent  
<strong>\<hiall\></strong> when official gui wallet out?  
<strong>\<gingeropolous\></strong> about 2 weeks  
<strong>\<moneromooo\></strong> Anything else you want to add, jaquee ?  
<strong>\<jaquee\></strong> nope  
<strong>\<TedTheFicus\></strong> There is no date, it was just discussed now and testing is being done.  
<strong>\<moneromooo\></strong> Anyone else want to talk about dev stuff for 6 minutes ?  
<strong>\<dEBRUYNE\></strong> hiall: Read the backlogs :P  
<strong>\<\_Slack\> \<nanoakron\></strong> Thanks @jaquee for all the GUI work. Two other issues I wanted to raise during this meeting were (a) killing dead issues on github and (b) formalising the log levels. WRT log levels, I don’t mind going through the code and changing all log outputs to the correct level if we can agree what those should be, in advance of a better programmer changing the logging subsystem itself. Please see and comment on <https://github.com/monero-project/monero>  
<strong>\<tompole\></strong> Can someone confirm that the languages page has been scrubbed from the GUI?  
<strong>\<endogenic\></strong> i do want to mention i don’t think any normal user would install boost on their own — and the crash itself wouldn’t be acceptable as a graceful failure fmpov as a product guy  
<strong>\<moneromooo\></strong> I’d leave any level change till after the log system change, let’s not waste work.  
<strong>\<hiall\></strong> so GUI release this month? :O  
<strong>\<\_Slack\> \<nanoakron\></strong> @moneromooo OK makes sense  
<strong>\<moneromooo\></strong> tompole: it’s here as of today, just with only en\_US IIRC.  
<strong>\<dEBRUYNE\></strong> \<tompole\>\*\* Can someone confirm that the languages page has been scrubbed from the GUI? <em><em>\<= Yeah, translations aren’t done yet  
<strong>\<jaquee\></strong> tompole: yes we’ve removed all languages except english for now until translations are finsihed  
<strong>\<sdgsdug9sd\></strong> if the issues with hardware acceleration get fixed in time, the gui should come out before oct 28 right?  
<strong>\<\_Slack\> \<nanoakron\></strong> Still inviting comments on the discussion though  
<strong>\<tompole\></strong> Okay cool, thanks.  
<strong>\<dEBRUYNE\></strong> I’ll put the strings on transifex next week  
<strong>\<dEBRUYNE\></strong> Such that the community can help translating  
<strong>\<dEBRUYNE\></strong> then we can enable them again  
<strong>\<moneromooo\></strong> As for killing closed bugs, that’ll happen, once the pony gets a minute. He has logs with issues list.  
<strong>\<imans\></strong> I just started to compile one for my ubuntu 15.10  
<strong>\<endogenic\></strong> i’m curious to know how qt was chosen as the gui lib, if anyone can comment  
<strong>\<moneromooo\></strong> For people wanting to read the kovri meeting a 3 minutes, that’ll be on \#kovri-dev  
<strong>\<+hyc\></strong> qt is multi-platform, seems a reasonable choice  
<strong>\<\_Slack\> \<nanoakron\></strong> Thanks all. See you around\!  
<strong>\<moneromooo\></strong> The other main one is GTK. Or.. custom :D  
<strong>\<moneromooo\></strong> WxWidgets maybe.  
<strong>\<i2p-relay\></strong> {-anonimal} \#kovri-dev topics today will be API and resolving the logo.  
<strong>\<+hyc\></strong> gtk is atrocious. yeah mebbe wxwidgets  
<strong>\<moneromooo\></strong> Java :o  
<strong>\<\_Slack\> \<dadude\></strong> libgui?  
<strong>\<hiall\></strong> so there is a possibility that we see gui before end of october?  
<strong>\<sdgsdug9sd\></strong> expected date for release of the gui?  
<strong>\<\_Slack\> \<dadude\></strong> libui sorry <https://github.com/andlabs/libui>  
<strong>\<gingeropolous\></strong> there’s always a possibility  
<strong>\<moneromooo\></strong> Oh my. Maybe in november.  
<strong>\<TedTheFicus\></strong> It is possible yes. Have a look on GitHub under project MonerCore to gauge the status  
<strong>\<moneromooo\></strong> December, otherwise.  
\*\*\<medusa</em>\></em>\* next year guys  
<strong>\<sdgsdug9sd\></strong> lol  
<strong>\<tompole\></strong> 2018  
<strong>\<@ArticMine\></strong> hiall A possibility Yes; Promises: No  
<strong>\<gingeropolous\></strong> now the probability of that possibility is a different story  
<strong>\<xmrcoma\></strong> 2018 sounds like fud. I say 2017 at the latest  
<strong>\<TedTheFicus\></strong> Thanks for all your hard work everyone\!  
<strong>\<moneromooo\></strong> For people wanting to read the kovri meeting 1 a minute, that’ll be on \#kovri-dev  
<strong>\<moneromooo\></strong> Thanks all  
<strong>\<tompole\></strong> Monero doesn’t need to be concerned with tending to deadlines that relate to other projects.  
<strong>\<gingeropolous\></strong> ONWARD MONERO\!  
<em><em>\<kali</em>\></em>\* Thanks guys\!  
<strong>\<+hyc\></strong> bye all  
<strong>\<@ArticMine\></strong> I am going there now.  
<em><em>\<medusa</em>\></em>\* thaks people, good luck and rock on  
<strong>\<sdgsdug9sd\></strong> on a serious note though, can someone just tell whats the anticipated date for gui release?  
<strong>\<gingeropolous\></strong> no  
<strong>\<kkhugs\></strong> @moneromoo thanks for that address verification wallet API pr  
<strong>\<sdgsdug9sd\></strong> why?  
<strong>\<gingeropolous\></strong> because development  
<strong>\<notyomomma\></strong> monero should be concerned with the needs of the user - which is the gui. I think the questions on timing are relevant  
<strong>\<\_Slack\> \<xmr\_eric\></strong> lol  
<strong>\<xmrcoma\></strong> gui will be done when it is done. not 1 day before or after  
<strong>\<moneromooo\></strong> sdgsdug9sd: apparently tomorrow  
<strong>\<xmrcoma\></strong> soon. tm  
<strong>\<moneromooo\></strong> (or so I read above)  
<strong>\<gingeropolous\></strong> well, its been 2.5 years  
<strong>\<pero\></strong> before the documentary  
<strong>\<pero\></strong> i think everyone can commit to that?  
<strong>\<dEBRUYNE\></strong> Like I said above, luigi &amp; ArticMine will test on windows systems tomorrow  
<strong>\<moneromooo\></strong> it’s a bit rickety still though  
<strong>\<dEBRUYNE\></strong> if there is no issue there, I see no reason to not put the beta release out  
<strong>\<endogenic\></strong> exciting  
<strong>\<dEBRUYNE\></strong> there can be a subsequent release when the linux path issue, wallet choosing issue, are fixed  
<strong>\<xmrcoma\></strong> I saw forget windows. just release for linux and make everyone convert:)  
<strong>\<sdgsdug9sd\></strong> hmmm, not sure im getting this clear. so, its expected to be released tomorrow but no later than oct 28?  
<strong>\<xmrcoma\></strong> f miscrosoft  
<strong>\<moneromooo\></strong> Unless tomorrow forgets to end, I guess.  
<strong>\<xmrcoma\></strong> sdg 2017 at the latest  
<strong>\<pero\></strong> the reason behind the prioritizing the file paths is that we’ll see an influx of ‘noobs’ asking if this or that directory can be safely deleted  
<strong>\<xmrcoma\></strong> but maybe tomorrow:)  
<strong>\<gingeropolous\></strong> moneromooo, lulz  
<strong>\<dEBRUYNE\></strong> No testing is tomorrow, if that is fine the bins can be put out  
<strong>\<dEBRUYNE\></strong> but that isn’t necesarily tomorrow too  
<strong>\<dEBRUYNE\></strong> :P  
<strong>\<hiall\></strong> gui testing tomorrow?  
<strong>\<moneromooo\></strong> Oh, multi day testing. Fair enough. Ignore me.  
<strong>\<ontario\></strong> noob question here , when the gui is released can we mine directly to gui wallet?  
<strong>\<moneromooo\></strong> Later, yes. Not yet.  
<strong>\<sdgsdug9sd\></strong> alrighty, what about kovri release? shouldnt it be december 2016?  
<strong>\<dEBRUYNE\></strong> moneromooo: you could put your GUI wallet address in the daemon though  
<strong>\<xmrcoma\></strong> can someone comment on this? <https://www.youtube.com/watch?v=dQw4w9WgXcQ>  
<strong>\<moneromooo\></strong> dEBRUYNE: what do you mean ?  
<strong>\<\_Slack\> \<dadude\></strong> rickrooool\!  
<strong>\<dEBRUYNE\></strong> moneromooo: just start\_mining in the daemon  
<strong>\<\_Slack\> \<dadude\></strong> it ends in XcQ  
<strong>\<dEBRUYNE\></strong> and then your GUI address  
<strong>\<dEBRUYNE\></strong> you need a daemon running to use the GUi anyway  
<strong>\<moneromooo\></strong> Hmm, yes. That was not the question though I think.  
<strong>\<dEBRUYNE\></strong> But that’s more of a way around :P I think the guy meant mining directly in the GUI  
\*\*\<moneromooo\>\*\* Oh, \*to\*, actually you’re right.  
<strong>\<tompole\></strong> You mean you still need a terminal window open in order for the GUI to work?
