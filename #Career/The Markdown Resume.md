# The Markdown Resume

_Captured: 2015-11-28 at 10:07 from [mszep.github.io](http://mszep.github.io/pandoc_resume/)_

Maintaining a resume is one of those annoying tasks that always takes up much more time than it should. Compounding this is the fact that resumes are regularly requested in different formats: raw text, pdf, Microsoft Word, etc. In addition, it might be desirable to have a HTML version online somewhere for added visibility. How then to manage this complexity? No one wants to manually update four versions of their resume, and the pdf conversion tools included with word processors leave much to be desired.

Christophe-Marie Duquesne has a great [blog post](http://blog.chmd.fr/editing-a-cv-in-markdown-with-pandoc.html) in which he shows that using the document translation tool [pandoc](http://johnmacfarlane.net/pandoc/), you can maintain your resume in [markdown format](http://daringfireball.net/projects/markdown/syntax) and convert to other formats such as html and Word at will.

This is convenient because:

  * It means there is only one file you need to update to make any changes.
  * Markdown is designed to be human-readable, so if you need a raw text version of your resume, no transformation is needed.
  * Markdown has syntax for section headers, lists, tables and more, so you can add as much structure as you want to your resume.
  * Being a format designed (partly) for human consumption and creation, it is also an appropriate format to keep in version control.

This is what a simple resume in markdown format looks like:

Johnny Coder

============

\------------------- ----------------------------

1 MyAddress email@example.com

MyTown 1000 @twitter_handle

MyCountry 1800 my-phone-nr

\------------------- ----------------------------

Education

\---------

2010-2014 (expected)

: **PhD, Computer Science**; Awesome University (MyTown)

*Thesis title: Deep Learning Approaches to the Self-Awesomeness

Estimation Problem*

2007-2010

: **BSc, Computer Science and Electrical Engineering**; University of

HomeTown (HomeTown)

*Minor: Awesomeology*

Experience

\----------

**Your Most Recent Work Experience:**

Short text containing the type of work done, results obtained,

lessons learned and other remarks. Can also include lists and

links:

* First item

* Item with [link](http://www.example.com). Links will work both in

the html and pdf versions.

**That Other Job You Had**

Also with a short description.

Technical Experience

\--------------------

My Cool Side Project

: For items which don't have a clear time ordering, a definition

list can be used to have named items.

* These items can also contain lists, but you need to mind the

indentation levels in the markdown source.

* Second item.

Open Source

: List open source contributions here, perhaps placing emphasis on

the project names, for example the **Linux Kernel**, where you

implemented multithreading over a long weekend, or **node.js**

(with [link](http://nodejs.org)) which was actually totally

your idea...

Programming Languages

: **first-lang:** Here, we have an itemization, where we only want

to add descriptions to the first few items, but still want to

mention some others together at the end. A format that works well

here is a description list where the first few items have their

first word emphasized, and the last item contains the final few

emphasized terms. Notice the reasonably nice page break in the pdf

version, which wouldn't happen if we generated the pdf via html.

: **second-lang:** Description of your experience with second-lang,

perhaps again including a [link] [ref], this time placing the url

reference elsewhere in the document to reduce clutter (see source

file). 

: **obscure-but-impressive-lang:** We both know this one's pushing

it.

: Basic knowledge of **C**, **x86 assembly**, **forth**, **Common Lisp**

[ref]: https://github.com/githubuser/superlongprojectname

Extra Section, Call it Whatever You Want

\----------------------------------------

* Human Languages:

* English (native speaker)

* ???

* This is what a nested list looks like.

* Random tidbit

* Other sort of impressive-sounding thing you did

However, in the above approach the generation of a pdf version (arguably the most important) is problematic. The suggestion is to use the [wkhtmltopdf tool](http://wkhtmltopdf.org/), which takes the pandoc-generated HTML and uses the webkit browser engine to generate a pdf. While this will preserve the look and feel of the resume, the pdf output is suboptimal, as webkit is not a typesetting engine. Most importantly, it does not handle page breaks well -- in some cases even putting a page break right across a line of text.

On the other hand, TeX-based typesetting systems are designed for this task. Moreover, pandoc supports two types of TeX output: LaTeX and [ConTeXt](http://wiki.contextgarden.net/). I chose the latter since it seemed interesting, is more focused on page layout, and is not specifically geared towards scientific documents. Through trial and error, I was able to create a style.tex which comes close to emulating Christophe-Marie's style.css, resulting in a nicely typeset pdf resume which looks quite similar to the HTML:

[HTML version](http://mszep.github.io/pandoc_resume/resume.html) of the resume:

The repository is [here](https://github.com/mszep/pandoc_resume) (pull requests welcome!), and it includes a Makefile, so the instructions to make your own resume are:
    
    
    git clone https://github.com/mszep/pandoc_resume
    cd pandoc_resume
    vim resume.md   #insert your own resume info
    make

You will need both pandoc and ConTeXt installed on your system, which on Debian and derivatives can be achieved with
    
    
    sudo apt-get install pandoc context
