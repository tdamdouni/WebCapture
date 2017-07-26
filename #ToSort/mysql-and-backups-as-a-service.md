# MySQL and Backups as a Service

_Captured: 2017-05-17 at 00:18 from [dzone.com](https://dzone.com/articles/mysql-and-backups-as-a-service?edition=298107&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-16)_

Whether you work in SQL Server Management Studio or Visual Studio, Redgate tools integrate with your existing infrastructure, [enabling you to align DevOps for your applications with DevOps for your SQL Server databases.](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667) Discover true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667).

With the recent announcement that MySQL is available as a Platform as a Service (PaaS) offering through Azure, a lot more exciting opportunities have presented themselves for companies to build and manage their information. According to the [DB-Engines Ranking](https://db-engines.com/en/ranking), MySQL is the second most popular data management system out there. At last, you get to incorporate it directly into your Azure ecosystem. While there are tons of reasons this is exciting, I'm going to focus on one very particular issue, backups.

## Why Are Backups Important?

I'm not going to answer that question. Everyone knows that backups are important. Everyone knows that they need to have backups. Yet… There is example after example where people either haven't bothered to set up backups or didn't know what a real backup entails, or even had backups, but never did any validation. I gathered a [few examples of failed backups](https://www.simple-talk.com/sql/backup-and-recovery/backups-what-are-they-good-for/) that literally destroyed companies in this article. Funny enough, a couple of them were running on MySQL. A backup is vital to the business. Even more important, a validated backup is vital to the business.

## Why Is MySQL Platform as a Service Important?

I am going to answer this question. There are a lot of advantages to creating, using and developing against data storage within a PaaS offering. One of the biggest for me is backups. Microsoft is automatically taking backups of the MySQL databases you create within Azure. These are real, full backups. Microsoft validates the backups. As I write this, you'll have the ability to restore your entire database, to any point in time, at intervals of five minutes, over a 35-day preceding period. By programming against a MySQL database within Azure, you are gaining the protection of the information you're storing within your database, and you don't have to do anything to benefit from this. It's all part of the service.

## MySQL Protection

Finally, with Microsoft's release of MySQL within Azure, you not only get a well-performing and maintained MySQL database, you get backups. Consequently, protection of your data, built into the service, at no added cost, is a vital part of what Microsoft delivers for us through MySQL on Azure.

Watch this space. As soon as I get the chance to more thoroughly test the self-service restore option I'll create another blog post detailing how it works. In case you didn't notice, they're hosting PostgreSQL as well, and it has backups in place.

It's easier than you think to [extend DevOps practices to SQL Server with Redgate tools](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673). Discover how to introduce true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673).
