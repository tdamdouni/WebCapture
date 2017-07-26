# Markdown Powered Resume with CSS Print Styles

_Captured: 2015-12-01 at 02:53 from [blog.michaelhamrah.com](http://blog.michaelhamrah.com/2013/03/markdown-powered-resume-with-css-print-styles/)_

As much as I wish a LinkedIn profile could be a substitute for a resume, it's not, and I needed an updated resume. My previous resume was done some time ago with InDesign when I was on a design-tools kick. It worked well, but InDesign isn't the best choice for a straight forward approach to a resume and I was not interested in going back to word. So in honor of my friend Karthik's [programming themed resume](http://kufli.blogspot.com/2013/02/evolution-of-my-resume-karthik.html) I had an idea: program my resume. My requirements were simple:

  * Easy to edit: I should be able to update and output with minimal effort.
  * Easy to design: Something simple, but not boilerplate.
  * Export to Html and PDF: For easy distribution.

I'm a big fan of [Markdown](http://daringfireball.net/projects/markdown/syntax) and happy to see the prevalence of Markdown across the web, however fragmented. I use Markdown to publish this blog and felt it would work well for writing a resume. The only problem is layout: you have minimal control over structural html elements which can make aspects of design difficult. For writing articles this isn't a problem but when you need structural markup for CSS it can be limiting. Luckily I found [Maruku](https://github.com/bhollis/maruku), a ruby-based markdown interpreter which supports [PHP Markdown Extra](http://michelf.ca/projects/php-markdown/extra/) and a [new meta-data syntax](http://maruku.rubyforge.org/proposal.html) for adding id, css, and div elements to a page. It does take away from Markdown's simplicity but adds enough structure for design. Combined with CSS I had everything I needed to fulfill my requirements.

My [markdown resume](https://github.com/mhamrah/mlh.com/blob/master/michael-hamrah-resume.md) is on GitHub. I was surprised it rendered well with GitHub-Flavored Markdown despite the extraneous Maruku elements. I knew I was on the right track. Maruku lets you add your own stylesheets to the html output which I used for [posting online](http://www.michaelhamrah.com/michael-hamrah-resume.html). One simple command gets me from markdown to ready-to-publish html. Exactly what I wanted.

Markulu supports pdf output as well, but requires a heavy LaTex install which I wasn't happy with. I also wasn't impressed with the LaTex PDF output. Luckily there's an easy alternative: printing to PDF. I used some [SASS media query overrides](https://github.com/mhamrah/mlh.com/blob/master/scss/resume.scss) on top of Html 5 Boilerplate's default styles to control the print layout in the way I wanted. You can even specify page breaks and print margins via CSS. I favored Safari's pdf output over Chrome's for the sole reason Safari automatically embedded custom fonts in the final PDF.

At the end of the day I realized I probably didn't need to add explicit divs to Markdown; I could have gotten the layout I wanted with just vanilla Markdown and CSS3 queries. I also could have a semantically better markup if I used HAML to add

tags instead of divs where appropriate, but HAML would have added a considerable amount of extraneous information to the markup. I'm also not sure editing the raw HAML text would have been as easy as Markdown.

At the end of the day, it's all a tradeoff. GitHub flavored markdown, Markdown Here and other interpreters support fenced code blocks; I like the idea of adding fenced blocks to get

elements to get semantic correctness and layout elements in the html output. Unfortunately there's no official Markdown spec and support is somewhat fragmented across various implementations, but [hopefully it will come together soon](http://www.codinghorror.com/blog/2012/10/the-future-of-markdown.html). Until then, if you need it, you can always fork. Luckily I didn't have to take it that far.
