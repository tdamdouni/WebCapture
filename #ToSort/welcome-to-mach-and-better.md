# Welcome to MACH and BETTER

_Captured: 2017-06-01 at 15:29 from [medium.com](https://medium.com/nbc-news-digital/welcome-to-the-new-mach-and-better-64fded55f73e)_

## Building a design system and publishing platform for digital verticals and a major news site -- from the outside in.

This is the story of how we created three new digital verticals, **[MACH**](https://www.nbcnews.com/mach), **[BETTER**](https://www.nbcnews.com/better) and the soon-to-be-launched **THINK**, while also laying the foundation for a new multi-brand design system, performant and flexible publishing platform, as well as faster development processes all around. It's a journey from product ideation and validation all the way through to scalable design and development.

![](https://cdn-images-1.medium.com/max/800/1*kv7_4nMjJBaJRaCAWDbkzw.png)

> _MACH and BETTER front page content packages_

These sites are the result of several months of prototyping, iteration and scaling of everything from content to advertising to platform. MACH and BETTER originally launched as pop-up verticals to test audience and advertiser demand. After seeing the positive feedback, both internally and externally, we decided to begin the redesign process with these verticals. Eventually, we will extend the work we did with these three verticals to the entire NBC News Digital product suite. Here is how we did it…

#### Co-creation: Teaming up with an agency to supercharge internal teams

Although the Pop-up verticals were well received, it was clear that we'd already reached the limit of what we could achieve for these new brands on our old stack and design system. These new verticals needed to be more compelling. They needed more video, more visuals, more flexible content creation and more dynamic curation capabilities. They also needed better recirculation of content and consumption through the full network of sites, and more premium advertising offerings, including seamless integration of branded content.

![](https://cdn-images-1.medium.com/max/800/1*ap_kJXg9eyB3o0pOUkiIaA.png)

> _Our dedicated war room and design boards at Code & Theory_

While we are blessed with having key resources and skillsets for product, design and development in-house, we knew we needed additional help to achieve our goal of launching a full new design system, frontend framework and improved curation tools by our deadline -- in just 16 weeks. Instead of completely outsourcing the project, we decided to partner with the digital agency [Code & Theory](http://www.codeandtheory.com/) to co-create everything from ideation to design and code completion. Around one-third of the project's staff came from Code & Theory and two-thirds from NBC News. All key positions, from design to development to project management were paired. The goal was to build a sustainable product and process to ensure the long-term viability of what we create. Most agencies optimize for short-term delivery and single reveal. This can be at odds with a more iterative approach and ensuring that everyone inside the company can maintain and evolve what was built in the long run. By supercharging our own teams with experienced and fast-moving agency talent, we achieved the best of both worlds: fast ramp-up and release, while also ensuring long-term sustainability and iteration with our own teams.

#### Design system: a visual language and user experience that scales across all brands

The danger of creating new brands iteratively is a proliferation of visual elements, inconsistent user experiences, technical debt and poor long-term maintenance. NBC News already has three major brands (MSNBC, TODAY, NBCNews), all with their own visual language, user experience and content management. Adding even more would only further complicate things, and over time, this accrued design and tech debt means that everything will slow down and become inflexible. Launching new features becomes a painfully slow and cumbersome process that frustrates the newsroom, business stakeholders and users that traverse multiple parts of the sites with different UX. We needed to start over and rebuild the entire system.

Having been through a few major redesigns we learned the hard way that starting with the homepage or other highly visible portions of the site can doom the project from the outset. Instead, we chose to create a new design system 'from the outside in' -- by starting with the new verticals which had only been around for a couple of months and were a complete greenfield in terms of design and content strategy. Together with Code & Theory we went about selecting a new font family, color palette, image treatments, content packaging, motion language, iconography and overall layout system. Using the actual examples of MACH, BETTER and THINK for implementation but always designing with the full network of sites in mind, we built new fronts, components and content types.

![](https://cdn-images-1.medium.com/max/800/1*vNi5wt8sIBFOGVb0q_P8PQ.gif)

> _Key components of our new design system_

#### Our approach and key components of the new system

**Approach: design from the outside in.** Start where you have the most freedom and least risk. Release a portion, monitor success and address shortcomings before scaling to a larger portion of the network. Redesigns of existing destinations can be very disruptive to loyal users. It's best to start on the periphery, with smaller sections, or ideally entirely new sections, and carefully design your way towards the center.

![](https://cdn-images-1.medium.com/max/600/1*j6h_8Ivl_FRMo5z4C9pglg.gif)

**Logo system: stay on brand but evolve**. Everything we do is proudly carrying the Peacock. For the verticals we wanted to find a way to combine our heritage and point to something new. The single feather was used in the pop-ups already, to represent an individual part of a larger whole. Now we move the feather to the edge of the frame to make it more modern and angular, like the rest of the design.

![](https://cdn-images-1.medium.com/max/600/0*YVKjygWsmnW8e8tQ.)

**Colors: select more than a palette**. Figure out a way to use color combinations to differentiate each brand's identity, while maintaining coherence across the full family of brands. The color palette we chose gives us a lot of flexibility to expand the system to future verticals. We chose violet for MACH to represent an optimistic but unknown future, teal for BETTER to represent obtainable change, and burst for THINK to represents bold ideas. Further, we identified global colors shared across the network and a number of future color pairings (still secret!) that will help evolve existing and new brands yet to be invented.

![](https://cdn-images-1.medium.com/max/600/0*QfxY69DxrcVOuF4V.)

**Fonts: like with color, select font pairings that scale**. We optimized for readability with serif fonts (like articles) and boldness and clarity with sans-serif fonts (headlines, navigation). We're using Founders Grotesk Condensed for headlines, a sans-serif typeface that provides more space and legibility for news titles. Founders Grotesk Mono for timestamps, metadata, tags providing the smallest yet important data and information with scannability and knowledge of it's function immediately to the user. For our serif typeface, we chose Publico for it's headline typeset and text typeset.

![](https://cdn-images-1.medium.com/max/600/0*2W3_2UI_4xAXKlXn.)

**Packages: depart from rigidly structured page templates**. Instead, develop modular packages that can be placed on fronts and allow editors to create new page layouts on the fly. A front is just a container of modules, not a fixed page layout. All packages can be shared across all fronts and stacked as desired. This enables the creation of modular homepages and the ability to spool up new fronts in minutes instead of weeks, without the assistance of developers. Further, fronts are no longer static templates but rather containers of packages. These packages can be re-arranged by editors all the time, creating dynamic pages that adjust to storyflow as often as needed.

![](https://cdn-images-1.medium.com/max/600/0*_1Omis7M7R1MBr4V.)

**Images: create a coherent way of treating images everywhere**. Ensure both visual consistency and workflow efficiency. All our image crops are ratio based. Everything begins with a simple square. This means editors never have to worry about cropping fails and our pages scale easily across all breakpoints. It's like a magical Tetris!

![](https://cdn-images-1.medium.com/max/600/1*potJt_h_bp-PmAIahIiqLA.png)

**Video: remove all friction**. We built our own, blazing fast HTML5 video player and created bold video modules and canonical video pages that draw users into the experience. We reward content sampling (harder with video than with text) by giving users a 'grace' period that removes pre-roll ads if a user jumps around between clips frequently. On desktop, a pre-roll will only be played once every 60 seconds. This means users will not see a pre-roll as they jump from one video to another in a period of 60 seconds or less. On mobile and tablet, the preroll is only shown before the first when the filmstrip mode is launched (basically the canonical page on mobile). This means they can consume as much video as they like without any interruption as long as they stay in the filmstrip mode. And of course, no autoplay! All plays are user initiated by clicks or swipes.

From the outset it was clear that we didn't just want to ship a new product. We wanted to build the processes and tools that would allow us to accelerate how we create. This means moving to a more performant javascript framework, more flexible API layer, and faster releases processes. For additional technical leadership we brought in [Econify](http://www.econify.com/), a boutique engineering shop that has helped other publishers like Bloomberg, Vevo, and Vice improve their tech stack.

#### Frontend framework: the road to React via Ramen

React has become the javascript framework of choice for many digital publishers. And rightly so. It is light, performant and modular. However, migrating to a new codebase and retraining developers can be disruptive to an active project, so we took a half-step towards React and created 'Ramen', a mini framework to get us React ready.. That's right, we created our own mini javascript framework. It's a kind of 'React Light' and will help us prepare for a full migration to React later this year. Ramen is highly componentized allowing us to create truly modular homepages, focus on performance, modularly organize our assets, and ease the on-boarding of new developers; all while increasing stability and minimizing the chance of regressions. More on that in another post!

#### GraphQL layer: further decoupling the stack for more flexibility and speed

Although the NBC News stack is already mostly decoupled into distinct services and repositories (we use Drupal, but just as a headless data entry tool), our backend services still required rigid 1:1 data contracts with the clients. This means a feature change often requires changes from several teams to connect frontend client and backend services. Aside from the development overhead, this 1:1 structure easily breaks downstream clients like mobile apps that are daisy-chained off the same data contracts but rarely on the same development cycles.

We decided to move our backend service from HAL to GraphQL to decouple our application data contracts. This increased stability amongst our downstream apps and decreased time to market by reusing a single service. The verticals were the first consumers of our GraphQL instance. We will roll it out to all clients throughout the rest of the year.

#### Towards continuous shipping: evolving DevOps to build and deploy fast and frequently

The verticals also allowed us to start revising our DevOps process to optimize for speed and agility.

First, we introduced tagged releases. By updating our system to force deployments via GitHub Tags, we've significantly decreased the likelihood of bugs in production while gaining the ability to easily roll back code to previously known stable points, quickly and with confidence.

Second, we've decreased the time it takes to get to staging, from a minimum of 3 hours down to a few minutes at most. This results in more frequent deployments, allowing us to deploy upwards of 30 to 40 times a day, if needed, dramatically decreasing the time it takes for new features to show up in production. Much of this was achieved through identical environments. By ensuring that every instance of our stack is identical to production (minus capacity), we've removed the need to support separate entry points for different environments such as Heroku and AWS. This eliminates the ability for a bug to creep up in production that does not exist in staging. Similarly, we now provide developers and QA the ability to spool up an on-demand instance of our stack with the code that exists in a PR. Devs and QA can test code before it gets merged in, dramatically increasing the stability of our master code base.

If you made it this far, thank you! We are only at the beginning of an exciting journey. Over the next nine months, we will redesign and rebuild every product and pixel at NBC News Digital. Our new design system and component-based platform will allow us to develop and release new features faster and deploy them across any of our sites. It makes ad and analytics integration easier and more comparable. It helps keep application of best practices for SEO consistent and greatly simplifies troubleshooting overall. Gone are the days of checking every template individually. Soon we will also start building a living style guide, taking our components from Sketch and Ramen, linking them to a dynamic module library that updates in realtime (more on that soon).

If you are deeply passionate about innovating in the publishing industry, and if you believe that there has never been a more important time to serve a broad audience with the best journalism and most compelling user experience, then check out [nbcnewsdigitaljobs.com](http://nbcnewsdigitaljobs.com) and come join us!

Thank you,

Moritz
