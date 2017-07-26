# Python read data from MySQL database

_Captured: 2015-11-22 at 13:49 from [www.programcreek.com](http://www.programcreek.com/2014/02/python-read-data-from-mysql-database/)_

The following code can read data from MySQL database.
    
    
    import MySQLdb
     
    # Open database connection
    db = MySQLdb.connect("localhost","username","password","DBName")
     
    # prepare a cursor object using cursor  method
    cursor = db.cursor() 
     
    sql = "select * from table1"
    cursor.execute(sql)
    results = cursor.fetchall() 
    for row in results:
        print row[0]
     
    # disconnect from server
    db.close()

Category >> [Python](http://www.programcreek.com/category/programming-languages/python/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
