# How to Document Multiple SQL Server Databases

_Captured: 2017-05-08 at 10:43 from [dzone.com](https://dzone.com/articles/how-to-document-multiple-sql-server-databases?edition=298008&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-07)_

You can use [SQL Doc's](http://www.red-gate.com/products/sql-development/sql-doc/) command-line parameters to [automate database documentation](http://www.red-gate.com/blog/getting-started-with-sql-doc-and-powershell), but when you try to automate the process of documenting a group of databases on a server, they sometimes don't give you enough control over your automated job.

The GUI does offer far more settings but when you're running an automated process, you can't use the GUI, so what are your choices? Fortunately, by creating a SQL Doc XML Project file, you can specify anything that you can specify within the GUI. Supply the path to the file as a command-line parameter, and you get both automation and a lot more flexibility, as I'll demonstrate in this quick tip.

## Hidden Treasure in the SQL Doc Project File

SQL Doc works best when documenting one or more databases on a particular server using a SQL Doc XML project file (`.sqldoc`). You use the tool in User Interface mode to create a project file that you then use, making slight modifications, when appropriate, from the command line.

For example, you can override some of the settings specified in the project file with command-line settings. This means you can run the same project file for several different servers, just by specifying the server and the databases on the server you want to document.

However, what if you want to name the documentation files differently for each database? There is no command line option for that.

In the command line, you can only control the way that objects such as tables are documented, allowing you to exclude creation scripts, triggers, indexes, foreign keys, check constraints or permissions. But what if you want to exclude other objects?

You can, in the project file, specify precisely what classes of object you want to exclude. You can exclude Tables, views, programmability objects (stored procedures, functions, database triggers, types, defaults and rules), and security objects (users, roles and schemas).

## Passing in a Project File on the Command Line

We can create or alter the Project XML file, and then pass the path to that file as a command-line parameter. We'll take the easier, but slightly reckless approach of creating a project XML file, rather than altering an existing one. (It isn't a 'supported' approach, however, so don't send anyone indignant emails if it doesn't work.)

This PowerShell script automates the documentation for four databases (Dave, Dee, Dozy, Beaky) on a single server. Obviously, you should change the values of the variables before you run this code.

Notice that for the `$outputformat` variable, we can specify several different types of documentation. I find the most useful form of documentation to be Framed HTML, which mimics the object browser in SSMS and provides a very quick way of navigating a database schema. If you just want output, the PDF option is useful, and Docx is also very good and has the advantage that it can quickly be converted into another format.

Sadly, I've never managed to get the Markdown format to do anything that can read within a markdown viewer. It seems to be a direct conversion of the HTML format, producing a vast number of individual markdown files and so isn't suitable for a document format.
