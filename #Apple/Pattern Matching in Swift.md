# Pattern Matching in Swift

_Captured: 2015-09-19 at 01:53 from [oleb.net](http://oleb.net/blog/2015/09/swift-pattern-matching/)_

Updates:

  1. Included a note about the existing Swift syntax for this problem. Renamed the custom operators because I thought of better symbols. Added a thought about functional programming to the conclusion. 

[Download this article as a playground](http://oleb.net/media/swift-pattern-matching.playground.zip) for Xcode 7. The text in the playground is identical to the blog post.

A great feature of Swift is that you can extend the pattern matching system. [Patterns](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Patterns.html) are the rules values are matched against in the cases of a `switch` statement, a `catch` clause of a `do` statement, or in the case condition of an `if`, `while`, `guard`, or `for`-`in` statement.

For example, suppose you want to check whether an integer is greater than, less than, or equal to zero. You could do that with an `if`-`else if`-`else` construct, but it's not very pretty:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    
    
    let x = 10
    if x > 0 {
        print("positive")
    } else if x < 0 {
        print("negative")
    } else {
        print("zero")
    }
    

A `switch` statement would be much nicer. I would love to be able to write code like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    
    
    // Pseudocode
    switch x {
    case > 0:
        print("positive")
    case < 0:
        print("negative")
    case 0:
        print("zero")
    }
    

But pattern matching using inequalities is not supported by default. Let's see if we can fix that. To make it clearer what's going on, I'll ignore the pretty `case > 0` syntax for the moment and settle for something like `case greaterThan(0): print("positive")`. I'll get back to defining custom operators later.

# Extending pattern matching

Swift's pattern matching is based on the `~=` operator. A match succeeds if the expression `pattern ~= value` returns true. The standard library comes with [four overloads for the `~=` operator](http://swiftdoc.org/operator/tildeeq/): one for `Equatable` types, one for optionals, one for ranges, and one for intervals. None of these match our needs, though ranges and intervals come close. More on that in a future article.

So we need to implement our own version of `~=`. The form of that function is:
    
    
    1
    
    
    func ~=(pattern: ???, value: ???) -> Bool
    

We know the function must return a `Bool` because that's the answer we need to provide: does the value match the pattern or not? The next question we need to ask ourselves is, what should the types of the arguments be?

For `value`, we could use `Int` since that's what we need in the example but let's make it generic and accept any type `T`. The `pattern` in our case is something of the form `greaterThan(0)` or `lessThan(0)`. More generally, the pattern should be a function which takes `value` as its argument and returns `true` if there is a match or `false` otherwise. The type of `value` is `T`, so the type of `pattern` should be `T -> Bool`:
    
    
    1
    2
    3
    
    
    func ~=<T>(pattern: T -> Bool, value: T) -> Bool {
        return pattern(value)
    }
    

Now we still need to define the `greaterThan` and `lessThan` functions that produce the pattern. It is important not to confuse the `0` in the pattern `greaterThan(0)` with the value we want to match against. The argument to `greaterThan` is part of the pattern, which is then in a second step applied to the value. So for example, `greaterThan(0) ~= x` is the same as `greaterThan(0)(x)`.

We know that `greaterThan(0)` must produce a function that takes a value and returns `Bool`. So in turn, `greaterThan` must be a function that takes another value and returns the first function. We constrain the arguments to `Comparable` in order to be able to use Swift's `>` and `<` operators in the implementation:
    
    
    1
    2
    3
    
    
    func greaterThan<T : Comparable>(a: T) -> (T -> Bool) {
        return { (b: T) -> Bool in b > a }
    }
    

Functions of this kind, where the function takes one parameter and then returns a function that takes another parameter (and so on), are called [curried functions](https://en.wikipedia.org/wiki/Currying). (I wrote last year about how [instance methods in Swift are a form of (partially) curried functions](http://oleb.net/blog/2014/07/swift-instance-methods-curried-functions/).) Swift provides [a special syntax for the definition of curried functions](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Declarations.html#//apple_ref/doc/uid/TP40014097-CH34-ID363) that mimics how they are called. Using this syntax, our functions look like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    func greaterThan<T : Comparable>(a: T)(_ b: T) -> Bool {
        return b > a
    }
    
    func lessThan<T : Comparable>(a: T)(_ b: T) -> Bool {
        return b < a
    }
    

That's all we need to write the first version of our `switch` statement:
    
    
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
    case greaterThan(0):
        print("positive")
    case lessThan(0):
        print("negative")
    case 0:
        print("zero")
    default:
        fatalError("Should be unreachable")
    }
    

Pretty nice, but note the `default` case. It's impossible with this solution to give the compiler any hints for exhaustiveness checking, so it will always force us to provide a default case. If you are certain that your patterns cover every possible value, it is a good idea to put a `fatalError()` call into the default case to document your expectation that this code path should never get hit.

# Custom operators

Scroll back to the top for a moment and take another look at the pseudocode syntax we started with. Ideally, we would like to replace `case greaterThan(0)` and `case lessThan(0)` with `case > 0` and `case < 0`, respectively.

Custom operators are a controversial topic because they often reduce readability if the reader is unfamiliar with a particular operator. Going back to our example, something like `case greaterThan(0)` is perfectly well readable, so one can certainly argue that no custom operators are needed. On the other hand, everybody understands what `case > 0` means, so let's try this. As we will see, it's not going to be quite as pretty.

Our custom operators are _unary_ - they have just one operand. And they are _prefix_ operators (as opposed to _postfix_, which come after their operand). There can be no whitespace between unary operators and their operands because Swift uses whitespace to disambiguate between unary and binary operators. Moreover, `<` is [not allowed as a prefix operator](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/LexicalStructure.html#//apple_ref/doc/uid/TP40014097-CH30-ID418), so we'll have to settle for something else. (`>` is allowed as a prefix, but not as a postfix operator.)

I suggest we use `~>` and `~<`, respectively. While it is not ideal that `~>` looks suspiciously like an arrow, the tilde nicely suggests an affiliation with the pattern match operator `~=`. And the other alternative I could come up with (`>>` and `<<`) risks to get mixed up with the bitshifting operators.

The actual implementation is trivial. All we have to do is declare the operators and write functions that implement them. These just delegate to the `greaterThan` and `lessThan` functions we already have:
    
    
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
    
    
    prefix operator ~> { }
    prefix operator ~< { }
    
    prefix func ~> <T : Comparable>(a: T)(_ b: T) -> Bool {
        return greaterThan(a)(b)
    }
    
    prefix func ~< <T : Comparable>(a: T)(_ b: T) -> Bool {
        return lessThan(a)(b)
    }
    

With that, our `switch` statement becomes:
    
    
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
    case ~>0:
        print("positive")
    case ~<0:
        print("negative")
    case 0:
        print("zero")
    default:
        fatalError("Should be unreachable")
    }
    

Again, note that the missing whitespace between operators and operands is significant.

This is the best we can do. It's quite close to the original plan but obviously not perfect.

**Update September 19, 2015:** [Joseph Lord reminded me](https://twitter.com/jl_hfl/status/644992487346581504) that Swift does have a similar syntax for this:
    
    
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
    case x where x > 0:
        print("positive")
    case x where x < 0:
        print("negative")
    case 0:
        print("zero")
    default:
        fatalError("Should be unreachable")
    }
    

(The default case is still necessary to satisfy the compiler. I filed a bug about that, rdar://22765436.)

This syntax, while it may not be quite as concise as our custom solution, is definitely good enough that you shouldn't create a custom syntax for this purpose. However, the design is generic and has many different applications. Read on.

# Other applications

Incidentally, the solution presented here is very generic. Our overload of the pattern matching operator `~=` works for any `T` and any function that takes a `T` and returns a `Bool`. In other words, our implementation makes `pattern ~= value` syntactic sugar for `pattern(value)`. And by extension, `switch value { case pattern: ... }` becomes syntactic sugar for `if pattern(value) { ... }`.

## Checking if a number is even or odd

Here are some examples how this can be used. First, a simple one that illustrates the point but is not very relevant in practice. Suppose you have a function `isEven` that checks if a number is even:
    
    
    1
    2
    3
    
    
    func isEven<T : IntegerType>(a: T) -> Bool {
        return a % 2 == 0
    }
    

Now this:
    
    
    1
    2
    3
    4
    
    
    switch isEven(x) {
    case true: print("even")
    case false: print("odd")
    }
    

can become this:
    
    
    1
    2
    3
    4
    
    
    switch x {
    case isEven: print("even")
    default: print("odd")
    }
    

Note the default case again. The following would not work:
    
    
    1
    2
    3
    4
    5
    
    
    switch x {
    case isEven: print("even")
    case isOdd: print("odd")
    }
    // error: Switch must be exhaustive, consider adding a default clause
    

## Matching strings

As a more practical example, suppose you want to check a string against several prefixes and suffixes. Let's first write two free functions, `hasPrefix` and `hasSuffix`, that take two strings and check if the first argument is a prefix/suffix of the second. These are just variants of the existing `[String.hasPrefix`](https://developer.apple.com/library/ios/documentation/Swift/Reference/Swift_String_Structure/index.html#//apple_ref/swift/structm/String/s:FSS9hasPrefixFSSFSSSb) and `[String.hasSuffix`](https://developer.apple.com/library/ios/documentation/Swift/Reference/Swift_String_Structure/index.html#//apple_ref/swift/structm/String/s:FSS9hasSuffixFSSFSSSb) methods in the standard library that bring the arguments in a convenient order us (prefix/suffix first, full string second). If you use partially applied functions and pass them to other functions a lot, you'll find that you often have to do something like this to accomodate the interface you're working with. It can be annoying, but it's never hard to do.
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    func hasPrefix(prefix: String)(value: String) -> Bool {
        return value.hasPrefix(prefix)
    }
    
    func hasSuffix(suffix: String)(value: String) -> Bool {
        return value.hasSuffix(suffix)
    }
    

Now we can do this, which is very easy to read in my opinion:
    
    
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
    
    
    let str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    switch str {
    case hasPrefix("B"), hasPrefix("C"):
        print("Starts with B or C")
    case hasPrefix("D"):
        print("Starts with D")
    case hasSuffix("Z"):
        print("Ends with Z")
    default:
        print("Something else")
    }
    

# Conclusion

By creating a generic solution for our initial problem, we came up with something that can be applied to a lot of very different problems. I find that this often happens when you treat functions as values that can be passed around and used in places you wouldn't normally expect them. It is one of the central concepts behind the argument that functional programming improves composability.

Extending Swift's pattern matching system with new capabilities for the built-in types or for your own custom types can be extremely powerful. As always, be careful not to push it too far, though. A custom syntax can make your code a lot harder to read for people who are not familiar it, even if it is seemingly cleaner than a more conservative solution.
