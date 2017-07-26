# Extreme regex foo: what you need to know to become a regular expression pro

_Captured: 2015-12-11 at 10:03 from [web.archive.org](http://web.archive.org/web/20090226045440/http://immike.net/blog/2007/06/21/extreme-regex-foo-what-you-need-to-know-to-become-a-regular-expression-pro/)_

This tutorial is intended for advanced audiences. If you're new to regular expressions, or if you could use a quick refresher, go read my [intro to regular expressions](http://web.archive.org/web/20090226045440/http://immike.net/blog/2007/04/06/the-absolute-bare-minimum-every-programmer-should-know-about-regular-expressions/), and work through [a few examples](http://web.archive.org/web/20090226045440/http://immike.net/blog/2007/04/06/5-regular-expressions-every-web-programmer-should-know/). Trust me, it'll be one of the most rewarding twenty minutes you've ever spent. If you're familiar with the basic regex concepts then read on and learn all you need to know to be a regex pro.

### What you should know

This tutorial will go beyond the basics of regular expressions. You should already know what the metacharacters are (`^[](){}.*?\|+$` and sometimes `-`) and how to use them, you should understand how to use parenthesis for grouping and capturing, and you should be able to construct basic regular expressions to match things like email addresses and URLs. If you're lost, go read the articles I mentioned in the first paragraph then come back here.

You should also be aware that many advanced regex features work differently (or aren't available at all) depending on the flavor of regular expression you're using. I'll be using perl compatible regular expressions (_PCREs_), which are far and away the most popular variety, and can be used in [Perl](http://web.archive.org/web/20090226045440/http://perldoc.perl.org/perlre.html), [PHP](http://web.archive.org/web/20090226045440/http://us3.php.net/pcre), [Ruby](http://web.archive.org/web/20090226045440/http://raa.ruby-lang.org/project/pcre/), [ECMAScript/Javascript](http://web.archive.org/web/20090226045440/http://www.ecma-international.org/publications/standards/Ecma-262.htm), [C/C++](http://web.archive.org/web/20090226045440/http://www.pcre.org/), and practically every other programming language known to man.

### What you will know

In this tutorial I'll be introducing some advanced regex concepts that will allow you to parse text like a pro. I'll be introducing _lazy quantifiers_, _lookaround_, _pattern modifiers_, and more. This is all good stuff, so let's get started.

#### Greedy vs. Lazy Quantifiers

The _standard quantifiers_ (?, *, +, and {_min_, _max_}) are _greedy_. When a quantifier is encountered in a regular expression, there is a minimum number of matches that are required before it's considered successful, as well as a maximum number that can be matched. What's important to know is that **the standard quantifiers will always match as many times as they can**.

Overlooking this rule is an exceedingly common trap that many novices fall into. Suppose I want to match emphasized text in an HTML document, for example. I could use a regular expression like `<em>.*</em>`, right? This expression would work fine for a string like "Mike's website has <em>billions</em> of visitors" (I wish). But if the text has multiple em tags this regex won't work. It will match from the beginning of the first <em> through to the last closing </em>, which isn't at all what we want.

The _lazy quantifiers_ are identical to the standard quantifiers, but have a trailing '?' (question mark) appended to them. The lazy version of '*', for example, is '*?'. Unlike their greedy counterparts, **lazy quantifiers will match _as few times as possible_**. This can be extremely useful, and can sometimes turn an exceedingly complicated regular expression into a simple one-liner. The regular expression `<em>.*?</em>` will only match up to the first closing </em> tag, which does just what we want (assuming there are no nested em tags).

#### Non-Capturing Parenthesis

By default, parenthesis _capture_ whatever text they match, storing it for later use. There are times when you'll want to group a subexpression together without capturing. To do so you can use the special notation `(?: )`. These **_non-capturing parenthesis_ behave exactly like normal parenthesis, but do not capture their contents**. Note that the use of the '?' (_question mark_) character has nothing to do with the "optional" '?' metacharacter.

Using non-capturing parenthesis is good practice for two reasons. First, it will make the regex slightly more efficient. More importantly, it can make a regex easier to understand. A complicated regex may require several grouped subexpressions to extract a single piece of text. By using non-capturing parenthesis it's immediately obvious which parts of the text you're interested in extracting, and which parts merely provide context for your match.

#### Pattern Modifiers

Perl compatible regular expressions allow _pattern modifiers_ (also called _regex modifiers_ or just _modifiers_) to be placed after the closing delimiter of an expression. The modifiers affect how the expression is compiled and interpreted by the regex engine. There are four core modifiers that are frequently used and extremely useful. If you need more than one modifier, you can group them together and place them in any order following the closing delimiter of your regex.

##### The `/i` modifier

Enables _case-insensitive matching_, and is probably the most frequently used modifier. If I wanted to match the word "mike," regardless of capitalization, I could use the regex `/mike/i` (note that I've included the regex delimiters in this example, which I haven't done anywhere else, in order to demonstrate how to use pattern modifiers). There are a number of Unicode-related issues with case-insensitive matching (or _loose matching_, as Unicode calls it). If you're matching Unicode text, it's best to avoid this mode unless you know what you're doing.

##### The `/x` modifier

Enables _extended mode_, which allows you to format complicated expressions so that they are more readable and maintainable. In extended mode, whitespace outside of character classes is ignored (or treated as a no-op metacharacter), and comments are allowed between # and a newline.

##### The `/s` modifier

Changes the behavior of the '.' (_dot_) metacharacter to match all characters, _including newlines_. The '.' metacharacter doesn't match newlines by default, for mostly historical reasons. The original regex tools were Unix command line utilities that operated as _filters_ on a line-by-line basis. Thus, matching a newline wasn't even an issue. Which mode is most appropriate will depend on what you're trying to match, so this modifier comes in handy on a pretty regular basis.

##### The `/m` modifier

Enables _multiline mode_, modifying where the line anchors ('^' and '$') match. By default, the line anchors _do not_ match before and after embedded newlines. Instead they match only at the beginning and end of the entire subject string. Given the subject string "Mike\nMalone," by default, the '^' character will match only at the beginning of the string (before the 'M'), and the '$' character will match only at the end (after the last 'e'). With multiline mode enabled, however, the '^' character will match at the beginning of the string, _and_ following the newline character. Similarly, the '$' character will match at the end of the string, _and_ preceding the newline character.

#### Character and Class Shorthands

There are a number of _character shorthands_ that allow you to match control characters that would otherwise be difficult to represent. They are, for the most part, the familiar set of escaped characters that have been around since the C programming language was developed: '\n' for a newline, '\r' for a carriage return, '\t' for a tab, etc.

There are also a series of _class shorthands_ that represent common character classes and are frequently used to simplify expressions. A short list of these should suffice, they're mostly self-explanatory.

  * **\d** matches **any decimal digit**
  * **\D** matches any character that is **not a decimal digit** (it's the same as `[^\d])`
  * **\s** matches any **whitespace character**
  * **\S** matches any **non-whitespace character**
  * **\w** matches any **"word" character** (usually the same as `[a-zA-Z0-9_]`)
  * **\W** matches any **"non-word" character**

#### Positive & Negative Lookahead / Lookbehind

_Lookaround_ is the general term used for a group of constructs that **allow you to ensure that a given expression exists in the text you're matching, _without actually matching anything_**. With _positive lookahead_, for example, you can write a regular expression that will match the word "mike," but only if it's immediately followed by the word "rocks."

_Positive lookahead_ is specified using the sequence `(?= )`. To match "mike" in the text "mike rocks," for example, I would write `mike(?= rocks)`. Another type of lookaround is _lookbehind_, which looks backwards. It is specified using the sequence `(?<= )`. Thinking of the '<=' sequence as an arrow pointing backwards might help you remember this construct.

_Negative lookahead_ and _lookbehind_ work the same way, but are successful only when their subexpression does **not** match. Negative lookahead is specified using the `(?! )` construct, and negative lookbehind is specified using `(?<! )`.

The most confusing thing about lookaround is understanding why it's useful, so let's look at an example that I've borrowed from Jeffrey Friedl's excellent book _[Mastering Regular Expressions](http://web.archive.org/web/20090226045440/http://www.amazon.com/gp/product/0596528124/ref=pd_cp_b_title/102-7486746-3142504?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-41&pf_rd_r=1HKNXWMTVFF257YA2P0X&pf_rd_t=201&pf_rd_p=252362401&pf_rd_i=1565922573)_. If you want to display a large number (like 8927369280) in printed text, it's often helpful to insert commas between each grouping of three numbers. The rule here is that we want to _insert a comma at locations having digits on the right in exact sets of three, and at least one digit on the left_. This can be accomplished fairly easily using lookaround.

We can fulfill the second requirement using lookbehind. The simple subexpression `(?<=\d)` will match locations that have at least one digit to their left. For the second requirement we need to match sets of three numbers up to the end of the string. The simple expression `(\d\d\d)+$` accomplishes this task, and if we wrap it in a lookahead construct it will match at _locations_ that are an even set of triple digits from the end of the string. So the completed regular expression
    
    
    (?<=\\d)(?=(\\d\\d\\d)+$)
    

will match each location where a comma should be inserted. We can test out this regex using a simple perl script on the command line:
    
    
    $ perl -e '$num = 8927369280;'\\
    > '$num =~ s/(?<=\\d)(?=(\\d\\d\\d)+$)/,/g;'\\
    > 'print $num, "\\n"'
    8,927,369,280
    

### Where to from here?

One final tip: whenever you write a particularly interesting or elegant regular expression, or whenever you find one that someone else has written, keep track of it somewhere (just as you would with a particularly elegant piece of code). Regular expressions are highly reusable and highly portable. And the tasks they accomplish are common to many applications (e.g., input validation, filtering, data-scraping, etc). If you use a regex once, you'll probably find it useful again in the future.

If you've gotten this far, you've got a pretty comprehensive understanding of how regular expressions work. With some practice you'll be a regex guru in no time. If you're interested in learning more, however, I **highly** recommend [Jeffrey Friedl's book _Mastering Regular Expressions_](http://web.archive.org/web/20090226045440/http://www.amazon.com/gp/product/0596528124/ref=pd_cp_b_title/102-7486746-3142504?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-41&pf_rd_r=1HKNXWMTVFF257YA2P0X&pf_rd_t=201&pf_rd_p=252362401&pf_rd_i=1565922573). It's an excellent read.
