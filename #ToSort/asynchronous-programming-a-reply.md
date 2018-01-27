# Asynchronous Programming: A Reply

_Captured: 2017-11-23 at 14:38 from [dzone.com](https://dzone.com/articles/asynchronous-programming-a-reply?edition=337906&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-11-23)_

Recently, Jesse Warden published an [article](https://dzone.com/articles/asynchronous-programming-1?edition=334866&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-13) about Asynchronous Programming on DZone which also can be found on his [blog](http://jessewarden.com/2017/11/asynchronous-programming.html/). Actually, there are a couple of misleading statements mostly due to the incorrect modification of his examples with JavaScript Promises and _async_/_wait_ modifications.

A better example of how JavaScript behaves with Node.js is described in "**[The Node.js Event Loop, Timers, and _process.nextTick()_](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/)**." Most of this article applies to browser-hosted JavaScript as well.

Jesse's first pre-ECMAScript2015 conformant example looks like this:
    
    
    slow(()=> console.log('3'));

If you are familiar with JavaScript, you will not be surprised about the output of this code snippet being the numbers 1 through 4 written in the sequence 1, 4, 2, 3: the timeout event is only handled after all the synchronous code has terminated execution.

Later in his article, Jesse removes the call to _setTimeout()_, and his code now looks like this:
    
    
    slow(() => console.log('3'));

In this case, we get the sequence 1, 2, 3, 4. Jesse states: _"Depending on 'how fast' your code runs, especially when unit testing with [mocks](http://sinonjs.org/), you now have a race condition."_ This is wrong. This code is completely synchronous and behaves as it should - namely by sequentially executing its statements. The call to _slow()_ is executed immediately which means the two statements inside the lambda block are executed before the call to _fast()_. There is **no** race condition at all. Maybe his mocks introduced asynchronicity, which led him to his conclusion.

Here is Jesse's version of the example which uses promises:
    
    
    fast = () => console.log('1');
    
    
    slow = () => new Promise(success => {
    
    
    slow().then(()=> console.log('3'));

Actually, what this code does is likely **not** to be what Jesse wants it to, namely, bringing code execution in an order which produces the output 1, 2, 3, 4. What it does not do is to serialize the output. Indeed, outputting 3 does not happen before the timeout event has occurred and was handled. This is the behavior which is implemented with this promise. However, the call to _slow()_ only creates the promise and initiates the action by calling the _timeout()_ function without waiting for the timeout event to occur. So the next action is the call to _then()_ which places another callback onto the stack of actions to be executed after the timeout event has been handled successfully. Both the event handling _and_ the action stack are executed _only after_ all the synchronous code has finished executing - and perhaps some other stuff like the keyboard or another I/O was processed. Therefore, the output of the sequence 1, 4, 2, 3 is exactly what one should expect. So Jesse ends up with possible race conditions due to his inappropriate usage of promises.

As you may have noticed, this version does not take any parameters, so there is no way to pass a callback to it which will be executed when the timeout event occurs.

An - almost - correct implementation would look like this:
    
    
      return new Promise((resolve, reject) => {
    
    
      slow(() => console.log('3')).then(() => console.log('4'));

This indeed delivers the desired sequence of 1, 2, 3, 4.

Here is the same code when using _async_/_wait_:

I call this code almost correct, however, since it does not allow you to pass any parameters to the callback or to handle possible return values of it. Here's a much better version then is this one which also adds exception handling:

As you can see, the return value of the first callback reappears as input to the second callback passed to the first call of the _then() _method, in case you prefer working with promises. Otherwise, this value is returned by the call to _await slow()_, which makes it look much like a synchronous call. Furthermore, you can separate general (reusable) exception handling (which is implemented here during the creation of the promise, that is as part of _slow() _itself) from the exception handling specific to the particular use case when _slow()_ is called. This nicely illustrates the principle that you should not try to handle exceptions completely in a function when you don't have enough information to do it in a meaningful way. Just add a little bit of contextual information if this makes sense, and rethrow. Somewhere further up in the call stack, exceptions can be handled as required by the needs of the business.

With _await_, exception handling looks quite natural and similar to that in synchronous code, and debugging code is much easier in this case since you do not need to step through a bunch of callbacks like you need to when you use promises directly. This is why I prefer working with _await_.

As a summary, I'd like to state that when using promises correctly, you can avoid race conditions altogether.
