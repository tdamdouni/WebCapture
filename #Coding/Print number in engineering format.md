# Print number in engineering format

_Captured: 2016-04-18 at 09:11 from [stackoverflow.com](http://stackoverflow.com/questions/12311148/print-number-in-engineering-format)_

To get this to work, you have to normalize the decimal first:
    
    
    >>> x = decimal.Decimal('10000000')>>> x.normalize()Decimal('1E+7')>>> x.normalize().to_eng_string()'10E+6'

The reason for this can be discovered by delving in to the source code.

If you examine `to_eng_string()` in the Python 2.7.3 source tree (`Lib/decimal.py` from the gzipped source tar ball [here](http://www.python.org/download/releases/2.7.3/)), it simply calls `__str__` with `eng` set to true.

You can then see that it decides on how many digits go to the left of the decimal initially with:
    
    
    leftdigits = self._exp + len(self._int)

The following table shows what the values are for those two things:
    
    
    ._exp       ._int         len   leftdigits
                             ---------------------------Decimal(1000000)0'1000000'77Decimal('1E+6')6'1'17

The code that continues after that is:
    
    
    if self._exp <=0and leftdigits >-6:# no exponent required
        dotplace = leftdigits
    elifnot eng:# usual scientific notation: 1 digit on left of the point
        dotplace =1elif self._int =='0':# engineering notation, zero
        dotplace =(leftdigits +1)%3-1else:# engineering notation, nonzero
        dotplace =(leftdigits -1)%3+1

and you can see that, unless it already _has_ an exponent in a certain range (`self._exp > 0 or leftdigits <= -6`), none will be given to it in the string representation.

Further investigation shows the reason for this behaviour. Looking at the code itself, you'll see it's based on the `[General Decimal Arithmetic Specification`](http://speleotrove.com/decimal/decarith.html) (PDF [here](http://speleotrove.com/decimal/decarith.pdf)).

If you search that document for `to-scientific-string` (on which `to-engineering-string` is heavily based), it states in part (paraphrased, and with my bold bits):

> The "to-scientific-string" operation converts a number to a string, using scientific notation **if an exponent is needed.** The operation is not affected by the context.
> 
> If the number is a finite number then:
> 
> The coefficient is first converted to a string in base ten using the characters 0 through 9 with no leading zeros (except if its value is zero, in which case a single 0 character is used).
> 
> Next, the adjusted exponent is calculated; this is the exponent, plus the number of characters in the converted coefficient, less one. That is, exponent+(clength-1), where clength is the length of the coefficient in decimal digits.
> 
> **If the exponent is less than or equal to zero and the adjusted exponent is greater than or equal to -6, the number will be converted to a character form without using exponential notation.** In this case, if the exponent is zero then no decimal point is added. Otherwise (the exponent will be negative), a decimal point will be inserted with the absolute value of the exponent specifying the number of characters to the right of the decimal point. "0" characters are added to the left of the converted coefficient as necessary. If no character precedes the decimal point after this insertion then a conventional "0" character is prefixed.

In other words, it's doing what it's doing because that's what the standard tells it to do.
