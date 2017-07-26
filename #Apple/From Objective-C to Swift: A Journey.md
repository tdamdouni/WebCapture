# From Objective-C to Swift: A Journey

_Captured: 2015-06-12 at 23:12 from [medium.com](https://medium.com/p/c8732c3a3c6)_

I am French. English is not my first language. I apologize in advance for any gallicism which may sneak its way into this article. But first let me explain what a gallicism is: It's a typical French idiom or construct applied to a foreign language. It can be an obvious and clear intention of the speaker, such as when Neo says, "Deja vu," when he sees that black cat for a second time. But when you are French this is usually what your English teacher writes in red on your essays when you've just translated, word for word, a typical French idiom into English. Something like, "It's raining ropes," instead of, "It's raining cats and dogs." I may even be writing some at the moment… Just let me know if you see one.

When I was 13 and learning English, my teacher told me, "A language is all about grammar and vocabulary," and sent me home with pages of vocabulary to memorize. Since then I've learned that a language is a lot more than grammatical rules and vocabulary. Any language has a symbiotic relationship with its culture. Culture and language evolve hand-in-hand, and it can be difficult to know how they are influencing each other. With English, a very dynamic language, you can witness the emergence of new idiomatic expressions or words. In turn, these shape the way we express ourselves, our thoughts, and our reasoning. New words are like new conceptual abstractions which can lead us to think and act differently. George Orwell illustrated this very well in "1984" with Newspeak: a language devoid of nuances, meant to limit the way people think. But you don't need a dystopian future to understand this; just try to express yourself in a foreign language you barely know and tell me how you feel. I usually feel pretty stupid.

### A Learning Opportunity

What does that have to do with Swift? Let me get to this.

I, along with some of my colleagues at [Black Pixel](http://blackpixel.com), have just completed a massive project written entirely in Swift. We developed a uniquely designed universal app for the iPad and iPhone. It took a substantial team of engineers, designers, project managers, and testers the better part of eight months to complete. Until Apple released Swift 1.2 we struggled with compilation times of several minutes every time we made the smallest change.

The decision to move to Swift was very daring for such a project and a great opportunity to learn.

We started by reading The Swift Programming Language, an overview that includes a mix of simple examples and grammatical rules. After overcoming my habit of typing semicolons, I felt comfortable writing code in Swift, but, dare I say, my level of expression in that code was not very fluent. The code I wrote worked but felt clunky and ugly, full of `if` statements and forced unwrapping of optionals.

That code was written in Swift, but it was full of Objective-C idioms. While it worked, it could have been written better. And so my journey began to try to learn more about the cultural fabric of Swift and become a more fluent practitioner of the language.

I was helped along the way by some great engineers. Kevin Ballard and Vic Smith had experience with functional programming, and their knowledge and mastery of the culture behind Swift proved invaluable.

I do not have a preference for one language over the other, and I am _not_ an expert in programming languages. My goal is to merely illustrate a few of the main discoveries I made regarding Swift over the past eight months. For each example I will show a piece of code very similar to what I was writing at the start of the project, these so-called Objective-C idioms. I will also have a functionally identical piece of code written in the spirit of Swift. All code can be directly pasted into Playground to see it in action.

### Optionals and Their ?, !, and ??

Simply put optionals are data containers which may or may not contain data. They are great for safely and clearly expressing data which may not exist, such as the `delegate` of a view controller or any other piece of data. In Swift, if an optional contains no data it is `nil`, otherwise it is not.

Coming from Objective-C, optionals are a weird beast: We are indeed used to dealing with `nil` values either implicitly or explicitly but as values nonetheless. So a typical way to deal with optionals within an Objective-C mindset is quite different from the intended idiomatic use. Here are a few examples:

#### Doing something with an optional when it's not nil

Let's say you want to print the content of your optional only if it's not nil. How would you go about it?
    
    
    // Objective-C idiom: you check that it’s not nil and you unwrap it  
    let anOptional: String? = “bonjour”  
    if anOptional != nil {  
       println(“We say \(anOptional!)”) // Will print “We say bonjour”  
    }
    
    
    // Swift idiom: use optional binding  
    if let anOptional = anOptional {  
       println(“We say \(anOptional)”) // Will print “We say bonjour”  
    }

To me the main hurdle was feeling comfortable allocating a new variable with which to bind my optional. After years of programming, I'd developed a reflex against allocating variables when I don't feel it's needed. But it's fine now. I'm cured!

#### Logical statements involving several optionals

Let's consider two `String?` constants: `bonjour` and `mademoiselle`. We want to write:

  * "Bonjour Mademoiselle" if both are not empty.
  * "Bonjour" if `mademoiselle` is empty.
  * "Comment allez-vous Mademoiselle?" if `bonjour` is empty.
  * "Mmmm…" if both are empty.
    
    
    // Objective-C idiom: using if…else statements checking for nil and force-unwrapping optionals
    
    
    if bonjour != nil && mademoiselle != nil {  
       println(“\(bonjour!) \(mademoiselle!)”)  
    } else if bonjour != nil && mademoiselle == nil {  
       println(bonjour!)  
    } else if bonjour == nil && mademoiselle != nil {  
       println(“Comment allez-vous \(mademoiselle!)?”)  
    } else {  
       println(“Mmmm…”)  
    }

There would be at least two ways to deal with this using a more idiomatic construct in Swift:

  1. Using optional binding on multiple variables and an `if…else` statement.
  2. Using a `switch` statement on the tuple `(bonjour, mademoiselle)`.

I will focus on the `switch` statement because this was the hardest one for me to internalize. Indeed I have been programming using C-based languages for so long that in my mind a `switch` was for `enum` or `integer` types only. This is not the case in Swift where `switch` statements can be used as very powerful filters on any type of data.

Here is an example of using a `switch` statement on the tuple `(bonjour, mademoiselle)`:
    
    
    switch (bonjour, mademoiselle) {  
       case let (.Some(string1), .Some(string2)): // If both optionals are non nil: we unwrap their values into local constants `string1` and `string2`  
          println(“\(string1) \(string2)”)
    
    
       case let (.Some(string1), _): // mademoiselle is nil, bonjour is not: we unwrap bonjour’s value into local constant string1  
          println(“\(string1)”)
    
    
       case let (_, .Some(string2)): // bonjour is nil, mademoiselle is not: we unwrap mademoiselle’s value into local constant string2  
          println(“Comment allez-vous \(string2)?”)
    
    
       case (_, _): // Both are nil  
          println(“Mmmm…”)  
    }

Nowadays I use this type of logical construct almost everywhere instead of the more complex `if…else` because:

  1. It's clear.
  2. The Swift compiler will complain if you have not covered all cases.

#### Comparing an optional with some other value

This took me a while to wrap my head around. I used the Objective-C idiom for a while before finally dropping it entirely. Consider the following examples:
    
    
    // Swift idiom: turn your value into an Optional  
    // Note this is not strictly required. For most types Swift will do this for you

A practical application of this would be when you are overriding the function `traitCollectionDidChange` method on `UIViewController` because you are dealing with `SizeClass`:
    
    
       if previousTraitCollection.userInterfaceIdiom == .Some(self.traitCollection.userInterfaceIdiom) {  
          return  
       }  
       // Do something here  
    }

#### Assigning an optional value to another variable

Sometimes you need to assign an optional value to another variable, for instance assigning an optional `String` to the `text` property of a `UILabel`:
    
    
    func updateLabelWithObjectiveCIdiom(label: UILabel, withString string: String?) {  
       if string != nil {  
          label.text = string!  
       } else {  
          label.text = “This is an empty string”  
       }  
    }
    
    
    // Swift idiom: using the ?? operator on the optional  
    func updateLabelWithSwiftIdiom(label: UILabel, withString string: String?) {  
       label.text = string ?? “This is an empty string”  
    }
    
    
    updateLabelWithObjectiveCIdiom(label, withString: “This is NOT an empty string”)  
    label.text // Contains “This is NOT an empty string”
    
    
    updateLabelWithSwiftIdiom(label, withString: “This is NOT an empty string”)  
    label.text // Contains “This is NOT an empty string”

#### Passing an optional to a function which does not take an optional as parameter

Another interesting thing to know is how to pass an optional to a method which does not take an optional as parameter. Here is a mockup `UIViewController` subclass with a `UILabel` meant to represent a birthday date. This controller has:

  1. A method `updateBirthdayWithDate(date: NSDate?)`.
  2. A lazily initialized `NSDateFormatter` that we will use to convert the `NSDate?` into a `String`.

The method `stringFromDate(date: NSDate)` of `NSDateFormatter` takes an `NSDate` parameter. How would you go about updating your label with the `NSDate?`:
    
    
    class OptionalsViewController : UIViewController {  
       let birthdayLabel : UILabel? = UILabel()  
       lazy var dateFormatter : NSDateFormatter = {  
          let dateFormatter = NSDateFormatter()  
          dateFormatter.dateStyle = .LongStyle  
          dateFormatter.timeStyle = .NoStyle  
          return dateFormatter  
       }()
    
    
       func updateBirthdayWithDate(date: NSDate?) {  
          // NSDateFormatter.stringFromDate takes an NSDate as parameter, not an NSDate?
    
    
          // The Objective-C mindset: making sure date is not nil and force-unwrap  
          if date != nil {  
             self.birthdayLabel?.text =       self.dateFormatter.stringFromDate(date!)  
          }
    
    
          // Swift idiom: use the map function on the optional  
          self.birthdayLabel?.text = date.map({          self.dateFormatter.stringFromDate($0) }) ?? “”  
          }  
       }  
    }

Using Playground you can see this code in action:
    
    
    let controller = OptionalsViewController()  
    controller.updateBirthdayWithDate(NSDate())  
    controller.birthdayLabel?.text // Will print whatever date today is

The `map` function can be called on any optional to unwrap it and call a method on the unwrapped value if it exists. If the optional is nil, the `map` function will return `nil`, which is very convenient if you remember it exists.

### Operating on Arrays

Swift's built-in `Array` type is very powerful once you get to know it. It is tempting to use NSArray or NSMutableArray for some operations until you realize you often don't need to. Here are a few examples, again comparing my initial use of Objective-C idioms with Swift ones.

#### The map function

Let's say you want to pin all edges of a `view` to a `parentView`.
    
    
    // The idiomatic Objective-C way could be to write this:  
    parentView.addConstraints([NSLayoutConstraint(item: view, attribute: .Left, relatedBy: .Equal, toItem: parentView, attribute: .Left, multiplier: 1, constant: 0),  
    NSLayoutConstraint(item: view, attribute: .Right, relatedBy: .Equal, toItem: parentView, attribute: .Right, multiplier: 1, constant: 0),  
    NSLayoutConstraint(item: view, attribute: .Top, relatedBy: .Equal, toItem: parentView, attribute: .Top, multiplier: 1, constant: 0),  
    NSLayoutConstraint(item: view, attribute: .Bottom, relatedBy: .Equal, toItem: parentView, attribute: .Bottom, multiplier: 1, constant: 0)])
    
    
    // Using an Array and the map function, the Swift version would look like this:  
    parentView.addConstraints([NSLayoutAttribute.Left, .Bottom, .Right, .Top].map({ edge in  
       NSLayoutConstraint(item: view, attribute: edge, relatedBy: .Equal, toItem: parentView, attribute: edge, multiplier: 1, constant: 0)}))

This creates an array of `NSLayoutAttribute`: `[NSLayoutAttribute.Left, .Bottom, .Right, .Top]` for all four edges.

Then the `map` function will apply the code in the provided closure to each element in that array.

#### Mutable arrays

Consider the following scenario: You are modeling a company that contains departments. Each department has employees, and you need to build an array containing all employees.

A natural way to do this in Objective-C is to use an `NSMutableArray` to store all employees, iterate over the departments, and call `addObjectsFromArray` to add the department's employees to the store employees.

It would look something like this:
    
    
       // With the Objective-C mindset you would probably write something like this:  
       func allEmployeesObjectiveC() -> NSArray {  
          var employees = NSMutableArray()  
          if self.departments != nil {  
             for department in self.departments! {  
                if department.employees != nil {  
                   employees.addObjectsFromArray(department.employees!)  
                }  
             }  
           }  
          return employees  
       }
    
    
       // Once familiar with Swift idioms your code would probably look like that:  
       func allEmployeesSwift() -> [String] {  
          var employees : [String] = Array()
    
    
          for department in self.departments ?? [] {  
             employees += department.employees ?? []  
          }  
          return employees  
       }  
    }

In Playground you could test to see that you get identical results by writing this:
    
    
    let wizzardDepartment = Department()  
    wizzardDepartment.employees = [“Harry”, “Hermione”, “Ron”]
    
    
    company.allEmployeesSwift()  
    // will print [“Sally”, “Harry”, “Harry”, “Hermione”, “Ron”, “Dan”, “Forrest”, “Buba”]

#### Sorting arrays

Building on the previous example, if you want to sort the resulting array of employees you could write something like this:

Objective-C mindset: the `allEmployeesObjectiveC()` returns an `NSArray` which contains the employees names. Items in this array are of type `AnyObject` and will need to be cast to `String` for comparison.
    
    
    let employeesObjC = company.allEmployeesObjectiveC().sortedArrayUsingComparator {   (name1, name2) -> NSComparisonResult in
    
    
       // Cast `name1` and `name2` to `String`:  
       if let name1 = name1 as? String, name2 = name2 as? String { // This is pretty Swift-like  
          return name1.caseInsensitiveCompare(name2)  
       }  
       return .OrderedSame  
    }

Swift mindset: use the `sorted` function on the array of employees. Since it's an array of `String` we can directly compare the strings together:
    
    
    let employeesSwift = company.allEmployeesSwift().sorted{ $0.caseInsensitiveCompare($1) == .OrderedAscending }

#### Dealing with enums

Swift enums are first class citizens, not just a collection of numbers used to organize options. I must admit that I still struggle to find ways to fully leverage the power of Swift enums. Still, there are a few things I learned along the way.

#### The Printable or DebugPrintable protocols are your friends

`Printable` or `DebugPrintable` are two protocols you should implement for your `enum` if you want to see something other than `(Enum Value)` when you attempt to debug an enum value in lldb.

Here is an example:
    
    
    enum Position: Int, Printable {  
       case Up = 0  
       case Down  
       case Left  
       case Right
    
    
    // This is the whole implementation of the `Printable` protocol  
       var description: String {  
          get {  
             switch self {  
                case .Up:  
                return “Up”
    
    
    case .Right:  
                return “Right”  
             }  
          }  
       }

#### Enums can be any type, not just Int

Below is an enum that lists some of the existing models of iOS hardware. In this case, the benefits of using an enum with a `rawValue` of type `String` is obvious, as are the benefits of having methods on the enum.
    
    
    enum DeviceModel : String, Printable {  
       case iPhone5_3 = “iPhone5,3” // (model A1456, A1532 | GSM)  
       case iPhone5_4 = “iPhone5,4” // (model A1507, A1516, A1526 (China), A1529 | Global)  
       case iPhone6_1 = “iPhone6,1” // (model A1433, A1533 | GSM)  
       case iPhone6_2 = “iPhone6,2” // (model A1457, A1518, A1528 (China), A1530 | Global)  
       case iPhone7_1 = “iPhone7,1” // All iPhone 6 Plus’s  
       case iPhone7_2 = “iPhone7,2” // All iPhone 6's  
       case Unknown = “Unknown
    
    
       var description: String {  
          return rawValue  
       }
    
    
       var name: String {  
          switch self {  
             case .iPhone5_3: return “iPhone 5c”  
             case .iPhone5_4: return “iPhone 5c”  
             case .iPhone6_1: return “iPhone 5s”  
             case .iPhone6_2: return “iPhone 5s”  
             case .iPhone7_1: return “iPhone 6 Plus”  
             case .iPhone7_2: return “iPhone 6”  
             case .Unknown: return “(unknown)”  
          }  
        }
    
    
       var isIphone6Plus: Bool {  
          return self == .iPhone7_1  
       }
    
    
       var isIphone6: Bool {  
          return self == .iPhone7_2  
       }
    
    
       var isIphone5: Bool {  
          let devices: [DeviceModel] = [.iPhone5_1, .iPhone5_2, .iPhone5_3, .iPhone5_4, .iPhone6_1, .iPhone6_2]  
          return contains(devices, self)  
       }  
    }

You could easily use such an enum in a `UIDevice` extension:
    
    
    extension UIDevice {  
       var modelString: String {  
          var systemInfo = utsname()  
          uname(&systemInfo)  
          let identifier = withUnsafeMutablePointer(&systemInfo.machine) {   ptr in String.fromCString(UnsafePointer<CChar>(ptr))}  
          return identifier ?? “”  
       }
    
    
       var modelName: String {  
          let name = self.modelString  
          return DeviceModel(rawValue: name)?.name ?? name  
       }
    
    
       var model: DeviceModel {  
          return DeviceModel(rawValue: self.modelString) ?? .Unknown  
       }  
    }

The added benefit of this is that in your code you could then use a robust `switch` statement on `UIDevice.currentDevice.model`. The mapping is defined once in the `enum` and you no longer need to perform string comparisons which are usually error-prone.

#### Looping over all cases in an enum

There is no built-in `allValues` method for enums, so if you ever want to loop over all the cases in your enum you have to add a method for this. For instance, we could add the following constant to the `Position` enum:
    
    
    enum Position: Int, Printable {  
       case Up = 0  
       case Down  
       case Left  
       case Right
    
    
       // This is the whole implementation of the `Printable` protocol  
       var description: String {  
          get {  
             switch self {  
                case .Up:  
                return “Up”
    
    
                case .Down:  
                return “Down”
    
    
                case .Left:  
                return “Left”
    
    
                case .Right:  
                return “Right”  
             }  
          }  
       }  
    }

With this in place you can very easily iterate over all cases:
    
    
    // Had you not implemented the Printable protocol, you would see: (Enum Value) (Enum Value) (Enum Value) (Enum Value).

### Clearing Hurdles

I realize that some of the examples presented in this article may be simplistic or downright artificial. However, they illustrate some of the most difficult mental challenges that I needed to overcome when transitioning from Objective-C to Swift.

The challenge with learning the Swift language is not the new syntax. That's the easy part. The real hurdles are altering the way we think in order to become fluent speakers of that language, understanding where the language is coming from, mastering its idioms, and ultimately becoming indistinguishable from native speakers. I know I'm not there yet. Are you?
