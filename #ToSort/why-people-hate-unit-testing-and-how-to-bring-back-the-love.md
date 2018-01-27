# Why People Hate Unit Testing and How To Bring Back the Love

_Captured: 2018-01-18 at 19:31 from [dzone.com](https://dzone.com/articles/why-people-hate-unit-testing-and-how-to-bring-back-1?edition=357091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-18)_

[Learn how _real _real-time monitoring is critical for DevOps](https://dzone.com/go?i=272435&u=https%3A%2F%2Fsignalfx.com%2Fsolutions%2Fenabling-devops%2F). Because you can't build what you can't see.

Let's face it. Nobody really likes to do unit testing. I've had people come up to me at conferences with stories and stories of how much they hate it. And while there are some people who are good at it, for the majority of us, it is just a necessary evil that must get done despite the best, most clever complaints. Today I'm going to look at some of the reasons why we don't like it, and how to get past these obstacles with software automation.

![](https://blog.parasoft.com/hs-fs/hubfs/Blogs/JUnit%20Testing%20Figure%201.png?t=1500394486158&width=280&name=JUnit%20Testing%20Figure%201.png)

> _Continuous Testing Pyramid_

## So Why Do Unit Testing, Anyway?

Most development teams will agree that, although they don't like it, unit testing is, in fact, valuable. It helps developers truly understand the code they are developing, and provides a solid foundation to the continuous testing pyramid, as shown above, which, in turn, enables teams to accelerate agile development while mitigating risk of defects slipping into later stages of the pipeline.

I would go further and say that the process of creating a unit test is a beneficial activity in and of itself, helping the developer to look at their code through a different lens, essentially doing an additional code review.

When you are unit testing, you review the interface to the functionality from an external point of view, benefitting from asking questions like, "How will my code be used?" (leading to a simplified interface and lower cost of code maintenance) or, "What happens if I get invalid data?" (resulting in more robust and reusable code).

## Where Intentions of Great Unit Testing Break Down

Typically, development teams do a minimal amount of unit testing, or skip it altogether, often due to some combination of (1) the pressure (and time it takes) to deliver more and more functionality, and (2) the complexity and time-consuming nature of creating valuable unit tests.

This breaks down into some common reasons developers cite that limit the adoption of unit testing as a core development practice include:

  * It is difficult to understand, initialize, and/or isolate the dependencies of the unit under test.
  * Determining what to validate, and defining appropriate assertions, is time-consuming and often requires intelligent "guess work."
  * There is lot of manual coding involved, often even more than was required to implement a specific feature or enhancement.
  * It's just not that interesting. Developers don't want to feel like testers, they want to spend time delivering more functionality.

To help with these limitations, there are several existing tools that are currently available that can help with unit testing. Unit testing and assertion frameworks provide standardized execution formats (i.e. Junit) for seamless integration into CI infrastructure (e.g. Jenkins, Bamboo, TeamCity). IDEs help in the creation of test code (e.g. Eclipse, IntelliJ). Mocking frameworks isolate the code from its dependencies (e.g. Mockito, PowerMock). Code coverage tools provide some visibility into what code was executed (e.g. Emma, Cobertura, Clover). Debuggers allow developers to monitor and inspect the step-by-step execution of an individual test.

But unfortunately, all of these tools have limitations, and developers still find many pain points, such as the following:

  * The IDE helps with creating a skeleton for the unit test, but no "content." The developer sill needs to add lots of code to create an executing test:
![](https://blog.parasoft.com/hs-fs/hubfs/Blogs/JUnit%20Testing%20Figure%202.png?t=1500394486158&width=379&height=217&name=JUnit%20Testing%20Figure%202.png)

  * Assertions need to be manually defined and tests must be executed to see if the correct values have been asserted.
  * Mocking frameworks require a significant amount of manual coding to instantiate and configure, plus the knowledge of how to correctly use them.
  * Coverage tools provide insight into what code an executed test has covered, but they don't provide any insight into the runtime behavior of the test.
  * Debuggers can be used for an individual test but do not scale as a way to monitor an entire test run.

In summary, creation of the unit test still requires a lot of manual, time-consuming, often mind-numbing effort before you've even started with adding business logic to a test.

## The Solution? We Created an Assistant!

To build a tool to help you bypass these pain points, we turned to software testing automation (of course). Parasoft Jtest's Unit Test Assistant is now available to help you create a fully-functioning unit test at the click-of-a-button.

Tests created with UTA are just "regular" JUnits but with all the mundane work done for you. UTA sets up the test framework, instantiates objects, and configures mocks for appropriate objects and method calls used by the method under test.

These JUnits can be executed as part of your standard CI workflow the same way as your existing tests; however, when a JUnit is executed by UTA, including your existing tests, the test is monitored in a way that provides analysis beyond just simply providing code coverage numbers.

By analyzing the test at runtime, UTA is able to provide a series of recommendations, many with **quick fixes** that help you take action with one-click, such as:

  * Highlighting object values that have changed and should be asserted,
  * Identifying method calls that should be mocked to better isolate the code under test, and
  * Finding tests that are not 'cleaning up' after themselves and creating a potentially unstable test environment (e.g. due to use of threads, external files, static fields or system properties).

We created UTA to ease the pain of unit testing because, as an organization that specializes in perfecting software, we know that unit testing is an essential step in creating software that is safe, secure, reliable, and high-quality. So I hope to have conversations with you at future conferences and events, where instead of telling me about how much you hate unit testing, you can tell me about your experiences using UTA to bring back the love.

To get a free demo of JTest UTA, [click here](http://software.parasoft.com/request-a-demo/).

[Get real-time alerts and visualizations](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue) across your cloud infrastructure for real real-time cloud monitoring. [Try it FREE now](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue)!
