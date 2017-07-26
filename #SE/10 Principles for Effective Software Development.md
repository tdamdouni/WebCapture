# 10 Principles for Effective Software Development

_Captured: 2016-03-23 at 22:59 from [medium.com](https://medium.com/p/aa5df91d0f00)_

![](https://cdn-images-1.medium.com/max/2000/1*sjpeJdx9jGWr9MPEfZIZJg.jpeg)

A few days ago I watched a really interesting video presented by [Harry Roberts](https://twitter.com/csswizardry) at dotCSS 2014. He talks about principles, or best practices, to become an effective front-end developer. In reality, however, these principles can apply to all kinds of developers. Below I have summarized these 10 principles and provided my thoughts on each.

#### 1\. The Simplest Option is Usually the Best

As engineers our job is to solve problems. We are curious by nature and many of us feel the strange desire to constantly learn new things, frameworks and technologies. Often in an effort to become better developers we tend to over-engineer solutions. Most of the time we feel the need to ditch everything that we know in favor of new paradigms, but most of the time it comes with a cost: the cost of overcomplicating things.

> No one appreciates over engineered stuff.

I couldn't agree more on this point. Whenever choosing a way to execute a solution, pick the simplest option. It's less likely to break, it's less complex, and it's easier to understand. In addition, it is always faster and cheaper to implement. Conversely adding levels of abstraction introduces the need to learn new ways of approaching a common problem. Less cognitive overhead when working at scale is always welcome.

I think it's important to stress the word "usually" in this principle because I would not always consider it a rule of thumb. There are certain cases where we need to sacrifice simplicity over adaptability, scalability and security. But more often than not these are rare exceptions.

#### 2\. Reduce the Amount of Moving Parts

Code that is simple and concise is always easier to maintain. As dependencies grow in a project the overall complexity of the code-base increases as well. This also increases the chances of injecting bugs and problems. It may seem easier to add a shiny new library that solves the problem faster, but in reality this introduces new problems that in the beginning you may fail to consider.

Any moving part we inject in a system comes with an added cost tied to its maintainability. So whenever you think about adding new things in a system think twice and ask yourself if the benefit of adding new dependencies will solve the problem in a more efficient manner or if it will only take you out of the problem temporarily.

> The best code is no code at all

I believe that whenever there is a chance of getting rid of something, it's better to choose that path instead of adding more moving parts to the system.Think of it this way: more code = more time spent maintaining, fixing, and refactoring. So next time you see the possibility of safely getting rid of something, do it. Every moving part of the system is a potential point of failure.

Refactor to reduce complexity. It's always a good exercise to try to refactor things in such a way that lets you simplify your solutions. I've found that it's most often a good idea to try to find the patterns that are core, and kill code and even features that don't add much value.

#### 3\. Understand the Business

Put yourself in your employer's shoes. Always think about where your effort can lead to the greater benefit. Understand the value of your work for the good of the company. Connect with everyone else's problems and always be ready to help. Know that others can avoid making the same mistakes you did by providing useful advice. This kind of mentality will put you in a much more valuable position in the long run.

Increasing your technical abilities is good for you but not necessarily for your company. Find a good balance between self-improvement and team-development. Remember that you are not isolated and that your work has a big impact even if you haven't realized it yet.

Know your strengths and also your weaknesses so you can be ready to guide and ask for guidance whenever needed. Understand all the things that make you valuable. Don't be just a developer, try to have a wider perspective and also understand how your work translates into wealth for your company. Don't just build features, create solutions.

#### 4\. Care Less, Care Appropriately

No one cares more about your work than you do. Often there are trade-offs that need to be made in order to keep the workflow running smoothly. You will always find different opinions about everything, Whilst it is sometimes useful to engage in a debate, you may not want to waste the time debating superficial stuff.

Know that every time you express your opinion, there is time spent by your colleagues, understanding you and responding to you. Be respectful of the time of others and also to yourself while expressing an opinion. So the next time you share something publicly, think twice on the value that it will add to your team's collective knowledge. Pick the right battles. Stand up whenever you are sure about something with humility and be open to hear opinions. Remember you won't always be right and that there is value in considering different points of view.

> Balance the needs and wants of everyone

Care less about your work but more for your team. Be less selfish and also be ready to make sacrifices for the good of others. Care more appropriately for everyone else's jobs. Remember that your work, words and opinions have an impact on your team mates work even if it's not that evident at first. Think about how you can make your teammates' lives better by removing stress, not adding it.

#### 5\. Pragmatism Trumps Perfection

It is better to be timely than perfect. Things change fast in our industry. We are continually trying to innovate and find new ways of making better products. Sometimes in an effort to ensure the quality of a product we make certain trade-offs. I am not saying quality is not important; every company should have at least a basic set of quality standards so every product provides the best experience possible. But in my opinion there should be a right balance between good enough and perfection.

> Good enough today is better than perfect tomorrow

Measure features based on business value. Don't wait so long to release. Does it work to the minimal quality standard set by your company? If so, ship now to solve the core problem and assign some time to refactoring tasks later (Make sure you do, otherwise quality can deteriorate over time). Measure every feature built based on its business value and prioritize accordingly. Nothing is or will ever be perfect. You shouldn't delay a project for superficial decisions. Focus on defining what is the minimum viable product and ship it as fast as possible. Later you can spend some time refining the experience. Something hacky that works today is better than something perfect that works next week.

#### 6\. Think at the Product Level

Your job is not just to produce features as if you were a factory. Whenever you are asked to build a feature is always good to give it some thought and ask yourself how much value your work is adding to the product. Don't be afraid to respectfully question management decisions. If you are not convinced on something, make sure you discuss it with your leads before going down that path.

I am sure they will find your opinions valuable or will light your way in case you are failing to see a broader scenario. Do it with respect and be flexible. Great managers are good listeners that will value different perspectives, and will try make the right decision based on the knowledge they have.

Think of the all the factors in play, whether it's team velocity, complexity, or productivity. Make decisions considering all possible factors. Get involved with everyone else's issues, don't just do your job. Be informed about the context of the project and make decisions that add value.

#### 7\. Don't Design Systems Around Edge-Cases

Don't let edge cases rule your product decisions, but rather focus on what yields the most benefit. Consider first solving the problem for your core audience and work on refining the experience later for edge cases. In other words, don't let the minority lead the majority, and don't base an entire product based on statistical outliers. These rare cases where something does not work for a specific segment shouldn't hold back the release of a product.

Think of your major user base and design for them not the rare anomalies. Build for the most common scenario first. Solve edge cases separately and later in the process. Define your ideal core user base and solve problems based on hard statistical data (for example browser usage). Sometimes we may spend a lot of time fixing a bug that affects only a minimal amount of users. If it's not critical, you shouldn't jeopardize the release of a product in the quest for perfection.

Everything is prone to have errors, and everything will be buggy, but know that releasing a product on time could yield to greater benefits than delaying the release for very uncommon situations. Have a release strategy and make sure you allocate time to fix those nasty errors but just don't wait until those are fixed in order to start gathering data or even ROI.

#### 8\. Don't Make Decisions Based on Anecdotal Evidence

Whenever someone tells you something is great, do you research before taking anything for granted. It's easy to jump into judgment and conclusions too quickly if something does not fit our current mindset. Do your homework, try to make unbiased decisions and always look for different opinions on the matter.

In general, rare anomalies or strong opinions that don't fit the common denominator are based on lack of understanding or deep introspection. If the later is the case, you should consider it. Make sure that those opinions are based on first-hand experience and careful analysis.

Don't believe everything that everyone says, but rather draw your own conclusions based on factual data. Anecdotes are not always representative, and may lead you to wrong decisions. Never trust gossip, always trust data.

#### 9\. Don't Build it Until you've Been Asked for it

It is really tempting to come up with a shiny new solution that wows everyone by how smart and innovative it is. But most of the times building something without everyone's approval is disrespectful not only because your time is costly to your employer but also because everything that you build has a maintenance cost.

It's really cool to over-deliver, but think twice before implementing things. Is it a requirement now? Are you 100% sure it will have a positive impact? And most important, is it approved by management? Maintaining things that nobody asked for is irresponsible. Solve every single problem whenever you encounter it, not before. Don't do work ahead of time.

It is not smart to solve problems that nobody has now. Be smart about how you use your time and the next time you want to create something awesome discuss it with your leads before doing so. I am sure if its really good you will have an approval sign and support from stakeholders to execute. Remember that communication is key for proving yourself valuable. It shows you understand how things work and that you are aware how your work impacts the organization.

#### 10\. Expect and Accommodate Change

Worry about something that solves the problem right now. Tomorrow's technology will most likely change, so you will need to adapt anyway. Focus on something that fixes the problem but be flexible enough to let the next developer easily adapt to your code. Make sure you can undo things.

Surely I've been bitten before for not following these principles, which is why these principles resonated a lot, I really wish I would have heard this before I started working with a team, since it could have made me so much more valuable. Now it's time to apply them as much as possible. What do you think? Are there other principles that you think are important? I would love to hear your opinions!

Watch the video of Harry Roberts at dotCSS2014 below:
