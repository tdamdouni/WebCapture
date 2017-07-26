# updating a jekyll/github blog from the iPad, or anywhere, without touching git

_Captured: 2015-11-29 at 12:14 from [www.hardscrabble.net](http://www.hardscrabble.net/2014/jekyll_api/)_

**UPDATE April 2015:** Here's a much, much better way to do it: <http://www.hardscrabble.net/2015/how-to-jekyll-from-ios/>

First of all: if anyone subscribes to my RSS feed, I apologize for flooding it today with test posts as I futzed with this.

Today I wrote my first [Editorial](http://omz-software.com/editorial/) workflow and also my first Python script. Fun day!

Editorial is a power user text editor for the iPad. Before today I never really used it but I think I'll use it more now.

This project was inspired by [a recent episode of the tech podcast Core Intuition](http://www.coreint.org/2013/12/episode-118-wrapping-up-2013/). They were discussing blogging software. One of the hosts, Daniel Jalkutt, makes the Mac blogging app [MarsEdit](http://www.red-sweater.com/marsedit/), and they've both been around long enough to have really interesting thoughts on the space. MarsEdit allows bloggers to post to most of the major blog systems but not static blogs like [Jekyll](http://jekyllrb.com/) (what I use for this blog), [Pelican](http://getpelican.com/), [Octopress](http://octopress.org/) (which is built on Jekyll), [Roots](http://roots.cx/), or any number of other, similar projects.

Which is understandable because those don't really expose an API for it to integrate with. _But what if they did?_ (haha)

I'm going to step away from discussing the broader context of static blog tools and focus specifically on Jekyll blogs deployed to GitHub pages, which is the bulk of my experience.

Here's how I generally write and publish posts, before today:

  * clone or pull the git repo
  * use [poole](https://rubygems.org/gems/poole) to run `poole draft "Title Of Post"`, which reates a new markdown file for me
  * use vim to write the post
  * serve the blog locally to make sure it looks right
  * when I'm done, run `poole publish _drafts/title_of_post.md`, which moves the file into the `_posts` directly and inserts the current time into the configuration at the top
  * use git to commit and push the post up to GitHub, which will re-compile the site using `jekyll build`

I can do this easily on the computer and it's pretty nice. I can do this on the iPad using [Prompt](http://panic.com/prompt/) to SSH into a DigitalOcean server and it's _okay_. I can do the same on my iPod Touch and it's kind of awkward and overly small.

There are a few major advantages to having a static blog. To me, the main boon is the lack of a database. It's definitely an advantage that there's no server-side computation going on - the HTML is available to serve immediately after being requested - but maybe it's a disadvantage that there's no server-side API. In theory, a static blog API could do several things:

  * create posts
  * update posts
  * delete posts
  * render posts as JSON

What I've created today only does the first thing. It's pretty simple. It would need to do all of those, and probably much more I'm not currently imagining, to integrate with something like MarsEdit. But it's enough to do something pretty cool: now I can write posts in Editorial on my iPad (I'm writing this one that way) which has a browser built-in for research and an embarrassment of possibilities for extensibility because it's somehow snuck the Python scripting language into Apple's walled garden.

Here's a demo video (sorry it's so long):

Here's the source of the Rails project that serves as a Jekyll API: [maxjacobson/jekyll_api](https://github.com/maxjacobson/jekyll_api). Here's [the Editorial workflow](http://editorial-app.appspot.com/workflow/5026138770374656/tRls0F7xb8s) which will currently only work for me, because I'm not sure the best way to share the source for something like this that's not just a script, but a chain of macros and scripts.

Actually, here's the most-relevant chunk of the workflow, my first python script, somewhat out of context:
    
    
    #coding: utf-8
    import workflow, requests
    
    script_params = workflow.get_parameters()
    
    auth_token = script_params["auth_token"]
    blog_id = script_params["blog_id"]
    
    post_slug = workflow.get_variable("slug")
    post_text = workflow.get_variable("text")
    
    params = {
      'auth_token': auth_token,
      'post[slug]': post_slug,
      'post[text]': post_text
    }
    
    response = requests.post("http://pairwith.maxjacobson.net:3000/blogs/" + blog_id + "/publish", params=params)
    
    if response.status_code == 200:
      workflow.set_output("Successfully posted")
    else:
      workflow.set_output("Something went wrong")

As I mention in the video, _in theory_ I can deploy this app to an actual production environment (note the weird URL if you like) and allow other people to use it. I probably won't.

Alright now I'm going to press "Post". I'm kind of nervous! Wish me lu
