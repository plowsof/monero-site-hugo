---
title: Logs for the Monero Research Lab Meeting Held on 2019-05-06
summary: Sarang work, Surae work, and miscellaneous
tags: [dev diaries, crypto, research]
author: el00ruobuob / sarang
---

# Logs

<strong>\<sarang\></strong> OK, let's begin  
<strong>\<sarang\></strong> ping suraeNoether et al.  
<strong>\<sarang\></strong> First on the agenda, GREETINGS  
<strong>\<sarang\></strong> hello  
<strong>\<sgp\_\></strong> hello  
<strong>\<sarang\></strong> I'll wait a couple of minutes to see if others join  
<strong>\<suraeNoether\></strong> hey guys  
<strong>\<suraeNoether\></strong> thank you for your patience  
<strong>\<sarang\></strong> Since suraeNoether went first last time, I'll go first in the ROUNDTABLE  
<strong>\<sarang\></strong> the DLSAG signature paper has been submitted to a conference in a short form, and the IACR preprint is forthcoming  
<strong>\<sarang\></strong> Thanks to our coauthors for their excellent work on this  
<strong>\<sarang\></strong> The submission process is arduous and irritating  
<strong>\<sarang\></strong> Zcoin published an intriguing Zerocoin protocol flaw recently: <https://zcoin.io/cryptographic-description-of-zerocoin-attack/>  
<strong>\<sarang\></strong> Sooooo we won't be switching to Zerocoin anytime soon\!  
<strong>\<sarang\></strong> My monthly report is available on CCS: <https://repo.getmonero.org/monero-project/ccs-proposals/merge\_requests/34#note\_5903>  
<strong>\<suraeNoether\></strong> is there an issue with DLSAG key images that will impact the publication process?  
<strong>\<sarang\></strong> I updated the CLSAG protocol code to reflect key prefixing, which had been left out mistakenly  
<strong>\<sarang\></strong> Doubtful  
<strong>\<sarang\></strong> It's an interesting construction regardless  
<strong>\<sarang\></strong> moneromooo asked about doing a CLSAG key image offset (like we do in BPs) to save time while avoiding subgroup issues  
<strong>\<sarang\></strong> Doing so would save \~315 us per signature on my test machine  
<strong>\<sarang\></strong> But it was also noted that there could easily be room for error depending on implementation  
<strong>\<sarang\></strong> Note that the CLSAG test code already performs this offset on the auxiliary key image, but this isn't used for linking anyway  
<strong>\<sarang\></strong> I had also been interested in BP generalizations to arbitrary input lengths  
<strong>\<sarang\></strong> I have code for it: <https://github.com/SarangNoether/skunkworks/tree/pybullet-np2>  
<strong>\<sarang\></strong> Unfortunately this requires the verifier to compute all inner product rounds and loses computational efficiency  
<strong>\<sarang\></strong> It may be possible to modify the algorithm to do the single-round version, but it is not clear to me how to do so cleanly  
<strong>\<sarang\></strong> Currently, I'm working on updating some formal definitions for suraeNoether for CLSAG, and have been doing some code and timing tests for a paper that was presented to me  
<strong>\<sarang\></strong> Any particular questions on this work?  
<strong>\<suraeNoether\></strong> just curious when you sleep :D  
<strong>\<sarang\></strong> lol  
<strong>\<sarang\></strong> Go ahead, suraeNoether \!  
<strong>\<suraeNoether\></strong> my update is shorter: unforgeability proof for CLSAG is nearly complete, but I'm holding off on continuing to write on this before I get some comments back from sarang. some of my protocols as described have a few mismatches with our current approaches, and I don't want to write proofs for the wrong protocols.  
<strong>\<suraeNoether\></strong> i'm working on my talk for the magical crypto conference (i'm leaving tomorrow for that and I'll be back home on sunday)  
<strong>\<sarang\></strong> Well, they'd be correct for our implementation AFAICT, but not for a neat generalization you were working on  
<strong>\<suraeNoether\></strong> oh\! well, still  
<strong>\<suraeNoether\></strong> since the proofs will be for the general case  
<strong>\<sarang\></strong> Right  
<strong>\<suraeNoether\></strong> anyway, i'm also trying to solve a problem with the dlsag key images that I thought had been solved, and I'm continuing to review a semi-secret paper for a colleague  
<strong>\<suraeNoether\></strong> (the last semi-secret paper ended up being DLSAG, which is the groundwork for monero lightning, so y'all know if we're keeping it semi-secret it's pretty neato burrito)  
<strong>\<dEBRUYNE\></strong> Is that semi-secrit paper related to Monero?  
<strong>\<suraeNoether\></strong> my action items for today involve a breaking monero episode, further DLSAG research, further semi-secret research, and writing my MCC talk  
<strong>\<suraeNoether\></strong> dEBRUYNE: yes  
<strong>\<dEBRUYNE\></strong> Cool  
<strong>\<suraeNoether\></strong> but i can't go further yet  
<strong>\<sgp\_\></strong> when is the earliest you expect to switch back to the bipartite graph paper?  
<strong>\<suraeNoether\></strong> in being public about the contents, I mean  
<strong>\<suraeNoether\></strong> sgp\_: thank you for reminding me about that, this is an ongoing project, sgp\_, and I've been putting in work regularly on that paper to try to get my simulations working appropriately.  
<strong>\<suraeNoether\></strong> actually putting work regularly into the simulations, because the paper is on hold until the sims are done  
<strong>\<suraeNoether\></strong> sarang and I are trading some projects back and forth; when i hand him clsag or dlsag, i work on MRL11 until he hands me something back, and it's like the tides  
<strong>\<suraeNoether\></strong> :P  
<strong>\<suraeNoether\></strong> i don't have a good timeline on completing it and getting results, however  
<strong>\<sgp\_\></strong> All I'm doing is making sure is that it doesn't fall by the wayside. There are a million things to do, I just want to make sure this remains in the top 3  
<strong>\<suraeNoether\></strong> ^ absolutely  
<strong>\<suraeNoether\></strong> i'll make a little descriptive blurb and make a link to it here later today so that people can see the current state of the thing  
<strong>\<sarang\></strong> perfect  
<strong>\<sarang\></strong> Any other questions for suraeNoether ?  
<strong>\<suraeNoether\></strong> i want to ensure that folks in the community are aware of the progress on each of these projects, and we definitely have a \*lot\* of projects/spinning plates  
<strong>\<sarang\></strong> If anyone else has relevant research to present, now is a great time  
<strong>\<sgp\_\></strong> none from me. looking forward to seeing the MCC recording/slides  
<strong>\<sarang\></strong> As am I  
<strong>\<sarang\></strong> Ok, how about ACTION ITEMS  
<strong>\<sarang\></strong> I'll be rewriting some definitions today to streamline suraeNoether's CLSAG generalization for the proofs  
<strong>\<sarang\></strong> Finishing up that timing data I mentioned earlier  
<strong>\<sarang\></strong> getting another couple of Breaking Monero out the door  
<strong>\<sarang\></strong> Reviewing some output selection stuff  
<strong>\<sarang\></strong> etc.  
<strong>\<sarang\></strong> Others?  
<strong>\<suraeNoether\></strong> I mentioned mine already  
<strong>\<sarang\></strong> that you did  
<strong>\<suraeNoether\></strong> and sgp\_ reminded me to re-add matching to my list  
<strong>\<suraeNoether\></strong> does anyone have any questions about konferenco or complaints or more action items to be added to the list of stuff to do for the research conference?  
<strong>\<suraeNoether\></strong> i'm asking this because sgp\_ just reminded me how human and fallible my memory is for big lists of stuff to do :D  
<strong>\<sarang\></strong> The speaking agenda for the conference is all set?  
<strong>\<suraeNoether\></strong> yep, i believe i'm waiting on two TBA titles. i need to add two sponsors to our list, Tari and Symas  
<strong>\<sarang\></strong> I'm excited to speak and serve as panel moderator  
<strong>\<suraeNoether\></strong> those sponsors are on the t-shirt design, but not the website  
<strong>\<suraeNoether\></strong> oh man that's going to be a good panel  
<strong>\<suraeNoether\></strong> i'm anticipating pretty rough questions for Voorhees and Gavigan actually  
<strong>\<sarang\></strong> FYI questions for the panel will be submitted by the audience and then selected by moderators  
<strong>\<sarang\></strong> to ensure quality and avoid the inevitable "a few follow-up questions..."  
<strong>\<sarang\></strong> Since we have time, here's an open question... now that the next point release is being finalized, any thoughts from the room about desired changes for the next network upgrade?  
<strong>\<suraeNoether\></strong> ^ i'm curious about this a lot  
<strong>\<suraeNoether\></strong> the other day sarang asked me what i want to see in the next upgrade  
<strong>\<sgp\_\></strong> another ringsize revisit. 2 output min. payment ID stuff  
<strong>\<suraeNoether\></strong> the next big change i want to see is CLSAG, since it'll be basically cutting our blockchain rate of growth by half  
<strong>\<sarang\></strong> 25%  
<strong>\<suraeNoether\></strong> but 2-out min and deprecating pay\_id is on my list also  
<strong>\<sarang\></strong> ish  
<strong>\<suraeNoether\></strong> oh yeah there are some constants  
<strong>\<sgp\_\></strong> any chance for dandelion++? I don't know how long this would take  
<strong>\<sarang\></strong> Probably not by fall, but it's not consensus  
<strong>\<sarang\></strong> any client release could do it  
<strong>\<sgp\_\></strong> right, jut curious  
<strong>\<sgp\_\></strong> are you anticipating any work on your end for RandomX? code is frozen and needs to be reviewed  
<strong>\<suraeNoether\></strong> i heard a rumor that tari is looking into ristretto and monero's protocol  
<strong>\<suraeNoether\></strong> i'm thinking we should invite someone from tari to give us an update on that for the meeting after next or something like that  
<strong>\<sarang\></strong> sgp\_: I'm working with hyc to solicit statements of work from reviewers  
<strong>\<sarang\></strong> We have 4 interested firms  
<strong>\<sgp\_\></strong> great\!  
<strong>\<sarang\></strong> Once we get publicly-releasable statements we can put them on GitHub  
<strong>\<sgp\_\></strong> do you expect those within the month?  
<strong>\<sarang\></strong> yes  
<strong>\<suraeNoether\></strong> i'm very excited about that  
<strong>\<suraeNoether\></strong> are the firms all auditing firms? should we consider trying to bring in a hardware firm to assess that end of the implementation?  
<strong>\<suraeNoether\></strong> like, code-auditing i mean  
<strong>\<sarang\></strong> We're getting reviewers with backgrounds in hardware design  
<strong>\<sarang\></strong> It's tough because at some level "can this be built into hardware efficiently" is answered by designing such hardware  
<strong>\<sarang\></strong> Part of the process will be getting feedback on which reviewers' experience aligns most closely with our goals  
<strong>\<suraeNoether\></strong> fair nuff  
<strong>\<sgp\_\></strong> I don't have any other consensus-related questions and comments  
<strong>\<sarang\></strong> Anyone else have any?  
<strong>\<sarang\></strong> Righto\!  
<strong>\<sarang\></strong> In that case, thanks to everyone for participating today. Logs will be posted shortly to the GitHub agenda issue  
<strong>\<sgp\_\></strong> I have a really quick announcement  
<strong>\<sarang\></strong> sure  
<strong>\<sgp\_\></strong> If you are interested in speaking, running a workshop, and/or volunteering at the Monero Village at Defcon in August, please fill out the CFP by June 3: <http://monerovillage.org>  
<strong>\<sgp\_\></strong> We already have some good submissions  
<strong>\<sgp\_\></strong> (done)  
<strong>\<sarang\></strong> When https?  
<strong>\<sgp\_\></strong> whenever rehrar gets the time  
<strong>\<sarang\></strong> :D  
<strong>\<sarang\></strong> OK, we are now adjourned
