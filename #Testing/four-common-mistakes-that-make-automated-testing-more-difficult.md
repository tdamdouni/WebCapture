# Four Common Mistakes That Make Automated Testing More Difficult

_Captured: 2018-02-09 at 14:35 from [dzone.com](https://dzone.com/articles/four-common-mistakes-that-make-automated-testing-m?edition=361094&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-02-09)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

Automated testing is an essential step in the development process (as covered in the [first blog post](https://keyholesoftware.com/2018/01/17/without-automated-testing-you-are-building-legacy/) in this series). Unfortunately, writing automated tests is often skipped because it's difficult or there is a high maintenance cost associated with the tests written.

Many of the difficulties of writing and maintaining tests can be traced back to a handful of common coding mistakes. This article examines four of these mistakes, how they negatively impact testing, and offers tips on how to resolve them.

## 1\. Improper Use of Dependency Injection

I love Spring; I love how it handles a lot of configuration for me. However, like any tool, Spring can also be misused.

For a long time I had a bad habit of auto-wiring fields directly:

![](https://i0.wp.com/i.imgur.com/hu19gLr.png?resize=541%2C277&ssl=1)

Directly auto-wiring fields makes testing more difficult as a Spring context must be now be instantiated to test the class.

At a high level, this might sound fine as the application will be using Spring in prod. However, initializing a Spring context takes time, often several seconds, which, in a large test suite, can quickly add up. A Spring context is also shared across test cases and test classes which can cause tests to fail inconsistently. This is known as "flickering."

The best solution is to create a constructor that takes in all the resources the class needs to function. This can easily be accomplished in Eclipse with the shortcut "shift (command) + alt + s."

![](https://i0.wp.com/i.imgur.com/02vLnPu.gif?resize=1235%2C635&ssl=1)

Using constructors for dependency injection makes passing in mock objects much easier in a test.

Beyond the testing benefits, however, constructor injection clearly defines what resources a class needs to function. This can be helpful if in the future the resources a class requires changes. Then, the change in constructor signature will cause compilation issues rather than tests (or the application) failing without obvious reason.

**Note:** There are many test cases where initializing a Spring context is necessary, however initializing a Spring context should not be a requirement for a unit test.

## 2\. Instantiating a Resource in a Method

Instantiating a resource in a method is a subtle issue that can greatly increase the difficulty of testing a method. An example of this would be using the `RestTemplate` class to make a REST call like this:

![](https://i2.wp.com/i.imgur.com/B9Qdwd0.png?resize=729%2C195&ssl=1)

Instantiating `RestTemplate` in method makes testing difficult as now the test directly relies upon the called service. This leads to tests that run slower and are less reliable as the dependent service might go down or not have the correct test data. It can also be difficult to simulate some scenarios, like the service throwing an error for example.

Resources, database connections, HTTP connections, etc should be injected into a class via the constructor which allows a test class to easily pass in a mock whose behavior it can control.

![](https://i0.wp.com/i.imgur.com/9c177wr.png?resize=726%2C283&ssl=1)

## 3\. Testing at Too High an Abstraction Layer

When automated testing is being introduced to a codebase, I have seen developers begin writing tests at a high abstraction layer. This has often been in an effort to quickly achieve high levels of code coverage.

An example of one is below:

![](https://i0.wp.com/i.imgur.com/xviOxDX.png?resize=841%2C448&ssl=1)

When used in [behavior-driven development](https://en.wikipedia.org/wiki/Behavior-driven_development), end-to-end tests can serve as a valuable guide in developing an application. However end-to-end tests alone are not capable of, or at least not well suited for, fully testing out all the paths through a codebase.

In the above example, it would be difficult to write a test case for how `PersonDao` responds when the database returns an unexpected value. And even if such a test could be written, it will have a high maintenance cost associated with it as changes to `PersonController` and `PersonService` could cause the test to fail, even though the test is _really_ only concerned with `PersonDao`'s behavior.

Automated test suites need unit tests written at the layer of abstraction you're trying to test. If you are testing a controller's behavior, your tests should only be testing that class and mocking out the behavior of dependent classes:

![](https://i0.wp.com/i.imgur.com/SCXUPcp.png?resize=754%2C513&ssl=1)

Testing at the proper abstraction layer helps reduce the maintenance cost of writing tests. It also makes it very clear where to look when a test begins to fail. If `testGetPerson` in the above example fails, it will only be because of a change in `PersonController`, not because of a change in `PersonService` or `PersonDao`.

## 4\. Accepting Failing Tests

When discussing whether a single test should fail a build or not, I think of this paraphrased quote from [Generation Kill](https://www.youtube.com/watch?v=0Oj_ZP4KUTc):

> _"If you don't enforce grooming standards, the men get lax, and then other standards fall."_
> 
> -Sgt. Maj. John Sixta

There can be a tendency to argue that a single test failure shouldn't fail a build. I feel this is a dangerous mindset as it can lead to accepting two, three, and so on failing tests. However, the larger issue is that the acceptance of failing tests means automated tests aren't yet seen as an essential step in the development process, or that the automated tests are not seen as a good indicator of the health of the code they are testing.

## Conclusion

Automated testing is an essential step in the development process. But, as it can be a challenge, writing automated tests is often skipped. The four mistakes covered in this article can directly affect the difficulty level of writing and maintaining tests. These four mistakes will be covered in even more depth in future articles, but in the meantime, I hope you'll consider these actions and how they can help improve your automated testing habits.

A major focus in this blog series (and [in my course](https://www.pluralsight.com/courses/effective-testing-with-spring)) will be how to write tests that fail only as a result of code changes or contract changes independent services. Confidence in an automated test suite increases as test failures are seen as directly relating to the scenario being tested, not the result of a service being down, tests running in an incorrect order, or other spurious reasons. And, as confidence in automated testing increases, this can lead an organization to adopt practices of [continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) and eventually [continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery).

As we continue this blog series, we will look into what has recently become a hot topic: the distinction between unit tests and integration tests. Stay tuned.

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
