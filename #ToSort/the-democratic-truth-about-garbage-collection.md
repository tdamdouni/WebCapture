# The Democratic Truth About Garbage Collection

_Captured: 2017-03-22 at 00:46 from [dzone.com](https://dzone.com/articles/the-democratic-truth-about-garbage-collection?oid=twitter&utm_content=buffer04c93&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Last week, I delivered a webinar entitled _[The Future of Garbage Collection in Java](https://www.azul.com/presentation/azul-systems-webinar-future-garbage-collection-java/)_. The premise of this session was to look at how things will change from a GC perspective in JDK 9 and then look a little further into the future at what research is being conducted in this area (specifically project Shenandoah).

Having talked about some of the basics of GC and the way GC works today in the OpenJDK (parallel, CMS and G1 collectors), I ran a poll to see how much of an impact GC has on the applications they develop and deploy. The results were interesting, but not terribly surprising.

Below are two charts showing the results from the webinar for Europe and then the same one delivered later in the day for North America.

![Image title](https://dzone.com/storage/temp/4681321-screen-shot-2017-03-17-at-14945-pm.png)

Looking at the results, very few people see GC as no problem at all -- 12% in Europe, 17% in America. For both regions, the largest group was those who saw some impact from GC but were able to change the JVM parameters to make the pauses acceptable. Figuring out which settings to change and what to set their values to is something that takes time (and therefore has a cost associated with it, something people often overlook).

For Europe, a majority of people fell into a category where they either had to expend significant time and effort to tune the JVM or couldn't even manage to meet their SLAs. In America, this group was a bit smaller but still represented nearly a third of those who responded. Again, this equates to a lot of skilled people working on a problem with a clear cost associated with it. Their time would be much better spent on solving the problems of their business rather than how the infrastructure works.

Although this is a small sample size, I would not be surprised to find that this was a pretty accurate reflection of Java users as a whole.
