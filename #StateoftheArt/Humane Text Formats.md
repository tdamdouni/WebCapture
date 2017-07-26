# Humane Text Formats

_Captured: 2015-11-09 at 15:03 from [bluebones.net](http://bluebones.net/2005/02/humane-text-formats/)_

**I write in plain text a lot**. I want to put stuff on the web a lot.  
Oftentimes it's the stuff I already wrote in plain text. I wondered if I could learn some conventions that would **convert to XHTML for no extra work** after I'd written the plain text. In fact, I am writing this article now in [Ultraedit](http://www.ultraedit.com/) and later it will go on [bluebones.net](http://bluebones.net) in HTML. And as I wrote ultraedit I wanted to put a link in for that very reason but wasn't sure whether to or not because it then makes this file html and I'd need to go back and put in <p> tags and so on. Let's just say that I think learning one of these formats would be A Good Idea™.

For those wondering **why I don't write in HTML all the time** check out [these good reasons](http://c2.com/cgi/wiki?WhyDoesntWikiDoHtml).

This seems to have been the [rationale behind Markdown](http://daringfireball.net/2004/03/dive_into_markdown). There are also numerous other text formats like [Textile](http://www.textism.com/tools/textile/) and [Almost Free Text](http://www.maplefish.com/todd/aft.html)  
with similar or identical motivations. I don't want to learn them all, so which one to pick? I couldn't find a good comparison or even much of a list of alternatives via Google. Answer: have a face off.

### The Test

I decided to use the text of [this very article](http://bluebones.net/news/default.asp?action=view_story&story_id=94).   
(Originally I decided I was going to use a BBC news story too but I'd learnt enough about the formats by the time I'd been through them all once!)

Some things I definitely want the winner to be able to do are:

  * Unordered lists
  * Like this one

and
    
    
    # Code examples like this.
    print "This is essential!"
    

The quality of tools available is also a big plus. For this to reap rewards I  
must be able to go effortlessly from text to XHTML and (strongly preferred) back  
again.

### The Results

#### Almost Free Text

<http://www.maplefish.com/todd/aft.html>

An enviable set of outputs: HTML, LaTeX, lout, DocBook and RTF. You have to tell it explicitly to use other than 8 spaces for tabstops, or use tabs. My text editor is set to use spaces for tabs because they travel better (email, etc.) and it is set to 4 spaces. No titles on links. Does table of contents.   
No line breaks allowed in link elements is a problem. Adds a whole load of  
extra formatting by default - makes whole documents instead of snippets. HTML 4.0 Transitional. Doesn't seem to be any way to make snippets or XHTML.

[See Almost Free Text Test Results](http://bluebones.net/textformats/almostfreetext-tests.html)

#### Markdown

<http://daringfireball.net/projects/markdown/>

A format that comes from [Daring Fireball](http://www.daringfireball.com/). Default formatting of the Instiki(http://instiki.org/) Wiki. Choked on converting trademark symbol from the HTML character entity reference to Mardown and cannot do tables but otherwise superb and plain text looks right too - not marked up just "natural".

Tools include [html2text](http://www.aaronsw.com/2002/html2text/html2text.py), a  
Python script that converts a page of HTML into valid Markdown. There is also a [PHP implementation](http://www.michelf.com/projects/php-markdown/). RedCloth  
(Ruby) has limited support for Markdown.

#### reStructuredText

<http://docutils.sourceforge.net/rst.html>

The format of Python doc strings. Only a "[very rough prototype"](http://philosophy.berkeley.edu/macfarlane/html2rst.html) for converting HTML to reStructuredText (written in OCaml). Links are clunkier than in Markdown or Textile. Cannot set title attributes on links. Nice autonumbering footnotes. No simple way to avoid turning processed text into a full document. I would ideally like to process snippets for cutting and pasting into existing documents or standard headers and footers.

[See reStructuredText Test Results](http://bluebones.net/textformats/restructuredtext-tests.html)

#### Textile

<http://www.textism.com/tools/textile/>

Originally created for Textpattern. There is a Movable Type plugin. An alternate to the default Markdown in Instiki. Does class, id, style, language attributes and lots of character entity replacement (em dash, curly quotes, that kind of thing). Only a rudimentary [HTML=>Textile converter](http://www.matthewsmith.id.au/textpattern/demo.php) available. Very obviously meant to be turned into HTML (look at the headings h1, h2, etc.) and not so good as just a way of formatting plain text.

I had trouble making html => text tool work - no trademark and strict xml parsing just exited with error "Junk after document element at line 12" despite passing W3C validator test for XHTML 1.0 Strict.

Code doesn't work. Breaks where it finds CR (can't have 80 col source and XHTML must use word wrap).

RedCloth (Ruby) supports Textile.

#### Others

[RDoc](http://rdoc.sourceforge.net/) - Originally created to produce documentation from Ruby source files. Offered as an alternative markup option by [Instiki](http://instiki.org/). Outputs XML, HTML, CHM (Compiled HTML) and RI (whatever that is). Commandline tool. Now part of core Ruby which ensures continued support but perhaps only as a documentation tool not in the more general sense that I want to use it.

[StructuredText](http://www.zope.org/Documentation/Articles/STX) - Allows  
embedded HTML and DHTML. Used by [Zope](http://www.zope.org/) and  
the related [ZWiki](http://www.zwiki.org/FrontPage). Rather horribly uses  
indentation rather than explicit heading markers. Supports tables. No way to  
go from HTML to Structured Text. Somewhat similar to reStructured Text.

Other formats I didn't have time to consider in depth or which I discounted for certain reasons: [WikiWikiWeb formatting](http://c2.com/cgi/wiki?TextFormattingRules) (no tools only as part of WikiWikiWeb), [DocBook](http://www.docbook.org/) (for whole books not snippets), atx (can't find enough info - seems to have been superseded by Markdown), RDTool (didn't like =begin/=end and lesser than RDoc from the same community), YAML (aimed mainly at configuration files), MoinMoin formatting (no tools to use it separate from the Wiki it comes from), SeText (superseded by StructuredText and ReStructuredText), POD (Plain Old Documentation - the Perl documentation format).

### Summary

Textile and Markdown were the only formats I investigated that were truly practical for snippets not full documents. Textile had better support for more HTML features at the expense of looking more like HTML and less like plain text in the first place. Since I can write HTML any time I want anyway and because it has the better tools, Markdown is my provisional "winner". If anyone wants  
to correct any errors above (in the comments section) I'm willing to revise my opinion. (Quick! Before I get wed to this syntax and can't change!)

### Feature Comparison Table

Plain Text Formats Feature Comparison Table 

Format To HTML Tool From HTML Tool Tables? Link Titles? class Attribute? id Attribute? Output formats License

[Almost Free Text](http://www.maplefish.com/todd/aft.html)
[Yes](http://www.maplefish.com/todd/aft.html)
No
No
No
No
No
HTML, LaTeX, lout, DocBook and RTF
Clarified Artistic License

[Markdown](http://daringfireball.net/projects/markdown/)
[Yes](http://daringfireball.net/projects/markdown/dingus/)
[Yes](http://daringfireball.net/projects/markdown/dingus/)
No
Yes
No
No
XHTML
BSD-style

[reStructuredText](http://docutils.sourceforge.net/rst.html)
[Yes](http://docutils.sourceforge.net/index.html)
[Sort of](http://philosophy.berkeley.edu/macfarlane/html2rst.html)
Yes
No
Yes
Auto
Latex, XML, PseduoXML, HTML
Python

[Textile](http://www.textism.com/tools/textile/)
[Yes](http://www.textism.com/tools/textile/)
No
Yes
Yes
Yes
Yes
XHTML
[Textile License](http://www.textism.com/tools/textile/license.html)
