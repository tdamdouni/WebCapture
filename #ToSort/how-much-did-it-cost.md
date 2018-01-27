# How Much Did it Cost?

_Captured: 2017-11-11 at 00:42 from [dzone.com](https://dzone.com/articles/how-much-did-it-cost?edition=334862&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

An interesting question came up at an event last week:

> "My Kanban team has been asked by accounts to put a cost on each story that is done. How do I calculate this?"

My initial thought was: easy, and it is easy to give a simple answer to this question but if you unpack the question and the motivation behind it things get more interesting. Although the question was asked about a Kanban team most of the answer applies equally to Kanban, Scrum, or [Xanpan](https://www.allankellyassociates.co.uk/xanpan) teams, but contrasting the Kanban and Scrum approach offers interesting insights.

So, first off, the easy answer:

  * Select a period of work, say a month.
  * Count how many things (the things you want to know the cost of, stories, backlog items, tickets) got done (whatever your definition of done) during that period, e.g. 6 user stories might have been completed in the month.
  * Calculate the burn-rate for your team, e.g. if you have 5 team members who each cost $100,000 a year then the monthly burn-rate for the team is $41,666.
  * Divide your burn-rate by the number of items done, e.g. $41,666 / 6 = $6,940.

This approach adheres to the maxim, "It is better to be roughly right than exactly wrong" \- which is often credited to John Maynard Keynes but I believe it actually comes from philosopher Careth Read.

Although you might see many things potentially wrong with this crude calculation it has one redeeming feature: it is quick and therefore the cost of doing this calculation is low.

If you want you can improve on this calculation with more data. At the aggregate level, you could consider a longer period with more items. Or you might calculate the statistical distribution and provide a range of answers.

Alternatively, if you record the start and end dates of the work you could make this calculation more fine-grained:

  * Work on an item starts on 1 November 2017 and completes on 6 November, 4 elapsed working days.
  * The daily burn rate for the team is $1,923 per day (based on the same team of 5 and 260 working days per year).
  * Therefore, a 4-day story cost: $7,692.

Now notice, this figure is $700 higher than the previous figure. Which is the right answer?

As an engineer you want to know the actual figure, there should be an equation here, right?

Well yes, there should, but as with any equation, you need to make some assumptions. Accountants know this, just ask them about "exceptional" items on the balance sheet and you will find out how subjective accounting is.

By the way, notice this second calculation is also fast and cheap. Were we to ask everyone who touched the story to record the time spent then two things would happen. Firstly, those who recorded their time would be less productive in doing the work itself so the cost of knowing the cost would increase.

Second, you are replacing one set of assumptions with another. Namely: that people can accurately record or recall the time they spend doing something. They can't, so the figure is subjective again, check out my [Notes on Estimation and Retrospective Estimation](https://www.allankellyassociates.co.uk/static/webonly/EstimationAndRetrospecitveEstimation.pdf) if you don't believe me.

Back to accounting...

Now the question that arises is "why even ask this question?" \- surely recording costs at such a detailed level is a waste itself? What value is it knowing the cost of each small piece of work?

Now I agree with this, and I would hope you have a conversation with those asking the question as to what they are trying to achieve, what are they going to use this data for? - how they are going to use the data will influence how you calculate it.

**But...**

But, if you are leading a team and are approached by an accountant with the question "how much does each item cost?" I would advise you not to open the waste question there and then. My advice is to comply with their request in the most efficient manner, i.e. calculate it by one of the methods above.

Let me suggest that were you to immediately move to the question of "Why are you asking me this?" let alone "Answering your question is a waste, therefore, I will ignore it," is likely to create more problems than it will solve.

Far better to answer such questions, win some credit and trust then later return with the bigger questions. And since there are different ways to come up with a number you have an opportunity:

> "Bill, you know those ticket costings I've been giving you for the last three months?"  
"Sure, Betty, they are really useful for the capex/opex report."  
"Well Bill, I think there is a better way of calculating them. Can we talk about how you are using them?"

The fact that there is some ambiguity in the question and answer is an opportunity to have a discussion. First, though, you need to win the right to have the discussion.

Now back to the original question.

The motivation behind the question was in part because Scrum teams assign estimates to stories and these estimates can be used as proxies for cost. In terms of accuracy, such an approach is wild at best - it is little more than a random number generator for most teams and at worst it will distort both the estimate and the cost calculation. Numbers based on such estimates are unlikely to be accurate at all.

However, the techniques described above will work just as well for a Scrum team as a Kanban team. You probably want to work at the Sprint level:

  * A team of five did 3 stories in a 2-week Sprint (10 working days).
  * Each team member costs $100,000 a year, therefore, each Sprint costs $20,000.
  * Each story cost $6,666 ($20,000 / 3).

Such an approach is going to be far more accurate than anything based on estimates and probably more accurate than anything based on time recording. Again you could use more data to build up an even more accurate picture.

Now my big BUT...

This is all about COST.

Everything so far has been about cost. And I know most teams deal in cost. I know most of you are constantly asked: "how much will it cost?"

But I also know there is someone, somewhere, who will promise to do the same thing for less. While you are on the cost side of the equation you will always lose.

What we should be doing is considering Value. How much are these work items worth?

Rather, or in addition, to reporting cost you want to be reporting Value added:

> "Bill, here are the figures from the last month, in total we did 10 items at a cost of $41,000 and we added $86,000 to sales."

> "Bill, here are the figures from the last month, in total we did 10 items at a cost of $41,000 and we added 1,000 site views."  
"Bill, here are the figures from the last month, in total we did 10 items at a cost of $41,000 and we made 500 children smile."

I know measuring value is hard but we have to try. If nothing else, [estimate value the same way you estimate effort](https://www.allankellyassociates.co.uk/archives/517/estimating-business-value-adding-value/).

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
