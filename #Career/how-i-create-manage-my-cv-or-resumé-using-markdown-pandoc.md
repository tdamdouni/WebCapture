# How I create & manage my CV (or resumé) using Markdown & Pandoc

_Captured: 2016-12-21 at 19:08 from [www.chainsawonatireswing.com](https://www.chainsawonatireswing.com/2013/05/28/how-i-create-manage-my-cv-using-markdown-pandoc//?from=@)_

It's a fact of life: everyone needs a resume. But if you're in academia, you also need a _[curriculum vitae](http://en.wikipedia.org/wiki/Curriculum_vitae)_, more commonly known as a CV. [Wikipedia defines it](http://en.wikipedia.org/wiki/Curriculum_vitae) this way

:

> In the United States and Canada, a CV is used in academic circles and medical careers as a "replacement" for a resume and is far more comprehensive … A CV elaborates on education to a greater degree than a resume and is expected to include a comprehensive listing of professional history including every term of employment, academic credential, publication, contribution or significant achievement.

CVs tend to be long & complicated documents. When I started out 15 years ago or so, I did what most people do at first: I used Word. I very quickly realized that Word was going to be a terrible, bloated tool for the job, & it also concerned me that I'd be locking up an important file in a proprietary format. I also tried OpenOffice.org, but it still felt bloated & overly complex to me.

Then it hit me: use HTML! I code it by hand & teach it, so creating a CV in HTML (with a splash of CSS) wouldn't be that hard. And that's what I've done for the last 10 years or so, & I very quickly learned to hate it. Here's why:

  * Editing a long, complicated HTML document is no fun (& no, I'm not going to use a WYSIWYG--that's for wimps).
  * Because it was a pain to edit, I rarely updated my CV (& I really should--I give a lot of talks).
  * Re-ordering sections was arduous.
  * Printing to PDF was also a pain. Basically, I would open the HTML file in Firefox (because it's the only browser on Mac OS X that allows you to customize the header & footer), change the header & footer, print, then change the header & footer back.
  * Because it was a pain to print to PDF, I rarely did so.

I finally said "Enough!" & decided I needed to try something else. But what? My goals were:

  * Easy to edit, which would encourage more frequent updating
  * Easy to re-arrange and re-emphasize sections of the CV
  * Not to depend in any way on proprietary formats or software
  * Quick to produce output, especially in PDF

After some cogitation, it hit me: Markdown documents that are converted & arranged using Pandoc, the "general markup converter" & Swiss army knife of markup documents. After a few days of fiddling, I got it to work, & it works _well_, perfectly meeting all of my goals (you can see sample output at the very end of this post).

This is a long post, but it's actually a pretty simple system once you try it. I know this works on a Mac, & it would be trivial to set it up on a Linux box. If you use Windows, the bash shell script that does the work will obviously not run unless you install something like [Cygwin](http://www.cygwin.com).

Let's jump in & learn how to generate a CV (or resume, if you really wanted) using Pandoc & Markdown!

## Table of Contents

## Pandoc

For this whole scheme to work, you have to first install Pandoc. Easy enough--just head over to <http://johnmacfarlane.net/pandoc/installing.html> & download Pandoc. It comes with a nice installer, so in no time you should be finished with that task. On my Mac, the `pandoc` binary is installed at `/usr/local/bin/pandoc`, & I have the following in my `~/.profile` so it's in my PATH:
    
    
    export PATH=/usr/local/bin:$PATH

## Directory Structure

I'm assuming you create the following two folders in your home directory:

You can put the directories someplace else more to your liking, but then you're going to have to make some changes to my script below.

## Markdown

I'm assuming you already know Markdown & have a text editor to write it in. For my CV, I created the following files in `~/CV/Builds/`:

  * articles.md
  * books.md
  * clients.md
  * cv.md
  * description.md
  * education.md
  * experience-business.md
  * experience-teaching.md
  * experience-writing.md
  * interviews.md
  * organizations.md
  * presentations.md
  * references.md
  * skills.md
  * training.md

Of these, `cv.md` is required. The others are optional, depending upon your needs.

### `cv.md`

Place the following inside `cv.md`:
    
    
    # R. Scott Granneman
    
    39 Summit Place • Webster Groves, MO 63119  
    scott@granneman.com • www.granneman.com • www.ChainsawOnATireSwing.com  
    314-780-0489 (c) • 314-644-4900 (w)

Note there are 2 spaces to create a line break after the ZIP & the URLs, & a blank line after the phone numbers. Oh, and those dots are created by pressing Command+8 on a Mac.

This is all you put in `cv.md`. Everything else is broken up into the other files. Let's look at a few of those so you get the idea of what to put in them.

### `description.md`

A very optional section, this is the very first thing that will appear after the contact info in `cv.md`. In my case, it's a brief four paragraph long summation of my background & skills. It's pretty simple Markdown, as you can see in this truncated example:
    
    
    Scott Granneman is an author, educator, and small business owner. 
    
    Scott has written five books, co-authored one, and contributed to two. …
    
    As an educator, Scott has taught thousands of people of all ages on a wide variety of topics. …
    
    As a Principal of WebSanity, he works with businesses and non-profits …

Nothing special here, except that there is no header to introduce this section, as I want it to flow right after the previous info.

Now on to actual labeled sections in the CV.

### `education.md`

This is one of the key sections in any CV (or resume): your educational background. My case is kind of weird: I got my B.A. & M.A at the same university & then worked for another 5 years on a Ph.D. there to boot!
    
    
    ## Education
    
    **Washington University in St. Louis**
    
    Ph.D. course work, 17th Century British Literature, 1990–1995
    
    M.A., English, 1989–1990 (2005)
    
    B.A., 1985–1989  
    Majors: English Literature, Education  
    Minor: History

I use simple bolded text to distinguish the university, which would obviously be even more helpful if there was more than one university to list! Again, there are two spaces after each of the first two lines in the B.A. block to create line breaks.

### `articles.md`

This part of my CV lists all the articles I've written (duh). Here's the relevant Markdown, greatly truncated.
    
    
    ## Publications: Articles
    
    Links to articles available at http://www.granneman.com/writing/.
    
    “In the Cockpit of JetS3t”  
    *Linux Magazine* (June 2007): 10
    
    “Security Analogies”  
    SecurityFocus (29 May 2007)
    
    “Vista Outsmarts Linux”  
    *Linux Magazine* (April 2007): 28-31, 52
    
    “Surprises Inside Microsoft Vista’s EULA”  
    SecurityFocus (27 Oct. 2006)

Again, the section name uses a level 2 header. Also, there are two spaces for a line break after each article title.

You might notice I'm not converting the link at the top into a clickable URL. I didn't do that because the eventual home of this document is going to be a PDF, & I didn't want any links to show up in that document (I just think they'd distract & look ugly in that format).

### `experience-business.md`

I work in three areas--education, writing, & business--so my CV has to cover everything I've done in all of them. Instead of running all my various work experiences together in one long, mixed-together list, I broke things up into 3 documents:

  * `experience-business.md`
  * `experience-teaching.md`
  * `experience-writing.md`

Breaking things up into 3 documents makes it easier to update the files, & also makes it easy for me to re-order things. If I'm applying for a teaching position, then `experience-teaching.md` goes first; if I'm delivering a talk to a group, I'll usually put `experience-business.md` first; & if a publisher needs validation, then I move `experience-writing.md` to the front.

Here's what `experience-business.md` looks like:
    
    
    ## Professional Experience: Business {#experience-business}
    
    WebSanity, St. Louis  
    Principal, 2001–Present
    
    * Create dynamic websites using a Content Management System which allows non-technical end users to manage content on their own websites
    * Administer UNIX-based Linux & Mac OS X servers
    * Write bash shell scripts to perform maintenance tasks
    * Wrote & maintain 200+ page help manual for clients
    
    Atisma Technologies, Inc., St. Louis  
    President & Chief Application Officer, 1999–2001
    
    * Created Virtual Registrar, world’s first fully Web-based school information system delivered via the Application Service Provider model
    * Co-founded 12-person company to develop & serve the software
    * Wrote requirements documents describing application in detail for developers’ use

After each business & location, there are 2 spaces to create a line break. Other than that, it's a lot of bulleted lists.

## CSS

You'll need to use Cascading Style Sheets for the HTML output (although they're ignored by the PDF output). I created a file named `granneman.css` in `~/CV/Builds/` that contained the following:
    
    
    <style>
      body {
        font-family: "Source Sans Pro", "Lucida Grande", Calibri, Helvetica, sans-serif;
      }
      h1 {
        font-size: 2.5em; 
        margin-bottom: 10px;
      }
      li {
        margin-bottom: .3em;
      }
    </style>

There's not much to this file. Most of it is just to make the generated HTML look nice & readable.

## LaTeX

To generate the PDF, Pandoc uses [LaTeX](http://en.wikipedia.org/wiki/LaTeX). As part of that process, Pandoc allows you to include a custom preamble in the output that controls what appears in the PDF. Now, I don't know much about LaTeX (though I'd sure like to learn more), but I was able to figure enough out to get the output I wanted.

To do it, I created a file named `granneman.tex` in `~/CV/Builds/` that contained the following:
    
    
    \usepackage[top=1in, bottom=1in, left=1in, right=1in]{geometry}
    
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \pagenumbering{arabic}
    \lhead{\itshape R. Scott Granneman}
    \chead{}
    \rhead{\thepage}
    \lfoot{}
    \cfoot{\today}
    \rfoot{}
    
    \thispagestyle{empty}

Let me walk through the important options I set in the file:

  * `\usepackage[top=1in, bottom=1in, left=1in, right=1in]{geometry}`  
I found that the default margins were too big, so I reduced them to 1 inch on all 4 sides.
  * `\lhead{\itshape R. Scott Granneman}`  
This prints my name in the top left of the header in italics, except for the first page.
  * `\rhead{\thepage}`  
This prints the page number in the top right of the header, except for the first page.
  * `\cfoot{\today}`  
This prints today's date in the center of the footer, except for the first page. The format is like this: `May 25, 2013`.

## The shell script

I created a shell script named `cv.sh` & put it in `~/bin`. I think it's well-commented, but I'll cover anything that might not be totally clear after the listing.
    
    
    #!/bin/bash
    
    #=====================================================================
    #          FILE:  cv.sh
    #         USAGE:  Run manually to generate my CV
    #   DESCRIPTION:  Uses Pandoc to pull together Markdown documents
    #                 & process them with Pandoc to generate my CV
    #        AUTHOR:  Scott Granneman (RSG), scott@ChainsawOnATireSwing.com
    #       VERSION:  0.2
    #       CREATED:  05/11/2013 11:50:30 CDT
    #      REVISION:  05/15/2013 09:59:30 CDT 
    #=====================================================================
    
    ###
    ## Variables
    # 
    
    # Directory for CV
    cvDir=/Users/scott/CV
    
    # Directory for CV Builds
    cvBuildDir=/Users/scott/CV/Builds
    
    # Name of the CV file
    cvName="Scott Granneman - CV - $(date +%Y-%m-%d)"
    
    ###
    ## Create HTML files for each Markdown file
    # 
    
    for i in $(ls $cvBuildDir/*md) ; do
      echo $i
      # Get the name of the file, sans extension, for generating HTML file
      cvBuildName=$(basename "$i" .md)
      # Convert to HTML
      pandoc --section-divs -f markdown -t html5 -o $cvBuildDir/$cvBuildName.html $i
    done
    
    ###
    ## Join the HTML files into one HTML CV
    # 
    
    pandoc -s -H $cvBuildDir/granneman.css --section-divs -f markdown -t html5 \
    -o "$cvDir/$cvName.html" \
    -A $cvBuildDir/description.html \
    -A $cvBuildDir/education.html \
    -A $cvBuildDir/experience-teaching.html \
    -A $cvBuildDir/experience-writing.html \
    -A $cvBuildDir/experience-business.html \
    -A $cvBuildDir/books.html \
    -A $cvBuildDir/articles.html \
    -A $cvBuildDir/presentations.html \
    -A $cvBuildDir/interviews.html \
    -A $cvBuildDir/training.html \
    -A $cvBuildDir/organizations.html \
    -A $cvBuildDir/clients.html \
    -A $cvBuildDir/skills.html \
    $cvBuildDir/cv.md
    
    ###
    ## Convert the HTML CV into PDF CV
    # 
    
    pandoc -H $cvBuildDir/granneman.tex "$cvDir/$cvName.html" -o "$cvDir/$cvName.pdf"
    
    ###
    ## References
    # 
    
    # Convert to HTML
    pandoc --section-divs -f markdown -t html5 -o "$cvBuildDir/references.html" "$cvBuildDir/references.md"
    
    # Convert HTML to PDF
    pandoc -H $cvBuildDir/granneman.tex "$cvBuildDir/references.html" -o "$cvDir/Scott Granneman - References - $(date +%Y-%m-%d).pdf"
    
    ###
    ## Cover Letter
    # 
    
    # Convert to HTML
    pandoc --section-divs -f markdown -t html5 -o "$cvBuildDir/cover-letter.html" "$cvBuildDir/cover-letter.md"
    
    # Convert HTML to PDF
    pandoc -H $cvBuildDir/granneman.tex "$cvBuildDir/cover-letter.html" -o "$cvDir/Scott Granneman - Cover Letter - $(date +%Y-%m-%d).pdf"

When you use this script, you'll obviously need to change the variables to match your username & directory structure.

Throughout the script you'll see `$(date +%Y-%m-%d)`, which generates today's date in this format: `2013-05-25`. This is appended to the final HTML & PDF files, so they look like this: `Scott Granneman - CV - 2013-05-24.pdf`.

### `Create HTML files for each Markdown file`

Let's start with the section labeled `Create HTML files for each Markdown file`. It takes each Markdown file--`articles.md`, `books.md`, `clients.md`, & `cv.md`, for instance--& converts it into a new HTML5 file. For example, `cv.md` goes from this Markdown:
    
    
    # R. Scott Granneman
    
    39 Summit Place • Webster Groves, MO 63119  
    scott@granneman.com • www.granneman.com • www.ChainsawOnATireSwing.com  
    314-780-0489 (c) • 314-644-4900 (w)

To this HTML:
    
    
    <section class="level1" id="r.-scott-granneman">
    <h1>R. Scott Granneman</h1>
    <p>39 Summit Place • Webster Groves, MO 63119<br />scott@granneman.com • www.granneman.com • www.ChainsawOnATireSwing.com<br />314-780-0489 (c) • 314-644-4900 (w)</p>
    </section>

Obviously, this is not a standalone HTML file. There's no `<head>` block, for instance, and not even a DTD or `<html>` to start things off. But that's fine, as you'll see shortly.

Notice also that Pandoc helpfully creates a `class="level1"` for first level headers, and also adds an `id` for each header automatically, with the value for the `id` attribute based on the contents of the header. See--more selectors for CSS!

Let's zoom in on the line in this section of the shell script that does the heavy lifting:
    
    
    pandoc --section-divs -f markdown -t html5 -o $cvBuildDir/$cvBuildName.html $i

Let me walk through each of those options:

  * `\--section-divs`  
Wraps each section (delineated by a 2nd level header or below) in `<section>` elements (`<div>` if I wasn't using HTML5). I do this in case I want more precise CSS selectors. In reality, my CSS doesn't take advantage of these sections--but it could!
  * `-f markdown`  
Convert the file from Markdown. Theoretically, this is unnecessary, but I found that it helps.
  * `-t html5`  
Convert the file to HTML5.
  * `-o $cvBuildDir/$cvBuildName.html`  
This outputs the HTML5 file into the same Builds directory as the Markdown file that's being converted.
  * `$i`  
This is the Markdown file that is being converted.

### `Join the HTML files into one HTML CV`

The `Join the HTML files into one HTML CV` section of the script is next. In this part, those individual, non-standalone HTML files that we just generated are joined together into one big standalone HTML file. In other words, in the previous section we converted files like `articles.md`, `books.md`, `clients.md`, & `cv.md` into `articles.html`, `books.html`, `clients.html`, & `cv.html`; in this section, we're combining `articles.html`, `books.html`, `clients.html`, `cv.html`, & all the others into one file named `Scott Granneman - CV - 2013-05-25.html`.

The really cool thing is that Pandoc lets me control the order those sections appear in the final, big HTML file. Normally you convert one file type to another using Pandoc, but Pandoc also allows you to append other files onto the first file, _in the order in which you specify them_. So look again at the code in this section of the script:
    
    
    pandoc -s -H $cvBuildDir/granneman.css --section-divs -f markdown -t html5 \
    -o "$cvDir/$cvName.html" \
    -A $cvBuildDir/description.html \
    -A $cvBuildDir/education.html \
    -A $cvBuildDir/experience-teaching.html \
    -A $cvBuildDir/experience-writing.html \
    -A $cvBuildDir/experience-business.html \
    -A $cvBuildDir/books.html \
    -A $cvBuildDir/articles.html \
    -A $cvBuildDir/presentations.html \
    -A $cvBuildDir/interviews.html \
    -A $cvBuildDir/training.html \
    -A $cvBuildDir/organizations.html \
    -A $cvBuildDir/clients.html \
    -A $cvBuildDir/skills.html \
    $cvBuildDir/cv.md

The file we're actually converting is `cv.md`

, which is specified at the very end. It's being output to `"$cvDir/$cvName.html"` (the quotation marks are there to catch spaces), specified near the beginning. But in between, I indicate that I want to append (via each `-A`) other files, and the order in which I list them is the order in which they will be added to `$cvName.html`.

Need to re-order the contents of my CV so that my business experience appears before my teaching experience? No problem--I just move `-A $cvBuildDir/experience-business.html \` ahead of `-A $cvBuildDir/experience-teaching.html \`.

That, by the way, is why I have each option on a separate line, with the `\` at the end: to make it easier to see the order sections are in & then to re-order them if necessary.

There are a few new options to the pandoc command that I need to mention:

  * `-s`  
Tells Pandoc to create a standalone HTML5 document, with `<html>` & `<head>` & everything else needed to exist as a complete webpage.
  * `-H $cvBuildDir/granneman.css`  
The `-H` tells Pandoc to insert the named file into the header of the document; in this case, to place the contents of the CSS file at the end of the `<head>` section that's created since this is a standalone file.

### `Convert the HTML CV into PDF CV`

This next section turns that big standalone HTML file into a beautifully-formatted PDF, courtesy of LaTeX. It's a really short & simple command:
    
    
    pandoc -H $cvBuildDir/granneman.tex "$cvDir/$cvName.html" -o "$cvDir/$cvName.pdf"

I had to fool around a bit & put the options in the order you see in order to get this command to work. Note the `-H`, which inserts `granneman.tex` into the header of the file.

### What about references & a cover letter?

I created a single file for each, both in `~/CV/Builds/`:

  * `references.md`
  * `cover-letter.md`

In turn, I convert each Markdown file into an HTML5 document, & then convert that HTML5 document into a PDF. It's all based on what I just showed you, so it's pretty easy.

I'm not going to show the Markdown for the references, but there are a few things special about the cover letter, so here it is:
    
    
    Scott Granneman  
    39 Summit Place  
    Webster Groves, MO 63119
    
    May 26, 2013
    
    Professor Lorem Ipsum
    Major University  
    123 Main Street  
    St. Louis, Missouri 63119
    
    Dear Professor Ipsum:
    
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
    
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
    
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
    
    I have attached my curriculum vitae and a list of references. Thank you for your consideration. I look forward to hearing from you soon.
    
    Yours, 
    
    &nbsp;  
    &nbsp;  
    &nbsp;
    
    Scott Granneman  
    scott@granneman.com  
    314-780-0489

There are two spaces to create line breaks in all the appropriate places. The big thing to note are the 3 &nbsp; that I include at the end. Those are there to create enough space for me to drop in my scanned signature in the PDF

.

## The final product

I have to say, I'm really pleased with the system I've created here. Whenever I need to update my CV, I simply edit the appropriate Markdown file, & then I run `cv.sh`. A few seconds later, I have an HTML file for each Markdown file, and I also have a CV, cover letter, & list of references in both HTML & PDF--& the PDFs look _great_. Here's a complete list of all the files I'm talking about, along with their paths:

  * ~/CV/Builds/articles.html
  * ~/CV/Builds/articles.md
  * ~/CV/Builds/books.html
  * ~/CV/Builds/books.md
  * ~/CV/Builds/clients.html
  * ~/CV/Builds/clients.md
  * ~/CV/Builds/cover-letter.html
  * ~/CV/Builds/cover-letter.md
  * ~/CV/Builds/cv.html
  * ~/CV/Builds/cv.md
  * ~/CV/Builds/description.html
  * ~/CV/Builds/description.md
  * ~/CV/Builds/education.html
  * ~/CV/Builds/education.md
  * ~/CV/Builds/experience-business.html
  * ~/CV/Builds/experience-business.md
  * ~/CV/Builds/experience-teaching.html
  * ~/CV/Builds/experience-teaching.md
  * ~/CV/Builds/experience-writing.html
  * ~/CV/Builds/experience-writing.md
  * ~/CV/Builds/granneman.css
  * ~/CV/Builds/granneman.tex
  * ~/CV/Builds/interviews.html
  * ~/CV/Builds/interviews.md
  * ~/CV/Builds/organizations.html
  * ~/CV/Builds/organizations.md
  * ~/CV/Builds/presentations.html
  * ~/CV/Builds/presentations.md
  * ~/CV/Builds/references.html
  * ~/CV/Builds/references.md
  * ~/CV/Builds/skills.html
  * ~/CV/Builds/skills.md
  * ~/CV/Builds/training.html
  * ~/CV/Builds/training.md
  * ~/CV/Scott Granneman - Cover Letter - 2013-05-24.pdf
  * ~/CV/Scott Granneman - CV - 2013-05-24.html
  * ~/CV/Scott Granneman - CV - 2013-05-24.pdf
  * ~/CV/Scott Granneman - References - 2013-05-24.pdf

Now all I need to do is send the 3 PDFs in `~/CV/` to whomever needs them, & hopefully fame & fortune (or at least a new opportunity) will follow. Again, if you'd like to see the finished products, here you go:

  * [Scott Granneman - Cover Letter - 2013-05-24.pdf](http://files.chainsawonatireswing.com/Scott%20Granneman%20-%20Cover%20Letter%20Lorem%20-%202013-05-27.pdf) (Uses lorem ipsum)
  * [Scott Granneman - References - 2013-05-24.pdf](http://files.chainsawonatireswing.com/Scott%20Granneman%20-%20References%20Lorem%20-%202013-05-27.pdf) (Also uses lorem ipsum)

I hope you find my system as helpful as I do!

  1. Note that Wikipedia prefers _resume_; however, _resume_ is also acceptable & makes more sense to me, so that's what I use. [↩](https://www.chainsawonatireswing.com/2013/05/28/how-i-create-manage-my-cv-using-markdown-pandoc//?from=@)

  2. If you've been paying really close attention, you'll notice that it was unnecessary in the previous section to convert `cv.md` to `cv.html`, as we're doing the same thing here. I don't mind, though, as it makes the first section easier to write, it doesn't add any overhead, and I like having that section as an individual HTML file, even if I don't strictly need it. [↩](https://www.chainsawonatireswing.com/2013/05/28/how-i-create-manage-my-cv-using-markdown-pandoc//?from=@)

  3. Apple's [Preview allows you to easily insert a signature](http://mac.tutsplus.com/tutorials/tips-shortcuts/quick-tip-digitally-insert-signatures-into-documents-using-preview/), [as does PDFpenPro](http://www.smilesoftware.com/help/PDFpen/images.html), which I what I've been using the past few months. [↩](https://www.chainsawonatireswing.com/2013/05/28/how-i-create-manage-my-cv-using-markdown-pandoc//?from=@)
