# Nine Releases Make an Xcode

_Captured: 2017-08-08 at 20:31 from [dzone.com](https://dzone.com/articles/nine-releases-make-an-xcode?edition=310393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-21)_

All [these](http://www.alexcurylo.com/2017/06/19/core-mlaguena/) [new](http://www.alexcurylo.com/2017/06/19/core-mlaguena/) [APIs](http://www.alexcurylo.com/2017/06/19/core-mlaguena/) are very well and all, but now let's get to the really exciting stuff from [WWDC](http://www.alexcurylo.com/2017/06/19/core-mlaguena/):

**[What's New in Xcode 9](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/WhatsNewXcode/xcode_9/xcode_9.html)**

  * **All new editor.** Fast, structure-based editor that lets you intelligently highlight and navigate your code. Includes great Markdown support.
  * **Refactoring.** Refactoring built right into the editing experience and works across Swift, Objective-C, Interface Builder, and many other file types.
  * **Super-fast search.** The Find navigator returns results instantly.
  * **Debugging.** Wirelessly debug iOS and tvOS devices over the network, new debuggers for Metal, and more features throughout Xcode.
  * **Source Control.** All new source control navigator and integrated support for GitHub accounts for quickly browsing repositories and pushing your repositories to the cloud.
  * **Xcode Server built-in.** Continuous integration bots can be run on any Mac with Xcode 9, no need to install macOS Server.
  * **New Playground templates.** Includes iOS templates designed to run well in both Xcode and Swift Playgrounds in iPad.
  * **New Build System.** An opt-in preview of Xcode's new build system provides improved reliability and performance.

That is … a _remarkable_ array of improvements. And those are just the highlights! Seriously, go Read The Whole Thing™. Most are runtime and debugging improvements, we'll just pick out to highlight further here the changes in asset catalogs, since there's some new resource stuff here you'll want to be aware of to be iOS 11 savvy:

> **Asset Catalogs**
> 
>   * Named colors support.
>   * Added wide gamut app icons.
>   * Added a larger iOS marketing to the App Icon set.
>   * Added option to preserve image vector data for matching Dynamic Type scaling.
>   * Added support for HEIF images.

The biggest one there is, as explained here, [Preserve Vector Data](http://martiancraft.com/blog/2017/06/xcode9-assets/):

> There's a new checkbox in the Asset Catalog Attributes Inspector called "Preserve Vector Data." Checking this box will ensure that Xcode includes a copy of the PDF vector data in the compiled binary. At runtime, iOS can automatically upscale or downscale the vector data to output an image in your app whether you're using the image in code or in a Storyboard scene. Remember: When using PDF vector data, set the "Scales" value to "Single Scale" in the Attribute Inspector to ensure the proper loading the PDF vector data to populate image.
> 
> This change also works in conjunction with [the new Tab Bar icon HUD](https://developer.apple.com/videos/play/wwdc2017/215/) that Apple implemented as an accessibility feature in iOS 11. If you enable "Preserve Vector Data" this feature comes to your apps with no additional work. By enabling this feature, iOS 11 can also automatically scale images regardless of whether you're increasing a UIImageView's bounds, or using Size Classes to change an UIImageView size…

Screenshot samples at [The Unexpected Joy of Vector Images in iOS 11](http://ericasadun.com/2017/06/15/the-unexpected-joy-of-vector-images-in-ios-11/).

And apparently Apple is bowing to popular pressure and making Xcode all but dependent on Github, see [Xcode GitHub Integration](http://indiestack.com/2017/06/xcode-github-integration/) and [The Marriage of Github and Xcode 9](https://dzone.com/articles/the-marriage-of-github-and-xcode-9). We'd mutter something curmudgeonly about why don't you go full fanboi and replace the documentation with hotlinks to Stack Overflow too, but we're worried they might take that idea seriously…

Community support we do find quite appealing though, is how enthusiastically the new stuff is being open sourced ([Apple open sources key file-level transformation Xcode components](http://ericasadun.com/2017/06/05/apple-open-sources-key-file-level-transformation-xcode-components/)).

This afternoon at WWDC we announced a new refactoring feature in Xcode 9 that supports Swift, C, Objective-C, and C++. We also announced we will be open sourcing the key parts of the engine that support file-level transformations, as well as the compiler pieces for the new index-while-building feature in Xcode…

And if that bit about "new build system" struck terror into your massively scripted heart, fear not, it appears to be pretty much a behind-the-scenes change all around: [New Xcode Build System and BuildSettingExtractor](http://jamesdempsey.net/2017/06/13/new-xcode-build-system-and-buildsettingextractor/).

> The new system is written in Swift and promises to be a significant advance in a number of areas including performance and dependency management. The new system is built on top of the open source [llbuild](https://github.com/apple/swift-llbuild) project and lays the foundation for integrating the Xcode build system with the [Swift Package Manager](https://swift.org/package-manager/)…
> 
> It appears that everything about defining build settings remains unchanged. Moving between the old and new build systems did not cause any build setting changes or recommended changes. The mechanisms for generating that giant bucket of key-value pairs known as build settings seem to be just the same as before.
> 
> This is great news. As developers, we don't need to learn a new complex system for defining build settings. We get to enjoy the benefits of a new, faster, modern build system with our existing build settings left intact…

(And if you haven't moved to .xcconfig files yet, or if you do them by hand, seriously do go check out [BuildSettingExtractor](https://github.com/dempseyatgithub/BuildSettingExtractor). So handy, we even contributed to it -- and that's as high praise as it gets, around these parts!)

That's enough for a TL;DR to get you salivating for the new stuff -- but if you missed our link to [New stuff from WWDC 2017](https://mackuba.eu/2017/07/05/new-stuff-from-wwdc-2017) last time, go check it out now; more details on Xcode changes there … and everything else as well. Veritably _encyclopedic,_ that reference!

OK, one last note that isn't Xcode 9 specific but you'll want to refer to it anyways: [iOS Simulator Power Ups](https://medium.com/the-traveled-ios-developers-guide/ios-simulator-power-ups-407060863b3c). Something for everyone there!
