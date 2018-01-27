# Performance Check on Different Type of Loops Available in Javascript

_Captured: 2017-12-27 at 13:22 from [dzone.com](https://dzone.com/articles/performance-check-on-different-type-of-for-loops-a?edition=347123&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-26)_

![Performance check](http://nodesimplified.com/wp-content/uploads/2017/12/forloop.png)

> _Performance check_

For loops plays a major role in software development, irrespective of programming language and a small mistake in the loop might collapse the entire application. So we should be really careful while handling** loops**.

In this post, we will look into different loops and the performance of each** loop** available in JavaScript. To measure the performance, we are going to use **[jsPerf](https://jsperf.com/)**.

Here's a description of jsPerf, per their website.

> jsPerf -- JavaScript performance playground!!
> 
> jsPerf aims to provide an easy way to create and share test cases, comparing the performance of different JavaScript snippets by running benchmarks.

Let's check different loops available in JavaScript and analyze the performance of each code snippet.

## for...loop

The ordinary for...loop. This loop is based on the length of the array that we will iterate through, going through each element, and access it using its index.
    
    
    for (i = 0; i < loopArrayVariable.length; i++) {

Note: If the loop is not properly implemented, we may end up accessing data that is out of the bounds of the index.

### for...each

Using for..each we can iterate through each and every element in an array. Easy to use.

### for...of

The for...of statement creates a loop iterating over iterable objects.

### for...in

The for...in statement iterates over the enumerable properties of an object.

### Performance Results

To check the performance, I have implemented 10000 iterations on above loop types.

![Javascript For loop performance](http://nodesimplified.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-14-at-10.48.02-PM-1024x708.png)

Here's how the different loops stacked up, based on Jsperf emulation performance results.

  1. for...in
  2. for...of
  3. for...each
  4. ordinary for loop 

## Conclusion

There are different types of loops available with ES6 standards. the **for...of statement** should be preferred whenever possible.

Even though the for...in statement got better performance, it includes a few unwanted prototype properties, so it should not be used for looping.

**Prefer for...of over for...in whenever possible.**

If you enjoyed this article, please share with your developer friends. Thanks for reading!
