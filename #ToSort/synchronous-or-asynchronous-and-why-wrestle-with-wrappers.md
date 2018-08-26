# Synchronous or Asynchronous, and Why Wrestle With Wrappers?

_Captured: 2018-04-26 at 20:28 from [dzone.com](https://dzone.com/articles/synchronous-or-asynchronous-and-why-wrestle-with-wrappers?edition=377192&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-26)_

Have you ever wondered why you have to wrestle with `CompletableFutures` instead of "just writing code" like in the old days? Is it only for performance? Or maybe it's just a fashion? Let's find out!

![](https://cdn-images-1.medium.com/max/1600/1*_Bi5vv6sxelS7qEar-GUdQ.jpeg)

> _   
_

Writing synchronous, blocking, procedural code **seems** simple. The business logic is expressed as a sequence of steps. When there is a need to do I/O, you synchronously call a blocking I/O method and further process the result. Calling a method which adds two numbers looks the same as calling a method which sends an HTTP request.

But since some time, asynchronous programming is gaining more and more popularity. We are encouraged to write code in terms of `Future`s, `CompletableFuture`s, `Task`s or `Deferred` values. This has very solid performance reasons: code written in a blocking way doesn't scale (at least on the JVM), and each concurrent invocation of the business logic requires a new thread. And threads are an expensive resource! Hence, synchronous applications quickly reach the limits of the number of threads that can concurrently operate.

On the other hand, code written in an asynchronous way can run using far less threads. In the asynchronous setup, concurrent invocations of the business logic are interleaved with each other, making threads available whenever there's a need to wait for the results of an I/O operation (hence also the name: non-blocking I/O). That way we can serve many more users, requests or process data faster, just by utilizing the expensive OS-level resources -- threads -- in a more efficient way.

But is performance the only reason to program in an asynchronous style, rather than in the seemingly convenient synchronous one? Or does the asynchronous style provide some other **fundamental** advantages?

If it's all about performance, then maybe we are just solving the wrong problem, and constructing an elaborate work-around because threads are expensive? Maybe we should concentrate our efforts on a better threading abstraction on the VM level, for example green threads?

> "Green threads" aren't bound to OS-level threads; many green threads might run on a single OS-level thread, hence providing much better utilization of that resource. 

## **Callbacks vs. Wrappers**

There are two main styles of writing asynchronous code. The first one is based on callbacks, the other on "wrappers" (or "containers" of a single value). Let's do away with callbacks upfront and then concentrate on the second approach.

In the callback-based approach, each method which should be run asynchronously accepts an additional `callback` parameter. The callback accepts the results of the asynchronous operation and is the code that should be run after the operation completes. This is also known as a **continuation**. When there are multiple operations that should be run asynchronously we get a stack of callbacks (often with increasing indentation). This ever-increasing nesting pyramid is only one of the problems with the callback approach and is especially well known to node.js programmers, who [coined the "callback hell" term](http://callbackhell.com/) to describe their experiences.

An alternative to callbacks is using "wrapper" objects which represent an asynchronous operation. These wrappers have various names in various platforms and libraries, but you've probably came across Java's `CompletableFuture`, Scala's `Future` or `Task `(in many flavors), Kotlin's `Deferred` or Javascript's `Promise`s. The idea of all these constructs is the same: the asynchronous operation is **reified as a value** in the host language. This value represents a computation which will eventually be done and **wraps the result of that computation**.

> As a side-note, there are some important differences between the various implementations of the concept as well: in general, `Future`-like constructs represent a **running** computation, while e.g. a `Task` in Scala represents a **description** of how to run a computation; such a description needs to be explicitly run at some point, possibly many times. 

These wrappers usually come with a number of combinators which allow combining multiple wrappers into a single one. But the ability to "grab" a computation's results and treat it as a value is the determining factor why the wrappers are preferred over callbacks. Going forward, we'll concentrate on that style only. The JavaScript community seems to be following the same route, [adopting promises](https://developers.google.com/web/fundamentals/primers/promises). In typed languages, generics are used to represent wrapped values, e.g. `CompletableFuture<Integer>` is the type of a computation which will eventually return an `Integer`.

To compare these styles in practice, here you can find three short snippets of the same code written using the synchronous, async-callback and async-wrapper styles. All of them dispatch three I/O operations: fetching data from a database, running a HTTP query and sending an email. We'll be omitting implementations where they are not relevant. The three snippets will use the following `User` class:

The synchronous version uses blocking methods for I/O operations: `fetchFromDb`, `sendHttpGet` and `sendEmail`. The business logic is expressed as a series of statements:
    
    
        <T> T fetchFromDb(Class<T> entityClass, long id) { return null; }
    
    
            User user = fetchFromDb(User.class, 42);
    
    
                "http://profile_service/get/" + user.getProfileId());

In the asynchronous-callbacks version, the I/O operations are no longer blocking. They all return `void` and accept an additional `callback` argument, which is a function consuming whatever is the result of the operation. The business logic also needs to be parametrized with a callback which should be run after it completes:
    
    
        <T> void fetchFromDb(Class<T> entityClass, long id, Consumer<T> callback) { }
    
    
                    user -> sendHttpGet("http://profile_service/get/" + user.getProfileId(),

Finally, in the asynchronous-wrapper version, the signatures change again. There are no additional arguments, but the return type now specifies that the result of the I/O operation will be eventually available in the future:
    
    
        <T> CompletableFuture<T> fetchFromDb(Class<T> entityClass, long id) { return null; }
    
    
        CompletableFuture<String> sendHttpGet(String url) { return null; }
    
    
            return fetchFromDb(User.class, 42).thenCompose(user -> {
    
    
                        sendEmail(user.getEmail(), "Your profile is: " + profile));

We'll be using Java in the code examples, but they carry over to other languages such as Kotlin or Scala quite naturally, usually with less code and better syntax.

## **Code as Data**

To go back to the original problem, on one side we have synchronous programming, on the other wrapper-based asynchronous programming. Does the asynchronous approach offer some fundamental advantages over the synchronous one -- apart from performance, which is more of an implementation detail of the current VMs?

As we mentioned before, in the asynchronous-wrapper approach computations are reified as values. Each value wraps the eventual result of the computation.

The idea to represent a running computation or a description of how to run a computation as a regular value is not new and dates back to -- you guessed it -- [LISP](https://blogs.mulesoft.com/dev/news-dev/code-is-data-data-is-code/)! However, that idea is very powerful, and **does** bring significant new possibilities to how we code. We just need to keep in mind that the `Future` on which we operate **is an ordinary value** -- one that can be stored in fields, passed to methods, returned as a return value, combined with other values of the same type, stored in collections, etc.

For a start let's consider a simple example of running two tasks in parallel and combining their results. Let's say we want to fetch the user's profile from one API call and the user's friends from another API call. In the synchronous setting we would either need to start two threads by hand, or -- which is a better solution -- use a thread pool. Having such a thread pool (`Executor`s in Java), we can submit both tasks and wait until the results are ready using thread-safe, concurrent data structures:

That's quite a lot of code and quite a lot of threading machinery for such a simple task! How can we make it better? Well, to combine the results of two operations in a convenient way, we need a handle on the asynchronous operations' "future results". Hence we'll either end up reimplementing a future, or we can use an implementation that's already there!

Therefore, let's see how the same method could be implemented using wrappers. As we want to code in the wrapper-based asynchronous style, ideally we'll need libraries which support that. Hence, we are assuming that there's a library which does non-blocking, asynchronous HTTP calls. The method to send the HTTP request will then return a `CompletableFuture` (and such libraries [do exist](https://github.com/AsyncHttpClient/async-http-client)). The only thing left to do is combine the results into a single future:

Note that the result of the computation also is a `CompletableFuture`; in that way, once we start using wrapper-based asynchronous programming, it's often "contagious" and spreads through the code base. While there are ways to "force" a future computation into a value in a blocking way, if there's such a need, it is a good idea to let the asynchronicity propagate as far as needed.

## **More combinators**

As a more advanced example, consider the task of writing a method which gets a list of publication IDs (as `long`s), looks up their RSS feed addresses in a database and fetches their contents in parallel. We'd like both the database lookups and the RSS feed fetching to be parallelized. In the synchronous setup, again that is not an easy task. Without utilizing `Future`s, the solution would not only be resource-heavy (if we want all requests to run in parallel, we need as many OS-level threads as URLs on the input list!), but also hard to read and error-prone, as concurrency would need to be managed **explicitly **and on a very low level: using locks, semaphores, atomic references, etc..

When writing the same method in an asynchronous way using wrappers, we can simply create a value representing the computation for each input publication ID. Then, once each database lookup is complete, sequence another asynchronous operation (fetching the RSS feed content). Finally, we can use one of the basic library functions which converts a `List<CompletableFuture<String>>` into a `CompletableFuture<List<String>>`:

Nice and (relatively) simple! We can improve even further by using a more advanced programming language. Thanks to Scala's higher-order functions, type inference and for comprehensions, the above becomes:

In general, wrapper-based asynchronous programming is great when processing data in parallel where I/O might be involved in some of the steps. The freedom to treat computations as values, pass them around, store in collections is truly liberating. The next step is manipulating unbounded streams, which is also transformational to the programming style, but out of scope for this article. Check out [ReactiveX](http://reactivex.io/), [akka-streams](https://doc.akka.io/docs/akka/2.5/stream/stream-quickstart.html) / [fs2](https://github.com/functional-streams-for-scala/fs2) in Scala and [Channels](https://github.com/Kotlin/kotlinx.coroutines/blob/master/coroutines-guide.md#channels) in Kotlin if you'd like to find out more.

## **The Power of Wrappers**

When using the wrapper representation, manipulating the wrapped data is very approachable. That is thanks to methods familiar from collection libraries, such as `map` and `flatMap`.

Because the computation is a value -- an ordinary object -- we can manipulate it by calling its methods. This allows us to influence how that computation is done and in some cases cancel it. And that's just the start of what's possible. Wrapper types usually offer a much richer set of combinators. Just look at [Monix's ](https://monix.io/api/3.0/monix/eval/Task.html)`[Task](https://monix.io/api/3.0/monix/eval/Task.html)`. You can find methods for scheduling work on different thread pools, creating async boundaries, error handling, restarts, memoization, timeouts, reactive streams integration and more.

There's also a number of methods operating on collections of asynchronous values. The list of futures to future of list conversion is just one special case of a general operation called `sequence`. Other similar operations include evaluating a collection of asynchronous computations into a stream where items are available as soon as the computation is done (potentially out-of-order, the first computation done is the first in the stream), or racing two asynchronous operations and taking only the first available value (for example, running a query against two replicas of a database, and returning the results of the faster one).

Representing code as data allows us also to **defer a number of hard threading decisions** as late as possible. It's quite possible that such decisions are better made at the use-site than at the declaration site. This might include choosing a specific thread pool to run the asynchronous operations on. Or, choosing a batching strategy for evaluating the wrapped asynchronous operations, so that there's not too much context switches (which might impact performance).

Finally, the choice when to start the computation can also be deferred -- as mentioned before, while `Future`-like constructs represent a **computation in progress**, `Task`-like constructs are a description of a computation which might be started on demand (**lazily**). When this takes place is up to the caller. Pushing the responsibility for such hard choices often leads to more reusable (as everybody can make the decisions fitting their use-case) and readable code (as there's less responsibilities when declaring the asynchronous task).

Deferring hard threading decisions is one less responsibility of the method in question. And the less responsibilities, the better.

## **Not All Roses**

Things are not always as beautiful as in the previous example. Let's consider a "business" method with a complex control flow. For example, what would a method which accepts an ID of a user, looks the user up in the database and if the user exists, sends an API call and optionally a notification email, look like in both settings?

With the synchronous approach, this business logic can be represented in a very readable way:

However, when dealing with an asynchronous, wrapper-based codebase, things get more complex:

The problem here is that even though the combinators used to combine the wrapped values are rich and flexible -- we are still constrained by the base language. All of the combinators are methods on the wrapper object and must leverage whatever language features are available. There's only so much flexibility. The reduced syntactic footprint of Kotlin and Scala do help in this example, but still it's not as readable as the original.

## **Types, Types, More Types!**

However, there **are** some good sides to the problem described above. To make complex control flow logic readable when using the asynchronous-wrapper style, we **have** to separate the various parts into small methods with descriptive names; and because of the added syntactic overhead, we might be inclined to do this more diligently than in the synchronous case. Some of these methods will operate on `Future`s (assuming that's our wrapper type), some will be **pure**.

> A **pure method** is one where the output depends only on the input parameters (like a mathematical function). Such a method cannot perform I/O, change or depend on shared mutable state. It's always safe to call in any context. 

And this brings us to another advantage of the wrapper approach: just by looking at a method's signature, it is clearly visible if the method might be doing I/O or not. A pure method, which just does some computations, won't have a `Future` or `Deferred` in its signature. However, if the resulting type is a `CompletableFuture<String>`, there's high probability that there's **some I/O**involved. And this is a big bonus to readability.

This distinction between pure and possibly side-effecting (involving I/O) methods is not visible in the synchronous approach: as mentioned in the beginning, all method calls look the same. And this in fact is a huge disadvantage: making sure that side-effects are contained and clearly visible is not only a huge boost to code readability, but significantly improves its correctness.

You probably know these hard-to-find, elusive bugs, which after hours of debugging turned out to be caused by an unexpected mutation of some shared state. Containing side effects helps to reduce exactly these kinds of bugs.

## **Hitting the Middle Ground With Coroutines**

There is some middle-ground between the synchronous approach and purely wrapper-based one, which helps to solve the problem with complex control flows: coroutines. Coroutines, as they are currently implemented in JVM-based languages, allow writing asynchronous code in a sequential, synchronous-like syntax, however only in a **limited scope**.

As we've seen on the earlier examples, it is often very convenient to combine the results of asynchronous computations by calling methods on the wrappers which represents them (e.g. `CompletableFuture.thenCompose`). However, in some cases the imperative, **step-by-step style** of writing the flow of a computation is just better from a readability standpoint (as we've seen on the last example). That's where coroutines are most useful.

The most interesting coroutines implementation currently seems to be the [one in Kotlin](https://kotlinlang.org/docs/reference/coroutines.html), as it unifies Go-style [channels](https://gobyexample.com/channels), sequence generators and [async/await constructs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) similar to those found in JavaScript.

With Kotlin's coroutines, the complex control flow example from before could be rewritten as:

Which is almost identical to the synchronous version! Behind the scenes, the compiler transforms `suspendable` methods and any code in the `async` block into a form where an additional `Continuation<T>` parameter is passed around -- similarly as with the callbacks approach described in the beginning. However, here we almost never deal with the continuations explicitly, all that is done by the compiler.

As mentioned, coroutines in Kotlin have a number of possibilities: there are built-in implementations for communication channels between two coroutines running concurrently, streaming primitives, actors support etc., all described in the [kotlinx.coroutines guide](https://github.com/Kotlin/kotlinx.coroutines/blob/master/coroutines-guide.md). Very often, these constructs are a blend of the wrapper-based approach with a convenient way to create the wrappers. For example, `async`/`await` coroutine builders create `Deferred`values, which are Kotlin's take on `Future`s. Kotlin's channels and pipelines correspond to RxJava's `Observable`s or fs2's `Stream`s, etc.

Coroutines have their limitations as well. First of all, the blocking-like syntax can only be used in a limited, clearly defined scope. Even inside such a block, you can't call the "blocking" methods everywhere -- it will work in a conditional or a for loop, but not inside an arbitrary lambda. Secondly, any **really** blocking calls (e.g. a blocking I/O call) will remain blocking -- there's no magic here. If you want to use the asynchronous features of subroutines, you need libraries which are appropriately adapted and either expose `suspendable` functions or use the kotlinx.coroutines concurrency primitives. Finally, while it is visible from type signatures which methods are suspendable or use e.g. channels, there's also a number of methods of running a coroutine in a blocking way, which isn't visible from the method signature. The same is possible with `Future`s or `Task`s, but most commonly futures propagate all the way to the program's edges.

If you are using Java, you can also use coroutines (called `Fiber`s), through [the Quasar project](http://docs.paralleluniverse.co/quasar/). Instead of compiler support, Quasar uses bytecode instrumentation to convert code to a non-blocking version. In Scala, there's [scala-async](https://github.com/scala/scala-async), which use macros to convert code which uses `async`/`await` in combination with `Future`s to the non-blocking version. For other wrappers, there are the [monadless](https://github.com/monadless/monadless) and [effectful](https://github.com/pelotom/effectful) projects. These solutions do their job well, but are not standard in the language. (The approach taken by these libraries can be taken even further, e.g. see this talk on [automatic parallelisation and batching](https://skillsmatter.com/skillscasts/11182-automatic-parallelisation-and-batching-of-scala-code) of I/O requests.) Finally, there's an ongoing effort to add fibers and coroutines/continuations to Java in [Project Loom](http://cr.openjdk.java.net/~rpressler/loom/Loom-Proposal.html).

Summing up, coroutines are great for **locally** expressing complex control flows involving asynchronous operations.

## **Wrapping Up on Wrappers**

To sum up: asynchronous programming using wrappers **does add significant value** over the synchronous style. It has two main benefits, in addition to better performance and resource utilization on current VM implementations:

  1. allows treating computations as values, which is very handy when processing data in parallel in the presence of I/O
  2. (some) side effects are contained and I/O is clearly demarcated, which increases readability and can improve correctness

`Future`\- or `Task`-based approaches are a good default when starting a new project. **In today's data-intensive world, it's very probable that you will need to run multiple asynchronous operations in parallel.** Hence, an approach which makes these operations readable and easy to reason about, without sacrificing performance is crucial.

There are some downsides in the presence of complex control flows, but these often can be either abstracted and delegated to library methods, or solved by using coroutines either in Java, Kotlin or [Scala](https://softwaremill.com/?utm_source=dzone&utm_medium=post). There's always some syntactical overhead (which impacts readability) comparing to the purely synchronous style, but in the end is not a show-stopper.

Even though synchronous programming might seem familiar and simple, in the long run it turns out more complex, as concurrency needs to be handled explicitly with a lot of boilerplate, error-prone code. While coding using contained, controlled side effects can take getting used to, it pays off! When choosing the implementation language for a project, support for wrappers and container-like types can be an important factor.

Various languages offer various features when it comes to supporting writing asynchronous code using wrappers. As mentioned, Kotlin has [first-class support for coroutines](https://kotlinlang.org/docs/reference/coroutines.html), which greatly simplify expressing complex control flows. Scala has support for [higher-kinded types](https://typelevel.org/blog/2016/08/21/hkts-moving-forward.html) and [typeclasses](https://typelevel.org/cats/typeclasses.html), which allow abstracting over a specific wrapper type and implementing a number of wrapper functionalities in a generic way. But even Java invests in making working with wrappers easier, with the addition of lambdas and the `CompletableFuture` class. Future is bright!
