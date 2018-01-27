# Controlling servo: how to determine the angle and needed pulse-width?

_Captured: 2017-11-11 at 02:17 from [electronics.stackexchange.com](https://electronics.stackexchange.com/questions/210354/controlling-servo-how-to-determine-the-angle-and-needed-pulse-width)_

I'm kind of new when it comes to using servo's with an Raspberry Pi. Although I do have some experience, I'd like to understand things a bit better. Therefore I would like to share some questions with you and hope to gain some better insights in how to work with servo's.

The questions I'm currently struggling with:

**1.** Given the specifications of the Servo, how can I deduct the minimum and maximum values (angles) of the servo?   
**2.** Using the PWM Hat described below, and the python library the comes with it, how exactly do I calculate the time that the PWM pulse needs to be set to High to achieve a certain angle? For example: what would be the PWM pulse high length to send to the servo so it will be at a 90 degree position? And what would it be for an 120 degree position?

Any thoughts, remarks or comments are highly appreciated, thanks in advance!

**Hardware and software specifications**

**_The servo_**

The servo we have is [this one](http://www.rc-addict.nl/webshop/5074-power-hd-lf-20mg-60g--20kg--016sec), the Power HD LF-20MG

Torque (4.8V): 16.5 kg-cm  
Torque (6.6V): 20 kg-cm  
Speed: 0.18sec (4.8V) | 0.16sec (6.6V)  
Operating voltage: 4.8 - 6.6 DC Volts  
Weigt: 60g  
Working frequency: 1520us (=1.52ms) at 333Hz  
Max-travel: 165 degrees

**_The PWM controller_**

To control the Servo using a Raspberry Pi we use [thi](https://www.adafruit.com/products/2327)s Adafruit's PWM/SERVO HAT for precise timing. The HAT must be controlled using their Python library in which the following functions control the servo:

**_The PWM software controller_**

First, setting the frequency. Based on the servo's specifications I guess it should be 333.
    
    
    pwm.setPWMFreq(333)
    

Secondly there's a function that actually controls the PWM pulse. This is were I'm really doubting (see the second question above).
    
    
    var port = 15
    var tickHigh = 0
    var tickLow = 1400 #For example; range from 0-4096
    pwm.setPWM(port, tickHigh, tickLow)
    

As stated in the docs (see [this link](https://learn.adafruit.com/adafruit-16-channel-pwm-servo-hat-for-raspberry-pi/library-reference)), the values to use are calculated based on the pulse-width needed in microseconds. But I'm really struggling here: I can't seem to determine what the needed pulse-width should be for this servo (hence the to questions).   
IF I was to know that, the calculation for the software becomes a lot easier:  
(1 / frequency) / 4096 = time per tick  
For this servo's frequency that would be: (1/333) / 4096 = 0,00000073315503   
Then I could use the following formula, given the needed pulse width length needed:  
pulse length needed / time per tick = tickHigh
    
    
    > If you need to calculate pulse-width in microseconds, you can do that
    > by first figuring out how long each cycle is. That would be 1/freq
    > where freq is the PWM frequency you set above. For 1000 Hz, that would
    > be 1 millisecond. Then divide by 4096 to get the time per tick, eg 1
    > millisecond / 4096 = ~0.25 microseconds. If you want a pulse that is
    > 10 microseconds long, divide the time by time-per-tick (10us / 0.25 us
    > = 40) then turn on at tick 0 and turn off at tick 40.
    

Your question was way too long to read.

These kind of hobby servo motors are controlled by the width of a pulse. The standard range is from 1 to 2 ms, and should be repeated every 20-50 ms. 1.5 ms pulse width will put the servo in the middle of its range, with 1 ms to one end and 2 ms to the other. Some servos can go a little farther in response to values a little past the 1-2 ms range.

Most will tell you the angle range they are intended to work over, so that gives you some idea of the angle change per pulse width increment on your end.

In the end, remember these are hobby servos, so don't expect a real datasheet with everything properly spelled out. The best way to know what a particular hobby servo can do is to measure it. Set up a jig that can vary the pulse width from 500 µs to 2.5 ms and see what the unit does in response.
