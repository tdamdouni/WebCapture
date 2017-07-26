# The Previously Sorted Algorithm

_Captured: 2017-03-20 at 14:38 from [dzone.com](https://dzone.com/articles/the-previously-sorted-algorithm?edition=285896&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-19)_

The performance team has noticed that a particular scenario (importing a large number of documents) is spending a lot of time sorting data. The finger was pointed directly at this guy:

![image](https://ayende.com/blog/Images/Open-Live-Writer/Sorting-Not-in-our-school_679/image_thumb_1.png)

That's 11.3% of the total operation time, in an area that is already extremely optimized. Before I go forward and explain what we did, I need to explain what is going on here. Consider the following JSON document (taken from the JSON value in Wikipedia):

RavenDB has progressed far beyond storing JSON as text. I have a [seven-part series](https://ayende.com/blog/posts/series/172705/the-importance-of-a-data-format) of posts that talk about how we store things. But the basic idea is that instead of storing the data as text, we store it in a well-crafted binary format that is optimized for reading parts of the document without having to do any work. In other words, if I wanted to what is the type of the second phone number in this document, I wouldn't have to parse it all. I would go to the root document table and find the 'phoneNumbers' positions, just to that, and then just to the second value, and then find the 'type' entry in that object table, and then I'll have the value.

Those searches inside the table require us to have the property names sorted so we can do a binary search on them. Binary search is really good, giving us an efficiency of O(logN). But we do better actually. In fact, we do a _lot _better than that with amortized cost of O(1). How do we do that? We do that by utilizing a very interesting aspect. We keep seeing the same (or very similar) documents, so we can learn from previous searches and start the search for a property name in the position we have previously found it. This tends to have high probability of success and, at most, adds a single operation, so it is a very successful optimization.

But in order to do that, we need to make sure that the data is sorted. And as you can see in the profiler trace above, this is decidedly non-trivial. In fact, we pay over 11% (!) of our JSON parsing time just in sorting those tables. That is crazy. We considered switching to a tailored sort algorithm, but this part was already heavily optimized. Instead of sorting by strings, we are pre-sorting all seen values, then sort on their previously calculated order. That means that we don't need to do a lot of string comparisons, but this still killed us.

Then I remembered that we aren't trying to optimize a single run. Instead, we are trying to optimize the entire process. And given that observation, we can utilize that knowledge. The basic idea is simple: We assume that most of the time, we are going to see similar data, so we are going to cache the _sort order_. Next time we get an object to sort, we can check if we have sorted this sequence of properties before, and just use that sort. This translates the operation into going over the list of properties a few times, with very little actual code and behavior. The details are a bit gnarly, of course, because we have a lot of stuff that we need to deal with (anything from duplicate properties to dynamic changes in property ids between documents to deciding how much we should cache and how we should do it), but we got it working.

The result is beautiful:

![image](https://ayende.com/blog/Images/Open-Live-Writer/Sorting-Not-in-our-school_679/image_thumb_2.png)

> _It is even more impressive if you look at the performance comparison directly:_

![image](https://ayende.com/blog/Images/Open-Live-Writer/Sorting-Not-in-our-school_679/image_thumb_3.png)

Total runtime dropped by close to 3 seconds, and we saved our 11% back with interest. Overall we are 13% faster.

This is us testing on production data, which has a high degree of real-world issues. Because the data has been through multiple releases and mutations.

But the key here is that this change actually improved all of RavenDB's JSON reading capabilities. As you might imagine with a JSON Document DB, we tend to do quite a lot of JSON parsing, and all of _that_ just got an amazing performance boost.
