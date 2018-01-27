# GC Explained: Heap

_Captured: 2017-09-06 at 20:27 from [dzone.com](https://dzone.com/articles/gc-explained-heap?edition=322400&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-06)_

[Transform incident management with machine learning and analytics](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2) to help you maintain optimal performance and availability while keeping pace with the growing demands of digital business with this [eBook](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2), brought to you in partnership with BMC.

## Generational Garbage Collectors 

JVM heap is divided into two different Generations. One is called Young and the second one is the Old (sometimes referred to as Tenured). The Young Generation is further separated into two main logical sections: Eden and Survivor spaces. There are also Virtual spaces for both Young and the Old Generations which are used by Garbage Collectors to [resize other regions](https://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/sizing.html) \- mainly to meet different GC goals.

![Image title](https://dzone.com/storage/temp/6478963-gc-heap-2.png)

## Weak Generational Hypothesis

Why is heap divided into the Young and Old Generations? It's because lots of objects are usually created and used for a relatively short period of time. This observation is called Weak Generational Hypothesis in GC theory. Imagine some objects created and used only inside the loop - assuming that they are not going to be [scalarized](http://performantcode.com/compiler/escape-analysis), every iteration discards previously created objects and creates new ones.

## Object Lifecycle

Objects start their journey in Eden of the Young Generation. When Eden fills up, so called **Minor GC **is performed: all application threads are stopped (stop-the-world pause), objects which are not used anymore are discarded and all other objects from the Eden are moved to the first Survivor space (S0). Next time a Minor GC is performed, the objects go from S0 to the second Survivor space (S1). All live objects from Eden go to S1 as well. Notice that it leads to a differently aged object in the Survivor space - we have objects from Eden and objects which were already in the Survivor space. Next iteration of Minor GC moves the objects from S1 back to the S0, so the Survivor spaces switch every GC. Why do we have two Survivor spaces and why do we switch them? It's pretty simple - when the object reaches certain age threshold, it is promoted to the Old Generation. It leads to Survivor space fragmentation which can be easily eliminated with moving all objects from S0 to S1 and back every Minor GC.

Eventually, when the Old Generation fills up, a **Major GC** will be performed on the Old Generation which cleans it up and compacts that space. If and how stop-the-world pauses occur during Major GC depends on specific GC algorithm used.

Besides Minor and Major GC, there is also a** Full GC** which is about cleaning the entire heap - both Young (by Minor GC) and Old (Tenured) (by Major GC) Generations. Because a Full GC includes Minor GC, it also causes stop-the-world pauses.

## Summary

There are two main advantages of having the heap divided into two regions. Firstly, it's always faster to process only some portion of the heap (stop-the-world pauses take less). Secondly, during Minor GC, all objects from Eden are either moved or discarded which automatically means that this part of the heap is compacted.

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

Topics:

gc ,heap ,heap sizing ,heap objects ,jvm ,garbage collection ,eden space ,generations ,performance
