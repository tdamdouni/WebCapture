# A useful web development standard from an unlikely source - The US government

_Captured: 2015-10-10 at 22:49 from [www.itworld.com](http://www.itworld.com/article/2989009/open-source-tools/a-useful-web-development-standard-from-an-unlikely-source-the-us-government.html)_

![us](http://images.techhive.com/images/article/2015/10/us-100619701-primary.idge.png)

> _Credit: CIO.gov_

I understand your apprehension on taking advice about web development from The United States government. The [Healthcare.gov](https://www.healthcare.gov/) catastrophe - an [approximately $180 million](http://www.washingtonpost.com/blogs/fact-checker/wp/2013/10/24/how-much-did-healthcare-gov-cost/) web application riddled with bugs and crashes at launch - is still fresh in the minds of programmers. It's a shocking number and an impressive failure, but you have to assume there are smart people elsewhere within the government who were not involved with that project.

I was recently made aware of the open source project dubbed "U.S. Web Design Standards" via Twitter:

> This is actually very cool. The U.S. Government (I know!) Web Design Standards. Useful stuff! <https://t.co/YKu075RoJY>
> 
> -- Scott Hanselman (@shanselman) [September 30, 2015](https://twitter.com/shanselman/status/649367052801564672)

[The site](https://playbook.cio.gov/designstandards/) lays out the recommended tools and practices for building U.S. government websites going forward. The entire thing is [even on GitHub](https://github.com/18F/web-design-standards) with clear instructions on how to bootstrap your project with the recommended tooling.

The standard defines the proper way to handle everything from which fonts to use, what CSS preprocessor to use, and how to name things - to how to organize your folders and even design templates to get you started on new projects. You can [read the entire standard here](https://playbook.cio.gov/designstandards/getting-started/).

What's interesting to me are not only the frameworks chosen but equally those which are not. It seems like every project we've started over the past couple of years begins with [Twitter Bootstrap](http://getbootstrap.com/). The ubiquitous framework is used with extreme frequency to get a new build off the ground quickly without having to worry about styling every little component from scratch. I pretty much assumed this is where the U.S. standards would start, but I was wrong.

Not only does the U.S. standard choose other frameworks, it specifically _does not_ recommend bootstrap for production sites.

> 18F specifically does not recommend using Twitter/Bootstrap for production work because of one, the difficulty in adapting its opinionated styles to bespoke design work and two, its CSS style places semantic layout instructions directly in HTML classes.

For CSS, the standard recommends using [Sass](http://sass-lang.com/) as a CSS preprocessor and the [Bourbon framework](http://bourbon.io/) to jumpstart layout development. They also define an alternative if you can't/don't want to use Sass and prefer something more lightweight: Yahoo's [Pure.css](http://purecss.io/).

I have to admit, this was kind of a wakeup call for me. Being a web developer and running a web development company I'm generally up on the trends and tools. Not only have I not done a project with either of these frameworks, I'd never even heard of Bourbon before this. As I read through the spec however, I began to see their rationale and have come to agree with their assessment of bootstrap. I've done countless projects with the framework and indeed it can work against your design goals at times. The other side effect is that, without considerable extra effort, bootstrap sites have a tendency to look very similar to one another. These guidelines push for more bespoke and original development which I really like.

A developers choice of tools can be personal. It never hurts to explore what others are doing and why though. These government guidelines are very well documented and have some excellent suggestions. Their font choices are appealing, their color pallet is pleasant, **it's all very modern**. Even if you don't want to adopt their entire toolset, there is something in there for everyone that can improve what you're working on today. If you work in web development you should definitely give it a read through.
