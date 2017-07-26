# Measuring Code Quality With Test Coverage Metrics

_Captured: 2017-06-02 at 00:19 from [dzone.com](https://dzone.com/articles/measuring-code-quality-with-test-coverage-metrics?edition=304112&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-01)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Test coverage and code quality are two of a handful of fundamental metrics used to analyze, track and measure the effectiveness of an IT project or initiative. Both test coverage and code quality are interlinked in a way few other metrics are. For instance, one of the ways we measure code quality is by looking at corresponding test coverage. Yet questions lurk around how effective it is to use test coverage metrics to measure code quality. So in this post, we'll take a critical look at this practice. We'll do this by reviewing the generally accepted view about measuring code quality with test coverage metrics, and how you can apply a solution that works for your situation.

## The Elephant in the Room - Test Coverage

Let's address the elephant in the room first - namely, test coverage. How much test coverage is adequate?

Granted - adequate test coverage helps improve your chances of catching all the critical/high priority bugs. This isn't just a grandmother's tale but actually a pretty reliable yardstick to build confidence about your IT system's code quality.

However, the major source of disagreement in the industry about test coverage, seems to be centered on 'how much is adequate?' Theories vary - from 60% to 80% to even 100%. Each proponent has a valid argument for why they think a certain amount of test coverage is enough or not enough.

The one thing nobody seems to be discussing: What do you measure test coverage against? Don't get me wrong - everyone does have a traditionally accepted basis for measuring test coverage - the number of lines of code in the software being tested. Is that the right measure though? That is precisely what we'll attempt to answer today.

## Test Coverage Measured Against Lines of Code

How does this work? You simply take:

  * (A) the total lines of code in the piece of software you are testing, and
  * (B) the number of lines of code all test cases currently execute, and
  * Find (B divided by A) multiplied by 100 - this will be your test coverage %.

For example, if the total lines of code in a system component is 1000 and the number of lines being executed through all existing test cases is 650, then your test coverage is: (650/1000) * 100 = 65%

What is the generally accepted 'sufficient' test coverage when measured by number of lines of code executed? The consensus hovers around 80% - higher for critical systems (definition of critical may vary by industry, geography, user base, etc.).

The important question is: Does this metric work? Hmm - that's a toughie. I scoured internet forums for an answer, and found that generally, people think 80% is adequate. Then again, there is the question of whether you're using good tests rather than those that aren't really useful for coverage.

### What Do Good Tests Look Like?

That's not very difficult to answer. A good test looks to trace a requirement to fulfillment. Both happy and unhappy flows can be good tests.

So, how do you ensure that you have mainly good tests to improve test coverage? Before we answer that question, let's look at the more important one.

## What Should You Really Measure Code Quality Against?

Test coverage - of course. But how do you really measure test coverage?

  * Popular answer: The number of lines of code executed by test cases.
  * Correct answer: Well, that's where it gets interesting.

### Measuring Test Coverage by Number of Lines of Code Executed

While traditionally leaned upon by developers, testers and project managers alike, I've been questioning the efficacy of using this method to measure coverage. Why? As [this forum thread](http://softwareengineering.stackexchange.com/questions/192/is-test-coverage-an-adequate-measure-of-code-quality) will tell you, ensuring 100% coverage in terms of lines of code executed doesn't really get you a quality product.

Then what does? As I've said before, good test cases and adequate test coverage. To achieve both, you need to look critically at your points of reference.

## Improving the Ratio of Good Test Cases in Your Test Repository

A good test case traces a requirement (happy and unhappy flows included) to fulfillment. All you have to do to ensure you mainly have good test cases is to establish [Requirements Traceability](http://reqtest.com/testing-blog/5-key-benefits-of-using-a-traceability-matrix-to-stay-on-top-and-in-control-of-your-project/).

My team achieves traceability in my projects by clearly mapping out test scenarios to cover all requirements in scope for that release, project, iteration, or sprint. By establishing requirements traceability, I know - at any given point in time - test coverage by requirements.

In Agile projects, given you're supposed to only focus on requirements intended for the next immediate release, achieving 100% test coverage by requirements should be fairly straightforward if you use an elementary traceability matrix. If you are only testing to requirements, you should only have good test cases in your repository.

Now to the next challenge - adequate test coverage.

Well, I started this section by NOT telling you that the correct answer is the number of lines of code executed by test cases. Why did I do that? Because I don't believe that is the correct measure of code quality. If you've still got 'Why?' on your lips, so I'll try and answer to that.

## How Do You Measure Code Quality With Test Coverage?

Requirements traceability gives you a reliable way to build good test cases. So, let's extend that for a minute to think about why that is. If you only write test cases that can trace back to a requirement, you're effectively eliminating any redundant, unnecessary test cases. This improves the efficiency of your team's testing efforts.

Now, if you turn that around, what you'd get is this: if you ensure 100% of your requirements are covered by test cases, then you have all the test cases you need. Interesting, right? Then again, how do you ensure you have 100% accurate requirements? What if some requirements are incorrect, or missed? Well, as they say, "A high-quality product built on bad requirements is a poor quality product."

The focus then shifts to ensuring you have high-quality user stories that cover all functional and non-functional requirements. A cursory search on the internet will tell you what you need to ensure all your requirements are captured adequately and effectively.

## Test Coverage in the World of Test Driven Development

Let's consider how I run my average Agile project (week-long sprints as an example).

### Sprint - Day 1

My Scrum team uses the planning session to shortlist the top x stories on the backlog for delivery. Each of the stories has been elaborated and story pointed in readiness for the planning sessions (through ongoing backlog grooming sessions). A Scrum Tester (or testers) picks up the freshly minted sprint backlog to map out all the test scenarios they expect to cover with their test cases. These scenarios are then handed over to the developers who are already plugging away at code.

### Sprint - Day 2

By this time, Scrum developers have made some initial headway with dev planning and kick off, and have had a chance to get an overview of the requirements and test scenarios for the sprint with the bas and testers. The testers have completed scripting new test cases or copying over existing test cases from a case repository as applicable, to cover off all the test scenarios. They've also identified both happy and unhappy flows, and prioritized these. And finally, they've mapped the test cases back to the source requirement, establishing traceability. By this point, the testers know if all the requirements for the current sprint have been covered by test cases.

### Sprint - Final Day

Scrum developers have used the test scenarios and detailed test cases to guide their effort at coding, and have unit tested the code with these test cases as well. By the time they deploy to an integrated test environment for end-to-end functional testing, most of the easy to find, unseemly bugs have been found. Scrum testers have also begun to execute end-to-end tests using these test cases, and help identify the high/critical bugs that prevent a story from being delivered in that sprint. When we get to the demo and retrospective, usually all high and critical bugs will have been fixed, with other unresolved bugs being prioritized for future resolution as necessary (we always end a release by mopping up most of these 'other' bugs with a spike).

As you can see, by the time we get to the end of a sprint, or a release, my team have a way of ensuring all requirements are covered adequately by tests, and that we meet exit criteria from testing to release (e.g.: no high/critical bugs, 100% test case execution, 95% tests passed).

With Test-Driven Development, this is truly achievable. And if you are able to demo a working, almost-bug-free product every Sprint, and follow this up with mop-up spikes to fix the remaining unseemly bugs, my experience suggests you're in a good place to go to release.

## So, What Should Code Quality Really Be Measured Against?

My response: Both requirements coverage and number of lines of code executed. Why? To be frank, I believe ensuring 100% requirements coverage is adequate. After all, with Agile, you're supposed to only work on the high priority requirements for a release all the time, thereby reducing waste - of effort, time, money.

Then again, humans aren't perfect. Bad requirements could sneak into your scope. Good requirements could be missed. You may not discover this until late into your project. We can't always guarantee 100% accuracy with requirements.

On the other hand, I've seen that reviewing test coverage by lines of code executed helps judge code quality at a superficial level. For instance, if you have achieved 100% requirements coverage with your tests, and passed all exit criteria for release, and yet find only 65% of your code is covered in your tests, why is that?

An extreme example, I agree, but this is probable. And it could be a combination of poor requirements quality and wasted coding effort. It's quite common to encounter projects where developers have written so many more lines of code than is necessary. The reasons could be many, and some justifiable, but I constantly find 'excess code' as an issue for a lot of my clients' projects. Coding effort veers away from the requirements, and developers spend precious resource writing unnecessary lines of code.

So, is it true by corollary that if a developer were to strictly follow agreed scope, 100% of the code will be covered by tests? Not necessarily. This, again, is down to inadequate coaching for developers to write efficient code - i.e., only write the code necessary to deliver a requirement. Even then, there may be scenarios where 100% coverage may not be achievable or necessary.

The goal, therefore shouldn't ever be to achieve 100% code coverage - or any specific number like that. Although when combined with 100% requirements coverage, you should be able to find that code coverage by default hovers in the high 80s and even low to high 90s.

## What Did We Learn?

Code quality is high on everyone's agenda. In an era of increasing cost of resource and tightening budgets to deliver, it's imperative to measure and track code quality to better understand your team's efficiency, and where they can improve.

You should use every tool at your disposal to achieve your target code quality metrics. Tracking the number of executed lines of code against the total lines of code is one option. But that alone will not help you ascertain either adequate test coverage or actual code quality.

You should rely on complementary, and at times more powerful ways to measure code quality and test coverage. You can achieve this easily by considering requirements coverage in your tests, which can directly lead to better code quality - instantly!

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
