# How Do You Measure Productivity?

_Captured: 2017-12-10 at 20:36 from [dzone.com](https://dzone.com/articles/how-do-you-measure-productivity?edition=343111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-10)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

How do you measure productivity? It's a simple question, but does it have an easy answer?

If I increase my productivity by 20% or even 50%, how do I know for certain? How does your manager know? Is it a subjective, finger-in-the-air guess?

I thought I would explore the process of measuring how productive a person is. I presumed that a simple question would have a simple answer. To get at that answer, I realized that I needed to ask more questions.

### What Amount of Work Was Done?

The most obvious answer to how productive someone is would be to measure how much work that person has done. For example, John has done 50 things today (a rate of 50 items/day), whereas Jane has done only 5 (a rate of 5 items/day). Obviously, John is more productive, right?

Let's consider another analogy: John delivered 50 parcels today. They were all on the same street, whereas Jane delivered only 5 parcels today -- but they were delivered in towns 100 km apart. Now, who do we think was more productive?

_The amount of work done does not seem to be a good measure._

### How Many Hours Were Spent on Work?

The next obvious answer is the more hours you work, the more productive you are. So John works 12 hours per day, whereas Jane works 7 hours per day. John, again, is more productive, right?

Well, John spent those 12 hours writing Testing Procedure Specification reports that no one reads, browsed MySpace, and twiddled his thumbs. He also complained about losing his stapler (Why, oh why, doesn't Netflix carry _Office Space_!). By contrast, Jane worked on a method to save the company $5 million per year. Who was more productive?

_The amount of time someone spends at work does not seem to be a good measure._

### What Was the Work's Value?

Perhaps we should try evaluating value. The higher the value of your work to the business, the more productive you are, right?

So John works on 5 high-value, 2 medium-value, and 1 low-value pieces of work. Jane worked on 1 high-value piece of work. However, John's 5 high-value and 2 medium-value pieces of work were not very difficult, as they took only a few hours to do. The low-value work took him weeks, whereas Jane's one high-value piece of work was difficult and required days of effort. Who was more productive?

_The amount of value of the work does not seem to be a good measure, but I think we are going in the right direction. Value does need to be taken into account._

### How Much Effort Was Needed and What Was the Difficulty Level?

Because the value of work must be taken into account, let's work on the high-value items first. However, I think we need to take into account how much effort something takes.

Suppose we rate the work based on how much effort each item takes by using measures such as small, medium, and large. Assume that John worked on a large item for a week, while Jane worked on three medium items for a week. Are three mediums more work than one large? Are three mediums equal to one large? How can you easily tell? Who is more productive in this case, John or Jane?

### Defining Units of Measure

I think we are getting close. We need a common unit of measure and some simple way to convert from (S)mall/(M)edium/(L)arge to a number. Let's say that S = 1, M = 2, and L = 3.

So, we have John who worked on 3 smalls, while Jane worked on 6 smalls. This also doesn't sound right. Some small tasks take no time at all, whereas others can take significant effort. We need something more than just three categories. Maybe we can use extra small (XS) for those items that take little to no effort; small (S) for items that take a little bit of effort, but still not much; medium (M) for those that are a quite bit more effort; large (L) for something that takes a lot of effort, and finally extra large (XL) for something that will either pull a muscle or burst a blood vessel, based on the amount of effort.

The units of measure look something like this:

  * XS = 1

  * S = 2

  * M = 3

  * L = 4

  * XL = 5

Wait, something doesn't seem right. Where is the cutoff point from, "I'm exhausted from the effort" (Large), to "My head hurts" (Extra Large), or from _tilts hand up/down, left/right in so-so motion_ (Medium) to "I'm exhausted" (Large)? The differences need to be much bigger than one unit greater.

How about this measure: The next level up is the sum of the two previous units? It looks something like this:

  * XS = 1

  * S = 2

  * M = 3 (same as before)

  * L = 5

  * XL = 8

Hmm, a 5 to 8 jump isn't "Ow, my head hurts!" level of effort, but if we add an XXL, we get XXL = 13. That's a big enough jump.

This sequence looks familiar. I remember my high school math teacher, Mr. Fibonacci, mentioning something like this. This looks very interesting. I'm going to call these _work units _(Hey, who said story points? What's that?). Now we can work out how much work has been done.

Assume that John with his _Large_ unit of measure has completed 5 work units, whereas Jane has completed 6 work units. I think we are making progress.

Let's standardize this to a time period. They both completed the tasks in one week. The productivity rate for John was 5 work units per week and Jane's was 6 work units per week (Hey, who mentioned velocity!).

Hang on, we're not quite done yet. Individual productivity rates are all well and good, but John and Jane are a team. Measuring individual productivity rates does not promote a team mentality. If Jane is doing less than John, she should be helping John or vice versa. I should combine these into one overall rating, so the team rating is 11 work units per week. I should only compare rates week to week, per team, and not across teams because each team sizes work differently. I also need to make sure that the team agrees on the size of the work as a whole. There's no point in having Jane say something is small when John thinks it's large. They will both need to discuss and agree.

If in a few weeks, Jane and John's combined work increases to 17 work units per week, they have gained about a 50% increase in productivity. A measurable, comparable unit of measure for productivity. I think we've got it!

### Conclusion

This experiment on trying to determine how a manager might work out how to measure productivity is a fun way, at least for me, of trying to understand why, in Agile, you would use something like story points and velocity.

Using velocity for measuring productivity is not perfect and is subjective because it is based on an individual's or the team's idea of the size of work. It is also open to abuse. Jane and John could say all their work is Large and increase their productivity (throughput) significantly. Therefore, this rating should not be used for any incentives, simply because it can be abused and thus the rate becomes meaningless. However, it does indicate, for an experiment or trial, whether a productivity gain has made headway.

As you can see, this also ties into estimation, which is another reason to move away from doing estimates as time units.

One more thing: although this story is complete fiction, I still think it deserves a happy ending.

### Epilogue

With the help of their manager, John and Jane were able to visualize their productivity rates. Thus, they were able to put them into effect. They could make changes to the way they worked and get quick feedback on how those changes affected their throughput for work. Six months later, their productivity rose 1000%. They did this through experimentation, eliminating wasteful practices, and adopting a framework called Scrum.

And they lived happily ever after.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
