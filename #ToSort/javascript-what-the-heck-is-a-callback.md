# JavaScript: What the heck is a Callback?

_Captured: 2017-06-12 at 19:19 from [hackernoon.com](https://hackernoon.com/javascript-what-the-heck-is-a-callback-aba4da2deced?source=userActivityShare-c79006fee040-1497291535)_

Learn and understand the basics of callbacks in just 6 minutes with easy examples.

![](https://cdn-images-1.medium.com/freeze/max/30/1*pWGJIKats-zuumA3RQNEWQ.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1000/1*pWGJIKats-zuumA3RQNEWQ.jpeg)

> _Callbacks -- image via unsplash_

### What is a Callback?

**Simply put:** _A callback is a function that is to be executed _**_after_**_ another function has finished executing -- hence the name 'call back'._

**More complexly put:** _In JavaScript, functions are objects. Because of this, functions can take functions as arguments, and can be returned by other functions. Functions that do this are called _**_higher-order functions_**_. Any function that is passed as an argument is called a _**_callback function_**_._

^ That's a lot of words. Lets look at some examples to break this down a little more.

### Why do we need Callbacks?

For one very important reason -- JavaScript is an event driven language. This means that instead of waiting for a response before moving on, JavaScript will keep executing while listening for other events. Lets look at a basic example:
    
    
    function first(){  
      console.log(1);  
    }
    
    
    function second(){  
      console.log(2);  
    }
    
    
    first();  
    second();

As you would expect, the function `first` is executed first, and the function `second` is executed second -- logging the following to the console:
    
    
    // 1  
    // 2

All good so far.

But what if function `first` contains some sort of code that can't be executed immediately? For example, an API request where we have to send the request then wait for a response? To simulate this action, were going to use `setTimeout` which is a JavaScript function that calls a function after a set amount of time. We'll delay our function for 500 milliseconds to simulate an API request. Our new code will look like this:
    
    
    function first(){  
      // Simulate a code delay  
      setTimeout( function(){  
        console.log(1);  
      }, 500 );  
    }
    
    
    function second(){  
      console.log(2);  
    }
    
    
    first();  
    second();

It's not important that you understand how `setTimeout()` works right now. All that matters is that you see we've moved our `console.log(1);` inside of our 500 millisecond delay. So what happens now when we invoke our functions?
    
    
    first();  
    second();
    
    
    // 2  
    // 1

Even though we invoked the `first()` function first, we logged out the result of that function after the `second()` function.

It's not that JavaScript didn't execute our functions in the order we wanted it to, it's instead that **JavaScript didn't wait for a response from **`**first()**`** before moving on to execute **`**second()**`**.**

So why show you this? Because you can't just call one function after another and hope they execute in the right order. Callbacks are a way to make sure certain code doesn't execute until other code has already finished execution.

### Create a Callback

Alright, enough talk, lets create a callback!

First, open up your Chrome Developer Console (_Windows: Ctrl + Shift + J_)(_Mac: Cmd + Option + J_) and type the following function declaration into your console:
    
    
    function doHomework(subject) {  
      alert(`Starting my ${subject} homework.`);  
    }

Above, we've created the function `doHomework` . Our function takes one variable, the subject that we are working on. Call your function by typing the following into your console:
    
    
    doHomework('math');
    
    
    // Alerts: Starting my math homework.

Now lets add in our callback -- as our last parameter in the `doHomework()` function we can pass in `callback`. The callback function is then defined in the second argument of our call to `doHomework()`.
    
    
    function doHomework(subject**, callback**) {  
      alert(`Starting my ${subject} homework.`);  
      **callback();**  
    }  
      
    doHomework('math'**, function() {  
      alert('Finished my homework');  
    }**);

As you'll see, if you type the above code into your console you will get two alerts back to back: Your 'starting homework' alert, followed by your 'finished homework' alert.

But callback functions don't always have to be defined in our function call. They can be defined elsewhere in our code like this:
    
    
    function doHomework(subject, callback) {  
      alert(`Starting my ${subject} homework.`);  
      callback();  
    }
    
    
    function alertFinished(){  
      alert('Finished my homework');  
    }
    
    
    **doHomework('math', alertFinished);**

This result of this example is exactly the same as the previous example, but the setup is a little different. As you can see, we've passed the `alertFinished` function definition as an argument during our `doHomework()` function call!

### A real world example

Last week I published an article on how to [Create a Twitter Bot in 38 lines of code](https://hackernoon.com/build-a-simple-twitter-bot-with-node-js-in-just-38-lines-of-code-ed92db9eb078). The only reason the code in that article works is because of [Twitters API](https://dev.twitter.com/rest/public). When you make requests to an API, you have to wait for the response before you can act on that response. This is a wonderful example of a real-world callback. Here's what the request looks like:
    
    
    T.get('search/tweets', params, function(err, data, response) {  
      if(!err){  
        // This is where the magic will happen  
      } else {  
        console.log(err);  
      }  
    })

  * `T.get` simply means we are making a get request to Twitter
  * There are three parameters in this request: `'search/tweets'`, which is the route of our request, `params` which are our search parameters, and then an anonymous function which is our callback.

A callback is important here because we need to wait for a response from the server before we can move forward in our code. We don't know if our API request is going to be successful or not so after sending our parameters to search/tweets via a get request, we wait. Once Twitter responds, our callback function is invoked. Twitter will either send an `err` (error) object or a `response` object back to us. In our callback function we can use an `if()` statement to determine if our request was successful or not, and then act upon the new data accordingly.

### You made it

Good work! You can now (ideally) understand what a callback is and how it works. This is merely the tip of the iceberg with callbacks, there is still a lot more to learn! I publish a few articles/tutorials each week, please [enter your email here](https://docs.google.com/forms/d/e/1FAIpQLSeQYYmBCBfJF9MXFmRJ7hnwyXvMwyCtHC5wxVDh5Cq--VT6Fg/viewform) if you'd like to be added to my once-weekly email list.

#### ❤ If this post was helpful, please hit the little green heart! And don't forget to check out my other recent articles:

  


Yesterday we looked at the basics of Mocha. Today, we'll be integrating Mocha into a project so you can see how it **really **works.

![](https://cdn-images-1.medium.com/freeze/max/30/1*AONMFzLg2smoc5M0uHhwmw.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*AONMFzLg2smoc5M0uHhwmw.jpeg)

> _Testing via [unsplash.com](https://unsplash.com/search/test?photo=FM9GD3aZqSU)_

### What exactly is this tutorial?

This tutorial will give you a small-scale, real-world example of how to use Mocha for testing. By the end of this tutorial you'll have successfully used Mocha to test an existing JS file. Before taking on this tutorial, you should understand what Mocha is, how to group tests, and how to use an assertion library. Please refer back to **[my first Mocha tutorial**](https://hackernoon.com/how-to-test-javascript-with-mocha-the-basics-80132324752e) if you need a refresher.

You should already have Mocha installed from the previous tutorial. If not, install Mocha globally by running: `$ npm install -g mocha`

Next, we'll create a project directory named `temperature`. In the `temperature` directory we'll create a file named `app.js` and a folder name `test`. Within the `test` folder, create a file named `test.js`. Finally, we'll initialize our project by running `npm init`. During your project initialization, the question that is most important here is '**test command:' **-- respond with **'mocha'. **This way we can run mocha by simply typing `npm test`.

When finished, you should have a file structure that looks like this:
    
    
    temperature  
    |-- app.js  
    |-- package.json  
    |-- test  
       |-- test.js

Your `package.json` file should also contain the following json:
    
    
    "scripts": {  
      "test": "mocha"  
    },

Once you have all of the above, we're ready to start!

### What are we testing?

We're going to be testing our `app.js` file in this tutorial. To speed the process along, I've already created the contents of our `app.js` for you. Go ahead and copy the code below into your `app.js`

Our `app.js` is only nine lines of code and consists of two functions:

  * `cToF()` -- is a function for converting Celsius temperatures to Fahrenheit. It takes one parameter, the temperature in Celsius, and returns the Fahrenheit equivalent.
  * `fToC()` -- is the reverse function. It converts Fahrenheit to Celsius. Its one parameter is the temperature in Fahrenheit and it returns the Celsius equivalent.
  * Both functions initially check to ensure the argument they've been passed is an integer. If it is not an integer (a string, blank, `undefined`, `NaN`, etc.) then `undefined` is returned and function short-circuits.

### Setting up our Tests

We're going to test to ensure these functions are working nicely. Here's the structure I see our `test.js` file taking:

  1. A testing group named `Temperature Conversion`
  2. Within that testing group, two additional testing groups, one named `cToF` and one named `fToC`
  3. Each testing group will have three test cases: two numbers, and a non-integer test.

First, we'll set up our two test groups using `describe()`
    
    
    var assert = require('assert');  
    describe('Temperature Conversion', function() {  
      describe('cToF', function() {  
        // tests here  
      });  
      describe('fToC', function() {  
        // tests here  
      });  
    });

Above, we have our two nested, function specific `describe` blocks within our outer `describe` block for `Temperature Conversion`. Now that we have the basic structure, we can add in our three `it()` test cases to each of our testing groups.

Our three test cases will use the built in assert assertion library. We will be testing equality, so we'll use `assert.equal(actual, expected);`

For our first test, we'll test a number that should remain unchanged. If you didn't know, both Fahrenheit and Celsius are equal at 40 degrees below zero. Lets setup this test to ensure our function handles the math correctly:
    
    
    it('should convert -40 celsius to -40 fahrenheit', function() {  
       assert.equal(-40, cToF(-40));  
    });

Perfect! We're asserting that once we run the number `-40` through our `cToF` function, the resulting value should also equal `-40`.

For our next test, we'll look at the freezing point of water. We want to ensure that 0 degrees Celsius equals 32 degrees Fahrenheit.
    
    
    it('should convert 0 celsius to 32 fahrenheit', function() {  
      assert.equal(32, cToF(0));  
    });

Everything is the same as test number one, except we're passing the number `0` into our function and expecting a result to equal `32`.

For our last test, we're going to test a blank string, and make sure the function returns undefined:
    
    
    it('should return undefined if no temperature is input', function(){  
      assert.equal(undefined, cToF(''));  
    });

For this test, we expect the result of `cToF('')` to equal `undefined`.

Awesome, all of our `cToF` tests are complete! Now we need to do the same for the `fToC` function. I wont walk you through writing these tests -- you should have that part down by now. Here's what they should look like:
    
    
    it('should convert -40 fahrenheit to -40 celsius', function() {  
      **assert.equal(-40, fToC(-40));**  
    });  
    it('should convert 32 fahrenheit to 0 celsius', function() {  
      **assert.equal(0, fToC(32));**  
    });  
    it('should return undefined if no temperature is input', function(){  
      **assert.equal(undefined, convert.fToC(''));**  
    });

Awesome, our tests are setup, now just need to run them with `npm test`
    
    
    0 passing (20ms)

Uh oh. So what happened?

### Exposing our functions

We never exposed our functions to Mocha. What this means is our `test.js` file has no way to interact with the functions in our `app.js` file. Luckily, there are a number of easy ways to do this.

  1. We're going to create an empty object named convert `let convert = {};`
  2. Instead of two different functions, we're going to make each function a method on our new `convert` object.
  3. At the end of `app.js` we're going to expose our `convert` object using `module.exports`. If you've never used it before, `module.exports` is how we tell JavaScript what object to return as the result of a `require` call. Lets look at the code to see it in action:

Now all that's left to do is require our `app.js` file in `test.js` and change the function names used in our tests to include the `convert` object. Here's the final `test.js` code:

This time when we run `npm test`, everything works as expected!
    
    
    Temperature Conversion  
      cToF  
        √ should convert -40 celsius to -40 fahrenheit  
        √ should convert 0 celsius to 32 fahrenheit  
        √ should return undefined if no temperature is input  
      fToC  
        √ should convert -40 fahrenheit to -40 celsius  
        √ should convert 32 fahrenheit to 0 celsius  
        √ should return undefined if no temperature is input
    
    
    6 passing (34ms)

Good work! You've now test Mocha in a separate file. There's still so much more left to learn -- check out the documentation, you should have all the tools you need to understand them now.

I publish a few articles/tutorials each week, please [enter your email here](https://docs.google.com/forms/d/e/1FAIpQLSeQYYmBCBfJF9MXFmRJ7hnwyXvMwyCtHC5wxVDh5Cq--VT6Fg/viewform) if you'd like to be added to my once-weekly email list.

#### ❤ If this post was helpful, please hit the little green heart! And don't forget to check out my other recent articles:
