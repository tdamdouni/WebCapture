# Java String Format Examples

_Captured: 2017-02-21 at 20:26 from [dzone.com](https://dzone.com/articles/java-string-format-examples?edition=272882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-21)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%26lst%3DDZ%26utm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%26lst%3DDZ%26utm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

Have you tried to read and understand Java's String [format documentation](https://docs.oracle.com/javase/8/docs/api/java/util/Formatter.html)? I have and found it hard to understand. While it does include all the information, the organization leaves something to be desired.

This guide is an attempt to bring some clarity and ease the usage of string formatting in java.

## String Formatting

Most common way of formatting a string in java is using _[String.format()_](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#format-java.lang.String-java.lang.Object...-). If there were a "java sprintf" then this would be it.

For formatted console output, you can use _[printf()](https://docs.oracle.com/javase/8/docs/api/java/io/PrintStream.html#printf-java.lang.String-java.lang.Object...-)_ or the _[format()](https://docs.oracle.com/javase/8/docs/api/java/io/PrintStream.html#format-java.lang.String-java.lang.Object...-)_ method of _[System.out](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html#out)_ and _[System.err](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html#err)_ PrintStreams.

Create a _[Formatter ](https://docs.oracle.com/javase/8/docs/api/java/util/Formatter.html)_and link it to a _[StringBuilder](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html)_. Output formatted using the _[format()](https://docs.oracle.com/javase/8/docs/api/java/util/Formatter.html#format-java.lang.String-java.lang.Object...-)_ method will be appended to the _StringBuilder_.

## Format Specifiers

Here is a quick reference to all the conversion specifiers supported.

Specifier
Applies to
Output

%a
floating point (except _[BigDecimal_](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html))
Hex output of floating point number

%b
Any type
"true" if non-null, "false" if null

%c
character
Unicode character

%d
integer (incl. byte, short, int, long, bigint)
Decimal Integer

%e
floating point
decimal number in scientific notation

%f
floating point
decimal number

%g
floating point
decimal number, possibly in scientific notation depending on the precision and value.

%h
any type
Hex String of value from hashCode() method.

%n
none
Platform-specific line separator.

%o
integer (incl. byte, short, int, long, bigint)
Octal number

%s
any type
String value

%t
Date/Time (incl. long, Calendar, Date and TemporalAccessor)
%t is the prefix for Date/Time conversions. More formatting flags are needed after this. See Date/Time conversion below.

%x
integer (incl. byte, short, int, long, bigint)

Hex string.

### Date and Time Formatting

Note: Using the formatting characters with "%T" instead of "%t" in the table below makes the output uppercase.

Flag
Notes

%tA
Full name of the day of the week, e.g. "`Sunday`", "`Monday`"

%ta
Abbreviated name of the week day e.g. "`Sun`", "`Mon`", etc.

%tB
Full name of the month e.g. "`January`", "`February`", etc.

%tb
Abbreviated month name e.g. "`Jan`", "`Feb`", etc.

%tC
Century part of year formatted with two digits e.g. "00" through "99".

%tc
Date and time formatted with "`%ta %tb %td %tT %tZ %tY`" e.g. "`Fri Feb 17 07:45:42 PST 2017`"

%tD
Date formatted as "`%tm/%td/%ty`"

%td
Day of the month formatted with two digits. e.g. "`01`" to "`31`".

%te
Day of the month formatted without a leading 0 e.g. "1" to "31".

%tF
ISO 8601 formatted date with "`%tY-%tm-%td`".

%tH
Hour of the day for the 24-hour clock e.g. "`00`" to "`23`".

%th
Same as %tb.

%tI
Hour of the day for the 12-hour clock e.g. "`01`" - "`12`".

%tj
Day of the year formatted with leading 0s e.g. "`001`" to "`366`".

%tk
Hour of the day for the 24 hour clock without a leading 0 e.g. "`0`" to "`23`".

%tl
Hour of the day for the 12-hour click without a leading 0 e.g. "`1`" to "`12`".

%tM
Minute within the hour formatted a leading 0 e.g. "`00`" to "`59`".

%tm
Month formatted with a leading 0 e.g. "`01`" to "`12`".

%tN
Nanosecond formatted with 9 digits and leading 0s e.g. "000000000" to "999999999".

%tp
Locale specific "am" or "pm" marker.

%tQ
Milliseconds since epoch Jan 1 , 1970 00:00:00 UTC.

%tR
Time formatted as 24-hours e.g. "`%tH:%tM`".

%tr
Time formatted as 12-hours e.g. "`%tI:%tM:%tS %Tp`".

%tS
Seconds within the minute formatted with 2 digits e.g. "00" to "60". "60" is required to support leap seconds.

%ts
Seconds since the epoch Jan 1, 1970 00:00:00 UTC.

%tT
Time formatted as 24-hours e.g. "`%tH:%tM:%tS`".

%tY
Year formatted with 4 digits e.g. "`0000`" to "`9999`".

%ty
Year formatted with 2 digits e.g. "`00`" to "`99`".

%tZ
Time zone abbreviation. e.g. "`UTC`", "`PST`", etc.

%tz

Time Zone Offset from GMT e.g. "

`-0800`

".

## Argument Index

An argument index is specified as a number ending with a "`$`" after the "`%`" and selects the specified argument in the argument list.

## Formatting an Integer

With the `%d` format specifier, you can use an argument of all integral types including byte, short, int, long and BigInteger.

Default formatting:

Specifying a width:

Left-justifying within the specified width:

Pad with zeros:

Print positive numbers with a "+":

_ (Negative numbers always have the "-" included):_

A space before positive numbers.

A "-" is included for negative numbers as per normal.

Use locale-specific thousands separator:

For the US locale, it is ",":

Enclose negative numbers within parentheses ("()") and skip the "-":

Octal output:

Hex output:

Alternate representation for octal and hex output:

Prints octal numbers with a leading "`0`" and hex numbers with leading "`0x`".
    
    
    String.format("|%#o|", 93);
    
    
    String.format("|%#x|", 93);
    
    
    String.format("|%#X|", 93);

## String and Character Conversion

Default formatting:

Prints the whole string.

Specify Field Length

Left Justify Text

Specify Maximum Number of Characters

Field Width and Maximum Number of Characters

## Summary

This guide explained String formatting in Java. We covered the supported format specifiers. Both numeric and string formatting support a variety of flags for alternative formats.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%26lst%3DDZ%26utm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%26lst%3DDZ%26utm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
