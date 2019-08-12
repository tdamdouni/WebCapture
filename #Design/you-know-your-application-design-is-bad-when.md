# You Know Your Application Design Is Bad When ...

_Captured: 2018-08-31 at 07:01 from [dzone.com](https://dzone.com/articles/you-know-your-application-design-is-bad-when?edition=385438&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-08-30)_

###  Is your application design solid? You might want to read this article for some real-life examples that a Zone Leader has encountered. 

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Designing applications is a lot of fun.

I think you would agree or you would probably not be reading articles in the [Web Dev](https://dzone.com/web-development-programming-tutorials-tools-news/list) zone at DZone, right?

One of my favorite aspects of architecting and building systems is to be able to conquer the challenge before me and believe that my design leads to some positive benefits to the intended user community.

A big challenge we often face, especially as contract developers, is that we don't get to see the overall response from the application once it has been deployed to the masses. While we hope that we built everything in the best possible way, there are times when the delivered application design is bad.

This article will focus on three examples I have witnessed in my career in Information Technology (IT) where the end result was a bad application design.

## Repurposing the Salutation Field

As a part of the feature team for a Salesforce conversion, I spent time job-shadowing users of the prior CRM application. It was neat to watch them do their job and interact with their customers. In all, I participated in three sessions. The last one demonstrated something I wasn't expecting.

I didn't see it right away, but it was there the entire time.

The team member looked in his queue, opened a record and clicked a button on the screen which caused his telephone to make a call. During the call he noted the results of the conversation. Then, he did something the other two individuals I sat with did not do. He put "C1017" in the Salutation field on the screen.

Not "Mr." or "Mrs." or even "Dr." He put "C1017" in the field.

After he pressed the Save button on the form and disconnected the call, I asked him what "C1017" meant and why it was put in the Salutation field.

His response was, "C1017 means I need to call them back on October 17th. The C means to call and the rest is the date I need to call again."

He paused when the list of items in his queue refreshed. Then I noticed, each of the records in his queue had a set of codes in the Salutation field. He explained that there wasn't a way to see the current status from this view of their system. So, to avoid having to open each record, he used the Salutation field (which wasn't really used in the system) to store his own personal status codes.

He had other prefixes for his codes, giving him an easy way to see his accounts at a glance without having to wait for the very-slow system to process requests.

> You know your application design is bad when... end-users have to repurpose fields to do their daily jobs. 

## Don't Have Time

While in New York for a data analytics project, I was sitting with a team of users who were providing data that would be used by the project. As part of meeting with the project sponsor, he wanted me to sit with his teams to make sure we weren't missing some key metrics for the group's activities.

Like the prior example, I was sitting with the end-users of the application as they had dialogs with their customers.

This time, I noticed the team members were using those legal-sized yellow tablets of lined paper. Each call represented a new row on the page, where they would note information from the call with their customer.

After watching this process a for a few minutes, I asked the team member why she was writing information on the paper. Her response surprised me.

She answered, "The system is really slow, especially this time of the day. So, we have all gotten into the habit of writing down the items we need to update. Then we make the system updates before heading home - since the response time is much better." She continued to include that when they attempted to make the changes online, the call times were increased, which caused their customers to become less happy waiting for the system to respond.

Neither the project sponsor or the development lead for the project were aware of this activity. When we reviewed queries into that system, we noticed several clusters of update activity - which aligned with the end of shifts for the teams that I job shadowed.

> You know your application design is bad when... end-users have to write changes down on paper to avoid waiting for a slow system to respond. 

## Changing the Business Process

Working with a large real estate company, I was involved with the conversion of a leasing workflow application at the core of their business.

Spending time with the Product Owner, I noticed she had concerns with the project from the beginning. At first I thought it was due to the team involved in the project, thinking maybe because we were new to working with real estate fundamentals. While trying to gain a better understanding of the overall goal, the source of her concerns was ultimately revealed.

The leasing application was going to maintain several integration points from both the Leasing division and other financial systems within their organization. When she started showing me one of the other Leasing applications that was delivered about a year earlier - I started to understand her concerns.

In order to give me an example of how to integrate with this other system, she started noting items on her whiteboard. Once she finished, there was basically a cross-reference table of items that were actual business aspects and how they translated into the items required to use this system. In short, the last system that was delivered by the IT group required a change in the business process to use the application.

Her fear is that the new application I was working on would yield the same result. The impact would be several times worse, since her group only utilized the other application periodically. She later confessed that she initially preferred not to replace the existing application due to the fear that the new application would require additional efforts by her team - causing delays to meet the needs of their customers.

> You know your application design is bad when... end-users have to change their business process to meet the needs of the system. 

## Conclusion

In today's world of tightly monitored budgets and frugal corporate spending, there is typically an isolated timeframe to analyze, design, and deliver applications. Once delivered, the application development team will change their focus to the next scheduled project. Often times, the development team is no longer engaged when an application reaches full deployment to the user community. When external developers are involved, they are often no longer working with the corporation who employed them for the project.

Without obtaining feedback from aspects of the entire user community, situations like those noted above are likely to exist. In each case, there were significant losses to the business from what was a bad application design. While I wasn't involved in the design of these applications, my hope is that the development team did not have a goal to deliver a bad application design.

Instead, the application design became bad based upon:

  1. Incomplete knowledge of the needs of the customer.

  2. Inability to provide a scalable application.

  3. A change in business needs without an update to the underlying system.

Information Technology leaders should maintain a strong relationship with the consumers of their applications, soliciting feedback from those using their systems on a daily basis. While updates may not be considered "in budget" initially, the required updates could fund themselves in the amount of time that is saved from the end-user's perspective.

Have a really great day!

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
