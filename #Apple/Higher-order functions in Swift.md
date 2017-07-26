# Higher-order functions in Swift

_Captured: 2015-12-11 at 01:39 from [ijoshsmith.com](http://ijoshsmith.com/2015/12/09/higher-order-functions-in-swift/)_

This article reviews some very useful higher-order functions available in Swift's standard library, by showing a simplified implementation of each function. Along the way, I'll explain how all of the higher-order functions are based on a single loop.

## Let's get higher

Similar to how a rock guitarist's style can be influenced by listening to jazz, Swift is influenced by functional programming. One of the key functional contributions is polished support for higher-order functions.

By definition, a function is "higher-order" if it has one or more parameters that are functions and/or if it returns a function. In Swift, "passing a function" really means passing a _closure_, which is the name for an executable block of code. For example:

![example-func](https://ijoshsmith.files.wordpress.com/2015/12/example-func.png?w=640)

The textbook definition of higher-order functions does not suggest how mind-altering it can be to use them. This might not seem like a big deal, but using higher-order functions to process sequences/collections, instead of writing loops, can lead to a new and arguably better way of thinking about data processing. It allows the developer to stop thinking so much about _how_ something should happen and, instead, focus more on _what_ should happen.

Let's look at simplistic implementations of commonly used higher-order functions in Swift. I'll show you how they are all based on the **reduce** function, which itself relies on a single loop.

The code reviewed in this article is available [here](https://gist.github.com/ijoshsmith/ee472ee30bb1f9bb17c6).

Note: Never use my implementations of these functions, they exist only for explanatory purposes. My functions assume the input and output collections are arrays, for simplicity. My functions are not at all optimized. The standard library methods are much better than mine, so use them instead.

## reduce

The most versatile function reviewed here is **reduce**. Reducing a sequence means transforming many items into a single item. For example, an array of integers could be reduced to the sum of every integer in the array. In this case, a sequence of integers is reduced to a single integer.

An interesting caveat, however, is that the resultant "single item" can itself be a sequence of items. After all, an array is a thing unto itself, despite the fact that it might contain other things. We will see this caveat put to use later.

As I explain [here](http://ijoshsmith.com/2014/06/25/understanding-swifts-reduce-method/), reducing a sequence involves an _accumulator_. The accumulator is initialized to a default value, and can be updated when "combining" each element in the sequence.

![reduce.png](https://ijoshsmith.files.wordpress.com/2015/12/reduce.png?w=640)

This function uses a _for-in_ loop to iterate the sequence and combine its elements into a single item. When you use **reduce** or any of the functions based on it, you're reusing that loop instead of writing a new one. In a sense, higher-order functions enable a form of code reuse that avoids loop duplication.

Here is how **reduce** can be called:

![reduce-usage](https://ijoshsmith.files.wordpress.com/2015/12/reduce-usage.png?w=640)

Note that I'm using [trailing closure syntax](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Closures.html#//apple_ref/doc/uid/TP40014097-CH11-ID102) for the closure argument. That closure is the _combine_ parameter.

All of the other higher-order functions that process a sequence can be defined in terms of **reduce**. Let's check out how…

## filter

Creating a collection that has a subset of the items found in another collection is a very common programming task. It involves making a yes/no decision for each item in the source collection, to determine if the item should be included in the new collection. The **filter** function does everything except decide which elements to include.

![filter.png](https://ijoshsmith.files.wordpress.com/2015/12/filter.png?w=640)

This function reduces the input array into an output array by consulting the _include_ closure for each item in the input array. That decision-making logic is provided by the code which calls **filter**, such as the "is even number" logic in the above example.

## map

The **map** function performs a one-to-one transformation from an input sequence to an output sequence. The output type can differ from the input type.

![map](https://ijoshsmith.files.wordpress.com/2015/12/map.png?w=640)

Once again, the **reduce** function is used to implement a higher-order function. As this example shows, mapping a sequence is another way of "reducing" it.

Here's a more enticing example. Suppose you have an array of Customer objects but what you need is an array of each Customer's _uniqueID_ property value. You could create a mutable array, loop over the Customer objects, and add each Customer's identifier to the array. Or you could transform the customers to their identifiers with one simple line of code, using **map**. Here's how that might look using the Swift standard library **map** method.

![customers](https://ijoshsmith.files.wordpress.com/2015/12/customers.png?w=640)

This example uses a shorthand argument name (_$0_) to refer to the first argument passed into the closure, which is a Customer object.

Note that the standard library implements higher-order functions as instance methods, not module-level functions. In other words, the Swift methods are accessed via _object.method() _unlike my functions, which are accessed directly via _function()_.

## flatMap for optionals

The Swift standard library provides another mapping function, named **flatMap**. There are two versions of this function: one that supports mapping optional values and another that supports mapping a sequence of sequences, such as [[Int]] (i.e. an array of array of integers). Here is my implementation of the version for optional values:

![flatMap-optionals](https://ijoshsmith.files.wordpress.com/2015/12/flatmap-optionals.png?w=640)

This function is like a mixture of **map** and **filter**. It creates a sequence of mapped values, but no mapped value is added to the output sequence if the closure returns nil. In that sense, returning nil is similar to returning false from a closure passed to the **filter** function.

Tip: **flatMap** provides a handy way to remove all nil elements from an array of optional values. Here is how you would do this using the standard library's **flatMap** method.

![remove-nils](https://ijoshsmith.files.wordpress.com/2015/12/remove-nils.png?w=640)

## flatMap for sequences

The other version of **flatMap** is for processing a sequence of sequences. It performs something similar to string concatenation, where the mapped elements for each sub-sequence are joined together into one flat sequence.

![flatMap-seq](https://ijoshsmith.files.wordpress.com/2015/12/flatmap-seq.png?w=640)

I'm sure there are more efficient ways to implement this, but I chose to keep this code as straightforward as possible, for the sake of clarity. It, too, is based on **reduce**, which is just a simple wrapper around a loop.

## Parting thought

Higher-order functions that operate on sequences, a seemingly sophisticated concept, can be "reduced" to a simple _for-in_ loop. There is nothing inherently different or special about how they work. What makes them special is how they can elevate your perspective about common programming tasks.

So come on brothers and sisters, let's get higher.

![hippy](https://ijoshsmith.files.wordpress.com/2015/12/hippy.jpeg?w=640)
