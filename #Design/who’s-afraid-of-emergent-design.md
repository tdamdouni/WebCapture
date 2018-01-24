# Who’s Afraid of Emergent Design?

_Captured: 2017-11-28 at 13:49 from [dzone.com](https://dzone.com/articles/whos-afraid-of-emergent-design?edition=338993&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-11-28)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

A hallmark of lightweight software development methods is the notion of _emergent design_. The idea is that the design of the solution will emerge little by little as we build up the code in small increments, typically using test-driven development with very short red-green-refactor cycles.

When it goes well, we avoid a number of problems. We won't create a comprehensive design and write a lot of code that only leads us down a rabbit hole that's hard to climb back out of. We won't get carried away with our natural creativity and over-engineer the thing way beyond what our customers want to pay for. We won't end up with a suboptimal architecture because we invested too much too soon in our initial design ideas.

It's a simple enough idea in principle. It really isn't difficult in practice, either; I can vouch for the fact it makes the work considerably less stressful and more enjoyable than the old ways of building applications.

And yet…

Have you ever tried to push the north poles of two magnets together? The magnets get close and then slide apart. Each time they slide apart, it's in a different direction than the time before.

When working with developers who are unaccustomed to emergent design, I sometimes get the same feeling. They seem to understand the concept, and they seem to be getting really close to doing it, and then it slips away from them.

Why so much difficulty? Well, as the saying goes, the devil is in the details.

### Where's the Safety Net?

If you've always worked from a comprehensive, detailed design specification, then starting to code with anything less than that is going to feel pretty uncomfortable. What if you forget something important? How can you be sure the design that emerges will be any good? Lacking detailed design specifications, how will you know whether a proposed code change will affect other parts of the solution?

It feels like you're crossing a half-frozen river by leaping from ice floe to ice floe. That design documentation was your safety net for changing the code. _Now,_ what are you supposed to do?

Actually, you _do_ have a safety net, and it's far more trustworthy than any design document. Remember that we use the technique known as test-driven development for emergent design. Those executable test cases accurately and fully describe the low-level behavior of every unit of code in the solution. They are always up-to-date with respect to the production code, however little or however much of it there is on any given day. Driving every new feature, every modification, and every bug-fix from tests gives you a high degree of protection from errors.

Nothing is foolproof, of course, and like anything else we do in our work, test-driven development is a learned skill that requires practice. But that's nothing new for you. After all, you weren't _born _knowing all the things you know how to do. You had to _learn_ them. _All_ of them. This is just one more thing. And it's easier than most of the other things you've learned about software development over the years.

See? I _told_ you it was less stressful!

### Just Enough Design Initially

Developers who are just beginning to learn emergent design often hold a certain misconception at first. They think "emergent design" means "no design at all." You just open up your favorite editor and start typing. That's not quite right.

There's an old mantra that (I think) came from the Feature Driven Development community years ago: Just Enough Design Initially (JEDI). To take an emergent approach to solution design, JEDI is our starting point. There's a lot of territory between _comprehensive, detailed up-front design,_ and _no design at all_. It's incumbent on us as professionals to be able to make judgments about where, in all that territory, we should begin any given project. It isn't always the same spot.

Well, if JEDI means different things in different situations, then how are we expected to learn to make judgments about it? The bad news is there are no hard-and-fast rules. The good news is there are no hard-and-fast rules. We get to use our intelligence, creativity, training, and experience, and we get to collaborate with other smart, creative people, rather than just coding to someone else's spec (See? I _told_ you it was more enjoyable!).

### Architectural Design or Application Design?

I find it useful to draw a distinction between architectural design and application design. Most of the time, when we write a new application we aren't simultaneously inventing the architecture that supports it. The architecture is like scaffolding on which applications can hang. Yet, many people think it's mandatory to begin each project by designing the architecture for the solution.

As long as our application is a _new instance of an existing type of thing_, we don't need to begin our work with an architectural design. There's already an architecture, if not several architectures, relevant to our new application. "Just enough" up-front design is probably not very much.

Sometimes, if we're lucky, we get to build an _entirely new type of thing_. There's no existing architecture on which to hang it. In this case, "just enough" up-front design amounts to more than in the first case…but you still might not do a comprehensive design up front, as there's value in emerging the architectural design, as well, once you get to a good starting point.

We aren't necessarily starting completely from scratch when we build an application. There may be reference architectures, design patterns, libraries, code generators, and other resources available to save us time and effort. You don't need to design an architecture to support a new web app. You can choose from Model 2 or MVC, Hierarchical, and Single-Page architectural patterns. You don't need to design a responsive web app from scratch; you can choose a web app framework that has responsive design built in already. You don't need to design an architecture for a mainframe batch process that grinds up sequential files all night. You already know it must comprise a subset of extract, sort/merge, edit, update, and report steps. These are well-known _types_ of things, and once you've seen an example or two, you never need to re-design one from whole cloth.

The basic advice here is: Don't reinvent the wheel.

### Your Past Experience Counts as Up-Front Design for Your Next Project

I don't recall where I first read or heard that saying. I didn't make it up, but I like it. Your new application isn't identical to any existing application. After all, if it _were_, then you wouldn't need to write it at all. But at the same time, the new application probably isn't so very different from other work you've done in the past.

Do you really need to re-draw all the design diagrams you drew on those past projects? I'll bet you don't. You're just checking a box on a checklist of tasks: "Draw design diagrams." I'll bet if you drew those diagrams, you'd never look at them again. After all, you didn't the last 25 times you drew them, now did you? Come on, 'fess up!

### Don't Do Anything Stupid on Purpose

That's another one of my favorite old sayings. It's been common among engineers for decades. Signs hang on the walls of labs bearing those inspiring words. All those software design principles folks like us are always jabbering about what can be derived from that single _ur_-principle: Don't do anything stupid on purpose.

Sometimes, when developers are first trying to apply the idea of emergent design, they very strictly follow the (intentionally)-incomplete and -lightweight specifications to the letter. That is, they _don't_ do anything that isn't explicitly specified.

And that violates the _ur_-principle. You _know_ your application has to handle exceptions gracefully. You _know_ it has to support logging. You _know_ it (probably) has to support internationalization, accessibility, and a host of other things that most or all applications have to do. Do you really need someone to write that stuff down for you every single time? You know the drill.

So, who's afraid of emergent design? Not you.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
