# Easy JavaScript Part 3: What Is a Default Parameter in a Function?

_Captured: 2017-12-05 at 21:02 from [dzone.com](https://dzone.com/articles/easy-javascript-part-3-what-is-a-default-parameter)_

A JavaScript function can have default parameter values. Using default function parameters, you can initialize formal parameters with default values. If you do not initialize a parameter with some value, then the default value of the parameter is **_undefined_**.

Let us consider the code listed below:

While calling the function foo, you are not passing any parameter, so the default value of the variable **num1** is set to _undefined_. However, sometimes you may want to set a default value other than _undefined_. In the past, the best strategy was to test for the parameter value _undefined_ and then assign a value. So, let us say that in the above example, you want to set the default value of num1 to **9**. You can do that as shown in the code listed below:

ECMAScript 6 introduced **default parameters** for the function. Using the default parameters features of ECMA 2015, you no longer have to check for an undefined parameter value. Now, you can put **9** as the default value in the parameter itself. You can rewrite the function above to use the default value as shown below:

For the function foo, if **num1** parameter's value is not passed, then JavaScript will set** 9** as the default value of num1.

## Checking for Undefined Parameters

Even if you explicitly pass **undefined** as the parameter value when calling the function, the parameter value will be set to the default value.

In the code above, you are passing **undefined** as the value of **num1;** therefore, the value of **num1** will set to default value **9**.

## Default Value Evaluated at Run Time

The JavaScript function default value gets evaluated at runtime. To understand this better, consider the code below:

In the function foo, the default value for the parameter **value **is set to the function _koo_. When you call the function foo at runtime, the function koo will be evaluated. Upon calling the foo function, you will get an output like the one shown in the below image (in this example, we're working with the Ignite UI framework).

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.jsseries/5633.t1.png)

## Reusing Default Parameters

Default parameters are available to be used by later default parameters. Let us consider the code listed below:

In the code above, the default value of num1 is used to calculate the default value of num2. You will get the following output when calling the function **foo**:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.jsseries/5381.t2.png)

## Conclusion

The JavaScript default parameter is very useful while writing a function. When calling the function, if a parameter is missing, the default parameter feature allows you to assign a default value to the function parameter, rather than leaving it undefined.
