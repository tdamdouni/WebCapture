# SQL or NoSQL, That Is The Question!

_Captured: 2017-03-18 at 21:09 from [dzone.com](https://dzone.com/articles/sql-or-nosql-that-is-the-question?edition=285895&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-18)_

[Check out the IT Market Clock report](https://dzone.com/go?i=190126&u=http%3A%2F%2Fgo.mariadb.com%2FGartner-IT-Market-Clock-Download-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dreport%26utm_campaign%3Dgartner_IT-market-clock_dzone%26utm_content%3Dindustry) for recommendations on how to consolidate and replace legacy databases. Brought to you in partnership with [MariaDB.](https://dzone.com/go?i=190126&u=http%3A%2F%2Fgo.mariadb.com%2FGartner-IT-Market-Clock-Download-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dreport%26utm_campaign%3Dgartner_IT-market-clock_dzone%26utm_content%3Dindustry)

We all know that in the database technology world, it comes down to two main database types - SQL (relational) and NoSQL (non-relational). The differences between them are rooted in the way they are designed, which data types they support, and how they store them.

Relational databases are relationally structured entities, usually representing a real-world object; for example, a person or shopping cart details. Non-relational databases are document-structured and distributed, holding information in a folder-like Hierarchy which holds the data in an unstructured format.

In daily language, we call them SQL and NoSQL, which reflects the fact that NoSQL databases are not written in structured query language (SQL) only.

## Reasons to Use a SQL Database

Not every database fits every business need. That's why **many companies rely on both relational and non-relational databases for different tasks**. Although NoSQL databases have gained popularity for their speed and scalability, there are still situations in which a highly structured SQL database might be preferable. Two reasons why you might consider a SQL database are:

  1. **You need ACID compliance (Atomicity, Consistency, Isolation, Durability).** ACID compliance reduces anomalies and protects the integrity of your database. It does this by defining exactly how transactions interact with the database, which is not the case with NoSQL databases, which have a primary goal of flexibility and speed, rather than 100% data integrity.

  2. **Your data is structured and unchanging.** If your business is not growing exponentially, there may be no reason to use a system designed to support a variety of data types and high traffic volume.

## Reasons to Use a NoSQL Database

To prevent the database from becoming a system-wide bottleneck, especially in high volume environments, NoSQL databases perform in a way that relational databases cannot.

The following features are driving the popularity of NoSQL databases like MongoDB, CouchDB, Cassandra, and HBase:

  1. **Storing large volumes of data without structure.** A NoSQL database doesn't limit storable data types. Plus, you can add new types as business needs change.

  2. **Using cloud computing and storage.** Cloud-based storage is a great solution, but it requires data to be easily spread across multiple servers for scaling. Using affordable hardware on-site for testing and then for production in the cloud is what NoSQL databases are designed for.

  3. **Rapid development.** If you are developing using modern agile methodologies, a relational database will slow you down. A NoSQL database doesn't require the level of preparation typically needed for relational databases.

In the next section, we will use examples to show some of the distinctions between these two worlds. We will take a look at one basic example, and then focus on three key topics:

  * Scalability - basic functionality
  * Indexing - basic functionality
  * CRM - advanced functionality

## SQL vs. NoSQL

We will start with some key concepts of relational and NoSQL databases. Below is a graph-structured database for human relationships. In the diagram, (a) shows a schema-less structure, and (b) shows how it can be extended to a normal, structured schema.

![](http://panoply.io/uploads/versions/graph-structured-database---x----990-429x---.JPG)

> _Schema-less means that two documents in a NoSQL data structure don't need common fields and can store different types of data._
    
    
    { Model: "BMW", Color: "Red", Manufactured: 2016 },
    
    
    { Model: "Mercedes", Type: "Coupe", Color: "Black", Manufactured: “1-1-2017” }

In a relational world, you have to store data in a defined structure from which you can then retrieve data. For example (using a JOIN operator between two tables):

As a more advanced topic, and a demonstration of when SQL is a better candidate than NoSQL, I will use the fast [compaction algorithm](http://web.engr.illinois.edu/~sgupta49/papers/compaction.pdf). This recently proposed NoSQL algorithm shows that it is difficult to handle the continuous generation of sorted string tables (called _sstables_). These tables are key-value strings sorted by keys. Their generation, over time, causes the read operation to create a disk I/O bottleneck, and reads become slower than writes in NoSQL databases, thereby negating one of the main advantages of NoSQL databases. In an attempt to reduce this effect, NoSQL systems run the compaction protocols in the background, trying to merge multiple tables in a single table. However, this merging is very resource-intensive.

### Scalability

One of the main differences between NoSQL and SQL is that NoSQL databases are considered to be more scalable than SQL databases. MongoDB, for example, has built-in support for replication and sharding (horizontal partitioning of data) to support scalability. While these features are, up to a point, available in SQL databases, they require significant investment of human and hardware resources.

![](http://panoply.io/uploads/versions/table-sql-vs-nosql---x----1073-844x---.png)

For a detailed comparison of the two options, you can reference [Cattell's proposed classification for data stores](http://www.cattell.net/datastores/Datastores.pdf). This report is summarized below. Testing was performed using three main parameters: concurrency, data storage, and replication. Concurrency was evaluated by analyzing data locking mechanism, multi-version concurrency control, and ACID. Data storage was tested in physical storage and in-memory modes and replication was tested on its support of synchronous or asynchronous modes.

Using data retrieved from these tests, authors concluded that SQL products with clustering capability have shown promising performance per node, and also the capacity for scalability, giving the advantage to RDBMS systems over NoSQL, because of their full ACID compliance.

## Indexing

In RDBMS systems, indexes are used to accelerate data retrieval operations. A missing index means that a table will need to be completely scanned to fulfill a read query.

In SQL and NoSQL, database indexes serve the same purpose, quicker and more optimized retrieval of data. But, how they do this is different, because of different database architectures and differences how data is stored in database engine. While in SQL indexes are in form of B-Trees which show hierarchical structure of relational data, in NoSQL databases they point to documents or parts of documents which, in general, have no relations among them. This is nicely described in [this article](http://sql-vs-nosql.blogspot.co.il/2013/11/indexes-comparison-mongodb-vs-mssqlserver.html), which goes into deep technical detail on this topic.

## Example: CRM Application

CRM applications are one of the best examples of big data environments, with huge daily data volumes and numbers of transactions. All vendors of these applications are using both SQL and NoSQL, and while the transactional data is still mostly stored in SQL databases, with improvements of publicly available DBaaS (database-as-a service) services like AWS DynamoDB and Azure DocumentDB, much more data processing could move to NoSQL world running on the clouds.

While these manage services remove security and technical access challenges, it is also an area where NoSQL databases are used for what they are primarily made -- analytic storage and data mining. The amount of data stored in huge CRMs in telecom or finance companies would be nearly impossible to analyze using data mining tools such as SAS or R, because the demand on hardware resources in a transactional world would be massive.

[Unstructured](http://panoply.io/blog/how-data-structures-impact-the-data-warehouse/), document-like data, which constitutes the input to statistical models, which then give companies the ability to do churn or marketing analysis, is the key benefit of these systems. CRM is also one of the best examples where these two systems are not competitors, but exist in harmony, each playing its own role in the bigger data architecture.

## Conclusion

It's possible to choose one option and switch to another later, but with good planning you can save a lot of time and money. It basically comes down to this:

**Indicators for projects where SQL is ideal:**

  * Logic-related discrete data requirements which can be identified up front
  * Data integrity is essential
  * Standards-based proven technology with good developer experience and support.

**Indicators for projects where NoSQL is ideal:**

  * Unrelated, indeterminate, or evolving data requirements
  * Simpler or looser project objectives, able to start coding immediately
  * Speed and scalability is imperative

It is, however, obvious that this is no longer an issue of SQL vs. NoSQL. Instead, it's SQL and NoSQL, with both having their own clear places, and increasingly being integrated into each other. Microsoft, Oracle, and Teradata, for example, are now all selling some form of Hadoop integration to connect SQL-based analysis to the world of unstructured big data.

Interested in reducing database costs by moving from Oracle Enterprise to open source subscription? [Read the total cost of ownership (TCO) analysis.](https://dzone.com/go?i=190127&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017OracleTCO_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3DOracle-TCO%26utm_content%3Dcompetitive) Brought to you in partnership with [MariaDB](https://dzone.com/go?i=190127&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017OracleTCO_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3DOracle-TCO%26utm_content%3Dcompetitive).
