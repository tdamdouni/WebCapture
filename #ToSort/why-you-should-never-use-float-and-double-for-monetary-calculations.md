# Why You Should Never Use Float and Double for Monetary Calculations

_Captured: 2018-08-26 at 09:59 from [dzone.com](https://dzone.com/articles/never-use-float-and-double-for-monetary-calculatio?edition=387229&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-25)_

> Float and double are bad for financial (even for military use) world, never use them for monetary calculations. If precision is one of your requirements, use `BigDecimal` instead. 

Let's explore this problem with the help of an example:

All floating point values that can represent a currency amount (in dollars and cents) cannot be stored exactly as it is in the memory. So, if we want to store 0.1 dollars (10 cents), float/double can not store it as it is. Instead, the binary can store only a closer approximation value (0.100000001490116119384765625 in decimal). The magnitude of this problem becomes significant (known as loss of significance) when we repetitively do arithmetic operations (multiply or divide) using these two data types. Below, we will demonstrate what this may look like.

Here is an example of the loss of precision using double:
    
    
            for (int i = 0; i < 100; i++) {
    
    
            System.out.println("total = " + total);

Program output:

The output should have been `20.20` (20 dollars and 20 cents), but the floating point calculation made it `20.19999999999996`. This is the loss of precision (or loss of significance).

## Cause of Loss of Significance

### ** Floating-Point Arithmetic **

In computing, the floating-point arithmetic (FP) is an arithmetic using a formulaic representation of real numbers as an approximation to support a trade-off between range and precision.

**According to [Wikipedia](https://en.wikipedia.org/wiki/Floating-point_arithmetic):**

"Whether or not a rational number has a terminating expansion depends on the base. For example, in base-10, the number 1/2 has a terminating expansion (0.5) while the number 1/3 does not (0.333…). In base-2 only rationals with denominators that are powers of 2 (such as 1/2 or 3/16) are terminating. Any rational with a denominator that has a prime factor other than 2 will have an infinite binary expansion. This means that numbers which appear to be short and exact when written in decimal format may need to be approximated when converted to binary floating-point. For example, the decimal number 0.1 is not representable in binary floating-point of any finite precision; the exact binary representation would have a "1100" sequence continuing endlessly:

e = −4; s = 1100110011001100110011001100110011…, where, as previously, s is the significand and e is the exponent.

When rounded to 24 bits this becomes

e = −4; s = 110011001100110011001101, which is actually 0.100000001490116119384765625 in decimal."

## BigDecimal for the Rescue

BigDecimal represents a signed decimal number of arbitrary precision with an associated scale. BigDecimal provides full control over the precision and rounding of the number value. Virtually, it's possible to calculate the value of pi to 2 billion decimal places using BigDecimal, with available physical memory being the only limit.

That's the reason why we should always prefer BigDecimal or BigInteger for financial calculations.

### Special Notes

Primitive type: int and long are also useful for monetary calculations if the decimal precision is not required.

We should really avoid using the BigDecimal (double value) constructor, and instead, we should really prefer using the BigDecimal(String), because BigDecimal (0.1) results in (0.1000000000000000055511151231257827021181583404541015625) being stored in the BigDecimal instance. In contrast, BigDecimal ("0.1") stores exactly 0.1.

## **What Are Precision and Scale? **

**Precision** is the total number of digits (or significant digits) of a real number.

**Scale** specifies the number of digits after the decimal place. For example, 12.345 has the precision of 5 (total digits) and the scale of 3 (number of digits right of the decimal).

### How Can we Format the BigDecimal Value Without Getting Exponentiation in the Result and Strip the Trailing Zeros?

We might get exponentiation in the calculation result if we do not follow some best practices while using `BigDecimal`. Below is the code snippet that shows a helpful usage example of handling the calculation result with `BigDecimal`.

BigDecimal Rounding:
    
    
            BigDecimal tempBig = new BigDecimal(Double.toString(value));

Program Output

How would you print a given currency value for Indian Locale (INR Currency)?

`NumberFormat` class is designed specifically for this purpose. Currency symbol & Rounding Mode is automatically set based on the locale using `NumberFormat`. Lets see this in action

NumberFormat example

Program output:

That's all, everything is taken care of by `NumberFormat`.

  * The BigDecimal(String) constructor should always be preferred over BigDecimal(Double) because using `BigDecimal(double)`is unpredictable due to the inability of the double to represent 0.1 as exact 0.1.
  * If double must be used for initializing a BigDecimal, use `BigDecimal.valueOf(double)`, which converts the Double value to String using `Double.toString`(double) method
  * Rounding mode should be provided while setting the scale
  * `StripTrailingZeros` chops off all the trailing zeros
  * `toString()` may use scientific notation but, `toPlainString()` will never return exponentiation in its result

## Did You Know?

### ** Using Float, Double Instead of BigDecimal Could Be Fatal for Military**

On February 25, 1991, a [loss of significance in a MIM-104 Patriot missile](http://www.gao.gov/products/IMTEC-92-26) battery prevented it from intercepting an incoming Scud missile in Dhahran, Saudi Arabia, contributing to the death of 28 soldiers from the U.S. Army's 14th Quartermaster Detachment.

### ** Banker's Rounding Mode **

Since the introduction of IEEE 754, the default method (rounded to the nearest decimal, ties to even and is sometimes called Banker's Rounding or `RoundingMode.HALF_EVEN`) is more commonly used in the US. This method rounds the ideal (infinitely precise) result of an arithmetic operation to the nearest representable value and gives that representation as the result. In the case of a tie, the value that would make the significand end in an even digit is chosen.

## Further Reading
