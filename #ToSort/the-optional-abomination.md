# The Optional Abomination

_Captured: 2017-01-23 at 00:55 from [dzone.com](https://dzone.com/articles/the-optional-abomination?edition=263911&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-22)_

Navigate the Maze of the End-User Experience and pick up this [APM Essential guide](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574).

There's this piece of code… I keep thinking about it. It shows up in my dreams. I open it every time I get to work. I learned it by heart already. It scares me. It reminds me of every bad thing that ever happened to me in my life. It reminds me of every line of crappy code that I ever wrote. It's like a whisper in my ear: _You can't avoid me._ Help! Please help!

My eyes are burning! Aaarrgh! Why? Why? Why? Why? Why?!

To be honest, I knew things are going the wrong way when Java 8 came along and I saw people using `Objects.isNull` and `Objects.nonNull` instead of a normal null check, but this?!

A big part of our profession is handling complexity. We take **complex domains** and make software out of it. We hide the complexity between a (supposedly) nice UI, so that the end-user does not have to deal with it. Ideally, what he sees is a reflection of his mental model of the problem and he feels "at home" using our software.

I've made the words "complex domains" bold for a reason. The world that we're trying to handle is complex already. This complexity needs to be then represented in the code somehow, in order to solve our user's problem. That's what we call _inherent complexity_.

Unfortunately, more often than not, there's another kind of complexity lurking in there -- _accidental complexity_. This is the kind of complexity that we developers create "accidentally" when coding and it's not related to complexity of the domain itself -- it's not necessary to make the system work.

Inherent complexity mixed with accidental complexity is an extremely dangerous mixture. Drink it for too long and your system will become a legacy that you don't want to drag along. Therefore, we have to do everything we can to limit the complexity. We want **simplicity**!

Now, it's beyond a single post, probably beyond a single book and maybe even beyond a single mind to understand and explain all the ways to limit complexity in software. But whatever programming language you use, whatever framework stack you choose and whatever kind of applications you make, the first step is always the same: **LEARN YOUR GOD DAMN PROGRAMMING LANGUAGE!**

Read books, documentation, blogs, read the damn source code. Sometimes, it's a matter of one click in the IDE to avoid making a fool out of yourself:

And you, Optional Abomination, leave me and my life, now!

![Image title](http://tidyjava.com/wp-content/uploads/2017/01/giphy.gif)

Thrive in the application economy with [an APM model that is strategic](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574). Be E.P.I.C. with CA APM. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574).
