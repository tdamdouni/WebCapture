# Why Do Programmers Fail to Write Good Unit Tests?

_Captured: 2017-12-29 at 20:23 from [dzone.com](https://dzone.com/articles/why-do-programmers-fail-to-write-good-unit-tests?edition=347139&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-12-29)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

We programmers are full of opinions when it comes to unit testing. We don't always agree about the importance of unit testing or what role it should play. There is also a lot of debate about what makes a good unit test. But before you dismiss unit testing, I'd like to argue that it's an essential part of what it means to write clean code, and in the long run will make you a better programmer.

I know that more and more programmers are starting to embrace unit tests, which is great news for the industry. But I'm also aware that many of us still remain skeptical. And a small part of me understands why. Those who are reluctant to embrace unit testing often claim that good tests are difficult to write, and they take time that can be used developing new features. Others take this a step further and question whether there is a link between passing a unit test and good code.

But when you see it in action, it very quickly becomes clear that unit testing--done well--can streamline the execution process and helps development teams build better processes. And perhaps that's why I'm going all in when it comes to unit testing. I think that once more programmers have a clear understanding of what makes a good unit test, they will also embrace it.

In my experience, however, it's almost too easy to write a bad unit test, and this just ends up costing you in the long run. Bad unit tests don't prove anything, making them very unhelpful. To truly see why I and many others in the industry are so excited about unit tests, you have to evaluate the many misconceptions about what unit tests are supposed to achieve. This is the only way to really see what unit testing can do for you.

## What Makes a Good Unit Test?

Where many programmers go wrong is failing to differentiate between good and bad unit tests. I believe that if you're ever really going to see the true benefit of unit testing, you must know what makes a good unit test.

While it may seem obvious, many fail to realize that a programmer with lots of experience won't necessarily write good unit tests. This is partly because writing unit tests and coding require different approachs. But it's more than that. Often the quality of these tests is impacted by false assumptions about what unit tests should achieve. The aim of a good unit test is to think about how the code should work in normal and extreme cases, examine and test each unit of code separately, and check that the code behaves as expected.

Here are some pointers to keep in mind for writing good unit tests:

  * **Each test should be independent of all other tests.** Specific behavior should be documented in only one test; otherwise, if you change that behavior, you'll have to change multiple tests.
  * **Tests must assert something. **It's vital that you assert anything that's also asserted by another test as this will yield the test ineffective and won't prove anything. Each test should have only one assertion.
  * **Test code unit by unit: **Avoid testing units of code grouped together as this can cause unnecessary overlap, and may cause one test to affect another.
  * **Avoid common setup code for unrelated tests. **Unnecessary preconditions which run at the beginning of unrelated tests will impact your results as it means you're not testing a single unit.
  * **Avoid testing configuration settings. **Keep in mind that your unit test configuration settings are not part of a unit of code. Testing these settings wouldn't prove anything.

## Why You Need to Unit Test

None of us are zero-bug programmers. We need to accept that, whether due to complexity or simply a mistake, errors will find their way into our code. And that's where unit testing and different unit testing patterns come in. One of the best ways to improve your code is by writing good unit tests. This ensures there's a formal process in place and helps us write clean code. Unit testing also plays an important role in helping us maintain clean code as we can easily see which future changes have impacted the code logic and have the ability to refactor the code and redesign it as it grows.

Without good unit testing, you cannot guarantee your code will be clean or consistent. Here are just a few reasons every programmer should consider unit testing:

  * Unit tests help reduce bugs in new and existing features.
  * Unit testing serves as a form of documentation.
  * Unit testing helps with refactoring.
  * Unit testing helps with maintaining code.
  * Unit testing forces you to think about your code more carefully.
  * Unit testing can make development faster.

## Any Unit Test Is Better Than Nothing at All?

Some programmers claim that just having a unit test is a good start. I couldn't disagree more. The [quality of the unit test matters ](https://www.typemock.com/blog/code-unit-testing-5-essential-tips-cant-neglect/)more than some are willing to acknowledge. In fact, I often say that if you aren't going to invest in good unit testing, why bother at all?

A good unit test makes all the difference and is often a big asset to the team, while a bad unit test is a costly burden that slows down the development process. It all comes down to how well we programmers understand the basic principles of unit testing. Unit testing has very specific goals and outcomes which we need to keep in mind when creating unit tests. That's only way we're going to write unit tests which have any real impact on our work.

Do you think unit testing is a waste of time? Tell us in the comments.

What makes a unit test good in your experience? We'd love to hear from you. Share your thoughts in the comments below.

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
