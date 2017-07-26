# Elements of Helpful Code Documentation

_Captured: 2017-04-19 at 22:06 from [dzone.com](https://dzone.com/articles/elements-of-helpful-code-documentation?oid=twitter&utm_content=buffer8b5e7&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

If you spend enough years writing software, sooner or later, your chosen vocation will force you into reverse engineering. Some weird API method with an inscrutable name will stymie you. And you'll have to plug in random inputs and examine the outputs to figure out what it does.

Clearly, this wastes your time. Even if you enjoy the detective work, you can't argue that an employer or client would view this as efficient. Library and API code should not require you to launch a mystery investigation to determine what it does.

![](http://www.daedtech.com/wp-content/uploads/2014/10/Sherlock.jpg)

Instead, such code should come with appropriate documentation. This documentation should move your focus from wondering what the code does to contemplating how best to leverage it. It should make your life easier.

But what constitutes appropriate documentation? What particular characteristics does it have? In this post, I'd like to lay out some elements of helpful code documentation.

## Elements of Style

Before moving on to what the documentation should contain, I will speak first about its stylistic properties. After all, poorly written documentation can tank understanding, even if it theoretically contains everything it should. If you're going to write it, make it good.

Now don't get me wrong -- I'm not suggesting you should invest enough time to make it a literary masterpiece. Instead, focus on three primary characteristics of good writing: clarity, correctness, and precision. You want to make sure that readers understand exactly what you're talking about. And, obviously, you cannot get anything wrong.

The importance of this goes beyond just the particular method in question. It affects your entire credibility with your userbase. If you confuse them with ambiguity or, worse, get something wrong, they will start to mistrust you. The documentation becomes useless to them and your reputation suffers.

## Examples

Once you've gotten your house in order with stylistic concerns in the documentation, you can decide on what to include. First up, I cannot overstate the importance of including examples.

Whether you find yourself documenting a class, a method, a web service call, or anything else, _provide examples_. Show the users the code in action and let them apply their pattern matching and deduction skills. In case you hadn't noticed, programmers tend to have these in spades.

Empathize with the users of your code. When you find yourself reading manuals and documentation, don't you look for examples? Don't you prefer to grab them and tweak them to suit your current situation? So do the readers of your documentation. Oblige them.

## Conditions

Next up, I'll talk about the general consideration of "conditions." By this, I mean three basic types of conditions: [preconditions, postconditions, and invariants](https://www.cs.umd.edu/class/fall2002/cmsc214/Projects/P1/proj1.contract.html).

Let me define these in broad terms so that you understand what I mean. Respectively, preconditions, postconditions, and invariants are things that must be true before your code executes, things that must be true after it executes, and things that must remain true throughout.

Documenting this information for your users saves them from the misery of trial and error. If you leave this out, they may have to discover for themselves that the method won't accept a null parameter or that it never returns a positive number. Spare them that trial and error experimentation and make this clear. By telling them explicitly, you help them determine up front whether this code suits their purpose or not.

Moving out from core principles a bit, let's talk about some important meta-information. People don't always peruse your documentation in "lookup" mode, wanting help with a code element whose name they already know. Instead, sometimes they will 'surf' the documentation, brainstorming the best way to tackle a problem.

For instance, imagine that you want to design some behavior around a collection type. Familiar with List, you look that up, but then maybe you poke around to see what inherits from the same base or implements the same interface. By doing this, you hope to find the perfect collection type to suit your needs.

Make this sort of thing easy on readers of your documentation by offering a concept of "related" elements. Listing OOP classes in the same hierarchy represents just one example of what you might do. You can also list all the elements with a similar behavior or a similar name. You will have to determine for yourself what related elements make sense based on context. Just make sure to include them, though.

## Pitfalls and Gotchas

Last, I'll mention an oft-overlooked property of documentation. Most commonly, you might see this when looking at the documentation for some API call. Often, it takes the form of "exceptions thrown" or "possible error codes."

But I'd like to generalize further here to "pitfalls and gotchas." Listing out error codes and exceptions is great because it lets users know what to expect when things go off the rails. But these aren't the only ways that things can go wrong, nor are they the only things of which users should be aware.

Take care to list anything out here that might violate the [principle of least surprise](https://en.wikipedia.org/wiki/Principle_of_least_astonishment) or that could trip people up. This might include things like, "common ways users misuse this method" or "if you get output X, check that you set Y correctly." You can usually populate this section pretty easily whenever a user struggles with the documentation as-is.

Wherever you get the pitfalls, just be sure to include them. Believe it or not, this kind of detail can make the difference between adequate and outstanding documentation. Few things impress users as much as you anticipating their questions and needs.

## Documentation Won't Fix Bad Code

In closing, I would like to offer a thought that returns to the code itself. Writing good documentation is critically important for anyone whose code will be consumed by others -- especially those selling their code. But it all goes for naught should you write bad or buggy code, or should your API present a mess to your users.

Thus, I encourage you to apply the same scrutiny to the usability of your API that I have just encouraged you to do for your documentation. Look to ensure that you offer crisp, clear abstractions. Name code elements appropriately. Avoid surprises to your users.

Over the last decade or so, organizations like Apple have moved us away from hefty user manuals in favor of "discoverable" interfaces. Apply the same principle to your code. I tell you this not to excuse you from the documentation, but to help you make your documentation count. When your clean API serves as part of your documentation, you will write less of it, and what you do write will have a higher value to readers.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
