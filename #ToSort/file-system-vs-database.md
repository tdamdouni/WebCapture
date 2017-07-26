# File System vs. Database

_Captured: 2017-04-28 at 19:40 from [dzone.com](https://dzone.com/articles/which-is-better-saving-files-in-database-or-in-fil?edition=292940&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-28)_

Learn how to [move from MongoDB to Couchbase Server](https://dzone.com/go?i=206124&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454368%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283402) for consistent high performance in distributed environments at any scale.

If you are indecisive in choosing the best way to save a file uploaded to your server, then cheers, mate! You're not alone.

As a developer, sometimes I feel confused when asked to choose the optimal way of doing certain simple, yet conflicting things. Later, I realized that understanding the circumstances and requirements paves the way for making the right choice.

If you are accustomed to storing files in a file system and think that file system were created for the purpose of holding files, or if you are not bothered with the advantages of using a database for saving files in certain scenarios, then it's time to reconsider your choices, my friend! This is because modern DBMS focuses on improving the storage of large blobs.

## File System

Let's see some pros and cons involved in saving files in the file system.

### **Pros of the File System**

  * **Performance can be better than when you do it in a database**. To justify this, if you store large files in DB, then it may slow down the performance because a simple query to retrieve the list of files or filename will also load the file data if you used `Select *` in your query. In a files ystem, accessing a file is quite simple and light weight.
  * **Saving the files and downloading them in the file system is much simpler** than it is in a database since a simple "Save As" function will help you out. Downloading can be done by addressing a URL with the location of the saved file.
  * **Migrating the data is an easy process**. You can just copy and paste the folder to your desired destination while ensuring that write permissions are provided to your destination.
  * **It's cost effective** in most cases to expand your web server rather than pay for certain databases.
  * **It's easy to migrate it to cloud storage** i.e. Amazon S3, CDNs, etc. in the future.

### **Cons of the File System**

  * **Loosely packed**. There are no ACID (Atomicity, Consistency, Isolation, Durability) operations in relational mapping, which means there is no guarantee. Consider a scenario in which your files are deleted from the location manually or by some hacking dudes. You might not know whether the file exists or not. Painful, right?
  * **Low security**. Since your files can be saved in a folder where you should have provided write permissions, it is prone to safety issues and invites trouble, like hacking. It's best to avoid saving in the file system if you cannot afford to compromise in terms of security.

### **Use Cases**

  * **If your application is responsible for handling large files** (i.e. over 5MB) and the lots of file uploads.
  * **If your application will have a large number of users**.

### Miscellaneous

Though the file system comes with some costs and certain cons, a good internal folder structure and choosing a folder location that may be a little difficult to access by others can help.

## Database

Let's see some pros and cons involved in saving files in the

### **Pros of Database**

  * **[ACID](https://www.tutorialspoint.com/dbms/dbms_transaction.htm) consistency**, which includes a rollback of an update that is complicated when files are stored outside the database.
  * **Files will be in sync with the database** and cannot be orphaned, which gives you the upper hand in tracking transactions.
  * **Backups automatically include file binaries**.
  * _**It's more secure**_ than saving in a file system.

### **Cons of Database**

  * **You may have to convert the files to blob** in order to store them in the database.
  * **Database backups will be more hefty and heavy**.
  * **Memory is ineffective**. Often, RDBMSs are RAM-driven, so all data has to go to RAM first. Yeah, that's right. Have you ever thought about what happens when an RDBMS has to find and sort data? RDBMS tracks each data page -- even the lowest amount of data read and written -- and it has to track if it's in-memory or if it's on-disk, if it's indexed or if it's sorted physically etc.

Note: I've skipped some contradictory points to curtail the content because while comparing two things, we often end up finding that the pros and cons of one are the opposite of other.

### **Use Cases**

  * **If your user's file needs to be more tightly coupled, secured, and confidential**. 
  * **If your application will not demand a large number of files** from a large number of users.

### Miscellaneous

Be cautious with your `Select` query. Avoid unwanted `Select *` queries, which may frequently retrieve the file data unnecessarily. Caching the file data can help reduce memory and database usage.

If you are using SQL server 2008 or a higher version, make use of Filestream. Filestream enables storing blob data in NTFS while ensuring transactional consistency between the unstructured blob data with a structured data in DB.

To explore more about Filestream, please [refer to this link](https://msdn.microsoft.com/en-us/library/gg471497.aspx).

You may realize that I haven't stated which is the better choice yet. The answer is that it depends.

I know that answer might make you furious, but honestly, the key lies in analyzing your requirements and anticipating the worst cases before hand.

Based on our product requirements, we at Habile opt for the file system when we deal with massive quantities and heavy files, and we go the database way in cases when we have lighter and fewer files.

Adapting to the Filestream feature of SQL server 2008 could be a worthy try, though. So, we at Habile have initiated incorporating Filestream. We encourage you to do the same if you can afford it.

Because in the world of survival of fittest, it's important to utilize the technology to its fullest potential.

Want to deliver a whole new level of customer experience? Learn how to make [your move from MongoDB to Couchbase Server](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)[.](https://dzone.com/go?i=206125&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F76151%3B2454369%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D14283403)
