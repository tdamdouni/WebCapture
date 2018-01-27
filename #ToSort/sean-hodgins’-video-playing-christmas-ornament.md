# Sean Hodgins’ video-playing Christmas ornament

_Captured: 2017-12-09 at 12:45 from [www.raspberrypi.org](https://www.raspberrypi.org/blog/sean-hodgins-ornament/)_

Standard Christmas tree ornaments are just so boring, always hanging there doing nothing. Yawn! Lucky for us, [Sean Hodgins](https://twitter.com/idlehandsdev) has created an ornament that plays classic nineties Christmas adverts, because of nostalgia.

## Ingredients

Sean first 3D printed a small CRT-shaped ornament resembling the family television set in _The Simpsons_. He then got to work on the rest of the components.

![Pi Zero and electronic components — Sean Hodgins Raspberry Pi Christmas ornament](https://www.raspberrypi.org/app/uploads/2017/12/FF44OK9JAWTS3BQ.MEDIUM.jpg)

> _All images featured in this blog post are c/o Sean Hodgins. Thanks, Sean!_

The ornament uses a [Raspberry Pi Zero W](https://www.raspberrypi.org/products/raspberry-pi-zero-w/), 2.2″ TFT LCD screen, Mono Amp, LiPo battery, and speaker, plus the usual peripherals. Sean purposely assembled it with jumper wires and tape, so that he can reuse the components for another project after the festive season.

![Clip of PowerBoost 1000 LiPo charger — Sean Hodgins Raspberry Pi Christmas ornament](https://www.raspberrypi.org/app/uploads/2017/12/FZPYR01JAWTS3FN.ANIMATED.MEDIUM.gif)

> _Sean Hodgins Raspberry Pi Christmas ornament_

By adding header pins to a PowerBoost 1000 LiPo charger, Sean was able to connect a switch to control the Pi's power usage. This method is handy if you want to seal your Pi in a casing that blocks access to the power leads. From there, jumper wires connect the audio amplifier, LCD screen, and PowerBoost to the Zero W.

## Code

Then, with Raspbian installed to an SD card and SSH enabled on the Zero W, Sean got the screen to work. The type of screen he used has both SPI and FBTFT enabled. And his next step was to set up the audio functionality with the help of an [Adafruit tutorial](https://learn.adafruit.com/adafruit-max98357-i2s-class-d-mono-amp/raspberry-pi-usage).

![Clip demoing Sean Hodgins Raspberry Pi Christmas ornament](https://www.raspberrypi.org/app/uploads/2017/12/FOV10CJJAWTS47G.ANIMATED.MEDIUM.gif)

> _Sean Hodgins Raspberry Pi Christmas ornament_

For video playback, Sean installed mplayer before writing a program to extract video content from YouTube*. Once extracted, the video files are saved to the Raspberry Pi, allowing for seamless playback on the screen.

## Construct

When fully assembled, the entire build fit snugly within the 3D-printed television set. And as a final touch, Sean added the cut-out lens of a rectangular magnifying glass to give the display the look of a curved CRT screen.

![Clip of completed Sean Hodgins Raspberry Pi Christmas ornament in a tree](https://www.raspberrypi.org/app/uploads/2017/12/F2B5GFKJAWTS586.ANIMATED.MEDIUM.gif)

> _Sean Hodgins Raspberry Pi Christmas ornament_

Then finally, the ornament hangs perfectly on the Christmas tree, up and running and spreading nostalgic warmth.

For more information on the build, check out the [Instructables](https://www.instructables.com/id/YouTube-Christmas-Ornament/) tutorial. And to see all of Sean's builds, subscribe to [his YouTube channel](https://www.youtube.com/channel/UCE-bw6PRKuDlH6fP1mP4nOw).

## Make

If you're looking for similar projects, have a look at [this tutorial by Cabe Atwell](https://www.element14.com/community/community/raspberry-pi/raspberrypi_projects/blog/2017/12/01/project-raspberry-pi-iot-ornament-texter-get-holiday-messages-on-your-tree) for building a Pi-powered ornament that receives and displays text messages.

Have you created Raspberry Pi tree ornaments? Maybe you've [3D printed some of our own](https://www.raspberrypi.org/blog/alexs-festive-baubles/)? We'd love to see what you're doing with a Raspberry Pi this festive season, so make sure to share your projects with us, either in the comments below or via our [social media channels](https://www.raspberrypi.org/blog/connecting-raspberry-pi-social/).

_*At this point, I should note that we don't support the extraction of video content from YouTube for your own use if you do not have the right permissions. However, since Sean's device can play back any video, we think it would look great on your tree showing your own family videos from previous years. So, y'know, be good, be legal, and be festive._
