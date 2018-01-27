# Code Rewrites and How They Create Value - Stop Fighting Against It

_Captured: 2018-01-26 at 18:24 from [dzone.com](https://dzone.com/articles/code-rewrites-and-how-they-create-value-stop-fight?edition=355142&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-26)_

Planning to extract out a few microservices from your monolith? Read this [free guide](https://dzone.com/go?i=265421&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) to learn the best practice before you get started.

TL;DR - To remove doubts and questions, rewrite it.

Many, many people are confronted with the request to maintain someone else's code.

Either it's open source, and you have to make formal PR's visible to the world.

Or it's "enterprise" in-house software, and you have to make PR's visible to a work team.

Or.

It's "work group" in-house software, and you have a source that may not be under proper source-code control installed on a server where you're taking over someone else's carefully built structure of porcelain components.

In the first case -- public code -- a rewrite is a challenge. People depend on it having a well-known interface. A small change here could alienate large swaths of the user community. On the other hand. A small change here could make the project *more* useful to *more* people. This is challenging. My advice here is limited.

When we look at enterprise software, however, a rewrite won't have quite the same "blast radius."

When we look at work-group software, there is no blast radius.

## Benefits of a Rewrite

Why rewrite? Three reasons.

  1. You can understand it. (This is HUGE.)
  2. You can make it objectively better (i.e., higher PyLint scores, better documentation coverage.)
  3. You can add or expand the test cases.

The first and foremost reason -- **understanding** \-- can't be understated.

And.

It's a HUGE fight every time. The standard argument is "If It Ain't Broke, Don't Fix It."

This is, of course, based on misunderstanding the level of "broke." A delicately-balanced tower of porcelain components that worked once last month is -- in effect -- already pre-broken if any change will disturb the structure and ruin everything.

There are lots of examples.

  * The app only works with Pandas 0.12.0 and will not work with 0.13.x or the 0.22.0 you have in your default Conda environment.
  * The app only works when you provide --someoption=False, and no one can figure out why.
  * Some test cases have @skip because they don't work. But should.
  * The setup.py doesn't work and you can only run it using PYTHONPATH.
  * The default logging initialization is "somehow" not right and requires a manual override in the app.

I know. I've created all of these problems.

On one hand, we have management: "It ain't broke."

On the other hand, we have everyone else: "It's a fragile nightmare of pre-broken components that cannot be touched."

## The Script

Here's how it plays out. In the Real World.

Management: "It ain't broke. Don't fix it."  
You: "I can't make it work."  
Management: "It ran last month."  
You: "I made one small change and it doesn't run this month."  
Management: "Back out the change."  
You: "The results are then useless."

After much Grrr and Gnashing...

Management: "Identify the problems and we'll prioritize."  
You: "Here are a dozen things."  
Management: "These are too vague. Be more specific."  
You: "Here are a score of things."  
Management: "You're in the weeds. Bring it up a level to where business people can understand it."

After more Grrr and Gnashing...

Management: "What's the smallest change we can get away with?"  
You: "The one I made that broke everything."  
Management: "Let's have lots of peer review and design walkthroughs."  
You: "Cool, then you'll see how broken it is."  
Management: "Okay. Let's not. Instead, make the smallest change you can."  
You: "I made one small change and it doesn't run this month."  
Management: "Back out the change."  
You: "The results are then useless."

Can we break the cycle of uselessness?

We may be struggling with management folks who are set against fixing what's obviously broken. They're living a rich fantasy life that you can't really change.

The Grrr and Gnashing part of the dialog represents time in which useful stuff can be done. Specifically. Rewrites.

## Rewriting Strategy

There are three important parts of rewriting.

  * Understand what it's doing and why.
  * Describe it with test cases.
  * Make it objectively clear (i.e., high PyLint scores, complete documentation, etc.)

The effort often involves multiple passes. I like to describe it as **Test-Driven Reverse Engineering** (TDRE).

  1. Create (or expand) the test cases.
  2. Rewrite the code.
  3. Repeat until it's better.

It's essential to do these in order. Without test cases, rewrites are only more breakage. With test cases, rewrites are guaranteed to produce the same results as the previous mess of horrible code.

Sometimes the test cases are really a kind of "system test" where the whole application is run against some known inputs to produce some expected outputs. This is better than nothing. It supports building fine-grained unit test cases that conform to the system test case.

Other times, the test cases may be proper unit tests and the rewrites can be at a finer level of granularity. In this case, test coverage may have to be expanded to include the fragile bits. In some cases, the rewrites may be necessary to make the code testable in the first place.

Adding test cases is objectively valuable work.

Even the dumbest of "It ain't broke" managers can recognize this value. The rewrites are a beneficial consequence of adding test cases. You may be able to achieve a goal of fixing something without ever being seen as "fixing" it. All you did was improve test case coverage and improve the "design for testability."

## Costs and Benefits

Consider the cost of struggling vs. the cost of rewriting.

It's the same 80 hours of effort.

In one case, you struggled with something management insisted wasn't broken. Eventually, you found ways to make it work.

In the other case, you rewrite something management insisted wasn't broken. In the end, you actually understood it and created objective improvements in the code.

Which is better?

Measure the impact of feature releases, and of your DevOps program more broadly with full stack experimentation. [Learn how](https://dzone.com/go?i=265422&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) with this free article from CITO Research, provided by Split Software.
