# DevOps Transformation Using Theory of Constraints - Part 1

_Captured: 2018-05-04 at 17:20 from [dzone.com](https://dzone.com/articles/devops-transformation-using-theory-of-constraints?edition=376246&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-05-04)_

**Don't let inefficiencies in software testing lead to delayed deployments and poor quality products. Get the [90 Days to Better QA](https://dzone.com/go?i=290423&u=https%3A%2F%2Finfo.rainforestqa.com%2F90-days-to-better-qa%3Futm_campaign%3D90-days-to-better-qa%26utm_medium%3Ddisplay%26utm_source%3Ddzone) Guide by [Rainforest QA](https://dzone.com/go?i=290423&u=https%3A%2F%2Fwww.rainforestqa.com%2F%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone) for best practices to avoid these common pitfalls.**

For several years, IT companies have been exposed to more and more blogs and conferences talking about DevOps, arguably the hottest topic since Agile. Those who follow the DevOps movement for some time might have also noticed that many presentations and blog posts repeatedly mention the Theory of Constraints by Dr. Eliyahu M. Goldratt. In fact "[The Phoenix Project](http://amzn.to/2lal8mE)," a book which many consider a must-read for any DevOps manager, was declared by its author Gene Kim that it was written using the exact same structure as Dr. Goldratt's best seller novel "[The Goal](http://amzn.to/2kOdZMt)."

The DevOps movement is full of ideas on how companies should improve, these ideas are created standing on the shoulders of several giant thinkers and doers who in turn transformed whole industries with their own ideas. One such giant is [Dr. Goldratt](http://amzn.to/2laplXA), others include [Dr. Edward W. Deming](http://amzn.to/2lxAcvH), [Taiichi Ohno](http://amzn.to/2lMZ4lo), and even Henry Ford, all of which have laid major contributions to management in manufacturing and multiple other industries.

Every time I attend a conference or watch a video where a speaker mentions ToC or Dr. Goldratt, it makes me really pleased to see that we are learning the lessons of the past. At the same time, I wonder: "How many people in the audience have read any Dr. Goldratt or Dr. Deming books?". There is probably no survey that can definitively answer this question. I believe that either Theory of Constraints coupled with DevOps talks is a vast echo chamber, or much more likely simply a large portion of the audience have not actually read any of the books or discovered the knowledge to understand this connection of DevOps and ToC. Those who do know ToC and Lean can be clearly distinguished, in many cases, these people don't shut up about it (in a good way).

While watching yet another video of such a presentation from the DOES16 conference, called "[Beyond the Phoenix Project](https://www.youtube.com/watch?v=TvgKHNts0WQ)" -- I decided to re-read and re-listen to the ToC ideas and provide my own narration to glue ToC and DevOps tighter together. I would like to quote Dr. Goldratt and light a wider spotlight on the IT industry using my interpretation of what he might have thought. (Disclaimer: I have re-read the books and watched the videos and listened to recordings more than once in the last decade. I try and keep the explanations as close as possible to what these great men and women are explaining, but any and all mistakes in understanding and interpretation are mine and mine alone.)

Let us start with a quote:

> "Technology can bring benefits if and only if it diminishes a limitation." -- Dr. Eliyahu M. Goldratt 

Dr. Goldratt begins with this quote in his "[Necessary but not Sufficient](http://amzn.to/2lN04X2)" book in his discussion on the role of technology. It is also the first topic of his "[Beyond the Goal](http://amzn.to/2m9AjAG)" audiobook and explained as the basis for all the logic derived to prove his point. He has repeated this basic assumption many times in other lectures and presentations.

According to Dr. Goldratt, to bring about a technology-based change that will have an effect, one _must _answer four questions. All four must have answers, or else the assumed benefit from implementing this technology cannot be gained.

  1. What limitation does this technology diminish?
  2. What were the policies and rules that governed before trying to adopt this technology?
  3. What must the new policies be when this new technology is used?

Let us take "DevOps" as an example of a "technology" in the broad sense of the word, and try to answer these four questions.

## Q1: What Benefits Do DevOps Bring?

The buzzword "DevOps" has become so overloaded that rarely two different people can agree on what it means anymore. Therefore the answer is not apparent. First, I will try and define the term DevOps using the same notions employed by those who coined the word, and not rely on the interpretation of those who guess its meaning after the fact.

> "[DevOps] … has a tremendous impact on the business. The technical team starts pulling together as one. An 'all hands on deck' mentality emerges, with all technical people feeling empowered and capable of helping in all areas… the battle of developers vs. sysadmins begins to transform into a cross-disciplinary approach to universally maximize reliability… has a positive effect on the bottom line -- better reliability and availability, happier clients, faster time to market, more time to focus the team energy on core business." -- [Stephen Nelson-Smith](http://www.jedi.be/blog/2010/02/12/what-is-this-devops-thing-anyway/)

According to Stephen, the main benefit that DevOps brings is reducing friction between engineers in an organization which creates more reliable systems that are easier to use, maintain and improve over time, as well as happier clients which all translates into real bottom line results.

Notice that there is no practical explanation on how this is achieved in practice, reading articles about DevOps we rarely know what we should do the next day at work. The description of the effects is quite verbose, leaving the reader to guess on how to get them.

## Q2: What Limitation Is Diminished by DevOps?

According to Dr. Goldratt, in some cases, a limitation might be recognized and apparent. And in other situations completely unrecognized, we just accept a given reality, the way things are and do not suspect that it should change or that it is possible to change it. To cope with existing limitations, our people invent rules and policies that allow us to continue achieving success in spite of the limitation existence.

The same blog article about DevOps clearly explains a given reality currently prevalent in many IT organizations.

> "In the software IT industry, there's a tacit assumption that projects will run late, and when they're delivered (if they're ever delivered), they will underperform, and not deliver well against investment. Once an application is in production, the business tends to gain a tremendous fear of change. A constant suspicion that the software and the platform upon which it sits is somewhat brittle and vulnerable. Bureaucratic change-management systems are put in place, making it painfully long to introduce new features or fix problems with the application." -- [Stephen Nelson-Smith](http://www.jedi.be/blog/2010/02/12/what-is-this-devops-thing-anyway/)

The quote above points to a cause of new policies for a company that is trying to deliver a much better experience, service, and products to its customers -- fear of change. Although the exact root cause for this is not explained -- it does exist if one is unafraid to remove several hidden layers of logical reasoning, we find a conflict underlying the reasoning. We can either fear change and deploy infrequently, or deliver products even faster to customers by changing more frequently -- both can't exist at the same time.

Engineers in organizations are quickly learning from experience, as are their managers. Learning from experience also creates a culture where intuition helps guide towards solutions that will have the best result. The engineers and managers are smart people and are actually achieving amazing feats in spite of the limitation existence, why? Because creating IT systems is a complicated endeavor, without sufficient data and information engineers and managers still face the need to make decisions -- they might not know the exact best solution, but they must decide, this is where intuition is born.

The intuition which makes IT achieve its goals states that IT systems are brittle, not very reliable, and trying to create cross-organizational communication and collaboration is pretty much fruitless. And yet there are dozens of extremely talented engineers who are getting by and achieving their goals, creating significant bottom-line results for businesses, governments, and non-profit organizations.

What happens when we introduce a new technology like DevOps, or Docker containers, or a public cloud? Is the limitation diminished by the fact that we started using "DevOps tools" or practices? Yes, probably. But did we get the full potential benefit from using these tools and practices while leaving our intuitions and policies unchanged?

**Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=268430&u=https%3A%2F%2Fgo.rainforestqa.com%2FGettingtoContinuousDeploymentGuide-DZone.html) with our on-demand QA solution, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=268430&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone). **
