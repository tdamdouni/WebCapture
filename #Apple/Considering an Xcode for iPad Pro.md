# Considering an Xcode for iPad Pro

_Captured: 2016-03-26 at 20:06 from [minutestomidnight.net](http://minutestomidnight.net/blog/2016/3/considering-an-xcode-for-ipad-pro)_

Lately I've been giving some thought about what it would take for me to be able to replace my laptop with an iPad. I do most of my day to day work at a 5K iMac. I only use the laptop for work when I'm traveling or need a change of scenery. For example, yesterday we had some beautiful weather here in Washington, DC, so I spent some time working at an outdoor table at Starbucks.

An iPad wouldn't need to be as fast or capable as my desktop computer, but there is one big requirement: Xcode. As an iOS developer, I spend a huge amount of time in Xcode. Without it, I can't get very much work done on the iPad. Fortunately, there have been rumblings lately that Apple is developing a [version of Xcode for the iPad](https://www.macstories.net/linked/why-the-ipad-pro-needs-xcode/). I hope that's true, and I gave some thought to some of the areas Apple would have to tackle in order to pull it off.

### Text Editing

Of course, a lot of time in Xcode involves manipulating code via a text editor. This is probably the easiest thing to get right. There are many capable text editors on iOS today, and there's no reason Apple couldn't build one into Xcode.

### Interface Builder

Many apps are laid out using storyboards in Interface Builder. Developers can drag and drop interface elements and set up constraints that define how they relate to one another visually. It's a great (and occasionally frustrating) tool that offers a ton of fiddly options and settings. Interface elements can be large or very small - as small as 1 pixel in length or width.

At first I thought this might be a deal-breaker for Xcode on the iPad. Manipulating tiny UI elements with precision isn't something that wide fingers are good at in the same way that a mouse is. Sure, zooming and panning could help, but that seems like it might be time consuming and unwieldy. Then I realized there's another solution: the Apple Pencil. I don't think it'd be required, but the Pencil might be ideally suited for this task. Just like making a detailed drawing, developers could use the Pencil to edit small elements with precise detail. Panning and zooming would still be an option for developers who don't own a Pencil.

### File Handling

There's no getting around it: Developing apps involves working with a lot of files. You've got source code files, storyboards, icons and images, database schema, and more. Not only do developers need to organize the files within their project, they often also need to add them from other sources. For example, a designer might send me an updated set of icons for an app I'm working on. I need to import those into Xcode, replacing the existing set or adding them as necessary. That means Xcode for iPad needs robust support for moving files into (and out of) the app, something that iOS apps haven't always been good at.

There's also the question of where project files will be stored. I'm still [not comfortable using iCloud Drive](https://sixcolors.com/link/2015/07/icloud-drives-file-deleting-problem/) for critical applications. Other document storage providers like Dropbox don't always support two-way editing, so opening files in an app creates a copy instead of modifying the file in place. Xcode could store project files within the app's local storage, but that means it's totally siloed away from editing by other apps. None of these are ideal, but I suspect we'll have to live with it.

### Source Control

Related to file handling is the issue of source control. Any developer worth their salt keeps every code base in a source control repository. Xcode on the Mac supports Git and Subversion repositories, but the support has never been that great. It always felt like source control was tacked on to Xcode almost as an afterthought. My guess is that we'll be stuck with Apple's implementation, but hopefully Xcode for iPad will give Apple a chance to re-think the feature from the ground up. I have no doubt that Apple realizes source control is critical to app development, and without a command line to fall back on, I have my fingers crossed that they'll build a great source control tool on iOS.

### Command Line

Speaking of the command line, source control isn't the only part of development commonly accessed that way. Tons of apps make use of tools like [Cocoapods](http://cocoapods.org) or [fastlane](https://fastlane.tools) when building apps. These aren't just conveniences; In many cases, they're critical parts of the development process. A lot of apps simply can't be built without them. This might be the trickiest part of putting Xcode on the iPad. Let's be honest: Apple isn't going to give us command line access to iOS. Even if it did, a lot of command line developer tools rely on modifying data across application bundles in a way that isn't possible on iOS.

I imagine Apple will tackle this through a combination of new tools and keeping the Mac as a backup. There are some interesting hints that Apple is working on [their own implementations](https://github.com/apple/swift-package-manager) of some commonly used command line tools. Over time, those could be integrated into Xcode for iPad. It wouldn't be quite the same as using the command line, and a developer's options would be more constrained, but it's better than nothing.

At the same time, the Mac is still out there. For things that simply can't be done on the iPad, developers could open up their project on the Mac. At least at the outset, Xcode for iPad won't be a complete replacement for its Mac cousin, and nearly all developers will still have a Mac to work with.

### Assumptions

Presumably, Xcode for iPad would only be capable of producing iOS apps. There's just no way Apple is going to build some kind of "Mac simulator" for the iPad, and even if it did, the user interface to Mac apps would be unworkable. Mac app development is going to stay on the Mac.

At the same time, I'm assuming that Xcode for iPad would be limited to the 12.9" iPad Pro. There's probably not a technical reason that it couldn't run on the new smaller iPad Pro, but I just don't think a 9.7" screen will be enough space. Heck, I don't really feel comfortable in Xcode on the Mac unless I have a big screen like the 27" display on my iMac!

The larger iPad Pro is probably also the only iPad with sufficiently advanced hardware to run Xcode. Even on a powerful Mac, Xcode can really get your CPU working hard and consumes a lot of RAM. It's possible the 9.7" iPad Pro could run Xcode as well, but its 2GB of RAM (vs. the 4GB in the larger iPad Pro) might be too small. Either way, compile times will be slower than on a modern Mac. The A9X is a fast CPU for a mobile device, but it's a lot slower than the CPU on a new iMac or even MacBook Pro.

### Opportunities

If all this sounds like a lot of contortions to go through just to build apps on the iPad, there are some distinct advantages as well. The most obvious is portability. When I travel, I don't always want to bring a laptop with me, especially if I'm not planning on doing work. Yet I often _do_ bring my laptop, in case a work emergency arises that I need to address. Having Xcode on my iPad would probably give me enough of a safety net in those situations that I could leave the laptop at home.

It would also be incredibly convenient to run iOS apps on the same device I'm using to build them. Imagine running your app in split-screen mode with Xcode. The iOS Simulator on the Mac is pretty good for what it is, but nothing beats running an app on the real hardware.

In recent press events, Apple has presented the iPad as a PC replacement and a place to do serious work. Building a version of Xcode for iPad is a tall order, but also creates opportunities to re-think some of Xcode's UI for new devices. If Apple is serious when it says the iPad is the future of personal computing, it makes sense to tackle Xcode sooner or later. I'm looking forward to seeing what they come up with.
