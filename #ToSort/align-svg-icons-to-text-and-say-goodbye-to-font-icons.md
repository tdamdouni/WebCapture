# Align SVG Icons to Text and Say Goodbye to Font Icons

_Captured: 2017-01-27 at 14:23 from [blog.prototypr.io](https://blog.prototypr.io/align-svg-icons-to-text-and-say-goodbye-to-font-icons-d44b3d7b26b4#.6z9g8jbuz)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*YJKqXVh1XZcKB9QeyVcKkA.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*YJKqXVh1XZcKB9QeyVcKkA.png)

The push for SVG icons over font icons has caught serious momentum in the web community. With an SVG icon system you can better meet accessibility standards, render higher quality visuals, and add/remove/modify icons in the library with ease. At [Pivotal](https://pivotal.io/) we've created an SVG icon system with React for use on our suite of products. This article is about my approach to styling the SVG icon system with CSS to make it easy and effective to use.

### Why should I care about how SVGs are styled?

If you've ever used font icon systems like [Font Awesome](http://fontawesome.io/) you know how easy it is to add to a project and get going. The icons align to your text easily and can be modified by changing the font-size of the element. There is no clearly defined way for styling an SVG icon system. I've seen some systems custom style and place each icon in their library. This route sounds painfully unsustainable if you utilize more than 15 icons in your UI.

### **Can it scale like an icon font?**

To emulate the font-size scaling I use a class to set the SVG size to 1em by 1em. This means that if your title text is a 48px font size the SVG will be 48px by 48px. This works nicely for components like buttons and inputs when you want to add an icon. This also empowers you to pass a font size to the element via modifier class or inlined CSS. Using font-size to determine the size of your icon makes your life a little easier.
    
    
    .svg-icon svg {  
      height: 1em;  
      width: 1em;  
    }

### **My SVG won't align to with my text. How do I fix this?**

The downside is that a DOM element on it's own doesn't align nicely with text. To counter this I wrote the .svg-icon handler class to hold the size and be relative positioned so that I can absolute position the SVG inside of it. Moving the icon down by "-0.125em" allows me to pull down the icon by 12.5% at any scale.

The first example shows that DOM elements align to the baseline of text by default. However, since our icon is already properly scaled to consider the baseline, we need to pull it down for the baseline to truly align. At this size the distance is 6px away, 6px/48px = ⅛ or 12.5%. In the second example, pulling the icon down by -0.125em places the icon onto the proper baseline of the text.
    
    
    .svg-icon {  
      display: inline-flex;  
      align-self: center;  
      position: relative;  
      height: 1em;  
      width: 1em;  
    }
    
    
    .svg-icon svg {  
      height:1em;  
      width:1em;  
    }
    
    
    .svg-icon.svg-baseline svg {  
      bottom: -0.125em;  
      position: absolute;  
    }

### Will this work with my typeface and icon system?

Maybe. Every typeface is built differently. In the example below you can see that despite being the same font-size the letter height and width are unique to each family. However, the browser's measurement of the line-height container will not change. You may have to customize the CSS above to position your existing icon set.

![](https://cdn-images-1.medium.com/max/800/1*GSfAY-rib0QAngPUK9LHMA.png)

### How do I create new icons?

Start with a template sized to match a sample of your preferred typeface. In the example below I'm using a 96px font-size with with a matching line-height. Drawing redlines to describe the boundaries of the line-height and the baseline of the text I'm able to figure out how to size my largest icons. In this example I'm comparing [Google's Material Icons](https://material.io/icons/). I've referenced their [icon design template](https://material.io/guidelines/style/icons.html#icons-system-icons) to better understand how to build my own icons.
