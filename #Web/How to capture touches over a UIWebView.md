# How to capture touches over a UIWebView

_Captured: 2016-06-01 at 01:06 from [wyldco.com](http://wyldco.com/blog/2010/11/how-to-capture-touches-over-a-uiwebview/)_

**This post was updated with corrections to work with iOS5.**

I spent the last few weeks polishing the What They Speak When They Speak to Me (WTS) iOS application I developed with Obx Labs, which I mentioned in a [previous post](http://wyldco.com/blog/2010/09/coding-portable-poetry/). Developing a working prototype for an iOS application can be done fairly quickly, thanks to the tools provided by Apple and a growing list of libraries and engines, but the more time consuming part of development takes place later, working with and often against the features embedded in the iOS SDK to polish your product. This how-to is about one specific issue that arose during the development of WTS: capturing touches over a UIWebView without losing its functionality.

This short tutorial assumes that you know how to place a UIWebView (or other touch swallowing views) in your app, and that you are at the frustrating point of trying to catch touch events over the Web View to implement some interactive behaviour. In my case, I wanted to swipe the Web View left and right to show or hide it, similarly to how the Twitter for iPad app manages its browser tab.

We'll start from scratch and go through the following four steps. You can jump to step 4 if you're looking for the meat of this tutorial.

  1. Create a new XCode project using the "View-based application" template.
  2. Add the standard methods to manage touch events.
  3. Add a UIWebView covering the main view.
  4. Add a custom class that extends UIWindow to capture touch events.

**1\. Create a new XCode project using the "View-based application" template.**

This step is self explanatory. From XCode you select from the main menu: File > New Project, and them "View-based Application" which is under the "Application" template folder. This is here mainly to have a common code base from which to start the tutorial; I named the project "CaptureTouch".

**2\. Add the standard methods to manage touch events.**

Before we get to the problematic UIWebView, we want to make sure that touch events get to the application's main standard view. The new project you created in step 1 should contain a view controller named CaptureTouchViewController. In the implementation file of this view controller, add the four standard touch management methods:

010203040506070809101112
`\- (``void``) touchesBegan:(``NSSet``*)touches withEvent:(UIEvent*)event {``NSLog``(``@"Touches began"``);``}``\- (``void``) touchesMoved:(``NSSet``*)touches withEvent:(UIEvent*)event {``NSLog``(``@"Touches moved"``);``}``\- (``void``) touchesEnded:(``NSSet``*)touches withEvent:(UIEvent*)event {``NSLog``(``@"Touches ended"``);``}``\- (``void``) touchesCancelled:(``NSSet``*)touches withEvent:(UIEvent*)event {``NSLog``(``@"Touches cancelled"``);``}`

At this point, if you build and run the application, you should see a gray background (the view), and clicking anywhere on the background will output "Touch began" to the console.

**3\. Add a UIWebView that covers the main view.**

As mentioned before, we assume you know how the UIWebView works, so we won't get into too much detail. All we need is the simplest UIWebView covering the application's main view. We will add the UIWebView in the .xib file created by XCode, but first we need to add an attribute and outlet to the CaptureTouchViewController. Your CaptureTouchViewController.h file should then look like the following:

`@interface` `CaptureTouchViewController : UIViewController {``UIWebView* webView;``}``@property` `(``nonatomic``, retain) ``IBOutlet` `UIWebView *webView;``@end`

With the outlet created, you can open the CaptureTouchViewController.xib file in Interface Builder. Open the "View" object, and then drag-and-drop a new Web View into it. The Web View should automatically expand to cover the whole view. Right-click on the Web View, and then link a "New Referencing Outlet" with the "webView" attribute you created above by clicking the "New Referencing Outlet", dragging to the "File's Owner" object, and then selecting the "webView" from the list that pops up.

At this point, you linked the interface to the "webView" attribute, but it is not loading any html. We will need one last bit of code before we get to the core of this tutorial, which will load a url to make sure the Web View is working correctly. After the application's main view finished loading, the CaptureTouchViewController's viewDidLoad: method is called. This is where we add the few lines that will load a url into the web view. Your viewDidLoad: method should look like the following after the changes:

12345678
`\- (``void``)viewDidLoad {``[``super` `viewDidLoad];``//Load the request in the UIWebView.``NSURL` `*url = [``NSURL` `URLWithString:``@"<http://www.wyldco.com>"``];``NSURLRequest` `*requestObj = [``NSURLRequest` `requestWithURL:url];``[webView loadRequest:requestObj];``}`

If you build and run the application, you should see the web page. Everything looks fine, but if you touch anywhere on the screen, you'll notice that the "Touch began" message from step 2 does not appear in the console anymore. The Web View swallows the touches to manage scrolling and displaying the magnifying glass if you hold down a touch over text, and it blocks touch events from getting to the view. The next step shows how to capture those touch events.

**4\. Add a custom class that extends UIWindow to capture touch events.**

There are different ways to capture touches over a Web View. One would be to extend the UIWebView class, but Apple says you should not, so we will stay away from that solution in case it causes problem later. Instead, we are going to extend the UIWindow class, and capture touch events before they get propagated to the correct view(s). The first thing you'll need is a new class, let's call it TouchCapturingWindow, with the following header and implementation files:

TouchCapturingWindow.h

01020304050607080910111213
`#import <Foundation/Foundation.h>``@interface` `TouchCapturingWindow : UIWindow {``NSMutableArray` `*views;``@private``UIView *touchView;``}``\- (``void``)addViewForTouchPriority:(UIView*)view;``\- (``void``)removeViewForTouchPriority:(UIView*)view;``@end`

This class is heavily inspired by [Michael Tyson's tutorial](http://atastypixel.com/blog/a-trick-for-capturing-all-touch-input-for-the-duration-of-a-touch/), with a few changes and some added notes about the implementation. Here's how it works. The TouchCapturingWindow overrides the sendEvent: method of UIWindow to check if touch events should be sent to certain views instead of only the top view, which is more or less the default behaviour. If you intend to have multiple views in your application, you probably don't want to have all of them capture touch events, so the TouchCapturingWindow provides methods (i.e. addViewForTouchPriority: and removeViewForTouchPriority:) to add and remove the specific view(s) you want to touch. Once you've replaced the standard UIWindow with an instance of this custom class, touch events will go through the sendEvent: method, and allow you to redirect them to the correct view(s) based on any criteria. In the above case, the only criteria is if the touch falls inside the frame of any of the views that were added to the TouchCapturingWindow.

First, you need to change the default "window" of your application's delegate to use the new custom class. Open the CaptureTouchAppDelegate.h file, and replace the UIWindow class by TouchCapturingWindow; don't forget to import the header, which should give you something like this:

After you changed the window in the code, you'll need to adjust the MainWindow.xib to also reflect this change. Open MainWindow.xib, and change the class of its window object from UIWindow to the new TouchCapturingWindow.

Now that the window can propagate touch events the way we want, we need to tell it which view to prioritize. In this case, we want the application's main view to receive the touch events that would normally be blocked by the Web View covering it. To add the view to the priority list, you'll need to modify the applicationDidFinishLaunchingWithOptions: method of the CaptureTouchAppDelegate. Just after the window is made visible, add the view using the new addViewForTouchPriority: method, which should give you the following:

**Conclusion**

At this point, if you run the application, you can see that touching anywhere on the Web View outputs the "Touch began" message of step 2. You can now use the touch events to add some touch-based interaction to your application, but be careful not to conflict with the Web View's features such as scrolling and text selection.

At the beginning I mentioned that I wanted to keep all the Web View's features. This is accomplished by one short but important line of code. In the sendEvent: method of the new TouchCapturingWindow class, the line [super sendEvent:event] assures that the Web View receives the event before we propagate it to the main view. As of iOS5, placing that line at the beginning of the method stopped working, and it now needs to be at the end of the method. Placing it at the end keeps all the Web View's features for iOS5, but does not show them for devices with [super sendEvent:event];

On a final note, if you look at the sendEvent: method, you'll notice that touch events are propagated to a view only if the location of the touch is inside the frame of the view. This is a common behaviour, but there is no reason why you should always stick to it. You might want to check the state of a view to decide if the view should receive touches, control the view by touching outside its visual frame, or send event to a specific view only after the user tapped around up, up, down, down, left, right, left, right…

**Related links**  
[Michael Tyson's (A Tasty Pixel) trick for capturing all touch input](http://atastypixel.com/blog/a-trick-for-capturing-all-touch-input-for-the-duration-of-a-touch/)  
[Satoshi Nakagawa's WebViewTappingHack](https://github.com/psychs/iphone-samples/tree/master/WebViewTappingHack/)  
[Mithin Kumar's post on detecting taps and events on UIWebView - The right way](http://mithin.in/2009/08/26/detecting-taps-and-events-on-uiwebview-the-right-way/)
