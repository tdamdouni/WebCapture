# iOS Apps Caught Using Private APIs

_Captured: 2015-10-23 at 15:20 from [sourcedna.com](https://sourcedna.com/blog/20151018/ios-apps-using-private-apis.html)_

We've found hundreds of apps in the App Store that extract personally identifiable user information via private APIs that Apple has forbidden them from calling. This is the first time we've seen iOS apps successfully bypass the app review process. But, based on what we learned, it might not be the last.

We found these apps while adding support to [Searchlight](https://searchlight.sourcedna.com) to scan for private API usage. This is something that will get your app rejected by app review, so we want to alert our users to this problem before it costs them time, especially when they're trying to get a critical update out.

iOS binaries contain ARM machine code that our system disassembles. When you make a call to an Objective-C method, it is vectored through `objc_msgSend`, which receives the class and method names as strings. In nearly all cases, these strings can be statically resolved in the disassembly by looking at data references prior to the call to `objc_msgSend`. We already track the origin and destination class/method of these calls to build a callgraph for each app in order to find which methods are in use.

However, in some cases, these parameters can't be statically resolved. Since they're just strings, they can be created at runtime by any string manipulation routines. Some tools take advantage of this capability to obfuscate the names of classes and methods, descrambling the strings right before calling `objc_msgSend`.

An app can also call `dlopen` to load a new library and then `dlsym` to get access to a function or data member in it. This causes the dynamic linker to map in the named file (first checking its code signature) and then look up the address to the given symbol. The library and symbol names are both strings, and thus can also be created at runtime.

SourceDNA disassembles and indexes the behavior of code in millions of apps. To determine if runtime library loading was being used to access private APIs, we searched our collection for ones that match this pattern:

  1. Calls `dlopen`/`dlsym` or `NSClassFromString`/`NSSelectorFromString`
  2. Generates the parameters via one of the various string manipulation functions

This found hundreds of matching calls, using `sprintf` with `%s` format strings and `%@` with `NSString stringWithFormat:`. We wrote a script to expand these format strings using nearby static strings and then clustered the reconstructed parameters.

We found four main groups of private APIs these apps are calling:

  1. Enumerate the list of installed apps or get the frontmost app name
  2. Get the platform serial number
  3. Enumerate devices and get serial numbers of peripherals
  4. Get the user's AppleID (email)

Since we also identify SDKs by their binary signatures, we noticed that these functions were all part of a common codebase, the [Youmi](http://youmi.net) advertising SDK from China.

We then associated the clusters of this SDK's code with the release dates of the apps that contain them to see how it has evolved over time. The older versions do not call private APIs, so the 142 apps that have them are ok. But almost two years ago, we believe the Youmi developers began experimenting with obfuscating a call to [get the frontmost app name](http://stackoverflow.com/questions/25926026/how-to-monitoring-app-running-in-the-foreground-in-ios8-use-the-privateframework).

Once they were able to get this through App Review, they probably became more confident they weren't being detected and added the above behaviors in order. They also use the same obfuscation to hide calls to retrieve the [advertising ID](http://techcrunch.com/2014/02/03/apples-latest-crackdown-apps-pulling-the-advertising-identifier-but-not-showing-ads-are-being-rejected-from-app-store/), which is allowable for tracking ad clicks, but they may be using it for other purposes since they went to the trouble to obfuscate this. The latest version of the Youmi SDK (v5.3.0), published a month ago, still gathers all the above information.

Apple has been locking down private APIs, including blocking apps from reading the platform serial number in iOS 8. Youmi worked around this by enumerating peripheral devices, such as the battery system, and sending _those_ serial numbers as a hardware identifier.

[Find out now!](https://searchlight.sourcedna.com) Just select your developer accounts from a list, and we'll tell you what we found about your apps. We'll also show the commercial and open-source code you're using and alert you to future issues we find.

We found 256 apps (est. total of 1 million downloads) that have one of the versions of Youmi that violates user privacy. Most of the developers are located in China. We believe the developers of these apps aren't aware of this since the SDK is delivered in binary form, obfuscated, and user info is uploaded to Youmi's server, not the app's. We recommend developers stop using this SDK until this code is removed.

Another research report was published last week titled "[iRiS: Vetting Private API Abuse in iOS Applications](http://dl.acm.org/citation.cfm?id=2813675)". The authors built an excellent system that selectively applies dynamic analysis to static call sites that can't be resolved. Credit where credit is due - they found these same patterns in apps before us and correctly attributed it to the Youmi SDK, albeit using a different approach and apps.

Given how simple this obfuscation is and how long the apps have been available that have it, we're concerned other published apps may be using different but related approaches to hide their malicious behavior. We're continuing to add new features to our engine to discover anomalous behavior in app code and find out if this is the case.

We notified our [Searchlight](https://searchlight.sourcedna.com) customers about this problem to help them address it and then sent a list of affected apps to Apple. Developers need to be aware that when they install an SDK in their app, they're responsible for how it affects their users. This is difficult for binary code (especially if it's obfuscated), so we'll keep providing transparency to help them make informed decisions about the code they use.

Update: Apple has issued the following statement.

> "We've identified a group of apps that are using a third-party advertising SDK, developed by Youmi, a mobile advertising provider, that uses private APIs to gather private information, such as user email addresses and device identifiers, and route data to its company server. This is a violation of our security and privacy guidelines. The apps using Youmi's SDK have been removed from the App Store and any new apps submitted to the App Store using this SDK will be rejected. We are working closely with developers to help them get updated versions of their apps that are safe for customers and in compliance with our guidelines back in the App Store quickly."
