# Transform HTML with Regular Expressions

_Captured: 2016-12-22 at 13:45 from [www.macworld.com](http://www.macworld.com/article/1027276/regex.html)_

![](http://images.techhive.com/images/article/2012/10/bbeditgrep_58-100007912-large.jpg)

Creating Web pages can be an exciting experience; after all, the Web is on the cutting edge when it comes to publishing technology. But when you have to update dozens of lines of code manually to make a minor design change, working with HTML can be infuriatingly tedious.

But making global changes to your code doesn't have to be time-consuming, if you use _regular expressions_ . This special search-and-replace feature (often called _pattern matching_ or _grep_ ) is built into most HTML editors, including Bare Bones Software's BBEdit and Macromedia's Dreamweaver. Regular expressions amplify the power of traditional search-and-replace commands by letting you search for _patterns_ of text and then selectively modify what you've found. That added power makes regular expressions a great tool for modifying HTML files quickly and painlessly.

To take advantage of this power, you have to learn the symbols used to build searches (see the table, "Decoding Regular Expressions," for a partial list). Regular expressions look incomprehensible at first glance, but once you learn a few rules, they'll save you hours of work.

## Decoding Regular Expressions

Symbol What It Means Example What It Might Find

+
find 1 or more of preceding item
ta+
ta, taa, taaa

*
find 0 or more of preceding item
ba*
b, ba, baa, baaa

?
preceding item is optional
ab?c
abc, ac

.
match any character (except return)
1.2
1 2, 122, 1d2, 1$2

[^x]
match any character except x
us[^a]
usb, usc, usd, use

[0-9]
match any digit
9021[0-9]
90210 through 90219

^
match start of line
^hello
matches hello only at beginning of line

$
match end of line
end$
matches end only at end of line

( )
group items together
(ab)+
ab, abab, ababab

Regular expressions are powerful because they let you search for dozens of permutations of text with a single trip to a Find window. For example, you could search for any _&#60;font&#62;_ tag and find _&#60;font&#62;_ , _&#60;font face="Helvetica"&#62;_ , or even _&#60;font size="+2" face="Arial,Helvetica" color="#990000"&#62;_ . Once you've found text, you can perform tricks such as changing the order of the text or inserting text within a found item.

A regular-expression search is like a normal search: you enter some text, and the program tries to find text that matches it. What makes regular expressions so powerful is that you can use wild-card characters to match all sorts of patterns in addition to exact text strings.

Say you want to search for a word that can be spelled various ways. For example, if you search for
    
    
    color

, you'll find every instance of _color_ . But if you search for
    
    
    colou?r

, you'll find all occurrences of both _color_ and _colour_ . That's because the question mark means that the character immediately preceding it is optionalin other words, the expression will accept a _u_ if it finds one, but it doesn't need to find one.

The plus sign and asterisk, cousins to the question mark, find repeating text rather than optional text. Because the plus sign finds one or more of the same character, searching for
    
    
    90+

matches _90, 900, and 9000,_ for instance, but not _9_ . The asterisk finds zero or more characters, so searching for
    
    
    90*

will match _9, 90, 900,_ and so on.

When you start crafting regular expressions, you may experience unexpected results. Chances are good that the problem involves the asterisk or the plus sign, which are quite powerful but also greedy: they try to match the largest amount of text possible. Avoid searching for open-ended expressions such as
    
    
    .*

or
    
    
    .+

which find as much of any character (signified by the period symbol) as possibleand target your expressions at specific characters.

One powerful feature of regular expressions involves text in brackets. The text inside the brackets is sort of a do-it-yourself wild card:
    
    
    [0-9]

will match any numeral, and
    
    
    [aeiou]

will match any vowel. You can put brackets around either a "run" of characters (say, from A to J or 1 to 5) or a list of individual characters. For example, if you want to match only _1, 2,_ or _3,_ you can search for either
    
    
    [1-3]

or
    
    
    [123]

they mean the same thing. If you search for
    
    
    gr[ea]y

, you'll find all instances of both _gray_ and _grey_ .

An even more powerful use of brackets involves excluding characters from the search. If you insert a caret (^) in the bracketed item, your search will exclude words that contain the character following the caret. For example, a search for
    
    
    hell[^]*

will match any word that starts with _hell_ , such as _hello, hellacious,_ and even _hell-on-wheels_ . By searching for any character except a space, you've limited your search to single words.

Symbols that search for repeating characters are powerful, but they affect only the item they followand how often do you have to find eight repetitions of a letter? However, you can get those symbols to match entire groups of characters by using parentheses.

Parentheses have two important uses in regular expressions. First, you can surround anything with parentheses to make the contents a single "item" for use with wild cards. For example, a search for
    
    
    (hedge)?hog

would match both _hedgehog_ and _hog_ , since the question mark makes the item preceding it, _hedge_ , optional.

Even more important, parentheses let you save what you've found so you can use it when you're replacing text. When you put any item in parentheses, any text the expression matches is automatically stored for later use. Each set of parentheses is assigned a number, starting with 1 for the first set. When it comes time to insert that stored text into your replacement text, you refer to it using a backslash () followed by the appropriate number. In the previous example,

would contain _hedge_ if the expression matched the word _hedgehog_ , and nothing if the expression matched only _hog_ .

Here's another example: a search for
    
    
    <img src="([^"]+)">

will match a plain HTML
    
    
    <img>

tag; the name of that image, which lies between those parentheses, will now be the contents of
    
    
    \\1

. Say you want to use this expression to replace an existing
    
    
    <img>

tag with one that lists the name of the file in the image's _alt_ (alternative text) variable. All you need to do is enter
    
    
    <img src="1" alt="\\1">

in the Replace box to quickly replace items such as
    
    
    <img src="jason.gif">

with
    
    
    <img src="jason.gif" alt="jason.gif">

throughout your document.

What if you want to search for a character that's part of the regular expression? Just put a backslash (\\\\) in front of it. A search for
    
    
    1

\+ will match _11, 111,_ and so on, but a search for
    
    
    \\|\\+

will find only _|+_ .

One of the Web sites I manage features articles submitted via e-mail. Once I get that mail, I have to convert it to HTML before posting it online. Since most of the writers use underscores to represent emphasized text, I have to convert all underscored text to some sort of HTML style. Rather than deleting underscores and replacing them with HTML tags by hand, I let a regular expression handle it.

The expression in question is
    
    
    _([^_]+)_

, or, to translate: find an underscore, followed by one or more characters that aren't underscore, followed by another underscore, saving the text between the underscores for later use by placing it in parentheses. Here, I've chosen to give that emphasized text the royal treatment, making it bold, brightly colored, and several point sizes larger and styling it in a different font. I do this with the following replacement expression:
    
    
    <font face="Arial,Helvetica" size="+2" color="#660000"><b>\\1</b></font>

In real life, I usually just italicize the text with the expression
    
    
    <i>\\1</i>

.

Regular expressions are great for converting preformatted text into a different format. Let's say someone gives you a tab-delimited text file containing items you need to place in an HTML table. On each line are three items: a name, a URL, and a description. You could convert that file into a table by hand, but a regular expression can do it in a flash: just search for
    
    
    (^([^t]*)t([^t]*)t([^t]*)$

and replace it with
    
    
    <tr><td><a href="\\2">1</a></td><d>3</td></tr>

. The result is a search-and-replace action that takes each line of a three-field, tab-delimited text file and converts it into one row of an HTML table. Just add
    
    
    <table>

and
    
    
    </table>

tags.

Let's break down this expression. The first caret indicates that you're finding only items that start at the beginning of a line. It's followed by
    
    
    ([^*t]*)

, which finds as many characters as it can, as long as they aren't tabs (
    
    
    t

is shorthand for the tab character). Since it's all within parentheses, the results will be stored in a variable for use when you replace the found text. Next is a tab, another group of as many characters as possible that aren't tabs, another tab, and another group of as many characters as possible, up to the dollar signthe end of the line.

What this expression does is grab all three collections of text located between the tabs of your tab-delimited text file and store them as variables by using parentheses. You can then use the
    
    
    1, 2,

and variables in your Replace box as placeholders for the found contents of the first, second, and third tab-delimited fields. You don't have to use those fields in order, either. Since the name field came before the URL field in this example's original text, the former is stored in that's why , the URL field, appears before in this example.

Regular expressions can be extremely powerfuland extremely complicated. If you're interested in learning more, there's no better resource than Jeffrey E. F. Friedl's _ [Mastering Regular Expressions Second Edition](http://www.oreilly.com/catalog/regex2/) _ (O'Reilly and Associates). It's a great source of sample expressions and detailed explanations of how regular expressions work their magic.

  


  * Get the latest technology for the car you already own with Pioneer Electronics. Pioneer offers in-vehicle smartphone technology, convenient safety packages and cutting-edge music sources for the ultimate entertainment experience.
  * Test your Mac's common problem areas including hard drive, system errors, and memory.
  * Use our exclusive benchmarking tool to compare your cloud investment and deployment plans with your peers.
  * Monitor your peering & transit from key ISPs to ensure that you have the connectivity you require.
  * Protect PCs, Macs, & Smartphones with IDrive - All your devices for $5.95 the first year!
  * Pinpoint network problems, hop-by-hop, across all enterprise and service provider networks. Try it free!
