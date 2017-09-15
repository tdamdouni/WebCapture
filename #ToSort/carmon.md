# CarMon

_Captured: 2017-08-25 at 11:59 from [www.hackster.io](https://www.hackster.io/carmon/carmon-c9fb7a)_

![CarMon](https://hackster.imgix.net/uploads/attachments/298971/16405_460_m_d9e861db2b1b0982212c47403f35839b_V0jfVHfB5g.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

Driving down the roads in the California Bay Area, I can't help but notice the amount of potholes, cracks, and road faults there are in such a developed area of the country. So I came up with this idea to use the sensors built into the Intel Curie module on the Arduino 101 to monitor if there is a significant bump in the road and send that data to Caltrans, the governmental organization that maintains the roads, for them to take a look at the road and fix it as necessary.

The Intel Curie Module is a very powerful and tiny chip that can be used in many scenarios, including this one. The on-board gyro and accelerometer can monitor if there is excessive and sudden Z (vertical) axis movement and send the data to a cell phone app via Bluetooth. In addition, there can be a button attached to an easily accessible part of the steering wheel to press whenever the driver notices a road hazard or some on the road that can be improved.

In the program, the Arduino 101 uses its onboard accelerometer to determine sudden Z axis motion, which causes it to print "BUMP" to the serial monitor. The raspberry pi code is a program that looks at the Arduino serial monitor and saves all of the prints, which include a timestamp, to a file. Additionally, a button is hooked up to pin 7 that, when pressed, also prints "BUMP" to the serial monitor with a timestamp.

This data can all be sent to a connected computer, in this case the relatively small Raspberry Pi, and saved to a file for reference after the drive. This way, the user is able to go through the data and determine the location of the bumps and submit the data.

In the future, this system can be integrated to send the data to a phone that can automatically get the GPS location and send it directly to Caltrans. It can also be integrated with the car's onboard computer to also track miles traveled, gas used, and other metrics for the user to use as they want.
