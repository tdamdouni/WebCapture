# Matching with Swift's Optional Pattern

_Captured: 2015-12-06 at 23:47 from [www.figure.ink](http://www.figure.ink/blog/2015/12/6/matching-with-swifts-optional-pattern)_

## For Example…

Swift enumerations with raw values can be very handy when dealing with "stringly-typed" data of the sort JSON is notorious for:
    
    
    {
      "characters":[
        {"name":"Hank",
         "class":"ranger"},
        {"name":"Sheila",
         "class":"thief"},
        {"name":"Diana",
         "class":"acrobat"},
        {"name":"Eric",
         "class":"cavalier"}
      ]
    }

A string can hold a nearly infinite combination of possible values, and we need that sort of flexibility when representing names (the variety of which is also quite large).

But what about a character's class? There's only a handful of valid values for that. Representing them as strings (with their infinite variability) would not just be overkill, it'd expose us to potentially subtle bugs such as misspellings, capitalization errors, and non-exhaustive switch statements:
    
    
    switch stringFromJSON{
    case "ranger":
      //Good...
    case "Thief":
      //Oh no! Wrong capitalization.
    case "cavaleer":
      //Oops! Wrong spelling
    }
    //Yikes! We forgot completely about acrobats!

If we represent a character's class with a strict `enum` instead of a flexible `String`, Swift will catch all these bugs for us! And if we give raw values to our enum types, translating back and forth between JSON's strings is pretty easy too:
    
    
    enum DNDClass:String{
      case Ranger = "ranger"
      case Thief = "thief"
      case Acrobat = "acrobat"
      case Cavalier = "cavalier"
    }
    
    let myDNDClass = DNDClass(rawValue:stringFromJSON)
    let jsonString = myDNDClass?.rawValue

And this works great… until we try to use it in a `switch` statement:
    
    
    switch myDNDClass(rawValue:stringFromJSON){
    case .Ranger:
    //ERROR:
    //Enum case 'Ranger' not found in type 'DNSClass?'
    }

See that tricky "?" at the end of `DNSClass?`? We're getting an optional back from our constructor because `rawValue:` is actually a [failable initializer](https://developer.apple.com/swift/blog/?id=17).

And it makes sense that it would be. Like we said before, strings can hold a nearly infinite number of possible values. Our enum's constructor has to be ready for that:
    
    
    DNDClass(rawValue:"ranger")
    //> "Optional(DNDClass.Ranger)"
    
    DNDClass(rawValue:"foobar")
    //> "nil"

We can deal with this by guarding against `nil`s:
    
    
    guard let c = DNDClass(rawValue:jsonString) else{
      fatalError("Unexpected class: \(jsonString)")
    }
    
    switch c{
    case .Ranger:
      //Do ranger stuff...
    }

And that's okay… But now we have to parse a chunk of logic above our `switch` before getting down to business.

We could, instead, take advantage of the fact that `[Optional`s are enums](http://www.codingexplorer.com/swift-optionals-declaration-unwrapping-and-binding/):
    
    
    switch DNDClass(rawValue:jsonString){
    case .Some(.Ranger):
      //Do ranger stuff...
    case .None:
      fatalError("Unexpected class: \(jsonString)")
    }

But now, instead of having a clean abstraction around the very concept of an `Optional`, we have a leaky abstraction that requires anyone who reads it to understand the `.Some`s and `.None`s being used under the covers. There's a reason, after all, that the [Swift Programming Language](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/index.html) makes no mention of `Optional`'s implementation.[1](http://www.figure.ink/blog/2015/12/6/)

## The Optional Pattern

This is why [the optional pattern](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/Patterns.html#//apple_ref/doc/uid/TP40014097-CH36-ID520) exists. Just add a "?" to the end of an [identifier](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/Patterns.html#//apple_ref/doc/uid/TP40014097-CH36-ID421), and it "matches values wrapped in a `Some(Wrapped)` case of an `Optional<Wrapped>` enumeration."

In other words, these `case`s are equivalent:
    
    
    switch DNDClass(rawValue:jsonString){
    case .Some(.Ranger):
      //...
    case .Ranger?:
      //...
    }

This goes for more complex [value-binding patterns](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/Patterns.html#//apple_ref/doc/uid/TP40014097-CH36-ID422) as well:
    
    
    enum Response{
     case Error(String)
    }
    
    switch myResponse:
    case .Some(.Error(let s)):
      //Do something with «s»...
    case .Error(let s)?:
      //Also can do something with «s»...
    }

In essence, any time you want to match a pattern against an unwrapped optional value, just put a `?` at the end of it.

## Don't Default

There's just one gotcha left to tackle. We might expect the following to be exhaustive, but Swift is going to tell us it's not:
    
    
    switch DNDClass(rawValue:jsonString){
    case .Ranger?:
      //Do ranger stuff...
    case .Thief?:
      //Hide in shadows...
    case .Acrobat?:
      //Backflips...
    case .Cavalier?:
      //Whatever it is a cavalier does...
    }
    
    //> ERROR: Switch must be exhaustive

That's because, even though we've covered every character class in our enum, there's one important case we've forgotten; what if `DNDClass`'s init fails and returns `nil`?

We could easily catch this with a `default`:
    
    
    switch DNDClass(rawValue:jsonString){
    case .Ranger?:
    case .Thief?:
    case .Acrobat?:
    case .Cavalier?:
    default:
      //None of the above...
    }

But we only want to catch the `nil` case, and `default` catches everything. With `default` in there, we could add new character classes to our enum,[2](http://www.figure.ink/blog/2015/12/6/) and Swift wouldn't warn us if we forgot to cover them in the `switch`.

A common mistake is to try to use the optional pattern again, maybe with something like `nil?`. But remember, the optional pattern only matches when an optional is expressly _not_ `nil`. So that will never work.

The easiest, most readable thing is to use the literal `nil`, itself:[3](http://www.figure.ink/blog/2015/12/6/)
    
    
    switch DNDClass(rawValue:jsonString){
    case .Ranger?:
    case .Thief?:
    case .Acrobat?:
    case .Cavalier?:
    case nil:
      //Failed to init.
    }

Patterns in Swift (or, at least, [the _documentation_ for patterns in Swift](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/Patterns.html)) use a lot of very precise terminology that can take a bit of work to wrap one's head around. But they're incredibly useful[4](http://www.figure.ink/blog/2015/12/6/) and punch well above their weight in their contributions to Swift's expressiveness.

As the language [continues to evolve](https://github.com/apple/swift-evolution), I'm most excited to see what changes and additions happen in this space.

1: Sort of. It actually _is_ mentioned in two places: an example that "Reimplements the Swift standard library's optional type", and the example that shows equivalent code to very optional pattern we're about to discuss.[↩︎](http://www.figure.ink/blog/2015/12/6/)

3: This isn't a special pattern or identifier -- it's simply an expression of the fact `Optional.None == nil` is `true`.[↩︎](http://www.figure.ink/blog/2015/12/6/)

4: Especially in Swift 2 since it gives `if`, `while`, `guard`, and `for-in` their own `case` matchers. Add those to the existing `switch`, and there are all sorts of places for us to play with patterns![↩︎](http://www.figure.ink/blog/2015/12/6/)
