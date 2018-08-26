# Search Engines vs. Relational Databases

_Captured: 2018-03-11 at 18:40 from [dzone.com](https://dzone.com/articles/search-engine-solr-vs-relational-database?edition=365237&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-11)_

Access NoSQL and Big Data through SQL using standard drivers (ODBC, JDBC, ADO.NET). [Free Download ](https://dzone.com/go?i=250345&u=https%3A%2F%2Fwww.cdata.com%2Ftech%2Fbigdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbump3%2520)

Recently, we launched a new product INVESTimate from HomeUnion. INVESTimate is using machine learning and AI to help determine the investment potential of a residential property. INVESTimate is powered by big data on 110 million homes, institutional quality research, and on-the-ground experts with deep insight on local real estate market conditions.

Behind the scenes, there is lots of data crunching, with data coming from more than 50+ sources, and mapping key property data with custom modeled PRICE AVM, RENT AVM, and Neighborhood Investment Rating (NIR) for more than 100M residential homes and 30,000+ neighborhoods. All this data are stitched together and indexed in the Apache Solr Search Engine for display of data in the front-end search portal.

The main purpose of this article is to discuss why we chose Solr Search Engine vs. MySQL or any relational database for storing, indexing, and retrieving data.

First, let's understand the five key differences between search engines and relational databases. In our case, Apache Solr is our chosen search engine and MySQL is our RDBMS :

**Category**
**MySQL**
**Solr**

Transaction Capability
Supports ACID (Atomicity, Consistency, Isolation, Durability) properties
Very less support or no support for ACID

Partitioning
Horizontal partitioning and sharding
Supports only sharding 

Consistency
Immediate consistency
Eventual consistency

Keys
Support primary and foreign key
Supports only primary key

Models
Relational model
Document store

Now, let's look at how and where we can efficiently use RDBMS vs. a search engine by taking a simple use case. Let's say, an investor is looking for an investment property located in Dallas, with an investment of $150,000 located next to the best schools in a simple drill-down wizard type of experience. This would be a perfect use case for an RDBMS-based solution, as the desired results could be presented to the users as a series of fixed, structured queries on the database. First, the top-level query can select all properties within Dallas; then, it can filter properties that fit within or equal to 150K and sort properties based on school ranking within that neighborhood. The investor can finally pick a property of his choice or his liking.

Let's take a simple use case in which search engines are very useful. Let's say an investor is looking for "textual" type of search experience. The investor simply types, "Find an investment property in the range of 150,000 with 8% yield." As you know, Solr stores data as documents and each document represents multiple fields with values. The documents represent a unit of search and index. The above textual content submitted by users is tokenized and matched with all the documents and based on relevancy, respective results are displayed to users. This allows for better user experience to find what users want in a fast and efficient way.

## **Technical Usage**

  1. All of our 110M properties with key attributes are processed and enriched in a big data environment. The processed data gets stored and indexed in the Solr Engine on a regular basis using DIH (Data Import Handler) within 15 minutes.

  2. Using Solr for ReadOnly for better performance. All queries coming from our INVESTimate website hit our Solr engine for most of the data required to be served.

  3. Created Java Interface using SolrJ for front-end to interact with Solr Engine. This completely encapsulates and decouples from front-end code and allows services to be scalable independently

  4. Our HomeUnion Asset Recommendation Engine (HARE) is built on top of Solr Engine for the recommendation of properties and search of portfolios. We have used the concepts of facets and boosting very extensively to recommend search results to our Investors

  5. Reduce load on our MySQL database. 90% of our searches are served by a Solr engine hosted within AWS, thereby reducing cost and improving query performance by more than 80%.

Hopefully, this article was useful to learn some practical use cases of using search engines.

[The fastest databases need the fastest drivers](https://dzone.com/go?i=250346&u=https%3A%2F%2Fwww.cdata.com%2Fblog%2Fnews%2F20170601-bigquery-driver-comparison%3Futm_source%3Ddzone%26utm_medium%3Dbump4) \- learn how you can leverage CData Drivers for high performance NoSQL & Big Data Access.

Opinions expressed by DZone contributors are their own.
