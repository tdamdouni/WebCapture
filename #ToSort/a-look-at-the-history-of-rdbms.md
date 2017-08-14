# A Look at the History of RDBMS

_Captured: 2017-08-08 at 20:19 from [dzone.com](https://dzone.com/articles/a-look-at-the-history-of-rdbms?edition=310395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-23)_

Traditional relational databases weren't designed for today's customers. Learn about the [world's first NoSQL Engagement Database](https://dzone.com/go?i=233224&u=https%3A%2F%2Finfo.couchbase.com%2Fengagement_database_white_paper.html) purpose-built for the new era of customer experience.

If you had to pick a unifying technology to bring all developers together, then you could do worse than selecting the relational database. Of course, no topic can truly unify

![](https://www.daedtech.com/wp-content/uploads/2013/07/Friendlies.jpg)

And, why not? We could boil software down to two core components: data and behavior. So, just as we all learn programming languages to express behavior, we also learn some means of recording and persisting our precious data.

When we put enough of this data together in some organized format, we have a database. When we organize that database in a manner known as "relational," we have a relational database. And then, when we add functionality for managing and optimizing access to that relational data, we have a relational database management system (RDBMS).

No doubt you have some familiarity with these products. They include such industry mainstays as Oracle, Microsoft's SQL Server, PostgreSQL, and MySQL, among others.

In fact, they blend so seamlessly into the scenery that you can easily take them for granted. But where did they come from and why? And how have they evolved over the years? Today, let's take a look back at the history of the RDBMS.

## The First Databases

It might surprise you to learn that the concept of a database predates modern computing. You can read about it in more detail [in this article](http://avant.org/project/history-of-databases/), but suffice to say, you can trace the roots of this concept back to the census of 1880 in the U.S. Innovators of that era devised "tabulation machines" that punched holes in so-called "punch cards." These cards and methods for storing them became the original "data bases" (or databases).

In the early 1960s, a man named Charles Bachman automated this concept. He would later [receive a Turing Award for his efforts](http://amturing.acm.org/award_winners/bachman_1896680.cfm) in creating something called "Integrated Data Store" or IDS. Using the concepts taken from physical card databases, such as "file," "field," and "key," he built a system that decoupled application logic from the storage of data into files. Even now, with more than 50 years in between, we would still recognize this as a database.

Drawing from Bachman's lead, two flavors of databases emerged in the 1960s: network databases and hierarchical databases. You can [read about these separately here](http://www.unixspace.com/context/databases.html). Briefly, the hierarchical model structures data into trees, while the network model, a looser structure, permitted the direct modeling of m to n relationships.

## The Relational Revolution

If you haven't heard of E.F. Codd, you may want to read up a bit about him. As far as figures in computer science go, he casts quite a long shadow. Codd conceived of the relational database model we use today. Appropriately, since he worked there, you can [read about him at IBM's site](https://www-03.ibm.com/ibm/history/exhibits/builders/builders_codd.html).

By the time Codd [published his seminal paper](http://www.morganslibrary.net/files/codd-1970.pdf) in 1970, the world had experienced existing database models long enough to understand their benefits and their shortcomings. Chief among these shortcomings was the difficulty caused by the coupling between the data and the physical storage of that data. In other words, the records themselves told searchers where to look for subsequent records.

Back then, as you no doubt understand, both processing power and disk space came at a _much_ higher cost. These systems did fine when initially storing data. But new ways of processing it or the need for new queries created expensive, time-consuming rework.

Codd changed this substantially. His relational model decoupled the form of data from the physical storage of that data. This alone ushered in significant improvements. But Codd's "[12 rules (actually 13 because he zero-indexed them)](http://www.w3resource.com/sql/sql-basic/codd-12-rule-relation.php) would come later. And these rules would call for the elimination of any duplication of data, effectively optimizing the cost of storage, as well.

## The Rise of SQL

Our history is starting to round the modern database into shape. But we still have a good bit of ground to cover.

If you've taken any college level database classes, you have probably heard of [Boyes-Codd Normal Form (BCNF)](http://www.vertabelo.com/blog/technical-articles/boyce-codd-normal-form-bcnf). Don't worry if you have only vague memories of exercises to de-duplicate your schema. I won't make you rehash your coursework, except to recognize that this Codd is the same Codd that fathered the relational model.

His normalization partner in crime, one Raymond Boyce, worked with Codd and another gentleman named Donald Chamberline at IBM. They all did significant work in the database arena. But Boyce and Chamberlin teamed up to create a standard way of requesting information from these newfangled "relational databases." They called it "Structured English Query Language" or "SEQUEL," for short. It later got even shorter and became "Structure Query Language" or "SQL."

While not the only proposed game in town for this type of query, SQL did come to win out. Certainly, many factors contributed. But an arguably killer feature of SQL was its _declarative_ nature. Application programmers need only specify _which_ records they want rather than _how_ to retrieve them. The "how" became an implementation detail of the RDBMS.

## The Internet Explosion

The origin of the relational model took place at IBM in the 70s, as did the conception of SQL. But SQL's big rise took place during the 1980s. So too did the rise of various commercial RDBMS vendors. During the 80s, as everyone normalized around the SQL standard, many RDBMS database products and vendors emerged. RDBMS proved a big commercial hit among businesses.

Like [planetesimals](http://www.universetoday.com/35974/planetesimals/) in a newly formed star system, however, these many small RDBMS did not last. Through a process of accretion, larger competitors absorbed smaller ones until the players we know today began to emerge and mature.

This happened right around the time the internet appeared on the scene. If the explosion following SQL in the 80s had been something, nobody had prepared for what came next. As websites became web apps, data mattered for communications in unprecedented ways. Suddenly, just about every developer on Earth seemed to need client-server access to some RDBMS or another.

This demand put pressure on vendors to optimize, expand feature sets, and generally cater to application developers Vendors bolted on all manner of offerings and encouraged a situation where the RDBMS occupied the role of "center of the universe."

## Competition Revisited

One last puzzle piece remains unattached, here. I bet you can guess. I'm talking, of course, about the emergence of the NoSQL movement.

Recall that when Codd worked, he sought to address expensive bottlenecks from his time: disk space and processing. Relational models economized intensely for space. But sometimes this has come at the price of intense complexity for certain types of data. In other words, not everything lends itself well to relational storage and normalization. Massive transactions logs, for instance, don't really benefit from normalizing.

As the concept of "web scale" grew into our collective consciousness, some began to revisit the ubiquitous assumption of RDBMS for every application. They implemented things like document databases that stored and processed data in new, "non-traditional" ways. And they realized a great deal of success in doing so.

It is with a fitting sense of symmetry that we arrive at the present. Before the RDBMS gained a stranglehold on the computing world, it had a few competitors. Now, about 40 years later, it once again has a few competitors. Few things have mattered as much to computing as the RDBMS. But a history written 40 years from now will categorize it as just one option among many for the age of web scale.

Learn how the world's first [NoSQL Engagement Database](https://dzone.com/go?i=233225&u=https%3A%2F%2Finfo.couchbase.com%2Fengagement_database_white_paper.html) delivers unparalleled performance at any scale for customer experience innovation that never ends.
