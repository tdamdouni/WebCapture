# To Index Data Is to Sort Data

_Captured: 2017-10-11 at 20:41 from [dzone.com](https://dzone.com/articles/to-index-data-is-to-sort-data?edition=329559&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-11)_

[Learn best practices](https://dzone.com/go?i=239229&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317) according to DataOps.[ Download the free O'Reilly eBook](https://dzone.com/go?i=239229&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317) on building a modern Big Data platform.

Indexing is a commonly used strategy among programmers. Without fully grasping the idea behind the technique, however, programmers are always eager to take advantage of it whenever they encounter a query performance problem, only to be disappointed by the result. By analyzing the principle of indexing, the article tries to show programmers the appropriate time to use an index and how to use it.

## **Basic Idea of Indexing**

The purpose of indexing is to quickly find the records where the value of a certain field is equivalent to a given value (finding the right person according to an ID card number, for instance). For a data set with a certain scale (_N_ rows), searching an eligible record using a full traversal needs _N_ comparisons. If the data set is sorted by the target field (called the key for an index), we can use the binary search by creating a binary tree. This way, the number of comparisons is _logN_ (base 2). For example, only 30 comparisons are needed for a data set with one billion rows (2^30 comparisons if one billion records are traversed), thereby causing a great performance increase. The key values could be duplicated (find people according to birthdays, for instance), or there is probably a query according to a certain range of key values (find people who were born in a certain period of time). In both scenarios, the number of comparisons is bigger than _logN_ but remains of the same order of magnitude.

**To index data is to sort data.**

Of course, we won't really _sort_ the original data set. Instead, we create an index, a smaller data set, that stores the key values of all records and the records' positions in the original data set in a table sorted by the key values. If more fields are specified for key-value searching, we can also create an index over each of these fields. For one original data set, multiple different indexes are allowed. But if the original data set is sorted and replicated each time when an index is created, the space consumption could be huge.

A database is designed to take data insertion and deletion into consideration when creating an index. An index with a simple sorting makes insertion and deletion a costly process. For this reason, a B-tree is used to facilitate the data update. A B-tree is a result of extending a binary tree into an n-ary tree, with data still sorted by key values. (We'll discuss how to create an index, which covers a lot of aspects, in another article; here, we only focus on how to use them.)

There is another method, hash indexing, which calculates the hash values of the key values in all records. These hash values are natural numbers falling into the range from 1 to _k_, and they can be used to locate records directly without a binary search. The hash method finds key values according to a specified exact value, not an interval, because the hash function isn't a monotonic function and doesn't show the original order of the key values anymore. Yet the method is sufficient in handling many scenarios (like finding a person by ID card number). At its heart, a hash index is also about sorting according to the hash values of the key values. The following discussion takes the ordinary indexing for example but the conclusion also applies to the hash index.

Regarding how the index works, it can't increase the full traversal performance. So, it's inappropriate to use an index to improve the performance of grouping and aggregation.

## **Single-Field Indexes**

With a deep understanding of the idea behind indexing, we know the right occasions to use an index and how to write the code properly.

  * **It is very effective with a condition on key values**, like finding the person whose ID card number is equivalent to the given value or finding people who were born in a certain period of time.
  * **Most of the time, it is ineffective if the condition is a function of the key values**. Other times, whether an index can be used depends on the degree of database optimization. Take a scenario where the index key is _Birthday_ but the condition is people who were born on a certain day of the week, for example. An ordinary index won't work because it isn't sorted by the days of a week. We need to create an index over the function of the key values. That type of index is supported by most databases. Another example is finding people who are in a certain age group with the index key as _Birthday_. We can't use an index directly, either. As there is a monotonic relationship between the age and the birthday, a properly optimized database may enable the use of the index, which, however, is rarely seen. Besides, phrase a query condition directly over the values of the index key rather than over their function or an expression.
  * **It is effective if a general search condition separated by `AND` puts the condition over key values at the outermost layer**, like finding people who were born on a certain date and whose names contain a certain character. The database will first filter out those who were born on this date using the index, and then find those whose names contain a given character. All modern commercial databases are capable of analyzing a conditional expression intelligently to find the part for which an index can be used to speed up the searching. But for a condition that finds people who were born on a certain date or whose names contain a certain character, the index becomes useless. Since only a traversal can be used for the second part of the condition, the database will skip the indexing to perform a traversal directly.

So, it would be better to write the condition over the key values at the outmost layer of a compound search condition separated by `AND`. Performance can only be enhanced when the index key can be used to narrow down the searching range.

## **Multi-Field Indexes **

Suppose we create indexes over all the fields involved in a searching condition. Will that lead to a stronger performance boost?

The answer is a disappointing _no_, according to the idea previously introduced. In most cases, only one index over a single field is useful.

There is a search condition `A=1 AND B=2` and two indexes created over field A and field B separately. First, index A is used to find records where the value of field A is 1; but as these records aren't ordered by field B, a traversal is still needed to find the records meeting the condition `B=2`. We'll face the same situation since the records filtered out with index B according to the condition `B=2` are not ordered by field A. A commercial database will assess the situation and choose an index whose filtered data set is smaller.

Both indexes might be useful if the search condition is `A=1 OR B=2`. A properly optimized database has the ability to use both indexes separately to filter the original data set according to `A=1 AND B=2` and then performing a union.

We can also build a multi-field index over both fields. The result set after filtering according to `A=1` is now also ordered by field B, and thus it can be further filtered using the index according to `B=2`. A database, if perfectly optimized, identifies `A=1 AND B=2` and `B=2 AND A=1` as the same condition, so the order of the different parts of a compound search condition is allowed to be different from the order of the index keys. It should be noted that for the situation discussed in the third case in the last section, it is preferable that a condition on the index key is written at the outermost layer.

Yet the double-field index over field A and field B doesn't work when being applied to `B=2` because an index ordered by both field A and field B doesn't necessarily ordered by field B. To find records according to `B=2`, the only choice is to perform a traversal. But a multi-field index tends to steer programmers wrong. In fact, a multi-field index over fields A, B, and C is valid for conditions including `A=?`, `A=? AND B=?`, and `A=? AND B=? AND C=?`, but it is invalid for conditions including `B=?, C=?, B=? AND C=?`. An additional index over field B or field C is needed.

Since a multi-field index over field A, field B, and field C is valid for conditions A, A/B and A/B/C, should we create as many index keys as possible? It seems we should according to its principle. With an index table getting bigger, however, the I/O cost will increase accordingly. So, the decision should come from a good assessment of a situation.

## **Index and Traversal**

Is a correctly created and properly used index a guarantee of a performance boost?

Not necessarily!

The purpose of using an index is getting records according to key values. In most cases, a relatively small number of records are expected to be retrieved from a huge data set. On those occasions, a suitable index, if used properly, will surely give a big boost to the retrieval performance. On other occasions where a lot of records may be retrieved through a conditional traversal, performance might or might not be improved -- it could even be worse.

Here is the reason.

As mentioned earlier, we create a separate index instead of sorting the original data set. Data retrieved based on the index is not continuously stored in the original data set -- it could even be totally disordered if the database isn't properly optimized. Retrieving a large amount of discontinuous data from the hard disk will be accompanied by the retrieval of a lot of irrelevant data. The data retrieval time shouldn't be calculated simply according to the amount of data to be retrieved.

More importantly, the performance increase brought by the use of an index is limited and isn't as much as expected. Retrieving data in a discontinuous way according to the index may cause duplicate data retrieval. For an HDD, it is most probable that a traversal is better than the index-based retrieval in performance due to a large number of time-consuming head jumps if the result set is very large. Usually, a commercial database will assess the cost before deciding the way to retrieve data. If any adverse conditions exist, the index-based data retrieval method will be abandoned. Generally, the performance is no worse than that of the traversal. But if the cost assessment is not as precise as expected, a wrong data retrieval method may result in a worse performance.

In general, the database data is stored in the order of insertion. If the order is in line with the order of the values of the index key, the data retrieved will be physically stored in a relatively continuous way. In this situation, the index-based filtering can bring a considerable performance increase, even if the retrieved amount of data is large.

Find the perfect platform for a scalable self-service model to manage Big Data workloads in the Cloud. [Download the free O'Reilly eBook to learn more](https://dzone.com/go?i=239230&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317).
