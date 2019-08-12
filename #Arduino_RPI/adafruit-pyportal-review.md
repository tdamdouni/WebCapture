# Adafruit PyPortal review

_Captured: 2019-05-02 at 07:33 from [hackspace.raspberrypi.org](https://hackspace.raspberrypi.org/features/adafruit-pyportal-review?utm_source=Raspberry+Pi+Press+Newsletter&utm_campaign=8a24c4c8a7-HS_RSS_WEEKLY&utm_medium=email&utm_term=0_e2ce89f288-8a24c4c8a7-495298587&mc_cid=8a24c4c8a7&mc_eid=9b04ee1c98)_

![](https://images.ctfassets.net/q092pc69zo4z/2aeN9nHMFGHQLirGn8ZLH1/6d3571efbbc118e3a18c2345e38c8b68/pyportal4.jpg)

The Adafruit PyPortal combines a 320×240 colour TFT display with a Cortex-M4 processor and an ESP32 WiFi module to create a web-based display programmable in CircuitPython or Arduino.

The most basic use of the PyPortal is as an information display. The CircuitPython library includes the ability to do this almost automatically. Feed in your WiFi credentials, the URL of the data (in JSON format), and the bit of data you want to extract. Pair this with a background image and the location on the screen you want the text to appear, and you've got your Internet of Things display. Adafruit has guides using this basic formula to display stats for social media (such as YouTube subscriber counts or Reddit viewership), environmental data such as air quality, and text via a quote of the day.

![Issue 18 cover](https://magazines-static.raspberrypi.org/issues/cover_images/000/000/072/original/HS_18_Cover_Web.jpg?1555569246)

Of course, you don't have to use the PyPortal like this. It's completely customisable - and compatible with the displayio CircuitPython library, which allows you to easily place text and graphics at different points on the screen. At the moment, performance isn't great - of the order of two or three frames per second, so animations aren't going to be smooth, but perfectly fine for static images and slowly changing text. The hardware is capable of much more than this, and it's currently slowed down by the CircuitPython libraries (which should hopefully see a speed boost in future versions). If you need animations, there's Arduino support, where we were able to get >20 fps on animations (take a look at the graphics demos here for examples: [hsmag.cc/jHheml](https://hsmag.cc/jHheml)).

If your main exposure to touchscreens is using phones, you need to be aware of the technology here. It's a 320×240 pixel 3.2-inch display with resistive touch. This has 125 pixels per inch (PPI). The iPhone X has 458 PPI, and other modern phones are similar - of course, they're also a lot more expensive and a lot less hackable. For text and simple graphics, the PyPortal works well. For photographs and highly detailed images, you're probably going to struggle. Similarly, the resistive touchscreen on the PyPortal works well for simple finger taps, but doesn't have the sensitivity of high-end capacitive touch displays.

![pyportal1](https://images.ctfassets.net/q092pc69zo4z/2hRMsX0no8d2YSEIwDvMGE/ad41e65356096d0112576f8e37886125/pyportal1.jpg)

> _pyportal1_

A built-in speaker and connections make it easy to give your projects audio, as well as visual, output. There's also an on-board temperature sensor (though the display can warm the whole board up a little), and an ambient light sensor which could be used to change the brightness of the display based on the conditions.

You can interact with extra hardware via an I2C bus (5 V, but can be converted to 3 V with a cuttable trace) and two digital IO/analogue-in pins, all of which are in Grove-compatible connectors.

## User experience

For a web-based data display, the out-of-the-box experience with PyPortal is brilliant. Grab one of the examples (such as the Reddit subscriber count here: hsmag.cc/kToalq), change the JSON source, the background image and caption, and you've got an internet counter. The range of examples has grown significantly between when we started reviewing the PyPortal and when we went to press. If you're already moderately familiar with Python and JSON, you can probably get something working in under half an hour.

Going further in CircuitPython can be a bit tricky at the moment. The displayio module is new in CircuitPython 4, and the documentation is still catching up. That said, there are some examples out there that show how to use it - take a look at the weather display example, particularly the openweather_graphics.py file or the HalloWing Magic 9 Ball example (hsmag.cc/SISvKr), for details. The basic idea is that the displayio root contains a list of nodes. Each node can be either a thing to be drawn or another list. These things are then drawn in the order they are in the list (so things go over or under each other in this order). You can add text or graphics in this way, and manipulating them automatically updates the display. Of course, things are improving all the time, and when you read this, there may be more information available.

![pyportal2](https://images.ctfassets.net/q092pc69zo4z/6251OmlHRwPpy0jbnxWCWp/7c2bd3a54e9270899fad360beac0f154/pyportal2.jpg)

> _pyportal2_

Using Arduino, the path is a bit more well-trodden. The ILI9341 chip that drives the display has a well-tested Arduino library that works with the classic GFX library.  
The Cortex-M4 processor is very heavyweight for such a product, especially as the data connection is handled by the ESP32. CircuitPython is getting faster all the time, but it's still a bit of a resource hog, so having this power gives you the space to do a reasonable amount of processing. If you use Arduino, rather than CircuitPython, then you've really got a lot of processing power to play with.

You do have access to the programming pins on the ESP32, so in principle you could do more with the processor it has if you want to, whether this is more processing of the data flowing in and out, or activating some of its other features such as Bluetooth.  
Overall, the PyPortal is a great one-piece solution to displaying internet data. It's got powerful hardware, is easily expandable, easy to program, and is great value for money.

**Adafruit From $54.95 [adafruit.com](https://adafruit.com)**

## Verdict

The best hackable out-of-the-box IoT display available at the moment.

## 9/10
