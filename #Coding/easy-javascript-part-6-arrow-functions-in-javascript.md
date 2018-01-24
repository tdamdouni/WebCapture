# Easy JavaScript Part 6 : Arrow functions in JavaScript

_Captured: 2017-12-05 at 21:05 from [dzone.com](https://dzone.com/articles/easy-javascript-part-6-arrow-functions-in-javascri)_

The JavaScript arrow function is a shorter way of writing a function expression that was introduced in ECMAScript 6. Usually, in JavaScript, you can create a function in two ways:

  1. Function as a statement.
  2. Function as an expression.

A **function statement** can be created as shown below:

The same function can be created as a **function expression** as shown below:

ECMA 2015 (or ECMA Script 6) introduced a shorter syntax to write a function expression called the **arrow function**. Using the arrow function, you can write the function expression above as seen here:
    
    
    var add = (num1, num2) => { return num1 + num2; };

As you can see, writing a function expression using the arrow function is shorter.

## Basic Syntax Rules for Arrow Functions

First, parameters should be passed in the small parentheses. You can create an arrow function with two parameters as shown below:
    
    
    var add = (num1, num2) => { return num1 + num2; };

If there is only one parameter to be passed, then the parentheses are optional and you can choose to omit them. You can create an arrow function with one parameter as seen below:

If there are no parameters, then you must have an empty parenthesis - it can't be written without them. So you can write a function without a parameter using the arrow function as seen here:

If there is a single expression or statement in the function:

  1. Using parenthesis in the body is optional.
  2. Using a return statement is optional.

You can rewrite the add function as seen below without using parenthesis in the function body and the return statement:

You can also write a function without a parameter with a console statement as seen below:

## Returning Object Literals

The JavaScript arrow function can return an object literal as well. The only requirement is that you need to enclose a return object in small brackets, as shown below:

As you can see, the object to be returned is enclosed in small brackets; if you don't do this, JavaScript won't be able to differentiate between the object literal and the function body.

## Arrow Function Supports Rest Parameters

The JavaScript arrow function supports another ES6 feature: rest parameters. You can use the rest parameter with the arrow function as shown in the code listing below:

In the example seen here, when you use the rest parameter with the arrow function, you'll get an output of 2 and 75 because the number of extra parameters passed is 2 and the summation of num1 and num2 is 75.

## The Arrow Function Supports the Default Parameter

Additionally, the JavaScript arrow function supports another ES6 feature: default parameters. [We covered default parameters in detail here](https://www.infragistics.com:443/community/blogs/infragistics/archive/2017/08/04/easy-javascript-part-3-what-is-a-default-parameter-in-a-function.aspx). You can use a default parameter with the arrow function as shown in the listing below:

In the listing above, we are using default parameters with the arrow function. We are not passing any value while calling the function, and due to the default parameters, the output would be 17.

## How Does "this" Work in an Arrow Function?

The arrow function does not have its own **this** value. The value of **this** inside an arrow function is always inherited from the enclosing scope. In JavaScript, each function has its own **this** value, and that depends on how the function is being called. Let us consider the code listed below:

Here, **cat** is an object literal that consists of:

  1. The Property name.

In the `canRun` method, we created an arrow function **foo**, giving the value of **this**. Since the arrow function does not have its own value for **this**, it will take the value from the surrounding function and you'll get:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.javascript5/1423.arrowimg1.png)

As you can see, the **this** value is the same in the `canRun` method and the arrow function foo. The arrow function gets the value of **this** from the inherited scope. If you're unclear on this, keep the following two rules in mind:

  1. Use object.method to get a meaningful object as the value of **this** in the method.
  2. For any other requirement, use the arrow function so the function won't have its own value of **this** and it will inherit the value of **this** from the enclosing scope.

## Restrictions With the Arrow Function

There are a few restrictions that apply to arrow functions to be aware of:

  1. The arrow function does not have an arguments object.
  2. The arrow function cannot be used with the new operator so it can't work as a constructor.
  3. The arrow function does not have the **prototype** property.

If you try to use the arrow function as a constructor, you will get an exception. Consider the code listed below:

Here, you're trying to create object f1 by using the arrow function **foo** as a constructor, and JavaScript will throw you the following exception:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.javascript5/2148.arrowimg2.png)

And when you try to print the prototype value of the arrow function, you will get **undefined** as your output:

This happens because the arrow function does not have a prototype property. Just remember: while the arrow function gives you shorter ways of writing function expressions, it does not have its own **this** value and cannot be used as a constructor.
