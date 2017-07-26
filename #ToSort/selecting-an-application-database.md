# Selecting an Application Database

_Captured: 2017-06-17 at 02:06 from [dzone.com](https://dzone.com/articles/selecting-an-application-database?edition=305102&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-16)_

What if you could learn how to use [MongoDB](https://dzone.com/go?i=219244&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) directly from the experts, on your schedule, for free? We've put together the ultimate guide for learning [MongoDB](https://dzone.com/go?i=219244&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad). [Sign up](https://dzone.com/go?i=219244&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) and you'll receive instructions for how to get started!

Selecting your data storage technology is one of the most important technical decisions that has to be made. Wrongly selected data storage can prevent you from being able to meet software requirements. Your database choice requires thoughtful design and research investment and should be done with maximum responsibility. Here, I want to share my knowledge and thoughts about how to choose the right database for your task.

## Understand the Difficulty of the Problem

While some applications need to store petabytes and process them in sub-milliseconds, other applications might need simple storage for the data that fits in the memory of your laptop and can wait seconds to be available. Not all applications are equally tough, and technology choice is not equally important. Mission-critical systems require thoughtful design -- feature comparison, prototype implementation, performance testing, etc. -- but not every system needs these steps. For simple tasks, you might use already adopted technologies. Invest your time appropriately to the value of the problem.

## Gather Requirements

Everything in software engineering starts from your requirements. Try to understand your data model and the ways that your application will interact with it. Try to estimate the size of your data. Get throughput and latency requirements. Understand which [consistency guarantees](https://aphyr.com/posts/313-strong-consistency-models) are required and whether [linearizability](https://aphyr.com/posts/313-strong-consistency-models) is required.

## Consider SQL by Default

Today, SQL vs. NoSQL is not about SQL. Traditional SQL databases like PostgreSQL or MySQL already support unstructured document store in JSON or other formats while NoSQL databases have evolved query syntax to reach capabilities close to SQL. The main difference remains in the fact that SQL databases are built by default for non-sharded setup with a single write instance and few read replicas. This is how full ACID can be met without heavy 2PC-like protocols. Consider anything other than "30-years-old legacy" SQL databases only if SQL cannot meet requirements in terms of the size of data, throughput, latency, or query capabilities. With SQL, you can query almost everything and make data durable and consistent at any time. You are on the safe side if requirements will change or if you realize that you made wrong assumptions on your data model.

## Anything Better Comes With a Cost

To do anything better than a SQL database, we have to sacrifice something. Usually, this includes consistency, durability, and ways that you can access and manipulate your data. Need to write more data faster? Don't write immediately to disk or don't update indexes immediately. Writes cannot be handled by a single instance? Remove consistency between documents and spread them across the cluster. Want to have faster access via keys? Change how data is stored and remove some query capabilities. These are rules of the game caused by real-world hardware limitations. Every characteristic of NoSQL database that outperforms SQL comes with sacrificing some SQL database capabilities. There is no free lunch here.

## The Right Question Contains the Answer

Assuming the problem is big enough or specific enough, by classifying the problem, we find and answer already. Need to store key/value data? Look at key/value stores. Write intensive workload? Look at write optimized solutions. Want to store relationships? Look at graph databases. But only if your problem is big enough or specific enough.

## CAP Classification Is Not That Helpful

While CAP theorem is absolutely valid in classifying databases into CP/AP, CA is usually not. Most NoSQL databases can be tuned to the level of consistency that is required. Focus rather on understanding database architecture and which problems and use-cases it typically solves. Find the experiences of others.

## Don't Trust Marketing to the Full Extent

Every database according to white papers is the best, fastest, and the reliable in the world. No one will write limitations on the main page or in whitepapers. They are usually hidden in documentation or even hidden until they become a surprise to many people. _[Jepsens_](https://aphyr.com/tags/Jepsen) by Kyle Kingsbury is a good example of exploring database limitations in hands-on tests. Measure -- don't trust. Benchmarks are tricky business. You can find a benchmark where database X outperforms database Y and another one with database Y outperforming X. Only your setup and data can give the confident answer.

## Understand Limitations of Free Editions

I can't name any single popular database behind which there is no company making money. Even those technologies born and open sourced at companies like Facebook and Google have consultancies and companies offering commercial editions. Even more tricky are the databases born because of the NoSQL trend. They are developed by companies making money on these technologies, which is fair enough. That's why a free edition might be very constrained, forcing you to pay for a commercial one. Understand the limitations of the selected edition. Frequently, they include security, replication, monitoring, and bug fixes, and are vital to many systems. Do this early in your project and align this with your budget.

## Understand Limitations of Hosted Options

There are many databases provided as a service, such as [Heroku Add-ons](https://elements.heroku.com/addons#data-stores). You don't have to deal with infrastructure, replication setup, and backups. Everything is there to start implementing the application. Usually, hosted databases are more expensive than just bare-metal machines with which you can set up any database with a license. But the price difference is not the only cost. Database maintenance as a service prevents you from being able to use some administrative capabilities directly. This means you might not be able to create multiple users with different permissions, install extensions, or even change durability/consistency level. What you _will_ get for sure is database communication protocol compliance -- but not all the features. Evaluate these limitations carefully.

## Is It the Right Time to Play?

Experience matters. Knowledge of the team matters. Old and known is better than new and unknown. Heterogeneity brings complexity. Distributed systems are tough. Building databases is tough. Old and tested is better than new and fancy. Trying new technologies is always a risk. Trying multiple new technologies at the same time is a big risk. Not every task and circumstance allow taking this risk. Understand whether you can allow yourself to try a new technology that should be better than the already used and adopted one. But not every problem is a nail you can fix with a hammer. There is no "best" database. There might be the most suitable one for your problem.

What if you could learn how to use [MongoDB](https://dzone.com/go?i=219245&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) directly from the experts, on your schedule, for free? We've put together the ultimate guide for learning [MongoDB](https://dzone.com/go?i=219245&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad). [Sign up](https://dzone.com/go?i=219245&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) and you'll receive instructions for how to get started!
