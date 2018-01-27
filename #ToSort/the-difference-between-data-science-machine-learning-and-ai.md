# The Difference Between Data Science, Machine Learning, and AI

_Captured: 2018-01-16 at 21:03 from [dzone.com](https://dzone.com/articles/the-difference-between-data-science-machine-learni?edition=356092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-16)_

Insight for I&O leaders on deploying AIOps platforms to enhance performance monitoring today. [Read the Guide](https://dzone.com/go?i=260321&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fgartner-market-guide-for-aiops-platforms-2017.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Gartner_AIOps_Market_Guide_Dzone_Analyst_Report-AB-03-f-08232017%26cc%3Dpt%26elqcid%3D4114%26sfcid%3D7011O0000027wFd).

When I introduce myself as a data scientist, I often get questions like "What's the difference between that and machine learning?" or "Does that mean you work on artificial intelligence?" I've responded enough times that my answer easily qualifies for my "rule of three:"

![Image title](https://dzone.com/storage/temp/7825612-screen-shot-2018-01-12-at-105018-am.png)

The fields do have a great deal of overlap, and there's enough hype around each of them that the choice can feel like a matter of marketing. But **they're not interchangeable**. Most professionals in these fields have an intuitive understanding of how particular work could be classified as data science, machine learning, or artificial intelligence, even if it's difficult to put into words.

So in this post, I'm proposing an _oversimplified_ definition of the difference between the three fields:

  * **Data science** produces **insights**.
  * **Machine learning** produces **predictions**.
  * **Artificial intelligence** produces **actions**.

To be clear, this isn't a _sufficient_ qualification; not everything that fits each definition is a part of that field. (A fortune teller makes predictions, but we'd never say that they're doing machine learning!) These also aren't a good way of determining someone's role or job title ("Am I a data scientist?"), which is a matter of focus and experience. (This is true of any job description: I write as part of my job but I'm not a professional writer.)

But I think this definition is a useful way to _distinguish_ the three types of work and to avoid sounding silly when you're talking about it. It's worth noting that I'm taking a [descriptivist rather than a prescriptivist approach](http://english.blogoverflow.com/2012/10/prescriptivism-and-descriptivism/): I'm not interested in what these terms "should mean", but rather how people in the field typically use them.

## Data Science Produces Insights

Data science is distinguished from the other two fields because its goal is an especially human one: to gain insight and understanding. Jeff Leek has an [excellent definition of the types of insights that data science can achieve](http://jtleek.com/modules/01_DataScientistToolbox/03_01_typesOfQuestions/#1), including descriptive ("the average client has a 70% chance of renewing"), exploratory ("different salespeople have different rates of renewal"), and causal ("a randomized experiment shows that customers assigned to Alice are more likely to renew than those assigned to Bob").

Again, not everything that produces insights qualifies as data science (the [classic definition of data science](http://drewconway.com/zia/2013/3/26/the-data-science-venn-diagram) is that it involves a combination of statistics, software engineering, and domain expertise). But we can use this definition to distinguish it from ML and AI. The main distinction is that in data science there's always a human in the loop: someone is understanding the insight, seeing the figure, or benefitting from the conclusion. It would make no sense to say, "Our chess-playing algorithm uses data science to choose its next move," or, "Google Maps uses data science to recommend driving directions."

This definition of data science thus emphasizes:

  * Statistical inference
  * Data visualization
  * Experiment design
  * Domain knowledge
  * Communication

Data scientists might use simple tools: they could report percentages and make line graphs based on SQL queries. They could also use very complex methods: they might work with distributed data stores to analyze trillions of records, develop cutting-edge statistical techniques, and build interactive visualizations. Whatever they use, the goal is to gain a better understanding of their data.

## Machine Learning Produces Predictions

I think of machine learning as the field of **prediction**: of "Given instance X with particular features, predict Y about it". These predictions could be about the future ("predict whether this patient will go into sepsis"), but they also could be about qualities that aren't immediately obvious to a computer ("predict whether [this image has a bird in it](https://xkcd.com/1425/)"). Almost all [Kaggle competitions](https://www.kaggle.com/competitions) qualify as machine learning problems; they offer some training data, and then see if competitors can make accurate predictions about new examples.

There's plenty of overlap between data science and machine learning. For example, logistic regression can be used to draw insights about relationships ("the richer a user is, the more likely they'll buy our product, so we should change our marketing strategy") and to make predictions ("this user has a 53% chance of buying our product, so we should suggest it to them").

Models like random forests have slightly less interpretability and are more likely to fit the "machine learning" description, and methods such as deep learning are notoriously challenging to explain. This could get in the way if your goal is to extract insights rather than make predictions. We could thus imagine a "spectrum" of data science and machine learning, with more interpretable models leaning towards the data science side and more "black box" models on the machine learning side.

![](https://imgs.xkcd.com/comics/machine_learning.png)

Most practitioners will switch back and forth between the two tasks very comfortably. I use both machine learning and data science in my work: I might fit a model on Stack Overflow traffic data to determine which users are likely to be looking for a job (machine learning), but then construct summaries and visualizations that examine why the model works (data science). This is an important way to discover flaws in your model and to combat [algorithmic bias](https://en.wikipedia.org/wiki/Algorithmic_bias). This is one reason that data scientists are often responsible for developing machine learning components of a product.

## Artificial Intelligence Produces Actions

Artificial intelligence is by far the oldest and the most widely recognized of these three designations, and as a result, it's the most challenging to define. The term is surrounded by a great deal of hype, thanks to researchers, journalists, and startups who are looking for money or attention.

![Image title](https://dzone.com/storage/temp/7825667-screen-shot-2018-01-12-at-110255-am.png)

This has led to a backlash that strikes me as unfortunate since it means some work that probably _should_ be called AI isn't described as such. Some researchers have even complained about the [AI effect](https://en.wikipedia.org/wiki/AI_effect): "AI is whatever we can't do yet." So what work can we fairly describe as AI?

One common thread in definitions of "artificial intelligence" is that an autonomous agent executes or recommends **actions** (i.e. [Poole, Mackworth and Goebel 1998](http://www.cs.ubc.ca/~poole/ci.html), [Russell and Norvig 2003](http://aima.cs.berkeley.edu/)). Some systems I think should be described as AI include:

  * Robotics and control theory (motion planning, walking a bipedal robot)
  * Optimization (Google Maps choosing a route)
  * Natural language processing (bots)
  * Reinforcement learning

Again, we can see a lot of overlap with the other fields. [Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is particuarly interesting for straddling the fields of ML and AI. The typical use case is training on data and then producing predictions, but it has shown enormous success in game-playing algorithms like AlphaGo. (This is in contrast to earlier game-playing systems, like Deep Blue, which focused more on exploring and optimizing the future solution space.)

But there are also distinctions. If I analyze some sales data and discover that clients from particular industries renew more than others (extracting an insight), the output is some numbers and graphs, not a particular action. (Executives might use those conclusions to change our sales strategy, but that action isn't autonomous.) This means I'd describe my work as data science: it would be cringeworthy to say that I'm "using AI to improve our sales."

![Image title](https://dzone.com/storage/temp/7825680-screen-shot-2018-01-12-at-110446-am.png)

The difference between artificial intelligence and machine learning is a bit more subtle, and historically ML has often been considered a subfield of AI (computer vision, in particular, was a classic AI problem). But I think the ML field has largely "broken off" from AI, partly because of the backlash described above: most people who to work on problems of prediction don't like to describe themselves as AI researchers. (It helped that many important ML breakthroughs came from statistics, which had less of a presence in the rest of the AI field.) This means that if you can describe a problem as "predict X from Y," I'd recommend avoiding the term AI completely.

![Image title](https://dzone.com/storage/temp/7825691-screen-shot-2018-01-12-at-110546-am.png)

## Case Study: How Would the Three Be Used Together?

Suppose we were building a self-driving car and were working on the specific problem of stopping at stop signs. We would need skills drawn from all three of these fields.

  * **Machine learning**: The car has to recognize a stop sign using its cameras. We construct a dataset of millions of photos of streetside objects and train an algorithm to **predict** which have stop signs in them.
  * **Artificial intelligence**: Once our car can recognize stop signs, it needs to decide when to take the **action** of applying the brakes. It's dangerous to apply them too early or too late, and we need it to handle varying road conditions (for example, to recognize on a slippery road that it's not slowing down quickly enough), which is a problem of [control theory](https://en.wikipedia.org/wiki/Control_theory).
  * **Data science**: In street tests, we find that the car's performance isn't good enough, with some false negatives in which it drives right by a stop sign. After analyzing the street test data, we gain the **insight** that the rate of false negatives depends on the time of day: it's more likely to miss a stop sign before sunrise or after sunset. We realize that most of our training data included only objects in full daylight, so we construct a better dataset including nighttime images and go back to the machine learning step.

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.
