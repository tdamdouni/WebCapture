# Exploring the Technical Debt In Your Codebase

_Captured: 2017-03-07 at 14:21 from [dzone.com](https://dzone.com/articles/exploring-the-technical-debt-in-your-codebase?oid=twitter&utm_content=bufferab1c2&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

Recently, I [posted about how the new version of NDepend lets you compute tech debt](https://blog.ndepend.com/computing-technical-debt-ndepend/). In that post, I learned that I had earned a "B" out of the box. With 40 minutes of time investment, I could make that an "A." Not too shabby!

In that same post, I also talked about the various settings in and around "debt settings." With debt settings, you can change units of debt (time, money), thresholds, and assumptions of working capacity. For folks at the intersection of tech and business, this provides an invaluable way to communicate with the business.

But I really just scratched the surface with that mention. You're probably wondering what this looks like in more detail. How does this interact with the NDepend features you already know and love?

Well, today, I'd like to take a look at just that.

To start, let's look at the queries and rules explorer in some detail.

## Introducing Quality Gates

Take a look at this screenshot, and you'll notice some renamed entries, some new entries, and some familiar ones.

![](http://www.daedtech.com/wp-content/uploads/2017/02/NDependQueriesAndRulesExplorer.png)

In the past, "Code Smells" and "Code Regressions" had the names "Code Quality" and "Code Quality Regression," respectively. With that resolved, the true newcomers sit on top: Quality Gates and Hot Spots. Let's talk about quality gates.

Many of these concern the evolution of the codebase with time. And not all of them directly address tech debt, though many do. You'll need to explore yourself, but I'll talk about some of these and how they weave into your experience.

![](http://www.daedtech.com/wp-content/uploads/2017/02/QualityGates.png)

First, understand the idea of a "quality gate." Quality gates say, "if this fails, your build should fail." Thus, you might reason about familiar concepts like code coverage by saying, "if coverage drops below 70%, fail the build."

You can now do this in ways explicitly involving tech debt. For example, consider "blocker issues." You want to fail when blocker issues crop up. These can occur as a result of you explicitly labeling them as blockers (e.g. "class bigger than 10,000 lines should fail the build"), but they can also now occur implicitly as a result of accrued tech debt.

To get a little more immediately concrete, we have "percentage debt," as shown above for ChessTDD. This metric results from computations of how long the codebase took to develop and how much debt exists. Out of the box, if tech debt accounts for more than 20% of total development time, a warning occurs. You could easily make this an error.

Some of the rules below "percentage debt" also involve debt directly in quality gates, generally in self-describing ways.

## Hot Spots

Next up, consider the new hot spots category. Here you can see a screenshot of that, with my Chess TDD codebase thankfully not triggering any warnings or failures.

![](http://www.daedtech.com/wp-content/uploads/2017/02/HotSpots.png)

Unlike the previous query group, this one concerns itself _exclusively_ with tech debt. Here, you can really navigate your codebase in terms of technical debt. "Types hot spots," for example, sorts the debt-heavy types in your codebase by the amount of tech debt computed for that type. Thus, you can use this as a quick, "where do I have the most debt" check.

The next two prioritize fixes and sort according to two different concerns: debt per type, and debt per code issue. And following that, you have a code query that I'll show in more detail. Here's the "Debt and Issues per Rule" query for my Chess TDD codebase.

![](http://www.daedtech.com/wp-content/uploads/2017/02/DebtPerRule.png)

Out of the box, it calls out the issues detected in the codebase and it sorts them by the quantity of tech debt. For example, I have many classes that could become structures and even more method names that are too long (the latter because I give unit tests very long names, and this analysis includes the test projects). But the sort places classes to become structures first because NDepend (understandably) computes that this will take longer to fix than shortening method names.

From here, I can see a nice snapshot of the tech debt in my codebase. What I have here is every issue that NDepend calls out, and the amount of tech debt it generates. Pretty powerful, huh?

## Turning Off Rules

Now, you might find yourself wondering, "what if I don't want a particular rule -- will the tech debt show up everywhere for it?" Nope. NDepend has enough smarts that you can turn an issue off and have that reflected in all calculations.

For example, recall my explanation about long test names creating an outsize number of warnings for "avoid methods with name too long." Let's say that I consider this noise and want to turn it off. To do that, I go under the "naming conventions" group and uncheck "Avoid methods with name too long."

![](http://www.daedtech.com/wp-content/uploads/2017/02/TurnOffMethodNamesTooLong.png)

With that turned off, I run an analysis and open the "debt and issues per rule" query again. I see the following:

![](http://www.daedtech.com/wp-content/uploads/2017/02/NDependQueriesAndRulesExplorerRedux.png)

No more "avoid methods with name too long" in the debt computation. Oh, and while I'm checking the effects of that, take a look at my new debt grade.

![](http://www.daedtech.com/wp-content/uploads/2017/02/NewDebtGrade.png)

My selection and deselection of rules affect this as well. You'll find, in general, that your rule settings weave in pretty seamlessly with the debt computations. And, while I don't advocate turning off rules to give yourself an A, it does provide a nice demonstration of how you can customize your settings to reflect what you prefer to see in the codebase.

## The Value of This Integration

I'll offer a sneak peek of something I intend to cover later. NDepend implements this functionality with a robust new part of its API and CQLinq oriented around issues and debt. In other words, the debt features are not a bolt-on but a first class, core part of the offering.

This counts for a lot, in my opinion. Now, instead of reasoning about things like "number of violations" and "severity" you can start to reason in units of time and currency throughout NDepend. So, sitting at your desk with a project manager, you can start to point out that certain projects or modules carry problems and create risk.

But I'd say the value goes well deeper than what you might communicate to some manager. It starts _you_ thinking about properties of the codebase in terms of time and money. And, as much as we all enjoy the language of technocracy and the programming feedback loop, thinking in economic, business terms makes us better at doing our jobs.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).

### Like This Article? Read More From DZone
