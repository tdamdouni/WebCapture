# Best Practices of DevOps for Effective Project Delivery

_Captured: 2018-01-30 at 21:02 from [dzone.com](https://dzone.com/articles/best-practices-of-devops-for-effective-project-del?edition=358105&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-30)_

In response to accelerated release cycles, a new set of testing capabilities is now required to deliver quality at speed. This is why there is a shake-up in the testing tools landscape--and a new leader has emerged in the just released [Gartner Magic Quadrant for Software Test Automation](https://dzone.com/go?i=265440&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Post_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ).

This article shares some of the interesting DevOps principles and the advantages in applying them for effective project delivery and turnaround. The concepts mentioned are based on the teachings of John Willis who is a veteran in IT management and a leader of the DevOps movement from the beginning. The related terminology and practices should be definitely useful and can be considered in organizations when thinking about practicing DevOps. This article talks about the following:

  * Knight Capital Story

  * DevOps Terminology

  * Value Stream/Lead/Cycle Time

  * High and Low Performing organizations

  * Learnings from Lean Model

  * Continuous Delivery Model

  * Practicing DevOps

## Knight Capital Story

Before we proceed into DevOps best practices, we will have a look at how the IT process and technology failure can lead to problems and losses in business. We will see the Knight Capital failure that happened in 2012 to understand more about this.

The **Knight Capital Group** was an American global financial services firm engaging in market making, electronic execution, and institutional sales and trading. On August 1, 2012, Knight Capital deployed untested software to a production environment which contained an obsolete function. The incident happened due to a technician forgetting to copy the new Retail Liquidity Program (RLP) code to one of the eight SMARS computer servers, which was Knight's automated routing system for equity orders.

When released into production, this resulted in 4 million executions in 154 stocks for more than 397 million shares in approximately 45 minutes, causing a loss of $440 million. The nature of the Knight Capital's unusual trading activity was described as a "technology breakdown."This shows the level of seriousness that can be caused by deploying software with a bug in production.

This incident could have been avoided if they had followed DevOps principles and reduced waste at all levels. Waste here means that they might have used a manual deployment which caused the human error and this should have been replaced by automated deployment. We'll see the various DevOps practices going forward.

## DevOps Terminology

"DevOps is a cultural and professional movement" [as defined by Adam Jacob](https://readwrite.com/2015/07/29/devops-people-not-technology/), the founder of Chef.

The three factors that influence a project are speed (time), reliability, and cost. Development requires speed to deliver on time and operations needs reliability. With DevOps, it is possible to achieve speed and reliability by keeping the cost low.

It is all about patterns, continual improvement, organization's culture, learning curve, continuous delivery, continuous learning, continuous collaboration, and automation.

Some terminology related to DevOps:

  * **Value Stream **- It refers to the sequence of activities that an organization undertakes to deliver for a customer request. How you get from an idea to something that makes money.

  * **Lead Time** \- The time it takes one piece to move all the way through a process of the value stream from start to finish. In general, the Lead Time is the time taken in the eyes of the customer.

  * **Cycle time **starts when the work begins on the request and ends when the item is ready for delivery.

  * The better we are at **Lead Time** means the better we are at DevOps.

  * The **Deployment Lead Time** is, how good we are at our automation.

Organizations should consider the following DevOps patterns and practices appropriately to reduce the lead time. They can follow one or more DevOps approaches such as amplifying feedback or enhance the culture of continuous learning. More information about these approaches is given in the latter section of the article.

## High Performing and Low Performing Organizations

There is a study on organizations where they are classified as high and low performing organizations, as covered in the [State of DevOps Report 2016](https://puppet.com/resources/whitepaper/2016-state-of-devops-report). As per this study, it is a fact that high performing organizations are closely following DevOps culture and low performing organizations are not. The below DevOps culture and practices have been observed to be followed in High Performing Organizations:

  * Higher Employee Engagement
  * Building Quality In
  * Follow Lean Product Management Principles 
    * Gathering, broadcasting and implementing customer feedback
    * Splitting work into small batches and making visible the flow of work through the delivery process
  * Spend the least amount of time on unplanned work and rework

As a result of following the above practices and culture, they have:

  * Higher Deployment Frequency
  * Less Lead Time for Changes
  * Less Mean Time To Recover(MTTR)
  * Less Change Failure Rate

Here are some more details about these high-performing organizations:

  * Examples: Amazon, Google, Facebook, Etsy, Netflix
  * In 2015, Google has stated that they did about 5,000 code commits a day, 75 million test cases per day; Amazon, 136 thousand code deploys per day, 15 million per year; Netflix, 500 code deploys per day; Etsy, hundreds plus. Refer to the [2015 State of DevOps Report](https://puppet.com/resources/whitepaper/2015-state-devops-report). 
  * Compared to low-performing organizations, they deploy 200 times more frequently, with 2,555 times faster lead times, recover 24 times faster, and have three times lower change failure rates.
  * They tend to have high cooperation, get trained, the risks are shared, the bridging is encouraged, have a healthy attitude towards failure, inquisitive

Low-performing organizations:

  * Organizations that struggle to deploy maybe more than twice a year and have kind of a waterfall deployment model.
  * They are slower and less reliable, have low cooperation, messengers are shot, bridging discouraged, have negative attitudes towards failure, try to avoid failure at all costs and novelty is crushed.

## Learnings From the Lean Model

Some of the terms related to Lean Model are Waste, Flow, and Stress.

  * **Waste:** Learning from Lean is to eliminate waste wherever possible. Waste denotes unnecessary steps that are not helping to achieve the Lead Time. To follow DevOps, we try to do several things like automating wherever possible. 

  * **Flow**: Flow is about evenness in the pipeline that is used for developing a finished product. It has to be consistent and global optimization always wins over local optimization.

  * **Stress:** When we reduce waste and handle the pipeline flow in an even fashion, then we reduce stress on the system. It's a kind of systems thinking where we look at the global performance of the flow. This should allow the end product to flow quicker in the pipeline. 

  * **Kaizen:** It is a Japanese term for continuous improvement. The Toyota Production System, in their greatest form, was able to optimize even this flow and eliminate waste and reduce stress on the system through continuous improvement.

  * **Kata:** Practicing kata allowed a company of persons to engage in a struggle using systematic approaches. By practicing in a repetitive manner the learner develops the ability to execute those techniques and movements in a natural, reflex-like manner.

Influence of Lean Model in DevOps is to eliminate Waste wherever possible so that the Flow is improved and evenness is achieved. Also, Stress has to be reduced so that the end product flows quicker in the pipeline. We need to follow Kaizen for continuous improvement and should have the ability to execute the techniques in a natural reflex-like manner as denoted by Kata.

## Continuous Delivery Model

An important piece of DevOps is the **Continuous Delivery Model**, also referred to as CI/CD - Continuous Integration/Continuous Delivery. The basic principle here is to build the quality in. This is to build a software pipeline with a full test coverage. High-performing organizations take testing very seriously. They take it seriously in the kind of functional code, the integration test, the smoke test all the way through the process, until even how they deliver the software.

## Practicing DevOps

At a high level, there are three ways to implement DevOps, out of which any one or more approach(es) can be suitable:

  * First Way - Shorten Lead Time
  * Second Way - Amplify Feedback
  * Third Way - Continuous Learning

The** First Way** is left to right. On the high level, what we're trying to do is shorten the Lead Time, the overall time it takes us to get from an idea to a delivery, to a customer. Approaches in this way are:

  * Make work visible, e.g. Kanban board

  * Work in small batches

  * Automate repeatable tasks

  * Apply lean software principles - eliminate waste, reduce bottlenecks

  * Set work-in-progress limits

The** Second Way** is kind of the right to left, or Amplified Feedback. We apply monitoring using many tools. This, in general, deals with accelerates our ability to get feedback, and be able to find defects or waste earlier in the flow. Some of the methods are

  * Telemetry

  * Fault injection

  * Peer Reviews - all changes are peer reviewed

  * Everyone monitors the commit logs

The** Third Way** is kind of the full circle; the First Way is left to right, the Second Way is the right to left, and the Third Way as kind of the continuous circle; it's Continuous Learning. It's where we apply things like Kaizen or Kata.

  * Dimensions of learning organizations using this approach:

  * Continuous Learning

  * Communication Feedback

  * Feedback should be goal oriented

  * Goals should be for learning improvement and Trust

  * Feedback should not be personal, should be about behavior and must be actionable

  * Feedback methods - porpoise feedback used in Low Trust environment, the sandwich feedback(medium Trust environments), and the Atkins feedback(High Trust environments)

  * Blameless Culture

## Conclusion

From the Knight Capital story, we have seen how serious damage software issues can cause. As per the State of DevOps Report, following the DevOps culture and practices is beneficial to the organizations and they improve the ROI with respect to Savings and Value:

  * Savings - includes the cost of downtime and the cost of excess rework.
  * Value - includes the potential revenue and customers gained from releasing more quickly.

We hope the analysis and guidance in this article will help you better understand the potential of implementing DevOps in your organization.

Recently published [Gartner Magic Quadrant Report for Software Test Automation ](https://dzone.com/go?i=265436&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ)provides an objective benchmark of all test automation solutions based on industry surveys, customer inquiries, product evaluations, and more.
