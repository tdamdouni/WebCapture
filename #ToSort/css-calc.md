# CSS calc()

_Captured: 2018-03-09 at 22:07 from [dzone.com](https://dzone.com/articles/css-calc?edition=365231&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-09)_

Ever wondered what in the world the [calc()](https://www.w3schools.com/cssref/func_calc.asp) property is? Well, you're about to find out!

It can be used for creating **layouts** in CSS. For this purpose, you can also use the [position property](https://kolosek.com/css-position-relative-vs-position-absolute/).

CSS `calc()` is used for **calculations** inside the stylesheet. The `calc()`function allows for the use of **mathematical expressions**:

  * addition (+)
  * subtraction (-)
  * multiplication (*)
  * division (/)

Being able to do math in CSS is a very useful feature, especially when creating complex layouts.

Preprocessors all have the ability to use math functions, but none as powerful as the `calc()` function. Some of the preprocessor abilities include [nesting in SASS and LESS](https://kolosek.com/nesting-in-less-and-sass/).

The main advantage of using the `calc()` property is the **ability to mix different units**. For example, you could divide the percentages with a unitless number or subtract pixels from percentages.

## The Syntax

The important thing to note is that there must be **space on both sides of the operator**.

## Browser Support

The best way to check if any of the CSS properties are supported by browsers is by visiting [CanIUse.com](https://caniuse.com/). We can see that the calc() function has a pretty good browser support, over 94%.

## Positioning Example

A simple example that demonstrates the power of the `calc()` function is positioning a div inside a container.

![](https://kolosek.com/content/images/2018/02/calc_position.png)

In this example, we will see how the `calc()` function helps us **position the child element relative to the parent element**.

Afterward, we can give the elements [some styling](https://kolosek.com/10-ways-to-improve-your-website-design/) and the text [some formatting](https://kolosek.com/css-line-height/).

## Width Example

Another good example might be looking at how to set the width of the element using the `calc()` function.

![](https://kolosek.com/content/images/2018/02/calc_width.png)

This way, the `calc()` function is used to define the **width of the** `.second-child` element **using both the percentage and pixel units**. This is a good demonstration of the unit mixing abilities of this function.

## Conclusion

We hope you learned something new from this article. We have shown you the basics of the `calc()` function, now it's time for you to play around with it and unlock its full potential.

Check out other articles about CSS properties such as [relative font size](https://kolosek.com/css-relative-font-size/) and [CSS positions](https://kolosek.com/css-position-relative-vs-position-absolute/).
