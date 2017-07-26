# A Brief Overview On Responsive Navigation Patterns

_Captured: 2017-04-20 at 11:05 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)_

  * [0 Comments](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

Today, too many websites are still inaccessible. In our new book _Inclusive Design Patterns_, we explore how to craft **flexible front-end design patterns** and make **future-proof and accessible interfaces without extra effort**. Hardcover, 312 pages. [Get the book now!](https://shop.smashingmagazine.com/products/inclusive-design-patterns?utm_source=magazine&utm_campaign=inclusive-design-patterns&utm_medium=html-ad-content-1)

To say that **responsive web design has changed our industry** would be an understatement at best. We used to ask our clients which resolutions and devices they wanted us to support, but we now know the answer is "as many as possible." To answer a challenge like this and to handle our increasingly complex world, our industry has exploded with new thinking, patterns and approaches.

In this article, I want to look specifically at the issue of responsive navigation. We will first talk about information architecture, then the purpose of navigation, and finally we will look at three responsive navigation patterns that have served well over time.

The first things that are affected in a mobile-first world, or at least should be, are content and information architecture strategies. If our applications are primarily about facilitating tasks and sharing of information, then we must focus there first.

The industry went through a trend of megamenus and increasingly complex navigation structures, but responsive web design has forced us to rethink this complexity. How much does our navigation need to hold in order to be effective? Does an application really need several different types of navigation, or can it work fine with just one? You will find that most responsive navigation patterns have forced us to simplify and concentrate, and that is a benefit of a [mobile-first approach](http://www.lukew.com/ff/entry.asp?933).

![An image of the responsive navigation used on Intel's website.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/intel-preview-opt.png)[6](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _Intel's navigation is complex, and that complexity is exacerbated on small viewports. Notice that the navigation has tabs, a listing of links and subcategories in a small space. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/03/intel-large-opt.png)[7](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/))  
_

The truth is that if your information architecture isn't optimized, then it doesn't matter how slick your responsive navigation solution is. This was true long before we were debating the merits of media queries, but now the challenge is even greater. We must ensure that our navigation structures, when they are revealed on our websites, are clear and minimize any [cognitive friction](https://www.interaction-design.org/literature/article/my-head-hurts-cognitive-friction-in-the-age-of-mobile).

Here are a couple of questions to ask as you create your navigation:

  * Is it painfully clear what each of your labels means, and is the value proposition (sometimes called "[information scent](https://www.nngroup.com/articles/information-scent/)") clear to your visitors?
  * How can you reduce the complexity in your navigation as much as possible? If your navigation structure is seven levels deep, not many are going to be up for that challenge.
  * How can you ensure that the navigation doesn't get lost throughout your resolution adaptations?
  * Have you tested it thoroughly to ensure that the navigation aligns with the user's goals in visiting the website?

Let's take a quick moment to reflect on the purpose of navigation. This might seem elementary, but I've seen too many applications whose designers have forgotten these important principles. The best article I've read on this comes from one [written over a decade ago by Derek Powazek](http://alistapart.com/article/whereami) (which shows that the heart of the matter remains the same). He writes:

> Navigation also has three parts, which are used to communicate to the user about their past, present, and future. Any good global navigation scheme should, at a glance, answer the top three questions every user has at the back of their mind on any page:
> 
>   * Where am I? (Present)
>   * Where can I go? (Future)
>   * Where have I been? (Past)

We must revisit these principles because I see that most responsive navigation solutions handle these very inconsistently. Most solutions handle the question "Where can I go?" pretty well, but most websites don't even bother to show in their responsive solutions where the user is currently or where they've been. As you adapt some of the patterns we'll look at, be sure to mold them to satisfy these important criteria.

![An image of the responsive navigation used on NCSBN website.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/ncsbn-preview-opt.png)[11](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _NCSBN's website is one of the few that marks in its responsive navigation where you are in the website's structure. (View large version)_

Stephanie Lin has just posted an article entitled "[The Rules for Modern Navigation](http://www.uxbooth.com/articles/the-rules-for-modern-navigation/)," which makes a good complement to this article. She covers important interaction design components to consider in your navigation.

Remember that we have a lot of options today for responsive navigation, but here is my take on the best patterns. Brad Frost has done us all a service and cataloged most, if not all, of these patterns on his website [This Is Responsive](https://bradfrost.github.io/this-is-responsive/patterns.html#navigation). He has also written two posts about these patterns: "[Navigation Patterns](http://bradfrost.com/blog/web/responsive-nav-patterns/)" and "[Complex Navigation Patterns for Responsive Design](http://bradfrost.com/blog/web/complex-navigation-patterns-for-responsive-design/)."

This pattern is well illustrated on the [UX London 2017's website](http://2017.uxlondon.com/). Here is what it looks in small viewports.

![An image of the responsive navigation used on UX Longdon 2017.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/UX_London_2017-opt.png)[18](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _UX London 2017 uses a pattern that maximizes its navigation's visibility and utility._

I love this pattern because it fundamentally makes navigation a priority, and it doesn't hide the navigation behind any [progressive disclosure](http://vanseodesign.com/web-design/progressive-discolosure/). Most responsive navigation patterns involve progressive disclosure, and while disclosure is a good option, it should only be pursued when a better option doesn't exist. I agree with [Nielsen Norman Group on this issue](https://www.nngroup.com/articles/killing-global-navigation-one-trend-avoid/): If you can show navigation, show it. No one visiting this website has to wonder where the navigation is. A bonus is that this has no client-side dependencies, so you can keep your dependencies low and reduce failure points.

However, this is a hard sell for a lot of responsive applications. First of all, it doesn't handle complex navigation well. If you need more than one level in your application shown at one time, then this pattern is not for you. Also, it could take up a lot of important vertical space in the application, so be sure that you can implement it like the UX London site and keep the allotted space in check.

Most applications can get away with two levels of navigation, and I have found this is the sweet spot for many of my implementations. In small viewports, this pattern enables users to toggle the subsections easily and see the contents within. One modern example of this is the [White House's website](http://whitehouse.gov).

![An image of the responsive navigation solution used for WhiteHouse.gov.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/whitehouse-preview-opt.png)[22](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _The White House's website provides toggles to show subcontent._

It may not be the flashiest solution, but I have found it to be very stable. This pattern works well for the majority of navigation I need to support, and it effectively handles simple two-level navigation structures (which I'm hesitant to go beyond in most circumstances). Also, we must always build these solutions [progressively](http://alistapart.com/article/understandingprogressiveenhancement), so that they work even when the code supporting them fails.

I used to use [FlexNav](http://jasonweaver.name/lab/flexiblenavigation/) to achieve this effect, but the project has been abandoned by its owner. A promising alternative is [SmartMenus](https://www.smartmenus.org), but I have not used it yet. If you are interested in a pure CSS version of this, check out [CSS Script's code example](http://www.cssscript.com/multi-level-toggle-responsive-navigation-menu-using-pure-css/).

This is another good option and is really a variant of the previous pattern. In this case, we have no need for multiple levels, but the navigation items are still too numerous to allow for the "do very little" pattern. An example of this is found on [Starbucks](http://www.starbucks.com/)' website.

![An image of the responsive navigation solution used for Starbucks.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/starbucks-preview-opt.png)[28](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _Starbucks provides a simple toggle. (View large version)_

With some clear iconography and colors, this option can really work well because it is very simple to implement and use. Variations of this pattern push content down or overlap it, and I feel both are acceptable. If you want a good script for this, check out [Responsive Nav](http://responsive-nav.com/).

Remember that you do not necessarily have to support multiple levels in your responsive solution. For example, the [World Wildlife Fund](http://www.worldwildlife.org/)'s navigation at higher viewport resolutions has a dropdown, but at the lowest viewport it simply toggles and the top-level links go to landing pages, where the remaining navigation items are shown. You could also provide alternate ways to navigate, including breadcrumbs, which can be a helpful addition at any viewport size.

![An image of the responsive navigation solution used for World Wildlife Fund.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/wwf-preview-opt.png)[32](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _World Wildlife Fund presents top-level links and shows subitems on the landing pages. (View large version)_

As mentioned, there are many approaches you could choose from today to handle your project's needs. Even though I like the three above the best, here are two other possibilities.

This is probably the most popular, but some implementations are better than others. It can be done well, and if you want a script, I have used [MMenu](http://mmenu.frebsite.nl/) with great results.

![Zurb's Foundation has popularized the off-canvas pattern.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/zurb-preview-opt.png)[35](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _Responsive frameworks like Zurb's Foundation have popularized the off-canvas pattern. (View large version)_

This has picked up steam in the last year or so, and it can also be good in some situations. I have used it on websites that have really long horizontal navigation, to avoid having to hide the menu items too early as the viewport shrinks. The only big problem with this solution is that it forces you to make assumptions about what is most important, so be careful. I have used the [PriorityNav.js](http://gijsroge.github.io/priority-nav.js/) script for this, and it has worked well.

![Wonderful Machine uses the Priority Plus pattern to good effect.](https://www.smashingmagazine.com/wp-content/uploads/2017/03/wonderfulmachine-preview-opt.png)[38](https://www.smashingmagazine.com/2017/04/overview-responsive-navigation-patterns/)

> _Wonderful Machine uses the Priority Plus pattern to good effect. (_

There is simply no way I can talk about responsive navigation and not mention the debate around the hamburger icon (there are also other variants of [responsive "mystery meat" navigation indicators](https://twitter.com/lukew/status/591296890030915585)). The real issue here is: Does the icon convey enough meaning on its own, or does it need a textual indicator? The debate is essentially about the universality and recognizability of the hamburger icon. For me, very few icons have a universally clear meaning without some kind of text to support them, and the hamburger icon is just another example of why it's best not to rely on the icon alone. Ask yourself, Is it worth confusing a visitor by not including it, or should I just include it to increase the likelihood that it will be understood? I lean towards including a textual indicator. Remember to always evaluate the context of your application to answer questions like these.

Here are some articles that talk about the issue if you want to learn more:

The great news is that there are more options than ever for handling navigation in your responsive application. As long as you stick to clear information architecture design, testing and proven patterns, you will ensure that visitors will be able to use your website easily now and into the future. The next step is to start experimenting with these and other patterns to see what works best for your particular application. Behavior and needs change over time, so continually re-evaluate how you use these approaches. Another article on Smashing Magazine, "[Responsive Navigation on Complex Websites](https://www.smashingmagazine.com/2013/09/responsive-navigation-on-complex-websites/)," provides case studies and code for you to go further.

_My thanks to [Ben Callahan](https://twitter.com/bencallahan) and [Jacqui Olkin](https://twitter.com/OlkinComm) for their feedback on drafts of this article._

_(da, vf, yk, al, il)_
