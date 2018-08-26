# 4 Types Of Code Reviews Any Professional Developer Should Know About

_Captured: 2018-07-30 at 07:46 from [dzone.com](https://dzone.com/articles/4-types-of-code-reviews-any-professional-developer?edition=385303&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-30)_

###  Because nobody's code is perfect, check out this explanation of the four main types of code reviews you should be familiar with. 

Discover how you can [take agile development to the next level](https://dzone.com/go?i=294434&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone) with low-code.

![](https://www.scrum-tips.com/wp-content/uploads/2018/05/types-of-code-reviews.png)

Every professional software developer knows that a code review should be part of any serious development process. But what most developers don't know is that there are many different types of code reviews. And each type has specific benefits and downsides depending on your project and team structure.

In this post, I am going to list the different types of code reviews and explain how each type works exactly. I am also going to give you some ideas on when to use which type.

Ok, let's get started.

First of all, on a very high level, you can classify code reviews into [two different categories ](https://en.wikipedia.org/wiki/Code_review#Types)-- formal code reviews and lightweight code reviews.

## Formal Code Review

Formal code reviews are based on a formal process. The most popular implementation here is the [Fagan inspection](https://en.wikipedia.org/wiki/Fagan_inspection).

There you have a very structured process of trying to find defects in code, but it is also used to find defects in specifications or designs.

The Fagan inspection consists of six steps: Planning, Overview, Preparation, Inspection Meeting, Rework and Follow-up. The basic idea is to define output requirements for each step upfront and when running through the process, you inspect the output of each step and compare it to the desired outcome. Then you decide whether you move on to the next step or still have to do work in the current step.

Such a structured approach is not used a lot. Actually, in my career, I have never come across a team that used such a process and I don't think I will ever be able to see that.

I think it is because of the big overhead that this process brings with it and so not a lot of teams make use of it.

However, if you have to develop software that could cause the loss of life in case of a defect, then such a structured approach for finding defects makes sense.

For example, if you develop software for nuclear power plants, then you probably want to have a very formal approach to guarantee that there are no bugs in the delivered code.

But as I said, most of us developers are working on software that is not life-threatening, and therefore, we use a more lightweight approach for code reviews instead of the formal approach.

So let's have a look at the lightweight code reviews.

## Lightweight Code Reviews

Lightweight code reviews are commonly used by development teams these days.

You can divide lightweight code reviews in following different sub-categories:

  1. Instant code review, also known as pair programming;
  2. Synchronous code review, also known as over-the-shoulder code review;
  3. Asynchronous code review, also known as tool-assisted code review;
  4. Code review once-in-a-while, also known as meeting-based code review.

### Type 1: Instant Code Review

The first type is the instant code review, which happens during pair programming. While one developer is hitting the keyboard to produce the code, the other developer is reviewing the code simultaneously, paying attention to potential issues and giving ideas for code improvement on the go.

#### Complex Business Problem

This type of code review works well when you have to solve a complex problem. By putting two heads together to go through the process of finding a solution you increase the chance to get it right. Having two brains thinking about the problem and discussing possible scenarios it is more likely that you also cover the edge cases of the problem.

I like to use pair programming when working on a task which requires a lot of complex business logic. Then it is helpful to have two people think through all the different possibilities of the flow and make sure all are handled properly in the code.

In contrast to complex business logic, you sometimes also work on a task that has a complex technical problem to solve, if, for instance, you make use of a new framework or explore a piece of technology you never used before. In such a situation, it is better to work by yourself because you can work on your own base. You have to do a lot of searching on the web or reading documentation on how the new technology works.

It is not helpful to do pair programming in a such a case, because you hinder each other while getting the required knowledge.

However, if you get stuck then talking to a colleague about the solution often helps you to view the problem from a different angle.

#### Same Level of Expertise

Another important aspect to consider when doing pair programming is the level of expertise of the two developers working together. Both developers should preferably be on the same level because then they are able to work along in the same speed.

Pair programming with a junior and senior does not work very well. If the junior has the steering wheel then the senior next to him just gets bored because he feels everything is just too slow. In such a setting the potential of the senior gets restricted and therefore is a waste of his time.

If the senior has the keyboard in his hand then everything goes too fast for the junior. The junior is not able to follow the base of the senior and after a few minutes, he loses the context.

Only if the senior slows down and makes sure he explains to the junior on a slower pace what he is about to do does this setup makes sense. However, then we are not talking about pair programming anymore. Then we are talking about a learning session, where the senior developer teaches the junior developer how to solve a specific problem.

But if both developers are on the same level then it is amazing how much work they can accomplish in such a setting. The big benefit here is also that the two developers motivate each other and in case of one of them loses focus the other developer brings him back on track again.

To sum it up: pair programming works well when two developers with a similar level of experience work together on solving a complex business problem.

### Type 2: Synchronous Code Review

The second type is the synchronous code review. Here the coder produces the code herself and asks the reviewer for a review immediately when she is done with coding.

The reviewer joins the coder at her desk and they look at the same screen while reviewing, discussing and improving the code together.

#### Lack of Knowledge of the Reviewer

This type of code review works well when the reviewer lacks knowledge about the goal of the task. This happens when the team does not have refinement sessions nor proper sprint planning sessions together, where they discuss each task upfront.

This usually results in the situation where only a specific developer knows about the requirements of a task.

In these situations, it is very helpful for the reviewer to get an introduction about the goal of the task before the review is started.

#### Lots of Code Improvements Expected

Synchronous code reviews also work well if there are a lot of code improvements expected due to the lack of experience from the coder.

If an experienced senior is going to review a piece of code that has been implemented by a very junior developer, then the review generally works way faster when they do the improvements together after the junior claims he is done.

#### The Downside Of Forced Context Switching

But there is a major downside of synchronous code reviews, which is the fact of forced context switches. This is not only very frustrating for the reviewer, but slows down the whole team.

In fact, I have written a separate blog post about [the 5 major problems with synchronous code reviews](https://www.scrum-tips.com/2018/05/22/synchronous-code-reviews/).

### Type 3: Asynchronous Code Review

Then we have the third type, the asynchronous code review. This one is not done together at the same time on the same screen, but asynchronously. After the coder is finished with coding, she makes the code available for review and starts her next task.

When the reviewer has time, he will review the code by himself at his desk on his own schedule, without talking to the coder in person, but writing down comments using some tooling. After the reviewer is done, the tooling will notify the coder about the comments and necessary rework. The coder is going to improve the code based on the comments, again on his own schedule.

The cycle starts all over by making the changes available for review again. The coder changes the code until there are no more comments for improvement. Finally, the changes are approved and committed to the master branch.

As you can see synchronous code reviews work quite differently compared to asynchronous ones.

#### No Direct Dependencies

The big benefit of asynchronous code reviews is that they happen asynchronously. The coder does not directly depend on the reviewer and both of them can do their part of the work on their own schedule.

#### The Downside Of Many Review Cycles

The downside is that you might have many cycles of reviews, which might spread over a couple of days until the review finally is approved.

When the coder is done, it usually takes a couple of hours until the reviewer starts to review. Most of the time the suggestions made by the reviewer are then fixed by the coder only the next day.

So the first cycle already takes at least a day. If you have a couple of those cycles then the reviewing time spans over a week -- and this is not even taking the time for coding and testing into account.

But there are options to prevent this long timespan to get out of hand. For instance, in my team, we made the rule that every developer starts with pending reviews in the morning before he picks up any other task. And the same thing is done after a lunch break.

As the developer is out of his context anyway after a longer break, you don't force unnatural context switching and still have the benefit of getting the code reviewed in a reasonable time.

Comparing the benefits and downsides of this type of code review I think that asynchronous code reviews should be the default type for every professional development team.

But before I tell you why I think that way, let's have a look at the fourth type of code reviews.

### Type 4: Code Review Once in a While

A long time ago I used to do code review sessions about once every month together with the whole team. We were sitting in a meeting room and one developer was showing and explaining a difficult piece of code he has recently been writing.

The other developers were trying to spot potential issues, commenting and giving suggestions on how to improve the code.

I don't think that any teams use the once-in-a-while code review method on a permanent basis. I can only think of one situation when this type could makes sense: when the whole team has no experience at all with code reviews, then getting everyone together in a room and doing the review together a couple of times might help everyone to understand the purpose and the goal of a code review.

However on a long-term the 4th type this is not an adequate technique, because it is rather inefficient having the whole team working through a piece of code.

## Which Code Review Type Should I Pick?

So, now you might wonder which type you should choose.

We talked about the formal type, which is obviously not so popular and hardly used in practice..

Then we talked about the category of lightweight code reviews and distinguished 4 different types.

Type 1, the instant code review, is done in pair programming and works well when two developers with a similar skill set are working on a complex business problem.

Type 2, the synchronous code review, works well when the reviewer lacks knowledge about the goal of the task and needs explanation by the coder. It also works well if there are a lot of code improvements expected due to the lack of experience from the coder.

But it has the downside of forced context switches, which is frustrating for the reviewer and slows down the whole team.

Type 3, the asynchronous code review, prevents the problem of forced context switching and works well for the most common use cases.

Type 4, the once-in-a-while code review is not a permanent option for a professional team and may be used only to get a team started with code reviews.

## Use Asynchronous Reviews by Default

I think that a professional team should have the asynchronous code review in place as the default type because it prevents a lot of drawbacks compared to the synchronous review.

The synchronous review can be used in case the reviewer is not able to make sense of the changes made by the coder. But in such a situation the reviewer is going to ask the coder for additional clarification anyway, and if you work in a team these situations should rarely occur.

In case you don't have a real team and work as a group of people, then the synchronous code review makes sense. If the reviewer does not know at all what you were working on the last couple of days, then it makes sense to give a proper explanation before you do the review together.

Switching to pair programming makes sense if you have two developers with a similar skill set and work on a complex business problem. But usually a team consists of people with multiple levels of experience and it does not work on complex business problems all the time. Most of the time you have common tasks with average complexity.

Therefore, the best choice for a professional team is to use the asynchronous review by default and switch to the synchronous type or pair programming if necessary.

Ok, that's it for today.

What type of code review does your team use? Do you know of another type of code review, which I missed here? Then please let me know in the comments.

Talk to you next time. Take care and HabbediEhre.

[Download this eBook ](https://dzone.com/go?i=294435&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone)to learn how to prepare your business for agile adoption, how to ensure the proper business-IT collaboration that is critical for agile development, and how to choose the right stakeholders to increase productivity and enable accelerated time-to-value.
