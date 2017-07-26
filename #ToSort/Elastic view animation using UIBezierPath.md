# Elastic view animation using UIBezierPath

_Captured: 2015-10-23 at 15:41 from [iostuts.io](http://iostuts.io/2015/10/17/elastic-bounce-using-uibezierpath-and-pan-gesture/)_

Hey!

This tutorial has been created to explain how the elastic bounce effect was achieved in [DGElasticPullToRefresh](https://github.com/gontovnik/DGElasticPullToRefresh):

![](http://iostuts.io/content/images/2015/10/DGElasticPullToRefresh1.gif)

Prerequisites / Requirements

  * Xcode 7
  * Swift 2.0
  * At least basic knowledge and understanding of UIBezierPath and UIGestureRecognizer

Understand logic

As you probably understood, the main thing we will be using for this trick is UIBezierPath. We will create a CAShapeLayer with a bezier path and will move all the control points each time a finger moves on the screen. Each control point will be represented as an invisible UIView. Here is an example of how it would look if I made all control points views red:

![](http://iostuts.io/content/images/2015/10/ControlPoints1.png)

![](http://iostuts.io/content/images/2015/10/ControlPoints2.png)

_See second screenshot for view variable names_

When the finger is released we will start UIView spring animation which will move all our control point views to their initial location with a nice bounce. While views are being animated we need to somehow update our bezier path. For this purpose we are going to use CADisplayLink, which will run on a main run loop and will call required function once per frame.

**It's time to code!**

Build

Create a single view application and paste this code into ViewController.swift file inside class declaration:
    
    
    // MARK: -
    // MARK: Vars
    
    private let minimalHeight: CGFloat = 50.0  
    private let shapeLayer = CAShapeLayer()
    
    // MARK: -
    
    override func loadView() {  
        super.loadView()
    
        shapeLayer.frame = CGRect(x: 0.0, y: 0.0, width: view.bounds.width, height: minimalHeight)
        shapeLayer.backgroundColor = UIColor(red: 57/255.0, green: 67/255.0, blue: 89/255.0, alpha: 1.0).CGColor
        view.layer.addSublayer(shapeLayer)
    
        view.addGestureRecognizer(UIPanGestureRecognizer(target: self, action: "panGestureDidMove:"))
    }
    
    // MARK: -
    // MARK: Methods
    
    func panGestureDidMove(gesture: UIPanGestureRecognizer) {  
        if gesture.state == .Ended || gesture.state == .Failed || gesture.state == .Cancelled {
    
        } else {
            shapeLayer.frame.size.height = minimalHeight + max(gesture.translationInView(view).y, 0)
        }
    }
    
    override func preferredStatusBarStyle() -> UIStatusBarStyle {  
        return .LightContent
    }
    

What we did here was:

  1. Declared two variables: _shapeLayer_ \- the layer, which will be used to display bezier path. _minimalHeight_ \- defines minimal shapeLayer height; 
  2. Added a shape layer to the view.layer; 
  3. Added a pan gesture to the view; 
  4. Added `panGestureDidMove` method which will be called when finger is moved. At the moment it only changes shapeLayer height; 
  5. Overwrote `preferredStatusBarStyle` function to make our UI look nicer.

Build your project and check it. It should work this way:

![](http://iostuts.io/content/images/2015/10/Builds1.gif)

Everything works the way we expect, except one thing. It changes height with a delay / animation. It is happening because of implicit animations. We definitely do not need that. Add this line of code just before adding shapeLayer to sublayers to disable implicit animation for _position_, _bounds_ and _path_:
    
    
    shapeLayer.actions = ["position" : NSNull(), "bounds" : NSNull(), "path" : NSNull()]  
    

Run project and try again. Fixed!

![](http://iostuts.io/content/images/2015/10/Builds2.gif)

The next step is to add our control points views _(L3, L2, L1, C, R1, R2, R3, as it was shown above)_ and apply all necessary logic.

Lets do it step by step.

  * Declare maxWaveHeight variable:
    
    
    private let maxWaveHeight: CGFloat = 100.0  
    

The only reason we define and use this variable is to make our wave look nicer. If we do not specify the maximum value it could be too big and look awful.

  * Declare these variables for out control points views:
    
    
    private let l3ControlPointView = UIView()  
    private let l2ControlPointView = UIView()  
    private let l1ControlPointView = UIView()  
    private let cControlPointView = UIView()  
    private let r1ControlPointView = UIView()  
    private let r2ControlPointView = UIView()  
    private let r3ControlPointView = UIView()  
    

  * Apply red background colour and 3x3 size _(it is needed for us to see our views, at the end of the tutorial we will make them invisible)_ and add to subviews. Copy and paste this code to the end of `loadView` method:
    
    
    l3ControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)  
    l2ControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)  
    l1ControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)  
    cControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)  
    r1ControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)  
    r2ControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)  
    r3ControlPointView.frame = CGRect(x: 0.0, y: 0.0, width: 3.0, height: 3.0)
    
    l3ControlPointView.backgroundColor = .redColor()  
    l2ControlPointView.backgroundColor = .redColor()  
    l1ControlPointView.backgroundColor = .redColor()  
    cControlPointView.backgroundColor = .redColor()  
    r1ControlPointView.backgroundColor = .redColor()  
    r2ControlPointView.backgroundColor = .redColor()  
    r3ControlPointView.backgroundColor = .redColor()
    
    view.addSubview(l3ControlPointView)  
    view.addSubview(l2ControlPointView)  
    view.addSubview(l1ControlPointView)  
    view.addSubview(cControlPointView)  
    view.addSubview(r1ControlPointView)  
    view.addSubview(r2ControlPointView)  
    view.addSubview(r3ControlPointView)  
    

  * Create _UIView_ extension with this code and place it above ViewController declaration:
    
    
    extension UIView {  
        func dg_center(usePresentationLayerIfPossible: Bool) -> CGPoint {
            if usePresentationLayerIfPossible, let presentationLayer = layer.presentationLayer() as? CALayer {
                return presentationLayer.position
            }
            return center
        }
    }
    

When you animate UIView from one frame to another and you are trying to access UIView.frame, UIView.center it will give you the final animation value instead of the current. For this purpose we create an extension which will give us the position of `UIView.layer.presentationLayer` when we ask for that. Information about presentationLayer can be found [here](https://developer.apple.com/library/ios/documentation/GraphicsImaging/Reference/CALayer_class/#//apple_ref/occ/instm/CALayer/presentationLayer).

  * Declare `currentPath` function:
    
    
    private func currentPath() -> CGPath {  
        let width = view.bounds.width
    
        let bezierPath = UIBezierPath()
    
        bezierPath.moveToPoint(CGPoint(x: 0.0, y: 0.0))
        bezierPath.addLineToPoint(CGPoint(x: 0.0, y: l3ControlPointView.dg_center(false).y))
        bezierPath.addCurveToPoint(l1ControlPointView.dg_center(false), controlPoint1: l3ControlPointView.dg_center(false), controlPoint2: l2ControlPointView.dg_center(false))
        bezierPath.addCurveToPoint(r1ControlPointView.dg_center(false), controlPoint1: cControlPointView.dg_center(false), controlPoint2: r1ControlPointView.dg_center(false))
        bezierPath.addCurveToPoint(r3ControlPointView.dg_center(false), controlPoint1: r1ControlPointView.dg_center(false), controlPoint2: r2ControlPointView.dg_center(false))
        bezierPath.addLineToPoint(CGPoint(x: width, y: 0.0))
    
        bezierPath.closePath()
    
        return bezierPath.CGPath
    }
    

This function returns current CGPath for shapeLayer. It uses our control points which we created and discussed earlier.

  * Declare `updateShapeLayer` function:
    
    
    func updateShapeLayer() {  
        shapeLayer.path = currentPath()
    }
    

This function will be called when we need shapeLayer to be updated. It is not a private func because we are going to use Selector() for CADisplayLink.

  * Declare `layoutControlPoints` function:
    
    
    private func layoutControlPoints(baseHeight baseHeight: CGFloat, waveHeight: CGFloat, locationX: CGFloat) {  
        let width = view.bounds.width
    
        let minLeftX = min((locationX - width / 2.0) * 0.28, 0.0)
        let maxRightX = max(width + (locationX - width / 2.0) * 0.28, width)
    
        let leftPartWidth = locationX - minLeftX
        let rightPartWidth = maxRightX - locationX
    
        l3ControlPointView.center = CGPoint(x: minLeftX, y: baseHeight)
        l2ControlPointView.center = CGPoint(x: minLeftX + leftPartWidth * 0.44, y: baseHeight)
        l1ControlPointView.center = CGPoint(x: minLeftX + leftPartWidth * 0.71, y: baseHeight + waveHeight * 0.64)
        cControlPointView.center = CGPoint(x: locationX , y: baseHeight + waveHeight * 1.36)
        r1ControlPointView.center = CGPoint(x: maxRightX - rightPartWidth * 0.71, y: baseHeight + waveHeight * 0.64)
        r2ControlPointView.center = CGPoint(x: maxRightX - (rightPartWidth * 0.44), y: baseHeight)
        r3ControlPointView.center = CGPoint(x: maxRightX, y: baseHeight)
    }
    

This part probably requires a little bit of explanation about what each variable means.

  1. **baseHeight** \- the height of the "base". baseHeight + waveHeight = our full height; 
  2. **waveHeight** \- wave of our curve, we want it to have max value which we defined before. Without max value it may look really weird. I was playing with values to find the most appropriate; 
  3. **locationX** \- X location of the finger in the view _(apex of our wave)_; 
  4. **width** \- as you probably understood, width of our view; 
  5. **minLeftX** \- defines minimal position X for l3ControlPointView. This value can go less than zero, so it visually looks nice and clean. I was playing with the values, you can have a play as well; 
  6. **maxRightX** \- same as minLeftX, but defines maximal position X for r3ControlPointView; 
  7. **leftPartWidth** \- defines distance between minLeftX and locationX; 
  8. **rightPartWidth** \- defines distance between locationX and maxRightX.

You may want to ask why we layout our control points in this way using these values. The answer is simple: I have used PaintCode and played with a bezier path. After I found values which I like, I put them all in code and played more to find the most appropriate ones.

  * Update our `panGestureDidMove` method, so all control points move when the finger moves. Replace all `panGestureDidMove` function with this code:
    
    
    func panGestureDidMove(gesture: UIPanGestureRecognizer) {  
        if gesture.state == .Ended || gesture.state == .Failed || gesture.state == .Cancelled {
    
        } else {
            let additionalHeight = max(gesture.translationInView(view).y, 0)
    
            let waveHeight = min(additionalHeight * 0.6, maxWaveHeight)
            let baseHeight = minimalHeight + additionalHeight - waveHeight
    
            let locationX = gesture.locationInView(gesture.view).x
    
            layoutControlPoints(baseHeight: baseHeight, waveHeight: waveHeight, locationX: locationX)
            updateShapeLayer()
        }
    }
    

What we do is calculate wave height, base height, location of the finger and call our function: `layoutControlPoints` to layout control points and `updateShapeLayer` to update our shape layer path.

  * Add these two lines to the end of the `loadView`, so our shape layer is displayed properly when we open app:
    
    
    layoutControlPoints(baseHeight: minimalHeight, waveHeight: 0.0, locationX: view.bounds.width / 2.0)  
    updateShapeLayer()  
    

  * Change:
    
    
    shapeLayer.backgroundColor = UIColor(red: 57/255.0, green: 67/255.0, blue: 89/255.0, alpha: 1.0).CGColor  
    

TO:
    
    
    shapeLayer.fillColor = UIColor(red: 57/255.0, green: 67/255.0, blue: 89/255.0, alpha: 1.0).CGColor  
    

Run your project and check how it works. It should work this way:

![](http://iostuts.io/content/images/2015/10/Builds3.gif)

The last thing left to do is to integrate our bounce animation when you release the finger.

Lets do it step by step again.

  * Declare **displayLink** variable:
    
    
    private var displayLink: CADisplayLink!  
    

and initialise it at the end of `loadView` method:
    
    
    displayLink = CADisplayLink(target: self, selector: Selector("updateShapeLayer"))  
            displayLink.addToRunLoop(NSRunLoop.mainRunLoop(), forMode: NSDefaultRunLoopMode)
            displayLink.paused = true
    

As mentioned at the beginning, our CADisplayLink will call required function `updateShapeLayer` each frame, so our shapeLayer path is up to date during UIView animation.

  * Declare _animating_ variable:
    
    
    private var animating = false {  
        didSet {
            view.userInteractionEnabled = !animating
            displayLink.paused = !animating
        }
    }
    

It will enable/disable interaction and will pause/unpause displayLink.

  * Update `currentPath` method, so `dg_center(Bool)` is called using previously defined _animating_ variable:
    
    
    private func currentPath() -> CGPath {  
        let width = view.bounds.width
    
        let bezierPath = UIBezierPath()
    
        bezierPath.moveToPoint(CGPoint(x: 0.0, y: 0.0))
        bezierPath.addLineToPoint(CGPoint(x: 0.0, y: l3ControlPointView.dg_center(animating).y))
        bezierPath.addCurveToPoint(l1ControlPointView.dg_center(animating), controlPoint1: l3ControlPointView.dg_center(animating), controlPoint2: l2ControlPointView.dg_center(animating))
        bezierPath.addCurveToPoint(r1ControlPointView.dg_center(animating), controlPoint1: cControlPointView.dg_center(animating), controlPoint2: r1ControlPointView.dg_center(animating))
        bezierPath.addCurveToPoint(r3ControlPointView.dg_center(animating), controlPoint1: r1ControlPointView.dg_center(animating), controlPoint2: r2ControlPointView.dg_center(animating))
        bezierPath.addLineToPoint(CGPoint(x: width, y: 0.0))
    
        bezierPath.closePath()
    
        return bezierPath.CGPath
    }
    

If we send _true_ it will use the value of the _presentationLayer_ _(as explained before)_.

  * And the last step is to update if statement in `panGestureDidMove` method. Replace all code inside this function with this:
    
    
    if gesture.state == .Ended || gesture.state == .Failed || gesture.state == .Cancelled {  
        let centerY = minimalHeight
    
        animating = true
        UIView.animateWithDuration(0.9, delay: 0.0, usingSpringWithDamping: 0.57, initialSpringVelocity: 0.0, options: [], animations: { () -> Void in
            self.l3ControlPointView.center.y = centerY
            self.l2ControlPointView.center.y = centerY
            self.l1ControlPointView.center.y = centerY
            self.cControlPointView.center.y = centerY
            self.r1ControlPointView.center.y = centerY
            self.r2ControlPointView.center.y = centerY
            self.r3ControlPointView.center.y = centerY
            }, completion: { _ in
                self.animating = false
        })
    } else {
        let additionalHeight = max(gesture.translationInView(view).y, 0)
    
        let waveHeight = min(additionalHeight * 0.6, maxWaveHeight)
        let baseHeight = minimalHeight + additionalHeight - waveHeight
    
        let locationX = gesture.locationInView(gesture.view).x
    
        layoutControlPoints(baseHeight: baseHeight, waveHeight: waveHeight, locationX: locationX)
        updateShapeLayer()
    }
    

We have added a UIView spring animation to animate our control point views back to their place with a really nice bounce. Have a play with these values, maybe you will make the animation even better!

Build project on your device and get ready to be amazed..

![](http://iostuts.io/content/images/2015/10/Builds4.gif)

We probably do not want these dots to be visible. Remove all lines of code which are responsible for setting control point views backgroundColor and frame in `loadView`.

Run again..

![](http://iostuts.io/content/images/2015/10/Builds5.gif)

It works perfectly, however, there is one thing which we forgot to do in this tutorial - we did not change the height of the shapeLayer, we only changed the path. It is not great and it should be fixed. I think this is great homework for you. Have a play with frame, path and all other values :)

I hope you enjoyed this tutorial. Please leave your comments and suggestions below and let me know which tutorial you would like to see next!

Source code of this tutorial can be found [here](https://github.com/gontovnik/DGElasticBounceTutorial)   
Source code of **DGElasticPullToRefresh** can be found [here](https://github.com/gontovnik/DGElasticPullToRefresh)

**See you next time!**
