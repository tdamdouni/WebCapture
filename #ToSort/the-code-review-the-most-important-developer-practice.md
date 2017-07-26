# The Code Review: The Most Important Developer Practice

_Captured: 2017-07-10 at 19:52 from [dzone.com](https://dzone.com/articles/the-most-important-developer-practice?edition=306243&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-10)_

Discover how to [build scalable and maintainable UI tests](https://dzone.com/go?i=222241&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Febooks%2Fbetter-test-design%2F%3Fsr%3Ddzone%26md%3Dcontent-synd) to optimize your Agile workflow. Brought to you in partnership with [TestComplete by SmartBear.](https://dzone.com/go?i=222241&u=https%3A%2F%2Fsmartbear.com%2Fproduct%2Ftestcomplete%2Foverview%2F%3Fsr%3Ddzone%26md%3Dad)

So, what is the most important practice you can implement within your development team?

It should be something that makes each developer better while helping your team to gel and identify problem areas. Ideally, this should also help reduce the introduction of technical debt, reduce existing technical debt, and improve code quality.

What single practice can do all that? Code Reviews.

Before we discuss the code review practice further, I want to draw your attention to the following Twitter poll from [Stephanie Hurlburt](https://twitter.com/sehurlburt), which inspired this blog post:

> When you write and/or submit code for review, do you feel emotionally vulnerable? [[poll](https://twitter.com/sehurlburt/status/859108203056857088)]
> 
> ![Poll Results](https://dzone.com/storage/temp/5823674-screenshot-twittercom-2017-07-05-17-20-16.png)
> 
> > _Poll Results_
> 
> -- Stephanie Hurlburt ( [@sehurlburt](https://twitter.com/sehurlburt)) [May 1, 2017](https://twitter.com/sehurlburt/status/859108203056857088)

Based on nearly 2,000 Yes/No votes on this poll, 60% of the respondents indicate that they _feel emotionally vulnerable_ when submitting code for review.

Let that sink in for a moment.

This means that the majority of developers are _emotionally attached to their code_. It turns out this is really the secret sauce of what makes code reviews powerful -- it forces your developers to engage with one another at an emotional level. Of course, this also means that code reviews require great care to be established successfully.

![Code Quality 3 \(XKCD #1833\)](https://imgs.xkcd.com/comics/code_quality_3.png)

> _[Code Quality 3 (XKCD #1833)](https://m.xkcd.com/1833/)_

## Getting Started

How should your team go about implementing a code review practice?

Start by making sure that you are introducing code reviews universally, as a way to strengthen your team and improve code quality. Never implement code reviews as a direct reaction to team performance as this will make it feel punitive rather than constructive.

It is also important to be sure you clearly understand your goals. Let's explore some key objectives of a code review to help answer this question.

### 1\. Learning Opportunities

It's hard to solve problems in a vacuum. Often our very best ideas and innovations are borne of necessity. As developers, this means that the code we wrote as a part of solving a particularly challenging problem may be one of our gems. And the best time to share this with others is right after we wrote it. Code reviews give an opportunity for every developer to teach others the things they have learned while solving a particular problem.

On the other hand, code reviews also provide a framework for the team to coach the coder and help him improve. It's a great coaching tool, and very handy when onboarding new developers to your team.

### 2\. Normalize Failure

Few things empower newer team members or younger coders more than spotting a bug introduced by a senior developer. It helps everyone realize and accept that everyone makes mistakes. It's important to understand that failure, mistakes, and bad approaches are just part of being a developer. We need to normalize the failure and discovery process.

The code review also serves as a safety net which can empower developers to try new things, since they know it will receive adequate verification.

This is important because those who no longer fear taking risks and making mistakes tend to outgrow and outperform those who only work within their comfort zone.

### 3\. Knowledge Transfer

In many companies and on many projects, not every developer is intimately familiar with every section of the code. Reviews help keep everyone on the same page and can allow developers to collaborate to identify areas of similar functionality that may need to be consolidated or differentiated. This is a great way to help avoid technical debt in the form of duplicated implementations of a rule, feature, or algorithm.

### 4\. Team Bonding

A great way to get a team to bond is to get them exploring and solving challenging problems as a team. Taking turns being emotionally vulnerable can build trust. Code reviews get developers talking together about problems, challenges, coding styles, and other topics of interest to developers (that will probably bore the rest of your team to tears).

### 5\. Code Quality

Code reviews absolutely improve code quality. It is one of the very cheapest ways to spot faulty logic, invalidated assumptions, memory leaks, or other potential defects. Developers can work together to ensure each contribution follows best practices and team coding standards.

However, you'll note that this isn't #1. It's pretty far down my priority list of what you should target as the goal of your code reviews. The reason is that there are lots of other things that can improve code quality which can be automated and reproduced -- such as linting, static code analysis, and unit tests.

## Implementation

You'll need some team agreements to make sure this goes smoothly. Things like:

  * Live demo (the coder presents her code) vs. online comments (the reviewer leaves feedback file-by-file and line-by-line, such as in a Pull Request).

  * How many reviewers can/should/must participate and approve?

  * Agree on a time frame by which the review must be completed.

  * Identify a safe word. Seriously. The coder needs to be able to tap out of a review (at least for a time) if they start to get [emotionally] overwhelmed by the feedback.

  * Minimize the total number of comments in an online review. Consider setting a threshold above which the reviewer and submitter must discuss before proceeding.

  * Limit the number of participants in a live review, to avoid overwhelming the coder with feedback.

  * No exceptions. Everyone must submit their code through review. Every time. Otherwise, you're not actually performing mutual team code reviews, you're implementing performance evaluations.

  * Strict policy on no teasing, mocking, or insulting. Work with your team on how they provide feedback. Work on providing feedback in neutral language that is not accusatory (e.g. "We could try" instead of "You should", or "This might be more efficient" instead of "Your approach is inefficient").

### Things to Keep in Mind:

#### Don't Nit Pic.

Unless you're writing life-or-death software (missile controllers, pacemakers, auto pilot systems, etc.) you probably don't need perfection. Don't reject a pull request 5-6 times for personal stylistic preferences.

#### Someone Needs to Be Responsible for Documenting Stylistic Decisions That Are Made During Reviews.

I suggest the [YAGNI](https://martinfowler.com/bliki/Yagni.html) _(You Aren't Gonna Need It)_ model for coding standards -- only write it down when it's become an issue, but once you make a decision to do something a certain way, make sure it's communicated. Ideally, build this decision into your linter or other static code tools. One reason this documentation is important is that it helps communicate to the entire team when feedback is a personal style opinion versus an agreed-upon team standard.

### Get Started

At the end of the day, it's important to just get started! You can always implement improvements to your process over time.

Good luck! Please let me know about your code review experiences, good or bad, and how it has impacted your team.

[Overcome the weakest link in your automated testing cycle](https://dzone.com/go?i=222242&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Febooks%2Fovercome-the-weakest-link-in-your-automated-testin%2F%3Fsr%3Ddzone%26md%3Dcontent-synd) to increase test speed and coverage. Brought to you in partnership with [TestComplete by SmartBear.](https://dzone.com/go?i=222242&u=https%3A%2F%2Fsmartbear.com%2Fproduct%2Ftestcomplete%2Foverview%2F%3Fsr%3Ddzone%26md%3Dad)

Opinions expressed by DZone contributors are their own.
