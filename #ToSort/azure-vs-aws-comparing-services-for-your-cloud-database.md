# Azure vs. AWS: Comparing Services for Your Cloud Database

_Captured: 2017-03-28 at 20:48 from [dzone.com](https://dzone.com/articles/azure-vs-aws-which-service-is-right-for-your-cloud?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

[MongoDB Atlas is a database as a service that makes it easy to deploy, manage, and scale MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). So you can focus on innovation, not operations. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad).

The public cloud is making a huge impact on the way enterprises host, manage, and scale their database operations.

They've been freed from the scalability constraints of their on-premise systems. They can provision new infrastructure at the click of a button, without a lengthy hardware procurement process. They no longer need large, upfront capital investments to launch new IT projects. And they're taking advantage of new, cloud-oriented technologies when storing and analyzing their data.

Through a range of Database as a Service (DBaaS) options, public cloud vendors now make it easier than ever for organizations to migrate and maintain their databases.

But while these solutions address many of the headaches involved in database management such as migration, provisioning, and administration, there are significant differences between the various DBaaS offerings on the market.

In this post, we explore the core DBaaS solutions provided by the two leading cloud platforms, AWS and Microsoft Azure, and compare key features such as the types of databases on offer, the underlying infrastructure, and the querying capabilities.

So, let's get to it.

## Relational DBaaS

Amazon's dedicated DBaaS for relational databases is **Relational Database Service (RDS) **while **SQL Database** is Microsoft's equivalent service. As you would expect from two mature cloud vendors, both solutions offer **automatic replication** and are highly durable and available. What's more, both services provide **automated backups**.

### Database Engines

RDS supports six database engines, **Amazon Aurora**, **PostgreSQL**, **MySQL**, **MariaDB**, **Oracle,** and **Microsoft SQL Server **whereas SQL Database is a service exclusively based on Microsoft SQL Server.

PostgreSQL, MySQL, MariaDB, Oracle, and Microsoft SQL Server are hosted by AWS on **Elastic Block Store (EBS) **volumes. As Amazon's own proprietary database engine, Aurora uses a different storage infrastructure and is designed to address some of the scaling and replication issues associated with traditional databases.

### Resource Allocation

RDS works on the same lines as EC2, using the concept of instances to allocate compute resources to your databases. You then provision storage capacity separately. However, in the case of Aurora, storage scales automatically and you only pay for what you actually consume.

By contrast, SQL Database works on a [tier system](https://docs.microsoft.com/en-gb/azure/sql-database/sql-database-service-tiers#service-tiers-for-elastic-database-pools) in which each tier is suited to different types of workloads ranging from small-scale development/testing environments to high-transactional, mission-critical applications. Each tier is broken down further into different performance levels ranked by Microsoft's own unit of measure for resource capability known as the [Database Transaction Unit (DTU)](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-what-is-a-dtu).

In addition to its Single Database [pricing model](https://azure.microsoft.com/en-gb/pricing/details/sql-database/), Microsoft recently introduced **Elastic Pools**, which provides a collective resource for database hosting. This helps users to address fluctuations in load by spreading resources across several databases, thereby maximizing utilization and reducing costs.

### Scaling

You can vertically scale an RDS or SQL Database deployment via either the vendor's console or a simple API call. In the case of SQL Database, you can also scale up using a **T-SQL** ALTER DATABASE statement.

AWS charges storage separately from compute. Standard RDS provides up to a maximum of 6TB of storage. However, it has no automatic resizing capability. Aurora, on the other hand, is more flexible and scales automatically in 10GB increments up to a maximum of 64TB of storage.

With SQL Database, storage is included in the price of your selected tier and performance level. The service permits a maximum database size of 1TB and up to 2.9TB total storage per elastic pool. However, individual limits apply within each tier.

RDS supports **read-only horizontal scaling**, by which you're able to add replicas to improve query performance. By contrast, Microsoft Azure advocates a sharding approach using its [Elastic Database tools](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-scale-introduction).

### Other Features

Both RDS and SQL Database provide **point-in-time backups**, which you can use to return a database to an earlier state.

Many RDS DB instance types include **Provisioned IOPS (PIOS)** -- a feature designed to improve I/O between your database instance and storage. RDS can also be launched in[ Amazon Virtual Private Cloud (VPC)](https://aws.amazon.com/vpc/) whereas Database SQL doesn't yet support a virtual private network (VPN).

One of Microsoft's notable SQL Database features is support for the hybrid cloud service[ Stretch Database](https://msdn.microsoft.com/en-gb/library/dn935011.aspx), which migrates cold data from your on-premise SQL Server. However, it still allows you to query your data stretched to Azure while streamlining your on-premise database at the same time.

## NoSQL DBaaS

**DynamoDB** is currently Amazon's only NoSQL DBaaS designed for storing data at scale whereas Microsoft offers two distinct products, **DocumentDB** and **Table Storage**.

### Database Models

DynamoDB and DocumentDB are based on the **document store** database model. They are similar in nature to open-source solutions [MongoDB](https://www.mongodb.com/) and [CouchDB](http://couchdb.apache.org/) and are built to accept JSON structures.

Table Storage, on the other hand, is a **key-value store**, and works on the same principle as [Redis](https://redis.io/) and [Couchbase](https://www.couchbase.com/). In other words, it uses a database model that's fundamentally very similar to DynamoDB and DocumentDB but without any constraints on document structure. It is therefore used for storing data rather than querying or processing it.

Table Storage also enforces strong data consistency. This ensures that the latest version of your data is always returned, which is essential in systems where concurrent users simultaneously access and update the same information.

With DynamoDB, you specify whether you want eventually consistent or strongly consistent reads. DocumentDB gives you [four options](https://docs.microsoft.com/en-gb/azure/documentdb/documentdb-consistency-levels): strong consistency, eventual consistency and two intermediate levels that offer an alternative consistency compromise.

### Scaling

Both DynamoDB and DocumentDB are virtually infinitely scalable. Table Storage is limited to a maximum of 500TB per account, although you can extend your capacity by partitioning your data objects across accounts.

Table Storage is the only DBaaS with native auto-scaling capability. However, a number of third-party solutions are available that can monitor and scale DynamoDB and DocumentDB automatically.

### Query Support

DocumentDB is the only one of the three DBaaS offerings that comes with full-blown SQL functionality. However, you can integrate DynamoDB with **Elasticsearch** using the DynamoDB [Logstash plugin](https://github.com/awslabs/logstash-input-dynamodb) to enable free-text search of content such as messages, tags, and keywords.

Amazon also provides another NoSQL service, [SimpleDB](https://aws.amazon.com/simpledb/), which works along a similar line to Table Storage. However, databases are limited to 10GB in size, making the service unsuitable for Big Data use cases.

## Data Warehouses

**Redshift** and **SQL Data Warehouse** are Amazon and Microsoft's data warehousing solutions, respectively. Although they're both SQL-oriented, they also leverage Big Data technologies such as **column-based storage**, **data compression,** and **massively parallel processing (MPP)** to enable fast query performance at scale.

### Resource Allocation

With Amazon Redshift, you configure your resources as a cluster of database instance types or nodes. You have a choice of four different node types -- two **Dense Compute** instances with directly attached SSD storage and two **Dense Storage** with directly attached HDD. According to your cost, performance, and storage requirements, you can fine-tune your infrastructure by choosing a suitable balance between instance type and number of nodes.

SQL Data Warehouse works slightly differently as it decouples compute from storage altogether. Compute resources are organized into a series of power levels that are ranked by Microsoft's own unit of measure for resource allocation known as [Database Transaction Units (DTUs)](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-what-is-a-dtu). Storage is charged in blocks of 1TB and grows automatically with your data.

### Scaling

In terms of scaling, SQL Data Warehouse is slightly more flexible than Redshift as you can adjust compute power and storage independently of one another. It also provides you with an option to pause compute, giving you even more scope to optimize your cloud costs. On the other hand, Redshift gives you more control over your underlying infrastructure through its choice of instances that each has different CPU, memory, and storage profiles.

### Query Support

Both data warehouses support full-blown SQL statements. However, as they use columnar storage, neither service is particularly well adapted to using the transactional INSERT, UPDATE, and DELETE commands. SQL Data Warehouse uses T-SQL, Microsoft's extended version of SQL, although Redshift is also a proprietary analytics engine offering slightly different query functionality.

### Built-In Features

One of the key built-in features of SQL Data Warehouse is [Polybase](https://msdn.microsoft.com/en-us/library/mt143171.aspx) -- a technology that bridges the gap between relational and non-relational data, seamlessly allowing you to manipulate and perform T-SQL queries stored externally in **Hadoop** or Azure **Blob Storage**. This could prove particularly useful to T-SQL analysts, who will be able to access unstructured and semi-structured data hosted on these frameworks without having to learn new Big Data tools.

Both Redshift and SQL Data Warehouse automatically replicate your data, providing built-in fault tolerance and high availability. What's more, backups are included at no extra charge -- up to a limit of 100% of your provisioned storage on Redshift or seven days of incremental snapshot storage on SQL Data Warehouse.

## The Bigger Picture

When researching your DBaaS options, you will need to dig deeper and consider the technical aspects of each service. For example, you should think about how to implement security and compliance, what programming languages each DBaaS supports, and how well each service is adapted to your application architecture.

Not only that, but you should also look at the wider picture, such as each vendor's approach to service delivery.

For example, AWS puts a strong emphasis on self-service, which tends to suit customers born in the Digital Age. By contrast, Microsoft is traditionally more hands-on, providing product support and guidance through its network of sales representatives.

Other factors -- such as Amazon's large ecosystem of third-party software providers and managed service partners or Microsoft's strong hybrid cloud capabilities -- could also play a pivotal role in the decision-making process.

Ultimately, the best way to choose your cloud DBaaS is to try out each service for yourself. Consider each offering in terms of ease of use and future development potential, making real-life projections of performance and cost. That's where monitoring your trial deployments can reveal insights that could help you make the right hosting decision.

MongoDB Atlas is [the best way to run MongoDB on AWS](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad) -- highly secure by default, highly available, and fully elastic. [Get started free](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). Brought to you in partnership with [MongoDB.](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad)
