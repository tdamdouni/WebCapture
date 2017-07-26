# Building the Website

_Captured: 2015-09-26 at 15:48 from [learn.andrewmunsell.com](http://learn.andrewmunsell.com/learn/jekyll-by-example/tutorial)_

Jekyll websites are configured based on the contents of several files and folders. To begin, create a folder somewhere on your hard drive and open a Command Prompt window or Terminal session. You will also want to `cd` into this folder so that we can generate the website.

#### _config.yml

All configuration is done using the **[YAML** format](https://en.wikipedia.org/wiki/YAML). Primarily, you'll keep these configuration variables in a file called `_config.yml`. To configure Jekyll, create a file called `_config.yml` with a plain text editor. You do _not_ want to use an editor like Microsoft Word, WordPad, or TextEdit in rich text mode. Notepad on Windows or programs such as [Sublime Text 2](http://sublimetext.com/), Notepad++, or other plain text editors should be used to edit files for your Jekyll website.

Place the following content in the configuration file:
    
    
    name: ""
    description: ""
    
    url: "[YOURDOMAIN]"
    
    paginate: 10
    
    markdown: rdiscount
    permalink: pretty
    pygments: true
    

If you didn't install Pygments earlier, remove the `pygments: true` line in the configuration file above.

Ensure you replace "[YOUR DOMAIN]" with your website's domain name, _without_ a trailing slash. For now, you should use "http://localhost:4000", since this is the server we'll use for development.

You'll also see I've omitted a name and description above. Be sure to enter your own inside of the quotation marks. It's also worth noting that you do not need to surround a string with quotation marks unless it contains specific characters, like the colon (":") in the URL.

#### _includes

If you're familiar with the idea of "template partials" (or Wordpress's `get_header()` command), the includes directory serves the same purpose. It allows theme builders to have common files, like a header or footer, that are shared between posts and pages. For now, just create a folder in your website's root called `_includes`. Note the underscore at the beginning of the folder's name- this is important. Files and folders with underscores prepending the name will not be copied to the final, generated website.

#### _layouts

Also used in themes is a folder called `_layouts`. This stores all of your posts' layout files. For example, on my website, I have several layouts. Most blog posts use a layout called `post`, containing the text content of each post, share buttons, and Disqus comments. Other pages use a variation of the posts layout, called `posts-no-comments`, that omits the comments and share buttons. I also have separate layouts for my [portfolio](http://www.andrewmunsell.com/work) as well as full width content pages.

For now, just create a folder called `_layouts`. We'll populate this folder later with the theme we build.

#### _posts

Finally, create a folder called `_posts`. This will contain the source Markdown (or HTML/Textile) files for all of your blog posts. If you do not wish to create a blog, you do not have to create this folder.

Once all of this is done, your website's folder should look like the following.

![Folder structure](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/02.png)

> _Folder structure_

If so, you can now go back to your Terminal or Command Prompt session and type the command `jekyll`. Once the command completes, you should see a "successful" message that states your website is located within the `_site` directory.

![Jekyll command results](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/03.png)

> _Jekyll command results_

Of course, no folder will actually be created because we haven't added any real content yet.

### Adding Content

All pages and blog posts in a Jekyll site are simple text files that have content processors associated wiht them. In Jekyll, all pages are processed and then copied into the same location they started at relative to the website's root. That means if you have a `/index.md` file in your website's root folder, it will be processed and copied into `_site/index.html`. Similarly, a page under `about/index.html` will ultimately be processed and copied to `_site/about/index.html`. This allows you to create static pages where your want on your website.

To demonstrate this, create a file called `index.md`. This file should be located in the website's root alongside `_config.yml`. Notice we also do _not_ have a prepended underscore since we do want this file processed and copied to the final generated site.

Add some content into the file. You can either use your own, or copy and paste the example Markdown below.
    
    
    # Hello World
    
    Proin eleifend libero accumsan felis luctus nec consectetur purus commodo. \
    Phasellus sodales est nec massa imperdiet commodo. Maecenas risus nulla, pl\
    acerat vel vestibulum vel, dapibus quis libero.
    
    Donec libero libero, bibendum non condimentum ac, ullamcorper at sapien. Du\
    is feugiat urna vel justo cursus facilisis. Vivamus ligula dui, convallis a\
     varius vitae, facilisis eget magna.
    

Before you save this and generate the site, you also need to add one thing to the beginning of the file called "**front matter**." Front matter is a mini-configuration block that tells Jekyll about the page, including its title, layout, and other information. Front matter is placed inside of two sets of three dashes, like the following:
    
    
    ---
    title: Hello, World!
    ---
    

Place the above front matter block before your Markdown text inside of the `index.md` file.

The front matter is important, as Jekyll will only process files that begin with the front matter block.

Once you've done this, go back to the command line and run `jekyll` again. You'll notice that this time, a `_site` folder was created with a single file: `index.html`. Open the `index.html` file in your browser and you'll see the Markdown was processed into HTML and copied to the appropriate file. Remember, this `_site` folder is ultimately what you deploy on your web server.

### Using Auto-Generate and the Jekyll Server

Typing `jekyll` every time you make a change is time consuming. Fortunately, Jekyll has a method of auto-generating the website every time a file changes. We also want to run a local web server so that we can type `http://localhost:4000` in your web browser to see the website. These two options are turned on by the command line switches, `\--auto` and `\--server`, respectively. To activate both, use the command `jekyll --auto --server` in your command line.

If you did everything right, go ahead and open a browser and navigate to `http://localhost:4000` and you should see the single `index.html` page you created early.

To test the auto-regeneration, go back into your text editor and make some changes to `index.md`. After you save the file and refresh your browser, you should see the changes you made without having to type `jekyll` into the command line again.

### Building the Theme

Now that you understand Jekyll's content processor, we can build a theme for our website. While you can always follow along to the letter, those with HTML and CSS skills may want to consider creating their website design from scratch for a challenge.

#### Download Bootstrap

To start, head to the [Twitter Bootstrap](http://getbootstrap.com/) page and download the framework. If you'd like to optimize your website a little further, you may also want to consider building a [custom Bootstrap package](http://twitter.github.com/bootstrap/customize.html) and removing the elements you do not need. In particular, you may want to consider unchecking the "Icons" box under the Base CSS header if you will be using an icon font like [Font Awesome](http://fortawesome.github.com/Font-Awesome/), [Elusive](http://aristath.github.com/elusive-iconfont/), or [Icomoon](http://icomoon.io/).

Once you've downloaded the files, place them into the root directory of your website. Your directory should now have the following in it:

![Folder structure](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/04.png)

> _Folder structure_

#### Creating a Layout

Remember the `_layouts` folder we created at the beginning? This is where it's put to use. Create a new file in the `_layouts` folder called `default.html`. This will be the default layout we use on all posts and pages and will contain the header, menu, and footer of all pages.

In the `default.html` file, place the following content.
    
    
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <title>{{ site.name }}</title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta name="description" content="{{ site.description }}">
    
        <link href="/css/bootstrap.css" rel="stylesheet">
        <style>
          body {
            padding-top: 60px;
          }
        </style>
        <link href="/css/bootstrap-responsive.css" rel="stylesheet">
    
        <!-- HTML5 shim, for IE6-8 support of HTML5 elements -->
        <!--[if lt IE 9]>
          <script src="http://html5shim.googlecode.com/svn/trunk/html5.js"></sc\
    ript>
        <![endif]-->
      </head>
    
      <body>
    
        <div class="navbar navbar-inverse navbar-fixed-top">
          <div class="navbar-inner">
            <div class="container">
              <a class="btn btn-navbar" data-toggle="collapse" data-target=".na\
    v-collapse">
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
              </a>
              <a class="brand" href="#">{{ site.name }}</a>
              <div class="nav-collapse collapse">
                <ul class="nav">
                  <li class="active"><a href="/">Home</a></li>
                </ul>
              </div>
            </div>
          </div>
        </div>
    
        <div class="container">
    
          {{ content }}
    
        </div>
    
      </body>
    </html>
    

Jekyll uses the Liquid Template System built by Shopify. You'll notice a few weird tags in the HTML markup above composed of two sets of curly braces. If you've ever used Handlebars, Mustache.js, or similar "mustache" template libraries, Liquid will be familiar.

If you want to output a variable, you surround the variable's name with two "mustaches," or curly braces. For example, to output the website's name, you'd write `{{ site.name }}` in the layout as shown above.

Jekyll has three main "global" variables that are always available for Liquid templates to use: `site`, `page`, and `content`. There's also `paginator`, but we'll use that one later.

The `site` variable corresponds to the configuration file (`_config.yml`) values. Because we placed a field called `name` in the `_config.yml` file, it is accessible through `site.name`. The same is true with each page's front matter. If you would like to output a page's title, you would use `{{ page.title }}`, because the name of the field in the page's front matter is `title`.

If you go back to your web browser, you'll see nothing has changed. This is because, while we've created a layout, we haven't specified `index.md` should _use_ this new layout. Go ahead and open `index.md` and add the following line to the front matter of the page:
    
    
    layout: default
    

The name of the layout is simply the file name of the layout inside of the `_layouts` folder, minus the extension. In this case, `default.html` is referenced by "default". If you refresh, your site should look like the following.

![A Basic Theme](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/05.png)

> _A Basic Theme_

#### Using Includes

To demonstrate Liquid's file include system, we'll separate out the header, footer, and create a sidebar for the website.

Open the `default.html` file in the `_layouts` directory. Take everything from the first `<!DOCTYPE html>` tag to the `<div class="container">` just before the `{{ content }}` tag, and move it into a new file under the `_includes` directory called `header.html`.

To create a footer include, take all of the HTML after `{{ content }}` to the end of the file and paste it into a new file called `footer.html` under the `_includes` directory.

You should be left with three files in two directories- `header.html` and `footer.html` in `_includes`, and `default.html` in `_layouts`. The files should have the following contents:

##### _layouts/default.html
    
    
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <title>{{ site.name }}</title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta name="description" content="{{ site.description }}">
    
        <link href="/css/bootstrap.css" rel="stylesheet">
        <style>
          body {
            padding-top: 60px;
          }
        </style>
        <link href="/css/bootstrap-responsive.css" rel="stylesheet">
    
        <!-- HTML5 shim, for IE6-8 support of HTML5 elements -->
        <!--[if lt IE 9]>
          <script src="http://html5shim.googlecode.com/svn/trunk/html5.js"></sc\
    ript>
        <![endif]-->
      </head>
    
      <body>
    
        <div class="navbar navbar-inverse navbar-fixed-top">
          <div class="navbar-inner">
            <div class="container">
              <a class="btn btn-navbar" data-toggle="collapse" data-target=".na\
    v-collapse">
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
              </a>
              <a class="brand" href="#">{{ site.name }}</a>
              <div class="nav-collapse collapse">
                <ul class="nav">
                  <li class="active"><a href="/">Home</a></li>
                </ul>
              </div>
            </div>
          </div>
        </div>
    
        <div class="container">
    
    
    
      </div>
    
      </body>
    </html>
    

If you refresh your browser, you'll notice that the page has reverted to its pre-styled state. This is because the layout (`default.html`) only says, "output the content"- it makes no reference to the new includes.

To correct this, above `{{ content }}`, add the following statement.

Then, below the content tag, add the same for the footer.

There are pretty easy to understand- they simply include the header and footer into the default layout. The include tags essentially tell the Liquid Template System to copy and paste the content of the file referenced into your layout. Once you refresh your browser again the page should be back to the styled Bootstrap page.

Now that you understand the purpose of the `include` tag in Liquid, we'll to build a sidebar for the website. For now, we can just put an "about" box in the sidebar- we will go through how to display the most recent posts later on once the blog element of the website is finished.

As you can probably guess, you'll need a new file in the `_includes` directory. Name it what you wish, but I'd suggest `sidebar.html` for clarity. Add some content into this file, such as a header and an about blurb. I put the following in mine:
    
    
    <h3>About Me</h3>
    
    <p>Donec libero libero, bibendum non condimentum ac, ullamcorper at sapien.\
     Duis feugiat urna vel justo cursus facilisis. Vivamus ligula dui, convalli\
    s a varius vitae, facilisis eget magna.</p>
    

With Twitter Bootstrap, it's easy to build a sidebar. If you've ever used Bootstrap before, you'll know that layouts are composed of rows and columns. For example, to create a sidebar we could use the following code.
    
    
    <div class="row-fluid">
      <div class="span8">
        <h1>Home Page</h1>
    
        <p>Content will go here</p>
      </div>
      <div class="span4">
        <h3>Sidebar</h3>
    
        <p>Sidebar content goes here.</p>
      </div>
    </div>
    

For those unfamiliar with Bootstrap, the layout is composed of 12 columns total. We want the content to be wider than the sidebar, so it "spans" 8 columns. The sidebar, as you can tell by the `span4` class, will span 4 columns, for a total of 12 columns in the row.

To translate this to our Bootstrap site, we will have to create the row for the content and the sidebar to sit in. Inside of the `default.html` file in the `_layouts` folder, wrap the `{{ content }}` tag with two `div` tags- one `.row-fluid`, one `.span8`. Next, add another column with the class `span4` to contain the sidebar. Inside this column, use the tag to include `sidebar.html`. Your `default.html` file should now look like this:
    
    
    <div class="row-fluid">
      <div class="span8">
        {{ content }}
      </div>
      <div class="span4">
        {% include sidebar.html %}
      </div>
    </div>
    

If you refresh your browser, you'll see that the layout has now turned into a two column format with the sidebar content you wrote earlier.

### Setting Up Blog Posts

Now that you have a grasp of partials, static pages, and Jekyll's basics, let's move onto transforming the website you've built into a blog. In this tutorial, I will be going over how to build a blog using pure Jekyll. There are alternatives, including [Octopress](http://octopress.org/), that make the blogging experience a little bit easier (it comes with some nice plugins and such, but nothing we can't recreate on our own), but the purpose of this tutorial is to teach you how Jekyll works. If you would like to read more about Octopress and what it offers, feel free to visit their website.

Anyhow, building a blog with Jekyll is actually quite easy. It doesn't require too much work to display posts because Jekyll was originally conceived with blogging in mind. At a high level, setting up Jekyll's blogging system is very similar to "the loop" in Wordpress. If you've ever built a Wordpress theme or know the basics of how Wordpress works, you'll be at home with Jekyll.

For those unfamiliar with the concept of a "post loop," it is essentially a way of asking a blogging platform to return a list of posts. In most cases, it will be posts 1-10, after which they will overflow onto the second page and so on and so forth. In this loop, we iterate over each post "object" and spit out HTML for each post, which means the code is the same to display 1, 10, or even a hundred posts.

#### Post Dummy Content

Before we write a post loop, we will need some dummy content so we can see the results.

The `_posts` folder contains all of the blog posts' content and metadata. Jekyll is pretty smart, so we can also mix Markdown, HTML, and other formats in this folder. For example, the more complicated articles on my website (such as [Moore's Law of the Mind](http://andrewmunsell.com/blog/moores-law-of-the-mind)) are written in `.html` files, whereas regular posts are simply Markdown.

To create a blog post, drop a Markdown file into the `_posts` folder. However, there is a specific naming structure for posts and the files _must_ be named in this way:

` YYYY-MM-DD-[POST SLUG].[FORMAT] `

For example, if you wrote a blog post on March 8th, 2013 in the Markdown format and wanted a post "slug" of "best-spring-recipies", you'd name your file `2013-03-08-best-spring-recipies.md`.

If you don't know this already, the term "[post slug"](https://en.wikipedia.org/wiki/Clean_URL#Slug) refers to a URL-friendly format for the post's name. This means, no spaces, weird characters, and anything that isn't normally allowed in a URL. Standard conventions include keeping all of the letters lower case, using dashes ("-") instead of spaces, and using a relatively short slug.

Anyhow, create a couple of blog posts using the file name format above. If you need some content and don't want to create it on your own, feel free to copy and paste the following into several files.
    
    
    ---
    title: Lorem Ipsum Dolor Sit Amet
    layout: default
    ---
    
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse elemen\
    tum leo non felis porttitor vulputate. Nulla ipsum quam, auctor ut hendreri\
    t quis, tincidunt eu metus. Quisque ipsum tellus, semper a tempus quis, int\
    erdum vel magna. Cras a nisl diam, in accumsan augue. Pellentesque varius n\
    ibh eu diam tempor rhoncus.
    
    ## Pellentesque sollicitudin
    
    Erat pellentesque ornare gravida, ipsum est luctus neque, eget condimentum \
    urna arcu sit amet felis. Duis nisl augue, scelerisque quis iaculis non, co\
    mmodo a tellus. Class aptent taciti sociosqu ad litora torquent per conubia\
     nostra, per inceptos himenaeos. Etiam tincidunt porttitor nibh at semper. 
    
    
    
    ---
    title: Consectetur Elit
    layout: default
    ---
    
    Sed id lacus eu urna ullamcorper mattis. Etiam ut nunc erat. Sed et velit a\
    c nisi mattis mollis tempus id nulla. In varius fermentum posuere. Vivamus \
    suscipit accumsan arcu ac ullamcorper. Aliquam adipiscing, ante non eleifen\
    d blandit, nunc diam vulputate augue, eu convallis lorem lacus in lacus. Cu\
    rabitur ultricies ultrices diam, vel tincidunt dui rhoncus a. Vivamus at sa\
    pien in turpis consequat pharetra sit amet quis elit.
    
    ## Nam vel justo ut nisl rutrum lobortis
    
    Donec at arcu nisi, quis euismod enim. Donec viverra felis vitae elit ornar\
    e porta. Vivamus ullamcorper consectetur odio, vitae imperdiet mi laoreet v\
    itae. Fusce ante ligula, cursus eget volutpat vel, pretium eget tellus.
    

In case you're wondering what the posts above say, its [lorem ipsum](https://en.wikipedia.org/wiki/Lorem_ipsum), generated by [Lipsum.com](http://lipsum.com). Basically, it is placeholder text. You can generate some yourself if you'd like and stick it into blog posts in you need more content, but for now, two posts will be plenty.

Another important thing to notice is the front matter of the two posts I embedded above. You'll see "title" and "layout" fields. Those two are the only fields you _need_ in front matter for blog posts, since the date is embedded in the file name.

#### Introduction to Post Loops

Now that you've got some dummy content, we can now create a way to _show_ the posts. Before we get into the main post loop, we'll create a recent posts section in the sidebar. This will allow you to see the basic structure of the post loop and basic methods for displaying content and controlling the posts displayed.

Go ahead and open the `sidebar.html` file in the `_includes` directory. Under the "About Me" paragraph, go ahead and add another header with the text "Recent Posts." Under _that_ header, paste the following code.
    
    
    <ul>
      {% for post in site.posts limit: 5 %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
    

You'll see that the post loop has two main parts- the loop itself, and code to be repeated for each item.

The line containing `{% for post in site.posts limit: 5 %}` signifies the beginning of the post loop. Notice the corresponding `{% endfor %}` at the end of the code block, which tells Jekyll where the end of the loop is. Essentially, the code says to "take everything in between 'for' and 'endfor', and repeat it for the 5 most recent posts."

This means, if we have five or more recent posts, five list elements will be generated. You can also see two curly braces with `post.title` in between them. If you recall the default template, you will remember that there was a `{{ content }}` tag in the layout and that the double "mustaches" resulted in a variable being displayed. In this case, we want to take the `url` property of each post and output it in an anchor, as well as display the `title` of the post.

You may be wondering why we access the `title` and `url` properties of the `post` variable rather than something else, like the global `page`. Remember, there is also the `site` and `page` globals that you can access. The reason we use `post` over `page` is because of the way the `for` loop is used. The `for` loop indicates that **for** every **post in** the **site**, up to a **limit** of 5," set the `post` variable and use it to output the following code. For those that have used another programming language before, such as Java, PHP, or even Javascript, the Liquid Template System's for loop is a similar concept.

If you'd like, you can change the number after `limit:` to a higher or lower number to customize how many recent posts are listed.

![Recent posts in the sidebar](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/06.png)

> _Recent posts in the sidebar_

Now that you've got a grasp on the basics of writing a post loop, we can take it further and write the _main_ loop. Because we want to display the blog posts on the home page of the website, we're going to use the `index.html` page. But right now, because we have an `index.md` page that is processed _into_ `index.html`, we have to delete it.

Go ahead and delete `index.md` in the website's root directory, and create a new, blank `index.html` page. As with before, create a front matter block with the layout specified as "default." You can try doing this yourself since you already have all of the knowledge needed, but the complete solution is also below.

If you'd like an even bigger challenge, try creating the for loop as well. You don't need to put anything in the loop yet, but try writing the actual for loop itself so that Jekyll will loop through `site.posts` up to a limit of 10 posts.

You can see the completed code below.
    
    
    ---
    layout: default
    ---
    
    {% for post in site.posts limit: 10 %}
    
    {% endfor %}
    

To test the loop out, you can always put something in between the `for` and `endfor`. This can be any text or HTML you want, including something as simple as `<p>Hello world.</p>`. If you do use this snippet to test your loop and you refresh your browser, you should see two "Hello world" paragraphs printed out, assuming you have two posts.

Once you've confirmed your post loop works, we can now begin to write the code that displays the post titles and dates. To do so, we'll use the following HTML.
    
    
    <div class="row-fluid">
      <div class="span12">
        <h2>{{ post.title }}</h2>
        <h4>{{ post.date | date_to_long_string }}</h4>
        <p>
          <a href="{{ post.url }}">Read Post</a>
        </p>
      </div>
    </div>
    

You'll probably recognize the `{{ post.title }}` tag, but inside of the `{{ post.date }}` tag there's a new bit of template code we haven't seen before: filters.

Filters are extremely useful bits of Ruby code that transform one value into something else, then spit it out again. This can be repeated as many times as you wish, so one filter can provide input to another and so on and so forth. One example of this would be the following template snippet, which truncates a title to ten words and then capitalizes each word.
    
    
    {{ post.title | truncatewords: 10 | capitalize }}
    

In our case, we are taking the post's date and using a date filter to transform it into a human readable date string. We can also output the date in a custom format by using the date filter and supplying a date format string.

The above code transforms a date into the format "MM-DD-YYYY." A complete reference of the date string formats can be found [in Liquid's documentation](http://liquid.rubyforge.org/classes/Liquid/StandardFilters.html#M000012).

Once you've copied and pasted the code for the post listing in between the `for` and `endfor`, you can refresh your browser. You should see something like the following.

![Result of post loop](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/07.png)

> _Result of post loop_

### Post Content Pages

Go ahead and click on one of the "Read Post" link under one of the posts on the home page. You'll notice, that out of the box, the post will open and the content will be displayed just fine- with your sidebar and all.

The one issue is, there is no title on the page. That is because our "default" layout is a generic page- it simply displays the content given to it. For the post content pages, it'd be idea to have a separate template so that we can add a comment system (like [Disqus](http://disqus.com/) or [LiveFyre](http://livefyre.com)) or social share buttons.

Go ahead and create a new layout in the `_layouts` folder called `post.html`. Inside, you can copy and paste the contents of `default.html` and add a `h1` element with the Liquid tag to display `post.title`. The full code of the `post.html` file can be seen below if you need a hint or if you'd like to check your solution. In my code below, I've also added another paragraph tag with the post's date.
    
    
    {% include header.html %}
    
    <div class="row-fluid">
      <div class="span8">
        <h1>{{ page.title }}</h1>
        <p class="muted">{{ page.date | date_to_long_string }}</p>
    
        {{ content }}
      </div>
      <div class="span4">
        {% include sidebar.html %}
      </div>
    </div>
    
    {% include footer.html %}
    

Refreshing the content page you visited earlier in your browser should now yield a nicely formatted post with the date below the title.

### Pagination

Though the site is near complete, there's still a few things left to do. One of them is paginating the home page's list of blog posts. If you've added more than ten blog items to the `_posts` directory, you'll notice that the front page will only display the top ten (or however many posts you set your loop to display).

To fix this, we need to use the final global variable in Jekyll- `paginator`.

The paginator will only work on your home page (the `index.html` file), so there's no way to use the paginator to build multi-page posts without a plugin. If you open your `_config.yml` file, you'll see the `paginate: 10` value. This tells the paginator to break pages at ten posts. You can change this value if you wish, or even lower to one or two for testing if you do not want to spend time adding more dummy posts. If you change the configuration file, you will also need to stop and restart the Jekyll server for the `_config.yml` file to be reloaded. This can be done by pressing Control+C on the command line.

The paginator uses a different style of post loop and will require a small change in your `index.html` page. Open `index.html` and look at your loop. Right now, we are looping through `site.posts`, which is a collection of _all_ your blog posts. The paginator has its own collection that automatically truncates to `N` posts, with `N` being the value in your `_config.yml` file. The only change you'll have to make is changing `site.posts` to `paginator.posts` and removing the `limit: 10`. The reason we don't need this limit anymore is because the paginator automatically limits the number of posts for us to the value in the configuration file.

Before you refresh the page in your browser, we still have to add next and previous page links. If you look, you can see that Jekyll has created a `/page2` directory in your generated website folder (`_site`) if you have more than the number of posts per single page.

![Generated website with a Second Page](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/08.png)

> _Generated website with a Second Page_

The `paginator` global variable has a couple of useful properties. `previous_page` and `next_page` are the numbers of the previous and next pages, respectfully, if they exist. On page one, there will be no previous page. `total_pages` contains, as indicated, the total number of pages needed to display all blog posts. If you have 26 blog posts and 10 posts per page, `pagiantor.total_pages` would be 3. Finally, `page` is the numeric representation of the current page.

For our buttons, we can use a modified version of the code [suggested by Jekyll's developer](https://github.com/mojombo/jekyll/wiki/Pagination). Just place the following in `index.html` under the post loop.
    
    
    <div class="row-fluid">
      <div class="span12">
        <div class="pagination">
          <ul>
            {% if paginator.previous_page %}
              {% if paginator.previous_page == 1 %}
              <li><a href="/">Prev</a></li>
              {% else %}
              <li><a href="/page{{ paginator.previous_page }}">Prev</a></li>
              {% endif %}
            {% else %}
            <li><span class="disabled">Prev</span></li>
            {% endif %}
            {% if paginator.page == 1 %}
            <li><span class="active">1</span></li>
            {% else %}
            <li><a href="/">1</a></li>
            {% endif %}
            {% for count in (2..paginator.total_pages) %}
              {% if count == paginator.page %}
              <li><span class="active">{{ count }}</span></li>
              {% else %}
              <li><a href="/page{{ count }}">{{ count }}</a></li>
              {% endif %}
            {% endfor %}
            {% if paginator.next_page %}
            <li><a href="/page{{ paginator.next_page }}">Next</a></li>
            {% else %}
            <li><span class="disabled">Next</span></li>
            {% endif %}
          </ul>
        </div>
      </div>
    </div>
    

It's a lot of code to go through, but the majority of it is simply checking to see whether a next or previous page exists, and if so, serve the correct URL. After all, there is no `/page1` directory, so if the previous page is the first, we must link directly to the home page instead of `/page1`.

The `for` loop is slightly different, however. Essentially, instead of looping through a collection of objects, we assign the variable `count` a number from 2 to `paginator.total_pages`.

### Challenge

Now that you've gotten a complete Jekyll website built and know how to use the blogging features, why don't we put them to the test with a challenge to see what you've remembered?

For this challenge, I want you to create an about page for yourself. This is similar to the content in the "About Me" section of the sidebar, but expanded into a full page. Create a page that will ultimately be accessible at `http://localhost:4000/about/`. Assume the default page for the web server is `index.html`.

#### Solution

Here's a possible solution to the challenge. The contents of the following is placed under `about/index.md` relative to your website's root directory so that it will ultimately be copied to `_site/about/index.html`. The content you may have used will be different and you may have actually used an HTML file versus a Markdown file- here, I've just used Lorem Ipsum.
    
    
    ---
    title: About Me
    layout: default
    ---
    
    # About Me
    
    Aliquam et quam non tellus lacinia adipiscing. Vivamus commodo, sem vitae p\
    retium accumsan, arcu lacus dictum orci, sed ullamcorper risus leo ut ligul\
    a. Nulla luctus tristique laoreet. Donec placerat arcu a leo ullamcorper vi\
    tae dictum tortor rhoncus. In pulvinar facilisis libero, nec dignissim orci\
     volutpat ac. Etiam eget nunc lacus.
    
    Integer non porttitor nisl. Mauris elit dolor, pretium euismod vehicula id,\
     facilisis a orci. Phasellus at magna quam, vel tincidunt quam. Sed a moles\
    tie purus. Mauris fringilla pretium lorem ut eleifend. Curabitur rhoncus, a\
    rcu eu blandit gravida, dolor tellus consequat tellus, at tincidunt risus f\
    elis id justo. Sed ac erat ultrices ipsum tempus suscipit id vitae nunc. In\
    teger sit amet sapien quis lectus tempor pharetra ut at velit. Quisque semp\
    er, libero a pellentesque sollicitudin, massa libero euismod justo, porta m\
    olestie erat dui vel tellus. Ut lacus turpis, dapibus ut mollis id, aliquet\
     in leo. Curabitur sollicitudin mauris sollicitudin dolor aliquam tristique\
    . Ut congue sem vitae justo congue consequat. Integer mauris nisi, blandit \
    in facilisis sed, lacinia quis lacus. Vestibulum sem enim, ullamcorper a po\
    rttitor vel, laoreet quis diam.
    

You should see something like the following when you navigate to `http://localhost:4000/about/`.

![Completed About Page](https://d1nflukuugqh7q.cloudfront.net/courses/jekyll-by-example/tutorial/img/09.png)

> _Completed About Page_
