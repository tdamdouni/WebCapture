# How to Handle Huge Database Tables

_Captured: 2017-06-09 at 03:13 from [dzone.com](https://dzone.com/articles/how-to-handle-huge-database-tables?edition=304143&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-07)_

Learn how to [move from MongoDB to Couchbase Server](https://dzone.com/go?i=206124&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454368%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283402) for consistent high performance in distributed environments at any scale.

Get a jump on query optimization in your databases by designing tables with speed in mind. This entails choosing the best data types for table fields, choosing the correct fields to index, and knowing when and how to split your tables. It also helps to be able to distinguish table partitioning from sharding.

It's a problem as old as databases themselves: large tables slow query performance. Out of this relatively straightforward problem has sprung an industry of indexing, tuning, and optimizing methodologies. The big question is, _which approach is best for your database system?_

For MySQL databases, in particular, query performance starts with the design of the table itself. Justin Ellingwood explains the basics of query optimization in MySQL and MariaDB in a Digital Ocean article from November 11, 2013, and updated on May 30, 2014.

For example, data elements that will be updated frequently should be in their own table to prevent the query cache from being dumped and rebuilt repeatedly. Generally speaking, the smaller the table, the faster the updates.

Similarly, by limiting data sizes up front you avoid wasted storage space, such as by using the "enum" type rather than "varchar" when a field that takes string values has a limited number of valid entries.

## There's More Than One Way to "Split" a Table

Generally speaking, the bigger the database table, the longer it takes to access and modify. Unfortunately, database performance optimization isn't as simple as dividing big tables into several smaller ones. Michael Tocker describes 10 ways to improve the speed of large MySQL tables in an October 24, 2013, post on his Master MySQL blog.

One of the 10 methods is to use partitioning to reduce the size of indexes by creating several "tables" out of one. This minimizes index->lock contention. Tocker also recommends using InnoDB rather than MyISAM even though MyISAM can be faster at inserts to the end of a table. MyISAM's table locking restricts updates and deletes, and its use of a single lock to protect the key buffer when loading or removing data from disk causes contention.

Much confusion surrounds the concept of database table partitioning, particularly how partitioning is distinguished from sharding. When the question was posed on Quora, Mosaic CTO Tony Bako explained that partitioning divides logical data elements into multiple entities to improve performance, availability, and maintainability.

Conversely, sharding is a form of horizontal partitioning that creates replicas of the schema and then divides the data stored in each shard by the shard key. This requires that DBAs distribute load and space evenly across shards based on data-access patterns and space considerations.

![](https://s3-us-west-1.amazonaws.com/morpheus-staging/system/spud_media/188/original/tables1.jpg?1414453819)

_Sharding uses horizontal partitioning to store data in physically separate databases; here a user table is sharded by values in the "s_age" field. Source: CUBRID._

Want to deliver a whole new level of customer experience? Learn how to make [your move from MongoDB to Couchbase Server](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)[.](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)
