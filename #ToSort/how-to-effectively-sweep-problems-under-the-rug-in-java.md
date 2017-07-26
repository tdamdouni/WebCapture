# How to Effectively Sweep Problems Under the Rug in Java

_Captured: 2017-04-06 at 00:47 from [dzone.com](https://dzone.com/articles/how-to-effectively-sweep-problems-under-the-rug-in-Java?oid=twitter&utm_content=buffer246d2&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Bitbucket](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Because software bugs can make us appear bad as developers and lead to others thinking less of us, it is best to avoid writing bugs, to identify and fix bugs quickly, or to cover up our bugs. There are numerous blog posts and articles that discuss avoiding bugs and identifying and fixing bugs, so, in this blog post, I look at some of the most effective tactics for sweeping problems in Java code bases [under the rug](http://idioms.thefreedictionary.com/sweep+under+the+rug).

## **Swallow Checked Exceptions**

Exceptions are one of the things that give us away when we've accidentally introduced bugs into the code. It's also a hassle to declare a `throws` clause on a method or `catch` a checked `Exception`. A solution to both problems is to simply catch the exception (even if it's a `RuntimeException`) at the point it might be thrown and do nothing. That keeps the API concise and there is little one could do about the checked exception anyway. By not logging it or doing anything about it, no one even needs to know it ever happened.

## **Comment Out or Remove Unhappy Unit Tests**

Failed unit tests can be distracting and make it difficult to determine when new functionality has broken the tests. They can also reveal when we've broken something with code changes. Commenting out these failing unit tests will make the unit test report cleaner and make it easier to see if anyone else's new functionality breaks the unit tests.

## **Use `@Ignore` on JUnit-based Unit Tests**

It may seem distasteful to comment out failing unit tests, so another and possibly more pleasing alternative is to annotate failing JUnit-based unit test methods with the [@Ignore](http://junit.sourceforge.net/javadoc/org/junit/Ignore.html) annotation.

## **Remove Individual Tests Altogether**

If commenting out a broken test or annotating a broken test with `@Ignore` are unsatisfactory because someone might still detect we've broken a unit test, we can simply remove the offending unit test altogether.

## **Comment Out the Offending Assertion**

We don't necessarily need to comment out or remove entire tests. It can be as simple as commenting out or removing the assert statements in a unit test method. The method can execute and run successfully every time because no assertions means no way to fail. This is especially effective when the unit test methods are very long and convoluted so that lack of assertions is not easily spotted.

## **Distract With the Noise of Useless and Redundant Tests**

Commenting out unit tests, annotating JUnit-based unit tests with `@Ignore`, and even removing unit tests might be too obvious of ploys for sweeping issues under the rug in Java. To make these less obvious, another effective tactic is to write numerous unnecessary and redundant test methods in the same unit test class so that it appears that comprehensive testing is being done, but in reality, only a small subset of functionality (the subset we know is working) is being tested.

## **Write Unit Tests That 'Prove' Your Code is Correct Even When It Is Not**

We can take advantage of the fact that unit tests can only test what the author of the unit test thinks is the expected behavior of the software under test to write unit tests that demonstrate our code to be correct. If our code for adding two integers together accidentally returns a sum of 5 when 2 and 2 are provided, we can simply set the expected result in the unit test to also be 5. A pretty unit test report is presented and no has to be the wiser.

## **Avoid Logging Details**

Logs can expose one's software problems and an effective approach to dealing with this risk is to not log at all, only log routine operations and results, and leave details (especially context) out of logged messages. Excessive logging of mundane details can also obscure any more meaningful messages that might reveal our code's weaknesses.

## **Avoid Descriptive `toString()` Implementations**

A descriptive `toString()` method can reveal far too much about the state of any given instance and reveal our mistakes. Not overriding `Object.toString()` can make it more difficult to identify issues and associate issues with any given code or developer. The extra time required to track down issues gives you more time to move onto the next project before it is discovered that it's your code that's at fault. If you write a Java class that extends a class with a descriptive `toString()` you can override that method in your extended class to do nothing (effectively removing the potentially incriminating `toString()` output). If you want it to appear as if it was never implemented at all in the inheritance hierarchy, be sure to have your extended class's `toString()` method return [System.identityHashCode(this)](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html#identityHashCode-java.lang.Object-).

## **Don't Let `NullPointerException`s Betray You**

The `NullPointerException` is probably the most common exception a Java developer deals with. These are especially dangerous because they often reveal code's weak spots. One tactic is to simply wrap every line of code with a `try`-`catch` and simply swallow the exception (including the NPE).

Another less obvious tactic is to avoid NPEs by never returning or passing a `null`. Sometimes there are obvious defaults that make sense to use instead of `null` (such as empty `String`s or collections), but sometimes we have to be more creative to avoid `null`. This is where it can be useful to use a "default" non-`null` value in place of `null`.

There are two schools of thought on how to approach this arbitrary non-`null` default. One approach is to use the most commonly seen value in the set of data as the default because, if it's common anyway, it may not be noticed when a few more of that value show up and you are more likely to have code that appears to process that common value without incident. On the other hand, if you have a value that is almost never used, that can make a good default because there may be less code (especially well-tested code) affected by it than by the commonly expected value.

## **Conclusion**

As I reviewed these tactics to sweep issues in Java code under the rug, I noticed some recurring themes. Exceptions, logging, and unit tests are particularly troublesome in terms of exposing our software's weaknesses and therefore it's not surprising that most of the ways of effectively "covering our tracks" relate to the handling of exceptions, logging, and unit tests.

[Bitbucket is the Git solution](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

### Like This Article? Read More From DZone
