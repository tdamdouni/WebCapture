# A Tale of Two Iterators

_Captured: 2017-12-01 at 20:28 from [dzone.com](https://dzone.com/articles/a-tale-of-two-iterators?edition=341091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-01)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

When you look at the most popular Java interview questions, you might encounter the one about fail-fast and fail-safe iterators:

> What's the difference between fail-fast and fail-safe iterators?

The simplified answer is that:

> A fail-fast iterator throws `ConcurrentModificationException` if the collection is modified while iterating, but fail-safe doesn't.

Even though it totally makes sense, it's not clear what the interviewer means by fail-safe. The Java specification does not define this term when it comes to iterators. Rather, there are four policies for concurrent modification instead.

## Concurrent Modification

Firstly, let's define what concurrent modification is. Concurrent modification occurs when, for example, we have an active iterator from a collection and there are some changes made to that collection, but they do not come from our iterator. The most obvious example is when we have multiple threads -- one thread is iterating, and the second one adds or removes the elements from the same collection. However, we can also get `ConcurrentModificationException` when we work in a single-threaded environment:
    
    
    List<String> cities = new ArrayList<>();

## Fail-Fast

The snippet above is the example of a fail-fast iterator. As you can see, as soon as we tried to get the second element from the iterator, the `ConcurrentModificationException` was thrown. How can an iterator know if the collection was modified after you had created it? You could have a timestamp such as `lastModified` in the collection.

When you create an iterator, you would need to make a copy of this field and store it in the iterator object. Then, whenever you would call the `next()` method, you just need to compare `lastModified` from the collection with the copy from the iterator. A very similar approach can be found in an `ArrayList` implementation, for instance. There is a `modCount` instance variable that holds the number of modifications made to the list:

It is important to mention that fail-fast iterators work on a best-effort basis -- there is no guarantee that `ConcurrentModificationException` will be thrown if there is a concurrent modification, so we should not rely on that behavior. It should be be used to detect bugs. Most of the non-concurrent collections provide fail-fast iterators.

## Weakly Consistent

Most concurrent collections from the `java.util.concurrent` package (such as `ConcurrentHashMap` and most `Queues`) provide weakly consistent iterators. What that means is very well explained in the [documentation](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/package-summary.html#Weakly):

>   * they may proceed concurrently with other operations
>   * they will never throw `ConcurrentModificationException`
>   * they are guaranteed to traverse elements as they existed upon construction exactly once, and may (but are not guaranteed to) reflect any modifications subsequent to construction.

## Snapshot

In this policy, the iterator is associated with the state of the collection from the moment when the iterator was created -- our snapshot of the collection. Any change made to the initial collection creates a fresh version of the underlying data structure. Of course, our snapshot is untouched, so it doesn't reflect any changes made to the collection after the iterator was created.

This is the good old copy-on-write (COW) technique. It completely solves the concurrent modification problem, so no `ConcurrentModificationException` can be thrown. Additionally, the iterators do not support element-changing operations. Copy-on-write collections are usually too expensive to use, but it might be a good idea to give it a try if traversal mutations happen significantly less often. The examples are `CopyOnWriteArrayList` and `CopyOnWriteArraySet`.

## Undefined

Undefined behavior can be found in legacy collections such as `Vector` and `Hashtables`. Both of them have standard iterators with fail-fast behavior, but they also expose the implementations of the `Enumeration` interface, which do not define behavior when a concurrent modification occurs. You might see some items being repeated or skipped, or even some weird exceptions flying around. It's better not to play with this beast!

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
