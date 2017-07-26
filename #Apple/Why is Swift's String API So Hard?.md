# Friday Q&A 2015-11-06: Why is Swift's String API So Hard?

_Captured: 2015-11-10 at 21:33 from [www.mikeash.com](https://www.mikeash.com/pyblog/friday-qa-2015-11-06-why-is-swifts-string-api-so-hard.html)_

Welcome to a very delayed edition of Friday Q&A. One of the biggest complaints I see from people using Swift is the `String` API. It's difficult and obtuse, and people often wish it were more like string APIs in other languages. Today, I'm going to explain just why Swift's `String` API is designed the way it is (or at least, why I think it is) and why I ultimately think it's the best string API out there in terms of its fundamental design.

**What is a String?**  
Let's build a conceptual foundation before we jump into it. Strings are one of those things we understand implicitly but often don't really think about too deeply. Thinking about them deeply helps understand what's going on.

What _is_ a string, conceptually? The high level view is that a string is some text. `"Hello, World"` is a string, as is `"/Users/mikeash"` and `"Robert'); DROP TABLE Students;--"`.

(Incidentally, I think that representing all these different concepts as a single string type is a mistake. Human-readable text, file paths, SQL statements, and others are all conceptually different, and this should be represented as different types at the language level. I think that having different conceptual kinds of strings be distinct types would eliminate a lot of bugs. I'm not aware of any language or standard library that does this, though.)

How is this general concept of "text" represented at the machine level? Well, it depends. There are a ton of different ways to do it.

In many languages, a string is an array of bytes. Giving meaning to those bytes is mostly left up to the program. This is the state of strings in C++ using `std::string`, in Python 2, in Go, and in many other languages.

C is a weird special case of this. In C, a string is a pointer to a sequence of non-zero bytes, terminated by a zero byte. The basic effect is the same, but C strings can't contain zero bytes, and operations like finding the length of a string require scanning memory.

A lot of newer languages define strings as a sequence of UCS-2 or UTF-16 code units. Java, C#, and JavaScript are all examples of this, as well as Objective-C using Cocoa and `NSString`. This is mostly a historical accident. When Unicode was first introduced in 1991, it was a pure 16-bit system. Several popular languages were designed around that time, and they used Unicode as the basis of their strings. By the time Unicode broke out of the 16-bit model in 1996, it was too late to change how these languages worked. The UTF-16 encoding allows them to encode the larger numbers as pairs of 16-bit code units, and the basic concept of a string as a sequence of 16-bit code units continues.

A variant of this approach is to define a string as a sequence of UTF-8 code units, which are 8-bit quantities. This is overall similar to the UTF-16 approach, but allows for a more compact representation for ASCII strings, and avoids conversion when passing strings to functions that expects C-style strings, as those often accept UTF-8 strings.

Some languages represent strings as a sequence of Unicode code points. Python 3 works this way, as do many C implementations of the built-in `wchar_t` type.

In short, a string is usually considered to be a sequence of some kind of _characters_, where a character is typically a byte, a UTF-16 code unit, or a Unicode code point.

**Problems**  
Having a string be a sequence of some "character" type is convenient. You can typically treat them like arrays (often they _are_ arrays) which makes it easy to grab subranges, slice pieces off the beginning or end, delete portions, count elements, etc.

The trouble is that we live in a Unicode universe, and Unicode makes things hard. Let's look at an example string and see how it works out:

Each Unicode code point has a number (written as U+nnnn) and a human-readable name (written in ALL CAPS for some reason) which make it easier to talk about the individual code points. This particular string consists of:

  * U+0061 LATIN SMALL LETTER A
  * U+0065 LATIN SMALL LETTER E
  * U+00B4 ACUTE ACCENT
  * U+221E INFINITY
  * U+1D11E MUSICAL SYMBOL G CLEF

Let's remove a "character" from the middle of this string, treating a "character" as a UTF-8 byte, a UTF-16 code unit, or a Unicode code point.

Let's start with UTF-8. Here's what this string looks like as UTF-8:

Let's remove the 3rd "character," which we're treating as the 3rd byte. That produces:

This string is no longer valid UTF-8. UTF-8 bytes fall into three categories. Bytes of the form `0xxxxxxx` with the top bit set to 0 represent plain ASCII characters and stand alone. Bytes of the form `11xxxxxx` denote the start of a multi-byte sequence whose length is indicated by the location of the first zero bit. Bytes of the form `10xxxxxx` denote the remainder of a multi-byte sequence. The byte `cc` formed the start of a multi-byte sequence a total of two bytes long, and the byte `81` was the trailing byte of that sequence. By removing `cc`, the trailing byte `81` is left standing alone. Any validating UTF-8 reader will reject this string. This same problem will occur when removing any of the bytes from the third place onward in this string.

How about the second byte? If we remove that, we get:

This is still valid UTF-8, but the result is not what we might expect:

To a human, the "second character" of this string is "e." But the second byte is just the "e" without the accent mark. The accent mark is added separately as a "combining character." Removing the second byte of the string just removes the "e" which causes the combining accent mark to attach to the "a" instead.

What if we remove the very first byte? This result, at least, is what we'd expect:

Let's take a look at UTF-16 now. Here's what the string looks like as UTF-16:

Let's try removing the second "character":

This has the same problem as we had above with UTF-8, deleting only the "e" but not the accent mark, causing it to attach to the "a" instead.

What if we delete the 5th character? We get this sequence:

Similar to the problem we had with invalid UTF-8 above, this sequence is no longer valid UTF-16. The sequence `d834 dd1e` forms a _surrogate pair_, where two 16-bit units are used to represent a code point beyond the 16-bit limit. Leaving a single piece of the surrogate pair standing alone is invalid. Code that deals with UTF-8 usually rejects this sort of thing outright, but UTF-16 is often more forgiving. For example, Cocoa renders the resulting string as:

What if the string is a sequence of unicode code points? It would look like this:

With this representation, we can remove any "character" without producing an invalid string. But the problem with the combining accent mark _still_ occurs. Removing the second character produces:

Even with this representation, we're not safe from unintuitive results.

These are hardly artifical concerns, too. English is one of the few languages you can write with pure ASCII, and even then you'll have trouble, unless you feel like applying for a job with your "resume" instead of your resume. The moment you step beyond ASCII, all these weird things start to appear.

**Grapheme Clusters**  
Unicode has the concept of a _grapheme cluster_, which is essentially the smallest unit that a human reader would consider to be a "character." For many code points, a grapheme cluster is synonymous with a single code point, but it also extends to include things like combining accent marks. If we break the example string into grapheme clusters, we get something fairly sensible:

If you remove any single grapheme cluster, you get something that a human would generally consider to be reasonable.

Note that I didn't include any numeric equivalents in this example. That's because, unlike UTF-8, UTF-16, or plain unicode code points, there is no single number that can describe a grapheme cluster in the general case. A grapheme cluster is a _sequence_ of one or more code points. A single grapheme cluster is often one or two code points, but it can be a _lot_ of code points in the case of something like [Zalgo](http://www.eeemo.net). For example, consider this string:

This mess consists of 14 separate code points:

  * U+0065
  * U+20DD
  * U+20DE
  * U+20DF
  * U+20E0
  * U+20E3
  * U+20E4
  * U+20E5
  * U+20E6
  * U+20E7
  * U+20EA
  * U+A670
  * U+A672
  * U+A671

All of these code points form a single grapheme cluster.

Here's an interesting example. Consider a string containing the Swiss flag:

This one symbol is actually two code points: `U+1F1E8 U+1F1ED`. What are these code points?

  * U+1F1E8 REGIONAL INDICATOR SYMBOL LETTER C
  * U+1F1ED REGIONAL INDICATOR SYMBOL LETTER H

Rather than include a separate code point for the flag of every country on the planet, Unicode just includes 26 "regional indicator symbols." Add together the indicator for C and the indicator for H and you get the Swiss flag. Combine M and X and you get the Mexican flag. Each flag is a single grapheme cluster, but two code points, four UTF-16 code units, and eight UTF-8 bytes.

**Implications For Implementations**  
We've seen that there are a lot of different ways to look at strings, and a lot of different things you can call a "character." A "character" as a grapheme cluster comes closest to what a human thinks of as a "character," but when manipulating a string in code, which definition you want to use will depend on the context. When moving an insertion point in text in response to an arrow key, you probably want to go by grapheme clusters. When measuring a string to ensure that it fits in a 140-character tweet, you want to go by unicode code points. When squeezing a string into an 80-character database table column, you're probably dealing in UTF-8 bytes.

How do you reconcile these when writing a string implementation, and balancing the conflicting requirements of performance, memory consumption, and clean code?

The typical answer is to pick a single canonical representation, then possibly allow conversions for the cases where other representations are needed. For example, `NSString` uses UTF-16 as its canonical representation. The entire API is built around UTF-16. If you want to deal with UTF-8 or Unicode code points, you can convert to UTF-8 or UTF-32 and then manipulate the result. Those are provided as data objects rather than strings, so it's not as convenient. If you want to deal with grapheme clusters, you can find their boundaries using `rangeOfComposedCharacterSequencesForRange:`, but it's a lot of work to do anything interesting.

Swift's `String` type takes a different approach. It has no canonical representation, and instead provides _views_ on various representations of the string. This lets you use whichever representation makes the most sense for the task at hand.

**Swift's String API, In Brief**  
In older versions of Swift, `String` conformed to `CollectionType` and presented itself as a collection of `Character`. As of Swift 2, this is no longer the case, and `String` mostly presents the various views as the proper way to access it.

This is not entirely the case, though, and `String` still somewhat favors `Character` and presents a bit of a collection-like interface:

You can index into a `String` to get individual `Character`s, but that's about it. Notably, you can't iterate using the standard `for in` syntax.

What is a "character" in Swift's eyes? As we've seen, there are a lot of possibilities. Swift has settled on the grapheme cluster as its idea of a "character." This seems like a good choice, since as we saw above it best matches our human idea of a "character" in a string.

The various views are exposed as properties on `String`. For example, here's the `characters` property:

`CharacterView` is a collection of `Character`s:

This looks a lot like the interface of `String` itself, except it conforms to `CollectionType` and so gets all of the functionality that provides, like slicing and iteration and mapping and counting. So while this is not allowed:

This works fine:

You can get a string back out of a `CharacterView` by using an initializer:

You can even get a String from an arbitrary sequence of `Character`s:

Working our way down the hierarchy, the next view is the UTF-32 view. Swift calls UTF-32 code units "unicode scalars," since UTF-32 code units correspond exactly to Unicode code points. Here's what the (abbreviated) interface looks like:

Like `CharacterView`, there's a `String` initializer for `UnicodeScalarView`:

Unfortunately, there's no initializer for an arbitrary sequence of `UnicodeScalar`s, so you have to do a little extra work if you prefer to manipulate, for example, an array of them and then turn them back into a string. There isn't even an initializer for `UnicodeScalarView` that takes an arbitrary sequence of `UnicodeScalar`s. There is, however, a mutable append function, so you can build a `String` in three steps:

Next is the UTF-16 view. It looks much like the others:

The `String` initializer for this view is slightly different:

Unlike the others, this is a failable initializer. Any sequence of `Character`s or `UnicodeScalar`s is a valid `String`, but it's possible to have a sequence of UTF-16 code units that don't form a valid string. This initializer will produce `nil` if the view's contents aren't valid.

Going from an arbitrary sequence of UTF-16 code units back to a `String` is pretty obscure. `UTF16View` has no public initializers and few mutating functions. The solution is to use the global `transcode` function, which works with the `UnicodeCodecType` protocol. There are three implementations of this protocol: `UTF8`, `UTF16`, and `UTF32`. The `transcode` function can be used to convert between them. It's pretty gnarly, though. For the input, it takes a `GeneratorType` which produces the input, and for the output it takes a function which is called for each unit of output. This can be used to build up a string piece by piece by converting to `UTF32`, then converting each `UTF-32` code unit to a `UnicodeScalar` and appending it to a `String`:

Finally, there's the UTF-8 view. It's what we'd expect from what we've seen so far:

There's an initializer for going the other way. Like with `UTF16View`, the initializer is failable, since a sequence of UTF-8 code units may not be valid:

Like before, there's no convenient way to turn an arbitrary sequence of UTF-8 code units into a `String`. The transcode function can be used here too:

Since these `transcode` calls are pretty painful, I wrapped them up in a pair of nice failable initializers:

Now we can create `Strings` from arbitrary sequences of UTF-16 or UTF-8:

**Indexes**  
The various views are all indexable collections, but they are very much _not_ arrays. The index types are weird custom `struct`s. This means you can't index views by number:

Instead, you have to start with either the collection's `startIndex` or `endIndex`, then use methods like `successor()` or `advancedBy()` to move around:

This is not fun. What's going on?

Recall that these are all views on the same underlying data, which is stored in some canonical form within the string object. When you use a view which doesn't match that canonical form, the data has to be converted when accessed.

Recall from above that these various encodings have different sizes and lengths. That means that there's no straightforward way to map a location in one view to a location in another view, because the mapping depends on the underlying data. Consider this string for example:

Imagine the canonical representation within `String` is UTF-32. That representation will be an array of 32-bit integers:

Now imagine we get the UTF-8 view of this data. Conceptually, that data is a sequence of 8-bit integers:

Here's how this sequence maps back to the original UTF-32:

If I ask the UTF-8 view for the value at index `6`, it has to scan the UTF-32 array starting from the beginning to figure out where that value is and what it contains.

Obviously, this can be done. Swift provides the necessary functionality, it's just not pretty: `string.utf8[string.utf8.startIndex.advancedBy(6)]`. Why not make it easier, and allow indexing with an integer? It's essentially Swift's way of reinforcing the fact that this is an expensive operation. In a world where `UTF8View` provided `subscript(Int)`, we'd expect these two pieces of code to be pretty much equivalent:

They would work the same, but the second one would be drastically slower. The first loop is a nice linear scan, whereas the second loop has to do a linear scan on each iteration, giving the whole loop a quadratic runtime. It's the difference between scanning a million-character string in a tenth of a second, and having that scan take three hours. (Approximate times taken from my 2013 MacBook Pro.)

Let's take another example, of simply getting the last character in the string:

The first version is fast. It starts at the end of the string, scans backwards briefly to figure out where the last `Character` starts, and then fetches it. The second version does a full scan of the entire string... _twice!_ It has to scan the entire string to count how many `Character`s it contains, then scan it _again_ to figure out where the specified numeric index is.

Everything you could do with an API like this can still be done with Swift's API, it's just different, and a little harder. These differences show the programmer that these views are not just arrays and they don't perform like arrays. When we see subscript indexing, we assume with pretty good reason that the indexing operation is fast. If `String`'s views supported integer subscripting, it would be break that assumption, and make it easy to write really slow code.

**Writing Code With `String`**  
What does all of this mean when writing code that uses `String` for practical purposes?

Use the highest-level API you can. If you need to see if a string starts with a certain letter, for example, don't index into the string to retrieve the first character and compare. Use the `hasPrefix` method, which takes care of the details for you. Don't be afraid to import Foundation and use `NSString` methods. For example, if you want to remove whitespace at the beginning and end of a `String`, don't manually iterate and look at the characters, use `stringByTrimmingCharactersInSet`.

If you do need to do character-level manipulation yourself, think carefully about exactly what a "character" means to you in this particular case. Often, the right answer is a grapheme cluster, which is what's represented by the Swift `Character` type and the `characters` view.

Whatever you're doing with the text, think about it in terms of a linear scan from the beginning or the end. Operations like asking for the count of characters or seeking into the middle will likely be linear time scans anyway, so it's better if you can arrange your code to do so explicitly. Grab the appropriate view, get its start or end index, then move that index around as you need it using `advancedBy()` and similar functions.

If you really need random access, or don't mind an efficiency hit and want the convenience of a more straightforward container, you can convert a view into an `Array` of whatever that view contains. For example, `Array(string.characters)` will produce an array of the grapheme clusters in that string. This is probably not a very efficient representation and will chew up some extra memory, but it's going to be much easier to work with. You can convert back to a `String` when done.

**Conclusion**  
Swift's `String` type takes an unusual approach to strings. Many other languages pick one canonical representation for strings and leave you to fend for yourself if you want anything else. Often they simply give up on important questions like "what exactly is a character?" and pick something which is easy to work with in code but which sugar-coats the inherently difficult problems encountered in string processing. Swift doesn't sugar-coat it, but instead shows you the reality of what's going on. This can be difficult, but it's no more difficult than it needs to be.

The `String` API does have some holes in it, and could use some extra functionality to make life a little easier. In particular, converting from UTF-8 or UTF-16 to a `String` is unreasonably difficult and annoying. It would be nice to have facilities for initializing a `UTF8View` and `UTF16View` from arbitrary sequences of code units, as well as some more useful mutating functions on these views so they can be manipulated directly.

That's it for today. Come back next time for more shenanigans and terror. Friday Q&A is driven by reader ideas, so in the meantime, [send me your requests for topics](mailto:mike@mikeash.com!).

Comments: [Comments RSS feed for this page](https://www.mikeash.com/commentsrss.py?page=pyblog/friday-qa-2015-11-06-why-is-swifts-string-api-so-hard.html)

Add your thoughts, post a comment:

Spam and off-topic posts will be deleted without notice. Culprits may be publicly humiliated at my sole discretion.
