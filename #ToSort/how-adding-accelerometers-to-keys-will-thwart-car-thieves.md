# How Adding Accelerometers to Keys Will Thwart Car Thieves

_Captured: 2017-11-21 at 10:08 from [spectrum.ieee.org](https://spectrum.ieee.org/view-from-the-valley/transportation/sensors/how-accelerometers-will-soon-thwart-car-thieves)_

![Magazine Cover](https://spectrum.ieee.org/image/Mjk3MzE0NA.jpeg)

![Illustration with a blue background, showing a car key and a keyless entry clicker, where one button has been replaced with a symbol indicating an accelerometer.](https://spectrum.ieee.org/image/Mjk4MDQ3Ng.jpeg)

> _Illustration: iStockphoto_

During last week's [MEMS and Sensors Executive Congress](http://www.semi.org/en/mems-sensors-executive-congress-2017) in San Jose, Calif., designers, researchers, and industry representatives argued for putting MEMS devices, like accelerometers and microphones, and a wide variety of other sensors in just about everything. We heard about an [electric snowboard](https://www.leiftech.com/) with traction control, voice-controlled garbage cans, and accelerometers placed on the nose to listen for speech in noisy environments.

But sometimes the simplest example is the most memorable. In this case, that was a MEMS accelerometer--like the one in your step-counter--that thwarts car thieves.

[Lars Reger](https://www.linkedin.com/in/larsreger/), chief technology officer for NXP's automotive division, said that passive keyless entry (PKE) systems can be made more secure with an inexpensive accelerometer. PKE systems unlock a car--and allow it to start with a button push--by recognizing when the "key" is close to the car, either right next to it or inside of it. This is convenient for drivers, who don't have to remove the key from a pocket or purse. But PKEs are ridiculously easy to hack--at least when a car is sitting in a driveway and the owner is at home.

The hack, demoed by Swiss researchers in 2011 and still being used by car thieves around the world today, works because most people toss car keys in a basket or on a counter fairly close to their front door--close enough that a thief with a radio outside can pick up signals from the key. An accomplice with another radio stands near the front door of the car to pick up signals from the key and transmit those signals to the car. The system, concluding that the key is nearby, unlocks the car.

Earlier this year, researchers pulled off the hack with US $22 worth of gear in a demo at a security conference [reported in _Wired_](https://www.wired.com/2017/04/just-pair-11-radio-gadgets-can-steal-car/). The team suggested that changing the timing of the calls and responses from the car and key could address the problem. In the meantime, PKE key holders were advised to keep their car keys in their refrigerators, whose metal exteriors would block the key's signals.

NXP has another solution (and, of course, the company is bringing it to market soon, which is why representatives are willing to talk about it). Business development manager [Marc Osajda](https://www.linkedin.com/in/marc-osajda-73aa984/) told me that NXP had initially been working on a mechanical switch to turn the radio in the PKE key on and off. Then, after the company merged with Freescale Semiconductor in 2015, engineers at Freescale made the case for using a MEMS device instead, arguing that its lower power consumption made it a good fit for a gadget with an expected battery life of a year or more.

Enter the accelerometer. The 50-cent component works on the assumption that if your PKE key has been sitting in one place for a while, you aren't going anywhere, so it can turn off its radio and the microcontroller that was listening to the car's radio; it will turn back on as soon as you pick it up. Osajda said that instead of reducing battery life, putting an accelerometer in the PKE key ends up extending battery life, because the accelerometer uses far less power than the parts it is allowing the key to turn off.

It wasn't all that simple, of course, Osajda says, mostly because car keys take a lot more abuse than wrist wearables. He pointed out that people frequently drop their keys (sometimes even out of second story windows onto concrete) or toss them into washing machines (not a surprise for keys designed to stay in your pocket).

NXP's MEMS switch is going into production within the next few weeks, Osajda said, and will be incorporated into PKE keys from a variety of manufacturers during 2018.

In the meantime, keep your eye out for familiar MEMS and other sensors turning up in unfamiliar places. This trend is only beginning.
