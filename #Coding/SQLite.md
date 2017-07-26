# SQLite

_Captured: 2016-12-21 at 15:50 from [pradeepgururani.blogspot.de](http://pradeepgururani.blogspot.de/2010/01/sqlite.html?m=1)_

SQLite is a compact database engine. Here is the brief description about SQLite, "SQLite is an embedded SQL database engine. Unlike most other SQL databases, SQLite does not have a separate server process. SQLite reads and writes directly to ordinary disk files. A complete SQL database with multiple tables, indices, triggers, and views, is contained in a single disk file. The database file format is cross-platform - you can freely copy a database between 32-bit and 64-bit systems or between [big-endian](http://en.wikipedia.org/wiki/Endianness) and [little-endian](http://en.wikipedia.org/wiki/Endianness) architectures."

There is no need of any installation here. You just copy your database file along with rest of your application and you are off using all database capabilities. You have tables, views, triggers, transactions everything barring SP support. Lack of SP support might be an issue but do you really need SPs in small level applications where most of the things might be mere CRUD. You will not get these features if you are using flat/xml file or for that sake windows registry also. This makes this small database eligible for all your quick applications. It also supports most of SQL-92 standard, so if you grow big and need enterprise level server, you can move to SQL Server/Oracle any day. Here is the list of links that you will find helpful when working with SQLite.

  1. SQLite dll - <http://www.sqlite.org/>
  2. SQLite Tutorial - <http://souptonuts.sourceforge.net/readme_sqlite_tutorial.html>
  3. SQLite with .net - <http://www.mikeduncan.com/sqlite-on-dotnet-in-3-mins/>
  4. SQLite .net data provider - <http://sqlite.phxsoftware.com/>
  5. SQLite Administrator - <http://sqliteadmin.orbmu2k.de/>

Good luck with SQLite.

Every SQL database uses its own implementation of the language that varies slightly. While basic queries are almost universal, there notable are nuances between MySQL, PostgreSQL, Microsoft SQL Server, Oracle Database, etc.

What's particularly notable about SQLite is that unlike all the others mentioned above, this database software doesn't come with a daemon that queries are passed through. This means that if multiple processes are using the database at once, they will be directly altering the data through the SQLite library and making the read / write data calls to the OS themselves. It also means that the locking mechanisms don't deal with contention very well.

This isn't a problem for most applications that where one would think of using SQLite -- the small overhead benefits and easy data retrieval are worth it. However, if you'll be accessing your database with more than one process or don't consider mapping all your requests through one thread, it could be slightly troublesome.

Sqlite is very light version of SQL supporting many features of SQL. Basically is been developed for small devices like mobile phones, tablets etc.

SQLite is a third party ,open-sourced and in-process database engine. SQL Server Compact is from Microsoft, and is a stripped-down version of SQL Server.They are two competing database engines.

SQL is query language. Sqlite is embeddable relational database management system.

Edit : ( Source from following comment on my answer )

Sqlite also doesn't require a special database server or anything. It's just a direct filesystem engine that uses SQL syntax. ( By : Adam Plocher )

Techinically, SQLite is not open-source software but rather public domain. There is no license. ( By : Larry Lustig )

SQL is query language. Sqlite is embeddable relational database management system.

Unlike other databases (like SQL Server and MySQL) SQLite does not support stored procedures.

SQLite is file-based, unlike other databases, like SQL Server and MySQL which are server-based.

SQL is a database querying language and SQLite is a database (RDBMS) which uses SQL specifications. SQLite can be said as competitor to Microsoft's SQL Server.

The name itself suggests that it is the light version of SQL RDBMS. It is used in most of the small and portable devices like Android and iOS devices.


