# A Little Lambda Tutorial

_Captured: 2017-01-31 at 04:18 from [dzone.com](https://dzone.com/articles/a-little-lambda-tutorial?oid=twitter&utm_content=buffer1df00&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Lambda expressions are thought to be one of the biggest features in the release of Java 8, as they allow a more functional approach to Java programming. This is something that wasn't built into Java in previous versions. Java follows the object-oriented programming paradigm, which uses objects, which can store data in fields and manipulate them. Functional programming, on the other hand, is declarative and uses expressions or declarations instead of statements.

As someone who didn't particularly like functional programming while at university, I was very skeptical about even trying to use lambda expressions in Java. I didn't want to relive the pain I had endured from trying to understand what the hell was going on. But I gave it a try and I wrote this little tutorial from what I learned.

Lambda expressions are defined by:

`parameters -> expression body`

`Comparator comparator = (a,b) -> a.compareTo(b); `

It takes in a parameter or parameters and does stuff with them.

Some rules about using Lambda expressions:

  * **Type declaration is optional**: The compiler can figure out types from the value of the input parameters.
  * **Brackets are not needed around a singular parameter**: If there is one parameter, then brackets are not needed (but can still be used), although multiple parameters will still require the brackets.
  * **Optional curly brackets**: If the expression body consists of a single statement, then the curly brackets can be removed.
  * **Return keyword is optional**: The compiler will return the value of the expression if it contains a single statement. If there are curly brackets around the expression body, then it will require a return statement whether it consists of a single statement or not.

Using a lambda expression first requires a functional interface that contains a method that it will override. The are many classes that are already built into Java that can be used as a functional interface, such as _Runnable _and _Comparator_.

Before Java 8, there were a few ways to use classes and override their behavior. Option 1 is to make a new class and implement it and its method. Unless it is a piece of code that is going to be used a lot, this can be seen as overkill and could lead to lots of tiny classes that are only used once. Option 2 is to use an Anonymous class and create an instance of the interface in the current code where it is needed and override the method there. For a piece of code that is used once, this makes more sense, as you get the functionality you need without the hassle and clutter of making a new class.

**Option 1: Create a new class:**
    
    
        public static void main(String args[]) {

**Option 2: Create an Anonymous class:**

Now we can follow the same path as the Anonymous class, but this time, the implementation of the interface will be done by using a lambda expression.

As you can see, this allows this simple implementation to be done in much fewer lines of code. This example, using _Runnable_, does not require any parameters, as the _run()_ method also has no input parameters.

Lambda expressions can also be passed in as inputs into methods that require a functional interface as one of their parameters.

Following the rules defined earlier in this post, there are a few ways this could be rewritten using lambda expressions, although one is clearly nicer than the rest.

By now you hopefully have a little understanding into using lambda expressions in Java 8. Currently, I am still skeptical about using them in my code but in writing this post and the examples, I can see why they are useful. The main reason I am starting to like them is that for simple operations, they are clear and concise, making the code much easier to read when quickly scanning through it. Although they might not be as useful once code becomes more complex, for simple operations, such as performing a function on the elements of a list, I would not hesitate to use a little lambda expression.
