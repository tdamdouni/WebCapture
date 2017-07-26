# Developing a Regression Testing Strategy

_Captured: 2017-03-03 at 22:55 from [dzone.com](https://dzone.com/articles/developing-a-regression-testing-strategy)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

Regression testing before agile was easy. Testers would gather up all of the tests ideas created during that release cycle, combine them with the old ideas, and run them one at a time till the stack of ideas was done. When software was shipped once a quarter, or every 6 months, the time that would take was easily accounted for. Today, software teams aim to release every 2 weeks, or sometimes faster.

Teams working in agile test each new function during the release cycle, maybe do some light poking the day before shipping, and then give the thumbs up. Alternately, they just do nothing and software still ships. There is a better way to approach this problem; develop a regression testing strategy.

## Why You Should Develop a Regression Testing Strategy

Every new software change introduces the potential for new problems. A user might get a new web page and submit a date format the programmer wasn't expecting. In return, that user gets an error on the page explaining things they might not understand or even care about, data loss, and browser crashes. These risks are easy to imagine and are where feature testing during a sprint shines. A tester can perform these scenarios, discover the problems, and report them. Programmers can come back over the code to fix the problems, and then build automated checks that run with the build so the team finds out fast when they emerge again.

Towards the end of a sprint, there is a mass of new features and small changes, each of which was tested somewhat on its own. Everything is OK now, right? Maybe, maybe not. There is risk hidden in the interactions of each of these changes and the rest of the product.

Software doesn't work in isolation. The authentication library interacts with user profiles, which interact with screen design and data access, which interacts with reporting. The tendrils of one feature reach out and touch other features. Sometimes in surprising ways. Regression testing is how these surprises are sometimes discovered.

## How to Create Regression Testing Strategy

One way to approach the problem of compressed time for regression testing is through socializing testing information using a 'regression board'.

![Image title](https://dzone.com/storage/temp/2532708-below-engineering-1-1.jpg)

Each member of the testing team can write a change they worked on in sprint on a post-it note and stick that note on a wall people walk by. After most of the changes are up on the wall, the notes are arranged, top down, based on what should be tested first. That list could be ordered based on perceived risk, importance to the customer, because the CEO said so, or any reason really. As other team members walk by, they can make slight rearrangements of the cards based on what they know. A programmer might walk by and add a card because she understands that changes to a user profile could potentially affect a demographics report. Different team members add their knowledge to the regression testing board based on their own unique project perspective.

When the feature work is done, and it is go time for pre-release testing, the test team can refer to that board. If there is about 12 hours of work listed on the board (assuming everything is OK and the testers don't have to spend time researching and reporting bugs) but only 8 hours before the release, there are decisions to make. Managers can make an educated decision to drop something off of the list, other non-testing staff can be recruited to help with low-risk features, or the release can be extended. The point, though, is that they can make a more educated decision.

Referring to a clear and organized list of regression testing work creates a massive shift in conversation from "There isn't enough time" to "This is what the team knows about, what is important and how much time is there".

## The Technical Side of a Regression Testing Strategy

The other side of a good regression testing strategy is technical. While developing new features, programmers can write automated checks. Eventually, culture shifts can happen to the point where a feature is not considered ready to commit till the programmer has done some amount of check building. While this isn't exactly testing, automation can show that a code change works how the programmer expects. The goal here is to help lower risk for changing code and create a system of change detection.

This is an example of one strategy for regression testing before pushing new code to production. The next step is to assess how the development team prepares for a release and find a point to improve. Most teams have a strategy, but just don't recognize it yet.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
