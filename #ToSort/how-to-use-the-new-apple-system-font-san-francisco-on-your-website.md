# How to use the new Apple System Font SAN FRANCISCO on your website

_Captured: 2017-04-23 at 10:25 from [wpguru.co.uk](https://wpguru.co.uk/2015/11/how-to-use-the-new-apple-system-font-san-francisco-on-your-website/)_

![Screen Shot 2015-11-04 at 16.58.08](https://i1.wp.com/wpguru.co.uk/wp-content/uploads/2015/04/Screen-Shot-2015-11-04-at-16.58.08.png?resize=600%2C313&ssl=1)

Apple have a new System Font in El Capitan and all of their other products starting 2015: it's called **San Francisco**. It's very similar to their previous font Helvetica Neue, but apparently San Francisco is better for your eyes (not to mention the fact that Helvetica Neue isn't owned by Apple, and obviously we can't have that).

If you've tried searching for San Francisco on your Mac's Font Book app, you'll notice that it doesn't seem to exist. Likewise, if you're trying to use it in CSS it won't work.

Thanks to Craig Hockenberry I now know that this is because Apple haven't exposed the font the usual way; rather, it can be used in web content and via CSS with a new property they've introduced. Here's how:
    
    
    body {
      font-family: -apple-system, Helvetica Neue, sans-serif;}

Replace body with your own CSS property, and on Apple devices running El Capitan, iOS 9, watchOS2 or tvOS, your web views will sport San Francisco. Other devices will show Helvetica Neue when installed, or use a generic sans-serif font.

  * Read Craig's post for more information: <http://furbo.org/2015/07/09/i-left-my-system-fonts-in-san-francisco/>
  * Check out Apple's Surfin' Safari post on this topic: <https://www.webkit.org/blog/3709/using-the-system-font-in-web-content/>
  * Download this font for your own projects: <https://developer.apple.com/fonts/> (license required)
