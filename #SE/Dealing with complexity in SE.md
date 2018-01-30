# Dealing with complexity

_Captured: 2015-11-19 at 23:49 from [focs.wordpress.com](https://focs.wordpress.com/2007/09/02/dealing-with-complexity/)_

Mark Chu-Carroll has [a really cool blog](http://scienceblogs.com/goodmath/). If he doesn't blog, he works for Google. Here is his answer to my [Hamming question](https://focs.wordpress.com/2007/05/13/hello-world/):

> I'll do my best to answer. By necessity, I've got to be a bit vague, because I don't want to give away any google secrets.
> 
> First, I need to draw one important distinction. Computer science is too broad - there are lots of different areas, and I don't think I can pick exactly one of them that's clearly more important than the others. So I'll arbitrarily pick the one that I know best: software engineering.
> 
> So - what are the most important problems in software engineering? I'd answer "dealing with complexity". Software is frighteningly complex, and becoming moreso by the day. The editor that I use for programming has reached more than 2 million lines of code - I don't think that there's any person in the world who actually understands the whole thing. And that's just a programming tool! Imagine the complexity of the things we build with it! Software is now built by groups of people, and no one person can understand all of the details. It's built for hardware that people can barely program themselves (if they can do it at all!). It's built to run scattered around huge numbers of machines around a network (the mail client where I'm writing this is running partly on my computer, partly on a web server at google, and partly in a mail database server.)
> 
> What do I do? I'm a toolbuilder. I make tools to help software engineers deal with complexity. Over the last few years, I've worked on SCM systems - which are tools that help groups of engineers deal with the complexity of working together. I've worked on programming environments - which are tools that help individual programmers deal with the complexity of understanding systems. And I've worked on build tools - which are tools that help deal with the complexity of assembling a large system from many small parts.
> 
> So what I do is a small part of trying to solve the biggest problems in software engineering. I don't want to sound too egotistical - it is a *very* small part of a *very* big problem, but it's the part that's interested me from the first time I saw a computer, and I'm very proud to be contributing to it, even in a tiny way.

Working on the tools really isn't a prominent job, but important none the less. Researchers may write prototypes and evaluate them for papers, but it needs more people to make real, useable programs out of that. When the programs are written we need even more people to maintain, adapt and debug those programs.
