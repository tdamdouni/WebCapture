# Make your app extensible with JavaScript Core

_Captured: 2016-05-28 at 18:53 from [medium.com](https://medium.com/ios-os-x-development/make-your-app-extensible-with-javascript-core-7074061f2b05#.6m09nydct)_

![](https://cdn-images-1.medium.com/max/1200/1*wxtcANhD7BZ0sUbyzHN27w.jpeg)

Undoubtedly, productivity apps are major time-savers over the use of homemade scripts and hacks. Not having to reinvent the wheel every time and getting a much improved experience is where the value comes from for the users. However, even the best apps are limited by the set of features the developer has bundled into, and sometimes it doesn't cover all the needs a user may have.

![](https://cdn-images-1.medium.com/max/600/1*yymi0OlC80QDsyVIu49-fA.png)

> _Craft plugin displaying an interface in Sketch_

Some apps are inherently extensible by their use of a scripting language as core _(e.g. Sublime with Python, Emacs with Lisp, Atom with JavaScript)_. It's not the case of many native apps, which are compiled, code-signed and sometimes sandboxed to guarantee their integrity. Very few native Mac apps have succeeded to become truly extensible: [Sketch](https://sketchapp.com/) is an amazing example, which has even succeeded to build a large ecosystem of plugins around it.

Since the early days, [Paw](https://luckymarmot.com/paw) has been sticking to the system as a native, code-signed and fully sandboxed app. But I realized the need of extensibility the day the [Apiary](https://apiary.io/) team showed interest in an integration with their open description format [API Blueprint](https://apiblueprint.org/). The idea of Paw importing 3rd party API descriptions to let users visually test their API calls and generate client code was extremely attractive. It was late 2014 and I was working alone on Paw. I knew I wouldn't be able to implement every feature request, so I wanted to make it scriptable and tell the Apiary folks: _"go ahead, you can build it yourself"_. It was challenging. But in just a few weeks I've been able to give them a beta version. Soon after, [Kyle Fuller](https://twitter.com/kylefuller), an Apiary guy and core CocoaPods maintainer, built the two first Paw extensions (one to import & one to export API Blueprint). It was an amazing feeling to see others actually build stuff for the app I was developing.

There was a dilemma on the choice of the scripting language. Sketch exposes an [CocoaScript](https://github.com/ccgus/CocoaScript) interface that lets users mix JavaScript with a syntax inspired by Objective-C, and gives access to all available OS X APIs. This would have been a serious security concern for Paw being a place where developers may store their production server credentials: letting 3rd party have unrestricted access to the app didn't feel right.

I had a personal preference for Python. The fully bidirectional _PyObjC_ bindings would have made nice API for Paw, and would give powerful control to the developers. Though, it had the same security concerns as CocoaScript, and OS X sandboxing would have become a challenge to achieve.

JavaScript was the most interesting choice because of its popularity, and OS X bundles a full JavaScript runtime in the system, which is the same as used by Safari. Since OS X 10.9 / iOS 7, the JavaScript Core framework exposes great Objective-C to JavaScript bindings (it had a C API before). This meant objects from either language would be bridged to the other by just following a simple protocol and following a few rules for memory management. The whole thing would run in a JavaScript Virtual Machine we would fully control. We would create JavaScript APIs to let 3rd parties safely access the data we wanted to expose.

#### Exposing a public interface is great for your codebase

Giving access to the internals of Paw to 3rd party developers has been a great experience: it forces us to think bigger and build more reusable components of which we aren't the only users anymore. It defines a clear contract between the application and the extensions, against which we're building unit tests.

We're probably the primary users of our own JavaScript API. Using it just after building it is nice to make sure it's functional when used in real projects and is easy to understand for others. We've built many extensions for Paw, mostly to import and export data, and to generate client code. We don't need to ship the app with the code necessary to read or write every possible file format. We keep our core code-base cleaner and the application's binary smaller.

![](https://cdn-images-1.medium.com/max/1200/1*yx0O3Yr2c6MFtDkFqEJ9mQ.png)

> _A JavaScript snippet running in Paw to generate a HMAC-SHA256 signature based on other inputs_

It's always exciting when I see an app I love get an update. But too many updates becomes bothersome, each requiring a new download and relaunch. It's where shipping features as extensions becomes great as it doesn't require to ship an update to fix a small issue in a component. We often improve the code generators for Paw, and we're currently refactoring all our importers/exporters: everything will be shipped without updating the app's binary.

The downside is if you're building your own app, you're going to have to implement your own extension update process. A typical Paw extension is compiled with Travis CI and pushed to a GitHub release. Our server only keeps the list of available extensions. When an update is needed, we just bump the Git tag number, and Travis and GitHub do the rest.

#### Open source

We would absolutely love to open source a significant chunk of Paw, but doing it right takes times, and time is the most valuable asset of a small team. Ultimately, we will do so by releasing some core components as beautiful libraries! Though, for extensions it was a no-brainer: we publish all our extensions on GitHub, users can help us improve them, and they use them as templates for new extensions.

It really worked! We've recently noticed a promising increase in the number of users asking questions about building extensions. People want to do more with Paw, make their workflow smoother, and use the app in scenarios we haven't integrated yet.
