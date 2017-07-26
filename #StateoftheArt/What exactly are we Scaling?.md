# What exactly are we Scaling?

_Captured: 2016-04-13 at 21:54 from [blog.scrum.org](http://blog.scrum.org/what-exactly-are-we-scaling/)_

Scaling Scrum. Agile at Scale. Enterprise Everything. Everyone is using the Scaled Agile Framework SAFe. Scaling, Scaling, Scaling. If you're working in product development, you've probably had a few conversations on this topic. It seems to be all the rage right now. In this blog post I hope to lend some clarity to what we mean by scaling. It turns out not everybody is talking about the same thing, and different organizations have different things they want to scale. So here's a break down of possible scaling scenarios, along with my very simple, high-level, thoughts on where you might want to start.

One quick note on the word "product." A Product is something a customer buys or internal stakeholder uses, as seen from **their** point of view. Too often the development side of the house sees products as a reflection of how their teams are organized or how the code has been written, or some other inside-out view. This is probably a result of Conway's Law, it frequently causes problems, and is a topic for a different blog post (or book?).

## 1\. One Product, One Team

You don't need to think about scaling the process. Just relax, and focus on growing a solid agile team. Professional Scrum may be a good place to start: its mixture of XP, modern development practices, lean product ownership, and the Scrum framework is a good choice for most teams. You may however want to start reading on #5. Note that for every scaling scenario that follows, I'm presuming you actually have a healthy, sustainable, vibrant agile team at the core. Before you focus on how to scale _**anything**_, I highly suggest spending some time getting the most out of the people and teams you already have. Improvements at the team level almost always have a greater ROI than improvements in scaling. Or if you don't believe that, at least know this: if you're doing "_just OK_" at the team level, you'll be doing no better that "_just OK_" at scale, and probably much much much much worse.

## 2\. One Product, Many Teams

This scenario's chief obstacle is how do you get many dozens of people to create a single product, a big complicated product, all working towards the same goal, and creating the thing all at the same time?! Things that help here include:

  * A single backlog owned by a single product owner who is the person with the overall customer-centric vision for the product. You may scale some of the tactical PO duties (writing PBI details, acceptance criteria, daily clarification of work) downstream by having strong business/product/analyst skills on the development teams. You can scale some of the market-side PO work upstream by having a team of product managers/marketers help with pricing strategies, customer feedback, and market research.
  * A way for teams to select work from the product backlog, without stepping on each other's toes. With just a few teams this is fairly straightforward and PBI's can be pulled via having a simple conversation amongst team members. ProTip: Refinement sessions should focus on dependancies up and down the Product Backlog as well as across teams. With dozens of teams, you may think about asking the PO and teams to label the backlog with a few simple categories in order to help this go a bit faster. A scaling framework may help here, but I do caution against large and long meetings just for selecting work - the cost almost always outweighs the benefit, and it screams of the old-school-thought that we can perfectly estimate->assign->execute the work. Keep this simple, it's not the biggest obstacle in this scaled scenario.
  * A way for teams to create a single product. Turns out if you want hundreds of people to simultaneously create one product, there are technical necessities. Single source control, continuous integration/build/test/deploy, use of SOLID principles, API's, DevOps concepts, etc. The bigger you scale, the more of this you need.
  * A way for teams to communicate with each other. You probably need a mixture of formal interactions and informal communication cues. Some of the scaling frameworks can help with the formal checkpoints. My experience is that the informal communications are even more important. Focus on growing a culture of communication where anybody can go talk to anybody else, regardless what team you're on or who you report to. Some chat tools like hipchat/slack/yammer and video tools like skype/hangouts/sqwiggle can help when there are hundreds of people across the globe too.
  * A way to see progress on the product across all the teams. Sprint Reviews become a challenge with dozens or hundreds of teams. Think about different formats like the "[science fair](http://www.erikweberconsulting.com/blog/2015/2/3/sprint-review-technique-the-science-fair)" or the "video reviews" made popular by the teams at Microsoft. Tools like [UserVoice](https://www.uservoice.com/) or even some [Visual Studio tools](https://msdn.microsoft.com/en-us/library/hh362461.aspx) can be useful for gathering asynchronous feedback from stakeholders/customers. You also may have to do some arithmetic magic in excel for creating a multi-team release burndown for teams that have various velocities (even if you're using a scaling framework I do not recommend the practice of "normalizing estimates" across teams, it breaks some core relative estimation principles, and it's simply not needed).

My recommendation here is to start with [Professional Scaled Scrum and the Nexus Framework](https://www.scrum.org/Resources/The-Nexus-Guide).

##  3\. Many Products, One Team

This is an often-overlooked situation in the whole scaling discussion. Many teams are in the difficult position of developing and supporting many different products and product lines all at the same time. The scaling question here is "how do we figure out what the team should be working on?" and the following things should be considered:

  * Our constraint in this system is the throughput of a single team. We should optimize for that constraint by ensuring they are only working on the most valuable work we can find. Therefore, product ownership, backlog refinement, and hyper-prioritization based on value become even more important. You should be terrified of working on the wrong things.
  * Lean thinking tells us that context switching is a form of waste, so "work a little bit on all the products" is probably not an optimal strategy. You will have to get good at "saying no" and being able to explain that the team is focused on higher value items at the moment.
  * Shorter sprints or flow-based systems typically work very well here. I personally like combo of: Kanban + DoD + Refinement-On-Demand + XP-Modern-Development-Practices.
  * Extreme focus on quality. If you're in the situation of also having to support all these various products, nothing buries a company quicker than poor quality. You have virtually no chance of survival if in addition to all the above, we have to constantly worry about production support issues. Keep quality high, tech debt low, and never compromise your definition of done.
  * Managing many different product backlogs and comparing the value of items between all of them can be a pain. Not to mention there are projects coming to an end and a funnel of possible new ones to begin. You need to consider some sort of agile portfolio management, whether that's a tool, process or framework. The key to agile portfolio management is to visualize the portfolio, get the PO and other stakeholders talking about it on a regular basis, and have a lightweight way to get the necessary data you need to make decisions.

##  4\. Many Products, Many teams

First, for each product, see #2. Now the only problem that remains is how to manage all these various products we're building, which we just covered in #3. You have both situations happening simultaneously. This is where most organizations reach for a solve-for-everything scaling framework. And that's not such a bad idea here, assuming that the individuals and teams on the core of this huge scaled system are already operating at very high levels. As in #1 above, I suggest you focus most on the teams, and don't spend all of your time, effort, on money, and solving for the higher level scaling issues. A process optimization that helps a dozen people at the top but hinders thousands of people on development teams is, well, not an optimization.

## 5\. Beyond the Team

What do you do when other departments needing to plug into agile product development? What are the leadership behaviors, management tools, and organizational structures that best support an agile enterprise? Along with the software and product development practices, the agile umbrella includes many other concepts that are useful to other departments in a modern agile organization. Here's just a few to look into.

  * Operations: [DevOps](http://itrevolution.com/manifesto/) and [Continuous Delivery](http://www.thoughtworks.com/continuous-delivery)
  * Finance: [Beyond Budgeting](http://www.amazon.com/Beyond-Budgeting-Managers-Annual-Performance/dp/1578518660)
  * HR: [Drive](http://driveworkshop.com/), [Holocracy](http://holacracy.org/), and [The Alliance Framework](http://www.theallianceframework.com/)
  * Sales & Marketing: [Pragmatic Marketing](http://www.pragmaticmarketing.com/) and the [O'Reilly series of Lean Books](http://search.oreilly.com/?q=lean&x=0&y=0)
  * Leadership & Management: [Management 3.0](http://www.management30.com/), [Radical Management](http://www.stevedenning.com/radical-management/default.aspx), and [Stoos](http://www.stoosnetwork.org/), and [The Responsive Org](http://www.responsive.org/)

## Conclusion

Want to be part of this discussion? Do you have more suggestions for "beyond the team" techniques? Want help implementing these ideas? Please [contact me](http://www.erikweberconsulting.com/)!

  

