# Relational to JSON With Node.js

_Captured: 2017-11-14 at 21:13 from [dzone.com](https://dzone.com/articles/relational-to-json-with-nodejs-1?edition=334873&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-14)_

Check out the other parts of this series here:

Node.js is a platform for building JavaScript-based applications that has become very popular over the last few years. To best support this rapidly growing community, Oracle developed [a driver for Node.js](http://github.com/oracle/node-oracledb). Written in C and utilizing the Oracle Instant Client libraries, the Node.js driver is both performant and feature rich.

When it comes to generating JSON, Node.js seems like a natural choice, as JSON is based on JavaScript objects. However, it's not exactly fair to compare a solution crafted in Node.js to the PL/SQL solutions as Node.js has a clear disadvantage: it runs on a separate server. That means we have to bring the data across the network before we can transform it to the desired output.

Whatever, let's compare them anyway!

## Solution 1: Emulating the PL/SQL Solutions

This first solution follows the same flow as the PL/SQL-based solutions. We start off by making a connection to the database and then begin creating the object we need by fetching data from the Departments table. Next, we go to the Locations table, then the Regions table, and on and on until finally, we have the object we want. We then use `JSON.stringify` to serialize the object into the JSON result we are after.
    
    
    var oracledb = require('oracledb');
    
    
                        department.id = results.rows[0][0];
    
    
                        department.name = results.rows[0][1];
    
    
                        department.managerId = results.rows[0][2];
    
    
                        getLocationDetails(results.rows[0][3], department, connection, callback);
    
    
                department.location.id = results.rows[0][0];
    
    
                department.location.streetAddress = results.rows[0][1];
    
    
                department.location.postalCode = results.rows[0][2];
    
    
                getCountryDetails(results.rows[0][3], department, connection, callback);
    
    
                department.location.country.id = results.rows[0][0];
    
    
                department.location.country.name = results.rows[0][1];
    
    
                department.location.country.regionId = results.rows[0][2];
    
    
                if (results.rows.length) {
    
    
                    department.manager.id = results.rows[0][0];
    
    
                    department.manager.name = results.rows[0][1];
    
    
                    department.manager.salary = results.rows[0][2];
    
    
                    department.manager.jobId = results.rows[0][3];
    
    
                    department.manager.job.id = results.rows[0][0];
    
    
                    department.manager.job.title = results.rows[0][1];
    
    
                    department.manager.job.minSalary = results.rows[0][2];
    
    
                    department.manager.job.maxSalary = results.rows[0][3];
    
    
    function getEmployees(department, connection, callback) {
    
    
            '   to_char(hire_date, \'' + dateFormat + '\'), \n' +
    
    
                results.rows.forEach(function(row) {
    
    
                    emp.isSenior = row[2] === 1;
    
    
                            '   to_char(start_date, \'' + dateFormat + '\'), \n' +
    
    
                            '   to_char(end_date, \'' + dateFormat + '\') \n' +

### Output

When called with the department ID set to 10, the function returns the serialized JSON that matches the goal 100%.

So we got the output we were after, but what about performance? Let's explore the test results...

### Test Results

When I finished the solutions for [PL/JSON](https://jsao.io/2015/07/relational-to-json-with-pljson/) and `[APEX_JSON](https://jsao.io/2015/07/relational-to-json-with-apex_json/)`, I wanted to see if one was faster than the other. I ran a very simple test: I generated the JSON for all 27 departments in the HR schema 100 times in a loop (2,700 invocations of the solution). `APEX_JSON` finished in around 3.5 seconds while PL/JSON took 17 seconds. How long did it take the Node.js solution from above to do this? 136 seconds! What??? Node.js must be slow, right? Well, not exactly...

You may have noticed that on Line 5, I used the base driver class to get a connection to the database. If I was just doing this once the code would be fine as is, but 2,700 times? That's not good. In fact, that's really bad! But what's a Node.js developer to do?

### Using a Connection Pool

The Node.js driver has supported connection pools from the beginning. The idea is that, rather than incur the cost of making a connection to the database each time we need one, we'll just grab a connection from a pool of connections that have already been established and release it back to the pool when we're done with it. Best of all, this is really simple!

Here's a new module that I'll use to create, store, and fetch the connection pool:

With that in place, I can update the test code to open the connection pool prior to starting the test. Then I just need to update the solution to use the connection pool:
    
    
    var pool = require(__dirname + '/pool');

That's it! I just swapped out the driver module for the pool module and used it to get a connection instead. How much did using the connection pool help? With that one simple change, the test completed in 21.5 seconds! Wow, that's just a little longer than it took PL/JSON. So Node.js is still slow, right? Well, not exactly...

## Solution 2: Optimizing for Node.js

Remember when I said that the solution mimicked the PL/SQL code? There are two major problems with doing this in Node.js:

  1. **Excessive round trips**: Each query we're executing is a round trip to the database. In PL/SQL, this is just a context switch from the PL/SQL to the SQL engine and back. I'm not saying we shouldn't minimize context switches in PL/SQL, we should, but in Node.js this is a round trip across the network! By using the database to do some joins we can reduce the number of queries from 7 to 3.
  2. **Sequential execution**: The way the PL/SQL solutions were written, a query was executed, the results were processed, and then the next query was executed. This sequence was repeated until all work was complete. It would have been nice to be able to do some of this work in parallel. While Oracle does have some options for doing work in parallel, such as [Parallel Execution](http://docs.oracle.com/database/121/DWHSG/schemas.htm#DWHSG9063) and `[DBMS_PARALLEL_EXECUTE](http://docs.oracle.com/database/121/ARPLS/d_parallel_ex.htm#CHDIJACH)`, PL/SQL is, for the most part, a single threaded environment. I could probably have worked some magic to execute the queries and process the results in parallel, perhaps via scheduled jobs or Advanced Queues, but it would have been difficult using PL/SQL.However, this is an area where Node.js shines! Doing work in parallel is quite easy with the the [async](https://github.com/caolan/async) module. In the following solution, I use async's parallel method to fire off three functions at the same time: the first builds the basic department object, the second builds the employees array, and the last builds the `jobHistory` array. The final function, which is fired when all the others have completed, puts the results of the first three functions together into a single object before returning the JSON.

Here's the solution optimized for Node.js:

How fast did that solution finish the test? 7.8 seconds! Not too shabby! That's faster than the PL/JSON solution but not quite as fast as `APEX_JSON`. But could we optimize even further?

## Client Result Caching

Because I was running my tests on Oracle XE, I wasn't able to do a final optimization that would have been possible with the Enterprise Edition of the database: [Client Result Caching](http://docs.oracle.com/database/121/ADFNS/adfns_perf_scale.htm#ADFNS464). With Client Result Caching, Oracle can automatically maintain a cache of the data on the server where Node.js is running. This could have eliminated some round trips and data having to move across the network. I'll revisit this feature in a future post where we can explore it in detail.
