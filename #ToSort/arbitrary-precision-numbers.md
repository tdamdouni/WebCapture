# Arbitrary Precision Numbers

_Captured: 2017-04-21 at 21:25 from [dzone.com](https://dzone.com/articles/arbitrary-precision-numbers?edition=292907&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-21)_

I am working on a system that involves money handling, written in Java. And as you can imagine, one of the challenges is to make sure that money is not appearing or disappearing because of the floating point arithmetic. I asked a few developers how to handle money and one common answer was to use BigDecimal for that. Therefore, I performed a few experiments on the side and discovered few things that you probably won't see after the first look into this class. In this article, I am going to show these discoveries together with the final solution I decided to go with.

## Rounding Errors

Before going into the detailed explanation, let's create an example that shows what happens with floating point numbers. Imagine you want to split $200 between four people. First, two of them will get 1/3 and the other two will get 1/6. Then let's see what happens when you put these parts back together. The following code demonstrates the situation (using Lenovo Yoga, Win 8.1, Java 1.8).
    
    
    double d = b + b + c + c;
    
    
    System.out.println(a);  // 200.0
    
    
    System.out.println(b);  // 66.66666666666667
    
    
    System.out.println(c);  // 33.333333333333336
    
    
    System.out.println(d);  // 200.00000000000003

As you can see, numbers _a_ and _d_ should be equal, but they are not. Since _d_ is greater than _a_, extra cash just appeared. Strictly speaking, this is not acceptable for any financial transaction, regardless of how small the difference is, and therefore a different approach is required. I choose to use BigDecimal, but it's not the only way. So let's start with that.

## Construction and Equality

At the beginning, I constructed a few numbers that are mathematically equal. My expectation was that they would be equal even after wrapping them to the BigDecimal. And here is what happened.

As you can see, my expectation was wrong. If you read the Javadoc, then you can see the reasons behind it. Or, here is my three-point extract from said Javadoc.

  1. The double constructor can be somewhat unpredictable. This has something to do with the binary representation of floating point numbers. String constructors are predictable. So if you want to get an exact number from double, then try taking the path of double -> String -> BigDecimal.

  2. The_ equals_ method doesn't work the same way as natural ordering. This is because BigDecimal is composed of two components called _unscalledValue _and _scale_. The value represented by the number is (unscaledValue × 10-scale). Since both components are part of the e_quals,_ then `true` is returned only if numbers have the same scale (that means _0.2_ and _0.20_ are not equal). The _HashCode_ method follows the contract as well (therefore you can expect different hash codes for _0.2_ and _0.20_).

  3. The_ CompareTo _method works in the same way as natural ordering. Number _a _is just greater than others due to a different constructor.

As a resolution, I always use the constructor that accepts the String while I make sure that the number doesn't have trailing zeros. This gives me consistency.

## Precision and MathContext

Simply put, precision is the number of digits representing the number from the left-most non-zero digit to the right-most digit, **including the trailing zeros**. The precision of 0 is 1. Signature doesn't affect the precision. Here are the examples.

You can see that precision of 0.0002 is 1 and the precision of 0.00020 is 2. Although these numbers are mathematically equal, they have different precision and therefore different scale components! This leads to the issue with the equals method.

Now let's explain MathContext. This is a pairing of precision and instructions of what to do if a number has more digits than the precision (some variation of rounding is performed). Here is an example of how MathContext can change the number.

As you can see, the first two numbers have enough precision to fully capture the number. Therefore, numbers are stored exactly as they are. The third number has only one digit of precision together with instructions to always round down. Therefore, value changed to 100 (100 = 1 × 102). The fourth number is the same, but the rounding is up, so you will get 200 (200 = 2 × 102). And the last number demonstrates what happens when rounding up causes an increase in the scale portion of the number. 1000 can be written with precision 1 as 1000 = 1 × 103. This is how precision and rounding works.

Next, let's look at operations and performance.

### Operations

At first, BigDecimal supports only basic operations. You won't find operations like sqrt, sin, cos, log, and so on. There are published ways on StackOverflow of how to create them, but chances are that in many cases, it's not really worth to use these type of numbers. I would rather strongly consider a way to transform the task and use standard floating point numbers.

If operations are limited to the simplest ones, then, in theory, there are two types. The first type is the one that always produces a terminating decimal expansion (meaning there is always a finite number of digits to express the numbers). This is, for example, the case with addition or multiplication. Then the second type might produce non-terminating decimal expansions. For example, take division: 1/3 = 0.333... Now in order to handle all the operations in a unified way, BigDecimal exposes an API that accepts the optional MathContext parameter for all operations. This gives a universal interface to calculate everything in the required precision.

It might be tempting to limit operations to the ones that produce only terminating decimal expansion. Then everything can be exact, right? That's true. Let's just see how this is useful in real life.

### Performance

To demonstrate the relation between performance and precision, I have run these two tests. The first one is right here.

This one produced a number with 323,228,497 digits and was greater than 0.The whole program took about **35 minutes**.

Now the second test.

This one produces a number with 10,000 digits, that is also greater than 0, and the whole program took about **1 second.**

The examples above are different just in precision. And as you can see, precision can a have huge impact on performance. Exact precision is nice, but you might run into performance trouble. Therefore, make sure precision is reasonably controlled.

## ANumber

Previous sections pointed out some issues with arbitrary precision numbers. Here, I will show you a solution I decided to use. I have been using this for a couple of months and it does the job. My core requirements are:

  * All calculations are exact

  * The equals method works as "naturally" expected

  * For division, there is an option to return a remainder as well

  * Easy interface for comparison methods (<, <=, ==, >, >=)

  * Operations like add, mul, and others accept double arguments as well

  * Having nice interface for easy-to-read printing

And here are the classes together with unit test.

Feel free to take the pieces you like and use them in your project.

Finally, an example from the first section would turn into the following:

Here, with the help of remainders, I was able to get back to the original number **exactly. **Of course, it is up to the application to decide what to do with reminders -- options are open.

## Summary

The BigDecimal class is useful in narrow scope calculations, like simple money handling. If you come into the situation when you need them, then here is what to expect.

  * Be careful about some constructors, hashCode, and equals methods. They might work slightly differently than you would expect.
  * Only limited operations are supported by default.
  * Be aware of precision and non-terminating decimal expansion.
  * There is a tradeoff between precision and required computing power.
  * A wrapper class can help you achieve a simple interface targetted to your needs.
