# Regular expressions in lexing and parsing

_Captured: 2015-12-11 at 21:39 from [commandcenter.blogspot.ch](http://commandcenter.blogspot.ch/2011/08/regular-expressions-in-lexing-and.html)_

Comments extracted from a code review. I've been asked to disseminate them more widely.

I should say something about regular expressions in lexing and   
parsing. Regular expressions are hard to write, hard to write well,   
and can be expensive relative to other technologies. (Even when they   
are implemented correctly in N*M time, they have significant   
overheads, especially if they must capture the output.)   
Lexers, on the other hand, are fairly easy to write correctly (if not   
as compactly), and very easy to test. Consider finding alphanumeric   
identifiers. It's not too hard to write the regexp (something like"[a-ZA-Z_][a-ZA-Z_0-9]*"), but really not much harder to write as a   
simple loop. The performance of the loop, though, will be much higher   
and will involve much less code under the covers. A regular expression   
library is a big thing. Using one to parse identifiers is like using a   
Ferrari to go to the store for milk.   
And when we want to adjust our lexer to admit other character types,   
such as Unicode identifiers, and handle normalization, and so on, the   
hand-written loop can cope easily but the regexp approach will break   
down.   
A similar argument applies to parsing. Using regular expressions to   
explore the parse state to find the way forward is expensive,   
overkill, and error-prone. Standard lexing and parsing techniques are   
so easy to write, so general, and so adaptable there's no reason to   
use regular expressions. They also result in much faster, safer, and   
compact implementations.

Another way to look at it is that lexers and parsing are matching   
statically-defined patterns, but regular expressions' strength is that   
they provide a way to express patterns dynamically. They're great in   
text editors and search tools, but when you know at compile time what   
all the things are you're looking for, regular expressions bring far   
more generality and flexibility than you need.   
Finally, on the point about writing well. Regular expressions are, in   
my experience, widely misunderstood and abused. When I do code reviews   
involving regular expressions, I fix up a far higher fraction of the   
regular expressions in the code than I do regular statements. This is   
a sign of misuse: most programmers (no finger pointing here, just   
observing a generality) simply don't know what they are or how to use   
them correctly.   
Encouraging regular expressions as a panacea for all text processing   
problems is not only lazy and poor engineering, it also reinforces   
their use by people who shouldn't be using them at all.   
So don't write lexers and parsers with regular expressions as the   
starting point. Your code will be faster, cleaner, and much easier to   
understand and to maintain.
