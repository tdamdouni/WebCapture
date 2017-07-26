# I Shall Call It.. SomethingManager

_Captured: 2015-11-19 at 17:33 from [blog.codinghorror.com](http://blog.codinghorror.com/i-shall-call-it-somethingmanager/)_

Alan Green rails against [the meaninglessness of `SomethingManager`](http://www.bright-green.com/blog/2003_02_25/naming_java_classes_without_a.html):

> How many classes do you come across named `SomethingManager`? Any decent sized commercial system seems to have plenty - `SessionManager`, `ConnectionManager`, `PolicyManager`, `QueueManager`, `UrlManager`, `ConfigurationManager`, or even, sadly, `EJBManager`. 
> 
> A quick look at the dictionary entry for "[manager"](http://www.merriam-webster.com/dictionary/manager) and "[manage"](http://www.merriam-webster.com/dictionary/manage) gives at least ten different meanings - from "to make and keep compliant" through to "to achieve one's purpose". I remember one day when the receptionist briefly retitled herself as Switchboard Manager. The common semantic to all these definitions seem to be a vague "looks after stuff". 
> 
> This imprecision makes Manager a bad word to use in naming classes. For instance, take a class named `UrlManager` - you cannot tell whether it pool URLs, manipulates URLs or audits the use of them. All the name tells you is that this class does something with URLs. On the other hand, the name `UrlBuilder` provides a much clearer picture of what the class does. 
> 
> In the Java world, the Manager suffix is thrown around a lot. Almost anywhere you have a class that is responsible in any way for other objects, it automatically earns the Manager label. 

There's nothing more ambiguous than a `SomethingManager`. Avoid this word. Alan proposes a few alternatives in [his blog post](http://www.bright-green.com/blog/2003_02_25/naming_java_classes_without_a.html) that might be helpful in narrowing down what your class actually does.

Giving your classes and objects good, descriptive names isn't easy. Steve McConnell provides a few helpful guidelines for routine naming in [Code Complete](http://www.amazon.com/exec/obidos/ASIN/0735619670/codihorr-20):

  1. **Describe everything the routine does**  
And we mean literally _everything_. If that makes the name ridiculously long, the name isn't the problem. Your routine is.  
  

  2. **Avoid meaningless, vague, or wishy-washy verbs**  
Like `UrlManager`, or `HandleOutput()`, or `PerformServices()`. Be specific. What does it _do?_ If you can't answer that question succinctly, it may be time to refactor the code until you can.  
  

  3. **Don't differentiate routine names solely by number**  
I include this only for completeness. If you ever find yourself writing `OutputUser1()` and `OutputUser2()`, God help you. And God help the team you work with.  
  

  4. **Make names as long as necessary**  
According to McConnell, the optimum name length for a variable is 9 to 15 characters; routines tend to be more complex and therefore deserve longer names. Make your names as long as they need to be in order to make them understandable.  
  

  5. **For functions, try using a description of the return value**  
An easy, straightforward rule. Some examples are `printer.IsReady()`, `pen.CurrentColor()`, etcetera.  
  

  6. **Use opposites precisely**  
For every `Open()`, there should be a `Close()`; for every `Insert()`, a `Delete()`; for every `Start()`, a `Stop()`.  
  

  7. **Establish conventions for common operations**  
This is best illustrated with an example, and McConnell provides an excellent one: 
    
        employee.id.Get()
    dependent.GetId()
    supervisor()
    candidate.id()
    

Now how do I get an Id again? 

I'd say renaming classes and variables is one of my most frequent refactoring activities. [Creating good names is hard](http://martinfowler.com/bliki/TwoHardThings.html), but it _should_ be hard, because a great name captures essential meaning in just one or two words

It's difficult to tell what something should be named until you're completely finished writing it. And like most code, it's never quite done, so the name may change over time. Succinct, descriptive variable, object, and function names can make the difference between [Daily WTF code](http://thedailywtf.com/) and… well, code you'd actually want to work on.

#### Written by Jeff Atwood

Indoor enthusiast. Co-founder of Stack Exchange and Discourse. Disclaimer: I have no idea what I'm talking about. Find me here: <http://twitter.com/codinghorror>
