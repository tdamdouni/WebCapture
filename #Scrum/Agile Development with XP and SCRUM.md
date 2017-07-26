# Agile Development with XP and SCRUM 

_Captured: 2015-10-14 at 23:09 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/agile-development-with-xp-and-scrum)_

## Agile Development with eXtreme Programming (XP) and SCRUM

Now that you've learned the theory of Agile, in this lesson we'll talk about how it's actually implemented. If you recall from the previous lesson, some key components of Agile are:

  1. Expectation of changes in the project requirements
  2. Short development cycles
  3. Heavy client involvement throughout the project
  4. Frequent re-evaluation of priorities and needs
  5. Working in small cross-functional teams (as Jeff Bezos put it, "two pizza teams" because they need to be able to share two pizzas)

Two of the most common implementations of Agile (though obviously there are many flavors out there) are XP and SCRUM. XP tends to focus on how the code is produced while SCRUM is all about managing the project itself.

### eXtreme Programming (XP)

![extreme computer](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/extreme_computer_small.jpg)

> _extreme computer_

Extreme was pioneered by Kent Beck during his work on the Chrysler Comprehensive Compensation System project in the late 1990's (note that it predates the [Agile Manifesto](http://agilemanifesto.org/)). Kent basically took many of the best practices of software development at the time and told his teams to take them to the extreme and leave the rest out.

XP provides a disciplined framework for teams to focus on producing code. It worries less about the overall project management and more about how to make developers more productive.

#### Key Concepts of XP

XP says you should:

  * Start with a **release planning phase** to figure things out
  * Have the clients define their requirements in terms of simple but specific **"user stories"** which describe the need from the perspective of the user
  * **Embed a user** or representative of users within the development team to provide real time feedback or clarification
  * Build the software in **shorter "iterations"** and only mark features completed when the users have tested and accepted them ("user acceptance testing")
  * Empower the user / client to decide that enough features have been built and terminate the project at any time.
  * Use **"Continuous Integration (CI)"**, where developers integrate their specific branch of the code with the main code base as often as multiple times a day (instead of waiting until lots of code is written and then doing a massive hellish code merge)
  * Measure the current development **"velocity"** of the project so you can better estimate how much longer it's going to take.
  * **Pair program** (have two developers work on the same workstation), which ensures higher quality code since there's basically constant code review going on.

You'll learn a bit more about XP when we talk about SCRUM below. See the Resources tab if you want to dive deeper.

### SCRUM

![Rugby SCRUM](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/scrum_small.jpg)

> _Rugby SCRUM_

In Rugby, the SCRUM is the competitive huddle when play is about to be restarted. It's also a very popular agile framework that provides both project management and an actual development process (unlike XP, which is more development focused). The software folks adopted the analogy because they like holding brief check-ins to see what needs to be done that particular day.  
We'll cover the high level stuff here and the reading and videos below will fill in the details.

#### Project Management with SCRUM

![SCRUM project management on a blackboard](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/scrum_blackboard_small.jpg)

> _SCRUM project management on a blackboard_

SCRUM project management is all about organizing the development of the **User Stories** we mentioned above in the section on XP.

Each project starts with figuring out the overall scope of what's needed and the high level design of how it'll get done (the Planning phase). All the required work is broken into user stories, prioritized, and placed into the **Product Backlog**. The backlog is broken up into short iterations (1-4 weeks) called **Sprints**, where the goal of each is to finish a certain number of items in the backlog. Ideally, finishing a sprint will result in some discrete or deployable product.

When a sprint begins, everyone gets on the same page about what items from the backlog they need to tackle during that sprint. During a sprint, every day begins with the **SCRUM meeting** where each member of the team very briefly highlights:

  1. What they did the day before
  2. What they're doing today
  3. What they are currently being "blocked" by (e.g. need some help with)

Team members stand for the whole meeting to keep it short. One member is assigned the role of the **SCRUM Master** and takes charge of the process. Another, called the **Product Owner**, advocates on behalf of the user and may be the client, a real user, or the [Product Manager](http://en.wikipedia.org/wiki/Product_manager) of the team.

The product backlog is populated by the same user stories we mentioned above. Each story is assigned a certain number of **points** related to its complexity. To see how much progress they are making during the sprint, the team uses a **burndown chart** which shows how many points they have finished relative to how many points they have left.

After the sprint ends, there is a **Retrospective** meeting with the entire team and the client to figure out how it went and what they learned. The team then takes a look at the backlog and decides what needs to be removed, added, or re-prioritized.

Once the client decides enough features have been built to release the product, the development team stops doing sprints and does testing, training, and documentation as necessary to make the release happen.

![SCRUM Process](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/scrum_process_small.jpg)

> _SCRUM Process_

_Source: [Sathees Kumar](http://satheespractice.blogspot.com/2011/11/what-is-agile-scrum.html)_

#### Development with SCRUM

SCRUM's development is closely tied with the project management -- small teams are allocated to each backlog item being worked on in the current sprint. The team working on a backlog item is responsible for writing the code, testing it, documenting it, and demonstrating it upon completion.

SCRUM teams often also use practices associated with XP like pair programming and continuous integration.

#### Learn More

Start by [watching this video (below) about SCRUM](https://www.youtube.com/watch?v=OJflDE6OaSc), which focuses on the business value it generates:

Then [watch this video (below)](https://www.youtube.com/watch?v=XU0llRltyFM) for a more detailed look at how it's implemented:

### Wrapping Up

You should have a good overview of the philosophy of XP and a more detailed understanding of how SCRUM looks. You don't necessarily need to remember all the steps that are involved but you should have a general picture in your head about how a SCRUM project comes together and how you might fit into it.

This is useful stuff because you might be a part of a SCRUM team as a software engineer working for a firm or you might actually implement it yourself to help manage your development process as an entrepreneur.

In the next lesson, we'll dive deeper into user stories since they will be used extensively throughout the mini-courses, the main VCS program, and your development career. They also help tie together the philosophy of User-Centered Design with the development of those designs... which is great because we're pretty sure hundreds of puppies around the world get a little bit cuter whenever Design and Development come together like that!

![Dilbert on XP](http://globalnerdy.com/wordpress/wp-content/uploads/2007/11/dilbert-xp01.gif)

> _Dilbert on XP_
