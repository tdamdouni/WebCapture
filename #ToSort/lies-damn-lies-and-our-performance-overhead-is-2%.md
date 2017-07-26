# Lies, Damn Lies, and "Our Performance Overhead Is 2%"

_Captured: 2017-06-16 at 02:08 from [dzone.com](https://dzone.com/articles/lies-and-quotour-performance-overhead-is-2quot?edition=305097&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-15)_

[Download](https://dzone.com/go?i=212221&u=http%3A%2F%2Fresources.apicasystem.com%2Fguides%2Fintro-to-api-performance-testing%3Futm_source%3Ddzone%26utm_medium%3Dadvertising%26utm_campaign%3Darticle-asm) our Introduction to API Performance Testing and learn why testing your API is just as important as testing your website, and how to start today.

The goal of Plumbr is to assist our customers in making sure their software performs better, so it is only natural that the performance of our own solutions is something we keep a close eye on. In this post, we will discuss the performance overhead aspects from the standpoint of our Java Agent, designed to harvest monitoring data from the JVMs it gets attached to.

Hopefully, after reading this post, you can challenge the vendor of your APM when they claim that their performance overhead is "in low single digits." The reality is way more complex than can be expressed in a single number, so let's start investigating what the real performance overhead of a Java Agent consists of and how it can impact your application.

## Saturation of the System Resources

Let's start by understanding the concept of saturation from software's perspective. System saturation is the level at which the system resources are being utilized. As the load increases, saturation rises, as well, until the system is fully saturated, meaning that the resources are being utilized at (close to) 100%. If load increases further, the application will become unable to keep up with the incoming work, and thus queues will be formed in front of the bottlenecks. For end users, this usually implies increased latency. Depending on the application specifics, it may also result in decreased throughput and increased error rates because of timeouts.

So, avoiding system saturation is crucial when managing a business-critical service. There are multiple ways in which systems can get saturated, among which there naturally is the poorly built system itself. In addition, one can (accidentally) reduce the number of resources available to the application. This may be data archival scripts, this may be your ops accidentally opening a 10-gigabyte log file in vim, or another virtual machine running on the same host having a spike in CPU usage introducing what is called a noisy neighbor.

In this section, we will focus on the ways how the saturation can be caused by your APM agent trying to figure out why the application is slow. Let's take a look at the most common ways a Java agent may steal system resources from the application:

  * **CPU**: If a computationally heavy task is being performed by the Java Agent, it will consume a lot of CPU cycles. As a result of this, fewer CPU cycles are available to the system. This is typically worked around by introducing throttling, running a separate low-priority process or thread, or entirely off-loading the heavy computations to a separate server instance. This is also one of the reasons why Plumbr Agents cannot be used without a Plumbr Server. The role of the Agent is just to harvest raw data as cheaply as possible and send it to the Server where heavy lifting is performed.
  * **RAM**: Like every program, Java Agents require memory. This may be Java heap memory and native memory if they go off-heap. In either case, agents are using memory resources, making less memory available for the software itself. In the worst case, this could result in an operating-system level [OOM killer](https://plumbr.eu/blog/memory-leaks/out-of-memory-kill-process-or-sacrifice-child) stepping in and terminating the memory-hungry process. Even if it does not come to that, reducing the amount of memory available for [disk caches](http://www.linuxatemyram.com/) may severely deteriorate I/O latency. It does not even have to be intentional: [increasing the native memory usage of the JVM](https://github.com/gvsmirnov/javaagent-massacre/tree/master/e1-noop) can happen by accident.
  * **Disk space and I/O**: Most readers, at some point in their career, probably have accidentally eaten up the entire disk by marking a debug log entry as INFO. Very few applications can continue to perform according to expectations when something like this happens. Most of the Java Agents also use disk storage to offload some data structures temporarily or for the aforementioned logging purposes.
  * **Network I/O**: Many Java Agents are similar to Plumbr in a sense that they act just as data harvesting probes, connecting to a server where the data is sent for analysis. Problems and, luckily, the solutions in this field are pretty straightforward. Using efficient data structures and compression algorithms, limiting the bandwidth and/or throttling are fairly simple to implement to keep the network overhead at bay.

There are more ways to steal resources from the application (e.g. creating more threads or eating up inodes), but the above are by far the most common traps.

The key here is to keep in mind that this sort of overhead is not evil as long as the system is not saturated. Running the application in slightly over-provisioned configurations is generally recommended to accommodate for possible load spikes and regular variation in load. So really, CPU and RAM usage are not that much of a concern when attaching a performance agent to your production environment. They are [poor indicators](https://plumbr.eu/blog/monitoring/how-to-set-meaningful-goals-towards-performance-and-availability-requirements) of the user experience anyway.

## Hindering the Application From Within

Now comes the more interesting part. As you put Java Agents inside your application, they have some very direct impact on how the application interacts with the Java Virtual Machine. Some of that may be obvious and straightforward, while some may be more obscure. Let's start with the more common pitfalls.

### Garbage Collection

One of the most notorious ways a Java Agent may accidentally ruin the performance of a monitored application is by disrupting the nominal functioning of garbage collection. Naturally, the simplest way is just allocating too many objects. If some parts of the Java Agent's logic are written in plain old Java, then it will allocate objects on the heap, increasing the GC pressure. This may result in more frequent or longer GC pauses, thereby decreasing throughput and skewing your latency distribution.

Even the completely allocation-free Java agents typically capture some of the objects created by the client application, extending their life cycle. For some applications, this may push them just past the tipping point and drastically worsen the GC performance. Such [examples](https://plumbr.eu/handbook/gc-tuning-in-practice#give-me-an-example-references) are few and far between, however, and generally, such a situation arising is an indication of much more serious issues lurking in the application itself.

Besides the dangers of allocating objects on the heap, there are less obvious ways to make the GC perform suboptimally. As we have seen in the [previous blog post](https://plumbr.eu/blog/java/how-to-shoot-yourself-in-the-foot-building-a-java-agent), one should exercise a lot of caution when using JVMTI, as it has a lot of impact on the more obscure and hidden parts of the JVM. But besides endangering stability, it's quite easy to hopelessly bloat the memory usage and [drastically increase GC pause durations](https://plumbr.eu/blog/garbage-collection/how-jvmti-tagging-can-affect-gc-pauses) if you're not careful enough.

As the closing remark to this section, we have written an entire [Java Garbage Collection Handbook](https://plumbr.eu/java-garbage-collection-handbook), covering all the nuances one should be aware when dealing with GC-related issues.

### Breaking JIT Optimizations

A much less obvious, but still quite a notorious issue with Java Agents is breaking [JIT](https://en.wikipedia.org/wiki/Just-in-time_compilation) optimizations. This deserves a blog post of its own as well, but let us give you just a brief summary.

One of the more common pitfalls of an instrumenting java agent in this regard is increasing a method size past its inlining threshold. The JIT compiler may stick hot method bodies directly into the caller method, thus saving on invocations. But it does so based on some heuristics, one of them being method size. Here is an interesting [article](http://normanmaurer.me/blog/2014/05/15/Inline-all-the-Things/) to read further on the matter.

Another common pitfall is breaking [Escape Analysis](https://en.wikipedia.org/wiki/Escape_analysis). To put it simply, the JVM is smart enough to (sometimes) figure out that a particular allocation does not really need a full-blown object on the heap, and can allocate on the stack instead. This optimization, along with scalarization, is especially prominent in allocation-intensive math workloads. Here is a [repo](https://github.com/cheremin/scalarization) with some interesting investigations into this. Alas, if a Java agent snatches off references to some objects for its own analysis, it may look to the JIT compiler like a Global Escape, and the optimization will not be performed, dramatically impacting the performance in some cases.

This list could go on and on: even calculating the identity hash code of an object may break [Biased Locking](https://blogs.oracle.com/dave/biased-locking-in-hotspot), significantly increasing overhead on locking and triggering extra stop-the-world pauses for bias revocations.

### And Much More

There are many other aspects one might dive into when explaining the potential performance overhead of a Java agent. But as a final example, let's take the [Memory Content Analysis](https://plumbr.eu/blog/product-updates/making-memory-usage-transparent) feature offered by Plumbr Agent. At some moments in the application's lifecycle, the feature triggers a stop-the-world pause inside the JVM, the duration of which is proportional to the number of objects and references in the heap. Even though usually it completes quite quickly, in some cases we have seen it last for minutes.

That's right: Plumbr Agent can completely stop your application. But is it really a problem if the application just died (or is predicted to imminently die) with an OutOfMemoryError? As practice and grateful customers tell us, it's totally worth it! The evidence gathered and exposed via most memory-hungry data structures gives you the culprit to optimize so you can avoid the pains of an OutOfMemoryError bringing down your entire application again.

## Take-Away

As you saw, the performance overhead of a Java Agent cannot be meaningfully expressed in a single number. There are numerous aspects which can and will impact the application depending on how the application is both built and used.

The way we recommend to approach this issue for our customers is to take Plumbr out on a test drive, where our Agents get attached to a load testing environment. In this environment, you should conclude two test runs of the application, one with a Plumbr Agent and one without. During the runs, you should monitor the behavior of the application under the same load for resource consumption, throughput, and latency. Analyzing the results will give you the exact overhead numbers for your environment.

Find scaling and performance issues before your customers do with our Introduction to [High-Capacity Load Testing guide](https://dzone.com/go?i=212222&u=http%3A%2F%2Fresources.apicasystem.com%2Fguides%2Fintro-to-high-capacity-load-testing%3Futm_source%3Ddzone%26utm_medium%3Dadvertising%26utm_campaign%3Darticle-alt).
