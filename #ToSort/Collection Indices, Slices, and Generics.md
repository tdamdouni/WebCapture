# Collection Indices, Slices, and Generics

_Captured: 2015-12-31 at 21:58 from [airspeedvelocity.net](http://airspeedvelocity.net/2015/12/28/collection-indices-slices-and-generics/)_

I missed posting about the last couple of releases of Swift before it was [open sourced](https://github.com/apple/swift/blob/master/CHANGELOG.md), but now that I have some time to write a couple of posts over the holidays, here's a one about this sentence in the release notes for 2.0 beta 5:

> For consistency and better composition of generic code, `ArraySlice` indices are no longer always zero-based but map directly onto the indices of the collection they are slicing and maintain that mapping even after mutations. 

Why is this interesting enough to write a whole post over? It has to do with this bit of code that you see written from time to time:

12345
`// iterate over the indices in a collection:``for` `idx in ``0``..<someCollection.count {``// use someCollection[idx] in some way``// that can't be done via for x in someCollection``}`

What's wrong with that? Well, if `someCollection` is an `Array`, nothing. Hmm, maybe readability. All collections have an `indices` property that does the same thing. If you think

1
`for` `idx in ``0``..<someCollection.count`

is just as readable as

1
`for` `idx in someCollection.indices`

then I put it to you that all these C derivatives have addled your brain. If you remain unconvinced, the rest of this article is probably going to be a bit like [this cartoon](http://www.theeditorialcartoons.com/store/add.php?iid=41786).

(if you find yourself wanting all but the last index, or all but the first, remember `Range` is a collection, so you can write things like `someCollection.indices.dropLast()`)

Anyway, readability aside, the problems come when you try and make your loop generic. For example, take everyone's favorite way to start an [algorithms text book](http://www.amazon.com/gp/product/032157351X/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=032157351X&linkCode=as2&tag=airspveloc0d-20&linkId=SX2U6P3O2T4Z6GUF), a binary search. Here's a version for arrays:

123456789101112131415161718192021222324252627282930313233343536
`extension Array``// this seems to be the indentation style``// found in the open-sourced the Swift code...``where  ``Generator.Element``:` `Comparable {``/// Returns an index of an element in `self` which ``/// is equal to `element`, or `nil` if such value``/// is not found.``///``/// - Requires: elements of `self` are ordered by <``///``/// - Complexity: O(log(`self.count`)).``public func binarySearch(``element``:` `Generator.Element``) -> Int? {``var` `left ``=` `0``var` `right ``=` `count - ``1``while` `left <``=` `right {``let mid ``=` `(left + right) / ``2``let candidate ``=` `self[mid]``if` `candidate < element {``left ``=` `mid + ``1``}``else` `if` `element < candidate {``right ``=` `mid - ``1``}``else` `{``return` `mid``}``}``// Not found``return` `nil``}``}`

(you'd probably want to implement a version that takes an `isOrderedBefore` predicate, then implement this one in terms of that one, but let's ignore that for now)

Binary searches are [notoriously hard to get right](http://googleresearch.blogspot.com/2006/06/extra-extra-read-all-about-it-nearly.html), and this one contains at least one bug - that I've left in deliberately to talk about later - as well as the ones I added accidentally that you can [let me know](https://twitter.com/airspeedswift) about.

A first trainer-wheels attempt to make this generic might be to switch the extension to be of `CollectionType`, and constrain the index to be of type `Int`:

123456
`extension CollectionType ``where ``Index ``==` `Int, ``Generator.Element``:` `Comparable {``// same as before``}`

This _seems_ like it's working at first. You can now use it on `ContiguousArray`, `UnsafeBufferPointer` and, up until it changed, `ArraySlice`. It won't work with random-access-indexed collections that don't use integer indices, but there aren't many of those around. But it makes a big assumption that the collection is zero based. As I [mentioned in a previous changes post](http://airspeedvelocity.net/2015/07/23/changes-to-the-swift-standard-library-in-2-0-betas-2-5/) when collections all became sliceable, this became a very shakey assumption, and now it doesn't even apply to array slices. It's also not something the type system will help you find - you'd discover it at runtime when your out-of-bounds error traps.

You could fix it while keeping the constraint to integer indices, but at this point you may as well rip the band-aid off and just make it fully generic. This also helps you spot all the places where you need to fix your zero-based assumption. It starts easy enough…

1234567891011
`extension CollectionType ``where``Index``:` `RandomAccessIndexType, ``Generator.Element``:` `Comparable {``public func binarySearch(``element``:` `Generator.Element``) -> Index? {``// instead of 0 for the start:``var` `left``:` `Index ``=` `startIndex``// and instead of count - 1 for the end:``var` `right``:` `Index ``=` `endIndex.predecessor()`

but then we hit trouble:

123
`// error: binary operator '+' cannot be``// applied to two 'Self.Index' operands``let mid ``=` `(left + right) / ``2`

You can't just add two indices together. Think about non-contiguous storage like a node-based container like a [linked list](http://airspeedvelocity.net/2015/07/26/linked-lists-enums-value-types-and-identity/) or a tree. You can't just add together two node pointers. Or for a random-access example, what about `ReverseRandomAccessCollection`, which is a wrapper around a random-access collection, and has an opaque index type. How could you add two of those together?

Really there are two concepts here - indices, and _distances_ between indices. You can always count, as an integer, the number of times you need to call `successor()` on an index to get to a later index. This is the distance between them. You can do mathematical operations on distances - you can go twice as far from an index, or advance as far from one index as another is from the start. All indices have this ability, but bi-directional indices can have negative distances (the number of times you'd need to call `predecessor()`), and random-access indices can move by a distance in constant time.

When we had an integer index on a zero-based collection, a handy trick we were relying on is that any index is also the distance of that index from the start. So when we wrote `let mid = (left + right) / 2`, really this was saying that the mid-point was the average of the distance from the start of the two indices. But now we want our algorithm to work not just on zero-based integer indices but kind of random-access index (random-access because if you can't move around in constant time, you may as well do a linear search).

You could rewrite that generically as:

1234
`let mid ``=` `startIndex.advancedBy(``(  startIndex.distanceTo(left) ``\+ startIndex.distanceTo(right)``) / ``2``)`

but this would be a bit silly. Instead, you can just take the distance from the left to the right, halve that, and add it to the start. We can add this ability to `Range`, to give us a mid-point property (and which also fixes a bug, if you followed the earlier link):

1234567
`extension Range {``var` `mid``:` `Element {``return` `startIndex.advancedBy(``startIndex.distanceTo(endIndex) / ``2``)``}``}`

which we can use in a fully generic binary search:

12345678910111213141516171819202122232425262728293031323334353637
`extension CollectionType ``where ``Index``:` `RandomAccessIndexType {``public func binarySearch(``element``:` `Generator.Element, ``isOrderedBefore``:` `(Generator.Element,Generator.Element)->Bool``) -> Index? {``var` `searchRegion ``=` `self.indices``while` `!searchRegion.isEmpty {``let mid ``=` `searchRegion.mid``let candidate ``=` `self[mid]``if` `isOrderedBefore(candidate,element) {``searchRegion.startIndex ``=` `mid + ``1``}``else` `if` `isOrderedBefore(element,candidate) {``searchRegion.endIndex ``=` `mid``}``else` `{``return` `mid``}``}``return` `nil``}``}``extension CollectionType ``where Index``:` `RandomAccessIndexType, ``Generator.Element``:` `Comparable ``{``public func binarySearch(``element``:` `Generator.Element``) -> Index? {``return` `binarySearch(element, isOrderedBefore``:` `<)``}``}`

Note, we can still write `searchRegion.startIndex = mid + 1` because `RandomAccessIndexType` conforms to `Strideable`, which has this definition of `+`

that allows you to add a distance (which is an indices' stride) to an index. There's a matching definition with the lhs and rhs flipped so you can write it the other way around.

This version makes a couple of other changes. It combines the left and right indices into a `Range`, `searchRegion`. I think this helps readability a bit - `!searchRegion.isEmpty` is a bit nicer than `left`<=`right` - and also allows us to use our `mid` extension. But more importantly, this rewrite ditches the other trick we were relying on when the index was an integer - you can go one past the end or ahead of the start without any consequences. When your index is an integer, who cares if you decrement it from `0` to `-1`. But some indices don't take kindly to going past their limit (try calling `&quot;hello&quot;.endIndex.successor()`). So to make the algorithm properly generic, it needed a rewrite to avoid this being a possibility.

Talking of readability, 2.1b5 added some additional slicing methods, so instead of:

123
`a[a.startIndex...idx]``a[a.startIndex..<idx]``a[idx..<a.endIndex]`

you can now write:

123
`a.prefixThrough(idx)``a.prefixUpTo(idx)``a.suffixFrom(idx)`

It's kinda fun, though probably a bit cute to be used in production code, to write Python-style one-sided subscript operations for these as well:

12345678910111213141516171819202122232425262728
`postfix operator ..< { }``prefix operator ..< { }``prefix operator ... { }``struct RangeStart<I``:` `ForwardIndexType> { let start``:` `I }``struct RangeToEnd<I``:` `ForwardIndexType> { let end``:` `I }``struct RangeThroughEnd<I``:` `ForwardIndexType> { let end``:` `I }``postfix func ..< <I``:` `ForwardIndexType>(lhs``:` `I) -> RangeStart<I>``{ ``return` `RangeStart(start``:` `lhs) }``prefix func ..< <I``:` `ForwardIndexType>(rhs``:` `I) -> RangeToEnd<I>``{ ``return` `RangeToEnd(end``:` `rhs) }``prefix func ... <I``:` `ForwardIndexType>(rhs``:` `I) -> RangeThroughEnd<I>``{ ``return` `RangeThroughEnd(end``:` `rhs) }``extension CollectionType {``subscript(r``:` `RangeStart<Self.Index>) -> SubSequence {``return` `self.suffixFrom(r.start)``}``subscript(r``:` `RangeToEnd<Self.Index>) -> SubSequence {``return` `self.prefixUpTo(r.end)``}``subscript(r``:` `RangeThroughEnd<Self.Index>) -> SubSequence {``return` `self.prefixThrough(r.end)``}``}`

which then means you can write:

1234
`let a ``=` `[``1``,``2``,``3``,``4``]``a[``1``..<] ``// [2,3,4]``a[..<``2``] ``// [1,2]``a[...``2``] ``// [1,2,3]`

You could even define pattern-matching versions, for use in a `switch` statement:

so you can write:

12345678
`for` `i in [``9``, ``10``, ``11``] {``switch i {``case` `..<``10``:` `print(``"below 10"``)``case` `...``10``:` `print(``"10 or below"``)``case` `2``..<``:` `print(``"2 or more"``)``default``:` `fatalError()``}``}`

If you're not familiar with `~=`, check out Ole's [series of posts](http://oleb.net/blog/2015/09/swift-pattern-matching/) about pattern matching, it's pretty powerful.
