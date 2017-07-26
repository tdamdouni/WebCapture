# Swift: Type Annotations

_Captured: 2015-10-10 at 13:29 from [ios-blog.co.uk](http://ios-blog.co.uk/tutorials/swift-type-annotations/)_

Type Annotations in Swift are a really useful way to make sure that the specified value matched that of the expected value. This is extremely useful when using functions and declaring your variables.

So what are type annotations? Well they are a simple way to specify what value should be going into your variables and constants. Now, swift is a type safe language which means that you must assign a value that is the type of the annotated variable.

You shouldn't need to use Type Annotation that much as Swift is extremely good at inferring what type of value can be assigned.

The easiest way is for me to show you. So, lets say that you have a variable called player name and you want to pass in a string. You would do this like so:
    
    
    1  
    
    var playerName = “Mark”
    
    
    

Swift has inferred that it is a variable of type String, meaning if we try to assign an integer value like this:

we would get the error message:

**Type 'String' does not conform to protocol 'IntegerLiteralConvertable'**

And all this is saying is that they both have different types and thus swift cannot pass an integer value into the variable as its expecting a String.

IF you wanted to be specific and create a string type annotation at the beginning of your code or in another included file. You can do this like so:
    
    
    1  
    
    var playerName: String;
    
    
    

again, if you try and assign a string to the variable playerName you will be fine, like so:
    
    
    1  
    
    playerName = “Mark”
    
    
    

but if you try to assign an integer like so:

We would get the error message:

**Type 'String' does not conform to protocol 'IntegerLiteralConvertable'**

I hope this clears things up. Please leave your comments and thoughts below.
