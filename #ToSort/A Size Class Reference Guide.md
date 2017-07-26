# A Size Class Reference Guide

_Captured: 2015-12-15 at 10:12 from [useyourloaf.com](http://useyourloaf.com/blog/size-classes.html)_

Apple introduced the concept of adaptive user interfaces in iOS 8 relying on a combination of Auto Layout and size classes. Building user interfaces that adapt to changes in size class became even more important when Apple added slide over and split screen support in iOS 9.

The _iOS Human Interface Guidelines_ describe the size classes used by full screen iPad and iPhone devices but do not (yet) include the various slide over and split screen combinations. In any case finding or remembering the details is tricky so after a few minutes with OmniGraffle here, for future reference, is my guide:

### Size Classes

There are two size classes that can apply to the horizontal (width) or vertical (height) dimension of an application interface:

  * **regular:** meaning your interface has _expansive_ space.
  * **compact:** meaning your interface has only _constrained_ space.

### iPhone 6 Plus

The iPhone 6 Plus is the only iPhone device that has a **regular width** in landscape orientation. The longest dimension is always regular and the shortest dimension is always compact.

![Size Classes iPhone 6 Plus](http://useyourloaf.com/assets/images/2015/SizeClasses-iPhone6Plus.png)

> _Size Classes iPhone 6 Plus_

### All Other iPhone Models

The other iPhone models have a trickier set of size classes to remember. The longest dimension of the device is **regular** in portrait but only **compact** in landscape.

![Size Classes iPhone](http://useyourloaf.com/assets/images/2015/SizeClasses-iPhone.png)

> _Size Classes iPhone_

### iPad

A **full screen** iPad application always has **regular** height and width size classes regardless of orientation.

![Size Classes iPad](http://useyourloaf.com/assets/images/2015/SizeClasses-iPad.png)

> _Size Classes iPad_

### iPad Split Screen and Slide Over

The multi-tasking views introduced in iOS 9 complicate the situation for the iPad. For the first time an iPad application can find it itself running with a compact horizontal size class. Another assumption that no longer holds is that the window and screen bounds will always be the same. I cover the details in an earlier post on [iOS 9 slide over and split view](http://useyourloaf.com/blog/ios-9-slide-over-and-split-view.html).

![Size Classes Slide Over Portrait](http://useyourloaf.com/assets/images/2015/SizeClasses-SlideOverP.png)

> _Size Classes Slide Over Portrait_

![Size Classes Slide Over Landscape](http://useyourloaf.com/assets/images/2015/SizeClasses-SlideOverL.png)

> _Size Classes Slide Over Landscape_

![Size Classes Split Screen](http://useyourloaf.com/assets/images/2015/SizeClasses-SplitScreen.png)

> _Size Classes Split Screen_

### Further Reading

  


## 2015
