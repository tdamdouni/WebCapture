# Programming to an Interface: A Simple Explanation

_Captured: 2018-09-07 at 16:14 from [dzone.com](https://dzone.com/articles/programming-to-an-interface-a-simple-explanation?edition=391208&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-09-07)_

###  In this article, we'll be looking at what it really means to program to an interface and why developers should be doing it. 

[Automatic continuous monitoring](https://dzone.com/go?i=302521&u=https%3A%2F%2Fwww.instana.com%2Ftrial%2F%3Futm_campaign%3DDZone_DevOps_Zone%2520%26utm_source%3DPreRoll%26utm_medium%3Dfree_trial%2520%2520) keeps continuous deployment pipelines flowing smoothly and efficiently. [Try Instana APM](https://dzone.com/go?i=302521&u=https%3A%2F%2Fwww.instana.com%2Ftrial%2F%3Futm_campaign%3DDZone_DevOps_Zone%2520%26utm_source%3DPreRoll%26utm_medium%3Dfree_trial%2520%2520) to automatically monitor containers and microservices!

As an architect, you know that programming to an interface is good. It's what everyone should do.

But what does that mean? And why should _you_ do it?

Searching the Internet for answers might only cause more confusion. There, you'll find people arguing over what "programming to an interface" really means. And how everyone else is wrong about it. Yet everyone's definition sounds pretty much the same. But is supposedly different. Somehow.

Let's remove the confusion and break it down. In this post, we'll look at what it means to program to an interface and why you should do it.

## What's an Interface?

When I first googled this term, I didn't expect much controversy. I've used interfaces for years. We all have. What could be hard about them?

Many answers to interface questions point to examples using the interface keyword in C# or Java. The word interface is right there, so that must be what an interface is.

Then there's a bunch of people who take a different stand. So they argue the originators of the "programming to an interface" rule never meant it as [the interface concept in C#](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/interfaces/). It's an object-oriented concept, they say. And you're silly for thinking it has anything to do with the keyword.

But this group might be confused when functional programmers talk about the concept of interfaces, too.

In reality, they're all partly right.

### It's a Contract

To put it simply, an interface is a contract. This contract states the behavior of some component. It defines the interaction between components that use the interface. It also defines the interface itself.

Most importantly, it leaves out the part about _how_ the interaction is implemented.

### How to Spot It

So how can you identify an interface? Well, interfaces come in many forms. Sometimes the word interface is in the name to help you out, as with the user interface. Or the commonly used application program interfaces (APIs) and command-line interfaces (CLIs).

Other times, the name may omit the word interface, but still indicates a contract.

Let's look back at how the word "interface" is used in languages like C#. That interface _also_ helps define a contract. A contract between layers and components of applications.

So, good news! Our Java and C# interfaces are, in fact, interfaces. And the concept of interfaces also exists in other languages like JavaScript and Rust. They just might not use the word interface explicitly.

## Why Should I Use Interfaces?

OK, now you have a high-level understanding of interfaces. So what's the big deal? Why are these so important?

To quote from the [Gang of Four's design patterns](https://en.wikipedia.org/wiki/Design_Patterns) book, using interfaces means the following:

  1. "Clients remain unaware of the specific types of objects they use, as long as the objects adhere to the interface that clients expect."

  2. "Clients remain unaware of the classes that implement these objects. Clients only know about the abstract class(es) defining the interface."

Great! Super awesome. But what does this actually do for me?

### You'll Have Code That's Easier to Modify

Interfaces make your code less brittle. If implementations change, your code will still work -- as long as the interface doesn't change.

Let's consider a very simple C# example. Suppose I need to have a collection of objects. Right now I don't care too much about implementation. A collection is a collection. So I'm going to use a `List<T>` .

However, I don't want to commit to using a List<T> everywhere, so I use the ICollection interface instead, like this:

But designing around implementation results in brittle code. It has to change in many fun and unexpected ways any time some downstream implementation changes. Or when you need to switch to a different implementation altogether.

### You'll Provide a Contract for Others

When adding interfaces to your own code, it helps to define what sort of behavior you expect from them. A clear contract makes behavioral boundaries explicit.

But you have to be careful here. You might have knowledge of the implementation from reading or writing it yourself. But the classes that use that interface shouldn't rely on how things are done. Otherwise, you'll once again get strong coupling between your code and the collaborators' implementation.

## Where Should I Use Interfaces?

You may be saying, "Interfaces are great! Thanks! I'm going to use them everywhere. I'm a real architect now!"

Sadly, I'd have to come back with, "Whoa there, friend! That's not what you want to do."

For starters, avoid slapping as many interfaces as you can into your application. That won't suddenly make your code better. Other architects won't be singing your praises at their weekly bocce ball tournament. Yes, that's right. They have a secret bocce ball tournament. I guess you haven't been invited yet.

So where should you start?

Step one: Measure where you are. With NDepend, you can now see where you are between the zone of uselessness and the [zone of pain](https://blog.ndepend.com/abstractness-entering-zone-pain/). Find out where you are on the scale and the direction you want to go.

Next, use interfaces that are already available. As with our simple collection example above, there are many existing interfaces that define exactly what you want your code to do. Use them instead of concrete implementations.

Finally, look at your existing implementation. Decide what functionality could be improved with some explicit contracts. Are there services or domains with clear boundaries? Additionally, what boundaries do you want future developers of your app to respect?

You need a good balance when deciding what interfaces to use, how many, and at what abstraction level. With practice and the right tools to measure your progress, you'll be more confident with your architectural choices.

## What Could Go Wrong If I Don't Use Interfaces?

Sometimes you need to learn lessons more painfully. Maybe it's not enough for me to say that you should program to an interface. Sometimes, you may need to feel the pain yourself of not doing this. What's the worst that could happen?

Well, do you recall the days of laboriously writing different code for every popular web browser? There are still many applications that only work in particular browsers. That's an example where an entire industry said, "You know what? I don't care about interfaces and contracts. I'm not limited by standards! I'm going to do it my way."

And web developers for decades have paid the price.

Another example is [WinAPI](https://en.wikipedia.org/wiki/Windows_API), our old and trusty friend. In this case, people would take advantage of how the API was implemented to do some weird things. The result was that any Windows upgrade could potentially break a lot of applications that used WinAPI.

What Microsoft had to do was create a number of patches and hacky backward compatibility just to keep everything working. Could that be holding back better design and breakthroughs? Maybe.

On a smaller level, without interfaces, you lose a clear understanding of domain boundaries and expected behavior. You start seeing how changes to implementations in one part of the program ripple up toward seemingly unrelated parts.

## Is That All There Is to Know?

We've taken a look at what interfaces are and how they can be used. Are you done learning about this?

Of course not! This is only the beginning. The next steps are all on you.

Look at interfaces in your existing code and projects. Think about why they're there and what purpose they serve. Also look at APIs and CLIs you're familiar with. Consider the history of implementation changes to those interfaces and how they can affect developers.

Really take some time to think about the interfaces you see on a daily basis and look at the contract they provide. This is a great way to learn through others' successes and failures without having to write them all yourself.

Will you make the right choice every time? Probably not. But you'll learn. And your architectural skills will grow.

[Automatic real-time observability](https://dzone.com/go?i=302522&u=https%3A%2F%2Fwww.instana.com%2Fwebinars%2Fai-powered-apm-your-compass-for-the-ci-cd-journey%2F%3Futm_campaign%3DDZone_DevOps_Zone%26utm_source%3DPostRoll%26utm_medium%3DCI_CD_Journey_Webinar) is critical to getting the full benefit of CI/CD. [Hear @DevOpsDon](https://dzone.com/go?i=302522&u=https%3A%2F%2Fwww.instana.com%2Fwebinars%2Fai-powered-apm-your-compass-for-the-ci-cd-journey%2F%3Futm_campaign%3DDZone_DevOps_Zone%26utm_source%3DPostRoll%26utm_medium%3DCI_CD_Journey_Webinar) discuss how Franklin American Mortgage Company cut their new application deployment time from 6-12 months to 2 weeks with the help of [Instana APM](https://dzone.com/go?i=302522&u=https%3A%2F%2Fwww.instana.com%2Fwebinars%2Fai-powered-apm-your-compass-for-the-ci-cd-journey%2F%3Futm_campaign%3DDZone_DevOps_Zone%26utm_source%3DPostRoll%26utm_medium%3DCI_CD_Journey_Webinar).
