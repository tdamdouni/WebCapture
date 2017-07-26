# Post to a Jekyll blog from an iPad

_Captured: 2015-09-26 at 17:07 from [www.stevencombs.com](http://www.stevencombs.com/web/2014/07/01/post-to-a-jekyll-blog-from-an-ipad.html)_

## Read a recent post:

In an [earlier post](http://www.stevencombs.com/web/2014/06/13/why-i-moved-from-blogger-to-jekyll.html), I discussed my move from [Blogger](https://www.blogger.com) to a [Jekyll blog](http://jekyllrb.com/) hosted on [GitHub](https://github.com/). While I could create a new blog post, the inability to submit a post to my blog from an iPad was a negative of the migration. I noted this was not possible because there is currently no way to manage a GitHub repository on an iOS device.

Several bloggers suggest alternatives:

  * [Wait until you get home](http://www.garron.me/en/blog/blogging-from-ipad-jekyll-dropbox.html) to submit the post
  * [Use remote connection](http://www.candlerblog.com/2012/04/01/remote-octopress-workflow/) iOS software to connect to a Mac
  * Use the iPhone only app [Octopage](https://itunes.apple.com/us/app/octopart/id592802548?mt=8&uo=4&at=10l9vL) (I'm really not interested in running iPhone only apps on my iPad)

{UPDATE - September 10, 2014: Carl Hicks gave a [shout out to this post](http://carlhicks.me/mobile-jekyll-posting/) and then added links to [Editorial Python scripts posted on GitHub](https://gist.github.com/MalphasWats) created by Mike, aka, MalphasWats. I haven't given these a try yet, but they appear to be a perfect way to submit and fetch posts to your Jekyll blog within [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=10l9vL).}

Each of these options involve extra steps and software and while technically they allow me to post via an iPad, they are not optimal solutions. I think I have a better solution as it allows me to use the wonderful iOS text editor [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=10l9vL).

While my solution doesn't require Editorial, its use streamlines my workflow. For those not familiar with this iOS software, Editorial includes a built-in web browser. This allows me to write and research all within the same app.

> **Note:** The iOS app [Writing Kit](https://itunes.apple.com/us/app/writing-kit-research-write/id426208994?mt=8&uo=4&at=10l9vL) also has this capability.

Editorial also includes a bookmarks manager within the editor to quickly launch sites. I will use both of these features as the basis for my all-in-one Jekyll blog posting solution.

I am a new user of GitHub and what some may already know, I recently discovered. You can add files to a GitHub repository using a web browser. GitHub includes a rudimentary browser based editor that you can use to create/edit code or text files.

In Editorial, I created a bookmark to my blog's GitHub `_posts` online directory as shown in the image below.

![](http://www.stevencombs.com/images/posts/2014-07-01-editorial-posts-bookmark.png)

> _When I tap the Editorial bookmark, GitHub provides an online list of the_

`_posts` directory within its built in web browser as shown in the image below.

![](http://www.stevencombs.com/images/posts/2014-07-01-jekyll-posts.png)

See the **`+`** symbol highlighted? That's the secret sauce. If you click the **`+`** symbol, GitHub will present a new online form as shown in the image below.

![](http://www.stevencombs.com/images/posts/2014-07-01-jekyll-posts-form.png)

Add the title of the post, copy the markdown from the Editorial text editor, return to the web browser and then paste the markdown code into the web based editor. Update the commit information at the bottom of the page (including optional notes) and finally click the `Commit new file` at the bottom-right of the page. The post is now added to your blog.

That's pretty simple. Given Editorial's extensibility through the built in [Python](https://www.python.org/) interpreter, I have to wonder if this process can be automated via an Editorial workflow. Maybe some enterprising programmer out there can figure this one out. Doubtful I'll have time to do so. Still, that's a pretty easy solution that allows me to use Editorial and my iPad as a complete Jekyll blog posting solution.

Have another solution? Drop it in the comments below.
