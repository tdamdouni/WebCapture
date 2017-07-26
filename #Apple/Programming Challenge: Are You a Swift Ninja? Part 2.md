# Programming Challenge: Are You a Swift Ninja? Part 2

_Captured: 2015-11-25 at 20:32 from [www.raywenderlich.com](http://www.raywenderlich.com/77845/swift-ninja-part-2)_

![Are you a Swift Ninja?](http://cdn4.raywenderlich.com/wp-content/uploads/2014/07/ninja_swift1-250x250.png)

> _Are you a Swift Ninja?_

_Update 8/5/14_: Series updated for Xcode6-beta 5.

Welcome back to our "Are you a Swift Ninja?" Programming Challenge!

In the [first part of this series](http://www.raywenderlich.com/?p=76349), you got some practice with default values in functions, variadic parameters, map/reduce, advanced switch statement features, and more.

Hopefully, you earned plenty of shurikens along the way!

In this second and final part of the series, you will get 4 more challenges to test your ninja skills.

In addition, this tutorial has a special _final challenge_, where you will get a chance to compete against other developers for fame and fortune!

The best solution to the final challenge will be featured in this post, and will also get a free copy of our upcoming [Swift by Tutorials Bundle](http://www.raywenderlich.com/?page_id=74805), which includes three books about programming in Swift.

Ninja mode activate - the challenge continues!

### Challenge #5

Stretch those fingers and assume the position. It's time to do another problem that involves recursion and function syntax.

Write a single function that reverses the text in a string. For example, when passed the string "Marin Todorov" will return the string "vorodoT niraM".  
Requirements:

  * You can't use any loop operators nor subscripts (i.e. no square brackets in the code).
  * You can't use any built-in `Array` functions.
  * Don't use variables.

Here's an example of a function call and its output:
    
    
    reverseString("Marin Todorov") //--> "vorodoT niraM"

### Challenge #6

Your next challenge has to do with operator overloading -- one of the most powerful features of Swift. I hope you've had a chance to look into how to do that :]

Your challenge is to overload the "`*`" operator so it takes a `Character` and an `Int` and produces a `String` with the character repeated Int times.

Here's an example usage and output:

Make usage of everything you learned so far and don't use any variables, loops, inout parameters, or subscripts.

You might need to define an extra auxiliary function. At the time of writing, Xcode crashes when you try to define a nested function inside an operator overload. Hopefully this is corrected at some point.

### Challenge #7

This challenge, while not necessarily pushing you to write beautiful and optimized code, will lead you to discover (or exercise) another very powerful feature of Swift.

"What's that?" you might ask. Well, you'll just have to work through it and figure that out for yourself!

For this challenge you'll need to use this function:

This function, for the purpose of writing and testing your solution, randomly succeeds or fails (eg. returns `true` or `false`).

Write code (and/or additional functions) that will output the message "success!" when `doWork()` returns `true`, and will output "error" when `doWork()` returns `false`. Your solution should meet the following requirements:

  * You can't modify the source of `doWork()`.
  * You can't use `if`, `switch`, `while`, or `let`.
  * You can't use the ternary operator `?:`.

### Challenge #8

Currying is a relatively unexplored area outside of functional languages like ML, SML, and Haskel. But as you may have noticed from the presentations at WWDC, Swift has this feature as well -- and the Apple engineers seem to be pretty excited about it.

Are you up to the challenge of using currying and partial function application?

Extend the `Array` structure and add 3 new functions that you could call like this on an array of any type:

  1. `list.swapElementAtIndex(index: Int)(withIndex: Int)`: Returns a copy of the original array with the elements at indexes `index` and `withIndex` exchanged.
  2. `list.arrayWithElementAtIndexToFront(index: Int)`: Returns a copy of the original array with the element at index `index` exchanged with the first element .
  3. `list.arrayWithElementAtIndexToBack(index: Int)`: Returns a copy of the original array with the element at index `index` exchanged with the last element.

(The examples above use an array called `list`).

Requirements:

  * You can use the keyword `func` only one time - to declare `swapElementAtIndex`.

Here is an example of usage and its output:

## The Final Challenge

![Ninja_Swift3](http://cdn4.raywenderlich.com/wp-content/uploads/2014/07/Ninja_Swift3-250x250.png)

Time for the last challenge. This time there will be no hints and no tutorial. It's all on you, dear Ninja.

Approach this challenge carefully and design a beautiful solution. Then post your solution in the comments on this post. Note it's ideal if you post your solution as a [gist](https://gist.github.com/) so it has nice syntax highlighting.

I will select one solution as the winner. The winner will be immortalized in this post as the correct solution for this challenge! Remember to leave your name along the code, so you can live in infamy, forever known as a true Swift Ninja :]

In addition, the winner will will receive a a free copy of our upcoming [Swift by Tutorials Bundle](http://www.raywenderlich.com/?page_id=74805), which includes three books about programming in Swift!

In choosing a winner, I will consider correctness, brevity and use of Swift's language features. Embrace all the techniques you've explored in this post. Should you and another developer post the same winning solution, I'll choose the one that was posted first.

You have 2 weeks from the time this post goes live. Better get to it!

Let's get to coding! Here's the enumerations and a struct to get started:
    
    
    enum Suit {
        case Clubs, Diamonds, Hearts, Spades
    }
     
    enum Rank {
        case Jack, Queen, King, Ace
        case Num(Int)
    }
     
    struct Card {
        let suit: Suit
        let rank: Rank
    }

Write a function called `countHand` that takes in an array of `Card` instances and counts the total value of the cards given.

The requirements for your solution are as follows:

  * The function returns the value of the cards in the hand as an Int.
  * Does not use loops or nested functions.
  * The card values are as follows: 
    1. Any Ace preceded by 5 of Diamonds is worth 100 points.
    2. Any odd numeric card (3, 5, 7, 9) of any suit's worth the double of its rank value in points when immediately preceded in the hand by any card of the Hearts. Examples: 
      1. The hand 3♥, 7♣ has total value of 14.
      2. The hand 3♣, 7♥ has total value of 0.
  * Since brevity is one of the points on which your code will be assessed, consider using one statement functions, closures and case statements.

Here's an example of usage and its result. Use this to check your solution:
    
    
    countHand([
      Card(suit:Suit.Hearts, rank:Rank.Num(10)),
      Card(suit:Suit.Hearts, rank:Rank.Num(6)),
      Card(suit:Suit.Diamonds, rank:Rank.Num(5)),
      Card(suit:Suit.Clubs, rank:Rank.Ace),
      Card(suit:Suit.Diamonds, rank:Rank.Jack)
    ]) //--> 110

## Where to Go From Here

First, check your challenge result!

Calculate how many shurikens you earned -- for the final challenge, give yourself 3 shurikens if you solved the problem and none if you didn't.  
How ninja are you?

  * _23 or more shurikens_: Congratulations! You're a Swift ninja! Fantastic!
  * _16 to 22 shurikens_: You're doing well, but you'll benefit from delving into the nitty gritty details of Swift. Luckily, this website is a great resource to [learn more about Swift](http://www.raywenderlich.com/?page_id=2519).
  * _15 or less shurikens_: Though you may not have been able to beat the challenges without help, you certainly learned tons of new Swift techniques and are on your way to being a certifiable ninja. Props!

You can download the complete Playground solution to the first 8 challenges here: [NinjaChallenge-Completed-beta6.playground](http://cdn4.raywenderlich.com/wp-content/uploads/2014/07/NinjaChallenge-Completed-beta6.playground.zip)

Even if you mastered the challenges, you can always learn more! Check out some additional Swift resources:

  * The raywenderlich.com [Swift style guide](http://www.raywenderlich.com/?p=76190)
  * Check out our [three new Swift books](http://www.raywenderlich.com/?page_id=74805), covering Swift, iOS 8, and more
  * Last but not least, [Apple's own page](https://developer.apple.com/swift/) is always a great source of Swift knowledge.

Remember to post your solution to the final challenge and your name, and good luck. Thanks for reading this tutorial, and if you have comments or questions, please join in the forum discussion below!

_Credit: All images in this post are from the public domain, and are available at: [www.openclipart.org](http://openclipart.org/search/?query=ninja)_
