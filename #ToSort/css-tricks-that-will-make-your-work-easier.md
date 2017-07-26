# CSS Tricks That Will Make Your Work Easier

_Captured: 2017-03-30 at 20:18 from [dzone.com](https://dzone.com/articles/css-tricks-that-will-make-your-work-easier?edition=287891&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-30)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

The Cascadian Style Sheets (CSS) offer such a wide variety of creative options that no one can master them all. Luckily, there are several tweaks that may seem simple or insignificant, but they are actually that set of details that contribute to a sleek and witty design. So, let's see the best CSS tips and tricks out there that will make your programmer work easier.

## Start With a Master Style Sheet

We all know the drill when beginning a new stylesheet. Open the new page with the <Head> </Head> sandwich where you add the CSS text style and spice it all up with style sheet information that should be enfolded in <!-- and --> to make them invisible.

However, by diving directly in the middle of your commands, you will overlook the connection between your style sheet and web browser. Many programmers face inconsistencies in their web design which doesn't make sense. The secret here is that usually web browsers have some format of their own which jams your commands.

To avoid that, start with a Master Style Sheet which will reset these standard formats. You should just insert the following script at the top of your sheet to override the original theme with your own.

## Replace the Normal With Smart Quotes

Typography is an important factor of any website, and everybody should use it correctly. For instance, did you know that simply using the quotation marks from your keyboard are actually used for coordinates or measurements? If you simply insert them into your text to signal a quote, the inverted commas will land an unusual look, which will be disturbing for the professional eye.

This is why the "q" tag is highly recommended to mark down your quotes, which simply go by the name of smart quotes. This is because they automatically adjust to the proper quotation marks before and after your text.

However, the story doesn't end here. There are some variations of quotation marks that depend on culture to culture. For example, the Germans are a bit peculiar when it comes to these signs, so they actually invert them, and they somehow ended up looking like this „ Ich glaub, mein Schwein pfeift. " To make sure that you respect all of these variations, you can simply insert the attribute of language inside your code.

## Parallax Scrolling Effect

One of the most beloved designs of this year is the Parallax website theme. It is everything that the web trends dream about such as sleek design, compact and modern features, a simplicity which becomes the ultimate sophistication. _The Parallax effect can be equally with the smooth touch of a silk material._

Many rely on a JavaScript library to achieve this kind of design, but we recommend you take control over the situation and insert your own code lines in CSS. This way, there will be no room left for inconsistencies with your design which can create a sluggish parallax scroll effect.
    
    
        box-shadow: 0 -1px 10px rgba(0, 0, 0, .7);
    
    
        transform: translateZ(.25px) scale(.75) translateX(-94%) translateY(-100%) rotate(2deg);
    
    
        box-shadow: 0 0 8px rgba(0, 0, 0, .7);
    
    
        transform: translateZ(.4px) scale(.6) translateX(-104%) translateY(-40%) rotate(-5deg);
    
    
        box-shadow: 0 0 8px rgba(0, 0, 0, .7);
    
    
    .slide:nth-child(2n+1) .title {
    
    
        transform: translateZ(-1px) scale(2);
    
    
        background-image: url("http://lorempixel.com/640/480/abstract/5/");
    
    
        transform: translateZ(-1px) scale(2);

## CSS Multiple Backgrounds

With CSS3, you can take the powerful impacts that several backgrounds have on our impression and combine them into one. You can achieve this by using the shorthand property and its individual properties except the background-color. The first background will be the first picture you insert in the code and it will be followed by the visuals that are next in line.
    
    
        background-image: url(http://image.flaticon.com/icons/svg/214/214280.svg), url(https://pixabay.com/static/uploads/photo/2015/12/10/16/04/mountain-1086641_960_720.jpg), linear-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0));
    
    
        background-repeat: no-repeat, no-repeat, no-repeat;
    
    
        background: -moz-linear-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0)), -webkit-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0)), -ms-linear-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0)), linear-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0));

## Backgrounds That Blink

It wouldn't have been a proper list with [CSS tips and tricks](https://itinterviewguide.com/css-sprites/) without the presence of an animation. There are thousands of ways to create beautiful clips in CSS, but this is a simple and attention grabbing one. You know that simple image with a mesmerizing, harmonious change of colors that you can spend hours looking at? Well, the following are all the code lines to obtain this effect.

## Show Off File Formats

This one is to offer the website visitors more information about your content. There is nothing more annoying than downloading files that you don't want just because they are in the wrong format. So, to ensure that the users will come to your web page again, you can simply make the icon of the file format pop up next to the download hyperlink. So, let's begin!

## Conclusion

So, these are some of the CSS tips and tricks that will come in handy for your future projects. Even though there are many shortcuts throughout the web as in prewritten JavaScript libraries, it is best to take the hard road and use CSS code lines. This way you make sure that everything works smoothly and there are no inconsistencies in your work.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
