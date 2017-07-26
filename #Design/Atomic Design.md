# Atomic Design

_Captured: 2015-11-25 at 14:24 from [bradfrost.com](http://bradfrost.com/blog/post/atomic-web-design/)_

> We're not designing pages, we're designing systems of components.--[Stephen Hay](http://bradfrost.com/blog/mobile/bdconf-stephen-hay-presents-responsive-design-workflow/)

As the craft of Web design continues to evolve, we're recognizing the need to develop thoughtful design systems, rather than creating simple collections of web pages.

A lot has been said about creating [design systems](http://24ways.org/2012/design-systems/), and much of it focuses on establishing foundations for color, typography, grids, texture and the like. This type of thinking is certainly important, but I'm slightly less interested in these aspects of design because ultimately they are and will always be subjective. Lately I've been more interested in what our interfaces are comprised of and how we can construct design systems in a more methodical way.

In searching for inspiration and parallels, I kept coming back to chemistry. The thought is that all matter (whether solid, liquid, gas, simple, complex, etc) is comprised of atoms. Those atomic units bond together to form molecules, which in turn combine into more complex organisms to ultimately create all matter in our universe.

Similarly, interfaces are made up of smaller components. This means we can break entire interfaces down into fundamental building blocks and work up from there. That's the basic gist of atomic design.

![Periodic Table of the Elements](http://bradfrost.com/wp-content/uploads/2012/11/Screen-Shot-2012-11-13-at-5.15.05-PM.png)

> _Josh Duck's HTML Periodic Table gives a great breakdown of web designers' atomic elements._

## What is Atomic Design

Atomic design is methodology for creating design systems. There are five distinct levels in atomic design:

  1. [Molecules](http://bradfrost.com/blog/post/atomic-web-design/)
  2. [Organisms](http://bradfrost.com/blog/post/atomic-web-design/)
![The progression of atomic design: atoms to molecules to organiams to templates to pages](http://bradfrost.com/wp-content/uploads/2013/06/atomic-design.png)

> _Let's explore each stage in more detail._

### Atoms

Atoms are the basic building blocks of matter. Applied to web interfaces, atoms are our HTML tags, such as a form label, an input or a button.

![Atoms](http://bradfrost.com/wp-content/uploads/2013/06/atoms.jpg)

Atoms can also include more abstract elements like color palettes, fonts and even more invisible aspects of an interface like animations.

Like atoms in nature they're fairly abstract and often not terribly useful on their own. However, they're good as a reference in the context of a pattern library as you can see all your global styles laid out at a glance.

### Molecules

Things start getting more interesting and tangible when we start combining atoms together. Molecules are groups of atoms bonded together and are the smallest fundamental units of a compound. These molecules take on their own properties and serve as the backbone of our design systems.

For example, a form label, input or button aren't too useful by themselves, but combine them together as a form and now they can actually do something together.

![molecule](http://bradfrost.com/wp-content/uploads/2013/06/molecule.jpg)

Building up to molecules from atoms encourages a "do one thing and do it well" mentality. While molecules can be complex, as a rule of thumb they are relatively simple combinations of atoms built for reuse.

### Organisms

Molecules give us some building blocks to work with, and we can now combine them together to form organisms. Organisms are groups of molecules joined together to form a relatively complex, distinct section of an interface.

![organism](http://bradfrost.com/wp-content/uploads/2013/06/organism2.jpg)

![organism-examples](http://bradfrost.com/wp-content/uploads/2013/06/organism-examples.jpg)

We're starting to get increasingly concrete. A client might not be terribly interested in the molecules of a design system, but with organisms we can see the final interface beginning to take shape. Dan Mall (who I'm working with on several projects) uses [element collages](http://danielmall.com/articles/rif-element-collages/), which articulate ideas for a few key organisms to facilitate client conversations and shape the visual direction (all without having to construct full comps).

Organisms can consist of similar and/or different molecule types. For example, a masthead organism might consist of diverse components like a logo, primary navigation, search form, and list of social media channels. But a "product grid" organism might consist of the same molecule (possibly containing a product image, product title and price) repeated over and over again.

Building up from molecules to organisms encourages creating standalone, portable, reusable components.

### Templates

At the template stage, we break our chemistry analogy to get into language that makes more sense to our clients and our final output. Templates consist mostly of groups of organisms stitched together to form pages. It's here where we start to see the design coming together and start seeing things like layout in action.

![template](http://bradfrost.com/wp-content/uploads/2013/06/template1.jpg)

Templates are very concrete and provide context to all these relatively abstract molecules and organisms. Templates are also where clients start seeing the final design in place. In my experience working with this methodology, templates begin their life as HTML wireframes, but over time increase fidelity to ultimately become the final deliverable. Bearded Studio in Pittsburgh follow [a similar process](http://alistapart.com/article/responsive-comping-obtaining-signoff-with-mockups), where designs start [grayscale and layout-less](http://aafh-css.heroku.com/wireframes-no-mq) but [slowly](http://aafh-css.heroku.com/wireframes) [increase](http://aafh-css.heroku.com/v1) [fidelity](http://aafh-css.heroku.com/v2) until the [final design](http://aafh-css.heroku.com/v5) is in place.

### Pages

Pages are specific instances of templates. Here, placeholder content is replaced with real representative content to give an accurate depiction of what a user will ultimately see.

![page](http://bradfrost.com/wp-content/uploads/2013/06/page1.jpg)

Pages are the highest level of fidelity and because they're the most tangible, it's typically where most people in the process spend most of their time and what most reviews revolve around.

The page stage is essential as it's where we test the effectiveness of the design system. Viewing everything in context allows us to loop back to modify our molecules, organisms, and templates to better address the real context of the design.

Pages are also the place to test variations in templates. For example, you might want to articulate what a headline containing 40 characters looks like, but also demonstrate what 340 characters looks like. What does it look like when a user has one item in their shopping cart versus 10 items with a discount code applied? Again, these specific instances influence how we loop back through and construct our system.

## Why Atomic Design

In a lot of ways, this is how we've been doing things all along, even if we haven't been consciously thinking about it in this specific way.

Atomic design provides a clear methodology for crafting design systems. Clients and team members are able to better appreciate the concept of design systems by actually seeing the steps laid out in front of them.

Atomic design gives us the ability to traverse from abstract to concrete. Because of this, we can create systems that promote consistency and scalability while simultaneously showing things in their final context. And by assembling rather than deconstructing, we're crafting a system right out of the gate instead of cherry picking patterns after the fact.

## Pattern Lab

In order to apply this methodology in my work, I (along with the help of the great [Dave Olsen](http://dmolsen.com/)) created a tool called [Pattern Lab](http://patternlab.bradfrostweb.com) to actually create these atomic design systems. I'll cover Pattern Lab in detail later, but feel free to [check it out on Github](https://github.com/bradfrost/patternlab).

## Further Reading

  * So Andy Clarke has been setting the stage for these types of conversations for a long while now. In fact, he wrote a chapter for _[Smashing Book 3](https://shop.smashingmagazine.com/smashing-book-3.html)_ called "Becoming Fabulously Flexible: Designing Atoms and Elements." I had no idea that existed, so how about that! I highly encourage you to check that out. I also highly encourage you to take a look at his tool called [Rock Hammer](http://malarkey.github.io/Rock-Hammer/), which is a great way to [construct a pattern library](http://stuffandnonsense.co.uk/blog/about/rock-hammer-a-curated-responsive-project-library) utilizing many of these principles.
  * [Web Components: A Tectonic Shift for Web Development](http://www.youtube.com/watch?v=fqULJBBEVQE) - Web Components seem to dovetail really nicely into the concept of atomic design, and watching this video will show why web components
  * [Modularity](http://www.w3.org/DesignIssues/Modularity.html) Tim Berners-Lee discusses how modularity as an important design principle for the Web.
  * [Responsive Deliverables](http://daverupert.com/2013/04/responsive-deliverables/) by Dave Rupert talks about the idea of constructing "Tiny Bootstraps, for Every Client"

And here's the video and slides from my talk on the subject at [Beyond Tellerrand](http://2013.beyondtellerrand.com/) in Germany.

[Brad Frost - Atomic Design - beyond tellerrand 2013](http://vimeo.com/67476280) from [beyond tellerrand](http://vimeo.com/beyondtellerrand) on [Vimeo](http://vimeo.com). 

I'm really excited to dive in deeper and develop more tools and thoughts around these concepts.
