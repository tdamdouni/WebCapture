# Write Cleaner Code Using Promises

_Captured: 2018-06-06 at 21:31 from [dzone.com](https://dzone.com/articles/node-promises-101?edition=380208&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-06)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Asking "around the web," I found out that one of the main problems new-comers have when starting to work with Node.js is "Promises." They find them hard to understand, difficult to know how to deal with them and when to use them correctly.

In this video, I gave a basic explanation of how they work and how you can create them:

Now, in this article, I want to go a bit deeper, looking at some other examples and discussing things like dealing with multiple parallel promises at once.

## Declarative Programming

One of the nice things promises enable you to do is to clean up your code (that's one of the **only **things they allow you to do basically). But the way they do that is by providing you with the syntactic sugar required to _declare _what you're doing instead of actually taking care of the control flow of your logic.

They do that in a very basic way, mind you, it's not like we're dealing with functional or reactive programming explicitly (although we very well could be), but it's a step in that direction. Why? Because you're structuring your code and logic in a step-by-step way, especially when you're dealing with several levels of complexity.

Let me show you:
    
    
    authenticateUser(usrname, pwd, (err, isAuth) => {
    
    
            loadUserDetails(usrname, (err, details) => {
    
    
                let user = new User(usrname, token, details);
    
    
                performAction(user, (err, result) => { //this is what you wanted to do all along

The above is a classic example of nested callbacks, where you have several pieces of information that need to be taken from different services (or in different steps, due to some other logic), by default, callbacks only let you deal with asynchronous behavior serially, which, in this case, is not ideal. Both `getSessionToken` and `loadUserDetails` could be done in parallel since they don't require the results of each other to perform their operations. But doing so requires you to either add extra code to handle the parallelism support or add a third-party library.

Furthermore, the entire structure is very imperative in the sense it's explicitly stating how to deal with errors and how to deal with serial calls. You (the developer working on this) need to think about these steps while writing them to ensure the correct behavior.

Let me show you how a promise-based approach would look:

I'm sure we can all agree that is a lot simpler to write and to read. Let me show you a mocked implementation of these functions since promises need to be returned in all of them:
    
    
        return new Promise( (resolve, reject) => {
    
    
        return new Promise( (resolve, reject) => {
    
    
        return new Promise( (resolve, reject) => {

The functions have been simplified for testing purposes, but you're more than welcome to mess around with them to get different results. You can even try to reject some of those promises to see when the flow would be interrupted.

To explain a bit further:

  * `preActions` calls both functions in parallel, using the `all`method for the native `Promise` object. If any of them were to fail (thus rejecting their respective promise), then the entire set would fail and the `catch` method would've been called.
  * The others are simply returning the promises, as explained in the video above.

The other way that the `Promise` object allows you to deal with multiple promises, is by using the `race` method, which, instead of trying to resolve all promises, actually just waits for the first one to finish, and either fails or succeeds based on whether the promise was resolved or rejected.

## When Would You Use Race?

It might not be very obvious when this method would come in handy, since when you have several asynchronous calls, you probably want the result of all of them. But there are some cases where it comes in handy.

If, for instance, performance was an important part of your platform, you might want to have several copies of the data source and you could to query them all hoping to get the fastest one, depending on network traffic or other external factors.

You could do it without promises, but again, there would be an added expense to this approach, since you would have to deal with the logic to understand who returned first and what to do with the other pending requests.

With promises and the `race` method, you can simply focus on getting the data from all your sources and let JavaScript deal with the rest.

Another example where you might want to consider using this method is when trying to decide whether or not to display a loading indicator in your UI. A good rule of thumb when creating SPAs is that your asynchronous calls should trigger a loading indicator for the user, to let him/her know something is happening. But this rule is not ideal when the underlying request happens very quickly, because all you'll probably get in your UI is a flicker of a message, something that goes by too fast. And loading times might depend on too many things for you to create a rule to know when to show the indicator, and when to simply do the request without it.

You can play around with the concepts of rejection and resolution to have something like this:
    
    
      return new Promise((resolve, reject) => {
    
    
      return yourAsynchronousRequest(params).then( data => console.log("data fetched:", data));
    
    
      return new Promise((resolve, reject) => {
    
    
    Promise.race([showDataToUser(), timeout()]).catch(showLoadingIndicator);

Now the race is against an actual asynchronous request and simply a timeout set as a limiter. Now the logic to decide whether to show or not the loading indicator is hidden behind the `race` method.

That's it for now, let me know what your thoughts are regarding promises and the benefits they bring to the table. Also, if you want more content like this or are looking for Node.js related books, please visit my site at [www.fernandodoglio.com](http://www.fernandodoglio.com)

Thanks for reading!

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
