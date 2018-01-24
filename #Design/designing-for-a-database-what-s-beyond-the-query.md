# Designing for a Database: What's Beyond the Query?

_Captured: 2017-11-28 at 09:57 from [dzone.com](https://dzone.com/articles/designing-for-a-database-whats-beyond-the-query?edition=337920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-27)_

Navigating today's database scaling options can be a nightmare. [Explore](https://dzone.com/go?i=255329&u=http%3A%2F%2Fgo.nuodb.com%2FDatabase-Scaling-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dad%26utm_content%3Ddb-scaling) the compromises involved in both traditional and new architectures.

Even the most technically minded companies need to think about design. Working on a database product at a startup is no different. But this comes with challenges, such as figuring out how to implement human-centered design methodology at a technical company but also how to contribute to building a design process that everyone agrees with across the organization. This blog will detail how product design is done at MemSQL as well as highlight how to design enterprise products at a startup.

## How Do We Define Product Design?

Product design is the end-to-end process of gathering requests and ideating in order to hand off pixel-perfect products and iterations. There are usually two different ways of dividing work: breaking down multiple design tasks into steps handled by different team members, or each designer taking ownership of a product, or a feature, and designing in a full-stack way. At MemSQL, we develop each product with the latter model, which requires constant and proactive engagement with other folks on the team.

Because everything our users experience when interacting with our product should ideally be counted in the scope of product design -- we wouldn't ignore email templates, docs, the help center, the support chat widget, and so on. By thinking about the product as a holistic ecosystem, we are able to capture the pain points both inside and beyond the stand-alone application.

## What Is the Process?

Below are the steps we work through at MemSQL before our customers see any end product or piece of collateral.

### Kickoff

Most of the product features are requested by product management (PM). PM gathers feedback directly from customers or other departments, such as customer success and sales. Designers are also encouraged to take initiative and lead their own project if it's valuable to the product as well as the business. To start the project, designers need to write a proposal doc and send it to key stakeholders. The stakeholders will evaluate the idea and decide if it should be put on the roadmap or not.

### Research

Before jumping onto the design phase, we do research to validate the goal, gather technical requirements, explore the market, understand our customer, and analyze what we have done so far.

### Getting Involved With the Engineering Team

First, we need to talk with the engineering team to understand the technical principles, expectations, difficulties, constraints, and context. This helps us set a clear scope of what we can implement, or not, in the project.

### Study Your Customers and Beyond

Customer study covers a wide range of topics. Various tools and methodologies are used, such as interviews, surveys, and focus groups. Notice that customer study is different from usability testing, which will be mentioned in the Testing section. While usability testing focuses on the ease of use of the product, the customer study is expected to answer more strategic questions and help us evaluate the direction of the product.

![](http://blog.memsql.com/wp-content/uploads/2017/10/trello_mosaic.png)

> _We use Trello to sort out massive notes from customers and color-code them by characteristics, which could later help us identify different target groups._

## Ideation

Personally, it is the most exciting phase of design since that's where we get to synthesize everything we learned about the problem and try to land the creativity and empathy. By ideating various ideas in a low-fi stage, we push ourselves out to seek more innovative solutions.

It's very easy to skip ideation and go straight to design, especially when "ship it" becomes the rule of thumb. It might even work, sometimes, which makes people underestimate the importance of ideation.

### Brainstorm

We start the design phase from brainstorming. We usually start with listing features and components, drawing flow maps on the whiteboard, and sketching rapid wireframes to show the idea. We will also discuss the realistic side of the projects: How/when do you think it could be implemented? Would it be better if we want an MVP? What would you like to be in the next round of iteration? This allows us to scope down properly while keeping the vision wide open.

There are massive ways to find inspirations, including looking into industries that seem irrelevant to your own industry (see [Analogous Market](http://pubsonline.informs.org/doi/abs/10.1287/mnsc.2013.1805)).

### User Flow

User flow is one of the most effective ways of communicating design ideas to other team members. We use flowcharts to represent each step the customer will experience. The chart could help the team, especially the engineers, to fact-check with the design team so that the backend and the experience design are aligned.

![](http://blog.memsql.com/wp-content/uploads/2017/10/Screen-Shot-2017-10-02-at-4.48.37-PM.png)

> _We keep user flow diagrams together with the interface design in the same Figma file so that it's always easy to go back and check the design._

### Spec

To consolidate the idea and to communicate effectively with the team, we usually write down specs and send it out to the whole team for review, spanning PM, design, and engineering. This is important because we want to make sure that all team members involved are on the same page. It is also a great place to review the goal, the metrics, and how to move forward.

## Design

Design is an iterative process. It requires patience and commitment to the process. Good ideas could come at the beginning or the very end; however, it is important to always have a holistic view of the timeline and the priority so that we won't get lost in the pixels and fancy animations.

### Wireframe

Though we also do wireframe during the brainstorming process, it is crucial to have more thorough wireframes to show a few design approaches. By using wireframe, both the designer and the reviewer could focus on the function, transition, and interaction, instead of all the pretty visual elements. Wireframe could also help cover different use cases, i.e. first-time user, returning user, multiple user permissions, and more.

### High-Fidelity Mockup

Hi-fi mockup is how the product will statically look. We use Figma to do hi-fi mockups, which allows us to effectively communicate with the front-end engineer while also collaboratively iterating on design.

### Prototype

Once the hi-fi mockup is nearly locked down, we use InVision to show the interaction. This is an important step for design review since it will be the first time that other stakeholders will see the look and feel of the product and check the flow and information are correct. We also use HTML+CSS examples to show the visual effect.

### Writing

There are two parts of writing - technical and UX writing. Sometimes it is merged into smaller topics. Technical writing goes in the document, so customers get all the information they need. UX writing, which covers the copy in the UI, sets a tone and personality of the product and could impact the customer's mood when interacting with the product.

## Implementation

We are lucky to have a very good front-end team that is collaborative and open for discussions. We make sure that the front-end team implements the design as accurately as possible; if it's not the same, there should be a reason.

### Handoff

When we do handoff specs on Figma by using red lines, call-outs, or mockups of different steps, we try to state the interaction as clear as possible. We also use Component Library to define and reuse some common design elements, including buttons, tables, and modal windows, which helps keep the design consistent and easier to implement.

![](http://blog.memsql.com/wp-content/uploads/2017/10/Screen-Shot-2017-10-02-at-5.05.46-PM.png)

> _By breaking down the interactions into steps, everyone gets on the same page of the design._

### Bug Bash

Similar to engineering bug bash, design bug bash aims to do a comprehensive click-through to fix the issues, big or small, which include browser compatibility, keyboard-tabbing, screen compatibility (retina display, readability under different brightness, contrast, color tone), error cases, error messages, breakpoints, UX writing, and more.

## Validation

People always say that there is no good or bad in design, which might be true; however, there could be good and better in each specific case. What is the problem we are trying to solve? What are the metrics to help reveal the progress? What is the ultimate goal we are trying to achieve? We ask ourselves the tough questions and seek answers from data and follow-up studies.

### Task Analysis

There are different forms of task analysis; thinking aloud is one commonly used. By giving participants a specific task or instruction, they will click through the product to finish the task as well as tell what they think along the way. It is great for gathering customer feedback on specific features, interactions, content, and visual components, and could be tested with a functional prototype on staging or InVision clickthrough.

### Data Analysis

We use Heap Analytics, Google Analytics, and other tools to track customer behavior through the funnel. With the end-to-end tracking, we could clearly see how each individual user interacts with our product and every single page, which is a great way to visualize the customer's journey. We usually pay attention to common patterns to try to identify if it is as expected or not when we design. We also look for data that could be misleading; when we see unexpected customer behavior happening again and again, it is better to conduct a Task Analysis with different types of customers to see what they say before jumping to conclusions too quickly. In other words, quantitative feedback is very helpful for validating an assumption than drawing an uninformed conclusion.

## Designing as a Team

Design is never a one-person job. As long as we are designing someone, it is the designer's responsibility to dig deeper into people's words and interpret them in a way that an effective solution could be built upon. By encouraging contributions from multiple stakeholders along the way as well as unlocking communication across departments, we are able to produce better design solutions.

We are still iterating the design process with feedback from both customers and internal teams, such as sales, customer success, PM, and engineering. We want the design to support the value of MemSQL and to help build products that meet our customers' real needs.

Planning for disaster doesn't have to actually be a disaster. [Understand your options](https://dzone.com/go?i=255325&u=http%3A%2F%2Fgo.nuodb.com%2FDR-eBook-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dad%26utm_content%3Ddr) for deploying a database across multiple data centers - without the headache.
