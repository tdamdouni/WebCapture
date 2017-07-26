# ArrayList vs. LinkedList vs. Vector

_Captured: 2015-11-22 at 13:53 from [www.programcreek.com](http://www.programcreek.com/2013/03/arraylist-vs-linkedlist-vs-vector/)_

**1\. List Overview**

List, as its name indicates, is an ordered sequence of elements. When we talk about List, it is a good idea to compare it with Set which is a set of unique and unordered elements. The following is the class hierarchy diagram of Collection. From the hierarchy diagram you can get a general idea of Java Collections.

![](http://www.programcreek.com/wp-content/uploads/2009/02/java-collection-hierarchy.jpeg)

> _2. ArrayList vs. LinkedList vs. Vector_

From the hierarchy diagram, they all implement List interface. They are very similar to use. Their main difference is their implementation which causes different performance for different operations.

ArrayList is implemented as a resizable array. As more elements are added to ArrayList, its size is increased dynamically. It's elements can be accessed directly by using the get and set methods, since ArrayList is essentially an array.

LinkedList is implemented as a double linked list. Its performance on add and remove is better than Arraylist, but worse on get and set methods.

Vector is similar with ArrayList, but it is synchronized.

ArrayList is a better choice if your program is thread-safe. Vector and ArrayList require more space as more elements are added. Vector each time doubles its array size, while ArrayList grow 50% of its size each time. LinkedList, however, also implements Queue interface which adds more methods than ArrayList and Vector, such as offer(), peek(), poll(), etc.

Note: The default initial capacity of an ArrayList is pretty small. It is a good habit to construct the ArrayList with a higher initial capacity. This can avoid the resizing cost.

**3\. ArrayList example**
    
    
    ArrayList<Integer> al = new ArrayList<Integer>();
    al.add(3);
    al.add(2);		
    al.add(1);
    al.add(4);
    al.add(5);
    al.add(6);
    al.add(6);
     
    Iterator<Integer> iter1 = al.iterator();
    while(iter1.hasNext()){
    	System.out.println(iter1.next());
    }

**4\. LinkedList example**
    
    
    LinkedList<Integer> ll = new LinkedList<Integer>();
    ll.add(3);
    ll.add(2);		
    ll.add(1);
    ll.add(4);
    ll.add(5);
    ll.add(6);
    ll.add(6);
     
    Iterator<Integer> iter2 = ll.iterator();
    while(iter2.hasNext()){
    	System.out.println(iter2.next());
    }

As shown in the examples above, they are similar to use. The real difference is their underlying implementation and their operation complexity.

**5\. Vector **

Vector is almost identical to ArrayList, and the difference is that Vector is synchronized. Because of this, it has an overhead than ArrayList. Normally, most Java programmers use ArrayList instead of Vector because they can synchronize explicitly by themselves.

**6\. Performance of ArrayList vs. LinkedList**

The time complexity comparison is as follows:

![arraylist-vs-linkedlist-complexity](http://www.programcreek.com/wp-content/uploads/2013/03/arraylist-vs-linkedlist-complexity.png)

* add() in the table refers to add(E e), and remove() refers to remove(int index)

  * ArrayList has O(n) time complexity for arbitrary indices of add/remove, but O(1) for the operation at the end of the list.
  * LinkedList has O(n) time complexity for arbitrary indices of add/remove, but O(1) for operations at end/beginning of the List.

I use the following code to test their performance:
    
    
    ArrayList<Integer> arrayList = new ArrayList<Integer>();
    LinkedList<Integer> linkedList = new LinkedList<Integer>();
     
    // ArrayList add
    long startTime = System.nanoTime();
     
    for (int i = 0; i < 100000; i++) {
    	arrayList.add(i);
    }
    long endTime = System.nanoTime();
    long duration = endTime - startTime;
    System.out.println("ArrayList add:  " + duration);
     
    // LinkedList add
    startTime = System.nanoTime();
     
    for (int i = 0; i < 100000; i++) {
    	linkedList.add(i);
    }
    endTime = System.nanoTime();
    duration = endTime - startTime;
    System.out.println("LinkedList add: " + duration);
     
    // ArrayList get
    startTime = System.nanoTime();
     
    for (int i = 0; i < 10000; i++) {
    	arrayList.get(i);
    }
    endTime = System.nanoTime();
    duration = endTime - startTime;
    System.out.println("ArrayList get:  " + duration);
     
    // LinkedList get
    startTime = System.nanoTime();
     
    for (int i = 0; i < 10000; i++) {
    	linkedList.get(i);
    }
    endTime = System.nanoTime();
    duration = endTime - startTime;
    System.out.println("LinkedList get: " + duration);
     
     
     
    // ArrayList remove
    startTime = System.nanoTime();
     
    for (int i = 9999; i >=0; i--) {
    	arrayList.remove(i);
    }
    endTime = System.nanoTime();
    duration = endTime - startTime;
    System.out.println("ArrayList remove:  " + duration);
     
     
     
    // LinkedList remove
    startTime = System.nanoTime();
     
    for (int i = 9999; i >=0; i--) {
    	linkedList.remove(i);
    }
    endTime = System.nanoTime();
    duration = endTime - startTime;
    System.out.println("LinkedList remove: " + duration);

And the output is:
    
    
    ArrayList add:  13265642
    LinkedList add: 9550057
    ArrayList get:  1543352
    LinkedList get: 85085551
    ArrayList remove:  199961301
    LinkedList remove: 85768810
    

![arraylist-vs-linkedlist](http://www.programcreek.com/wp-content/uploads/2013/03/arraylist-vs-linkedlist1.png)

The difference of their performance is obvious. LinkedList is faster in add and remove, but slower in get. Based on the complexity table and testing results, we can figure out when to use ArrayList or LinkedList. In brief, LinkedList should be preferred if:

  * there are no large number of random access of element
  * there are a large number of add/remove operations
