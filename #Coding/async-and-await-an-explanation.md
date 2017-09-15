# Async and Await: An Explanation

_Captured: 2017-08-24 at 16:50 from [dzone.com](https://dzone.com/articles/async-and-await-an-explanation?oid=twitter&utm_content=buffer6a186&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

For a while now, the Async and Await commands in C# have confused me.

Like most things, the best way to learn about something is to use it in a real-world example. I am currently adding an email alert feature to a website. This is an ideal example of something that would benefit from Asynchronous programming. There is no need for the webpage to wait to send thousands of emails; let's just send a call to get started and allow the browser to carry on as normal.

This is my first try at using async and await, so feel free to suggest best practices in the comments.

Let's start with a `Send` method in my `EmailController`.
    
    
        Task<string> t = SendNotifications(id,userID);

This simply checks to see if you have permission to the page. If not redirects to the login page otherwise it makes a method call and redirects back to the page it came from.

Let's have a look at that method call in more detail.

`SendNotification` doesn't return a normal string it returns a `Task<string>`, so let's look at how we are creating this.

The return type is set to `Task` but it has the aysnc keyword appended to it. It also makes a call with the await keyword.

So that is it. My first bit of code that uses Async and Await. My controller calls a method asynchronously which then calls another method asynchronously which sends emails asynchronously.

  * **Async**: This enables the Await keyword to be used in the method.

  * **Await**: This is where things get asynchronous. The await keyword allows the code to wait asynchronously for the long running code to complete.
