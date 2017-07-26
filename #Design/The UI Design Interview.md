# The UI Design Interview

_Captured: 2016-05-23 at 13:43 from [www.palantir.com](https://www.palantir.com/2011/12/the-ui-design-interview/)_

![](http://imgs.xkcd.com/comics/computer_problems.png)

> _Compiler design dependency comic, originally from http://www.xkcd.com/722/_

Comic courtesy of [XKCD](http://www.xkcd.com/722/), via Creative Commons License

Our frontend engineering [candidates](http://www.palantir.com/engineering-culture/) go through many of the same types of interviews as our backend candidates, i.e., [algo](https://www.palantir.com/2011/09/how-to-rock-an-algorithms-interview/) and [coding](https://www.palantir.com/2011/10/the-coding-interview/). But because they'll be building the user-facing parts of our system, we want to make sure candidates have some design chops as well. Hence the UI design interview.

## Why have a design interview for an engineer?

Perhaps my favorite part of being on the frontend team at Palantir is that we get to work on both the design and the implementation of our own UIs, from inception to finished product. Engineers collaborate on the design of the product with other engineers as well as with designers, and we openly debate the merits of all our decisions. The UI interview simulates this kind of cooperative design and debate. Typically, this means you'll be asked to design and/or evaluate one or two pieces of UI during the interview, while your interviewer plays both collaborator and critic.

Read on for some helpful points to keep in mind as you work on a design problem with your interviewer.

## It's all about the user

The user is the ultimate arbiter of success for any interface. If users can accomplish their tasks in a simple, efficient, intuitive way, then we're doing our job right. Therefore, we must **keep the user in mind** at every stage of interface design.

One common mistake that you can make up front is to assume YOU are the user. Because working on a computer is a solitary activity, it's easy to forget that everyone experiences an interface in a different way. Depending on what you're designing, the user may be a complete novice or a seasoned sysadmin.

It's important to **imagine what your users are like**. If it helps, give the user a name, age, and occupation. Ask yourself these questions:

  * In what context will they use this feature? At work? At home? On a TV from 10 feet away?
  * Have they used a similar interface before?
  * How savvy are they with computers in general? Do they know how to copy and paste, drag and drop, or open a context menu?

When designing a feature for the interface, walk the user through the feature. **Make a rough sketch** of the main components (buttons, lists, text blocks) on a whiteboard or sheet of paper. Then simulate how your user might interact with the feature, by drawing in their input and selections.

While sketching your proposed interface, **put yourself in the user's shoes**. Ask yourself these questions:

  * What will they be doing when they want to start doing X?
  * How do they discover the feature?
  * What will they want to do after?
  * How frequently will the user do X?
  * What if X fails to complete properly?

and so on. Once you've asked yourself those questions, consider how the answers should impact your design and modify it accordingly.

**tl;dr: The user is paramount. Each of your decisions should be justified by its impact on the user**.

## The interview is highly interactive

Some candidates are reluctant to contradict the interviewer or provide alternative ideas. We want the opposite. If you have a good idea,**advocate for your position**. I prefer candidates who will contradict me, as long as they back up their ideas with arguments, stories, or examples. The more you can articulate the reason for your beliefs, the better.

Go ahead and keep throwing ideas out there. I'll shoot down some of them, but don't be daunted. It may take 10 ideas before we discover a gem. (This is how all design works, not just in an interview setting.)

## Be creative, but don't re-invent the wheel

I've seen many candidates jump through incredibly awkward (albeit fancy) hoops just to display some very simple data. If you have a list of data, display it as a list. In general, being familiar with UI conventions is helpful because they encode a lot of hard-earned wisdom.

If you've created an interface that will enable the user to do their task as quickly and painlessly as possible, then stop. Don't weigh down the interface with unnecessary features. As Dieter Rams famously said, "**Good design is as little as possible**." This holds true for user interface design just as well as product design. Consider Alan Cooper's rule of thumb, "A user will take as much time to make a choice as there are choices." If a user is inundated with options and features, they find the interface more difficult to use. A simple, direct approach is frequently the best one.

If you want a quick and easy measure of the simplicity of a feature, just count the number of clicks to complete the task using your interface. If the user has to switch from mouse to keyboard, count that twice.

## How to prepare

If you've done some design in the past, especially in a collaborative setting, just come and be yourself--you'll do fine. But if you're relatively inexperienced, here are some ways you can improve your design skills:

  1. If you're still in school, **take an HCI or infoviz course**, especially a project-based course. This will give you some actual design experience, as well as a rich vocabulary and set of concepts for thinking about user interfaces.
  2. **The design mindset is a muscle, so exercise it every chance you get**. Constantly ask yourself, "How could this be different? How could it be better?" The more you ask yourself these questions, the more they'll become unconscious and automatic. Soon you'll be wondering about [the design of everyday things](http://www.amazon.com/Design-Everyday-Things-Donald-Norman/dp/0385267746)--in the shower, on the train, and hopefully every time you interact with a piece of software. If you develop the skills to analyze other people's designs, you'll be able to apply those skills to your own.
  3. **Actually build something** and pay attention to the UI. Go through more than one design before (tentatively) settling on the one you're going to build. Draw wireframes and/or mockups. Iterate constantly, even after you think you're done.
  4. **Ask someone to critique your work**. If you can find someone with an HCI background (or other design skills), she'll show you things you couldn't see yourself. Once this has happened a few times, you'll start internalizing your critics; you'll start asking yourself, "What am I missing here?" If you find someone who doesn't have a design background, treat them like a user. This means taking their feedback very seriously but leaving some room for skepticism. Notoriously, [users don't always know what they want](http://uxmyths.com/post/746610684/myth-21-people-can-tell-you-what-they-want).
  5. **Read up on UI/UX/HCI/infoviz**. There are a lot of good books and blogs out there. Some of the ones that we've found particularly helpful are _About Face_ by [Alan Cooper](https://twitter.com/#!/MrAlanCooper), _Now You See It_ by Stephen Few, and _Don't Make Me Think_ by Steve Krug.

I hope this post will help you design better interfaces, and perhaps I'll be [working with you](http://www.palantir.com/engineering-culture/) soon!
