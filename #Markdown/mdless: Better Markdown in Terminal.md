# mdless: Better Markdown in Terminal

_Captured: 2015-08-22 at 10:54 from [brettterpstra.com](http://brettterpstra.com/2015/08/21/mdless-better-markdown-in-terminal/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

Here's a side project that got out of hand.

![](http://cdn3.brettterpstra.com/uploads/2015/08/mdless.jpg)

I wanted to be able to view Markdown README files quickly and pleasantly from Terminal. More often than not, I'm working in an [iTerm2](https://www.iterm2.com/) visor window, so opening any app--including a simple `qlmanage -p`--will make my current view slide away. Not a big deal, of course, but it seemed like it could be easier.

I created `mdless` for this. It's a little utility that colorizes, cleans up, and pages Markdown documents. You can use `-s SECTION` to spit out just a single section of the document (use `\--list` to show available sections).

Markdown is pretty easy to read just as a text file, but some README files are really long and have a lot of cruft that only looks good when rendered. So this tool cleans it up. It also fixes table formatting and highlights it, among other goodies.

If you have [Pygments](http://pygments.org/) installed, fenced code blocks will be highlighted. And if you're running the [latest iTerm2](https://www.iterm2.com/version3.html) (beta), you can even view images inline.

You can install it with `gem install mdless` (you may need to use `sudo gem install mdless` depending on your setup). It's been tested on systems with Ruby 1.9 through 2.1. It should work on non-Mac systems, but I haven't tried it out.

`mdless` is a work in progress, but it's doing everything it was supposed to do already. [Check the project page for more info.](http://brettterpstra.com/projects/mdless)
