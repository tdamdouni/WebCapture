# Writing Mathematical Equations in Ulysses

_Captured: 2016-11-28 at 23:41 from [ulyssesapp.com](https://ulyssesapp.com/blog/2016/11/eline-explains-5/)_

![1480px_eline2@2x-1](http://ulyssesapp.com/blog/wp-content/uploads/2016/06/1480px_eline2@2x-1.png)

_Eline, originally from The Netherlands, is currently doing an English Language and Linguistics Master and is a member of The Soulmen's support team. In her column, she responds to some of the most frequently asked questions and share support answers that could be of interest for more Ulysses users out there._

Ulysses isn't just used by those who write fiction - it is also suited for mathematicians and other scientists that have to include equations in their writing. In this blog post, we will present you with two of the most commonly used workflows: on the one hand, you can use LateX to write your equations, rendering them with Pandoc. On the other hand, you can use MathJax, a powerful web-based script which can render your equations in HTML.

## LaTeX and Pandoc

A well-known way of writing mathematical equations is with [LaTeX](https://www.latex-project.org). This document preparation system uses markup tags, much in the same way as Ulysses does. It has been around since the mid-80's and hasn't lost popularity since. Ulysses lets you write in LaTeX just fine, as long as you wrap it in Raw Source tags. These tags will make sure Ulysses doesn't change your LaTeX code when exporting it. In the screenshot below, the LaTeX equations are contained by `$` signs, and the indexes in subscript are rendered by placing an `_` before them.

![tanimoto-latex](http://ulyssesapp.com/blog/wp-content/uploads/2016/11/tanimoto-latex.png)

After writing these equations, you can export your sheets as Markdown files. Just press `⌘6` to bring up Quick Export and select the "Text" exporter from the top-left menu. Next, select the "Markdown" format and save your sheet.

Now, you will want to render your formulas. This is where [Pandoc](http://pandoc.org/index.html) comes in. Pandoc is the Swiss-Army knife of file conversion. It can read your LaTeX Markdown files and convert them to a host of other filetypes. In order for Pandoc to convert your equations to PDF, please make sure to install [MacTeX](http://www.tug.org/mactex/) as well, a LaTeX distribution for Mac. After this is done, enter this command in your Terminal to convert your LaTeX Markdown file into a PDF:

`pandoc Math.md --output Math.pdf`

In this example, the file was named Math.md, however you can choose any name you'd like. When executing this command, Pandoc will create a PDF file for you, automatically rendering the equations:

![tanimoto-export](http://ulyssesapp.com/blog/wp-content/uploads/2016/11/tanimoto-export.png)

## MathJax

In recent years, [MathJax](https://www.mathjax.org) has gained much attention. Since it's written in JavaScript, it can be rendered by any browser, thus making at a perfect way of showing your equations within Ulysses' Export Preview itself. You can write your MathJax formulas in Ulysses just fine: wrap them in Raw Source tags. You will need to place the following snippet in Raw Source Block tags before your actual formula though:

`<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax: {inlineMath:[['$','$']]}});</script>  
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>  
`

Then write your text and include your formulas in Raw Source tags:

![mathjax-example](http://ulyssesapp.com/blog/wp-content/uploads/2016/11/MathJax-Example.png)

As with LaTeX above, you can use [Pandoc](http://pandoc.org/index.html) to convert your HTML files into almost any other filetype.

Happy exporting!

_Do you have a question about Ulysses yourself? Please don't hesitate to get in touch via our [contact form](http://ulyssesapp.com/contact/), Eline and her colleagues from the Ulysses support will do their best to help you out._
