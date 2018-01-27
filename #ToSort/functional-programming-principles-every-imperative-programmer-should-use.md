# Functional Programming Principles Every Imperative Programmer Should Use

_Captured: 2018-01-23 at 00:09 from [dzone.com](https://dzone.com/articles/functional-programming-principles-every-imperative?edition=357094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-22)_

[Learn how](https://dzone.com/go?i=268439&u=http%3A%2F%2Falm.parasoft.com%2Flaser-focus-your-testing-with-change-based-testing%3Futm_campaign%3DImpact%252520of%252520Change%2525202018%26utm_source%3DDZone%26utm_medium%3DDZone%252520Java%252520Partner%252520Resources) to stop testing everything every sprint and only test the code you've changed. Brought to you by Parasoft.

Sometimes it seems like functional programmers are a totally different breed. Even by programmer standards, they seem more nerdy than the rest. They use weird terms such as "monad," "for-comprehension," and "lambda." They use languages that don't end every line with a semicolon. And, no matter how uneasy Java programmers are around C++ programmers, both groups can at least agree that Haskell is _weird_.

![XKCD 1270: Tail Recursion](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/functional-programming-principles/xkcd1312.png)

_The truth is, functional programming has much to offer, even to developers accustomed to working in imperative languages. (Source: [xkcd.com](https://xkcd.com/1270/))_

But what if there were programming principles favored by their functional paradigm languages that could be useful to the rest of us? The truth is, functional programming has much to offer, even to developers accustomed to working in imperative languages. In fact, many functional programming principles are becoming more and more prevalent in imperative languages today (I'm looking at you, Java 8).

## How Can Functional Programming Principles Benefit Me?

Every developer wants to write good, clean, maintainable, understandable code. The popularity of object-oriented programming, for example, partly arose from the code writing and maintenance benefits that followed from the way the paradigm encouraged developers to organize their code.

Functional programming offers tools and practices of its own that can make code more modular in ways that imperative programming cannot. Modular code leads to code that is easier to comprehend, easier to reuse, and easier to test.

You can think of these tools as a sort of glue that is available when we need to connect parts of our programs together. Imperative programming offers some types of glue; functional programming offers others. Having more types of glue at our disposal can improve the overall structure of the code we write.

In particular, practices like preferring immutability over mutability, writing pure functions, and breaking problems down using recursion can each serve as a new type of glue with their own particular benefits. The best part? These are practices, not language features, and are all available no matter what language you code in.

## Immutability

Many functional programming languages encourage immutability, often making values immutable by default. Immutability refers to preventing state from being modified. Mutation can happen on two levels: reference mutation and value mutation. Reference mutation happens when you assign a new reference to an existing variable:
    
    
    console.log(x, y); // Prints "{foo: 'baz'}, {foo: 'bar'}"

In this example, the reference `x` was mutated, but the object it was pointing to was not, so the value pointed to by `y` was not changed.

Value mutation happens when you modify an existing object:
    
    
    console.log(x, y); // Prints "{foo: 'baz'}, {foo: 'baz'}"

Here, even though `y` was not directly modified, it is referencing the same object as `x`, and the value of its `foo` property was changed.

The distinction between reference mutation and value mutation is a subtle one, but one that is still important to understand. In many languages with compile-time immutability, reference immutability is easy to add to your code -- but value immutability is more difficult. In Java, for example, you can declare a reference to be `final`, but this doesn't prevent you from changing the value of non-`final` values on the object being referenced, unless those values are also denoted as `final`.

Immutability is a low-cost way to ensure your code is decoupled. It allows you, as the developer, to control how objects in your system are allowed to be changed. This can be very helpful, for example, in a multithreaded program. Many (though not all) of the bugs and obscure edge cases that cause code to not be thread-safe arise because of mutation.

If objects and references are locked down, then you don't have to worry about a race condition where two threads try to overwrite a value at the same time, or where the value unexpectedly changes between reads. It also makes code easier to visually debug. The person reading the code does not need to worry about how a particular value may have changed by sources outside of the code they are currently reading, since the value cannot be changed at all. These are just a few of the ways that immutability can make your code safer and easier to reason about.

Immutability does come at a cost, though. Depending on the implementations of your objects and what language you are using, in order to modify an immutable object, you may need to make a clone of the entire object with the changes you want declared at the time the object is instantiated. This would result in a lot of objects being created and then discarded, which can trigger garbage collection more frequently.

Some use cases, such as game or GUI development, are a poor fit for immutability for this reason. However, even in these specialized environments, immutability can be used where appropriate in order to benefit from the safety guarantees it provides. Despite this caution, it is still possible to utilize immutability without a performance cost if you structure your objects correctly and are deliberate in which parts of your objects are immutable. For example, trees or linked lists are much easier to work with in an immutable fashion than are hash tables or arraylists.

Immutability changes the way we approach problems in our code. It changes the way that we think about the parts of our code and encourages us to put them together in cleaner, more thread-safe ways. However, immutability alone can at times seem like more of a hindrance than a help. Luckily, it is easier to work with when used in tandem with other functional programming principles. Many of these principles, like pure functions, are enabled by writing immutable code.

## Pure Functions

It's surely no surprise to know that functional programming places an emphasis on functions. However, they don't mean "function" the way an imperative programmer means "method" or "procedure." Rather, "function" in this context harkens back to the functions we learned about in math class. Things like the good ol' `f(x) = x + 1`. These functions are simple. They take a value and return a result. They are predictable and reliable. Most of all, they _only_ calculate their result. Functional programming encourages writing procedures after the manner of the functions found in mathematics.

These are called pure functions.

The most significant characteristic of pure functions is that they don't modify any state. This includes state on the arguments provided to the function, global state, or even state external to the program itself. Functional programmers like to say that non-pure functions can really do anything they want, and there's no way to know at the call site that there won't be side-effects at the call site. One amusing example is that calling a non-pure function may launch a missile somewhere. Certainly not likely, but how can you guarantee that calling some arbitrary procedure won't actually do this without investigating the code yourself? If the function is pure, then it cannot launch any missiles, by definition.

Of course, function purity can be taken too far. If no state is modified, then a program might as well not have been run at all. Thus, pure functions should be used with care, just as with immutability.

![XKCD 1312: Pure Functions](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/functional-programming-principles/xkcd1270.png)

_Function purity can be taken too far. If no state is modified, then a program might as well not have been run at all. (Source: [xkcd.com](https://xkcd.com/1312/))_

Pure functions come with quite a few benefits. A big one is a property called **referential transparency**. Referentially transparent functions can, in theory, have the call site replaced with the actual result of invoking the function without changing the program's behavior at all.

Stated another way, referentially transparent functions guarantee a given result for a given set of inputs. `f(x) = x + 1` will always return 3 when `x` is 2, no matter how many times you invoke it. This means that not only can the function not mutate any state when it is called, but it also can't rely on any external state that may be mutated as well. Functions that are referentially transparent can easily have their results cached. For example, memoization and dynamic programming become possible when you use pure functions.

Pure functions are also naturally thread-safe. Because no state is mutated, a pure function can be called by as many threads as you want in parallel. In fact, pure functions make parallelization and concurrent programming a breeze. Given two pure functions that do not depend on the results of one another, you can call the functions in any order without causing race conditions.

The easiest way to convert a function into a pure function is to inject all of the state that a pure function needs as arguments to the function. This can have some drawbacks if your function is too complex because you may end up with long parameter lists.

This also highlights the importance of using pure functions with care alongside the OOP paradigm. Methods on objects have a lot of state available to them that doesn't need to be provided as a parameter. This tension can be resolved if you make the member variables on an object immutable or use static functions that take the object as one of their parameters (think Python).

## Recursion

Recursion -- and its refined subtype, tail recursion -- is a concept that should be familiar to almost every programmer. Recursion is nothing short of essential in functional programming, where the emphasis on immutability and pure functions render the conventional `for` loop awkward to use, at best, and discouraged in the general sense. Recursion is a looping mechanism where a function calls itself repeatedly for every pass of the loop instead of relying on a counter variable.

One of the core concepts of recursion -- and the reason I include it as a tip to be used by imperative programmers -- is breaking down larger problems into smaller, self-similar pieces. Smaller problems are easier to understand and more intuitive to solve. This naturally leads to improved code comprehension and maintainability.

Whenever you're faced with code that needs to loop, ask yourself if recursion is the right way to perform the loop. Iterating over an array to call a function on each of the values it contains is better suited to a normal loop, while sorting an array using the quicksort strategy would be a great candidate for recursion.

Always remember to use tail recursion if the problem allows for it (assuming your language supports it). Tail recursion is when the recursive call is the very last thing that happens before the function ends -- in other words, it is in the tail position. This recursive function is tail-recursive:
    
    
        acc = acc || 1; // acc can be omitted when initially invoking factorial()
    
    
            return factorial(x - 1, acc * x);

Tail recursion is beneficial because it avoids one of the greatest weaknesses of recursion: stack overflows. The compiler can optimize tail-recursive calls in such a way that they do not result in function pointers on the stack getting deeper and deeper with every call. If your recursive function may be called hundreds of times, consider writing your function in a tail-recursive way or rewriting it using more conventional looping mechanisms.

## Conclusion

The divide between functional programmers and imperative programmers is not as wide as you might think. At the end of the day, both sides have a lot to contribute to the world of programming. Tools familiar to the functional programming world can be utilized in imperative programming languages to make our code cleaner, more modular, and easier to maintain.

[Get the top tips](https://dzone.com/go?i=268440&u=http%3A%2F%2Falm.parasoft.com%2Fget-unit-testing-done-right%3Futm_campaign%3DUTA%2525202018%26utm_source%3DDZone%26utm_medium%3DDZone%252520Java%252520Partner%252520Resources) for Java developers and best practices to overcome common challenges. Brought to you by Parasoft.
