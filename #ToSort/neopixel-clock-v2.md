# Neopixel Clock, V2

_Captured: 2017-12-29 at 05:55 from [zweben.org](http://zweben.org/2017/12/06/neopixel-clock-v2/)_

<span data-mce-type="bookmark" style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" class="mce_SELRES_start"> </span>

## Idea

After building my [first Neopixel Clock](http://zweben.org/2017/12/03/neopixel-clock-v1/), I decided I needed one for myself. There was no way I was going to solder 90 lengths of wire onto 180 tiny pads again, though, so I knew I needed to design a custom PCB. This necessitated a redesign of the entire clock, focused around making it as easy as possible to assemble.

## Design

Having been unsatisfied with Kicad the last time I designed a PCB, I looked for new options, and found EasyEDA. They are a PCB design web app plus manufacturing service all in one. I found the web app to work quite nicely for my needs, and their PCBs were both high quality and cheap, so I'm happy with them so far.

![](https://i2.wp.com/zweben.org/wp-content/uploads/2017/12/IMG_0379.jpg?w=2250)

> _Custom PCB populated with Neopixel strip segments_

![](https://i2.wp.com/zweben.org/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-7.58.24-PM.png?w=782)

> _Digit diffuser in CAD_

To minimize the cost and the size of the finished product, I designed a single circuit board that could hold Neopixel strips in a 7-segment arrangement, plus all of the electronics needed to drive the clock. Each digit uses the same circuit board, with the holes for the microcontroller and clock module left unpopulated in all but the first digit. Power and data come in from the left and exit out the right.

After designing the circuit boards, I designed a new light diffuser around the board shape. The circuit board slides and snaps in from the back of the diffuser, forming a separate enclosure around each of the seven Neopixel strip segments. Each digit is a separate 3D print measuring 76mm wide by 120mm tall.

## Hardware

Like the previous version, the clock is powered by an Arduino Pro Mini clone (purchased from eBay). It communicates with a DS3231 Real Time Clock module (also from eBay) via I2C. Power comes over USB, via a micro USB breakout board (eBay). The Neopixel strips (from Amazon) are 60-per-meter WS2812B LEDs. There are two LEDs per digit segment, for a total of 14 on each digit and 58 individually-addressable lights on the entire clock.

## Software

The software (full source code and download link below) was reused from my original Neopixel clock. I updated the arrays to fit a clock with a different number and arrangement of pixels, and it worked straight away.

## Result

![IMG_0368](https://i1.wp.com/zweben.org/wp-content/uploads/2017/12/IMG_0368.jpg?w=348&h=261&crop)

![IMG_0370 2](https://i1.wp.com/zweben.org/wp-content/uploads/2017/12/IMG_0370-2.jpg?w=348&h=261&crop)

> _IMG_0370 2_

![IMG_0373](https://i0.wp.com/zweben.org/wp-content/uploads/2017/12/IMG_0373.jpg?w=394&h=526&crop)

## Downloads

## Code

```

```
## Copyright

All files should be considered [Creative Commons 3.0 non-commercial](https://creativecommons.org/licenses/by-nc/3.0/us/) licensed.
