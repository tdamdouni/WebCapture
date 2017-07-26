# Strings, characters, and performance in Swift — a deep dive

_Captured: 2017-01-08 at 22:15 from [medium.com](https://medium.com/@tonyallevato/strings-characters-and-performance-in-swift-a-deep-dive-b7b5bde58d53#.e375tjkh6)_

# Strings, characters, and performance in Swift -- a deep dive

## You might be writing extremely inefficient code without even realizing it.

_The content of this article applies to the current Swift version at the time of this writing (Swift 3.0.1). A future version of Swift could change some or all of the details discussed here._

A few weeks ago, I was running some benchmarks on a Swift project to which I contribute. A subset of our code base, which involves string scanning/parsing, was taking about _twelve seconds_ to parse approximately 150K of text. Something obviously didn't smell right. What follows is a deep dive into the internals of Swift strings that lead to an understanding of why the performance was so unsatisfactory and a solution that shaved it down to a fraction of a second without large-scale changes--with conclusions that you can adopt in your own code.

Before we jump in, let's define some Unicode terminology that will show up throughout this discussion:

  * **Code point:** the unique 21-bit numerical value assigned to a position in the Unicode code space. A code point can represent things like standalone characters (U+0065, Latin Small Letter E, "e"), glyphs that combine with the preceding character (U+0300, Combining Grave Accent, ◌̀), emoji (U+1F355, Slice of Pizza, 🍕), or control characters (U+000A, Line Feed), to name a few. Code points in the ranges U+0000…U+D7FF and U+E000…U+10FFFF are represented in Swift with the `UnicodeScalar` type.
  * **Surrogate code points:** Code points in the range U+D800…U+DFFF that are reserved for use by UTF-16 to encode code points that are larger than 16 bits. A pair consists of a "high surrogate" (U+D800…U+DBFF) followed by a "low surrogate" (U+DC00…U+DFFF).
  * **Code unit:** the sequence of bits that corresponds to a code point in a _specific_ encoding. UTF-8 uses 8-bit code units; UTF-16 uses 16-bit code units. A single code point may be represented by multiple code units; for example, the Greek lowercase letter phi (φ) is encoded in UTF-8 as the two-byte hex sequence <CF 86>. These are represented in Swift with types like `UTF8.CodeUnit` and `UTF16.CodeUnit` (which are just aliases for `UInt8` and `UInt16`, respectively).
  * **Extended grapheme cluster:** A sequence of code points that form a single human-readable character, such as "a" \+ ◌̀, which together form "a". Another example is the set of emoji that represent nations' flags--for example, the Italian flag (🇮🇹) is represented by a pair of code points: U+1F1EE (Regional Indicator Symbol Letter I) followed by U+1F1F9 (Regional Indicator Symbol Letter T). This concept is represented in Swift with the `Character` type.
  * **Canonical equivalence:** Two sequences of code points are considered canonically equivalent if they represent the same character. For example, code point U+00E0 (Latin Small Letter A with Grave, "a") is equivalent to the code point sequence <U+0061 U+0300> (Latin Small Letter A, "a"; Combining Grave Accent, ◌̀).

### Swift string views

Swift's `String` type provides four different ways to access the underlying data, called "views":

  * `characters`, a collection of extended grapheme clusters, represented by the type `String.CharacterView`
  * `unicodeScalars`, a collection of (non-surrogate) Unicode code points, represented by the type `String.UnicodeScalarView`
  * `utf8`, a collection of 8-bit unsigned integers representing the UTF-8 encoding of the string, represented by the type `String.UTF8View`
  * `utf16`, a collection of 16-bit unsigned integers representing the UTF-16 encoding of the string, represented by the type `String.UTF16View`

If you have experience with other programming languages, you've come to think of a string as a collection of characters, so `characters` feels like the natural view to use in most cases. It is arguably also biased by the fact that its name sounds the most "friendly" of all the string views.

"Character" is a bit of an overloaded term whose meaning differs depending on the programming language. For example, `char` in C/C++ is an 8-bit integer for which the language does not specify any encoding. Characters in Java and Objective-C (as returned by `String.charAt()` and `-[NSString characterAtIndex:]`, respectively) are actually UTF-16 code units.

In languages like those above, a single "human-readable character" may actually be represented by multiple values of its character type. This means that a word like "citta" could report having six characters if the last character is encoded as "a" \+ ◌̀, even though it looks like five characters to our eyes. Swift's `Character` type is designed to represent that "human-readable character" concept and would treat those final two code points as a single character, which also makes it more attractive to use.

Since `String.characters` is essentially the "obvious" way to work with elements of strings in Swift, let's spend some time designing an algorithm around it and see how it performs.

### Designing the tokenizer

We'll recreate a similar problem to the one I faced. Imagine that we have some textual data about U.S. states, their populations, and capital cities:
    
    
    "California", 39250017, "Sacramento"; "Texas", 27862596, "Austin"; "Florida", 20612439, "Tallahassee"; "New York", 19745289, "Albany"; "Illinois", 12801539, "Springfield"; (...and so on)

The data is made up of the following tokens:

  * **Strings,** which start with double quotes and include everything up until the next double quote. (To keep this example simple, we don't allow escaped characters like `\n`or `\"`.)
  * **Integers,** which are sequences of one or more digits 0-9.
  * The **comma** and the **semicolon.**
  * Whitespace between tokens is allowed and ignored. (We'll only worry about space, newline, carriage return, and tab.)

(If you're looking at the data format above and wonder why I'm not just calling `String.components(separatedBy:)`, bear with me--it's a contrived example. There are a couple reasons we might not want to do that here: it wouldn't work if we allow commas and semicolons inside the quoted strings, or we might just want to scan the input string no more than once.)

Given the description above, we want to write a **tokenizer** that will return each component one-by-one, like so:
    
    
    string("California")  
    comma  
    integer(39250017)  
    comma  
    string("Sacramento")  
    semicolon  
    (...and so on)

Since the focus of this article is on performance rather than writing a lexical analyzer, I won't belabor the details of specific components like the token and error types. The entire project can be [viewed on Github](https://github.com/allevato/swift-performance-strings).

### Character-based scanning

Tokenizing the input string means scanning it element-by-element and returning meaningful tokens based on what we see. So, the natural thing that probably comes to mind is to use an iterator over the string's `characters` to build up those tokens. A snippet of the character-based tokenizer is shown below (the full source, with comments, can be seen [here](https://github.com/allevato/swift-performance-strings/blob/master/Tokenizing/CharacterBasedTokenizer.swift)):

struct CharacterBasedTokenizer: Tokenizing {

private var iterator: String.CharacterView.Iterator

init(text: String) {

iterator = text.characters.makeIterator()

}

mutating func nextToken() throws -> Token? {

while let ch = nextCharacter() {

switch ch {

case " ", "\n", "\r", "\t":

continue

case ",":

return .comma

case ";":

return .semicolon

case "0"..."9":

return try integerToken(startingWith: ch)

case "\"":

return try stringToken()

default:

throw TokenizingError.unrecognizedCharacter

}

}

return nil

}

}
[view raw](https://gist.github.com/allevato/6f8d13cc31ff9b97e04e3a06dd52d54c/raw/c4f6a1bc05406a7c52abf00694ab0eaae0caed40/CharacterBasedTokenizer_2.swift) [CharacterBasedTokenizer_2.swift](https://gist.github.com/allevato/6f8d13cc31ff9b97e04e3a06dd52d54c#file-characterbasedtokenizer_2-swift) hosted with ❤ by [GitHub](https://github.com)

(The `nextCharacter` method is a helper function that calls `iterator.next()` but also handles a "push-back" case needed when scanning the end of an integer. The `integerToken` and `stringToken` methods scan those tokens specifically and have been factored out to keep the main loop small.)

Notice that our `case` patterns use string literals. This is an important feature of Swift; unlike languages in the C family that distinguish character literals with single quotes, the Swift compiler allows a string literal containing a single extended grapheme cluster to be treated as if it were a `Character`, based on context.

Let's measure execution time. The benchmark is set up to fully tokenize our state population/capital data 1,000 times, and the measurement is repeated five times to smooth out noise. (It's also executed a couple times without measuring it first, to "prime" the benchmark and ensure that the first measured run isn't artificially longer because of static data that is lazily loaded.)

My sample data is 1,694 characters long. Scanning that 1,000 times gave me these results:
    
    
    CharacterBasedTokenizer:  
    ..... 2164.5144464 ms ± 6.15726058362173 ms (mean ± SD)

_Over two seconds_ to make one pass over 1.6 MB of text on modern hardware? That can't be right.

### Instruments to the rescue

To figure out exactly where the tokenizer is spending all of that time, we can run the Time Profiler template in Instruments. If we do this and then focus on the `CharacterBasedTokenizer.nextToken` method, we see something shocking:

![](https://cdn-images-1.medium.com/max/2000/1*6dB7zKiV2q_RKtLmBLWpuQ.png)

> _The statistics printed in the previous section are just the mean execution time. So 15.71 seconds for two priming runs and five measured runs is just about right._

A full _two-thirds_ of the time taken to scan tokens is spent in an initializer for the `Character` type. What is going on?

The first argument label of the initializer gives a small hint: `_builtinExtendedGraphemeClusterLiteral`. Note the word "literal." This initializer isn't used to extract `Character` values from the string I'm iterating over; it's used to create `Character` values from literal text elsewhere in the source code. The only place where those are found beneath `nextToken` is in my tokenizer's `switch/case` patterns. Are they really causing that much overhead?

We can have the Swift compiler emit the "canonical SIL" (Swift Intermediate Language) using the `-emit-sil` option to take a closer look at how those `case` patterns are being compiled to lower-level code. (I've included a [small script](https://github.com/allevato/swift-performance-strings/blob/master/emit_sil.sh) in the repository that does this and also demangles the Swift symbols.) Let's find the SIL corresponding to the `case` pattern where we match the comma character (reformatted with line numbers and scopes omitted for brevity):
    
    
    %448 = string_literal utf8 ","  
    %449 = apply %26(%448, %23, %24, %25) :  
     $@convention(method) **(Builtin.RawPointer, Builtin.Word,  
     Builtin.Int1, @thin Character.Type) -> @owned Character**

The method signature shown on the second and third lines of `%449` gives it away, but we can confirm it by looking back up at value `%26`, which is the function being invoked:
    
    
    %26 = function_ref **@Swift.Character.init (  
     _builtinExtendedGraphemeClusterLiteral : Builtin.RawPointer,  
     utf8CodeUnitCount : Builtin.Word,  
     isASCII : Builtin.Int1) -> Swift.Character** :  
     $@convention(method) (Builtin.RawPointer, Builtin.Word,  
     Builtin.Int1, @thin Character.Type) -> @owned Character

#### What does this all mean?

It means that _every_ time through the scanning loop (that is, for _every_ character in the string), Swift is invoking this initializer to create _each_ character in the `case` patterns that is compares the current character against until a match is found--and that initializer is significantly more expensive than you might expect if you're used to languages where the character type is really just a numeric code unit.

By looking at the Swift standard library source, we can see the sequence of actions that occurs when a string literal like `","` is converted to a `Character`:

  1. The compiler embeds the UTF-8 encoded representation of the literal in the executable's data segment.
  2. At the point where the literal is used, Swift invokes `Character.init(_builtinExtendedGraphemeClusterLiteral:utf8CodeUnitCount:isASCII)`, passing it the address of the string data embedded in step 1 ([source](https://github.com/apple/swift/blob/797b807/stdlib/public/core/Character.swift#L123)).
  3. This initializer, in turn, invokes the same initializer on `String`. Eventually, a `StringBuffer` is allocated ([source](https://github.com/apple/swift/blob/797b807/stdlib/public/core/StringBuffer.swift#L94)).
  4. Finally, the `String` is converted into back into a `Character` value ([source](https://github.com/apple/swift/blob/797b807/stdlib/public/core/Character.swift#L161)). Depending on the size of its UTF-8 representation (remember that a single "character" can contain multiple code units), it will either be stored compactly as an integer no larger than 63 bits, or the entire string buffer will be retained ([source](https://github.com/apple/swift/blob/797b807/stdlib/public/core/Character.swift#L67-L81)).

In other words, just to ask the question "does `ch == ","`?" we end up allocating a string in memory that we don't even need, because `","` easily fits within eight bits, let alone 63.

#### Why is this so complicated?

It's the price we pay for Unicode correctness and for having a character model that corresponds to what users _see_ rather than the string's internal representation. It is both powerful and convenient to be able to take a string like "citta" and know that it is five _characters_ long, regardless of whether it is five or six _code points_ long ("citt" \+ "a" vs. "citt" \+ "a" \+ combining grave accent). Likewise, it is desirable to be able to compare those strings and determine that they are canonically equivalent even when their internal representations differ.

#### Could the compiler do a better job here?

Possibly. In contexts where a string literal is being converted to a `Character`, I would imagine that with a bit more work the compiler could determine that the value would fit in the compact representation and emit that code directly, bypassing the string-to-character dance described above.

### You don't have to live with execution times like this.

Let's talk about things you can do to improve your run-time that don't depend on changes to the compiler.

First, if the majority of the tokenizer's time is spent initializing the `Character` values being matched against, what if we preinitialized them ourselves?

private let space: Character = " "

private let newLine: Character = "\n"

private let carriageReturn: Character = "\r"

private let tab: Character = "\t"

private let comma: Character = ","

private let semicolon: Character = ";"

private let zero: Character = "0"

private let nine: Character = "9"

private let quote: Character = "\""

struct CharacterBasedTokenizer: Tokenizing {

private var iterator: String.CharacterView.Iterator

init(text: String) {

iterator = text.characters.makeIterator()

}

mutating func nextToken() throws -> Token? {

while let ch = nextCharacter() {

switch ch {

case space, newLine, carriageReturn, tab:

continue

case comma:

return .comma

case semicolon:

return .semicolon

case zero...nine:

return try integerToken(startingWith: ch)

case quote:

return try stringToken()

default:

throw TokenizingError.unrecognizedCharacter

}

}

return nil

}

}
[view raw](https://gist.github.com/allevato/d6f80f82edf5c4e85bb9439b3aab92ed/raw/7664ccdf7fb200073d1e0840745ee123262a290e/CharacterBasedTokenizer_3.swift) [CharacterBasedTokenizer_3.swift](https://gist.github.com/allevato/d6f80f82edf5c4e85bb9439b3aab92ed#file-characterbasedtokenizer_3-swift) hosted with ❤ by [GitHub](https://github.com)

After this change alone, the new execution time is about one-third of what it was before:
    
    
    CharacterBasedTokenizer:  
    ..... 686.6116408 ms ± 14.3905875334629 ms (mean ± SD)

Looking at the time profile again, we can see that most of the time now is spent in the `CharacterView`'s iterator:

![](https://cdn-images-1.medium.com/max/1000/1*O_RaXdQo-3Tw2xYJyr1jDA.png)

`CharacterView` inherits the default `IndexingIterator` from `Collection`, so each call to `next` does the following:

  1. Uses `subscript` to get the current character, which constructs a new `String` from a slice of the buffer and then a `Character` from that ([source](https://github.com/apple/swift/blob/797b80765f5e5a7a0b4ad079dbd7bf9ae279be32/stdlib/public/core/StringCharacterView.swift#L347)).
  2. Advances its index to the next character, which is a relatively complex algorithm in order to achieve Unicode correctness ([source](https://github.com/apple/swift/blob/797b80765f5e5a7a0b4ad079dbd7bf9ae279be32/stdlib/public/core/StringCharacterView.swift#L255)).

This is still a lot of overhead--and pulling the characters being matched into separate variables is a pretty big sacrifice to code readability that we shouldn't have to make. The set of characters we need to recognize in this example is fairly small, but a tokenizer for a more complex language could have many more. Can we do better?

### Do you need characters at all? If not, use something else.

The power of `Character` is that it treats code point sequences as a single "human-perceived character" and that it cleanly handles canonical equivalence, but it is _not_ the natural representation of string elements.

Swift `String` values contain an instance of the `_StringCore` type, which is optimized to store either ASCII or UTF-16 encoded text. When Swift gives you a `CharacterView`, it needs to transform that underlying representation into `Character` values. Even though it does this lazily as you traverse the collection, if you iterate over the entire string, `CharacterView` is doing a lot of memory allocations and complex calculations to give you those values.

So, if your use case doesn't need the advanced capabilities that `Character` provides--our scanner doesn't--then you'll get much better performance by using something closer to the string's internal representation. We still have three string views to consider: `UTF8View`, `UTF16View`, and `UnicodeScalarView`.

#### Digging into string internals

Let's start by taking a closer look at `_StringCore`. First, notice the leading underscore: this is one of those types that was made public as an implementation detail, but which we shouldn't touch in our code. The Swift team can--and likely will--change it in ways that would break us if we accessed it directly. That said, it's beneficial to understand how it works and affects performance. We won't use `_StringCore` directly in any code that we write, but we'll explore its implementation so that we can make informed decisions about how to make our scanner more efficient.

As I mentioned above, `_StringCore` is optimized to handle both ASCII and UTF-16 encoded text--it does so by using some clever bit-twiddling and arithmetic tricks. An instance variable stores a pointer to the underlying bytes that make up the string content. Another instance variable keeps track of the count of ASCII or UTF-16 code units in the string, but the most significant bit of this count is special. `_StringCore` calls it `elementShift`: if it equals 0, the buffer contains ASCII data; if it equals 1, the buffer contains UTF-16 data. In other words, adding 1 to the value of this bit gives us the number of bytes that we need to advance to get from one code unit to the next: 1 for ASCII and 2 for UTF-16. `_StringCore` also ensures that internal consistency is maintained during other string operations; for example, if you append a string with UTF-16 data to one with ASCII data, the ASCII data will be widened to UTF-16.

Since `_StringCore` can store both kinds of text, how does it know which one to use for a given string? The compiler examines string literals and detects whether it contains only 7-bit ASCII (code units in the range 0 to 127) or if it contains Unicode, and it uses different initializers to create the `String` values. Let's consider these two strings:
    
    
    let s1 = "foo"  
    let s2 = "föö"

The first can be represented in 7-bit ASCII, while the second cannot. If we compile this and examine the SIL, we see that slightly different code is generated:
    
    
    %13 = string_literal **utf8 "foo"**  
    %14 = integer_literal $Builtin.Word, 3  
    %15 = integer_literal $Builtin.Int1, -1  
    %16 = metatype $@thin String.Type  
    %17 = function_ref **@Swift.String.init (  
     _builtinStringLiteral : Builtin.RawPointer,  
     utf8CodeUnitCount : Builtin.Word,  
     isASCII : Builtin.Int1) -> Swift.String** :  
     $@convention(method) (Builtin.RawPointer, Builtin.Word,  
     Builtin.Int1, @thin String.Type) -> @owned String  
    %18 = apply %17(%13, %14, %15, %16) :  
     $@convention(method) (Builtin.RawPointer, Builtin.Word,  
     Builtin.Int1, @thin String.Type) -> @owned String
    
    
    %22 = string_literal **utf16 "föö"**  
    %23 = integer_literal $Builtin.Word, 3  
    %24 = integer_literal $Builtin.Int1, 0  
    %25 = metatype $@thin String.Type  
    %26 = function_ref **@Swift.String.init (  
     _builtinUTF16StringLiteral : Builtin.RawPointer,  
     utf16CodeUnitCount : Builtin.Word) -> Swift.String** :  
     $@convention(method) (Builtin.RawPointer, Builtin.Word,  
     @thin String.Type) -> @owned String  
    %27 = apply %26(%22, %23, %25) :  
     $@convention(method) (Builtin.RawPointer, Builtin.Word,  
     @thin String.Type) -> @owned String

The `String` initializers in `%17` and `%26` call `_StringCore.init` with the appropriate value for `elementShift` to indicate whether the string is ASCII or UTF-16 ([source](https://github.com/apple/swift/blob/2fe4254cb712fa101a220f95b6ade8f99f43dc74/stdlib/public/core/String.swift#L394-L435)).

Armed with this knowledge, we might guess that either the `UTF8View` or the `UTF16View` would be quite fast, depending on what kind of string we have. That last part is tricky, though: there's no fast way to determine whether we have an ASCII string or a UTF-16 one. It's an implementation detail of `_StringCore` and not exposed by the public API (nor should it be). Even if we did know, how would we use that information? Would we write two separate scanners--one for ASCII text and one for UTF-16? That's not a realistic approach, either.

Instead of jumping right into the details of how `UTF8View` and `UTF16View` are implemented, first let's consider the four possible cases and use our intuition to hypothesize about how efficient they might be:

  1. A `String` with ASCII data accessed through `UTF8View`: Since ASCII is a subset of UTF-8, the data matches the way we're viewing it, so this should be fast.
  2. A `String` with UTF-16 data accessed through `UTF8View`: The UTF-16 data has to be transcoded to UTF-8 and the iterator must maintain state about where it currently sits _within_ a character's UTF-8 code units, so the computational overhead would make this somewhat slower.
  3. A `String` with ASCII data accessed through `UTF16View`: ASCII characters can be cheaply widened to 16 bit integers that are valid UTF-16 code units, so this should be fairly fast.
  4. A `String` with UTF-16 data accessed through `UTF16View`: The data matches the way we're viewing it, so this should be fast.

Since there's a case where we believe `UTF8View` will perform poorly, we'll set it aside. On the other hand, `UTF16View` looks promising, so let's try converting our tokenizer to one that uses it. We can start by switching from `String.characters` to `String.utf16` and updating uses of `Character` to `UTF16.CodeUnit`. A snippet is shown below:

struct UTF16BasedTokenizer: Tokenizing {

private var iterator: String.UTF16View.Iterator

init(text: String) {

iterator = text.utf16.makeIterator()

}

mutating func nextToken() throws -> Token? {

while let ch = nextCodeUnit() {

switch ch {

case " ", "\n", "\r", "\t":

continue

case ",":

return .comma

case ";":

return .semicolon

case "0"..."9":

return try integerToken(startingWith: ch)

case "\"":

return try stringToken()

default:

throw TokenizingError.unrecognizedCharacter

}

}

return nil

}

}
[view raw](https://gist.github.com/allevato/ac0bc2e3a82fe40905220f7809c18fc8/raw/c85616dd61d8d32af3c0b47f9ed7d8f604db1879/UTF16BasedTokenizer.swift) [UTF16BasedTokenizer.swift](https://gist.github.com/allevato/ac0bc2e3a82fe40905220f7809c18fc8#file-utf16basedtokenizer-swift) hosted with ❤ by [GitHub](https://github.com)

There's just one problem--this won't compile yet. There are two big issues:

  1. Unlike with`Character`, Swift does not let single-character string literals be used as UTF-16 code units. We would have to replace the literals in our `case` patterns with their raw numeric UTF-16 values, which isn't readable or easily maintainable.
  2. In the `integerToken` and `stringToken` methods, we collect the token text by appending each character to a new string. There is no overload of `String.append` that can take a UTF-16 code unit, `UTF16View` is not mutable, and converting a single UTF-16 code unit to a `String` which could be appended is not always feasible (for example, if it is part of a surrogate pair). We would have to use an alternate approach, like collecting the UTF-16 code units in an array and then decoding that into a `String` after the fact.

In other words, to use `UTF16View`, the code we would have to write would be fairly low-level compared to what we originally had. Swift is not a low-level language and we shouldn't have to make that sacrifice. Let's reject this approach.

### Help me, UnicodeScalarView--you're my only hope.

With all this in mind, the only option left is `UnicodeScalarView`. Either I've saved the best for last, or this article is going to have a very disappointing ending. Let's look at what `UnicodeScalarView` and its element type `UnicodeScalar` are capable of.

First, `UnicodeScalar` conforms to `ExpressibleByUnicodeScalarLiteral`, so the compiler will let us create a `UnicodeScalar` using a string literal that contains a single scalar. In other words, we can still write `case ","` and have our code be readable.

In addition to the readability benefit, initializing a `UnicodeScalar` from a string literal is _fast._ `UnicodeScalar` is a wrapper around a 32-bit unsigned integer, and there are no string buffer allocations involved like we saw with `Character`. Let's look at the generated SIL for a simple assignment:
    
    
    **// let scalar: UnicodeScalar = "ö"**
    
    
    %12 = global_addr @StringTest.scalar : Swift.UnicodeScalar :  
     $*UnicodeScalar  
    %13 = integer_literal $Builtin.Int32, **246**  
    %14 = struct $UInt32 (%13 : $Builtin.Int32)  
    %15 = struct $UnicodeScalar (%14 : $UInt32)  
    store %15 to %12 : $*UnicodeScalar

The compiler has already extracted the scalar from the string (246 is the decimal Unicode code point for "Latin Small Letter O with Diaeresis"), and the remaining instructions are simple value type conversions. The resulting machine code will be nothing more than an instruction that loads the number 246 into a register or memory address.

Next, we can't append `UnicodeScalar` directly to a `String`, but unlike `UTF8View` and `UTF16View`, `UnicodeScalarView` is mutable and the `append(UnicodeScalar)` operation can be found there. This makes the implementation of the `integerToken` and `stringToken` methods work as they did before with only minor modifications.

Finally, iterating over the `UnicodeScalarView` is very fast as well. The iterator delegates most of its behavior to the `UTF16` codec type, which decodes the underlying ASCII or UTF-16 code units in the string buffer and produces `UnicodeScalar` values. The `decode` method can be seen [here](https://github.com/apple/swift/blob/2fe4254cb712fa101a220f95b6ade8f99f43dc74/stdlib/public/core/Unicode.swift#L495) and is fairly straightforward. The vast majority (96.875%) of UTF-16 code units are numerically equivalent to their Unicode scalar (those in the range 0x0000-0xD7FF or 0xE000-0xFFFF). The remaining ones are the surrogate code units, and well-formed UTF-16 surrogate pairs consist of one high surrogate followed immediately by one low surrogate. The decoder never has to look more than one position ahead to convert any UTF-16 code unit or surrogate pair into a `UnicodeScalar`, and the conversion is simple bitwise arithmetic that does not require any additional memory to be allocated.

A downside is that if we switch to `UnicodeScalar`, each element we process no longer necessarily corresponds to a single human-recognizable character and we lose the ability to easily check for canonical equivalence. Fortunately, this does not affect our tokenizer. The basic tokens we recognize, like comma and semicolon, are simple ASCII characters. The only location where Unicode characters might appear is inside double quoted strings, and those scalars will simply be appended to another string that we get back in the returned token.

All of this seems promising, so let's test it out by creating a `UnicodeScalarBasedTokenizer`. The conversion from `CharacterBasedTokenizer` is very simple ([view source](https://github.com/allevato/swift-performance-strings/blob/master/Tokenizing/UnicodeScalarBasedTokenizer.swift)). Running the benchmark:
    
    
    UnicodeScalarBasedTokenizer:  
    ..... 108.4403786 ms ± 2.50400540742841 ms (mean ± SD)

That's a _significant_ improvement--50 times faster than the version that used `CharacterView`, with only minor changes.

### Summary

Swift's `String` type is a powerful abstraction that provides access to different encodings through a set of "views." In particular, `CharacterView` and the `Character` type provide a clean and convenient API that solves a long-standing problem with text processing--identifying clusters of code points that form a single human-recognizable character and determining canonical equality without having to roll your own algorithms to handle low-level Unicode details.

This power comes with a computational cost, however. As they are currently implemented, `Character` values involve time-consuming heap allocations that aren't immediately obvious to callers--especially for `Character` literals. Although these allocations are often short-lived, the recurring allocate-and-free churn can significantly drag down the performance of string processing in tight loops.

Since `String.characters` is the "obvious" way to access a string's elements, it's easy to write code that performs sub-optimally when you don't need to take advantage of those features.

To improve the efficiency of your code when you don't need the features that `Character` provides, use `String.unicodeScalars` instead. `UnicodeScalarView` is a happy medium between the very high-level `CharacterView` and the low-level `UTF8View` and `UTF16View`, and as we've seen above, very minor changes to your code can yield _significant_ performance gains.
