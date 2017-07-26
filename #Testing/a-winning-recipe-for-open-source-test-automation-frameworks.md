# A Winning Recipe for Open Source Test Automation Frameworks

_Captured: 2017-04-07 at 23:22 from [dzone.com](https://dzone.com/articles/a-winning-recipe-for-open-source-test-automation-f?edition=288885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-07)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

There's no doubt that the bulk of software delivery today relies on test automation through open-source test frameworks.

In a recent [blog post](http://blog.perfectomobile.com/mobile-application-testing/best-open-source-test-automation-tool-2/), I highlighted some of the main differences between the leading frameworks such as [Appium](https://www.perfectomobile.com/integrations/appium-extension), Selenium, Calabash, Espresso and XCTest UI.

As a quick summary, the key points that were identified as critical for success in adopting an open-source is to have these three robust ingredients supporting that framework:

  * 24x7 available and elastic Lab.
  * Advanced automation features.
  * Deep quality analysis post-execution.
![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/Frameworks.png)

> _In this post, let's talk about the second item above- Advanced Test Automation._

## **Extending Test Automation Coverage for Open Source Frameworks**

While it is important to have support for the basic automation features in the OS level, it is also important to extend framework capabilities to support:

  * Visual analysis.
  * User condition testing.
  * Full system level control.
  * Same day support for the latest platforms.

To give examples of why some of these extensions are important from a test automation coverage perspective, let's look at testing an app using [Espresso](https://www.perfectomobile.com/solutions/devtunnel/espresso-in-continuous-integration) or XCTest UI- while these frameworks are great, fast, and support the latest features from an OS level perspective, they do not support the full system level. That limits testing scenarios which cover things like incoming calls, events, popups, and things like the recent [iOS 10.3 2FA](https://9to5mac.com/2017/02/25/two-factor-authentication-ios-10-3/) (2 factor authentication) that requires an acknowledgment of an incoming text message with code, etc.

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/Index.png)

Consider a different example from a recent enforcement coming from Google around [privacy policy](http://www.zdnet.com/article/google-plans-purge-of-play-store-apps-without-privacy-policies/). It will mandate apps that are submitted to the Google Play Store, use sensitive data, and require "[dangerous permissions](https://developer.android.com/guide/topics/permissions/requesting.html#normal-dangerous)," to prompt the user with a privacy policy and permissions list so they Accept or Decline.

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/googledangerouspermissions.png)

In some cases, the test automation developers would like to run an additional validation of the policy and check how it appears when rotating the screen- are the buttons still visible? Are there any truncations of text?

Also, when testing such an app using Espresso and/or XCTest UI, the process requires 2 apps- one is the app under test (AUT). The second is the testing app, which also requires validation that the initial install of the app triggered the policy screen and, upon a new test, won't show up again (mostly from a test flakiness perspective).

For the above scenarios, it is important to state that most of the leading open-source test frameworks do not support visual test automation and analysis.

## **Consider Community Support for Open Source Frameworks**

Finally, open-source is all about community. If the community is not strong enough, or is biased toward vendors, its value to end users will be weakened from the perspectives of features, adaptation to free tools, and more.

A good source to consider when measuring open-source community strength is usually the github of these tools- how many branches? How many contributors, and where are they coming from? How many releases? With that in mind, let's compare a few frameworks just to see…

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/appiumcommunity.png)

> _[Selenium Community:](https://github.com/SeleniumHQ/selenium)_

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/seleniumcommunity.png)

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/XCTestUI.png)

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/Calabash.png)

![](http://blog.perfectomobile.com/wp-content/uploads/2017/03/GoogleEspresso.png)

As can be seen in the above examples, all of these communities are active, people are contributing and branching out of the master repo (not at the same volume, of course), and each has different [star gazer ratings and watchings](https://developer.github.com/v3/activity/starring/).

  * Stars would measure the interest in that specific repository- by people using bookmarks.
  * [Watchers](https://developer.github.com/v3/activity/watching/) would measure a number of people that subscribed to receive notifications on new discussions around that repository.

If we consider the entire measures of contributors, releases, branches, stars, and watchers, we can learn a lot about the level of support, interest, and traffic that a community gets. This makes it easier to pick one framework over another- especially when there is a debate after teams examine things like the above functional comparison matrix across all tools.

## **Bottom Line**

A winning recipe is an open source test automation framework that meets the automation capabilities your app requires, like visual validations and environment conditions, along with maintaining a robust and active community around that framework.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).

Topics:

mobile testing ,open source ,test automation ,appium ,espresso ,selenium ,cloud
