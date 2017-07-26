# The Cache Aside Pattern

_Captured: 2017-04-15 at 18:15 from [dzone.com](https://dzone.com/articles/cache-aside-pattern?oid=twitter&utm_content=buffer772ba&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

The Cache Aside pattern, if used correctly, can improve the performance and data consistency between your data store and the cache. This pattern can be used for read and update operations of data to and from the data store.

## **Read Operations**

For read operations, your cache is checked first for the availability of data using a key. If the data is present, then the read call returns the data from the cache and completes the operation. In a case where data is not present in the cache, a round trip is made to the underlying data store to fetch the data, and a cache entry is created against a key before returning the response. This newly created cache entry will make subsequent read operations for the same data fetched from the cache, thus cutting down on the response time and increasing throughput.

![Image: 1.a](https://dzone.com/storage/temp/4819926-capture.png)

> _Image: 1.a_

In Spring, you can implement it as described below, where when `getRecordForSearch` is called, it will be fetched automatically from the cache if it is available (it will not hit the method code at all). Otherwise, it will be retrieved from the data store.

## Data Update

If the interfacing application can update the data in the data store and it is present in the cache, then the cache has to reflect the update as well. This will ensure the data consistency and performance for the data retrieval. Two strategies can be utilized, depending on the requirements.

### Cache Eviction on Data Updates

In this case, when a method to update the data in the data store is called, it also invalidates the cache entry using the key. In this approach, the cache entry gets loaded only when it is re-requested after the update. In Spring, this can be done as follows:

### Cache Updates on Data Updates

Cache entries can also be updated if and when the data is updated in the data store to get faster data retrieval and consistency in one shot. In Spring, this can be achieved by doing as follows:

Depending on the need and type of data, different cache loading strategies can be adopted.

  * **Load data as you go**: If and when data is needed, it is loaded into the cache. The first request fetches it from the data store, but the subsequent requests get the data from the cache.

  * **Preload cache**: This strategy is best for data loaded with an application's startup, reference data such as country list, currency, important dates, etc. This is great for data that does not change very often.

Share your comments if you have any other caching patterns that you have used and found useful.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
