# Guice Stories ( Part 1)

_Captured: 2017-05-03 at 23:44 from [dzone.com](https://dzone.com/articles/guice-stories-part-1?edition=294992&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-03)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

I've always been a fan of [Google Guice](https://github.com/google/guice). More so lately, as Guice became an indispensable part of [Bootique.io](http://bootique.io/) , responsible for Bootique's dependency injection (DI) and modularity. Guice is a simple, fun, and powerful DI engine with a number of advantages over the industry _status quo_, yet there's not a lot of guidance out there on its proper use compared to, say, Spring. To partially fill this gap, I wrote a few "stories", each describing a coding or a design task, then going through Guice solutions, from the most obvious to the most optimal. I hope this will be useful to developers who use either Guice or Bootique. This post starts with two stories. More will follow.

## Story 1: Injection Hygiene

This story is about basic injection. We assume some services have been already "bound" in Guice and we want to use them to write our own "service". The simplest way to get a hold of another service is via field injection:

This is a quick and dirty approach. It is obvious why I am calling it quick: We declare an instance variable and annotate it with `@Inject`. Very little code. Why is it dirty though? Well, we ended up with a class that has a hard dependency on the injection container. There's no way (short of ugly reflection) to create instances of `A` without Guice. So you won't be able to write unit tests, etc. An obvious refactoring is to create a public constructor and use constructor injection:

Much better -- now both Guice and our own code will be able to create instances of `A`. This is good enough and we can stop here, or we can perfect our solution a bit more. Notice that we still have a compile dependency on the `@Inject` annotation. I don't know about you, but annotations on _domain _objects always look like a code smell to me. Let's refactor this to a pure object, moving the construction code into a "provider" method inside our Guice module:

We ended up with a bit more code, but this code is arguably higher quality than what we had initially. And in a real app with many DI-managed objects of some complexity, such a trade-off will actually pay off.

There are other reasons as well why constructor injection may not be ideal, and the provider approach can save us. Some objects can have too many dependencies, so the argument list becomes unwieldy. (Yes, I am aware of setter injection, but that breaks object immutability, so let's not go there). Also, many objects require complex initialization logic. Using provider methods (or custom Provider classes) as a default choice keeps you from a temptation to stick factory code inside the constructor, and thus greatly reduces domain object coupling.

## Story 2: Open/Closed Principle for Modules

I think the Injection story was pretty straightforward. Now let's talk a bit about modules and collections. If you've been using Guice, you are likely familiar with `Multibinder` and `MapBinder` that allow us to declare injectable maps and collections. What does it really give us? Let's consider an example. Say we have an imaginary `Command` interface, and also an imaginary `CommandExecutor` that looks up a command by name and then executes it:

Let's define a few commands and write a provider method for our executor:
    
    
          Map<String, Command> commands = new HashMap<>();
    
    
          commands.put("a", ca);
    
    
          return commandName -> commands.get(commandName).exec();

This code will work. There's one problem with it though. The module that defines `CommandExecutor` will need to know all the commands upfront. This violates the [open/closed principle](https://en.wikipedia.org/wiki/Open/closed_principle), or in simpler terms, it does not allow us to create a reusable module with `CommandExecutor`, deferring command definitions to app-specific downstream modules. Changing this code to use `[MapBinder](https://google.github.io/guice/api-docs/latest/javadoc/index.html?com/google/inject/multibindings/MapBinder.html)` to collect commands cleanly solves the reusability problem:
    
    
          return name -> commandMap.get(name).exec();

Here, we replaced a hardcoded map with an injectable map that is initially empty. Also we created a static `contributeCommands` method that gives other modules a hint on how our reusable module can be _extended_. So downstream modules can add any number of commands that will all be available to the application.

This all sounds simple, but it is a very important design pattern. It turns our DI environment into a powerful modularity engine. Common algorithms can be "bound" in generic reusable modules, but the actual set of objects they operate upon is composed by all collaborating modules present in the app. "contribute*" methods comprise custom Module-level APIs, often the only thing we need to know about any given Module.

## Conclusion

This concludes Part 1 of my Guice stories. It is not a substitute for the [Guice documentation](https://github.com/google/guice/wiki), but it will hopefully answer some practical questions and will get you over the learning curve faster. More stories will follow shortly.

Have something to say? Leave a comment or [follow me](https://twitter.com/andrus_a) on Twitter.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
