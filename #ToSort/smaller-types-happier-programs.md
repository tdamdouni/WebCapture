# Smaller Types, Happier Programs

_Captured: 2017-01-08 at 22:10 from [queertypes.com](https://queertypes.com/posts/57-small-types.html)_

This post will be all about a simple technique for making programs a little easier to maintain. It's all about the size of types.

Most code examples will be given using Haskell. When an example uses another programming language, I'll call that out before showing the example.

The advice is focused on languages that have a compile-time type-check step, but can be informally adopted to make maintenance of dynamically-typed programs (Javascript, Python, Ruby, etc.) a little easier.

## The Size of Types

When I talk about the size of types, I'm talking about how many values a given type can represent. A few examples:

  * boolean: true or false, a type of size 2
  * 32-bit integer: 2^32 possible values, a type of size 2^32
  * a string, encoded as a byte array: 2^8 * n, n being the length of the string 
    * a type of infinite size, for our calculations

These examples are all primitive types. Fortunately, most programming languages offer at least some form of abstraction over these primitive types. Leveraging those abstractions will allow us to craft types that are smaller than the primitive types, and can therefore more accurately describe our domain of interest.

In particular, I want to talk about algebraic data types. They're called as such because in a sense I'll make clear soon, they allow us to add to and multiply a type space to meet our needs as precisely as possible.

For example, a sum type `Color`:
    
    
    data Color = Red | Green | Blue

This type has 3 values, or variants: `Red`, `Green`, `Blue`. It's a sum type, because each variant adds 1 one more value to the size of the type. With that, `Color` is a type of size 3. This is a reliable fact as long as implicit conversion isn't something to watch for in your programming language of choice. More on that later.

In Scala, this might look like:
    
    
    sealed trait Color
    final case object Red extends Color
    final case object Green extends Color
    final case object Blue extends Color

Most mainstream languages have basic support for sum types, via enumerations. However, sum types become particularly interesting when used with product types. A product type might look something like:
    
    
    data AreaColor = AreaColor { inverted :: Bool, color :: Color }
    -- basic shape: AreaColor Bool Color

An `AreaColor` has 2 * 3 possible values. Let's enumerate them.
    
    
    > let ct0 = AreaColor True Red
    > let ct1 = AreaColor True Green
    > let ct2 = AreaColor True Blue
    > let cf0 = AreaColor False Red
    > let cf1 = AreaColor False Green
    > let cf2 = AreaColor False Blue

Most mainstream languages have excellent support for product types. You may have heard them referred to by the names, "struct", "record", or the like. The components of the product type multiply together to give the new type size.

Here's where most mainstream programming languages falter: being able to combine sum and product types conveniently.

Here's an example of the two used together:

`PaletteCommand` is a toy example of the sorts of concepts that can be expressed when you have algebraic data types.

It's very powerful being able to conveniently combine sum and product types. So much so, that without this ability, it becomes very easy for the complexity of a program to multiply. This is what I meant when I said 2 years ago that "In languages lacking sum types, the complexity of a program can only multiply". [ref](https://twitter.com/queertypes/status/588020984856367105)

Now we have just enough of the basics of calculating the size of types so that we can talk about dealing with how to resolve design problems.

## Stringly-Typed and Work Arounds

One of the most common design problems that one might encounter when working with existing code is that everything will be expressed and encoded as a string, e.g., a so-called stringly-typed code base. This can happen in any programming language. After all, strings are nearly always provided as a primitive type. It might come up in the context of retrieving data from a database to affect control flows, as messages from a queuing system, as commands from a network-connected client, or even as commands from a command line interface.

Below, I'll show some of the trouble with relying on strings to handle program control flow.

Let's write a function, `colorToInt`, that given a string, returns a numeric representation of that color:

And an example of where this goes wrong:

This will raise an exception. Our `colorToInt` function doesn't know how to handle `"Red"`. A first-pass at fixing this might be something like:

Now, our former example works alright. But what about:

These all return `3`, which amounts to an unknown color value. A third and common pass might throw an exception:

This will catch all typos. But - how does it fare in the face of program updates?

Let's assume we have a `morbidify` function defined deep in our system. It's worked for a long time, and no one's thought about it for months because there's been other priorities in mind.

New requirements come in: Red in no longer supported and now we need to add Cyan.

We remember to update `colorToInt3`:

But somewhere in the system, the following call occurs:

Suddenly, this call will start to fail. Given the nature of the code, one that performs a side-effect on behalf of the system, it is very unlikely that tests will have been written for this. If we're somewhat fortunate, someone thought to add some logging to `morbidify`, so at least the problem will be detected and can be explained. If we're not so lucky…

Well, the good news is we can do much better than this. Let's talk about it next.

## A Solution: Smol Types

Many of the problems we ran into the last section were because the size of string types is far too large. Let's see how using sum types can make the situation better. First, we start with a few definitions:

Let's play around with this a little. First, our failing examples from before:

This gives us a compile-time error, noting that we expect a `Color` but got a `String`

This gives us a compile-time error, noting that the value `Reed` is unknown.

Let's add support for `Cyan`:

And a small test program:

This gives us a compile-time **warning** that `Cyan` wasn't handled in `colorToInt4`. This is a cool thing known as **exhaustivity analysis**, a super helpful thing a few languages containing full support for sum types can do.

Let's remove support for `Red` and `Cyan`:

This will give us two compile-time errors:

  * we mention `Cyan` in `main` when we've never defined it
  * we mention `Red` in `colorToInt4` when we've not defined it

This is the basic premise behind using small types as a tool for making programs easier to maintain. If the size of our types is as small as possible, while still fully expressing our domain, errors cannot be represented.

Now let's talk about caveats and things to watch for.

## Implicits Ruin Everything

Implicit conversion. Sometimes, we try as hard as we can, and the programming languages we use try to be as helpful as they can, and things Just Go Wrong.

This is particularly notable in Java and Scala, where `toString` is defined over all types.

The problem arises when interfacing with legacy code, where most of the types are still the infinitely-sized `String` instead of our constrained `Color`. We might pass in a `Color` to such a legacy function, and expect the compiler to flag us somehow, but it silently gets converted to a String. Where we expected to be able to reason about a type that is at most size 3, we're back to the land of infinites.

Another problematic conversion that is fairly common, is one of most primitive types to `Bool`. This will sometimes come up in control paths, where an if-statement is used to determine what's to be done next, rather than a switch. The problem here is that we're defined fine-grained control with our type, say `Color`, of size 3, but we've shrunken down to something that can only express 2 paths, `Bool`.

Another common implicit conversion to watch for is that of enumeration to integer. This happens in C, and when using regular enumerations (rather than `enum class`) in C++.

For languages (frequently object-oriented languages) that have a notion of value and reference types, and of nulls, beware of the possibility of `null` inhabiting your type. It is entirely possible in `Scala` and `Java` for `null` to be a member of our `Color` type, and still cause us trouble.

There's a few other forms of implicit conversion to worry about. It all depends on your domain and the programming language you're working with. They're beyond the scope of this post.

In sum, watch out for:

  * implicit string conversions, particularly in Java and Scala
  * implicit conversion to Bool at control paths
  * implicit conversion from enumeration to integer, particularly in C and C++
  * nulls, because they break everything

It's worthwhile to keep in mind the danger of implicit conversions when relying on the size of types to design your programs.

## In Practice

To wrap up, I'll leave you with a few practical tips.

Make the types at the core of your program as small as possible.

The best time to shrink a type is as early as possible. By this I mean, if you're interfacing with the outside world, say, reading an environment variable or parsing some user input, that is the time to determine whether the input is valid and make a value of your small type or return some form of error. `Either` and `Maybe` types are lovely here.

The best time to grow your types again is when outputing at the boundaries of your programs. Serialize them as needed, and send them off to the database as a String field or as a response to a client command as a part of a JSON blob.

Sometimes, there'll be data that really needs to be a `String` or an `Int`, and can't be shrunk. This will be safe to do as long as no control paths depend on the shapes of the values contained in the `String` or `Int`. If you notice the flow of your program start to depend on what's in those strings or integers, it might be time to consider shrinking to a more representative type.

That's the basic idea.

## Topics Not Covered

We've covered a lot in this post. However, there's still a whole lot more to explore when it comes to using the size of types to design programs. Here's a selection of things I didn't cover that might be of interest:

  * size of polymorphic types:
  * size of functions and their compositions
  * size of subtypes (Scala, Java, etc.):
  * size of constrained types:
  * typed holes
  * limits of exhaustivity analysis
  * reasoning about the size of effectful functions:
  * using the size of types for automated linting and static analysis

Anyway, enjoy your small types. ❤
