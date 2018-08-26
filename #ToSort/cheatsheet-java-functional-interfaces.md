# Cheatsheet: Java Functional Interfaces

_Captured: 2018-03-12 at 20:16 from [dzone.com](https://dzone.com/articles/cheatsheet-java-functional-interfaces?edition=365238&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-12)_

Take 60 minutes to understand the Power of the Actor Model with "Designing Reactive Systems: The Role Of Actors In Distributed Architecture". Brought to you in partnership with [Lightbend](https://dzone.com/go?i=281427&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Designing-Reactive-Systems_RES-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dpre-roll-text%26utm_campaign%3DCOLL-20XX-Designing-Reactive-Systems%26utm_term%3Dnone%26utm_content%3Djava-zone).

Looking at the alphabetical list of 43 functional interfaces in java.util.function is a bit overwhelming. Trying to learn and remember them all is going to be a challenge!

Luckily Joshua Bloch came to the rescue in his 3rd edition of Effective Java.

**Item 44: Favor the use of standard functional interfaces.**

I really recommend you read this!

It's unlikely that you will need to write your own, except in the cases that Prof. Bloch describes:

  * Will be often used and a descriptive name is helpful
  * Has a strong contract associated with it
  * Would benefit from custom default methods

My goal is to produce a cheat sheet based on his work for easy reference (or your next interview!).

**Remember **(covers 39 of the 43 functional interfaces)

  * Predicate, Unary Operator, BinaryOperator, Function, Supplier, and Consumer operate on reference types. Each has 3 variants, which operate on double, int, or long respectively

  * BiPredicate, BiFunction, BiConsumer accept two reference types as arguments 

  * Function has six variants, which can accept a primitive and return a different primitive, and six (inc. BiFunction) that accept reference types and return a primitive

## Summary

  * There are five basic functional interfaces that, by default, operate on a single reference type: Predicate, Unary Operator, Function, Supplier, Consumer and one which operates on two reference types -- BinaryOperator

  * Each of the six basic types has three variants that accept a primitive: double, int, or long

  * Variants of the three basic types accept two arguments: BiPredicate, BiFunction, BiConsumer

  * Function has 6 variants that convert one of the primitives (double, int, long) to a different primitive.

  * Function and BiFunction each have 3 variants that take a reference type and return a primitive double, int, or long

  * Supplier has a variant that returns a boolean

  * BiConsumer has three variants that accept a reference type and a primitive: double, int, or long

## Basic Types

PREDICATE 

takes one (or two) argument(s) and returns a boolean (5 variants)

UNARY OPERATOR 

result and the single argument types are the same (4 variants)

BINARY OPERATOR 

result and both argument types are the same (4 variants)

FUNCTION 

result and one (or two) argument(s) types are different (17 variants)

SUPPLIER 

takes no arguments, returns a value ( 5 variants )

CONSUMER 

takes one (or two) arguments and returns no value (8 variants)

## **Notation**

If the interface accepts primitive arguments: prefixed Double, Int, Long, e.g. DoubleConsumer

If the interface produces a primitive result: prefixed ToDouble, ToInt, ToLong, e.g. ToDoubleFunction

If the interface both accepts and produces a primitive: prefixes combined e.g. IntToDoubleFunction

BiConsumer variants that accept an object type and a primitive are prefixed Obj + the primitive, e.g. ObjDoubleConsumer

## Package Summary

<https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html>

### Predicate

Predicate<T>

Represents a predicate (boolean-valued function) of one argument (reference type)

DoublePredicate

Accepts one double-valued argument

IntPredicate

Accepts one int-valued argument.

LongPredicate

Accepts one long-valued argument

BiPredicate<T,U>

Accepts two arguments (reference types)

### Unary Operator

UnaryOperator<T>

Represents an operation on a single operand that produces a result of the same type as its operand (reference type)

DoubleUnaryOperator

Accepts single double-valued operand and produces a double-valued result

IntUnaryOperator

Accepts a single int-valued operand and produces an int-valued result

LongUnaryOperator

Accepts a single long-valued operand and produces a long-valued result

### Binary Operator

BinaryOperator<T>

Represents an operation upon two operands of the same type, producing a result of the same type as the operands (reference type)

DoubleBinaryOperator

Accepts two double-valued operands and produces a double-valued result

IntBinaryOperator

Accepts two int-valued operands and produces an int-valued result

LongBinaryOperator

Accepts two long-valued operands and produces a long-valued result.

### **Function**

Function<T,R>

Represents a function that accepts one argument and produces a result (reference type)

DoubleFunction<R>

Accepts a double-valued argument and produces a result

IntFunction<R>

Accepts an int-valued argument and produces a result

LongFunction<R>

Accepts a long-valued argument and produces a result

DoubleToIntFunction

Accepts a double-valued argument and produces an int-valued result

DoubleToLongFunction

Accepts a double-valued argument and produces a long-valued result

IntToDoubleFunction

Accepts an int-valued argument and produces a double-valued result

IntToLongFunction

Accepts an int-valued argument and produces a long-valued result

LongToIntFunction

Accepts a long-valued argument and produces an int-valued result

LongToDoubleFunction

Accepts a long-valued argument and produces a double-valued result.

ToDoubleFunction<T>

Accepts a reference type and produces an int-valued result

ToIntFunction<T>

Accepts a reference type and produces an int-valued result

ToLongFunction<T>

Accepts a reference type and produces a long-valued result.

BiFunction<T,U,R>

Represents a function that accepts two arguments and produces a result (reference type)

ToDoubleBiFunction<T,U>

Accepts two reference type arguments and produces a double-valued result

ToIntBiFunction<T,U>

Accepts two reference type arguments and produces an int-valued result

ToLongBiFunction<T,U>

Accepts two reference type arguments and produces a long-valued result

### Supplier

Supplier<T>

Represents a supplier of results (reference type)

DoubleSupplier

A supplier of double-valued results

IntSupplier

A supplier of int-valued results

LongSupplier

A supplier of long-valued results

BooleanSupplier

A supplier of boolean-valued results

### Consumer

Consumer<T>

Represents an operation that accepts a single (reference type) input argument and returns no result

DoubleConsumer

Accepts a single double-valued argument and returns no result

IntConsumer

Accepts a single int-valued argument and returns no result

LongConsumer

Accepts a single long-valued argument and returns no result

BiConsumer<T,U>

Represents an operation that accepts two (reference type) input arguments and returns no result

ObjDoubleConsumer<T>

Accepts an object-valued and a double-valued argument, and returns no result

ObjIntConsumer<T>

Accepts an object-valued and an int-valued argument, and returns no result

ObjLongConsumer<T>

Accepts an object-valued and a long-valued argument, and returns no result

Learn how the Actor model provides a simple but powerful way to design and implement reactive applications that can distribute work across clusters of cores and servers. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=281428&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Designing-Reactive-Systems_RES-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-20XX-Designing-Reactive-Systems%26utm_term%3Dnone%26utm_content%3Djava-zone).
