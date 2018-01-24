# Easy JavaScript, Part 1: Learn the 'let' Statement

_Captured: 2017-12-05 at 21:01 from [dzone.com](https://dzone.com/articles/easy-javascript-part-1-learn-the-quotletquot-state)_

Using the `let` statement, you can create Block-scoped local variables in JavaScript. The `let` statement was introduced in the [ECMAScript 6 standard of JavaScript](https://www.ecma-international.org/ecma-262/6.0/).

Before you go ahead and learn about `let`, I recommend you to check out Infragistics jQuery-based library [Ignite UI](https://www.infragistics.com:443/products/ignite-ui), which helps you write and run web applications faster. You can use the Ignite UI for JavaScript library to help quickly solve complex LOB requirements in HTML5, jQuery, Angular, React, or ASP.NET MVC. ([You can download a free trial of Ignite UI here](https://www.infragistics.com:443/free-downloads/ignite-ui).)

Before ECMAScript 6, JavaScript had three types of scoping:

  1. Global scoping
  2. Functional scoping
  3. Lexical scoping

To explore **let** statement in detail, consider the code snippet given below:
    
    
            console.log("Value of x in if statement = " + x);
    
    
        console.log("Value of x outside if statement = " + x);

You will get this output for the above code listing:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.lessonlearnd1/1222.imglet1.png)

In the above listing, variable `x` is declared using the `var` statement. Hence, the scope of variable `x` is a function scope. Variable `x` inside the `if` statemnet is same variable `x` which was created _outside_ the `if` statement. So, when you modify the value of variable `x` inside the`if` statement block, it modifies the value for all references of variable `x` in the function.

To avoid this, you need block-level scoping, and the `let` statement allows you to create a block-scoped local variable.

Let's modify the above code snippet and use the `let` statement to declare the variable:
    
    
            console.log("Value of x in if statement = " + x);
    
    
        console.log("Value of x outside if statement = " + x);

In the above code snippet, you are declaring scope level local variable x using the `let` statement. Therefore updating value of variable x inside the `if` statement will not affect value of variable x outside the `if` statement.

This is the output you'll get for the above code:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.lessonlearnd1/7801.imglet2.png)

Unlike variables declared with **var** that are function-scoped (or global-scoped), variables declared with **let** are block-scoped: they only exist in the block they are defined in.

## Variable Hoisting With let

Hoisting of variables declared with `let` works differently than variables declared with `var`. Therefore, there is no variable hoisting for variables declared with let, which means variables declared with `let` do not move to the top of the execution context.

To understand this better, let's consider this code:

As output, you will get a `ReferenceError` for variable `y`, which is declared using the `let` statement. So, a variable declared using `let` does not hoist on top of the execution context.

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.lessonlearnd1/7608.imglet3.png)

## Redeclaring Variables With let

You cannot redeclare a variable with let in the same function or block. Trying to do so will give you a syntax error. Consider this code listing:

Running the above code will give you a syntax error as shown here:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.lessonlearnd1/4024.imglet4.png)

## Temporal Dead Zone With let

Sometimes a variable declared with let causes a temporal dead zone. In the next code listing, `let x=x+67` will throw the exception that x is not defined.

You will get this error because the expression (x+67) is evaluating to an `if` block-scoped local variable `x`, instead of a function-scoped local variable x. On running the above code, you will get this exception:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.lessonlearnd1/3817.imglet5.png)

You can fix the above error by moving the declaring variable one line above the expression, as shown here:

Block-level scoping is one of the most important features of any programming language, and with the introduction of the `let` statement in ECMAScript 6, now JavaScript has it. Using the `let` statement, you can create a variable, which has a lifetime scoped to a block. This solves many problems, such as accidental modification of global-level scoped variables, local variables in a closure, and helps in writing cleaner code.

[In the next post of this "Easy JavaScript" series](https://www.infragistics.com:443/community/blogs/infragistics/archive/2017/07/21/easy-javascript-part-2-what-is-rest-parameter-in-a-function.aspx), you will learn about rest parameters in JavaScript functions. You can learn in detail about these topics at the [ECMA International site](https://www.ecma-international.org). Also, do not forget to check out [Ignite UI](http://www.igniteui.com/), which you can use with HTML5, Angular, React, or ASP.NET MVC to create rich Internet applications.
