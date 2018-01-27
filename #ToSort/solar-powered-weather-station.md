# Solar Powered Weather Station

_Captured: 2017-11-26 at 20:08 from [www.instructables.com](http://www.instructables.com/id/Solar-Powered-Weather-Station/)_

![](https://cdn.instructables.com/FZO/KRJZ/J3YQAM2H/FZOKRJZJ3YQAM2H.MEDIUM.jpg)

Welcome to my solar powered weather station!

My objective was to build a self sustaining and wireless weather station, let me know what you think of it.

## Step 1: Introduction

Hello, I am Thiemo Seys a 20 year old student at Howest NMCT located in Kortrijk. For a course we had to make a big project combining all the subject material we had learned during the year. When we had to choose a project i wasn't quite sure what i would take, but eventually i ended up picking a weather station.

When I began thinking about the project i decided to make it solar powered, this has several advantages such as no need to replace batteries and being better for the environment. An other important part of the project is the wireless communication between the raspberry pi and the arduino. If you want to find out how to build the weather station, continue reading the next steps!

## Step 2: The Parts of the Build!

![](https://cdn.instructables.com/FF3/3BG0/J3YQAMBF/FF33BG0J3YQAMBF.MEDIUM.jpg)

![](https://cdn.instructables.com/FOM/EUGX/J3YQAMCQ/FOMEUGXJ3YQAMCQ.SMALL.jpg)

![](https://cdn.instructables.com/FVJ/W525/J3YQAMDV/FVJW525J3YQAMDV.MEDIUM.jpg)

![](https://cdn.instructables.com/FBU/WR0Y/J3YQAMF7/FBUWR0YJ3YQAMF7.SMALL.jpg)

![](https://cdn.instructables.com/F3L/GI15/J3YQAMGI/F3LGI15J3YQAMGI.SMALL.jpg)

![](https://cdn.instructables.com/F11/I8DL/J3YQAMHX/F11I8DLJ3YQAMHX.SMALL.jpg)

First let's by getting the required parts. I recommend ordering the parts from Aliexpress if you have the time to wait. Shipping can take a rather long amount of time. The second but more expensive option is shopping locally or ordering on Amazon, both options will get you the parts faster but at a higher price.

You can find the prices i paid for it in the included Bill Of Materials file! The cost without having anything is around 100 euro -120 euro. If you already have a raspberry pi it is about 50-60 euro cheaper.

**Electronics:**

1 arduino nano

1 arduino uno

1 raspberry pi3 (earlier versions should work but are not tested)

1 dht21/am2301

1 bmp180

4 6V 1W solar cells (ordering some extra can't hurt in case some are broken upon arrival or when you drop them

1 TP4056 lithium charging board

1 boost converter to 5V with usb port

2 2x 18650 battery holder

4 18650 battery cells 3.7V

1 433mHz rf transmitter

1 433mHz rf receiver

2 lcd 16x2

2 lcd to i2c adapters (mostly for convenience and using less wires)

**Miscellaneous:**

jumper wires

arduino to usb cables

duct tape (if you can't fix it with duct tape, nothing can fix it)

some sort of wood/material to make a case for the project.

copper wire (to make the antennas)

**Tools:**

soldering iron

Stanley knife

Drill

Saw

screwdriver

sand paper

Volt meter

Measuring instrument

**Some explanation about certain part choices:**

The reason i chose a arduino nano to receive the data instead of wiring the receiver directly to the pi is for modularity, we can juts unplug the USB cable from the pi and have everything working separately. This is handy so we can reuse the pi for other projects without having to destroy everything.

I went with 433 mHz rf communication because it offers a nice blend of performance for the price when coupled with a decent antenna. 433mHz is also pretty good at penetrating walls which is desirable for this project.

The choice for an arduino nano was mainly for lower power consumption and better form factor, do note that an arduino uno would also work but would use more power.

The 18650 batteries are very good at storing energy in a small form factor, the only downsides is that they are tricky to charge and are rather expensive. A lead based acid battery is also a possibility but will add a lot of weight and space to the project. Also note that for the lead battery you would have to step down the voltage.

![](https://cdn.instructables.com/FFP/6E98/J3YQAMUC/FFP6E98J3YQAMUC.MEDIUM.jpg)

![](https://cdn.instructables.com/FVX/7BX7/J3YQAMX6/FVX7BX7J3YQAMX6.SMALL.jpg)

![](https://cdn.instructables.com/FGC/3DCI/J3YQAMZP/FGC3DCIJ3YQAMZP.SMALL.jpg)

![](https://cdn.instructables.com/FZU/U865/J3YQAO3G/FZUU865J3YQAO3G.MEDIUM.jpg)

![](https://cdn.instructables.com/FQH/P9OH/J3YQAO65/FQHP9OHJ3YQAO65.SMALL.jpg)

![](https://cdn.instructables.com/FO4/HZBY/J3YQAOBA/FO4HZBYJ3YQAOBA.SMALL.jpg)

![](https://cdn.instructables.com/FFD/BHXW/J3YQAOW7/FFDBHXWJ3YQAOW7.MEDIUM.jpg)

![](https://cdn.instructables.com/FQA/HFFB/J3YQAP3G/FQAHFFBJ3YQAP3G.SMALL.jpg)

![](https://cdn.instructables.com/FIT/9WRF/J3YQAPC1/FIT9WRFJ3YQAPC1.SMALL.jpg)

![](https://cdn.instructables.com/FW2/89YW/J3YQARET/FW289YWJ3YQARET.MEDIUM.jpg)

![](https://cdn.instructables.com/F9N/PMS2/J3YQARGG/F9NPMS2J3YQARGG.SMALL.jpg)

![](https://cdn.instructables.com/FI8/K8DD/J3YQAPPT/FI8K8DDJ3YQAPPT.MEDIUM.jpg)

![](https://cdn.instructables.com/FZU/AMLW/J3YQAPU3/FZUAMLWJ3YQAPU3.MEDIUM.jpg)

![](https://cdn.instructables.com/FGH/JL8S/J3YQAQME/FGHJL8SJ3YQAQME.MEDIUM.jpg)
