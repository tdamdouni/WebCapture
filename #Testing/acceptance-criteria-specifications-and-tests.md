# Acceptance Criteria, Specifications, and Tests

_Captured: 2017-08-08 at 19:02 from [www.agileconnection.com](https://www.agileconnection.com/article/acceptance-criteria-specifications-and-tests)_

Summary:

One of the benefits of agile is how it helps specify requirements. Instead of trying to predict the future with your requests, you can wait an iteration and see if more criteria are needed. This article gets into how executable specifications, specification by example, and test automation can help further improve your requirements management.

Back in the dark days before agile, a friend of mine, Tony, worked on a government project that trusted in upfront, written requirements and specifications. One day a screen Tony had developed failed testing because the specification stated that a "Please wait" icon should display while the system was accessing the database.

But database access happened very fast--far faster than the analyst who wrote the request had considered. Rather than discuss the specification, it was easier for Tony to introduce a delay so that testers (and, later, users) could admire the hourglass icon before seeing the results.

The specification Tony faced might well exist in an agile world, only instead of being a line item in a boring document somewhere, it would be part of the acceptance criteria on a story. Because stories and acceptance criteria are placeholders for a conversation--not rigid mandates--having a conversation about those requests can resolve mismatches like what Tony experienced.

This conversation isn't necessarily a single event. It can be an ongoing discussions as the testers and programmers work to build the story. As understanding improves, the story can, and will, change.

In an agile world, I would hope Tony's predicament never arises. The icon request was premature--an attempt to second-guess the future--and it created more work for the writer, the tester, and the developer. In an agile world, the next iteration could always be to add an icon if it's needed, so it is safe to postpone a decision and omit the criteria.

Even if the request did make it into the original acceptance criteria, then during the discussion about the story, Tony would get a chance to ask, "What if the database returns very quickly?" If the question wasn't asked beforehand, I would expect Tony, and perhaps the tester, to talk the issue through with the product owner. And I would expect the product owner to have the knowledge and authority to say, "There is no need to display a timer when the result is fast."

### Splitting Stories by Acceptance Criteria

One of the things teams typically find difficult is [making stories small](https://www.agileconnection.com/article/relieving-agile-tension-how-write-small-stories-still-have-value). Getting pieces of work that then can be delivered in a few days and demonstrate business benefit is undoubtedly hard. And when you've not done it before, it's harder still!

Acceptance criteria, or ACs, have a role to play here. Each individual criterion is potentially a story in its own right.

Take the first AC, write it on the back of a new index card, and write a story on the front that contains some element of the original user story. Even if you need to restrict the story in some way, you may still have something that delivers a teeny-tiny bit of business benefit--something that shows progress or advances understanding and the conversation.

In the process, decoupling the work has reduced the risk of the original story. The risk is further reduced because you now have a tiny piece of functionality that demonstrates a bigger story: an even thinner vertical slice.

  


### Specifications and Tests

In everyday conversation, IT folks use the terms _requirements_ and _specifications_ interchangeably, as if they mean the same thing. They don't.

  * Requirements are the things the customers want to achieve; think of them as a problem for the team to solve.
  * Specifications are the parameters within which the solution must operate. They are the details that can make crafting a solution hard.

Each one of your ACs will, in time, expand to one or more tests. Together, these form the specifications of the story. The front of the card spells out the requirement--the thing asked for--while the ACs and tests describe the exact parameters that define and constrain the work.

In other words, specifications are tests, and tests are specifications. After all, how can anyone know if the specification has been satisified if it cannot pass a test? (If someone tells you they cannot give you acceptance criteria, tell them the work is complete and mark it as done. The resulting bug reports will provide the missing tests.)

Automating these tests and executing them by a machine creates _executable specifications_. In truth, even a manual test script is executable after a fashion, but that execution is slow, expensive, and error-prone.

### Specification by Example

In creating your tests you need to generate some small data, you need to come up with a test scenario. This itself is an example of what the system needs to do. Such examples can be useful beyond mere tests.

Users who don't know about technology can read these examples, comment on them, and discuss their correctness. Examples can even be mentally tested, if needed. This is _specification by example_. The example models the specification.

Rather than writing a dry set of rules that state "The system shall …" and "The system must …" an example gives a better illustration: "When I show the system a picture of a square, it displays square." This example is more interesting, and more accessible to a novice.

Models and examples have more useful attributes, too. You can take other examples and mentally compare them, and counterexamples can help to determine if the original represents existing functionality or something new. If it is something new, you can add it to the test set; it will fail at first, but then you know you have work to do.

### Test Automation: More Than Fast

Specification by example and executable specifications are the key ideas underpinning behavior-driven development and automated acceptance test-driven development. More than automating tests, the real value of these techniques is in promoting meaningful conversations between different people in different roles with different experience.

  


Automating your tests makes them fast and cheap to execute, and many people think that is what test automation is all about. But is isn't.

Test automation is a game changer. Because test execution is fast, it provides feedback much sooner, so we tighten the feedback loop. Because test automation is rigorous--it's code!--it flushes out details and anomalies. Because test automation remains in place, it provides a legacy, a sort of insurance policy, which catches future problems.

Traditional tests written in verbose, boring English or a hieroglyph programming language form a barrier to conversation. When users and customers can understand tests, they become powerful communication tools for enhancing learning and understanding on all sides.

Finally, readable tests form documentation, and because the tests are executable (and get executed regularly against actual code), there is no space or time for discrepancies between specification documentation, tests, and code.
