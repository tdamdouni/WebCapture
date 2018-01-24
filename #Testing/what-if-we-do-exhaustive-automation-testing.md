# What if We Do Exhaustive Automation Testing?

_Captured: 2017-12-04 at 01:36 from [dzone.com](https://dzone.com/articles/what-if-we-do-exhaustive-automation-testing?edition=343092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-03)_

### A developer examines the benefits of using UI and functional tests to a great extent that advocated by leaders such as Martin Fowler.

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

**Will the Benefit of Covering Every Possible Case Using Automation Tests Justify the Cost of Maintaining Such Test Suites?**

![](https://d33wubrfki0l68.cloudfront.net/ccee8b92ba1cf40d3cd8ed9132d3323bbf017305/2c8e2/assets/images/exhaustive-automation-testing/test-pyramid.png)

> _Tests Pyramid. Source: Martin Fowler's blog_

You must have heard about the test pyramid in the context of Agile.

The test pyramid is a representation of the different types of testing methodologies you can use and how should you be using them. It's recommended that you have a lot of unit tests, fewer integration tests, and even fewer UI tests. Generally, in the ratio of 70:20:10. This is recommended as unit tests cost less to maintain and are faster to run. As you move up the pyramid, the tests get slower and cost more to maintain.

This article is advocating having lots of functional/UI tests. Don't get me wrong, I'm not suggesting an anti-pattern like Hourglass or Inverted pyramid. I'm suggesting using the same pattern but having more functional/UI tests - as many as you can have.

> _But, aren't you writing redundant tests?_

Well, not actually, unit tests are good but they don't really reflect what a user will see. They do provide you coverage but things can still mess up.

![Image title](https://d33wubrfki0l68.cloudfront.net/364d7798c48d225a1a2d84cccb1bf34a74059f2d/e3449/assets/images/exhaustive-automation-testing/no_integration_test.gif)

> Doesn't the picture say a lot? 

One problem that I have with unit testing is that everything is mocked, so when you change some code in one class, you can get away with not changing the test of its consumers. Consumers, however, will have this class mocked so the new behavior is not being handled by the consumer. This can land you in trouble at times. As this happens more and more you'll end up with code that works great alone but fails when put together.

Such scenarios can be prevented with integration tests and functional/UI tests.

. . .

Even though things can be handled with integration tests I'd still say that we should be writing functional/UI tests because integration tests are dependent on application code as they test a certain part of code coupled together, though some mocking is still required. This is the same problem that unit testing has but instead of between classes now the problem not sits between modules.

On the other hand, UI or functional tests are isolated from application code and they will never be affected by any change in the code unless the functionality changes.

Even in the case of a complete application rewrite or major code refactoring, these test won't require changes, as they mock only external dependencies. It gives you more confidence when your existing tests are passing.

Assume you have a web application that has undergone exhaustive UI tests that have every user flow covered as part of its automation.

Consider this web application to be a huge monolithic application which is deployed on a single server and turns out your company is booming. You have more and more users coming in every day. You are having the time of your life. But, your servers aren't, they can't handle all the load.

> What do you do? 

You either throw more hardware at it or you change the code to handle more load. But there is only so much you can do without any radical changes.

Microservices can help you scale better. But that would require a rewrite of the application and also require a lot of time to build and test it. You can save yourself from all of this if you have exhaustive functional/UI tests in place to verify all the user flows.

Make changes in the application code all you want. Your functional test suite is there to cover you. Now you can develop that microservices architecture for your backend and be sure that existing functionalities will not break.

Try doing all this with your puny unit tests. No offense, unit tests have their place in the testing world, but, in this case, I'd give the trophy to functional tests.

Point being, the closer a test is to the application code the less reliable it is from a functional perspective. Your class might handle null better but it doesn't know a users perspective. UI tests, simply put, are automating manual testing. And nothing can beat looking at the actual thing.

_Do you see why exhaustive functional/UI tests are not redundant?_

. . .

> What you are saying requires a lot of time and effort. 

On a small scale, shoestring budget project this makes little sense. The cost of creating all these tests and maintaining them is far greater than the benefits that it comes with.

But consider a company whose bread and butter is the software that they make or their business is somehow dependent on their website/app/software to bring in revenue. In such cases, a customer-facing application/website must be top notch or you lose customers.

_In my personal opinion user experience is very important. It's user experience that makes you stand out in a crowd of companies that are trying to be different but are doing almost the same thing._

These companies or projects need to stay competitive and, to that end, they make radical changes frequently. They follow Agile practices like CI/CD ([Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration) and [Continuous Delivery](https://en.wikipedia.org/wiki/Continuous_delivery)).

If you are aiming for CD (Continuous Delivery) but are struggling to do so, then this approach just might help you. I've generally seen people doing CI but not CD. The problem I've seen is the confidence in code and tests.

A feature requirement comes, you analyze it, your team develops it, and then it goes off for testing. All your unit and integration tests are passing. But still, a bug comes up. Won't be the first, I'm sure almost everyone would have seen this in the past. Incidents like this destroy the confidence in a test suite. Which is why people shy away from CD. But if you have exhaustive functional tests you can lower such incidents to almost zero.

A typical project has a low amount of functional coverage. With every release, they have some amount of manual testing where they test new and old features that are not broken.

I'm proposing that we remove all the manual effort and only do manual on tests that can't be automated. Writing functional/UI automation tests for everything possible looks like a lot of effort. But, for a project that has a long shelf-life, this is a bargain. You'd never have to manually check any functionality again and if that test is passing you'd be sure that nothing will break.

Some companies follow true CD, where one commits all the tests that are executed and it automatically goes to production unless manually stopped. These companies have great confidence in their automation. This helps them stay on top of their game. CD also helps you with lower time to market. And having an exhaustive test suite helps achieve CD.

_So, all in all, if you have a business critical application, you'd be actually be lowering your cost of testing and gaining opportunity cost thanks to lower time to market. And in case of any architecture change or even an application rewrite you will have a test suite that you can rely on._

. . .

### A Few More Things

#### **Behaviour-Driven Development**

If you choose to practice what I explained, you can try practices like BDD ([Behaviour driven development](https://en.wikipedia.org/wiki/Behavior-driven_development)) to further optimize the throughput of your team. In this, you'd be creating all the possible scenarios as functional tests before development starts and the development objective is to pass these tests. So, you end up with an even shorter delivery cycle.

#### **Consider This Exhaustive Test Suite as Your Regression Test Suite**

Think of this test suite as regression because it won't be very useful for minor changes. It will, however, definitely save you when the stakes are higher. These tests take a lot of time to run and having lots of them makes feedback cycles even longer. I'd suggest you don't run them for every commit.

#### **Pick Your Tool Carefully**

UI tests have a reputation for being flaky and I agree with that. Pick a tool that is not flaky or is the least flaky.

#### **No More Documentation**

Your shiny new test suite is the only documentation you'd ever need. Just refer to this to know any functional detail about the software.

#### **Keep Your Test Suite Separate From the Application Code**

Keeping the test and app code separate will help you in case of any major changes/refactoring. Changing the code of your application should not affect your tests unless any functional change comes in.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
