# Apple just created the largest installed base of AR-capable devices

_Captured: 2017-06-15 at 01:09 from [qz.com](https://qz.com/1003672/what-apples-silicon-business-might-have-to-do-with-its-machine-learning-desires/)_

_At last week's Worldwide Developers Conference (WWDC), Apple made an unusually large number of hardware and software announcements. Today we'll look at a potential connection between Apple's silicon design strengths and its just-unveiled augmented reality and machine learning applications development tools._

When Apple introduced its 64-bit [A7 processor](https://en.wikipedia.org/wiki/Apple_A7) in Sept. 2013, they caught the industry by surprise. According to an ex-Intel gent who's now at a long-established Sand Hill Road venture firm, the competitive analysis group at the imperial [x86 maker](https://en.wikipedia.org/wiki/X86) had no idea Apple was cooking a 64-bit chip.

As I recounted in a Sept. 2013 Monday Note titled "[64 bits. It's Nothing. You Don't Need It. And We'll Have It In 6 Months](https://mondaynote.com/64-bits-it-s-nothing-you-don-t-need-it-and-we-ll-have-it-in-6-months-1d394641e97a)," competitors and Intel stenographers initially dismissed the new chip. They were in for a shock: Not only did the company jump to the head of the race for powerful mobile chips, but Apple also used its combined control of hardware and software to build what Warren Buffett refers to as a wide "[wide moat](https://signalvnoise.com/posts/333-warren-buffett-on-castles-and-moats)":

> In days of old, a castle was protected by the moat that circled it. The wider the moat, the more easily a castle could be defended, as a wide moat made it very difficult for enemies to approach.

The industry came to accept the idea Apple has one of the best, if not _the_ best, silicon design team; the company [just hired Esin Terzioglu](http://fortune.com/2017/05/30/apple-qualcomm-esin-terzioglu/), who oversaw the engineering organization of Qualcomm's core communications chips business. By moving its smartphones and tablets--hardware and software together--into the 64-bit world, Apple built a moat that's as dominant as Google's superior Search, as unassailable as the aging [Wintel](https://en.wikipedia.org/wiki/Wintel) dominion once was.

I think we might see another moat being built, this time in the fields of [augmented reality](https://en.wikipedia.org/wiki/Augmented_reality) (AR), [machine vision](https://en.wikipedia.org/wiki/Machine_vision) (MV), and, more generally, [machine learning](https://en.wikipedia.org/wiki/Machine_learning) (ML).

At last week's [WWDC](https://developer.apple.com/wwdc/), Apple introduced ARKit ([video here](https://developer.apple.com/videos/play/wwdc2017/602/)), a programming framework that lets developers build augmented reality into their applications. The demos (a minute into the video) are enticing: A child's bedroom is turned into a "virtual storybook"; an Ikea app lets users place virtual furniture in their physical living room.

As many observers have pointed out, Apple just created the largest installed base of AR-capable devices. There may be more Android devices than iPhones and iPads, but the Android software isn't coupled to hardware. The wall protecting the massive Android castle is fractured. Naturally, Apple was only too happy to compare the 7% of Android smartphones running the latest OS release to the 86% of iPhones running iOS 10.

Apple also introduced [CoreML](https://developer.apple.com/documentation/coreml), an application framework that integrates "[trained models](https://developer.apple.com/documentation/coreml/converting_trained_models_to_core_ml)" into third-party apps. Unlike with ARKit, there were no fun CoreML demos; CoreML implementations will be both "everywhere" and less explicit than AR. Architecturally, CoreML is a foundation for sophisticated machine vision and natural language processing apps:

![](https://qzprod.files.wordpress.com/2017/06/components-of-app-development.jpeg?quality=80&strip=all&w=50)![components-of-app-development](https://qzprod.files.wordpress.com/2017/06/components-of-app-development.jpeg?quality=80&strip=all&w=353)

> _Courtesy: Apple Developer Documentation. (Provided by author)_

As far as we know, all of this runs on the Ax processors in recent iPhones and iPads. But a recent, unsubstantiated Bloomberg rumor has aroused interest: "[Apple Is Working on a Dedicated Chip to Power AI on Devices](https://www.bloomberg.com/news/articles/2017-05-26/apple-said-to-plan-dedicated-chip-to-power-ai-on-devices)."

Auxiliary chips that run to the side of the main processor, dedicated to a specific set of operations, have (almost) always existed. The practice started with [FPUs](https://en.wikipedia.org/wiki/Floating-point_unit) (Floating Point Processors). High-precision [Floating Point](https://en.wikipedia.org/wiki/Floating-point_arithmetic) operations, mostly for scientific and technical applications, demanded too much from the main [CPU](https://en.wikipedia.org/wiki/Central_processing_unit) (central processing unit), slowing everything down. Such operations were offloaded to specialized, auxiliary FPUs.

Later, we saw the [rise of GPUs](https://en.wikipedia.org/wiki/Graphics_processing_unit), graphic processing units, dedicated to demanding graphics operations, simulations, and games. Because of the prevalence of graphics-intensive apps and the demand for reactive, no-lag interactions, GPUs are now everywhere, in PCs, tablets, and smartphones. Companies such as [Nvidia](https://en.wikipedia.org/wiki/Nvidia) made their name and fortune building a range of high-performance GPUs.

These are impressive machines. Stripped of the logic (transistors) needed for the complex logic operations of general purpose CPUs, GPU hardware resources are dedicated to a narrow set of tasks performed at the highest possible speed. Think of a track car with none of the amenities of a road vehicle, running much faster but unsuited for everyday road and city use.

Such was the performance of GPUs that some financial institutions experimented with machines that harnessed hundreds of GPUs in order to execute complex predictive models in near real-time, giving them a putative trading advantage.

A similar thought arose with the need to run complicated [convolutional neural networks](https://en.wikipedia.org/wiki/Convolutional_neural_network) and related ML/AI computations. This led Google to design its [TPU](https://en.wikipedia.org/wiki/Tensor_processing_unit) (tensor processing unit) to better run its [TensorFlow algorithms](https://en.wikipedia.org/wiki/TensorFlow).

Back to the dedicated AI chip rumor: It's an attractive story that comes from a source (Bloomberg) that has a record of eerily accurate predictions mixed with a few click-baiting bloopers.

Let's indulge in a bit of speculation.

Tentatively dubbed Apple Neural Engine (ANE), this hypothetical chip fits well with Apple's tradition of designing hardware for its software, following [Alan Kay's](https://en.wikiquote.org/wiki/Alan_Kay) edict: "People who are really serious about software should make their own hardware."

Couple Apple's AR and ML announcements with the putative ANE chip and we have an integrated whole that sounds very much like the Apple culture and silicon muscle we've already witnessed, a package that would further strengthen the company's moat, its structural competitive advantage.

It's an attractive train of thought, although possibly a dangerous one, in the vein of "It'll work because it'd be great if it did." That perfunctory precaution taken, I'd give it more than an even chance of becoming reality in some form. Or your Monday Note subscription money back.

_This post originally appeared at [Monday Note](https://mondaynote.com/apple-silicon-and-machine-learning-1ea34ccab246). Learn how to [write for Quartz Ideas](https://qz.com/635686/the-complete-guide-to-writing-for-quartz-ideas/). We welcome your comments at [ideas@qz.com](mailto:ideas@qz.com)._
