# Intricacies of Multi-Threading in Java

_Captured: 2017-04-18 at 19:53 from [dzone.com](https://dzone.com/articles/intricacies-of-multi-threading-in-java?edition=293881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-18)_

Navigate the Maze of the End-User Experience and pick up this [APM Essential guide](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574).

Multi-threading represents a very intriguing topic, even after years of research and development for high quality, robust, and efficient software. With equal emphasis on hardware improvements and the software that runs on it - we have newer paradigms for parallelism. The most important yet basic concepts are the ones which I present here. I then explain the intricacies of multi-threading in the Java programming language. Some of these are newer features and supported only from the Java Platform Standard Edition 5.0. Let us start with a quick overview and understanding of the core concepts.

## **Thread Concepts in Operating Systems **

**Thread**: A thread is a lightweight process, but it differs from a process in multiple ways. The primary features of a thread are that it creates a sense of execution of processes concurrently; it effectively distributes work and executes a single task, it can be used to schedule and asynchronously execute tasks, it has a more effective context switching mechanism than processes, and it shares the memory space along with other threads yet can have its own storage

**Critical Section**: The critical section of the code is identified as the focus area that will be accessed by multiple threads concurrently and can modify the state. Since there is concurrent modification while sharing a resource, there needs to be controlled access.

**Semaphores: **Semaphore is a resource count that can be used to control access to a shared resource, especially in a multi-threaded environment.

**Mutex**: Mutex is a synchronization construct that allows only one thread a time to use a resource and has ownership associated with it.

**Monitor**: A synchronization construct that allows both mutual exclusion and the ability to wait for a condition to be true.

**Deadlocks**: While accessing the critical section of the code, there might be situations where multiple shared resources are accessed by multiple threads. In such scenarios, when a single thread requires access to a shared resource, it may first need to relieve the currently shared resource that is holding. It may also be true of another concurrently executing thread with respect to the same resources. When such mutual exclusion cannot be achieved, it leads to a Deadlock.

**Deadlock Prevention**: The techniques involved in preventing deadlock conditions from arising constitute Deadlock Prevention.

**Deadlock Handling**: Detection of deadlocks and its removal constitute Deadlock Handling.

**Reentrancy**: When a method or subroutine can be reentered without completing its previous invocation.

![Image title](https://dzone.com/storage/temp/4926946-4.png)

## **Thread Interfaces or Classes or in Java**

**Thread**: The important methods of Thread Class are explained and usage shown in the code samples. The most confusing and common errors even for experienced Java programmers in multi-threading is in understanding locks. I have provided the status of locks on shared objects during each of these methods.

**Runnable**: An alternate way to create a Thread is by implementing this interface. One can create a thread in Java by either of implementing a Runnable interface or extending the Thread class. The programmer will have to override the run() method from this interface to implement logic.

  * _start(), _Lock Status: Can Acquire Locks; This is the method called to **schedule** a thread to run. Once scheduled and a CPU cycle is available the thread actually runs.

  * _run(), _Lock Status: Can Acquire Locks; It is implicitly called by the Thread runtime to start **executing** a thread.

  * _yield(), _Lock Status: **Locks Held; **This method yields or **transfers control** to another thread of equal priority. It does not provide any guarantee regarding which thread it will transfer control to or whether it will at all. The code snippet below also shows how to create a Thread by extending the Thread class. 

  * _sleep(), _Lock Status: **Locks Held; **This method causes the current thread in execution to **pause execution** for a given time period. The time period is specified in milliseconds. It throws an interrupted exception, which needs to be handled by the programmer.

  * _join(), _Lock Status: **Locks Held**; This leads to an execution mode where all threads join at the end of the current thread. In other words, the current thread is **taken to completion** before switching to another thread. It throws an interrupted exception, which the programmer has to handle.

  * _suspend(), _Lock Status: **Locks Held**, Deprecated.

  * _resume(), _Lock Status: **Locks Held**, Deprecated; These thread methods are deprecated as it could lead to deadlocks and frozen processes. This is especially when the thread that has to resume a suspended thread requires access to the shared resource or lock held by the suspended thread before invoking _resume()_.

  * _stop(), _Lock Status: **Locks Released**, Deprecated; This thread method is deprecated as it produced inconsistent states due to damaged objects. I am not providing the code sample as it is pretty straight forward usage - but I will not recommend the use of these methods, even if using a very old compiler version.

### **Object in Java**

The Object class in Java inherently contains the methods that can control access to this object, especially in shared or multi-threaded applications.

  * w_ait(), _Lock Status: Current Object Lock Released, **OtherLocks Held**; The wait() method causes the current thread to **pause execution** and move to a wait state. It also releases the lock that it holds on the current object but retains all other locks on other objects.

  * _notify(), _Lock Status: Acquisition of Lock by an Arbitrary Waiting Thread**; **The notify() method notifies an arbitrary thread that is waiting to **obtain a lock** on the currently shared object.

  * _notifyAll(), _Lock Status: Acquisition of Lock by an Arbitrary Waiting Thread**; **The _notifyAll() _counterpart of this method **notifies all threads** that are waiting to acquire a lock on the shared object.

**Note on locks**: You may use this thought process whenever you think of Locks or Monitors in Java - Any concurrent modification by Threads should not lead to a damaged object. The only exception being the wait() and notify() mechanisms which may cause changes to a shared resource or object before swapping or switching control. A damaged object is one in which undesirable or corruptible changes have occurred to the state.

_synchronized_: In Java, the synchronized keyword is used to control access to the critical section of the code. Alternatively, it is the implementation of Thread Monitors in Java. The _synchronized _keyword can be applied to both static methods or to instance level methods or blocks. When a thread enters a _synchronized _block or method, it obtains the lock on that class or object. In the case of static synchronized methods, a single lock is held at the class level and is different from an instance level lock that is held per instance of the class. The synchronized keyword provides the necessary mutual exclusion on a shared resource. _wait(), notify(), and notifyAll()_ can only be called in synchronized blocks or methods. **Mutexes are not inherently supported in Java. **

**Case Study:** Design a multi-threaded system that has a shared resource that can take only two values; 0 or 1. It should have two methods, one each for incrementing and decrementing that are called by two threads concurrently. One of the threads can only constantly increment and another can only constantly decrement. Their operations should be mutually exclusive.

**Solution: **It is a simplified version of the Producer-Consumer problem.
    
    
    package org.csi_india.programming.workbench.multithreading;

You may refer to the following section, as these tools were introduced only since JDK 5 and 6. They provide a more granular or controlled access for asynchronous task execution in Java.

  * **Callable**: Another class similar to Runnable, whose instances are potentially executed by another Thread.

  * **Executors**: A helper interface for creation of thread pool.

  * **ExecutorService**: An asynchronous task executor that can be used to submit Runnable or Callable tasks for execution and then to track their status through a Future object.

  * **Future**: An object return from task submission to an asynchronous task executor using which a task state can be monitored.

  * **AtomicInteger**: A type of Integer object in Java that performs concurrent lock-free updates using hardware instructions.

**Case Study:** Design an asynchronous task executor modeled as a thread pool executor.

**Solution: **It is a simplified version of the Producer-Consumer problem.

Most of the below classes were introduced since JDK 7. They provide an alternate and simpler way of programming multi-threaded applications in Java.

**Condition**: Condition factors out the Object monitor methods (wait, notify and notifyAll() into distinct objects to give the effect of having multiple wait-sets per object, by combining them with the use of arbitrary Lock implementations. Where a Lock replaces the use of synchronized methods and statements, a Condition replaces the use of the Object monitor methods. Condition is a Java interface.

_**_signal()_**:_ Wakes up one waiting Thread.

_**_signalAll()_**:_ Wakes up all waiting Threads.

_**_await()_**:_ Causes the current Thread to wait until it is signaled or interrupted. _Lock_: Lock implementations provide more extensive locking operations than can be obtained using synchronized methods and statements. Lock is an interface.

**ReentrantLock**: A reentrant mutual exclusion lock with the same basic behavior as implicit monitor lock. It is a concrete implementation of Lock.

Happy Multi-Threading in Java!

Thrive in the application economy with [an APM model that is strategic](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574). Be E.P.I.C. with CA APM. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574).
