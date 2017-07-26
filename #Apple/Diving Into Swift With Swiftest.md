# Diving Into Swift With Swiftest

_Captured: 2015-10-17 at 22:18 from [blog.8thlight.com](http://blog.8thlight.com/brian-pratt/2014/07/14/diving-into-swift-with-swiftest.html)_

When working in a language that's new to you, it's important to spend a lot of extra time making sure you are using the correct semantics. And when working in a language that is new to everyone, you have to dedicate as much time to _reading_ the code as you do to _writing_ it, because the semantics are still being discovered.

While reading through Swift, newly released by Apple at their Worldwide Developers Conference, I got a really good first impression of the language. The type system includes great static, non-nillable types without being verbose the way Java is. Its syntax is relatively simple, unlike Objective C or Haskell. It feels modern and expressive while still being pragmatic about mutation, unlike Haskell and Clojure.

But it's hard to get a firm sense of things when you're only writing basic "Hello World"\- or "kata"-level examples. So I tried something much more difficult: I decided to write a behavior-driven development framework. I figured this would be a good way for me to get experience with types, closures, and various other language features, while also presenting a problem sufficiently large enough to give a sense of Swift's design.

## Designing Swiftest

While diving into this project, I kept a few criteria in mind. I wanted the final product to be:

  * Extensible (think RSpec or Jasmine)
  * Written in pure Swift, or as close to it as possible
  * Not coupled to Apple's XCode testing framework

### Extensible

Swift comes with a few built-in extensions, so I've put off some of the "assertion matcher" work until later. Instead, I focused on making Swiftest as extensible as possible. I created "listeners" that can register themselves with Swiftest for different types of UI notifications. I made the Swiftest runner configurable with a simple closure, so users are free to modify the way Swiftest scans their code.

### Pure Swift

The core libraries of Swiftest are written in Swift and only Swift, because supporting 100 percent Obj-C interoperation would have meant sacrificing many of Swift's greatest features (generics, enums, immutable/non-nullable types). Interop coding has to be done in terms of simple language-based values, as opposed to complex types. By writing everything in Swift, I'm retaining the semantics and idioms of the language, while embracing Swift's actual environment.

The more time I spent working directly with Swift, the more apparent its benefits became. I don't really plan on writing in Obj-C anymore, because Swift is the bee's knees.

### Decoupled

I knew right away that I wanted to make Swiftest completely decoupled from Apple's XCode. This way we don't need to match every update in XCTest with a corresponding update in Swiftest. Instead, Swiftest allows XCode-based reporting to be implemented via "listeners."

## Next Steps

I have three major priorities following this release: the first is to redesign the matcher system for more direct extensibility.

Next, I want to simplify the installation process so that the user experience is as simple as possible. Nobody wants to fiddle with XCode build settings more than they have to.

Lastly, I'm seeking community feedback! Let me know what works well, what you think could use refining, or anything else I could add or subtract to make Swiftest a more effective BDD framework. I'm very excited about the possibilities provided by Swift, and I hope Swiftest helps you get started discovering these possibilities as well.

You can check Swiftest out [here](https://github.com/Swiftest/Swiftest) if you want to take a closer look!

#### More Posts by This Author
