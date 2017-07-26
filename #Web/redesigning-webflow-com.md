# Redesigning Webflow.com

_Captured: 2017-01-23 at 09:30 from [medium.com](https://medium.com/webflow-design/redesigning-webflow-dot-com-part-1-c59a0cef01e#.91ef5cypn)_

## Part 1: Why redesign?

## Redesigning Webflow.com

![](https://cdn-images-1.medium.com/max/2000/1*9z2wm0buXOiWmRZrtcR-1w.png)

_This is part 1 of a three part series. Read __[part 2_](https://medium.com/webflow-design/redesigning-webflow-dot-com-part-2-9f655b38c95b#.kwr28oksw)_. (Part 3 forthcoming.)_

At the end of December 2016, the marketing and design teams here at [Webflow](https://webflow.com/) wrapped up a three-month redesign of our main website. And, yes: we built it all in Webflow 😎. This is the first of three posts about what our goals were, how we made it happen, and what challenges we faced along the way.

As _very_ active Webflow users, we thought it'd be interesting to share how we approached this project, including our perspectives on planning, goals, workflow, tools, and processes.

Then, as we discuss the last phase of our redesign -- actually building out the new site in Webflow -- we'll look at how we approached building a site of our scale in Webflow, techniques we used to make the process flow, and where we saw room for improvement in our own product.

### Part 1: Why redesign?

The first step in our redesign was deciding _what_ we wanted to say as a company, _why_ we needed to say it, and _how_ we wanted to present that message.

What was the goal of the redesign? Why did we want to invest the time and energy required to redo our website? What did we want to improve?

These were questions we'd all been thinking about for a long time (as designers and marketers, we_ all_ think about these things almost _all_ the time), so when we gathered the team together to discuss redesigning the website, there was _a lot_ to sort out.

For one, our product had evolved substantially since the last website redesign in late 2015. Since then, we'd introduced the CMS, expanded the CSS properties available in Webflow (including [flexbox](http://flexbox.webflow.com) in April 2016, and [CSS filters](https://webflow.com/blog/new-feature-css-filters) in May), started work on a [new CMS API](http://developers.webflow.com), started a [revamp](https://webflow.com/feature/interactions-v2) of our interactions and animations toolset, and developed a new set of hosting features.

![](https://cdn-images-1.medium.com/max/800/0*YaQZCRkHI-DQ3RHS.)

> _New features and updates to Webflow since our last redesign in 2015._

At the same time, our own thinking about the product had begun to shift as we talked with customers, observed and joined discussions in the Webflow community, and noticed the enthusiasm that more technical people began to show for our product. Considering all this, we knew there were things we could improve.

### Goals of the redesign

We had an extended series of discussions before doing any actual design work, and although these discussions carried on _throughout_ the redesign, we started by agreeing on a core set of principles for what the new site should do:

**1) Bring more focus to the UI and product.** Our then-current site abstracted the core product to focus on _what you could do with it_ -- to the point where people weren't understanding _how_ Webflow actually works.

From the conversations we had with both current and non-Webflow users, we confirmed our suspicions that most designers want to _see_ a product in action when they visit the website, and our old site simply didn't do this clearly enough.

**2) Differentiate us from consumer WYSIWYGs.** We wanted to move away from -- if not directly contradict -- the misleading association we've had with consumer WYSIWYGs like Squarespace, Wix, Weebly, etc., and make it clear that Webflow is a modern, professional, and technical tool.

This serves two purposes: one, it better sets expectations for site visitors, so they know what they're getting into with Webflow, and, two, improves the quality of leads coming through the site, as they're better prepared for some of the more technical aspects of Webflow.

**3) Embrace the technical.** On a similar note, while discussing our product, we wanted to cozy up more to the technical language of HTML, CSS, and JavaScript, since many of our most enthusiastic customers are already familiar and comfortable with this type of language.

**4) Create a more distinctive visual language.** To go along with our efforts to give Webflow more professional, technical spin, we wanted to introduce a new, sleeker visual language that would support that messaging.

At the same time, we wanted our new site to feature more visual creativity, using illustrations to help communicate some of the more complex aspects of our product.

**5) Let our customers speak for us.** We wanted to do a better job surfacing quotes and stories from our more recent, higher-profile customers in the design world.

We also wanted to sync the release of our new site with the launch of a revised pricing structure (and, of course, a new pricing page) and the release of several big features, including: SSL for all hosted sites, [per-page password protection](https://webflow.com/blog/new-feature-per-page-password-protection), and the public release of our [CMS API](http://developers.webflow.com/).

All of these components of last month's release warrant their own posts, and in due time, they will. But for now, we'll focus on the redesign of our core site, which included: the [home page](https://webflow.com), the [Designer page](https://webflow.com/designer), the [CMS page](https://webflow.com/cms), and a new page about [Webflow Hosting](https://webflow.com/hosting).

### Finding inspiration

As we considered the goals of the redesign, the stylistic direction we wanted to take, and the visual elements we wanted to emphasize on the new site, we looked to a number of companies that we felt were doing a good job "telling their story" on their website.

Here are some of the standouts:

#### Framer

Framer was one of the first sites we looked at that embraced the direction we were hoping to take with our new website. By scrolling through their website, you can quickly see what working with their tool _feels_ like, and they support these videos with thoughtful copy that expands upon the ideas and features hinted at in their visuals.

![](https://cdn-images-1.medium.com/max/800/1*y8jm0PO9KiSmD6NF7Hq17g.gif)

> _Framer's product videos were an early source of inspiration during the redesign._

#### Sketch

Sketch does a good job educating their visitors about the tool's features by showing them in context. This was a theme we noticed across many design-tool websites: designers want to _see_ the tool before they try it.

![](https://cdn-images-1.medium.com/max/800/0*L_a6T9SH6p1gjAVf.)

> _Sketch does a good job featuring their product in context -- a common thread we noticed across design tool websites._

#### Intercom

Intercom counterbalances the UI-heavy examples of Sketch and Framer with their playful and engaging illustrations, which inspired our design team to create our own visual language and iconography throughout the site. Of course, these illustrations don't replace product shots entirely -- their deeper product pages also feature clear, informative UI videos.

![](https://cdn-images-1.medium.com/max/800/0*lhj2f6Xo3IaGrt8t.)

> _Intercom balanced playful illustrations with informative product videos and screenshots._

### Doing the work

After interviewing users, doing our own research, and coming to consensus internally, the next step was scoping out what work needed to be done, and by whom. We broke the work down into four categories:

#### 1\. Recording product videos

We knew we wanted the new site to feature HTML5 videos of Webflow in action. We knew these videos needed to be visually appealing, but more importantly, they needed to communicate the Webflow's features and flexibility.

**Owner**: marketing, with support from design

#### 2\. Content, copywriting, and structure

We needed to support the visual story that these videos communicated with the written word. This encompassed not only what we wanted to say, and in what order, but also how we wanted to say it, what tone we would adopt, and what language we'd use to describe our product.

**Owner**: marketing, with indirect support from our community.

#### 3\. Brand and visual language work

With the new website, we had a chance to reconsider our visual language and style, which meant new iconography and illustration styles, a new font set, and a fresh color scheme.

**Owner**: design.

#### 4\. Building the site

Someone needed to build the site in Webflow, obviously.

**Owner**: design, with support from marketing.

Next week, in [part two of this series](https://medium.com/webflow-design/redesigning-webflow-dot-com-part-2-9f655b38c95b#.dmj45rwxp), we'll look at how we tackled this work, the tools we used along the way, and how we communicated as the design and content of the new website evolved.

Finally, in part three, we'll take a closer look at how we built the site in Webflow, discussing the design and workflow strategies we used while building the site, how we collaborated throughout the process, and where we saw room for improvement in our own product.

## Part 2: Content design and visual direction

_Captured: 2017-01-23 at 09:30 from [medium.com](https://medium.com/webflow-design/redesigning-webflow-dot-com-part-2-9f655b38c95b#.orqudt3u2)_

## Redesigning Webflow.com

_Co-authored by Barrett Johnson and __[Ryan Morrison_](https://medium.com/@ryryjmo)

![](https://cdn-images-1.medium.com/max/2000/1*MkQMWDwBZwTuxD5YyHl4Yw.png)

Last week, we looked at [why we decided to redesign Webflow.com](https://medium.com/webflow-design/redesigning-webflow-dot-com-part-1-c59a0cef01e#.ittbzmblu), how we approached it, and discussed our goals for the redesign.

This time, we'll take a closer look at the actual work of designing the site.

As we outlined at the end of last post, we'll discuss how marketing and design worked together on the videos, content, and design of the site before taking the final step and building everything in Webflow. Next week, Ryan will focus on how he approached building the site in Webflow and what he learned along the way.

### Phase 1: Recording the product videos

Because we knew that the product videos on the homepage would play a key role in "selling" Webflow, and that they would be among the more labor-intensive aspects of the redesign, we decided to work on these first.

> _A final product of one of the videos, showing Webflow CMS in action._

Once we had the videos in a presentable place, we could then work on filling out the copy and the layout alongside them, at which point we could present our first pass at the homepage redesign to the larger team for feedback and first impressions.

Once we had the homepage design far enough along, we'd expand on the points it introduced within the more detailed [Designer](https://webflow.com/designer), [CMS](https://webflow.com/cms), and [Hosting](http://webflow.com/hosting) pages.

But first, we had to answer a question: what should we feature in the videos?

This question had a couple parts to it. The obvious first half was: What _features or aspects of Webflow_ do we want to highlight in the videos? The second part was: What exactly are we going to be _building_ in the video?

We knew the videos needed to illustrate the core features of Webflow -- the things that make our product uniquely powerful. Among others, we considered these to be:

  * **The CSS and styling controls in the Designer**, which provides near-complete control over layout and styling in a completely visual interface
  * **The Webflow CMS**, which lets designers define their own content structure and display it via whatever layout and structure they have in mind
  * **Our interactions and animations toolset**, which give designers a completely visual way to bring CSS and Javascript style animations to their designs

A theme that kept cropping up in the team's initial discussions was how expressive designers can be with Webflow -- that "if you can design it, you can build it with Webflow" really is the heart of the matter.

So, we decided the videos should visually express the precision, power, and expressiveness that Webflow offers designers.

The second part of the initial question -- "What are we going to be _building_ in the video?" -- was one of the more fun parts of the process: now we had to "invent" a few fake websites to serve as example projects in the videos themselves.

In all, we created three dummy sites before settling on those you see on our current site.

![](https://cdn-images-1.medium.com/max/800/0*BaR5dQpNe89okUik.)

> _A "fake" music blog we built to show off the flexibility of the CMS._

Once Ryan designed and built the fake sites, I went in and used [ScreenFlow](http://www.telestream.net/screenflow/overview.htm) to record myself working in the Designer. I then edited these for presentation on the site, splicing clips, speeding some parts up, adding freeze frames where necessary, and so on.

![](https://cdn-images-1.medium.com/max/800/0*ibfUMH7y02n54Url.)

> _We used ScreenFlow to record and edit the videos._

In all, we cycled through 8 to 10 versions of each of the five videos featured on the site. Each version varied in terms of what we were building, how we were building it, and how the timing and clip splicing played out.

Once we had versions that we felt were strong enough to present to our larger team, we exported the videos as MP4s at 1440x900px, using [H.264 encoding](https://sidbala.com/h-264-is-magic/) at 1,200 kbits/sec to save space. In the end, the videos ranged in file size from 2.5 to 3.5 MB -- a compression result that, given the quality of the videos, we were happy with.

### Phase 2a: Content structure and copywriting

Once we had (nearly) final versions of the videos recorded, I (Barrett) threw screenshots of them into a Sketch file and made a first pass at the copywriting and content structure.

My goal was to create a simple wireframe of the content and layout I had in mind, which I could then hand off to Ryan for him to polish, using the new visual direction that he was developing in parallel (more on that below).

#### Why I didn't start copywriting in Google Docs

From the beginning, we knew this redesign was as much about _what_ we were saying as _how_ we were presenting it visually. So, when I sat down to wireframe the homepage, I realized that, for me, writing the copy in an isolated Google Doc would divorce the content from the visual story we were telling alongside it.

At the same time, the tools available were changing before our very eyes. The downside of copywriting in Sketch -- when compared to something like Google Docs, Notion, Dropbox Paper, or the many other collaborative writing tools available -- is the lack of native commenting, and for many, InVision bridges this gap.

With InVision, you can upload static mocks and comments on design, content, functionality -- whatever. And in the earlier stages of the process, we used InVision to do just that.

![](https://cdn-images-1.medium.com/max/1000/1*4UTs0xY-nJ21jnncH6Og4Q.png)

> _A screenshot from one of our earlier stage InVision projects._

But as we moved through the redesign process, we saw Figma launch its real-time collaboration feature in early October. This interested us, but it was the ability to directly comment on artboards that sold us.

For us, this unified the process of refining copy and design in parallel, since you can instantly make changes in response to comments, and there was no disconnect between the annotation and the corrections, as there is with InVision. Also helpful was the easy Sketch file import feature Figma offered.

![](https://cdn-images-1.medium.com/max/1000/0*vFjZMkGvVAfkKOnD.)

> _Figma's live annotation tools streamlined the copy editing and design refinement process, and let us comment on and compare versions side by side._

While I worked on the content, copywriting, and structure, Ryan worked on charting out a new visual and creative direction for our site, which I'll let him get into below.

### Phase 2b: Charting a new design direction

While Barrett worked on copywriting and content structure, I (Ryan) started exploring a new visual language that would help tell the story of what Webflow is now, and where we're going. In short, this meant devising a visual style and iconography that reflected how Webflow had evolved technically since the last design, as well as how we see it evolving in the future.

#### Picking the right fonts

Type offers designers a powerful tool to shape the feeling of a design. We were using Circular and Avenir in our old designs, and although I love both of those, the roundness of Circular didn't have the technical and professional vibe I was aiming for.

First, I searched far and wide for typeface candidates, and reached out to both my fellow designers at Webflow and my designer buddies, collecting all of my favorites. After many many iterations of possible type combinations and tweaks, I landed on a combination of Akkurat and Graphik with a little dash of Roboto Mono here and there.

![](https://cdn-images-1.medium.com/max/1000/1*itzQwXFhbOW5snyT7ZzwWg.png)

> _A look at the move from Circular and Avenir to Akkurat and Graphik._

After I locked in my typeface choices, I took some time to freshen up my knowledge of [best practices](https://spec.fm/specifics/type-scale), spacing recommendations, and [type scales](http://type-scale.com/). I spent about a day of tweaking the sizes, weights, line heights, letter spacing, and margins to achieve the desired levels of balance and contrast between all my headings, paragraphs, and other standard web type styles.

![](https://cdn-images-1.medium.com/max/800/1*SP9Apk8BRJYvB3JwhC854Q.gif)

> _The immediate visual feedback while making edits to font family, size, weight, line height, and letter spacing in Webflow made iterating on fonts super easy._

I learned along the way that the set of fonts I had defined for our website--though great in a more visual-centric context--was pretty awful for long form reading situations like on our blog. In Webflow, I gotta say, this was really easy to fix. All I had to do to was edit how some of the fonts within rich text elements were styled, such as adding some extra vertical breathing room, and making the headlines smaller with more contrast between the H1's, H2's, paragraph's etc.

#### Choosing a color scheme

When it came to colors, I wanted to use a new palette with a lot more blacks, whites, and neutrals, with pops of bolder colors that would make our site stand out and look sharp. As I explored colors, I didn't just throw colors onto arbitrary squares and compare them side by side. Instead, I tried different color schemes on a quick sample web page that I built in Webflow to see everything in context.

![](https://cdn-images-1.medium.com/max/1000/1*FKYQghEw8apgXhHiJBVq4Q.png)

> _Some exploratory sample pages we built to visualize different color scheme options._

In the end, I came up with a system where each of the main pages features a dominant accent color that contrasts as well as compliments the sharp blacks and whites throughout. This system allows for consistency throughout the site, yet allows each page to be clearly branded as its own.

![](https://cdn-images-1.medium.com/max/1000/1*iVNo5RzY8mjTnZ8ALxYGqA.png)

> _New website, new colors._

#### The role of illustration

Over the years, I've spent many many hours on illustration and icon work, which has given me a lot of time to think about the role that illustrations should play in design. Above all, I believe every illustration and icon should serve a functional role, though I also know that they have at least as much emotion-evoking power as color and type.

![](https://cdn-images-1.medium.com/max/1000/1*0r2L6mian0vJsNzD1hDo-A.png)

> _A selection of the new icons, which aim to balance meaning with visual creativity._

As you'll see in the icons on the site, each is designed to support the copy by adding information -- whether it's literal or abstracting the point -- so that it can be more easily understood at a glance. Though I put function first, it was important to me that the illustrations and icons I made were not only interesting and fresh, but also unique to Webflow.

(For more on this, Meg Robichaud from Shopify does a great job exploring the duality of the functional and emotional role that icons can play in marketing in her article [Product Vs. Marketing Illustration](https://medium.com/shopify-ux/product-vs-marketing-illustration-7ac474dfe2ed#.ttdr3ptxw).)

### Phase 3: Presentation, feedback, and review cycles

#### Marketing and design collaboration

As our design direction and content collaboration advanced, the two of us went back and forth in Figma quite a bit, with the marketing side refining what we say, in what order, and adding and subtracting pieces as we moved along; and the design side tightening the visual presentation, type hierarchy, and creating a set of components and styles that we could use across the site.

We also needed to make sure that the four pages communicated well together, and that they had a unified visual style that would be immediately apparent as visitors clicked around and explored our product.

Once we had everything in a presentable state, we went to the rest of the team for buy-in and feedback.

#### Getting feedback and iterating on design and content

Before we could start building the site in Webflow, we needed to present our proposed pages to the larger team, including our content lead, some members of our support team, and the three founders.

We knew we'd still be able to make more copy edits and design decisions_ as we built it in Webflow_, but we needed buy-in on content, structure, and design direction from the team before moving forward with the build.

As we discussed in Phase 2a, InVision and Figma played key roles in helping us work out some of the more nitty-gritty details of copy and small design questions. But we also made a point of having regular meetings to encourage discussion as questions came up.

To be fair, asynchronous tools and communication modes were critical to helping us move this along -- especially with almost a third of our team being remote -- but getting everyone in the same (proverbial) room and having those discussions live remained an important part of our design review process.

### Phase 4: Redesigning Webflow.com in Webflow

Next week, we'll take a look at how Ryan approached the task of building out the website in Webflow. Along the way, he'll discuss building a component system to lay out initial styles and elements, deciding on class-naming conventions, and using the previous version of the marketing site as a starting point.

How did you get these to play in webflow? As they start playing when you scroll into view?

Hey Daniel! The videos are custom HTML embed <video> elements with some inline styling, and play/pause based on where they are in the viewport using this JavaScript.

It would be really cool if you let people play around with your homepage design using Webflow right on your own homepage to see how it works before even signing up or anything. I think that would really sell it more than a video.

Thanks for the suggestion Johnny, this is actually something we plan on testing :)
