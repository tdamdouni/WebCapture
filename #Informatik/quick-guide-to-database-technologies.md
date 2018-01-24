# Quick Guide to Database Technologies

_Captured: 2018-01-20 at 09:57 from [dzone.com](https://dzone.com/articles/quick-guide-to-database-technologies?edition=355109&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-19)_

Running out of memory? [Learn how Redis Enterprise enables large dataset analysis](https://dzone.com/go?i=252321&u=https%3A%2F%2Fredislabs.com%2Flanding%2Fredis-enterprise-flash%2F%3Futm_source%3Ddzone%26utm_medium%3Dtext%252520ad) with the highest throughput and lowest latency while reducing costs over 75%!

Database technology has seen rapid developments in the past two decades. Online analytical processing (OLAP), which gained prominence in the 1990s, gradually lost altitude in favor of in-memory databases at the start of the 21st century.

However, the requirements of modern business intelligence have set a challenge that in-memory databases will have a very difficult time responding to. This, in turn, has brought on the next generation of databases and querying: in-chip analytics. This newly developed technology makes use of the CPU, RAM, and disk storage in innovative ways in order to tackle the complexity and size of datasets that current BI software is forced to handle in order to provide effective insights to end users at a reasonable timeframe.

## What Are Database Technologies?

Database technologies take information and store, organize, and process it in a way that enables users to easily and intuitively go back and find details they are searching for. Database technologies come in all shapes and sizes, from complex to simple and large to small. It's important to think about how the database technology you choose will be able to grow as the size of your data grows, as well as how it will interact with any software you use to query your data. Let's begin to break it down.

## OLAP Cubes: Overview

> OLAP technology provided a great basis for business intelligence 20 years ago but suffers from several limitations which make it a less than ideal fit for most modern BI projects. It allows users to receive quick answers to specific pre-defined queries but is resource intensive and problematic when it comes to larger data sets and ad-hoc querying. 

An [OLAP](https://www.sisense.com/glossary/olap/) database converts table based datasets into multi-dimensional arrays called _cubes_ in order to optimize querying and data retrieval. Users can then access specific dimensions of the data for analysis purposes.

To answer queries, an OLAP cube typically includes roll-up cells that contain aggregated data, according to certain parameters -- such as sales over time or item sales by location. These aggregations are pre-calculated when the system is "at rest" (i.e. not being used by end-users).

Thus, once a query is made, the answer is already within the data cube and retrieved instantaneously.

### The Problem

OLAP cubes have their drawbacks, the main ones being:

  * **Resource-intensive data storage and management**: Each additional query requires a new dimension to be added to the cube, which means duplicating the entire cube in terms of data storage.
  * **It takes a long time to produce each new build when new data is added**: Aggregating data requires the CPU to process every cell of the database.
  * **Need to pre-define queries**: New queries, the data is not pre-calculated and requires additional dimensions to be added -- a lengthy process.

## In-Memory Databases

> In-memory technology (i.e. loading the entire database into RAM and from there transferring it to the CPU to perform calculations) has become a leading solution for business intelligence, as it provides users with the ability to receive fast answers to their queries, without the need for lengthy builds and pre-calculations; but the size and complexity of modern data is forcing in-memory databases to face their limitations. 

Generally speaking, a computer has two types of data storage mechanisms: disk (often called a hard disk) and RAM (random access memory).

The important differences between them are outlined in the following table:

![](https://cdn.sisense.com/wp-content/uploads/Disk-vs-RAM-storage.png)

Most modern computers have 15-100 times more available disk storage than they do RAM.

However, reading data from disk is much slower than reading the same data from RAM. This is one of the reasons why 1GB of RAM costs approximately 320 times that of 1GB of disk space.

In-memory technology aims to address performance issues by pre-loading the entire database into RAM and loading data from RAM to the CPU to perform calculations and data retrieval.

### The Problem

  * **Scalability**: When datasets are simple and small, in-memory technology enables speedy development compared to other solutions. The challenge it continues to face is that RAM -- when used to store and analyze raw business data -- tends to run out quickly and unexpectedly.
  * **RAM is expensive**: The fact of the matter is, datasets are getting bigger and bigger, with companies generating and using more information than ever. This exponential growth in the size of data has not been mirrored by a similar reduction in RAM prices; while it's indeed cheaper than it was 15 years ago, it's still relatively expensive storage that cannot be scaled indefinitely without procuring significant costs.

And so, at this point in time, it seems that in-memory technology might just have hit its glass ceiling and can no longer promise reasonable performance, considering the amounts and complexity of the data that is currently being gathered aggregated and analyzed by modern businesses.

## ElastiCubes and In-Chip Analytics

> In-chip technology is the latest development in database technology. It combines the flexibility of in-memory-based querying with the speed and robustness of OLAP cubes, without the hardware costs and difficult implementation of traditional solutions. Although only recently developed and released, in-chip is quickly gaining popularity due to its increased performance and ability to tackle complex and large datasets. 

ElastiCube is a unique form of a database developed by Sisense, the result of thoroughly analyzing the strengths and weaknesses of both OLAP and in-memory technologies. Its name comes from the database's unique ability to stretch beyond the hard limitations imposed by older technologies. In-chip is the latest generation of in-memory technology for business analytics and sets itself apart by being fast as well as scalable.

It uses a disk-based [columnar database](https://www.sisense.com/glossary/columnar-database/) for storage to provide fast disk reads and is able to load data from disk to RAM (and vice versa) when needed. The queries themselves are processed entirely in-memory without any disk-reads throughout.

Most importantly, there is only a subset of the data physically stored in RAM at any given time, leaving more space for other operations to take place in parallel -- in other words, RAM limitations are less of an issue than with previous in-memory technologies since there is no need to keep the entire data in RAM on a permanent basis.

This is achieved via advanced compression as well as identification of the parts of the dataset which are not being used on a regular basis and can be left "at rest" (typically, this is around 80% of the data that businesses collect).

Further optimization is done by employing a unique way of handling joins. Instead of joining tables, in-chip uses columnar algebra to merge between fields. Thus, the join operation can be processed entirely in the CPU cache.

All of these factors combined produce unparalleled performance rates on commodity hardware -- even when it comes to huge, complex datasets that would previously have required massive hardware upgrades to even consider handling.

## Summary: The Future of Databases?

As we have seen, both OLAP and in-memory technology suffer from scalability issues, and there are significant doubts as to their ability to provide a reasonable solution for the requirements of 21st-century business intelligence, in terms of data size, complexity, and cost to implement.

In-chip technology is currently the most advanced way to store and query data in rapidly changing business environments and is expected to be adopted by more and more companies in coming years.

Running out of memory? Never run out of memory with[ Redis Enterprise database](https://dzone.com/go?i=252322&u=https%3A%2F%2Fredislabs.com%2Flanding%2Fredis-enterprise-flash%2F%3Futm_source%3Ddzone%26utm_medium%3Dtext%252520ad). [Start your free trial today](https://dzone.com/go?i=252322&u=https%3A%2F%2Fredislabs.com%2Flanding%2Fredis-enterprise-flash%2F%3Futm_source%3Ddzone%26utm_medium%3Dtext%252520ad).
