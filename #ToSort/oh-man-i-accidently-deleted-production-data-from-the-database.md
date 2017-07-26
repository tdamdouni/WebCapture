# Oh Man, I Accidently Deleted Production Data From the Database

_Captured: 2017-06-02 at 00:18 from [dzone.com](https://dzone.com/articles/oh-man-i-accidently-deleted-production-data-from-t?edition=304112&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-01)_

Learn how to [move from MongoDB to Couchbase Server](https://dzone.com/go?i=206124&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454368%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283402) for consistent high performance in distributed environments at any scale.

The probable outcome of a software engineer or database administrator deleting data he didn't mean to from production database is an immediate heart attack. Hospitals are full of programmers leaving out the `WHERE` clause by mistake.

If you're reading this post, I assume you would like to know one of two things:

  1. How to restore data you just deleted from your MySQL database.
  2. How to avoid deleting data you don't mean to from production database.

So, let's tackle both of those.

## How to Restore Data Deleted From MySQL Database by Accident

If you just deleted a couple (of million) records from your production database, you have few options to restore them quickly.

  1. Well, this might be trivial, but I still have to state the obvious -- if you have a backup, this is the time to use it. I recommend restoring the backup to a new server/database, and only once you have the data safely in there, you can copy it to the old server. You can decide whether you just want to revert to an old dump, or maybe just copy a few rows from the backup database/replica.
  2. If you have binary logs enabled, you can restore the relevant statements from there and re-execute them on your production database. The binary logs keep track of all changes that occur on your database, so if you still have the relevant logs, you should be able to restore the data. If you don't know whether the binary logs are activated, use this command in the MySQL client shell: `SHOW VARIABLES LIKE 'log_bin';`_._ Please note that these logs are rotated after a while, so hopefully, your data is still there. 
    * To extract the statements from an entire binary log file, run this command: 
      * `mysqlbinlog mysql_bin.000001 | mysql -u root -ppassword database_name`
    * If you want to extract the lost data from several binary log files, use this command: 
      * `mysqlbinlog mysql_bin.000001 mysql_bin.000002 | mysql -u root -ppassword database_name`
    * If you know when this data was added to the database, you can extract statements by using the relevant timestamps: Do you want to avoid accidentally deleting production data from the MySQL database? 
      * `mysqlbinlog --start-datetime="2017-04-20 10:01:00" \ --stop-datetime="2017-04-20 9:59:59" mysql_bin.000001 \ | mysql -u root -ppassword database_name`

## How to Avoid Deleting Data You Don't Mean to From Production Database

Preventing an issue is always easier and better than handling it after it happened, so let's go over a few tips to make it happen:

  1. **Using the MySQL dummy/beginners mode**: This is a MySQL client startup flag which will prevent accidental data loss in most cases. Start your client using this flag: `mysql -i-am-a-dummy -uroot` test. Using this flag will result in the following constraints: 
    * You won't be able to execute an `UPDATE` or `DELETE` statements unless a key constraint is specified in the `WHERE` clause or unless you provide a `LIMIT` clause (or both).
    * You'll be protected from running large `SELECT` queries -- you'll only be able to fetch up to 1,000 rows unless you explicitly specify a `LIMIT` clause.
    * The MySQL server will abort your query if the optimizer will guess that your query requires analyzing more than 1,000,000 rows to return an answer.
  2. **By using transactions, you can protect yourself from losing precious data**. If you start your work with a `START TRANSACTION` clause, update and delete statements can be rolled back in case you performed a mistake. You can choose to `ROLLBACK` the statements once you're done, or `COMMIT` them to keep the changes.
  3. **Use an advanced MySQL client that protects you from typing mistakes and enables protection flags** -- for example, the free version of MySQL workbench client will automatically enable the dummy flag mentioned above, to protect you from accidentally losing data.
  4. **Generate regular cold backups and/or a database replica**. They are both used for different use cases, but they will both be very helpful if you'll lose some data. In most data loss cases, the cold backups will be more helpful, as in replicas, the data changes will usually be replicated within minutes, so the lost data won't be on the replica database either once that happens.

## Summary

So to summarize, enable binary logs in your MySQL implementation. Also, perform regular backups to make sure you don't lose any data. In addition, enable the dummy mode in all your MySQL clients and ask all other employees to do the same (or maybe use MySQL workbench which comes with this configuration by default).

Want to deliver a whole new level of customer experience? Learn how to make [your move from MongoDB to Couchbase Server](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)[.](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)
