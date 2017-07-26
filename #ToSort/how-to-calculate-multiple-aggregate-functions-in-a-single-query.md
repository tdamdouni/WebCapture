# How to Calculate Multiple Aggregate Functions in a Single Query

_Captured: 2017-04-23 at 10:13 from [dzone.com](https://dzone.com/articles/how-to-calculate-multiple-aggregate-functions-in-a?edition=292908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-22)_

At a customer site, I've recently encountered a report where a programmer needed to count quite a bit of stuff from a single table. The counts all differed in the way they used specific predicates. The report looked roughly like this (as always, [I'm using the Sakila database for illustration](https://www.jooq.org/sakila)):

And then, unsurprisingly, combinations of these predicates were needed, as well. For example:

In the end, there were 32 queries in total (or 8 in my example) with all the possible combinations of predicates. Needless to say, running them all took quite a while because the table had around 200M records and only one predicate could profit from an index.

But in fact, the improvement is really easy. There are several options to calculate all these counts in a single query

## Simple Solution That Works on All Databases: Filtered Aggregate Functions (or Manual Pivot)

This solution allows for calculating all results in a single query by using 8 different, explicit, [filtered aggregate functions](https://blog.jooq.org/2014/12/30/the-awesome-postgresql-9-4-sql2003-filter-clause-for-aggregate-functions/) and no `[GROUP BY` clause](https://blog.jooq.org/2014/12/04/do-you-really-understand-sqls-group-by-and-having-clauses/) (none in this example. More complex cases where `GROUP BY` persists are sill imaginable).

This is how it works on all databases:

Which yields:

How do we read the above query?

Instead of evaluating the three different predicates in a `WHERE` clause, we pre-calculate it in a derived table (subquery in the `FROM` clause) and translate the predicate in some random value (i.e. `1`) if `TRUE` and `NULL` if `FALSE`. Note, I omitted the `ELSE` clause from the `CASE` expression, which means that we get `NULL`s per default. Running the nested select on its own…

…yields something along the lines of:

Now, in the outer query, we're using once `COUNT(*)`, which simply counts all the rows regardless of any predicates in the `CASE` expressions. The other `COUNT(expr)` aggregate functions do something that surprisingly few people are aware of (yet a lot of people use this form "by accident"). They count only the number of non-`NULL` rows. For instance:

Or also:

These queries will count those films whose length is `BETWEEN 120 AND 150` (because those rows produce the value `1`, which is non-`NULL`, and thus counted), whereas all the other films are not being counted.

Finally, I just used a trick to combine nullable values to make sure they're all non-`NULL`:

This counts those rows whose `length BETWEEN 120 AND 150`_and_ whose `language_id = 1`, because if either predicate was `FALSE`, the number would be `NULL` and thus the sum is `NULL` as well.

## **PostgreSQL and HSQLDB Variant: FILTER**

In PostgreSQL and HSQLDB (and in the SQL standard), there's a special syntax for this. We can use the `FILTER` clause instead of encoding values in `NULL`/non-`NULL` like this:

Or even, writing out the entire predicates again:

Usually, the `FILTER` clause is more convenient, but both approaches are equivalent, and we're running only a single query!

I also call this manual `PIVOT` because it really works like a `PIVOT` table. And the good news is…there is a `PIVOT` syntax!

## A More Fancy Solution: PIVOT

This solution is vendor-specific and only works in Oracle and with a bit fewer features in SQL Server. Here's the Oracle version:

How to read this solution? There are three steps.

### **Step 1: The Derived Table**

As in the previous example, we're translating the desired predicates for our report into three columns that produce values `1` and `0`. That's understood so I won't repeat the explanation.

### **Step 2: The PIVOT Clause**

The `[PIVOT` clause](https://blog.jooq.org/2014/08/05/are-you-using-sql-pivot-yet-you-should/) can be applied to a table expression to "pivot" it in a similar way as we're used from Microsoft Excel's powerful pivot tables. It takes three parts:

  * A list of aggregate functions.
  * An expression (`FOR` clause).
  * A list of expected values (`IN` clause).

The resulting table expression groups the `PIVOT`'s input table by all the remaining columns (i.e. all the columns that are not part of the `FOR` clause, in our example, that's no columns), and aggregates all the aggregate functions (in our case, only one) for all the values in the `IN` list.

If we `SELECT *` from this `PIVOT` table:

…we'll get these values:

As you can see, the column names are generated from the `IN` list of expected values and the values contained in these columns are aggregations for the different predicates. These aggregations are not exactly the ones we wanted. For instance, column `G` is all the films whose `length BETWEEN 120 AND 150` and whose `language_id = 1` and whose `RATING != 'PG'`.

### **Step 3: Summing the Count Values**

So, in order to get the expected results, we have to sum all the partial counts as such:

The result is now the same.

## A More Fancy Solution: GROUPING SETS

`[GROUPING SETS` are a SQL standard](https://blog.jooq.org/2011/11/26/group-by-rollup-cube/) and they're supported in at least:

  * DB2.
  * HANA.
  * Oracle.
  * PostgreSQL.
  * SQL Server.
  * Sybase SQL Anywhere.

Simply put, `GROUPING SETS` allow for grouping a table several times and creating a `UNION` of all the results. For example, the following two queries are the same, conceptually, although the `GROUPING SETS` one is usually faster:

Both queries yield:

Clearly, the `GROUPING SETS` variant is more concise. Let's imagine, we'd like to add more combinations of grouping columns. For example:

Now, we're grouping by all the combinations of columns, and the result is:

Of course, this would all be more impressive if we had more than one language in the system…

So, how do we solve the original problem with `GROUPING SETS`? Here's how:

Wow. How do we read this? In four steps:

### **Step 1: Again, the Derived Table**

This time, we'll encode `FALSE` as `0`, not `NULL`, because `NULL` already has a different meaning in `GROUPING SETS`. It means that for a given `GROUPING SET`, we didn't group by that column. We'll see that in Step 3.

### **Step 2: The GROUPING SETS**

In this section, we're just listing all the possible combinations of `GROUP BY` columns that we want to use, which produces 8 distinct `GROUPING SETS`. I've already explained this in the previous introduction to `GROUPING SETS`, so this is no different.

### **Step 3: Filter Out Unwanted Groupings**

Just like in the `PIVOT` example, we're also getting results for which the predicates are `FALSE`, but we don't want those in the result. So we're filtering them out in the `HAVING` clause:

How do we read this? `LENGTH` can be any of:

  * `1`: The length predicate was `TRUE`.
  * `0`: The length predicate was `FALSE`.
  * `NULL`: The length column is not considered for a given `GROUPING SET`, i.e. `()` or `(rating, language_id)`.

So, using `COALESCE`, we're making sure that we include only `1` and `NULL` lengths, not `0` lengths.

### **Step 4: Ordering the Results**

This is optional, but in order to get the same output order as before, we can use the special `GROUPING_ID()` (or `GROUPING()` depending on the DB) function which returns an ID for each `GROUPING SET`. The output is:

Excellent! And hey, there's even syntax sugar for "special" `GROUPING SETS` configurations like ours, where we list all the possible column permutations. In this case, we can use `CUBE()`!

## Performance

Such a comparison blog post wouldn't be complete if we wouldn't benchmark for performance. This time, I'll be benchmarking only for Oracle, as PostgreSQL doesn't support `PIVOT` and SQL Server's PIVOT is more limited than Oracle's.

Here's the complete benchmark:

And the results:

Very disappointingly, the `PIVOT` solution is the slowest every time. I'm assuming there's some substantial temporary object overhead which wouldn't be as severe if the table were much larger, but clearly, the manual `PIVOT` solution (`COUNT(CASE ...)`) and the `GROUPING SETS` solution heavily outperform the initial attempt, where we calculate 8 counts individually.

To get back to the original report where 32 counts were calculated: The report was roughly 20x as fast with manual `PIVOT` on 200M rows and imagine if you need to `JOIN` -- you definitely want to avoid those 32 individual queries and calculate everything in one go.
