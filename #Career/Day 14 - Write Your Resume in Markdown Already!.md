# Day 14 - Write Your Resume in Markdown Already!

_Captured: 2015-11-28 at 09:54 from [sysadvent.blogspot.de](http://sysadvent.blogspot.de/2011/12/day-14-write-your-resume-in-markdown.html)_

This was written by [Phil Hollenback](http://www.twitter.com/philiph) ([www.hollenback.net](http://www.hollenback.net))

Like most of you, I hate dealing with my resume. That means I don't keep it as current as I should. Over the years, I've kept my resume in all sorts of formats: straight text, nroff, TeX, etc. I think I might have even handcrafted a postscript resume once.

However, I got so tired of recruiters always asking for a Word version of my resume that somewhere along the way I gave up and wrote one in Word (probably OpenOffice now that I think about it). I saved that as a pdf and an html version and forgot about it. That seemed to work ok since I've been gainfully employed for the last decade or so.

However, I recently got a promotion at work so I decided it was time to revisit my resume. Frankly it was a little embarrassing as much of my resume was no longer particularly current or relevant. Does anyone really care that I once worked as a Tcl programmer? Also there's probably no real need for me to list jobs from 10 years ago that I barely remember. Thus, I decided to rewrite my resume.

Speaking of promotions, I often see folks only maintaining their resumes when considering job changes, but you should keep it updated! A record of accomplishments at your current job is useful in times of performance reviews or promotion consideration. For company internal things, you can maintain an internal company resume.

## Selecting a Markup Language

You sysadmins can see where this is going: I used my resume rewrite as an excuse to try new tools. Specifically, I wanted to answer the question of how a system administrator should be managing their resume in 2011. I decided on a few criteria:

  * human-readable source format  

    * I should be able to look at the original document and understand it. That presumably means straight ASCII text.
    * (yes I know that's US English only).
    * This also eliminates the 'oops, my deleted text is still in the file' problem with Word.
  * PDF output  

    * PDFs seem the most portable way to exchange documents and ensure that formatting remains intact.
  * HTML output  

    * I want a version of my resume I can post on a website.
  * Open-source tools  

    * No lockdown in proprietary formats.
  * the _cool factor_  

    * I wanted something fresh and interesting that I could (for example) blog about.

With these constraints, it was pretty clear I'd have to choose something like [Markdown](https://en.wikipedia.org/wiki/Markdown) or [TeX](https://en.wikipedia.org/wiki/TeX) for the my source document and then figure out a way to convert those to various output formats.

I have some experience writing TeX / LaTeX documents, and I knew that would probably be sufficient. For example, I knew I could convert TeX into HTML and PDF fairly easily.

However, while TeX files are somewhat human-readable, they aren't really presentable in that format. The big advantage of formats such as Markdown is that the source document can stand on it's own. That way if I needed an ASCII version of my markdown document I could just use the source file. That wouldn't work for TeX.

As I mentioned, I wanted to try something interesting and fairly new for this exercise, and Markdown certainly is the lightweight markup language of choice these days. Lots of blogging tools support Markdown as a native format, so if I pasted chunks of my resume onto websites they would magically [show up as formatted text](http://liresume.blogspot.com/2010/12/pro-tip-format-your-resume-using.html).

Finally, Markdown has _momentum_. There are lots of other perfectly good alternatives like [textile](https://en.wikipedia.org/wiki/Textile_%28markup_language%29) and [reSTructured Text](https://en.wikipedia.org/wiki/Restructured_text). However, none of them are the default [markdown language on github](http://github.github.com/github-flavored-markdown/).

## Tools

I'm a hardcore emacs user so I knew I wanted to write my markdown in Emacs. Naturally there's a [Markdown mode for Emacs](http://jblevins.org/projects/markdown-mode/). I run Emacs 23.3.1 on my Mac, by the way, and I recommend it. Getting markdown-mode running was as simple as copying the .el file and adding a few bits to my .emacs:
    
    
    (autoload 'markdown-mode "markdown-mode.el"
      "Major mode for editing Markdown files" t)
    (setq auto-mode-alist
       (cons '("\\.md" . markdown-mode) auto-mode-alist))
    

Once that was installed I could open a `.md` file, make my edits, and preview it as html in my browser with a simple `C-c C-c p`.

Next I tackled the problem of converting markdown to pdf. Luckily [Brandon Burton](http://twitter.com/solarce) happened to mention the free markup converter [Pandoc](http://johnmacfarlane.net/pandoc/) on a mailing list I subscribe to. Pandoc comes with a [markdown2pdf](http://johnmacfarlane.net/pandoc/README.html#markdown2pdf) script. Based on the name of that script I was pretty sure pandoc could do what I needed.

I installed pandoc from [macports](http://www.macports.org), and I should mention that I also had TeX installed from the same source. This is important because pandoc uses TeX in the markdown->pdf pipeline.

## Constructing A Resume

Now that I had some tools for creating and processing Markdown documents, I needed to figure out how to structure my resume in Markdown. For this I just stared googling "markdown resume" until I found something I liked. [Nathaniel Welch's resume](http://icco.github.com/Resume/) is an excellent place to start. I ended up using a similar although somewhat simplified design. I basically just used standard headers and paragraphs all the way down: my name in the largest header size, major headings one size smaller, etc. Something like this:
    
    
    # Philip J. Hollenback
    
    philiph@pobox.com
    
    ## Overview
    
    I do stuff.
    
    ## Experience
    
    ### SysAdvent, On The Interwebs
    
    #### Blogger, 2010 to present
    
    Wrote some awesome and some mediocre SysAdvent articles.
    

et cetera, et cetera. Note that you should consider using [reference links](http://daringfireball.net/projects/markdown/syntax#link) for readability as this puts the links at the end of your Markdown document for a more natural text flow.

## Generating Output

### TeX Time

Once you have your resume written in Markdown, it's time to produce some output. I put my `resume.md` file in a separate `resume` directory and wrote a makefile to handle generating the html and pdf versions. I'll go over that later in this article.

To generate a pdf from my markdown source, I first tried this:
    
    
    markdown2pdf resume.md
    

which produced a usable pdf file, but there were some problems:

  * there was a page number at the bottom of every page
  * the margins were much too large
  * the font looked like garbage when I printed the pdf file

After reading the pandoc documentation and [researching on the web](https://github.com/mwhite/resume) I figured out how to fix the first two problems. You just need to include a TeX header file to control how the output gets generated. Here's a good starting point for that header:
    
    
    \usepackage[top=1in, bottom=1in, left=1.25in, right=1.25in]{geometry}
    \pagestyle{empty}
    

That gave me a resume with much more narrow margins, and turned off the page numbers. All I had to do was include the header file when running markdown2pdf:
    
    
    markdown2pdf -o resume.pdf -H header.tex resume.md
    

that fixed all my problems except the ugly font. Fixing that turned out to be a little more complicated: I had to turn on XeTeX and create an entirely new output template. That's the only way I could find to easily select new fonts for TeX on my mac. I'm hoping people who read this have better solutions.

I ran `fc-list` to find all my available system fonts. I ended up using that delightful old standard, Times New Roman.

Next, I dumped out the LaTeX template that pandoc uses by default to use as a starting point:
    
    
    pandoc -D latex > resume-template.tex
    

and modified that file to incorporate my header changes and add font selection to the xetex section. I also forced the font size to 11 points:
    
    
    @@ -1,9 +1,16 @@
    -\documentclass$if(fontsize)$[$fontsize$]$endif${article}
    +\documentclass[fontsize=11pt]{article}
     \usepackage{amssymb,amsmath}
    +
    +\usepackage[top=1in, bottom=1in, left=1.25in, right=1.25in]{geometry}
    +\pagestyle{empty}
    +
    $if(xetex)$
     \usepackage{ifxetex}
     \ifxetex
     \usepackage{fontspec,xltxtra,xunicode}
    +  \setmainfont{Times New Roman}
    +  \setsansfont{Verdana}
    +  \setmonofont{Courier New}
     \defaultfontfeatures{Mapping=tex-text,Scale=MatchLowercase}
     \else
     \usepackage[mathletters]{ucs}
    

(you can [download the full template from my website](http://www.hollenback.net/personal/resume-template.tex)).

The final step was to use the `\--xetex` option to `markdown2pdf` to use xetex and enable my custom font. My markdown2pdf invocation thus became:
    
    
    markdown2pdf --template=resume-template.tex --xetex resume.md
    

the end result of this is a [nice clean pdf file](http://www.hollenback.net/personal/resume-phil.pdf). Compare this to the [original Markdown](http://www.hollenback.net/personal/resume-phil.md).

### HTML

The final piece of the output puzzle is HTML. Convert the markdown to html by invoking pandoc directly:
    
    
    pandoc -o resume.html resume.md
    

That results in a serviceable but not very attractive html file. Fortunately pandoc allows you to also use a css file to change the html output. I used [Michael White's css file](https://github.com/mwhite/resume) as starting point and tweaked the colors slightly. Then, I invoke pandoc as follows:
    
    
    pandoc -t html -o resume.html -c resume.css resume.md
    

You can see the final result [on my website](http://www.hollenback.net/personal/resume-phil.html). I'm quite happy with the fit and finish.

### Automation

No SysAdvent article is complete without a section on automation. To wrap this whole thing together, I [wrote a makefile](http://www.hollenback.net/personal/Makefile) (as I mentioned earlier). I also wrote a perl script to automatically update my resume files on my website when they changed. First, the makefile:
    
    
    all:    resume.html resume.pdf
    
    %.html: %.md
        pandoc -t html -o $@ $< -c resume.css
        ./resume-uploader $@ $< resume.css
    
    %.pdf:  %.md
        markdown2pdf --template=resume-template.tex --xetex $<
        ./resume-uploader $@ $< resume-template.tex
    
    clean:
        rm -f *~ *.html *.log *.pdf
    

The perl script is a bit too long to post here, but you can find it [on my website as well](http://www.hollenback.net/personal/resume-uploader). This script takes a filename as input, and checks if the file exists on the server. If it exists and the version on the server is older than the one just generated, the script uploads the file. Note that authentication is handled via the `.netrc` file.

Now I have a one-stop mechanism for updating my resume. I just load up my `resume.md` file in emacs and use markdown-mode to edit it. I can hit `C-c C-c p` at any time to view it in html in my browser. When I'm happy with the contents, I run my makefile with `C-x C-k` to build fresh html and pdf versions. Finally, the uploader script uploads the new versions of my resume and support files to my website as appropriate.

Another enhancement to consider is putting this whole thing in git and hosting it on [github pages](http://pages.github.com/) (did I mention that github supports Markdown as a native format)?

## Conclusion

So there you have my account of how I converted my resume to Markdown. In general, I'm very pleased with this approach: I get the simplicity of a text source file combined with decent HTML and PDF output. With a little bit of sysadmin-compatible automation, I've turned this whole thing in to a repeatable workflow. The best thing about this approach is the flexibility. If I want to host my resume on github, it's ready to go. If I want to change my fonts or html output, I just have to make a few simple changes to the input files. Most importantly, I'm not locked in to a proprietary format like Microsoft Word.

If you are interested in using my resume as a starting point for your own, I suggest you consider some [hardcore github forking action](https://github.com/tels7ar/resume).

## Further Reading

  * This one got me started: [icco's markdown resume on github](https://github.com/icco/Resume/blob/master/resume.md).
  * Ycombinator: [maintain your resume on github with markdown](http://news.ycombinator.com/item?id=1863688).
  * edrex has a [markdown resume on github](https://github.com/edrex/resume) that include html css so it renders nicely for the web via pandoc.
  * mwhite's [markdown resume on github](https://github.com/mwhite/resume) \- includes css _and_ a tex header so both formats render similarly.
  * Here's some [pandoc templates](https://github.com/claes/pandoc-templates) that illustrate how to override tex fonts.

_Editor's note_: This year's sysadvent posts are all written in markdown. They are converted them to HTML using pandoc for publishing on Blogger.
