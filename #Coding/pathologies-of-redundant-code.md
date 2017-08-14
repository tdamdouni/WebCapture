# Pathologies of Redundant Code

_Captured: 2017-08-08 at 20:20 from [dzone.com](https://dzone.com/articles/pathologies-of-redundant-code?edition=310395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-23)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Remember Y2K? Before the turn of the millennium, computer storage was at such a premium that years were stored with only the last two digits so the year 1989 was stored as 89. This worked fine--up until the end of 1999, at which point the year returns to 00 which many programs would interpret as 1900 rather than 2000. Hundreds of millions of lines of code had already been written and in were in operation. All of it had to be scanned to make sure that dates were handled correctly. This turned out to be a massive effort but in the end, the critical systems that needed to be updated were updated and our civilization didn't descend into anarchy.

I knew people who worked on systems that were affected, but they had built their own date libraries years ago that already addressed these concerns. Their software was good to go, but that wasn't true in many of the banking programs I worked on back then.

I understand if it's the early 1970s and memory is at a premium so you want to store dates as efficiently as possible under certain conditions. Looking at the timeshare price sheets from back then, you could spend a thousand dollars a month renting one thousand bytes of data--only 1K! Today, Google gives you a terabyte for free. That was far more than existed in all the computers in the world back then.

Kind of puts things in perspective, doesn't it?

There is a lot of redundancy in code out there. We don't have much of a forum for sharing what we've learned. How many times have software developers "discovered" the same valuable techniques?

When I talk about redundancy in code, I'm not just referring to redundant behavior or redundant state. Redundancy can exist at many levels. We can have redundant relationships, redundant concepts, redundant construction, redundant conditionals, and so on. Each time a redundancy is introduced into the system it degrades it just a little bit. When this is done over and over again, a system becomes viscid and difficult to work with. It's hard to make changes because many areas of the code are impacted by a single change. This is a sure sign that you have redundancy and split functionality in your system.

Split functionality is even worse than redundancy. Instead of repeating a process in multiple places, split functionality puts different parts of the same process in different places, requiring that all the pieces be in sync in order for the process to work. To me, this is a particularly odoriferous code smell because the process breaks if you touch any piece of it.

The solution is to refactor and bring the pieces together. Organize the pieces by how they're varying. If several things vary together, organize them so they're located together. This makes code easier to read and understand and reduces the chance that things can get out of sync.

Software is like Russian nesting dolls, and good software has many layers. Each layer of abstraction provides the opportunity for an additional layer of indirection. But again, each abstraction must be represented in our system only once so that there is only one place to extend in the future.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
