# Transcending the Limitations of the Human Mind

_Captured: 2017-11-10 at 00:51 from [dzone.com](https://dzone.com/articles/transcending-the-limitations-of-the-human-mind?edition=334849&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-07)_

Get the Edge with a Professional Java IDE. [30-day free trial](https://dzone.com/go?i=255333&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-preroll%26utm_campaign%3Didea).

No, this article is not about mind-altering substances, rather it is about how to deal with complexity in general and in software development in particular.

All but the simplest problems that we face in software development exceed the capacity of our minds. Our short-term memory can barely hold [7-8 items](https://en.wikipedia.org/wiki/Short-term_memory#Capacity) on a good day, and our [computing capacity](https://en.wikipedia.org/wiki/Computer_performance_by_orders_of_magnitude) is almost non-measurable against computers.

How is it then that we can design and implement software monoliths of millions of lines of code despite our apparent limitations? How can we learn and understand such large and complex systems? How can we maintain such systems? How can we get better at dealing with large systems, or perhaps more importantly, deal with smaller systems more easily?

## Cognitive Capacity

There is some scientific evidence that [Cognitive Capacity](https://en.wikipedia.org/wiki/Cognitive_load) is a real and measurable thing. In short, it means that everything we have to keep in mind or think about during the solution of a particular problem creates _Cognitive Load_. That is, it uses up part of our total _Cognitive Capacity_, which is very much finite.

Everything means literally everything. Not just the business concepts, their rules, and relationships, but all the technical details we have to track, like remembering special meanings to certain values, whether one method must be called after another one, whether the object needs to be explicitly initialized before usage, what effect certain values would have elsewhere, and so on.

There are two conclusions to be taken from this theory if we want to maximize the amount of problem complexity we are able to handle (or minimize the difficulty of handling a given amount of complexity):

  1. We have to avoid using our Cognitive Capacity for technical details because those don't get us closer to solving the "business" problems.
  2. We have to limit the complexity of the "business" logic we have to think about at any given time to be below our Capacity.

## Whose Cognitive Capacity Are We Talking About?

Every line of code is written exactly once (if we consider modifications a completely new line) but are potentially read many times during the life of the software.

In other words, the effort to _write_ is not as important as the effort to _read_ and _understand_ a given piece of code. It seems reasonable therefore to suggest that those writing (or modifying) the code should do everything in their power to minimize the Cognitive Load of the readers.

This article argues that the convenience of the _writer_ is irrelevant, indeed a writer should follow the requirements outlined in the next topics rigorously and thoroughly, even if it leads to significant additional effort.

## Decomposition

Developers of large systems do not (on average) have more brain capacity than any other developer and they aren't magicians either. What they do have, however, is a very simple trick to be able to cope with increased complexity.

This trick is called _decomposition_. If you know this trick and you know how to do basic things like the "Hello World" program, reading/writing files, calculating things, the syntax of your programming language, etc., then you can write arbitrarily complex software.

Decomposition is a method to _break_ a big problem into a number of smaller problems, with the assumption that the smaller problems, taken together, will solve the big problem.

![Decomposition of the big problem into smaller problems with two levels.](https://dzone.com/storage/temp/7102888-problem-decomposition1.png)

> _Decomposition of the big problem into smaller problems with two levels._

The above diagram shows a problem that cannot be directly solved because of its size, so decomposition is applied. The resulting two smaller problems are still uncomfortably large, so those are decomposed further. On each _level of decomposition_, the actual total problem size remains approximately equal to the original problem, but each time, the individual tasks become smaller until they are directly solvable.

Consider the following task:

Most people will not solve this task in one go, but decompose the task into smaller ones. For example, first solve "4 * 5", then solve "3 * 2", and then add the two results together. Instead of one big task, three smaller ones are executed, with the end result being the same.

## Abstraction

Decomposing a problem is, unfortunately, not as easy as it sounds. In the previous section, we assumed that each of the resulting small tasks at the end was independent and, therefore, they were solvable without considering the other ones. This is, however, very rarely possible in software development. There are always dependencies between parts of software, between objects, modules, etc.

Even in the simple calculation example above, the three tasks are _not_ completely independent, the "last" task is obviously depending on the previous two multiplication tasks.

So why is this a problem? It is a problem because if we have to think about things coming from other tasks, we are wasting our Cognitive Capacity with stuff not directly relevant to the task at hand. Dependencies transfer Cognitive Load "up", from the "dependee" to the "depender", ultimately defeating decomposition if left unchecked.

![Image title](https://dzone.com/storage/temp/7102893-dependend-tasks.png)

So how could we limit this backflow of Load up the dependency tree? The answer to that is _Abstraction_. Abstraction splits up the individual bubbles into two distinct parts. One part is called the _interface_ and is responsible for containing the knowledge (the "Load") that the dependent _absolutely needs to know_ in order to work, and the other is called the _implementation_, which contains everything else. We cannot eliminate the backflow entirely this way, but we can limit it quite well.

This method is called abstraction=i6\;;;;;;ry2 because the goal is to hide details and in turn offer higher level (more abstract) view of everything that is below, to the layers above.

![Image title](https://dzone.com/storage/temp/7102902-dependend-tasks-abs1.png)

This concept was already used above to solve this equation:

For the last step, adding the results of the two multiplications together, we don't actually have to know how to multiply, we just have to know how to add. Why is the knowledge of multiplication no longer required at this last step although it does depend on the multiplication steps?

It is because the multiplication tasks _abstracted_ the details of the multiplication away. The _interface_ of those tasks was just the resulting number and only the _implementation_ contained the actual details of how to multiply.

### Leaky Abstractions

Abstractions that do not perfectly hide the details of the underlying layers of abstractions are said to be _leaking_. They are leaking unwanted knowledge up the dependency hierarchy and, with it, making the abstraction layers above use up more cognitive capacity from the developers.

![Image title](https://dzone.com/storage/temp/7102907-dependend-tasks-leak1.png)

A leaky abstraction, even if it leaks just a little, can have a very big impact on its surroundings because of amplification through dependencies. Each dependency will carry the same amount of additional leaked knowledge, thereby multiplying the effect of one leak with the number of dependencies on the abstraction. Therefore the more an abstraction is used, the more rigorously it has to be designed to eliminate or at least minimize leakage.

![Image title](https://dzone.com/storage/temp/7102912-dependend-tasks-leak-amplification2.png)

Note, that whether an abstraction leaks or not cannot be decided objectively without context, only when considering the business meaning and responsibilities too. In other words, a leak can only exists _with respect to_ the requirements. Code alone, without knowing the exact requirements, cannot leak.

#### Examples of Leaky Abstractions

Consider the following class:

This is sometimes referred to as an _immutable value object_. It is "[immutable](https://en.wikipedia.org/wiki/Immutable_object)" because it cannot be modified (mutated) at all, and it is a "[value object](https://en.wikipedia.org/wiki/Value_object)" because it represents a value and has no identity (two objects with the same values are interchangeable).

Let's further assume, that the business requirements of the system this class are a part of demands that we can add two such `Amount`s together. In this case, the above class is _heavily leaking_. There are several pieces of knowledge that could be easily hidden, but aren't:

  * The fact that an `Amount` is composed of a _value_ and _currency_.
  * The type of the _value_, and with it the complete knowledge about values.
  * The type of the _currency_, and with it the complete knowledge of currencies.

A proper abstraction (for the above requirements) would look like this:

This fulfills all the requirements the same way the previous implementation does but requires much less knowledge, therefore causes much less Cognitive Load in the developer using this class.

Another example from a banking application:

It turned out that this class was used for answering remote calls from other systems based on XML messages. It can be therefore considered an abstraction of a proper response message according to the required protocol. In this case, however, there is significant leakage here because the usage of the objects of this class should not require the caller to know all the fields of this class. The class should look more like this:

### Technical Leaks

You might have heard the saying "[If it compiles, it works](https://wiki.haskell.org/Why_Haskell_just_works)" in relation to using some class or library, usually in the context of a functional programming language. This refers to a perfect or near perfect abstraction, where misusing the interface is virtually impossible, therefore all syntactically valid code constructs are likely to be semantically correct too.

Technical leaks are certain pieces of information a developer has to learn (in addition to the language and its prevailing idioms) in order to use something (a class or a module), even though it has nothing to do with the business case at hand. In other words, technical leaks occur _if there is a syntactically valid sequence of method calls that has no real business meaning_ (it compiles, but it does not work).

Not all languages are powerful and expressive enough to arrive at a near perfect abstraction all the time. Still, in the confines of a given language, technical leaks should be always avoided, especially in core concepts, where amplification through multiple dependencies could make problems much worse.

We've already seen an example of a technical leak with the `CashTransferResponse` class. Its original "bean" implementation looked like this:

It was, therefore, possible to write this code somewhere else:

This type of leak is sometimes called _temporal coupling_. It requires the developer to call certain methods in some predetermined order, all the correct setters in this case, before sending can be done. The above code is syntactically correct but will always fail because sending does not make sense without the "transferId".

Another form of this type of abstraction error is having methods to initialize or close. Consider this `DatabaseTransaction` for example:

Obviously, this class needs the developer to make sure the transaction is closed properly. The developer is probably expected to use Java's try-with-resources construct. It's pretty easy to see, however, that the compiler can not really check whether the transaction is always properly closed, so there is technical leakage.

This is one way the technical leak in the `DatabaseTransaction` could be avoided:

In this case, the whole logic is supplied _into_ the transaction itself, which can, therefore, close itself after execution, freeing up precious Cognitive Capacity on the developer side.

## Distractions

We developers, being naturally attracted to algorithms and design patterns, sometimes concentrate too much on the technical aspects of our code: thinking about how to apply certain patterns, how to make a clean separation between certain parts of the code, etc.

This tendency is in itself mostly advantageous, except when it starts to dominate our code. In this case, it becomes a _distraction_. It distracts the reader from the actual content (the domain) and encourages thinking about irrelevant details.

So what is a distraction? A _distraction_ is anything that does not directly solve at least some part of the problem domain, or it can not be easily identified as solving some part of the problem.

[Java Beans](https://en.wikipedia.org/wiki/JavaBeans) (see `CashTransferResponse` above), for example, are distractions in this sense. They do not solve any part of the problem. They are merely a grouping of data that may or may not belong together in some context. They don't hide anything, therefore, their existence does not make the problem domain smaller in any way, or free up any Cognitive Capacity.

Sometimes distractions can be recognized just by looking at their name: _Service_, _Manager_, _Util_, _UseCase_, _Interaction, Strategy_, etc. objects are all distractions. These are usually objects created for the _convenience of the writer_ only and contain some grouping of procedures to operate on other objects. Their name clearly betrays that they are not part of the "business."

Again, most programming languages (if not all) require at least some amount of distractions to exist: bootstrapping the first objects, binding technical aspects into the application, etc. Still, distractions should be rigorously avoided as far as possible.

## Conclusion

Since the human mind has a very limited capacity to deal with complexity, we have to make sure that we use this capacity very wisely. This involves the following steps:

  1. Decomposing the problem domain, potentially through multiple levels, until it's split into small enough chunks so every one of them can fit into a human mind.
  2. Creating abstractions (interface and implementation) to prevent knowledge from escaping the chunks. A chunk must fit a human mind including all the interfaces it needs!

During these activities, it is extremely important to:

  1. Refrain from distractions. Do not create objects or classes that are artificial, because they use up brain capacity without contributing directly to the solution.
  2. Avoid technical leaks as much as possible. Syntactically correct code should be semantically correct too.
  3. Avoid leaky abstractions. Make an extra effort to demand as little business knowledge from the user of your code as possible.

Most importantly, these rules should be followed rigorously whenever code is written, even if it takes significantly more time to do so! It will always pay for itself in the end!

[Get the Java IDE](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea) that understands code & makes developing enjoyable. Level up your code with IntelliJ IDEA. [Download the free trial](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea).
