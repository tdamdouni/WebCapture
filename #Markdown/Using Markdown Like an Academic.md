# Using Markdown Like an Academic

_Captured: 2015-11-10 at 20:31 from [www.gradhacker.org](http://www.gradhacker.org/2012/11/20/using-markdown-like-an-academic/)_

![](http://www.gradhacker.org/wp-content/uploads/2012/11/Image-NCReedPlayer-300x201.jpg)

> _Image by Flickr user NCReedPlayer and used under the Creative Commons license._

Markdown, a text formatting syntax designed for easy readability but also transformability, gets a lot of love from geeks. Lincoln Mullen has [written a great introduction to Markdown](http://chronicle.com/blogs/profhacker/markdown-the-syntax-you-probably-already-know/35295) for Profhacker if you are unfamiliar with the syntax. My big question when I made the shift away from traditional word processors and began using plaintext and markdown was if it would be flexible enough to support the conventions of scholarly work. After all, if the format wouldn't support footnotes, tables, figures, and so on, it wouldn't be much use since such conventions are expected across the genres we use in scholarly writing and publishing.

Much of our work involves writing emails, notes, drafts of manuscripts, blogs, ideas, fellowship applications, and so on. Until about year ago, all of this work took place in Microsoft Word. But I increasingly grew frustrated with Word getting in the way of getting my work done. Auto-formatting, proprietary document formats, and its complexity no longer fit my workflow. So, I turned to plain text.

I was part of a larger wave of adoption among Internet nerds who were turning to Markdown as a writing format. Simultaneously, I was making a move between operating systems. I left Windows for Linux, and then Linux for OS X. The shift to another operating system led me to confront the issue of proprietary file formats head on, and further convinced me to pursue plain text for its near universal adaptability to any computing platform.

To get the most out of plain text, I turned to [Fletcher Penny's MultiMarkdown](http://fletcherpenney.net/multimarkdown/), which adds additional features to Markdown especially useful for academics. My last large academic project -- writing my comprehensive exams -- was completed entirely using MultiMarkdown and transformed into file formats I could share with my examiners with John MacFarlane's [Pandoc](http://johnmacfarlane.net/pandoc/).

MultiMarkdown gives writers a greater range of tools for writing more complex material. Footnotes, for example, are represented by [^1] and correspond to the note such as:

> This sentence needs a citation.[^1]
> 
> [^1]: This is the citation.

When the document is converted into PDF, HTML, Word document, or other format, the footnote will appear as expected. If things start getting a little messy, Dr. Drang has a [Python script that will clean up Markdown reference links](http://www.leancrew.com/all-this/2012/09/tidying-markdown-reference-links/). In addition, if you are using Pandoc for transforming text, you can use its flavor of Markdown to do inline footnoting.^[Which looks something like this.]

MultiMarkdown also handles tables, styled like this:


| Left align | Right align | Center align |  
|:-----------|------------:|:------------:|  
| This       |        This |    This      |  
| column     |      column |   column     |  
| will       |        will |    will      |  
| be         |          be |     be       |  
| left       |       right |   center     |  
| aligned    |     aligned |   aligned    |  


I keep a [TextExpander](http://www.smilesoftware.com/TextExpander/index.html) snippet available to create the base table above and then modify as I need. Once again, Dr. Drang has a script that can [clean up Markdown tables](http://www.leancrew.com/all-this/2012/11/markdown-table-scripts-for-bbedit/).

This may all seem complicated, but writing _in_ Markdown is easier than trying to write _about_ it. MultiMarkdown has [many other features](http://fletcherpenney.net/multimarkdown/features/) that academics will find useful, such as math support, image attribution, and figure captions.

_**Have you made the switch to plain text? Have you found Markdown to be useful to your academic workflow?**_
