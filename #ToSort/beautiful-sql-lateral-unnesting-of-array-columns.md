# Beautiful SQL: Lateral Unnesting of Array Columns

_Captured: 2017-02-17 at 15:23 from [dzone.com](https://dzone.com/articles/beautiful-sql-lateral-unnesting-of-array-columns?oid=twitter&utm_content=buffere8c7f&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

In PostgreSQL, you can write:

Or in Oracle:

So, roughly the same thing. Now, let's insert some data. How about the thre most recent posts on the [jOOQ blog](http://blog.jooq.org), prior to this one:

In PostgreSQL:

Or in Oracle:

Now, the array type by itself is not very useful. When it gets really interesting is when we unnest it again into a table. For instance in PostgreSQL:

Note that we're using the keyword `LATERAL` in some of the above queries. For those of you who are used to T-SQL syntax, it's almost the same thing as `[APPLY`](https://technet.microsoft.com/en-us/library/ms175156\(v=sql.105\).aspx). Both `LATERAL` and `APPLY` are also very useful with table valued functions (stay tuned for a blog post on those).

The idea behind `LATERAL` is that the table (derived table, subquery, function call, array unnesting) on the right side of `LATERAL` can "laterally" access stuff from the left side of `LATERAL` in order to produce new tables. In the above query, we're producing a new table of tags for each blog post, and then we [cross join](https://en.wikipedia.org/wiki/Cartesian_product) the two tables.

Here's what the above queries result in:

You can immediately see the cross join semantics here, as we're combining each tag (per post) with its post.

Looking for ordinals (i.e. the tag number inside of the array) along with the array? Easy!

Just add the powerful `WITH ORDINALITY` clause after the `UNNEST()` call in PostgreSQL:

A bit more complicated to emulate in Oracle:

The result now contains the tag "ID", i.e the ordinal of the tag inside of the array:

Now, imagine looking for those blog posts that are tagged "jooq". Easy!

PostgreSQL:

## Conclusion

These are just a few nice things we can do when we denormalize our data into nested collections/arrays, and then use features like `UNNEST` to bring them back to the table level. Both Oracle and PostgreSQL support a variety of really nice features building on top of arrays, so do check them out!
