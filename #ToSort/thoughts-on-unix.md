# Thoughts on UNIX

_Captured: 2018-08-22 at 16:47 from [dzone.com](https://dzone.com/articles/thoughts-on-unix?edition=385406&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-08-22)_

I recently completed a UNIX workbench course by John Hopkins University in Coursera. So, I thought I would write something about UNIX, GNU/Linux.

![unix_workshop](https://sudipbhandari126.github.io/resources/unix_workshop.png)

## Love for UNIX

There is a documentary by AT&T on Unix on [Youtube](https://www.youtube.com/watch?v=tc4ROCJYbm0) which I regularly rewatch now and again which shows the early story of UNIX and has [Brian Kernighan](https://en.wikipedia.org/wiki/Brian_Kernighan) talk about the power, simplicity and elegance of UNIX design.

![AT&T Story of Unix](https://img.youtube.com/vi/tc4ROCJYbm0/0.jpg)

We know the story of how Linux came to be. UNIX was developed in AT&T and the prominent scientists involved were [Ken Thompson](https://en.wikipedia.org/wiki/Ken_Thompson), [Dennis Ritchie](https://en.wikipedia.org/wiki/Dennis_Ritchie) and [Brian Kernighan](https://en.wikipedia.org/wiki/Brian_Kernighan), among many others. As the years passed by, there were a lot of variations of UNIX and they were used by companies like Sun, DEC, IBM, HP, etc. There was no version of UNIX which could be used by personal hobbyists. [Richard Stallman](https://en.wikipedia.org/wiki/Richard_Stallman), in an attempt to build Unix-like computer operating system, launched the GNU project and the free software foundation in 1983. In 1991, [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) developed a UNIX clone, named it Linux, and kickstarted the growth of Linux. Linux as an OS is kernel (monolithic) and has a lot of libraries and utilities which actually come from the GNU project launched by Richard Stallman. For this reason, the Free Software Foundation actually calls it GNU/Linux rather than just Linux.

## **UNIX Philosophy**

Unix is also known for its philosophy. One intriguing thing about the UNIX philosophy for me is that it was created back in the days when we didn't have much software programming going on, and decades later it still sounds very relevant and practical.

  * Make each program do one thing well. To do a new job, build afresh rather than complicate old programs by adding new "features."
  * Expect the output of every program to become the input to another, as yet unknown, program. Don't clutter output with extraneous information. Avoid stringently columnar or binary input formats. Don't insist on interactive input.
  * Design and build software, even operating systems, to be tried early, ideally within weeks. Don't hesitate to throw away the clumsy parts and rebuild them.
  * Use tools in preference to unskilled help to lighten a programming task, even if you have to detour to build the tools and expect to throw some of them out after you've finished using them.

I started using Linux during my college. After I started using Linux it has become my primary OS for personal usage and thankfully all the companies that I have been part of. As any other Linux fanatic I go about switching distros, have tried centos, fedora, debian, ubuntu, mint and too many more. I also keep switching desktop environment. Currently I prefer GNOME on Ubuntu, not a fan of Unity though I heard it's going to be replaced in coming Ubuntu release. I love using Linux for it's simplicity in design which it derives from UNIX. Everything is a file, there are short powerful commands which can be chained, the whole system is nicely documented, and there's always something new and interesting for you to learn if you dig down the man pages. I also love the developer communities which are super supportive.

Speaking of the UNIX philosophy of short, powerful, chainable (useful output which can be fed directly into another program) commands, one thing that impresses me now and then is how efficiently people make use of these tools. It's always refreshing to see one of your colleagues or fellow developers chaining a lot of commands with `grep` and `awk` thrown in between (just an example) to achieve something in a short span of time.
