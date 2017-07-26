# Keeping Java Simple

_Captured: 2017-06-27 at 20:48 from [dzone.com](https://dzone.com/articles/keeping-java-simple?edition=305152&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-26)_

Lately, I was hooked on an algorithm challenge from a popular site, and I found it very difficult to provide a decent solution in Java. That solution was not approved, but none of the test cases really did not pass. The solution was not optimized.

But, later, I came up with another solution containing just **3 lines** of code! In my first solution, the number of lines in the code was more than **50!**

Let me explain it to you what it was.

## **Problem Scenario**

There are two players, A and B, taking part in a game with turns. A number is selected at random, initially. The game starts with **A** on turn 1 with B getting the second turn. There are two operations performed by these players, one at a time.

1\. If the number is a power of 2, it is divided by two **( N = N /2 )**

2\. Otherwise, find the square root of the largest number below N and subtract it from N.

The game ends when N = 1.

## **Analysis**

The upper bound of N is **2** to the **power** of **64 - 1**. A really huge number.

The category of this challenge is '**Bitwise operations**'. We need to use bitwise operations in order to implement the algorithm. The most difficult part of the challenge is efficiency and the huge number to calculate.

My normal Java code had difficulty in successfully passing all the test cases.

So what is the solution to this problem?

## **Solution**

The optimal solution is to count all the number of '**1**'s and '**0**'s in the binary format of the input number. If it is even, then B wins the game. Otherwise, A does. This is the most efficient technique to deal with this problem.

The code below does all this for us.

However, these **3** lines of code certainly deserve more explanation.

## **Explanation**

First of all, we read the input in the form of an 'unsigned long value' so that can be store up to 2 to the power of 64 - 1 values. But Java does not have the 'unsigned' concept. This is because a value from 0 to 2 to the power of 64 - 1 is the equivalent of assigning long data type.

The second line needs a thorough explanation.

Let's assume that the input number is **N = 235 **and its binary equivalent is = **11101011**. The next action is to determine the number of operations in the game (mentioned in the problem scenario). This can be done by counting all the '1's and '0's respective to their position of the last '1' in the above binary string.

  * '**1**'s = 5. There are 5 '**1**'s to the left of last '**1**'. (A)

  * '**0**'s = 0. There are zero '**0**' to the right of last '**1**'. (B)

Total number of operations in the game are = **A + B = 5 + 0 = 5**.

But how can we do this?

  1. Flip all the trailing zeros to the right of last '1' (0 of them) and the last '1' to '0'. Then the new binary string becomes '**11101010**'. This is a new number altogether.

  2. In order to get the above new binary string, we need to subtract '**1**' from **N**. So if we subtract **1**  
from the above number, we get the following binary string:

    * 11101011: flip the last '**1**' to '**0**' and in this case, there are no trailing zeros, hence it becomes '**11101010**'. This is equal to **234**, i.e. **N - 1**.

  3. Now count all the '1's in this binary string by calling **Long.countBits()**. This will return the number of operations in the game. If the result is an even number, then **B** wins the game. Otherwise, **A** does. In this particular case, A wins because the total number of '**1**'s are 5, which is an odd number.

All these things were possible with just **3 lines** of code in Java.
