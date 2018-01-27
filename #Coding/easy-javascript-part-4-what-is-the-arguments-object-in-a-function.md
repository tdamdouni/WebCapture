# Easy JavaScript Part 4: What Is the Arguments Object in a Function?

_Captured: 2017-12-05 at 21:03 from [dzone.com](https://dzone.com/articles/easy-javascript-part-4-what-is-the-arguments-objec)_

A JavaScript function has array-like objects called **arguments** which correspond to the arguments passed to the function. All arguments passed to a JavaScript function can be referred using the arguments object.

Now as we get started, let's consider the code listed here:

In the above function, num1 and num2 are two arguments. You can refer to these arguments using the arguments named num1 and num2. Besides the arguments name, you can also refer to them using a JavaScript array like the object **arguments**. So, the above function can be rewritten as shown in the listing below:
    
    
        var res = arguments[0] + arguments[1];

In JavaScript functions, the arguments object is used to access or refer to all arguments passed to the function. The arguments object is a local variable available to the function. The length of the arguments object is equal to the number of arguments passed to the function. Let us consider the code below, where you'll get 2 as an output because two arguments have been passed to the function:

## An Arguments Object Is Not a Pure Array

The JavaScript arguments object is not a pure JavaScript array. You cannot perform operations such as push, pop, slice, etc. with the arguments object. As you'll see in the code listed below, doing so will throw an exception because **arguments.push** is not a function.

## An Arguments Object Can Be Set

You can set a particular item in an arguments object array. To begin, you can set the first item of the array using the index 0 as shown in the listing below:

In the add function, **num1** and **arguments[0]** refer to same value. So, when you update the arguments[0], the value of num1 also get updated. For the above code, the output would be 23.

## Convert Arguments Object to an Array

As we've covered already in this post, a JavaScript function arguments object is not a pure array. Other than the **length** property, it does not have any other property. However, you can convert an arguments object to an array using **Array.prototype.slice.call** as shown in the listing below:

In ECMAScript 6, you can convert the arguments object to an array as shown in the listing below:

## Conclusion

To recap, here are a few important things to remember about the arguments object:

  * The length of the arguments object is equal to the number of arguments (parameters) passed to the function.
  * An arguments object is an array-like object but not a JavaScript array.
  * You cannot use other JavaScript array methods such as push, pop, slice, etc. with the arguments object.
  * The JavaScript arguments object index starts with zero. So the first parameter will be referred by arguments[0], the second parameter will be referred by arguments[1], and so on.

Simply put, a JavaScript arguments object is an array-like object which refers parameters passed to the function. In ECMAScript 6, [rest parameters](https://www.infragistics.com:443/community/blogs/infragistics/archive/2017/07/25/easy-javascript-part-2-what-is-rest-parameter-in-a-function.aspx) were introduced and are now widely used instead of the arguments object in functions for variable numbers or arguments.

In the next post of this "Easy JavaScript" series, you will learn about the **class** in JavaScript functions.
