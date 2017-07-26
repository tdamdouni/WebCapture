# Real Objects vs. Data Containers

_Captured: 2017-06-13 at 23:04 from [dzone.com](https://dzone.com/articles/oop-real-objects-vs-data-containers?edition=303098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-13)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

After more than three years of working as backend (and mobile) programmer, mostly in the Java Virtual Machine ecosystem, I have realized that no one of those procedural MVC/MVP/MVVM patterns has made me feel comfortable when implementing new features or big changes in a project. Also, ER-ending classes (Controller, Manager, Helper, etc.), which are well-accepted and used in many frameworks, don't help with that either: they will get bigger and bigger, and you will have to segregate them without any logical criteria. And when that happens, you're screwed. Maintainability becomes really hard.

In the last few months, I have been heavily influenced by [Yegor Bugayenko](http://www.yegor256.com/) and what he claims is "pure" object-oriented programming. Instead of treating objects as simple (and silly) data containers/data structures, we should give them the power and trust them. Convert them into real objects.

Can you see any difference between this Java code:

And this C code:

Not at all. Because there is none. However, we write objects like above and are convinced we are object-oriented developers. But we aren't. We must think of objects as something more than simple in-memory data structures exposing its state to everybody. Objects should wrap its real-life representation.

Let's say we need to write a class `File` (in Java) with a method, `content()`, that returns its content in a byte array. A first implementation could be something like this:

And we would use it this way:
    
    
    File confFile = new File(path, fs.getFileContent(path));

Done.

To be honest, I think this implementation is a mess. Don't you?

If we change the content of file _/tmp/conf.xml, _the_ configFile _object becomes inconsistent. The `File` class is not representing a real file, but a bunch of bytes. It has been reduced to a data container. A C _struct. _It can't be considered an object at all.

This is a nice implementation for the same class:

And we use it this way:

Much better, right? Now, _configFile _is a real object. We have converted `File`type in an interface. This way, we can have more implementations like `RemoteFile`, if needed.

You may think that this implementation is not efficient because each time we call the `content()` method, a disk read is performed. It may be slow, depending on the system and the application requirements. You are right. So now, _object composition_ and the _decorator design pattern_ come into action.

We are going to create a class, `CachedFile`, that wraps a `File` and caches its content, so just one disk read will be performed:
    
    
            if (this.cached == null) {
    
    
                this.cached = origin.content(); //real disk read

(This is a very naive cache implementation. Also, you must never use `null`. I did it just for the example.)

And we use it this way:

It looks great for me!

What if I tell you that this approach can be applied to database objects, too?

Let's go back to the `User` example. A real, stored in-database `User` would look like this:

Now, a User is not just a bunch of data. Its state is not being exposed. It is a real object. Again, we can "decorate" it with a cache or whatever we want for throughput optimization.

If you liked it this approach of OOP, I strongly recommend you to read [Yegor's](http://www.yegor256.com/) posts and his book [Elegant Objects](https://www.amazon.co.uk/Elegant-Objects-1-Yegor-Bugayenko/dp/1519166915/ref=sr_1_1?ie=UTF8&qid=1493851410&sr=8-1&keywords=elegant+objects+volume+1).

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
