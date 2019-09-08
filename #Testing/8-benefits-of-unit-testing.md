# 8 Benefits of Unit Testing - DZone DevOps

_Captured: 2019-09-06 at 21:56 from [dzone.com](https://dzone.com/articles/top-8-benefits-of-unit-testing?edition=521312&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202019-09-06)_

_Originally published Jan. 18, 2017_

![beads_separated_into_compartments](/storage/temp/12413286-beads-in-compartments.jpg)

_If there were ever a time to compartmentalize..._

As we write a lot about [Agile](https://dzone.com/articles/agile-development-and-testing-an-introduction), [CI](https://dzone.com/articles/what-is-cicd), and [TDD](https://dzone.com/articles/the-basics-of-tdd), we had to mention unit testing. This time, we will talk about what [unit testing](https://dzone.com/articles/the-anatomy-of-good-unit-testing-with-examples-in) is, why it is part of Agile methodology, and the main benefits of using it.

In computer programming, unit testing is a software testing method by which individual units of source code are tested to determine whether they are fit for use. A unit is the smallest possible testable software component. Usually, it performs a single cohesive function. A unit is small, so it is easier to design, execute, record, and analyze test results for than larger chunks of code are. Defects revealed by a unit test are easy to locate and relatively easy to repair.

> You may also enjoy:  [Unit Testing Best Practices: How to Get the Most Out of Your Test Automation](https://dzone.com/articles/unit-testing-best-practices-how-to-get-the-most-ou)

The goal of unit testing is to segregate each part of the program and test that the individual parts are working correctly. It isolates the smallest piece of testable software from the remainder of the code and determines whether it behaves exactly as you expect. Unit testing has proven its value in that a large percentage of defects are identified during its use. It allows automation of the testing process, reduces difficulties of discovering errors contained in more complex pieces of the application, and enhances test coverage because attention is given to each unit.

For example, if you have two units and decide it would be more cost-effective to glue them together and initially test them as an integrated unit, an error could occur in a variety of places. Is the error in unit 1 or in unit 2? Is the error in both units? Is the error in the interface between the units? Is the error because of a defect in the test?

As you can see, finding the error in the integrated module is much more complicated than first isolating the units, testing each, then integrating them and testing the whole.

At [Apiumhub](http://www.apiumhub.com), we work using Agile methodology, and we work a lot with unit tests. Unit testing is a signature of Extreme Programming (XP), another agile software development methodology we use quite often, which led quickly to test-driven development. We strongly believe that being Agile is doing CI and TDD. Using test-driven development, developers create unit tests as they develop their code so that each unit test tests a tiny piece of software code usually before the code is written.

Unit testing provides numerous benefits including finding software bugs early, facilitating change, simplifying integration, providing a source of documentation, and many others, which we will look right now with more detail. 

## **1\. Makes the Process Agile**

One of the main benefits of unit testing is that it makes the coding process more Agile. When you add more and more features to a software, you sometimes need to change old design and code. However, changing already-tested code is both risky and costly. If we have unit tests in place, then we can proceed for refactoring confidently.

Unit testing really goes hand-in-hand with agile programming of all flavors because it builds in tests that allow you to make changes more easily. In other words, unit tests facilitate safe refactoring. 

## **2\. Quality of Code**

Unit testing improves the quality of the code. It identifies every defect that may have come up before code is sent further for integration testing. Writing tests before actual coding makes you think harder about the problem. It exposes the edge cases and makes you write better code. 

## **3. Finds Software Bugs Early**

Issues are found at an early stage. Since unit testing is carried out by developers who test individual code before integration, issues can be found very early and can be resolved then and there without impacting the other pieces of the code. This includes both bugs in the programmer’s implementation and flaws or missing parts of the specification for the unit.

## **4. Facilitates Changes and Simplifies Integration**

Unit testing allows the programmer to refactor code or upgrade system libraries at a later date and make sure the module still works correctly. Unit tests detect changes that may break a design contract. They help with maintaining and changing the code.

Unit testing reduces defects in the newly developed features or reduces bugs when changing the existing functionality. 

Unit testing verifies the accuracy of the each unit. Afterward, the units are integrated into an application by testing parts of the application via unit testing. Later testing of the application during the integration process is easier due to the verification of the individual units.

## **5\. Provides Documentation**

Unit testing provides documentation of the system. Developers looking to learn what functionality is provided by a unit and how to use it can look at the unit tests to gain a basic understanding of the unit’s interface (API).

## **6. Debugging Process**

Unit testing helps simplify the debugging process. If a test fails, then only the latest changes made in the code need to be debugged.

## **7. Design**

Writing the test first forces you to think through your design and what it must accomplish before you write the code. This not only keeps you focused; it makes you create better designs. Testing a piece of code forces you to define what that code is responsible for. If you can do this easily, that means the code’s responsibility is well-defined and therefore that it has high cohesion.

## **8. Reduce Costs**

Since the bugs are found early, unit testing helps reduce the cost of bug fixes. Just imagine the cost of a bug found during the later stages of development, like during system testing or during acceptance testing. Of course, bugs detected earlier are easier to fix because bugs detected later are usually the result of many changes, and you don’t really know which one caused the bug. 

### Further Reading

#### [To Unit Test or Not to Unit Test?](https://dzone.com/articles/to-unit-test-or-to-not-unit-test)

#### 

[ Unit Testing Anti-Patterns — Full List 

](https://dzone.com/articles/unit-testing-anti-patterns-full-list)
