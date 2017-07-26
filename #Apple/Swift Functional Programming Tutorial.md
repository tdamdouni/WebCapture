# Swift Functional Programming Tutorial

_Captured: 2015-11-25 at 20:49 from [www.raywenderlich.com](http://www.raywenderlich.com/82599/swift-functional-programming-tutorial)_

![Learn how to use functional programming in Swift!](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/iOS-8-Feast-Swift-250x250.png)

> _Learn how to use functional programming in Swift!_

_Note from Ray_: This is an abbreviated version of a chapter from [Swift by Tutorials](http://www.raywenderlich.com/?page_id=74805) released as part of the [iOS 8 Feast](http://www.raywenderlich.com/?p=82230) to give you a sneak peek of what's inside the book. We hope you enjoy!

When making the transition from Objective-C to Swift, it's logical to map concepts you know in Objective-C onto Swift. You know how to create classes with Objective-C, and now you know the equivalent in Swift. There are, of course, some completely new features, such as generics and range operators, but these are still little more than refinements of what you already know. (OK, perhaps not so little!)

However, Swift does more than provide a better syntax for your applications. With this new language, you have the opportunity to change the way in which you tackle problems and write code. With Swift, _functional programming_ techniques become a viable and important part of your programming toolkit.

Functional programming can be a theory-heavy topic, so this tutorial will introduce the topic by example. You'll work through a number of programming examples using what will likely be the more familiar, imperative style, and then try your hand at solving the same problems using functional techniques.

_Note:_ This Swift functional programming tutorial assumes you already know the basics of Swift development. If you are new to Swift, we recommend you check out some of our [other Swift tutorials](http://www.raywenderlich.com/?page_id=2519) first.

## What is Functional Programming?

Briefly put, functional programming is a programming paradigm that emphasizes calculations via mathematical-style functions, immutability and expressiveness, and minimizes the use of variables and state.

Since there's minimal shared state and each function is like an island in the ocean of your app, it makes things easier to test. Functional programming has also come into popularity because it can make concurrency and parallel processing easier to work with. That's one more thing in your toolbox to improve performance in these days of multi-core devices.

Its time to put the fun- into functional programming!

## Simple Array Filtering

You'll start with something quite easy: a simple bit of math. Your first task is to create a simple Swift script that finds all the even numbers between 1 and 10 (inclusive). A pretty trivial task, but a great introduction to functional programming!

### Filtering the Old Way

Create a new Swift playground file and save it wherever you like. Replace the contents of the newly created file with the following code:
    
    
    var evens = [Int]()
    for i in 1...10 {
      if i % 2 == 0 {
        evens.append(i)
      }
    }
    println(evens)

This produces the desired result:
    
    
    [2, 4, 6, 8, 10]
    

(If you can't see the console output, remember that you need to show the Assistant Editor via the _View/Assistant Editor/Show Assistant Editor_ menu option.)

This little script is very simple; the key points of the algorithm are as follows:

  1. You create an empty (and mutable) array.
  2. The for loop iterates over the numbers from 1 to 10 (remember "…" is inclusive!).
  3. If the condition (that the number must be even) is met, you add it to the array.

The above code is imperative in nature. The instructions tell the computer how to locate the even numbers by giving it explicit instructions that use basic control structures, in this case `if` and `for-in`.

The code works just fine but the important bit--testing whether the number is even--is buried inside the for loop. There's also some tight coupling, where the desired action of adding the number to the array is inside the condition. If you wanted to print each even number somewhere else in your app, there's no good way to reuse code without resorting to copy-and-paste.

It's _fun_-ctional time. (Sorry, I'll stop it with the "fun" puns now!)

### Functional Filtering

Add the following to the end of your playground:
    
    
    func isEven(number: Int) -> Bool {
      return number % 2 == 0
    }
    evens = Array(1...10).filter(isEven)
    println(evens)

You'll see that the above, functional code creates exactly the same result as the imperative version:
    
    
    [2, 4, 6, 8, 10]
    

Let's look more closely at the functional version. It's comprised of two parts:

  1. The `Array(1...10)` section is a simple and convenient way to create an array containing the numbers 1 through 10. The range operator `1...10` creates a `Range` you pass to the array's initializer.
  2. The `filter` statement is where the functional programming magic takes place. This method, exposed by `Array`, creates and returns a new array that contains only the items for which the given function returns true. In this example, `isEven` is supplied to `filter`.

You're passing in the function `isEven` as a parameter to filter, but remember functions are just named closures. Try adding the following, more concise version of the code to your playground:

Again, verify that the results from all three approaches are identical. The above example demonstrates that the compiler infers the type of the parameter number and return types of the closure from its usage context.

If you like your code to be as concise as possible, take it one step further and try the following:

The above uses argument shorthand notation, implicit returns, type inference… the works!

The functional version of this code is certainly more concise than the imperative equivalent. This simple example exhibits a few interesting features that are common to all functional languages:

  1. _Higher-order functions_: These are functions that you pass as arguments to other functions. In this simple example, filter requires that you pass a higher-order function.
  2. _First-class functions_: You can treat functions just like any other variable; you can assign them to variables and pass them as arguments to other functions.
  3. _Closures_: These are effectively anonymous functions you create in-place.

You may have noticed that Objective-C also exhibits some of these features through the use of blocks. Swift, however, goes further than Objective-C in promoting functional programming with a mix of more concise syntax and built-in functional abilities such as `filter`.

### The Magic Behind Filter

Swift arrays have a number of functional methods, such as `map`, `join` and `reduce`. What, exactly, goes on behind the scenes in these methods?

It's time to look behind the magic of filter and add your own implementation.

Within the same playground, add the following function:
    
    
    func myFilter<T>(source: [T], predicate:(T) -> Bool) -> [T] {
      var result = [T]()
      for i in source {
        if predicate(i) {
          result.append(i)
        }
      }
      return result
    }

The above is a generic function that takes as its inputs a source, which is an array of type `T`, and `predicate`, a function that takes an instance of `T` and returns a `Bool`.

The implementation of `myFilter` looks a lot like the imperative version you added at the start. The main difference is that you supply the condition being checked as a function rather than hard-code it.

Try out your newly added filter implementation by adding the following code:

Once again, the output is the same!

_Challenge_: The above filter function is global; why not see if you can make it a method on Array?

## Reducing

The previous example was a simple one, making use of a single functional method. In this section, you'll build upon the last, showing how you can implement more complex logic using functional techniques.

Create a new Swift playground and get ready for your next assignment!

### Manual reduction

Your task in this section is just a little more complicated: Take the even numbers between 1 and 10 and compute their sum. This calls for what is known as a _reduce_ function, which takes a set of inputs and generates a single output.

I'm sure you are more than capable of working this one out yourself, but here it is anyway! Add the following to your playground:
    
    
    var evens = [Int]()
    for i in 1...10 {
      if i % 2 == 0 {
        evens.append(i)
      }
    }
     
    var evenSum = 0
    for i in evens {
      evenSum += i
    }
     
    println(evenSum)

The Assistant Editor will display the following result:

The imperative code above continues in the same vein as the previous example, adding an additional `for-in` loop.

Let's see what a functional equivalent looks like!

### Functional Reduce

Add the following to your playground:

You'll see exactly the same result:

The previous section covered the array construction and use of `filter`. The net result of these two operations is an array with five numbers, `[2, 4, 6, 8, 10]`. The new step in the above code uses `reduce`.

`reduce` is a tremendously versatile `Array` method that executes a function once for each element, accumulating the results.

To understand how `reduce` works, it helps to look at its signature:

The first parameter is the initial value, which is of type `U`. In your current code, the initial value is `0` and is of type `Int` (hence `U` is `Int` in this case). The second argument is the `combine` function that is executed once for each element of the array.

`combine` takes two arguments: the first, of type `U`, is the result of the previous invocation of `combine`; the second is the value of the array element that is being combined. The result returned by `reduce` is the value returned by the last `combine` invocation.

There's a lot going on here, so let's break it down step by step.

In your code, the first reduce iteration results in the following:

![Iteration1](http://cdn2.raywenderlich.com/wp-content/uploads/2014/09/Iteration1.png)

The inputs to combine are the initial value, 0, and the first item in the input array, which is 2. combine sums these values, returning 2.  
The second iteration is illustrated below:

![Iteration2](http://cdn1.raywenderlich.com/wp-content/uploads/2014/09/Iteration2.png)

On the second iteration, the inputs to combine are the result from the previous iteration and the next item from the input array. Combining them results in 2 + 4 = 6.

Continuing this process for all the items in the array gives the following inputs and outputs:

![Iteration3](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/Iteration3.png)

The number highlighted in the bottom-right corner is the overall result.

This is quite a simple example; in practice, you can perform all kinds of interesting and powerful transformations with reduce. Below are a few quick examples.

Add the following to your playground:

This code uses reduce to find the maximum number in an array of integers. In this case, the result is rather obvious! Remember that here, `total` is really just the result of `max` of the last iteration of `reduce`.

If you're struggling to see how this works, why not create a table like the one above where you compute the inputs and output of `combine` (i.e., the closure) for each iteration?

The examples you've seen so far all reduce arrays of integers into single integer values. Of course, `reduce` has two type parameters, `U` and `T`, which can be different and certainly don't have to be integers. This means you can reduce an array of one type into a completely different type.

Add the following to your playground:

This produces the following output:
    
    
    numbers: 1 2 3 4 5 6 7 8 9 10
    

This example reduces an array of integers into the string shown above.

With a bit of practice, you'll find yourself using reduce in all kinds of interesting and creative ways!

_Challenge_: See if you can use reduce to take an array of digits and convert them into an integer. Given the input array:

Your reduce method should return an Int with the value 3141.

### The Magic Behind Reduce

In the previous section, you developed your own implementation of `filter`, which was surprisingly simple. You'll now see that the same is true for `reduce`.

Add the following to your playground:
    
    
    extension Array {
      func myReduce<T, U>(seed:U, combiner:(U, T) -> U) -> U {
        var current = seed
        for item in self {
          current = combiner(current, item as T)
        }
        return current
      }
    }

The above adds a `myReduce` method to `Array` that mimics the built-in `reduce` function. This method simply iterates over each item in the array, invoking `combiner` at each step.

To test out the above, replace one of the `reduce` methods in your current playground with `myReduce`.

At this point, you might be thinking, "Why would I want to implement `filter` or `reduce` myself?" The answer is, "You probably wouldn't!"

However, you might want to expand your use of the functional paradigm in Swift and implement your own functional methods. It's encouraging (and important!) to see and understand just how easy it is to implement powerful methods like `reduce`.

## Building an Index

It's time to tackle a more difficult problem, and that means it's time to open a new playground. You know you want to!

In this section, you're going to use functional programming techniques to group a list of words into an index based on the first letter of each word.

Within your newly created playground, add the following:

To accomplish this section's task, you're going to group these words by their first letters (case insensitive!).

In preparation, add the following to the playground:
    
    
    typealias Entry = (Character, [String])
     
    func buildIndex(words: [String]) -> [Entry] {
      return [Entry]()
    }
    println(buildIndex(words))

The `Entry` typealias defines the tuple type for each index entry. Using a typealias in this example makes the code more readable, removing the need to repeatedly specify the tuple type in full. You're going to add your index-building code in `buildIndex`.

### Building an Index Imperatively

Starting with an imperative approach, update `buildIndex` as follows:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      var result = [Entry]()
     
      var letters = [Character]()
      for word in words {
        let firstLetter = Character(word.substringToIndex(
          advance(word.startIndex, 1)).uppercaseString)
     
        if !contains(letters, firstLetter) {
          letters.append(firstLetter)
        }
      }
     
      for letter in letters {
        var wordsForLetter = [String]()
        for word in words {
          let firstLetter = Character(word.substringToIndex(
            advance(word.startIndex, 1)).uppercaseString)
     
          if firstLetter == letter {
            wordsForLetter.append(word)
          }
        }
        result.append((letter, wordsForLetter))
      }
      return result
    }

This function has two halves, each with its own `for` loop. The first half iterates over each of the words to build an array of letters; the second iterates over these letters, finding the words that start with the given letter, to build the return array.

With this implementation in place, you'll see the desired output:
    
    
    [(C, [Cat, Chicken]),
     (F, [fish]),
     (D, [Dog]),
     (M, [Mouse, monkey]),
     (G, [Guinea Pig])]
    

(The above is formatted a little for clarity.)

This imperative implementation has quite a few steps and nested loops that can make it difficult to understand. Let's see what a functional equivalent looks like.

### Building an Index the Functional Way

Create a new playground file and add the same initial structure:
    
    
    import Foundation
     
    let words = ["Cat", "Chicken", "fish", "Dog",
                          "Mouse", "Guinea Pig", "monkey"]
     
    typealias Entry = (Character, [String])
     
    func buildIndex(words: [String]) -> [Entry] {
      return [Entry]();
    }
     
    println(buildIndex(words))

At this point, the `println` statement will output an empty array:
    
    
    []
    

The first step toward building an index is to transform the words into an array that contains only their first letters. Update buildIndex as follows:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      let letters = words.map {
        (word) -> Character in
        Character(word.substringToIndex(advance(word.startIndex, 1)
          ).uppercaseString)
      }
      println(letters)
     
      return [Entry]()
    }

The playground now outputs an array of uppercase letters, each one corresponding to a word in the input array.
    
    
    [C, C, F, D, M, G, M]
    

In the previous sections, you encountered `filter` and `reduce`. The above code introduces map, another functional method that's part of the array API.

`map` creates a new array with the results of calls to the supplied closure for each element in the supplied array. You use map to perform transformations; in this case, map transforms an array of type `[String]` into an array of type `[Character]`.

The array of letters currently contains duplicates, whereas your desired index has only a single occurrence of each letter. Unfortunately, Swift's array type doesn't have a method that performs de-duplication. It's something you're going to have to write yourself!

In the previous sections, you saw how easy it is to re-implement `reduce` and `filter`. It will come as no surprise that adding a de-duplication method of your own isn't tricky, either.

Add the following function to your playground before `buildIndex`:
    
    
    func distinct<T: Equatable>(source: [T]) -> [T] {
      var unique = [T]()
      for item in source {
        if !contains(unique, item) {
          unique.append(item)
        }
      }
      return unique
    }

`distinct` iterates over all the items in an array, building a new array that contains only the unique items.

Update `buildIndex` to put `distinct` to use:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      let letters = words.map {
        (word) -> Character in
        Character(word.substringToIndex(advance(word.startIndex, 1)
          ).uppercaseString)
      }
      let distinctLetters = distinct(letters)
      println(distinctLetters)
     
      return [Entry]()
    }

Your playground will now output the unique letters:

Now that you have an array of distinct letters, the next task in building your index is to convert each letter into an `Entry` instance. Does that sound like a transformation? That'll be another job for map!

Update `buildIndex` as follows:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      let letters = words.map {
        (word) -> Character in
        Character(word.substringToIndex(advance(word.startIndex, 1)
          ).uppercaseString)
      }
      let distinctLetters = distinct(letters)
     
      return distinctLetters.map {
        (letter) -> Entry in
        return (letter, [])
      }
    }

The second call to map takes the array of characters and outputs an array of `Entry` instances:
    
    
    [(C, []), 
     (F, []), 
     (D, []), 
     (M, []), 
     (G, [])]
    

(Again, the above is formatted for clarity.)

You're almost done. The final task is to populate each `Entry` instance with the words that begin with the given letter. Update the function to add a nested `filter`, as follows:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      let letters = words.map {
        (word) -> Character in
        Character(word.substringToIndex(advance(word.startIndex, 1)
          ).uppercaseString)
      }
      let distinctLetters = distinct(letters)
     
      return distinctLetters.map {
        (letter) -> Entry in
        return (letter, words.filter {
          (word) -> Bool in
         Character(word.substringToIndex(advance(word.startIndex, 1)
           ).uppercaseString) == letter
        })
      }
    }

This provides the desired output:
    
    
    [(C, [Cat, Chicken]),
     (F, [fish]),
     (D, [Dog]),
     (M, [Mouse, monkey]),
     (G, [Guinea Pig])]
    

In the second half of the function, there's now a nested call to `filter` inside map. That will filter the list of words for each distinct letter, and thus identifies the words starting with the given letter.

The above implementation is already more concise and clear than its imperative equivalent, but there's still room for improvement: this code extracts and capitalizes a word's first letter multiple times. It would be good to remove this duplication.

If this were Objective-C code, you would have a few different options at your disposal: You could create a utility method that performs this functionality, or perhaps you could add this method directly to `NSString` via a class category. However, if you only ever need to perform this task within `buildIndex`, a utility method lacks semantic clarity and using a class category is overkill.

Fortunately, with Swift, there's a better way!

Update `buildIndex` with the following:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      func firstLetter(str: String) -> Character {
        return Character(str.substringToIndex(
                advance(str.startIndex, 1)).uppercaseString)
      }
     
      let letters = words.map {
        (word) -> Character in
        firstLetter(word)
      }
      let distinctLetters = distinct(letters)
     
      return distinctLetters.map {
        (letter) -> Entry in
        return (letter, words.filter {
          (word) -> Bool in
          firstLetter(word) == letter
        })
      }
    }

You'll see exactly the same output as before.

The above code adds a `firstLetter` function that is nested within `buildIndex` and as a result, is entirely local to the outer function. This takes advantage of Swift's first-class functions that you can treat much like variables, allowing for assignment and scoping.

The new code removes the duplicate logic, but there's even more you can do to clean up `buildIndex`.

The first map step that constructs the array of letters takes a closure whose signature is `(String) -> Character`. You may notice this is exactly the same signature as the `firstLetter` function you just added, which means you can pass it directly to map.

Making use of this knowledge, you can rewrite the function as follows:
    
    
    func buildIndex(words: [String]) -> [Entry] {
      func firstLetter(str: String) -> Character {
        return Character(str.substringToIndex(
                advance(str.startIndex, 1)).uppercaseString)
      }
     
      return distinct(words.map(firstLetter))
        .map {
          (letter) -> Entry in
          return (letter, words.filter {
            (word) -> Bool in
            firstLetter(word) == letter
          })
        }
    }

The end result is concise, yet highly expressive.  
Perhaps you've noticed an interesting side effect of the functional techniques you have employed so far. While your imperative solutions have relied on variables (as defined using the `var` keyword), you've defined everything in the functional equivalents as constants (via `let`).

You should strive for immutability; immutable types are easier to test and aid concurrency. Functional programming and immutable types tend to go hand in hand. As a result, your code will be more concise as well as less error-prone. And it will look cool and impress your friends!

_Challenge:_ Currently, `buildIndex` returns an unsorted index; the order of the `Entry` instances depends on the order of the words in the input array. Your challenge is to sort the index into alphabetic order. For the example array of strings, this would give the following output:
    
    
    [(C, [Cat, Chicken]),
     (D, [Dog]),
     (F, [fish]),
     (G, [Guinea Pig]),
     (M, [Mouse, monkey])]
    

## Where To Go From Here?

Here are the [finished playgrounds](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/Functional.zip) you developed in this Swift functional programming tutorial.

Congratulations, you now have hands-on experience with functional programming in Swift! Not only did you learn how to use functional methods like `map` and `reduce`, but you learned how to implement them yourself, and how to think in a functional way.

If you want to learn more about functional programming, check out the full chapter in [Swift by Tutorials](http://www.raywenderlich.com/?page_id=74805), where I go a bit further and cover partial application of functions and currying.

I hope to see you experiment with functional programming techniques in your own apps. If you have any questions or comments along the way, please join the forum discussion below!
