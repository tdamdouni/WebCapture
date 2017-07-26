# Database alternatives for Mobile (NoSQL ) A glance to Realm and Couchbase Lite

_Captured: 2015-06-12 at 23:20 from [medium.com](https://medium.com/p/c7ed425de6a1)_

NoSQL in a nutshell -NoSQL technology was pioneered by leading internet companies -- including Google, Facebook, Amazon, and LinkedIn -- to overcome the limitations of 40-year-old relational database technology (such as mysql and postgress) for use with modern web applications. Today, enterprises are adopting NoSQL for a growing number of uses cases, a choice that is driven by four interrelated megatrends: Big Users, Big Data, the Internet of Things, and Cloud Computing.

#### So why should I use NoSQL when developing mobile apps?

One of the main features of NoSQL is that it's scheme-less which means that we don't need to manage migrations, that allows you to update any models without deleting / adding values to your current data.

Another cool feature that mobile apps could benefit from is the ability to save a model that has relationship in place (Denormalization) . Let's say that we have two models User and Email, User has multiple emails . Every time we need a user we also need all his emails eargely and we don't need to run any query on the user's emails, we can store the user in a document and the user email as a list of documents within it (of course that using files could give you the same but you will need to write some boilerplate code for managing files for that and you won't be able to make queries on your items).

#### Here are two libs that implements NoSQL for Android which are the two leaders at the NoSQL domain in my opinion:

This is a light version of the well known Couchbase db, they reduced the size of the binary by taking only part of Couchbase db which they thought could be suitable for mobile. One of the main feature of CB db is the ability to make "Views" of the data. View -- is a kind of predefined query that is fetched with O(1). How it works -- when a new object is inserted to the db it passes through the predefined view filter functions, if it passed all of them it's added to the view. If you want to go all the way with this DB there is an option to sync it with Couchbase db on the server with no need to write any boilerplate code for that, this could be very useful depending on the data that you use in the app.

(The code snippets are in Android code but there are iOS equivalent syntax)

Creating the Couchbase lite db :

Saving a document :

Fetching a document :

Some Pro's and Con's:

Pros -- server sync capabilities, backed by Couchbase which is well known for it's server databases, [support revisions](http://developer.couchbase.com/mobile/develop/references/couchbase-lite/couchbase-lite/revision/index.html), scheme less and has views.

Cons -- don't have model mapper in Android (only in IOS) which means that you have to map your POJO's (Plain Old Java Object and for iOS guys object that has primitive members) by yourself , doesn't supports object relationships out of the box, [you have to implement them yourself](http://developer.couchbase.com/mobile/develop/guides/modeling/one-to-many/index.html) .
