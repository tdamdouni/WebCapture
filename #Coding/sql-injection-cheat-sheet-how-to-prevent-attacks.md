# SQL Injection Cheat Sheet: How to Prevent Attacks

_Captured: 2017-08-08 at 20:13 from [dzone.com](https://dzone.com/articles/sql-injection-cheat-sheet-how-to-prevent-attacks?edition=310396&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-24)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

![Image title](https://dzone.com/storage/temp/5992868-sql-injection-cheat-sheet-768x339.jpg)

[SQL injection](https://www.synopsys.com/software-integrity/resources/knowledge-database/sql-injection.html) takes place when database software can't tell the difference between arbitrary data from the user and genuine commands from the application. When an attacker injects commands into the data they send to a database, they can take database control away from the application owner. This can lead to data corruption, leaks of confidential data, or the bypass of essential logic (e.g., authentication, authorization checks).

The good news is that SQL injection is preventable using a special feature that allows database software to separate application commands from user-supplied data. Or, by preventing untrusted user data from going directly to the database.

Let's look out onto a variety of actionable ways to steer clear of SQL injection attacks.

### 

  1. Identify SQL Injection Attack Vectors for Your Application and Database Solution

  * Check the [National Vulnerability Database ](https://nvd.nist.gov/)for known bugs in your chosen database solution.
  * After selecting the database solution, analyze available safety features (e.g., parameterized queries). These allow the database to ignore any commands injected into the data that the user supplies.
  * Analyze the application's design to identify potential SQL injection attack vectors. Additionally, highlight data paths where commands containing tainted data may be reused to attack queries that don't directly accept user data.

### 

  2. Develop SQL Query Best Practices and Protections

  * Write a set of coding standards that anticipate and protect common use cases for SQL database queries.
  * Develop and approve safe SQL query templates and make them available for developer use.
  * Identify database use cases that are unique to your application. Also, develop custom validation or query building code if parameterization queries aren't enough.
  * Create or customize automated source code scanning tool rules to check for vulnerabilities as the code is being written.

### 

  3. Educate Developers About the SQL Risks and Protection Methods

  * Ensure that developers are familiar with application-specific threats and data sources.
  * Provide developers with foundational training about the risks and general mitigations involving SQL injection.
  * Specify coding standards and standard SQL query templates. Run training sessions on the standards and templates so that developers clearly understand how to utilize them.

### 

  4. Find Problems in the Code

  * Perform automated testing to detect SQL injection vulnerabilities in the source code.
  * Implement manual reviews to ensure that coding standards are followed when a SQL query appears in the code.

### 

  5. Test for SQL Injection

  * Build test cases that attempt to manipulate the database through SQL injection. Run those tests during the QA process.
  * Bring in a [third-party penetration tester.](https://www.synopsys.com/software-integrity/security-testing/penetration-testing.html) Provide them access to the design documents with which they can then perform white box testing.

### 

  6. Don't Add SQL Injection to Your Legacy

  * Make sure that safeguarded or privileged SQL queries and routines aren't exposed to tainted data as new functionalities are added over the life of the application.
  * Be vigilant for new SQL injection vulnerabilities that may lurk in third-party software or libraries that your applications depend on.
  * Have a plan to securely fix any SQL injection vulnerabilities that make it into production.
  * SQL injection is a serious concern. However, with the proper steps, prevention and mitigation can keep your applications securely on course.

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.
