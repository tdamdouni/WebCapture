# Securing MySQL Server on Ubuntu 16.04 LTS, Part 1: Installing MySQL

_Captured: 2017-05-25 at 10:22 from [dzone.com](https://dzone.com/articles/securing-mysql-server-on-ubuntu-1604-lts?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Databases can be found in everything from desktop applications, web applications, corporate servers to smartphones and other devices. Almost every software program relies on some sort of database to store its data. As applications continue to grow, so is the amount of data that is being stored in databases, which is the main reason why they are the number one target of attackers-databases frequently contain information that is useful or desirable to an attacker. Data breaches, commonly expose data containing personally identifiable information such as names, usernames, passwords, email addresses, credit card numbers, health records; as well as other confidential documents such as trade secrets or commercially sensitive information. Legislation around the world is very strict when it comes to data privacy, so much so, that substantial fines may be incurred by organizations suffering a data breach. To such an extent, it is crucial to secure databases and their content.

For the past 15 years, [SQL injection](https://www.acunetix.com/websitesecurity/sql-injection/) has been among the most common and dangerous attacks on web applications. In SQL injection, the database server is not directly exposed to the attacker since an attacker would exploit vulnerabilities that arise as a result of poor coding practices in the frontend or backend of web applications. However, misconfiguration of the database server itself can also lead to unauthorized access or escalation of privileges which is granted via other vulnerabilities like the SQL injection.

In this series, we will focus on how to create a more secure environment for a MySQL server, which is currently the second most popular database management system (DBMS), in order to prevent common attacks, as well as to mitigate the attack vector of other vulnerabilities.

For the purposes of this article, we have set up a machine running **Ubuntu 16.04 LTS** (Xenial Xerus) and MySQL 5.7. We have also edited our hosts' file to point 'example.com' to the IP address of our test machine.

## Installing MySQL Server

MySQL server can be installed in two ways. We can either do a version-specific installation or automatically install the latest version that is available for our distribution. We will proceed with the second option since it is always better to run the latest version of a software.

Before installing any software, we need to make sure that our system has the latest package lists from its repositories, otherwise, this might result in installing outdated software.

Now that our package lists are updated, we can proceed with the installation of the latest version of MySQL server by running the following command.
    
    
    secuser@secureserver:/# sudo apt-get install mysql-server

The installer will search for the packages and dependencies that need to be installed and then we will be prompted to confirm that we want to proceed with the installation of those packages.
    
    
    mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server-5.7 mysql-server-core-5.7
    
    
    mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server mysql-server-5.7 mysql-server-core-5.7
    
    
    0 to upgrade, 9 to newly install, 0 to remove and 253 not to upgrade.
    
    
    Need to get 0 B/17.9 MB of archives.
    
    
    After this operation, 160 MB of additional disk space will be used.
    
    
    Do you want to continue? [Y/n] Y

## MySQL Setup - Root Account

During the initial setup, we are being prompted to set a password for the MySQL's root account.

![MySQL set up](https://www.acunetix.com/wp-content/uploads/2016/07/image01.png)

Using a strong password is **critical**. A strong password should be longer than 12-15 characters and should be a combination of alphanumeric and special characters and ideally, it should not contain words you can find in a dictionary (e.g. - _LjoS^5hwF$9Uyn*0pBEe_). Many administrators, choose very easily guessable passwords for their own convenience or forget to change passwords when the server moves into a production environment. This means that the database user account can be brute-forced either remotely or locally (requires to already have access to the server). Furthermore, simple passwords are much easier for an attacker to crack offline should they manage to steal the MySQL users' password hashes.

The following is an example of a MySQL server which is exposed over a network combined with an insecure root account password.
    
    
    [*] 192.168.2.108:3444 MYSQL - Found remote MySQL version 5.7.12
    
    
    [-] 192.168.2.108:3444 MYSQL - LOGIN FAILED: root:admin (Incorrect: Access denied for user 'root'@'192.168.2.112' (using password: YES))
    
    
    [-] 192.168.2.108:3444 MYSQL - LOGIN FAILED: root:root (Incorrect: Access denied for user 'root'@'192.168.2.112' (using password: YES))
    
    
    [-] 192.168.2.108:3444 MYSQL - LOGIN FAILED: root:r00t (Incorrect: Access denied for user 'root'@'192.168.2.112' (using password: YES))
    
    
    [-] 192.168.2.108:3444 MYSQL - LOGIN FAILED: admin:r00t (Incorrect: Access denied for user 'admin'@'192.168.2.112' (using password: YES))
    
    
    [-] 192.168.2.108:3444 MYSQL - LOGIN FAILED: admin:toor (Incorrect: Access denied for user 'admin'@'192.168.2.112' (using password: YES))
    
    
    [-] 192.168.2.108:3444 MYSQL - LOGIN FAILED: admin:l3tme1n (Incorrect: Access denied for user 'admin'@'192.168.2.112' (using password: YES))
    
    
    [+] 192.168.2.108:3444 MYSQL - Success: root:l3tme1n'

The root account should under **no circumstances** be used in any of our web applications. If we use the root account to connect our web application to the database, then if an attacker is able to execute commands on the SQL server, they will be able to enumerate and possibly modify and even delete data inside all the databases and tables that the database server manages.

Not only will an attacker be able to compromise data in the database server, but in the case of a server misconfiguration, as we will see later on in this article, this could result in a complete server compromise.

## Testing Installation

Now that the installation is finished, we can test whether the MySQL has been successfully installed and is running. We can verify if the `mysql` daemon is running in numerous ways.

### Services

We can list the services that are currently running on the system and filter to show `mysql` related ones:
    
    
    secuser@secureserver:/# ps aux | grep mysql
    
    
    --> mysql 7891 0.2 7.1 1784520 145100 ? Ssl 14:32 0:00 /usr/sbin/mysqld
    
    
    secuser 8093 0.0 0.0 14232 1084 pts/5 S+ 14:35 0:00 grep mysql

### mysqladmin

We can use mysqladmin, which is a client for performing administrative operations on MySQL Server.
    
    
    secuser@secureserver:/# mysqladmin -u root -p status
    
    
    --> Uptime: 318 Threads: 1 Questions: 2 Slow queries: 0 Opens: 67 Flush tables: 1 Open tables: 60 Queries per second avg: 0.006

### service

We can use the `service` command which is mostly used to start/stop services. Using the status parameter, we can see the current status of a given service.
    
    
    --> Active: active (running) since Thu 2016-07-14 11:13:03 BST; 6min ago

Should the MySQL daemon not be running, we'd get the following output instead.
    
    
    --> Active: inactive (dead) since Thu 2016-07-14 11:19:50 BST; 1s ago
    
    
    Main PID: 7891 (code=exited, status=0/SUCCESS)

We can also login to the MySQL server. A successful login means that the server is properly functioning.
    
    
    secuser@secureserver:/# mysql -u root -p
    
    
    Welcome to the MySQL monitor. Commands end with ; or \g.
    
    
    Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.
    
    
    Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.
    
    
    Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
