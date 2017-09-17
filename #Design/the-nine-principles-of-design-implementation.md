# The Nine Principles Of Design Implementation

_Captured: 2017-08-23 at 08:59 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/08/nine-principles-design-implementation/)_

Today, too many websites are still inaccessible. In our new book _Inclusive Design Patterns_, we explore how to craft **flexible front-end design patterns** and make **future-proof and accessible interfaces without extra effort**. Hardcover, 312 pages. [Get the book now!](https://shop.smashingmagazine.com/products/inclusive-design-patterns?utm_source=magazine&utm_campaign=inclusive-design-patterns&utm_medium=html-ad-content-1)

Recently, I was leading a training session for one of our clients on best practices for implementing designs using HTML and CSS. Part of our time included a discussion of processes such as [style-guide-driven development](https://www.smashingmagazine.com/2016/06/designing-modular-ui-systems-via-style-guide-driven-development/)1, approaches such as [OOCSS](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)242 and SMACSS, and modular design. Near the end of the last day, someone asked, "But how will we know if we've done it right?"

At first, I was confused. I had just spent hours telling them everything they need to "do it right." But after thinking about it, I realized the question was rooted in a deeper need to guide and evaluate what is often a set of subjective choices — choices that are sometimes made by a lot of different people at different times. Stuff like consistent naming conventions and live style guides are the end result, but these "best practices" are rooted in a deeper set of values that aren't always explicit. For example, specific advice like "[Minimize the number of classes with which another class collaborates](http://emphaticsolutions.com/2011/03/19/object-oriented-css-for-programmers.html)3" isn't as helpful without a broader appreciation for modularity.

I realized that in order to really know whether our work is any good, we need a higher level of principles that can be used as a measuring stick for implementing design. We need something that is removed from a specific language like CSS or an opinionated way of writing it. Much like the [universal principles of design](https://www.smashingmagazine.com/2015/02/design-principles-dominance-focal-points-hierarchy/)4 or [Nielsen's usability heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)5, we need something to guide the way we implement design without telling us exactly how to do it. To bridge this gap, I've compiled nine principles of design implementation.

#### Architecting Progressive Single-Page Applications Link

By using just a couple of CSS tricks, less than 0.5 KB of JavaScript and, importantly, some static HTML, Heydon Pickering introduces an experimental solution for progressively enhanced single-page applications. [Read more →](https://www.smashingmagazine.com/2015/12/reimagining-single-page-applications-progressive-enhancement/)6

This is not a checklist. Instead, it is a set of broad guidelines meant to preserve an underlying value. It can be used as a guide for someone working on implementation or as a tool to evaluate an existing project. So, whether you're reviewing code, auditing CSS or interviewing candidates for a role on your team, these principles should provide a structure that transcends specific techniques and results in a common approach to implementing design.

  1. **Structured**  

The document is written semantically and logically, with or without styles.

  2. **Efficient**  

The least amount of markup and assets are used to achieve the design.

  3. **Standardized**  

Rules for common values are stored and used liberally.

  4. **Abstracted**  

Base elements are separated from a specific context and form a core framework.

  5. **Modular**  

Common elements are logically broken into reusable parts.

  6. **Configurable**  

Customizations to base elements are available through optional parameters.

  7. **Scalable**  

The code is easily extended and anticipates enhancements in the future.

  8. **Documented**  

All elements are described for others to use and extend.

  9. **Accurate**  

The final output is an appropriate representation of the intended design.

To make it easier to follow along and see how each principle applies to a project, we'll use a design mockup from one of my projects as the basis for this article. It's a special landing page promoting daily deals on an existing e-commerce website. While some of the styles will be inherited from the existing website, it's important to note that the majority of these elements are brand new. Our goal is to take this static image and turn it into HTML and CSS using these principles.

![This card layout for products is brand new to our e-commerce website.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-1-daily-deals-opt.png)7  
This "card" layout for products is brand new to our e-commerce website. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-1-daily-deals-opt.png)8)

### 1\. Structured Link

**The document is written semantically and logically, with or without styles.**

The principle here is that the content of our document (HTML) has meaning even without presentational styles (CSS). Of course, that means we're using properly ordered heading levels and unordered lists — but also using meaningful containers such as `<header>` and `<article>`. We shouldn't skip out on using things such as ARIA labels, `alt` attributes and any other things we might need for accessibility.

It might not seem like a big deal, but it does matter whether you [use an anchor tag or a button](https://www.smashingmagazine.com/2016/05/developing-dependency-awareness/)9 — even if they're visually identical — because they communicate different meanings and provide different interactions. Semantic markup communicates that meaning to search engines and assistive technologies and even makes it easier to repurpose our work on other devices. It makes our projects more future-proof.

Creating a well-structured document means learning to write [semantic HTML](https://www.w3schools.com/html/html5_semantic_elements.asp)10, familiarizing yourself with [W3C standards](https://www.w3.org/standards/)11 and even [some best practices](http://learn.shayhowe.com/html-css/writing-your-best-code/)12 from other experts, and taking the time to make your code accessible. The simplest test is to look at your HTML in a browser with no styles:

  * Is it usable without CSS?
  * Does it still have a visible hierarchy?
  * Does the raw HTML convey meaning by itself?

One of the best things you can do to ensure a structured document is to start with the HTML. Before you think about the visual styles, write out the plain HTML for how the document should be structured and what each part means. Avoid `div`s and think about what an appropriate wrapping tag would be. Just this basic step will go a long way toward helping you to create an appropriate structure.

    
    
    <section>
      <header> 
        <h2>Daily Deals</h2>
        <strong>Sort</strong> <span class="caret"></span>
        <ul>
          <li><a href="#">by ending time</a></li>
          <li><a href="#">by price</a></li>
          <li><a href="#">by popularity</a></li>
        </ul>
        <hr />
      </header>
      
      <ul>
        <li aria-labelledby="prod7364536">
          <a href="#">
            <img src="prod7364536.jpg" alt="12 Night Therapy Euro Box Top Spring" />
            <small>Ends in 9:42:57</small>
            <h3 id="prod7364536">12" Night Therapy Euro Box Top Spring</h3>
            <strong>$199.99</strong>
            <small>List $299</small>
            <span class="callout">10 Left</span>
          </a>
        </li>
      </ul>
    </section>
    

Starting with HTML only and thinking through the meaning of each element results in a more structured document. Above, you can see I’ve created the entire markup without using a single `div`.

### 2\. Efficient Link

**The least amount of markup and assets are used to achieve the design.**

We have to think through our code to make sure it's concise and doesn't contain unnecessary markup or styles. It's common for me to review code that has `div`s within `div`s within `div`s using framework-specific class names just to achieve a block-level element that's aligned to the right. Often, an overuse of HTML is the result of not understanding CSS or the underlying framework.

![Bloated HTML and CSS can be rewritten to be more efficient.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-2-efficient-2-opt.png)13  
Here's an example of the common over-reliance on frameworks, which creates bloated HTML and CSS, and a case of `div`itis. Think about what the markup needs to be, not what the framework can do to achieve the desired design. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-2-efficient-large-opt.png)14)

In addition to the markup and CSS, we might need other external assets, such as icons, web fonts and images. There are a lot of great methods and opinions about the best ways to implement these assets, from custom icon fonts to base64 embeds to external SVGs. Every project is different, but if you've got a 500-pixel PNG for a single icon on a button, chances are you're not being intentional about efficiency.

![A style guide is great, but a live style guide generated directly from the CSS is life-changing.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-3-efficient-800w-opt.png)15  
It's not always about file size. Considering the implications of using a base64’ed icon in CSS versus an external asset such as an image or icon font is important to writing efficient code. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-3-efficient-large-opt.png)16)

When evaluating a project for efficiency, there are two important questions to ask:

  * Could I accomplish the same thing with less code?
  * What is the best way to optimize assets to achieve the smallest overhead?

Efficiency in implementation also overlaps with the following principles on standardization and modularity, because one way of being efficient is to implement designs using set standards and to make them reusable. Creating a mixin for a common box shadow is efficient, while also creating a standard that is modular.

### 3\. Standardized Link

**Rules for common values are stored and used liberally.**

Creating standards for a website or app is usually about establishing the rules that govern things like the size of each heading level, a common gutter width and the style for each button type. In plain CSS, you'd have to maintain these rules in an external style guide and remember to apply them correctly, but using a preprocessor such as LESS or Sass is best, so that you can store them in variables and mixins. The main takeaway here is to **value standards over pixel-perfect designs**.

So, when I get a design mockup with a gutter width of 22 pixels, instead of the 15 pixels we're using elsewhere, I'm going to assume that such precision is not worth it and instead will use the standard 15-pixel gutter. Taken a step further, all of the spacing between elements will use this standard in multiples. An extra wide space is going to be `$gutter-width * 2` (equalling 30 pixels), rather than a hardcoded value. In this way, the entire app has a consistent, aligned feel.

    
    
    .product-cards {
      li {
        display: inline-block;
        padding: @gutter-width/4;
        color: @text-color;
        text-decoration: none;
        background-color: @color-white;
        .border;
        margin-bottom: @gutter-width/2;
        margin-right: @gutter-width/2;
      }
    }
     
    .product-status {
      font-size: @font-size-small;
      color: @grey-darker;
      font-weight: @font-weight-bold;
      margin-bottom: @gutter-width/4;
    }
    

Because we're using standardized values derived from LESS variables or mixins, our CSS doesn't have any numerical values of its own. Everything is inherited from a centralized value.

To check for standardization, review the CSS and look for any hardcoded unit: pixels, HEX colors, ems or pretty much any numerical value.

  * Should these units use an existing standard value or variable?
  * Is the unit reused such that it would benefit from a new variable? Perhaps you've realized that this is the second time you’ve applied a partially opaque background, and the same opacity is needed both times.
  * Could the unit be derived from the calculation of an existing variable? This is useful for variations on color — for example, using a standard color and performing a calculation on it to get something 10% darker, rather than hardcoding the resulting HEX value.

As often as possible, I use standard values and create new ones only as an exception. If you find yourself adjusting an element 5 pixels here and 1 pixel there, chances are your standards are being compromised.

In my experience, the majority of preprocessed CSS should use centralized variables and mixins, and you should see almost no numeric, pixel or HEX values in individual components. Occasionally, adding a few pixels to adjust the position of an individual component might be appropriate — but even those cases should be rare and cause you to double-check your standards.

### 4\. Abstracted Link

**Base elements are separated from a specific context and form a core framework.**

I originally called this principle "frameworked" because, in addition to creating the one specific project you're working on now, you should also be working toward a design system that can be used beyond the original context. This principle is about identifying larger common elements that need to be used throughout the entire project or in future projects. This starts as broad as typography and form field inputs and all the way up to different navigation designs. Think of it this way: If your CSS were going to be open-sourced as a framework, like Bootstrap or Foundation, how would you separate the design elements? How would you style them differently? Even if you're already using Bootstrap, chances are that your project has base elements that Bootstrap doesn't provide, and those also need to be available in your project's design system.

![Comparing the design to our abstracted CSS framework.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-4-abstracted-800w-opt.png)17  
Though none of these design elements currently exists in our e-commerce website, most of them are useful enough to abstract and make available to the entire framework. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-4-abstracted-large-opt.png)18)

The key here is to think of each element in more generic terms, rather than in the specific context of your project. When you look at a particular element, break it into parts, and give each part overall styles that that element would have regardless of the specific implementation you're working with now. The most common elements are typography (heading styles, line height, sizes and fonts), form elements and buttons. But other elements should be "frameworked" too, like the callout tag or any special price formatting that might have been designed for our Daily Deals but would also be useful elsewhere.

When checking your project for abstraction, ask:

  * How would I build this element if I knew it was going to be reused in another context with different needs?
  * How can I break it into parts that would be valuable throughout the entire application?

Thinking through a more general implementation of each element is key. These pieces should be stored as completely separate and independent classes or, better yet, as separate LESS or Sass files that can be compiled with the final CSS.

This principle is easier in a [web component](https://www.smashingmagazine.com/2016/12/styling-web-components-using-a-shared-style-sheet/)19 or module app architecture because the widgets are probably already separated in this way. But it has as many implications for our thinking as anything else. We should always be **abstracting our work from the context it was derived from** to be sure we're creating something flexible.

### 5\. Modular Link

**Common elements are logically broken into reusable parts.**

Overlapping with the "Abstracted" principle, making our designs modular is an important part of establishing a concrete design system that is easy to work with and maintain. There is a fine line between the two, but the difference is important in principle. The nuance is that, while global base elements need to be abstracted from their context, individual items in context also need to be reusable and to maintain independent styles. Modules may be unique to our app and not something we need available in the entire framework — but they still need to be reusable so that we aren't duplicating code every time we use that module.

For example, if you're implementing the product card list from the previous example for a Daily Deals landing page, instead of making the HTML and CSS specific to Daily Deals, with class names like `daily-deal-product`, instead create a more general `product-cards` class that includes all of the abstracted classes yet could also be reused outside of the Daily Deals page. This would probably result in three separate places where your component gets its styles:

  * **base CSS**  

This is the underlying framework, including default values for typography, gutters, colors and more.

  * **CSS components**  

These are the abstracted parts of the design that form the building blocks of the overall design but can be used in any context.

  * **parent components**  

These are the `daily-deal` component (and any children) containing styles or customizations specific to Daily Deals. For many, this will be an actual JavaScript web component, but it could just be a parent template that includes the HTML necessary to render the entire design.

![Modular components often inherit styles from the framework and only need CSS for layout.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-5-modular-800w-opt.png)20  
Making your implementation modular results in a structure that looks something like this, where each component might have a few styles for spacing or position, but where most of the CSS is inherited from the framework. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-5-modular-large-opt.png)21)

Of course, you can take this too far, so you'll have to exercise judgement. But for the most part, everything you create should be as reusable as possible, without overcomplicating long-term maintenance.

### 6\. Configurable Link

**Customizations to base elements are available through optional parameters.**

Part of building a design system is about thinking through options that the project might need now or in the future. It's not enough to implement the design only as prescribed. We also have to consider what parts might be optional, turned on or off through a different configuration.

For example, the callout flags in our design show only three variations of color, all pointing to the left. Rather than create three separate classes, we'll create a default class and add additional class names as the optional parameters. Beyond that, I think someone might come along and want to point the flag right for a different context. In fact, using our default brand colors for these callouts is also useful, even though the design doesn't specifically call for it. We’d write the CSS specifically to account for this, including both left and right as options.

![These callouts have options that allow for easily creating different styles.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-6-configurable-opt.png)22  
Our default callout actually uses default brand colors, while the special Daily Deals callouts have the styles we want for our landing page. We’d also create some alternate options, like a different color or right-pointing tip. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-6-configurable-opt.png)23)

While you're thinking through a particular design element, think about the options that might be valuable. An important part of understanding this is thinking critically about other contexts in which this element might be reused.

  * What parts could be configured, optional or enabled through an external variable?
  * Would it be valuable for the color or position of the element to be able to change?
  * Would it be helpful to provide small, medium and large sizes?

Using a methodology such as BEM, [OOCSS](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)242 or SMACSS to organize your CSS and establish naming conventions can help you make these decisions. Working through these use cases is a big part of building a configurable design system.

### 7\. Scalable Link

**The code is easily extended and anticipates enhancements in the future.**

In the same spirit as the principle of "Configurable," our implementation also has to expect changes in the future. While building in optional parameters is useful, we can't anticipate everything that our project will need. Therefore, it's important to also consider how the code we're writing will affect future changes and intentionally organize it so that it's easy to enhance.

Building scalable CSS usually requires me to use more advanced features of LESS and Sass to write mixins and functions. Because all of our call out flags are the same except for the colors, we can create a single LESS mixin that will generate the CSS for each call out without the need to duplicate code for each variation. The code is designed to scale and is simple to update in one place.

    
    
    @angle: 170;
     
    .callout {
      &.qty-left {
        .callout-generator(@color-deals, @color-white, @angle);
      }
      &.qty-sold {
        .callout-generator(@color-white, @color-deals, @angle, 2px solid @color-deals);
      }
      &.qty-out {
        .callout-generator(@color-grey, darken(@color-grey, 10%), @angle);
      }
    }
    

To make the callouts scalable, we'll create a LESS mixin named `.callout-generator` that accepts values for such things as the background color, text color, angle of the point and border.

![.callout-generator accepts values like background color, text color, angle of the point, and border.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-7-scalable-callouts-800w-opt.png)25  
The result is scalable CSS capable of generating any number of new callouts. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-7-scalable-callouts-large-opt.png)26)

    
    
    .review-flag {
        .callout-generator(@color-brand, @color-white, 75);
    }
    

In the future, when a new requirement calls for a similar design pattern, generating a new style will be easy.

![.callout-generator accepts values like background color, text color, angle of the point and border.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-8-verified-purchase-opt.png)27  
([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-8-verified-purchase-opt.png)28)

To create a scalable design system, learn to anticipate the changes that are common in projects, and apply that understanding to make sure the code you write is ready for those changes. Common solutions include using variables and mixins, as well as storing values in arrays and looping through them. Ask yourself:

  * What parts of these elements are likely to change?
  * How can you write the code so that it's easy to make those changes in the future?

### 8\. Documented Link

**All elements are described for others to use and extend.**

Documenting design is undervalued and is often the first corner to be cut in a project. But creating a record of your work is more than about just helping the next person figure out what you intended — it's actually a great way to get all of your stakeholders onboard with the entire design system, so that you're not reinventing the wheel everytime. Your documentation should be a reference for everyone on the team, from developers to executives.

The best way to document your work is to create a live style guide, one that is generated directly from the comments in your code. We use an approach called [style-guide-driven developmentDocumentCSS](https://www.smashingmagazine.com/2016/06/designing-modular-ui-systems-via-style-guide-driven-development/)29, which pays for itself in dividends. But even if your project can't have a live style guide, creating one manually in HTML or even a print-formatted PDF is fine. The principle to remember is that **everything we do must be documented**.

To document your design system, write instructions to help someone else understand how the design has been implemented and what they need to do to recreate it themselves. This information might include the specific design thinking behind an element, code samples or a demo of the element in action.

  * How would I tell someone else how to use my code?
  * If I were onboarding a new team member, what would I explain to make sure they know how to use it?
  * What variations of each widget can I show to demonstrate all the ways in which it can be used?

![A style guide is great, but a live style guide generated directly from the CSS is life-changing.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-9-style-guide-800w-opt.png)30  
A style guide is great, but a live style guide generated directly from the CSS is life-changing. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-9-style-guide-large-opt.png)31)

### 9\. Accurate Link

**The final output is an appropriate representation of the intended design.**

Finally, we can't forget that what we create has to look just as great as the original design concept it's intended to reflect. No one is going to appreciate a design system if it doesn't meet their expectations for visual appeal. It's important to emphasize that the result can only be an **appropriate representation** of the design and will not be pixel-perfect. I'm not fond of the phrase "pixel-perfect" because to suggest that an implementation has to be exactly like the mockup, pixel for pixel, is to forget any constraints and to devalue standardization (never mind that every browser renders CSS a little differently). Complicating accuracy is the fact that static designs for responsive applications rarely account for every possible device size. The point is that a certain degree of flexibility is required.

You'll have to decide how much of an appropriate representation is needed for your project, but make sure that it meets the expectations of the people you're working with. In our projects, I'll review major deviations from pixel-perfection with the client, just to be sure we're on the same page. "The designs show a default blue button style with a border, but our standard button color is slightly different and has no border, so we opted for that instead." Setting expectations is the most important step here.

![The implmentation varies from the original design, but it's still accurate.](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-10-accurate-800w-opt.png)32  
In production with real data and standardized CSS, the final implementation looks slightly different from the original mockup. Plus, some of the requirements changed during implementation. The result, though, is accurate. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-10-accurate-large-opt.png)33)

### A System Of Thinking Link

The goal of these nine principles is to provide a guide for implementing design in HTML and CSS. It is not a set of rules or prescriptive advice as much as it is a way of thinking about your work so that you can optimize for the best balance between great design and great code. It's important to give yourself a certain amount of flexibility in applying these principles. You won't be able to achieve perfection with each one every time. They are ideals. There are always other distractions, principles, and priorities that prevent us from doing our best work. Still, the principles should be something to always strive for, to constantly be checking yourself against, and to aggressively pursue as you take your design from the drawing board to the final medium in which it will be experienced. I hope they will help you to create better products and build design systems that will last for many years.

I'd love to hear from you about your experience in implementing design. Post a comment and share any advice or other principles you might be using in your own work.

_(rb, vf, al, il)_

#### Footnotes Link

  1. 1 https://www.smashingmagazine.com/2016/06/designing-modular-ui-systems-via-style-guide-driven-development/
  2. 2 https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/
  3. 3 http://emphaticsolutions.com/2011/03/19/object-oriented-css-for-programmers.html
  4. 4 https://www.smashingmagazine.com/2015/02/design-principles-dominance-focal-points-hierarchy/
  5. 5 https://www.nngroup.com/articles/ten-usability-heuristics/
  6. 6 https://www.smashingmagazine.com/2015/12/reimagining-single-page-applications-progressive-enhancement/
  7. 7 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-1-daily-deals-opt.png
  8. 8 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-1-daily-deals-opt.png
  9. 9 https://www.smashingmagazine.com/2016/05/developing-dependency-awareness/
  10. 10 https://www.w3schools.com/html/html5_semantic_elements.asp
  11. 11 https://www.w3.org/standards/
  12. 12 http://learn.shayhowe.com/html-css/writing-your-best-code/
  13. 13 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-2-efficient-large-opt.png
  14. 14 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-2-efficient-large-opt.png
  15. 15 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-3-efficient-large-opt.png
  16. 16 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-3-efficient-large-opt.png
  17. 17 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-4-abstracted-large-opt.png
  18. 18 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-4-abstracted-large-opt.png
  19. 19 https://www.smashingmagazine.com/2016/12/styling-web-components-using-a-shared-style-sheet/
  20. 20 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-5-modular-large-opt.png
  21. 21 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-5-modular-large-opt.png
  22. 22 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-6-configurable-opt.png
  23. 23 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-6-configurable-opt.png
  24. 24 https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/
  25. 25 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-7-scalable-callouts-large-opt.png
  26. 26 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-7-scalable-callouts-large-opt.png
  27. 27 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-8-verified-purchase-opt.png
  28. 28 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-8-verified-purchase-opt.png
  29. 29 https://www.smashingmagazine.com/2016/06/designing-modular-ui-systems-via-style-guide-driven-development/
  30. 30 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-9-style-guide-large-opt.png
  31. 31 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-9-style-guide-large-opt.png
  32. 32 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-10-accurate-large-opt.png
  33. 33 https://www.smashingmagazine.com/wp-content/uploads/2017/07/design-implementation-10-accurate-large-opt.png
