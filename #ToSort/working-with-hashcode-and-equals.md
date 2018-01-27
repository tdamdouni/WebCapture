# Working With hashcode() and equals()

_Captured: 2018-01-06 at 19:35 from [dzone.com](https://dzone.com/articles/working-with-hashcode-and-equals-in-java?edition=350091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-05)_

By default, the Java super class **_java.lang.Object _**provides two important methods for comparing objects: **_equals()_** and _**hashcode()**_. These methods become very useful when implementing interactions between several classes in large projects. In this article, we will talk about the relationship between these methods, their default implementations, and the circumstances that force developers to provide a custom implementation for each of them.

## Method Definition and Default Implementation

  * _**equals(Object obj):**_ a method provided by **_java.lang.Object_** that indicates whether some other object passed as an argument is **_"equal to"_** the current instance. The default implementation provided by the JDK is based on memory location -- two objects are equal if and only if they are stored in the same memory address.

  * **_hashcode():_ **a method provided by _**java.lang.Object** _that returns an integer representation of the object memory address. By default, this method returns a random integer that is unique for each instance. This integer might change between several executions of the application and won't stay the same.

## The Contract Between equals() and hashcode()

The default implementation is not enough to satisfy business needs, especially if we're talking about a huge application that considers two objects as equal when some business fact happens. In some business scenarios, developers provide their own implementation in order to force their own equality mechanism regardless the memory addresses.

As per the Java documentation, developers should override both methods in order to achieve a fully working equality mechanism -- it's not enough to just implement the **_equals()_** method.

> If two objects are equal according to the **_equals(Object)_** method, then calling the _**hashcode()**_ method on each of the two objects must produce the same integer result.

In the following sections, we provide several examples that show the importance of overriding both methods and the drawbacks of overriding **_equals()_** without **_hashcode()_**.

## Practical Example

We define a class called _**Student**_ as the following:
    
    
    package com.programmer.gate.beans;

For testing purposes, we define a main class **_HashcodeEquals _**that checks whether two instances of **_Student_** (who have the exact same attributes) are considered as equal.
    
    
        public static void main(String[] args) {
    
    
            Student alex1 = new Student(1, "Alex");
    
    
            Student alex2 = new Student(1, "Alex");
    
    
            System.out.println("alex1 hashcode = " + alex1.hashCode());
    
    
            System.out.println("alex2 hashcode = " + alex2.hashCode());
    
    
            System.out.println("Checking equality between alex1 and alex2 = " + alex1.equals(alex2));

Output:

Although the two instances have exactly the same attribute values, they are stored in different memory locations. Hence, they are not considered equal as per the default implementation of _**equals()**_. The same applies for **_hashcode()_** -- a random unique code is generated for each instance.

## Overriding equals()

For business purposes, we consider that two students are equal if they have the same _ID_, so we override the _**equals()** _method and provide our own implementation as the following:

In the above implementation, we are saying that two students are equal if and only if they are stored in the same memory address **OR **they have the same ID. Now if we try to run _**HashcodeEquals**,_we will get the following output:

As you noticed, overriding _**equals() **_with our custom business forces Java to consider the ID attribute when comparing two **_Student_** objects.

### equals() With ArrayList

A very popular usage of **_equals() _**is defining an array list of **_Student_** and searching for a particular student inside it. So we modified our testing class in order the achieve this.

After running the above test, we get the following output:

## Overriding hashcode()

Okay, so we override **_equals() _**and we get the expected behavior -- even though the hash code of the two objects are different. So, what's the purpose of overriding **_hashcode()_**?

### equals() With HashSet

Let's consider a new test scenario. We want to store all the students in a **_HashSet_**, so we update **_HashcodeEquals _**as the following:

If we run the above test, we get the following output:

WAIT!! We already override **_equals() _**and verify that _alex1_ and _alex2 _are equal, and we all know that **_HashSet_** stores unique objects, so why did it consider them as different objects ?

**_HashSet_** stores its elements in memory buckets. Each bucket is linked to a particular hash code. When calling _students.add(alex1)_, Java stores _alex1_ inside a bucket and links it to the value of _alex1.hashcode()_. Now any time an element with the same hash code is inserted into the set, it will just replace _alex1._ However, since _alex2_ has a different hash code, it will be stored in a separate bucket and will be considered a totally different object.

Now when **_HashSet_** searches for an element inside it, it first generates the element's hash code and looks for a bucket which corresponds to this hash code.

Here comes the importance of overriding _**hashcode()**, _so let's override it in **_Student_** and set it to be equal to the ID so that students who have the same ID are stored in the same bucket:

Now if we try to run the same test, we get the following output:

See the magic of **_hashcode()_**! The two elements are now considered as equal and stored in the same memory bucket, so any time you call _contains()_ and pass a student object holding the same hash code, the set will be able to find the element.

The same is applied for **_HashMap, HashTable_**, or any data structure that uses a hashing mechanism for storing elements.

## Conclusion

In order to achieve a fully working custom equality mechanism, it is mandatory to override _**hashcode()** _each time you override **_equals()._** Follow the tips below and you'll never have leaks in your custom equality mechanism:

  * If two objects are equal, they MUST have the same hash code.
  * If two objects have the same hash code, it doesn't mean that they are equal.
  * Overriding **_equals() _**alone will make your business fail with hashing data structures like: **_HashSet, HashMap, HashTable_** ... etc.
  * Overriding **_hashcode() _**alone doesn't force Java to ignore memory addresses when comparing two objects.
