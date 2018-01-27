# Build it, Buy it, or Open Source: The Software Dilemma

_Captured: 2017-11-17 at 21:30 from [dzone.com](https://dzone.com/articles/build-it-buy-it-or-open-source-the-software-dilemm?edition=335891&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-17)_

### In this post we tackle the age-old question: When it comes to software, do you build it, buy it, or open source it? Read on for some insight.

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

One problem that all developers and companies struggle with is trying to decide if they should "build it" or "buy it." **Software developers love to build things.** That is what we do! Their natural reaction tends to lean towards building things. We are also always up for a new challenge.

## How Do You Know When You Should Build Software or Buy It?

There are very good reasons for building things. There are also good reasons to use open source projects, which is a third option!

### Some Things You Never Want to Build

I started my last company in 2003. In the early days of that company, I decided that it was easy enough to store customer credit card numbers in a database table and process them via Authorize.net. Simple stuff, right?

Billing systems always seem simple. Until you have to figure out how to handle if someone cancels in the middle of a billing cycle, switches plans, free trials, discounts, and a million other little things that add up to a nightmare.

What we did at my last company was also way before PCI compliance. The idea these days of even touching a credit card number sounds like a terrible idea. Plus, in my new company [Stackify](https://stackify.com/), our billing needs are much more complicated.

In my opinion, the last thing you ever want to build is a billing system.

### Open Source Is Another Option

A few years ago, I was talking to the CTO of a really large software company. I was actually having a whole conversation with him on this topic of build vs buy. Because they had so many employees, they felt that it was cheaper for them to build software rather than pay expensive licensing fees for every one of their employees. They had thousands of developers. Hiring a couple more was no issue to them.

He said they went as far as to build their own version of Excel. This literally about knocked me out of my chair. These days there are lots of Excel alternatives, such as [OpenOffice](https://www.openoffice.org/), Google Sheets, etc. OpenOffice is free and definitely a good alternative. I think they went down the path of writing their own spreadsheet software before free alternatives like OpenOffice came to market.

These days, perhaps they are a major contributor to OpenOffice. This is why open source products like OpenOffice exist. It doesn't make sense for someone to make their own version of Excel, but it might make sense to work with several other companies as a **community to build an open source solution**.

These days, developers use a huge array of open source tools to actually build new software. Virtually every programming language, including .NET, is now open source.

Source: [GitLab](https://about.gitlab.com/2017/03/03/why-choose-open-source/)

There are also a lot of open source monitoring tools that developers can use.

### Should You Build Your Own Application Monitoring Stack?

In the old days, most people used the open source monitoring tool Nagios for just about everything. Not because it was good, but because everyone used it. These days, monitoring has morphed in two directions: [application monitoring](https://stackify.com/application-monitoring/) tools vs infrastructure monitoring tools.

Infrastructure monitoring is still pretty simple. It is primarily based on monitoring servers, storage, firewalls, and other hardware. Some also support monitoring key metrics from things like SQL, Redis, etc. Using Nagios, PRTG, Zabbix and other tools is pretty sufficient for a lot of people.

Application monitoring is much more complex because it requires several sources of data. This includes basic server monitoring, metrics from your application runtime, application logs, application errors, and code-level performance data.

Building your own application monitoring stack is hard because it requires so many pieces. To build your own, you would have to combine things like Nagios, Graphite, Elasticsearch, StatsD, and Sentry. You would still need add an [APM solution](https://stackify.com/what-is-apm/) to the mix to get the code-level performance data.

### When Do You Build vs When Do You Buy?

Most people would say that you never want to build anything unless it provides **strategic value** to your company. Like most companies, we use products like Google Analytics, Zendesk, Hubspot, billing systems, [appointment booking software](https://gigabook.com/), chat, and other things. Trying to build any of these would be a pretty huge waste of time.

Sometimes you do need to build things though. A friend of mine has a company that relies heavily on partners to sell his software. He needed a really good way to distribute information to these partners and keep them organized to sell his software. Having success with these partners was mission critical to his go-to-market strategy.

After doing some research, he couldn't find any off-the-shelf solutions to manage these partner relationships. He had to build it. It was very strategic to his success. The product he built around managing partners ended up being so successful that it turned into a second software service that he could sell!

### Can You Build It and Sell It?

I know someone else that has a business that buys a lot of concert and sports tickets and resells them. They buy them all with credit cards, which causes them to accumulate a massive volume of credit card points. To help optimize the value of the points, they figured out how to sell them for a premium. As entrepreneurs, they decided to make a business out of that.

This same entrepreneur sent so many tickets with UPS and FedEx that he also figured out that many times they were not being delivered on time. If the shipping carriers don't deliver on time, you technically are due a partial or full refund of some form. They also spun this out into its own business.

For some companies who are run by very entrepreneurial leaders, building something in-house could lead to a new profit center!

### 4 Reasons to Never Build Your Own Software

#### 1\. More to Support

One of the great analogies I learned from a coworker is that every line of code that you write is another line of code you have to forever carry around with you. You have to support that code. It weighs down your backpack as you are trying to climb the mountain.

#### 2\. Time vs Money

What is your time worth? If you can spend $100 on a 3rd-party component to send FTP files or something, why spend hours writing your own version? Spend a few bucks on something that you know will work and you also don't have to support.

#### 3\. Opportunity Cost

Opportunity cost is another big factor. What could you have gotten done that would have made a big difference to your company?

#### 4\. Quality Is Important

I could easily write my own version of a lot of things. But the quality of it would never be the same. Someone who wakes up every day focused on creating the best X in the world is always going to do provide a much higher quality solution than I would cobble together.

## Conclusion

As software developers, we love to build things. It is in our blood to say, "yeah, I could build that." Building things that are not of strategic value can be a distraction and definitely take away your opportunity to work on something else that could have been very strategic.

One good reason to build something in-house is if you think you could sell it to other companies. Smart entrepreneurs are always looking to solve problems and build businesses. Learning first hand how to solve problems that others have is a good way to start up a new business.

Working with other companies on open source projects is another great solution. Building your own version of Elasticsearch would be a huge undertaking. Forking it or submitting a pull request with a new feature would be a great idea.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
