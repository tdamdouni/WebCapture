# Change the Font Size of Web Pages in Safari for iOS with Bookmarklets

_Captured: 2017-01-17 at 08:56 from [osxdaily.com](http://osxdaily.com/2012/05/11/change-font-size-safari-ios-bookmarklets/)_

![Change font size on Safari for iPad with bookmarklets](http://cdn.osxdaily.com/wp-content/uploads/2012/05/font-size-ipad-safari-bookmarklets.jpg)

Everyone has run into a webpage where the font size is unbearably small on an iOS device, typically a reverse pinch gesture will make the text legible but on some pages that have a fixed width you then have to scroll sideways in addition to up and down. You can sort of get around that font size limitation by [using the Reader feature](http://osxdaily.com/2011/10/16/increase-font-size-in-safari-on-the-iphone-by-using-reader/) on an iPhone or iPad, but that's not ideal for every website either. This is precisely what two handy bookmarklets aim to resolve, by creating two fontsize increase and decrease buttons that can be accessed directly in Safari.

This addition is so useful that the concept should probably be included in future versions of Safari for iOS but only time will tell if that happens. In the meantime here's what you need to do to get this working.

Repeat this process separately for _both_ the increase and decrease functions:

  1. Open Safari on iPad or iPhone and create a bookmark for any page
  2. Tap the Bookmarks button at the top of the screen and choose "Edit"
  3. Edit the newly created bookmark, naming it either a minus (-) or plus (+) symbol and replace the URL by pasting in the appropriate javascript code shown below, depending on the desired function
  4. Save the bookmark change and load a new web page, tap on the + or - buttons to test font size changes live. Refreshing the page restores the font size to it's default.

**Decrease Font Size (-)**
    
    
    1
    
    
    
    javascript:var p=document.getElementsByTagName('*');for(i=0;i<p.length;i++){if(p[i].style.fontSize){var s=parseInt(p[i].style.fontSize.replace("px",""));}else{var s=12;}s-=2;p[i].style.fontSize=s+"px"}

**Increase Font Size (+)**
    
    
    1
    
    
    
    javascript:var p=document.getElementsByTagName('*');for(i=0;i<p.length;i++){if(p[i].style.fontSize){var s=parseInt(p[i].style.fontSize.replace("px",""));}else{var s=12;}s+=2;p[i].style.fontSize=s+"px"}

These bookmarklet tweaks work by editing a bookmark URL and replacing it with a javascript that changes on page behavior, similar custom bookmarklets have allowed us to [View Page Source in iOS Safari](http://osxdaily.com/2012/03/30/view-source-safari-ipad-iphone/) and [even use Firebug on iOS](http://osxdaily.com/2011/12/02/run-firebug-on-ipad-or-iphone/).

This very handy solution [comes from Marcos.Kirsch.com.mx](http://marcos.kirsch.com.mx/2012/04/29/font-size-bookmarklets/), who recommends placing them in the Safari bookmarks bar for easy access.
