# How do you tell the time in binary?

_Captured: 2018-07-29 at 10:37 from [hackspace.raspberrypi.org](https://hackspace.raspberrypi.org/features/how-do-you-tell-the-time-in-binary?mc_cid=ea66ed996f&mc_eid=9b04ee1c98)_

![](https://images.ctfassets.net/q092pc69zo4z/5rFAd2LoY0myYCiIOIqEQc/ccbdfd347527be1b8d2fb09e9496d78a/Binary_Clock.jpg)

I am David Watts (yes, I have heard the song), and I am a self-styled maker/tinkerer. I learnt how to wire a plug at school, but that is about as far as my electronics education extends.

I call this the 'BCD Crap Clock' - why? Well, it lowers expectations with the hope of exceeding them. BCD stands for Binary-Coded Decimal - you see, it isn't a true binary clock.

![Issue 9 cover](https://s3-eu-west-1.amazonaws.com/rpi-magazines/issues/cover_images/000/000/017/original/HS_9_Cover_Web.jpg?1531491616)

Tools: they help us give form to our ideas but which ones to you need? We take a look at 50 of our favourite maker tools to help you equip your workshop. We also build an auto-targeting water cannon and look into how electricity works. 

[Buy Issue 9](https://hackspace.raspberrypi.org/features/how-do-you-tell-the-time-in-binary?mc_cid=ea66ed996f&mc_eid=9b04ee1c98) [Download Free PDF](https://s3-eu-west-1.amazonaws.com/rpi-magazines/issues/full_pdfs/000/000/017/original/HS_9_Digital_Optimised.pdf?1531983540)

This is a fairly crap 'binary' clock kit made with CMOS logic, a simple design without a microcontroller, and it has the unique feature of being both difficult to read and difficult to set the time! It is a curiosity rather than a real timepiece, but it is at least better than guessing the time. Consider it an exercise in learning about CMOS logic and making my first kit that would go on to sell out in a day on Tindie.

It uses quite a few ICs for something that could be achieved with one PIC or ATmega but hey, there are advantages. It runs down to about 2.7-3 V, consuming 0.5 mA with LEDs enabled or ~6 µA with the LEDs disabled, meaning it could keep time for decades on a few AA cells. Also, I get 'no microcontroller' bragging rights.
