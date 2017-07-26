# Separation: The Web Designer’s Dilemma

_Captured: 2015-12-16 at 13:14 from [alistapart.com](http://alistapart.com/article/separationdilemma)_

With all the discussion about separating presentation from content (and structure), it's easy to lose track of the goal. So let's step back, define our terms, and take a look at why it matters.

## Presentation

The major reason to separate presentation from the rest of the page is simple: to simplify any change from a slight design adjustment to a full-fledged redesign. To achieve complete separation of the presentation, we must isolate everything specifically and solely geared towards style.

Contrary to what you might be thinking, this isn't limited to just the CSS, not even on a site like [CSS Zen Garden](http://www.csszengarden.com/). It also involves HTML tags and properties that exist only to provide a handle for the designer to apply styles to. After all, what use is a `.pageheader {…}` declaration block if there is no element with that class on the page?

Hold on to this thought and read on.

## Content

The reason to separate content from the rest of the page is just as easy to see as the reason to isolate presentation. Isolation of content makes adding or updating things easy while maintaining presentational consistency throughout the site. However, as with the presentation, there can be confusion over what content actually _is_.

For our purposes, content is (usually) text and includes accompanying semantic coding: tags like h1-h6, paragraphs, list, em, strong, code, cite, etc. Content should not require any additional presentational tags or styles in order to fully convey its message.

In isolated cases, we might use additional tags to more correctly present the content. For example, a poem -- where specific line breaks are important -- could be set apart by a `<pre class="poem">` tag, or it could simply make use of `<br>` tags to break lines.

## Structure

Here's where things get sticky. First of all, what is structure? We could describe structure as everything that makes up a page, minus presentational elements and content. However, this is at best an overly simplified definition that could easily cause undue confusion.

Take the navigation menus on ALA as an example:

  * Change a color here, a border thickness there, and you have a change in presentation.
  * Change the text of the first navigation item from "Up front" to "Home", and you have a change in content.
  * Lastly, you have the `<div id="menu">`, `<ul>`, and `<li id="…">` tags as the structure. Switch those out with an antique row of table cells, and you have a change in structure.

But wait -- remember what I pointed out earlier? Those tags include presentational elements: the IDs. As both [Doug Bowman](http://www.stopdesign.com/log/2003/10/14/separated.html) and [Eric Meyer](http://www.meyerweb.com/eric/thoughts/200310.html#t200310015) have pointed out, presentation is pointless without structure. Furthermore, I'll show that it's also pointless to try to separate structure from content.

Take the simplest example of web content you can think of:
    
    
      
    
    # Title
    
    
    
    
    Lorem ipsum dolor met.
    
    
    

The `<h1>` and `<p>` tags are clearly part of the content, right? We can't write correct HTML content without this basic semantic markup. Yet this markup is also part of the document structure, dividing up an otherwise-uniform blob of words into a heading and a paragraph. (And of course, if you want to get picky, you can consider the markup to also be a part of the presentation as well. After all, the browser has a preset way of displaying `<h1>` and `<p>` text, doesn't it?)

So where does this leave us?

### Content and structure

You can theoretically separate content and structure, but then you'd be left with `<ul><li>` for structure and plain featureless text for content. Needless to say, building a functional site out of those is quite impossible.

So we can conclude that structure cannot and should not be separate from content.

### Presentation and structure

As we have seen, without structural elements, there is no way to apply styling to the content. Structure cannot be separate from presentation -- nor should it be.

Which leaves us with …

### Presentation and content

Although presentation still depends on structure, some of which is embedded into the content as noted above, presentation can and should be separated from content.

And while major presentational changes can require changes in structure, _content_ can be changed without any need for structural change beyond the already-embedded structural elements.

## Real-world separation tools

With all this in mind, let's envision the perfect website separation system.

It would store content in a database, allowing the isolation and management of content information. Presentation and structure would be handled together; presentation could be managed with a stylesheet and accompanying structural elements where needed.

Structure would best be dealt with through a system of template "packages" built using a server-side scripting language (such as PHP or ASP). Each template "package" could have one or more stylesheets (e.g. CSS Zen Garden), but every template "package" would connect to the same with the same database to retrieve content for display.

Many content management systems provide varying levels of this kind of template support. However, full-featured template systems that make CSS Zen Garden-like usage of stylesheets -- especially ones that come with a comprehensive content management system -- are few and far between.

But for a competent webmaster, building something like this from scratch can't be all that hard. Can it?
