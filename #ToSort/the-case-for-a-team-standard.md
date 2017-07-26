# The Case for a Team Standard

_Captured: 2017-03-21 at 01:46 from [dzone.com](https://dzone.com/articles/the-case-for-a-team-standard)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

In professional contexts, I think that the word "standard" has two distinct flavors. So when we talk about a "team standard" or a "coding standard," the waters muddy a bit. In this post, I'm going to make the case for a team standard. But before I do, I think it important to discuss these flavors that I mention. And keep in mind that we're not talking dictionary definition as much as the feelings that the word evokes.

First, consider standard as "common." To understand what I mean, let's talk cars. If you go to buy a car, you can have an automatic transmission or a standard transmission. _Standard_ represents a weird naming choice for this distinction since (1) automatic transmissions dominate (at least in the US) and (2) "manual" or "stick-shift" offer much better descriptions. But it's called "standard" because of historical context. Once upon a time, automatic was a new sort of upgrade, so the existing, default option became boringly known as "standard."

In contrast, consider standard as "discerning." Most commonly you hear this in the context of _having_ standards. If some leering, creepy person suggested you go out on a date to a fast food restaurant, you might rejoin with, "ugh, no, I have _standards_."

![](http://www.daedtech.com/wp-content/uploads/2014/11/TooMuchConfidence.jpg)

Now, take these common contexts for the word to the software team room. When someone proposes coding standards, the two flavors make themselves plain in the team members' reactions. Some like the idea, and think, "it's important to have _standards_ and take pride in our work." Others hear, "check your creativity at the gate because around here we write standard, default code."

## What I Mean by Standard

Now that I've drawn the appropriate distinction, I feel it appropriate to make my case. When I talk about the importance of a standard, I speak with the second flavor of the word in mind. I speak about the team looking at its code with a _discerning_ attitude. Not just any code can make it in here -- we have _standards_.

These can take somewhat fluid forms, and I don't mean to be prescriptive. The sorts of standards that I like to see apply to design principles as much as possible and to cosmetic concerns only when they have to.

For example, "all non-GUI code should be test driven" and "methods with more than 20 lines should require a conversation to justify them," represent the sort of standards I like my teams to have. They say, "we believe in TDD" and "we view long methods as code smells," respectively. In a way, they represent the coding ethos of the group.

On the other side of the fence lie prescriptions like, "all class fields shall be prepended with underscores" and "all methods shall be camel case." I consider such concerns _cosmetic_ since they concern appearance and not design or runtime behavior. Cosmetic concerns are not important… unless they are. If the team struggles to read the code and becomes confused because of inconsistency, then such concerns become important. If the occasional quirk presents no serious readability issues, then prescriptive declarations about it stifle more than they help.

Having standards for your team's work product does not mean mandating total homogeneity.

## Why Have a Standard at All?

Since I'm alluding to the potentially stifling effects of a team standard, you might reasonably ask why we should have them at all. I can assert that I'm interested in the team being discerning, but is it really just about defining defaults? Fair enough. I'll make my case.

First, consider something that I've already mentioned: maintenance. If the team can easily read code, it can more easily maintain that code. Logically, then, if the team all writes fairly similar code, they will all have an easier time reading, and thus maintaining that code. A standard serves to nudge teams in this direction.

Another important benefit of the team standard revolves around the integrity of the work product. Many team's standards incorporate methodology for security, error handling, logging, etc. Thus the established standard arms the team members with ways to ensure that the software behaves properly.

And finally, well-done standards can help less experienced team members learn their craft. When such people join the team, they tend to look to established folks for guidance. Sadly, those people often have the most on their plate and the least time. The standard can thus serve as a teacher by proxy, letting everyone know the team's expectations for good code.

## Forget the Conformity (by Automating)

So far, my rationale has followed a fairly happy path. Adopt a team standard, and reap the rewards: maintainability, better software, learning for newbies. But equally important is avoiding the dark side of team standards. Often this dark side takes the form of nitpicking, micromanagement, and other petty bits of nastiness.

Please, please, please remember that a standard should not elevate conformity as a virtue. It should represent shared values and protection of work product quality. Therefore, in situations where conformity (uniformity) is justified, you should automate it. Don't make your collaborative time about telling people where to put spaces and brackets -- program your IDE to do that for you.

## Make Justification Part of the Standard

Another critical way to remove the authoritarian vibe from the team standard is one that I rarely see. And that mystifies me a bit because you can do it so easily. Simply make sure you justify each item contained in the standard.

"Methods with more than 20 lines of code should prompt a conversation," might find a home in your standard. But why not make it, "methods with more than 20 lines of code should prompt a conversation because studies have demonstrated that defect rate increases more than linearly with lines of code per method?" Wow, talk about powerful.

This little addition takes the authoritarian air out of the standard, and it also helps defuse squabbles. And, best of all, people might just learn something.

If you start doing this, you might also notice that boilerplate items in a lot of team standards become harder to justify. "Prepend your class fields with m underscore" becomes "prepend your class fields with m underscore because… wait, why do we do that again?"

## Prune and Always Improve

When you find yourself trailing off at, "because you have a problem?" Something exists in your team standard that you can't justify. If _no one_ can justify it, then rip it out. Seriously, get rid of it. Having items that no one can justify starts to put you in conformity for the sake of conformity territory. And that's when standard goes from "discerning" to "boring."

Let this philosophy guide your standard in general. Revisit it frequently, and audit it for valid justifications. Sometimes justifications will age out of existence or seem lame in retrospect. When this happens, do not hesitate to revisit, amend, or cull. The best team standards are neither boring nor static. The best team standards reflect the evolving, growing philosophy of the team.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
