# Open-Sourcing Code Is a BAD Default Policy

_Captured: 2018-05-11 at 12:08 from [dzone.com](https://dzone.com/articles/open-sourcing-code-is-a-bad-default-policy?edition=376278&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-10)_

RavenDB vs MongoDB: **[Which is Better?](https://dzone.com/go?i=283421&u=https%3A%2F%2Fravendb.net%2Fwhitepapers%2Fmongodb-ravendb-best-nosql-open-source-document-database%3Futm_source%3Ddzone%26utm_medium%3Dbumper-text%26utm_campaign%3Dravendb-vs-mongodb-white-paper)** This White Paper compares the two leading NoSQL Document Databases on 9 features to find out which is the best solution for your next project.

I ran into [this Medium post](https://medium.com/@matteofigus/why-is-this-code-open-sourced-lets-flip-the-question-89d3f6d949c4) that asks: _Why is this code open-sourced?_ Let's flip the question. The premise of the post is interesting, given that the author asks that the default mode for code is that it should be open-source. I find myself in the strange position of being a strong open source adherent that very strongly disagrees on pretty much every point in this article. Please sit tight. This may take a while. This article really annoyed me.

Just to clear the fields, I have been working on open-source software for the past 15 years. The flagship product that we make is open-source and available on GitHub and we practice a very open development process. I was also very active in a number of high-profile open-source projects for many years and had quite a few open-source projects that I had built and released on my own. I feel that I'm quite qualified to talk from experience on this subject.

The quick answer for why the default for a codebase shouldn't be open-source is that it _costs_. In fact, there are several very different costs around that.

The most obvious one is the reputation cost for the individual developer. If you push bad stuff out there (like this [100+ lines method](https://github.com/ayende/rhino-pht/blob/master/Rhino.PersistentHashTable/PersistentHashTableActions.cs#L121-L231)), that can have a real impact on people's perception on you. There is a very different model for internal interaction inside the team and stuff that is shown externally without the relevant context. A lot of people don't like this exposure to external scrutiny. That leads to things like: "Clean up the code before we can open-source it." You can argue that this is something that should have been done in the first place, but that doesn't change the fact that this is a real concern and adds more work to the process.

Speaking of work, just throwing code over the wall is _easy_. I'm going to assume that the purpose isn't to just do that. The idea is to make something useful and that means that aside from the code itself, there is also a lot of other aspects that need to be handled. For example, engaging the community, writing documentation, and ensuring that the build process can run on a wide variety of machines. Even if the project is only deployed on Ubuntu 16.04, we still need to update the build script for that MacOS guy. Oh, this is open-source and they sent us a PR to fix that. Great, truly. But who is going to _maintain _that over time?

Open source is not an idyllic landscape where you dump your code and someone else is going to come and garden it for you.

And now, let me see if I can answer the points from the article in detail:

> Open-source code is more accessible -- Maintainers can get code reviews … consumers from anywhere in the world … can benefit from something I was lucky enough to be paid for building. 

First, drive-by code reviews are _rare_ -- as in, they happen extremely infrequently. I know that because I do them for interesting projects and I explicitly invited people to do the same for my projects and had very little response. People who are actually using the software will go in and look at the code (or some parts of it) and that can be very helpful, but expecting that just because your code is open-source you'll get reviews and help is setting yourself for failure.

There is also the interesting tidbit there about consumers benefiting from something that the maintainers were paid to build. That part is a pretty important one because there is a side here in the discussion that hasn't been introduced. We had maintainers and consumers, but what about the guy who ended up paying the bills? I mean, given that this is paid work, this isn't the property of the maintainer; it belongs to the people who actually paid for the work. So, any discussion on the benefits of open-sourcing the code should start from the benefits for _these people_.

Now, I'm perfectly willing to agree (in fact, I do agree, since my projects are in the open) that there are good and valid reasons to want to open-source a project, and community feedback is certainly a part of that. But any such discussion should start with the interests of the people paying for the code and how it helps them. And part of that discussion should involve the real and nontrivial costs of actually open sourcing a project.

> Open-source code keeps us healthy -- Serotonin and Oxytocin are chemicals in the brain that make you feel happy and love. Open source gives you that. 

I did a bad job summarizing this part, quite intentionally -- mostly because I couldn't quite believe what I was reading. The basic premise seems to be that by putting your code out there, you open yourself to the possibility of someone seeing your code and sending you a "Great Job" email and making your day.

I... guess that can happen. I certainly enjoy it when it happens, sure. Why would I say no to something like that?

Well, to start with, it happens, sure, but it isn't a major factor in the decision-making process. I'll argue that if you think that compliments from random strangers are so valuable, just get in and out of Walmart in a loop. There are perfect strangers there who will greet you _every single time_. Why wouldn't you want to do that?

More to the point, even assuming that you have a very popular project and _lots_ of people write you how awesome you are, this gets tiring fast. What is worse is you throwing code over the wall and expecting a pat on the back. But no one cares; actually getting them to care takes a whole lot of additional work.

And we haven't even mentioned that other side of open-source projects: the users who believe that just because your code is open-source, they are entitled to all your time and effort (for free). And you are expected to fix any issues that they find (immediately, of course) and are quite rude and obnoxious. There aren't a lot of them, but literally any open-source project that has anything but the smallest of followings will have to handle them at some point. And often, dealing with such a disappointed user means dealing with abuse. That can be exhausting and painful.

Above, I pointed out a piece of code in the open that is open to critique. This is a piece of code that I wrote, so I feel comfortable telling you that it isn't so good. But imagine that I took your code and did that. It is very easy to get offended by this, even when there was no intent to offend.

> Open-source code is more maintainable -- lots of tools are free for OSS projects. 

So? This is only ever valuable if you assume that tooling is expensive (it isn't). The article mentions tools such as Travis-CI, Snyk, Codecov, and Dependencies.io that are offering free tiers for open-source projects. I went ahead and priced these services for a year for the default plans for each. The total yearly cost of all of them was around $8,000. That is a lot of money. But that is only assuming that you are an individual working for free. Assuming that you are actually getting paid, the cost of such tools and services is miniscule compared to other costs (such as developer salaries).

So, admittedly, this is a very nice property of open-source projects, but it isn't as important as you might imagine it would be. In a team of five people, if the effort to open-source the project is small, only taking a couple of weeks, it will take a few years to recoup that investment in time (and I'm ignoring any additional effort to run the open-source portion of the project).

> Open-source code is a good fit for a great engineering culture. 

Well, no. Not really. You can have a great engineering culture without having open source and you can have a really crappy engineering with open source. They sometimes go in tandem, but they aren't really related. Investing in the engineering culture is probably going to be much more rewarding for a company that just open-sourcing projects. Of particular interest to me is this quote:

_"Engineers are winning because they can autonomously create great projects that will have the company's name on it: good or bad..."_

No, engineers do not spontaneously create great projects. That comes from hard work, guidance, and a lot of surrounding infrastructure. Working in open source doesn't mean that you don't need coordination, high-level vision, and good attention to detail. This isn't a magic sauce.

What is more, and that is really hammering the point home: good or bad. Why would a company want to attach its name to something that can be good or bad? That seems like a very unnecessary gamble. So, in order to avoid publicly embarrassing the company, there will be the need to do the work to make sure that the result is good. But the alternative to that is not to have a bad result. The alternative to that is to not open-source the code.

Now, you might argue that such a thing is not required if the codebase is good to begin with, and I'll agree. But then again, you have [things like this](https://github.com/search?l=C%2B%2B&q=fucked&type=Code) that you'll need to deal with. Also, be sure that you cleaned up both the code and the [commit history](https://github.com/search?q=stupid+customer&type=Commits).

> Just why not? 

The author goes on to gush about the fact that there are practically no reasons why not to go open source, that we know that projects such as frameworks, languages, operating systems, and databases are all open-source and are very successful.

I think that this gets to the heart of the matter. There is the implicit belief that the important thing about an open-source project is the code. That couldn't be further from the truth. Oh, of course, the code is the foundation of the project, but foundations can be replaced (e.g. FireFox, OpenSsl -> BoringSsl, React, etc).

The most valuable thing about an open-source project is the community. The contributors and users are the things that make a project unique and valuable. In other words, to misquote Clinton, _It's the community, stupid._

And a community doesn't just spring up from nowhere. It takes effort, work, and a whole lot of time to build. And only when you have a community of sufficient size will you start to see the actual ROI for your efforts. Until that point, all of that is basic sunk cost.

I'm an open-source developer. Pretty much all the code I have written in the past decade or so is under one open-source license or another and is publicly available. And with all that experience behind me, I can tell you what really annoyed me the most about this article. It isn't an article about promoting open source. It is an article that, I feel, promotes just throwing code over the wall and expecting flowers to grow. That isn't the right way to do things. And it really bugged me that in all of this article, there wasn't a single word about the people who actually _paid_ for this code to be developed.

Note that I'm not arguing for closed-source solutions for things like IP, trade secrets, secret sauce, and the like. These are valid concerns that need to be addressed, but that isn't the issue. The issue is that open-sourcing a project (vs. throwing the code to GitHub) is something that should be done in a forthright manner -- with clear understanding of the costs, risks, and ongoing investment involved. This isn't a decision you make because you don't want to pay for a private repository on GitHub.

Do you pay to use your database? What if your database paid you? [Learn more with RavenDB](https://dzone.com/go?i=292421&u=https%3A%2F%2Fravendb.net%2Farticles%2Fcost-benefits-ravendb-nosql-acid-database%3Futm_source%3Ddzone%26utm_medium%3DDBPays4ITself%26utm_campaign%3Ddzone-partner-resources).
