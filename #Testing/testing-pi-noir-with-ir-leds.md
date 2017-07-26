# Testing Pi NoIR with IR LEDs

_Captured: 2017-06-02 at 01:33 from [www.element14.com](https://www.element14.com/community/community/raspberry-pi/raspberrypi_projects/blog/2014/01/24/pi-noir-with-ir-leds)_

When I got my Pi NoIR camera, I didn't have any IR LEDs to play with, so instead I used my TV's remote control for testing ([Road Test review](https://www.element14.com/community/external-link.jspa?url=%2FroadTestReviews%2Fhttp%3A%2F%2Fwww.element14.com%2Fcommunity%2FroadTestReviews%2F1638)).

This was enough to demonstrate the functionality of the Pi NoIR, but it wasn't a permanent solution.

In the mean time, I managed to get my hands on a couple of IR LEDs.

The voltage drop across the IR LEDs I got is approx. 1,5V for a current rating of 60mA, meaning that with a 5V power supply I could put a resistor and 3 LEDs in series.

The resistor's value would have to be approx. 8 ohms (0,5V / 0,060A), but the closest resistor value I had lying around was 10 ohms.

I ended up with following circuit of two times three LEDs, in order to place three LEDs on each side of the camera board:

![Screen Shot 2014-01-24 at 19.42.13.png](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191670/Screen+Shot+2014-01-24+at+19.42.13.png)

I downloaded a camera holder that I found on thingiverse ([Raspberry Pi Camera Holder by gryphius - Thingiverse](https://www.element14.com/community/external-link.jspa?url=http%3A%2F%2Fwww.thingiverse.com%2Fthing%3A92155)), modified it in Sketchup to be able to hold the LEDs and printed it.

![photo 1.JPG](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191679/312-418/photo+1.JPG)

![photo 2.JPG](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191680/312-418/photo+2.JPG)

![photo 3.JPG](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191681/313-419/photo+3.JPG)

![photo 4.JPG](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191682/313-419/photo+4.JPG)

The circuit was powered with a separate 5V supply for this test, but ideally I'd like to power this from the pi itself.

Perhaps someone knows if it's ok to use the 5V/GND pins on the GPIOs to do this ? I'll have to look into this ...

With the LEDs powered, and the Pi NoIR running, it was time to take pictures and videos in the dark.

These are the results (at night, with all lights turned off except for power switches, etc ...):

![test.jpg](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191687/1200-900/test.jpg)

![test2.jpg](https://www.element14.com/community/servlet/JiveServlet/downloadImage/38-14761-191688/1200-900/test2.jpg)

Play Video

Play

Mute

Current Time 0:00

/

Duration Time 0:00

Loaded: 0%

0:00

Progress: 0%

0:00

Progress: 0%

Stream TypeLIVE

Remaining Time -0:00

Playback Rate

1

  * Chapters

Chapters

  * descriptions off, selected

Descriptions

  * subtitles off, selected

Subtitles

  * captions settings, opens captions settings dialog
  * captions off, selected

Captions

Audio Track

Fullscreen

This is a modal window.

Caption Settings Dialog

Beginning of dialog window. Escape will cancel and close the window.

TextColorWhiteBlackRedGreenBlueYellowMagentaCyanTransparencyOpaqueSemi-TransparentBackgroundColorBlackWhiteRedGreenBlueYellowMagentaCyanTransparencyOpaqueSemi-TransparentTransparentWindowColorBlackWhiteRedGreenBlueYellowMagentaCyanTransparencyTransparentSemi-TransparentOpaque

Font Size50%75%100%125%150%175%200%300%400%

Text Edge StyleNoneRaisedDepressedUniformDropshadow

Font FamilyProportional Sans-SerifMonospace Sans-SerifProportional SerifMonospace SerifCasualScriptSmall Caps

DefaultsDone

The raspivid utility saves .h264 format files. Some programs need this in a .mp4 wrapper to use, which you can do in several ways. One is to use "MP4Box" which is in the 'gpac' package.

Using these IR LEDs, I was able to light the room up to 1.5 to 2m away with a limited field of vision.

Perhaps I should try some high power IR LEDs and compare the results, but that will be for next time

![180114_162146 \(Small\).jpg](https://www.element14.com/community/servlet/JiveServlet/downloadImage/105-30448-191755/180114_162146+%28Small%29.jpg)

![DSC_3265 \(Medium\).JPG](https://www.element14.com/community/servlet/JiveServlet/downloadImage/105-30515-191811/DSC_3265+%28Medium%29.JPG)
