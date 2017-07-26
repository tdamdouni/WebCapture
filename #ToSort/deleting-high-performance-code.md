# Deleting High-Performance Code

_Captured: 2017-04-14 at 00:10 from [dzone.com](https://dzone.com/articles/deleting-high-performance-code?edition=290900&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-13)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

[5 years ago](https://ayende.com/blog/160546/the-last-ravendb-feature-of-the-year-bulk-inserts), we introduced bulk insert support to RavenDB. The idea was to let users have a good way to insert data into RavenDB as fast as possible. In order to do that, we created special code paths that were super optimized for loading a large amount of data into the database as fast as possible.

Basically, we bypassed a lot of the stuff along the way, put some constraints on the user when calling this and smoothing everything we could. Internally, this was implemented using a pretty complex system that split work among multiple threads to handle serializing, sending over the network, parsing, and writing to disk.

When we start working on 4.0, one of the very first things we did was to build bulk insert from scratch. We built it on top of TCP instead of HTTP, and we decided that for the sake of performance, we could throw pretty much anything at this problem. The overall design looked something like this:

  * One thread at the client side to **get entities and serialize them to our blittable binary format**.
  * One thread at the client side to **send the data over the network**.

In order to save memory, those two threads have a common buffer pool that they reuse all the time.

  * On the server side, we have a dedicated thread reading from the network, constructing our blittable instances, and validating their format and putting them in a queue.
  * On the server side, we have a dedicated thread pooling from the queue and batching requests, then saving them in a single transaction.

Like the client, we are saving memory by having a common shared buffer pool.

Initially, having a dedicated code path for bulk insert was awesome because we could get _really_ high performance from it. But it also introduced problems. Consider the scenario above. The server thread is reading from the network is reading as fast as it can and sending the data to the queue.

If the consuming thread isn't fast enough (for example, we just hit an I/O bump), we might start accumulating stuff in the queue -- and if this goes for long enough, we might run out of usable memory.

We had to implement our own backpressure and congestion control because of that, and that led to more interesting issues. Because we were starting to read very quickly and only ran into the I/O problem later, we had incidents in which we weren't fast enough with the "let me catch my breath" notification and overloaded the TCP connection, resulting in timeouts on the client.

This all sounds very complicated. And it was. But we managed to solve all of those issues and this piece of code had very few changes for a long time.

This week, we deleted all of it in favor of a radically different implementation. Basically, the new implementation will just open a standard HTTP request and write JSON strings to the network. This is about as simple an implementation as we can get. And we delete all this high performance, extremely tuned and carefully crafted code.

Why?!

You might have noticed that we are putting a major emphasis on performance, so why would we throw all that code away?

There are several reasons:

  * **Back pressure, congestions control, and other fun factors are not things that we want to deal with**. Instead, we want to deal with them at the network layer, where there is a lot more information about it.
  * **Complex code is costly** and it requires us to modify other pieces of code to ensure that this still works.
  * We are used to getting impressive numbers from this special casing, but **we are seeing similar numbers without all the hoopla**.

The trigger for this was a set of optimization we did for optimizing standard write patterns -- your usual OLTP workload, basically. As we made that faster and faster, we started to think whatever it made sense to think to allow the bulk insert code to still remain a special snowflake.

For example, the bulk insert code didn't use our transaction merging capabilities. Instead, it would directly talk to the storage. But that meant that it lost out on a lot of the benefits we made to the transaction merging code. It would also cause bulk inserts to fight concurrent write loads (including other bulk inserts), instead of cooperating.

The decision to go with TCP connection directly was made because we wanted absolute performance and control, but we had taken too much upon ourselves and we were concerned about firewall issues. Forcing admins to open another port can be tricky, and we want to reduce the cost of deploying RavenDB instances as much as possible.

Finally, we needed something that was a lot more approachable. While using our own binary format over the wire meant that we could do a lot less work, it also put a _major_ stumbling block if you wanted to do bulk insert via anything but our .NET code. If we wanted to do bulk insert from Node.js, that would require a non-trivial amount of effort, to say the least.

The new wire format looks like this:

This is trivial to integrate with regardless of platform. The reason we use this particular format? This is actually identical to the format we use fo `SaveChanges`, and _that_ piece of code has been through multiple optimization rounds. Here is a small example from that code path:
    
    
                if (*(int*)state.StringBuffer != 1752458573 ||
    
    
                   *(short*)(state.StringBuffer + 4) != 25711)
    
    
                if (*(short*)state.StringBuffer != 25931 ||
    
    
                    state.StringBuffer[2] != (byte)'y')
    
    
                if (*(long*)state.StringBuffer != 8389754676633104196)

This is pretty fast (and gnarly) code, so we get to reuse that and benefit from any future optimizations.

The major difference here is that this is a _streaming_ format -- that is, we are going to read from the stream and process this immediately. With `SaveChanges`, we have to read the whole thing to memory and apply it as a single transaction. In the case of our new bulk insert code, we're not going to do the whole thing as a single transaction, but a series of them, based on the actual workload.

The fun thing here is that we can dramatically reduce the overall complexity while maintaining a lot of the desired behavior. In fact, the entire bulk insert implementation is under 50 lines of code now. Small enough that I can just include it in this post in its entirety.
    
    
            using (var parser = new BatchRequestParser.ReadMany(ctx, requestBodyStream))
    
    
                var list = new List<BatchRequestParser.CommandData>();
    
    
                    if (task.IsCompleted == false && list.Count > 0 ||
    
    
                        totalSize > 16 * Voron.Global.Constants.Size.Megabyte)

Note that this code rely on a lot of other code, but none of this other code is Bulk Insert specific. There are a few interesting bits here that are worth exploring.

`BatchRequestParser.ReadMany` allows us to stream read the data, it read each individual command and return it. The code in line 17 (`var task = await parser.MoveNext()`) is pretty strange. MoveNext is returning a `Task<Task>`. The idea is that we are going to read a command from the network and parse it immediately. However, if there isn't a full command already buffered, we'll return an async task for completing it. (The `Task<Task>` is here because we might need to wait for the initial command, or for the final `]` of the array. We'll probably optimize that once we are done with all the taxes on this feature, to avoid the `Task` allocation.).

The basic idea is that we'll read and parse from the network as long as there is information available, and when we start waiting for the network, we'll go into the if statement and send it to the transaction merger. That gives us three very important properties.

  1. **We parallelize the work**. While we are waiting for the next document to arrive over the network, we are concurrently writing the current batch to disk. Note that we don't have any such things as batch size defined. This is all controlled by the network speed. We do have the 16 MB limitation, to prevent a really fast network from causing excess memory utilization on the server side.
  2. **We are only buffering a relatively small amount of data** (by default, however much the network can give us without waiting), so we get pretty consistent read experience. **_Read a buffered document_** > **_Write to disk_**. This has the effect of being able to teach the connection how fast we can read and process the results, giving us much better behavior as far as the network stack is concerned.
  3. **We play well with the rest of the system**. By utilizing the transaction merger, we'll work well with concurrent work on the server, instead of fighting for the same resources.

The code still needs some work (resource handling, better error management, etc.), but it is a new win in terms of simplicity and manageability.

But what about performance? Previously, we have spread the load across many threads on both client and server ends. That gave us a faster overall performance at the cost of much higher complexity.

As it turns out, quite a lot of the benefit of bulk insert is related to the fact that we have just a single network connection going on, and we have that. We get some parallelism between writing the documents and reading from the network, but that is intentionally limited (to avoid fooling the other side that we can keep up with that rate of reads if we have an I/O stall).

But let's assume that you have really need to be able to insert a _lot_ of data into the database -- fast enough and large enough that you want us to be even faster.

That is actually quite easy. Remember how many times I said that this new system plays well with other operations? This is _important_, because if you want to have a faster performance for bulk insert...just run parallel bulk inserts. This way, you'll have multiple threads on the server side reading and parsing, and all of that work will go (together) to the transaction merger), giving us a much better overall performance.

In our benchmarks, we actually had issues with data generation on the client side, causing a major slowdown. We had to pre-generate all the data upfront, and only then start the bulk insert process. Otherwise, the call to Random to generate the data would have enough of an impact on the overall benchmark test. I don't _think _that you'll be able to generate the data fast enough to saturate a single bulk insert connection easily, but given how easy concurrency has become, if you can, the scale-up option is incredibly easy.

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).
