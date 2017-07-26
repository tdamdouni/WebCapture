# Building Publishing Workflows with Pandoc and Git

_Captured: 2015-12-03 at 15:00 from [publishing.sfu.ca](http://publishing.sfu.ca/2013/11/building-publishing-workflows-with-pandoc-and-git/)_

This fall, I subjected some MPub students to working out a book publishing workflow, using [Pandoc](http://johnmacfarlane.net/pandoc/README.html), the amazing document processor tool created by Berkeley philosopher John MacFarlane.

Pandoc is a remarkably flexible document conversion tool. It takes text input in a variety of _open_ input formats (most usefully [markdown](http://daringfireball.net/projects/markdown/) and HTML) and can convert to more than a dozen outputs, including a variety of web-based formats (HTML, EPUB, markdown, and other blogging markup), word processor formats (RTF and OpenOffice's ODT), and to a couple of TeX-based typeset outputs (that is, to PDF). That's useful, but what makes PanDoc really great is that it works bloody well. It's solid as a rock, totally well organized and documented. In short, the attention to detail in it is really superior.

I say that I "subjected" the students to it, because you run Pandoc almost entirely from the Unix command line. That's a bit of a stretch zone for people raised on the Adobe Creative Suite. But if you're comfy working with the shell (and even moreso if you're happy with shell scripts) it is stunningly efficient.

We started by using Pandoc to build EPUB files from a set of markdown text files. This is simple like falling off a log:
    
    
    pandoc file1.txt file2.txt file3.txt  -t epub  -o file.epub

A little more sophisticated, you can pass it (again on the command line) your tailor-made CSS file, plus a file full of [DC-style metadata](http://dublincore.org/documents/dces/), and it will make the EPUB accordingly. It builds the EPUB by breaking it up on first-level heads (or a different level, if you tell it to), creates the spine and table of contents, and does it all pretty much exactly perfectly.

Next step was to create a printed book from the same source. Pandoc can create typeset output via the venerable TeX typesetting system, either in the popular LaTeX format and also in the newer, more typographically flexible [ConTeXt](http://wiki.contextgarden.net/What_is_ConTeXt) flavour.

This makes a TeX file ready to typeset with ConTeXt:
    
    
    pandoc -s --chapters file1 file2 file3  -t context  -o book.tex

Then you just run ConTeXt on it (everyone has TeX installed, right?)
    
    
    context book.tex; open book.pdf

Pandoc is smart enough to fix up typographers' quotes, em-dashes, and so on. Furthermore, it builds these outputs based on a set of templates that are easily hackable. For instance, we were able to set up all the page layout details (facing pages, margin widths, running heads, typeface, etc) by tweaking Pandoc's default ConTeXt template before running the conversion.

I'm not really convinced TeX is the future of publishing (insert sardonic laughter here), but that's not the point. Pandoc merely comes out of the box able to produce TeX. But any of the new crop of CSS-based page-rendering tools are directly usable, because of course Pandoc produces HTML too. (I have a weirdly retrotech idea that we could do typesetting with groff. For regular prose, groff is every bit as powerful as TeX, while being about one tenth the size and complexity.) Pandoc already knows how to output Unix 'man' pages via groff, so it's just a matter of swapping out the 'man' page macros for a proper typesetting set like Peter Schaffter's [mom macros](http://www.schaffter.ca/mom/).) Or you could go to a [pathway to InDesign's ICML format](http://code.google.com/p/ickmull).

More recently, I have been mucking about with Pandoc as a way of producing presentation slides. Pandoc features at least _three_ different HTML-based slideshow options. Again, by hacking Pandoc's template for its slideshow output, we can add custom stylesheets and whatnot, and have a basically automated presentation-builder, starting from markdown source. Because Pandoc writes a unique html id on each slide (as a div or a section), it's straightforward to link up background images to each individual slide--just a couple of text files holding the whole thing together.
    
    
    pandoc -s -t dzslides slides.txt -o slideshow.html

## Managing Content with Git

So far, I've been talking about a standalone system, with one user on one computer--usable on your laptop, on your lap. But what about a scaled-up project with more people and some centralized services?

[Git](http://git-scm.com/) is a hugely popular "distributed version control system" designed to manage teams of programmers working on a common collection of source code files. Source code is made of text files, so it doesn't take much of a leap to see that Git can manage the kinds of text files I'm talking about here as well.

A Git _repository_ (or "repo") is a collection of files managed by Git. By collection, I just mean a folder (or a set of folders and subfolders). Git manages all the changes to those files: who did what when. It keeps a fine-grained revision history, and also does a pretty reasonable job of merging edit conflicts (if two people edit the same file). Git is another Unix command line tool at heart, so a handful of shell commands allow you to do things like pull a local copy of the repo, commit changes to it, and push your changes back to the master copy. As with all these things, the good old Unix philosophy of "small pieces loosely joined" applies.

The piece that makes this really handy for an editorial workflow is another tool by Pandoc's creator, John MacFarlane, called [Gitit](http://gitit.net/). Gitit is a wiki, designed in the best possible way: as minimal as possible. Gitit is essentially a Git repository (one file per wiki page) with Pandoc sitting on top as the rendering engine. The wiki layer does little besides providing a web interface to the whole thing, handling access control (via password logins), and allowing quick wiki links between pages.

A Gitit wiki is, therefore, just a Git repository with a wiki interface. You can edit the files wiki-style, in which case the wiki takes care of committing your changes to Git. Or you can edit the files directly as text files, in which case you explicitly commit your changes to the repo. This may sound like a pretty dull technical detail, but it's actually wickedly useful in practice.

For instance, using the wiki as a content management system (CMS) provides one centrally managed content store in a friendly package. I've written before about [using wiki as a CMS](http://tkbr.ccsp.sfu.ca/bits/onWikis/Maxwell2008-CW-WhatCantYouDoWithWiki.pdf), that the complete absence of technical features in a wiki pushes all the adminstrative tasks back into the _editorial_ sphere, which is where they belong. So a great deal of editorial work can be done straight through the web-native wiki interface--especially the many short, incidental passes through the material. Here, the versioning gets handled automatically by the wiki engine.

But for more engaged, deliberate work, like serious writing and editing passes, you can go straight to the text files, open them up in a full-featured text editor, and spend hours in the text. Or, you'd work on a local copy and let Git syncronize your copy with the master.

Similarly, production work can draw from the files in the repo directly. Those long, chained up Pandoc commands shown above can be run directly on the files in the repo (or your local copy). It's like having a friendly front door and a rear, service entrance on the same content repository.

The fact that the Git repo is also a website by virtue of the wiki layer Gitit provides, means that in practice, I can work on a set of local files, and then "publish" to the web whenever I choose to syncronize with the Git repo on the server. And of course, Git is specifically designed to facilitate exactly this sort of interaction across large project teams, ensuring that everyone stays in sync with everyone else.

Further, via the Pandoc steps shown above, we can push the repository out to various digital, print, or slideshow (etc., etc.) outputs, on demand, with a few keystrokes

The tools I've been describing here--Pandoc, Git, and Gitit--are pretty sophisticated bits of software. But it's important to appreciate that what really makes this kind of workflow integration work is the Unix architecture underneath--a uniform interface to collections of text files, and standard means of inputting, processing, and outputting files. Unix was designed to do this 40 years ago, and has evolved over that time to be a pretty bulletproof system. And because Unix is nearly everywhere, these tools work nearly everywhere. The workflows described above work on my MacBook, on my Ubuntu servers and workstations, and in practice stretch across these platforms: I have Git and Pandoc running everywhere, and I sync my files across these systems. The Gitit wiki runs on our webserver, providing an easy web interface to all of it, readily available anytime.

The strategies described here are a long way from what most publishing professionals would recognize as editorial or production practices. Indeed, this way of working trades the comfortably visual approach of Desktop Publishing software for the efficient "pipelining" approach of Unix, chaining combinations of specific tools together for particular ends. It is worth noting too that all the software mentioned here is free and open source.
