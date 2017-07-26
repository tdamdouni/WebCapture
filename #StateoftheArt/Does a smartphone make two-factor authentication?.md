# Does a smartphone make two-factor authentication?

_Captured: 2016-03-18 at 11:57 from [www.csoonline.com](http://www.csoonline.com/article/3044605/security/does-a-smartphone-make-two-factor-authentication.html)_

![hands coffee smartphone technology](http://images.techhive.com/images/article/2016/03/hands-coffee-smartphone-technology-100649899-primary.idge.jpg)

Here's a polarizing question: is a phone a second factor, in the context of two-factor authentication? Fellow infosec pro [@johnnysunshine](https://twitter.com/johnnysunshine) tweeted the above last week, and sparked a lively debate.

Before answering the question, let's back up a bit and [explain two-factor authentication](http://www.securityforrealpeople.com/2015/10/grog-and-narg-teach-two-factor.html) (or 2fa). To borrow an analogy I first used two years ago: 10,000 years ago, Grog and Mag formed a secret club. To ensure new members of the club would be accepted, they came up with a secret phrase. Thus was born the first password. One day Narg overheard two members greeting one another and learned the secret phrase. Thus occurred the first password breach.

Passwords can be stolen though, whether through a server database breach, or via a [phishing scam](http://www.securityforrealpeople.com/2015/06/please-oh-please-wont-you-phish-me.html), or by keylogging malware that captures the password as you enter it into a webpage. If a password is the only thing protecting your account, then a stolen password lets an attacker pretend to be you. If the attacker knows the right password, the server or website has no way of knowing it's an impostor.

By adding a second factor - something you physically possess (an identification card, or a token generator, or - the crux of today's question - a phone), the bar for an attacker is raised. Individually, each factor might be relatively easy to defeat. Gaining access to both a password and a device at the same time though takes more effort, and is far less likely. Not impossible, but less likely.

### About that phone...

![For the average consumer, 2FA using a phone is reasonably strong, and far better than nothing](http://images.techhive.com/images/article/2016/03/2fa-phone-2-100650789-large.idge.jpg)   


Two-factor means you as the user have to have a second thing with you to serve as the second factor. Some services offer a physically unique device to serve as the second factor - often something along the lines of an "RSA Token" \- a small device about the size of a USB flash drive that displays a number, which changes every minute or so. Less common is a token the size and shape of a credit card that does the same.

But think about the number of important accounts you have: banks, credit card accounts, email accounts, social media accounts. Carrying one "second factor" around might not be a nuisance, but carrying a dozen around becomes impractical in a hurry. What is something almost everyone has though, and has with them at almost all times?

A cell phone.

Service providers caught onto this a few years ago and began implementing a form of two-factor authentication in which the provider sends a SMS or text message with a typically six-digit code to enter along with your password. Similar to a physical code generator, the SMS code is only useful for about a minute before it changes to something else.

More recently, companies including Google, game maker Blizzard, and security provider Duo have produced Android and iOS authenticator apps that emulate the function of a code generator. Functionally though, they behave the same: they give a one-time-use token that is good for about a minute, and must be used along with the password in order to log into an account.

### So what's the big deal?

![The downside to using a phone as a second authentication factor: it can be compromised.](http://images.techhive.com/images/article/2016/03/2fa-phone-3-100650791-large.idge.jpg)   


Well, as Twitter alias [@munin](https://twitter.com/munin) implies, phone malware and malicious actors. The story that kicked off this discussion described a [sophisticated new mobile malware scheme](https://www.grahamcluley.com/2016/03/android-trojan-intercepts-sms-messages-bank-accounts/) currently targeting customers of 20 banks in Australia, New Zealand and Turkey. The initial bait was a popup message indicating that a particular website required installing "Flash Player" \- but the install link was fake. Upon installing the malicious fake Flash Player, the program would silently scan the phone for the mobile apps of targeted banks and download additional payloads for each app found.

To defeat two-factor authentication, the malware can forward SMS communication to the attacker. It can also delete SMS communication from the phone itself, enabling the attacker to generate and intercept future 2FA tokens without the user being aware. Security firm ESET has all the gory details in their [analysis of the malware](http://www.welivesecurity.com/2016/03/09/android-trojan-targets-online-banking-users/).

### So, phones _aren't_ suitable for two-factor authentication?

![What raises the bar while adding negligible overhead for the consumer? A phone.](http://images.techhive.com/images/article/2016/03/2fa-phone-4-100650792-large.idge.jpg)   


If you ask 10 security experts that question, you'll get 12 answers. There are many experts whose opinions I respect, that will disagree with me - and that's OK. Read the [discussion that follows the original tweet](https://twitter.com/johnnysunshine/status/708000062786248704) and you will see a variety of well-informed opinions on both sides. Cyber security is a complicated field, fraught with threats and exploits.

But Security For Real People exists to give reasonable advice for reasonable security. Saying mobile two-factor authentication is too risky to use is no help to you - because what is your alternative? Two-factor authentication using a phone is convenient to you, it is [widely available](https://twofactorauth.org/), and it raises the bar for an attacker significantly. Can it be defeated? Sure. But using a password alone is far more likely to result in a compromised account.

Bottom line? For accounts that you would be seriously unhappy to have broken into, if the provider offers two-factor authentication using your cell phone, by all means take advantage of it.

**This article is published as part of the IDG Contributor Network. [Want to Join?](http://www.csoonline.com/contributor-network/signup.html)**
