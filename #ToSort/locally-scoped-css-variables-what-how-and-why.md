# Locally Scoped CSS Variables: What, How, and Why

_Captured: 2017-06-09 at 19:28 from [una.im](https://una.im/local-css-vars/#%F0%9F%92%81)_

CSS Custom Properties (also popularly called CSS Variables) are [here](http://caniuse.com/#feat=css-variables)! This is really exciting because we finally have _true_ variables in CSS! What do I mean by _true_ variables? I mean variables that can be updated and altered dynamically in the file. While we had "variables" with pre/post-processors (like Sass and PostCSS), these "variables" got compiled into CSS and didn't have dynamic capabilities to update their content. This isn't true with CSS variables, which truly store updateable values.

The way you set CSS variables is with a pre-pended `\--` and the way you access them is via `var(--varName)`. In a very elemental way, you can write the following to use a CSS variable that declares the text color to be red:
    
    
    div {
      --color: red;
      color: var(--color);
    }
    

## CSS Variables Are Very Exciting

Lets talk for a moment _why_ dynamic CSS Variables are so much better than what we've had before.

### Dynamic JavaScript + CSS Love

With CSS variables, we can now more easily update values that we determine through JavaScript. This means we don't have to use inline property styles or update class names. We can simply pass values into our CSS variables instead.

To pass values into the `:root`, one can do the following:
    
    
    document.documentElement.style.setProperty('--varName', 'propValue')
    

This writes and/or updates the value to the root of your CSS file. So, if I wanted to update the width of a loader bar to represent the percentage of load time, I could do something like this:
    
    
    function calculateLoadProgress() {
      let loadProgress = 0;
    
      // codes to update loadProgress here
    
      return loadProgress;
    }
    
    // Set width of progress bar
    document.documentElement.style.setProperty('--progressBarWidth', calculateLoadProgress());
    

That's just one example of many! [David Khourshid](https://twitter.com/DavidKPiano) is doing some really interesting explorations using React and JS Physics Libraries to identify values which he then passes back into CSS variables. He gave a _great_ [talk about this at CSS Conf EU](https://www.youtube.com/watch?v=4IRPxCMAIfA&t=1s) recently,.

### Dynamic Property Fragments

Another note that's really cool about CSS variables is how specific we can get within property values. While we previously had to use separate declarations for border properties, we now can use variables to update _any_ portion of a property, including shorthand properties like the border and properties that accept an unknown argument list like drop-shadow and gradients.

Take this example:
    
    
    .button-gradient {
      background: linear-gradient(var(--gradientAngle), var(--gradientStart),var(--gradientStop));
    
      --gradientAngle: 60deg;
      --gradientStart: lightpink;
      --gradientStop: lightyellow;
    }
    
    .button-gradient:hover {
      --gradientAngle: 0deg;
    }
    

We're updating the `\--gradientAngle` and not the entire background property. We can also do this with JavaScript and update these values as the user interacts with any element. Nice 😎.

### Cleaner Components

CSS variables also allow us to write modular code with modifiers in a cleaner way. A typical example for components are multi-style buttons, so let's stick with those. Take a look at the following example:

[ ![Button types example](https://una.im/../images/posts/css-var-scope/buttonsexample.jpg) ](https://codepen.io/una/pen/bRGaBE)

Traditionally, with a naming convention like BEM, we would set classes via a pre/post processor, and then make modifier classes to override the base classes:

In the example above, we're writing a property to override a previously stated property, increasing specificity, file weight, and cluttering our codebases. But with CSS Variables, we **no longer need to override entire base style properties!** We just update their variables!

It can look something like this:

## We Can Do Better with Local Scope

Similar to the one above, most current examples of CSS Variables in [docs](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables), [articles](https://developers.google.com/web/updates/2016/02/css-variables-why-should-you-care), and [demos](https://codepen.io/davidkpiano/pen/vxZEoO), use the `:root` of the CSS file to initiate and access variables.

This is a great way to set global variables, but isn't a necessity. CSS variables don't need to be declared only in the `:root`--they can be declared at any point in the CSS file, and live within the scope at which point they are specified. This is similar to JavaScript variables instantiated with the `let` keyword, which take the scope of their containing block (`{}`) (aka _block scope_). So we can leverage this specificity in our component styling declarations.

![](https://una.im/../images/posts/css-var-scope/04-css-vars.png)CSS Custom Properties are scoped to their containing blocks (`{}`), just like JavaScript variables instantiated with the *let* keyword.

**[Leveraging CSS Variable scope improves the size, specificity, & semantics of our stylesheets](https://twitter.com/share?&via=Una&text=Leveraging CSS Variable scope improves the size, specificity, & semantics of our stylesheets).** That's a lot of alliteration!

For example, `\--buttonBgColor` isn't something we needed to put in `:root` as a global variable (in the earlier example). A cleaner approach would be to rename that variable to just `\--bgColor` and place it within the `<button>` component. This makes it more tightly coupled with its parent component, and makes more semantic sense in its ordering within the CSS file.

A good general rule is as follows: [Use local CSS variables until you need a global variable.](https://twitter.com/share?&via=Una&text=Use local CSS variables until you need a global variable.) Then, work your way up the tree. This reduces a massive list of CSS variables from piling up in your `:root` and makes the code much cleaner when building design systems and custom properties.

## Organization & Example Time

With Sass, we can extend this idea use the nested `&` to rewrite it a little bit cleaner and more visually object-oriented. This is where we can see a neat structure emerging, broken up by:

  1. **Default styles (property specification)**
  2. **Default values (base variables)**
  3. **Variances (updated variables)**

Note: We can and should still leverage `:root` for global variables, like base color styling and sizing resets, but locally scoped variables reduce specificity, thereby reducing size, and also increase semantics.

### Default Values

It's also interesting to note that you can use _default values_ to stub variables in case they don't exist yet. `var()` gives us this capability by accepting two arguments (and can be nested within itself). In the example below, if `\--bgColor` is not defined, the card will take the primary color (red). So we can potentially remove step 2 from the base style for `.button` and just update `\--bgColor` in the modifiers (if we wanted the base button to be the primary color).

### Theming with the Trailing &

If we have more complex components, we can still use this technique, and to make it even more concise, we can combine this with a CSS preprocessor like Sass. Theming buttons inside of card components using the Sass [trailing ampersand](https://una.im/2014/03/06/sass-snippets-the-almighty-ampersand) technique can work like so:

This would make all large buttons have a slightly bigger `\--size` within a card component than they would in any other place. The trailing ampersand allows us to style directly within the element block and outputs to:

So just to demonstrate with our example, lets give `.card` a red border and apply it the above code. We can see that the large pink button is even larger within our makeshift card.

![larger text in the card button](https://una.im/../images/posts/css-var-scope/card-ex.jpg)

## Is it Ready?

CSS Variables are widely supported in browsers today, though support is lacking in Internet Explorer, and Edge is still working on it. However, there are two alternatives if you need to support those browsers and want to get started today.

Current Support is as follows:

Within CSS, we have a way of detecting feature support by using the `@supports` query. (Can we take a minute to note how cool this is too, by the way?). `@supports` is an excellent tool when you want to play with some of the more modern CSS properties like [CSS Grid](https://una.im/css-grid). You can check for variable support and send fallbacks for browsers who don't support it:

Using `@supports` is definitely an option, but may be difficult to wrangle for a functionality like CSS variables (it works really well with Grid though!), so sending a backup value may be a better solution.

### Sending a Backup Value

You can leverage the forgiving style of CSS (pun intended) to send multiple values. First send the value as you normally would, then have a second statement with the variable:

This is redundant for now, but it allow you to slowly ease into using some CSS Variables within an existing codebase, making it easier to refactor once support catches up.

**tl;dr: CSS Variables are super powerful, and scoping them locally makes them an even more powerful tool for clean, modular design systems.**

#### More Resources
