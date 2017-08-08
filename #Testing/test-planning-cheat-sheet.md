# Test Planning Cheat Sheet

_Captured: 2017-08-04 at 23:37 from [agiletester.ca](http://agiletester.ca/test-planning-cheat-sheet/?utm_content=bufferb4049&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

A successful whole-team approach to agile testing means lots of conversations about potential upcoming features. These might begin with a project inception, a design critique, a pre-iteration or iteration planning meeting. We need to learn so much about each feature if we're going to successfully deliver what the business, customer and users want and need.

Recently we experimented with putting together a "cheat sheet" of questions to ask in discussions about planned new features and stories. Lisa finds that referring to a list of possible questions during these conversations helps her think of good questions to ask. Not all of these questions are applicable to every feature set or story, but just looking at the list can help generate good conversation-starters. The answers may flush out hidden assumptions, and help make sure all testing activities can be done when needed.

We haven't thought of a short, catchy name yet for this "cheat sheet." We could call it "feature testing questions to remember' or "feature conversation cheat sheet for quality," but those aren't short and catchy! We welcome your ideas.

In any case, feel free to download the cheat sheet and see if it helps you generate productive conversations that help your team build shared understanding of each feature and how it can be tested.

**Name this cheat sheet: Questions to ask when discussing prospective features**

**Value to users/business**

  * What's the purpose of the story?
  * What problem will it solve for the user, for us as a business?
  * How will we know the feature is successful once it is released? What can we measure, in what timeframe? Do we need any new analytics to get usage metrics in production?

**Feature behavior**

  * What are the business rules?
  * Get at least one happy path example for each rule, and ideally also one misbehavior example
  * Who will use this feature? What persona, what particular job is a person doing?
  * What will users do before using this feature? Afterward?
  * What's the worst thing that could happen when someone uses it? (exposes risks)
  * What is the the best thing that can happen? (delighting the customer)
  * Is the story / feature / epic too big? Can we deliver a thin slice and get feedback?
  * Watch out for scope creep and gold-plating!

**Quality Attributes**

  * Could this affect performance? How will we test for that?
  * Could this introduce security vulnerabilities? How will we test for that?
  * Could the story introduce any accessibility issues?
  * What quality attributes are important for this feature, for the context?

**Risks**

  * Are there new API endpoints or server commands? Will they follow current patterns?
  * Do we have all the expertise for this on our team? Should we get help from outside?
  * Is this behind a feature flag? Will automated tests run with the feature flag on as well as off?
  * Are mobile/web at risk of being affected?
  * Are there impacts to other parts of the system?

**Testability**

  * How will we test this?
  * What automated tests will it have - unit, integration, smoke?
  * Do we need a lot of exploratory testing?
  * Should we write a high level exploratory testing charter for where to focus testing for this feature/epic?
  * Do we have the right data to test this?
  * Does it require updating existing tests, or adding new ones? If new ones, is there any learning curve for a new technology?
