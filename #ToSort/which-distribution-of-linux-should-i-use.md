# Which Distribution of Linux Should I Use?

_Captured: 2018-03-09 at 17:16 from [dzone.com](https://dzone.com/articles/which-distribution-of-linux-should-i-use?edition=366226&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-03-09)_

Planning to extract out a few microservices from your monolith? Read this [free guide](https://dzone.com/go?i=265421&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) to learn the best practice before you get started.

I'm often asked this question: "hey, you're a Linux guy right? What Linux should I use? I have this friend who recommends _____ and I want to know what you think?" I usually reply with the same question: what do you want to do? So I decided to make a blog post about it that I can send people instead.

## My History With Linux

I should probably preface this article with a little bit of my history with Linux, in case you're reading this and you don't know me (very likely). You can probably skip this if you don't care.

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/slackware-linux.jpg)

I started out using Linux around 1996. My first Linux was Slackware 4, a set of CDs I purchased at Egghead Software (yep, I'm old). A friend of mine told me about this Unix like thing that was so great and I just had to try it and he thought I would love it.

I read a lot about Unix, and was very curious about it. I had a shell account at my internet provider and I'd tinkered around, yet at first I was a bit hesitant. "Why would I need this?" His reply was simply: "Because you hate Windows 95 so much and love DOS, you'll love this". So I bought it. He was right.

I took an old hard drive I had and installed it. I fought with it for hours, then days. I finally got a desktop up and running. I have no idea what drove me in this time, but I had to figure out how to make this system work, and it was difficult. I had to know so much about my hardware! Simple things were suddenly hard again. But I pushed through, and I got my desktop up. And I started building some silly scripts for fun. The system was fast, and I could change nearly everything about it.

It had a built in C compiler? I just bought some really expensive Borland package for this I could barely figure out. But this OS had a compiler built in? A free Image editor? I was hooked!

For years after that, I experimented with tons of Distributions. Even BSD Unix ones. My "main computer" was always a dual boot, and some of them were pure Linux. Most of the early 2000s, I avoided Windows completely. So by year, I can break it down to my "main machine", it would be:

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/redhat-linux.jpg)

  *   
1996-1999: Slackware
  * 1999-2002: Redhat (and FreeBSD)
  * 2003-2005: FreeBSD / Knoppix
  * 2005-2009: Gentoo
  * 2009-2011: Linux Mint
  * 2011-2018: Arch Linux / Debian

So, of course, I used probably 50 or more distributions in my time, but this was what was running on my "main machine" I used for work, or browsing, or development or whatever. Obviously Arch had the longest run so far, mainly because I could just configure it and forget about it for long periods of time.

But the main distro for my "real work" the last few years has been Debian.

Enough about me though, let's talk about what you should use.

## So What Do You Want to Do?

I'm going to put these in categories based on common needs. There is some overlap here, and with enough work any of these Linux distributions will work for your desired needs. One of the great things about Linux is you can make it whatever you want. But some distributions do a lot of that work for you, or have a design that works better towards certain goals. I'll present these in categories based on the easiest path to reach your goals.

## I'm a Linux Newbie Just Getting Started

For a long time I recommended Ubuntu for this. As far as ease of use and compatibility it was great. But I pretty much hate Ubuntu now. I still use it for demos in my courses and articles because so many people use it, but I am not a fan of the way they run this distribution, the built in Amazon adware, and Unity is annoying.

**So if you're just starting out I recommend:**

It's kind of a cheat because Linux Mint is built off Debian, but Mint looks prettier and has some nice cross-platform stuff.

**Use these distributions if you want:**

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/linux-mint.jpg)

  * A Windows-like experience
  * Something simple to install
  * Something reliable
  * Something "Linux like" that doesn't deviate from the norm
  * Something that "just works"

Okay, so that last one is really important. It just works. Either of these distributions are plug and play. Set them up, and forget about it. I have become increasingly reliant on Debian for my development machines because at times **I don't care about the OS and I don't want it to get in my way**. When I'm in a mood where I just want to build things, it can't be beat.

## I Want to Learn More About Linux/Unix and My Hardware

Maybe you're in the mood to play and experiment. You want to challenge yourself and force yourself to learn by doing. That's great, it's exactly what I did.

**If you want to challenge yourself and learn, I recommend:**

  * [FreeBSD ](https://www.freebsd.org/where.html)(Not Linux, but fits in this category)![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/arch-linux.jpg)

Each of these distributions requires a lot of configuration, hardware discovery, and compiling of source. With Gentoo you have to compile everything. It's a great way to have absolute full control over your operating system.

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/gentoo-linux.jpg)

**Use these distributions if you want:**

  * Full control of your computer and OS
  * To learn about Linux internals
  * A lean and mean optimized system

This comes at a cost: mainly your time. A full install of these can take hours. On the plus side, they tend to run forever.

I had an Arch Install on a Lenovo that took the better part of a Saturday to configure, and let's say another 10 hours or more spread out after that. It ran nearly effortlessly for 5 years (till the laptop hardware died). I only had to do a few updates once in a while, but I used it reliably every day for 5. Long. Years. So in a way you can look at it as investment.

## I Want Cutting Edge Stuff

Okay, maybe you want the latest greatest software and you don't care how stable it is. You want to do some kernel hacking or some other cool thing that some coder committed yesterday.

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/opensuse-tumbleweed.jpg)

**To hell with stability and security, you want the newest thing now.**

**Use these distributions if you want:**

  * To trade risk for the newest stuff
  * The latest and greatest features always
  * Fun configuring things to work with breaking changes

To be fair I've personally used Arch and Gentoo without significant stability problems, but I was risking using the bleeding edge stuff on rolling releases.

## I Just Want to Get Some Work Done

Ok maybe you don't really care about the OS particulars and just want to GSD (Get Stuff Done). Maybe you have some Node or GoLang apps you want to build and heard Linux is the best for it.

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/debian-linux.jpg)

**These are great for getting work done:**

**Use these distributions if you want:**

  * Smooth operation with low maintenance
  * Minimal configuration
  * Things that just work mostly automatically
  * Compatibility with hardware and software

As I said I often use Debian these days as I'm usually just making something and don't really feel like tinkering around and optimizing. It's stable, fast, and stays out of my way. I'm writing this article in Debian 9 right now.

## I Want to Set Up a Server

Maybe you want to set up a web server or virtual host and don't know what to use. The first one on this list is the dominant distribution for web hosting, so if you want something that mimics the site that's hosting your software, try CentOS (or learn Docker!)

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/centos-linux.jpg)

**These are solid and reliable for web hosting:**

**Use these distributions if you want:**

  * Stability
  * Security
  * Support from other people using it for the same reason

I believe any Linux distribution can be used for web hosting effectively, but some take more work than others.

## I Want the Most Performance Possible

So if you're one of those types who wants to squeeze out every ounce of performance (I've been there) these are great for you. Some of these require compiling all the source code to produce binaries optimized for your processor(s). Fun stuff!

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/clear-linux.jpg)

**Use these distributions if you want:**

  * Fast performance
  * High Load Computing

Keep in mind that hardware has reached a performance point where these don't matter quite as much as they used to. 15 years ago you could hack a kernel and dial in your services and see a big boost. These days, the difference is negligible. Any Linux will be pretty snappy.

## I Want a Secure Desktop

Maybe you want to set up a system that's hard to break into, for whatever reason. There are a couple distributions with security as a top focus. If you're really concerned about locking down your main machine, these are great ones to look at.

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/tails-linux.jpg)

**Use these distributions if you want:**

  * Security

  * Anonymity

## I Want a Minimal Computer System

Ok sometimes you just want something lean and mean that gets a certain job done. I definitely understand this. Maybe you have an old Pentium you want to re-purpose. Sometimes the OS is just a small part of your goal and you want the bare minimum.

![](https://www.jeremymorgan.com/images/what-distro-of-linux-should-i-use/lubuntu-linux.jpg)

**Use these distributions if you want:**

  * Something that will run on old hardware
  * Something minimal as possible

## Conclusion

I hate to sound like a broken record, but you could just pick out one of these Linux distributions and make it whatever you want. That's the nature of Linux, its customizable to the furthest degree. But these are great distributions for getting started fast. If you think I've missed the mark or left out a distribution feel free to leave me a message in the comments, or [yell at me on Twitter](https://twitter.com/JeremyCMorgan).

And whatever you do, if you reached this page because you're curious about Linux, try it out!! Now! These days you can download something like [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (free of charge) and try it out before really committing to anything. It's definitely worth your time to check it out!

[Learn how](https://dzone.com/go?i=275425&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%25252520DZone%25252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%25252520roll) to measure the impact of every feature release on performance and customer experience metrics.
