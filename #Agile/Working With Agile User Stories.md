# Working With Agile User Stories

_Captured: 2015-10-14 at 23:10 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/working-with-agile-user-stories)_

## More About Stories and How They Are Used

![Dilbert on Agile Stories](http://globalnerdy.com/wordpress/wp-content/uploads/2007/11/dilbert-xp02.gif)

> _Dilbert on Agile Stories_

During these prep mini-courses and the main VCS program, we'll be advocating a blending of the SCRUM planning methods with XP programming tactics. Regardless of what you end up using on your own or with your team, it's worth spending a few extra minutes to make sure you understand User Stories.

Stories are particularly powerful because they tie together the user-first philosophy of User-Centered Design that we talked about before with the actual development of your project.

Even if you don't follow the project management process of SCRUM, creating user stories to guide your development work will be helpful. They'll force you to clarify what you're working on and break your project down into simple manageable pieces.

### Writing Good Stories

If you're following the User-Centered Design process from the [Design mini-course](http://www.vikingcodeschool.com/web-design-basics), you've started your project by discovering who your users are and what their most important objectives are. User stories break up those larger goals (like "I want to buy a coffee mug that says 'Hello, World.'") into specific achievable pieces. Taking apart a project and turning it into stories is an art, and it's best done when working directly with users.

At it's most basic, your task is to turn those big user goals into little bite-sized mini-goals that can be developed. Each story is meant to fit onto a single 3x5 notecard to force you to be brief. That's why they are sometimes referred to as "story cards".

For practical reasons, teams often use sticky notes instead:

![agile story board](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/agile_story_board.jpg)

> _agile story board_

As an example, turn a larger goal like "I want to buy a specific product" into a series of individual steps like:

  1. Search for items
  2. Add items to your shopping cart
  3. View your cart
  4. Begin the checkout process
  5. Et cetera... 

It's up to you exactly how specific you want to make these steps, but you'll get the hang of it once you've actually developed a few of them and found them to be either too narrow or too broad.

It's also worth noting that breaking down the larger problem into pieces like this is the heart of the engineering approach that we've been pounding into your brain for a while now :)

#### Story Format

The format of a user story is that it should be brief, in the language and perspective of the user, and contain the following:

  1. Who the user is (specifically)
  2. What the user's goal is for that story
  3. Why that goal is important to the user

Stories are designed to fit on a simple note card or post-it note. They have a brief title and are written in the following format:

**As a** [specific type of user], **I want to** [accomplish some specific goal] **so I can** [achieve some benefit].

This is valuable because it forces you to think in terms of what your user wants and why, which will help you make the right development decisions along the way.

![agile story card](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/story_card.jpg)

> _agile story card_

_Source: [www.gov.uk](https://www.gov.uk/service-manual/agile/writing-user-stories.html)_

The other thing you need to add to your stories to use them for development work is their **acceptance criteria** (which usually goes on the other side of the card). That means writing down the specific tasks that need to be achieved in order for that story to be finished (or accepted by the client/user). For instance, if your story is:

"**As a** reader of this post, **I want to** subscribe to your newsletter **so I can** follow your blog"

Then the acceptance criteria, which would usually be on the back of the note card / post-it note, will include core paths and edge cases. It is meant to add detail to the conversation around the story but not (yet) serve as an exhaustive list of tests. The story above might include the following acceptance criteria:

  1. The visitor can enter a valid email to the subscribe form
  2. The visitor cannot submit the form without entering a valid email
  3. After submission, the visitor should see a "thank you" message on the top of the screen

These acceptance criteria form the basis for the things you'll actually need to write tests for during the development process (we'll cover testing in a separate lesson). Once the client agrees that all criteria are met, the story is accepted and you can move on to the next one.

To learn more about writing good user stories, **Check out [this video (below)](https://www.youtube.com/watch?v=DaqyLWOEObY)**:

Then **read through [this article from RallyDev.com](https://help.rallydev.com/writing-great-user-story)** by Ronica Roth. It's got good detail about the specifics of implementing stories.

If you still want some more tips, check out the Resources tab for more helpful links.

### How Stories Are Used

There are some specific ways that stories are used if you are implementing a formal development process like SCRUM. You probably won't go through all this added process if you're just building a website on your own, but it's useful to know your options. If you begin working as part of a team and need to start coordinating work among members and to meet time-based objectives, this will be more readily applicable.

As we said in the previous lesson, the project starts with the planning phase, when you break down the project into iterations and each iteration into stories. Once the team figures out what the user stories are, they go over each one and vote for how many **Points** it is worth. A point is a pretty subjective thing but it represents the developmental complexity of the story. Usually they are either on a 1,2,3,4 scale, a 1,2,4,8, or a Fibonacci 1,2,3,5,8 scale (it really doesn't matter). Any story that hits the highest number usually needs to be broken down into several stories.

The point of points (heh) is to estimate and track your progress as you are working through a sprint. It doesn't really matter on some absolute scale if you're giving the story the "correct" number of points -- as long as your team is consistent, you'll be able to use them for estimation.

Large groups of stories that combine to compose a particular feature are often grouped inside so-called **Epics**. In the product world, Epics are often considered "features significant enough you can write a press release about".

During the planning phase of the project and after you've broken the project into stories, you'll work with the client to prioritize these stories. Some features are essential and should be tested with real users ASAP while others are more in the "nice to have" category for now. This prioritization determines what order they go into your product backlog. Your team will tackle the top stories of the backlog first and work their way through it.

At the start of each sprint, you'll have a certain number of total points that you're expecting to finish during that sprint. Each day that goes on, you will complete some stories and reduce how many points are remaining.

Your average daily number of completed points is called your **velocity**. In theory, if your velocity times the days remaining is less than the remaining points of the sprint, you're in good shape.

The chart of your remaining points over time is called the **burndown chart** since it shows how many points you have left to burn down each day. It visually shows you whether you're on track to finish the sprint or not. Note that points can actually be added if you add new stories mid-sprint or discover additional complexity.

See the image below of a burndown chart:

![burndown chart](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/burndown_chart.jpg)

> _burndown chart_

### Wrapping Up

You should have a good feel for how you can break a project into stories and how those stories are used by a SCRUM team. Again, you may not use a full SCRUM process yourself but the exercise of producing user stories will almost certainly be helpful. Regardless, the tools we cover in the next lesson will help you organize your development work and stay on track.

###  Next Lesson: Implementing Agile Yourself 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/implementing-agile-yourself) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/agile-development-with-xp-and-scrum)
