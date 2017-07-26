# Writing 600 Times Faster

_Captured: 2017-03-31 at 00:55 from [dzone.com](https://dzone.com/articles/writing-600-times-faster?oid=twitter&utm_content=buffer68554&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](https://servedbyadbutler.com/getad.img/;libID=300344)

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

In my day job, I'm building RavenDB, a NoSQL document database. It is a very cool product, but not the subject of today's article. Instead, I'd like to talk about how we made RavenDB very fast, the techniques and processes we used to get there, as well as the supporting infrastructure.

During the design process for the next release of RavenDB, we set ourselves a pretty crazy goal. We wanted to get a tenfold performance improvement across the board. It's one thing to say that, but a lot harder to do. We've had to work quite hard to get there, re-working pretty much every layer in the system to make it better.

Here, we'll talk about how we improved the write speed of RavenDB (and more particularly, Voron, which is the low-level storage engine we wrote) by a tremendous margin, while maintaining the same transaction safety properties. This was neither easy nor fast, but it was a very rewarding journey.

I chose to write about the write speed improvements because it was a challenging task that doesn't respond very well to standard optimization techniques. You can't just throw more cores at the problem -- and while you can buy faster hardware, at some point you'll reach the limit. Before we get to the optimizations we implemented, let me explain what the problem is.

RavenDB is an ACID-compliant database, meaning that once a transaction has been completed, it should remain in the database even in the face of a failure. In other words, if the database reported a successful transaction, pulling the plug from the machine immediately afterward would not impact the data. Once we restart, the data that we committed is still there and still valid. At the same time, a transaction that was midway through (not committed to the database) is not going to be there at all.

![Image title](https://dzone.com/storage/temp/4803311-screen-shot-2017-03-29-at-110347-am.png)

In the following graph, you can see the results of running the following code on a variety of disks and using various sizes of buffers.

![Image title](https://dzone.com/storage/temp/4803325-screen-shot-2017-03-29-at-110445-am.png)

Several interesting things are shown in this table. A 4 KB buffer is 512 times smaller than a 2 MB buffer, but writing 2 MB to disk is only 8 times slower on an SSD, and only about 50% slower on an HDD. It seems that the size of the writes rarely matters. In fact, we tested writes with a size of64 MB and the results were 1,336.27 ms for HDD and 373.6 ms for SSD.

Databases usually implement their durability guarantees using some sort of journal, each transaction writes the data it modified to the journal, and the commit happens when we ensure that the data is on stable storage by calling fsync.

That leads to a lot of performance challenges. Writing to the disk at random places tends to offer the worst possible performance, so we really want to only write to the journal in a sequential manner. That, in turn, leads to the serialization of the access to the journal. The problem is the disk access is so slow that we are effectively turning our whole system into one big queue sitting in front of the disk I/O and waiting… and waiting… and then waiting some more.

The first version of Voron we built acquired an exclusive lock whenever it needed to write, and its top speed was roughly around 200 transactions per second. Note that this isn't quite saying that it was able to do 200 writes per second. As you can see in the table above, the size of the write isn't really that important, in the grand scheme of things. It is the number of times that you have to hit the disk.

We call it the bus factor because when you take the bus, its speed is rarely impacted by how many people are on board. The bus is the bus, and it will take you to the destination at its own pace.

These and other observations led us to try using traffic optimization methods to improve our performance. The very first thing we did was to implement the bus, known in database jargon as transaction merging. Instead of each transaction traveling alone all the way to the disk, they would now join together in a queue, and then travel to the disk in a group. Basically, each request would prepare all the information it needed (parsing the request, computing work, etc.) and then submit the work into a single queue. A dedicated thread would pull the work from the queue, apply it to the database, and then write it to the journal.

This means that even though our writes were sequential, we could still parallelize a lot of the work before we hit the actual database, and we were also able to send a lot more transactional work with every trip to the disk.

This single change had a mind-blowing effect. We moved from an average of 200 writes per second to an average of over 20,000 writes per second. That was two orders of magnitude increase in performance, all because we were optimizing our I/O pattern.

The next thing we tackled was how much we are writing to the transaction journal. Now that we had merged transactions, they could get pretty fat. It takes 8 milliseconds to write 2 MB and flush it, but it takes 375 milliseconds to write 64 MB and flush it to SSD. On the other hand, compressing data using LZ4 can be done at a rate of over 625MB/sec. Being a document database, most of the data we place in RavenDB are actually JSON documents, which compress extremely well and quite cheaply.

With compression, we're able to perform a large number of operations in a single transaction, but only write a fraction of the size of the data that we manipulate to the journal. With this technique, it meant that we traded off CPU time for I/O, but given the numbers that we see here, that was a very wise choice. Even if we spent a whole 100 milliseconds on compressing the data, we typically reduced it by so much that the saved I/O time is a net benefit.

Those two optimizations (transaction merging and compressing the journal output) have managed to dramatically improve the performance of our system, but there was still a lot of additional work to be done. At that point, we pulled a profiler and started going over the code, finding hotspots and improving them one by one.

The really nice thing about such work is that it is cumulative. That is, you improve 2% here and 0.5% there, then suddenly it is like releasing the floodgates and you have a 5% increase in performance. A small increase in performance in one location can dramatically affect the whole system utilization.

![Performance Guide](https://dzone.com/storage/temp/2579425-performanceguide.jpg)

> _Performance Guide_

_Find this article and much more in..._

**[DZone's Guide to Performance: Optimization and Monitoring](https://dzone.com/guides/performance-optimization-and-monitoring?oid=performanceplug)**

Including:

  * Survey findings from over 500 developer responses

  * Articles written by top Performance experts

  * "What Ails Your Application" Infographic

  * Directory of performance optimization and monitoring tools

A lot of the time, this means analyzing what we are doing and finding ways to either avoid doing it entirely (caching, different algorithm, etc.) or doing it more efficiently (better locality of data, more efficient instructions, etc.).

But, there was one thing that truly annoyed me. As we kept improving things, the cost of compressing the data slowly took more and more of our time. It got to the point where it was the dominating factor in the transaction commit process. But, at the same time, it had such an impact on our performance that we couldn't just drop it.

Down below, I have visualized what this looked like. The green portion is the part that we care about -- actually processing the transaction.

The yellow portion is compression, and the red is the actual writing to disk. Note that without the compression, the work would be completely dominated by the disk, so we can't just drop it. But this type of behavior introduces a lot of jitter into the system. We are processing operations in a transaction, then compressing the data, then writing to disk. That means that the disk is actually idle for a non-trivial portion of the time -- a crime in high-performance circles.

Instead, we made the transaction commit an asynchronous process. Whenever a transaction is completed, it will start a task to compress its data and write the data to disk. At the same time, we can already start the next transaction, which gives us much more concurrency. In fact, as long as we are waiting for the previous transaction to complete writing to the disk, we can continue accepting more work into the new transaction.

![Image title](https://dzone.com/storage/temp/4803355-screen-shot-2017-03-29-at-111432-am.png)

This gives us an additional benefit because the transaction size is now determined by the actual I/O speed of the system; we are in effect self-balancing, and we'll find the optimal balance of CPU vs. disk work in a short order.

The overall behavior now looks like this:

![Image title](https://dzone.com/storage/temp/4803368-screen-shot-2017-03-29-at-111525-am.png)

And while this change isn't as dramatic as the transaction merging one, it did manage to up our performance by a total of 45%.

In total, we were able to reach a maximum amount of about 120,000 writes per second, counting all optimizations and running at full throttle. We've been able to manipulate the nature of physically accessing the hardware to merge a lot of individual writes into "full bus trips" to the disk, and then compress and parallelize the rest of the work even further.

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
