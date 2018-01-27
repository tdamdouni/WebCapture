# Real-time MPG display on an older car

_Captured: 2017-12-08 at 00:01 from [www.macchina.cc](https://www.macchina.cc/content/real-time-mpg-display-older-car)_

![](https://www.macchina.cc/sites/default/files/mpg%20banner%20crop.png)

Most newer cars already have a display showing you how efficiently you are driving. Usually this takes the form of a digital readout showing you miles driven per gallon of gas over 2 time-frames: short term (instantaneous) and long term (average). Wouldn't it be cool to add this feature to older cars?

![](https://www.macchina.cc/sites/default/files/styles/640_wide/public/20171106_122955_1.png?itok=cJK3j5kf)

#  Here is a typical MPG readout from a typical car. Kinda lame. Let's make something cooler!

**So how do you calculate MPG?** We need to know how much fuel is being used and how far the vehicle travels by burning that fuel. With only 2 variables, Mass Air Flow (MAF) and vehicle speed (VSS), we can calculate fuel economy.

Mass air flow (MAF) is a measurement of the amount of air going to the engine measured in grams/second. Your car's ECU constantly tries to maintain the ideal ratio of air and fuel to make the most efficient combustion. For gasoline, this ratio is 14.7 grams of air per gram of fuel. Read more about that [here](https://en.wikipedia.org/wiki/Stoichiometry).

Vehicle speed (VSS) is a measurement of speed (duh) measured in Km/hour.

Next, we convert grams of gasoline to gallons. This can vary depending on fuel grade, but we'll use 6.17 pounds per gallon for this constant. Now it is just a matter of converting units and simplifying the math knowing that 454g = 1 pound, 3600 seconds = 1 hour, and 1 Km = 0.621371 miles. This yields the following formula to derive MPG:

The original source for the above math can be found in a 2005 article in Circuit Cellar magazine by Bruce D. Lightner. For a more in-depth explanation, refer to the article [here](http://www.lightner.net/lightner/bruce/Lightner-183.pdf).

Thankfully, both of these values (and many more) are required to be available at the OBD2 port of a car. While we could have done this project with a newer CAN-bus equipped car, we decided to test with an older Pre-CAN car. In this case, we gave a sweet 2004 Toyota Rav4 a modern car feature!

**Hardware:**

The hardware setup is pretty straight-forward. Our test vehicle (the sweet 2004 Rav4) uses ISO9141 (aka K-Line) as the communication protocol. ISO9141 is similar to RS-232, but with different voltage levels. Read all about K-line in our [documentation section. ](http://docs.macchina.cc/m2/technical-references/interfaces.html#k-line-aka-iso9141-kwp2000)

We use a [Macchina M2](https://www.macchina.cc/content/m2-under-dash) as the ISO9141 interface.

To display MPG data, we could have used a standard digital readout like some cars have, but we thought it would be much cooler to build a more "relative" value gauge. While knowing the exact MPG value can be useful, we figured a display that gave us an instant visual feedback of how we are driving would easier to interpret while in motion.

For this purpose, we chose the [Adafruit NeoPixel Stick](https://www.adafruit.com/product/2869) as the indicator - simply 8 addressable RGB LEDs in a row.

Only 3 wires are needed to connect M2 to a NeoPixel. We connected +5V, GND and Data from the 26 pin connector to the NeoPixel.

![](https://www.macchina.cc/sites/default/files/styles/640_wide/public/setup.png?itok=anGFfAWC)

> _Simple set up_

![](https://www.macchina.cc/sites/default/files/styles/640_wide/public/connections.png?itok=JD6197E1)

> _3 wires connected to 26 pin "expansion" connector_

![](https://www.macchina.cc/sites/default/files/styles/640_wide/public/NeoPixel.png?itok=OltbKLeV)

> _3 wires soldered to NeoPixel_

For our demo, we used an OBD extension cable and shorter wire to the NeoPixel. Alternatively, we could have plugged M2 directly into the OBD2 port and ran longer wires to the LED display. For the test drive, we just stuck the LEDs and M2 to the dash with double-sided tape.

**Code:**

The sketch loaded onto M2 employs 2 excellent libraries to handle the ISO9141 communication and LED driving:

The actual sketch code is here:

**Demo:**

An interesting discovery is that it is quite easy to "train" yourself to not make the red LEDs light up when driving. M2 was programmed to make the LED display show red light up when car goes below 10 MPG. It seems that even small gas pedal changes can make a large MPG change, while not making a large acceleration change.

It would be interesting to monitor how using this gauge over time can change affect overall driving habits.

**Next steps, going further: **

\- Do the same project with a newer CAN-equipped car.  
\- Expand display by adding additional NeoPixel Stick for "Average" MPG.  
\- Add more colors for more visual feedback and cooler display. Maybe more colors for different ranges of MPG.  
\- Add a "trip cost" feature: Input how much you paid for a gallon of gas, M2 calculates actual cost of traveling from A to B.

**Discussion:**

Join the conversation at our forums. Share your thoughts, questions and ideas.
