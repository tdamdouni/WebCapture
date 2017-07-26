# How Dropbox Uses C++ for Cross-Platform iOS and Android Development

_Captured: 2015-12-12 at 11:02 from [oleb.net](http://oleb.net/blog/2014/05/how-dropbox-uses-cplusplus-cross-platform-development/)_

Of all the things I learned at [UIKonf 2014](http://www.uikonf.com/) last week, the one that impressed me most was Dropbox's story of how they use C++ to share non-UI code between iOS and Android apps. (UIKonf was awesome, by the way; you shouldn't miss it next year.)

[ ![The UIKonf 2014 venue at Heimathafen Neukölln, Berlin](http://oleb.net/media/uikonf-2014-venue.jpg) ](https://www.flickr.com/photos/thewavingcat/14181205181/in/set-72157644254871277)

> _The UIKonf venue. Since Dropbox was a sponsor of the conference and their talks were not part of the regular schedule, they got moved to a side stage. They would definitely have deserved a place on the regular stage._

What follows is mainly a summary of my notes from the talk by [Mailbox](http://www.mailboxapp.com/) developer [Steven Kabbes's](https://twitter.com/kabb) about how they brought Mailbox to Android. It also includes information from talks by [Stephen Poletto](https://twitter.com/stephenpoletto) and [Tina Wen](https://twitter.com/TinaWen4) who worked on [Carousel](https://www.carousel.com) and talked about their experiences launching version 1.0 simultaneously on iOS and Android. Please note that I may have misunderstood a few points so be skeptical about everything I say here. I apologize to the Dropbox team for anything I got wrong.

# Motivation

> **Android is not going away.**

Let's face it, Android is not going away, said Stephen Poletto to a room full of iOS developers. But fully native development for several platforms is expensive and time-consuming. Essentially, your company has to write and maintain multiple implementations for the same problem. Teams write (and have to fix) the same bugs multiple times. There is a good chance that bugs reported on one platform also exist on the others but remain unnoticed. Apps that are meant to behave identically on all platforms may exhibit subtle differences due to differing implementations. Shipping new features at the same time on all platforms is hard.

When work started on the Mailbox app for Android, the team made the choice to write a large portion of the non-UI code in C++ -- rather than rewriting the entire app in Java -- with the goal of sharing that common C++ layer between iOS and Android. The iOS app used [Core Data](http://en.wikipedia.org/wiki/Core_Data) at the time, so migrating it off of Core Data to the shared C++ library was also part of the process. C++ seemed like an obvious choice because it is available on every platform and team members preferred the language over Java.

The Carousel team made the same choice since launching simultaneously on iOS and Android was an important goal from the start.

> **If you haven't looked at C++ in the last five or ten years, it is worth another look.**

# Toolchain

C++ is natively supported on iOS and it is very easy to interface between Objective-C and C++ using [Objective-C++](http://en.wikipedia.org/wiki/Objective-C#Objective-C.2B.2B).

On Android, calling into C++ can be done through the [NDK](https://developer.android.com/tools/sdk/ndk/), which reportedly is not a pleasure to use. Dropbox found Google's meta-build system [gyp](https://code.google.com/p/gyp/) to work reasonably well. In addition, the [Java Native Interface](http://en.wikipedia.org/wiki/Java_native_interface) is a pain you have to accept. But none of these issues is a roadblock, and Steven expressed hope that Google or the community will build better tooling support over time.

C++ as a language has quite a bad reputation in the Objective-C community. However, Steven noted that it has improved a lot with [C++11](http://en.wikipedia.org/wiki/C%2B%2B11) and definitely warrants a closer look again if you haven't used it recently. In fact, many modern Objective-C features like blocks or [ARC](http://en.wikipedia.org/wiki/Automatic_Reference_Counting) even have close equivalents in C++11 ([lambdas](http://en.wikipedia.org/wiki/Anonymous_function#C.2B.2B_.28since_C.2B.2B11.29) and [smart pointers](http://en.wikipedia.org/wiki/Smart_pointer#C.2B.2B_smart_pointers), respectively). C++ remains a very complex language, though, and definitely involves a learning curve for many teams.

[SQLite](http://sqlite.org) is the obvious choice for a powerful data store that is supported everywhere. The standard SQLite C API is a bit unwieldy, but there exist many C++ libraries that wrap it in an object-oriented interface, just like [FMDB](http://ccgus.github.io/fmdb/) does in the Objective-C world.

> **Think of it as a client-server architecture where the server is never offline and has zero latency.**

# Architecture

## Client-Server Design

All UI code uses the native UI APIs on all platforms (Objective-C/UIKit on iOS, Java on Android). Most of the "model layer" code lives in the shared C++ library. Rather than calling it a model layer, Steven likened the design to a client-server architecture where the server (the C++ library) is never offline and has zero latency. Seeing the UI code and the shared library as two separate entities helps design clear interfaces between the two and thus keep the concerns properly separated.

The client-server architecture inside the app also predetermines how data is passed between the UI and the C++ layer. The two layers don't access the same data objects. They use message passing to send copies of the data from A to B.

Where to draw the line between the shared library and platform-native code will always be tricky. You should be prepared to make wrong decisions and correct them later. This is further complicated by the fact that some things that should ostensibly be part of the shared library have platform-specific features and APIs. Examples include networking (think of background downloads with `[NSURLSession`](https://developer.apple.com/library/ios/documentation/Foundation/Reference/NSURLSession_class/) on iOS), app backgrounding behavior, and also file system access (because iCloud defaults to backing up all files). For these areas, the team had to build abstractions in the shared library that are then implemented with native implementations in the client apps.

For other platform-specific APIs, replacements must be selected. One such example is the `NSUserDefaults` system used for [storing preferences and settings in Cocoa](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/UserDefaults/). As that API is not available to the shared library, Dropbox uses Google's [LevelDB](https://code.google.com/p/leveldb/) instead.

## "Rewriting Core Data"

The central component of the shared C++ library is a query and persistence framework that more or less assumes the same role that Core Data plays in Cocoa. As I understand it, the Mailbox team did not attempt to rewrite Core Data in its entirety. Firstly, only a subset of Core Data's features was required and secondly, the team found that some Core Data APIs were just not a good fit on Android. Instead, they designed their own framework based on SQLite.

Steven gave this broad outline of the architecture in the Mailbox app:

  * `Query` objects essentially represent the parameters of an SQL statement. Running a query returns a result set.

  * Result sets get turned into `DataView`s. These are essentially the [view models](http://en.wikipedia.org/wiki/Model_View_ViewModel) that represent the data in the form that can be consumed by the UI (for example, in a table view). As you can see, the view models are also part of the shared C++ library. Both the iOS and Android apps consume the same view models. `DataView`s are immutable.

  * Whenever a query is updated, a new `DataView` is the result. The framework then computes a `ChangeSet` that describes how to transition from the old to the new `DataView`. The frontend apps can use these `ChangeSet`s to update their views without having to reload everything. This improves performance and allows animated UI updates. It works quite similarly to what you would do with `[NSManagedObjectContextObjectsDidChangeNotification`](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/CoreDataFramework/Classes/NSManagedObjectContext_Class/NSManagedObjectContext.html#//apple_ref/doc/uid/TP30001182-BAJJHDFC) or `[NSFetchedResultsController`](https://developer.apple.com/library/ios/documentation/CoreData/Reference/NSFetchedResultsController_Class/) in Core Data.

  * When the UI wants to make a change to the data, it sends a message to the server. As the server processes the update, the client is immediately notified of a new `ChangeSet` for its `DataView` and can update its UI accordingly.

For each platform, the team writes thin wrapper classes in the native language to abstract the C++ classes away from the UI code. In Objective-C, this is easy to do thanks to Objective-C++. Most methods in the Objective-C wrapper classes just pass right through to the C++ objects they encapsulate, converting data to and from native types as needed. From the perspective of the client, it should not matter how the server is implemented.

## Image Caching

The Carousel app also handles image caching -- an essential component in a photo app -- in the shared library. The UI layer passes the size and position of the current viewport to the C++ layer, which uses this information to choose what images to hold in the cache. This algorithm can be shared between iOS and Android since the app uses essentially the same view layouts on both platforms.

## Concurrency

The client-server architecture also simplifies the threading model. Since the UI and C++ layers do not share data, they can make their own threading considerations independently from each other. While the main thread must obviously be reserved for the UI, the C++ layer mostly (with very few exceptions) runs in a single background thread, as Steven told me after his talk.

This makes the architecture considerably simpler because locking is rarely needed. And since most devices currenly only come with two cores anyway, using one core for the main thread and one for the "data store" thread gives you most of the benefits (provided that networking and disk I/O is performed asynchronously). This design may change in the future as devices with more cores become ubiquitous, but it was the right decision to keep the architecture as simple as possible initially.

# Challenges

Clearly, what the Mailbox and Carousel teams did is not a perfect solution for every app. As always, the devil is in the details, and I am sure you will encounter many issues you haven't thought of before when you actually try to implement something like this. You will also have to adjust your processes to allow for the tighter integration of your apps. Going forward, changes to the shared library that could break the clients must be synchronized across all platforms.

At any rate, I think this topic deserves a broader discussion in the iOS community, and that's why I wrote this piece. It would be great if we as a community could develop these ideas further.

# Sample Code

I would like to thank Steven Kabbes for his input on a draft of this post. Steven also published [his notes about his talk](https://github.com/skabbes/uikonf_coredata_talk) and generously [set up a repository](https://github.com/skabbes/mx3) that shows how to implement this approach in a small sample app that compiles on iOS, Android, and OS X. This is a tremendous help, if only because it helps you get the toolchain set up. I encourage you to check it out and [join the discussion on GitHub](https://github.com/skabbes/mx3/issues).

**Update December 15, 2014:** At CppCon 2014, folks from Dropbox gave several talks that may be of interest to you. In [A Deep Dive Into Two Cross-Platform Mobile Apps Written in C++](https://www.youtube.com/watch?v=5AZMEm3rZ2Y), Steven Kabbes and Tony Grue approach the topic from a slightly different angle. Alex Allain and Andrew Twyman's presentation titled [Practical Cross-Platform Mobile C++ Development](https://www.youtube.com/watch?v=ZcBtF-JWJhM) gives practical advice how you could go about implementing this in your own apps.
