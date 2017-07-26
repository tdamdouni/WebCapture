# Collection Data Structures In Swift

_Captured: 2015-11-25 at 20:42 from [www.raywenderlich.com](http://www.raywenderlich.com/79850/collection-data-structures-swift)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

_Update 04/21/2015_: Updated for Xcode 6.3 and Swift 1.2.

![What kind of performance do you want from your data structure?](http://cdn1.raywenderlich.com/wp-content/uploads/2014/10/data-structures-square-250x250.png)

> _What kind of performance do you want from your data structure?_

Imagine you have an application that needs to work with a lot of data. Where do you put that data? How do you keep it organized and handle it efficiently?

If your program only manages one number, you store it in one variable. If it has two numbers then you'd use two variables.

What if it has 1000 numbers, 10,000 strings or the ultimate library of memes? (Wouldn't it be nice to be able to find a perfect meme in an instant?) In that case, you'll need one of the fundamental _collection data structures_. Fortunately for you, that's the topic of this tutorial.

Here's how the tutorial will flow:

  * You'll review what a data structure is and then you'll learn about Big-O notation. It's the standard tool for describing the performance of different data structures.
  * Next up: practicing by measuring the performance of arrays, dictionaries and sets -- the most basic data structures available in Cocoa development. This will also double as a rudimentary introduction to performance testing.
  * As you proceed, you'll compare the performance of mature Cocoa structures with newer, Swift-only counterparts.
  * Finally, you'll briefly review some related types offered by Cocoa. These are data structures that you might be surprised to learn are already at your fingertips. 

## Getting Started

Before you dive in and explore the data structures used in iOS, you should review a couple of basic concepts about what they are and how to measure their performance.

There are many types of collection data structures, and each represents a specific way to organize and access a collection of items. One collection type might make some activities especially efficient, such as adding a new item, finding the smallest item or ensuring you're not adding duplicates.

Without collection data structures, you'd be stuck trying to manage items one by one. A collection allows you to:

  1. Handle all those items as one entity
  2. Imposes some structure on them
  3. Efficiently insert, remove and retrieve items

### What is "Big-O" Notation?

Big-O -- that's the letter O, not the number zero -- notation is a way of describing the efficiency of an operation on a data structure. There are various kinds of efficiency: you could measure how much memory the data structure consumes, how much time it takes under the worst case scenario, how much time it takes on average and so on and so forth.

In this tutorial, you'll measure how much time an operation takes, on average.

In general, larger quantities of data don't make an operation faster. Usually it's the opposite, but sometimes there is little or no slowdown. Big-O notation is a precise way of describing this. You write an exact functional form that roughly describes how the running time changes based on the number of elements in the structure.

When you see Big-O notation written as `O(something-with-n)`, the `n` is the number of items in the data structure, and the `something-with-n` is roughly how long the operation will take.

"Roughly", ironically enough, has a specific meaning: the behavior of the function at the asymptotic limit of very large `n`. Imagine n is a really really large number - you're thinking about how the performance of some operation will change as you go from n to n+1.

_Note:_ This is all a part of _algorithmic complexity analysis_, and if you wish to explore it deeper then whip out any computer science textbook. There you'll find mathematical methods for analyzing complexity from scratch, finer distinctions between different kinds of efficiency, more explicit formulations of assumptions about the underlying machine model, and other fun stuff that you may or may not wish you knew.

The most commonly seen Big-O performance measures are as follows, in order from best to worst performance:

  * _O(1)_ (constant time): No matter how many items are in a data structure, this function calls the same number of operations. This is considered _ideal performance_.
  * _O(log n)_ (logarithmic): The number of operations this function calls grows at the rate of the logarithm of the number of items in the data structure. This is _good performance_, since it grows considerably slower than the number of items in the data structure.
  * _O(n)_ (linear): The number of operations this function calls will grow linearly with the size of the structure. This is considered _decent performance_, but it can grind along with larger data collections.
  * _O(n (log n))_ ("linearithmic"): The number of operations called by this function grow by the logarithm of the number of items in the structure multiplied by the number of items in the structure. Predictably, this is about the _lowest level_ of real-world tolerance for performance. While larger data structures perform more operations, the increase is somewhat reasonable for data structures with small numbers of items.
  * _O(n²)_ (quadratic): The number of operations called by this function grow at a rate that equals the size of the data structure, squared -- _poor performance_ at best. It grows quickly enough to become unusably slow even if you're working with small data structures.
  * _O(2^n)_ (exponential): The number of operations called by this function grow by two to the power of the size of the data structure. This gives _very poor performance_ and becomes intolerably slow almost immediately.
  * _O(n!)_ (factorial): The number of operations called by this function grow by the [factorial](http://en.wikipedia.org/wiki/Factorial) of the size of the data structure. Essentially, you have the _worst case scenario_ for performance. For example, in a structure with just 100 items, the multiplier of the number of operations is [158 digits long](http://www.wolframalpha.com/input/?i=100%21).

Here's a more visual representation of performance and how it degrades when there are more items in a collection, going from one to 25 items:

![Big-O Notation](http://cdn2.raywenderlich.com/wp-content/uploads/2014/09/Screen-Shot-2014-09-14-at-11.54.21-AM-700x460.png)

> _[Big-O Notation](http://cdn2.raywenderlich.com/wp-content/uploads/2014/09/Screen-Shot-2014-09-14-at-11.54.21-AM.png)_

Did you notice that you can't even see the green `O(log n)` line because it is so close to the ideal `O(1)` at this scale? That's pretty good! On the other hand, operations that have Big-O notations of `O(n!)` and `O(2^n)` degrade so quickly that by the time you have more than 10 items in a collection, the number of operations spikes completely off the chart.

Yikes! As the chart clearly demonstrates, the more data you handle, the more important it is to choose the right data structure for the job.

Now that you've seen how to compare the performance of operations on data structures, it's time to review the three most common types used in iOS and explore how they perform in theory and in practice.

## Common iOS Data Structures

The three most common data structures in iOS are _arrays, dictionaries and sets_. First you'll consider how they differ in ideal terms as fundamental abstractions, and then you'll examine the performance of the actual concrete classes which iOS offers for representing those abstractions.

For all three major structure types, iOS offers multiple concrete classes that work for the same abstraction. In addition to the old _Foundation_ data structures available in Swift and Objective-C, there are new _Swift-only_ versions of data structures that integrate tightly with the language.

Foundation data structures have been around longer and are currently faster to create, even when you're working with vast quantities of data. Swift data structures, however, can be faster when you need to search through data. Which one to choose depends on the operation you want to perform.

### Arrays

An _array_ is a group of items placed in a specific order, and you can access each item via an _index_ -- a number that indicates its position in the order. When you write the index in brackets after the name of the array variable, this is _subscripting_.

Swift arrays are _immutable_ if you define them as constants with `let`, and _mutable_ if you define them as variables with `var`.

In contrast, a Foundation `NSArray` is immutable by default. If you want to add, remove or modify items after creating the array, you must use the mutable variant class `NSMutableArray`.

An `NSArray` is heterogeneous, meaning that it can contain Cocoa objects of different types. Swift arrays are homogeneous, meaning that each Swift `Array` is guaranteed to contain only one type of object.

However, you can still define a single Swift `Array` so it stores various types of Cocoa objects by specifying that the one type is `AnyObject`, since every Cocoa type is also a subtype of this.

### Expected Performance and When to Use Arrays

The primary reason to use an array to store variables is when order matters. Think about those times when you sort contacts by First or Last name, a To-Do list by date, or any other situation when it's critical to find or display data in a specific order.

Apple's documentation includes three key expectations for Array performance in the [CFArray header](http://www.opensource.apple.com/source/CF/CF-550.13/CFArray.h):

  1. Accessing any value at a particular index in an array is at worst `O(log n)`, but should usually be `O(1)`.
  2. Searching for an object at an unknown index is at worst `O(n (log n))`, but will generally be `O(n)`.
  3. Inserting or deleting an object is at worst `O(n (log n))` but will often be `O(1)`.

These guarantees subtly deviate from the simple "ideal" array that you might expect from a computer science textbook or the C language, where an array is always a sequence of items laid out contiguously in memory.

Consider it a useful reminder to check the documentation!

In practice, these expectations make sense when you think about them:

  1. If you already know where an item is and need to look it up, then it should be very fast.
  2. If you don't know where a particular item is, you'll need to look through the array from beginning to end to find it, and your search will be slower.
  3. If you know where you're adding or removing an object, it's not too difficult, although you may need to adjust the rest of the array afterwards, and that is more time-consuming.

How well do these expectations align with reality? Keep reading to find out!

### Sample App Testing Results

Download [the sample project](http://cdn1.raywenderlich.com/wp-content/uploads/2014/11/DataStructures_Swift_1_22.zip) for this tutorial and open it in Xcode. There are some testing methods that will create and/or test an array, and then show you the how long it took to perform each task.

_One thing to note_: In the app, the Debug configuration automatically sets optimization to a level equal to the release configuration -- this is so when you test the application you get the same level of optimization you'd see in the real world.

You need a minimum of 1000 items to run tests with the sample app. When you build and run, the slider will be set to 1000. Press the _Create Array and Test_ button, and you'll be testing in no time:

![Swift 1.2 Create 1000 items](http://cdn5.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-19.50.12-281x500.png)

> _[Swift 1.2 Create 1000 items](http://cdn3.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-19.50.12.png)_

Drag the slider over to the right side until it hits 10,000,000, and press _Create Array and Test_ again to see the difference in creation time with a significantly larger array:

![Swift 1.2 Create 10,000,000](http://cdn1.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-19.51.44-281x500.png)

> _[Swift 1.2 Create 10,000,000](http://cdn2.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-19.51.44.png)_

These tests were run against an iPhone 6 running iOS 8.3 from Xcode 6.3 (which includes Swift 1.2). With 10,000 times as many items, creating the array only takes about 714 times as much time.

`O(n)` time in this case would mean that adding 10,000x as many items would take 10,000x as much time, and `O(log n)` time would mean adding 10,000x as many items would only take 4x as much time. Performance in this case is somewhere between `O(log n)` and `O(n)`, which is pretty solid.

This used to take…quite a bit longer. From the original version of this tutorial, written a long time ago, in a galaxy far, far away, on an iPhone 5 which was running the iOS 8 Gold Master with the Swift 1.0/Xcode 6.0 Gold Master, the tests took a rather long time:

![Swift 1000 Items](http://cdn5.raywenderlich.com/wp-content/uploads/2014/09/IMG_5140-281x500.png)

> _[Swift 1000 Items](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/IMG_5140.png)_

![Swift Array 100,000](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/IMG_5139-281x500.png)

> _[Swift Array 100,000](http://cdn2.raywenderlich.com/wp-content/uploads/2014/09/IMG_5139.png)_

That was a sad time. However, you've seen that with the updates to Swift 1.2, you can easily make huge arrays with no problem!

What about `NSMutableArray`? You can still call Foundation classes from Swift without having to drop back down to Objective-C, and you'll notice there is also a Swift class called `NSArrayManipulator` that conforms to the same protocol, `ArrayManipulator`.

Because of this, you can easily swap in `NSMutableArray` for a Swift Array. The project code is simple enough that you can try `NSMutableArray` with a single line change to compare the performance.

Open _ArrayViewController.swift_ file and change line 27 from:

To:

Build and run again, and press _Create Array and Test_ to test the creation of an `NSMutableArray` with 1000 items:

![NSArray Create 1000 items Xcode 6.3](http://cdn1.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-20.20.34-281x500.png)

> _[NSArray Create 1000 items Xcode 6.3](http://cdn3.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-20.20.34.png)_

…and then again with 10,000,000 items:

![NSArray Create 10,000,000 items Xcode 6.3](http://cdn5.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-20.20.45-281x500.png)

> _[NSArray Create 10,000,000 items Xcode 6.3](http://cdn3.raywenderlich.com/wp-content/uploads/2014/11/2015-04-21-20.20.45.png)_

Raw performance for creation is not as good as Swift in 1.2 - though some of that may come from needing to go back and forth between objects that can be stored in an `NSArray` and their Swift counterparts.

However, you only create an array once - you perform other operations on it far more often, like finding, adding, or removing objects.

In more exhaustive testing, like when you're using some of Xcode 6's performance testing methods to call each of these methods 50 times, patterns begin to emerge:

  * Creating a Swift `Array` and an `NSArray` degrade at roughly the same rate - between `O(log n)` and `O(n)`. In terms of raw time at both 5,000 and 25,000 items, Swift takes around 3x as long as Foundation - but both are under 2 hundredths of a second.
  * Adding items to the beginning or middle of an array structure is considerably slower in Swift than in Foundation (which is around `O(1)`). Adding items to the end of a Swift `Array` (less than `O(1)`) is actually faster than adding items to the end of an NSArray (just over `O(1)`)
  * Removing objects is very similar in performance degradation across Foundation and Swift array structures: From the beginning, the middle, or the end, removing an object degrades between `O(log n)` `O(n)`. Raw time is a bit worse in Swift for removing from the beginning of an `Array`, but the distinction is a matter of milliseconds.
  * Looking up items within an array is where Swift justifies its name. Lookups up by index and object grow at very close rates for both Swift arrays and `NSArray`. When you're looking up by index, large Swift arrays perform nearly 10 times faster in raw time than using comparable `NSMutableArray` objects.

### Dictionaries

![Dictionaries](http://cdn1.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-08-12-at-7.48.28-PM-414x320.png)

Dictionaries are a way of storing values that don't need to be in any particular order and are uniquely associated with keys. You use the key to store or look up a value.

Dictionaries also use subscripting syntax, so when you write `dictionary["hello"]`, you'll get the value associated with the key `hello`.

Like arrays, Swift dictionaries are constant if you declare them with `let` and mutable if you declare them with `var`. Similarly on the Foundation side, there are both `NSDictionary` and `NSMutableDictionary` classes for you to use.

Another characteristic that is similar to Swift arrays is that dictionaries are strongly typed, and you must have known key and value types. `NSDictionary` objects are able to take any `NSObject` as a key and store any object as a value.

You'll see this in action when you call a Cocoa API that takes or returns an `NSDictionary`. From Swift, this type appears as `[NSObject: AnyObject]`. This indicates that the key must be an `NSObject` subclass, and the value can be any Swift-compatible object.

### When to use Dictionaries

![Chaplin](http://cdn2.raywenderlich.com/wp-content/uploads/2014/09/jpeg-250x250.jpg)

> _My cat knows when you use dictionaries. Do you?_

Dictionaries are best used when there isn't a particular order to what you need to store, but there is a meaningful association to what you need to store.

To help you examine how dictionaries and other data structures in the rest of this tutorial work, create a Playground by going to _File…\New\Playground_, and name it _DataStructures_.

For example, pretend you need to store a data structure of all your friends and the names of their cats, so you can look up the cat's name using your friend's name. This way, you don't have to remember the cat's name to stay in that friend's good graces.

First, you'd want to store the dictionary of people and cats:

Thanks to Swift type inference, this will be defined as `[String: String]` - a dictionary with string keys and string values.

Now try to access items within it:

Note that subscripting syntax on dictionaries returns an optional. If the dictionary doesn't contain a value for a particular key, the optional is nil; if it does contain a value for that key you could get the wrapped value.

Because of that, it's a good idea to use the `if let` optional-unwrapping syntax to access values in a dictionary:

Since there is a value for the key "Ellen", this will print out "Ellen's cat is named Chaplin" in your Playground.

### Expected Performance

Once again, Apple outlines the expected performance of dictionaries in Cocoa in the [CFDictionary.h](http://opensource.apple.com/source/headerdoc/headerdoc-8.5.10/ExampleHeaders/CFDictionary.h) header file:

  1. The performance degradation of getting a single value is guaranteed to be at worst `O(n)`, but will often be `O(1)`.
  2. Insertion and deletion can be as bad as `O(n²)`, but will much more typically be closer to `O(1)` because of under-the-hood optimizations.

These aren't quite as obvious as the array degradations. Due to the more complex nature of storing keys and values versus an ordered list of stuff, the effects can be less predictable.

### Sample App Testing Results

`DictionaryManipulator` is a similar protocol to `ArrayManipulator`, and it tests dictionaries. With it, you can easily test the same operation using a Swift `Dictionary` or an `NSMutableDictionary`.

To compare the Swift and Cocoa dictionaries, you use a similar procedure as you used for the arrays. Build and run the app, and select the _Dictionary_ tab at the bottom.

Run a few tests - you'll notice that dictionaries take significantly longer to create than arrays. If you push the item slider up to 10,000,000 items, you might even be able to get a memory warning or even an out-of-memory crash!

Back in Xcode, open _DictionaryViewController.swift_ and find the `dictionaryManipulator` property:

Replace it with the following:

Now the app will use `NSDictionary` under the hood. Build and run the app again, and run a few more tests. If you're running Swift 1.2, your findings will probably match what was found in the more extensive tests:

  * In raw time, creating Swift dictionaries is significantly slower than creating `NSMutableDictionaries` - but both degrade at roughly the same `O(n)` rate.
  * Adding items to Swift dictionaries is roughly 3 times faster than adding them to `NSMutableDictionaries` in raw time, and both degrade close to the best-case-scenario `O(1)` rate promised by Apple's documentation.
  * Removing items from Swift dictionaries is 1-3x slower than removing items from `NSMutableDictionaries`, but the degradation of performance is again close to `O(1)` for both types.
  * Both Swift and Foundation dictionaries are able to lookup at roughly an `O(1)` rate. Unlike Swift arrays, dictionaries aren't faster in raw time than Foundation dictionaries, but the performance is very, very close.

And now, on to the final major data structure used in iOS: Sets!

### Sets

![Sets](http://cdn5.raywenderlich.com/wp-content/uploads/2014/08/Screen-Shot-2014-08-12-at-7.45.35-PM-368x320.png)

A Set is a data structure that stores unordered, unique values. When you try to add the same item to a set more than once, the item will not be added. "Sameness" here is determined by `isEqual()`.

Swift added support for a native `Set` structure in version 1.2 - for earlier versions of Swift, you could only access Foundation's `NSSet`. Again, Swift sets are type-specific - all the items in a Swift `Set` must be of the same type.

Note that like arrays and dictionaries, a native Swift `Set` is constant if you declare it with `let` and mutable if you declare it with `var`. Once again on the Foundation side, there are both `NSSet` and `NSMutableSet` classes for you to use.

### When to use Sets

Sets are most useful when uniqueness matters, but order doesn't. For example, what if you wanted to select four random names out of an array of eight names, with no duplicates?

Enter the following into your Playground:
    
    
    let names = ["John", "Paul", "George", "Ringo", "Mick", "Keith", "Charlie", "Ronnie"]
    var stringSet = Set<String>() // 1
    var loopsCount = 0
    while stringSet.count < 4 {
        let randomNumber = arc4random_uniform(UInt32(count(names))) //2
        let randomName = names[Int(randomNumber)] //3
        println(randomName) //4
        stringSet.insert(randomName) //5
        ++loopsCount //6
    }
     
    //7
    println("Loops: " + loopsCount.description + ", Set contents: " + stringSet.description)

In this little code snippet, you're doing the following:

  1. Initialize the set, so you can add objects to it.
  2. Pick a random number between 0 and the count of names.
  3. Grab the name at the selected index.
  4. Log the selected name to the console.
  5. Add the selected name to the mutable set. Remember, if the name is already in the set the set will stay unchanged since it doesn't store duplicates.
  6. Increment the loop counter so you can see how many times the loop ran.
  7. Once the loop finishes, print out the loop counter and the contents of the mutable set.

Since this example uses a random number generator, you'll get a different result every time. Here's an example of the log one of the times it ran while writing this tutorial:
    
    
    John
    Ringo
    John
    Ronnie
    Ronnie
    George
    Loops: 6, Set contents: ["Ronnie", "John", "Ringo", "George"]

Here, the loop ran six times in order to get four unique names. It selected Ronnie and John twice, but only wound up in the set once.

As you're writing the loop in the Playground, you'll notice that it runs over and over and over again, and you'll get a different number of loops each time. It'll always be at least four loops, since there must always be four items in the set to break out of the loop.

Now that you've seen `Set` at work on a small scale, it's time to examine performance with a larger batch.

### Sample App Testing Results

Apple didn't outline overall expectations for set performance as they did for dictionaries and arrays (the Swift `Set` documentation has expectations for a couple of methods, but `NSMutableSet` does not), so in this case you'll just look at real-world performance.

The Swift 1.2 version of the sample project has `NSSetManipulator` and `SwiftSetManipulator` objects in the `SetViewController` class similar to the setup in the Array and Dictionary view controllers, and can be swapped out the same way.

In both cases, if you're looking for pure speed, using a `Set` probably won't make you happy. Compare the numbers on `Set` and `NSMutableSet` to the numbers for `Array` and `NSMutableArray`, and you'll see set creation is considerably slower -- that's the price you pay for checking if every single item in a data structure is unique.

Detailed testing revealed that since Swift's `Set` spent a bit more time in the oven than its array and dictionary counterparts, its performance degradation and raw time for most operations is extremely similar to that of `NSSet`: Creation, removal, and lookup operations are all nearly identical between Foundation and Swift in raw time.

Creation degrades for both Swift and Foundation set types at a rate of around `O(n)` - this is expected since every single item in the set must be checked for equality before a new item can be added.

Removing and looking up are both around `O(1)` performance degradations across Swift and Foundation. This is largely because set structures use hashes to check for equality, and the hashes can be calculated and stored in sorted order. This makes set lookup considerably faster than array lookup.

The primary performance difference between `NSMutableSet` and Swift's native `Set` is that performance in adding an object wound up all over the place in limited testing.

Overall, it appears that adding an object to an `NSSet` stays near `O(1)`, whereas it can degrade at a rate higher than `O(n)` with Swift's `Set` structure.

Swift has seen very significant performance improvements in collection data structure performance in its short public life, and will hopefully continue to see them as Swift evolves.

## Lesser-known Foundation Data Structures

Arrays, dictionaries and sets are the workhorses of data-handling. However, Cocoa offers a number of lesser-known and perhaps under-appreciated collection types. If a dictionary, array or set won't do the job, it's worth checking if one of these will work before you create something from scratch.

### NSCache

Using `NSCache` is very similar to using `NSMutableDictionary` - you just add and retrieve objects by key. The difference is that `NSCache` is designed for temporary storage for things that you can always recalculate or regenerate. If available memory gets low, NSCache might remove some objects. They are thread-safe, but Apple's documentation warns:

Basically, this means that an `NSCache` is like an `NSMutableDictionary`, except that an object can be automatically removed from another thread at any time without your code doing anything. This is good for managing how much memory the cache uses, but can cause issues if you're trying to use an object that suddenly disappears.

NSCache also stores weak references to keys rather than strong references.

### NSCountedSet

`NSCountedSet` tracks how many times you've added an object to a mutable set. It inherits from `NSMutableSet`, so if you try to add the same object again, it's only in the set once.

However, in an `NSCountedSet`, the set tracks how many times that object was added. You can see how many times an object was added with `countForObject()`.

Note that when you call count on an `NSCountedSet`, it only returns the count of unique objects, not the number of times all objects were added to the set.

For instance, in your Playground, take the array of names you created in your earlier `NSMutableSet` testing, and add each one to an NSCountedSet twice:

Then, log out of the set itself and find out how many times "Ringo" was added:

Your log should read:
    
    
    Counted Mutable set: {(
        George,
        John,
        Ronnie,
        Mick,
        Keith,
        Charlie,
        Paul,
        Ringo
    )}) with count for Ringo: 2

Note that while you may see a different order for the set, you should only see "Ringo" appear in the list of names once, even though you can see that it was added twice.

### NSOrderedSet

An `NSOrderedSet` along with its mutable counterpart, `NSMutableOrderedSet`, is a data structure that allows you to store a group of distinct objects in a specific order.

"Specific order" -- gee, that sounds an awful lot like an array, doesn't it? Apple succinctly sums up why you'd want to use an `NSOrderedSet` instead of an array (emphasis mine):

Because of this, the ideal time to use an `NSOrderedSet` is when you need to store an ordered collection of objects that cannot contain duplicates.

### NSHashTable and NSMapTable

![Map table? ](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/10984514674_9315a34d25_z-250x250.jpg)

> _Not this kind of Map Table. (Courtesy the Tennessee Valley Authority(!) via Flickr Creative Commons)_

`NSHashTable` is another data structure that is similar to a set, but with a few key differences from `NSMutableSet`.

You can set up an `NSHashTable` using any arbitrary pointers and not just objects, so you can add structures and other non-object items to an `NSHashTable`. You can also set memory management and equality comparison terms explicitly using `NSHashTableOptions` enum.

`NSMapTable` is a dictionary-like data structure, but with similar behaviors to `NSHashTable` when it comes to memory management.

Like an `NSCache`, an `NSMapTable` can hold weak references to keys. However, it can also remove the object related to that key automatically whenever the key is deallocated. These options can be set from the `NSMapTableOptions` enum.

### NSIndexSet

An `NSIndexSet` is an immutable collection of unique unsigned integers intended to represent indexes of an array.

If you have an NSArray of ten items where you regularly need to access items' specific positions, you can store an NSIndexSet and use NSArray's `objectsAtIndexes:` to pull those objects directly:
    
    
    let items : NSArray = ["one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten"]
     
    let indexSet = NSMutableIndexSet()
    indexSet.addIndex(3)
    indexSet.addIndex(8)
    indexSet.addIndex(9)
     
    items.objectsAtIndexes(indexSet) // returns ["four", "nine", "ten"]

You specify that "items" is an `NSArray` since right now, Swift arrays don't have an equivalent way to access multiple items using an `NSIndexSet` or a Swift equivalent.

An `NSIndexSet` retains the behavior of `NSSet` that only allows a value to appear once. Hence, you shouldn't use it to store an arbitrary list of integers unless only a single appearance is a requirement.

With an `NSIndexSet`, you're storing indexes as sorted ranges, so it is more efficient than storing an array of integers.

## Pop Quiz!

Now that you've made it this far, you can test your memory with a quick quiz about what sort of structure you might want to use to store various types of data.

For the purposes of this quiz, assume you have an application where you display information in a library.

_Q: What would you use to create a list of every author in the library?_

_Q: How would you store the alphabetically sorted titles of a prolific author's entire body of work?  
_

_Q: How would you store the most popular book by each author?_

## Where to Go From Here?

I'd like to give special thanks to my fellow tutorial team member [Chris Wagner]( http://www.raywenderlich.com/about#cwagner), who started on an Objective-C version of this article before the SwiftHammer came down upon us all, for passing along his notes and sample project for me to use while pulling this tutorial together.

I'll also say thanks to the Swift team at Apple -- despite the fact that there's still considerable room for performance improvement in the native data structures, I had an awful lot of fun writing and testing in Swift. I may continue to use the Foundation data structures for a while, but I'm looking forward to porting a few little toys over to Swift. :]

Anyway, if you want to learn more about data structures for iOS, here are a few excellent resources:

  * [NSHipster](http://NSHipster.com/) is a fantastic resource for exploring little-known corners of the Cocoa APIs including data structures.
  * Peter Steinberger of [PSPDFKit](http://pspdfkit.com/) fame's [excellent article in ObjC.io issue 7](http://www.objc.io/issue-7/collections.html) on Foundation data structures. 
  * Former UIKit engineer Andy Matuschak's [article in ObjC.io issue 16](http://www.objc.io/issue-16/swift-classes-vs-structs.html) about Struct-based data structures in Swift. 
  * [AirspeedVelocity](http://airspeedvelocity.net/), a blog looking into some of the internals of Swift -- it gets bonus points for the Monty Python reference in its title. 
  * A super, super [deep dive into the internals of `NSMutableArray`](http://ciechanowski.me/blog/2014/03/05/exposing-NSMutableArray/), and how changing items in an `NSMutableArray` affects memory.
  * A fascinating study of how [NSArray and CFArray performance changes with extremely large data sets](http://ridiculousfish.com/blog/posts/array.html). This is further evidence that Apple names classes not for what they do under the hood, but how they work for developers. 
  * If you want to learn more about algorithmic complexity analysis, [Introduction to Algorithms](http://mitpress.mit.edu/books/introduction-algorithms) will fill your brain with more than you're likely to ever need to know in practice, but perhaps exactly as much as you'll need to know to pass job interviews.

If you'd like to dissect the numbers presented in this article further, you can download [the numbers spreadsheet used to track all the testing runs with Swift 1.2](http://cdn4.raywenderlich.com/wp-content/uploads/2014/11/performance-test-iPhone-6-iOS-8.3-Swift-1.2.numbers.zip) and analyze the data yourself.

Got more questions or want to dissect these numbers further? Go nuts in the comments below!
