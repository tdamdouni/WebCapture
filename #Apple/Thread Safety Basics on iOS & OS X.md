# Thread Safety Basics on iOS/OS X

_Captured: 2015-11-06 at 09:42 from [blog.parse.com](http://blog.parse.com/learn/thread-safety-basics-on-iosos-x/)_

Dealing with concurrency and reentrancy is one of the more difficult challenges any library will inevitably face as it grows. Here at Parse, we have put a large effort towards ensuring that anything you do with our SDKs is thread-safe, without letting performance suffer.

In this article, we'll go over some of the basic concepts about about how the you can handle concurrency and race conditions in a clean, concise, safe, way.

First, before we get into the gritty details, let's get a few definitions out of the way.

  * **Thread: **A context of execution of a program, scheduled for running by the Operating System. Any number of these can exist at once.
  * **Concurrency: **A state of execution in which multiple threads are performing tasks on the same shared resource.
  * **Reentrancy: **A state of execution in which a function re-enters itself, either via explicit recursion, software/hardware interrupt, or other methods.
  * **Atomicity: **A property of an operation such that it is guaranteed to finish or fail, but can never end up or produce an intermediate state, or an invalid state.
  * **Thread Safe: **A function is thread safe if, and only if, invalid state cannot be caused, or observed, by entering a state of concurrency.
  * **Re-entrant: **A function is re-entrant if, and only if, invalid state cannot be caused, or observed, by entering a state of reentrancy.

**The first thing that should always be discussed when talking about thread safety is that thread safety is inherently hard.** Due to the way that threading, scheduling, garbage collection, cache misses, branch predictions, etc. work, issues with threading can be _very_ difficult to trace down and fix. Given these factors, whenever possible, do not write code that can fail in a multithreaded environment. That can be achieved quite simply, if you follow the following guidelines:

  * Don't have mutable state whenever possible. Copies, copies, copies.
  * Yes, your code has a race condition.
  * Prefer thread-local storage over global state when it makes sense.
  * When in doubt, use a lock.
  * **Yes, your code has a race condition** (even if you think it's impossible).

# Race Conditions

Race conditions. The bane of any multithreaded system. When you don't directly control scheduling (as is what happens in a single thread), how can you ensure that things happen in the order that you expect them to? There is a lot of good advice on the internet about[ how to track down race conditions](http://www.cs.cmu.edu/~nbeckman/papers/race_detection_survey.pdf), but surprisingly little about avoiding them.

Most race conditions are caused by shared mutable state, such as the following:
    
    
    void thread1() {
        _sharedState = 1;
        // Do stuff   
        if (someCondition) {
            _sharedState = 0;
        }
        // Do stuff
        _sharedState = 1;
    }
    
    void thread2() {
        // Do stuff
        if (_sharedState == 0) {
            _sharedState = 1;
        }
        // Do stuff
    }

If thread 1's `someCondition` evaluates to `true`, will _sharedState be 0 or 1? That depends on the state of thread 2, and whether or not it has evaluated its conditional yet.

Mutable state does not necessarily mean variables, either. State can be modified outside the realm of your application, including the file system, network, syscalls, and more.

## States and Copying

One of the best ways to avoid mutable state is to have strict guidelines on how you manage state as a whole. In general, at Parse, we adhere to three rules:

  1. Separate your state from the code that modifies it. This allows you to have a clear separation of concerns between your reading and mutation, and allows you to better reason about threading in your code.
  2. Pass **anything** mutable by copy. Passing by reference creates the possibility of concurrent resource modification, and you will need to do some form of synchronization to ensure this doesn't happen.
  3. When in doubt, just lock. It may be slower, but it's better than having a 1-in-1000 race condition that breaks your app.

Remember that global state is bad, and you should avoid it at all costs (yes, this includes singletons). At Parse, we prefer to use dependency injection over things like singletons (e.g. `-initWithObjectController:` vs. `[ObjectController sharedController]`), as it helps us keep track of our usages of objects, as well as strengthen our reasoning about threading, and use thread-local stoage vs. global if it makes sense.

As mentioned above, mutable states (as well as global state) make concurrency significantly harder to cope with than it should be. Avoid it at all costs.

## Atomicity

As stated above, atomicity is defined as follows:

  * A property of an operation such that it is guaranteed to finish or fail, but can never end up or produce an intermediate state, or an invalid state.

That's great, albeit a bit cryptic. What does that mean in practice, though?

Imagine you have a counter variable named `y`, which needs to be updated from multiple threads. A naive solution to this problem would be to directly increment, such as `y++`. However, there's a critical flaw with this operation. What happens if two threads try to increment `y` at the same time? You end up in a non-deterministic state, and you're forced to find another solution.

One solution might be to stick a lock around your counter variable, but that would decrease performance significantly. Another solution (depending on the situation) might be to use a separate counter on a per-thread basis, but that increases memory usage and cognitive load of your program.

There is, however, a better way. Using some processor specific instructions, abstracted away using the functions provide `<libkern/OSAtomic.h>`, which guarantees that all operations performed on an address are properly synchronized, and are enforced by the processor, not by the operating system. These are the basis for creating lock-free data structures, very useful entities, but well outside the scope of this blog post.

As a general rule though, if every operation you perform on a specified address is atomic, no reads to that address can put your application in an invalid state. These primitives, then, when combined with atomic properties, can ensure than any single field cannot be in an invalid state. Note that the object as a whole may still be able to be in an invalid state, as every atomic operation you perform is entirely independent of all other atomic operations that are being executed on other addresses.

## Locking

When atomics won't serve your purpose, you do have the more 'traditional' method of thread safety in locking. Locking exists in many forms, with many contradicting opinions on what kind of lock is the 'best' for a situation. We will discuss a few of the options available by default on iOS/OS X.

Before we discuss _how_ to lock, lets talk about _when_to lock. One of the largest mistakes that is made when developing 'thread-safe' code, is overaggressive use of locking. Yes, if you lock every single possible method call to an object, there's no possible chance of a race condition. However, you can do significantly better if you can isolate the sections where you have access to mutable state.

Now, to demonstrate several kinds of locks, let's begin with an example:
    
    
    - (NSInteger)foo {
        return _foo;
    }
    
    - (void)incrementFooBy:(NSInteger)x {
        _foo += x;
    }

This simple function, while appearing completely harmless, is neither thread-safe or re-entrant. In fact, there are multiple issues with this snippet of code:

  * In the concurrent use-case, the operator `*=` is not atomic. This means that if two threads call `incrementFooBy:` at exactly the same time, we will end up with an intermediate value that may not represent any valid state at all.
  * In the re-entrant use-case, if an interrupt is raised between the multiplication and the assignment, we have a very similar problem to above, where we may end up in a strange intermediate issue.

Hmm. So this code doesn't work. How can we make it better?

## Approach 1: `@synchronized`
    
    
    - (NSInteger)foo {
        @synchronized (self) {
            return _foo;
        }
    }
    
    - (void)incrementFooBy:(NSInteger)x {
        @synchronized (self) {
            _foo += x;
        }
    }

This solves both the concurrency and the re-entrancy problem, but it provides issues of its own as well. The first, and most obvious issue, is that by synchronizing on `self`, we restrict any other thread from synchronizing on `self`, which can be very bad if you over-use this.

The second issue with this solution is performance of `@synchronized` is [well known](http://perpendiculo.us/2009/09/synchronized-nslock-pthread-osspinlock-showdown-done-right/) to be [dismal at best](http://cocoasamurai.blogspot.com/2008/04/osspinlock-lock-showdown-posix-locks-vs.html). However, it still is the simplest way to create a lock in Objective-C, and as such it is still used widely. That doesn't mean that better options do not exist, however, which brings us to...

## Approach 2: Serial dispatch queue

At some point in your Cocoa/Cocoa Touch programming career, you probably have touched one of these, even if it is just the main queue. A dispatch queue is a list of tasks that are executed in a linear fashion, by whichever threads are available from the OS. Dispatch queues have a few unique properties however, which make them more than suitable for synchronization.
    
    
    @implementation SomeObject() {
       dispatch_queue_t _barQueue; // = dispatch_queue_create("com.parse.example.queue", DISPATCH_QUEUE_SERIAL);
    }
    
    - (NSInteger)foo {
        __block NSInteger result = 0;
        dispatch_sync(_barQueue, ^{
            result = _foo;
        });
        return result;
    }
    
    - (void)incrementFooBy:(NSInteger) x {
        dispatch_sync(_barQueue, ^{
            _foo += x;
        });
    }
    
    @end

  * All dispatch queues, aside from the main queue, will ignore signal interrupts, making sources of reentrancy significantly more logical.
  * Dispatch queues, via their QoS system, are immune to [Priority Inversion](https://en.wikipedia.org/wiki/Priority_inversion).
  * Can do deferred execution via dispatch_async, without breaking synchronization model.

However, there are some downsides to using dispatch queues as your source of mutual exclusion, including:

  * All dispatch queues are non-reentrant, meaning you will deadlock if you attempt to dispatch_sync on the current queue.
  * Dispatch queue objects are fairly heavy-weight, clocking in at just about 128 bytes (plus extra space for some internal pointers). Compared to a simple `OSSpinLock`, which is only 4 bytes.
  * Returning values from a `dispatch_sync` block gets a little ugly at times, due to requiring a `__block` variable.
  * Exceptions do not play nicely with dispatch queues.

These tradeoffs are well worth the performance benefits in most scenarios, and is used widely throughout the SDK.

## Approach 3: Concurrent dispatch queue

Approach #2 is good, in scenarios where read-write balance is even (e.g. same number of gets as sets). However, in the real world, this is very rarely the case. Frequently, you will have logic which includes reading from many times, but only writing occasionally.

Dispatch has built in support for these so-called read-write locks, in the form of Concurrent Queues. These work like most other queues, however, they attempt to let as many executors in as possible, and only get exclusive access when you place a `dispatch_barrier`'d block onto the queue. This allows that queue to run solely in the context of the concurrent queue, and helps to speed our uncontested use-case up significantly.
    
    
    @implementation SomeObject() {
        dispatch_queue_t _barQueue; // = dispatch_queue_create("com.parse.example.queue", DISPATCH_QUEUE_CONCURRENT);
    }
    
    - (NSInteger)foo {
        __block NSInteger result = 0;
        dispatch_sync(_barQueue, ^{
            result = _foo;
        });
        return result;
    }
    
    - (void)incrementFooBy:(NSInteger)x {
        dispatch_barrier_sync(_barQueue, ^{
            _foo += x;
        });
    }
    
    @end

As you can see, another advantage of the above code is that it makes a clear contrast between what functions update the instance variables, and which ones don't. It is important to note the performance overhead of a concurrent dispatch queue versus a serial dispatch queue. In the contested case (e.g. lots of `dispatch_barrier_sync` calls), a concurrent dispatch queue will spend a lot more time spinning on its internal lock vs. a serial queue, though it will probably only be noticeable in benchmarks.

## Conclusion

Here at Parse, we strive on creating the best APIs possible, with the best threading support possible as well. We do this using a number of mechanisms inside the SDK, which we think are good best practices for any mobile project. Stay tuned in the coming weeks for more posts like this! We'll be sharing more on our test philosophies, learnings, and more.
