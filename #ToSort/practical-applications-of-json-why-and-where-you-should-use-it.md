# Practical Applications of JSON: Why and Where You Should Use It

_Captured: 2018-07-01 at 21:18 from [dzone.com](https://dzone.com/articles/practical-applications-of-json-why-and-where-you-s?edition=383282&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-01)_

Databases are better when they can run themselves. CockroachDB is a SQL database that automates scaling and recovery. [Check it out here.](https://dzone.com/go?i=292425&u=https%3A%2F%2Fwww.cockroachlabs.com%2Fproduct%2Fcockroachdb%2F%3Futm_source%3Ddzone%26utm_medium%3Dtextad%26utm_campaign%3Dzs%26utm_content%3D1)

![](https://www.cockroachlabs.com/uploads/2018/06/JSON_Part2_WentingLi.jpg)

CockroachDB provides scale without sacrificing SQL functionality. It offers fully-distributed ACID transactions, zero-downtime schema changes, and support for secondary indexes and foreign keys.

But what about some of the additional benefits NoSQL databases provide such as the ability to use semi-structured data?

CockroachDB listened to our customers and realized that we needed to provide options for managing rapid development, data without a clear schema or whose schema you do not control, and impedance mismatches. That's why we are excited to support JSON in 2.0!

Previously, we've [shown you](https://www.cockroachlabs.com/blog/json-coming-to-cockroach/) how we implemented JSON and inverted indexes as well as a few examples. This article will explain when you might want to leverage these features.

## Why Use CockroachDB + JSONB?

### Rapid Development

Most successful new products (or new companies) use rapid prototyping to quickly adjust to frequently changing customer requirements. JSONB makes it easy to tweak your data model and prototype new features to iterate your way to customer success.

As your product grows, you'll need to strike a delicate balance between the need for data model updates and the need to minimize downtime. CockroachDB helps shift that balance back towards shipping product by adding rich support for JSON.

Imagine you launch a new blog platform that includes a table in which we use JSONB to store metadata about a user's blog post:

Within the metadata field, we might store something like:

We continue to add metadata fields that represent our best hypothesis about the kinds of information our users will want to store. After our initial launch, we checked in with a few of our users and learned that we have a large number of travel bloggers. These bloggers would like to store the location they wrote the blog post from. Since we are using JSON, we do not need to complete a schema change. Instead, we can insert new data fields:
    
    
    { "est-reading-time": "15m", "topics": ["consensus algorithms", "research"], "writing-location": "Manhattan" }

We are now able to quickly modify our application as we learn more about our users.

### Data Without a Clear Schema or Whose Schema You Do Not Control

Many applications cannot be modeled ahead of time (e.g., game elements, inventory items). These models are frequently stored as opaque bytes that can be difficult to update. Without JSONB, any data model changes would result in the need for individual data to be updated, extracted, modified, and stored back within a transaction.

Imagine a table `events` which stores system-wide events with the caveat that not every event has the same metadata associated with it. For example, if a user likes a post, we have to store different information than if, say, some group appoints a new administrator. Having JSONB columns available lets us model this scenario without resorting to a complex table structure with many foreign keys or redundant columns.
    
    
    CREATE TABLE events ( id UUID DEFAULT uuid_v4()::UUID, ts TIMESTAMP DEFAULT now(), data JSONB, INDEX (ts) );

Now inserting data is as simple as:

We do not need to do any schema changes to record new event types. Instead, we can insert the new data from our application and everything will automatically be stored correctly. This allows us to run interesting queries such as, for example, the most recent 10 "liked post" events:

Without inverted indexes, the above query would be very slow. For more information on how inverted indices work please consult [Be Flexible & Consistent: JSON Comes to CockroachDB](https://www.cockroachlabs.com/blog/json-coming-to-cockroach/).

### Impedance Mismatch

Many developers don't like modeling the world in a fully normalized way and want databases that can more intuitively map to the object-oriented programming languages powering their applications.

Both startups and enterprises need a method for storing increasingly large amounts of unstructured data such as storing sensor data.

Or say I want don't want complex data at all -- I just want a plain old document store with no restrictions at all on what I put in it, but I still want all the transactional guarantees provided by CockroachDB. Let's say that we require all of our documents to have an id field. We can make a simple document store like this:

Now, we can insert JSON documents and they will be appropriately indexed:

Since we added an inverted index on the `data` column, CockroachDB will add an index entry for every path through the JSON tree of every inserted value. This makes it efficient to look up containment relationships in JSON data, because it means that you can do a single point lookup into the inverted index to find out whether there's a match.

## Why Not Use a NoSQL Database?

NoSQL databases have garnered a large amount of public support and press about their easy to setup capabilities. Things like the "MEAN stack" became not just a cleverly marketed name but almost a requirement to prove your developer credentials.

Given the press around these databases, you might be asking yourself, why don't I just use a NoSQL database? Aren't they designed to take advantage of semi-structured data? Whether you are an early-stage startup or a fully vetted enterprise, you might be tempted to use NoSQL for their promised scale and simplicity. However, this could cost your business money. Most NoSQL databases fail to offer performant, general ACID transactions (e.g. Serializable isolation).

We believe that businesses have not placed enough weight upon correctness when making these decisions. In [Real Transactions are Serializable](https://www.cockroachlabs.com/blog/acid-rain/), we explained [recent research at Stanford](http://www.bailis.org/papers/acidrain-sigmod2017.pdf) that explored the degree to which weak isolation leads to real-world bugs in 12 eCommerce applications. In five of the tested applications, adding an item to your cart while checking out in another browser tab could result in the item being added to the order for free. NoSQL databases cannot even maintain weak isolation levels as they often fail to administer transactions correctly, a simpler construct than isolation levels.

Weak isolation doesn't just leave your application vulnerable to attack, it might also prevent you from answering fundamental questions about your business such as what is my revenue?

Luckily for you, this doesn't have to be true for your business. CockroachDB provides you with easy to use JSON with the same ACID transactions and serializable isolation levels you have come to expect from a world-class SQL database. Now you can have your cake and eat it too.

## Final Thoughts

CockroachDB provides the flexibility of JSON with strict guarantees of ACID transactions and serializable isolation. We are excited to provide you with the tools to make your company successful no matter what your combination of structured or semi-structured data turns out to be.

Databases should be easy to deploy, easy to use, and easy to scale. If you agree, you should check out CockroachDB, a scalable SQL database built for businesses of every size. [Check it out here.](https://dzone.com/go?i=292426&u=https%3A%2F%2Fwww.cockroachlabs.com%2Fproduct%2Fcockroachdb%2F%3Futm_source%3Ddzone%26utm_medium%3Dtextad%26utm_campaign%3Dzs%26utm_content%3D2)
