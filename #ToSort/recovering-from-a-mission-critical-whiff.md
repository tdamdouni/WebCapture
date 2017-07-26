# Recovering From a Mission Critical Whiff

_Captured: 2017-06-12 at 13:49 from [dzone.com](https://dzone.com/articles/recovering-from-a-mission-critical-whiff?edition=304169&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-11)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

A career in software produces a handful of truly iconic moments. First, you beam with pride the first time something you wrote works in production. Then, you recoil in horror the first time you bring your team's project to a screeching halt with a broken build or some sort of obliteration of the day's source history. And so it goes at the individual level.

But so it also goes at the team or department level, with diluted individual responsibility and higher stakes. Everyone enjoys that first major launch party. And, on the flip side, everyone shudders to recall their first death march. But perhaps no moment produces as many hangdog looks and feelings as the collective, mission critical whiff.

I bet you can picture it. Your group starts charging at an aggressive deadline, convinced you'll get there. The program or company has its skeptics, and you fall behind schedule, but you resolve to prove them wrong. External stakes run high, but somehow your collective pride trumps even that. At various points during the project, stakeholders offer a reprieve in the form of extensions, but you assure them you will get there.

It requires a lot of nights and weekends, and even some all-nighters in the run up to launch. But somehow, you get there. You ship your project with an exhausted feeling of pride.

And then all hell breaks loose.

![](http://www.daedtech.com/wp-content/uploads/2015/01/TerrifiedOfFurnace.jpg)

Major bugs stream in. The technical debt you knew you'd piled up comes due. Customers get irate and laugh sardonically at the new shipment. And, up and down the organizational ladder, people fume. Uh oh.

How do you handle this? What can you learn?

### Big, Visible, Transparent Progress

No one likes an "I told you so." But I'm afraid that I'll tread perilously close with the first couple of suggestions in this post. I say this because you first need to realize where you went off the rails.

As a consultant that works with many organizations, I constantly see the same process mistake. Companies think that they can make up for falling behind early. 2 months into a year-long project, they've completed 2% of the work. "That's okay," they tell themselves. "We can make it up later. We've learned a lot and worked out the kinks, so no need to sound the alarm bells."

Except, they _should_ sound some kind of bells, though I don't recommend ones of alarm. If you fall behind your plan right out of the gate, you need to make that clear immediately. Don't you think interested stakeholders and people funding that would rather know earlier than later for the sake of planning? You don't need to ask them to panic -- you just need to make your progress completely transparent. You _may_ still make up the slack. But if you don't, at least it won't startle anyone.

### Ship Early and Often

You could also have eliminated this issue altogether by not shipping a big bang, all-or-nothing project at the end of the year. By doing this, you create an excessively long feedback loop.

Even better than simply making your progress transparent, is to _prove_ your progress with incremental shipments. You don't need to build your entire, v2.0 interactive company site all in one shot. First, ship a few new reports. Then switch over to a new login screen. From there, ship a new version of the administrative pages. And so on and so forth.

When you ship frequently, no one miss will destroy your group's reputation. You ship all the time. It would surprise people if you _didn't _have a miss every now and then.

### Own It

Okay, let's go past the "20/20 hindsight" points. Let's assume that you've stepped in it and you can't go back in time to undo it. What next?

First of all, step up and own it. Don't start pointing fingers, casting blame, or making excuses. Your users, customers, and stakeholders don't care that you've been going through a lot lately or that the sales guys promised too much, or anything else like that. They won't want to hear it.

They won't necessarily want to hear, "yep, we messed up," either. But they will react to that better in the long run. Sometimes you can mollify people to a surprising degree by simply saying, "yes, we did that, and it was unacceptable -- we'd be upset too in your position." So start there.

### Don't Apologize -- Offer a Remediation Plan

The aggrieved parties don't really care how sorry you are. You _can_ apologize, but don't _only_ apologize. That means little, especially if you've already "owned it."

What people want to hear about next is how you'll make it up to them -- what sort of redress you will provide. So, when you come forward with a _mea culpa_, have a plan.

"As you've had the misfortune to see, we shipped some unacceptable software. To make it up to you, we will first roll back to your old service and give you a discount for the next six months. From there, we will instrument our build and delivery process with automated checks that look for these sorts of issues so that you will never see another release like this from us."

Your constituents won't throw you a party, and they will most likely remain angry. But you'll begin to earn back a bit of credibility in their eyes with the combination of ownership, remediation, and a decisive plan.

### Retrospect

So far, everything I've discussed involves outsiders. And, rightfully so. After all, when you blow it, you let those outsiders down. Getting them to a whole state should take top priority.

But I decided to conclude with a bit of team introspection because it carries the most importance for your long term team and organizational health. Everything else here has addressed preventative maintenance and damage control. Introspection drives meaningful improvement.

You need to get your team together and perform a meaningful retrospective. [Agile teams and organizations do this](http://searchsoftwarequality.techtarget.com/definition/Agile-retrospective) at the end of each shippable increment of work. For a long tail spectacle like this, however, you need to go a bit deeper.

Do a root cause analysis, using something along the lines of [the so-called "5 whys."](https://en.wikipedia.org/wiki/5_Whys) Get to the root of what caused the mistake. And make sure to do so in a blame free context. That last part tends to cause the most difficulty, particularly after a failure. To get there, bear in mind that people generally try their best and make good faith decisions in the moment.

When it comes to mistakes and flops like this over the course of your career, the question is not "if" but "when." But they needn't define you or your team. Make sure to learn from them and do better the next time.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
