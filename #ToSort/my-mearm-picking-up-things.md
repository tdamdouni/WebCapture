# My MeArm Picking Up Things

_Captured: 2018-05-05 at 16:38 from [www.instructables.com](http://www.instructables.com/id/My-MeArm-Picking-Up-Things/)_

## Introduction: My MeArm Picking Up Things

![Picture of My MeArm Picking Up Things](https://cdn.instructables.com/FNG/KM5K/J4OFONT8/FNGKM5KJ4OFONT8.LARGE.jpg?auto=webp&width=933)

Hi guys!

This Project is really special. I bought a MeArm (a popular, easy-to-find, inexpensive and easy-to-assembly Robotic Arm) . After putting everything together, I started with some typical stuff such as making it work with potentiometers in order to pick up some objects. It was nice at the beginning, but I got tired of it , so I decided to move on to something cooler. What I had in mind was to make my MeArm work on its own, detecting objects by itself, picking them up and eventually dropping them to a small bucket. Me just watching!!! In other words, I badly needed some way to tyde up my table once and for all. I started by google-researching similar projects but didn´t find much, so I had to start hardly from scratch. At first glance it seemed a challenging thing to be done, and after getting down to work it turned out to be even harder than expected. The good point: I ended up learning a bunch of things about Arduino and robotics, and it was really fun. And of course, when you see the final result…well, it is worth the effort!

If you are interested in doing one of your own, I can save you most of the problems that I had (and believe me, I found a lot of them) and I can provide you with some explanations, tips and my code. With all this stuff, it should be rather straightforward to get there, so get ready and get down to it!

## Step 1: Materials

![Picture of Materials](https://cdn.instructables.com/FTU/CCVV/J4OFORCP/FTUCCVVJ4OFORCP.LARGE.jpg?auto=webp&width=933)

Of course add your MeArm and some wire. To feed it you will need 5-7V (using batteries or a transformer)

## Step 2: Connections

![Picture of Connections](https://cdn.instructables.com/F9K/EGES/J4OFN2HZ/F9KEGESJ4OFN2HZ.LARGE.jpg?auto=webp&width=818)

Here I included everything I have in my setup. If you do not want to use the pushbuttons or the potentiometers, just take them away. Since Fritzing does not supply my v5.0 shield, I draw the scheme without it.

## Step 3: Built Up Your MeArm With 4 Potentiometers

![Picture of Built Up Your MeArm With 4 Potentiometers](https://cdn.instructables.com/FOZ/CF54/J4OFONT3/FOZCF54J4OFONT3.LARGE.jpg?auto=webp&width=933)

I first built up the arm with four potentiometers. You won´t be using them in the final project, when your arm works automatically, but at the beginning they are capital to calibrate and tune the arm, and to find the parameters you need in your arm. Here are some links down here with very clear explanations:

In this great youtube clip by DroneBot Workshop, everything is clear. They show you how to build a MeArm controlled by 4 potentiometers:

Here some other useful links: [ https://cdn-shop.adafruit.com/datasheets/Pocket-S...](https://cdn-shop.adafruit.com/datasheets/Pocket-Sized-Robot-Arm-meArm-V04.pdf)

please follow instructions carefully, they are easy to follow but if you miss one single step you are probably going to end up moving back to square one again, so make sure everything is ok before moving up to the next step. Once you complete this part, here is my [improved sketch](https://create.arduino.cc/editor/fjvila/719f8796-f08d-4393-9e72-e5e226a769d5/preview) so that you can try it out. This sketch uses the EEPROM memory, very useful to avoid the typical initial jolts of the servos when reseting your Arduino. The code stores in the EEPROM memory the values of the servo positions before switching off or reseting it, and if in the meantime for some reason you move the potentiometers, it will go smoothly to the pot position. Cool!

...and If you just want the typical basic one,[ here it is](https://create.arduino.cc/editor/fjvila/f211b29a-b3ab-4c12-8425-fe2f6813a6ca/preview)

## Step 4: Connect Pusthbuttons (optional)

![Picture of Connect  Pusthbuttons \(optional\)](https://cdn.instructables.com/FOP/AW0M/J4OFONT6/FOPAW0MJ4OFONT6.LARGE.jpg?auto=webp&width=600)

![Picture of Connect  Pusthbuttons \(optional\)](https://cdn.instructables.com/FA8/23PD/J4OFOTSU/FA823PDJ4OFOTSU.LARGE.jpg?auto=webp&width=600)

This step is optional, but I find it particularly useful while the Arm is moving and something wrong happens, you just press the help-button then , and everything stops right on time…very useful stuff in my opinion. You will see at the sketch that those pins are defined as "INPUT PULL_UP", this way you use an internal 20K before the 5V signal. By using these buttons the code gets longer and more difficult, involving Interruptions, but everything is written down there at my code, so don´t worry much about it if what you want is just a "plug-and-play" robot.

## Step 5: Time to Connect the Acoustic Sensor

![Picture of Time to Connect the Acoustic Sensor](https://cdn.instructables.com/F3E/YEQ7/J4OFOR6P/F3EYEQ7J4OFOR6P.LARGE.jpg?auto=webp&width=800)

![Picture of Time to Connect the Acoustic Sensor](https://cdn.instructables.com/FZ4/M0MR/J4OFORBW/FZ4M0MRJ4OFORBW.LARGE.jpg?auto=webp&width=400)

![Picture of Time to Connect the Acoustic Sensor](https://cdn.instructables.com/FBB/FO6A/J4OFORBY/FBBFO6AJ4OFORBY.LARGE.jpg?auto=webp&width=400)

Glue the acoustic sensor to your robotic arm as in the pictures. If you want to run some checks on your sensor, here I hand you this [testing-sketch](https://create.arduino.cc/editor/fjvila/ab544b36-94ff-4cb4-a2dd-84ca32d51fb5/preview). That code runs several types of measures: taking (200/100/20/5/1) measures, then calculating the average value . Of course taking 200 measures to calculate the average is , in theory, more accurate, but It also takes a lot of time, and since the arm is always moving it is better to do the average over 5-20 measures at most.

## Step 6: The Sketch

Now comes the software part. Before uploading the code, you are going to need the library NewPing.h. With that library you will control your HC-SR05 acoustic sensor more precisely. Once you got it, just upload the sketch and start playing with your cool MeArm robot!

## Step 7: Some Final Remarks

The kind of objects that you will want to use for your project will be the small, square-like, cardoard-made ones. Don´t even try curved-cross section objects, this acoustic sensor proved to be absolutely dumb with them. Even following this tip, this HC-SR05 sensor makes mistakes every now and then no matter the distance or the conditions, and proved to be absolutely unreliable at short distances (specially under 5-6 cm) In addition, the claw is quite a simple one, and it must be almost perfectly perpendicular to the object to succeed on picking up the object. Of course all these details made the project harder than expected, but I bypassed most of the hard stuff by modifying my initial sketch. But finally I got there!!!

If you have any suggestions on the code to make it simpler, more efficient or elegant, or about anything, or you just need some more help let me know!!!

Hope you enjoyed it!!!

## Recommendations

  * ![IoT Wallet \(smart Wallet With Firebeetle ESP32, Arduino IDE and Google Spreadsheet\)](https://cdn.instructables.com/FO1/6MAE/JGMJ9GEU/FO16MAEJGMJ9GEU.RECTANGLE1.jpg)

> _IoT Wallet (smart Wallet With Firebeetle ESP32, Arduino IDE and Google Spreadsheet)_

  * ![Pocket Metal Locator - Arduino](https://cdn.instructables.com/FG9/WLL8/JGMJC6LW/FG9WLL8JGMJC6LW.RECTANGLE1.jpg)

> _Pocket Metal Locator - Arduino_

  * ![Awful to Awesome: Replace a Mechanical Alarm Sound](https://cdn.instructables.com/FFE/3SGA/JGNWS8SB/FFE3SGAJGNWS8SB.RECTANGLE1.jpg)

> _Awful to Awesome: Replace a Mechanical Alarm Sound_

  * ![Arduino Class](https://cdn.instructables.com/FVR/H9FV/J1WW2UOV/FVRH9FVJ1WW2UOV.RECTANGLE1.jpg)

> _Arduino Class_

## 4 Comments
