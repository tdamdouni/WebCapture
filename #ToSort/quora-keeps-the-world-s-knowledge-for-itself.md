# Quora Keeps the World's Knowledge For Itself

_Captured: 2017-04-23 at 18:48 from [konklone.com](https://konklone.com/post/quora-keeps-the-worlds-knowledge-for-itself)_

![](https://konklone.com/assets/images/blog/quora/library-of-the-future.jpg)

> _The Stockholm Public Library's proposed Wall of Knowledge._

I recently made the mistake of answering a question on Quora: **"[What is it like to be a member of the 18F team?"](https://www.quora.com/What-is-it-like-to-be-a-member-of-the-18F-team)**

I have a Quora account, but I've almost never used it. I noticed this question because the user somehow found me and "asked" me to answer it, which caused Quora to email me. It's a fine question, the kind of question Quora excels at getting answered, and I think the [answers](https://www.quora.com/What-is-it-like-to-be-a-member-of-the-18F-team) it produced will stand as an accurate snapshot of how the early [18F](https://18f.gsa.gov) team feels about their job and their work.

Sadly, Quora's policy is to lock that snapshot in their own private store, and out of the historical record.

> Bothered that [@quora](https://twitter.com/Quora) blocks the [@internetarchive](https://twitter.com/internetarchive). [@quora](https://twitter.com/Quora)'s mission is to "share and grow the world's knowledge", but they don't really care.
> 
> -- Eric Mill (@konklone) [September 17, 2013](https://twitter.com/konklone/status/379965892747984896)

The [Internet Archive](https://archive.org) is one of the world's [most fantastical organizations](https://en.wikipedia.org/wiki/Internet_Archive), housed in a [majestic temple](http://www.sfgate.com/news/article/Brewster-Kahle-s-Internet-Archive-3946898.php), and is maniacally devoted to **_archiving the entire Internet_** since **_1996_**.

At the Archive's [Wayback Machine](https://archive.org/web/), you can search through and relive an unbelievably rich swath of the Internet's history. It's one of the most valuable and widely cited collections in the world, and it's actually difficult now to imagine tolerating an Internet without it.

But if you visit Quora's `[/robots.txt`](https://www.quora.com/robots.txt) (the Internet's standard for sending web crawlers a strongly worded letter) you'll see that they single out the Internet Archive for exclusion. The Internet Archive respects the robots.txt standard, and so [there is no Wayback Machine content for Quora](https://web.archive.org/web/*/https://www.quora.com).

Quora recognizes that this is significant enough to [merit an explanation](https://www.quora.com/robots.txt) in their `robots.txt`.
    
    
     # People share a lot of sensitive material on Quora - controversial political
     # views, workplace gossip and compensation, and negative opinions held of
     # companies. Over many years, as they change jobs or change their views, it is
     # important that they can delete or anonymize their previously-written answers.
     # 
     # We opt out of the wayback machine because inclusion would allow people to
     # discover the identity of authors who had written sensitive answers publicly and
     # later had made them anonymous, and because it would prevent authors from being
     # able to remove their content from the internet if they change their mind about
     # publishing it. As far as we can tell, there is no way for sites to selectively
     # programmatically remove content from the archive and so this is the only way
     # for us to protect writers. If they open up an API where we can remove content
     # from the archive when authors remove it from Quora, but leave the rest of the
     # content archived, we would be happy to opt back in. See the page here:
     # 
     # https://archive.org/about/exclude.php
     # 
     # Meanwhile, if you are looking for an older version of any content on Quora, we
     # have full edit history tracked and accessible in product (with the exception of
     # content that has been removed by the author). You can generally access this by
     # clicking on timestamps, or by appending "/log" to the URL of any content page.
     # 
     # For any questions or feedback about this please email robotstxt@quora.com.
    
     User-agent: ia_archiver
     Disallow: /
    

(_Update_: After publication of this piece, Quora added the first paragraph above. I've [updated the excerpt](https://github.com/konklone/writing/commit/c18b2118193b725376a7648112701e5eb283cb9f) above to match their current robots.txt.)

So, Quora's rationale for blocking the Internet Archive is that **Quora can't go back and automatically rewrite history whenever one of its users wants to**.

Bear in mind, you can already remove individual pages (in their entirety) from the Internet Archive by [adding them to your robots.txt](https://archive.org/about/faqs.php#2). Quora is asking for the ability to excise specific _content_ from already archived pages.

Can you imagine if the Archive implemented such a feature? It would make the Archive's historical record completely untrustworthy, and destroy its credibility. You can bet many people, companies, and governments would love the ability to go in and selectively excise or modify the historical record of their work.

But that's not how history works, and it's _definitely_ not how the Internet works. Quora is not a private communications network. When users contribute to Quora, they're participating in Quora's mission: to "[share and grow the world's knowledge"](https://www.quora.com/about). Like publishing a book, making a TV show, or any other form of human broadcasting: once it's out there, you can shape its use, but you don't get to withdraw it from the public record.

![](https://konklone.com/assets/images/blog/quora/library-of-alexandria.jpg)

> _The [Library of Alexandria](http://io9.com/the-great-library-at-alexandria-was-destroyed-by-budget-1442659066)._

What Quora is asking for from the Internet Archive -- and really, since the Archive has no public competition, from the Internet -- is unreasonable, short-sighted, and selfish. Quora is simply being a shark about "their" content, at the public's expense.

I usually try to be generous about people's motives, but I'm comfortable assuming the worst here. Quora's reason is simply too flimsy, and its business incentives too tangled up in the outcome, for their comment above to be the full story.

Quora is a free service built on [venture capital](http://blogs.wsj.com/digits/2014/04/09/with-80-million-in-new-capital-quora-still-has-no-business-model/) that will need to monetize its users over the next couple years, and wouldn't you know, they really want you to visit quora.com, and they _really_ want you to create an account.

In fact, until very recently, Quora would [block visitors from seeing more than the first answer](http://devilsworkshop.org/block-automatic-quora-login-popup/) unless they logged in. I'm willing to bet most people reading this have run into that popup before.

They've taken down the popup, but all that content is still entirely under Quora's control. If Quora was to collapse next year, it's completely unclear what would happen to the human output they've collected. This is not theoretical: unilateral mass destruction of user-generated content [happens](http://www.archiveteam.org/index.php?title=Geocities) [all](http://www.archiveteam.org/index.php?title=Friendster) [the](http://www.archiveteam.org/index.php?title=Google_Video) [time](http://www.archiveteam.org/index.php?title=Yahoo!_Video).

![](https://konklone.com/assets/images/blog/quora/quora-logo.png)

Quora's question-and-answer system is a generalization of the extraordinarily successful model of [Stack Overflow](https://stackoverflow.com), a Q&A site for coders that quickly became the world's free google-able university and teaching assistant for anyone working in technology.

It's not an understatement to say that Stack Overflow has completely changed how and how fast software developers get their work done today. If you were to chart the days I visit Stack Overflow, it would look awfully similar to the [chart on my GitHub profile](https://github.com/konklone). Stack Overflow has since expanded into the [Stack Exchange network](http://stackexchange.com), and in many ways is a direct competitor to Quora.

Like Quora, Stack Overflow is privately run, and like Quora, Stack Overflow depends on a community of active users to generate activity, knowledge, and [revenue](https://meta.stackexchange.com/questions/79435/what-is-stack-overflows-business-model).

_Unlike_ Quora, Stack Overflow has no problem being [archived back to Day 1 of its existence](https://web.archive.org/web/20141013225838/http://stackoverflow.com/) -- presumably because the founders understand how the Internet works and understand what it actually means to grow the world's knowledge.

Until Quora understands this, I'll be contributing my knowledge to the world, and not to Quora.

![](https://konklone.com/assets/images/blog/quora/archive-1.jpg)

> _The Internet Archive's ceramic archivists. Photo by Tom Foremski of Silicon Valley Watcher._
