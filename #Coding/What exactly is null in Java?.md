# What exactly is null in Java?

_Captured: 2015-11-22 at 13:28 from [www.programcreek.com](http://www.programcreek.com/2013/12/what-exactly-is-null-in-java/)_

Let's start from the following statement:

**1\. What exactly does this statement do?**

Recall what is a variable and what is a value. A common metaphor is that a variable is similar to a box. Just as you can use a box to store something, you can use a variable to store a value. When declaring a variable, we need to set its type.

There are two major categories of types in Java: primitive and reference. Variables declared of a primitive type store values; variables declared of a reference type store references. In this case, the initialization statement declares a variables "x". "x" stores String reference. It is null here.

The following visualization gives a better sense about this concept.

![what-is-null](http://www.programcreek.com/wp-content/uploads/2013/12/what-is-null-150x150.png)

> _If x = "abc", it looks like the following:_

![variable-reference](http://www.programcreek.com/wp-content/uploads/2013/12/variable-reference-300x144.png)

**2\. What exactly is null in memory?**

What exactly is null in memory? Or What is the null value in Java?

First of all, null is not a valid object instance, so there is no memory allocated for it. It is simply a value that indicates that the object reference is not currently referring to an object.

From [JVM Specifications](http://docs.oracle.com/javase/specs/jvms/se7/html/jvms-2.html#jvms-2.4):

> The Java Virtual Machine specification does not mandate a concrete value encoding null.

I would assume it is all zeros of something similar like itis on other C like languages.

**3\. What exactly is x in memory?**

Now we know what null is. And we know a variable is a storage location and an associated symbolic name (an identifier) which contains some value. Where exactly x is in memory?

From [the diagram of JVM run-time data areas](http://www.programcreek.com/2013/04/jvm-run-time-data-areas/), we know that since each method has a private stack frame within the thread's steak, the local variable are located on that frame.

References:

1\. [Variables, Operators, and Expressions](http://www.cs.cmu.edu/~pattis/15-1XX/15-200/lectures/voe/lecture.html)  
2\. [Variable](http://en.wikipedia.org/wiki/Variable_\(computer_science\))  
3\. [JVM Specifications](http://docs.oracle.com/javase/specs/jvms/se7/html/jvms-2.html#jvms-2.4)
