# New side project: highlights minisite, and checking for interaction feature support

_Captured: 2017-04-21 at 19:21 from [melanie-richards.com](https://melanie-richards.com/blog/highlights-minisite/)_

![Screenshot of the highlights minisite](https://melanie-richards.com/assets/images/content/highlights-s.png)

I read quite a bit, and wanted somewhere to keep highlights from books and articles. That "somewhere" is [highlights.melanie-richards.com](http://highlights.melanie-richards.com/), a simple Jekyll site [hosted on Github Pages](https://github.com/melanierichards/highlights). I'm not doing anything fancy to get the highlights into the project (for various reasons I won't bore you with), just using some YAML data files.

I did, however, come across a couple neat little use cases for interaction feature queries.

## Handling a hover-dependent interaction

![Screenshot of the fade effect](https://melanie-richards.com/assets/images/content/highlights-hover.gif)

On the index of the highlights site, there's an interaction where the base imagery of each book/collection cover is this rough cut-paper style digital illustration, and when you hover over the image it fades to a high-fidelity version of the cover. It's a fun reveal, but not very useful when you don't have hover capabilities on your current device. Enter [level 4 media queries](https://drafts.csswg.org/mediaqueries-4).

Among the media query types introduced in this level of the specification is the ability to detect whether or not [the hover feature](https://drafts.csswg.org/mediaqueries-4/#hover) is available to the user. Two things to note here: 1) a mouse is not the only device input that can "hover" (some game console controllers have this capability, for example) and 2) this media query looks at the device's "primary" inputs, so there's some cases where hover is technically available, but this query would be falsey.

On my site, I have the rough illustration in an SVG sitting in a link with the background image set to the high-fidelity cover. This SVG by default has an opacity of `0`. If hover is available, the SVG has full opacity, and is animated to `0` opacity on hover. The entire link has an opacity transition of `.75` => `1`, so that even if the hover feature query is false or unsupported, there's still visual feedback on the element. Here's what that looks like:
    
    
    /* Using tag in the selector because .source__image is not a link on individual book pages and should not get these styles */
    
    a.source__image {
      opacity: .75;
      transition: opacity 400ms;
    }
    
    a.source__image:hover {
      opacity: 1;
    }
    
    a.source__image svg {
      opacity: 0;
    }
    
    @media (hover) {
      a.source__image svg {
        opacity: 1;
        transition: opacity 400ms;
      }
    
    
      a.source__image:hover svg {
        opacity: 0;
      }
    }
    

You can also check for the inverse, i.e. `@media (hover: none)`, but I think this direction usually yields a better experience.

At time of writing, interaction media queries are supported in Microsoft Edge, Chrome, Safari, Opera, and Android browser ([Can I Use link for posterity](http://caniuse.com/#feat=css-media-interaction)). I hope that Firefox supports them soon so that this feature can light up over there too!

## Adding a non-intrusive fade

![Screenshot of the fade effect](https://melanie-richards.com/assets/images/content/highlights-fade.jpg)

At the bottom of the highlights minisite, I have a fade effect. This is simply an `::after` pseudo element with a gradient background applied, like so:
    
    
    .page-wrap::after {
      display: block;
      content: '';
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 10em;
      background: linear-gradient(rgba(0,0,0,0), rgba(0,0,0,1));
    }
    

But wait! Any content that falls underneath this shadow will not be selectable or otherwise available for interaction. Here is where we use `pointer-events`. What this property does is tells the browser when a particular element should be available for interaction; [read more on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events). For this little fade here, we don't want any user interaction, and we don't want to block interactivity of elements falling beneath the fade pseudo element.

So let's remove all pointer events from the pseudo element:
    
    
    **@supports(pointer-events: none) {**
      .page-wrap::after {
        display: block;
        content: '';
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 10em;
        background: linear-gradient(rgba(0,0,0,0), rgba(0,0,0,1));
        **pointer-events: none;**
      }
    }
    

In addition to the `pointer-events` property, I'm also wrapping this entire declaration block within an `@supports` rule, so that the fade pseudo element is only rendered on browsers that support both `@supports` and `pointer-events`. This way, more modern browsers have an enhanced design, and users in other browsers don't get a broken experience. [pointer-events CSS](http://caniuse.com/#feat=pointer-events) has better support than `[@supports`](http://caniuse.com/#search=%40supports), but again, this is an enhancement.

That's about it for this post, but feel free to [poke around in the code](https://github.com/melanierichards/highlights/) or [visit the minisite](http://highlights.melanie-richards.com/)!
