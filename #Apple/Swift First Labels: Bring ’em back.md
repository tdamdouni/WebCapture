# Swift First Labels: Bring ’em back

_Captured: 2016-03-10 at 00:01 from [ericasadun.com](http://ericasadun.com/2016/03/09/swift-first-labels-bring-em-back/)_

Today [Joe Groff](http://twitter.com/jckarter) asked whether the first parameter in a function declaration should follow the same rules as the remaining parameters.

> Our accepted naming guidelines have embraced first argument labels for functions and methods. This weakens our justification for making the first parameter declaration in a `func` declaration behave differently from the others, implicitly being unlabeled. It seems pretty clear to me we should make all of the parameter declarations behave uniformly:
> 
> `func foo(x: Int, y: Int) // Should declare foo(x:y:)`
> 
> instead of foo(_:y:)
> 
> `func foo(_ x: Int, y: Int) // Explicitly declares foo(_:y:)`
> 
> This would also make `init` and `func` parameters behave consistently, which is nice. There may still be hope for our keyword argument rules to one day be shorter than the Smalltalk spec…

I endorse this. Swift's guiding principles are clarity, concision, and consistency. The history of leading-labels from Swift 1 to Swift 2 and now to Swift 3 showcases a place where language design swerved to [better serve Cocoa/Objective-C standards](https://www.goodreads.com/quotes/353571-a-foolish-consistency-is-the-hobgoblin-of-little-minds-adored) and now returns to the emerging needs of a new and distinct language.

Swift supports Objective-C interoperation but the language is not Objective-C. There's still a great need to support, bridge to, and interact with legacy code but that support should not drive Swift's design.

A natural turbulence exists between Swift's design principles and the existing body and APIs of Cocoa code. From error handling to type safety, method signatures to core types, Swift needs to focus more on being Swift and less on feeling familiar to transitioning developers, especially as more users hop onboard from non-Apple platforms and languages.
