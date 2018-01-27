# Getting to Know Custom CSS Properties

_Captured: 2017-12-15 at 09:52 from [dzone.com](https://dzone.com/articles/getting-to-know-custom-css-properties?edition=342156&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-14)_

Tips, tricks and tools for creating your own [data-driven app](https://dzone.com/go?i=247321&u=http%3A%2F%2Fplayground.qlik.com%2Flearn%2Fnoobs%2Fintro%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_1%26utm_campaign%3Ddzone), brought to you in partnership with Qlik.

Today's front-end developers have a plethora of tools to help them create and edit CSS. One of those tools are preprocessors, and one of the major perks of using a preprocessor is the ability to use variables within your styles. This eliminates the need for copying and pasting, which then makes refactoring easier.

When using preprocessor variables, developers tend to define them with colors, font sizes, layout details, etc. This is all fine and dandy, but preprocessor variables have some limitations:

  * **Can not be manipulated by JavaScript.** Preprocessor variables are compiled ahead of time before they get to the browser, as CSS property/value pairs.
  * **Not aware of the DOM or CSSOM.** Just like above, the variables are compiled ahead of time and are not given this opportunity to be aware of these details.
  * **Cannot be inherited.** Defining a preprocessed variable on a selector doesn't mean descendants of that selector can also use the variable.

## The Old School CSS Variable

Before moving on to the topic at hand, it is good to know that CSS has sort of had a quasi-variable, and that is the `currentColor` keyword. This supported variable refers to the current color value of an element.

Although `currentColor` is powerful, it does have its limitations, including only accepting color values.

## Defining Custom CSS Properties

The great creators of the CSS specs, aka the W3, did not inherently create CSS variables. What was created was custom properties, which by their terms are:

> ... a family of custom author-defined properties known collectively as custom properties, which allow an author to assign arbitrary values to a property with an author-chosen name, and the `var()` function, which allow an author to then use those values in other properties elsewhere in the document.

Custom proprieties are just like any other CSS property and can be defined on any element. They use the same inheritance and cascading we all hold dear to our heart. They can be conditional, set inside media queries, and other rules. Also, they can be set inline and in `style` tags.

There are two main parts to CSS custom properties: defining them and reading them.

#### Declaring a Custom Property

Declare a custom property by starting its name with `\--` and then assigning it a value.

Property names are case sensitive. So `\--bodyColor` and `\--BodyColor` are two different custom properties.

#### Reading a Custom Property

To read a CSS custom property, all one has to do is use the `var` function:

Above, we defined a custom property `linkColor`on the`:root`pseudo-class, and then used the `var` function to get the value of the property to set the link color value. Since we defined the `linkColor` on the `:root` pseudo-class, we have access to the `linkColor` variable within the link selector. But, take a look at this example:

In the above example, we define `linkColor` in the link selector but we try to reference it in the button selector. Since we defined `linkColor` in the link selector, `linkColor` will not be defined. So we will end up with a color value of `inherited`.

Something to point out is that with custom properties, the computed value, if not found, will either be `initial` or `inherited` depending on the specific property at hand.

To help with this situation where our custom property might not be defined or might not have a value when it is used, the `var` function has a fallback argument.

In the above situation, if `headingColor` was never defined or given a value, the `h1` will fall back to the color red.

## Changing Custom CSS Properties Without JavaScript

Let's start off with a very simple example of changing a custom property on hover:

As you can see, the on hover for the button redefines the value of the `buttonBackground` to blue.

Yes, I know this is a fairly simple example and could have been done without custom properties. But what happens if we were changing several other properties and values at once? This ability allows us to create more readable code. Let's look at a little more advanced example.
    
    
    @media screen and (min-width: 768px) {

Now, let's consider the above. As you can see, we set `borderRadius` to 10 pixels in the root. We then use this custom property in the value of our button's `border-radius` value. But the cool thing is that we also redefine that custom property in our media query to be slightly larger. So if we hit a breakpoint of 768 or larger, then our button will have a slightly larger border radius.

## Changing Custom CSS Properties With JavaScript

Now where custom properties start to shine is their ability to be used with JavaScript.

The two main parts we need to do when working with CSS custom properties in JavaScript is to read the property and set a new value on the property.

#### Get the Value of a Custom Property

To get the value of an inline custom property value, you simply use the following:

To get the custom property value from within the style sheet or when it's inherited:

I would use the above way to get the value because it will work for inline values  
as well, unlike the first one that was covered.

### Set the Value of a Custom Property

Setting the value of a custom property is very a straightforward one:

The above will set the value of `foo` to 4 inline on the element. Pretty simple,  
right?

## Wrap it Up With a Demo

Let's take a look at a little example that puts this all together.

![](https://s3-us-west-2.amazonaws.com/i.cdpn.io/86577.XeqBdo.19f1bf91-f7c0-4350-90a2-746cad68c8d0.png)

In the above pen, you can see in results view if you move your mouse around the white dot will follow your cursor. A simple demo that shows a few things we just covered in this post. Let's break it down.

Let's look at the JavaScript part:

What we are doing here is binding a simple mouse move event to the document. When the mouse moves, we take the mouse position either vertical or horizontal and divide that value by the view port's width or height to get a number from 0 to 1. This will allow us to use this number as a percentage. After doing these calculations, we then set the CSS custom property values for mouse x and y like so:

After doing this, we now have access to our mouse position in our CSS. How darn cool is that? Let's see exactly how we did that in our CSS:
    
    
    top: calc((100% * var(--mouse-y)) - (var(--ballWidth) * .5));
    
    
    left: calc((100% * var(--mouse-x)) - (var(--ballWidth) * .5));

As you can see in the above CSS snippet, we reference our mouse position properties we set in our JavaScript. We are simply calling them in these two lines:
    
    
    top: calc((100% * var(--mouse-y)) - (var(--ballWidth) * .5));
    
    
    left: calc((100% * var(--mouse-x)) - (var(--ballWidth) * .5));

We take the corresponding mouse position for the direction we want to move the element in and then multiplying by 100% to convert our number to a percentage. So, as our mouse moves, we are updating the mouse variable and our CSS is doing the work of moving the element for us.

## Closing Thoughts

CSS custom properties are a very powerful way for you to spice up your style sheets. They are a way to separate JavaScript behavior and styling, as shown in the ability to set information in the JavaScript for the CSS to use for its styling.

Even if you're using a preprocessor for your CSS, there is still a place for CSS custom properties to be directly embedded in your CSS. The reason being that custom properties can interact with the DOM or CSSOM and can be changed dynamically unlike preprocessor variables.

What do you think?

Explore [data-driven apps](https://dzone.com/go?i=247322&u=http%3A%2F%2Fplayground.qlik.com%2F%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_2%26utm_campaign%3Ddzone) with less coding and query writing, brought to you in partnership with Qlik.
