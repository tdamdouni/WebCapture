# Hash Table (Stuff Formally Trained Programmers Know)

_Captured: 2018-07-14 at 14:24 from [dzone.com](https://dzone.com/articles/hash-table-stuff-formally-trained-programmers-know?edition=385238&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-07-14)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

This post is one in a series of stuff formally trained programmers know - the rest of the series can be found [in the series index](https://www.sadev.co.za/content/stuff-formally-trained-programmers-know).

The hash table, like the tree, needs a key. That key is then converted into a number using a hash function which results in the position in the array that is the data structure. So when you need to lookup an item, you pass in the key, get the same hash value and that points to the same place in memory so you get an O(1) lookup performance.

This is better than a pure array, where you cannot do a lookup so you have to search through giving an O(n) performance and better than a tree which also needs a search, so it ends at O(log n).

A hash table would be implemented with an array, which means that inserting is O(1) -- unless the array is full then it is O(n), so this is a pretty good level of performance. An important note in comparing, O(1) when adding to the end of the array and O(1) with a hash table is that the hash table has additional computation so that while they have the same complexity it is still slower to use a hash table; this is why big O notation is useful for understanding it has limits on how it can help us choose what to use.

A hash table, in concept, is easy, but in practice, it is another thing altogether. First, you need a hash algorithm that ends up giving a value inside the bounds of the array - this is often done using modulus. For example, if we get a value of 14213 but our array is only 8 in size we can do 14213 % 8 to get its position, 5.

This converting of numbers brings a new problem, collisions; namely, we are taking a large number of possible numbers and converting them to a smaller number, so what happens when we get, say, 85? It also has a modulus of 5! Two items can't live in the same location. There is no single solution to collisions, there are many.

One option uses linked lists in the items, so if there is a collision then you can store it at the same index and then you only have to search the, hopefully, very limited set in the collisions list. Others use offsets to shift collided items around the existing array. For this series though, a complete analysis of the options is beyond the scope.

## Implementations

.NET has [hashtable](https://msdn.microsoft.com/en-us/library/system.collections.hashtable.aspx) and [Dictionary](https://msdn.microsoft.com/en-us/library/system.collections.hashtable.aspx). Java comes with [Hashtable](https://docs.oracle.com/javase/7/docs/api/java/util/Hashtable.html) and Kotlin has [HashMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-hash-map/index.html).

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)

Opinions expressed by DZone contributors are their own.
