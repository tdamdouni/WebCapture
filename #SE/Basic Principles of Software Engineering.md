# Basic Principles of Software Engineering

_Captured: 2015-10-14 at 23:05 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/basic-principles-of-software-engineering)_

## Basic Principles of Software Engineering

### Engineers are Not Just Builders

Software engineering is all about finding and applying the best ways to solve technical problems with software (which is why it's so much fun). If you watched [Paolo Perrotta's Baruco 2012 video](https://www.youtube.com/watch?v=9IPn5Gk_OiM) in the previous lesson, you saw how attempts to replace software engineering as just another commoditized production process failed. In particular, how the comparison between Engineers and builders breaks down.

That's because software _engineers aren't just builders_ and _software isn't a commodity_. The compiler (which turns source code into something the computer can execute) is what actually does all the building. The engineer, on the other hand, must figure out what the compiler is actually supposed to build. That requires creative problem solving.

Engineers are thus much more like _architects_ or even _designers_ \-- they live firmly in the **design** phase of the problem solving process and are frequently required to solve loosely defined or unusual problems. Their techniques for doing so therefore are less concerned with _building quickly_ than they are with finding and designing the _right_ solution amidst trying out new things.

That's not to say that software engineers aren't constantly coming up with tools (like languages and frameworks and boilerplate code) to make the design of their software "blueprints" more efficient... but there will always be a need for someone to figure out _what_ to build in the first place.

Because of the inherant creativity required to solve software problems, the source code of multiple engineers building the "same" thing will probably look very different. Despite this, if they stick to established principles, patterns, designs and methods to do so, then they will all likely arrive at similarly effective solutions and will have accomplished the task at hand.

These principles, patterns, designs and methods for producing good software form the core of software engineering. Many were inherited from other engineering disciplines while others are hard won epiphanies from years in the trenches of building software. In this lesson, we'll take a look at some of these high level guiding principles and best practices.

_Our goal for this lesson isn't for you to remember all these principles and acronyms but for you to absorb what it means to be an engineer and how engineering "works". The specifics will flow from that higher level understanding later on._

### How an Engineer Solves a Problem

There's no major mystery to engineering -- you just apply a systematic process for creatively solving problems. What that looks like is this:

  1. **Understand the problem**
  2. **Plan a solution**
  3. **Carry out that plan**
  4. **Examine your results for accuracy**

What most people don't understand is that most of the significant effort goes into the first two parts of the process. If you fail either of those, it hardly matters whether you've carried out your plan perfectly or accurately. So if you want to think like an engineer, **solve your problems fully BEFORE diving into the implementation of your solution**.

This is easier said than done -- engineers often love creating things to the point where they would rather dive into building something interesting than make sure they're solving the _right_ problem. Wait, that seems sort of familiar...

In the [Design mini-course](http://www.vikingcodeschool.com/web-design-basics) we said that if you're designing a product because you think it's fun to design and not because it's what users want, _it's going to fail_. A similar principle applies to engineers writing code -- if you find yourself coding mostly because building is fun and you didn't fully explore the problem or plan your approach ahead of time, then _you will waste a lot of time_.

_If you pay attention over the remainder of this mini-course, you'll see all kinds of parallels between the ideas of good User-Centered Design and good software engineering._

### Principles and Best Practices of (Software) Engineering

Engineers _really_ like acronyms and rules of thumb because they represent clarity and simplicity. In fact, just about everything you need to know about software engineering can be summed up with the following principles, rules, and acronyms. Most apply to other forms of engineering as well. In the list below, they start high level and then get more code-specific towards the end.

The most important ones to absorb are the high level ones -- you'll be able to come back later and ponder some of the more software-specific ones once you've had some time behind the wheel of real code.

#### Starting High Level

  1. **Think through the problem completely before you try to implement a solution** \-- simply the most important thing you can possibly do. Seriously.
  2. **Divide and conquer** \-- break down larger problems into multiple smaller problems that can be worked on independently. They didn't build the space shuttle or the pyramids in one giant step. This is how scary problems become manageable.
  3. **KISS (Keep It Simple, Stupid!)** \-- you saw this one back in the section on UX, remember? KISS might just be the engineer's motto. We've acknowledged our tendencies to build overly complex systems at times (there are anonymous meetings for this kind of thing) and it's forced us to admit that simplicity makes your solution _so much better_. 

That's not to say simplicity is easy! It's often the result of hair pulling and teeth gnashing as complex solutions are refactored to break apart their core components. KISS applies in countless other ways as well -- among beginners, for instance, there's a real tendency to over-think logical problems and come up with strange and novel solutions when the "dumb" simple way is simply better. 

  4. **Learn, especially from your mistakes** \-- Engineering is always changing and software engineering in particular might be one of the most rapidly changing fields on the planet. You need to always be learning, both from other people in the industry and from acknowledging your own mistakes and crappy code. That's the recipe for a long and stimulating career in the field.

  5. **Remember the reason the software exists** \-- there are countless small decisions that you'll be faced with during your work as a developer and, if you don't know the bigger picture, you might waste time going down the wrong path. This is pretty much the foundational principle behind why we've created these mini-courses for you!

  6. **Remember that YOU won't be using the software** \-- it's very tempting for engineers to design solutions for themselves. Remember what we talked about in the Design mini-course and it will serve you well here! Think about the user not yourself. Don't assume your user will have the same level of technical competency or familiarity with the system as you do.

#### Thinking About the Process

  1. **Have a clear vision for the project** \-- if you don't know exactly what you're trying to build, you're going to build the wrong thing. Often, especially if you're freelancing or working in a team, that means asking important questions of clients/customers. The old adage is "You built exactly what we asked for but not what we need".
  2. **Have a rigorous process** \-- software engineering is a creative design activity but must be practiced systematically. You don't need to get bogged down in process, but you can't just rush into a solution with guns blazing. We're solving some pretty complex problems, so you need to be mindful of taking a logical and thoughtful approach to solving them and a rigorous approach to managing your projects or they'll quickly get away from you.
  3. **Develop applications rapidly** \-- this is one that we'll cover a bit more in the Agile section but it's certainly worth noting here. Software project requirements change constantly. The faster your process works, the better you're able to respond to those changes. 
  4. **Make it WORK first, then work RIGHT, THEN look pretty** \-- this is an adaptation of the above "develop applications rapidly", and again emphasizes a try-it-first philosophy. More specifically, it says that you should first build something that works (even if it's held together with string and duct tape) and then seeing if it's worth investing the time to make it work right. Not until the final phase of the process should you actually make your solution "look" good (e.g. refactoring your code).

#### Thinking About (Coding) the Solution

  1. **YAGNI (You Ain't Gonna Need It!)** \-- there's a really strong temptation to build code that could respond to any future eventuality by being incredibly flexible and "perfect". Don't do it! You're wasting effort because you really aren't going to need all those extra features or options or flexibilities. Just build what you need. Trust us and every other engineer who's looked over old code and facepalmed at all the wasted effort.
  2. **DRY (Don't Repeat Yourself)** \-- one of the best things about code is how reusable it is. If you write a cool bit of code that solves a useful problem in one place, refer back to it when the problem comes up in other places as well. From your perspective, any time you find yourself manually typing something in multiple times, there's a way to combine it all into a single task that gets run multiple times.
  3. **Embrace abstraction** \-- Software engineering is all about abstraction, or ignoring the details and solving higher order problems. You don't have to write machine code or assembly code for a reason -- today's programming languages allow you to basically just tell the computer what you want and it will deliver. This also applies to how you approach complex systems -- focus on making sure the system functions properly without needing to know the implementation details of every component part.
  4. **DRITW (Don't Re-Invent The Wheel)** \-- okay, we made up the acronym for that one but it's key. Any time you're building code to do something general that's not directly related to the fundamentals of your application, someone else probably already wrote that code and better. It's either posted on a blog somewhere, on Stack Overflow, or open-sourced as a gem. Learn from and use their code instead of wasting your time reinventing the wheel.
  5. **Write code that does one thing well** \-- a single piece of code should only do a single thing and do it well. If you try to make a do-everything miracle solution and jam it all into one piece of code, you've got a maintainability nightmare and it probably violates multiple best practices. KISS!
  6. **Debugging is harder than writing code** \-- readable code is better than compact code. So stop trying to combine those 10 lines into one run-on chain of methods that use obscure input patterns! Someone else will have to read and debug it later and you're not doing them any favors.
  7. **Kaizen (leave it better than when you found it)** \-- fix not just the bug you're trying to solve but the code around it. A band-aid bug-fix doesn't help if the real problem is a design flaw (which it usually is).

### Rules of Thumb

  * Finding and fixing a software problem in production is **100 times** more expensive than finding and fixing it during the requirements and design phase. Catch those bugs and design flaws early!
  * In the same token, more than half of errors in design are committed during the design phase.
  * Just about all the time spent fixing issues can be traced back to just a small handful of trouble modules.
  * About half of user programs contain nontrivial defects
  * Only 60% of features in a system are actually used in production

_Adapted from [Rules of Thumb in Software Engineering](http://www.sw-engineering-candies.com/blog-1/rules-of-thumb-in-software-engineering) by Markus Sprunck_

### Wrapping Up

...so do you get the major themes yet? **Think first. Break problems into pieces. Keep things simple.** If you've figured that out (and we probably don't need to hammer them in any harder at this point, do we?), then you're officially on the same page as the rest of the engineering community. Everything else is just implementation detail.

To finish up, **check out [Principles of Software Engineering (part 1)](http://nathanmarz.com/blog/principles-of-software-engineering-part-1.html)** by Nathan Marz. It could instead be called "Engineering for Uncertainty". He goes into some specific terminology which might not make a lot of sense but his perspective should give you a good feel for how a software engineer views the world. He also has some great points about the difference between how systems are designed and how your users will actually use them (and what that means for the software engineer).

###  Next Lesson: Approaching Complex Problems 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/approaching-complex-problems) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/a-brief-history-of-software-engineering)
