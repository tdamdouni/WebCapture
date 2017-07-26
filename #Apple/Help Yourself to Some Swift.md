# Help Yourself to Some Swift

_Captured: 2015-12-11 at 01:29 from [bandes-stor.ch](http://bandes-stor.ch/blog/2015/11/28/help-yourself-to-some-swift/)_

One perk of being a programmer is that, if your tools don't do what you want, you can improve them yourself. Swift makes this particularly easy, providing several features which enable you to extend and customize the language in a way that feels natural.

In this post, I'm going to share a handful of examples where Swift has made my life better. My hope is that reading these will inspire you to recognize your own pain points with the language, and to take action. (But not without thinking!)

## Wrangling Repetitive Identifiers

Here's a convention you might be familiar with from Objective-C: enumeration values and string constants have very long, descriptive names.
    
    
    label.textAlignment = NSTextAlignmentCenter;Select All

(I'm reminded of the maxim from middle school science class: Repeat Question In Answer, or RQIA. _Which text alignment?_ **_Center text alignment._** Useful when the answer is read out of context, but redundant otherwise.)

Swift mitigates the redundancy, since enum values are accessed using dot-notation on the type name, which can be inferred if you omit it:
    
    
    label.textAlignment = NSTextAlignment.Center
    
    // More concisely:
    label.textAlignment = .CenterSelect All

But sometimes you're not using an enum, and you're stuck with a long-winded constructor.
    
    
    animation.timingFunction = CAMediaTimingFunction(name: kCAMediaTimingFunctionEaseInEaseOut)Select All

How many "timingFunction"s was that? Too many.

A less-well-known fact is that the abbreviated dot-notation works with _any_ static member of any type. Combined with the power to add custom properties in an extension…
    
    
    extension CAMediaTimingFunction
    {
        // This property will be initialized lazily the first time it's accessed.
        // (The @nonobjc is required to prevent the compiler from trying to
        //  generate a dynamic accessor for a static (therefore final) property.)
        @nonobjc static let EaseInEaseOut = CAMediaTimingFunction(name: kCAMediaTimingFunctionEaseInEaseOut)
    
        // Another option would be to use a computed property, which works just as well,
        // but is evaluated *every* time it's accessed:
        static var EaseInEaseOut: CAMediaTimingFunction {
            // .init is short for self.init
            return .init(name: kCAMediaTimingFunctionEaseInEaseOut)
        }
    }Select All

We've got ourselves a very nice shorthand:

### In Context

Code that deals with Core Graphics contexts, color spaces, etc. also tends to be long-winded.
    
    
    CGContextSetFillColorWithColor(UIGraphicsGetCurrentContext(),
        CGColorCreate(CGColorSpaceCreateWithName(kCGColorSpaceGenericRGB), [0.792, 0.792, 0.816, 1]))Select All

Again, with feeling extensions:
    
    
    extension CGContext
    {
        static func currentContext() -> CGContext? {
            return UIGraphicsGetCurrentContext()
        }
    }
    
    extension CGColorSpace
    {
        static let GenericRGB = CGColorSpaceCreateWithName(kCGColorSpaceGenericRGB)
    }
    
    CGContextSetFillColorWithColor(.currentContext(),
        CGColorCreate(.GenericRGB, [0.792, 0.792, 0.816, 1]))Select All

Much easier now. And certainly, there are [many more ways](https://developer.apple.com/videos/play/wwdc2015-408/) to extend the Core Graphics types to suit your needs.

### Auto Layout

Does this look familiar?
    
    
    spaceConstraint = NSLayoutConstraint(
        item: label,
        attribute: .Leading,
        relatedBy: .Equal,
        toItem: button,
        attribute: .Trailing,
        multiplier: 1, constant: 20)
    widthConstraint = NSLayoutConstraint(
        item: label,
        attribute: .Width,
        relatedBy: .LessThanOrEqual,
        toItem: nil,
        attribute: .NotAnAttribute,
        multiplier: 0, constant: 200)
    
    spaceConstraint.active = true
    widthConstraint.active = trueSelect All

Hard to read, isn't it? Apple realized this was a common problem, and designed the new NSLayoutAnchor APIs (available in iOS 9 and OS X 10.11) to mitigate it:
    
    
    spaceConstraint = label.leadingAnchor.constraintEqualToAnchor(button.trailingAnchor, constant: 20)
    widthConstraint = label.widthAnchor.constraintLessThanOrEqualToConstant(200)
    spaceConstraint.active = true
    widthConstraint.active = trueSelect All

However, I think we can do better. In my mind, this is much easier to read and use than the built-in APIs:
    
    
    spaceConstraint = label.constrain(.Leading, .Equal, to: button, .Trailing, plus: 20)
    widthConstraint = label.constrain(.Width, .LessThanOrEqual, to: 200)
    
    // "Make the label's leading edge equal to the button's trailing edge, plus an extra space of 20."
    // "Make the label's width less than or equal to 200."Select All

This is made possible by a couple extensions on UIView or NSView. These helper functions may look a bit long and unwieldy, but they're easy to use, and can easily pay for themselves in maintainability. (Here I've actually included some extra parameters with default values -- a `multiplier`, `priority`, and `identifier` -- so you can optionally customize the constraints even further.)
    
    
    extension UIView
    {
        func constrain(
            attribute: NSLayoutAttribute,
            _ relation: NSLayoutRelation,
            to otherView: UIView,
            _ otherAttribute: NSLayoutAttribute,
            times multiplier: CGFloat = 1,
            plus constant: CGFloat = 0,
            atPriority priority: UILayoutPriority = UILayoutPriorityRequired,
            identifier: String? = nil)
            -> NSLayoutConstraint
        {
            let constraint = NSLayoutConstraint(
                item: self,
                attribute: attribute,
                relatedBy: relation,
                toItem: otherView,
                attribute: otherAttribute,
                multiplier: multiplier,
                constant: constant)
            constraint.priority = priority
            constraint.identifier = identifier
            constraint.active = true
            return constraint
        }
        
        func constrain(
            attribute: NSLayoutAttribute,
            _ relation: NSLayoutRelation,
            to constant: CGFloat,
            atPriority priority: UILayoutPriority = UILayoutPriorityRequired,
            identifier: String? = nil)
            -> NSLayoutConstraint
        {
            let constraint = NSLayoutConstraint(
                item: self,
                attribute: attribute,
                relatedBy: relation,
                toItem: nil,
                attribute: .NotAnAttribute,
                multiplier: 0,
                constant: constant)
            constraint.priority = priority
            constraint.identifier = identifier
            constraint.active = true
            return constraint
        }
    }Select All

## Hello Operators

I have to lead with a word of warning: **please think carefully** before using custom operators. It's easy to make use of them, but you might end up with an unreadable mess. Do apply healthy skepticism, and I think you'll still find there are some places where custom operators truly make sense.

### Overload 'em

If you've ever made something draggable, you've probably written code like this:
    
    
    // Touches began / mouse down:
    
    let touchPos = touch.locationInView(container)
    objectOffset = CGPoint(x: object.center.x - touchPos.x, y: object.center.y - touchPos.y)
    
    // Touches moved / mouse dragged:
    
    let touchPos = touch.locationInView(container)
    object.center = CGPoint(x: touchPos.x + objectOffset.x, y: touchPos.y + objectOffset.y)Select All

Here we're just doing simple addition and subtraction, but because CGPoint [comprises](https://en.wikipedia.org/wiki/User:Giraffedata/comprised_of) both `x` and `y`, we have to write each expression twice. This calls for some convenience functions.

`objectOffset` represents the difference between the touch position and the object's position. The best way to express a difference like this is actually not CGPoint, but the lesser-known [CGVector](https://developer.apple.com/library/ios/documentation/GraphicsImaging/Reference/CGGeometry/#//apple_ref/c/tdef/CGVector), which instead of `x` and `y` has `dx` and `dy` representing differences or "deltas".

So it's logical that subtracting two points should produce a vector, and to that end we can overload the `-` operator:
    
    
    /// - Returns: The vector directed from `rhs` to `lhs`.
    func -(lhs: CGPoint, rhs: CGPoint) -> CGVector
    {
        return CGVector(dx: lhs.x - rhs.x, dy: lhs.y - rhs.y)
    }Select All

And, inversely, adding a vector to a point gives you another point:
    
    
    /// - Returns: The point `lhs` offset by `rhs`.
    func +(lhs: CGPoint, rhs: CGVector) -> CGPoint
    {
        return CGPoint(x: lhs.x + rhs.dx, y: lhs.y + rhs.dy)
    }Select All

Now this is readable!
    
    
    // Touches began:
    objectOffset = object.center - touch.locationInView(container)
    
    // Touches moved:
    object.center = touch.locationInView(container) + objectOffsetSelect All

**Exercise:** think about what other operators might be useful for points and vectors, and implement them. Suggestions: `-(CGPoint, CGVector)`, `*(CGVector, CGFloat)`, and `-(CGVector)`. 

### Roll your own

Here's something a little more creative. Swift provides several _compound assignment operators_ which perform an operation and assignment at the same time:
    
    
    a += b   // equivalent to "a = a + b"
    a %= b   // equivalent to "a = a % b"Select All

But there are other operators which don't have built-in compound-assignment forms. A common example is `??`, the nil-coalescing operator. [Ruby's `||=`](http://ruby-doc.org/docs/ruby-doc-bundle/Manual/man-1.4/syntax.html#assign), for example, only performs assignment if the variable is nil (or false) to begin with. This makes good sense with Swift's Optionals, and it's easy to add:
    
    
    infix operator ??= { associativity right precedence 90 assignment } // matches other assignment operators
    
    /// If `lhs` is `nil`, assigns to it the value of `rhs`.
    func ??=<T>(inout lhs: T?, @autoclosure rhs: () -> T)
    {
        lhs = lhs ?? rhs()
    }Select All

That might look daunting -- there are several things going on here.

  * The `infix operator` declaration tells Swift to treat `??=` as an operator.

  * Making the function generic with `<T>` makes it work for any type of value.

  * `inout` allows it to modify the left-hand operand.

  * `@autoclosure` allows for [short-circuit evaluation](https://en.wikipedia.org/wiki/Short-circuit_evaluation), only evaluating the right-hand side if it's needed. (This also relies on the short-circuiting nature of `??` itself.)

But the result, in my opinion, is clear and easy to use:

## Dispatched

Note: A proper Swift treatment of Grand Central Dispatch deserves its own article, but I'll cover some basics here. You can find some more ideas in [this Gist](https://gist.github.com/jtbandes/a5ce62019585dd4f998e).

Swift 2 brought [protocol extensions](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Protocols.html#//apple_ref/doc/uid/TP40014097-CH25-ID521), and thereby, many previously-global standard library functions became quasi-member functions: `map(seq, transform)` is now `seq.map(transform)`, `join(separator, seq)` is now `seq.joinWithSeparator(separator)`, and so forth. This way, functions which aren't _technically_ instance methods on a class can still be used with dot-notation, reducing the number of parentheses [cluttering up](https://xkcd.com/297/) the code.

Such gains weren't afforded, however, to free functions outside of the Swift standard library, like `dispatch_async()` and `UIImageJPEGRepresentation()`. These still feel clunky to use, and if you use them a lot, it's worth thinking about how to help Swift help you. Here are some GCD examples to start with.

### A `sync` or not `async`

These are simple; let's jump right in:
    
    
    extension dispatch_queue_t
    {
        final func async(block: dispatch_block_t) {
            dispatch_async(self, block)
        }
        
        // `block` should be @noescape here, but can't be <<http://openradar.me/19770770>>
        final func sync(block: dispatch_block_t) {
            dispatch_sync(self, block)
        }
    }Select All

These two conveniences call directly into the normal dispatch functions, but allow us to use them with dot-notation, which we couldn't do before.

Note: By a weirdness of the way GCD objects are exposed to Swift, `dispatch_queue_t` is actually a protocol, although this would work just as well if it had been a class. I've marked the functions `final` here to signal our intent that dynamic dispatch shouldn't be used, although my understanding is that protocol extensions, in situations like this one, [don't really use it anyway](http://nomothetis.svbtle.com/the-ghost-of-swift-bugs-future).
    
    
    mySerialQueue.sync {
        print("I’m on the queue!")
        threadsafeNum++
    }
    
    dispatch_get_global_queue(QOS_CLASS_BACKGROUND, 0).async {
        expensivelyReticulateSplines()
        print("Done!")
        
        dispatch_get_main_queue().async {
            print("Back on the main queue.")
        }
    }Select All

A slightly more advanced version of `sync`, taking cues from the `with*` family of Swift standard library functions, lets us return a value that's computed inside the block:
    
    
    extension dispatch_queue_t
    {
        final func sync<Result>(block: () -> Result) -> Result {
            var result: Result?
            dispatch_sync(self) {
                result = block()
            }
            return result!
        }
    }
    
    // Grab some data while on the serial queue
    let currentItems = mySerialQueue.sync {
        print("I’m on the queue!")
        return mutableItems.copy()
    }Select All

### Groupthink

Another two simple extensions let us play nicely with [dispatch groups](https://developer.apple.com/library/ios/documentation/General/Conceptual/ConcurrencyProgrammingGuide/OperationQueues/OperationQueues.html#//apple_ref/doc/uid/TP40008091-CH102-SW30):
    
    
    extension dispatch_queue_t
    {
        final func async(group: dispatch_group_t, _ block: dispatch_block_t) {
            dispatch_group_async(group, self, block)
        }
    }
    
    extension dispatch_group_t
    {
        final func waitForever() {
            dispatch_group_wait(self, DISPATCH_TIME_FOREVER)
        }
    }Select All

Now an additional `group` parameter can be included along with a regular call to `async`.
    
    
    let group = dispatch_group_create()
    
    concurrentQueue.async(group) {
        print("I’m part of the group")
    }
    
    concurrentQueue.async(group) {
        print("I’m independent, but part of the same group")
    }
    
    group.waitForever()
    print("Everything in the group has now executed")Select All

Note: We could have chosen `group.async(queue)` just as easily as `queue.async(group)`. Which one is preferable is a matter of opinion -- you could even choose to implement both.

## Refined & Elegant

If your project has both Objective-C and Swift, you may encounter an awkward moment when an Obj-C API just doesn't feel _Swifty_ enough. `NS_REFINED_FOR_SWIFT` to the rescue.

Functions, methods, and variables marked with this macro [(new in Xcode 7)](https://developer.apple.com/library/ios/releasenotes/DeveloperTools/RN-Xcode/Chapters/xc7_release_notes.html) are used as normal in Obj-C code, but when exposed to Swift, they're prefixed with "`__`".
    
    
    @interface MyClass : NSObject
    
    /// @return The index of the given @c thing, or NSNotFound if it's not present.
    - (NSUInteger)indexOfThing:(id)thing NS_REFINED_FOR_SWIFT;
    
    @end
    
    // When exposed to Swift, this becomes:
    
    public class MyClass: NSObject
    {
        public func __indexOfThing(thing: AnyObject) -> UInt
    }
    Select All

With the Obj-C method moved aside, you can reuse the same name to provide a more Swift-friendly API (often implemented by calling the now-underscored original version):
    
    
    extension MyClass
    {
        /// - Returns: The index of the given `thing`, or `nil` if it's not present.
        func indexOfThing(thing: AnyObject) -> Int?
        {
            let idx = Int(__indexOfThing(thing)) // call the original method
            if idx == NSNotFound { return nil }
            return idx
        }
    }Select All

Now you can "`if let`" to your heart's content!

Swift is young, and each codebase is different. A multitude of micro-libraries have popped up, and with them each author's differing opinions on operators, helper functions, and naming conventions. This landscape calls for a critical eye when pulling in dependencies and settings standards within teams.

The best reason to take advantage of the techniques here is not in order to write the coolest, hippest Swift code. Surely, someone else who maintains your work -- possibly your future self -- will see it a different way. For their sake, dear reader, extend Swift not when it is easy, but when it is clear and sensible.
