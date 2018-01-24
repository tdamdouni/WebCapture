# Inside Two-Factor Authentication Apps

_Captured: 2017-10-22 at 12:24 from [hackaday.com](https://hackaday.com/2017/10/16/inside-two-factor-authentication-apps/)_

![](https://hackadaycom.files.wordpress.com/2017/10/authentication1.jpg?w=800)

Passwords are in a pretty broken state of implementation for authentication. People [pick horrible passwords](http://www.whatsmypass.com/the-top-500-worst-passwords-of-all-time) and [use the same password](https://www.troyhunt.com/what-do-sony-and-yahoo-have-in-common/) all over the place, firms fail to store them correctly and then [their databases get leaked](https://haveibeenpwned.com/PwnedWebsites), and if anyone's looking over your shoulder as you type it in (literally or metaphorically), you're hosed. We're told that two-factor authentication (2FA) is here to the rescue.

Well maybe. 2FA that actually implements a second factor is fantastic, but Google Authenticator, Facebook Code Generator, and any of the other app-based "second factors" are really just a second password. And worse, that second password cannot be stored hashed in the server's database, which means that when the database is eventually compromised, your "second factor" blows away with the breeze.

Second factor apps _can_ improve your overall security if you're already following good password practices. We'll demonstrate why and how below, but the punchline is that the most popular 2FA app implementations protect you against eavesdropping by creating a different, unpredictable, but verifiable, password every 30 seconds. This means that if someone overhears your login right now, they wouldn't be able to use the same login info later on. What 2FA apps _don't_ protect you against, however, are database leaks.

![](https://hackadaycom.files.wordpress.com/2017/10/quote-2fa-database-leaks.png)

And you should absolutely be concerned about database leaks. Did you have a Yahoo account in 2013? Well, they got hacked. In late 2016 they revealed (three years later!) that a password database with a jaw-dropping 500 million passwords was breached. In December 2016, they upped that figure to a mind-blowing 1 billion. Well, it was [actually 3 billion](http://money.cnn.com/2017/10/03/technology/business/yahoo-breach-3-billion-accounts/index.html). That's every password they had, at Yahoo! and all of their subsidiary services.

But Yahoo! is not alone, even if the scale makes it unique. Name a large company, and they've probably been hit. It's to the point that responsible services protect their passwords in ways that are [designed assuming the database is eventually compromised](https://www.owasp.org/index.php/Password_Storage_Cheat_Sheet). Assuming that all databases will eventually be compromised is equivalent to assuming that 2FA as it's implemented at Google, Facebook, Dropbox, Microsoft, Twitter, Amazon Web Services, and almost all the rest, will eventually be broken.

But this is Hackaday, and we understand things best by taking them apart. So I'm going to step quickly through how 2FA apps work, and then show you how you can implement it yourself if you want in a few lines of Python. Along the way, you'll see for yourself why 2FA app secrets _can't_ be stored as securely as passwords can, and why a good strong password is still important. None of this is news, and this is not a hack, but taking a look inside the black box helps you assess security claims for yourself.

## 2FA and TOTP

[Two-factor](https://twofactorauth.org/) is great in theory. Instead of just relying on a password, "something you know" in the jargon, you combine another factor for authentication: "something you have" or "something you are". Ideally, this means requiring possession of a cellphone or security token, or presenting your fingerprint to be scanned. In theory, there's no difference between theory and practice.

![](https://hackadaycom.files.wordpress.com/2017/10/2017-10-16-122250_1024x1368_scrot.png)

In practice, because of cost and convenience, most 2FA implementations use an app that authenticates using the time-based one-time password (TOTP) algorithm. That is, it's just another password. In particular, Google's Authenticator app and the WordPress interface which I'm currently using implement "something I have" by storing this one-time password on my cellphone.

Remember that QR code on the screen when you enrolled your phone? That was the password. You could tell me this secret password, and then I'd know your account token too. With access to this initial password and a little code, I can log in without having a cell phone at all, much less yours. This is "something you know" rather than "something you have". If you think this is semantics, let's compare the security properties of SMS-based 2FA (which _is_ 2FA) and app-based "2FA" which isn't.

To fake an SMS-based 2FA query, someone has to have access to your phone number and receive a six-digit code, or at least overhear it along the way. Unless you're being targeted by hackers with very significant resources, they're not going to redirect phone traffic to hack you. And in the event that the SMS-number database gets compromised, the worst that happens is that the hackers can call you up. (At least in theory. In practice, the few SMS systems I've tested simply contain the current value of my TOTP password, which means that it's just as vulnerable as the application. They could do much better: by sending a random number, for instance.)

To fake an app-based 2FA query, someone has to know your TOTP password. That's all, and that's relatively easy. And in the event that the TOTP-key database gets compromised, the bad hackers will know _everyone's_ TOTP keys.

How did this come to pass? In the old days, there was a physical dongle made by RSA that generated pseudorandom numbers in hardware. The secret key was stored in the dongle's flash memory, and the device was shipped with it installed. This was pretty plausibly "something you had" even though it was based on a secret number embedded in silicon. (More like "something you _don't_ know?") The app authenticators are doing something very similar, even though it's all on your computer and the secret is stored somewhere on your hard drive or in your cell phone. The ease of finding this secret pushes it across the plausibility border into "something I know", at least for me.

![](https://hackadaycom.files.wordpress.com/2017/10/totp.png)

TOTP algorithms are far from worthless, however. The beauty of these algorithms is that the one-time secret password is hashed with some other number that's common knowledge to me and the server -- sometimes it's a simple counter. This generates a different "password" for every value of the counter. Because the [hash function is one-way](https://en.wikipedia.org/wiki/Cryptographic_hash_function), you can't figure out what my secret was even if you intercept the hashed value and know the counter. Contrast this with a regular password; if it's overheard in transmission, the attacker knows it forever.

In most TOTP implementations, the counter is the number of 30 second intervals that have elapsed since Jan 1, 1970 -- the Unix epoch. This gives you a different, strong, password every 30 seconds. Practically, servers will accept either the previous, current, or next values to allow for clocks to go a little out of sync, but after a minute or so, that old hashed value is useless to an attacker. That's pretty cool.

But it's _not_ "something you have" or "something you are" and it's not safe against database compromises. Want proof? Let's make our own.

## DIY

To make your own Authenticator, all you need is the password. Usually this is conveyed to your cell phone in the form of a QR code. You download their app, point your phone at the screen, and it converts the QR code into the 80-bit password. But you don't want the QR code, so refuse it. Click "can't use the QR code" or "manual entry" or whatever until you get to a code that you could write down. Some sites give you hexadecimal, others give you base-32, but you'll soon be looking at 16-20 letters and numbers. That is the TOTP key that's going to be hashed with the time counter to generate the session passwords.

As for the secret one-time password itself, the standard that almost all websites adhere to is pretty good at 80 bits -- presumably of full entropy. If you're using a good human-chosen password right now, you're probably around 30 bits. "[Correct horse battery staple](https://www.xkcd.com/936/)" only gets you 44 bits. So 80 bits is looking pretty good, and you won't be re-using the same secret across different web domains either.

The basic idea of TOTP works under the hood are actually pretty straightforward. It's a [hash-based message authentication code](https://en.wikipedia.org/wiki/Hmac) (HMAC) with the time-dependent counter as the message. A HMAC essentially appends a message to your secret key and hashes them together, the idea being that anyone with the password can verify the integrity of the message, and verifying the HMAC signature confirms that the other person has the same secret key.

The details to both HMAC and TOTP are the killer. HMAC actually hashes the secret and message twice, with different padded versions of the secret. This prevents [length-extension attacks](http://blog.mmmonk.net/2012/09/sha-1-length-extension-attack-example.html) by using different keys on the first and second hashing rounds. The final value that comes out of a TOTP routine is the value of four bytes, the location of which depends on the value of the nineteenth byte. This is called [dynamic truncation](https://tools.ietf.org/html/rfc4226#section-5.3), and implementing this correctly in Python cost me some gray hairs.

Anyway, there are TOTP libraries out there, and for production work you should probably use them. The Linux program `oathtool` can implement a TOTP nearly every way possible, and was an invaluable benchmark during development. (Call it with the `-v` flag for verbose debugging output.) But if you want to see how TOTP works, here's some code:

## Implications

We can generate the TOTP password with just the time and the secret key. So how does the server authenticate us? By following the exact same procedure. And this means that the server must have access to the secret key as well, which means that it can't be stored hashed because hashes are one-way. Think about that: the server knows your secret.

![](https://hackadaycom.files.wordpress.com/2017/10/quote-totp-database-breach-worse-than-password-breach.png)

This is not the case for a regular password, which should never be known by the server at all! Once you've entered your password for the first time, the server hashes your password and stores that hash, forgetting the original password forevermore. When you enter a password the next time, it hashes what you've typed and checks to see if it matches the stored hash. Because the server only keeps a hashed version of your password, because it's a [good one-way hash with a salt](https://security.stackexchange.com/questions/51959/why-are-salted-hashes-more-secure-for-password-storage#51983), and because you chose a strong password, it's virtually impossible to get your password back out of the database even when it's publicly available.

The practical upshot of all of this is that, although some websites still don't, all should be able to store normal passwords hashed, and will thus be relatively safe even if their password database gets hacked. If you've used a good password, that'll buy you some time, even if the breach is discovered a while after the fact. On the other hand, if your password gets snooped in transit, you're done for.

TOTP keys simply can't be stored hashed, because the authentication algorithm requires them in raw form. When the TOTP key database gets compromised, all of the TOTP / 2FA protection becomes worthless and you're relying on the strength of your password to save you. Until the database gets breached, however, the ever-changing TOTP password is a great protection against eavesdroppers.

Getting the best of both worlds is easy enough: use TOTP / 2FA when it's available, but make sure that your passwords are unique across websites and that each one is long and strong. But don't fool yourself into thinking that 2FA is a substitute for good password practices -- you'll be living just one database breach away from the edge.
