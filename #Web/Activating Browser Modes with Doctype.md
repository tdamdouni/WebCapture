# Activating Browser Modes with Doctype

_Captured: 2016-12-10 at 11:16 from [hsivonen.fi](https://hsivonen.fi/doctype/)_

The main conclusion to draw from this article is that you should start all your HTML documents (i.e. anything that gets served as `text/html`) with `<!DOCTYPE html>` as the first thing in the source. (Read on to learn why.)

If you want to take extra care to make sure that users of IE8, IE9 or IE10 cannot press a button that makes your site regress as if it was being viewed in IE7, either configure your server to send the HTTP header `X-UA-Compatible: IE=Edge` for `text/html` or put `<meta http-equiv="X-UA-Compatible" content="IE=Edge">` in the `head` of your HTML documents (before any scripts). This will, however, make the HTML document invalid and if you don't include these IE-specific incantations, the default behavior of IE is reasonable in most cases, so you don't really _need_ to jump through these IE-specific hoops. (Read on for exceptions.)

### `text/html`

Here are simple guidelines for choosing a doctype for a new `text/html` document:

Standards mode, cutting edge validation
    

`<!DOCTYPE html>`

This is what you should use. With this doctype, you can [validate](http://html5.validator.nu/) new features such as `<video>`, `<canvas>` and ARIA. Please be sure to test your page in the latest versions of the top browsers.

Standards mode, legacy validation target
    

`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`

This doctype also triggers the Standards mode, but lets you stick to less precise legacy validation that doesn't know about new features in case your organization has silly policies that require targeting legacy validation. But you really should be using `<!DOCTYPE html>` and get the policies of your organization revised.

You'd like to use the Standards mode, but you use sliced images in table layouts and don't want to fix them
    

`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">`

This gives you the Almost Standards mode. Please note that your layouts based on sliced images in tables are likely to break if you later move to HTML5 (and, hence, the full Standards mode), so it's better to make your designs Standards mode-compatible right now.

You willfully want the Quirks mode
    

No doctype.

Please don't do this. Willfully designing for the Quirks mode will come and haunt you, your coworkers or your successors in the future.

If you frustrated by the differences between old IE versions and still need to support them due to client requirements, it is better to apply specific hacks for legacy versions using [conditional comments](http://www.quirksmode.org/css/condcom.html) than seek commonality in the Quirks mode.

I am not recommending any of the XHTML doctypes, because [serving XHTML as `text/html` is considered harmful](http://hixie.ch/advocacy/xhtml). If you choose to use an XHTML doctype anyway, please note that the XML declaration makes IE 6 (but not IE 7!) trigger the Quirks mode.

### `application/xhtml+xml`

The simple guideline for `application/xhtml+xml` is _not_ to use a doctype _at all_. This way the page cannot be "strictly conforming" XHTML 1.0, but that does not matter. (Please see the [Addendum](https://hsivonen.fi/doctype/) below.)

Here are simple guidelines for choosing an `X-UA-Compatible` HTTP header or `meta` tag for a new `text/html` document that _already has a doctype that triggers the standards mode or almost standards mode in other browsers_:

Your domain is not on Microsoft's blacklist and you care more about not having to have browser-specific cruft than about making sure users can't regress the rendering to IE7 behavior
    

You don't need to include an `X-UA-Compatible` HTTP header or `meta` tag.

Your domain is on Microsoft's blacklist, your domain (like iki.fi!) has other authors whose broken sites may induce users to enable Compatibility View for the _whole domain_, you are concerned about Google or Digg framing your site or you want to make sure users cannot enable the Compatibility View
    

Include either the following `meta` element (which in invalid in HTML5) on your page `<meta http-equiv="X-UA-Compatible" content="IE=Edge">` (before any `script` elements!) or set the following HTTP header on your page: `X-UA-Compatible: IE=Edge`

Your site worked in IE7 but breaks in IE8 or IE9
    

First, include either the following `meta` element (which in invalid in HTML5) on your page `<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7">` (before any `script` elements!) or set the following HTTP header on your page: `X-UA-Compatible: IE=EmulateIE7`

Then fix your site not to rely on non-standard IE7 behaviors and migrate to `IE=Edge`.

Your site worked in IE8 but breaks in IE9
    

First, include either the following `meta` element (which in invalid in HTML5) on your page `<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE8">` (before any `script` elements!) or set the following HTTP header on your page: `X-UA-Compatible: IE=EmulateIE8`

Then fix your site not to rely on non-standard IE8 behaviors and migrate to `IE=Edge`.

Your site worked in IE9 but breaks in IE10
    

First, include either the following `meta` element (which in invalid in HTML5) on your page `<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE9">` (before any `script` elements!) or set the following HTTP header on your page: `X-UA-Compatible: IE=EmulateIE9`

Then fix your site not to rely on non-standard IE8 behaviors and migrate to `IE=Edge`.

There are a couple of important reasons against using Chrome Frame:

  * Chrome Frame lacks IE's accessibility support. When Chrome Frame is activated, the content area in IE becomes an accessibility black hole. That is, screen readers and Windows Speech Recognition don't work with Chrome Frame.
  * Making your site tell users that they should install Chrome Frame perpetuates the security anti-pattern of sites telling users that they should let someone install a privileged native-code plug-in on their computer in order to use a site.
