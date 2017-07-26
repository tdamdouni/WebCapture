# If You Automate Your Tests, Automate Your Code Review

_Captured: 2017-06-23 at 13:40 from [dzone.com](https://dzone.com/articles/if-you-automate-your-tests-automate-your-code-revi?edition=305129&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-22)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

_Editorial Note: I originally wrote this post for the SubMain blog. You can [check out the original here, at their site](http://blog.submain.com/if-you-automate-your-tests-automate-your-code-review/). While you're there, have a look at CodeIt.Right._

For years, I can remember fighting the good fight for unit testing. When I started that fight, I understood a simple premise. We, as programmers, automate things. So, why not automate testing?

Of all things, a grad school course in software engineering introduced me to the concept back in 2005. It hooked me immediately, and I began applying the lessons to my work at the time. A few years and a new job later, I came to a group that had not yet discovered the wonders of automated testing. No worries, I figured, I can introduce the concept!

![Image title](http://www.daedtech.com/wp-content/uploads/2016/05/Archemedies-Running-Naked-Yelling-Eureka.png)

Except, it turns out that people stuck in their ways kind of like those ways. Imagine my surprise to discover that people turned up their nose at the practice. Over the course of time, I learned to plead my case, both in technical and business terms. But it often felt like wading upstream against a fast moving current.

Years later, I have fought that fight over and over again. In fact, I've produced training materials, courses, videos, blog posts, and books on the subject. I've brought people around to see the benefits and then subsequently realize those benefits following adoption. This has brought me satisfaction.

But I don't do this in a vacuum. The industry as a whole has followed the same trajectory, using the same logic. I count myself just another advocate among a euphony of voices. And so our profession has generally come to accept unit testing as a vital tool.

### Widespread Acceptance of Automated Regression Tests

In fact, I might go so far as to call acceptance and adoption quite widespread. This figure only increases if you include shops that totally mean to and will definitely get around to it like sometime in the next six months or something. In other words, if you count both shops that have adopted the practice and shops that feel as though they should, acceptance figures certainly span a plurality.

Major enterprises bring me in to help them teach their developers to do it. Still, other companies consult and ask questions about it. Just about everyone wants to understand how to realize the unit testing value proposition of higher quality, more stability, and fewer bugs.

This takes a simple form. We talk about unit testing and other forms of testing, and sometimes this may blur the lines. But let's get specific here. A holistic testing strategy includes tests at a variety of granularities. These comprise what some call "[the test pyramid](https://martinfowler.com/bliki/TestPyramid.html)." Unit tests address individual components (e.g. classes), while service tests drive at the way the components of your application work together. GUI tests, the least granular of all, exercise the whole thing.

Taken together, these comprise your _[regression test suite](https://en.wikipedia.org/wiki/Regression_testing)_. It stands against the category of bugs known as "regressions," or defects where something that used to work stops working. For a parallel example in the "real world" think of the warning lights on your car's dashboard. "Low battery" light comes on because the battery, which used to work, has stopped working.

### Benefits of Automated Regression Test Suites

Why do this? What benefits to automated regression test suites provide? Well, let's take a look at some.

  * Repeatability and accuracy. A human running tests over and over again may produce slight variances in the tests. A machine, not so much.
  * Speed. As with anything, automation produces a significant speedup over manual execution.
  * Fast feedback. The automated test suite can tell you much more quickly if you have broken something.
  * Morale. The fewer times a QA department comes back with "you broke this thing," the fewer opportunities for contentiousness.

I should also mention, as a brief aside, that I don't consider automated test suites to be acceptable _substitutes_ for manual testing. Rather, I believe the two efforts should work in complementary fashion. If the automated test suite executes the humdrum tests in the codebase, it frees QA folks up to perform intelligent, exploratory testing. As [Uncle Bob once famously said](https://sites.google.com/site/unclebobconsultingllc/tdd-with-acceptance-tests-and-unit-tests), "it's wrong to turn humans into machines. If you can write a script for a test procedure, then you can write a program to execute that procedure."

### Automating Code Review

None of this probably comes as much of a shock to you. If you go out and read tech blogs, you've no doubt encountered the widespread opinion that people should automate regression test suites. In fact, you probably _share_ that opinion. So don't you wonder why we don't more frequently apply that logic to other concerns?

Take code review, for instance. Most organizations do this in entirely manual fashion outside of, perhaps, a so-called "linting" tool. They mandate automated test coverage and then content themselves with sicking their developers on one another in meetings to gripe over tabs, spaces, and camel casing.

Why not approach code review the same way? Why not automate the aspects of it that lend themselves to automation, while saving human intervention for more conceptual matters?

### Benefits of Automated Code Reviews

In a study by Steve McConnell and [referenced in this blog post](https://kev.inburke.com/kevin/the-best-ways-to-find-bugs-in-your-code/), "formal code inspections" produced better results for preemptively finding bugs than even automated regression tests. So it stands to reason that we should invest in code review in the same ways that we invest in regression testing. And I don't mean simply time spent, but in driving forward with automation and efficiency.

Consider the benefits I listed above for automated tests, and look how they apply to automated code review.

  * Repeatability and accuracy. Humans will miss instances of substandard code if they feel tired -- machines won't.
  * Speed. Do you want your code review to take seconds or hours/days?
  * Fast feedback. Because of the increased speed of the review, the reviewee gets the results immediately after writing the code, for better learning.
  * Morale. The exact same reasoning applies here. Having a machine point out your mistakes can save contentiousness.

I think that we'll see a similar trajectory to automating code review that we did with automating test suites. And, what's more, I think that automated code review will gain steam a lot more quickly and with less resistance. After all, automating QA activities blazed a trail.

I believe the biggest barrier to adoption, in this case, is the lack of awareness. People may not believe automating code review is possible. But I assure you, you can do it. So keep an eye out for ways to automate this important practice, and get in ahead of the adoption curve.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
