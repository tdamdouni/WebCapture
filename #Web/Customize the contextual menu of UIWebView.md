# Customize the contextual menu of UIWebView

_Captured: 2015-11-22 at 21:36 from [www.icab.de](http://www.icab.de/blog/2010/07/11/customize-the-contextual-menu-of-uiwebview/)_

When you tap and hold your finger on a link in a UIWebView object for about a second, a contextual menu will open and provides a few choices: copy the URL to the pasteboard, open the link and a button to close the menu again. Unfortunately there's no API available to add additional menu items to this contextual menu. But if you look at iCab Mobile, you'll notice that there are a lot of additional menu items here. How is this done?

First of all, you really can't add additional menu items to the default ones of the standard contextual menu. But you can switch off the contextual menu using a certain CSS property. So the solution would be to switch off the default menu and implement your own from scratch. And to implement your own contextual menu, you have to first catch the tab-and-hold gesture, get the coordinates of the finger on the screen, translate these coordinates into the coordinate system of the web page and finally look for the HTML elements at this location. Based on the HTML elements, you can then decide which menu items to include in the contextual menu, and then create and display the contextual menu.

The first step is to switch off the default contextual menu of UIWebView. This is easy because we only need to set the CSS property "-webkit-touch-callout" to "none" for the body element of the web page. We can do this using JavaScript in the UIWebView delegate method "webViewDidFinishLoad:"…
    
    
    - (void)webViewDidFinishLoad:(UIWebView *)webView
    {
       [webView stringByEvaluatingJavaScriptFromString:@"document.body.style.webkitTouchCallout='none';"];
    }

Now, the default Contextual menu won't open anymore.

The next step is to catch the "tap-and-hold" gesture. If your App only needs to run on iOS 3.2, iOS 4.0 or newer, you can simply use the new UIGestureRecognizer API. But if you still want to address the 1st generation iPod Touch and iPhone devices (where you can install at most iOS 3.1) where these UIGestureRecognizer classes are not available, you need to do a little bit more. I'll show here a solution which will work with iOS 3.0 as well, so it's compatible to all iPhone, iPad and iPod Touch devices.

A big problem when you need to catch gestures within UIWebView is that UIWebView internally consists of many nested views, and only the inner ones do respond to events and gestures. Which means, if you subclass UIWebView and overwrite the methods "touchesBegan:withEvent:", "touchesMoved:withEvent:" etc., you'll notice that these methods won't be called. The events are delivered directly to these private inner views which are actually doing all the work. And if you overwrite "hitTest:withEvent:", which is used by the iOS to find the view to which the events will be delivered, you would be able to get the touch events, but then you would have to deliver the events to these inner views yourself so these can still do their work. And because these inner views are private and the relationships between these views are unknown, it can be extremely dangerous to mess with the events here.

A much easier way would be to subclass UIWindow and overwrite the method "sendEvent:" of the UIWindows class. Here you'll get all events before they are delivered to the views. And we can deliver the tap-and-hold events using the notification manager to the rest of the app. Each object that is interested in this gesture can listen to this notification.

Recognizing the tap-and-hold gesture is not very complicated. What we need to do is to save the screen coordinates of the finger when the finger first touches the screen. At that time we will also start a timer which fires after about a second. As soon as another finger touches the screen, the finger moves or the touch event is canceled, we invalidate the timer because then it can not be a simple tap-and-hold gesture anymore. If the timer fires, we can be sure that a single finger has touched the screen for about a second without moving and then we've recognized the "tap-and-hold" gesture. We post the gesture as notification.

This is the implementation of the UIWindow subclass:

MyWindow.h:
    
    
    @interface MyWindow : UIWindow
    {
       CGPoint    tapLocation;
       NSTimer    *contextualMenuTimer;
    }
    @end

MyWindow.m:
    
    
    #import "MyWindow.h"
    
    @implementation MyWindow
    
    - (void)tapAndHoldAction:(NSTimer*)timer
    {
       contextualMenuTimer = nil;
       NSDictionary *coord = [NSDictionary dictionaryWithObjectsAndKeys:
                 [NSNumber numberWithFloat:tapLocation.x],@"x",
                 [NSNumber numberWithFloat:tapLocation.y],@"y",nil];
       [[NSNotificationCenter defaultCenter] postNotificationName:@"TapAndHoldNotification" object:coord];
    }
    
    - (void)sendEvent:(UIEvent *)event
    {
       NSSet *touches = [event touchesForWindow:self];
       [touches retain];
    
       [super sendEvent:event];    // Call super to make sure the event is processed as usual
    
       if ([touches count] == 1) { // We're only interested in one-finger events
          UITouch *touch = [touches anyObject];
    
          switch ([touch phase]) {
             case UITouchPhaseBegan:  // A finger touched the screen
                tapLocation = [touch locationInView:self];
                [contextualMenuTimer invalidate];
                contextualMenuTimer = [NSTimer scheduledTimerWithTimeInterval:0.8
                            target:self selector:@selector(tapAndHoldAction:)
                            userInfo:nil repeats:NO];
                break;
    
             case UITouchPhaseEnded:
             case UITouchPhaseMoved:
             case UITouchPhaseCancelled:
                [contextualMenuTimer invalidate];
                contextualMenuTimer = nil;
                break;
          }
       } else {                    // Multiple fingers are touching the screen
          [contextualMenuTimer invalidate];
          contextualMenuTimer = nil;
       }
       [touches release];
    }
    @end

Some remarks for the UITouchPhaseMoved phase: it can be sometimes useful to allow small movements on the screen. You can add some code to check for the distance the finger has moved and if it is within a certain range, you just don't abort the timer. This helps users which have difficulties to hold the finger still for about a second.

Another important thing you have to do when the App window is created by a NIB file: you have to change the UIWindow class of the window within the NIB file in Interface Builder to the new subclass MyWindow. This way the window is created with our subclass, which is important.

The next step is to listen for the "TapAndHoldNotification" notification within the UIWebView delegate and when this notification is received, we need to check which HTML element was touched.

When initializing the UIWebView delegate, we need to add the delegate as observer for the notification…
    
    
       [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(contextualMenuAction:) name:@"TapAndHoldNotification" object:nil];
    }

And here's the method "contextualMenuAction:"…
    
    
    - (void)contextualMenuAction:(NSNotification*)notification
    {
       CGPoint pt;
       NSDictionary *coord = [notification object];
       pt.x = [[coord objectForKey:@"x"] floatValue];
       pt.y = [[coord objectForKey:@"y"] floatValue];
    
       // convert point from window to view coordinate system
       pt = [webView convertPoint:pt fromView:nil];
    
       // convert point from view to HTML coordinate system
       CGPoint offset  = [webView scrollOffset];
       CGSize viewSize = [webView frame].size;
       CGSize windowSize = [webView windowSize];
    
       CGFloat f = windowSize.width / viewSize.width;
       pt.x = pt.x * f + offset.x;
       pt.y = pt.y * f + offset.y;
    
       [self openContextualMenuAt:pt];
    }

The method "scrollOffset" and "windowSize" are implemented as category for the UIWebView class. "scrollOffset" is required to make sure the coordinates are also correct when the web page was scrolled. The "windowSize" returns the visible width and height of the HTML document from the point of view of the HTML document. So based on the windowsSize of the "HTML window" and the view size of the UIWebView, you can calculate the zoom factor, and the zoom factor is necessary to transform and scale the screen coordinates to the correct HTML coordinates.

Here's the implementation of "scrollOffset" and "windowSize"…

WebViewAdditions.h:
    
    
    @interface UIWebView(WebViewAdditions)
    - (CGSize)windowSize;
    - (CGPoint)scrollOffset;
    @end

WebViewAdditions.m:
    
    
    #import "WebViewAdditions.h"
    
    @implementation UIWebView(WebViewAdditions)
    
    - (CGSize)windowSize
    {
       CGSize size;
       size.width = [[self stringByEvaluatingJavaScriptFromString:@"window.innerWidth"] integerValue];
       size.height = [[self stringByEvaluatingJavaScriptFromString:@"window.innerHeight"] integerValue];
       return size;
    }
    
    - (CGPoint)scrollOffset
    {
       CGPoint pt;
       pt.x = [[self stringByEvaluatingJavaScriptFromString:@"window.pageXOffset"] integerValue];
       pt.y = [[self stringByEvaluatingJavaScriptFromString:@"window.pageYOffset"] integerValue];
       return pt;
    }
    @end

Finally, we need to implement the method "openContextualMenuAt:" for the UIWebView delegate, which first checks for the HTML elements that are at the touch locations and the creates the contextual menu. Checking for the HTML elements at the touch location must be done via JavaScript…

JSTools.js
    
    
    function MyAppGetHTMLElementsAtPoint(x,y) {
       var tags = ",";
       var e = document.elementFromPoint(x,y);
       while (e) {
          if (e.tagName) {
             tags += e.tagName + ',';
          }
          e = e.parentNode;
       }
       return tags;
    }

This JavaScript function simply collects the tag names of all HTML elements at the touch coordinates and returns the tag names as string list. The JavaScript file must be added as "resource" to your XCode project. It can happen that Xcode treats JavaScript file as normal code and tries to compile and link it instead of adding it to the resources. So make sure the JavaScript file is in the "Copy Bundle Resources" section within the XCode project target and not in the "Compile Sources" or "Link Binaries" section.
    
    
    - (void)openContextualMenuAt:(CGPoint)pt
    {
       // Load the JavaScript code from the Resources and inject it into the web page
       NSString *path = [[NSBundle mainBundle] pathForResource:@"JSTools" ofType:@"js"];
       NSString *jsCode = [NSString stringWithContentsOfFile:path encoding:NSUTF8StringEncoding error:nil];
       [webView stringByEvaluatingJavaScriptFromString: jsCode];
    
       // get the Tags at the touch location
       NSString *tags = [webView stringByEvaluatingJavaScriptFromString:
                [NSString stringWithFormat:@"MyAppGetHTMLElementsAtPoint(%i,%i);",(NSInteger)pt.x,(NSInteger)pt.y]];
    
       // create the UIActionSheet and populate it with buttons related to the tags
       UIActionSheet *sheet = [[UIActionSheet alloc] initWithTitle:@"Contextual Menu"
                      delegate:self cancelButtonTitle:@"Cancel"
                      destructiveButtonTitle:nil otherButtonTitles:nil];
    
       // If a link was touched, add link-related buttons
       if ([tags rangeOfString:@",A,"].location != NSNotFound) {
          [sheet addButtonWithTitle:@"Open Link"];
          [sheet addButtonWithTitle:@"Open Link in Tab"];
          [sheet addButtonWithTitle:@"Download Link"];
       }
       // If an image was touched, add image-related buttons
       if ([tags rangeOfString:@",IMG,"].location != NSNotFound) {
          [sheet addButtonWithTitle:@"Save Picture"];
       }
       // Add buttons which should be always available
       [sheet addButtonWithTitle:@"Save Page as Bookmark"];
       [sheet addButtonWithTitle:@"Open Page in Safari"];
    
       [sheet showInView:webView];
       [sheet release];
    }

This method injects the JavaScript code which looks for the HTML elements at the touch location into the web page and calls this function. The return value will be a string with a comma-separated list of tag names. This string will start and end with a comma so we can simply check for occurrences of a substring ",tagName," if we want to find out if an element with a certain tag name was touched. In our example, we simple add some buttons if an "A" tag was hit and some other buttons if and "IMG" tag was hit. But what you're doing is up to you. Also the information that is returned from the JavaScript function (in this example "MyAppGetHTMLElementsAtPoint()") is up to you. In iCab Mobile it returns the HREF and SRC attributes of A and IMG tags, so the URLS can be directly processed.

The example doesn't include the UIActionSheet delegate method which is called when you tab on one of the buttons in the contextual menu. But I think you should already know how to handle this. Also a few other details might be missing, but I think you should be able now to implement your own custom contextual menu for UIWebView objects with the information from the blog post.

[168 comments](http://www.icab.de/blog/2010/07/11/customize-the-contextual-menu-of-uiwebview/#comments)
