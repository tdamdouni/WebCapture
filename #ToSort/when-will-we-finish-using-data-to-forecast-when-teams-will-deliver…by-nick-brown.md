# When will we finish? Using data to forecast when teams will deliver…by Nick Brown

_Captured: 2017-06-16 at 18:11 from [scrum-master-toolbox.org](http://scrum-master-toolbox.org/2017/06/podcast/when-will-we-finish-using-data-to-forecast-when-teams-will-deliverby-nick-brown/)_

**When will we finish? **

**Using data to forecast when teams will deliver…**

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/pic1.png)

**Confessions of a Scrummaster**

Before we start, confession time.

If you had asked me 18 months ago how I would predict the delivery date for a piece of work, I would typically have taken a team's velocity and used a burn-up chart to estimate an end date.  
As well as focusing on story points (rather than working software), I would often find these estimates to be way off, which had the potential to let customers down with aligning to their expectations.

Looking back, I can see where the flaws were, without taking data from the system to get the 'true' picture. It was incredibly naive to think that in an environment as complex as software development, we could estimate for a single date for delivery. I was ignoring one of the cornerstones of Agile in empirical evidence and instead trying to apply 'traditional' estimating approaches for delivery.

The actual data I needed was right in front of me; I just wasn't using it…

**The case for data**

Data-driven companies are becoming more the norm -- 39% of executives say their companies are already highly data-driven, according to [our most recent survey](http://www.pwc.com/bigdecisions).

Given this is the case, if we are serious about Agile and encouraging companies to embrace the agile mindset, then we owe it to ourselves as practitioners to use data to help individuals/teams/execs on that journey.

We should no longer rely on outdated approaches like RAG statuses that are inconsistent and heavily influenced by groupthink/cognitive bias. Instead, we should look to be objective and transparent, using the data we gather from teams as a means to collaborate.

If a user story is an invitation to a conversation, then the same should be said for data…

**How can we use data to forecast when we'll finish?**

A large amount of teams are unaware of just how much data they are gathering, and how little is needed to forecast. Troy Magennis has a wealth of [free tools ](http://focusedobjective.com/free-tools-resources/)available for people to take advantage of, with very little data (gathered via physical or digital means) needed in order to forecast.

With some of our agile teams at PwC, we use a product called Senseadapt to leverage our data (also available for JIRA) to forecast end dates for development.  
This is done by taking the traditional burn-up and using Monte-Carlo simulation to visualise the _landing zone_, which is a range of dates we may potentially finish.

**How does it work?**

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture1.png)

Step (1): We build a mathematical model from the actual behaviour of the board.

Scope is calculated through new items being added to the backlog and completed work is items moving to 'Done' on the board.

As real data is used, it captures key information such as; how long have cards

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-2.png)

spent in a particular state, how many got blocked, the amount of rework, etc.

Step (2): Take the remainder of the backlog and run it through the model 1000 times - each time, the model will slightly randomise the behaviour of some of the cards as they go across the model 'board'.

This allows us to draw the forecast lines for both Throughput (based on a team's historical performance) and Scope (ranging from zero additional scope through to an increase at the current average rate).

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-3.png)

Step (3): Visualise the 'landing zone' which is where the forecast ranges intersect.

Through this visual, we can provide a delivery date range which is far more realistic than the traditional 'single' date we are so used to operating with. The vertical lines show the earliest likely finish dates through to the latest, which enables teams to be transparent (using their data rather than traditional 'estimates') and show the business the key role they have (managing scope) in agile delivery.

This is a screenshot of the visualisation from one of our teams:

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-4.png)

As you can see, we use story count (1) on the Y-axis as opposed to story points (more on why that is [here](https://twitter.com/NBrown02/status/846778941679521792)) and you can easily visualise the earliest (2) and latest (3) range of finish dates, opening the door to a conversation with stakeholders.

**Aligning to Agile Princ****iples**

Metrics are often treated with disdain in the agile world, viewed negatively due to the connotations with governance, micro-managin

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-5-2.jpg)

g Project Managers and those who enforce 'process'.

It's time to reclaim these and get back to data-based coaching for agile teams. Metrics such as the burnup are invaluable if you want to follow the principles of agile. _Inspection_ of the throughput and scope allows for _adaption_ for the remainder of the backlog due to the _transpa__rency_ shown visually to everyone involved.

Let's get away from estimating and use our data to forecast the range of finishing

**Working with deadlines using data**

Typically, teams will be working with a deadline imposed on them by the

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-6.png)

business and, while the above visual is helpful in setting expectations for delivery, it isn't immediately clear 'what will we get' if we're working with a deadline.

This scenario is easily accounted for through a different visualisation. Again, the Monte Carlo simulation forecasts completion of the work 1000 times. However, this time, you get a different visual, the potentially deliverable scope (PDS) chart.

Through this visual, it is easy to see what stakeholders are 95% likely to get, with this being anything above the probable line. Likewise it's also clear what stakeholders are highly likely not

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-7.png)

to get, which is below the possible line.

What it does, however, is that it encourages questions and the conversation around the _potentially deliverable scope_ in between the two lines.

It is in effect saying 'this is where we could get to in the backlog' with the onus on the close collaboration between the teams and the business through working closely together, refining stories, slicing stories, etc.

On a recent project, we used the two visuals above in combination whereby the _landing zone_ didn't present a date that was months away from what the business expected.  
We then used the _PDS_ to visualise what we could get to in the next 6 weeks, with the business looking at this from the perspective of an MVP and, once they saw where the probable and possible lines were, committing as many resources as possible on their side to try and help collaborate with the team to get as many of those stories in the 'possible' section to 'Done'.

**Validating the model**

What's really advantageous about this approach is that it allows us to historically look back and validate our model. With a recently completed project, we were able to compa

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/picture-8.png)

re multiple forecasts from the 27th January through to the actual finish date of 17th March.

The forecast was run every few weeks and then, as we grew closer to finishing, every few days.

As you can see from the animation above, even back in January, we were able to accurately forecast a 6-week finish range. This allowed the team to manage the expectations of the customer, rather than hopelessly targeting an end date that was not possible, one which could have been given with a traditional 'give me an estimate' approach.

**![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/small-senseAdapt-nologo_570x321_animated.gif)**

**Summary**

This is a new take on agile metrics and how you can leverage a lot of the data which you probably already have to forecast delivery dates. It provides a far more realistic view of the future than a "guesstimate" influenced by groupthink and allows you to be totally transparent with your stakeholders. Through moving away from the notion of a single finish date, which we know is highly unlikely in the software development world, we are encouraging that core value of customer collaboration over contract negotiation.

We have found that when this visualisation is presented to stakeholders, they can start to see just how important their role is on delivery dates and that it encourages the conversation around those items that could be deferred to a future release. We can protect the team from the pressure that come from trying to meet deadlines with a scope that is unachievable as well as reducing the waste from traditional 'estimating' approaches.

To find out more, check out Senseadapt or leave a comment below/contact me on [Twitter](https://twitter.com/NBrown02).

**About Nick Brown**

![](http://scrum-master-toolbox.org/wp-content/uploads/2017/06/Capture-135x150.png)

Nick currently works as Agile Lead at PwC in London.

Nick has previously operated as a Scrummaster for teams within PwC and as a Scrummaster/PM for Royal Mail on their Digital programme. Rather than focusing on a particular framework, Nick uses data-based coaching to help teams find a way of working based on agile values and principles, whilst maintaining the focus on the continuous flow of value to the customer.

**NEW BOOK **  
**ACTIONABLE AGILE TOOLS!**  
For Expert and Amateur Agile Coaches And Scrum Masters

![Actionable Agile Tools](https://a.optnmstr.com/users/242f7a85d0a1/images/802176b244c61490707529-Mock-up.jpg)

**GET FREE CHAPTER NOW!**

Discover a New Approach in Solving Issues Before, During And After Retrospective

(The book will be released soon, we'll send you an email when it's released)
