# Browsing the Web with cookies disabled

_Captured: 2017-04-20 at 14:05 from [jgthms.com](http://jgthms.com/browsing-the-web-with-cookies-disabled.html)_

For more than a month now, I've been on a cookie diet: I've **disabled all browser cookies**.

![Blocking cookies in Chrome](http://jgthms.com/images/post/cookie-blocking.png)

> _No cookies for me anymore_

## Can't login

The main issue is logging into any website, as Web authentication requires a cookie to be stored on the client's computer.

![Can't login to Twitter](http://jgthms.com/images/post/cookie-no-twitter-login.png)

> _It's like an infinite login loop_

## Can't interact

Some basic interactions, like adding items to a cart, are not possible anymore.

![Can't shop](http://jgthms.com/images/post/cookie-amazon-cant-shop.png)

> _I saved a lot of money_

## Can't even browse sometimes

Some website don't even load, because a script tries but fails to access localStorage.

![Can't listen to music](http://jgthms.com/images/post/cookie-soundcloud.png)

> _MuteCloud, amirite?_

![Can't watch a video](http://jgthms.com/images/post/cookie-vimeo.png)

> _The layout looks nice even with no content_

![Can't watch a vine](http://jgthms.com/images/post/cookie-vine.png)

> _I waited more than 6 seconds, which defeats the whole purpose of watching the vine_

I liked the **Forbes** one in particular.

> This browser has no localStorage, we cannot prefetch.

![Can't read Forbes](http://jgthms.com/images/post/cookie-no-localstorage.png)

> _I like how relevant the quote was_

## Can GMail without Google

Weirdly enough, by allowing the pattern `[*.]google.com`, I can log in to GMail **without** being automaticlly logged in to Google, YouTube, and Blogger.

## Is blocking cookies a good idea?

Honestly, it's a **pain** to maintain. By using a whitelist strategy, every time I encounter a login form, I need to manually add the domain pattern to the list of approved websites. And when a website doesn't load at all, I just don't bother.

Do I feel less tracked and more secure? Of course! /s
