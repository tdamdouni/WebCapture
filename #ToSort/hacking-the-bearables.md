# Hacking the Bearables

_Captured: 2017-11-18 at 14:37 from [roques.xyz](https://roques.xyz/?p=71)_

![](https://roques.Xyz/wp-content/uploads/2017/11/Screenshot-2017-11-18-at-02.22.52-1024x544.png)

> _Much cute, such lights!_

Yesterday (as I write this), [Pimoroni](http://www.pimoroni.com), creators of the amazingly cute [Bearables](https://shop.pimoroni.com/collections/bearables), put out the following tweet:

> When we said that was just a programming header on the back of the Bearables badges, we kind of lied…
> 
> We'll give a fully-assembled pHAT Stack to the first person who successfully hacks a new pattern onto their badge and provides code/video proof. Tag with [#bearableshack](https://twitter.com/hashtag/bearableshack?src=hash&ref_src=twsrc%5Etfw) [pic.twitter.com/a59PiJ7DY5](https://t.co/a59PiJ7DY5)
> 
> -- pimoroni (@pimoroni) [November 17, 2017](https://twitter.com/pimoroni/status/931496743220457472?ref_src=twsrc%5Etfw)

Just like that, all the work I was about to do for the rest of Friday evaporated.

I must admit, I did have some prior knowledge of this hidden capability - as Phil adorned me with a Bearable at CamJam, he informed me that 'these are some power pins and a few data bus pins, sure you can figure them out' - but I forgot to do anything about it… until now!

The first step to working out what was what, was to look at the chip. A bit of googling and it was found to be a [PIC16F1503](http://www.microchip.com/wwwproducts/en/PIC16F1503) microcontroller. With datasheet in-hand, a spot of multimeter probing between the controller and the pins and I had the pinout: Prog. Vref / SDa / SCl / Gnd / VCC. I highly suspected the Bearables used I2C for the comms, as the same chip is used on all of Pimoroni's Flotilla line, where I2C is the main communication protocol. Makes sense, right?

After hooking it up to a Pi, and running a good ol' `i2cdetect`, my suspicions were proven correct - the Bearable appeared as 0x15! I tried sending it some 1s and 0s down the command line (with, frankly no clue what I was doing - I have yet to delve into the world of raw I2C comms on a Pi) but nothing happened. I also found the rather excellent [Raspberry Pi PIC Programmer](http://holdenc.altervista.org/rpp/), but I assumed that a full firmware rewrite wasn't necessary. I also have absolutely no experience with PIC microcontrollers, and the programmer software didn't support the chip in hand. Besides, everyone knows that Friday afternoons are not a good time to do important and serious things such as firmware flashing.

So I started looking for other approaches. The Bearables line also includes a range of sensors - perhaps I could fake a sensor and see what that did? After shoving 3.3v and Gnd down the sensor connections without much luck, I tried just shorting out the pins. This worked, kind of: once the badge was in sensor mode, you could sort-of-ish make stuff happen by shorting the lines. But, there seemed to be an erratic time delay between the connection being made and a change being seen, so it wasn't going to work for a new pattern.

There's only really one other interface on the badge: the button for changing modes/patterns. I noticed whilst poking around that if you spam it fast enough, it just interrupts the current pattern, instead of changing it to the next one along. To test this theory out, the switch was brutally removed from the badge, and the pads hooked up to an NPN transistor, with the base hooked up to the Pi again. I then wrote some very quick and dirty code (see below) to pulse the line as fast as possible. This had a pretty cool effect - it mostly made some rapidly flashing variants of the current pattern, but when it was on the chasing LEDs pattern you could get it to do almost single LED control. I had a new pattern!

> [@pimoroni](https://twitter.com/pimoroni?ref_src=twsrc%5Etfw) here you go. 
> 
> I must be completely honest, I didn't use the intended method, but it does in fact work! [pic.twitter.com/GIgzPtAFjj](https://t.co/GIgzPtAFjj)
> 
> -- Archie Roques (@archieroques) [November 17, 2017](https://twitter.com/archieroques/status/931588907216654337?ref_src=twsrc%5Etfw)

> You've earned yourself a bear badge at the very least, Archie. You can upgrade to the pHAT Stack with a "correct" solution. <https://t.co/j7e543Bm6T>
> 
> -- pimoroni (@pimoroni) [November 17, 2017](https://twitter.com/pimoroni/status/931597570215948288?ref_src=twsrc%5Etfw)

The offending code:
    
    
    from gpiozero import LED
    from time import sleep
    l = LED(3) 
    x = 0.01
    y = 0.002
    while True:
    l.on()
    sleep(x)
    l.off()
    sleep(y)
    

I was all chuffed with myself and ready to have a nice, relaxing evening. And I did, for a bit. Until Team Underwood came along with their I2C knowledge and properly formatted code….

> We've done it! (We = my husband Phil) [#bearableshack](https://twitter.com/hashtag/bearableshack?src=hash&ref_src=twsrc%5Etfw) [@pimoroni](https://twitter.com/pimoroni?ref_src=twsrc%5Etfw) New pattern coming next [pic.twitter.com/XPbGpIjQCx](https://t.co/XPbGpIjQCx)
> 
> -- Lorraine Underwood (@LMcUnderwood) [November 17, 2017](https://twitter.com/LMcUnderwood/status/931664791424458752?ref_src=twsrc%5Etfw)

And, what's more, the Underwood method uses the actual intended method - I was quite close to begin with! If only I'd read up on my `smbus` eh… Their very proper code is [online](https://gist.github.com/furbrain/0c5b92ca01264ecc25700dce4a9eb946), which meant there was an opportunity for more hacking!

Over the course of the night (and early next morning) I produced….

> -- Archie Roques (@archieroques) [November 18, 2017](https://twitter.com/archieroques/status/931679827307958272?ref_src=twsrc%5Etfw)

> Get this… It's Bearablompass! Never before has there been a more cute but less useful way of measuring degrees of rotation. [pic.twitter.com/SggTNusaGN](https://t.co/SggTNusaGN)
> 
> -- Archie Roques (@archieroques) [November 18, 2017](https://twitter.com/archieroques/status/931686996187152384?ref_src=twsrc%5Etfw)

> And now, for my final masterpiece of the day, I present the world's most broken binary clock. So bad but so good. [pic.twitter.com/dx8g972Mlm](https://t.co/dx8g972Mlm)
> 
> -- Archie Roques (@archieroques) [November 18, 2017](https://twitter.com/archieroques/status/931694508655431681?ref_src=twsrc%5Etfw)

Amazing what you can achieve with a little badge! And it's really easy once someone else has written the code for you (thanks team Underwood!) If you haven't got one, get one (just for the cuteness factor!) and have a go at programming it.

I quite fancy trying to write some firmware for a little ATTiny microcontroller that can be bodged onto the back of the badge…. maybe in the future.
