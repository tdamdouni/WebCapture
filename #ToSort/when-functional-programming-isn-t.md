# When Functional Programming Isn't

_Captured: 2018-03-08 at 21:43 from [dzone.com](https://dzone.com/articles/when-functional-programming-isnt?edition=366221&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-08)_

![](https://www.leadingagile.com/wp-content/uploads/2018/02/When-functional-programming-isnt.jpg)

When [functional programming](https://en.wikipedia.org/wiki/Functional_programming) started to become a "thing" in the software industry, I had a lot of difficulty understanding the fundamentals. I've always worked primarily in business application software and in system administration. The mathematical orientation of functional programming languages represented an unfamiliar paradigm for me.

I mentioned this to a colleague, and he told me that he fully grokked FP after learning to use lambda expressions in C#. His reply puzzled me, as I had been using lambda expressions in Java, Ruby, and JavaScript for some time, and I knew that similar features were present in other languages, like Python, SmallTalk, and Lisp. I had also done the usual tutorials for languages that had some FP features, like Scala and Clojure. Could it be that FP was really nothing more than this, decorated with arcane buzzwords?

Surely there was more to it. My attempts to teach myself Haskell had not gone as easily as learning other languages that were based on familiar paradigms. Haskell code was clearly quite different from lambda expressions in Java or Ruby. It seemed, instead, that support for lambda expressions in object-oriented languages had been _inspired_ by functional languages, but that there was much more to FP than just that.

## Mathematical Programming

As I read more about FP, it became clear that the purpose of functional languages is to model mathematical expressions. It might have been better if the inventors of FP had named it "mathematical programming" instead. It isn't just about writing "functions," after all.

[APL](https://en.wikipedia.org/wiki/APL_\(programming_language\)), a language developed in the 1960s, uses non-ASCII symbols in its source code to represent mathematical concepts. A special keyboard mapping was designed to support working in APL. It looks like this:

![](https://www.leadingagile.com/wp-content/uploads/2018/02/apl-keyboard-mapping.png)

Here's an example of Conway's Game of Life implemented in APL, from [StackOverflow](https://stackoverflow.com/questions/4110165/is-there-a-programming-language-that-uses-characters-other-than-those-in-the-no):

![](https://www.leadingagile.com/wp-content/uploads/2018/02/apl-conway.gif)

Other functional languages, such as [J](http://www.jsoftware.com/), substitute ASCII symbols for mathematical symbols so that mathematical expressions can be entered using a standard keyboard. Here's an example of Conway's Game of Life [implemented in J](http://www.leadingagile.com/2018/02/applying-brooks-law/):

Even if you aren't familiar with those languages, you can probably see the two code snippets are roughly similar. Personally, I find the J code harder to read, but I appreciate the practicality of being able to enter source code with a standard keyboard.

One of the key uses of mathematical expressions is to process _lists_ or _series_, like this formula for calculating the area under a curve (image borrowed from [here](https://www.math.ucdavis.edu/~kouba/CalcTwoDIRECTORY/defintdirectory/)):

![](https://www.leadingagile.com/wp-content/uploads/2018/02/area-under-curve.gif)

So, there's an integral and a summation and so forth. Functional programming languages are designed to solve this sort of problem efficiently based on concise source code. The language may have a number of these common calculations built in or available through libraries.

Lambda expressions in object-oriented languages serve the same purpose. The examples we find online can be confusing for a business application programmer because we don't often face mathematical problems. Programmers who write data analytics code and those who work on scientific/engineering solutions will find the usual examples more relatable.

In business application programming we _do_ quite often process collections of objects, either filtering a subset of members, combining two collections, or performing an operation on all members (like _map_ and _reduce_ operations). Lambda expressions often enable us to express these operations in a concise and readable way, as compared with (for instance) nested _for_ loops. The code also tends to be less error-prone than a complicated loop structure.

For example, here's an iterative solution to the Fibonacci series in Java (snagged from a [StackOverflow question](https://stackoverflow.com/questions/21710756/recursion-vs-iteration-fibonacci-sequence)):
    
    
        int x = 0, y = 1, z = 1;
    
    
        for (int i = 0; i < n; i++) {

For contrast, here's a solution using lambda expressions (thanks to [Artem Lovan](https://gist.github.com/artlovan/d7315b375f4553a1be1605b16c7a9098)):
    
    
        return Stream.iterate(new int[]{0, 1}, s -> new int[]{s[1], s[0] + s[1]})

(Yes, I was lazy and didn't write my own examples. How different could they have been, anyway?)

You can see for yourself that the lambda version is more concise and expresses its intent effectively.

## Practical Software Development Takeaways

Is it true that when you've mastered lambda expressions in an OO language, you've also mastered functional programming? I don't think so. But I _do_ think it's a good idea to master lambda expressions.

General business application programming has taken several ideas from FP that improve our software design. These include (at least):

  * avoid hidden side-effects
  * ensure referential transparency
  * use list-processing functions rather than loops where it makes sense

Those guidelines are not really different from conventional OO design guidelines. Avoiding hidden side-effects is another way to express the idea of _separation of concerns_ or _single responsibility principle_. When you do that, you also achieve _referential transparency_. Lambda expressions that operate on collections make the code more expressive of intent and more concise. It has always been a goal of OO design to make the code expressive of intent.

## Microtests

Contemporary development practices include the idea of _microtests_, which are very small examples of functionality that exercise (in an OO language) a single logical path through a single method. They are often used to support emergent design through test-driven development as well as to explore the functionality of an existing code base by probing it with small test cases.

When I use lambda expressions in an OO language, I find that the smallest logical chunk of code that can be exercised by a micro-example is larger than when I use iteration or recursion for the same solution. Let's look at the two Java examples above, and write microtests for them.

If we take that iterative example and flesh it out a bit so that we can obtain a Fibonacci series, we get this:
    
    
            int x = 0, y = 1, z = 1;
    
    
            for (int i = 0; i < n; i++) {
    
    
        public List<Integer> fibSeries(int limit) {
    
    
            List<Integer> result = new ArrayList<Integer>();
    
    
            for (int i = 0 ; i < limit ; i++ ) {
    
    
                result.add(fib(i));

Some microtests for that code could look like this:

The key point here is that the smallest chunk of logic we can check is the code that determines the next number in the series. The third example shows that we _could_ verify the functionality by checking the entire list. However, if there is an error in the single-number routine the whole-list check won't take us directly to the offending line in the source. (You may have to imagine something more complicated than this to visualize the problem.) There are special rules for the first few numbers in the Fibonacci series, and that's where an error is most likely.

An advantage of using a lambda expression is that the correctness of the series can be assured by the lambda expression itself. The smallest microtest example we need is one that covers the whole series.

Adjusting the sample lambda solution so it will compile, and making the method non-static, we have this:

You can already see a couple of advantages, even before we consider the microtests. This solution involves less code, and therefore less probability of an error occurring. The code is also a little more self-describing.

We don't need microtest examples to verify that individual numbers in the series will be calculated correctly, as that is baked into the lambda expression. We only need to verify that the series comes out as expected. So, we have fewer test cases to maintain, without getting into the [ice cream cone anti-pattern](https://medium.com/@fistsOfReason/testing-is-good-pyramids-are-bad-ice-cream-cones-are-the-worst-ad94b9b2f05f) of test automation.

## Programmer Effectiveness

It takes a programmer about the same amount of time and effort to read/understand, design/create, comprehend/modify a line of source code regardless of the programming language involved. When a language offers more power per source expression, solutions can be built using fewer lines of code. Programmers' time is used more effectively than when they must write in a language that doesn't offer much power per expression.

Functional languages pack a lot of power into each line of source code. When we use elements borrowed from FP in our OO languages, we can gain some of those benefits, too.

To illustrate, here are some code snippets that sum the values in an array. First, let's look at Intel assembly language. This example is borrowed from [here](http://heather.cs.ucdavis.edu/~matloff/50/LinuxAssembly.html).

So, we have 21 lines of source code to understand and maintain. Due to the nature of the language, we also have to include quite a few source comments to communicate the intent of the code. Those things increase the time and effort programmers must expend to live with this solution. The dependence on comments introduces a risk that the comments and code will no longer match, after the solution has been modified during its long years of production life.

The equivalent code in Java, using iteration to sum the values, looks like this:

That's seven lines (four of which are "meat"), which is a lot more understandable than 21 lines. We don't need any source comments to explain the intent of the code, either.

Now let's do the same thing using a lambda expression.

Using a lambda expression reduces the number of source lines to three (two of which are "meat"). It makes programmers' time just a little bit more impactful, and makes the code just a little bit more [habitable](https://silkandspinach.net/tag/habitable-code/).

Another advantage: Those "non-meat" lines in source code are clutter that makes it harder to follow what the code is doing. With the Java iterative solution, almost half the source lines are clutter. With the lambda solution, there's only one line of clutter, and it's nothing more distracting than a closing curly brace.

## Learning Resources

Martin Fowler has written a very clear [introduction to _collection pipelines_](https://martinfowler.com/articles/collection-pipeline/), which are in essence what we are writing when we use the lambda expression features of OO languages. That article contains numerous examples in several languages.

He also wrote a [step-by-step guide](https://martinfowler.com/articles/refactoring-pipelines.html) to refactoring a loop into a collection pipeline in a way that safely preserves behavior at each step. I suggest this is a useful skill to practice in a dojo setting or on your own.

The ever-practical Brian Marick has been spending considerable time delving into FP in the past couple of years. He has shared his learning journey on Twitter, and has produced a couple of very useful e-books that can help a general software developer get a handle on FP.

_[Functional Programming for the Object-Oriented Programmer_](https://leanpub.com/fp-oo) and _[An Outsider's Guide to Statically-Typed Functional Programming_](https://leanpub.com/outsidefp) introduce FP in a way an everyday software development practitioner can relate to, as opposed to the abstract approach offered by most other sources. The latter book seems to have offended some in the FP community for reasons I don't understand. In any case, these are great resources for learning about FP, if you're already an experienced OO developer.

## Conclusion

Using lambda expressions in an OO language doesn't make you a functional programmer, but using ideas from the FP community to produce clean OO code is a Good Thing. OO code that uses a functional _style_ will tend to have fewer problems of the kinds that arise from hidden side effects and poor separation of concerns. Lambda expressions are readable and expressive of intent for sections of code that process lists or collections; often moreso than iteration. In Java, for instance, using the explicitly-defined [functional interfaces](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html) helps us produce reliable code that is compatible with other useful design techniques such as immutable objects.
