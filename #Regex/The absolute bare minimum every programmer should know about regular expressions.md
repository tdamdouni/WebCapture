# The absolute bare minimum every programmer should know about regular expressions

_Captured: 2015-12-11 at 09:57 from [web.archive.org](http://web.archive.org/web/20090209182018/http://immike.net/blog/2007/04/06/the-absolute-bare-minimum-every-programmer-should-know-about-regular-expressions/)_

### Wtf is a regular expression?

Regular expressions are strings formatted using a special pattern notation that allow you to describe and parse text. Many programmers (even some good ones) disregard regular expressions as line noise, and it's a damned shame because they come in handy so often. Once you've gotten the hang of them, regular expressions can be used to solve countless real world problems.

Regular expressions work a lot like the filename "globs" in Windows or *nix that allow you to specify a number of files by using the special * or ? characters (oops, did I just use a glob while defining a glob?). But with regular expressions the special characters, or _metacharacters_, are far more expressive.

Like globs, regular expressions treat most characters as literal text. The regular expression `mike`, for example, will only match the letters m - i - k - e, in that order. But regular expressions sport an extensive set of metacharacters that make the simple glob look downright primitive.

### Meet the metacharacters: ^[](){}.*?\|+$ and sometimes -

I know, they look intimidating, but they're really nice characters once you get to know them.

#### The Line Anchors: '^' and '$'

The '^' (_caret_) and '$' (_dollar_) metacharacters represent the start and end of a line of text, respectively. As I mentioned earlier, the regular expression `mike` will match the letters m - i - k - e, but it will match anywhere in a line (e.g. it would match "I'm mike", or even "carmike"). The '^' character is used to _anchor_ the match to the start of the line, so `^mike` would only find lines that start with mike. Similarly, the expression `mike$` would only find m - i - k - e at the end of a line (but would still match 'carmike').

If we combine the two line anchor characters we can search for lines of text that contain a specific sequence of characters. The expression `^mike$` will only match the word mike on a line by itself - nothing more, nothing less. Similarly the expression `^$` is useful for finding empty lines, where the beginning of the line is promptly followed by the end.

#### The Character Class: '[]'

Square brackets, called a _character class_, let you match any one of several characters. Suppose you want to match the word 'gray', but also want to find it if it was spelled 'grey'. A character class will allow you to match either. The regular expression `gr[ea]y` is interpreted as "g, followed by r, followed by either an e or an a, followed by y."

If you use `[^ ... ]` instead of `[ ... ]`, the class matches any character that _isn't_ listed. The leading ^ "negates" the list. Instead of listing all of the characters you want to included in the class, you list the characters you don't want included. Note that the ^ (_caret_) character used here has a different meaning when it's used outside of a character class, where it is used to match the beginning of a line.

#### The Character Class Metacharacter: '-'

Within a character-class, the _character-class metacharacter_ '-' (dash) indicates a range of characters. Instead of [01234567890abcdefABCDEF] we can write [0-9a-fA-F]. How convenient. The dash is a metacharacter only within a character class, elsewhere it simply matches the normal dash character.

But wait, there's a catch. If a dash is the first character in a character class it is not considered a metacharacter (it can't possibly represent a range, since a range requires a beginning and an end), and will match a normal dash character. Similarly, the question mark and period are usually regex metacharacters, but _not_ when they're inside a class (in the class [-0-9.?] the only special character is the dash between the 0 and 9).

#### Matching Any Character With a Dot: '.'

The '.' metacharacter (called a _dot_ or _point_) is shorthand for a character class that matches any character. It's very convenient when you want to match any character at a particular position in a string. Once again, the dot metacharacter is _not_ a metacharacter when it's inside of a character class. Are you beginning to see a pattern? The list of metacharacters is different inside and outside of a character class.

#### The Alternation Metacharacter: '|'

The '|' metacharacter, (_pipe_) means "or." It allows you to combine multiple expressions into a single expression that matches any of the individual ones. The subexpressions are called _alternatives_.

For example, `Mike` and `Michael` are separate expressions, but `Mike|Michael` is one expression that matches either.

Parenthesis can be used to limit the scope of the alternatives. I could shorten our previous expression that matched Mike or Michael with creative use of parenthesis. The expression `Mi(ke|chael)` matches the same thing. I probably would use the first expression in practice, however, as it is more legible and therefore more maintainable.

#### Matching Optional Items: '?'

The '?' metacharacter (_question mark_) means _optional_. It is placed after a character that is allowed, but not required, at a certain point in an expression. The question mark attaches only to the immediately preceding character.

If I wanted to match the english or american versions of the word 'flavor' I could use the regex `flavou?r`, which is interpreted as "f, followed by l, followed by a, followed by v, followed by o, followed by an optional u, followed by r."

#### The Other Quantifiers: '+' and '*'

Like the question mark, the '+' (_plus_) and '*' (_star_) metacharacters affect the number of times the preceding character can appear in the expression (with '?' the preceding character could appear 0 or 1 times). The metacharacter '+' matches one or more of the immediately preceding item, while '*' matches any number of the preceding item, including 0.

If I was trying to determine the score of a soccer match by counting the number of times the announcer said the word 'goal' in a transcript, I might use the regular expression `go+al`, which would match 'goal', as well as 'gooooooooooooooooal' (but not 'gal').

The three metacharacters, question mark, plus, and star are called _quantifiers_ because they influence the quantity of the item they're attached to.

#### The Interval Quantifier: '{}'

The '{min, max}' metasequence allows you to specify the number of times a particular item can match by providing your own minimum and maximum. The regex `go{1,5}al` would limit our previous example to matching between one and five o's. The sequence {0,1} is identical to a question mark.

#### The Escape Character: '\'

The '\' metacharacter (_backslash_) is used to escape metacharacters that have special meaning so you can match them in patterns. For example, if you would like to match the '?' or '\' characters, you can precede them with a backslash, which removes their meaning: '\?' or '\\\'.

When used before a non-metacharacter a backslash can have a different meaning depending on the flavor of regular expression you're using. For perl compatible regular expressions (_PCREs_) you can check out [the perldoc page for perl regular expressions](http://web.archive.org/web/20090209182018/http://perldoc.perl.org/perlre.html). PCREs are extremely common, this flavor of regexes can be used in [PHP](http://web.archive.org/web/20090209182018/http://us3.php.net/pcre), [Ruby](http://web.archive.org/web/20090209182018/http://raa.ruby-lang.org/project/pcre/), and [ECMAScript/Javascript](http://web.archive.org/web/20090209182018/http://www.ecma-international.org/publications/standards/Ecma-262.htm), and many other languages.

#### Using Parenthesis for Matching: '()'

Most regular expression tools will allow you to _capture_ a particular subset of an expression with parenthesis. I could match the domain portion of a URL by using an expression like `http://([^/]+)`. Let's break this expression down into it's components to see how it works.

The beginning of the expression is fairly straightforward: it matches the sequence "h - t - t - p - : - / - /". This initial sequence is followed by parenthesis, which are used to _capture_ the characters that match the subexpression they surround. In this case the subexpression is '[^/]+', which matches any character except for '/' one or more times. For a URL like http://immike.net/blog/Some-blog-post, 'immike.net' will be captured by the parenthesis.

### Want to know more?

I've only touched the surface on what can be done with regular expressions. If want to learn more, check out [Jeffrey Friedl's book _Mastering Regular Expressions_](http://web.archive.org/web/20090209182018/http://www.amazon.com/gp/product/0596528124/ref=pd_cp_b_title/102-7486746-3142504?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-41&pf_rd_r=1HKNXWMTVFF257YA2P0X&pf_rd_t=201&pf_rd_p=252362401&pf_rd_i=1565922573). Friedl did an outstanding job with this book, it's accessible and a surprisingly fun and interesting read, considering the dry subject matter.

Check out [my follow up to this article](http://web.archive.org/web/20090209182018/http://immike.net/blog/2007/04/06/5-regular-expressions-every-web-programmer-should-know/) where I take a look at some of the most useful regular expressions for common programming tasks. And once you understand the basics read on to [learn all you need to know to become a regex pro](http://web.archive.org/web/20090209182018/http://immike.net/blog/2007/06/21/extreme-regex-foo-what-you-need-to-know-to-become-a-regular-expression-pro/).
