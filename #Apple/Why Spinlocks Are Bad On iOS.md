# Why Spinlocks Are Bad On iOS

_Captured: 2015-12-25 at 00:24 from [engineering.postmates.com](http://engineering.postmates.com/Spinlocks-Considered-Harmful-On-iOS/)_

![](http://engineering.postmates.com/images/blog-header.jpg)

Spinlocks are a pretty simple synchronization construct, right? In this post we'll explain what spinlocks are, how they work, and why they're **fundamentally unsafe** on iOS.

But first, we're also announcing the release of a new open-source Swift/Obj-C library that provides a more modern API on top of KVO called [PMKVObserver](https://github.com/postmates/PMKVObserver). This library is MIT licensed, supports iOS, OS X, watchOS, and tvOS, is fully thread-safe (including canceling concurrently from several threads at once), automatically unregisters itself when the observed object deallocates, and uses strong typing in the Swift API. If you write Swift or Obj-C apps and use KVO, I encourage you to [check out the library](https://github.com/postmates/PMKVObserver), see the sample code, and maybe even use it in your app.

You may be wondering what this announcement has to do with spinlocks. Well, two days before releasing the library, I [rewrote it to not use spinlocks](https://github.com/postmates/PMKVObserver/commit/eb770becf9c5dfb31b91a42924bd90830911c0d4) after learning the very things I'm going to be talking about.

## Spinlocks: What are they?

For those who don't know, a [spinlock](https://en.wikipedia.org/wiki/Spinlock) is a lock that causes the acquiring thread to wait in a loop, or "spin", checking the lock repeatedly until it becomes available. Most locks cause the acquiring thread to sleep if the lock is unavailable, and the act of releasing a lock wakes up one of the sleeping threads. That's appropriate in many cases, but if the critical section that the lock protects is particularly small and is strictly CPU-bound, the overhead of a regular lock is pretty significant. But a spinlock can be implemented with a single bit and without any special support in the OS or threading library, all that's required for a spinlock is the basic atomic compare-and-swap operation.

Using C11, you can implement a Spinlock using a single `atomic_flag` variable as follows:
    
    
    // Declare the spinlock
    static atomic_flag spinlock = ATOMIC_FLAG_INIT;
    
    void doSomethingWithLock() {
        // Take the spinlock by setting the flag to true
        while (atomic_flag_test_and_set_explicit(&spinlock, memory_order_acquire)) {
            // Flag was already set; loop and keep trying until it wasn't set
        }
    
        // Perform your work here
    
        // Release the spinlock
        atomic_flag_clear_explicit(&spinlock, memory_order_release);
    }
    

OS X and iOS also provide a type called `OSSpinLock` in `<libkern/OSAtomic.h>` that is used in a similar fashion.

## Spinlock performance

When conditions are good, spinlocks beat every other synchronization technique. This is because they're just two simple atomic operations. The problem with spinlocks is if the thread yields while the lock is held, then that can cause any other thread that wants the lock to waste a lot of time spinning. If the critical section is small enough it's unlikely that the thread will yield with the lock held, but even unlikely events happen sometimes. And if no other thread wants the lock then there's no problem. But if another thread does want the lock, it has to wait until the thread scheduler gives time back to the thread that holds the lock. This is particularly problematic on a single-core system where only one thread can execute at once, because the thread with the lock can't run until the spinning thread exhausts its quantum, or alloted time.

There are tricks to minimize this problem, such as counting the number of times you loop trying to take the lock, and deliberately yielding back to the scheduler after enough iterations. `OSSpinLock` implements some of these back-off strategies. And in most cases it works well enough, even protecting against most priority inversions.

## Priority inversions? What's that?

A priority inversion is when a high-priority thread is blocked on a lock that's held by a low-priority thread, or waiting for the results of the low-priority thread's computation. With normal locks, this is a problem simply because the high-priority thread may have to wait a relatively long time for the low-priority thread to finish doing its work, because the low-priority thread is running at that low priority and therefore won't be scheduled as often. But with spinlocks this is an especially bad problem because the high-priority thread is actually spinning while it waits, and any time a thread is spinning on the lock it's using up execution time that could otherwise have been given to another thread such as the one that holds the lock.

Back-off strategies like what `OSSpinLock` implements can mitigate this problem, by yielding after a set number of iterations so as to not waste too much time spinning when the thread that holds the lock isn't making progress. Dispatch queues and pthread mutexes also handle this automatically by raising the priority of the thread that owns the lock or the priority of the queue when a higher-priority thread is blocked on it, although it's worth noting that semaphores (e.g. `dispatch_semaphore_t`) do _not_ do this as semaphores don't know which threads are performing the work that will lead to signaling the semaphore.

## Thread scheduling and Quality Of Service

Traditionally, OS X (and iOS) has used a [multilevel feedback queue](https://en.wikipedia.org/wiki/Multilevel_feedback_queue) as its thread scheduler. The way this works, roughly, is that it executes threads starting with the highest priority first, and as threads exhaust their quantum (alloted time), they're demoted to the next lower priority. Threads that yield their time back to the scheduler (e.g. because they're blocking on I/O or on a lock, or waiting for an event) can be promoted back to a higher priority. This algorithm means that high-priority threads run more often, but eventually (as long as there aren't a constant stream of new high-priority threads being created) even the lowest-priority thread is given a chance to execute.

More recently, the kernel was upgraded with a concept called [Quality Of Service](https://developer.apple.com/library/ios/documentation/Performance/Conceptual/EnergyGuide-iOS/PrioritizeWorkWithQoS.html) (or QOS). QOS allows you to categorize work being done by various APIs, such as `NSOperation`, `NSThread`, dispatch queues, and pthreads. This is basically another form of thread priority, except it's separated into separate QOS classifications instead of just being a number. For example, the highest QOS is `QOS_CLASS_USER_INTERACTIVE`, which is for work that interacts with the user or operates on the main thread.

## The problem with spinlocks on iOS

Now to the actual problem at hand. To the surprise of practically everybody, it turns out that [spinlocks are illegal on iOS](https://lists.swift.org/pipermail/swift-dev/Week-of-Mon-20151214/000321.html). The reason for this comes back to the thread scheduler and QOS. You remember how I said low-priority threads will eventually execute? [That's no longer true with QOS](https://lists.swift.org/pipermail/swift-dev/Week-of-Mon-20151214/000372.html). More specifically, threads in a higher QOS class will never decay to a lower QOS class, and the scheduler will always prioritize runnable threads in a given QOS class before threads in lower classes. And since threads spinning on a spinlock are always runnable, this means that if there's enough high-QOS threads waiting on a lock held by a lower-QOS thread, the thread that owns the lock will _never execute_.

> This is not a theoretical problem. libobjc saw dozens of livelocks against its internal spinlocks until we stopped using OSSpinLock. 

This problem affects iOS, and apparently also affects [the new fanless MacBooks](https://twitter.com/Catfish_Man/status/676851988596809728). And there's no good solution (that third-party code can use). The only solution that guarantees progress is to use unbounded back-off, where the threads waiting on the lock suspend themselves for longer and longer, but this leads to a case where high-priority threads can be blocked for tens of seconds depending on system load.

The Obj-C runtime switched to a handoff lock algorithm, where the spinlock is the size of a word and the owning thread actually stores its thread ID in the lock. Threads that block on the lock can then temporarily donate their priority to the thread that owns the lock, which fixes the priority inversion. There's potential issues when multiple locks are involved, but in practice it works. The only problem with this solution is [it relies on private API](https://lists.swift.org/pipermail/swift-dev/Week-of-Mon-20151214/000389.html), and the spinlock implementation itself isn't public, so there's no way for third-party code to use these locks.

## So what can we do about this?

The simplest answer is to just stop using spinlocks. Every spinlock can be replaced with a "real" lock (such as a pthread mutex), or with a serial dispatch queue. There's more overhead to these constructs, but they do work. If you look back at that [PMKVObserver commit](https://github.com/postmates/PMKVObserver/commit/eb770becf9c5dfb31b91a42924bd90830911c0d4), you can see that I replaced two spinlocks with a mutex and an atomic reference count.

Alternatively, you can keep using spinlocks if you can guarantee that all threads run at the same priority, as there's no risk of priority inversion. You can also use spinlocks if you're comfortable running the slight risk of a livelock; if you know you're not doing a lot of high-priority stuff in your application, the risk may be sufficiently small. If you do decide to run this risk, you should at least make sure the critical section of the lock is as small as possible; if you're just setting a single ivar, you're unlikely to yield while the lock is held, but if you're doing something more complicated then your risk goes up significantly.

_Kevin Ballard ([@eridius](https://twitter.com/eridius)) is an iOS Developer at Postmates._
