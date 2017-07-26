# How to Convert MySQL to MySQLi

_Captured: 2017-04-20 at 23:59 from [dzone.com](https://dzone.com/articles/convert-mysql-to-mysqli?edition=292902&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-20)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

One of the most important developments in the PHP world was the backward compatibility break for the PHP MySQL extension, which leaves us with two methods to connect to the database: MySQLi and [PDO](https://www.cloudways.com/blog/introduction-php-data-objects/).

![Image title](https://dzone.com/storage/temp/4967954-mysql.png)

In PHP 7, the MySQL extension is completely removed. Thus, in this article, I will discuss how to convert a MySQL extension into MySQLi. The first thing you should understand is that MySQL works as a resource whereas MySQLi works as a resource and an object. While you really do not need to know the technical differences, you must understand that these two are a lot different from each other.

## MySQL to MySQLi Procedural Methods

I will first start with the most commonly used MySQL methods. The only thing that changed in the following method is the addition of "i" in MySQL and some changes of the positions of `link` and `result` in the parameter of the method.

Following are the popularly used methods of MySQL, followed by the equivalent methods in MySQLi.

If you want to convert your script from a MySQL extension to a MySQLi extension manually, you must start with the top of the script and start converting all the methods one by one.

For this, open the script in any text editor and use the find-and-replace tool to replace `mysql_` with `mysqli`. But that's not all. You must manually check and verify the parameters of the method, as well.

To automate the process of converting the script from MySQL to MySQLi, I can use the following online tools. I will create a sample insertion and retrieval code and convert it using one of these tools.

## Sample Code for Conversion

I am going to use the following database and code for testing the online conversion tools.

### Database SQL

### Connection.php
    
    
    $con = mysql_connect($servername,$username,$pass) or die("Problem occur in connection");

### Insert.php

### Retrieve.php

Here is the basic PHP code which uses MySQL extension to create the database connection, select database, create and execute a query and fetch data from the database.

Now I will convert the script using an online tool.

## ICT Academie

In order to convert the code using [ICT Academie](http://www.ictacademie.info/mysqlconverter/GUI/convert_snippet.php), all you need to do is paste your code snippet enclosed in PHP opening and closing tags.

For example, if you want to see how `mysql_connect()` gets converted, paste `<?php mysql_connect() ?>`>".

Code conversion result from the ICT Academie for the above code is as follows.

### Connection.php

### Insert.php

### Retrieve.php
    
    
    while($data = mysqli_fetch_array($result)) 

To test the converted code, it is clear that all the MySQL methods have been successfully converted into MySQLi. It only changes the PHP code, but the result remains the same.

Note: Before starting the conversion process, create backups of all the files and test run all the code before live deployment. The converter only converts the code. It does not add any security measures to prevent SQL injections.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).

Opinions expressed by DZone contributors are their own.
