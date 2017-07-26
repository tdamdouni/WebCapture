# How To Use Shadows And Blur Effects In Modern UI Design

_Captured: 2017-02-22 at 12:13 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)_

  * [0 Comments](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

When you examine the most successful interaction designs of recent years, the clear winners are those who provide an excellent functionality. While functional aspect of a design is key to product success, aesthetics and visual details are equally important -- particularly how they can improve those functional elements.

In today's article, I'll explain how visual elements, such as shadows and blur effects, can improve the functional elements of a design. If you'd like to try adding these elements to your designs, you can download and test [Adobe XD](https://adobe.ly/2knsUsI) **for free** and get started right away.

There's a reason GUI designers incorporate shadows into their designs -- they help create _visual cues_ in the interface which tell human brains _what user interface elements_ they're looking at.

Since the early days of graphical user interfaces, screens have employed shadows to help users understand how to use an interface. Images and elements with shadows seem to pop off of a page, and it gives users the impression that they can physically interact with the element. Even though visual cues vary from app to app, users can usually rely on two assumptions:

  * Elements that appear raised look like they could be pressed down (clicked with the mouse or tapped with a finger). This technique is often used as a visual signifier for buttons.
  * Elements that appear sunken look like they could be filled. This technique is often used as a visual signifier for input fields.

You can see how the use of shadows and highlights help users understand which elements are interactive in this Windows 2000 dialog box:

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/1-preview-opt.jpg)[2](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Perceived possibility of action: notice how the buttons appear raised. (_

Modern interfaces are layered and take full advantage of the z-axis. The position of several objects in the z-axis act as important cues to the user.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/2-preview-opt.png)[4](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _The z-axis is perpendicularly aligned to the plane of the display, with the positive z-axis extending towards the viewer. Image credit:_

Shadows help indicate the hierarchy of elements by differentiating between two objects. Also, in some cases, shadows help users understand that one object is above another.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/3-preview-opt.png)[7](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Image credit: Material Design (Large preview)_

Why is it so important to visualize the position of an element within three-dimensional space? The answer is simple -- laws of physics.

Everything in the physical world is dimensional, and elements interact in three-dimensional space with each other: they can be stacked or affixed to one another, but cannot pass through each other. Objects also cast shadows and reflect light. The understanding of these interactions is the basis for our understanding of the graphical interface.

Let's have a look at Google's Material Design for a moment. A lot of people still call it flat design, but the key feature is that it has _dimension_ -- the use of consistent metaphors and principles borrowed from physics help users make sense of interfaces and interpret visual hierarchies in context.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/9.1-preview-opt.png)[10](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _The laws of physics are deeply integrated in our cognition: without a larger shadow, nothing indicates that the round yellow circle is separate from the background surface. Image credit: [Google](https://developers.googleblog.com/2014/06/this-is-material-design.html)[11](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/) ([Large preview](https://www.smashingmagazine.com/wp-content/uploads/2017/02/9.1-large-opt.png)[12](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/))  
_

One very important thing about shadows is that they work in tandem with _elevation_. The elevation is the relative depth, or distance, between two surfaces along the z-axis. Measured from the front of one surface to another, an element's elevation indicates the _distance_ between surfaces and the _depth_ of its shadow. As you can see from the image below, the shadow gets bigger and blurrier the greater the distance between object and ground.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/5-preview-opt.jpg)[13](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Elevation in Material Design: z-depth = 1 is very close to the ground, z-depth = 5 is far away from the ground. (Large preview)_

Some elements like **buttons** have dynamic elevation, meaning they change elevation in response to user input (e.g., normal, focused, and pressed). Shadows provide useful clues about an object's direction of movement and whether the distance between surfaces is increasing or decreasing. For users to feel confident that something is clickable or tappable, they need immediate reassurance after clicking and tapping, which elevation provides through visual cues:

![An illustration that simulates the physical impact of a button that is being clicked, using an animated shadow](https://www.smashingmagazine.com/wp-content/uploads/2017/02/object-elevation-shadow-opt.gif)[15](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _An object's elevation determines the appearance of its shadow. The values shown are for Android apps. Image credit: Behance_

When Apple introduced iOS 8, it raised the bar for app design, especially when it came to on-screen effects. One of the most significant changes was the use of blur throughout, most notably in Control Center; when you swipe up from the bottom edge of a screen you reveal the Control Center, and the background is blurred. This blur occurs in an interactive fashion, as you control it completely with the movement of your finger.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/7-preview-opt.jpg)[16](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Control Center in Apple iOS. (_

Apple moved further in this direction with the latest version of iOS which uses 3D Touch for the flashlight, camera, calculator and timer icons. When a user's hand presses on those icons, real-time blur effect takes place.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/8-preview-opt.jpg)[18](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Large preview_

**Make User Flow Obvious**

Blur effects allow for a certain amount of play within the layers and hierarchy of an interface, especially for mobile apps. It's a very efficient solution when working with layered UI since it gives the user a clear understanding of a mobile app's user flow.

The [Yahoo Weather](https://itunes.apple.com/us/app/yahoo!-weather/id628677149?mt=8) app for iOS displays a photo of each weather location, and the basic weather data you need is immediately visible, with more detailed data only a single tap away. Rather than cover the photo with another UI layer, the app keeps you _in context_ after you tap -- the detailed information is easily revealed, and the photo remains in the background.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/9-preview-opt.jpg)[21](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Blur effect in Yahoo Weather provides contextual awareness to the user about where they are in the navigational hierarchy. (Large preview)_

**Direct the User's Attention**

Humans have a tendency to pay attention to objects that are in focus and ignore objects that aren't. It's a natural consequence of how our eyes work, known as [accommodation reflex](https://en.wikipedia.org/wiki/Accommodation_reflex). App designers can use it to blur unimportant items on the screen in an effort to direct a user's attention directly to the valuable content or critical controls. The [Tweetbot](http://tapbots.com/tweetbot/) app uses blur to draw users attention to what needs to be focused on; the background is barely recognizable, while the focus is on information about accounts and call to action buttons.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/10-preview-opt.png)[25](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Large preview_

**Make Overlaid Text Legible**

The purpose of text in your app is to establish a clear connection between the app and user, as well as to help your users accomplish their goals. Typography plays a vital role in this process, as good typography makes the act of reading effortless, while poor typography turns users off.

In order to maximize the readability of text, you need to create a [proper contrast](https://blogs.adobe.com/creativecloud/xd-essentials-typography-in-mobile-apps/) between the text and background. Blur gives designers a perfect opportunity to make overlaid text legible -- they can simply blur a part of the underlying image. In the example below, you can see a restaurant feed which features the closest restaurants to the user. Immediately, your attention goes to the restaurant images as they feature a darkened blur with text overlay.

> _Image credit: Medium>_

Blurred effect can seamlessly blend into the website design.

**Decorative Background**

Together with full-screen photo backgrounds, frequently used for website decorations, blur backgrounds have found their niche in modern website design. This decorative effect also has a practical value: _by blurring one object, it brings focus to another_. Thus, if you want to emphasize your subject and leave the background out of focus, the blurring technique is the best solution.

The website for Trellis Farm uses an iconic image of a farm to give visitors a sense of place for its website. For added interest, the photo is layered with a great typeface to grab a visitor's attention. The blur is nice because it helps the visitor focus on the text and the next actions to take on the screen.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/12-preview-opt.jpg)[28](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Blur backgrounds are able to focus attention on specified elements. (_

**Progressive Image Loading**

As modern web pages load more and more images, it's good to think of their loading process, since it affects performance and user experience. Using blur effect you can create a progressive image loading effect. One good example is Medium.com, which blurs the post image cover as well as images within the post content until the image is fully loaded. First, it loads a small blurry image (thumbnail) and then makes a transition to the large image.

![A progressively loaded JPG image showing blur first](https://www.smashingmagazine.com/wp-content/uploads/2017/02/progressively-loaded-jpg-image.gif)[30](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _How image loading works on Medium.com_

This technique has two benefits:

  * It helps you serve different images sizes depending on the device that makes the requests, optimizing the weight of the page.
  * The thumbnails are very small (just a few kilobytes) which combined with the blurry effect allows for a better placeholder than a solid color, without sacrificing payload.

If you want to reproduce this effect on your site see the _Resources and Tutorials_ section.

**Testing Websites' Visual Hierarchy**

Blur effect can be used not only as visual design technique but also as a good testing technique for page visual hierarchy.

A blur test is a quick technique to help you determine if your user's eye is truly going where you want it to go. All you need to do is, take a screenshot of your site and add a 5-10 px Gaussian blur in Photoshop. Look at a blurred version of your page (like the Mailchimp example below) and see what elements stand out. If you don't like what's projecting, you need to go back and make some revisions.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/14-preview-opt.jpg)[31](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _The blurring test is technique used to reveal a design's focal point and visual hierarchy. (_

Mailchimp's homepage passes the blur test because the prominent items are the sign-up button and text copy which states the benefits of using the product.

**Overuse of Blurs in Mobile Apps**

Blur effect isn't exactly free. It costs something -- graphics performance and battery usage. Since blurring is a memory bandwidth and power intensive effect, it can affect system performance and battery life. Over-used blurs result in slower apps with largely degraded user experiences.

We all want to create a beautiful design, but at the same time, we can't make users suffer from long loading or empty battery. Blur effects should be used wisely and sparsely -- you need to find a balance between great appearance and the resource utilization. Thus, when using blur effects always check CPU, GPU, Memory and Power usage of your app (see section _Resources and Tutorials_ for more information).

**Blur Effect and Text Readability Issues**

Another factor that you should remember -- blurring is not as dynamic. If your image ever changes, make sure the text is always over the blurry bits. In the example below, you can see what happens when you forget this.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/15-preview-opt.png)[33](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _Subheader text is completely unreadable. (_

**Blur Effect and Content-Heavy Pages**

Blurred background can cause a problem when it is used for screens filled with a lot of content. You can compare two examples below. The screen on the left using blur effect looks dirty, and the text seems unreadable. The screen without blur effect is much clearer.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/02/16-preview-opt.jpg)[35](https://www.smashingmagazine.com/2017/02/shadows-blur-effects-user-interface-design/)

> _When we need to display more content on a page, blurring background may be not so great. Image credits:_

The following resources can help you implement blur effect into your design:

  * In his article "[How Medium Does Progressive Image Loading](https://jmperezperez.com/medium-image-progressive-loading-placeholder/)," Jose M. Perez provides solutions on how to incorporate progressive image loading using blur effect using CSS filters or HTML canvas elements.
  * The article, "[Creating A Blurring Overlay View](http://stackoverflow.com/questions/17041669/creating-a-blurring-overlay-view)," provides examples of applying the blur effect to images in Apple iOS 8+ using the UIVisualEffectView class, with both Objective-C and Swift code samples. This is a native API that has been fine-tuned for performance and great battery life.
  * In his article, "[iOS App Performance: Instruments And Beyond Igor Mandrigin](https://medium.com/@mandrigin/ios-app-performance-instruments-beyond-48fe7b7cdf2#.y7dpuock4)," show how to measure performance of the different areas of the app.

Shadows and blur effects provide visual cues that allow users to better and more easily understand what is occurring. In particular, they allow the designer to inform users on objects' relationships with each other, as well as potential interactions with these objects. When carefully applied, such elements can (and should) improve a functional aspect of design.

> This article is part of the UX design series sponsored by Adobe. The newly introduced [Experience Design app](https://adobe.ly/2knsUsI) is made for a fast and fluid UX design process, as it lets you go from idea to prototype faster. Design, prototype and share -- all in one app.
> 
> You can check out more inspiring projects created with Adobe XD on [Behance](https://www.behance.net/search?content=projects&sort=appreciations&time=week&tools=387566349), and also visit the [Adobe XD blog](https://blogs.adobe.com/creativecloud/design/) to stay updated and informed. Adobe XD is being updated with new features frequently, and since it's in public Beta, you can [download and test it for free](https://adobe.ly/2knsUsI).

_(il, aa)_
