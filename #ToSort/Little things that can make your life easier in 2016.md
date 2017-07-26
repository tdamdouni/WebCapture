# Little things that can make your life easier in 2016

_Captured: 2015-12-25 at 00:22 from [merowing.info](http://merowing.info/2015/12/little-things-that-can-make-your-life-easier-in-2016/)_

As we are closing this year, let's take a look at few simple things you can add to your iOS developer toolbox to make your life easier and be more productive in 2016.

## Using the power of User Breakpoints

We use breakpoints quite a lot, but I see that most of my friends only use regular breakpoints whilst debugging.

There is much more you can do with them, e.g. you can elevate your custom breakpoint to User Breakpoint and have them work in all your projects, why would you do that?

Because you can create symbolic breakpoint's that execute code whenever a specific point is reached, e.g. **UIApplicationMain**:

![](http://merowing.info/2015/12/symbols.png)

Did you see what did I do there?

Now whenever I debug ANY project I'm working on, instead of:

I can get straight to business with:

Without extra steps.

And you can do so much more:

  * [Want to log all methods getting called in Objective-C?](https://gist.github.com/krzysztofzablocki/4396302)

  * [Need some other good breakpoints ideas to add?](https://gist.github.com/Ashton-W/5c1ede17f8cec1f8b529)

## Making Xcode better

#### Plugins

Here are some of my favourite plugins for Xcode, if you don't give them a try you might be missing out on some really great features:

  * [Alcatraz](http://alcatraz.io) \- this is a plugin that adds a PackageManager into Xcode, which you will use to install all other plugins.

  * [KZLinkedConsole](https://github.com/krzysztofzablocki/KZLinkedConsole) \- adds ability to jump straight to the source code that logged an error 

![](https://github.com/krzysztofzablocki/KZLinkedConsole/raw/master/logs.gif?raw=true)

  * [XCodeColors](https://github.com/robbiehanson/XcodeColors) \- while would you not want to have colors in your Xcode console? makes error **stand out** so much more

  * [KSImageNamed](https://github.com/ksuther/KSImageNamed-Xcode) \- adds intelisense with preview to your **imageNamed:** calls

![](https://camo.githubusercontent.com/c354bf04524df86daeabe7a6d2b9926fac790f85/68747470733a2f2f7261772e6769746875622e636f6d2f6b7375746865722f4b53496d6167654e616d65642d58636f64652f6d61737465722f73637265656e73686f742e676966)

  * [OMColorSense](https://github.com/omz/ColorSense-for-Xcode) \- adds preview to your UIColors and it even allows you to use Color Picker straight from that to modify the code.

  * [VVDocumenter](https://github.com/onevcat/VVDocumenter-Xcode) \- if you write libraries you should be adding documentation to them, this plugin makes it easy by giving you context-aware templates

![](https://camo.githubusercontent.com/ca5518c9872e15b8a95b9d8c5f44bc331977d710/68747470733a2f2f7261772e6769746875622e636f6d2f6f6e65766361742f5656446f63756d656e7465722d58636f64652f6d61737465722f53637265656e53686f742e676966)

#### Hidden options

Open your terminal and type those:

  * Want to see how long it takes to build your project?
    
    
    defaults write com.apple.dt.Xcode ShowBuildOperationDuration YES
    

  * Better autocompletion with Fuzzy mode?
    
    
    defaults write com.apple.dt.Xcode IDECodeCompletionFuzzyMode 3
    defaults write com.apple.dt.Xcode IDEWorkaroundForRadar6288283 3
    

  * Faster build times by leveraging multi-core CPU ?
    
    
    defaults write com.apple.dt.Xcode IDEBuildOperationMaxNumberOfConcurrentCompileTasks `sysctl -n hw.ncpu`
    

### Other

  * Use [iRamDisk](https://itunes.apple.com/us/app/iramdisk/id492615400?mt=12) to put your Derived Data and iOS Simulator on fastest memory you have. Even on new SSD it makes a difference.
  * Use [KZPlaygrounds](https://github.com/krzysztofzablocki/KZPlayground) to implement your new features faster in both Swift and Objective-C
  * Using interface builder? you probably got annoyed by view being added as a subview everytime you move it? Just hold **cmd** and it won't do that ever again.
