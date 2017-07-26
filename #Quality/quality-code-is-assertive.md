# Quality Code Is Assertive

_Captured: 2017-06-27 at 20:48 from [dzone.com](https://dzone.com/articles/quality-code-is-assertive?edition=305152&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-26)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

The "A" in CLEAN stands for assertive.

I don't hear a lot of people talking about it but I think it's an important code quality. We want the software we write to be assertive, to be in charge of its own state. We want objects to tell the world things rather than ask the world things. Why? Because this fundamentally supports object-oriented programming.

We need to think of objects as autonomous units that are in charge of themselves, responsible for their own state, and capable of managing themselves. This is really important in making the object-oriented paradigm work. When the responsibilities of an object get spread out among multiple objects in a system it's hard to understand what's going on in the code. It makes maintenance difficult because we'll have to touch several objects in a system. That usually means reading through a huge amount of code.

One way to think about assertiveness in code is to put all the behavior related to the data of an object with that object. Doing this makes the code more performant, makes it easier to test, makes it easier to understand, and makes the system more modular.

But sometimes, a process requires accessing data from more than one object. In this case, you may want to pick the object whose data it uses the most, or pick one for some other reason. It's just a rule of thumb: keep behavior with the data it consumes in order to keep the code assertive. That is, not constantly calling out to other code to access its state.

Assertive objects cannot be created in a vacuum. If all the other objects in a system are inquisitive then new objects will likely also be inquisitive. If a system is generally assertive, it should be rather straightforward to introduce other assertive objects. This is one of the other main benefits of having an assertive system. It's much more straightforward to extend the object model because assertive objects are autonomous. They are in charge of their own state so they're more easily migrated, extended, removed, or changed.

Assertive systems put the responsibilities of the system in the right places so that you can look at the object model and understand where a system's behavior is. It thinks about the objects on the system as actors carrying out their task and implementing features.

Assertive systems are straightforward to understand because the behaviors in a system are in the right place, making code easier to read and understand.

Note that assertive code is different than procedural code. Procedural code is also in charge but it's in charge of everything. Procedural programs take a global perspective. They are the hands of God coming down from on high, commanding the system to do their bidding. It's an easy to follow but somewhat unrealistic programming paradigm. It's easy to follow because we tend to think in a straightforward narrative way, but it's a bad programming paradigm because it doesn't scale well.

We've seen this time and time again in procedural programs. They're fine for small tasks or services but as soon as we start to scale them up and build enterprise systems, we find that those systems increase in complexity rather quickly, ending up in unmanageable states. This is why we went to the object-oriented paradigm in the first place in the early '90s.

Well, I went to the object-oriented paradigm in the early '90s. It might have taken the rest of the world a few years more. I've been on the leading edge of software development for about thirty years and although I've been doing object-oriented programming for over a quarter of a century, I keep finding deeper and deeper levels of understanding for how to build systems with objects.

As I learned to build more autonomous objects, the systems I have built are more flexible and more agile.

One way to tell when code is lacking in assertiveness is when an object makes excessive use of accessor methods in other objects. When objects call get and set methods on other objects they're trying to control the other object's state. If objects were people in the real world, this would be illegal. Even though it's the virtual world we should respect an object's autonomy.

That's really what assertiveness is: allowing objects to be objects. Who could argue with that?

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
