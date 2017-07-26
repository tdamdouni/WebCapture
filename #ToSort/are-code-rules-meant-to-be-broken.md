# Are Code Rules Meant to Be Broken?

_Captured: 2017-05-14 at 21:47 from [dzone.com](https://dzone.com/articles/are-code-rules-meant-to-be-broken?edition=298100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-14)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

If you've never seen the movie [Footloose](http://www.imdb.com/title/tt1068242/), I can't honestly say I recommend it. If your tastes run similarly to mine, you'll find it somewhat over the top.

A boy from the big city moves to a quiet country town. Once there, he finds that the town council, filled with local curmudgeons, has outlawed rock music and dancing. So follows a predictable sequence of events as the boy tries to win his new town over and to convince them of the importance of free expression. You can probably hear his voice saying, "_come on_, Mr. Uptighterton, rules are made to be broken!"

Today, I'd like to explore a bit the theme of rules and breaking them. But I'll move it from a boy teaching [the people from American Gothic](http://www.americangothichouse.net/about/the-painting/) to dance and into the software development shop and to rules around a codebase.

Perhaps you've experienced something similarly, comically oppressive in your travels. A power mad architect with a crazy inheritance framework. A team lead that lectures endlessly about the finer points of [Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation). Maybe you've wanted to grab your fellow team members by the shirt collars, shake them, and shout, "go on, leave the trailing underscore off the class field name!"

If so, then I sympathize and empathize. Soul crushing shops do exist, seeking to break the spirits of all working there. In such places, rule breaking might help if only to shake people out of learned helplessness and depression. But I'm going to examine some relatively normal situations and explore the role of rules for a software team.

### Anatomy of a Workplace Rule

Before going further, let's back up just a touch. Coding standard rules make up a subset of workplace rules in general. What makes up a workplace rule? What does it really mean?

I would argue that workplace rules consist of two essential components: convention and consequence. A rule establishes a convention, such as no smoking within 25 feet of the entryway. Such rules may come via democratic compromise or edict from someone with authority. And the breaking of these rules has a consequence. Consequences can be explicit or implied, but I would argue that rule without consequence cannot happen, since that removes any compulsory nature of the rule.

So you wind up with a workplace-centric version of the social contract. And, believe it or not, that's _insanely_ valuable. Without rules, you'd have no shortcuts to debate. Instead, you'd re-adjudicate the same issues each and every time they arose. Imagine having to explain to Jim down the hall _every day_ that playing loud music distracted everyone around him.

### Anatomy of a Codebase Rule

Assuming you write most of your code at work, the codebase rule forms a subset of the workplace rule, as I mentioned before. Any given rule may result from an architect edict or a group decision. Or, unlike most other workplace rules, it might come directly out of a static analysis tool like [NDepend](http://www.ndepend.com/ndepend-v2017).

But in the end, it serves the same purpose and has the same components. It stops the non-stop re-adjudication of past decisions. And it does so by establishing a convention and a consequence.

Usually, the consequence takes the form of some social shaming or instructions from a senior team member to modify your code. Run afoul frequently enough or willfully enough, and you might smack into some more formal consequences. But overall, these rules become a matter of social jockeying among the software development team.

By and large, this helps. But it can get seriously off the rails, as in the case of the draconian shops I mentioned in the intro.

### Calculus of Rule-Breaking

Let's assume, for the moment, that you don't work in one of these draconian shops. If you do, you and the shop have far bigger problems then when to defy a coding convention. So let's assume that the team has a mostly favorable, mostly collaborative approach to coding conventions and rules. How then do you know when to break one of them?

First of all, the case for breaking the rule gets an awful lot better if your peers agree with you on the matter. However wise your course of action, breaking a rule creates interpersonal blowback and resentment if it creates the impression that you think you're special. Dr. Greg House might get away with this behavior, but it tends to create problems in non-fictional situations.

So let's then look at the notion of rule-breaking from a team perspective. Let's say that you generally follow NDepend's suggestion to avoid the [singleton design pattern](https://sourcemaking.com/design_patterns/singleton) and you've internalized that as a team rule. But you have a situation where you should totally use it and you've convinced your team of it. Should you abide by your rule, or should you break it?

Apply a calculating business mind to it, and you have a good heuristic for an answer. Does the benefit of using it this one time offset the cost of using it other times? After all, you've created the rule for a _reason_, meaning the forbidden action has a cost. Can you afford that cost?

### Don't Break Them -- Change Them

Of course, you can have your cake and eat it too. And, I think you should. Interestingly enough, and as iconoclast as I might seem at times, I do not advocate breaking rules.

Are rules meant to be broken? No, not at all. They're meant to be obeyed. When breaking the rule is consistently a good idea, you have a bad rule. In Footloose, the dancing kid's breaking of the rules didn't represent an ideal action or outcome. Rather, it represented an "ends justify the means" approach fraught with its own potential for problems. Ideally, the town would simply have tossed the rule (or not made it to begin with), rather than forcing some Walkman wearing punk to break it. But when we talk about societal laws and injustices, things can get pretty complicated.

Luckily for us, we're talking about the much simpler prospect of rules governing our codebase. If we need concepts like nonviolent resistance and laws around freedom of expression to change our coding standards, then we're in serious trouble. We probably just need to grab a conference room and talk through it.

Because we have autonomy and a lack of morally hazardous situations, we have the easy power to change rules that no longer make sense. And I encourage you to do so! If the rule needs an exception, don't break the rule -- amend it to have more nuance. If the rule no longer makes sense, toss it. And if a static analyzer tells you to do something that you don't agree with, turn off the rule. (Probably do some research first, though, and make sure you can justify this.)

Are rules made to be broken when it comes to your codebase? No. But they are made to be constantly revisited.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
