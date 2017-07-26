# How iOS 9's Safari View Controller could completely change your app’s onboarding experience.

_Captured: 2015-12-05 at 13:43 from [library.launchkit.io](https://library.launchkit.io/how-ios-9-s-safari-view-controller-could-completely-change-your-app-s-onboarding-experience-2bcf2305137f#.f40d1ygug)_

_Getting somebody successfully onboarded into your app is fraught with pitfalls and hiccups which prevent them from becoming a regular user. Here's a potential solution for it._

Every social app out there relies on some form of invitation to get people to become new users. It usually involves an email or SMS sent to prospective new users, enticing them to sign up.

On the web, or where people are using computers, this generally is considered a Solved Problem™. The user clicks a link with a special, unique code in it, instantly identifying them on the webpage, allowing the site to tailor the onboarding experience for the new person.

In an iOS app, there are 2 additional complications:

  1. The invited user must download an app.
  2. The app has _no idea_ who the user is, or where they came from.

This means that even the best invitation flow looks like this:

  * User receives an email from someone to be friends in a new iOS app.
  * User clicks on a special link in the email, which opens a webpage in Mobile Safari.
  * Knowing who the recipient was, the web app eases the signup process by pre-filling data.
  * User signs up at the site, and decides to download the iOS app.
  * **When she starts the iOS app, she's unexpectedly presented with a sign-up or login screen**.

> _Before iOS 9, there's no way for your app to know anything about who the user is, or even that the user visited the company's website and signed up for an account._

At this point, you would think the user would intuitively just log in to the app using the same credentials she used on the site. However, [you are not your users](http://uxmyths.com/post/715988395/myth-you-are-like-your-users), and many things can go wrong:

  * Some get frustrated, feeling like they _just_ did this (which they did).
  * Some others people will mistakenly try to sign up again.
  * There's even some that will sign up with [a different email address](https://library.launchkit.io/the-unexpected-costs-of-third-party-login-cda41c087653) than the one they were invited with, which complicates private sharing apps.
  * They have forgotten their password or even email address they used to sign in with (see 2nd bullet)

Luckily, Apple has been listening and watching how native apps have been struggling to transition a user from the web to an app and have offered a few solutions over the years, but they're not so great, as you'll see.

I'm going to show you how iOS 9's Safari View Controllers might make this way easier, but first let's take a look at what the current tools by Apple are:

The first not-so-great solution by Apple is Smart App Banners. When your user is viewing your site in Mobile Safari, a banner can display across the top that lets you open this page within the app. With this, a trick can be to include some sort of auth token within the url, so when the app receives the url, it can perform a behind-the-scenes sign in.

However, this only works if the app is already installed, which a new user is not likely to have. If the app is not installed initially, the smart app banner shows an "Install" link, which takes you to the App Store. After installing the app, the user would have to _know_ to return to the website, _then_ press "Open" in the app banner in order to sign in. This makes the Smart App Banner not a realistic helper in the onboarding process.

I can't completely discredit Apple here though, because I don't think they were designed to help this onboarding problem.

The next not-optimal solution that Apple came up with is Shared Web Credentials. Essentially, if you save your passwords to iCloud Keychain (which you generally turn on at setup), then the app can access the passwords.

You can create a special **apple-app-site-association** file to the root of your website, and it will whitelist any apps which can access any saved passwords that the user may have stored while signing in on the web.

In the native app, it can query the shared web credentials and get access to the email and password and sign you in.

However, in my opinion, this is not been a great solution: a) iCloud Keychain needs to be enabled, b) your site needs to have some of a password login, and c) the user must agree to save their password to iCloud Keychain _before_ running your iOS app.

### Introducing Safari View Controller

At [WWDC 2015](https://developer.apple.com/wwdc/), Apple [introduced Safari View Controller](https://developer.apple.com/videos/wwdc/2015/?id=504) as a way for developers not to have to create mini-browsers of their own, to show small bits of web content inside their own apps. (Like what happens when you tap a link in the Twitter app: Rather than go to Mobile Safari, Twitter will open its own browser window for you to view the content).

Safari View Controller is a pre-built browser that has all the bells and whistles of Mobile Safari, but can be presented without leaving your app.

[Ricky Mondello](https://twitter.com/rmondello), a Safari and WebKit engineer at Apple, [says](http://asciiwwdc.com/2015/sessions/504) (emphasis mine):

> And with Safari in the name, Safari View Controller brings features that your users already love from Safari, but now they're in your app.

> **Let's start off, first and foremost Safari View Controller shares cookies with Safari and other website data.**

> **So what this means is if one of your users is already logged into a website in Safari, if they tap a link in your app and Safari View Controller comes up they might still be logged in**.

But there's something else nobody has been focusing on: In addition to third-party services being logged in, _you can also see if YOUR users are logged into your web app already_, so you can seamlessly sign them into your iOS app!

#### A Real-World Example

For the last couple of years, I've worked on [Cluster](https://cluster.co), an app for sharing photos and videos with small groups of people. Think Instagram mixed with privacy and multiple feeds.

One of the biggest challenges for Cluster (and any app where content is shared to specific people only) is how to invite someone easily, and have them identify themselves to Cluster the same way they were invited (i.e. they use the same email address to sign-up with, that they were invited with).

For the longest time our solution has been:

  * When the user receives an email or sms invite, they click a link, which takes them to Mobile Safari and gets them to sign up on the web.
  * Then we encourage them to download the iOS app and use that instead (Cluster is primarily heavy media sharing, so works better in a native app)
  * Hope/cross fingers/pray that they sign in with the same account they just created.

For the most part, it works ok, but we still have people accidentally making new accounts with different email addresses, simply because they forgot what email address they had originally used. Then, they wonder why none of their private groups are showing up. To them it is as if Cluster completely "lost" their data.
