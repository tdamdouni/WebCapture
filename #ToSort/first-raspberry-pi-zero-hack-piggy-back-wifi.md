# First Raspberry Pi Zero Hack – Piggy-Back WiFi.

_Captured: 2017-05-23 at 18:49 from [hackaday.com](https://hackaday.com/2015/11/28/first-raspberry-pi-zero-hack-piggy-back-wifi/)_

![](https://hackadaycom.files.wordpress.com/2015/11/raspi_edimax_hack_2-1.jpg?w=800)

And we have the [first Raspberry Pi Zero hack](http://www.hackerspace-ffm.de/wiki/index.php?title=Raspberry_PI_Zero_%2B_nano_USB_WiFi_Adapter_mod)! In less than 72 hours from the official release announcement [Shintaro] attached an Edimax WiFi USB Adapter directly to the USB solder pads on the Pi Zero. He couldn't bear to disturb the small dimensions of the Pi Zero by using the USB On-the-Go (OTG). The OTG is needed to convert the micro-USB connector on the board to a full USB-A connector.

The case was removed from the Edimax and the device and Zero wrapped in Kapton to insulate the exposed solder points. Power was taken from the PP1 and PP6 points on the back of the board. These are the unregulated inputs from the USB power so should be used with caution. Some cheap USB power supplies can put out more that 5 volts when first connected and that might let the smoke out of a device.

![raspberry_pi_quarter](https://hackadaycom.files.wordpress.com/2015/11/raspberry_pi_quarter.jpg)

The data wires were connected to PP22 and PP23, also on the back, and behind the USB data connector. Since USB is a differential signal these wires were carefully kept of equal length to avoid distorting the signal.

An SD card was created and edited on a Raspberry Pi B 2 to set the WiFi credentials. Inserted into the Zero it booted fine and started up the WiFi network connection.

Congratulations, [Shintaro] for the first Hackaday Raspberry Pi Zero hack. Is that a Hack-a-Zero-Day hack?
