# The Clean Code Blog

_Captured: 2015-10-17 at 22:07 from [blog.cleancoder.com](http://blog.cleancoder.com/uncle-bob/2014/09/03/TestTime.html)_

# Test Time

I was working with a client a few weeks ago; and they told me that it took several minutes to run their unit tests. I suggested that they run a smaller suite; and they responded by telling me that the issue wasn't the runtime of the tests, but the _build time_. They were using C++, and it took several minutes to build and link an executable that could run even a small suite of tests.

I told them that they should link with smaller libraries, and make sure that the dependencies between those libraries were unidirectional, concrete to abstract, in order to shorten their link times. "After all," I said "if you limit the amount you link, the link time can be less than a second."

They responded by telling me that their unit testing library was one of the reasons that the link time was so slow. This took me by surprise since I couldn't imagine a unit testing library that would be large enough to slow down the link time appreciably. So I told them: "If your unit testing tool is slowing down the tests, you need a new tool."

Their response was that this tool was _the best tool out there_.

Here's a clue: If your testing tool is the reason it takes a long time to run your tests, then it's not the best tool for the job -- let alone the best tool out there.

### Fast.

Tests need to run fast. _Anything_ that gets in the way of fast test times is forfeit, no matter what other wonderful benefits it may provide. It may have really super mocking tools; but if it's slow, drop it!. It may be endorsed by all the top gurus; but if it's slow, burn it!. It may be the tool that ships with your IDE; but if it takes ten seconds just to start testing, toss it! Allow _nothing_ to slow down your tests.

Why? Simple. Slow tests aren't run often enough. The slower the tests the less frequently they are run. The less frequently the tests are run, the more invested you get in the code you write between the test runs; and the more you will allow the code to rot just to avoid another expensive test run.

The primary benefit of TDD is the ability to refactor without fear, and without cost. The slower your tests run, the higher the refactoring cost. The higher the refactoring cost, the faster your code will rot. And rotten code slows everything else down. _Don't let the tests get slow!_

### A Design Challenge

Keeping the tests running very fast is a design challenge. It's one of the design constraints that well heeled craftsmen put upon themselves. They purposely design the system so that the test time is fast. That means choosing fast testing tools and building decoupled architectures. That means _thinking_ about how to keep the tests running fast all the time; and _refactoring_ when the tests start getting slow.

Decoupled architectures allow you to build fast test doubles that stub out subsystems that are traditionally slow. For example, if your system is well decoupled, it is trivial to stub out the database or the web server. If the system is well decoupled, all slow operations fall on the far side of an architectural boundary that can be stubbed. And that stubbing can turn a test that takes minutes, into a test that runs in milliseconds!

### FitNesse

I and my associates have been working on FitNesse for well over 10 years. FitNesse is around 72,000 lines of Java code nowadays; 31,000 of those lines are unit tests. There are also nearly three hundred acceptance tests (FitNesse tests). The compile/build/test time for the whole project (on my laptop) is about one minute and 45 seconds. Typically we don't run the acceptance tests while we are in the fast red/green/refactor loop. Indeed, we usually only run a subset of the unit tests in that loop. So running the tests in the red/green/refactor loop seldom takes more than two or three seconds. _That's the kind of test speed you are after!_

To attain those speeds we stub out all the slow things like the persistence framework, and the web framework. We stub them in the unit tests. We stub them in the acceptance tests. _Anything_ that runs slow, we stub.

Of course not all the tests stub those things out. Some of the tests go all the way through from web server to database. But well over 90% of those tests bypass the slow stuff. After all, how many times do you need to tests the database to know that it works? How many times do you need to test the web server to know that it works? The answer to both questions is pretty close to one. So testing those slow things much more than once is a waste of time.

### Conclusion

Programmers who care about their systems, care about the tests for those systems. Programmers who care about the tests, make sure those tests run _fast_. Slow running tests represent a design flaw that reflects on the experience and professionalism of the team. A slow running test suite is either a freshman error, or just plain carelessness.
