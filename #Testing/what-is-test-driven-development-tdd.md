# What is Test-Driven Development (TDD)?

_Captured: 2017-04-25 at 23:41 from [dzone.com](https://dzone.com/articles/what-is-test-driven-development-tdd?edition=292916&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-25)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Test-driven development (TDD) is not new but it certainly is in vogue. It was originally invented by Kent Beck as part of his extreme programming methodology, back in the 1990s and has continued to gain adherents ever since. In our [2016 open source languages survey](https://www.activestate.com/blog/2016/09/activestate-2016-open-source-survey) almost half of all respondents mentioned TDD as being a development methodology they use.

## What Is TDD?

Very simply, write the tests first! For each new feature (user story):

  * Write tests to test the feature.
  * Run tests (only new tests should fail).
  * Write your code to implement the feature.
  * Run tests (repeat steps 3 and 4 until all tests pass).
  * Refactor code (if necessary).

Of course, the devil is in the details and the simplicity of the steps highlight the overall framework for each functionality that needs to be tested. Once your first test is complete, the best practice is to review both the code and tests then refactor to ensure a clean design. The goal is to have cleanly-written and well-documented code and tests so you're generating a thorough and solid solution. Then you move on to the next bit of functionality.

Over time, your application builds up a comprehensive suite of tests that gives you confidence in what you've built. Subsequently, when people make changes and the tests pass or fail, you have confidence in the changes and understand what has gone awry.

## Why TDD Is Crucial for Enterprise Applications

TDD is particularly important for large scale enterprise applications because it is too easy for these to become unmaintainable monstrosities over time. You can easily lose your way if a large application is not well structured and tested consistently. This is extremely important for enterprise applications because they need to be maintained over a very long period of time. So having a good suite of tests that cover the majority of the functionality in your application gives you confidence when you make changes even years down the road.

For example, I have a piece of code that implements a business rule and its associated tests and then I have a user story to change the business rule logic. I write my tests and the new tests pass, but one or more original tests fail, this is a great outcome. Now many questions arise- Is it a bug? Is it a side effect? Perhaps I should've rewritten the test along with the functionality? These questions and subsequent changes are a way of giving you confidence in what your application is supposed to produce.

## Are You Covered?

If you are responsible for a suite of software or a software application, you want to ensure your engineers are adding the functionality and their respective tests along with it. This is where your coverage tool steps in. Over time, different developers come and go and a coverage tool can help you see the trend- if it is trending down, you might want to make sure there is a good reason for this.

Also, a good coverage library can help to determine what percentage of your product is covered. The first step is determining what is your coverage goal. You would think that it should always be 100%...but is it realistic? It might be interesting because you figure you've covered everything, but the fact of the matter is you've probably wasted a large amount of time to test things that do not need to be tested. Realistically, 100% is not the goal you should be aiming for.

How much code you cover depends on many factors. If you have an application that is largely doing complicated logic, then you might need 90% code coverage. On the other hand, if your application is a pre-existing framework of business objects without any really complicated new functionality, you might be happy with 50% code coverage. The amount of coverage is going to change depending on the type of application and the functionality involved.

## Python: Master of TDD

Python lends itself very well to test driven development because of the packages and support available for testing. In this case, having a good suite of tests when you're building a large system in Python makes that large system more maintainable and gives you more confidence in the system. It can also reduce the number of defects due to its higher level of testing. In Python, its dynamic types make it crucial to do testing for types, so always be on the lookout for those cases.

For an enterprise to get value out of a code base over the long term, it has to be easily changeable to rapidly provide new business value and that's what TDD helps you do. Python has a good set of testing packages such as pytest, nose, and coverage, all of which we have included in [ActivePython 2.7.13, 3.5.3, and 3.6](https://www.activestate.com/activepython/downloads).

Learn more about TDD in our on-demand webinar: [Test-Driven Development with using ActivePython](https://www.activestate.com/webinars/test-driven-development-activepython) or [download ActivePython](https://www.activestate.com/activepython/downloads) to test out these code quality packages in our distribution.

![TDD Pros and Cons](https://www.activestate.com/sites/default/files/wysiwyg/TDD-Pros-Cons_0.png)

> _TDD Pros and Cons_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
