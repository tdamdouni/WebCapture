# Swift Tutorial: Variables and Constants

_Captured: 2015-11-25 at 20:52 from [www.raywenderlich.com](http://www.raywenderlich.com/117139/swift-tutorial-variables-and-constants)_

_Note from Ray:_ This is an abridged version of a chapter from the [Swift Apprentice](http://www.raywenderlich.com/store/swift-apprentice), to give you a sneak peek of what's inside the book, released as part of the [iOS 9 Feast](http://www.raywenderlich.com/113226/introducing-the-ios-9-feast). We hope you enjoy!

![A Swift 2 tutorial for the iOS 9 Feast!](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_Swift2-250x250.jpg)

> _[A Swift 2 tutorial for the iOS 9 Feast!](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_Swift2.jpg)_

At its simplest, computer programming is all about manipulating data.

Everything you see on your screen can be reduced to numbers that you send to the CPU. Sometimes you yourself represent and work with this data as various types of numbers, but other times the data comes in more complex forms such as text, images and collections.

In this tutorial, you'll discover constants, variables, types and tuples, and learn how to declare them, name them and change them. You'll also learn about type inference, one of Swift's most important features and one that will make your coding life a lot easier.

## Naming data

In your Swift code, you can give each piece of data a name you can use to refer to it later. The name carries with it an associated _type_ that denotes what sort of data the name refers to: text, numbers, a date, etc.

### Constants

Take a look at your first bit of Swift:
    
    
    let number: Int = 10

This declares a constant called `number` which is of type `Int`. Then it sets the value of the constant to the number `10`.

The type `Int` can store integers--that is, whole numbers. It would be rather limiting be able to store only whole numbers, so there's also a way to store decimals. For example:
    
    
    let pi: Double = 3.14159

This is similar to the `Int` constant, except the name and the type are different. This time the constant is a `Double`, a type that can store decimals with high precision.

There's also a type called `Float`, short for floating point, that stores decimals with lower precision than `Double`. A `Float` takes up less memory than a `Double` but generally, memory use for numbers isn't a huge issue and you'll see `Double` used in most places.

Once you've declared a constant, you can't change its data. For example, consider the following code:
    
    
    let number: Int = 10
    number = 0

This code produces an error:

In Xcode, you would see the error represented this way:

![01_Constant_reassign_error](http://cdn1.raywenderlich.com/wp-content/uploads/2015/10/01_Constant_reassign_error-480x30.png)

Constants are useful for values that aren't going to change. For example, if you were modeling an airplane and needed to keep track of the total number of seats available, you could use a constant.

You might even use a constant for something like a person's age. Even though their age will change as their birthday comes, you might only be concerned with their age at this particular instant.

### Variables

Often you want to change the data behind a name. For example, if you were keeping track of your bank account balance with deposits and withdrawals, you might use a variable rather than a constant.

If your program's data never changed, then it would be a rather boring program! But as you've seen, it's not possible to change the data behind a constant.

When you know you'll need to change some data, you should use a variable to represent that data instead of a constant. You declare a variable in a similar way, like so:

Only the first part of the statement is different: You declare constants using `let`, whereas you declare variables using `var`.

Once you've declared a variable, you're free to change it to whatever you wish, as long as the type remains the same. For example, to change the variable declared above, you could do this:

To change a variable, you simply set it equal to a new value.

This is a good time to introduce the results sidebar of the playground. When you type the code above into a playground, you'll see that the results sidebar on the right shows the current value of `variableNumber` at each line:

![02_Variables_results_sidebar](http://cdn4.raywenderlich.com/wp-content/uploads/2015/10/02_Variables_results_sidebar-480x56.png)

The results sidebar will show a relevant result for each line, if one exists. In the case of a variable or constant, the result will be the new value, whether you've just declared a constant, or declared or reassigned a variable.

### Naming

Always try to choose meaningful names for your variables and constants.

A good name _specifically_ describes what the variable or constant represents. Here are some examples of good names:

  * `personAge`
  * `numberOfPeople`
  * `gradePointAverage`

Often a bad name is simply not descriptive enough. Here are some examples of bad names:

  * `a`
  * `temp`
  * `average`

The key is to ensure that you'll understand what the variable or constant refers to when you read it again later. Don't make the mistake of thinking you have an infallible memory! It's common in computer programming to look back at code as early as a day or two later and have forgotten what it does. Make it easier for yourself by giving your variables and constants intuitive, precise names.

In Swift, you can even use the full range of Unicode characters. This means you could, for example, declare a variable like so:

That might make you laugh, but use caution with special characters like these. They are harder to type and therefore may end up causing you more pain than amusement.

![bad_choice](http://cdn2.raywenderlich.com/wp-content/uploads/2015/10/bad_choice-480x178.png)

Special characters like these probably make more sense in _data_ that you store rather than in Swift code.

### Type conversion

Sometimes you'll have data in one format and need to convert it to another. The naive way to attempt this would be like so:

Swift will complain if you try to do this and spit out an error on the third line:

Some programming languages aren't as strict and will perform simple numeric conversions like this automatically. Swift, however, is very strict about the types it uses and won't let you assign a value of one type to a variable of another type.

Remember, computers rely on us programmers to tell them what to do. In Swift, that includes being explicit about type conversions. If you want the conversion to happen, you have to say so!

Instead of simply assigning, you need to explicitly say that you want to convert the type. You do it like so:

The assignment on the third line now tells Swift unequivocally that you want to convert from the original type, `Double`, to the new type, `Int`.

## Tuples

Sometimes data comes in pairs or triplets. An example of this is a pair of (x, y) coordinates on a 2D grid. Similarly, a set of coordinates on a 3D grid is comprised of an x-value, a y-value and a z-value.

In Swift, you can represent such related data in a very simple way through the use of a _tuple_.

A tuple is a type that represents data composed of more than one value of any type. You can have as many values in your tuple as you like For example, you can define a pair of 2D coordinates where each axis value is an integer, like so:

The type of `coordinates` is a tuple containing two `Int` values. The types of the values within the tuple, in this case `Int`, are separated by commas surrounded by parentheses. The code for creating the tuple is much the same, with each value separated by commas and surrounded by parentheses.

You could similarly create a tuple of `Double` values, like so:

Or you could mix and match the types comprising the tuple, like so:

And here's how to access the data inside a tuple:

You can reference each item in the tuple by its position in the tuple, starting with zero. So in this example, `x` will equal `2` and `y` will equal `3`.

In the example above, it may not be immediately obvious that the first value, at index 0, is the x-coordinate and the second value, at index 1, is the y-coordinate. This is another demonstration of why it's important to _always_ name your variables in a way that avoids confusion.

Fortunately, Swift allows you to name the individual parts of a tuple, so you to be explicit about what each part represents. For example:

Here, the code annotates the type of `coordinatesNamed` to contain a label for each part of the tuple.

Then, when you need to access each part of the tuple, you can access it by its name:

This is much clearer and easier to understand. More often than not, it's helpful to name the components of your tuples.

If you want to access multiple parts of the tuple at the same time, as in the examples above, you can also use a shorthand syntax to make it easier:

This declares three new constants, `x`, `y` and `z`, and assigns each part of the tuple to them in turn. The code is equivalent to the following:

If you want to ignore a certain element of the tuple, you can replace the corresponding part of the declaration with an underscore. For example, if you were performing a 2D calculation and wanted to ignore the z-coordinate of `coordinates3D`, then you'd write the following:

This line of code only declares `x` and `y`. The `_` is special and simply means you're ignoring this part for now.

## Type inference

Every time you've seen a variable or constant declared, there's been an associated type. That is, until you saw the syntax for reading multiple values from a tuple at the same time. Take a look at it again:

There's nothing on the second line to indicate that `x`, `y` and `z` are of type `Int`. So how does Swift know that they are of type `Int`?

Reading the code yourself, it's clear that the constants created on the second line are of type `Int`. You know that because the code declares a tuple comprising three `Int` values.

It turns out the Swift compiler can do this process of deduction, as well. It doesn't need you to tell it the type--it can figure it out on its own. Neat! :]

As it happens, you can drop the type in other places besides tuples. In fact, in most places, you can omit the type because Swift already knows it.

For example, consider the following constant declaration:

The value on the right-hand side is an integer type. Swift knows this, too, and therefore it _infers_ that the type of the constant should be an `Int`. This process is known as _type inference_, and it's a key component of Swift's power as a language.

Sometimes it's useful to check the inferred type of a variable or constant. You can do this in a playground by holding down the _Option_ key and clicking on the variable or constant's name. Xcode will display a popover like this:

![03_Type_inferred_Int](http://cdn5.raywenderlich.com/wp-content/uploads/2015/10/03_Type_inferred_Int-480x81.png)

Xcode tells you the inferred type by giving you the declaration you would have had to use if there were no type inference. In this case, the type is `Int`.

It works for other types, too:

Option-clicking on this reveals the following:

![04_Type_inferred_Double](http://cdn4.raywenderlich.com/wp-content/uploads/2015/10/04_Type_inferred_Double-480x78.png)

You can see from this that type inference isn't magic. Swift is simply doing what your human brain does very easily. Programming languages that don't use type inference can often feel verbose, because you need to specify the often obvious type each time you declare a variable or constant.

## Where to go from here?

In this tutorial you have learned about one of the fundamentals of Swift and programming in general. Variables and constants will follow you throughout the course of your Swift career.

By defining things as either variables or constants with a type, Swift will help you keep track of your data. With type inference, Swift also lets you be more concise with syntax when it can figure things out.

This post is an excerpt from the [Swift Apprentice](http://www.raywenderlich.com/store/swift-apprentice). Pick up a copy of the book if you'd like to learn more about Swift right from the foundations.

If you have any questions or comments on this tutorial, please join the forum discussion below!
