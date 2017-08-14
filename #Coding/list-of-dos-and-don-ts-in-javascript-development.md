# List of Dos and Don'ts in JavaScript Development

_Captured: 2017-08-02 at 21:57 from [dzone.com](https://dzone.com/articles/list-of-dos-and-donts-in-javascript-development?edition=312392&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-02)_

![http://www.nodesimplified.com/2017/07/javascript-list-of-dos-and-donts-in.html](https://dzone.com/storage/temp/6083833-the-world-through-my-eyes.png)

This post contains primary coding standards for the JavaScript programming language. JavaScript programming guidelines will help you to deliver error free code and it follows on the **Google JavaScript guideline documentation**.

**File Name:**

  * The file name must be **_all lower case_**. It may include dashes(-) or underscores(_) but no other punctuation allowed. 
  * File encoding type must be UTF-8.

**Package Name:**

  * Package names are all **_lowerCamelCase_**.
  * example: com.nodeSimplified.exampleCode.

**Class Name:**

  * Class names, interface names, typedef, and record names are all **_UpperCamelCase_**.
  * These names are always nouns or noun phrases.
  * example: ImmutableList.

**Method Name:**

  * Method names must be _**lowerCamelCase**_.
  * The private Method name must end with a trailing underscore.
  * These names are typically verbs or verb phrases.
  * example: sendMessage().

**Enum Name:**

  * Enum names should be written in **_UpperCamelCase_**.
  * These names are typically singular nouns.

**Constant Name:**

  * Constant names should be all **_Upper case_**, separated by underscores.
  * example: CONSTANT_NAME.

**Non-constant Name:**

  * Non-constant field names (static) should be written in **_lowerCamelCase_** and private variable should end with a trailing underscore.
  * Parameters are well written in **_lowerCamelCase_**. This applies to constructor parameters as well.
  * One character parameter should not be used in public methods.
  * Local variable names are written in **_lowerCamelCase_**.

**Local Variable Declaration:**

  * Declare the local variables with either let or const keyword. Use const by default if the variable doesn't need to be reassigned. 
  * The Var keyword must not be used.
  * One variable per declaration. for example: let i = 1 , j =2 is not a good practice. 

**Array Literals:**

  * Whenever there is a line break between a closing bracket and the final element, include a trailing comma.
  * Do not use the variadic constructor.
    
    
    const a3 = new Array(x1); // if x1 is undefined, then exception will be thrown.

  * Do not use non-numeric properties on an array except length. Use an Object or Map instead.

**String Literals:**

  * Ordinary string literals should be delimited with _**single quotes(').**_ single quotes(') should be preferred over double quotes(").
  * Devs should not use **line continuations(\\).**

_Illegal:_

_Legal:_

**For Loops:**

  * There are three different types of **for loop **available with ES6 Standards. The[ for...of ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)statement should be preferred whenever possible.
  * [The for...in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) statement includes a few unwanted prototypes properties so it should not be used for looping.
  * Prefer for...of and Objects.key over for...in whenever possible.

**Exception:**

  * Exceptions are an important part of the JavaScript programming language.
  * Whenever exceptional cases occur, it must be used. Code should always throw an **_Error_** or subclass of an Error, in these cases.
  * A_ new _keyword must be used while constructing an error.
  * Never throw a string or any other object as an Error in your code.

**Switch Statement:**

  * Must be enclosed in braces. Switch statements must contain **_default _**cases, even if the code is not present.
  * Switch cases will either terminate abruptly (with the break, or return statement) or will be marked with a comment that states that execution will continue in the next statement group. The "_**// Fall through**_" comment should be used to mention the idea of fall-through.

**this Keyword:**

  * **this keyword** must be used only inside class constructors and methods or in the arrow function inside class constructors and methods.

**Some General Guidelines:**

  * [With](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/with) keyword should not be used.
  * Eval function should not be used.
  * Always terminate a statement with a semicolon.
  * Mark deprecated methods, classes, and interfaces with **@deprecated **annotation.
  * Set compiler warning level to **verbose**.
  * Use of "[Strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)" is highly encouraged.

This article is originally published from [Node Simplified](http://www.nodesimplified.com). Take a look into [Top Javascript Tips and Tricks.](http://www.nodesimplified.com/2017/07/javascript-top-javascript-tips-and.html)

If you enjoyed this article, please share with your developer friends. Thanks for reading.
