# 200MB Max, No Storage, No Web Views: Is tvOS the Future of Apps?

_Captured: 2015-10-30 at 10:49 from [realm.io](https://realm.io/news/is-tvos-the-future-of-apps/)_

"The future of TV is apps." This was the provocative statement Tim Cook made at the Apple keynote presentation on September 9, 2015. It captures Apple's vision for the future of TV. Passive viewing is no more, and instead we will navigate through apps, offering up more dynamic experiences.

As bold as Tim's vision was, in the end, its success will be defined by what developers can ultimately do with Apple's tvOS platform.

![](https://realm.io/assets/news/tvos/future-of-tv.jpg)

> _So while Apple views apps as the future of TV, is tvOS also meant to show us the future of apps?_

As we set out to build a sample app that would showcase [the many tech talks we host](https://realm.io/news), and test our library's compatibility with this new platform, we ran into a number of different limitations & quirks that paint an exciting or dire picture of the future of development, depending on where you stand…

### No Persistent Local Storage

The first and most relevant to us, was that tvOS offers no persistent local storage. To some degree this is understandable, given that the devices come with a relatively small amount of storage: 32GB or 64GB. While it isn't much less than what you can get on an iPhone, most 1080p HD movies come in around 4-6GB, so it makes sense to reserve as much of the space as possible for that. Nevertheless, the lack of local storage means any app maker must use CloudKit or another cloud service to save their app's state across launches.

Of course as a persistence provider we could be worried, but the fact is that Realm can still be useful in this environment because we offer an in-memory mode. This mode still requires some disk access to coordinate internal locks. We ran into this immediately when attempting to open a Realm in the documents directory that caused this error:
    
    
    open() failed: No such file or directory

Evaluating the file system we realized that the documents folder is not available, and instead only the NSCachesDirectory and NSTemporaryDirectory can be written to. As a result, the tvOS build of Realm defaults to using the cache directory instead of the standard default in the documents directory.

### 200MB App Size Limit

tvOS enforces a 200MB limit on the app size, which will likely affect a number of apps. Games especially can reach over 1GB due to the inclusion of static assets. While, Apple has addressed this by offering [App Thinning and On-Demand Resources](https://developer.apple.com/library/watchos/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html), this is still a stark departure from the constraints on their other platforms.

### No Mach Messages

[Mach messages](http://www.opensource.apple.com/source/xnu/xnu-1456.1.26/libsyscall/mach/headers/mach.h) are a low-level kernel technology to pass messages between processes. Internally, Realm uses this technology in relation to our built-in support for encryption. Exploring the tvOS SDK, the mach.h header file lists the functions to send and receive mach messages, as unavailable, similar to WatchOS:
    
    
    __WATCHOS_PROHIBITED __TVOS_PROHIBITED
    extern void         mach_msg_destroy(mach_msg_header_t *);
    
    __WATCHOS_PROHIBITED __TVOS_PROHIBITED
    extern mach_msg_return_t    mach_msg_receive(mach_msg_header_t *);
    
    __WATCHOS_PROHIBITED __TVOS_PROHIBITED
    extern mach_msg_return_t    mach_msg_send(mach_msg_header_t *);

This seems reasonable since multitasking isn't possible with tvOS like it is on iOS or OSX. As a result, we had to disable encryption for Realm on tvOS.

Similar to mach messages, a [named pipe](https://developer.apple.com/library/mac/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemTechnology/SystemTechnology.html) is form of interprocess communication. Realm added support for interprocess notifications to support seamless sharing of Realm files between multiple processes on Cocoa. This enables debugging a file with the Realm browser while it is in use and also for iOS App and Watch extensions to share the same Realm file used in the main app. The notifications are delivered through a named pipe so that when a write transaction occurs, a notification can be sent to other processes to inform them that the Realm was updated.

Originally, Realm didn't offer support for this, so to get Realm working on tvOS, we simply [reverted back to the original code](https://github.com/realm/realm-cocoa/commit/18bd97cae016bf1e8250b6caea0f7b06ee55f21e) that only offers notifications within the same process.

### No Pasteboard API

Given the situation with mach messages and named pipes, this should come as no surprise. Pasteboard is the most high level form of interprocess communications, enabling copy/paste functionality on iOS and OSX. Under the hood, pasteboard is using mach messages to pass data back and forth between processes, so without this tvOS can't support copy/paste.

This is probably one of the more difficult limitations that developers are going to have to deal with. Web views are used in many places in iOS apps. For app makers supporting more platforms than iOS, non-critical components can be displayed through a web view to simplify development. Furthermore, web views can be updated after an app ships, so this offers flexibility to test features. Finally, this means web browsing in general isn't possible. For example, apps that support 3rd-party authentication with OAuth, their login flow will have to be redesigned specific for tvOS.

Apple does offer their own alternative in the form of TVML. This is a form of XML that allows developers to define their app's views, and then is used in conjunction with TVJS to create the overall client-server app via Javascript APIs. This allows developers to adjust the content of the app after it is deployed, but means rebuilding any existing web views with this technology.

### No Built-In PiP

We encountered this issue when building the RealmTV app, since we wanted to display the slides used in the presentation along-side the video of the presenter. Given that iOS 9 added support on the iPad for picture-in-picture, we assumed tvOS would have built-in support as well. However, [the new PiP is limited to iOS and only for the iPad](https://developer.apple.com/library/prerelease/ios/documentation/WindowsViews/Conceptual/AdoptingMultitaskingOniPad/QuickStartForPictureInPicture.html). As a result, we ended up tweaking the view hierarchy of [AVPlayerViewController](https://developer.apple.com/library/prerelease/tvos/documentation/AVFoundation/Reference/AVPlayerViewController_Class/index.html#//apple_ref/occ/cl/AVPlayerViewController) to make our own PiP solution

![](https://realm.io/assets/news/tvos/sam-brainfuck2.jpg)

![](https://realm.io/assets/news/tvos/sam-brainfuck1.jpg)

![](https://realm.io/assets/news/tvos/sam-brainfuck.jpg)

Viewers can cycle through 3 different PiP modes via a long-press on the Apple TV remote. While we are happy with our current version, we hope in the future tvOS adds built-in support for PiP.

### No Customizable Video Player

Following up on the lack of PiP, we were disappointed that the built-in video player in AVKit was not extended to offer greater customization. Sure you can drop down to AVFoundation and build your own video player, but you would then run into issues of supporting features specific to Apple TV, such as the top navigation bar that drops down to adjust audio preferences. Given that the Apple TV's primary purpose is to consume media, this aspect should be available for developers to customize and create novel experiences with.

### No ReplayKit

Similar to the lack of PiP, looking over the tvOS SDK, we were surprised to see that ReplayKit wasn't available. This framework is targeted at gamers and lets players record their gameplay and then share video with other players and viewers online. Given that the Apple TV is being promoted as not just a media consumption device but also for gaming, it seems odd that this framework isn't available for developers to integrate. One guess, is that the hardware is not powerful enough to handle recording 1080p gameplay along-side the rendering of the actual game.

### No Photos Access

In iOS, you could display a photo picker to the user via UIKit's [UIImagePickerController class](https://developer.apple.com/library/prerelease/tvos/documentation/UIKit/Reference/UIImagePickerController_Class/index.html#//apple_ref/doc/uid/TP40007070), or starting with iOS 8, via the [Photos framework](https://developer.apple.com/library/prerelease/ios//documentation/Photos/Reference/Photos_Framework/index.html). Both of these are unavailable in tvOS, which means your app can't take advantage of a user's photos. This seems odd, given that the device supports viewing photos stored in iCloud.

### No Calendar/Address Book/iMessage

AddressBook/Contacts, and EventKit frameworks are unavailable, so apps won't be able to incorporate any data stored in iCloud. Furthermore, the MessagesUI framework isn't available, inhibiting the ability to send iMessages. Given that the new Apple TV remote includes a button for Siri, this seems like a lost opportunity.

### No Multipeer Connectivity

Finally, the [Multipeer Connectivity framework](https://developer.apple.com/library/ios/documentation/MultipeerConnectivity/Reference/MultipeerConnectivityFramework/) isn't available in tvOS. This framework handles identifying iOS devices via Wi-Fi, peer-to-peer Wi-Fi, and Bluetooth, and then subsequently managing the transfer of data between the devices. For multiplayer gaming, this framework really shines and its absence on tvOS means game that could have a split-screen between the tv and the users' iPhone/iPad/iPod will require syncing the data via iCloud or another service. This might work for say a multi-player poker game but anything with lower latency requirements might suffer.

### So what does this all mean for tvOS & iOS?

In terms of app development, tvOS doesn't seem to break new ground. watchOS has struggled to attract developers to the platform because what they can do is still very limited. tvOS doesn't seem to be in that bad of a position, but its limitations are still going to create hurdles for developers.

The lack of web views seems pretty drastic, especially given the prevalence of OAuth. While TVML/TVJS are an interesting departure from native development, and somewhat balances the lack of web views, its proprietary format still forces development teams to rewrite existing web content. Dropping support for web views might be reflective of new long-term position for Apple, similar to their refusal to support Flash once was. iOS 9 brought content blocking to Safari, so it does appear Apple could be trying to push more development towards native apps.

The other limitations, though, appear to be more of temporary limits imposed on a first version product. The lack of video player customization and no Multipeer Connectivity seem like probable targets for improvement in future versions.

Overall, though, you have to balance the limitations against the potential scale of the opportunity. In the US, the average person spends [2.8 hours a day watching tv](http://www.bls.gov/news.release/atus.nr0.htm). This is actually more than the [~1.3 hour per day the average person spends in apps](http://www.nielsen.com/us/en/insights/news/2015/so-many-apps-so-much-more-time-for-entertainment.html) on their smartphone in the US. From that perspective, tvOS is opening up a new opportunity for developers that could be even bigger than the one experienced with iOS.

_We are excited to see where the platform goes and if you are interested in using Realm in your tvOS app, check out [this PR](https://github.com/realm/realm-cocoa/pull/2506) until we can make an official release for it. And look out for the Realm app once it is released in the App Store ;)_

![](https://realm.io/assets/news/tvos/realm-tv-main.jpg)

![](https://realm.io/assets/news/tvos/realm-videos-main.jpg)
