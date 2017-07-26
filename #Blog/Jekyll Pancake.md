# Jekyll

_Captured: 2015-11-03 at 19:08 from [theworldstatic.org](http://theworldstatic.org/guides/jekyll)_

## Basic Commands
    
    
    jekyll new NAME    # Initializes new project NAME
    jekyll build       # Builds the static site
    jekyll serve       # Starts the preview server
                       #   (use -w to watch for changes)
    jekyll help        # Show command usage information
    

## Getting Started

A basic Jekyll project might look like:
    
    
    # jekyll configuration file
    _config.yml
    
    # ruby dependencies
    Gemfile
    
    # templates
    _layouts/my-layout.html
    
    # posts
    _posts/  # see posts
    
    # source (everything else)
    foo/page.md
    css/all.css
    js/all.js
    

## Pages

Jekyll supports conversion of `.markdown`, `.md`, `.textile`, `.sass`, `.scss`, and `.coffee` formats out of the box. Files with "[YAML Front Matter"](http://jekyllrb.com/docs/frontmatter/) will be processed by Jekyll. Files without the front matter (e.g. `.html`, `.js`, `css` files) will be copied directly to the output folder unchanged.

## Posts

Jekyll has special support for blog posts (i.e. content which has a specific date), which go under `_posts`. See [here](http://jekyllrb.com/docs/posts/) for more on how to take advantage of this feature.

## Templating

[Templates](http://jekyllrb.com/docs/templates/), also known as layouts in Jekyll, live in `./_layouts`. By default they are written in the [Liquid](http://liquidmarkup.org/) templating language. Liquid template files end in `.html`.

Also by default, pages do not get any layout. You must explicitly specify which layout to use the page's front matter. In Jekyll v2, you can specify a [default layout](http://jekyllrb.com/docs/configuration/#frontmatter-defaults) (along with other default frontmatter variables).

For example, to apply a layout `_layouts/pineapple.html` to `fruit/apple.md`, you need to specify the following at the top of `apple.md`:
    
    
    ---
    layout: pineapple
    ---
    
    ... markdown content goes here ...
    

Apart from `layout`, there are other special keywords such as `permalink` and `published`. You can learn more about that [here](http://jekyllrb.com/docs/frontmatter/). Everything else gets passed to the template, in the `page` hash.

## Extensions

Starting with v2, Jekyll has built-in support for Sass and Coffeescript. For a Sass or Coffeescript file to be converted, the file needs to have the correct extension. Also, the file must contain empty frontmatter (two lines of triple dashes), like so:
    
    
    ---
    ---
    
    // sass or coffeescript goes here
    

For Less, there's [jekyll-less](https://github.com/zroger/jekyll-less).
