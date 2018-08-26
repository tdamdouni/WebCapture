# 3D Sensing for Automotive Control

_Captured: 2018-06-01 at 20:20 from [www.hackster.io](https://www.hackster.io/Scythe/3d-sensing-for-automotive-control-a9bda6?utm_source=Hackster.io+newsletter&utm_campaign=9a75e5ec5d-EMAIL_CAMPAIGN_2018_05_23_COPY_01&utm_medium=email&utm_term=0_6ff81e3e5b-9a75e5ec5d-141949901&mc_cid=9a75e5ec5d&mc_eid=1c68da4188)_

![3D Sensing for Automotive Control](https://hackster.imgix.net/uploads/attachments/490504/2017-ford-fusion-rotary-gear-shift-dial-610x539_YcJX58wAJs.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

Sensing the position and movement of automotive control functions such as gear selectors and turn signal indicators is an important requirement in modern vehicle design. However, sensing movement in 3 axes is not straightforward and conventional sensor technologies present engineers with challenges. These range from physical device size and reliability to power consumption and cost. Recently introduced 3D magnetic sensing technology is helping engineers to address these challenges.

Electro-mechanical switching is a common source of failure in many applications, including vehicles. Contacts can corrode over time or burn out, causing failure and inconvenience for the vehicle owner and potentially damaging the reputation of the car manufacturer. As such, manufacturers prefer solid-state technology, such as switching based on Hall effect detection of magnetic-signals, wherever possible to increase reliability and save space and cost.

Two of the most common things we do when driving are signalling to turn and changing gear. In the past, cars relied on heavy-current wiring harnesses to transmit signals and power around the vehicle. Today, using a turn indicator or moving a gear shift is just as likely to send a high-impedance signal to a central processor as it is to physically switch something.

As vehicle controls become more sophisticated and multi-functional, the trend is towards them moving in more than one plane. Many modern cars with automatic gearboxes now offer sequential control by moving the gear lever into a different plane, thus making the task of sensing position more complex.

There are several ways to implement 3D position sensing based upon the Hall effect. Where the movement to be sensed has multiple fixed positions (in the case of a gear lever or turn signal), one approach is to add individual Hall sensors for each possible position, resulting in as many as seven sensor elements, allowing the controller to know the position by knowing which sensor was 'live'.

An alternative solution can be a Hall-based sensor capable of simultaneously determining the x, y, and z coordinates of a magnetic source to build a 3D image of the magnetic field surrounding the sensor.

![](https://hackster.imgix.net/uploads/attachments/490507/3d_sensing_solution_jFH9q1HrtH.gif?auto=compress%2Cformat&w=680&h=510&fit=max)

In my project I'll be portraying how Infineon's 3D magnetic sensor can be the solution that the automotive industry is looking for.

First thing were going to do is go to Infineon's 3D Magnetic Sensor webpage and download the [GUI for 3D Magnetic Sensor 2 GO](https://www.infineon.com/cms/en/product/sensor/magnetic-position-sensor/3d-magnetic-sensor/tlv493d-a1b6/#!tools), this will be the first software we use to determine that our sensor functions properly and to get a sense of its capabilities.

Our next step is to go to [SEGGER Downloads](https://www.segger.com/downloads/jlink/JLink_Windows_beta.exe) and download the J-Link related software that we will be using to program our sensor.

**Step 3****(Integration****into****the****Arduino****IDE)**

Now open Arduino IDE and go to File -> Preferences.

![](https://hackster.imgix.net/uploads/attachments/490513/preferences_HPO8m5Ctpd.png?auto=compress%2Cformat&w=680&h=510&fit=max)

Paste the following URL into the 'Additional Boards Manager URLs' input field under **File** > **Preferences** to add Infineon's microcontroller boards to the Arduino IDE.

![](https://hackster.imgix.net/uploads/attachments/490514/preferences_json_7Nmjy6E4Ly.png?auto=compress%2Cformat&w=680&h=510&fit=max)

To install the boards, please navigate to **Tools** > **Board** > **Boards Manager...** and search for XMC. You will find options to install the board files for the microcontrollers. Click "Install" to add the boards to your Arduino IDE.

![](https://hackster.imgix.net/uploads/attachments/490515/boards_manager_entry_Rn4FJJMxCH.png?auto=compress%2Cformat&w=680&h=510&fit=max)

In the boards list **Tools** > **Board**, the XMC microcontroller boards are added and can be used from now on.

![](https://hackster.imgix.net/uploads/attachments/490516/board_list_VSfPvq1XYs.png?auto=compress%2Cformat&w=680&h=510&fit=max)

In this step will add the Arduino library needed to be able program our 3D Magnetic Sensor. The library I used is the following [TLV493D-A1B6-3DMagnetic-Sensor](https://github.com/Infineon/TLV493D-A1B6-3DMagnetic-Sensor).

Our final step will be to upload to Arduino IDE the example code I've provided which will depict on our Serial Monitor the X, Y, Z values of the 3D magnetic sensor and we will also be using the on board LED for this example which in this case is pin 14. Once the knob is turned to an "x" value of more than "-1" then the LED is turned on, below "-1" the LED is off. In the following videos you can see the infineon 3D magnetic sensor board being tested with infineon's GUI, Arduino and finally with the code I've provided.
    
    
    Tle493d_w2b6 Tle493dMagnetic3DSensor = Tle493d_w2b6(Tle493d_w2b6::LOWPOWERMODE);
      while (!Serial);
      Tle493dMagnetic3DSensor.setWakeUpThreshold(1,-1,1,-1,1,-1);
    
      //The update rate is set to 3 (fastest is 0 and slowest is 7)
    
    
    
      if (Tle493dMagnetic3DSensor.getX() > -1.0) {
    
