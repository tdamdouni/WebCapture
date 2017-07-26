# The three-year journey to multitasking and resolution-independence in iOS 9

_Captured: 2015-06-25 at 21:59 from [arstechnica.com](http://arstechnica.com/apple/2015/06/the-three-year-journey-to-multitasking-and-resolution-independence-in-ios-9/)_

iOS 9 is giving the iPad some of the attention it needs, especially if you're the kind of person who's using it as a laptop replacement. The software keyboard is better. Support for physical keyboards is better. And, most importantly, we'll be able to use that big screen to look at more than one app at a time.

This may feel like a big change for the platform, but in reality, Apple has been laying the groundwork for multitasking apps since at least iOS 6. Developers have had to change their apps a lot in the last two years, between iOS 7's new aesthetic and the introduction of the iPhone 6 and 6 Plus. If they've been making those changes according to Apple's best practices, then they're already done most of the work to make their apps multitasking-capable.

We'll take a quick look at the existing technologies Apple is using to enable multitasking on the iPad, and then we'll look at what developers need to do to their apps to get them ready. Don't expect every app in the App Store to support multitasking on the day iOS 9 drops, but it should at least be a pretty easy process for anyone maintaining a universal iPhone and iPad app that plays by most of Apple's rules.

## Three years of groundwork: Auto Layout

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_0030-980x735.jpg) ](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_0030.jpg)

Apple began laying the groundwork for more flexible, resolution-independent apps back in iOS 6 with a then-new feature called [Auto Layout](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/Introduction/Introduction.html).

[This post](http://www.raywenderlich.com/20881/beginning-auto-layout-part-1-of-2) illustrates the challenges of making an app look good on multiple devices with multiple screen sizes in both landscape and portrait views, at least in the days before Auto Layout. Developers needed to write a fair amount of code to make sure that apps looked right on 3.5- and 4.0-inch iPhones and, if applicable, 10-inch iPads.

Auto Layout introduced the concept of "constraints," a set of conditions that defines the size and positioning of onscreen elements in relation to one another. Apple's [example](https://developer.apple.com/library/ios/recipes/xcode_help-IB_auto_layout/chapters/UnderstandingAutolayout.html#//apple_ref/doc/uid/TP40014226-CH22-SW1): "you can center an image horizontally in a storyboard scene. As the user rotates the iOS device, the image remains horizontally centered in both landscape and portrait orientations of the device."

Constrain your UI properly, and it will scale smoothly from 3.5-inch iPhones all the way up to 5.5-inch iPhones and even 10-inch iPads. Constraints can align items, define the amount of padding between items, and even control the size of buttons or other text fields (useful if, say, the length of a word inside a button changes when the language changes). These were the first seeds of resolution independence planted in iOS.

Apple has continued to build on Auto Layout and introduce complementary features in newer versions of iOS. A related feature coming with iOS 9, "[Stack views](https://developer.apple.com/library/prerelease/ios/documentation/UIKit/Reference/UIStackView_Class_Reference/index.html#//apple_ref/doc/uid/TP40015256)," makes it easier to align multiple views with one another.

## Size classes, not screen sizes

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_0035-980x735.jpg) ](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_0035.jpg)

In iOS 8, "size classes" were introduced to better support the new screens on the iPhone 6 and 6 Plus. Understanding size classes is key to understanding how Apple is making multitasking and resolution independence work.

iOS 8 apps can support two different horizontal and vertical size classes: "regular" and "compact." Standard iPad apps have regular horizontal and vertical size classes. Most iPhones have compact horizontal and vertical size classes. The iPhone 6 Plus in landscape mode has a compact height, but it's large enough to support a regular width, which is why so many of Apple's built-in apps resemble iPad apps when you turn the phone sideways.

Apple is actually encouraging developers to stop thinking of their apps as "iPhone" and "iPad" apps with "portrait" and "landscape" layouts, but as one big app that uses size classes to move information around no matter what device you're using or how the screen is turned. All of this is covered in the "[Getting Started with Multitasking on iPad in iOS 9](https://developer.apple.com/videos/wwdc/2015/?id=205)" session at the recently concluded WWDC (there are [some good resources](https://developer.apple.com/library/prerelease/ios/documentation/WindowsViews/Conceptual/AdoptingMultitaskingOniPad/QuickStartForSlideOverAndSplitView.html#//apple_ref/doc/uid/TP40015145-CH13-SW1) available on the developer site too).

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_4124.png) ](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_4124.png)

Let's look at the iOS Mail app to demonstrate the differences between regular and compact views. The compact view of the Mail app focuses on showing one thing at a time--your list of inboxes and accounts, a list of your messages, or the message you're currently reading or writing.

The regular view is a two-column layout. The left column is used to switch between inboxes and accounts and scroll through your e-mails, while the larger right column is always used for e-mail content. You can implement this kind of two-column layout for regular views using a [UISplitViewController](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UISplitViewController_class/) to combine two different, otherwise-independent views into a single, large view (despite its name, this feature is unrelated to the Split View multitasking feature).

On an iPad that supports the Slide Over feature (the iPad Air, Air 2, Mini 2, and Mini 3), it's no coincidence that the apps that are slid over look exactly like tall iPhone apps. Apps that already support compact views will just use that compact view when slid over.

Split View is more versatile but a bit more complicated. In Split View, each app you have open is either the "primary" app or the "secondary" app. The primary app is the one on the left and it can do a few things that the secondary app can't--it "owns" the status bar, can work with an external display, and can use as much as 75 percent of the display. This gives it enough room to use a regular horizontal size class. The secondary app, which can't use more than half of the display, can only use its compact size class. This image sums it up:

![](http://cdn.arstechnica.net/wp-content/uploads/2015/06/multitasking-size-classes_2x-980x671.png)

> _Enlarge / All the different potential size class combinations you can get on an iPad with Split View support._

When the iPad's screen is using the default 75/25 split in landscape mode, the primary app uses a regular horizontal size class while the secondary app uses a compact size class. When the screen is split down the middle, both apps use a compact size class.

There have been rumors about a new, larger "iPad Pro" for quite a while now, and [references in the iOS 9 code](http://www.macrumors.com/roundup/ipad-pro/) suggest that a device with 2732×2048 display may be in development. iOS 9's new multitasking features might actually make this sort of tablet feasible--a screen that large could conceivably fit two regular-sized views next to one another, rather than sticking with one regular view and one compact view or two compact views. It's certainly easier to imagine a larger iPad now than it was at this time a year or two ago.

## Making a multitasking app, and fighting for resources

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_0042-980x735.jpg) ](http://cdn.arstechnica.net/wp-content/uploads/2015/06/IMG_0042.jpg)

Apple is pushing developers pretty hard to make their apps compatible with these multitasking features. New projects created in Xcode 7 support multitasking by default. Developers can opt out by putting the `UIRequiresFullscreen` string in their app's info.plist file, but it's significant that it's opt-out rather than opt-in.

Current apps can be updated to support multitasking if their developers do three things: use the iOS 9 SDK, support all available screen orientations, and use a [Launch Storyboard](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/LaunchImages.html) when the app originally loads. Launch storyboards, also introduced in iOS 8, are just basic images that display while your actual app loads. Developers are supposed to make them look enough like their app that they trick users into thinking their app loads more quickly than it does (or, to use Apple's euphemism, "to enhance the user's perception of your app as quick to launch and immediately ready for use.")

Even though developers can opt out of Split View and make an app use the whole screen all the time, Apple still stresses that your app needs to be a "good citizen" when it comes to resource usage. Slide Over still works even if the app doesn't support Split View, and picture-in-picture video overlays will work everywhere. And even though users are going to have more apps fighting over the same hardware resources, Apple still wants everything to run at 60FPS as often as possible.

On a similar note, Apple also points out some edge cases developers might want to be aware of even if their apps don't explicitly support Split View multitasking. During [a WWDC session about multitasking](https://developer.apple.com/videos/wwdc/2015/?id=205), Apple talked a bit about how one app calling up the keyboard actually obscures both apps. Developers may want some of their content to move to make room for the keyboard even if the other app is the one that called the keyboard up. This is true even if your app uses the whole screen and never uses the keyboard, since users can still call in other apps that use the keyboard via Slide Over.

The WWDC session "[Performance on iOS and WatchOS](https://developer.apple.com/videos/wwdc/2015/?id=230)" runs through the Xcode instruments used to track performance--Core Animation, System Trace, Allocations, Leaks, and others.

Even if an app is individually well-behaved, Apple is asking developers to consider how that app will behave if two more apps are opened at the same time. Now you know why Split View is only available on the iPad Air 2, a device with twice the RAM and an extra CPU core that other iPads don't have. Apple is keeping a bunch of Apple A5-powered devices with 512MB of RAM around in iOS 9, so even developers targeting iOS 9 exclusively need to keep thinking about performance on these resource-limited devices.

And that's about everything you need to know--all the stuff Apple has done since 2012 to change iOS from an operating system that only supported a couple of screen sizes to one that, like other operating systems, doesn't care what size your windows are. There are many different WWDC sessions that cover all the technologies we've talked about here--if you're more interested in digging in, we've linked them all below.

### More information:

_Listing image by Apple_
