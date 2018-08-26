# The New Raspberry Pi PoE HAT

_Captured: 2018-03-16 at 06:28 from [blog.hackster.io](https://blog.hackster.io/the-new-raspberry-pi-poe-hat-823de8a8f5f?mc_cid=a90c7728ed&mc_eid=1c68da4188)_

Announced alongside [the new Raspberry Pi 3 Model B+](https://blog.hackster.io/meet-the-new-raspberry-pi-3-model-b-2783103a147) this morning was an official [Power over Ethernet](https://en.wikipedia.org/wiki/Power_over_Ethernet) (PoE) HAT to accompany the board. The HAT is not scheduled to be released until the summer, and beyond the fact it existed, there were few other details available… at least until now.

![](https://cdn-images-1.medium.com/freeze/max/60/1*j4k4loHWb_3_UoEdqokWLA.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1600/1*j4k4loHWb_3_UoEdqokWLA.jpeg)

> _The Raspberry Pi PoE HAT. (📷: Farnell/Element14)_

As Farnell has now published [a product page](http://cpc.farnell.com/raspberry-pi/rpi3-modbp-poe/poe-hat-for-raspberry-pi-3-model/dp/SC14884) for the new PoE HAT.

It is Class 2 device, and Power over Ethernet (PoE) 802.3af compliant, with a fully isolated Switched-Mode Power Supply (SMPS). Input voltage range can be between 36 and 56V, with an output voltage is 5V at 2.5Amps.

It is "plug-and-play" compatible with the new [Raspberry Pi 3 Model B+](https://blog.hackster.io/meet-the-new-raspberry-pi-3-model-b-2783103a147), although obviously not with previous models, and the product page suggests that the onboard fan may be controllable--perhaps over GPIO?

While the addition of PoE to the latest Pi is probably the result of pressure from commercial users--who account for about a third of all sales--the inclusion of the PoE headers on the board itself hasn't been given a universal welcome.

While the physical specification of the PCB mounting holes for the new Model B+ board are in the same place [as the Raspberry Pi 3](https://www.raspberrypi.org/documentation/hardware/raspberrypi/mechanical/Raspberry-Pi-3B-V1.2-Mechanical.pdf), the Foundation has acknowledged that there may be some problems with third-party cases that clash with the new PoE header block.

> "Cases which make assumptions about the z-height of particular points over the surface of the board may have issues. Examples would be cases which intrude into the space occupied by the new 4-pin PoE header, or which have components designed to thermally couple to the top of the processor package which now has greater z-height." _-- Eben Upton, Founder, Raspberry Pi Foundation_

However it's yet unclear whether the headers will really interfere with existing HATs, as others aren't seeing any problems quite yet.

The new HAT will be priced at £17.75 (including VAT), which is just under $25 at current exchange rates, and should be available from summer 2018.
