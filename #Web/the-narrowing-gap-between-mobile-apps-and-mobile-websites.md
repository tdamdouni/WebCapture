# The Narrowing Gap Between Mobile Apps and Mobile Websites

_Captured: 2017-12-11 at 20:22 from [dzone.com](https://dzone.com/articles/the-narrowing-gap-between-mobile-apps-and-mobile-w-1?edition=342127&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-11)_

[Download](https://dzone.com/go?i=242231&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17Q3-AST-Mobile-Testing-Reference-Guide_LP-Dzone.html) this comprehensive Mobile Testing Reference Guide to help prioritize which mobile devices and OSs to test against, brought to you in partnership with Sauce Labs.

Internet usage has [soared](http://gs.statcounter.com/press/mobile-and-tablet-internet-usage-exceeds-desktop-for-first-time-worldwide) on smartphones. Today, more than half of the internet is accessed through them. It's no surprise that smartphones have the lion's share of mobile data consumption, as well. Cisco [estimates](http://www.cisco.com/c/en/us/solutions/collateral/service-provider/visual-networking-index-vni/mobile-white-paper-c11-520862.html) that by 2021 mobile data traffic could be 5 times the present value. Smartphones would eclipse every other device by consuming 86% of that data. It's clear that future belongs to a smartphone. Smartphones will be the primary mode of accessing internet services by people.

Internet services are either provided as mobile websites or installable native apps on smartphones. Businesses choose either or both of them based on their requirements. The mobile websites are typically used for audience reach, while native apps are preferred for better user experience and driving engagement from existing customers.

Mobile websites and native apps both have inherent shortcomings and pose challenges for businesses around user acquisition and engagement. While the current technologies have come a long way, there is room for further innovation. Google has been at the forefront of this innovation and has been trying to push state of the art forward with [Progressive Web Apps](https://developers.google.com/web/progressive-web-apps/) (PWA) and [Instant Apps](https://developer.android.com/topic/instant-apps/index.html).

## Progressive Web App - The Evolved Website

In 2015, Google started working on PWAs. They wanted to incorporate app-like features into a website so that it looks, feels and functions like an app.

![](http://blog.devathon.com/content/images/2017/06/PWA_vs_Websites_compariosion_progressive_web_apps.jpg)

> _Good User Experience_

Mobile websites often have a sluggish feel. You must have suffered slow page loads, jittery videos, and janky scrolling or animations. Such experience frustrates users and negatively impacts business. Google [reports](https://www.doubleclickbygoogle.com/articles/mobile-speed-matters/) that 77% of websites are not mobile friendly. 53% of visits are abandoned if pages take longer than 3 seconds to load. This means more than half of the websites are never seen on smartphones.

On the other hand, PWAs are a pleasure to use. Scrolling is stick-to-finger fast, while animations and interactions are smooth as silk. It also loads faster than a mobile website. This is because on the first visit, the browser stores the app-like shell of a PWA. On repeat visits, only the content (kernel) needs to be loaded. While a website loads each page afresh, PWA loads only new contents of the shell. This mechanism gives PWAs a great advantage. Using the stored data, a PWA is able to load even when the internet connection is unreliable or absent. All this is achieved by

  * Avoiding unnecessary downloads,
  * Reducing the size of data that needs to be transferred
  * Using several compression techniques,
  * Leveraging caching whenever possible to eliminate redundant downloads,
  * Optimizing at every step in the entire rendering path that begins from browser receiving a code (HTML, CSS, Javascript) and processing them to turn them into rendered pixels on our screen.

Mobile websites open with all the browser elements whereas a PWA has more control over its appearance. Using a Web App Manifest file PWAs opens with an immersive full-screen experience without any browser elements. It can also display a custom loading page, change UI and set screen orientations.

Inactive users can be brought back using push notifications. They can be targeted to give a specific reminder or offer. Push notifications have been a popular way to engage users with native apps. Mobile websites have always lacked this feature. PWAs, however, support push notifications, providing a big boost to user engagement capability of websites.

Progressive Web Apps are installable and live on the user's home screen, without the need for an app store. Their icon on the home screen appears exactly like any other surrounding native app's icon. Presence of an icon simplifies and increases the usage.

Mobile websites cannot use all device features and hardware sensors like accelerometer, and GPS for location. PWAs, on the other hand, can leverage most common device features like location, motion events, and orientation events.

The Geolocation API available for PWAs lets you discover the user's location and track them (with consent). Like Instagram app you can geo-tag user-content for marking where a pic was taken, or like Uber app you can use this it for guiding a user to their destination, or like Nike+ app for tracking a running user.

Via device motion and orientation events, PWAs get access to the built-in accelerometer, gyroscope, and compass in the mobile devices. These events can be used for many purposes; in gaming, for example, to control the direction or action of a character. It can also be used to detect which side of the device is up and accordingly control app screen's orientation. You can build an app like Angry Birds on a PWA which lets the user control the direction or action of a character.

PWAs can even access camera and mic for capturing an image or recording an audio, but the experience varies with the browser. Depending on the browser, it might be a full dynamic and inline experience, or it could be delegated to another app on the user's device. However, all major browsers are expected to catch up eventually.

## Instant App - A Lightweight Version of an Android App

Introduced for Android in 2016, Instant Apps let you use any service of a Native app without downloading it. It is an idea of one app running in two different modes - Instant and Installable.

![](http://blog.devathon.com/content/images/2017/06/Instant_apps_Comparision_Android_native_apps.jpg)

Let's say we offer an airfare comparison service through a travel app. When users find this service they would click a link that opens the Play store. Users now need to first download and then install the travel app in order to compare the airfares. These steps ask for a lot of work from a visitor even before they can get any value from the product, resulting in a lot of them abandoning midway. A product manager at Google [estimates](http://blog.gaborcselle.com/2012/10/every-step-costs-you-20-of-users.html) that an app loses 20% of users at every step that the app asks them to do before it can deliver a solution to their problem.

Instant apps are designed to overcome this barrier to adoption. Their premise itself is to be an evolution in-app sharing and discovery. When such a link is clicked by a user who doesn't have the corresponding app already installed, the instant app version of the app will be instantly loaded by the play store and airfare comparison page of the app is accessed instantly. Thus all the download and installation steps are bypassed, resulting in instant delivery of value. The user can then be prompted to install the app for future use.

With Instant apps, users can share any service of an app with their friends who can instantly open them. Similarly, users searching online can click on a link from search results to access the app instantly. These users can savor the same beautiful and immersive app experience as an Android native app, but without having to download and install first.

An average user uses no more than 3-5 apps on a regular basis. Only around a thousand out of more than a million Android and iOS apps have more than 50,000 users. There is a reason for it. There are only so many apps that one uses repeatedly and regularly (like Facebook or Uber). All others serve one-off use cases. Users don't like to keep these apps on their phones because they consume space and data (because of frequent updates). When an app is not already on the phone, the friction for one-time use is very high and most users just tend to use a mobile website for it. Instant apps solve this problem. They don't need to be downloaded. You just click and you're using them.

Links to searches, social media, messaging, and other deep links can be pointed to open an Instant App. Such links that otherwise open a dull mobile webpage would now open a lively app.

Native apps need to be updated by downloading from the store, every time there is a new version. New versions are often released for rolling out new features and bug fixes. Users don't like frequent updates as they eat up precious data. App developers also have a tough time getting their entire user base to move to the latest version, especially when it includes an urgent bug fix or security update. Instant Apps, on the other hand, are accessed on demand via Google Play. This means that every user always gets served the latest version. This helps businesses provide the best experience always to their users, just like a website.

## Concluding Thoughts

Although being nascent technologies, interest for both PWAs and Instant apps is rapidly growing. PWAs have been available publicly since 2016 and have a relatively higher number of examples available for businesses to experience first hand. Instant apps were also first announced in 2016 but have become publicly available only in second half of May 2017. Early adopters of PWAs have reported encouraging results.

PWAs are currently fully supported by Chrome, Firefox, UC browser and Edge. Safari too has partial support for PWAs and for unsupported features, there are workarounds. So overall, a PWA is able to reach almost all of its intended audience. Instant Apps were originally supposed to run on Android 4.3 onwards, but are supported only 6.0 onwards as of now. However, this is set to change soon (support for Android 5.0 is expected to arrive soon). The upcoming Android O will add include further improvements to Instant Apps, including the ability to search for and launch Instant Apps from the launcher, as well as to add them to phone's home screen.

Despite being around for almost a decade, these are still exciting and promising times for smartphone apps. A lot will change in ways business think about acquiring and engaging users on smartphones, and also for how developers build these apps. Learn, unlearn and relearn.

Analysts agree that a mix of emulators/simulators and real devices are necessary to optimize your mobile app testing - learn more in this [white paper](https://dzone.com/go?i=242232&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17-ADV-EmuSimRealDevices-WP-LP-DZone.html), brought to you in partnership with Sauce Labs.
