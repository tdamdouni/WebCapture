# EasyIoT Cloud and Raspberry Pi 3

_Captured: 2017-04-28 at 19:42 from [dzone.com](https://dzone.com/articles/easyiot-cloud-and-raspberry-pi-3?edition=292940&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-28)_

The Raspberry Pi is a tiny and affordable computer with a GPIO interface. In this tutorial, we will connect a Raspberry Pi 3 to EasyIoT Cloud and control the GPIO pins in a web interface or mobile application. GPIO pins can be connected to relay modules and to be used to control different devices like lights, motors, and so on. You can configure GPIO pin as digital inputs.

The Raspberry Pi application is stored on a Raspbian SD card image.

Here's a look at the EasyIoT Cloud user interface:

![](http://iot-playground.com/images/articles/056/EasyIoTCloud_raspberry3.png)

## Materials

  * Raspberry Pi 3
  * SD card
  * Power supply
  * Relay module
  * 2N2222 NPN transistor
  * 5K resistor
  * MB102 Breadboard
![](http://iot-playground.com/images/articles/056/20170425_121858.jpg)

## EasyIoT Cloud Configuration

Register to the [EasyIoT Cloud](http://cloud.iot-playground.com) service and remember your username and password. If there are pre-configured demo modules in the user interface, simply delete them.

## Raspberry Pi 3 Configuration 

First, go to the [download](http://iot-playground.com/download) page and download the EasyIoT Cloud Raspberry PI 3 Client image file. The image consists of the Raspbian OS and EasyIoT Cloud client service to control the GPIO pins.

Copy the image to your SD card. You can use dotNetDiskImager.exe or a similar program to copy the image to the SD card. You need 8GB or more space on your SD card. After copying it over, put the SD card into Raspberry Pi 3 and connect it to a power supply and the Internet.

Use a keyboard and monitor (or SSH access) to log into the Raspberry Pi 3. The default username is **pi** and the password **raspberry**. After logging in, go to the nano editor to edit the EasyIoT Cloud username and password. In the console, enter:

After editor is opened, correct the following:

If you want to change the GPIO pin directions (Input/Output), you can also change this in the XML file under Type. Possible entries are Input and Output

If you are using a GPIO pin as your input, you can also configure the GPIOResistor value to: OFF, PULL_UP, or PULL_DOWN.

After you finish the configuration, close the editor by pressing Crtl+X.

Reboot Raspberry Pi with the command:

After the reboot, log into EasyIoT Cloud and you should see new modules with the names Pin_P1_[pin number]. Pin numbers are displayed in the following picture:

![](http://iot-playground.com/images/articles/056/RPI3_Pinout.png)

> _For example, the module Pin_P1_3 is GPIO2._

Later, you can change the pin name in the EasyIoT Cloud interface under Configure->Modules to a more appropriate name like "Light living room."

Additionally, if you want the Raspberry Pi to be connected to Wi-Fi, configure the Wi-Fi adapter. In the console, enter:

And at the end of the file, add:

And replace "Your_ESSID" and "Your_wifi_password" to your own, of course. Close the editor with Ctrl+X and reboot the Raspberry Pi.

## Hardware

In our demo configuration, the GPIO output pin is connected to a relay module:

![](http://iot-playground.com/images/articles/056/Raspberry_pi_relay.png)

Input pin (Pin_P1_5 ) is configured with the PULL_UP resistor. If you do not connect anything, the input is in the high state (On). If you connect this pin to GND, the input state is OFF.
