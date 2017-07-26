# How to Use SQL INTERSECT to Work Around SQL's NULL Logic

_Captured: 2017-06-04 at 01:17 from [dzone.com](https://dzone.com/articles/how-to-use-sql-intersect-to-work-around-sqls-null?edition=304120&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-03)_

### Stumped at how to get around Oracle's NULL logic when searching for items in a query using 'IN'? In this post, we see if we can't figure out how to make this work.

Learn how to [move from MongoDB to Couchbase Server](https://dzone.com/go?i=206124&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454368%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283402) for consistent high performance in distributed environments at any scale.

_Another_ SQL post this week? I got [nerd-sniped](https://xkcd.com/356/):

![Image title](https://dzone.com/storage/temp/5487347-screen-shot-2017-06-02-at-123642-pm.png)

Oooooh, challenge accepted!

So, let's assume we have a table `T` with columns `(A, B, C)` like this:

As expected, this yields:

Truly exciting.

Now, we want to find all those rows that "match" either `('a', 'b', NULL)` or `('a', NULL, 'b')`. Clearly, this should produce the first two rows, right?

Yes. Now, the canonical solution would be to tediously write out the entire predicate as such:

That's really boring. Sure, we could have factored out the first, common predicate:

That's certainly better from a performance perspective, but Rafael had a nifty idea. Let's use row value expressions (tuples) in our predicates:

Unfortunately, this doesn't yield any results because nothing is equal to `NULL` in SQL (not even `NULL` itself). The above query is the same as this one:

D'oh.

## Solutions

We've got a couple...

### **The Lame One**

The canonical solution then would be a really lame (but perfectly valid) one. Encode `NULL` to be some "[impossible"](https://en.wikipedia.org/wiki/Murphy%27s_law) string value. Rafael suggested `yolo`. Fair enough.

This works:

All we have to do now is to always remember the term `yolo` which means "`NULL`, but not `NULL` thank you SQL."

### **The Hipster One**

But wait! SQL is painstakingly inconsistent when it comes to `NULL`. See, `NULL` really means `UNKNOWN` in three-valued logic, and this means, we never _know_ if SQL abides to its own rules.

Come in `INTERSECT`. Like `UNION` or `EXCEPT` (`MINUS`) in Oracle, as well as `SELECT DISTINCT`, these set operations handle two `NULL` values as `NOT DISTINCT`. Yes, they're not equal but also not distinct. Whatever. Just remember: That's how it is

So, we can write this hipster solution to Rafael's problem:

We create an intersection of the tuple `(a, b, c)`, the left side of Rafael's `IN` predicate, and the desired values on the right side of the `IN` predicate, and we're done.

Clearly less tedious than writing the original predicates, right? (We won't look into performance this time.)

Want to deliver a whole new level of customer experience? Learn how to make [your move from MongoDB to Couchbase Server](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)[.](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)
