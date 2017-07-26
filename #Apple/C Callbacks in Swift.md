# C Callbacks in Swift

_Captured: 2015-06-23 at 01:38 from [oleb.net](http://oleb.net/blog/2015/06/c-callbacks-in-swift/)_

A few years ago I wrote about [how to access the elements](http://oleb.net/blog/2012/12/accessing-pretty-printing-cgpath-elements/) of a `CGPath` or `UIBezierPath`. To do that, you call the `[CGPathApply`](https://developer.apple.com/library/ios/documentation/GraphicsImaging/Reference/CGPath/index.html#//apple_ref/c/func/CGPathApply) function and pass in a pointer to a callback function. `CGPathApply` then calls this callback for each path element.

If you wanted to do this in Swift 1.x, you were out of luck because there was no way to bridge a Swift function to a C function pointer. You had to write a small wrapper in C or Objective-C that encapsulated the callback function.

With Swift 2, it is now possible to do this fully natively in Swift. C function pointers are [imported into Swift as closures](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/InteractingWithCAPIs.html). You can pass any Swift closure or function with matching parameters to code that expects a C function pointer - with one massive caveat: unlike closures, C function pointers don't have the concept of capturing state. As a result, the compiler will only allow Swift closures that do not capture any outside state to be bridged to a C function pointer. Swift uses the new `@convention(c)` notation to indicate this calling convention.

[Download this article as a playground](http://oleb.net/media/c-callbacks-in-swift.playground.zip) to experiment directly with the code. The text in the playground is identical to the blog post. Requires Swift 2/Xcode 7.

# Accessing the Elements of a UIBezierPath

Let's take the familiar task of iterating over the elements of a path as an example.

## A Swiftified Data Structure

First, consider the data structures we have to deal with. `CGPathApply` will pass a pointer to a `[CGPathElement`](https://developer.apple.com/library/ios/documentation/GraphicsImaging/Reference/CGPath/index.html#//apple_ref/c/tdef/CGPathElement) to the callback function (or closure). This is a struct that contains a constant indicating the type of the path element and a C array of `CGPoint`s. The number of points in the array varies between 0 and 3 depending on the element type.

Working with `CGPathElement` in Swift is not very pleasant. The C array gets imported as a `UnsafeMutablePointer<CGPoint>` whose lifetime is limited to the callback function, so we'd have to copy its contents to somewhere else if we wanted to keep the data around. Moreover, a safer way to access the correct number of points for each element type would be nice.

A Swift `enum` with associated values for the points is ideal for this purpose. A custom initializer does the conversion from `CGPathElement`.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    27
    
    
    /// A Swiftified representation of a `CGPathElement`
    ///
    /// Simpler and safer than `CGPathElement` because it doesn’t use a C array for the associated points.
    public enum PathElement {
        case MoveToPoint(CGPoint)
        case AddLineToPoint(CGPoint)
        case AddQuadCurveToPoint(CGPoint, CGPoint)
        case AddCurveToPoint(CGPoint, CGPoint, CGPoint)
        case CloseSubpath
    
        init(element: CGPathElement) {
            switch UInt32(element.type) {
            case kCGPathElementMoveToPoint.rawValue:
                self = .MoveToPoint(element.points[0])
            case kCGPathElementAddLineToPoint.rawValue:
                self = .AddLineToPoint(element.points[0])
            case kCGPathElementAddQuadCurveToPoint.rawValue:
                self = .AddQuadCurveToPoint(element.points[0], element.points[1])
            case kCGPathElementAddCurveToPoint.rawValue:
                self = .AddCurveToPoint(element.points[0], element.points[1], element.points[2])
            case kCGPathElementCloseSubpath.rawValue:
                self = .CloseSubpath
            case let v:
                fatalError("Unknown path element type: \(v)")
            }
        }
    }
    

Next, let's add a nice string representation to our new data type for easier debugging.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    
    
    extension PathElement : CustomDebugStringConvertible {
        public var debugDescription: String {
            switch self {
            case let .MoveToPoint(point):
                return "\(point.x)\(point.y) moveto"
            case let .AddLineToPoint(point):
                return "\(point.x)\(point.y) lineto"
            case let .AddQuadCurveToPoint(point1, point2):
                return "\(point1.x)\(point1.y)\(point2.x)\(point2.y) quadcurveto"
            case let .AddCurveToPoint(point1, point2, point3):
                return "\(point1.x)\(point1.y)\(point2.x)\(point2.y)\(point3.x)\(point3.y) curveto"
            case .CloseSubpath:
                return "closepath"
            }
        }
    }
    

While we're at it, we should also make `PathElement` `Equatable` (because that's what [you should always do](https://developer.apple.com/videos/wwdc/2015/?id=414)).
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    
    
    extension PathElement : Equatable { }
    
    public func ==(lhs: PathElement, rhs: PathElement) -> Bool {
        switch(lhs, rhs) {
        case let (.MoveToPoint(l), .MoveToPoint(r)):
            return l == r
        case let (.AddLineToPoint(l), .AddLineToPoint(r)):
            return l == r
        case let (.AddQuadCurveToPoint(l1, l2), .AddQuadCurveToPoint(r1, r2)):
            return l1 == r1 && l2 == r2
        case let (.AddCurveToPoint(l1, l2, l3), .AddCurveToPoint(r1, r2, r3)):
            return l1 == r1 && l2 == r2 && l3 == r3
        case (.CloseSubpath, .CloseSubpath):
            return true
        case (_, _):
            return false
        }
    }
    

## Enumerating Path Elements

Now comes the interesting part. We'd like to extend `UIBezierPath` with a new computed property named `elements` that iterates over the path and returns an array of `PathElement`s. We know that we have to call `CGPathApply()` and pass it a closure that gets called for each element. Inside the closure, we need to convert the `CGPathElement` to a `PathElement` and store it somehow in an array. This last part is not as easy as it sounds because the C calling convention prevents the closure from accessing any variables from the surrounding context.

Since pure C implementations of this API face the same problem, `CGPathApply` takes one more argument in the form of a `void *` and passes this pointer on to the callback function. This enables the caller to pass an arbitrary piece of data (such as a pointer to an array) to the callback - exactly what we need.

`void *` gets imported into Swift as `[UnsafeMutablePointer<Void>`](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Reference/Swift_UnsafeMutablePointer_Structure/). We create a Swift array to hold the `PathElement` values and then call `[withUnsafeMutablePointer()`](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Reference/Swift_StandardLibrary_Functions/index.html#//apple_ref/swift/func/s:FSs24withUnsafeMutablePointeru0_rFTRq_FGVSs20UnsafeMutablePointerq__q0__q0_) to get a pointer to the array, which is valid inside the closure passed to the function. In this closure we can then put the call to `CGPathApply`. The final step in the inner path element callback closure is to cast the void pointer back to an `UnsafeMutablePointer<[PathElement]>` and access the array directly via its `memory` property. _(Note: I'm not entirely sure if this is the best way to make pass the array to the callback closure. If you know a better way, please let me know.)_

The full implementation looks like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    
    
    extension UIBezierPath {
        var elements: [PathElement] {
            var pathElements = [PathElement]()
            withUnsafeMutablePointer(&pathElements) { elementsPointer in
                CGPathApply(CGPath, elementsPointer) { (userInfo, nextElementPointer) in
                    let nextElement = PathElement(element: nextElementPointer.memory)
                    let elementsPointer = UnsafeMutablePointer<[PathElement]>(userInfo)
                    elementsPointer.memory.append(nextElement)
                }
            }
            return pathElements
        }
    }
    

## Loose Ends

Now that we have an array of path elements, it is trivial to turn `UIBezierPath` into a sequence. This allows users to iterate over the path with a `for element in path` loop or to call methods like `map` or `filter` directly on the path.
    
    
    1
    2
    3
    4
    5
    
    
    extension UIBezierPath : SequenceType {
        public func generate() -> AnyGenerator<PathElement> {
            return anyGenerator(elements.generate())
        }
    }
    

Finally, here is an implementation of a debug string representation for `UIBezierPath`, modeled after the output of `NSBezierPath` on OS X.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    
    
    extension UIBezierPath : CustomDebugStringConvertible {
        public override var debugDescription: String {
            let cgPath = self.CGPath;
            let bounds = CGPathGetPathBoundingBox(cgPath);
            let controlPointBounds = CGPathGetBoundingBox(cgPath);
    
            let description = "\(self.dynamicType)\n"
                + "    Bounds: \(bounds)\n"
                + "    Control Point Bounds: \(controlPointBounds)"
                + elements.reduce("", combine: { (acc, element) in
                    acc + "\n\(String(reflecting: element))"
                })
            return description
        }
    }
    

# Example

Let's try this with an example path:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    
    
    let path = UIBezierPath()
    path.moveToPoint(CGPoint(x: 0, y: 0))
    path.addLineToPoint(CGPoint(x: 100, y: 0))
    path.addLineToPoint(CGPoint(x: 50, y: 100))
    path.closePath()
    path.moveToPoint(CGPoint(x: 0, y: 100))
    path.addQuadCurveToPoint(CGPoint(x: 100, y: 100),
        controlPoint: CGPoint(x: 50, y: 200))
    path.closePath()
    path.moveToPoint(CGPoint(x: 100, y: 0))
    path.addCurveToPoint(CGPoint(x: 200, y: 0),
        controlPoint1: CGPoint(x: 125, y: 100),
        controlPoint2: CGPoint(x: 175, y: -100))
    path.closePath()
    

[ ![The example path](http://oleb.net/media/uibezierpath-example.png) ](http://oleb.net/media/uibezierpath-example.png)

> _The example path._

Now we can iterate over the path and print a description of each element:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    
    
    for element in path {
        debugPrint(element)
    }
    /* Output:
    0.0 0.0 moveto
    100.0 0.0 lineto
    50.0 100.0 lineto
    closepath
    0.0 100.0 moveto
    50.0 200.0 100.0 100.0 quadcurveto
    closepath
    100.0 0.0 moveto
    125.0 100.0 175.0 -100.0 200.0 0.0 curveto
    closepath
    */
    

Or we can count how many `closepath` commands there are in the path:
    
    
    1
    2
    3
    4
    
    
    let closePathCount = path.filter {
            element in element == PathElement.CloseSubpath
        }.count
    // -> 3
    

# Conclusion

Swift 2 automatically bridges C function pointers to closures. This makes it possible (and very convenient) to work with a large number of C APIs that take function pointers as callbacks. Because the C calling convention does not allow these closures to capture external state, you often have to pass external variables that your callback closure needs to access through a void pointer that many C APIs offer for this purpose. Doing this from Swift is a bit convoluted but entirely possible.
