# Android vs. iOS Development: Fight!

_Captured: 2015-12-24 at 17:40 from [techcrunch.com](http://techcrunch.com/2013/11/16/the-state-of-the-art/)_

![](https://tctechcrunch2011.files.wordpress.com/2013/11/duel21.jpg?w=738)

The eternal startup question "Android or iOS first?" grows ever thornier, with [news](http://techcrunch.com/2013/11/14/gartner-456m-phones-sold-in-q3-55-smartphone-android-at-82-share-samsung-a-flat-leader/) that Android's market share exceeds 80%. But never mind the managers and non-technical founders: what do _[developers! developers!](http://www.youtube.com/watch?v=8To-6VIJZRE)_ think of that divide? Whoever makes life easier for them gains a sizable edge.

And by "them" I mean "us." When not writing [TC columns](http://techcrunch.com/author/jon-evans/) (and [novels](http://rezendi.com/)) I'm a software engineer for [HappyFunCorp](http://www.happyfuncorp.com/), a consultancy with the best name (and web site-go on, click through) ever. To keep my hand in, as I find myself doing ever more management, I recently wrote and open-sourced a pair of more-or-less identical Android and iOS apps for a pet personal project. So let me use them to walk you through the state of the art.

Background: I've written numerous Android and iOS apps previously, both personally and professionally. These apps are native clients for my pet news aggregator, [Scanvine](http://www.scanvine.com/), which identifies stories being shared unusually widely across social media. Their complete source code is available on Github: ([Android](https://github.com/rezendi/scanvine-android) | [iOS](https://github.com/rezendi/scanvine-ios)) and the actual apps are available for download: ([Google Play](https://play.google.com/store/apps/details?id=com.scanvine.android) | [App Store](https://itunes.apple.com/app/scanvine/id717815889?mt=8).)

Before we begin, I would be remiss not to mention [Xamarin's cross-platform development tools](http://xamarin.com/). If I was fluent in C#, especially if I didn't already know Java and Objective-C, that would be my first choice for native app development.

Also, a disclaimer: this is more "fun code" than "production quality." You'll notice a stark lack of test code; I still need to track down an iOS heisenbug; I should be using git submodules rather than copy-pasted files for the third-party libraries; etc. (**_eta:_** ugh, and a rogue layout file slipped into the Android build which caused it to crash on tablets. Now fixed.)

Now, with no further ado, _let the battle commence!_

### Environment

You can still write code with text files and command lines, and many do, but it's _so_ much more productive to use an integrated development environment, or IDE.

Apple's is [Xcode](https://developer.apple.com/xcode/), which is, by and large, a joy to work with. It's slick, fast, powerful, helpful without being intrusive, and it keeps getting better at papering over both the unheimlich compilation machinery beneath its glossy exterior, and the complex and paranoid certificate/profile machinery which Apple imposes on developers to retain its titanium-fisted control over iOS apps and devices. The debugger works seamlessly, and the simulator is fast and responsive.

But Android? Oh, Android. The current state-of-the-art IDE is [Eclipse, customized with Android plugins](https://developer.android.com/tools/sdk/eclipse-adt.html), and it is _embarrassingly_ bad. Slow, clunky, counterintuitive when not outright baffling, poorly laid out, needlessly complex, it's just a mess. Its debugger is so clumsy that I find myself doing log-file debugging most of the time, whereas the XCode debugger is my iOS go-to bug-hunt tool. And the less said about the Android emulator, which takes _minutes_ to launch and then half the time fails to connect to the Android Debug Bridge, the better.

Now, to be fair, Google knows this is a problem, and they are working on a new [Android Studio](http://developer.android.com/sdk/installing/studio.html) IDE. Alas:

> Android Studio is currently available as an early access preview. Several features are either incomplete or not yet implemented and you may encounter bugs. If you are not comfortable using an unfinished product, you may want to instead download (or continue to use) the ADT Bundle (Eclipse with the ADT Plugin).

It's nice to see they're working on it, but it's amazing-in a bad way-that 4.5 years after I purchased my first Android phone, this mess is still the state of the art.

_Advantage:_ iOS, by a country mile.

### Configuration

As I mentioned, beneath the sleek, seamless exterior of Xcode and Objective-C lurk the Lovecraftian horrors of 1970s programming. I kid, I kid…but still. Macros and header files; projects, targets, schemes, and build configurations; an appallingly-intimidating list of build settings; the grim despair of encountering a baffling linker error; and [discoveries](http://stackoverflow.com/questions/6646052/how-can-i-disable-arc-for-a-single-file-in-a-project) like "oh, your third-party code doesn't support ARC? Just add the -fno-objc-arc flag! Simple, no?"

Android has a single manifest file and Eclipse builds your app in its entirety (usually) every time you save any file. I'd prefer more clarity in the error messages you get when your app isn't working because you haven't configured its permissions correctly, but that's a minor cavil. By and large, Android app configuration is simple and elegant.

_Advantage:_ Android.

### UX Design

You would expect Apple to walk off with this trophy. Its Interface Builder is a very sleek way to put simple good-looking user interfaces together quickly. The trouble is, the more I've actually used Interface Builder, the less I've liked it. It's another layer of configuration complexity; it's excellent for simple things, but as time goes by and apps evolve, those simple things tend to get complex and messy; and I _really_ don't like the multi-screen Storyboards Apple added about a year ago.

While Android theoretically has a comparable visual tool, the less said about it the better. In practice you wind up writing [XML files](https://github.com/rezendi/scanvine-android/tree/master/res/layout) which provide layout guidelines, as opposed to rules, so that apps are rendered (hopefully) well on the entire vast panoply of devices and screen sizes out there. (Apple's [Auto Layout](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/Introduction/Introduction.html) moves in the same direction, with an eye towards a larger variety of iOS screens in the future, no doubt.) Meanwhile, Android provides an [icon pack](http://developer.android.com/design/downloads/index.html) for developers to use, whereas iOS developers have to go with third parties like [Icons8](http://icons8.com/), or roll their own.

Overall it's a closer contest than you'd think, although I concede that this is pretty idiosyncratic. In the end two things give iOS the edge. First, it's still much simpler: three screen sizes (including iPad) and two screen densities, as opposed to the mass of complexity which is Android. Second, the default iOS visual elements -- eg popup menus and messages - are so much more visually attractive than Android's.

_Advantage:_ iOS.

### Language

Android apps are written in Java; iOS apps in Objective-C. There are exceptions - there's Xamarin, again; there are various other native-app fringe cases; and there are native/web hybrids like PhoneGap -- but in general, native Android apps are written in Java and native iOS apps in Objective-C.

I cut my programming teeth on Java, and didn't think much of Objective-C at first, in large part because of its excessive verbosity: a line like

_String s2 = s1.replace("abc","xyz");_

becomes

_NSString *s2 = [s1 stringByReplacingOccurrencesOfString:@"abc" withString:@"xyz"];_

but I've grown very fond of Objective-C. It's just better and cleaner than Java. It has [blocks](http://en.wikipedia.org/wiki/Block_%28programming%29): Java does not. It has [categories](https://developer.apple.com/library/ios/documentation/cocoa/conceptual/ProgrammingWithObjectiveC/CustomizingExistingClasses/CustomizingExistingClasses.html); Java does not. It does not require you to wrap much of your code with vast swathes of boilerplate try/catch exception-handling whitespace: Java does.

Java has its advantages. Better stack traces, for one thing, which means tracking down sporadic bugs tends to be a lot easier. And until a couple of years ago Android had the huge advantage of garbage collection. But now that iOS has [automatic reference counting](https://developer.apple.com/Library/ios/releasenotes/ObjectiveC/RN-TransitioningToARC/Introduction/Introduction.html), that advantage has mostly vanished (although old third-party tools often don't work with ARC, which means you have to do some XCode configuration voodoo to switch it off on a file-by-file basis.) With that distinction gone, the winner here is clear.

_Advantage:_ iOS.

### APIs

Both Android and iOS make an enormous library of software available to their developers, and, broadly speaking, those libraries are fairly similar: there are APIs for phone functions and features, network access functions, a panoply of View objects including a powerful WebView which essentially functions as a full-fledged browser. Most of the work, meanwhile, is done in controllers: very roughly, an iOS ViewController is equivalent to an Android Activity.

What iOS has which Android doesn't is an extra set of frameworks and features -- there's no real Android equivalent to iOS's powerful Core Data framework, for instance -- and a generally cleaner, better designed system. Compare [these](https://github.com/rezendi/scanvine-ios/blob/master/SVMasterViewController.m) [two](https://github.com/rezendi/scanvine-ios/blob/master/SVStoryTableViewCell.m) relatively simple iOS classes, for instance, which really do the bulk of all the work in the app, with [these](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/ui/StoryListActivity.java) [three](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/ui/StoryListFragment.java) [equivalent](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/ui/StoryArrayAdapter.java) Android classes, which between them include a half-dozen more inner or anonymous classes. At the end of the day I'd just much rather work with an iOS [CollectionViewController](https://github.com/rezendi/scanvine-ios/blob/master/SVMasterViewController.m) than an Android [ListAdapter](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/ui/StoryArrayAdapter.java).

Another metric, albeit a flawed one: lines of code. These apps are very nearly functional identical, but the iOS one has 1596 lines of custom code, including header files, compared to 2109 lines of Java code and XML for Android. That's a full 32% more.

_Advantage:_ iOS.

### Internet

These days many-to-most apps are conduits to Internet APIs more than they're standalone programs; this is important enough that it's worth looking at separately. Both iOS and Android provide a panoply of tools and APIs for this. They also both provide very similar WebViews, which are basically full-fledged browser windows that you can plug into your app anywhere.

Network connections basically have to run in the background, so as not to block the main thread of the app, and multithreading is hard. Android provides an [AsyncTask](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/ui/StoryListFragment.java#L166) class for things like this, which is verbose but works well, and a [very easy way](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/util/Util.java#L29) to determine whether you're currently online. iOS provides equivalent facilities, but they're all pretty low-level and unsatisfying.

However, there are a host of open-source libraries that make life much easier. I used AFNetworking, which is as delightful as advertised. You simply pass it blocks of code to run when web requests are complete -- which isn't possible in Android, because Java doesn't do blocks.

_Advantage:_ Android natively, but iOS when third-party libraries are considered.

### Sharing

How easy is it to share something from your app to Facebook, Twitter, Evernote, etc? I had thought this would be a first-round knockout for Android, which has long had a powerful inter-app communications system called Intents. And in general Android is still much better at letting apps call and share data with one another.

In the (perhaps unfortunately) much more common case of sharing, though, Apple has caught up considerably. Don't take my word for it, judge for yourself. The Android code to share a Scanvine story is [here](https://github.com/rezendi/scanvine-android/blob/master/src/com/scanvine/android/ui/StoryArrayAdapter.java#L133), and the iOS code [here](https://github.com/rezendi/scanvine-ios/blob/master/SVStoryTableViewCell.m#L192). The only reason the iOS code is longer is because I do a little more Google Analytics tracking there than on the Android side (which I should fix.)

_Advantage:_ Neither.

### Fragmentation

No need to spend much time on this one. [Android](http://developer.android.com/about/dashboards/index.html). [iOS](http://techcrunch.com/2013/10/22/200-million-devices-running-ios-7-five-days-after-launch-64-of-all-idevices-20-million-itunes-radio-listeners/). QED. Though it's worth noting that Google is implementing an [interesting defragmentation strategy](http://arstechnica.com/gadgets/2013/09/balky-carriers-and-slow-oems-step-aside-google-is-defragging-android/), so this may be worth revisiting soon enough.

_Advantage:_ iOS.

### Publication

Publishing an Android app is easy as a dream. Just sign your app via a handy Eclipse wizard, and poof, you have an APK file that can run on any device. Email it, put it up on a web site, or upload it to Google Play and make it available worldwide (probably) within the hour. Could hardly be simpler. Check install statistics and crash reports, including stack traces which (usually) identify the individual line of code that went wrong, at your leisure, and you can upload a bug-fix version immediately.

Publishing an Apple app is a nightmare. A brilliant friend of mine always advises people to add at least a day to their iOS development schedule _just_ to wrestle with certificates and distribution profiles. No matter how many times I do it, or how easy the latest version of XCode tries to make it, it's _always_ a giant hassle. And testing would be even _worse_ if not for TestFlight. And Apple's "iTunes Connect" web site is to Google Play Developer Console as a Ford Pinto is to a Tesla. Good luck getting any crash reports at all, much less useful information from them; have fun jumping through their arbitrary hoops; and marvel at just how bad mighty Apple's UX can be.

_Advantage:_ Android, by a long shot.

### And The Winner Is…

iOS, and by some distance. Android has its advantages, but overall, it remains significantly easier to write good iOS apps than good Android apps. Combine that with the fact that iOS users tend to be wealthier-and arguably more influential-and it still makes sense for most startups who want to make a splash to go iOS-first, Android-later. The new Android Studio IDE could conceivably close some of that gap…but not all of it.

(For the record, my own primary phone is a Nexus 4, and I'm very happy with it.)

_Image credit:_ Jennifer Stolzer, [DeviantArt](http://jameson9101322.deviantart.com/art/An-Epic-Duel-for-the-Ages-SPG-347196439).
