# Swift's Implicitly Unwrapped Optionals

_Captured: 2015-11-19 at 15:01 from [codenugget.co](http://codenugget.co/2014/10/13/swift-implicitly-unwrapped-optionals.html)_

Like the majority of iOS and OS X developers, I'm genuinely excited about [Swift](https://developer.apple.com/swift/), the new programming language Apple dropped as big surprise on this year's [WWDC keynote](http://www.apple.com/apple-events/june-2014/). Due to other projects, I didn't had that much time to dig into Swift as much as I would have liked during the summer, but I read as much as I could about it.

One thing I kinda skipped (because I didn't really get it) were Swift's "[Implicitly Unwrapped Optionals"](https://developer.apple.com/library/ios/documentation/swift/conceptual/swift_programming_language/TheBasics.html#//apple_ref/doc/uid/TP40014097-CH5-XID_491). I mean, I got that it automatically unwraps your optionals, so instead of writing code like this
    
    
    let possibleString: String? = "An optional string."
    
    if let definiteString = assumedString {
        println(definiteString)
    }
    

you can write it like that:
    
    
    let assumedString: String! = "An optional string."
    
    if assumedString {
        println(definiteString)
    }
    

Well... okay. What gives?

Today I was trying to port some Objective-C code over to Swift, which contained a `CAShapeLayer`[1](http://codenugget.co/2014/10/13/swift-implicitly-unwrapped-optionals.html). Let's look at a simplified version of its contents:
    
    
    @interface Shape: CAShapeLayer
    
    @property (nonatomic, strong) NSString titleText;
    @property (nonatomic, strong) NSString subTitleText;
    
    @end
    
    @implementation
    
    - (id)init {
      if (self = [super init]) {
        self.titleText = @"A title";
        self.subTitleText = @"A subtitle";
    
        // ...
      }
    
      return self;
    }
    
    @end
    

That's easy enough, right? And since we know that every shape _must_ eventually have a `titleText` and a `subtitleText`, we will be doing this in a type safe way:
    
    
    class Shape: CAShapeLayer {
      let titleText: String
      let subtitleText: String
    
      override init() {
        super.init()
        titleText = "A title"
        subtitleText = "A subtitle"
      }
    }
    

As of Xode 6.0.1, the compiler will complain: `'required' initializer 'init(coder:)' must be provided by subclass of 'CAShapeLayer'`. Let's try to fix this by giving the compiler the required initializer it wants:
    
    
    class Shape: CAShapeLayer {
      let titleText: String
      let subtitleText: String
    
      override init() {
        super.init()
        titleText = "A title"
        subtitleText = "A subtitle"
      }
    
      required init(coder aDecoder: NSCoder) {
        super.init(coder:aDecoder)
      }
    }
    

Now the compiler will complain in both `init()` and `init(coder:)` that `Property 'self.titleText' not initialized at super.init call`. We now see the problem: **Swift classes require all non-optionals to be initialized at the end of an initializer call.**

Now with Swift's implicitly unwrapped optionals, this is easy to solve:
    
    
    class Shape: CAShapeLayer {
        let titleText: String!    // <--
        let subtitleText: String! // <--
    
        override init() {
            super.init()
            titleText = "A title"
            subtitleText = "A subtitle"
        }
    
        required init(coder aDecoder: NSCoder) {
            super.init(coder:aDecoder)
        }
    }
    

So here's my take on this: **Use implicitly unwrapped optionals in places where you know that those optionals "almost always" have a value.** Especially with `UIKit` subclasses, you'll have to deal with more than one initializer, and in most cases, it is just not possible to initialize everything before their super initializers return. That's how Apple does it in their APIs, and this is how you should do it.

The (inevitable) downside of this, of course, is that things now might fail at runtime, if you forgot to initialize everything that is necessary. Since the compiler just cannot predict what has to be initialized, there simply won't be any warnings displayed up front in Xcode in case some initializing is missing.
