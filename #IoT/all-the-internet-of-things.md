# All the (Internet of) Things

_Captured: 2018-05-15 at 21:44 from [news.codecademy.com](https://news.codecademy.com/internet-of-things/?utm_source=Adafruit+Products+Newsletter&utm_campaign=aed5ae975b-EMAIL_CAMPAIGN_2018_05_15&utm_medium=email&utm_term=0_f5693aed98-aed5ae975b-114333953)_

![](https://news.codecademy.com/content/images/2018/04/internet-of-things.gif)

_Limor "Ladyada" Fried is the founder and CEO of [Adafruit Industries](https://www.adafruit.com), an open-source hardware company. A founding member of the NYC Industrial Business Advisory Council, she was named a [White House Champion of Change](https://blog.adafruit.com/2016/06/10/whitehouse-white-house-to-recognize-champions-of-change-for-making-limor-ladyada-fried/) in 2016._

The Internet of Things is all about connections--connecting your electronics design, product, or project to the wider world. We start with the idea that you have a "Thing" that you want to connect to the "Internet of."

How do you do that? Usually you start with something you'd like to improve. Say you love fish and have a home or school aquarium. Since you've got some really fancy fish, they need the water temperature to stay between 20 and 30 degrees Centigrade. You could always check the water temperature, but it would be better if you had a microcontroller to help you out!

You could start with a simple temperature manager, but even better would be one that could email or text you to let you know if something went amiss and maybe the heater broke. **That's what the Internet of Things is all about: Making stuff smart!**

Your browser does not support the video tag. 

A Bluetooth-enabled [Adafruit board](https://www.adafruit.com/product/3406?utm_source=codecademyblog).

## What is Adafruit?

I design that "smart stuff"--the electronics and code for makers who make real things in the real world. We also teach them how to make their ideas come to life. Some are simple projects, like getting an alert if there is water in your basement. Others are getting real-time information like transit schedules and [displaying it at home so you know when your bus is coming](https://learn.adafruit.com/nextbus-transit-clock-for-raspberry-pi?utm_source=codecademyblog).

Some of our favorite IoT projects are ones that make life easier for people who need Accessibility Technology (AT). For example, a project from our friend Chris Young, who not only uses AT but designs it, for people who have the same needs he does! He has written up [how to make an IoT remote control](https://learn.adafruit.com/internet-of-things-infrared-remote?utm_source=codecademyblog) so he can use a laptop or tablet with touchscreen to turn on/off devices in his house.

What we think is the most exciting part of IoT's future is seeing makers and coders design the devices that best suit _them_ and their community. Instead of relying on what's available in the store, customization and optimizations will let small-scale engineering happen by the people who will actually use it!

We made an internet of things service called "[adafruit.io"](http://adafruit.io/?utm_source=codecademyblog) that gets you started quick and easy, so your things can spend more time on the internet, not just trying to get going.

## The best language for IoT

Here at Adafruit, we like using [Python](https://www.codecademy.com/learn/learn-python?utm_source=ccblog&utm_medium=blog&utm_campaign=publication&utm_content=Adafruit) to program IoT devices. What, a snake? Close! The Python programming language is the [fastest-growing programming language](http://news.codecademy.com/why-learn-python/?utm_source=ccblog&utm_medium=blog&utm_campaign=publication&utm_content=Adafruit) that beginners and experts alike use. Python is great for IoT for a lot of reasons.

IoT is all about getting and sending data. Maybe you want your aquarium to let you know when the temperature is too high or too low. You could code this up in Python using an `if` conditional:

` water_temp = aquarium_temperature() # read the sensor if water_temp > 30: send_text_message("Help! The water in the aquarium is too hot!") if water_temp < 20: send_text_message("Oh no! The water in the aquarium is too cold!") `

Even simple examples such as the above are super powerful when you add the Internet, email, cellular and text messages so that your programming can reach outside your screen.

## Why Python and IoT?

Why is Python so great for IoT? First, of course, is how popular it is--it's available for any and all computers. It's also really great for parsing text, in particular the "structured data in text" that the Internet runs on, often referred to as HTML, XML or JSON. Other languages may be faster in some ways, but they often struggle to do regular expressions, text parsing or moving from one data format to another.

Python has flexible memory management, so you don't have to worry about pointers or memory. This comes at a cost to speed, but helps avoid some of the ickiest security problems that plague IoT devices. You definitely don't want to accidentally turn your smart aquarium into a botnet!

Python also has exception handling, which is a "proper" way to handle errors compared to some languages. Whenever you expose your devices to the Internet, you'll have inconsistent connections (e.g., "the WiFi is down!") or unexpected data sent your way. Exceptions mean that even if you are a little lazy and forget to check a value or function output, your program will be more likely halt rather than blithely continue with incorrect instructions.

And of course, Python comes with the kitchen sink--so much is included already, so you can get started faster than ever. Not only is Python available on computers like your desktop or laptop, it also comes on embedded computers like the [Raspberry Pi](https://www.raspberrypi.org/?utm_source=codecademyblog) and on microcontrollers as [Circuit Python](https://learn.adafruit.com/welcome-to-circuitpython/what-is-circuitpython?utm_source=codecademyblog).

Learning Python is a great way to make internet-connected things, and to share data and creativity around the world. Cuddle up to this friendly snake and check out [learn.adafruit.com](https://learn.adafruit.com?utm_source=codecademyblog) for thousands of free IoT projects you can build with Python!

## Where anyone can get the skills they need for the jobs they want.
