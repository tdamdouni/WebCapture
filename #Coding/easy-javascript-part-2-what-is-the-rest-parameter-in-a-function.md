# Easy JavaScript Part 2: What Is the Rest Parameter in a Function?

_Captured: 2017-12-05 at 21:01 from [dzone.com](https://dzone.com/articles/easy-javascript-part-2-what-is-the-rest-parameter)_

A JavaScript function can take any number of parameters. Unlike other languages like C# and Java, you can pass any number of parameters while calling a JavaScript function. JavaScript functions allow an unknown number of function parameters. Before ECMAScript 6, JavaScript had a variable to access these unknown or variable numbers of parameters, which is an array-like object but not an array. Consider this code to understand the **arguments** variable:
    
    
        for(let i=0;i<arguments.length;i++){

As you see, that **arguments **object is used to access unknown or variable function parameters. Even though arguments uses length property and square brackets, it is not a real JavaScript array. You cannot use other JavaScript array methods like pop, push, slice etc. with the arguments object. Some of the problems in using arguments are:

  * The JavaScript function arguments object is not a real JavaScript array; therefore, you cannot use other array methods like pop, push, slice, etc. with it.
  * It is difficult to access an arguments object of an outer function in an inner function. To use it, you need to assign the arguments function of the outer function in a variable, and then use it in an inner function.
  * If you want to use the arguments object as an array, then you need to convert it manually using Aarry.prototype.slice.

[ECMAScript 6](https://www.ecma-international.org) introduces a new feature, **Rest Parameters**, which represents an unknown number of parameters as an array in a function. It not only represents extra parameters as an array, it also solves many of the problems of the arguments object. Let us rewrite the above add function using the rest parameters.
    
    
        for(let i=0;i<theArgs.length;i++){

You can define a rest parameter as **...theArgs** or **...args. **If the last-named function parameter is prefixed with **... **(three dots), it becomes the rest parameter of the function. JavaScript functions' rest parameters are pure JavaScript arrays. In the above code, **...theArgs** is the rest parameter of the function **add** because it is the only named parameter, and it is also prefixed with ... (three dots). Since the rest parameter is a JavaScript array, you can perform operations such as push, pop, etc. on rest parameter **theArgs**, as shown in the code below:
    
    
        for(let i=0;i<theArgs.length;i++){

JavaScript functions' rest parameters can work with other parameters also. You may need other named parameters in your function if you do not want to include particular parameters in a rest parameter array. Let us consider next code block:

For a first-time function call, 6 and 9 will be assigned to **num1** and **num2** respectively. For the second function call, 7 and 56 will be assigned to **num1** and **num2**. Parameters starting the third parameter will be assigned to the rest parameter array. Keep in mind that the first two parameters will not become part of the rest parameter array. So, if not all values should be included in the parameter, you should define those as a comma-separated named parameter in the beginning. The code given below will give you an error:

In the above code listing, the rest parameter is not the last parameter, so JavaScript will throw an error. The rest parameter must be the last formal parameter.

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.lessonlearnd1/0777.img2.png)

JavaScript allows you to destruct rest parameters, which means that you can unpack rest variable data into a distinct variable name. Let us consider the below code:

For a first-time function call, a=6 , b= undefined, c = undefined will be assigned, and for the second function call, a=7, b=56, c=9 will be assigned. In this case, if you pass any extra parameter then that will be ignored in the function.

JavaScript function's rest parameter is a great improvement over the arguments object to work with unknown parameters of the function. It is a pure JavaScript array; hence, you can use all array methods with it. You can unpack the rest variable data to named variables. You can give any name to the rest parameters, which is again a major improvement over always using the arguments keyword.

In the next post of this "Easy JavaScript" series, you will learn about **default parameters** in JavaScript functions. You can learn in detail about these topics at the [ECMA International site](https://www.ecma-international.org/). Also, do not forget to check out [Ignite UI](http://www.igniteui.com/), which you can use with HTML5, Angular, React, or ASP.NET MVC to create rich Internet applications.
