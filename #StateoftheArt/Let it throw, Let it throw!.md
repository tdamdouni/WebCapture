# Let it throw, Let it throw!

_Captured: 2015-12-17 at 01:14 from [alisoftware.github.io](http://alisoftware.github.io/2015/12/17/let-it-throw/)_

Today's article will be about handling errors in Swift.  
Because let's be honest, that makes a fun post title for the season ❄️☃️.

## Objective-C and the NSError of its ways

Remember Objective-C? Back then[1](http://alisoftware.github.io/2015/12/17/let-it-throw/), the main and official way for a method to tell that something went wrong was to take a `NSError*` by reference.
    
    
    NSError* error;
    BOOL ok = [string writeToFile:path
                       atomically:YES
                         encoding:NSUTF8StringEncoding
                            error:&error];
    if (!ok) {
      NSLog(@"An error happend: %@", error);
    }
    

Man that was painful. To the point that many people were tempted to not even bother to check for errors and simply pass `NULL` there. Not very responsible and safe.

## Do you want to build a throw, man?

![Frozen-Illustration-1](http://alisoftware.github.io/assets/frozen-throw-man.jpg)

With Swift 2.0, Apple decided to introduce a different way to handle errors: using `throw` [2](http://alisoftware.github.io/2015/12/17/let-it-throw/).

The use of `throw` is actually quite simple:

  * If you want to create a function that might fail, mark it with `throws` in its signature;
  * Inside the function itself you can use `throw someError` if needed;
  * At call site, you'll have to explicitly use `try` in front of your calls to methods which can throw[3](http://alisoftware.github.io/2015/12/17/let-it-throw/);
  * To catch errors and handle them, use `do { … } catch { … }` constructs.

This looks like this:
    
    
    // Define a function that can throw…
    func someFunctionWhichCanFail(param: Int) throws -> String {
      ...
      if (param > 0) {
        return "somestring"
      }
      else {
        throw NSError(domain: "MyDomain", code: 500, userInfo: nil)
      }
    }
    
    // … then call it
    do {
      let result: String = try someFunctionWhichCanFail(-2)
      print("success! \(result)")
    }
    catch {
      print("Oops: \(error)")
    }
    

## The failure never bothered me anyway

![Frozen-Illustration-2](http://alisoftware.github.io/assets/frozen-failure.jpg)

You can see that `someFunctionWitchCanFail` returns a plain `String`, which is the type returned when everything was ok. It makes it easy to call the function "normally", first thinking (in the `do { … }` block) about the **happy** path, to handle the case where nothing wrong happens.

The only reminder that those methods can fail is the `try` keyword that the compiler enforces you to add in front of that call, otherwise it's like a non-throwing function call. And then, you only write the code to handle errors in a separate place (inside the `catch`)

Note that you can write more than one line (and `try`-call more than one throwing function) in that `do` block. If everything is successful, it will execute them as expected, but as soon as one of them fails it will jump out of the `do` block into the `catch` statement instead. That's very handy as well for long runs of code with multiple potential points of failure, as you can handle them all in a single error path at the end.

## NSError is a bit of a fixer-upper

![Frozen-Illustration-3](http://alisoftware.github.io/assets/frozen-fixer-upper.jpg)

Ok, but with this example we still have to handle errors using `NSError`, which is a pain. Comparing domains and error codes with `==` and make a list of domain and code constants, just to know which error we got and handle it properly… ouch.

But we can fix this fixer-upper… up with a little bit of love! What if we used what we learned in my [Enums as Constants](http://alisoftware.github.io/swift/enum/constants/2015/07/19/enums-as-constants/) article and use `enums` to represent errors instead?

Well, Good news, everyone!™, that's exactly what Apple intended in this new error handling model! In fact, when a function `throw`, it can throw any object which conforms to `ErrorType`. `NSError` is one of those types, but you can make your own, and it's even recommended!

The best fit for an `ErrorType` type is an `enum`, which can even have associated values if needs be. For example:
    
    
    enum KristoffError : ErrorType {
      case ClumsyWayHeWalks
      case GrumpyWayHeTalks
      case PearShapedSquareShapedWeirdnessOfHisFeet
      case NotWashedSince(days: Int)
    }
    

Then you can now use `throw KristoffError.NotWashedSince(days: 3)` in a function to throws this kind of error, then use `catch KristoffError.NotWashedSince(let days)` at call site to catch such errors:
    
    
    func loveKristoff() throws -> Void {
      guard daysSinceLastShower == 0 else {
        throw KristoffError.NotWashedSince(days: daysSinceLastShower)
      }
      ...  
    }
    
    do {
      loveKristoff()
    }
    catch KristoffError.NotWashedSince(let days) {
      print("Ewww, he hasn't had a shower since \(days) days!")
    }
    catch {
      // Any other kind of error, whatever it is
      print("I prefer we stay friends")
    }
    

That's way easier to catch specific errors than having to compare domains and error codes!

That also makes better errors with clear names as constants and associated values. No more obscure `userInfo`, you have a clear list of associated values right there in the enum case of the error -- like `days` in the above example -- which are only valid for that specific type (wouldn't make sense to have that `days` associated value for the `ClumsyWayHeWalks` error).

## I can't hold it back anymore

![Frozen-Illustration-4](http://alisoftware.github.io/assets/frozen-cant-hold-it-back.jpg)

When you call a `throw`-ing function, the error it throws can be caught in the calling function using a `do…catch`. But if it isn't, then it propagates to the upper level:
    
    
    func doFail() throws -> Void { throw … }
    
    func test() {
      do {
        try doTheActualCall()
      } catch {
        print("Oops")
      }
    }
    func doTheActualCall() throws {
      try doFail()
    }
    

Here when `doFail` is called, the potential error is not caught by `doTheActualCall` (there is no `do…catch` capturing it), so it propagates up to the calling `test()` function. Because it doesn't catch all errors, `doTheActuallCall` must also be marked as `throws`: even if it doesn't throw errors by itself, it can still propagate some. It can't keep the error to itself, it has to… _let it go_ to the upper level.

On the other end, `test()` catches all errors internally so even if it calls a throwing function (`try doTheActualCall()`), all errors thrown by that function are caught in the `do…catch` block. The `test()` function itself doesn't throw, so callers don't need to know about this internal behavior.

## Conceal, don't feel, don't let them know

![Frozen-Illustration-5](http://alisoftware.github.io/assets/frozen-conceal-dont-feel.jpg)

You may have wondered by now how to know which kind of error each method throws. Indeed, functions are marked with `throws` but what `ErrorType` can this function actually throw? Can it throw `KristoffErrors`, `JSONErrors`, other? Which ones do I need to catch?

Well that's a problem. Currently, due to some ABI and resilience concerns[4](http://alisoftware.github.io/2015/12/17/let-it-throw/), this is not possible. The only way to know is using the documentation of your code.

But that's also a good thing. For example, imagine you use two libraries, `MyLibA` containing a function `funcA` that `throws` errors of type `MyLibAError`, and `MyLibB` with a function `funcB` that `throws` errors of type `MyLibBError`.

Then you want to create your own library, a wrapper around those two libraries, with a function `funcC` that calls both `MyLibA.funcA()` and `MyLibB.funcB()`. Then the resulting function `funcC` might throw either error of type `MyLibAError` or `MyLibBError`. And if you add another level of abstraction, it gets worse, with more and more error types being able to be thrown. If we had to list them all, and the call site would need to catch them all, that would make a quite verbose signature.

## Don't let them in, don't let them see

![Frozen-Illustration-5](http://alisoftware.github.io/assets/frozen-dont-let-them-in.jpg)

For that reason, but also to prevent your internal errors from bleeding across your library boundaries and to limit the number of error types that must be handled by your users, I suggest that you keep your error types scoped to each level of abstraction.

In the example above, instead of making `funcC` directly propagate both `MyLibAErrors` and `MyLibBErrors`, you should instead throw `MyLibCErrors`. I suggest this for two reasons, both related to abstraction:

  1. Your users shouldn't have to know which internal library you're using. If some day in the future you decide to switch your implementation to use `SomeOtherPopularLibA` instead of `MyLibA`, which will obviously not throw exactly the same errors, the caller of your own `MyLibC` framework shouldn't need to know or care. That's what abstraction is all about.
  2. The caller shouldn't have to handle all the errors. Surely you can catch some of those errors and consider them internal: not all errors thrown by `MyLibA` make sense to be exposed publicly to your users, for example a `FrameworkConfigurationError` error mentioning that you misused the `MyLibA` framework and forgot to call its `setup()` method or whatever should not make its way to the user, as the user can't do much about it. That kind of error is your fault, not theirs.

So instead, your `funcC` should probably catch all `MyLibAErrors` and `MyLibBErrors`, wrap them / re-interpret them and expose them as `MyLibCErrors` instead. That way, the users of your framework don't have to know what you're using under the hood. You can switch your internal implementation and libs used at any time, and you expose to the user only the errors they might care for.

## We finish each others sandwiches[5](http://alisoftware.github.io/2015/12/17/let-it-throw/)

![Frozen-Illustration-6](http://alisoftware.github.io/assets/frozen-sandwiches.jpg)

There is a lot more to tell about `throw` and the Swift 2.0 error model. I could talk about `try?` and `try!`, about the `rethrows` keyword for high-order functions.

I won't have time to talk about every subject about error handling there, that would have made that post way too long; but other interesting blog posts might help you finish your exploration in the world of Swift error handling, including (but not limited to) those:

  * [Throw that don't throw](http://robnapier.net/throw-what-dont-throw) and [Re…throws?](http://robnapier.net/re-throws) by Rob Napier
  * [Error Handling](https://littlebitesofcocoa.com/108-error-handling) by Little Bites of Cocoa
  * [What we learned from rewriting our robotic control software in Swift](http://www.sunsetlakesoftware.com/2015/11/03/what-we-learned-rewriting-our-robotic-control-software-swift), by Brad Larson
  * … _(Don't hesitate to share more links in the comments section!)_

Let me finish this article by wishing you all happy holidays ☃️❄️ and see you soon for the next post!

![Happy Holidays](http://alisoftware.github.io/assets/frozen-olaf-holidays.jpg)

> _Happy Holidays_

  1. For more info about how the old way to handle errors in Objective-C work, see [this great article by NSHipster](http://nshipster.com/nserror/). But today's article is about Swift and the new way, so let's not lose too much time about that old beast. [↩](http://alisoftware.github.io/2015/12/17/let-it-throw/)

  2. Despite its name, `throw` is not about throwing _exceptions_ like in Java or C++ or even ObjC. But the way to use it is so similar that Apple decided to keep the same wording so that people used to exceptions find it natural. [↩](http://alisoftware.github.io/2015/12/17/let-it-throw/)

  3. This is enforced by the compiler, the aim being to let you realize that this function can go wrong and you have to handle the potential error [↩](http://alisoftware.github.io/2015/12/17/let-it-throw/)

  4. Swift 2.0 doesn't support typed throws, but [there is a discussion about adding that feature in [the swift-evolution Mailing List](https://lists.swift.org/pipermail/swift-evolution/2015-December/000076.html) where Chris Lattner explains why this was not possible in Swift 2 and why we need the resilience model of Swift 3.0 to be able to make that feature consistent. [↩](http://alisoftware.github.io/2015/12/17/let-it-throw/)

  5. Ok, promise, that was my last shameful _Frozen_ reference. [↩](http://alisoftware.github.io/2015/12/17/let-it-throw/)
