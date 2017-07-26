# Optional Method Parameters

_Captured: 2017-03-01 at 02:55 from [dzone.com](https://dzone.com/articles/optional-method-parameters?edition=271922&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-28)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

I have recently come across an interesting problem: should you use Optional as a method parameter type? The majority of sources says that you shouldn't, but let's weigh the arguments before making a verdict.

## Why Not Just Pass Nulls Around?

Before we get into the case of using Optional, we should understand _why we even have this problem_. We could just pass nulls around, right? Well, not quite. As I've written in [my post about null handling](http://tidyjava.com/10-tips-handle-null-effectively/), you should never pass null as an argument to a public method. It'd require you to read all the code down the call stack to make sure that null value is actually supported and won't blow the application. And once you'd do that, the callee code could not be modified in any way that does not support null, which is a rather unwanted constraint. Therefore, you need another solution in case one of the parameters is missing.

Now, that we're done with nulls, let's evaluate using the Optional type.

## "It Was Not Meant to Be Used Like This"

The majority of articles that I read, and even my fantastic IDE point out, that Optional as a method argument is bad because the original intent of creating Optional was to:

> [..] provide a limited mechanism for library method return types where there needed to be a clear way to represent "no result". 

I'm sorry to say this, but this is a really bad argument. If there would be arguments for using Optional as a parameter type that outweigh the arguments against, it would only mean that the class is better than it intended to be and everyone should be happy. It's like saying that you should not use a bread knife to open a package in your kitchen because the bread knife was not meant to do that.

## "It Causes Conditional Logic Inside Methods"

The source of this argument is the top answer in [a related question on StackOverflow](http://stackoverflow.com/questions/31922866/why-should-java-8s-optional-not-be-used-in-arguments). To quote the original author:

> Using Optional parameters causing conditional logic inside the methods is literally contra-productive. 

This argument refers to a situation when you use Optional as a method parameter just to do conditional logic based on its presence:

It is an argument, but a limited one. The first limitation that I see is that oftentimes you would not do any conditional logic on the argument -- you just want to pass it through:

The second limitation is that the only reasonable alternative that you have in most cases is method overloading. Then, if a client has a potential null on his side, he's forced to do the conditional logic himself:

This, depending on the case might be a good thing or a bad thing.

## "It's Still Perfectly Possible to Pass in Null to a Method"

That's a quote from [another StackOverflow answer](http://stackoverflow.com/a/31923042). I'd say that it can be an argument against Optional in general, but not solely against Optional arguments, as you can return a null instead of Optional, too. As a general argument, it still seems weak, as we're not talking about a dangerous toy for a kid, we're talking about programmers (smart guys, you know?). If we followed this logic, we'd have to say that using Java is unsafe as you can do almost anything via reflection. Would that stop you from using Java? Obviously not.

## "Function Does More Than One Thing"

Ah, us clean coders! Such a good movement, but sometimes we tend to overdo things. But yes, that could be a code smell, especially if that one thing would be the conditional logic we talked about earlier. I'm not so sure if it would be so evil if the logic looked like this:

Does it still do more than one thing? Maybe. Is that bad for your codebase? Hard to judge, you'd have to consider other forces.

## "The Client Code Has to Explicitly Wrap"

Now, we're on the client side of things and it seems like a valid argument. If the client has the value and knows that it's surely not null, wrapping it into an optional might seem like a waste.

On the other hand, we've shown already that if the client has a potential null in hand, he might get even more complexity if we opt for overloading. Just look at the first client example above and compare it to this one:

Also, don't forget that the client can leverage static imports to control the complexity of the invocation.

To conclude this argument, know your clients! A safe approach would be to choose one depending on the client's needs. If you don't know all your clients e.g. in a case of library code, you should probably stick to overloading.

## "[..] Imagine Having Two or Three"

Daniel Olszewski, in his article titled [Java 8 Optional Use Cases](http://dolszewski.com/java/java-8-optional-use-cases/), argues that the case of Optional method parameters is much worse in the case of multiple such parameters. My intuition suggests that this could be the case, but I can't come up with a good example. He does not provide any examples or reasoning for such state of things, just:

> Uncle Bob definitely wouldn't be proud of such code 

All due respect to Uncle Bob, that's not a valid argument. I'd say that you should apply common sense and other known guidelines to figure out what's the best in such case.

We're done with the arguments against Optional method parameters that I found online. Let me augment those with some of my recent reasoning.

## Pass-Thru Optional

Imagine that one of your API parameters is optional and it's represented by a null. The data from your API is supposed to go from the controller, through application and domain services, down to the depths of your domain model. And it's only the domain model that knows the "reasonable default" for that field, e.g. null, which you shouldn't pass around for some boundary value like MAX_INT. Obviously, you could just make this default value a public constant and pass it in the controller. But do you really want to couple the controller to an implementation detail of your domain class, especially if that would mean passing a null around? I don't.

This is the case that we've already seen in the argument about conditional logic. The Optional is supposed to pass through down the call stack to be handled by the class that actually knows what to do it. In our case, it would look like this:
    
    
        void method(Optional<String> argument) {
    
    
        void method(Optional<String> argument) {

I will skip the overloading version for brevity (you can see it in [this gist](https://gist.github.com/anonymous/7e3f26d010534dc78127f6e42dee0387)), but it's much longer and less expressive. Instead of stating clearly in the code: _This parameter is optional_, we're adding the_ complexity_ of multiple analogous overloads. And it's just for one such parameter, "imagine having two or three!"

## What's More Testable?

This question is the reason why I started the research and then decided to write this article. If we consider overloading the right alternative to Optional method parameters, we might end up with a lot of unnecessary tests.

Let's say that our method (and the private ones that it calls) has two testable side-effects and one error case in which it throws an exception. If I were to write tests for this method, it would look more or less like this:

That's already a decent amount of code. Now, imagine testing the two overloaded methods… I don't want to make you scroll down in annoyance but if someone wants to see it, I created [a gist](https://gist.github.com/anonymous/c255ede3b77cdc2d2c844f4e0aa16627). And with all that being said, let's once again "imagine having two or three."

## Conclusion

There are some valid arguments against using Optional as method parameter type, but to me, they are not good enough to be able to say with confidence that you should avoid it at all costs. And don't forget, there are also arguments _for_ using Optional this way. I'd say that you should keep each of them in the back of your head and evaluate things on a case by case basis. Like always, it's an _it depends_ problem, and it requires a bit of programming sense.

If you have any additional arguments for or against using Optional as method parameter type, let me know in comments!

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
