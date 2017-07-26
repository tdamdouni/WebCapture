# All About the Singleton

_Captured: 2017-06-07 at 01:21 from [dzone.com](https://dzone.com/articles/all-about-the-singleton?edition=304133&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-06)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

The Singleton design pattern is one of the simplest design patterns: It involves only one class throughout the application that is responsible for instantiating itself to make sure it creates no more than one instance. At the same time, it provides a global point of access to that instance. In this case, the same instance can be used from everywhere, being impossible to directly invoke the constructor each time.

There are various kinds of implementations, and I am going to explain them one by one.

## Eager Initialization

In eager initialization, the instance of Singleton Class is created at the time of class loading. This is the easiest method to create a Singleton class, but it has the drawback of the instance being created even though client application might not be using it.

## Static Block Initialization

Static block initialization is similar to eager initialization, except that the instance of the class is created in the static block that provides the option for exception handling.

## Lazy Initialization

Lazy initialization is a method to implement the Singleton pattern to create an instance in the global access method.

The above implementation works fine in case of a single-threaded environment, but when it comes to multithreaded systems, it can cause issues if multiple threads are inside the if loop at the same time. It will destroy the singleton pattern, and both threads will get the different instances of the singleton class.

## Thread-Safe Singletons

The easier way to create a thread-safe singleton class is to make the global access method synchronized so that only one thread can execute this method at a time. The general implementation of this approach is like the following class:

## Double-Checked Locking

The above implementation works fine and provides thread-safety, but it reduces performance because of the cost associated with the synchronized method, although we need it only for the first few threads that might create the separate instances (Read: Java Synchronization). To avoid this extra overhead every time, the double-checked locking principle is used. In this approach, the synchronized block is used inside the if condition with an additional check to ensure that only one instance of the singleton class is created. Let's see how. Suppose there are two threads, T1 and T2. Both come to create an instance and execute "instance==null". Now both threads have identified the instance variable as null and thus assume they must create an instance. They sequentially go to a synchronized block and create the instances. In the end, we have two instances in our application.

## Bill Pugh Solution

Bill Pugh was the main force behind Java memory model changes. His principle "Initialization-on-demand holder idiom" also uses static blocks but in a different way. It suggests using a static inner class. Notice the private inner static class that contains the instance of the singleton class. When the singleton class is loaded, the SingletonHelper class is not loaded into memory, and only when someone calls the getInstance method, does this class get loaded and create the Singleton class instance. This is the most widely used approach for Singleton classes, as it doesn't require synchronization. I am using this approach in many of my projects, and it's easy to understand and implement, too.

## Enum Singleton

To overcome this situation with Reflection, Joshua Bloch suggests the use of Enum to implement the Singleton design pattern, as Java ensures that any enum value is instantiated only once in a Java program. Since Java Enum values are globally accessible, so is the Singleton. The drawback is that the enum type is somewhat inflexible; for example, it does not allow lazy initialization.

## Using Reflection to Destroy Singleton Patterns

Reflection can be used to destroy all the above Singleton implementation approaches. Let's see this with an example class:
    
    
        public static void main(String[] args) {

When you run the above test class, you will notice that the hashcode of both the instances is not same, whcih destroys the Singleton pattern. Reflection is very powerful and used in a lot of frameworks like Spring and Hibernate.

## Serialization and Singleton

Sometimes in distributed systems, we need to implement a Serializable interface in our Singleton class so that we can store its state in a file system and retrieve it at a later point in time. Here is a small Singleton class that also implements a Serializable interface.

The problem with the above-serialized singleton class is that whenever we deserialize it, it will create a new instance of the class. Let's see it with a simple program.
    
    
            System.out.println("instanceOne hashCode="+instanceOne.hashCode());
    
    
            System.out.println("instanceTwo hashCode="+instanceTwo.hashCode());

**It destroys the Singleton design pattern**. To overcome this scenario, all we need to do is provide the implementation of the readResolve() method. This method will be invoked when you \ deserialize the object. Inside this method, you must return the existing instance to ensure a single instance application-wide.

## Examples of Singleton Design Patterns

### Hardware Interface Access

The use of a Singleton depends on the requirements. However, practically, Singletons can be used in the case of external hardware resource usage limitations -- for example, hardware printers where the print spooler can be made into a Singleton to avoid multiple concurrent accesses and creating a deadlock.

### Logger

Similarly, a Singleton is a good potential candidate for using in log file generation. Imagine an application where the logging utility has to produce one log file based on the messages received from the users. If there are multiple client applications using this logging utility class, they might create multiple instances of this class -- and it can potentially cause issues during concurrent access to the same logger file. We can use the logger utility class as a Singleton and provide a global point of reference.

This is another potential candidate for Singleton pattern because this has a performance benefit. It prevents multiple users from repeatedly accessing and reading the configuration file or properties file. It creates a single instance of the configuration file, which can be accessed by multiple calls concurrently, as it will provide static config data loaded into in-memory objects. The application only reads from the configuration file the first time and, thereafter, from the second call onward, the client applications read the data from in-memory objects.

### Cache

We can use a cache as a Singleton object, as it can have a global point of reference and, for all future calls to the cache object, the client application will use the in-memory object.

You can [download ](https://github.com/Vishnu24/Design-Patterns)the complete reference with source code samples. It also contains the [complete guide](https://github.com/Vishnu24/Design-Patterns/wiki/Singleton-Pattern) that will help you to go through with this.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
