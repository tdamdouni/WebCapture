# The Internet of… Power Outlets?

_Captured: 2018-06-22 at 08:02 from [blog.hackster.io](https://blog.hackster.io/the-internet-of-power-outlets-ac8fcacde48d?mc_cid=69561dbd6c&mc_eid=1c68da4188)_

In modern houses, you'll have unprotected outlets, and those that feature arc fault interrupter (AFCI) circuits. These devices, seen mostly in bathrooms and kitchens, are designed to "fault out" if they detect a short, potentially endangering lives and property. Considering the dire consequences, these AFCI outlets are surely a good thing, providing another layer of safety for electrical dangers. On the other hand, these outlets often trip when there is no danger, simply because a high-load appliance such as a vacuum cleaner or window air conditioning unit start up.

![](https://cdn-images-1.medium.com/freeze/max/60/1*0qqxMX-eErScaaNSgxRh0Q.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1600/1*0qqxMX-eErScaaNSgxRh0Q.jpeg)

> _A team of MIT engineers has developed a smart power outlet that can "learn" to identify plugged-in appliances, and distinguish dangerous electrical spikes from benign ones. (📷: Christine Daniloff /_

While most of us reset the unit and then go about our lives, a team at MIT has been [developing a solution to this problem](https://news.mit.edu/2018/mit-engineers-build-smart-power-outlet-0615) in what they are calling a "smart power outlet." This system is designed to distinguish between benign power surges when an appliance starts up and actual dangerous situations. It currently runs on a [Raspberry Pi 3](http://hackster.io/raspberry-pi), using a USB sound card and current clamp for data acquisition and processing.

With data in hand, a machine learning algorithm is used to analyze when certain appliances are plugged in, then compare spikes to known power signatures. As this system is used by more and more people, the idea is that it will become more accurate, however even in testing it's already able to distinguish between a benign and dangerous surge with a 99.95% accuracy, higher than existing AFCI devices. It can also distinguish between types of gadgets with over 95% accuracy, another potentially useful feature.
