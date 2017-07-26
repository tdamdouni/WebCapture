# Cycle time and lead time

_Captured: 2017-02-14 at 05:33 from [www.extremeuncertainty.com](http://www.extremeuncertainty.com/cycle-time-ead-time/)_

## What are cycle time and lead time?

[Cycle time](http://www.extremeuncertainty.com/glossary/) and [Lead time](http://www.extremeuncertainty.com/glossary/) are important concepts from [Kanban](http://www.extremeuncertainty.com/glossary/) and [Lean Manufacturing](http://www.extremeuncertainty.com/glossary/). People often use them as metrics in Agile Software Development, however. And they can provide important insights into how your teams are operating. Cycle and Lead Time are measurements that describe how work is flowing **into** and **through** a system.

![cycle time and lead time](http://www.extremeuncertainty.com/wp-content/uploads/2016/03/stopwatch-150x150.jpg)

> _Cycle time clock starts now!_

By the way, the "work" and "system" could be anything. User stories describing software for a development team, a request for an agency to come up with an advertising campaign, an order for a hamburger at a corner store. The concepts here are abstract and you can apply them anywhere.

## How do you calculate Cycle Time?

Cycle time is simply the amount of time it take for a unit of work (again, this could be a software task to be completed, a coffee to be made, whatever) to go from a In Progress state to a Completed state. The clock "starts ticking" on the cycle time as soon as the work moves from a "Ready" state to an "In Progress" state, and it stops ticking when that work item goes from an "In Progress" state to a "Completed" state. Exactly what those states mean will depend on the work and the context. If the work item moves back and forth (e.g. the customer changes their mind or doesn't accept the work and insists it be changed or done again), then the clock doesn't reset, it continues to tick.

![cycle time agile lean kanban](http://www.extremeuncertainty.com/wp-content/uploads/2016/03/cycletime.png)

Cycle time is a very important metric that describes the efficiency of a system in processing units of work. It has nothing to say about what happens outside that system, however, such as the queue to get work into that system. That is where lead time comes into play.

## How do you calculate Lead Time?

Lead time is the amount of time it takes for a unit of work to go from an In Queue state (i.e. a customer of some kind has requested some work to be done) to a Completed state. It encompasses, and is therefore always longer than, cycle time. Lead time describes two aspects of a system: the time it takes for work to be processed in that system (cycle time), and the time it takes for work to **begin** to be processed in that system, which is a function of the frequency that orders come into that system.

![lead time agile lean kanban](http://www.extremeuncertainty.com/wp-content/uploads/2016/03/leadtime.png)

### Huh? Lead Time seems confusing

If that confuses you, imagine a cafe with a barista, a cashier and some customers. As soon as the customer places an order for a coffee with the cashier, that work goes In Queue. That is, the customer has placed an order for a coffee and expects a coffee soon. The Lead Time clock has started ticking. If there are no other orders in the system, the barista can start making the coffee right away. As soon as they do, the Cycle Time clock starts ticking.

Cycle Time is purely how long it takes for the barista to make a coffee. The only way to improve it is for the barista to get faster at making coffees. If the barista can start making a coffee the instant an order is placed, then Lead Time is equal to cycle time. But if orders start coming in faster than they can make coffees, then a backlog of orders will start piling up. If the barista can make a coffee in one minute, but a coffee order comes in every 20 seconds, then cycle time stays at one minute, but lead time is going to start increasing, and will keep increasing as the barista gets further behind.

## How do you fix Lead Time?

If lead time for a system is much higher than cycle time, and is getting higher, there are only two ways to fix this:

  * improve the efficiency of the system (i.e. teach the barista how to make a coffee faster, which will improve cycle time and let you chew through orders faster
  * increase the capacity of the system (hire another barista).

There is also a third way, to simply stop taking coffee orders, but this has obvious shortcomings. Well, if you're a coffee shop. But maybe not if you're a software delivery team.

### Fixing lead time with WIP limits

If your lead time is getting bigger, you have too many requests coming into your system for your capacity. If you can't or won't improve or increase your capacity, you can actually stop taking orders. More specifically, you can implement a [WIP limit](http://www.extremeuncertainty.com/glossary/). WIP stands for Work In Progress, and describes the amount of work items in a given Kanban state (e.g. Ready for Development). If you have too many work items in a given state, you can just shut the door and say you're not taking any more work into that state.

In the case of a cafe, it means putting up a sign saying "sorry we're too busy to make your coffee". You will lose customers and sales, and that's a bad thing. But for a software delivery team, it means saying "sorry, please stop giving us ideas for new features, we can't do them. You need to spin up a new team." This is a pretty reasonable request.

## What do the Lead Time and Cycle Time metrics tell us?

Cycle Time tells you how quickly your team can process a piece of work. You want it to be low. If you are doing software delivery, your work items are probably user stories and your sprints are probably two weeks. You want your cycle time to be under two weeks, well under. Ideally you want cycle time to be five or so days. If your cycle time is ten or more days, you are not completing your stories in one sprint. That is is a bad thing.

Lead Time tells you how you process work based on the amount of requests coming into the system. It is a function of the efficiency of the system. If you get your cycle time down you can chew through your backlog faster. And more quickly process the work requests coming into the system. Both of these metrics are interesting and tell an important story.
