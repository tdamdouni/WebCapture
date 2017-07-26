# Write to a Google Spreadsheet from a Python script

_Captured: 2016-11-20 at 10:40 from [www.mattcutts.com](https://www.mattcutts.com/blog/write-google-spreadsheet-from-python/)_

Suppose you want to write to a Google Spreadsheet from a Python script. Here's an example spreadsheet that you might want to update from a script:

![Example spreadsheet](http://www.mattcutts.com/images/write-to-spreadsheet.png)

I did some searching and found [this page](http://james-says.blogspot.com/2007/07/beginners-guide-for-google-spreadsheet.html), which quickly led me to the [Python Developer's Guide for the Google Spreadsheet API](http://code.google.com/apis/spreadsheets/docs/1.0/developers_guide_python.html).

There's a simple "[Getting started with Gdata and Python"](http://code.google.com/apis/gdata/articles/python_client_lib.html) page. The upshot is 1) make sure you have a recent version of Python (e.g. 2.5 or higher), then 2) install the Google Data Library. The commands I used were pretty much

> mkdir ~/gdata  
(download the [latest Google data Python library](http://code.google.com/p/gdata-python-client/downloads/list) into the ~/gdata directory)  
unzip gdata.py-1.2.4.zip (or whatever version you downloaded)  
sudo ./setup.py install 

That's it. You can test that everything installed fine by running "./tests/run_data_tests.py" to verify that the tests all pass. The program "./samples/docs/docs_example.py" lets you list all of your Google Spreadsheets, for example. An extremely useful program that lets you insert rows right into a spreadsheet is "./samples/spreadsheets/spreadsheetExample.py" and someone has also got a really nice example of [uploading a machine's dynamic IP address](http://ubuntuforums.org/showthread.php?t=1011105) to a spreadsheet.

The most painful thing is that InsertRow() must be called with a spreadsheet key and a worksheet key. If you find out those values, you could hardcode them into the script and probably cut the size of the script in half. Or you could just look in the url to see the key value. That's what I did. So here's an miniature example script to write to a Google Spreadsheet from a Python script:

`  
#!/usr/bin/python`

`import time  
import gdata.spreadsheet.service`

`

email = 'youraccount@gmail.com'  
password = 'yourpassword'  
weight = '180'  
# Find this value in the url with 'key=XXX' and copy XXX below  
spreadsheet_key = 'pRoiw3us3wh1FyEip46wYtW'  
# All spreadsheets have worksheets. I think worksheet #1 by default always  
# has a value of 'od6'  
worksheet_id = 'od6'

spr_client = gdata.spreadsheet.service.SpreadsheetsService()  
spr_client.email = email  
spr_client.password = password  
spr_client.source = 'Example Spreadsheet Writing Application'  
spr_client.ProgrammaticLogin()

# Prepare the dictionary to write  
dict = {}  
dict['date'] = time.strftime('%m/%d/%Y')  
dict['time'] = time.strftime('%H:%M:%S')  
dict['weight'] = weight  
print dict

`

`entry = spr_client.InsertRow(dict, spreadsheet_key, worksheet_id)  
if isinstance(entry, gdata.spreadsheet.SpreadsheetsList):  
  print "Insert row succeeded."  
else:  
  print "Insert row failed."  
`

That's it. Run the script to append a new row to the current spreadsheet. By the way, if you make a chart from the spreadsheet data, you can right-click on the chart, select "Publish chart…" from the menu, and get a snippet of HTML to copy/paste that will embed the chart on a web page. It will look like this:

That's a live image served up by Google, and when the spreadsheet gets new data, the image should update too.
