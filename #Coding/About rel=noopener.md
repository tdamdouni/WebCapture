# About rel=noopener

_Captured: 2016-03-15 at 19:13 from [mathiasbynens.github.io](http://mathiasbynens.github.io/rel-noopener/)_

## What problems does it solve?

You're currently viewing `index.html`.

Imagine the following is user-generated content on your website:

Clicking the above link opens `malicious.html` in a new tab (using `target=_blank`). By itself, that's not very exciting.

However, the `malicious.html` document in this new tab has a `window.opener` which points to the `window` of the HTML document you're viewing right now, i.e. `index.html`.

This means that once the user clicks the link, `malicious.html` has full control over this document's `window` object!

Note that this also works when `index.html` and `malicious.html` are on different origins -- `window.opener.location` is accessible across origins! (Things like `window.opener.document` are subject to [CORS](https://www.w3.org/TR/cors/) though.) Here's an example with a cross-origin link:

In this proof of concept, `malicious.html` replaces the tab containing `index.html` with `index.html#hax`, which displays a hidden message. This is a relatively harmless example, but instead it could've redirected to a phishing page, designed to look like the real `index.html`, asking for login credentials. The user likely wouldn't notice this, because the focus is on the malicious page in the new window while the redirect happens in the background. This attack could be made even more subtle by adding a delay before redirecting to the phishing page in the background (see _[tab nabbing_](http://www.azarask.in/blog/post/a-new-type-of-phishing-attack/)).

TL;DR If `window.opener` is set, a page can trigger a navigation in the opener regardless of security origin.

## Recommendations

To prevent pages from abusing `window.opener`, use `[rel=noopener`](https://html.spec.whatwg.org/multipage/semantics.html#link-type-noopener). This ensures `window.opener` is `null` in Chrome 49 and Opera 36.

For older browsers, you could use `[rel=noreferrer`](https://html.spec.whatwg.org/multipage/semantics.html#link-type-noreferrer) which also disables the `Referer` HTTP header, or the following JavaScript work-around which potentially triggers the popup blocker:
    
    
    var otherWindow = window.open();
    otherWindow.opener = null;
    otherWindow.location = url;

Don't use `target=_blank`, _especially for links in user-generated content_, unless you have [a good reason to](https://css-tricks.com/use-target_blank/).

## Bug tickets to follow
