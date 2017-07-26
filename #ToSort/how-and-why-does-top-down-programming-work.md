# How and Why Does Top-Down Programming Work?

_Captured: 2017-05-13 at 08:55 from [dzone.com](https://dzone.com/articles/how-does-top-down-programming-work?edition=298091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-12)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Top-down programming might be out of vogue, but that doesn't mean it doesn't have its merits. In fact, I would argue that for some people top down programming might indeed be the best way to program. Not for everybody, mind you, but certainly for some people.

What's more, it might also be a better solution for some kinds of problems than for others. And that is ultimately what programming is about, solving problems.

## In a Nutshell

Top-down programming starts at the top and then works its way down. Or, as Wikibooks puts it, "A **top**-**down** approach (also known as stepwise design) is essentially the breaking** down** of a system to gain insight into the sub-systems that make it up. In a **top**-**down** approach, an overview of the system is formulated, specifying but not detailing any first-level subsystems."

So you start at the most abstract level, by defining the problem, and from there add more details. It's a bit like starting with an outline and then filling things in as you go until you have a story.

## From Abstract to Program

So, let's say that you want to create a program that plays checkers, but you don't know where to start. Well, when you're working with top-down systems you do.

You just write: `PlayCheckers( );`

Of course, that doesn't mean anything yet, as you don't have a 'play checkers' procedure. But you have defined the problem and can now move to the next level down.

Here you might write:

Now, obviously this still does not give you an actually working game, but it has defined the problem down still further. Yes, none of these operations will tell the computer what to do yet, but that's okay. What matters is that you know what to do. What the computer has to do will come later.

Yes, it might take a while before you get to the actual code that the computer can interpret and understand, but when you get there you have a very accurate framework that you can interpret and you can understand - and ultimately, which is more important?

Well, obviously having code that the computer can understand, because otherwise it's not working problem, but you get the idea. You can't change the code that you can't understand, while code the computer can't yet understand is just a few steps away from a fully functioning program.

## Divide and Conquer

What's more, this kind of setup allows you to easily break up a project that seems insurmountable into something that has manageable pieces which have clearly defined parts. Don't underestimate the power of this technique!

You see, I've found that defining the project is often one of the most fundamental steps you need to do if you want to make sure you don't end up staring at the wall and procrastinating. It really doesn't matter if we're talking about programming or writing your dissertation (if you don't want to use a dissertation writing service, anyway).

The thing is, with programming, it has the extra advantage that it takes something that can often be arcane and quite finicky and turn it into something that has logical well-defined steps that even a person starting out in the field can understand.

Now that has something to be said for it, right?

## Now for the Downsides

This kind of programming does have its downsides. Of course, it does. If it was perfect, it wouldn't have gone out of vogue, would it? So, for example, you might drill down from the top level to a level where you find a step you simply don't know how to implement.

Alternatively, you might do a bad job in dividing up your plan. Maybe you didn't think about it correctly and you divide a task into two in a way that it shouldn't be divided, for example. Then, when you try to execute that lower level step, you find it to not be possible because you made a higher-level problem.

Now, if you discover that late in the programming game, you could be in for a lot of trouble. But then, sloppy thinking can always get you into trouble.

One of the bigger problems is that this requires a very hierarchical way of structuring your code. Information flows top down and bottoms up throughout the hierarchy, without a real guide as to how that information should be organized. This is where object-oriented programming has the advantage.

I have also heard people complain that this kind of programming can be kind of rigid, with it being hard to rewrite certain parts of the code. I don't exactly buy this argument. Because if you do this type of coding correctly, then the only communication between the different parts of the program are through defined parameters.

## And the Big One

What is a problem that you'll find with top-down programming is that you'll find yourself naturally following certain grooves that you've become used to following in the past. That makes sense, because if you solved a problem in some way in the past, then naturally you're going to define and solve it in a similar way this time around.

Of course, the problem with that is that you might not see other solutions to the problems that are out there, which might be far more efficient and innovative. This is where other forms of programming can be superior to top-down programming.

## Last Words

That said, there are still plenty of types of programming for which a top-down approach offers you a clearer idea and a better framework to get your code written down.

That's why programmers who prefer to think abstractly about a problem or who can't think of a solution in some way using different forms of programming should definitely give top-down programming a try.

It might be just the slightly different way to look at things they need to get past a problem that otherwise might have been unsolvable. Even if it isn't, it's always a good idea to try new things. You never know what you'll learn by doing so.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

Opinions expressed by DZone contributors are their own.
