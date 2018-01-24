# 4 Reasons Why DevOps Ignores Data Professionals

_Captured: 2017-11-17 at 21:33 from [dzone.com](https://dzone.com/articles/4-reasons-why-devops-ignores-data-professionals?edition=334926&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-11-17)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

Avoid the data group at your peril. Too often we have seen DevOps being adopted at companies without engaging with the data group. Those efforts will fail to deliver the benefits initially sought by DevOps.

Simply put, a pack can only move as fast as its slowest member. If you look at how wolves travel, you'll notice that the slowest members are at the front, the fastest, strongest at the back

But, time and time again we see DevOps teams completely ignore data professionals. From tool evaluation, to process improvement, those calling for DevOps adoption routinely ignore data professionals and fail to embrace them. The irony is not lost on us as we see a movement built around inclusiveness ignoring a key component to a companies' success. Here are the 4 reasons why DevOps ignores data professionals.

## #1 - It's Easy to Ignore Them

Most companies are able to deploy database changes to their dev and test databases. There was a time when that responsibility was owned by the Data Group. But, with the adopting of Agile, companies have ceded that responsibility of deploying database changes to the development and test team. Thus, dev and test have no need to interact with the Data Group. This has led to the Data Group being completely cut out of data architectural decisions as they must simply accept the changes as requested by the development team. If the Data Group does make issue of bad database schema changes ("What! Is that an index with eight columns?!?!?"), the release teams use deadline pressure to force the Data Group to make the change anyway. Therefore, there is no need to do anything but ignore the Data Group. The similarity to Douglas Adams "Somebody Else's Problem Field" is uncanny.

## #2 - Data Is Hard

The concept of state is very difficult for development teams to deal with. One of the 12 factors for applications is stateless applications. Thus, to introduce the idea of handling state for the persistence layer is often dismissed out of hand. As described before, it's somebody else's problem so why even bother addressing it. If somebody else is responsible and the problem is hard, there is no reason to address it. After all, "that's an operations problem".

## #3 - Data Professionals Have Different Goals Than Other Team Members

The Application Development Group is incented to change things. The Operations Group is incented to maintain stability. Change is the enemy of stability. Thus, we have adopted DevOps to mitigate the conflict and find a way to have both teams reach their goals. [The Data Group has slightly different goals](http://www.datical.com/whitepapers/the-dbas-role-in-devops/). They too seek stability, but the integrity and security of the data is also paramount. Remember that the most valuable asset a company has in the tech stack is the data. Look at photo sharing apps as an example: it doesn't matter that you can put dog ears on your photos if the app continues to forget who you are connected too and you can't share the photo. Features are important, but only if the data is there to support the features. Of course, the people that create those features might argue against that. Thus, we have a difference in values that leads to avoidance.

### #4 - Data Professionals say "No" too often.

Finally, Data Professionals do have well-deserved reputation as Dr. No. In the past, DBAs have been guilty of using data as a Billy club to get their way. As a result, they have taken all responsibility for production database changes. This includes all of the glory and all of the headaches; today it is all headaches, pain, and hand wringing. Because of their long history of mandating they be the final arbiters of production database deployments, and often being dissatisfied with development created schema and logic changes, they have caused the rest of the company to voice their frustration with a terse, "Fine. Do it yourself then."

Because of such a long time of demanding to be the single point through which all change flows, the Data Group has not only caused their work load to increase with the level of application releases (exponentially!), now that they are suffering with high demands, the rest of the wolf pack is not very eager to help.

### We Can Fix This

These challenges are not insurmountable. We can resolve these issues by addressing the root cause: the data group is not a part of our New Development teams. We have cross functional teams in development now; no longer do we have separate UX and Business Logic teams. As such, we need to embrace distributed data management and move some of our Data Professionals into these Development Groups.

Of course, we still need our Data Professionals that understand the challenges of storage, performance, high availability for databases. But, a large percentage of our Data Professionals need to look at their peers in Systems Administration and mirror their career paths by adopting Infrastructure as Code.

By adopting this new approach with teaming and distribution of responsibilities, we can move our pack faster to the end goal which is faster software releases and delighted customers.

To learn more about the role of Data Professionals in DevOps read this white paper, [The DBAs Role in DevOps](http://www.datical.com/whitepapers/the-dbas-role-in-devops/).

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**

Opinions expressed by DZone contributors are their own.
