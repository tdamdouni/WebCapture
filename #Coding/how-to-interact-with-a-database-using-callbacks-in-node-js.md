# How to Interact With a Database Using Callbacks in Node.js

_Captured: 2017-07-26 at 23:01 from [dzone.com](https://dzone.com/articles/how-to-interact-with-a-database-using-callbacks-in?oid=twitter&utm_content=buffer63329&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn how to [move from MongoDB to Couchbase Server](https://dzone.com/go?i=206124&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454368%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283402) for consistent high performance in distributed environments at any scale.

Be sure to check out [Part 1](https://dzone.com/articles/how-to-get-use-and-close-a-db-connection-using-var) first if you haven't already!

Callback functions have been around since the early days of JavaScript, but there have never been any standards for using them. How should callbacks be passed into async APIs? How should errors that occur during async processing be handled? A lack of standards led to variations in API implementations.

The developers of Node.js decided that some basic rules for callbacks would be good for consistency. Today, Node.js style callbacks are the canonical pattern used for async APIs (though some `EventEmitter`-based APIs exist, as well). Because the pattern is so simple, it's very easy to learn and put to use. But as you'll see, the pattern alone isn't perfect for every situation.

## Callback Pattern Overview

The callback pattern in Node.js follows two basic rules:

  1. When an asynchronous API is invoked, the callback function will be the last parameter passed in.
  2. When the callback function is invoked, the first parameter is reserved for an error that may have occurred. The value will be `null` (falsy) if no error occurred and an instance of `Error` (truthy) if an error did occur.

Here's a fictitious example that demonstrates the callback pattern:

This is what's happening in the script above:

  * **Line 1**: A fake async API is required in. This API is a function that implements the Node.js callback pattern.
  * **Lines 3-10**: A function named `myCallback` is declared. The first formal parameter is reserved for errors that may occur when the async work is running (Rule #2 above). The return statement on Line 6 is used to exit the function after the error is handled.
  * **Line 12**: The `asyncFunc` function is invoked. The last parameter passed in is a reference to the callback function (Rule #1 above). When the async work is done, the callback will be added to the callback queue and eventually executed on the main thread.

**Remember**: If an error has occurred, it's important to exit the function after handling the error. With this pattern, that responsibility falls on you.

As you can see, this is a pretty simple pattern and it works great for simple, sequential async flows. But in addition to forgetting to exit after error handling logic, there are a couple of other issues that might trip up newcomers to Node.js.

## Callback Hell

Callback hell (AKA the pyramid of doom) is something of a right of passage with Node.js. You start by writing one async call using an anonymous callback. Then you embed another async call, and then another, and you continue doing this until even you can't make sense of the code anymore.

The following script, which writes a file, is a not-so-bad example of callback hell:
    
    
    fs.open('test.txt', 'a+', function(err, fd) {
    
    
        fs.write(fd, 'test line', function(err, written, string) {
    
    
            fs.close(fd, function (err) {

Do you see how each async call is indented to help keep the code readable? To some, the whitespace that builds up to the innermost async call looks like a horizontal pyramid (I used four spaces for indentation over two to make this effect more obvious). Welcome to the pyramid of doom!

Thankfully, the solution to this problem is simple: Use named functions over anonymous functions! Here's the same basic logic, rewritten using named functions.
    
    
        fs.open('test.txt', 'a+', function(err, fd) {
    
    
        fs.write(fd, 'test line', function(err, written, string) {

OK, so there are more lines of code in this version. But in the real world, using named functions leads to code that's more readable, maintainable, composable, etc. Plus, you can limit the level of indentation, thus avoiding callback hell!

However, there are still situations where the callback pattern alone isn't enough.

## Callback Pattern Limitations

While the callback pattern is easy to use, there are lots of asynchronous workflows that it doesn't help with out-of-the-box. Here are some examples:

  * You need to run multiple asynchronous functions concurrently, then run a different function when the concurrent functions have finished.
  * You need a queue that can run n number of functions concurrently.
  * You have an array of "things" that needed to be processed asynchronously (either serially or in parallel), then run another function after all elements in the array have been processed.

Although the sample application in this series doesn't do anything this complex, these types of flows are quite common. All of the tools that you need to write such flows using just callbacks are available to you in JavaScript, but writing the algorithms may not be so easy and the resulting code may not be easy to maintain -- especially for folks that are new to Node.js.

You might start writing a library to abstract away some of the complexity involved with such async flows. If you spend a lot of time building out such a library, you'd eventually have something that looks a lot like [Async](http://caolan.github.io/async/#), one of the most popular libraries in the history of Node.js. I'll cover Async in the next post in this series. For now, let's stick to the callback pattern and see how it can be used to code the demo application.

## Callback Demo App

The callback demo app is comprised of the following four files. The files are also available via [this Gist](https://gist.github.com/dmcghan/9f09d931637df16baa634eebef55feed).

`package.json`:

This is a very basic `package.json` file. The only external dependency is `oracledb`.

`index.js`:
    
    
      employees.getEmployee(101, function(err, emp) {

In this version of the `index.js`, the Node.js callback pattern is used to first create a connection pool and then to fetch an employee. Although the pool is passed to the callback function for `createPool`, it's not referenced here as the [built-in pool cache](https://github.com/oracle/node-oracledb/blob/master/doc/api.md#-831-connection-pool-cache) will be used in `employees.js`.

The `db-config.js` file is used in `index.js` to provide the connection info for the database. This configuration should work with the [DB App Dev VM](https://dzone.com/articles/creating-a-sandbox-for-learning-nodejs-and-oracle), but it will need to be adjusted for other environments.

This version of the `employees.js` file uses the Node.js callback pattern to get a connection, to execute a query, and then tp close the connection. Notice that the logic to close the connection, the "`finally`" in the `try…catch…finally` block, appears twice -- once if an error occurs during the call to `connection.execute` and again if everything completes without error. The code could be refactored so that the "`close`" logic is only defined once, but it would still need to be called from these two locations.

The Node.js callback pattern is important to understand when working with Node.js. It's simple but effective. Hopefully, you now have a better understanding of how it works. Check out the next part of the series to see how to use the Async module to do the same work.

Want to deliver a whole new level of customer experience? Learn how to make [your move from MongoDB to Couchbase Server](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)[.](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)

### Like This Article? Read More From DZone
