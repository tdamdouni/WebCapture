# iOS Animation Tutorial: Custom View Controller Presentation Transitions

_Captured: 2015-10-03 at 13:25 from [www.raywenderlich.com](http://www.raywenderlich.com/113845/ios-animation-tutorial-custom-view-controller-presentation-transitions)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

_Note from Ray_: This is an abbreviated version of a chapter from [iOS Animations by Tutorials Second Edition](http://www.raywenderlich.com/store/ios-animations-by-tutorials) to give you a sneak peek of what's inside the book, released as part of the [iOS 9 Feast](http://www.raywenderlich.com/113226/introducing-the-ios-9-feast). This tutorial is fully up-to-date for iOS 9, Xcode 7, and Swift 2. We hope you enjoy!

![An iOS animation tutorial for the iOS 9 Feast!](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_minis_ios_anim-250x250.jpg)

> _[An iOS animation tutorial for the iOS 9 Feast!](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_minis_ios_anim.jpg)_

Whether you're presenting the camera view controller, the address book, or one of your own custom-designed modal screens, you call the same UIKit method every time: `presentViewController(_: animated:completion:)`. This method "gives up" the current screen to another view controller.

The default presentation animation simply slides the new view up to cover the current one. The illustration below shows a "New Contact" view controller sliding up over the list of contacts:

![01_iAT_addressbook](http://cdn2.raywenderlich.com/wp-content/uploads/2015/02/01_iAT_addressbook.png)

In this tutorial, you'll create your own custom presentation transitions controller to replace the default animations and liven up tutorial's starter project.

## Getting Started

Download the starter project: [BeginnerCook Starter](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/BeginnerCook-Starter1.zip), unarchive the zip file and open the Beginner Cook starter project. Select _Main.storyboard_ to begin the tour:

![image003](http://cdn3.raywenderlich.com/wp-content/uploads/2015/02/image003-480x219.png)

The first view controller (`ViewController`) contains the app's title and main description as well as a scroll view at the bottom, which shows the list of available herbs.

The main view controller presents `HerbDetailsViewController` whenever the user taps one of the images in the list; this view controller sports a background, a title, a description and some buttons to credit the image owner.

There's already enough code in ViewController.swift and HerbDetailsViewController.swift to support the basic application. Build and run the project to see how the app looks and feels:

![image005](http://cdn2.raywenderlich.com/wp-content/uploads/2015/02/image005-440x320.png)

Tap on one of the herb images, and the details screen comes up via the standard vertical cover transition. That might be OK for your garden-variety app, but your herbs deserve better!

Your job is to add some custom presentation transitions to your app to make it blossom! You'll replace the current stock animation with one that expands the tapped herb image to a full-screen view like so:

![image007](http://cdn1.raywenderlich.com/wp-content/uploads/2015/02/image007-480x233.png)

Roll up your sleeves, put your developer apron on and get ready for the inner workings of custom presentation controllers!

## Behind the Scenes of Custom Transitions

UIKit lets you customize your view controller's presentation via the delegate pattern; you simply make your main view controller (or another class you create specifically for that purpose) adopt `UIViewControllerTransitioningDelegate`.

Every time you present a new view controller, UIKit asks its delegate whether or not it should use a custom transition. Here's what the first step of the custom transitioning dance looks like:

![image009](http://cdn4.raywenderlich.com/wp-content/uploads/2015/02/image009-480x224.png)

UIKit calls `animationControllerForPresentedController(:_ presentingController:sourceController:)`; if that method returns nil UIKit uses the built-in transition. If UIKit receives an object instead, then UIKit uses that object as the animation controller for the transition.

There are a few more steps in the dance before UIKit can use the custom animation controller:

![image011](http://cdn2.raywenderlich.com/wp-content/uploads/2015/02/image011-480x211.png)

UIKit first asks your animation controller (simply known as the animator) for the transition duration in seconds, then calls `animateTransition()` on it. This is when your custom animation gets to take center stage.

In `animateTransition()`, you have access to both the current view controller on the screen as well as the new view controller to be presented. You can fade, scale, rotate and manipulate the existing view and the new view however you like.

Now that you've learned a bit about how custom presentation controllers work, you can start to create your own.

## Implementing Transition Delegates

Since the delegate's task is to manage the animator object that performs the actual animations, you'll first have to create a stub for the animator class before you can write the delegate code.

From Xcode's main menu select _File\New\File…_ and choose the template _iOS\Source\Cocoa Touch Class_.

Set the new class name to _PopAnimator_ and make it a subclass of `NSObject`.

Open _PopAnimator.swift_ and update the class definition to make it conform to the `UIViewControllerAnimatedTransitioning` protocol as follows:
    
    
    class PopAnimator: NSObject, UIViewControllerAnimatedTransitioning {
     
    }

You'll see some complaints from Xcode since you haven't implemented the required delegate methods yet, so you'll stub those out next.

Add the following method to the class:
    
    
    func transitionDuration(transitionContext: UIViewControllerContextTransitioning?)-> NSTimeInterval {
      return 0
    }

The 0 value above is just a placeholder value for the duration; you'll replace this later with a real value as you work through the project.

Now add the following method stub to the class:

The above stub will hold your animation code; adding it should have cleared the remaining errors in Xcode.

Now that you have the basic animator class, you can move on to implementing the delegate methods on the view controller side.

Open _ViewController.swift_ and add the following extension to the end of the file:

This code indicates the view controller conforms to the transitioning delegate protocol. You'll add some methods here in a moment.

Find `didTapImageView()` in the main body of the class. Near the bottom of that method you'll see the code that presents the details view controller. `herbDetails` is the instance of the new view controller; you'll need to set its transitioning delegate to the main controller.

Add the following code right before the last line of the method that calls `presentViewController`:

Now UIKit will ask `ViewController` for an animator object every time you present the details view controller on the screen. However, you still haven't implemented any of `UIViewControllerTransitioningDelegate`'s methods, so UIKit will still use the default transition.

The next step is to actually create your animator object and return it to UIKit when requested.

Add the following new property to `ViewController`:

This is the instance of `PopAnimator` that will drive your animated view controller transitions. You only need one instance of `PopAnimator` since you can continue to use the same object each time you present a view controller, as the transitions are the same every time.

Now add the first delegate method to the extension in `ViewController`:
    
    
    func animationControllerForPresentedController(
      presented: UIViewController,
      presentingController presenting: UIViewController,
      sourceController source: UIViewController) ->
      UIViewControllerAnimatedTransitioning? {
     
        return transition
    }

This method takes a few parameters that let you make an informed decision whether or not you want to return a custom animation. In this tutorial you'll always return your single instance of `PopAnimator` since you have only one presentation transition.

You've already added the delegate method for presenting view controllers, but how will you deal with dismissing one?

Add the following delegate method to handle this:

The above method does essentially the same thing as the previous one: you check which view controller was dismissed and decide whether to return nil and use the default animation, or return a custom transition animator and use that instead. At the moment you return nil, as you aren't going to implement the dismissal animation until later.

You finally have a custom animator to take care of your custom transitions. But does it work?

Build and run your project and tap one of the herb images:

![image013](http://cdn1.raywenderlich.com/wp-content/uploads/2015/02/image013-452x320.png)

Nothing happens. Why? You have a custom animator to drive the transition, but… oh, wait, you haven't added any code to the animator class! :] You'll take care of that in the next section.

## Creating your Transition Animator

Open _PopAnimator.swift_; this is where you'll add the code to transition between the two view controllers.

First, add the following properties to this class:

You'll use `duration` in several places, such as when you tell UIKit how long the transition will take and when you create the constituent animations.

You also define `presenting` to tell the animator class whether you are presenting or dismissing a view controller. You want to keep track of this because typically, you'll run the animation forward to present and in reverse to dismiss.

Finally, you will use `originFrame` to store the original frame rect of the image the user taps - you will need that to animate from the original frame to a full screen image and vice versa. Keep an eye out for originFrame later on when you fetch the currently selected image and pass its frame to the animator instance.

Now you can move on to the `UIViewControllerAnimatedTransitioning` methods.

Replace the code inside `transitionDuration()` with the following:

Reusing the duration property lets you easily experiment with the transition animation; you can simply modify the value of the property to make the transition run faster or slower.

### Setting your Transition's Context

It's time to add some magic to `animateTransition`. This method has one parameter of type `UIViewControllerContextTransitioning`, which gives you access to the parameters and view controllers of the transition.

Before you start working on the code itself, it's important to understand what the animation context actually is.

When the transition between the two view controllers begins, the existing view is added to a transition container view and the new view controller's view is created but not yet visible, as illustrated below:

![image015](http://cdn3.raywenderlich.com/wp-content/uploads/2015/02/image015-480x236.png)

Therefore your task is to add the new view to the transition container within animateTransition(), "animate in" its appearance, and "animate out" the old view if required.

By default, the old view is removed from the transition container when the transition animation is done:

![image017](http://cdn3.raywenderlich.com/wp-content/uploads/2015/02/image017-480x236.png)

### Adding a Pop Transition

To create the animations for your custom transition you need to work with the so called "container" view of the transition context. This is a temporary view (much like a scratchpad) that gets added to the screen only for the time while the transition takes place. You will create all your animations in this view.

Insert into `animateTransition()`:
    
    
    let containerView = transitionContext.containerView()!
     
    let toView =
      transitionContext.viewForKey(UITransitionContextToViewKey)!
     
    let herbView = presenting ? toView : transitionContext.viewForKey(UITransitionContextFromViewKey)!

`containerView` is where your animations will live, while `toView` is the new view to present. If you're presenting, `herbView` is just the `toView`; otherwise it will be fetched from the context. For both presenting and dismissing, `herbView` will always be the view that you animate.

When you present the details controller view, it will grow to take up the entire screen. When dismissed, it will shrink to the image's original frame.

Add the following to `animateTransition()`:
    
    
    let initialFrame = presenting ? originFrame : herbView.frame
    let finalFrame = presenting ? herbView.frame : originFrame
     
    let xScaleFactor = presenting ?
      initialFrame.width / finalFrame.width :
      finalFrame.width / initialFrame.width
     
    let yScaleFactor = presenting ?
      initialFrame.height / finalFrame.height :
      finalFrame.height / initialFrame.height

In the code above, you detect the initial and final animation frames and then calculate the scale factor you need to apply on each axis as you animate between each view.

Now you need to carefully position the new view so it appears exactly above the tapped image; this will make it look like the tapped image expands to fill the screen.

Add the following to `animateTransition()`:
    
    
    let scaleTransform = CGAffineTransformMakeScale(xScaleFactor, yScaleFactor)
     
    if presenting {
      herbView.transform = scaleTransform
      herbView.center = CGPoint(
        x: CGRectGetMidX(initialFrame),
        y: CGRectGetMidY(initialFrame))
      herbView.clipsToBounds = true
    }

When presenting the new view, you set its scale and position so it exactly matches the size and location of the initial frame.

Now add the final bits of code to `animateTransition()`:
    
    
    containerView.addSubview(toView)
    containerView.bringSubviewToFront(herbView)
     
    UIView.animateWithDuration(duration, delay:0.0,
      usingSpringWithDamping: 0.4,
      initialSpringVelocity: 0.0,
      options: [],
      animations: {
        herbView.transform = self.presenting ?
         CGAffineTransformIdentity : scaleTransform
     
        herbView.center = CGPoint(x: CGRectGetMidX(finalFrame),
                                  y: CGRectGetMidY(finalFrame))
     
      }, completion:{_ in
        transitionContext.completeTransition(true)
    })

This will first add `toView` to the container. Next, you need to make sure the `herbView` is on top since that's the only view you're animating. Remember that when dismissing, `toView` is the original view so in the first line, you'll be adding it on top of everything else and your animation will be hidden away unless you bring `herbView` to the front.

Then, you can kick off the animations - using a spring animation here will give it a bit of bounce.

Inside the animations expression, you change the transform and position of `herbView`. When presenting, you're going from the small size at the bottom to the full screen so the target transform is just the identity transform. When dismissing, you animate it to scale down to match the original image size.

At this point, you've set the stage by positioning the new view controller over the tapped image; you've animated between the initial and final frames; and finally, you've called `completeTransition()` to hand things back to UIKit. It's time to see your code in action!

Build and run your project; tap the first herb image to see your view controller transition in action:

![image019](http://cdn4.raywenderlich.com/wp-content/uploads/2015/02/image019-272x320.png)

Currently your animation starts from the top-left corner; that's because the default value of `originFrame` has the origin at (0, 0) - and you never set it to any other value.

Open _ViewController.swift_ and add the following code to the top of `animationControllerForPresentedController()`:

This sets the originFrame of the transition to the frame of `selectedImage`, which is the image view you last tapped. Then you set presenting to true and hide the tapped image during the animation.

Build and run your project again; tap different herbs in the list and see how your transition looks for each:

![image023](http://cdn1.raywenderlich.com/wp-content/uploads/2015/02/image023-480x285.png)

### Adding a Dismiss Transition

All that's left to do is dismiss the details controller. You've actually done most of the work in the animator already - the transition animation code does the logic juggling to set the proper initial and final frames, so you're most of the way to playing the animation both forwards and backwards. Sweet! :]

Open _ViewController.swift_ and replace the body of `animationControllerForDismissedController()` with the following:

This tells your animator object that you're dismissing a view controller so the animation code will run in the correct direction.

Build and run the project to see the result. Tap on an herb and then tap anywhere on screen to dismiss it and enjoy!

![image027](http://cdn5.raywenderlich.com/wp-content/uploads/2015/02/image027-165x320.png)

A final touch to make the transition a bit smoother - you will animate the corner radius of the presented view controller so it really falls back in place when you dismiss it.

Add at the bottom of `animateTransition`:
    
    
    let round = CABasicAnimation(keyPath: "cornerRadius")
    round.fromValue = presenting ? 20.0/xScaleFactor : 0.0
    round.toValue = presenting ? 0.0 : 20.0/xScaleFactor
    round.duration = duration / 2
    herbView.layer.addAnimation(round, forKey: nil)
    herbView.layer.cornerRadius = presenting ? 0.0 : 20.0/xScaleFactor

When you are presenting the view controller you animate the radius from 20.0 to 0.0 and vice versa when you are dismissing the view controller. A nice touch to finish this tutorial on a high note!

## Where To Go From Here?

You can grab the completed project from this tutorial here: [BeginnerCook Completed](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/BeginnerCook-Completed1.zip).

From here, you can do a lot more to polish this transition even further. For example, here are some ideas to develop:

  * hide tapped images during transitions so it really looks like they grow to take up the full screen
  * fade in and out each herb's description text so the transition animation is smoother
  * test and adjust the transition for landscape orientation

All of these and more are tackled in the presentation transition animations chapter in [iOS Animations by Tutorials](http://www.raywenderlich.com/store/ios-animations-by-tutorials). In the book, you'll learn in a bit more detail about view controller presentation transitions, orientation change animations, navigation controllers and interactive transitions, and more.

We hope you enjoyed this tutorial, and if you have any questions or comments, please join the forum discussion below!
