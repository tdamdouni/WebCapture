# Control Home Appliance With Raspberry Pi Using Django

_Captured: 2017-11-23 at 12:49 from [www.instructables.com](http://www.instructables.com/id/Control-Home-Appliance-With-Raspberry-Pi-Using-Dja/)_

![](https://cdn.instructables.com/FWQ/ADHM/JA1TY7F0/FWQADHMJA1TY7F0.MEDIUM.jpg)

### Introduction:

In this project we are going to switch on the home appliance from remote location using web services. In this we are going to use one raspberry pi interfacing with 4 bulb using relay module with low level trigger. Each bulb is connect in each corner like right, left, top, button. We can trigger the relay from anywhere in the world using a website. In each trigger of relay the correspondence Bulb will glow and one stop button is there for stop operation.

## Step 1: Installation of All Software

![](https://cdn.instructables.com/FC0/1174/JA1TY7GS/FC01174JA1TY7GS.MEDIUM.jpg)

![](https://cdn.instructables.com/F86/UA17/JA1TY7GT/F86UA17JA1TY7GT.MEDIUM.jpg)

![](https://cdn.instructables.com/FFK/QU25/JA1TY7GU/FFKQU25JA1TY7GU.SMALL.jpg)

### 1) Raspbian OS: 

This is the recommended os for raspberry pi. You can also installed other OS from third party. Raspbian OS is debian based OS. We can install it from noobs installer. you can Download [here ](https://www.raspberrypi.org/downloads/noobs/)

### **2) Python idle: **

This is the software we get in raspbian os. For this project we have used python script.

### 3) Pagekite: 

This is the tool to make a local website publicly accessible. We've used this to make our local website and ssh servers accessible to any network. We'll describe it later. you can Download [here ](https://pagekite.net/)

### 4) Putty: 

we are using putty for remote access of Raspberry Pi.you can Download [here ](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

### 5) Win32DiskImager: 

This software is used to burn Raspbian Os on SD Card. you can Download [here ](https://sourceforge.net/projects/win32diskimager/)

### 6) SDFormatter: 

This software is used to format memory card. you can Download [here](https://www.sdcard.org/downloads/formatter_4/)

## Step 2: Component Used:

![](https://cdn.instructables.com/F5V/X5ET/JA1TY7H3/F5VX5ETJA1TY7H3.MEDIUM.jpg)

![](https://cdn.instructables.com/FUQ/E5G6/JA1TY7H5/FUQE5G6JA1TY7H5.MEDIUM.jpg)

![](https://cdn.instructables.com/FWK/5ADK/JA1TY7H6/FWK5ADKJA1TY7H6.SMALL.jpg)

For this project you need :  
1) Raspberry pi 3

2) Relay Module

3) led Bulbs

### 1) Raspberry pi 3:

This is the latest version of raspberry pi. In this we have inbuilt Bluetooth and wi-fi, unlike previously we have to use Wi-Fi dongle in one of its usb port. There are total 40 pins in RPI3. Of the 40 pins, 26 are GPIO pins and the others are power or ground pins (plus two ID EEPROM pins.) There are 4 USB Port and 1 Ethernet slot, one HDMI port, 1 audio output port and 1 micro usb port and also many other things you can see the diagram on right side. And also we have one micro sd card slot wherein we have to installed the recommended Operating system on micro sd card. There are two ways to interact with your raspberry pi. Either you can interact directly through HDMI port by connecting HDMI to VGA cable, and keyboard and mouse or else you can interact from any system through SSH(Secure Shell). (For example in windows you can interact from putty ssh.) Figure is given above.

### 2) Relay Module: 

We have used 3 four channel relay module to control 12 led bulbs. As we are working with 220 volt ac we have to make sure that our connection are properly connected.Figure is given above.

## Step 3: Circuit Diagram

![](https://cdn.instructables.com/FQE/W14O/JA1TY7HP/FQEW14OJA1TY7HP.MEDIUM.jpg)

![](https://cdn.instructables.com/FRI/8A3Z/JA1TY7HS/FRI8A3ZJA1TY7HS.MEDIUM.jpg)

### Circuit diagram for Relay and Raspberry pi:

For complete isolation with microcontroller we can wire up our circuit as below. Here we have to remove jumper used in jd-vcc and vcc. Connection are given in figure 1

**Bulb connection with relay and raspberry pi 3: **

Here we are connecting our relay to one single Bulb. In this there is no optical isolation we can make it by removing jumper from vcc and jd-vcc. And by giving separate power supply to Jd-VCC. As below the diagram I've just shorted all the com pin of relay and from NO we've taken wire which is going to the entire bulbs one terminal and from the second terminal of bulb it will go to the ac main and the hot line of the ac will be coming from the shorted com pin of relay. Connection are given in figure 2

## Step 4: Importing Necessary Library for Raspberry Pi and Python

![](https://cdn.instructables.com/FLP/41H8/JA1TY7JE/FLP41H8JA1TY7JE.MEDIUM.jpg)

As we are using web services for this project so we have chosen Django python framework. There are many frameworks in python like flask, django, bottle so you can chose other one as well but in our project we are using Django framework.So for that you have to import django for python.

**Here are the steps for importing Django:**

**step 1: **

sudo apt-get install python-pip

After pip is installed,

**step 2: **

sudo pip install django

## Step 5: Code for Project

![](https://cdn.instructables.com/F1O/02T4/JA1TY7IJ/F1O02T4JA1TY7IJ.MEDIUM.jpg)

![](https://cdn.instructables.com/FN1/UO8T/JA1TY7IM/FN1UO8TJA1TY7IM.MEDIUM.jpg)
