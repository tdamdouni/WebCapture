# It’s Time To Start Using CSS Custom Properties

_Captured: 2017-04-20 at 13:21 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/04/start-using-css-custom-properties/)_

Meet the new [Sketch Handbook](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1), our brand **new Smashing book** that will help you master all the tricky, advanced facets of Sketch. Filled with **practical examples and tutorials in 12 chapters**, the book will help you become more proficient in your work. [Get the book now ->](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1)

Today, CSS preprocessors are a standard for web development. One of the main advantages of preprocessors is that they enable you to use variables. This helps you to avoid copying and pasting code, and it simplifies development and refactoring.

We use preprocessors to store colors, font preferences, layout details -- mostly everything we use in CSS.

But preprocessor variables have some limitations:

  * You cannot change them dynamically.
  * They are not aware of the DOM's structure.
  * They cannot be read or changed from JavaScript.

As a silver bullet for these and other problems, the community invented CSS custom properties. Essentially, these look and work like CSS variables, and the way they work is reflected in their name.

Custom properties are opening new horizons for web development.

The usual problem when you start with a new preprocessor or framework is that you have to learn a new syntax.

Each preprocessor requires a different way of declaring variables. Usually, it starts with a reserved symbol -- for example, `$` in Sass and `@` in LESS.

CSS custom properties have gone the same way and use `\--` to introduce a declaration. But the good thing here is that you can learn this syntax once and reuse it across browsers!

You may ask, "Why not reuse an existing syntax?"

[There is a reason](http://www.xanthir.com/blog/b4KT0). In short, it's to provide a way for custom properties to be used in any preprocessor. This way, we can provide and use custom properties, and our preprocessor will not compile them, so the properties will go directly to the outputted CSS. _And_, you can reuse preprocessor variables in the native ones, but I will describe that later.

(Regarding the name: Because their ideas and purposes are very similar, sometimes custom properties are called the CSS variables, although the correct name is CSS custom properties, and reading further, you will understand why this name describes them best.)

So, to declare a variable instead of a usual CSS property such as `color` or `padding`, just provide a custom-named property that starts with `\--`:
    
    
    .box{
      --box-color: #4d4e53;
      --box-padding: 0 10px;
    }

The value of a property may be any valid CSS value: a color, a string, a layout value, even an expression.

Here are examples of valid custom properties:
    
    
    :root{
      --main-color: #4d4e53;
      --main-bg: rgb(255, 255, 255);
      --logo-border-color: rebeccapurple;
    
      --header-height: 68px;
      --content-padding: 10px 20px;
    
      --base-line-height: 1.428571429;
      --transition-duration: .35s;
      --external-link: "external link";
      --margin-top: calc(2vh + 20px);
    
      /* Valid CSS custom properties can be reused later in, say, JavaScript. */
      --foo: if(x > 5) this.width = 10;
    }
    

In case you are not sure what `[:root`](https://developer.mozilla.org/en-US/docs/Web/CSS/:root) matches, in HTML it's the same as `html` but with a higher specificity.

As with other CSS properties, custom ones cascade in the same way and are dynamic. This means they can be changed at any moment and the change is processed accordingly by the browser.

To use a variable, you have to use the `var()` CSS function and provide the name of the property inside:
    
    
    .box{
      --box-color:#4d4e53;
      --box-padding: 0 10px;
    
      padding: var(--box-padding);
    }
    
    .box div{
      color: var(--box-color);
    }
    

The `var()` function is a handy way to provide a default value. You might do this if you are not sure whether a custom property has been defined and want to provide a value to be used as a fallback. This can be done easily by passing the second parameter to the function:
    
    
    .box{
      --box-color:#4d4e53;
      --box-padding: 0 10px;
    
      /* 10px is used because --box-margin is not defined. */
      margin: var(--box-margin, 10px);
    }
    

As you might expect, you can reuse other variables to declare new ones:
    
    
    .box{
      /* The --main-padding variable is used if --box-padding is not defined. */
      padding: var(--box-padding, var(--main-padding));
    
      --box-text: 'This is my box';
    
      /* Equal to --box-highlight-text:'This is my box with highlight'; */
      --box-highlight-text: var(--box-text)' with highlight';
    }
    

As we got accustomed to with preprocessors and other languages, we want to be able to use basic operators when working with variables. For this, CSS provides a `calc()` function, which makes the browser recalculate an expression after any change has been made to the value of a custom property:
    
    
    :root{
      --indent-size: 10px;
    
      --indent-xl: calc(2*var(--indent-size));
      --indent-l: calc(var(--indent-size) + 2px);
      --indent-s: calc(var(--indent-size) - 2px);
      --indent-xs: calc(var(--indent-size)/2);
    }
    

A problem awaits if you try to use a unit-less value. Again, `calc()` is your friend, because without it, it won't work:
    
    
    :root{
      --gap: 10;
    }
    
    .box{
      padding: var(--spacer)px 0; /* DOESN'T work */
      padding: calc(var(--spacer)*1px) 0; /* WORKS */
    }
    

Before talking about CSS custom property scopes, let's recall JavaScript and preprocessor scopes, to better understand the differences.

We know that with, for example, JavaScript variables (`var`), a scope is limited to the functions.

We have a similar situation with `let` and `const`, but they are block-scope local variables.

A `closure` in JavaScript is a function that has access to the outer (enclosing) function's variables -- the scope chain. The closure has three scope chains, and it has access to the following:

  * its own scope (i.e. variables defined between its braces),
  * the outer function's variables,
  * the global variables.
![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/closure-780w-opt.png)[7](https://www.smashingmagazine.com/2017/04/start-using-css-custom-properties/)

> _View large version_

The story with preprocessors is similar. Let's use Sass as an example because it's probably the most popular preprocessor today.

With Sass, we have two types of variables: local and global.

A global variable can be declared outside of any selector or construction (for example, as a mixin). Otherwise, the variable would be local.

Any nested blocks of code can access the enclosing variables (as in JavaScript).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/closure-scss-780w-opt.png)[9](https://www.smashingmagazine.com/2017/04/start-using-css-custom-properties/)

> _(View large version)_

This means that, in Sass, the variable's scopes fully depend on the code's structure.

However, CSS custom properties are inherited by default, and like other CSS properties, they cascade.

You also cannot have a global variable that declares a custom property outside of a selector -- that's not valid CSS. The global scope for CSS custom properties is actually the `:root` scope, whereupon the property is available globally.

Let's use our syntax knowledge and adapt the Sass example to HTML and CSS. We'll create a demo using native CSS custom properties. First, the HTML:
    
    
    global
    <div class="enclosing">
      enclosing
      <div class="closure">
        closure
      </div>
    </div>
    

And here is the CSS:
    
    
    :root {
      --globalVar: 10px;
    }
    
    .enclosing {
      --enclosingVar: 20px;
    }
    
    .enclosing .closure {
      --closureVar: 30px;
    
      font-size: calc(var(--closureVar) + var(--enclosingVar) + var(--globalVar));
      /* 60px for now */
    }
    

So far, we haven't seen how this is any different from Sass variables. However, let's reassign the variable after its usage:

In the case of Sass, this has no effect:
    
    
    .closure {
      $closureVar: 30px; // local variable
      font-size: $closureVar +$enclosingVar+ $globalVar;
      // 60px, $closureVar: 30px is used
    
      $closureVar: 50px; // local variable
    }
    

But in CSS, the calculated value is changed, because the `font-size` value is recalculated from the changed `\--closureVar` value:
    
    
    .enclosing .closure {
      --closureVar: 30px;
    
      font-size: calc(var(--closureVar) + var(--enclosingVar) + var(--globalVar));
      /* 80px for now, --closureVar: 50px is used */
    
      --closureVar: 50px;
    }
    

That's the first huge difference: If you reassign a custom property's value, the browser will **recalculate all variables and `calc()` expressions** where it's applied.

Suppose we wanted to use the default `font-size` for the block, except where the `highlighted` class is present.

Here is the HTML:
    
    
    <div class="default">
      default
    </div>
    
    <div class="default highlighted">
      default highlighted
    </div>
    

Let's do this using CSS custom properties:
    
    
    .highlighted {
      --highlighted-size: 30px;
    }
    
    .default {
      --default-size: 10px;
    
      /* Use default-size, except when highlighted-size is provided. */
      font-size: var(--highlighted-size, var(--default-size));
    }
    

Because the second HTML element with the `default` class carries the `highlighted` class, properties from the `highlighted` class will be applied to that element.

In this case, it means that `\--highlighted-size: 30px;` will be applied, which in turn will make the `font-size` property being assigned use the `\--highlighted-size`.

Everything is straightforward and works:

Now, let's try to achieve the same thing using Sass:
    
    
    .highlighted {
      $highlighted-size: 30px;
    }
    
    .default {
      $default-size: 10px;
    
      /* Use default-size, except when highlighted-size is provided. */
      @if variable-exists(highlighted-size) {
        font-size: $highlighted-size;
      }
      @else {
        font-size: $default-size;
      }
    }
    

The result shows that the default size is applied to both:

This happens because all Sass calculations and processing happen at compilation time, and of course, it doesn't know anything about the DOM's structure, relying fully on the code's structure.

As you can see, custom properties have the advantages of variables scoping and add the usual cascading of CSS properties, being aware of the DOM's structure and following the same rules as other CSS properties.

The second takeaway is that CSS custom properties are **aware of the DOM's structure and are dynamic**.

CSS custom properties are subject to the same rules as the usual CSS custom properties. This means you can assign any of the common CSS keywords to them:

  * `inherit`  
This CSS keyword applies the value of the element's parent.
  * `initial`  
This applies the initial value as defined in the CSS specification (an empty value, or nothing in some cases of CSS custom properties).
  * `unset`  
This applies the inherited value if a property is normally inherited (as in the case of custom properties) or the initial value if the property is normally not inherited.
  * `revert`  
This resets the property to the default value established by the user agent's style sheet (an empty value in the case of CSS custom properties).

Here is an example:
    
    
    .common-values{
      --border: inherit;
      --bgcolor: initial;
      --padding: unset;
      --animation: revert;
    }
    

Let's consider another case. Suppose you want to build a component and want to be sure that no other styles or custom properties are applied to it inadvertently (a modular CSS solution would usually be used for styles in such a case).

But now there is another way: to use the `[all` CSS property](https://developer.mozilla.org/en/docs/Web/CSS/all). This shorthand resets all CSS properties.

Together with CSS keywords, we can do the following:
    
    
    .my-wonderful-clean-component{
      all: initial;
    }
    

This reset all styles for our component.

Unfortunately, the `all` keyword [doesn't reset custom properties](https://drafts.csswg.org/css-variables/#defining-variables). There is an ongoing [discussion about whether to add the `\--` prefix](https://github.com/w3c/webcomponents/issues/300#issuecomment-144551648), which would reset all CSS custom properties.

So, in future, a full reset might be done like this:
    
    
    .my-wonderful-clean-component{
      --: initial; /* reset all CSS custom properties */
      all: initial; /* reset all other CSS styles */
    }
    

There are many uses of custom properties. I will show the most interesting of them.

The name of these CSS variables is "custom properties," so why not to use them to emulate non-existent properties?

There are many of them: `translateX/Y/Z`, `background-repeat-x/y` (still not cross-browser compatible), `box-shadow-color`.

Let's try to make the last one work. In our example, let's change the box-shadow's color on hover. We just want to follow the DRY rule (don't repeat yourself), so instead of repeating `box-shadow`'s entire value in the `:hover` section, we'll just change its color. Custom properties to the rescue:
    
    
    .test {
      --box-shadow-color: yellow;
      box-shadow: 0 0 30px var(--box-shadow-color);
    }
    
    .test:hover {
      --box-shadow-color: orange;
      /* Instead of: box-shadow: 0 0 30px orange; */
    }
    

One of the most common use cases of custom properties is for color themes in applications. Custom properties were created to solve just this kind of problem. So, let's provide a simple color theme for a component (the same steps could be followed for an application).
    
    
    .btn {
      background-image: linear-gradient(to bottom, #3498db, #2980b9);
      text-shadow: 1px 1px 3px #777;
      box-shadow: 0px 1px 3px #777;
      border-radius: 28px;
      color: #ffffff;
      padding: 10px 20px 10px 20px;
    }
    

Let's assume we want to invert the color theme.

The first step would be to extend all of the color variables to CSS custom properties and rewrite our component. So, the [result would be the same](https://codepen.io/malyw/pen/EZmgmZ):
    
    
    .btn {
      --shadow-color: #777;
      --gradient-from-color: #3498db;
      --gradient-to-color: #2980b9;
      --color: #ffffff;
    
      background-image: linear-gradient(
        to bottom,
        var(--gradient-from-color),
        var(--gradient-to-color)
      );
      text-shadow: 1px 1px 3px var(--shadow-color);
      box-shadow: 0px 1px 3px var(--shadow-color);
      border-radius: 28px;
      color: var(--color);
      padding: 10px 20px 10px 20px;
    }
    

This has everything we need. With it, we can override the color variables to the inverted values and apply them when needed. We could, for example, add the global `inverted` HTML class (to, say, the `body` element) and change the colors when it's applied:
    
    
    body.inverted .btn{
      --shadow-color: #888888;
      --gradient-from-color: #CB6724;
      --gradient-to-color: #D67F46;
      --color: #000000;
    }
    

Below is a demo in which you can click a button to add and remove a global class:

This behavior cannot be achieved in a CSS preprocessor without the overhead of duplicating code. With a preprocessor, you would always need to override the actual values and rules, which always results in additional CSS.

With CSS custom properties, the solution is as clean as possible, and copying and pasting is avoided, because only the values of the variables are redefined.

Previously, to send data from CSS to JavaScript, we often had to [resort to tricks](https://blog.hospodarets.com/passing_data_from_sass_to_js), writing CSS values via plain JSON in the CSS output and then reading it from the JavaScript.

Now, we can easily interact with CSS variables from JavaScript, reading and writing to them using the well-known `.getPropertyValue()` and `.setProperty()` methods, which are used for the usual CSS properties:
    
    
    /**
    * Gives a CSS custom property value applied at the element
    * element {Element}
    * varName {String} without '--'
    *
    * For example:
    * readCssVar(document.querySelector('.box'), 'color');
    */
    function readCssVar(element, varName){
      const elementStyles = getComputedStyle(element);
      return elementStyles.getPropertyValue(`--${varName}`).trim();
    }
    
    /**
    * Writes a CSS custom property value at the element
    * element {Element}
    * varName {String} without '--'
    *
    * For example:
    * readCssVar(document.querySelector('.box'), 'color', 'white');
    */
    function writeCssVar(element, varName, value){
      return element.style.setProperty(`--${varName}`, value);
    }
    

Let's assume we have a list of media-query values:
    
    
    .breakpoints-data {
      --phone: 480px;
      --tablet: 800px;
    }
    

Because we only want to reuse them in JavaScript -- for example, in [Window.matchMedia()](https://developer.mozilla.org/en/docs/Web/API/Window/matchMedia) -- we can easily get them from CSS:
    
    
    const breakpointsData = document.querySelector('.breakpoints-data');
    
    // GET
    const phoneBreakpoint = getComputedStyle(breakpointsData)
      .getPropertyValue('--phone');
    

To show how to assign custom properties from JavaScript, I've created an interactive 3D CSS cube demo that responds to user actions.

It's not very hard. We just need to add a simple background, and then place five cube faces with the relevant values for the `transform` property: `translateZ()`, `translateY()`, `rotateX()` and `rotateY()`.

To provide the right perspective, I added the following to the page wrapper:
    
    
    #world{
      --translateZ:0;
      --rotateX:65;
      --rotateY:0;
    
      transform-style:preserve-3d;
      transform:
        translateZ(calc(var(--translateZ) * 1px))
        rotateX(calc(var(--rotateX) * 1deg))
        rotateY(calc(var(--rotateY) * 1deg));
    }
    

The only thing missing is the interactivity. The demo should change the X and Y viewing angles (`\--rotateX` and `\--rotateY`) when the mouse moves and should zoom in and out when the mouse scrolls (`\--translateZ`).

Here is the JavaScript that does the trick:
    
    
    // Events
    onMouseMove(e) {
      this.worldXAngle = (.5 - (e.clientY / window.innerHeight)) * 180;
      this.worldYAngle = -(.5 - (e.clientX / window.innerWidth)) * 180;
      this.updateView();
    };
    
    onMouseWheel(e) {
      /*…*/
    
      this.worldZ += delta * 5;
      this.updateView();
    };
    
    // JavaScript -> CSS
    updateView() {
      this.worldEl.style.setProperty('--translateZ', this.worldZ);
      this.worldEl.style.setProperty('--rotateX', this.worldXAngle);
      this.worldEl.style.setProperty('--rotateY', this.worldYAngle);
    };
    

Now, when the user moves their mouse, the demo changes the view. You can check this by moving your mouse and using mouse wheel to zoom in and out:

Essentially, we've just changed the CSS custom properties' values. Everything else (the rotating and zooming in and out) is done by CSS.

**Tip:** One of the easiest ways to debug a CSS custom property value is just to show its contents in CSS generated content (which works in simple cases, such as with strings), so that the browser will automatically show the current applied value:
    
    
    body:after {
      content: '--screen-category : 'var(--screen-category);
    }
    

You can check it [in the plain CSS demo](https://codepen.io/malyw/pen/oBWMOY) (no HTML or JavaScript). (Resize the window to see the browser reflect the changed CSS custom property value automatically.)

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/css-variables-780w-opt.png)[20](https://www.smashingmagazine.com/2017/04/start-using-css-custom-properties/)

> _(View large version)_

This means that, you can start using them natively.

If you need to support older browsers, you can learn the syntax and usage examples and consider possible ways of switching or using CSS and preprocessor variables in parallel.

Of course, we need to be able to detect support in both CSS and JavaScript in order to provide fallbacks or enhancements.

This is quite easy. For CSS, you can use a `[@supports` condition](https://developer.mozilla.org/en/docs/Web/CSS/@supports) with a dummy feature query:
    
    
    @supports ( (--a: 0)) {
      /* supported */
    }
    
    @supports ( not (--a: 0)) {
      /* not supported */
    }
    

In JavaScript, you can use the same dummy custom property with the `CSS.supports()` static method:
    
    
    const isSupported = window.CSS &&
        window.CSS.supports && window.CSS.supports('--a', 0);
    
    if (isSupported) {
      /* supported */
    } else {
      /* not supported */
    }
    

As we saw, CSS custom properties are still not available in every browser. Knowing this, you can progressively enhance your application by checking if they are supported.

For instance, you could generate two main CSS files: one with CSS custom properties and a second without them, in which the properties are inlined (we will discuss ways to do this shortly).

Load the second one by default. Then, just do a check in JavaScript and switch to the enhanced version if custom properties are supported:
    
    
    <!-- HTML -->
    <link href="without-css-custom-properties.css"
        rel="stylesheet" type="text/css" media="all" />
    
    
    
    // JavaScript
    if(isSupported){
      removeCss('without-css-custom-properties.css');
      loadCss('css-custom-properties.css');
      // + conditionally apply some application enhancements
      // using the custom properties
    }
    

This is just an example. As you'll see below, there are better options.

According to a [recent survey](https://ashleynolan.co.uk/blog/frontend-tooling-survey-2016-results), Sass continues to be the preprocessor of choice for the development community.

So, let's consider ways to start using CSS custom properties or to prepare for them using Sass.

We have a few options.

One advantage of this method of manually checking in the code whether custom properties are supported is that it works and we can do it right now (don't forget that we have switched to Sass):
    
    
    $color: red;
    :root {
      --color: red;
    }
    
    .box {
      @supports ( (--a: 0)) {
        color: var(--color);
      }
      @supports ( not (--a: 0)) {
        color: $color;
      }
    }
    

This method does have many cons, not least of which are that the code gets complicated, and copying and pasting become quite hard to maintain.

The PostCSS ecosystem provides dozens of plugins today. A couple of them process custom properties (inline values) in the resulting CSS output and make them work, assuming you provide only global variables (i.e. you only declare or change CSS custom properties inside the `:root` selector(s)), so their values can be easily inlined.

This plugin offers several pros: It makes the syntax work; it is compatible with all of PostCSS' infrastructure; and it doesn't require much configuration.

There are cons, however. The plugin requires you to use CSS custom properties, so you don't have a path to prepare your project for a switch from Sass variables. Also, you won't have much control over the transformation, because it's done after the Sass is compiled to CSS. Finally, the plugin doesn't provide much debugging information.

I started using CSS custom properties in most of my projects and have tried many strategies:

  * Switch from Sass variables to pure CSS custom properties.
  * Use CSS variables in Sass to detect whether they are supported.

As a result of that experience, I started looking for a solution that would satisfy my criteria:

  * It should be easy to start using with Sass.
  * It should be straightforward to use, and the syntax must be as close to native CSS custom properties as possible.
  * Switching the CSS output from the inlined values to the CSS variables should be easy.
  * A team member who is familiar with CSS custom properties would be able to use the solution.
  * There should be a way to have debugging information about edge cases in the usage of variables.

As a result, I created css-vars, a Sass mixin that you can [find on Github](https://github.com/malyw/css-vars). Using it, you can sort of start using CSS custom properties syntax.

To declare variable(s), use the mixin as follows:
    
    
    $white-color: #fff;
    $base-font-size: 10px;
    
    @include css-vars((
      --main-color: #000,
      --main-bg: $white-color,
      --main-font-size: 1.5*$base-font-size,
      --padding-top: calc(2vh + 20px)
    ));
    

To use these variables, use the `var()` function:
    
    
    body {
      color: var(--main-color);
      background: var(--main-bg, #f00);
      font-size: var(--main-font-size);
      padding: var(--padding-top) 0 10px;
    }
    

This gives you a way to control all of the CSS output from one place (from Sass) and start getting familiar with the syntax. Plus, you can reuse Sass variables and logic with the mixin.

When all of the browsers you want to support work with CSS variables, then all you have to do is add this:
    
    
    $css-vars-use-native: true;
    

Instead of aligning the variable properties in the resulting CSS, the mixin will start registering custom properties, and the `var()` instances will go to the resulting CSS without any transformations. This means you'll have fully switched to CSS custom properties and will have all of the advantages we discussed.

If you want to turn on the useful debugging information, add the following:
    
    
    $css-vars-debug-log: true;
    

This will give you:

  * a log when a variable was not assigned but was used;
  * a log when a variable is reassigned;
  * information when a variable is not defined but a default value gets passed that is used instead.

Now you know more about CSS custom properties, including their syntax, their advantages, good usage examples and how to interact with them from JavaScript.

You have learned how to detect whether they are supported, how they are different from CSS preprocessor variables, and how to start using native CSS variables until they are supported across browsers.

This is the right time to start using CSS custom properties and to prepare for their native support in browsers.

_(al)_
