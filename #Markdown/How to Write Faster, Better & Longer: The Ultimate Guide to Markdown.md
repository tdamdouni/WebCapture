# How to Write Faster, Better & Longer: The Ultimate Guide to Markdown

_Captured: 2016-04-10 at 01:36 from [blog.ghost.org](https://blog.ghost.org/markdown/)_

![Post image](https://blog.ghost.org/content/images/2015/03/markdown-guide-1.jpg)

It's no secret that we're big fans of **Markdown** at [Ghost](https://ghost.org). We pretty much built our entire editor around it!

Once you get the hang of Markdown, it's an incredibly powerful writing tool which will allow you to write rich content for the web far faster than almost any other method. To get to that point, however, there's a little bit of a learning curve. We thought we'd put together an all inclusive guide to make that curve a little bit shorter, and potentially teach you a few super-user tricks to Markdown that you might not have known.

## What is Markdown

**Markdown** is a plain text formatting syntax for writers. It allows you to quickly write structured content for the web, and have it seamlessly converted to clean, structured HTML.

Back in 2004, Apple pundit John Gruber [came up with the idea](http://daringfireball.net/projects/markdown/) after becoming frustrated by writing long, laborious HTML tags to properly format his content. He devised a simple writing system which would make web based documents both easier to write, and easier to read in their raw state.

Here's a quick example of Markdown in action:
    
    
    The *quick* brown fox, jumped **over** the lazy [dog](https://en.wikipedia.org/wiki/Dog).  
    

becomes

The _quick_ brown fox, jumped **over** the lazy [dog](https://en.wikipedia.org/wiki/Dog).

With just a couple of extra characters, Markdown makes rich document formatting quick and beautiful.

## Why do Writers Love Markdown so Much?

"Is that it?" \- I hear you ask - "I could just click on a few formatting buttons in most editors and achieve the same thing!"

Very true! But we're only just getting started. The range of formatting tools has come a very long way since Markdown's inception in 2004, so you'd be forgiven for wondering what advantages it holds over, say, the "Bold" button in Microsoft Word.

While most novice users do indeed find buttons a bit easier to use, advanced writers often swear by Markdown and nothing else. Why? The biggest reason is _writing flow_.

Using a traditional writing user interface you have to pause your writing every few minutes (or sometimes seconds) and reach for the mouse in order to click, highlight, click a formatting button, and then click back to where you left off in order to continue. This process creates a tiresome, disjointed experience when all you want to do is get the words out of your head and onto the screen.

Markdown allows you to keep your fingers firmly planted on the keyboard as you apply formatting on the fly. In short: You never have to stop typing or think about anything else in order to apply your styles.

It might seem like a small detail, but it can have a really big effect. Once you start writing in Markdown, it's really hard to back to the click-fest of the past.

## Basic Markdown Formatting

Ok! You're sold. So how does this work? Let's dive in:

Markdown was designed with the explicit intention to be easily readable by humans. You should find that most of the syntax is pretty simple and intuitive.

Here are the elements you'll use most often:

### Headings
    
    
    # Heading 1
    ## Heading 2
    ### Heading 3
    

Headings in Markdown are any line which is prefixed with a `#` symbol. The number of hashes indicates the level of the heading. One hash is converted to an **h1**, two hashes to an **h2** and so on. There are a total of **6** levels which you can make use of - but for most writing, you'll rarely ever need more than 3.

### Text
    
    
    *italic*
    **bold**
    ***bold-italic***
    [link](http://example.com)
    

If you want to emphasise a word a _little_ bit, wrap it in asterisks. For something that needs **more** emphasis: double asterisks. If you really want to **_drive_** the point home, use triple asterisks. If you prefer, you can also use underscores - they're completely interchangeable.

To add a link: wrap the text which you want to be linked in square brackets, followed by the URL to be linked to in parenthesis. An easy way to remember this one is to think of it like turning a word into a button. `[button]` and `(place to go when the button is clicked)` combine to form a [link](https://blog.ghost.org/markdown/).

### Images
    
    
    ![m'lady](http://i.imgur.com/v8IVDka.jpg)
    

Markdown images have exactly the same formatting as a link, except they're prefixed with a `!`. This time, the text in brackets is the `alt text` \- or the descriptive text for the image.

![m’lady](http://i.imgur.com/v8IVDka.jpg)

In most Markdown editors, you don't have to write this code out. They will provide a tool to allow you to upload an image and insert this code automatically. After that, it will appear in your document.

### Lists
    
    
    * Milk
    * Bread
        * Wholegrain
    * Butter
    
    
    
    1. Tidy the kitchen  
    2. Prepare ingredients  
    3. Cook delicious things  
    

Lists are a formatting nightmare in HTML, but Markdown lists are incredibly easy to manage. For a bullet list, just prefix each like with a `*` \- or `-` or `+` and they will be converted to dots. You can also create nested lists; just indent a line with _4 spaces_ and it will be nested under the line above.

  * Milk
  * Bread 
    * Wholegrain
  * Butter

For numbered lists, do exactly the same thing - but use numbers!

### Quotes
    
    
    > To be or not to be, that is the question.
    

When you want to add a quote in Markdown, it's exactly the same as the formatting which you may already be familiar with from your email app of choice when you reply to someone.

> To be or not to be, that is the question.

Prefixing the line with a `>` converts it into a block-quote.

### How can I remember all the Markdown syntax?!

It seems a little daunting at first, but you might be surprised how naturally it comes to you after a couple of posts written in Markdown. Most good Markdown editors come with a built-in cheat sheet to make it a little easier to learn.

![Ghost’s Markdown cheat-sheet screenshot](http://blog.ghost.org/content/images/2015/03/ghost-markdown-help.jpg)

Here's the one you can pull up from the [Ghost](https://ghost.org) editor at any time if you get stuck.

## Intermediate Markdown Formatting

So you've got the Markdown basics nailed and you want to move on to bigger and better things? Excellent. There's much more we can do.

### Horizontal Rules
    
    
    ---
    

Want to throw-down a quick divider in your article to denote a visual separation between different sections of text? No problem. 3 dashes produce:

A sleek `<hr>` element.

### Code Snippets
    
    
    Some text with an inline `code` snippet  
    
    
    
        .my-link {
            text-decoration: underline;
        }
    

If you're a technical writer, you may want to use example snippets of code to teach your readers a particular syntax (like I'm doing, with this very blog post). Using a single back-tick around a word in a sentence, you can show a quick `code` snippet.

Indenting by **4 spaces** will turn an entire paragraph into a code-block.

### Reference Lists & Titles
    
    
    **The quick brown [fox][1], jumped over the lazy [dog][2].**
    
    [1]: https://en.wikipedia.org/wiki/Fox "Wikipedia: Fox"
    [2]: https://en.wikipedia.org/wiki/Dog "Wikipedia: Dog"
    

If you prefer to use reference lists for your attribution, Markdown can handle this, too. In the above example, all of the links are kept separate in Markdown (so it's easy to read even in its raw format), and then inserted directly as normal links when converted to HTML.

**The quick brown [fox](https://en.wikipedia.org/wiki/Fox), jumped over the lazy [dog](https://en.wikipedia.org/wiki/Dog).**

You'll also notice that we've added a title attribute to the links by adding a `"word"` in quote marks just after the URL. Anywhere you use a URL, you can follow it with a `"title in quotation marks"` to generate a title attribute.
    
    
    [Dog](https://en.wikipedia.org/wiki/Dog "Wikipedia: Dog")
    

### Escaping
    
    
    \*literally\*
    

What if you _literally_ want to type *literally* - without it appearing in italics? Escaping Markdown characters with a back-slash `\` allows you to use any characters which might be getting accidentally converted into HTML.

### Embedding HTML
    
    
    <button class="button-save large">Big Fat Button</button>  
    

Possibly the coolest feature of Markdown is that it also just supports plain old HTML. If you find yourself stuck and unable to do what you want in Markdown - you can simply write in regular HTML and it will work just fine.

In the above example, I know that within this blog's stylesheet is the CSS to style a nice button that with a `class` attribute.

So you can drop in any HTML, sharing button, JavaScript snippet or iFrame you like and it will work on the page just as normal.

## Advanced Markdown

Ok, you want the big guns. Every example so far has been vanilla, normal Markdown. Those code snippets will work absolutely anywhere which supports Markdown syntax.

Now we're going to look at some syntax which is **not standard** to native Markdown. They're extensions of the language. All of these things work in [Ghost](https://ghost.org), but they may not work in other editors.

Here are some nice advanced things you can do with Markdown in Ghost:

### Strike-throughs
    
    
    ~~deleted words~~
    

deleted words

### Highlights
    
    
    ==oooh fancy==
    

oooh fancy

### Automatic Links
    
    
    https://ghost.org  
    

<https://ghost.org>

### Markdown Footnotes
    
    
    The quick brown fox[^1] jumped over the lazy dog[^2].
    
    [^1]: Foxes are red
    [^2]: Dogs are usually not red
    

The quick brown fox[1](https://blog.ghost.org/markdown/) jumped over the lazy dog[2](https://blog.ghost.org/markdown/).

### Syntax Highlighting
    
    
    ```language-javascript
       [...]
    ```
    

Combined with [Prism.js](http://prismjs.com/) in the Ghost theme:
    
    
    // # Notifications API
    // RESTful API for creating notifications
    var Promise            = require('bluebird'),  
        _                  = require('lodash'),
        canThis            = require('../permissions').canThis,
        errors             = require('../errors'),
        utils              = require('./utils'),
    
        // Holds the persistent notifications
        notificationsStore = [],
        // Holds the last used id
        notificationCounter = 0,
        notifications;
    

## Speed up Your Workflow with Markdown Keyboard Shortcuts

Writing Markdown is pretty quick right out of the box, but you can speed it up even further by getting to know the keyboard shortcuts in your editor of choice. These all tend to be a little different, but in Ghost you can access some on-the-fly formatting very easily:

  * Ctrl + B for **Bold**
  * Ctrl + I for _Italic_
  * Ctrl + K for a [link]()
  * Tap Ctrl + H multiple times for the most common **H2** and **H3**

There are lots more included in the _Markdown Help_ overlay in the editor. Regardless of which app you use to write, it's work figuring out the Markdown keyboard shortcuts available to speed up your workflow.

## Converting HTML to Markdown

If you're just getting into Markdown and you've found yourself with a massive back-log of old files which are written in HTML, you might want to convert them to Markdown to make them easier to work with in future.

[Here's a handy tool](http://domchristie.github.io/to-markdown/) by Dom Christie which lets you do exactly that.

## Best Markdown Apps

As well as using Markdown in the Ghost editor, you might also want to use it in the formatting of your day-to-day documents. Lots of people enjoy writing in Markdown and then exporting later to HTML, PDF, or a wide variety of document types.

Here are some of our favourite Markdown editors for Mac, PC, desktop and mobile.

### Mac OSX Markdown Editors

![Mou](http://blog.ghost.org/content/images/2015/03/markdown-osx.jpg)

The Mac is graced with a large selection of Markdown apps to choose from! The very first one, Mou, is what the Ghost editor was originally based on.

  * [Mou](http://25.io/mou/) \- Free
  * [iA Writer](https://ia.net/writer/mac/) \- $19.99
  * [Desk](http://desk.pm/) \- $29.99
  * [ByWord](http://bywordapp.com/) \- $11.99
  * [Day One](http://dayoneapp.com/) \- $9.99
  * [SublimeText](http://www.macstories.net/roundups/sublime-text-2-and-markdown-tips-tricks-and-links/) \- $70

### Windows PC Markdown Editors

![MarkdownPad](http://blog.ghost.org/content/images/2015/03/markdown-windows.jpg)

Competition on Windows seems to be pretty sparse in the Markdown world, but most seem to agree that MarkdownPad is the tool of choice.

### Apple iOS Markdown Apps

![Day One](http://blog.ghost.org/content/images/2015/03/markdown-ios.jpg)

The best Markdown apps for iOS don't come cheap! On the plus side, most of them do offer extremely nice cloud-sync functionality which makes a big difference if you use the same app across multiple devices.

### Google Android Markdown Apps

![iA Writer](http://blog.ghost.org/content/images/2015/03/markdown-android.jpg)

Markdown apps on the Google Play Store couldn't be any cheaper if they tried! This is just a small selection of a large number of apps that are out there. The quality seems to be decidedly lower overall than the iOS store, so it may take a little digging to find a good Android Markdown app.

## Publishing Online with Markdown

![Ghost](https://blog.ghost.org/content/images/2015/03/markdown-web.jpg)

**Markdown based blogging is kind of what we specialise in!** If you're looking for a blog with a comprehensive Markdown editor. [Ghost](http://ghost.org) might be exactly what you need for beautiful, simple publishing.

It works across any device, and any platform.

## What to do next

After just a couple of hours with Markdown, we're certain that your fingers will be flying across the keys as you pen your latest and greatest post.

**Practice these steps to become a pro:**

  1. Start with **writing** your first Markdown document and get a feel for the basics. It comes more quickly than you might think! 
  2. Don't forget **keyboard shortcuts** for instant time-saving and much faster writing. 
  3. Use **HTML whenever** you want advanced formatting, having this power available to you means you can really do (almost) anything.

_We've been writing in Markdown for quite a while now, but we're always learning new and amazing ways of using it. Got any tips that we've missed?_

#### Footnotes
