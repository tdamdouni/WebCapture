# Comparing Unsorted (Unordered) Whitespace in Different XML Files

_Captured: 2017-06-25 at 19:21 from [dzone.com](https://dzone.com/articles/compare-unsorted-unordered-whitespace-different-xm?edition=305136&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-25)_

[Bitbucket](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Many developers struggle to compare XML files. There are a number of reasons for that, including:

  * Whitespace differences

  * Unordered

  * Comment differences

CData differences can cause different results.

Most of the time, developers try to convert XML into Strings to do the comparison. If this is for unit testing, performance may not be an issue. But again, if the format is different or whitespace/comments are different, then the test will fail -- and that is a false failure.

[XMLUnit](http://www.xmlunit.org/) is the solution for this. The following example will demonstrate how you can compare unsorted XML files even with whitespaces.

Maven dependencies:

Java class:
    
    
        public static void main(String[] args) throws IOException, SAXException {
    
    
        private static void xmlComparator(String expectedXmlFilePath, String currentXmlFilePath) throws SAXException, IOException {
    
    
            DetailedDiff detailedDiff = new DetailedDiff(new Diff(expected, current));
    
    
                System.out.println(i.next().toString());
    
    
            System.out.println("================== if soarting issues are ignored =============================");

Target xml file (expected)
    
    
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
    
    
            <loc>http://www.krishantha.net/</loc>
    
    
            <loc>http://www.krishantha.net/tag/multi-root-xml/</loc>
    
    
            <loc>http://www.krishantha.net/tag/oauth/</loc>
    
    
            <loc>http://www.krishantha.net/tag/payload/</loc>

Source XML file:
    
    
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
    
    
            <loc>http://www.krishantha.net/</loc>
    
    
            <loc>http://www.krishantha.net/tag/multi-root-xml/</loc>
    
    
            <loc>http://www.krishantha.net/tag/oauth/</loc>
    
    
            <loc>http://www.krishantha.net/tag/payload/</loc>

When you execute, you'll see there are no failures. But if you made any changes (content) to either XML file, you will see a fail on assert.

If you'd like to play around more with this, a sample project can be [downloaded here](https://github.com/krishantha/code-samples/tree/master/xmlDif).

[Bitbucket is the Git solution](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
