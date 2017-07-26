# Hardware Fundamentals: what exactly is a microcontroller?

_Captured: 2017-04-26 at 09:14 from [medium.freecodecamp.com](https://medium.freecodecamp.com/hardware-fundamentals-what-exactly-is-a-microcontroller-8a502a3650dc?source=userActivityShare-c79006fee040-1493190841)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*WKKNCMKqg6yEkowj28CHng.jpeg?q=20)![](https://cdn-images-1.medium.com/max/2000/1*WKKNCMKqg6yEkowj28CHng.jpeg)

At the fundamental level, a microcontroller is a just tiny computer.

Being a "tiny computer" doesn't really tell us much, though. So let's go deeper. Many people associate microcontrollers with Arduino. But it's important to point out that **Arduino is not a microcontroller**. Arduino is a complete platform which spans across software and hardware.

Arduino makes devices like the [Arduino Uno](https://www.arduino.cc/en/Main/arduinoBoardUno):

The Arduino Uno is not a microcontroller, either. It's a breakout board based on the [Atmel ATmega328P microcontroller](http://www.microchip.com/wwwproducts/en/ATmega328P).

Here is what the Atmel microcontroller looks like:

If you were to have just the Atmel microcontroller in hand, as a beginner, it wouldn't be very useful. This is where the breakout board comes in.

The breakout board "breaks out" the pins on the microcontroller into a larger device (like the Arduino Uno). This larger device makes the microcontroller easier to use.

For the Arduino Uno, the breakout board gives you the ability to insert a USB cord, give it power, program the device, and more.

Without the breakout board, for a beginner, this would be a daunting task. This problem is the very reason that Arduino exists -- to make it super easy for you to learn about hardware.

### Ah, So it's like the Raspberry Pi?

Well, not entirely. Both the Arduino and the Raspberry Pi are still computers by definition. But the Raspberry Pi is considered a [single-board computer](http://maxembedded.com/2013/07/introduction-to-single-board-computing/). A single-board computer is [a full computer built on a single circuit board](https://en.wikipedia.org/wiki/Single-board_computer).

Your laptop is also technically a single-board computer -- just a powerful one. The Raspberry Pi is a simple version of the same hardware in your laptop. Just as your laptop runs an operating system (Windows, Mac, or Linux), the Raspberry Pi runs a Linux operating system.

Now, back to Microcontrollers. Microcontrollers can't run an operating system. Microcontrollers also don't have the same amount of computing power or resources as most single-board computers.

A microcontroller will run just one program repeatedly -- not a full operating system. We can see this in Arduino programs because they only need two functions: `Setup` and `loop`. `Setup` will run once and `loop` will run indefinitely.

### So, what's a microcontroller?

A microcontroller is a small computer with low-memory and programmable input/output peripherals.

#### Inputs/Outputs

As you probably know, everything with a computer eventually starts with binary (0 or 1).

An input means that the microcontroller will read binary. An example input would be a sensor.

An output means that the microcontroller will send binary. An example output would be to control a motor or LED.

### Why do we need microcontrollers?

Well, these were "computers" before we arrived at the idea of the computers you know today. Microcontrollers stuck around because some computing tasks are incredibly trivial and require simple logic. For example, flipping a switch or controlling small components -- like a LED light -- don't require the same resources we need for day-to-day tasks like sending an email.

We use them today because their low-powered and low memory makes them low-cost. Microcontrollers are part of the reason the [Internet of Things](https://en.wikipedia.org/wiki/Internet_of_things) is possible and successful today.

### How do I get one?

Which microcontroller you'll want to get depends on which problem you want to solve. If you are doing something simple -- turning things on and off, or reading a sensor -- pretty much any microcontroller will do.

If you want to play games or have more complex ideas, you'll need more compute power, so you'll need to move up to single-board computers, like the Raspberry Pi.

[Adafruit](https://www.adafruit.com/) and [Sparkfun](https://www.sparkfun.com/) both have TONS of kits and hardware that are all amazing. You can also make use of their tutorials.

[Losant](https://losant.com) also has some cool [kits](https://docs.losant.com/getting-started/losant-iot-dev-kits/builder-kit/) available. You could build your own [door sensor](https://docs.losant.com/getting-started/losant-iot-dev-kits/door-sensor-kit/) -- to be notified when a door is left open for too long.

If you don't have a specific problem you want to solve, just grab some hardware and play around with it.

Here are some things you can buy to get started:

The [NodeMCU](http://amzn.to/2p3YDEu) is a board based on the ESP8266 microcontroller. This board is special because it's cheap and WiFi enabled. It will only run you about $8.79 on Amazon and is even less on Ebay.

Not all microcontrollers are WiFi-enabled. The fact that this one is opens the door to a number of projects you can build with this device. For example, you can collect data and send it to the cloud ☁️.
