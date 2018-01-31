# TDD Gamification – Turning Test Driven Development into a Game

_Captured: 2017-05-06 at 00:28 from [blog.dmbcllc.com](https://blog.dmbcllc.com/tdd-gamification/)_

![ge-gam-018](https://blog.dmbcllc.com/wp-content/uploads/2015/04/ge-gam-018.jpg)

> _Test Driven Development Gamification_

When I was in college, there were some guys I hung out with who played this game called "Questions" which they got from some book. [Actually, it was a play](https://en.wikipedia.org/wiki/Questions_%28game%29).

Anyhow, the basic rules are:

  * You can't answer a question with a statement
  * You can't hesitate or make a false start
  * You can't repeat a question that has already been used
  * You can't ask a rhetorical question
  * You can't ask an unrelated question.

There was also [this podcast at DotNetRocks](http://dotnetrocks.com/default.aspx?showNum=1111) where they were talking about a beer app and how they had added game elements to the app by adding badges for various types of beer to get you out of your comfort zone. Maybe there is one for "My first beer that I liked" because I've yet to find something I like. But give me a good Merlot!

All of this got me to thinking about how we might turn Test Driven Development into something of a game.

There are several people who have already addressed the Gamification of TDD

This article talks mostly about how TDD has many elements of good gaming inherent in it.

  * Because it makes testing more like programming. Well, what he actually says is that it raises testing to the level of complexity the programmer is familiar with. But in reality, I think this is because it makes testing something that can be coded.
  * Because TDD is measurable. The test either succeeds or fails.
  * Because TDD gives you immediate feedback. Or at least a well written test gives you immediate feedback.

This article provides an interesting perspective of someone trying to program using TDD for the first time. You get the normal complaints, like "this takes too long" along with acknowledgement of some of the benefits. But what he realizes is that the process has made programming more like a game than about the creative problem solving most of us got in to programming for in the first place.

## [Gamify TDD](http://www.tdddev.com/2014/09/gamify-tdd.html)

This is the first article I found that, instead of saying that TDD is already a game, like the two above, actually ask how we might formally turn TDD into a game because it already has many elements of a game. But he never actually says HOW he would do that.

## TDD Gamification

Putting this all together. Here is how I would actually make TDD into a game.

#### The rules:

  * The game is played in pairs. (Paired programming)
  * Game starts when programmer 1 writes the first test.
  * Once a failing test is written, programmer 2 writes JUST ENOUGH to make the test succeed.
  * Once a test succeeds, programmer 2 writes another test, and programmer 1 writes just enough to make it succeed.
  * Play alternates until no one can think of another test that will force more code to be written.
  * Programmer loses points if he is caught writing more code than is necessary to pass the test.
  * Programmer loses points if he is caught writing code that has dependencies embedded in it.
  * If a dependency is required, the test writer and the code implementer will collaborate in the method of dependency injection to be used.
  * All points lost by one programmer go to the programmer who caught the mistake.

#### Embellishment:

If code is found to have a bug in production, both programmers responsible for the code loose a point, regardless of how many lines of code are impacted. One point per recorded bug.

I'm assuming that most shops have more than 2 programmers. On any given day, programmers would be paired up for the day of programming. They are responsible for turning out bug free code. Because we are tracking the code over the long term, we will be able to see just how effective each programmer is at eliminating bugs.

In fact, if you are in an environment that can't quite stomach having your programmers paired up, I would suggest keeping track of the code that wasn't done under the game. This would be the "house score" compared to an individual programmer's score.

The only thing we have left is some way of being able to account for productivity. I mean, if I write no code, I'll have no bugs, right? And all things being equal, the more productive I am, the more bugs I'll have. So how do we measure this?

Here is what we can't do:

  * Lines of code - you can't measure based on lines of code because that has been shown to be an inaccurate measure of productivity. More lines may just mean you are not very efficient.
  * Hours worked - [Rapid Development](https://blog.dmbcllc.com/rapidDevelopment) has statistics in it that show there is a factor of 10 difference between good programmers and bad programmers.

#### Just a suggestion:

Since short methods are desirable, what if we measure number of test relative to number of methods relative to number of classes. This would enforce the single responsibility principle.

T = Tests

M = Methods

C = Classes

1/((T/M)/C) = Productivity Score

Therefore,

  * If I worked on 3 classes each with 6 methods and each method has 2 tests, I end up with a productivity score of 1.5
  * If I had one class with 18 methods each with 2 tests, I end up with a productivity score of .5
  * If, on the other hand, I put everything in one method, and one class and had the same 36 tests, my productivity score would be .02
  * If you write no code, your productivity score is 0.

That's just a simple way to calculate. You may choose to use cyclomatic complexity in some way if you have that number easily available to you.

Well, that's my rough sketch of how we might be able to turn TDD into something of a game along with being able to prove to ourselves and management that it really does produce better code.

How else might you embellish this or change it so it works better? Let me know in the comments below.

#### Other Test Driven Development Resources

This page contains copyright material from [//blog.dmbcllc.com](https://blog.dmbcllc.com) and you have no rights to copy and paste the full text into your own blog even if you have written permission to the contrary. Violations will be reported.

**Other post in TDD**

  * [Test Driven Specifications](https://blog.dmbcllc.com/test-driven-specifications/) \- February 25th, 2014
  * [Unit Test Structure](https://blog.dmbcllc.com/unit-test-structure/) \- March 11th, 2014
  * [What Not To Test](https://blog.dmbcllc.com/what-not-to-test/) \- April 9th, 2014
  * [The Proper Function of QA](https://blog.dmbcllc.com/the-proper-function-of-qa/) \- May 1st, 2014
  * [Selenium Performance Improvements](https://blog.dmbcllc.com/selenium-performance-improvements/) \- October 2nd, 2014
  * [Technical Debt Is Inevitable](https://blog.dmbcllc.com/technical-debt-is-inevitable/) \- October 16th, 2014
  * [NUnit &amp; Visual Studio](https://blog.dmbcllc.com/nunit-visual-studio/) \- December 4th, 2014
  * [NUnit Test Code Structure](https://blog.dmbcllc.com/nunit-test-code-structure/) \- February 5th, 2015
  * [Excuses For Not Testing](https://blog.dmbcllc.com/excuses-for-not-testing/) \- February 26th, 2015
  * [Changing Habits](https://blog.dmbcllc.com/changing-habits/) \- March 19th, 2015
  * [100% Code Coverage Possible?](https://blog.dmbcllc.com/100-code-coverage/) \- March 26th, 2015
  * [The Fallacy of Motion](https://blog.dmbcllc.com/the-fallacy-of-motion/) \- July 23rd, 2015
  * [Test Driven Learning - An Experiment](https://blog.dmbcllc.com/test-driven-learning-an-experiment/) \- March 24th, 2016
  


I've talked around NgRX several times over the last few months but I've yet to write an article on how to use NgRX. This is because I was under the impression that there were better articles available. And while there are a lot of articles available, there is not anything I feel comfortable sending another programmer to who is trying to learn NgRX.

So, rather than spend a lot of time on why you want to learn NgRX, or arguing against some of the unfounded hesitations, today I'm just going to dive into how to use NgRX.

![How to Really use NgRX](https://blog.dmbcllc.com/wp-content/uploads/2017/04/image-6.png)

> _Photo credit: Bilal Kamoon via VisualHunt / CC BY_
