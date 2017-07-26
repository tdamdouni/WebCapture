![iPhone Development 101](/ilogo.gif)

[Home](/)  

iPhone 101

[Learning iPhone Programming](/learn_iphone_programming.html)  

Code Tips

[Objective-C](/code/Objective-C/)  
[User Interface](/code/User_Interface/)  
[Distribution](/code/Distribution/)  
[Marketing](/code/Marketing/)  

Resources

[Buttons & Icons](/icons.html)  
[Open Source Libraries](/libraries.html)  
![](/app/icon80x80.png)  
[Quick Reference App](/app/)

Links

[Apple: iOS Dev Center](http://developer.apple.com/ios/)  
[Conferences & Classes](/conferences.html)  
[More...](/#links)  

Follow

[Twitter](http://twitter.com/idev101) • [RSS](http://feeds.feedburner.com/idev101) • [E-mail](http://feedburner.google.com/fb/a/mailverify?uri=idev101&loc=en_US)

More

[Contact](mailto:kira@lightsphere.com)  
[Search This Site](/search.html)

##  [iPhone Development 101:](/) [User Interface:](/code/User_Interface/)   
Sizes of iPhone UI Elements 

![](img/fourPhones.jpg)

How to detect the [current device size](deviceSizes.html) and kind 

Element iPhone 4S (and earlier) iPhone 5 iPhone 6 iPhone 6 Plus

Window (including status bar area)

320 x 480 pts

320 x 568 pts

375 x 667 pts

414 x 736 pts

iOS8 Portrait [Keyboard](keyboard.html) (English)  
with QuickType

320 x 253 pts 

320 x 253 pts 

375 x 258 pts

414 x 271 pts

iOS8 Portrait [Keyboard](keyboard.html) (English)  
without QuickType

320 x 224 pts 

320 x 224 pts 

375 x 225 pts 

414 x 236 pts 

iOS8 Landscape [Keyboard](keyboard.html) (English)   
with QuickType

480 x 193 pts 

568 x 193 pts 

667 x 194 pts

736 x 194 pts

iOS8 Landscape [Keyboard](keyboard.html) (English)   
without QuickType

480 x 170 pts 

568 x 170 pts 

667 x 171 pts

736 x 171 pts

[Launch Image Sizes](launchImages.html)

640 x 960 pixels

640 x 1136 pixels

750 x 1334 (@2x) portrait  
1334 x 750 (@2x) landscape

1242 x 2208 (@3x) portrait  
2208 x 1242 (@3x) landscape

![](/app/icon80x80.png)

This page is available as an interactive version in the [idev101 app](/app/)!

Other dimensions common to all screen sizes: 

Status Bar  
([How to hide the status bar](UIStatusBar.html))

20 pts 

Navigation Bar 

44 pts 

Nav Bar/Toolbar Icon

white icon - up to 20 x 20 pts (transparent PNG) 

Tab Bar

49 pts

Tab Bar Icon

up to 30 x 30 pts (transparent PNGs)

Text Field 

31 pts

### Points vs. Pixels

Apple introduced retina displays starting with the iPhone 4. You don't have to modify your code to support high-res displays; the iOS coordinate system uses points rather than pixels, so the dimensions and position in points of all UI elements remains the same across all devices. 

iOS supports high resolution displays via the scale property on UIScreen, UIView, UIImage, and CALayer classes. If you load an image from a file whose name includes the @2x modifier, its scale property is set to 2.0. Similarly an image with a @3x modifier has a scale of 3.0. Otherwise the scale defaults to 1.0. 

### Retina Graphics

To support high-resolution graphics on devices with retina displays, create two versions of the image: a standard size image, and a double-sized image with "@2x" added to the name: 

Standard Size:

High Resolution:

![](img/homeSmall.png)  
**button.png**  
60 x 20 

![](img/homeBig.png)  
**button@2x.png**  
120 x 40 

To refer to an image in your code (or in Interface Builder), use the filename of the standard sized image. iOS will automatically detect and use the @2x version if the device supports it: 

    
    
    imageView.image = [UIImage imageNamed:@"button.png"];
    

### Adjusting Sizes

Click here to see how to adjust [View Frames and Bounds](view_frames_bounds.html). 

### Additional References

  * Apple Documentation: [Points vs. Pixels](http://developer.apple.com/library/ios/documentation/2DDrawing/Conceptual/DrawingPrintingiOS/GraphicsDrawingOverview/GraphicsDrawingOverview.html#//apple_ref/doc/uid/TP40010156-CH14-SW7)
  * Apple Documentation: [UIBarButtonItem Class Reference](http://developer.apple.com/iphone/library/documentation/UIKit/Reference/UIBarButtonItem_Class/Reference/Reference.html#//apple_ref/doc/uid/TP40007519-CH3-SW3) says "Typically, the size of a toolbar and navigation bar image is 20 x 20 points."
  * Apple Documentation: [UITabBarItem Class Reference](http://developer.apple.com/iphone/library/documentation/UIKit/Reference/UITabBarItem_Class/Reference/Reference.html#//apple_ref/occ/instm/UITabBarItem/initWithTitle:image:tag:) says "The size of an tab bar image is typically 30 x 30 points."
  * Apple Documentation: [Supporting High-Resolution Screens](https://developer.apple.com/library/ios/documentation/2DDrawing/Conceptual/DrawingPrintingiOS/SupportingHiResScreensInViews/SupportingHiResScreensInViews.html)
  * Apple Documentation: [Icon and Image Sizes](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/IconMatrix.html)
  * [iPhone 6 Technical Specs](https://www.apple.com/iphone-6/specs/)   

[Top](javascript:window.scrollTo\(0,0\)) • [Home](/)

Site design, writing, and code by [Kira](http://www.lightsphere.com/). (C) 2009-2016.  
