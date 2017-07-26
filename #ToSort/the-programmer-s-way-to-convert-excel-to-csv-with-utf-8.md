# The Programmer's Way to Convert Excel to CSV (With UTF-8)

_Captured: 2017-03-22 at 00:16 from [dzone.com](https://dzone.com/articles/the-programmers-way-to-convert-excel-to-csv?edition=286887&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-21)_

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

[CSV ](https://tools.ietf.org/html/rfc4180)stands for Comma-Separated-Values and is a very common format used for exchanging data between diverse applications. While the Excel Spreadsheet file format is complex (since it has to accommodate a lot more!), CSV is a simpler format representing just tabular data.

In this article, we show you a way of exporting the data from an Excel spreadsheet to CSV. We use the Apache POI library for the purpose.

## But Why?

Excel directly provides for exporting CSV data using the **Save As** functionality in the **File** menu. While it gets the job done in most cases, it leaves something to be desired.

Specifically, if your spreadsheet contains Unicode data, you are out of luck. It appears that Excel uses Windows default character set [Windows-1252](https://en.wikipedia.org/wiki/Windows-1252) (or cp-1252) to perform the export. This character set is a very limited set and cannot represent characters from most foreign languages. This leaves your CSV output from Excel severely broken if it contains such characters.

The proper solution is to use Unicode (specifically UTF-8) for encoding the CSV file so all your data is preserved.

It is indeed a surprise that the Excel team has not yet figured out in 2017 that people may have Unicode data that need to be exported properly to CSV.

Maybe the Excel developers have not read [this article by Joel Spolsky](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/) stressing the need for programmers to be aware of Unicode. Ironically, Joel was (until 1995?) the project manager for the Excel team. Joel penned the article in 2003, long after leaving the Excel group.

## Using Apache POI

We use [Apache POI](https://poi.apache.org/) to read the [Excel spreadsheet](https://poi.apache.org/spreadsheet/index.html). Building the program requires this dependency to be declared in pom.xml (assuming Maven for the build) as follows:
    
    
      <version>${poi.version}</version>

## Take 1 - The Naive Approach

The first cut of the approach to convert Excel spreadsheet data to CSV is shown in the block below.
    
    
                if ( ! firstCell ) out.print(',');

## Use the UTF-8 BOM

There are several problems with the code above. While the code above correctly outputs UTF-8 and encodes characters properly, Excel cannot load the generated CSV file. The reason is that Excel needs the [Byte-Order-Marker](https://en.wikipedia.org/wiki/Byte_order_mark) to indicate that the file is encoded in UTF-8. With that modification, the code is now:
    
    
    byte[] bom = {(byte)0xEF, (byte)0xBB, (byte)0xBF};

## Exporting Formulas

When Excel exports CSV, it evaluates all the formulas and writes out the data. In the code below, we have an option of exporting the formula itself (starting with a "`=`") to CSV, or evaluating the formula and exporting the result.

## Escape Quotes and Commas

When exporting a field value, it is necessary to properly escape certain characters such as double quotes, commas, and line separators. This is handled as follows:
    
    
        if ( value.indexOf(',') != -1 || value.indexOf('"') != -1 ||
    
    
             value.indexOf('\n') != -1 || value.indexOf('\r') != -1 )
    
    
        if ( m.find() ) needQuotes = true; value = m.replaceAll("\"\"");
    
    
        if ( needQuotes ) return "\"" + value + "\"";

## Including Empty Rows and Cells

When a formula is exported as-is, it needs the cell references to remain intact. We achieve this by exporting empty rows and cells to CSV to maintain these references.

To ensure that empty rows and cells are also output to CSV, we use row and cell numbers explicitly since the for-each loop shown above skips empty rows and cells.

## Export Specified Sheet Only

If the spreadsheet contains multiple sheets, a sheet number must be explicitly specified for export.

## The Final Cut

The core exporting program segment with all these updates now looks like this.
    
    
    byte[] bom = {(byte)0xEF, (byte)0xBB, (byte)0xBF};
    
    
        for (int r = 0, rn = sheet.getLastRowNum() ; r <= rn ; r++) {
    
    
            if ( row == null ) { out.println(','); continue; }
    
    
            for (int c = 0, cn = row.getLastCellNum() ; c < cn ; c++) {
    
    
                Cell cell = row.getCell(c, Row.MissingCellPolicy.RETURN_BLANK_AS_NULL);
    
    
                if ( ! firstCell ) out.print(',');
    
    
                    if ( fe != null ) cell = fe.evaluateInCell(cell);

## Summary

Exporting data in Excel spreadsheet to CSV is quite simple; it is also provided directly in Excel. However exporting Unicode data within the spreadsheet is not done correctly by Excel. In this article, we covered some issues arising from this process including exporting formulas, maintaining cell references and proper escaping of data.

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
