# OptionSetType & Integers & Generics

_Captured: 2015-10-31 at 15:10 from [www.robertvojta.com](http://www.robertvojta.com/2015/10/31/optionsettype-integers-generics/)_

## Story behind

My son wanted to exercise math on the iPad. He likes math, which is good. We tried several apps, but nothing suits his needs. I did end up in the Xcode.

Started with implementation of `MathOperation`. `OptionSetType` looked like a good choice. He can exercise one operation, any combination or all of them. Here's the `OptionSetType` [documentation](http://swiftdoc.org/v2.0/protocol/OptionSetType/).
    
    
    struct MathOperation : OptionSetType {
        let rawValue: Int
        init(rawValue: Int) {
            self.rawValue = rawValue
        }
        
        static let Addition         = MathOperation(rawValue: 1)
        static let Subtraction      = MathOperation(rawValue: 2)
        static let Multiplication   = MathOperation(rawValue: 4)
        static let Division         = MathOperation(rawValue: 8)
    }

Later on, I came to the point where I wanted to select random `MathOperation` from provided options. But how? There's no _easy_ way and it seems that `enum` & `Set` would be much better. But let it be and finish it with `OptionSetType`. Just to learn more about Swift standard library. What do we need?

  * Conversion of `OptionSetType` to an array of single options. In other words - we need to convert `OptionSetType` to `Array<OptionSetType>`.
  * Generic implementation - any integer type can be used as `RawValue` (`OptionSetType`).

## Integers

All integer types (`Int`, …) are structs in Swift. All of them conform to slightly different set of protocols. Here's the quick overview:

![](http://www.robertvojta.com/public/images/swift-integers.png)

Lot of protocols omitted to make it more readable. Common ancestor for all integer types is `IntegerType` protocol. Great, I'm going to stick with it. Let's define `OptionSetType` extension in this way:
    
    
    extension OptionSetType where RawValue : IntegerType {
        var array: [Self] {
            // Return [empty] array of single options
        }
    }

Next step is to iterate over all single bit values (power of two), check if they're set and add them to an array. I do like generators, so, let's introduce `BitValuesGenerator` and implement `array` property with it.
    
    
    extension OptionSetType where RawValue : IntegerType {
        var array: [Self] {
            return AnySequence(BitValuesGenerator<RawValue>())
                // Filter out options that are not set
                .filter({ $0 & self.rawValue == $0 })
                // Transform them to `Self` (= `OptionSetType`)
                .map({ Self(rawValue: $0) })
        }
    }

## BitValuesGenerator

What do I want? In case of:

  * `UInt8` \- 1, 2, 4, 8, 16, 32, 64, 128
  * `Int8` \- 1, 2, 4, 8, 16, 32, 64
  * …

[Signed integer](https://en.wikipedia.org/wiki/Signed_number_representations) does use one bit for sign (minus, plus) and I'm going to ignore this bit.
    
    
    class BitValuesGenerator<Element : IntegerType> : AnyGenerator<Element> {
        var bitValue: Element? = 1
        
        override func next() -> Element? {
            guard let currentBitValue = bitValue else { return nil }
            bitValue = ? // How for `IntegerType`
            return currentBitValue
        }
    }

### Left shift

One can think that I can use `<<` operator.
    
    
    class BitValuesGenerator<Element : IntegerType> : AnyGenerator<Element> {
        var bitValue: Element? = 1
        
        override func next() -> Element? {
            guard let currentBitValue = bitValue else { return nil }
            bitValue = currentBitValue << 1 // no trap on overflow
            if bitValue! < currentBitValue { bitValue = nil } // overflow
            return currentBitValue
        }
    }

No, I can't. This code doesn't compile. Operator `<<` cannot be applied to operands of type `Element` and `Int`. And it cannot be applied to two `Element` operands as well even when `Element` is `IntegerType`. The problem lies in the Swift standard library.
    
    
    public func <<(lhs: UInt64, rhs: UInt64) -> UInt64
    public func <<(lhs: Int64, rhs: Int64) -> Int64
    public func <<(lhs: UInt, rhs: UInt) -> UInt
    public func <<(lhs: UInt8, rhs: UInt8) -> UInt8
    public func <<(lhs: Int8, rhs: Int8) -> Int8
    public func <<(lhs: UInt16, rhs: UInt16) -> UInt16
    public func <<(lhs: Int16, rhs: Int16) -> Int16
    public func <<(lhs: UInt32, rhs: UInt32) -> UInt32
    public func <<(lhs: Int32, rhs: Int32) -> Int32
    public func <<(lhs: Int, rhs: Int) -> Int

_Copy & paste_ for all integer types, but there's no `<<` operator for `IntegerType`.

### Optional left shift

What now? Going introduce new `<<?` operator - left shift or `nil` if overflow happens. And for `IntegerType` instead of copy & pasting it for all integer types.
    
    
    infix operator <<? {
        associativity none
        precedence 160
    }
    
    func <<? <T: IntegerType>(lhs: T, rhs: Int) -> T? {
        // ?
    }

Now I'm going to check Swift standard library to see what can I do with `IntegerType`.
    
    
    /// A set of common requirements for Swift's integer types.
    public protocol IntegerType : _IntegerType, RandomAccessIndexType {
    }
    
    /// This protocol is an implementation detail of `IntegerType`; do
    /// not use it directly.
    public protocol _IntegerType : IntegerLiteralConvertible,
        CustomStringConvertible, Hashable, IntegerArithmeticType,
        BitwiseOperationsType, _Incrementable {
    }
    
    public protocol IntegerArithmeticType : _IntegerArithmeticType, Comparable {
        <snip>
        /// Explicitly convert to `IntMax`, trapping on overflow (except in
        /// -Ounchecked builds).
        @warn_unused_result
        public func toIntMax() -> IntMax
    }
    
    /// This protocol is an implementation detail of `IntegerArithmeticType`; do
    /// not use it directly.
    ///
    /// Its requirements are inherited by `IntegerArithmeticType` and thus must
    /// be satisfied by types conforming to that protocol.
    public protocol _IntegerArithmeticType {
        /// Multiply `lhs` and `rhs`, returning a result and a `Bool` that is
        /// true iff the operation caused an arithmetic overflow.
        public static func multiplyWithOverflow(lhs: Self, _ rhs: Self) -> (Self, overflow: Bool)
        <snip>
    }

`toIntMax()`? No way. `Int64` maximum value is `2^63 - 1`. `UInt64` maximum value is `2^63`. `toIntMax()` converts integer to `IntMax` (typealias for `Int64`). And `Int64` can't hold `2^63` = overflow = crash in case where `RawValue` of `OptionSetType` is `UInt64` and `2^63` is used as `rawValue`.
    
    
    let a: UInt64 = 9223372036854775808 // 2^63
    let b = a.toIntMax() // EXC_BAD_INSTRUCTION

`multiplyWithOverflow`? Left shift is multiplication by 2. Result type of this function is `(Self, overflow: Bool)`. Where `Self` is multiplication result and `overflow` indicates if overflow happened or not. Useful.
    
    
    func <<? <T: IntegerType>(lhs: T, var rhs: Int) -> T? {
        guard rhs != 0 else { return lhs }
        guard rhs > 0 else { return nil }
        
        var result = lhs
        var overflow: Bool
        while rhs-- > 0 {
            (result, overflow) = T.multiplyWithOverflow(result, 2)
            if overflow { return nil }
        }
        return result
    }

Safe left shift for `IntegerType` done and I can fix broken `BitValuesGenerator`.
    
    
    class BitValuesGenerator<Element : IntegerType> : AnyGenerator<Element> {
        var bitValue: Element? = 1
        
        override func next() -> Element? {
            guard let currentBitValue = bitValue else { return nil }
            bitValue = currentBitValue <<? 1
            return currentBitValue
        }
    }

## Random generator

Finally I can extend `OptionSetType` with `randomGenerator()` as well.
    
    
    extension OptionSetType where RawValue : IntegerType {
        func randomGenerator() -> AnyGenerator<Self> {
            var singleOptions = array
            return anyGenerator {
                guard singleOptions.count > 0 else { return nil }
                return singleOptions[Int(arc4random_uniform(UInt32(singleOptions.count)))]
            }
        }
    }

We have working generic random option generator for `IntegerType`.

![](http://www.robertvojta.com/public/images/swift-integers-playground.png)

## Conclusion

Go back to the Swift standard library and check `IntegerType` documentation again.
    
    
    /// A set of common requirements for Swift's integer types.
    public protocol IntegerType : _IntegerType, RandomAccessIndexType {
    
    /// This protocol is an implementation detail of `IntegerType`; do
    /// not use it directly.
    public protocol _IntegerType : IntegerLiteralConvertible,
    <snip>
    }

Useful functions are hidden in protocols with prefix `_`. And these protocols documentation says: _This protocol is an implementation detail of …; do not use it directly_. Bummer.

Another approach can be `&*`.
    
    
    /// multiply `lhs` and `rhs`, silently discarding any overflow.
    @warn_unused_result
    public func &*<T : _IntegerArithmeticType>(lhs: T, rhs: T) -> T

Updated `<<?` implementation.
    
    
    func <<? <T: IntegerType>(lhs: T, var rhs: Int) -> T? {
        guard rhs != 0 else { return lhs }
        guard rhs > 0 else { return nil }
        
        var result = (lhs, lhs) // (previous, current)
        while rhs-- > 0 {
            result = (result.1, result.1 &* 2)
            if result.1 < result.0 { return nil } // overflow
        }
        return result.1
    }

Probably safer way in terms of `_` protocols & implementation details. On the other side, all these functions are available (again _copy & paste_) on all integer types as well.
    
    
    extension Int {
        <snip>
        /// Multiply `lhs` and `rhs`, returning a result and a
        /// `Bool` that is true iff the operation caused an arithmetic
        /// overflow.
        public static func multiplyWithOverflow(lhs: Int, _ rhs: Int)
            -> (Int, overflow: Bool)
        /// Represent this number using Swift's widest native signed
        /// integer type.
        public func toIntMax() -> IntMax
    }

Maybe it's okay to use `_IntegerArithmeticType.multiplyWithOverflow`. Don't know, not 100% sure and don't have good feeling about it when working with `IntegerType`.

Anyway, you can find both implementations in [this gist](https://gist.github.com/robertvojta/723ea6e900c90b91ca3f). Choose whatever feels safer to you.

What I would like to see in Swift 3? Better generics support for integer types - more operators in standard library. I would like to work with `IntegerType` as with any other integer type like `Int8`, … Type safety is good, really good, but it makes things harder to do sometimes.
