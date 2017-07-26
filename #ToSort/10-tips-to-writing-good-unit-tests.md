# 10 Tips to Writing Good Unit Tests

_Captured: 2017-06-12 at 13:50 from [dzone.com](https://dzone.com/articles/10-tips-to-writing-good-unit-tests?edition=304169&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-11)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Since we already got started on unit testing in the previous post, I thought we could stick with the topic and lay out some rules for writing good, maintainable unit tests. The choice was pretty arbitrary and by no means complete, but I hope it will be helpful. Let's get started.

## 1\. Make Them Short

Since we're testing a single piece of functionality, delivered by a single unit of code, it makes sense that a test should be reasonably short. How short? Well, that depends on multiple factors, but usually not longer than a few lines of code.

## 2\. Don't Repeat Yourself

Good coding practices apply to test code in the same way they apply to production code. In my experience, one of the most commonly violated rules in unit tests is [DRY](http://wiki.c2.com/?DontRepeatYourself). Some people even claim that unit tests should not share any code at all. That's pure BS. Of course, you want to keep your tests as readable as possible, but copy-pasting things around is not the solution.

## 3\. Prefer Composition Over Inheritance

Once you acknowledge the two previous points, you might feel tempted to create some sort of base class for your test that will contain commonly used code. If you do, stop right there! Such a base class works like a magnet for all sorts of unrelated shared code and grows very quickly until it takes over your project, your company, and even your dog. Protect your dog, use composition!

## 4\. Make Them Fast

Unit tests are something you should be able to run almost all the time. For this reason, make sure to mock out external dependencies and other things that might slow your tests down. This will usually be things like databases, external systems, or file operations. At the same time, don't overdo this - [complete isolation of the unit under test is not a good solution either](https://dzone.com/articles/unit-testing-the-myth-of-complete-isolation).

## 5\. Make Them Deterministic

Every time I hear that somebody has a 95% working test suite and that's it good enough to go to production, I want to both laugh and cry at the same time. For God's (or your dog's) sake, unit tests should be working 100% of the time. Only 100% passing tests mean that everything is okay (with the units, you need other kinds of tests as well). If your unit tests seem flaky, make sure to find the root cause and fix it as soon as possible.

## 6\. Don't Ignore Tests

Given points 4. and 5., it's particularly important to mention that adding the [@Ignore annotation to your test is not a way to fix your test suite](https://dzone.com/articles/open-letter-from-an-ignored-test). It's a way to make your test suite even more unreliable because now it's not protecting you from regression bugs and such.

## 7\. Test Your Tests

Yes, you read that right, and no, I'm not crazy. I don't mean writing tests of your tests. I mean practices like [mutation testing](http://pitest.org/), [test-driven development](http://amzn.to/2rG2GI4), or frequent "changing random stuff" in your codebase to see if any tests fail. I also often do a mental exercise of trying to come up with such potential changes to the code that my tests would not spot.

## 8\. Name Your Tests Well

No, shouldThrowException is not a good name for your test. Although I'm not convinced that every project should use some fancy naming conventions for the tests, I am fully convinced that you should be able to tell which part of your code is broken by barely reading the names of failed test cases.

## 9\. One Logical Assertion Per Test

To achieve the nice goal of being able to tell what's wrong by just reading the names of failed tests, one requires something more than just good names. A number of things that a single test check must be limited as well. Therefore, a good unit test should contain only one logical assertion i.e. check only one output/side effect of the tested method.

## 10\. Design Your Tests

This is a meta-tip, that spans all other tips in this article and all those that I did not mention here. Treat your tests with the same care that you treat your production code with. Consider both good design principles and indicators like low coupling between the test code and production code, and code smells such as duplication, dead code and the like. Remember, that a good test suite can make your life much easier by making you feel safe when changing and refactoring your code, while a bad test suite can make you miserable, waste a ton of your time and make your code almost impossible to change.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
