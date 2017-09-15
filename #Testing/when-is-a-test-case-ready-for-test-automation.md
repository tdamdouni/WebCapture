# When Is a Test Case Ready for Test Automation?

_Captured: 2017-09-04 at 22:43 from [dzone.com](https://dzone.com/articles/when-is-a-test-case-ready-for-test-automation-1?oid=twitter&utm_content=buffer226a9&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Getting to continuous deployment can be tough. Discover [best practices to speed up your development cycles](https://dzone.com/go?i=227264&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) and techniques to minimize regressions and bugs. Brought to you by [Rainforest QA.](https://dzone.com/go?i=227264&u=https%3A%2F%2Fwww.rainforestqa.com%2F%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone)

_This article is featured in the new DZone Guide to [Automated Testing](https://dzone.com/guides/automated-testing-improving-application-speed-and). Get your free copy for more insightful articles, industry statistics, and more!_

There are so many things you need to think about when working on software projects: what problem you want to solve, if software is actually the best way to do it, what technology to use, how to structure your teams, which development methodology to use, and -- finally -- what and how often to test?

That last part is often left as an afterthought, but that's not always a bad decision! After all, going from "no solution" to "some solution" is the first step and it does not, strictly speaking, require having good test coverage. However, as your product and your organization mature, testing and Quality Assurance become more and more critical to your success. Learning this lesson took us, as an industry, time and some painful lessons.

While these days most professional software developers agree that QA is important, we are still working out the best way to implement it. What seems clear, however, is that the ideal QA strategy should fit right into a modern continuous integration pipeline, and therefore be fast and reliable. Today, we'll discuss how to identify test cases that are ready for testing automation as part of your QA strategy, and how to gain the most from its benefits while minimizing its downsides.

## Creating a Balanced Test Automation Strategy

One of the choices you have to make when thinking about your QA strategy is between automatic and manual testing, and it's almost always a balance; there are few situations really suitable for a 100% approach one way or the other.

First, to get the obvious out of the way: some things, like unit tests, are unambiguous. You should always have some form of automated unit tests! Other things, like penetration testing and usability research, almost always require a human touch. The boundary between these two is where things get interesting.

So what are the trade-offs? Well, I'm glad you asked! That's something I tend to think about a lot, so let me try to give you a breakdown of what we've got.

## Functional Test: To Automate, or Not to Automate?

Let's focus on functional testing, which in the world of web applications, usually means testing the UI and flow of your app. Once you have a working app with a UX flow you are comfortable with and ship it to production, you'll want it to have some functional test coverage. This coverage is designed to make sure you can safely iterate and improve it over time without breaking the ability of your users to achieve things. Should you test it using an automated or manual approach?

Automated tests are great because executing them is free and they are usually fast. These are huge bonuses when you are trying to save development time, which is usually one of your most precious resources. Once you have, for example, a working Selenium script, you can run it as often as you want and get the results fairly quickly. The problem is that these tempting savings only come in after the initial (and often significant) investment of -- you guessed it -- dev time to write such scripts. Worse still, some automated tests tend to break unexpectedly as you change your application, so you need to continually reinvest into keeping them up-to-date.

Manual testing doesn't have this problem. It will generally work as expected, giving you reliable results without you having to specify every tiny detail. The drawbacks, however, are significant: manual testing generally creates high, persistent costs and long turnaround times.

From this, some clear pictures start to emerge. If you have a fairly stable component that you need to test often, automation is probably the way to go. Every time you execute your test suite, you will rake in a return on your initial investment. Assuming the unexpected breakages don't happen too often, the continuous maintenance will not hurt you either, because you only need to fix your test scripts when things break. On the other hand, if you are testing something that tends to change frequently and especially if you don't test often (which you should be doing, but life is not always simple) you might be better off going through a manual testing phase before every release.

## Determining When to Use Test Automation

The next question is, how can we assess when and how often something is going to break? This is a tough question to answer and it heavily depends on your specific situation. Luckily, smart people have done some work for us already! For instance, [this paper](http://ieeexplore.ieee.org/abstract/document/7515470/?part=1) discusses the most common ways in which automated tests of web applications tend to break (while they mostly talk about record/replay tests, the same principles apply to hand-crafted testing scripts). The authors created suites of automated tests for early versions of five different open source web applications and then executed these tests for each subsequent version. Every time a test broke, they recorded the breakage reason, fixed the test, and continued testing. This way, they created a very unique dataset, which makes it possible to explore the most common failure reasons.

Broadly, they describe five main types of test breakages. Thinking about these potential breakage risks should give you some idea which areas of your applications might be suitable for test automation, and which are better served by manual QA.

### 1\. Element Locators-Based Breakage

When your test script validates something, it usually needs to find and inspect a DOM element, whether by its attribute, text, or place in the hierarchy. Each of these ways can break: changing page styles, updating copy, or restructuring your layout can all threaten your ability to find the same thing reliably. This is by far the most common cause of breaking automated tests, and one that is very difficult to mitigate. This is one of the reasons why humans are still much more robust testers than machines!

### 2\. Value-Based Breakage

When testing text input fields, you often want to make sure they accept the correct values and raise appropriate errors when the provided values are invalid. Whenever you change your backend, e.g. the requirements for passwords when testing a password input field, you need to update your test to prevent it from breaking. Similarly, if you add a new, required input field, your old automation script will try to submit a form with missing data unless you update it.

Another common case is asserting that a specific error message appeared and then updating the error message, which will also break the script.

### 3\. Page Reloading

Depending on your backend, going through some user flows might require page reloads. On the other hand, reloading a page at the wrong time can often break the test! Changes to your application can often result in broken reload login test scripts, because of: 1) reloads being required at different points; 2) reloads no longer happening (while the script is still expecting them); 3) reloads potentially requiring different amounts of time than previously (since explicit "sleep" times are often used to allow the page to reload before continuing, changing the logic behind the reload might render the original wait time insufficient).

### 4\. User Session Times

Many applications implement logic to log out inactive users after a set amount of time and use test scripts that are intentionally inactive for a while and validate that the expected action (warning and/or logging the user out) happens when expected. Such tests are likely to break whenever the allowed session time changes.

### 5\. Pop-Up Windows

Pop-ups, whether windows or alerts, are often used in web applications and need to be tested. It's therefore common for test scripts to assert either the presence or absence of pop-ups, which will break whenever the application is updated to change the relevant behavior. While the paper authors have found this to be one of the least-frequent reasons for broken tests, here at Rainforest we have seen our customers being affected by this particular issue often enough to develop a specific set of rules for testers to follow when testing pop-up behavior.

## The Takeaway: Leverage Test Automation Strategically

Test automation is great for development -- it not only gives you a peace of mind about being able to serve your customers well and without hiccups, but also allows you to move at a much faster pace because your team spends less time dealing with QA overhead and the consequences of bugs in production. When done well it can truly supercharge your development efforts, but it is not without pitfalls. Thinking carefully about your QA strategy and about which parts of your test suite can be automated will definitely pay off.

_This article is featured in the new DZone Guide to [Automated Testing](https://dzone.com/guides/automated-testing-improving-application-speed-and). Get your free copy for more insightful articles, industry statistics, and more!_

Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=227267&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) with our cloud-powered testing platform, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=227267&u=https%3A%2F%2Fwww.rainforestqa.com%2F%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone).
