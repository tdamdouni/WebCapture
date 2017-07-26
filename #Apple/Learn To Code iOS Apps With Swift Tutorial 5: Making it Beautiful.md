# Learn To Code iOS Apps With Swift Tutorial 5: Making it Beautiful

_Captured: 2015-11-25 at 19:34 from [www.raywenderlich.com](http://www.raywenderlich.com/114298/learn-to-code-ios-apps-with-swift-tutorial-5-making-it-beautiful)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!_

_Update note:_ This tutorial was updated for iOS 9 and Swift 2 by Brian Moakley. [Original post](http://www.raywenderlich.com/78264/learn-to-code-ios-apps-with-swift-tutorial-5) by [Mike Jaoudi](http://www.raywenderlich.com/u/MJaoudi) and [Ry Bristow](http://www.raywenderlich.com/u/rgbthe4).

Congratulations, you made it to the final part of our Learn to Code iOS Apps with Swift tutorial series!

In the [first part of the series](http://www.raywenderlich.com/?p=114148), you learned the basics of programming with Swift. You learned about variables, if/else statements, loops, optionals, and more.

In the [second part of the series](http://www.raywenderlich.com/?p=114173), you put your new Swift skills to the test by making a simple number guessing game.

In the [third part of the series](http://www.raywenderlich.com/?p=114234), you created a simple command-line app to record the names and ages of people.

In the [fourth part of the series](http://www.raywenderlich.com/?p=114262), you created your first simple iPhone app.

In this fifth and final part of the series, how about you take the game from last time and make it look a little more visually appealing?

This part of the series will teach you how to use images for the background of different objects on the screen to spice it up a bit. Also, you will learn how to implement background music and sound effects. Let's get started!

## Getting Started

You'll start from the project where you left it off last time, so [download a copy](http://cdn4.raywenderlich.com/wp-content/uploads/2014/07/TapMeFinal.zip) if you don't have it already.

I recommend that you make a copy of the project folder before you begin. This way, you will still have your original version of the app before you change what the interface looks like. This is not only good because you can compare your two finished versions, but it also allows you to have the original, working version if you mess up something while trying to change the interface.

![Screen Shot 2014-07-28 at 3.56.23 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/Screen-Shot-2014-07-28-at-3.56.23-PM-480x304.png)

> _[Screen Shot 2014-07-28 at 3.56.23 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/Screen-Shot-2014-07-28-at-3.56.23-PM.png)_

Then, you'll want to download the [Tap Me Resources](http://cdn3.raywenderlich.com/wp-content/uploads/2014/07/TapMe_Resources.zip), which is basically a collection of the images and sounds that you will need for this project. After you download it, you should open up the folder and select all of the items inside. Drag these items over to the Supporting Files folder in your Document Outline.

Make sure _Copy items if needed_ is selected so that the project will still work on another computer or if you move/delete the resources file from your downloads folder.

![Screen Shot 2015-09-09 at 6.09.15 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.09.15-PM-480x281.png)

> _[Screen Shot 2015-09-09 at 6.09.15 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.09.15-PM.png)_

## Setting A Button's Background Image

Rather than just having your button's background be a solid color, it looks a lot better when you create an image in a photo editing program. To set the background image, you have to do it based on what state the button is in. Make sure the state of the button is set to default in the Attributes Inspector. This is the state of the button when nothing is happening to it.

![Screen Shot 2015-09-09 at 6.10.44 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.10.44-PM.png)

> _[Screen Shot 2015-09-09 at 6.10.44 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.10.44-PM.png)_

Then, find the box that mentions the _Background_, and set it to _button_tap_deselected.png_

![Screen Shot 2015-09-09 at 6.13.28 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.13.28-PM.png)

> _[Screen Shot 2015-09-09 at 6.13.28 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.13.28-PM.png)_

In your previous version of the app, you had the background of the button set to be white. Change it back to the default of no color so it doesn't show behind the image.

![Screen Shot 2015-09-09 at 6.15.03 PM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.15.03-PM.png)

> _[Screen Shot 2015-09-09 at 6.15.03 PM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.15.03-PM.png)_

![1Screen Shot 2014-07-18 at 12.47.27 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/1Screen-Shot-2014-07-18-at-12.47.27-PM-301x320.png)

> _[1Screen Shot 2014-07-18 at 12.47.27 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/1Screen-Shot-2014-07-18-at-12.47.27-PM.png)_

Uh oh! The image is hard to read since the button title is still "Tap Me!". Since the words are a part of the image, you can go ahead and get rid of the title.

![Screen Shot 2015-09-09 at 6.16.06 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.16.06-PM.png)

> _[Screen Shot 2015-09-09 at 6.16.06 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.16.06-PM.png)_

![1Screen Shot 2014-07-18 at 12.49.25 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/1Screen-Shot-2014-07-18-at-12.49.25-PM-298x320.png)

> _[1Screen Shot 2014-07-18 at 12.49.25 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/1Screen-Shot-2014-07-18-at-12.49.25-PM.png)_

Much better! Now, the button is legible and looks a whole lot better than it did in your previous version of the app. Rather than a boring white rectangle with some text in it, you now have a 3-dimensional-looking button with colors and better looking text.

Your next step is to set the background image for the same button when it is in the highlighted state. This is the state of the button when it is being clicked by the user. It should have the _Background_ field set to _button_tap_selected.png_.

![Screen Shot 2015-09-09 at 6.17.32 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.17.32-PM.png)

> _[Screen Shot 2015-09-09 at 6.17.32 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.17.32-PM.png)_

You may notice your button looks a little bit squished at this point. This is because you have hardcoded width and height constraints that are smaller than the image itself.

Luckily, there is an easy way to fix this. All views have something called an _intrinsic content size_, which you can think of as an automatic constraint that is set to the size of the element being presented. In the case of an image, it will be the size of the image itself.

So rather than having hardcoded width and height constraints, you can rely on the intrinsic content size of the image to size the image view appropriately.

Let's try this out. In the document navigator, find the width and height constraints for the button and hit delete to remove them:

![DeleteConstraints](http://cdn5.raywenderlich.com/wp-content/uploads/2014/08/DeleteConstraints-480x271.png)

Then, update all the frames in your view controller to match their constraints by clicking on the triangle icon in the bottom right and selecting _All Views\Update Frames_.

![Screen Shot 2015-09-09 at 6.20.38 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.20.38-PM.png)

> _[Screen Shot 2015-09-09 at 6.20.38 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-6.20.38-PM.png)_

Build and run, and enjoy your big button!

![BigButton](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/BigButton-179x320.png)

## Adding Images to the Screen

Sometimes, you may want to add images to the screen that do not act as buttons. In this case, you can use a `UIImageView`. Find _Image View_ in the Object Library and drag one onto the screen.

You will be using this Image View object to create a border, so you will want to position and resize it so that it stretches from the left side of the screen to the right side of the screen and touches the top part of the screen. Do the same with another Image View object for the bottom border.

![Screen Shot 2014-07-18 at 1.35.13 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-1.35.13-PM-302x320.png)

> _[Screen Shot 2014-07-18 at 1.35.13 PM](http://cdn5.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-1.35.13-PM.png)_

Move your labels a bit to make room. The easiest way to do this is to just update their constraints using the Edit button in the size inspector. Select the _Timer_ Label, and in the Size Inspector in the Constraints section, click the _Edit_ button in the _Top Space to: Top Layout Guide_ constraint.

![UpdateConstraint](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/UpdateConstraint.png)

Now, set the constraints for the top Image View. Click the _Pin_ button. First, make sure to _uncheck_ the _Constrain to margins_ checkbox. Next, _click_ the _left_, _top_, and _right T-bars_ . Make sure each has a value of _0_. Finally, _check_ the _Height_ constraint. Make sure it has a value of _22_. When done, _click_ the button that reads, _Add 4 Constraints_.

![Screen Shot 2015-09-10 at 9.44.58 AM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-9.44.58-AM-213x320.png)

> _[Screen Shot 2015-09-10 at 9.44.58 AM](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-9.44.58-AM.png)_

If you see the orange lines, make sure to update the frames as described earlier in the tutorial.

Do the same to the bottom Image View. Try setting the constraints based on the previous instructions. If you get stuck, check the spoiler.

Select the top Image View and in the Inspector, set the _Image_ to _chekecker_top.png_. Set the _Mode_ to _Aspect Fill_.

![Screen Shot 2015-09-10 at 10.10.29 AM](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.10.29-AM.png)

> _[Screen Shot 2015-09-10 at 10.10.29 AM](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.10.29-AM.png)_

Do the same for the bottom Image View except set the _Image_ to _checker_bottom.png_.

Run the app again and enjoy your beautiful borders!

![Borders](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/Borders-179x320.png)

## Programmatically Setting the Background Color

You don't always have to go through Storyboard to change the way your app looks. Let's change the background color to purple to test this out. Try adding this line inside of `viewDidLoad()` in _ViewController.swift_:
    
    
    view.backgroundColor = UIColor.purpleColor()

What this line of code does is it takes the `backgroundColor` attribute of the `view` and sets it to the `UIColor` object returned by the method `purpleColor()`.

Now run the app and check out what it looks like.

![Screen Shot 2014-07-18 at 2.01.48 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-2.01.48-PM-175x320.png)

> _[Screen Shot 2014-07-18 at 2.01.48 PM](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-2.01.48-PM.png)_

Although this shows proof of concept, it still doesn't look that great. However, lucky for you, you can also set the background of the view to an image. Let's do this in the program again. Replace the line where you set the background color to purple with the following:

This line tiles the image to fill the background of the view. Run the app to see what it looks like.

![Screen Shot 2014-07-18 at 2.02.48 PM](http://cdn1.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-2.02.48-PM-174x320.png)

> _[Screen Shot 2014-07-18 at 2.02.48 PM](http://cdn5.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-2.02.48-PM.png)_

While you're at it, go ahead and programmatically set the background of both labels as well. To do this, type in the following two lines of code.

Run the app and see what it looks like now.

![Screen Shot 2014-07-18 at 2.03.48 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-2.03.48-PM-176x320.png)

> _[Screen Shot 2014-07-18 at 2.03.48 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-07-18-at-2.03.48-PM.png)_

## Positioning and Sizing Labels

There are a couple things that could use some improvement here. One thing is that the positioning and sizes of the labels are off. `scoreLabel` is obviously too high up and its size and shape do not fit its image.

To fix this, select the top label and use the _Pin_ button to add constraints to set its _width_ to _133_ and _height_ to _46_:

![Screen Shot 2015-09-10 at 10.30.59 AM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.30.59-AM-216x320.png)

> _[Screen Shot 2015-09-10 at 10.30.59 AM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.30.59-AM.png)_

Then select the bottom label, find its current height constraint in the Project Navigator, and hit delete to remove it:

![RemoveScoreCosntraint](http://cdn1.raywenderlich.com/wp-content/uploads/2014/08/RemoveScoreCosntraint-480x245.png)

Then use the Pin button to add constraints to set its _width_ to _146_ and _height_ to _102_:

![Screen Shot 2015-09-10 at 10.40.00 AM](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.40.00-AM-210x320.png)

> _[Screen Shot 2015-09-10 at 10.40.00 AM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.40.00-AM.png)_

Finally, clear your selection, click the third button, and choose _All Views in View Controller\Update Frames_ to apply the constraints.

One final tweak. The background that you are using for the labels makes it nearly impossible to read black text on. To solve this, change the text color to a light blue that goes well with the rest of the interface. Use these values for the best results. Make sure you do this for both `timeLabel` and `scoreLabel`.

![Screen Shot 2015-09-10 at 10.42.50 AM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.42.50-AM.png)

> _[Screen Shot 2015-09-10 at 10.42.50 AM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-10-at-10.42.50-AM.png)_

Also set the alignment of each label to center justified.

Now, run the app to see how much easier it is to read the newly colored text!

![Screen Shot 2014-08-10 at 11.29.56 AM](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-08-10-at-11.29.56-AM-174x320.png)

> _[Screen Shot 2014-08-10 at 11.29.56 AM](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-08-10-at-11.29.56-AM.png)_

## Adding Sound

Music and sound effects are great ways to add character to your app. That's the last thing this app is missing!

But first, you'll need some sounds. [Download these sounds](http://cdn5.raywenderlich.com/wp-content/uploads/2014/08/Sounds.zip), unzip the file, and the three sound files into your project.

The three sound files are: background music, a beep for every time the player taps the button, and a beep for every second that passes on the countdown clock, just to make the player sweat a little!

The sound playback will be handled from the view controller code, so open up _ViewController.swift_. Near the top of your file, you'll notice this line

You will also need to use an import statement for the AVFoundation framework, which is the Apple framework responsible for playing sound and video. Add the following statement immediately following the previous import statement mentioned.

Just as importing UIKit lets you use things like UIButton and UILabel, importing AVFoundation lets you use the very useful _AVAudioPlayer_ class. Next, you'll need an instance variable for each of the three sounds. Add a line for each instance variable just after the declaration of other instance variables inside the class body.

Since the _AVAudioPlayer_ may not able available, the instance variables are declared as optionals.

Next, you will need to add this helper method above the _viewDidLoad_ method.
    
    
      func setupAudioPlayerWithFile(file:NSString, type:NSString) -> AVAudioPlayer?  {
        //1
        let path = NSBundle.mainBundle().pathForResource(file as String, ofType: type as String)
        let url = NSURL.fileURLWithPath(path!)
     
        //2
        var audioPlayer:AVAudioPlayer?
     
        // 3
        do {
          try audioPlayer = AVAudioPlayer(contentsOfURL: url)
        } catch {
          print("Player not available")
        }
     
        return audioPlayer
      }

This method will return an AVAudioPlayer object (declared by the `->`), and takes two arguments: a file name and type. Let's look at what it does by section.

  1. You need to know the full path to the sound file, and `NSBundle.mainBundle()` will tell you where in the project to look. AVAudioPlayer needs to know the path in the form of a URL, so the full path is converted to URL format. 
  2. You'll notice that `audioPlayer` is an optional. There may be a condition where an `AVAudioPlayer` may not be created depending on the device that is trying to instantiate it
  3. This is where you try to create the `AVAudioPlayer`. Since creating the object may throw an error, you start the block with the `do` keyword. Next, you try to create the player. If the player is unable to be created, you then catch error. In this case, an error is just being printed to the console but in a real application, you would place your error handling in that block. This error handling code is new in Swift 2.0.
  4. If all goes well, the AVAudioPlayer object will be returned! 

Now that you have a handy method that will set up AVAudioPlayer objects, it's time to use it! Add this code to the `viewDidLoad()` method, at the top of the method _before_ `setupGame()`:
    
    
    if let buttonBeep = self.setupAudioPlayerWithFile("ButtonTap", type:"wav") {
      self.buttonBeep = buttonBeep
    }
    if let secondBeep = self.setupAudioPlayerWithFile("SecondBeep", type:"wav") {
      self.secondBeep = secondBeep
    }
    if let backgroundMusic = self.setupAudioPlayerWithFile("HallOfTheMountainKing", type:"mp3") {
      self.backgroundMusic = backgroundMusic
    }

Here you create each of the players. If the players are able to be created, the objects will be assigned to instance variables.

At this point in `viewDidLoad`, you'll have all three sounds ready to be called in your code!

The first sound, buttonBeep, should play when the button is pressed. Update the `buttonPressed` method to play the sound by adding this line at the end of its method body:

By adding a question mark after the variable name, you are trying to call a method on an optional. If there is an object, then the method will be called. Otherwise, the code will be ignored.

There are two other sounds to add. The `secondBeep` sound should be played every second when the timer ticks down. Add the call to play that sound in `subtractTime()` method by adding this line right before the `if` statement.

You're almost done!

The final step is to add the background music. To play the music every time a new game is started, add the play code to the `setupGame()` method. Add these lines to the very bottom of the method body:

You can adjust the volume of the background music so the beeps can still be heard. Changing the `volume` attribute of the `backgroundMusic` is a good way to do this. It can be set from 0 (off) to 1.0 (full volume), but 0.3 is a good starting point.

Now run the app for a final time and experience the glory of your fully featured app!

![FinalGame](http://cdn2.raywenderlich.com/wp-content/uploads/2014/08/FinalGame-179x320.png)

## Where To Go From Here?

Congratulations! You have just made your first iPhone app, and taken it from having very basic functionality, to being a polished looking and sounding app. [Here](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/TapMe2Final.zip) is a copy of the finished project for you to compare to your finished project.

There are lots of things that you can modify in your app, such as adding or changing some of the graphics, adding different levels, or even modifying the sound effects - the sky is the limit!

From here, you might want to go through the iOS Apprentice series, which goes much more into depth about making iOS apps. It's also for complete beginners, and you can get the first part for free by [signing up for our newsletter](http://www.raywenderlich.com/?page_id=4275).

In the meantime, if you have any questions or comments, please join the forum discussion below!
