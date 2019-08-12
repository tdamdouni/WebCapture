# Casio Pi Portable CCTV Monitor

_Captured: 2018-11-10 at 10:58 from [www.instructables.com](https://www.instructables.com/id/Casio-Pi-Portable-CCTV-Monitor/)_

![](https://cdn.instructables.com/F7M/BQ2U/JN0L3LTC/F7MBQ2UJN0L3LTC.LARGE.jpg?auto=webp&width=900)

![](https://cdn.instructables.com/FL2/9UCC/JN0L3LSN/FL29UCCJN0L3LSN.LARGE.jpg?auto=webp&width=300)

![](https://cdn.instructables.com/FOO/GW5M/JN0L3LT0/FOOGW5MJN0L3LT0.LARGE.jpg?auto=webp&width=300)

![](https://cdn.instructables.com/FUG/HY7Z/JNOVKYVI/FUGHY7ZJNOVKYVI.LARGE.jpg?auto=webp&width=300)

About: I love the design and ambition of vintage technology, and the usability and potential of new - my passion is bringing the two together. [More About MisterM »](https://www.instructables.com/member/MisterM/)

## Intro: Casio Pi Portable CCTV Monitor

In this Instructable I'll show you how to convert an obsolete portable LCD TV into a low-cost and retro-cool display for a Raspberry Pi project. I'll take you through all the stages of making a handy CCTV monitor with a 1997 Casio EV-510 and a Raspberry Pi Zero W, but we'll also look at the many other possibilities!

The original TV circuit is untouched and the Pi is fixed neatly under the battery cover, playing a video stream from the local network, all powered from a USB power bank.

I love these pocket LCD TVs, especially as they're so cheap to pick up second hand, I remember paying £2 for this one. Since the analogue TV channels were switched off they're pretty much useless - **unless** you have one like this that has the all-important 3.5mm Audio/Video input, in which case you can easily give it a new lease of life with a Raspberry Pi.

It's a pretty straightforward build - you can see the project in action and follow the whole end-to-end process on the YouTube video at <https://youtu.be/SLkvcTYdm-A> , there are also links in each Instructable step to the relevant parts of the video.

## Step 1: Proof of Concept

![Picture of Proof of Concept](https://cdn.instructables.com/F34/Q8OU/JN0L3MCP/F34Q8OUJN0L3MCP.LARGE.jpg?auto=webp&width=624)

![Picture of Proof of Concept](https://cdn.instructables.com/FN5/0Y4N/JN0L3MCQ/FN50Y4NJN0L3MCQ.LARGE.jpg?auto=webp&width=576)

Before doing any dismantling I wanted to test the setup to make sure this old TV would work with the Pi. I set a video stream running on the Pi Zero using [omxplayer](https://www.raspberrypi.org/documentation/raspbian/applications/omxplayer.md) (more on coding this later) then experimented with different cable combinations to connect the jumpers of the analogue video output of the Pi to the 3.5mm Audio/Video input of the TV. This took some trial and error to get a clear picture (if you have a very bad picture it's likely the wiring of the cable!) but I ended up with a clear view from the local IP camera.

I also tested powering both the Pi and the TV simultaneously from the same USB source and thankfully this worked - I planned to use a USB power bank so needed to use a single power cable for both.

Having convinced myself that it would work I moved on to more fiddly matters - dismantling the TV.

## Step 2: Dismantling and Chopping

![Picture of Dismantling and Chopping](https://cdn.instructables.com/FLO/KC6B/JN0L3N5W/FLOKC6BJN0L3N5W.LARGE.jpg?auto=webp&width=800&crop=3:2)

![Picture of Dismantling and Chopping](https://cdn.instructables.com/FQ6/IZ0E/JN0L3N5Y/FQ6IZ0EJN0L3N5Y.LARGE.jpg?auto=webp&width=400&crop=3:2)

![Picture of Dismantling and Chopping](https://cdn.instructables.com/FAA/U0BE/JN0L3N6N/FAAU0BEJN0L3N6N.LARGE.jpg?auto=webp&width=400&crop=3:2)

Dismantling video: <https://youtu.be/SLkvcTYdm-A?t=147>

I had two main objectives for the dismantling - to get the TV circuit out of the case without destroying it and to double-check that the Pi would actually fit in there.

The dismantling went well at first, just four small screws held the two halves of the TV together and they came apart quite easily. Unfortunately all of the TV's circuitry was fixed to the front side, ruining my hopes of easily turning the battery compartment into a cosy Pi-den. It turned out that all of the circuit components had to be removed from the case, really tense work as one false snip would bring an end to the project. The LCD panel was attached to the circuit with a small ribbon cable, which I was very nervous of removing, but once that was out of the way I was able to separate the circuit boards a bit and gain access to the final screws holding in the LCD panel.

Chopping video: <https://youtu.be/SLkvcTYdm-A?t=563>

Next I fired up the rotary tool and started chopping away the battery holders, leaving what I hoped would be plenty of space for the Pi. Checking it afterwards however it was obvious that the Pi Zero I'd been using for testing was never going to fit. It had a standard 40-pin header soldered on, but in addition to that also had a Button Shim, which was bulking it up far too much. I decided to start over with a fresh Pi Zero, leaving the header off - but even then it was still too wide, so I had to do some more detailed chopping around the case as well as remove part of the Pi's camera connector. It was a perfect fit finally, but with not even a millimetre to spare.

## Step 3: Pi Hardware and Soldering

![Picture of Pi Hardware and Soldering](https://cdn.instructables.com/FGW/LP3Z/JMKVC6ZE/FGWLP3ZJMKVC6ZE.LARGE.jpg?auto=webp&width=898)

![Picture of Pi Hardware and Soldering](https://cdn.instructables.com/F24/DHNZ/JNOVFJE6/F24DHNZJNOVFJE6.LARGE.jpg?auto=webp&width=302&crop=3:2)

![Picture of Pi Hardware and Soldering](https://cdn.instructables.com/FIX/LOWP/JMKVC77O/FIXLOWPJMKVC77O.LARGE.jpg?auto=webp&width=302)

![Picture of Pi Hardware and Soldering](https://cdn.instructables.com/F2X/P42M/JNOVFJE7/F2XP42MJNOVFJE7.LARGE.jpg?auto=webp&width=302)

Hardware & Soldering Video: <https://youtu.be/SLkvcTYdm-A?t=714>

I needed to save as much space as possible to stand a chance of the Pi still fitting once all the original electronics had been reassembled, so decided to power it via the GPIO instead of with a Micro USB cable. I read up on the [risks of doing this ](https://www.raspberrypi.org/magpi/power-supply/)beforehand, and was happy to continue. Instead of fitting a 40-pin header I just soldered a red wire to 5v (pin 2) and a black wire to GND (pin 6) as the rest of the GPIO pins wouldn't be needed for this simple build.

Next I snipped a four-connector piece off the end of a right angle 40 pin header for the TV connection and soldered it to the board. Only two of the connectors were needed, but having the four together gave it a bit more stability. The beauty of using the right angle header piece is that the connecting TV cable stays nice and flat along the top of the Pi rather than sticking up.

Lastly I joined a couple of female jumper cable ends to a stripped-down 3.5mm audio cable to make the connector between the Pi and the TV. The internal wiring of these cables can vary so you may need a bit of trial and error if you're doing the same.

## Step 4: Pi Software

![Picture of Pi Software](https://cdn.instructables.com/FAV/15NQ/JNOVL25G/FAV15NQJNOVL25G.LARGE.jpg?auto=webp)

![Picture of Pi Software](https://cdn.instructables.com/FGH/KJ25/JNOVL25F/FGHKJ25JNOVL25F.LARGE.jpg?auto=webp&width=307)

![Picture of Pi Software](https://cdn.instructables.com/F4O/2YQK/JNOVL1QR/F4O2YQKJNOVL1QR.LARGE.jpg?auto=webp&width=307)

Software & Coding Video: <https://youtu.be/SLkvcTYdm-A?t=922>

The soldering wasn't too taxing, just six joints (though I did mess one up and had to re-do it) so I moved on to setting up the Pi software.

I began with a fresh install of [Raspbian](https://www.raspberrypi.org/downloads/raspbian/), installed all of the available updates then made the following changes:

Enabling SSH - As this Pi would be running headless I enabled SSH so I'd be able to log into it remotely, for example to change the URL of the video stream. This setting can be changed in Preferences > Raspberry Pi Configuration > Interfaces.

Setting the output to PAL - I'm not 100% sure this is needed, but I edited the config.txt file...

sudo nano /boot/config.txt

...and uncommented the line:

sdtv_mode = 2

After these changes were made I needed to test the stream to make sure the Pi would display it. The streaming URL of my camera is http://192.168.0.59:8081 so I opened a terminal and typed:

omxplayer --live http://192.168.0.59:8081

To my amazement a live view from the camera popped up on the screen straightaway! The camera I'm using is another Pi Zero, powered by a LiPo battery and running [MotionEye OS](https://github.com/ccrisan/motioneyeos/wiki), which I'd already set to a 4:3 resolution so that the stream would be the right shape for the TV. The --live part of the command helps it play without buffering, and it works really well.

To get the stream to load on startup I just edited the following file...

nano ~/.config/lxsession/LXDE-pi/autostart

...and added the following at the bottom of the list:

@omxplayer --live http://192.168.0.59:8081

After a reboot the stream loaded instantly once the Pi desktop had loaded - coding done!

## Step 5: Assembly

![Picture of Assembly](https://cdn.instructables.com/FR4/5RUQ/JN0L4NGH/FR45RUQJN0L4NGH.LARGE.jpg?auto=webp&width=909&crop=3:2)

![Picture of Assembly](https://cdn.instructables.com/FHC/E3RL/JN0L4NGO/FHCE3RLJN0L4NGO.LARGE.jpg?auto=webp&width=291)

![Picture of Assembly](https://cdn.instructables.com/FZE/MQEC/JN0L4NGP/FZEMQECJN0L4NGP.LARGE.jpg?auto=webp&width=291&crop=3:2)

![Picture of Assembly](https://cdn.instructables.com/FEM/SM5N/JNOVL43L/FEMSM5NJNOVL43L.LARGE.jpg?auto=webp&width=291&crop=3:2)

Assembly Video: <https://youtu.be/SLkvcTYdm-A?t=1387>

Before starting the assembly I tested the newly-programmed Pi to make sure everything was working as intended, then began by soldering the power inputs of the Pi and the TV to a USB cable. Next I carefully bent back these wires so that the Pi was sitting in roughly the right place on the circuit board.

I was able to fairly easily reverse the dismantling process, nervously fitting the fiddly screws, and just before putting the case halves back together I hot-glued the Pi to the case. I normally like to use bolts or screws for this but there just wasn't the space this time!

It took some gentle squeezing and persuading but eventually the case closed with a click and I was able to secure it with the final four screws.

One final test and I was so relieved to see the Pi logo and boot sequence!

With everything working I secured the USB cable to the back of the TV with cable tie holders, and hot-glued a handy USB power back to the back of the case, in place of the kick-stand.

## Step 6: More Possibilities

![Picture of More Possibilities](https://cdn.instructables.com/F4M/J6W8/JN0L4PQF/F4MJ6W8JN0L4PQF.LARGE.jpg?auto=webp&width=838&crop=3:2)

![Picture of More Possibilities](https://cdn.instructables.com/FW5/O5HJ/JNOVFJGY/FW5O5HJJNOVFJGY.LARGE.jpg?auto=webp&width=362)

![Picture of More Possibilities](https://cdn.instructables.com/FGP/H963/JNOVFJZ8/FGPH963JNOVFJZ8.LARGE.jpg?auto=webp&width=362)

More Options Video: <https://youtu.be/SLkvcTYdm-A?t=1789>

This was a fun little build, it didn't take a long time and the coding wasn't too complicated but I'm very pleased with the result. It's a really practical piece now, and I love that I didn't have to change the external appearance too much.

You could easily achieve the same thing using a new LCD display from one of the Pi accessory shops, but for me the challenge was making use of a TV that had cost me £2, bringing an obsolete piece of old tech back to life.

I have several more of these TVs and I'm now thinking what else could be built!

\- Maybe add in a Python script and use a button to switch between different stream URLs

\- Use just a Pi Zero without the WiFi and have it play locally-stored videos on a loop

\- Add in an IR receiver, load up [OSMC](https://osmc.tv/) and make a teeny remote-controllable Kodi box

\- Add in an [Adafruit Joy Bonnet](https://www.adafruit.com/product/3464) and make a mini handheld [RetroPie](https://retropie.org.uk/) console - I've tested this a bit and it would definitely work and just about fit - you'd ideally need to fit in a USB sound card though.

\- Now that the [Raspberry Pi TV HAT](https://www.raspberrypi.org/blog/raspberry-pi-tv-hat/) has been released you could even stream a live digital TV signal from another Pi on the network to this little Casio - bringing it full circle and keeping faithful to its original function.My TV HAT arrived a few days ago so this may well be the first thing I try.

If you enjoyed this Instructable check out my [other projects](https://www.instructables.com/member/MisterM/instructables/ ) and subscribe to [Old Tech. New Spec. on YouTube](https://www.youtube.com/channel/UCRrwSKYBu4N7P6HWZsWJ2MA?view_as=subscriber) for more videos!
