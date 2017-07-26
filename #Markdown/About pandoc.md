# About pandoc

_Captured: 2015-06-09 at 21:56 from [pandoc.org](http://pandoc.org/)_

If you need to convert files from one markup format into another, pandoc is your swiss-army knife. Pandoc can convert documents in [markdown](http://daringfireball.net/projects/markdown/), [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html), [textile](http://redcloth.org/textile), [HTML](http://www.w3.org/TR/html40/), [DocBook](http://www.docbook.org/), [LaTeX](http://www.latex-project.org/), [MediaWiki markup](http://www.mediawiki.org/wiki/Help:Formatting), [TWiki markup](http://twiki.org/cgi-bin/view/TWiki/TextFormattingRules), [OPML](http://dev.opml.org/spec2.html), Emacs [Org-Mode](http://orgmode.org), [Txt2Tags](http://txt2tags.org/), Microsoft Word [docx](http://www.microsoft.com/interop/openup/openxml/default.aspx), [EPUB](http://en.wikipedia.org/wiki/EPUB), or [Haddock markup](http://www.haskell.org/haddock/doc/html/ch03s08.html) to

  * HTML formats: XHTML, HTML5, and HTML slide shows using [Slidy](http://www.w3.org/Talks/Tools/Slidy), [reveal.js](http://lab.hakim.se/reveal-js/), [Slideous](http://goessner.net/articles/slideous/), [S5](http://meyerweb.com/eric/tools/s5/), or [DZSlides](http://paulrouget.com/dzslides/).
  * Word processor formats: Microsoft Word [docx](http://www.microsoft.com/interop/openup/openxml/default.aspx), OpenOffice/LibreOffice [ODT](http://en.wikipedia.org/wiki/OpenDocument), [OpenDocument XML](http://opendocument.xml.org/)
  * Ebooks: [EPUB](http://en.wikipedia.org/wiki/EPUB) version 2 or 3, [FictionBook2](http://www.fictionbook.org/index.php/Eng:XML_Schema_Fictionbook_2.1)
  * Documentation formats: [DocBook](http://www.docbook.org/), [GNU TexInfo](http://www.gnu.org/software/texinfo/), [Groff man](http://www.gnu.org/software/groff/groff.html) pages, [Haddock markup](http://www.haskell.org/haddock/doc/html/ch03s08.html)
  * Page layout formats: [InDesign ICML](https://www.adobe.com/content/dam/Adobe/en/devnet/indesign/cs55-docs/IDML/idml-specification.pdf)
  * Outline formats: [OPML](http://dev.opml.org/spec2.html)
  * TeX formats: [LaTeX](http://www.latex-project.org/), [ConTeXt](http://www.pragma-ade.nl/), LaTeX Beamer slides
  * [PDF](http://en.wikipedia.org/wiki/Portable_Document_Format) via LaTeX
  * Lightweight markup formats: [Markdown](http://daringfireball.net/projects/markdown/) (including [CommonMark](http://commonmark.org)), [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html), [AsciiDoc](http://www.methods.co.nz/asciidoc/), [MediaWiki markup](http://www.mediawiki.org/wiki/Help:Formatting), [DokuWiki markup](https://www.dokuwiki.org/wiki:syntax), Emacs [Org-Mode](http://orgmode.org), [Textile](http://redcloth.org/textile)
  * Custom formats: custom writers can be written in [lua](http://www.lua.org).

Pandoc understands a number of useful markdown syntax extensions, including document metadata (title, author, date); footnotes; tables; definition lists; superscript and subscript; strikeout; enhanced ordered lists (start number and numbering style are significant); running example lists; delimited code blocks with syntax highlighting; smart quotes, dashes, and ellipses; markdown inside HTML blocks; and inline LaTeX. If strict markdown compatibility is desired, all of these extensions can be turned off.

LaTeX math (and even macros) can be used in markdown documents. Several different methods of rendering math in HTML are provided, including MathJax and translation to MathML. LaTeX math is rendered in docx using native Word equation objects.

Pandoc includes a powerful system for automatic citations and bibliographies, using [pandoc-citeproc](http://hackage.haskell.org/package/pandoc-citeproc) (which derives from Andrea Rossato's [citeproc-hs](http://hackage.haskell.org/package/citeproc-hs)). This means that you can write a citation like
    
    
    [see @doe99, pp. 33-35; also @smith04, ch. 1]

and pandoc will convert it into a properly formatted citation using any of hundreds of [CSL](http://citationstyles.org/) styles (including footnote styles, numerical styles, and author-date styles), and add a properly formatted bibliography at the end of the document. Many forms of bibliography database can be used, including bibtex, RIS, EndNote, ISI, MEDLINE, MODS, and JSON citeproc. Citations work in every output format.

Pandoc includes a Haskell library and a standalone command-line program. The library includes separate modules for each input and output format, so adding a new input or output format just requires adding a new module.

Pandoc is free software, released under the [GPL](http://www.gnu.org/copyleft/gpl.html). (C) 2006-2014 [John MacFarlane](http://johnmacfarlane.net/).

![pandoc conversions](http://pandoc.org/diagram.jpg)

> _pandoc conversions_
