# iOS 9 Slide Over and Split View Multitasking

_Captured: 2015-12-15 at 10:12 from [useyourloaf.com](http://useyourloaf.com/blog/ios-9-slide-over-and-split-view.html)_

One of the most interesting announcements at WWDC 2015 was the news that iOS 9 will support multi-tasking on the iPad with two apps running side by side in Slide Over or Split View modes. This post summarises what you need to know to get your app ready to support these new modes.

_Information in this post is based on the first beta release of iOS 9_

### Prerequisites to Adopt Split View and Slide Over

Enabling an existing app to run in these new Split View or Slide Over multitasking modes _requires_ three things:

  * Build with the iOS 9 SDK
  * Support all device orientations
  * Use [launch storyboards](http://useyourloaf.com/blog/using-a-launch-screen-storyboard.html)

That is all. Note there is no requirement to use autolayout though that might help your views adapt to the new configurations. Also remember that this only currently works on the iPad Air 2 (though we can expect it will also work on any new larger iPads Apple may introduce in the future).

### Trying It Out

I did a very quick test using my [WorldFacts sample project](https://github.com/kharrison/CodeExamples/tree/master/WorldFacts). This project already supports all iPad orientations and has a launch storyboard. It also uses a `UISplitViewController` that does most of the hard work of adapting to the compact and regular size classes introduced in iOS 8.

The only missing step was to rebuild using the Xcode 7 beta and iOS 9. Once complete I can report that it does indeed run fine in both slide over and split screen modes. It is interesting to see an App using a UISplitView in a split view with a second App.

Of course this was an easy test so your mileage may vary depending on how adaptive your app is to having views change their bounds.

### A More Detailed Look

I will avoid posting any actual screenshots of the beta for now but it is interesting to take a closer look at the different application states we can now achieve on iOS 9.

#### Landscape Full Screen

Let's start from the familiar iPad landscape orientation with the app filling the whole screen:

![Full Screen](http://useyourloaf.com/assets/images/2015/2015-06-15-001.png)

> _Full Screen_

The primary app horizontal size class and bounds are as follows:

  * Horizontal Size Class: regular
  * Window Bounds: w:1024 h:768
  * Screen Bounds: w:1024 h:768

Note that the window and main screen bounds are the same and as with iOS 8 they take the [device orientation into account](http://useyourloaf.com/blog/uiscreen-bounds-in-ios-8.html).

#### Landscape Slide Over

Swiping in from the right hand edge allows us to select another application to slide over the current full screen app. Tapping the divider causes the primary app to resize so that both apps are running side by side:

![Slide Over](http://useyourloaf.com/assets/images/2015/2015-06-15-002.png)

> _Slide Over_

The horizontal size class of our primary application does not change but the width of the application window shrinks. This is first time on iOS that I have seen a window size that is smaller than the main screen:

  * Horizontal Size Class: regular
  * Window Bounds: w:694 h:768
  * Screen Bounds: w:1024 h:768

#### Landscape Split View

If we continue to slide the secondary app we end up in the split view configuration:

![Split View](http://useyourloaf.com/assets/images/2015/2015-06-15-003.png)

> _Split View_

This time we do see a change in the horizontal size class from regular to compact and the window width shrinks a little more:

  * Horizontal Size Class: compact
  * Window Bounds: w:507 h:768
  * Screen Bounds: w:1024 h:768

#### Portrait Split View

From either the slide over or split view positions we can rotate the device to portrait and get a variation on the split view:

![Portrait Split View](http://useyourloaf.com/assets/images/2015/2015-06-15-004.png)

> _Portrait Split View_

This also gives our primary app a compact horizontal size class with an even narrower window width:

  * Horizontal Size Class: compact
  * Window Bounds: w:438 h:1024
  * Screen Bounds: w:768 h:1024

#### Opting Out

If for some reason you want to opt out of allowing your iOS 9 app from being presented in slide over or split view configurations you need to set the `UIRequiresFullScreen` key to `YES` in your targets plist file (or check the Requires full screen box in the General tab of the target settings):

![UIRequiresFullScreen](http://useyourloaf.com/assets/images/2015/2015-06-15-006.png)

If you think you have met all the prerequisites and multi-tasking is not working double check you don't have this set by mistake. Note that a user can still slide a second app over an app that has opted out but it is not possible to then switch to the side by side mode with both apps active.

### More Information

When iOS 9 ships in a few months time iPad Air 2 users (and perhaps owners of new iPad Pros) are going to expect apps to play well in these new multitasking modes. If your app does not allow side-by-side operation it is going to look out of date. At first glance it does not look like it will take most developers long to add support. For more information take a look at the WWDC videos [Getting Started with Multitasking on iPad in iOS 9](https://developer.apple.com/videos/wwdc/2015/?id=205) and [Optimizing Your App for Multitasking on iPad in iOS 9](https://developer.apple.com/videos/wwdc/2015/?id=212).
