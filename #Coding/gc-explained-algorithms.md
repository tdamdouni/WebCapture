# GC Explained: Algorithms

_Captured: 2017-09-21 at 19:30 from [dzone.com](https://dzone.com/articles/gc-explained-algorithms?edition=326503&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-21)_

[Transform incident management with machine learning and analytics](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2) to help you maintain optimal performance and availability while keeping pace with the growing demands of digital business with this [eBook](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2), brought to you in partnership with BMC.

As described in the [previous post](https://dzone.com/articles/gc-explained-collectors-overview), we have four different garbage collectors available in HotSpot JVM. There are some significant differences between them, but the actual concepts behind the algorithms which are used to do the actual job are quite similar. In this short post, I will try to explain three basic algorithms:

  * Mark-sweep
  * Mark-sweep-compact
  * Mark-copy

## GC Roots

Before we move into the details, let's make sure that we have a common understanding of what GC Roots are. These are the objects which are **directly accessible from outside the heap**. For example:

  * Active threads
  * Static variables
  * Local variables (accessible via stack of a thread)
  * JNI references
![Image title](https://dzone.com/storage/temp/6631766-gc-roots.png)

## Mark

All of the algorithms discussed have the same mark phase. Marking phase is about traversing the whole object graph, starting from GC Roots. When GC visits the object, it marks it as accessible and thus alive. All the objects which are not reachable from GC Roots are garbage. Marking requires stop-the-world (STW) pauses, because the running application threads could interfere. How long the STW pause is, depends mostly on the number of visited objects.

##  Mark-Sweep

After marking phase, we have the memory space which is occupied by visited (accessible via GC Roots) and unvisited objects. Sweep phase releases the memory fragments which contains unreachable objects. It is simple, but because the dead objects are not necessarily next to each other, we end up having a fragmented memory. That's not bad per se, but trying to fit a too large object into the memory can lead to [OutOfMemoryError](http://performantcode.com/jvm/what-causes-outofmemoryerror).

##  Mark-Sweep-Compact

This algorithm fixes the problem with fragmented memory. After all alive objects are marked, they are moved to the beginning of the memory space. That helps to avoid [OutOfMemoryError](http://performantcode.com/jvm/what-causes-outofmemoryerror) caused by too fragmented memory, but compacting the heap isn't for free. Copying objects and updating all references to them take time and it all happens during STW pause.

##  Mark-Copy

Mark-copy algorithm copies all alive objects to a new memory region. The previously occupied region is considered to be free. Next time mark-copy is executed, all the alive objects are moved back to the previous memory region. As you can imagine, this, of course, leads to a memory compaction. Unfortunately, it requires additional extra region large enough to fit all live objects at any given point in time.

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

Topics:

gc ,algorithms ,jvm ,heap ,memory ,out of memory ,compaction ,fragmentation ,performance
