# Learn to Code iOS Apps with Swift Tutorial 1: Welcome to Programming

_Captured: 2015-11-25 at 19:27 from [www.raywenderlich.com](http://www.raywenderlich.com/114148/learn-to-code-ios-apps-with-swift-tutorial-1-welcome-to-programming)_

![Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!_

_Update note:_ This tutorial was updated for iOS 9 and Swift 2 by Brian Moakley. [Original post](http://www.raywenderlich.com/75601/learn-to-code-ios-apps-with-swift-tutorial-1) by [Mike Jaoudi](http://www.raywenderlich.com/u/MJaoudi) and [Ry Bristow](http://www.raywenderlich.com/u/rgbthe4).

Have you ever thought about how awesome it would be to make your own apps for your iPhone or iPad?

There's never been a better time to learn than now!

This is a tutorial series for complete beginners to iOS development, that will take you from the basics (like beginning Swift programming topics, or making a command-line app) all the way to making a full iOS app with a beautiful user interface.

With iOS app development, the sky is the limit. This Swift tutorial series will provide you with the basic knowledge you'll need to make the amazing apps you've dreamed of!

_Note:_ If you are a complete beginner to programming, this tutorial is for you! If you already have some experience with programming and want something faster paced, check out [this tutorial series](http://www.raywenderlich.com/?p=74438).

## Getting Started

The very first step is to download Xcode - the software program that you write your apps in. You can [download it for free](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) on the Mac App Store:

![Xcode on the Mac App Store](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/XcodeOnAppStore-700x375.png)

> _Xcode on the Mac App Store_

Be sure you have the latest version of Xcode - you need Xcode 6 or later to work with Swift.

Once you have Xcode installed, open Xcode and click the button that says _Get started with a playground_.

![Get Started with a Playground](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/GetStarted-480x281.png)

> _[Get Started with a Playground](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/GetStarted.png)_

_Note:_ If you don't see the "Welcome to Xcode" window, click _Window\Welcome to Xcode_ to display it.

A _playground_ is a simple way to experiment and play around with Swift code.

You cannot run a playground as an iPhone app, but it will be very important in helping you to understand the basics of Swift. Don't worry, you'll be creating your very own iPhone app soon enough!

Set the name to _MyPlayground_, the platform to _iOS_, and click _Next_. Save the playground wherever you wish.

![NewPlayground](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/NewPlayground2-700x408.png)

## Introduction to Playgrounds

You will see that the playground you created already has three lines of code:
    
    
    // Playground - noun: a place where people can play
     
    import UIKit
     
    var str = "Hello, playground"

Here's the breakdown of the playground, one line at a time.

This first line, which starts with two forward slashes, is called a _comment_.

This line is only there for you, or any other programmers that look at your code, to see. It does not affect the way that your code functions. Think of it as "a way to write notes in your code".

The second line imports UIKit, which you can think of as "a bunch of code written by the smart folks at Apple." All you need to know about this right now is that you need it for the rest of your code to work.

The third line is the one you should focus on right now.

This line creates a variable named _str_ that holds the value `Hello, playground`. On the right side of the window, you can see that Xcode is keeping track of what value this variable holds.

![PlaygroundRight](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/PlaygroundRight-480x117.png)

Try changing `"Hello, playground"` to `"Look what I can do!"`, like this:

Did you see how the right side of the window changed what it said too? Congratulations, you just did some programming!

![Victory is yours!](http://cdn1.raywenderlich.com/wp-content/uploads/2011/05/Screen-Shot-2012-11-05-at-5.36.16-PM-193x320.png)

> _Victory is yours!_

## Your Own Calculator

Now let's see what else you can do. At the bottom of your file, try typing a basic math expression such as `2 + 2` and hit enter to go to the next line:

The playground will give you the answer to your equation over in the shaded right side of the window:

![Calculator](http://cdn5.raywenderlich.com/wp-content/uploads/2014/06/Calculator-480x125.png)

Cool, eh? You can do any other math operation too.

_Challenge:_ Quick - try to use Playgrounds to tell me the result of 123 * 456!

Using playground as a simple calculator is great and all, but now let's move on and get into some more coding! Delete everything in the program except for `import UIKit` so you have a clean slate to work with.

It is extremely important that you leave that line there because the Playground will not work without it.

## Variables

Next, it's time for you to play with variables.

You use variables to store values. When you create a variable, you always use the following syntax:

Except you substitute the following:

  * `yourVariableName`: Whatever you want to name the variable, like `str` or `age` for example.
  * `yourType`: The type of the variable, like `String` or `Int`. More on that in a moment.
  * `yourInitialValue`: Whatever you want to set the initial value of the variable to, like "Look what I can do!" or 18.

Try an example! Add these lines to the bottom of your playground:

In the first line, you created a variable named `str` of type `String`, and set the initial value to "Look what I can do!"

In the second line, you created a variable named `age` of type `Int`, and set the initial value to 18.

You're starting to get a good idea how how to make a variable, but you may be wondering what the difference between `String` and `Int` types is, and what other types you can use.

## Types

Here is a list of some of the basic data types that Swift has to offer:

  * _Int_ - whole numbers, or integers
  * _Double_ - decimal numbers
  * _Bool_ - a value that can be true, or false
  * _String_ - a "string" of letters or words

Practice using these data types. Add the following lines to the bottom of your playground:

Notice how each of the values show up on the shaded right area of the window as the playground keeps track of them. Now, try changing the value of the String name.

Add the following line to the bottom of your playground:

This line did not require the use of `var` or `: String` because the object was already created. All you did here was change the value that it was storing.

_Challenge:_ Your turn to give it a try. At the bottom of the file, try creating a variable to represent your favorite video game.

## Constants

There are also special types of variables called constants.

Rather than declaring them with `var`, you use the keyword `let`. What this does, is it makes the immutable, or unchangeable.

Whenever possible, you should use `let` rather than `var` because it allows your code to run faster because the compiler doesn't have to account for the possibility that the value may be changed. Any data type can be used as a constant, just as any data type can be used as a variable.

Try creating some now. Add this code at the bottom of your playground file:

Now try assigning a new value to `captain`, such as `"Hook"`. Type this line of code at the bottom of your playground file:

Notice that a small red symbol with an exclamation mark comes up on the far left-hand side. This is telling you that an error has occurred in your code.

![Screen Shot 2015-09-08 at 2.22.45 PM](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-2.22.45-PM.png)

> _[Screen Shot 2015-09-08 at 2.22.45 PM](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-2.22.45-PM.png)_

Click on the symbol, and see that the error message _Cannot assign to 'let' value 'captain'_ pops up. This is telling you that since you initialized the variable with `let`, therefore making it a constant, its value cannot be changed.

![itsbroke](http://cdn3.raywenderlich.com/wp-content/uploads/2014/03/itsbroke-480x177.png)

Remove the line `captain = "Hook"` to get rid of the error.

_Challenge:_ Make a constant named `favoriteNumber` of type `Int`, and set the value to your favorite number.

## Inferred Typing

Tired of typing yet? No need to fear, Swift is smarter than you might think.

There is a new feature in Swift called _Inferred Typing_. This means that if you provide enough information when declaring and initializing the variable, Swift can predict the data type so you don't have to include it every time.

Not only does this save time and energy from typing, but it also makes your program less cluttered and easier to follow.

To try this, find your line that says `var luckyNumber: Int = 7` and replace it with the following:

![Well, that's convenient!](http://cdn1.raywenderlich.com/wp-content/uploads/2014/05/convenient-280x320.jpg)

> _[Well, that's convenient!](http://cdn1.raywenderlich.com/wp-content/uploads/2014/05/convenient.jpg)_

This may not seem like that big of a deal right now, but it will save you a lot of typing in the long run!

Just remember, inferred typing only works if you provide the right amount of information. If you wanted `luckyNumber` to be a `Double`, you would have had to set it equal to `7.0` (to make it clear that it's a decimal number, rather than `7` which is an integer).

_Challenge:_ Go back and try to make sure all of your variables and constants use inferred typing.

## Comparison Operators

Just like Playground can do simple math operations as explained earlier, it can compare numbers and values. Some of these operators include:

  * _>_ Greater Than
  * _<_ Less Than
  * _==_ Equal To
  * _>=_ Greater Than or Equal To
  * _&&_ AND 
  * _||_ OR 

You can use these operators to compare two values.

Give this a try! First, add these lines to the bottom of your playground to declare some variables and initiate them with values:

Great! Now you can use these two variables to test our comparison operators. Place the following block of code at the end of your Playground file.

Review the results in the shaded right-hand side of the window. Playground will evaluate your statements and tell you if they are true or false.

![Screen Shot 2015-09-08 at 2.26.54 PM](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-2.26.54-PM-480x110.png)

> _[Screen Shot 2015-09-08 at 2.26.54 PM](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-08-at-2.26.54-PM.png)_

For the AND statements (`&&`), both comparisons have to be true. For the OR statements (`||`), only one of the two comparisons has to be true. If the first one is true, the program doesn't even bother to evaluate the second because there is no need to.

_Challenge:_ Try adding a new variable for Spiderman called `spidermanCoolness` and give him a coolness value. Then try using some of the comparison operators (like >, <, ==, &&, and ||) to compare Spiderman's coolness to other superheroes. _(Notice that I made batmanCoolness a constant so you can't change it ;) )_

## If/else statements

In if/else statements, the computer executes a certain block of code if a condition is true, and does not execute the code if the condition is false.

Add this example to the bottom of your playground:
    
    
    if (batmanCoolness > spidermanCoolness) {
      spidermanCoolness = spidermanCoolness - 1
    } else if (batmanCoolness >= spidermanCoolness) {
      spidermanCoolness = spidermanCoolness - 1
    } else {
      spidermanCoolness = spidermanCoolness + 1
    }

This block of code decreases Spiderman's coolness if Batman is cooler, but increases Spiderman's coolness if Spiderman is cooler.

As you can tell from the Playground, Spiderman's coolness decreases to 6 from the realization that he is not as cool as Batman. As you can see from the grey area, the program never goes through the `else if` statement, even though it is true. That is because the program has already found that the first `if` statement was true, so it doesn't even look at the rest of the code in the if/else statements.

_Challenge:_ Create your own control flow statements using the superheroes from the last example. Remember, none of the `if` or `else if` statements have to be true. The program will either perform the `else` statement if you have one, or just move on to what is next in the program.

## Simple Functions

Functions are blocks of code that perform a certain task. For example, a function named `printMyFavoriteSnack()` might print out `"Pringles"`.

![Mic Pringle, iOS Team Lead](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/MicPringle.jpg)

> _Mic Pringle, iOS Team Lead_

You can either write and use your own functions, or use functions written by other programmers. For example, Apple has provided a bunch of built-in functions that do useful things that you can use in your apps.

One example is the `print()` function. When you call `print`, the program "prints" whatever you type inside the parentheses to the console.

Let's try a quick example. Type the following at the bottom of your file:

You should see "Hello, World" printed out on the right hand side.

Programming anything involves using a lot of different functions. Sometimes you use functions written by Apple or by other people, as you have just done, and sometimes you write your own, as you will experience further along.

_Challenge:_ Try changing the string inside the `print()` function to say something nice about yourself. Also, try putting one of the superhero coolness factor variables in there and see what happens.

## String Interpolation

Printing strings to the console is great and all, but wouldn't it be great if you could combine a string and the value from a variable in the same print statement?

Good news, everyone! You can! It's called String Interpolation.

This is very useful when you want to say something like "Sally has (some value) apples." Try out this code at the bottom of your playground:

See that? By using the format `\\(_variable name_)`, you can put the value of any variable you want into a String. You can even perform operations inside the parentheses if you want. Add this code to the bottom of your playground:

Nice job! String Interpolation is something that you will be using for just about every program that you write.

![35_making_progress](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/35_making_progress.png)

_Challenge:_ Now it's time to combine some of the concepts that you have learned. Create two variables for grades for students in a class: John's grade (95), and Sam's Grade (85). Then make an if/else statement that compares John's and Sam's grade, and prints out whether John's grade is less than, greater than, or equal to Sam's grade. You can do it!

## While Loops

While loops are another kind of control flow statement, like the if/else statements you learned earlier. They are similar in the fact that they require a condition to execute.

However, instead of simply executing its code block once, while statements continue to execute the code block as long as its condition remains true. Type out this example at the bottom of your playground.
    
    
    var secondsLeft = 3
    while (secondsLeft > 0) {
      print(secondsLeft)
      secondsLeft = secondsLeft - 1
    }
    print("Blast off!")

Make sure that you code some way of making sure that the condition becomes false at some point. You do not want to create an infinite loop because it will cause all kinds of problems and your program will not reach anything after the loop.

When you run this, you will see the line `(3 times)` on the right hand side, which represents that the `print()` statement is running each time. Since there are multiple values printed out, you have to bring up another window called the _Assistant Editor_ to see them.

To do this, go to the top of your screen and select _View\Assistant Editor\Show Assistant Editor_. In the box marked Console Output, you should be able to see what you printed:

![AssistantEditor](http://cdn1.raywenderlich.com/wp-content/uploads/2014/11/AssistantEditor-480x159.png)

_Challenge:_ Go ahead and try writing your own while loop - for example make a while loop about a cop eating a box of donuts. Remember, no infinite loops!

## Break Statement

Say you have some kind of loop in your program, like a while loop, and you want to exit the loop if a specific thing happens. That's where the `break` command comes in. Follow along with this example by writing out the code at the end of your playground.
    
    
    var cokesLeft = 7
    var fantasLeft = 4
    while(cokesLeft > 0)  {
      print("You have \(cokesLeft) Cokes left.")
      cokesLeft = cokesLeft - 1
      if(cokesLeft <= fantasLeft)  {
        break
      }
    }
    print("You stop drinking Cokes.")

In this example, you want to keep drinking Coke until there are none left. However, you realize that you also have Fanta in the fridge. You decide you should stop drinking Coke when you have the same amount or less than Fanta because then you would have to start drinking the Fanta to even it out. When this situation occurs, you exit the loop, and thereby stop drinking the Coke.

_Challenge:_ Now it's your turn to try. Create a while loop that eventually has an ending point - for example a loop about goofing off until the boss stops by. In that loop, add an if statement where you use `break` to exit from the loop.

## Continue Statement

The continue statement is very similar to the break statement, however, instead of exiting from the loop, it just sends the program back to the beginning of the loop. Type in the example below at the end of your playground.
    
    
    var numbers = 0
    while(numbers <= 10)  {
      if(numbers == 9)  {
        numbers = numbers + 1
        continue
      }
      print(numbers)
      numbers = numbers + 1
    }

As you can see from what the program printed to the console, every number from 0 to 10 was printed except 9 because of the continue statement. It's too bad that 7 ate 9, but for that reason, you can't include him in our list.

![rocket_mouse_unity_p2_1](http://cdn4.raywenderlich.com/wp-content/uploads/2014/03/rocket_mouse_unity_p2_1.png)

_Challenge:_ Use continue in your own loop. Find a reason to have a specific value miss commands that other values have to execute and use the continue statement to go to the top of the loop.

## Optionals

Sometimes, due to the use of different functions, you don't know if a variable will have a value or not. When it does not have a value, it is said to contain `nil`. This is where optionals come in.

Optionals are variables that can either contain a value or contain `nil`. Declare an optional and notice you can set it to `nil`:

The `?` is what declares the value as an optional. To figure out if optionals contain a value or are set to nil, you use something called an `if let` statement. It looks something like this:

`if let` statements act similar to `if` statements. If `optionalNumber` contains an `Int`, `number` is set to that value and the code inside the `if let` curly braces is executed.

Optionally, you can set up an `else` statement to execute if `optionalNumber` happens to be nil.

_Challenge:_ Try this out yourself. Write an `if let` statement for `optionalNumber` to print different Strings if it contains a value or if it is nil.

## Conversion Between Data Types

Let's see how this can be useful in a program. Optionals can help you to convert between variable types. Try the example below where a `String` is converted into an `Int`.

Here, after declaring and initializing `languagesLearned` as a `String` with the value `"3"`, you declare the optional `languagesLearnedNum` and initialize it with the method `toInt()`. Methods are very similar to functions like `print()` that you learned earlier, except that they are a part of a `class`. You will learn more about that later.

`Int()` is a constructor that allows you to create a new int from a string value. The reason that you have to set an optional like `languagesLearnedNum` equal to that value is because it has the potential to be `nil`. This occurs if the `String` you are trying to convert does not contain a numerical value, but contains something like `"Hello, World"`.

Enter in the following code to test this out:
    
    
    if let num = languagesLearnedNum  {
      print("It is a number")
    }
    else  {
      print("It is not a number")
    }

The `if let` statement tests to see if `languagesLearnedNum` actually contains a value, or if it is nil. If it contains a value, that value is passed to `num` and the code inside the curly braces is executed. If not, the code inside of the `else` curly braces is executed.

See what happens if you change the `String` in `languagesLearned` to `"Three"`. The program should print `"It is not a number"` to the console because languagesLearnedNum will be set to `nil` when the program tries to convert `"Three"` to an `Int`.

## Putting it all together

_Challenge:_ Last one! Try creating your own variables where you try to convert a `String` to an `Int`. Then, compare these variables to other variables you set in `if` statements that contain `print()` statements. These `print()` statements should contain `String`s with `String` Interpolation so you can say which values are greater than/less than which values.

## Where To Go From Here?

Here is the [finished playground file](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/MyPlayground.playground.zip) for this tutorial series so far.

Check out the [next part](http://www.raywenderlich.com/?p=114173) of the series, where you'll learn how to take your Swift knowledge and make a simple command-line number guessing game!

If you have any questions or comments, please join the forum discussion below!
