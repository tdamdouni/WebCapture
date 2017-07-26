# Functional Programming Is Not What You (Probably) Think

_Captured: 2017-01-18 at 17:22 from [dzone.com](https://dzone.com/articles/functional-programming-is-not-what-you-probably-th?edition=262903&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-17)_

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

After seeing many of the comments from [another article attempting to explain what FP (Functional Programming) is about](https://dzone.com/articles/explaining-functional-programming), I thought I would take another attempt at my own explanation. First, just a little background about me: I am currently a Quality Engineer at Red Hat, and I have been writing Clojure off and on (mostly off) since 2010. I have just recently begun a journey learning [PureScript ](http://www.purescript.org)which is (sort of) a dialect of Haskell that targets a JavaScript engine. My goal in this article is to give yet another explanation of FP and give at least a notion of the differences between "mostly" FP from pure FP. I welcome any comments, questions, or corrections (especially with regards to pure functional programming, which I am still fairly new at).

## Definition of a Pure Function

So in the previous article mentioned above, the author wanted to convey the notion of what a pure function is: namely, a function which, given the same input, always yields the same output and without any side effects. A side effect can include mutating any variable or affecting the "outside" world (for example writing to a file or stdio). A related but orthogonal concept to a pure function is a total function, which perhaps I'll cover in another article.

It must also be mentioned that technically, a mathematical function is a function of one argument, and it must map to one and only one result. Most pure FP languages take functions which appear to take multiple arguments and convert them to functions of one argument (which returns another function, which takes one arg). This process is called currying. Note that currying is not a technical requirement of a pure function, since we can always curry a function anyhow. Here's an example of currying in JavaScript:
    
    
    let fn = (a, b, c) => {
    
    
          return a / (b - c);
    
    
    console.log(curriedFn(10)(4)(2));
    
    
    let curryfn = a => b => c => a / (b - c)

## The Real Meaning of "Side Effect"

Going over the comments from that article, I realized that one of the big misunderstandings people have about pure functions is the notion of the term "side effect." In colloquial English, a "side effect" is an **unintended** consequence of an action. But in computer science, a side effect is any action that affects or alters the outside world, including the parameters passed to the function. This leads to confusion when an FP advocate says a function is effectful, but someone new to FP says, "But the function's intended behavior is to change the state! So it's not a side effect, just an effect." Problem is, that's not what side effect means from a computer science point of view.

### An Effectful Example

So let's look at a concrete example of an effectful class in Java. Here's some sample Java code:
    
    
                System.out.println(String.format("Warning! Level of %d is too high, attempting to settle...", this.level));
    
    
            System.out.println(String.format("The safe level is now %d", seff.level));

Here, we have a class that has some internal state representing a _level_, which is either normal or too high. If we set the _level_ too high, we can call _makeSafe_ to settle the system back down to normal. Hopefully, this code is relatively straightforward to understand. Obviously, we are keeping track of state internally in the object, and this state is implicitly used and changed by the methods, and thus this code is side effectful.

Why is it side effectful? Isn't my "intention" of the increase function to increase the _level_ field? That's the colloquial interpretation of the term "side effect," but that's not what is meant by FP programming. The side effect here is that relative to the _increase_ function, it has mutated the outside world (the internal field _level_). One may argue that the _level_ field is private, so it is properly encapsulated. But what if I throw in another thread calling _makeSafe_? Or later on, I add another method that changes _level_?

But there's even more effects lurking here. The _state_ is also being mutated by the _determineLevel_ function, and even the System.out.println calls are side effects. Any kind of IO is also a side effect, because you can never be sure if your filesystem, socket, or even console is available. Recall that the definition of a pure function is that given the same input, it must always yield the same answer. With any kind of IO, you can not be guaranteed this. Another thread may have blown away your file (or file system), the console may have been redirected, or a socket may time out for example.

### An Example Without Effects

So how can we make something similar but with pure functions?
    
    
        public Tuple<Integer, String> makeSafe(int currentLevel, int decrementBy, String log) {
    
    
            if (this.determineLevel(currentLevel).equals("too high")) {
    
    
                log = log + String.format("Warning! Level of %d is too high, attempting to settle...\n", currentLevel);
    
    
                return makeSafe(currentLevel - decrementBy, decrementBy, log);
    
    
            log = log + String.format("The safe level is now %d", currentLevel);
    
    
            Tuple<Integer, String> start = new NoSideEffects.Tuple<>(24, "");
    
    
            Tuple<Integer, String> result = noseff.makeSafe(start.first, 5, start.second);

First off, I hope the above example has shown that OOP and FP are not mutually exclusive. For some reason, many people think FP is "against" OOP. What FP is "against" is uncontrolled mutation and side effects (I put "against" in quotes because totally eliminating side effects is impossible). In fact, the astute reader may notice that all of the methods may have been declared static with no loss of computation equivalence.

So what has changed here? Probably the most obvious change is that inner Tuple class. I'll explain that in a moment. The next change that has occurred is that the "state" is being passed to the function explicitly now instead of implicitly as a field inside an object. For example _level_ is no longer a field inside the class, it's now a parameter passed to functions. In fact, we don't even need the _increase_ function anymore. Notice that the _makeSafe_ function uses recursion instead of a while loop. This is quite frequent in functional programming since recursion does not rely upon some kind of hidden inner state which is mutated and affects the control flow of a for or while loop.

Some may argue that this is inefficient and creates more overhead by pushing a new function on the call stack. And depending on the language, they would be correct. Unfortunately, Java does not support Tail Call Optimization (TCO) yet wherein a function which recurses in the tail position (as makeSafe does) is effectively optimized to a loop, but other languages on the JVM can do so such as Scala or Clojure. So depending on your language, do not shy away from recursive solutions to problems and even if your language doesn't support TCO, very often you will know that your problem will be bounded and not suffer a stack overflow.

So, about that Tuple. Notice that in the _makeSafe_ call, instead of calling System.out.println, it is accumulating a logging value on every call. It is only in _main_ where we get to see what happened during the _makeSafe_ function call. The _makeSafe_ returns a Tuple of two elements, the first being an integer value which is our current level, and the second being a string which is the accumulation of our logging results. For those familiar with haskell or purescript, they may recognize this as something similar to the Writer monad.

## The Advantages of Purity

So there is only one place in the NoSideEffect class where we have an effect of any kind, and yet the result is the same. Also, because _makeSafe_ and _determineLevel_ are pure functions, they are immune to time. It does not matter when or what computer you run these functions on, given the same input, they will always yield the same output. If you call these functions in different threads, each thread will operate on different values (which may or may not be what you want...in this case spawning another thread calling makeSafe will not make it get to a safe level twice as fast for example). Also, since there is no IO going on in makeSafe, you never have to worry that your console got redirected or went away (or if I rewrote this to log to a file, that the filesystem went away or someone changed file permissions under your feet).

_"A-ha!! But your main called System.out.println, so your so-called pure program isn't pure!! Got you!!"_

Well, yes :). But I can test makeSafe in isolation, asserting the accumulated log has a certain value. Pure functional programming does not deny side-effectful functions. Perhaps you've heard of Monads before. Well, there are Monads for stateful computations with the ST Monad. However, do not think that Monads are "impure" (or only about IO, or only about state). Perhaps one day I'll write [Yet Another Monad Tutorial](http://dev.stephendiehl.com/hask/#eightfold-path-to-monad-satori). Also, every program's main has to eventually do IO, otherwise there would be no way to know the result of your program. PureScript calls it Eff (for Effect), but basically it says that the program (or function) has some kind of effect. The trick in pure FP is that you have a pure part of computation which is lifted into a larger impure language. Pure FP languages keep track of what parts of your program are pure and which are impure. This is in contrast to mostly FP languages (like Clojure) for example, where you can never be sure if a function is truly pure or not and instead impure functions are usually marked with something in their function names like an exclamation point.
    
    
    (defn inc-by-10-foo! [foo]
    
    
      (swap! foo #(+ % 10)))
    
    
    (let [first10 (inc-by-10-foo! foo)

There are some other considerations here. The _makeSafe_ function is accumulating the _log_ value in a string. In Java, strings are immutable, but if you have a really long running function, it might not be a good idea to store the string in an ever increasing parameter (not to mention all the garbage collection that will be happening). You may want to use a StringBuffer, even though StringBuffers mutate their value. Ultimately, even a pure FP language could potentially throw an out of memory error even on a "pure" function (and pure functions aren't supposed to have side effects like throwing exceptions). Again, pure style FP programming is not about disallowing side effects, it's about keeping track of them and by knowing what and how to compose pure and impure functions together.

## Tracking (Im)Purity

Another common misperception I saw from the comments in the other article was that, ultimately, a function calls a function, which calls a function (etc., etc.) so it's impossible to keep track of whether a function is pure or not. This is not true if you are programming in a pure FP language like Haskell, PureScript, or Idris. The type system ensures that you have a pure function or not. This goes back to the real benefit of pure FP systems, which is in knowing what parts of your program are pure and which are not. This is the hallmark difference IMHO between "mostly" pure FP languages and pure FP languages.

To put it another way, the purity of a function is part of the type information. The parts of your program that are impure need more testing because you don't know if something might fail outside of your control. Even pure FP languages have the need to read files (for config data, for example), write to files (logging data for example), or sometimes to keep track of shared state between multiple processes of execution.

Here's an example of some PureScript code where the purity of the function is clearly marked by its type:
    
    
               -> Eff ( ref :: REF, buffer :: BUFFER, console :: CONSOLE | e) Unit
    
    
      modified <- modifyRef ref \current -> current <> bdata

A reader of this function knows it is impure because the return type is an Eff (which has the effects that it uses a mutable reference, a mutable buffer, and an IO console) and which returns Unit. If you ask, _"Well, what if I simply didn't declare the type to return Eff?"_ then that is impossible. The compiler knows, for example, that since I am using a Ref and a Buffer, those are effectful types. Since the compiler enforces and keeps track of the (im)purity of functions for you, you will know what parts of your program are pure or not.

In fact, PureScript, like Haskell, uses type inference, and had I failed to declare the type of onDataSave, the PureScript compiler would have inferred the type for me and would have indicated what effects it had! Hopefully, this simple example shows you that even pure FP languages can handle the impure and stateful world.

## Pros and Cons of FP

One may ask what benefits programming in this style brings. As I have already mentioned, writing in a pure FP style is:

  * safer because pure functions are automatically thread safe.

  * easier to reason about with pure functions, since you do not need to be aware of any hidden implicit state that can be changed under your feet

  * easier to test pure functions because you do not need mocks to simulate or eliminate side effects

  * helpful to know what functions are impure so it will be more obvious where QA should spend the majority of its testing resources

  * safer to compose (in typed pure FP) because you will know that the output of one function is compatible with the input of another, and there are no locks to order appropriately

This is why I recommend that everyone should learn a pure functional language. Even if you already know a "mostly" FP language like Scala, Clojure, or elixir, I encourage you to try out Haskell or PureScript. It won't be easy, but the effort will be paid back in learning how to solve problems in a different manner.

Are there downsides to FP? Generally speaking, FP can be slower than imperative programming. Mutating a data structure is faster than even persistent data structures. For example, most FP languages use special kinds of data structures that are immutable. If you want to "set" a key to a new value in a persistent map, you call a function that "sets" the key to the new value, and what is returned is a new map with the key set to that value, rather than mutating the map in-place.

This sounds expensive, and it would be if you had to copy every single item in the map. The trick is that you only have to change what is necessary leaving the rest untouched. But even this has logarithmic complexity versus an O(1) operation to mutate a structure in place. Also, as mentioned in the warning about the accumulated log value, you have to be careful thinking what kind of data structure to use when accumulating values. Also, FP often (but not always) uses currying, which is a way to represent functions of multiple arguments as functions that return functions. This can result in extra function call overhead.

_"But I thought you said one of FP's benefit is concurrency? Won't that make FP faster?"_

My not-so-simple answer is... it depends. If your data can be split up without any kind of dependency or sharing, then yes, the speed up will be dramatic. For example, working with matrices will be a breeze--where you can split up the matrices into separate vectors and have them operated on independently. But for other kinds of workloads, waiting for data to "settle down" will cause some contention (as, for example, how STM systems work) as the process has to retry any computations where data has been changed. There will probably be some speed up, but will it be enough to counter the inherent speed advantage that imperative languages have? I'd say you won't really know until you try. Just be mindful that FP doesn't necessarily bring automatic performance advantages. But what it does bring is easier to reason about concurrency, and more importantly, unlike locks or mutexes, concurrent functions in FP are easier to compose with each other (because there are no locks, the ordering of acquiring/releasing locks does not matter which is a big reason you can't compose functions utilizing locks easily).

All things have their pros and cons, but I believe that pure FP is the way to go to solve tomorrow's problems. It makes concurrency and parallelism easier (though still only in comparison to imperative style), the separation of pure and impure functions makes it easier to know where to spend your QA "budget," and pure functions are easier to reason about because there are no hidden implicit factors to think about.

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
