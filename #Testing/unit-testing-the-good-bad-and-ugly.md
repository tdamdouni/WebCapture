# Unit Testing: The Good, Bad, and Ugly

_Captured: 2018-09-13 at 07:07 from [dzone.com](https://dzone.com/articles/unit-testing-the-good-bad-amp-ugly?edition=392202&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-09-12)_

xMatters delivers integration-driven collaboration that relays data between systems, while engaging the right people to proactively resolve issues. Read the [Monitoring in a Connected Enterprise whitepaper](https://dzone.com/go?i=283436&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fmonitoring-connected-enterprise%3Futm_campaign%3D70138000001C2pDAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3D3-steps-to-monitoring-in-a-connected-enterprise-wp) and learn about 3 tools for resolving incidents quickly.

Unit testing is common to all the code that we write. We all do it, so it's important to understand the most "looked-forward to" (sarcasm) aspect of development. However overlooked and underestimated, unit testing forms the most important part of any development cycle and hence it's worth delving into. So let's begin

.So

the big question at hand is, what is unit testing?

> "A unit test is an automated piece of code that **invokes a unit of work** in the system and then **checks a single assumption about the behavior of that unit of work**."
> 
> \- Roy Osherove

A fair definition, but let's break it down. I want to focus on two important constituents of this definition

:Here

, a unit of work is a single logical use case of the system irrespective of its size. It could span a method, multiple methods, a class or even classes. All that matters is this combination achieves a single logical purpose.

## "...**checks a single assumption about the behavior of that _unit_ of work."**

![](https://i2.wp.com/knoldus.blog/wp-content/uploads/2018/04/overloaded-tricycle-funny-transportation-picture.jpg?resize=400%2C301&ssl=1)

A unit test case works with something specific about a functionality, it doesn't cover it entirely. It's a bad practice to create something called

testAllThings

and call every method in the namespace

.Another

important aspect of a unit test is that it works with the use case in **isolation.**Which means it should not depend or be bothered by any external entity. So changing another part of the codebase should not affect a unit test case. Simply put, if you have a unit test case that doesn't run without a proper setup or malfunctions in the presence of one, you haven't written a unit test case

.Now

before we dive further, lets first understand the need for a unit test. Why do we put in at least half as much time as we devote in development, on unit tests?"_It helps us verify a functionality_" one might say, and I won't disagree, it is an important thing to know what you have coded actually works. But however much we say it, one thing always bugs us.

## **It Slows Us Down**

![](https://i2.wp.com/knoldus.blog/wp-content/uploads/2018/04/speedbreakersignage-300x280.png?resize=300%2C280&ssl=1)

That same time could have been spent more productively on other activities, right? Wrong. And I'm not saying this out of thin air. According to a press release by [TypeMock](https://www.typemock.com), which makes unit testing products,**_ unit testing saves about 70-80% time _**in debugging. So in the long run, it saves time. Go figure!

In addition, unit testing offers great feedback on the modularity and design of your code. Whenever you're struggling to work with a class and method in order to test it, there is a design problem. Hence it's not only about making testing.

Now that we know what unit testing is and why one should do unit testing, let's look at some good practices:

## Good Practices

  * Test cases should be small and isolated. As mentioned above, they should test something specific about the code.

  * Try keeping test to assertion ratio near to 1. It makes it easy to identify any assertion which has failed. Having multiple assertions can make it cumbersome to verify which assertion went rogue.

  * Always avoid test interdependence. Each test case should handle their own build up and tear down. Test runners don't generally run tests in any specified order. Thus, we can not assume anything based on the order in which we write the cases.

  * A test case approaches the behavioral aspect of the code. So it should be easily comprehensible in the sense that what we are testing and what to do in case of failure.

  * Mock as little as needed. Too many fakes create fragile tests which break when they code undergoes changes in production.

  * Avoid mocking chatty interfaces. Any change in the order of calling may break the test.

  * It should be independent of external factors. You must not require a setup to run a unit test.

  * We must maintain a clear naming convention in writing unit tests. This simply makes our code more comprehensible.

  * While working on a continuous integration build, always add the unit test cases to the build so that whenever one test case fails, the whole build fails thus leaving no exemptions.

## Bad Practices

  * Using nondeterministic factors in the codebase: Such scenarios are difficult to test especially when they don't reproduce/hold a constant value on each rerun. Eg Using Time as an authentication measure in code which would vary at each moment and also in different time zones.

  * Using side-effecting methods: Testing these could be as difficult as testing methods with a nondeterministic factor in them. Poorly designed untestable code introduce unwarranted complexities.

  * Impurity is highly toxic: Method depending upon nondeterministic or side-effecting methods themselves become the same kind and in the end complicate the entire codebase. Considering the effect it may have on a real-life complex application, we may find ourselves trapped in codebase filled with antipatterns, secret dependencies and all sorts of unpleasant scenarios.

  * Mocking interfaces and classes outside the codebase: If you don't fully understand the proper usage of an interface, you should avoid mocking it. Rather you should wrap interaction with external API classes into specially created interfaces for the same purpose.

  * Working with the mutable global state: Method depending upon mutable global state not only requires you to consider the current value but also be updated about other code that may have altered its value earlier. Hence its advisable to avoid them.

This was a brief version of The Good, Bad and Ugly of Unit Testing. I hope it was of some help.

**References:**

Discovering, responding to, and resolving incidents is a complex endeavor. [Read this narrative to learn how you can do it quickly and effectively by connecting AppDynamics, Moogsoft and xMatters to create a monitoring toolchain.](https://dzone.com/go?i=300536&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fmonitoring-connected-enterprise%3Futm_campaign%3D70138000001C2pDAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3D3-steps-to-monitoring-in-a-connected-enterprise-wp)
