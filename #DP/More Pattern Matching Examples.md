# More Pattern Matching Examples

_Captured: 2015-10-01 at 00:23 from [oleb.net](http://oleb.net/blog/2015/09/more-pattern-matching-examples/)_

In this final part of my little series on pattern matching I'd like to show you some more examples of what we can do with this.

# Recap

In [part 1](http://oleb.net/blog/2015/09/swift-pattern-matching/), we overloaded the pattern matching operator `~=` with a variant that takes a function of the type `T -> Bool` as its first argument:
    
    
    1
    2
    3
    
    
    func ~=<T>(pattern: T -> Bool, value: T) -> Bool {
        return pattern(value)
    }
    

We also saw that this implementation is very generic. We can use it to match any value of type `T` against any function that takes a `T` and returns a `Bool` (like the `isEven` example in part 1).

When we tried to use pattern matching with the `[String.hasPrefix`](http://swiftdoc.org/v2.0/type/String/#func-hasPrefix) method next, we hit a problem with the order of the parameters. Remember that [instance methods are (partially) curried functions](http://oleb.net/blog/2014/07/swift-instance-methods-curried-functions/) with the instance as the first argument. So the type of the `String.prefix` function is `String -> String -> Bool`, where the first `String` parameter is the method receiver and the second one is the prefix we want to match:
    
    
    1
    2
    3
    4
    
    
    // This:
    "Hello World".hasPrefix("H") // true
    // is equivalent to this:
    String.hasPrefix("Hello World")("H") // true
    

The argument order is exactly backwards from what we need when we want to use a partially applied version of this method with our pattern matching operator. We need a version where the receiver is applied last (unless you want to match one prefix against multiple strings, in which case the order would be correct but the method name would be confusing). In part 1 we wrote a small helper function that flips the arguments:
    
    
    1
    2
    3
    4
    5
    6
    
    
    func hasPrefix(prefix: String)(_ value: String) -> Bool {
       return value.hasPrefix(prefix)
    }
    
    // Now we can call it with the arguments flipped:
    hasPrefix("H")("Hello World") // true
    

That way we can partially apply the prefix and get a function back that we can then use as the pattern argument for `~=`.

# A Generic Solution

This works, but doing this for every method we want to use in this way quickly becomes tedious. So let's write a generic function, `flip`, that moves the first argument of a curried function to the back, right before the final return value.
    
    
    1
    2
    3
    4
    5
    6
    
    
    /// Moves the first argument to the back
    func flip<A, B, C>(method: A -> B -> C) -> (B -> A -> C) {
        return { (b: B) in
            { (a: A) in method(a)(b) }
        }
    }
    

I like the type signature of this function because the type alone shows very clearly what it does: there is really only one possible implementation for a function of the type `(A -> B -> C) -> (B -> A -> C)`. The function body with its pair of nested closure expressions can be a bit difficult to parse, though. An alternative way of writing this function if to take advantage of Swift's special syntax for curried functions. This variant makes the function body trivial to write, but the type signature is a little harder to understand in my opinion:
    
    
    1
    2
    3
    
    
    func flip<A, B, C>(method: A -> B -> C)(_ b: B)(_ a: A) -> C {
        return method(a)(b)
    }
    

We can now match a string against different prefixes like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    
    
    let str = "ABCDEF"
    switch str {
    case flip(String.hasPrefix)("A"):
        print("A")
    case flip(String.hasPrefix)("B"):
        print("B")
    default:
        "default"
    }
    

And since `flip` is generic, it works with all methods on all types - even those that have a different number of parameters. This last bit may be surprising, but a (non-curried) function that takes multiple arguments really just takes one argument: a tuple with a corresponding number of elements that have the same types as the parameters. It's no accident that the syntax for tuples, `(a, b)`, is the same as the syntax for function arguments, `f(a, b)` - they are the same thing. This means that any method matches the generic type `A -> B -> C` our `flip` function expects, no matter how many elements the parameter tuple (represented by the generic type `B`) contains.

# Examples

## Matching Arrays

`flip` even works for methods that take no arguments (except the implicit receiver parameter) because the empty tuple `()` is also a valid type. Unfortunately, we can't use `flip` directly on properties because Swift currently doesn't allow referring to a type's property as a function. We need write a separate wrapper function, like in this example for a collection's `[isEmpty`](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Reference/Swift_CollectionType_Protocol/index.html#//apple_ref/swift/intfp/CollectionType/s:vPSs14CollectionType7isEmptySb) property:
    
    
    1
    2
    3
    4
    5
    
    
    extension CollectionType {
        func isEmptyFunc() -> Bool {
            return isEmpty
        }
    }
    

Here is a full example where we do pattern matching on an array of numbers. In addition to the `[contains`](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Reference/Swift_SequenceType_Protocol/index.html#//apple_ref/swift/intfm/SequenceType/s:FeRq_Ss12SequenceTypeqqq_S_9GeneratorSs13GeneratorType7ElementSs9Equatable_SsS_8containsuRq_S_qqq_S_9GeneratorS0_7ElementS1__Fq_Fqqq_S_9GeneratorS0_7ElementSb) method that's included in the standard library, we use a custom overload of `contains` that takes two arguments and checks whether the sequence contains both.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    
    
    extension SequenceType where Generator.Element : Equatable {
        func contains(a: Self.Generator.Element, and b: Self.Generator.Element) -> Bool {
            return contains(a) && contains(b)
        }
    }
    
    let numbers = [1,2,3,4,5,6,7,8,9]
    switch numbers {
    case flip(Array.isEmptyFunc)():
        print("is empty")
    case flip(Array.contains)(10):
        print("contains 10")
    case flip(Array.contains)(2, 4):
        print("contains 2 and 4")
    case flip(Array.contains)(5):
        print("contains 5")
    default:
        print("default")
    }
    

## Matching CGRects

Or how about matching a `CGRect` against another?
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    
    
    import CoreGraphics
    
    let rect1 = CGRect(x: 20, y: 20, width: 50, height: 50)
    let rect2 = CGRect(x: 40, y: 40, width: 100, height: 100)
    
    switch rect1 {
    case flip(CGRect.contains)(rect2):
        "contains"
    case flip(CGRect.intersects)(rect2):
        "intersects"
    default:
        "default"
    }
    

## Matching Sets

One last example, comparing two sets. Here we use another helper function, `not`, to negate a pattern.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    
    
    func not<T>(f: T -> Bool) -> T -> Bool {
        return { !f($0) }
    }
    
    let set1: Set = [1,2,3,4,5,6,7,8,9]
    let set2: Set = [3,4,5]
    
    switch set1 {
    case flip(Set.contains)(10):
        "contains 10"
    case not(flip(Set.isSupersetOf)(set2)):
        "is not a superset of \(set2)"
    case flip(Set.isSupersetOf)(set2):
        "is superset of \(set2)"
    case flip(Set.isDisjointWith)(set2):
        "is disjoint with \(set2)"
    default:
        "default"
    }
    

# Conclusion

Let me say again that I'm not claiming you should write code like this. Although I think the patterns we developed are extremely elegant, the syntax is often less so. Many of the examples above are quite ugly in my opinion, and harder to read than the alternative (a bunch of if statements).

My goal with this series was to encourage you (and myself) to start thinking about programming problems in terms of functions. By treating functions as values that can be passed to and returned from other functions, and by composing multiple simple functions into more complex ones, we can build very generic and expressive systems from a few simple building blocks.
