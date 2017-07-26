# The Stepdown Rule

_Captured: 2017-03-31 at 00:57 from [dzone.com](https://dzone.com/articles/the-stepdown-rule)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

It has recently occurred to me that some people are ordering the functions in a class randomly, mostly based on gut feelings. It's a good indicator that we should rehash the old, simple but very important…

## Stepdown Rule

The rule tells us that **the code in our class should be [readable](http://amzn.to/2mDj6jz) from top to bottom, descending one level of abstraction per function**. It implies that the function ordering is no longer random. A caller function should always reside above the callee function.

### Bad: Wrong Order
    
    
        self.give(fryingPan.getContents(80, PERCENT)); // huehuehue
    
    
            .forEach(egg -> fryingPan.add(egg.open());

As you can see, organizing the code randomly makes it far harder to comprehend. Also, you might not be interested in comprehending the details at all -- you could just want to get the idea on how the breakfast is done and the bad organization just caused you to read a lot of stuff that you didn't want to.

### Bad: Mixed Levels of Abstraction
    
    
       self.give(fryingPan.getContents(80, PERCENT)); // huehuehue
    
    
            .forEach(egg -> fryingPan.add(egg.open());

It's also important to extract the methods so that they keep the [same level of abstraction](https://dzone.com/articles/slap-your-methods-and-dont-make-me-think). Even if the makeBreakfast method is not too long at this point, it's still relatively hard to read.

_To make a breakfast, you need to:_

  * _Add eggs_
  * _Cook them_
  * _Give your wife 20 percent of frying pan contents_
  * _Give yourself 80 percent of frying pan contents_

Doesn't that sound ridiculous?

### Good
    
    
            .forEach(egg -> fryingPan.add(egg.open());
    
    
        self.give(fryingPan.getContents(80, PERCENT)); // huehuehue

Top-to-bottom, the same level of abstraction per function, one level of abstraction down per function call - as simple as that!

## What If…

  * _… the lower-level function is used by two or more higher-level functions?_ Then place it below the last usage.  

    
            self.give(fryingPan.getContents(80, PERCENT)); // huehuehue

  * _… there are two similar functions in the class? _That's actually a common temptation. As programmers, we're organized minds. We like symmetry and all that stuff. Wouldn't it look good if we did something like this:  

    
            self.give(fryingPan.getContents(80, PERCENT)); // huehuehue

  
No. People rarely read or search the code by method similarity. Stay top-to-bottom:  

    
            self.give(fryingPan.getContents(80, PERCENT)); // huehuehue

  * _… I'm writing a test, not a production class? _Yet another common temptation. We often have some "factory" methods to prepare our test data and they might not be necessary to comprehend the test itself:  
  
This one's tricky, but I'd stick to the _stepdown_ (top-to-bottom) approach. I believe that in a majority of cases, we feel tempted to push such stuff to the bottom because we're too lazy to make the code right. If the test setup takes too much work and makes the test incomprehensible, maybe it means that we should improve the design or use some patterns, instead of "put it down and forget?"  


## Summary

_The Stepdown Rule_ tells us that we should organize our code so that we can read the code top-to-bottom and each function call descends by [one level of abstraction](http://tidyjava.com/slap-your-methods-and-dont-make-me-think/). It applies even if a function is used multiple times, there are similar functions in the same class or we're writing unit tests. Last but not least, whether you choose to use the rule or not, [remember to stay consistent](https://dzone.com/articles/keep-your-code-consistent)! If I understand the key you use to organize functions in classes once, I should be able to use that understanding in any place in the project.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).

### Like This Article? Read More From DZone
