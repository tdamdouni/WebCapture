# Why All Your Data Should Be Raw

_Captured: 2017-09-16 at 22:20 from [dzone.com](https://dzone.com/articles/why-all-your-data-should-be-raw?edition=326497&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-16)_

See how the [beta release of Kubernetes on DC/OS 1.10](https://dzone.com/go?i=246334&u=https%3A%2F%2Fmesosphere.com%2Fblog%2Fkubernetes-dcos%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_campaign%3Ddcos_1-10%26utm_content%3Dpre) delivers the most robust platform for building & operating data-intensive, containerized apps. [Register now for tech preview.](https://dzone.com/go?i=246334&u=https%3A%2F%2Fevent.on24.com%2Fwcc%2Fr%2F1497867%2FF201F8CC4BE7EC6F4188C1AD40361214%3Fpartnerref%3Ddzcloud)

Your company generates a ton of data -- so much that it's essential to pare it down and only store the most relevant stats, right?

Well, it was 1975 when data warehouses were developed. At that time, a gigabyte of storage cost $200,000. But today? About 2 cents.

With this low storage cost, companies can stop worrying about compression and start worrying about making sure they can fully understand their data. Heavily "cooking" (processing) data may have been necessary a few decades ago, but now, its few benefits are far outweighed by the advantages of keeping that data raw.

## What Is Cooked Data?

"Cooked" data is data that has been taken from its raw format and processed, reorganized, or compressed. Traditionally, companies heavily cook their data in order to optimize storage space and query times. Three major ways to cook data are:

  1. **Fitting data warehouses with compression schemas**. One common schema is the star schema, which compresses data by taking information from an event and storing it in different dimension tables.![Star Schema ](https://www.interana.com/wp-content/uploads/2017/08/Star-Schema.png)

When an event, such as a click, occurs, information like the timestamp and user ID is collected. In a star schema, this information is split up into pieces and stored in dimension tables.

  2. **Fitting tables with indices**. Schemas are usually paired with indices, like [bitmaps](https://docs.microsoft.com/en-us/dotnet/framework/winforms/advanced/types-of-bitmaps) and [B-trees](http://www.cs.cornell.edu/courses/cs3110/2011sp/recitations/rec24-B-trees/B-trees.htm), so information can be found again quickly.
  3. **Only storing aggregates or subsets of the data**. Companies may choose to store precomputed aggregates, like averages, or just pick a few dimensions of the data to store in an [OLAP cube](http://olap.com/learn-bi-olap/olap-bi-definitions/olap-cube/), instead of keeping the raw data.

But these methods were created because they allowed the data to fit on a machine and allowed people to answer queries quickly -- not because they actually made sense. Subtle bugs, like an email automator pulling information from the wrong table, are exceedingly difficult to find when data is processed like this.

And again, the motivation behind cooking data no longer exists as storage prices have dropped.

## Better Understand Your Data by Keeping It Raw

The Sushi Principle says that raw data is better than cooked data because it keeps your data analysis fast, secure, and easily comprehendible. There are three steps you need to take to keep your data raw.

![Sushi Principle Diagram](https://www.interana.com/wp-content/uploads/2017/08/Sushi-Principle-Diagram.png)

> _1. Use a Simple, Well-Tested Pipeline_

When your pipeline already has to read every line of your data, it's tempting to make it perform some fancy transformations. But you should steer clear of these add-ons so that you:

  * **Avoid flawed calculations**. If you have thousands of machines running your pipeline in real-time, sure, it's easy to collect your data -- but not so easy to tell if those machines are performing the right calculations.
  * **Won't limit yourself to the aggregates you decided on in the past**. If you're performing actions on your data as it streams by, you only get one shot. If you change your mind about what you want to calculate, you can only get those new stats going forward -- your old data is already set in stone.
  * **Won't break the pipeline**. If you start doing fancy stuff on the pipeline, you're eventually going to break it. So you may have a great idea for a new calculation, but if you implement it, you're putting the hundreds of other calculations used by your coworkers in jeopardy. When a pipeline breaks down, you may _never_ get that data.

Of course, there are a few circumstances where you will need business logic in your pipeline. Regulations may require you to purge old user accounts and drop IP addresses. But every time you think about pushing a piece of business logic into your pipeline, you need to consider the risks. We're all still relatively bad at writing software; every complicated bit you add increases your chances of an error. And since storage is so much cheaper now, you have every incentive to just perform those calculations later.

### 2\. Keep All of Your Original Data

Once you've gone through the trouble of collecting all your data, you shouldn't toss out portions of it. With data storage costs so low, there's no reason _not_ to keep all of your data -- but a bunch of reasons _to _do so:

  * **You can easily trace the lineage of any statistic**. Imagine trying to figure out exactly how your DAU was calculated. If your stored data is in the same format that it was generated in, you can just ask the developer of whatever service you're using to generate data what they meant. If you have heavily processed data, it's harder to backtrack through all the transformations that were done to find the original data.
  * **You can perform any query you want**. The beauty of data is in how it can lead you to further questions. If the number of users subscribing through email is shockingly low, you're going to want to look into the attributes of users who do actually signup through that channel. You don't lose any detail when you have all your data on hand, which means you can iterate on your questions at any time. If you've pared down your data to an OLAP cube, you can only measure already defined dimensions -- everything else is lost.
![Interana Query Builder](https://www.interana.com/wp-content/uploads/2017/08/Interana-Query-Builder.png)

  * **You don't have to waste time deciding what stats you want**. If you decide to precompute stats, you're going to need to spend a whole lot of time planning out what those will be -- and even that's no guarantee that you'll have everything you need.

Keeping your original data reduces your unnecessary work so that you can get to parts that actually add value. It takes away the need for extensive prior planning and spending time figuring out where your stats came from so that more time can be spent on fully exploring your data.

### 3\. Summarize and Sample at Query Time

You may be tempted to summarize and sample your data early in the pipeline. The thinking goes, I'm going to have to do these things no matter what, why not shrink my data and make it easier to process? But sampling and summarizing early on can harm the accuracy of your data. It's much less risky to do those at query time:

  * **You can ensure that your summary statistics aren't skewed**. If you calculate the average number of edits a Wikipedia user makes per week, that figure is going to be outrageously high unless you exclude bots. (Check that out yourself with our [demo](https://www.interana.com/try-demo/?ref=blog).) While this may seem like a mistake you'd never make, little things slip through the cracks all the time.
  * **You can sample once you know who's interesting**. You can't simply keep every 100th event that's logged -- that doesn't give you a picture of how users, accounts, and devices are behaving. You need to [sample by actor, not event](https://www.interana.com/blog/event-sampling-done-right/). But you won't know which actors will be interesting to look at before you've started coming up with queries. And the types of users you want to look at will change between queries.
![Sampling By Actor](https://www.interana.com/wp-content/uploads/2017/08/Sampling-By-Actor.jpg)

  * **You'll get statistically significant results**. Much of the time, you're going to want to look into the behavior of small segments of your user population. But if you sample before query time, you may not have enough data on that small population to get statistically significant answers to your queries.

Yes, you will likely need to sample your data at some point to get answers to your queries quickly. But making that point at query time will ensure that you have the representative sample you need for every query.

## Do Less to Your Data and Do More With it

Data is necessary to grow any business -- so stop wasting it.

We believe data works best when you can iterate queries continuously instead of having to craft the perfect idea first; if you throw business logic into your pipeline, you lose this ability. By keeping your data raw, you can ask any query you want without having to plan for it in advance.

[New Mesosphere DC/OS 1.10](https://dzone.com/go?i=246335&u=https%3A%2F%2Fmesosphere.com%2Fblog%2Fdcos-1_10-kubernetes%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_campaign%3Ddcos_1-10%26utm_content%3Dpost): Production-proven reliability, security & scalability for fast-data, modern apps. [Register now for a live demo.](https://dzone.com/go?i=246335&u=https%3A%2F%2Fevent.on24.com%2Fwcc%2Fr%2F1497865%2F8D4FA6AADBB00B9C9704C90F1DA08516%3Fpartnerref%3Ddzcloud)
