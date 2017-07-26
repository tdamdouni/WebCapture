# Turning Requirements Into User Stories

_Captured: 2017-02-06 at 12:37 from [dzone.com](https://dzone.com/articles/turning-requirements-into-user-stories?oid=twitter&utm_content=bufferd2995&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

Let me ask you something. When you read the title of this post, did you envision it laying out some onerous process for converting gigantic Word documents full of requirements into "user stories" in JIRA? If so, I'll set your mind at ease right now. It's not that.

Indeed, I am not talking about the mechanics of taking the square peg of "traditional, Waterfall-style requirements document" and jamming it into the round hole of some ALM suite's Agile workflow. Instead, I'm talking about the more labor-intensive practice of taking a document like that and using it to generate actual Agile-style user stories. There is absolutely a difference -- and it's not even a subtle one. Putting, "1.4.2.3 System shall cause cursor to blink twice after user types A key" into Jira and calling it a "user story" does not make it one.

![](http://www.daedtech.com/wp-content/uploads/2013/02/YeRequirements2.jpg)

## Anatomy of a User Story

It bears asking, then, "Since you say _that's_ not a user story, what _is_ a user story?" The most common way one sees it defined is via a mad lib. "As an _X_ , I want to _X_ so that _X_." The definer then creates an example, such as, "As a personal banking customer, I want to know my account balance so that I don't overdraft with my next withdrawal."

To get a bit more philosophical, the user story has three components: persona, action, and value proposition. The person is the "who" and it typically involves a description of a user or "actor" in the broader context of the system. Some groups will actually define personas, give them names and characteristics, and then use the names instead. "Dave is a 35-year-old stock broker with a checking and savings account, who…" The user story is then, "As Dave, I want to know my account balance so that I don't overdraft at my next withdrawal."

The action is the way in which the user interacts with the system. It is not framed in terms of minutiae and sequential, detailed actions. Rather, it is framed in terms of goals that can be accomplished in a sitting. There is a certain amount of art and subjectivity to what is an appropriate goal, but you'll get the hang of it with practice.

Finally, there is the value proposition of the user story. In my experience, this is the part that is both most frequently omitted and most important. (It is also the part that is hardest to grok for people used to waterfall/contract-style requirements). The value proposition explains why the person in question wants to do the thing in question. Including it is particularly urgent for two reasons:

  1. If the value proposition is weak or nonexistent, you may deprioritize or eliminate this story altogether.
  2. If you hit a roadblock during an implementation of the action, you can immediately start thinking of other, more technically feasible ways to achieve the value proposition.

## How This Differs

If you look at traditional requirements documents, they generally lack all three of the components, though one might argue that they contain a very specific, granular form of user goals. (I would argue against this, however). Instead, they deal exclusively in stating future behavior of "the system." They also love to do this with the word "shall."

  * 1.4.5.9 System shall prompt the user input.

  * 1.4.5.10 System shall display, "phone numbers cannot contain anything but numbers, parentheses, spaces and dashes" in the event of bad input.

  * 1.4.5.11 System shall store user phone number into the PhoneNumber column of the User table of the database.

You get the idea.

There is no persona here. There is the nebulous concept of "user," but the system is really the star of the show, which makes the author of the requirements document the star of the show. Anyone asking, "Why are we doing it this way?" would get an answer of, "Because it says so in the document, that's why, so just do what the document says."

There is likewise no actual goal and there is certainly no value proposition. From the example above, we can infer that some user wants the computer to have their phone number for some reason. Is it because they're signing up to get a text message when their table is ready at a restaurant? Or is it because they're angrily filling out a bunch of useless information so that they can click "next" in the wizard and find out how much cable costs in their area?

Does this matter? Absolutely! With that context, the development team might say, "Oh, wow, supplying the phone number and having is stored are mission critical, since the whole point is the user getting a text message." Or alternatively, "Gosh, maybe we shouldn't do this at all because it serves no business purpose for anyone and just angers people."

In a traditional requirements document, who and why are irrelevant. So, either way, the team shrugs, implements the phone number prompt, and, if the end result is a bunch of angry users, says "Whatever, that's what it said in the document."

Software development teams are made of intelligent knowledge workers with excellent problem-solving capabilities. Getting the "who" and "why" in front of them, rather than the "how" makes your entire organization better at helping its users.

## Migrating Toward Stories

In businesses with a long history of traditional requirements, the shift can be difficult. It requires a mindset change from, "I need to lay out every last workflow and detail," to "I'll just say who wants to accomplish what, and why, and trust that it gets sorted." However, that trust is difficult when it has never historically been extended or validated. It requires practice and a leap of faith.

In my experience, one of the _best_ ways to get started on that journey is to resist the impulse to toss out the traditional document and start from scratch. However, the same approach also requires you not to pollute your user stories with cut and paste snippets from that document.

Rather, have the development team (and an experienced user story writer, if the team doesn't have one) sit with the traditional requirements document authors with the shared goal of stocking the team's backlog with user stories. This approach is messy in its own right, but only messy for the days it takes to generate enough stories to prioritize and get going (rather than being messy throughout the project).

However, what comes out on the other side will be valuable. It will be an end result in which all parties to the development process have thought through and articulated who will be using the system to accomplish what, and why. It may wind up showing parts of the requirements document as wholly unnecessary and that the document missed some things that need to be covered. In the cases where the document contains valuable, detailed information, that can be added to the story as acceptance criteria that the user story must satisfy to be considered done.

This is by no means a perfect solution. However, none really are when you're undertaking a philosophical change in approach. This is a solution that I have implemented in the field and watched yield excellent results. It's a powerful thing when your team stops viewing software development as a checklist and starts viewing it as a way to help real humans achieve real goals with real value to them.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
