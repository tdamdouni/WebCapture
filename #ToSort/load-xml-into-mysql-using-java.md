# Load XML Into MySQL Using Java

_Captured: 2017-02-21 at 20:07 from [dzone.com](https://dzone.com/articles/load-xml-into-mysql-using-java?edition=272882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-21)_

> "Never memorize something that you can look up."  
― Albert Einstein

XML provides the ability to represent hierarchical structures with its parent-child relationships. This enables applications to store structured data in XML for export. Importing this XML data into a database is a bit involved as we shall see in this article. You need to write code to manage the database connection. In addition, you need to parse the XML and isolate the data that needs to be imported.

In this article, we show how to import and load XML data into a MySQL database. The application creates the table for storing the data and proceeds to import the data.

We are attempting to import data from [books.xml](https://msdn.microsoft.com/en-us/library/ms762271\(v=vs.85\).aspx), which looks like this:

## 2\. Load MySQL JDBC Driver

Download the MySQL Connector/J Driver from [here](https://dev.mysql.com/downloads/connector/j/). Unpack the distribution and copy the `mysql-connector-java-<version>-bin.jar` to your application directory. _(Replace <version> with the version of the driver you downloaded.)_

The first thing we need to do in the application is to load the MySQL JDBC driver. While we use a `static` block for that, you can always load the driver while the application is running.

## 3\. Connect to MySQL

The format of the JDBC connection string is as shown. This string is used for connecting to a MySQL database running on the localhost -- the database name we are using is `testing`. The username and password are also specified in the connection string.

Here is the code to open a connection to the MySQL database using the above connection string.

If you would rather specify the username and password separately instead of including it in the connection string, you can do this instead. _(Maybe you are obtaining these values from different locations.)_

## 4\. Create MySQL Table

Let us now create the table with the structure needed for the storage.

Note the following:

  * MySQL sets the `id` field to an auto incremented value when creating the row.
  * We store the XML attribute `id` in the `book_id` field.
  * The `description` field is `text` since we expect it to be somewhat large but not exceed 65,535 characters.

## 5\. Parse XML

With the database setup code out of the way, let us look into importing the XML data into the application. [See here](http://www.novixys.com/blog/how-to-extract-data-from-xml-in-java/) for a tutorial about using an XML parser to parse the XML data.

With this code, we end up with a _[Document](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html)_ object representing the XML data in memory. We can use this _Document_ object to search for the data we want to insert into the database.

To insert the data, we need to obtain the required data from the XML nodes. The following is a convenience method to extract an attribute value from a _[Node](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Node.html)_.

And we use this convenience method to extract the text content of a named child element.

## 7\. Prepare XML Data

We use [XPath ](http://www.novixys.com/blog/how-to-extract-data-from-xml-in-java/)to extract the set of nodes whose data we want to insert into the database. Given the structure of the XML, the set of nodes are located at the XPath `/catalog/book.`

The above code returns a _[NodeList_ ](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/NodeList.html)that matched the specified XPath.

## 8\. Insert into MySQL

To insert the data extracted in a loop, we create a _[PreparedStatement_ ](https://docs.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html)as follows:

We use the following loop to extract and insert the data from the child elements using the convenience methods defined earlier:

With that, we have successfully imported data from an XML file into a MySQL database.

This article covered the details of importing XML into a MySQL database. We parsed the XML using the DOM parser. Then we used XPath to extract just the data we needed. Finally, we inserted it into the database using JDBC.
