# Pros and Cons of Database Normalization

_Captured: 2017-06-01 at 00:40 from [dzone.com](https://dzone.com/articles/pros-and-cons-of-database-normalization?edition=304109&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-31)_

### To normalize or not to normalize? Find out when the normalization of a database is helpful and when it is not at all helpful.

[Download the Guide to Open Source Database Selection: MySQL vs. MariaDB](https://dzone.com/go?i=214226&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017MariaDBvs.MySQL_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dtext-ad%26utm_campaign%3Dmysql-mariadb-comparison_dzone%26utm_content%3Dcompetitive) and see how the side-by-side comparison of must-have features will ease the journey. Brought to you in partnership with [MariaDB](https://dzone.com/go?i=214226&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017MariaDBvs.MySQL_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dtext-ad%26utm_campaign%3Dmysql-mariadb-comparison_dzone%26utm_content%3Dcompetitive).

When using a relational database, normalization can help keep the data free of errors and can also help ensure that the size of the database doesn't grow large with duplicated data. At the same time, some types of operations can be slower in a normalized environment. So, when should you normalize and when is it better to proceed without normalization?

## What Is Normalization?

Database [normalization](http://en.wikipedia.org/wiki/Database_normalization) is the process of organizing data within a database in the most efficient manner possible. For example, you likely do not want a username stored in several different tables within your database when you could store it in a single location and point to that user via an ID instead.

By keeping the unchanging user ID in the various tables that need the user, you can always point it back to the appropriate table to get the current username, which is stored in only a single location. Any updates to the username occur only in that place, making the data more reliable.

![](https://s3-us-west-1.amazonaws.com/morpheus-staging/system/spud_media/368/original/1nf.png?1424210006)

> _An example of using the first normal form. Source: ChatterBox's .NET._

## What Is Good About Database Normalization?

A normalized database is advantageous when operations will be write-intensive or when [ACID compliance](http://en.wikipedia.org/wiki/ACID) is required. Some advantages include:

  1. **Updates run quickly** due to no data being duplicated in multiple locations.
  2. **Inserts run quickly** since there is only a single insertion point for a piece of data and no duplication is required.
  3. **Tables are typically smaller** than the tables found in non-normalized databases. This usually allows the tables to fit into the buffer, thus offering faster performance.
  4. **Data integrity and consistency is an absolute must** if the database must be ACID compliant. A normalized database helps immensely with such an undertaking.

## What Are the Drawbacks of Database Normalization?

A normalized database is not as advantageous under conditions where an application is read-intensive. Here are some of the disadvantages of normalization:

  1. **Since data is not duplicated, table joins are required**. This makes queries more complicated, and thus read times are slower.
  2. **Since joins are required, indexing does not work as efficiently**. Again, this makes read times slower because the joins don't typically work well with indexing.

## What If the Application Is Read-Intensive and Write-Intensive?

In some cases, it isn't as clear that one strategy should be used over the other. Obviously, some applications really need both normalized and non-normalized data to work as efficiently as possible.

In such cases, companies will often use more than one database: a relational data such as MySQL for ACID compliant and write-intensive operations and a NoSQL database such as MongoDB for read-intensive operations on data where duplication is not as big of an issue.

![](https://s3-us-west-1.amazonaws.com/morpheus-staging/system/spud_media/370/original/dbcompare.jpg?1424210111)

> _What NoSQL and SQL databases do well. Source: SlideShare._

Interested in reducing database costs by moving from Oracle Enterprise to open source subscription? [Read the total cost of ownership (TCO) analysis.](https://dzone.com/go?i=190127&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017OracleTCO_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3DOracle-TCO%26utm_content%3Dcompetitive) Brought to you in partnership with [MariaDB](https://dzone.com/go?i=190127&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017OracleTCO_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3DOracle-TCO%26utm_content%3Dcompetitive).
