# Getters and Setters Considered Harmful

_Captured: 2018-03-27 at 20:34 from [dzone.com](https://dzone.com/articles/getters-and-setters-considered-harmful?edition=370191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-27)_

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251321&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Gain insights on a hybrid approach. Download white paper now!

Java programmers habitually pepper their classes with getters and setters, and this practice is so ingrained that probably few ever question why they do so, or whether they should. Lately, I have come think that it is better not to, and I have begun avoiding it in the Java code that I write. In this blog post, I will explain the reasons why. But first, a quick history lesson.

## JavaBeans

Getters and setters originated in the [JavaBeans specification](http://download.oracle.com/otn-pub/jcp/7224-javabeans-1.01-fr-spec-oth-JSpec/beans.101.pdf?AuthParam=1521468655_f6fb953a104ee5ea145aaf4390a91638%22>), which came out originally in late 1996 and was updated to version 1.01 in August 1997. The original idea was to enable the creation of objects that could be used like building blocks to compose applications out of. The idea went, a "user" might use some kind of builder tool to connect together and customize a set of JavaBeans components to act together as an application. For example, a button in an AWT application would be a bean (AWT was the precursor to the Java UI library Swing). Alternatively, some JavaBeans would be more like regular applications, which may then be composed together into compound documents, so a spreadsheet bean might be embedded inside a web page.

An object is a JavaBean when it adheres to the following conventions:

  1. It must have a zero-argument constructor which cannot fail.
  2. It has properties which are accessed and mutated via 'getter' and 'setter' methods.
  3. For any property of a bean called `Foo` then the accessor method must be called `getFoo`. In the case of boolean properties, the getter may alternatively be called `isFoo`.
  4. The setter method for Foo must be called `setFoo`.
  5. A bean is not obliged to present both a getter and a setter for every property: a property with getter and no setter is read-only; a property with setter and no getter is write-only.

The specification describes many different use cases, but it is clear from the above description that JavaBeans were conceived of as objects with behavior, not mere bags of data. The idea has faded into obscurity, but while JavaBeans have been largely forgotten, the idiom of getter and setter methods in Java has persisted.

## The Metaphor Is Wrong

The concept of "get" and "set" seems natural enough, but is it correct? The JavaBeans convention uses "get" to mean query, which is an operation without side effects, but in the real world getting is an action that does alter state: if I get a book off the shelf, the book is no longer on the shelf. You may object that this is mere pedantry, but I think this misconception encourages us to think wrongly about the way we write our objects to interact with each other. For example, if we had a Thermometer class then most Java devs would write code to read the temperature like this:

Really though, is it the job of a thermometer to "get" the temperature? No! The job of a thermometer is to _measure_ the temperature. Why do I labor over this point? It is because "get" is an imperative statement: it is an instruction to the thermometer to do something. But we do not want to instruct the thermometer to do anything here; it is already doing its job (measuring the temperature) and we just want to know what its current reading is. The act of reading is done by us. Therefore the code is more natural when written this way:

I think this better places the responsibilities where they really belong. But do always please give thought to whether the accessor is needed at all, because...

### Objects Are Not Data Structures

The habit of writing classes with getters and setters has a subtle effect on the way we code. It naturalizes the idea that we should reach into objects to get the data we need, process it, then update the objects with the results, rather than get the objects to perform the processing themselves. In other words, it encourages us to view objects as bags of data. We pull the data out through the getters and update them via the setters. The code that operates on the data, meanwhile, resides elsewhere.

If our coding habits incline us towards treating objects as mere data structures, ORM frameworks positively enforce it. Worse still, if you're using Spring framework - and if you're a Java dev there's a good chance you are - by default it creates all your beans as singletons. (Confusingly, Spring beans have nothing to do with JavaBeans). So now you have a system composed of singleton objects, operating on data structures with no behavior. If keeping your code and data separate sounds like a programming style you know, you're not wrong: we call it procedural programming.

Consider whether this is a good thing. Java is, after all, supposed to be an object-oriented programming language. One of the great strengths of OO is that we can write classes of objects whose names and interactions reflect the problem domain. It enables us to write code that reads in terms of the problem being solved, without obscuring the big picture behind basic programming constructs and primitive data types. It helps us see the wood through the trees. We ought not to give this up.

## What to Do Instead

Wherever possible, stop writing get and set! Sometimes it will be appropriate, but _definitely_ stop using your IDE's facility to generate getters and setters for you. This is just a convenient way to quickly do the wrong thing. If you need to expose an attribute on an object, simply name it after the attribute, but do also examine whether it's really necessary to expose it. Ask why you want to do this. Can the task be delegated to the object itself? For example, say I have a class representing a currency amount, and I wish to sum a bunch of transactions:

Instead of the `getValue` accessor why not give the Amount class an `add()` method and have it do the summing for me?

This brings benefits -- perhaps you raised an eyebrow at the idea of using a double to represent a currency amount. You'd be right, BigDecimal would be better. The second example makes this easier to fix because the internal representation is better encapsulated. We only need to change it in one place.

Maybe you want to get at an object's data in order to test whether it is equal to something. In this case, consider implementing an `equals()` method on the object and have it test equality for you. If you're using Mockito to create spies, this avoids the need to use argument captors: instead you can create an object of equal value to serve as an example and pass it directly to the verify statement for comparison.

There will be times when you must create accessors. For example, in order to persist data in a database, you may need to access primitive representations of your data. Do you really have to follow the get/set naming convention though? If your answer is "that's the way it's done in Java," I encourage you to go back and read the JavaBeans specification. Are you really writing a JavaBean to use it in the way the specification describes? Are you using a framework or library that expects your objects to follow the convention?

There will be fewer times when you must create mutators. Functional Programming is sweeping the industry like a craze right now, and the principle of immutable data is a good one. It should be applied to OO programs as well. If it is not necessary to change state, you should consider it necessary _not_ to change state, so don't add a mutator method. When you write code that results in new state, wherever possible return new instances to represent the new state. For instance, the arithmetic methods on a BigDecimal instance do not alter its own value: they return new BigDecimal instances representing their results. We have enough memory and processing power nowadays to make programming this way feasible. And Spring framework does not require setter methods for dependency injection, it can inject via constructor arguments too. This approach is indeed the way [the Spring documentation](https://docs.spring.io/spring/docs/4.1.x/spring-framework-reference/html/beans.html#beans-constructor-injection) recommends.

Certain technologies do require classes to follow the JavaBeans convention. If you're still writing JSP pages for your view layer, EL and JSTL expect response model objects to have getter methods. Libraries for serializing/deserializing objects to and from XML may require it. ORM frameworks may require it. When you are forced to write data structures for these reasons, I recommend you keep them hidden behind architectural boundaries. Don't let these data structures masquerading as objects leak into your domain.

## Conclusion

Speaking to programmers who work in other languages, I often hear them criticise Java. They say things like, "it's too wordy," or "there's too much boilerplate." Java certainly has its flaws, but when I enquire deeper into these criticisms I usually find they are aimed at certain practices rather than anything intrinsic to the language. Practices are not set in stone, they evolve over time and bad practices can be fixed. I think the indiscriminate use of get and set in Java is a bad practice and we will write better code if we give it up.

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Maintaining high quality data is essential for operational efficiency, meaningful analytics and good long-term customer relationships. But, when dealing with multiple sources of data, data quality becomes complex, so you need to know when you should build a custom data quality tools effort over canned solutions. [Download our whitepaper](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) for more insights into a hybrid approach.
