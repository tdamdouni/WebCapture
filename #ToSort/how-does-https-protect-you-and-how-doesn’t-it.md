# How does HTTPS protect you (and how doesn’t it?)

_Captured: 2017-04-26 at 15:41 from [medium.com](https://medium.com/mozilla-internet-citizen/how-does-https-protect-you-and-how-doesnt-it-6c785884a130?source=userActivityShare-c79006fee040-1493214060)_

![](https://cdn-images-1.medium.com/max/2000/1*RDHvcuh3n0RueAMNbcwJkw.png)

by M.J. Kelly

We have long advised Web users to look for HTTPS and the lock icon in the address bar of their favorite browser ([Firefox!](https://www.getfirefox.com/)) before typing passwords or other private information into a website. These are solid tips, but it's worth digging deeper into what HTTPS does and doesn't do to protect your online security and what steps you need to take to be safer.

### Trust is more than encryption

It's true that looking for the lock icon and HTTPS will help you prevent attackers from seeing any information you submit to a website. HTTPS also [prevents your internet service provider (ISP)](https://www.wired.com/2017/01/half-web-now-encrypted-makes-everyone-safer/) from seeing what pages you visit beyond the top level of a website. That means they can see that you regularly visit [https://www.reddit.com](https://www.reddit.com/), for example, but they won't see that your spend most of your time at <https://www.reddit.com/r/CatGifs/>. But while HTTPS does guarantee that your communication is private and encrypted, it doesn't guarantee that the site won't try to scam you.

Because here's the thing: Any website can use HTTPS and encryption. This includes the good, trusted websites _as well as the ones that are up to no good_ -- the scammers, the phishers, the malware makers.

You might be scratching your head right now, wondering how a nefarious website can use HTTPS. You'll be forgiven if you wonder in all caps HOW CAN THIS BE?

The answer is that the security of your connection to a website -- which HTTPS provides -- knows nothing about the information being relayed or the motivations of the entities relaying it. It's a lot like having a phone. The phone company isn't responsible for scammers calling you and trying to get your credit card. You have to be savvy about who you're talking to. The job of HTTPS is to provide a secure line, not guarantee that you won't be talking to crooks on it.

That's your job. Tough love, I know. But think about it. Scammers go to great lengths to trick you, and their motives largely boil down to one: to separate you from your money. This applies everywhere in life, online and offline. Your job is to not get scammed.

### How do you spot a scam website?

Consider the uniform. It generally evokes authority and trust. If a legit looking person in a spiffy uniform standing outside of your bank says she works for the bank and offers to take your cash in and deposit it, would you trust her? Of course not. You'd go directly to the bank yourself. Apply that same skepticism online.

Since scammers go to great lengths to trick you, you can expect them to appear in a virtual uniform to convince you to trust them. "Phishing" is a form of identity theft that occurs when a malicious website impersonates a legitimate one in order to trick you into giving up sensitive information such as passwords, account details or credit card numbers. Phishing attacks usually come from email messages that attempt to lure you, the recipient, into updating your personal information on fake but very real-looking websites. Those websites may also use HTTPS in an attempt to boost their legitimacy in your eyes.

Here are some things you should do.

### Don't click suspicious links.

I once received a message telling me that my Bank of America account had been frozen, and I needed to click through to fix it. It looked authentic, however, I don't have a BoFA account. That's what phishing is -- casting a line to bait someone. If I did have a BoFA account, I may have clicked through and been hooked. A safer approach would be to go directly to the Bank of America website, or give them a call to find out if the email was fake.

If you get an email that says your bank account is frozen / your PayPal account has a discrepancy / you have an unpaid invoice / you get the idea, and it seems legitimate, go directly to the source. Do not click the link in the email, no matter how convinced you are.

### Stop for alerts.

Firefox has a built-in [Phishing and Malware Protection feature](https://support.mozilla.org/t5/Protect-your-privacy/How-does-built-in-Phishing-and-Malware-Protection-work/ta-p/9395#w_how-does-phishing-and-malware-protection-work-in-firefox) that will warn you when a page you visit has been flagged as a bad actor. If you see an alert, which looks like [this](http://itisatrap.org/firefox/its-a-trap.html), click the "Get me out of here!" button.

### HTTPS matters

Most major websites that offer a customer login already use HTTPS. Think: financial institutions, media outlets, stores, social media. But it's not universal. Every website out there doesn't automatically use HTTPS.

It's not difficult for sites to convert. The website owner needs to get a certificate from a certificate authority to enable HTTPS. In December 2015, Mozilla joined with Cisco, Akamai, EFF and University of Michigan to launch [Let's Encrypt](https://letsencrypt.org/), a free, automated, and open certificate authority, run for the public's benefit.

HTTPS across the Web is good for Internet Health because it makes a more secure environment for everyone. It provides integrity, so a site can't be modified, and authentication, so users know they're connecting to the legit site and not some attacker. Lacking any one of these three properties can cause problems. More non-secure sites means more risk for the overall Web.

If you come across a website that is not using HTTPS, send them a note encouraging them to get on board. Post on their social media or send them an email to let them know it matters: _@favoritesite I love your site, but I noticed it's not secure. Get HTTPS from @letsencrypt to protect your site and visitors. _If you operate a website, encrypting your site will make your it more secure for yourself and your visitors and [contribute to the security of the web](https://internethealthreport.org/v01/stories/lets-encrypt-making-the-web-safer/) in the process.

In the meantime, share this article with your friends so they understand what HTTPS does and doesn't do for their online security.
