# Gumption Traps: Bad Code

_Captured: 2017-05-10 at 00:38 from [dzone.com](https://dzone.com/articles/gumption-traps-bad-code?edition=298034&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-09)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

In my [previous post](https://dzone.com/articles/zen-and-the-art-of-software-maintenance), we briefly touched on the topic of gumption traps. Since the topic seemed very interesting to me and, at the same time, important to many software developers, I decided to elaborate on it a bit more. We will take a look at a huge gumption trap that I somehow omitted in the previous post: bad code.

## What Were the Gumption Traps, Again?

Let's start with the word gumption, as some non-native English speakers might not know it (I didn't before I read[ Zen and the Art of Motorcycle Maintenance)](https://www.amazon.com/gp/product/0060589469/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=tidyjava-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=0060589469&linkId=c88349419fbdcb9d5f124d1fc2d8b9c3). Oxford English Dictionary defines it as follows:

> Shrewd or spirited initiative and resourcefulness, e.g.   
_'the president would hire almost any young man who had the gumption to ask for a job.'_

Indirectly speaking, it's the _thing_ that makes you able and willing to go to work every day and solve hard programming problems. Obviously, from time to time, there are situations and feelings that rob you of the _thing_ and make you want to leave your job and work at McDonald's (or at least stop doing what you're doing). These situations and feelings are called _gumption traps_, more aptly defined by Wikipedia as follows:

> "A gumption trap is an event or mindset that can cause a person to lose enthusiasm and become discouraged from starting or continuing a project."

There are two main types of gumption traps. When the cause of gumption loss is external, the trap is called a _setback_. When the cause is internal, it's called a _hang-up_.

## Bad Code

One of the most common _setbacks_ that all of us come across fairly often is bad, low-quality code. God classes with methods spanning over thousands of lines of code, poor naming, obsolete comments and no tests, hahaha! And there's you, trying to change that button's color to match your bosses preference or just adding a small checkbox for your business people. It's hard to have a lot of gumption in such an environment.

The most obvious way of dealing with any gumption trap is simply avoiding it. What I mean here is not job-hopping every time you see a piece of legacy code (although it could work in theory). What I mean is minimizing the chance that someone falls in the bad code trap because of you. You know, there's [Clean Code](http://amzn.to/2p1bQiJ), [SOLID principles](https://en.wikipedia.org/wiki/SOLID_%28object-oriented_design%29) and a plethora of other McDonald's job preventers available that are just a single google search away. Therefore, as a first step, minimize the amount of newly produced bad code.

Unfortunately, more often the code is already in place and you have no choice but to deal with it. Your mileage may vary but for me, the bad code gumption trap has at least two disastrous implications. First, I have no motivation to even start working with the code and it only gets worse once I do so. Second, I get frustrated very quickly. Let's see how to deal with these issues.

### Staying Motivated

High motivation in such situations can be achieved by following [Charles Duhigg's method of "turning a chore into a choice."](http://amzn.to/2p1dyke) Before you start working, try to make as many choices as possible about the work you are about to begin.

Are you going to start by preparing missing tests for the feature? Or maybe by refactoring what's already tested? How much of the code are you willing to refactor? In what order? Are you going to add a new feature once the code is fully clean and tested or at the first possible occasion? And so on.

The method of "turning a chore into a choice" is based on scientific research, which shows that in order for people to remain motivated, they have to feel like they are in control. By making choices about the upcoming "chore," you remind your brain that you are the one in control here and your motivation rises.

### Avoiding Frustration

The second problem that we have to deal with is frustration. I don't know about you but to me, the two most frustrating things about working with bad code are a lack of progress in understanding it and the feeling of unfairness that comes from the fact that I have to work with bad code that I didn't write myself.

The most common reason for the lack of progress that I feel is that I often try to work with bad code the same way I work with the good code. I simply read the code line by line and somehow hope that I will magically start understanding what's happening in there. That's not possible. Human working memory does not work that way. It can carry only a few items at the same time and only for a short period of time. That's rarely enough to grasp all of the behaviors of a god class or a multi-thousand LOC method.

To work effectively with bad code, you must leverage tools other than just your brain. Pen and paper are good enough for the not-so-bad cases. For worse cases, a couple of whiteboards and a diagramming tool might be indispensable. Instead of trying to remember and connect everything in your brain, create an intermediate representation of the information using the tool. Once you forget something or want to get back to it again, you'll get back to your nice drawing or diagram, not the ugly piece of code.

If your code is not well-tested, which is often the case, you can use automated tests as an analysis tool while, at the same time, preparing a safety net for future refactorings. This technique is called Characterization Testing and was introduced by Michael Feather in his great book [Working Effectively with Legacy Code](http://amzn.to/2pcsOa9).

When it comes to the second part of the problem, the feeling of unfairness, you can find some ease by answering a simple question: _why am I working with this old, bad code instead of something new and shiny? _Try to put yourself in the shoes of the people paying you for the job. Answer this question thoroughly, honestly, and without emotions. What is the business reason? Why is the change important for someone? Why wouldn't they just spend a few million, wait a few years, and solve the problem from scratch? Would you?

## Summary

Bad code is a common and important gumption trap. The first and obvious step to avoid the trap is to stop producing such code yourself. When faced with bad code that someone else wrote, one must work smart to maintain motivation and avoid frustration. Doing this is not really that hard. Plan your work thoroughly, use tools that make your work easier and don't forget that there's always a reason why working with this bad code is a better solution than starting from scratch. Now, go face your company's legacy code like a master and, if you know any other advice for fighting the bad code gumption trap, let me know in the comments!

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
