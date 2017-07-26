# Google Is 2 Billion Lines of Code—And It’s All in One Place

_Captured: 2015-09-18 at 13:42 from [www.wired.com](http://www.wired.com/2015/09/google-2-billion-lines-codeand-one-place/)_

![STORY GettyImages-132073812](http://www.wired.com/wp-content/uploads/2015/09/STORY-GettyImages-132073812-582x417.jpg)[Click to Open Overlay Gallery](javascript:;)

> _Getty Images_

How big is Google? We can answer that question in terms of revenue or stock price or customers or, well, metaphysical influence. But that's not all. Google is, among other things, a vast empire of computer software. We can answer in terms of code.

Google's [Rachel Potvin](https://www.linkedin.com/pub/rachel-potvin/1/659/103https://www.linkedin.com/pub/rachel-potvin/1/659/103) came pretty close to an answer Monday [at an engineering conference in Silicon Valley](https://www.youtube.com/watch?v=W71BTkUbdqE). She estimates that the software needed to run all of Google's Internet services--from Google Search to Gmail to Google Maps--spans some 2 _billion_ lines of code. By comparison, Microsoft's Windows operating system--one of the most complex software tools ever built for a single computer, a project under development since the 1980s--is likely [in the realm of 50 million lines](https://www.facebook.com/windows/posts/155741344475532).

So, building Google is roughly the equivalent of building the Windows operating system 40 times over.

The comparison is more apt than you might think. Much like the code that underpins Windows, the 2 billion lines that drive Google are _one thing_. They drive Google Search, Google Maps, Google Docs, Google+, Google Calendar, Gmail, YouTube, and every other Google Internet service, and yet, all 2 billion lines sit in a single code repository available to all 25,000 Google engineers. Within the company, Google treats its code like an enormous operating system. "Though I can't prove it," Potvin says, "I would guess this is the largest single repository in use anywhere in the world."

Google is an extreme case. But its example shows how complex our software has grown in the Internet age--and how we've changed our coding tools and philosophies to accommodate this added complexity. Google's enormous repository is available only to coders inside Google. But in a way, it's analogous to GitHub, the public [open source repository where engineers can share enormous amounts of code](http://www.wired.com/2015/03/github-conquered-google-microsoft-everyone-else/) with the Internet at large. We're moving toward a world in which we regularly collaborate on code at a massive scale. This is the only way we can keep up with the rapid evolution of modern Internet services.

"Having 25,000 developers, as Google does, means it's sharing code with a diverse set of people with diverse set of skills," says Sam Lambert, the director of systems at GitHub. "But, as a small company, you can get some of that same advantage using GitHub and open source. There's that saying: 'A rising tide raises all boats.'"

The flip side is that building and running a 2-billion-line monolith is no simple task. "It must be a technical challenge--a huge feat," Lambert says. "The numbers are absolutely staggering."

Part of the genius of GitHub is that it lets coders so easily share and collaborate on code. But GitHub doesn't house a single software project. It spans millions of projects. Google goes a step further, combining many projects into one. Given the difficulty of juggling that much code across that many engineers, this may seem slightly crazy. But according to Potvin, it works.

### Listen to the Piper

Basically, Google has built its own "[version control system](https://en.wikipedia.org/wiki/Version_control)" for juggling all this code. The system is called Piper, and it runs across the [vast online infrastructure Google has built](http://www.wired.com/2012/08/google-as-xerox-parc/) to run all its online services. According to Potvin, the system spans 10 different Google data centers.

It's not just that all 2 billion lines of code sit inside a single system available to just about every engineer inside the company. It's that this system gives Google engineers an unusual freedom to use and combine code from across myriad projects. "When you start a new project," Potvin tells WIRED, "you have a wealth of libraries already available to you. Almost everything has already been done." What's more, engineers can make a single code change and instantly deploy it across all Google services. In updating one thing, they can update everything.

There are limitations this system. Potvin says certain highly sensitive code--stuff akin to the Google's PageRank search algorithm--resides in separate repositories only available to specific employees. And because they don't run on the 'net and are very different things, Google stores code for its two device operating systems--Android and Chrome--on separate version control systems. But for the most part, Google code is a monolith that allows for the free flow of software building blocks, ideas, and solutions.

### The Bot Factor

As Lambert point out, building and running such a system requires not only know-how but enormous amounts of computing power. Piper spans about 85 terabytes of data (aka 85,000 gigabytes), and Google's 25,000 engineers make about 45,000 commits (changes) to the repository each day. That's some serious activity. While the Linux open source operating spans 15 million lines of code across 40,000 software files, Google engineers modify 15 million lines of code across 250,000 files _each week_.

At the same time, Piper must work to remove much of the burden from human coders. It must ensure that humans can wrap their heads around all that code; that they don't step on each other's toes with code changes; that they can readily remove bugs and unused code from the repository. And because all of this is so difficult, it must actually take some of that work away from the humans. Now that Google has switched to Piper from its previous version control system--a tool called Perforce--automated 'bots handle a majority of the commits.

This doesn't mean 'bots are writing code. But they are generating a lot of the data and configuration files needed to run the company's software. "You need to make a concerted effort to maintain code health," Potvin says. "And this is not just humans maintaining code health, but robots too."

### Piper for Everyone

Could others benefit from the same kind of system? Certainly. And they do. The main Facebook app spans [upwards of 20 million lines of code](http://www.wired.com/2013/04/facebook-windows/), and the company treats the whole thing as a single project. Others do the same on a smaller scale. As companies approach the size of a Google or a Facebook, the logistics can get in the way. But Google and Facebook are exploring ways of changing that--for everyone.

The two internet giants are working on an open source version control system that anyone can use to juggle code on a massive scale. It's based on an existing system called [Mercurial](https://en.wikipedia.org/wiki/Mercurial). "We're attempting to see if we can scale Mercurial to the size of the Google repository," Potvin says, indicating that Google is working hand-in-hand with programming guru [Bryan O'Sullivan](https://www.linkedin.com/in/bryanosullivan) and others who help oversee coding work at Facebook.

That may seem extreme. After all, few companies juggle as much code as Google or Facebook do today. But in the near future, they will.
