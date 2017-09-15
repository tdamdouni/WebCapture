# Agile Talent Management

_Captured: 2017-08-18 at 18:57 from [leadinganswers.typepad.com](http://leadinganswers.typepad.com/leading_answers/2015/10/agile-talent-management.html?utm_content=buffer73023&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![Talent Management](http://leadinganswers.typepad.com/.a/6a00d834527c1469e201bb0881c39a970d-200wi)

> _Talent Management_

Talent Management is the science of human resource planning to improve business value. It includes the activities of recruiting, retaining, developing and rewarding people along with workforce planning. From an agile perspective much of what we do on agile projects helps with talent management. We encourage empowered teams and give people autonomy over how they work which improves satisfaction and motivation. We also promote knowledge sharing through a variety of collaborative practices which reduce the impact to the team of people leaving.

However, these measures only address some recommendations for talent management. This article examines the ideas and project implications of the other recommendations. First, let's examine why talent management is important and understand the labor cost vs opportunity cost differential.

**Recruiting costs**

If we lose a team member and need to replace them; a job posting needs to be created and sent out to agencies and online forums. We then need to sift through replies and come up with a short list of candidates to consider further. Next comes reviewing candidates with the project manager, arranging interviews, interviewing candidates (preferably with team involvement), following up on references, salary negotiations and hopefully finally hiring someone. I went through this recently for a developer on a software project and estimated the total time to the organization to be 64 hours. At an average labor rate of $80/hr that is $5,120. Had our first choice candidate not joined or failed reference checks the total time to hire would be much higher.

**Getting up to Speed Costs**

A point often overlooked is not this initial hire effort, but the subsequent, much larger learning cycle before becoming a productive team member. A convenient Tayloristic view of management believes one developer can be swapped out for another. However, for a large, complex project it often takes smart, motivated individuals 3 months of learning to get up to speed with the business and technical domain and a further 6 months before they become truly productive. In these first 3 months not only are they not contributing to net new functionality but they are spending 50% of their time asking questions of other team members - slowing their output too.

These costs are huge, assuming a fully loaded developer rate of $80 / hour (typical for North American software engineering) 3 months of not contributing and slowing other developers by 50% full time equivalent (FTE) costs: 3m X 4.2wks x 40hrs x $80/hr + 50%(3m X 4.2wks x 40hrs x $80/hr) = $60,480.

Follow this with 6 months of increasing capability going from 0% productive (no longer a net drain) to 100% productive (up to speed) we can use an average figure of 50% non-productive so 6m x 4.2wks x 40hrs x $80/hr x 50% = $40,320

So, the cost of losing a team member and having to recruit and train another could easily be $5,120 + $60,480 + $40,320 = $105,920. However it gets worse, whenever a high performing team loses a team member they move from the Tuckman "Performing" phase to the 'Storming" phase again as the team dynamics change and have to get back through "Norming" to "Performing".

**Impacts to the Rest of the Team**

The likelihood of making it back to "Performing" and cost of moving from "Performing" to "Storming" is difficult to estimate. The COCOMO II estimation model has Team Cohesion scaling factor that is used to _"__account for the sources of project turbulence and entropy because of difficulties in synchronizing the project participants_". It varies from a high of 2.2 to a low of 4.4, let's assume that moving a high performing team from "Performing" to "Storming" and then back to "Performing" takes 3 months and has an average scaling factor somewhere between these numbers, say 3.3. An average team of 10 people operating at 2.2/3.3 = 69% optimal output compared to how they were before costs: 100%-69% = 31%* 10ppl x 3ms x 4.2 wks x 40hrs x $80hr = $124,992 impact to the team.

Add this to our previous recruiting and "Getting up to Speed" costs and we have a total of $230,912. Over a quarter of a million dollars every time we lose a team member. You may not agree exactly with my numbers, but hopefully agree with my point that the true cost of turnover is significant.

**Opportunity Costs**

Unfortunately we are not done calculating the cost of turnover. The cost to an organization is much larger. Companies do not stay in business paying people $80 an hour to make $80 an hour in revenue, instead they look to make a 3 - 5 X return on that investment.

The cost of delay, disruption to business, loss of market share and general opportunity costs of having a project run late are significant. We could try multiplying that $230,912 figure by some opportunity cost multiplier but I fear we are already beyond "A guess multiplied by a guess" and while closer to the true value, it no longer resists scrutiny. Suffice to say Talent Management is important and finding ways to get better at it is a great place for focus attention. As an aside, I don't know if this has ever been used as an argument for a pay rise, but a $25,000 bump to salary sure looks better than the alternative of losing someone and then having to replace them!

**Talent Management Strategies:**

A recent PMI Thought Leadership Series Report entitled "_Talent Management: Powering Strategic Initiatives in the PMO_" made the following recommendations to improve talent management capabilities:

  1. Identifying replacement candidates in the event of turnover or churn

  2. Move people around to share knowledge and reduce the impact of resource losses

  3. Create succession plans across organizational boundaries

  4. Linking advancement and succession processes

  5. Stimulating adoption and analytics use among business leaders

  6. Being a preferred employer 

These are recommendations made by HR specialists and there may be some conflicts for project managers. So, let's see if we can look at optimizing value to the organization at one level higher up than just an HR view or a project view.

**1\. Identifying replacement candidates in the event of turnover or churn** - Buddy systems, agile pairing practices, and collective knowledge sharing systems help address these same goals. While agile focusses on sharing the knowledge rather than making sure we "have a replacement for Bob" the goals are similar. Don't let knowledge become silo'd into a single person and have a plan for persisting key knowledge in the event of turnover or churn.

**2\. Move people around to share knowledge and reduce the impact of resource losses** - This one is more interesting. It suggests moving people as a means of achieving the goal of sharing knowledge. The trouble with moving people around (between teams and departments) is that it sends the teams back to the Storming phase with the high cost to productivity we explored earlier.

From a HR perspective we might be reducing flight impact risk, but from a company value perspective, options that share knowledge without disrupting teams output are preferable. Team members are not plug-and-play interchangeable at no cost, I recommend collaborative information sharing within teams to reduce this risk while still delivering project value to the organization.

**3\. Create succession plans across organizational boundaries** - This seems smart advice; don't limit succession plan candidates to only the local organizational group. A big part of anyone's onboarding and journey to becoming productive is learning about the company business, history, goals and norms of working. People in other departments have a huge head start in these areas and their tenure proves they can survive and develop in the company's cultural soup.

Cross training new technical skills for people with the right aptitude is much easier than trying to instill soft skills and political smarts. So, look for people doing well in their own area and talk to them about promotion opportunities into your own groups. Provide training and mentoring and make use of their existing corporate knowledge and connections.

**4\. Linking advancement and succession processes** - The idea here is that promotions and bonuses are linked to succession planning progress. That way we incentivize it and get it to happen as part of people's goals and natural progression. Of course a counter, cynical view point could be that we have just made it everyone's problem, and now the onus for succession planning moves from HR to everybody else. However, it kind of is everyone's responsibility. If you are the sole owner of knowledge, you represent a risk as well as an asset to an organization and we should be managing that risk.

From an agile perspective we can put a slight spin on this recommendation and make succession processes part of our Definition-of-Done. For instance we can decide a user story or feature may not be "Done" for claiming credit until it has been documented in the project wiki - sharing knowledge about it and reducing turnover risk. A release may not be declared complete and "Done" until the production support group have been trained in its support and maybe even supported it in production for a month. If what we are trying to do is incentivize knowledge sharing then there are lots of options for us to achieve this.

**5\. Stimulating adoption and analytics use among business leaders** - This recommendation builds on the idea that: If we can measure it and discuss it then we maintain visibility and consideration into this important goal. Fortunately agile has many great tools for making invisible work visible. Kanban is largely about visualizing often non-visual work items and making processes policies explicit (bringing attention to improvements we want to make).

On agile projects we can create story and task cards for knowledge sharing and other succession planning activities. Information radiators and a culture of transparency provide visibility into work queues, progress, issues and impediments. Short iterations then give us frequent checkpoints to review the effectiveness of these metrics and new approaches.

All in all agile projects are great vehicles for testing analytics. With some creativity succession work can be blended in with regular development work and reviewed, discussed and improved in shortened timeframes than slower moving traditional projects. Geneticists study Mayflies because their reproductive cycle is so short you can run many experiments and get the results in a small timeframe. Agile iterations are the organization equivalent of a Mayfly, you get your results back quickly from change tolerant groups.

**6\. Being a preferred employer** - This piece of advice is probably the most effective but also the most difficult to implement. If you have a great work place that is better and more appealing than your competition then you will have less talent management problems. The trouble is that, by definition, only a small percentage of companies can be truly exceptional (otherwise they would be normal, not the exception) and 49% of companies will always be below average.

Nearly everyone would love to work for a humanitarian organization in an Apple like campus with Google like perks and flexibility. The trouble is most companies are more like "Bill's Toxic Plumbing" and have to compete fiercely on price with "Ted's Septic Services". We have limited ability to offer lavish benefits and the overall calling might, at first glance, be not very appealing.

So, we have to work with what we are given. Daniel Pink's book "_Drive: The Surprising Truth About What Motivates Us_" explains that the IF-THEN, carrot-and-stick extrinsic motivation that he describes as Motivation 2.0 is flawed and needs an upgrade. Hence the need and rise of Motivation 3.0 based on the intrinsic concepts of:

    1. Autonomy

    2. Mastery

    3. Purpose.

**1\. Autonomy** means giving people control over how they work, specifically:

**Task** - the work they do and how they undertake it

**Time** - when they choose to work in the day, week, year

**Technique** - How they perform tasks and from where

**Team** - How they organize, interact and collaborate

**2\. Mastery **describes the pleasure we get from doing what we love and following our passion. This can be seen when someone is so absorbed in a task that they are in the zone, or what Pink calls finding their flow. "Flow" is a great term to describe the state of mind when time seems to disappear and we are just immersed in the task. This feeling of flow can be difficult to find when our work environment puts obstacle after obstacle in front of us, whether it is admin and rules that limit our time in the role that we love, or restrictive work processes that impinge too much to allow us to get into this flow.

Mastery comes from:

**Flow** - having the time, space and freedom to find and exercise your passion for a profession.

**Goldilocks Tasks** - Not too difficult and not too easy, but just right. We need enough Goldilocks tasks to stretch, engage and indulge our desire for completion and satisfaction.

**Mindset of learning** - people who believe intelligence and knowledge is not a fixed capacity we are endowed with, but rather a muscle or skill we can grow. People who are happy to face their limitations and continually find new learning opportunities achieve mastery easier.

**3\. Purpose** describes tapping into people's belief that there should be more to work than just making money and being successful. Instead aligning company goals with individual's aspirations for doing good and meeting a higher guiding principle.

This is why companies like TOMS Shoes were created that give away a pair of shoes to poor countries for every pair sold. Buyers feel good since their purchase has a charitable impact and the workers at TOMS feel good since they are doing more than just generating shareholder value. Instead they are tapping into their motivation 3.0 principle of a compelling Purpose.

**Motivation 3.0 for Agile Teams**

The good news is that agile teams are half way there. The stepping stone to autonomy that empowered teams have is a huge leg-up on those people caught in command-and-control hierarchies.

Agile teams already have good autonomy over task, technique, and some aspects of team. Time, the remaining component of autonomy is seeing some progress too. Kanban approaches that are being adopted by agile teams have a more pragmatic view to iteration structures and scheduled meetings. If these time structures add value, then fine go ahead and use them, if they do not, then try without them; using more of pull model of task selection and work scheduling. Not only does this remove delays and eliminate waste, but it also affords the team more autonomy over their time.

Some agile organizations go further and allow 20% time (or 10% time) for pursuing new ideas and experiencing the joy of flow, being in the groove doing work you love. These one day a week (or half day a week) opportunities for self-directed work provide more Autonomy, an opportunity to experience work Mastery, and pursue a goal with a Purpose, perhaps for a good cause.

Regardless of your organization, all project managers can tap into the more sustaining benefits of motivation 3.0 even if you do not have the influence to change the company focus. Try to give more autonomy over task, time, team and technique by insulating people from petty office rules and unproductive admin, this will give them a little more freedom (to be more effective). Promote mastery by showing enthusiasm for the craft, for software teams this could include: encouraging code reviews, new tool evaluations, technology spikes, and local events like code-challenges, conferences and presentations.

**Conclusion**

Talent management is really important. Losing people is hugely expensive, disruptive and demotivating. From an optimizing business value perspective, project managers should be spending much more of their time and effort working on retention, training and promotion of team members. However it is hard to visualize, quantify and report on so it gets less attention. Plus, to many people, it represents the gooey "soft skills" stuff about people that is always tricky and unpredictable.

Increasingly the term "soft-skills" is being replaced with "Leadership". "Soft skills" got a bad reputation for being somehow secondary, or less important than technical skills. Hopefully, this article has demonstrated that retention and motivation are more significant to a company's bottom line than having a better widget efficiency. Leadership encompasses both production and retaining production capability, we need to focus on both to be successful.

[I wrote this article first for ProjectManagement.com [here](http://www.projectmanagement.com/articles/304160/Agile-Talent-Management--Part-1-)]
