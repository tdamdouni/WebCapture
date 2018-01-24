# 10 Tricky Interview Questions for Java Devs

_Captured: 2017-12-21 at 23:08 from [dzone.com](https://dzone.com/articles/10-tricky-interview-questions-for-java-devs?edition=347111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-21)_

Here is a list of 10 tricky/popular interview questions and answers for Java developers. I got these questions out from StackOverflow. You are a junior or intermediate level Java developer and are planning to appear for interviews in the near future, you would probably find these questions to be useful enough.

**Q1: Is Java "pass-by-reference" or "pass-by-value"?**

Ans: Java is always "pass by value". Read the details on this page, [Is Java "pass-by-reference" or "pass-by-value"?](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value)

**Q2: How can you create a memory leak in Java?**

Ans: This is possible by making use of a class loader and ThreadLocal. Read the details on this page, [Creating a memory leak in Java](https://stackoverflow.com/questions/6470651/creating-a-memory-leak-with-java)

**Q3: What is the difference between package private, public, protected, and private?**

Ans:

  * A private member variable is accessible within the same class.

  * A package private variable (member variable with no access specifier) is accessible within all classes in the same package.

  * A protected variable is accessible within all classes in the same package and within subclasses in other packages.

  * A public member is accessible to all classes.

Read more details on this [page](https://stackoverflow.com/questions/215497/in-java-difference-between-package-private-public-protected-and-private).

**Q4: What are two differences between a HashMap and a Hashtable?**

Ans: A Hashtable is synchronized and does not allow null keys or values. Read more details on this page: [differences between HashMap and Hashtable](https://stackoverflow.com/questions/40471/differences-between-hashmap-and-hashtable).

**Q5: What are different techniques for avoiding != null statements (Not Null Check)?**

Ans: Usage of _assert_ statements is one way. Custom annotations can also be defined for NotNull checks. See more details on this page: [How to avoid != null Statements](https://stackoverflow.com/questions/271526/avoiding-null-statements).

**Q6: Does "finally" always execute in Java?**

Ans: Not in a scenario such as an invocation of a "System.exit()" function, an infinite loop, or system crash, etc. More details can be found here: [Does finally always execute in Java?](https://stackoverflow.com/questions/65035/does-finally-always-execute-in-java)

**Q7: Is it possible to call one constructor from another in Java?**

Ans: Yes, but one can only chain to one constructor -- and it has to be the first statement in your constructor body. More details can be found on this page: [How do I call one constructor from another in Java?](https://stackoverflow.com/questions/285177/how-do-i-call-one-constructor-from-another-in-java)

**Q8: Which one should be used, "implements Runnable" vs. "extends Thread"?**

Ans:"Implements Runnable" is the preferred way. Read further details here: [Implements Runnable vs. Extends Thread](https://stackoverflow.com/questions/541487/implements-runnable-vs-extends-thread)

**Q9: Is it possible to break out of nested loops in Java?**

Ans: Yes, and here is an example of how to do it: [Breaking out of nested loops in Java](https://stackoverflow.com/questions/886955/breaking-out-of-nested-loops-in-java).

**Q10: What is reflection and why is it useful?**

Ans: Reflection is used to describe code that is able to inspect other code in the same system. Read the reasons for doing so here: [Why Reflection is useful](https://stackoverflow.com/questions/37628/what-is-reflection-and-why-is-it-useful).
