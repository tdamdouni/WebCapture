# Smart Robot Car

_Captured: 2017-11-17 at 09:36 from [bit.ly](http://bit.ly/2AqxDSi)_

![](https://cdn.instructables.com/FPQ/BAL9/J9EH5XZ6/FPQBAL9J9EH5XZ6.MEDIUM.jpg)

I've tinkered around with Arduino and other microcontrollers for years, and was recently asked if I'd be interested in teaching a class on building a simple autonomous robot car. The "UCTRONICS Smart Robot Car Kit" is the kit that was settled on for the class. The material list should be common enough to purchase individually if the kit can no longer be found.

This project took me about 3 hours to complete in addition to taking the photos and being distracted by my 6 year old daughter and 10 month old son.

## Step 1: Gather Materials and Tools

![](https://cdn.instructables.com/FUM/39UO/J9EH3S30/FUM39UOJ9EH3S30.MEDIUM.jpg)

![](https://cdn.instructables.com/F79/5F59/J9EH3S00/F795F59J9EH3S00.SMALL.jpg)

![](https://cdn.instructables.com/F95/VURV/J9EH3S2G/F95VURVJ9EH3S2G.SMALL.jpg)

Materials:

  * Arduino UNO R3 
  * L293D motor drive shield 
  * HC-SR04 ultrasonic sensor 
  * holder for HC-SR04 
  * TowerPro SG90 servo motor 
  * SG90 servo arms 
  * mount for HC-SR04 and SG90 servo 
  * 2 gear motors (1:48) 3V-6V DC 
  * 2 tire wheels (65mm) 
  * wheel mounts 
  * 2 speed encoders 
  * caster wheel 
  * 4 AA battery pack 
  * rocker switch 
  * car chassis 
  * screws 
  * nuts 
  * extender nuts 
  * wires 
  * male headers 
  * 4 AA batteries 
  * 9v battery (optional) 
  * 9v battery power cord (optional)

Tools:

  * soldering iron (Weller WLC100)
  * silver bearing solder 
  * solder wick 
  * Phillips-head screwdriver 
  * needle nose pliers 
  * wire stripper 
  * breadboard or foam pad (optional) 
  * multimeter (optional)

Software:

  * Arduino IDE 
  * computer 
  * USB cable A-male to B-male

## Step 2: Prepare Servo Mount

![](https://cdn.instructables.com/FVP/XVRA/J9EH3SB2/FVPXVRAJ9EH3SB2.MEDIUM.jpg)

![](https://cdn.instructables.com/FHT/LUL0/J9EH3SB5/FHTLUL0J9EH3SB5.MEDIUM.jpg)

## Step 3: Prepare Ultrasonic Sensor Holder

![](https://cdn.instructables.com/FR4/KE1K/J9EH3SCS/FR4KE1KJ9EH3SCS.MEDIUM.jpg)

![](https://cdn.instructables.com/FVW/LODZ/J9EH3SFW/FVWLODZJ9EH3SFW.MEDIUM.jpg)

Carefully slide the ultrasonic sensor holder around the transmitter and receiver protrusions.  
You may need to file the holder holes or bend the transmitter and receiver to get it to fit.

## Step 4: Solder Header Pins to Motor Drive Shield

![](https://cdn.instructables.com/F4K/RQAB/J9EH3SHG/F4KRQABJ9EH3SHG.MEDIUM.jpg)

![](https://cdn.instructables.com/F74/NOCD/J9EH3SJ0/F74NOCDJ9EH3SJ0.SMALL.jpg)

![](https://cdn.instructables.com/F0L/XFY0/J9EH3SM6/F0LXFY0J9EH3SM6.SMALL.jpg)

![](https://cdn.instructables.com/FW9/FGIQ/J9EH3SNR/FW9FGIQJ9EH3SNR.SMALL.jpg)

![](https://cdn.instructables.com/F3O/8KVC/J9EH3STX/F3O8KVCJ9EH3STX.SMALL.jpg)

![](https://cdn.instructables.com/FU8/QO4J/J9EH3SUA/FU8QO4JJ9EH3SUA.SMALL.jpg)

Solder the header pins into the motor drive shield.  
We will need 4 additional pins for the ultrasonic sensor: a power source, ground, I/O pin (in this cases analog pin 5), and pin 2 (for programming the interrupt when the sensor is ready to calculate the distance).

Alternatively, you could sandwich the wires between the shield and Arduino if soldering is not your thing.

## Step 5: Attach Motors to Chassis

![](https://cdn.instructables.com/F1F/FI1A/J9EH3SVY/F1FFI1AJ9EH3SVY.MEDIUM.jpg)

![](https://cdn.instructables.com/FHO/7NWG/J9EH3SXI/FHO7NWGJ9EH3SXI.SMALL.jpg)

![](https://cdn.instructables.com/FI2/P1OK/J9EH3SXK/FI2P1OKJ9EH3SXK.SMALL.jpg)

![](https://cdn.instructables.com/F1Q/322V/J9EH3SXM/F1Q322VJ9EH3SXM.SMALL.jpg)

![](https://cdn.instructables.com/FTQ/0UQO/J9EH3SZ6/FTQ0UQOJ9EH3SZ6.SMALL.jpg)

![](https://cdn.instructables.com/FSG/1PNC/J9EH3T0R/FSG1PNCJ9EH3T0R.SMALL.jpg)

Remove any connections from the ends of the wires to expose bare wire.  
Tin the wire with solder and solder them to the motor terminals.  
Slide the motor mounts through the chassis and secure each motor with 2 screws and 2 nuts.  
Attach the speed encoders to the inside part of the motor.

**Note**: the speed encoders can be used in conjunction with an optical sensor to determine how fast the wheels are spinning and/or how far the car has traveled, but that'll have to be another instructable.

## Step 6: Attach Caster Wheel to Chassis

![](https://cdn.instructables.com/F7V/5ZDF/J9EH3T5N/F7V5ZDFJ9EH3T5N.MEDIUM.jpg)

![](https://cdn.instructables.com/FOG/6J9Y/J9EH3T84/FOG6J9YJ9EH3T84.SMALL.jpg)

![](https://cdn.instructables.com/FK8/9R9A/J9EH3TBV/FK89R9AJ9EH3TBV.SMALL.jpg)

![](https://cdn.instructables.com/FZ0/19J9/J9EH3TFC/FZ019J9J9EH3TFC.SMALL.jpg)

## Step 7: Attach Wheels to Motors

![](https://cdn.instructables.com/FHL/MXMZ/J9EH3TFE/FHLMXMZJ9EH3TFE.MEDIUM.jpg)

![](https://cdn.instructables.com/FDE/O9G8/J9EH3TFF/FDEO9G8J9EH3TFF.MEDIUM.jpg)

## Step 8: Attach Server and Ultrasonic Sensor to Chassis

![](https://cdn.instructables.com/FIO/R7O4/J9EH3TGG/FIOR7O4J9EH3TGG.MEDIUM.jpg)

![](https://cdn.instructables.com/FED/F4GL/J9EH3THG/FEDF4GLJ9EH3THG.SMALL.jpg)

![](https://cdn.instructables.com/FTK/NTIF/J9EH3TKD/FTKNTIFJ9EH3TKD.SMALL.jpg)

![](https://cdn.instructables.com/FJT/UVVJ/J9EH3TLP/FJTUVVJJ9EH3TLP.SMALL.jpg)

![](https://cdn.instructables.com/FOR/KX2G/J9EH3TN1/FORKX2GJ9EH3TN1.SMALL.jpg)

## Step 9: Attach Arduino Uno and Motor Drive Shield to Chassis

![](https://cdn.instructables.com/FVH/BJJW/J9EH3SUC/FVHBJJWJ9EH3SUC.MEDIUM.jpg)

![](https://cdn.instructables.com/F4H/IGV7/J9EH3SUD/F4HIGV7J9EH3SUD.SMALL.jpg)

![](https://cdn.instructables.com/F5U/NMFD/J9EH3UGV/F5UNMFDJ9EH3UGV.SMALL.jpg)

![](https://cdn.instructables.com/F8K/FQAJ/J9EH3UPN/F8KFQAJJ9EH3UPN.SMALL.jpg)

![](https://cdn.instructables.com/F7G/XVB1/J9EH3W8Z/F7GXVB1J9EH3W8Z.SMALL.jpg)

## Step 10: Connect Servo and Ultrasonic Sensor to Motor Shield

![](https://cdn.instructables.com/FWR/SUFS/J9EH3USW/FWRSUFSJ9EH3USW.MEDIUM.jpg)

![](https://cdn.instructables.com/F48/OL48/J9EH3TOC/F48OL48J9EH3TOC.SMALL.jpg)

![](https://cdn.instructables.com/FK2/B3PY/J9EH3TSW/FK2B3PYJ9EH3TSW.SMALL.jpg)

![](https://cdn.instructables.com/F1J/BA2I/J9EH3U7N/F1JBA2IJ9EH3U7N.SMALL.jpg)

![](https://cdn.instructables.com/FGX/AUHK/J9EH75QQ/FGXAUHKJ9EH75QQ.SMALL.jpg)

![](https://cdn.instructables.com/FOK/KJWC/J9EH75QP/FOKKJWCJ9EH75QP.SMALL.jpg)

There are dedicated servo pins on the motor drive shield so attach the servo cord to "servo one" being sure the colors are brown, red, and orange for pins 1, 2, and 3 respectively.  
Bend the pins on the ultrasonic sensor so that they are perpendicular to the back of the sensor and attach 4 wire jumpers.   
Attach the opposite ends to the power, ground, A5, and pin 2 headers soldered in from earlier.  
The remaining pins can be used for future projects.

## Step 11: Connect Motors to Motor Drive Shield

![](https://cdn.instructables.com/F9O/QRLY/J9EH3V71/F9OQRLYJ9EH3V71.MEDIUM.jpg)

![](https://cdn.instructables.com/FQE/6WSQ/J9EH3VAK/FQE6WSQJ9EH3VAK.SMALL.jpg)

![](https://cdn.instructables.com/FYJ/ASSU/J9EH3VHY/FYJASSUJ9EH3VHY.SMALL.jpg)

![](https://cdn.instructables.com/FTR/8HT8/J9JFN97Q/FTR8HT8J9JFN97Q.SMALL.jpg)

## Step 12: Attach Battery Pack and Rocker Switch to Chassis

![](https://cdn.instructables.com/FCB/UVFS/J9EH3VKT/FCBUVFSJ9EH3VKT.MEDIUM.jpg)

![](https://cdn.instructables.com/F4W/34H2/J9EH3VOW/F4W34H2J9EH3VOW.SMALL.jpg)

![](https://cdn.instructables.com/F41/ZS3K/J9EH3VRM/F41ZS3KJ9EH3VRM.SMALL.jpg)

## Step 13: Connect Battery Pack and Switch to Motor Drive Shield

![](https://cdn.instructables.com/FGS/SN4V/J9EH3VTJ/FGSSN4VJ9EH3VTJ.MEDIUM.jpg)

![](https://cdn.instructables.com/FR4/E50J/J9EH5XZX/FR4E50JJ9EH5XZX.SMALL.jpg)

![](https://cdn.instructables.com/F3N/V0GI/J9EH5XZ7/F3NV0GIJ9EH5XZ7.SMALL.jpg)

![](https://cdn.instructables.com/FHF/O88Z/J9EH3VX2/FHFO88ZJ9EH3VX2.SMALL.jpg)

![](https://cdn.instructables.com/F33/MH8N/J9JFN97R/F33MH8NJ9JFN97R.SMALL.jpg)

Cut the power (red) wire roughly in half so that we can solder it through the rocker switch.  
Attach the power wire from the switch and the ground from the battery pack to the power and ground terminal on the motor drive shield.  
This will also power the Arduino.  
Put 4AA batteries into the battery pack, hit the switch to the "on" position, and ensure that both the motor shield and Arduino power indicator lights are illuminated.

Optionally, a 9v batter can be used to power the Arduino separately.  
Powering the Arduino separately will prevent any voltage drops from resetting the Arduino code being executed.   
Similarly, the 9v battery could also be wired into the switch instead of the battery pack.

## Step 14: Download Arduino IDE, Program Sketch, and Upload to Arduino Uno

![](https://cdn.instructables.com/F3A/0059/J9JFNA6Q/F3A0059J9JFNA6Q.MEDIUM.jpg)

**Download the Arduino IDE for your operating system and architecture:  
**<https://www.arduino.cc/en/Main/Software>  
[   
](https://www.arduino.cc/en/Main/Software)**Download the program sketch: **  
[https://github.com/rricklic/arduino.uctronics.robo...  
  
](https://github.com/rricklic/arduino.uctronics.robot.car)The code will have the car move forward at full speed until it detects an obstacle.  
It will scan from 60 to 120 degrees in front and determine if it should back up and turn left or right.  
Once done it will continue moving forward again at full speed.

**How to upload program sketch to Arduino Uno:  
**Attach the USB cord to your computer and the other end to the Arduino.  
You will likely need to remove the ultrasonic sensor to get proper clearance.  
Open up the program sketch in the IDE.  
Under the "Tools" menu item, ensure that the board is set to "Arduino/Genuino Uno" and that the port is your Arduino (eg: /dev/ttyACM0).  
Hit the check button to ensure the sketch compiles.  
Hit the arrow button to upload the sketch to the attached Arduino.

**NOTE**: If you are using a Linux distribution as your operating system, you may need to set permissions by adding your user to the "dialout" group:  
_$ __sudo usermod -a -G dialout $USER  
  
_Rebooting makes this change permanent.

## Step 15: Experiment! Have Fun!

The code was made fairly simple, but the functionality is defined well in functions allowing for easily modifying the default behavior. There are also 5 analog pins that can be used for more sensors (eg: optical sensor for use with speed encoders), room for 2 more motors on the shield, and a set of servo pins so this base car can be enhance quite a bit!
