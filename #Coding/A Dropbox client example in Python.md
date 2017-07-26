# A Dropbox client example in Python

_Captured: 2016-04-03 at 01:03 from [taught-process.blogspot.de](http://taught-process.blogspot.de/2012/05/asdlasd-asda-sd-asd-asdasd.html)_

While I was looking to get the program working for me, I did see that a lot of people were interested in using Dropbox as a file store for their applications and not really have each user sign-in and allow access to Dropbox. This is absolutely possible. There were other questions on how to use the access token and store it for future use. In this post, I answers the dummy's question - How can I use Dropbox with my Phyton program to store and distribute files that are not specific to a user's context.

I am assuming that the people reading this already understand [virtualenv](http://pypi.python.org/pypi/virtualenv). If not, there is a very simple explanation on the [flask site](http://flask.pocoo.org/docs/installation/#virtualenv). Let's start by creating an environment for ourselves. Here is what I did:

![](http://2.bp.blogspot.com/-ercWO8riSiQ/T7a4z_x0a8I/AAAAAAAAA5E/thVyrTcIYLA/s320/01.png)

Before we start, you should create an "App" in Dropbox. Start by going to <https://www.dropbox.com/developers/apps>. Create an App with any name you wish.

![](http://1.bp.blogspot.com/-BYyDg3ljkNo/T7a40J2qcYI/AAAAAAAAA5M/zzfpe4H_BvM/s640/02.png)

Notice that I left the access level to app folder. This will create a folder in Dropbox with the "App Name" that was provided. The program we write will have access to this folder ONLY.

Once you create the application, you'd notice that Dropbox creates a unique set of App key and App Secret. This is required to identify the application that accesses Dropbox. We will use it in our program.

![](http://3.bp.blogspot.com/-WrQlHhCLtT8/T7a6Z5QLbWI/AAAAAAAAA6I/cnoJVuUa0ps/s640/02a.png)

Before we start writing our programs, we need to ensure we have the dropbox libraries. If you are using [virtualenv](http://pypi.python.org/pypi/virtualenv) as I did, this should be as simple as running [pip](http://pypi.python.org/pypi/pip)

![](http://1.bp.blogspot.com/-4qBebuegiXM/T7a40qzJ3TI/AAAAAAAAA5U/YJsYpxtF76A/s640/03.png)

Dropbox uses [OAuth](http://oauth.net/). Therefore, each user will need to get a auth token to access Dropbox. The tokens need to be generated once and can be used repeatedly. Dropbox forums say that the token do not expire for a "long time". I believe that they live until the user revokes it. So if you are using one user to serve files, you have very little to worry about.

Here is a program that is adopted from the one on the [Dropbox Authentication Tutorial](https://www.dropbox.com/developers/start/authentication#python). We generate a request token; wait for the user to authenticate and print the auth tokens for reference and future use.

![](http://1.bp.blogspot.com/-fFUCi5wv2hQ/T7a40z___MI/AAAAAAAAA5c/V6NGqN1AypM/s640/04.png)
