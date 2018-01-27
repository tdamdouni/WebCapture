# How to Make Your Website Mobile-Friendly

_Captured: 2017-10-05 at 15:48 from [dzone.com](https://dzone.com/articles/how-to-make-your-website-mobile-friendly?edition=329520&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202017-10-05)_

[Download](https://dzone.com/go?i=242231&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17Q3-AST-Mobile-Testing-Reference-Guide_LP-Dzone.html) this comprehensive Mobile Testing Reference Guide to help prioritize which mobile devices and OSs to test against, brought to you in partnership with Sauce Labs.

It's a no-brainer to optimize your website to be mobile-friendly. [As of 2016](https://www.thinkwithgoogle.com/advertising-channels/mobile/device-use-marketer-tips/), 80 percent of Americans own a smartphone of some kind, and 27 percent of people only use a smartphone in an average day (which is 2 times as many as those who only use a computer), while 57 percent use more than one device. We spend almost three hours a day on mobile devices, and 94 percent of mobile users browse the web on an average day.

However, though the idea of mobile-first is surely tempting, there are many methods of taking your site to the mobile web. Deciding which direction you go will determine associated costs and maintenance as well as ROI, and some options may be better for certain time allowances, skill sets, budgets, and business goals than others.

## Designing for the Mobile-Friendly Web

### Web and Mobile Versions

Quite a few big name sites still have two versions of their website - mobile and desktop. You can usually tell a site has two versions because accessing it on your phone will have an "m." in front of the normal URL.

The problem developers have found with two different site versions is that upkeep and maintenance get tricky because having two separate designs means that any time that code needs to be changed, it needs to be integrated differently and tested separately on each one.

Not only will two websites prove to make things difficult for teams who want to be continuously integrating features, but it's also not an adaptable strategy for an evolving technological environment. When you consider the ways today's consumers access the internet, there are all kinds of variables that affect how they'll see the web as [smartphones continue to get bigger and tablets continue to get smaller](https://500ish.com/the-ipad-mini-mini-the-iphone-plus-plus-99fa2087b07f).

By definition, having only a web and mobile-friendly version means leaving out a plethora of devices, browsers, and screen sizes. Only having two versions of a website doesn't account for the fact there are more than two screen sizes users will look at it on. As web options continue to become more [plentiful and more fragmented](https://crossbrowsertesting.com/blog/mobile-devices/android-fragmentation-web-app-quality/), having two rigid site structures may not be the best way to safeguard your site for the future.

### Native Mobile Apps

A native app is probably what first comes to mind when you think of an app - the icon you can download from your smartphone's app store that sits on your display screen and opens with a tap.

The pro of native mobile apps? Push notifications, or the little alerts that pop up on your phone screen to let you know you've been tagged in a picture or someone "liked" your status. Push notifications are a great way to keep users engaged and draw them back to the app. In fact, [one study](http://info.localytics.com/blog/push-messaging-drives-88-more-app-launches-for-users-who-opt-in) found that apps that utilize push notification achieve up to three times more retention, and users are three times more likely to reopen an app with push notifications than a website.

The biggest con of native mobile apps? Taking up phone space and memory. Smartphones are so expensive today that people will often end up picking the device with the least amount of memory in order to save some cash. While 32GB seems like a lot of room, it fills up quickly with media, messages, and must-have apps. Most [people aren't downloading _any_ new apps](https://techcrunch.com/2017/08/25/majority-of-u-s-consumers-still-download-zero-apps-per-month-says-comscore/?ncid=rss) on a montly basis. But even if you convince people to download your app, the more time goes by, the more chance they're going to delete it to free up space for pictures of their kids or cats.

[Another study](http://blog.gaborcselle.com/2012/10/every-step-costs-you-20-of-users.html) actually found that every step you make a user perform on a native app increases the chance they will delete it by 20 percent. By the time they find it in the app store, download it, open the app, and sign up, only about 40 percent of original users remain, and it just goes down from there. In the end, if you can't convince users that they need your app on a regular basis, it's likely to go the way of Angry Birds and Temple Run.

Additionally, native apps are designed for a specific operating system. This means iPhone and Android apps must be created separately from each other - an app made for iOS can not work on an Android phone and vice versa. Similar to having two different websites, this means designing and maintaining two different native apps.

### Hybrid App

Hybrid apps, as you can likely tell by the name, combine some similarities of both native and web apps. A hybrid app uses a native container (which means it looks like a native app) and a web app's web code (HTML, CSS, and Javascript) for what some consider the best of both worlds since it's quicker, cheaper, and easier to build than native apps.

To clarify, this means that while a hybrid app mimics a native app since you have to download it from an app store, but it's built like a web app, which means it performs a little more like a website in a browser. Additionally, physical device features that could previously only be accessed through a native app like camera and microphone can be also utilized in a hybrid app.

### Progressive Web App

Progressive web apps are fast loading, cross-browser compatible, and can even work offline, making them increasingly popular among mobile developers. In fact, a progressive web app is basically just a website that performs more like a native app on mobile devices, which a lot of people find contributes to better usability.

Since it can be accessed via the browser, it skips the step of finding and installing an application from the app store, which in turn takes out the associated risk of it being deleted. Even though it's in the browser, you can also find it on your home screen when saved as a shortcut so it's easy to get to with a tap. It should also work on any device, regardless of OS, making testing a lot easier than for other kinds of applications since it only has to be done on one platform.

Of course, if it was all that easy, everyone would be making progressive web apps, right? Unfortunately, with all these benefits comes high development costs and they are often much more complex to build, requiring specialized skills utilizing Service Workers and Web APIs.

### Responsive Web Design

Responsive design is the process of combining media queries, fluid grids, and flexible images to develop a website that adapts to any browser or device size. Though responsive design does require knowledge of these principles, once a website is made responsive it takes very little upkeep, allowing you to keep a single code for the entire website and thus only requiring you to integrate new features once.

Additionally, when done right, responsive design provides first-class usability for users on almost any device, from laptop to tablet to smartphone. This means that you could depend on one website to reach all potential users.

A few have attempted to argue that responsive design isn't worth the time, energy, or cost, but over and over again we see that a responsive site is one of the only ways to ensure a positive experience on any screen and thus ensure their user satisfaction and business (and most of the time you will see an angry mob of disagreement in the comment section of any [blog that does try to argue this](https://managewp.com/5-reasons-why-responsive-design-is-not-worth-it)).

Even if you do decide to splurge on a progressive web app or native app, responsive design should still remain a part of your main website to ensure different user environments are accounted for when accessing your web page through a browser.

### Combination

There's always the option to leverage more than one of these options. For example, some sites that go the route of having a set mobile-friendly and desktop versions will also have a native app.

This is frequently done to make up for a lack of user experience on the web app by encouraging them to download the native app for a better experience, but also allowing them the option to continue on the mobile web version.

While this may be strategic depending on who your users are, it can also be annoying for users to be pushed to download an app they don't want or forced to endure poor usability.

Again, you also want to keep in mind the more different applications you design, the more you have to maintain, which is a big reason why responsive design has become so popular in the coming years so developers only have to keep up with one version that works for everyone.

## Mobile Testing

Of course, all your development and design efforts with any of these mobile-friendly options will go to waste without an A-game testing strategy. By using an arsenal of [real devices](https://crossbrowsertesting.com/blog/manual-testing/emulators-simulators-real-devices-testing/) for testing, you can determine whether your app functions correctly and look goods regardless of device, screen size, OS, or browser.

Additionally, while testers have flocked to the likes of [Selenium](https://crossbrowsertesting.com/blog/selenium/intro-selenium-testing/) as an open source option for test automation on web applications, [Appium](https://crossbrowsertesting.com/blog/appium/appium-native-web-hybrid-applications/) has become the equivalent for [mobile testing](https://smartbear.com/learn/software-testing/what-is-mobile-testing/). This will further allow you to speed up testing no matter which method you choose when bringing your users to mobile.

Analysts agree that a mix of emulators/simulators and real devices are necessary to optimize your mobile app testing - learn more in this [white paper](https://dzone.com/go?i=242232&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17-ADV-EmuSimRealDevices-WP-LP-DZone.html), brought to you in partnership with Sauce Labs.
