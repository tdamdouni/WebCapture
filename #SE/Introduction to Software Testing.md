# Introduction to Software Testing

_Captured: 2015-10-14 at 23:12 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/introduction-to-software-testing)_

## Introduction to Software Testing

![Software Testing Bug Catching](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/bug_catching_small.jpg)

> _Software Testing Bug Catching_

While learning about Agile Development and project management, we talked mostly about "Acceptance Testing", which is the final stage where the code is sent to the Product Owner for testing. While that may be the _last_ step of the testing process, it's far from the _only_ place where testing comes in. In fact, though software testing is something that few beginners ever really consider, it is a critically important part of the production process and it's done by every single reputable development team.

You may remember that in the Waterfall process there is an entire phase devoted to testing and perhaps saw hints about how it's used in the Agile process as well. Hopefully this has made you curious about what the heck software testing really is.

In this lesson, we'll give you an overview of what testing is and why it's so helpful.

### Why We Need It

Let's say you're building a simple website and you've got a couple of pages linked together with a simple navigation bar at the top. You make some changes to the code and want to know if the website still works. So you open up your local version of the webpage and click through each of the buttons on the navigation bar to make sure they each still lead to the right location. Not too difficult, is it? It doesn't take too long, and it doesn't seem like such a bad way of doing things.

But now imagine that you've got a dozen pages with a login system and content that's meant to look different depending on which type of user you are logged in as. You could come up with a checklist of all the buttons you'd have to manually click on and all the times you'd have to log in as a different user... but think about how many steps it would take before you were satisfied that your changes didn't accidentally blow up some obscure but necessary function of your website? Situations like that should yell "automate me!" in your head, and that's exactly what automated software testing does.

Here's another example -- you're a junior developer who just stepped onto the job after an older developer left. The older dev had been working with a giant code base that was largely untested and largely unknown to the rest of the team (bad news). Something just broke in that black box... how do you even start figuring out how to fix the problem? How do you know that you didn't break something else when you deployed your fix? The best way to do this is to add tests to the existing code, which forces you to begin to understand how that code works.

### Different Approaches to Testing

Everyone does testing a little differently. Some teams still rely heavily on a Quality Assurance (QA) department with people manually executing checklists like we described in the example above. Some people use an approach called Test Driven Development (TDD) in which they write the (failing) test first and only then do they actually write the code necessary to make it pass, and thus very deliberately build the application out with nearly full test coverage (see the next lesson to learn more!). Others prefer to keep their test suites fairly light and will only write tests for the major interactions on their pages and any bugs that they have to fix along the way (to make sure they don't come back).

Regardless of how exactly it's done, testing is highly important and you'll be required to do it whatever your job is. Beginning developers are often tasked to write tests and fix bugs to become familiar with a given code base.

### So What Is It Exactly?

Software tests are just a set of instructions that you give to the computer to run. You specify:

  1. How to prepare for the test (maybe you need to create some items in your database first or visit a specific web page, for instance)
  2. Some action to take (like clicking a button or calling a method with a specific input)
  3. Your expectation for what should happen afterward (e.g. landing on a specific page, creating a user in the database, or throwing an error).  


If the thing happens, woohoo! You've passed the test. If it doesn't, you get a failing test.

### Testing Tools

Every major software development framework or language has a set of tools that help you to test your code. With Ruby and Ruby on Rails, we most commonly use RSpec. RSpec is actually written in Ruby (Ruby testing Ruby!) and it lets you execute a broad and flexible script of tests to make sure your application is still working the way that it should. RSpec's syntax even reads sort of like English, though it still takes some getting used to.

Here's some example RSpec code. It's not exactly readable but you can kind of get the gist of what's going on:

![Rspec Examples](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/rspec_examples.png)

> _Rspec Examples_

Testing isn't just for the server-side either. On the front end, a testing framework called Jasmine does a similar sort of thing for JavaScript. That should make sense to you -- the reasons to properly test your code apply whether it's run on a server or in the browser.

### Zooming Out

In [the following video (only watch 49:55 to 55:56)](https://www.youtube.com/watch?v=Fr-B4xHZRzY), David Patterson of Berkeley explains some of the higher level concepts surrounding testing:

### Test Coverage

Backing up to the highest level, how much testing do you need anyway?

We use the term **Test Coverage** to describe how much of the code is actually tested. But what does 100% "test coverage" really mean? Do you test every method? Every possible path the user could take through your application? Every possible way that any logical branch (e.g. an `if` statement) of your code can be run? You will always need to compromise between an acceptable level of coverage and the complexity (and time) costs of implementing a highly granular test suite.

Some ways of thinking about test coverage (borrowing heavily from [Wikipedia](http://en.wikipedia.org/wiki/Code_coverage)) dive in deeper than you need to remember but should give you a healthy respect for how much people have thought about testing over the years:

  * **Function Coverage** \-- Has each function or subroutine been called?
  * **Statement Coverage** \-- Has each statement been executed?
  * **Branch Coverage** \-- Has each branch of each control structure been executed?
  * **Decision Coverage** \-- Has every possible decision in the program been tested? Similar but not identical to branch coverage.
  * **Condition Coverage** \-- Has every boolean sub-expression been both `true` and `false`?
  * **State Coverage** \-- Has each state in a finite-state machine been reached?
  * **Parameter Value Coverage** \-- In a method taking parameters, have all the common values for those parameters been tried?

In a web environment, there are also a variety of simulation tests that can be run -- you not only test the methods of your application on a specific level but you can "fire hose test" the whole application by throwing thousands of requests at it per second and see what breaks first.

That's a lot of testing!

### Testing Levels

There are also different levels of testing. Starting as specific as possible and getting more general, they are listed below:

  1. **Unit Testing** \-- isolating a very specific unit of code (by faking any inputs/outputs/methods inside it) and testing its characteristics. Is the function working as expected?
  2. **Integration Testing** \-- Verify the interfaces between units. This can occur on many levels, from small modules to high level architectural components.
  3. **System Testing** \-- Verify that the fully integrated system meets its requirements and without corrupting its environment.
  4. **Acceptance Testing** \-- The system is delivered to the user (or Product Owner in Agile) for acceptance or rejection.

### What to Test

If you were to start writing tests for your projects tomorrow, what should you be testing? Though there are extremes on either end of the spectrum, good rules of thumb for what to test (for beginners) includes:

  1. Anything you would otherwise manually test (e.g. by checking the page to verify it loaded properly)
  2. All critical paths the users will take (like signing in and using the app's core functions)
  3. Anything that might reasonably break later (e.g. if it relies on code that may get changed later or produce unexpected outputs)
  4. All critical methods that are run during the critical user paths (often unit tests for your models)
  5. Any bugs you discovered along the way (write a test for the bug that fails, then fix the bug, then your test will pass)

If you haven't gotten into code before, just consider this a reference for later use and just try to understand the kinds of things you might test in a real software project.

### Wrapping Up

We covered a lot of new concepts here and you certainly don't need to memorize all the nitty-gritty details. The important takeaways are an appreciation for how useful automated testing is for you as a developer and an understanding of the kinds of places where you will encounter it. You should be aware that there are testing tools in every language and that testing can occur at all levels of code from tiny little pieces up to the bigger picture.

In the next lesson, you'll see how testing is used extensively as part of certain Agile Development practices that you're already familiar with.

###  Next Lesson: Test- and Behavior-Driven Development 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/test-and-behavior-driven-development) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/implementing-agile-yourself)
