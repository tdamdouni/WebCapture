# JavaScript — Make your Code Cleaner with Decorators

_Captured: 2017-04-24 at 18:44 from [medium.com](https://medium.com/@sonam_86445/javascript-make-your-code-cleaner-with-decorators-b9090d1c36d8?ref=quuu)_

When working with JavaScript, you sometimes need to use the `setTimeout `function to force some piece of code to run at the next **tick**.

The `setTimeout` "hack":
    
    
    setTimeout(() => {
    
    
    ...Code...  
     This Code will run at the next tick.
    
    
    }, 0);

I hate to write code like this, especially when the `setTimeout` is not something that comes from my need. I want this to be cleaner. So what if we could abstract the `setTimeout` function to a decorator.

Let's create a method decorator named `timeout` to clean our code.

In `[typescript](https://www.typescriptlang.org/docs/handbook/decorators.html), `a method decorator is just a function that takes three parameters.

#### The target:

Either the constructor function of the class for a static member, or the prototype of the class for an instance member.

#### The key:

The name of the member.

#### The descriptor:

The Property Descriptor for the member.

In our case, we also need to pass an argument to our decorator ( the number of milliseconds, that by default will be zero), so we need to use a Decorator Factory:

> A Decorator Factory is simply a function that returns the expression that will be called by the decorator at runtime.

Next, we can get a reference to the original method from the descriptor value property.  
Then we are overriding the original value and creating a new function that wraps the original with `setTimeout`.

Now we can use our decorator like this:

#### Conclusion:

You can leverage decorators in your apps and create powerful things with them. Decorators are not only for frameworks or libraries, so be creative and start using them.
