# Guest Blogger: Phil Underwood hacking the Bareables Badge

_Captured: 2017-11-18 at 23:53 from [lorrainbow.wordpress.com](https://lorrainbow.wordpress.com/2017/11/18/guest-blogger-phil-underwood-hacking-the-bareables-badge/)_

![](https://lorrainbow.files.wordpress.com/2017/11/20171118_221327.jpg?w=1640&h=624&crop=1)

[Pimoroni](https://shop.pimoroni.com/) are selling very cute flashing badges in a range called [Bareables](https://shop.pimoroni.com/collections/bearables) (get it??). You can wear them as a badge that flashes a number of patterns or connect it to a motion or light sensor. After buying one and showing it off on Twitter the conversation quickly turned to how we could hack it. The next day Pimoroni announced a competition for people to hack the badge, the quickest would win a pHat Stack.

> When we said that was just a programming header on the back of the Bearables badges, we kind of lied…
> 
> We'll give a fully-assembled pHAT Stack to the first person who successfully hacks a new pattern onto their badge and provides code/video proof. Tag with [#bearableshack](https://twitter.com/hashtag/bearableshack?src=hash&ref_src=twsrc%5Etfw) [pic.twitter.com/a59PiJ7DY5](https://t.co/a59PiJ7DY5)
> 
> -- pimoroni (@pimoroni) [November 17, 2017](https://twitter.com/pimoroni/status/931496743220457472?ref_src=twsrc%5Etfw)

My husband Phil is actually a bigger geek than me, especially when it comes to electronics. So he decided to hack the bearables badge

### Research observation

There are five pads on the back of the badge. Using a multimeter in continuity check mode he worked out which pad connects to which pin on the chip. Pimoroni told us that the chip is a [http://www.microchip.com/wwwproducts/en/PIC16F1503](http://PIC16F1503)

![20171118_213455.jpg](https://lorrainbow.files.wordpress.com/2017/11/20171118_213455.jpg?w=1240)

He connected one probe on the multimeter to the first pad then tried every pin on the chip with the other probe until it beeped and discovered that:

  1. First pad connects to Pin4, its function is VPP/MCLR (resets the chip or puts it into programming code)
  2. Second pad connects to Pin13, its function is ICSPDAT (sends data to the chip)
  3. Third pad connects to Pin12, its function is ICSPCLK (clock used to tell the chip when data on ICSPDAT has changed)
  4. Fourth pad connects to Pin14, its function is Ground
  5. Fifth pad connects to Pin1, its function is VDD (Power supply for the chip)

## Hacking

**Connect the badge to the pi**

With two female to female jumper wires:

  1. Cut them in half
  2. Strip the wire at the cut end
  3. Solder the wire to each pad (you only need the middle 3 pads)
  4. Connect the headers as follows, to a Raspberry Pi 
    1. Pad2 connects to Pin3 (SDA1)
    2. Pad3 connects to Pin5 (SCL1)
    3. Pad4 connects to Pin6 (GND)

**Connect to the Pi**

Turn on i2c on the Pi:

  1. In a terminal on the Pi: 
    1. Type _sudo raspi-config_
    2. Select Interfacing Options
    3. Enable i2c

Each device on an i2c bus has it's own address. Raspberry Pi has a handy utility called i2cdetect to find all connected devices

  1. Type _ic2detect1 _
  2. This showed a device at address 15 - woohoo!
  3. NOTE: This is 15 hexadecimal which is 21 in decimal, which is what we need![Screenshot from 2017-11-18 21-54-04.png](https://lorrainbow.files.wordpress.com/2017/11/screenshot-from-2017-11-18-21-54-04.png)

Now it's guessing time!

In the terminal window type

_i2c set 1 21 0 0_

This sends a 0 to device at address 21 to memory location 0. This turned all the lights off, woo! Slightly worried that he actually broke it… so he tried sending

_i2c set 1 21 0 1_

And nothing happened, ahhhh! Start panic sending numbers to the device (add -y for quicker testing)

  * _i2c -y set 1 21 0 2_
  * _i2c -y set 1 21 0 3_
  * _i2c -y set 1 21 0 4_
  * _i2c -y set 1 21 0 5_
  * _i2c -y set 1 21 0 6_

PANIC. Start looking up how much these bears cost…

_i2c -y set 1 21 0 16 _

The lights came back on. Hurrah! Phew.

_i2c -y set 1 21 0 17_

A single light came on… oooo. Time to try different registers:

_i2c -y set 1 21 1 22_

This turned two lights on. Further experimenting showed that each of the memory locations between 1 and 7 correlated to 2 of the lights on the Bearable. The first light is controlled by the higher nybble of the byte. The second light is connected by the lower nybble. Also sent in the nybble is the brightness level. The maximum brightness for each light is 7.

The code for controlling the Bearable is here. Happy hacking!

import smbus

import time

DEV_ADDRESS = 0x15

class Bearable():

def __init__(self):

self.bus=smbus.SMBus(1)

self.leds = [0]*12

def enable_hack_mode(self, on=True):

if on:

self.bus.write_byte_data(DEV_ADDRESS,0,0x11)

else:

self.bus.write_byte_data(DEV_ADDRESS,0,0x10)

def set_led(self,number, brightness):

self.leds[number] = min(brightness,8)

def clear(self):

self.leds = [0]*12

self.update() 

def update(self):

for i in range(0, len(self.leds), 2):

byte = self.leds[i]*16 +self.leds[i+1]

index = (i/2)+1

self.bus.write_byte_data(DEV_ADDRESS, index, byte)

if __name__=="__main__":

bear = Bearable()

bear.enable_hack_mode(True)

for i in range(6):

for j in range(8):

bear.set_led(i,j)

bear.set_led(i+6,j)

bear.update()

time.sleep(0.050)

for j in range(8):

bear.set_led(i, 7-j)

bear.set_led(i+6, 7-j)

bear.update()

time.sleep(0.050)

time.sleep(0.200)

bear.clear()

bear.update()

bear.enable_hack_mode(False)
