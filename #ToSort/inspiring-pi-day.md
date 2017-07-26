# Inspiring Pi Day

_Captured: 2017-05-23 at 18:59 from [bigl.es](http://bigl.es/inspiring-pi-day/)_

## It'ssssss Pi Day.

tl;dr Alex has created a great Kickstarter to enable anyone to hack with the APA102 LEDs and make cool sculptures with light. [The Kickstarter is still live and you should go and back it!](https://www.kickstarter.com/projects/raspitv/raspio-inspiring-connect-rgb-led-shapes-sculpt-you)

For this special blog post I took a look at [Alex Eames' latest Kickstarter.](https://www.kickstarter.com/projects/raspitv/raspio-inspiring-connect-rgb-led-shapes-sculpt-you)

# RasPiO InsPiRing

Alex is a _serial_, no pun intended Kickstarter and has successfully delivered many Kickstarters and products.

![alt](https://farm9.staticflickr.com/8642/28396312425_bb4b764dd5_z_d.jpg)

Alex very kindly gave me a bleeding edge prototype board as he knows that I am already a backer for this project.

## So what is it?

![alt](https://farm4.staticflickr.com/3773/32624643223_a720b32307_k_d.jpg)

> _Excuse the mess...it's always like that_

![alt](https://farm3.staticflickr.com/2878/33440003045_a303c889ba_o_d.gif)

At it's core the project are a series of inter-connectable APA102 LED modules that come in a range of shapes enabling you to build cool things with lots of lights. The modules can be controlled using devices such as

![alt](https://farm4.staticflickr.com/3893/33056951140_88a55cf192_z_d.jpg)

  * Raspberry Pi (even the new Pi Zero W)
  * Arduino
  * ESP8266
  * ATtiny
  * micro:bit (work is progressing on this)

### APA102 LEDs...?

These are becoming more and more popular, with companies such as Pimoroni using them in products such as PHAT BEAT, Blinkt and Rainbow HAT.   
Adafruit use these same LEDs in their DotStar strips.

The [APA102 datasheet](https://hyperion-project.org/attachments/apa102_led-pdf.102/) _<< (Warning PDF download)_ shows that it uses the SPI interface on the Raspberry Pi, which is really easy to use and can be enabled using the Raspberry Pi Configuration tool.

![alt](https://farm4.staticflickr.com/3822/33283389552_f6cf1284f5_o_d.png)

They are a little different to the Neopixel (WS2812B) protocol LEDs, as using these with the Raspberry Pi requires split second timing using PWM (Pulse Width Modulation) and this also renders the analogue audio out of a Pi useless as it conflicts with the Neopixels.   
The APA102 only use the SPI interface, which means that we can play audio via the analogue audio port and have lots of flashing LEDs...BLISS!

## The PCBs

![alt](https://farm4.staticflickr.com/3936/32624652903_17a81a2ee5_k_d.jpg)

_These are prototype PCBs and the quality is not as high as those that will be shipped to Kickstarter backers, I trust Alex on his PCB QA as I have backed many of his Kickstarters._

The PCBs are connected using a 4 pin male / female connection, enabling the user to chain many units together and make a crazy sculpture with light...in three dimensions.   
Some soldering is required for the PCBs, but this is only for the 4 pins on either side of the board.

## The Controller

![alt](https://farm4.staticflickr.com/3730/33438553555_2c64fe2013_z_d.jpg)

For the Raspberry Pi there is a controller board that breaks out the connections via an [SN74AHCT125N logic shifter](http://bigl.es/inspiring-pi-day/SN74AHCT125N) _<< (Warning PDF download)_ which the APA102 LEDs require for 5V logic.   
The board has breakouts for the four pins (5V, GND, Clock and Data) so all you need to do is attach your PCBs and start building a masterpiece.

## Software

### Raspberry Pi

I've only had chance to test the software for the Raspberry Pi   
The software is still under wraps for now, but what I can say is that it is a Python based interface to interact and control the APA102 LEDs.   
The library depends on `python-spidev` in order to talk to the LEDs, but this is an easy installation.
    
    
    sudo apt install python-spidev  
    

I had a tinker with a few of the examples and settled on this little animation for my final test.

![alt](https://farm3.staticflickr.com/2846/32625051173_063c8e6db7_o_d.gif)

## Conclusion

This is still in prototype form, but I can see that this project has legs. The ability to control the LEDs using many different boards means that you are not stuck with a product that is a "one trick pony". If you want to plug it into an Arduino, go for it, fancy some Twitter controlled LEDs with a Pi, sure! Or if you want to control your desk lights using an ESP8266, then you can!   
I had great fun hacking around with this kit and I can't wait to get my final Kickstarter reward.

Alex has done a great job with the Kickstarter, which was funded in just over 8 hours! (8.63hrs)

## Back it!

There is still time to back this great Kickstarter, [just head over and pledge your support!](https://www.kickstarter.com/projects/raspitv/raspio-inspiring-connect-rgb-led-shapes-sculpt-you)

![alt](https://farm4.staticflickr.com/3874/32624650743_9ccc7db57a_z_d.jpg)

> _Yes that is a hot glue Lego mini fig with an LED in it's chest_
