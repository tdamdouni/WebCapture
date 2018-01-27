# Dealing With the Disadvantages of Multithreading

_Captured: 2018-01-19 at 13:21 from [dzone.com](https://dzone.com/articles/deal-with-disadvantagesnbspof-multithreading?edition=355098&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-01-19)_

[Learn how _real _real-time monitoring is critical for DevOps](https://dzone.com/go?i=272435&u=https%3A%2F%2Fsignalfx.com%2Fsolutions%2Fenabling-devops%2F). Because you can't build what you can't see.

When I stared to work on multithreading as a request from a customer, I heard a lot of good points about multithreading like improved performance, better use of system resources, better availability, among other things.

At that time, I thought this one is exactly which I was looking for. But one question came to me: multithreading sounds good, but what are disadvantages?

![Image title](https://dzone.com/storage/temp/7704905-multithreading.png)

I found a list of disadvantages in my research. If we choose to use multithreading we have to know which problems will come to our project in the near feature, and how our project can live with them. When we know that, we can minimumize the effect of disadvantages to our project.

So, let's see which we can do. Here are some of the main disadvantages of multitheading.

## **Difficulty of Writing Code**

When you check the guideline to using threads, it's so simple: it just extends and implements some functions. But it's not really as simple as it appears, as you have to take care for a lot of things afterwards.

When you apply multithreading, you will push a lot of threads together at same time, on the same data, same objects, and same functions. If you don't have a good way to control them, everything will become terrible. So that's reason why we need expert person-to-design multithreading.

So, what can we do?

### Replace Any Function or Code That Are Not Thread-Safe 

What's thread-safe? Your source code can be called thread-safe if all threads go inside the same function at the same time, and each thread can get exactly the data which they expected not the data of other thread.

![Image title](https://dzone.com/storage/temp/7704915-123-2.png)

There are many cases which make your source code not thread-safe, including static variables, static function, and singleton class, to name a few. If all threads run same time, they will use the same static variables or function, and this thread will get the data of another thread.

Three ways to make an object thread-safe are:

  * **Synchronizing the critical sections.** When you do that, only 1 thread can work with this part at 1 time, but take care when you use that, only for the source code which all thread can't run together. This one will make the performance go down.

  * **Use immutable objects.** Immutable objects are simply objects whose state (the object's data) can't change after construction.

  * **Use thread-safe wrappers.** This means you put the main class (which isn't thread-safe) inside a new class that is thread-safe. This way is helpful when the main class from third party or can't update.

### **Ignore Deadlock**

![Image title](https://dzone.com/storage/temp/7704927-deadlock-of-threads.jpg)

The deadlock happens when one thread is waiting for the resource of other thread, but the other thread still waiting for the resource which keep by the first thread.

To ignore the deadlock, we have to ensure that:

  * Each thread has to process different data.

  * Each thread have to create own object and function by themselves.

  * Don't share the data between threads.

### **Careful When Using _Synchronized_**

Inside multiple thread when we use this one, it will make the performance go down, you have to make it as small as you can, only use it when you have to use.

![Image title](https://dzone.com/storage/temp/7704928-blog-trampoline.png)

## **Difficulty of Testing and Debugging**

With simple thread you can easily test and debug, and see the work flow of data inside your function, but if all threads run together, you can't do it.

To deal with that, we can:

**1\. Keep the number of threads as a input parameter of main function if you can**. And when something happens, we can set the number of threads to 1, and we have a single thread to test and debug.

However, this way just supports finding the business bugs, and the bugs of single thread. If we got the problem with multiple threads like each threads have conflict with each other, this way is not helpful.

**2\. Add useful log to the thread.** The log is so powerful, try to put the log at the position which you can see the running flow, and you can see the whole flow. Write log when the exception happen, I hate to catch java. lang.Exception but if you want the thread keep going on the next data, you have to catch it, to make sure everything is under control.

At the first time running we can put a lot of log info to your source code, and when everything runs stably, you can remove them. But don't make it too big.

![Image title](https://dzone.com/storage/temp/7704931-small-person-holding-too-big-log-file.jpg)

**3\. Use the tool to test. **When multiple threads are running, you can use the tool to see how the threads running, which one is running, which one is not, the status of each thread, and so on.

We have some tools here. I used Jconsole, which already supports Java 6.

You can read detail about it [here](https://docs.oracle.com/javase/8/docs/technotes/guides/management/jconsole.html).

You will get a lot of helpful information from this tool. To check the threads status, you can see the picture below.

![Image title](https://dzone.com/storage/temp/7705533-jconsolve.png)

With this GUI, you can see how many threads are running, when they stop, whether they are deadlock edor not, and more. It's so helpful for testing purpose.

A coin has two sides, everything have good and bad points. Each technical tool will have advantages and disadvantages. If you can use the power of advantages and find the way to live with disadvantages, you've got that technical tool.

Let's enjoy it!

[Get real-time alerts and visualizations](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue) across your cloud infrastructure for real real-time cloud monitoring. [Try it FREE now](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue)!

Opinions expressed by DZone contributors are their own.
