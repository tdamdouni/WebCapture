# Scrum And DevOps

_Captured: 2018-07-30 at 07:46 from [dzone.com](https://dzone.com/articles/scrum-and-devops?edition=385303&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-30)_

**[Download this white paper](https://dzone.com/go?i=283441&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fcharacteristics-great-scrum-team-0%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3Dcharacteristics-whitepaper%2520) to learn about the ways to make a Scrum Team great, brought to you in partnership with [Scrum.org](https://dzone.com/go?i=283441&u=https%3A%2F%2Fwww.scrum.org%2FAbout%2FAll-Articles%2FarticleType%2FArticleView%2FarticleId%2F1029%2FCharacteristics-of-a-Great-Scrum-Team%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3DGreatScrumTeam). **

![](https://scrumorg-website-prod.s3.amazonaws.com/drupal/inline-images/Scrum_and_DevOps.jpg)

Hello, great people of the world. Welcome back to [Professional Software Delivery with Scrum (PSD)](https://www.scrum.org/courses/professional-software-delivery-scrum) blog series with yours truly. This time we're going talk about how to use Scrum And DevOps. I am interested to discuss this topic because it's quite common I get the question from someone in the Agile community, "Should I use Scrum or DevOps?" This question deserves attention because of the motivation to choose DevOps over Scrum. People want to go with DevOps over Scrum because they want to be Agile but they can't change their organization. Many people in the Agile community whom I've interacted with think that DevOps is only about toolings for continuous delivery. We're going to learn why DevOps is not only about tooling for the delivery pipeline. Unlike my previous article about [Scrum and eXtreme Programming](https://www.scrum.org/resources/blog/scrum-and-extreme-programming-xp), this time we're going to learn how to integrate Scrum And DevOps, starting from a DevOps lense.

## Scrum Is Just a Framework

Scrum is just a simple framework for complex product development that is based on values and principles. Scrum is not a prescriptive methodology that tells you how your process should look. Scrum is highly focused on what is happening during the Sprint. Scrum will not tell you how your process within the Sprint should look like. Scrum is an additive framework, which means that Scrum will only tell you the minimum sets of what you need to have to use it. The same as when you need to install a software on your computer, there is a minimum requirement for the computer specification, but there is nothing wrong with installing the software on a computer that is above the minimum specification. So with this premise, it is not illegal to add practices that will enhance the flow of your value delivery within the Scrum Framework.

## DevOps: Lean Thinking, Systems Thinking and Value Stream Mapping

DevOps starts with systems thinking and views the whole value stream in the system rather than only zooming into the development phase, analyzing how the work gets into the development (the upstream) and how the works get delivered to customers (the downstream). Systems thinking views how every interconnected element in the system affects one another. In a complex system like a corporate infrastructure, elements do not work in isolation. Making one change in an element is going to impact another element in the system.

A value stream is how processing customer requests into a tangible outcome flows from one element to another element in the whole system. Whenever there is a request, there is a value stream in the system.

Besides systems thinking, DevOps is also based on lean thinking. Lean thinking is about reducing waste in the value stream. Any activities that are non-value added can be considered as waste. I am not going to elaborate on Lean and types of waste in this article.

Lean thinking, systems thinking and mapping the whole value stream is important and works nicely with Scrum because Scrum is based on lean thinking. This is what I do before starting Scrum in a large corporation, view the whole system holistically and map the whole value stream in the system first rather than only applying Scrum the IT department. Kanban is a good tool to visualize the whole value stream in the system.

When we're using Scrum And DevOps, all of the activities in the value stream, from customer requests and releasing the product, to production environments and customers, happens within the Sprint. This does not mean a Sprint is a mini-Waterfall where deployment only happens at the end of the Sprint or all of the analysis happens at the beginning of the Sprint. Using Scrum with Kanban helps to get out of using Sprint as mini-waterfall and move towards single piece flow-based models in the Sprint.

## Scrum Team Applying DevOps: The Composition

Scrum Teams adopting DevOps will have a different way of working than a Scrum Team that is not adopting DevOps. Not only their way of working is different, the team composition also look very different.

> The development team consists of professionals who do the work of delivering a potentially releasable Increment of "Done" product at the end of each Sprint.  
\- Scrum Guide

Scrum says that the development team consists of professionals who deliver the potentially releasable increments at the end of the Sprint. As DevOps views the whole value stream and uses Systems thinking, the professionals on Scrum Teams adopting DevOps are everyone who processes the Product Backlog Item (PBI) in the whole value stream from end-to-end. Many people see the development team only consists of developers that is why many come to think that Scrum is for development phase only.

In a Scrum Team adopting DevOps, the team composition includes everyone, but not limited to, marketing people, analysts, UI/UX designers, developers, operations people, sysadmins, data scientists and site-reliability engineers. They all work together collaboratively as one unit to deliver value to their customers.

## DevOps Three Ways

[DevOps Three Ways](https://itrevolution.com/the-three-ways-principles-underpinning-devops/) are the set of underlying principles that make up DevOps. DevOps Three Ways is based on lean thinking and systems thinking. DevOps Three Ways work with Scrum as the Three Ways is not about specific tools and practices that are often more emphasized during any discussion about DevOps in the communities. Scrum Teams adopting DevOps Three Ways will have a different way of working with Scrum Teams who are not adopting it. None of the DevOps Three Ways are in conflict with the Scrum Framework and Scrum Values.

**Disclaimer**: The practices I elaborate here are not a complete list of practices to implement the DevOps Three Ways. I will be only elaborating some practices to meet the DevOps Three Ways that are already commonly practiced in the communities. I believe in the future there will be more practices to meet the DevOps Three Ways that is not listed here.

### 1\. Optimise Flow

The First Way in the DevOps Three Ways is Optimise Flow. In DevOps, we are concerned about optimizing the flow of single Product Backlog Item since the first time customer requested it until the customer get the requested PBI in forms of tangible item (i.e working feature) in the production environment. Anything that gets in the way of make the PBIs flows smoothly in the value stream may be a bottleneck that should be removed. Many people in the Agile communities believe that flow contradicts Scrum's Sprint because the premise is:

  1. You plan for the whole PBI need to be completed for the Sprint during the Sprint Planning. The Sprint is a commitment.
  2. You can only deliver to production once after the Sprint Review.

This is Sprint as mini-Waterfall model. Even though there is nothing wrong with this, great Scrum teams should move away from this model as they are improving their way of working. We will see why the Sprint works with flow-based models.

In Scrum, the Scrum Master is the role responsible for removing anything that impedes the flow of value delivery to the customers. When the Scrum Team decides to adopt a flow-based model, the Scrum Master needs to learn about flow-based models and coach the whole Scrum Team on how Scrum works with flow-based models.

#### Sprint Planning

> "...enough work is planned during Sprint Planning for the development team to forecast what it believes it can do in the upcoming Sprint. Work planned for the first days of the Sprint by the development team is decomposed by the end of this meeting, often to units of one day or less." \- Scrum Guide

Scrum Teams adopting a flow-based model will have a different nature of Sprint Planning. Nothing in the Scrum Guide states that the Scrum Team fixes the plan for the Sprint during Sprint Planning. The Sprint Planning is more focused and committed with the Sprint Goal rather than the Sprint Backlog. The Sprint Planning is an opportunity to get everyone's heads down to look at the same goal. The purpose of the Sprint Planning is to calibrate the next Sprint development with a single goal. During Sprint Planning enough work is forecasted for the very few days of a Sprint. More work may emerge later on during the Sprint as long as it does not endanger the Sprint Goal. Having Kanban systems helps the team to manage the work that emerges later during the Sprint.

#### Continuous Delivery to Production Environment 

> "The heart of Scrum is a Sprint, a time-box of one month or less during which a "Done", useable, and potentially releasable product Increment is created." - Scrum Guide

Nothing in Scrum that says you can only deliver to production environment after a Sprint Review. [The Sprint Review is not a phase gate](https://www.scrum.org/resources/blog/sprint-review-not-phase-gate) but an opportunity to get feedback about what you have developed and the Sprint Retrospective is an opportunity to improve the process of how you develop the product. Even in flow-based models, you need to know whether you have flown in the right direction. Consider that the end of the Sprint works like a Global Positioning System (GPS) to track where you are at the moment. The Sprint Review and the Sprint Retrospective does not and should not block flow, but enhance flow.

One thing that I would like to highlight here is that the Sprint is not a release cadence but a planning and review cadence. At a minimum, you need to have a "potentially" releasable product increment at the end of the Sprint. In a previous article, we've learned that a [Scrum Team adopting eXtreme Programming (XP)](https://www.scrum.org/resources/blog/scrum-and-extreme-programming-xp) delivers to production every night. So there is nothing wrong with releasing the product to the production environment more than once in a Sprint. If the Scrum team is able to deliver frequently more than once in a Sprint, that means they've gone beyond the minimum standards that Scrum requires. We should celebrate it because not many teams are able or allowed to release to production environment multiple times in a Sprint or even multiple times a day.

#### Flow-Based Daily Scrum

> The structure of the meeting is set by the development team and can be conducted in different ways if it focuses on progress toward the Sprint Goal.

Scrum Teams adopting flow-based models will use the Daily Scrum to inspect the flow of the PBI towards the Sprint Goal. The Daily Scrum becomes a tool for the Scrum Team to optimize flow. Some Scrum Teams may do it more than once a day because they know that Daily Scrum is not about reporting but about synchronizing each other's plans. Some Scrum Teams will look at their Kanban system during the Daily Scrum to optimize flow. During Daily Scrum, new Sprint Backlog may be added as the team learn more about their progress. The Scrum Master will work to remove anything that is impeding flow that is discovered during Daily Scrum.

Scrum Teams adopting DevOps will have a more ambitious Definition of Done compared to Scrum Teams who are not adopting DevOps because they have the ambition to deliver the product to production environment more than once a Sprint, sometimes multiple times a day. If their Definition of Done is not ambitious, they may not meet their goals. Some practices they may have in their Definition of Done that will optimize flow are:

  * Infrastructure-as-Code so that the team has a production-like environment at every stage in the value stream.
  * Automated Testing that will improve flow from Unit Testing to Integration Testing to Acceptance Testing, with supporting practices such as Test Driven Development, Behaviour Driven Development, and Acceptance Test Driven Development.
  * Continuous Integration.
  * Continuous and Automated Deployment.
  * Decouple deployments from release using techniques like canary release or feature toggling.
  * Architect for low-risk releases like using Microservices.

Some of the practices listed above are already implemented by Scrum Teams who are implementing eXtreme Programming (XP). The list above is not necessarily a complete list of practices to optimise flow in the value stream as I believe there will be more practices that may be discovered by the community in the future.

### 2\. Amplify Feedback 

The Second Way in the DevOps Three Ways is Amplify Feedback. Scrum is all about feedback. At its core, Scrum has the Sprint and the Daily Scrum as a built-in feedback loop. Scrum Teams adopting DevOps will have a different nature of implementing the feedback loops. Scrum Teams implementing eXtreme Programming have multiple feedback loops with pair programming and Test Driven Development as the smallest feedback loops.

#### 1\. Sprint Review

Scrum Teams adopting DevOps will have a different way of running the Sprint Review because the product is already in the production environment before the Sprint Review is held. So instead of giving feedback about the product increment, the whole Scrum Team along with the business will look at a single dashboard of metrics that covers business-level, application-level, infrastructure-level, and deployment pipeline metrics. By looking at a holistic view instead of isolated view metrics, the whole business and the Scrum Team is able to give a sound judgment about the performance of the product in the market and collaborate on creating a strategy they should apply in the next Sprint to optimize the value of the product.

#### 2\. Hypothesis-Driven Development and A/B Testing

A Scrum Team adopting DevOps will implement Hypothesis-Driven Development. For this kind of Scrum Team, "Done" does not stop until a feature is complete only because they believe completed features do not mean the product is successful in the market. For this kind of Scrum Team, "Done" is when the feature gains traction in the market. The whole Scrum Team works together to ensure that every feature delivered is valuable for customers.

#### 3\. You Ship It, You Manage It

Developers in a Scrum Team adopting DevOps have a higher responsibility and need to learn about maintaining the application live and stable in the production environment. To amplify feedback and reduce wasteful activities, developers in a Scrum Team adopting DevOps get to maintain the applications they develop in a production environment. The mantra is, you ship it, you get to manage it. In some organizations, this goes as far as giving time-shifts to developers to attend to production incidents and outages support call. Not only in DevOps developers are given higher responsibility, the management also needs to give higher trust to empower the developers to go above and beyond.

#### 4\. Pair Programming and Code Review

From my previous article, we have learned that [Scrum Teams implementing eXtreme Programming](https://www.scrum.org/resources/blog/scrum-and-extreme-programming-xp) religiously do pair programming. We have learned that pair programming is not about two programmers doing programming together on one computer but more about live feedback on how the code will actually work in production. Scrum Teams adopting DevOps will utilize pair programming and code review to amplify feedback.

#### 5\. Daily Scrum as a Feedback Loop

The Daily Scrum is all about feedback, not a status report. In a complex unpredictable environment, feedback is very important. Having feedback loops nested within another feedback loop is essential in a complex environment. The feedback in Daily Scrum will amplify the feedback received at the end of the Sprint. The Scrum Team will learn how they are progressing towards the Sprint Goal.

The list above is not necessarily a complete list of practices to amplify feedback as I believe there will be more practices that may be discovered by the community in the future.

### 3\. Maximise Learning and Experimentation

The Third Way in the DevOps Three Ways is Maximise Learning and Experimentation. The heart of Scrum is about continuous learning because Scrum is based on empiricism. Empiricism asserts that knowledge comes from experience and making decisions based on what is known. The purpose of having Sprints is to maximise learning and to improve how Scrum Teams will operate and deliver value in the next Sprint. Sadly, many organizations without a clear understanding of Scrum values and principles will treat the Sprint as a mini-waterfall and will fix the scope for the Sprint without any rooms for the Scrum Team to innovate or to learn something new. The Scrum Master is the role that is responsible to ensure that the organization has a culture of learnings.

#### 1\. Psychologically-safe and Blameless Environment

A great Scrum Master will focus and will invest more time in injecting the Scrum Core Values into the Scrum Team and the whole organization rather than just focusing on the Scrum mechanics. They know that the Scrum core values will contribute to creating a psychologically-safe and a blameless environment.

In DevOps, everyone works together to ensure that the product is valuable and meets the business goal. In a psychologically-safe and blameless environment, there should be no politics, personal agenda, and silos. Everyone in the value stream looks at the same holistic product metrics regardless of their role. A blameless culture is important so that everyone in the value stream is collaborative and not just throwing work over each one's shoulder. Any incentives that make everyone only cares about their metrics should also be removed.

The Third Way is more about organizational refactoring practice than it is about technical practice. The Scrum Master is the role responsible to coach the management and the human resource department on changing the incentives system that blocks collaboration and only foster politics and bureaucracy.

#### 2\. On-Demand Retrospectives

> The Scrum Master encourages the Scrum Team to improve, within the Scrum process framework, its development process and practices to make it more effective and enjoyable for the next Sprint.  
\- Scrum Guide

One misconception about Scrum in the communities is that retrospectives or learnings only happen at the end of the Sprint. In a Scrum Team adopting flow-based models, learning needs to happen just-in-time and more frequent. As we've learned earlier, Scrum is an additive process. Everything in Scrum is a minimum set requirements. Sprint Retrospectives provides a focused time to reflect back and to learn about what is happening in the Sprint. But that does not mean Scrum does not allow you to learn multiple times or to have additional retrospectives in a Sprint. If the organization becomes a learning organization and wants to continue to learn, then we should celebrate it because many organizations stopped growing when they stopped learning. Many Scrum Teams celebrate what they've learned during the Daily Scrum as they see Daily Scrum is about inspecting and adapting.

#### 3\. Slack Time for Improvements

> To ensure continuous improvement, it includes at least one high priority process improvement identified in the previous Retrospective meeting.  
\- Scrum Guide

Many managers or organisations still see Scrum's Sprint as a mini-waterfall (or sometimes mini-deadlines) and only about delivering features. People working in these organisations come to think that Scrum does not provide time for improvements. This is not true. In fact, Scrum Guide states that at least one item in the Sprint Backlog must contain improvements identified during the previous retrospectives. Scrum Team adopting DevOps will go further by deliberately providing slack time to innovate as much as 20% time (or more) to improve the value of delivery in the value stream.

The list above is not necessarily a complete list of practices to maximise learnings and experimentation as I believe there will be more practices that may be discovered by the community in the future.

## DevOps is More about Organizational Culture than about Tools

As you can see, DevOps is not about tools and automation in the delivery pipeline. In fact, as we have learned, tools and automation is only one-third of DevOps (I would say it is even less). Overall, DevOps is about collaboration and collective ownership, focus on the flow of value delivery and learning and experimentation culture. But sadly, many tooling vendors position DevOps as tools and process for delivery pipeline (the vendors that I've witnessed in my market are more focused on tools but your experience may be different to mine). This will get the management excited because many managers whom I've met think that after buying and installing the "DevOps" tools without changing their organization will make their company instantly Agile. This is like putting the cart in front of the horse.

From this article, we've seen that Scrum and DevOps actually share more in common than most realize. Just like how Scrum is not about tools and process, the DevOps Three Ways is also about values and principles.

Hopefully, this article along with the visual helps you understand how Scrum and DevOps work together and how they do not contradict each other. You should be adopting both Scrum and DevOps rather than choosing either one. Looking forward to hearing you exploit Scrum and DevOps to deliver great products to your customers. If your team want to learn how to use Scrum and DevOps check out [Professional Software Delivery with Scrum course](https://www.scrum.org/courses/professional-software-delivery-scrum).

Thank you to [Jesse Houwing](https://www.scrum.org/user/76), [Fredrik Wendt](https://www.scrum.org/fredrik-wendt) and everyone in the Scrum.org Professional Scrum Developer Trainer community for assisting me on the creation of this article.

**[Learn more](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) about the myths about Scrum and DevOps. [Download the whitepaper](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) now brought to you in partnership with Scrum.org.**

Topics:

agile ,scrum ,devops ,metrics ,extreme programming ,Lean thinking ,value maps
