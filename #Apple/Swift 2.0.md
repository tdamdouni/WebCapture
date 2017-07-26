# Swift 2.0

_Captured: 2015-09-26 at 02:20 from [developer.apple.com](https://developer.apple.com/swift/blog/?id=29)_

Today at WWDC, we announced Swift 2.0. This new version has even better performance, a new error handling API, and first-class support for availability checking. And platform APIs feel even more natural in Swift with enhancements to the Apple SDKs.

### Open Source

In addition to new features, the big news is that Apple will be making Swift open source later this year. We are all incredibly excited about this, and look forward to giving you a lot more information as the open source release gets nearer. Here is what we can tell you so far:

  * Swift source code will be released under an OSI-approved permissive license.
  * Contributions from the community will be accepted -- and encouraged.
  * At launch we intend to contribute ports for OS X, iOS, and Linux.
  * Source code will include the Swift compiler and standard library.
  * We think it would be amazing for Swift to be on all your favorite platforms.

We are excited about the opportunities an open source Swift creates for our industry. Baked-in safety features combined with excellent speed mean it has the chance to dramatically improve software versus using C-based languages. Swift is packed with modern features, it's fun to write, and we believe it will get used in a lot of places. Together, we have an exciting road ahead.

### New Features

Swift 2.0 also includes a lot of new language features and refinements. Expect to see blog posts exploring the features in more depth, and be sure to watch for the WWDC sessions covering these topics all this week. A few of the new features include:

**Error handling model: **The new error handling model in Swift 2.0 will instantly feel natural, with familiar try, throw, and catch keywords. Best of all, it was designed to work perfectly with the Apple SDKs and NSError. In fact, NSError conforms to a Swift's ErrorType. You'll definitely want to watch the WWDC session on What's New in Swift to hear more about it.

**Availability: **Using the latest SDKs ensures you get access to new features and information about platform changes. But sometimes you still need to target an older OS, and Swift makes doing so much easier and safer. The Swift compiler now shows an error when you use an API that is too new for your target OS, and #available blocks can safely wrap lines of code to only run when on the right OS versions.

**Protocol extensions: **Swift is very focused on protocol-oriented development -- there's even a session on the topic at WWDC 2015. Swift 2.0 adds protocol extensions, and the standard library itself uses them extensively. Where you used to use global functions, Swift 2.0 now adds methods to common types so functions chain naturally, and your code is much more readable.

**Swift-er SDKs: **Swift 2 works even better with the Apple SDKs, thanks in part to two new features in Objective-C: nullability annotations and generics. The SDKs have been updated to annotate API that cannot return nil so you don't need to use optionals as often. And with a true generics system employed by the SDKs you can more often preserve detailed type information in your Swift 2 code.

### Learn more

This is just a taste of what's new in Swift 2. You can download the latest version of _The Swift Programming Language_ from the iBooks Store, and be sure to watch the WWDC sessions live streamed and on video throughout the week. And to read more, visit <http://developer.apple.com/swift>
