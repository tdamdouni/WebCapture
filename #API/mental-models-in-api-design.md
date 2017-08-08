# Mental models in API design

_Captured: 2017-08-01 at 18:48 from [oleb.net](https://oleb.net/blog/2017/07/mental-models-in-api-design/)_

I recently read Don Normanʼs classic _[The Design of Everyday Things_](https://en.wikipedia.org/wiki/The_Design_of_Everyday_Things). The book is primarily about product design, but some of the principles Norman mentions are just as applicable to API design.

[ ![The user’s mental model is not identical with the product designer’s mental model. Graphic adopted from The Design of Everyday Things by Don Norman.](https://oleb.net/media/design-of-everyday-things-design-model-vs-user-model-2224px.png) ](https://oleb.net/media/design-of-everyday-things-design-model-vs-user-model-2224px.png)

> _ The user only interacts with the product through the system image. He doesn't know the designer's mental model. When the system image doesn't reflect the design model, the user's mental model won't match the design model and the user will find the product hard to use. _

# Mental model mismatch

Norman points out that everybody approaches a product with a conceptual model of how it works. He calls this the _user's mental model_. Customers construct their mental model through interaction with the product. A customer's mental model will be shaped by the phsyical structure of the product -- its visual design, including things like knob placement and button labels -- and other information like the user manual that comes with the product. Norman calls this the _system image_. The system image will also be influenced by previous experiences the customer has had, perhaps having used similar items before or having seen ads for the product.

> Mental models, our conceptual models of the way objects work, events take place, or people behave, result from our tendency to form explanations of things. These models are essential in helping us understand our experiences, predict the outcomes of our actions, and handle unexpected occurrences. We base our models on whatever knowledge we have, real or imaginary, naive or sophisticated.**
> 
> Part of the power of a good mental model lies in its ability to provide meaning to things.

The product's designers also have a mental model of its inner workings -- the _design model_. A designer knows a lot more about the product than the average customer, so the design model is likely much more detailed and accurate than the customers' models.

**The fallacy many designers run into is to expect the user's model to be identical with the design model,** despite the huge information gap between designers and users:

> But the designer doesnʼt talk directly with the user--all communication takes place through the system image. **If the system image does not make the design model clear and consistent, then the user will end up with the wrong mental model.**

So the goal of product design is to provide customers with an accurate mental model:

> People probably make up mental models for most of the things they do. This is why designers should provide users with appropriate models: when they are not supplied, people likely make up inappropriate ones.

# Applied to APIs

I think this is where many APIs that we think of as unintuitive or hard to use break down.

## Are strings collections?

The string model in Swift 2 and 3 might be an example. Most developers probably think of strings as a collection of characters (or bytes, or …?). The fact that `[String` is not a `Collection` in Swift 3](https://oleb.net/blog/2016/08/swift-3-strings/) may be "correct" in a strict sense because a few Unicode edge cases are not compatible with `Collection` [semantics](https://oleb.net/blog/2016/12/protocols-have-semantics/), but new users will surely find it surprising.

If users don't have the correct mental model, they can't use the feature successfully, which can be very frustrating. For example, this doesn't work in Swift 3:
    
    
    str.split(separator: " ")
    // error: value of type 'String' has no member 'split'
    

One must write:
    
    
    str.characters.split(separator: " ")
    

The next possibly surprising thing is that this returns an array of `String.CharacterView` and not `[String]`. If you want to pass the result into another function, you probably have to do this:
    
    
    str.characters.split(separator: " ")
        .map(String.init)
    

Thankfully this will be fixed in Swift 4. (`split` will return `[Substring]`, still requiring the manual conversion to `String` if needed. But the name `Substring` expresses much better what's going on, I think. And [the documentation](https://developer.apple.com/documentation/swift/substring) explains the purpose of the type very well.)

## Strings and integer subscripting

Many (most?) developers also have mental models of strings that are closer to an "array of characters" and are therefore disappointed to learn that Swift doesn't support subscripting into strings with integer indices, such as `str[n]` to access the n-th character (for whatever interpretation of "character" the language uses).

This gap in mental models is harder to bridge because it can't easily be solved with different APIs. Swift's design model is arguably the correct and desirable one: Unicode strings inherently _aren't_ simple arrays of characters. To pretend otherwise by offering integer subscripting would contribute to users developing inaccurate mental models, e.g. with regard to performance characteristics.

Here, clear documentation and communication by the API designers must take care of teaching users the correct mental model. A great step in this direction is that the Swift compiler provides a hand-crafted error message for this particular issue. When you try to subscript a string with an integer, the compiler refers you to the documentation for a detailed explanation:
    
    
    "Hello World"[5]
    
    
    
    error: 'subscript' is unavailable: cannot subscript String
    with an Int, see the documentation comment for discussion
    

(The flipside is that I could not find [the documentation comment in question](https://github.com/apple/swift/blob/915923999592c4988fb1e6ec1673dfd46043f316/stdlib/public/core/UnavailableStringAPIs.swift.gyb#L13-L52) using Xcode. Command-clicking on subscript expressions is not supported, and I was unable to locate it in the documentation browser or in the standard library's generated interface. I ultimately found it by searching for the error message in the Swift repository on GitHub.)

I'm starting to see a pattern here. Swift's string model is very powerful and arguably more "correct" than what most other languages have. Once you've grokked it, it makes it easier to write Unicode-correct code. But that same aspect also makes it harder to learn, especially for developers who are coming from other languages (and thus have different mental models for how a string API usually works).

This is a common tradeoff in API design. The more features you add to an API, the more difficult it becomes to learn (and sometimes to use). For instance, Apple's [date and time APIs in Foundation](https://developer.apple.com/documentation/foundation/dates_and_times) are famous for being very accurate and nuanced. The cost of the correctness is that it takes more code than in other frameworks to do seemingly simple things like getting the hour component of a date.

Sometimes the added complexity is essential. I'd argue not supporting integer subscripting in strings is such a case. At other times it might be better to trade some correctness for a simpler API, as Swift did by making strings collections again.

## Method dispatch rules

Swift's [complicated method dispatch rules](https://www.raizlabs.com/dev/2016/12/swift-method-dispatch/) could be another example of a mental model mismatch. Method dispatch for protocol extensions changes depending on whether a method is a protocol requirement or not, for example. This makes sense if you have deep knowledge of the language's design model: since protocols can be extended in other modules after the protocol definition has been compiled, there is no space for additional methods in the protocol's [witness table](https://github.com/apple/swift/blob/master/docs/Lexicon.rst), so static dispatch is the only option for extensions. But I would guess that most users of the language [find the behavior unintuitive](https://nomothetis.svbtle.com/the-ghost-of-swift-bugs-future).

Again, the "solution" here is probably to make the documentation as clear as possible. I'm not sure how realistic improved compiler diagnostics are for this situation. It would certainly be ideal if the compiler were able to deduce the developer's intent and warn them about misconceptions in their mental model.

(Another option would be for Swift to make message dispatch the default everywhere. That is clearly not what the language designers have in mind, but it would make this part of the language easier to learn.)

> When the system image is incoherent or inappropriate …, then the user cannot easily use the device.

_-- Don Norman, _The Design of Everyday Things__

# Recap

Developers form a mental model of how the APIs they interact with work. A well-designed API manages to convey the API designer's mental model to the user through things like sensible naming, clear documentation, and similarities with other APIs the user is familiar with.

When APIs feel frustrating to use, a common pattern is that the API's design model is more nuanced and complex than the user's mental model.

PS: I used Swift APIs in the examples because I and most readers are familiar with them. I certainly don't mean to imply that the Swift standard library APIs are badly designed. (Although I do think there's a tendency in the Swift community to favor features over simplicity, for better or worse.)

  1. Yes, you can also do `str.components(separatedBy: " ")`, and that returns `[String]`. But only if you import Foundation. The weird mix between native `String` APIs and Foundation APIs that come from `NSString` is another unintuitive gap newcomers have to, uhm, bridge. [↩︎](https://oleb.net/blog/2017/07/mental-models-in-api-design/)
