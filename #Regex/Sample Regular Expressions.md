# Sample Regular Expressions

_Captured: 2016-05-14 at 16:58 from [regular-expressions.mobi](http://regular-expressions.mobi/examples.html)_

**[Collect your own regular expression library](http://www.regexbuddy.com/library.html) with RegexBuddy.**  
RegexBuddy's regular expression library includes all the examples on this website, plus many more. Easily edit any of the regexes or create your own. Build your own personal regular expression library. It'll often come in handy and save you time when searching through files on your computer, writing applications or scripts, or processing text or data. [Get your own copy of RegexBuddy now](http://www.regexbuddy.com/).

Below, you will find many example patterns that you can use for and adapt to your own purposes. Key techniques used in crafting each regex are explained, with links to the corresponding pages in the [tutorial](http://www.regular-expressions.info/tutorial.html) where these concepts and techniques are explained in great detail.

If you are new to regular expressions, you can take a look at these examples to see what is possible. Regular expressions are very powerful. They do take some time to learn. But you will earn back that time quickly when using regular expressions to automate searching or editing tasks in [EditPad Pro](http://www.regular-expressions.info/editpadpro.html) or [PowerGREP](http://www.regular-expressions.info/powergrep.html), or when writing scripts or applications in a [variety of languages](http://www.regular-expressions.info/tools.html).

[RegexBuddy](http://www.regular-expressions.info/regexbuddy.html) offers the fastest way to get up to speed with regular expressions. RegexBuddy will analyze any regular expression and present it to you in a clearly to understand, detailed outline. The outline links to RegexBuddy's regex tutorial (the same one you find on this website), where you can always get in-depth information with a single click.

Oh, and you definitely do not need to be a programmer to take advantage of regular expressions!

## Grabbing HTML Tags

<TAG\b[^>]*>(.*?)</TAG> matches the opening and closing pair of a specific HTML tag. Anything between the tags is captured into the first [backreference](http://www.regular-expressions.info/backref.html). The question mark in the regex makes the star [lazy](http://www.regular-expressions.info/repeat.html), to make sure it stops before the first closing tag rather than before the last, like a greedy star would do. This regex will not properly match tags nested inside themselves, like in <TAG>one<TAG>two</TAG>one</TAG>.

<([A-Z][A-Z0-9]*)\b[^>]*>(.*?)</\1> will match the opening and closing pair of any HTML tag. Be sure to turn off case sensitivity. The key in this solution is the use of the [backreference](http://www.regular-expressions.info/backref.html) \1 in the regex. Anything between the tags is captured into the second backreference. This solution will also not match tags nested in themselves.

## Trimming Whitespace

You can easily trim unnecessary whitespace from the start and the end of a string or the lines in a text file by doing a regex search-and-replace. Search for ^[ \t]+ and replace with nothing to delete leading whitespace (spaces and tabs). Search for [ \t]+$ to trim trailing whitespace. Do both by [combining the regular expressions](http://www.regular-expressions.info/alternation.html) into ^[ \t]+|[ \t]+$. Instead of [ \t] which matches a space or a tab, you can expand the [character class](http://www.regular-expressions.info/charclass.html) into [ \t\r\n] if you also want to strip line breaks. Or you can use the [shorthand](http://www.regular-expressions.info/shorthand.html) \s instead.

## IP Addresses

Matching an IP address is another good example of a trade-off between regex complexity and exactness. \b\d{1,3}\\.\d{1,3}\\.\d{1,3}\\.\d{1,3}\b will match any IP address just fine, but will also match 999.999.999.999 as if it were a valid IP address. Whether this is a problem depends on the files or data you intend to apply the regex to. To restrict all 4 numbers in the IP address to 0..255, you can use the following regex. It stores each of the 4 numbers of the IP address into a [capturing group](http://www.regular-expressions.info/brackets.html). You can use these groups to further process the IP number. [Free-spacing mode](http://www.regular-expressions.info/freespacing.html) allows this to fit the width of the page.

\b(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.  
(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.  
(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.  
(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\b

If you don't need access to the individual numbers, you can shorten the regex with a [quantifier](http://www.regular-expressions.info/repeat.html) to:

\b(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.){3}  
(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\b

Similarly, you can shorten the quick regex to \b(?:\d{1,3}\\.){3}\d{1,3}\b

## More Detailed Examples

[Numeric Ranges](http://www.regular-expressions.info/numericranges.html). Since regular expressions work with text rather than numbers, matching specific numeric ranges requires a bit of extra care.

[Matching a Floating Point Number](http://www.regular-expressions.info/floatingpoint.html). Also illustrates the common mistake of making everything in a regular expression optional.

[Matching an Email Address](http://www.regular-expressions.info/email.html). There's a lot of controversy about what is a proper regex to match email addresses. It's a perfect example showing that you need to know exactly what you're trying to match (and what not), and that there's always a trade-off between regex complexity and accuracy.

[Matching Valid Dates](http://www.regular-expressions.info/dates.html). A regular expression that matches 31-12-1999 but not 31-13-1999.

[Finding or Verifying Credit Card Numbers](http://www.regular-expressions.info/creditcard.html). Validate credit card numbers entered on your order form. Find credit card numbers in documents for a security audit.

[Matching Complete Lines](http://www.regular-expressions.info/completelines.html). Shows how to match complete lines in a text file rather than just the part of the line that satisfies a certain requirement. Also shows how to match lines in which a particular regex does _not_ match.

[Removing Duplicate Lines or Items](http://www.regular-expressions.info/duplicatelines.html). Illustrates simple yet clever use of capturing parentheses or backreferences.

[Regex Examples for Processing Source Code](http://www.regular-expressions.info/examplesprogrammer.html). How to match common programming language syntax such as comments, strings, numbers, etc.

[Two Words Near Each Other](http://www.regular-expressions.info/near.html). Shows how to use a regular expression to emulate the "near" operator that some tools have.

## Common Pitfalls

[Catastrophic Backtracking](http://www.regular-expressions.info/catastrophic.html). If your regular expression seems to take forever, or simply crashes your application, it has likely contracted a case of catastrophic backtracking. The solution is usually to be more specific about what you want to match, so the number of matches the engine has to try doesn't rise exponentially.

[Making Everything Optional](http://www.regular-expressions.info/floatingpoint.html). If all the parts in your regex are optional, it will match a zero-length string anywhere. Your regex will need to express the facts that different parts are optional depending on which parts are present.

[Repeating a Capturing Group vs. Capturing a Repeated Group](http://www.regular-expressions.info/captureall.html). Repeating a capturing group will capture only the last iteration of the group. Capture a repeated group if you want to capture all iterations.

[Mixing Unicode and 8-bit Character Codes](http://www.regular-expressions.info/unicode8bit.html). Using 8-bit character codes like \x80 with a Unicode engine and subject string may give unexpected results.

## Make a Donation

Did this website just save you a trip to the bookstore? Please [make a donation](http://www.regular-expressions.info/donate.html) to support this site, and you'll get a **lifetime of advertisement-free access** to this site! Credit cards, PayPal, and Bitcoin gladly accepted.
