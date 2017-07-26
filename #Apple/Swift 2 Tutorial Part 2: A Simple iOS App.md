# Swift 2 Tutorial Part 2: A Simple iOS App

_Captured: 2015-11-25 at 19:14 from [www.raywenderlich.com](http://www.raywenderlich.com/115279/swift-2-tutorial-part-2-a-simple-ios-app)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Create a simple iOS app in this Swift 2 tutorial!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Create a simple iOS app in this Swift 2 tutorial!_

_Update 9/21/15_: Series updated for Xcode 7.0.

Welcome back to our Swift 2 tutorial series!

In the [first Swift 2 tutorial](http://www.raywenderlich.com/115253/swift-2-tutorial-a-quick-start), you learned the basics of the Swift language, and created your very own tip calculator class.

In this second Swift 2 tutorial, you will learn how to make a simple iOS app. Specifically, you will create a user interface for your tip calculator class that you developed last time.

I will be writing this tutorial in a manner so that it is useful for both complete beginners to iOS, and seasoned iOS developers transitioning to Swift.

For this Swift 2 tutorial, make sure you have the very latest public copy of Xcode (Xcode 7.0 at the time of writing this Swift 2 tutorial). Swift is changing quickly and we are doing our best to update this tutorial as each beta comes out; the code may not work on older versions of Xcode or Pre-Release versions of Xcode.

_Note:_ This tutorial is best if you are already an experienced programmer and want a "quick start" to Swift. If you are brand new to programming and want something a bit slower-paced, you should check out [this tutorial series](http://www.raywenderlich.com/114148/learn-to-code-ios-apps-with-swift-tutorial-1-welcome-to-programming) instead.

## Getting Started

Start up Xcode and go to _File\New\Project_. Select _iOS\Application\Single View Application_, and click _Next_.

![Creating a new Single View Application in Xcode](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/001_NewProject-700x491.png)

> _Creating a new Single View Application in Xcode_

Enter _TipCalculator_ for the _Product Name_, set the _Language_ to _Swift_, and _Devices_ to _iPhone_. Make sure _Use Core Data_ and the other checkboxes are _not checked_, and click _Next_.

![Creating a new project in Xcode](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/002_NewProject2-700x494.png)

> _Creating a new project in Xcode_

Choose a directory to save your project, and click _Create_.

Let's see what Xcode has built for you. In the upper left corner of Xcode, select the _iPhone 6S Simulator_ and click _Play_ to test your app.

![Choosing the iPhone 6S Simulator](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/003_Simulator.png)

> _Choosing the iPhone 6S Simulator_

You should then see a blank white screen appear:

![008_Blank_Screen](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/008_Blank_Screen-281x500.png)

Xcode has created a single blank screen in your app; in this tutorial you'll fill it up!

## Creating Your Model

First things first - before you create the user interface for your app, you should create your app's model. A model is a class (or set of classes) that represents your class's data, and operations that your app will perform on that data.

In this tutorial, your app's model will simply be the `TipCalculator` class you created in the [first Swift 2 tutorial](http://www.raywenderlich.com/115253/swift-2-tutorial-a-quick-start), except you will rename it to `TipCalculatorModel`.

Let's add this class to your project. To do this, go to _File\New\File_, select _iOS\Source\Swift File_, and click _Next_. Name the file _TipCalculatorModel.swift_, and click _Create_.

_Note:_ You cannot call code from your app that resides in a Playground file. Playground files are just for testing and prototyping code; if you want to use code from a Playground in your app, you have to move it to a Swift file like you're doing here.

Open _TipCalculator.swift_, and copy your `TipCalculator` class (just the class, not the testing lines at the bottom) from the previous tutorial into the file, and make the following changes:

  1. Rename the class to `TipCalculatorModel`
  2. Change `total` and `taxPct` from constants to variables (because the user will be changing these values as he/she runs the app)
  3. Because of this, you need to change `subtotal` to a _computed property_. Replace the `subtotal` property with the following:

A computed property does not actually store a value. Instead, it is computed each time based on other values. Here, you calculate the subtotal each time it is accessed based on the current values of `total` and `taxPct`.
    
    
    var subtotal: Double {
      get {
        return total / (taxPct + 1)
      }
      set(newSubtotal) { 
         //... 
      }
    }

  1. Delete the line that sets `subtotal` in `init`
  2. Delete any comments that are in the file

When you're done, the file should look like this:
    
    
    import Foundation
     
    class TipCalculatorModel {
     
      var total: Double
      var taxPct: Double
      var subtotal: Double {
        get {
          return total / (taxPct + 1)
        }
      }
     
      init(total: Double, taxPct: Double) {
        self.total = total
        self.taxPct = taxPct
      }
     
      func calcTipWithTipPct(tipPct: Double) -> Double {
        return subtotal * tipPct
      }
     
      func returnPossibleTips() -> [Int: Double] {
     
        let possibleTipsInferred = [0.15, 0.18, 0.20]
     
        var retval = [Int: Double]()
        for possibleTip in possibleTipsInferred {
          let intPct = Int(possibleTip*100)
          retval[intPct] = calcTipWithTipPct(possibleTip)
        }
        return retval
     
      }
     
    }

You have your app's model ready to go - time for the views!

## Introduction to Storyboards and Interface Builder

You create the user interface for your iOS apps in something called a _Storyboard_. Xcode comes with a built-in tool called _Interface Builder_ that allows you to edit Storyboards in a nice, visual way.

With Interface Builder, you can lay out all of your buttons, text fields, labels, and other controls in your app (called _Views_) as simply as dragging and dropping.

Go ahead and click on _Main.storyboard_ in the left side of Xcode to reveal the Storyboard in Interface Builder.

![009_InterfaceBuilder](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/009_InterfaceBuilder-700x360.png)

There's a lot of stuff to cover here, so let's go over each section of the screen one at a time.

  1. _On the far left_ is your _Project Navigator_, where your can see the files in your project.
  2. _On the left of Interface Builder_ is your _Document Outline_, where you can see at a glance the views inside each "screen" of your app (view controllers). Be sure to click the "down" arrows next to each item to fully expand the document outline.

Right now your app only has one view controller, with only one empty white view. You'll be adding things into this soon.

  3. _There's an arrow_ to the left of your view controller. This indicates that this is the _initial view controller_, or the view controller that is first displayed when the app starts up. You can change this by dragging the arrow to a different view controller, or by clicking the "Is Initial View Controller" property on a different view controller in the Attributes Inspector (more on Inspectors later).
  4. _On the bottom of the Interface Builder_ you'll see something that says "w Any", "h Any". This means that you are editing the layout for your app in a way that should work on _any_ sized user interface. You can do this through the power of something called _Auto Layout_. By clicking this area, you can switch to editing the layout for devices of specific size classes. You'll learn about Adaptive UI and Auto Layout in a future tutorial.
  5. _On the top of your view controller_ (if you don't see these, click the view controller to reveal them) you'll see three small icons, which represent the view controller itself and two other items: First Responder, and Exit. If you've been developing in Xcode for a while, you'll notice that these have moved (they used to be below the view controller). You won't be using these in this tutorial, so don't worry about them for now.
  6. _On the bottom right of Interface Builder_ are four icons related to _Auto Layout_. Again, you'll learn more about these in a future tutorial.
  7. _On the upper right of Interface Builder_ are the _Inspectors_ for whatever you have selected in the Document Outline. If you do not see the inspectors, go to _View\Utilities\Show Utilities_. 

Note there are several tabs of inspectors. You'll be using these a lot in this tutorial to configure the views you add to this project.

  8. _On the bottom right of Interface Builder_ are the _Libraries_. This is a list of different types of views or view controllers you can add to your app. Soon you will be dragging items from your library into your view controller to lay out your app.

## Creating your Views

Remember that your `TipCalculatorModel` class has two inputs: a total, and a tax percentage.

It would be nice if the user could type in the total with a numeric keyboard, so a text field is perfect for that. As for the tax percentage, that usually is restricted to a small range of values, so you'll use a slider for that instead.

In addition to the text field and slider, you will need a label for each, a navigation bar to show the app's name, a button to click to perform the tip calculation, and a text field to show the results.

Let's build this user interface one piece at a time.

  1. _Navigation bar._ Rather than adding a navigation bar directly, select your view controller by selecting it in the document outline: 

![010_SelectViewController](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/010_SelectViewController-700x245.png)

Once it's selected, go to _Editor\Embed In\Navigation Controller_. This will set up a Navigation Bar in your view controller. Double click the Navigation Bar (the one inside your view controller), and set the text to _Tip Calculator_.

![011_SetNavBar](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/011_SetNavBar-700x257.png)

  2. _Labels._ From the Object Library, drag a _Label_ into your view controller. 

![012_DragLabel](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/012_DragLabel-700x244.png)

Double click the label and set its text to _Bill Total (Post-Tax):_. Select the label, and in the _Inspector_'s fifth tab (the _Size Inspector_), set _X=33_ and _Y=81_. Repeat this for another label, but set the text to _Tax Percentage (0%):_, _X=20_, and _Y=120_.

![013_AddLabels](http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/013_AddLabels-700x230.png)

  3. _Text Field._ From the Object Library, drag a Text Field into your view controller. In the Attributes Inspector, set _Keyboard Type=Decimal Pad_. In the Size Inspector, set _X=192_, _Y=77_, and _Width=392_. 

![014_TextField](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/014_TextField-700x211.png)

  4. _Slider._ From the Object Library, drag a Slider into your view controller. In the Attribute Inspector, set _Minimum Value=0_, _Maximum Value=10_, and _Current Value=6_. In the Size Inspector, set _X=190_, _Y=116_, and _Width=396_. 

![015_Slider](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/015_Slider-700x196.png)

  5. _Button._ From the Object Library, drag a Button into your view controller. Double click the Button, and set the text to _Calculate_. In the Size Inspector, set _X=268_ and _Y=154_. 

![016_Button](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/016_Button-700x220.png)

  6. _Text View._ From the Object Library, drag a Text View into your View Controller. Double click the Text View, and delete the placeholder text. In the Attributes Inspector, make sure _Editable_ and _Selectable_ _are not checked_. In the Size Inspector, set _X=16_, _Y=192_, _Width=568_, and _Height=400_. 

![017_TextView](http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/017_TextView-700x190.png)

  7. _Tap Gesture Recognizer._ From the Object Library, drag a Tap Gesture Recognizer onto your main view: 

![018_GestureRecognizer](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/018_GestureRecognizer-700x313.png)

This will be used to tell when the user taps the view to dismiss the keyboard.

  8. _Auto Layout._ Interface Builder can often do a great job setting up reasonable Auto Layout constraints for you automatically; and it definitely can in this case. To do this, first select the main View in the Document Outline, then click on the third button in the lower right of the Interface Builder (which looks like a Tie Fighter) and select _All Views\Add Missing Constraints._

![019_AddMissingConstraints](http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/019_AddMissingConstraints-700x314.png)

Build and run on your iPhone 6S simulator, and you should see a basic user interface working already!

![020_BasicUI](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/020_BasicUI-281x500.png)

## A View Controller Tour

So far you've created your app's models and views - it's time to move on to the view controller.

Open _ViewController.swift_. This is the Swift code for your single view controller ("screen") in your app. It is responsible for managing the communication between your views and your model.

You will see that the class has the following code in it already:
    
    
    // 1
    import UIKit
     
    // 2
    class ViewController: UIViewController {
     
      // 3
      override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
      }
     
      // 4
      override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
      }
     
    }

There are some new elements of Swift here that you haven't learned about yet, so let's go over them one at a time.

  1. iOS is split up into multiple _frameworks_, each of which contain different sets of code. Before you can use code from a framework in your app, you have to import it like you see here. _UIKit_ is the framework that contains the base class for view controllers, various controls like buttons and text fields, and much more.
  2. This is the first example you've seen of a class that subclasses another class. Here, you are declaring a new class `ViewController` that subclasses Apple's `UIViewController`.
  1. This method is called with the root view of this view controller is first accessed. Whenever you override a method in Swift, you need to mark it with the `override` keyword. This is to help you avoid a situation where you override a method by mistake.
  2. This method is called when the device is running low on memory. It's a good place to clean up any resources you can spare.

## Connecting your View Controller to your Views

Now that you have a good understanding of your view controller class, let's add some properties for its subviews, and hook them up in interface builder.

To do this, add these following properties to your `ViewController` class (right before `viewDidLoad`):

Here you are declaring four variables just as you learned in the [first Swift 2 tutorial](http://www.raywenderlich.com/115253/swift-2-tutorial-a-quick-start) - a `UITextField`, a `UISlider`, a `UILabel`, and a `UITextView`.

There's only two differences:

  1. You're prefixing these variables with the `@IBOutlet` keyword. Interface Builder scans your code looking for any properties in your view controller prefixed with this keyword. It exposes any properties it discovers so you can connect them to views.
  2. You're marking the variables with an exclamation mark (!). This indicates the variables are optional values, but they are _implicitly unwrapped_. This is a fancy way of saying you can write code assuming that they are set, and your app will crash if they are not set.

Implicitly unwrapped optionals are a convenient way to create variables you know for sure will be set up before you use them (like user interface elements created in the Storyboard), so you don't have to unwrap the optionals every time you want to use them.

Let's try connecting these properties to the user interface elements.

Open _Main.storyboard_ and select your View Controller in the Document Outline. Open the _Connections Inspector_ (6th tab), and you will see all of the properties you created listed in the _Outlets_ section.

![021_ConnectionsInspector](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/021_ConnectionsInspector-700x206.png)

You'll notice a small circle to the right of `resultsTextView`. Control-drag from that button down to the text view below the Calculate button, and release to connect your Swift property to this view.

![022_ConnectTextView](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/022_ConnectTextView-700x304.png)

Now repeat this for the other three properties, connecting each one to the appropriate UI element.

## Connecting Actions to your View Controller

Just like you connected views to properties on your view controller, you want to connect certain actions from your views (such as a button click) to methods on your view controller.

To do this, open _ViewController.swift_ and add these three new methods anywhere in your class:
    
    
    @IBAction func calculateTapped(sender : AnyObject) {
    }
    @IBAction func taxPercentageChanged(sender : AnyObject) {
    }
    @IBAction func viewTapped(sender : AnyObject) {
    }

When you declare callbacks for actions from views, they always need to have this same signature - a function with no return value, that takes a single parameter of type `AnyObject` as a parameter, which represents a class of any type.

To make Interface Builder notice your new methods, you need to mark these methods with the `@IBAction` keyword (just as you marked properties with the `@IBOutlet` keyword).

Next, switch back to _Main.storyboard_ and make sure that your view controller is selected in the Document Outline. Make sure the Connections Inspector is open (6th tab) and you will see your new methods listed in a the _Received Actions_ section.

![023_NewMethods](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/023_NewMethods-700x211.png)

Find the circle to the right of `calculateTapped:`, and drag a line from that circle up to the _Calculate_ button.

In the popup that appears, choose _Touch Up Inside_:

![024_TouchUpInside](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/024_TouchUpInside-700x239.png)

This is effectively saying "when the user releases their finger from the screen when over the button, call my method `calculateTapped:`".

Now repeat this for the other two methods:

  * Drag from `taxPercentageChanged:` to your slider, and connect it to the _Value Changed_ action, which is called every time the user moves the slider.
  * Drag from `viewTapped:` to the _Tap Gesture Recognizer_ in the document outline. There are no actions to choose from for gesture recognizers; your method will simply be called with the recognizer is triggered.

## Connecting Your View Controller to your Model

You're almost done - all you have to do now is hook your view controller to your model.

Open _ViewController.swift_ and add a property for the model to your class and a method to refresh the UI:
    
    
    let tipCalc = TipCalculatorModel(total: 33.25, taxPct: 0.06)
     
    func refreshUI() {
      // 1
      totalTextField.text = String(format: "%0.2f", tipCalc.total)
      // 2
      taxPctSlider.value = Float(tipCalc.taxPct) * 100.0
      // 3
      taxPctLabel.text = "Tax Percentage (\(Int(taxPctSlider.value))%)"
      // 4
      resultsTextView.text = ""
    }

Let's go over `refreshUI()` one line at a time:

  1. In Swift you must be explicit when converting one type to another. Here you convert `tipCalc.total` from a `Double` to a `String`.
  2. You want the tax percentage to be displayed as an Integer (i.e. 0%-10%) rather than a decimal (like 0.06). So here you multiply the value by 100.

_Note:_ The cast is necessary because the `taxPctSlider.value` property is a `Float`.

  3. Here you use string interpolation to update the label based on the tax percentage.
  4. You clear the results text view until the user taps the calculate button.

Next, add a call to `refreshUI()` at the bottom of `viewDidLoad`:

Also implement `taxPercentageChanged` and `viewTapped` as follows:
    
    
    @IBAction func taxPercentageChanged(sender : AnyObject) {
      tipCalc.taxPct = Double(taxPctSlider.value) / 100.0
      refreshUI()
    }
    @IBAction func viewTapped(sender : AnyObject) {
      totalTextField.resignFirstResponder()
    }

`taxPercentageChanged` simply reverses the "multiply by 100" behavior, while `viewTapped` calls `resignFirstResponder` on the `totalTextField` when the view is tapped (which has the effect of dismissing the keyboard).

One method left. Implement `calculateTapped()` as follows:
    
    
    @IBAction func calculateTapped(sender : AnyObject) {
      // 1
      tipCalc.total = Double((totalTextField.text! as NSString).doubleValue)
      // 2
      let possibleTips = tipCalc.returnPossibleTips()
      var results = ""
      // 3
      for (tipPct, tipValue) in possibleTips {
        // 4
        results += "\(tipPct)%: \(tipValue)\n"
      }
      // 5
      resultsTextView.text = results
    }

Let's go over this line by line:

  1. Here you need to convert a `String` to a `Double`. This is a bit of a hack to do this; hopefully there will be an easier way in a future update to Swift.
  1. Here you call the `returnPossibleTips` method on your `tipCalc` model, which returns a dictionary of possible tip percentages mapped to tip values.
  2. This is how you enumerate through both keys and values of a dictionary at the same time in Swift. Handy, eh?
  3. Here you use string interpolation to build up the string to put in the results text filed. `\n` is the newline character.
  4. Finally you set the results text to the string you have been building.

And that's it! Build and run, and enjoy your hand-made tip calculator!

![025_Complete](http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/025_Complete-281x500.png)
    
    
    var keys = Array(possibleTips.keys)
    keys.sortInPlace()
    for tipPct in keys {
      let tipValue = possibleTips[tipPct]!
      let prettyTipValue = String(format:"%.2f", tipValue)
      results += "\(tipPct)%: \(prettyTipValue)\n"
    }

## Where To Go From Here?

Here is the [final Xcode project](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/TipCalculator-Demo4.zip) with all the code from this Swift 2 tutorial.

Want to learn more? Keep reading for the [next part of this series](http://www.raywenderlich.com/?p=75289), where you'll learn about tuples, protocols, and table views - or check out our [new Swift books](http://www.raywenderlich.com/store)!

Thanks for reading this tutorial, and if you have any comments or questions please join in the forum discussion below!
