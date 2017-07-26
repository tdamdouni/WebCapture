# What is a WebView?

_Captured: 2017-04-20 at 17:59 from [developer.telerik.com](http://developer.telerik.com/featured/what-is-a-webview/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)_

![](http://developer.telerik.com/wp-content/uploads/2015/11/what_webview_header.jpg)

Every hybrid mobile app developer has that moment. You know the one I'm talking about, when someone asks you, "So what kind of mobile apps do you develop?" Depending on context, a follow-up question might be, "Well, are you developing these apps natively?" meaning, using native languages like Swift, Objective-C, and Java. Bravely, you might respond, "Nope. My apps are all hybrid mobile" …and get ready for the blank stare. Taking a deep breath, you launch into an explanation about what a hybrid mobile app is, and how it presents its content in a WebView. Prepare now for the mother of all questions: "Well, what's that?"

![Lucy](http://developer.telerik.com/wp-content/uploads/2015/11/169189__splain-lucy_p.jpg)

> _'Splain this! - image source_

This article is an attempt on my part to save you some hand-wringing moments the next time you get cornered into a discussion of development architecture. Let's tackle this question, "What is a WebView?". We'll start by defining what WebViews are, why we care about them, how they allow developers to use web technologies to build mobile apps, and then take a look at the types of WebViews.

## WebViews. Why do we even?

Honestly, it seems weird - this idea that we build a mobile app using web technologies and present the whole thing in a WebView. It feels a bit like smashing a whole site into an iframe.

![webviews](http://developer.telerik.com/wp-content/uploads/2015/11/2685181.jpg)

But the key to the weirdness is that developers can reuse the web technologies they know and love to spin up a mobile app. This is conducive to code reuse - the philosophy of write once, run anywhere.

You build with web technologies, add a bridge to native technologies via tools like [Cordova](https://cordova.apache.org/), and just like that, you have a mobile app fit for the app marketplaces! In fact, WebViews can even drive desktop apps using tools like [Electron](http://electron.atom.io/).

It seems so simple. A mini web browser, e.g. a WebView, runs your app, but you can make use of native APIs.

If you have web skills but want to reach a platform on which you have little experience--iOS, Android, Windows, OS X, or Linux--using a WebView is often a compelling option. And it doesn't have to be slow and clunky! Done right, hybrid mobile apps can often perform quite well. The Untappd app is a great example of a well-built hybrid mobile app.

![untappd](http://developer.telerik.com/wp-content/uploads/2015/11/untappd.jpeg)

_[Untappd](http://www.untappd.com), a great example of a hybrid mobile app, uses [plugins](http://developer.telerik.com/featured/native-or-hybrid-the-path-of-least-resistance/) to enhance its slick, native feel._

## Anatomy of a WebView

In his [article on hybrid mobile apps](http://developer.telerik.com/featured/what-is-a-hybrid-mobile-app/), John Bristowe identifies a WebView as a "chromeless browser window that's typically configured to run fullscreen." The basic architecture can be understood in this infographic, comparing native, hybrid, and web apps:

![hybrid native web](http://developer.telerik.com/wp-content/uploads/2015/11/hybrid-native-web.png)

> _courtesy of myShadesOfGray_

> There are many different names for what is essentially a minimal browser that delivers web content. In this article, I will use the term WebView to cover the chromeless browser window referenced above. There are several different types of WebViews available for different platforms which I discuss below.

If a WebView, then, is not much more than an iframe or a tab in a browser, how is it leveraged by mobile apps to support native capabilities like the ability to take a picture using the device's camera?

This question can be answered by looking at the frameworks that utilize WebViews to present content. The best-known framework, Apache Cordova, embeds HTML5 code inside a WebView and then provides a "[foreign function interface](https://en.wikipedia.org/wiki/Foreign_function_interface)" (FFI), or a "native bridge", to access the native resources on the device. Thus, a developer using a Cordova-friendly framework such as [Kendo UI Mobile](http://demos.telerik.com/kendo-ui/) could write a few lines of code to leverage a native camera in a cross-platform-friendly fashion:
    
    
    function capturePhoto() {
        // Take picture using device camera and retrieve image as base64-encoded string
        navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 50,
            destinationType: destinationType.DATA_URL });
    }

If you were to invoke this method on a button click, the camera would open on either an iOS or Android device, based on how the framework forms a bridge between the WebView with which the user interacts, and the FFI bridge itself that allows code to be interpreted by a native system.

> Fun Fact: Cordova has been described as having evolved from a [hack](http://www.i-programmer.info/news/83-mobliephone/3133-phonegap-making-changes.html) that enabled a Foreign Function Interface to an embedded WebView on iOS.

Although all hybrid mobile app frameworks by definition rely on standard implementations of WebViews for the app presentation tier, there are many differences in the types of WebViews available to us, depending on the framework we choose to use. Let's take a look at some of these.

## The Need for Speed

Building a mobile app using layers of technology above the native API inevitably involves some sacrifice of performance. A clever developer can often minimize this performance hit, but frameworks like to promise more.

For example, Trigger.io boasts a [super-fast native bridge](http://trigger.io/cross-platform-application-development-blog/2012/02/24/why-trigger-io-doesnt-use-phonegap-5x-faster-native-bridge/) ("5x faster than PhoneGap!"). Cocoon.js goes farther, offering a [faster experience](https://www.ludei.com/landing/cocoonjs-phonegap/) based on both the use of Canvas+ (which allows avoidance of using WebView at all) and WebView+, a faster implementation of the native WebView.

Ludei, the makers of Cocoon.js, deplore the use of the native WebView:

> The system webview is a native component provided by the operating system to be able to load web content. Webviews are a great tool provided by both desktop and mobile operating systems…but they have some problems.

Specifically, Ludei says, the problems are performance and fragmentation - so they decided to roll their own.

As a native element, the WebView is tied to the native OS, so maintaining a performant ecosystem that can take advantage of hardware speed increases as well as advances in WebView technologies _while also_ taking into account the limitations of older devices and fragmented ecosystems (I'm looking at you, Android) is a big challenge.

As the mobile device ecosystem has evolved, so has the WebView. Let's take a look at how the WebView has changed over the past few years based on its use across the ever-changing mobile landscape.

## Types of WebViews

For the purpose of this article, I'd like to concentrate on the interesting history of both the iOS and Android WebView, which have evolved considerably recently, before discussing the brave new world of the desktop WebView.

### The iOS WebViews: UIWebView and WKWebView

Since [Apple made the decision](http://www.theregister.co.uk/2011/03/15/apple_ios_throttles_web_apps_on_home_screen/) not to have mobile apps run in Safari's mobile browser, [UIWebView](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIWebView_Class/index.html) was leveraged instead. This has had far-reaching implications for hybrid mobile apps on iOS.

As Mattt Thompson [noted](http://nshipster.com/wkwebkit/):

> UIWebView is massive and clunky and leaks memory. It lags behind Mobile Safari, which has the benefit of the Nitro JavaScript engine.

The lack of the speedier [JavaScript engine](http://developer.telerik.com/featured/a-guide-to-javascript-engines-for-idiots/) helped spur the perception of apps running in this environment as glitchy, laggy, and slower than their native counterparts.

With the introduction of iOS 8, however, developers [celebrated the arrival](http://developer.telerik.com/featured/why-ios-8s-wkwebview-is-a-big-deal-for-hybrid-development/) of [WKWebView](https://developer.apple.com/library/prerelease/ios/documentation/WebKit/Reference/WKWebView_Ref/index.html).

> WKWebView is the centerpiece of the modern WebKit API introduced in iOS 8 & OS X Yosemite. It replaces UIWebView in UIKit and WebView in AppKit, offering a consistent API across the two platforms. - [NSHipster](http://nshipster.com/wkwebkit/)

Along with several [performance enhancements](http://developer.telerik.com/featured/using-ios-8-wkwebview-telerik-appbuilder/), including 60fps scrolling and built-in gesture support, WKWebView includes the same JavaScript engine as Safari, a huge improvement over the slower UIWebView.

> #### Why no Nitro?
> 
> While it seems like Apple was deliberately plotting to slow down UIWebView and the web apps that run in it, [John Gruber](http://daringfireball.net/2011/03/nitro_ios_43) noted in 2011 that Apple was primarily interested in maintaining the security of apps running on its systems. Nitro uses JIT (Just-In-Time) compilation, but since "JIT requires the ability to mark memory pages in RAM as executable", Apple, as a security measure, does not allow this. WKWebView makes use of [improved inter-application communication APIs](http://daringfireball.net/linked/2014/06/09/ios-8-webkit). WKWebView now allows third-party plugins to run JavaScript on separate sandboxed processes _outside_ the application. This ability eases Apple's security concerns regarding third parties using JIT compilation.

A handy comparison table of the UIWebView and WKWebView components is available [here](http://nshipster.com/wkwebkit/) in which you can see the increase in capability of WKWebView over UIWebView.

The [WKWebView Cordova plugin](http://plugins.telerik.com/cordova/plugin/wkwebview) for iOS apps in Telerik's curated plugin marketplace offers a handy drop-in way for your iOS apps to consistently use WKWebView in a hybrid mobile app, irrespective of the device on which the user interacts with the app. This plugin promises to solve backward compatibility issues, although there are [several caveats](http://plugins.telerik.com/cordova/plugin/wkwebview) about the compatibility of this plugin with others.

### The Android WebViews

On Android devices, unsurprisingly (given the [vast array of devices that run Android OS](http://opensignal.com/reports/2015/08/android-fragmentation/)), the situation is more fragmented than on iOS. TJ VanToll gives a [good explanation](http://developer.telerik.com/featured/android-5-0s-auto-updating-webview-means-mobile-apps/) of the situation on Android.

Whereas earlier versions of the Android OS relied on the WebKit rendering engine to power its WebView, as of Android 4.4, various versions of Chromium are implemented. Typically, with each consecutive update of Android's OS, a new version of Chromium would also be included, thereby giving access to the new rendering engine's capability. This clearly causes issues in backward compatibility for developers who must support earlier versions of Android.

To combat this particular problem, as of Android 5.0, the concept of the 'auto-updating' WebView has been introduced. Instead of the WebView version and capabilities depending on Android OS's update cycle, the Android 5.0 WebView is a "system-level .apk" available in Google Play that can update itself in the background.

> So cool to see the Android System WebView updating outside of an Android release. [pic.twitter.com/qBogbej96T](http://t.co/qBogbej96T)
> 
> -- TJ VanToll (@tjvantoll) [March 12, 2015](https://twitter.com/tjvantoll/status/576028963409104896)

Of course, having access to the auto-updating WebView hinges up on Android users' adoption of Android 5.0. It remains to be seen how quickly this can occur.

#### The Special Case of Crosswalk

Like Android's auto-updating system, Intel's [Crosswalk project](https://crosswalk-project.org/documentation/getting_started.html) aims to bridge the gaps between old devices using old OSs and clunky WebViews and their newer counterparts. Crosswalk "enables you to deploy a web application with its own dedicated runtime", so you are not dependent on a third-party or platform-dependent WebView. Rather, _you_ are in the driver's seat, and control the WebView in use by your app.

![tokyo crosswalks](http://developer.telerik.com/wp-content/uploads/2015/11/tokyo-crosswalks-019.jpg)

> _Cross with care! Image courtesy of Candy Chang_

The Crosswalk project itself is tied to [Blink](http://www.chromium.org/blink), Chromium's rendering engine, and its updates follow the release cycle of Blink. While its use is particularly helpful for Android versions 4.0 and above, it can also be used for iOS, Linux desktop, and Tizen. On Android, Crosswalk uses Chromium and on iOS it relies on WKWebView, but cross-platform developers can relax, as they can use a unified API to support most use cases. A Cordova [plugin for Crosswalk](http://plugins.telerik.com/cordova/plugin/crosswalk) uses the Chromium 45 browser rendering engine uniformly for quick implementation into your hybrid mobile project targeting Android devices.

### Other WebViews

Up to this point, I have restricted my discussion of WebViews to those of most interest to hybrid mobile app developers. However, WebViews are everywhere! Let's take a quick look at some work on WebViews that aim to replace the old in-app browsers, and then check out what's going on on the desktop.

#### Other Mobile WebViews

On occasion, there's a need to an in-app browser option to open from within a mobile app, and both Apple and Google have a few options for developers:

  * **Safari View Controllers**  
In its quest to stop developers from creating fragmentation by developing custom mini-browsers to run in-app browser content on iOS, Apple has introduced the [Safari View Controller](https://www.macstories.net/stories/ios-9-and-safari-view-controller-the-future-of-web-views/) in iOS9, which is a "sandboxed" version of Safari. It gives the developer a standardized environment in which to present content, while offering the user a consistent experience and several convenient security helpers that allow users, for example, to log in to a View Controller and stay logged in when visiting a related site in mobile Safari by means of shared cookies and shared login credentials. These snack-sized app views allow for a consistent in-app deep-linking experience for the iOS user.
![view controllers](http://developer.telerik.com/wp-content/uploads/2015/11/vc.jpg)

> _Safari View Controllers, image courtesy of MacRumors_

  * **Chrome Custom Tabs**  
The Android counterpart to Safari View Controllers is [Chrome Custom Tabs](https://developer.chrome.com/multidevice/android/customtabs). It allows developers to create a custom browser experience within the parameters of Android's developer guidelines. They are available to all devices that can run Chrome 45 on Android 4.1+ (Jellybean). Many goodies are included in this custom WebView, including "pre-warming" of the browser in the background "while avoiding stealing resources from the application," shared cookies and permissions, and one-tap return to the app. In addition, it allows Android developers to serve content in a faster manner to users who are navigating on devices that do not have auto-updating WebViews instead of falling back on an older, slower WebView.
![chrome custom tab](http://developer.telerik.com/wp-content/uploads/2015/11/cct.jpg)

> _An example of a Chrome Custom Tab. Note the minimal browser chrome_

#### WebViews on the Desktop

You can find WebViews on the desktop as well, and you might not even realize that you're using one. Slack is a great example of one of these. The user experience is both speedy and well-contained:

![slack](http://developer.telerik.com/wp-content/uploads/2015/11/slack.png)

> _The productivity phenomenon that is Slack. Image courtesy of MetaLab_

  * **NW.js**  
An interesting project created at the Intel Open Source Technology Center (thanks, Intel!) is [NW.js](https://github.com/nwjs/nw.js), previously known as Node-webkit, which is an app runtime based on Chromium. It allows the developer to call Node.js modules directly from the DOM. Desktop applications are written using this library and are presented as a chromeless browser standalone, easily packaged and distributed with all the firepower of Node.js. A great use case for this library would be HTML5 [desktop games](https://speakerdeck.com/zcbenz/node-webkit-app-runtime-based-on-chromium-and-node-dot-js).
  * **Electron**  
Perhaps better-known than NW.js, Github's [Electron](http://electron.atom.io/) is another framework to help you build [desktop apps](http://developer.telerik.com/featured/desktop-apps-with-electron-and-kendo-ui/). The project was originally called Atom Shell as it was the basis for GitHub's desktop [Atom editor](https://atom.io/). Companies such as Slack, Particle, and Microsoft have used Electron to build great desktop apps such as Visual Studio Code and the Slack client. A good discussion of the differences between NW.js and Electron can be found [here](http://electron.atom.io/docs/v0.34.0/development/atom-shell-vs-node-webkit/)

## WebViews. Know them, love them

![I love WebViews](http://developer.telerik.com/wp-content/uploads/2015/11/ill.jpg)

_Image courtesy of the [I Love Lucy wiki](http://ilovelucyandricky.wikia.com/wiki/I_Love_Lucy_Wiki)_

If you are in the business of presenting web content on a mobile device and/or on a desktop, it behooves you to embrace the wild and crazy world of the WebView. It's a world that is constantly evolving, influenced by vendors' real and perceived security requirements and by advances in both hardware and software. The WebView lands squarely in the middle of the developer's toolkit, providing a way to get your awesome app content in front of your users in an efficient way…assuming its quirks are well understood by a knowledgeable front-end developer.

Plus WebViews can provide at least 1/2 hour of solid conversation at any given party.

_With thanks to TJ VanToll and Cody Lindley for their valuable feedback on this article!_

_Header image courtesy of [Mark Klotz](https://flic.kr/p/oVv6W4)_

[Jen Looper](http://developer.telerik.com/author/jlooper/)  
Jen Looper is a Developer Advocate at Telerik with over 15 years' experience as a software developer. She is a web and mobile developer and founder of [Ladeez First Media](http://LadeezFirstMedia.com) , specializing in creating cross-platform educational and fitness-oriented mobile apps. She's a multilingual multiculturalist with a passion for hardware hacking and learning new things every day.
