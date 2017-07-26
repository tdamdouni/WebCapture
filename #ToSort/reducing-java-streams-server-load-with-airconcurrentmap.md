# Reducing Java Streams Server Load With AirConcurrentMap

_Captured: 2017-05-14 at 21:48 from [dzone.com](https://dzone.com/articles/reducing-java-streams-server-load-with-airconcurrentmap?edition=298100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-14)_

The Java 8 streams feature is an excellent way to perform semi-declarative operations on Maps, especially as it provides improved performance via almost free parallelism, taking advantage of the increasing core count of modern computers. However, the parallelism is primarily useful in single-threaded applications which have batch operations to do on Maps. Servers that are under continuous load react in a completely different way to parallelism, and we will show here graphically what happens.

We will discuss:

  * The most basic stream operations and how to use them, as applied to a max() function. This function is very fast on Long-valued Maps, so the differences between Map implementations is most apparent.

  * The effects of heavy server load on stream performance, with graphical results.

  * The Java Microbenchmarking Harness JMH, with the example code which generated the results.

  * The streaming performance of `[AirConcurrentMap](https://boilerbay.com/airmap)`, a standard `ConcurrentNavigableMap `written by the author.

## Basic Stream Use

It is easy to use a stream to calculate, for example, the maximum of a Long-valued Map, which will be our test case. We can do it several ways. As an example, we can use a `reduce()`:
    
    
        Map<Object, Long> map = new HashMap<Object, Long>();
    
    
                         .reduce(Long.MIN_VALUE, (x, y) -> x > y ? x : y);

In order to maximize performance, we can convert the stream to a `LongStream`
    
    
                        .mapToLong(o -> ((Long)o).longValue())
    
    
                        .reduce(Long.MIN_VALUE, (x, y) -> x > y ? x : y);

Then, in order to get the parallelism for free, we just chain in a `.parallel()` invocation:
    
    
                        .mapToLong(o -> ((Long)o).longValue())
    
    
                        .reduce(Long.MIN_VALUE, (x, y) -> x > y ? x : y);

It turns out the `LongStream` has a built-in `max()` method, but it returns an `OptionalLong`, which is a bit more trouble so we ignore it. It just does a `reduce(Math::max)` anyway.

## Test Setup

We used the excellent [Java Microbenchmarking Harness](http://openjdk.java.net/projects/code-tools/jmh/) to do fair and precise testing. This framework handles almost all of the hard work in testing, including process forking, setup, threading, looping, timing, parameterization, and statistics including confidence intervals. It is good for small pieces of code that are to execute frequently as well as slower operations. We present the entire test code below. Our test code also has a selection of other interesting Map performance measurements. The scanning techniques we cover are very important, because they can easily become the chief bottleneck, and not all situations cause `get(), put(), and remove()`to be limiting, particularly in large Maps.

We will cover various techniques for finding the maximum of a Map with Long values, including iterating, `Map.forEach()`, serial streams, and parallel streams, for both 8- and 100-thread loads. The system is an Intel X86-64 2.4GHz quad core. So, with 8 threads we are fully loading the CPU, but many servers have very large numbers of threads handling web hits.

## We Use Only ConcurrentMaps

In this testing, we assume that the Maps may be modified during the scanning. This will normally be the case in a server environment, because most Maps cannot simply be loaded with data when the server boots and then held static thereafter. Various tricks can be used to avoid problems with write/write and read/write access overlap, but in general, if a system contains multiple threads, non-concurrent Maps can be very dangerous. Write/read overlaps may occasionally return wrong results and write/write failures may even permanently corrupt the structure of the Map. These failures manifest rarely and may be difficult to understand, detect and diagnose. So, we do not use bare `HashMap`and `TreeMap`, but wrap them using `Collections.synchronizedMap(Map)`. Catching `ConcurrentModificationException`is not a reliable means to detect wrong results or corruption and it is not guaranteed to be thrown at all, in spite of the choice of a particular Map implementation to have the 'fail-fast' characteristic.

## Problems With Collections.synchronizedMap()

It is easy to adapt `HashMap`and `TreeMap`-- or any other Map -- for Thread safety using `Collections.synchronizedMap(Map)`. This static method simply wraps the given Map and returns a new instance of a private `SynchronizedMap` which delegates _almost_ every method within a synchronized() block. However, the resulting Map is not very satisfactory. The model is incomplete, slow, and risky:

  * The wrapped Map may no longer be used directly, so all references to it must be hidden safely.

  * Iterators, `Map.forEach(BiConsumer)`, Spliterators, and streams uses are not synchronized (possibly others too?). These must be synchronized explicitly at the point of use. The synchronization must be on the `SynchronizedMap` itself, and not on the wrapped Map. Outside code such as library code that receives a `SynchronizedMap` may fail to do such scan synchronization.

  * All access is serialized, so only one core is used.

  * Scans may dramatically delay otherwise fast operations such as `get(), put() and remove()` in other Threads, reducing throughput in those Threads: `ConcurrentMaps`avoid this problem.

  * If a Map is wrapped more than once in different places, access may still overlap and cause problems. It is not enough to do a temporary wrapping at each point of use.

  * Synchronization is slow compared to some Map operations, especially when wait queues build up. Synchronization is very fast, however, when there is no contention.

Nevertheless, we test `HashMap`and `TreeMap` in their synchronized forms.

## The Tested Maps

We test over:

  * [AirConcurrentMap](https://boilerbay.com/airmap) - a `java.util.concurrent.ConcurrentNavigableMap` from [boilerbay.com](https://boilerbay.com).

  * Synchronized java.util.HashMap.

  * Sychronized java.util.TreeMap.

  * java.util.concurrent.ConcurrentHashMap.

  * java.util.concurrent.ConcurrentSkipListMap.

## General Conclusions

These are rough observations - you should look at the graphs for yourself. Generally, the four scanning techniques have widely different startup times, efficiency, and inter-thread interference. The variations over different Map implementations are extreme as well.

  * Iteration is slower than `Map.forEach( BiConsumer)`, sometimes very much.

  * Iteration and `forEach()` start fast, peak at about 100 entries, then slow down.

  * Streams have a significant startup delay.

  * The synchronized `HashMap` and `TreeMap`are very slow.

  * The 8-Thread case is comparable to the 100-Thread case.

  * For small Maps, `ConcurrentSkipListMap` is best, for large Maps, `AirConcurrentMap` is best, with a break-even point from 100 to 10K Entries.

  * Parallel streams are slow, and actually slower than serial streams in these high-load cases, except for `AirConcurrentMap`, which remains fast. This is because `AirConcurrentMap` 3.2 uses only serial scan even for parallel streams. Parallel scanning as discussed in a [previous DZone article](https://dzone.com/articles/faster-streaming-with-airconcurrentmap) will be added transparently later.

## The Graphs

The 8-thread Graphs:

![Image title](https://dzone.com/storage/temp/5263806-serverload-8-threads-iterator.png)

![Image title](https://dzone.com/storage/temp/5263807-serverload-8-threads-foreach.png)

![Image title](https://dzone.com/storage/temp/5263808-serverload-8-threads-serial-stream.png)

![Image title](https://dzone.com/storage/temp/5263809-serverload-8-threads-parallel-stream.png)

The 100-thread Graphs:

![Image title](https://dzone.com/storage/temp/5263810-serverload-100-threads-foreach.png)

![Image title](https://dzone.com/storage/temp/5263811-serverload-100-threads-serial-streams.png)

![Image title](https://dzone.com/storage/temp/5263812-serverload-100-threads-parallel-streams.png)

## The Java Microbenchmarking Harness Code

The JMH code is very concise, owing to the fact that only a few Annotated features are needed, factoring out almost everything but the state, setup methods, and benchmark methods. We have parameterized the tests so that JMH will sweep over a range of Map sizes and Map implementations. The testing uses the Maven framework so it is easy to setup and use. The code here provides many interesting performance metrics. The command line can override the Annotated setup defaults. Each benchmark method must return a value so that there is some tangible result that prevents the JIT from removing all the code!

## Result Data

Here is the result data obtained by running this command with an X86-64 ORACLE Java 8 JVM:

`java -Xmx4g -jar target/benchmarks.jar`

Note that the graphical representations show performance in terms of values per second, which is the product of ops/s and mapsize. As a bonus, the performance of `get() `is included, plus that of `put()` combined with `remove()`.

## Summary

Under heavy thread load, parallel Map streams behave differently than in the few-threaded case. Parallelism only works well when cores are actually available for use that would otherwise be idle. The overhead of the parallelism framework can become very great.

`Collections.synchronizedMap()` is slow, inconvenient and risky. [AirConcurrentMap](https://boilerbay.com/airmap) is best above about 100 to 10K Entries, while `ConcurrentSkipListMap` is best below that.
