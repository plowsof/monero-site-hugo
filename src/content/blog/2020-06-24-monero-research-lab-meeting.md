---
title: Logs for the MRL Meeting Held on 2020-06-24
tags: [dev diaries, crypto, research]
author: asymptotically / Sarang
---

# Logs

<strong>\<sarang\></strong> First, GREETINGS  
<strong>\<ArticMine\></strong> Hi  
<strong>\<I3^RELATIVISM\></strong> 0/  
<strong>\<Isthmus\></strong> Greetings  
<strong>\<sarang\></strong> All right, on to ROUNDTABLE, where anyone is welcome to share research of interest  
<strong>\<sarang\></strong> Who would like to go first?  
<strong>\<sarang\></strong> Isthmus:?  
<strong>\<Isthmus\></strong> Heyo  
<strong>\<Isthmus\></strong> Update on quantum audit, here is our preliminary analysis existing vulnerabilities. (Results subject to change as research progresses\!)  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/RKKVcmGZ/image.png>  
<strong>\<Isthmus\></strong> <https://usercontent.irccloud-cdn.com/file/ZPskux3i/image.png>  
<strong>\<Isthmus\></strong> It's kind of a mixed bag, tbh.  
<strong>\<sarang\></strong> To be expected, I suppose  
<strong>\<sarang\></strong> There are many components of interest  
<strong>\<Isthmus\></strong> Our reliance on DLP is the biggest weak spot right, as expected  
<strong>\<sarang\></strong> ya  
<strong>\<Isthmus\></strong> That's all on that, any Q's?  
<strong>\<sarang\></strong> By "ring signatures" I assume you mean a quantum adversary identifying signing indices via key images?  
<strong>\<Isthmus\></strong> Yea (or via any mechanism)  
<strong>\<Isthmus\></strong> Oh, one thing that we started wondering about  
<strong>\<Isthmus\></strong> If you're creating a multisig transactions and one of the signers has a quantum computer, can they gain any extra information about their co-signers  
<strong>\<sarang\></strong> Well, you can just derive the whole private key  
<strong>\<sarang\></strong> if that's what you mean  
<strong>\<Isthmus\></strong> Yea. I need to sit down with ZtM2 to figure out what's passed around, and what should be unknown, just crossed my mind yesterdy  
<strong>\<sarang\></strong> That's a good point  
<strong>\<sarang\></strong> I don't think anyone had specifically mentioned the multisig process during the planning stages of your analysis  
<strong>\<Isthmus\></strong> Yea, we just added it. Will probably realize 1 or 2 more aspects to check throughout the next few weeks  
<strong>\<Isthmus\></strong> Keep dropping us your ideas :- )  
<strong>\<sarang\></strong> Are there particular assumptions made about whether or not the adversary has a public key already?  
<strong>\<sarang\></strong> e.g. the adversary suspects a particular address as a destination  
<strong>\<Isthmus\></strong> I'm assuming that the adversary is a co-signer on the multisig transaction. They would know the public key with or without a quantum computer, right?  
<strong>\<Isthmus\></strong> \[erm, well we can consider the adversary both ways, this is just what I had been wondering about yesterday\]  
<strong>\<sarang\></strong> I mean in general, sorry  
<strong>\<sarang\></strong> Not specific to multisig  
<strong>\<Isthmus\></strong> Ah yea, quantum computer with your public key and quantum computer without your public key are two adversary models that are considered separately.  
<strong>\<Isthmus\></strong> Though TBH the first one is pretty (sadly) easy  
<strong>\<Isthmus\></strong> Public key --\> \[shor's algorithm\] --\> private key --\> init wallet --\> game over  
<strong>\<sgp\_\></strong> sorry I'm late  
<strong>\<sarang\></strong> And not even "your" public key  
<strong>\<sarang\></strong> But just looking at a given transcation on chain  
<strong>\<sarang\></strong> If the adversary's goal is to identify as much as possible about keys, addresses, etc.  
<strong>\<sarang\></strong> Sending wallet address, receiving wallet address, etc.  
<strong>\<Isthmus\></strong> Yea, if an outside observer plucks a transaction at random from the blockchain, with no further knowledge, what can they ascertain about 1) the sender, 2) the transaction, 3) the recipient  
<strong>\<sarang\></strong> Right. And then what can they learn if they have an idea of possible addresses  
<strong>\<Isthmus\></strong> Bingo  
<strong>\<sarang\></strong> I assume that there is (or will be) a more specific write-up with details on what relates to this chart?  
<strong>\<UkoeHB\_\></strong> Earlier I argued you could brute force output amounts if the DLP is broken (assuming recipient address is unknown), however I'll retract that. Output amounts are information-theoretically secure.  
<strong>\<Isthmus\></strong> Gotcha  
17:23:44 \* Isthmus makes a note  
<strong>\<Isthmus\></strong> Yeah, this will all be in the research writeup, and more intuitive parts will be included in the general audience writeup  
<strong>\<sarang\></strong> Anything else to consider about your analysis at this point Isthmus?  
<strong>\<Isthmus\></strong> We were thinking about some medium articles throughout, just for good measure  
<strong>\<Isthmus\></strong> Nope, that's all on the quantum end for now  
<strong>\<sarang\></strong> OK great\!  
<strong>\<Isthmus\></strong> I started going down a rabbit hole of subliminal channels this morning, but will save those thoughts for later  
<strong>\<sarang\></strong> Did anyone else wish to present research of interest?  
<strong>\<UkoeHB\_\></strong> This means even if both DLP and hash preimage are broken, there should not be a way to extract the recipient's address from an output.  
<strong>\<Isthmus\></strong> That's a huge relief, or else we could recursively apply Shor's algorithm and move forward through the transaction tree breaking everybody's wallets  
<strong>\<sarang\></strong> I'll share a few things  
<strong>\<sarang\></strong> Here's a time-windowed CDF of spend age: <https://usercontent.irccloud-cdn.com/file/5EccXpmE/cdf\_window.png>  
<strong>\<sarang\></strong> Still tracks the gamma distribution pretty well, but there are differences over time (pre-CT)  
<strong>\<sarang\></strong> Related to this, I posted my tracing code: <https://github.com/SarangNoether/skunkworks/tree/tracing>  
<strong>\<sarang\></strong> It now supports iterative updates, which may be useful  
<strong>\<sarang\></strong> Unrelated to this, I'm still working with the CLSAG auditors  
<strong>\<sarang\></strong> I rewrote the proof for Theorem 1 that relates unforgeability to non-slanderability, and it now addresses the auditors' suggestions  
<strong>\<sarang\></strong> There are a bunch of other non-security-related updates to it  
<strong>\<sarang\></strong> and I'm now in the process of overhauling the linkability anonymity proof to use a better hardness assumption and method, which is a tedious process  
<strong>\<sarang\></strong> but I think that will address their comments and be a stronger result  
<strong>\<sarang\></strong> The auditors' conclusion is that the construction seems secure, and that the security model seems appropriate to the use case  
<strong>\<sarang\></strong> This was the overall goal of the audit; suggestions relating to presentation, formality, etc. are very useful for later submission, but don't appear security-related  
<strong>\<UkoeHB\_\></strong> Sounds like the audit is moving along well  
<strong>\<sarang\></strong> It is\! The code review portion has not begun yet, but there are no changes in code to be made as a result of the preprint audit at this point  
<strong>\<sarang\></strong> Any questions on these research topics?  
<strong>\<sarang\></strong> OK, did anyone else have anything to share before we move on?  
<strong>\<sgp\_\></strong> nope  
<strong>\<sarang\></strong> If not, we can move on to ACTION ITEMS for the coming week  
<strong>\<sarang\></strong> I will be finishing up this linkable anonymity overhaul and incorporating it into the preprint, which will complete the updates needed for the auditors  
<strong>\<sarang\></strong> Once that's done, I'll get the preprint in a submittable state  
<strong>\<sarang\></strong> Anyone else?  
<strong>\<sgp\_\></strong> I'll be opening a GitHub issue for segregating coinbase outputs into coinbase-only rings  
<strong>\<sarang\></strong> It's a good time to discuss this, with an upcoming network upgrade for CLSAG at some point  
<strong>\<sgp\_\></strong> yeah I think so too  
<strong>\<sarang\></strong> especially given the spend-age data  
<strong>\<sarang\></strong> I'd still love to see the corresponding data for bitcoin  
<strong>\<sarang\></strong> but I don't have that dataset  
<strong>\<sarang\></strong> all the Monero data is necessarily pre-CT because of deducibility  
<strong>\<sarang\></strong> and any post-CT deducible data spends old funds and is therefore basically useless for those kinds of distributions  
<strong>\<sgp\_\></strong> I've been pretty clear that I think this BTC data would be nice but isn't necessary to make this change  
<strong>\<sarang\></strong> understood  
<strong>\<sarang\></strong> OK, anything else before we adjourn?  
<strong>\<UkoeHB\_\></strong> Isthmus I have to walk back my walkback (sorry for the interruption sarang). You can definitely brute force it if the DLP and hash preimage are broken. Information-theoretic security means nothing in the face of brute forcing all possibilities (64 bits worth). You'd 1) get the DLP of generator H and the commitment C, 2) pick an amount, 3) compute the possible derivation to scalar, 4) get its hash preimage,  
<strong>\<UkoeHB\_\></strong> 4a) use the key sequence of bits from the preimage to test the encoded amount and only continue if it matches the guessed amount (very unlikely to match if the guessed amount isn't correct) 5) use the key sequence of bits from the preimage to compute the one time address derivation to scalar, 6) subtract it from the one time address private key to get the nominal private spend key, 7) get the DLP of the  
<strong>\<UkoeHB\_\></strong> preimage key with respect to the tx pub key to get the nominal private view key, 8) test if the spend key can produce the view key directly (normal address) or if any reasonable sub address index can be used to extract a spend key that produces the view key, 9) repeat 2-8 until you get a match (step 4a will probably catch most mistaken guesses). Let's blame this mishap on a stray synapse.  
<strong>\<sarang\></strong> hmm  
<strong>\<Isthmus\></strong> ohhhhhh  
<strong>\<sarang\></strong> IIRC preimage on keccak is something like O(2^100) or so  
<strong>\<sarang\></strong> but I'd have to check on that  
<strong>\<Isthmus\></strong> Unrelated: Does ZtM2 talk about variable types or just math? Trying to figure out if fees are uint64 or what  
<strong>\<UkoeHB\_\></strong> They are varints, which I mention in section 6.3 footnote iirc  
<strong>\<Isthmus\></strong> Ah, perfect. Thanks\!  
<strong>\<sarang\></strong> Righto, let's go ahead and adjourn since it's now 18:00 UTC  
<strong>\<sarang\></strong> Thanks to everyone for participating\!
