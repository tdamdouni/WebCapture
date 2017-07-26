# Friction in Software

_Captured: 2017-03-01 at 02:57 from [dzone.com](https://dzone.com/articles/friction-in-software?edition=271922&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-28)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Friction can be a very powerful force when building software. The things that are made easier or harder can dramatically influence how we work. I'd like to discuss three areas where I've seen friction at work: dependency injection, code reviews, and technology selection.

## DI Frameworks

A few years ago a [colleague](https://twitter.com/bertvanbrakel) and I discussed this and came to the conclusion that the reason most DI frameworks suck (I'm looking in particular at you, Spring) is that they make adding new dependencies _so damned easy_! There's absolutely no friction. Maybe a little XML (shudder) or just a tiny little attribute. It's so easy!

So when we started a new greenfield project, we decided to put our theory to the test and introduced just a little bit of friction to dependency injection. I've written before about the [basic scheme](https://blog.activelylazy.co.uk/2012/08/30/i-can-haz-dependencies/) we adopted and the [AOP endpoint](https://blog.activelylazy.co.uk/2015/03/18/dependency-injection-with-postsharp/) it reached. The end result was, I believe, very successful. After a couple of years of development, we still had the order of only 10-20 dependencies. The friction we'd introduced was light (add a couple of lines to a single class), but it was sufficient to act as a constant reminder not to just add a new dependency because it was _easy_.

## Code Reviews

I was reminded of this recently when discussing code reviews. I have mixed feelings about code reviews: I've seen them work well, and it is better to have code reviews than not to have them, but it's better still to pair program. But not all teams, not all developers, like pair programming - so code reviews exist. The trouble with code reviews is they can provide a form of friction.

If you and I are pairing on a piece of work, we will discuss the various trade-offs as we go: do we spend time on this, do we refactor that, etc, etc. The constant judgments about what warrants attention and what can be left for another day are verbalized and agreed upon. In general, I find the code written while pairing is high in quality but also remains tightly focused on the task. The long rambling refactors I've been guilty of in the past disappear and the lazy "quick hacks" we all try and explain away to ourselves, aren't so easy to gloss over when pairing.

But code reviews exist outside of this dynamic. In the cold light of the following day, someone uninvolved reviews your work and passes judgment on whether they think it's up to scratch. It's easy to see why this becomes combative: rather than being collaborative it can be seen as a judgment being passed, on not only the code but the author, too.

When reviewing code it is easy to set a very high bar, higher than you might set for yourself and higher than you might have agreed when pairing. Now, does this mean the comments aren't valid? Absolutely not! You're right, there is a test case missing here, although my change is unrelated, I should have added the missing test case. And you're right this code is a mess; it was a mess before I was here and made a simple edit; but you're right, I should have tidied it up. Everyone should practice code gardening.

These are all perfectly valid comments, but they create a form of _friction_. When I worked on a team that relied on these code reviews you _knew_ you were going to get comments: so you kept the commit small, so as to minimize the diff. A small diff minimizes the amount of extra tests you could be asked to write. A small diff keeps most of the existing mess out of the review, so you won't be asked to start refactoring.

Now, this seems dysfunctional: we're deliberately trying to optimize a smooth passage through the review process, instead of optimizing for code quality. Worse than this, though, was what never happened: refactoring commits. Looking back I realize that the only code reviews I saw (as both reviewer and reviewee) were for feature changes. There were never any code reviews submitted for purely technical debt reduction. Sure, there'd be some individual commits in amongst the feature changes. But never any dedicated, multi-commit sessions, whose sole aim was to improve the code base. Which was a shame, because, like any legacy code base, there was scope for improvement.

Comparing this to teams that don't do code reviews, where I've tended to see more effort on reducing technical debt. Without fearing an endless cycle of review comments, developers are free to embark on refactoring efforts (that may or may not even work out!) - but at least they can try. Instead, code reviews provide a form of friction that might actually hurt code quality in the long run.

## Technology Selection

I was talking to another colleague recently who is convinced that Hibernate is still the best way to get data in and out of a relational database. I can't really work out how to persuade people they're wrong - surely using Hibernate is enough to persuade you? Especially in a large, legacy code base - the pain that Hibernate causes is obvious. Yet plenty of people still believe in Hibernate. There are even people that still believe in Spring. Whether or not they still believe in the tooth fairy is unclear.

But I think technology selection is another area where friction is important. When contemplating moving away from something well-known and well used in industry like Spring or Hibernate there is a lot of friction. There are new technologies to learn, new approaches to understand, and new risks to manage. This all adds friction, so sometimes it's easiest just to stick with what we know. Sometimes it really is the right choice - the technology you have expertise in is the one you'll be most productive in immediately. But there are longer-term questions too, which are much harder to answer: will the team eventually be more productive using technology X than technology Y?

Friction in software is a powerful process: we're very lazy creatures, constantly trying to optimize. Anything that slows us down or gets in our way quickly gets side-stepped or worked around. We can use this knowledge as a tool to guide developer behavior, but sometimes we need to be aware of how friction can change behaviors for the worse as well.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
