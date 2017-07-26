# Java Method Overriding and Visibility [Snippet]

_Captured: 2017-02-15 at 19:49 from [dzone.com](https://dzone.com/articles/java-method-overriding-and-visibility?edition=269881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-15)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

This post is about a little test I set up to get my head around one aspect of method overriding in Java. A method in a superclass can call either another superclass method or a subclass method, depending on the visibility of the methods involved.

These are the demo classes:

`new SuperClass().a()` returns "superclass". `new SubClass().a()` returns "subclasssubclass".

If we change the visibility of method c() to private, however:

`new SuperClass().a()` returns "superclass". `new SubClass().a()` returns "superclasssuperclass".

In other words, superclass method b() will call the subclass implementation of c() if it is visible, or the superclass implementation if it is not.

Of course, if we then overrride b() in the subclass as well, things change again. Then we will see `new SubClass().a()` returns "subclasssubclass" no matter whether c() is public or private.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
