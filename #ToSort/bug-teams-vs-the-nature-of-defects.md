# Bug Teams vs. The Nature Of Defects

_Captured: 2017-02-24 at 16:46 from [agileotter.blogspot.de](http://agileotter.blogspot.de/2014/01/bug-teams-well-meaning-foolishness.html?utm_content=buffer67047&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer&m=1)_

####  How it Happens

You realize that you're not getting as much done as you expected to get done. It's troublesome, because you have plans and promises and releases to deal with. You're likely to end up the scapegoat when your behind-ness snowballs into a large organization-wide issue.

You also have quality problems. Your team leads estimate that the teams are spending 70% of their effort on defect-fixing activities.

It dawns on you that you can get back 70% of the productivity of your team if you can spin up a separate team to handle bugs! Now one team can be 100% dedicated to adding new functionality without being encumbered by bug-fixing work.

After months, you find that the defect density has not improved from your effort. You see a ramp-up in the number of defects fixed per month as the bug team's diagnostic and corrective skills improve, but they are still lucky to hold-even against the tide of defect injection.

Why doesn't this work?

What has gone wrong?

####  Some Basis For Reasoning

Good decision-making needs good information. I call it "grist for the mill."

Remember these facts:

  * Programming is not typing; it is a purely intellectual labor
  * Code is a collection of decisions, not a collection of keystrokes.
  * Good code is a set of decisions made _well_.
  * A defect is a result of one or more decision(s) made _poorly_.
  * Maintainability is the ability to arrive at good decisions quickly
  * Poor code invites or limits decision-makers to compromised decision-making

Everyone makes mistakes. There are many reasons for this, including a lack of knowledge, stress, overwork, and daily decision fatigue.

Lack of knowledge always figures into defect creation, because our domains and our systems and our features and tools are always partly new to us. After more than 30 years in the field, I'm still learning stuff all the time. Having an advanced degree even a few years ago doesn't mean you don't need to learn all kinds of stuff now. Software is perpetually new -- it is the nature of the beast.

Teams build an immune system into their delivery systems.

The immune system includes alpha and beta testers, human testers, automated tests, continuous build systems, peer reviews, etc.

Agile teams tend to have more advanced immune systems which operate continuously (which may be one reason that they work so well). They typically have automated unit tests, automated integration tests, automated acceptance tests, automated pen tests, automated performance tests, human testers integrated into every team, pair programming, frequent integration and delivery, etc. Some software immune systems are very effective at rejecting bugs.

Manually-managed immune systems can be quite powerful and relatively effective as well.

The linux kernel, as I understand it (correct me if wrong) is a hybrid system involving both automated and human components. You see a tremendous amount of improvement and change each year, and the quality is consistently high compared to other operating system products.

You will find quite sophisticated automated systems in companies practicing continual deployment, since any change we make might make it to the live system in mere minutes or hours.

The automated immune system is absolutely crucial, but it only detects defects and reports them. It can't fix them.

The linux kernel team, as I understand it, does a better job of reporting _why_ a particular change is being rejected than most systems. It is also a hybrid between human and automated systems.

Most immune systems work great, providing us meaningful data which we tally and (in most corporate environments) discard and ignore.

Defects are not random happenings, but holes in our decision-making process. If we had perfect understanding of our technology and code base, and the attention required to stay mindful of all aspects of our work at all times, we would make no errors.

Defects come in categories. Most software defects arise because there is something that the programmer(s) or architects or product managers simply didn't know or were not mindful of at the time.

Imagine you have trouble with C pointers. You don't really have a good policy about who owns what block of memory, when it can be deleted, and when pointers should not be stashed. You will create a whole host of intermittent or puzzling errors. Your code works in limited test runs, or possibly even in demos, but the system keeps crashing!

Your next-door neighbor Jack doesn't really get concurrency and deadlocking. He just copies from existing code, and edits it to do new stuff. He produces a lot of code.

Sue has all that concurrency and pointer work down pat. She has spent years doing server-side programming, but she's never really done web programming before. She has real issues in Javascript and HTML.

Your team has fifty people on it. If you look at the defects produced in a month, it seems pretty random. Sh** happens, you deal with it -- you spin up a bug team to deal with "random bugs" that "just happen."

Our problem is that too few companies have put any serious thought into preventing defects scientifically.

One might think that defects occur at a steady pace, but they don't. One might think that they are evenly distributed over a code base, but they're not. One might think that they're all different and unique like snowflakes, but they're not.

A little looking takes us in a different direction.

####  Bugs Clump by Type

But it is likely that a system has only a few classes of errors which repeat over and over again. You can get better at fixing them, but then your system runs in a very efficient inject->detect->correct cycle that is eating your budget and schedule.

Fixing _the tendency to introduce defects_ can't be done by a bug team.

Even if the feature team has your best, most productive "new code" experts, architects, and geniuses, they are the system generating the defects. Telling them to "be better" isn't actionable, so demanding zero defects isn't very effective.

Reducing defect injection will require some design change to the system and some education for the feature team. They need to know _what to change_ about how they write their code, not merely that it's "not good enough."

Defects are much more common in certain files. We've seen situations where one source file out of thousands held nearly a third of all errors reported in a two-month period. The file wasn't newly-written, either. It was just heck to deal with.

Version control history can tell you where your bugs are being corrected (sadly, it can't find the ones you haven't fixed), so if you report bug fixes as part of your commit comment you can do some data mining and find the code that most needs redesigned. This can significantly reduce the appearance of defects.

I don't have numbers to support my theory (yet) that more defects happen at certain points in a project's lifetime.

I have experienced code written during the "2:30 slump" in the afternoon. I've seen code that was puzzling to me as I left work at 5 or 6 in the evening, only to seem obvious and easily corrected the next morning.

I've seen "quick hack fixes" during hardening sprints, usually made with good intentions to "clean up later" (grep for "to do" or "clean up" in your code base). Deferred corrections are a kind of promise debt.

I've seen periods of panic drive developers into "least-thought" programming, where they produce a huge quantity of code (and defects) in a short period, only to spend the next six months/years discovering and correcting them.

I've seen teams have to slip releases by months because of defects inserted while they were pushing hard to make their release.

We like to believe that working faster and harder will give us higher productivity, but that really is an unproven belief. Nobody has done the research. We don't know the "sweet spot," so we don't know whether working longer or shorter hours produces more value over time, or when the long or short hours are most beneficial.

The timing of defects, if we would track it, would tell us a lot about how we should manage our time.

JB Rainsberger said that if he works overtime today, he will be impaired tomorrow by being tired and frustrated. The question that remains is whether tomorrow is the right day to be impaired. It's a fairly enlightened view of the situation.

####  Is there a system that works?

Feedback works.

In our first five years of programming we gain competence quickly _because_ of our mistakes. Some errors are shallow (mistyping, syntax, etc) and others are deeper (floating point math with rounding problems) and others are deeper yet (concurrency, performance).

In the process of fixing our mistakes we discover we have categories of weakness. We study up on these categories, or topics, and we add competence to competence.

I have memories of getting "stuck" on a bug and digging into the man pages or books, writing experimental code, and/or pulling in a more experienced programmer to help me understand what is going on.

Being responsible for our code and able to explore our mistakes helped us learn not to create defects. That system worked.

Later, when we become code-emitting cogs, we are often discouraged from learning activities including measuring and studying our own defect rates or code quality. I once was told "you're not getting paid to learn."

####  What I would like to try

  * Disband the bug team right now.
  * Give up the "random theory of bugs." Assume all defects are meaningful.
  * Do not punish developers for having defects, lest you squash responsibility and learning.
  * Track bugs down to the code change where they were introduced.
  * Involve the team that injected the defect in corrective actions.
  * Measure the defect trends over the medium-to-long term, indefinitely.
  * Perform experiments on closing bugs by file, by time, and by class.

**Footnote**

Over 25 years ago, Jerry Weinberg wrote about introspection and defects in _The Psychology of Computer Programming_. I'd like to let his words (all emphasis mine) close this blog post:

> Now, a single case such as this contains insights into many problems in computing: _the proper size of statements_, the _choice of data structures_, the a_rrangement of different parts _of a program, the use of parentheses rather than other techniques for decomposition, the design of compiler and execution-time diagnostics, and _techniques for learning and teaching programming_. None of these insights could be obtained without introspection of this sort, yet thousands of programmers each day have these same problems and simply grumble that they are having "bugs." **Without the introspection, they will simply continue to have "bugs" until, in the end, the bugs will have them**.
