# Getting iOS Notifications in Linux

_Captured: 2018-04-21 at 10:59 from [lukeberndt.com](http://lukeberndt.com/2015/getting-ios-notifications-in-linux/)_

![IMG_0583](http://lukeberndt.com/wp-content/uploads/2015/10/IMG_0583.jpg)

Apple provides access to iOS notifications over Bluetooth LE through the Apple Notification Center Service. It is really a pretty cool thing. I got support for it up and running in Arduino and documented it [here](http://lukeberndt.com/2014/ios-notifications-with-arduino/). It works great and has been pretty reliable. The problem is that it is not very practical. First off, it really only works with one specific chipset from Nordic Semiconductor. Secondly, by the time you have bought an Arduino and the BLE shield, you have already spent close to $40. The final kicker is that once you load up the library for BLE and ANCS, there isn't much memory space left on the Arduino, so you can't do anything too complex.

This led me to start looking at what was possible on Linux. Given how common and cheap Raspberry Pis are, it seemed like an interesting platform. [Sandeep Mistry](https://github.com/sandeepmistry) is doing some great work with Bluetooth LE on Linux and has even created a sample ANCS app. It is all based in Node.js, which is a fun language to use. Unfortunately, I could never get the ANCS example running on the Raspberry Pi. It also required the iOS device to be running a virtual peripheral through an App like [LightBlue Explorer](https://itunes.apple.com/us/app/lightblue-explorer-bluetooth/id557428110?mt=8).

In order to be able to work natively with iOS without requiring any app to run, you have to have your Linux system initially look like a BLE peripheral and then pivot to act like a BLE Central. In ANCS the iOS device acts like a peripheral, and the Linux device need to act like a Central. This means combing Sandeep's libraries for [BLE Peripheral](https://github.com/sandeepmistry/bleno) and [BLE Central](https://github.com/sandeepmistry/noble).

One of the other challenges I ran into is that you need to have Bluetoothd initially run, and then kill it. I am not exactly sure why, but it seems to initialize the kernel portion of Bluez. I am going to look more into this in the future, but for now do a 'stop bluetooth' or '/etc/init.d/bluetooth stop' and watch out for respawns.

The code for this is up on github: <https://github.com/robotastic/ble-ancs>

You should be able to do some pretty fun stuff with this. Since the Raspberry Pi has lots of memory, you can make notifications trigger some complex interactions. Lights can blink, balloons can be popped, and Nerf guns can be fired. And since it is written in Node, it is easy to write complex runs to make sure only VIPs get the balloon popping.

I am not sure which USB Bluetooth LE dongles to recommend. I think it is best to use a Cambridge Silicon Research or Broadcomm based dongle. There is a list up here: <https://github.com/sandeepmistry/noble/wiki/Compatible-devices>

I have just been using a couple of cheap, random ones I got off Amazon.
