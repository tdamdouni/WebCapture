# The Language of Modular Design

_Captured: 2015-12-01 at 14:19 from [alistapart.com](http://alistapart.com/article/language-of-modular-design)_

![](http://alistapart.com/d/_made/d/ALA_426_Modular-Design_960_440_81.jpg) [Issue № 426](http://alistapart.com/issue/426)

As many of us move away from designing pages toward designing [systems](http://24ways.org/2012/design-systems/), one concept keeps cropping up: modularity. We often hear about the benefits of a modular approach; modules are scalable, replaceable, reusable, easy to test, quick to put together--"They're just like LEGO!"

Modularity might appear to be a simple concept at first, but making it work for your team demands significant effort and commitment.

The biggest challenges around modularity are all the decisions that need to be reached: when to reuse a module and when to design a new one, how to make modules distinct enough, how to combine them, how to avoid duplications with the modules other designers and teams create, and so on. When modularizing an existing design or building a new one, it's not always clear where to begin.

## Start with language

Language is fundamental to collaboration. In her book [How to Make Sense of Any Mess](http://abbytheia.com/makesense/), Abby Covert says that the biggest obstacle teams face is the lack of a shared language. To help establish that shared language, she suggests that we discuss, vet, and document our [ontological decisions](http://www.slideshare.net/AbbyCovert/lessons-from-an-ontology-nerd) in the form of "controlled vocabularies."

In short, we should start with language, not interfaces.

For about a year now, our team at [FutureLearn](http://futurelearn.com), an open education platform, has been experimenting with a modular approach. I'd like to share a few ways we have tried to hone a shared language to help our team transition into modular design.

### Build a pattern library as a team

One of our first experiments with modularity was an attempt to redesign our homepage. A visual designer created modular slices, and we then held a workshop where we tried to organize the modules into comps. That's what we thought (perhaps naively) a "modular design process" would look like.

![Photograph of the team at FutureLearn organizing modules into comps.](http://alistapart.com/d/426/kholmatova_01.jpg)

> _One of our first experiments with modularity._

We ended up with three designs that eventually became fully functioning prototypes. But even though it was a useful exercise, the result we came up with wasn't truly modular:

  * Modules weren't clearly defined.
  * They didn't have clear functions; the differences between them were often merely aesthetic.
  * We didn't standardize and name them.
  * We didn't put a lot of thought into how they would be reused.

Ultimately, we decided not to use the resulting designs. These experiments were useful in propelling us into a modular mindset, but the defining step toward thinking modularly was going through the process of [building a pattern library](https://about.futurelearn.com/blog/pattern-library/) as a team, which took several months (and is still in progress).

The [atomic design methodology](http://bradfrost.com/blog/post/atomic-web-design/) pioneered by [Brad Frost](http://twitter.com/brad_frost) served as our foundation. This is when we started looking closely at the UI, taking the interface apart, conducting [inventories](http://bradfrost.com/blog/post/interface-inventory/), and defining the core elements and patterns that we used to build new pages.

Once we had a library, we were better prepared to think about design in terms of distinct reusable components. Until then--even after all of our experiments--we were still thinking in pages.

### Name things collaboratively, based on their high-level function

Once you lay the foundation, it's important to build on it by evolving the language as a team. An important part of that is naming the things you create.

Imagine you have a simple component whose function is to persuade people to take a specific online course. What would you call it?

![Screenshot of a module promoting an online course in cyber security.](http://alistapart.com/d/426/kholmatova_02.jpg)

> _UI component promoting an online course on FutureLearn._

The name depends on the component's function and how and where it appears in the interface. Some people, for example, might call it "image header" or "course promo."

James Britton, a well-known British educator, explains in [Language and Learning](https://www.goodreads.com/book/show/846917.Language_And_Learning) that by conferring names on objects, we engage in a "process of bringing [them] into existence," just like children who use language to "call into existence, to draw out of nothingness," the world around them. Similarly, if an object in the interface doesn't have a name--a name that makes sense to your team, and is known and used by people on your team--then it doesn't exist as a concrete, actionable module to work with.

Once you name an object, you shape its future. For example, if you give it a presentational name, its future will be limited, because it will be confined by its style. A functional name [might work better](http://seesparkbox.com/foundry/naming_css_stuff_is_really_hard). But functional names require more thought and are harder to arrive at, because function can be relative. For example, we almost called the component above "course poster" because it had an image of the course in the background and its function was to promote the course. It wasn't a bad name (it was quite functional, in fact), but it was also limiting.

Around the same time, for another project, a different designer introduced a component that looked (apart from minor variations in layout and typography) quite similar to our "course poster."

![Screenshot of a module inviting learners to take part in a discussion on brain activity.](http://alistapart.com/d/426/kholmatova_03.jpg)

> _UI component inviting learners to take part in a discussion._

The function of the new component was to invite people to take part in a discussion. So the first thought that came to mind was to call it "discussion." No one made a connection with "course poster" at first, because its name limited it to one specific function--promoting courses--and the function of "discussion" had little to do with it.

If we had given those components the names we initially thought of ("course poster" and "discussion"), we would have ended up with two named modules that were almost identical but non-reusable. Such oversights can lead to duplications and inconsistencies--which undermine modularity.

Although their functions may appear different at first, if you look at multiple uses of these components in context, or even imagine potential use cases, it's easier to see that they both do analogous things: they serve as attention-seeking slices. They command the core calls to action on those pages. In other words: their high-level function is to focus users' attention on the most important action.

![Screenshots of multiple billboard components in use.](http://alistapart.com/d/426/kholmatova_04.jpg)

> _A billboard component in use._

In the end, we created a single component called a "billboard." Billboards are not restricted by their position on the page, or by their content, or by their appearance. They can appear either with an image as the background or as part of the content. What matters is the high-level function, and that this high-level function is understood in the same way by different people on the team.

![Screenshot of a billboard component with an image of a hamburger inserted between the headline and the call to action.](http://alistapart.com/d/426/kholmatova_05.jpg)

> _Example of a billboard component with an image as part of the content._

In the process of naming an element, you work out the function as a group and reach an agreement. It's not so much about giving something a great name (although, of course, that's an ideal to aspire to), but _agreeing_ on the name. That determines how the element will be used and helps to ensure that it's used consistently by everyone.

### Make design language part of everyday culture

Naming things this way may take longer, at least initially, because it doesn't yet feel habitual. It requires additional effort and commitment from the whole team to make the process more familiar.

One way to make conversations about language happen is to create a physical space for them in the office.

![A photograph of two walls papered in printouts of modules and naming discussions.](http://alistapart.com/d/426/kholmatova_06.jpg)

> _A space in our office where language conversations often take place._

High-level functions are easier to define if you have the whole UI printed out and intelligible at a glance. It's also a lot easier to spot any duplications and inconsistencies that way.

[Slack](https://slack.com/) or other chat clients are also a [viable way](https://source.opennews.org/en-US/articles/remote-control-mandy-brown-vox-product/) to have these discussions. For example, it can help to post new elements you've just introduced, or existing ones that you suspect are inconsistent or potential duplicates, and then try to work out their function and find a suitable name. When thinking of names, it helps to have a common point of reference; our team often borrows terms from other industries, such as publishing or architecture, to give us ideas.

![Screenshot from a Slack discussion about potential names, such as 'bracket' or 'triglyph,' for a module with three content chunks.](http://alistapart.com/d/426/kholmatova_07.jpg)

> _A typical naming discussion on Slack._

Keeping design language alive by making it part of our day-to-day conversations, whether in-person or remote, plays a key role in maintaining modularity within our team.

### Define CSS architecture at the design stage

Needless to say, reaching consensus can be difficult. For example, we may disagree on whether we should reuse an existing module, customize it for a specific context, or create a new component.

[Several articles](http://philipwalton.com/articles/extending-styles/) have been written about styling UI components based on context. But Harry Roberts [has suggested](http://csswizardry.com/2015/06/contextual-styling-ui-components-nesting-and-implementation-detail/) that "having to change the cosmetics of a component in a certain context is a Design Smell"--a sign that your design is failing. How do you prevent this from happening?

What helps us is trying to standardize elements at the design stage, before building them--in other words, starting with design language. This means that developers need to understand why things are designed in a certain way, and designers need to know how the modules are built so that they can make tweaks without having to create a different version of the module.

Before writing the CSS, it's useful for designers and developers to understand the purpose of every element they create. They might start by asking lots of questions: "Will this module always be full width? Why? Will it always include those buttons? Is the typography likely to change? Is the image background critical to the design? Are the horizontal rules part of the [molecule](http://bradfrost.com/blog/post/atomic-web-design/#molecules)?"

Answering these questions helps to ensure that components follow through on design intent. For example, you might choose to specify some styles at the [atomic level](http://bradfrost.com/blog/post/atomic-web-design/#atoms), instead of at the [organism](http://bradfrost.com/blog/post/atomic-web-design/#organisms) level, to make it easier to change those properties without changing the module itself.

### Involve users in the design process

Another critical aspect in establishing a shared understanding is involving people from different disciplines, as well as users, in the design process from the outset. When brainstorming and sketching together, we can't help but talk about the design elements, so we inevitably make ontological decisions that help to strengthen and evolve the design language.

Getting to the testing stage early is important, even if modules are presented as simple paper cards. Testing with ideas on cards is very different from our usual process, where we have a list of tasks and scenarios that we walk users through. Here, participants can pick up, move around, discuss, and scribble on the cards, actively becoming part of the design process. This gives us a chance to test our language choices and make sure that the functions we've defined make sense to our users.

![Three photographs of users reacting to large paper printouts of modules.](http://alistapart.com/d/426/kholmatova_08.jpg)

> _User testing and participatory design with learners._

## Takeaways

A well-established language foundation is a powerful tool that allows teams to synthesize their efforts around implementing modular design. But the way a shared design language evolves is a piecemeal, gradual, and organic process. Every person on the team plays a role in making it more coherent. Going through the process of building a pattern library as a team is an effective way to establish a language foundation. Using a solid methodology, like [atomic design](http://bradfrost.com/blog/post/atomic-web-design/), can speed up the process.

Naming things together is a useful habit for your team to develop, because in the process of trying to give something a name that makes sense, you work out its function and, most importantly, reach consensus. The agreed-upon name determines how the element will be built and encourages consistent usage across the team. As Abby Coverts [writes](http://abbytheia.com/makesense/), "If you don't get agreement up front, prepare for more work later."

Make an effort to refer to the elements by the name you agreed on--no matter how strange this might sound in everyday conversations. It takes more effort initially to call something a "whisper box" (yes, we have an element called "whisper box") rather than "that thing with the lines and an icon in the middle." But until you start referring to an element by its proper name, it doesn't exist in your modular system as a solid, actionable block. Every time you use the name you agreed on, you strengthen the element you call on and evolve your design language.

Put your language to the test outside of your team by using it throughout the company, with other teams, and with users. It's always interesting to see what sticks--it's a real kick when someone outside the product team starts using the name, too.

Finally, remember that no language (aside from a few [exceptions](https://en.wikipedia.org/wiki/Language_isolate#List_of_language_isolates_by_continent)) exists in isolation. By evolving and strengthening your design language, you have an opportunity to contribute to the larger language of the web, and to help make it more consistent and coherent for everyone.
