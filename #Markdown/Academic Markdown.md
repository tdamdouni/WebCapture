# Academic Markdown

_Captured: 2016-03-31 at 23:52 from [medium.com](https://medium.com/@chriskrycho/academic-markdown-and-citations-fe562ff443df#.ty228c7s3)_

Much of my past few weeks were taken up with study for and writing and editing [a paper](http://www.chriskrycho.com/2015/not-exactly-a-millennium.html) for one of my classes at Southeastern. I've been writing all of my papers in Markdown ever since I got here, and haven't regretted any part of that… except that managing references and footnotes has been painful at times.

Footnotes in Markdown look like this:

This poses no problems at all for normal footnotes. Academic writing introduces a few wrinkles, though, which means that this has always been the main pain point of my use of Markdown for writing papers.

Many academic citation styles (including the Chicago Manual of Style, on which our seminary's [style guide](http://www.press.uchicago.edu/books/turabian/turabian_citationguide.html) is based) tend to have a long version of the footnote appear first, followed by short versions later. Nearly _all_ academic citations styles make free use of the "[ibid."](https://en.wikipedia.org/wiki/Ibid.) abbreviation for repeated references to save space, time, and energy. Here is how that might look in manually-written footnotes, citing the very paper in which I sorted this all out:

This seems straightforward enough, though it is a bit of work to get the format right for each different kind of citation (articles, books, ebooks, electronic references to articles…). Things _really_ get complicated in the editing process, though. For example, what if I needed to flip the order of some of these notes because it became clear that the paragraphs needed to move around? This happens _frequently_ during the editorial process. It becomes particularly painful when dealing with the "ibid."-type references, because if I insert a new reference between two existing references, I have to go back in and manually add all that the reference content again myself.

Enter Pandoc and BibTEX.

### Managing Citations

The idea of plain-text solutions to academic writing is not especially new; only the application of Markdown to it is -- and that, only relatively. People have been doing this, and [documenting their approaches](http://kieranhealy.org/blog/archives/2014/01/23/plain-text/), for quite a while. Moreover, tools for managing references and citations have existed for quite some time as well; the entire [LATEX](http://www.latex-project.org/) toolchain is largely driven by the concerns of academic publishing, and as such there are tools in the LATEX ecosystem which address many of these problems.

One such is BibTEX, and the later (more capable) BibLATEX: tools for managing bibliographies in LATEX documents. The BibTEX/BibLATEX approach to managing citations in a document is the use of the \cite command, with the use of "keys" which map to specific documents: \cite{krycho:2015aa}, for example.

This is not Markdown, of course. But other folks who have an interest in Markdown and academic writing have put their minds to the problem already. Folks such as Jon MacFarlane, the originator and lead developer of [Pandoc](http://pandoc.org/), perhaps the single most capable text-conversion tool in existence. As it turns out, Pandoc Markdown supports a [citation extension](http://pandoc.org/README.html#citations) to the basic markup. It's just a variant on the BibTEX citation style that feels more at home in Markdown: a pair of braces and an @, plus the citation key, like [@krycho]. Moreover, Pandoc knows how to use BibTEX libraries, as well as many others, and [Citation Style Languages](http://citationstyles.org/) (CSLs) to generate markup in _exactly_ the format needed for any given citation style.

Instead of writing out all those citations details by hand, then, I can just format my footnotes like this (assuming the citekey I had set up for the article was krycho:revelation:2015):
    
    
    Some text in which I cite an author.[^fn1]  
      
    More text. Another citation.[^fn2]
    
    
    [^fn1]: [@krycho:revelation:2015], ¶6.
    
    
    [^fn2]: Contra [@krycho:revelation:2015], ¶15, who has everything *quite* wrong.
    
    
    [^fn3]: [@krycho:revelation:2015].

This is much simpler and, importantly, has the exact same form for each citation. Pandoc will take care of making sure that the first reference is in the long form, later references are in the short form, and repeated references are in the "ibid." form as appropriate. It even renders a properly sorted and structured Works Cited section.

The slightly complex command I used to generate a Word document from a Markdown file with citations (using my own BibTEX library and the Chicago Manual of Style CSL) on the command line is:
    
    
    $ pandoc revelation.md --smart --standalone \ --bibliography /Users/chris/Dropbox/writing/library.bib \ --csl=/Users/chris/Dropbox/writing/chicago.csl -o revelation.docx

To see an extended sample of this kind of usage in practice, take a look at the [Markdown source](http://www.chriskrycho.com/2015/not-exactly-a-millennium.txt) for the paper I wrote last week, using exactly this approach. Every footnote that references a specific source simply has a cite key of this variety. The header metadata includes a path to the bibliography file and a CSL. (These could be configured globally, as well, but I chose to specify them on a per-file basis so that if I want or need to use _different_ styles or a separate library for another file at a later time, I can do so with a minimum of fuss. More on this below.)

[Here](http://www.chriskrycho.com/downloads/revelation.docx) is the rendered result. You can see that it automatically generated everything right down to the "ibid."-style footnotes. I made a few, fairly minimal tweaks (replacing the search URL with an ATLA database catalog reference and inserting a section break before the Works Cited list), and turned the paper in -- confident, for the first time since I started seminary, that all of the references were in the right order and the right format. With carefully formatted reference documents (with their own style sets), I was able to generate an actually _nice_ [PDF](http://www.chriskrycho.com/downloads/revelation-pretty.pdf) version of the paper from another Word document, as well.

And, better yet, you don't even have to put citations in footnotes. As [@anjdunning](https://twitter.com/anjdunning) pointed out in a [tweet](https://twitter.com/anjdunning/status/625415216575197184) response to the original version of this post:

In my standard example from above, then, you could simply do this:
    
    
    Some text in which I cite an author.[@krycho:revelation:2015, ¶6]
    
    
    More text. Another citation.[Contra @krycho:revelation:2015, ¶15, who has everything *quite* wrong.]

This will generate the same markup for my purposes here; and as [@anjdunning](https://twitter.com/anjdunning) noted, it goes one step further and does what's appropriate for the CSL. This might be handy if, for example, you wanted to use the Chicago notes-bibliography style in one format, but switch to a simpler parenthetical citation style for a different medium -- or even if you had a paper to submit to different journals with different standards. Having the citations inline thus has many advantages.

Now, there are still times when you might want to split those out into distinct footnotes, of course. That second one is a good candidate, at least for the way I tend to structure my plain-text source. I find it useful in the case of _actual_ footnote content -- i.e. text that I'm intentionally leaving aside from the main text, even with reference to other authors -- to split it out from the main flow of the paragraph, so that someone reading the plain text source gets a similar effect to someone reading the web or Word or PDF versions, with the text removed from the flow of thought. In any case, it's quite nice that Pandoc has the power and flexibility such that you don't _have_ to.

Finally, you don't actually _need_ the brackets around the citekey, depending on how you're using the reference. If you wanted to cite the relevant author inline, you can -- and it will properly display both the inline name and a reference (footnote, parenthetical, etc.) in line with the CSL you've chosen. If I were going to quote myself in a paper, I would do something like this:
    
    
    As @krycho:revelation:2015 comments:

This is _extremely_ powerful, and while I didn't take advantage of it in my first paper using these tools, you can bet I will be in every future paper I write.

#### All those references

Of course, as is probably apparent, managing a BibTEX library by hand is no joke. Entries tend to look like this:
    
    
    @book{beale:revelation:2015,   
     Date-Added = {2015-07-20 21:16:02 +0000},  
     Date-Modified = {2015-07-20 21:21:05 +0000},  
     Editor = {G. K. Beale and David H. Campbell},  
     Publisher = {William B. Eerdmans Publishing Company},  
     Title = {Revelation: A Shorter Commentary}, Year = {2015}}

While there is a lot of utility in having that data available in text, on disk, no one wants to _edit_ that by hand. Gladly, editing it by hand is not necessary. For this project, I used the freely available [BibDesk](http://bibdesk.sourceforge.net/) tool, which is a workable (albeit not very pretty and not _very_ capable) manager for BibTEX:

![](https://cdn-images-1.medium.com/max/600/0*VsoPqSZ7QxjHHA7C.png)

> _BibDesk -- open to the library for my Revelation paper_

Once I filled in the details for each item and set a citekey for it, I was ready to go: BibDesk just stores the files in a standard .bib file on the disk, which I specified per the Pandoc command above.

BibDesk gets the job done alright, but only alright. Using a citation and reference management tool was a big win, though, and I fully intend to use one for every remaining project while in seminary -- and, quite possibly, for other projects as well. Whether that tool is BibDesk or something else is a different matter entirely. (More on this below.)

### To the web!

I wanted something more out of this process, if I could get it. One of the reasons I use plain text as a source is because from it, I can generate Word documents, PDFs, and _this website_ with equal ease. However, Python Markdown knows nothing of BibTEX or citekeys, to my knowledge -- and since I render everything for school with Pandoc, I have long wanted to configure [Pelican](http://docs.getpelican.com/en/3.6.0/) to use Pandoc as its Markdown engine instead of Python Markdown anyway.

As it happens, I actually set this up about a month ago. The process was pretty simple:

  1. I set the plugin path in my Pelican configuration file.
  2. I specified the arguments to Pelican I wanted to use.

The only additional tweaks necessary to get citation support were calling it with the
    
    
    --filter pandoc-citeproc

arguments, which lets it process any bibliography data supplied in the header metadata for the files. Calling Pandoc with:
    
    
    --bibliography <path to bibliography>

(as in my example above) is a [shortcut](http://pandoc.org/README.html#citation-rendering) for calling it with:
    
    
    --metadata <path to bibliography> --filter pandoc-citeproc

I could just supply the bibliography directly in the call from Pelican, but this would limit me to using a single bibliography file for _all_ of my posts -- something I'd rather not limit myself to, since it might make sense to build up bibliographies around specific subjects, or even to have smaller bibliographies associated with each project (exported from the main bibliography), which could then be freely available along with the contents of the paper itself. (On this idea, see a bit more below under **The Future**.)

One word of warning: Pandoc is much slower to generate HTML with pandoc-citeproc than _without_ the filter, and the larger your site, the more you will feel this. (The time to generate the site from scratch jumped from about 10s to about 30s for me, with 270 articles, 17 drafts, 2 pages, and 1 hidden page, according to Pelican.) Pandoc has to process _every_ article to check for citations, and that's no small task. However, if you have Pelican's content caching turned on, this is a one-time event. After that, it will only be processing any new content with it; total generation time is back down where it was before for me: the effort is all in generating the large indexes I use to display the content for the landing pages and for category and tag archives.

And the result: that same paper, rendered to HTML [on my website](http://www.chriskrycho.com/2015/not-exactly-a-millennium.html), with citations and works cited, generated automatically and beautifully.

#### Other site generators

I don't know the situation around using Pandoc itself in other generators, including Jekyll -- I simply haven't looked. I do know, however, that there _is_ some tooling for Jekyll specifically to allow a similar workflow. If you're using Jekyll, it looks like your best bet is to check out [jekyll-scholar](https://github.com/inukshuk/jekyll-scholar) and the [citeproc-ruby](https://github.com/inukshuk/citeproc-ruby) project, which (like pandoc-citeproc) enables you to embed citations and filter them through CSLs to generate references automatically. As a note: you should definitely be able to get those working on your own deployment sites, but I have no idea whether it's possible to do them with the GitHub Pages variant of Jekyll. (If anyone who reads this knows the answer to that, let me know on Twitter or App.net or here on Medium, and I'll update the post accordingly.)

### The future

In addition to continuing to use BibTEX with BibDesk as a way of managing my citations in the short term, I'm thinking about other ways to improve this workflow. One possibility is integrating with [Scholdoc](http://scholdoc.scholarlymarkdown.com/) as it matures, instead of [pandoc](http://pandoc.org/), and maybe (hopefully, albeit unlikely) even contributing to it somewhat. I'm also open to using other citation library tools, though my early explorations with Mendeley and Zotero did not particularly impress me.

There are substantial advantages for the applications (and thus for most users) to maintaining the data in an application-specific format (e.g. an SQLite database) rather than on the file system -- but the latter has the advantage of making it much easier to integrate with other tools. However, Zotero and Mendeley both natively export to BibTEX format, and Mendeley natively supports [sync](http://blog.mendeley.com/tipstricks/howto-use-mendeley-to-create-citations-using-latex-and-bibtex/) to a BibTEX library (Zotero can do the same, but via third-party [plugins](https://zoteromusings.wordpress.com/tag/bibtex/)), so those remain viable options, which I may use for future projects.

I also want to look at making my library of resources available publicly, perhaps (a) as a standalone library associated with each project, so that anyone who wants to can download it along with the Markdown source to play with as an example and (b) as a general library covering my various reading and research interests, which will certainly be irrelevant to most people but might nonetheless provide some value to someone along the way. I'm a big fan of making this kind of data open wherever possible, because people come up with neat things to do with it that the original creators never expect. Not _everything_ should be open -- but lots of things should, and this might be among them.

I'm pretty happy with the current state of affairs, the aforementioned interest in other reference managers notwithstanding:

  * I can set up the citations _once_, in a tool designed to manage references, instead of multiple times in multiple places.
  * I can use Pandoc and a CSL to get the citations formatted correctly throughout a paper, including generating the bibliography automatically.
  * I can use the same tooling, integrated into my static site generator, to build a web version of the content -- with no extra effort, once I configured it properly the first time.

Perhaps most importantly, this helps me meet one of my major goals for all my writing: to have a single canonical _source_ for the content, which I will be able to access in the future regardless of what operating system I am using or what publishing systems come and go. Simple plain text files -- Markdown -- get me there. Now I've put good tools around that process, and I love it even more.
