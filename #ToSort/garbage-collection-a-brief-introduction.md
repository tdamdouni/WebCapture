# Garbage Collection: A Brief Introduction

_Captured: 2018-03-31 at 19:07 from [dzone.com](https://dzone.com/articles/garbage-collection-a-brief-introduction?edition=371194&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-31)_

In this blog, I'm going to talk about how used memory is freed in programming languages like C or C++ that do not offer automatic garbage collection, the disadvantages of that process and how the garbage collector automatically helps in resolving this issue.

Memory management plays an important role in determining the performance of an application. It involves recognizing when allocated objects are no longer needed, deallocating the memory used by such objects, and eventually making it available for further use in allocating objects. Managing memory manually is a nontrivial and complex task as it can cause unexpected or erroneous program behavior and crashes.

### **Deallocating Memory Explicitly**

Does handling memory manually sound great? Wait! We'll see in a bit.

Traditional programming languages like C offers to deallocate the used memory manually. It is performed using the `free() `function. Let's have a look at the below example,
    
    
    int *ptr = (int*) malloc(sizeof(int));

Here, the ptr is allocated memory using `malloc()` function and after using it programmer deallocate it using `free()` function.

### **Problems in Managing Memory Explicitly**

Following are the problems that occur while managing memory explicitly:

  1. **Memory leaks -** Consider a program in which you are trying to deallocate the memory used by the linked list. Suppose there is a small flaw in the part of the code that handles the deallocation of the memory of the head of a list. Then the remaining elements of the list will no longer be referenced. It will result in loss of some bytes of memory which cannot be recovered or used in future. These small losses are called memory leaks. After hundreds of iterations, all the remaining will be consumed and eventually, the program will crash.
  2. **Dangling references - **When the programmer deallocates the memory used by an object to which any other object still has a reference, then trying to access the original object would result in unpredictable behavior. Suppose there are two objects referring to the same memory location.  
![dangling reference 1](https://knoldus.files.wordpress.com/2018/01/dangling-reference-1.jpg)

But accidentally developer deletes the obj1 and deallocate the memory then accessing obj2 would not give desired value.

![dangling reference 2](https://knoldus.files.wordpress.com/2018/01/dangling-reference-2.png)

Thus, managing memory explicitly will double the development effort for a more complex program.

### **Garbage Collection**

Performance of the garbage collector is one key feature to the overall performance of any Java application. In Java, we don't have to explicitly manage the lifecycle of objects, i.e. objects are created when needed, and when the object is no longer in use, the JVM automatically frees the object. An object is eligible for garbage collection when no live thread can access it. The garbage collection revolves around ensuring that heap has enough memory available for allocating objects.

The basic process of garbage collection is explained below :

**Step 1: Marking**  
In this step, the garbage collector identifies which objects are used and which objects are not.

![marking](https://knoldus.files.wordpress.com/2018/01/marking.png)

**Step 2: Normal Deletion**  
The garbage collector removes the unused objects and reclaims the free space which can be used for further allocating other objects.

![normal deletion](https://knoldus.files.wordpress.com/2018/01/normal-deletion.png)

**Step 3: Deletion with Compaction**  
Since there can be free spaces left in small chunks at the different location of the heap when the objects are freed, there might be a chance that enough memory is not available in any one contiguous area for allocating objects that require large memory. Thus, to avoid such a memory fragmentation scenario, the garbage collector does the process of compaction of memory.

![deletion with compaction](https://knoldus.files.wordpress.com/2018/01/deletion-with-compaction.png)

## How to Explicitly Make Objects Eligible for Garbage Collection

In this section, we'll learn how to explicitly make objects eligible for garbage collection using the actual code.

  1. **Assign `null` to a Reference Variable**  
  
By assigning `null` to a reference of an object will make it no longer accessible  
  
  
Here the Integer object is not eligible for collection![assigning null 1](https://knoldus.files.wordpress.com/2018/01/assigning-null-1.jpg?w=640)

![assigning null 2](https://knoldus.files.wordpress.com/2018/01/assigning-null-2.jpg?w=640)

At the point where an object, x, is assigned null it will make it eligible for garbage collection and accumulated to the heap once the garbage collector runs for the cleanup process.

#### 2.** Reassigning a Reference Variable**

At this point, the object referred to by s1 is not eligible for garbage collection

![reassigning reference 1](https://knoldus.files.wordpress.com/2018/01/reassigning-reference-1.jpg?w=640)

![reassigning reference 2](https://knoldus.files.wordpress.com/2018/01/reassigning-reference-2.png?w=640)

Now the object referred earlier by s1 is eligible for garbage collection as it cannot be accessed by any thread.

Another scenario that we'll look into is when any other reference variable also points to the local variable are returned by a method.

We know that the lifetime of a local variable is up until the method is executing. Thus, an object created in the method will be eligible for garbage collection once the same method has completed its execution. The only exception is when an object is returned from the method. Its reference may be assigned to some reference variable in the method that called it, then the returned object will not be eligible for garbage collection. This example will give the better understanding,

Here, name and s1 are two local variable present in `makeStudentObject()` method. Student object, s1, is returned by the method and it being `inside main()` method so it will not be eligible for garbage collection. But the `StringBuffer` object, `name`, will be eligible for garbage collection as it not returned by a method. In other words, s1 is still alive and the name did not survive. Sad!

#### 3\. **Making Anonymous Objects**

Since the reference to an anonymous object is not stored anywhere, it can't be accessed by any thread. Hence it can be regarded as another way of making objects which will be eligible for garbage collection. To understand it better let's go through the below example.

#### 4\. **Island of Isolation**

Objects can become eligible for garbage collection, even if they have correct references. For example, a class has an instance variable that is a reference variable to another instance of the same class. Suppose there are three objects and they refer to each other (as shown below in the figure). If the original references to the objects are removed, then even if they have a valid reference, they won't be accessible. This condition is known as island of isolation.

![island of isolation](https://knoldus.files.wordpress.com/2018/01/island-of-isolation.png?w=492&h=371)

**_Using the built-in methods for Garbage Collection_**

Should we use any predefined method for the garbage collection? NO! You might be wondering why when there is `System.gc()` or `Runtime.gc()` method available. It's because invoking either of them does not guarantee all the unused objects will be removed. It will only make a request to JVM for some garbage collection.

## **The `finalize()` method**

Java provides a `finalize()` method present in Object class which you can override for objects to do some task before it gets deleted by the garbage collector. But it is recommended not to use `finalize()` method as again it does not guarantee that it will run on every object. In general,

  1. For each object, `finalize()` method will be invoked at most ONCE by the garbage collector.
  2. The `finalize()` can severely affect the performance of the application.
  3. Any Exception thrown by `finalize()` method is ignored by GC thread and it will not be propagated further.

In my next blog, I will be discussing why heap is divided into different generations, different garbage collectors, etc. Until then, learn and share !!
