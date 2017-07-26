# Facebook’s Four Business Design Principles for Crafting Elegant Tools

_Captured: 2015-12-16 at 13:20 from [medium.com](https://medium.com/elegant-tools/facebook-s-four-business-design-principles-for-crafting-elegant-tools-581a7055dee8#.hke3gzkmm)_

![](https://cdn-images-1.medium.com/max/2000/1*YqTsf-vsKY1iDCrP-nlE0g.jpeg)

When I joined Facebook three years ago to lead Business Design, I faced a steep learning curve. I had spent my whole career designing consumer experiences and loved every minute of it. Yearning for a big new challenge, I decided to dive into the less visible but equally high-impact world of B2B/enterprise software, helping Facebook realize its enormous potential as a marketing platform. My job was to build a team that would drive the research and design for Facebook's advertising products, helping organizations of all shapes and sizes connect with people all around the world in meaningful ways. It was new territory for me.

But I wasn't the only one learning how to design elegant tools for the 2 million-plus businesses that Facebook partners with every day. The whole company was facing that challenge. While it's safe to say that Facebook has proven itself to be exceptionally good at building engaging consumer experiences, we did not have that reputation in the business context. Building B2B and enterprise software had not historically been one of our corporate core competencies and, in the past, that lack of expertise in designing for businesses was reflected in the quality of the products we shipped. We wanted to do much, much better, but we had to learn how.

So it was with a lot of humility that we engaged in an exploration of what great product design means in the work context. Certainly there are universal truths about what good design is. Good design should solve a real problem. It should be easy to use. It should be well crafted. We knew we wanted to create the most effective advertising software in the world, and we are blessed with an engineering team that cares a lot about product quality. But in order to hold ourselves accountable and maintain a high standard of quality, it was critical for us to define some principles around what product quality really means in the work context, and how it differs from consumer design.

Unlike in the consumer space, there aren't many heroes after whom we can model ourselves in the business context. [I've written before about the low bar for quality in business tools](https://medium.com/elegant-tools/my-grandfather-s-drill-and-what-it-can-teach-us-about-designing-business-software-8a76f533e55c). We are working to change that for our own company and the larger ad tech industry we are a part of. In the longer term, we hope that doing high quality work and sharing what we learn along the way might benefit other industries with equally complex ecosystems, such as healthcare, education, financial services, and government. Improving the software that drives those systems and industries would be good news for all of us and, in particular, for the many people who are often stuck using poorly designed software to get their jobs done.

We've learned a lot over the past few years, through trial and lots of error, about what great business tools look and feel like, how they work, and how they impact people's productivity and success. We've found that there are some consistent themes that arise when designing tools for most work contexts -- not just advertising, where my team is principally focused, but also other business-related tools like content management systems, developer tools, or even internal tools like expense reporting and performance management products. We've boiled down our learnings into four guiding principles for designing great business products.

### **1\. Help people learn and grow.**

#### Teach people to make the best choices, increasing their confidence and success.

When we design for people's work, we must take on the responsibility not just of helping them complete discrete tasks but also get better at their jobs. This means understanding the levers that will help them grow their business or succeed within their organization. Then we must design the experience to help them constantly become more effective at what they do -- achieved through effective inline help documentation, notifications that prompt people to take the right action at the right time, and training people on the best practices that will take their work to new levels of success.

Think of your product as a personal trainer for each of the people using it. Ideally, every person gets a personalized experience that meets them where they are, and then stretches them to achieve things they didn't think were possible. So what does this look like in practice?

In the past, Facebook's inline help for businesses provided explanations and definitions of various features and terms, but it was generic and didn't take into account the broad diversity of the businesses accessing our advertising tools. Our customers range from first-time Facebook Page administrators and advertisers to seasoned professional marketers. But our system fell somewhere in the middle, and because it didn't optimize for anyone, it tended to under-serve everyone.

We now have a framework for smart inline help that's a great example of this principle in action. Internally, we call it "Actions You May Take," or AYMT, and the help it provides isn't just tool tips or hover cards that improve clarity around a specific feature. Instead, it offers more substantial, personalized guidance.

![](https://cdn-images-1.medium.com/max/800/1*T4BG9rIGzQzUIVrsY1zBqQ.png)

> _Examples of Facebook Ads "Actions You Might Take" system, which guides and coaches people throughout the ad creation and management experience._

The goal of AYMT is to take into account advertisers' and Page admins' lifetime account activity and performance, and to suggest ways to correct issues, fix problems, and help them improve results for their Facebook business activity. The guidance is dynamically generated for each user, personalized to each business that accesses the system. AYMT also provides customized context on the performance of a Page or ad campaign by comparing it to that of similar types of businesses, making the data a lot more meaningful than just the raw results. This kind of coaching feels good all around, but does it really work in terms of driving the business forward?

Last year, we did a master holdout for the entire AYMT framework, which meant that the people in the control group got no AYMT tips whatsoever. The result was that exposure to the AYMT system results in a sustained 4 percent lift in overall active accounts. When you are dealing with 2M+ businesses, that is a _lot_ of people and a _lot_ of additional engagement in our marketing tools. And it shows that proactively helping people learn and grow really works. Users don't just learn how the system works -- they learn how to make it work for them.

### **2\. Balance efficiency and effectiveness.**

#### Improve how people work so they achieve their objectives with the least amount of effort.

In the consumer space, we often look at the amount of time people spend using our product as an indicator of the quality of the product. The more engaging an app is, the more time people will spend using it, so we measure "time spent" carefully and try to increase it.

But in the work context, maximizing time spent is an anti-goal. We want people to be able to realize the full value of our products in as little time as possible. So efficiency is a critical principle for which we design. If we can shave off even a small percentage of time from a task that people do many, many times a day, it starts to add up in terms of efficiency gains. That time can then be spent doing more engaging, creative, and fulfilling tasks, or maybe just allowing people to get home a bit earlier each day.

Last year, we launched a redesign of Atlas, a product that allows businesses to use Facebook targeting abilities to market across all kinds of digital experiences outside of the Facebook properties. This means you can use Facebook targeting to improve the relevance and performance of ads on other websites and applications other than Facebook properties. It's a complex tool that is used by expert agency professionals.

Prior to the redesign, "classic" Atlas had gone for years with little or no design love. In researching the customers' experience, we heard from one user describing a particularly inefficient task, and it's become a legendary articulation of failing at this principle:

> "This is hands-down the most time-consuming process and the least efficient thing that I do in my life. I am confident with that statement. There is no doubt in my mind that is true. People have wasted years of their lives doing this."

_-- Participant testing "classic" Atlas,  
prior to the redesign that launched in September 2014_

What strikes me about this quote is not just the frustration expressed but also the hopelessness. It practically screams, "Doesn't anyone care about how inefficient this experience is for me?" Atlas is an enterprise tool that some people use for many hours a day. The repetitive tasks this participant had to do in the old tool were clunky and inefficient, and the frustration understandably accumulated over time. When you rely on products to get your job done and spend significant parts of your day using specific tools, efficiency is critical. So we study flows to streamline then as much as possible to shave time off each task.

> But myopically focusing on efficiency can create problems. If you oversimplify in the interest of efficiency, you might end of making the tool faster to use but create the wrong outcomes.

One example of how we strive to streamline the experience while keeping it effective is through a wholesale redesign of our ad creation flow experience, launched in late 2013. Historically, the ad creation interface focused heavily on the ad format details and placement of the ad (in the right-hand column of Facebook on desktop, within the Newsfeed, etc). The flow that followed was generic, regardless of the type of business you were promoting or what you were looking to achieve with your marketing dollars.

![](https://cdn-images-1.medium.com/max/800/1*JhhQrun2yLVkDIqq_cgI-w.png)

> _The old Facebook ad creation flow, which neglected to ask a key question: what business objective are you trying to accomplish?_

In late 2013, we launched a redesigned of all of our Facebook ad interfaces. The most important change was that the ad buying process would now always start by asking what business objective the person was trying to achieve.

![](https://cdn-images-1.medium.com/max/2000/1*JJl0ibN5Mr1APLAQoTNprA.png)

> _The redesigned ad creation flow which asks first and foremost, 'What are you trying to accomplish?"_

Once we understood the business's objective, we could significantly streamline the flow in smart ways. Objectives-based design focuses all of the ad creation tasks and elements on the things that are particularly relevant to, say, bringing customers into a local retail store, or selling products online. As a result, we are able to strip away irrelevant or non-essential elements of the ad creation flow, increasing the efficiency of a task that some marketers may repeat many, many times a day. As with most good design decisions, it seems perfectly obvious in hindsight, but this was a new way of thinking about ad creation, and one that has been emulated by others since our launch.

There is still a lot of work to do in optimizing the experience of our ad creation tools, but by shaping the experience around the business's end goal, we are more likely to achieve that balance of efficiency and effectiveness.

### **3\. Bring clarity to complexity.**

#### Create intuitive ways for people to tackle complicated topics and workflows.

Business tools can be extremely complex. We aspire to put powerful technology and useful insights into people's hands, but finding the right balance between simplifying it and giving access to innovative, advanced functionality can be difficult. In the consumer space, we strive to reduce the design to the simplest form possible, eliminating complexity at every turn, often focusing people on a single path and call to action. In business, however, we're designing for a population with sometimes radically different levels of expertise.

For Facebook ads, these tools serve a wide variety of people. Many business users are completely new to digital advertising, and some are new to advertising in general. These folks don't think of themselves as advertisers or marketers; they just have a product or a service or an idea they passionately want to share. At the other end of the spectrum there is a much smaller but crucial population of professional marketers -- experts in large corporations or agencies, working all day in software tools which are supposed to help them do their jobs.

The persistent challenge we face is to figure out how to take all of that advanced technology and make it accessible to people who aren't necessarily experts, while also provide providing experts with access to the advanced features and functionality that they want and need to do their work. Business workflows and technologies have inherent complexities that must be understood and respected, and yet everyone benefits from the elimination of unnecessary complexity.

In a sense, this is the [Goldilocks effect](https://en.wikipedia.org/wiki/Goldilocks_principle) made manifest in design: the optimal solution must fall within certain parameters rather than at the extremes.

> With a complex piece of UI, if you don't simplify it enough, people can't figure out how to use it. But if you swing too far in the other direction and _over-simplify_ it, you risk dismantling the very value that people are looking to access through the tool.

To make matters even more challenging, each person accessing the tool has a different level of experience and domain expertise. The "Goldilocks zone" of the optimal solution isn't static; the UX sweet spot varies in response to the individual's needs and abilities.

Facebook's advertising targeting UI is a great example of the challenges involved in bringing clarity to complexity. Facebook offers unparalleled targeting capabilities; we can help businesses of all shapes and sizes get the right message to the right people at the right time and place in a way no other marketing platform can. But with that very power comes significant complexity. The targeting UI of our advertising systems is one of the most difficult design problems in all of Facebook product design. And the stakes are high if we don't get it right.

If we don't succeed in bringing clarity to the complexity of this part of the product experience, people won't target the right audiences for their message. If people get the targeting wrong, it essentially undermines the main value proposition of Facebook marketing. These businesses will have wasted their marketing dollars reaching the wrong people, they will become enormously frustrated in the process, and they may understandably lose trust that Facebook marketing works.

But if we do get it right, and they do reach the right people, it will be the most cost-effective form of advertising they can do, and they will feel empowered, confident, and successful. And in the process, we will have achieved something even greater: we will have leveraged Facebook's ability to dramatically increase the relevancy and value of advertising.

Over the past few years, we've made many changes and improvements to our targeting UI as we look to balance this complexity with ease of use.

![](https://cdn-images-1.medium.com/max/1200/1*PFntIBvtqOJ87VYGsu4Yvw.png)

> _Facebook ad targeting UI, before and after significant simplification and usability improvements._

We regrouped the core sections of the UI into Demographics, Interests, and Behaviors, which makes it easier to find targeting criteria and broad enough to accommodate future targeting options. Our content strategy team led the creation of an improved taxonomy for targeting categories that is significantly more intuitive and reduces overlap. And instead of showing all the functionality inline, we reveal some advanced features through [progressive disclosure](https://medium.com/r/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FProgressive_disclosure), allowing advertisers to build sophisticated targeting audiences with a UI that grows in complexity alongside their needs. These changes, among others, have significantly improved the success rate of advertisers moving through the flow and help marketers more often reach the right people.

### **4\. Be accurate and predictable.**

#### Provide reliable controls and relevant feedback that build trust in our products.

When a consumer app doesn't perform as expected, it's annoying but not usually a catastrophe. But when a business application fails, people lose money, customers and, in extreme cases, their jobs. That's why the accuracy and predictability of the experience are so paramount with business tools.

When we use products in our personal lives for entertainment, a certain amount of serendipity and surprises can be fun. But in business, surprises can cause more harm than good. Say you run an ad campaign on Facebook to drive customers into your physical retail store to buy a certain product, and you plan for a certain result in the form of an estimated number of people who show up. You run the campaign, and the result is 10x what you planned for. This sounds like good news, right?

There are two possible problems with this scenario. First, if you don't know what caused the unexpected success, you often can't replicate it, which can be frustrating for a business owner or marketer who often has limited time and funds to experiment.

Second, while an under-performing ad campaign is obviously a problem, over-performance can also cause trouble for businesses, depending on the business objective. If you planned for a certain among of foot traffic and stocked the appropriate amount of product but 10 times that many people came in, you'd run out of inventory and fail to meet customer demand. Suddenly that "happy surprise" has caused enormous customer services issues and negatively impacted your business and its brand.

> Predictability and accuracy aren't sexy words, but they are table stakes for products that businesses can count on.

For a company that is used to moving fast and pushing the envelope of what's been done before, being accurate and predictable can be challenging. But we are finding real and meaningful ways to engender trust in the accuracy and predictability of our products.

For example, our large brand advertising clients -- think companies like Proctor & Gamble, Coca-Cola, Toyota -- have historically had trouble integrating Facebook into their marketing plans, in part because they plan well in advance and need to "lock in" specific marketing opportunities. These needs were challenging for us to support because Facebook's ad system has traditionally been auction-based, a flexible system that allows for advertisers to buy ad space at the best market price. While this is advantageous for many advertisers, it was a challenge for our large brand advertisers who need a more predictable guarantee of the number of people they can reach for a specific budget.

To meet this need we introduced a new buying type called Reach & Frequency.

![](https://cdn-images-1.medium.com/max/2000/1*QzGXMgCEjSvAeSh_EY2PGw.jpeg)

> _Facebook's new Reach & Frequency tool allows large brand advertisers to accurately predict the audiences they will reach and stay within budget._

This feature allows large brand marketers to buy ads based on what they care most about:

  1. How many people see their ads (reach) and how many times they see them (frequency)
  2. The ability to predict exactly how much they will spend so they can plan large campaigns
  3. What their spend will deliver

We still have many areas where we can and should improve the accuracy and predictability of our products; it's a goal that we work towards but will never perfectly achieve. But with each step we take, we engender more trust with our customers.

We hope these principles can be a helpful framework for teams in other companies and industries who are tackling similarly complex problems. And we hope we can look back a decade from now and see this as a time when business and enterprise design made a massive leap forward in quality, catching up with and maybe even occasionally exceeding the state of consumer design quality. If we succeed, these elegant tools could dramatically reduce the significant waste of financial and human capital produced by bad software. And even more importantly, at a human level, we can help people be more successful, and, ultimately happier in their work lives.

![](https://cdn-images-1.medium.com/max/800/1*5Ngln9V72JA83h6C8j08Sg.png)
