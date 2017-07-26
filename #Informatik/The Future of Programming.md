# The Future of Programming

_Captured: 2016-04-26 at 23:38 from [sapan.svbtle.com](https://sapan.svbtle.com/musings-on-programming)_

> It seems to me that there have been two really clean, consistent models of programming so far: the C model and the Lisp model. These two seem points of high ground, with swampy lowlands between them. As computers have grown more powerful, the new languages being developed have been moving steadily toward the Lisp model. A popular recipe for new programming languages in the past 20 years has been to take the C model of computing and add to it, piecemeal, parts taken from the Lisp model, like runtime typing and garbage collection. -Paul Graham

I have done a lot of introspection recently on programming language design as I've learned Swift and become familiar with other languages including Objective-C, Javascript, Java, Ruby, Python, Go, Haskell, Clojure, Elixir and Elm. When I read the above quote by PG in his paper "The Roots of Lisp" my introspection finally gave way to some clarity that I would like to share.

**PARADIGMS**

On one hand you have the Object Oriented Programming paradigm seen in higher level derivatives of C including C++, Objective-C, Java, C#, Perl, Python, Ruby and PHP, where emphasis is on information hierarchy, separation of concerns and message passing. And on the other hand you have this "code and data are essentially the same" thinking present in Lisp. Because of this indifference between code and data, it makes sense that Lisp pioneered many critical ideas in computer science, the most notable, in my opinion is functional programming (where code can be an input, just like data). (Side note: This code is data paradigm also explains why Lisp was thought to be potentially so useful in Artificial Intelligence research where such a thesis would likely be a necessary ingredient in creating a self coding AI).

**FUNCTIONAL**

Functional programing is a must have in today's asynchronous message passing world. You see it popping up in all manners whether as completion blocks in Objective-C or as a first class citizen in Swift.

The reason functional programming is so critical is because creating and maintaining programs under OOP is hard. As programs become larger and more feature filled their complexity grow non-linearly and the state machine soon becomes exponentially complex, incomprehensible, verbose and damn near impossible to debug. Functional programming helps reduce the complexity by cutting down and eliminate transient state.

For example doubling an array of numbers imperatively in Swift:
    
    
    var nums =[1,2,3,4]for(var i=0; i<nums.count; i++){
      nums[i]*=2}//nums -> [2,4,6,8]

While doing it functionally in Swift:
    
    
    var nums =[1,2,3,4]
    nums = nums.map({num in num *2})//nums -> [2,4,6,8]

In the case of Swift we are able to completely bypass the need to manage state of iterating through the array and thereby removing complexity and potential for error.

But still, what is state?

**STATE**

> State is what makes our job as programmers VERY hard sometimes. To be honest, I didn't recognize this. That is to say, I knew when I had lots of different events and variables affecting my UI that it became really hard to manage; but I didn't recognize it in a philosophical, definable way. It's so ingrained in me that I just thought it was part of the deal with programming, and that maybe I wasn't the best programmer for constantly struggling with it. This is not the case. **Everyone sucks at managing state.** It is the source of an endless amount of bugs and blank stares. "I understand WHY it crashed. I just don't understand how the user could have possibly gotten it in that state." <- Programmer adds another state check. -Bob Spryn

State is the current permutation a program is in, and managing state is controlling the program and making sure it's not wandering of into one of the multitude of incorrect states it could take on. This is critical because every time you add another variable, you increase the number of permutations **exponentially**, for example in the case of a boolean by a power of 2.

![state.png](https://svbtleusercontent.com/cxwapabv5d0oxq_small.png)

What if we could combine the power of functional programming with something else to help prevent this exponential complexity?

**REACTIVE**

> Native apps spend a lot of time waiting and then reacting. We wait for the user to do something in the UI. Wait for a network call to respond. Wait for an asynchronous operation to complete. Wait for some dependent value to change. And then they react. But all those things--all that waiting and reacting--is usually handled in many disparate ways. That makes it hard for us to reason about them, chain them, or compose them in any uniform, high-level way. We can do better. -Josh Abernathy co-creator of ReactiveCocoa

In this pursuit of simplifying state, a new exciting paradigm called Functional Reactive Programming (FRP) has emerged. FRP is a way of thinking about software in terms of transforming inputs to produce output continuously over time. Consider the following example of a user sign up flow in iOS.

Here's a conventional, imperative paradigm approach in Objective-C:
    
    
    -(BOOL)isFormValid {return[self.usernameField.text length]>0&&[self.emailField.text length]>0&&[self.passwordField.text length]>0&&[self.passwordField.text isEqual:self.passwordVerificationField.text];}#pragma mark -UITextFieldDelegate-(BOOL)textField:(UITextField*)textField
    shouldChangeCharactersInRange:(NSRange)range
    replacementString:(NSString*)string{self.createButton.enabled =[self isFormValid];return YES;}

Here's a FRP approach in Objective-C via the ReactiveCocoa framework:
    
    
    RACSignal*formValid =[RACSignal
      combineLatest:@[self.username.rac_textSignal,self.emailField.rac_textSignal,self.passwordField.rac_textSignal,self.passwordVerificationField.rac_textSignal
      ]
      reduce:^(NSString*username,NSString*email,NSString*password,NSString*passwordVerification){return@([username length]>0&&[email length]>0&&[password length]>8&&[password isEqual:passwordVerification]);}];
    
    RAC(self.createButton.enabled)= formValid;

FRP is such an amazing tool because instead of setting a value one time for the button, it instead elegantly creates a relationship between form validity and button enabled-ness which persists over time. Thus FRP gives us a way to think of programs as just input and output, thereby allowing us to minimize state and code more effectively.

**Lisp**

> Over time, the median language, meaning the language used by the median programmer, has grown consistently closer to Lisp. So by understanding Lisp you're understanding what will probably be the main model of computation well into the future. -Paul Graham

There's all kinds of other stuff still left to explore in Lisp that may trickle down, for example macros, but that's for another post.

**Conclusion**

Ultimately, Object Oriented Programming languages are becoming more powerful, functional, reactive, and Lisp-like overtime in order to help the modern programmer reduce exponential complexity and verbosity in today's asynchronous performant era.
