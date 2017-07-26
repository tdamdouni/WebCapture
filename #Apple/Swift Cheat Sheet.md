## Swift Cheat Sheet

#### Variables 

```swift
`var myNumber = 5  
myNumber = 6 // setting the value of myNumber to now be 6 instead of 5
var myDouble:Double = 5 // explicitly defining  myDouble to be a Double type  
```
`
#### Constants 

```swift
`let myNumber = 5
myNumber = 4 // error, not allowed to mutate myNumber
```
`
#### Types 

```
`Int: A whole number ex) 5  
Double: A number with more precision ex) 5.55  
String: A collection of characters inside quotation marks ex) "Hello"
Bool: true or false
```
`
#### Control Flow 

```swift
`var firstNumber = 1
var secondNumber = 1

if firstNumber == secondNumber {

// write code in here to run if firstNumber is equal to secondNumber

} else {

// write code in here to run if firstNumber is NOT equal to secondNumber

}
```
`
```swift
`var finalNumber = 5

for i in 1...finalNumber {
print(i)
}

// prints the numbers 1 to 5

```
`
### Functions and Methods

```swift
`func greet() {
print("Hello!")
}

func greet(name:String) {
print("Hello \(name)")
}

func greet(name:String) -\> String{
return "Hello \(name)"
}
```
`
#### Arrays 

```swift
`var scores = [74, 94, 88]()
scores[0]() // returns 74
scores[3]() // error, nothing in index 3
scores[3]() = 99 // sets the value at index 3 to be 99

var scores = [Int]()() // initializes a blank array where every element in this array is an Int

```
`
#### Dictionaries

```swift
`var scores:[String:Int]() = ["Dan": 74, "Paul": 94]()
scores["Tom"]() = 88 //scores now has a value for the key "Tom"

var scores = [String:Int]()() // initializes a blank dictionary where the key is of type String, and the value is of type Int

```
`
#### Classes

```swift
`
class ClassName : ParentClass {

let aVariable = 0

func aFunction() -\> String {
returns "A String"
}


}

````

