# Are Changing Programming Paradigms Underrated by Developers?

_Captured: 2018-08-03 at 07:31 from [dzone.com](https://dzone.com/articles/are-changing-programming-paradigms-underrated-by-d?edition=388194&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-02)_

Get the Edge with a Professional Java IDE. [30-day free trial](https://dzone.com/go?i=255333&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-preroll%26utm_campaign%3Didea).

In all the chatter around architecture and design patterns when building or upgrading a software system, the fundamental programming paradigms are becoming second fiddle. To preempt any impediments in execution and long-term maintainability, the importance of programming paradigm-related decisions should not be trivialized. This is an aspect to be considered when bootstrapping a new project.

This article aims to provide a new perspective on programming paradigms to help in the decision making process of selecting languages and constructs, which form the building blocks for your solution. It traverses through the basic programming paradigms, the latest trends, and how languages evolve and embrace new paradigms. The article takes latest evolutions in Java as a reference and how it has evolved from an object-oriented language to embracing functional and reactive programming styles, as it steps into its latest long-term release -- Java 11.

## **What Is a Programming Paradigm?**

A programming paradigm is a style of creating or using the structure and elements of a program. It can change from one programming language to another. Often times, programming languages change, embracing newer programming paradigms.

## **Creation of New Programming Paradigms or Adoption of Existing Paradigms**

The increased use of technology is the primary driver that leads to how the applications serve its users. It leads to businesses demanding better performance and more secure, responsive applications. With improved hardware designs and decreasing hardware costs, designers can explore the options that were not previously available.

For instance, though the idea of functional programming floated around 22 years ago, it has gained momentum in recent years. Computer systems with multi-core processors are getting cheaper and, hence, accessible to more business users, which is driving its adoption. Functional programs can efficiently execute code parallel on multiple cores.

A similar trend is where a change in the usage and behavioral patterns of users have pushed the creation of stimuli-based reactive programming paradigms. It supports the creation of responsive applications that deliver high performance and are resilient and scalable.

## **Challenges in Adopting a Programming Paradigm**

Programming paradigms are analogous to habits. You form a habit by practicing the same behavior over a period of time. The longer you practice it, the more difficult it is to unlearn it and complete the same task in another manner.

While it is simple to understand the syntax of a programming language, the difficult part is to apply alternate thinking (a programming paradigm) to devise a solution to a problem.

It takes a lot of conscious effort to pause thinking in a certain way and adopt a newer thinking style.

## **Why Should You Know Multiple Programming Paradigms?**

Business requirements vary over a wide spectrum -- knowing multiple programming paradigms can help you select the most appropriate programming language for implementing the solution. The nature of the problem is that it would also affect the adoption of a programming paradigm.

An application ecosystem is composed of multiple elements. As an architect, leader, or developer, you must be aware of the feasibility of interoperability between these entities, especially if they use different programming paradigm.

This article doesn't cover _all_ the known paradigms, for instance, reactive functional, aspect-oriented, data flow, and more. There are other published resources available for these.

Let's cover some of the popular programming paradigms.

### **Imperative Programming Paradigm**

With the imperative programming paradigm, you specify the detailed steps of how a solution is implemented. The earliest imperative languages were the machine languages. Therefore, the CPU instructions are imperative.

This programming paradigm is essential to know if you are developing compilers or other programs that interact with low-level code. A lot of high-level languages, like Java, Python, C, and C++, can also include imperative programming in their functions or methods.

Here's an example code, which iterates through a list of integer arrays and finds the largest number:
    
    
    1. int[] numbers = new int[]{12, 19, 27, 28, 2, 1};
    
    
    3. for (int i = 0; i < numbers.length; i++) {

The preceding code specifies _all_ the details to find the largest number from the integer array -- it starts by defining variables to store the integer array and largest number. It defines a loop with the starting value and exit condition, incrementing the value by 1 after each visit to the array element. Within the loop, it compares the value of the previously stored larger number with the visiting array element. If the previously stored larger number is small, it stores the new value. After the loop exits, it outputs the value of the variable that stores the largest number.

### **Procedural Programming Paradigm**

The procedural programming paradigm encourages the creation of smaller and reusable procedures or methods in your code.

You can define smaller methods in a lot of high-level languages, like Java, C, C++, C#, Python, and many other languages. Smaller methods make your code more readable (which is very important), clean up your code, and identify spaghetti code within a comparatively longer method.

The following code modifies the code written in listing 1, defining a method `larger()`, which is called from the main code:
    
    
    int[] numbers = new int[]{12, 19, 27, 28, 2, 1};
    
    
    for (int i = 0; i < numbers.length; i++) {
    
    
    private static int larger(int a, int b) {
    
    
        return (a > b ? a : b);

> In Java, you can't define code outside a method or a code block. So, the code defined above the method `larger()` is ideally defined in another method. 

The preceding code creates a method `larger()` and calls it from the main code. You could also go a step further and create another method `findLargest()`, as follows:
    
    
    int[] numbers = new int[]{12, 19, 27, 28, 2, 1};
    
    
    private static int larger(int a, int b) {
    
    
        return (a > b ? a : b);
    
    
        for (int i = 0; i < arr.length; i++) {
    
    
            largest = larger(largest, arr[i]);

With smaller methods, the preceding method becomes easy to read and understand.

### **Object-Oriented Programming Paradigm**

The object-oriented programming paradigm models the real world. It proposes the creation of templates (or classes) which can define the state and behavior of the instances they model. The instances interact with each other by sending them messages via methods.

This programming paradigm defines four principles:

  * **Abstraction** -- proposes to eliminate the irrelevant details and supports the inclusion of essential details
  * **Encapsulation** -- encapsulates the state of the instance, hiding it from the outside world
  * **Inheritance** -- groups the similar
  * **Polymorphism** -- support specialized behavior for same behavior name.

Let's modify the coding example from code listing 3 and add classes to it. Here are the steps of modification:

  * Define a new class `NumberGenerator`
  * Create instance variable `myNumbers` in `NumberGenerator` to store array of numbers
  * Define methods - `larger()` and `findLargest()` , compare numbers
  * Instantiate `NumberGenerator` in another class
  * Call relevant methods

Here's the modified code:
    
    
            myNumbers = new int[]{12, 19, 27, 28, 2, 1};      
    
    
        private int larger(int a, int b) {        // returns the larger number
    
    
            return (a > b ? a : b);
    
    
            int largest = myNumbers[0];           // 
    
    
            for (int i = 0; i < myNumbers.length; i++) {       
    
    
                largest = larger(largest, myNumbers[i]);

Let's add a bit of complexity to the preceding code. Imagine you need to extract the behavior of the class `NumberGenerator` in an interface to decouple its behavior from its implementation. Here's the code:
    
    
        abstract int larger(int a, int b);
    
    
            int[] myNumbers = getNumbers();                       // use abstract
    
    
            for (int i = 0; i < myNumbers.length; i++) {          // methods
    
    
                largest = larger(largest, myNumbers[i]);
    
    
            intNumbers = new int[]{12, 19, 27, 28, 2, 1};
    
    
        public int larger(int a, int b) {
    
    
            return (a > b ? a : b);

The interface `NumberGenerator` in the preceding example will not work for non-integers, say, a custom class `Point`, which stores the X and Y coordinates and may define its custom algorithm to determine the larger of two `Point` instances.

Let's work with custom structures, like `Point`:
    
    
            return "[" + x + "," + y + "]";

The interface `NumberGenerator` in code listing 4 works with int values. To make it work with other types, you can use the _Generics_, passing type parameters to the `NumberGenerator`:
    
    
            for (int i = 0; i < myNumbers.length; i++) {
    
    
                largest = larger(largest, myNumbers[i]);
    
    
            points = new Point[]{new Point(12, 19), 
    
    
            if (a.x > b.x) return a;
    
    
            else if (a.y > b.y) return a;

### **Functional Programming Paradigm**

The functional programming paradigm is a style that recommends pure mathematical functions to process data, working with immutable data. It is a superset of declarative programming paradigm, which specifies _what_ needs to be done, rather than _how_ (with detailed steps).

With immutable data, the processing of data can execute in parallel over multiple cores, resulting in overall faster execution of programs. It also uses higher order functions -- functions that can be passed around as values. These functions can be passed to methods and returned from a method. Functional programming uses pure functions that always return the same output for the same set of input values -- without any side effects of mutating data.

Let's modify the code from listing 1 and use functional programming style to find the largest from an array of integers. The code retrieves a stream of integer values and then calls another function ( `max()`), which uses an internal iterator to find the largest number based on the comparison criteria defined by the `Comparator.naturalOrder()`:
    
    
    List<Integer> numbers = List.of(12, 19, 27, 28, 2, 1);

Here's another example of code that uses functional composition with streams. These include streams that return a (usually processed) stream. The code creates a list of `talk` instances and outputs the topic, where talk duration is greater than 52 minutes:
    
    
            List<Talk> talks = List.of( new Talk("Java 11", 59),     // LIST
    
    
                                        new Talk("Clean Code", 50),  // OF
    
    
                .filter(o -> o.getDuration() >= 52)  // filter : duration >= 52
    
    
                .map(e -> e.getTopic())              // get stream with Topic
    
    
                .forEach(System.out::println);       // output each element  

The order in which you process the streams is important. I've modified the preceding code by swapping the order of the `map()`and `filter()` functions on the integer stream. Do you think it will still output the same answer? Let's take a look:
    
    
            List<Talk> talks = List.of( new Talk("Java 11", 59),      // LIST
    
    
                                        new Talk("Clean Code", 50),   // OF
    
    
                .map(e -> e.getTopic())             // stream with just the Topic
    
    
                .filter(o -> o.getDuration() >= 52) // filter : duration >= 52
    
    
                .forEach(System.out::println);      // output elements 

The preceding code won't compile. The first transformation of the stream includes just the topics from the original list, so the call to the `filter()` function, which tries to call `getDuration() `method on `String `values, fails to compile.

### **Reactive Programming Paradigm**

The reactive programming paradigm is all about handling asynchronous streams of data.

The surge in the Internet users has drastically changed the needs of the applications. Today, users don't want any downtime and command minimum delays while accessing applications. Applications handle the humongous amount of data measured in Petabyte.

Different programming languages and frameworks have been providing their own solution to combat this problem. In the year 2014, ReactiveManifesto.org condensed the experience of the industry of building reactive applications in a set of features with a common vocabulary so that it could be discussed among the stakeholders (customers, programmers, architects, CTO, developer advocates, etc) without any ambiguity. These aren't an exhaustive set of features for a reactive application. It defines a starting point on what to strive for in a reactive application.

ReactiveManifesto.org outlines the following pillars of reactive applications:

  * **Responsive** -- Responsive applications strive to provide a consistent response time. Responsiveness also means locating issues quickly and correcting them.
  * **Resilient** -- A resilient system remains responsive, even in the case of a failure. This can be achieved by replication, containment, isolation, and delegation. Applications can recover from the failure by replacing a working component with the failed one. Failures are contained within boundaries so that they can be isolated and recovery delegated to external components.
  * **Elastic** -- Elastic system remains responsive during varying workloads. With increased workloads, a reactive system should allocate more resources to handle it and deallocate when no longer required.
  * **Message-driven** -- Responsive applications work with asynchronous streams of data. To ensure loose coupling between components, it uses messages. It also helps to implement back-pressure, that is, control message flow in the queues.

## **Conclusion**

This article provided a perspective on programming paradigms and how it helps in the decision making in selecting languages and constructs. This will form the building blocks for your solution. In this post, we covered the importance of the programming paradigms and the challenges with the adoption of new paradigms. It traveled through some programming paradigms, the latest trends, and how Java evolved and embraced different programming paradigms using a hands-on example.

[Get the Java IDE](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea) that understands code & makes developing enjoyable. Level up your code with IntelliJ IDEA. [Download the free trial](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea).

Topics:

java ,java 11 ,programming ,paradigms ,functional paradigms ,imperative paradigms ,object-oriented ,procedural paradigms
