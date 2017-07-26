# Using markdown + pandoc to write my biology PhD thesis

_Captured: 2015-12-03 at 16:33 from [chiakaivalya.wordpress.com](https://chiakaivalya.wordpress.com/2014/04/23/using-markdown-pandoc-to-write-my-biology-phd-thesis/)_

The last I ever used Microsoft Word for a thesis was 2007. This thesis worked out to something like 50 pages. After page 30, things started getting ugly. Word crashed regularly, attempts at centering one paragraph led to centering of the entire document (followed by yet another crash). Maybe it was because I just had a sucky Windows laptop then… but on the other hand, the results were also quite ugly! For my Master thesis, I tried to do things a little differently. LaTeX was pretty common in my field and produced really nice typeset documents, but I didn't want to bother with LaTeX language for symbols and italics and what not. I know it's probably not that difficult, but it does intrude with the writing process (which is difficult enough as it is!). So in 2008, I turned to [LyX](http://www.lyx.org) for my Master thesis and a couple of grant applications after that. LyX uses LaTeX in the background, and lets you format the final look with LaTeX, but allows you to type in a WYSIWYG document processor. Not too bad an experience.

However, LyX looked a little messy and outdated, and it felt too much like using Word. For my PhD thesis, I wanted to go even simpler (or more complicated, depending how you want to look at it!). My bf introduced me to **[markdown](http://daringfireball.net/projects/markdown/)**, and I saw that others had [used](http://inundata.org/2012/12/04/how-to-ditch-word/) it for [their](http://kieranhealy.org/blog/archives/2014/01/23/plain-text/) [thesis](http://savethevowels.org/essays/markdowndissertation.html) [or](http://recurrentprocessing.blogspot.ch/2013/02/write-academic-papers-with-markdown.html) [papers](http://www.gradhacker.org/2012/11/20/using-markdown-like-an-academic/), and that it was possible to add citations and everything else academics needed, with the help of [pandoc](http://johnmacfarlane.net/pandoc/). It basically uses the power of LaTex to create your document, but you get to concentrate on writing, in a simple text editor. It looked clean and tidy, and appealed to the procrastinating, typography-loving, tools-and-gadgets geek in me. Or maybe I'm just an [academic hipster](http://labandfield.wordpress.com/2013/08/08/beware-the-academic-hipster-or-use-what-works-for-you/).

Anyway, even though there are a couple of how-tos already out there (the best one being [this](http://inundata.org/2012/12/04/how-to-ditch-word/)), I found that I still had to hack around to get my bibliography and greek-letters to work. So I thought I would put my workflow and example files/template here, in case anyone is searching for how to write their PhD thesis in markdown + pandoc.

[Check out the final (example) result](https://www.dropbox.com/s/nl7a2n6khdg8m4p/phdthesis.pdf)

**Tools**

OS: Mac OS X Mavericks

Markdown editor: [Mou](http://mouapp.com) (free, clean layout, but gets a bit laggy after some time and requires a restart)

Bibliography manager: [Papers](http://www.papersapp.com/mac/)

LaTeX editor: [Sublime Text](http://www.sublimetext.com) (for final document typesetting/formatting the pre-amble. I could also have used this for markdown instead of having two separate apps opened, but i couldn't get markdown syntax highlighting to work here and didn't want to waste more time figuring that out!)

Backup + versioning + sharing: [Dropbox](https://www.dropbox.com) (rest in peace knowing there is one local copy and one in the cloud, and all changes are saved as versions in dropbox!)

PDF builder: [pandoc](http://johnmacfarlane.net/pandoc/) via Terminal

![Mou screenshot](https://chiakaivalya.files.wordpress.com/2014/04/screenshot-2014-04-23-19-16-12.png?w=700&h=527)

> _Thesis writing in markdown using Mou_

**How-To**

[Install](http://johnmacfarlane.net/pandoc/installing.html) pandoc and LaTex, and other tools above that you might need.

[Download my template/example files](https://www.dropbox.com/sh/lhs4j30xobylkld/IflvlQx_Gt), or [get them from GitHub](https://github.com/chiakaivalya/thesis-markdown-pandoc).

In Terminal, set the current directory: (Note: Don't use spaces in your folder or file names!)
    
    
    cd /Users/chia/Dropbox/ThesisMarkdownPandoc

Then run this pandoc command to build your pdf:
    
    
    pandoc --latex-engine=xelatex -H preamble.tex -V fontsize=12pt -V documentclass:book -V papersize:a4paper -V classoption:openright --chapters --bibliography=papers.bib --csl="csl/nature.csl" title.md summary.md zusammenfassung.md acknowledgements.md toc.md "introduction/intro1.md" "introduction/intro2.md" chapter2_paper.md chapter3_extra_results.md chapter4_generaldiscussion.md appendix.md references.md -o "phdthesis.pdf"
    
    
    

If you like how it looks, feel free to use my files and play around. Good luck with thesis writing!

[Download the template/example files](https://www.dropbox.com/sh/lhs4j30xobylkld/IflvlQx_Gt)
