# Learn to Code iOS Apps with Swift Tutorial 3: Arrays, Objects, and Classes

_Captured: 2015-11-25 at 19:33 from [www.raywenderlich.com](http://www.raywenderlich.com/114234/learn-to-code-ios-apps-with-swift-tutorial-3-arrays-objects-and-classes)_

![Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Learn to Code iOS Apps in this Swift Tutorial - for complete beginners to programming!_

_Update note:_ This tutorial was updated for iOS 9 and Swift 2 by Brian Moakley. [Original post](http://www.raywenderlich.com/76044/learn-to-code-ios-apps-with-swift-tutorial-3) by [Mike Jaoudi](http://www.raywenderlich.com/u/MJaoudi) and [Ry Bristow](http://www.raywenderlich.com/u/rgbthe4).

Congratulations, you made it to part 3 of our Learn to Code iOS Apps with Swift tutorial series!

In the [first part of the series](http://www.raywenderlich.com/?p=114148), you learned the basics of programming with Swift. You learned about variables, if/else statements, loops, optionals, and more.

In the [second part of the series](http://www.raywenderlich.com/?p=114173), you put your new Swift skills to the test by making a simple number guessing game.

In this third part of the series, you will create a simple command-line app to record the names and ages of people.

Along the way, you will be learning about some more Swift concepts like Arrays, Objects, and Classes. Let's get started!

_Note:_ For this part of the series, you will be developing a command-line OS X app since it is one of the simplest ways to get started. Therefore, you will need Xcode 6.1 or later to complete this part of the tutorial. Please double check your version of Xcode before continuing.

## Getting Started

Open Xcode and create a playground file, by clicking on _Get started with a playground_:

![1-Welcome_To_Xcode_New_Playground](http://cdn1.raywenderlich.com/wp-content/uploads/2014/06/1-Welcome_To_Xcode_New_Playground2-340x320.png)

Set the name to _Person_, the platform to _iOS_, and click _Next_. Save the playground wherever you wish.

Delete this line to start from a blank slate:
    
    
    var str = "Hello, playground"

## Classes and Objects

A _class_ is like a blueprint that describes how an object should act and what it should do. It determines what methods can be used to manipulate the object and what characteristics the object should have.

In this project, you will be creating a class called `Person`. You will then be able to create methods in this class and give it characteristics such as name and age so that it can serve its purpose in your program.

First, add the class declaration to the playground:

Next, you need to add some _properties_ to this class. Properties are variables that each instance of the class has. For example, each person has a first name, last name, and age.

Adding properties is just like creating variables, except you add them inside the class declaration. Add a few properties into the class like so:
    
    
    class Person  {
     
      var firstName = ""
      var lastName = ""
      var age = 0
     
    }

In addition to properties, classes can have _methods_. Methods are operations that do something on the class - for example, you might want to add a method to print the user to the screen - in fact, you'll do that later!

First things first, for this app you're going to need a method to ask the user for information. Copy and paste these lines right after the `age` property:
    
    
    func input() -> String {
      let keyboard = NSFileHandle.fileHandleWithStandardInput()
      let inputData = keyboard.availableData
      let rawString = NSString(data: inputData, encoding:NSUTF8StringEncoding)
      if let string = rawString {
        return string.stringByTrimmingCharactersInSet(NSCharacterSet.whitespaceAndNewlineCharacterSet())
      } else {
        return "Invalid input"
      }
    }

This is a method that gets user input as a string. Don't worry about how it works for now; you'll learn how to write your own method in the next section.

## Writing Your Own Method

For this class, you are going to need to write three methods:

  1. `changeFirstName()` to allow a user to change their name
  2. `enterInfo()` to prompt the user to enter their info
  3. `printInfo()` to print the information to the console

Let's start with `changeFirstName()`. This method will take a value and set the first name of the `Person` to that value.

The first thing you are going to need to do is type in the method header. Place this below the `input()` method, but still in `Person`:

Great! You just completed the first step in writing your own method. Now, you need to figure out what goes in the method. The part of the header inside the parentheses creates a variable called `newFirstName` of type `String`. You will have to set the first name of the `Person` object to `newFirstName`. The body of the method should look like this:

You can put any code you'd like inside a method, this was just a very simple example.

At this point your file should look like the following:
    
    
    import UIKit
     
    class Person  {
     
      var firstName = ""
      var lastName = ""
      var age = 0
     
      func input() -> String {
        let keyboard = NSFileHandle.fileHandleWithStandardInput()
        let inputData = keyboard.availableData
        let rawString = NSString(data: inputData, encoding:NSUTF8StringEncoding)
        if let string = rawString {
          return string.stringByTrimmingCharactersInSet(NSCharacterSet.whitespaceAndNewlineCharacterSet())
        } else {
          return "Invalid input"
        }
      }
     
      func changeFirstName(newFirstName:String) {
        firstName = newFirstName
      }
     
    }

Now let's try out your class!

## Using Your Class

To create an instance of your `Person` class, go down to the bottom of your playground file and use the line:

What you just did was created the object `newPerson` of type `Person` and set it equal to an initialized `Person` object.

Now try setting the properties of your person class:

If you move your mouse over the right hand size and click on the eye icon next to the last line, you'll see that you have been updating the properties inside your `newPerson` object:

![Inspector](http://cdn5.raywenderlich.com/wp-content/uploads/2014/07/Inspector-700x101.png)

Cool, eh? You can use the new method you wrote like this:

Over on the righthand side of the window, you should see that the values associated with your object have changed to include `"Paul"` as the value stored in `firstName`.

That's the basics of using a class - let's just extend it a bit!

## More Methods

Now that you know how writing and using your own methods works, lets move on to the methods you will need for your project. The first one will be called `enterInfo()`. Just like before, the first thing you have to do is create the method header. Write this method header below the `changeFirstName()` method in your class `Person`:

Now, let's work on the body.In order to get the user to enter in what you want them to enter in, you have to tell them what you want. Let's use a `print()` statement for this.

This statement should go inside the curly braces of the method. This is called the method body. After this line, you should set the variable `firstName` to `input()`.

You will add more to this method later. For now, let's move on to `printInfo()`. The purpose of this method is to print the information about the `Person` object. It should look like this:

Congratulations, you have finished prototyping your class! It's nice to prototype things in a Playground like this when possible because it's a quick and easy way to experiment with new things before making a full app.

Here is the [Person.playground](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/Person.playground.zip) at this point.

Now let's put this to use in a command line tool!

## Creating a Class with a Swift File

Open up Xcode (if it is not already open) and click the button that says _Create a new Xcode project_. If you accidentally close the "Welcome to Xcode" window or already have an Xcode project open, you can create a new project by going to the _File_ menu and selecting _New > Project_. Then, in the OS X section, select _Application_ and then _Command Line Tool_ and click _Next_.

![2-Select_Command_Line_Tool_2](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/2-Select_Command_Line_Tool_2-426x320.png)

On the following screen, fill in the fields as indicated:

  * _Product Name:_ PeopleDatabase
  * _Organization Name:_ This field can be left blank. Or you can enter your company name.
  * _Organization Identifier:_ Enter _com.yourname_, such as _com.bmoakley_
  * _Language:_ Swift
![Naming_PeopleDatabase](http://cdn3.raywenderlich.com/wp-content/uploads/2014/06/Naming_PeopleDatabase-480x283.png)

Now, go to _File\New\File_ and choose the _OS X\Source\Swift File_ template, and click _Next_.

![Screen Shot 2015-09-09 at 11.56.41 AM](http://cdn1.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-11.56.41-AM-450x320.png)

> _[Screen Shot 2015-09-09 at 11.56.41 AM](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/Screen-Shot-2015-09-09-at-11.56.41-AM.png)_

Name the file _Person.swift_ and click _Create_.

Inside Person.swift, copy the Person class that you prototyped in your Playground (but not the test code). It should look like this:
    
    
    import Foundation
     
    class Person  {
     
      var firstName = ""
      var lastName = ""
      var age = 0
     
      func input() -> String {
        let keyboard = NSFileHandle.fileHandleWithStandardInput()
        let inputData = keyboard.availableData
        let rawString = NSString(data: inputData, encoding:NSUTF8StringEncoding)
        if let string = rawString {
          return string.stringByTrimmingCharactersInSet(NSCharacterSet.whitespaceAndNewlineCharacterSet())
        } else {
          return "Invalid input"
        }
      }
     
      func changeFirstName(newFirstName:String) {
        firstName = newFirstName
      }
     
      func enterInfo()  {
        print("What is the first name?")
        firstName = input()
      }
     
      func printInfo()  {
        print("First Name: \(firstName)")
      }
     
    }

Before you move on to working in the _main.swift_ file, you should finish up your methods in your `Person` class. To do this, you will have to add prompts and input statements for the last name and the age of the `Person` in the `enterInfo()` method and the ability to print these two pieces of information in the `printInfo()` method. Here is what the `enterInfo()` method should look like:
    
    
    func enterInfo()  {
      print("What is the first name?")
      firstName = input()
      print("What is \(firstName)'s last name?")
      lastName = input()
      print("How old is \(firstName) \(lastName)")
      let userInput = Int(input())
      if let number = userInput {
        age = number
      }
    }

Make sure you aren't just copying and pasting the code each time it is provided for you. Take the time to go through and examine the different parts of it. That is how you will learn. This block of code has a `print()` statement and an input statement for each of the variables, but the one for `age` is a bit more complicated.

Since `age` is of type `Int` instead of `String`, it requires the `toInt()` method. If this seems familiar, it's because you've used it before! Remember, this conversion requires that you use the `if let` statement in case an input is entered that cannot be converted to an `Int`.

Now, try to update the `printInfo()` method yourself. Try to get the output to say something like:

If you get stuck, here is a possible solution:

If you want to double check your work, here is what _Person.swift_ should look like after this section.

## Testing Your Class

Click on _main.swift_ in the Project Navigator, and replace the contents with the following:

Now press run and try out your application!
    
    
    What is the first name?
    Ry
    What is Ry's last name?
    Bristow
    How old is Ry Bristow
    18
    Ry Bristow is 18 years old
    Program ended with exit code: 0
    

Congratulations - you have made your first class!

## The Repeat While Loop

For this next section, you'll need the helper functions from the previous tutorial, so download them [here](http://cdn2.raywenderlich.com/wp-content/uploads/2014/10/helpers.swift_.zip). Drag _helpers.swift_ into your Xcode project, and make sure that you select the option to copy the items into the project.

It would be nice to allow the user to enter more than one person when you run the app. To do this, let's try out a new loop.

This one is called the e called the `repeat...while` loop. The repeat while loop used to be called the do while loop. It was renamed in Swift 2.0 to avoid conflicting with another Swift feature.

The repeat while is different than a `while` loop because it executes once, no matter what, before it checks the condition to see if it should continue to run.

First, create a string variable called `response` directly below the `import` statement.

Below that, start the `do...while` loop out with

Then, cut everything below it and paste it into the body of the loop.

In order to make it so that the loop will continue as long as the user wants, you have to prompt them to ask if they want to continue and set `response` to that value. Enter these lines of code before the closing curly brace of the `do...while` loop.

Now, the user will tell the program to continue or not by either entering `y` for yes and `n` for no (although technically, anything but a `y` will exit the loop).

If you want to double check your work, here is what _main.swift_ should look like after this section.

Test your program again by pressing the run button. Try entering several names by entering `y` each time and then exiting by entering `n`
    
    
    What is the first name?
    Ry
    What is Ry's last name?
    Bristow
    How old is Ry Bristow
    18
    Ry Bristow is 18 years  old
    Do you want to enter another name? (y/n)
    y
    What is the first name?
    Ray
    What is Ray's last name?
    Wenderlich
    How old is Ray Wenderlich
    34
    Ray Wenderlich is 34 years  old
    Do you want to enter another name? (y/n)
    n
    Program ended with exit code: 0
    

## Arrays

Each time you go through the loop, the program completely forgets about information that has already been processed. Arrays are objects that can store other objects in a list, and allow you to access them. Declare an array underneath this line:

by entering the following:

You just created an array called `people` that stores objects of type `Person`. By a surrounding the class name with `[]` brackets, you have declared it as an array. By setting it equal to `[]`, you made it an empty array that doesn't contain anything.

To add an object to the array, you use the method `append()`. Let's give this a try. Insert the following line of code between the `enterInfo()` and `printInfo()` method calls in the loop.

Now, every time you create the `newPerson` object by prompting the user for information, you add the object to the Array. To finish up the project, add a few more useful `print()` statements outside of the loop.

This first line will let the user know how many people they entered into the database by counting how many objects are in the Array `people`.

Run your app again, and enter two names. When you're done, you will see the following:

## For Loops

There's one last thing to cover: a `for` loop. This loop is an easy way to iterate through all of the elements in an array. This is perfect if you want to print out the entire database of people at the end!

Let's try it out. Add these lines to the bottom of _main.swift_:

What this loop will do is work its way through the Array `people` one object at a time. Each time it goes through the loop, the object at the next index will be set to `onePerson` until it has gone through them all.

Next add this line to the body of the loop:

This line will print the information about each `Person` object in the array `people` after the user has entered them all in.

Nice job! Here is what the full text of your _main.swift_ file should look like after you are done. If you have a problem somewhere and can't figure it out, use this to help you.

You're done - build and run to try the final version! Here is an example of what the output should look like after you have run the application:

![Example_Output](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/Example_Output-480x316.png)

## Where to Go From Here?

The final project with full source code can be found [here](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/PeopleDatabase.zip)

You're now ready to move on to the [next tutorial](http://www.raywenderlich.com/?p=114262) in this series, where you'll learn to make your first iPhone game!

If you have any question or comments, come join the discussion on this series in the forums!
