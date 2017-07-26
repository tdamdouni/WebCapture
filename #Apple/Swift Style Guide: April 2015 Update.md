# Swift Style Guide: April 2015 Update

_Captured: 2015-11-25 at 20:36 from [www.raywenderlich.com](http://www.raywenderlich.com/102357/swift-style-guide-april-2015-update)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Swift style guide: updated for Swift 1.2!](http://cdn4.raywenderlich.com/wp-content/uploads/2015/04/style-guide-201504-250x250.png)

> _Swift style guide: updated for Swift 1.2!_

This is an exciting week for iOS developers - Swift 1.2 came out of beta with the release of Xcode 6.3, which is now available on the App Store!

Swift 1.2 brings faster compiles, more concise syntax, an improved `if let` statement, and more. If you're not familiar with the changes, check out our post on [What's New in Swift 1.2](http://www.raywenderlich.com/95181/whats-new-in-swift-1-2).

Our goal is to stay on top of changes to Swift and iOS - we are in the process of updating our books and tutorials to Swift 1.2.

One of the things we've already updated is our [raywenderlich.com Swift style guide](https://github.com/raywenderlich/swift-style-guide). We've made some changes for Swift 1.2, and some other changes based on pull requests and issues filed from team members and readers.

Let's dive in and see what changed!

_Note_: Our style guide is different than other style guides out there; we're a tutorial site, which means our priorities are shorter and more readable code for printed books and the web. Many of the decisions were made with an eye toward conserving space for print, legibility, and tutorial writing.

## Multiple Optional Binding

Swift 1.2 now allows you to optionally bind multiple things in one line. Our style guide recommends using this new style, rather than the old style of multiple `if let` statements:
    
    
    // old
    if let widget = widget {
      if let url = options.url {
        if let host = options.host {
          // widget, url, and host are all non-optionals
        }
      }
    }
     
    // new
    if let widget = widget, url = options.url, host = options.host {
      // widget, url, and host are all non-optionals
    }

This new syntax lets you avoid the "pyramid of doom" when you had to test and bind several optionals.

![So many spaces saved!](http://cdn4.raywenderlich.com/wp-content/uploads/2015/02/TooManyLabels.png)

> _So many spaces saved!_

Note you can also include boolean conditions in your `if let` statements, which can make your code more concise as well.

## Enumerations and Case

After a good amount of discussion, we formalized the style we were using in our tutorials: UpperCamelCase for enumeration values.
    
    
    enum Language {
      case Swift
      case ObjectiveC
      case ObjectOrientedFortran
    }

There's a bit of an inconsistency since enum values are like class constants inside the enum scope, and feel like they should be in lower-camel case. However, the style guide usage matches our general practice, existing enumerations in Cocoa, and Swift itself - remember, optionals are implemented as enums with values `Some` and `None` which begin with a capital letter.

## Trailing Closures

Trailing closures are great for keeping the closure expression linked to its function call, without having to wrap them in the argument parentheses.
    
    
    UIView.animateWithDuration(0.75) {
      self.dogeImage.alpha = 1.0
    }

Our old guidance was to use trailing closures wherever possible. However, there's one special case where this isn't a good idea: when there are _two_ closure arguments! In that case, you should use the normal syntax to keep both closure expressions "on the same level" with named arguments:
    
    
    UIView.animateWithDuration(1.0, animations: {
      self.myView.alpha = 0
    }, completion: { finished in
      self.myView.removeFromSuperview()
    })

The alternative is to have one named and one trailing, which looks strange and we recommend against.
    
    
    // Don't do this!
    UIView.animateWithDuration(1.0, animations: {
      self.myView.alpha = 0
    }) { f in
      self.myView.removeFromSuperview()
    }

## Function and Method Naming

As in Objective-C, a full, unambiguous function signature includes the method name and its named arguments. When referring to a function in a tutorial, we follow the same formatting as you see in the Xcode jump bar:

![xcode-jump](http://cdn2.raywenderlich.com/wp-content/uploads/2015/04/xcode-jump.png)

Previously, we said it was OK to write just the bare function name if the context was clear. That allowed us to write `viewDidAppear` rather than the full `viewDidAppear(_:)`.

After some discussion, we decided it was best to be clear about whether something was a function or a variable. The new guideline is to _always_ include the full signature. That means something like `viewDidLoad()` where there are no arguments, and `tableView(_:cellForRowAtIndexPath:)` where there are arguments.

## MARK

In the last style guide update, we introduced the rule of one extension per protocol. That keeps the protocol conformance together with the protocol methods, and makes adding and finding related code easier.

As an addition to that rule, we want to start adding `MARK` comments to provide better navigation.
    
    
    // MARK: - UITableViewDataSource
     
    extension MyTableViewController: UITableViewDataSource {
      // table view data source methods here...
    }

Extensions are great for grouping methods together, and the `MARK` comment should help navigating your way around source files even easier than before!

![Code flows out much easier when your files are well organized!](http://cdn2.raywenderlich.com/wp-content/uploads/2015/04/rainbows.png)

> _Code flows out much easier when your files are well organized!_

## Shadowing

Speaking of optional binding, one thing that hasn't changed in the style guide is that we use the same name for the optional and the unwrapped version:
    
    
    var subview: UIView?
     
    // later...
    if let subview = subview {
      // referring to "subview" here is the unwrapped version
    }

The benefit is that the names remain short and we avoid things like `maybeView` and `unwrappedWidget` and `optionalTableView`. Once you understand Swift and optionals, the code makes sense. The downside is that the code just looks strange and can be hard to read and understand for beginners.

The [issue thread on variable shadowing](https://github.com/raywenderlich/swift-style-guide/issues/75) is still there and we're open to change things if you're especially convincing. "Especially convincing" includes offers of an Apple Watch Edition, of course. ;]

## Where to Go From Here?

"_Style is a simple way of saying complicated things_," said the French writer Jean Cocteau. That's what programming is really about, isn't it? -- complicated algorithms and app logic, expressed in an understandable way through code. I hope our site's coding style helps you understand the sometimes complicated things we're trying to teach as you expand your knowledge in Swift development.

Swift 1.3 and 2.0 and beyond are surely in the works and we'll keep adapting to provide you with a consistent and readable style. As Swift evolves, why not get involved yourself? File radars on parts of the language you think should be changed, and join in the discussion at our [Swift style guide](https://github.com/raywenderlich/swift-style-guide) repository on GitHub.

If you've left a comment, filed a new issue, or even sent in a pull request - thank you! Please keep the feedback coming. If you have a general question or comment, join in the forum discussion below!
