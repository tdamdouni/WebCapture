# Interesting discussions on Swift Evolution

_Captured: 2015-12-24 at 17:18 from [ericasadun.com](http://ericasadun.com/2015/12/15/interesting-discussions-on-swift-evolution/)_

Thought I'd share a few highlights:

## newtype

One proposal suggests Swift introduces a `newtype` keyword that adds an extensible derived type that is otherwise identical to the original. For example,
    
    
    newtype Currency = NSDecimal

creates a `Currency` type that has all the behaviors of `NSDecimal`. However, you can't sum together a `Currency` with an `NSDecimal` so there's type checking, and you can extend the `Currency` type. It's specialization without subclassing or adding new storage.

Another spin on `newtype` creates a kind of type currying:
    
    
    newtype Counter<A> = Dictionary<A, Int>

The type is partially specified so behavior can be implemented through extensions that applies generically across various dictionaries with arbitrary keys and Int values.

I'm looking forward to seeing where this discussion leads.

## self

Another proposal suggested that `self` be instated as a mandatory prefix instead of permitting context inference. Greg Parker wrote in response:

> Note that the `self.property` access in Objective-C was not the preferred design.
> 
> The first choice was for bare `property` to work. That turned out to be ambiguous too often because of identically-named ivars. Swift doesn't have that problem.
> 
> The second choice was for bare `property` to access the property, requiring `self->ivar` to access an identically-named ivar. That was not feasible because it was incompatible with too much existing source code. Swift doesn't have that problem either.

## precondition vs assert

Dave Abrahams responded to a proposal about renaming assert and precondition with some insights that I immediately bookmarked in my notes file:

> Here's some rationale that may be missing. The two functions have distinct roles:  
- assert: checking your own code for internal errors.  
- precondition: for checking that your clients have given you valid arguments.
> 
> It's actually important to distinguish these two cases because the second one demands public documentation while the first does not.
> 
> For example: in Swift's standard library we promise never to allow memory errors unless you call (Obj)C code or use an explicitly labeled "unsafe" construct. On the occasions where we need to do a check on the client's parameters to avoid causing a memory error when we're given invalid arguments, we document the requirements on the arguments as a precondition, and use (our equivalent of) precondition() to check it. We also have a bunch of internal sanity checks to make sure our assumptions about our own code, where the type system doesn't already guarantee them, are correct. For those, we use (our equivalent of) assert(), because we don't want to slow down *your* code as an artifact of our development process (the use of sanity checks).
> 
> Here are a couple of concrete examples:
>     
>     
>     /// A collection whose elements are all identical `Element`s.
>     
>     public struct Repeat<Element> : CollectionType {
>       ...
>       /// Access the element at `position`.
>       ///
>       /// - Requires: `position` is a valid position in `self` and
>       ///   `position != endIndex`.
>       public subscript(position: Int) -> Element {
>         _precondition(position >= 0 && position < count, "Index out of range")
>         return repeatedValue
>       }
>     }
>     extension String.UTF8View {
>       ...
>      private func _encodeSomeContiguousUTF16AsUTF8(i: Int) -> (Int, UTF8Chunk) {
>         _sanityCheck(elementWidth == 2)
>         _sanityCheck(!_baseAddress._isNull)
>      
>         let storage = UnsafeBufferPointer(start: startUTF16, count: self.count)
>         return _transcodeSomeUTF16AsUTF8(storage, i)
>       }
>     }
> 
> In the first example, we have a precondition that the client doesn't index past the end of the collection. In this case we're not strictly bound to check it because we're not avoiding a memory error,* but we do check it as a service to our clients; it will help them find their bugs sooner.
> 
> In the second example, this is a private function that is meant to be called only on a code path where we've ensured elementWidth == 2 and _baseAddress is not null (_sanityCheck is the stdlib's equivalent of assert). That is in fact how it is being used, but we want to ensure that ongoingly. For example, we don't want someone to add code later that uses it incorrectly. Since we run our tests in both debug and release and we have decent test coverage, the assertions are very likely to fire if that should happen.
> 
> You might think from the above that assert() only gets used in private methods and precondition() only gets used in public methods, but that's not the case; you could inline any private method into the body of the public method it implements, and doing sanity checks there would still make sense. Precondition checks occasionally appear in private methods, too. The simplest example is where duplicated precondition checking code is factored out of a bunch of public methods and into a single private helper.
> 
> * Note that some preconditions actually can't be checked, so having a rule that all preconditions must be checked isn't tenable.

[ Tweet this Post ](https://twitter.com/share?text=Interesting%20discussions%20on%20Swift%20Evolution&url=http://ericasadun.com/2015/12/15/interesting-discussions-on-swift-evolution/&counturl=http://ericasadun.com/2015/12/15/interesting-discussions-on-swift-evolution/)
