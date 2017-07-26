# A Software Developer's Guide to Maintaining Code

_Captured: 2017-02-19 at 00:08 from [dzone.com](https://dzone.com/articles/a-software-developers-guide-to-maintaining-code?edition=271895&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-18)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

When you first think about becoming a software developer, you probably have dreams of creating exciting new features, playing with new technologies, and writing some really cool and interesting code.

What you probably don't think about is working on a 10-year-old, crufty application written by some guy who left the company a long time ago, fixing the bugs he left behind.

The truth of the matter is that you'll spend much more time over the course of your software development career maintaining code than you will writing new code. That's how life is. Just one of those things.

This fact doesn't mean, though, that you'll only be working on maintaining old VB6 applications written decades ago. In fact, probably a large amount of the code you'll be maintaining is your own.

So, it's probably a good idea if you learn two things.

First, you'll need to know how to properly maintain code so that it doesn't get worse and worse over time until it finally falls apart. Second, you'll need to learn how to write good code that is easy to maintain, so that developers who later have to maintain your code don't track you down, come to your house, and kill you in your sleep.

In this article, we are going to talk about why learning how to maintain code and write maintainable code is so important, and I'll give you some practical advice on how to do both of those things.

Sound good?

## A Majority of Your Career Will Be Spent Maintaining Code

![Image title](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/02/Maintaining-Code-768x432.png)

I've already mentioned this, but it's worth mentioning again because it's so true: In one form or another, you are going to be maintaining code.

New software gets created all the time, but every new software application is expected to have some sort of lifespan that is hopefully longer than the time it took to create it.

This means that there will always be more old software out there than new software -- unless we have a ridiculously high influx of new software and a bunch of old software dies off at the same time, but that is very unlikely to happen.

That old software that is out there will constantly need to be improved and maintained. Customers will find bugs that need to be fixed. New features will need to be added or existing features will need to be modified. Production software is like a living, breathing organism, always growing and changing or slowly dying.

Why am I telling you this? Do I just want to dash your hopes against the walls? No. I want you to have realistic expectations of what you will be doing in your career as a software developer.

Oftentimes, eager, well-meaning hiring managers can paint a rosy picture of a job, telling you that you'll be working on designing and coding a brand new system from scratch using the latest technologies.

While some of your job might be doing this, more often than not, a majority of that job -- no matter how good it sounds -- will involve maintaining an existing system. Again, it's just the way life works.

Does this mean you can never get a job where you can completely write a new system from scratch? No. It definitely happens, but don't expect it all the time. Even if you do, expect that at some point in time, you or someone else will have to maintain that code. That's all.

## Great Developers Write Maintainable Code

![Image title](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/02/Depositphotos_123749090_s-2015-1.jpg)

Now that you have your expectations properly set, I'm going to try and inspire you to write "the best darn maintainable code you can," because by gosh, it's just a swell thing to do.

One incontrovertible fact I have found during my many years of working as a software developer and working with software developers is that great developers write highly maintainable code. In fact, I would say that the sole criteria I judge a programmer on is how maintainable their code is.

This might seem silly. You might think I'm making this up just to make my point in this chapter -- but I'm telling you, it's true. Here's why.

Great developers know that the majority of the life of any code they write will be spent in the maintenance phase. Great developers know that the most valuable code they write is [code that lasts a long time](https://simpleprogrammer.com/2010/04/17/when-doing-the-right-thing-is-wrong/) and doesn't have to be scrapped and rewritten. Rather than being clever and as fast or efficient as possible, great developers optimize for maintainability.

They write good, clean code that can be easily understood, modified, and maintained. They create flexible designs that are loosely coupled, so that if one thing changes in the system, it doesn't affect every other component of the system. They take extra care to make sure what they do is well documented and as self-explanatory as possible. They've spent enough time looking at someone else's code--or their own--and trying to maintain it that they know the best code they can write is the code that is the most maintainable.

## The Boy Scout Rule

One secret to being great at maintaining code is the Boy Scout Rule.

This rule originates from the Boy Scouts of America who emphasize a simple rule for camping: "Leave the campground cleaner than you found it."

This is a great rule to apply to multiple areas of your life, but it's especially useful in software development. Leave the code better than you found it. It's really that simple. When you are working on some code, perhaps fixing a bug or adding a new feature, try to leave that code in a slightly better state than it was when you found it.

It might mean writing an extra unit test to make the code a little more robust for the next developer who comes along and has to change something in it. It might mean renaming some variables in the code to make the meaning more clear. It might mean grouping some functionality into a method or procedure to reduce some redundancy in the code or to make it easier to understand. It might even involve refactoring a large chunk of the code to implement a cleaner, more simple design.

As long as you are following this rule, the code will gradually get better over time -- or at least the rate of entropy will decline severely. This basic rule is the most simple secret for maintaining an existing codebase.

## Readability Is of Utmost Importance

![Image title](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/02/Readability-1024x576.png)

[One of the most important factors influencing the maintainability of code is its readability](https://simpleprogrammer.com/2013/04/14/what-makes-code-readable-not-what-you-think/). The more readable the code is, the easier it is to maintain that code. The more cryptic and difficult to understand code is, the more difficult it is to maintain.

It's that plain and simple.

Too many developers try to write succinct and clever code. While being succinct can be valuable, being terse and clever is an absolute recipe for disaster. Why? Because code is [read more than it is written](https://www.youtube.com/watch?v=RLxHNRY6-bU).

Every time a programmer is trying to understand some workflow passing through your code so they, in turn, can add a new feature, modify an existing one, or troubleshoot a bug, they are going to need to understand what your code is doing.

The easier it is for them to understand, the easier it will be for them to make the correct changes to the system and the less time it will take. If the code is obscure and difficult to understand, it's going to take extra time whenever another developer -- or even yourself -- has to examine and try to understand that code.

It is also highly likely that someone will misunderstand the code, and may then make an error when changing the code or another part of the system which uses that code, further degrading the system.

The fact of the matter is that readable code is just easier to maintain, period. Therefore, when writing code that is meant to be maintained, strive for readability above all else.

## Refactor Code to Make It Better

We've already talked about the Boy Scout Rule, but let's dive a little deeper into what it means to "make code better." How can you make code better?

A whole book could be written on the subject of refactoring -- [and several have been](http://amzn.to/2c2FgYt) -- but in this section, I'm going to introduce you to the basics, and you can practice and learn on your own.

Refactoring is essentially improving the design of existing code. To me, refactoring means making existing code more readable without changing its functionality.

The "without changing its functionality" part is pretty important because you can't go around leaving code better than you found it if you are also changing the functionality. You could be introducing bugs and making the code worse (not that you can't ever change functionality when you improve code, but that isn't the point of refactoring).

The point of refactoring is to take some existing code and make it even better. Better could -- and really, always should -- mean more readable and maintainable.

However, it could also mean that you've reduced the total lines of code by eliminating some duplication or organizing it in a different way. It could mean that you've improved the overall architecture to make it more flexible and robust against further changes.

There are many ways to refactor code, but the big rule in refactoring is to not change functionality but to make the code better. Refactoring and unit testing go hand-in-hand since it's difficult to know that you haven't changed the functionality of code if you have no way to test it.

It's a good idea to have some unit tests in place before you do refactoring, especially if it's a non-trivial change. There are also some modern refactoring tools which can assist you and can pretty much guarantee that the refactorings won't change the functionality of the code.

Most modern IDEs have some of these tools baked in. Think of it as rearranging a mathematics equation without altering their meaning. You can always be sure that 4x = 8 is the same as 2x = 4 or x = 2. You don't have to prove it.

## Automation Is Essential

![Image title](https://spzone-simpleprogrammer.netdna-ssl.com/wp-content/uploads/2017/02/Depositphotos_86227536_s-2015-1.jpg)

It's really difficult to maintain software on which you have to manually build and manually run tests to make sure nothing breaks.

The faster you can make changes and test changes, the better the safety net you'll have, which will protect you from adding new bugs and errors to an existing codebase.

This is why automation is essential to increasing the maintainability of a software project.

Having an automated build, a continuous integration system and automated tests make it incredibly simple to make changes to the code and quickly find out if you broke anything.

This quick cycle of feedback gives developers more confidence in their changes and also allows them to refactor the code, making it better without fear.

## If You Write Comments, Write Good Ones

[I'm not a huge fan of writing comments in code](https://simpleprogrammer.com/2015/04/13/why-comments-are-stupid-a-real-example/). Yes, I know this is heresy, but I'd rather write clear, expressive code that is self-explanatory than write cryptic code that can only be understood when reading through the comments -- which, by the way, have hopefully been maintained along with the code.

I'd rather see you write clean, readable code than add a bunch of comments to the code which usually end up outdated, but, if you do write comments, make sure they are really good. Make sure the comments clearly explain something that is non-obvious and needs to be explained.

Cryptic comments are sometimes as bad as or worse than cryptic code because you can at least figure out what cryptic code does. You can't really figure out what a cryptic comment might have meant.

Along with comments in the code, make your commit messages as clear and helpful as possible as well. Clear messages also contribute to the maintainability of a code base because commit messages give us a history of not just what happened to code over time, but why.

That why can be crucial when trying to understand some code or change that wasn't apparent, especially when it involves fixing a tricky bug.

## Resources for Learning to Write Maintainable Code

Maintaining code is tricky. It involves quite a few skills from writing clean code to refactoring to design and even infrastructure concerns like DevOps and automation.

I've decided to include a list of some valuable resources which can help you become better at both writing maintainable code and maintaining existing code that you didn't write.

  * **_[Clean Code_ by Robert Martin](http://amzn.to/2c2E0F1). **I've mentioned this book a few times, but it's one of the best books about writing clean, readable code, and it also includes great information about design and refactoring for maintainability.

  * **_[Code Complete_ by Steve McConnell](http://amzn.to/2ch6jgD). **Again, I've mentioned this book a few times already, but it's another great book about writing good, maintainable code. You'll find this book goes into some of the low-level, structural details of writing good, readable code. Read it.

Note: Combined, _Clean Code_ and _Code Complete_ will give you a solid base and understanding of what makes good, clean, readable code and how to write and structure your code, so I highly recommend reading both books.

  * **_[Working Effectively With Legacy Code_ by Michael Feathers](http://amzn.to/2cmhvKl).** This is a classic book about maintaining existing code. It dives pretty deep down into the nitty-gritty of legacy systems and how to deal with code that someone else wrote. Every software developer should read this book since every software developer is likely to spend a majority of their time working with legacy code.

  * **_[Refactoring_ by Martin Fowler](http://amzn.to/2c2FgYt). **Another classic book that all software developers should read. This book goes over all the major refactorings you can do to restructure code without changing its functionality.

Well, there's the gist of it.

Just remember the Boy Scout Rule, and you'll do ok. Oh, also, don't worry: you'll get plenty of practice maintaining code over the course of your software development career.

Good luck.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
