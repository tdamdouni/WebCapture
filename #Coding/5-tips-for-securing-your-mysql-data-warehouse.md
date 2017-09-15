# 5 Tips for Securing Your MySQL Data Warehouse

_Captured: 2017-08-19 at 19:26 from [dzone.com](https://dzone.com/articles/5-tips-for-securing-your-mysql-data-warehouse?edition=317403&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-19)_

Traditional relational databases weren't designed for today's customers. Learn about the [world's first NoSQL Engagement Database](https://dzone.com/go?i=233224&u=https%3A%2F%2Finfo.couchbase.com%2Fengagement_database_white_paper.html) purpose-built for the new era of customer experience.

By creating a central repository of data from different sources within a company, the process of data warehousing allows businesses to make intelligent, strategic decisions by analyzing and reporting on the combined business data. While data warehouses offer many convenient benefits, gathering such sensitive data into a single system brings with it the problem of data warehouse security.

If your business uses a data warehouse, you need to consider how best to protect the information inside the system. Any compromise in data warehouse security grants intruders or cyber criminals access to information on your company's sales, marketing, customer details, and more. As the [WannaCry ransomware attack of 2017](https://www.theguardian.com/technology/2017/may/12/nhs-ransomware-cyber-attack-what-is-wanacrypt0r-20) showed, data crime is an important consideration for every modern business.

Perhaps the most common database management system used in data warehouses is the open source MySQL database. The following five tips highlight some of the best ways to secure your MySQL data warehouse.

## **1\. Limit Access**

One of the most useful ways to secure your MySQL data warehouse is to only give users the access they absolutely need. You can limit access to the information in your data warehouse by implementing role-based control, in which the ability to view and/or manipulate database objects including tables and schemas is limited by the user account's defined role in the warehouse database.

The MySQL database administrator can enforce rigid security measures limiting what individual users can do to the data warehouse, including:

  * The number of queries an account can issue per hour. 
  * The number of updates an account can issue per hour.
  * The number of times an account can connect to the server per hour. 
  * The number of simultaneous connections to the server by an account.

Since you will use the information contained in the data warehouse to make important business decisions, access to view or alter MySQL warehouse data should only be given to key business stakeholders.

## **2\. Create a Password Expiration Policy**

Password hacking represents one of the main ways intruders may get access to any database system. Using MySQL gives you the option to create your own password expiration policy using the `default_password_lifetime` variable to set the number of days for a user's password to expire.

The problem with password expiration is that you need to find the right balance. [Evidence suggests ](https://www.cylab.cmu.edu/files/pdfs/tech_reports/CMUCyLab13013.pdf)that users required to change their password too frequently might become frustrated with such a policy, thus leading them to create a more simple password that is vulnerable to hacking. Choose a sensible expiration time such as six months after which users need to create a new password to access the data warehouse.

Consider also advising anyone with access to the data warehouse to use a password generator, enabling them to create a strong password every time.

## **3\. Back Up Files**

As with any database system, the importance of backing up your MySQL data warehouse cannot be understated. Natural disasters such as floods and fires, system crashes, hardware failures, and human error all pose a threat to important business data.

MySQL comes with a slew of backup features enabling you to quickly recover your database in the event of a security compromise. Most important for data warehouses is to create physical backups, which are raw copies of the directories and files that store database information. You can easily and quickly restore backed up information when you need it using special MySQL functions.

Remote backups allow your business to choose a secure remote server as the destination for a data backup, which is useful for avoiding problems arising from fires, floods, and hardware failures.

## **4\. Install Critical Patch Updates**

As current developers of the MySQL system, Oracle Corporation regularly releases critical patch updates that fix security issues with your MySQL data warehouse. It's extremely important that your business keeps updated on these critical patches and installs them as soon as possible after they are released.

Patches exist because the developers sometimes find certain flaws in the existing software and they need to fix these errors. [You can check here](https://www.oracle.com/technetwork/topics/security/alerts-086861.html) for all scheduled and past critical patch updates for MySQL.

## **5\. Use Trusted Data Integration Solutions**

Since a MySQL data warehouse pulls information from multiple data sources within your business, it's important to use reliable solutions to gather and integrate such data. A good data integration platform should efficiently and securely send data from multiple sources to your MySQL data warehouse with the minimum of fuss.

Furthermore, the security of your chosen data integration platform is vital when you replicate data from [MySQL to data warehouses](https://www.alooma.com/integrations/mysql) on the cloud including Redshift and BigQuery. A trusted platform securely sends important data from MySQL to the cloud for larger-scale data analysis.

Incorporate these five tips into managing your MySQL data warehouse and you'll ensure that important business data gets full protection.

Learn how the world's first [NoSQL Engagement Database](https://dzone.com/go?i=233225&u=https%3A%2F%2Finfo.couchbase.com%2Fengagement_database_white_paper.html) delivers unparalleled performance at any scale for customer experience innovation that never ends.

Opinions expressed by DZone contributors are their own.
