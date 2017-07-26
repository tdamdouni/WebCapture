# Build a Jekyll Blog in 60 seconds

_Captured: 2015-09-10 at 15:20 from [community.nitrous.io](https://community.nitrous.io/tutorials/build-a-jekyll-blog-in-60-seconds)_

![](https://nitrous-community.s3.amazonaws.com/images/jekyllrb.png)

[Jekyll](http://jekyllrb.com/) is a markdown-based static site generator that is great for blogs and static websites that do not require a database. Jekyll is used by tons of programmers for their personal blogs and project websites, as it's free, easy, and much more "hackable" than most other site-builders.

As an added benefit, [GitHub](https://www.github.com/) also provides free hosting for static sites and blogs via [GitHub Pages](https://pages.github.com/)!

This post will show you how to setup a jekyll blog in just a few minutes using [Nitrous](https://www.nitrous.io). In Part 2., we'll spend some time deploying the blog to [GitHub Pages](https://pages.github.com/) and setting up a custom domain.

## Prerequisites

## Creating a new Jekyll container on Nitrous

Creating a Jekyll container on Nitrous is very easy. In the [new container](https://pro.nitrous.io/app/#/containers/new) screen, find the `Jekyll` container, give your new site a name, and click `Next`.

![Nitrous jekyll template](https://nitrous-community.s3.amazonaws.com/images/jekyll-template.jpg)

> _Nitrous jekyll template_

You'll be shown a status screen as your Jekyll development container is created. When it's completed (it should take about 20 seconds), click the blue `Open IDE` button to launch the IDE.

The Jekyll container will take care of a lot of the configuration for you in advance, including running `jekyll new jekyll`, where the 2nd mention of `jekyll` is the new site we've created. Now that we're in our new Jekyll container, let's look at the files we'll be editing.

### Directory structure

Since Jekyll is working with static sites, we're really just working with text and transforming text into markup (html). In our case, we create some pages in markdown, and Jekyll spits out markup based on a layout defined in the `_layouts` folder.

I named my container `Jekyll`, so my blog files will be in `~code/jekyll`. If we `cd` into the jekyll folder and `ls` to list the directory, let's see what we're working with:

We won't go into detail on all of the files that have been created, but here are the important ones:

#### `about.md`

Any files you create in the root directory will be pages that are available on your blog. So you might want to have an "About me" page, or a "Projects" page listing some things you've worked on.

#### `_config.yml`

When you're using Nitrous, you don't need to worry about this file too much. You can setup a lot of [advanced features](http://jekyllrb.com/docs/configuration/) in the `_config.yml` file, including server settings, build settings, display settings, and more.

#### `index.html`

This is going to be your landing page. Typically you'll have a list of your blog posts, and you'll see in this file that we're just looping through all of the posts in the `_posts` directory.

#### `_layouts`

The layouts directory includes templates that encapsulate your static pages and blog posts. Layouts are defined on each page in the YAML Front Matter where you define the layout and title of the page. The page content is then injected into the page via the {{ content }} tag as you'll see in each layout file.

![jekyll layout](https://nitrous-community.s3.amazonaws.com/images/jekyll-dir.jpg)

> _jekyll layout_

#### `_posts`

This directory is where your blog posts reside. You will need to name your posts according to the following convention: `YEAR-MONTH-DAY-title.md`. You can define other attributes of the blog post in the [YAML front matter](http://jekyllrb.com/docs/frontmatter/).

### Starting the Jekyll server

Jekyll comes with a lightweight development server built-in that will let you preview your site via the [Nitrous Preview Menu](https://community.nitrous.io/docs/preview-your-app).

Since our container has a sample site already created, let's go ahead and start the simple webserver so we can preview our blog and start making some changes. To run the jekyll server on Nitrous, you'll need to change directories into your blog's root directory and run `jekyll serve`:

![jekyll server output](https://nitrous-community.s3.amazonaws.com/images/jekyll-serve.png)

> _jekyll server output_

Ok great, now we know our server is running properly on port 4000. To preview our new Jekyll blog, we just need to navigate to the _Preview_ menu in the Nitrous IDE:

![preview menu](https://nitrous-community.s3.amazonaws.com/images/jekyll-preview.png)

> _preview menu_

Kaboom! Our Jekyll blog is up and looking good.

![jekyll blog](https://nitrous-community.s3.amazonaws.com/images/jekyll-blog.png)

> _jekyll blog_

### Automatic site re-generation upon save

After version 2.4.0, the Jekyll server will run with the `\--watch` flag by default. This means you just need to save your changes and refresh your preview to see the live changes. Check out the example below where we're editing a css file and previewing changes:

![jekyll watch](https://nitrous-community.s3.amazonaws.com/images/jekyll-watch.gif)

> _jekyll watch_

## Deploying to Github Pages for Free blog hosting

Stay tuned for the next post in this series, where we'll walk you through how to deploy your new Jekyll blog to [GitHub Pages](https://pages.github.com/) and how to setup a custom domain.
