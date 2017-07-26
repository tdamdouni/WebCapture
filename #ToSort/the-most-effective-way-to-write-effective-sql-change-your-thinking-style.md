# The Most Effective Way to Write Effective SQL: Change Your Thinking Style

_Captured: 2017-07-08 at 09:25 from [dzone.com](https://dzone.com/articles/the-most-effective-way-to-write-effective-sql-chan?edition=306238&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-07)_

Learn how to create flexible schemas in a relational database using [SQL for JSON.](https://dzone.com/go?i=226221&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017JSONPartIIWhitePaper_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dtext-ad%26utm_campaign%3Dtext-ad_json_dzone%26utm_content%3Dproduct)

Writing effective SQL queries is one of the biggest problems in the enterprise software world.

The most fundamental problem faced by every company that develops projects on a database is that the performance achieved in development environments can not be achieved in live environments. Generally, the reason for these performance losses is that the volume of data in the live environment is much larger.

These kinds of problems (database operations that run slowly) can occur for a variety of reasons. This article will explain how to think when writing a query, which is the most basic point that can be considered as the starting point of such problems.

I've observed that SQL developers write queries with a procedural approach. In fact, this is very natural because solving problems with a procedural approach is the most convenient solution to human logic. Another reason for this is that almost all of the SQL developers are writing code in Java, C#, or any other programming language at the same time. Java, C#, and so on can be used to train developers to develop their thinking style in a procedural way because when we develop applications with these languages, we use a lot of things like IF .. THEN .. ELSE, FOR .. LOOP, WHILE .. DO, CASE .. WHEN. Naturally, in this case, when applying a business rule to a set of data, it means that each record is processed separately (row-by-row processing). This procedural approach is used in Java, C#, and so on. While developing software with languages is the right approach, it does not produce the same result when it comes to writing queries at the database level (SQL).

Our approach to solving the problem that we are working on at the database level (SQL) should be a `SET` approach (holistic) instead of a procedural approach. To write effective and fast-running code at the database level, we must focus on solving problem solutions with a holistic approach (set-based). It is possible to process a batch of data to be processed in a batch -- it produces highly performant results compared to row-by-row processing.

Let's solve a sample problem with two different approaches and compare the results with each other.

Let's find out how many records are in the `SALES` table for each customer in the `CUSTOMERS` table.

Procedural approach:

![](https://emrahmete.files.wordpress.com/2016/02/prosedurel.png?w=900)

> _Now, let's write our question with a SET -based approach._

![setbased](https://emrahmete.files.wordpress.com/2016/02/setbased.png?w=640&h=254)

We can see that the difference between the `consistent get` numbers between two queries (i.e. when we examine the block numbers that the buffer cache reads) is huge. Queries written with both different approaches led to different numbers of readings at runtime. This difference is explained in terms of performance.

In another example, another frequently observed habit is to call the PL/SQL function from within the SQL statement. This is also a problem-solving approach, which is an example of procedural work. There are other handicaps that affect the performance of calling PL/SQL code from within SQL, but I will not mention a performance problem at that level in this article.

Let's write the code that finds the sum of the purchases of each customer in the `CUSTOMERS` table.

Procedural approach:

In the first step, we create a PL/SQL function that calculates the sum of each customer and then we call this function in our code and output.

![plpro](https://emrahmete.files.wordpress.com/2016/02/plpro.png?w=640&h=252)

> _Now, let's write our question a SET -based approach._

![plbut](https://emrahmete.files.wordpress.com/2016/02/plbut.png?w=640&h=269)

In this example, we can see that the same situation is the case by looking at the consistent `GET` and recursive call output.

Our queries are also the first step in making more efficient database operations, thinking about batch processing, rather than thinking about row-by-row. Approaching this way to solve problems while doing our database operations will allow you to produce less resource-consuming and more fast work at the end of the day.

Create flexible schemas using dynamic columns for semi-structured data. [Learn how](https://dzone.com/go?i=226222&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017JSONPartI_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3Dtext-ad_dynamic-columns_dzone%26utm_content%3Dproduct).
