# Part I: Top 10 Programmer Jokes, Explained for the Rest of Us

_Captured: 2016-10-31 at 19:31 from [www.idtech.com](https://www.idtech.com/blog/part-i-top-10-programmer-jokes-explained-for-the-rest-of-us/)_

by: [Kendall](/blog/author/kendall/) on March 13, 2014

![Programmer Jokes Blog Header](//media.idtech.com/uploads/2014/03/Top-10-Programmer-Jokes-Header.png)

Ahhhh…programmer humor! Hilarious to coders and completely baffling to the
rest of us. Not a programmer?  Thanks to our very own Development Manager,
Christian, you can be in on the jokes, too. He was kind enough to explain the
punchlines of the following programmer jokes, for those of us who are dazed
and confused. (UPDATE, binary jokes are now my favorite.)

### **1\. Why do programmers always mix up Halloween and Christmas? Because
****Oct 31 = Dec 25.**

The joke here is that Octal 31 (which abbreviated looks like October 31st,
Halloween) is equal to Decimal 25 (which abbreviated looks like December 25th,
Christmas).

Decimal and octal are two number systems with different bases.

Decimal is the base-10 number system that everyone is familiar with. A number
system has as many digits as its base number. That means a base-10 number
system 10 digits (0, 1, 2, 3, 4, 5, 6, 7, 8, and 9) and is where it gets its
name from (decimal, from Latin _decimus_, means _tenth_).

When you get to a number that is higher than the highest digit, you add
another column to the left, so you count like 8, 9, 10, 11, 12, and so on.

Octal (from the Latin root _oct-_ meaning eight) is a base-8 number system
commonly used in programming. A base-8 system means it has 8 digits (0, 1, 2,
3, 4, 5, 6, and 7). When you get to a number higher than 7, you also add
another column, so you count like 6, 7, 10, 11, 12, and so on.

If we convert the octal 31 to decimal, we end up with 25. Watch: if we break
octal 31 out to a math equation, it ends up being 3 x 81 \+ 1 x 80 = 3 x 8 + 1
x 1 = 24 + 1 = decimal 25.

To convert the other way, you start with the biggest power of the base (8, in
this case) you can divide by and get a whole number, then take that and divide
the remainder by the next smaller power until you get to the 0-th power. Then
you just combine the digits together. In the case of 25, we need to start at
81: 25 / 81 = 3, remainder of 1 / 80 = 1, so 31.__

### **2\. There are 10 types of people in this world. Those who understand
binary and those who don’t.**

This is a binary joke; binary being a base-2 system. Since it is a base-2
system, it has only 2 digits, 0 and 1.

If we convert binary 10 to decimal, we get: 1 * 21 \+ 0 * 20 = 1 * 2 + 0 = 2.

So, the joke means “There are two types of people. Those who understand binary
and those who don’t.”

If you don’t understand binary though, you’d think there are ten types of
people, which would be weird.

In addition to decimal (base-10), octal (base-8) and binary (base-2),
hexadecimal (base-16) is also used commonly in programming. It uses the
letters A, B, C, D, E, and F as the “digits” above 9.

### **3\. There are two ways to write error-free programs; only the third one
works.**

This joke refers to the fact that it is actually impossible to write an error-
free program.

It is possible to write a program that seems to have no errors, usually
referred to as “bugs” in programmer lingo, but Lubarsky’s Law of Cybernetic
Entomology states “There is _always_ one more bug.” The bug may be so tiny and
under such specific conditions that you’ll never see it… but there is _always_
one more bug.

Since there is always one more bug, the joke says only the third, _non-
existent_ method is the only way to write an error-free program.

### **4\. The best thing about a Boolean is even if you are wrong, you are
only off by a bit.**

A Boolean is a data type which can only have one of two possible values: true
and false.

A data type just means what type of data is held within something like a
variable.

Variables in programming are similar to variables you might have seen in math
class, with the difference being that a variable in programming can represent
more than just a number. It could, for example, hold an alphabetic character
like “c” or a whole word or phrase like “Hello World”, commonly called a
string or a Boolean.

Booleans are typically stored within a bit, which is the smallest amount of
storage in a computer. It holds a single binary digit. Binary, being a base-2
number system, means it can only hold the value 0 or 1. In the case a Boolean,
0 usually means false while 1 is usually used for true.

The joke then, is that if you have a Boolean, the most you can be off is a
bit, which would just be 0 or 1.

### **5\. A good programmer is someone who always looks both ways before
crossing a one-way street.**

This joke refers to the fact that, as a programmer, you can’t make assumptions
about how things will behave in your program and always have to check
everything.

For example, if you ask a user to type in a number, a good programmer won’t
just assume what the user entered is a number. They need to check that what
they got is actually a number and not a word or symbol or was left blank.
Then, they need to check to make sure that the number is within the range that
they were expecting (for example, -3 wouldn’t be a valid value for “How many
people are attending?”).

Thus, the joke refers to the fact that they programmer can’t just assume
because the road is one-way that everyone is going to follow that rule.

