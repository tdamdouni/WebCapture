# Ranges and Intervals in Swift

_Captured: 2015-09-24 at 23:57 from [oleb.net](http://oleb.net/blog/2015/09/swift-ranges-and-intervals/)_

In my previous [post on pattern matching](http://oleb.net/blog/2015/09/swift-pattern-matching/), I mentioned that the standard library includes overloads of the pattern matching operator `~=` for ranges and intervals.

These two data types are related, but have some important differences. I'd like to talk a bit more about them because they offer an alternative solution to our original problem of expressing inequalities in `switch` statements.

# Ranges

Ranges are represented by the `[Range`](http://swiftdoc.org/swift-2/type/Range/) type. A range is a _collection_ of _indexes_.

**A range is a collection of indexes.**

Ranges are used a lot in the standard library, especially in the context of collections. The tight relationship between ranges and collections becomes apparent when we look at the type definition for `Range`:
    
    
    1
    2
    3
    
    
    struct Range<Element : ForwardIndexType> : CollectionType, Indexable, ... { 
        ...
    }
    

The elements in a range must conform to `[ForwardIndexType`](http://swiftdoc.org/swift-2/protocol/ForwardIndexType/), which is the protocol that a ton of the functionality of `CollectionType` is based on. Having a special type that can represent a range of collection indexes makes sense for specifying subsets of a collection. For example, we can use ranges to access part of an array:
    
    
    1
    2
    3
    
    
    let numbers = [1,2,3,4,5,6,7,8,9]
    // 1..<5 is equivalent to Range(start: 1, end: 5)
    numbers[1..<5] // [2,3,4,5]
    

As you can see in the type definition, `Range` itself also conforms to `CollectionType`, so you can do with ranges pretty much everything you can do with arrays, like iterating over the elements in a `for` loop or checking if a particular index falls within the range using `contains(_:)`.

Although ranges are mainly used with other collections, nothing stops you from creating a `Range<Int>` just to represent an interval of numbers. After all, `[Int`](http://swiftdoc.org/swift-2/type/Int/) implements `ForwardIndexType`. And that's where we come back to our pattern matching problem.

We can represent the condition `x < 0` using a range: `(Int.min..<0).contains(x)` is exactly equivalent. It is vastly slower, though. The default implementation of `contains(_:)` traverses the entire collection, and executing a loop [nine quintillion times](https://en.wikipedia.org/wiki/9223372036854775807) in the worst case is not cheap. We could provide a better implementation for indexes that are `[Comparable`](http://swiftdoc.org/swift-2/protocol/Comparable/) (such as `Int`):
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    
    
    extension Range where Element : Comparable {
        func contains(element: Element) -> Bool {
            return element >= startIndex && element < endIndex
        }
    }
    
    (Int.min..<0).contains(-1) // true
    (Int.min..<0).contains(0) // false
    (Int.min..<0).contains(1) // false
    

That's a nice exercise, but it isn't even necessary in our case because the `~=` implementation for `Range` is already efficient (like our `contains(_:)` overload, it only works with indexes that are `Comparable`). So we can do this:
    
    
    1
    2
    3
    
    
    Int.min..<0 ~= -1 // true
    Int.min..<0 ~= 0 // false
    Int.min..<0 ~= 1 // false
    

With this we can write a `switch` statement that checks whether a number is greater than, less than, or equal to zero using ranges, right? Unfortunately, not quite. This code crashes:
    
    
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
    
    
    let x = 10
    switch x {
    case 1...Int.max: // EXC_BAD_INSTRUCTION
        print("positive")
    case Int.min..<0:
        print("negative")
    case 0:
        print("zero")
    default:
        fatalError("Should be unreachable")
    }
    

We get an `EXC_BAD_INSTRUCTION` at the `case 1...Int.max:` line, and the error message says "fatal error: Range end index has no valid successor". The reason for this is that a range's `endIndex` is _always_ the value that comes after the last element in the range. This is true for both half-open ranges (created with the `..<` operator) and closed ranges (created with the `...` operator) because both variants are represented identically internally. `a...b` is really just `a..<b.successor()`.

**A `Range<Int>` can never contain `Int.max`.**

That means `Int.max` can never be a member of a `Range<Int>`, and the same is true for other types that have a maximum value. This limitation makes ranges unusable for our purpose. So let's look at intervals next.

# Intervals

Ranges and intervals model the same concept (a consecutive sequence of elements, with a start and an end), using different approaches. Ranges are index-based and can therefore be collections; they get most of their functionality from this characteristic. Intervals _aren't_ collections; their implementation relies on the `Comparable` protocol. We can only create intervals for types that conform to `Comparable`:
    
    
    1
    2
    3
    4
    
    
    protocol IntervalType {
        typealias Bound : Comparable
        ...
    }
    

Unlike ranges, intervals are represented by a protocol, `[IntervalType`](http://swiftdoc.org/swift-2/protocol/IntervalType/), and two concrete implementations, `[HalfOpenInterval`](http://swiftdoc.org/swift-2/type/HalfOpenInterval/) and `[ClosedInterval`](http://swiftdoc.org/swift-2/type/ClosedInterval/). The two range operators also provide overloads for creating intervals: `..<` creates a `HalfOpenInterval` and `...` creates a `ClosedInterval`. Note that you have to explicitly specify the type because the overload for `Range` is the default:
    
    
    1
    2
    3
    4
    
    
    let int1: HalfOpenInterval = 1..<5
    int1.contains(5) // false
    let int2: ClosedInterval = 1...5
    int2.contains(5) // true
    

Another thing to remember is that a `ClosedInterval` cannot be empty. `x...x` always contains x and `x...(x - 1)` results in runtime error.

Closed intervals can contain a type's maximum value, however. That means we can now write our `switch` statement. Again, explicit typecasts are necessary to tell the compiler that we want intervals instead of ranges:
    
    
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
    
    
    let x = 10
    switch x {
    case 1...Int.max as ClosedInterval:
        print("positive")
    case Int.min..<0 as HalfOpenInterval:
        print("negative")
    case 0:
        print("zero")
    default:
        fatalError("Should be unreachable")
    }
    

# Custom operators for open-ended intervals

That's nice, but I'd like to get rid of the `Int.min` and `Int.max` values. To do this, we need custom prefix and postfix operators to represent open-ended intervals - intervals that include all values that are smaller than an upper bound or larger than a lower bound, respectively. Not only would the syntax be nicer; ideally, these operators would also work with other types than `Int` and automatically go to the type's minimum or maximum value. It would look like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    switch x {
    case 1...: // an interval from 1 to Int.max (inclusive)
        print("positive")
    case ..<0: // an interval from Int.min to 0 (exclusive)
        print("negative")
    ...
    }
    

We need two variants each for `..<` and `...`, a prefix and a postfix one. The following is largely based on [a wonderful Gist](https://gist.github.com/natecook1000/3b15b8bd974c8c08b3df) by [Nate Cook](http://natecook.com) who implemented this already in November 2014, using a mix of ranges and intervals. The code I present here uses intervals throughout.

The first thing we have to do is declare the operators we want to introduce:
    
    
    1
    2
    3
    4
    
    
    prefix operator ..< { }
    prefix operator ... { }
    postfix operator ..< { }
    postfix operator ... { }
    

And here is the implementation for the first one for `Int`:
    
    
    1
    2
    3
    4
    
    
    /// Forms a half-open interval from `Int.min` to `upperBound`
    prefix func ..< (upperBound: Int) -> HalfOpenInterval<Int> {
        return Int.min..<upperBound
    }
    

Not bad, but we should really make this generic. Intervals require their underlying type to be `Comparable` so using the same constraint would be the natural choice. Here's where we run into a problem, though: we need to know the minimum value of the type `T` to construct the interval, and there seems to be no generic way to get this:
    
    
    1
    2
    3
    
    
    prefix func ..< <T : Comparable>(upperBound: T) -> HalfOpenInterval<T> {
        return T.min..<upperBound // error: type 'T' has no member 'min'
    }
    

Even other protocols in the standard library hierarchy for numbers (like `[IntegerType`](http://swiftdoc.org/swift-2/protocol/IntegerType/), for example) don't provide this - the `min` and `max` properties are defined on the number types themselves.

Nate came up with a very cool solution to this problem: define a custom protocol, `MinMaxType`, that lifts the two properties `min` and `max` into a separate interface. Since all integer types already have these properties, conforming them to the new protocol is no additional work:
    
    
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
    
    
    /// Conforming types provide static `max` and `min` constants.
    protocol MinMaxType {
        static var min: Self { get }
        static var max: Self { get }
    }
    
    // Extend relevant types
    extension Int : MinMaxType {}
    extension Int8 : MinMaxType {}
    extension Int16 : MinMaxType {}
    extension Int32 : MinMaxType {}
    extension Int64 : MinMaxType {}
    extension UInt : MinMaxType {}
    extension UInt8 : MinMaxType {}
    extension UInt16 : MinMaxType {}
    extension UInt32 : MinMaxType {}
    extension UInt64 : MinMaxType {}
    

This is a great trick that is worth keeping in mind. Whenever you have several unrelated types that have one or more methods or properties with identical types, you can create a new protocol to provide a common interface for them.

**Whenever you have several unrelated types that have one or more methods with identical signatures, you can create a new protocol to provide a common interface for them.**

Constraining our generic type `T` to `MinMaxType` makes the implementation work:
    
    
    1
    2
    3
    4
    5
    
    
    /// Forms a half-open interval from `T.min` to `upperBound`
    prefix func ..< <T : Comparable where T : MinMaxType>
        (upperBound: T) -> HalfOpenInterval<T> {
        return T.min..<upperBound
    }
    

Here are the implementations for the other three operators:
    
    
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
    
    
    /// Forms a closed interval from `T.min` to `upperBound`
    prefix func ... <T : Comparable where T : MinMaxType>
        (upperBound: T) -> ClosedInterval<T> {
        return T.min...upperBound
    }
    
    /// Forms a half-open interval from `lowerBound` to `T.max`
    postfix func ..< <T : Comparable where T : MinMaxType>
        (lowerBound: T) -> HalfOpenInterval<T> {
        return lowerBound..<T.max
    }
    
    /// Forms a closed interval from `lowerBound` to `T.max`
    postfix func ... <T : Comparable where T : MinMaxType>
        (lowerBound: T) -> ClosedInterval<T> {
        return lowerBound...T.max
    }
    

And some tests:
    
    
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
    
    
    (..<0).contains(Int.min) // true
    (..<0).contains(-1) // true
    (..<0).contains(0) // false
    
    (...0).contains(Int.min) // true
    (...0).contains(0) // true
    (...0).contains(1) // false
    
    (0..<).contains(-1) // false
    (0..<).contains(0) // true
    (0..<).contains(Int.max) // false
    (0..<).contains(Int.max - 1) // true
    
    (0...).contains(-1) // false
    (0...).contains(0) // true
    (0...).contains(Int.max) // true
    

Back to our `switch` statement, which works great now:
    
    
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
    
    
    switch x {
    case 1...:
        print("positive")
    case ..<0:
        print("negative")
    case 0:
        print("zero")
    default:
        fatalError("Should be unreachable")
    }
    

# Conclusion

Ranges and intervals in Swift serve similar purposes but have different implementations and generic constraints. Ranges are based on indexes and are used most often in the context of collections. The fact that a range can't contain the maximum value of a type can make them unsuitable for working with intervals of numbers. Intervals work with all `Comparable` types and don't have the maximum-value limitation.

While custom operators should be used very sparingly, I'd argue that in this case they significantly improve readability without harming comprehensibility - the prefix and postfix operators are so close in meaning to their binary counterparts that even readers unfamiliar with the code should have no trouble understanding them.

That said, I'd still argue that the advantages of the custom notation over the standard Swift syntax (`case _ where x > 0`) are so small in this specific case that using it in real code isn't worth it. Treat this as a thought experiment, not as a recommendation.

If you liked this article, you might enjoy Chris Eidhof's and Airspeed Velocity's upcoming book, [Advanced Swift](https://www.objc.io/books/advanced-swift/). They discuss, among many other things, the same idea of open-ended ranges in the context of collection subscripting. I'm the technical reviewer for the book, so I'm obviously biased, but I highly recommend it if you're interested in Swift. The book is currently in beta, but you can already buy it and get immediate access to the current draft.
