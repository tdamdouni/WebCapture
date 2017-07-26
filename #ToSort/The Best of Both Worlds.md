# The Best of Both Worlds

_Captured: 2016-06-18 at 13:40 from [m.high90.com](https://m.high90.com/the-best-of-both-worlds-fdce29d2c88c#.2123rr4hy)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*iPGVeiDCQN-meEG2pDTRXg.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*iPGVeiDCQN-meEG2pDTRXg.jpeg)

> _From The Children's Book of Stars, 1908. G.E. Mitton_

It's never been easier to choose a blog engine and it's never been harder.

For someone who just wants to write and get their words out in front of as many people as they can, it's hard to beat [Medium](http://medium.com). Here are a few things they have to offer:

  * Costs no money to publish
  * A large audience
  * Clean, responsive design
  * Basic branding and custom domain support
  * A simple true-WYSIWYG editor for web and mobile
  * Subscriptions
  * Elegant community interaction tools

For those of us who are a little more picky, Medium has some less appealing aspects:

  * Your stuff lives on someone else's platform
  * You appear to be a Medium staff writer
  * Limited control over site design and layout

#### Roll Your Own

There are so many alternatives to Medium that I'll just list a few. You could try a hosted blog engine like [Wordpress](http://wordpress.com), [Squarespace](http://squarespace.com), and [Tumblr](http://tumblr.com), or a self-hosted one like [Wordpress](http://wordpress.org), [Jekyll](http://jekyllrb.com), [Pelican](http://blog.getpelican.com/), [Hugo](https://gohugo.io/), [Statamic](http://statamic.com), or [Docpad](http://docpad.org/). Many of the self-hosted options are static engines, which typically means they take [Markdown](https://daringfireball.net/projects/markdown/) input and process it to create static HTML files.

If the following items are appealing, then static, self-hosted blogging may be for you:

  * Total control over architecture, structure, and design
  * Unquestioned ownership of identity, design, and content
  * Write in Markdown with a plain-text editor
  * Manage your blog via command line, hosted on the server of your choice
  * Offboard or limited search and community interaction tools

#### I'm Conflicted

It's safe to say that static, self-hosted blogs tend to attract the nerdier slice of the vast writing public. I am a proud member of that slice.

Having said that, even nerds get tired of dealing with the day-to-day demands of managing _yet-another-web-application_, especially if that's what they do all day long, day-in and day-out.

This situation becomes even more complicated when you have a number of authors with varying experience and priorities. For a multi-author static site, version control is essential, but dealing with commits and compiling and conflicts can be kind of a drag. Also, static blog engines tend to be quirky beasts that are easy to break.

Developers should find the following train of thought familiar:

> My_ application is so simple, clean, and robust that it doesn't even need _comments_, while _your_ application is a frightening, tangled, confusing morass of spaghetti code that will shatter into a million pieces at the slightest touch._

It's possible for two developers to simultaneously feel this way about each other's projects _and both be right_. Such is the nature of web development, and blog engines are no exception. _Every_ collaborator on _every_ static blog or podcasting site I've managed has felt that our shared static blog workflow involved unnecessary confusion, friction, and anxiety.

Thankfully there are attractive alternatives.

#### Stop Giving Me Static

Sometimes you just want to _write_. In that case, it's hard to beat this:

Just write, no obstacles.

While I personally prefer the text-editor inspired styling of [Ulysses](http://www.ulyssesapp.com/) (which offers the ability to publish directly to Medium [from Mac](http://ulyssesapp.com/blog/2015/11/publish-stories-on-medium-directly-from-ulysses/) or [iOS](https://medium.com/@ovanrijswijk/medium-publishing-with-ulysses-ios-71802bb5edb2#.r02zev5zj) if you're so inclined) Medium's approach is well-executed and gets out of your way entirely. They also offer a large, intelligent, and involved audience, which has drawn some [big name](https://www.engadget.com/2016/02/23/bill-simmons-grantland-replacement-the-ringer-medium/) [publishers](https://theawl.com/), [companies](https://m.signalvnoise.com/signal-v-noise-moves-to-medium-c8083ce19686#.oc1dfpl7v), and [writers](https://medium.com/@joshuatopolsky). Even better, Medium's [response system](https://help.medium.com/hc/en-us/articles/214571938-Responses) ([don't call them comments](https://medium.com/@ev/responses-are-not-free-for-all-comments-6c9a4927c03#.swl1qqlpk)) is elegant and restrained.

So what if you could have it all? What if you could have the best of both worlds?

That's what we're going to try.

#### The Middle Way

[The high90 Blog](https://m.high90.com/) has now moved to Medium. Bob and Mark's old posts are still archived at their former URLs, but going forward they'll be posting directly to our new home, where they can take advantage of all the great features that platform has to offer.

I'll be doing the same thing, with one little caveat. I'm a little quirky about those issues we mentioned earlier: identity, ownership, and design. Also, I tend to use my blog as a platform to keep my development skills from getting rusty and as a playground to try new things.

To that end, I've created version six of my personal blog [The Mindful Bit](http://themindfulbit.com), built with Jekyll this time and hosted on Github Pages ([thanks for the inspiration Eddie!](http://www.practicallyefficient.com/2016/04/03/static-and-free.html)).

Using Medium's [import feature](https://help.medium.com/hc/en-us/articles/218572107-How-to-move-to-Medium), my entries will be cross-posted to the high90 Blog, and canonical links will point back to the original on my personal site. In this way, we can enjoy all the benefits of Medium, while I get to keep the advantages of a static blog where it matters to me.

What's nice is that Bob and Mark can decide to build their own static sites if they change their minds someday, and they'll just import their posts in the same way I do. Freedom, flexibility, identity, and audience.

Canonical links are an HTML element designed to help search engines deal with duplicate information on the web and properly point to its "official" source. Google has an [excellent walkthrough](https://support.google.com/webmasters/answer/139066?hl=en) on its support site.

To use an example already available, the post _Noble Absence_ lives on [my personal blog](http://themindfulbit.com/blog/noble-absence) and was cross-posted to the high90 blog [on Medium](https://m.high90.com/noble-absence-ef2cad89ca6e#.xptc2yp2q). If you use Medium's import feature they insert the following tag into the page's <head> element:
    
    
    <link rel=”canonical” href=”http://themindfulbit.com/blog/noble-absence">

Now the search engines know which one of the two sites is the original.

In theory, using canonical links prevents search engines from penalizing you for having your stories in more than one place. In practice, implementing canonical links can be [a bit tricky](https://webmasters.googleblog.com/2013/04/5-common-mistakes-with-relcanonical.html), so use them with care.

In addition to the aforementioned canonical links, Medium also provides an attribution link at the bottom of your imported posts to send interested readers back to your site:
