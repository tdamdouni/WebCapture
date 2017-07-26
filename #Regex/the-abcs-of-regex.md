# The ABCs of RegEx

_Captured: 2017-06-24 at 00:30 from [dzone.com](https://dzone.com/articles/abc-of-regex?edition=305134&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-23)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

![the-regex-session-with-shamik-highres.png](https://lh3.googleusercontent.com/PFPE0vXbWs6UniITrGGw-Dc4_nrq-f7aitobqHE6QcH-xXAuhFdu9mAinADsNp5Kwa6V10PN-o69c07anJsvyEeePpc7UlRSWctENhnkX2ZmvaP3lyXyCKAkmCi_wCaVrLH9Vdts)

**Teacher**: Today we will learn RegEx and how to use it in Java.

**Jonny and Alice scream with fear, then say**: That's so confusing! It makes our lives miserable!

**Teacher**: Yes, I also used to think that when I was a student, but it isn't as hard as you think. You just need some key points to remember. But before that, tell me why you think RegEx is confusing.

**Alice**: It's hard to read and write. If we have a string to validate with a complex pattern, say email validation, if you look at the RegEx for that, it is a one liner with multiple backslashes, third brackets, first brackets, etc., so it is hard to understand what it says. When we see a RegEx solution, we don't understand what it's trying to say!

**Teacher**: So you mean readability right? You prefer to write more code to avoid RegEx, so code increases readability. But let me tell you, RegEx is the Holy Grail. If you unleash its power, you can write concise and readable code.

**Jonny**: Sir, another problem is that there is no fixed solution for a problem. Let's take email validation again: If you search for it with Google, you can see a ton of different solutions to validate an email. So it is hard to pick the right one.

**Teacher**: This is because you do not understand the crux of RegEX. Any other problem?

Pin drop silence there.

So, the teacher slowly takes a step toward the board and starts his lesson.

## **What Is RegEx?**

The teacher said that Regular Expression is a technique for searching a pattern in a String. This search pattern can be very simple or very complex: a word to a sentence, or an expression made by different meta-characters or symbols used in the RegEx.

To understand RegEx correctly, we need to know metacharacters/symbols and their meanings. This is the only thing you need to remember.

We find RegEx hard because we are not able to understand the symbols. So, let's take a look at the different symbols used in RegEx.

We can classify RegEx symbols into three brackets or categories.

  1. Meta-Characters
  2. Ranges and reserved symbols
  3. Quantifiers

## **Meta-Characters**

In RegEx, there are some reserved meta-characters that have pre-defined meanings to express some common patterns like the digit, whitespace, etc. in a compact way.

Meta Character

Expression

Alternate Expr.

Definition

To express digit

\d

[0-9] or [^\D]

By this we represent a digit character

To express anything EXCEPT digit

\D

[^0-9] or [^\d]

By this we represent a non-digit character

To express a word

\w

[a-zA-Z_0-9] or [^\W]

By this we represent a word character

To express anything EXCEPT a word

\W

[^a-zA-Z_0-9] or [^\w]

By this we represent a non-word character

To express a whitespace

\s

[\t\n\x0b\r\f] or [^\S]

By this we represent any whitespace like \r,\t,\n etc

To express anything EXCEPT a whitespace

\S

[^\t\n\x0b\r\f] or [^\s]

By this we represent any non whitespace

To express a boundary

\b

[a-zA-Z0-9_]

By this we represent a boundary

## **Ranges and Reserved Symbols**

In RegEx, when we try to match patterns, some information has to be included, like how many times a pattern will be matched or whether you want to match the beginning of the string or end of the string. We define them using ranges and reserved symbols.

Symbol

Description

Example

Example Definition

.

Any character

.ha.

Start with any character followed by ha then any character -- sham matches, whereas gyan: does not match

^

Check beginning of the line

^sha

If the line starts with sha, it's matched. Otherwise, it fails.

sham: match. Aha: no match

$

Check end of the line

tra$

If the line ends with tra, it's matched. Otherwise, it fails.

Mitra: Matched

Chakra: Not matched

[xyz]

Match either x or y or z

a[xyz]

ax : Matched

aa : Not matched

[xyz][abc]

Match x, y, or z followed by a or b or c

s[hwo][abc]

sha: Matched

sou : Not matched

XA

Exactly X followed by A

sm

sm: Matched

sa: Not matched

X|A

X or A

s[X|A]

sX: Matched

sZ: Not matched

[^abc]

Remember: When ^ is used inside square brackets, it acts as a negation.

s[^abc]m

shm: Matched

sam: Not matched

[a-c1-10]

Match between character and digit 1 to 10 remember characters between/except boundaries

digit : All/Include boundaries

s[x-z1-10]

sy1: Matched

sx1: Not matched

()

Used for Grouping

(s[^yz])(a|b)([a-c1-10]

sab1: Matched

shac: Not matched

syab: Not matched

sabb: Matched

  


## **Quantifiers**

Quantifiers say how many times a pattern can be found in a String.

Quantifiers

Description

Example

Example Definition

*

Pattern can occur zero to many times

s(\s)*m

sm:Matched

s m: Matched

s:m:Not Matched

+

Pattern can occurs one to many times

s(\s)+m

s m : Matched

sm: Not Matched

  


?

Pattern can occur zero or one time

s(h)?a

sha: Matched

sa: Matched

shha: Not Matched

{X}

Pattern must occur exactly X times

s(\d)(3)

s123: Matched

s1234: Not Matched

s1: Not Matched

{X,Y}

Pattern must occur at least X times and a maximum of Y times

s(\d)(2,4)

s12 :Matched

s1: Not Matched

s12345: Not Matched

## **Email Validation**

**Teacher**: So Jonny, earlier you said that email validation is confusing. Now can you tell us what this email validation says?

**Jonny**: The first part says ^[A-Za-z0-9]+, so the email must start with any characters and at least one occurrence should be present. The ^ denotes the start of the line and + says one or more, so the email can start with any characters with any length.

**Sir**: Very good. Alice, you tell me the second part.

**Alice**: (\\\\.[A-Za-z0-9-]+)* says that after first part, it's followed by a dot, then, again, any length of characters but there must be at least one. Also, this part is optional because * is at the end.

**Sir**: Impressive.

**Jonny**: @[A-Za-z0-9-]+: So, it strictly matches @ and then at least one character, as the + symbol is there.

**Alice **: (\\\\.[A-Za-z0-9]+)*, which means, again, it's follows by a dot and at least one character. But this is also optional

Jonny: When we get to (\\\\.[A-Za-z]{2,})$, that means the email ends($) with a dot and any character in a-z or A-z and a length of between two to any.

**Sir**: Great, now Alice, tell me a valid email according to this RegEx.

**Alice**: shamik.mitra@gmail.co.in or shamik@gmail.com

**Sir**: Good, Jonny, tell me an invalid one

**Jonny**: shamik.mitra@co.i or .mitra@gmail.co.uk

**Sir**: Well, it seems you are learning RegEx very quickly. So before we finish today's lesson, I 'll give you one tip: Stick the tables above on your desk so that every day you can go through the RegEx symbols. Soon, you'll easily remember everything you need to know.

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
