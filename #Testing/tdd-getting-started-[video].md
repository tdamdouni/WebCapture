# TDD - Getting Started [Video]

_Captured: 2017-08-25 at 14:16 from [dzone.com](https://dzone.com/articles/tdd-getting-started-video?edition=319415&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-08-25)_

With test-first TDD, the starting point is to figure out how to code a unit test.

The test has to be easy to read, say exactly what the production class needs to do, and use its public interface.

The key to writing a unit test is to use the **three 'A's**:

  * **Arrange** - new up our object under test, and wire it to any collaborators it needs
  * **Act** - ca[iill the method we are testing to get an actual result
  * **Assert** - check the actual result is correct

In Test Driven Development, you do these in the reverse order - figure out the assert, make the actual call, then arrange the objects.

So how does this work in practice?

## TDD 'add Two Numbers' Example

Let's code a toy object to add two numbers together.

We'll use Java, JUnit 4 and [Mockito](http://site.mockito.org/).

Our object will be a Calculator class. And purely to demonstrate the TDD technique, it will have one, very weird responsibility: it will read its two numbers from a NumberSource, add them together, and return the actual result.

The reason for the NumberSource is to show how we can write the test for the Calculator class _before_ we write the real number sources.

### Coding the NumberSource Interface

First up (at least the way I do it), we'll need an interface for our number source:

The contract here is that whenever you call fetchNumber(), a new number will be returned as a long.

### We've Already Started Designing …

This interface might seem trivial, but in fact we have just made a **_design decision_**.

This interface relates to the _design_ of our software - how the pieces pull apart and fit together.

It is a _decision_ because it is not the only way of doing this. But we have chosen this one.

The value of Test Driven Development is that it _forces_ you to think of these things up front. Before we write a ton of spaghetti code which we later delete :D

### Coding the Test Class - 'assert'

We start with the test class shell:

We follow our 3 As backwards, so next we add the 'assert' line:

This bit doesn't compile. But it will do soon.

This is a typical workflow in TDD. A compile failure is simply classed as a test failure.

Overall, the assert is saying "is the actual answer the sum of two test numbers?' If we've done a good job, this is easy to read out of the code.

We will supply these two test numbers to the Calculator as a later step.

### Using Hamcrest Matchers to Make It More Readable

To code the assert, we're using the [hamcrest matchers](http://hamcrest.org/JavaHamcrest/) library to get the method 'is'. We statically import this from Matchers.is().

We use the variable name 'actual' to clue us in that this is going to be the result of a method call on our calculator object.

To move us along a TDD step and fix the compile fail around 'actual', we begin to flesh out our public interface for our Calculator class.

  * We've got "actual" defined as a long, so that's one compile failure sorted.
  * We've also defined the public interface to our calculator object.
  * We've called the object "calculator," and given it a public method.
  * We created a new instance of the Calculator class, to make the calculator object.

### Coding the Production Class

We can now start the calculator class coding:

This should all compile now.

We run the test, to prove that the JUnit 'success' bar goes red, to indicate the test has failed.

### We Prove That the Test Fails? Why?

We follow a **RED-GREEN-REFACTOR** cycle in TDD. As the tests drive along our development, we need to know that we have a test that fails because the production code isn't ready yet. This gives us some confidence when it is ready and the test passes.

If the test passes as soon as you write it, chances are it's a side effect of some other code somewhere. Side effects are bad. They make it hard to spot where in the code an effect happens. That makes it hard to change, and prone to bugs. The side effect probably won't work for any values other than the ones in the test.

So we make sure our new tests _fail_ first, to avoid such mistakes.

### Growing the Test - 'arrange'

The next step of our backwards 3 As is "arrange." This is where we do "object wiring."

First in the test class:

We've now used Mockito to add a [stub object](https://www.martinfowler.com/bliki/TestDouble.html) for our NumberSource interface. We've initialized the Mockito system with MockitoAnnotations.initMocks(this). We've then told Mockito that when we call fetchNumber(), the first time it should return FIRST_NUMBER, and the second time we call it should return SECOND_NUMBER.

This simulates our production code that will implement this interface. We don't have to worry about that yet - this is the big use of Mockito.

The 'arrange' step is then completed by passing the 'source' object into the Calculator constructor.

### We've Just Done Some More Software Design

This is another fundamental design decision as to how our two objects will collaborate together. And we've made it as a decision, now, before we write the production code.

With the test in place, let's fix those compile failures and write the production wiring code in the Calculator class:

Another quick run of the test proves it still fails.

We're now all set. We have locked into place our public interface for our method. We have locked into place how our Calculator object is going to collaborate with its NumberSource supplier.

All that's missing is the production code:

At last. We run the test, and it goes green and passes.

**We have completed a TDD Red-Green cycle.**

### Now for the Most Important TDD Step: Refactor

At this point, the true value of TDD happens.

With a green test, we look at the code we have written:

  * Is it clearly named?
  * Is there any duplicated code - such as copy and paste lines?
  * Is the flow of the code simple to understand?

Our goal here is to **eliminate duplicated code** and **make it easy for others to change later**.

As this is our first ever test and method, there isn't any refactoring to do. So we're done.

### Looking Back

We have:

  * Used TDD to complete a Red-Green-Refactor cycle.
  * Built the test backwards using the 3 As: Arrange, Act, Assert.
  * Got 100% test coverage of our code (which is a vanity metric in larger codebases, but hey, it sounds nice).
  * Created a nice design for our problem.

### Check It In

Time to let the rest of the team have our shiny new code:

And we can have a crafty cup of tea before coding the next story. Which would probably be "Read two numbers from a csv file."

### Some Reflections

  * **The only new thing is "assert."** TDD is a workflow. In terms of new techniques, it only adds the one: you get to assert actual results against expected results. Other than that, it's business as usual here at the code face.
  * **TDD doesn't design - _you do._** There is often a belief that TDD provides 'magic'. It really doesn't. At each step, you have to design your software, as we have seen. Where TDD is helpful is that it pushes you into a highly decoupled design, and it forces you to design in small 'just-in-time' pieces.
  * **The magic is in the refactoring.** The Red-Green-Refactor approach means your best design work often happens whilst refactoring
  * **Watch your granularity.** It is quite easy to code a test that accidentally locks you in to a particular implementation. It is better if you can make them so only the public output is significant. We have done that here, with the one class. But as you get clusters of collaborating classes, this takes care.

There is definitely a craft behind writing good unit tests. And **Arrange - Act - Assert** is the guide.

#### Recommended Books:

  * [Growing Object Oriented Software Guided by Tests](https://www.amazon.co.uk/Growing-Object-Oriented-Software-Guided-Signature/dp/0321503627) is quite brilliant. It features a book-long case study of building an XMPP chat system, test first. The best bit is it is very practical. The first version of code is a complete mess - by design. As the authors point out, if this was all that was needed, it is tested and perfectly adequate. As the system grows, they refactor it into something with very clean layers.
  * [Test Driven Development](https://www.amazon.co.uk/d/cka/Test-Driven-Development-Addison-Wesley-Signature-Kent-Beck/0321146530/): The original! This is a highly readable, quite chatty book. I like Kent's approach - write tests for the things you care about: functionality, "Have I got the right library version?" and so on. Favors tests that leave you free to change the implementation, which I like. Has the brilliant advice to _refactor to eliminate duplication_. Not just "tidy it up a bit." Very good.
