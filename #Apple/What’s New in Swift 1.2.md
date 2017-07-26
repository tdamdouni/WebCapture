# What’s New in Swift 1.2

_Captured: 2015-11-25 at 20:34 from [www.raywenderlich.com](http://www.raywenderlich.com/95181/whats-new-in-swift-1-2)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Get the heads up on what's new in Swift 1.2!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Get the heads up on what's new in Swift 1.2!_

Just when we thought Apple was busy working on more WatchKit and Xcode 6.2 betas - _Xcode 6.3_ beta and _Swift 1.2_ landed in our collective laps on Monday!

There are a ton of exciting changes in Swift 1.2. It's still very much a beta, and only the inner circle at Apple know when it will be finalized, so it's not a good idea to use it in any apps you're planning on shipping anytime soon.

But it's still good to keep up-to-date with the changes so you're when they go live. In this article, I'll highlight the most significant changes in Swift 1.2:

  * Speed improvements
  * Improved if-let optional binding
  * Changes to `as` when casting
  * Native Swift sets
  * Changes to initializing constants
  * Objective-C interop and bridging

And to tie it all together, I'll try out the new Swift migrator tool to see just how well it converts a project written in Swift 1.1 to 1.2, and I'll let you know how Swift 1.2 affects our tutorials books.

Remember, _Swift 1.2 is beta software_. The final Swift 1.2 release is still a good way away, and you can't submit apps built with Xcode 6.3 beta to the store. So again, this isn't something you'll probably want to use yet, but it's nice to keep track of what Apple has in mind for the language and the platform.

Let's look into the future and get a sneak peek of what's in store for us Swift developers!

## Speed Improvements

Swift 1.2 brings several speed improvements to make both your apps and development even swifter!

  * _Incremental Builds_: Xcode no longer needs to recompile every single file in the project every time you build and run. The build system's dependency manager is still pretty conservative, but you should see faster build times. This should be especially significant for larger projects.
  * _Performance Enhancements_: The standard library and runtime have been optimized; for example, the release notes point to speed ups in multidimensional array handling. You'll need to benchmark your own apps since performance characteristics are so different between apps.

Swift code is already [faster than Objective-C code in some cases](http://www.jessesquires.com/apples-to-apples-part-two/), so it's good to see continued improvement here!

## if-let improvements

The aptly-named "pyramid of doom" is no more! Before Swift 1.2, you could only do optional binding on one thing at a time:
    
    
    // Before Swift 1.2
    if let data = widget.dataStream {
      if data.isValid {
        if let source = sourceIP() {
          if let dest = destIP() {
            // do something
          }
        }
      }
    }

Now, you can test multiple optionals at once:
    
    
    // After Swift 1.2
    if let data = widget.data where data.isValid, let source = sourceIP(), dest = destIP() {
      // do something
    }

Note the new `where` keyword that lets you test for boolean conditions inline. This makes your conditionals much more compact and will avoid all that extra indentation.

## Upcasts and downcasts

The `as` keyword used to do both upcasts and downcasts:
    
    
    // Before Swift 1.2
    var aView: UIView = someView()
     
    var object = aView as NSObject // upcast 
     
    var specificView = aView as UITableView // downcast

The upcast, going from a derived class to a base class, can be checked at compile time and will never fail.

However, downcasts can fail since you can't always be sure about the specific class. If you have a `UIView`, it's possible it's a `UITableView` or maybe a `UIButton`. If your downcast goes to the correct type - great! But if you happen to specify the wrong type, you'll get a runtime error and the app will crash.

![cast](http://cdn4.raywenderlich.com/wp-content/uploads/2015/02/cast-371x320.png)

In Swift 1.2, downcasts must be either optional with `as?` or "forced failable" with `as!`. If you're sure about the type, then you can force the cast with `as!` similar to how you would use an implicitly-unwrapped optional:
    
    
    // After Swift 1.2
    var aView: UIView = someView()
     
    var tableView = aView as! UITableView

The exclamation point makes it absolutely clear that you know what you're doing and that there's a chance things will go terribly wrong if you've accidentally mixed up your types!

As always, `as?` with optional binding is the safest way to go:
    
    
    // This isn't new to Swift 1.2, but is still the safest way
    var aView: UIView = someView()
     
    if let tableView = aView as? UITableView {
      // do something with tableView
    }

## Sets

_Note:_ If you're unfamiliar with sets, or data structures in general, check out our tutorial [Collection Data Structures In Swift](http://www.raywenderlich.com/79850/collection-data-structures-swift).

![Doge](http://cdn2.raywenderlich.com/wp-content/uploads/2015/02/Doge-250x250.png)

Swift 1.0 shipped with native strings, arrays and dictionaries bridged to `NSString`, `NSArray` and `NSDictionary`. The data structure nerds asked, "what happened to sets?"

Better late than never, native Swift sets are here! Like arrays and dictionaries, the new `Set` type is a struct with value semantics.

Like arrays, sets are generic collections so you need to provide the type of object to store; however, they store unique elements so you won't see any duplicates.

If you've used `NSSet` before, you'll feel right at home:
    
    
    var dogs = Set<String>()
     
    dogs.insert("Shiba Inu")
    dogs.insert("Doge")
    dogs.insert("Husky puppy")
    dogs.insert("Schnoodle")
    dogs.insert("Doge")
     
    // prints "There are 4 known dog breeds"
    println("There are \(dogs.count) known dog breeds")

You can do everything you would expect with Swift sets: check if a set contains a value, enumerate all the values, perform a union with another set, and so on.

This is a great addition to the standard library and fills a big abstraction hole where you still had to drop down to `NSSet`, which doesn't feel very native in Swift. Hopefully, other missing types such as `NSDate` are next on the list to be Swift-ified. ;]

## let constants

Constants are great for safety and ensuring things that shouldn't change don't change. Our [Swift Style Guide](https://github.com/raywenderlich/swift-style-guide) even suggests this rule of thumb: "define everything as a constant and only change it to a variable when the compiler complains!"

One of the biggest problems with constants was that they had to be given a value when declared. There were some workarounds, ranging from just using `var` to using a closure expression to assign a value.

But in Swift 1.2, you can now declare a constant with `let` and assign its value some time in the future. You do have to give it a value before you access the constant of course, but this means you can now set the value conditionally:
    
    
    let longEdge: CGFloat
     
    if isLandscape {
      longEdge = image.calculateWidth()
    } else {
      longEdge = image.calculateHeight()
    }
     
    // you can access longEdge from this point on

Any time using `let` is made easier, it's a thumbs up for clearer, cleaner code with fewer possible side effects.

## Objective-C interop

As Swift matures, the default classes will slowly shift towards the native Swift implementations. And that's already happening!

In Swift 1.2, Objective-C classes that have native Swift equivalents (`NSString`, `NSArray`, `NSDictionary` etc.) are no longer automatically bridged. That means passing an `NSString` to a function that expects a `String` will now fail!
    
    
    func mangleString(input: String) {
      // do something with input
    }
     
    let someString: NSString = "hello"
     
    mangleString(someString) // compile error!

If you want to do this, you'll need to be explicit with the type conversion:
    
    
    mangleString(someString as String)

Again, Swift is becoming the first-class citizen here: basically, Swift strings will work whenever some kind of string (`String` or `NSString`) is expected. The only change here is when you have those old `NSString` instances to work with.

![NSString quaint](http://cdn5.raywenderlich.com/wp-content/uploads/2015/02/NSString-quaint.png)

> _NSString quaint_

### Dealing with optionals

If you've been following all the changes to Swift until now, you've seen arguments change from `UIView` to `UIView!` to `UIView?` and back again. We were spoiled with being able to message `nil` in Objective-C, but Swift is much stricter about things.

If you're maintaining Objective-C code, there are some new qualifiers for you to use when specifying the type for arguments, variables, properties, etc.:

  * `nonnull` - will never be `nil`
  * `nullable` - can be `nil`
  * `null_unspecified` - unknown whether it can be nil or not (the current default)

For example, consider how these Objective-C declarations would map to Swift:

  * `nonnull NSString *string` - a regular object, `String`
  * `nullable NSString *string` - this is an optional, `String?`
  * `null_unspecified NSString *string` - unknown, thus implicitly unwrapped, `String!`

If you don't have Objective-C code to maintain, you'll still benefit from Apple adding these qualifiers to the Cocoa headers. That will make your Swift experience that much cleaner with fewer implicitly-unwrapped values.

## Swift migrator

Xcode 6.3 beta includes a Swift migrator to help automate some of these changes to Swift 1.2.

I made a copy of the official [RWDevCon](http://www.rwdevcon.com) app project and opened it in Xcode 6.3 beta. How far would I get with a build and run?

![migration-12-errors](http://cdn4.raywenderlich.com/wp-content/uploads/2015/02/migration-12-errors.png)

There's a new menu option: _Edit\Convert\To Swift 1.2…_. First you select a target and then it's very similar to how refactoring works - Xcode will churn away and then come back with a preview. You'll see the old code and new code side-by-side with the changes highlighted.

In this project, all the automated conversion did was suggest changing `as` to `as!` all over the place. There was one case of nil coalescing that the migrator didn't understand:
    
    
    let date = (data["metadata"] as NSDictionary?)?["lastUpdated"] as? NSDate ?? beginningOfTimeDate

That's a pretty complicated expression! The migrator got confused and assumed there were two expressions there. The solution? A semicolon, of course!
    
    
    let date = (data["metadata"] as! NSDictionary?)?["lastUpdated"] as? NSDate ??; beginningOfTimeDate

That's some kind of syntax error that doesn't compile. The other additions of `as!` made sense (and showed how much I rely on forced downcasts!) but this one line needed to be fixed manually.

_Note:_ Your mileage may vary with the migrator on your own projects, of course. Feel free to share your experiences on our forums!

## What does this mean for tutorial updates?

We're very excited about these updates to Swift. However, we won't start updating our tutorials, books, and videos until the gold master (GM) release of Xcode 6.3 and Swift 1.2 at the earliest.

![To be updated sometime after the GM release of Xcode 6.3 and Swift 1.2 - stay tuned!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/12/Main_Thumb.png)

> _To be updated sometime after the GM release of Xcode 6.3 and Swift 1.2 - stay tuned!_

The team at Apple will continue to tweak things in future beta releases and in our experience, it's best to wait until the GM to get a good sense of what will ship. We'll still be keeping an eye on each new beta, and we can't wait to have our tutorials be compatible with the final release version of Swift 1.2!

If you've purchased PDF versions of _iOS 8 by Tutorials_, _Swift by Tutorials_, or any book released after and including _iOS 7 by Tutorials_, you'll receive updated versions _free of charge_ as and when they're released. You'll also see a note added to the top of our free tutorials stating which version of Xcode they're compatible with.

## Where to go from here?

Remember, Swift 1.2 is bundled with Xcode 6.3, which is still a beta - that means you can't ship your apps with it yet! But you can try things out on a copy of your project and get a feel for how much work you'll have to do after the final release.

In the meantime, why not try out the beta and see what you think about the changes to the language? You can always contribute back and file a radar with Apple to report a bug or make a feature request - there's nothing quite like the thrill of having your radar marked as a duplicate, except perhaps when it gets marked as "fixed" and you see your radar number in the next set of release notes. ;]

What do you like or dislike about Swift 1.2 so far? Let us know in the forum discussion below!
