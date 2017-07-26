# Is Passwordless Authentication More Secure Than Passwords?

_Captured: 2017-04-10 at 01:08 from [dzone.com](https://dzone.com/articles/is-passwordless-authentication-more-secure-than-pa?edition=288887&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-09)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

One place where both businesses and consumers agree is login safety. For consumers, it's important that they trust the login of their apps and websites because they are handing over sensitive, personal information. For businesses, keeping that information safe is of the utmost importance -- nobody wants to send out a [notification that their system has been breached](http://arstechnica.com/security/2016/06/how-linkedins-password-sloppiness-hurts-us-all/).

So when a new way to log in comes along, it's only natural that we respond with skepticism -- is this _really _safe? -- because we know how important a secure sign on is. In the case of passwordless authentication, that reaction is particularly strong, because we have had it drilled into our heads that passwords are the ultimate source of protection for your account.

Although that skepticism is healthy and helps us find the best, most secure ways to log in, Auth0 is here to clear things up. Not only is passwordless authentication safe to use, it might even be safer than a traditional username + password login.

## What Is Passwordless Authentication?

Passworldess authentication is a way to configure your login, well, without a password. For example, a user might register their email and then receive a single-use passcode for each sign on. One common example of this is[ Slack's magic links](https://auth0.com/blog/how-to-implement-slack-like-login-on-ios-with-auth0/). Put in your email, hit "Send Magic Link," and you can log into Slack from your email inbox with no password.

![Slack Magic Link](https://cdn.auth0.com/blog/passwordless/slack_magiclink.jpg)

> _While it is not as popular as other forms of login yet, it is sustaining rapid growth._

![Passwordless Connections](https://cdn.auth0.com/blog/passwordless/passwordconnection.png)

In fact, by our estimates, it could overtake passwords as the [primary form of login](https://auth0.com/blog/analysis-of-passwordless-connections/) within the next ten years.

![Forecast vs Passwordless](https://cdn.auth0.com/blog/passwordless/forecast-up-vs-passwordless.png)

But magic links are just the tip of the passwordless iceberg. There are several different [ways you can configure your passwordless login](https://auth0.com/blog/how-passwordless-authentication-works/). Here's a quick overview:

  * **Magic link through email:** In this scenario, a user is asked for their email. Once they've given it, the IAM (in this chart, Auth0) facilitates the creation of a token that allows the user to log in through a link sent to their email. ![Passwordless email magic link start flow](https://cdn.auth0.com/blog/passwordless/passwordless-email-magic-link-start-flow.png)

  * **Code through email: **This works similarly to a magic link, but instead of a token, a one-time code is generated. This starts a session when a user retrieves the code from their email and puts it into the app or website. ![Passwordless create user flow](https://cdn.auth0.com/blog/passwordless/passwordless-create-user-flow.png)

  * **Code through SMS: **This is the same process as code through email, but the one-time code is sent through SMS instead. Auth0 [protects SMS messages](https://auth0.com/blog/how-passwordless-sms-authentication-can-improve-your-app/) with Twilio to keep everything secure.
  * **Auth0 Guardian: **Instead of putting in a password, with Auth0 Guardian you can approve or deny login requests on a second device paired with your account via the Guardian app (compatible with smartphone or smartwatch). When there's a login attempt, you get a push notification that allows you to log in with the swipe of a finger. ![Guardian](https://cdn.auth0.com/blog/passwordless/guardian.png)

  * **Touch ID: **Instead of a password, Touch ID uses a fingerprint to log you in. When you set up Touch ID, [your fingerprint is paired with a unique key](https://auth0.com/blog/how-fingerprint-auth-gives-you-security/) that is accessed every time you authenticate. In this way, it sets up an original login without sending your biometric data off of your device. Since fingerprints and other biometric data are becoming more integrated to our electronic devices, it's easier than ever to rely on it for authentication.
![TouchID Flow](https://cdn.auth0.com/blog/passwordless/passwordless-touchid-flow.png)

## How Does the Safety of Passwordless Authentication Compare to Other Logins?

The technical side of both passwordless and username + password authentication has many considerations. It's up to the company to make sure that they are storing customer information correctly and to protect it from hacks. There are best practices for each method, and, if done correctly, there isn't a runaway winner.

Here's a brief rundown of how things stack up on the technical side of things:

  * **Touch ID**: Apple cites [1-in-50,000 chance](https://support.apple.com/en-us/HT204587) of a fingerprint being guessed or interpreted as a false positive. There have been [reports of fake fingerprints ](http://www.cheatsheet.com/gear-style/smartphone-fingerprint-scanners-are-they-secure.html/?a=viewall)being printed and used to log into phones, although it is not likely that fingerprints are currently being stolen and printed en masse.
  * **Numerical Passcode:** Apple cites a [1-in-10,000 chance](https://support.apple.com/en-us/HT204587) of a numerical passcode being guessed (or generated).
  * **Passwords and passphrases:** If a password or passphrase is unique and complex, it can be a perfectly adequate form of security.
  * **Login codes and magic links: **Since each time a login code or link is used it is generated, there isn't the same type of risk for a security risk via brute force generation. When a login code or link is sent, an IAM should ensure that the channel is secure. If the code or link is not used within a certain time frame, login access will expire, to guard against malicious use.
  * **SMS risks:** Codes sent via SMS may carry more risk factors because of [phone networks' vulnerabilities](https://www.wired.com/2016/06/hey-stop-using-texts-two-factor-authentication/), but otherwise operate similarly to other login codes and magic links.
  * **Guardian:** App authenticators like Auth0's Guardian also use token generators, but have the benefit of not relying on SMS messaging.

All good IAM systems like Auth0 will have safety nets in place to mitigate the risks of brute force attacks, recognize malicious login attempts, and alert users of potential threats. They will also have advanced encryptions to keep data safe and will do their utmost to protect data at every step of the process.

Where things really get interesting is how user behavior affects the safety of login systems.

Unfortunately, even the best-laid plans can be rendered insecure when people use unsafe login practices. Let's look at how user behavior can compromise the safety of authentication, and especially how passwordless authentication deals with this.

### Username + Password

By now, it's pretty clear: we reuse the same passwords over, and over, and over. The Telegraph reported that "the data shows that at least some people are still [failing to heed even the most basic security principles](http://www.telegraph.co.uk/technology/2016/01/26/most-common-passwords-revealed---and-theyre-ridiculously-easy-to/) about secure codes." When you look at the [best ways to keep your personal information secure](https://auth0.com/blog/personal-information-security-identity-guide/), it's no wonder why: it takes time and attention to ensure security with a password.

With an average of [130 accounts](http://blog.dashlane.com/wp-content/uploads/2015/07/MailboxSecurity_infographic_EN_final1.jpg) registered to one email in the US, it's not surprising that [73% of users](https://www.telesign.com/resources/research-and-reports/telesign-consumer-account-security-report/) have duplicate passwords. To remember 130 different passwords would be extremely difficult for anyone -- and probably send password retrieval requests through the roof.

![Online hoarders](https://cdn.auth0.com/blog/passwordless/online-hoarders.png)

These bad habits can make it hard to protect your users, no matter how good your system is. When one password is used across multiple accounts, that's a huge risk that is completely out of your hands.

### Eliminating the Password

Passwordless authentication, by its nature, eliminates the problem of using an unsafe password. This means that one of the biggest user errors is taken out of your login.

One of the biggest skepticisms around passwordless authentication is the idea that using a channel like email to send a code or link can be unsafe because it can be compromised. This is a legitimate concern, but a compromised email account could also be used to "reset" a password, and therefore this concern presents no additional risk for the passwordless method over username + password login.

Passwordless authentication can also have the added benefit of two devices required for login. If you are authenticating with Auth0 Guardian, for example, you would need the device paired with the account in order to access that account, even if you knew the username. Of course, it is possible for devices to be stolen, but it makes malicious logins more difficult

Requiring two devices for login is part of multi-factor, physical authentication, which is the most secure login option. Each individual method has a [single point of failure](http://www.imore.com/talk-mobile/future-authentication-biometrics-multi-factor-and-co-dependency-talk-mobile), and multi-factor authentication helps reduce the impact of a single system's flaws.

## For Login, Passwordless Is the Future

Although this has not been an exhaustive exploration into all of the safety considerations relevant to the username + password and passwordless methods, it's clear that the technical foundations of passwordless authentication are safe and robust.

Although username + password is currently the most familiar login method, it is by no means the gold standard. Yes, much of this rests on the way that users behave. Unfortunately, humans simply aren't built to remember and use different secure passwords for all of our 130 accounts.

Passwordless authentication, then, is becoming an increasingly relevant option for login. Users are connected to more devices and have more accounts than ever, which means that the passwordless approach is only growing more convenient for users. Sometimes it's also the case that you have to save the user from themselves -- and for that, passwordless_ is_ a clear winner.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
