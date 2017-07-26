# Choosing the Right Markdown Parser

_Captured: 2017-04-11 at 10:59 from [css-tricks.com](https://css-tricks.com/choosing-right-markdown-parser/)_

_The following is a guest post by [Ray Villalobos](http://www.raybo.org/). Ray is going to explore many of the different varietals of Markdown. All of them offer features beyond what the original Markdown can do, but they offer different features amongst themselves. If you're choosing a version to use (or a version you're offering to users on your web product), it pays to know what you are getting into, as it's difficult to switch once you've chosen and there is content out there that depends on those features. Ray, who has [a course on Markdown](http://www.lynda.com/Web-Development-tutorials/Up-Running-Markdown/438888-2.html), is going to share which versions have which features to help you make an informed choice._

Markdown has changed the way professionals in many fields write. The language uses simple text with minimal markup and can convert it to a growing number of formats. However, not all markdown parsers are created equally. Because the original spec hasn't evolved with the times, alternate versions like Multi-Markdown, GFM (Github Flavored Markdown), Markdown Extra and others have expanded the language.

The [original parser](https://daringfireball.net/projects/markdown/) was written in Perl. The core features include parsing block elements (such as paragraphs, line breaks, headers, blockquotes, lists, code blocks and horizontal rules) and span elements (links, emphasis, code snippets and images). Since then, the language hasn't been expanded by its creator John Gruber, so a number of additions and implementations have surfaced with different parsers adding support for different implementations as they see fit, or interpreting how certain elements are parsed.

![](https://cdn.css-tricks.com/wp-content/uploads/2016/01/choose-markdown.jpg)

There's a lot to consider when thinking about implementing Markdown into a project, including the language you'll be developing with as well as the features you want to support. The original implementation was written in Perl, but that's not a practical option for every project. There are implementations in most popular languages including: PHP, Ruby and JavaScript. Which language you choose will have repercussions as to which features you'll be able to support and what libraries will be available. Let's take a look at some of the options:

Language Library (download project)

Perl
[Original version](http://daringfireball.net/projects/markdown/)

JavaScript
[CommonMark](https://github.com/jgm/commonmark.js), [Marked](https://github.com/chjj/marked), [Markdown-it](https://github.com/markdown-it/markdown-it), [Remarkable](https://github.com/jonschlinkert/remarkable), [Showdown](https://github.com/showdownjs/showdown)

Ruby
[Github Flavored Markup](https://github.com/github/markup), [Kramdown](https://github.com/gettalong/kramdown), [Maruku](https://github.com/bhollis/maruku), [Redcarpet](https://github.com/vmg/redcarpet)

PHP
[Cebe Markdown](https://github.com/cebe/markdown), [Ciconia](https://github.com/kzykhys/Ciconia), [Parsedown](https://github.com/erusev/parsedown), [PHP Markdown Extended](https://github.com/piwi/markdown-extended)

Python
[Python Markdown](https://pypi.python.org/pypi/Markdown)

There are additional implementations in [many other languages](https://github.com/markdown/markdown.github.com/wiki/Implementations), just in case you're looking to implement Markdown in other languages.

The core markdown language supports a number of default features that are quite useful. Although different implementations support a range of extended features, they should all support at least the following core syntax: [Inline HTML](https://daringfireball.net/projects/markdown/syntax#html), [Automatic paragraphs](https://daringfireball.net/projects/markdown/syntax#p), [headers](https://daringfireball.net/projects/markdown/syntax#header), [blockquotes](https://daringfireball.net/projects/markdown/syntax#blockquote), [lists](https://daringfireball.net/projects/markdown/syntax#list), [code blocks](https://daringfireball.net/projects/markdown/syntax#precode), [horizontal rules](https://daringfireball.net/projects/markdown/syntax#hr), [links](https://daringfireball.net/projects/markdown/syntax#link), [emphasis](https://daringfireball.net/projects/markdown/syntax#em), [inline code](https://daringfireball.net/projects/markdown/syntax#code) and [images](https://daringfireball.net/projects/markdown/syntax#img).

With the many versions of markdown available, a few have had a substantial impact on other versions. So much so that you'll often see them quoted as part of other versions. For example, libraries will mention support of CommonMark, GFM or Multi-Markdown. Let's take a look at what those mean.

One of the reason Markdown became so popular with developers is because Github, the open source sharing platform accepted and extended the language with a version called [Github Flavored Markup](https://help.github.com/articles/working-with-advanced-formatting/) (GFM) to include [Fenced Codeblocks](https://css-tricks.com/choosing-right-markdown-parser/), [URL Autolinking](https://css-tricks.com/choosing-right-markdown-parser/), [Strikethrough](https://css-tricks.com/choosing-right-markdown-parser/feature-strikethrough), [Tables](https://css-tricks.com/choosing-right-markdown-parser/) and even the ability to [create to-dos](https://css-tricks.com/choosing-right-markdown-parser/) within repos. So, when a version mentions support of GFM, look for those extensions to be implemented.

Recently there has been a move to standardize markdown. A group of Markdown developers joined to create a version, tests and documentation for the language that resulted in a more robust specification for the language called [CommonMark](http://commonmark.org/). At this time, the implementation added [fenced codeblocks](https://css-tricks.com/choosing-right-markdown-parser/), but mostly detailed the specifics of how certain features were to be implemented for consistent output and conversion. A lot more extensions that would bring this more in line with what's available in other languages [have been proposed](https://github.com/jgm/CommonMark/wiki/Proposed-Extensions) for the future.

This format is relatively new and doesn't support a lot of features, but it is actively being developed and there are plans to add many Multi-Markdown features.

Let's take a look at the features that are available through different implementations.

Dimensions Megapixels

1,920 x 1,080
2.1MP

3,264 x 2,448
8MP

4,288 x 3,216
14MP
![Markdown Tables Generator](https://cdn.css-tricks.com/wp-content/uploads/2016/01/OiO5m2q.png)

One thing that you have to be careful about is how different versions handle input and output. Just because a version says it supports tables, it doesn't mean that there's a standard way of creating the code for the tables. Some versions will generate HTML that is verbose and some will render minimalist code.

There's also variations of how things like white space are handled. Some versions will place IDs within each headline and some won't. This has been one of the concerns that the OpenMark platform tries to address, how to generate consistent output. The best way to figure out how the version you've chosen handles this is to use the [Babelmark 2 test](http://johnmacfarlane.net/babelmark2/). Paste some code and it will show you how different parsers take care of the output as well as a preview of what that looks like on a browser.

![](https://cdn.css-tricks.com/wp-content/uploads/2016/02/babelmark.png)
