# Manual Code Review Anti-Patterns

_Captured: 2017-07-29 at 17:27 from [dzone.com](https://dzone.com/articles/manual-code-review-anti-patterns?oid=twitter&utm_content=buffer2b9d6&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Speed up delivery cycles and improve software quality with [TestComplete.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover the most robust automated testing tool for end-to-end desktop, mobile, and web testing. [Try TestComplete Free.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)

_Editorial Note: I originally wrote this post for the SubMain blog. You can [check out the original here](http://blog.submain.com/manual-code-review-anti-patterns/), at their site. While you're there, take a look around at some of the other posts and at their offerings._

Today, I'd like to offer a somewhat lighthearted treatment to a serious topic. I generally find that this tends to offer catharsis to the frustrated. And the topic of code review tends to lead to lots of frustration.

When talking about code review, I always make sure to offer a specific distinction. We can divide code reviews into two mutually exclusive buckets: automated and manual. At first, this distinction might sound strange. Most of you reading this probably think of code reviews as activities with exclusively human actors. But I tend to disagree. Any static analyzer (including the compiler) offers feedback. And some tools, like [CodeIt.Right](http://submain.com/products/codeit.right.aspx), specifically regard their suggestions and automated fixes as an automation of the code review process.

I would argue that automated code review should definitely factor into your code review strategy. It takes the simple things out of the equation and lets the humans involved focus on more complex, nuanced topics. That said, I want to ignore the idea of automated review for the rest of the post. Instead, I'll talk exclusively about manual code reviews and, more specifically, where they tend to get ugly.

You should _absolutely_ do manual code reviews. Full stop. But you should also know that they can easily go wrong and devolved into useless or even toxic activities. To make them effective, you need to exercise vigilance with them. And, toward that end, I'll talk about some manual code review anti-patterns.

![](https://www.daedtech.com/wp-content/uploads/2016/04/TriviaInterview.png)

### The Gauntlet

First up, let's talk about a style of review that probably inspires the most disgust among former participants. Here, I'm talking about what I call "the gauntlet."

In this style of code review, the person submitting for review comes to a room with a number of self-important, hyper-critical peers. Of course, they might not view themselves as peers. Instead, they probably imagine themselves as a panel of judges for some reality show.

From this 'lofty' perch, they attack the reviewee's code with a malevolent glee. They adopt a derisive tone and administer the third degree. And, frankly, they crush the spirit of anyone subject to this process, leaving low morale and resentment in their wake.

### The Marathon

Next, consider a less awful, but not effective style of code review. This one I call "the marathon." I bet you can predict what I mean by this.

In the marathon code review, the participants sit in some conference room for _hours_. It starts out as an enthusiastic enough affair, but as time passes, people's energy wanes. Nevertheless, it goes on because of an edict that all code needs review and because everyone waited until the 11th hour. And predictably, things get more careless as time goes on and people space out.

Marathon code reviews eventually reach a point where you might as well not bother.

### The Scattershot Review

Scattershot reviews tend to occur in organizations without much rigor around the code review process. Perhaps their process does not officially or formally include code review. Or, maybe, it offers few more specifics than "do it."

With a scattershot review process, the reviewer demonstrates no consistency or predictability in the evaluation. One day he might suggest eliminating global variables, and on another day, he might advocate for them. Or, perhaps the variance occurs depending on the reviewer. Whatever the specifics, you can rest assured you'll never receive the same feedback twice.

This approach to code review can cause some annoyance and resentment. But morale issues typically take a backseat to simple ineffectiveness and churn in approach.

### The Exam

Some of these can certainly coincide. In fact, some of them will _likely _coincide. So it goes with "the exam" and "the gauntlet." But while the gauntlet focuses mostly on the process of the review, the exam focuses on the outcome.

Exam code reviews occur when the parlance around what happens at the end involves "pass or fail." If you hear people talking about "failing" a code review, you have an exam on your hands.

Code review should involve a second set of eyes on something to improve it. For instance, imagine that you wrote a presentation or a whitepaper. You might ask someone to look it over and proofread it to help you improve it. If they found a typo, they wouldn't proclaim that you had "failed." They'd just offer the feedback.

Treating code reviews as exams, generally, hurts morale and causes the team to lose out on the collaborative dynamic.

### The Soliloquy

The review style I call "the soliloquy" involves paying lip service to the entire process. In literature, characters offer soliloquies when they speak their thoughts aloud regardless of anyone hearing them. So it goes with code review styles as well.

To understand what I mean, think of times in the past where you've emailed someone and asked them to look at a commit. Five minutes later, they send back a quick, "looks good." Did they _really_ review it? _Really_? You have a soliloquy when you find yourself coding into the vacuum like this.

The downside here should be obvious. If people spare time for only a cursory glance, you aren't really conducting code reviews.

### The Alpha Dog

Again, you might find an "alpha dog" in some of these other sorts of reviews. I'm looking at you, gauntlet and exam. With an alpha dog code review, you have a situation where a particularly dominant senior developer rules the roost with the team. In that sense, the title refers both to the person and to the style of review.

In a team with a clear alpha dog, that person rules the codebase with an iron fist. Thus the code review becomes an exercise in appeasing the alpha dog. If he is present, this just results in him administering a gauntlet. But, even absent, the review goes according to what he may or may not like.

This tends to lead team members to a condition known as "[learned helplessness](https://en.wikipedia.org/wiki/Learned_helplessness)," wherein they cease bothering to make decisions without the alpha dog. Obviously, this stunts their career development, but it also has a pragmatic toll on the team in the short term. This scales terribly.

### The Weeds

Last up, I'll offer a review issue that I'll call "the weeds." This can happen in the most well meaning of situations, particularly with folks that love their craft. Simply put, they get "into the weeds."

What I mean with this colloquialism is that they get bogged down in the details at the expense of the bigger picture. Obviously, an exacting alpha dog can drag things into the weeds, but so can anyone. They might wind up with a lengthy digression about some arcane language point, of interest to all parties, but not critical to shipping software. And typically, this happens with things that you ought to make matters of procedures, or even to address with your automated code reviews.

The biggest issue with a "weeds" code review arises from the poor use of time. It causes things to get skipped, or else it turns reviews into marathons.

### Getting it Right

How to get code reviews right could easily occupy multiple posts. But I'll close by giving a very broad philosophical outlook on how to approach it.

First of all, make sure that you get clarity up front around code review goals, criteria, and conduct. This helps to stop anti-patterns wherein the review gets off track or bogged down. It also prevents soliloquies and somewhat mutes bad behavior. But, beyond that, look at code reviews as collaborative, voluntary sessions where peers try to improve the general codebase. Some of those peers may have more or less experience, but everyone's opinion matters, and it's just that -- an _opinion_ for the author to take under advisement.

While you might cringe at the notion that someone less experienced devs might leave something bad in the codebase, trust me. The damage you do by allowing these anti-patterns to continue in the name of "getting it right" will be far worse.

Release quality software faster with [TestComplete.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover how to decrease testing times and expand test coverage with the most robust automated UI testing tool. [Try free for 30 days.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)
