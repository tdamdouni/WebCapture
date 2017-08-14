# The Function and the Object Should Be Friends

_Captured: 2017-08-03 at 07:37 from [dzone.com](https://dzone.com/articles/the-function-and-the-object-should-be-friends?edition=0&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=java%202017-08-02)_

When I hear people debate object-oriented vs. functional programming, I get a tune stuck in my head.

> _The Function and the Object_   
to the tune of _[The Farmer and the Cowman_ from _Oklahoma!_](https://duckduckgo.com/?q=the+farmer+and+the+cowman&t=hb&ia=lyrics)   
  
The function and the object should be friends.   
Oh, the function and the object should be friends.   
One holds state and methods, too; the other thinks monads are cool,   
But that's no reason why they can't be friends. 

I think the reason there's even an argument stems from three myths.

## Myth 1: "Pure" Programming Is Good Programming

When a new way of programming is invented, it takes a while to figure out what it's good for. This is true for both functional and object-oriented programming. Pure functional programming or pure OO follows the original idea -- which doesn't leave room to learn from experience.

Functional programming was invented in the 1950s as a way to apply theoretical mathematics (in particular, lambda calculus) to real-world computers. Being able to write code that looked like mathematical proofs made mathematicians and computer scientists happy, but for decades they struggled to explain why anyone else should care.

Then in 2004, [Google published a paper](https://research.google.com/archive/mapreduce.html) describing how MapReduce, a core functional pattern, solved the complexities of large-scale parallel programming. Simply put, loops are incompatible with parallel programming while synchronizing state between multiple threads or computers is error prone and difficult to debug. MapReduce eliminates both loops and state and lets developers reason about algorithms without concerning themselves about how the algorithms are run.

The fact that functional programming had found an application that had vexed developers for decades made people take another look. They liked what they saw: a compact and less error-prone way to write algorithms.

But functional programming has a downside. Pure functional programming has no side effects -- meaning no logging or I/O. What's more, pure functions always return the same output given a particular input, meaning no clocks or random-number generators. A pure functional language can, in theory, perform any computation, but real-world computers do more than compute. Even though there are now [workarounds](https://en.wikipedia.org/wiki/Monad_\(functional_programming\)), functional programming is best thought of as a tool -- and good craftspeople don't limit themselves to one tool.

One of Java's original signature features was that it is a pure object-oriented language: everything in Java exists within a class. Java was developed in the mid-1990s, just as OO experts were starting to formalize best practices, in particular, [SOLID](https://zeroturnaround.com/rebellabs/object-oriented-design-principles-and-the-5-ways-of-creating-solid-applications/). Java wasn't developed with SOLID in mind, rather it followed the example of Smalltalk, with heavyweight, stateful objects. Which brings us to our next myth.

## Myth 2: OO's Strengths Are Inheritance and Stateful Objects

Smalltalk came out of Xerox's Palo Alto Research Center along with a whole new way to interact with computers: the graphical user interface. Its advantages were clear: a window object on the screen corresponded to window code, a button corresponded to button code. Windows and buttons both knew how to draw themselves and handle events. They shared common code -- and making a new kind of button only required specifying how it differed from regular buttons. Each object was essentially a computer-within-a-computer, so it was obvious which thing was responsible for what.

Over the years, this style has started to show its limitations. Not necessarily problems inherent to OO, but with this computer-within-a-computer view of OO. The main issue has to do with how to manage complexity. If you have a small number of objects, or if you grant a few objects too much authority, you are barely doing OO. If you have too many objects, the complexity no longer lives in the objects, it lives in the coupling between objects -- subtle disagreements over expected behavior turn into bugs that are hard to track down.

What's more, single inheritance (one direct superclass per subclass) doesn't actually describe most use cases, but multiple inheritance gets really confusing. So let's remember why we use OO in the first place.

OO makes it really easy to identify which code is responsible for what. That "share" button? Look for a ShareButton. In fact, one of Java's great strengths -- which has been copied by just about every language since -- is that you have two hierarchies: a class hierarchy for shared code, and a package hierarchy for related use cases. Add legible stack traces, good logging, and global string searching (`find . -name '*.java' | xargs grep DistinctiveTextFromADialogBox`) and you can quickly hunt down bugs in any size code base.

The power of OO isn't from inheritance, it's from interfaces. Inheritance is just one strategy for describing a set of expectations and then having multiple classes follow them. The SOLID principles don't even mention inheritance by name, but they have a lot to say about interfaces.

The other problem with the computer-within-a-computer mindset is that people assume it has to be a full-fledged [von Neumann machine](https://en.wikipedia.org/wiki/Von_Neumann_architecture): a stateful computer with random-access memory that is ultimately programmed in a C-style language. Objective-C typifies this; stuff in square brackets is in "Objective" (like Smalltalk), everything else is in C. Computer scientists will tell you that there are all sorts of machines with totally different architectures. Regular expressions and pure functional programming produce finite automata: pipelines in which the same input produces the same output. Your graphics card uses a similar pipeline. This high-performance stateless architecture makes video games fast. The scene is recomputed for every frame.

There's nothing in OO that says that objects ought to be stateful, and plenty of reasons to avoid state. If two objects share similar state, complexity arises in keeping them in synch. Objects that can be modified make bug tracking harder because you need to track down where they could have been modified--especially if there are multiple threads involved. And here's a little secret: your compiler is turning your mutable variables into a series of immutables in order to do static code analysis. Immutables aren't just easier to read, they're also easier for the compiler to optimize.

## Myth 3: It's OO or FP, Not Both

This brings us to a key insight: OO and FP are good at completely orthogonal things! That is to say, OO is good at organizing the overall code base, whereas FP is just a bucket of functions. Meanwhile, FP gives you a way to compose algorithms, which is something OO doesn't touch. There is absolutely no reason why you can't use them together, each for its own strength.

In fact, when you do this, you remove the OO temptation to put a function within a class simply because it works only in that class (a violation of the Single Responsibility Principle, the "S" in SOLID). You also avoid the FP temptation to use lists and tuples instead of well-named data classes.

## Example

Here's a simple grammar for addition. The example comes straight from the [Kotlin documentation](http://kotlinlang.org/docs/reference/sealed-classes.html). It's a little dense, so we'll go through it line-by-line. Let's start with four OO classes.
    
    
    data class Sum(val e1: Expr, val e2: Expr) : Expr()

First, we define the class `Expr` which does nothing in itself; it is just there to initiate a class hierarchy. It is `sealed`, meaning that it is abstract and all of its subclasses must be defined in the same file.

Next, we define two `Expr` data classes: one to contain a number and the other to hold a sum of two numbers.

Finally, we create a singleton object to represent `Double.NaN`. We don't use that value directly since we need an `Expr` type.

Now, let's add a function to evaluate an expression. The `eval` expression takes an `Expr` and returns a `Double`. This code can sit on its own in the same file as the other code above (it doesn't have to be part of a class) or it could be kept elsewhere.

I won't go into the details of how this works, if you're curious read [Kotlin's when expression documentation](http://kotlinlang.org/docs/reference/control-flow.html#when-expression). The point is that we're decomposing an expression into its component parts and handling each case. **The code won't compile unless every case is handled.**

This may look odd to OO developers. After all, code for a class is usually found within that class. Methods which _could be_ in classes is often considered a _code smell:_ a sign that the code might be rotten. That comes from the old days when C developers were learning OO and would forget to do things OO-style.

However, putting `eval` directly in `Expr` would be a violation of the Single Responsibility Principle. (The "S" in SOLID.) The classes describe the grammar. They don't evaluate it, graph it, read it, write it, or anything else. The reason is that there are many design decisions related to those operations which have nothing to do with the grammar itself, so implementing them would add additional responsibilities.

This may not seem obvious for such a simple grammar, but even here external evaluation might be necessary. For example, we may want to add support for [Apache Spark](https://spark.apache.org/), GPU processing, and other exotic parallel-processing engines. In that case, defining the grammar is clearly different from evaluating it, and we clearly don't want to make the grammar depend on the evaluation engine. Keeping `eval` separate in the first place keeps the design clean.

## Conclusion: There's No Conflict!

In the musical _Oklahoma!_, the farmers and the cowboys were in competition because they had conflicting uses for the same territory. OO's territory is organizing the structure of a program to describe which piece of code is responsible for which functionality. Functional programming's territory is composing individual algorithms. There's no overlap, so there's no conflict. You can -- and should -- use both together.
