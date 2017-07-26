# Correct Index Choices for Equality + LIKE Query Optimization

_Captured: 2017-04-19 at 22:09 from [dzone.com](https://dzone.com/articles/correct-index-choices-for-equality-like-query-opti?oid=twitter&utm_content=buffer66b20&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

As part of our support services, we do a lot of query optimization. This is where most performance gains come from. Here's an example of the work we do.

Some days ago, a customer arrived with the following table:

And a query that looked like this:

The table had an index `t_msg` that wasn't helping at all: the `EXPLAIN` for our 1000000 rows test table looked like this:

You can see the index is the on that was expected: `t_msg`. But the `key_len` is 4. This indicates that the INT part was used, but that the `msg_type(5)` part was ignored. This resulted examining 100k+ rows. If you have MySQL 5.6, you can see it more clearly with `EXPLAIN FORMAT=JSON` under `used_key_parts`:

The customer had multi-valued strings like `PREFIX:INT:OTHER-STRING` stored in the column`msg_type`, and that made it impossible to convert it to an enum or similar field type that allowed changing the `LIKE` for an equity.

So, the solution was rather simple. Just like for point and range queries over numeric values, you must define the index with the ranged field as the rightmost part. This means the correct index would have looked like `msg_type(5),t2send`. The `EXPLAIN` for the new index provided the customer with some happiness:

You can see the `key_len` is now what we would have expected: four bytes for the INT and another seven bytes for the `VARCHAR` (five for our chosen prefix + two for prefix length). More importantly, you can notice the rows count decreased by approximately 22 times.

We used [pt-online-schema](https://www.percona.com/doc/percona-toolkit/3.0/pt-online-schema-change.html) on the customer's environment to apply `ALTER` to avoid downtime. This made it an easy and painless solution, and the query effectively executed in under 1/20 of the time! So, all fine and dandy? Well, almost. We did a further test, and the query looked like this:

So, where's the difference? The length of the string used for the `LIKE` condition is shorter than the prefix length we choose for the `VARCHAR` part of the index (the customer intended to lookup strings with only three chars, so we needed to check this). This query also scanned 100k rows, and `EXPLAIN` showed the `key_len` was 4, meaning the `VARCHAR` part was being ignored once again.

This means the index prefix needed to be shorter. We ALTERed the table and made the prefix four characters long, counting on the fact that the multi-valued strings were using `:` to separate the values, so we suggested the customer include the colon in the lookup string for the shortest strings. In this case, `'abc%'` would be `'abc:%'` (which is also four characters long).

As a final optimization, we suggested dropping old indexes that were covered by the new `better_multicolumn_index`, and that were most likely created by the customer while testing optimization.

## Conclusion

Just like in point-and-range queries, the right order for multi-column indexes is putting the ranged part last. Equally important is that the length of the string prefix needs to match the length of the shortest string you intend to look-up. Just remember that you can't make this prefix too short or you'll lose specificity and the query will end up scanning rows unnecessarily.
