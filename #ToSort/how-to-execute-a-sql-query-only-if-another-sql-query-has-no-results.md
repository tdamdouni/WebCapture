# How to Execute a SQL Query Only If Another SQL Query Has No Results

_Captured: 2017-06-08 at 21:21 from [dzone.com](https://dzone.com/articles/how-to-execute-a-sql-query-only-if-another-sql-que?edition=304123&utm_source=weekly%20digest&utm_medium=email&utm_campaign=wd%202017-06-07)_

I stumbled upon an [interesting question on Stack Overflow](https://stackoverflow.com/q/44265810/521799) recently. A user wanted to query a table for a given predicate. If that predicate returns no rows, they wanted to run another query using a different predicate. Preferably in a single query.

Challenge accepted!

## Canonical Idea: Use a Common Table Expression

We're querying the [Sakila database](https://www.jooq.org/sakila) and we're trying to find films of length 120 minutes. If there are no such films, then let's find films of length 130 minutes. The following query is formally correct and runs without any adaptations on all of Oracle, PostgreSQL and SQL Server (and probably on other DBs too, as it's pretty standard):

How does it work?

The common table expression (`WITH` clause) wraps the first query that we want to execute no matter what. We then select from the first query and use `UNION ALL` to combine the result with the result of the second query, which we're executing only if the first query didn't yield any results (through `NOT EXISTS`). We're hoping here that the database will be smart enough to run the existence check on a pre-calculated set from the first subquery in order to be able to avoid running the second subquery.

Let's see which database actually does this.

## PostgreSQL

Running `EXPLAIN ANALYZE`…

…we can see the following plan:
    
    
        ->  Seq Scan on film film_1  (cost=0.00..68.50 rows=9 width=394) (actual time=0.047..0.289 rows=9 loops=1)
    
    
      ->  CTE Scan on r  (cost=0.00..0.18 rows=9 width=672) (actual time=0.051..0.297 rows=9 loops=1)

So, indeed, the database seems to be smart enough to avoid the second query, because the first one does yield nine rows.

Can we see this in a benchmark, as well? In principle, the complete query should take about as much time in a benchmark as the Common Table Expression alone. Here's the benchmark logic:

The result is:

As you can see, the second statement is consistently slower by around 5%-10%. So we can safely say, the second subquery looking for length = 130 is not executed, but there's still some overhead compared to making a decision in a client application to avoid that second subquery entirely. My guess here is that this is due to PostgreSQL's Common Table Expression (CTE) being "optimisation fences," i.e. the CTE is materialized every time. [See here for more](https://blog.2ndquadrant.com/postgresql-ctes-are-optimization-fences/).

### **What About the Inverse Case?**

In the above benchmark, we've measured how much time it takes when the first query succeeds (and the second query should be avoided). What about the inverse case, where the first query doesn't match any rows and we have to run another query?

Benchmark time!

The result is roughly the same:

A slight overhead in the single query case.

But what's this? We didn't even have an index on the `LENGTH` column. Let's add one!

Now, the result is very different. Query 1 succeeds:

Query 1 fails:

## Oracle

In Oracle, I couldn't find any difference in execution speed (see below). The plan of a combined query also contains an element that prevents the execution of the second subquery. In this case, I'm using the `/*+GATHER_PLAN_STATISTICS*/` hint to make sure we get actual execution values/times in our execution plan:

While the estimates are off just as in PostgreSQL (an error that can propagate, see conclusion), the actual rows for the second subquery is zero, and the second subquery is run zero times ("starts"), because we don't have to really access it at all. Excellent. Exactly what we expected!

Here, I've finally created a benchmark that anonymises the results properly by normalising them in order to comply with Oracle's forbidding of publishing benchmark results. The fastest execution time is simply 1, and the other execution times are multiples of that value:

The result being (query 1 succeeds, no index):

Or in the inverse case (query 1 fails, no index):

Adding an index doesn't change much (query 1 succeeds):

Yet, when query 1 fails:

This time, the combined query is a bit faster!

As can be seen, both queries are executed in roughly the same time on Oracle 12c although again, the single query seems to be a little bit slower, but not always. Which is an important reminder to do benchmarking properly! Meaning:

  * Repeat benchmarks several times.
  * Beware of warmup penalties (the first run is often the slowest).
  * Beware of excessive caching effects in benchmarks.
  * Don't trust performance differences that aren't significant.
  * Don't compile any Scala code or chat on Slack while benchmarking. Your system should be idle, otherwise.
  * Remember to benchmark the right data set. We only have 600 films in this table. What would happen with 60 million films?

## SQL Server

Same exercise again:

The result, this time, is more drastic (no index, query 1 succeeds):

There is a 30%-40% overhead for the CTE solution over the two query solution. If we don't find any rows in the first query (no index):

…then the difference is slightly less drastic but still clear. The reason here is that SQL Server doesn't avoid the unnecessary subquery:

![](https://lukaseder.files.wordpress.com/2017/05/sql-server-doesnt-avoid-subquery.png)

Too bad! (Note that I was using SQL Server 2014. Perhaps in 2016, this optimization is implemented.)

Note, you can trust me that adding an index doesn't change much in this case.

## Conclusion

We've seen that we can easily solve the original problem with SQL only: Select some data from a table using predicate A, and if we don't find any data for predicate A, then try finding data using predicate B from the same table.

Oracle and PostgreSQL can both optimise away the unnecessary query 2 by inserting a "probe" in their execution plans that knows whether the query 2 needs to be executed or not. In Oracle, we've even seen a situation where the combined query outperforms two individual queries. SQL Server 2014 surprisingly does not have such an optimisation.

While the performance impact was negligible in all benchmarks (even in SQL Server), we should be careful with these kinds of queries and not entirely rely on the optimiser to "get it right." In all three databases, the cardinality estimates were off. We're working with small data sets, but if data sets grow larger and queries like the above are embedded in more complex queries, then the wrong cardinality estimates can easily produce wrong execution plans (for example, favoring hash join over nested loop joins because of a high number of estimated rows). [An example of this was given in a previous blog post](https://blog.jooq.org/2016/10/20/be-careful-when-emulating-parameterised-views-with-sys_context-in-oracle/).

Nevertheless, we can get quite far with SQL without resorting to procedural client languages. And if I had conducted my benchmark with a JDBC client instead of procedural blocks directly inside of the database, perhaps the single query would have outperformed the double query case -- at least in those cases where query 1 yielded no rows and query 2 had to be executed from a remote client. Probably in Oracle.

[Ultimately, I can only repeat myself. Measure! Measure! Measure!](https://blog.jooq.org/2017/03/29/how-to-benchmark-alternative-sql-queries-to-find-the-fastest-query/) There's no point in guessing. Truth can only be found by measuring actual executions.
