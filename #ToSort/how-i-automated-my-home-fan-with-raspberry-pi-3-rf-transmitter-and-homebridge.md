# How I Automated My Home Fan with Raspberry Pi 3, RF Transmitter and HomeBridge

_Captured: 2017-04-15 at 00:57 from [hackernoon.com](https://hackernoon.com/diy-home-automation-fan-control-with-raspberry-pi-3-rf-transmitter-and-homebridge-59ad24845770?source=userActivityShare-c79006fee040-1492210645)_

I have always wanted to get involved in a hardware project. And I love home automation. So automating my home fan seems to be the perfect project to start with.

![](https://cdn-images-1.medium.com/freeze/max/30/1*Bge5IaWRdDp1oRZ-c5C3BQ@2x.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*Bge5IaWRdDp1oRZ-c5C3BQ@2x.jpeg)

I use HomeKit for my door locks and lights. When I leave, HomeKit will lock my door and turn off all lights. But I always have to search for my fan remote to turn it off manually. It is not how I imagine my smart home should be.

### Setting up the Raspberry Pi

Having had no experience with hardware, starting on my first project was quite intimidating. I did some research on what I needed, then purchased a [Raspberry Pi starter kit](https://www.amazon.com/CanaKit-Raspberry-Ultimate-Starter-Kit/dp/B01C6Q4GLE/ref=sr_1_1?ie=UTF8&qid=1491809908&sr=8-1-spons&keywords=canakit+ultimate+raspberry+pi+3&psc=1) and [a pair of 433Mhz receiver/transmitter](https://www.amazon.com/433Mhz-Transmitter-Receiver-Link-Arduino/dp/B016V18KZ8/ref=sr_1_2?ie=UTF8&qid=1491810017&sr=8-2&keywords=433+Mhz+RF+Transmitter).

Setting up Raspberry Pi 3 was a lot easier than I thought. [Canakit Ultimate Starter Kit](https://www.amazon.com/CanaKit-Raspberry-Ultimate-Starter-Kit/dp/B01C6Q4GLE/ref=sr_1_1?ie=UTF8&qid=1491809908&sr=8-1-spons&keywords=canakit+ultimate+raspberry+pi+3&psc=1) comes with the OS preloaded in a microSD card. It also comes with jumper wires, a breadboard, a GPIO to breadboard interface board, LEDs and resistors.

The next thing I did, I went through an [LED tutorial](https://thepihut.com/blogs/raspberry-pi-tutorials/27968772-turning-on-an-led-with-your-raspberry-pis-gpio-pins), and figured out how to use the breadboard. I was not sure if I would fry my Raspberry Pi if it was not connected properly, so I turned off the device during setup, turned it on when I was done. When connected wrongly, the device simply did not boot. I was lucky, the LED test went fine. That is equivalent to the 'Hello World' of coding.

### Reading RF Signals

I suspected that my fan remote uses RF because it can work from a different room, but I was not sure that a 433Mhz receiver/transmitter was the right hardware to buy. It was a guess, but it worked out for me.

My first task was to read signals with the RF receiver. I followed [this guide closely](http://www.princetronics.com/how-to-read-433-mhz-codes-w-raspberry-pi-433-mhz-receiver/)--installed _wiringPi_ and _433Utils_, connected the data-pin of the RF receiver to GPIO27, GND to GND, VCC to 5V, run _RFSniffer_ and pressed my remote. It worked!

### Sending RF Signals

Next, I connected the 433Mhz RF transmitter following the instructions [here](https://shop.ninjablocks.com/blogs/how-to/7506204-adding-433-to-your-raspberry-pi). I was able to test that the transmitter was working fine using _codesend_ to transmit a number, and received by the RF receiver running _RFSniffer_.

### Sending RF Signals to emulate fan remote

Everything went very smoothly until this point. However, the signal received from my remote using _RFSniffer_ were not able to control my fan when re-transmitted with _codesend_. There must be something I misunderstood about how RF remote works. Looks like the hardware was the easy part.

After installing _pilight_, I configured it to work with my setup. The photo above shows that RF transmitter was connected to pin 17 and RF receiver to pin 27.

The sender and receiver value in the config.json file can be determined by referencing the GPIO table above. Sender value at pin 17 should be 0, and receiver value at pin 27 should be 2.

Then I used _[pilight-debug_](https://wiki.pilight.org/doku.php/pdebug) to read and output raw information from my remote. Remember to kill _pilight-daemon _before running _pilight-debug_.
    
    
    pi@raspberrypi:~/ $ sudo killall pilight-daemon

The raw code from _pilight-debug_ is a series of numbers, with each single number measuring the time difference between a HIGH-LOW or LOW-HIGH transition. There were a lot of other noise signals, so I had to filter manually for the correct signal that originated from my remote. It seems the trick is to look out for series of numbers that only contain three unique numbers. These 'cleaner' numbers are only ones that worked for me. I had to keep pressing my remote until I get a code that looks 'clean' like this.
    
    
    209 627 627 209 209 627 209 627 209 627 209 627 209 627 627 209 209 627 209 627 209 627 209 627 209 627 209 627 209 627 209 627 627 209 627 209 209 627 209 627 209 627 209 627 209 627 209 627 209 7106

Then I used _pilight-send_ to send the raw code (If you have previously killed _pilight-daemon_, remember to start it again `sudo pilight-daemon`). Viola! It worked. I repeated that for all buttons on the remote to get the different code for turning off, and changing speed. The signals are different for different remotes as well, so I have to repeat the same steps for the fan in my bedroom even though it is the same model.
    
    
    pi@raspberrypi:~/ $ sudo pilight-daemon
    
    
    pi@raspberrypi:~/ $ pilight-send -p raw -c “209 627 627 209 209 627 209 627 209 627 209 627 209 627 627 209 209 627 209 627 209 627 209 627 209 627 209 627 209 627 209 627 627 209 627 209 209 627 209 627 209 627 209 627 209 627 209 627 209 7106”

### Apple HomeKit integration with HomeBridge

Now that I have managed to control my fan with command line, the next step is to get it working with HomeKit. _HomeBridge_ is an open-sourced _NodeJS_ server to emulate iOS _HomeKit_ API. You can find the instruction to install _HomeBridge_ in Raspberry Pi [here](https://github.com/nfarina/homebridge/wiki/Running-HomeBridge-on-a-Raspberry-Pi).

_pilight_ has a _[HomeBridge_ plugin](https://www.npmjs.com/package/homebridge-pilight). However, I had to create a custom plugin instead because I could not figure out how to set up _pilight_ to do this. I found an open-source _HomeBridge_ plugin to control a 3-speed TOSR0x fan, [homebridge-tosr0x-fan](https://github.com/jasoncodes/homebridge-tosr0x-fan) via API calls. I used that as a template for my plugin.

I created a REST API using _Python/Flask_ that executes _pilight-send_ with command line.

Then I modified the plugin to call the _REST API_, and removed temperature sensor, which is not supported by my fan.

I used the command below to install the plugin, though it is slower compared to [setting up a development folder](https://github.com/nfarina/homebridge#plugin-development).
    
    
    pi@raspberrypi:~/ $ npm install -g homebridge

After installing the plugin, I added my fans to _HomeBridge_ by editing the configuration file in ~_/.homebridge/config.json_. The key 'accessory' has to be identical to the name declared in the plugin.

Restart _HomeBridge_ for changes to take effect.
    
    
    pi@raspberrypi:~/ $ sudo killall homebridge

Not bad for my first hardware hack, done in a weekend.

If you are trying to replicate the same setup for your RF remote controlled fan, you will have to identify the signals again because it will be different from mine. Good luck!
