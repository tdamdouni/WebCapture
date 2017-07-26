# Why do some functional programmers criticize design patterns in OOP languages as a sign of language deficiency, while Monad is also a design pattern?

_Captured: 2015-09-14 at 00:17 from [www.quora.com](http://www.quora.com/Why-do-some-functional-programmers-criticize-design-patterns-in-OOP-languages-as-a-sign-of-language-deficiency-while-Monad-is-also-a-design-pattern/answer/Tikhon-Jelvis?srid=3zh0&share=1)_

**Monad is an abstraction**. It's only a design pattern in the most general sense, like other abstractions, fundamentally different from what people _specifically_ mean by "design pattern" in OOP (influenced by the Gang of Four book).

**The general idea of Monad is expressed ****_in_****_the language_****; the general idea behind design patterns in OO ****_isn't_****.**

That's the fundamental difference: things like "the observer pattern" are nothing more than patterns. They're like extended code idioms--general patterns of code people write over and over. They exist in programmers' minds and they exist in documentation--they're a useful vocabulary to have--but they _don't_ exist in the language. There is no single object or class or interface in Java you can point to and say "this is the observer pattern" or "this is the strategy pattern" or "this is the singleton pattern".

You can for monads. **Monad** **is defined directly in Haskell**:

    
    class Monad m where
     return :: a -> m a
     (>>=) :: m a -> (a -> m b) ->  m b
    

A monad is any type which fulfills this interface. There are a few other restrictions that exist purely in documentation (the monad laws), but otherwise _this is it_.

Really, Monad is more comparable to something like `Comparable` in Java (pun, of course, entirely intended). It's a useful abstraction _that's actually captured by the language_. Sure there are additional laws (both for `Monad` and `Comparable`) that aren't reflected in the language, but the core structure is.

This is why some people talk about design patterns as deficiencies in the language: they're common structure in code that _can't_ be expressed directly in the language, so are instead passed around as a shared vocabulary and set of conventions. Monads, on the other hand, are a concrete structure expressible directly in Haskell, so thinking of them as "just design patterns" is misleading.
