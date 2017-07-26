# Untangling iOS PIN code security

_Captured: 2016-03-21 at 09:50 from [marcan.st](https://marcan.st/2016/03/untangling-ios-pin-code-security/)_

A lot has been written about the Apple vs. FBI saga. However, the truth about exactly what it all means from a technical standpoint is scattered among many sources, amidst quite a bit of misinformation. This post is my attempt to provide, in a question and answer format, what I consider to be the current knowledge of the state of affairs, from the perspective of a security researcher.

Very little of this is my own research. Rather, consider this a collection of information based on publicly available sources, filtered by my knowledge as a security engineer of how secure systems work. It represents the true state of iOS PIN code security to the best of my knowledge, and what is and isn't possible. I do not guarantee that everything stated here is 100% accurate, but rather, it is my understanding of the status quo.

I've tried to make this post accessible to less technically minded people. Although the reader is expected to, for example, know what "encryption" and "firmware" mean, I've tried to explain more complicated concepts. I hope this at least makes it accessible to interested users, and also journalists who are looking to make sense of the available info. Feel free to contact me if you need clarification or feel something doesn't make sense.

## How does iOS PIN security work?

Here is a simple explanation of how the iPhone protects its user's data:

  1. **Firmware**: The iPhone will only run firmware that is signed by Apple. This allows them to guarantee that it will follow their security policies and design.

  2. **Full disk encryption**: The iPhone's "hard drive" data is encrypted with an encryption key that is different for every individual iPhone, and can be destroyed at any time. This prevents attackers from taking off the iPhone's memory chip and reading it externally. This key is long enough that "trying all possible keys" is impossible.

  3. **User data encryption**: Within the encrypted storage, user data (such as SMSes and e-mail) are again encrypted using a key that is derived from the user's PIN. This means that you need to know the PIN to access the data. Deriving the key also requires a secret key available inside the iPhone's CPU.

  4. **PIN policy**: To prevent attackers from simply trying every PIN, the firmware enforces a policy that requires a certain delay between PIN retry attempts, and optionally destroys the full disk encryption key after 10 incorrect guesses (thereby making all data permanently inaccessible).

It is the combination of these four points that allows an iPhone user's data to be secure against attackers (such as the FBI). The points rely on each other: If one or more of the points can be bypassed, the security is broken and the data can be accessed.

(Strictly speaking, there are some nuanced interactions between the points, particularly points 2 and 3, but for our purposes let's say that if anything breaks, the whole chain breaks.)

These 4 points are described in Apple's [iOS Security Guide](https://www.apple.com/business/docs/iOS_Security_Guide.pdf) pages [5](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=5) (#1), [11](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=11) (#2 and #3), and [12](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=12) (#4).

## What does the FBI want?

The FBI is asking Apple to use their ability to create and sign any new version of iOS (the first point above) to create a new, custom firmware version that allows them to try all possible PIN codes (undermining the fourth point above), therefore allowing them to guess the PIN and access user data (third point above). Then they can simply use that PIN to access the data on the phone itself (making the second point moot).

The FBI isn't asking Apple to do something fundamentally new such as "create" a backdoor in iOS. Instead, they are asking them to use an ability that they already have - the ability to create new firmware and sign it so that it will be accepted by an iPhone. iPhone security currently relies on Apple promising not to release firmware that would break their security model, and the FBI is simply asking Apple to break that promise. The "backdoor" is already there: that Apple can write new versions of iOS and sign them.

## How does firmware signing work?

iPhone firmware signing (much like firmware signing for most modern devices) is based around a concept called [public-key encryption](https://en.wikipedia.org/wiki/Public-key_cryptography). In public-key encryption, two keys are generated at the same time: a public key and a private key. The keys are mathematically related to each other, but it is impossible to calculate the private key if you only know the public key.

To sign a piece of firwmare, its [hash](https://en.wikipedia.org/wiki/Cryptographic_hash_function) is first calculated. The hash is just a number (say, 256 bits in length) that represents a unique "fingerprint" of the firmware--in practice, no two firmwares will ever have the same hash, and the firmware cannot be engineered to have a specific hash. Then this hash is signed using the private key, producing a signature. The signature can be checked by using the public key.

The phone only has the public key, so it can check the signature, while the private key is kept in a secure facility at Apple and only used to sign vetted versions of iOS. To verify the firmware, the phone calculates the hash of the firmware, and then verifies that the signature indeed matches that hash, using its copy of the public key.

The public key is burned into the CPU chip in the iPhone and cannot be replaced. The hash is too long to just "try until you get the right hash", and the private key is too long to just "try until you get the right key". With modern key sizes and assuming no major flaws have been found in the cryptography, or the firmware implementation, it is impossible to forge a signature for a particular firmware version without having access to the private key.

## How much effort would it take for Apple to comply?

This is hard to guess, because it's fundamentally a policy issue, and we don't know what Apple's internal policies are like.

From a technical perspective, creating a new firmware does not take a lot of effort. This doesn't mean creating a new version of iOS entirely from scratch. Indeed, the easiest way to provide what the FBI wants would be to use existing debug tools that Apple no doubt already has to grant external access from the phone's recovery mode, and then create a small tool that allows the FBI to brute force the iPhone's PIN from that mode, perhaps making a few small changes along the way to disable the limitation on the number of PIN retries. I estimate that, as far as the bare minimum development time needed goes, this could be accomplished by a single engineer in a day or two.

However, the bulk of the issue is not the time required to actually develop the firmware, but rather, the internal policies that Apple no doubt enforces on internal operations, such as signing a new version of iPhone firmware. Some of these policies might be enforced by hardware--that is, Apple may not even be physically capable of expediting them. This is the case if, as is most likely, the master signing private key for iOS firmware versions is kept in a Hardware Security Module, which enforces certain restrictions on how it may be used. Depending on how that works out, and how safe Apple wants to keep its users in spite of the FBI's request, the process could be complicated by one or more orders of magnitude, both in time and money.

## Does this undermine security for all iPhones?

It doesn't. Much has been written and claimed about how creating this "backdoored" firmware image would undermine the security of the entire iPhone ecosystem. However, that is not true. Just because Apple writes a piece of code does not mean that it can be used on all iPhones. The security does not depend on what code is written, but rather, on what is signed. As it turns out, Apple already has a mechanism that requires that every version of iOS is signed specifically to run on each and every individual iPhone.

This is known to jailbreakers as the "SHSH" mechanism, and Apple calls it [System Software Authorization](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=6)[page 6]. During an iPhone firmware restore, iTunes contacts Apple's servers to obtain a certificate that validates the specific version of iOS being installed, for the specific iPhone where it is being installed. This is why you can't downgrade iOS to an older version: Apple's servers no longer give out certificates for older iOS versions. This very same mechanism could be used to only allow the special FBI firmware image to be used on the specific iPhone that is being targeted. All iPhones have a unique device ID (based on a key burned into the CPU). The certificates also use public-key encryption technology, and are basically signatures that authorize a specific firmware version for a specific iPhone device ID. The iPhone checks on every boot to make sure it has a certificate valid for its specific device ID.

Since creating these certificates requires Apple's private key, nobody else can create them. The simple fact is that, assuming Apple does not massively undermine their internal processes in order to grant this request, the special firmware developed for the FBI would be secured to only work on the target iPhone using their existing technology.

Instead, the major danger is not in creating a backdoor that could be used on other phones, or making it easier for an attacker to break into Apple more easily. The main issue is a matter of precedent: if Apple does this for a single phone for the FBI, other agencies, in the US and other countries, are going to want to be able to do the same.

Granting the FBI's request doesn't undermine security in the iOS ecosystem. What it does is undermine trust in the iOS ecosystem--trust that Apple will not willingly do this.

## Has Apple done this in the past?

Yes, they have. With older iOS versions, data was not encrypted using the user's PIN. It was still encrypted using the full disk encryption mechanism. For those phones, Apple cooperated with law enforcement to [perform data extraction](http://www.apple.com/privacy/docs/legal-process-guidelines-us.pdf#page=9)[page 9] on iPhones. They did this in much the same way: by uploading a special firmware image that allowed extraction of all data and files from the phone without requiring that the PIN code be entered. The firmware image still undermined iOS's normal policy of requiring the PIN code to be entered to access data.

Therefore, newer iOS versions aren't actually more secure against this kind of attack than older ones: in both cases, law enforcement practically required Apple's cooperation. Indeed, the only thing that has truly changed is that Apple introduced a new security feature--encryption using the user's PIN--and has now chosen to not undermine that particular security feature for the benefit of law enforcement, from now onward. The fact that doing so requires brute-forcing a user's PIN is mostly irrelevant, from a security perspective: the time required to brute-force a 4-digit PIN is basically ignorable. Instead, Apple has simply changed their policy, using this new feature as a convenient "cut-off" for what they are willing to help with and what they aren't. Apple could refuse to perform data extraction on older versions of iOS from now onward, just like they could comply with the FBI's request for the current iOS version, and future such requests, from now onward, as long as the PIN code length used is bruteforceable. It all boils down to a change in policy, not a change in technology.

Of course, each side can choose their own angle to view the situation. Apple can claim that the data is secured using the PIN code (which is true), and thus they cannot unlock it without knowledge of the PIN code (which is true), which they could on older iOS versions. However, since a short PIN code is not secure, its security relies on iOS security policy, and thus the FBI can (rightly) counter with the claim that all Apple has to do is allow them to bypass that policy (which doesn't require knowing the PIN), so that they can simply try all possible PIN codes, and bypassing iOS security policies for law enforcement is something Apple has done in the past. It's a PR match between Apple and the FBI more than it is a real technical argument.

## What can the FBI do to avoid relying on Apple's help?

There are at least 3 plausible attacks that the FBI could use to gain access to the phone:

### Firmware exploit ("jailbreak")

This is the method used by jailbreakers to jailbreak a phone. If the FBI can find a flaw in the iPhone's secure boot process--that is, a bug in the firmware that allows them to execute their own arbitrary code--then they could use it to remove the restrictions on PIN retries, just like jailbreaks allow users to modify iOS in ways unauthorized by Apple.

This is more complicated in this case than for regular jailbreaks, as jailbreaks usually have the luxury of being able to rely on the user doing something on an unlocked phone (such as visiting a website), while the FBI only has access to a locked phone--the attack surface is smaller. However, they could still find a bug in an application that can be launched from the lock screen, or in the iPhone's Boot ROM, or part of the firmware that is uploaded by the iPhone firmware restore process using iTunes, or in the USB protocols used by the iPhone to communicate with a PC, or with other USB devices (such as USB storage devices).

With this process, the FBI could guess as many PINs as the device can physically process. According to my understanding of Apple's security model, each PIN attempt is designed to require [80 milliseconds](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=12)[page 12] of hardware processing time. That's 13 minutes for a 4-digit PIN, or just under a day for a 6-digit PIN.

### Silicon attack

Ultimately, the only thing that prevents the FBI from simply removing the phone's "hard drive"--its [NAND flash](https://en.wikipedia.org/wiki/Flash_memory) memory chip--and reading its contents, trying as many passcodes as they want, is the fact that the iPhone's CPU holds a secret key that is required to decrypt any data from the NAND chip in the first place. This key is actually derived from a master secret that is actually stored on the CPU chip in permanent memory, which is called the "[UID key](https://www.theiphonewiki.com/wiki/UID_key)". If you can physically get to the location, buried in the chip, where this key is stored, you could read it out.

We [actually have technology](http://www.wsj.com/articles/chip-hacking-might-help-fbi-unlock-iphones-1457050959)[paywalled - [infographic](http://si.wsj.net/public/resources/images/BT-AH348_PLANB_9U_20160303184523.jpg)] that can do this. It is called a Focused Ion Beam (FIB) workstation, and it can basically perform microscopic surgery on the wiring of silicon chips and enable attacks like this.

However, this is a pretty long shot. You only get one chance to do this on the target chip, it's very expensive, time-consuming, and may be borderline impractical depending on how modern a manufacturing process Apple used for their CPU. But it's fundamentally possible.

With this attack, since the master secret is extracted, the PIN cracking could be performed on a computer, or a computer cluster. This allows easily cracking PINs as long as 10 digits without much issue, only limited by how much CPU or GPU power you can buy. Alphanumeric passphrases are also vulnerable unless they are long and secure. Even individuals can rent large amounts of compute power from Amazon EC2 by the minute for a very reasonable amount of money.

### Replay attack

There is one glaring flaw in the iOS pin code protection mechanism. The entire idea relies on the phone being able to count how many times the PIN has been entered incorrectly, locking the phone (by destroying vital encryption keys) after 10 failed tries. But how does the phone keep track of this number?

The answer is simple: it stores it in the phone's NAND flash chip, just like all the other data on the phone. While the count can presumably not be directly modified (it would be cryptographically protected from tampering), the NAND flash chip is just a memory device. That means that, even though you can't change the "number of tries left" to a number of your liking, you can take a complete snapshot of the contents of the NAND flash chip, and then restore it as many times as you want. In a way, the iPhone's "mind" is rolled back in time to a point where you still had 10 PIN tries left, and the CPU is none the wiser, because it has no way to detect that. This is called a [replay attack](https://en.wikipedia.org/wiki/Replay_attack) (replay attacks are often described for network protocols, but they also work for memory storage systems).

To do this, the FBI would have to remove the NAND flash chip, and connect it to a reader/writer. Then they could take a snapshot of its contents, and then write that snapshot back to reset it to its original state of "10 tries left".

Removing the NAND Flash memory chip is easy. All it takes is a hot-air gun and some finesse. Replacing it is slightly harder, but not at all a challenge to anyone experienced with board repair for modern electronics. Any shop doing, say, MacBook logic board repair jobs (not just replacement) can do this.

Actually removing and replacing the chip many times would be time-consuming and impractical, but there are much more intelligent ways of performing this attack. The chip can simply be replaced with a socket, allowing you to insert/remove it with ease. Or, even better, the chip can be replaced with a simulator that can effortlessly switch between any version of its contents at any time. This allows the entire process to be automated and run without human intervention.

The FBI could then try guessing 4 or 5 PINs and then reboot the phone while resetting the NAND memory to its original contents, which might take, say, 90 seconds. At 4 PINs every minute and a half, it would take 2.6 days to try all possible 4-digit combinations. Each extra digit multiplies that by a factor of 10, so a 5-digit PIN would take 26 days (which is still reasonable), while a 6-digit PIN would take 260 days--less practical, but still short enough to be useful.

This would look a lot like the Chinese "iP-BOX" PIN cracking attack that worked on older versions of iOS, except with the addition of a NAND simulator hooked up to the phone.

> _

#### Automated iPhone PIN cracking

_

This is the most practical way to do it, and it can be accomplished by an experienced team with a very modest amount of resources (a few thousand dollars or less) in initial development cost, and then could be reused on any iPhones of the same or similar model almost for free.

For an example of a similar replay attack used in practice, check out how Brazilian game shops used the same process to [pirate PS4 games](http://wololo.net/2015/05/13/new-piracy-technique-on-ps4-in-brazil-confirmed-to-be-real-sony-might-take-legal-action/): they authorized an account with games on the PS4, copied the storage (hard disk and Flash memory chip), deauthorized the account, then restored the copy, leaving the PS4 to think that it was still legitimately authorized to play those games. Replay attacks are relatively low-tech and often work on rather secure systems, and do not require any specific knowledge of the details of the security system that you're attacking: as long as there is no replay protection, which is often overlooked or dismissed in the design, they will work.

### Other attacks

There are other possible attacks, such as discovering a flaw in the fundamental cryptography technology used by Apple (such as the AES encryption cipher, or a preimage attack on the SHA family of hash algorithms), but this is extremely unlikely (and, if such a flaw were discovered at this time, we'd have bigger problems to worry about than anyone's iPhone). Other options may include side-channel attacks (monitoring things like electromagnetic interference emitted from the iPhone's CPU to try to gain information about encryption keys), or using electrical glitching to try to "confuse" the iPhone's CPU into running unauthorized code, but it's very hard to estimate the success rate of those kinds of approaches, as they are very dependent on the specific system being attacked.

## Is there a way for users to secure themselves against these attacks?

If the user's PIN is actually a complex alphanumeric passphrase, then the equation does change--at that point, the user's data _is_ cryptographically protected with a strong key, and bruteforcing it becomes impractical, with or without Apple's cooperation. The reliance on Apple not using their power for evil only goes as far as enforcing the policy on PIN retries. If, even without that policy, it's impractical to try all possible passphrases until the user's passphrase is found, then the retry limit doesn't matter. This also applies to the other attacks above that do not rely on Apple's help.

One way of doing this without a major inconvenience is to use a newer iPhone with Touch ID and use a long and complex passphrase to unlock it. The phone is still convenient since the passphrase only has to be entered rarely (such as on first boot). Then all you have to do is make sure you do not lose your phone (or have it seized) while it is still powered on--an attacker might be able to obtain and replicate your fingerprint to unlock the phone, but if it is powered off, there is nothing they can do to unlock it without your passphrase.

One thing worthy of note is that the iOS user data protection currently only applies to file data, but not metadata--such as filenames. Not 100% of files are encrypted either, so there is the possiblity that an attacker could gain tidbits of information from unencrypted portions of the filesystem, if they can defeat the full-disk encryption protection (which Apple can, with rogue firmware, as they did for previous iOS versions). Most third party application data is encrypted by default, but it is my understanding that apps can deliberately opt out of this encryption if they so choose. There is no way to fully secure metadata, as it is never protected by the user's PIN or passphrase. This is in contrast to Android, which does use the user's PIN or passphrase to protect all data and metadata when full disk encryption is enabled (which is why the passphrase must be entered early during the boot process, and the phone is useless and cannot do anything until it has been).

## Aren't newer phones safe anyway?

No. Although newer phones include what Apple calls a [Secure Enclave](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=7)[page 7], which is a separate CPU dedicated to security operations and isolated from the main CPU, it does not have a separate policy for what firmware it will run. The Secure Enclave firmware is just [one more component of iOS](https://twitter.com/JohnHedge/status/699882614212075520), and Apple can freely modify it, sign it, and deploy it on a phone. A common misconception is that the Secure Enclave firmware is separately "upgraded", but, in fact, it is a component of the main iOS firmware that is [loaded into the Secure Enclave memory](https://twitter.com/JohnHedge/status/701673688752484352) on every boot, as the Secure Enclave does not have any separate firmware Flash memory and is just a component of the main A7-A9 chip. For this attack, it makes no difference.

## So the Secure Enclave does not help at all?

It does. The Secure Enclave helps protect against the "jailbreak" attack scenario: to pull off an attack (exploit) based on a vulnerability in iOS, you'd have to find a vulnerability not only in the main system firmware (which includes a very large amount of code, and is "relatively" easy: this is what jailbreakers do), but also in the Secure Enclave firmware (which is much smaller, better audited, and less likely to contain exploitable bugs). This is because the Secure Enclave is [responsible for enforcing PIN delays and policy](https://www.apple.com/business/docs/iOS_Security_Guide.pdf#page=12)[page 12].

## What about the replay attack?

As I understand it, Secure Enclave-equipped phones have additional protection against replay attacks, in the form of a separate memory device (an EEPROM) on the board which is used by the Secure Enclave for storage of critical security information, to prevent replay attacks. However, this storage is still on a separate chip on the board, which can still be removed, re-written or emulated (along with the main NAND flash chip), to perform the replay attack.

So, although mechanically/physically the attack is somewhat more complex, it doesn't fundamentally change, from a security perspective. The problem is that, without some kind of re-writable secure memory storage, there is no way to protect against replay attacks. If the A7 chip had built-in Flash memory, this wouldn't be an issue, but for manufacturing reasons embedding Flash memory into a high-end modern system-on-chip like the Apple Ax series is impractical. These chips have [write-once memory](https://en.wikipedia.org/wiki/Programmable_read-only_memory) (used, for example, for the UID key), but not re-writable memory.

## How can security be improved further?

Although Apple currently cannot claim that it is _technically impossible_ for them to assist the FBI, they could design a future revision of the iPhone and iOS to be able to make that claim.

The core issue at hand is that, currently, all iPhones fully trust firmware signed by Apple. That is, Apple has the ability to run any firmware they want, at any time, on any iPhone (both on the main CPU and the Secure Enclave), assuming they physically possess it, with no effect on the user's data stored on the phone.

This can be changed, however. If the design were modified such that access to the user's data were conditional on the phone running a _particular_ piece of firmware -such as the current version of iOS installed on the phone- then users could be protected from "rogue" firmware used by Apple. This could work, for example, by wrapping ("entangling", in Apple terminology) the user's data encryption key with a hash of the iOS firmware currently installed on the phone. Although Apple could replace the firmware with another version at any time, the design of the boot process would guarantee that said new firmware cannot access any user data. This requires both hardware support (to maintain some kind of access policy for encryption keys) and firmware support (to enforce that policy during boot, and the entangling with the firmware version hash), but it is entirely reasonable to implement it on a newer revision of the iPhone's CPU. Updates would be handled by being authorized by the user (while the phone is unlocked) so that the user's keys can be re-entangled with the to-be-installed firmware version.

## Would that make targeted attacks against iOS users impossible?

No, it is not a foolproof security measure. In particular, it cannot protect the user against a targeted attack _while the user still has the phone_: Apple could deliver a malicious, rogue over-the-air system update masquerading as a legitimate one, and the user might install it being none the wiser. This could be mitigated by having the update process display a hash of the firmware version, which could be checked against online sources of "known good" iOS version hashes, but this is not a very user-friendly process and it's unlikely that Apple would go for it.

However, the above approach should protect against a situation where the phone is stolen or seized and is no longer under the user's control. Without knowledge of the PIN code, modified firmware cannot be used or installed without losing access to the user's data.

## Is the replay attack a lost cause? Can that be fixed?

It can. What is needed is secure memory storage--that is, memory that can communicate with the main CPU (or the Secure Enclave, if applicable) using a secure channel, with replay attack protection.

The eMMC memory chip in some Android phones has a feature called the [Replay Protected Memory Block (RPMB)](http://rere.qmqm.pl/~mirq/JESD84-A44.pdf#page=86)[page 86], which is designed to solve this particular issue. This is a special section of memory in the eMMC (which is analogous to Apple's NAND flash) that can only be accessed by the main CPU by using cryptographic protection, and cannot be "rolled back" to a previous state, because it includes a counter that can only be incremented, not ever decremented. An attacker cannot just replace the eMMC with an emulator either, as the communications are secured by a secret key shared known by both the CPU and the eMMC chip. (Note: I am only describing the RPMB feature of the eMMC memory; I do not know whether it is actually used in any Android phones in a useful or secure way)

However, although the design solves the fundamental replay problem, eMMC flash memories are not designed as security devices, and eMMC memory manufacturers do not, in my opinion, have the security expertise required to truly design and implement a secure feature like this. The security of the RPMB is dependent entirely on the security of the firmware of the controller embedded in the eMMC memory chip, and most eMMC devices have secret "backdoor" commands that can be used to gain access to them, for purposes of debugging or, at times, even fixing bugs that cause data corruption in production. Therefore, I wouldn't bet my phone's security on the RPMB in an eMMC flash chip.

A more mature, well-tested technology that solves the problem is smart card chips, such as those used in "chip and PIN" bank cards. These chips usually include hardware cryptography, more secure firmware, physical defenses, and enough built-in secure memory. Apple could include one such chip on their phones to serve as secure, replay-protected memory storage, paired to the CPU so that it cannot be removed and emulated. People such as [Chris Tarnovsky](https://www.youtube.com/watch?v=tnY7UVyaFiQ) might still be able to pull off a replay attack against this kind of storage, but the bar would be significantly raised.

## Postscript

Feel free to contact me if you have any corrections or suggestions. I'll be happy to make any amendments based on reliable sources or on logical arguments that make technical sense. As mentioned before, this is based on a combination of public sources and my knowledge about security, so it's only as authoritative as I am (which is to say, it depends on how much you trust me to know what I'm talking about).

Finally, if you want more details on exactly how the iPhone's data protection system works, what modes it supports, and under what circumstances data is unlocked, check out this [article from 2014](http://www.darthnull.org/2014/10/06/ios-encryption) which covers it in more detail and also mentions the PIN bruteforcing attack (and whether Apple might or might not do it for law enforcement).
