# Using Apache POI to Read Excel

_Captured: 2017-04-21 at 18:31 from [dzone.com](https://dzone.com/articles/using-apache-poi-to-read-excel?oid=twitter&utm_content=buffera327e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Apache POI](https://poi.apache.org/index.html) is a Java library to read and write Microsoft Documents including Word and Excel. [Java Excel API](https://poi.apache.org/spreadsheet/index.html) can read and write Excel 97-2003 XLS files and also Excel 2007+ XLSX files. In this article, we show how to get going using the Apache POI library to work with Excel files.

## Maven Dependency

You need the following maven dependency to work with Apache POI.
    
    
      <version>${poi.version}</version>

## The Basics

Create an Excel 2007 XLSX file by using the class _[XSSFWorkbook](https://poi.apache.org/apidocs/org/apache/poi/xssf/usermodel/XSSFWorkbook.html) _as follows:

To Work with the older Excel 97-2003 XLS format, use the following:

Once you have a _[Workbook](https://poi.apache.org/apidocs/org/apache/poi/ss/usermodel/Workbook.html)_, you can use the interfaces _[Sheet](https://poi.apache.org/apidocs/org/apache/poi/ss/usermodel/Sheet.html)_, _[Row](https://poi.apache.org/apidocs/org/apache/poi/ss/usermodel/Row.html)_, _[Cell](https://poi.apache.org/apidocs/org/apache/poi/ss/usermodel/Cell.html)_, _[CellStyle](https://poi.apache.org/apidocs/org/apache/poi/ss/usermodel/CellStyle.html)_ to avoid tying your application to the version-specific interfaces.

## The First Spreadsheet

Let's say hello to a Hello-World spreadsheet created in Java. The code below creates an Excel spreadsheet with a single sheet named "Population".

The _[WorkbookUtil.createSafeSheetName()](https://poi.apache.org/apidocs/org/apache/poi/ss/util/WorkbookUtil.html#createSafeSheetName%28java.lang.String%29)_ is used since certain characters are invalid in a sheet name. This utility method replaces such characters with the space character.

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xhello-sheet-300x102.png.pagespeed.ic.z_IcO8T9lt.jpg)

## Creating a Row and Cells

A _Row_ object needs to be created inside a sheet before you can fill it with data. A sheet is considered to be comprised of a set or rows. Create a specific numbered row with the call:

Let us now add some cells to this row. This row will serve as the header row since we will add some column titles to the row. There is no such concept of header row in Apache POI or Excel; we just treat the first row as such.

Here is what the sheet looks like after adding the header row:

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xheader-row-300x94.png.pagespeed.ic.DeSgVyAXSx.jpg)

## Auto Sizing Columns

You will notice that the columns are of equal size and some text in the columns is not visible. Wouldn't it be nice to auto-size the columns so all the text is visible? Here is how you can do it. Note that you should do this once just before writing the spreadsheet to a file to avoid having to resize columns when not required.

## Multi-Line Column

In the above code, we might want to split the text in a column into multiple lines. This is not just a matter of inserting a new-line (or a carriage-return-new-line). You need to set the cell style to allow multi-line cells to show the data.

Assume we need to show a header cell in two lines:

Once the data is inserted into the cell, set the cell style to allow wrapping.

After this, the cell data shows multiple lines if required.

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xmulti-line-300x104.png.pagespeed.ic.x3zRp9V0gA.jpg)

## Adding Rows

Let us now add rows in a loop to our spreadsheet. The data we want to add looks like this:

And here is the loop creating each row:

The spreadsheet now looks like this. Notice that we have a few Excel errors: "Number Stored As Text". That is because we are using _[Cell.setCellValue(String)](https://poi.apache.org/apidocs/org/apache/poi/ss/usermodel/Cell.html#setCellValue%28java.lang.String%29)_ method to set the cell value. Let us see how we can fix it.

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xnumber-as-text-300x148.png.pagespeed.ic.YKTuXj1fM5.png)

## Fixing "Number Stored As Text"

The solution is simple. Parse the text value to integer or double and use that to set the value. Pretty simple fix for the `Rank`.

Similarly for the floating point value.

After these changes, the error disappears on the two columns.

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xnumber-as-text-fixed-1-300x138.png.pagespeed.ic.roqzRGjZ3j.jpg)

## Using NumberFormat for Parsing

The fix for the Total field is a bit more involved. The numeric value is formatted with commas for the thousands-separator which we need to parse to obtain the value.

First, we create a _[NumberFormat_](https://docs.oracle.com/javase/8/docs/api/java/text/NumberFormat.html)with the correct Locale. We store the _NumberFormat_ for re-use (without recreating it every time).

We use the _NumberFormat_ for parsing the string value into a double.

With that update, the "Number Stored As Text" error has disappeared.

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xnumber-as-text-fixed-2-300x130.png.pagespeed.ic.2qVnvn0Cr1.jpg)

## Setting Cell Style

However, we would still like to store the number with thousands-separator as before. For this, we need to tell Excel that the number is to be formatted with the correct formatter. This is done by setting the cell style. (The _CellStyle_ is expensive to create and use. It should be created outside the loop and stored for reuse).

After the style is created, we need to set it on the cell.

Now we can see that the numbers are formatted correctly.

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xnumber-as-text-fixed-3-300x127.png.pagespeed.ic.zWlaq5Afpf.jpg)

## Some More Formatting

The last bit of formatting we need is to eliminate the "Number Stored as Text" on the Date column. As you can see, some rows have an integer value and some have a non-numeric value mixed in. We handle that column as follows. Try to parse the value for a number to set it as a number, and if it fails set the value as a string.

Looks like the spreadsheet is now all fixed up. Woo hoo!

![](http://www.novixys.com/blog/wp-content/uploads/2017/02/xnumber-as-text-fixed-4-300x127.png.pagespeed.ic.WpwlzsO3C2.jpg)

## Summary

And that was a beginner introduction to using the Apache POI library to create a spreadsheet. We have just scratched the surface of what the library can do. Hope you learned something useful today.

Stay tuned for the next installment, where we'll show you how to convert CSV to Excel along with more formatting examples.
