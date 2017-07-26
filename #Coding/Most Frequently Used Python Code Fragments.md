# Most Frequently Used Python Code Fragments

_Captured: 2015-12-04 at 01:44 from [www.programcreek.com](http://www.programcreek.com/2015/05/most-frequently-used-python-code-fragments-for-java-developers/)_

The syntax of Python may seem strange at first for Java developers. There are some python code fragments that are used very often, but these code fragments are not easy to remember for new programmers. Those frequently used code fragments are call "code idioms". Reading the code idioms of a programming language is often helpful, or even a shortcut, for learning a new programming language. 

The intent of this post is to list some of the most commonly used Python code idioms, in the hope that it will provide useful recommendations for other programmers (especially beginners). Remember that in addition to the listings below, there are other frequently used Python code fragments. You may also want to check you [the most popular 3000 python modules](http://www.programcreek.com/python/index/module/list). 

*Note: The order does not reflect each code idiom's frequency.

**# Filter a list**

    
    
    #filter out empty strings in a sting list
    list = [x for x in list if x.strip()!='']

**# Read file line by line**

    
    
    with open("/path/to/file") as f:
        for line in f:
            print line

**# Write file line by line**

    
    
    f = open("/path/tofile", 'w')
    for e in aList:
        f.write(e + "\n")
    f.close()

**# Regular expression finding**

    
    
    sentence = "this is a test, not testing."
    it = re.finditer('\\btest\\b', sentence)
    for match in it:
        print "match position: " + str(match.start()) +"-"+ str(match.end())

**# Regular expression search**

    
    
    m = re.search('\d+-\d+', line) #search 123-123 like strings
    if m:
        current = m.group(0)

**# Query database**

    
    
    db = MySQLdb.connect("localhost","username","password","dbname")
    cursor = db.cursor()
    sql = "select Column1,Column2 from Table1"
    cursor.execute(sql)
    results = cursor.fetchall()
     
    for row in results:
        print row[0]+row[1]
     
    db.close()

**# Connet a list with a specified separator**

    
    
    theList = ["a","b","c"]
    joinedString = ",".join(theList)

**# Filter out duplicate elements**

    
    
    targetList = list(set(targetList))

**# Filter out empty strings from a list of strings**

    
    
    targetList = [v for v in targetList if not v.strip()=='']
    # or
    targetList = filter(lambda x: len(x)>0, targetList)

**# Add a list to another list**

    
    
    anotherList.extend(aList)

**# Iterate a dictionary**

    
    
    for k,v in aDict.iteritems():
        print k+v

**# Check if any element of a string list appears in a target string**

    
    
    if any(x in targetString for x in aList):
        print "true"

Apparently, not all Python code idioms are shown above. I would appreciate if you can add more in your comment. 

If you are a Java programmer, and you are totally new to Python, I recommend you read the the following:

  * [Java vs. Python (1)](http://www.programcreek.com/2012/04/java-vs-python-why-python-can-be-more-productive/)
  * [Java vs. Python (2)](http://www.programcreek.com/2012/09/java-vs-python-data-types/)

### You may also like ...

  1. [Python read data from MySQL database ](http://www.programcreek.com/2014/02/python-read-data-from-mysql-database/)
  2. [Java vs. Python (1): Simple Code Examples ](http://www.programcreek.com/2012/04/java-vs-python-why-python-can-be-more-productive/)
  3. [Python read file line by line ](http://www.programcreek.com/2014/02/python-read-file-line-by-line/)
  4. [Java vs. Python (2): Data Types ](http://www.programcreek.com/2012/09/java-vs-python-data-types/)

