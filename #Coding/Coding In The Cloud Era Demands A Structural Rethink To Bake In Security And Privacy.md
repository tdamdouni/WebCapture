# Coding In The Cloud Era Demands A Structural Rethink To Bake In Security And Privacy

_Captured: 2015-09-27 at 23:18 from [techcrunch.com](http://techcrunch.com/2015/09/27/bake-in-security-and-privacy/)_

![](https://tctechcrunch2011.files.wordpress.com/2015/08/368912557_2fc44d3709_b.jpg?w=738)

> _Protecting privacy in an age of big data, cloud processing and increasingly interconnected digital services demands a structural shift in how software is developed._

That's the view of academic [Jean Yang](http://people.csail.mit.edu/jeanyang/), who holds a PhD from MIT and has been conducting research around data privacy for several years - including devising her own programming language, called [Jeeves](http://projects.csail.mit.edu/jeeves/), which centralizes how privacy policies are handled in order to take the burden of correct enforcement off the shoulders of individual programmers.

"This helps programs be more secure because instead of trusting the programmer to write checks and filters and all those things correctly across the entire code, they just have to correctly attach the policy once -- and this reduces the surface area that that programmer's got to make mistakes," she explains.

"I spent many years as an undergrad thinking about this," adds Yang, discussing a forthcoming talk she's giving at the [Privacy. Security. Risk. conference](https://iapp.org/conference/privacy-security-risk-2015) in Las Vegas at the end of the month. "How come people don't care that their programs aren't correct and that programmers aren't writing programs that they intended to write?"

Yang reckons there has been a shift in attitude in recent years, with more attention being paid to the problem of problematic legacy code design because of increased concerns around privacy and security online.

2013 was of course the year NSA whistleblower Edward Snowden revealed the extent of government intelligence agencies' surveillance programs - an act that put the spotlight onto online privacy in general. The Snowden revelations also appear to have accelerated adoption of end-to-end encryption by (some) consumer technology services. Given that those self-same services were revealed to have become the de facto outsourced data-harvesting arms for state surveillance operations then locking down user data is now a political imperative for commercial entities concerned about user trust.

Meanwhile, of course, data breaches continue to make tech news every week - reinforcing an impression that current gen software and systems are not fit for purpose in an increasing interconnected digital world. The long and the short of all this is there has to be a better way - and that means rethinking how we program on a structural level, argues Yang.

"Here's the way I see it: the way we're programming is still very similar to the way we were programming in the 1970s," she tells TechCrunch. "Software used to be these tiny recipes. These tiny procedures. They were maybe 10, 20 lines… A lot of it used to be to calculate things like ballistics trajectories. Not sensitive data at all. Those programs were probably bigger than 10, 20 lines. So programs were either very small, and/or not operating on sensitive data.

> …programs that didn't even know about each other are sharing the same physical machine with very interesting -- perhaps terrifying -- privacy and security implications.

"Now the programs are huge. There are these whole software ecosystems. Programs are easily millions of lines of code. The size of this code didn't even used to be able to fit in computer memory a few decades ago. So the code is huge. So many people are programming it. Before you only had a very small number of programmers. They could keep it all in their heads. And they could all talk to each other easily. Now you have stuff on the cloud, you have stuff on virtual machines… programs that didn't even know about each other are sharing the same physical machine with very interesting -- perhaps terrifying - privacy and security implications."

Yang argues that a massive feature-rich data repository such as Facebook has "terrifying" implications for data privacy -- given it's unclear how the user's information is going to end up being sliced and diced by Facebook and Facebook users.

For example, she notes that users' information is not just displayed chronologically on their Facebook profile but can be searched in multiple ways -- via the [Graph Search feature](http://techcrunch.com/tag/facebook-graph-search/), for instance - meaning the user has little hope of understanding how the personal data they share on Facebook might end up being viewed.

"They have everything I described: millions of lines of code, this army of programmers, there's all these places in the code where sensitive data's being used. The programmer has to think at every point 'ok what policy should I be enforcing here?'" says Yang.

"The thing with Facebook is people complain 'oh the privacy policies are inconsistent, they seem to be changing all the time', but it's really hard for them because they have to protect your information not just directly through your profile but also if you're searching through Graph Search [or other avenues]."

Yang notes there are some existing engineering strategies to mitigate problems around enforcing privacy policies correctly - such as encapsulating policies in library function calls - but even then the programmer has to remember the points where they should be calling a particular library function. So she argues it's still "a real bottleneck".

But while she believes bigger structural solutions are definitely needed to properly secure sensitive data in the cloud era, she also cautions against hoping for too radical a shift in programming techniques. Getting ingrained habits and processes to shift is, after all, always an uphill struggle.

She believes more subtle solutions are called for - which let programmers carry on writing code in pretty much the same ways they're used to but which enforce privacy and security "under the covers", as she puts it. What that boils down to is technical solutions that do things like "encrypt your data for you in a way that you don't have to think that hard about", or which wrap systems in preventative procedures to stop "bad things from happening". A sort of data 'health and safety' ethos baked in from the get-go.

"These kinds of whole system solutions that aren't changing how things look will, I think, be the way to go," she adds.

This summer Yang and fellow PhD student Frank Wang piloted an accelerator at MIT called the [Cybersecurity Factory](http://cybersecurityfactory.com/). Their focus here is on academic entrepreneurs with deeply technical security solutions that seek to address the structural issues mentioned above. The pilot program was funded by [Highland Capital Partners](https://www.crunchbase.com/organization/highland-capital-partners) and the two initial teams -- Aikicrypt and Oblivilock -- included multiple PhDs apiece. The aim for next year is to run an expanded version of the program, taking in up to five teams and casting a wider net for which teams are selected, says Yang.

The opportunities for startups in and around data protection are becoming clearer, but a good part of the reason there is such untapped potential in this space are the extra layers of complexity involved with these businesses. Not least, as Yang notes, the fact the kinds of structural solutions that are needed can be a tough sell - given they're likely to be highly technical and therefore and abstract so likely harder to pitch to investors and customers than the average startup idea.

"If you look at the space for security startups, a lot of the ones that are successful are about finding bugs, finding vulnerabilities, if you have an existing system what's wrong with it already?" she notes. "And it makes sense that these companies are successful because as a startup if you're trying to find bugs, all you have to do is be able to go into a company, demonstrate that you can find bugs in their system and they can say oh yeah, you're useful.

"But if you want to help the system builders build the systems better in the first place, having frameworks for building the systems better or having things that -- for instance -- encrypt an entire layer over the data… it's much harder to do a company [sales pitch] or some type of type-transfer based on it. Because, first of all, whoever's buying a solution like this really has to trust you. And also these solutions are often deeply technical.

"If you have something that's providing guarantees throughout your system it's probably a deeply technical solution that's pretty abstract, it's hard to explain, It's very hard to explain to people."

For this reason Cybersecurity Factory's pilot program ended up focusing not so much on developing the ideas themselves as helping the teams with their sales pitch to customers and investors, and creating a network of customers, investors and entrepreneurs with relevant experience to help the startups take their ideas to market.

"It seems like for other kinds of startups there's kind of a set way to go. But for security it's such a relatively new space the way to go is different than perhaps less technical startups. And there's a new path that security startups should be taking. So we've been learning about what this new path might look like. If you're a technical enterprise company, how should you be looking for your customers? How long should you be waiting to find a customer? And how should you be pitching your ideas? So we've been learning these kinds of lessons," says Yang.

She notes that YC's Sam Altman has been paying some public attention to the security space in recent times - tweeting this summer how he wants YC to fund "dozens" of security startups in the "next couple of years" -- so there are signs investors are taking a closer look at the business opportunities in and around protection and privacy.

"There's definitely going to be a lot more security companies in this space. The question is what will the companies look like?" adds Yang. "And what I'd like to see [is] more of these technical solutions. Because yeah we can patch, we can do patches and we can find vulnerabilities all we want but the way I see it is the tools we're using are breaking under the strain of what we're trying to do -- and so without better tools things are just going to be hard."

Featured Image: [Josh hallett](https://www.flickr.com/photos/hyku/368912557/in/photolist-yALRk-7Cc8Ki-Bcz4z-4qwA15-asybHk-rcNFpT-8ADP5g-9rg8Mb-9r2dSX-hypjha-tBVvp-6m1CYz-6TCe9D-8bnteV-rRvcV-9HmR8k-7WnK75-5rYEJy-dQobVt-sRfUW9-6BcbG1-mjhubJ-qd5437-84nstx-5xizxo-7Cc822-rTJyYM-e1TC5K-t4TnZp-7XxVMY-qYbFGD-2djUni-5rS6Te-asAPd5-7RGZwQ-833n7j-85dBXk-8t8yb3-pjv28L-q85rAY-7RDJGV-7RGZrh-7RGZiU-7RDJjT-7RGZ9f-7RGZ4d-7RDJ6D-6b2Ung-475R2N-6Ld2NH)/[Flickr](https://www.flickr.com/) UNDER A [CC BY 2.0](http://creativecommons.org/licenses/by/2.0/) LICENSE
