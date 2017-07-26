# Academic Markdown and Citations

_Captured: 2016-03-31 at 23:54 from [www.chriskrycho.com](http://www.chriskrycho.com/2015/academic-markdown-and-citations.html)_

Much of my past few weeks were taken up with study for and writing and editing [a paper](http://www.chriskrycho.com/2015/not-exactly-a-millennium.html) for one of my classes at Southeastern. I've been writing all of my papers in Markdown ever since I got here, and haven't regretted any part of that… except that managing references and footnotes has been painful at times.

Footnotes in Markdown look like this:
    
    
    Here is some text.[^fn]
    
    [^fn]: And the footnote!

This poses no problems at all for normal footnotes. Academic writing introduces a few wrinkles, though, which means that this has always been the main pain point of my use of Markdown for writing papers.

Many academic citation styles (including the Chicago Manual of Style, on which our seminary's [style guide](http://www.press.uchicago.edu/books/turabian/turabian_citationguide.html) is based) tend to have a long version of the footnote appear first, followed by short versions later. Nearly _all_ academic citations styles make free use of the "[ibid."](https://en.wikipedia.org/wiki/Ibid.) abbreviation for repeated references to save space, time, and energy. Here is how that might look in manually-written footnotes, citing the very paper in which I sorted this all out:
    
    
    Some text in which I cite an author.[^fn1]
    
    More text. Another citation.[^fn2]
    
    What is this? Yet *another* citation?[^fn3]
    
    [^fn1]: So Chris Krycho, "Not Exactly a Millennium," chriskrycho.com, July 22,
        2015, http://www.chriskrycho.com/2015/not-exactly-a-millennium.html
        (accessed July 25, 2015), ¶6.
    
    [^fn2]: Contra Krycho, ¶15, who has everything *quite* wrong.
    
    [^fn3]: ibid.

This seems straightforward enough, though it is a bit of work to get the format right for each different kind of citation (articles, books, ebooks, electronic references to articles…). Things _really_ get complicated in the editing process, though. For example, what if I needed to flip the order of some of these notes because it became clear that the paragraphs needed to move around? This happens _frequently_ during the editorial process. It becomes particularly painful when dealing with the "ibid."-type references, because if I insert a new reference between two existing references, I have to go back in and manually add all that the reference content again myself.[1](http://www.chriskrycho.com/2015/academic-markdown-and-citations.html)

Enter Pandoc and BibTEX.

![<span style=](http://cdn.chriskrycho.com/images/bibdesk.png)

> _BibDesk - open to the library for my Revelation paper">_
