# A Japanese Woodworker’s secret to good software design.

_Captured: 2015-10-01 at 00:26 from [medium.com](https://medium.com/@sschillace/a-japanese-woodworker-s-secret-to-good-software-design-c16158ce596c)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*kcsZxaT5eLFIdnEuqB6MKA.jpeg?q=20)![](https://cdn-images-1.medium.com/max/600/1*kcsZxaT5eLFIdnEuqB6MKA.jpeg)

This week at BoxWorks, we previewed an all new Box webapp experience that is beautifully designed and optimized for functionality. Often, design is only associated with the way that something looks, but it's really about the way an entire system preforms. I was reminded of this recently, after visiting the SF Pen Show last month.

At the show, we met a Japanese couple who were making wood pens. They were made from beautiful wood and were very simple, with clean lines and every detail well thought out. These pens were not particularly spectacular, but the attention to detail that went into them was immediately apparent, and they write better than anything I've ever used. As I examined the couple's wares, it was evident to me that the pen-maker was present at every step of the pen-making process. All of his pens are perfect, thoughtful items that he is proud to share and use.

Why am I spending so much time talking about fountain pens? In a word: design. We should strive to write code in the same way that this man makes pens. The word is often misused these days, but a good coder is an artisan, a skilled craftsman who takes pride in his or her work.

Right now at Box, we are in the process of doing some major redesigns of some of our systems. It's easy to think of these projects as the only ones where we need to be thoughtful about design, since there's so much invested in them. But the reality is that we all do design every day, and all of it matters, even (maybe especially) the small stuff.

Code without a sense of design isn't very valuable. At best, you're creating value in linear relation to the amount of time you spend. The reason engineers get paid well, and the reason the tech industry generates so much value, is that, if we do it right, the value compounds with effort (software that is designed well is easy to re-use), changing a linear relationship between value and effort into one that is geometric or even exponential. As an engineer, you should *always* be trying to achieve this compounding effect with your designs, not just because it adds more value to the company you work for, but because it makes you more valuable as an engineer. Plus it's just more fun.

There's no simple formula for good design. The difference between good engineers and great ones is often in the technical and design taste that the engineers have -- good engineers aren't 10x or 100x more productive just because they type faster!

Personally, I think about first principles. When you're coding, ask yourself some key questions:

> What is the fundamental problem I'm trying to solve? Does it generalize?

At its core, software engineering is problem solving, which means software engineers should be problem-minded. Always be sure that you have a firm grasp on what exactly you're trying to solve before you sit down to code. At Box, we are constantly balancing the needs of the CIO with the needs of the end user, so getting this right is really important. We always have to understand how it's solving a problem for each kind of user.

> What can I remove from the problem definition and still solve it?

This is often the most powerful way to design. Many of the most effective distributed systems designs I've seen rely on selectively dropping something (for example turning consistency into eventual consistency). Making sharing as simple as possible while also making sure the business has everything it needs to work well is a tough challenge. Simpler is always better though.

> How can I isolate the system and reduce side effects, so it's understandable?

I'm a pretty dumb programmer, so I like things to be simple and easy to understand. As we scale, it's impossible for everyone to understand everything all the time. We have to build a system of small pieces with well thought out, well defined behaviors.

Writing code is easy. It doesn't take much to learn how programming languages and environments work, or to hack something together until it does more or less what you expect it to do. That's something almost anyone can learn to do at a basic level. Writing code well, however -- code that scales, code that other people can understand, use, and build on -- that's hard. That's what everyone should aspire to. It's easy to lose this in the day to day, but that craft is important.
