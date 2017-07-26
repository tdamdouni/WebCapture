# To Mock or Not to Mock: Is That Even a Question?

_Captured: 2017-06-04 at 11:08 from [www.solutionsiq.com](http://www.solutionsiq.com/to-mock-or-not-to-mock-is-that-even-a-question/?utm_content=buffere53fe&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](http://www.solutionsiq.com/wp-content/uploads/2017/05/Mock-or-Not-e1493166036316.png)

Mocking is a very popular approach for handling dependencies while unit testing, but it comes at a cost. It is important to recognize these costs, so we can choose (carefully) when the benefits outweigh that cost and when they don't.

## A Quick Overview of Mocking

Mocking is a way to replace a dependency in a unit under test with a stand-in for that dependency. The stand-in allows the unit under test to be tested without invoking the real dependency.

![](http://www.solutionsiq.com/wp-content/uploads/2017/05/Mock-as-stand-in.png)

**A note on terminology:**

It would be more accurate to use the term "test double" instead of "mock", but somehow "mock" has become the generic term among programmers. Bob Martin has suggested the following relationship among the different kinds of test doubles:

![](http://www.solutionsiq.com/wp-content/uploads/2017/05/Test-Double-Hierarchy.png)

That is, a mock is a spy is a stub is a dummy. A fake is a different kind of thing (it has business behavior). For a more detailed explanation of these different types of test doubles, see <https://8thlight.com/blog/uncle-bob/2014/05/14/TheLittleMocker.html>.

## **The Costs of Mocking**

In my experience, there are 3 reasons to mock sparingly:

  1. Using mocks leads to violations of the DRY principle.
  2. Using mocks makes refactoring harder.
  3. Using mocks can reduce the simplicity of the design.

All of these reasons are interrelated (and, you could argue, are just different ways of saying the same thing), but let's take them one at a time.

### **Mocks Can Lead to Violations of the DRY Principle**

I first read about the DRY principle in "[The Pragmatic Programmer"](https://pragprog.com/book/tpp/the-pragmatic-programmer) by Andrew Hunt and Dave Thomas. They state it as: "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system" (p. 27).

So, this isn't just about code duplication - it is about _knowledge_ duplication. When you use a mock you are in violation of this principle because the knowledge of how the components in the system interact is defined in two places: once in the production code and once in the tests. Any change to those interactions has to be made in two places.

### **Mocks Make Refactoring Harder**

In the preface of [Martin Fowler's "Refactoring" book](https://martinfowler.com/books/refactoring.html), he defines refactoring as "the process of changing a software system in such a way that it does not alter the external behavior of the code yet improves its internal structure". One of the XP practices is "[refactor mercilessly"](http://www.extremeprogramming.org/rules/refactor.html). A fair assumption when practicing merciless refactoring is that unit tests should pass before and after any given refactoring that we do. This is the essence of the red-green-refactor cycle: we only attempt a refactoring when we are in a "green" state, and we expect to still be in a "green" state after the refactoring.

But mocks break this assumption, because with mocks our tests do NOT merely test the "external behavior of the code" but also test the internal workings of the code under test -- specifically what other modules are being used and how.

Here's an example that just happened to me recently. I started out with class A invoking methods on two other classes, B and C.

![](http://www.solutionsiq.com/wp-content/uploads/2017/05/A-invoking-methods-on-B-and-C.png)

Then I realized the design could be improved if I structured things this way:

![](http://www.solutionsiq.com/wp-content/uploads/2017/05/A-Invoking-C-Invoking-B.png)

The functionality of A had not changed, as far as its external behavior goes. But in the tests for A, I had mocked out B, so with this refactoring many of the A tests were now broken. Mocking couples the production code to the test code in a way that hinders refactoring, because with mocks your test code knows about the internal workings of the code under test.

Mocking also inhibits refactoring because some refactoring tools do not cleanly refactor code that uses mocks (renaming a method, for example, may not catch method names that are represented as strings, as in some mocking frameworks).

### **Mocks Reduce Design Simplicity**

In Cory Haines' book "[Understanding the Four Rules of Simple Design"](https://leanpub.com/4rulesofsimpledesign), he defines a simple design as "one that is easy to change". As illustrated in the above example, the use of mocks makes the system harder to change. When the system is harder to change, we become reluctant to refactor, and the design slowly deteriorates over time.

Arlo Belshee asserts that the need for mocking is a sign of a design with too many dependencies. At a Seattle Software Craftsmanship meetup in May of 2014 he put it this way: Mocking "basically allows me to treat highly dependent code as if it were not dependent, without having to change the design. Perfect for legacy, perfect for learning, a real problem when you are trying to get design feedback. As soon as I remove the [mocking] tool then I am required to change the design and reduce the dependency and reduce the coupling. That's what all the design literature is about." ([Watch the full talk here](https://www.youtube.com/watch?v=njg33YM0E0M).) This is a good description of how mocking reduces the simplicity of the design, namely, by increasing coupling and increasing the cost of change.

## When to Mock

So, given these drawbacks to mocks, how do we decide when to use them? I use the following guidelines in my own code:

  * Only use a mock (or test double) "when testing things that cross the dependency inversion boundaries of the system" ([per Bob Martin](https://cleancoders.com/episode/clean-code-episode-23-p2/show)).
  * If I truly need a test double, I go to the highest level in the class hierarchy diagram above that will get the job done. In other words, don't use a mock if a spy will do. Don't use a spy if a stub will do, etc. This is because the lower you go in the class hierarchy of test doubles, the more knowledge duplication you are creating. (A test that uses a dummy only knows that a collaborator is used in the code under test. A test that uses a mock knows which method on the collaborator is used, how many times it is invoked, and the types of the parameters that are passed).
  * If I truly need a test double, I prefer to write my own, rather than using a mocking framework. This keeps the code simpler and works fine in most cases. I will resort to using a mocking framework when mocking fairly large interfaces or third party libraries.

Also, as Arlo mentioned above, mocking may be needed initially when getting legacy code under test, until some of the dependencies can be removed.

By using mocks sparingly, we can keep our code DRY, enable easier refactoring, and improve the simplicity of our designs.
