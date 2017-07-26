# Guice Stories ( Part 2)

_Captured: 2017-05-25 at 10:23 from [dzone.com](https://dzone.com/articles/guice-storiespart-2?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

For those of you who missed out, [Part 1](https://dzone.com/articles/guice-stories-part-1) of our Guice Stories series focused on Bootique and Guice's importance to it, especially for dependency injection. Let's continue on the journey with more Google Guice stories.

## Story 3: Filling Maps and Collections

Previously, we saw the examples of adding objects to `MapBinder`. Let's dwell on this for a moment. Here, I will use `[Multibinder](https://google.github.io/guice/api-docs/latest/javadoc/index.html?com/google/inject/multibindings/Multibinder.html)` for a change (remember, it produces an injectable `Set<SomeType>`), but the discussion applies to `MapBinder` just as well. What can we put in these DI-managed collections? If the objects in the Set are trivial to create and do not rely on any dependencies, we can add them as instances:

Though most objects (like our commands from the previous story) do require assembly and/or dependencies . So one option is to add them by type (just like we did with commands):

Intuitively, it is clear what happens here (an instance of `MySubType` is created and loaded into `Set<MyType>`). What's important to understand is that _adding to collections is a form of injection_. I.e. `MySubtype.class` is a shortcut for a "key" to lookup a DI binding. So while it may appear that we are telling Guice to "create an instance of `MySubtype.class`", in fact we are asking to "find an injectable object of this type, regardless of how it was created". What are we to do with this subtle knowledge? For one thing we can customize `MySubType` assembly code via a dedicated provider method. E.g.:

Another common scenario -- filling collection with multiple instances of the same type that differ only in their generic parameter. E.g. consider the following class:

Say we want to build a `Set<MyGenericType>`. We can't use the approach above. Due to [Java type erasure](https://docs.oracle.com/javase/tutorial/java/generics/erasure.html) we can't obtain Class objects that correspond specifically to `MyGenericType<String>` or `MyGenericType<Integer>`. The most commonly used trick to work around this problem is to create an anonymous inner class that mirrors the generics signature of the desired type. Such class can be used as a binding key. In Guice there is a superclass for it called `TypeLiteral`:

Notice that we only need a proper `TypeLiteral` when adding an object to a collection. Generic types of the provider methods are resolved by Guice automatically.

## Story 4: Going in Circles

A common problem that all Guice (or more generally -- DI) users will run into sooner or later is dependency cycles. E.g. class A depends on class B, B depends on C, C depends on A. Can a DI container still create all these objects for us?

In most cases, the answer is "yes". Guice will figure out how to correctly resolve a cycle and you won't even know you had a potential problem. But there are cases when it won't. Consider this example using constructor injection:

When trying to access an instance of A, you will get a scary error that starts like this:

The same issue would have happened with provider methods. But not with field injection! For all its downsides discussed above, field injection would allow Guice to handle dependency cycles with no user interference.

Now let's look at the exception. It hints that we won't have to resort to field injection. Instead, we can replace direct dependencies on classes with dependencies on interfaces. Then Guice would be able to create a proxy placeholder for the interface object, deferring resolution of the actual object until later. This solution is clean and injection of interfaces may even improve our overall design.

There's also one more way to break the cycle -- injecting Guice `Provider` instead of the instance of a dependency. Rewriting class C to take a `Provider<A>` solves the problem just as well:
    
    
       public C(Provider<A> aProvider) {

The trade-off is a newly acquired hard dependency on Guice API that we tried to avoid so hard in the previous stories. To keep things clean, you may replace Guice's `Provider` with Java's `Supplier` and use the provider method to convert an injectable provider into a supplier. I am leaving this as an exercise to the reader.

Referencing dependencies via Providers (or Suppliers) may help us beyond just breaking the cycles. Another thing it does is _deferring initialization of dependencies_, which comes handy when optimizing various conditional execution flows. E.g. consider an app that, depending on the passed command-line flags, either prints a help message or runs a database operation. It would be highly inconvenient to eagerly connect to the database if all we need is to print a help message. Injecting a provider solves this problem.

## Conclusion

This concludes the second part of the Guice Stories. I hope someone finds it useful. I have other story ideas as well. For example, I've been researching lately how to best use Guice with functional Java code and some patterns are starting to emerge. So, hopefully, I will get around to continue this series. Feel free to suggest your own ideas and useful Guice patterns.

[Follow me](https://twitter.com/andrus_a) on Twitter.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
