# Lessons learned from scaling a product team

_Captured: 2015-12-16 at 13:21 from [blog.intercom.io](https://blog.intercom.io/how-we-build-software/)_

![](https://blog.intercom.io/wp-content/uploads/2015/01/How-we-build-software-at-Intercom-984.png)

There's been lots written about how Internet businesses _should_ build software, from books like [The Lean Start-Up](http://theleanstartup.com/book), and [posts](https://www.gv.com/library/product-management) from Google Ventures, but not many examples where startups open up their process and show how it really happens.

Back in 2013, Spotify talked about [how they build](https://dl.dropboxusercontent.com/u/1018963/Articles/HowSpotifyBuildsProducts.pdf), but other detailed examples are hard to find. Maybe that's because it's a messy reality and people can be uncomfortable sharing that in public.

Given the abundance of abstracted advice, primarily from advisors rather than operators, and lack of actual examples happening from fast growing startups, we thought it would be valuable to share more about how we work at Intercom. In the last 12-18 months, over dozens of releases from incremental improvements to huge redesigns, we've learned a lot about scaling a product building team, and the nitty gritty involved in getting valuable product out the door as fast as possible.

Our process is broken down into four main areas:

  1. A set of guidelines for making decisions
  2. Clear accountability
  3. A lightweight, transparent, comprehensive roadmap
  4. A culture of goal setting

Some things to keep in mind:

  * This process is _not_ right for every company. It is heavily influenced by our culture. Your culture is different, so what you do should be different.
  * This process is by no means perfect. We iterate on it constantly. By the time you read this, we will have tweaked something.
  * This process is generally working for us today. And whilst this works for our current team size (four Product Managers, four Designers, 25 Engineers), it's not how we worked when we had a much smaller team, and it may not work when we have doubled our team.

Nonetheless, we hope that by sharing how we work, we will help others reflect on how they build, and ultimately help them improve.

## 1\. We have a set of guidelines for making decisions

In order to grow and scale our product teams, people need a set of values to help them make good decisions that align with what we believe. To that end, we have a set of guidelines:

#### Many small steps are better than bigger launches

We believe you achieve greatness in 1,000 small steps. Therefore we always optimise for shipping the fastest, smallest, simplest thing that will get us closer to our objective and help us learn what works. All our projects are scoped into small independent releases that add value to customers. Everyone should push everyone else to reduce scope and simplify, in order to move faster and not spend time on things that turn out not to be important.

#### When we think about building, we think about daily and weekly goals

We believe [Intercom](https://www.intercom.io/) has an incredible opportunity, but we are in a race against time. Every single day of work counts. Teams have weekly goals, broken down into daily and subdaily goals. Every individual should know at the start of the day what their goals are for that day, how they relate to the team's weekly goal, and to what is being released.

#### We optimise for face to face collaboration

We believe things are faster face to face. Two people at a whiteboard generate more ideas faster and conclude in agreement quicker than any other set-up we've ever seen. Yes, remote working can be great for many things, but not for speed and efficiency of decision making. For that reason, our teams all sit together in one pod with one war room each, and we have a principle that if you can talk in person, you should do it.

#### We fight against work work

Using software to build software is often slower than using whiteboards and Post-it notes. We fight anything beyond a lightweight process, and use the minimum number of software tools to get the job done. When managing a product includes all of Google Docs, Trello, Github, Basecamp, Asana, Slack, Dropbox, and Confluence, then something is very wrong.

#### The outcome matters much more than the plan

Having a plan is critical for success but nothing ever goes fully to plan. Plans are made with the information available at the time but only become fully clear as you execute them. The best teams absorb and react to new information. They are creative in executing a plan in an ever changing environment and fight to reach the same outcome in the same timeframe.

## 2\. We demand clear accountability

We work in small product teams, each of whom own a part of Intercom. These teams consist of a Product Manager (PM), Product Designer, Engineering Lead, and two to four Product Engineers. Because of this, it needs to be crystal clear who is accountable for what. To that end, we have a list:

  * If the analysis of the problem to be solved is incorrect, it's on the PM. _Ensure appropriate research is done._
  * If the design doesn't address the problem, it's on the Designer. _Ensure you understand the research and problem._
  * If the design solves the problem, but doesn't fit with Intercom, deliver best practices, or is otherwise weak, it's on the Designer. _Ensure you understand our beliefs, patterns and principles._
  * If engineering doesn't deliver what was designed, or delivers it late, it's on the Eng Lead. _Ensure you understand the problem being solved and design, plan appropriately and accurately before writing code._
  * If it goes out with too many bugs and broken use cases it's on the PM. _Ensure the team test realistic usage and edge cases._
  * If the team is spending too much time on fixing bugs and not adding new value per our roadmap, it's on the Eng Lead. _Ensure each project improves overall code quality._
  * If we don't know how it performed, it's on the PM. _Ensure success criteria are defined and instrumented._
  * If it doesn't solve the problem, it's on the PM. _Ensure there is a plan to improve product changes that don't fully solve the problem._

Product building teams have natural grey areas and collaboration often means a better end result. So people within teams work this out themselves. But when it comes to analyzing what we spent our precious time building, the lines of accountability need to be very clear.

## 3\. We obsess over our lightweight, transparent roadmap

Our roadmap is the plan for what we will build over the next few months. It has three timeframes:

  * The next 4-6 weeks are solid, with clear releases.
  * The following few months are planned, with high level project briefs describing the problem and opportunity.
  * Beyond a few months out is speculative, loose ideas that align with our mission.

All other ideas for what we might build go onto a list, managed by the PM, reviewed regularly by the team.

Our roadmap draws from three primary sources.

  1. Things we believe in.  
This is based on our opinion rather than research, in particular the opinion of our product leadership team. This includes trends we see and ideas we have.
  1. Qualitative feedback from customers.  
We have three sources of qualitative feedback:
  * Solicited feedback from customers including studies by our research team, and conversations between product managers and customers. [Our PMs use Intercom](http://blog.intercom.io/the-blind-product-manager/) to talk to customers.
  * Unsolicited feedback from customers that comes in [via Intercom](https://www.intercom.io/customer-feedback). Hundreds of conversations are [tagged](http://docs.intercom.io/Intercom-for-user-analysis/grouping-users-with-segments-and-tags#tags) by our Customer Success team every week, reviewed by PMs, added to their list of things we might build in the future, and some are moved to the roadmap.
  * Feedback from sales conversations. Our sales team share conversation notes with PMs so they understand barriers to people adopting our product. Our roadmap is reviewed monthly by sales and product leadership to ensure we're removing these barriers.
  1. Quantitative data based on measuring performance of our current product.  
We have two sources of quantitative feedback:
  * The success metrics defined in every project.
  * Product and team level success metrics.
![](https://blog.intercom.io/wp-content/uploads/2015/01/Roadmap-overview.png)

Everything in our roadmap is broken down by team objective, which is broken down into multiple projects, which in turn are broken down into individual releases. This is critical for us to live by our values, that we produce the most value for our customers with the fastest thing we can build. We also have strategic product themes that cut across all product teams, objectives, projects and releases. Below is a summary of how we tackle each of these phases.

#### Product strategy themes

We currently have eight themes that we are folding into everything we do. To communicate the themes, we created a board for each that we hang on the wall of our offices.

Each board has a title, a section describing why we believe it is important, the problem we're tackling, the opportunity it affords us, and illustrative concept sketches. _Note that the board below is an old one, we've since shipped integrations with __[Salesforce_](http://docs.intercom.io/Integrations/Salesforce-Integration)_, __[Zendesk_](http://docs.intercom.io/Integrations/zendesk-integration)_, __[Slack_](http://docs.intercom.io/Integrations/slack-integration)_, and __[Zapier_](https://docs.intercom.io/integrations/zapier-integration)_ amongst others._

![](https://blog.intercom.io/wp-content/uploads/2015/01/Product-strategy-board.png)

#### Team objective

Each product team has an objective. This is a strategic goal that will take a few months to achieve. These are our big bets, the aggregation of which form our product strategy.

#### The project brief (aka The Intermission)

![](https://blog.intercom.io/wp-content/uploads/2015/01/Intermission-doc.png)

The Intermission is our quirky name for a project brief. This document is the responsibility of the Product Manager. It is restricted to less than one page and must succinctly cover the problem we're solving, how we will measure success, and the scope of the project. It never includes solutions because this comes later. The goal of the Intermission doc is to have a shared understanding of what we are building and why.

#### The Roadmap in Trello

![](https://blog.intercom.io/wp-content/uploads/2015/01/RoadmapTrelloBlurred.png)

Because we move very fast with short release cycles (between one day and two weeks), we can have up to 5 or 6 Intermissions in play, and 10+ releases being worked on at once. We use [Trello](https://trello.com/) to stay organised. Everything in Trello is owned by the PM. We have a Trello card for every release we do, and that card includes links to design work. We have five product teams and the colour on the card denotes the team responsible. To force accountability, we have a rule that only one team can own a release. If something slips we add a red label so we can keep track of any slippage patterns.

![](https://blog.intercom.io/wp-content/uploads/2015/01/RoadmapTrelloBlurredIntermission.png)

Each Intermission has a card in Trello. That card links to the Intermission doc, and to the releases within that project. It also contains a checklist to make sure we didn't forget anything. Sometimes we knowingly check things off without doing them, the checklist is for checking, not for mandating.

#### The release card in Trello

![](https://blog.intercom.io/wp-content/uploads/2015/01/RoadmapTrelloBlurredRelease.png)

Each release has a card in Trello that links to design work and any supporting docs that explain product and design decisions. Each release card also has a checklist broken into five sections: Design, Build, QA, Beta, Full release, Post release. Again, this checklist is for checking, not for mandating.

## 4\. A culture of goal setting

#### Weekly goals and Hustle

![](https://blog.intercom.io/wp-content/uploads/2015/01/Hustle-weekly.png)

To ensure we stay focused and stay on track we set weekly goals in each product team. These goals map to releases from our roadmap, include reducing bug counts, and system improvements that will enable us to move faster in future. We built an internal tool called Hustle to keep track of goals. Hustle is worth a blog post in and of itself - for next time. As well as goals, it pulls in our roadmap via the Trello API, and pulls in a summary of our open bugs via Github's API. The main thing to understand here is that teams set weekly goals and are held accountable to them.

#### Daily goals and the whiteboard

![](https://blog.intercom.io/wp-content/uploads/2015/01/RoadmapWhiteboard.png)

To hit our weekly goals, individuals have daily and sub-daily goals. This reinforces the idea that every day counts. Each product team has a whiteboard that they use to track daily goals. They set them during their morning stand-up.

#### Weekly demos

Every Friday at 5pm, we all gather round our big screen in our canteen, people grab a beer and the engineers demo what they worked on that week.

![](https://blog.intercom.io/wp-content/uploads/2015/01/Friday-demos.png)

This reinforces all that we believe in. Cadence of building matters. We're in a race against time. Everything we build should be broken down into steps that can be built in less than a week.

## This process has changed

We are constantly examining and iterating our process. Every week we learn new things. This captures all we've learned so far. These are lessons we learned that hard way, by getting it wrong and trying again. Building a product in a fast growing company in times of rapid change is very very hard. Hopefully this helps you reflect on and improve how you build product. We'd love to hear your war stories below.

Like what you read here? Why not come and work with us? We're hiring for [roles in Dublin and San Francisco](https://www.intercom.io/careers).

Want to read more of our product best practices? [Download our free book](https://www.intercom.io/books/product-management), _Intercom on Product Management_. It's recommended by folks like Ryan Singer, Hunter Walk, and Dharmesh Shah.
