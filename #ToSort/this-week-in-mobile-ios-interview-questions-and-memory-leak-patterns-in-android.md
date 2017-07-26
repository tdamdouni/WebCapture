# This Week in Mobile: iOS Interview Questions and Memory Leak Patterns in Android

_Captured: 2017-03-29 at 01:58 from [dzone.com](https://dzone.com/articles/this-week-in-mobile-march-24?oid=twitter&utm_content=buffer3f995&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The developer preview of Apple also released a new [red iPhone](http://www.apple.com/ie/ipad-9.7/), supporting the (RED) global fund to fight AIDS, along with a [new iPad](http://www.apple.com/ie/ipad-9.7/), which is pretty much an original iPad Air with a bumped up A9 chip and a 9.7 inch Retina display.

Every few weeks I find another great article exploring memory leaks. We've got another this week, for Android developers, which goes into a fantastic level of detail. There's also lots of other great articles covering audible Xcode breakpoint, interview questions for iOS developers, and a long list of resources that every Android developer should be aware of.

## **iOS**

Did you know that you could have [Audible Xcode Breakpoints](http://sound-of-silence.com/?article=20170306%20)? Matt Reagan explains how you can add them, and even has a [collection of audio files](https://github.com/matthewreagan/Xcode-Breakpoint-Sounds) that he has compiled for this purpose.

The team at Pinterest have put together [Plank: Immutable Model Generation for iOS](https://medium.com/@Pinterest_Engineering/introducing-plank-immutable-model-generation-for-ios-4b2f64bda00c#.7mqbk4frm), ensuring that models are thread safe. It's written in Swift and generates the resulting models in Objective-C.

You might not yet be taking full advantage of Protocol Oriented Programming. Learn how it's [A Swift Solution to OOP Headaches](https://medium.com/ios-seminar/protocol-oriented-programming-a-swift-solution-to-oop-headaches-e05d9c5d29a1#.h7wqpqdx1).

Whether you're running the interviews or looking for a job, this series of [iOS Interview Questions and Answers](https://medium.com/ios-os-x-development/50-ios-interview-questions-and-answers-part-3-3fad146b6c3d#.ys7dd4fbd) makes for great reading. How many are you able to answer?

Some projects to check out:

  * [ReverseExtension](https://github.com/marty-suzuki/ReverseExtension): A UITableView extension that enables cell insertion from the bottom of a table view.
  * [GodEye](https://github.com/zixun/GodEye): Automatically display Log, Crash, Network, ANR, Leak, CPU, RAM, FPS, NetFlow, Folder, etc., with one line of code based on Swift.
  * [Serpent](https://github.com/nodes-ios/Serpent): A protocol to serialize Swift structs and classes for encoding and decoding. 
  * [spruce-ios](https://github.com/willowtreeapps/spruce-ios): Swift library for choreographing animations on the screen.

## **Android **

[Nearby Notifications](https://android.jlelse.eu/nearby-notifications-9bc5e52e4436#.ltb276nfx) are location-specific notifications that can be sent to users for any app without needing the app installed on their device. If you're dealing with beacons, this is something you should learn.

From common causes to the tools that will help you discover them, [Memory Leak Patterns in Android](https://android.jlelse.eu/memory-leak-patterns-in-android-4741a7fcb570#.mp06dciv4) is one article that you can't afford to miss. The article links out to some great references and there's even an [accompanying app](https://github.com/frank-tan/SinsOfMemoryLeaks) with two branches: one with the leaks, one with the fixes.

In this new [From Design To Android](http://saulmm.github.io/from-design-to-android-part1) series, you'll see how to take an existing design and build a complete implementation in Android.

With sections for beginners and advanced developers alike, [50+ Ultimate Resources to Master Android Development](https://blog.aritraroy.in/50-ultimate-resources-to-master-android-development-15165d6bc376#.eysjvz4eo) is a goldmine!

Some projects to check out:

  * [atlas](https://github.com/alibaba/atlas): A powerful Android dynamic component framework.
  * [DiscreteScrollView](https://github.com/yarolegovich/DiscreteScrollView): Scrollable list of items, where the current item is centered and can be changed using swipes.
  * [Robust](https://github.com/Meituan-Dianping/Robust): Robust is an Android HotFix solution with high compatibility and high stability.Robust can fix a bug immediately without publishing an apk.
  * [fancyDialog](https://github.com/geniusforapp/fancyDialog): A simple dialog to show fancy content.

## **General **

In an article that will resonate with all designers, Alastair Simpson explains that [The Hardest Thing in UX Design](https://blog.marvelapp.com/hardest-thing-ux-design/) is convincing the rest of your team the importance of UX design.

It's funny that we spend so much time perfecting our builds, but the accompanying release notes are often an afterthought. In [As a Designer I Want Better Release Notes](https://uxdesign.cc/design-better-release-notes-3e8c8c785231) you'll see some easy tips into making your release notes so much better.
