# The OOP(S) Concepts You Need To Know: Part 1

_Captured: 2018-02-10 at 23:24 from [dzone.com](https://dzone.com/articles/the-oops-concepts-you-need-to-know)_

**O**bject **O**riented **P**rogramming (OOPS or OOPS for Object Oriented Programming System) is the most widely used programming paradigm today. While most of the popular programming languages are multi-paradigm, the support to object-oriented programming is fundamental for large projects. Of course, OOP has its share of critics. Nowadays functional programming seems the new trendy approach. Still, criticism is due mostly to misusage of OOP.

This means that if you are learning to become a better programmer it's fundamental to have a good idea of the main concepts of object-oriented programming and how they work. Maybe you are an experienced programmer, but you started right from practice, without any theoretical background. Or you simply forgot to update your knowledge while working. You may be surprised by the things you don't actually know. Apparently, [it can happen to the very best of us](https://www.saturnflyer.com/blog/the-gang-of-four-is-wrong-and-you-dont-understand-delegation).

So we will try to keep the right mix between theory and practice, providing a good number of examples. Our examples will be based on representing a team sport: our domain will be about players, coaches, and other staff members. How do you represent that? We are going to answer that.

## Class

Every player is a different person, but they all have something in common: they can perform the same actions, such as running or passing, and they share certain features, like a number and a position. The same thing could be said for coaches and the rest of the staff. Each one of them will have different combinations, but they all follow the same model.

A class is a model, a blueprint, a template that describe some features. More precisely, a class represents data, usually with variables called _fields_, and behaviors, represented by functions, usually called _methods_. For example, a class `Player `could have a field called `Role` to represent its role, or position, on the actual field of the game, a `Name`, to represent his name. As behavior it could have a method `Pass(Player)`, that would make him pass the ball to some other player.

Let's see an example in pseudo-code.

A class:

### Object

If a class is a model what are the actual players? They are called objects or instances of the class. In the previous example, the argument **teamMate** was an object. To create an object from a class you instantiate, or create, an object.

For example, the object of the class `Player` **John** has the `Name` "Johnny John" and the `Role` "Attacker."

An object called John:

### A Black Box

A black box is something of which you can observe input and output, but you ignore how it works: you cannot look inside. This is can be a good thing because you do not depend on what is inside the box. And you do not care if one day someone changes what is inside the box, if it still behave the same as seen from the outside. Now, this is a principle that is applied in OOP and it is a good thing.

In simple terms: if you just know what something is supposed to do, but not how it does it, then you cannot mess it up.

The idea is to delegate all that is needed to do something of importance to a specific section of the code so that you can change it, independently of any other, without the risk of breaking something else.

For instance, imagine that the coach has created a certain strategy: it does not need to explain to the players how to pass or how to run. It just needs to tell them that them what they have to do. The players themselves must know how to actually do these things. We want to achieve the same organization in our programming.

We can achieve it with **Abstraction** and **Encapsulation**.

Let's start from a common pseudo-code.

A black box:

### Abstraction

Abstraction refers to hiding the details of the implementation from the outside the class.

As an example, the object **OldMan** of the class `Coach` call the method `Run()` of **John, **an object of the class `Player`. It does not know what **John** must do to actually run. It just needs to know that an object of the class `Player` has the method `Run()`.

Encapsulation involves two notions: restricting access to some of the fields and method of a class from the outside world and binding together related data and methods.

For instance, to simulate the ability to run, the class `Player` has a method called` Run()`, but it also has a field called `Legs`. This field represents the condition of the legs of the player: how tired they are and their health, that is to say, whether they are injured. The outside world does not need to know that the `Player` has `Legs` and how they operate.

So the class `Player` hides the field of `Legs` from the outside world. Since to perform `Run()` it just need to operate on `Legs`, by doing so it guarantees that the individual object can be completely autonomous from external interference. This is useful if you later want to add to the simulation the effects of different shoes. You just need to modify the class `Player`, and nothing else.

## Inheritance

To solve a problem you usually end up creating classes which are related somehow. They share some characteristics or even some behaviors. Since you want to avoid repetition, and thus errors, you want to collect all these common features in a common class. Usually, this class is called the parent, super, or base class. Once you have created this class the other classes can declare to be like it, or to inherit from it. This is called inheritance.

The end result is that each of the classes that inherit from the _parent class_ can also have the methods and fields of the parent class, in addition to their own.

As an example, you notice that the `Player`, `Coach` and `Staff` classes have a name and a salary, so you create a parent class called `Person` and you made them inherit from it. Notice that you just keep creating only an object of the class `Player`, `Coach`, etc. you don't need to explicitly create an object of the class `Person`.

An example of Inheritance:

In some languages, you can explicitly forbid from creating a class `Person` by marking it as an _abstract class_. In such cases, a class that you can actually instantiate is called a _concrete class_.

Most object-oriented languages support inheritance, some also support _multiple inheritance_: a class can inherit from multiple classes. This is not always possible because it creates problems and adds complexity. A typical problem is deciding what to do when two different parent classes have a method with the same signature.

In common parlance, inheritance defines a relationship between two classes _is(-a-type-of)-a_. In our example a `Player` _is(-a-type-of)-a _`Person`.

## Interface

Interface, also known as protocol, is an alternative to inheritance for two unrelated classes to communicate with each other. An interface defines methods and (often, but not always) values. Every class that implements the interface must provide a concrete method for each method of the interface.

For example, you want to simulate ejection, or dismissal. Since only players and coaches can be ejected from the field, you cannot make it a method of the parent class that represents people. So you create an interface `Ejectable`with a method `Ejection()` and make `Player` and `Coach` implement it.

An example of an Interface:

There is not a standard way of describing the relationship that an interface establishes, but you can think of it as `behave-as`. In our example a `Player` _behave-as_ `Ejectable`.

## Association, Aggregation, Composition

Inheritance and interface apply to classes, but there are possible ways to link two, or more, different objects. These ways can be thought in order of looseness of the relationship: association, aggregation, and composition.

An association simply describes any kind of working relation. The two object are instances of completely unrelated classes, and none of the objects controls the lifecycle of the other one. They just collaborate to accomplish their own goals.

Imagine that you want to add the effect of the audience on the players; in real life the audience is made of people, but in our simulation, they are not children of the class `Person`. You simply want to make that if the object **HomePeople** of the class `Audience` is cheering then **John **is playing better. So **HomePeople** can affect the behavior of **John, **but neither **HomePeople **nor John can control the lifecycle of the other.

An example of Association:

An aggregation describes a relationship in which one object belongs to another object, but they are still potentially independent. The first object does not control the lifecycle of the second.

In a team sport, all objects of class `Player` belong to an object of `Team`, but they don't die just because they are fired. They could be unemployed for a while or change `Team`.

This kind of relationship is usually described as _has-a (_or_ is-part-of)_, or on the inverse_ belongs-to_. In our example the object **Winners** of `Team` _has-a_ **John **of `Player`, or on the inverse **John** _belongs-to_ **Winners**.

The Winners' Team:

A composition describes a relationship in which one object completely controls another object that has no independent lifecycle.

Imagine that we want to add stadiums, or arenas, to our simulation. We decide that an object `Arena `cannot exist outside of a `Team`, they are owned by a `Team` which decides their destiny. Of course, in real life, an arena doesn't magically disappear as soon as a team decides to dismiss it, but since we want to simulate only team sports, for our purpose it is out of the game as soon as it stops being owned by a team.

Compositions are described just like aggregations, so pay attention so as not to confuse the two.

An example of composition:

This article will be continued soon in Part 2.