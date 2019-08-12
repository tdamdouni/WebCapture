# Set Up a Pi-hole with PiTFT Display for Nerdy Stats

_Captured: 2019-03-16 at 12:00 from [www.hackster.io](https://www.hackster.io/chriscw/set-up-a-pi-hole-with-pitft-display-for-nerdy-stats-d575aa?utm_source=Hackster.io+newsletter&utm_campaign=0bd5a7f925-EMAIL_CAMPAIGN_2019_02_14_02_53_COPY_01&utm_medium=email&utm_term=0_6ff81e3e5b-0bd5a7f925-141949901&mc_cid=0bd5a7f925&mc_eid=1c68da4188)_

![Set Up a Pi-hole with PiTFT Display for Nerdy Stats](https://hackster.imgix.net/uploads/attachments/805356/main-image-logo_s1uW7ms4OL.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

Recently, I posted a full tutorial telling you [how to set up Pi-hole for network-wide ad-blocking on your entire network](https://www.balena.io/blog/deploy-network-wide-ad-blocking-with-pi-hole-and-a-raspberry-pi/). Today I'm going to expand on that a little by showing you how to add a display to your setup for monitoring and statistics using [PADD](https://github.com/jpmck/PADD).

For this guide you'll need to be running the the [Pi-hole on balenaCloud](https://github.com/klutchell/balena-pihole) project by [@klutchell](https://github.com/klutchell) that we used in our [original guide](https://www.balena.io/blog/deploy-network-wide-ad-blocking-with-pi-hole-and-a-raspberry-pi/). This project already includes all of the additional software components we'll need to set up and run the display. If you've not set up your Raspberry Pi with this project yet, head over and work through [the guide](https://www.balena.io/blog/deploy-network-wide-ad-blocking-with-pi-hole-and-a-raspberry-pi/), then come back and we can continue on with the display setup.

Next, we're going to need some kind of display for the Raspberry Pi. In the original tutorial, I used a Raspberry Pi 3B+, and so I'm using an [Adafruit PiTFT 3.5"](https://www.adafruit.com/product/2441). This is a reasonably common display available from a few different vendors so shouldn't be too hard to obtain if you need to get one. Alongside [Adafruit themselves](https://www.adafruit.com/product/2441), take a look at [Pimoroni](https://shop.pimoroni.com/products/pitft-plus-480x320-3-5-tft-touchscreen-for-raspberry-pi-pi-2-and-model-a-b), [PiSupply](https://uk.pi-supply.com/products/adafruit-pitft-plus-480x320-3-5-tfttouchscreen-raspberry-pi-pi-2-model-a-plus-b-plus) and [Digi-Key](https://www.digikey.com/products/en?mpart=2097&v=1528).

![The Adafruit PiTFT 3.5](https://hackster.imgix.net/uploads/attachments/805258/adafruit-display_Obqzd8SjXs.jpg?auto=compress%2Cformat&w=740&h=555&fit=max)

> _The Adafruit PiTFT 3.5"_

Although not strictly required for this project, I wanted a nice case to display the unit on my desk. I found the [Pi TFT plus Console Case](https://www.thingiverse.com/thing:2471701) by [arcmatt](https://www.thingiverse.com/arcmatt/about) on Thingiverse which is designed to house the Pi along with the Adafruit screen in a neat little 3D-printable case.

![The case parts laid out in Cura before 3D printing](https://hackster.imgix.net/uploads/attachments/805260/case3d_YaMk5asmXT.png?auto=compress%2Cformat&w=740&h=555&fit=max)

> _The case parts laid out in Cura before 3D printing_

The case has a cool feature where you can pause your print and insert some captive M2.5 nuts before resuming. This means you get really nice and secure fixings when assembling the pieces of the case. Additionally the design includes options for printing a base that includes a fan for cooling of your Pi if you need it.

![3D printing in progress using my Ender 3](https://hackster.imgix.net/uploads/attachments/805264/case-printing_7lZy0L8yCm.jpg?auto=compress%2Cformat&w=740&h=555&fit=max)

For my own project I decided to print the model which includes a space for a 40mm fan. For this you'll need to obtain a 5V fan which you can then drive from the same power supply as the Pi.

If you don't have access to a 3D printer, take a look at the [Pibow PiTFT+ from Pimoroni](https://shop.pimoroni.com/products/pibow-pitft), which is available from [Adafruit](https://www.adafruit.com/product/2779) too.

If you're interested in seeing the case build, we live streamed the assembly of this case and installation of the software on our [Twitch channel @balenaio](https://www.twitch.tv/balenaio/) on the 1st March 2019. It's archived on our [YouTube channel](https://www.youtube.com/c/balenaio) and included below too.

> _Stream archive from the build_

Now that you've followed our [original guide](https://www.balena.io/blog/deploy-network-wide-ad-blocking-with-pi-hole-and-a-raspberry-pi/) there's very little left to do in order to enable the stats display.

The [Pi-hole project](https://github.com/klutchell/balena-pihole) includes the [PADD](https://github.com/jpmck/PADD) software already, but it's only enabled if it detects the PiTFT display connected to the system. Therefore, to get it up and running, we just need to add a few configuration variables in the balenaCloud dashboard to tell the system to load the driver for the screen and set the correct resolution.

All of the below values should be set in the **device configuration** within balenaCloud.

![](https://hackster.imgix.net/uploads/attachments/805319/screenshot_2019-03-12_at_15_08_10_h6y5sruoIt.png?auto=compress%2Cformat&w=740&h=555&fit=max)

After you've set these configuration variables and rebooted the device, the software should detect the display and automatically enable the PADD output. You should get output that looks something like the below.

Now that the display is up and running, we can do a little fine tuning of the output to get it to utilise the full display and look a bit better.

The output is quite compressed as the console uses a small font by default. We can change the font size to expand the output by editing the file `/mnt/boot/cmdline.txt` on the device.

![](https://hackster.imgix.net/uploads/attachments/805268/cmdline-txt_esU9BvFZjw.png?auto=compress%2Cformat&w=740&h=555&fit=max)

Edit this file to include `fbcon=font:VGA8x16` after `rootwait`; ensure you maintain a space between them.

![](https://hackster.imgix.net/uploads/attachments/805281/font-setting_8TGiyLAzew.png?auto=compress%2Cformat&w=740&h=555&fit=max)

Save your changes and reboot, and you should then have something like the below on your display.

![](https://hackster.imgix.net/uploads/attachments/805282/second-output_5Zr24hwdHK.jpg?auto=compress%2Cformat&w=740&h=555&fit=max)

This is a bit better in terms of readability, but alas now the output is too large for our display and the top few lines have been cut off. I mentioned in the configuration section above that the HDMI output is copied (via `fbcp`) to the PiTFT display. In order to gain a few more lines on the display we can drive it at a slightly higher resolution. This has the downside in that the pixel mapping will no longer be 1:1 and hence the display will not appear as sharp, but the benefit is that the full output will then fit on the screen.

To do this we need to increase the vertical resolution from `320` to `368` which gives us an extra 3 lines of display output. Alter `RESIN_HOST_CONFIG_hdmi_cvt` to be `480 368 60 1 0 0 0`, noting the change in resolution.

After one last reboot, you should then end up with an output that looks like the below.

![](https://hackster.imgix.net/uploads/attachments/805285/final-output_Zmquv89sbN.jpg?auto=compress%2Cformat&w=740&h=555&fit=max)

That's it for this project. For a little future addition I'm planning to implement a display backlight timeout and utilize the touchscreen to wake it back up when you need to see the information. This will be pushed to the same project repo when it happens so make sure you keep up to date!
