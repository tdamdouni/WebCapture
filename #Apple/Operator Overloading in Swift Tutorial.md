# Operator Overloading in Swift Tutorial

_Captured: 2015-11-25 at 20:43 from [www.raywenderlich.com](http://www.raywenderlich.com/80818/operator-overloading-in-swift-tutorial)_

![Learn how to overload operators in Swift!](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/iOS-8-Feast-Swift-250x250.png)

> _Learn how to overload operators in Swift!_

_Note from Ray:_ This is a brand new Swift tutorial released as part of the [iOS 8 Feast](http://www.raywenderlich.com/?p=82230). Enjoy!

As you've learned in earlier tutorials in the iOS 8 Feast, Swift offers many powerful modern programming features, such as generics, functional programming, first class enums and structs, and more.

But there's another new feature of Swift that you should know and love: _operator overloading_!

This is a fancy way of saying you can make operators like `+`, `-`, `/`, or `*` to work with any type you'd like! You can even define your own operators if you're feeling especially creative.

For example, we use operator overloading in our [Swift Sprite Kit utility library](https://github.com/raywenderlich/SKTUtils/tree/swift) to add and multiply `CGPoints` like this:
    
    
    let pt1 = CGPoint(x: 10, y: 20)
    let pt2 = CGPoint(x: -5, y: 0)
    let pt3 = pt1 + pt2
    let pt4 = pt3 * 100

Handy, eh? Get ready to overload your Swift development powers - [to over 9,000](https://www.youtube.com/watch?v=SiMHTK15Pik)!

_Note:_ This Swift functional programming tutorial assumes you already know the basics of Swift development. If you are new to Swift, we recommend you check out some of our [other Swift tutorials](http://www.raywenderlich.com/?page_id=2519) first.

## Operators: An Overview

_Note:_ This section is optional if you would like a review of operators and precedence. If you are already familiar with this, just create an empty playground and proceed to the next section: Overloading.

Begin by creating a new playground to help you explore operators.

Add the following line to your playground:

You'll see the expected result:

There are two familiar operators in play here:

  1. First, you define a variable named `simpleSum` and set its value with the assignment operator (`=`).
  2. Second, you sum the two integers using the addition operator (`+`). 

You'll be overriding operators like these in this tutorial. But first, you need to understand the concept of _precedence_.

### Precedence

You may remember from math class in school that rules of precedence apply to operators. These rules give some operators higher priority than others; higher-priority operators are applied first. For instance, you multiply before adding or subtracting.

Enter the following in your playground to confirm Swift operators follow these same rules:

You'll see the following result:

In cases where arithmetic operators have the same precedence, Swift evaluates the operators from left to right. In this example, this means operations are completed in the following order:

  1. `3 * 2`: subtraction.
  2. `1 + 3`: Because the leftmost operator is applied first for operations with equal precedence.
  3. `4 - 6`: This operation is completed upon the results of the prior operations.

### Adding Isn't Just for Ints

Integer arithmetic works as expected. But can you use the `+` operator for other types as well?

It turns out you can! Try it for yourself by adding this line to your playground:

You might expect this to add each element of the same position together. Instead, you'll see something like this:

In this case, Swift interprets the `+` as an _append_ instruction. But what if you _did_ want to add each element by position? This is known as _vector addition_.

Well, you could add a custom function to do this. Give it a try by adding the following to your playground:
    
    
    func add(left: [Int], right: [Int]) -> [Int] {
        var sum = [Int]() 
        assert(left.count == right.count, "vector of same length only") 
        for (key, v) in enumerate(left) {
            sum.append(left[key] + right[key]) 
        }
        return sum
    }

Here you define a global function that takes two integer arrays as input, checks that they have the same length, sums the values of each vector element and stores the resulting values in a new array.

Now add the following to confirm that your new function works:

You'll see the following in the console:

It works! But rather than having to call a function do this, wouldn't it be nice to use the `+` operator instead?

With Swift, this is possible--with the power of _operator overloading_!

## Operator Overloading

Operator overloading allows you to change the way existing operators work with specific structures or classes. This is exactly what you need - you'd like to change the way the `+` operator works with `Int` arrays!

Because operator overloading is global to the playground scope, start with a new playground sheet to avoid impacting your earlier examples. Then add the following to your playground:
    
    
    func +(left: [Int], right: [Int]) -> [Int] { // 1
        var sum = [Int]() // 2
        assert(left.count == right.count, "vector of same length only")  // 3
        for (key, v) in enumerate(left) {
          sum.append(left[key] + right[key]) // 4
        }
        return sum
    }

You've just defined a global function called `+` that takes two `Int` arrays as input and returns a single `Int` array. Here's a breakdown of how it works:

  1. Note there's nothing fancy about this function definition. It's a normal function definition except you use `+` for the name!
  2. Here you create an empty `Int` array.
  3. This sample will only work with input arrays of the same length, and this `assert` enforces that.
  4. You then enumerate through the left array, and sum each value with the corresponding value in the right array at the same position.

Test this function by adding the following to your playground:

Finally--the expected results of your vector addition operator! You will see the following in the console:

Of course, operator overloading isn't all fun and games. It would be fairly confusing to someone jumping into your code if they were expecting the default behavior. For that matter, there's nothing to stop you from overriding the `+` operator to, for example, perform subtraction on integers--the risks are obvious!

![OperatorRage](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/OperatorRage.png)

Remember the operator overloading mantra: _with great power comes great responsibility._

Typically, you'll use overloading to extend an operation to a new object while maintaining the original semantics, rather than defining different (and confusing) behavior.

In this example, the behavior override does maintain semantics; vector addition is still a form of addition. But you may still want the ability to append arrays, and you want to avoid confusing yourself months down the road when you've forgotten you overrode the default behavior for `Int` arrays.

Fortunately, Swift lets you create your own custom operators.

## Defining Custom Operators

There are three steps to define a custom operator:

  1. Name your operator
  2. Choose a type
  3. Assign precedence and associativity

Let's go over these one by one.

### Naming Your Operator

Now, you have to pick a character for your operator. Custom operators can begin with one of the ASCII characters `/`, `=`, `-`, `+`, `!`, `*`, `%`, `<`, `>`, `&`, `|`, `^`, or `~`, or with one of the Unicode characters. This gives you a broad range of possible characters. Don't go crazy, though--remember that you'll have to type these characters repeatedly and the fewer keystrokes, the better.

In this case, you'll copy and paste the Unicode symbol `⊕`, a representation of [direct sum](http://en.wikipedia.org/wiki/Direct_sum) that fits your purposes nicely.

### Choosing a Type

With Swift, you can define _binary_, _unary_ and _ternary_ operators. These indicate the number of targets involved.

  * _Unary_ operators involve a single target and are defined either as _postfix_ (`i++`) or _prefix_ (`++i`), depending on where they appear in relation to the target.
  * _Binary_ operators are _infix_ because they appear in between the two targets, for example `1 + 1`.
  * _Ternary_ operators operate on three targets. In Swift, the conditional operator is the only Ternary operator, for example `a ? b : c`.

You should choose between these based on the number of targets of your operation. You want to add two arrays (i.e. 2 targets), so you will define a binary operator.

### Assigning Precedence and Associativity

Because operators are defined globally, you need to choose the associativity and precedence of your custom operator with care.

This can be tricky, so a good rule of thumb is to find a comparable standard operator defined in the [Swift language reference](https://developer.apple.com/library/prerelease/mac/documentation/Swift/Conceptual/Swift_Programming_Language/Expressions.html#//apple_ref/doc/uid/TP40014097-CH32-XID_720) and use similar semantics. For example, to define vector addition, it makes sense to use the same associativity and precedence as the `+` operator.

### Coding Your Custom Operator

Back in your playground, enter the following to define your custom operator. You'll probably want to copy and paste the ⊕ for simplicity.
    
    
    infix operator ⊕ { associativity left precedence 140 } // 1
    func ⊕(left: [Int], right: [Int]) -> [Int] { // 2
        var sum = [Int](count: left.count, repeatedValue: 0)
        assert(left.count == right.count, "vector of same length only")
        for (key, v) in enumerate(left) {
            sum[key] = left[key] + right[key]
        }
        return sum
    }

This code is similar to your earlier override, aside from section 1, where you do all of the following:

  * Define an infix/binary operator that operates on two targets and is placed in between those targets.
  * Name the operator ⊕.
  * Set associativity to _left_, indicating that operands of equal precedence will use left associativity to determine order of operation.
  * Set the precedence to _140_, which is the same weight as `Int` addition, as found in the [Swift language reference](https://developer.apple.com/library/prerelease/mac/documentation/Swift/Conceptual/Swift_Programming_Language/Expressions.html#//apple_ref/doc/uid/TP40014097-CH32-XID_720).

The code in section 2 is similar to what you've seen so far - it adds the two arrays item by item, based on their order in the arrays. Test the new operator by adding the following to your playground:

You'll see the same results as the earlier function and override, but this time, you have different operators for different semantics.

### Bonus Round!

Now that you have a good idea of how to create a custom operator, it's time to challenge yourself. You've already created a ⊕ operator to perform vector addition, so use that knowledge to create a ⊖ operator for subtracting `Int` arrays in a similar manner. Give it your best shot, and check your solution against the answer below.

### Remember Related Operators!

If you define a new operator, don't forget to define any related operators.

For example, the addition assignment operator (`+=`) combines addition and assignment into a single operation. Because your new operator is semantically the same as addition, it's a good idea to define the assignment operator for it, as well.

Add the following to _Operator2.playground_:

Line 1 is exactly the same declaration as for the ⊕ operator, except it uses the compound operator symbol.

The trick is on line 2, where you mark the compound assignment operator's left input parameter as `inout`, which means the parameter's value will be modified directly from within the operator function. As a result, the operator doesn't return a value--it simply modifies the input.

Test that this operator works as expected by adding the following to your playground:

You'll see the following in the console:

As you can see, defining your own operators is not difficult at all! :]

## Defining Operators for More Than One Type

Now imagine that you want to define vector addition for decimal points, too.

One way is to overload a new operator for the types `Double` and `Float`, just like you did for `Int`.

It's just a couple of lines of code, but you'll have to use copy/paste. If you're like me--a clean code addict--then duplicating code is not your first choice, as it makes your code harder to maintain.

### Generics to the Rescue!

Luckily, Swift generics can help with exactly this! If you need a refresher on Swift generics, check out our [Swift Generics Tutorial](http://www.raywenderlich.com/?p=82572) released earlier this week.

Start a new playground so you have a clean slate. Add the following to your new playground:
    
    
    infix operator ⊕ { associativity left precedence 140 }
    func ⊕<T>(left: [T], right: [T]) -> [T] { // 1
        var minus = [T]()
        assert(left.count == right.count, "vector of same length only")
        for (key, v) in enumerate(left) {
            minus.append(left[key] + right[key]) // 2
        }
        return minus
    }

On line 1, you define a generic function called ⊕ that works with a placeholder type signified by `T`. The playground isn't happy. You'll see a compile error that looks like this: `Could not find an overload for '+' that accepts the supplied arguments.`

The error comes from line 2, where you're attempting to use the `+` operator on the values `left` and `right`, which are the placeholder type. Swift doesn't know how to apply a `+` operand to those variables, because it has no idea what type they are!

### Extending With a Protocol

Erase your old code and replace it with the following:
    
    
    protocol Number {  // 1
        func +(l: Self, r: Self) -> Self // 2
    }
     
    extension Double : Number {} // 3
    extension Float  : Number {}
    extension Int    : Number {}
     
    infix operator ⊕ { associativity left precedence 140 }
    func ⊕<T: Number>(left: [T], right: [T]) -> [T] { // 4
        var minus = [T]()
        assert(left.count == right.count, "vector of same length only")
        for (key, v) in enumerate(left) {
            minus.append(left[key] + right[key])
        }
        return minus
    }

You're doing quite a lot here, so let's take a step back and break it down.

  1. You define a protocol called `Number`.
  2. The `Number` protocol defines an operator called `+`.
  3. You create an extension for `Double`, `Float` and `Int` data types that causes them to adopt the `Number` protocol.
  4. You use a _type constraint_ that requires `T` to conform to the `Number` protocol. 

Ultimately, you're telling the compiler that the generic type `T` understands the `+` operand. Now that you've cleared the compile error, try out the operand with arrays of `Double`s and, separately, with `Int`s by adding the following code:

You'll see the following in your console:
    
    
    [4.0, 6.0]
    [3, 6]
    

The operand now works with multiple data types and involves no duplication of code. If you wanted to add more numeric types, you could simply add a markup extension conforming to `Number`.

## How Can I Use Overloading in Real Life?

Do you think I'd let you spend your time on this tutorial if I wasn't convinced of its usefulness? :] This section will employ a practical example to give you a better idea of how to use overloading in your own projects.

### Operators and CGPoints

For this demo, you'll use the [SKTUtils library](https://github.com/raywenderlich/SKTUtils/tree/swift), a collection of handy Sprite Kit helper classes, written for the second edition of our [iOS Games by Tutorials](http://www.raywenderlich.com/?page_id=48022) book.

You can find the repo of the framework on [github](https://github.com/raywenderlich/SKTUtils/tree/swift). Clone the Swift branch of the repo by typing the following into a Terminal window:

Alternatively, you can download the ZIP of the Swift branch from [github](https://github.com/raywenderlich/SKTUtils/tree/swift).

Open _SKUTils/Examples/Playground/SKUTils.xcodeworkspace_ and build the project (you must build the project at least once for the associated framework to be compiled).

Then navigate to _MyPlayground.playground_ from the project navigator. Delete what is currently in the playground and add the following code:
    
    
    import SKTUtils 
     
    let pt1 = CGPoint(x: 10, y: 20)
    let pt2 = CGPoint(x: -5, y: 0)
    let pt3 = pt1 + pt2 
    let pt4 = pt3 * 100

You might be surprised to see that you're successfully using the `+` and `*` operators on a `CGPoint` without a word of complaint from the compiler.
    
    
    {x 10 y 20}
    {x -5 y 0}
    {x 5 y 20}
    {x 500 y 2,000}
    

The magic here is coming from SKTUtils, which you've imported up top. Let's take a closer look.

### Overloading in SKTUtils 

Navigate to _SKTUtils/CGPoint+Extension.swift_ in the project navigator. You'll see that this class defines an extension on `CGPoint` that, among other things, overloads the `+` operator as well as the corresponding compound assignment (`+=`) operator.
    
    
    public func + (left: CGPoint, right: CGPoint) -> CGPoint {
      return CGPoint(x: left.x + right.x, y: left.y + right.y)
    }
     
    public func += (inout left: CGPoint, right: CGPoint) {
      left = left + right
    }

The code is similar to what you did earlier, but notice the access control set to `public`. Access control restricts access to parts of your code from code in other source files and modules. As SKTUtils is a framework, its utilities need to be accessible from outside its module and it is thus defined as public.

The prestidigitation explained, there is no magic, after all--just smart coding!

Adding, subtracting, and multiplying `CGPoint`s is a very common operation in games, so overloading operators to work on `CGPoint`s greatly simplified the code in the book, making it much more concise and easier to read. I'm sure you can find similar examples in your own projects!

Operator overloading is a powerful feature of Swift that can make development much more efficient, if you do it with care.

## Where to Go From Here?

You've reached the end of this tutorial--I hope you enjoyed it! You can find copies of the final playground files [here](http://cdn5.raywenderlich.com/wp-content/uploads/2014/09/OperatorsPlaygrounds.zip) and [here](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/SKTUtils.zip).

If you'd like to learn more about operator overloading and Swift in general, check out our new book [Swift by Tutorials](http://www.raywenderlich.com/?page_id=74805).

I hope you find a way to use operator overloading in your own projects! But remember, _with great power comes great responsibility_ - don't be Troll Dev! ;]

If you have any questions or comments on this tutorial or on operator overloading in general, please join the forum discussion below!
