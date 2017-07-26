# How I gained access to TMobile’s national network for free

_Captured: 2016-11-06 at 21:50 from [medium.com](https://medium.com/@jacobajit/how-i-gained-access-to-tmobiles-national-network-for-free-f9aaf9273dea#.so3g2rkxe)_

We'll see how long this survives after this post, of course…

![](https://cdn-images-1.medium.com/max/800/1*VwJYHPoPL-DD44iz1KAYBg.jpeg)

**Important edit**: I wanted to clarify that I have reached out to TMobile and am awaiting a response. However, I made a decision to go ahead and publish this in the meantime since this unintentional flaw does not pose any harm to TMobile or their customers. It's a trivial fix to whitelist Speedtest servers based on their official host list, as I point out in this post, and the educational benefits of sharing my findings with the community in this case outweighed the case for waiting for a [possible] response from TMobile. Shoutout to Vice! <http://motherboard.vice.com/read/a-teenage-hacker-figured-out-how-to-get-free-data-on-his-phone-t-mobile?utm_source=vicetwitterca>

One Friday night, I was sitting around pretending to be fine having absolutely nothing to do. I had a TMobile prepaid SIM on a spare phone with no active service, so I came up with a fun challenge: could I somehow get access to the internet without a data plan? Theoretically, the phone still had some sort of LTE connection, just one that would redirect to a captive portal asking me to upgrade my plan.

![](https://cdn-images-1.medium.com/max/800/1*HppQXpyROVWoadOikM-EKQ.png)

Naturally, I played around with this portal for a while, clicking on links and trying to escape. Some links failed, and some worked, somewhat randomly. The TMobile website seemed to load fine, even with its media-heavy content.

Then, I decided to stretch things a bit and see if any random apps would connect to the LTE. Sure enough, the Speedtest app was able to test my speed and display a respectable 20 mbps LTE connection. Clearly, the app was allowed to fetch data. One thing I noticed was that it was picking a TMobile Speedtest server. Just in case, I tried changing the server to a neutral third-party here. Still worked.

![](https://cdn-images-1.medium.com/max/800/1*nPraxLd2ngTxqIcIXkFR2A.png)

I was onto something, or was I? I assumed they must be whitelisting Speedtest-affiliated servers in some way, perhaps using the [official list](https://www.speedtest.net/speedtest-servers.php)? I wasn't too familiar with how Speedtest actually worked, so I decided to do some fieldwork with my phone connected to [mitmproxy](https://mitmproxy.org/) running on my Mac.

I was getting a better understanding of Speedtest works, looking at it download large 30x30 [images](http://208.54.35.70/speedtest/random4000x4000.jpg), etc. These files were hosted on various URLs, the only similarity between them being the /speedtest folder with its appropriate contents. I confirmed all of this by looking through Ookla's [documentation](http://www.ookla.com/support/a22030676/speedtest-installation). Just for kicks, I loaded up one of these images through Safari, figuring the requests would be served the same way.

![](https://cdn-images-1.medium.com/max/800/1*lbspAny7Osw3hidZxuxMNw.png)

> _Yuuuuuge JPG with random static -- the "speedtest"_

Now I got really curious. What if TMobile was simply checking for similarly formatted /speedtest folders without any real verification? So I set up my own little /speedtest folder on my page and loaded it up with various files.

![](https://cdn-images-1.medium.com/max/800/1*_qG4Y63ZoQjVO905eA_1vA.png)

> _Turns out the filenames within the /speedtest folder are irrelevant. This is blankspace.mp4._

Wow, this was great! I can now host all my Taylor Swift songs in the cloud and access them on my phone without paying for data! But having access to a set of predetermined files isn't quite as good as the good ol' web, is it?

I set up a proxy server on Heroku (edit: now down) using Glype. Now, to try it out.

![](https://cdn-images-1.medium.com/max/800/1*X66mH10-vzz4ft1r8_ZpXQ.png)

> _Excuse the ugly, unresponsive Glype interface._

![](https://cdn-images-1.medium.com/max/800/1*6trJcJfPgoBDvuUopIp7Ow.png)

> _Don't mind me, staying informed Kenya's environmental efforts on my free mobile data._

Just like that, I now had access to data throughout the TMobile network without maintaining any sort of formal payments or contract. Just my phone's radios talking to the network's radios, free of any artificial shackles. Mmm, the taste of liberty.

It's interesting to note this is a _very_ simple fix on TMobile's part. They simply need to make their whitelist check against the official Speedtest server list I [linked to](https://www.speedtest.net/speedtest-servers.php) earlier. But the bigger idea here is that people make mistakes due to oversight all the time. This time, I'm getting some unexpected free stuff. What about all those darker lurking zero-days that are so simple yet some engineer assumed everything would be alright? It's a bit scary, and reminds us that all of our systems are indeed developed by humans. For now.

Let's see how long before this glitch is solved. Clock starts now!

_Don't forget to heart and follow for more random musings. Need to get back to college apps for now :(_
