# Implementing Agile Yourself

_Captured: 2015-10-14 at 23:11 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/implementing-agile-yourself)_

## Using Agile Tools Yourself

Over the last few lessons you learned how teams use SCRUM to manage software projects but you probably still don't have a good idea how you would implement it yourself. That's okay because in this lesson we'll change that. You will learn how to set up your own projects the Agile way using a tool called Pivotal Tracker.

You'll see Pivotal Tracker a fair bit over the coming mini-courses and during the VCS intensive program -- we'll use it to give you assignments and to coordinate work during our SCRUM-based process. We do this both because it's really helpful for guiding you through your work and also because it gives you good exposure to the kinds of tools and processes you'll use on the job.

Even if you're not planning to use the SCRUM process for anything, working with user stories to break your project into bite-sized user-focused pieces can be an incredibly valuable experience. Tracker will help you manage those stories.

### Pivotal Tracker

[Pivotal Tracker](http://pivotaltracker.com) is a free web-based project management program that was created by the consulting firm [Pivotal Labs](http://pivotallabs.com/). It's certainly not the only project management tool out there (Atlassian's [Jira](https://www.atlassian.com/software/jira) is also quite popular) but it gets major points for simplicity and ease-of-use. We also appreciate that it's free for public-facing projects :)

Essentially, Tracker stores your backlog of stories and then automatically allocates them to your current and future iterations/sprints based on your velocity. It lets you enter each story and its acceptance criteria, attach mockups, and keep track of comments on it via email.

Naturally, the folks over at Pivotal Labs are really the right people to walk you through their product. **Go to their [Getting Started site](https://www.pivotaltracker.com/help/gettingstarted) and watch the two videos on the top ("[Getting Started"](https://www.pivotaltracker.com/flash/flvplayer.swf?file=https://s3.amazonaws.com/tracker.screencast/GettingStarted-2.0.mov&image=https://d3jgo56a5b0my0.cloudfront.net/images/v7/application/screenshots/storyview.png&autostart=true) and "[The Concepts"](https://www.pivotaltracker.com/flash/flvplayer.swf?file=http://tracker.screencast.s3.amazonaws.com/pivotal-tracker-concepts.flv&image=https://d3jgo56a5b0my0.cloudfront.net/images/v7/application/screenshots/storyview.png&autostart=true)).**

Once you've watched the videos, **read through the Getting Started site itself** to clarify the concepts. The videos move pretty quick so you may benefit from watching again.

### Put Another Way

We'll quickly walk you through what your workflow might look like on a new project if it seemed too fast in the Pivotal videos.

If you remember from the lesson on SCRUM, the **Product Owner** is the team member or client who acts on behalf of the users (so you can ask questions of this person when you need clarification) and the person who ultimately accepts or rejects your stories. If you're a developer on a team or sometimes as a freelancer, you'll probably have someone to report to who assumes this role. If you're an entrepreneur... well, that's another hat for you to wear.

It may seem confusing how you would actually put an Agile story into the tracker. Where do the components of the story go?

  1. Start by creating a new story and giving it a descriptive title.  

  2. Write the full story text (i.e. "As a ... I want to ... So I can ...") in the "Description" field.  

  3. Add the specific acceptance criteria to the "Tasks" section.  

  4. If you have mockups or images to include, paste them into the "Comments" section of the story.

Here's an example story from an open-source project:

![The Odin Project story example in Pivotal Tracker](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/pivotal_story.jpg)

> _The Odin Project story example in Pivotal Tracker_

#### Who Does What Now??

Let's review how the SCRUM-like Agile process works with Tracker:

  1. You'll start each project by **Gathering Requirements** from your client and/or users. You or the design team will work with them to produce mockups. _This function is often done by the product owner but developers are useful for asking detailed clarifying questions._
  2. Then you'll do the **Stories Breakdown** by turning the requirements (and user goals) into a series of bite-sized stories. You'll want to think about the overall system architecture at this stage so you'll be able to intelligently break down large features. Add the stories to the Pivotal Tracker project. _This is a collaboration between the product owner and the developers_.
  3. Next, you'll do the **Story Estimation** by running through each story and estimating how many points it should be. Stories too large get broken down again. _This is done by the development team_.
  4. Once the stories are estimated, the product owner will **Prioritize the Stories** based on client needs. This means shuffling them into the right order in the Tracker project.
  5. Now it's time to **Build the Software**. You'll take the first open story (because they're priority-sorted) and click "Start". Develop the story, commit your code, and then click "Finish" once you've checked off all the acceptance criteria in the "Tasks" section. When you push your code to the staging environment (if you have one), click "Deliver". _This is obviously done by the development team who ask the Product Owner clarifying questions as necessary_.
  6. Finally, during the **Acceptance** phase the Product Owner will decide whether the code you build accurately satisfies the acceptance criteria of the story. If so, they'll click "Accept", otherwise they'll click "Reject" and provide a reason.

### Some Quick Tips

  * The person who creates the story will automatically be added to it (as the "REQUESTOR") and anyone who advances the story state will to. Make sure you select FOLLOW THIS STORY if you're working on it but haven't been added!
  * Any comments left in the comments section will automatically be emailed out to followers of the story. Replying to the email will send it to the other members and also post it to the story on Tracker. This is why you should make sure to follow the story.
  * You can attach links to files (like mockups) in the comments as well.

### Wrapping Up: Does This Seem Familiar?

The Agile workflow we've just covered in the context of using Pivotal Tracker should seem awfully familiar if you saw the [SimpleBlogger Demo](http://www.vikingcodeschool.com/web-development-basics/how-a-website-is-built) from the first mini-course, where we walked through how a sample web development project might look. In it, we discussed how our overall approach follows these steps:

![VCS high level workflow](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/our_workflow_broad.png)

> _VCS high level workflow_

At this point you should be able to see how you would manage that high level workflow using Pivotal Tracker. The coding part comes later -- during the last mini-course and as you go through the main VCS program you'll become intimately familiar with tackling and coding up stories (we're honing in on it!). But now you can at least approach that step with a full appreciation of each story's context in the larger project flow.
