# Machine Learning: The Known Unknown

_Captured: 2017-12-10 at 20:37 from [dzone.com](https://dzone.com/articles/machine-learning-the-known-unknown?edition=343111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-10)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

Machine learning has risen from its humble beginnings decades ago as a simple three-layer [perceptron](https://web.csulb.edu/~cwallis/artificialn/History.htm) to today's immensely complicated and extremely deep convolutional neural nets. But there's a secret that computer scientists don't talk about much. Since the earliest days, there was a known problem, and it was also known that problem got worse as a direct result of the neural nets getting better. Early researchers, as well as early adopters, were all fully aware of this problem, but in light of how magical this simulated brain tissue was becoming, it was easy to play down the problem because the neural nets kept improving. But it turns out that being magical is its own kind of problem.

## ML Beginnings

Research and AI began with relatively conventional programmatic systems that used semantic and mathematical models to represent the logic necessary to operate intelligently on the input in order to generate "intelligent" output. There were systems centered around [frames](https://en.wikipedia.org/wiki/Frame_\(artificial_intelligence\)), examples ([case-based](http://artint.info/html/ArtInt_190.html)), and [rules](https://cs.stackexchange.com/questions/4972/whats-the-difference-between-a-rule-based-system-and-an-artificial-neural-netwo) long before there were any practical neural net-based systems. They were constructed on familiar (or at least comprehensible) paradigms that allowed their developers to trace back through the system's operation and in some way explain what went right (or wrong). It was possible to understand and explain how the result was generated.

## Enter Neural Nets

Neural nets are intriguing because they seem to work much like a brain works. You don't program but rather you "teach" them. And this is where the problem begins. We train (teach) the neural net with as much data as we can get. Of course, we reserve a small part of the data that was not used in the training to be used as a test set. After the system is trained, we test the resulting neural net against the reserved data and can come up with a solid measurement of the accuracy of the system. We get an understandable accuracy measure of how well the system performed.

But what we _don't_ get and _don't_ know and _can't_ explain is exactly how the system came up with its result in each instance. We could trace all the weights and all of the computations that lead to the final, confidence value, but there is no underlying model. We don't know why it did any of those things, we just know that the training gave us those weights.

Imagine looking at a slice of brain tissue and trying to figure out why and how it made a leg move.

Some might say, "Who cares? It gets the right answer (or at least one that's good enough)." And for some small and simple applications, that might be okay if the system is trained once and the system is "frozen" and tested against a large enough test set to know that it works with acceptable reliability. The behavior is basic enough that the results are rarely confounding; they make sense from an anthropomorphic point of view.

However, real-world neural net systems (just as with any conventional program) will naturally expand into more functionality. In the context of a neural net, that means adding more examples to the training set as well as more layers and more nodes to handle the larger array of possible results. This implies a completely new model that will inevitably have slightly different results for all of the regression test examples that were used previously. And even subtler variations may be introduced by the order in which the examples are trained as well as the relative frequency distribution of the various traits being learned.

Much like biological brains, modern neural nets attempt to generalize the patterns they are exposed to and pay less attention to extraneous details. If the early examples in the training set tend to cluster around one type of example, it may become biased in a way that will impede or skew learning about other examples if they occur later in the training set. You can think of it sort of like a child learning from examples from their family and neighbors. Later, they move away and are exposed to very different examples, but they train these new examples with the perspective of their previously learned behavior. Childhood memories are inherently strong. Freud thought he could explain a lot of what we do based on our earliest lessons in life.

Okay, okay, you're probably asking my just rambling is there a point to this. Yes. Ultimately, our computer systems must be used (purchased) in the real world.

## My Point: The Marketplace

The researcher/programmer perspective might still be, "Who cares?" But the marketplace is a far more powerful force. We're beginning to see some very large markets opening up for AI (autonomous driving, medical diagnosis, etc.) but they also require extreme confidence and verification in order to survive the extremely litigious environments these products exist in. These new important AI marketplaces revel in the magic of the seeming intelligence of self-driving cars but are terrified that the car can never tell us why it decided to drive over your dear aunt Gertrude. I know I would be upset if my AI radiologist said my chest x-ray was fine but a couple years later I find out I had lung cancer all the time. When I ask my AI radiologist, "Why didn't you detect it?" It responds with "I don't know."

These are not imaginary concerns. The European Union passed a [law](https://www.cio.com/article/3234305/privacy/eu-privacy-law-says-companies-need-to-explain-the-algorithms-they-use.html) requiring that any decision made by a machine be readily explainable, on penalty of fines that could cost companies like Google and Facebook billions of dollars. This law becomes effective in 2018 and is expected to be enforced. Legal experts claim that the language of this law is reasonably broad and forward-looking. It promises to hold algorithms accountable to "explain themselves." It's only a matter of time before such laws become worldwide.

In a future article, I'll take a look at some of the efforts underway to produce "explainable" results derived from neural nets.

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.

Opinions expressed by DZone contributors are their own.
