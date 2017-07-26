# SQL Clone: Ending Provisioning Headaches

_Captured: 2017-03-12 at 19:54 from [dzone.com](https://dzone.com/articles/sql-clone-ending-provisioning-headaches?oid=twitter&utm_content=buffer64189&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Whether you work in SQL Server Management Studio or Visual Studio, Redgate tools integrate with your existing infrastructure, [enabling you to align DevOps for your applications with DevOps for your SQL Server databases.](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667) Discover true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667).

![Dedicated database development 1](https://www.red-gate.com/wp-content/uploads/2017/02/clone-sheep-5cm-225x300.png)

When developing a database as a team, most team members would generally prefer to work with their own, isolated copy of the database, rather than work on a shared development database.

Up to now, however, there have been a number of additional management and security problems with the dedicated database approach and these burdens only increase as the size of the database grows, and as regulations around data security and sharing grow. As a result, many organizations still tend to favor the shared model, despite its drawbacks.

[SQL Clone](http://www.red-gate.com/products/dba/sql-clone/) can help reduce the pain associated with many of the provisioning tasks that go with database development, regardless of what development model you use. For teams who use a shared development database out of necessity rather than choice, I believe SQL Clone can remove enough of the additional problems to make the dedicated model viable for the first time.

## Why Is the Shared Development Database Model Still Prevalent?

Whichever model you use when developing a database, you are always going to have to overcome database provisioning problems. Even in the shared model, you'll still need to manage a few 'sandboxes', where developers can try out new ideas. Both development models require test databases. Both models require provisioning and management of databases in UAT/QA/Staging environments.

Over the years, I've heard and read some impassioned arguments in favor of dedicated development databases. [Troy Hunt's article](https://www.simple-talk.com/sql/sql-tools/the-unnecessary-evil-of-the-shared-development-database/) is a great example. Central to his theme is the idea that on a dedicated database, each developer can do whatever is needed to accomplish an assigned task, without fear of conflicting with the work of others. They have the freedom to experiment without having to worry about causing unpredictable data states, disrupting integration tests, and so on.

A dedicated development database simplifies the task of diagnosing a sudden change in behavior or performance by removing the possibility that someone else's modification caused the issue. In short, dedicated database development makes developers more productive.

These arguments are still valid, and yet in my experience, for databases of any size or significance, I've found the shared database development model to be more prevalent. Why?

For many companies, the question is not _Why?_, but rather _Why not?_ The shared model uses less disk space and requires less DBA time to manage (at least, in theory). Security concerns compel companies to keep data in locations where it is under IT control. And if the workload and databases schemas and permissions are managed properly, the changes of different developers don't often conflict with each other.

The risk of changing a development practice that isn't broken, in favor of one that will likely have a higher administrative overhead, is not outweighed by the intangible reward of increased productivity.

![dedicated-database-development-quote](http://www.red-gate.com/wp-content/uploads/2017/03/dedicated-database-development-quote.png)

Of course, the benefits of the shared development database come at a cost. Since multiple developer schedules are involved, opportunities for refreshing that shared development database are dramatically reduced. Often, this means planning an outage on that database to allow time for the refresh.

When the time does finally come to provision the new copy of the database, work must be stopped while the provisioning is occurring - for large databases, the time required can be hours or even days. Far too often, this means that the refresh is avoided in favor of keeping the normal flow of work moving. Developers must adapt to using stale data for their testing, while companies settle for results that are 'good enough'. The cost to change that state has traditionally been high enough to put it out of reach for many companies that may otherwise desire to improve.

SQL Clone is a tool that aims solely to reduce the pain of database provisioning. I believe it can remove enough of the burden that teams can simply choose whichever development model suits them best, rather than being constrained for logistical reasons.

## So How Does SQL Clone Help?

SQL Clone allows you to get the best of both worlds by providing as many updateable copies of a database image as you wish, either on one server or on several servers within the same network. Each clone shares the data from the original image, and merely stores locally any subsequent differences to that image that are caused by changes to the data or metadata.

SQL Clone does this by using Windows own VM technology. SQL Server is entirely unaware of any difference in the cloned image and any other database. It is used entirely unchanged, because SQL Clone works at the operating system level. The effect is that the database is stored only once, and the clones store only the subsequent changes.

If additional data security is required, data masking or loading of development data can be completed before the image is created. Development work can then proceed without any concern that user data or confidential data can be compromised.

Even with SQL Clone, you'll still require a slick management process to be able to keep things under control when provisioning, and regularly refreshing multiple development, test, and other environments. Fortunately, in addition to a streamlined web interface that is accessible to both administrators and developers, SQL Clone comes with a library of PowerShell cmdlets, allowing full control of the process within a script.

## Provisioning Copies of Large Databases

As the size of databases has increased, the difficulty of transferring those databases between servers has also increased. Large production databases can take hours, or longer, to restore. Finding space for multiple copies of these large databases is also a challenge in the face of ever-increasing demands for storage space from all sides.

SQL Clone solves this problem by significantly reducing the amount of space required to store multiple copies of these large databases. Instead of requiring the full amount of space on the database server each time a copy is provisioned, the image is only stored once, in a central location. Each clone is then created with a small differencing disk on the database server, starting with less than 50MB of space. Even though the clone will grow as changes are made to the schema or data, the space required is generally a fraction of the amount that would have been required for a full copy of the database.

## Provisioning Multiple Development Environments

Sometimes, database provisioning simply means restoring the latest backup of the production database to the target server, though it's rarely as simple as that sounds. For many databases, there are usually a number of additional steps to perform any time a fresh database copy is deployed, such as basic data cleansing, or removing production logins, and then recreating logins for that target environment and mapping them to existing users and roles.

![dedicated-database-development-quote-2](http://www.red-gate.com/wp-content/uploads/2017/03/dedicated-database-development-quote-2.png)

For large databases containing sensitive data, the problems are challenging. It can be hard to keep up with the regular demand for fresh data, as well as the various ad-hoc requests from developers who need to return to a stable state after a failed experiment, or need to replicate a production issue from last night that didn't exist the night before.

With SQL Clone, you can create an initial 'clean' data image (see later), and from that image create as many clones as required, in seconds. All local changes made to a particular developer's clone are isolated, stored in a local differencing file, and simply committed to source control in the usual manner. The space required on each machine is just the space required to store any local changes.

It means, in effect, that each developer can work with their own copy of the production database. If they need to create a branch, they can quickly create a new clone to support development on that branch. Likewise, if they need to reset their environment, or refresh it with a clone of the latest data image, it becomes a matter of seconds rather than hours or days.

Clones can be created and destroyed at will to meet the specific situation, and because the changes made by the developer are not transferred back to the image, there is no chance that an experimental change will affect either production or other developers.

## Provisioning for Database Testing

For companies adopting a fully automated DevOps workflow, provisioning provides a unique challenge. Ideally, a fresh copy of the database would be created for each run of the build process so that unit tests and integration tests could judge accurately whether the changes made in that build had the intended effect, and whether the changes introduced any unwanted regressions.

This ideal has not been feasible in many cases, simply because large databases take too long to restore. This has left teams with the choice of finding ways to revert the changes in the previous test or living with an unclean copy of the database.

With SQL Clone, a clean copy of the database can be provisioned as part of the build process without creating unwanted delays, and because a clone only requires a small amount of disk space, clones can be created as often as necessary to run the desired tests.

It even becomes feasible to do parallel testing with real databases. Let's say you have a series of five tests, one for each for end-to-end testing of a specific business function, which if run serially, take 16 hours. What if you could spin up five separate clones and test each business process in parallel? It would dramatically reduce the time required for end-to-end testing.

The end result is faster test times, much more accurate testing, and higher quality code.

## Dealing With Sensitive Data

Most companies now have to comply with some sort of regulation regarding the privacy of the data they store, and in those cases, providing developers with realistic volumes of 'production-like' data for testing is a bigger problem.

SQL Clone can help make this process easier. In cases where there are no real data sensitivity issues, we can perform very basic data cleansing, such as replacing real email addresses that we don't want the application to use, by altering the data in the clone. This can easily be incorporated in an automated PowerShell script that produces the clones. Because a clone can also be imaged, we can still create a new data image to use for distribution.

For more stringent requirements, though, it's probably best to produce clean data before creating the data image. This means restoring the backup, sanitizing or obfuscating the production data to an extent that it complies with any relevant regulations regarding data sharing, then creating the data image from that database.

Alternatively, we can avoid production data altogether, by performing a new database build, from the latest version in source control, and then importing standard data sets for testing, and then creating the image.

## Streamlined Management

![technology-overview](https://www.red-gate.com/wp-content/uploads/2017/03/technology-overview-1.png)

With traditional methods, the task of provisioning databases, and keeping control of each environment, falls heavily on the shoulders of database administrators.

Creating a backup, restoring it to a different server, performing data cleansing, and adjusting the security for the development environment all take a significant amount of time when done manually. Automation is possible with existing tools, but it often requires complex scripts, which also take time to create and maintain. If a company is affected by strict regulations that prevent a DBA from seeing customer data, all of this must be performed under the watchful eyes of an auditor.

With SQL Clone, an image can be created using SQL Clone's built-in PowerShell cmdlets, which simplifies the scripting required. That script can be scheduled during off-hours using the company's standard scheduling tools. To satisfy regulators, the variant using non-production data can be created without intervention by a DBA by using additional scripts.

Clones can then be created from the resulting image, either automatically with PowerShell or on-demand from the SQL Clone web interface, by anyone with permissions, including developers. Automation that was previously difficult becomes feasible for anyone.

## Conclusion

SQL Clone might be a game-changer. Developers benefit from being able to work with realistic data and 'self-service' provisioning. Database administrators benefit from the reduced management overhead, leaving more time for tasks that add real value.

Companies benefit from improved developer productivity and the higher quality code that results from improved testing. And the best part is, all of these benefits are possible without giving up the benefits of the development model you're already using.

**_Get rid of your database provisioning headache with a 14-day fully functional [free trial](http://www.red-gate.com/dynamic/products/dba/sql-clone/download) of SQL Clone._**

It's easier than you think to [extend DevOps practices to SQL Server with Redgate tools](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673). Discover how to introduce true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673).
