# Travel Blogging with Jekyll, iPad, and Self Hosted Git Repo

_Captured: 2015-11-29 at 12:23 from [jml.is](http://jml.is/tech/2015/11/12/travel-blogging-with-jekyll-ipad-and-self-hosted-git-repo.html)_

Having recently upgraded to an iPad Pro and [Jekyll](http://jekyllrb.com) as my local blogging solution, I had to find a way to make things work while on the road. Perusing Jekyll from a MacBook is easy - write, git push, done. The usual magic on the other end (usually through _hooks/post-receive_) takes care of the rest. On iPad… it gets a little bit more complicated, not impossible though.

_Please note that while I had access to an iPad Pro for the past weeks and wrote this on and with one, the same setup works handily on my iPad Air 2 and, with changed apps (and sometimes even better, think improved sharing), on any Android tablet._

## Setup

jml.is runs on the cheapest possible [Digital Ocean](https://www.digitalocean.com/?refcode=976704d97fa4) server setup, a $5/month server. Static HTML just doesn't need that much, plus all pictures are hosted elsewhere (more about that below). Set this up as recommended on Jekyll's own "[Automated Methods](http://jekyllrb.com/docs/deployment-methods/#automated-methods)" and you're all set.

Download [Editorial for iOS](http://omz-software.com/editorial/) ($9.99), [Working Copy for iOS](http://workingcopyapp.com/), Flickr (or a similar solution to host pictures), Photoshop Mobile or VSCO Cam to edit images.

## Blogging

![Explore Mikka Luster's photos on Flickr. Mikka Luster has uploaded 491 photos to Flickr.](https://farm1.staticflickr.com/573/22562752197_603a5516da_b.jpg)

> _Working Copy (left) to Editorial (right) and back_

Setup Working Copy on your iPad to clone your server git repository. Either open an existing post (in _posts) or create a new one. Use the share menu to share to Editorial which, at the first invocation, will prompt you to install the [Working Copy workflow](http://www.editorial-workflows.com/workflow/5231728385851392/YYF3YuB5oGM). Install it manually, if that doesn't work. Also install the [Jekyll "New Post Settings"](http://www.editorial-workflows.com/workflow/5897508043620352/K5vl5H_YCBA) workflow, this one makes setting FrontMatter much easier.

You're more or less set now, for text-only posts at least.

## Pictures

To add pictures, sounds, YouTube, and more, I simply use [embed.ly](http://embed.ly). Warning, constant rebuilds of the site will count against the 5,000 calls on the free plan, so add images as the last thing if you want to save API calls. Also turn on -incremental. The plugin can be [found here](https://github.com/ryanburnette/jekyll-embedly-plugin).

I take pictures on my RX 100 Mk III or Sony Alpha 6000 and download them onto my iPad via the [Sony Play Memories app](https://itunes.apple.com/en/app/playmemories-mobile/id489191124?mt=8). An alternative solution would be to use eye-fi's Moby Pro, which I use for my Canon 5D and other cameras without WiFi sharing built in.

![Explore Mikka Luster's photos on Flickr. Mikka Luster has uploaded 490 photos to Flickr.](https://farm1.staticflickr.com/593/22959008222_76cf252085_b.jpg)

> _An embedly embed, first outing with the iPad Pro_

After editing the image in Lightroom for iOS (I like the Dehaze settings for my iPhone and the RX 100), I upload them to Flickr. There I simply make them public and copy the URL to be added to an { embedly } tag.

## Getting the blog all shiny

### Maps

I am using Bing for my maps. Much as I'd like to use OSM, OSM doesn't provide static maps anymore (and Google Maps is completely out, due to its 640x480 restriction on images). This could be solved much more elegantly with a plugin, caching, etc, but for my uses (less than 5,000 visitors/day) using the [Bing Static Maps ruby gem](https://github.com/justinxreese/bing-location) and a few lines of totally inelegant code (hey, I am a hiker, not a coder) did the trick. If you want to use it as your starting point, add the bing-location gem to your Gemfile. Add a root key "bing" to your _config.yml and beneath it api_key: <[your bing maps api key](https://www.bingmapsportal.com)>. Done.

![](http://dev.virtualearth.net/REST/v1/Imagery/Map/Road/Hugenottenstrasse%2089%20Friedrichsdorf%20Germany?mapSize=970,200&key=AmD8XADJM8f5sl_M1QAYL8DA8314SQRBSFzJRzFMevtls1WWsc1skr7l3tLT0SBa)

Yes, I know, the `<img>` tag is missing title and alt, and there's **no** error checking, it's easy to hack that in. It's a really old version of the plugin, later versions have error checking, better parameter handling, and stability. You should be able to hack that in in a few seconds. For more parameters, @params does the work for you.

### What's Next?

Day/Week/Month archives for specific trips and a trip archive are next. Maybe a few more collections and code to track me more or less live while I hike. For this, I'd have to work a lot more with incremental builds and server code (my emergency responder sends a location every sixty seconds while I am on the mountain, the data is easily read from their website, but it's something I won't enable until I am actually on a mountain and above 12,000 feet).

I want to start a gear archive (backpacks, sleeping bags, etc.), that's just a matter of writing some templates and parsing some yml, but it's work. Right now it's Friday, the trail's calling, and I won't be near a computer for a while. Maybe in Episode 2, or so.
