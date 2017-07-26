# OS Specific Fonts in CSS

_Captured: 2015-12-13 at 13:43 from [css-tricks.com](https://css-tricks.com/os-specific-fonts-css/)_

I'm not sure what the exact use case was, but Sam Stephenson recently asked me:

> [@chriscoyier](https://twitter.com/chriscoyier) What's the best way to reference the OS X system font in CSS (to get Lucida Grande or Helvetica, as appropriate)?
> 
> -- Sam Stephenson (@sstephenson) [November 20, 2014](https://twitter.com/sstephenson/status/535502527995727872)

My immediate thought was to use the old trick where you put the User Agent in a data-attribute on the root element that you can select off of.
    
    
    var doc = document.documentElement;
    doc.setAttribute('data-useragent', navigator.userAgent);

Then set the fonts as needed. In this case, setting Lucida Grande for OS X but Helvetica Neue for the latest version.
    
    
    html {
      font-family: sans-serif;  
    }
    
    html[data-useragent*='Mac OS X'] {
      font-family: "Lucida Grande","Lucida Sans Unicode", Tahoma, sans-serif;
    }
    
    html[data-useragent*='Mac OS X 10_10'] {
      font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif; 
      font-weight: 300;
    }

Which [basically works](http://codepen.io/chriscoyier/pen/LEEdzb). It's UA-sniffing which is [bad](http://css-tricks.com/browser-detection-is-bad/), but we aren't doing anything particularly mission critical here such that we would put our site or the web at risk.

Sam tried another path and [got pretty fancy](http://codepen.io/sstephenson/pen/bNNvMm). Here, he creates an `iframe` (so there is no interfering styles), inserts a `button` element (which should have the system font on it by default), and tests the styles on it.
    
    
    (function() {
      window.addEventListener("DOMContentLoaded", function() {
        getSystemFontFamily(function(systemFontFamily) {
          var cssText = ".system-font { font-family: " + systemFontFamily + " }";
          var element = createStyleElement(cssText);
          document.head.insertBefore(element, document.head.firstChild);
        });
      });
    
      function getSystemFontFamily(callback) {
        withHiddenFrame(function(document) {
          var button = document.createElement("button");
          document.body.appendChild(button);
          callback(window.getComputedStyle(button).fontFamily);
        });
      }
    
      function withHiddenFrame(callback) {
        var frame = document.createElement("iframe");
        frame.style.cssText = "width: 0; height: 0; visibility: hidden";
        frame.onload = function() {
          callback(frame.contentDocument);
          document.body.removeChild(frame);
        }
        document.body.appendChild(frame);
      }
    
      function createStyleElement(cssText) {
        var element = document.createElement("style");
        element.type = "text/css";
        if (element.styleSheet) {
          element.styleSheet.cssText = cssText;
        } else {
          element.appendChild(document.createTextNode(cssText));
        }
        return element;
      }
    })();

On Yosemite (10.10.1) you'll get:
    
    
    .system-font { 
      font-family: '.HelveticaNeueDeskInterface-Regular';
    }

Weird name, but it works.

In 10.9 you get:
    
    
    .system-font { 
      font-family: '.LucidaGrandeUI';
    }

Again, weird name, but works.

Tab Atkins [suggested](https://twitter.com/tabatkins/status/535506051987038208) that CSS should be able to do this with essentially `font-family: sans-serif;`, but it just doesn't work that way unfortunately. You'd get Helvetica in 10.9, not Lucida Grande.

Tab [also suggested](https://twitter.com/tabatkins/status/535508233792659456) trying @font-face. By setting multiple `local()` values for the `src` property, [it works](http://codepen.io/chriscoyier/pen/raxwQP)!
    
    
    @font-face {
      font-family: "MacSystem";
      src:
        local(".HelveticaNeueDeskInterface-Regular"),
        local(".LucidaGrandeUI");
    }
    
    body {
      font-family: "MacSystem", sans-serif;
    }

The trick there is to pick the "rarest" one first. As I type this on Yosemite 10.10.1, it `font-family: ".LucidaGrandeUI";` works, so it _has_ to be second in the list for this to work.

You could extend this idea to Linux and Windows and stuff too, I'm sure, and make a big ol' `@font-face` declaration that covers all the ground. If anyone is so inclined, feel free to post it and I'll link it up here.

[Twitter](https://twitter.com/intent/tweet?text=OS Specific Fonts in CSS&url=https://css-tricks.com/os-specific-fonts-css/&via=real_css_tricks) [Facebook](https://www.facebook.com/sharer/sharer.php?u=https://css-tricks.com/os-specific-fonts-css/) [Google+](https://plus.google.com/share?url=https://css-tricks.com/os-specific-fonts-css/)
