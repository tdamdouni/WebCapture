# The End of Agile

_Captured: 2019-08-23 at 12:31 from [www.forbes.com](https://www.forbes.com/sites/cognitiveworld/2019/08/23/the-end-of-agile/)_

![hockey puck and stick on the ice texture background](https://specials-images.forbesimg.com/imageserve/958701308/960x0.jpg?fit=scale)

> _

Agile is a powerful methodology but in an increasingly data-driven world, it may not necessarily be the right one. 

Getty_

I knew the end of Agile was coming when we started using hockey sticks. Every morning, at precisely eight o'clock, the team of developers and architects would stand around a room paneled in white boards and would begin passing around a toy hockey stick. When you received the hockey stick, you were supposed to launch into the litany: _Forgive Father, for I have sinned. I only wrote two modules yesterday, for it was a day of meetings and fasting, and I had a dependency upon Joe, who's out sick this week with pneumonia._

The scrum master, the one sitting down while we were standing, would duly note this in Rally or Jira (I forget which), then would intone, _"You are three modules behind. Do you anticipate that you will get these done today?"_

"_I will do the three modules as you request, scrum master, for I have brought down the team average and am now unworthy."_

"_See that you do, my child, for the sprint endeth on Tuesday next, and _**_management is watching_**_."_

The holy hockey stick would then get passed on to the next developer, and like nervous monks, the rest of us would breathe a sigh of relief when we could hand off the damned stick to the next poor schmuck in line.

This was no longer a methodology. It had become a religion, and like most religions it really didn't make that much sense to the outsider - or even to the participants, when it got right down to it. 

## YOU MAY ALSO LIKE

![agile management concept](https://specials-images.forbesimg.com/imageserve/1067923108/960x0.jpg?fit=scale)

> _

Agile started out as a radical concept. By breaking the product cycle into smaller, manageable units and working with small teams, software projects, in particular, could be accomplished more efficiently. That much still holds true.

Getty_

## Small is Good

The Agile Manifesto, like most such screeds, started out as a really good idea. The core principle was simple - you didn't really need large groups of people working on software projects to get them done. If anything, beyond a certain point extra people just added to the communication impedance and slowed a project down. Many open source projects that did really cool things were done by small development teams of between a couple and twelve people, with the ideal size being about seven.

When your team was that size, design could be done almost as a group activity. Two weeks seems a reasonable amount of time to show demonstrable progress. Meetings stay short, and having the customer in the room keeps them in the loop. The alternative - "Waterfall methodology" meant that a client would often have to wait six months to see the product, and the unveiling at the end of that phase usually ended up with the customer hyperventilating in the corner somewhere.

Agile was hip, it was cool, and it involved Fibonacci Numbers. What was not to like about that?

Over the years, I began to realize a subtle but very important distinction. The Agile Manifesto had it wrong from the beginning - it was not so much that small teams worked better because they could follow a lean and mean methodology to accomplish a project. Rather, small teams on small projects made it possible to follow a lean and mean methodology and have any luck at success.

Open software projects worked because the tasks that were needed to complete one were relatively self contained - they could be coded quickly, functionality could be shown within a few weeks, design could be emergent because putting an interface up early and expanding that out was acceptable and even encouraged, and once it was done, maintenance was someone else's problem.

As significant, in open source software the customer could end up staying engaged on a project for a couple of months, because those months were typically the ones that were most oriented towards design. The longer a project dragged on, however, the more likely that other demands would take more and more of that customer's time, to the extent that their involvement became cursory at best.

![scrum board](https://specials-images.forbesimg.com/imageserve/1058533774/960x0.jpg?fit=scale)

> _

Agile has done more for the Post-It Note than any other technology in history.

Getty_

## Becoming Agile

At the time that Agile emerged, the typical software project fell within the parameters of what Agile does well. Most were web based, where a web interface could be put up within a few days. They used databases as a way of storing state, and the web developer usually had unfettered access to that database. They were projects that took between four and six months (eight to twelve two-week-sprints) to accomplish, and they were predominantly client facing (both in the sense that user interfaces were a big part of the experience, and the sense that the client could see changes occuring practically before her eyes). 

They were also projects where, if functionality was lopped off, the application would in fact not be significantly degraded by that loss. This was about the time that the concept of a _minimal viable product_ began to take hold - the notion that, beyond the first couple of sprints, the product would be useful even if development stopped right then, for some arbitrary definition of useful. 

Needless to say, businesses began to take note, and becoming Agile soon became the mantra of the week. Agile went from a rough manifesto to a formal methodology where a project manager (now with the weighty term _scrum master_) would work with managers to come up with "stories" that described what they wanted their product to accomplish (those things once known as requirements), and "tasks" that then became the steps necessary to complete those stories, and that formed the contract between the manager (through the proxy of the scrum master) and the developer or designer.

Within this framework, a dance should then emerge in which the overall shape of the application comes into play, then successive levels of detail, then implementation. By tracking this information, in theory, one can actually ascertain whether a project is behind, and if it is, assign additional resources to shore up the problem area.

Again, from the business perspective, this is a big win. Software projects are by nature kind of scary for managers - you are investing a large amount of money without much in the way of assurances that you'll see anything for that investment, so being able to see red, yellow and green colored boxes show up on a chart can be calming. 

![Innovation is almost never straightforward.](https://specials-images.forbesimg.com/imageserve/5d5fae8e68cb0a000917e4be/960x0.jpg?fit=scale)

> _

The problem with estimating is that it is dependent upon having all of the facts ahead of time. Programming by its very nature is only moderately knowable innovation. Agile implementations, originally designed to get a better handle on these

Getty Images_

## **Where Agile Breaks Down**

The problem, of course, is in the details - and in the nature of human behavior.

Most project management works upon the idea that tasks are measurable, based upon the metrics set up by other people doing that same task. Setting up an assembly line is a very predictable task (in the old economy, anyway), and because it is done so often, you can estimate the time it takes to do so to within a few days either way. Unfortunately, creating software is not predictable. In almost all cases, it is usually cheaper (if not necessarily always better from an organization standpoint) to buy off the shelf software, even when the sticker prices are high. The reason for that is simple - the functionality you are looking for already exists, and the price for the pain of building the application the first (several) times has been paid. 

How long does it take to build login functionality? It takes about an hour to code up the user interface. It can take thirty minutes to code in the back end ... or thirty days. If you want full integration with your Active Directory authentication system on a non-standard platform that only supports LDAP, and you want to integrate a two-pass email authentication system into the mix, then the UI is the least of your worries. How about a pretty network graph dashboard that shows how all of the components in your system are interrelated and allows for drag and drop operations? Don't get me started. I still have nightmares about that one.

There is a fallacy in computer programming circles that all applications are ultimately decomposable - that is to say, you can break down complex applications into many more simple ones. In point of fact, however, you often cannot get more complex behaviors to actually start working until you have the right combination of components working, and even then you will run into problems with synchronization of data availability, memory usage and deallocation and race conditions - problems that will only become apparent when you've built most of the plumbing. 

This is why "but will it scale?" entered the lexicon of programmers everywhere. Scale problems only show up once you've built the system out almost completely and attempt to make it work under more extreme conditions. The solutions often entail scrapping significant parts of what you've just built, much to the consternation of managers everywhere.

This is one of the reasons why developers really hate having to put any numbers on tasks if they can help it. This becomes even more of an issue when developers have to integrate their efforts with other developers, especially for those components developed at the same time. If there is an impedance mismatch between how two components interact, redesigning those pieces can take time and complexity that are difficult to measure. 

It also suggests that Agile does not always scale well. Integration dependencies are often not tracked (or are subsumed into hierarchical stories), yet it tends to be one of the most variable aspects of any software development.

Realistically, this is not so much a fault with Agile as it is with its most common tools. Technically speaking, such a project diagram is a graph of information, not just a tree. You have dependencies in space, time, organization, abstraction and complexity, and estimating time to complexity is often the weakest link throughout these tools. On the other hand, this effort is also made worse when you have too many people involved in the projects, because the complexity of managing such projects increases geometrically with time.

One consequence of this approach as well is that, with large teams, the amount of time involved in planning can often consume as much as a quarter of the overall time available for development. Another is that the constant emphasis on minimum viable product means that at any given point developers end up spending a significant percentage of their time building and demonstrating their work to date, eating up another ten to fifteen percent of their available time, often for code that will be thrown away.

Because this essentially leaves a "week" of development time in what amounts to a two week sprint, this also has the drawback of limiting what you can accomplish in that sprint to only the most bare bones components possible. This is especially true once you shave off another a day for scrum meetings. They are intended to go only fifteen minutes, but the reality is that they can easily go on and on when there are problems. Spreading out sprints to three weeks makes more sense, but in practice few organizations adopt that. 

One other side effect of these meetings is on managers, who by their very roles are often involved at scrums at multiple levels in their organizations, which means that this leaves them with little time to actually lead at a strategic level and forces them to micromanage, typically with lackluster results.

It is often manpower consulting organizations that are most gung-ho about Agile, despite the fact that their goal on any project is to maximum the number of developers and support staff employed on projects as possible. This is ironic, because what happens is that Agile is thus employed most heavily in operations where classical Waterfall methodology, with an emphasis on precise specifications and detailed pre-planning, would actually be preferential. 

![online curation media concept. electronic newspaper. young woman holding laptop PC and various news images. abstract mixed media.](https://specials-images.forbesimg.com/imageserve/824126056/960x0.jpg?fit=scale)

> _

Data-centric problems do not fit well into the stand-alone open-source domain that Agile does handle well. As more and more business projects move in that direction, the utility of Agile as a methodology declines.

Getty_

## Data Projects and the Post Agile World

As an aside to all of this, it should be noted that there are whole classes of projects where traditional Agile is counterproductive. Enterprise data projects, in particular, do not fit the criteria for being good Agile candidates, for several reasons:

  * Enterprise data systems (EDS) place a heavy emphasis on data modeling, which can range in complexity from a few days to months, depending upon the sources and the size of the organization.
  * EDS projects tend to focus on queries, transformations and data movement (ingestion and services), none of which are typically client facing.
  * EDS projects are usually ongoing, requiring a mixture of automated data ingestion and active data curation, as opposed to time-boxed application development.
  * Because of the typically generalized nature of EDS, navigators, knowledge bases, data hubs and similar applications are more appropriate than specialized applications, meaning that the need for customized development is also held to a minimum.

To be fair, while there have been a few development methodologies in the enterprise knowledge space, the domain itself is new enough that no single methodology has established itself for enterprise data systems in the way that Agile has for application development. This shouldn't be surprising - the focus on Enterprise Data itself is comparatively new.

A key facet of enterprise data projects comes not in the technical integration of pipes between systems, but in the mapping of data models from one system to another, either by curation or machine learning. In other words, the kind of work that is being done is shifting from an engineering problem (dedicated short term projects intended to connect systems) to a curational one (mapping models via minimal technical tools). 

This transition also points to what the future of Agile will end up being. In many respects we're leaving the application era of development - applications are thinner, mostly web-based, where connectivity to both data sets and composite enterprise data will be more important than complex client-based functionality. This is also true of mobile applications - increasingly, smart phone and tablet apps are just thin shells around mobile HTML+CSS, a sea-change from the "there's an app for that" era. 

The client as relatively thin endpoint means that the environment for which Agile first emerged and for which it is most well suited - stand-alone open source applications - is disappearing. Today, the typical application is more likely a data stream of some sort, in which the value is not in the programming but in the data itself, with the programming consequently far simpler (and with a far broader array of existing tools) than was the case twenty or even ten years ago. 

Perhaps the last major holdout of such applications is with the category of games, and even there, the emergence of a few consistent tool-sets such as the Unreal Engine means that there's increasing convergence on the technical components, with Agile really only living on in areas such as design and media creation. 

What that points to in the longer term is that work methodologies are moving towards an asynchronous event model where information streams get connected, are mapped and then are transformed into a native model in unpredictable fashion. We release platforms, then "episodes" of content, some as small as a tweet, some gigabyte sized game updates. While aspects of Agile will remain, the post-Agile world has different priorities and requirements, and we should expect whatever paradigm finally succeeds it to deal with the information stream as the fundamental unit of information. 

So, Agile is not "dead", but it is becoming ever less relevant. There's something new forming (topic for another article, perhaps), but all I can say today is that it likely won't have hockey sticks.

#agile #innovation #methodologies #data #waterfall #sdlc #theCagleReport
