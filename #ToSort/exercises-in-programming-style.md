# Exercises in Programming Style

_Captured: 2018-03-22 at 19:46 from [dzone.com](https://dzone.com/articles/exercises-in-programming-style?edition=368219&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-22)_

[Read this guide](https://dzone.com/go?i=266422&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-robotic-process-automation-rpa%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Drpa%26utm_content%3Dlookbook-guide-rpa) to learn everything you need to know about RPA, and how it can help you manage and automate your processes.

In the [book club at work](https://henrikwarne.com/2016/11/08/developer-book-club/), we recently finished reading by Cristina Videira Lopes. The book consists of a simple program implemented in 33 different programming styles. It is a great way of showing the different styles, and the book was quite popular in the book club. The book is relatively new (it was published in 2014), and I don't think it is as well-known as it deserves to be. So here is a summary and review of it.

![](https://henrikwarne1.files.wordpress.com/2018/03/exercises-in-programming-style.jpg?w=332&h=443)

### Organization

The inspiration is a book from the 1940s by the French writer Raymond Queneau called [Exercises in Style](https://www.amazon.com/Exercises-Style-Raymond-Queneau/dp/0811207897/). In it, he tells the same short story in 99 different styles. Exercises in Programming Style uses the same concept but implements a short program in 33 different programming styles. Each style is defined by what constraints it imposes on the program.

The program counts the occurrences of words (term frequencies) in a file. The sample input is the book _Pride and Prejudice_ from the Gutenberg Collection. The program reads input words from a file, removes all non-alphanumeric characters, normalizes (down-cases) the words, removes stop words ("the", "a", "for", etc), counts the occurrences of all words, and finally prints out the 25 most common words in order.

All implementations are in Python, and most programs are one or two pages in the book. The size of the task is just right - it takes a little bit of programming logic, but it is small enough to quickly get familiar with. At the same time, it is enough to be able to express the logic in all the different styles covered.

Each style is presented in its own chapter and in the same way. First, the constraints of the style are given. Then the complete program in this style is listed, with line numbers, followed by an explanation of its key features. Next, there are comments on the use of this style, historical notes, further reading, a glossary, and exercises.

### Styles

The different styles are grouped together into nine categories. Here is a description of the categories and the styles.

**Historical.** The first program in this category has the constraints of very little memory and no identifiers. There is only memory, addressable with numbers. The result is a program that in many ways looks like assembler. The second style has a data stack, and all operations are done over data on the stack.

**Basic Styles.** There are three styles here that show how programming has developed. The first style is _Monolithic_, where the program is not sub-divided in functions. Instead, the logic is just in one long sequence of statements. In the next style, the logic is divided into functions, but all functions operate on shared global variables. In the third style, called _Pipeline_, the functions don't communicate using global data. Instead, they receive input and produce output. The program then becomes a long chain of function calls. This section also contains _Code Golf_, where the emphasis is on short and compact programs (in this case using libraries to achieve the goal).

**Function Composition. ** This section shows three different ways of connecting function calls together. The first uses recursion. The second uses a continuation-passing style, where each function is also given the next function that should be called. This resulting program is a bit hard to read because of this. The third illustrates the concept of a monad, and all function calls and resulting values are done through the monad, creating a calling pipeline.

**Objects and Object Interactions. **There are six styles here. The first four are variations on regular object orientation, going from a normal object-oriented program and one with abstract classes, to examples of how object orientation can be implemented (for example, how you find the method to call, and how the methods of an object are stored). Then there is an example of where you register for a callback and a version with infrastructure for publish and subscribe.

**Reflection and Metaprogramming. **The theme here is programs accessing and changing themselves as they execute. The first example of this style uses introspection (_inspect.stack()_ in Python) to check the calling function name. The second uses _exec/eval_ to build functions from strings containing Python code. The third example uses Python decorators to show how profiling of functions can be done, i.e. Aspect Oriented Programming (the author is one of the creators of AOP). The final program is an example of a plugin architecture, where functions from external files are brought in via a config file.

**Adversity.** Here, various error handling strategies are showcased. In the first example, when an error is encountered, an attempt is made to continue with a "reasonable" default value. The next throws an exception on every error, and the third also throws exceptions but tries to handle the errors at a higher level. There is a good discussion on the pros and cons of these strategies, and how it is easier or harder to implement, depending on if the language supports exceptions. There is also an example with types, but this becomes very awkward to show in Python. Finally, there is an example where all IO is quarantined, inspired by the design philosophy of Haskell's IO monad.

**Data-Centric.** In this section, the data, rather than the program behavior, is in focus. The first example solves the task by putting all the words in a database and uses SQL queries to find the top words. The next style emulates a spreadsheet, where changed values trigger a recalculation of dependent values. The final example works on data available as a stream (as opposed to getting the complete data at the beginning). In other words, the data is "pulled" by the sink, not pushed from the source. This is solved nicely with generators (using _yield_) in Python.

**Concurrency.** This part starts with one of my favorite paradigms, actors. Different threads send and receive messages to solve the task, and there is no shared memory between them. The downside of this example is that it is quite hard to follow the program flow. The next three examples use data spaces and map reduce (in two variations) to partition the task and then collect the results.

**Interactivity.** The final two examples allow for interactive usage. The first is an MVC (Model View Controller) version, although the view simply prints to the console (no GUI). The second is a REST solution, in the purest form, meaning that at each interaction, the next allowed actions are always presented to be selected from. Both these examples brought home the key points really well.

### Observations

I have read quite a lot of books on programming, but this book is unique among them. I really like the approach of showcasing various programming styles and paradigms by implementing the same program in different ways. First, there is a concrete program to look at for each case, instead of just a verbal description. Second, seeing all the programs next to each other highlights the differences in a very accessible way.

At work we use Python, so all of us already knew Python when reading the book. It was quite convenient to already be familiar with the language used, but I think the book works well even if you don't know Python. There are a few quirks, for example with classes in Python, but the author explains those when needed. The only time Python was a problem was when showing how types protect against errors in the _Adversity_ section.

When it came to understanding the programs, there was always a very good section called _Commentary_ that explained in detail how each program worked. For the most part, though, I preferred to just start reading the code and see if I understood how it worked. Usually, this was enough, but sometimes I missed not having an IDE for searching for usages, etc. I could have done that though because all of the programs are available on [GitHub](https://github.com/crista/exercises-in-programming-style).

For each style, there were references and historical notes. These were quite good and interesting. In particular, it was surprising that there were so many references to papers and books from the '50s and '60s. There were also a lot of references to Smalltalk, and to Dijkstra.

Before reading the book, I decided to implement [my own version](https://github.com/henrikw/exercises-in-programming-style/blob/master/word_count.py) of the term frequency program. This gave me a slightly better understanding of what is needed to solve the problem. Mostly, though, it was for the fun of seeing which style my solution was written in. The best match turned out to be _Pipeline_ in _Basic Styles_. Also, when testing my solution I noticed that the _Pride and Prejudice_ sample input the author is using also includes a few Project Gutenberg sentences in addition to the book text. I found this slightly disappointing.

My only criticism of the book is the naming of the styles. Naming is [famously hard](https://martinfowler.com/bliki/TwoHardThings.html), but also very important, because the names help you remember the styles better and makes discussing them easier. In many cases, there are already established names for the styles, but instead of using them, the author came up with her own. For example _Trinity_ instead of _MVC_, _Things_ instead of _Objects_, _Hollywood_ instead of _Callbacks_, _Bulletin Board_ instead of _Pub/Sub_ and _Kick Forward_ instead of _Continuation-passing_. Those names are OK, but it is much better to stick to the industry standard ones.

### Conclusion

I really enjoyed this book. It is unique in its approach, and it really succeeds in showing a wide variety of programming styles in just the right amount of code. Seeing the concepts implemented, and being able to compare them easily, is the main strength. At around 300 pages it manages to explain a lot in a concise way. Well done!

[Get the senior executive's handbook](https://dzone.com/go?i=266423&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-digital-transformation%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Ddigital-transformation%26utm_content%3Dtransformers-almanac) of important trends, tips, and strategies to compete and win in the digital economy.
