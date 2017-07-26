# Swift NSTimer Tutorial – Lets create a counter application

_Captured: 2015-10-18 at 20:43 from [ios-blog.co.uk](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)_

In this Swift tutorial we are going to create a basic counter application that utilises the **NSTimer** class. This is a great introduction to using **NSTimer** with Swift.

Jump to:

  * [What is NSTimer?](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Set up your project](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [NSTimer in Swift](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Start NSTimer](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Pause/Stop NSTimer](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Clear NSTimer](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Subclass NSTimer](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Summary](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)
  * [Download](http://ios-blog.co.uk/tutorials/swift-nstimer-tutorial-lets-create-a-counter-application/)

### What is NSTimer?

The **NSTimer** class can be used to create 'timer' objects in your iOS applications. Simply put - a timer. I'm sure you've all seen iOS applications that have a similar function to this. Ever wondered how they work? Wondering How **NSTimer** Works? Well, it works by waiting for a specific interval of time to elapse before it fires. Upon firing it will send a specified message to your swift app target object. For example you can tell your **NSTimer** object to send a message to a window with instructions to perform an update after a period of time has elapsed, or with this example update a label every second.

So now, are you wondering how to use **NSTimer** in Swift? Great. I'm about to show you in this tutorial.

### Setting up your Xcode Project

Create a new Single View Application is Xcode and name it: **NSTimer**.

On your **Main.storyboard** we need to add in a few elements from the Object Library in Xcode. The items we need are:

  * Toolbar
  * Navigation Bar
  * Flexible Space Bar Button Item
  * Bar Button Item x 2
  * UILabel

Toolbar: Drag this to the bottom of your project:

![NSTimer Tutorial Toolbar](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Tutorial-Toolbar.png)

> _NSTimer Tutorial Toolbar_

Next, click on the button that is already there 'Item' and head over to the property inspector. We need to change the identifier to **Play**:

![NSTimer Tutorial Property Inspector Play](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Tutorial-Property-Inspector-Play.png)

> _NSTimer Tutorial Property Inspector Play_

This should change the 'Item' to the widely recognised play icon. So now your toolbar should look like:

![Swift NSTimer Tutorial Play button bar](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Tutorial-Play-button-bar.png)

> _Swift NSTimer Tutorial Play button bar_

Flexible Space Bar Button Item: This item will space out our bar button items. Drag this item on top of the tool bar that you already have at the bottom of your project:

![Swift NSTimer Tutorial Flexible Space Bar Item](http://ios-blog.co.uk/wp-content/uploads/2014/12/Swift-NSTimer-Tutorial-Flexible-Space-Bar-Item.png)

> _Swift NSTimer Tutorial Flexible Space Bar Item_

Bar Button Item (1): The next item is the Bar Button Item. Drag this item to the bottom left of your toolbar. Like we did before when we changed the identifier to play for the first button we need to do that again but this time change the identifier to Pause. This should now look like this:

![NSTimer Tutorial With Swift Pause Button](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Tutorial-With-Swift-Pause-Button.png)

> _NSTimer Tutorial With Swift Pause Button_

Navigation Bar: Drag the navigation bar to the op of your view controller. Do not put it right at the top as it will overlap the iPhone Battery icon. Double click the word 'Title' and Name it **NSTimer Tutorial**. This should now look like:

![NSTimer Tutorial Navigation Bar In Swift](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Tutorial-Navigation-Bar-In-Swift.png)

> _NSTimer Tutorial Navigation Bar In Swift_

Bar Button Item (2): Drag another Bar Button Item onto the navigation bar to the right and change the custom identifier to **Clear**. You can do this by double clicking the word '**Item**' and then changing it:

![NSTimer Bar Button Clear](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Bar-Button-Clear.png)

> _NSTimer Bar Button Clear_

UILabel: Finally, the last element. Drag this element onto your View Controller. Preferably in the middle of the project. Go to the Property Inspector and edit the label size, alignment and if you want colour. Next, Double click the UILabel and change the word '**Label**' to zero '**0**':

![NSTimer Tutorial Storyboard View Controller](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTImer-Tutorial-Storyboard-View-Controller.png)

> _NSTimer Tutorial Storyboard View Controller_

That's it for your project setup. Now we can start coding the **NSTimer**.

### NSTimer in Swift

In your Project Navigation Area select the file **ViewController.swift**. This is the file where we will define and program our **NSTimer** to use the custom class and perform actions.

In between these lines:
    
    
    1  
    2  
    3  
    
    class ViewController : UIViewController {  
    
      
    
    override func viewDidLoad() {
    
    
    

we need to define our **NSTimer**. The first variable that we are going to need is a variable called **timer** of type **NSTimer**. We do this like:
    
    
    1  
    
    var timer = NSTimer()
    
    
    

Next we need to define the counter. This will be initially set to zero. So under the above variable declaration we need to declare our variable **counter** of type integer. Like so:
    
    
    1  
    
    var counter = 0
    
    
    

On your UILabel in the middle of your storyboard **CTRL + Drag** to your View Controller file and give it the name of **countingLabel**:

![NSTimer Counting Label UILabel](http://ios-blog.co.uk/wp-content/uploads/2014/12/NSTimer-Counting-Label-UILabel.png)

> _NSTimer Counting Label UILabel_

This should then output the following lines of code into your ViewController.swift file:
    
    
    1  
    
    @IBOutlet var countingLabel: UILabel!
    
    
    

Do the same for the buttons: Play, Pause and Clear but this time select the connection type of: Action. This should then add these lines of code to your project:
    
    
    1  
    2  
    3  
    
    @IBAction func startButton(sender: AnyObject) { }  
    
    @IBAction func pauseButton(sender: AnyObject) { }  
    
    @IBAction func clearButton(sender: AnyObject) { }
    
    
    

Now we can assign values to the **countingLabel**. If we go into our **viewDidLoad** Method. Under **super.viewDidLoad()** we can add in some basic Swift that will get the variable of **counter** and assign it to the **countingLabel**. Hang on a minute! The counter is an integer and the UILabel is a string. we need to make sure we convert the output to string before passing it to the Label. This can simply be done by wrapping it in **String(*)**:
    
    
    1  
    
    countingLabel.text = String(counter)
    
    
    

### Start NSTimer

In out IBAction **startButton** we need to add in:
    
    
    1  
    
    timer = NSTimer.scheduledTimerWithTimeInterval(TIME_INCREMENT, target:self, selector: Selector("FUNCTION"), userInfo: nil, repeats: BOOL)
    
    
    

What this line will do is assign a new instance of **NSTimer** to the variable **timer** that we created earlier. As you can see in the line there are a few things I have added in in capitals; **TIME_INCREMENT**,**FUNCTION**,**BOOL**. Here are those parameters and what we're going to do with them.

Parameter Usage

TIME_INCREMENT
The number of seconds between firings of the timer. If seconds is less than or equal to 0.0, this method chooses the nonnegative value of 0.1 milliseconds instead. We are going to set this to 1.

FUNCTION
A function that we will create that will be triggered on the time. We are going to call this updateCounter.

BOOL
If YES, the timer will repeatedly reschedule itself until invalidated. If NO, the timer will be invalidated after it fires. We are going to set this to yes

so now, this line should look like:
    
    
    1  
    
    timer = NSTimer.scheduledTimerWithTimeInterval(1, target:self, selector: Selector("updateCounter"), userInfo: nil, repeats: true)
    
    
    

The next thing we need to do is create the function that we declared here: **Selector("updateCounter")** and update the counter integer by a value of 1. We do this similar to the way that we defined in the **viewDidLoad** however we need to add **++** to the counter as this will add 1 every time it is called. Which as you remember we told the **NSTimer.scheduledTimerWithTimeInterval** to call it every second. Like so:
    
    
    1  
    2  
    3  
    
    func updateCounter() {  
    
        countingLabel.text = String(counter++)  
    
    }
    
    
    

Run your app, Press start and see the magic and simplicity of coding **NSTimer with Swift**

### Pause/Stop NSTimer

This class comes with the method **invalidate()** Which is the perfect way to stop / pause your **NSTimer**. In the IBAction that we created for the pause button we simply need to add in one line of code:
    
    
    1  
    2  
    3  
    
    @IBAction func pauseButton(sender: AnyObject) {  
    
        timer.invalidate()  
    
    }
    
    
    

Run your app, Press the pause button and notice how easy it is to use **NSTimer with Swift**

### Clear the NSTimer Counter

Clearing the **NSTimer** is a little different as we need to do several things when the button is pressed:

  * Stop **NSTimer** from firing
  * Reset the counter
  * Clear the countingLabel on the View

Note: These must be done in the above order.

They are all simple to do, your final **IBAction** should look like:
    
    
    1  
    2  
    3  
    4  
    5  
    
    @IBAction func clearButton(sender: AnyObject) {  
    
        timer.invalidate()  
    
        counter = 0  
    
        countingLabel.text = String(counter)  
    
    }
    
    
    

There you have it. Run your app. and Voila. As you can see you have created a basic counting app using NSTimer and Swift.

### Subclassing NSTimer

I thought that I would just quickly mentioned subclassing with **NSTimer**.  
What is subclassing? Well.. A class can inherit all sorts from another class like methods and properties and many more characteristics. It is this, when one class inherits from another class that it is known as subclassing.

It is recommended in the [Apple Documentation](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSTimer_Class/index.html) for **NSTimer** that you do not try to subclass this class.

### Summary

In this **NSTimer Swift Tutorial** we have learned how to use **NSTimer** to call a custom function at a certain time interval. We have learned how to pause, start and clear the **NSTimer** in Swift. We have also learned how to deal with integers and strings.

### Download the files

In order to download these files we ask that you do us a litter favour and help us spread the word about this awesome Swift NSTimer tutorial with other people, Just click one of the social media buttons below and the files will be yours:
