# 5 Code Review Tricks the Experts Use - Based on 3.2 Million Lines of Code

_Captured: 2017-03-01 at 02:55 from [dzone.com](https://dzone.com/articles/5-code-review-tricks-the-experts-use-based-on-32-m?edition=271922&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-28)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

## **Getting Started with Code Reviews: Here are a Few Tips to Help You do it Right**

One of the work methods you'll find in a growing number of companies is code reviews. While some might not like the idea of co-workers going through their code, others embrace it as a way to grow, learn, or simply prove how awesome their code is.

In the following post, we'll go over some of the concepts of code review, highlight a few of the tools that are used in the process, and share our own experience with it. Get ready to examen your coding skills.

## What is a Code Review?

A code review is "systematic examination of computer source code." This process aims to help find errors that might have been missed during the development phase, and improve the overall quality of the code and the product.

It's like getting a second opinion on your code before you decide to move on with it. There are a number of review types, and the top 4 are:

  * **Pair programming** - 2 developers that work together writing and observing the code, as it's typed, switching positions as they progress
  * **Informal walkthroughs** - The developers are lead through the product, allowing them to ask questions and comment on issues before they happen.
  * **Tool-Assisted** - The review is done through code review tools.
  * **Formal inspections** - Looking for defects using a defined process.

It doesn't matter which type of code review you choose, the workflow stays the same: writing code, reviewing it, applying changes and so on until it's ready for the next phase. The amount of cycles needed for each piece of code can alter according to deadlines, the importance of this specific feature, or the amount of nitpicking included.

## How Do You Do It?

A few years ago Cisco did a large (some might say, the largest) [case study](http://support.smartbear.com/support/media/resources/cc/book/code-review-cisco-case-study.pdf) on lightweight code review processes. The 10-month study is based on 2,500 reviews and 3.2 million lines of code, that were written by 50 developers. It elaborates on the values and method of code reviews, as well as how they should be handled inside the company. Here are a few takeaways we learned from it:

### 1\. Set the Tone

First of all, since the code review process might sound a little intimidating at first - asking others to find the errors and issues in your code - it's important to know what you're doing.

You have to build a plan, talk with the dev teams about it, and explain how to give and receive a good or a bad review. In order for this process to work, it's important to keep a non-threatening, collaborative environment in the team.

A good place to start is by letting everyone know that there's no harm in finding errors. The goal is not to bring a certain developer down by "bashing" his code but help everyone understand how they can write it better.

### 2\. Comment All the Things!

The first few code reviews might be harder, but not just for those who are being reviewed. If you want to help your teammates understand your code and workflow better, you should add comments to your source code.

Not only will it help others review you better, it will make the code smarter and those who'll arrive after a few weeks, months, or even years will know what you were trying to do.

### 3\. Line and Time Management

Code review is important, but it's critical to remember that it's not the most important thing you have to do. There's a long list of features to build, lines of code to write, and you don't want yourself or your team to spend the whole day reviewing each other.

According to Cisco, in order to get optimal effectiveness, developers should review fewer than 200-400 lines of code (LOC) at a time. It also affects the ability to find defects within the code itself. The following graph shows the defect density against the number of lines of code under review that supports this rule.

![density](http://384uqqh5pka2ma24ild282mv.wpengine.netdna-cdn.com/wp-content/uploads/2017/01/density.png)

In addition, Cisco points out that the optimal inspection rate is less than 300-500 LOC/hour. This rate allows developers to take their time with the review, analyze it, and find the issues that might be in it.

When reviewing at a faster rate of 400-500 LOC/hour, the graph shows a severe drop-off in effectiveness, and when the rate goes over 1000 LOC/hour, you can be pretty sure the reviewer is just scrolling through the code without actually checking it.

![defect](http://384uqqh5pka2ma24ild282mv.wpengine.netdna-cdn.com/wp-content/uploads/2017/01/defect.png)

How much time should you actually assign to each review? 60 minutes is a good, round number that you should focus on. Also, after an hour you'll simply grow tired of the task and won't be as efficient in finding errors and defects.

### 4\. Goals, Goals, Goals

Getting the team on board with code reviews is a hard task. It has to be a part of the daily schedule, and go hand in hand with the existing tickets and assignments each team member has. We know the drill - there's always something much more important to do.

One method of overcoming this is assigning a review as part of the ticket. That way, a reviewer has to go over the code in order to mark the task as completed. It helps the team to gain a wider view of the daily/weekly tasks, know what everyone is working on and, of course, add the code review to their workflow.

Another method is setting goals and measurements for the review process itself. Once you define specific goals, it will be easier to see when peer review is really achieving the results you require.

These goals can be anything, from "reduce support tickets" through "get lower bounce rate." The only rule here is that it has to have a quantifiable measure, and not a vague "fix more bugs."

Once you've set the goals, each member of the team will be able to create his own checklist of points he should address when writing and reviewing code. Keep in mind that goals are dynamic and adjustable, and as your code review process grows you'll have a better idea of what you're looking to solve with it.

### 5\. See it Through

The team is on board, everyone is sharing their knowledge, and code is being reviewed. That's awesome, but what happens next? The review part is pointless unless the code is actually being modified and fixed accordingly.

It might be silly to point out the fact that you have to fix the errors in the code, but it's important. Issues that are found during the review are not a part of your usual testing process, and they might "get lost" and not be fixed.

Make sure that every issue found as part of the code review is known by the original developer who wrote it, and that they actually fix it. This part might be a little tricky if you're just getting started with code review, but important nonetheless.

This can be accomplished by reviewing tools such as GitHub's Code Review, Review Board, Upsource by JetBrains, and others that show the changes in the code, allowing you to comment on them, change, or simply decline them.

## Why Should You Do It?

There are a lot of reasons why you should apply a code review routine in your team. It helps you see design issues and fix them before deploying the code, adjust the code according to the company's design (if it exists) and it helps to make your code and application better. It also takes part in the company's culture, helping juniors interact with the seniors and vice versa while creating a nurturing and a patient work environment.

While some dev teams prefer to have the tech lead review every piece of code, others might embrace the peer review concept. In the latter case, teammates review each other's code before pulling it into production, or before handing it to the tech lead.

Getting started with code review is not an easy decision and an even harder task. It's even harder when you're thinking about letting the teams review each other, and you have to build your game plan beforehand.

## How Do We Do It?

Full disclosure: we at [OverOps](https://www.overops.com) had to do a lot of research before "opening up" our code review routine to peer code reviews. We talked with other companies, read some case studies, and found various opinions and methods on the web.

Our conclusion was that it's important enough for us to give it a go, and started doing peer code reviews in our teams. We're still taking our first steps, but we've collected some [guidelines](https://docs.google.com/document/d/101FGZ0B1QqrPKl5F9x9-2vpr4xm6ku8sGqG1nALRwKA/edit?usp=sharing) to help everyone get on board. It's heavily based on Cisco's research, along with '[Code Review Best Practices](https://www.kevinlondon.com/2015/05/05/code-review-best-practices.html)' by Kevin London and '[The Zen of Code Reviews: Best Practices](https://www.simple-talk.com/dotnet/net-framework/the-zen-of-code-reviews-best-practices/)' by Michael Sorens.

## Final Thoughts

Code reviews can be a big part of your company's workflow and culture. Not only will it help creating code standards for current and future team members, it will also allow everyone to think of the design before writing new features or adding lines to existing code.

With that being said, it might not be a good fit for everyone. Smaller teams with tight deadlines, startups working in bootstrap models, or even big companies who simply don't know how to do it right. It's not a decision you should take lightly, and just like it can help your team, it can also cause it to break over ego wars.

Spend the time to do the right research, talk with your team members and understand - is this the right move for your company and product?

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
