# Scalability Cheatsheet

_Captured: 2017-06-11 at 02:06 from [dzone.com](https://dzone.com/articles/scalability-and-performance-part-2?edition=304168&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-10)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

Before reading, be sure to check out [my previous article in scalability and performance in Scala](https://dzone.com/articles/scalability-and-performance).

## **1\. Simplify**

Simplify your code and design to gain an understanding of scalable systems. Your life will be scalable -- the more complex it is, the less it's possible to scale it out and the more complex your life is. Of course, if it's not possible to simplify, do not. However, many times, we think it's _not_ possible to simplify while it actually _is _possible, so do yourself a favor and put some effort into this.

## 2.** Duplicate Data**

Create multiple read-only databases or clones for your data and thus scale your reads. You can then use a read query to read multiple copies of your data, thus putting less strain on your servers.

## 3\. **Split on Business**

Your data, like microservices, are also at the database level -- not only in service level. There are different roles and different databases. Think about having two or more databases, or just splitting your data. You could still have a single database; just make sure you split things.

## **4\. Split on the Same**

If you have multiple customers split on a customer ID, you can put smaller customers on the same shard and larger customers on a different one. Be sure you split into categories that make sense for an even split. For example, don't split on location; if 80% of your customers are from a certain place, your split won't be okay.

## 5\. Having Three** Data Centers Is Even Better**

If you have only two data centers, you need 200% capacity if one goes down in order to serve 100% capacity. If you have three data centers, you need a total of 150%, so two of them would make 100% capacity if one of them goes down.

## 6\. **Remember Storage Alternatives**

Remember that you have different types of file storage such as ceph (don't forget the file system), NoSQL, wide column storage such as Cassandra, and relational. Column storage usually provides automatic row sharding and asynchronous replication with eventual consistency, while column splits require more manual intervention.

## 7\. **Consistency **

If you increase consistency, for example, on NoSQL, then operations such as `getSomething` would require you to contact all nodes to make sure they return the most recent, greatest version.

## 8\. **Firewalls Are Like Locks**

You lock your main door but you don't lock internal doors, right? A credit card request is through a lock, not an image request. Don't overuse your firewall; it's complex enough without it.

## 9\. Do You R**eally Need a Transaction?**

When you pass money from one customer to another, do you really need a transaction? Consider all options. Usually, when you start considering event sourcing, you see you that can compromise without transactions.

## 10\. **Don't Read Validate Your Write**

Have you just wrote something to disk/cache/database? Don't reread it in order to validate it; your servers have more useful things to do.

## **References**

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).
