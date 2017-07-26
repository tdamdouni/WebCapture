# Configuring mySQL For Use With A Web-Based Sign-in System

_Captured: 2017-05-25 at 13:42 from [hackmypi.com](https://hackmypi.com/SignInPart2.php)_

![](https://hackmypi.com/images/thumbnails/SignInPart2/MySQL.jpg)

**Web Check-In Part 2: Configuring mySQL**

Disclaimer: This guide is a bit more technical than the average guide on this site. I recommend taking it slow.

So for those of you not following the sign-in series, myself and a coworker made a web-based sign-in system for tracking people waiting to be helped during a product launch. In part 1 we explained how to install and setup a LAMP webserver on the Raspberry Pi for hosting the webpage itself. In this part of the series we will accomplish 2 goals. First we'll setup a database server that our webpage can store data in, and talk to, for tracking people being helped. Second, we'll create a PHP script to do the initial work of communicating with the server. The other PHP files will all use this script when we start working on them.

### Setting up mySQL

As always, you'll need the terminal open for this. If your pi auto-boots to a terminal, awesome! If not, press Ctrl+Alt+T from within the Pi's desktop environment to open a terminal. Type the following command into the terminal:

` mysql -uroot -p `

This tells MySQL (which we installed in the last section as part of LAMP) that we want to log in as its "root" user and that we'll enter the password at the first prompt. MySQL does support entering the password as part of the initial login command, but I don't recommend doing it (the password then gets saved as part of your terminal's command history and anyone with physical access can see your password). Once you've logged in and you're at the "mysql>" prompt, the first step is to create the database our pages will connect to. You'll type in the following:

` CREATE DATABASE queueDB DEFAULT CHARACTER SET utf8; `

Don't forget the ending semicolon! Just like with PHP (and C, etc.), the semicolon tells MySQL that your statement is complete. This statement creates a database named queueDB that we can add our tables to and sets the default character encoding to "utf8". This enables us to support languages other than English relatively easily. Next we'll need to create the table like this:

` CREATE TABLE queueDB.Customers (`  
`id INT PRIMARY KEY AUTO_INCREMENT,`  
`first VARCHAR(30) NOT NULL,`  
`last VARCHAR(30) NOT NULL,`  
`status TINYINT DEFAULT 0,`  
`signin TIMESTAMP DEFAULT CURRENT_TIMESTAMP,`  
`assist TIMESTAMP NULL,`  
`finish TIMESTAMP NULL,`  
`preorder BOOL DEFAULT FALSE); `

What that does is create a table, and tell MySQL what each column should be.

1) The first one ("id") is also called the "PRIMARY KEY" which implies that it has to be unique (no 2 rows can have the same value in that column), and "AUTO_INCREMENT" tells MySQL to automatically give it a value.

2) The next 2 columns ("first" and "last") are "VARCHAR" types, which means they are strings of characters up to a maximum length (the number in the parentheses); this will be where our customer's first and last names go.

3) "status" is a "TINYINT", meaning the value it holds is very small; it just contains a number that tells us whether the customer is being helped, is finished, etc. Its default value is set to "0", which is what we'll use for customers who are waiting. We'll get to the other possible statuses in the next part!

4) The "signin", "assist", and "finish" columns are "TIMESTAMP" values which means we can use them to tell when something happened.

5) And finally, "preorder" is a "BOOL" value which can only store either "TRUE" or "FALSE", so we'll use that to know if this customer has a preorder or not (for our event, people who preordered the product had to be handled slightly differently, so asking up front saved our associates time).

Next, we'll need to create a user account that can be used to access these tables (just like you don't log in to your Pi as "root", you don't want to have every access to your database done as "root" either!). The following command will create a user account with a password:

` CREATE USER queueUser@localhost IDENTIFIED BY 'Pass!234'; `

Now, please do not actually use that password on any live machine (especially if it can connect to the internet)! It's just an example I'm giving here, but please change it for your own usage. The user account we just created is named "queueUser", and the "@localhost" tells MySQL that the account can only log on from the local machine (no remote connections are allowed). For our PHP scripts this will be fine; after all, they'll be running on the server locally and only the results are seen by the client computer. Since user accounts are initially created with no access permissions, we'll need to allow this account to have access to modifying the database with the following command:

` GRANT SELECT, INSERT, UPDATE ON queueDB.* to queueUser@localhost; `

This gives our account the ability to "select" rows (get data from them), insert new rows, and update existing rows. It's good practice for any account to only have permissions it actually needs and this is all we'll need this account to do. At this point we're done inside MySQL, so you can type "exit" at the prompt to quit the program (no semicolon needed this time!).

### Accessing the database with PHP/PDO

Now, before we get started here I want to explain a couple things. PDO (PHP Data Objects) is a library of functions for PHP that allows you to connect to a database so that you can interact with it. There are multiple ways to connect with SQL databases from PHP (MySQL included) aside from PDO, but I chose PDO specifically because of its easy support for "prepared statements" which, when used properly, can help protect you and your website against what's called a "SQL injection attack". PDO also supports multiple SQL databases, not just MySQL, so if for some reason you change to using a different database down the road it's a matter of adjusting your SQL statements rather than using a completely different library.

Now to get started, we'll need to create a new PHP file. If you've been following Matt's guides, you'll have a "/scripts" directory which is a great place to create this first file (it will never be accessed by a web browser). If you don't have a /scripts directory, or are unsure, run the following command to create it:

`sudo mkdir /scripts`

Next enter the following terminal commands:

` cd /scripts`  
`nano dbc.php `

The second line of code creates a PHP file called "dbc.php" and opens it in the nano text editor within linux. Now we can start with our PHP code. Our first line should be:

` <?php `

This tag opens the PHP code block, and tells the webserver that the following should be executed as php. Next:

` function connectDB() { `

That tells PHP we're defining a function (a re-usable piece of code), and what's inside the function will only be executed if another part of the script asks it to be.

` $host = 'localhost';`  
` $name = 'queueDB';`  
` $user = 'queueUser';`  
` $pass = 'Pass!234';`  
` $dsn = "mysql:host=$host;dbname=$name;charset=utf8"; `

These statements set up how we'll be connecting to the MySQL database. You'll recognize the database and user names along with the password we set up; localhost means we're connecting to a database server on the same machine, and the "$dsn" variable tells PDO what database server to use and what character set to talk to it with.

` $opt = [`  
` PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,`  
` PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,`  
` PDO::ATTR_EMULATE_PREPARES => false`  
` ]; `

This tells PDO how to handle errors, fetch data, and whether to emulate prepared statements or to use "native" prepared statements (meaning, use the database server's own ability to deal with prepared statements). These are good defaults for this kind of usage, but there are lots of options for PDO that are outside the scope of this article. Feel free to look them up on the PHP website in the documentation section (link==php.net). Next, we want to create the database connection:

` return new PDO($dsn, $user, $pass, $opt); `

What that does is create a new database connection and pass it to the original function call. This function will be called in the files we havent created just yet. This file is almost done! To finish it up we just need the following:

` } ?> `

The "}" closes out the function definition, and the "?>" tells the PHP interpreter that all the PHP code is finished. Make sure you have a blank line at the end of the document, and then type [Control+X] followed by [Y] and [Enter] to save the document and exit nano. Now, what have we done here? We've created a small script that our other PHP files will use in order to connect to our database. With it being so small, why not just include it in the main file? For one thing, having the code in multiple places means more places to change things if you find you need to (and means that one or more could be forgotten!), so this makes your work easier going forward.

### Some other considerations:

If you just want to use the code I've written "as-is", you can skip this section. This will be covering some of the reasons why I chose to set up the database the way it is.

If you're like me, your first impulse when trying to set up such a system would be to make a table for customers who are waiting, a table for customers who are being assisted, a table for who preordered, and maybe a table to store the timestamps exclusively (I didn't want customer names to be stored long-term).

One problem that arises when you do that is in order to move a customer from one status to another you have to "select" the data from their current table, "insert" it into the new table, and finally "delete" it from the old table (in that order, so that if any errors happen the data is just left untouched, or duplicated at the worst). So, that becomes 3 statements. However in order to make sure that only one script is touching a given customer's data at once you need to lock both tables you're working with, and then unlock them when you're done. So now you're at 5 statements, and you're temporarily preventing other scripts from doing what they need to do.

On the other hand, if you're storing everything in a single table, you can use SQL's ability to intelligently modify specific records so that you just change the status (and update a timestamp if appropriate) only on rows matching the id *and* status you specify. This way if 2 scripts try to change the same customer's data the first one will succeed, and the second one will silently do nothing. As far as the SQL database is concerned, both statements executed successfully, but the second one didn't match any records so it didn't actually *do* anything. This means that, using a single table, you're able to do that same work in a single SQL statement instead of 5!

So, is a single table always the way to go? No! The right number of tables depends on the data you're storing in there. I highly recommend that if you want to design and use databases you study "normalization". To "normalize" your database tables is to follow a set of rules that results in them being laid out in a logical fashion which facilitates (relative) ease of use and access. SQL was designed to work with normalized tables, and so you'll find that if you work with those rules you'll get the same job done with fewer, more concise, and easier-to-maintain SQL statements. As a bonus they'll generally be easier to read as well.

Another thing I thought about, was that I wasn't sure how well MySQL (especially on a Pi!) would handle tables with many, many rows (after all, if I leave this running how many customers will eventually sign in?). It turns out that if you properly design your tables MySQL (and any other SQL database, really) can easily handle tables with many thousands of rows (millions or even tens of millions if your hardware is powerful enough). So the concern is less "how big will this table be" and more "are these tables designed properly".

This was all very new to me when I started this project (and still is!), so again I recommend that you study database design principles before designing a database. I spent several hours redoing my code after realizing I'd been doing it "the hard way", and the end results were something that could've taken a few minutes to code had I done it properly to start off with. Learn from my mistakes and study before you cost yourself a ton of time!

#### **Parts links (as of April 2017): **

[SanDisk Ultra 32GB microSDHC UHS-I Card with Adapter, Grey/Red, Standard Packaging (SDSQUNC-032G-GN6MA)](https://www.amazon.com/gp/product/B010Q57T02/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B010Q57T02&linkCode=as2&tag=hackmypi09-20&linkId=b5e7e99239a2b7d427d469794ce0fb51)   
[Raspberry Pi 3 Model B Motherboard](https://www.amazon.com/gp/product/B01CD5VC92/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B01CD5VC92&linkCode=as2&tag=hackmypi09-20&linkId=955c48e6807942c90cd76cdc298935a0)   
[NeeGo 2.5A Power Supply USB Adapter Charger for Raspberry Pi 1, 2 and 3, 6-Feet](https://www.amazon.com/gp/product/B01DTDDDMQ/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B01DTDDDMQ&linkCode=as2&tag=hackmypi09-20&linkId=c2cebdde51dad3410e7fdc1d07fdff24)
