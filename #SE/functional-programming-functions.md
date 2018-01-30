# Functional Programming: Functions

_Captured: 2018-01-29 at 21:22 from [dzone.com](https://dzone.com/articles/functional-programming-functions?edition=358101&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-29)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

In the previous posts, we took a look at how functions are the core pieces in functional programming languages. We talked about [pure functions, referential transparency, side effects](https://dzone.com/articles/side-effects-1) and [recursion](https://dzone.com/articles/functional-programming-recursion) in the previous posts. In this post, we are going to explore some properties of functions and how we can use them in a functional programming language.

## Function Definition

A function is a black box that, given an input, **always** gives you back the same output. As we stated before, a function does not have any side effects; if it has any, it could be a procedure, but not a function. Function is a term that comes from mathematics, and there is no concept of side effects in there. A function accepts a set of input values; we call that the domain of a function. The output of a function is called the _codomain_ and the set of outputs is called the _image_ of the function. We can decompose them like this:

Where A is the domain and B is the codomain. For example, for the function `f(x) = 2x` we can decompose it as it follows:

![domain-codomain-image](https://codurance.com/assets/custom/img/blog/2018-01-18-functions/diagram.png)

Where, as we stated, `A` is the domain, `B` is the codomain, and `[2, 4, 6]` is the image of the function.

## Arity

Arity is the number of arguments that a function takes. We say that the arity of `f(x: Int)` is 1, or that is a unary function, or that is a function with one argument. Therefore, the arity of a function can be expressed with a number or the spring term. Unary, binary, ternary, etc... Are words that come from Latin, but mathematicians usually use Greek instead of Latin, so, usually, they interchange those words for the same ones coming from Greek. We can say as well that the arity of a function is monadic, dyadic, or triadic.

## Function Composition

Function composition is one of the bases of functional programming. The idea is that if you have a function `f = A->B` and a function `g = B->C` you can create a 3rd function `h = A->C` which internally uses `f` and `g` to create that `C`, that is: `h = g(f(x))`. If we express it in mathematical terms we can say that `h = f∘g` readed as "h is equal to f after g" or what is the same: `h = Cgf` An example of function composition is:

We declared two functions, `intToString` and `stringToDouble`. When we compose them, we create a third function that accepts an int and returns a double. So if we call it: `composedFunction("32")`, it returns `32.0`, which is the result after converting that String to int, and from that int to a Double. Notice that when composing functions, the functions are applied from right to left, this time: `intToString` and then `stringToDouble`. We can do the same without modifying the order of the functions with the function `andThen`. This will look like this:

This is the same and, in my opinion, less confusing. This last expression could be stated without infix operators as follows:

## Higher-Order Functions

The idea behind higher-order functions is that functions are values, hence functions can be passed around as we do with Integers, Strings, etc. Functions that accept other functions as arguments or return functions are called higher-order functions. An example of a really common higher-order function is `map`. Its definition in Scala's List class is:

The meaning of map is to apply a transformation to every element of the List and return a new List with all the new transformed elements. If a language supports higher-order functions, we say that the functions in that language are treated as [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) -- that is, functions are first-class functions. So when we refer to a programming language, we say that the language supports first-class citizens but if we refer to a function, we say that the function is a first-class function. One of the convenient usages of higher-order functions is to create inline functions, which we call anonymous functions or function literals. One example using the previously defined map could be this:

As you can see, the function `i => i + 1` is passed in as an argument of the `map` function.

## Partial Application

Partial application means that for a function that accepts a number of arguments, N, we can fix or bind some of its arguments that it takes to reduce the arity of the function. Consider these two functions:

Notice that `sumOfOne` partially applies the function sum, reducing its arity to 1. This is super useful, and if you take a look on the internet, you will see some people using this technique as a replacement for dependency injection.

## Currying

Currying is a technique that allows us to decompose a function with arity N (where N is > 1) in a chain of calls to smaller functions with arity 1. Let's see an example:
    
    
    def sumCurried = (a: Int) => (b: Int) => a + b

Now `sumCurried` returns a function that returns another function. That last one calculates the result. Doing that, we reduced the arity of sum to 1, expressing it as a smaller function. Scala can automatically curry a function using the `curried` function, an example of the previous version of sum:

This is a sample curry implementation:
    
    
    def curry[A, B, C](f: (A, B) => C): A => (B => C) = a => b => f(a, b)

It receives a function with arity 2 and returns a function with arity 1, which returns another function with arity 1, and finally, that function calls the given function with the required parameters. Take some time to digest this, and if you have the chance, play around a little until you understand the concept. It is a powerful technique, but it takes some time to fully understand it. We can, as well, uncurry a function. It is the same concept, but all the way around, so we take a function with less arity and we convert it to another with a higher arity. The dual of the previous function is:
    
    
    def uncurry[A, B, C](f: A => (B => C)): (A, B) => C = (a, b) => f(a)(b)

This time, it takes a function with arity 1 and it returns a function with arity 2 that finally applies those arguments to the original one.

## Currying vs. Partial Application

So, what is the difference between currying and partial application? As we stated before:

  * **Currying**: Ability to decompose a function with arity N (where N is > 1) in a chain of calls to smaller functions with arity 1.
  * **Partial application**: Possibility to apply a function with a given set of arguments to reduce the original function arity. A requirement to do partial application is that the function is already curried so that we can apply arguments one by one.

This is an example of how to apply currying to a binary function:
    
    
    @ def aFunction(a: Int, b: String) : String = a.toString + b 
    
    
    curriedFunction: Int => String => String = ammonite.$sess.cmd1$$Lambda$2127/1053392896@788bebee

This is an example of how to partially apply a curried function:
    
    
    partiallyAppliedFunction: String => String = ammonite.$sess.cmd1$$Lambda$2140/255517071@6ad5f700

There is a small difference, but is important to understand it.

[Download Building Reactive Microservices in Java](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031): Asynchronous and Event-Based Application Design. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031).

Topics:

java ,functional programming ,scala ,arity ,higher-order functions ,currying ,partial application ,tutorial
