---
title: Logs for the Monero Research Lab Meeting Held on 2018-07-16
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> Welcome to everyone; greetings  
<strong>\<suraeNoether\></strong> hi  
<strong>\<sarang\></strong> Let us go with brief updates  
<strong>\<sarang\></strong> The initial draft report from Kudelski has arrived, with generally positive results  
<strong>\<sarang\></strong> A few small things to address  
<strong>\<sarang\></strong> I am working on some prototyping code for a sublinear RingCT proposal that's progressing very nicely  
<strong>\<sarang\></strong> I delivered a talk on fungibility in Portland (in the airport right now about to depart)  
<strong>\<sarang\></strong> Other reports?  
<strong>\<suraeNoether\></strong> I wrote a thing... it was sort of a whim  
<strong>\<suraeNoether\></strong> endogenic and I started talking about comparing addresses when sending a transaction  
<strong>\<suraeNoether\></strong> humans tend to only check the first five or sex and last five or six characters in an address  
<strong>\<suraeNoether\></strong> there are graphical representations of random data so people can visually compare them  
<strong>\<suraeNoether\></strong> one way to do this is using seashells, since they are easily parameterizable  
<strong>\<sarang\></strong> (e.g. randomart)  
<strong>\<suraeNoether\></strong> <https://github.com/b-g-goodell/research-lab/tree/master/source-code/iseeseashells>  
<strong>\<sarang\></strong> nice  
<strong>\<suraeNoether\></strong> so i wrote a thing that takes an address, hashes it, breaks the hash into 4-byte pieces  
<strong>\<suraeNoether\></strong> uses each of those pieces to define a parameter of a seashell  
<strong>\<suraeNoether\></strong> and then plot it  
<strong>\<suraeNoether\></strong> so if we could get something going client-side with each transaction, with a javascript renderer, it would work like this  
<strong>\<suraeNoether\></strong> i want to send xmr to a bitcoin address using xmr.to  
<strong>\<suraeNoether\></strong> i fire up my xmr wallet and copy-paste my xmr.to address into it, and a seashell appears. i compare it to the seashell on the xmr.to website. they look the same, and the characters seem to mostly match, so i send the transaction  
<strong>\<suraeNoether\></strong> (same thing for firing up my bitcoin wallet to verify i'm sending to myself appropriately)  
<strong>\<sarang\></strong> So you effectively treat the shell as a fingerprint  
<strong>\<suraeNoether\></strong> yeah, pretty much  
<strong>\<suraeNoether\></strong> there are collision issues  
<strong>\<sarang\></strong> its use being similar to key fingerprints in other places  
<strong>\<suraeNoether\></strong> but i think if we do it appropriately, it's less likely than for other approaches  
<strong>\<sarang\></strong> Right, so it's not a primary check  
<strong>\<knaccc\></strong> very cool, can you paste an example seashell ascii art please?  
<strong>\<suraeNoether\></strong> in addition to that, i wrote a thing on churn that is 3+ pages long. it's statistics-heavy, still internal, will be shared later this week. it'll help inform us on our ring size choices, etc, for the next fork  
<strong>\<suraeNoether\></strong> not ascii :D  
<strong>\<suraeNoether\></strong> but one sec  
<strong>\<knaccc\></strong> oh it's not ascii art? so won't work in the CLI?  
<strong>\<suraeNoether\></strong> correct, it is a 3d rendering  
<strong>\<knaccc\></strong> oh cool  
<strong>\<moneromooo\></strong> You can have cli shells there.  
<strong>\<suraeNoether\></strong> so it'd have to be a javascript client side rendering sort of deal  
<strong>\<knaccc\></strong> hehe  
<strong>\<suraeNoether\></strong> let me find where i saved some of the cool ones last night  
<strong>\<sarang\></strong> will it work in bash, or just in csh =p  
<strong>\<endogenic\></strong> you could render it easily enough  
<strong>\<moneromooo\></strong> :)  
<strong>\<endogenic\></strong> and could also scan a render  
<strong>\<endogenic\></strong> rotated of course  
<strong>\<sarang\></strong> FYI will have to leave meeting early in 20 min to catch plane  
<strong>\<knaccc\></strong> 3d renderings sound much more useful than the kind of ssh-keygen fingerprint ascii art  
<strong>\<suraeNoether\></strong> <https://usercontent.irccloud-cdn.com/file/vM0sXAXB/Figure\_1.png>  
<strong>\<suraeNoether\></strong> <https://usercontent.irccloud-cdn.com/file/RKtCkotV/Figure\_1-1.png>  
<strong>\<suraeNoether\></strong> so, 1) i'm using matplotlib in python, so it's ugly  
<strong>\<knaccc\></strong> oooh that's lovely\! much better than this:  
<strong>\<knaccc\></strong> +---\[RSA 2048\]----+  
<strong>\<knaccc\></strong> \| .++ \|  
<strong>\<knaccc\></strong> \| .+.. .\|  
<strong>\<suraeNoether\></strong> ikr  
<strong>\<knaccc\></strong> \| . . . . ..\|  
<strong>\<knaccc\></strong> \| . . .E.. \|  
<strong>\<moneromooo\></strong> ...  
<strong>\<knaccc\></strong> \| ...S . \|  
<strong>\<knaccc\></strong> \| o+. \|  
<strong>\<knaccc\></strong> \| +..o \|  
<strong>\<knaccc\></strong> \| o B .o. \|  
<strong>\<knaccc\></strong> \| . + +.. \|  
<strong>\<knaccc\></strong> +------\[MD5\]------+  
<strong>\<sarang\></strong> omg stahp  
<strong>\<sarang\></strong> the ascii, it hurts  
<strong>\<knaccc\></strong> haha  
<strong>\<suraeNoether\></strong> so, all the formulaes and everything need to be tweaked to make them prettier and more shell-like... and a good javascript person could use the marching cubes algorithm to render these really easily. someone could mess with textures and colors using the hashes, too  
<strong>\<moneromooo\></strong> Or we could generate rogue rooms...  
<strong>\<suraeNoether\></strong> but i'm essentially \*not\* going to put more effort into it: my goal was to construct parameterizations of these surfaces, the math heavy end of things, so someone else can take it and run with it  
<strong>\<sarang\></strong> To jump in quickly due to time... any questions lingering about the audit results? The initial stuff has been picked up by a few sites, generally reported badly  
<strong>\<sarang\></strong> We'll respond to the findings and they'll issue a final report, and then get the rest of their payment from OSTIF  
<strong>\<sarang\></strong> The initial draft doesn't mention OSTIF, which is an oversight on Kudelski's part  
<strong>\<suraeNoether\></strong> sarang I was going to ask about how money was transferred to OSTIF without tax exposure to the monero project or whatever  
<strong>\<suraeNoether\></strong> i was thinking about \*how to pay for the monero conference\*  
<strong>\<suraeNoether\></strong> like, will we need to start an LLC for each conference? maybe  
<strong>\<endogenic\></strong> didn't seem like anyone found the keyspace validation issue.. is that correct  
<strong>\<endogenic\></strong> ?  
<strong>\<suraeNoether\></strong> endogenic: you mean the multiply-by-8 stuff?  
<strong>\<endogenic\></strong> mm  
<strong>\<sarang\></strong> endogenic: kudelski did not mention the subgroup checks  
<strong>\<endogenic\></strong> oh wiat one did  
<strong>\<sarang\></strong> quarkslab did note it in an email to me  
<strong>\<endogenic\></strong> i think  
<strong>\<endogenic\></strong> k \*zips it\*  
<strong>\<sarang\></strong> suraeNoether: what about taxes?  
<strong>\<endogenic\></strong> scoobybejesus ^  
<strong>\<suraeNoether\></strong> sarang: well, some entity has to pay another entity  
<strong>\<suraeNoether\></strong> example: to pay for a venue  
<strong>\<sarang\></strong> I mean for the audits  
<strong>\<sarang\></strong> The payment for the audit was from OSTIF, a nonprofit, to Kudelski, a private company  
<strong>\<suraeNoether\></strong> ah, so we paid OSTIF in monero, and OSTIF is dealing with it  
<strong>\<nioc\></strong> when is QuarksLab expected to be finished?  
<strong>\<suraeNoether\></strong> and since they are non-profit, tax reports must be made but they aren't exposed to the taxes. i get it. but now i'm thinking about how to funnel money from the monero project towards something like a venue expenditure  
<strong>\<sarang\></strong> Correct; OSTIF does the transfer to Kudelski's preferred fiat  
<strong>\<suraeNoether\></strong> which is a different question  
<strong>\<sarang\></strong> the phrase "funnel money" sounds like a Very Bad Thing  
<strong>\<sarang\></strong> nioc: I had expected it this past week  
<strong>\<charuto\></strong> Probably a bad idea to make the audits public one at a time  
<strong>\<sarang\></strong> charuto: I've been posting public audit information as I receive it, in the interest of open disclosure  
<strong>\<suraeNoether\></strong> i can see the argument that it foils some of the independence of the teams  
<strong>\<sarang\></strong> and IMHO we should fix issues openly as we find them  
<strong>\<moneromooo\></strong> Well, if they'd found something bad, we'd have wanted to wait till a release anyway.  
<strong>\<moneromooo\></strong> (without piping up)  
<strong>\<sarang\></strong> true, good point  
<strong>\<sarang\></strong> Their issues were only minor  
<strong>\<charuto\></strong> the last team to release their results could have done nothing and waited to see the other team's results to copy them  
<strong>\<sarang\></strong> I suppose  
<strong>\<suraeNoether\></strong> charuto while that's technically possible, it's more likely that hte second report will merely be \*bigger\* than the first, including everything the first does, plus more.  
<strong>\<charuto\></strong> Imagine like a student assignment where students make their work public before the assignment is due  
<strong>\<suraeNoether\></strong> yeah, except these firms make their living off repeat business and word of mouth  
<strong>\<sarang\></strong> Except that I trust these groups to operate in good faith  
<strong>\<suraeNoether\></strong> it's not a great incentive to screw over one small software project for a relatively small amount of money, when all of them are on twitter all the time trolling zooko  
<strong>\<suraeNoether\></strong> yeah, the incentive structure for them to not do their jobs isn't really there the way it is in high school or college  
<strong>\<silur\></strong> hey guys sorry for being late :(  
<strong>\<sarang\></strong> hullo  
<strong>\<sarang\></strong> Anyway, other questions on the audits?  
<strong>\<sarang\></strong> We shall make changes as necessary and continue the plan toward a release  
<strong>\<suraeNoether\></strong> i have one last quick question on that  
<strong>\<sarang\></strong> go  
<strong>\<suraeNoether\></strong> i know we signed contracts wtih K and QL  
<strong>\<suraeNoether\></strong> or did we just accept their SOW?  
<strong>\<sarang\></strong> We signed the statements of work regarding scope and payment  
<strong>\<sarang\></strong> y?  
<strong>\<suraeNoether\></strong> either way, i'm curious about what we have for Buenz. in terms of "what happens if he just gets busy and phones it in? do we still owe him 10k if he does that?"  
<strong>\<sarang\></strong> We have an SoW for Benedikt  
<strong>\<sarang\></strong> There is no defined metric for what counts as "phoning it in"  
<strong>\<suraeNoether\></strong> k i'll read through it again  
<strong>\<sarang\></strong> It is assumed that he will operate in good faith, just as we assume this for the other reviewers  
<strong>\<suraeNoether\></strong> yep  
<strong>\<sarang\></strong> part of the reason he and the others were chosen was for this reason  
<strong>\<suraeNoether\></strong> yep, just curiuos.  
<strong>\<nioc\></strong> When is QuarksLab expected to be finished?  
<strong>\<moneromooo\></strong> He gave bulletproofs research for free already. No reason why he'd try and screw us here.  
<strong>\<sarang\></strong> I emailed a few days ago to QL asking for a status update; no word yet  
<strong>\<nioc\></strong> thx  
<strong>\<sarang\></strong> I am not pleased with their lack of communication this week  
<strong>\<moneromooo\></strong> Well, not "no reason", that is too strong.  
<strong>\<suraeNoether\></strong> moneromooo: i'm not assuming malice, but densely packed schedules, the priorities and prerogatives of grad students, etc  
<strong>\<sarang\></strong> suraeNoether: he waited for summer term  
<strong>\<sarang\></strong> partly because of scheduling  
<strong>\<suraeNoether\></strong> yeah i know\\  
<strong>\<suraeNoether\></strong> i'm not making any accusations, i was just curious. gosh guys  
<strong>\<sarang\></strong> lol  
<strong>\<suraeNoether\></strong> i'm going to re-iterate my request that future audits have a "suggested unit testing" section to their reports, though. if we're going to be forking over lots of cash for someone to audit our code, and they are going to spend time saying "gee, this HERE would have been an easy test to write" then... may as well  
<strong>\<suraeNoether\></strong> anyway, that's all i have: seashells, churn paper (and small delay on multisig for churn analysis last week, but I've been communicating with Yannick of musig regarding our multisig paper, so that's still moving too)  
<strong>\<suraeNoether\></strong> oh, if anyone is curious on the churn paper, and they are tolerant of \*incorrect statistics\* (NEVER BE TOLERANT OF THIS) then you can read my crapdraft here: <https://v2.overleaf.com/read/rznczkmdmchy>  
<strong>\<endogenic\></strong> lol  
<strong>\<endogenic\></strong> all statistics are incorrect  
<strong>\<endogenic\></strong> got 'em  
<strong>\<sarang\></strong> OK, I need to board my plane now  
<strong>\<sarang\></strong> I'll be back online in the air  
<strong>\<sarang\></strong> because we're living in the freaking future  
<strong>\<endogenic\></strong> man can't believe they make people actually catch the planes these days  
<strong>\<sarang\></strong> they don't taxi that fast  
<strong>\<endogenic\></strong> maybe if you're riding a pony  
<strong>\<silur\></strong> last time border police didn't let me on my flight..... again  
<strong>\<silur\></strong> \#beingstateless  
<strong>\<suraeNoether\></strong> Okay, does anyone have any other things they want to discuss?  
<strong>\<silur\></strong> yep, any news from the new-new-new-updated rtrs?  
<strong>\<suraeNoether\></strong> silur yes, sarang is getting permission to post it on his github  
<strong>\<silur\></strong> shall we merge the implementation too there?  
<strong>\<suraeNoether\></strong> he has finished around half the algorihtms required, and has been messing around wtih an ed25519 library in python  
<strong>\<silur\></strong> oh it's AN implementation  
<strong>\<silur\></strong> thought only text  
<strong>\<suraeNoether\></strong> no, no, friend  
<strong>\<suraeNoether\></strong> sarang has been ON THIS  
<strong>\<suraeNoether\></strong> okay, any other questions before we call it?  
<strong>\<sarang\></strong> Yeah code is making good progress, waiting on permission to include on my repo  
<strong>\<silur\></strong> I kinda don't want to progress with mine if the reference is outdated but glad to hear the py version is goin good  
<strong>\<sarang\></strong> I don't have an opinion on it yet  
<strong>\<sarang\></strong> The code is basically to help me better understand the setup and efficiency  
<strong>\<endogenic\></strong> i'm curious to bring up the question of bindings to C/C++  
<strong>\<sarang\></strong> It's also not even remotely optimized  
<strong>\<endogenic\></strong> but i know it's work  
<strong>\<endogenic\></strong> the mem mgmt could be made v simple  
<strong>\<endogenic\></strong> guess it can be a future goal  
<strong>\<silur\></strong> @endogenic my implementation is pure C with openssl dependency  
<strong>\<suraeNoether\></strong> endogenic: yeah, all we are doing right now is trying to prototype it to get a \*sense\* of asymptotic properties of verification time, etc beyond the statistics described in the paper  
<strong>\<endogenic\></strong> i mean for various util libs so the usage of a specific language for r&amp;d isn't indicated by the existence of those shared libs  
<strong>\<endogenic\></strong> r&amp;d as in prototyping, sims, etc  
<strong>\<suraeNoether\></strong> alllrighty, well, it appears as if we have run out of stuff to talk about. Any final questions?  
<strong>\<suraeNoether\></strong> I love you all  
<strong>\<endogenic\></strong> no i mean that's unsolved  
<strong>\<suraeNoether\></strong> ?  
<strong>\<endogenic\></strong> sarang chose a specific language to work in because there were libs in that language already  
<strong>\<endogenic\></strong> even if it wasn't the preferred language  
<strong>\<endogenic\></strong> just saying there are alternatives and asking how recently they've been investigated  
<strong>\<suraeNoether\></strong> oh, gosh  
<strong>\<suraeNoether\></strong> i don't know\!  
<strong>\<suraeNoether\></strong> last time i checked... which was last year when knaccc and i were working on ruffct  
<strong>\<suraeNoether\></strong> i believe there weren't better options available at the time  
<strong>\<suraeNoether\></strong> but since it's just prototyping, i'm not sure it matters too much  
<strong>\<endogenic\></strong> yeah, just a matter of language preference for him..  
<strong>\<suraeNoether\></strong> okay, \</meeting\>
