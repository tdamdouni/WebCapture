# Using Nullable to Annotate Objective-C Code

_Captured: 2016-01-10 at 19:54 from [useyourloaf.com](http://useyourloaf.com/blog/using-nullable-to-annotate-objective-c.html)_

If you have tried and tested Objective-C code you do not need to rewrite it to use it in a Swift project. Unfortunately unless you take some extra steps the resulting Swift interface will treat all Objective-C references as _implicitly unwrapped optionals_. All those "!" symbols make for some ugly and unsafe Swift code.

Fortunately there is a quick fix if you annotate your Objective-C header file with **nullable** and **nonnull**.

### Viewing the Swift interface with Xcode

_Before we look at annotating our Objective-C code here is a quick Xcode tip to view the Swift interface for an Objective-C header file._

If you are viewing an Objective-C header file in Xcode and switch to the Assistant Editor you can find the Swift interface file in the counterparts menu - look for the "(Interface)" file. This will cause Xcode to import the Objective-C code and create the corresponding Swift interface:

![Xcode assistant editor](http://useyourloaf.com/assets/images/2016/2016-01-08-001.png)

> _Xcode assistant editor_

### Implicitly Unwrapped Optionals!

So let's see what the default Swift interface is for an Objective-C class that we have not yet annotated. Here is a simple interface for a class with a single property, an initializer and an instance method:
    
    
    @interface Robot : NSObject
    @property (copy,readonly) NSString *name;
    - (instancetype)initWithName:(NSString *)name;
    - (NSString *)tellMeSomething;
    @end

If we use Xcode to preview the Swift interface for this class this is what we get:
    
    
    public class Robot : NSObject {    
      public var name: String! { get }
      public init!(name: String!)
      public func tellMeSomething() -> String!
    }

Notice how the references from the Objective-C code appear as implicitly unwrapped optionals in the Swift code. The problem comes from the different ways Objective-C and Swift handle NULL or nil values. It is common in Objective-C to return nil for an object reference where in Swift you would use an optional type.

Unfortunately there is nothing in the Objective-C code that tells the compiler which references can be nil so it assumes the worst and makes everything an implicitly unwrapped optional.

### Nullability Annotations

There are two annotations we can apply to our Objective-C code to improve this situation:

  * Marking types as **nonnull** imports them as **non-optional** in Swift.
  * Marking types as **nullable** imports them as **optional** in Swift.

#### Properties

Consider first the name property in our class. This is a readonly string that we want to initialise when we create the object so it should not be nil. We can document that by marking it with nonnull:
    
    
    @property (nonnull,copy,readonly) NSString *name;

This changes the Swift code to give us a normal, non-optional variable:
    
    
    public var name: String { get }

#### Initializers

Next let's look at the initializer. It has an NSString name parameter which should not be nil so we again mark that as nonnull. What about the instancetype return type? That depends on whether this initializer can fail and return nil or not. If it can we need to mark it as nullable as follows:
    
    
    - (nullable instancetype)initWithName:(nonnull NSString *)name;

The Swift code now knows that the return type is an optional:
    
    
    public init?(name: String)

If the initialization cannot fail and always returns a value we would use nonnull to import to Swift as a non-optional init function:
    
    
    // - (nonnull instancetype)initWithName:(nonnull NSString *)name;
    public init(name: String)

#### Methods

Finally let's assume that our method can return a nil value and annotate it as such:
    
    
    - (nullable NSString *)tellMeSomething;

This gives us a function with an optional return type in Swift:
    
    
    public func tellMeSomething() -> String?

### Saving Some Time

Once you add a single annotation to a header file Xcode expects you to annotate the whole interface. Expect a lot of warnings if you don't:

This is a big pain, but there is a shortcut. Most of the time we tend to want nonnull references. We can make that the default for a region of code by using **NS_ASSUME_NONNULL_BEGIN** and **NS_ASSUME_NONNULL_END**.

**We then only need to add nullable annotations for references that can be nil.** Our annotated class now looks like this:
    
    
    NS_ASSUME_NONNULL_BEGIN
    @interface Robot : NSObject
    @property (copy,readonly) NSString *name;
    - (nullable instancetype)initWithName:(NSString *)name;
    - (nullable NSString *)tellMeSomething;
    @end
    NS_ASSUME_NONNULL_END

The final Swift interface looks like this:
    
    
    public class Robot : NSObject {
      public var name: String { get }
      public init?(name: String)
      public func tellMeSomething() -> String?
    }

### Further Reading

  * [Nullability and Objective-C](https://developer.apple.com/swift/blog/?id=25) from the Apple Developer Swift Blog
  * [Using Swift with Cocoa and Objective-C (Swift 2.1)](https://itunes.apple.com/gb/book/using-swift-cocoa-objective/id888894773?mt=11) See the section on Nullability and Optionals
