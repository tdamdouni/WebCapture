# Analyzing Apple's Statement on TSMC and Samsung A9 SoCs

_Captured: 2015-10-10 at 15:08 from [www.anandtech.com](http://www.anandtech.com/show/9708/analyzing-apple-statement-for-tsmc-and-samsung-a9)_

![](http://images.anandtech.com/doci/9708/ChipworksA9_678x452.jpg)

Since we [first learned that the A9 SoC in Apple's iPhone 6s lineup is dual sourced](http://www.anandtech.com/show/9665/apples-a9-soc-is-dual-sourced-from-samsung-tsmc) \- that is that it's being made by two different vendors with two distinct manufacturing processes - one major question has remained in the process of reviewing these two phones. The main issue under question here is whether the TSMC A9 or Samsung A9 have any difference in performance and power consumption. If there is a difference, the question then becomes whether the difference is significant.

In an atypical move for the normally tight lipped manufacturer, Apple issued a statement this afternoon in response to these questions and some [rudamentary end-user benchmarking showing that there may be a difference](http://www.macrumors.com/2015/10/07/tsmc-samsung-a9-battery-tests/):

> With the Apple-designed A9 chip in your iPhone 6s or iPhone 6s Plus, you are getting the most advanced smartphone chip in the world. Every chip we ship meets Apple's highest standards for providing incredible performance and deliver great battery life, regardless of iPhone 6s capacity, color, or model.
> 
> Certain manufactured lab tests which run the processors with a continuous heavy workload until the battery depletes are not representative of real-world usage, since they spend an unrealistic amount of time at the highest CPU performance state. It's a misleading way to measure real-world battery life. Our testing and customer data show the actual battery life of the iPhone 6s and iPhone 6s Plus, even taking into account variable component differences, vary within just 2-3% of each other.

It interesting to see this response as Apple normally doesn't comment on anything like this, which in turn is likely a good indicator of how seriously Apple is taking any concerns. However, this statement is also of interest because it's revealing in terms of what internal data Apple has collected on the issue. Apple has in recent years been one of the better companies in accurately promoting the battery life of their products, and that kind of accuracy comes not only from taking a conservative (safe) stance in marketing, but also collecting massive amounts of data to understand their products and their capabilities.

### The Test

To get to the meat of matters then, let's talk about battery life, tests, chips, and statistics. In terms of the testing that has seemingly spurred on this Apple response, it's likely that the "manufactured lab tests" in the statement refer directly to Primate Labs' GeekBench battery life benchmark. The GeekBench test runs parts of the GeekBench CPU benchmark in a loop, making sure to do a fixed amount of work per time interval while idling the rest of the time, and using the score result as a modifier for the runtime score. This makes the GeekBench battery life benchmark primarily a SoC/CPU/Memory benchmark, and that in turn has repercussions for interpreting the data.

![](http://images.anandtech.com/doci/9708/GB3Battery2_575px.png)

In the case of our own web browsing battery life test, for example, this is a test that attempts to simulate light reading of web pages, meaning that the SoC is only working hard a fraction of the time. The vast majority of the time the SoC is idling, making the display the biggest power consumer; and this is especially the case on these latest generations of high performance flagship smartphones. A heavy test on the other hand would be a test that keeps a sustained and significant load on the CPU and GPU, which shifts the power consumption of a test from the display and the SoC.

![Battery Life: Light vs. Heavy](http://images.anandtech.com/graphs/graph9708/77891.png)

> _An Example of the Wide Gulf Between Light and Heavy Battery Life Testing_

Due to the nature of its use of fixed size workloads, the GeekBench battery life benchmark lies somewhere in between a heavy load and a light load (Primate Labs states it's around 30% on the 6s). And this is notable because if this is the case, it means that GeekBench is in fact highlighting the difference in power consumption between the TSMC and Samsung A9s. However as Apple points out in their statement, a sustained workload is not necessarily representative of what real world usage is like, with the real world having a burst of of different types of workloads. This doesn't mean GeekBench doesn't return valuable data, however it means we're looking at a slice of a bigger picture. Ultimately if there is a difference between the TSMC and Samsung A9s, then it means that GeekBench is likely to be exacerbating the difference versus what a real world mixed use case test would see.

As for the data itself, due to the fact that GeekBench is a heavier workload, it means that there are a number of factors that could explain why battery life in this test shows such a large difference, and not all of these factors are easy to account for. With the chips themselves, it could be that the Samsung A9 variant is simply reaching higher average temperatures due to its smaller die size (same heat over a smaller area), which then accordingly affects power draw due to the nature of semiconductor physics (increased leakage). It doesn't have to be at the point where the workload is causing thermal throttling, but even a sustained load for significant periods of time could be enough to cause this effect, as the CPU will reach higher temperatures even if the phone is cool to the touch.

![](http://images.anandtech.com/doci/7457/TempvsPowerforCi7.png)

> _An example of the temperature versus power consumption principle on an Intel Core i7-2600K. Image Credit: AT Forums User "Idontcare"_

Given the nature of chip manufacturing, it's also hard to say one way or another whether an individual chip and phone pair will have better or worse battery life than another chip and phone pair. This is a pretty complicated subject, but it basically boils down to the difficulty of injecting exactly a certain number of ions into a small part of the silicon wafer or depositing a layer of insulator that meets an exact thickness. This results in chip manufacturing quality being distribution based - a wafer will come out of production with individual chips of varying quality, with some chips operating at lower voltages or lower leakages than others, and other chips being altogether defective. This is colloquially known as the "silicon lottery."

It's then from these chips that a customer (e.g. Apple) needs to made tradeoffs between how "poor" of a chip they are willing to accept and how many chips per wafer they'd like to be able to use from each wafer (the yield). In doing so, a customer will set minimum tolerances, certain parameters that a chip needs to meet to be qualified. However as these are minimums, it means that a customer will also receive chips that exceed these minimums, as we can see in our completely fictitious chart below.

![](http://images.anandtech.com/doci/9708/CPUDistribution3_575px.png)

> _A completely fictitious processor quality distribution example. Chips in the white area are used, outlying chips in red areas are rejected_

In the case of someone like Intel, they will bin these passing chips as different products (Core i3/i5/i7) and different clockspeeds to charge the most for the best chips. However since Apple currently only uses at most two bins of chips (those suitable for 6s and those suitable for 6s Plus), this means there is a wider variation in the chips used in each phone. As a result, even if there isn't a true and consistent difference between TSMC and Samsung for A9 SoCs, you could easily have a pair of phones where due to the silicon lottery there is a notable - though not extreme - difference in power consumption.

This variation is an expected part of chip manufacturing, and while Apple could disqualify more chips and thereby reduce the yield, they will always have a certain degree of variation. The key here is to set rigorous minimums, advertise a phone based on those minimums (e.g. battery life), and should a customer end up with a phone, then they have won the silicon lottery in this case.

### The Statistics

So how does one compare phones when there's a natural variance in chip quality? Ideally it would be done just like Apple does, testing a large number of phones (chips) for power consumption and battery life to determine the distribution. Otherwise if we only test one TSMC A9 and one Samsung A9, we don't know where in the distribution each A9 lies, and consequently whether each phone is a representative "average" sample or not.

Of course this is easier said than done, as the greater the accuracy desired the greater the number of iPhones required, a bill that at $650/$750 a unit adds up quickly. This makes it incredibly impractical for any one group short of a large corporate competitive analysis team to get enough samples, especially since at the press level Apple only distributes one phone of each type (for a total of 2) to each press organization. In lieu of that, typically the best one can do is look at a small number of samples, which offers some data to account for variance, but not much.

![](http://images.anandtech.com/doci/9708/GB3Scores_575px.png)

This brings us back to where we started with GeekBench. As part of the GeekBench benchmark, results are uploaded to Primate Labs' servers, [where they are available for browsing](http://browser.primatelabs.com/battery3/search?utf8=%E2%9C%93&q=iPhone8). I've had a couple of people ask whether these results are a collective whole - in essence crowdsourced benchmarking - can answer anything, and the answer to that is a "yes, but" kind of scenario.

The big problem right now is that GeekBench doesn't know what model processor is being tested, so there's no way to sort out TSMC versus Samsung. Even if there was, we'd get to matters of testing rigor. How bright is the screen on each phone? Are there any background tasks running? Is it in airplane mode or spending power talking on WiFi/cellular? With Geekbench running at on average just a 30% duty cycle, these are all potential power consumers that can significantly impact the resulting battery life. In turn, these are all things that are accounted for in formal testing, but they cannot reliably be accounted for in benchmarks run by the wider public. This as a result adds even more variance to the equation, which makes individual or even small groups of results potentially very inaccurate.

### The Conclusion

Wrapping things up then, where do we stand? The short answer is that all we know is that we don't know. What we know is that there isn't enough information currently out there to accurately determine whether the TSMC or Samsung A9 SoC has better power consumption, and more importantly just how large any difference might be. 1-on-1 comparisons under **controlled** conditions can provide us with _some_ insight in to how the TSMC and Samsung A9s compare, but due to the natural variation in chip quality, it's possible to end up testing two atypical phones and never know it.

![](http://images.anandtech.com/doci/9708/DSC_3787_575px.jpg)

To that end I suspect that Apple's statement is not all that far off. They are of course one of the few parties able to actually analyze a large number of phones, and perhaps more to the point, having a wide variation in battery life on phones - even if every phone meets the minimum specifications - is not a great thing for Apple. It can cause buyers to start hunting down phones with "golden" A9s, and make other buyers feel like they've been swindled by not receiving an A9 with as low the power consumption as someone else. To be clear there will always be some variance and this is normal and expected, but if Apple has done their homework they should have it well understood and reasonably narrow. The big risk to Apple is that dual sourcing A9s in this fashion makes that task all the harder, which is one of the reasons why SoCs are rarely dual sourced.

As for AnandTech, we'll continue digging into the matter. Unfortunately all of the iPhones we've received and purchased so far have used TSMC A9s - it's a silicon lottery, after all - but whether there is a real and consistent difference between the TSMC and Samsung A9s is a very interesting question and one we're still looking to ultimately be able to address.

[Tweet](https://twitter.com/share)
