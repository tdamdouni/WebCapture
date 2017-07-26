# How to Convert CSV to JSON in Java

_Captured: 2017-03-14 at 18:42 from [dzone.com](https://dzone.com/articles/how-to-convert-csv-to-json-in-java?edition=283881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-14)_

CSV to JSON conversion is easy. In this article, we present a couple of methods to parse [CSV ](https://tools.ietf.org/html/rfc4180)data and convert it to [JSON](http://www.json.org/). The first method defines a POJO and uses simple string splitting to convert CSV data to a POJO, which, in turn, is serialized to JSON. The second method uses a more complete CSV parser with support for quoted fields and commas embedded within fields. In this method, we use the Java Collection classes to store the parsed data and convert those to JSON.

We use [Jackson ](http://wiki.fasterxml.com/JacksonHome)for the JSON conversion.

![CSV data](http://www.novixys.com/blog/wp-content/uploads/2017/02/xfinancial-report_800x350.jpg.pagespeed.ic.dGgsXzufOm.jpg)

## Simple CSV Parsing

When the CSV file to be parsed is simple (there are no quoted fields or commas embedded in fields), you can use a simple pattern matcher to split the CSV fields.

## POJO Definition

We are going to parse the CSV data and create the POJO (Plain-Old-Java-Object) shown in this definition.
    
    
        public Player(int year, String teamId, String leagueId, String playerId, int salary) {

## Reading the CSV Data

Open the CSV file using a _[BufferedReader](https://docs.oracle.com/javase/8/docs/api/java/io/BufferedReader.html) _in a try-with-resources block.
    
    
    try (BufferedReader in = new BufferedReader(new FileReader(csvFile));) {

Create the List of POJOs using a streaming pipeline. The first line is skipped because it is the CSV header. The line is split into fields using the [Pattern](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html), converted to appropriate types and used to create the object.

## Serialize to JSON

Once the _[List](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) _is ready, use Jackson's _[ObjectMapper ](https://fasterxml.github.io/jackson-databind/javadoc/2.6/com/fasterxml/jackson/databind/ObjectMapper.html)_to write the JSON. Check for full details on JSON serialization and deserialization.

And here is the whole programs segment.

## CSV to JSON Conversion (No POJO)

In this example, we use the CSV parser presented in [this article](http://www.novixys.com/blog/howto-read-csv-file-java/). This CSV parser can handle multi-line quoted fields and commas embedded within fields, just like Excel can. It uses the first line of the CSV file as field names and loads the data into a _List_, which is then exported to JSON.

Here is the complete segment.

Here is a part of the CSV data that was converted:

Notice that one of the fields in the data is quoted because of embedded commas. Here is the converted JSON for that record, which shows that the record has been parsed and converted correctly.

## Summary

CSV data can be converted to JSON via a POJO using Jackson. If a POJO is not already defined or required, you can always use the Java Collection classes to store parsed data and later convert it to JSON.
