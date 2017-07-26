# 35+ Examples of Regex Patterns Using sed and awk in Linux

_Captured: 2017-02-28 at 11:29 from [dzone.com](https://dzone.com/articles/35-examples-of-regex-patterns-using-sed-and-awk-in?edition=271921&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-27)_

Make the transition to Node.js if you are a Java, PHP, Rails or .NET developer with [these resources to help jumpstart your Node.js knowledge](https://dzone.com/go?i=182121&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127833%26PluID%3D0%26ord%3D%5Btimestamp%5D) plus pick up some development tips. Brought to you in partnership with [IBM](https://dzone.com/go?i=182121&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127833%26PluID%3D0%26ord%3D%5Btimestamp%5D).

In order to successfully work with the [Linux sed](https://likegeeks.com/sed-linux/) editor and the [awk command](https://likegeeks.com/awk-command/) in your shell scripts you have to understand regular expressions, or regex for short (and to be accurate in our case, it is bash regex). Though there are many engines for regex you can use, I've decided to that in this tutorial we will use the shell regex, so you can see bash working with regex.

First, we need to understand what regex is, then we will dive deep into using it.

## **Our Main Points Are:**

1\. What is regex?

2\. Types of regex.

3\. Define BRE Patterns.

4\. Special characters.

5\. Anchor characters.

6\. The dot character.

7\. Character classes.

8\. Negating character classes.

9\. Using ranges.

10\. Special character classes.

11\. The asterisk.

12\. Extended Regular Expressions.

13\. Grouping expressions.

14\. Practical examples.

## What is Regex

For some people, when they see regular expressions for the first time they say, 'what are those ASCII buggers! Well, a regular expression, or regex, in general, is a pattern of text you define that a Linux program (in our case) like sed or awk uses to filter text.

The regex pattern makes use of wildcard characters to represent one or more characters in the data stream. We've seen some of those wildcard characters when introducing basic Linux commands and see how ls commands use wildcard characters to filter output.

## Types of Regex

There are many different applications that use different types of regex in Linux. These include programming languages (Java, Perl, Python) and Linux programs like (sed, awk, grep) and many other applications.

A regex is implemented using a regular expression engine_. _A regular expression engine is an underlying software that interprets regular expression patterns and uses those patterns to match the text.

Linux has two regular expression engines:

  * The **POSIX Basic Regular Expression (BRE)** engine
  * The** POSIX Extended Regular Expression (ERE)** engine

Most Linux programs at a minimum conform to the POSIX BRE engine specifications, recognizing all the pattern symbols it defines. Unfortunately, some utilities (such as the sed) conform only to a subset of the BRE engine specifications. This is due to speed constraints because the sed attempts to process text as quickly as possible.

The POSIX ERE engine is often found in programming languages. It provides advanced pattern symbols as well as special symbols for common patterns, such as matching digits and words. The awk command uses the ERE engine to process its regular expression patterns.

And because there are so many different ways to implement regex, it's hard to write patterns that work on all engines. Hence we will focus on the most commonly found regex and demonstrate how to use them in the sed and awk.

## Define BRE Patterns

The most basic BRE pattern is matching text characters in a data stream, and we've seen that using sed and awk, but let's refresh our memory.

$ echo "This is a test" | sed -n '/test/p'

$ echo "This is a test" | awk '/test/{print $0}'

![regex tutorial](https://likegeeks.com/wp-content/uploads/2017/02/01-regex-tutorial.png)

![regex awk example](https://likegeeks.com/wp-content/uploads/2017/02/02-regex-awk-example.png)

You may notice that the regex doesn't care where in the data stream the pattern occurs. It also doesn't matter how many times the pattern occurs. After the regex can match the pattern anywhere in the text string, it passes the string along to the Linux program that's using it.

The first rule to remember is that regular expression patterns are case sensitive.

$ echo "This is a test" | awk '/Test/{print $0}'

$ echo "This is a test" | awk '/test/{print $0}'

![regex character case](https://likegeeks.com/wp-content/uploads/2017/02/03-regex-character-case.png)

The first regex found no match because the word "this" doesn't appear in uppercase in the text string, while the second line, which uses the lowercase letters in the pattern, worked just fine

You also don't have to limit yourself to single text words in the regular expression. You can include spaces and numbers in your text string as well.

$ echo "This is a test 2 again" | awk '/test 2/{print $0}'

![regex space character](https://likegeeks.com/wp-content/uploads/2017/02/04-regex-space-character.png)

> _Spaces are treated just like any other character in regex._

## Special Characters

There are a few exceptions when defining text characters in a regex. Regex patterns assign a special meaning to a few characters. If you try to use these characters in your text pattern, you won't get the results you were expecting.

The following special characters are recognized by regex:

.*[]^${}\\+?|()

If you want to use one of the special characters as a text character, you need to escape it. The special character that does this is the backslash character (\\). For example, if you want to search for a dollar sign in your text, just precede it with a backslash character like this:

![regex dollar sign](https://likegeeks.com/wp-content/uploads/2017/02/05-regex-dollar-sign.png)

Also, backslash itself is a special character, so if you need to use it in a regex pattern, you need to escape it as well, producing a double backslash.

![regex special character](https://likegeeks.com/wp-content/uploads/2017/02/06-regex-special-character.png)

Although the forward slash isn't a regular expression special character, so if you use it in your regular expression pattern in the sed or the awk, you get an error.

![regex slash](https://likegeeks.com/wp-content/uploads/2017/02/07-regex-slash.png)

So you need to escape it like this:

![regex escape slash](https://likegeeks.com/wp-content/uploads/2017/02/08-regex-escape-slash.png)

## Anchor Characters

You can use two special characters to anchor a pattern to either the beginning or the end of lines in the text. The caret character (^) defines a pattern that starts at the beginning of a line of text, in the text. If the pattern is located at any place other than the start of the line of text, the regex pattern fails.

You can use it like this:

![regex anchor begin character](https://likegeeks.com/wp-content/uploads/2017/02/09-regex-anchor-begin-character.png)

> _The caret anchor character checks for the pattern at the beginning of each new line of data._

![regex caret anchor](https://likegeeks.com/wp-content/uploads/2017/02/10-regex-caret-anchor.png)

Great!! When using sed, if you position the caret character in any place other than at the beginning of the pattern, it acts like a normal character and not as a special character.

![regex caret character](https://likegeeks.com/wp-content/uploads/2017/02/11-regex-caret-character.png)

But if you use awk you have to escape it like this:

![regex escape caret](https://likegeeks.com/wp-content/uploads/2017/02/12-regex-escape-caret.png)

> _The above code pertains to the beginning of the text, but what about looking at the end?_

The dollar sign ($) special character defines the end anchor:

![regex end anchor](https://likegeeks.com/wp-content/uploads/2017/02/13-regex-end-anchor.png)

> _You can combine both the start and end anchor on the same line like this:_

![regex combine anchors](https://likegeeks.com/wp-content/uploads/2017/02/14-regex-combine-anchors.png)

> _As you can see, it prints only the line that has the matching pattern._

You can filter blank lines with the following pattern:

Here we introduce the negation which is done by the exclamation mark (!).

The pattern looks for lines that have nothing between the start and end of the line and negates that to print only the lines that have text.

## The Dot Character

The dot character is used to match any single character except a newline character.

Look at the following example to get the idea:

![regex dot character](https://likegeeks.com/wp-content/uploads/2017/02/15-regex-dot-character.png)

You can see from the result that it prints only the first two lines because they contain the _st_ pattern while the third line does not have that pattern, and the fourth line starts with _st_ so that also doesn't match our pattern.

## Character Classes

You can match any character with the dot special character, but what if you want to limit what characters to match? This is called a character class.

You can define a set of characters that would match a position in a text pattern. If one of the characters from the character set is in the text, it matches the pattern.

To define a character class, you use square brackets [] like this:

![regex character classes](https://likegeeks.com/wp-content/uploads/2017/02/16-regex-character-classes.png)

> _Here we search for any th character that has the characters, o or I, before it._

This comes in handy when you are searching for words that may contain upper or lower case letters, and you are not sure about that.

![regex upper and lower case](https://likegeeks.com/wp-content/uploads/2017/02/17-regex-upper-and-lower-case.png)

Of course, it is not limited to characters; you can use numbers or whatever you want. You can employ it as you want as long as you got the idea.

## Negating Character Classes

You can also reverse the effect of a character class. Instead of looking for a character contained in the class, you can look for any character that's not in the class. To do that, just place a caret character at the beginning of the character class range.

![regex negate character classes](https://likegeeks.com/wp-content/uploads/2017/02/18-regex-negate-character-classes.png)

> _By negating the character class, the regex pattern matches any character that's neither o nor an i._

## Using Ranges

You can use a range of characters within a character class by using the dash symbol like this:

![regex ranges](https://likegeeks.com/wp-content/uploads/2017/02/19-regex-ranges.png)

This matches all characters between e and p then followed by st as shown. You can also use ranges for numbers.

![regex number range](https://likegeeks.com/wp-content/uploads/2017/02/20-regex-number-range.png)

> _You can also specify multiple, non-continuous ranges in a single character class._

![regex non-continuous range](https://likegeeks.com/wp-content/uploads/2017/02/21-regex-non-continuous-range.png)

> _The character class allows the ranges a through f, and m through z to appear before the st text._

## Special Character Classes

The BRE contains special character classes you can use to match against specific types of characters.

And this is the list:

[[:alpha:]] - Matches any alphabetical character, either upper or lower case.

[[:alnum:]] - Matches any alphanumeric character 0-9, A-Z, or a-z.

[[:blank:]] - Matches a space or Tab character.

[[:digit:]] - Matches a numerical digit from 0 through 9.

[[:lower:]] - Matches any lowercase alphabetical character a-z.

[[:print:]] - Matches any printable character.

[[:punct:]] - Matches a punctuation character.

[[:space:]] - Matches any whitespace character: space, Tab, NL, FF, VT, CR.

[[:upper:]] - Matches any uppercase alphabetical character A-Z.

You can use them like this:

![regex special character classes](https://likegeeks.com/wp-content/uploads/2017/02/22-regex-special-character-classes.png)

## The Asterisk

Placing an asterisk after a character signifies that the character must appear zero or more times in the text to match the pattern.

![regex asterisk](https://likegeeks.com/wp-content/uploads/2017/02/23-regex-asterisk.png)

This pattern symbol is commonly used for handling words that have a common misspelling or variations in language spellings.

![regex asterisk example](https://likegeeks.com/wp-content/uploads/2017/02/24-regex-asterisk-example.png)

Here in these examples, whether you spell it color or colour, it will match because the asterisk means if the u character existed many times or zero times that these two would still match.

Another handy feature is combining the dot character with the asterisk character. This combination provides a pattern to match any number of any characters.

![regex asterisk with dot](https://likegeeks.com/wp-content/uploads/2017/02/25-regex-asterisk-with-dot.png)

> _It doesn't matter how many words between the words this and test, any line will match and be printed._

The asterisk can also be applied to a character class.

![asterisk with character classes](https://likegeeks.com/wp-content/uploads/2017/02/26-asterisk-with-character-classes.png)

All three examples match because the asterisk means if you find the a or e character zero times or more it will print.

## Extended Regular Expressions

The POSIX ERE patterns include a few additional symbols that are used by some Linux applications and utilities. The awk command recognizes the ERE patterns, but sed doesn't. We will discuss the commonly used ERE pattern symbols that you can use in your awk program scripts.

The question mark indicates that the preceding character can appear zero times or once so no repeating here.

![regex question mark](https://likegeeks.com/wp-content/uploads/2017/02/27-regex-question-mark.png)

> _You can use the question mark symbol along with a character class._

![regex question mark with character classes](https://likegeeks.com/wp-content/uploads/2017/02/28-regex-question-mark-with-character-classes.png)

> _If zero characters or one character from the character class appears, the pattern match passes._

But if both characters appear, or if one of the characters appears twice, the pattern match fails.

### The Plus Sign

The plus sign indicates that the preceding character can appear one or more times, but must be present at least once.

![regex plus sign](https://likegeeks.com/wp-content/uploads/2017/02/29-regex-plus-sign.png)

If the e character is not present, the pattern match fails. The plus sign also works with character classes, the same way as the asterisk and question mark

![regex plus sign with character classes](https://likegeeks.com/wp-content/uploads/2017/02/30-regex-plus-sign-with-character-classes.png)

> _This time if either character defined in the character class appears, the text matches the specified pattern._

### Curly Braces

Curly braces are available in ERE to allow you to specify a limit on a repeatable regex, it has two formats.

n: The regex appears exactly n times.

n,m: The regex appears at least n times, but no more than m times.

![regex curly braces](https://likegeeks.com/wp-content/uploads/2017/02/31-regex-curly-braces.png)

In old versions of awk, you should use -re-interval command line option for the awk command to recognize regular expression intervals but now you don't need it

![regex curly braces interval pattern](https://likegeeks.com/wp-content/uploads/2017/02/32-regex-curly-braces-interval-pattern.png)

In this example, the e character can appear once or twice for the pattern match to pass, otherwise, the pattern match fails

The interval pattern match also applies to character classes the same way we did above so we don't have to do it again.

![regex interval pattern with character classes](https://likegeeks.com/wp-content/uploads/2017/02/33-regex-interval-pattern-with-character-classes.png)

This regex pattern matches if there are exactly one or two instances of the letter a or e in the text pattern, but it fails if there are any more in any combination.

### The Pipe Symbol

The pipe symbol allows to you to specify two or more patterns that the regex engine uses in a logical OR formula when examining the data stream. If any of the patterns match the text, the text passes. If none of the patterns match, the pattern will fail. Here is an example:

![regex pipe symbol](https://likegeeks.com/wp-content/uploads/2017/02/34-regex-pipe-symbol.png)

This example looks for the regular expression test or exam in the text. Keep in mind that you can't place any spaces within the regular expressions and the pipe symbol.

## Grouping Expressions

Regex patterns can also be grouped by using parentheses. When you group a regex pattern, the group is treated like a standard character. You can apply a special character to the group just as you would to a regular character

![regex grouping expressions](https://likegeeks.com/wp-content/uploads/2017/02/35-regex-grouping-expressions.png)

The grouping of the "Geeks" ending along with the question mark allows the pattern to match either the full day name LikeGeeks or the word Like only.

## Practical Examples

We've seen some simple demonstrations of using regular expression patterns, it's time to put that in action, just for practice.

### Counting Directory Files

Let's look at a bash script that counts the executable files that are present in the directories defined in your PATH environment variable. To do that, you need to parse out the PATH variable into separate directory names.

$ echo $PATH

To get a listing of directories that you can use in a script, you must replace each colon with a space.

Now let's iterate through each directory using for a loop like this:

Great!!

Now we can use the ls command to list each file in each directory and save the count in a variable.

You may notice some directories don't exist, no problem there.

![regex count files](https://likegeeks.com/wp-content/uploads/2017/02/36-regex-count-files.png)

Cool!! This is the power of regex. Those few lines of code count all files in all directories. Of course, there is a Linux command to do that very easily, but here we introduced how to employ regex in something you can know how to use it, and with some creativity, come up with some more useful ideas.

### Validating e-mail Addresses

There are a ton of websites that use regex patterns for everything e-mail phone number related. Here's how it works.

username@hostname.com

The username can use any alphanumeric characters combined with dot, dash, plus sign, and underscore. The hostname can use any alphanumeric characters combined with dot and underscore.

Let's start building the regular expression pattern from the left side. We know that there can be multiple valid characters in the username. This should be very easy.

^([a-zA-Z0-9_\\-\\.\\+]+)@

This grouping specifies the allowed characters in the username and the plus sign to indicate that at least one character must be present or more than the @ sign.

Then the hostname pattern should be like this:

([a-zA-Z0-9_\\-\\.]+)

There are special rules for the top-level domain. Top-level domains are only alphabetic characters, and they must be no fewer than two characters (used in country codes) and no more than five characters in length. The following is the regex pattern for the top-level domain:

\\.([a-zA-Z]{2,5})$

Now we put them all together:

Let's test that regex against an email:

![regex validate email](https://likegeeks.com/wp-content/uploads/2017/02/37-regex-validate-email.png)

Awesome! Works great!

This was just the beginning for a regex world that never ends. I hope after this post you understand these ASCII buggers and use it more professionally.

This is for now, hope you like the post!

Thank you.

Learn why developers are gravitating towards Node and its ability to [retain and leverage the skills of JavaScript developers](https://dzone.com/go?i=182122&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127834%26PluID%3D0%26ord%3D%5Btimestamp%5D) and the ability to deliver projects faster than other languages can. Brought to you in partnership with [IBM](https://dzone.com/go?i=182122&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127834%26PluID%3D0%26ord%3D%5Btimestamp%5D).
