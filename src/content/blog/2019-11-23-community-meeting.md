---
title: Logs for the Community Meeting Held on 2019-11-23
tags: [dev diaries, crypto]
author: asymptotically / SamsungGalaxyPlayer
---

# Logs

<strong>\<sgp\_\></strong> Meeting time  
<strong>\<sgp\_\></strong> 0. Introduction  
<strong>\<needmonero90\></strong> Hi diego  
<strong>\<sgp\_\></strong> Welcome to the Emergency Response Process and Compromised Binaries Post-Mortem Meeting. Today, we shall discuss the information we know so far about the compromised binaries and introduce ideas to better respond to emergencies in the future.  
<strong>\<sgp\_\></strong> It’s later than most of our meetings, so thank you for coming at this unusual time.  
<strong>\<sgp\_\></strong> 1. Greetings  
<strong>\<needmonero90\></strong> Hello\!  
<strong>\<M5M400\></strong> Servus\!  
<strong>\<rehrar\></strong> h'lo  
<strong>\<binaryFate\></strong> hi  
<strong>\<pizzaburger\></strong> Good day\!  
<strong>\<anhdres2\></strong> hola\!  
<strong>\<mrpublic\></strong> top o the mornin'  
<strong>\<intj440\></strong> Hello  
<strong>\<needmonero90\></strong> Is the fluffiest pony here this evening?  
<strong>\<sgp\_\></strong> Welcome everyone\! There is a lot to cover, so let's move methodically so that we can respect those staying up late  
<strong>\<sgp\_\></strong> <https://github.com/monero-project/meta/issues/413>  
<strong>\<sgp\_\></strong> 2. Website compromised facts and review  
<strong>\<el00ruobuob\_\[m\]\></strong> Hi  
<strong>\<ArticMine\></strong> hi  
<strong>\<sgp\_\></strong> long set of text incoming describing the situation, including new information  
<strong>\<almutasim\></strong> Hello.  
<strong>\<sgp\_\></strong> Here is a short timeline of the events that unfolded earlier this week:  
<strong>\<sgp\_\></strong> Relevant blog post: <https://getmonero.org/2019/11/19/warning-compromised-binaries.html>  
<strong>\<sgp\_\></strong> The CLI binaries were compromised for approximately 35 minutes on Monday  
<strong>\<sgp\_\></strong> The attackers did not modify the hashes on the website  
<strong>\<needmonero90\></strong> Is that time frame known for certain?  
<strong>\<sgp\_\></strong> Core team member binaryFate created a Reddit post and messaged me about it on IRC. He shared it on his personal Twitter account  
<strong>\<needmonero90\></strong> Did the logs get pulled?  
<strong>\<sgp\_\></strong> needmonero90: I will cover the exact time frame near the end of this wall :)  
<strong>\<needmonero90\></strong> Mmk  
<strong>\<sgp\_\></strong> Reddit link: <https://www.reddit.com/r/Monero/comments/dyfozs/security\_warning\_cli\_binaries\_available\_on/>  
— needmonero90 waits patiently  
<strong>\<sgp\_\></strong> I found it likely that this was true given binaryFate’s position and that it was shared on three different mediums. Thus, I immediately sent Blockfolio, CoinGecko, and Delta notifications. I created a tweet from the Monero Twitter account  
<strong>\<sgp\_\></strong> Note that although I have partial access to the Monero Twitter account, I am not the primary owner or maintainer of it, and the tweet I created was an exception for the circumstances  
<strong>\<sgp\_\></strong> I also contacted the other moderators of r/CryptoCurrency, who agreed to allow an announcement about the situation in r/CryptoCurrency  
<strong>\<sgp\_\></strong> ErCiccione authored an announcement on the website about 14 hours after the incident was initially reported. An email to the Monero-announce mailing list went out around the same time.  
<strong>\<sgp\_\></strong> Approximately 12 hours after the sending the Blockfolio notification, it had 14,673 impressions and 259 clicks. Today, it has 25,308 impressions and 326 clicks. I don't have numbers for the other portfolio platforms.  
<strong>\<sgp\_\></strong> The Reddit thread has nearly 300 upvotes and nearly 300 comments.  
<strong>\<sgp\_\></strong> Twitter reports that the initial tweet has 100,918 impressions and 1,455 engagements.  
<strong>\<sgp\_\></strong> Major and minor news sites picked up on the story, including Naked Security, Crypto Briefing, The Next Web, Ars Technica, ZDNet, CoinGeek, Fossbytes, CoinTelegraph, Bleeping Computer, AMBCrypto, Bitcoinist, Coingape, Finder, and Decrypt.  
<strong>\<sgp\_\></strong> There are a few writeups on the content of the malware:  
<strong>\<sgp\_\></strong> Bartblaze: <https://bartblaze.blogspot.com/2019/11/monero-project-compromised.html>  
<strong>\<sgp\_\></strong> serhack: <https://serhack.me/articles/cli-binaries-compromised-monero-analysis/>  
<strong>\<sgp\_\></strong> They both determined that the malware was a simple coin stealer. KnifeOfPi also came to the same determination.  
<strong>\<sgp\_\></strong> Now, on to the website information.  
<strong>\<sgp\_\></strong> I can answer a few more questions than I could before, but I can’t answer everything yet, including how the website was compromised. I have no insider info there  
<strong>\<sgp\_\></strong> Security professionals have been working to learn more information. The security team has promised their post-mortem when they have more details.  
<strong>\<sgp\_\></strong> The downloads are served by two sources: the CDN and the source. The CDN binaries were not affected, which are the preferred sources. The source is fallback.  
<strong>\<sgp\_\></strong> After the hack, the security admins temporarily turned logging on with the DR download box (which was switched to) in case someone was trying to hack it. A benefit of this is that we learned there are typically fewer than 10 wallet downloads per hour from the direct source.  
<strong>\<sgp\_\></strong> I can also confirm that 35 minutes is the \*maximum\* time that the malicious binaries were served. The file integrity monitor (FIM) was killed 35 minutes before fluffypony initiated the failover to the backup DR box. If the attackers replaced the files immediately after, then the website was compromised for 35 minutes.  
<strong>\<sgp\_\></strong> Full timeline:  
<strong>\<sgp\_\></strong> The FIM’s last log entry was at 16:04 UTC (10:04 CST) - malicious binaries were not served before this point  
<strong>\<sgp\_\></strong> A Github issue was created at 16:21 UTC  
<strong>\<sgp\_\></strong> A community member privately informed site admins at 16:30 UTC  
<strong>\<sgp\_\></strong> fluffypony switched to the failover at 16:40 UTC  
<strong>\<sgp\_\></strong> The maximum compromised time was between 16:04 UTC and 16:40 UTC Monday November 18  
<strong>\<sgp\_\></strong> Since they were served for only 35 minutes, it’s highly likely that fewer than 10 malicious downloads were served. Among these, some were presumably updating their nodes, not running wallets.  
<strong>\<sgp\_\></strong> and that brings us to the end of the wall of text  
<strong>\<sgp\_\></strong> Does anyone have questions or comments on what happened? I won’t be able to answer some of them unfortunately but I’ll do my best.  
<strong>\<M5M400\></strong> one question comes to mind: HOW?  
<strong>\<needmonero90\></strong> The security researchers are dealing with the box atm  
<strong>\<needmonero90\></strong> We'll probably only know after their analysis  
<strong>\<sgp\_\></strong> M5M400: that's an important question that I don't really have the answer to  
<strong>\<sgp\_\></strong> But I am certain that a dedicated team is digging through the boxes  
<strong>\<DarkDotFail\></strong> Hi Justin - What does "DR" stand for?  
<strong>\<M5M400\></strong> disaster recovery  
<strong>\<needmonero90\></strong> Disaster Recovery  
<strong>\<DarkDotFail\></strong> "it’s highly likely that fewer than 10 malicious downloads were served" - I assume this is based on logs? How confident are you in this count?  
<strong>\<sgp\_\></strong> I find it remarkable that two independent community members reported on the issue within 30 minutes  
<strong>\<M5M400\></strong> when did fluffy upload the original files? ie, how long did it take them from upload to replacment?  
<strong>\<Supportoi\></strong> Sio  
<strong>\<sgp\_\></strong> DarkDotFail: unless there was a significant anomaly (3+ sd downloads over that period), then I am very confident. So I'd say \>95% confident  
<strong>\<Supportoi\></strong> Any news?  
<strong>\<HungryForAvo420\></strong> Are there any plans to periodically check sha256 hashes?  
<strong>\<sgp\_\></strong> There are almost never more than 10 downloads/hr. And it was compromised for 35 minutes  
<strong>\<DarkDotFail\></strong> Who has server access, and what is the process for giving someone server access?  
<strong>\<Supportoi\></strong> I read about hacking this is Russian hackers  
<strong>\<sgp\_\></strong> Supportoi: there is no evidence I know of that suggests this  
<strong>\<anhdres\></strong> is it my non-techie impression or we got very lucky here? I mean we only realized it because someone that downloaded the CLI checked the hashes AND they didn't change the hashes accordingly  
<strong>\<Supportoi\></strong> I downloaded this fkng cli  
<strong>\<needmonero90\></strong> Changing the hashes would have required compromising a second box  
<strong>\<Supportoi\></strong> I'm not infected?  
<strong>\<Supportoi\></strong> My money not stolen  
<strong>\<sgp\_\></strong> Supportoi: when did you download the cli exactly?  
<strong>\<Supportoi\></strong> But I worry about my PC  
<strong>\<anhdres\></strong> needmonero90, ok  
<strong>\<Supportoi\></strong> 18th  
<strong>\<sgp\_\></strong> DarkDotFail: I do not have a full list  
<strong>\<sgp\_\></strong> Supportoi: what time and what time zone?  
<strong>\<DarkDotFail\></strong> and regarding the process of granting access, how is it determined who should have access?  
<strong>\<needmonero90\></strong> As few people as is realistically possible  
<strong>\<Supportoi\></strong> SHA is eq to SHA of infected files  
<strong>\<almutasim\></strong> It's really good that changing the hashes requires hacking a second box.  
<strong>\<rehrar\></strong> DarkDotFail Tari or Globee hosts the getmonero infrastructure  
<strong>\<xmrscott\[m\]\></strong> Supportoi: Verify your hashes, that will conclusively tell you if it's the nalicious binary  
<strong>\<rehrar\></strong> the details would have to be asked of them  
<strong>\<anhdres\></strong> is there a way to have a bot somewhere else doing just what the human user did by chance? I mean downlaoding the files regularly and checking the hashes to see they match, and if they don't issue an alarm?  
<strong>\<DarkDotFail\></strong> anhdres: I am working on precisely that :)  
<strong>\<sgp\_\></strong> anhdres: while technically possible, this service would probably be blocked as a DoS attack  
<strong>\<needmonero90\></strong> That would be a tiny DOS on the server, and if done with a consistent IP, it's possible to serve uninfected binaries to the pollers  
<strong>\<Supportoi\></strong> Fkng Russian hackers  
<strong>\<anhdres\></strong> mmmm...  
<strong>\<sgp\_\></strong> there are a stupid number of people who constantly are trying to download the 55GB blockchain.raw  
<strong>\<M5M400\></strong> when did fluffy upload the original files? ie, how long did it take them from original upload to replacment with compromised bins?  
<strong>\<needmonero90\></strong> Supportoi: please keep on topic, speculation on who did this is unwarranted at the moment.  
<strong>\<needmonero90\></strong> We will know more after the post mortem  
<strong>\<Supportoi\></strong> I reading news and founded article about some hacking russian forum  
<strong>\<DarkDotFail\></strong> sgp\_: Is there any indication yet that the server was compromised, and how?  
<strong>\<sgp\_\></strong> M5M400: are you referring to the time between the 0.15 safe binary uploads and them being compromised?  
<strong>\<M5M400\></strong> sgp\_: yes  
<strong>\<Supportoi\></strong> Where they have article about monero hacking  
<strong>\<binaryFate\></strong> M5M400 the malicious binaires were compiled from sources, they are not obtained based on the original ones. So it's indepedendant from original upload time.  
<strong>\<Supportoi\></strong> Russian hackerssssssss omg  
<strong>\<sgp\_\></strong> DarkDotFail: yes, I can state that the website WAS compromised, though I do not yet have details on how  
<strong>\<anhdres\></strong> good thing it wasn't the GUI, because those would have been less technical users and therefore less probable they checked the hashes. We need a fool-proof official tutorial to teach how to check them.  
<strong>\<needmonero90\></strong> Supportoi: last warning.  
<strong>\<DarkDotFail\></strong> sgp\_: Has law enforcement been notified about this breach?  
<strong>\<pizzaburger\></strong> Is there a possibility that the attackers were after something else and we just haven't noticed their ulterior motives?  
<strong>\<PewPewPewPew\></strong> ^^  
<strong>\<M5M400\></strong> binaryFate: trying to gauge how premeditated this attack was... ie if they had everything ready and possibly already access to the box for a while, just waiting for new bins to be uploaded and then quickly replacing them...  
<strong>\<sgp\_\></strong> DarkDotFail: no, and we have not yet found a strong reason to. I will make a recommendation that the security researchers do (in addition to their own assessments) if there's a clear reason to. I do not have knowledge on the state of the investigation to make a recommendation  
<strong>\<HungryForAvo420\></strong> What is the decommission schedule for source box? CDN was not impacted, but am wondering what the maintanance is like for Source.  
<strong>\<needmonero90\></strong> I would like to point out that the attack felt rushed/incomplete, from reports I'm hearing. There were many things that could have been done that weren't (infecting the GUI dls for example)  
<strong>\<sgp\_\></strong> pizzaburger: while we can never know for sure what their motivations were, we know the security researchers only found a relatively primitive coin stealer included in the wallet software  
<strong>\<Supportoi\></strong> I'm worry about my privacy. I'm not programmer but I know some in programming and security. My antivirus not detected danger, I runned this file.  
<strong>\<DarkDotFail\></strong> How long has FIM been installed, and has it ever detected other anomalies?  
<strong>\<Supportoi\></strong> And I readed about this forum. This forum contains information about CLI replace  
<strong>\<sgp\_\></strong> DarkDotFail: I do not know for how long, but FIM was disabled by the attacker  
<strong>\<Supportoi\></strong> Somebody know some about this?  
<strong>\<DarkDotFail\></strong> Has FIM ever detected other anomalies?  
<strong>\<needmonero90\></strong> Supportoi: this has nothing to do with the issue at hand. Please stay in topic for the meeting.  
<strong>\<PlasmaPower\></strong> I know you don't know how it was compromised yet, but what were the potential avenues of attack for the box other than an insider threat? The web server, maybe SSH, maybe a cloud provider?  
<strong>\<M5M400\></strong> needmonero90: that's my gut feeling aswell. that's why I was asking how long it took them to replace the bins after initial upload... but I don't seem to get an answer :)  
<strong>\<sgp\_\></strong> DarkDotFail: I do not know about the test environment in which it was tested, but I know there were no other anomalies on the live version of the site  
<strong>\<DarkDotFail\></strong> Thank you. that's very good.  
<strong>\<Supportoi\></strong> I payed 50$ in xmr to body from comments and they gived me screenshot  
\* Supportoi was kicked by needmonero90 (Supportoi)  
<strong>\<sgp\_\></strong> M5M400: I don't know when the original 0.15 binaries were uploaded, but that's something we can check on I suppose  
<strong>\<sgp\_\></strong> Any other questions? Sorry to not have juicy details yet on how this happened  
<strong>\<binaryFate\></strong> this reddit post suggest the 9th: <https://www.reddit.com/r/Monero/comments/dtt2j3/cli\_v01500\_carbon\_chamaeleon\_released/>  
<strong>\<DarkDotFail\></strong> I want to quickly commend Justin and team for the quick response. My complaint is that the public website took over 14 hours to update after the breach, and I suggest we get a quicker "post an alert to the website" process in place. Going AFK for now, but be safe everyone.  
<strong>\<M5M400\></strong> binaryFate: that would speak for the less premeditated "uh, new release. let's try to hack that box and replace with our coinstealer" theory  
<strong>\<rehrar\></strong> honestly, the timing of this seems too good for it to not be premeditated  
<strong>\<xmrscott\[m\]\></strong> binaryFate: Also semi-verified going off of WebArchive for getmonero  
<strong>\<needmonero90\></strong> Processes are being put in place to expedite updates of the public site in the event of a security event. 14 hours was excessive, but we can do better.  
<strong>\<ZaiRoX\></strong> Strange of them not waiting for the GUI release though  
<strong>\<M5M400\></strong> rehrar: why wait 5 days then?  
<strong>\<rehrar\></strong> honestly, who updates CLI early? Exchanges. Services.  
<strong>\<rehrar\></strong> I think they were hoping for big fish.  
<strong>\<binaryFate\></strong> Agree website update has the largest room for improvement.  
<strong>\<M5M400\></strong> rehrar: agreed.  
<strong>\<anhdres\></strong> would a stupid but useful security measure to suggest to newbie users for them to wait a few hours before running a downloaded binary and see if there's any warning on an official channel?  
<strong>\<needmonero90\></strong> Hash checking should be sufficient  
<strong>\<needmonero90\></strong> And signature ofc  
<strong>\<sarang\></strong> With signature verification you know the file is what it is expected to be  
<strong>\<rehrar\></strong> M5M400 you asked why wait 5 days after the new CLI was released?  
<strong>\<needmonero90\></strong> I think prioritizing teaching people how to verify signatures is infinitely better than having them wait for a few hours and hope someone notices  
<strong>\<rehrar\></strong> because if you release ASAP, everyone is downloading and testing. They will catch it right away.  
<strong>\<needmonero90\></strong> That's just me tho  
<strong>\<sgp\_\></strong> they also compromised the website at a relatively convenient time  
<strong>\<M5M400\></strong> rehrar: makes sense  
<strong>\<sgp\_\></strong> time of day  
<strong>\<PlasmaPower\></strong> frankly, even Monero's "beginner" guide to signature verification on Windows is way too long  
<strong>\<anhdres\></strong> ok, and based on that "hacking" the hash to match the compromised binary would be too difficult to pull of, right?  
<strong>\<M5M400\></strong> rehrar: good thing the "big fish" are usually the laziest in updating, I guess...  
<strong>\<rehrar\></strong> PlasmaPower I just spoke about this with another individual that does website stuff.  
<strong>\<sgp\_\></strong> anhdres: it's more realistic to check the hashes haven't changed  
<strong>\<rehrar\></strong> We need to separate verification user guides into three. Linux, Mac, and Windows.  
<strong>\<rehrar\></strong> They won't be so long or scary then.  
<strong>\<sgp\_\></strong> rehrar: good, that's a specific action item  
<strong>\<rehrar\></strong> I was literally helping a person on Telegram and told him to verify hashes and he got scared by how big the page was and how much CLI commands there were  
<strong>\<anhdres\></strong> sgp\_, needmonero90 : got it thanks  
<strong>\<pizzaburger\></strong> Thank you for the information and hard work. Best of luck to the Monero team, bye\!  
<strong>\<PlasmaPower\></strong> rehrar: the Windows specific guide is still long, though not scary except the small part that requires command prompt  
<strong>\<xmrscott\[m\]\></strong> FWIW with respect to timing, domain was bought 11/14. Arguments could be made that a purchase so close to delivering the attack means it wasn't pre-meditated, but best to wait for the official report  
<strong>\<M5M400\></strong> xmrscott\[m\]: ah, I forgot about that domain info. makes perfectly sense  
<strong>\<justalurk3r\></strong> sgp\_: I, too, have downloaded the compromised binaries. If my browser history is right, then it must have happened at 12:24 CET  
<strong>\<anhdres\></strong> would it be too cumbersome to develop a little monero-branded, hash-checking program for windows that required no installation so a very noob could use it practically guide-less?  
<strong>\<M5M400\></strong> sgp\_: any info which hosting company the infected box belongs to?  
<strong>\<sgp\_\></strong> M5M400: I don't know that  
<strong>\<PlasmaPower\></strong> anhdres: I thought about that too, but then what if that binary gets compromised :P  
<strong>\<needmonero90\></strong> Andrhes: and if they compromise that?  
<strong>\<needmonero90\></strong> Jinx  
<strong>\<anhdres\></strong> well, it needs to be in a third box  
<strong>\<sgp\_\></strong> the malicious software would just say "I'm totally safe"  
<strong>\<needmonero90\></strong> 🤔  
<strong>\<cbster\></strong> Yeah, were it too simple I think they'd just change that program too  
<strong>\<anhdres\></strong> if screwing with the hash is "safe" we could do the same with the app  
<strong>\<sarang\></strong> The only guarantee is a full hash and signature check  
<strong>\<needmonero90\></strong> ^  
<strong>\<sarang\></strong> Only doing hash checks is potentially vulnerable  
<strong>\<cbster\></strong> Agreed, a lot of people leave off the signature check  
<strong>\<sarang\></strong> It's annoying but important  
<strong>\<tevador\></strong> one positive aspect of this incident is that people are more likely to verify the hashes from now on  
<strong>\<M5M400\></strong> sgp\_: is there any intersection in the groups of people who research the breach and the group who had access to the box?  
<strong>\<rehrar\></strong> honestly, the entire cryptography space is long overdue for a good UX GUI for hash checking and verification  
<strong>\<rehrar\></strong> one that could be used for all of the programs ever  
<strong>\<needmonero90\></strong> Pgp is pretty good  
<strong>\<anhdres\></strong> rehrar: yes, please  
<strong>\<needmonero90\></strong> ...not  
<strong>\<sarang\></strong> However if you're confident that externally hosted trusted hash lists have not been modified, then a hash check is ok  
<strong>\<PlasmaPower\></strong> Are GitHub release assets generally deemed safer than the website downloads? I don't think they're GPG signed (though the tags themselves can be).  
<strong>\<sgp\_\></strong> PlasmaPower: it's simpler to hack a Github account probably  
<strong>\<HungryForAvo420\></strong> Any consideration in using GitLab? have seen MS owned github drop some repos in some countries  
<strong>\<pca\></strong> Just arrived. How was the box compromised, or does anybody know that information yet?  
<strong>\<tevador\></strong> are we signing git tags?  
<strong>\<sgp\_\></strong> HungryForAvo420: Monero already partially uses Gitlab, but this is mostly irrelevant for the conversation at hand  
<strong>\<M5M400\></strong> pca: not yet  
<strong>\<sgp\_\></strong> For the sake of time, I'm going to warp up this section soon. Most of these questions have been answered in Reddit  
<strong>\<rehrar\></strong> kthanksbai  
<strong>\<PlasmaPower\></strong> tevador: I just checked, yes at least the latest tag was signed and most commits seem to be signed too.  
<strong>\<needmonero90\></strong> Thanks for hosting sgp\_  
<strong>\<sgp\_\></strong> just this section lol  
<strong>\<sgp\_\></strong> still have a few more  
<strong>\<needmonero90\></strong> Oh rip  
<strong>\<sgp\_\></strong> that was just the update and clarification portion  
<strong>\<xmrscott\[m\]\></strong> I was going to, still plenty left to discuss nm90 ;)  
<strong>\<sgp\_\></strong> now time to do actual work  
— needmonero90 nods sheepishly  
<strong>\<sgp\_\></strong> 3. Introduction of emergency procedure  
<strong>\<M5M400\></strong> ah, the big red button  
<strong>\<sgp\_\></strong> I would like to introduce a project to draft more formalized emergency procedures. This procedure will help the community understand what to do if another emergency occurs.  
<strong>\<anhdres2\></strong> haha everybody was "ok good one see ya" and Justin still had the cake untouched  
<strong>\<sgp\_\></strong> <https://github.com/monero-project/meta/issues/412>  
<strong>\<sgp\_\></strong> We can pull from existing resources, including the Monero Vulnerability Response Process and the Monero Malware Response Workgroup.  
<strong>\<sgp\_\></strong> I know that the Monero community has significant concerns about centralization, and these are justified and should be considered carefully. Nevertheless, there are many was that this process can help organize a proper response without having many centralization advantages. And to be clear, it’s not like we can force people to follow a set procedure anyway. All participants’ involvement is entirely voluntary  
<strong>\<sgp\_\></strong> and subject to their own best judgments.  
<strong>\<sgp\_\></strong> I'm currently breaking the procedure into main topic areas: a) safe verification of the emergency, b) classification of the severity, c) communication, d) incident response, e) regular tests/audits, and f) responsible roles, including alternates in case of inactivity.  
<strong>\<sgp\_\></strong> Let’s open discussion on the 6 points that I have above, one at a time. We can talk about what processes (even if informal) we already have, and what you think is a good idea to help with these. If you feel there are any missed topics (likely), please reserve them for later.  
<strong>\<sgp\_\></strong> a. safe verification of the emergency  
<strong>\<sgp\_\></strong> in this case, we didn't have signed messages saying "this was compromised." We simply relied on several trusted accounts. What are our thoughts on this?  
<strong>\<sgp\_\></strong> also related: if people want to contact someone about an emergency, is there a clear disclosure process?  
<strong>\<needmonero90\></strong> The people who would verify signatures of warnings would verify signatures of their binaries  
<strong>\<PlasmaPower\></strong> you mean from the perspective of the user verifying the emergency, not the Monero team verifying the emergency?  
<strong>\<needmonero90\></strong> Trust-y auth is fine here.  
<strong>\<M5M400\></strong> I'm less worried about "fake news" as about response time, so I guess reputable community members breaking the news is fine  
<strong>\<anhdres2\></strong> agree  
<strong>\<cbster\></strong> I agree, even were there a false alarm I can't foresee harm from it  
<strong>\<sgp\_\></strong> needmonero90: is there a certain threshold where you would personally say "hold on a minute, I need some extra verification"?  
<strong>\<sgp\_\></strong> false alerts are unprofessional and also harm the project potentially  
<strong>\<ArticMine\></strong> Provided one relies on decentralization for alarm security  
<strong>\<needmonero90\></strong> If the person was in my web of trust, no. If they were not, I would manually verify sigs  
<strong>\<xmrscott\[m\]\></strong> Wouldn't hurt to have public keys of core members on getmonero  
<strong>\<needmonero90\></strong> Personal webs of trust are fine here, theyre probably just as effective (and faster) than signatures  
<strong>\<sgp\_\></strong> they're definitely faster  
<strong>\<needmonero90\></strong> And that's what should be prioritized imo  
<strong>\<cff97476\></strong> hello to everyone  
<strong>\<needmonero90\></strong> If there's questions, the warning can say it's a question mark  
<strong>\<sgp\_\></strong> I received binaryFate's RC PM and was sending out notifications 2 minutes later  
<strong>\<cff97476\></strong> any news?  
<strong>\<needmonero90\></strong> I had a post stickied on the sub a minute after I got your ping  
<strong>\<sgp\_\></strong> cff97476: scroll up and find section 2  
<strong>\<sgp\_\></strong> ok, so we are all ok with relatively basic identity checks here  
<strong>\<M5M400\></strong> +1  
<strong>\<sgp\_\></strong> no need to require something that would delay the process  
<strong>\<cbster\></strong> +  
<strong>\<sgp\_\></strong> ok, so the second question  
<strong>\<needmonero90\></strong> False positives are better than delayed warnings  
<strong>\<ArticMine\></strong> yes there is enough redundancy  
<strong>\<sgp\_\></strong> do we have a clear disclosure process? who should people contact?  
<strong>\<sgp\_\></strong> how does the discoverer know how to initiate the process of raising the alarm?  
<strong>\<binaryFate\></strong> I don't think we can assume much from people finding out something is wrong. It's not like programmers finding bugs who are technical and educated about response.  
<strong>\<sgp\_\></strong> surely long-time Monero members would probably contact people by DM and have personal relationships  
<strong>\<cbster\></strong> My first thought would be to turn to Reddit, but not everyone knows the site  
<strong>\<sgp\_\></strong> but the first person to raise the alarm in this case did so through a Github issue  
<strong>\<anhdres2\></strong> I would have used Reddit but I'm not technical  
<strong>\<needmonero90\></strong> I suspect regardless of where it was posted (irc, github, gitlab, reddit), it would have percolate quickly  
<strong>\<needmonero90\></strong> We have lots of lurkers  
<strong>\<needmonero90\></strong> Percolated\*  
<strong>\<cbster\></strong> There could be a section added to the site clarifying what to do in an emergency  
<strong>\<binaryFate\></strong> I think everyone's first thought will be different, and they are not going to dig for information to know how to disclose. Most people would think they are doing something wrong rather than recognize there is an actual issue  
<strong>\<cbster\></strong> Perhaps detailing the subreddit, the GitHub and a few handles of core members  
<strong>\<sgp\_\></strong> something in the github readme may be appropriate imo  
<strong>\<cbster\></strong> Although that could also lead to false alarms, not everyone understands emergencies  
<strong>\<sgp\_\></strong> I'm sure many users will report false alarms  
<strong>\<PlasmaPower\></strong> I think that might send too much "spam" (users who think they have an emergency but don't) their way  
<strong>\<PlasmaPower\></strong> yeah  
<strong>\<ArticMine\></strong> across multiple platforms for redundancy  
<strong>\<almutasim\></strong> False alarms have a price, too.  
<strong>\<M5M400\></strong> binaryFate: agreed.  
<strong>\<binaryFate\></strong> I find it more important to have an "internal" response process so that however this is disclosed, it then quickly gets put on the right rails by community members  
<strong>\<M5M400\></strong> +1  
<strong>\<ArticMine\></strong> +1  
<strong>\<OWLHACKATHON\></strong> hello world  
<strong>\<PewPewPewPew\></strong> is it safe to assume if someone found a problem like this again they would be technical enough to know about git and irc  
<strong>\<sgp\_\></strong> should we just point people who are new to \#monero or something?  
<strong>\<M5M400\></strong> PewPewPewPew: no  
<strong>\<needmonero90\></strong> Don't we already?  
<strong>\<cbster\></strong> I think it's wise to assume  
<strong>\<cbster\></strong> Unwise\*  
<strong>\<needmonero90\></strong> Getting people to use IRC is like pulling teeth  
<strong>\<sgp\_\></strong> needmonero90: just something that clearly says to go to \#monero in the case of an emergency  
<strong>\<needmonero90\></strong> Ah I see  
<strong>\<needmonero90\></strong> That could work  
<strong>\<sgp\_\></strong> eg: what if it's an exchange or mining pool who never talks to anyone  
\* ChanServ set +o needmonero90  
<strong>\<needmonero90\></strong> Oops  
<strong>\<OWLHACKATHON\></strong> go to \#churchofmonero ;)  
\* needmonero90 set -v OWLHACKATHON  
<strong>\<binaryFate\></strong> Harmless but still a lot of people never used IRC whatsoever  
<strong>\<cbster\></strong> It's always an option, we could offer multiple channels of reporting  
<strong>\<cbster\></strong> I think IRC is a good start  
<strong>\<needmonero90\></strong> binaryFate: linking to kiwiirc would work  
<strong>\<sgp\_\></strong> agreed, this is just something I think people should think about since not all the people who will notice major anomalies are always active  
<strong>\<needmonero90\></strong> Webirc portal  
<strong>\<needmonero90\></strong> No downloads, no logins  
<strong>\<\_XeN\_\></strong> love IRC =)  
<strong>\<binaryFate\></strong> It's fine to give them suggestions, but we should not assume they will follow nicely  
<strong>\<sgp\_\></strong> binaryFate: of course not, we just want to make it easier for people to know what they're supposed to do  
<strong>\<sgp\_\></strong> Anything else on a)?  
<strong>\<PlasmaPower\></strong> There's a good amount of posts on r/Monero about people who lost funds because of something that was their fault like a fake web wallet, so I don't think telling people to DM the Monero team for emergencies is a good idea. A public location like IRC is probably the best idea.  
<strong>\<cbster\></strong> Good point  
<strong>\<sgp\_\></strong> b. classification of the severity  
<strong>\<sgp\_\></strong> should we use low - medium - high, and how? who determines?  
<strong>\<fluffyunicorn\></strong> ALL YOUR BASE ARE BELONG TO OWL  
<strong>\<fluffyunicorn\></strong> \>)\>  
<strong>\<fluffyunicorn\></strong> WEEEEEEE  
<strong>\<needmonero90\></strong> Er  
<strong>\<needmonero90\></strong> Can you not? This is a meeting  
<strong>\<fluffyunicorn\></strong> IM HERE TO HACK STUFF  
<strong>\<xmrscott\[m\]\></strong> (Sorry didn't look up in advance, re: A it may be good to look at Tails/Qubes escaltion process)  
\* needmonero90 set channel modes +b fluffyunicorn\!\*@\*  
\* fluffyunicorn was kicked by needmonero90 (fluffyunicorn)  
<strong>\<needmonero90\></strong> I'll remove after the meeting.  
<strong>\<sgp\_\></strong> xmrscott\[m\]: yes, it's important to look at what other people are doing too  
<strong>\<sgp\_\></strong> these classifications are common in projects and in the industry  
<strong>\<cbster\></strong> I think low, high and critical give more emphasis  
<strong>\<sgp\_\></strong> we use it for HackerOne  
<strong>\<sgp\_\></strong> is there anyone who thinks this classification is unnecessary?  
<strong>\<binaryFate\></strong> what is the purpose? Public disclosure later? Internal while we work on issue?  
<strong>\<sgp\_\></strong> binaryFate: depends on how it's used. could be either or both  
<strong>\<sgp\_\></strong> how do you envision it being used?  
<strong>\<anhdres2\></strong> do the classifications change how / which channels are used ? or are they only informative?  
<strong>\<cbster\></strong> I think they'd stay standard across platforms  
<strong>\<binaryFate\></strong> I don't find it very useful for either, simply because these incidents are so rare  
\* needmonero90 set channel modes +b \*\!18cdb83a&#64;gateway/web/cgi-irc/kiwiirc.com/ip.24.205.184.58  
<strong>\<sgp\_\></strong> anhdres2: they could  
<strong>\<anhdres2\></strong> for example only critical are pushed to all channels and low ones only stick in reddit  
<strong>\<cbster\></strong> Mind you, as Monero grows, they may not stay so rare  
\* satoshijnakamoto was kicked by needmonero90 (satoshijnakamoto)  
<strong>\<sgp\_\></strong> indeed, these should happen rarely / never  
<strong>\<xmrscott\[m\]\></strong> If they are used for escalation though the user may not know what the proper flag is, etc  
<strong>\<PlasmaPower\></strong> Does anyone have an example of a low severity emergency? I'm thinking that things that send out a notification, like delta direct, shouldn't be used for those.  
<strong>\<anhdres2\></strong> exactly  
<strong>\<PlasmaPower\></strong> but I'm not quite sure what a low severity emergency would be, assuming that we aren't including 3rd party services  
<strong>\<anhdres2\></strong> yellow warnings are usability or network related  
<strong>\<anhdres2\></strong> red warnings are those when funds might be in danger and therefore are not reversible  
<strong>\<anhdres2\></strong> for example  
<strong>\<sgp\_\></strong> maybe something low would be like after RingCT was first added, where blocks were super full  
<strong>\<sgp\_\></strong> no attack necessarily, but degraded network experience  
<strong>\<anhdres2\></strong> something like that yes  
<strong>\<binaryFate\></strong> wasn't really about an emergency response  
<strong>\<sgp\_\></strong> unless there are other topics on this, we can move on from b)  
<strong>\<ArticMine\></strong> It was a good cover for an emergency response  
<strong>\<sgp\_\></strong> c. communication (internal and public)  
<strong>\<sgp\_\></strong> this is communication standards and processes  
<strong>\<sgp\_\></strong> eg: do we all need to be available on a specific platform (mattermost users can't DM IRC users)  
<strong>\<sgp\_\></strong> also, using services like Twitter, Reddit, Blockfolio  
<strong>\<needmonero90\></strong> I'm generally available. My ringer is generally on even when I'm asleep, so I can resoond when stuff happens  
— needmonero90 should consider getting paid for this availability  
<strong>\<sgp\_\></strong> we took too long this time to get the website notification up and the monero-announce mailing list email out  
<strong>\<M5M400\></strong> yes, the website should be a priority  
<strong>\<asymptotically\></strong> \!tip needmonero90 0.001  
<strong>\<tippero\></strong> asymptotically has tipped needmonero90 1 millinero (0.001 Monero)  
<strong>\<binaryFate\></strong> internal communication between community members to deal with issue was very efficient I found  
<strong>\<sgp\_\></strong> are there other platforms we forgot about this time? ones we felt were mostly a hassle and not very beneficial?  
<strong>\<xmrscott\[m\]\></strong> Where was the roadblock though in getting the site annoucement up  
<strong>\<M5M400\></strong> it's traditionally generally slacking, but in this case updates need to be of high priority  
<strong>\<needmonero90\></strong> Your generosity will not be forgotten  
<strong>\<xmrscott\[m\]\></strong> Was it in getting approval after erc drafted it?  
<strong>\<xmrscott\[m\]\></strong> etc  
<strong>\<binaryFate\></strong> we'd need a website specific timeline of events  
<strong>\<xmrscott\[m\]\></strong> Exactly  
<strong>\<sgp\_\></strong> can we build in notification systems with Cake Wallet, Monerujo, etc?  
<strong>\<xmrscott\[m\]\></strong> (Which may be best done after the meeting)  
<strong>\<needmonero90\></strong> I think we just blanked on updating the site  
<strong>\<needmonero90\></strong> It was an oversight  
<strong>\<needmonero90\></strong> Once we were clued in it was updated fairly quickly  
<strong>\<sgp\_\></strong> indeed, which is why the process is important. it gives us a checklist to help us remember  
<strong>\<asymptotically\></strong> sgp\_: bitcoin-qt used to have a built in notification system, but it kind of sucked and got removed  
<strong>\<M5M400\></strong> sgp\_: like a emergency broadcast system that pushes out to multiple outlets with minimal effort?  
<strong>\<anhdres2\></strong> sgp\_ I don't see how unless it adds a centralized element.  
<strong>\<cbster\></strong> I think built-in notification systems would be smart, but their use would be limited as those affected are probably not using them (they downloaded the core wallet)  
<strong>\<xmrscott\[m\]\></strong> Built in notifications introduce a point of attack  
<strong>\<M5M400\></strong> yeah. super amplified FUD  
<strong>\<cbster\></strong> If the binaries are comprised for that, I'd be unsure of its reliability to relay notifications  
<strong>\<PlasmaPower\></strong> Bitcoin's now retired system: <https://en.bitcoin.it/wiki/Alert\_system>  
<strong>\<sgp\_\></strong> PlasmaPower: thanks for the reference  
<strong>\<xmrscott\[m\]\></strong> Hey, wallet is compromised, download at this new (malicious) website  
<strong>\<PlasmaPower\></strong> cbster: yeah, though for e.g. an active linking attack it could be helpful  
<strong>\<cbster\></strong> I think you're right, could prove more troublesome than what it solves  
<strong>\<sgp\_\></strong> ok, no additional platforms coming up. keep thinking about better ways to reach people  
<strong>\<sgp\_\></strong> \*coming to mind  
<strong>\<sgp\_\></strong> d. incident response  
<strong>\<M5M400\></strong> I'd like to throw the mailinglist in the ring. who's got access to post there besides the big fluff?  
<strong>\<sgp\_\></strong> M5M400: good q\> I don't know  
<strong>\<binaryFate\></strong> everyone can post, but emails are approved on a case basis (pigeon and maybe fluffy too)  
<strong>\<M5M400\></strong> maybe take a note for later. I think it is a good medium, but worthless when notifications get sent out a day or two late  
<strong>\<binaryFate\></strong> in this case there was a misunderstanding between fluffy and myself. He thought I would send email, I thought he would  
<strong>\<binaryFate\></strong> (I did not have access to my PGP key in time)  
<strong>\<M5M400\></strong> fair enough  
<strong>\<sgp\_\></strong> an example of the communication process helping in that case could be specifically assigning tasks to people  
<strong>\<PlasmaPower\></strong> is there any generally applicable "incident response" besides communication?  
<strong>\<sgp\_\></strong> PlasmaPower: nice segway, thanks  
<strong>\<sgp\_\></strong> an example of an incident response process, though extreme, could be something like getting the opinion and help of an independent firm  
<strong>\<M5M400\></strong> sgp\_: that's not extreme. it's common practice to have security incidents assessed by independent parties to minimize the risk of compromized entities being part of the investigation  
<strong>\<sgp\_\></strong> right, so how do we do that without writing a $10m check to Deloitte?  
<strong>\<M5M400\></strong> hence my question earlier if the people disecting the box also had access at the time of breach  
<strong>\<asymptotically\></strong> write me a $9m check instead  
<strong>\<needmonero90\></strong> I'll do it for $8m  
<strong>\<M5M400\></strong> sgp\_: that's the $8m question  
<strong>\<PlasmaPower\></strong> I definitely agree that's a good step when a server is compromised. Would it also be applicable to e.g. an RCE in the protocol? I'm not sure how useful an investigation would be there, besides a `git blame`.  
<strong>\<needmonero90\></strong> And by do it I mean delegate  
<strong>\<binaryFate\></strong> I don't see that as possible or useful in an emergency situation. Maybe for investigations later. No firm will be hired (with what funds?), get to the case and help us in a couple hours  
<strong>\<PlasmaPower\></strong> true  
<strong>\<sgp\_\></strong> binaryFate: right, which is why I'm looking for realistic procedures  
<strong>\<binaryFate\></strong> Since we are not a company and we do not have people around the clock 24/7, I think we should realistically focus on procedures indeed. Not even assigned them strictly so we do not have bottleneck if someone is afk  
<strong>\<M5M400\></strong> sgp\_: community internal segregation of duties would be a start  
<strong>\<sgp\_\></strong> M5M400: can you elaborate a bit more?  
<strong>\<M5M400\></strong> seperate publishing teams and forensic teams  
<strong>\<binaryFate\></strong> Maping the current capabilities (mostly website update) would be good too. What processes are required for each steps and who has the permissions currently to do them?  
<strong>\<sgp\_\></strong> binaryFate: good one  
<strong>\<sgp\_\></strong> basic access control stuff  
<strong>\<PlasmaPower\></strong> though probably keep that documentation internal  
<strong>\<M5M400\></strong> not sure how it's organized right now, so can't elaborate in detail. but from previous conversations it seems that it's not even totally clear who even had access to the comped box. (probably multiple people)  
<strong>\<PlasmaPower\></strong> you don't want to provide attackers with a guide of who to attack  
<strong>\<M5M400\></strong> PlasmaPower: internal is a pretty fuzzy thing... where do you draw the line in the circle of trust an opensource project?  
<strong>\<M5M400\></strong> anyone in here could be a potential attacker  
<strong>\<sgp\_\></strong> M5M400: I agree in this case it's pretty industry-standard to have some discussions like this kept in the dl  
<strong>\<PlasmaPower\></strong> M5M400: it's going to be somewhat arbitrary of course, and IDK how the Monero team is currently organized, but whoever has access to the GitHub is a good place to start.  
<strong>\<sgp\_\></strong> any other incident response comments? we will need to revisit this much more later  
<strong>\<sgp\_\></strong> e. regular tests/audits  
<strong>\<sgp\_\></strong> ideally, we will assess the existing processes and suggest improvements. then we can test them to see how effective these processes are  
<strong>\<sgp\_\></strong> that's why schools have fire drills  
<strong>\<binaryFate\></strong> I want to highlight that people that trust each other getting on an IRC channel to discuss the situation at hand remains by far the most efficient decision process. I find it more important to remove potential bottlenecks in terms of who can do what, than to try to guide too much said decision process.  
<strong>\<binaryFate\></strong> Have to go now, thanks everyone, thanks sgp\_ for meeting  
<strong>\<sgp\_\></strong> binaryFate: thanks for coming  
<strong>\<M5M400\></strong> +1 on the removing bottlenecks thing  
<strong>\<M5M400\></strong> cu  
<strong>\<sgp\_\></strong> ideally this would be its own workgroup, but I also don't know how realistic this is  
<strong>\<sgp\_\></strong> ok, people are pretty quiet on this one. we can keep going  
<strong>\<sgp\_\></strong> f. responsible roles, including alternates  
<strong>\<sgp\_\></strong> it's an open-source project without people getting paid for things, so people will be asleep, on vacation, etc  
<strong>\<M5M400\></strong> regarding fire drills... we could regularly publish emergency broadcast test posts on the outlets and have people go to a website, click on a button or something to assess message reception depth  
<strong>\<sgp\_\></strong> it's important imo to have a list of primary and secondary contacts  
<strong>\<M5M400\></strong> sorry, I'm slow. it's late.  
<strong>\<needmonero90\></strong> One solution is to create a hired role for this.  
— needmonero90 puts his name into the hat  
<strong>\<sgp\_\></strong> needmonero90: I'll give you $1  
<strong>\<needmonero90\></strong> 🤔  
<strong>\<needmonero90\></strong> I can do a writeup of role requirements later  
<strong>\<sgp\_\></strong> that would be very beneficial  
<strong>\<sgp\_\></strong> eg: Justin is the primary for Blockfolio, secondary for Twitter, etc  
<strong>\<sgp\_\></strong> any other ideas? we're getting close to finishing this long meeting  
<strong>\<M5M400\></strong> would those roles be published somewhere?  
<strong>\<sgp\_\></strong> M5M400: I recommend they're only given to trusted people  
<strong>\<sgp\_\></strong> give people only what they need to see  
<strong>\<sgp\_\></strong> g. missed topics and frameworks  
<strong>\<sgp\_\></strong> If you have any topics you feel were not covered or some other better framework to consider going forward, please mention these now for discussion.  
<strong>\<M5M400\></strong> \<void\>  
<strong>\<ArticMine\></strong> I would raise the question of post incident hardening  
<strong>\<M5M400\></strong> good one  
<strong>\<asymptotically\></strong> is there a post mortem of how the bad wallet binary actually ended up on the site? or is that not known yet  
<strong>\<M5M400\></strong> but probably needs the forensics to complete first  
<strong>\<asymptotically\></strong> ok nvm that answered my question :p  
<strong>\<M5M400\></strong> though it begs the question what makes the DR host more secure than the comped box at this point in time  
<strong>\<needmonero90\></strong> Nothing left on my end  
<strong>\<ArticMine\></strong> Yes that is the case, but for example hardening the the binary verification process  
<strong>\<ArticMine\></strong> Such as rehrar suggested but going further  
<strong>\<ArticMine\></strong> binary verification for android  
<strong>\<ArticMine\></strong> Free BSD etc  
<strong>\<M5M400\></strong> still awake - but I can't contribute to this  
<strong>\<sgp\_\></strong> ArticMine: I don't have anything to add here, but I'll note the process  
<strong>\<sgp\_\></strong> Any final thoughts?  
<strong>\<sgp\_\></strong> 4. Action items  
<strong>\<sgp\_\></strong> I will compile the recommendations in 3 into a document and share the initial draft version  
<strong>\<sgp\_\></strong> Once shared, please comment on the draft  
<strong>\<sgp\_\></strong> Please think about specific roles you would feel comfortable filling, even in a backup role  
<strong>\<sgp\_\></strong> rehrar named an action item 1000 years ago when the meeting started but I forget what it was  
<strong>\<sgp\_\></strong> then there's the action item of identifying who has access to what parts of the server (or making sure the core team has that info already)  
<strong>\<sgp\_\></strong> Anything else?  
<strong>\<ArticMine\></strong> It was about improving the guides for binary verification  
<strong>\<ArticMine\></strong> Making them easier to understand for users  
<strong>\<rehrar\></strong> Goodness\! This is still going?  
<strong>\<sgp\_\></strong> ok, add that :)  
<strong>\<sgp\_\></strong> very nearly done rehrar, we were very productive  
<strong>\<xmrscott\[m\]\></strong> Write up website notification timeline to figure out what the major contributors were ro thevdelay  
<strong>\<asymptotically\></strong> maybe openbsd signify would be easier than a pgp signed shasums file?  
<strong>\<sgp\_\></strong> xmrscott\[m\]: good, have a timeline so we can see what took the longest  
<strong>\<sgp\_\></strong> last chance to say something  
<strong>\<sgp\_\></strong> 5. Conclusion  
<strong>\<sgp\_\></strong> Thank you for participating in this extremely important discussion for Monero  
<strong>\<almutasim\></strong> Thank you.  
<strong>\<M5M400\></strong> thx  
<strong>\<sgp\_\></strong> I was extremely pleased at the dedication for this emergency response, and with some organization, I think we can set a gold standard for other projects to follow  
<strong>\<sgp\_\></strong> See you all later :)  
<strong>\<needmonero90\></strong> Great :)  
\* needmonero90 set channel modes -b \*\!18cdb83a&#64;gateway/web/cgi-irc/kiwiirc.com/ip.24.205.184.58  
\* needmonero90 set channel modes -b \*\!18cdb83a&#64;gateway/web/cgi-irc/kiwiirc.com/ip.24.205.184.58  
\* needmonero90 set channel modes -b fluffyunicorn\!\*@\*
