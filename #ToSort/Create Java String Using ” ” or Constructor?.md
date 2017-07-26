# Create Java String Using ” ” or Constructor?

_Captured: 2015-11-22 at 13:25 from [www.programcreek.com](http://www.programcreek.com/2014/03/create-java-string-by-double-quotes-vs-by-constructor/)_

In Java, a string can be created by using two methods:

What is the difference between using double quotes and using constructor?

**1\. Double Quotes vs. Constructor**

This question can be answered by using two simple code examples.

Example 1:

`a==b` is true because `a` and `b` are referring to the same string literal in the [method area](http://www.programcreek.com/2013/04/jvm-run-time-data-areas/). The memory references are the same.

When the same string literal is created more than once, only one copy of each distinct string value is stored. This is called "_string interning_". All compile-time constant strings in Java are automatically interned.

Example 2:

`c==d` is false because `c` and `d` refer to two different objects in the heap. Different objects always have different memory references.

This diagram illustrate the two situations above:

![constructor vs double quotes Java String - New Page](http://www.programcreek.com/wp-content/uploads/2014/03/constructor-vs-double-quotes-Java-String-New-Page-650x324.png)

> _2. Run-Time String Interning_

Thanks to LukasEder (his comment below):

String interning can still be done at run-time, even if two strings are constructed with constructors:

**3\. When to Use Which**

Because the literal "abcd" is already of type String, using constructor will create an extra unnecessary object. Therefore, double quotes should be used if you just need to create a String.

If you do need to create a new object in the heap, constructor should be used. [Here](http://www.programcreek.com/2013/09/the-substring-method-in-jdk-6-and-jdk-7/) is a use case.
