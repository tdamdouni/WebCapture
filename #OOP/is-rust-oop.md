# Is Rust OOP?

_Captured: 2017-03-20 at 10:46 from [rust-lang.github.io](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)_

Aphorism: DRY

So how do you share code?

I'm used to doing things to solve problems, what do i do instead? Why do i need to do different things in Rust? Let's look at an example with the Command pattern.

## [Command pattern](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

Look up official def

Want caller to be able to customize what gets done

Method takes command object, calls a run fn

How do we say "we want a thing that has a run function"? Answer: Traits!

where T: Run

This is the definition of the Fn trait! So we wouldn't implement this, we'd just pass closures in

## [Supertraits](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

Trait constraints that use other traits

Copy requires Clone because Copy is a subset of Clone's behavior, since if you have one, you can trivially implement the other.

Traits that need behavior of another trait in a default method or something.

## [Trait objects](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

Runtime decisions about deciding what shared code we use

Give example code

With traits, libraries are extensible. This is why trait objects are different than having an enum and a match statement that has to be exhaustive at compile time and we have to know all the things at compile time and no one can add new things to the set of possible things

T: trait is a compile time decision, monomorphization == static dispatch

when you implement this trait, you get this other shared behavior

dynamic dispatch (C++)

### [Implementation details](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

  * Like how other languages implement oo.

### [How to use it](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

  * Statically checked duck typing

## [Builder pattern](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

When you don't know how many arguments you're going to have

## [Delegation](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

Deref - be mad

Deref is a way to delegate everything, if you don't want that, then write boilerplate. Sending messages to your components.

## [How do you share data?](https://rust-lang.github.io/book/second-edition/ch17-00-oop.html)

Answer: get and set methods, this is awkward and might get better someday.
