PythonCheatSheet
================

Python 2.7

```python
# coding: utf-8
```

```python
# important built-in types: None, bool (True/False), int, long, float, str, unicode, list, dict, tuple (and some others)
n = 30.5
print str(n)        # 30.5
print str(int(n))   # 30
print str(bool(n))  # True

h = 0xFF
print str(h)        # 255
print chr(65)       # A
print ord("A")      # 65
```

```python
# Compare: ==, <, >, <=, >=, !=
# Bitwise: & (AND), | (OR), ^ (XOR), ~ (COMPLEMENT), << (SHIFT LEFT), >> (SHIFT RIGHT)
# Logical: and, or, not
# Escape Sequence: \\ (\), \r (CR), \n (LF), \' ('), \" ("), \t (TAB), \x41 (A), \u0000 (16bit Unicode), \U00000000 (32bit Unicode)
```

```python
# if, elif, else
b = True
if b == True:     # short form => "if b:"
  print "Yes, it's true."
else:
  print "Did you change the value of b?"
# Yes, it's true.
```

```python
# while
i = 2
while i > 0:
  print str(i) + " > 0"
  i -= 1                    # i = i - 1
# 2 > 0 and 1 > 0
```

```python
# for, in, range()
for i in range(2, 10, 2):   # range(start = 2, stop = 10, step = 2)
  print str(i)
# 2, 4, 6 and 8
```

```python
# break, continue, pass
for i in range(0, 10):      # range(start = 0, stop = 10, step = 1)
  if i == 1:
    pass                    # do nothing
  elif i == 2:
    continue                # don't print 2
  elif i == 5:
    break                   # loop interruption
  print str(i)
# 0, 1, 3 and 4
```

```python
# string[], len()
first_string = "Hello world!"
print first_string            # Hello world!
print str(len(first_string))  # 12 (amount of characters => 0-11)
print first_string[:5]        # Hello (characters 0-4)
print first_string[6:11]      # world (characters 6-10)
print first_string[11:]       # ! (character 11)
```
| H | e | l | l | o |   | w | o | r | l | d | ! | DIRECTION |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | from left |
| -12 | -11 | -10 | -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 | from right |

```python
# string.index(), string.count()
first_string = "Hello world!"
if "w" in first_string:
  a = first_string.index("w")
  print "index of 'w' in first_string"
  print "a  = " + str(a)
if "l" in first_string:
  b = first_string.count("l")
  print "amount of character 'l' = " + str(b)
# index of 'w' in first_string
# a = 6
# amount of character 'l' = 3
```

```python
# list, type()
l = ["This", "is", "my", "list", 1, 2, True, 30.5]
for item in l:
  print str(item) + " [" + type(item).__name__ + "]"
print l[0:-4]
# This [str], is [str], my [str], list [str], 1 [int], 2 [int], True [bool] and 30.5 [float]
# ['This', 'is', 'my', 'list']
```

```python
# list.remove(), .insert(), .append(), .extend(), .sort(), .reverse(), del
la = ["This", "is"]
lb = ["my", "list"]
la.extend(lb)         # la = ["This", "is", "my", "list"]         ### la = la + lb ###
print la
la.remove("list")     # la = ["This", "is", "my"]                 ### del la[3] ###
print la
la.insert(3, "new")   # la = ["This", "is", "my", "new"]          
print la
la.append("list")     # la = ["This", "is", "my", "new", "list"]
print la
la.sort()             # la = ["This", "is", "list", "my", "new"]
print la
la.reverse()          # la = ["new", "my", "list", "is", "This"]
print la
```

```python
# immutable tuple
t = ("This", "is", "a", "tuple")
del t[0]            # TypeError: 'tuple' object doesn't support item deletion
```

```python
# dict
d = { "car" : 100,                      # key : value
      "ship" : 70,
      "plane" : 50}
print "Length of d = " + str(len(d))    # Length of d = 3
for key in d.keys():
  print key                             # car, ship, plane
for value in d.values():
  print value                           # 100, 70, 50
for item in d.items():
  if item[1] == 70:                     # item = tuple = ('key', value)
    print "Found " + item[0]            # Found ship
value = d.get("ship")                   # value = 70 or None if key is missing
```

```python
# string.find() => find all "is" strings in s 
s = "This is my test string which is much longer than this other string."
i = 0                   # start position
l = []                  # empty list
while i != -1:
  i = s.find("is", i)   # i = position or -1
  if i != -1:
    l.append(i)
    i += 1
print l                 # [2, 5, 29, 51]
```

```python
# Regular Expressions
#
# raw_string = r"\"   vs. plain_string = "\\"
# . (any char), [^a] (not a), [A-Z] (A-Z), [A-Za-z] (A-Z and a-z), [0-9] == \d (only digits)
# \s (whitespace chars), [A-Za-z0-9_] == \w
# ? (left char once or never), + (left char once or several times), * (left char not, once or several times)
# {2} (left char have to exist twice), {1,} (left char once or several times), {1,2} (left char have to exist once or twice)
#
import re

s = "This \r\nis \ta -special- string!"
l = re.split(r"[^\w]+", s)              # or re.split(r"[^A-Za-z]+", s)
print l                                 # ['This',  'is',  'a', 'special', 'string', '']
```

```python
# read/write textfile
# see also .readline(), .readlines(), .writelines()
filename = "data.txt"
file = open(filename, 'a')          # append/create file
file.write("A new line in data.\n")
file.close()

file = open(filename, 'r')          # read file
print file.read()                   # A new line in data.\n (every time you start the script a new line is added)
file.close()
```

```python
# read/write binaryfile
# see also .seek(), .tell()
filename = "data.dat"
file = open(filename, 'wb')           # write/create binary file
l = [0,1,2,128,255]
b = bytearray(l)
file.write(b)
file.close()

file = open(filename, 'rb')           # read binary file
s = file.read()
for item in s:
  print int(item.encode('hex'), 16),
  print '= 0x' + item.encode('hex')   # 0 = 0x00 ... 255 = 0xff
file.close()
```

```python
# read/write csvfile
import csv

filename = "data.csv"
file = open(filename, 'wb')                                 # write/create binary file
la = ['column1', 'column2', 'column3', 'column4']
lb = ['text with spaces', '1/1/2016', 4567.12, '12:00:00']
csvwriter = csv.writer(file, delimiter=';')                 # delimiter=',' is default
csvwriter.writerow(la)
csvwriter.writerow(lb)
file.close()

file = open(filename, 'rb')                                 # read binary file
csvreader = csv.reader(file, delimiter=';')                 # delimiter=',' is default
for l in csvreader:
  print l                                                   # ['column1', 'column2', 'column3', 'column4']
                                                            # ['text with spaces', '1/1/2016', '4567.12', '12:00:00']
file.close()
```

```python
# os.getcwd(), .path.expanduser('~'), ...
# see also .uname() and .environ for information about your os
import os

print os.getcwd()                   # current working directory
print os.path.expanduser('~')       # user's HOME directory
print os.listdir('/')               # show root directory (r'C:\' should work for Windows)
print os.path.exists(path)          # True/False if file/directory exists or not (see also os.access())
print os.path.split(path)           # tuple with directory-path and filename
print os.path.getsize(path)         # file size in bytes
```

```python
# sys.version , .path, .exit()
import sys

print sys.version                   # Python version
print sys.path                      # show PYTHONPATH
sys.path.append(path)               # add an additional path
sys.exit()                          # exit the python script (doesn't make sense at the end)
```

```python
# SQLite 3
import sqlite3

sqlcon = sqlite3.connect("test.db")     # sqlite.connect(":memory:") won't be stored
sqlcur = sqlcon.cursor()
sqlcur.execute("CREATE TABLE table1 (id INTEGER PRIMARY KEY, name TEXT, birthday TEXT)")
sqlcur.execute("INSERT INTO table1 (id, name, birthday) VALUES (NULL, 'myname', '2016-01-01')")
sqlcon.commit()
sqlcon.close()

sqlcon = sqlite3.connect("test.db")
sqlcur = sqlcon.cursor()
sqlcur.execute("SELECT * FROM table1")
sqldata = sqlcur.fetchone()             # .fetchone() => get the first record or use .fetchall()
print sqldata
sqlcon.close()

# data types: NULL, INTEGER, REAL, TEXT and BLOB

# Delete all records in table1:
# sqlcur.execute("DELETE FROM table1")
# sqlcon.commit()

# Delete a particular record in table1:
# sqlcur.execute("DELETE FROM table1 WHERE id=0")
# sqlcon.commit()

# Delete whole table1:
# sqlcur.execute("DROP TABLE IF EXISTS table1")
# sqlcon.commit()

# Change data in a particular record in table1:
# sqlcur.execute("UPDATE table1 SET name=? WHERE id=?", (name, id))
# sqlcon.commit()

# Adding a column to a table
# sqlcur.execute("ALTER TABLE table1 ADD COLUMN 'hobby' TEXT")
# sqlcon.commit()

# Working with Variables:
# sqlcur.execute("INSERT INTO table1 VALUES (?, ?, ?)", (var1, var2, var3))
# sqlcur.execute("SELECT name, birthday FROM table1 WHERE id = (?)", (id,))
# sqlcon.commit()

# Find all tables in current database:
# sqlcur.execute("SELECT name FROM sqlite_master WHERE type='table')
# sqldata = sqlcur.fetchall()

# SELECT COUNT(*) FROM table1                                   # how many records are in table1?
# SELECT * FROM table1 JOIN table2 ON table1.id = table2.t1id WHERE name='myname' ORDER BY birthday;
# ORDER BY DESC birthday;                                       # (default:ASC) / DESC (larger values first)
# SELECT name AS nickname, birthday AS bd FROM table1;          # AS define an ALIAS
# SELECT t1.name, t1.birthday FROM table1 as t1;                # ALIAS for table1
# SELECT t1.name, COUNT(*) AS samename FROM table1 as t1 GROUP BY t1.name; # how many users have the same name?
# search for a picture "SQL JOINS" with your favorite search engine
```

```python
if __name__ == '__main__':
    #this code will be ignored if you import the script as module
```

```python
import module            #module.class() or module.methode()
import package.module    #package.module.class() or package.module.methode()
from module import *                    #class() or methode()
from module import methode1, methode2    #methode1() or methode2()
```
