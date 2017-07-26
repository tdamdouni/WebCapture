# 21 CSS techniques I used for my new about me page

_Captured: 2015-12-11 at 13:41 from [medium.com](https://medium.com/@ellekasai/21-css-techniques-i-used-for-my-new-about-me-page-22afdf3f019a#.htldxlbly)_

Recently, I designed my "about me" page without using any CSS frameworks. Here are some of the CSS techniques I used, along with the resources to learn more about them.

![](https://cdn-images-1.medium.com/max/800/0*AeWSdKrmRsEgwWnl.)

### 1\. Use SCSS mixins and breakpoint variables to set media queries

It's faster to type.

![](https://cdn-images-1.medium.com/max/800/0*0LDivxqc0oxM4rXE.)

### **2\. Style mobile first**

First write mobile style, then write style for larger screens using media query mixins.

![](https://cdn-images-1.medium.com/max/800/0*fZXS8g0vGZEAk5dZ.)

### **3\. Use em for media queries**

By doing this, media queries work better with page zooming.

![](https://cdn-images-1.medium.com/max/800/0*uqbXh1OVfHiVnZPs.)

Code: <http://bit.ly/17elFMC>  
Learn more: [7 Habits of Highly Effective Media Queries](http://bradfrost.com/blog/post/7-habits-of-highly-effective-media-queries/#relative)

### **4\. Use px for html tag and use rem for other font sizes**

It becomes easier to change font size on different screen size.

![](https://cdn-images-1.medium.com/max/800/0*-T9Fd6La0tYazubV.)

![](https://cdn-images-1.medium.com/max/800/0*29Ap2yftZ3rsAEFd.)

Code: <http://bit.ly/1yS4iYh>  
Learn more: [Font Size Idea: px at the Root, rem for Components, em for Text Elements](http://css-tricks.com/rems-ems/)

### **5\. Use unitless line-height**

By doing this, line height changes when font size changes. Also, use smaller line-height for headings so they look better.

### **6\. Use border-box for everything**

It's easier to calculate box sizes.

![](https://cdn-images-1.medium.com/max/800/0*GSROGjn7BQv83G5z.)

Code: <http://bit.ly/1EKCw4s>  
Learn More: [* { Box-sizing: Border-box } FTW](http://www.paulirish.com/2012/box-sizing-border-box-ftw/)

### **7\. Use single directional margins**

It's easier to reason about the vertical rhythm.

![](https://cdn-images-1.medium.com/max/800/0*GJVc1JlC_BSnRy5c.)

### **8\. Use BEM for naming classes**

It's easier to think in terms of components.

![](https://cdn-images-1.medium.com/max/800/0*Lm8AnCvzfp7xvHa-.)

Code: <http://bit.ly/1EKCPMz>  
Learn More: [MindBEMding -- getting your head 'round BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

### **9\. Use the component's name for its file's name**

It's easier to find the corresponding files.

![](https://cdn-images-1.medium.com/max/800/0*L3pW3T9uzK9UyIdT.)

### **10\. Use "is-*" classes for state**

It's easier to know which classes are set from JS.

![](https://cdn-images-1.medium.com/max/800/0*Cb9OJH65w5229cIQ.)

Code: <http://bit.ly/1EKD5eq>  
Learn More: [Mobify CSS Style Guide -- State](https://github.com/mobify/mobify-code-style/tree/master/css/class-naming-conventions#state)

### **11\. Use utility classes if they make the code simpler**

![](https://cdn-images-1.medium.com/max/800/0*LN68zyrCxBypvd1f.)

Code: <http://bit.ly/1E2BUJv>

### **12\. Avoid tag selectors when possible**

By doing this, the code becomes more portable. In this case, I didn't write "ul.social-links".

### **13\. Avoid selectors that depend on location**

The code becomes more predictable and reusable. In this case, I didn't write ".footer .social-links".

### **14\. Use placeholder selectors to DRY the code**

…when it doesn't make sense to break down to more components/classes.

![](https://cdn-images-1.medium.com/max/800/0*857fxIitYEbQFoUV.)

Code: <http://bit.ly/1E2C6IE>  
Learn More: [Mobify CSS Style Guide -- @extends](https://github.com/mobify/mobify-code-style/tree/master/css/sass-best-practices#workaround)

### **15\. Use section -> container -> inner pattern**

  * Section (or header/footer) sets the background and margin bottom
  * Container sets the common width and centers the content
  * Inner positions the text
  * Use more classes/components if necessary
![](https://cdn-images-1.medium.com/max/800/0*70doChtnLcYo-xun.)

![](https://cdn-images-1.medium.com/max/800/0*iZ51N3dNNOk66bqM.)

![](https://cdn-images-1.medium.com/max/800/0*wa22YTQsHHIbe8k0.)

### **16\. Use percent-based vertical padding to position text over an image**

Because I use background-size: cover, the image scales with the page width. Percent based vertical padding scales with the width, so it scales with the image too.

![](https://cdn-images-1.medium.com/max/800/0*ytd3K8g4HyXalaae.)

### **17\. Use comments when the code is not clear**

![](https://cdn-images-1.medium.com/max/800/0*ELY3DQYwy8bSCxAe.)

### **18\. Use negative left margin for grid rows (same size as column gutters)**

Bootstrap uses the same technique.

![](https://cdn-images-1.medium.com/max/800/0*KedXLSMPwYzZDWWX.)

Code: <http://bit.ly/1EKDZri>  
Learn more: [Why does the bootstrap .row has a default margin-left of -30px?](http://stackoverflow.com/questions/16699672/why-does-the-bootstrap-row-has-a-default-margin-left-of-30px)

### **19\. Use nth-child for responsive column resets**

![](https://cdn-images-1.medium.com/max/800/0*jwABGAtJ8b7a2zat.)

![](https://cdn-images-1.medium.com/max/800/0*G2sTcAul7G2K4JHu.)

### **20\. Columns only take care of horizontal positioning. For vertical positioning, add a different class.**

It keeps the grid system simple.

![](https://cdn-images-1.medium.com/max/800/0*kPd6koN_Ap3m39b6.)

### **21\. Use simple CSS animations**

### That's all!

Thanks to [Shu Uesugi](https://twitter.com/chibicode) for revising my English.

Source Code [HTML](https://github.com/ellekasai/ellekasai.com/blob/gh-pages/index.html) / [CSS](https://github.com/ellekasai/ellekasai.com/tree/gh-pages/_sass/about)
