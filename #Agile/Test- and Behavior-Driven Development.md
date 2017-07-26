# Test- and Behavior-Driven Development

_Captured: 2015-10-14 at 23:13 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/test-and-behavior-driven-development)_

## TDD and BDD in the Agile Process

![Flat testing](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/flat_testing_small.jpg)

> _Flat testing_

To get acquainted with Test-Driven Development (TDD) and Behavior-Driven Development (BDD), let's first go back to our discussion of Agile methods, specifically eXtreme Programming (XP). XP, we said, provides some prescriptions for productive programming. In particular, it takes the "good" parts of the development process and cranks them up to the extreme.

One of those "good" things is writing tests -- and if writing tests is a good thing, why not write tests for every piece of code? Why not actually start by writing the test and then write the code to make the test pass?

That's the basic premise of Test-Driven Development, a philosophy that has grown beyond its roots in XP and is now practiced by a variety of proponents throughout the industry. It's something you might encounter early on in your career or you might not see it in practice at all but you can certainly learn from the philosophies behind it.

### How TDD Works

As the name implies, TDD works by writing the test for a specific piece of code before actually writing that code. Put more strictly, you cannot write a piece of code without there being a failing test waiting to pass because of it. The process looks like this:

  1. **Add a Test** for the first piece of work in your new story. The test will fail (you don't have the code in place to make it pass!) and is called "Red" because that's typically the color of failing tests. The test should cover only a very focused and narrow use case.
  2. **Run all the Tests** to make sure everything is good in your test suite except for the new test.
  3. **Write the Code to Pass the Test** in the simplest possible way, even if it's a really dumb way to make the test pass. According to strict TDD, if you want the code to do anything else, you've got to write a new test for that functionality.
  4. **Run all the Tests** to make sure your new test is now "Green", or passing, and you haven't broken anything else.
  5. **Refactor your Code** to make the ineligant code better organized and more efficient and to remove duplication. You can then run your tests again, confident that if you've broken something it will show up.
  6. **Repeat**

This approach is also termed **"Red-Green-Refactor"** because of the progression from test failure to test passing and finally to refactoring.

While strict TDD advocates writing tests before any code, it also allows that sometimes you really need to code something up to see how it works before you implement it in the main project. A **"Spike"** is exactly that -- you code something up to try it out with no intention of ever using that code in production.

### Why TDD is Useful

Because you're writing the test first, you really need to understand what your code is supposed to do ahead of time. You will architect good code simply because you are so focused on what it's doing. It essentially forces you to solve the problem ahead of time (in your head, on a whiteboard...) in order to write the proper test.

Testing first also prevents **[Scope Creep](http://en.wikipedia.org/wiki/Scope_creep)**. If you can't write any code except what's necessary to make the test pass and you can only justify a test based on the requirements for the project, then you'll be able to resist the temptation to go off and build a bunch of unnecessary functionality. Remember that awesome engineer's acronym [YAGNI](http://en.wikipedia.org/wiki/You_aren't_gonna_need_it)? How about [KISS](http://en.wikipedia.org/wiki/KISS_principle)?

In a more concrete sense, you also emerge from the development process with great test coverage. That means you'll have the confidence to refactor your code later, hand it off to other developers, or simply deploy it to production. And, despite the extra work of writing the tests, you can actually save time in the overall process because you avoid getting pulled into chaotic debugging situations later.

Watch [Test-Driven Development: A Love Story (below)](https://www.youtube.com/watch?v=nBtO1UOK9Hs) by Nell Shamrell for an entertaining real-life story of being introduced to using TDD approaches (and the benefits of doing so). She gets a bit more technical than you need to understand so don't worry about the details -- absorb the narrative instead.

### What is BDD and How Does it Work?

BDD is a derivative of TDD and it stands for Behaviour-Driven Development. In BDD, the business stakeholders (usually non-technical people) work with the developers to write high level tests called **Scenarios** based on their needs (or the "desired behavior" of the code). The format of these tests closely follows the standard Agile Development story template -- their desired behavior is set up like the acceptance criteria of those stories.

For instance, an acceptance criteria for a user story might say that "the user should not be able to enter a name greater than 20 characters long". Using the hybrid english/code phrasing of BDD testing, this might be set up like:

  1. **GIVEN** the user is on the signup page AND has selected the first_name field AND has entered 12345678901234567890123
  2. **WHEN** the user clicks submit
  3. **THEN** the user should_not be created in the database

Because it's so similar to English, non-technical stakeholders can write their acceptance criteria and the program automatically (with some initial setup of course) converts that into executable test code so the developers know when they've finished the story.

Essentially, BDD gives you an idea of what you should actually be writing tests for (your Agile Stories!) where TDD does not (a common criticism of the specification). So BDD is really just a more specific implementation of TDD that also happens to work well within an Agile framework and which involves multiple levels of the organization.

To pull an example from [Wikipedia](http://www.vikingcodeschool.com/software-engineering-basics/http://localhost:3000/web-engineering/behavior-and-test-driven-development), BDD might look like:

> **Story: Returns go to stock**
> 
> In order to keep track of stock
> 
> As a store owner
> 
> I want to add items back to stock when they're returned
> 
> **Scenario 1:** Refunded items should be returned to stock
> 
> Given a customer previously bought a black sweater from me
> 
> And I currently have three black sweaters left in stock
> 
> When he returns the sweater for a refund
> 
> Then I should have four black sweaters in stock
> 
> **Scenario 2:** Replaced items should be returned to stock
> 
> Given that a customer buys a blue garment
> 
> And I have two blue garments in stock
> 
> And three black garments in stock.
> 
> When he returns the garment for a replacement in black,
> 
> Then I should have three blue garments in stock
> 
> And two black garments in stock

### Wrapping Up

We've just covered a fair bit of stuff but now you should have a good sense for where that testing theory fits into the practice of Agile Development. As usual, you don't need to worry about the little details of it but should work on capturing the theory -- why a TDD approach can be useful and how BDD works well within the Agile Development method.

Your own approach to testing may involve TDD or maybe you've got good reasons for sticking to a test-last approach. You might test every single thing like TDD prescribes or you might only test the higher level "things that matter". In the real world, it's still more common to do the latter than the former (especially in startups where no one seems to want to devote the time to testing), but TDD's popularity is increasing as the tools for it improve.

That's enough about testing for now and this concludes your introduction to Agile. You're now well prepared to put it into practice on your own and to understand how we'll use it to teach you the nuts and bolts of web development later on.

Of course, project management is really just the framework around the actual development work. That's why, in the next section, you'll learn how "pseudocoding" and systems thinking can be used to help you effectively solve all kinds of engineering problems.

###  Next Lesson: Stories for the E-Commerce App 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/stories-for-the-e-commerce-app) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/introduction-to-software-testing)
