# A Look at 5 NoSQL Solutions

_Captured: 2017-07-05 at 21:45 from [dzone.com](https://dzone.com/articles/a-look-at-5-nosql-solutions?edition=306229&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-05)_

Learn how to create flexible schemas in a relational database using [SQL for JSON.](https://dzone.com/go?i=226221&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017JSONPartIIWhitePaper_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dtext-ad%26utm_campaign%3Dtext-ad_json_dzone%26utm_content%3Dproduct)

If you've never seen it, you should take a look at [the Gartner "Hype Cycle."](http://www.gartner.com/technology/research/methodologies/hype-cycle.jsp) Technology changes the world quickly -- and the technology world itself changes even more quickly. This can lead to breathless buzzword saturation, followed by the so-called "trough of disillusionment" when the tech predictably fails to cure world hunger.

[Wired magazine put "big data" in the trough of disillusionment](https://www.wired.com/insights/2013/06/is-big-data-in-the-trough-of-disillusionment/) in 2013, so that placed it at the peak of inflated expectations around 2011. And, as a matter of fact, I remember that time quite well.

Everyone suddenly became interested in something called [NoSQL](http://nosql-database.org/). What was it? What problems did it solve? It didn't matter -- you just needed to start doing it. And, given the year, you should start doing it in a way that somehow involved a mobile app.

![Image title](http://www.daedtech.com/wp-content/uploads/2013/09/Amway.jpg)

## What Is NoSQL?

Neither the big data movement nor NoSQL technologies have gone anywhere. They've woven themselves seamlessly into the fabric of the tech world. Only the hype has abated.

But that doesn't mean everyone obtained perfect clarity about what this involved. When a concept hits the peak of the hype wave, definitions get fuzzy and folks get confused. If you don't believe me, try to obtain universal consensus about what "agile" means. NoSQL suffered the same fate.

You can [read about some of those misconceptions here](http://www.dummies.com/programming/big-data/10-nosql-misconceptions/), but I'd like to focus on the one I recall as most prominent from my experience. Specifically, many people (and particularly relational database traditionalists) seemed to believe NoSQL was some kind of off-brand competitor to traditional databases; that is, you could go with Oracle, SQL Server, or NoSQL.

I highlight that misconception to underscore the counterpoint. I've seen a few different suggested meanings of the acronym, but I favor "Not Only SQL." Simply put, the NoSQL movement represented the idea that there were other options for storing data besides relational databases.

## A Brief History of Relational Databases

Databases existed dating back to the 1960s, but the relational database came of age during the 1970s. A man named Codd proposed in an academic paper the use of a relational model to decouple physical from logical storage. This model took off because it economized an expensive commodity: disk space.

Over the next two decades, relational database management systems (RDBMS) became the norm. Major players built major products and expanded the offering from simple structured query languages (SQL) to more robust, complex surrounding tooling. As the Internet exploded onto the scene, RDBMS cemented themselves as the cornerstone of the technical world. Any non-trivial application had, right at its heart, an RDBMS.

But during this time, a curious parallel development happened a bit more quietly. Disk space became less expensive and, eventually, pretty cheap. And people started questioning the wisdom of a 30-year-old database model built upon a now outdated assumption.

This questioning lies at the heart of the NoSQL movement: "Why does everything need to be stored in relational databases?" Their answer? It doesn't.

NoSQL thus represents not only a variety of products but a variety of _types _of storage made by a variety of types of vendors. Let's take a look at some of the more prominent ones.

### MongoDB

I'll start with [MongoDB](https://www.mongodb.com/), one of the most prominent and widely known options. A document database, MongoDB supports storing information in JSON format. It's open source, and it doesn't require a DBA to administer. These characteristics make it extremely popular with developers and easily approachable, particularly during early stages of project development.

You'll find yourself most interested in MongoDB if you do large volumes of writes and have big data-scale volumes to deal with. It also does well in situations where you need a high degree of availability in uncertain environmental conditions. And, of course, the lack of need for a dedicated DBA should appeal to groups, well, without a dedicated DBA.

### Cassandra

Next up, consider [Apache Cassandra](http://cassandra.apache.org/). Cassandra came into existence at Facebook and is a key-value, column-oriented database. This provides somewhat more familiar of a feel for those coming from the RDBMS world than a document database. Cassandra Query Language (CQL) reinforces that familiarity. It really shines at providing continuous availability across distributed servers.

You should give Cassandra a look when managing massive data volumes that simply cannot fit on a single server. This might include click analytics for websites, for instance. If you want this data, want highly available access to it, and want a familiar-ish experience, then check Cassandra out.

### CouchDB

Speaking of Apache products, I'll talk next about [CouchDB](http://couchdb.apache.org/). Another document database like MongoDB, users access CouchDB using JSON over HTTP. As you might imagine, this makes it particularly well suited for web applications. Like Cassandra, CouchDB favors availability and partition tolerance, at the expense of consistency. MongoDB, on the other hand, defaults to favoring consistency and partition tolerance. CouchDB is another open source tool.

When considering its use, you should definitely give it a strong look when building web-based applications or mobile applications. The HTTP and REST query mechanisms will make you feel right at home. This dovetails nicely with the way that CouchDB provides high availability. It also serves well should you need a highly reliable solution.

### Redis

[Redis](https://redis.io/) has one highly significant difference from the rest of the NoSQL solutions listed here. It runs in memory, which makes it lightning fast. Like MongoDB, it falls on the CP (consistency and partition tolerance) side of the [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem), and like Cassandra, it furnishes key-value lookups. It is also an open source tool.

Obviously, this lends itself to some pretty obvious use cases. When you need something extremely fast and performant, Redis offers a great starting point. It also makes a whole lot of sense to use when you find yourself building some kind of caching layer.

### HBase

Lastly comes another Apache solution: [HBase](https://hbase.apache.org/). Neither a document database nor a key value database, it qualifies as a "wide column store." HBase drives the well-known Hadoop product, and it does this by providing a conceptual store of billions of rows by millions of columns. Like Redis, it gives you consistency and partition tolerance.

With HBase, you have, in a sense, the epitome of big data. This makes sense to use when you want _serious_ data processing capabilities and the use of map/reduce. Use this system for complex computational work.

## Keep Your Options Open

My intent here today was to introduce you to some NoSQL tools that exist. But I also wanted to advance the notion that a rich world of options exists outside of the relational database world.

Make no mistake -- I have nothing at all against relational databases. They still solve a lot of problems really well. And that's why I really enjoy the particular interpretation of NoSQL that I favor: _not only_ SQL. Make yourself aware of the other options so that you can pick the best tool for the job.

Create flexible schemas using dynamic columns for semi-structured data. [Learn how](https://dzone.com/go?i=226222&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017JSONPartI_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3Dtext-ad_dynamic-columns_dzone%26utm_content%3Dproduct).
