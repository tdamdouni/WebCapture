# Aslak's view of BDD

_Captured: 2017-08-11 at 06:37 from [cucumber.io](https://cucumber.io/blog/2015/03/27/aslaks-view-of-bdd?utm_content=buffer3d94d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

It's been 11 years since Dan introduced BDD to me while we were working together at ThoughtWorks, and 9 years since he published the article [Introducing BDD](http://dannorth.net/introducing-bdd/).

BDD has evolved a lot in the past decade. Dan's article is still a great read, but when I visit organisations who try to adopt BDD I see a lot of recurring problems. Many people still think BDD is a tool. Many people still think it's about testing. BDD is still poorly understood and frequently misappropriated.

Moreover, we know a lot more about what works and what doesn't work a decade later.

It's time to redefine what BDD is.

I don't claim to have the authority to do this alone. I think this is something the BDD community must do together. There is a session today at the [CukeUp](http://blog.skillsmatter.com/2015/03/03/while-its-compiling-skills-matter-interviews-tom-stuart/) conference in London that I won't be able to attend since I'm at Agile India.

This rambling blog post is my input to that discussion.

My BDD thinking is mostly influenced by the following people:

  * Chris Stevenson - Invented tests as sentences with AgileDox way back when
  * Dan North - The fathet of BDD and Deliberate Discovery
  * Chris Matts - Came up with "Given" in GWT and all that Real Options stuff
  * Liz Keogh - JBehave, Cynefin, Capability Red. Pushing BDD in new directions
  * Gojko Adzic - Brought BDD to the business folks and coined "Specification by Example"
  * Matt Wynne - Example mapping - a technique to break stories into examples
  * David Chelimsky - Hugely influential with his pioneering work on RSpec
  * Konstantin Kudryashov - Modelling by Example - bringing BDD closer to DDD

BDD needs a description that makes sense to management. What's in it for them? Why should they hire people who know BDD? Why should they try this out?

This is my elevator pitch:

> Behaviour-Driven Development (BDD) is a set of principles and practices that enables software teams to produce more valuable software with fewer bugs. BDD can lead to reduced development and maintenance costs and shorter time to market.

What I hope to achieve with this is to illustrate the _financial benefits_ of BDD.

I also like Matt Wynne's high level definition:

> BDD practitioners explore, discover, define, then drive out the desired behaviour of software using conversations, concrete examples and automated tests.

Let me try and break these high level definitions down to something more concrete...

## Deliberate Discovery

This is about learning early to fail less.

In traditional software development, learning is amplified when software is tested or put in production or in front of users. That's valuable feedback, but it usually requires the software to be _built_ before you can get that feedback. That causes significant delays in a team's learning, and that can be very costly.

What if the developers built the wrong thing? What if we could learn more before writing the defective code?

Deliberate Discovery and Exploration are principles that tell us to try to learn more _before_ we write the software. As with any principles, the practice to support this is contextual. There is one practice that I have seen work well in many contexts, and that is _Discovery Workshops_.

Some people call them Three Amigos meetings. Others call them Specification Workshops. _A beloved child has many names_ as we say in Norway.

In my view of BDD, _Discovery Workshops_ is an essential practice, and involving non-technical stakeholders as well as developers and testers is essential to make it efficient.

## Talking about examples

One of the things that come out of BDD Discovery Workshops is _Examples_. These are real-world examples of how the system should or could work, if it existed. The purpose of examples is to trigger discovery through conversations, but also to _define_ how the system should behave.

Examples should illustrate more general constraints, rules and acceptance criteria. They do not have to be written in a particular form. Some teams write examples down as Given-When-Then, but I prefer not to. I find plain language easier to have a conversation around:

> Joan has two books in her virtual basket and loses connection.

What's supposed to happen next? Does it matter what kind of books? Can she get to her basket from a new device?

## Test-Driven Development

BDD started out as TDD, replacing the word "test" with "should" to help people understand that TDD is not about testing, but about design and reflection. The word "should" might not have caught on, but we have learned that choosing the right words can have a deep impact on how we think.

When it's time to write code, BDD is no different from TDD. Write a failing test. Watch it fail. Write enough code to make it pass. Clean up your mess (refactor).

So how is BDD's TDD different? In a couple of areas:

  * BDD gives you a well-defined starting point: The examples created by the deliberate discovery process.
  * Tests that result from BDD are not unit tests, but high level tests that interact with the system at a much more granular level.

I don't consider tools like RSpec to be a BDD tool. I think of it more as a unit testing tool that is great for TDD in the _spirit_ of BDD. I used to think differently (heck, I wrote about half of the RSpec code in its early days). The reason that I have changed my mind is that a tool like RSpec (fantastic as it is) is usually used at an abstraction level below the level that the non-technical stakeholders care about, and stakeholder involvement is key to BDD in my view.

That sums it up for me. BDD according to Aslak.

  * A diverse group having conversations around examples
  * Test-Driven Development based on those examples

Now, there are many more techniques and guidelines that are helpful to to BDD well, but I'm not sure those belong in a definition of BDD itself. Here is a small dump - I have many more, but that's a subject for another blog post (or book).

People stuff:

  * Keep Discovery Workshops short and frequent. 15 min. per story, as often as you can.
  * Strive to make examples illustrate a single business rule. That keeps them expressive and valuable.
  * Don't do a big-bang adoption of BDD. Start with quick ad-hoc Discovery Workshops. Don't call them that, just ask for an example.
  * Start with the risky stuff - that's what you want early feedback on

Technical stuff:

  * Modelling by Example - enforce a ubiquitous language right into yourdomain model / hexagonal architecture.
  * Automate most of your tests through the domain, not the UI (brittle and slow)
  * Don't aim for high test coverage with BDD. It's for discovery of your domain, not for testing the implementation.
  * Learn about the test pyramid. Do most of the rigorous testing with unit tests (TDD'ed or not).
  * Use shallow depth of test (google it)
  * Give each developer and tester a completely isolated test environment

That's all. I hope some of this will help to create an updated definition of BDD.
