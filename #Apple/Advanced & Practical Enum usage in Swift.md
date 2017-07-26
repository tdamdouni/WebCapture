# APPVENTURE

_Captured: 2015-10-23 at 15:24 from [appventure.me](http://appventure.me/)_

### [Advanced & Practical Enum usage in Swift](http://appventure.me/2015/10/17/advanced-practical-enum-examples/)

When and how to use enums in Swift? This is a detailed practical overview of all the possibilities enums can offer you.

Similarly to the `[switch` statement](http://appventure.me/2015/08/20/swift-pattern-matching-in-detail/), `enum`'s in Swift may at first glance look like a slightly improved variant of the well known **C** `enum` statement. I.e. a type that allows you to define that something is "one of something more general". However, upon close introspection, the particular design decisions behind Swift's enums allow it to be used in a much wider range of practical scenarios than plain **C** enums. In particular, they're great tools to clearly manifest the intentions of your code.

In this post, we'll first look at the syntax and possibilities of using `enum`, and will then use them in a variety of (hopefully) practical, real world scenarios to give a better idea of how and when to use them. We'll also look a bit at how enums are being used in the Swift Standard library.

Before we dive in, here's a definition of what `enums` can be. We'll revisit this definition later on:

"Enums declare types with finite sets of possible states and accompanying values. With nesting, methods, associated values, and pattern matching, however, enums can define any hierarchically organized data."

##  Diving In

###  Defining Basic Enums

We're working on a game, and the player can move in four directions. So our player movement is restricted. Obviously, we can use an enum for that.
    
    
    enum Movement {
    case Left
    case Right
    case Top
    case Bottom
    }
    

You can then use [various pattern matching constructs](http://appventure.me/2015/08/20/swift-pattern-matching-in-detail/) to retrieve the value of a `Movement`, or act upon a specific case:
    
    
    let aMovement = Movement.Left
    
    switch aMovement {
    case .Left: print("left")
    default: ()
    }
    
    if case .Left = aMovement { print("left") }
    
    if aMovement == .Left { print("left") }
    

Note that you don't have to specify the actual name of the `enum` (i.e. `case Movement.Left: print("Left")` in this case. The type checker figures that out automatically. This is extremely helpful for some of those convoluted **UIKit** or **AppKit** enums.

Of course, you may want to have a value assigned to each `enum` case. This is useful if the `enum` itself indeed relates to something which can be expressed in a different type. **C** allows you to assign numbers to `enum cases`. Swift gives you much more flexibility here:
    
    
    // Mapping to Integer
    enum Movement: Int {
        case Left = 0
        case Right = 1
        case Top = 2
        case Bottom = 3
    }
    
    // You can also map to strings
    enum House: String {
        case Baratheon = "Ours is the Fury"
        case Greyjoy = "We Do Not Sow"
        case Martell = "Unbowed, Unbent, Unbroken"
        case Stark = "Winter is Coming"
        case Tully = "Family, Duty, Honor"
        case Tyrell = "Growing Strong"
    }
    
    // Or to floating point (also note the fancy unicode in enum cases)
    enum Constants: Double {
        case π = 3.14159
        case e = 2.71828
        case φ = 1.61803398874
        case λ = 1.30357
    }
    

For `String` and `Int` types, you can even omit the values and the Swift compiler will do the right thing:
    
    
    // Mercury = 1, Venus = 2, ... Neptune = 8
    enum Planet: Int {
        case Mercury = 1, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
    }
    
    // North = "North", ... West = "West"
    enum CompassPoint: String {
        case North, South, East, West
    }
    

Swift supports the following types for the value of an enum:

  * Integer 
  * Floating Point 
  * String 
  * Boolean 

So you won't be able[1](http://appventure.me) to use, say, a CGPoint as the value of your enum.

If you want to access the values, you can do so with the `rawValue` property:
    
    
    let bestHouse = House.Stark
    print(bestHouse.rawValue)
    // prints "Winter is coming"
    

However, there may also be a situation where you want to construct an `enum case` from an existing raw value. In that case, there's a special initializer for enums:
    
    
    enum Movement: Int {
        case Left = 0
        case Right = 1
        case Top = 2
        case Bottom = 3
    }
    // creates a movement.Right case, as the raw value for that is 1
    let rightMovement = Movement(rawValue: 1)
    

If you use the `rawValue` initializer, keep in mind that it is a [failable initializer](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Declarations.html#//apple_ref/doc/uid/TP40014097-CH34-ID376), i.e. you get back an [Optional](http://appventure.me/2014/06/13/swift-optionals-made-simple/), as the value you're using may not map to any case at all, say if you were to write `Movement(rawValue: 42)`.

This is a very useful feature in case you want to encode low level C binary representations into something much more readable. As an example, have a look as this encoding of the **VNode Flags** for [the BSD kqeue library](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man2/kqueue.2.html):
    
    
    enum VNodeFlags : UInt32 {
        case Delete = 0x00000001
        case Write = 0x00000002
        case Extended = 0x00000004
        case Attrib = 0x00000008
        case Link = 0x00000010
        case Rename = 0x00000020
        case Revoke = 0x00000040
        case None = 0x00000080
    }
    

This allows you to use the much nicer looking **Delete** or **Write** cases, and later on hand the raw value into the **C** function only when it is really needed.

If you have specific sub type requirements, you can also logically nest enums in an enum. This allows you to contain specific information on your enum case within the actual enum. Imagine a character in an RPG. Each character can have a weapon, all characters have access to the same set of weapons. All other instances in the game do not have access to those weapons (they're trolls, they just have clubs).
    
    
    enum Character {
      enum Weapon {
        case Bow
        case Sword
        case Lance
        case Dagger
      }
      enum Helmet {
        case Wooden
        case Iron
        case Diamond
      }
      case Thief
      case Warrior
      case Knight
    }
    

Now you have a hierachical system to describe the various items that your character has access to.
    
    
    let character = Character.Thief
    let weapon = Character.Weapon.Bow
    let helmet = Character.Helmet.Iron
    

In a similar vein, you can also embed enums in `structs` or `classes`. Continuing with our previous example:
    
    
    struct Character {
       enum CharacterType {
        case Thief
        case Warrior
        case Knight
      }
      enum Weapon {
        case Bow
        case Sword
        case Lance
        case Dagger
      }
      let type: CharacterType
      let weapon: Weapon
    }
    
    let warrior = Character(type: .Warrior, weapon: .Sword)
    

This, again, helps in keeping related information together.

###  Associated Values

####  Simple Example
    
    
    enum Trade {
        case Buy
        case Sell
    }
    func trade(tradeType: Trade, stock: String, amount: Int) {}
    

However, the stock and amount clearly belong to the trade in question, having them as separate parameters feels unclean. You could embed it into a `struct`, but associated values allow for a much cleaner solution:
    
    
    enum Trade {
        case Buy(stock: String, amount: Int)
        case Sell(stock: String, amount: Int)
    }
    func trade(type: Trade) {}
    

####  Pattern Matching

####  Labels

Associated values do not require labels:
    
    
    enum Trade {
       case Buy(String, Int)
       case Sell(String, Int)
    }
    

If you add them, though, you'll have to type them out when creating your enum cases.

####  Tuples as Arguments

What's more, the Swift internal associated information is just a `Tuple`, so you can do things like this:
    
    
    let tp = (stock: "TSLA", amount: 100)
    let trade = Trade.Sell(tp)
    
    if case let Trade.Sell(stock, amount) = trade {
        print("buy \(amount) of \(stock)")
    }
    // Prints: "buy 100 of TSLA"
    

This syntax allows you to take `Tuples` as a simple data structure and later on automatically elevate them into a higher type like a `enum case`. Imagine an app where a user can configure a Desktop that he wants to order:
    
    
    typealias Config = (RAM: Int, CPU: String, GPU: String)
    
    // Each of these takes a config and returns an updated config
    func selectRAM(_ config: Config) -> Config {return (RAM: 32, CPU: config.CPU, GPU: config.GPU)}
    func selectCPU(_ config: Config) -> Config {return (RAM: config.RAM, CPU: "3.2GHZ", GPU: config.GPU)}
    func selectGPU(_ config: Config) -> Config {return (RAM: config.RAM, CPU: "3.2GHZ", GPU: "NVidia")}
    
    enum Desktop {
       case Cube(Config)
       case Tower(Config)
       case Rack(Config)
    }
    
    let aTower = Desktop.Tower(selectGPU(selectCPU(selectRAM((0, "", "") as Config))))
    

Each step of the configuration updates a `tuple` which is handed in to the `enum` at the end. This works even better if we take a hint from **functional programming** apply [2](http://appventure.me):
    
    
    infix operator <^> { associativity left }
    
    func <^>(a: Config, f: (Config) -> Config) -> Config { 
        return f(a)
    }
    

Finally, we can thread through the different configuration steps. This is particularly helpful if you have many of those steps.
    
    
    let config = (0, "", "") <^> selectRAM  <^> selectCPU <^> selectGPU
    let aCube = Desktop.Cube(config)
    

####  Use Case Examples

Associated Values can be used in a variety of ways. As code can tell more than a thousand words, what follows is a list of short examples in no particular order.
    
    
    // Cases can have different values
    enum UserAction {
      case OpenURL(url: NSURL)
      case SwitchProcess(processId: UInt32)
      case Restart(time: NSDate?, intoCommandLine: Bool)
    }
    
    // Or image you're implementing a powerful text editor that allows to have
    // multiple selections, like Sublime Text here:
    // https://www.youtube.com/watch?v=i2SVJa2EGIw
    enum Selection {
      case None
      case Single(Range<Int>)
      case Multiple([Range<Int>])
    }
    
    // Or mapping different types of identifier codes
    enum Barcode {
        case UPCA(numberSystem: Int, manufacturer: Int, product: Int, check: Int)
        case QRCode(productCode: String)
    }
    
    // Or, imagine you're wrapping a C library, like the Kqeue BSD/Darwin notification
    // system: https://www.freebsd.org/cgi/man.cgi?query=kqueue&sektion=2
    enum KqueueEvent {
        case UserEvent(identifier: UInt, fflags: [UInt32], data: Int)
        case ReadFD(fd: UInt, data: Int)
        case WriteFD(fd: UInt, data: Int)
        case VnodeFD(fd: UInt, fflags: [UInt32], data: Int)
        case ErrorEvent(code: UInt, message: String)
    }
    
    // Finally, all user-wearable items in an RPG could be mapped with one
    // enum, that encodes for each item the additional armor and weight
    // Now, adding a new material like 'Diamond' is just one line of code and we'll have the option to add several new Diamond-Crafted wearables.
    enum Wearable {
        enum Weight: Int {
    	case Light = 1
    	case Mid = 4
    	case Heavy = 10
        }
        enum Armor: Int {
    	case Light = 2
    	case Strong = 8
    	case Heavy = 20
        }
        case Helmet(weight: Weight, armor: Armor)
        case Breastplate(weight: Weight, armor: Armor)
        case Shield(weight: Weight, armor: Armor)
    }
    let woodenHelmet = Wearable.Helmet(weight: .Light, armor: .Light)
    

###  Methods and Properties

You can also define methods on an `enum` like so:
    
    
    enum Wearable {
        enum Weight: Int {
    	case Light = 1
        }
        enum Armor: Int {
    	case Light = 2
        }
        case Helmet(weight: Weight, armor: Armor)
        func attributes() -> (weight: Int, armor: Int) {
           switch self {
    	 case .Helmet(let w, let a): return (weight: w.rawValue * 2, armor: w.rawValue * 4)
           }
        }
    }
    let woodenHelmetProps = Wearable.Helmet(weight: .Light, armor: .Light).attributes()
    print (woodenHelmetProps)
    // prints "(2, 4)"
    

Methods on enums exist for every `enum case`. So if you want to have specific code for specific cases, you need a branch or a switch to determine the correct code path.
    
    
    enum Device { 
        case iPad, iPhone, AppleTV, AppleWatch 
        func introduced() -> String {
           switch self {
    	 case AppleTV: return "\(self) was introduced 2006"
    	 case iPhone: return "\(self) was introduced 2007"
    	 case iPad: return "\(self) was introduced 2010"
    	 case AppleWatch: return "\(self) was introduced 2014"
           }
        }
    }
    print (Device.iPhone.introduced())
    // prints: "iPhone was introduced 2007"
    

Even though you can't add actual stored properties to an `enum`, you can still create computed properties. Their contents, of course, can be based on the **enum value** or **enum associated value**.
    
    
    enum Device {
      case iPad, iPhone
      var year: Int {
        switch self {
    	case iPhone: return 2007
    	case iPad: return 2010
         }
      }
    }
    

####  Static Methods

You can also have static methods on `enums`, i.e. in order to create an `enum` from a non-value type. In this example we want to get the proper Apple Device for the wrong name that's sometimes used by people.
    
    
    enum Device { 
        case AppleWatch 
        static func fromSlang(term: String) -> Device? {
          if term == "iWatch" {
    	  return .AppleWatch
          }
          return nil
        }
    }
    print (Device.fromSlang("iWatch"))
    

####  Mutating Methods

Methods can be declared `mutating`. They're then allowed to change the `case` of the underlying `self` parameter [3](http://appventure.me):
    
    
    enum TriStateSwitch {
        case Off, Low, High
        mutating func next() {
    	switch self {
    	case Off:
    	    self = Low
    	case Low:
    	    self = High
    	case High:
    	    self = Off
    	}
        }
    }
    var ovenLight = TriStateSwitch.Low
    ovenLight.next()
    // ovenLight is now equal to .High
    ovenLight.next()
    // ovenLight is now equal to .Off
    

We've finished our overview of the basic use cases of Swift's `enum` syntax. Before we head into the advanced usage, lets have another look at the explanation we gave at the beginning and see if it became clearer now.

> Enums declare types with finite sets of possible states and accompanying values. With nesting, methods, associated values, and pattern matching, however, enums can define any hierarchically organized data. 

The definition is a lot clearer now. Indeed, if we add associated values and nesting, an `enum case` is like a closed, simplified `struct`. The advantage over structs being the ability to encode categorization and hierachy:
    
    
    // Struct Example
    struct Point { let x: Int, let y: Int }
    struct Rect { let x: Int, let y: Int, let width: Int, let height: Int }
    
    // Enum Example
    enum GeometricEntity {
       case Point(x: Int, y: Int)
       case Rect(x: Int, y: Int, width: Int, height: Int)
    }
    

The addition of methods and static methods allow us to attach functionality to an `enum` without having to resort to free functions [4](http://appventure.me)
    
    
    // C-Like example
    enum Trade {
       case Buy
       case Sell
    }
    func order(trade: Trade)
    
    // Swift Enum example
    enum Trade {
       case Buy
       case Sell
       func order()
    }
    

##  Advanced Enum Usage

I already mentioned the similarity between the `structs` and `enums`. In addition to the ability to add methods, Swift also allows you to use **Protocols** and **Protocol Extensions** with enums.

Swift protocols define an interface or type that other structures can conform to. In this case our `enum` can conform to it. For a start, let's take a protocol from the Swift standard library.

`CustomStringConvertible` is a type with a customized textual representation suitable for printing purposes:
    
    
    protocol CustomStringConvertible {
      var description: String { get }
    }
    

It has only one requirement, namely a **getter** for a string. We can implement this on an enum quite easily:
    
    
    enum Trade: CustomStringConvertible {
       case Buy, Sell
       var description: String {
           switch self {
    	   case Buy: return "We're buying something"
    	   case Sell: return "We're selling something"
           }
       }
    }
    
    let action = Trade.Buy
    print("this action is \(action)")
    // prints: this action is We're buying something
    

Some protocol implementations may need internal state handling to cope with the requirements. Imagine a protocol that manages a bank account:
    
    
    protocol AccountCompatible {
      var remainingFunds: Int { get }
      mutating func addFunds(amount: Int) throws
      mutating func removeFunds(amount: Int) throws
    }
    

You could easily fulfill this protocol with a `struct`, but in the context of your application, a `enum` is the more sensible approach. However, you can't add properties like `var remainingFunds: Int` to an `enum`, so would you model that? The answer is actually easy, you can use associated values for this:
    
    
    enum Account {
      case Empty
      case Funds(remaining: Int)
    
      enum Error: ErrorType {
        case Overdraft(amount: Int)
      }
    
      var remainingFunds: Int {
        switch self {
        case Empty: return 0
        case Funds(let remaining): return remaining
        }
      }
    }
    

To keep things clean, we can then define the required protocol functions in a protocol extension on the `enum`:
    
    
    extension Account: AccountCompatible {
    
      mutating func addFunds(amount: Int) throws {
        var newAmount = amount
        if case let .Funds(remaining) = self {
          newAmount += remaining
        }
        if newAmount < 0 {
          throw Error.Overdraft(amount: -newAmount)
        } else if newAmount == 0 {
          self = .Empty
        } else {
          self = .Funds(remaining: newAmount)
        }
      }
    
      mutating func removeFunds(amount: Int) throws {
        try self.addFunds(amount * -1)
      }
    
    }
    
    var account = Account.Funds(remaining: 20)
    print("add: ", try? account.addFunds(10))
    print ("remove 1: ", try? account.removeFunds(15))
    print ("remove 2: ", try? account.removeFunds(55))
    // prints:
    // : add:  Optional(())
    // : remove 1:  Optional(())
    // : remove 2:  nil
    

As you can see, we implemented all the protocol requirements by storing our values within our `enum cases`. A very nifty side effect of this is, that now you can test for an empty account with a simple pattern match all over your code base. You don't have to see whether the remainingFunds are zero.

We're also nesting a `ErrorType` compatible `enum` in the **Account** enum so that we can use Swift 2.0's new error handling. This is explained in more detail in the **[Practical Use Cases**](http://appventure.me) section.

As we just saw, enums can also be extended. The most apparent use case for this is keeping `enum cases` and `methods` separate, so that a reader of your code can easily digest the `enum` and after that move on to the methods:
    
    
    enum Entities {
        case Soldier(x: Int, y: Int)
        case Tank(x: Int, y: Int)
        case Player(x: Int, y: Int)
    }
    

Now, we can extend this `enum` with methods:
    
    
    extension Entities {
       mutating func move(dist: CGVector) {}
       mutating func attack() {}
    }
    

You can also write extensions to add support for a specific protocol:
    
    
    extension Entities: CustomStringConvertible {
      var description: String {
        switch self {
           case let .Soldier(x, y): return "\(x), \(y)"
           case let .Tank(x, y): return "\(x), \(y)"
           case let .Player(x, y): return "\(x), \(y)"
        }
      }
    }
    

Enums can also be defined over generic parameters. You'd use them to adapt the associated values of an enum. The simplest example comes straight from the Swift standard library, namely the `Optional` type. You probably mostly use it with **optional chaining** (`?`), `if let`, `guard let`, or `switch`, but syntactically you can also use Optionals like so:
    
    
    let aValue = Optional<Int>.Some(5)
    let noValue = Optional<Int>.None
    if noValue == Optional.None { print("No value") }
    

This is the direct usage of an Optional without any of the syntactic sugar that Swift adds in order to make your life a tremendous amount easier. If you look at the code above, you can probably guess that internally the `Optional` is defined as follows [5](http://appventure.me):
    
    
    // Simplified implementation of Swift's Optional
    enum MyOptional<T> {
      case Some(T)
      case None
    }
    

What's special here is, that the enum's **associated values** take the type of the generic parameter `T`, so that optionals can be built for any kind you wish to return.

Enums can have multiple generic parameters. Take the well-known **Either** type which is not part of Swift's standard library but implemented in many open source libraries as well as prevalent in other functional programming languages like Haskell or F#. The idea is that instead of just returning a value or no value (nee Optional) you'd return either the successful value or something else (probably an error value).
    
    
    // The well-known either type is, of course, an enum that allows you to return either
    // value one (say, a successful value) or value two (say an error) from a function
    enum Either<T1, T2> {
      case Left(T1)
      case Right(T2)
    }
    

Finally, all the type constraints that work on classes and structs in Swift also work on enums.
    
    
    // Totally nonsensical example. A bag that is either full (has an array with contents)
    // or empty.
    enum Bag<T: SequenceType where T.Generator.Element==Equatable> {
      case Empty
      case Full(contents: T)
    }
    

###  Recursive / Indirect Types

Indirect types are a new addition that came with Swift 2.0. They allow you to define enums where the associated value of a `case` is the very same enum again. As an example, consider that you want to define a file system representations with files and folders containing files. If **File** and **Folder** were enum cases, then the **Folder** case would need to have an array of **File** cases as it's associated value. Since this is a recursive operation, the compiler has to make special preparations for it. Quoting from the Swift documentation:

> Enums and cases can be marked indirect, which causes the associated value for the enum to be stored indirectly, allowing for recursive data structures to be defined. 

So to implement our **FileNode** `enum`, we'd have to write it like this:
    
    
    enum FileNode {
      case File(name: String)
      indirect case Folder(name: String, files: [FileNode])
    }
    

The `indirect` keyword tells the compiler to handle this `enum case` indirectly. You can also add the keyword for the whole enum. [As an example imagine mapping a binary tree](http://airspeedvelocity.net/2015/07/22/a-persistent-tree-using-indirect-enums-in-swift/):
    
    
    indirect enum Tree<Element: Comparable> {
        case Empty
        case Node(Tree<Element>,Element,Tree<Element>)
    }
    

This is a very powerful feature that allows you to map complex relationships in a very clean way with an enum.

###  Using Custom Data Types as Enum Values

If we neglect associated values, then the value of an enum can only be an Integer, Floating Point, String, or Boolean. If you need to support something else, you can do so by implementing the `StringLiteralConvertible` protocol which allows the type in question to be serialized to and from String.

As an example, imagine you'd like to store the different screen sizes of iOS devices in an enum:
    
    
    enum Devices: CGSize {
       case iPhone3GS = CGSize(width: 320, height: 480)
       case iPhone5 = CGSize(width: 320, height: 568)
       case iPhone6 = CGSize(width: 375, height: 667)
       case iPhone6Plus = CGSize(width: 414, height: 736)
    }
    

However, this doesn't compile. CGPoint is not a literal and can't be used as an enum value. Instead, what you need to do is add a type extension for the `StringLiteralConvertible` protocol. The protocol requires us to implement three **initializers** each of them is being called with a `String`, and we have to convert this string into our receiver type (`CGSize`)
    
    
    extension CGSize: StringLiteralConvertible {
        public init(stringLiteral value: String) {
    	let size = CGSizeFromString(value)
    	self.init(width: size.width, height: size.height)
        }
    
        public init(extendedGraphemeClusterLiteral value: String) {
    	let size = CGSizeFromString(value)
    	self.init(width: size.width, height: size.height)
        }
    
        public init(unicodeScalarLiteral value: String) {
    	let size = CGSizeFromString(value)
    	self.init(width: size.width, height: size.height)
        }
    }
    

Now, we can write our `enum`, with one downside though: The initial values have to be written as a String, since that's what the enum will use (remember, we complied with StringLiteralConvertible, so that the **String** can be converted to our `CGSize` type.
    
    
    enum Devices: CGSize {
       case iPhone3GS = "{320, 480}"
       case iPhone5 = "{320, 568}"
       case iPhone6 = "{375, 667}"
       case iPhone6Plus = "{414, 736}"
    }
    

This, finally, allows us to use our `CGPoint` enum. Keep in mind that in order to get the actual CGPoint value, we have to access the `rawvalue` of the enum.
    
    
    let a = Devices.iPhone5
    let b = a.rawValue
    print("the phone size string is \(a), width is \(b.width), height is \(b.height)")
    // prints : the phone size string is iPhone5, width is 320.0, height is 568.0
    

The String serialization requirement makes it a bit difficult to use any kind of type, but for some specific use cases, this can work well (such as **NSColor** / **UIColor**). However, you can also use this with your custom types obviously.

###  Comparing Enums with associated values

Enums, by nature, are easily comparable by equality. A simple `enum T { case a, b}` implementation supports the proper equality tests `T.a == T.a, T.b != T.a`.

If you add associated values though, Swift cannot correctly infer the equality of two enums, and you have to implement the `==` operator yourself. This is simple though:
    
    
    enum Trade {
        case Buy(stock: String, amount: Int)
        case Sell(stock: String, amount: Int)
    }
    func ==(lhs: Trade, rhs: Trade) -> Bool {
       switch (lhs, rhs) {
         case let (.Buy(stock1, amount1), .Buy(stock2, amount2))
    	   where stock1 == stock2 && amount1 == amount2:
    	   return true
         case let (.Sell(stock1, amount1), .Sell(stock2, amount2))
    	   where stock1 == stock2 && amount1 == amount2:
    	   return true
         default: return false
       }
    }
    

As you can see, we're comparing the two possible `enum cases` via a switch, and only if the cases match (i.e. .Buy & .Buy) will we compare the actual associated values.

###  Custom Initializers

In the context of **static methods** on enums, we already mentioned that they can be used as a way to conveniently create an enum from different data. The example we had was for returning the proper Apple device for the wrong worded version that the press sometimes uses:
    
    
    enum Device { 
        case AppleWatch 
        static func fromSlang(term: String) -> Device? {
          if term == "iWatch" {
    	  return .AppleWatch
          }
          return nil
        }
    }
    

Instead of using a static method for this, we can also use a custom initializer. The main difference compared to a Swift `struct` or `class` is that within an `enum` initializer, you need to set the implicit `self` property to the correct case.
    
    
    enum Device { 
        case AppleWatch 
        init?(term: String) {
          if term == "iWatch" {
    	  self = .AppleWatch
          }
          return nil
        }
    }
    

In the above example, we used a failable initializer. However normal initializers work just as well:
    
    
    enum NumberCategory {
       case Small
       case Medium
       case Big
       case Huge
       init(number n: Int) {
    	if n < 10000 { self = .Small }
    	else if n < 1000000 { self = .Medium }
    	else if n < 100000000 { self = .Big }
    	else { self = .Huge }
       }
    }
    let aNumber = NumberCategory(number: 100)
    print(aNumber)
    // prints: "Small"
    

One particularly often asked question with regards to enums is how to iterate over all cases. Sadly, enums do not conform to the `SequenceType` protocol, so there is no official way to do this. Depending on the type of enum that you have, it might be easier or more difficult to implement a way of iterating over all cases. [There's a very good overview in this StackOverflow thread.](http://stackoverflow.com/questions/24007461/how-to-enumerate-an-enum-with-string-type) Also, there's so much variation in the replies that it wouldn't to listing only some of the examples here. On the other hand, listing all the examples would be too much.

###  Objective-C support

Integer-based enums such as `enum Bit: Int { case Zero = 0; case One = 1}` can be bridged to Objective-c via the `@objc` flag. However once you venture away from integers (say `String`) or start using **associated values** you can't use enums from within Objective-C.

[There's a hidden protocol called `_ObjectiveCBridgeable` which apparently](http://nshint.io/blog/2015/10/07/easy-cast-with-_ObjectiveCBridgeable/?utm_campaign=Swift%252BSandbox&utm_medium=email&utm_source=Swift_Sandbox_11) allows defining the proper methods so that Swift can convert things back and forth from Objective-C, but I suppose there's a reason why it is hidden. Nevertheless, theoretically it should allow you to add support for bridging an `enum` (including associated values) to Objective-C.

You don't have to do it that way though. Add two methods to your `enum`, define a type replacement on the `@objc` side, and you can move `enums` back and forth just fine, without having to conform to private protocols:
    
    
    enum Trade {
        case Buy(stock: String, amount: Int)
        case Sell(stock: String, amount: Int)
    }
    
    // This type could also exist in Objective-C code.
    @objc class OTrade: NSObject {
        var type: Int
        var stock: String
        var amount: Int
        init(type: Int, stock: String, amount: Int) {
    	self.type = type
    	self.stock = stock
    	self.amount = amount
        }
    }
    
    extension Trade  {
    
        func toObjc() -> OTrade {
    	switch self {
    	case let .Buy(stock, amount):
    	    return OTrade(type: 0, stock: stock, amount: amount)
    	case let .Sell(stock, amount):
    	    return OTrade(type: 1, stock: stock, amount: amount)
    	}
        }
    
        static func fromObjc(source: OTrade) -> Trade? {
    	switch (source.type) {
    	case 0: return Trade.Buy(stock: source.stock, amount: source.amount)
    	case 1: return Trade.Sell(stock: source.stock, amount: source.amount)
    	default: return nil
    	}
        }
    }
    

This still has the downside that you need to mirror your `enum` via a `NSObject` based type on the Objective-C side (or you just go and use an `NSDictionary`), but if you ever end up in a situation where you **need** to access an enum with associated values from Objective-C, this is a way to do it.

[Erica Sadun wrote a great blog post explaining the internals](http://ericasadun.com/2015/07/12/swift-enumerations-or-how-to-annoy-tom/) of `enums` when you look at the bits and bytes behind the glossy syntax. This is something you should never do in production code, but still interesting to know. We'll only mention one of her findings here, go and read her original article for more.

> Enums are typically one byte long. […] If you want to get very very silly, you can build an enumeration with hundreds of cases, in which case the enum takes up 2 or more bytes depending on the minimum bit count needed. 

##  Enums in the Swift Standard Library

Before we go on and explore various use cases for enums in your projects, it might be tempting to see some of the enums being used in the Swift standard library, so let's have a look.

**[Bit**](https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_Bit_Enumeration/index.html#//apple_ref/swift/enum/s:OSs3Bit) The `Bit` enum can have two possible values, **One**, and **Zero**. It is used as the `Index` type for `CollectionOfOne<T>`.

**[FloatingPointClassification**](https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_FloatingPointClassification_Enumeration/index.html#//apple_ref/swift/enumelt/FloatingPointClassification/s:FOSs27FloatingPointClassification12SignalingNaNFMS_S_) This enum defines the set of possible IEEE 754 "classes", like `NegativeInfinity`, `PositiveZero`, or `SignalingNaN`.

**[Mirror.AncestorRepresentation**](https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_Mirror-AncestorRepresentation_Enumeration/index.html#//apple_ref/swift/enum/s:OVSs6Mirror22AncestorRepresentation), and **[Mirror.DisplayStyle**](https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_Mirror-DisplayStyle_Enumeration/index.html#//apple_ref/swift/enum/s:OVSs6Mirror12DisplayStyle) These two are used in the context of the Swift Reflection API.

**[Optional**](https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_Optional_Enumeration/index.html#//apple_ref/swift/enum/s:Sq) Not much to say here

**[Process**](https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_Process_Enumeration/index.html#//apple_ref/swift/enum/s:OSs7Process) The Process enum contains the command line arguments of the current process (`Process.argc`, `Process.arguments`). This is a particularly interesting `enum` as it used to be a `struct` in Swift 1.0.

##  Practical Use Cases

We've already seen a couple of useful `enums` in the [previous feature descriptions.](http://appventure.me) Examples would be `Optional`, `Either`, `FileNode`, or the binary tree. However, there're many more scenarios where using an `enum` wins over a `struct` or `class`. Usually, if your problem domain can be divided into a finite set of distinctive categories, an `enum` may be the right choice. Even only two cases are a perfectly valid scenario for an enum, as the Optional and Either types show.

Here are, then, some more examples of practical `enum` usage to fuel your creativity.

One of the prime examples of Enum usage in Swift is, of course, the new error handling in Swift 2.0. Your throwing function can throw anything which conforms to the empty `ErrorType` protocol. As the Swift documentation succinctly observes:

> Swift enumerations are particularly well suited to modeling a group of related error conditions, with associated values allowing for additional information about the nature of an error to be communicated. 

As an example, we have a look at the popular [JSON Decoding library Argo](https://github.com/thoughtbot/Argo). When their JSON Decoding fails, it can fail due to two primary reasons.

  1. The JSON Data lacks a key which the end model requires (say your model has a property `username` and somehow the JSON lacks that) 
  2. There's a type mismatch. Say instead of a String the `username` property in the JSON contains an `NSNull` [6](http://appventure.me). 

In addition to that, Argo also includes a custom error for anything not fitting in these two categories above. Their `ErrorType enum` looks like this:
    
    
    enum DecodeError: ErrorType {
      case TypeMismatch(expected: String, actual: String)
      case MissingKey(String)
      case Custom(String)
    }
    

All cases have associated values that contain additional information about the error in question.

A more general `ErrorType` for complete HTTP / REST API handling could look like this:
    
    
    enum APIError : ErrorType {
        // Can't connect to the server (maybe offline?)
        case ConnectionError(error: NSError)
        // The server responded with a non 200 status code
        case ServerError(statusCode: Int, error: NSError)
        // We got no data (0 bytes) back from the server
        case NoDataError
        // The server response can't be converted from JSON to a Dictionary
        case JSONSerializationError(error: ErrorType)
        // The Argo decoding Failed
        case JSONMappingError(converstionError: DecodeError)
    }
    

This `ErrorType` implements the complete REST Stack up to the point where your app would get the completely decoded native `struct` or `class` object.

If you look closely, you'll see that within the `JSONMappingError`, we're wrapping the **Argo** `DecodeError` into our `APIError` type as we're still using Argo for the actual JSON decoding.

More information on `ErrorType` and more `enum` examples in this context can be found in the official documentation [here](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/ErrorHandling.html).

There're various ways of modelling observation in Swift. If you include `@objc` compatibility, you can use `NSNotificationCenter` or **KVO**. Even if not, the `didSet` syntax makes it easy to implement simple observation. Enums can be used here in order to make the type of change that happens to the observed object clearer. Imagine collection observation. If we think about it, we only have a couple of possible cases: One or more items are inserted, one or more items are deleted, one or more items are updated. This sounds like a job for an enum:
    
    
    enum Change {
         case Insertion(items: [Item])
         case Deletion(items: [Item])
         case Update(items: [Item])
    }
    

Then, the observing object can receive the concrete information of what happened in a very clean way. This could easily be extended by adding **oldValue** and **newValue**, too.

If you're working with an outside system which uses status codes (or error codes) to convey information, like HTTP Status Codes, enums are obviously a great way to encode the information. [7](http://appventure.me)
    
    
    enum HttpError: String {
      case Code400 = "Bad Request"
      case Code401 = "Unauthorized"
      case Code402 = "Payment Required"
      case Code403 = "Forbidden"
      case Code404 = "Not Found"
    }
    

Enums are also frequently used to map the result of JSON parsing into the Swift type system. Here's a short example of this:
    
    
    enum JSON {
        case JSONString(Swift.String)
        case JSONNumber(Double)
        case JSONObject([String : JSONValue])
        case JSONArray([JSONValue])
        case JSONBool(Bool)
        case JSONNull
    }
    

Similarly, if you're parsing something else, you may use the very same structure to convert your parsing results into Swift types. This also makes perfect sense to only do it during the parsing / processing step and then taking the `JSON enum` representation and converting it into one of your application's internal `class` or `struct` types.

Enums can be used to map reuse identifiers or storyboard identifiers from stringly typed information to something the type checker can understand. Imagine a UITableView with different prototype cells:
    
    
    enum CellType: String {
        case ButtonValueCell = "ButtonValueCell"
        case UnitEditCell = "UnitEditCell"
        case LabelCell = "LabelCell"
        case ResultLabelCell = "ResultLabelCell"
    }
    

Units and unit conversion are another nice use case for enums. You can map the units and their respective values and then add methods to do automatic conversions. Here's an oversimplified example.
    
    
    enum Liquid: Float {
      case ml = 1.0
      case l = 1000.0
      func convert(amount amount: Float, to: Liquid) -> Float {
          if self.rawValue < to.rawValue {
    	 return (self.rawValue / to.rawValue) * amount
          } else {
    	 return (self.rawValue * to.rawValue) * amount
          }
      }
    }
    // Convert liters to milliliters
    print (Liquid.l.convert(amount: 5, to: Liquid.ml))
    

Another example of this would be Currency conversion. Also, mathematical symbols (such as degrees vs radians) can benefit from this.

Enums are a great use cases for games, where many entities on screen belong to a specific family of items (enemies, obstacles, textures, …). In comparison to native iOS or Mac apps, games oftentimes are a tabula rasa. Meaning you invent a new world with new relationships and new kinds of objects, whereas on iOS or OSX you're using a well-defined world of UIButtons, UITableViews, UITableViewCells or NSStackView.

What's more, since Enums can conform to protocols, you can utilize protocol extensions and protocol based programming to add functionality to the various enums that you defined for your game. Here's a short example that tries to display such a hierarchy:
    
    
    enum FlyingBeast { case Dragon, Hippogriff, Gargoyle }
    enum Horde { case Ork, Troll }
    enum Player { case Mage, Warrior, Barbarian }
    enum NPC { case Vendor, Blacksmith }
    enum Element { case Tree, Fence, Stone }
    
    protocol Hurtable {}
    protocol Killable {}
    protocol Flying {}
    protocol Attacking {}
    protocol Obstacle {}
    
    extension FlyingBeast: Hurtable, Killable, Flying, Attacking {}
    extension Horde: Hurtable, Killable, Attacking {}
    extension Player: Hurtable, Obstacle {}
    extension NPC: Hurtable {}
    extension Element: Obstacle {}
    

###  Battling stringly typed code

In bigger Xcode projects, you're quickly accumulating lots of resources which are accessed by string. We've already mentioned reuse identifiers and storyboard identifiers above, but there's also: Images, Segues, Nibs, Fonts, and other resources. Oftentimes, those resources can be grouped into several distinct sets. If that's the case, a `String` typed `enum` is a good way of having the compiler check this for you.
    
    
    enum DetailViewImages: String {
      case Background = "bg1.png"
      case Sidebar = "sbg.png"
      case ActionButton1 = "btn1_1.png"
      case ActionButton2 = "btn2_1.png"
    }
    

For iOS users, [there's also R.swift which auto generates `structs` for most of those use cases.](https://github.com/mac-cain13/R.swift) Sometimes you may need more control though (or you may be on a Mac [8](http://appventure.me))

Rest APIs are a great use case for enums. They're naturally grouped, they're limited to a finite set of APIs, and they may have additional query or named parameters which can be modelled through associated values.

Take, for example, a look at a simplified version of the **[Instagram API**](https://instagram.com/developer/endpoints/media/)
    
    
    enum Instagram {
      enum Media {
        case Popular
        case Shortcode(id: String)
        case Search(lat: Float, min_timestamp: Int, lng: Float, max_timestamp: Int, distance: Int)
      }
      enum Users {
        case User(id: String)
        case Feed
        case Recent(id: String)
      }
    }
    

[Ash Furrow's **Moya** library](https://github.com/Moya/Moya) is based around this idea of using `enums` to map rest endpoints.

[Airspeed Velocity has a great writeup on how to implement a Linked List with an `enum`.](http://airspeedvelocity.net/tag/swift/) Most of the code in his post goes far beyond enums and touches a lot of interesting topics [9](http://appventure.me), but the basis of his linked list looks kinda like this (I simplified it a bit):
    
    
    enum List {
        case End
        indirect case Node(Int, next: List)
    }
    

Each `Node case` points to the next case, and by using an `enum` instead of something else, you don't have to use an optional for the `next` value to signify the termination of the list.

Airspeed Velocity also wrote a great post about the implementation of a red black tree with indirect Swift enums, so while you're already reading his blog, [you may just as well also read this one.](http://airspeedvelocity.net/2015/07/22/a-persistent-tree-using-indirect-enums-in-swift/)

The biggest issue is, [again, Tuple support](http://appventure.me/2015/07/19/tuples-swift-advanced-usage-best-practices/). I love tuples, they make many things easier, but they're currently under-documented and cannot be used in many scenarios. In terms of enums, you can't have tuples as the enum value:
    
    
    enum Devices: (intro: Int, name: String) {
      case iPhone = (intro: 2007, name: "iPhone")
      case AppleTV = (intro: 2006, name: "Apple TV")
      case AppleWatch = (intro: 2014, name: "Apple Watch")
    }
    

This may not look like the best example, but once you start using enums, you'll often end up in situations where you'd like to be able to do something like the above.

###  Default Associated Values

Another thing which you may run into is that associated values are always types but you can't set a default value for those types. Imagine such an example:
    
    
    enum Characters {
      case Mage(health: Int = 70, magic: Int = 100, strength: Int = 30)
      case Warrior(health: Int = 100, magic: Int = 0, strength: Int = 100)
      case Neophyte(health: Int = 50, magic: Int = 20, strength: Int = 80)
    }
    

You could still create new cases with different values, but the default settings for your character would be mapped.

##  Changes

****10/22/2015****

  * Incorporated PR [#6 from @mabidakun](https://github.com/terhechte/appventure-blog/pull/6). 
  * Added internal links 
  * Split up the account example into two easier to digest snippets. 

****10/21/2015****

[1](http://appventure.me)

Except by jumping through some hoops, see below

[2](http://appventure.me)

This is a simplified implementation for demo purposes. In reality you'd write this with optionals and a reverse argument order. Have a look at popular functional programming libraries like [Swiftz](https://github.com/typelift/Swiftz) or [Dollar](https://github.com/ankurp/Dollar.swift)

[3](http://appventure.me)

This example stems straight [from Apple's Swift documentation](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Methods.html#//apple_ref/doc/uid/TP40014097-CH15-ID234)

[4](http://appventure.me)

Which make it oftentimes very difficult to discover them

[5](http://appventure.me)

This is a simplified version, of course. Swift adds a lot of sugar for you

[6](http://appventure.me)

If you ever used JSON in an app, you may well have run into this issue once

[7](http://appventure.me)

Btw. You can't use only numbers as enum case names, so `case 400` does not work

[8](http://appventure.me)

Although Mac support for R.swift seems to be forthcoming

[9](http://appventure.me)

Translated: Go there, read it

[Here's a small Github project by WUD](https://github.com/WDUK/A9ChipSource) which uses the private [libMobileGestalt](https://gist.github.com/Cykey/5216992) to identify the manufacturer of the CPU in your fancy new iPhone 6S. Because, as you may not know, this year Apple is sourcing the chips from two different foundries: Samsung and TSMC. So which one did you get? You could, of course, just run the aforementioned GitHub project on your phone. However, that's all Objective-C and out of curiosity I wondered: How would you pull that off in Swift?

##  Step One: Adding a header

The first obstacle is already a tricky one. `LibMobileGestalt` doesn't offer a header as it is a private library. So how do you tell Swift / the linker that the function you want to call will indeed exist at compile time. At first glance it seems that pure Swift doesn't offer any facilities for this (if you're impatient, there's another solution below ;-), so we can always resort back to the [Brdiging Header](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/BuildingCocoaApps/MixandMatch.html) that Apple introduced to easily bridge the Swift and the Objective-C/C worlds. [Here is](https://bohemianpolymorph.wordpress.com/2014/07/11/manually-adding-a-swift-bridging-header/) a short guide on how to add a bridging header to your project. Basically add a new header file, and add the path to your target's Build Settings under `Objective-C Bridging Header`.

Then, add the following code to your header:
    
    
    #if __cplusplus
    extern "C" {
    #endif
        CFPropertyListRefMGCopyAnswer(CFStringRefproperty);
    #if __cplusplus
    }
    #endif
    

But what if you're writing a pure Swift project and don't want to add a bridging header? There's a mostly undocumented ([Thanks to someone on HN for pointing it out to me](https://news.ycombinator.com/item?id=10305664)) Swift attribute called `@asmname` that allows us to do something similar straight in Swift. [Russ Bishop has a post on this and much more you can do in this realm.](http://www.russbishop.net/swift-don-t-do-this)

Using the `@asmname` keyword, the code looks like this (and you can remove the bridging header):
    
    
    @asmname("MGCopyAnswer")
    func MGCopyAnswer(_: CFStringRef) -> Optional<Unmanaged<CFPropertyListRef>>;
    

We're basically telling Swift that this function exists, and we're telling it specifically what it requires and what it will return.

##  Step Two: Writing Swift

Next up, we want to write the Swift code to call this function, so let's do it:
    
    
    chipInfo = MGCopyAnswer("HardwarePlatform")
    

We might expect that the result of this is already the required `String`, but Swift is a safe language so first of all it is returning an `Optional` here, since the key in question ("HardwarePlatform") might not even exist. We first have to get the value out. To do that, we'll use the new Swift 2 `guard` statement.
    
    
    guard let chipInfo = MGCopyAnswer("HardwarePlatform")
        else { fatalError("Could not read hardware") }
    

If we look at the type of `chipInfo`, sadly, we still don't have a `String`. Instead, we're getting `Unmanaged<CFPropertyList>`. What's that?

The Apple Documentation has this to say about `Unmanaged`:

> A type for propagating an unmanaged object reference. 
> 
> When you use this type, you become partially responsible for keeping the object alive. 

Of course, we're getting a value from the Core Foundation world where ARC does not know how to manage the memory. Objective-C uses the `__bridge` keyword to manage this, and in Swift it smartly changes the type so that we definitely don't forget that this variable's memory is currently not managed. [NSHipster](http://nshipster.com/unmanaged/), and [Apple](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Reference/Swift_Unmanaged_Structure/index.html) have more documentation for this. What we'll do is call the `takeReaintedValue` method:
    
    
    guard let chipInfo = MGCopyAnswer("HardwarePlatform")
        else { fatalError("Could not read hardware") }
    chipInfo.takeRetainedValue()
    

So, do we finally have a String? No, but we're close. We're getting a `CFPropertyList` object back. The Apple Documentation has this to say about this type:

> CFPropertyListRef can be a reference to any of the property list objects: CFData, CFString, CFArray, CFDictionary, CFDate, CFBoolean, and CFNumber. 

This means that if the result is indeed of type `CFString`, since `CFString` is toll-free-bridged to `NSString` and since `NSString` is bridged to Swift's `String`, we could just force cast this to the `String` type and be done with it. Swift is a safe language however, and when possible we should strive to do everything the safe way. So instead we'll do an optional cast to String and if that works out, we can get the actual String value out of the `Optional`.

If we do it this way, it will not blow up whtn the contents of the reference are, say, a `CFDate` or a `CFBoolean`. This is particularly easy with [Swift's Pattern Matching syntax](http://appventure.me/2015/08/20/swift-pattern-matching-in-detail/):
    
    
    guard let chipInfo = MGCopyAnswer("HardwarePlatform")
        else { fatalError("Could not read hardware") }
    
    switch chipInfo.takeRetainedValue() as? String {
    case "s8000"?:
        print("Samsung")
    case "s8003"?:
        print("TSMC")
    default:
        print("Unknown")
    }
    

The question mark at the end of the two codes **("s8000"?)** signifies that we're not matching against a `String`, but against an `Optional<String>`.

##  Step Three: Add the Framework

There we are. Awesome it works. Except, it doesn't. You still have to add the `libMobileGestalt.tbd` library and the `Core Foundation` framework to your project target's `Linked Frameworks and Libraries`.

I've [also created a small GitHub project that includes all this](https://github.com/terhechte/SwiftiPhone6sChipFinder) including the correct library setup etc.

Swift 2.0 b6 includes a new way of handling exceptions via the `try?` keyword. This is a quick post to explain the basics, and why this is cool.

In Swift 1.x, all we had for error handling were optionals and `NSError`. Which is [why many people adopted `Either` / `Result` types](https://github.com/antitypical/Result) as they can be found in [other](https://hackage.haskell.org/package/base-4.8.1.0/docs/Data-Either.html) [programming](http://www.scala-lang.org/api/2.9.3/scala/Either.html) languages:
    
    
    let success = Result<String, NSError>.Success("success")
    

With Swift 2 and the introduction of `try / catch` exception handling. Internally, this doesn't use expensive stack unwinding, as other (say, Objective-C or Java) do it, but instead seems to pretty much return something akin to `Either` or `Result`. Only the syntax hides this from the user in order to make it simpler to use[1](http://appventure.me).

##  Swift 2 b5 and earlier

However, once you start using the new `do / try / catch` more, what happens from time to time is that you start nesting code into messy branches because `do` is (was) incompatible with the other major way of handling potentially unknown states: optionals. Here's a particular ugly piece of code. Observe how we're nesting `if let` with `let` with `do` with `let` [2](http://appventure.me).
    
    
    import Foundation
    // get the currently logged in user
    func loggedInUser() -> Int? { return 0 }
    // get his name
    func getUserName (userId: Int) throws -> String { return "Claus" }
    // create a new image post with this username. Returns the post data
    func imagePostForUserName(name: String, imageURL: NSURL?) -> NSData? { return NSData() }
    // post the data to a server
    func postImage(data: NSData) throws -> Bool { return true }
    
    if let uid = loggedInUser() {
        do {
    	let username = try getUserName(uid)
    	if let data = imagePostForUserName(username, imageURL: nil) {
    	    do {
    		let success = try postImage(data)
    		if success {
    		    print ("Submitted")
    		}  
    	    } catch {
    		// more error handling
    	    }
    	}
        } catch {
    	// todo: error handling
        }
    }
    

One reason why this is difficult to simplify is that the `do` forces a break in any multi `guard` or multi `let` [3](http://appventure.me).

##  Swift 2 b6

With beta 6, we get a new keyword, `try?` which performs a throwing operation and returns optional `None` in case of failure and optional `Some` in case of success. [Quoting straight from the changelog:](http://adcdownload.apple.com/Developer_Tools/Xcode_7_beta_6/Xcode_7_beta_6_Release_Notes.pdf)

> A new keyword 'try?' has been added to Swift. 'try?' attempts to perform an operation that may throw. If the operation succeeds, the result is wrapped in an optional; if it fails (I.e. if an error is thrown), the result is 'nil' and the error is discarded. 'try?' is particularly useful when used in conjunction with "if let" and "guard". 

This makes it possible to retrieve the value of a potential throwing operation as an optional. If we apply this to our code above, we can simplify it quite a bit:
    
    
    if let uid = loggedInUser(),
       username = try? getUserName(uid),
       data = imagePostForUserName(username, imageURL: nil),
       success = try? postImage(data)
       where success == true {
          print ("Submitted")
    }
    
    
    
    Submitted
    

This is, of course a bit of a contrived example, engineered to explain `try?`. But still, that's definitely less code. We're, of course, loosing a lot of possibly valuable error information that would otherwise be available in the `catch`.

##  Which to choose?

`try?` can help you write terser code at the expense of loosing insights. Using `try?` only returns an optional without further information on the particular cause of the error / exception. The benefit, of course, is beautiful composability with **a lot** of the other Swift syntax, like `map`, `flatmap`, `switch`, `guard`, `if let`, `for case`, and others.

The non-optional `try` works great for distinct task where you're not dependant on earlier or later possible optional results.

The aforementioned `Result` type, on the other hand offers both; either the requested value, or a possible error. You can just continue using `Result`, which also has support for wrapping throws and much more, however keep in mind that this is not the direction Swift seems to intend to go [4](http://appventure.me). Otherwise, we'd have a full blown Result or Either type in Swift 2.

I'm really happy about the introduction of `try?` as it will make many snippets, particularly when interacting with the Cocoa API, easier to solve.

Among the new features that Swift offers to Objective-C programmers is one that disguises itself like a boring old man while it offers huge potential for forming elegant solutions to otherwise unwieldy sets of nested branches. I'm, of course talking about the `switch` statement that many Objective-C programmers probably consider as a clunky syntax device which is most entertaining when used as [Duff's Device](http://en.wikipedia.org/wiki/Duff's_device), yet usually offers little to no advantages over multiple if statements.

The `Switch` statement in Swift can do much more though. In the following tutorial, I will try to explain the various usages for these new features in more detail. I'll mostly ignore those solutions where there's no benefit over how `switch` works in Objective-C or C. The basics of this post were actually written in July 2014, but so many of my patterns crashed the compiler back then that I postponed writing it until there's better support.

This Blog Post is also available in the following languages:

##  Diving In

The main feature of `switch` is of course pattern matching, the ability to destructure values and match different switch cases based on correct match of the values to the cases.
    
    
    // Example of the worst binary -> decimal converter in history
    let bool1 = 1
    let bool2 = 0
    switch (bool1, bool2) {
       case (0, 0): print("0")
       case (0, 1): print("1")
       case (1, 0): print("2")
       case (1, 1): print("3")
    }
    

Pattern matching has long existed in other languages like Haskell, Erlang, Scala, or Prolog. This is a boon, because it allows us to have a look at how those languages utilize pattern matching in order to solve their problems. We can even have a look at their examples to find the most practical ones that offer real world adaptability.

##  A Trading Engine
    
    
    enum Trades {
        case Buy(stock: String, amount: Int, stockPrice: Float)
        case Sell(stock: String, amount: Int, stockPrice: Float)
    }
    

You were also handed the following API to handle trades. **Notice how sell orders are just negative amounts**. And you're told the stock price is not important, their engine will take an internal one anyway.
    
    
    /**
     - parameter stock: The stock name
     - parameter amount: The amount, negative number = sell, positive = buy
    */
    func process(stock: String, _ amount: Int) {
        print ("\(amount) of \(stock)")
    }
    

The next step is to process those trades. You see the potential for using pattern matching and write this:
    
    
    let aTrade = Trades.Buy(stock: "APPL", amount: 200, stockPrice: 115.5)
    
    switch aTrade {
    case .Buy(let stock, let amount, _):
        process(stock, amount)
    case .Sell(let stock, let amount, _):
        process(stock, amount * -1)
    }
    // Prints "buy 200 of APPL"
    

Swift lets us conveniently only destructure / extract the information from the `enum` that we really want. In this case only the stock and the amount.

Awesome, you visit Wall Street to show of your fantastic trading platform. However, as always, the reality is much more cumbersome than the beautiful theory. Trades aren't trades you learn.

  * You have to calculate in a fee which is different based on the trader type. 
  * The smaller the institution the higher the fee. 
  * Also, bigger institutions get a higher priority. 

They also realized that you'll need a new API for this, so you were handed this:
    
    
    func processSlow(stock: String, _ amount: Int, _ fee: Float) { print("slow") }
    func processFast(stock: String, _ amount: Int, _ fee: Float) { print("fast") }
    

So you go back to the drawing board and add another `enum`. The trader type is part of every trade, too.
    
    
    enum TraderType {
    case SingleGuy
    case Company
    } 
    
    enum Trades {
        case Buy(stock: String, amount: Int, stockPrice: Float, type: TraderType)
        case Sell(stock: String, amount: Int, stockPrice: Float, type: TraderType)
    }
    

So, how do you best implement this new restriction? You could just have an `if` / `else` switch for buy and for sell, but that would lead to nested code which quickly lacks clarity - and who knows maybe these Wall Street guys come up with further complications. So you define it instead as additional requirements on the pattern matches:
    
    
    let aTrade = Trades.Sell(stock: "GOOG", amount: 100, stockPrice: 666.0, type: TraderType.Company)
    
    switch aTrade {
    case let .Buy(stock, amount, _, TraderType.SingleGuy):
        processSlow(stock, amount, 5.0)
    case let .Sell(stock, amount, _, TraderType.SingleGuy):
        processSlow(stock, -1 * amount, 5.0)
    case let .Buy(stock, amount, _, TraderType.Company):
        processFast(stock, amount, 2.0)
    case let .Sell(stock, amount, _, TraderType.Company):
        processFast(stock, -1 * amount, 2.0)
    }
    

The beauty of this is that there's a very succinct flow describing the different possible combinations. Also, note how we changed `.Buy(let stock, let amount)` into `let .Buy(stock, amount)` in order to keep things simpler. This will destructure the `enum` just as before, only with less syntax.

###  Guards! Guards!

Once again you present your development to your Wall Street customer, and once again a new issue pops up (you really should have asked for a more detailed project description).

  * Sell orders exceeding a total value of $1.000.000 do always get fast handling, even if it's just a single guy. 
  * Buy orders under a total value of $1.000 do always get slow handling. 

With traditional nested `if` syntax, this would already become a bit messy. Not so with `switch`. Swift includes guards for `switch cases` which allow you to further restrict the possible matching of those cases.

You only need to modify your `switch` a little bit to accommodate for those new changes
    
    
    let aTrade = Trades.Buy(stock: "GOOG", amount: 1000, stockPrice: 666.0, type: TraderType.SingleGuy)
    
    switch aTrade {
    case let .Buy(stock, amount, _, TraderType.SingleGuy):
        processSlow(stock, amount, 5.0)
    case let .Sell(stock, amount, price, TraderType.SingleGuy)
        where price*Float(amount) > 1000000:
        processFast(stock, -1 * amount, 5.0)
    case let .Sell(stock, amount, _, TraderType.SingleGuy):
        processSlow(stock, -1 * amount, 5.0)
    case let .Buy(stock, amount, price, TraderType.Company)
        where price*Float(amount) < 1000:
        processSlow(stock, amount, 2.0)
    case let .Buy(stock, amount, _, TraderType.Company):
        processFast(stock, amount, 2.0)
    case let .Sell(stock, amount, _, TraderType.Company):
        processFast(stock, -1 * amount, 2.0)
    }
    

This code is quite structured, still rather easy to read, and wraps up the complex cases quite well.

That's it, we've successfully implemented our trading engine. However, this solution still has a bit of repetition; we wonder if there're pattern matching ways to improve upon that. So, let's look into pattern matching a bit more.

##  Advanced Pattern Matching

So now we've seen several patterns in action. But what's the syntax here? Which other things can we match for? Swift distinguishes **7** different patterns. We're going to have a quick look at each of them.

All of those patterns can not only be used with the `switch` keyword, but also with the `if`, `guard`, and `for` keywords. For details on this, see below.

###  1\. Wildcard Pattern

The wildcard pattern ignores the value to be matched against. In this case any value is possible. This is the same pattern as `let _ = fn()` where the `_` indicates that you don't wish to further use this value. The interesting part is that this matches all values including `nil` [1](http://appventure.me). You can even match optionals by appending a `?`:
    
    
    let p: String? = nil
    switch p {
    case _?: print ("Has String")
    case nil: print ("No String")
    }
    

As you've seen in the trading example, it also allows you to omit the data you don't need from matching `enums` or `tuples`:
    
    
    switch (15, "example", 3.14) {
        case (_, _, let pi): print ("pi: \(pi)")
    }
    

###  2\. Identifier Pattern

###  3\. Value-Binding Pattern

This is the very same as binding values to variables via `let` or `var`. Only in a switch statement. You've already seen this before, so I'll provide a very short example:
    
    
    switch (4, 5) {
      case let (x, y): print("\(x) \(y)")
    }
    

###  4\. Tuple Pattern

[I've written a whole blog post about tuples,](http://appventure.me/2015/07/19/tuples-swift-advanced-usage-best-practices/) which offer much more information than this, but here's a quick example:
    
    
    let age = 23
    let job: String? = "Operator"
    let payload: AnyObject = NSDictionary()
    
    switch (age, job, payload) {
      case (let age, _?, _ as NSDictionary):
      print(age)
      default: ()
    }
    

Here, we're combining three values into a tuple (imagine they're coming from different API calls) and matching them in one go. Note that the pattern achieves three things:

  1. It extracts the age 
  2. It makes sure there is a job, even though we don't need it 
  3. It makes sure that the payload is of kind `NSDictionary` even though we don't need the actual value either. 

###  5\. Enumeration Case Pattern

As you saw in our trading example, pattern matching works **really great** with Swift's `enums`. That's because `enum cases` are like sealed, immutable, destructable structs. Much like with `tuples`, you can unwrap the contents of an individual case right in the match and only extract the information you need [2](http://appventure.me).

Imagine you're writing a game in a functional style and you have a couple of entities that you need to define. You could use `structs` but as your entities will have very little state, you feel that that's a bit of an overkill.
    
    
    enum Entities {
        case Soldier(x: Int, y: Int)
        case Tank(x: Int, y: Int)
        case Player(x: Int, y: Int)
    }
    

Now you need to implement the drawing loop. Here, we only need the X and Y position:
    
    
    for e in entities() {
        switch e {
        case let .Soldier(x, y):
          drawImage("soldier.png", x, y)
        case let .Tank(x, y):
          drawImage("tank.png", x, y)
        case let .Player(x, y):
          drawImage("player.png", x, y)
        }
    }
    

###  6\. Type-Casting Patterns

As the name already implies, this pattern casts or matches types. It has two different keywords:

  * `is` **type**: Matches the runtime type (or a subclass of it) against the right hand side. This performs a type cast but disregards the returned type. So your `case` block won't know about the matched type. 
  * pattern `as` **type**: Performs the same match as the `is` pattern but for a successful match casts the type into the pattern specified on the left hand side. 

Here is an example of the two.
    
    
    let a: Any = 5 
    switch a {
      // this fails because a is still anyobject
      // error: binary operator '+' cannot be applied to operands of type 'Any' and 'Int'
      case is Int: print (a + 1)
      // This works and returns '6'
      case let n as Int: print (n + 1)
      default: ()
    }
    

Note that there is no `pattern` before the `is`. It matches directly against `a`.

###  7\. Expression Pattern

The expression pattern is very powerful. It matches the `switch` value against an expression implementing the `~=` operator. There're default implementations for this operator, for example for ranges, so that you can do:
    
    
    switch 5 {
     case 0..10: print("In range 0-10")
    }
    

However, the much more interesting possibility is overloading the operator yourself in order to add matchability to your custom types. Let's say that you decided to rewrite the soldier game we wrote earlier and you want to use structs after all.
    
    
    struct Soldier {
      let hp: Int
      let x: Int
      let y: Int
    }
    

Now you'd like to easily match against all entities with a health of **0**. We can simply implement the `~=` operators as follows.
    
    
    func ~= (pattern: Int, value: Soldier) -> Bool {
        return pattern == value.hp
    }
    

Now we can match against an entity:
    
    
    let soldier = Soldier(hp: 99, x: 10, y: 10)
    switch soldier {
       case 0: print("dead soldier")
       default: ()
    }
    

Sadly, full matching with tuples does not seem to work. If you implement the code below, there'll be a type checker error.
    
    
    func ~= (pattern: (hp: Int, x: Int, y: Int), value: Soldier) -> Bool {
       let (hp, x, y) = pattern
       return hp == value.hp && x == value.x && y == value.y
    }
    

One possible way of implementing something akin to the above is by adding a `unapply` method to your `struct` and then matching against that:
    
    
    extension Soldier {
       func unapply() -> (Int, Int, Int) {
          return (self.hp, self.x, self.y)
       }
    }
    
    func ~= (p: (Int, Int, Int), t: (Int, Int, Int)) -> Bool {
       return p.0 == t.0 && p.1 == t.1 && p.2 == t.2 
    }
    
    let soldier = Soldier(hp: 99, x: 10, y: 10)
    print(soldier.unapply() ~= (99, 10, 10))
    

But this is rather cumbersome and defeats the purpose of a lot of the magic behind pattern matching.

In an earlier version of this post, I wrote that `~=` doesn't work with protocols, but I was wrong. I remember that I tried it in a Playground, and it didn't work. However, this example ([as kindly provided by latrodectus on reddit](https://www.reddit.com/r/swift/comments/3hq6id/match_me_if_you_can_swift_pattern_matching_in/cub187r)) does work fine:
    
    
    protocol Entity {
        var value: Int {get}
    }
    
    struct Tank: Entity {
        var value: Int
        init(_ value: Int) { self.value = value }
    }
    
    struct Peasant: Entity {
        var value: Int
        init(_ value: Int) { self.value = value }
    }
    
    func ~=(pattern: Entity, x: Entity) -> Bool {
        return pattern.value == x.value
    }
    
    switch Tank(42) {
        case Peasant(42): print("Matched") // Does match
        default: ()
    }
    

There's a lot of things you can do with `Expression Patterns`. For a much more detailed explanation of Expression Patterns, [have a look at this terrific blog post by Austin Zheng](http://austinzheng.com/2014/12/17/custom-pattern-matching/).

This completes list of possible switch patterns. Before we move on, there's one final thing to discuss.

###  Fallthrough, Break, and Labels

The following is not directly related to pattern matching but only affects the `switch` keyword, so I'll keep it brief. By default, and unlike C/C++/Objective-C, `switch` `cases` do not fall through into the next case which is why in Swift, you don't need to write `break` for every case. You can opt into traditional fallthrough behaviour with the `fallthrough` keyword.
    
    
    switch 5 {
       case 5:
        print("Is 5")
        fallthrough
       default:
        print("Is a number")
    }
    // Will print: "Is 5" "Is a number"
    

Alternatively, you can use `break` to break out of a switch statement early. Why would you do that if there's no default fallthrough? For example if you can only realize within the `case` that a certain requirement is not met and you can't execute the `case` any further:
    
    
    let userType = "system"
    let userID = 10
    switch (userType, userID)  {
       case ("system", _):
         guard let userData = getSystemUser(userID) else { break }
         print("user info: \(userData)")
         insertIntoRemoteDB(userData)
       default: ()
    }
    ... more code that needs to be executed
    

Here, we don't want to call `insertIntoRemoteData` when the result from `getSystemUser` is `nil`. Of course, you could just use an `if let` here, but if multiple of those cases come together, you quickly end up with a bunch of horrifyingly ugly nested `if lets`.

But what if you execute your switch in a `while` loop and you want to break out of the loop, not the `switch`? For those cases, Swift allows you to define `labels` to `break` or `continue` to:
    
    
    gameLoop: while true {
      switch state() {
         case .Waiting: continue gameLoop
         case .Done: calculateNextState()
         case .GameOver: break gameLoop
      }
    }
    

We've discussed the syntax and implementation details of `switch` and pattern matching. Now, let us have a look at some interesting (more or less) real world examples.

##  Real World Examples

[There're many ways to unwrap optionals,](http://appventure.me/2014/06/13/swift-optionals-made-simple/) and pattern matching is one of them. You've probably used that quite frequently by now, nevertheless, here's a short example:
    
    
    var result: String? = secretMethod()
    switch result {
    case .None:
        println("is nothing")
    case let a:
        println("\(a) is a value")
    }
    

With Swift 2.0, this becomes even easier:
    
    
    var result: String? = secretMethod()
    switch result {
    case nil:
        print("is nothing")
    case let a?:
        print("\(a) is a value")
    }
    

As you can see, `result` could be a string, but it could also be `nil`. It's an `optional`. By switching on result, we can figure out whether it is `.None` or whether it is an actual value. Even more, if it is a value, we can also bind this value to variable right away. In this case `a`. What's beautiful here, is the clearly visible distinction between the two states, that the variable `result` can be in.

Given Swift's strong type system, there's usually no need for runtime type checks like it more often happens in Objective-C. However, when you interact with legacy Objective-C code [(which hasn't been updated to reflect simple generics yet)](https://netguru.co/blog/objective-c-generics), then you often end up with code that needs to check for types. Imagine getting an array of NSStrings and NSNumbers:
    
    
    let u = NSArray(array: [NSString(string: "String1"), NSNumber(int: 20), NSNumber(int: 40)])
    

When you go through this NSArray, you never know what kind of type you get. However, `switch` statements allow you to easily test for types here:
    
    
    for x in u {
        switch x {
        case _ as NSString:
    	print("string")
        case _ as NSNumber:
    	print("number")
        default:
    	print("Unknown types")
        }
    }
    

###  Applying ranges for grading

So you're writing the grading iOS app for your local Highschool. The teachers want to enter a number value from 0 to 100 and receive the grade character for it (A - F). Pattern Matching to the rescue:
    
    
    let aGrade = 84
    
    switch aGrade {
    case 90...100: print("A")
    case 80...90: print("B")
    case 70...80: print("C")
    case 60...70: print("D")
    case 0...60: print("F")
    default:
        print("Incorrect Grade")
    }
    

We have a sequence of pairs, each representing a word and its frequency in some text. Our goal is to filter out those pairs whose frequency is below or above a certain threshold, and then only return the remaining words, without their respective frequencies.

Here're our words:
    
    
    let wordFreqs = [("k", 5), ("a", 7), ("b", 3)]
    

A simple solution would be to model this with `map` and `filter`:
    
    
    let res = wordFreqs.filter({ (e) -> Bool in
        if e.1 > 3 {
    	return true
        } else {
    	return false
        }
    }).map { $0.0 }
    print(res)
    

However, with `flatmap` a map that only returns the non-nil elements, we can improve a lot upon this solution. First and foremost, we can get rid of the `e.1` and instead have proper destructuring by utilizing (you guessed it) tuples. And then, we only need one call `flatmap` instead of `filter` and then `map` which adds unnecessary performance overhead.
    
    
    let res = wordFreqs.flatMap { (e) -> String? in
        switch e {
        case let (s, t) where t > 3: return s
        default: return nil
        }
    }
    print(res)
    

Imagine you want to traverse a file hierachy and find:

  * all "psd" files from customer1 and customer2 
  * all "blend" files from customer2 
  * all "jpeg" files from all customers. 
    
    
    guard let enumerator = NSFileManager.defaultManager().enumeratorAtPath("/customers/2014/")
    else { return }
    
    for url in enumerator {
        switch (url.pathComponents, url.pathExtension) {
    
        // psd files from customer1, customer2
        case (let f, "psd") 
    	    where f.contains("customer1") 
    	    || f.contains("customer2"): print(url)
    
        // blend files from customer2
        case (let f, "blend") where f.contains("customer2"): print(url)
    
        // all jpg files
        case (_, "jpg"): print(url)
    
        default: ()
        }
    }
    

Note that `contains` stops at the first match and doesn't traverse the complete path. Again, pattern matching lead to very succinct and readable code.

Also, see how beautiful an implementation of the fibonacci algorithm looks with pattern matching [3](http://appventure.me)
    
    
    func fibonacci(i: Int) -> Int {
        switch(i) {
        case let n where n <= 0: return 0
        case 0, 1: return 1
        case let n: return fibonacci(n - 1) + fibonacci(n - 2)
        }
    }
    
    print(fibonacci(8))
    

Of course, this will kill your stack with big numbers.

###  Legacy API and Value Extractions

Oftentimes, when you get data from an external source, like a library, or an API, it is not only good practice but usually even required that you check the data for consistency before interpreting it. You need to make sure that all keys exists or that the data is of the correct type, or the arrays have the required length. Not doing so can lead from buggy behaviour (missing key) to crash of the app (indexing non-existent array items). The classic way to do this is by nesting `if` statements.

Let's imagine an API that returns a user. However, there're two types of users: System users - like the administrator, or the postmaster - and local users - like "John B", "Bill Gates", etc. Due to the way the system was designed and grew, there're a couple of nuisances that API consumers have to deal with:

  * `system` and `local` users come via the same API call. 
  * the `department` key may not exist, since early versions of the db did not have that field and early employees never had to fill it out. 
  * the `name` array contains either 4 items (username, middlename, lastname, firstname) or 2 items (full name, username) depending on when the user was created. 
  * the `age` is an Integer with the age of the user 

Our system needs to create user accounts for all system users from this API with only the following information: username, department. We only need users born before 1980. If no department is given, "Corp" is assumed.
    
    
    func legacyAPI(id: Int) -> [String: AnyObject] {
        return ["type": "system", "department": "Dark Arts", "age": 57, 
    	   "name": ["voldemort", "Tom", "Marvolo", "Riddle"]] 
    }
    

Given these constraints, let's develop a pattern match for it:
    
    
    let item = legacyAPI(4)
    switch (item["type"], item["department"], item["age"], item["name"]) {
       case let (sys as String, dep as String, age as Int, name as [String]) where 
          age < 1980 &&
          sys == "system":
         createSystemUser(name.count == 2 ? name.last! : name.first!, dep: dep ?? "Corp")
      default:()
    }
    
    // returns ("voldemort", "Dark Arts")
    

Note that this code makes one dangerous assumption, which is that if the name array does not have 2 items, it **must** have 4 items. If that case doesn't hold, and we get a zero item name array, this would crash.

Other than that, it is a nice example of how pattern matching even with just one case can help you write cleaner code and simplify value extractions.

Also, see how we're writing `let` at the beginning right after the case, and don't have to repeat it for each assignment within the case.

##  Patterns with other Keywords

The Swift documentation points out, that not all patterns can be used with the `if`, `for` or the `guard` statement. However, the docs seem to be outdated. All 7 patterns work for all three keywords.

For those interested, I compiled an example Gist that has an example for each pattern for each keyword.

[You can see the example patterns here.](https://gist.github.com/terhechte/6eaeb90276bbfcd1ea41)

As a shorter example, see the **Value Binding**, **Tuple**, and **Type Casting** pattern used for all three keywords in one example:
    
    
    // This is just a collection of keywords that compiles. This code makes no sense
    func valueTupleType(a: (Int, Any)) -> Bool {
        // guard case Example
        guard case let (x, _ as String) = a else { return false}
        print(x)
    
        // for case example
        for case let (a, _ as String) in [a] {
    	print(a)
        }
    
        // if case example
        if case let (x, _ as String) = a {
           print("if", x)
        }
    
        // switch case example
        switch a {
        case let (a, _ as String):
    	print(a)
    	return true
        default: return false
        }
    }
    let u: Any = "a"
    let b: Any = 5
    print(valueTupleType((5, u)))
    print(valueTupleType((5, b)))
    // 5, 5, "if 5", 5, true, false
    

With this in mind, we will have a short look at each of those keywords in detail.

##  Using **for case**

With Swift 2.0, pattern matching has become even more important in the language as the `switch` capabilities have been extended to other keywords as well. For example, let's write a simple array function which only returns the non-nil elements
    
    
    func nonnil<T>(array: [T?]) -> [T] {
       var result: [T] = []
       for case let x? in array {
          result.append(x)
       }
       return result
    }
    
    print(nonnil(["a", nil, "b", "c", nil]))
    

The `case` keyword can be used in for loops just like in `switch` cases. Here's another example. Remember the game we talked about earlier? Well, after the first refactoring, our entity system now looks like this:
    
    
    enum Entity {
        enum EntityType {
    	case Soldier
    	case Player
        }
        case Entry(type: EntityType, x: Int, y: Int, hp: Int)
    }
    

Fancy, this allows us to draw all items with even less code:
    
    
    for case let Entity.Entry(t, x, y, _) in gameEntities()
    where x > 0 && y > 0 {
        drawEntity(t, x, y)
    }
    

Our one line unwraps all the necessary properties, makes sure we're not drawing beyond 0, and finally calls the render call (`drawEntity`).

In order to see if the player won the game, we want to know if there is at least one Soldier with health > 0
    
    
    func gameOver() -> Bool {
        for case Entity.Entry(.Soldier, _, _, let hp) in gameEntities() 
        where hp > 0 {return false}
        return true
    }
    print(gameOver())
    

What's nice is that the `Soldier` match is part of the for query. This feels a bit like `SQL` and less like imperative loop programming. Also, this makes our intent clearer to the compiler, opening up the possibilities for dispatch enhancements down the road. Another nice touch is that we don't have to spell out `Entity.EntityType.Soldier`. Swift understands our intent even if we only write `.Soldier` as above.

##  Using **guard case**

Another keyword which supports patterns is the newly introduced `guard` keyword. You know how it allows you to bind `optionals` into the local scope much like `if let` only without nesting things:
    
    
    func example(a: String?) {
        guard let a = a else { return }
        print(a)
    }
    example("yes")
    

`guard let case` allows you to do something similar with the power that pattern matching introduces. Let's have a look at our soldiers again. We want to calculate the required HP until our player has full health again. Soldiers can't regain HP, so we should always return 0 for a soldier entity.
    
    
    let MAX_HP = 100
    
    func healthHP(entity: Entity) -> Int {
        guard case let Entity.Entry(.Player, _, _, hp) = entity 
        where hp < MAX_HP 
        else { return 0 }
        return MAX_HP - hp
    }
    
    print("Soldier", healthHP(Entity.Entry(type: .Soldier, x: 10, y: 10, hp: 79)))
    print("Player", healthHP(Entity.Entry(type: .Player, x: 10, y: 10, hp: 57)))
    
    // Prints:
    "Soldier 0"
    "Player 43"
    

This is a beautiful example of the culmination of the various mechanisms we've discussed so far.

  * It is very clear, there is no nesting involved 
  * Logic and initialization of state are handled at the top of the `func` which improves readability 
  * Very terse. 

This can also be very successfully combined with `switch` and `for` to wrap complex logical constructs into an easy to read format. Of course, that won't make the logic any easier to understand, but at least it will be provided in a much saner package. Especially if you use `enums`.

##  Using **if case**

`if case` can be used as the opposite of `guard case`. It is a great way to unwrap and match data within a branch. In line with our previous `guard` example. Obviously, we need an move function. Something that allows us to say that an entity moved in a direction. Since our entities are `enums`, we need to return an updated entity.
    
    
    func move(entity: Entity, xd: Int, yd: Int) -> Entity {
    	if case Entity.Entry(let t, let x, let y, let hp) = entity
    	where (x + xd) < 1000 &&
    	    (y + yd) < 1000 {
    	return Entity.Entry(type: t, x: (x + xd), y: (y + yd), hp: hp)
        }
        return entity
    }
    print(move(Entity.Entry(type: .Soldier, x: 10, y: 10, hp: 79), xd: 30, yd: 500))
    // prints: Entry(main.Entity.EntityType.Soldier, 40, 510, 79)
    

Some limitations were already mentioned in the text, such as the issues regarding `Expression Patterns`, which seem to not match against `tuples` (as would be really convenient). In Scala or Clojure, pattern matching can also work against collections, so you could match head, tail, parts, etc. [4](http://appventure.me) This doesn't work in Swift ([although Austin Zheng kinda implemented this in the blog post I linked above](http://austinzheng.com/2014/12/17/custom-pattern-matching/)).

Another thing which doesn't work (wich, again, Scala does just fine) is destructuring against classes or structs. Scala allows us to define an `unapply` method which does basically the opposite of `init`. Implementing this method, then, allows the type checker to match against classes. In Swift, this could look as follows:
    
    
    struct Imaginary {
       let x: Int
       let y: Int
       func unapply() -> (Int, Int) {
         // implementing this method would then in theory provide all the details needed to destructure the vars
         return (self.x, self.y)
       }
    }
    // this, then, would unapply automatically and then match
    guard case let Imaginary(x, y) = anImaginaryObject else { break }
    

##  Changes

****08/21/2015**** Incorporated [helpful feedback from foBrowsing on Reddit](https://www.reddit.com/r/swift/comments/3hq6id/match_me_if_you_can_swift_pattern_matching_in/)

  * Added `guard case let`
  * Added simplified syntax for let (i.e. `let (x, y)` instead of `(let x, let y)`

****08/22/2015**** [Apparently I didn't test some things properly enough.](https://www.reddit.com/r/swift/comments/3hq6id/match_me_if_you_can_swift_pattern_matching_in/) Some of the limitations I listed do actually work, as another helpful Reddit commenter (latrodectus) pointed out.

  * All patterns work for all three keywords. Changed that, and added a Gist with examples 
  * The limitations regarding protocols and the expression pattern were invalid. This works fine, too. 
  * Added "Pattern Availability" section 

****08/24/2015****

  * Added `if case` examples, renamed some sections. 
  * Fixed typos in the text. In particular, I accidentally wrote that `_` does not match `nil`. That's of course not true, `_` matches everything. (thanks to [obecker](https://github.com/obecker)) 

****09/18/2015****

[1](http://appventure.me)

Think of it like the `*` wildcard you use in the shell

[2](http://appventure.me)

I'm not sure whether the compiler optimizes for this, but theoretically, it should be able to calculate the correct position of the requested data and inline the address ignoring the other parts of the enum case

[3](http://appventure.me)

of course, no match for a Haskell implementation:   
fib 0 = 0  
fib 1 = 1  
fib n = fib (n-1) + fib (n-2)

[4](http://appventure.me)

I.e. switch [1, 2, 4, 3] {   
case [_, 2, _, 3]:   
}

Tuples are one of Swift's less visible language features. They're occupying a small space between Structs and Arrays. In addition to that, there's no comparable construct in Objective-C (or many other languages). Finally, the usage of tuples in the standard library and in Apple's example code is sparse. One could get the impression that their raison d'etre in Swift is pattern machting, but I disgress.

Most tuple explanations concentrate on three tuple use cases (pattern matching, return values, destructuring) and leave it at that. The following guide tries to give a more comprehensive overview of tuples with best practices of when to use them, and when not to use them. I'll also try to list those things that you can't do with tuples, to spare you asking it on stack overflow. Let's dive in.

##  The absolute basics
    
    
    // Constructing a simple tuple
    let tp1 = (2, 3)
    let tp2 = (2, 3, 4)
    
    // Constructing a named tuple
    let tp3 = (x: 5, y: 3)
    
    // Different types
    let tp4 = (name: "Carl", age: 78, pets: ["Bonny", "Houdon", "Miki"])
    
    // Accessing tuple elements
    let tp5 = (13, 21)
    tp5.0 // 13
    tp5.1 // 21
    
    let tp6 = (x: 21, y: 33)
    tp6.x // 21
    tp6.y // 33
    

###  Tuples for pattern matching

As already mentioned above, this feels like the strongest use case for tuples. Swift's `switch` statement offers a really powerful way of easily defining complex conditionals without cluttering up the source code. You can then match for the type, existence, and value of multiple variables in one statement:
    
    
    // Contrieved example
    // these would be return values from various functions
    let age = 23
    let job: String? = "Operator"
    let payload: AnyObject = NSDictionary()
    

In the code above, we want to find the persons younger than 30 with a job and a NSDictionary payload. Imagine the payload as something from the Objective-C world, it could be a Dictionary or an Array or a Number. Awful code somebody else wrote years ago and you have to interact with it now.
    
    
    switch (age, job, payload) {
      case (let age, _?, _ as NSDictionary) where age < 30:
      print(age)
      default: ()
    }
    

By constructing the switch argument as a tuple `(age, job, payload)` we can query for the specific or unspecific attributes of all tuple elements at once. This allows for elaborately constrained conditionals.

###  Tuples as return types

Probably the next-best tuple use case. Since tuples can be constructed on the fly, they're a great way of easily returning multiple values from one function.
    
    
    func abc() -> (Int, Int, String) {
        return (3, 5, "Carl")
    }
    

###  Tuple Destructuring

Swift took a lot of inspirations from different programming languages, and this is something that Python has been doing for years. While the previous examples mostly showed how to easily get something into a tuple, destructuring is a swifty way of getting something out of a tuple, and in line with the `abc` example above, it looks like this:
    
    
    let (a, b, c) = abc()
    print(a)
    

Another example is getting several function calls into one line:
    
    
    let (a, b, c) = (a(), b(), c())
    

Or, an easy way of swapping two values:
    
    
    var a = 5
    var b = 4
    (b, a) = (a, b)
    

##  Beyond the basics

###  Tuples as anonymous structs

Tuples as well as structs both allow you to combine different types into one type:
    
    
    struct User {
      let name: String
      let age: Int
    }
    // vs.
    let user = (name: "Carl", age: 40)
    

As you can see, these two types are similar, yet while the struct is made from a struct description and a struct instance, the tuple exists only as an instance. This similarity can be leveraged whenever you have the need of defining a temporary struct inside a function or method. As the Swift docs say:

> Tuples are useful for temporary groups of related values. (…) If your data structure is likely to persist beyond a temporary scope, model it as a class or structure (…) 

As an example of this, consider the following situation where the return values from several functions first need to be uniquely collected and then inserted:
    
    
    func zipForUser(userid: String) -> String { return "12124" }
    func streetForUser(userid: String) -> String { return "Charles Street" }
    
    
    // Find all unique streets in our userbase
    var streets: [String: (zip: String, street: String, count: Int)] = [:]
    for userid in users {
        let zip = zipForUser(userid)
        let street = streetForUser(userid)
        let key = "\(zip)-\(street)"
        if let (_, _, count) = streets[key] {
    	streets[key] = (zip, street, count + 1)
        } else {
    	streets[key] = (zip, street, 1)
        }
    }
    
    drawStreetsOnMap(streets.values)
    

Here, the tuple is being used as a simple structure for a short interim usecase. Defining a struct would also be possible, but is not strictly necessary.

Another example would be a class which handles algorithmic data, and you're moving an interim result from one method to the next one. Defining an extra struct for something which is only used once in between two or three methods may not be required.
    
    
    // Made up algorithm
    func calculateInterim(values: [Int]) -> (r: Int, alpha: CGFloat, chi: (CGFloat, CGFLoat)) {
       ...
    }
    func expandInterim(interim: (r: Int, alpha: CGFloat, chi: (CGFloat, CGFLoat))) -> CGFloat {
       ...
    }
    

There's, of course, a fine line here. Defining a struct for one instance is overly complex, defining a tuple 4 times instead of one struct is overly complex too. Finding the sweet spot depends on various factors.

In addition to the previous example, there're also use cases where using tuples beyond a temporary scope is useful. Following Rich Hickey's "If a tree falls in the woods, does it make a sound?" as long as the scope is private and the tuple's type isn't littered over the implementation, using tuples for storing internal state can be fine.

A simple and contrieved example would be storing a static UITableView structure which displays various information from a user profile and contains the key path to the actual value as well as a flag whether the value can be edited when tapping on the cell.
    
    
    let tableViewValues = [(title: "Age", value: "user.age", editable: true),
    (title: "Name", value: "user.name.combinedName", editable: true),
    (title: "Username", value: "user.name.username", editable: false),
    (title: "ProfilePicture", value: "user.pictures.thumbnail", editable: false)]
    

The alternative would be to define a struct, but if the data is a purely private implementation detail, a tuple works just as well.

A better example is when you defined an object and want to add the ability to add multiple change listeners to your object. Each listener consists out of a name and the closure to be called upon any change:
    
    
    func addListener(name: String, action: (change: AnyObject?) -> ())
    func removeListener(name: String)
    

How are you storing these listeners in your object? The obvious solution would be to define a struct, but this is a very limited scope, and the struct would only be internal, and it'd only be used in three cases. Here, using a tuple may even be the better solution as the destructuring makes things simpler:
    
    
    var listeners: [(String, (AnyObject?) -> ())]
    
    func addListener(name: String, action: (change: AnyObject?) -> ()) {
       self.listeners.append((name, action))
    }
    
    func removeListener(name: String) {
        if let idx = listeners.indexOf({ e in return e.0 == name }) {
    	listeners.removeAtIndex(idx)
        }
    }
    
    func execute(change: Int) {
        for (_, listener) in listeners {
    	listener(change)
        }
    }
    

As you can see in the `execute` function, the destructuring abilities make tuples especially useful in this case as the contents are directly destructured into the local scope.

###  Tuples as Fixed-Size Sequences

Another area where tuples can be used is when you intend to constrain a type to a fixed amount of items. Imagine an object that calculates various statistics for all months in a year. You need to store a certain Integer value for each month separately. The solution that comes to mind first, would of course be:

However, in this case we don't know whether the property indeed contains 12 elements. A user of our object could accidentally insert 13 values, or 11. We can't tell the type checker that this is a fixed size array of 12 items[1](http://appventure.me). With tuples, this specific constraint can easily be put into place:
    
    
    var monthValues: (Int, Int, Int, Int, Int, Int, Int, Int, Int, Int, Int, Int)
    

The alternative would be to have the constraining logic in the object's functionality (say via the new `guard` statement), however this would be a run time check. The tuple check would be at compile time; your code wouldn't even compile when you try to give 11 months to your object.

###  Tuples for Complex Varargs Types

Varargs i.e. variable function arguments are a very useful technique for situations where the amount of parameters of a function is unknown.
    
    
    // classic example
    func sumOf(numbers: Int...) -> Int {
        // add up all numbers with the + operator
        return numbers.reduce(0, combine: +)
    }
    
    sumOf(1, 2, 5, 7, 9) // 24
    

Tuples can be useful here if your requirement goes beyond simple integers. Take this function which does a batch update of `n` entities in a database:
    
    
    func batchUpdate(updates: (String, Int)...) -> Bool {
        self.db.begin()
        for (key, value) in updates {
    	self.db.set(key, value)
        }
        self.db.end()
    }
    
    // We're imagining a weird database
    batchUpdate(("tk1", 5), ("tk7", 9), ("tk21", 44), ("tk88", 12))
    

##  Advanced Tuples

In the above descriptions, I've tried to stay clear from calling tuples sequences or collections because they aren't. Since every element of a tuple can have a different type, there's no type-safe way of looping or mapping over the contents of a tuple. Well, no beautiful one, that is.

Swift does offer limited reflection capabilities, and these allow us to inspect the contents of a tuple and loop over it. The downside is that the type checker has no way of figuring out what the type within the loop is, and thus everything is typed as `Any`. It is your job then to cast and match this against your possible types to figure out what to do.
    
    
    let t = (a: 5, b: "String", c: NSDate())
    
    let mirror = Mirror(reflecting: t)
    for (label, value) in mirror.children {
        switch value {
        case is Int:
    	print("int")
        case is String:
    	print("string")
        case is NSDate:
    	print("nsdate")
        default: ()
        }
    }
    

This is not as simple as array iteration, but it does work if you really need it.

There's no `Tuple` type available in Swift. If you wonder why that is, think about it: Every tuple is a totally different type, dependin on the types within it. So instead of defining a generic tuple requirement, you define the specific but generic incarnation of the tuple you intend to use:
    
    
    func wantsTuple<T1, T2>(tuple: (T1, T2)) -> T1 {
        return tuple.0
    }
    
    wantsTuple(("a", "b")) // "a"
    wantsTuple((1, 2)) // 1
    

You can also use tuples in `typealiases`, thus allowing subclasses to fill out your types with details. This looks fairly useless and complicated, but I've already had a use case where I need to specifically do this.
    
    
    class BaseClass<A,B> {
        typealias Element = (A, B)
        func addElement(elm: Element) {
    	print(elm)
        }
    }
    class IntegerClass<B> : BaseClass<Int, B> {
    }
    let example = IntegerClass<String>()
    example.addElement((5, ""))
    // Prints (5, "")
    

###  Define a Specific Tuple Type

In many of the earlier examples, we re-wrote a certain tuple type like `(Int, Int, String)` multiple times. This, of course, is not necessary per se, as you could define a `typealias` for it:
    
    
    typealias Example = (Int, Int, String)
    func add(elm: Example) {
    }
    

However, if you're using a certain tuple construction so often that you think about adding a typealias for it, you might really be better of defining a struct.

###  Tuples as function parameters

As [Paul Robinson lays out eloquently](http://www.paulrobinson.net/function-parameters-are-tuples-in-swift/) there's a strange similarity between `(a: Int, b: Int, c: String) ->` and `(a: Int, b: Int, c:String)`. Indeed, for the Swift compiler, the parameter header of a method / function is nothing more than a tuple:
    
    
    // Copied from Paul Robinson's blog, you should read the article:
    // http://www.paulrobinson.net/function-parameters-are-tuples-in-swift/
    
    func foo(a: Int, _ b: Int, _ name: String) -> Int     
        return a
    }
    
    let arguments = (4, 3, "hello")
    foo(arguments) // returns 4
    

This looks cool, doesn't it. But wait a minute.. In this case the function signature is a bit specific. What happens when we add or remove labels. Same with the tuple. Well, lets find out:
    
    
    // Lets try with labels:
    func foo2(a a: Int, b: Int, name: String) -> Int {
        return a
    }
    let arguments = (4, 3, "hello")
    foo2(arguments) // fails to work
    
    let arguments2 = (a: 4, b: 3, name: "hello")
    foo2(arguments2) // works! (4)
    

So labelled tuples are supported if the function signature also has labels.

Do we explicitly need to write the tuple into a variable, though?
    
    
    foo2((a: 4, b: 3, name: "hello")) // Error
    

Yeah, bummer, that doesn't work. But what if we get the tuple back from a function call?
    
    
    func foo(a: Int, _ b: Int, _ name: String) -> Int     
        return a
    }
    
    func get_tuple() -> (Int, Int, String) {
        return (4, 4, "hello")
    }
    
    foo(get_tuple()) // Works! returns 4!
    

Awesome, this works!

This has a lot of interesting implications and possibilities. When you plan your types well, you can then move parameters around functions without having to destructure the data.

Even better, for functional programming, you can return a tuple with multiple parameters straight into a function without having to destructure it.

##  Tuple impossibilities

###  Tuples as Dictionary Keys

If you'd like to do the following:
    
    
    let p: [(Int, Int): String]
    

Then this is not possible, because tuples don't conform to the hashable protocol. Which is, really, a bummer as the example above has a multitude of use cases. There may be a crazy type checker hack to extend tuples of varying arities to the hashable protocol, but I haven't really looked into that. If you happen to know if this works, feel free to contact me via [twitter](http://twitter.com/terhechte).

###  Tuple Protocol Compliance

Given the following protocol:
    
    
    protocol PointProtocol {
      var x: Int { get }
      var y: Int { set }
    }
    

You can't tell the type checker that a tuple `(x: 10, y: 20)` complies with that protocol.
    
    
    func addPoint(point: PointProtocol)
    addPoint((x: 10, y: 20)) // doesn't work.
    

##  Changes

****07/23/2015**** Added section on tuples as function parameters

****08/06/2015**** Updated the Reflection example to the latest Swift beta 4. (It removes the `reflect` call)

****08/12/2015**** Updated the **Tuples as function parameters** with a couple more examples and more information.

****08/13/2015**** Fixed a couple of bugs..
