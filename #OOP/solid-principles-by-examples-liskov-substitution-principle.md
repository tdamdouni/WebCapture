# SOLID Principles by Examples: Liskov Substitution Principle

_Captured: 2017-09-22 at 13:53 from [dzone.com](https://dzone.com/articles/solid-principles-by-examples-liskov-substitution-p)_

In this post, we're going to explore the third of the SOLID principles: the Liskov **Substitution Principle** (LSP).

The most practical definition of this principle was written by Robert C. Martin in his book, "Agile Software Development, Principles, Patterns, and Practices:" _"Subtypes must be substitutable for their base types."_

The concept was introduced by Barbara Liskov in 1987. The formal definition is: _"Let q(x) be a property provable about objects x of type T. Then q(y) should be provable for objects y of type S where S is a subtype of T."_

For our **daily activities**, we must remember that a subclass should override the parent class's methods in a way that doesn't break functionality from a consumer's point of view.

## Example

## The Evergreen Example

To better understand LSP, let's examine this classic example. It's a classic because it's easy to understand and very meaningful. We start with this question: Is a square a special rectangle in OOP?

We try to answer this question with this simple class hierarchy: a **Rectangle** as the base class and a **Square** class that inherits from it. In the Square class, we override the behavior of the setters to enforce that the Height and Width properties have the same value.

Now we have to remember that a subclass must override the base class in a way that it doesn't break functionality from a client's POV. We write these two tests to check.
    
    
                Assert.AreEqual(21, sut.Area); //This test will fail. Area equals 49.

So it's clear that in OOP, a square isn't a particular case of a rectangle. How can we do to better organize these classes? The typical approach consists of creating an abstract class (or an interface). For example:

Now our code states that both the Rectangle class and the Square class are Shapes, which is true. Our code is also safer and we don't have any situation where a client will receive unexpected values.

## TL;DR

In this post, we explored the Liskov Substitution Principle (LSP) and we learned that it's not true that real-life objects always maps to the same OOP structure/class ecosystem. We also tried to improve the wrong example with the simple technique of adding an abstraction layer (the Shape class).
