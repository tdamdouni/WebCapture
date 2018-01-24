# Remote Control Bluetooth Light Switch

_Captured: 2017-11-30 at 19:03 from [www.instructables.com](http://www.instructables.com/id/Remote-Control-Bluetooth-Light-Switch/)_

This will be the first project in a series entitled: "Optimised Laziness: Over Engineered Solutions to Remarkably Trivial Problems"

Ever been lying in bed late at night reading or watching Netflix on your laptop? The worst part is of course crawling out of bed to turn off the lights. Here is an over engineered solution to that remarkably trivial problem.

As a side not:

If you have the confidence and experience to play with your mains power, a much nicer looking solution would be to use a relay and wire it in behind the light switch in the wall. However since I am renting my place I don't think this would make my landlord too happy!

## Step 1: Parts

![](https://cdn.instructables.com/FBB/4SLW/JACTV2WP/FBB4SLWJACTV2WP.MEDIUM.jpg)

  * 2 HC-05 Bluetooth Modules
  * 2 ATtiny85 chips
  * 2 8 pin IC socket
  * 2 small Lipo batteries
  * 2 push buttons
  * 2 470 ohm resistors (there is a bit of flexibility with this, the values don't need to be exactly 470)
  * 1 sg90 servo
  * Solid core wire 
  * Prototype board
  * Arduino Uno 

## Step 2: Remote Control and Switch

![](https://cdn.instructables.com/FMV/4PZ4/JACTV2WB/FMV4PZ4JACTV2WB.MEDIUM.jpg)

![](https://cdn.instructables.com/FOI/3148/JACTV2WC/FOI3148JACTV2WC.SMALL.jpg)

![](https://cdn.instructables.com/F7Q/DG4G/JACTV2WO/F7QDG4GJACTV2WO.SMALL.jpg)

![](https://cdn.instructables.com/FDO/4KJY/JACTV2WG/FDO4KJYJACTV2WG.SMALL.jpg)

Assembling the 2 circuits as shown in the pictures above. (Do not put the ATtiny85 chips in the 8 pin socket as we still need to program them.

Using a 3D printer, print out the parts for the switch. They can be found [here](https://www.thingiverse.com/thing:1156995). This is not my original design and all credit for the files goes to Thingiverse user Carjo3000.

## Step 3: Pair the Bluetooth Modules 

Next you will need to pair the two hc-05 bluetooth modules. The master will be used as the remote, and the slave for the light switch. I could outline how to do this but there are plenty of other great tutorials for doing this and there is no point reinventing the wheel. I would suggest following one of these two tutorials to pair the bluetooth modules before coming back and finishing this one.

## Step 4: Program the ATtiny85 and Upload the Code

![](https://cdn.instructables.com/FRJ/26PQ/JACTV2W3/FRJ26PQJACTV2W3.MEDIUM.jpg)

![](https://cdn.instructables.com/F9I/FP5K/JACTV2WF/F9IFP5KJACTV2WF.MEDIUM.jpg)

Again there is a great tutorial [here](https://www.hackster.io/arjun/programming-attiny85-with-arduino-uno-afb829) of how to program the ATtiny85 chips using an Arduino Uno. Just to make it clear ensure that on the step titled "Uploading program to ATtiny85" that you set the clock to "8Mhz (internal)" before burning the bootloader.

The standard servo library for Arduino does not work for the ATtiny85 chip, instead install the SoftwareServo library. I initially had a small problem with this library the solution is to open the file **Software.h** in a text editor and change the line **#include <WProgram.h>** to **#include <Arduino.h>**

To upload the code onto the ATtiny85 follow the instructions in the earlier tutorial, except upload the code I have on my [GitHub](https://github.com/WillDonaldson/Bluetooth-Light-Switch), each to each of the 2 chips. Plug the chips into the 2 circuits and now when you push the buttons it will turn on and off your lights!
