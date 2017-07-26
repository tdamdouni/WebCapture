# Generating a PDF using the new printing stuff in iOS 4.2

_Captured: 2016-04-06 at 09:04 from [stackoverflow.com](http://stackoverflow.com/questions/4356436/generating-a-pdf-using-the-new-printing-stuff-in-ios-4-2/8141008#8141008)_

I made a discovery: this is possible, if you're willing or allowed to use private API. (e.g., in an enterprise app.)

The method: create your formatter as usual; install it in a UIPrintPageRenderer.

**Set the renderer's private properties `paperRect` and `printableRect` appropriately.**

`numberOfPages` now works!

Set up your pdf cgcontext like normal, and draw the page with the renderer's `drawPageAtIndex:inRect:` method. Holy cow, it worked.

Obligatory protestation: yes, I know Apple doesn't want you submitting apps that call (e.g.) `[ppr setValue:[NSValue valueWithCGRect:page] forKey:@"paperRect"];` and will bounce them.
