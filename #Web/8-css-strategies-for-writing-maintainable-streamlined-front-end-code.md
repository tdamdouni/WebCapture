# 8 CSS Strategies for Writing Maintainable, Streamlined Front-End Code

_Captured: 2017-12-20 at 11:42 from [dzone.com](https://dzone.com/articles/8-css-strategies-for-writing-maintainable-streamli-1?edition=347096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-19)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Writing basic CSS and HTML is one of the first things we learn as web developers. Yet I've encountered many applications where it's apparent that no one really took the time to really think about the longevity and maintainability of development on the front-end.

I think this is mainly due to the fact that many developers lack a deep understanding of any kind of strategy to organize their CSS/HTML and JavaScript.

It's important to me and our team here to prioritize writing maintainable front-end code. Though we have several clients who have worked with us for many years, it's always important to keep in mind that you won't be the only person working on an application forever. Just because your one-off elements and configurations make sense to _you_, doesn't mean they'll make sense to the next person who might inherit the application.

In order to prevent this post from being too long, I'll mostly touch on CSS organization today. JavaScript organization is an entirely different can of worms.

This post is intended to be less of a rulebook and more of a guidebook of things to think about as you're writing CSS. I encourage you to find your own processes, but the goal here is to make your CSS consistent, uncomplicated, and easy to work with.

Here are 8 tips for keeping your CSS organized and easy to maintain for the long haul.

## 1\. Don't Write Style Definitions That Don't Need to Be There

For example: be mindful about writing `display:block;` on anything because many elements have that style by default.

Another example of this would be defining font-sizes on elements that would inherit the body font size that you're looking to have defined anyway.

The goal here is twofold:

  * Reduce the length of your CSS file so it's easier to navigate.
  * Be explicit about what your CSS class actually needs to do instead of defining a bunch of junk that would have happened already.

A common issue here is lingering CSS that isn't cleaned up, when, for brevity's sake, it can be removed entirely.

## 2\. Think About Your CSS as Reusable Components

Instead of thinking of your CSS elements as specific forms or elements on each individual page, you'll reduce a lot of the complexity if you can define re-usable CSS utilities and components for yourself to use.

Writing classes that are intended to be reused does a few things:

  * It assures that your designs will stay consistent between different pages. When you share your CSS class across many pages, you know that when you change that one class it will change on every single page that it appears on.
  * It makes writing CSS really fast. For one thing, if most of your styles are defined as utilities and classes that you know about, you don't have to spend a whole lot of time refreshing and recreating styles that already exist elsewhere in the app.

## 3\. Define Utilities in Your CSS to DRY up Your CSS

We define 'utilities' as a CSS class that is really only intended to do a specific thing, rather than encapsulating a whole element.

You'll see this strategy used often in popular CSS frameworks like Bootstrap and Foundation.

Some examples of this that you see in popular frameworks are:

For example, with `.hide`, instead of having to write out a new class every single time you want to hide an element on the page, you can just slap the `.hide` class on your element and it will make the element `display: none;`.

We've come up with our own utility file that gets shared across applications with some common utilities we use to reduce the need to write out specific styles for each element.

A good example of this is how we use margin and padding utilities. Here's a simplified example of what our padding utilities look like (we also have some for margins, right/left only padding, etc):

By combining a bunch of these utilities, we can stay consistent with the pixel counts for our spacing as well as quickly mark up a page without having to write very much CSS at all.

The idea behind utilities is that you think you're likely to use them more than once. If it's a one-off style, or if you think the combo of styles will be used often, it may work better as its own CSS class.

## 4\. Avoid Nesting Until You Absolutely Need It

Say there is a form with some checkboxes. In this one particular case, you need your checkboxes to be inline from each other (side by side).

So you attempt to write your style like this:

Then down the road, you realize that you need one of the links in your list element to actually be black. So you attempt to write a utility class for black links:

This `.link--black` link is going to be overwritten by CSS specificity and will not be able to overpower the `.my-form li a` style.

That may be your intention now to make sure that all anchor tags inside your list element are red, but you don't know what the future holds for that element and what design changes may be made.

You might be reading this and ask, "_Ok Corinne, but how do you resolve the above problem?_ "

With the above example, you should understand that anchor tag color should be a variant away from the default link color.

So, in this case, I would be 100% ok with defining an additional utility class to handle the red links. So here's an example of what that would look like in practice:

Then adding it to every `li` element in the HTML.

I would be making the assumption here that this red link is going to need to be used somewhere else in the app someday. I don't want to nest it into `.user-form` because then I'll have to write out another style in the future to account for the other time a red link is needed.

Also, because I defined my hover on my anchor, the red link will get a black hover without me having to define any additional styles.

## 5\. Utilize BEM to Prevent Over-Nesting

A strategy that can really prevent over-nesting is a naming strategy called [BEM (Block Element Modifier)](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/).

A good example of using BEM would be when you have a component with really specific styling that would be too messy and complicated to use utilities for.

An example of that would look like this:
    
    
      <img src=”person.jpg” class=”profile__photo”/>

You can see from this example, I can see right from my stylesheet that `.profile__photo` is nested within `.profile` without actually having to nest the class. That's really the greatest thing about BEM, and why I recommend using it.

## 6\. Only Use !important as a Last Resort

Slapping an `!important` definition on a class is a way to make overwriting your code a pain in the neck, especially when you are attempting to work with media queries.

This was one of the headaches that I had with a [certain version of Foundation](https://github.com/zurb/foundation-sites/issues/6024) in which they decided to slap `!important` on their visibility classes.

It was a pain for mobile. For example, if you wanted to have things show for mobile screens, you'd have to override the `.hide` class with another `!important` class for mobile to show it.

_I've never found a valid excuse for using `!important` other than writing over someone else's misplaced !important definition._

## 7\. There Is a time and a Place for Reinventing the Wheel, but Consider Your Options Carefully

An example of reinventing the wheel might be creating your own grid CSS framework in a client project.

In my experience, there's not much to gain by writing this stuff yourself unless you want to know how it works under the hood. There are a ton of edge cases to building your own, and why not use someone else's when it's free and works great already?

That said, it can be a great learning experience to build one yourself - but it's likely that doesn't belong in a production application.

**Ok, but what about JavaScript plugins?**

When talking about JavaScript or jQuery plugins, I would say that the same holds true for really common components that have great integration options with whatever you're using. Some examples of this would be a JavaScript carousel that swaps between photos, or a date picker.

An edge case here can be using some of these plugins with JavaScript frameworks with encapsulated component logic (React, Ember, Angular, etc.). It can sometimes be more trouble than it's worth to get these plugins into these components if what you are trying to do is relatively straightforward.

For example, I would use the out of the box Foundation or Bootstrap modal if I was using a project that was relying on jQuery but would build my own modal in React (simply because it's easier to write a component to handle this over introducing a jQuery plugin into a React component).

## 8\. Care About Your Front-End Code!

Finally, the most important thing that I can suggest to you is that you care about the code you write for your front-end, take ownership of it, and always continue to improve upon it (and yourself!).

I believe this is one of the biggest factors between an application which has long-term maintainability and one that is problematic and difficult to work with.

By following these eight tips when writing CSS, you'll be saving time for both yourself and the inevitable future developer that inherits your code.

**What guidelines do you follow to organize and streamline your CSS? Leave a comment below and let me know.**

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
