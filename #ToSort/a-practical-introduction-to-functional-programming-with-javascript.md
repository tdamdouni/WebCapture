# A Practical Introduction to Functional Programming With JavaScript

_Captured: 2017-04-23 at 21:58 from [dzone.com](https://dzone.com/articles/a-practical-introduction-into-functional-programmi?edition=292909&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-23)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Many articles talk about advanced functional programming topics, but I want to show you simple and useful code that you can use in day-to-day developer tasks. I've chosen JavaScript because you can run it almost everywhere and it's well suited for functional programming. Two of the reasons why it's so great are that functions are first class citizens and you can create higher-order functions with it.

**Higher order functions** are functions that can take a function as an argument or return a function as a result. Such as the createAdd function below:

Note how you can store a function in a variable and call it later. Functions in variables are treated just like any other variable.

But why is it great that you can return a function as a result? Because you are able to return behavior, not just values, and because of this the abstraction will be higher and the code will be more readable and elegant.

Let's take an example. You want to print the double of every number in an array (something that every one of us does once in a while), so you would probably do something like this:
    
    
    for (x = 0; x < nums.length; x++) {

You can see a common pattern here, the looping through an array is a behavior that you can extract into a function so you don't have to write it again.

How do you do it?
    
    
        for (x = 0; x < array.length; x++) {

The forEach function gets an array of numbers and a function printDouble and calls printDouble on every element of the array. Actually, this is a very useful function and its implemented in the [prototype of the array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach). So you don't have to write the previous code in every codebase that you work on.

(forEach is a higher-order function too because it takes a function as a parameter.)

_**Welcome to a life without having to write loops again to do something with an array.**_

You can also write the above code this way:

JavaScript has abstractions for similar common patterns such as **reduce**, which can be used to produce a single output from an array.

What it does is:

**Map** is similar to forEach, but the function you give it modifies the value of the current element:

**Filter **is used for removing the elements that do not match a given set criteria:

You can also use the filter with the [fat arrow](http://www-db.deis.unibo.it/courses/TW/DOCS/JS/developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions.html) operator:

Below is a similarly common example for a web application:

_Don't repeat yourself - as every good programmer knows._

In this scenario, we can see a pattern, but it cannot be abstracted with OOP structures, so let's do our functional magic.

In the end, we have the same functions in a more elegant way.

_I think_ in the future functional programming will creep into our everyday life and will be used beside OOP so we can have a more abstract and readable codebase.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
