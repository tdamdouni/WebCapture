# I'm in the mood...for hacking

_Captured: 2017-05-23 at 18:58 from [bigl.es](http://bigl.es/im-in-the-mood-for-hacking/)_

## Blinkies...everywhere!

![alt](https://farm1.staticflickr.com/721/33261096186_f741d06a36_z_d.jpg)

You may have noticed, but there was another Raspberry Pi released the other day. Yes we now have the new Pi Zero W, the W stands for Wireless, obvs!

![alt](https://farm3.staticflickr.com/2856/32458916044_0667a01117_z_d.jpg)

So now we have a Pi Zero with WiFi (b,g,n) and Bluetooth 4.0, all for $10, bargain for Internet of Things and embedded projects.

> Spending a little quality time with [@pimoroni](https://twitter.com/pimoroni) mood light [pic.twitter.com/HYZGrgB5Ib](https://t.co/HYZGrgB5Ib)
> 
> -- biglesp (@biglesp) [March 6, 2017](https://twitter.com/biglesp/status/838797894744432640)

## Kits

![alt](https://farm1.staticflickr.com/724/33302427505_1e92852396_o_d.png)

One of the surprises for the Pi Zero W launch, were a series of kits from Pimoroni. These kits contain all of the parts that you will need to build a project. Emma from Pimoroni very kindly sent me a review sample and this is the kit that I used for this post.

![alt](https://farm4.staticflickr.com/3831/33146322682_d3eed2e7c2_z_d.jpg)

I received the [Mood light project kit](https://shop.pimoroni.com/products/mood-light-pi-zero-w-project-kit) which comes with

  * A Raspberry Pi Zero W
  * GPIO header (to solder)
  * Mini HDMI and micro USB to USB A adapter.
  * Unicorn pHAT (32 super bright WS2812B LEDs, known as Neopixels)
  * USB lead
  * Laser cut parts for assembly.
![alt](https://farm4.staticflickr.com/3842/33146336072_4e62c369b4_z_d.jpg)

![alt](https://farm4.staticflickr.com/3924/33146343312_83fceb5f7f_z_d.jpg)

## Building at the dining table

![alt](https://farm1.staticflickr.com/693/33173848301_6e9bc5bf39_z_d.jpg)

So [using the great instructions, written by Sandy.](https://learn.pimoroni.com/tutorial/sandyj/assembling-mood-light) I got to work building the kit.

First up, assembling the laser cut pieces...oh and peeling the protective tape off

![alt](https://farm4.staticflickr.com/3675/33261063336_80ab2acc3e_z_d.jpg)

I then soldered up the GPIO pins on the Raspberry Pi Zero, and the header connection on the Unicorn pHAT. I used my USB soldering iron..._I really need to write a post on that iron as it is rather good for jobs like this._

Finally I assembled the stand and attached it to the main frame.

![alt](https://farm4.staticflickr.com/3734/33261085166_f9da5bd635_z_d.jpg)

## Software

Installing the software was a breeze, I just [followed the guide for the Unicorn pHAT](https://github.com/pimoroni/unicorn-hat) and then ran the example script to test that it all worked....which it did.

## Automate all teh things

_deliberate typo_

I wanted the mood light to run on boot, so I used the example _rainbow.py_ which is an executable Python script, and edited my cron file so that it ran on boot.

To do this I opened a terminal and typed
    
    
    sudo crontab -e  
    

I then added a new line to the end of my cron file so that on reboot it ran the executable Python code.
    
    
    @reboot /path/to/the/Rainbow/example/code.py
    

_Remember to change the path to the location of the code that you want to run_

So now when I power up the mood light, it automatically runs the rainbow.py example code and lights up my bookshelf.

![alt](https://farm4.staticflickr.com/3833/33173830161_7c8c008ddf_z_d.jpg)

## Conclusion

This kit was great fun to build, it took me about an hour to make the entire kit. This includes writing a new SD card for the Pi Zero W, and tinkering with the example code so that the Unicorn pHAT LEDs were a little brighter.

![alt](https://farm3.staticflickr.com/2902/32459764604_568a852b6c_z_d.jpg)

The kit retails for £30, which is a great price considering how much stuff is packed into the box...oh yeah the plastic box that contains the project kit is really nice quality and can be re-purposed to contain your Pi kit when you are travelling to Jams etc.

If you are just starting on the path to becoming a maker, then kits such as these should be your first step. Easy and fun to build, with a clear goal for the maker to work to.

You can [buy the mood light project kit from Pimoroni for £30](https://shop.pimoroni.com/products/mood-light-pi-zero-w-project-kit) and there are [other kits available.](https://shop.pimoroni.com/collections/raspberry-pi-zero)

![alt](https://farm3.staticflickr.com/2916/32920012990_9e525dce61_z_d.jpg)

All in all, an enjoyable hour of hacking.

## For my next trick

I'm messing around with MQTT and I reckon I can now have my mood light react to triggers from external devices...watch this space :D
