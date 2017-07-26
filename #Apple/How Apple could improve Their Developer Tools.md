# How Apple could improve Their Developer Tools

_Captured: 2015-11-27 at 11:23 from [stanislaw.github.io](http://stanislaw.github.io/2015/11/20/how-apple-could-improve-their-developer-tools.html)_

This is the summary of numerous discussions I had with my colleague [Alex Denisov](http://lowlevelbits.org/) about our developer experience related to Xcode and iOS development in general.

I would like to share our thoughts to community because definitely there are gaps in Xcode infrastructure that have negative impact on our developer's productivity and hence the final quality of products we produce.

The following topics are considered:

  * Monoliths are always bad 
    * Xcode
    * project.pbxproj
  * Visual vs Semantic ("mouse-driven" vs "keyboard-driven" development) 
    * Auto Layout
    * Xibs/Storyboards
    * Focused tests

## Monoliths are always bad so why are they still here?

The problem with monoliths is that they either scale poorly or do not scale at all: [Monoliths are Bad Design… and You Know It](https://www.thoughtworks.com/de/insights/blog/monoliths-are-bad-design-and-you-know-it).

We do understand that monolith is always a necessary step for some thing to emerge, grow and become mature. But at some point monolith has to be decomposed into a modular components so that each component does have [one single responsibility](https://en.wikipedia.org/wiki/Single_responsibility_principle) and so that it can be developed in isolation without affecting the rest of the system. In that sense LLVM emerged as reaction to monolithic GCC, Carthage, "decentralized dependency manager" opposes to more "centralized" CocoaPods, modular AFNetworking 2 was a reaction to monolithic AFNetworking 1 so on and so on.

We also have one example of how Apple fixed one of its Big Monoliths: Storyboards. It took quite a few years before from Apple we got "official" functionality to split huge Storyboard files into a smaller single-story-focused ones while Open Source libraries like RBStoryboardLink had been introduced much earlier, in 2012: [RBStoryboardLink - DEPRECATED](https://github.com/rob-brown/RBStoryboardLink/blob/dab792e5e3707634dd16300cd8e9874e5151805e/README.md#deprecated).

Aside from that positive precedent with Storyboards many of those Monoliths are still here. Let's look at the most critical of them.

### Xcode

Obviously the biggest monolith is Xcode itself: its main blocks are text editor and interface builder, the others are related to Build Settings management, Apple account management, Source Control integration etc ([Xcode Sucks And Here's Why](http://devcodehack.com/xcode-sucks-and-heres-why/)).

We don't see what's the rational behind having one huge app doing all that, instead we see how in Xcode 7 switching between code- and xib- files literally can take 10+ seconds, we see simulators hanging, crashing or starting from scratch (apple on a black screen 5+ times a work day). We never use source control functionality as it is much more poor compared to what we can have by "just" using command line or specialized tools like [SourceTree](https://www.sourcetreeapp.com/).

Currently more and more people switch to using AppCode which is better focused coding IDE. It doesn't have Interface Builder and other modules that Xcode has but instead provides better code analysis and refactoring tools because, I believe, AppCode developers can concentrate on doing things well by not doing things that are not really needed (though for example [CocoaPods support](https://www.jetbrains.com/objc/features/) is not what I would expect from a "smarter" IDE as AppCode, looks like they also sometimes tend to onboard trendy thingies just to have "everything covered").

### project.pbxproj

The project.pbxproj file is what we consider the second biggest monolith after Xcode.

I bet that if you ever have a chance to look at this file from beginning to end you always have the same impression that I have: this file is not to be managed for humans and I would say is not designed for humans in mind in general.

Apart from having poor format which has those comments describing obscure identifiers everywhere (`867CFE661BFFDC5E001F85A8` is a `/* ViewController.m */` so that you know) it does quite a lot of things that we would like to have under our complete human control i.e. would like all of the following to be readable and editable as plain text files that humans can easily understand and therefore can maintain:

  * Project structure
  * Configurations
  * Targets
  * Schemes
  * Build Settings
  * Code signing details,
  * Run Scripts (yo `shellScript = "\"${SRCROOT}/Pods/Target Support Files/Pods/Pods-frameworks.sh\"\n";`)
  * Build Phases (yo `74E916613A2758307FB74A44 /* Embed Pods Frameworks */ = {`),

We didn't manage yet to play around CMake to maintain iOS project structure but I strongly believe that next replacement for .pbxproj will be some build system based on text files and inspired by mature build systems like Make, CMake, Ninja, Gradle etc and yes it will be designed **for humans**.

Below we discuss some of the issues that prevent us from moving away from rigid .pbxproj structure.

#### Groups vs Folders

We never need groups - our groups always match just real folders. We even consider it as anti-pattern if one uses different structures for groups/files and folders/files because it usually indicates the lack of understanding and care about the semantics of project structure.

I mentioned it already: we are even very close to start replicating Xcode iOS project skeleton using CMake and start developing our apps using it by maintaining our project structure using `CMakeLists.txt` pretty much the same as LLVM developers do it.

I specially asked my colleague Android developer and he confirmed that they do not have this concept of Groups so that when you add a new file your Git working tree contains only that file and nothing else and quite to the opposite: when we add file to Xcode, also the corresponding entry is added to project.pbxproj which take us to the land of merge/rebase conflicts.

#### xcconfig: wrapping and inheritance

Had we better xcconfig parser we could nicely abstract our build settings configuration and also manage build settings of our third-party components that we use.

[This question](http://www.cocoabuilder.com/archive/xcode/251602-xcconfig-files-line-wrap-and-inheriting.html) was asked in 2006 and we are still there:

Line wrapping:

> > I have a line longer than the width of my monitor: can I break it up? The C way doesn't work.

> You can turn on wrapping in the editor, but no, the very, very simple parser for .xcconfig files doesn't support broken-up lines.

The benefit from this feature would be better readability and lower risks of potential merge conflicts (example: one long string of `-Warning-flags` is again the monolith).

Inheritance - [How to append values in xcconfig variables?](http://stackoverflow.com/questions/1393987/how-to-append-values-in-xcconfig-variables):

> > Does anyone had success appending new values to variables in xcconfig files?

> For reasons stated in other answers to this question, you can't inherit values easily.

The recommended workaround there is to namespace corresponding variables and merge them into one final xcconfig at the last step:

> merge.xcconfig:
    
    
    OTHER_CFLAGS = $(inherited) $(APP_PLATFORM_CFLAGS) $(APP_PROJECT_CFLAGS) $(APP_TARGET_CFLAGS)
    

As another workaround CocoaPods uses its own generator of final configuration-specific xcconfig file which merges into it all the Pods xcconfigs:
    
    
    // Pods/Target\ Support\ Files/Pods/Pods.debug.xcconfig 
    HEADER_SEARCH_PATHS = $(inherited) "${PODS_ROOT}/Headers/Public" "${PODS_ROOT}/Headers/Public/AFNetworking" "${PODS_ROOT}/Headers/Public/ObjectiveSugar"
    

We could instead have:
    
    
    // AFNetworking.xcconfig
    HEADER_SEARCH_PATHS = $(inherited) "${PODS_ROOT}/Headers/Public/AFNetworking"
    
    // FinalConfig.xcconfig
    #include "AFNetworking.xcconfig"
    

## Visual vs Semantic: mouse-driven vs keyboard-driven development

A few examples are better than a paragraph, they are in random order so guess which is which:

  * Pressing Command + U key to run tests instead of clicking on small green/red icon
  * Using mouse to set up complex auto layout in Storyboard instead of doing the same using some code DSL like [Carthography](https://github.com/robb/Cartography) / [SnapKit](https://github.com/SnapKit/SnapKit)
  * Building static framework using Makefile or CMake instead using Build action in Xcode
  * Opening quake-like terminal using F1 key and doing Git stuff in it instead of using Xcode embedded Source Control tools.

Yes, mouse can help us to come up with something simple quickly in just a few clicks but as soon as our system becomes more complex it becomes very hard to manage that complexity with a mouse or trackpad.

_**Our thesis is that Apple should invest more of its huge intellectual resources into development of semantics of its Developer Tools infrastructure (good example: Testing frameworks) rather than development of "all covered" visual studio because mouse-driven development just does not scale while semantics, eternal OOP, SOLID principles and they are all about making things scalable.**_

Currently it looks like Apple rather favours mouse-oriented developers - every time new UI feature appears we more likely first get new clickable items in Xcode but corresponding semantics on code and infrastructure level is often poor and does not help us to manage complexity and maintain good separation of concerns. Again, let's look at some examples.

### Auto layout and UI in general

If we look at Web we'll see that clean separation between content (HTML) and styles (CSS) was introduced at the rather early stage of its evolution. The fact that both content and styles can be managed by plain text files should have inspired Apple to introduce something based on the same principle. I am not sure if there is any specific reason why concept similar to the concept of stylesheets was not introduced yet.

With current native tools you cannot succeed in management of complex auto layout: we neither have visual tools that would allow us to set up constraints for complex views (unless we are True Mouse Clickers) nor we have fine-grained DSLs developed by Apple officially (that's why we sometimes have those crazy amounts of `addConstraint:` given we want to stay native).

_**This is why so many Open Source solutions appear to compensate that lack of native support for semantics of UI: good examples are ComponentKit and different Auto Layout DSLs like Carthography, Snapkit and Parus. It is worth mentioning that so far AFAIK nobody ever tried to create alternative to Interface Builder because nobody wants to compensate THAT mouse-driven thing.**_

### We don't need Xibs in our binaries and there is no need in overhead of loading them via Runtime

One important thing that contributes to this gap between Interface Builder level and Objective-C/Swift code level implementations is the fact that we do not have access to intermediate representation that is produced from our Storyboards and Xibs. We only get final artefacts like View Controllers or Views in Runtime space when application is already a binary and is on the air.

Completely alternative approach would be to generate intermediate code in a form of classes based on Factory Pattern so that for particular View Controller or View we could have access to their Factories generated from their Xib/Storyboard files. Not only it would allow developers to observe their artefacts long before compilation process even starts but would also eliminate overhead of both compilation time and runtime instantiation. Can you imagine your application binary without Xibs/Storyboards in its resources folder, can you expect better performance seen in Instruments?

Having that direction taken eventually we would realize that those factories are now to be managed **by humans** and this could initiate a new cycle in our UI programming practice.

### Focused tests feature is missing in XCTest

It have been there for years in Cedar testing framework: [Focused specs](https://github.com/pivotal/cedar/wiki/Getting-started#focused-specs). But using XCTest when you want to run one test or one test class in a focused mode the only way to do that is to click that small green/red icon using your mouse/trackpad which is completely counter productive as it adds additional complexity to the TDD flow which always implies fast iteration.

We could just have conventions like `\- (void)ftest...` or even better Clang annotations to instruct XCTest to run Command+U on only the tests that we marked as a focused group.

## Conclusion

To be honest we have many more of those ideas that we could share with Apple if we were sure that there actually is anybody who is ready to listen. For example, the third biggest Monolith that I didn't write about is of course xcodebuild which is another story probably for the Part 2 of this post.

To wrap it up: aside from examples given above we find those simple principles or heuristics very valuable in our development practice:

  * Stay away from monoliths. If you have one think carefully and break it into components and make them as fine-grained as you can using "[loose coupling, high cohesion"](https://en.wikipedia.org/wiki/Coupling_\(computer_programming\)) principle.
  * Mouse-driven development doesn't scale while plain text files with carefully designed classes or DSLs in them at least have a chance to.
