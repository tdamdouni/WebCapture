# Swift Style Guide: December 2014 Update

_Captured: 2015-11-25 at 20:33 from [www.raywenderlich.com](http://www.raywenderlich.com/90974/swift-style-guide-december-2014-update)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Check out our official Swift style guide!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/SwiftStyleGuide.png)

> _Check out our latest Swift style guide update!_

Swift has only been out for a few months, but it's already gone through a ton of changes - both in terms of syntax, and what we consider best practices.

As a team, we want to have a consistent style for you in our tutorials, books, videos and conference materials, and part of that consistency is keeping up to date with the changes to the language.

As such, we've recently made some additions and tweaks to our [raywenderlich.com Swift style guide](https://github.com/raywenderlich/swift-style-guide) and I wanted to highlight some of the changes.

If you left a comment, issue, or pull request - thank you! We appreciate your feedback and advice.

With that in mind, let's take a look at what's new!

_Note_: Our style guide is different than other style guides out there; we're a tutorial site, which means our priorities are shorter and readable code for printed books and the web. Many of the decisions were made with an eye toward conserving space for print, legibility, and tutorial writing.

## Optional Binding

After a surprisingly short discussion (knock on wood) we came to a consensus on two things about naming:

  1. Don't give optional variables names like `maybeView` or `optionalString`.
  2. Don't give unwrapped variables names like `reallyLabel` or `unwrappedFloat`.

For optional binding, we went for the simplest solution: to shadow the original name.
    
    
    var textLabel: UILabel?
     
    // later...
    if let textLabel = textLabel {
      // do something with textLabel, which is now unwrapped
    }

While `let textLabel = textLabel` might look a little strange, I think it's the best solution: the variable name is short and obvious, and the type system will catch you at compile time if you mix up the optional from the unwrapped.

## Structs vs Classes

In Objective-C, we pretty much used classes for everything. C-style structs became especially rare in the post-ARC world, thanks to the compiler's need to track retains and releases for us.

Swift structs are a powerful option available to us, but there's still some confusion over when to use a class and when to use a struct. Some people out there are suggesting, when in doubt, use a struct.

![struct](http://cdn2.raywenderlich.com/wp-content/uploads/2014/12/struct.png)

However, it's not that simple. Our ever-wise tutorial team member Matthijs added a great explanation using _identity_ as a guide to whether something should be a struct or a class:

  * Structs have [value semantics](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html#//apple_ref/doc/uid/TP40014097-CH13-XID_144). Use structs for things that _do not have an identity_. 

An array that contains [a, b, c] is really the same as another array that contains [a, b, c] and they are completely interchangeable. It doesn't matter whether you use the first array or the second, because they represent the exact same thing. That's why arrays are structs. 

  * Classes have [reference semantics](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html#//apple_ref/doc/uid/TP40014097-CH13-XID_145). Use classes for things that _do have an identity_ or a _specific life cycle_. 

You would model a person as a class because two person objects are two different things. Just because two people have the same name and birthdate, doesn't mean they are the same person. But the person's birthdate would be a struct because a date of 3 March 1950 is the same as any other date object for 3 March 1950. The date itself doesn't have an identity.

## Struct Initializers and Constants

Like Apple, we really appreciate initializers with named parameters for clarity. From early on, our style guide expressed a preference for struct initializers over the previous C-style constructor functions for `CGGeometry` structs.
    
    
    // preferred
    var point = CGRect(x: 0, y: 10, width: 200, height: 120)
     
    // not preferred
    var point = CGRectMake(0, 10, 200, 120)

The struct initializer is longer (although just as easy to type with code completion) but each parameter is clearly marked.

New to the guide is a preference to constants such as `CGRect.zeroRect` rather than `CGRectZero`. For an existing variable, you can use the shorter style without the type name:
    
    
    view.frame = .zeroRect

This mirrors Swift's approach to namespacing and uses the constant that's "included" inside the struct definition itself. We hope this makes the types easier to spot and the constants themselves cleaner-looking.

## Protocol Conformance

Perhaps you've seen a class declaration like this before:
    
    
    class MyViewController: UITableViewDelegate, UITableViewDataSource, UIScrollViewDelegate, UINavigationControllerDelegate, UIImagePickerControllerDelegate, UITextFieldDelegate

We won't judge you for having such a busy view controller, but we do suggest having each protocol conformance declared in its own extension:
    
    
    class MyViewController {
      // Standard view controller stuff here
    }
     
    extension MyViewController: UITableViewDelegate {
      // Table view delegate methods here
    }
     
    extension MyViewController: UITextFieldDelegate {
      // Text field delegate methods here
    }
     
    // etc.

This keeps things organized and helps keep related methods together. It also means you can add a protocol and related methods in one step in one place, rather than editing the class declaration and then adding methods somewhere to a potentially crowded list of methods.

## Where to Go From Here?

"_Code is executed (or compiled) by computers but read by humans_" - I've heard variants of this quote many times, and it especially reminds me of what we do here on raywenderlich.com: our job is to communicate with you both in writing and in code.

If you learn from and enjoy our tutorials, I hope at least a small part of that is thanks to things like readability and formatting and consistency.

Swift continues to evolve, and there will continue to be strong opinions about code style. As always, we welcome your suggestions, comments, and especially pull requests at the [Swift style guide](https://github.com/raywenderlich/swift-style-guide) repository!
