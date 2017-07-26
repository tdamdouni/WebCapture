# Conceptual Debt is Worse than Technical Debt

_Captured: 2015-12-31 at 22:23 from [medium.com](https://medium.com/@nicolaerusan/conceptual-debt-is-worse-than-technical-debt-5b65a910fd46#.eq4h71a52)_

**Definition**. _The consequences of making bad design choices when choosing concepts to model your product around. A conceptual or mental model consists of the core objects and actions that you present to users in your system. There is usually substantial design and technical work associated with trying to shift a system to a new conceptual model._

I've been using the term conceptual debt as a way to communicate to companies the importance of choosing the right mental model and abstractions from the outset of designing products. The consequences and inertia of bad design choices at the modeling stages can be really expensive for a company, because they're potentially building their entire product on the wrong foundation. Conceptual debt is often the difference between a product succeeding or failing.

I came up with the term conceptual debt as an analog to the familiar 'technical debt'. Technical debt happens when you make mistakes like choosing the wrong database or programming language for the task at hand, or when you write code in a hurry that ends up being buggy and non-performant. The consequences of making poor technical choices is that your product may be buggy, may run slow, and may result in your team requiring a prohibitively long time to develop new features due to code complexity. To fix issues associated with technical debt you may need to change the programming language you're using, or refactor substantial portions of code. Dealing with technical debt involves making changes under the hood, but the interface that your user sees stays the same: the conceptual design of the product already works well for users. The main issues in the case of technical debt are that the product is running slowly, not scaling well, or preventing your company from getting new improvements out the door -- but conceptually the product is intuitive. Technical debt is usually bad, but fixable.

On the other hand, conceptual debt happens when you've made design choices that lead to an unintuitive product. The product is unintuitive because you've chosen the wrong way to model and represent the core concepts in your system.

Customers using your product have a mental (conceptual) model of how your system works, and what objects and actions it's composed of. They believe that if they take certain actions in your product certain results will occur. If your system does something they don't expect, your system doesn't align with their mental model. It's your aim as a product designer to ensure that your system has a simple and obvious mental model that is learnable and works the way your customers expect it to.

Let me give you a quick example of conceptual debt I encountered:

  * A photo baby book app that was similar to Instagram had two ways for users to organize their photos: Tags & Folders. Both folders & tags had no hierarchy (i.e. you couldn't nest folders or tags), and conceptually folders and tags were identical in terms of their functionality. There was no need to have both folders and tags. Users ended up being confused by when they should use folders instead of tags, and so for each photo they often ended up adding it to both a folder and a tag, e.g. a folder named Walking and a tag #walking. This was twice the work for users, and twice the work for the products' developers as they had to code and support both features, despite the fact that conceptually they did the same exact thing. Undoing this conceptual mistake also becomes tricky as now some users are using folders, and others are using tags for organization.

Though this baby book Folder/Tag example doesn't seem like a big issue at first glance, it was. The main function of the baby book app was organizing your baby photos, and users were confused by how to organize their photos because of the dual folders & tags. If your users are frustrated in the main use cases of your app it's going to have negative consequences.

As the first step in building your product, it's essential to identify a good mental model that aligns with your customers' before you start writing any code. A mental model is probably effective if users find the the product easy to learn, and the product doesn't need a manual to describe how it works.

Scott Klemmer's Stanford Human-Computer Interaction course has an excellent discussion of Mental Models (https://class.coursera.org/hci/lecture/26) and the importance of representation in design (https://class.coursera.org/hci/lecture/8). So much of good design is simply choosing the right mental model.

What is the cost of conceptual debt and choosing the wrong mental model? As Klemmer describes in his lecture, a mismatch between your system's conceptual model and the user's conceptual model leads to "slow performance, errors, and frustration". From a practical standpoint, you will have spent time designing and coding an interface based around concepts that provide a less than ideal user experience.

**Signs Your Product Has Conceptual Debt:**

  * New users don't get what's going on. It takes a while for them to learn a product, they are often surprised by what specific features do, or what the objects in the system represent.
  * Your product introduces many concepts which are entirely unfamiliar to users, and have no analogies in other products they may have used.
  * There are many exceptions and unique cases that users are presented with in the flow of using your product, that they need to handle in a different way then they usually behave in your product.

The users that persevere and use your product despite its confusing design become familiar with the broken concepts and adapt their mental model to the way you've designed the system. This creates an unfortunate inertia to keep things as they are. While persistent users may adapt because they have no better alternative, new users will continue to find the product confusing and there will be a steep learning curve for those users as they onboard. As soon as a simpler to use product appears new users will choose that product over yours.

**Courage For Clarity**

It can be hard to undo conceptual debt. First you need to realize you have chosen the wrong concepts, or that your concepts are outdated. Then you are embarking on a substantial redesign. Attempting a redesign requires re-educating and transitioning the users who are familiar with the old mental model, and substantially reworking your codebase to reflect the more intuitive mental model you're trying to introduce.

There's going to be switching costs: once users have adapted to the mental model of your product they don't want it to change. You will always see some backlash whenever you introduce new designs, as it takes time for people's mental models to adapt to a new model you're introducing, even if it's simpler. Beyond the cost of re-educating users, the transition to a new mental model is usually considerable from a code perspective. The original concepts will be deeply embedded in your code, though there are strategies for managing a conceptual redesign from the code side.

While it's difficult to undo conceptual debt, the payoff of an intuitive product with a simple, learnable conceptual model are immense:

  * Happier users because they can figure out how everything works easily
  * Fewer user mistakes that have bad consequences, because users know what their actions do in the system
  * Less time needed to onboard users -- it just works and makes sense, no explanation required.
  * Happier and more productive developers, because the conceptual model of your product is easier for them to grasp as well!

Choosing the wrong concepts when designing a software product can be really expensive down the road, so it's important to get things right from the start.

**Choosing The Right Mental Model**

Here are a few tips for Klemmer's course and my own experience to ensure you choose the right mental model, along with some advice on how to rework existing concepts that may be confusing to your users.

  * Leverage conceptual models already familiar to the user from other products. As Klemmer says "People reason about new interfaces by analogy to old interfaces they are more familiar with" -- so it's good to leverage familiar conceptual models where possible.
  * Make your conceptual model clean and consistent. If you expect clicking a button to do something consistent every time, it's weird if it does something different 1/100 times.
  * Unify concepts wherever possible -- don't have two concepts where one will do, since people will be confused when it's appropriate to use one or the other.

As an analog to the old adage "measure twice, cut once" you should 'model twice, code once'. I have a immense conviction in the power of a clear conceptual model, and the business benefits that come from clarity of thought in your product design. I've worked with companies that have clear conceptual models and good system design, in those cases the product sells itself, customer support is required rarely, and developing new features is easy. In cases where the company has a product that is confusing, way more salesmanship needs to occur to convince people the product is worthwhile, customer support is required constantly, and developers are frustrated and slowed down by the concepts they have to architect the system around.

Even if you've gotten off on the wrong foot, there are good strategies for addressing conceptual debt, and transitioning your product to a new mental model that is intuitive for users. For now hopefully you find the term 'conceptual debt' useful for your own design conversations. In a subsequent post I hope to go through some examples of conceptual debt, how you can identify if there are conceptual issues, and what sort of strategies you can use to transition your product to a better conceptual model.

I also hope that this post can help articulate some of the business motivations for why clear design at the modeling stage is important.
