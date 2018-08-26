# Why Write the Test First

_Captured: 2018-06-08 at 17:26 from [dzone.com](https://dzone.com/articles/why-write-the-test-first?edition=379250&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-06-08)_

[Learn how error monitoring with Sentry](https://dzone.com/go?i=286425&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzoneperformancezone%26utm_campaign%3Dsponsorship) closes the gap between the product team and your customers. With Sentry, you can focus on what you do best: building and scaling software that makes your users' lives better.

As you can probably tell by reading my blog, I am a proponent of TDD. But my enthusiasm for test-first development took a long time coming. It took me a long time to convince myself that TDD had great value and was worth the effort. Software developers already have too much to do and not enough time so adding an additional practice to our already tight schedules is something that caused me great trepidation.

But I believe that doing TDD, if we do it correctly, can simultaneously improve quality while reducing our workloads. This happens because adding the practice of TDD can let us remove several things that were actually major impediments to the software development process.

I don't usually find the developers like to read and interpret long-winded requirements and statistically, it consumes 30 to 50% of software development efforts, if we also include the time spent capturing requirements. I find I spend far less time reading and interpreting requirements when I have acceptance tests driving my development.

The place that developers lose most of their time is typically in debugging and it's not a very fun activity. I used to be an expert with the debugger but now I find that I'm rarely in it these days because my unit tests find problems for me before they can even become defects.

As soon as I type a mistake, my unit tests tell me there's a problem while it is still fresh in my mind and I can quickly fix it. I hardly notice defects when I'm doing this and in just a few seconds I fix what could have become a showstopper defect for me if I was made aware of them long after I've forgotten the code that I was working on, which for me is just a few days.

Very few developers can be intimately familiar with code that they wrote, even a few weeks ago, and so there is a learning process or I should say a re-learning process to get ourselves back up to speed with code before we can start to debug it and that's time-consuming, as well as being a fairly unpleasant activity.

Developers love to develop. It's what we're good at and what we're paid to do. So, many of us feel a bit frustrated when our company's development process has us in meetings or writing programmer documentation or interpreting requirements or estimating work to be done.

These activities can be valuable but they're never nearly as valuable as producing working software. That is what we are paid to do and that is what we love doing but unfortunately, in many organizations programming can be a programmer's last responsibility. I know some companies who keep their developers in meetings so much of the time that they only have about 20% of their time available to actually write code. A good software development process has most of the developer's time devoted to writing software.

One thing that I love about doing test-first development is that it is coding. Tests are code and writing tests is writing code. When developers get that they can spend time doing TDD instead of writing programmer documentation or doing extensive debugging then they recognize a lot of the value inherent in TDD. I've written a lot about the value of automated regression tests and this is yet another benefit from doing TDD.

But perhaps the biggest benefit of doing test-first software development is that we're always writing testable code because the process forces us to. In TDD, we write the test first and then we write the implementation to make the test pass. In this context, it's pretty much impossible to write an implementation that isn't testable. So, all the code we build doing TDD is testable code. And testable code is high-quality software that's more straightforward to maintain and extend than untestable code.

[What's the best way to boost the efficiency of your product team](https://dzone.com/go?i=286426&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzoneperformancezone%26utm_campaign%3Dsponsorship) and ship with confidence? Check out this [ebook](https://dzone.com/go?i=286426&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzoneperformancezone%26utm_campaign%3Dsponsorship) to learn how Sentry's real-time error monitoring helps developers stay in their workflow to fix bugs before the user even knows there's a problem.
