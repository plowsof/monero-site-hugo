---
title: Overview and Logs for the tini2p Dev Meeting Held on 2019-03-28
summary: Project infrastructure, Current status, Roadmap, I2P proposal implementation, and miscellaneous
tags: [dev diaries, i2p, crypto]
author: el00ruobuob / oneiric
---

# Logs

<strong>\<oneiric\_\></strong> 0. greets  
<strong>\<oneiric\_\></strong> hi  
<strong>\<Corklander\></strong> Hey\!  
<strong>\<endogenic\></strong> o/  
<strong>\<oneiric\_\></strong> 1. Project infrastructure / DevOps  
<strong>\<kinghat\></strong> hi all  
<strong>\<oneiric\_\></strong> recently setup CircleCI, Docker and Bitbucket CI pipelines  
<strong>\<oneiric\_\></strong> going to try out Drone CI (integrates w/ GitLab), and decide on a final CI provider  
<strong>\<oneiric\_\></strong> will keep alternative configs in contrib/  
<strong>\<oneiric\_\></strong> got a basic Docker image setup with everything needed to build tini2p  
<strong>\<oneiric\_\></strong> need to fix net tests to be able to run in a container for accurate coverage stats  
<strong>\<oneiric\_\></strong> other than that, CI is more-or-less setup  
<strong>\<oneiric\_\></strong> will be experimenting/playing with gitea over the next weeks, and mirror GitLab to GitHub, BitBucket, and gitea  
<strong>\<oneiric\_\></strong> unfortunately lost access to tini2p account on GitHub, though still have push ability  
<strong>\<oneiric\_\></strong> main github repo is now: <https://github.com/tnii2p-project/tini2p>  
<strong>\<Corklander\></strong> 404 :(  
<strong>\<oneiric\_\></strong> derp  
<strong>\<oneiric\_\></strong> type  
<strong>\<oneiric\_\></strong> typo  
<strong>\<oneiric\_\></strong> my fingers are terrible today  
<strong>\<oneiric\_\></strong> <https://github.com/tini2p-project/tini2p>  
<strong>\<Corklander\></strong> Yea\!  
<strong>\<oneiric\_\></strong> -\_-  
<strong>\<oneiric\_\></strong> lol  
<strong>\<oneiric\_\></strong> anyway  
<strong>\<oneiric\_\></strong> any questions/comments? i think that's all for infrastructure stuff.  
<strong>\<Corklander\></strong> Do you see any dependency problems with Drone CI or the other choices? (I haven't used them so I'm not sure about any restrictions/costs.)  
<strong>\<oneiric\_\></strong> most of them i've seen are basically the same  
<strong>\<oneiric\_\></strong> x free hours for builds, then monery  
<strong>\<oneiric\_\></strong> the integrations are the differentiators  
<strong>\<oneiric\_\></strong> circle works with github and bitbucket, drone works with gitlab  
<strong>\<Corklander\></strong> sry, have to go due to emrf, bbl  
<strong>\<oneiric\_\></strong> think there are webhook integrations on most/all major gitserver providers  
<strong>\<oneiric\_\></strong> anyway  
<strong>\<oneiric\_\></strong> ttyl  
<strong>\<oneiric\_\></strong> anything else on 1?  
<strong>\<oneiric\_\></strong> 2. Current project status / what's been done  
<strong>\<oneiric\_\></strong> spent a lot of time replacing crypto++ with libsodium + tiny-AES-c  
<strong>\<oneiric\_\></strong> then realized, "oh, i need an SSL lib"  
<strong>\<oneiric\_\></strong> so, added LibreSSL as a dependency for potential future Keccak patch, and replaced tiny-AES-c with SSL impl  
<strong>\<oneiric\_\></strong> that's in an open MR: <https://gitlab.com/tini2p/tini2p/merge\_requests/2>  
<strong>\<oneiric\_\></strong> finished with code cleanup, generic crypto/signature wrappers, and a basic experimental ECIES-X25519-AEAD-Ratchet impl  
<strong>\<oneiric\_\></strong> merged MR: <https://gitlab.com/tini2p/tini2p/merge\_requests/1>  
<strong>\<oneiric\_\></strong> currently working on generic wrappers for the proposed Blake2b EdDSA variants  
<strong>\<oneiric\_\></strong> which i will discuss in 4  
<strong>\<oneiric\_\></strong> questions/comments on 2?  
<strong>\<endogenic\></strong> awesome progress  
<strong>\<oneiric\_\></strong> will also hopefully be able to help zzz with ECIES testing (fingers-crossed)  
<strong>\<oneiric\_\></strong> thanks endogenic :)  
<strong>\<oneiric\_\></strong> 3. Short-term road map  
<strong>\<oneiric\_\></strong> implement the Blake2b sig variants to help other I2P projects with testing  
<strong>\<oneiric\_\></strong> implement tunnels + basic netdb  
<strong>\<oneiric\_\></strong> if lmdb interface is simple enough, will skip past doing blockfile format, and just use lmdb for addressbook/netdb needs  
<strong>\<oneiric\_\></strong> that's where i want to be anyway :)  
<strong>\<oneiric\_\></strong> adding alpha and beta milestones to the gitlab project  
<strong>\<oneiric\_\></strong> projected alpha release for 2019/07/10  
<strong>\<oneiric\_\></strong> with a beta following 3 months after  
<strong>\<oneiric\_\></strong> will see how this first cycle goes, but will try to keep to that release schedule, or shorten it if feasible  
<strong>\<endogenic\></strong> good plan  
<strong>\<endogenic\></strong> the minimum usable set is generally critical to keep in mind to avoid getting lost along the way  
<strong>\<endogenic\></strong> dont think that's a huge issue here given the name "tiny" though :)  
<strong>\<endogenic\></strong> good origins  
<strong>\<oneiric\_\></strong> yeah, if shorter, may do alpha (2 months) -\> beta (2 months) -\> point release  
<strong>\<oneiric\_\></strong> true, as part of 4. i'll talk about the current sig variant proposals, and which of those will end up in tini2p  
<strong>\<oneiric\_\></strong> which is actually a nice transition (smooth endogenic)  
<strong>\<oneiric\_\></strong> 4. I2P proposal implementation  
<strong>\<oneiric\_\></strong> <https://geti2p.net/spec/proposals/123-new-netdb-entries>  
<strong>\<oneiric\_\></strong> <https://geti2p.net/spec/proposals/144-ecies-x25519-aead-ratchet>  
<strong>\<oneiric\_\></strong> <https://geti2p.net/spec/proposals/146-red25519>  
<strong>\<oneiric\_\></strong> <https://geti2p.net/spec/proposals/148-eddsa-blake2b-ed25519>  
<strong>\<oneiric\_\></strong> we went over 123 and 144 last meeting, iirc  
<strong>\<oneiric\_\></strong> one thing that has changed, zzz has said he will be switching focus back to ECIES, and hammering out some spec details  
<strong>\<oneiric\_\></strong> so we are getting closer to a finalized spec, which will reduce code footprint  
<strong>\<oneiric\_\></strong> 146 and 148 are the new sig variant proposals  
<strong>\<oneiric\_\></strong> for eddsa  
<strong>\<oneiric\_\></strong> RedDSA is needed for blinding encrypted lease sets, and Blake2b variants are needed to protect against LEA attacks  
<strong>\<oneiric\_\></strong> Ed25519ctx was also suggested, and is being considered for LEA protection  
<strong>\<oneiric\_\></strong> personally, think Ed25519ctx is gross given the alternatives, but it's in an RFC  
<strong>\<oneiric\_\></strong> RFC 8032 to be specific  
<strong>\<oneiric\_\></strong> the hash function in RFC 8032 isn't specified, other than being a crypto-secure hashing function with 512-bits security  
<strong>\<oneiric\_\></strong> Blake2b satifies all criteria  
<strong>\<oneiric\_\></strong> for full details see the proposals and \#ls2 meeting logs  
<strong>\<oneiric\_\></strong> so, my plan is to write generic wrappers for all variants, then keep whichever get accepted  
<strong>\<oneiric\_\></strong> right now, it's looking like RedDSA-Blake2b-EdDSA can be used for all places where a signature is needed  
<strong>\<oneiric\_\></strong> a lot is still up in the air though, and nothing has been finalized yet  
<strong>\<oneiric\_\></strong> any comments/questions on 4?  
<strong>\<oneiric\_\></strong> one more thing actually, EdDSA-Blake2b-Ed25519 could also be used everywhere a signature is used  
<strong>\<oneiric\_\></strong> afaiui EdDSA-Blake2b-Ed25519 can also do blinding needed for encrypted lease sets  
<strong>\<oneiric\_\></strong> 5. Confirm next meeting time  
<strong>\<oneiric\_\></strong> same time two weeks?  
<strong>\<kinghat\></strong> yup  
<strong>\<oneiric\_\></strong> right on, meeting over. thanks to all for attending
