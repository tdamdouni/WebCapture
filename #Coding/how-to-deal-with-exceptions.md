# How to Deal With Exceptions

_Captured: 2018-01-26 at 20:33 from [dzone.com](https://dzone.com/articles/how-to-deal-with-exceptions?edition=358095&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-26)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

I recently had a discussion with a friend, who is a relatively junior but very smart software developer. She asked me about exception handling. The questions were pointing to a tips-and-tricks kind of path and there is definitely a list of them. But I am a believer in context and motivation behind the way we write software so I decided to write my thoughts on exceptions from such a perspective.

Exceptions in programming (using Java as a stage for our story) are used to notify us that a problem occurred during the execution of our code. Exceptions are a special category of classes. What makes them special is that they extend the Exception class which in turn extends the Throwable class. Being implementations of Throwable allows us to "throw" them when necessary. So, how can an exception happen? Instances of exception classes are thrown either from the JVM or in a section of code using the throw statement. That is the how, but why?

I am sure that most of us cringe when we see exceptions occur, but they are a tool we can use to our benefit. Before the inception of exceptions, special values or error codes were returned to let us know that an operation did not succeed. Forgetting (or being unaware) to check for such error codes, could lead to unpredictable behavior in our applications. So yay for exceptions!

There are 2 things that come to mind as I write the above. Exceptions are _a bad event_ because when they are created we know a problem occurred. Exceptions are _a helpful construct_ because they give us valuable information about what went wrong and allow us to behave properly in each situation.

Trying to distil the essence of this design issue: _a method/request is triggered to do something but it might fail - how do we best notify the caller that it failed? How do we communicate information about what happened? How do we help the client decide what to do next? The problem with using exceptions is that we "give up" and not just that, we do it in an "explosive" way and the clients/callers of our services have to handle the mess_.

So my first advice when it comes to exceptions, since they are a bad event, is to try to avoid them. In the sections of software under your control, implement a design that makes it difficult for errors to happen. You can use features of your language that support this behavior. I believe the most common exception in Java is the `NullPointerException` and `Optional` can help us avoid this. For instance, let's say we want to retrieve an employee with a specified id:

So much better now. But besides the features of our language, we can design our code in a way that makes it difficult for errors to occur. If we consider a method, which can only receive positive integers as an input, we can set our code up so that it is extremely unlikely for clients to mistakenly pass invalid input. First, we create a `PositiveInteger` class:

Then, we make a method that can only use a positive integer as an input:

These are of course simple examples and I did argue that the heart of the issue is that occasionally problems occur and then we have to inform clients about what happened. So let's say we retrieve a list of employees from an external back-end system and things go wrong. How can we handle this?

We can set our response object to `GetEmployeesResponse`, which would look something like this:

But let's be realists, you do not have control over every part of your codebase and you are not going to change everything either. Exceptions do and will happen, so let's start with some brief background information on them.

As mentioned before, the Exception class extends the Throwable class. All exceptions are subclasses of the exception class. Exceptions can be categorized in checked and unchecked exceptions. That simply means that some exceptions, the checked ones, require us to specify at compile time how the application will behave in case the exception occurs. The unchecked exceptions do not mandate compile time handling from us. To create such exceptions, you extend the RuntimeException class which is a direct subclass of Exception. An old and common guideline when it comes to checked vs unchecked is that runtime exceptions are used to signal situations which the application usually cannot anticipate or recover from, while checked exceptions are situations that a well-written application should anticipate and recover from.

Well, I am an advocate of _only using runtime exceptions_. And if I use a library that has a method with a checked exception, I create a wrapper method that turns it into a runtime. Why not checked exceptions then? Uncle Bob, in his "Clean Code" book, argues that _they break the Open/Closed principle_, since a change in the signature with a new throws declaration could have effects in many levels of our program calling the method.

Now, checked or unchecked, since exceptions are a construct to give us insights on what went wrong, they should be _as specific and as informative as possible_ on what happened. So try to_ use standard exceptions_, as other developers will understand what happened easier. When seeing a NullPointerException, the reason is clear to anyone. If you make your own exceptions, _make them sensible and specific_. For example, a ValidationException lets me know a certain validation failed, an AgeValidationException points me to the specific validation failure. Being specific allows one to both to diagnose what happened but also to specify a different behavior based on what happened (the type of exception). That is the reason why you should always catch the most specific exception first! So here comes another common piece of advice that instructs us to not catch on "Exception." It is _valid advice which I occasionally do not follow_. In the boundaries of my API (let's say the endpoints of my REST service) I always have generic catch Exception clauses. I do not want any surprises and something that I did not manage to predict or guard against in my code, to potentially reveal things to the outside world.

Be descriptive but also _provide exceptions according to the proper level of abstraction_. Consider creating a hierarchy of exceptions that provide semantic information in different abstraction levels. If an exception is thrown from the lower levels of our program, such as a database related exception, it does not have to provide the details to the caller of our API. Catch the exception and throw a more abstract one, that simply informs callers that their attempted operation failed. This might seem like it goes against the common approach of "catch only when you can handle," but it is not. Simply, in this case, our "handling" is the triggering of a new exception. In these cases, _make the whole history of the exception available_ from throw to throw by passing the original exception to the constructor of the new exception.

The word "handle" was used many times. What does it mean? An exception is considered to be handled when it gets "caught" in our familiar catch clause. When an exception is thrown, first it will search for exception handling in the code where it happened, and, if none are found, it will go to the calling context of the method in which it is enclosed and so on until an exception handler is found or the program will terminate.

One nice piece that I like, from Uncle Bob again, is that the try-catch-finally blocks define a scope within the program. And besides the lexical scope, we should think of its _conceptual scope, and treat the try block as a transaction_. What should we do if something goes wrong? How do we make sure to leave our program in a valid state? Do not ignore exceptions! I am guessing many hours of unhappiness for programmers were caused by silent exceptions. The catch and finally block are the place where you will do your cleaning up. Make sure you wait until you have all the information to handle the exception properly. This can be tied to the _throw early-catch late principle_. We throw early so we don't make operations that we have to revert later because of the exception and we catch late in order to have all the information to correctly handle the exception. And, by the way, when you catch exceptions, only log when you resolve them, or else a single exception event would cause clutter in your logs. Finally, for exception handling, I personally prefer to _create an error handling service_ that I can use in different parts of my code and take appropriate actions in regards to logging, rethrowing, cleaning resources, etc. It centralizes my error handling behavior, avoids code repetition, and helps me keep a more high-level perspective of how errors are handled in the application.

So now that we have enough context, paradoxes, rules and their exceptions, let's summarize:

  * Try to avoid exceptions. Use the language features and proper design in order to achieve it.
  * Use runtime exceptions, wrap methods with checked exceptions and turn them in at runtime.
  * Try to use standard exceptions.
  * Make your exceptions specific and descriptive.
  * Catch the most specific exception first.
  * Do not catch on Exception.
  * But catch on Exception on the boundaries of your API. Have complete control over what comes out to the world.
  * Create a hierarchy of exceptions that match the layers and functionalities of your application.
  * Throw exceptions at the proper abstraction level. Catch an exception and throw a higher level one as you move from layer to layer.
  * Pass the complete history of exceptions when rethrowing by providing the exception in the constructor of the new one.
  * Think of the try-catch-finally block as a transaction. Make sure you leave your program in a valid state when something goes wrong.
  * Catch exceptions when you can handle it.
  * Never have empty catch clauses.
  * Log an exception when you handle it.
  * Have a global exception handling service and have a strategy on how you handle errors.

That was it! Go on and be exceptional!

[Download Building Reactive Microservices in Java](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031): Asynchronous and Event-Based Application Design. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031).
