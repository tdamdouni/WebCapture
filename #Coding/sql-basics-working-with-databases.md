# SQL Basics: Working with Databases

_Captured: 2017-09-02 at 19:25 from [www.dataquest.io](https://www.dataquest.io/blog/sql-basics/)_

SQL, pronounced "sequel" (or ess-cue-ell, if you prefer), is a very important tool for data scientists to have in their repertoire. You may well have heard the name and wondered what it is, how it works and whether you should learn it. To put it simply, SQL (Structured Query Language) is the language of databases and almost all companies use databases to store their data.

Because of this, no matter whether you prefer to use Python, R or something else for analysis, you'll need to have at least a basic knowledge of SQL to be able to access the data to begin with. Job Search Engine [Indeed](https://www.indeed.com/jobs?q=sql&l=usa) shows over 100,000 job listings in the US that mention SQL at the time of writing.

There are a few different database systems (MySQL, PostgreSQL, Microsoft SQL Server to name a few) but all of them speak SQL, so once you've got the hang of the basics you'll be able to work with any of them.

In this tutorial we'll We'll be working with a dataset from the bike-sharing service [Hubway](https://www.thehubway.com), which includes data on over 1.5 million trips made with the service.

![](https://www.dataquest.io/blog/images/jcoe-intro-to-sql/hubway.jpg)

> _Hubway Bicycles in Boston_

We'll start by looking a little bit at databases, what they are and why we use them, before starting to write some queries of our own in SQL.

If you'd like to follow along you can download the `hubway.db` file [here](https://www.dataquest.io/blog/images/jcoe-intro-to-sql/hubway.db).

## Relational Databases

A relational database is, simply, a database that stores related information across multiple tables and allows you to query information in more than one table at the same time.

It's easier to understand how this works by thinking through an example. Imagine you're a business and you want to keep track of your sales information. You could set up a spreadsheet in Excel with all of the information you want to keep track of as separate columns: Order number, date, amount due, shipment tracking number, customer name, customer address, and customer phone number.

![](https://www.dataquest.io/blog/images/jcoe-intro-to-sql/spreadsheet.png)

> _Our sales data in Excel_

This setup would work fine for tracking the information you need to begin with, but as you start to get repeat orders from the same customer you'll find that their name, address and phone number gets stored in multiple rows of your spreadsheet and, as your business grows and the number of orders you're tracking increases, this redundant data will take up unnecessary space and generally decrease the efficiency of your sales tracking system. You might also run into issues with data integrity. There's no guarantee, for example, that every field will be populated with the correct data type or that the name and address will be entered exactly the same way every time.

![](https://www.dataquest.io/blog/images/jcoe-intro-to-sql/frame.png)

> _Our sales data in a relational database_

With a relational database, like the one in the above diagram, you avoid all of these issues. You could set up two tables, one for orders and one for customers. The 'customers' table would include a unique ID number for each customer, along with the name, address and phone number we were already tracking. The 'orders' table would include your order number, date, amount due, tracking number and, instead of a separate field for each item of customer data, it would have a column for the customer ID. This enables us to pull up all of the customer info for any given order, but we only have to store it once in our database rather than listing it out again for every single order.

## Our Data Set

Let's start by taking a look at our database. The database has two tables, `trips` and `stations`. To begin with, we'll just look at the `trips` table, which contains the following columns:

  * `id` \- A unique integer that serves as a reference for each trip
  * `duration` \- The duration of the trip, measured in seconds
  * `start_date` \- The date and time the trip began
  * `start_station` \- An integer that corresponds to the `id` column in the `stations` table for the station the trip started at
  * `end_date` \- The date and time the trip ended
  * `end_station` \- The 'id' of the station the trip ended at
  * `bike_number` \- Hubway's unique identifier for the bike used on the trip
  * `sub_type` \- The subscription type of the user. `"Registered"` for users with a membership, `"Casual"` for users without a membership
  * `zip_code` \- The zip code of the user (only available for registered members)
  * `birth_date` \- The birth year of the user (only available for registered members)
  * `gender` \- The gender of the user (only available for registered members)

## Our Analysis

With this information and the SQL commands we'll learn shortly, here are some questions that we'll try to answer over the course of this post:

  * What was the duration of the longest trip?
  * How many trips were taken by 'registered' users?
  * What was the average trip duration?
  * Do registered or casual users take longer trips?
  * Which bike was used for the most trips?
  * What is the average duration of trips by users over the age of 30?

The SQL commands we'll use to answer these questions are:

  * `SELECT`
  * `WHERE`
  * `LIMIT`
  * `ORDER BY`
  * `GROUP BY`
  * `AND`
  * `OR`
  * `MIN`
  * `MAX`
  * `AVG`
  * `SUM`
  * `COUNT`

## Installation and Setup

For the purposes of this tutorial, we will be using a database system called [SQLite3](https://www.sqlite.org). SQLite has come as part of Python from version 2.5 onwards, so if you have Python installed you'll almost certainly have SQLite as well (Python and the SQLite3 library can easily be installed and set up with [Anaconda](https://www.continuum.io/downloads) if you don't already have them). Using Python to run our SQL code allows us to import the results into a Pandas dataframe to make it easier to display our results in an easy to read format. It also means we can perform further analysis and visualization on the data we pull from the database, although that will be beyond the scope of this tutorial.

Alternatively, if you don't want to use or install Python, you can run SQLite3 from the command line. Simply download the "precompiled binaries" from the [SQLite3 web page](http://sqlite.org/download.html) and use the following code to open the database:
    
    
    ~$ sqlite hubway.db 
    SQLite version 3.14.0 2016-07-26 15:17:14
    Enter ".help" for usage hints.
    sqlite>
    

From here you can just type in the query you want to run and you will see the data returned in your terminal window.

An alternative to using the terminal is to connect to your SQLite database via Python. One advantage is that if you use the Jupyter notebook you can see the results of your queries in a neatly formatted table.

To do this, we'll define a function that takes our query (stored as a string) as an input and shows the result as a formatted dataframe:

## SELECT

The first command we'll work with is `SELECT`. `SELECT` will be the foundation of almost every query you write - it tells the database which columns you want to see. You can either specify columns by name (separated by commas) or use the wildcard `*` to return every column in the table. In addition to the columns you want to retrieve, you also have to tell the database which table to get them from. To do this you use the keyword `FROM` followed by the name of the table. For example, if we wanted to see the `start_date` and `bike_number` for every trip in the `trips` table, we could use the following query:

In this example, we started with the `SELECT` command so that the database knows we want it to find us some data. Then we told the database we were interested in the `start_date` and `bike_number` columns. Finally we used `FROM` to let the database know that the columns we want to see are part of the `trips` table.

One important thing to be aware of when writing SQL queries is that the language requires every query to end with a semicolon (`;`).

## LIMIT

The next command we need to know before we start to run queries on our Hubway database is `LIMIT`. `LIMIT` simply tells the database how many rows you want it to return. The `SELECT` query we looked at in the previous section would return the requested information for every row in the `trips` table, but sometimes that could mean a lot of data and you might not want all of it. If, instead, we wanted to see the `start_date` and `bike_number` for the first five trips in the database, we could add `LIMIT` to our query as follows:

We simply added the `LIMIT` command and then a number representing the number of rows we want to be returned. In this instance we used 5, but you can replace that with any number to get the appropriate amount of data for the project you're working on.

We will use `LIMIT` a lot in our queries on the Hubway database in this tutorial - the `trips` table contains over a 1.5 million rows of data and we certainly don't need to display all of those to answer the questions we're going to be working on.

Let's run our first query on the Hubway database. First we will store our query as a string and then use the function we defined earlier to run it on the database. Take a look at the following example:

id duration start_date start_station end_date end_station bike_number sub_type zip_code birth_date gender

0
1
9
2011-07-28 10:12:00
23
2011-07-28 10:12:00
23
B00468
Registered
'97217
1976.0
Male

1
2
220
2011-07-28 10:21:00
23
2011-07-28 10:25:00
23
B00554
Registered
'02215
1966.0
Male

2
3
56
2011-07-28 10:33:00
23
2011-07-28 10:34:00
23
B00456
Registered
'02108
1943.0
Male

3
4
64
2011-07-28 10:35:00
23
2011-07-28 10:36:00
23
B00554
Registered
'02116
1981.0
Female

4
5
12
2011-07-28 10:37:00
23
2011-07-28 10:37:00
23
B00554
Registered
'97214
1983.0
Female

This query uses `*` as a wildcard instead of specifying columns to return. This means the `SELECT` command has given us every column in the `trips` table. We also used the `LIMIT` function to restrict the output to the first five rows of the table.

You will often see that people capitalize the commmand keywords in their queries (a convention that I shall follow throughout this tutorial) but this is mostly a matter of personal preference for readability rather than something that will affect the function of your code. If you prefer to write your queries with lowercase commands then feel free to do so.

The previous example returned every column in the `trips` table. If we were only interested in the `duration` and `start_date` columns, we could replace the wildcard with the column names as follows:

duration start_date

0
9
2011-07-28 10:12:00

1
220
2011-07-28 10:21:00

2
56
2011-07-28 10:33:00

3
64
2011-07-28 10:35:00

4
12
2011-07-28 10:37:00

## ORDER BY

The final command we need to know before we can answer the first of our questions is `ORDER BY`. This command allows you to sort the database on a given column. To use it, you simply specify the name of the column you would like to sort on. By default, `ORDER BY` sorts in ascending order. If you would like to specify which order the database should be sorted, you can add the keyword `ASC` for ascending order or `DESC` for descending order. For example, if we wanted to sort the `trips` table from the shortest `duration` to the longest we could add the following line to our query:

With the `SELECT`, `LIMIT` and `ORDER BY` commands in our repertoire, we can now attempt to answer our first question: **What was the duration of the longest trip?**

To answer this question, it's helpful to break it down into sections and identify which commands we will need to address each part. First we need to pull the information from the `duration` column of the `trips` table. Then, to find which trip is the longest, we can sort the `duration` column in descending order. Here's how you might work this through to come up with a query that will get the information you're looking for:

  * Use `SELECT` to retrieve the `duration` column `FROM` the `trips` table
  * Use `ORDER BY` to sort the `duration` column and use the `DESC` keyword to specify that you want to sort in descending order
  * Use `LIMIT` to restrict the output to 1 row

Using these commands in this way will return the single row with the longest duration and will provide us the answer to our question.

One more thing to note - as your queries add more commands and get more complicated, you may find it easier to read if you separate them onto multiple lines. This won't affect how the code runs (the system just reads the code from the beginning until it reaches the semicolon) but it can make your queries clearer and easier to follow. In Python, you can separate a string onto multiple lines by using triple quote marks.

Let's go ahead and run this query and find out how long the longest trip lasted.

Now we know that the longest trip lasted 9999 seconds, or a little over 166 minutes. With a maximum value of 9999, however, we don't know whether this is really the length of the longest trip or if the database was only set up to allow a four digit number. If it's that particularly long trips are being cut short by the database, then we might expect to see a lot of trips at 9999 seconds where they reach the limit. Let's try running the same query as before, but adjust the `LIMIT` to return the 10 highest durations and see if that's the case:

duration

0
9999

1
9998

2
9998

3
9997

4
9996

5
9996

6
9995

7
9995

8
9994

9
9994

What we see here is that there aren't a whole bunch of trips at 9999, so it doesn't look like we're cutting off the top end of our durations, but it's still difficult to tell whether that's the real length of the trip or just the maximum allowed value. Hubway charges additional fees for rides over 30 minutes (somebody keeping a bike for 9999 seconds would have to pay an extra $25 in fees) so it's plausible that they decided 4 digits would be sufficient to track the majority of rides.

## WHERE

The previous commands are great for pulling out sorted information for particular columns, but what if you already have a specific subset of the data you want to look at? That's where `WHERE` comes in. The `WHERE` command allows you to use a logical operator to specify which rows should be returned. For example you could use the following command to return every trip taken with bike `B00400`:

You'll also notice that we use quote marks in this query. That's because the `bike_number` is stored as a string. If the column contained numeric data types the quote marks would not be necessary.

Let's write a query that uses `WHERE` to return every column in the `trips` table for each row with a `duration` longer than 9990 seconds:

id duration start_date start_station end_date end_station bike_number sub_type zip_code birth_date gender

0
4768
9994
2011-08-03 17:16:00
22
2011-08-03 20:03:00
24
B00002
Casual

1
8448
9991
2011-08-06 13:02:00
52
2011-08-06 15:48:00
24
B00174
Casual

2
11341
9998
2011-08-09 10:42:00
40
2011-08-09 13:29:00
42
B00513
Casual

3
24455
9995
2011-08-20 12:20:00
52
2011-08-20 15:07:00
17
B00552
Casual

4
55771
9994
2011-09-14 15:44:00
40
2011-09-14 18:30:00
40
B00139
Casual

5
81191
9993
2011-10-03 11:30:00
22
2011-10-03 14:16:00
36
B00474
Casual

6
89335
9997
2011-10-09 02:30:00
60
2011-10-09 05:17:00
45
B00047
Casual

7
124500
9992
2011-11-09 09:08:00
22
2011-11-09 11:55:00
40
B00387
Casual

8
133967
9996
2011-11-19 13:48:00
4
2011-11-19 16:35:00
58
B00238
Casual

9
147451
9996
2012-03-23 14:48:00
35
2012-03-23 17:35:00
33
B00550
Casual

10
315737
9995
2012-07-03 18:28:00
12
2012-07-03 21:15:00
12
B00250
Registered
'02120
1964
Male

11
319597
9994
2012-07-05 11:49:00
52
2012-07-05 14:35:00
55
B00237
Casual

12
416523
9998
2012-08-15 12:11:00
54
2012-08-15 14:58:00
80
B00188
Casual

13
541247
9999
2012-09-26 18:34:00
54
2012-09-26 21:21:00
54
T01078
Casual

As you can see, the query returned 14 different trips, each with a duration of 9990 seconds or more. Something that stands out about this query is that all but one of the results has a `sub_type` of `"Casual"`. Perhaps this is an indication that `"Registered"` users are more aware of the extra fees for long trips and maybe Hubway could do a better job of conveying their pricing structure to Casual users to help them avoid overage charges.

We can also combine multiple logical tests in our `WHERE` clause using `AND` or `OR`. If, for example, in our previous query we had only wanted to return the trips with a `duration` over 9990 seconds that also had a `sub_type` of Registered, we could use `AND` to specify both conditions. I also recommend using parentheses to separate each logical test. This isn't strictly required for the code to function, but they can make your queries easier to understand as you increase the complexity. Let's run that query now. We already know it should only return one result, so it should be easy to check that we've got it right:

The next question we set out at the beginning of the post is **"How many trips were taken by 'registered' users?"** To answer it, we could run the same query as above and modify the `WHERE` expression to return all of the rows where `sub_type` is equal to `'Registered'` and then count them up. You could count them up on the screen, however, SQL actually has a built in command to do the work for us, `COUNT`.

This allows us to shift the calculation to the database and save us the trouble of writing additional scripts to count up results. To use it, you simply include `COUNT(column_name)` instead of (or in addition to) the columns you want to `SELECT`, like this:

In this instance, it doesn't matter which column we choose to count because every column should have data for each row in our query, but sometimes a query might have missing (or "null") values for some rows. If you're not sure whether a column contains null values you can run your `COUNT` on the `id` column - the `id` column is never null, so you can be sure your count won't have missed anything. You can also use `COUNT(1)` or `COUNT(*)` to count up every row in your query. It's worth noting that sometimes you might actually want to run `COUNT` on a column with null values, for example if you wanted to know how many rows in your database have missing values for a column.

Let's take a look at a query to answer our question. We can use `SELECT COUNT(*)` to count up the total number of columns returned and `WHERE sub_type = "Registered"` to make sure we only count up the trips taken by Registered users.

This query worked and has returned the answer to our question, but the column heading isn't particularly descriptive. If you want to make your results more readable, you can use `AS` to give your output an alias (or nickname). If we wanted to re-run the previous query but give our column heading an alias of `Total Trips by Registered Users`, we could do the following:

## Aggregate Functions

`COUNT` is not the only trick SQL has in this domain. You can also use `SUM`, `AVG`, `MIN` and `MAX` to return the sum, average, minimum and maximum of a column respectively. These, along with `COUNT`, are known as **aggregate functions**. So to answer our third question, **"What was the average trip duration?"**, we can use the `AVG` function on the `duration` column (and, once again, use `AS` to give our output column a more descriptive name):

So it turns out that the average trip duration is 912 seconds, which is about 15 minutes. This makes some sense since we know that Hubway charges extra fees for trips over 30 minutes because the service is designed for riders to take short, one-way trips.

But what about our next question, **do registered or casual users take longer trips?** We already know one way to answer this question - we can run two `SELECT AVG(duration) FROM trips` queries with `WHERE` clauses that restrict one to `"Registered"` and one to `"Casual"` users. SQL also includes a way that we can answer this question in a single query, using the `GROUP BY` command.

## GROUP BY

`GROUP BY` separates the rows into groups based on the contents of a particular column and allows us to perform aggregate functions on each group. To get a better idea of how this works, let's take a look at the `gender` column. Each row can have one of three possible values in the `gender` column, `"Male"`, `"Female"` or `Null` (missing - we don't have `gender` data for casual users). When we use `GROUP BY`, the database will separate out each of the rows into a different group based on the value in the `gender` column, in much the same way that you might separate a deck of cards into different suits. You can imagine making two piles, one of all the males, one of all the females.

Once you have your two separate piles, the database will then perform any aggregate function in your query on each of them in turn. If you used `COUNT`, for example, then the query would count up the number of rows in each pile and return the value for each separately.

So let's walk through exactly how to write a query to answer our question of whether registered or casual users take longer trips.

  * As with each of our queries so far, we'll start with `SELECT` to tell the database which information we want to see. In this instance, we'll want `sub_type` and `AVG(duration)`.
  * We'll also include `GROUP BY sub_type` to separate out our data by subscription type and calculate the averages of registered and casual users separately.

Here's what the code looks like when you put it all together:

sub_type Average Duration

0
Casual
1519.643897

1
Registered
657.026067

Well that's quite a difference. On average, registered users take trips that last around 11 minutes whereas casual users are spending almost 25 minutes per ride. Registered users are likely taking shorter, more frequent trips, possibly as part of their commute to work. Casual users, on the other hand, are spending around twice as long per trip. It's possible that casual users tend to come from demographics (tourists, for example) that are more inclined to take longer trips make sure they get around and see all the sights.

Our next question was **which bike was used for the most trips** and we can answer this using a very similar query. Take a look at the following example and see if you can figure out what each line is doing - we'll go through it step by step afterwards so you can check you got it right:

As you can see from the output, bike `B00490` took the most trips. Let's run through how we got there:

  * The first line is a `SELECT` clause to tell the database we want to see the `bike_number` column and a count of every row. It also uses `AS` to tell the database to display each column with a more useful name.
  * The second line uses `FROM` to specify that the data we're looking for is in the `trips` table.
  * The third line is where things start to get a little tricky. We use `GROUP BY` to tell the `COUNT` function on line 1 to count up each value for `bike_number` separately.
  * On line four we have an `ORDER BY` clause to sort the table in descending order and make sure our most-used bike is at the top.
  * Finally we use `LIMIT` to restrict the output to the first row, which we know will be the bike that was used in the highest number of trips because of how we sorted the data on line four.

## Arithmetic Operators

The last of our questions about this table is a little more tricky than the others. We want to know the **average duration of trips by registered members over the age of 30**. We could just figure out the year in which 30 year olds were born in our heads and then plug it in, but a more elegant solution is to use arithmetic operations directly within our query. SQL allows us to use `+`, `-`, `*` and `/` to perform an arithmetic operation on an entire column at once.

## JOIN

So far we've been looking at queries that only pull data from the `trips` table, but you'll remember from the introduction that this database contains a second table, `stations`. The `stations` table contains information about every station in the Hubway network and includes an `id` column that is referenced by the `trips` table.

Before we start to work through some real examples on our dataset, let's take a moment to look back at the hypothetical order tracking database from earlier. In that database we had two tables, `orders` and `customers`, and they were connected by the `customer_id` column. Let's say we wanted to write a query that returned the `order_number` and `name` for every order in the database. If they were both stored in the same table, we could use the following query:

Unfortunately `order_number` column and the `name` column are stored in two different tables, so we have to add a few extra steps. Let's take a moment to think through the additional things the database will need to know before it can return the information we want:

  * Which table is the `order_number` column in?
  * Which table is the `name` column in?
  * How is the information in the `orders` table connected to the information in the `customers` table?

To answer the first two of these questions, we can include the table names for each column in our `SELECT` command. The way we do this is simply to write the table name and column name separated by a `.`. For example, instead of `SELECT order_number, name` we would write `SELECT orders.order_number, customers.name`. Adding the table names here helps the database to find the columns we're looking for by telling it which table to look in for each.

To tell the database how the `orders` and `customers` tables are connected, we use `JOIN` and `ON`. `JOIN` specifies which tables should be connected and `ON` specifies which columns in each table are related. We're going to use an inner join, which means that rows will only be returned where there is a match in our columns specified in `ON`. In this example, we will want to use `JOIN` on whichever table we didn't include in the `FROM` command. So we can either use `FROM orders INNER JOIN customers` or `FROM customers INNER JOIN orders`. As we discussed earlier, these tables are connected on the `customer_id` column in each table. Therefore, we will want to use `ON` to tell the database that these two columns refer to the same thing like this:

Once again we use the `.` to make sure the database knows which table each of these columns is in. So when we put all of this together, we get a query that looks like this:

This query will return the order number of every order in the database along with the customer name that is associated with each.

Moving back to our Hubway database we can now write some queries to see `JOIN` in action, but before we get started we should take a look at the rest of the columns in the `stations` table. Here's a query to show us the first 5 rows so we can see what the `stations` table looks like:

id station municipality lat lng

0
3
Colleges of the Fenway
Boston
42.340021
-71.100812

1
4
Tremont St. at Berkeley St.
Boston
42.345392
-71.069616

2
5
Northeastern U / North Parking Lot
Boston
42.341814
-71.090179

3
6
Cambridge St. at Joy St.
Boston
42.361284999999995
-71.06514

4
7
Fan Pier
Boston
42.353412
-71.044624

  * `id` \- A unique identifier for each station (corresponds to the `start_station` and `end_station` columns in the `trips` table)
  * `station` \- The station name
  * `municipality` \- The municipality that the station is in (Boston, Brookline, Cambridge or Somerville)
  * `lat` \- The latitude of the station
  * `lng` \- The longitude of the station

  * Which stations are most frequently used for round trips?
  * How many trips start and end in different municipalities?

Like before, we'll try to answer some questions in the data, starting with **which station is the most frequent starting point?** Let's work through it step by step:

  * First we want to use `SELECT` to return the `station` column from the `stations` table and the `COUNT` of the number of rows.
  * Next we specify the tables we want to `JOIN` and tell the database to connect them `ON` the `start_station` column in the `trips` table and the `id` column in the `stations` table.
  * Then we get into the meat of our query - we `GROUP BY` the `station` column in the `stations` table so that our `COUNT` will count up the number of trips for each station separately
  * Finally we can `ORDER BY` our `COUNT` and `LIMIT` the output to a manageable number of results

Station Count

0
South Station - 700 Atlantic Ave.
56123

1
Boston Public Library - 700 Boylston St.
41994

2
Charles Circle - Charles St. at Cambridge St.
35984

3
Beacon St / Mass Ave
35275

4
MIT at Mass Ave / Amherst St
33644

If you're familiar with Boston, you'll understand why these are the most popular stations. South Station is one of the main commuter rail stations in the city, Charles Street runs along the river close to some nice scenic routes and Boylston and Beacon streets are right downtown near a number of office buildings.

The next question we'll look at is **which stations are most frequently used for round trips?** We can use much the same query as before. We will `SELECT` the same output columns and `JOIN` the tables in the same way, but this time we'll add a `WHERE` clause to restrict our `COUNT` to trips where the `start_station` is the same as the `end_station`.

Station Count

0
The Esplanade - Beacon St. at Arlington St.
3064

1
Charles Circle - Charles St. at Cambridge St.
2739

2
Boston Public Library - 700 Boylston St.
2548

3
Boylston St. at Arlington St.
2163

4
Beacon St / Mass Ave
2144

As you can see, a number of these stations are the same as the previous question but the amounts are much lower. The busiest stations are still the busiest stations, but the lower numbers overall would suggest that people are typically using Hubway bikes to get from point A to point B rather than just to cycle around for a while before returning to where they started. As for the esplanade being the most popular area for round trips, well, they say a picture is worth a thousand words and this certainly looks like a nice spot for a bike ride.

![](https://www.dataquest.io/blog/images/jcoe-intro-to-sql/esplanade.jpg)

> _The Esplanade in Boston_

Finally, **how many trips start and end in different municipalities?** This question takes things a step further. We want to know how many trips start and end in a different `municipality`. To achieve this, we need to `JOIN` the `trips` table to the `stations` table twice. Once `ON` the `start_station` column and then `ON` the `end_station` column. In order to do this, we have to create an alias for the `stations` table so that we are able to differentiate between data that relates to the `start_station` and data that relates to the `end_station`. We do this in exactly the same way we've been creating aliases for individual columns to make them display with a more intuitive name, using `AS`.

For example we can use the following code to `JOIN` the `stations` table to the `trips` table using an alias of 'start'. We can then combine 'start' with our column names using `.` to refer to data that comes from this specific `JOIN` (rather than the second `JOIN` we will do `ON` the `end_station` column):

Here's what the final query will look like when we run it:

This shows that about 300k out of 1.5 million trips (or 20%) ended in a different municipality than they started in - further evidence that people mostly use Hubway bicycles for relatively short journeys rather than longer trips between towns.

And there you have it, an introduction to SQL. We have covered a number of important commands, `SELECT`, `LIMIT`, `WHERE`, `ORDER BY`, `GROUP BY` and `JOIN`, as well as aggregate and arithmetic functions. These will give you a strong foundation to build on as you continue your SQL journey.

## Next Steps

You should now be able to pick up a database you find interesting and write queries to pull out information you want to work with. Feel free to play around with the Hubway database and see what else you can find out. Here are some other questions you might want to try and answer:

  * How many trips incurred additional fees (lasted longer than 30 minutes)?
  * Which bike was used for the longest total time?
  * Did registered or casual users take more round trips?
  * Which municipality had the longest average duration?

If you would like to take things a step further, you might want to read our post about [exporting the data from your SQL queries into Pandas](https://www.dataquest.io/blog/python-pandas-databases/) or our [SQL Intermediate Tutorial](https://www.dataquest.io/blog/sql-intermediate/).
