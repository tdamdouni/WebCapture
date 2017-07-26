# Tips for Fixing Open Source Bugs

_Captured: 2017-04-14 at 20:40 from [dzone.com](https://dzone.com/articles/tips-for-fixing-open-source-bugs?edition=290908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-14)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

Support isn't sexy, but it's necessary. How open source software is supported is just as important as how well it works. Given the choice between building awesome new features or carefully reading and responding to 10 bug reports, which would you choose? Which is more important? When you think of Open Source maintainers what do you see? I see issues. I see dozens of open bug reports that haven't been responded to in days. I see a pile of feature requests waiting to be worked on. Now when I open those issues, I see maintainers spending most of their time trying to get the information they need. "What version are you using?"; "was it working before"; "can you give me an example app?" Would you rather maintainers spend time asking for minute in-bug reports or fixing issues?

When I think of open source bug reports, I think of hospitals. A bug report is like a sick patient walking into an emergency room. No one knows exactly why they need to get better. They have self-reported symptoms, but more information is needed. When someone goes into an ER, they don't immediately go to a thoracic surgeon to get their blood pressure taken. Instead, they go to someone that records their vitals, takes care of their paperwork, and then makes sure the right doctor is assigned to the case. Hospitals call this process "triage," from the French "separate out." This person or team of people doesn't need to know exactly what is wrong with you, they only need to know what information the doctor will need. Every minute someone spends on triage is an extra minute someone else gets to dig into the root problem.

Triaging bugs is a necessary skill for any open source maintainers, whether they're working on a newly minted library or helping out with a 10-year-old framework. It's also a skill that can be picked up relatively quickly without years of required programming knowledge. If you want to get started in Open Source but are worried you're not ready, triage can be a great first step.

## Getting Started

First up, consider the Open Source software you use. Think of the languages, and then think of any open source libraries you use. For example, if you're a Python programmer you might use [Django](https://www.djangoproject.com/), the [Requests library](http://docs.python-requests.org/en/master/), and a whole lot of [other packages](https://www.djangopackages.com/). Pick a few that you think are very popular. These projects will have a larger existing team and you'll get good experience from them, however, you'll also want to pick a few smaller projects. While you might get lost in the crowd with a larger project, one person can make a huge impact on a smaller one.

Once you've picked a few libraries, find their issue trackers. Try to think of a good trigger when you'll be able to spend some time on open source. Maybe it's every day in the middle of your morning coffee, or right after your once-a-week team stand up, or maybe you can use the time right before your once-a-month community meet-up. I maintain an [Open Source project that sends issues to my inbox](https://www.codetriage.com/). Find a consistent schedule and pace that works with your life.

When you sit down to triage, make a goal. Maybe you want to find 5 issues to comment on. What exactly should you say? There are 3 states to an issue:

  1. A bug is reported.

  2. Extra information is gathered to reproduce the bug.

  3. If the bug can't be reproduced GOTO 2.

It's your job to gather information and move towards a resolution. Let's look at some common issue types and things you can do to help.

## Stale Issues

Issues have a shelf life. If they're not actively being worked on, they can go bad. Maybe the original reporter found a work around, or maybe the bug resolved itself.

To find issues, sort by "updated at" if the issue tracker allows for it. Go through a few of them and leave a comment:

> Can you confirm this is still an issue?

If the issue is really old and someone already did that, you can push for the inactive issue to be closed:

> There is no activity here for the last 2 months, let's close this issue for now and re-open if needed.

An issue is only good or as helpful as the people working on it. If the issue isn't important enough for the original reporter to care, there are likely more pressing problems that maintainers should focus on. Closing an issue isn't a finality, if the problem comes up again, the issue can be re-opened or referenced by a new issue. Often if a thread goes on for too long it can be difficult to easily scan all the conversations; sometimes starting fresh is the best way to move forward.

## Regressions

When someone's program was working but after a version update no longer works, it's a regression. These are usually the easiest bugs to work on as a maintainer. Usually, these bugs will say something like "it worked before" but not give specifics, which is where you can come in:

> What version are you using now? What version were you using before when it was working?

Usually, these reports will have some kind of reproduction instructions. Once you find the version numbers, try to reproduce the problem. Time box it to maybe 5 or 10 minutes so you don't sink too much time into the problem. Take notes. If you run into any problems or questions when trying to reproduce the issue, write them down. 99% of reports will not include enough information to reproduce the bug. To the reporter it's almost impossible to NOT hit the bug, they will give you wide sweeping brush strokes and expect you to hit the bug just as they did. In reality, they're probably hitting a stress case or made an assumption that most other people don't. Your job is to find that assumption.

If you can't reproduce the problem, you've got two options. Either you can report back with detailed information about how you tried to reproduce the issue and how it didn't work. Hopefully, this will jog the reporter's memory and they will point out a crucial step you missed. The second takes more time from the reporter but, in my experience, it will save everyone time in the long run.

> Can you please attach a small example app that reproduces the problem?

If the original reporter makes a new repo with the minimal artifacts required to reproduce the problem, you might still need to have some back and forth with them, but it will be much less. If they don't want to make an example app, tell them about how you couldn't reproduce and remind them that normally if a bug cannot be reproduced it cannot be fixed. People triaging and fixing open source bugs have limited time, the faster it takes them to reproduce the problem, the faster they can fix it. If a problem is important enough to you to report, it is important enough to report well, which means going the extra mile and including an example app.

If they already included an app, try to reproduce the problem and report back if it's valid or not. When a maintainer sees the issue, and if they know someone else reproduced the problem, they'll know they can reproduce it as well. It might not sound like much, but it's really helpful.

## Trust but Verify

Reading bug reports is a bit like reading a story written by an [unreliable narrator](https://en.wikipedia.org/wiki/Unreliable_narrator). They all mean well, but submitting bug reports is as much a skill as triaging bugs. Half of your job is education and coaching bug reporters on what a good bug report looks like. Likewise, it can be tempting when you see a report that looks like a "Usual Suspect" to declare the underlying problem code without verification.

When someone comes along to look into fixing a bug, we want them to have a consistent narrative. One thing that can help with getting this information is a good rapport with the person submitting the bug. You can thank them for their time and their report. If they have follow-up up questions about the triage process ("why exactly do I have to make an example app after I gave you reproduction instructions?") remember that this might be the first issue they've ever opened. We're all on the same team and working towards the same goals of making our open source software better. Humans are a large part of software, and they all come with emotions. When everyone is level headed and respectful is when the most gets accomplished.

## Pull Requests

A Pull Request (PR) is a bug report with a solution attached. Go through the same motions. Make sure you understand the problem and if there isn't a linked issue ask for a reproduction case. In addition, see if the coding style matches the rest of the project. Does the PR come with tests or a CHANGELOG attached? What are base things that every new feature or bugfix to the project must have?

## Not a Bug

Frequently people will open up bug reports that have nothing to do with the library or have very well documented fixes. Instead of replying "RTFM," closing, and locking the issue, put yourself in their shoes. Maybe they saw the documentation but were confused. Maybe it could be documented somewhere else? It costs you nothing to be nice and may earn a contributor in the future.

Here is an example from a [comment I made in 2012](https://github.com/schneems/wicked/issues/7#issuecomment-5425093). The behavior was unclear so I explained why the software worked as it did. I also linked to the relevant documentation and invited them to ask follow-up questions.

Every time an issue is closed you should ask yourself, why did they open that issue? There are lots of technically "not a bug" problems in software that are masked by a lack of documentation, [meaningful error messages](http://schneems.com/post/31460949407/raise-hell-better-programming-through-error-messages/), or [properly written deprecations](https://blog.codeship.com/the-straight-dope-on-deprecations/).

Sometimes issues are opened to ask questions "I want to do this, but I'm not sure how." This is a clear sign that documentation could be better. If you're looking for easy commits, look no further than writing documentation. The best stories are written by the people who experienced them. The best docs are written by users. If you don't have time to add docs, you can leave a note explaining where you think a doc change should have gone and ask the reporter to make the change. If your issue tracker is small, maybe open a new issue pointing out the documentation change. Often it's easier to just make the change.

## Nothing to Do

If you find a bug report that is active and has already been reproduced, you might not need to do anything. Great! Find another issue or take the time to read how they got from bug report to reproduction. Is there a consistent theme or phrase other maintainers use? Maybe they have their own techniques for triaging issues that you can use.

## Historian: Code, Culture, and Conventions

Over time you'll become more and more familiar with the projects you're triaging. You'll know which maintainers love fixing bugs, you'll be able to predict which maintainer will ask to trim whitespace. Every project has its own conventions. For example, I've worked on projects that don't accept any refactoring as they mess with the ability to `blame`. Some projects welcome feature proposals in issues, some don't and ask for discussions to go to a mailing list. As you see more issues, you'll see what the existing maintainers tell people who open issues. Over time you'll notice an issue almost identical to a previous one. It's good for you to provide context. If you know that another maintainer will ask for something, you can be pre-emptive and ask for it first.

Eventually, you'll start to see patterns in bugs or documentation. While you're only signing up to triage issues, for now, it's a very slippery slope to full blown bug fixing and code contribution. This is a good thing. If you already know what the other maintainers will say about an issue or a PR you open up, the process becomes a whole lot less scary.

## Start at the Beginning

While this article is a bit long, the core ideas are simple. Maintainer time is valuable. Triaging issues takes a minute of your time and saves a minute of maintainers time. Triaging is a skill you can learn with common patterns that can be easily applied. If you're still struggling with where to start I recommend going back to your list of libraries, find or add them to [CodeTriage](https://www.codetriage.com/) and subscribe.

Contributing to Open Source doesn't have to be a full-time job. If everyone chips in a little the contributions really add up. Your small contributions can make a big impact.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
