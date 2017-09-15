# Do You Really Need That SQL to Be Dynamic?

_Captured: 2017-09-07 at 19:50 from [dzone.com](https://dzone.com/articles/do-you-really-need-that-sql-to-be-dynamic?edition=324491&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-07)_

Traditional relational databases weren't designed for today's customers. Learn about the [world's first NoSQL Engagement Database](https://dzone.com/go?i=233224&u=https%3A%2F%2Finfo.couchbase.com%2Fengagement_database_white_paper.html) purpose-built for the new era of customer experience.

Dynamic SQL refers to a SQL statement that is constructed, parsed, and executed "dynamically" at run time (vs. "statically" at compile time).

It's very easy to write static SQL in PL/SQL program units (one of the great joys of working with this database programming language). It's also quite easy to implement dynamic SQL requirements in PL/SQL.

But that doesn't mean you _should_. The bottom line regarding dynamic SQL is to **construct and execute SQL at runtime _only when you have to._**

There are several good reasons to _avoid_ unnecessary dynamic SQL:

  1. **Security**: Dynamic SQL opens up the door to SQL injection, which can lead to data corruption and the leaking of sensitive data.
  2. **Performance**: While the overhead of executing dynamic SQL has gone way down over the years, it is certainly still faster to use static SQL.
  3. **Maintainability**: The code you write to support dynamic SQL is more -- literally _more_ code -- and harder to understand and maintain.

Sometimes, the misuse of dynamic SQL is obvious. Consider the following:

The developer apparently believed, however, that since the value of the ID can change, it needs to be concatenated to the SQL statement, so it's gotta be done dynamically. Ha! There's nothing dynamic about this query. It should be rewritten to:

Often, the need for dynamic SQL is compelling at first but then disappears with a little bit of analysis. Consider this function:

Well, heck, if I don't know the table name until run time, I sure can't use a static `SELECT` statement, right? Of course, right!

So, first of all, if this code is _really and truly_ necessary, you need to think about SQL injection.

Is the table name provided directly by the user? You should _never_ allow user input to be stuffed directly into your dynamic statement. They could enter all sorts of nasty stuff.

Even if not passed directly from user fingertips to `EXECUTE IMMEDIATE`, you should use `[DBMS_ASSERT](http://docs.oracle.com/database/122/ARPLS/DBMS_ASSERT.htm#ARPLS231)` to make sure that the table name passed in is a valid DB object, as in:

Great, so the function is less vulnerable than before to injection. But does it really need to be dynamic?

The only way to answer that question is to check and see where and how the function is used. I could do a text search through my code (via an editor like Sublime) or an object search (in SQL Developer). I could also use [PL/Scope](https://stevenfeuersteinonplsql.blogspot.com/search?q=pl%2Fscope) if I'd gathered identifier information across my code base.

Suppose after doing my analysis, I find that the function is called twice as follows:

OK, I _could_ shrug and say, "Yep, two different table names. I need to use dynamic SQL."

But that would be a mistake. What I _should _think and say is, "What? Just two different tables? I don't need dynamic SQL for that. That's just laziness."

Instead, I could do either of the following.

  1. **Create two different functions**. Really, why not? It's so easy and fast to write PL/SQL functions that call SQL. Just change to:
  2. **One function, no dynamic SQL**. So you don't want two, three, etc. functions for the "same" functionality (get a name for ID). Fine, keep them all in one subprogram, but move the conditional logic inside.

Sure, sometimes you really do need to use `EXECUTE IMMEDIATE` and dynamic SQL. In those situations, make sure you minimize the attack surfaces for SQL injection. Make sure you've got strong exception handling and logging.

But do make certain that this extra "technical debt" is necessary. There's a good chance you can get by without dynamic SQL. If so, your users, your fellow developers, and your manager will all thank you!

Learn how the world's first [NoSQL Engagement Database](https://dzone.com/go?i=233225&u=https%3A%2F%2Finfo.couchbase.com%2Fengagement_database_white_paper.html) delivers unparalleled performance at any scale for customer experience innovation that never ends.
