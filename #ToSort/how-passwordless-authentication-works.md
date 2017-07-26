# How Passwordless Authentication Works

_Captured: 2017-06-20 at 19:38 from [dzone.com](https://dzone.com/articles/how-passwordless-authentication-works?edition=305104&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-19)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

## What Is Passwordless Authentication?

Passwordless authentication is a type of authentication where users do not need to log in with passwords. This form of authentication totally makes passwords obsolete. With this form of authentication, users are presented with the options of either logging in simply via a magic link, fingerprint, or using a token that is delivered via email or text message.

## How Did Passwordless Authentication Come About?

Over the years, cases of stolen and hacked passwords have been on the rise. So many cases, such as the [Yahoo data breach](https://auth0.com/blog/yahoo-confirms-data-breach-of-half-a-billion-user-accounts/), [Dropbox user accounts leak](http://www.foxnews.com/tech/2016/08/31/dropbox-data-breach-68-million-user-account-details-leaked.html), and [LinkedIn Data Breach](http://fortune.com/2016/05/18/linkedin-data-breach-email-password/) had to do with having several passwords leaked.

In addition, platforms and applications keep emerging by the day and users have to register and set passwords for almost every one of them. Users are finding it really hard to keep up, thus encouraging them to use the same password for several applications. This is a very [common occurrence](https://nakedsecurity.sophos.com/2013/04/23/users-same-password-most-websites/). Now, there is a problem with this approach. Once a hacker gets access to user's password for one application, the hacker has a high probability of gaining access to every other account the user possesses. Password managers like [LastPass](https://www.lastpass.com/) and [1Password](https://1password.com/) attempt to combat the challenge of users having to remember strong, crazy, and unique passwords across various systems.

With these challenges staring down at us like a monster, what if there are no more passwords to be hacked? What if there are no more passwords for users to remember? What if we discard the use of passwords totally? Passwordless authentication to the rescue!

## Benefits of Passwordless Authentication

Without much ado, passwordless authentication helps:

  * **Improve User Experience:** The faster users can sign up and use your service, the more users your app tends to attract. Users dread having to fill out forms and go through a rigorous registration process. Imagine eliminating that extra five minutes of asking users to remember their grandmother's maiden name as a security question. Passwordless authentication helps improve user experience in this regard!
  * **Increase Security:** Once you go passwordless, there are no passwords to be hacked.

## How Does Passwordless Authentication Really Work?

Having given a refresher on what passwordless authentication is and the benefits of its implementation, let's take an in-depth look at the process of implementing passwordless authentication in a typical application. Passwordless authentication can be implemented in various forms:

  * **Authentication with a magic link via email:** With this form of authentication, the user is asked to enter their email address. Once the user submits the email address, a unique token or code is created and stored. An email with a URL that contains the unique token will be generated and sent to the user. When the link is clicked by the user, your server verifies that the unique token is valid and exchanges it for a long-lived token, which is stored in your database and sent back to the client to be stored typically as a browser cookie. There will also be checks on the server to ensure that the link was clicked within a certain period, e.g. three minutes.

Let's take a look at Auth0's magic link implementation below:

![Email Magic Link](https://cdn.auth0.com/docs/media/articles/connections/passwordless/passwordless-email-magic-link-start-flow.png)

> _Auth0 sends a clickable link to your email_

![Email link received in inbox](https://cdn.auth0.com/docs/media/articles/connections/passwordless/passwordless-email-receive-link.png)

> _The user is then logged in._

![User Authenticated without using password](https://cdn.auth0.com/docs/media/articles/connections/passwordless/passwordless-authenticated-magic-flow.png)

  * **Authentication with a one-time code via e-mail:** With this form of authentication, the user is requested to enter their email address. An email is sent to the user with a unique, one-time code. Once the user enters this code into your application, your app validates that the code is correct, a session is initiated, and the user is logged in.

Let's take a look at Auth0's one-time code via email implementation below:

![Authentication with a onetime code via email](https://cdn.auth0.com/docs/media/articles/connections/passwordless/passwordless-create-user-flow.png)

If the email address matches an existing user, Auth0 just authenticates the user like so:

![Authenticates user](https://cdn.auth0.com/docs/media/articles/connections/passwordless/passwordless-authenticated-flow.png)

  * **Authentication with a one-time code via SMS:** With this form of authentication, the user is asked to enter a valid phone number. A unique, one-time code is then sent to the phone number. Once the user enters this code into your application, your app validates that the code is correct and that the phone number exists and belongs to a user, a session is initiated, and the user is logged in.

Let's take a look at Auth0's one-time code via SMS implementation below:

If the phone number matches an existing user, Auth0 just authenticates the user like so:

  * **Authentication with Fingerprint:** With this form of authentication, the user is asked to place their finger on a mobile device. A unique key pair is generated on the device and a new user is created on the server that maps to the key. A session is initiated and the user is logged in.

Let's take a look at Auth0's fingerprint implementation. Auth0 supports **Touch ID** for iOS. This is the authentication flow:

![Authentication with Fingerprint](https://cdn.auth0.com/docs/media/articles/connections/passwordless/passwordless-touchid-flow.png)

## Aside: Passwordless Authentication With Auth0

With Auth0, passwordless authentication is dead simple to implement. There are diagrams earlier in this post that already show the passwordless authentication flow using Auth0. You must have noticed a `Passwordless API` in those diagrams. This is a battle-tested and efficient [API implementation](https://auth0.com/docs/api/authentication#passwordless) of passwordless authentication. You can check out how it works under the hood or simply build your own implementation on top of it.

We can also easily configure our applications to use **Auth0 Lock** for passwordless authentication. Let's quickly create an application that implements a magic link by following the steps below:

  * Create an .
  * On the dashboard, click on the red `Create Client` button to create a new app like so: ![Create a Passwordless Application](https://cdn.auth0.com/blog/passwordlessApp.png)

  * Head over to the [Passwordless Connections](https://manage.auth0.com/#/connections/passwordless) side of the dashboard and enable the email option.![Enable Passwordless App](https://cdn.auth0.com/blog/enableEmailOne.png)

> _Enable Passwordless App_

![Enable Magic Link](https://cdn.auth0.com/blog/enableEmailLink.png)

> _Enable Magic Link_

![Save Configuration for Passwordless App](https://cdn.auth0.com/blog/enableEmailForApp.png)

> _Save Configuration for Passwordless App_

  * Head over to your settings tab for the `Passwordless App` and copy your `client_id` and `domain`![Passwordless Authentication Settings](https://cdn.auth0.com/blog/passwordlessSettings.png)

> _Settings Tab_

  * Open up `auth0-variables.js` in your code and replace the `AUTH0_CLIENT_ID` and `AUTH0_DOMAIN` values with your real Auth0 keys.
  * Run and test the app.![Click Magic Link Button](https://cdn.auth0.com/blog/clickMagicLink.png)

> _Click the Magic Link Button_

![Sign in without passwords](https://cdn.auth0.com/blog/lock-magic-link.png)

> _Follow the instructions and sign in_

![Email Modal](https://cdn.auth0.com/blog/inputEmail.png)

> _Submit your email on the Lock Widget_

![Magic link email notification](https://cdn.auth0.com/blog/notificationBox.png)

> _Notification Modal to show that the link has been sent_

![Magic Link from email](https://cdn.auth0.com/blog/magicLinkPasswordless.png)

> _Magic Link From Email_

![Signed in via the Magic Link](https://cdn.auth0.com/blog/welcomeEmailFromLink.png)

> _Signed in via the Magic Link_

If you don't want to go through the process of creating an app, there is an online version you can play with [here.](https://auth0.github.io/lock-passwordless/)

## Conclusion

There is no doubt that passwords have become more susceptible to being compromised in recent years. Passwordless authentication aims to eliminate authentication vulnerabilities. This recent [analysis of passwordless connections ](https://auth0.com/blog/analysis-of-passwordless-connections/)shows that passwordless adoption is increasing. Passwordless authentication is also very useful and gaining ground in the IoT world. It's easier, friendlier, and faster to be authenticated into an IoT device via Touch ID, push notification, or even a one-time passcode than with traditional means. If you really care about security, you should look into passwordless authentication!

We have covered how to implement practical passwordless authentication in an application using magic links. You can follow a similar process to achieve the same objective using a one-time code via SMS, and implement passwordless authentication today!

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.
