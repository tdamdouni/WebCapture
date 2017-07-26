# The Challenges Of Building AI Apps

_Captured: 2015-10-16 at 10:19 from [techcrunch.com](http://techcrunch.com/2015/10/15/machine-learning-its-the-hard-problems-that-are-valuable/?ncid=rss)_

![](https://tctechcrunch2011.files.wordpress.com/2015/10/rubiks.jpg?w=738)

Artificial intelligence (AI) has an intellectual lineage stretching back to the greats of computer theory: Turing and, ultimately, Babbage, inventor of the calculating machine. What we now see in London, where leading teams such as DeepMind are working on machine learning, is the movement from the realm of computer science to practical uses and business cases.

It's not just Google, which [bought the DeepMind team last year](http://recode.net/2014/01/26/exclusive-google-to-buy-artificial-intelligence-startup-deepmind-for-400m/), or Facebook, with a [50-person AI lab](http://www.popsci.com/facebook-ai), that see the possibilities. Roughly one-sixth of [YC companies](http://yclist.com/) seemed to be using machine learning in the most recent cohort, while IBM has bet billions on the success of [Watson, its Jeopardy question-answering supercomputer. ](http://www.ibm.com/smarterplanet/us/en/ibmwatson/)

Thousands of companies are taking advantage of infrastructure to manage or extract insight from large datasets. They are all working to predict outcomes or recommend or execute actions based on analyses of programmatically available digitized data.

I'd like to share some of the challenges facing startups that are attempting to build AI-based applications for businesses, and how some companies are attempting to overcome those challenges. Selecting, perfecting and combining the algorithms themselves is only a small part of the thoughtful work done by the best entrepreneurs. Other important factors include:

  * Proprietary access to unique data that will form the basis for the training data set.

  * A clear view of how insight will be generated, with tightly coupled software that intelligently extracts meaning from the data or evaluates which data requires human classification.

  * If possible, a data model that can accommodate new data sources as they emerge.

  * A skilled team that can write or adapt publicly available algorithms, select the right algorithm for the desired result and combine algorithms as needed to optimize the result.

A couple of years ago, data analysis of any kind was labelled as "data science." Today, the label AI is widely applied, sometimes carelessly. So let's first consider what is described as AI.

Current commercial applications are "narrow" or "weak" forms of AI. This means the machine specializes in one area, and cannot infer from first principles as humans can ("general AI"). Narrow AI is based on well-understood techniques being exploited commercially for the first time. What is considered AI can quickly become a well-understood data science technique.

A closely related approach is "deep learning," whereby data inputs are not pre-described. Rather, models learn about data (and data structures), then, using multiple layers of non-linear feedback, learn important features of the data and even self-refine.

While the technique has been around for more than 20 years, wider access to compute power is finally a match for the data intensity it requires. London-based startup [Improbable](http://improbable.io/) is an exciting example of a company using vast compute power and deep learning to simulate complex environments, ranging from open-ended game worlds to cities.

Still, many startups we meet claim to incorporate machine learning (ML) into their technologies. For most of these companies, when we scratch beneath the surface, ML is not a truly important element of the product. In some cases it is just a veneer to make a project seem cutting-edge. In others it is real, but just table stakes, so does not offer a technical barrier to competitors; rather, it enables startups to offer an increasingly accurate and efficient service for customers.

For instance, some startups will use commodity code, of which there are many significant [open-source libraries](http://sourceforge.net/directory/science-engineering/ai/os:mac/freshness:recently-updated/). An interesting open-source project for distributed stream and batch data processing, Apache [Flink](https://flink.apache.org/), has collated a library of publicly available ML algorithms that will scale to large data sets.

Amazon launched [machine learning as a service](https://aws.amazon.com/machine-learning/) in April, and startups such as [MetaMind](https://www.metamind.io/) are aiming to offer AI as a service to developers, an extension of the more crowded market of predictive analytics as a service. The reality is that most algorithms are well-known, and AI learning techniques will commoditize fast.

So companies building products using narrow AI need to be very thoughtful about how they build and improve their products or services.

## The Moat: Training Data

Training data is at the heart of building distinctive narrow-AI-based products. Startups need to find sources of structured data that can help them build the best possible models. In this case, "best" means the data set is large enough to learn from, and varied enough that it may help a range of customers rather than only one, and the resulting machine can seamlessly improve processes or decision-making.

Machine learning theory states that with unlimited data, we could expect all algorithms to produce similar-quality results. So startups will only resist commoditization if they have access to a unique data set and extend their early lead by continuously learning how to improve their algorithms based on end-user interactions. The most famous example is Google's use of clickstream data as a private source of training data to improve search-ranking results.

As we have touched on [before](https://medium.com/@Mosaic_VC/more-than-traction-3854c5da341a), startups sometimes confuse revenue traction with value creation. Choosing projects that yield short-term revenue based on easily available data sets is unlikely to yield a differentiated, valuable application.

One example is [Digital Genius](http://digitalgenius.com/), a London- and New York-based startup focused on automating customer service conversations. The founder bootstrapped for its first couple of years. Admirable though that is, the initial technology and commercial choices were not scalable. The first version of its technology was very flexible, but it needed to be highly customized. Also, initial demand was for lower-value applications in marketing services. The combination was not attractive to venture investors at that point.

However, the company may well have found its way. First, the team created a platform it can reuse for many different text-based AI applications, whereas it had started with a tool set. Second, it has found a high-value focus in [automating text conversations](http://techcrunch.com/2015/05/05/digitalgenius-brings-artificial-intelligence-to-customer-service-via-sms/). Importantly, the algorithm is based (amongst other data quarries) on analyses of huge repositories of real call-center transcripts. This may now yield a replicable product that can be the foundation of a large business.

## A Technology-Driven Process To Extract Insight And Meaning From The Data Set

Having access to useful data sets is only a start: A system needs to extract accurate metadata from the data, and use it as an input to improve the machine's accuracy.

We find that the best AI-driven startups are focused on increasing both the throughput and the refinement and accuracy of their algorithms. That takes iteration and time -- and a lot of data -- to get right.

For example, [Unbabel](https://unbabel.com/), a Lisbon- and San Francisco-based startup focused on AI-augmented translation. In order to deliver, the company must create scalable methods for translators to annotate, refine and reject machine translations. [The workflow software](http://techcrunch.com/2015/09/11/translation-startup-unbabel-unveils-new-smartcheck-technology/) that Unbabel's translators use to assess translation accuracy is strikingly granular. Rather than a simple yes/no/maybe, 15-20 measures of accuracy are judged by the translator, which also suggests an alternative. Accuracy in this case can also include brand suitability for Unbabel's commercial customers. The machine then uses this feedback to self-improve.

That is an intelligent and well-managed approach to model improvement. It solves for quality and scale, rather than just efficiency, and acknowledges that the machine is a work in progress and not yet ready for full automation of translation tasks.

That iterative combination of training data and machine accuracy is the heart of what many startups are working through.

## How Do You Make It All Work?

A lot of commentary on AI-based applications makes building them sound straightforward. Yet AI itself is rarely sufficient. As with many disruptive software opportunities, startups using AI need to be competent in multiple spheres and make the product or service easy to use.

Even once the right algorithms are chosen, a good data set identified and a process to improve and scale ML is hardened, startups are often just at the starting line. Some challenges (and often ones that are worthy of venture capital funding) require innovation on multiple fronts. Even for narrowly focused startups, engineering challenges are rarely one-dimensional.

IT operations-focused startup [Moogsoft](http://www.moogsoft.com/) is a good example (full disclosure: I am an angel investor). [Phil Tee](http://www.moogsoft.com/meet-the-herd), the founder and CEO of Moog, is a fifth-time founder, and as the founding CTO of Micromuse was responsible for the dominant incumbent in network management. His goal was to work out how to process millions of different event data points so that IT operations could be evaluated across the full stack.

He saw that he would need to build a machine that was model-free so that it could make sense of new data sources on the fly, as operations evolved. This required the technical chops to build relevant algorithms that together could cope with untagged data. Phil then went further and broke additional ground by predicting faults -- all whilst tuning the machine for processing at scale and in real time.

The team also needed to have the understanding of enterprise use cases so that the software was effective in reducing time to resolve and troubleshoot tickets, and in delivering transparency to the affected organizations. This combination is not trivial.

Of the many potential applications of AI that get us excited -- for example, automated code generation, QA or optimization platform, automated risk and lending decisions in the financial supply chain, automated [legal documentation](https://ironclad.ai/) and [contract analytics](http://www.seal-software.com/platform/seal-contract-discovery-and-analytics), or automated [visual](http://tractable.io/) assessments such as health checks or insurance claims adjustments -- many fall into this category of startup management and engineering challenges that are not going to be straightforward to solve.

## What's The Right Team?

Assembling the right team is a challenge. Supply of graduates from the world's best computational linguistics, machine learning and data science programs cannot meet demand. Google and Facebook are building teams and [acquiring startups](http://www.inference.vc/the-story-of-dark-blue-labs-and-google/) with critical mass, offering recruits the chance to work on both general and narrow AI problems with enormous resources at their disposal. Their pay scales make it difficult for smaller startups to recruit. Startup CEOs who are aiming to recruit the best in their specific fields have to recruit globally.

Most importantly, startups must offer recruits an exciting problem to solve in order to attract a world-class team. At least, as we've shown, the valuable problems also tend to be the harder ones. Mere efficiency gains are not attractive enough as a mission to attract the best. And once the ML team is assembled, as the Moog example shows, wider skills are needed to turn a working machine into a commercially viable product.  
AI, predictive analytics and data science-driven startups are only going to grow in size and in importance. Navigating how to build them is not straightforward.

If you are working on a very ambitious project in this field and have identified unique or proprietary training data, and have a product and a business model that can capitalize on the insights from the data and a well-rounded team to go to market, please get in touch, we would love to learn more.

Featured Image: [ChristianChan](http://www.shutterstock.com/gallery-2665057p1.html)/[Shutterstock](http://www.shutterstock.com)
