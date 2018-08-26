# Types: When I Use Them, and When I Don't

_Captured: 2018-03-27 at 16:41 from [dzone.com](https://dzone.com/articles/types-when-i-use-when-i-dont?edition=367224&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-26)_

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251321&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Gain insights on a hybrid approach. Download white paper now!

**Note**: Below is my personal perspective.

If I write a one-page program, I don't mind having no types: 0 types, **-**1 types, I'm happy with it.

But if I write a bigger app, one handled by multiple programmers and that is expected to be maintained, I consider types to be a must! I'm still happy with it!

## When I Like Types

Today, most modern languages have `type inference`, so the typed code looks as concise as non-typed code. In Scala, Haskell, OCaml, Kotlin, and ELM, concise, typed code pretty much is both pretty and awesome!

## When I Don't Like Types

We still need to compile code, and that takes time, but I'm willing to pay this price. Both maintenance time and code-understanding time are also time spent. Time is time: A second is a second. I would rather pay seconds of compile time for hours of unusual bugs and code readability time.

> Type Inference + Types => Concise, readable code!

## The Performance Penalty for Type Inference

You pay the price at compile time. As mentioned earlier, **I prefer to pay someone to compile than to pay someone to read and not understand the code.**

> Programs that are hard to understand also compile slower.

So if you write readable code, it will compile faster, in its own way.

## Parametric Polymorphism

> Parametric Polymorphism: Same subtype [A] for the container which we defined.

Let's consider a hypothetical `Array[A]`. So you can have a single implementation that does something with the array and uses it for a different type.

## Subtype Polymorphism

You inherit in order to have multiple implementations, but you end up with one big, giant object (the class hierarchy). For me, that is like a global ball of mud-code.

> Subtype Polymorphism: a big ball of mud-code. There are multiple types when you traverse the array.

## Simple Type System

Like in Java, **we still get so much benefit from tooling**: what our functions are doing, how the program is constructed, etc.

> Simple type systems give us great tooling!
> 
> Simple type systems give us great documentation checked by the compiler!

You need to explain to the compiler what you mean with those non-type inference languages.

## Rich Type System

Here, we're talking about languages like Scala, OCaml, and Haskell.

> Rich Type Systems allow us to have clean, simple code!

This sounds unnatural, but take, for example, `generics` used to express code that can be used polymorphically over types -- code reuse. I return Int, Double -- I don't care as long a I return `A`.

## Rich Type Systems Catch Bugs

> Lie: If it compiles, it works!

I don't treat this as a truth. But many bugs just vanish:

  1. Null Pointer Exception, I don't remember having one since using Scala.
  2. Undefined is not a function. Forget about it with ELM.

## Summary

My summary is very simple -- for code that would require maintenance by new developers and is not a single-page project, I use typed languages. For simple scripts and short code snippets, no types.

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Maintaining high quality data is essential for operational efficiency, meaningful analytics and good long-term customer relationships. But, when dealing with multiple sources of data, data quality becomes complex, so you need to know when you should build a custom data quality tools effort over canned solutions. [Download our whitepaper](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) for more insights into a hybrid approach.

Opinions expressed by DZone contributors are their own.
