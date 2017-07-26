# Swift Tutorial: Repeating Steps with Loops

_Captured: 2015-11-25 at 20:53 from [www.raywenderlich.com](http://www.raywenderlich.com/117456/swift-tutorial-repeating-steps-with-loops)_

_Note from Ray:_ This is an abridged version of a chapter from the [Swift Apprentice](http://www.raywenderlich.com/store), to give you a sneak peek of what's inside the book, released as part of the [iOS 9 Feast](http://www.raywenderlich.com/113226/introducing-the-ios-9-feast). We hope you enjoy!

![A Swift 2 tutorial for the iOS 9 Feast!](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_Swift2-250x250.jpg)

> _[A Swift 2 tutorial for the iOS 9 Feast!](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_Swift2.jpg)_

In this tutorial, you'll learn how to control the flow of execution, this time using loop statements.

Loop statements allow you to perform the same operation multiple times. That may not sound very interesting or important, but loops are very common in computer programs.

For example, you might have code to download an image from the cloud; with a loop, you could run that multiple times to download your entire photo library. Or if you have a game with multiple computer-controlled characters, you might need a loop to go through each one and make sure it knows what to do next.

Let's get started!

## Ranges

Before you dive into the loop statements themselves, you need to know about one more data type called a _Range_, which lets you represent a sequence of numbers. Let's look at two types of `Range`.

First, there's _closed range_, which you represent like so:
    
    
    let closedRange = 0...5

The three dots (`...`) indicate that this range is closed, which means the range goes from 0 to 5, inclusive of both 0 and 5. That's the numbers `(0, 1, 2, 3, 4, 5)`.

Second, there's half-open range, which you represent like so:
    
    
    let halfOpenRange = 0..<5

Here, you replace the three dots with two dots and a less-than sign (`..<`). Half-open means the range goes from 0 to 5, inclusive of 0 but not of 5. That's the numbers `(0, 1, 2, 3, 4)`.

You need to know about ranges because they're commonly used with loops, the main focus of this tutorial.

## Loops

Loops are Swift's way of executing code multiple times. In the following sections, you'll learn about two variants of loops available to you in Swift: `for` loops and `while` loops. If you know another programming language, you'll find the concepts and maybe even the syntax familiar.

### For Loops

First, let's turn to the _for loop_. This is probably the most common loop you'll see, and you'll use them to run code a certain number of times, incrementing a counter at each stage.

You construct a `for` loop like this:

The loop begins with the `for` keyword, followed by three expressions:

  1. You set up the loop with an initial condition, such as the value of a variable. 
  2. The loop runs as long as the loop condition is `true`. 
  3. At the end of each loop, the loop runs the iteration code. 

Here's an example:
    
    
    let count = 10
     
    var sum = 0
    for var i = 1; i <= count; i++ {
      sum += i
    }

In the code above, you set up the loop with a variable called `i` that you initially assign the value of 1; the loop runs until `i` is no longer less than or equal to `count` (that is, until `i` is greater than `count`).

Inside the loop, you add `i` to the `sum` variable, and at the end of each iteration of the loop, you increment `i` by 1.

In terms of scope, the `i` variable is only visible inside the scope of the `for` loop, which means it's not available outside of the loop.

This loop runs 10 times to calculate the sequence `1 + 2 + 3 + 4 + 5 + ...` all the way up to 10.

Here are the values of the variables for each iteration:

  * _Before iteration 1:_ `i` = 1, `sum` = 0 
  * _After iteration 1:_ `i` = 2, `sum` = 1 
  * _After iteration 2:_ `i` = 3, `sum` = 3 
  * _After iteration 3:_ `i` = 4, `sum` = 6 
  * _After iteration 4:_ `i` = 5, `sum` = 10 
  * _After iteration 5:_ `i` = 6, `sum` = 15 
  * _After iteration 6:_ `i` = 7, `sum` = 21 
  * _After iteration 7:_ `i` = 8, `sum` = 28 
  * _After iteration 8:_ `i` = 9, `sum` = 36 
  * _After iteration 9:_ `i` = 10, `sum` = 45 
  * _After iteration 10:_ `i` = 11, `sum` = 55 

Xcode's playground gives you a handy way to visualize such an iteration. Hover over the `sum += i` line in the results pane, and you'll see a white dot on the right. Hover over that dot to reveal a plus (+) button:

![01_Loop_before_graph](http://cdn5.raywenderlich.com/wp-content/uploads/2015/10/01_Loop_before_graph-480x267.png)

Click this plus (+) button and Xcode will display a graph underneath the line within the playground code editor:

![02_Loop_after_graph](http://cdn3.raywenderlich.com/wp-content/uploads/2015/10/02_Loop_after_graph-480x267.png)

This graph lets you visualise the `sum` variable as the loop iterates.

There's another way to implement the same `for` loop, and it involves using a special `for` loop called a _for-in loop_. Instead of having to create a variable to hold the loop counter and increment it yourself, you can iterate through a _range_, like so:
    
    
    let count = 10
    var sum = 0
     
    for i in 1...count {
      sum += i
    }

This code executes in exactly the same way as the previous loop and computes the same number; it's simply a more succinct way of doing so. Because of this, `for-in` loops are desirable over standard `for` loops wherever possible.

Finally, sometimes you only want to loop a certain number of times, and so you don't need to use the loop variable at all. In that case, you can employ the underscore once again, like so:
    
    
    let count = 10
    var sum = 1
    var lastSum = 0
     
    for _ in 0..<count {
      let temp = sum
      sum = sum + lastSum
      lastSum = temp
    }

This code doesn't require the loop variable; the loop simply needs to run a certain number of times. In this case, the range is 0 through `count` and is half-open. This is the usual way of writing loops that run a certain number of times.

### While loops

The next type of loop continues to iterate only while a certain condition is true. Because of this, it's called the _while loop_.

You create a `while` loop this way:

Every iteration, the loop checks the condition. If the condition is `true`, then the loop executes and moves on to another iteration. If the condition is `false`, then the loop stops. Just like `for` loops and `if` statements, `while` loops introduce a scope.

The simplest `while` loop takes this form:

This is a `while` loop that never ends, because the condition is always `true`. Of course, you would never write such a `while` loop, because your program would spin forever! This situation is known as an _infinite loop_, and while it might not cause your program to crash, it will very likely cause your computer to freeze.

![force_quit](http://cdn4.raywenderlich.com/wp-content/uploads/2015/10/force_quit-480x178.png)

Here's a more useful example of a `while` loop:

This code calculates a mathematical sequence, up to the point where the value is greater than `1000`. The loop executes as follows:

  * _Before iteration 1:_ `sum` = 1, loop condition = true 
  * _After iteration 1:_ `sum` = 3, loop condition = true 
  * _After iteration 2:_ `sum` = 7, loop condition = true 
  * _After iteration 3:_ `sum` = 15, loop condition = true 
  * _After iteration 4:_ `sum` = 31, loop condition = true 
  * _After iteration 5:_ `sum` = 63, loop condition = true 
  * _After iteration 6:_ `sum` = 127, loop condition = true 
  * _After iteration 7:_ `sum` = 255, loop condition = true 
  * _After iteration 8:_ `sum` = 511, loop condition = true 
  * _After iteration 9:_ `sum` = 1023, loop condition = false 

After the ninth iteration, the `sum` variable is `1023`, and therefore the loop condition of `sum < 1000` becomes false. At this point, the loop stops.

### Repeat-while Loops

Another variant of the `while` loop is called the _repeat-while loop_. It differs from the `while` loop in that the condition is evaluated _at the end_ of the loop rather than at the beginning.

You construct a `repeat-while` loop like this:

Here's the example from the last section, but using a `repeat-while` loop:

In this example, the outcome is the same as before. However, that isn't always the case--you might get a different result with a different condition. Consider the following `while` loop:

And now consider the corresponding `repeat-while` loop, which uses the same condition:

In the case of the regular `while` loop, the condition `sum < 1` is `false` right from the start. That means the body of the loop won't be reached! The value of `sum` will equal `1`, because the loop won't execute any iterations.

In the case of the `repeat-while` loop, however, `sum` will equal `3` because the loop will execute once.

### Breaking out of a loop

Sometimes you want to break out of a loop early. You can do this using the `break` keyword, which immediately stops the execution of the loop and continues on to the code after the loop.

For example, consider the following code:
    
    
    var sum = 1
     
    while true {
      sum = sum + (sum + 1)
      if (sum >= 1000) {
        break
      }
    }

Here, the loop condition is `true`, so the loop would normally iterate forever. However, the `break` means the `while` loop will exit once the sum is greater than or equal to `1000`. Neat!

You've seen how to write the same loop in different ways, demonstrating that in computer programming, there are often many ways to achieve the same result. You should choose the method that's easiest to read and conveys your intent in the best way possible, an approach you'll internalize with enough time and practice.

### Labeled Statements

Sometimes you want to be able to skip a loop iteration. For example, if you were going through a range but wanted to skip over all odd numbers, you don't want to break out of the loop entirely--you just want to skip the current iteration but let the loop continue.

You can do this by using the `continue` keyword, which immediately finishes the current iteration of the loop and begins the next iteration.

To demonstrate this, I'll use an example of a chess board that's an 8 by 8 grid, where each cell holds a value of the row multiplied by the column, like a multiplication table:

![03_Full_board](http://cdn1.raywenderlich.com/wp-content/uploads/2015/10/03_Full_board-496x500.png)

The first code example will calculate the sum of all cells, excluding all even rows. To illustrate, it will sum the following cells:

![04_First_board_example](http://cdn5.raywenderlich.com/wp-content/uploads/2015/10/04_First_board_example-496x500.png)

Using a `for` loop, you can achieve this as follows:
    
    
    var sum = 0
     
    for row in 0..<8 {
      if row % 2 == 0 {
        continue
      }
     
      for column in 0..<8 {
        sum += row * column
      }
    }

When the row modulo 2 equals 0, the row is even. In this case, `continue` makes the `for` loop skip to the next row.

Just like `break`, `continue` works with both `for` loops and `while` loops.

The second code example will calculate the sum of all cells, excluding those where the column is greater than or equal to the row. To illustrate, it will sum the following cells:

![05_Second_board_example](http://cdn1.raywenderlich.com/wp-content/uploads/2015/10/05_Second_board_example-496x500.png)

Using a `for` loop, you can achieve this as follows:
    
    
    var sum = 0
     
    rowLoop: for row in 0..<8 {
      columnLoop: for column in 0..<8 {
        if row == column {
          continue rowLoop
        }
        sum += row * column
      }
    }

This last code block makes use of _labeled statements_, labeling the two loops as the `rowLoop` and the `columnLoop`, respectively. When the row equals the column inside the inner `columnLoop`, the outer `rowLoop` will continue.

You can use labeled statements like these with `break` to break out of a certain loop, if you like. Normally, `break` and `continue` work on the inner-most loop, so you need to use labeled statements if you want to manipulate an outer loop.

## Where To Go From Here?

In this tutorial, you've learned about all the kinds of loops you can use in Swift. With ranges, loops and loop control statements such as `break` and `continue`, you'll be able to get your Swift code running and repeating exactly as you intend!

Hopefully this has piqued your interest to learn more about Swift. This post is an excerpt from the [Swift Apprentice](http://www.raywenderlich.com/store/swift-apprentice). Pick up a copy of the book if you'd like to learn more about Swift right from the foundations.

If you have any questions or comments on this tutorial, please join the forum discussion below!
