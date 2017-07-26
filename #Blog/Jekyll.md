# Jekyll

_Captured: 2015-12-12 at 00:08 from [imaginaryterrain.com](http://imaginaryterrain.com/classes/2014/jekyll/)_

![Diagram of Jekyll data flows](http://imaginaryterrain.com/classes/2014/jekyll/images/jekyll.png)

> _With Jekyll, you write content in text files and generate the website locally._

### Basics

### Liquid

Developed by the Shopify people; popular in Ruby circles but starting to show up everywhere.

  * [Liquid templating language](http://liquidmarkup.org)
  * [Liquid template docs](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) "for designers"
  * [Friendly Liquid docs](http://docs.shopify.com/themes/liquid-basics) for Shopify but general principles apply

### Other template languages

  * [Django templates](https://docs.djangoproject.com/en/dev/topics/templates/) (Django/Python) started it all
  * [Mustache](http://mustache.github.io) (multi-environment)
  * [Handlebars](http://handlebarsjs.com) (JavaScript)
  * [AngularJS](http://angularjs.org) (JavaScript) uses the same approach in its templates

### More with Jekyll

### Sites using Jekyll

  * [List in Jekyll docs](https://github.com/jekyll/jekyll/wiki/Sites) (incomplete and slewed toward the devs!)
  * Obama 2012 fundraising platform (static files, not the transactional areas, obviously)
  * Development Seed's [Healthcare.gov](https://www.healthcare.gov) (the static part of the site)
  * GOV.UK service design: [code](https://github.com/alphagov/government-service-design-manual) and [live site](https://www.gov.uk/service-manual)
  * [Jessica Hische](http://jessicahische.is/awesome) is on Kirby, a similar CMS ([see below](http://imaginaryterrain.com/classes/2014/jekyll/))

### Markdown

By default, you save your pages as textfiles, with formatting described in Markdown. There are some Markdown editors, desktop and online.

  * [Markdown project documentation](http://daringfireball.net/projects/markdown/)
  * [Prose](http://prose.io) (online, integrated w. GitHub)
  * [iA Writer](http://www.iawriter.com/mac/) (Mac, iOS)
  * [Byword](http://bywordapp.com) (Mac, iOS)
  * [MarkdownPad](http://markdownpad.com) (Win)
  * [MOU](http://mouapp.com) (Mac, iOS)

### Other "Indie CMSes"

There are a whole raft of tools that aim for simplicity and flexibility. Some use databases and run on the server, while others live on local machines like Jekyll. There are even a few that store data in flat files but reside server-side.

  * [Craft](http://buildwithcraft.com)
  * [Statamic](http://statamic.com) (static and dynamic, not a reference to the Devil)
  * [ExpressionEngine](http://expressionengine.com) (You can build almost anything with EE; it's a fine tool but made by an eccentric company)
  * [Cactus](https://github.com/koenbok/Cactus)
  * [Escher](http://www.eschercms.org)
  * [Ghost](https://ghost.org) ("just a blogging platform" - worth a look for philosophy)
  * [ProcessWire](http://processwire.com)
  * [Hyde](http://ringce.com/hyde) (a Python-based Jekyll; get it?)
  * [Pico](http://pico.dev7studios.com/docs.html#)

### Design philosophy

We had a great question. To paraphrase:

_I noticed that the sites on the [list of Jekyll sites](https://github.com/jekyll/jekyll/wiki/Sites) all tend to be text-based. Can you use Jekyll to make sites with images?_

Yes, you can build image-based sites or ones with complicated layouts.

I don't really pay attention to the tools that people use to maintain their sites because a skilled hand can maintain _almost_ any site from almost any tool. I did recently note that [Jessica Hische](http://jessicahische.is/awesome) - known chiefly as a lettering designer - runs her site on [Kirby](http://getkirby.com), a flat-file CMS that's similar to Jekyll. She's got a lovely, highly visual site, especially the portfolio section.

There's no Jekyll site "look." With Jekyll and the indie CMSes, layout, structure, and interactivity are up to you. You want it, you can build it, but you'll have to gather the tools yourself. That's good and bad, depending on the task and your team's preferences.

Let's take the ubiquitous JavaScript [image slider](http://www.woothemes.com/flexslider/). Say you wanted a slider for a website. (I'll wager that you can find a better design element than a slider, but I want a common example.) With WordPress, you could find a photo gallery plugin and install the script, supporting CSS and images, templates, and content types in the database, all with a few clicks. Jekyll won't give you that help. You'll have to find the script yourself, and you'll need to assemble the templates.

Each of these approaches embodies its own kind of simplicity.

WordPress tightly integrates the frontend and backend, tying HTML/CSS/JavaScript for templates in with PHP code and the database. It's easy to add new features - find the right plugin and click - but complexity creeps in if you want to customize anything, or if the plugin plays badly with other plugins.

Jekyll will process your text and image content, but it won't do anything else for you. The Jekyll approach requires more knowledge at the start, but tweaks are easier, and the parts of the system are clearly and cleanly separated.

Software embodies someone's world view. Jekyll appeals to people who want a high level of control over details, whether that means the site's organizational structure, [micro typography](http://ia.net/blog/the-web-is-all-about-typography-period/), or HTML markup.
