# A Look at Java Collections

_Captured: 2017-03-01 at 02:56 from [dzone.com](https://dzone.com/articles/java-collections?edition=271922&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-28)_

Navigate the Maze of the End-User Experience and pick up this [APM Essential guide](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574).

The [Java Collections framework](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/index.html) is an architecture for storing, managing, and manipulating collections of objects. It provides many data structures and algorithms commonly used for dealing with collections -- searching and sorting, for instance. Many details about storing objects are abstracted away (meaning you do not have to deal with it in code). A unified interface is provided to manipulate them, for example for adding and removing entries.

## The Collections Hierarchy

The Collections Framework is organized into a class hierarchy, which can be understood at a glance from the picture below.

_Note: The hierarchy shown below includes only the most common and useful classes and interfaces. Some have been skipped to facilitate easier understanding._

![Image title](http://www.novixys.com/blog/wp-content/uploads/2017/02/Collections-768x480.png)

> _Java Collections Framework_

## A Brief Introduction to Collections

  1. At the root of the hierarchy is _[Iterable_ ](https://docs.oracle.com/javase/8/docs/api/java/lang/Iterable.html)which, as the name indicates, provides for iterating over the collection.
  2. The next is the [Collection ](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html)interface, which provides most of the methods representing a collection. These methods include providing for adding and removing elements, checking if the collection includes an element, and obtaining the number of elements in the collection.
  3. A _[Set_ ](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html)contains no duplicate elements. Common implementations are: 
    * _[HashSet_ ](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html)does not provide any ordering of the elements in the _Set_.
    * _[LinkedHashSet_ ](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html)maintains a double-linked list of the elements and thus provides a predictable iteration order.
    * _[TreeSet_ ](https://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html)which uses a comparator function to maintain element ordering.
  4. A _[List](https://docs.oracle.com/javase/8/docs/api/java/util/List.html)_ is an ordered sequential collection. Concrete implementations include: 
    * _[Vector_ ](https://docs.oracle.com/javase/8/docs/api/java/util/Vector.html)is also a re-sizable array similar to an _ArrayList_. Use it only when you need thread-safety and synchronization.
    * _[Stack_ ](https://docs.oracle.com/javase/8/docs/api/java/util/Stack.html)is a LIFO(Last-In-First-Out) array. A subclass of _Vector_ and is also thread-safe.
    * _[LinkedList_ ](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html)is a doubly linked list of elements. Offers fast adds and removes from intermediate positions. Note that this class also implements the _[Deque_ ](https://docs.oracle.com/javase/8/docs/api/java/util/Deque.html)interface.
  5. A _[Queue](https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html)_ orders elements in a FIFO (First-In-First-Out) order. The _[add()](https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html#add-E-)_ method adds elements at the tail and _[remove()](https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html#remove--)_ removes elements from the head. Typical usage is storage to hold elements before processing in the order of receipt.
  6. On the other hand, a _[Deque](https://docs.oracle.com/javase/8/docs/api/java/util/Deque.html)_ (Double-Ended-Queue) can add and remove elements at both ends. 
    * A _LinkedList_ is also a _Deque_.

This article presented a brief overview of the Java Collections hierarchy. In further articles, we explore the various collection classes and their usage.

Thrive in the application economy with [an APM model that is strategic](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574). Be E.P.I.C. with CA APM. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574).
