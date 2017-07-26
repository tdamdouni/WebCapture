# Command line web browser: internet search from BASH terminal

_Captured: 2017-05-20 at 10:08 from [www.raspberrypi.org](https://www.raspberrypi.org/magpi/command-line-web-browser/)_

![](https://www.raspberrypi.org/magpi/wp-content/uploads/2017/05/web-browser-command-line.jpg)

> _Most people aren't aware that you can access a command line web browser and search the internet from the text-based shell._

At first glance, a command line web browser doesn't make much sense. One of the advantages when using a desktop interface, like Raspbian, is that a web browser - and a search engine - is just a click away.

**This article first appeared in [The MagPi 56](http://magpi.cc/2oBtrJh) and was written by Lucy Hattersley.**

Getting online from the command line web browser is a lot easier than you'd imagine. And it's incredibly useful for searching for help, right inside the command line environment. And it's especially useful when you're working on a headless version of Rasbpian (without the PIXEL desktop interface).

There are many different text-based web browsers that enable you to access Google, Bing, DuckDuckGo, and other websites without having to boot into the PIXEL desktop interface.

### Set up the ELinks command line web browser

We're going to use [ELinks](http://magpi.cc/2pHyVX0):

Now you can open the web browser from the command line using:

The elinks interface is a full-screen command line web browser, so it replaces the command line. Press g to open a URL field. You can enter full URLs, such http://www.google.com or just shortened versions, such as raspberrypi.com.

Better yet, there are a few key bindings for helpful sites. Press g then enter these shortcuts:

  * d - dict.org search
  * sd - Slashdot
  * g - Google search

You can also enter Google search terms in the URL field. Press g, then enter 'g the magpi' to search for our website in Google.

Other keyboard shortcuts can be used to navigate the program:

  * g - Goto URL
  * Down Arrow - Next link
  * Up Arrow - Previous link
  * Return - Select link
  * Left Arrow - Back
  * u - Forward
  * q - Quit
  * . - Toggle link numbering
  * % - Toggle colours
  * t - New tab
  * T - Open link in new tab
  * > - Next tab
  * < - Previous tab
  * c - Close tab
