# 10 Tips to Handle Null Effectively

_Captured: 2017-01-27 at 19:37 from [dzone.com](https://dzone.com/articles/10-tips-to-handle-null-effectively?edition=265886&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-27)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

When I started programming in Java, I considered the null value my enemy and I dreaded NullPointerExceptions, which happened fairly often to me. Over time, I learned to work with it, and nowadays, I can consider my personal battle with nulls a victory. Most NPEs that I see nowadays are caused by incorrectly set up mocks during development. I can't even remember the last time I caused an NPE in a production environment. But enough bragging, here's my list of practices when dealing with null values.

## 1\. Don't Overcomplicate Things

Handling nulls can be a complicated problem on its own and therefore we should make it as clean and as obvious as possible. One very bad practice that I've seen in some codebases is using Objects methods, Optional classes, or even a [separate method using Optional](https://dzone.com/articles/the-optional-abomination) in places where a simple null check would be enough. This caused me to check where the method comes from, what it contains, and wonder what the difference is between this and direct comparison. Of course, your mileage may vary, but for me, this is significant overhead that we should avoid.

## 2\. Use Objects Methods as Stream Predicates

Although Objects.isNull and Objects.nonNull are not the best fit for typical null checks, they are a perfect fit to use with streams. The filtering or matching lines with them read (arguably) much better than those with operators. In fact, this is the reason why they were introduced in the JDK.

## 3\. Never Pass Null as an Argument

This is one of the most important principles of good coding, but if you don't know it already, you deserve an explanation. Passing null to indicate that there's no value for a given argument might seem like a viable option. But it has two big disadvantages:

  1. You need to read the function's implementation and figure out if it, and potentially every affected function down the way, can handle null value correctly.
  2. You have to always be careful when changing function's implementation not to throw away something that might handle nulls for its users. Otherwise, you have to search through the whole source code to check if null is being passed anywhere.

By accepting the principle of never passing null, both of these problems are gone forever. And what about a function with optional parameters? It's simple, just overload the function with different sets of parameters:

By the way, since the two disadvantages are not that visible in the scope of a single class, you can give up on the rule when dealing with private methods. Just make sure things are safe from the outside.

## 4\. Validate Public API Arguments

You and your team might use the principle of not passing nulls with great success, but when you're exposing a public API, you have no control over its users and what they pass to your functions. For this reason, always check the arguments being passed to your public APIs for correctness. If your only concern is the nullity of the argument, consider using the requireNonNull function from the Objects class:

## 5\. Leverage Optional

Before Java 8, it was common that a method would return null in the case of a missing value. This was inherently error prone, as the developer had to always check the documentation or, if the documentation was missing, the underlying source code for the possiblity of null being returned. Since JDK 8 was released, we have the Optional class available, designed specifically to indicate that a return value might be missing. A developer calling a method with Optional as the return value has to explicitly handle the case when the value is not present. Therefore, wrap your return types with Optional when applicable.

## 6\. Return Empty Collections Instead of Null

We already know that null is not the best return value for a method and that we can make use of the Optional class to indicate that the value might be missing. But things are a bit different when we're talking about collections. Since a collection can contain any amount of elements, it can also contain… 0 elements! There are even special emptyXxx methods in the Collections class that return such collections. Therefore, we should avoid returning null or complicating things with Optional and return an empty collection when there are no values to fill it with.

## 7\. Optional Ain't for Fields

As I already said, Optional was designed to indicate missing return values. One tempting case that it was not designed for and surely is not necessary for is class fields. By means of encapsulation, you should have full control over the field's value, including null. On the other hand, making fields explicitly Optional might bring you weird problems like:

  * How should you write a constructor or setter for such a field?
  * How should automappers handle those fields?

Therefore, use direct references for fields and carefully analyze whether a field can be null or not at any given point. If your class is well-encapsulated, this should be fairly easy.

## 8\. Use Exceptions Over Nulls

One strange case when you might see people using null is exceptional situations. This is an inherently error prone practice, as critical errors can be omitted or resurface in different places of the system, causing debugging to be a pain. Therefore, always throw an exception instead of returning null if something went wrong.

## 9\. Test Your Code

Well, this advice is related to all kinds of bugs, not just unexpected nulls, but it's so important that I felt it should make it to the list. Testing your code thoroughly using an environment similar to production is a great way to prevent NPEs. Never release a piece of code without making sure it works. There's no such thing as "a quick, simple fix that doesn't require testing."

## 10\. Double Check

Every time you assume that some reference cannot be null, double check that you're right. This is especially important when dealing with huge legacy databases or external providers. With the former, take the time to check if the columns you're meaning to use do not contain any null values, and if they do, check if those rows can make it into your system. In case of external providers, rely on contracts, documentation, and if you're not sure, send an email or call someone to make sure your assumptions are right. This might be annoying, especially when working with a poorly documented API, but when it comes to nulls: _better safe than sorry_!

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
