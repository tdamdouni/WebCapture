# What is Agile Development?

_Captured: 2015-10-14 at 23:08 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/what-is-agile-development)_

## What is Agile Development (and Why Should You Care)?

So now you're familiar with how engineers approach complex problems. You've also got an appreciation for why engineering encompasses not just the product you're building but also the process for building it. How are engineering processes implemented in the real world to manage software development prjects? Because you're going to either work as part of a team on a larger project or manage a team of your own, it makes sense to understand how this choreography comes together.

In this lesson, we'll walk through two broad philosophies of project management -- Waterfall and Agile -- before diving deeper into the Agile Development process and the tools it uses in the following lessons. By the end of this section, you'll be able to apply an Agile process to your own projects and workflows.

Let's get started!

![Dilbert Agile Programming](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/dilbert_agile.jpeg)

> _Dilbert Agile Programming_

### What is Project Management?

When you've got large teams of people trying to solve even larger problems, you naturally need some sort of structure to make sure you're all heading in the right direction. Have you ever been a part of a team that lacked strong structure or a process that wasn't well defined? Imagine that occurring when there are millions of dollars and possibly even lives at stake! The discipline of "Project Management" evolved to formalize the best practices of managing complex projects, particularly around the organization and allocation of time and resources.

For a more official (and general) definition, we turn once again [to Wikipedia](http://en.wikipedia.org/wiki/Project_management):

> Project management is the process and activity of planning, organizing, motivating, and controlling resources, procedures and protocols to achieve specific goals in scientific or daily problems.

Project management was born out of the need to apply systematic approaches to running significant (mostly civil) engineering projects in the 1950's. Because of its roots in engineering, project management follows the steps of the engineering problem-solving approach but on a macro, project-level scale. If you'll recall, those steps are:

  1. Understand the problem
  2. Plan your solution
  3. Execute your solution
  4. Verify the results

There are many different approaches to project management including Lean, Iterative, Incremental and Phased. Though they each have their own creative flowcharts and diagrams and specific implementations, all these approaches follow approximately those same four steps in some fashion or another.

For software project management, the two approaches we'll cover below are Waterfall and Agile.

### Waterfall Project Management

It seems like the most logical approach to project management is to just go right through the four problem-solving steps from start to finish. In fact, that's basically how the Waterfall method works. They just break the steps out into several more and flow downhill from one to the next:

  1. **Requirements Specification** \-- where you figure out all the details of the project and produce the "Product Requirements Document", which contains everything you need to fulfill. _ie. "Understand the Problem"._
  2. **Design** \-- figure out the architecture of the software you'll be building. _ie. "Plan your Solution"._
  3. **Construction/Implementation** \-- build the software. _ie. "Execute your Solution"._
  4. **Testing** \-- make darn sure the thing works before shipping it. _ie. "Verify your Results"._
  5. **Installation** \-- install the product with the customer or end user
  6. **Maintenance** \-- address issues that arise from actual use

Each phase is verified and approved prior to moving to the next. You'll notice that there are a few extra phases on the end -- in the real world, once you've created a software product, there are additional practical stages like installation and maintenace that aren't really covered in the 4-step approach.

[ ![The waterfall model diagrammed](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/waterfall_flowchart.jpg) ](http://www.buzzle.com/editorials/1-5-2005-63768.asp)

> _[The waterfall model diagrammed](http://www.buzzle.com/editorials/1-5-2005-63768.asp)_

_Source: [Buzzle.com](http://www.buzzle.com/editorials/1-5-2005-63768.asp)_

#### What Waterfall is Good For

The process is designed to make _really_ sure that you're building a functional product. It's a legacy of hardware construction, where it's very costly to change things after the fact. When software engineering was getting started, software was shipped out on physical disks that had to be updated manually so it was reasonable to adopt that kind of process.

In general, the waterfall "Big Design Up Front (BDUP)" model is most effective for projects with high barriers to future change or serious safety or reliability needs (e.g. space programs or critical health software).

Waterfall follows some good engineering theory as well -- you learned before that a bug caught early is worth much more than one caught late. You've been relentlessly pushed to think and plan first. Why isn't waterfall still in favor?

#### What Waterfall is Not Good For

Unfortunately, the process is extremely long, bureaucratic and costly. It assumes that you know what you're going to build from the beginning and can spend long periods of time (often 12- or 18-month cycles) building it. By assuming they know everything up front about the customer, engineers ended up building all kinds of features that never got used (most features you build will never get traction with users... sorry if that's a shock).

Companies developing consumer-facing software found that they were having trouble keeping up with the market given these constraints and needed something more.

**Check out [this very brief intro to Waterfall (below)](https://www.youtube.com/watch?v=McWOIye8Kr0)**:

For an amusing history of waterfall, watch **[this video as well (below)](https://www.youtube.com/watch?v=X1c2--sP3o0)**:

### Agile Development

After about 40 years, developers came up with something more appropriate to delivering software in a dynamic environment. Though there were certainly precursors to it, the Agile philosophy was really kicked off in 2001 when a group of software engineers posted the _Agile Manifesto_. That manifesto read:

> We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value:
> 
>   * **Individuals and interactions** over Processes and tools
>   * **Working software** over Comprehensive documentation
>   * **Customer collaboration** over Contract negotiation
>   * **Responding to change** over Following a plan
> 
> That is, while there is value in the items on the right, we value the items on the left more.

What that basically means is that, instead of a long and rigid development process, they wanted to create software that was more responsive to change. More specifically, as [Wikipedia says](http://en.wikipedia.org/wiki/Agile_software_development):

> The meanings of the manifesto items on the left within the agile software development context are:
> 
> **Individuals and interactions** - in agile development, self-organization and motivation are important, as are interactions like co-location and pair programming.
> 
> **Working software** - working software will be more useful and welcome than just presenting documents to clients in meetings.
> 
> **Customer collaboration** - requirements cannot be fully collected at the beginning of the software development cycle, therefore continuous customer or stakeholder involvement is very important.
> 
> **Responding to change** - agile development is focused on quick responses to change and continuous development.

So Agile is about more than just creating a nimbler planning process for a particular software project -- it provides a whole philosophy for organizing teams and working with clients. It specifically advocates working with customers constantly during the development process to keep up with changing requirements, which should feel familiar from our User-Centered Design lessons in the [Design mini-course](http://www.vikingcodeschool.com/web-design-basics).

Agile teams operate in ways that promote collaboration and adaptiveness, including co-location and pair programming. A notable piece that's missing is the massive specification document produced early in the waterfall process.

Agile also advocates very short cycles, often only 1-2 weeks at a time, before the software is shipped. That software is usually deployed to users as soon as possible (obviously highly project dependent) and feedback is collected in real time to help adjust the priorities for the coming iterations.

You might have noticed that Agile also meshes really well with the prevailing [Lean Startup](http://en.wikipedia.org/wiki/Lean_startup) philosophy, which advocates shipping the simplest functional version of your product to customers ASAP. Keeping cycle times short has all kinds of advantages -- better responsiveness with clients, quicker feedback from users, and happier engineers who get to frequently ship meaningful software (woohoo!!!).

So why did it take so long to "go Agile"? The advance of Agile methodologies has been undoubtedly supported and accelerated by the invention and growth of cloud-based software. Deploying your code to "the cloud" instead of having users install it directly onto their machines makes it MUCH easier to update software for all your users (essentially just a button click). Without that option, it would be much more difficult to adapt to change as quickly as Agile requires.

For a helpful introduction to Waterfall, Agile (and Spiral), **check out [this video (below)](https://www.youtube.com/watch?v=Fr-B4xHZRzY)** from the Berkeley CS169.1 course _between 36:08-45:04._

It's important to note that, though Waterfall was (and is) heavily implemented, it wasn't the only project management technique to be used by the software industry prior to Agile and it won't be the last. We've obviously simplified things here and we don't want to give you the impression that the world was all Waterfall prior to 2001 and all Agile after.

In fact, you'll see in the next lesson that XP was around before the Agile Manifesto was ever released and it's based on practices that were started in the 1960's.

[ ![waterfall vs agile infographic](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/waterfall_vs_agile_infographic_small.jpg) ](http://www.liquidplanner.com/blog/agile-v-waterfall-which-project-management-style-is-right-for-you/)

> _[waterfall vs agile infographic](http://www.liquidplanner.com/blog/agile-v-waterfall-which-project-management-style-is-right-for-you/)_

_Source: [liquidplanner.com](http://www.liquidplanner.com/blog/agile-v-waterfall-which-project-management-style-is-right-for-you/)_

### Wrapping Up

You should have a good sense of the general principles of the Agile process and how they differ from those of the Waterfall process which was dominant in the past. In the next lesson, you'll learn about two specific ways that Agile is implemented in the real world -- eXtreme Programming (XP) and SCRUM.

###  Next Lesson: Agile Development with XP and SCRUM 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/agile-development-with-xp-and-scrum) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/engineering-product-vs-process)
