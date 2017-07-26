# User Story Reflections

_Captured: 2017-02-07 at 20:37 from [dzone.com](https://dzone.com/articles/user-story-reflections?edition=267885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-07)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

## Users

As its name suggests, a user story describes how a user or customer uses the product-a digital product is captured from the perspective of the users. This avoids a solution-centric view where we worry more about how to provide and implement the product features than why and how people will use them.

Understanding who the users are and how the product will benefit them is central to discovering and creating the right stories. In other words, if you do not know who your users are and what problem they want to see addressed or which benefit they would like to experience, then you should not create stories! Otherwise, you are in danger of speculating about the product features rather than deriving them from the user needs.

I'd like to take this further and suggest that you should meet the users. This is not to say that the users will be able to correctly tell you what the product should do--it's your job to figure this out. I know that product managers and product owners don't always have access to the users and are sometimes shielded from them by the sales team or management. I also understand that development team members tend to see users even less frequently. If you want to leverage user stories to develop a successful product, however, you should try to observe and talk to the people who will use it. How else can you truly understand their needs and empathize with them?

## Conversation

When I first came across user stories over 15 years ago, I was surprised by their lack of detail. I was used to working with use cases, and it took me a while to get my head around their sketchiness. They seemed less like requirements and more like notes. And that's exactly what stories are meant to be--notes that capture the essence of a [conversation](http://ronjeffries.com/xprog/articles/expcardconversationconfirmation/).

On its own, a user story is pretty useless. It needs to be complemented with a conversation between the person in charge of the product, the product manager or product owner, and a cross-functional development team.

Maybe it's helpful to take a quick look at the context in which user stories emerged. Stories were first used in Extreme Programming in combination with the role of an onsite customer. The onsite customer is a member of the user community who is collocated with the development team. The individual would discuss with the team what should be built in the next iteration, and captured the conversation as stories to remind everyone of what was discussed.

Agile approaches happily accept tacit knowledge; knowledge that is not explicitly expressed and written down, and they prefer face-to-face conversation over documentation. Why? To speed things up, to allow the team to quickly implement some functionality and to validate it by exposing it to the users.

I find it even better to co-create user stories by inviting the development team members to help discover new stories and amendments to existing ones--based on the feedback and data gathered from the users. This leverages the team's collective knowledge and creativity and tends to result in better, clearer stories. To do so, make collaborative story work part of your [product backlog grooming](http://www.romanpichler.com/blog/grooming-the-product-backlog/) or refinement process.

But if you cannot have a meaningful conversation, if the product owner and the team cannot discuss new stories together so that the team understands the stories and can make suggestions for improving or splitting them, then you should not use user stories. The conversation is not optional; it is an essential part of user stories. Without it, the story is not usable or it becomes bloated with details. If you find that you need to capture more details or hand-off requirements, then use a different approach, like use cases, instead.

Use cases tend to be more effort to create and update, but they offer more structure. They come with pre- and post-conditions, triggers, main success scenarios, alternative success scenarios, and exception scenarios. This allows you to describe the product functionality in more detail, which may be necessary when working with remote teams.

## Simplicity

User stories are a very simple tool--we simply tell stories about how users are likely to interact with the product and capture their essence. That's it. Unfortunately, I have seen a fair amount of stories that were far from simple and straightforward.

I find it helpful to remember that in the early days of agile, people didn't talk so much about user stories. Instead, they used the term _story cards_. The reason for this is simple: stories were captured on paper cards. These have two advantages: they facilitate collaboration and visualization. Everybody can write on a piece of paper, and the cards can be easily arranged on the table or office wall. Electronic tools are less conducive to teamwork in my experience; one person is usually in control of the keyboard and tool. What's more, it's much harder to display the stories and prevent them from being hidden away. I would, therefore, encourage you to experiment with paper cards to capture your stories--at least when you create new stories. You can key them into your favorite electronic tool afterward if you wish. But be warned: I've seen teams who decided after some experimentation to switch from electronic to paper-based stories.

Another area that can benefit from simplification are the acceptance criteria. As the name implies, the criteria want to communicate what needs to be in place so that the story can be considered as done and the corresponding functionality can be exposed to a user or customer. Acceptance criteria should be no big deal, but follow naturally from the narrative by asking, "how can we tell the story is done?" If you make the criteria more complicated, the stories become harder to understand and start to slow you down.

## Limits

User stories are great at capturing product functionality, things people can do with a digital product like searching, evaluating, and purchasing products online. You can also use stories to capture [non-functional aspects](http://www.romanpichler.com/blog/agile-nonfunctional-requirements/) of a product, such as performance, robustness, and interoperability.

But when it comes to the user interface and user interaction, user stories are less suitable. Sketches and mock-ups are better at describing the UI design. And [scenarios](http://www.romanpichler.com/blog/agile-scenarios-and-storyboards/), workflow diagrams, storyboards, and story maps are better suited to capture user interactions that comprise several steps.

Additionally, writing user stories is worthwhile when you develop software that's likely to be reused. But if you want to quickly create a throwaway prototype or mock-up to validate an idea, then writing stories may not be necessary. Remember: user stories are not about documenting requirements; they want to enable you to move fast and develop software as quickly as possible--not to impose any overhead.

User stories should, therefore, be one of the tools in your product toolbox, not the only one.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
