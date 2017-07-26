# Markdown Resume

_Captured: 2015-12-01 at 02:47 from [arturoherrero.com](http://arturoherrero.com/markdown-resume/)_

A few weeks ago I needed to update my curriculum vitae. When was the last time that you composed your cv? The last time I had to updated it, I was using a completely different stack. I remember having used Microsoft Office Word.

Now my options are an online editor, LaTeX or [Markdown](http://daringfireball.net/projects/markdown/). I love to write in Markdown and I like to create my own tools so I decided to craft a tool to do the job.

### Biteydown

[Biteydown](https://github.com/arturoherrero/biteydown) is Ruby application that turns a simple Markdown document into a resume in HTML or PDF file.

####  Instalation
    
    
    bundle install
    

#### Usage
    
    
    Usage: biteydown [options] file
            --html                       Create HTML file
            --pdf                        Create PDF file
        -h, --help                       Display help
    
    $ bin/biteydown --html --pdf example/curriculum.md
    

#### Style

You can customize the look and feel of text and headings in your document using the `style/style.css` file. First is transformed the Markdown document to HTML file and then apply the style. It's a little bit hacky, but works fine.

Markdown is a lightweight markup language designed as an easy-to-read, easy-to-write plain text format and then convert it to structurally valid HTML; therefore, CSS selectors can be used to customize the curriculum.

![CV CSS Selectors](http://arturoherrero.com/assets/images/cv-css-selectors.png)

> _CV CSS Selectors_

CSS works by associating rules with HTML elements. In this case, there are a little group of selectors that can be used: `h1-h6`, `blockquote`, `a`, `li`, `code`, `strong`, `em`, `img`. You cannot use id or class selectors to create rules that apply to elements.
