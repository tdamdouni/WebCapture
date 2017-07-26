# And then there was .None: when to nil and when to not

_Captured: 2016-01-05 at 00:40 from [ericasadun.com](http://ericasadun.com/2016/01/04/and-then-there-was-none-when-to-nil-and-when-to-not/)_

I was updating some _very_ old code today, when I stumbled across a `return .None` for some function that returned `T?`. It's been pretty much forever since I have used anything other than `return nil` and I thought I'd take a quick moment to figure out where `.None` belongs in my life.

It didn't take long (thanks, Olivier) to shake out a sketchy rule of thumb. It's this: if you're using pattern matching, you can go use `.None` if you really want to. If you are returning an optional value, just use `nil`.
    
    
    if case (.None, .None) = items { return nil }

Even if you can theoretically use:
    
    
    if case (nil, nil) = items { return nil }

skipping the `.None` in pattern matching just doesn't feel as nice, especially when you're doing any conditional binding:
    
    
    if case (.Some(let x), .None) = items { ... }

_vs_
    
    
    if case (.Some(let x), nil) = items { ... }

but then again, Swift now supports x? vs .Some(let x), so I'm also actually pretty okay with:
    
    
    if case (let x?, nil) = items { ... }

Conclusive? Not especially but there you have it.

_If you are building a custom enumeration and your conversation regularly includes terms like monads and functors, you're on your own._

> [@ericasadun](https://twitter.com/ericasadun) If you have a type other than Optional that conforms to NilLiteralConvertible, nil can lead to surprises <https://t.co/SRQtTHIV5V>
> 
> -- Bart Whiteley (@bwhiteley) [January 4, 2016](https://twitter.com/bwhiteley/status/684140219059159040)
