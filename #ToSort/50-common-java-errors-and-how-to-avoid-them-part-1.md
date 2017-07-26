# 50 Common Java Errors and How to Avoid Them (Part 1)

_Captured: 2017-06-20 at 19:36 from [dzone.com](https://dzone.com/articles/50-common-java-errors-and-how-to-avoid-them-part-1?edition=305104&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-19)_

There are many types of errors that could be encountered while developing Java software, but most are avoidable. We've rounded up 50 of the most common Java software errors, complete with code examples and tutorials to help you work around common coding problems.

For more tips and tricks for coding better Java programs, download our [Comprehensive Java Developer's Guide](http://info.stackify.com/buildbetter-2.2-the-comprehensive-java-developers-guide), which is jam-packed with everything you need to up your Java game - from tools to the best websites and blogs, YouTube channels, Twitter influencers, LinkedIn groups, podcasts, must-attend events, and more.

If you're working with .NET, you should also check out our guide to the [50 most common .NET software errors](https://stackify.com/top-net-software-errors/) and how to avoid them. But if your current challenges are Java-related, read on to learn about the most common issues and their workarounds.

## Compiler Errors

Compiler error messages are created when the Java software code is run through the compiler. It is important to remember that a compiler may throw many error messages for one error. So fix the first error and recompile. That could solve many problems.

### 1\. "… Expected"

This error occurs when something is missing from the code. Often this is created by a missing semicolon or closing parenthesis.

Often this error message does not pinpoint the exact location of the issue. To find it:

  * Make sure all opening parenthesis have a corresponding closing parenthesis.
  * Look in the line previous to the Java code line indicated. This Java software error doesn't get noticed by the compiler until further in the code.
  * Sometimes a character such as an opening parenthesis shouldn't be in the Java code in the first place. So the developer didn't place a closing parenthesis to balance the parentheses.

Check out an example of [how a missed parenthesis](https://stackoverflow.com/questions/19752135/java-expected-error) can create an error ([@StackOverflow](https://twitter.com/StackOverflow)).

### 2\. "Unclosed String Literal"

The "unclosed string literal" error message is created when the string literal ends without quotation marks, and the message will appear on the same [line as the error](http://www.dreamincode.net/forums/topic/116743-unclosed-string-literal-error/). ([@DreamInCode](https://twitter.com/dreamincode)) A literal is a source code of a value.

Commonly, this happens when:

  * The string literal does not end with quote marks. This is easy to correct by closing the string literal with the needed quote mark.
  * The string literal extends beyond a line. Long string literals can be broken into multiple literals and concatenated with a plus sign ("+").
  * Quote marks that are part of the string literal are not escaped with a backslash ("\").

Read a [discussion of the unclosed string literal](https://www.quora.com/What-is-an-unclosed-string-literal) Java software error message. ([@Quora](https://twitter.com/Quora))

### 3\. "Illegal Start of an Expression"

There are numerous reasons why an "illegal start of an expression" error occurs. It ends up being one of the less-helpful error messages. Some developers say it's caused by bad code.

Usually, expressions are created to produce a new value or assign a value to a variable. The compiler expects to find an expression and cannot find it because the [syntax does not match expectations](https://stackoverflow.com/questions/19581173/java-getting-illegal-start-of-expression-and-expected-errors-for-a-metho). ([@StackOverflow](https://twitter.com/StackOverflow)) It is in these statements that the error can be found.

Browse discussions of [how to troubleshoot the "illegal start of an expression"](https://stackoverflow.com/search?q=%22illegal+start+of+an+expression%22+java) error. ([@StackOverflow](https://twitter.com/StackOverflow))

### 4\. "Cannot Find Symbol"

This is a very common issue because all identifiers in Java need to be declared before they are used. When the code is being compiled, the compiler does not understand what the identifier means.

![](https://stackify.com/wp-content/uploads/2017/05/cannot-find-symbol-error-screenshot-11495.jpg)

There are many reasons you might receive the "cannot find symbol" message:

  * The spelling of the identifier when declared may not be the same as when it is used in the code.
  * The variable was never declared.
  * The variable is not being used in the same scope it was declared.
  * The class was not imported.

Read a thorough [discussion of the "cannot find symbol" error](https://stackoverflow.com/questions/25706216/what-does-a-cannot-find-symbol-compilation-error-mean) and examples of code that create this issue. ([@StackOverflow](https://twitter.com/StackOverflow))

### 5\. "Public Class XXX Should Be in File"

The "public class XXX should be in file" message occurs when the class XXX and the Java program filename [do not match](https://coderanch.com/t/628555/java/Netbeans-static-variables). The code will only be compiled when the class and Java file are the same. ([@coderanch](https://twitter.com/coderanch)):

To fix this issue:

  * Name the class and file the same.
  * Make sure the case of both names is consistent.

See an [example of the "Public class XXX should be in file"](https://stackoverflow.com/questions/13811020/java-class-is-public-should-be-declared-in-a-file-named) error. ([@StackOverflow](https://twitter.com/StackOverflow))

### 6\. "Incompatible Types"

"Incompatible types" is an error in logic that occurs when an assignment statement tries to pair a variable with an expression of types. It often comes when the code tries to place a [text string into an integer](https://stackoverflow.com/questions/18861044/what-is-wrong-with-this-incompatible-type-error) -- or vice versa. This is not a Java syntax error. ([@StackOverflow](https://twitter.com/StackOverflow))

There really isn't an easy fix when the compiler gives an "incompatible types" message:

  * There are functions that can convert types.
  * The developer may need change what the code is expected to do.

Check out an example of [how trying to assign a string to an integer created the "incompatible types."](https://stackoverflow.com/questions/7466133/java-error-incompatible-types-message) ([@StackOverflow](https://twitter.com/StackOverflow))

### 7\. "Invalid Method Declaration; Return Type Required"

This Java software error message means the return type of a method was not explicitly stated in the method signature.

There are a few ways to trigger the "invalid method declaration; return type required" error:

  * Forgetting to state the type
  * If the method does not return a value then "void" needs to be stated as the type in the method signature.
  * Constructor names do not need to state type. But if there is an error in the constructor name, then the compiler will treat the constructor as a method without a stated type.

Follow an example of [how constructor naming triggered the "invalid method declaration; return type required"](https://stackoverflow.com/questions/7451707/java-error-invalid-method-declaration-return-type-required) issue. ([@StackOverflow](https://twitter.com/StackOverflow))

### 8\. "Method <X> in Class <Y> Cannot Be Applied to Given Types"

This Java software error message is one of the more helpful error messages. It explains how the method signature is calling the wrong parameters.

The method called is expecting certain arguments defined in the method's declaration. Check the method declaration and call carefully to make sure they are compatible.

This discussion illustrates [how a Java software error message identifies the incompatibility created by arguments](https://stackoverflow.com/questions/13169606/method-in-class-cannot-be-applied-to-given-types) in the method declaration and method call. ([@StackOverflow](https://twitter.com/StackOverflow))

### 9\. "Missing Return Statement"

The "missing return statement" message occurs when a method does not have a return statement. Each method that returns a value (a non-void type) must have a statement that literally returns that value so it can be called outside the method.

There are a couple reasons why a compiler throws the "missing return statement" message:

  * A return statement was simply omitted by mistake.
  * The method did not return any value but type void was not declared in the method signature.

Check out an example of [how to fix the "missing return statement" Java software error](https://stackoverflow.com/questions/21256469/java-missing-return-statement). ([@StackOverflow](https://twitter.com/StackOverflow))

### 10\. "Possible Loss of Precision"

"Possible loss of precision" occurs when more information is assigned to a variable than it can hold. If this happens, pieces will be thrown out. If this is fine, then the code needs to explicitly declare the variable as a new type.

![](https://stackify.com/wp-content/uploads/2017/05/possible-loss-of-precision-error-11501.jpg)

A "possible loss of precision" error commonly occurs when:

  * Trying to assign a real number to a variable with an integer data type.
  * Trying to assign a double to a variable with an integer data type.

This [explanation of Primitive Data Types in](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)[ Java](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html) shows how the data is characterized. ([@Oracle](https://twitter.com/Oracle))

### 11\. "Reached End of File While Parsing"

This error message usually occurs in Java when the program is missing the closing curly brace ("}"). Sometimes it can be quickly fixed by placing it at the end of the code.

The above code results in the following error:

Coding utilities and proper code indenting can make it easier to find these unbalanced braces.

This example shows [how missing braces can create the "reached end of file while parsing"](https://stackoverflow.com/questions/4934412/java-compile-error-reached-end-of-file-while-parsing) error message. ([@StackOverflow](https://twitter.com/StackOverflow))

### 12\. "Unreachable Statement"

"Unreachable statement" occurs when a statement is written in a place that prevents it from being executed. Usually, this is after a break or return statement.

Often simply moving the return statement will fix the error. Read the discussion of [how to fix unreachable statement Java software error](https://stackoverflow.com/questions/18308159/unreachable-statement-compile-error-in-java). ([@StackOverflow](https://twitter.com/StackOverflow))

### 13\. "Variable <X> Might Not Have Been Initialized"

This occurs when a local variable declared within a method has not been initialized. It can occur when a variable without an initial value is part of an if statement.

Read this discussion of [how to avoid triggering the "variable <X> might not have been initialized"](https://www.reddit.com/r/learnprogramming/comments/1njfui/java_error_variable_x_might_not_have_been/) error. ([@reddit](https://twitter.com/reddit))

### 14\. "Operator ... Cannot be Applied to <X>"

This issue occurs when operators are used for types not in their definition.

This often happens when the Java code tries to use a type string in a calculation. To fix it, the string needs to be converted to an integer or float.

Read this example of [how non-numeric types were causing a Java software error warning](https://stackoverflow.com/questions/26890817/error-operator-cannot-be-applied) that an operator cannot be applied to a type. ([@StackOverflow](https://twitter.com/StackOverflow))

### 15\. "Inconvertible Types"

The "inconvertible types" error occurs when the Java code tries to perform an illegal conversion.

For example, booleans cannot be converted to an integer.

Read this discussion about [finding ways to convert inconvertible types](https://stackoverflow.com/questions/19138960/is-there-any-way-to-convert-these-inconvertible-types) in Java software. ([@StackOverflow](https://twitter.com/StackOverflow))

### 16\. "Missing Return Value"

You'll get the "missing return value" message when the return statement includes an incorrect type. For example, the following code:

Returns the following error:

Usually, there is a return statement that doesn't return anything.

Read this discussion about [how to avoid the "missing return value"](https://coderanch.com/t/566414/java/missing-return-error) Java software error message. ([@coderanch](https://twitter.com/coderanch))

### 17\. "Cannot Return a Value From Method Whose Result Type Is Void"

This Java error occurs when a void method tries to return any value, such as in the following example:

Often this is fixed by changing to method signature to match the type in the return statement. In this case, instances of void can be changed to int:

Read this discussion about [how to fix the "cannot return a value from method whose result type is void"](https://stackoverflow.com/questions/15518399/cannot-return-a-value-from-method-whose-result-type-is-void-error) error. ([@StackOverflow](https://twitter.com/StackOverflow))

### 18\. "Non-Static Variable ... Cannot Be Referenced From a Static Context"

This error occurs when the compiler tries to [access non-static variables from a static method](https://javarevisited.blogspot.com/2012/02/why-non-static-variable-cannot-be.html) ([@javinpaul](https://twitter.com/javinpaul)):

To fix the "non-static variable ... cannot be referenced from a static context" error, two things can be done:

  * The variable can be declared static in the signature.
  * The code can create an instance of a non-static object in the static method.

Read this tutorial that explains [what is the difference between static and non-static variables](http://www.sitesbay.com/java/java-static-and-non-static-variable). ([@sitesbay](https://twitter.com/sitesbay))

### 19\. "Non-Static Method ... Cannot Be Referenced From a Static Context"

This issue occurs when the Java code tries to call a non-static method in a non-static class. For example, the following code:

Would return this error:

To call a non-static method from a static method is to declare an instance of the class calling the non-static method.

Read this explanation of [what is the difference between non-static methods and static methods](http://beginnersbook.com/2013/05/static-vs-non-static-methods/).

### 20\. "(array) <X> Not Initialized"

You'll get the "(array) <X> not initialized" message when an array has been declared but not initialized. Arrays are fixed in length so each array [needs to be initialized](https://stackoverflow.com/questions/5387643/array-initialization-syntax-when-not-in-a-declaration) with the desired length.

The following code is acceptable:

As is:

But not:

Read this discussion of [how to initialize arrays in Java software](https://stackoverflow.com/questions/2403477/array-variable-initialization-error-in-java). ([@StackOverflow](https://twitter.com/StackOverflow))

## Next Time

Now that we've covered compiler errors, next time we'll dive into the variety of runtime exceptions that might crop up to ruin your day. Just like this segment, they will include code blocks, explanations, and pertinent links to help fix your code as fast as possible.
