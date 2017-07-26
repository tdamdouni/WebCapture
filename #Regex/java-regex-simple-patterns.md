# Java Regex: Simple Patterns

_Captured: 2017-03-27 at 22:50 from [dzone.com](https://dzone.com/articles/java-regex-simple-patterns?edition=286926&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-27)_

[Bitbucket](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=text-code-that-takes-us-to-mars&utm_campaign=bitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=text-code-that-takes-us-to-mars&utm_campaign=bitbucket_adexp-bbtofu_dzone-text)

Regular Expressions are the bread and butter of string pattern matching. They allow you to express a search pattern in general terms without being too specific about what you are searching for.

This article covers the basics of string pattern matching using regular expressions.

## Pattern String vs. Pattern Class

A regex pattern is expressed as a string with characters that carry special meanings. Some methods used in string search accept such a regex string directly while some require an instance of the _[Pattern ](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html)_class. An instance of the _Pattern_ class can be created by compiling a string description of a pattern. When reusing a pattern for repeated matching, it makes sense to compile the regex string to a _Pattern_. This is to avoid paying the cost of compilation every time the regex pattern is used.

## Some Regex Examples

Have you seen the description of regular expression patterns and characters from the [Javadocs](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html)? An overwhelming list, to say the least! A newbie would take a look at this list and not know where to start. To help you begin to understand, we have included some commonly used regular expression constructs below.

We use _[String.matches()](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#matches-java.lang.String-)_ method to perform a regular expression match. This method accepts a pattern string and returns an indicator of whether the string matched the pattern.

The following example illustrates using the pattern "`.*`" (explained below) which matches any string, including the empty string.
    
    
    String str = "hello";
    String pattern = ".*";
    System.out.println("Matching \"" + str + "\" with (" + pattern + "): " + str.matches(pattern));
    
    // prints:
    Matching "hello" with (.*): true

### A Single Character

Pattern: `.`
    
    
    Matching "hello" with (.): false
    Matching "h" with (.): true
    Matching "" with (.): false

### Anything

Pattern: `.*`

Use this pattern to match any number (including the empty string) of any characters.
    
    
    Matching "hello" with (.*): true
    Matching "" with (.*): true

### Beginning of String

Pattern: `^`
    
    
    Matching "hello" with (^h.*): true
    Matching "world" with (^h.*): false

### End of String

Pattern: `$`
    
    
    Matching "banana" with (.*e$): false
    Matching "apple" with (.*e$): true
    Matching "orange" with (.*e$): true
    Matching "melon" with (.*e$): false

### Optional Character

Pattern: `?`

Matches 0 or 1 instance of the preceding character.
    
    
    Matching "ilma" with (W?ilma): true
    Matching "Wilma" with (W?ilma): true
    Matching "Hilma" with (W?ilma): false

### Multiple instances

Pattern: `*`

Match any number of instances of the preceding pattern (including zero matches).

### Any in a Set

Pattern: `[abc]`

Matches any **one** of the characters listed within brackets ([]).
    
    
    Matching "a" with ([abc]): true
    Matching "b" with ([abc]): true
    Matching "c" with ([abc]): true
    Matching "ab" with ([abc]): false

You can, of course, attach `*` to the pattern to get it to match multiple times.
    
    
    Matching "a" with ([abc]*): true
    Matching "ab" with ([abc]*): true
    Matching "abccca" with ([abc]*): true
    Matching "abcd" with ([abc]*): false

### Any Not in Set

Pattern: `[^abc]`

Exclude all characters specified from the match
    
    
    Matching "a" with ([^abc]): false
    Matching "b" with ([^abc]): false
    Matching "c" with ([^abc]): false
    Matching "d" with ([^abc]): true
    Matching "dd" with ([^abc]): false

### Range of Characters

Pattern: `[a-z]`

Instead of specifying characters in a continuous range such as `[abcde]`, you can use `[a-e]`.
    
    
    Matching "a" with ([a-d]): true
    Matching "b" with ([a-d]): true
    Matching "cd" with ([a-d]): false
    Matching "e" with ([a-d]): false

### Negate Range

Pattern: `[^a-d]`

To invert a range match, use the negation operator `^`
    
    
    Matching "a" with ([^a-d]): false
    Matching "e" with ([^a-d]): true
    Matching "fg" with ([^a-d]): false

### Digits

Pattern: `[0-9]`

Alternate: `\d`

A range match consisting of digits only.
    
    
    Matching "3" with ([0-9]): true
    Matching "a" with ([0-9]): false
    Matching "45" with ([0-9]): false
    Matching "hello" with ([0-9]): false

Use `*`to match multiple instances.
    
    
    Matching "3" with ([0-9]*): true
    Matching "a" with ([0-9]*): false
    Matching "45" with ([0-9]*): true
    Matching "hello" with ([0-9]*): false

### Word Character Class

Pattern: `\w`

Matches any _word_ character which includes `[a-zA-Z0-9]`.
    
    
    Matching "a" with (\w): true
    Matching "hello" with (\w): false
    Matching "6" with (\w): true
    Matching "7e" with (\w): false
    Matching "+" with (\w): false

### Non-Word Character Class

Pattern: `\W`

Reverses the above word character matching.
    
    
    Matching "a" with (\W): false
    Matching "3" with (\W): false
    Matching "+" with (\W): true
    Matching "," with (\W): true
    Matching "[]" with (\W): false

### Non-Digit Character Class

Pattern: `\D`

Contrast with `\d` which matches a single digit only is the \D which matches a non-digit only.
    
    
    Matching "a" with (\D): true
    Matching "1" with (\D): false
    Matching "+" with (\D): true

### Space and Non-Space Characters

Space: `\s`
    
    
    Matching "hello world" with (\w+\s\w+): true
    Matching "helloworld" with (\w+\s\w+): false

Non-Space: `\S`
    
    
    Matching "hello" with (\S*): true
    Matching "hello world" with (\S*): false
    Matching "helloworld" with (\S*): true

### Escape Special Character

With all these special characters (such as `.`, `*`, `+`, etc) carrying special meanings, how do you use one of these to match itself? By escaping it with a backslash (`\`).
    
    
    Matching "hello" with (hel\*o): false
    Matching "helo" with (hel\*o): false
    Matching "hel*o" with (hel\*o): true

## Summary

Regular Expressions are used to search for patterns in text. We learned the basics of regex pattern search including very commonly used regex constructs. These included anchoring to beginning and end, character classes including digits, word characters, spaces and so on.

[Bitbucket is the Git solution](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=text-teams-who-code-with-a-purpose&utm_campaign=bitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=text-teams-who-code-with-a-purpose&utm_campaign=bitbucket_adexp-bbtofu_dzone-text)

### Like This Article? Read More From DZone
