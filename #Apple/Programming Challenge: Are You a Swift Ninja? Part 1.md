# Programming Challenge: Are You a Swift Ninja? Part 1

_Captured: 2015-11-25 at 20:30 from [www.raywenderlich.com](http://www.raywenderlich.com/76349/swift-ninja-part-1)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Are you a Swift Ninja?](http://cdn4.raywenderlich.com/wp-content/uploads/2014/07/ninja_swift-250x250.png)

> _Are you a Swift Ninja?_

_Update 8/5/14_: Series updated for Xcode6-beta 5.

Although Swift has only been out for a little while and is still in beta, many of you have been digging in already.

How far have you come so far? Have you:

  * Read Apple's [Swift Programming Language](https://itunes.apple.com/book/the-swift-programming-language/id881256329?mt=11) book?
  * Read Apple's [Using Swift with Cocoa and Objective-C ](https://itunes.apple.com/book/using-swift-cocoa-objective/id888894773?mt=11) book?
  * Ported or written a project in Swift?
  * Read at least 5 blog posts or tutorials on Swift?
  * Visited the #swift-lang IRC group?
  * Subscribed to the [Swift language mailing list](https://groups.google.com/forum/#!forum/swift-language)?
  * Signed up for email updates when [Chris Lattner posts](https://devforums.apple.com/people/ChrisLattner)?

If you've scored 3 or more on this quiz, then you might be a _Swift Ninja_.

Well, this 2-part series is going to help you find out for sure!

I'll give you a series of programming challenges in Swift, that you can use to test your Swift knowledge and see if you're a true _Swift Ninja_.

And if by any chance you're not feeling so ninja, you'll have the chance to learn the craft! No matter whether you're already advanced or still intermediate in Swift, you'll likely still learn a thing or two.

In addition, [part 2](http://www.raywenderlich.com/?p=77845) of this tutorial has a special _final challenge_, where you will get a chance to win a free copy of our upcoming [Swift by Tutorials Bundle](http://www.raywenderlich.com/?page_id=74805), which includes three books about programming in Swift.

Get your shurikens and katana ready - the challenge begins!

_Note:_ This post is for experienced programmers who are well-versed in the Swift language. If you don't feel quite at ease with it yet, check out [the rest of our Swift tutorials](http://www.raywenderlich.com/?page_id=2519).

## The Challenge

This series is a bit different in style compared to the ones we usually post on this web site. It will present a series of problems in order of increasing complexity. Some of these problems reuse techniques from previous sections, so working through them in order is essential for your success.

Each of the problems highlight at least one feature, syntax oddity, or clever hack made possible by Swift.

Don't worry, you'll not be thrown to the wolves - there's help when you need it. Each post has two levels of hints, and of course there's always the Swift books from Apple, or your good friend Stack Overflow.

### How to Approach Each Problem

Each problem is defined by stating what you need to accomplish in code, and what Swift features you can and can't use. I recommend you use a Playground to work through the each challenge.

If you have difficulties, open up the _Hints_ section. Though _Hints_ won't give you instant gratification, they offer direction.

In case you can't muster the solution -- open up the problem's _Tutorial_ section. There you'll find the techniques to use and provide the code to solve the given problem. In any case, by the end of this series you'll have the solutions to all the problems.

Oh - and remember to track your score!

  * If you solve the problem _without peeking at the hints or tutorial sections_ you get 3 shurikens: 
  * If you solve the problem _by peeking at the hints section_, you get 2 shurikens: 
  * If you solve the problem _by peeking at the tutorial section_, you get 1 shuriken: 

Even if you solved the problem yourself, take a few moments to see the solution provided in the Tutorial -it's always great to compare code!

Some challenges offer an extra shuriken if you do the solution in a certain (more difficult) way.

Keep a piece of paper or your favorite tracking app handy and keep count of how many shurikens you got for each challenge.

Don't cheat yourself by padding your score. That's not the way of the noble ninja. At the end of the post you'll have broadened your mind and moved boldly into the future, even if you don't collect every single shuriken.

## The Swift Ninja challenge

### Challenge #1

In the Swift book from Apple, there are several examples of a function that swaps the values of two variables. The code always uses the "classic" solution of using an extra variable for storage. But you can do better than that.

Your first challenge is to write a function that takes two variables (of any type) as parameters and swaps their values.

Requirements:

  * For the function body use a single line of code

Give yourself if you don't have to crack open the _Hints_ or _Tutorial_ spoilers.

### Challenge #2

Swift functions are very flexible -- they can take a variable number of arguments, return one or more values, return other functions and much more.

For this challenge you'll test your understanding of function syntax in Swift. Write a function called _flexStrings_ that meets the following requirements:

  * The function can take precisely 0, 1 or 2 string parameters.
  * Returns the function parameters concatenated as `String`.
  * If no parameters pass to the function, it will return the string "none".
  * For an extra shuriken use one line of code for the function body.

Here's some example usage and output of the function:

Take for solving the problem, and an extra shuriken for a total of 4 if you did it in one line.

### Challenge #3

You've already mastered functions with optional parameters in the previous challenge. That was fun!

But with the approach from the previous solution, you can only have a fixed maximum number of parameters. There's a better approach if you _truly_ want a variable number of input values for a function.

This challenge demonstrates how to best use the built-in `Array` methods and `switch` statements. Did you pay attention when you read Apple's [Swift Programming Language](https://itunes.apple.com/book/the-swift-programming-language/id881256329?mt=11) book? You're about to find out. :]

Write a function called `sumAny` that can take 0 or more parameters of any type. The function should meet the following requirements:

  * The function will return the sum of the passed parameters as a `String`, following the rules below.
  * If a parameter is an empty string or an Int equal to 0, add -10 to the result.
  * If a parameter is an `String` that represents a positive number (e.g. "10", not "-5"), add it to the result.
  * If a parameter is an `Int`, add it to the result.
  * In any other case, do not add it to the result.
  * For an extra shuriken - write the function as a single `return` statement and don't use any loops (i.e. no `for` or `while`).

Here's some example calls to the function with their output, so you can check your solution:

### Challenge #4

Write a function `countFrom(from:Int, #to:Int)` that will produce as output (eg. via `print()` or `println()`) the numbers from `from` to `to`. You can't use any loop operators, variables, nor any built-in Array functions. Assume the value of `from` is less than `to` (eg. the input is valid).

Here's a sample call and its output:

## Where To Go From Here?

![Get your revenge in part 2!](http://cdn1.raywenderlich.com/wp-content/uploads/2014/07/Ninja_Swift2-250x250.png)

> _Get your revenge in part 2!_

Ninjas need to take breaks, too. And if you made it this far you're doing a fantastic job -- you deserve some rest!

I'd like to take this time to reflect a bit on the problems and the solutions so far. Swift is very powerful, and is a much more expressive and safe language than Objective-C is.

With the first 4 problems in this challenge, I wanted to push you into exploring various areas of Swift. I hope working on the first few problems so far has been fun and beneficial experience.

Let's do a small recap:

  * So far, none of the solutions required you to declare any variables -- you probably don't need them as much as you think!
  * You didn't use any loops either. Reflect on that!
  * Parameters with default values and variadic parameters make Swift functions incredibly powerful.
  * It's very important to know the power of the basic built-in functions like `map`, `reduce`, `sort`, `countElements`, etc.

And if you're truly looking to take your mind off programming for a bit you watch the classic opening sequence from the game Ninja Gaiden:

Stay tuned for [part 2](http://www.raywenderlich.com/?p=77845) of the Swift Ninja programming challenge - where you can get your revenge! :]
