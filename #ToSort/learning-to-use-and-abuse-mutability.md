# Learning to Use and Abuse Mutability

_Captured: 2017-01-31 at 23:54 from [dzone.com](https://dzone.com/articles/learning-to-use-and-abuse-mutability?edition=266901&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-31)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

![](https://cdn-images-1.medium.com/max/2000/1*sATSRAvqzDPhQr46Fda56w.jpeg)

I am an old Java man. I never allocated many of my thoughts to reflect on the philosophy of mutability. In Java, unlike in other languages, there is no precise control over what is mutable and immutable. I never thought of Java objects as having this feature. Instead, I would always refer to them as _"that Java class that has no setter."_ _"That Java class that cannot be modified once the value has been set up." _A very non-scientific wording in an almost scientific world. Mutability is the default in imperative languages, and we just do not think a lot about it. There is a lack of awareness, and our minds work inertially on the paradigm we have learned.

![](https://cdn-images-1.medium.com/max/800/1*vqMIv93v28QsBFzEKaqipA.jpeg)

Through my career, I saw that many languages could distinguish between the mutability of a class. And this was cool, but since I never used it so much (I have mostly worked on Android and J2EE), I let it go. It was not in my sphere of influence.

A year ago, I started working with Kotlin. It has been a bright light in how I develop, and I use it and advocate for it when I can (I do also curate the [Kotlin Weekly](http://kotlinweekly.net), if you want to subscribe for a weekly dose). If you happen to develop for Android, you are likely doing it in Java. Version 1.0 of Java [was released in 1995](http://www.oracle.com/technetwork/java/javase/overview/javahistory-index-198355.html). That is right, 22 years ago. The world was a very different place back then, and Java was designed to tackle the challenges of that time. Smartphones did not exist as we know them. Neither were phones so commercially available as they are nowadays. When Java was released, Windows 95 was not even available to the public (yes, Java is that old). eBay had just started.

I like to think of the IT world as an analogy to the Stock Market. In the 1960s, General Motors was the dominant company, and nobody could compete against them. The US government even thought of forcing its breakup into small parts to avoid a huge monopoly. Today, General Motors survives, thanks to a huge bailout, as a walking zombie. In the 1990s, nobody would have bet a dime on Apple. Today, Apple is the single largest global company.

> Today's stars are tomorrow's wrecks. Today's fallen are tomorrow's exciting turnarounds -- J.L.Collins, [The Simple Path to Wealth](http://amzn.to/2kKBGB9)

Java has evolved through many patches and updates. I am not criticizing the language: I do make a living by speaking Java -- although I do not restrict myself only to it. But in the meantime, new stars are rising, and here I think of Kotlin. Straight to the point, Kotlin distinguishes between mutable and immutable collections. Out-of-the-box.

Recently, my colleague in the [Google Experts](https://developers.google.com/experts/) program [Mike Nakhimovich](https://medium.com/u/6ebfb5fe99f9) posed the following on Twitter: "Just make everything immutable and avoid it?"

That also put my brain to work. I wrote recently a blog post, "[On properly using volatile and synchronized."](https://medium.com/google-developer-experts/on-properly-using-volatile-and-synchronized-702fc05faac2#.nitcvxkfz) I realized that threading and synchronization are hard. Oh man, so many edge cases, so many concepts colliding, so much abstraction. And this solution is an out-of-the-box solution. I used it sometimes, and I always saw it as a hack.

After this introduction, let's explore the world of mutability in Java and all its perks. In order to tackle the problem more efficiently, let's provide the following definition as an axiom:

> An immutable class is a class whose state cannot be changed once it has been created. 

Easy peasy. If you are in the Java arena, now you can come up with a few clues of how to make a class immutable.

  * **All fields must be private**. This is another axiom of the OO programming paradigm. If a field is private, it cannot be externally changed. If, as a bonus, it's also final, you cannot accidentally change it.
  * **Do not provide a setter**. Combine this with the previous point. If the fields are private and there is no setter provided, this class fields will always remain the same.
  * **Subclasses should not be able to override methods**. Otherwise, they can trick our immutability. This is easy. Just declare the class as final.

Check in this example to see how it can look:

We have covered the theoretical part. Now, what can we do with this?

## The Good

  * Immutable objects can make life easier. An immutable object is automatically thread-safe, and it has no synchronization issues. Wow, big pro! They make concurrent programming safer and cleaner. Have you ever debugged a concurrent programming issue? Most of the bugs are due to sharing state between threads. Imagine just getting rid of it at a glance. Worth trying.
  * Immutable objects do not need a copy constructor or an implementation of clone. For the sake of simplicity.
  * Have you heard of the term failure atomicity, coined by Joshua Bloch in [Effective Java](http://amzn.to/2jJoq1V)? It means that when an immutable object throws any exception, it will never result with the object left in an indeterminate state. Big kudos.

## The Bad

  * Making copies of objects in order to mutate them can drain our resources, especially when dealing with complex data structures. Also, changing objects with a distinct identity can be also more intuitive.
  * Our perception of the model world is based on mutable objects.

## What Should I Do?

I have heard that "mutability is the source of all evil." I like to have multiple options and not take anything as a dogma. The more options, generally speaking, the better.

In Effective Java, Joshua Block writes:

> "Classes should be immutable unless there's a very good reason to make them mutable. If a class cannot be made immutable, limit its mutability as much as possible."

Immutability can solve many problems and make your life easier, especially when it comes to working in a concurrent environment. However, it can over-engineer and make things more complex if you use it by default. So know your war, and apply the solution that fits more.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
