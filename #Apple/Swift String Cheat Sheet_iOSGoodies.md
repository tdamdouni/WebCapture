# Swift String Cheat Sheet

_Captured: 2016-03-10 at 18:09 from [useyourloaf.com](http://useyourloaf.com/blog/swift-string-cheat-sheet/)_

The Swift String API is [hard](https://www.mikeash.com/pyblog/friday-qa-2015-11-06-why-is-swifts-string-api-so-hard.html) to get used to. It has also changed over time as the Swift language and the standard library have developed. Those answers you found on Stack Overflow that worked with Swift 1.2 may not work as expected (or at all) with Swift 2. On the plus side I am finding the Apple documentation to be helpful (see bottom of the post for links). So for my future reference and hopefully to help others also struggling here is my still growing list of String code snippets:

(_Also available as a [Gist](https://gist.github.com/kharrison/08d1db4169d70a88b194) and a [Playground](https://github.com/kharrison/CodeExamples/tree/master/Playgrounds/String.playground) in my GitHub repository_)

### Initializing a String

There are an almost endless number of ways to create a String, using literals, conversions from other Swift types, Unicode, etc.
    
    
    var emptyString = ""        // Empty String
    var stillEmpty = String()   // Another empty String
    let helloWorld = "Hello World!" // String literal
    
    let a = String(true)        // from boolean: "true"
    let b: Character = "A"      // Explicit type to create a Character
    let c = String(b)           // from character "A"
    let d = String(3.14)        // from Double "3.14"
    let e = String(1000)        // from Int "1000"
    let f = "Result = \(d)"     // Interpolation "Result = 3.14"
    let g = "\u{2126}"          // Unicode Ohm sign Ω
    let h = String(count:3, repeatedValue:b) // Repeated character "AAA"
    

### Strings are Value Types

Strings are value types that are copied when assigned or passed to a function. The copy is performed lazily on mutation.
    
    
    var aString = "Hello"
    var bString = aString
    bString += " World!"    // "Hello World!"
    print("\(aString)")     // "Hello\n"
    

### Testing String (Empty, Equality and Order)

To test for an empty String:
    
    
    emptyString.isEmpty         // true
    

Swift is Unicode correct so the equality operator ("==") checks for Unicode _canonical equivalence_. This means that two Strings that are composed from different Unicode scalars will be considered equal if they have the same linguistic meaning and appearance:
    
    
    let spain = "España"
    let tilde = "\u{303}"
    let country = "Espan" + "\(tilde)" + "a"
    if country == spain {
      print("Matched!")       // "Matched!\n"
    }
    

Comparing for order:
    
    
    if "aaa" < "bbb" {
      print("aaa")
    }
    

### Testing for suffix/prefix

Quick way for testing if a String for a suffix or prefix:
    
    
    let line = "0001 Some test data here %%%%"
    line.hasPrefix("0001")    // true
    line.hasSuffix("%%%%")    // true
    

### Converting to upper/lower case

Does as the name suggests:
    
    
    let mixedCase = "AbcDef"
    let upper = mixedCase.uppercaseString // "ABCDEF"
    let lower = mixedCase.lowercaseString // "abcdef"
    

### Views

Strings are not collections of anything but do provide collection views for different representations accessed through the appropriate property:
    
    
    country.characters       // characters
    country.unicodeScalars   // Unicode scalar 21-bit codes
    country.utf16            // UTF-16 encoding
    country.utf8             // UTF-8 encoding
    

### Counting

String does not directly have a property to return a count as it only has meaning for a particular representation. So count is implemented on each of the collection views:
    
    
    // spain = España
    print("\(spain.characters.count)")      // 6
    print("\(spain.unicodeScalars.count)")  // 6
    print("\(spain.utf16.count)")           // 6
    print("\(spain.utf8.count)")            // 7
    

### Using Index to Traverse a Collection

Each of the collection views has an Index that you use to traverse the collection. This is maybe one of the big causes of pain when getting to grips with String. You cannot randomly access an element in a string using a subscript (e.g. string[5]).

To iterate over all items in a collection (I will use the characters collection from now on) with a for..in loop:
    
    
    var sentence = "Never odd or even"
    for character in sentence.characters {
      print(character)
    }
    

Each collection has two instance properties you can use as subscripts to index into the collection:

  * **startIndex**: the position of the first element if non-empty, else identical to endIndex.
  * **endIndex**: the position just "past the end" of the string.

_Note the choice for endIndex means you cannot use it directly as a subscript as it is out of range._
    
    
    let cafe = "café"
    cafe.startIndex   // 0
    cafe.endIndex     // 4 - after last char
    

The startIndex and endIndex properties become more useful when modified with the following methods:

  * successor() to get the next element
  * predecessor() to get the previous element
  * advancedBy(n) to jump forward/backward by n elements

Some examples, note that you can chain operations if required:
    
    
    cafe[cafe.startIndex]                         // "c"
    cafe[cafe.startIndex.successor()]             // "a"
    cafe[cafe.startIndex.successor().successor()] // "f"
    
    // Note that cafe[endIndex] is a run time error
    cafe[cafe.endIndex.predecessor()]             // "é"
    cafe[cafe.startIndex.advancedBy(2)]           // "f"
    

The indices property returns a range for all elements in a String that can be useful for iterating through the collection:
    
    
    for index in cafe.characters.indices {
      print(cafe[index])
    }
    

You cannot use an index from one String to access a different string. You can convert an index to an integer value with the distanceTo method:
    
    
    let word1 = "ABCDEF"
    let word2 = "012345"
    let indexC = word1.startIndex.advancedBy(2)
    let distance = word1.startIndex.distanceTo(indexC) // 2
    let digit = word2[word2.startIndex.advancedBy(distance)] // "2"
    

### Using a range

To identify a range of elements in a String collection use a range. A range is just a start and end index:
    
    
    let fqdn = "useyourloaf.com"
    let rangeOfTLD = Range(start: fqdn.endIndex.advancedBy(-3), 
                             end: fqdn.endIndex)
    let tld = fqdn[rangeOfTLD] // "com"
    

Alternate creation of range using the "…" or "..<" operators:
    
    
    let rangeOfDomain = fqdn.startIndex..<fqdn.endIndex.advancedBy(-4)
    let domain = fqdn[rangeOfDomain] // "useyourloaf"
    

### Getting a substring using Index or Range

Various methods to get a substring identified by an index or range:
    
    
    var template = "<<<Hello>>>"
    let indexStartOfText = template.startIndex.advancedBy(3)
    let indexEndOfText = template.endIndex.advancedBy(-3)
    let subString1 = template.substringFromIndex(indexStartOfText) // Hello>>>
    let subString2 = template.substringToIndex(indexEndOfText)     // <<<Hello
    
    let rangeOfHello = indexStartOfText..<indexEndOfText
    // Both the following should return the String "Hello"
    let subString3 = template.substringWithRange(rangeOfHello)
    let subString4 = template.substringWithRange(indexStartOfText..<indexEndOfText)
    

### Getting a Prefix or Suffix

If you just need to drop/retrieve elements at the beginning or end of a String:
    
    
    let digits = "0123456789"
    let tail = String(digits.characters.dropFirst())  // "123456789"
    let less = String(digits.characters.dropFirst(3)) // "3456789"
    let head = String(digits.characters.dropLast(3))  // "0123456"
    
    let prefix = String(digits.characters.prefix(2))  // "01"
    let suffix = String(digits.characters.suffix(2))  // "89"
    
    let index4 = digits.startIndex.advancedBy(4)
    let thru4 = String(digits.characters.prefixThrough(index4)) // "01234"
    let upTo4 = String(digits.characters.prefixUpTo(index4))    // "0123"
    let from4 = String(digits.characters.suffixFrom(index4))    // "456789"
    

### Inserting/removing

To insert a character at position given by an index:
    
    
    var stars = "******"
    stars.insert("X", atIndex: stars.startIndex.advancedBy(3))
    // "***X***"
    

To insert a string at index (converting to characters):
    
    
    stars.insertContentsOf("YZ".characters, at: stars.endIndex.advancedBy(-3))
    // "***XYZ***"
    

### Replace with Range

To replace with a range:
    
    
    // "***XYZ***"
    let xyzRange = stars.startIndex.advancedBy(3)..<stars.endIndex.advancedBy(-3)
    stars.replaceRange(xyzRange, with: "ABC")
    // "***ABC***"
    

### Append

You can concatenate strings with the "+" operator or the appendContentsOf method:
    
    
    var message = "Welcome"
    message += " Tim" // "Welcome Tim"
    message.appendContentsOf("!!!") // "Welcome Tim!!!
    

### Remove and return element at index

To remove an element from a String. Note that this method invalidates any indices you may have on the string.
    
    
    var grades = "ABCDEF"
    let ch = grades.removeAtIndex(grades.startIndex) // "A"
    print(grades) // "BCDEF"
    

### Remove Range

To remove a range of characters - this also invalidates any index you may have on the String:
    
    
    var sequences = "ABA BBA ABC"
    let midRange = sequences.startIndex.advancedBy(4)...sequences.endIndex.advancedBy(-4)
    sequences.removeRange(midRange)  // "ABA ABC"
    

### Bridging to NSString

String is bridged to Objective-C as NSString. If the Swift Standard Library does not have what you need import the Foundation framework to get access to methods defined by NSString.

** Be aware that this is not a toll-free bridge so stick to the Swift Standard Library where possible. **
    
    
    // Don't forget to import Foundation
    import Foundation
    let welcome = "hello world!"
    welcome.capitalizedString     // "Hello World!"
    

### Searching for a substring

An example of using NSString methods to perform a search for a substring:
    
    
    let text = "123045780984"
    if let rangeOfZero = text.rangeOfString("0",
           options: NSStringCompareOptions.BackwardsSearch) {
      // Found a zero, get the following text
      let suffix = String(text.characters.suffixFrom(rangeOfZero.endIndex)) // "984"
    }
    

### Playground

I have found it useful to maintain a playground in Xcode with String code snippets while I get familiar with the API. I have made the [Playground](https://github.com/kharrison/CodeExamples/tree/master/Playgrounds/String.playground) available for download from my GitHub repository if you want to grab it and experiment on your own.

### Further Reading
