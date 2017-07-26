# Markdown + JavaScript = Great HTML Presentation Decks

_Captured: 2015-11-23 at 01:27 from [theholyjava.wordpress.com](https://theholyjava.wordpress.com/2013/03/24/markdown-javascript-great-html-presentation-decks/)_

You can easily create beatiful, interactive, simple presentations by writing them in [Markdown](http://daringfireball.net/projects/markdown/) (falling back to HTML whenever needed) with special markers separating the individual slides and using JavaScript to render it into an interactive HTML presentation. We will now look at a few tools that can help you with that. My favorite one is Reveal.js that has recently got out-ot-the-box support for full Markdown presentations.

## Presentation frameworks

### Reveal.js

  * [Reveal.js at GitHub](https://github.com/hakimel/reveal.js/), [live demo](http://lab.hakim.se/reveal-js/) introducing many of its features
  * Popular, beautiful, many capabilities
  * PDF export, speaker notes (show on demand or on another device via node.js)
  * The presentation is in HTML but individual slides may contain Markdown (this will result in a number of vertical and/or horizontal slides/sections): 
    
        <section data-markdown>
        <script type="text/template">
            Markdown body of a slide here ...
        </script>
    </section>

  * Moreover, [the whole presentation may be loaded from a Markdown file](https://github.com/hakimel/reveal.js/#external-markdown): 
    
        <section data-markdown="/my_presentation.md" data-separator="^\n---\n" data-vertical="^\n\n">
         Markdown body of a slide here ...
    </section>

    * Beware: Both the index.html and the presentation .md file must be served by the same HTTP server due to security limitations; a simple one likely available on your machine is `python -m SimpleHTTPServer`
    * The two other attributes are optional. `\---` sourrounded by blank lines is the default separator for horizontal slides (none for vertical ones).
  * Code syntax higlighting via [highlight.js](http://softwaremaniacs.org/soft/highlight/en/)
  * Overview mode (overview over all the slides)
  * You can also create and share Reveal.js presentation online via rvl.io

### deck.js

  * [deck.js](https://github.com/imakewebthings/deck.js): "A JavaScript library for building modern HTML presentations"
  * Markdown supported within slides with the [deck.js-markdown](https://github.com/tmbrggmn/deck.js-markdown) extension
  * Similarly to Reveal.js, the presentation is still HTML with `<section>...</section>` but the slides content may be Markdown

### MarkdownPresenter

  * minimalistic, little older
  * uses showdown.js to transform a standard Markdown document into HTML
  * slides separated by ! surrounded by empty lines
  * move around with <-, -> and reload it (staying on the same slide) with a space (useful during writing)

### Slidedown

  * Contary to the other, JS-based frameworks, this tool is written in Ruby and the presentation HTML must be generated from Markdown offline
  * Generate syntax-highlighted slides from Markdown
  * the whole presentation is in Markdown, slides separated by `!SLIDE`
  * syntax highlighting (put your code between `@@@ ruby` and `@@@`)
  * last commit Feb 2012

## Tools

### Showdown.js: Markdown to HTML via JS

  * supports custom extensions (regexp replace, filter callback)

### PageDown

  * [PageDown](http://code.google.com/p/pagedown/wiki/PageDown) is the JavaScript Markdown previewer used at Stack Overflow - renders Markdown into HTML
  * usable on client or server side (with node.js)
  * based on a fork of showdown.js
  * no support for presentation but it could easily be extended via its hooks

### Highlight.js: Automatic source code highlighting

  * "it works automatically: finds blocks of code, detects a language, highlights it"
  * 2/2013: 54 languages, bundled with 26 style themes

## Other resources

  * [Roundup of HTML-Based Slide Deck Toolkits](http://www.impressivewebs.com/html-slidedeck-toolkits/) - Fathom.js, impress.js, 5lide, Slidedown, deck.js, html5slides (Google HTML5 slide template) and a number of others
