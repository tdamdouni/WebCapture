# Exception Testing in Java and AssertJ

_Captured: 2017-05-12 at 21:51 from [dzone.com](https://dzone.com/articles/exceptions-testing-in-java-and-assertj?oid=twitter&utm_content=buffer01c89&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

As long as I have been writing tests and seeing others write them, Java exceptions have been a problem for many programmers, including those more experienced ones. When an exception is being thrown, it stops the execution of the code going up to the top of the execution stack, or until it's handled. In unit test environments, this usually means that the execution of a given test is stopped, and whatever code runs after the exception is not going to be executed. This means that the most obvious way to verify the exception is to do it in a catch block:

The code does exactly what it's supposed to do -- verifies that some `NullPointerException` is being thrown from the method. It's valid, but I still don't like it. It introduces some logic to the validation, something that should be avoided in tests. In a simple example like the one above, it's usually not a problem, but with larger number and more complex tests, it can obfuscate the purpose.

One way to handle that is to add parameters to the `@Test` annotation. This is pretty straightforward:

Thankfully, later versions of JUnit allow you to use the [rules mechanism](http://junit.org/junit4/javadoc/4.12/org/junit/Rule.html). They provide wrappers over the tests, allowing you to modify the execution of the particular test. You can implement your own rules, but JUnit provides a couple of them pre-implemented. One of them is `[ExpectedException](http://junit.org/junit4/javadoc/4.12/org/junit/rules/ExpectedException.html)`, which, as you would have probably guessed, expects an exception. With that, the next step in our example looks like this:

Now, all the logic of the test is explicitly stated in the test, and with `ExpectedException`, you can check the class, the message, and the underlying cause. The only thing that bothers me is having to state the requirements for the exception before the tested method. This disturbs the flow I had mentioned earlier.

For a long time, one could do a better job by importing external libraries, like `[catch-exception](https://github.com/Codearte/catch-exception)`. To the rescue comes [AssertJ](http://joel-costigliola.github.io/assertj/), one of my favorite Java libraries (I even pushed some commits a couple of years ago!). The solution was possible thanks to the lambda expressions that came in Java 8, and it looks like this:
    
    
        Throwable thrown = catchThrowable(() -> { testObject.throwAnException() });

Pure perfection! I feel sorry for myself for using JUnit extensions for so long, while the perfect solution was just under my nose! As you can see, there is a proper execution with the result, and a set of verifications after that. There is no inversion of execution, so you can do other validations -- for example, verifying that a mock was (or wasn't) called.

Before AssertJ exception handling, it was hard to convince someone not to use the plain `try-catch` solution. But now I don't know why anyone would need to be convinced. The AssertJ approach is far superior, and I'm looking forward to starting using that in all my projects.

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).

### Like This Article? Read More From DZone
