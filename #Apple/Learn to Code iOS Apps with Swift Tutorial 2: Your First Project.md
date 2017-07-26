# Learn to Code iOS Apps with Swift Tutorial 2: Your First Project

_Captured: 2015-11-25 at 19:30 from [www.raywenderlich.com](http://www.raywenderlich.com/114173/learn-to-code-ios-apps-with-swift-tutorial-2-your-first-project)_

![Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!_

_Update note:_ This tutorial was updated for iOS 9 and Swift 2 by Brian Moakley. [Original post](http://www.raywenderlich.com/75919/learn-to-code-ios-apps-with-swift-tutorial-2) by [Mike Jaoudi](http://www.raywenderlich.com/u/MJaoudi) and [Ry Bristow](http://www.raywenderlich.com/u/rgbthe4).

Congratulations, you made it to part 2 of the Learn to Code iOS Apps with Swift tutorial series!

In the [first part of the series](http://www.raywenderlich.com/?p=114148), you learned the basics of programming with Swift. You learned about variables, if/else statements, loops, optionals, and more.

In this second part of the series, you'll put your new Swift skills to the test, by making a simple number guessing game!

You will be using a lot of the concepts that you learned in the first section, so feel free to use your [finished playground file](http://cdn1.raywenderlich.com/wp-content/uploads/2014/10/MyPlaygroundPart1.zip) from the previous tutorial to look up things that you may have forgotten how to do.

Get ready to get guessing!

_Note:_ For this part of the series, you will be developing a command-line OS X app since it is one of the simplest ways to get started. Therefore, you will need Xcode 6.1 or later to complete this part of the tutorial. Please double check your version of Xcode before continuing.

## Writing a Prototype

In this part of the tutorial series, you'll create an application that runs the classic game "Higher or Lower". The computer generates a secret random number and prompts you to guess what that number is. After each guess, the computer tells you if your guess was too high or too low until you get it right. The game also keeps track of how many guesses you take.

First, you are going to prototype your app in a Playground before you move on to actually creating the Command Line Tool Application. Open Xcode and create a playground file, by clicking on _Get started with a playground_:

![1-Welcome_To_Xcode_New_Playground](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/1-Welcome_To_Xcode_New_Playground2-340x320.png)

As in the previous tutorial, set the name to _MyPlayground_, the platform to _iOS_, and click _Next_. Save the playground wherever you wish.

![NewPlayground](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/NewPlayground2-700x408.png)

Remove the comment at the top and the declaration of the `String`, leaving just

Then, copy in the following block of code:
    
    
    func randomIntBetween(low:Int, high:Int) -> Int {
      let range = high - (low - 1)
      return (Int(arc4random()) % range) + (low - 1)
    }

You don't have to worry about what everything means here, except that it is the code a method that gives you a random number between a high and low number. Eventually, you will get to write your own methods, but for now, you can just use these that have been provided for you, just like you used `Int()` in [Part 1](http://www.raywenderlich.com/?p=75601) of this series.

## Time to Make a Game!

Time to start making the game! The first thing you need to do is tell the program to come up with a random number for the answer. One of the methods that was provided to you will come in handy here. Type the following line at the bottom of your playground file.

What you just did was declare a constant of type `Int` and initialized it to a random `Int` value between 1 and 100. That way, the answer will be different every time without you having to go in and manually change the code (that would make the game pretty lame).

Now, the user will need to know what they are supposed to do. You can use a `print()` statement for this. Enter in the next line:

Unfortunately, playgrounds do not allow for user input. You can include that when you move over to the Command Line Tool. For now, just create a new variable to hold an Int that represents the guess like this:

Time to use some more of your knowledge from [Part 1](http://www.raywenderlich.com/?p=75601). You need to use some conditionals to tell the user whether their guess is greater than, less than, or equal to the actual answer.

Go ahead and give it a try yourself. Don't be afraid to check back with [Part 1](http://www.raywenderlich.com/?p=75601) of the tutorial series or with the playground file that you created. If you get stuck, here is the solution.

## Creating a Command Line Tool Application

Playgrounds are great for testing out bits of code, but you can't actually get any input from a user or make an app with it.

To do that, you are going to need to create a different type of project in Xcode. In this tutorial, you will be using an OS X Command Line Tool, since this is one of the easiest ways to get started.

Remember - you must have Xcode 6.1 or later to continue with this part of the tutorial!

Open up Xcode (if it is not already open) and click the button that says _Create a new Xcode project_. If you accidentally close the "Welcome to Xcode" window or already have an Xcode project open, you can create a new project by going to the _File_ menu and selecting _New > Project_.

Then, in the OS X section, select _Application_ and then _Command Line Tool_ and click _Next_.

![2-Select_Command_Line_Tool_2](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/2-Select_Command_Line_Tool_2-426x320.png)

On the following screen, fill in the fields as indicated:

  * _Product Name:_ My First Project
  * _Organization Name:_ This field can be left blank. Or you can enter your company name.
  * _Organization Identifier:_ Enter _com.yourname_, such as _com.rybristow_
  * _Language:_ Swift
![3-Naming_My First Project](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/3-Naming_My-First-Project-480x284.png)

> _[3-Naming_My First Project](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/3-Naming_My-First-Project.png)_

Click _Next_. Choose somewhere to store the project files. I would suggest keeping it in a file with the Playground file from [Part 1](http://www.raywenderlich.com/?p=75601) of this series, just so you keep all that stuff together. Now click _Create_ and Xcode will set up your new project and open it for you.

## Running Your App

Just like when you first started your Playground file, Xcode creates the file with some code in it already. Try clicking the _Run_ button in the top left of the screen. It is the triangle that looks like a "Play" button.

![PlayButton](http://cdn3.raywenderlich.com/wp-content/uploads/2014/10/PlayButton.png)

When you press this button, Xcode runs your app. Check out the bottom of the screen. There is a box that stretches across the bottom. In the right half of this box, you should see that the program outputted the text `Hello, World!`.

![5-Console_Full](http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/5-Console_Full-480x108.png)

![5-Console_Left_Half](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/5-Console_Left_Half-480x150.png)

![5-Console_Right_Half](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/5-Console_Right_Half-480x148.png)

Before you go into writing your first app, here are some of the different features of Xcode.

## Xcode

The left pane of Xcode displays a list of files that are part of the project. The files you see were automatically created by the project template you used. Find _main.swift_ inside the _My First Project Folder_ and click on it to open it up in the editor, as shown below.

![Screen Shot 2015-09-08 at 4.19.56 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-4.19.56-PM.png)

> _[Screen Shot 2015-09-08 at 4.19.56 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-4.19.56-PM.png)_

The editor window should look very similar to the following screenshot.

![7-Editing_Window](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/7-Editing_Window-300x320.png)

This should look very familiar to you. The last line in the file: `print("Hello, World!")` is just like the `print()` statement that you worked with in Part 1 of this series. However, not everything is the same. As you worked within the Playground file, the right side of the screen kept track of the values of each variable as you typed. Swift files do not do that. However, Swift files are what you will actually use to create apps.

If you were using Objective-C to create apps, like you used to have to, there would be more to this basic file. There would be another line that declared a function called `main` that was necessary for kicking off the app. Swift no longer requires this function, but the project is set up to require a file named _main.swift_, so make sure you do not try to rename this file.

## From Prototype to Project

First, go ahead and delete the `print()` statement so all that is left is the comment section at the top and the line `import Foundation`.

Now, you can pull in some of the code from your playground file. Copy and paste the following code from your playground file into your _main.swift_ file, right below `import Foundation`
    
    
    let answer = randomIntBetween(0, high: 100)
     
    print("Enter a number between 1 and 100.")
     
    var guess = 7
     
    if(guess > answer) {
      print("Lower!")
    } else if(guess < answer) {
      print("Higher!")
    } else {
      print("Correct! The answer was \(answer).")
    }

Oh no! The code has an error. Don't worry, that's just because the computer doesn't know the method `randomIntBetween()`. To fix this, you need to download the helper file that has been written up for you [here](http://cdn2.raywenderlich.com/wp-content/uploads/2014/10/helpers.swift_.zip).

To use this new file, you first want to download it, then, open your downloads folder (or wherever you downloaded it to) and drag it into your Xcode window in the folder marked _My First Project_.

![8-Copy_File_Into_Project](http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/8-Copy_File_Into_Project-426x320.png)

Make sure that you select the option to copy the items into the project. That way, if the location of the original file is moved, your project will still have it.

![Screen Shot 2015-09-08 at 4.24.12 PM](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-4.24.12-PM-480x284.png)

> _[Screen Shot 2015-09-08 at 4.24.12 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-4.24.12-PM.png)_

Save the project and the error should go away.

## Allowing for User Input

Let's be honest, the game is pretty lame if you have to change the value of the variable and re-run the app manually every time you want to guess. You can fix this by allowing the user to input their guess. This is where the other method from the helpers.swift file you were provided with comes in handy.

In _main.swift_, hit enter a few times between

and

so you have some room to work with. Now, delete the line

as well.

First, you are going to want to create a constant to store what the user inputs. Enter the following line of code in the space you just created.

You just created a constant `userInput` to store a `String` that was entered by the user on the keyboard. That's great, but you can't compare a `String` to an `Int` to see which one is greater than the other. To do this, you first need to convert the `String` value entered by the user into an `Int`. See if you can do this by yourself from what you learned in [Part 1](http://www.raywenderlich.com/?p=75601). If you get stuck, I have provided the solution for you.

Hint: You will need to use an `if let` statement.

Since the block of code in between the `if let` curly braces will be the executed code if the input really is an `Int` value, that is where you should put the `if`/`else` statements from earlier that you currently have below. Your code should now look like this:
    
    
    import Foundation
     
    let answer = randomIntBetween(1, 100)
     
    print("Enter a number between 1 and 100.")
     
    let userInput = input()
    let inputAsInt = userInput.toInt()
     
    if let guess = inputAsInt {
      if(guess > answer) {
        print("Lower!")
      } else if(guess < answer) {
        print("Higher!")
      } else {
        print("Correct! The answer was \(answer).")
      }
    }  else  {
     
    }

Now, you should come up with a message for the user if their input is not valid. How about something like:

In the `else` block of the `if let` statement, add the following:

Press the run button to try your game out.

![SingleGuess](http://cdn1.raywenderlich.com/wp-content/uploads/2014/10/SingleGuess.png)

Great success! But it's kinda hard to win the game in just one guess.

## Implementing Rounds

Your game is almost done! All you have to do is add a few more things and you will have programmed your first Swift game. Right now, your game only lets you guess once. You're going to want it to keep asking you to guess until you get it right. To do this, you will use a `while` loop. You will only need a very simple `while` statement and you will use the code inside of it to tell the computer when to end it. Go ahead and add these lines at the very end of your code.

Cut everything except the declaration of the constant `answer` and paste it inside of this while loop.

Your file should now look like this:
    
    
    import Foundation
     
    let answer = randomIntBetween(0, high: 100)
    var turn = 1
     
    while(true) {
      print("Guess #\(turn): Enter a number between 1 and 100.")
     
      let userInput = input()
      let inputAsInt = Int(userInput)
      if let guess = inputAsInt  {
        if(guess > answer) {
          print("Lower!")
        } else if(guess < answer) {
          print("Higher!")
        } else {
          print("Correct! The answer was \(answer).")
          break
        }
      }  else  {
        print("Invalid input! Please enter a number.")
        continue
      }
      turn = turn + 1
    }
     
    print("It took you \(turn) tries.")

If you tried to run the app now it would never stop. (If you do on accident, press the stop button to the right of the run button) You need to implement a way of stopping it. Put to use the `break` statement that you learned in [Part 1](http://www.raywenderlich.com/?p=75601) of this series.

The `break` statement should be placed into the `else` part of the inner `if`/`else` statement like so:

This will cause the program to exit the loop when the user's input is equal to `answer`.

Last, but not least, you need a way to include how many turns it takes for the user to guess the right answer.

Create a new variable before the while loop called turn and set it equal to 1.

Now, adjust the `print()` statement so that it now includes what number guess it is for the user. It should look something like:

The best spot to increment the variable`turn` would be at the very end of the while loop. Enter this line on the line right before the last curly brace.

Then, place a `print()` statement after the while loop to let the user know how many guesses it took them to get it right.

One last suggestion would be to use a `continue` statement in the situation that an incorrect input is entered. That way, the user is not penalized for it. The `else` statement belonging to the `if let` statement should then become:

Your finished file should look like this:
    
    
    import Foundation
     
    let answer = randomIntBetween(0, 100)
    var turn = 1
     
    while(true)  {
     
      print("Guess #\(turn): Enter a number between 1 and 100.")
     
      let userInput = input()
     
      let inputAsInt = userInput.toInt()
      if let guess = inputAsInt  {
     
        if(guess > answer) {
          print("Lower!")
        } else if(guess < answer) {
          print("Higher!")
        } else {
          print("Correct! The answer was \(answer).")
          break
        }
     
      } else  {
        print("Invalid input! Please enter a number.")
        continue
      }
     
      turn = turn + 1
     
    }
     
    print("It took you \(turn) tries.")

Great job! Now run your app and enjoy your game!
    
    
    Guess #1: Enter a number between 1 and 100.
    10
    Higher!
    Guess #2: Enter a number between 1 and 100.
    50
    Higher!
    Guess #3: Enter a number between 1 and 100.
    80
    Lower!
    Guess #4: Enter a number between 1 and 100.
    60
    Higher!
    Guess #5: Enter a number between 1 and 100.
    70
    Higher!
    Guess #6: Enter a number between 1 and 100.
    75
    Lower!
    Guess #7: Enter a number between 1 and 100.
    73
    Correct! The answer was 73.
    It took you 7 tries.
    Program ended with exit code: 0
    

## Where to Go From Here?

The final project with full source code can be found [here](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/MyFirstProject.zip).

You're now ready to move on to the [next tutorial](http://www.raywenderlich.com/?p=114234) in this series, where you'll learn about some more fundamental concepts in Swift, including working with objects and classes.

If you have any question or comments, come join the discussion on this series in the forums!
