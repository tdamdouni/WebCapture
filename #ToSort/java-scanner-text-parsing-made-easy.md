# Java Scanner: Text Parsing Made Easy

_Captured: 2017-02-22 at 19:07 from [dzone.com](https://dzone.com/articles/java-scanner-text-parsing-made-easy?edition=271915&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-22)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

> "The only way of discovering the limits of the possible is to venture a little way past them into the impossible."  
― Arthur C. Clarke

Java provides a _[Scanner_ ](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)class that can be used as a text parser. It accepts a regular expression as a delimiter and returns tokens separated by the delimiter. Let us look at some usage scenarios of the _Scanner_ class.

![Image title](http://www.novixys.com/blog/wp-content/uploads/2017/02/search-for-importer_600.jpg)

## Count Words in a File

The default delimiter used by the _Scanner_ is whitespace. It returns text tokens separated by whitespace. Let us use this fact to count the words in a file. The following code prints the value as well as its index from the file. Note that the Scanner implements the _[AutoCloseable](https://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html)_ interface so we can use it in [try-with-resources](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) block.
    
    
    try (Scanner scanner = new Scanner(new File(filename));) {
    
    
        System.out.printf("%3d) %s%n", nword, sent);

Specifying an empty-line regex as the delimiter allows you to read text by paragraphs. The regular expression pattern specifies the multi-line flag, so use `^` and `$` match at the beginning and end of each line, rather than the whole input.
    
    
    try (Scanner scanner = new Scanner(new File(filename));) {
    
    
        System.out.printf("%3d) %s%n", ntoken, token);

## Scanner Trick: Read a Whole File

To read the whole file in a single String, use the following. The delimiter here is the regular expression for the beginning of the file.
    
    
    try (Scanner scanner = new Scanner(new File(filename));) {

The Java class Scanner is used for text parsing. By setting the delimiter appropriately, various parsing tasks can be accomplished.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
