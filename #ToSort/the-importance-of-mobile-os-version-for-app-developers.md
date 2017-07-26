# The Importance of Mobile OS Version for App Developers

_Captured: 2017-03-25 at 19:26 from [dzone.com](https://dzone.com/articles/the-importance-of-mobile-os-version-for-app-develo?edition=286924&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-25)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

The operating system and its version have a crucial role for all development going on Android and iOS. The applications - whether considered as more traditional applications, gaming apps, hybrid or web apps - are the beef for end-users to get everything out of their devices. All those mobile apps play an essential role in determining if devices, OEMs,the platform itself, and the whole ecosystem can flourish.

In this blog, we'll take a look at Bitbar's data and analyze it a bit to understand why operating system versions are an extremely important factor for app developers, and why app devs should take every update seriously. Harshly, you know, the OS update can make or break the revenue generation from your app.

## The War of Mobile Apps and Ecosystems

Just a few years ago (2013 or so) and generally in the early of 2010s, there was a war of mobile ecosystems. From the retrospective point of view, how did all that play and where are we today? In 2010, Android has quickly gained traction with OEMs, Apple pushed their iOS forward and entrenched their app ecosystem with new applications and allured more app devs to jump on the bandwagon. However, the number of Android devices by a variety of different OEMs made Android also sexy among app devs, and more devs jumped on their (or both) bandwagons.

We all also remember the famous "[burning platform" memo by Stephen Elop](http://blogs.wsj.com/tech-europe/2011/02/09/full-text-nokia-ceo-stephen-elops-burning-platform-memo/) back in early 2011 - and as many of us mobile insiders thought, there was a truth in that metaphor, however, the resolution and pick for a new platform was completely wrong (and yes, everyone who was seriously into the mobile business knew it). _What would have happened if the giant was set to go Android waters?_ That's speculation and we'll skip that part for now.

Besides Windows, there were few others that were poised to be the next significant mobile OS platforms for apps, app developers, OEMs, and the whole mobile ecosystem. However, Android and iOS are the ones that remained popular - and for good reasons. App developers took both of them well and both Google and Apple got traction around the ecosystem and gave good incentives for developers to build their stuff on these platforms.

Going back to the comparison of these two, in general, the number of available Android apps exceeded the number of iOS apps around autumn 2012 - as shown in this statistic by xyologic:

![Image title](http://bitbar.com/wp-content/uploads/2017/03/Screen-Shot-2017-03-22-at-11.37.32-AM.png)

Since 2013, we've seen two major platforms become a standard (Android and iOS) for mobile apps that are very different from the app developers point of view. We've done several [comparisons of Android and iOS platforms](http://bitbar.com/app-stability-android-vs-ios-before-ios8/), including particular OS versions, chipsets, hardware setup, and a couple of other form factors.

## What Role Does the OS Version Play in Fragmentation?

There are lots of things that every [app developer should know about Android](https://www.smashingmagazine.com/2014/10/what-every-app-developer-should-know-about-android/). For example, the "F" word - fragmentation - is widely used to describe how differently apps work and are compatible with a variety of different devices. In the case of Android, there are more contributing factors for fragmentation (than with iOS): OEM branded devices (hardware), different adoption of the OS, different hardware specification, and a few others.

In the past, Android OS has been blamed for the platform fragmentation, making things very difficult for developers and users to keep up with upgrades, new tools, and so on. This is still the case and nowadays the major contributing fragmentation factor is the OS version. Yes, a few other factors such as OEM customizations, integration, and compatibility with other software (e.g. backends, services) cause issues for apps.

![Image title](http://bitbar.com/wp-content/uploads/2017/03/Screen-Shot-2017-03-23-at-1.32.09-PM.png)

On the hardware side of things, many things actually cause issues for developers and users. The display, its resolution, quality factors, and portrait/landscape use with apps are the most common display-related problems that both app devs and users see. The other notable root cause for fragmentation, or simply not getting apps working properly on devices, is the memory. Devices that do not have enough memory (RAM) may work badly, flaky, or simply can't perform well enough.

The above picture illustrates various characteristics that cause issues for developers and users. Let's take a look at how operating systems work differently when the same hardware setup is used. These figures, and generally this data, contains the test run data from our Bitbar Public Cloud (aka Testdroid Cloud) from the last year and thousands of apps have been used to validate the data.

### Android OS Versions Compared

![Image title](http://bitbar.com/wp-content/uploads/2017/03/Screen-Shot-2017-03-23-at-1.24.42-PM.png)

Comparing Android OS versions against each other is straightforward when the same application is used. The devices under testing should be identical with their hardware factors and because of this people testing of their apps should always [use real mobile devices for testing](http://bitbar.com/rely-only-on-real-emulators-vs-devices/). The emulated/simulated environment doesn't produce comparable or trustworthy results showing how the application actually works in hands of end-users.

### iOS Versions Compared

![Image title](http://bitbar.com/wp-content/uploads/2017/03/Screen-Shot-2017-03-23-at-1.25.37-PM.png)

Comparing iOS versions is no different from Android versions. Applications are executed on the same device with different OS version and basically with the same test script or smoke test run.

## The Importance of Mobile OS Version for App Developers

When looking at these statistics it's quite obvious that the difference of average failure rate is pretty close with both of these platforms. With Android, the average failure rate is **17.8%** and with iOS, it's only slightly lower, **15.5%**. And despite this slight difference between different OS versions, the trend is typically this: more bugs have been fixed on new sub-version of that specific OS version. For example, every minor release of Android and iOS OS reduces the number of issues that app developers see with their app.

When the new major OS version is released it typically increases the failure rate and there are various reasons why this actually happens. New APIs, features, even OEM customizations, and upgrades provide flakiness to the test foundation. As this is not "vanilla-Android" OS versions that we compared with Android devices, OEMs typically provide those OS versions (with their own stuff).

If you are looking for trends in [mobile app development and testing](http://bitbar.com/whats-trending-with-mobile-test-automation-frameworks/) remember to keep yourself updated with the latest news on the test automation field. There are constantly lots of things going on and new versions coming out to support your test automation efforts with these great mobile platforms.

We'll dive deeper into the details of failure rates, statistics, and comparisons - so stay tuned!

**Happy Testing Folks!**

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
