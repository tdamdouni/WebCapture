# Setting up the Edimax EW-7811Un or Tenda W311Mi 802.11b/g/n WiFi Adapter on a Raspberry Pi

_Captured: 2017-05-21 at 10:52 from [www.jeffgeerling.com](https://www.jeffgeerling.com/blogs/jeff-geerling/edimax-ew-7811un-tenda-w311mi-wifi-raspberry-pi)_

> Note: On Raspberry Pi models with built-in WiFi (e.g. the Raspberry Pi 3 model B), USB WiFi interfaces will use `wlan1` (`wlan0` is reserved for the first interface, in this case the internal one).

Since this is maybe the fourth time I've done this process on my Raspberry Pis, I decided to document the process of setting up cheap mini WiFi adapters on a Raspberry Pi A+/B+/2.

This process works great with any USB WiFi adapter that's supported out of the box. My three favorites (due to their inexpensive price and decent connection speed/reliability) are:

  * [Tenda W311Mi 802.11b/g/n USB WiFi adapter](http://www.microcenter.com/product/411056/W311Mi_Wireless_N_Pico_USB_20_Adapter) (usually available for under $10 from Micro Center)
  * [Kootek 802.11b/g/n USB WiFi adapter with Realtek RTL8188CUS chipset](http://www.amazon.com/gp/product/B00FWMEFES/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00FWMEFES&linkCode=as2&tag=mmjjg-20&linkId=RQUVE4XMKPUGROY2) (usually available for under $10 from Amazon)

## Configuring the adapter

  1. Make sure the Raspberry Pi sees the adapter on the USB bus: `$ lsusb`.
  2. Make sure the network interfaces file (`/etc/network/interfaces`) has a `wlan0` configuration; if not, make it look somewhat like the following:  
`allow-hotplug wlan0  
iface wlan0 inet manual  
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf`
  3. If the Pi doesn't connect automatically within 10-20 seconds, you can manually refresh the interface to connect and get an IP address: `$ sudo ifdown wlan0 && sudo ifup wlan0`. Then run `ifconfig` to find your IP address (in the `wlan0` section).

You can also reboot your Pi entirely (`$ sudo reboot`) to make sure the configuration sticks and your Pi joins the network automatically. I typically set up static IP reservations on my network router, so each Pi gets a permanent IP address.

Also, if you need to scan for a list of the WiFi networks your Pi can see, run `sudo iwlist wlan0 scan`.

Troubleshooting the wifi connection:

  * Make sure your Pi can see the network you're trying to connect to: use `$ sudo iwlist wlan0 scan | grep ESSID` to list all the found network SSIDs. If you're network isn't in the list, it might be a 5GHz network (the Edimax only works on 2.4GHz networks), or it might be out of range.
  * To find your IP address, MAC address, and other interface information, run the command `$ ifconfig -a`.

## Ensuring the adapter doesn't go into sleep mode

One of the most annoying things that can happen with a headless wifi-connected computer is the wireless connection dropping, or hanging for 10+ seconds at a time. It seems the Edimax is configured to go into a sleep state after a few seconds of inactivity by default, but this can be disabled pretty easily:

  1. Create a configuration file for the adapter: `$ sudo nano /etc/modprobe.d/8192cu.conf`
  2. Reboot your Raspberry Pi: `$ sudo reboot`

I've had one Pi running for almost a year now, doing nothing but some temperature data aggregation inside the house, and the Edimax WiFi adapter has been rock solid. A missed packet here or there, but way more reliable than any other cheap adapter I've used!

I've only recently started using the Tenda adapter, but so far it seems to be just as reliable as the Edimax, despite being a little less popular. It doesn't seem to require any extra configuration to stay out of sleep mode, and it's readily available at my local Micro Center!
