# The push-pin principle

_Captured: 2016-03-10 at 17:53 from [ericasadun.com](http://ericasadun.com/2016/03/10/the-push-pin-principle/)_

I've written before on my desire to reconstitute a weak reference in completion handlers, something along the lines of :
    
    
    guard bind self else { return }

John Estropia writes,

> About the weak-strong dance, it's currently perfectly fine to do
> 
> `guard let `self` = self else {return}  
self.doSomething`
> 
> We actually made this a rule in our team.

I feel all kinds of odd about this approach, which rests on the notion of ensuring a strong reference to self that persists through the handler's scope. Once you pass through the guard, the self reference will be valid for that lifetime. What do you think of this work-around, which of course would be improved merely by renaming ``self``?
    
    
    guard let strongSelfReference = self else {return} self.doSomething

([Mike Ash](http://mikeash.com) offered [another solution](https://swiftlang.ng.bluemix.net/#/repl/597afca36bc1ecf949d82cd95b19e4352d6a1442e6a345be9e195113f3f4fdfc) that works in existing Swift that I encourage you to peek at. His approach registers items and invokes callbacks.)

Looking forward in terms of Swift Evolution, I've recommended enhancements along the lines of:
    
    
    // self-shadow a weak item
    guard bind self else {return}
    self.doSomething
    
    //and an equivalent for a symbol that doesn't shadow itself
    guard bind symbol = someInstance.blah.weakReference else {return}
    symbol.doSomething

But don't hold your breath waiting for `bind` to appear in Swift.

I find `bind` clearer than overloading a constant or variable declaration. It's garnered no supporters and I've reluctantly been letting it go. (Although not so quickly that I didn't first include it in this post as a last farewell.)

Others suggested integrating a guard into the initial weak capture. Unfortunately` [guard self]` doesn't express how scope should exit. Should it return? Throw? Print an error? A separate guard statement is more verbose but it places explicit control in the hands of the developer on exit strategies.

How would you redesign things? What do you think of the pushpin? Does Swift need to change? If so, how?
