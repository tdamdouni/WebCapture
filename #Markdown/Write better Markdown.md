# Write better Markdown

_Captured: 2015-08-25 at 02:23 from [brettterpstra.com](http://brettterpstra.com/2015/08/24/write-better-markdown/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

![](http://cdn3.brettterpstra.com/uploads/2015/08/markdown-ice-cream.jpg)

> _As John Gruber stated in his original introduction of the Markdown project:_

> The overriding design goal for Markdown's formatting syntax is to make it as readable as possible. The idea is that a Markdown-formatted document should be publishable as-is, as plain text, without looking like it's been marked up with tags or formatting instructions.

I work with many different "flavors" of Markdown that have branched off since Markdown 1.0. Some add syntax to accomplish more advanced output control, but the design goal typically remains the same.

> The idea is that a Markdown-formatted document should be publishable as-is, as plain text, without looking like it's been marked up with tags or formatting instructions.

Well-formatted text is not only more readable, it's more future-proof, and following a set of rules derived from the original spec means better portability.

The [CommonMark](http://commonmark.org/) project aims to clarify a lot of the things I'm about to mention. Its goal is stricter handling of ambiguities in the syntax, and it's a justifiable one. The negative reactions to the idea seem primarily summed up as "you're not my _real_ dad." People seemed more offended by the approach than [the spec](http://spec.commonmark.org/).

I'm on both sides. As a developer whose [primary application](http://marked2app.com) is Markdown-based, at least 50% of my customer support involves explaining Markdown syntax and differences between flavors. A common knowledge of what's standard is useful. Many users learn a syntax particular to a specific processor, and then face disappointment when their documents don't render properly elsewhere.

However, I love that Markdown has been extended and tweaked for specific purposes, and I take a "personal responsibility" stance on the syntax. As long as users are aware of potential compatibility issues, they can decide for themselves how much of a mess to make when working with any given processor.

This post isn't about proposing any standard or new flavors, it's just about common sense guidelines that allow you to work with _any_ processor.

Messes happen because some processors are more lax than others about formatting (preserving line breaks, allowing 2-space indentation, different interpretations of unescaped emphasis markers, etc.), or provide a syntax for elements which aren't universal (e.g. centering with `~`, fenced code with backticks or tildes, strikethrough characters). It's fine to make use of the latter, as long as you're aware of what won't work elsewhere. Ambiguous formatting without recognizing the general rules, though, is just shooting yourself in the foot.

The following guidelines will serve writers well across any flavor of Markdown, and provide portability between them.

You can test any syntax across the most common processors using [Babelmark](http://johnmacfarlane.net/babelmark2/), and if there's ever a question as to why something is working in one place and not another, it's the best place to start an investigation.

### Whitespace

Empty lines visually separate paragraphs, headlines, and other elements. Whitespace is good. You wouldn't see a word processor jam a paragraph on a line immediately after a headline or another paragraph, so why would you do it in a text file? Those blank lines don't cost you anything, and it makes your text vastly easier to scan and read. Use an empty line after headlines, between paragraphs, and before and after code/verbatim blocks and other block elements.

> One overall problem in Markdown 1.0's syntax is that it isn't clear when you need blank lines to separate block-level constructs. -- [John Gruber](http://article.gmane.org/gmane.text.markdown.general/2146)

Don't forget about spaces, either. A space after a list item delimiter (`-`, `*`, `+`, or `1.`) is required by most processors, but a space after hashmarks in headlines usually isn't. It looks better, though, and ensures universal compatibility. Again, those spaces cost you nothing. Why wouldn't you?

#### Blank lines in lists and block quotes

As [Gruber noted early on](http://article.gmane.org/gmane.text.markdown.general/2554), nested lists are an exception to the never-too-much-whitespace rule. Blank lines between list items can be interpreted very differently between processors. Keep list items consecutive, but you can use blank lines above paragraphs within lists. Just follow the last paragraph immediately with another list item (or the end of the list).
    
    
    * list item 1
    
        paragraph in list item 1
    * list item 2
    

Empty lines in block quotes are handled differently between flavors as well. The most common way to make a multi-paragraph block quote is to use a greater than symbol on each blank line:
    
    
    > paragraph one
    >
    > paragraph two
    >> nested paragraph
    >>
    >> nested paragraph two
    

Though a considerable number of the flavors will [behave oddly with that](http://johnmacfarlane.net/babelmark2/?text=%3E+paragraph+one%0A%3E%0A%3E+paragraph+two%0A%3E%3E+nested+paragraph%0A%3E%3E%0A%3E%3E+nested+paragraph+two). The issue is whether it creates a new block quote element, paragraphs within an element. Most results look the same when viewed as HTML, although Pandoc thinks the `>>` on the empty line should be escaped as HTML entities…

### ATX Headers

Use ATX Headers (i.e. hashmarks). Setext headers (dashes or equal signs immediately after a headline) are harder to visually differentiate from other syntax when scanning, plus they only go up to 2, so you're using ATX headers after that anyway. Be consistent.

### Indentation

Different Markdown flavors treat indentation in different ways. For example, Discount and its ilk (as commonly seen on GitHub) allow two-space indentation in nested lists. Other processors essentially see anything less than four spaces as a user error, and place those nested items at the same level as the parent. However, four-space/one-tab indentation is recognized across the board. Thus, when creating nested lists, **always use four spaces** instead of two.

Four spaces are universally recognized for indented code and nested lists. They're also interchangeable with a single tab character, but pick one or the other.

Personally, I'm a four-space guy. The display of tabs changes with the application and environment, so you can't rely on a tab to always be the same width and indentation can become visually confusing.

Further, if worse came to worst and you had to use basic search and replace to parse your document, consistent indentation makes life much easier.

Within a list item, indent additional paragraphs one tab or four spaces from the bullet or number indentation, with a blank line above each one. This will work in every processor. For "verbatim" (indented code blocks), you need to indent an additional level within the list item. That's two tabs or eight spaces from the nested list item's current indentation.

### Link formats

Markdown allows either inline (`[text](url)`) or reference format links. Either will work anywhere, and my personal preference is usually determined by the length of the document. Short documents get inline links. Longer ones get blocks of reference links. The readability is the determining factor.

When using the reference style, you can put the actual links anywhere in the document. I used to always group them at the top or the bottom, but have come to include the links shortly after the paragraph or list the reference is included in. This makes it much easier when reading the raw text document to see where a referenced link points to.

### Escaping

This is a short one. Some processors are looser (you could substitute "smarter") with requiring escaping of special characters. Reserved characters such as asterisks, underscores, and backticks that are not paired _and_ touching non-whitespace characters are generally ignored, but it's wise to _always_ escape them (using a preceding backslash) if you don't want to confuse less detail-oriented processors. This includes words with underscores inside of them, e.g. a `file\\_name`.

### Emphasis

You can use asterisks and underscores interchangeably for emphasis markup. Using one for italics and one for bold is the best way to clearly distinguish intention within the text. I personally like underscores for italics and double asterisks for bold, but I don't care when reading someone else's text, as long as it's consistent.

### Fenced code blocks

As mentioned above, fenced code blocks are an extension found in a majority of modern Markdown processors, but not all of them. It's a useful syntax to have if you use programming languages in your writing, and especially if you want syntax highlighting. I consider them a standard at this point, with some caveats.

If you're using fenced code blocks, it should be because you need to specify a language (e.g. `\`"ruby`). If you don't need syntax highlighting, then you don't need to specify a language, and using an indented code block (any block of text indented one level) will better ensure compatibility.

The language specifiers defined by Python Markdown, Markdown Extra, and others can use combinations curly brackets and colons to declare a language. If avoidable, don't do this. The format where the language nickname immediately follows the opening fence with no braces is more widely accepted, and thus most likely to work in more flavors and future implementations.

Many syntaxes allow fences to be either backticks ("`) or tildes (~~~). Backticks are the universal option, I suggest sticking with them. Most flavors also allow you to use as many of these characters as you want, as long as the opening and closing fences are exactly the same length. I find that three characters (which is the minimum) does the job perfectly and maintains readability. Again, it's the widely accepted style, and most likely to work across flavors.

### That's not universal

Here's a list of fairly common elements you might have thought would work anywhere, but won't:

Tables
    The PHP Markdown Extra format for tables, (pipes (`|`) between cells with a header row on the second line consisting of colons and dashes for alignment) is generally rendered, but not at all a standard part of the syntax. 
    

The trick is to ensure that your tables are formatted such that they're readable in plain text. This way, if needed, you can just indent the whole table and have it displayed as a code block. 

    

It's a pain to type a well-formatted table, but there are numerous tools and scripts to clean them up automatically as you go. See [Fletcher Penney's table formatting](http://brettterpstra.com/2011/05/23/quick-tip-clean-up-your-multimarkdown-tables/) script (also in the [Markdown Service Tools](http://brettterpstra.com/project/markdown-service-tools/), [Dr. Drang's version](http://www.leancrew.com/all-this/2014/06/cleaning-up-my-markdown-table-cleanup-script/) in Python, [MultiMarkdown Composer](http://brettterpstra.com/2015/08/24/write-better-markdown/!s)'s built in table tools, or [packages available for Sublime Text](https://packagecontrol.io/search/table), [BBEdit](http://www.leancrew.com/all-this/2012/11/markdown-table-scripts-for-bbedit/), and [TextMate](https://github.com/textmate/markdown.tmbundle), among others.

Footnotes
    

Again, there's a format for footnotes that's generally accepted (`[^marker]` and `[^marker]: footnote text`) , but I'd estimate less than 50% of common Markdown processors will render them. In plain text form, they're perfectly readable and you can easily include the footnotes themselves immediately below a paragraph. They might mess up rendering in many cases, though. It's one of those nifty additions that--as long as you realize the potential pitfalls--can be a very useful tool.

Fenced code blocks
    As previously discussed
CSS class syntax
    Any syntax used to define CSS classes, ids, anchors, etc. is not universal. Markdown does not cover these cases (which is a reason so many flavors evolved). 
    They're handy, especially for blogging and design platforms, but a format from one (such as Kramdown or Maruku) is unlikely to be recognized in another.
Center/justify/align, strikethrough, underline
    The Discount-style formats for additional markup elements are again handy, but mean nothing to 90% of processors.

### Semantics

You have six levels of headlines available, make them make sense. The highest level (usually an H1) should be the first headline in your document. If your document is long enough to have sections, use a consistent header level to divide them.

From a semantic standpoint, H1s don't make good section dividers in a continuous document. If the document has no title headline, start the diveders at H2.

Don't jump from an H2 to an H4 without precedence in the structure. I'll reserve judgement if the levels are used consistently, but a proper hierarchy allows processors with Table of Contents features to generate an accurate outline.

This is mostly semantics and not style, but using header levels for emphasis willy-nilly leads to a mess of a document structure, especially if your output destinations include HTML.

### Make good life choices

Much like coding styles, everyone has the option to be unique (messy), but following style guidelines makes it easier to work with your writing in the future, and people who acquire it down the line will thank you.

Like coding styles, there are tools available to clean up your Markdown. Take a look at tools such as [markdownfmt](https://github.com/shurcooL/markdownfmt), [formd](http://drbunsen.github.io/formd/), and [markdownlint](https://github.com/mivok/markdownlint).

Use whatever Markdown flavor you like (or need), just keep these notes in mind to save yourself some pain. Now go write.
