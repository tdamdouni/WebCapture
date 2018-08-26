# Three Distinct Mindsets in TDD

_Captured: 2018-07-13 at 17:00 from [dzone.com](https://dzone.com/articles/three-distinct-mindsets-in-tdd?edition=385232&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-07-13)_

Read why times series is the [fastest growing database](https://dzone.com/go?i=283423&u=https%3A%2F%2Fwww.influxdata.com%2Ftime-series-database%2F) category.

[I have blogged about TDD before](http://www.davefarley.net/?p=220). I think that it is one of the most important tools in improving the design of our software, as well as increasing the quality of the systems that we create. TDD provides valuable, fine-grained feedback as we evolve the solutions to the problems that our code is meant to address.

Oh yes, and as a side-benefit, you get some nice, efficient, loosely coupled tests that you can use to find regression problems in future.

I sometimes teach people how to practice TDD more effectively, and one of the things that I notice is that one subtlety that people often miss is the difference in focus for each of the TDD steps.

True TDD is very simple, it is "RED, GREEN, REFACTOR."

  * We write a test, run it and see it fail (RED).
  * We write the minimum code to make it pass, run it and see it pass (GREEN).
  * We refactor the code, and the test, to make them as clean, expressive, elegant and simple as we can imagine (REFACTOR).

These steps are important not just as a teaching aid, but also because they represent three distinct phases in the design of our code. We should be thinking differently during each of these steps...

## RED

We should be wholly focussed on expressing the behavioral need that we would like our code to address. At this point, we should be concentrating only on the public interface to our code. That is what we are designing at this point, nothing else.

If you are thinking about how you will implement this method or class, you are thinking of the wrong things. Instead, think only about how to write a nice clear test that captures just what you would like your code to do.

This is a great opportunity to design the public interface to your code. By focusing on making the test simple to write, it means that if ideas are easy to express in our test, they will also be easy to express when someone, even you in the future, uses your code. What you are really doing, at the point when you strive for a simple, clear test, is designing a clean, simple to use, easy to understand API.

Treat this as a distinct, separate step from designing the internal workings of the code. Concentrate only on describing the desired behavior in the test as clearly as you can.

## GREEN

Experienced TDD practitioners, like me, will tell you to do the simplest thing that makes the test pass. Even if that simple thing is trivial, or even naive. The reason that we advise this is because your code is currently broken, the test is failing. You are at an unstable point in the development.

If you start to try and do more complex things at this point, like make your design elegant or performant or more general, you can easily get lost and get stuck in a broken state for a while.

If the "simplest thing" is to return a hard-coded value, hard-code it!

This does a couple of things. It forces you to work in tiny steps, a good thing, and it also prompts you to write more tests that allow you to expand the logic of your code, another good thing.

Your tests should grow to form a "behavioral specification" for your code. Adopting the discipline of only writing production code when you have a failing test helps you to better elaborate and evolve that specification.

Don't worry, we won't forget to tidy-up the dumb, overly simplistic things that we do at this point.

Over-complicating the solution is one of the commonest mistakes that I see TDD beginners make. They try to capture too much in one step. They prefer to have fewer more complex tests than many, small, simple tests that prod and probe at the behavior of their system. The small steps, in thinking and in code, help a lot. Don't be afraid of many small simple tests.

## REFACTOR

Always refactor on a passing build. Wait until you are in the "GREEN" state before you begin. This keeps you honest and stops you wandering off into the weeds and getting lost! Make small simple steps and then re-run the tests to confirm that everything still works.

Refactoring is not just an afterthought, it is not just about aligning the indents and optimizing the imports. This is an opportunity to think a bit more strategically about your design.

It is important that we treat it as a separate step. I often see things that I want to change either when writing a test (RED) or when writing code to make the test pass (GREEN). On my good days, I remember that this is not the time. I make a note and come back to it once the test is passing. On my bad days I often end up making mistakes, trying to do things in steps that are too big an complicated, rather than small and simple, and so I end up having to revert or at least think a lot harder than I need.

If you use a distributed VCS like GIT, I recommend that after each refactoring step, after you have checked that the tests all pass, commit the change. The code is working, and the committed version gives you a chance to step back to a stable state if you wander-off into more complex changes by mistake.

In general, I tend to commit locally after each individual refactoring step and push to origin/master after finishing refactoring, but before moving on to the next test.

Another beginner mistake that I frequently observe is to skip the refactor step altogether. This is a big mistake! The refactor step is the time to think a little bit more strategically. Pause and think about the direction in which your code is evolving, try and shape the code to match this direction. Look for the cues that tell you that your code is doing too much or is too tightly-coupled to surrounding code.

One of my driving principles in design is "separation of concerns" if your code is doing "something AND something else" it is wrong. If your code is doing a business level calculation and is responsible for storing the results - wrong! These are separate and distinct concerns. Tease out new classes, new abstractions that allow you to deal with concerns independently. This naturally leads you down the path towards more modular, more compose-able designs. Use the refactoring step to look for the little cues in your code that indicates these problems.

If the set-up of your tests is too complex, your code probably has poor separation of concerns and may be too tightly-coupled to other things. If you need to include too many other classes to test your code, perhaps your code is not very cohesive.

Practice a pause for refactoring every single time you have a passing test. Always look and reflect "could I do this better?" even if sometimes the answer is "no, it is fine."

The three phases of TDD are distinct and your mental focus should also be distinct to maximize the benefit of each phase.

Learn how to get 20x more performance than Elastic by [moving to a Time Series database](https://dzone.com/go?i=283422&u=https%3A%2F%2Fwww.influxdata.com%2Fresources%2Fbenchmarking-influxdb-vs-elasticsearch-for-time-series%2F%3Futm_campaign%3Ddbzone%26utm_medium%3Dpartner%26utm_source%3Ddzone%26utm_content%3D%26utm_term%3D).
