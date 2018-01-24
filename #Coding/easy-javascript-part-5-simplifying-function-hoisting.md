# Easy JavaScript Part 5: Simplifying Function Hoisting

_Captured: 2017-12-05 at 21:04 from [dzone.com](https://dzone.com/articles/easy-javascript-part-5-simplifying-function-hoisti)_

To understand function hoisting, let us start by considering the code listed below:

What should the output be?

In any other programming language, the output here would be a **reference error**. However, in JavaScript, you will get **undefined** as the output. Why? Because JavaScript hoists variables at the top of the execution context. An execution context could be the function in which a variable is declared or a JavaScript file in which a variable is declared. So, let us rewrite the above code snippet using a function:

Here, the variable "foo" is hoisted at the top of the function **abc**'s execution context; which means you can access foo before it is declared. To put it simply, whenever you declare a variable, the JavaScript interpreter breaks it into two statements:

  1. Declaration of a variable.
  2. Assignment.

The declaration of a variable goes at the top of the execution context, and assignment happens where the variable is created. So the above code snippet is broken into two statements as shown in the image below:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.javascript5/5710.js51.png)

The variable foo is hoisted at the top of the execution context of the function **abc**, hence when you use it before its declaration, you get "undefined" as the output.

**Keep in mind that a variable declared using the [let statement](https://dzone.com/articles/easy-javascript-part-1-learn-the-quotletquot-state) does not get hoisted to the top of the execution context. **

Now that you understand how variables are hoisted in JavaScript, let's explore function hoisting in JavaScript. In JavaScript, a function can be created in two ways:

  1. Function as a declaration.
  2. Function as an expression.

**A function created as a declaration or statement is hoisted as a whole to the top of the execution context. However, a function created as an expression is hoisted like a variable. **

To illustrate this, let's create a function as a statement:

Above, if you use a function before it's created, you will get an output of **hello**. This is happening because a function created as a statement gets hoisted as a whole to the top of the execution context.

Whenever you create a function as a statement, you can use that function before the function is created. So if you are creating a function as a statement in line number 5, you can use that function in lines 1-4 because function statements are hoisted with the function body at the top of the execution context.

**Function statements are hoisted with the function body at the top of the execution context**.

Function expressions get hoisted to the top of the execution context like a variable. Let us consider the code listed below:

Here you are creating the function **foo** as an expression, so JavaScript will hoist it in the same way a normal variable is hoisted. JavaScript treats the above code as shown in the image below:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.javascript5/2465.js52.png)

As you see in the above image, foo is getting declared as a variable at the top of the execution context, however, the assignment of a function in the variable foo is happening in line number 6 where the function as an expression was created. So, when you try to execute the code listed above, you will get the error **undefined is not a function** as shown in the image below:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.javascript5/7848.js53.png)

You cannot use the function expression before it is created because only the function declaration gets hoisted at the top.

In summary:

  1. The function statement gets hoisted with the function body at the top of the execution context. You can use a function created as a statement before it's created.
  2. The function expression cannot be used before it's created. Only the declaration part gets hoisted and the assignment happens in the line where the function was created.

In the next post of this "Easy JavaScript" series, you will learn about more important concepts in JavaScript, so stay tuned.
