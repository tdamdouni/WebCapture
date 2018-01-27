# Code Reuse Is Not a Good First Class Goal

_Captured: 2017-11-09 at 20:10 from [dzone.com](https://dzone.com/articles/code-reuse-is-not-a-good-first-class-goal?edition=334857&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-09)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Wait, wait, wait. Put down the pitchforks and listen for a minute. You're probably thinking that I'm about to tout the "virtues" of copy/paste programming or something. But I assure you I'm not going to do that. Instead, I'm going to speak to a similar but subtly different topic: code reuse as a first-class goal.

If you've read _[The Pragmatic Programmer](https://www.amazon.com/Pragmatic-Programmer-Journeyman-Master/dp/020161622X)_, you know about [the DRY principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). You'll also know that the underlying evil comes from the duplication of knowledge in your system. This creates inconsistencies and maintenance headaches. So, since you duplicate code at your peril, isn't code reuse a good thing? Isn't it the opposite of code duplication?

No, not exactly. You can write "hello world" without any duplication. But you can also write it without reusing it or anything in it.

### Code Reuse as a First-Class Goal

So what, then, do I mean when I talk about code reuse as a first-class goal? I'm talking about a philosophy that I see frequently in my consulting, especially in the enterprise.

The idea seems to come from a deep fear of rework and waste. If we think of the history of the corporation, the Industrial Revolution saw an explosion in manufacturing driven by global efficiency. The world scrambled to make things cheaper and faster, and waste or rework in the process impeded that.

Today and in our line of work, we don't manufacture widgets. Instead, we produce software. But we still seem to have this atavistic terror that someone, somewhere, might already have written a data access layer component that you're about to write. And you writing it would be a _waste_.

In response to this fear, organizations come up with plans that can get fairly elaborate. They create "[centers of excellence](https://en.wikipedia.org/wiki/Center_of_excellence)" that monitor teams for code reuse opportunities, looking to stamp out waste. Or they create sophisticated code sharing platforms and internal app stores. Whatever the details, they devote significant organizational resources to avoiding this waste.

And that's actually great, in some respects. I mean, you don't want to waste time reinventing wheels by writing your own source control tools and logging frameworks. But things go sideways when the goal becomes not one of avoiding reinvented wheels but instead one of seeing how much of your own code you can reuse.

Let's take a look at some of the problems that you see when organizations really get on the "code reuse" horse.

### The Immediate Complexity Problem

When you have what I'll call a culture of reuse, you start to notice the way people approach it at a granular level. Developers start to view _everything_ they do as a target for reuse.

> Alright, I'm getting hello world going for this new ASP MVC app. But wait a minute! We write a hello world every time we start on a new technology. What if I wrote a technology-agnostic, UML-driven hello world framework that...

Okay, that's a little extreme. But hopefully, it illustrates the point. This is the sort of mentality that takes over in a shop that really prides itself on code reuse. The developers start to imagine that every bit of code they ever happen to write could become a library - nay, a standalone app - nay, a first-class piece of code to be put on GitHub or sold for profit. And this happens at the expense of solving real, actual, immediate problems.

The results can be subtle. You might see extra interfaces that don't seem necessary or [heavily partitioned codebases](https://www.ndepend.com/Res/PDF/Partitioning_NET_Assemblies_NDepend.pdf). Or, commonly, you'll see a _lot_ of logic pulled into inheritance schemes. "We've got this awesome abstracted framework for writing unit tests. Just inherit from these six classes and you can do your whole test arrange, act, assert with one magic string each!"

This kind of thing develops a lot when teams view the epitome of software development as minimizing future keystrokes. The main problem is that you make your codebase a lot more complex and abstract under the premise that, eventually, it will pay off. Maybe it will and maybe it won't, but in either case, you get a lot more upfront complexity.

### Trading Rework for Useless Work

Having extra complexity in your codebase is obviously problematic in and of itself. But think about how you're spending your time.

Instead of creating a hello world application or just writing some unit tests, you create a hello world _framework _and a unit test _framework_. This generalization has made your code more complex, but it's also sucked up a bunch of your time. After all, you're essentially productizing part of your implementation rather than just, well, implementing.

And here's a sequence of steps that usually follow when you build such a thing:

  * You spend extra time building it, and then you try to convince everyone how great it is.
  * In spite of your best efforts, nobody cares.
  * You _force_ them to use it (or get management to force them), convinced that they'll come around.
  * They don't really come around to agreeing, but they use it anyway and you wind up with a lot of maintenance requests.
  * The organization expends a lot of time maintaining this "product" until, eventually, someone realizes that it's never going to be used elsewhere and pulls the plug.

Often, by the end, you're executing an act of mercy. Nobody wants to use the thing, and, it turns out, the different places where you _thought_ reuse would be seamless turned out all to be a little different. So you've responded by building this thing that winds up reusing very little in practice, needing excessive configuration for each individual case.

I see this cycle over and over, and it's hardly the stuff that dreams are made of. This is what happens when you speculatively assume that others will be able to use the fruits of your labor. And cultures that promote code reuse as a first-class goal encourage and reward that speculation.

### Management Gets the Wrong Idea

I've cited two pitfalls to the pursuit of code reuse run amok: codebase complexity and wasted effort. In light of the fact that both of these translate into straightforward fashion to bad business outcomes, you'd think that management and "the business in general" would hate this. Right?

Well, no, not at all. In fact, management _loves_ this idea. Do you know why? Because of what it looks like in their heads. Mind you, it looks much different to them than it does to you.

To non-technical management, code reuse is the same thing as reusing a dish towel. "Well, that's not _actually _ the best metaphor because - " you start, but they're done listening. You've written a customer admin screen, and you practice code reuse, don't you? Well, that means that nobody will ever need to revisit this screen, nor will it ever take any effort to write a similar screen in any other application.

It's ridiculous to think that you spend any time on the dish towel when you do dishes, right? You bought it and now there it is, ready for reuse with every load of dishes. Same with the customer admin screen. Because, just like a dish towel, it's a fungible, simple, and tangible commodity. Right?

You'll protest this, and management will have simple objections and fixes. Ugh, fine, reuse isn't that simple. Just copy and paste the old one and make the changes. How long could that possibly take? And what do you mean "modify it to work with the new application," anyway? I thought you were building things you could reuse!

### Forget About Code Reuse and Focus on Avoiding Duplication

When I encouraged you to put down the pitchfork in the beginning, I talked about the subtle difference between avoiding duplication and pursuing code reuse. I'm now going to revisit that.

Avoiding duplication is a critically important goal in software development, often saving you from outsized technical debt. But avoiding speculative complexity and abstraction actually has the same risk profile. You need to walk a fine line in the middle.

I've heard talk of the "rule of three" for abstractions. Write some code, and then if you need something similar, write it again, living for the moment with the potential duplication. Then, if you need it a third time, it's time to create a library and reuse some code. In general, I find this to be excellent philosophical guidance.

Code reuse is not a worthwhile goal. Avoiding duplication is a worthwhile goal. Avoiding waste is a worthwhile goal. And you do both of these things by looking out for and eliminating repetition of your labor and of functionality in code. So write the code you need and keep doing that, right up to the point that you start repetitively solving the same problem. Then refactor that solution out into a commonplace and refer to it. When you do this, you're not reusing _code_ \- you're reusing valuable functionality.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
