# Diagram to show Java String’s Immutability

_Captured: 2015-11-22 at 13:27 from [www.programcreek.com](http://www.programcreek.com/2009/02/diagram-to-show-java-strings-immutability/)_

Here are a set of diagrams to illustrate Java String's _immutability_.

**1\. Declare a string**

s stores the reference of the string object. The arrow below should be interpreted as "store reference of".

![String-Immutability-1](http://www.programcreek.com/wp-content/uploads/2009/02/String-Immutability-1.jpeg)

**2\. Assign one string variable to another string variable**

s2 stores the same reference value, since it is the same string object.

![String-Immutability-2](http://www.programcreek.com/wp-content/uploads/2009/02/String-Immutability-2.jpeg)

**3\. Concat string**

s now stores the reference of newly created string object.

![string-immutability](http://www.programcreek.com/wp-content/uploads/2009/02/string-immutability-650x279.jpeg)

**Summary**

Once a string is created in [memory](http://www.programcreek.com/2013/04/jvm-run-time-data-areas/)(heap), it can not be changed. We should note that all methods of String do not change the string itself, but rather return a new String.

If we need a string that can be modified, we will need StringBuffer or StringBuilder. Otherwise, there would be a lot of time wasted for Garbage Collection, since each time a new String is created. [Here](http://www.programcreek.com/2011/11/java-read-file-into-a-string/) is an example of StringBuilder usage.
