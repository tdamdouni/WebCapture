# Pan-Tilt HAT review

_Captured: 2017-05-25 at 13:44 from [www.raspberrypi.org](https://www.raspberrypi.org/magpi/pan-tilt-hat-review/)_

![](https://www.raspberrypi.org/magpi/wp-content/uploads/2017/02/Pan-Tilt_HAT_5_of_5_1024x1024-2.jpg)

> _The Raspberry Pi Camera Module is one of the best accessories you can get, enabling cheap photography on the Pi. But it doesn't sit upright on its own - a stand is required._

[Pan-Tilt HAT](https://shop.pimoroni.com/products/pan-tilt-hat) fulfils this function and a whole lot more. The Camera Module is mounted on the end of a robotic arm that sits on top of the HAT. Thanks to the arm's horizontal and vertical joints, the camera can be angled precisely by the two servo motors.

_The full article can be found in [The MagPi 54](https://www.raspberrypi.org/magpi/issues/magpi/54) and was written by Lucy Hattersley._

The finished effect is adorably cute, instantly imbuing your Raspberry Pi with personality as it looks around the room.

It's really useful too. You could set the Pan-Tilt HAT up to monitor a room, and then use VNC or SSH to adjust its viewing position remotely.

Alternatively, you can set up a Raspberry Pi with face-tracking software and connect it to the Pan-Tilt HAT. Pimoroni, the HAT's makers, also suggest mounting it on top of a robot for a set of eyes.

### Setting it up

First, you have to set the HAT up. Fortunately, there is an [online setup guide](https://learn.pimoroni.com/tutorial/sandyj/assembling-pan-tilt-hat).

The board has a GPIO connection on one side, and servo connections on the other. The two sets of cables on the arm are connected to Servo 1 and Servo 2 on the board (1 for pan, 2 for tilt). A third servo channel can be used to control an optional NeoPixel strip for lighting.

### Camera control

You can download all of the code from Pimoroni's [GitHub page](https://github.com/pimoroni/pantilt-hat). You need to install the pantilthat module to access the controls.

After importing the pantilthat library in Python, you use pan() and tilt() methods to change the camera position. These accept any value between -90 and 90. To set the camera straight forward, for example, you would use:

To look up by 45 degrees, use:

To look all the way to the camera's left, you'd put:

We would have dearly loved more software examples. There are ones for motion and NeoPixels, but none for recording from the camera or face-tracking. A few more sample programs and it'd be perfect.  
Even so, we had a lot of fun setting up the Pan-Tilt HAT and look forward to researching and coding a face-tracking program.

### Last word

4/5

A highly enjoyable and extremely cute accessory. With a bit of research, you should be able to create some fun things with it.
