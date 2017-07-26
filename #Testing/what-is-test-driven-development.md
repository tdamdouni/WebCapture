# What Is Test-Driven Development?

_Captured: 2017-02-03 at 13:46 from [dzone.com](https://dzone.com/articles/what-is-test-driven-development?utm_source=Top%205&utm_medium=email&utm_campaign=2017-02-03)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

I have a love/hate relationship with test-driven development and unit testing. I've been both an ardent supporter of these "best practices," but I've also been more than skeptical of their use.

One of the big problems in software development is when developers -- or sometimes managers -- who mean well [apply "best practices" simply because they are best practices](https://simpleprogrammer.com/2010/04/17/when-doing-the-right-thing-is-wrong/) and [don't understand their reason or actual use](https://simpleprogrammer.com/2013/02/17/principles-are-timeless-best-practices-are-fads/).

I remember working on one such software project where I was informed that the software we were going to be modifying had a huge number of unit tests -- around 3,000. Normally, this is a good sign. This probably means the developers on the project implemented other best practices as well and there is going to be some semblance of structure or meaningful architecture within the code base.

I was excited to hear this news since it meant that my job as the mentor and coach for the development team was going to be easier. Since we already had unit tests in place, all I had to do was get the new team to maintain them and start writing their own.

I opened up my IDE and loaded the project into it. It was a big project. I saw a folder labeled "unit tests." _Great. Let's run them and see what happens. _It only took a few minutes and -- much to my surprise -- all the tests ran and everything was green. They all passed.

I really became skeptical. Three thousand unit tests -- and they all passed? What is going on here?

Most of the time, when I am first pulled onto a development team to help coach them, there are a bunch of failing tests if there are any unit tests at all. I decided to spot check one test at random. At first glance, it seemed reasonable enough. It wasn't the best, most explanative test I'd ever seen, but I could make out what it was doing.

![](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/01/Testing.png)

Then I noticed something: There was no assert. [Nothing was actually being tested](https://simpleprogrammer.com/2010/03/05/the-ego-test/). The test had steps and those steps were running, but at the end of the test where it was supposed to check something, there was no check.

The "test" wasn't testing anything. I opened up another test. It was worse. The assert statement, which was testing something at some point, was commented out.

Wow, that's a great way to make a test pass: Just comment out the code that's making it fail_._

I checked test after test. None of them were testing anything. Three thousand tests and they were all worthless. There is a huge difference between writing unit tests and [understanding unit testing](https://simpleprogrammer.com/2010/10/15/the-purpose-of-unit-testing/) and test-driven development.

## What Is Unit Testing?

The basic idea of unit testing is to write tests which exercise the smallest "unit" of code possible. Unit tests are typically written in the same programming language as the source code of the application itself and written to utilize that code directly.

Think of unit tests as code that tests other code. When I use the word "test" here, I'm using it fairly liberally because unit tests aren't really tests. They don't test anything. What I mean by this is that when you run a unit test, you don't typically find out that some code doesn't work. It's when you write a unit test that you find that information out.

Yes, the code could change later and that test could fail, so in that sense, a unit test is a regression test. In general, however, a unit test is not like a regular test where you have some steps you are going to execute and you see whether the software behaves correctly or not. As a developer writing a unit test, you discover whether the code does what it is supposed to or not while you are writing the unit test because you are going to be continually modifying the code until the unit test passes.

Why would you write a unit test and not make sure that unit test passes? When you think about it this way, unit testing is more about specifying absolute requirements for specific units of code at a very low level.

You can think of a unit test as an absolute specification. The unit test specifies that under these conditions with this specific set of input, this is the output that I should get from this unit of code.

True unit testing tests the smallest cohesive unit of code possible, which in most programming languages -- at least object-oriented ones -- is a class.

## What Is Sometimes Called Unit Testing?

Oftentimes, unit testing is confused with integration testing. Some "unit tests" test more than one class or test larger units of code. Plenty of developers will argue that these are still unit tests since they are white box tests written in code at a low level.

You shouldn't argue with these people. Just know in your mind that these are really integration tests and that true unit tests test the smallest unit of code possible in isolation.

Another thing that is often called unit testing -- but isn't really anything at all -- is writing unit tests that have no assert. In other words, unit tests that don't actually test anything.

Any test, unit test or not, should have some kind of check (we call it an assertion) at the end that determines whether it passes or fails. A test that always passes is useless. A test that always fails is useless.

## The Value of Unit Testing

![](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/01/Unit-Testing-1024x576.png)

Why am I such a stickler on unit testing? What is the harm in calling unit testing real testing and not testing the smallest unit in isolation? So what if some of my tests don't have an assert? They are at least exercising the code.

Well, let me try to explain. [There are two major benefits, or reasons, to perform unit testing](https://simpleprogrammer.com/2010/10/15/the-purpose-of-unit-testing/).

The first one is to improve the design of the code. Remember how I said unit testing is not actually testing? When you write proper unit tests where you force yourself to isolate the smallest unit of code, you find problems in the design of that code.

You might find it extremely difficult to isolate the class and not include its dependencies, and that might make you realize that your code is too tightly coupled. You might find that the basic functionality you are trying to test is spread out across multiple units, and that might make you realize that your code is not cohesive enough. You might find that you sit down to write a unit test and you realize -- and believe me, this happens -- that you don't know what the code is supposed to do, so you can't write a unit test for it.

Of course, you might find an actual bug in the implementation of the code as the unit test forces you to think about some edge cases or test multiple inputs which you may not have accounted for.

By writing unit tests and strictly adhering to having them test the smallest units of code in isolation, you find all kinds of problems with that code and the design of those units. In the software development lifecycle, unit testing is more of an appraisal activity than a testing one.

The second main purpose of unit testing is to create an automated set of regression tests which can operate as a specification for the low-level behavior of the software.

What does that mean? When you change sh*t, you don't break sh*t. In that way, unit tests are tests: regression tests.

However, the purpose of unit testing is not to merely build these regression tests. In the practical world, very few regressions are caught by unit tests since changing the unit of code you're testing almost always involves changing the unit test itself.

Regression testing is much more effective at the higher level as a black box testing activity because, at that level, the internal structure of the code could be changed while the external behavior is expected to remain the same.

Unit tests test the internal structure, so when that structure changes, the unit tests don't "fail" -- they become invalid and have to be changed, thrown out, or rewritten.

Now you know more about the true purpose of unit testing than most 10-year software development veterans.

## What Is Test-Driven Development (TDD)?

![](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/01/Test-Driven-Develope-1024x576.png)

Remember the chapter where we talked about software development methodologies, and about how the Waterfall methodology often didn't work out practically because we never had complete specifications up front?

TDD is the idea that before you write any code, you write a test that acts as a specification for exactly what that code is supposed to do. [This is an extremely powerful concept in software development, but it is often misused](https://simpleprogrammer.com/2014/03/27/views-test-driven-development/).

TDD usually means using unit tests to drive the creation of the production code being written, but it can be applied at any level. For the purposes of this chapter, though, we are going to stick with the most common form of unit testing: application.

TDD flips things around so that instead of writing the code first and then writing unit tests to test that code, (which we know isn't the case anyway), you are going to write the unit test first and then write just enough code to make that test pass.

In this way, the unit test is "driving" the development of the code. This process is repeated over and over. You write another test that defines more functionality of what the code is supposed to do. You change the code or add code to make the test pass. Finally, [you refactor the code](http://amzn.to/2coV0DA) -- or clean it up -- to make it more succinct.

This is often called "red, green, refactor" because at first the unit test fails (red), then the code is written to make it pass (green), and finally the code is refactored.

## What Is the Purpose of TDD?

Just like unit testing can be a best practice that is misapplied, TDD can be, as well. It's very easy to call what you are doing TDD and to even follow the practice and not understand why you are doing it or the value (if any) it is providing.

The biggest value of TDD is that tests happen to make excellent specifications. TDD is essentially the practice of writing unambiguous specifications that can be automatically checked before writing code.

Why are tests such great specifications? Because they don't lie. They don't tell you your code should work one way and then tell you after you spend two weeks pounding Mountain Dew and getting everything working that it should actually work another way and, "It's all wrong; that's not what I said at all."

Tests, if properly written, either pass or fail. Tests specify in no uncertain terms exactly what should happen under a certain set of circumstances. So, in that respect, we could say the purpose of TDD is to make sure we fully understand what we are implementing before we implement and that we "got it right."

If you sit down to do TDD and you can't figure out what the test should test, it means you need to go ask more questions.

The other value of TDD is in keeping the code lean and succinct. Code is costly to maintain. I often joke that the best programmer is the one who writes the least code or even [finds a way to delete code](http://elegantcode.com/2010/06/06/the-best-code-you-will-ever-write/) because that programmer has found a surefire way to reduce errors and to decrease the maintenance cost of the application.

By utilizing TDD, you can be absolutely sure that you do not write any code that is not necessary since you will only ever write code to make tests pass. There is a principle in software development called YAGNI, or you ain't going to need it. TDD prevents YAGNI.

## A Typical TDD Workflow

It can be a little difficult to understand TDD from a purely academic perspective, so let's explore what [a sample TDD session](http://amzn.to/2bNG4xA) might look like.

You sit down at your desk and quickly sketch out what you think will be a high-level design of a feature to allow a user to login to the application and change their password if they forget it. You decide that you are going to start off by first implementing the login functionality by creating a class that will handle all the logic for doing the login process.

You open up your favorite editor and create a unit test called "Empty login does not log the user in."

You write the unit test code that first creates an instance of a Login class (which you haven't created yet).

Then, you write some code to call a method on the Login class that passes in an empty username and password.

Finally, you write an assertion (or assert), which asserts that the user is indeed not logged in. You attempt to run the test, but it doesn't even compile because you don't have a Login class. You remedy that situation by creating the Login class along with a method on that class for logging in and another for checking the status of a user to see if they are logged in. You leave the functionality in this class and methods completely empty. You run the test and this time it compiles but quickly fails.

Now, you go back and implement just enough functionality to make the test pass. In this case, it would mean always returning that the user is not logged in. You run the test again, and now it passes.

On to the next test.

This time, you decide to write a test called "User is logged in when the user has valid username and password."

You write a unit test that creates an instance of the Login class and try to login with a username and password. In the unit test, you write an assertion that the Login class should say the user is logged in. You run this new test and, of course, it fails because your Login class always returns that the user is not logged in. You go back to your Login class and implement some code to check for the user being logged in.

In this case, you'll have to figure out how to keep this unit test isolated.

For now, the simplest way to make this work is to hard code the username and password you used in your test and if it matches, then you'll return that the user is logged in.

You make that change, run both tests, and they both pass.

Now you look at the code you created and see if there is a way you can refactor it to make it more simple.

So, on you go, creating more tests, writing just enough code to make them pass, and then refactoring the code you wrote until there are no more test cases you can think of for the functionality you are trying to implement.

## These Are Just the Basics

![](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/01/Basic-1-1024x576.png)

So, there you have it. Those are the basics of TDD and unit testing -- [but they are just the basics](https://simpleprogrammer.com/2011/01/14/back-to-basics-unit-testing-automated-blackbox-testing-and-conclusions/).

TDD can get a bit more complex when you truly try and isolate units of code because code is connected together. Very few classes exist in complete isolation. [Instead, they have dependencies, and those dependencies have dependencies and so on](https://simpleprogrammer.com/2010/12/12/back-to-basics-why-unit-testing-is-hard/).

To handle situations like these, veteran TDDers make use of mocks, which can help you to isolate individual classes by mocking the functionality of dependencies with pre-setup values.

Since this is a basic overview of TDD and unit testing, we won't go into details here about mocks [and other TDD techniques](https://simpleprogrammer.com/2011/01/23/back-to-basics-unit-testing-without-mocks/), but just be aware that what I presented in this chapter is a somewhat simplified view.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
