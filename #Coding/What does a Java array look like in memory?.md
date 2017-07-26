# What does a Java array look like in memory?

_Captured: 2015-11-22 at 13:26 from [www.programcreek.com](http://www.programcreek.com/2013/04/what-does-a-java-array-look-like-in-memory/)_

Arrays in Java store one of two things: either primitive values (int, char, ...) or references (a.k.a pointers).

When an object is creating by using "new", memory is allocated on the heap and a reference is returned. This is also true for arrays, since arrays are objects.

**1\. Single-dimension Array**

The int[] arr is just the reference to the array of 3 integer. If you create an array with 10 integer, it is the same - an array is allocated and a reference is returned.

![one-dimension-array-in-java](http://www.programcreek.com/wp-content/uploads/2013/04/one-dimension-array-in-java.png)

**2\. Two-dimensional Array**

How about 2-dimensional array? Actually, we can only have one dimensional arrays in Java. 2D arrays are basically just one dimensional arrays of one dimensional arrays.

![Array-in-Memory-Java](http://www.programcreek.com/wp-content/uploads/2013/04/Array-in-Memory-Java.png)

> _Multi-dimensional arrays use the name rules._

**3\. Where are they located in memory?**

Arrays are also objects in Java, so how an object looks like in memory applies to an array.

As we know that [JVM runtime data areas ](http://www.programcreek.com/2013/04/jvm-run-time-data-areas/)include heap, JVM stack, and others. For a simple example as follows, let's see where the array and its reference are stored.
    
    
    class A {
    	int x;
    	int y;
    }
     
    ...
     
    public void m1() {
    	int i = 0;
    	m2();
    }
     
    public void m2() {
    	A a = new A();
    }
     
    ...

With the above declaration, let's invoke m1() and see what happens:

  1. When m1 is invoked, a new frame (Frame-1) is pushed into the stack, and local variable i is also created in Frame-1. 
  2. Then m2 is invoked inside of m1, another new frame (Frame-2) is pushed into the stack. In m2, an object of class A is created in the heap and reference variable is put in Frame-2. Now, at this point, the stack and heap looks like the following:
![Java-array-in-memory](http://www.programcreek.com/wp-content/uploads/2013/04/Java-array-in-memory.png)

Arrays are treated the same way like objects, so how array locates in memory is straight-forward.
