# The Different Types of Server Monitoring Software

_Captured: 2017-10-08 at 22:29 from [dzone.com](https://dzone.com/articles/the-different-types-of-server-monitoring-software?edition=329537&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-08)_

If you landed here from a Google search for "server monitoring software," then I don't envy you. You're probably searching for a specific answer to a specific problem, and you've no doubt learned that there are roughly 8,498 companies that offer server monitoring software. But the only thing they have in common? All of them can totally monitor everything that you might ever need monitored.

E-commerce has grown steadily in the last two decades, eventually coming to completely dominate our commercial world. So _a lot_ of people have _a lot_ of money invested in _a lot_ of stuff running on the internet. This, in turn, makes _a lot_ of people interested in monitoring that stuff, seeking to defend their livelihoods and gain competitive advantages.

Thus when we talk about server monitoring software, we're casting a pretty wide net. Too wide, in fact. Servers handle lots of things. Searching for server monitoring software will cause you to smack up [against the paradox of choice](https://en.wikipedia.org/wiki/The_Paradox_of_Choice). You have too many options.

You _could _ narrow the field in a number of ways. How much does the tool cost? What server operating system? Is it open source? You get the idea.

But today, I'd like to help you focus the scope of your search by acknowledging that servers are extremely complex, resulting in many different potential things to monitor. Let's take a look at the different types of server monitoring software as a function of what, exactly, they monitor. Get a better focus there, and you'll know what to look for.

### ![](http://blog.scalyr.com/wp-content/uploads/2017/09/iStock-806867250.png)

### Uptime/Availability Monitoring

Let's start simply. If you're concerned about any kind of server anywhere, you'll want to know if it's even reachable for people in the first place. Is it humming along, doing what it's supposed to? Or did someone trip over the power cord and take it completely offline? (If so, you should think about moving it out of a closet in your office and into somewhere this isn't a concern.)

[Uptime](https://en.wikipedia.org/wiki/Uptime) or availability monitoring software performs one of the simplest functions you can imagine. It just periodically polls your server to see if it's on and responding. This gives you a picture of how available (or not) it is to its users. You can find any number of [tools that offer this free, simple service](https://uptimerobot.com/). And this will almost certainly be your entry into the world of production monitoring.

### Site Performance Monitoring

So you've got your uptime monitor in place and you feel pretty good. Your website hardly ever goes down, and users can almost always reach it. But that doesn't mean that they're necessarily having a good experience.

Perhaps pages are taking forever to load. Or maybe many of your images fail to load altogether. A JavaScript library might not come down, rendering the page semi-functional. None of these issues would trigger an uptime monitor to regard your site as down, but you can bet that users will leave in droves.

Website performance monitoring will help you here, keeping track of all of the concerns that I've just mentioned. You can find [services that specialize in all things web performance](https://gtmetrix.com), letting you know not just that problems exist, but breaking those problems down in detail.

### Resource Monitoring

At this point, you might find yourself thinking, "wait, not all servers are servers for production websites." Indeed, performance certainly matters in contexts other than page load times and other web-specific concerns. Perhaps you have a server that's a backend for mobile apps or that's part of a distributed system. Performance can prove equally critical in these scenarios, obviously.

To address this, you can monitor all sorts of performance aspects of your server's operations by keeping an eye on its hardware resources. What's the CPU load? Is it consistently running out of memory? Might it soon run out of disk space? You can even [drill in and measure really granular concerns](http://openhardwaremonitor.org/), like temperature, fan speeds, and voltage.

By keeping an eye on all of these vital signs for your server, you can get advance warnings for things before they become problems. (Though, if you rely primarily on cloud providers, you may not need this particular type of monitoring, since they tend to handle this for you.)

### Error Monitoring

Anyone in the software game knows that errors happen. They happen all too frequently, in fact. As a result, error monitoring commands a niche set of tooling in and of itself.

Even in the most favorable circumstances, things go wrong. Users try to navigate to nonexistent URLs or they make illegal calls to your cloud-based service. You expect some errors. But you get concerned if that number spikes.

So you can actually instrument your servers specifically to [track and monitor application errors](https://airbrake.io/). This gives you an early detection scheme for your application code.

### Log Monitoring

Speaking of early detection, you might also want to monitor your log files. Which log files? Well, any and all of them.

Servers generate all sorts of application logs. Your custom software has log files (or, if not, it should). But so does the web server, the database server, the operating system, and just about every other relevant piece of software running on it.

You can [aggregate those log files and keep an eye on them](https://www.scalyr.com/product) to gain critical insight into your server's behavior. In a way, this provides some of the most comprehensive monitoring that you can do since everything else you might want to monitor tends to dump information into log files.

### Database Monitoring

A lot of people in IT might tell you that data is the motor of the technical world. It's so important that we gather tons of it, give it the simple moniker "big data" and then dedicate whole areas of study to "mining" it. Data helps with everything from election strategy, to mass marketing, to medical research.

So you're generally safe wagering that servers will have databases. And, since databases are everywhere, database monitoring deserves its own mention.

You can find software specifically to let you [keep track of what your databases are doing](http://go.solarwinds.com/dpa/en/database-performance-general). Are they performing well? Do applications put them to good use? Are there areas for improvement? Database monitoring can answer all of these questions.

### Security or Malware Monitoring

Everything I've talked about so far speaks to inadvertent problems. Slow page load times, overworked processors, and application errors all result from mistakes. But what about the problems that people cause on purpose?

Unfortunately, exploits and malware are big business. And they make their money by threatening your work and your business. So you certainly want software that monitors for vulnerabilities.

Anti-virus software has been around now for decades, but for a server, you'll want a more comprehensive approach. You can monitor for security issues both from the outside in and from the inside out. And you should. But you should also realize that you'll need expertise and ongoing creativity that go beyond simply installing a tool. Automated security monitoring is necessarily reactive, and you'll need to get out in front of this more than this form of server monitoring software alone will let you.

### Customizing for Your Own Needs

I'll round out the list here by suggesting that you customize your server monitoring software choices according to your specific needs. Understanding the different types of tools out there is a great starting point. It'll let you narrow down what you need and navigate the confusing maze of options and vendors.

But, you need to realize two things. First, you'll to need more than one of these solutions, in all likelihood. And secondly, try as they might, nobody is really going to be your one-stop shop for all things monitoring. Shop around, mix and match, and look for focused solutions instead of sprawling ones.

I say that because your business might, for its own specific reasons, need to monitor how many users named Bob log in on Wednesdays. And no matter how expansive the tooling options out there, they won't offer that. You'll need to understand your tools well enough to make that happen.
