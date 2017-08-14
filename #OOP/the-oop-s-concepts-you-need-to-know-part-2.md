# The OOP(S) Concepts You Need To Know: Part 2

_Captured: 2017-08-03 at 21:56 from [dzone.com](https://dzone.com/articles/the-oops-concepts-you-need-to-know-part-2?edition=313391&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-03)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

This article is a continuation from Part 1, found [here](https://dzone.com/articles/the-oops-concepts-you-need-to-know).

## Polymorphism

Polymorphism, in the context of OOP, means that you can invoke the same operation on objects of different classes and they will all perform it in their own way. This is different, and should not be confused with a programming concept that is independent of OOP: function (method) _overloading_. Overloading applies to functions and allows you to define functions with the same name that operate on different and unrelated types. For example, you can make two methods `add()`: one that can add integer numbers and another one that add real numbers.

Polymorphism in a class usually means that a method can operates on different objects of related classes. It can behave differently on different objects, but it does not have to. At the most basic level an object of a _child class_, one that inherit from a parent, can be used when you can use an object of the parent class. For example, you can make a function `Interview(Person)` that simulate an interview of a `Player`, `Coach` or `Staff`. No matter the actual object. Obviously for this to work `Interview` can only act upon fields that are present in the `Person` class.

In practice, this means that an object of a child class is also an object of the parent class. In some cases a child class can redefine a method of parent class of the same name, this is called _overriding_. In this situation whenever this method is called the actual method executed is the one of the child class. This is especially useful when you need all the child classes to have a certain behavior, but there is no way to define a generic one. For example you want all object of the class `Person` to retire, but a `Player` must retire after a certain age, while a `Coach` or `Staff` does not.

## Delegation and Open Recursion

"In object-oriented programming, delegation refers to evaluating a member of one object (the receiver) in the context of another, original object (the sender)." -[Wikipedia](https://en.wikipedia.org/wiki/Delegation_\(object-oriented_programming\)).

The concept is used extensively in a particular style of object-oriented programming called Prototype-based programming. One widespread language that uses it is JavaScript. The basic idea is to not have classes, but only objects. So you do not instantiate objects from a class, but you clone them from a generic one and then modify its prototype to suit your needs.

Despite being at the core of the most known programming language it is little known. Indeed even JavaScript it is mostly used in the usual style of object-oriented programming. While it may seem arcane knowledge it is important to know it because it is widely used with a special variable or keyword called _this_ or _self_.

Most object-oriented programming language support it and it allows to refer to the specific object (not the class) that will be instantiated, from inside a method **defined in the class or in any child class**. The fact that when the code will run `this` will refer to a specific object is what allows _open recursion_. Which means that a base class can define a method that uses `this` to refer to one of its methods, that the actual object will use to refer to a child method with the same signature.

This sounds complicated, but it is not. Imagine the following pseudo-code.

An example of this:

On the last line is where open recursion happens, because the method `DoesHaveToRetire `is a method defined in the parent class that uses `this.IsOld()` (on line 16). But the `IsOld` method that is actually called at runtime is the one defined in the child class `Player`.

This is also delegation, because on line 16 the `this` is evaluated in the context of the object **John,** evaluated as object of the `Player` class, and not the original this of **John**, as object of the `Person` class. Because remember that **John** is both an object of the class `Player` and its parent class `Person`.

## Symptoms of Bad Design

Up until now, we have talked about the basics. We think that some people need more to apply this knowledge fruitfully. First, we need to look at the symptoms of bad design, so you can detect them for your code.

### Rigidity

The software is hard to change, even for little things. Every modification requires cascading changes that take weeks to apply. The developers themselves have no idea what will happen and what will have to be changed when they need to do X or Y. This lead to reluctance and fear to change in both the developers and the management. And that slowly makes the code very hard to maintain.

### Fragility

The software breaks in unexpected ways for every change. This is a related problem to rigidity, but it's different because there is not a sequence of modification that continues to become longer by the hour. Everything seems to work, but when you think you are ready to ship the code a test, or even worse a customer, tells you that something else does not work anymore. The new thing works, but another one is broken. Every fix is actually two new problems. This lead to existential dread in the developer that feels like it has lost control the software.

### Unportability

Every module works, but only in the careful situation it has been placed in. You cannot reuse the code in another project, because there are too many little things that you will have to change. The program seems to work by dark magic. There is no design, only hacks. Every time you modify something you know what to do, but it is always a terrible thing that makes you afraid that it will come back to bite you. And it will. Apart from shame, that you should really feel, it makes the code hard to reuse. Instead, you will recreate a slightly different code, that does almost the same thing.

## Principles of Good Design

To know what a problem looks like, it is not enough. We also need to know practical design principles, to be able to avoid creating a bad design in the first place. These well-known principles are the fruits of many years of experience and are known by their acronym: SOLID.

### Single Responsibility

"There should never be more than one reason for a class to change."

Usually, the reason to change is modified in "responsibility," hence the name of the principle, but this is the original formulation. In this context, a responsibility, or reason to change, depends on the particular project and its requirements. It obviously does not mean that a class should only have one method. It means that, when you describe what it does, you say that it only does this one thing. If you violate this principle different responsibilities become coupled and you might have to change the same class, or multiple classes, for many disparate reasons.

Let's go back to our example. You need to keep the score of the game. You might be tempted to use the `Player`class, after all, players do the scoring. But if you do that, every time you need to know the score you would also need to interact with the Player. And what you would do, if you need to invalidate a point? Keep one job for each class.

### Open/Closed

"A module should be open for extension, but closed for modification."

In this context, a module means a class, or a group of classes, that takes care of one objective of the software. This principle means that you must be able to add support for new items without having to change the code of the module itself. For example, you must be able to add a new kind of player (eg. a keeper) without changing the `Player` class.

This allows a developer to support new things, that perform the same functions of the ones that you already have, without having to make a "special case" for that.

### Liskov Substitution

"Subclasses must be usable as their base classes."

Note that this is not the original formulation, because that one it is too mathematical. This is such an important principle that it has been incorporated in the design of object oriented language themselves. But the language itself guarantees only part of the principle, the formal part. Technically you can always use an object of the subclass as if it were an object of the base class, but what it matters to us it is also the practical usage.

This means that you should not modify substantially the behavior of the subclass, even when you override a method. For example, if you are making a race car game, you cannot make a subclass for [a car that moves underwater](https://en.wikipedia.org/wiki/Rinspeed_sQuba). If you do that the `Move()` method will behave differently from the base class. And a few months later there will be a weird bug of random cars taking the gulf stream as a highway.

### Interface Segregation

"Many client specific interfaces are better than one general purpose interface."

In this context, "client specific" means specific for each type of client and not for each and every client class. This principle says that you should not implement one generic interface for clients that really do very different things. That is because this couples each type of client to each other. If you modify one type of client you have to modify the general interface and maybe you also have to modify the other clients. You can recognize a violation of this principle if you have several methods on the interface that are specific to one client. This could be both in the sense that they do usual things in a different, specific, way and also that they do things that are needed only by one client.

In practical use this is probably the more difficult to respect. Especially because at the beginning it is easy to miss what are actually different requirements. For example, imagine that you have to deal with connections: a cable connection, a mobile connection, etc. They are all the same, isn't it?

Well, in theory, they behave the same way, but in practice, they may differ. Mobile connections are usually costlier and they have strict limitation for the size of the monthly transferred data. So a megabyte for a mobile connection it is more precious than one for a cable one. As a consequence, you might find yourself checking the data less often or using a `SendBasicData() `instead of` SendData()`… Unless you already have experience in the specific field you may end up to keep forcing yourself to follow this principle.

### Dependency Inversion

"Depend upon Abstractions. Do not depend upon concretions."

At this point, it should be clear that by "abstraction" it is meant _interfaces_ and _abstract classes_. And it should also be clear why it is true. An abstraction, by definition, deals with the general case. By using abstraction you make easier to add new features or to support new items, like different databases or different programs.

Of course, you should not always use interfaces for everything lest two classes touch each other. But if there is a need to use an abstraction, you also cannot let the abstraction leak. You cannot demand that the client of the interface it is aware that it must use interface in a certain way. If you find yourself checking if an interface actually represent a certain class and then you do Y instead of X, you have a problem.

We have seen the basic OOP(s) concepts that you need to know to be a good programmer. We have seen the fundamental design principles that must guide how you develop software. If you are just starting out these might seem a bit abstract, but like all specialized knowledge, they are needed to communicate well with your colleagues. Both with your voice and with your code. They are fundamental to organize your knowledge and practice of Object Oriented Programming so that you can create code that is easily understandable by other people.

Now that you have a solid foundation you can move forward. And overall you can finally participate in the wonderful polemics of the programming world. I suggest you start with [Composition or inheritance?](http://stackoverflow.com/questions/49002/prefer-composition-over-inheritance#).

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
