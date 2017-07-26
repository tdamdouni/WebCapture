# I Deleted My MySQL Database

_Captured: 2017-07-13 at 11:06 from [dzone.com](https://dzone.com/articles/i-deleted-my-mysql-database?edition=308191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-12)_

Learn how to create flexible schemas in a relational database using [SQL for JSON.](https://dzone.com/go?i=226221&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017JSONPartIIWhitePaper_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dtext-ad%26utm_campaign%3Dtext-ad_json_dzone%26utm_content%3Dproduct)

I just deleted my primary MySQL database. Of course, I backed up everything, but it is the first time since 2011 I've cleaned up my entire database backend to the point where I could delete the entire instance (with confidence). I was motivated to do this mostly because I couldn't downsize the AWS RDS instance to a smaller instance due to a variety of constraints. The situation gave me the opportunity to clean house and to rethink my next moves.

![Image title](https://s3.amazonaws.com/kinlane-productions/101/amazon_aurora_thumb_person.png)

Instead of setting up a new MySQL instance, I went with [the new MySQL compatible Amazon Aurora](https://aws.amazon.com/rds/aurora/). I set up a smaller instance that was more affordable, and I was able to easily import the database backups I had made in my previous setup, but now I had a cleaner, more modern Amazon Aurora situation that, as Amazon claims "provides up to five times better performance than MySQL with the security, availability, and reliability of a commercial database at one-tenth the cost." Time will tell…

I like cleaning up my database and migrating to a new solution, even if the solution is still with the same provider. It helps me think through things and shed unnecessary databases, tables, and hopefully costs. Everywhere that I've worked and within all of the businesses I have owned, the database is always the hardest thing to manage and migrate. I want that to be a thing of the past. Now that I have things cleaned up, I'm going to keep my databases small and modular and use standardized solutions that top-tier providers support. This means I can migrate my data wherever I need to, and wherever it makes sense to my business.

Another thing that has also allowed me to migrate my data in this way is that I have offloaded a significant portion of the data I manage, which drives my public research to Google Sheets. This approach helps me simplify and modularize my data, again using a common tool (spreadsheet/CSV) in a way that I can easily collaborate with others and publish to Jekyll and GitHub using YAML. This shift in my world is all about helping me reduce the bulk on the backend of my business and making sure I spread out my business data, content, and algorithms across a variety of solutions, while making sure all the services I use have APIs that allow me to automate, orchestrate, and (of course) migrate my data whenever I need to.

Create flexible schemas using dynamic columns for semi-structured data. [Learn how](https://dzone.com/go?i=226222&u=http%3A%2F%2Fgo.mariadb.com%2FGLBL-WC2017JSONPartI_LP-Registration.html%3Futm_source%3Ddzone%26utm_medium%3Dwhitepaper%26utm_campaign%3Dtext-ad_dynamic-columns_dzone%26utm_content%3Dproduct).
