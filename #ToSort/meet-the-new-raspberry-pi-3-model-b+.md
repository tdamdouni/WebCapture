# Meet the New Raspberry Pi 3, Model B+

_Captured: 2018-03-16 at 06:26 from [blog.hackster.io](https://blog.hackster.io/meet-the-new-raspberry-pi-3-model-b-2783103a147?mc_cid=a90c7728ed&mc_eid=1c68da4188)_

Earlier this morning the Raspberry Pi Foundation unveiled the latest board in their lineup, the Raspberry Pi 3 Model B+. Today's announcement comes just a couple weeks after the Raspberry Pi's [sixth birthday party](https://www.raspberrypi.org/blog/big-birthday-weekend-2018-roundup/), and a little over two years since the [release of the Raspberry Pi 3 Model B](https://makezine.com/2016/02/28/meet-the-new-raspberry-pi-3/).

![](https://cdn-images-1.medium.com/freeze/max/60/1*dPMGU-yawX6J_usKHvMy7w.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1600/1*dPMGU-yawX6J_usKHvMy7w.jpeg)

> _The new Raspberry Pi 3 Model B+ (📷: The Raspberry Pi Foundation)_

Based around the same 64-bit quad-core Broadcom BCM2837 processor as its predecessor, but now clocked at 1.4GHz rather than 1.2GHz, the new Raspberry Pi board will run [only moderately faster](https://medium.com/@ghalfacree/benchmarking-the-raspberry-pi-3-b-plus-44122cf3d806)--around fifteen percent--and comes with the same 1GB of LPDDR2 SDRAM as its predecessor.

However while the footprint of the board remains the pretty much same as the Raspberry Pi 3, the board itself looks somewhat different. Whereas it was quite hard to tell the Raspberry Pi 3 from its predecessor, the Pi 2, or even the B+ that proceeded that, the new board looks cleaner and is a lot more sparsely populated.

With the processor encapsulated in a new package with a heat spreader for better thermal control, and the wireless chips now in an RF shielded module--along with the custom power supply based around a MaxLinear [MxL7704](https://www.exar.com/ds/mxl7704.pdf)--the board now looks almost empty, and significantly the new RF shielding also means that the board comes with RF modular compliance certification, allowing it to be designed into end products with much reduced compliance testing.

For the first time the Raspberry Pi also offers dual-band 2.4GHz and 5GHz wireless networking, with the new RF shielded module based around a Cypress [CYW43455](http://www.cypress.com/documentation/product-overviews/cyw43455-wiced-ieee-80211ac-wifi-bluetooth-41-connectivity-solution) providing IEEE 802.11.b/g/n/ac wireless LAN, as well as Bluetooth 4.2/BLE.

The other big change is visible to the right of the board. The LAN7514 chip which has acted as the USB hub and as the Ethernet Controller for the Pi since the Model B+ was released back in 2014, has been replaced by the LAN7515.

If we [compare the LAN7515 to the previous LAN7514](https://www.microchip.com/wwwproducts/ProductCompare/LAN7515/LAN9514) chip we can see this is a crucial change, and one that a lot of people have been calling for since the Raspberry Pi originally launched. Because it means that, again for the first time, this is a Raspberry Pi with Gigabit Ethernet. Although since this is still Ethernet over USB, the maximum throughput will be limited to 300Mbps.

In the same way the earlier Model B+ was about [fixing a lot of the problems](https://makezine.com/2014/07/14/first-look-at-the-new-raspberry-pi-b/) and getting as much from the hardware used in the original Raspberry Pi as possible, the new board is a refinement of the existing Raspberry Pi 3.

> "This sort of attention to detail work is exactly what I love about being involved with Raspberry Pi. We're squeezing the last drops of performance out of the 40nm process node, and perfecting Pi 3 in the same way that the original B+ perfected Pi 1." _-- Eben Upton, Founder, Raspberry Pi Foundation_

The new board is an evolution rather than a revolution, and that's not a bad thing. This is the Raspberry Pi [maturing as a technology platform](https://medium.com/@aallan/capable-computing-50867847a8d8). As we've now wrung the last bits of performance out of the current platform, it's interesting to speculate what the Foundation might do around the next board. The Raspberry Pi 4 might well turn out to be as big a jump from this matured Model B+ as the [Raspberry Pi 2 was from the original Model B+](https://makezine.com/2015/02/02/eben-upton-raspberry-pi-2/).

One thing to be aware of is that the tolerances on the power supply, already fairly tight for the Raspberry Pi 3 Model B, are even thiner for the new Model B+. If you don't have a reliable 2.5 Amp USB power supply you might want to invest in [the official Raspberry Pi Power Supply](http://amzn.to/2pbsx96) to power the new board.

The Raspberry Pi 3 Model B+ does have 'one more thing' to surprise us with: it comes with Power over Ethernet (PoE) capability as well.

PoE will be provided via a n[ew official PoE add-on HAT](https://blog.hackster.io/the-new-raspberry-pi-poe-hat-823de8a8f5f) for the Raspberry Pi which will be available to buy from the summer 2018.

We've also heard some rumours that, despite the physical specification of the PCB mounting holes for the new Model B+ board being in the same place [as the Raspberry Pi 3](https://www.raspberrypi.org/documentation/hardware/raspberrypi/mechanical/Raspberry-Pi-3B-V1.2-Mechanical.pdf), there may be some problems with third-party cases that clash with the new PoE header block.

> "Cases which make assumptions about the z-height of particular points over the surface of the board may have issues. Examples would be cases which intrude into the space occupied by the new 4-pin PoE header, or which have components designed to thermally couple to the top of the processor package which now has greater z-height." _-- Eben Upton, Founder, Raspberry Pi Foundation_

The Model B+ is available to buy today from resellers in the UK, however the wait for FCC approval means that the Raspberry Pi 3 Model B+ won't be available on launch day in the United States. The [publication of FCC documents](https://hackaday.com/2016/10/10/using-the-fcc-eas-for-fun-and-profit/) ahead of launch has lead to leaks about many new products, including [the Raspberry Pi 3](https://fccid.io/2ABCB-RPI32) where rumours of the new board leaked out almost two weeks ahead of the official launch.

This probably explains why the Foundation has held off submitting documents to the FCC on the new board before ahead of announcing it this morning. But we're assured that the FCC filing for the new board will be submitted this morning, and the Foundation has units sitting in bonded warehouses on the East Coast ready for customs clearance as soon as the offices open for business.

That means the board could arrive on shelves as early as Friday, although it's more likely that they'll hit retail stores on Monday. The board keeps the same $35 price tag as its predecessor.

**Update:** More information on the [new PoE HAT](https://blog.hackster.io/the-new-raspberry-pi-poe-hat-823de8a8f5f) is now available.
