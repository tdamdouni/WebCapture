# CSS: :before and :after

_Captured: 2018-05-25 at 18:29 from [dzone.com](https://dzone.com/articles/css-before-and-after?utm_source=Top%205&utm_medium=email&utm_campaign=Top%205%202018-05-253)_

The CSS **:before and :after** properties are what are also known as **pseudo elements**. They are used to add something before or after the content of an element. There are a lot of great uses for these pseudo elements, and we are here to explore some of them.

## The Syntax

If we have an element like this one:

`<h2>welcome to our website</h2>`

We can add a pseudo element before it using CSS, like this:

The result will be:

This is a quite simple principle. You are adding content before or after a certain element. It can be extremely helpful when **adding icons, [clearing floats](https://kolosek.com/css-clear-float/)**, and in many other cases.

The **content** property of the pseudo element can be left **empty** with empty quotes like this `content: ""`. This way, you can treat the pseudo element like a **box with no content**. If the content property is removed altogether, the pseudo element **will not work**.

## Adding Icons

Probably the most popular usage of the before and after pseudo elements is using them to **add icons**. Let's look at the markup.

HTML:

CSS:

The result:

Now we have successfully added an icon before the text. Easy, right?

## Clearing Floats

After elements [are floated](https://kolosek.com/css-float/), another one needs to be added in order to clear that float. You can **avoid adding a new element** by simply using a pseudo one.

Let's say we have this situation:

![after_clear_float](https://kolosek.com/content/images/2018/03/after_clear_float.png)

We can use the following code to clear the floats.

HTML:

CSS:

Now, let's take a look at the result.

![after_float_cleared](https://kolosek.com/content/images/2018/03/after_float_cleared.png)

By using this method, we are **clearing the float** and the paragraph is moved below the two elements.

## Using a Background Image

We can also **add a background image** to a pseudo element. This is commonly used when styling a header.

HTML:

CSS:

The result achieved:

## Browser Support

As with everything else in CSS, browser support needs to be checked. By consulting the [Can I Use](https://caniuse.com/#search=%3Abefore) service, we see that these pseudo classes have a high browser support (**over 98%**) and we won't have a headache when using them.

## Summary

Here, we have explained **basic principles** of the CSS pseudo elements. The examples illustrate just some of the many possible usages. Don't worry if it's not completely clear in the beginning. A little practice goes a long way.

Hopefully, this article will help with any future projects. Thank you for reading!
