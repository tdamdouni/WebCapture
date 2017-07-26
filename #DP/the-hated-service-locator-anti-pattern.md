# The Hated Service Locator (Anti-)Pattern

_Captured: 2017-05-10 at 22:04 from [dzone.com](https://dzone.com/articles/the-hated-service-locator-anti-pattern?edition=298048&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-10)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

I was recently doing some reading about Spring and Dependency Injection in general when I came across a particularly harsh comment about the Service Locator pattern. The guy was so convinced that he was right that he even linked to the famous [Martin Fowler's post about injection](https://martinfowler.com/articles/injection.html), adding some other disrespectful comment. I was curious as to whether that was an isolated case or other people share this guy's opinions, so I started Googling the topic. To my surprise, a majority of the results I found yell from the very title: Antipattern! Don't use! It's bad for your health…

But is it?

## What the Haskell Are You Talkin' Bout?

Aside from some weird implementations using JNDI or reflection that you can find online, Service Locator can be a very simple way to resolve dependencies in your project. Instead of using a constructor or setters to provide the necessary dependencies for a class, the class takes whatever it requires from a central registry called the Service Locator. The simplest implementation of the pattern and its usage could look like this:
    
    
        public static void main(String[] args) {

Obviously, this is only a simplistic starting point. Depending on your needs, you can go from there and provide more sophisticated implementations of the locator. The key characteristic is that we're acquiring dependencies using the locator instead of Dependency Injection, Singletons, or the new keyword. Now, let's look why the pattern is so "evil".

## "It Makes Testing Difficult!"

If you'd like to write a unit test for class A, its constructor wouldn't tell you anything about the dependencies it has. You can write a compiling unit test that will fail with a `NullPointerException`.

Whoa! How EVIL! Did you see that?

Come on! That's laughable. How often do you write unit tests so long after implementation that you don't remember about loading some dependency inside the locator? Even if it happens to you sometimes, how hard is it to correct the mistake? It's trivial!

Hola, hola, Mr. Smartass, what about integration tests?! I'm writing these long after the initial implementation, and running the tests 20 times with 20 NPEs to finally load up all the dependencies is not really desired, is it?!

Two things. Firstly, the problem is not unique to the Service Locator pattern. Those still in the age of Spring XML configurations know that very well. Secondly, the problem is not really that hard to solve. I'll give you two ideas, and I'll trust in your brainpower to explore further if needed.

  1. You could use the same code that configures the locator in production code for testing purposes. Since you're already adding all new dependencies there, reuse might be a good option.
  2. You could prepare a test version of the locator that configures all "good" dependencies and stubs away the "bad" ones. After that, you can simply update both locators every time you add a new "service" to the application.

I know, I know. It requires a little thinking, but not that much, really.

## "The Dependencies Are Hidden!" -- Version 1

Fact: You can't see all of the class' dependencies by merely looking at their fields and/or constructors in a typical Service Locator usage scenario. Not really a fact: The dependencies between the classes are therefore hidden.

Watch the magic happen:

![](http://tidyjava.com/wp-content/uploads/2017/05/hidden-dependencies-1.png)

WHOOAAA! Look at this guy! He highlighted all of the lines with dependencies with a single mouse click in the IDE. He has to be a magician! But that's not everything! Two more clicks in my IDE and I've got this:

![](http://tidyjava.com/wp-content/uploads/2017/05/hidden-dependencies-2.png)

> _Noooo waaay! The IDE can unhide the hidden!_

## "The Dependencies Are Hidden!" -- Version 2

Fact: Missing dependencies will cause runtime errors rather than compile time errors when using the Service Locator pattern.

Another fact: The same applies when using DI containers instead.

Magician advice: Test your code so that these errors never occur! I guess it does not require further commentary.

## "You Can Easily Introduce Breaking Changes!"

This one is my favorite. I guess it comes straight from the land of spaghetti monoliths and people's silver bullet dreams.

![](http://tidyjava.com/wp-content/uploads/2017/05/screwdrivers.jpg)

Well, if you're trying to use the Service Locator pattern to configure your public APIs, regardless of whether these are for the general public or just another team in your company, I guess you're doing something wrong. It's even worse than using the screwdriver like in the quote above. It's like trying to get the nail in using your forehead. Leave your forehead safe and use the whole head to think instead. The fact that a pattern does not apply to every single use case does not make it an anti-pattern right away.

## "So, What Are You Trying to Say, Magician?"

I'm trying to say that most of the arguments for Service Locator being an anti-pattern are laughable. Of course the pattern is not a silver bullet. Of course, at first, it might not seem as easy to use as blindly spraying `@Autowired` or `@Inject` all over the place. At the same time, it's not as evil as people try to describe it online. It's different, but it has its strengths. For example, you don't have to use DI containers to construct the object graph for you or, God forbid, you don't have to do it manually.

The concept is very simple to understand and gives you endless possibilities for implementation. Given a bit of thought, it's as testable as regular dependency injection or even moreso (tests without DI containers run faster). All in all, I think that the Service Locator pattern could work really well, especially in modern microservices architecture, and deserves much more love than it currently gets.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
