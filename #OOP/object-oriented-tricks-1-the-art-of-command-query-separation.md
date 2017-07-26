# Object Oriented Tricks: #1 The Art of Command Query Separation

_Captured: 2017-04-26 at 09:09 from [hackernoon.com](https://hackernoon.com/oo-tricks-the-art-of-command-query-separation-9343e50a3de0)_

OOT is a mini series on writing maintainable Object Oriented code without pulling your hair out.

![](https://cdn-images-1.medium.com/freeze/max/30/1*6Da9jqVrnGsxWilCOBoejg.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*6Da9jqVrnGsxWilCOBoejg.jpeg)

Functions have _side-effects_. At times they change the state of the system when you least expect them to and wreak all kinds of havoc. It's difficult to get rid of all _side-effects_ in an Object Oriented programming paradigm. We just need to make sure to manage them so that they don't bite us when we aren't looking.

#### Managing Side Effects

One of the good ways to manage _side-effects_ is to create a strong separation between commands and queries. In this context, a **command** changes the system, it has a side effect. A **query** returns the value of a computation or the observable state of the system.

#### Example

When you call a function `getAmount()` , you expect it to just return the amount and not change state of the system. It would be horrific if it did. Similarly, when you call `setAmount()` , it will have _side-effects_ and you expect it to change the state of the system. But what do you expect `setAmount()` to return? Probably nothing.

#### Formal Definition

Command Query Separation formalises this by saying:

> Functions that change state should not return values and functions that return values should not change state.

This term was coined by Bertrand Meyer in his book _Object Oriented Software Construction_.

#### Advantages

One of the advantages of following this separation is that you can easily recognize whether or not a function has a _side-effect._
    
    
    int m();  // query  
    void n(); // command 

#### Violation

Take a look at the call below. Is it a command or a query? Clearly, it changes the state of the system.
    
    
    User u = UserService.login(username, password);

What about the user object? Why was it returned? Are you supposed to manage it? Are you supposed to call logout on it at some point in the future? Shouldn't it rather be a simple getter?
    
    
    User u = UserService.getUser();

Maybe `login()` returned the `User` so it could return `null` when it failed? We are tempted to return error codes from a command if it fails to change state. But it's better to throw an exception, maintaining the convention that commands return `void`.

#### Gotchas

Though CQS works well most of the times, there are exceptions. Popping a stack is an example of a function that modifies state and returns a result like a query.
    
    
    Element e = Stack<Element>.pop(); // stateful query

#### Summary

  * Commands return `void` and queries return values.
  * Use exceptions rather than returning and checking for error states.

As Martin Fowler said, it would be nice if the language itself would support this notion. The language could detect state changing methods, or at least allow the programmer to mark them. [Anup Cowkur](https://medium.com/@anupcowkur) has made a handy tool to help you with this. Check it out [here](https://github.com/anupcowkur/here-be-dragons).

### If you liked this post, please hit the little heart! ❤
