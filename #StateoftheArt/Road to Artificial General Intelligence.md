# Road to Artificial General Intelligence

_Captured: 2016-03-25 at 00:28 from [medium.com](https://medium.com/ai-revolution/the-road-to-artificial-general-intelligence-45578b8585b9#.op72xnhef)_

![](https://cdn-images-1.medium.com/max/2000/1*A0TyIXDtzVE8qxJfVNSmJQ.jpeg)

#### Building a Computer as Smart as Humans

_Note: This is the 3rd part of a short essay series aiming to condense knowledge on the __[Artificial Intelligence Revolution_](http://medium.com/ai-revolution)_. Feel free to start reading here __[or go to Part 1_](https://medium.com/ai-revolution/ai-revolution-dfd51f9f3a74#.3bucyffu7)_. The project is based on the two part essay __[AI Revolution_](http://waitbutwhy.com/2015/01/artificial-intelligence-revolution-1.html)_ by Tim Urban & Wait But Why. I recreated all images, shortened it x3 and added a couple of new perspectives. Read more on why/how I wrote it __[here_](https://medium.com/ai-revolution/writing-ai-revolution-231633145281#.14j00ygg1)_._

#### Building Hardware

If an AI system is going to be as intelligent as the human brain, one crucial thing has to happen--AI "needs to equal the brain's raw computing capacity. One way to express this capacity is in the total calculations per second the brain could manage."³²

![](https://cdn-images-1.medium.com/max/800/1*1W55EkgNt9OZEIdqzVRTqA.gif)

The challenge is that currently only a few of the brain's regions are precisely measured. However, Ray Kurzweil, a computer scientist and AI expert, has developed a method for estimating the total cps of the human brain. He arrived at this estimate by taking the cps from one brain region and multiplying it proportionally to the weight of that region compared to the weight of the whole brain. "He did this a bunch of times with various professional estimates of different regions, and the total always arrived in the same ballpark -- around 10¹⁶, or 10 quadrillion cps."³³

"Currently, the world's fastest supercomputer, China's [Tianhe-2](http://www.reuters.com/article/2014/11/17/us-china-supercomputer-idUSKCN0J11VV20141117), has actually beaten that number, clocking in at about 34 quadrillion cps."³[⁴](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) But Tianhe-2 is also monstrous "taking up 720 square meters of space, using 24 megawatts of power (the brain runs on just [20 watts](http://www.popsci.com/technology/article/2009-11/neuron-computer-chips-could-overcome-power-limitations-digital)), and costing $390 million to build. Not especially applicable to wide usage, or even most commercial or industrial usage yet."³[⁵](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

"Kurzweil suggests that we think about the state of computers by looking at how many cps you can buy for $1,000. When that number reaches human-level -- 10 quadrillion cps -- then that'll mean AGI [computer that passes human level intelligence] could become a very real part of life."³[⁶](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

Currently we're only at about 10¹⁰ (10 trillion) cps per $1,000. However, historically reliable [Moore's Law](http://www.mooreslaw.org/) states "that the world's maximum computing power doubles approximately every two years, meaning computer hardware advancement, like general human advancement through history, grows exponentially³[⁷](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) … right on pace with this graph's predicted trajectory:"³[⁸](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

![](https://cdn-images-1.medium.com/max/800/1*bxekOxCkfR4gxn_uMacyBw.gif)

> _Vizualisation based on Ray Kurzweil's graph and analysis from his book The Singularity is Near_

This dynamic "puts us right on pace to get to an affordable computer by 2025 that rivals the power of the brain … But raw computational power alone doesn't make a computer generally intelligent -- the next question is, how do we bring human-level intelligence to all that power?"³[⁹](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

#### _Building Software_

The hardest part to creating AGI is the method for developing software. "The truth is, no one really knows how to make it smart -- we're still debating how to make a computer human-level intelligent and capable of knowing what a dog and a weird-written B and a mediocre movie is."[⁴⁰](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) But there are a couple of strategies. These are the three most common:

  1. Copy how the brain works.

The most straight-forward idea is to plagiarize the brain, to build the computer's architecture with close resemblance to how a brain is structured. One example "is the artificial neural network. It starts out as a network of transistor 'neurons,' connected to each other with inputs and outputs, and it knows nothing -- like an infant brain. The way it 'learns' is it tries to do a task, say handwriting recognition, and at first, its neural firings and subsequent guesses at deciphering each letter will be completely random. But when it's told it got something right, the transistor connections in the firing pathways that happened to create that answer are strengthened; when it's told it was wrong, those pathways' connections are weakened. After a lot of this trial and feedback, the network has, by itself, formed smart neural pathways and the machine has become optimized for the task."[⁴¹](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

The second, more radical approach to plagiarism is Whole Brain Emulation. Scientists take a real brain, cut it into hundreds of tiny slices to detect the multitude of neural connections and replicate them in a computer as a software system. If that method will ever be successful we will have "a computer officially capable of everything the brain is capable of -- it would just need to learn and gather information … How far are we from achieving whole brain emulation? Well so far, we've [just recently](http://www.smithsonianmag.com/smart-news/weve-put-worms-mind-lego-robot-body-180953399/?no-ist) been able to emulate a 1mm-long flatworm brain, which consists of just 302 total neurons."[⁴²](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) To put this into the perspective, the human brain consists of [86 billion neurons](http://www.ncbi.nlm.nih.gov/pubmed/19226510) linked by trillions of synapses.

2\. Introduce evolution to computers.

"The fact is, even if we can emulate a brain, that might be like trying to build an airplane by copying a bird's wing-flapping motions -- often, machines are best designed using a fresh, machine-oriented approach, not by mimicking biology exactly."[⁴³](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) If the brain is just too complex for us to digitally replicate, we could try to emulate evolution instead. This method is called Genetic Algorithm. "A group of computers would try to do tasks, and the most successful ones would be _bred _with each other by having half of each of their programming merged together into a new computer. The less successful ones would be eliminated."[⁴⁴](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) Speed and a goal-oriented approach are the advantages that artificial evolution has over the biological one. "Over many, many iterations, this natural selection process would produce better and better computers. The challenge would be creating an automated evaluation and breeding cycle so this evolution process could run on its own."[⁴⁵](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

3\. "Make this whole thing the computer's problem, not ours."[⁴⁶](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p)

The last concept is the simplest, but probably the scariest of them all. "We'd build a computer whose two major skills would be doing research on AI and coding changes into itself -- allowing it to not only learn but to improve its own architecture. We'd teach computers to be computer scientists so they could bootstrap their own development."[⁴⁷](https://medium.com/@pawsys/footnotes-d325588415a8#.o1b83497p) This is regarded as the most promising path we have.

All these software advances may seem slow or a little bit intangible, but as it is with the sciences, one minor innovation can suddenly accelerate the pace of developments. Kind of like the aftermath of the Copernican revolution -- the finding that suddenly made all the complicated math equations of the planet trajectories much easier to calculate, which enabled a multitude of other innovations. Moreover, the "exponential growth is intense and what seems like a snail's pace of advancement can quickly race upwards."⁴⁸
