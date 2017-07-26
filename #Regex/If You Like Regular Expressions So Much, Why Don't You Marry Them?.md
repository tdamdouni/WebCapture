# If You Like Regular Expressions So Much, Why Don't You Marry Them?

_Captured: 2015-12-11 at 10:05 from [blog.codinghorror.com](http://blog.codinghorror.com/if-you-like-regular-expressions-so-much-why-dont-you-marry-them/)_

[All right... _I will!_](http://www.x-entertainment.com/messages/509.html)

![Pee-Wee likes fruit salad so much, he married it](http://blog.codinghorror.com/content/images/uploads/2005/03/6a0120a85dcdae970b0168ea1266b4970c-800wi.jpg)

> _[Pee-Wee likes fruit salad so much, he married it](http://www.youtube.com/watch?v=Bs81piYG2G8)_

I'm continually amazed how useful regular expressions are in my daily coding. I'm still working on the MhtBuilder refactoring, and I needed a function to convert all URLs in a page of HTML from relative to absolute:
    
    
    ''' <summary>
    ''' converts all relative url references
    '''    href="myfolder/mypage.htm"
    ''' into absolute url references
    '''    href="http://mywebsite/myfolder/mypage.htm"
    ''' </summary>
    Private Function ConvertRelativeToAbsoluteRefs(ByVal html As String) As String
    Dim r As Regex
    Dim urlPattern As String = _
    "(?<attrib>shref|ssrc|sbackground)s*?=s*?" & _
    "(?<delim1>[""']{0,2})(?!#|http|ftp|mailto|javascript)" & _
    "/(?<url>[^""'>]+)(?<delim2>[""']{0,2})"
    Dim cssPattern As String = _
    "@imports+?(url)*['""(]{1,2}" & _
    "(?!http)s*/(?<url>[^""')]+)['"")]{1,2}"
    '-- href="/anything" to href="http://www.web.com/anything"
    r = New Regex(urlPattern, _
    RegexOptions.IgnoreCase Or RegexOptions.Multiline)
    html = r.Replace(html, "${attrib}=${delim1}" & _HtmlFile.UrlRoot & "/${url}${delim2}")
    '-- href="anything" to href="http://www.web.com/folder/anything"
    r = New Regex(urlPattern.Replace("/", ""), _
    RegexOptions.IgnoreCase Or RegexOptions.Multiline)
    html = r.Replace(html, "${attrib}=${delim1}" & _HtmlFile.UrlFolder & "/${url}${delim2}")
    '-- @import(/anything) to @import url(http://www.web.com/anything)
    r = New Regex(cssPattern, _
    RegexOptions.IgnoreCase Or RegexOptions.Multiline)
    html = r.Replace(html, "@import url(" & _HtmlFile.UrlRoot & "/${url})")
    '-- @import(anything) to @import url(http://www.web.com/folder/anything)
    r = New Regex(cssPattern.Replace("/", ""), _
    RegexOptions.IgnoreCase Or RegexOptions.Multiline)
    html = r.Replace(html, "@import url(" & _HtmlFile.UrlFolder & "/${url})")
    Return html
    End Function
    

Each regex is repeated because I have to resolve relative URLs starting with forward slashes to the webroot first--and then all remaining relative URLs to the current web folder.

One of the BCL team recently [recommended pretty-printing regular expressions](http://blogs.msdn.com/bclteam/archive/2005/03/15/396450.aspx), eg, using whitespace to make regexes more readable with **RegexOptions.IgnorePatternWhitespace**. I agree completely. We do this all the time with SQL. I can think of a half-dozen tools that will block of SQL and pretty format it-- but I am not aware of any regex tools that offer this functionality. I guess I'll email the author of [Regexbuddy](http://www.regexbuddy.com/cgi-bin/affref.pl?aff=jatwood) and see what he has to say.

And here's an interesting bit of trivia: did you know that [the ASP.NET page parser uses regular expressions?](http://weblogs.asp.net/cazzu/archive/2005/01/10/RegexParsing.aspx)
