# TDD and Code Quality

_Captured: 2017-02-07 at 14:51 from [dzone.com](https://dzone.com/articles/tdd-and-code-quality?fromrel=true)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Every time I see an article claiming that TDD improves code quality, a part of me cries. It's not that I don't think it can be true. It's because it's not necessarily true, and those articles rarely bother to provide a satisfying explanation. Here's my try.

## TDD and Better Design

There's a lot of talking about TDD making your codebase more modular and less coupled, and making the designs you produce being better in general. I think this might be true, mainly because of two factors: the act of design and characteristics of testable code.

### The Act of Design

A lot of people (judging mostly by comments sections on dev portals) tend to skip the design part of software development and jump straight into coding. They try to get a rough implementation working, then refactor it a little and write the tests in the end. While this approach can succeed, it gives a lot of attention to just making it work and little to no attention to representing end-user or domain models that lie at the heart of object orientation.

In my understanding of TDD, before I even sit down to start coding I need to know (at least) the starting point. Especially when going the inside-out way, I need to first think of the objects and their behavior necessary to solve the given problem. Given I'm a _homo-sapiens_ and not a _code-o-sapiens_, I will get those objects from the end-user or someone's domain knowledge and thus ensure that the code does not diverge from the root of requirements. This is what I called "the act of design."

#### How Could It Go Wrong?

Well, it happens that even when doing TDD people forget the design or do it without due diligence. They just go and test drive the first idea that comes to their mind and then bend it until it works for all test cases. Such approach, although not meant by TDD pioneers, happens and can be actually detrimental to the design produced.

#### Avoiding the Pitfalls

Pay attention to the design process. Before you start coding, make sure you understand the underlying domain and/or technical concepts. If you find yourself implementing an "awkward" design, don't be afraid to take a step back and figure out what's missing. _[TDD by Example_](http://amzn.to/2kX0RQM) has some good insights into how flexible we should be with deleting the code and trying different approaches during TDD.

### Characteristics of Testable Code

When you're focused on making it work and not thinking about the test, there's a chance that the code that you'll produce will be to some degree untestable. In the best case, you'll notice the flaw and correct it; in the bad case, you'll hack here and there to make the test pass and in the worst case, you won't test it at all. When doing TDD, you start from a test, from your dream vision of how the test would look like. Again, given you're a _homo-sapiens_, you won't make things worse unless you're forced to and thus the code produced will be testable.

Testability itself is by most considered a sign of good design. However, it often happens to bring you some other design benefits "in the package." I think the most popular design benefit associated with TDD is lower coupling. In my experience, this might actually be true -- code that can be tested without excessive mocking and complex object initialization (most likely) isn't highly coupled to the rest of the system.

#### How Could It Go Wrong?

Well, I've seen a lot of people that just "mock all the things" and don't care about the size of the test setup (you can always create a base class or an util), and the testability benefit is gone. Obviously, other characteristics of code written like this won't be perfect either.

#### Avoiding the Pitfalls

Treat testability seriously. Do the minimum amount of setup and mocking required to test a functionality and strive not to change it during actual implementation. Follow other [good unit testing practices](http://amzn.to/2kX2TAq).

## TDD and Simpler Solutions

Some say that TDD leads to simpler solutions than other approaches. This is because in TDD, you should never write more production code than it is necessary to pass the currently failing unit test. This has profound implications. You no longer think about the whole implementation upfront. You let the tests guide you. It might happen that complex algorithms, extra methods, classes, or other constructs that you initially thought were necessary weren't actually needed. If test case by test case you arrived at a solution without those, then you have saved yourself some accidental complexity -- good for you!

### How Could It Go Wrong?

Supposedly you did no design or lousy design up front and you're going inside out. Then, there's no way that TDD saves you from unnecessary classes and such. Another common scenario is to write a single test or even all the author can think off, and then spin off the entire implementation as you imagined it. Simplicity? Doubt it.

#### Avoiding the Pitfalls

Again, pay attention to the design. Don't break the TDD rules -- have at most one failing test at a time and produce just enough implementation to make it work. At every point of the process, [do the simplest thing that could possibly work](http://c2.com/xp/DoTheSimplestThingThatCouldPossiblyWork.html). Switch between [the modes of TDD](http://tidyjava.com/three-modes-of-tdd/) to adjust the steps you're making to the complexity of the problem you're dealing with.

## TDD and Better Tests

The last claim that I wanted to discuss is how TDD can make your tests better. Better in this context means mostly that the tests are less coupled to the internals of production code. The reason for this would be that the production code did not exist at the time of writing the test. From my own experience, I can say that this can work very well. At the same time…

### How Could It Go Wrong?

Well, in most code bases that I've seen, it actually went wrong. People are so used to mocking everything around that they often develop their mock-TDD approach. Like, you write a failing unit test that the code will hit the mock and implement it. Then, they add another one for another mock and so on. In the end, when all mocks are in place and verified, they check that the tested method actually returns the correct result. I would not consider such a test loosely coupled to the production code.

#### Avoiding the Pitfalls

Take the time to understand [the differences between different types of test doubles and between state and interaction testing](https://martinfowler.com/articles/mocksArentStubs.html). Always focus on the outcomes of the functionality and not on the details of its implementation. Consider driving the functionality with a more coarse-grained test if you feel that unit testing would barely test that the compiler works and you've set up all mocks correctly.

## Conclusion

TDD can make your code better, but there's a ton of ways to do it wrong (trust me; I listed only a few). Take your time to understand the underlying dynamics and improving your skills. And when it comes to improvement, don't just read and talk -- practice, practice, practice!

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
