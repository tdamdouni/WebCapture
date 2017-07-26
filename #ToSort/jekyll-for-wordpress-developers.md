# Jekyll For WordPress Developers

_Captured: 2017-04-21 at 19:23 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/04/jekyll-wordpress-developers/)_

  * [3 Comments](https://www.smashingmagazine.com/2017/04/jekyll-wordpress-developers/)

Meet the new [Sketch Handbook](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1), our brand **new Smashing book** that will help you master all the tricky, advanced facets of Sketch. Filled with **practical examples and tutorials in 12 chapters**, the book will help you become more proficient in your work. [Get the book now ->](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1)

Jekyll is gaining popularity as a lightweight alternative to WordPress. It often gets pigeonholed as a tool developers use to build their personal blog. That's just the tip of the iceberg -- it's capable of so much more!

In this article, we'll take on the role of a web developer building a [website for a fictional law firm](https://grey-grouse.cloudvent.net/). WordPress is an obvious choice for a website like this, but is it the only tool we should consider? Let's look at a completely different way of building a website, using Jekyll.

![Jekyll For WordPress Developers](https://www.smashingmagazine.com/wp-content/uploads/2017/04/Jekyll-for-wp-developers-opt.png)

[Jekyll](http://jekyllrb.com/) is a static website generator. Instead of software and a database being installed on our server, a Jekyll website is simply a directory of files on our computer. When we run Jekyll on that directory, it generates a static website, which we upload to a hosting provider.

We need to consider a number of tradeoffs when deciding whether Jekyll is right for a project.

  * **Less complexity**  
A Jekyll website is essentially a static website with a templating language. It has fewer components to create and maintain. On the server, we only need a web server capable of serving files.
  * **Speed**  
When visitors view pages on Jekyll sites, the server returns existing files _without any extra processing_. This is much faster than WordPress, which generates pages dynamically at request time. Note: WordPress Caching plugins can eliminate this performance gap.
  * **Stability**  
WordPress has more components working together to generate pages for visitors. If a component fails, visitors may not be able to view the website. Much less can go wrong when a web server is serving only files.
  * **Security**  
WordPress does a lot to mitigate security risks such as CSRF, XSS, or SQL injection attacks however it relies on you always having the latest updates. Statics sites eliminate this problem because there's no dynamic data storage a hacker can exploit.
  * **Source-controlled**  
A Jekyll website is a directory of files, so we can store the entire website in a Git repository. Working with a repository gives us [many benefits](https://www.atlassian.com/git/tutorials/why-git/git-for-developers) (although [VersionPress](https://versionpress.net/) is in development and enables this workflow for WordPress).
  * **No GUI**  
A client can sign up to WordPress.com, choose a theme and set up a basic website by themselves. Jekyll is a command-line tool, which overwhelms most non-technical users. There are third-party GUIs for Jekyll, including [CloudCannon](https://cloudcannon.com/) (disclaimer: I'm the cofounder), [Forestry](https://forestry.io/), [Jekyll Admin](https://github.com/jekyll/jekyll-admin), [Netlify CMS](https://github.com/netlify/netlify-cms), [Prose](http://prose.io/) and [Siteleaf](https://www.siteleaf.com/). However, these need to be set up by the developer before being handed off to the client.
  * **Build time**  
In our situation, this isn't a problem because the website will build in under a second. However, a larger website with 10,000 to 100,000 posts could take minutes to build. This is frustrating when we're developing because we have to wait for the website to build before previewing it in the browser.
  * **Themes**  
Jekyll has some themes available, but it's nothing compared to the thousands of themes available for WordPress.
  * **Extensibility**  
If we need to add custom functionality to our WordPress website, we can write our own PHP. We can create custom Ruby plugins for Jekyll, however, these run at build time rather than request time.
  * **Support**  
WordPress has a huge community of experts and other resources to help. Jekyll has similar resources but on a smaller scale.

Jekyll is a great tool for largely informational websites, like this project. If the project is more of an application, we could add dynamic elements using JavaScript, but at some point we would probably need a back end like WordPress'.

WordPress and Jekyll take different approaches to building a website yet share a lot of functionality. Let's get started building our Jekyll website.

A typical development environment for WordPress requires installation of Apache or NGINX, PHP and MySQL. Then, we would install WordPress and configure the web server.

For Jekyll, we need to make sure we have Ruby installed (sometimes this is harder than it sounds). Then we install the Jekyll gem:
    
    
    gem install jekyll

If you're on macOS make sure you have Xcode developer installed first.
    
    
    xcode-select --install

Running a WordPress site usually consists of starting the database and web server.

In Jekyll, we navigate to our site files (an empty directory at this point) in the terminal and run:
    
    
    jekyll serve

This starts a local web server on port `4000` and rebuilds the site whenever a file changes.

It's time to create our first page. Let's start with the home page. Pages are for standalone content without an associated date. WordPress stores page content in the database.

In Jekyll, pages are HTML files. We'll start with pure HTML and then add Jekyll features as they're needed. Here's `index.html` in its current state:
    
    
    <html>
      <head>
        <meta charset="utf-8">
        <link rel="stylesheet" href="/css/main.css">
      </head>
      <body>
        <div class="container">
          <h1><a href="/">Justice</a></h1>
          <nav>
            <ul>
              <li><a href="/about/">About</a></li>
              <li><a href="/services/">Services</a></li>
              <li><a href="/contact/">Contact</a></li>
              <li><a href="/advice/">Advice</a></li>
            </ul>
          </nav>
        </div>
    
        <section class="main">
          <div class="container">
            <p>Justice Law is professional representation. Practicing for over 50 years, our team have the knowledge and skills to get you results.</p>
    
            <blockquote class="testimonial">
              <p class="testimonial-message">Justice Law are the best of the best. Being local, they care about people and have strong ties to the community.</p>
              <p class="testimonial-author">
                <img src="/images/peter.jpeg" alt="Photo of Peter Rottenburg"> Peter Rottenburg
              </p>
            </blockquote>
          </div>
        </section>
    
        <footer>
          <p class="copyright">
            &copy; 2016
          </p>
        </footer>
      </body>
    </html>
    

In WordPress, we can write PHP to do almost anything. Jekyll takes a different approach. Instead of providing a full programming language, it uses a templating language named [Liquid](http://shopify.github.io/liquid/). (WordPress has templating languages, too, such as [Timber](https://upstatement.com/timber/).)

The footer of `index.html` contains a copyright notice with a year:
    
    
    <p class="copyright">
      &copy; 2016
    </p>
    

We're unlikely to remember to update this every year, so let's use Liquid to output the current year:
    
    
    <p class="copyright">
      &copy; {{ site.time | date: "%Y" }}
    </p>
    

We're building a static website in Jekyll, so this date won't change until we rebuild the website. If we wanted the date to change without having to rebuild the website, we could use JavaScript.

The bulk of the HTML in `index.html` is for setting up the overall layout and won't change between pages. This repetition will lead to a lot of maintenance, so let's reduce it.

Includes were one of the first things I learned in PHP. Using includes, we can put the header and footer content in different files, then include the same content on multiple pages.

Jekyll has exactly the same feature. Includes are stored in a folder named `_includes`. We use Liquid to include them in `index.html`:
    
    
    {% include header.html %}
    <p>Justice Law is professional representation. Practicing for over 50 years, our team have the knowledge and skills to get you results.</p>
    
    <blockquote class="testimonial">
      <p class="testimonial-message">Justice Law are the best of the best. Being local, they care about people and have strong ties to the community.</p>
      <p class="testimonial-author">
        <img src="/images/peter.jpeg" alt="Photo of Peter Rottenburg"> Peter Rottenburg
      </p>
    </blockquote>
    {% include footer.html %}
    

Includes reduce some of the repetition, but we still have them on each page. WordPress solves this problem with template files that separate a website's structure from its content.

The Jekyll equivalent to template files is layouts. Layouts are HTML files with a placeholder for content. They are stored in the `_layouts` directory. We'll create `_layouts/default.html` to contain a basic HTML layout:
    
    
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <link rel="stylesheet" href="/css/main.css">
      </head>
      <body>
        <div class="container">
          <h1><a href="/">Justice</a></h1>
          <nav>
            <ul>
              <li><a href="/about/">About</a></li>
              <li><a href="/services/">Services</a></li>
              <li><a href="/contact/">Contact</a></li>
              <li><a href="/advice/">Advice</a></li>
            </ul>
          </nav>
        </div>
    
        <section class="main">
          <div class="container">
            {{ content }}
          </div>
        </section>
    
        <footer>
          <p class="copyright">
            &copy; {{ site.time | date: "%Y-%m-%d" }}
          </p>
        </footer>
      </body>
    </html>
    

Then, replace the includes in `index.html` by specifying the layout. We specify the layout using front matter, which is a snippet of [YAML](https://en.wikipedia.org/wiki/YAML) that sits between two triple-dashed lines at the top of a file (more on this soon).
    
    
    ---
    layout: default
    ---
    
    <p>Justice Law is professional representation. Practicing for over 50 years, our team have the knowledge and skills to get you results.</p>
    
    <blockquote class="testimonial">
      <p class="testimonial-message">Justice Law are the best of the best. Being local, they care about people and have strong ties to the community.</p>
      <p class="testimonial-author">
        <img src="/images/peter.jpeg" alt="Photo of Peter Rottenburg"> Peter Rottenburg
      </p>
    </blockquote>
    

Now we can have the same layout on all of our pages.

In WordPress, custom fields allow us to set meta data on a post. We can use them to set SEO tags or to show and hide sections of a page for a particular post.

This concept is called [front matter](https://jekyllrb.com/docs/frontmatter/) in Jekyll. Earlier, we used front matter to set the layout for `index.html`. We can now set our own variables and access them using Liquid. This further reduces repetition on our website.

Let's add multiple testimonials to `index.html`. We could copy and paste the HTML, but once again, that leads to increased maintenance. Instead, let's add the testimonials in front matter and iterate over them with Liquid:
    
    
    ---
    layout: default
    testimonials:
      - message: We use Justice Law in all our endeavours. They offer an unparalleled service when it comes to running a business.
        image: "/images/joice.jpeg"
        name: Joice Carmold
      - message: Justice Law are the best of the best. Being local, they care about people and have strong ties to the community.
        image: "/images/peter.jpeg"
        name: Peter Rottenburg
      - message: Justice Law were everything we could have hoped for when buying our first home. Highly recommended to all.
        image: "/images/gibblesto.jpeg"
        name: D. and G. Gibbleston
    ---
    
    <p>Justice Law is professional representation. Practicing for over 50 years, our team have the knowledge and skills to get you results.</p>
    
    <div class="testimonials">
      {% for testimonial in page.testimonials %}
        <blockquote class="testimonial">
          <p class="testimonial-message">{{ testimonial.message }}</p>
          <p class="testimonial-author">
            <img src="{{ testimonial.image }}" alt="Photo of {{ testimonial.name }}"> {{ testimonial.name }}
          </p>
        </blockquote>
      {% endfor %}
    </div>
    

WordPress stores the HTML content, date and other meta data for posts in the database.

In Jekyll, each post is a static file stored in a `_posts` directory. The file name has the publication date and title for the post -- for example, `_posts/2016-11-11-real-estate-flipping.md`. The source code for a blog post takes this structure:
    
    
    ---
    layout: post
    categories:
      - Property
    ---
    
    Flipping is a term used primarily in the US to describe purchasing a revenue-generating asset and quickly reselling it for profit.
    
    ![House](/images/house.jpeg)
    

We can also use front matter to set categories and tags.

Below the front matter is the body of the post, written in [Markdown](https://en.wikipedia.org/wiki/Markdown). Markdown is a simpler alternative to HTML.

Jekyll allows us to create layouts that inherit from other layouts. You might have noticed this post has a layout of `post`. The `post` layout inherits from the default layout and adds a date and title:
    
    
    ---
    layout: default
    ---
    <h3>{{ page.title }}</h3>
    <p>{{ page.date | date: '%B %d, %Y' }}</p>
    
    {{ content }}
    

Let's create `blog.html` to iterate over the posts and link to them:
    
    
    ---
    layout: default
    ---
    <ul>
      {% for post in site.posts %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
    

In WordPress, custom post types are useful for managing groups of content. For example, you might use custom post types for testimonials, products or real-estate listings.

Jekyll has this feature and calls it [collections](https://jekyllrb.com/docs/collections/).

The `about.html` page shows profiles of staff members. We could define the meta data for the staff (name, image, phone number, bio) in the front matter, but then we could only reference it on that page. In the future, we want to use the same data to display information about authors on blog posts. A collection enables us to refer to staff members anywhere on the website.

Configuration of our website lives in `_config.yml`. Here, we set a new collection:
    
    
    collections:
      staff_members:
        output: false
    

Now we add our staff members. Each staff member is represented in a Markdown file stored in a folder with the collection name; for example, `_staff_members/jane-doe.md`.

We add the meta data in the front matter and the blurb in the body:
    
    
    ---
    name: Jane Doe
    image: "/images/jane.jpeg"
    phone: "1234567"
    ---
    
    Jane has 19 years of experience in law, and specialises in property and business.
    

Similar to posts, we can iterate over the collection in `about.html` to display each staff member:
    
    
    ---
    layout: default
    ---
    <ul>
      {% for member in site.staff_members %}
        <li>
          <div><img src="{{ member.image }}" alt="Staff photo for {{ member.name }}"></div>
          <p>{{ member.name }} - {{ member.phone }}</p>
          <p>{{ member.content | markdownify }}</p>
        </li>
      {% endfor %}
    </ul>
    

WordPress has powerful built-in search and even more powerful search plugins.

Jekyll doesn't have search built in, but there are solutions:

  * client-side search using a JavaScript library such as [Lunr.js](http://lunrjs.com/) ([Jekyll.tips has a tutorial](http://jekyll.tips/jekyll-casts/jekyll-search-using-lunr-js/) on how to set this up);
  * third-party solutions, such as [Algolia](https://blog.algolia.com/instant-search-blog-documentation-jekyll-plugin/) for high-performance search;

Plugins are an appealing part of WordPress. It's easy to load in functionality to get WordPress to do almost anything.

On our Jekyll website, many popular WordPress plugins aren't necessary:

  * [iThemes Security](https://wordpress.org/plugins/better-wp-security/)  
Our Jekyll website is as secure as the web server it's running on.
  * [Backup Guard](https://wordpress.org/plugins/backup/)  
Our Jekyll website will live in a repository that gives us access to the entire history of changes.

Other WordPress plugins have third-party equivalents that we can drop into the website:

Some WordPress plugins can be emulated with core Jekyll. Here's a photo gallery using front matter and Liquid:
    
    
    ---
    layout: default
    images:
      - image_path: /images/bill.jpg
        title: Bill
      - image_path: /images/burt.jpg
        title: Burt
      - image_path: /images/gary.jpg
        title: Gary
      - image_path: /images/tina.jpg
        title: Tina
      - image_path: /images/suzy.jpg
        title: Suzy
    ---
    <ul class="photo-gallery">
      {% for image in page.images %}
        <li><img src="{{ image.image_path }}" alt="{{ image.title }}"/></li>
      {% endfor %}
    </ul>
    

We just need to add our own JavaScript and CSS to complete it.

Jekyll plugins can emulate the functionality of other WordPress plugins. Keep in mind that Jekyll plugins only run while the website is being generated -- they don't add real-time functionality:

One of the major benefits of using a static site generator like Jekyll is the entire site and content can live in Git. At a basic level, Git gives you a history of all the changes on the site. For teams, it opens up all sorts of workflows and approval processes.

GitHub has a fantastic [interactive tutorial](https://try.github.io/) for beginners learning Git.

That covers the nuts and bolts of creating the website. If you're curious to see how an entire Jekyll website fits together, have a look at the [Justice template](https://github.com/CloudCannon/justice-jekyll-template). It's a free MIT-licensed template for Jekyll. The snippets above are based on this template.

The WordPress CMS is built into the platform, so we would need to set up an account for the client.

With our Jekyll website, we'd link our Git repository to one of the Jekyll GUIs mentioned earlier. One of the nice things about this workflow is that clients changes are committed back to the repository. As developers, we can continue to use local workflows even with non-developers updating the website.

Some Jekyll GUIs offer hosting, while others have a way to output to an Amazon S3 bucket or to [GitHub Pages](https://pages.github.com/).

At this point, our Jekyll website is live and editable by the client. If we need to make any changes to the website, we simply push to the repository and it will automatically deploy live.

Now it's your turn. Plenty of resources are available to help you build your first Jekyll website:

  * The [official Jekyll website](https://jekyllrb.com/) is a great place to start with in-depth documentation on all of Jekyll's features.
  * [Jekyll.tips](http://jekyll.tips/) has a video tutorial series covering core Jekyll topics.
  * Have a look at Jekyll templates on GitHub to see how they're put together: [Frisco](https://github.com/CloudCannon/frisco-jekyll-template) for marketing websites, [Scholar](https://github.com/CloudCannon/scholar-jekyll-template) for documentation and [Urban](https://github.com/CloudCannon/urban-jekyll-template) for digital agencies.

If you're migrating, Jekyll has [tools to import posts](https://import.jekyllrb.com/) from WordPress and WordPress.com websites. After importing, you'll need to manually migrate or create the layouts, pages, CSS, JavaScript and other assets for the website.

The beauty of Jekyll is in its simplicity. While WordPress can match many of the features of Jekyll, it often comes at the cost of complexity through extra plugins or infrastructure.

Ultimately, it's about finding the tool that works best for you. I've found Jekyll to be a fast and efficient way to build websites. I encourage you to try it out and post your experience in the comments.

_(al)_
