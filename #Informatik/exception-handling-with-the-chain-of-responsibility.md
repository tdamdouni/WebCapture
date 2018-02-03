# Exception Handling With the Chain Of Responsibility

_Captured: 2018-02-02 at 16:50 from [dzone.com](https://dzone.com/articles/exception-handling-with-chain-of-responsibility?edition=359106&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-01)_

Just released, a [free O'Reilly book on Reactive Microsystems: The Evolution of Microservices at Scale](https://dzone.com/go?i=237227&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone). Brought to you in partnership with Lightbend.

An [exception](https://www.tutorialspoint.com/java/java_exceptions.htm) (or exceptional event) is a problem that arises during the execution of a program. When an exception occurs, the normal flow of the program is disrupted and the program/application terminates abnormally, which is not recommended. Therefore, these exceptions are to be handled.

An exception can occur for many different reasons. The following are some scenarios where an exception occurs.

  * A user has entered invalid data.
  * A file that needs to be opened cannot be found.
  * A network connection has been lost in the middle of communications or the JVM has run out of memory.

## Class Hierarchy

![alt text](https://camo.githubusercontent.com/769d73c84d1cb1462250de635c1055137c9cb649/68747470733a2f2f696d6167652e6962622e636f2f6b51725937612f657863657074696f6e73312e6a7067)

Based on these, we have three categories of exceptions. You need to understand them to know how exception handling works in Java.

According to **Item 58 - Use checked exceptions for recoverable conditions and runtime exceptions for programming errors**, from [Effective Java 2/e](https://goo.gl/PgsN7i) by [Joshua Bloch](https://en.wikipedia.org/wiki/Joshua_Bloch), the Java programming language provides three kinds of throwables.

  1. **Checked exceptions**: Use exceptions for conditions from which the caller can reasonably be expected to recover.

  2. **Runtime exceptions (unchecked exceptions)**: Use exceptions to indicate programming errors. All of the unchecked throwables you implement should use subclass RuntimeException

  3. **Errors**

## Motivation

We can view [Chain Of Responsibility -- Design Pattern](https://dzone.com/refcardz/design-patterns) for this purpose.

![alt text](https://camo.githubusercontent.com/7ac7551d36f19254d20f4a7b079b773c16c8df0b/68747470733a2f2f696d6167652e6962622e636f2f6b46735753612f31303630395f7468756d622e706e67)

**Example:** When an exception is thrown in a method, the runtime checks to see if the method has a mechanism to handle the exception or if it should be passed up the call stack. When passed up the call stack, the process repeats until the code to handle the exception is encountered or until there are no more parent objects to hand the request to.

## Code Example

For see the source code on GitHub, please refer to [this ](https://github.com/mahdieha/ExceptionHandling#exception-handling)link.

Strategies and techniques for building scalable and resilient microservices to refactor a monolithic application step-by-step, [a free O'Reilly book](https://dzone.com/go?i=237228&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone). Brought to you in partnership with Lightbend.
