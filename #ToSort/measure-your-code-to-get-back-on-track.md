# Measure Your Code to Get Back on Track

_Captured: 2017-02-04 at 19:11 from [dzone.com](https://dzone.com/articles/measure-your-code-to-get-back-on-track-1?edition=267883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-04)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

When I'm called in for strategy advice on a codebase, I never arrive to find a situation where all parties want to tell me how wonderfully things are going. As I've mentioned before here, one of the main things I offer with my consulting practice is codebase assessments and subsequent strategic recommendations.

Companies pay for such a service when they have problems and those problems drive questions. "Should we scrap this code and start over, or can we factor toward a better state?" "Can we move away from framework X, or are we hopelessly tied to it?" "How can we evolve without doing a forklift upgrade?"

To answer these questions, I assess their code (often using NDepend as the centerpiece for querying the codebase) and synthesize the resultant statistics and data. I then present a write-up with my answer to their questions. This also generally includes a buffet of options/tactics to help them toward their goals. Invariably, I (prominently) offer the option "instrument your code/build with static analysis to raise the bar and prevent backslides."

I find it surprising and a bit dismaying how frequently clients want to gloss over this option in favor of others.

## Using the Observer Effect for Good

Let me digress for a moment before returning to the subject of preventing backslides. In physics and science, experimenters use the term "[observer effect](https://en.wikipedia.org/wiki/Observer_effect_%28physics%29)" to describe an experimental problem. This occurs when the act of measuring a phenomenon changes its behavior, inextricably linking the two. This presents a problem, and indeed a paradox, for scientists. The mechanics of running the experiment contaminate the results of the experiment.

![](http://www.daedtech.com/wp-content/uploads/2017/01/Giant-telescope.png)

To make this less abstract, consider the example mentioned on the Wikipedia page. When you use a tire pressure gauge, you measure the pressure, but your measurement lets some of the air out of the tire. You will never actually know what, exactly, the pressure was before you ran the experiment.

While this creates a problem for scientists, businesses can actually use it to their advantage. Often you will find that the simple act of measuring something with your team will create improvement. The Agile concept of "[big, visible charts](http://ronjeffries.com/xprog/articles/bigvisiblecharts/)" draws inspiration from this premise.

In discussing this principle, I frequently cite a dead simple example. On a Scrum team, the [Product Owner](https://www.mountaingoatsoftware.com/agile/scrum/product-owner) has ultimate responsibility for making decisions about the software's behavior. The team thus needs frequent access to this person, despite the fact that product owners often have many responsibilities and limited time. I recall a team who had trouble getting this access and put a big piece of paper on the wall that listed the number of hours the product owner spent with the team each day.

The number started low and improved noticeably over the course of a few weeks with no other intervention at all.

## The Importance of Measurement

The simple act of measuring something your team does can result in improvements. That's _powerful_. We haven't even done anything with the measurement results yet.

You can probably now understand why I find it so dismaying that teams opt to skip the static analysis implementation. The simple act of setting up the tools and making their results visible can have a lasting positive effect. The concept of "gamification" builds on this idea and gives us the astonishing success of Stack Overflow, where people labor for free in the hopes of chasing "points" and "badges."

Before Scrum or Stack Overflow, famous management consultant [Peter Drucker](https://en.wikipedia.org/wiki/Peter_Drucker) purportedly said, "what gets measured gets managed." Measurement's impact transcends the observer effect and helps establish goals and means of tracking progress. Returning to the product owner example, perhaps the figure improves from two hours per day to five, but the team really wants seven. Establishing seven as a goal and examining the reasons for the shortfall can help improve things even more.

Nothing about this should mystify anyone reading. But the complexity of the workplace has a tendency to gobble up deliberate action and put us into a frantic churn of emails, meetings, and "fighting fires." Establishing measures and goals helps the team stay focused on important activities and prevents their sweeping under the rug.

## The Sins of the Past

All too often, we mistake simply identifying problems for having solutions to them. "Oh, we had way too many dependencies! We won't make that mistake again." This represents a macroscopically focused attitude -- one that will promptly get lost in the day to day activities of writing code.

As I mentioned in the beginning of this post, when teams call me, they don't pick up the phone to tell me how well they're doing. They want to know why their code got messy and how they can fix it. They want a different outcome. For this to happen, they also need specific, actionable information.

"This code has large, complex methods and classes. You're using global state extensively. You frequently write to external sources, making the code hard to test. You take an outsized number of dependencies, making refactoring difficult." And so on.

"Oh, thanks for letting us know. We'll stay away from those problems in the future." This sentiment represents an excellent start, but only a start. The team needs visible measurements of what "good" looks like.

"Fail the build if more than 5% of classes have 300+ lines. Do the same with use of global variables. Issue a warning if more than 3% of classes write to files." Now we're talking.

I really mean that. We're talking. Such rules exist not to create draconian restrictions, but to force conversations. "Hey, we've had problems with hard to test code in the past. Your commit just pushed us over the threshold of more than 3% of classes writing to files. Could we revisit our approach here?"

## Don't Boil the Ocean

Assuming that you find my argument for code metrics to be appealing, I will leave you with one final piece of advice. Avoid implementing every metric or best practice that comes to mind. You will thrash and you will give up.

Start by picking a few that seem most critical and getting those within acceptable thresholds. Once the team grows used to that and accepts it as a norm, move on to the next few. This creates a constant cycle of mastery and growth.

Measuring practices around your code is critical to your success. If you don't have measurements around your coding practice, go out and get them. Make sure that you improve at a sustainable pace so that you continuously reap the benefits.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
