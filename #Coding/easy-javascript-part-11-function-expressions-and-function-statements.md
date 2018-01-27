# Easy JavaScript Part 11: Function Expressions and Function Statements

_Captured: 2017-12-05 at 20:59 from [dzone.com](https://dzone.com/articles/easy-javascript-part-11-function-expressions-and-f?edition=343095&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-05)_

In JavaScript, a function can be created in three possible ways:

  1. Function as an expression.
  2. Function as a statement.

In this post, we will learn about function expressions and the function statement.

Consider the following code:

When you create a function, as shown above, it is called a **function declaration or statement**. You can rewrite the code above to add a function in different ways, as shown below:

The function created above is called a **function expression** \- in this case, an anonymous function expression. A named function expression can be created as below:

The name of the function expression can only be used inside a function body, which is helpful in recursion. A function expression can either be:

  1. A Named function expression.
  2. An anonymous function expression.

The third method of creating a function is by using the Arrow function, which was introduced in ECMAScript 6. You can learn more about [Arrow functions here](https://infragistics.com/community/blogs/infragistics/archive/2017/08/28/easy-javascript-part-6-arrow-functions-in-javascript.aspx).

Some important points about naming functions are as follows:

  1. A function statement cannot be created without a name.
  2. A function expression **can** be created without a name, meaning you're able to create an anonymous function.

## Hoisting

A function statement is hoisted at the top of the execution context. Therefore, you can call a function that was created as a statement before it is declared. Consider the following code:

Since the foo function is created as a function statement, it is hoisted and therefore can be called before it is created.

**Function declaration or statements are hoisted at the top of the execution context, **whereas function expressions are not hoisted. Consider the following code:

Since here, the **foo **function is created as an expression, it is not hoisted at the top of the execution context. Therefore, when you try to call the function foo before it is created, you will get the error that "foo is not a function." [Learn more about function hoisting here](https://infragistics.com/community/blogs/infragistics/archive/2017/08/23/easy-javascript-part-5-simplifying-function-hoisting.aspx).

Some important points to remember about hoisting:

  1. A function statement is hoisted at the top of the execution context, so you can invoke it before it is created.
  2. A function expression is not hoisted at the top of the execution context, so you cannot invoke it before it is created.

## Immediately Invoked

A function expression can be immediately invoked (IIFE), which means a function expression can be executed as soon as it is defined. Consider the following code:

Above, we are creating a function expression and immediately invoking it, which is allowed. However, if you try to immediately invoke a function statement, you will get an error. See below:

The code above will throw an **invalid token** error. To immediately invoke a function statement, you need to wrap that inside braces, creating a different scope:

By using IIFE, we achieve data privacy. Any variable created inside IIFE whether for a function expression or statement cannot be accessed outside.

## Name Property of Function Expression

In a function expression, you assign a function expression to a variable, and that variable will have a **name** property. The variable's name property contains the name of the function. Consider this code:

In the **foo** variable we are assigning a named function expression **abc**, therefore the **name** property of the variable `foo` will contain the value of abc. For an anonymous function expression, the variable name property will be the same as the variable name:

Since we are creating an anonymous function expression, the variable name property will be the same as the variable name and you'll get **foo**.

## Calling a Function Inside a Body

To call a function inside its own body, you need to create a named function expression. Keep in mind that the name of the function expression is only available in the body of the function, and it is local to the body scope. You can write a function to find the factorial of a number using a named function expression as shown below:

If you want to avoid using a named function expression and want to call a function inside its body, then you should use **arguments.callee**. In the above, a factorial function can be rewritten as an anonymous function as shown in the listing below:

As you see, we are avoiding the named function expression and calling the function inside its body, using **arguments.callee**. [Learn more about arguments here](https://infragistics.com/community/blogs/infragistics/archive/2017/08/14/easy-javascript-part-4-what-is-the-arguments-object-in-a-function.aspx).

## Conclusion

A JavaScript function can be created in three possible ways: function statement, function expression, and arrow functions. In this post, we learned about the function statement and function expressions, but in the next post of this "Easy JavaScript" series, you will learn about another important concept of JavaScript, so stay tuned!
