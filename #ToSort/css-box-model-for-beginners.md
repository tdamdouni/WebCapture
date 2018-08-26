# CSS Box Model for Beginners

_Captured: 2018-06-22 at 07:49 from [dzone.com](https://dzone.com/articles/css-box-model-for-beginners?edition=383240&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-21)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Every beginner should first start with the basics. In the case of CSS, the basics are learning the box model. Before proceeding with learning any other CSS concepts, this is the one you should master first!

The box model is the basic building block of CSS.

It does tend to cause confusion with beginner developers so now is the moment to set the record straight. Here you will learn all the basic elements of the box model and how they are all connected.

Before we dive deeper, everyone needs to understand that **every element in web design is a rectangular box**. You have probably heard this multiple times before, but this is an important concept that every developer should be aware of.

Now, let's explain the mysterious box model!

## Structure of the Box Model

As mentioned above, the structure of the box model consists of:

  * **Content** (height and width).
  * **Padding**.
  * **Border**.
  * **Margin**.

These are all the elements the browser needs in order to render a box model. Thankfully, with CSS we can control each of them individually. Let's see how.

In this article, we will use the following code and add to it gradually.

HTML
    
    
    <div class="box">Lorem ipsum dolor amet whatever woke cronut, farm-to-table church-key tousled edison bulb. </div>

CSS

## The Content

The content is pretty clear. It is the content of our element that has a specific width and height. A fixed height and width can be set using the height and width of CSS properties, or they can be determined by the content itself.

![](https://kolosek.com/content/images/2018/05/Group-4.png)

Now, the one thing that is a bit confusing here is the usage of inline or block level elements.

### Using Inline and Block Level Elements

To refresh your memory, the difference between inline and block elements is the fact that **block elements take up 100% of the container width**, while **inline elements only take up the amount of space that the content needs**.

When using **inline** elements it is **not possible** to set a fixed width or height for that element, since the element doesn't have any predetermined width and height (because the width and height are determined by the content). **This can be overcome by converting the element to a block element.**

Unlike inline elements, **when using block-level elements you can easily set a fixed width or height for it**. Since by default the block level elements take up 100% of the container width, we can easily override it by setting a fixed width.

You can also covert your element to **inline-block**. When using inline-block, the element has the **behavior of the inline element** (only take up the space of content), **but you can manipulate it the same way as you can do with a block element**.

Now when we have a block level element we can give it a width and height.

CSS

The result is this:

![](https://kolosek.com/content/images/2018/05/box_2-1.png)

## The Padding

Next, we are going to add some padding to our box.

Padding defines the space between the content and the edge of the box.

![](https://kolosek.com/content/images/2018/05/box_3.png)

Let's see it in action on our example.

CSS

The result:

![](https://kolosek.com/content/images/2018/05/box_4.png)

In the image, we see how padding affects the overall look of the box. There is space of 10px between the content and edge of the box **on all four sides**. We can also add padding to every side individually, using **padding-top, padding-bottom, padding-left, padding-right.**

## The Border

Since we are going from the inside out, the next step would be defining the border. The border surrounds the content, and you don't have to use it, but it still exists. This just means that the border has a width of zero.

![](https://kolosek.com/content/images/2018/05/box_5.png)

Now, we will add a border to our example.

CSS

![](https://kolosek.com/content/images/2018/05/box_6.png)

## The Margin

The final aspect of the box model is the margin. As some of you know, the margin is the space outside of the border. It is the space between elements.

![](https://kolosek.com/content/images/2018/05/box_7.png)

The best way to demonstrate this in a practical example is to show you how two elements are positioned with and without margins.

HTML

CSS

![](https://kolosek.com/content/images/2018/05/box_8.png)

In this example, we see how, without margins, two elements stick together and there is no space between them.

Now, let's add some margins.

CSS

![](https://kolosek.com/content/images/2018/05/box_9.png)

Now, this looks better. We added some space between the boxes. We can also add space on every side of the elements individually using **margin-top, margin-bottom, margin-left, **or** margin-right.**

## Summary

You have made it to the end of this article, congrats! So, what have we learned?

  1. Every element on a web page is basically a box.

  2. The aspects of the box model are content, padding, border, and margin.

  3. When using an inline element you can't set a fixed width or height for that element, while it is possible with a block and inline-block element.

Hopefully, this helped you learn something new or refreshed your memory.

Stay tuned, because in the next article we will talk about another very important property that helps you calculate the width of the box model, **the box-sizing property**.

Thanks for reading!

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
