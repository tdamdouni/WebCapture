# Transaction Tracing Helps Developers Optimize Code as They Write It

_Captured: 2017-03-22 at 22:02 from [dzone.com](https://dzone.com/articles/transaction-tracing-helps-developers-optimize-code?oid=twitter&utm_content=bufferc506a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

The best time for developers to optimize their code is while they are writing it. Developers can leverage the detailed transaction tracing available from [APM-type tools](https://stackify.com/application-performance-management-tools/) like Prefix as a fast feedback loop to understand what their code is doing and how long it takes. Prefix works as an [ASP.NET profiler](https://stackify.com/asp-net-profiler/) and also works with several common JVMs for Java.

## Transaction Tracing Is a Critical Feedback Loop

> "When informed about a problem whilst in the moment, I'm in a much better position to make corrections or come up with alternative solutions. Without a quick feedback loop, the passing of time makes it difficult to get into the initial mindset which caused the problem to begin with." -- [Vince Panuccio](https://stackify.com/asp-net-profiler/)

Lightweight code profilers and other data collect methodologies can be used to provide developers a wealth of information about what their code is doing -- including logging statements, errors, SQL queries, web services, and other dependencies.

Today's applications are complex and typically connect to multiple dependencies like SQL and NoSQL databases, PaaS services, MongoDB, Elasticsearch, Redis, queueing, and many other services. Prefix helps developers instantly understand if their code is using them correctly and how they impact the performance of their app.

![transaction-tracing-prefix](https://stackify.com/wp-content/uploads/2017/01/prefix-error-log-full-trace-2.png)

> _Example transaction tracing captured by Prefix._

As an example, developers can find common problems like [N+1 database query patterns](https://secure.phabricator.com/book/phabcontrib/article/n_plus_one/) caused by SQL queries being run in a loop. Prefix's built-in suggestions highlight a potential problem -- and the 38 database queries become a glaring problem.

![stackify-prefix-n-plus-1](https://stackify.com/wp-content/uploads/2017/01/Stackify-Prefix-n-plus-1.png)

This instant feedback can help developers validate that their code is doing what they expected it to do. Profiling and performance tuning is something developers don't typically do until the tail end of a project. Most of the time, they don't even do it unless there is a known performance issue in the code or they are doing stress testing.

By using tools like Prefix, developers can continually be looking for performance problems in their code as part of their natural development process. The transaction tracing that developers can get from these types of free tools is a must have.

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).
