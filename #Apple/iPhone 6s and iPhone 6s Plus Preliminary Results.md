# iPhone 6s and iPhone 6s Plus Preliminary Results

_Captured: 2015-09-30 at 21:24 from [www.anandtech.com](http://www.anandtech.com/show/9662/iphone-6s-and-iphone-6s-plus-preliminary-results)_

![](http://images.anandtech.com/doci/9662/DSC_3796_678x452.jpg)

At this point the iPhone release cycle is pretty well understood. One year, Apple releases the design refresh that changes the external design significantly while generally focusing on evolving the internal components. The year after, the S variant is released with the same design as the previous year, but with sweeping changes to the internals. This cycle of upgrades allows Apple to focus on updating one half of the iPhone at a time while essentially giving their teams a more comfortable two years to develop their next generation technologies.

The iPhone 6s fits into this model quite well, with the introduction of new features like 3D Touch and a 12MP camera that supports 4K video recording. However, it's often difficult to understand exactly how much has changed with an S model as Apple tends to focus on high level features, this despite the fact that so many of the changes in an S model are at a low level. While I haven't had a lot of time with the iPhone 6s yet, I wanted to share some of the first results that I've acquired over the course of testing the iPhone 6s and 6s Plus in the past few days.

![](http://images.anandtech.com/doci/9662/DSC_3793_575px.jpg)

The first, and probably biggest change that I haven't seen addressed anywhere else yet is the storage solution of the iPhone 6s. Previous writers on the site have often spoken of Apple's custom NAND controllers for storage in the iPhone, but I didn't really understand what this really meant. In the case of the iPhone 6s, it seems that this means Apple has effectively taken their Macbook SSD controller and adapted it for use in a smartphone. Doing some digging through system files reveals that the storage solution identifies itself as APPLE SSD AP0128K, while [the Macbook we reviewed had an SSD that identified itself as AP0256H](http://www.anandtech.com/show/9136/the-2015-macbook-review/8).

![](http://images.anandtech.com/doci/9662/DSC_3802_575px.jpg)

While the name alone isn't all that interesting, what is interesting is how this SSD enumerated. One notable difference is that this storage solution uses PCI-E rather than SDIO, so it's unlikely that this is eMMC. Given the power requirements, it's likely that this isn't the same PCI-E as what you'd see in a laptop or desktop, but PCI-E over a [MIPI M-PHY](http://mipi.org/specifications/physical-layer) physical layer. By comparison, UFS's physical layer is MIPI M-PHY as well, while the protocol is SCSI.

The iPhone 6s in turn appears to use [NVMe](http://www.anandtech.com/show/7843/testing-sata-express-with-asus/4), which rules out both UFS and traditional eMMC. To my knowledge, there's no publicly available mobile storage solution that uses PCI-E and NVMe, so this controller seems to have more in common with the Macbook SSD controller than anything in the mobile space. It doesn't seem this is an uncommon idea though, [as SanDisk detailed the potential advantages of PCIE and NVMe in mobile storage at the Flash Memory Summit a month ago](http://www.flashmemorysummit.com/English/Collaterals/Proceedings/2015/20150811_S101C_Baram.pdf).

NVMe
eMMC

Latency
2.8 µs
N/A

Maximum Queue Depth
Up to 64K queues with  
64K commands each
Up to 1 queue with  
32 commands each

Duplex (Typical)
Full
Half

The controller is a critical part of any storage component, but without any NAND to control it's a bit pointless. Fortunately, the NAND used appears to be exposed in the OS as it's referred to as 1Y128G-TLC-2P. Breaking this down, the 1Y means that we're looking at 1Ynm NAND process with TLC. The TLC portion might concern some, but as we'll soon see it turns out that we're looking at a hybrid SLC/TLC NAND solution similar to [SanDisk's iNAND 7232 eMMC](http://www.anandtech.com/show/9432/sandisk-announces-inand-7232-emmc-51-128gb-and-slctlc) and desktop SSDs like Samsung's 850 EVO which is better suited to the bursty workloads seen in mobile and PC segments. Between the 128GB and 64GB units we currently have, the 64GB unit uses Hynix NAND, but it remains to be seen who is supplying the NAND for the 128GB variants and what other suppliers exist for the 64GB SKUs.

![](http://images.anandtech.com/doci/9019/7132_Arch.PNG)

> _An example of how an SLC/TLC NAND storage device looks in mobile devices_

For those that are unfamiliar how these hybrid SLC/TLC NAND solutions work, in essence the SLC cache is made sufficiently large to avoid showing the reduced performance of TLC NAND. Any time you're writing to the storage, the writes go to the SLC cache first before being committed to TLC NAND. As long as the overall average bandwidth demand doesn't exceed the speed of the TLC, short-run bandwidth is solely limited by the speed of the SLC cache, which turns out to be the case for almost every normal use case.

In order to see how all of this translates into performance, we once again use StorageBench, which is an app that allows us to do 256K sequential and 4K random storage performance testing developed by Eric Patno and is comparable to AndroBench 3.6.

![Internal NAND - Sequential Read](http://images.anandtech.com/graphs/graph9662/77664.png)

> _Internal NAND - Sequential Read_

![Internal NAND - Sequential Write](http://images.anandtech.com/graphs/graph9662/77665.png)

> _Internal NAND - Sequential Write_

![Internal NAND - Random Read](http://images.anandtech.com/graphs/graph9662/77667.png)

> _Internal NAND - Random Read_

![Internal NAND - Random Write](http://images.anandtech.com/graphs/graph9662/77668.png)

> _Internal NAND - Random Write_

In practice, it seems random IO performance is relatively low, but it's likely that we're looking at a bottleneck of the testing methodology as the queue depth of the test is 1 and given PCB size limitations it isn't reasonable to have as many NAND die working in parallel as we would see in something like a laptop. However, when we look at sequential speeds we can really start to see the strengths of the new storage controller and SLC/TLC. In the interest of seeing the limits of this SLC cache I decided to try running this test over a 5GB span.

![](http://images.anandtech.com/doci/9662/iP6sPlus_256KSeq_5GB_575px.png)

The graph is a bit difficult to interpret, but in effect we're looking at the time it takes to write 256KB at a time until we get to 5GB. There are two notable spikes roughly around 2GB, but it appears to be small and likely to be some kind of garbage collection or some background work. At 3GB or so the latency increases which suggests that the SLC cache is overrun and write bandwidth is limited by TLC NAND performance.

Overall, NAND performance is impressive, especially in sequential cases. Apple has integrated a mobile storage solution that I haven't seen in any other device yet, and the results suggest that they're ahead of just about every other OEM in the industry here by a significant amount.

Storage aside, the SoC itself sees major changes this year. Apple has moved to a FinFET process from either TSMC or Samsung for the A9 SoC. However, it still isn't clear whether the A9 is single source from one foundry or if A9 is being dual-sourced. [Chipworks has reason to believe](http://www.chipworks.com/about-chipworks/overview/blog/inside-the-iphone-6s) their iPhone 6s' A9 is fabricated on Samsung's 14nm process, though it hasn't been confirmed yet. Dual-sourcing is well within Apple's capabilities, however TSMC's 16nm and Samsung's 14nm process are not identical - naming aside, different processes developed by different fabs will have different characteristics - so dual-sourcing requires a lot more work to get consistent chips out of both sources. For what it's worth A8 was initially rumored to be dual-sourced as well, but decapping by Chipworks only ever turned up Samsung chips.

Moving on, let's talk about initial performance and battery life measurements, which look promising. Of course, it's worth noting that the web browser benchmarks we currently have are often optimization targets for OEMs, so web browser benchmarks seen here aren't necessarily evidence that the browser experience will be performant and smooth across all scenarios.

![Kraken 1.1 \(Chrome/Safari/IE\)](http://images.anandtech.com/graphs/graph9662/77650.png)

> _Kraken 1.1 (Chrome/Safari/IE)_

![Google Octane v2  \(Chrome/Safari/IE\)](http://images.anandtech.com/graphs/graph9662/77651.png)

> _Google Octane v2 (Chrome/Safari/IE)_

![WebXPRT 2013 \(Chrome/Safari/IE\)](http://images.anandtech.com/graphs/graph9662/77652.png)

> _WebXPRT 2013 (Chrome/Safari/IE)_

![WebXPRT 2015 \(Chrome/Safari/IE\)](http://images.anandtech.com/graphs/graph9662/77653.png)

> _WebXPRT 2015 (Chrome/Safari/IE)_

Regardless of whether an OEM is optimizing specifically for these benchmarks, it's hard to ignore just how well Apple has optimized Safari and the dual core Twister CPUs as they've effectively set new records for these benchmarks in mobile. Of course, to try and really figure out the relative performance between CPU architectures when ignoring differences in operating system and developer convention we'll have to turn to some of our native benchmarks such as SPEC CPU2000, but this will have to wait for the full review. What we can look at are some of our standard benchmarks that test graphics and game-related performance.

![3DMark 1.2 Unlimited - Overall](http://images.anandtech.com/graphs/graph9662/77654.png)

> _3DMark 1.2 Unlimited - Overall_

![3DMark 1.2 Unlimited - Graphics](http://images.anandtech.com/graphs/graph9662/77655.png)

> _3DMark 1.2 Unlimited - Graphics_

![3DMark 1.2 Unlimited - Physics](http://images.anandtech.com/graphs/graph9662/77656.png)

> _3DMark 1.2 Unlimited - Physics_

In 3DMark, we see the continuation of a long-running trend in the physics test in which the primary determinant of performance is clock speed and memory performance as data dependencies mean that much of the CPU's out of order execution assets go unused. However, in graphics we see an enormous improvement, to the extent that the A9's PowerVR GPU is actually beating the iPad Air's GXA6850 GPU by a significant margin.

![GFXBench 3.0 Manhattan \(Onscreen\)](http://images.anandtech.com/graphs/graph9662/77657.png)

> _GFXBench 3.0 Manhattan (Onscreen)_

![GFXBench 3.0 T-Rex HD \(Onscreen\)](http://images.anandtech.com/graphs/graph9662/77659.png)

> _GFXBench 3.0 T-Rex HD (Onscreen)_

![GFXBench 3.0 Manhattan \(Offscreen\)](http://images.anandtech.com/graphs/graph9662/77658.png)

> _GFXBench 3.0 Manhattan (Offscreen)_

![GFXBench 3.0 T-Rex HD \(Offscreen\)](http://images.anandtech.com/graphs/graph9662/77660.png)

> _GFXBench 3.0 T-Rex HD (Offscreen)_

In GFXBench, we see a similar trend which is incredible to think about. Apple has managed to fit a GPU into the iPhone 6s that is more powerful than what was in the iPad Air 2 for OpenGL ES, which is really only possible because of the new process technology that enables much lower power consumption and higher performance.

![GFXBench 3.0 Driver Overhead Test \(Offscreen\)](http://images.anandtech.com/graphs/graph9662/77661.png)

> _GFXBench 3.0 Driver Overhead Test (Offscreen)_

While I don't normally call attention to most of the GFXBench subtests, in this case I think the driver overhead is worthy of special attention as it highlights one of the real-world benefits that improved CPU performance has. While we often think of CPU and GPU performance as orthogonal, the GPU is fundamentally tied to CPU performance to a certain extent as traditional APIs like OpenGL ES can have significant CPU overhead, especially as GPU performance has grown far faster than CPU performance. For APIs like OpenGL ES, to set up a frame it's necessary for the CPU to check that the API call is valid, then do any necessary GPU shader or state compilation and begin running code on the GPU at draw time, which incurs increasing overhead as scenes become more complex. Through a combination of efficient drivers and enormous CPU performance, the dual core Twister CPU manages to set a new record for OpenGL ES driver overhead.

![Web Browsing Battery Life \(WiFi\)](http://images.anandtech.com/graphs/graph9662/77669.png)

> _Web Browsing Battery Life (WiFi)_

The final piece of data I've been able to collect over the course of the past few days is basic WiFi battery life. For those that are unfamiliar with the changes from the iPhone 6 line to iPhone 6s, the iPhone 6s now has a 1715 mAh (6.517 WHr) battery, and the iPhone 6s Plus has a 2750 mAh (10.45 WHr) battery. Both have a battery about 5.5-6% smaller than the previous generation.

Interestingly, the iPhone 6s Plus appears to actually have accordingly less battery life at 12.9 hours, or right around 6% less than the iPhone 6 Plus. This could be evidence that there haven't been any efficiency improvements to the iPhone 6s line, but given that our testing shows Apple is already at the point where our web browsing test is effectively a pure display rundown it's likely we're looking at the worst-case difference. This warrants additional investigation, but it's possible that a more balanced workload will even out the difference in battery life and maybe even tilt the scales back towards the iPhone 6s depending upon how much load is placed on the SoC.

![](http://images.anandtech.com/doci/9662/DSC_3787_575px.jpg)

Overall, while there's still a great deal of work left to do to exhaustively evaluate the iPhone 6s and 6s Plus, the initial results are quite positive. I haven't finished a detailed investigation into the architecture of Twister, but I suspect we're looking at some pretty significant changes compared to Typhoon, which would be unlike the smaller move from Cyclone to Typhoon. The GPU improvements are enormous, and while we don't have enough data to determine whether the iPhone 6s retains the same sustained GPU performance that we saw in the iPhone 6, the peak performance figures are impressive to say the least. The SSD-like storage solution is also a major surprise, and likely to be overlooked as its effects are often hard to distinguish without direct comparison. Battery life does regress in a single test, but I suspect in real-world situations with less of a focus on the display battery life will either be equal or favor the iPhone 6s, so it will be interesting to see if Apple's battery life estimates remain as accurate as they traditionally have been. We've definitely discovered much more about the iPhone 6s than what we're able to cover in this initial article, so stay tuned for the full review.
