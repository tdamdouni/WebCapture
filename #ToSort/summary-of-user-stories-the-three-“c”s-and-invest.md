# Summary of User Stories: The Three “C”s and INVEST

_Captured: 2017-01-27 at 01:57 from [linkis.com](http://linkis.com/www.agileadvice.com/LIceO?next=5&page=6)_

# **Learning Objectives**

Becoming familiar with the "User Story" approach to formulating Product Backlog Items and how it can be implemented to improve the communication of user value and the overall quality of the product by facilitating a user-centric approach to development.

## **Consider the following**

User stories trace their origins to [eXtreme Programming](http://en.wikipedia.org/wiki/Extreme_programming), another Agile method with many similarities to Scrum. Scrum teams often employ aspects of eXtreme Programming, including user stories as well as engineering practices such as [refactoring](http://en.wikipedia.org/wiki/Code_refactoring), test-driven development ([TDD](http://en.wikipedia.org/wiki/Test-driven_development)) and [pair programming](http://en.wikipedia.org/wiki/Pair_programming) to name a few. In future modules of this program, you will have the opportunity to become familiar enough with some of these practices in order to understand their importance in delivering quality products and how you can encourage your team to develop them. For now, we will concentrate on the capability of writing good user stories.

A User Story has three primary components, each of which begin with the letter 'C':

**Card**

  * The Card, or written text of the User Story is best understood as an invitation to conversation. This is an important concept, as it fosters the understanding that in Scrum, you don't have to have all of the Product Backlog Items written out perfectly "up front", before you bring them to the team. It acknowledges that the customer and the team will be discovering the underlying business/system needed _as they are working on it_. This _discovery _occurs through conversation and collaboration around user stories.
  * The Card is usually follows the format similar to the one below

> As a <_user role_> of the product,
> 
> I can <_action>_
> 
> So that <_benefit_>_._

  * In other words, the written text of the story, the invitation to a conversation, must address the "_who_", "_what_" and "_why_" of the story.
  * Note that there are two schools of thought on who the <benefit> should be for. Interactive design specialists (like [Alan Cooper](http://en.wikipedia.org/wiki/Alan_Cooper)) tell us that everything needs to be geared towards not only the user but a user _Persona _with a name, photo, bio, etc. Other experts who are more focused on the testability of the business solution (like [Gojko Adzic](http://en.wikipedia.org/wiki/Gojko_Adzic)) say that the benefit should directly address an explicit business goal. Imagine if you could do both at once! You can, and this will be discussed further in more advanced modules.

**Conversation**

  * The collaborative conversation facilitated by the Product Owner which involves all stakeholders and the team.
  * As much as possible, this is an in-person conversation.
  * The conversation is where the real value of the story lies and the written Card should be adjusted to reflect the current shared understanding of this conversation.
  * This conversation is mostly verbal but most often supported by documentation and ideally automated tests of various sorts (e.g. [Acceptance Tests](http://en.wikipedia.org/wiki/Acceptance_test-driven_development)).

**Confirmation**

  * The Product Owner must confirm that the story is complete before it can be considered "done"
  * The team and the Product Owner check the "doneness" of each story in light of the Team's current definition of "done"
  * Specific acceptance criteria that is different from the current definition of "done" can be established for individual stories, but the current criteria must be well understood and agreed to by the Team. All associated acceptance tests should be in a passing state.

The test for determining whether or not a story is well understood and ready for the team to begin working on it is the INVEST acronym:

I - Independent

  * The solution can be implemented by the team independently of other stories. The team should be expected to break technical dependencies as often as possible - this may take some creative thinking and problem solving as well as the Agile technical practices such as refactoring.

N - Negotiable

  * The scope of work should have some flex and not be pinned down like a traditional requirements specification. As well, the solution for the story is not prescribed by the story and is open to discussion and collaboration, with the final decision for technical implementation being reserved for the Development Team.

V - Valuable

  * The business value of the story, the "why", should be clearly understood by all. Note that the "why" does not necessarily need to be from the perspective of the user. "Why" can address a business need of the customer without necessarily providing a direct, valuable result to the end user. All stories should be connected to clear business goals. This does not mean that a single user story needs to be a marketable feature on its own.

E - Estimable

  * The team should understand the story well enough to be able estimate the complexity of the work and the effort required to deliver the story as a potentially shippable increment of functionality. This does not mean that the team needs to understand all the details of implementation in order to estimate the user story.

S - Small

  * The item should be small enough that the team can deliver a potentially shippable increment of functionality within a single Sprint. In fact, this should be considered as the maximum size allowable for any Product Backlog Item as it gets close to the top of the Product Backlog. This is part of the concept of Product Backlog refinement that is an ongoing aspect of the work of the Scrum Team.

T - Testable

  * Everyone should understand and agree on how the completion of the story will be verified. The definition of "done" is one way of establishing this. If everyone agrees that the story can be implemented in a way that satisfies the current definition of "done" in a single Sprint and this definition of "done" includes some kind of user acceptance test, then the story can be considered testable.

Note: The INVEST criteria can be applied to any Product Backlog Item, even those that aren't written as User Stories.

## **Splitting Stories:**

Sometimes a user story is too big to fit into a Sprint. Some ways of splitting a story include:

  * Split by process step
  * Split by I/O channel
  * Split by user options
  * Split by role/persona
  * Split by data range

**WARNING**: Do not split stories by system, component, architectural layer or development process as this will conflict with the teams definition of "done" and undermine the ability of the team to deliver potentially shippable software every Sprint.

## **Personas**

Like User Stories, Personas are a tool for interactive design. _The purpose of personas is to develop a precise description of our user and so that we can develop stories that describe what he wishes to accomplish._ In other words, a persona is a much more developed and specific "who" for our stories. _The more specific we make our personas, the more effective they are as design tools.[iii](http://linkis.com/www.agileadvice.com/LIceO?next=5&page=6)_

Each of our fictional but specific users should have the following information:

  * Name
  * Occupation
  * Relationship to product
  * Interest & personality
  * Photo

Only one persona should be the primary persona and we should always build for the primary persona. User story cards using personas replace the user role with the persona:

> <_persona_>
> 
> can <_action>_
> 
> so that <_benefit_>_._

**Please share!**
