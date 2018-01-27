# Is Cellular Finally Becoming a Real Option for the Internet of Things?

_Captured: 2017-10-05 at 19:19 from [blog.hackster.io](https://blog.hackster.io/is-cellular-finally-becoming-a-real-option-for-the-internet-of-things-959d8318b6be)_

## A look at the new Nova cellular modem from Hologram.io.

There's a long history of maker built cellular-based smart devices. One of the first projects I ever backed on Kickstarter, back in 2012, was the [Geogram One](https://www.kickstarter.com/projects/dsscircuits/open-source-tracking-device)--an Arduino-compatible tracking board that you could communicate with via SMS messages.

But cellular is expensive, not just the hardware itself, but perhaps more importantly the data plans you needed to use it. Cellular operators have been hamstrung by their pricing models, something that has driven the rapid expansion of [community LoRa networks](https://www.thethingsnetwork.org/).

However more recently companies like [Particle](https://www.particle.io/) have made access to cellular technology easier, and cheaper, for makers. Last month they were joined by Hologram, who [kicked off their developer program](https://blog.hackster.io/using-cellular-data-for-the-internet-of-things-3c0c2be4fc6) offering free [developer SIMs](https://hologram.io/devplan/) with 1MB/month of data included which will use [over 900 operators](https://gist.github.com/sandeepmistry/af0491a262a4cb9cce88afb40b13d019) globally.

Hologram started out [under a different name on Kickstarter](https://www.kickstarter.com/projects/konekt/konekt-dash-cellular-dev-kit-free-global-data-plan) with a board that eventually became the [Hologram Dash](https://hologram.io/dash/), and now they're back with new hardware--a cellular modem [called Nova](http://www.hologram.io/nova).

![](https://cdn-images-1.medium.com/freeze/max/60/1*HtG4vX8VdBhT2w9aX0vxqg.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1600/1*HtG4vX8VdBhT2w9aX0vxqg.jpeg)

> _The Hologram Nova. (📷: Hologram.io)_

One of the things holding cellular back is the reliance by most on cheap 2G hardware that is quickly becoming obsolete as [2G network are being turned off](https://www.theverge.com/2012/8/3/3218332/att-2g-network-2017) around the world. Although the ever practical Europeans might well [turn off their 3G networks before the 2G network](http://blog.telegeography.com/2g-is-fading-away-but-it-might-outlive-3g-in-europe), due to this problem, and the large number of machine-to-machine (M2M) traffic on the legacy networks.

At launch the Nova will come in two configuration options. The first will be available globally and leveraging the [ublox SARA-U201](https://www.u-blox.com/en/product/sara-u2-series) module for 3G [HSPA](https://en.wikipedia.org/wiki/High_Speed_Packet_Access) support globally with 2G fallback. While inside the US there will also be an option configured with the [ublox SARA-R404M](https://www.u-blox.com/en/product/sara-r4-series) module supporting 4G LTE CAT-M.

The Nova is a bare bones USB stick designed to be a hackable transition between prototype and production. The design of the Nova will be open sourced and with the Nova will exposing available cell module GPIO with micro pads, developers should be able to get much better access to the cell module that the Nova is built around than is typical.

At launch the the modem will be supported by a [Python SDK](https://hologram.io/docs/reference/cloud/python-sdk/), however we've been told that Node, C++, and Go SDKs are on the roadmap.

Support will initially be available for Debian based systems -- so that means the Raspberry Pi, BeagleBone, and CHIP -- with support for OpenWRT systems such as the Arduino Yun and the Tessel coming later, and support for Windows 10 Core to eventually follow. The SDKs will be released under an MIT license.

All the core functionality of the cellular modem will also be exposed in a command line interface to assist in troubleshooting and debuging.

The SDK itself will let you do all the usual things--like send and receive data--but will also give you access to location triangulation based on cell towers, as well as beta access to SIM authentication which will allow you to talk to the [Hologram Cloud](https://hologram.io/cloud/) without having to embed an API key into your code.

Using the cloud side of Hologram you will also be able to SSH through the cellular modem into the attached device, and replicate any commands you send across all of your deployed devices. That's not that interesting when you have one or two devices, but if you're dealing with a large Internet of Things deployment with hundreds--or thousands--of sensors out in the field, it suddenly becomes much more vital.

It's fairly obvious that the Nova has been designed to be a bare bones, and at least to an extent, an entirely replaceable piece of hardware. Like their developer program, which offers free SIMs and free data, the Nova is there to tempt developers to use the Hologram Cloud and--like Particle before them--help them build a developer community.

Developers can start off [working with a Raspberry Pi](https://www.hackster.io/hologram/add-cellular-to-a-raspberry-pi-with-a-hologram-nova-ea5926) and the Nova--along with Hologram's SDK and Cloud--and then build a product without having to change their code. For instance moving directly from a standard Raspberry Pi 3 to the Compute Module, alongside a custom PCB integrating the same [ublox module](https://www.u-blox.com/en/product-search/field_product_class/modules-199/field_product_form/sara-111) as the Nova, would mean that you wouldn't have to change anything at all.

The 2G/3G model of the Hologram Nova is [available today](http://www.hologram.io/nova), and costs $49. You can also pick up a [Hologram Global SIM Card](https://hologram.io/store/developer-global-iot-sim-card/) on their Developer Plan, which includes up to 1MB of data per month, for free, and right now Hologram is running a promotion. The first 1,000 Nova orders will receive $30 of additional free data.

Partnering with both Hackster and Raspberry Pi, [Hologram will also be kicking off a contest](https://www.hackster.io/contests/hologram), which will be ship up to free 200 Nova sticks to participants worldwide. So if you have a good idea, you might well be able to build it for free.
