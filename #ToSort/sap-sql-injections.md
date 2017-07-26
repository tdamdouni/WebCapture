# SAP SQL Injections

_Captured: 2017-05-23 at 03:50 from [dzone.com](https://dzone.com/articles/sap-sql-injections?edition=299094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-22)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

This series of articles will continue our [EAS-SEC Guide for secure development](https://erpscan.com/tag/secure-abap-development-guide/) that is aimed to unveil all the most important types of vulnerabilities in ABAP applications. At first, we would like to shed a light on SAP SQL Injections.

At the moment, SQL injection is one of the most common injection vulnerabilities in general and in ABAP as well.

![SAP Vulnerability lists for 2012, 2013, 2014, 2016 and OWASP Top 10](https://erpscan.com/wp-content/uploads/2017/05/xtable-Comparison-of-SAP-vulnerability-lists.jpg.pagespeed.ic.EdL45nr2Lm.webp)

> _Comparison of SAP vulnerability lists for 2012, 2013, 2014, 2016, and the OWASP Top 10_

It consists of the insertion of a malicious SQL query crafted by an attacker into an entry field of an application. Via SQL injection, an attacker can affect database in different ways: to read sensitive data, modify content, or even shutdown the database.

In ABAP, there are several statements where SQL injection can occur:

  * Open SQL Injections in SQL Statements (read more below).
  * Injections in System functions.
  * ADBC Injections.
  * AMDP Injections.

### Open SQL Injections

As the name implies, SQL injections can occur in Open SQL statements: SELECT, WHERE, FROM UPDATE, DELETE, and INSERT.

Here is an example of a potentially dangerous piece of code:

In this example, in the WHERE statement a user-controlled parameter _input_ is used. If an attacker is able to define data reading criteria, he or she will be able to get access to critical data.

An attacker can pass the string 'anything' OR '1'='1' to the variable _input_. As a result, the SQL statement will look as follows:

As '1'='1′ is always true, all records from the database will be shown. Besides, an attacker can use a UNION statement to combine two different SQL requests and get data from other tables.

### Injections in System Functions

Another dangerous construction is related to the system functions "C_DB_EXECUTE" and "C_DB_FUNCTION". These functions are used to call for database commands directly:

The field 'STATTXT' contains a SQL statement. The variable STMT is declared as a parameter and transmitted to this field. Therefore, an attacker can pass a specially crafted SQL statement to the variable STMT and reach the malicious goals by executing it.

Methods "EXECUTE_UPDATE", "EXECUTE_DDL" and "EXECUTE_QUERY" of the "CL_SQL_STATEMENT" class also can be sources of SQL injections:

By exploiting a SQL injection vulnerability, an attacker can get access to business-critical information or system data. Moreover, a denial of service attack can be performed by executing a complicated SQL statement. For example, a perpetrator can pass a query, which will search for a certain pattern through all the records in the database (via a LIKE statement). This query will take a long time to run and, at the same time, will significantly increase the server load, thus blocking access to the application for legitimate users.

### SAP ADBC Injections

There is also a risk of a SQL injection when ABAP Database Connectivity (ADBC) is used. SQL statements are passed as strings to the objects of the ADBC class and then to the database system. An attack is possible if all parts of one of these SQL statements originate from outside of the program to the following methods:

  * `create_query`  

  * `get_persistent_by_query`  

  * `execute_query`  

  * `execute_update`  

  * `execute_ddl`  

  * `execute_procedure`  


Example:

The variable 'key' passes from a request to the method 'execute_query' without validation. An attack example is similar to one described in the Open SQL injection section.

### SAP AMDP Injections

With new power comes new responsibility; thus, when working with the most powerful database, namely [SAP HANA](https://erpscan.com/solutions/by-system/sap-hana-security/), you have to pay close attention to its security.

When ABAP Managed Database Procedures (AMDP) is used, database procedures are created and called that are currently implemented in SQLScript for the SAP HANA database. Risks are incurred whenever a database procedure contains dynamic parts.

Example:

This method uses the SQLScript statement EXEC in the SAP HANA database to execute a SQL specified as a character string into which the input parameter seats are merged. In this example, the value in the SEATSOCC column is increased by the value of the parameter _seats,_ which is passed unchecked. An attacker can send the string `2, seatsmax = seatsmax + 10` to this parameter and change the value in the SEATMAX column as well. A method like this should be classified as a potential risk since the input parameter is not checked. If possible, an input check should be implemented in the SQLScript directly before the statement EXEC is executed.

## SAP SQL Injection Protection

To protect an ABAP code from SQL injections, primarily, you need to make sure that dynamically generated statements are necessary for your code (actually, this applies to all injections). In some cases, you can transform the program so they will not be required. For example, use the listing of tables (FROM … table1 … tableN …) instead of the table catalog (FROM …(tablecatalog)…).

If it is not possible, filter user input via special methods QUOTE_STR and QUOTE of the CL_ABAP_DYN_PRG class. In ABAP, strings are usually enclosed with backticks (') and char arrays are usually enclosed in single quotation marks ('). Use different methods of CL_ABAP_DYN_PRG depending on the type of enclosing symbol: use QUOTE_STR with backticks and QUOTE with single quotation marks.

Example:

**Note:** CL_ABAP_DYN_PRG=>ESCAPE_QUOTES_STR and CL_ABAP_DYN_PRG=>ESCAPE_QUOTES methods can also be used to filter data, but they provide less security.

In terms of ADBC, the values transmitted to the database can be parameterized to avoid a SQL injection. To specify parameters, it is necessary to use the character "?" (placeholder). Before SQL expression execution, all parameters must be filled. The filling of parameters is carried out through the SET_PARAM method with specifying of the link to a variable. At the same time, by default, the filling of parameters happens in turn, from left to right, in the SQL expression. After the SQL expression execution, all assignments of the parameters are lost.

That's all for today, and I hope the article clarified all questions you wanted to learn about SAP SQL injections.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
