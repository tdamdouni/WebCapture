# Stack Overflow: Helping One Million Developers Exit Vim

_Captured: 2017-05-24 at 17:23 from [stackoverflow.blog](https://stackoverflow.blog/2017/05/23/stack-overflow-helping-one-million-developers-exit-vim/)_

This morning, a [popular Stack Overflow question](https://stackoverflow.com/questions/11828270/how-to-exit-the-vim-editor) hit a major milestone:

![](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/05/exitvim.png)

You're not alone, jclancy. In the five years since this question was asked, there have been over a million other developers who got stuck in Vim and couldn't escape without a bit of help. Indeed, the difficulty of quitting the Vim editor is a common joke among developers.

![](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/05/practicaldev-1.jpg)

![](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/05/meme.jpeg)

I've been told by experienced Vim users that this reputation is unfair, and I'm sure they're right (even I've gotten the hang of it in the last few years). I think there are two reasons it's easy to forget how to exit Vim: developers are often dropped into Vim from a git command or another situation where they didn't expect to be, and they run into it infrequently enough to forget how they solved it last time.

In honor of this milestone, we decided to take a look at the data surrounding this question. In particular, we'll try measuring who is most likely to get **stuck** in Vim as opposed to using it intentionally, and examining how that balance varies by country and by programming language.

### How many people have been struggling to exit Vim?

In the last year, [How to exit the Vim editor](http://stackoverflow.com/questions/11828270/how-to-exit-the-vim-editor) has made up about .005% of question traffic: that is, one out of every 20,000 visits to Stack Overflow questions. That means during peak traffic hours on weekdays, there are about 80 people per hour that need help getting out of Vim.

Has the percentage of traffic it makes up changed over time? That is, have developers started learning to exit Vim on their own?

![](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/05/exit_vim_over_time-1-1200x1200.png)

It doesn't look like it. The question was asked in August 2012, and for a few months it got very little traffic. Then it began growing in the following two years, presumably as more sources linked to it online and it moved to the top of search engine results. It's been relatively steady for the last two years. This doesn't necessarily mean the same people visited it again and again, of course; it could represent relatively new programmers getting stuck in Vim for the first time.

### Differences across countries

As we saw in [a previous blog post](https://stackoverflow.blog/2016/11/30/how-do-developers-in-new-york-san-francisco-london-and-bangalore-differ/), we can use Stack Overflow traffic to learn a lot about the geographical distribution of developers.

Let's consider what percentage of _visits to Vim_ this question comprises within each country. In countries with a lot of experienced Vim users, we'd expect this percentage to be low. When it's high, it indicates many users got stuck in Vim when they didn't necessarily expect to.

![](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/05/country_stuck_vim-1-2-1200x1200.png)

It looks like developers in Ukraine, Turkey and Indonesia are getting stuck in Vim quite a bit: it makes up a larger portion of their Vim questions than in any other country. In contrast, in China, Korea and Japan the fraction going to this question is a tenth smaller. That might indicate that when developers in these countries enter Vim, they usually meant to do so, and they know how to get out of it.

### What kind of programmers get stuck in Vim?

It's also likely that users of different programming languages will have different experiences with Vim. We can investigate this by stratifying the "Exit Vim / Total Vim" percentage across each user's **main programming technology**.

We'll define this based on what Stack Overflow tag they visit most often. (For instance, my most visited tag is [R](https://stackoverflow.com/questions/tagged/r): it makes up 52% of my question views). It's not a perfect measure, but it's reliable enough to give a sense of the breakdown by language. (For this analysis, we considered only registered users with at least 100 visits to the site).

![](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/05/exit_vim_by_language-1-3-1200x1200.png)

The developers who are most likely to get stuck in Vim are front-end web developers: those who primarily visit tags like JQuery, CSS, and AngularJS. They're followed by Microsoft developers (C# and SQL Server) and mobile (Android and iOS). These developers usually work with an IDE (Visual Studio, Eclipse, XCode, and so on), rather than a plain text editor, so it makes sense that they're relatively more likely to get "stuck" in Vim rather than to open it intentionally.

The developers least likely to get stuck in Vim are those who program in C, C++, Python and Ruby. This languages make sense to me: they are a combination of low-level languages and scripting languages that are often used with a plain text editor rather than an IDE, so they have the experience to escape it without a Google search.

### Conclusion

I was amused when I saw this question approach a million visits, but I was also proud that I work for, and contribute answers to, a site that helps so many developers. You never know when an answer you contribute could help millions of people, whether it shares how to [undo a git commit](https://stackoverflow.com/questions/927358/how-to-undo-last-commits-in-git) or how [the yield keyword in Python works](https://stackoverflow.com/questions/231767/what-does-the-yield-keyword-do-in-python).

If you want to contribute yourself, we encourage you to [join the world's largest developer community](https://stackoverflow.com/users/login?utm_source=so-owned&utm_medium=blog&utm_campaign=gen-blog&utm_content=blog-link), whether it's to ask and answer questions, get your next job, or [build your online presence with a Developer Story](https://stackoverflow.blog/2016/10/11/bye-bye-bullets-the-stack-overflow-developer-story-is-the-new-technical-resume/). In any case, next time you solve your problem through Stack Overflow, remember the hundreds of thousands of users who regularly ask, answer, edit, and moderate the site to make it all possible.
