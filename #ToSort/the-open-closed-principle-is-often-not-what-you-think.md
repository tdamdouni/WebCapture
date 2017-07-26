# The Open-Closed Principle Is Often Not What You Think

_Captured: 2017-03-24 at 18:49 from [dzone.com](https://dzone.com/articles/the-open-closed-principle-is-often-not-what-you-think?edition=286910&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-24)_

jOOQ is a library that loves making everything internal `final` and package private. We have tons of classes like these:

The class implements the semantics of SQL string concatenation. Clearly, you shouldn't need to tamper with it (or even know about it), because it is "protected" behind the corresponding public API in the [DSL class](https://www.jooq.org/javadoc/latest/org/jooq/impl/DSL.html):

Now, in the past decades, there have been a lot of software design movements that were contrary to the concept of encapsulation in some ways. The driving powers of that were:

  * Testing (and in particular: mocking)
  * A misunderstanding of what [SOLID](https://en.wikipedia.org/wiki/SOLID_\(object-oriented_design\)) (and in particular the [open-closed principle](https://en.wikipedia.org/wiki/Open/closed_principle), as well as the [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)) really mean

A fun to read example of "slightly" (read: completely) exaggerated advocacy of extreme application of object orientation is [Yegor Bugayenko's blog](http://www.yegor256.com).

Through exaggeration, he makes some really interesting points that make you think. Of course, you have to be able to accept the hyperboles as non-facts. Not everyone can do that, so don't get angry reading.

## Let's Look at the Open-Closed Principle

The [open-closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) claims, according to Wikipedia:

> In object-oriented programming, the open/closed principle states "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"; that is, such an entity can allow its behaviour to be extended without modifying its source code.

This is a very desirable aspect of _some_ software entities. For instance, it is _always_ true for an [SPI (Service Provider Interface)](https://en.wikipedia.org/wiki/Service_provider_interface), by design, of course. Let's read the Wikipedia definition of an SPI:

> Service Provider Interface (SPI) is an API intended to be implemented or extended by a third party. It can be used to enable framework extension and replaceable components

Perfect. For instance, a jOOQ `[Converter`](https://www.jooq.org/javadoc/latest/org/jooq/Converter.html) is a SPI. [We've just published a recent post about how to use the `Converter` API in a strategy pattern style with lambdas](https://blog.jooq.org/2017/03/17/a-nice-api-design-gem-strategy-pattern-with-lambdas/) - the strategy pattern works really well with SPIs.

In fact, the [strategy pattern](https://en.wikipedia.org/wiki/Strategy_pattern) isn't even strictly an object oriented feature, you can get it for free in functional programming without giving it a fancy name. It's just any [ordinary higher order function.](https://en.wikipedia.org/wiki/Higher-order_function)

Another fine example of what could be considered an SPI is an `[Iterable`](https://docs.oracle.com/javase/8/docs/api/java/lang/Iterable.html). While `Iterable` subtypes like `[List`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) are more often used as APIs (user is the consumer) rather than SPIs (user is the implementor), the `Iterable` API itself is more of a way of providing the functionality required to run code inside of a foreach loop. For instance, jOOQ's `[ResultQuery`](https://www.jooq.org/javadoc/latest/org/jooq/ResultQuery.html) implements `[Iterable`, which allows it to be used in a foreach loop](https://blog.jooq.org/2016/09/27/a-hidden-jooq-gem-foreach-loop-over-resultquery/):

So, clearly, it can be said that:

  * `Iterable` follows the open-closed principle as it models an entity that is open for extension (I can produce my own iterable semantics), but closed for modification (I won't ever modify the Java compiler and/or the foreach loop semantics
  * The Liskov substitution principle is also followed trivially, as the foreach loop doesn't care at all about how I implement my `Iterable`, as long as it behaves like one (providing an `Iterator`)

That was easy.

## But When Does It NOT Apply?

In a lot of situations. For instance, jOOQ is in many ways not designed for object oriented extension. You simply should not:

  * **Mock the `concat()` function**.  
You might be tempted to do so, as you might think that you need to unit test everything, including third party libraries, and then you have to mock out the string concatenation feature inside of your database. But it doesn't work. The `DSL.concat()` method is static, and the implementation hidden. No way you could replace it with ordinary means (there are some dirty tricks). But hold on for a second. Why are you even doing this? [Aren't integration tests the better way here](https://blog.jooq.org/2014/06/26/stop-unit-testing-database-code/)? Do you really have time (and want to spend it) on replacing entire complex implementations with your mocks? I don't think so. That hardly every works
  * **Modify the concatenation behavior for some use-case**.  
While you may think that sometimes, you'd just like to tweak an implementation a little bit to get a quick win, that is certainly not the intent of the authors of the open-closed principle or the Liskov substitution principle. We as API designers _don't want you_ to extend all of our functionality. As simple as that. Why? Because we want you to get in touch with us to help us improve our software for everyone, rather than you tweaking something for a quick win.

Let this sink in - especially the latter.

The premise that _everything_ should be object oriented and _everything_ should be extensible is wrong. Object orientation (and all the philosophies connected to it) are a tool. They're a very powerful tool, for instance, when we as API/SPI designers _want to_ allow users to extend our software. (mostly through SPIs). And we spend a lot of time thinking about really good, generic, useful, powerful SPIs that solve 99% of all extensibility problems in a way that we can control and keep backwards compatible. For some examples, check out these blog posts:

  * [Easy Mocking of Your Database](https://blog.jooq.org/2013/02/20/easy-mocking-of-your-database/) (that's a bit ironic in the context of this article…)
  * And in jOOQ, there's always the option of just [using plain SQL to extend jOOQ](https://www.jooq.org/doc/latest/manual/sql-building/plain-sql/), but that's jOOQ-specific.

And sometimes, yes, we did not foresee a justified request for extensibility. Nothing is perfect. You have a feature request, and you cannot implement it right away. Then you start exploring. You look into ways how you can inject some behavior into jOOQ. And as we Java developers like object orientation, we're looking into writing subclasses to override existing behavior. That's what we were taught. That's what we're doing all the time. That's what the combination of the [open-closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) and the [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle) suggest.

Let me shock you for a moment.

Yes. There are entire ecosystems out there, that don't have the luxury of bikeshedding the fact that if a class cannot be (easily) extended through subtype polymorphism and overriding of methods, it must be ill-designed. An entire ecosystem that never worries about something being `final`, and thus "closed for extension" (through subtype polymorphism).

## Alternative Definitions

Given the historic context, both principles are very interesting things. But their object-oriented context is something we should free our minds of. Here's a better definition:

  * **Open-closed principle:**  
Systems should strive for openness for extension, but not at any price. _Some_ parts of a system / module / perhaps class should be open for extension. Those parts should be very well designed and kept very backwards compatible. And the vendor of those parts should listen to its consumers to better identify the required extension points. Consumers, on the other hand, shouldn't blindly assume that _everything_ can be extended. If they're extending (through unexpected subtype polymorphism) random parts, then they're hacking in the same way as if they would be actually modifying the system / parts. There's no more benefit to extending.
  * **Liskov substitution principle:**  
Subtype polymorphism is just a tool, and in 2017, we have long started understanding that it's a very wrong tool for many things. The [composition over inheritance concept](https://en.wikipedia.org/wiki/Composition_over_inheritance) has shown that we've regretted the subtype polymorphism hype from the 90s. So, forget about your mocks through subtype overriding. Start looking for alternative interpretations of this principle. [I like Jessica Kerr's finding](http://blog.jessitron.com/2013/06/what-fp-taught-me-about-oo-liskov.html):  


> Therefore, the Liskov Substition Principle says, "Don't surprise people."

That's a much better credo to follow, than the one that is strictly related to an aspect of object orientation and in particular to subtype polymorphism.

## Conclusion

Yes. Package private, final classes mean you cannot extend them. The open-closed principle is "violated". Because that part of the system was not designed for you to know about (it's _encapsulated_).

Sometimes, you think that if just you could override such an entity, you might get a quick win and inject your desired behavior into a third party library / entity / class / module / system. My claim here is that: Mostly, you'll deeply regret your desire for a quick win later on. You shouldn't argue about open-closed or Liskov substitution. These principles _simply don't apply here_. They do not at all, in particular, apply to badly designed legacy software. Once software is "badly designed," no principles will help you.

Instead, do get in touch with the vendor if you run into a bump. There's always an interesting idea for a great new feature hidden in such a limitation. And for the time being, accept that your overriding of what was not meant to be overridden is just _the same thing_ as actually modifying that entity. You're patching the library. Let's do that and move on.
