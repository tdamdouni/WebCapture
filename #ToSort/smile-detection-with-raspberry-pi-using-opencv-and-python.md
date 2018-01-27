# Smile Detection With Raspberry Pi Using Opencv and Python

_Captured: 2017-11-05 at 16:14 from [www.instructables.com](http://www.instructables.com/id/Smile-Detection-With-Raspberry-Pi-Using-Opencv-and/)_

![](https://cdn.instructables.com/FCD/OJRP/J97LFXCD/FCDOJRPJ97LFXCD.MEDIUM.jpg)

In this Project we are going to detect Face and Smile Detection using OpenCv with Raspberry Pi.

## Step 1: Project Description:

![](https://cdn.instructables.com/FL0/E1BS/J97LFV5R/FL0E1BSJ97LFV5R.MEDIUM.jpg)

In this Smile detection with raspberry pi using python project we are using OpenCv in Raspberry pi. This project is used to detects the human Face and smile with the help of OpenCv tool. In order to do object detection with cascade files, you first need cascade files for face and smile detection. For the extremely popular tasks, these file already exist.

## Step 2: Software Used

![](https://cdn.instructables.com/FQB/ZMHE/J97LFV77/FQBZMHEJ97LFV77.MEDIUM.jpg)

![](https://cdn.instructables.com/FBQ/VPPV/J97LFV7B/FBQVPPVJ97LFV7B.SMALL.jpg)

![](https://cdn.instructables.com/FA1/SJ5A/J97LFV7D/FA1SJ5AJ97LFV7D.MEDIUM.jpg)

### 1.Raspian OS: 

This is the recommended os for raspberry pi. You can also installed other OS from third party. Raspbian OS is debian based OS. We can install it from noobs installer. you can get the link from [here](https://www.raspberrypi.org/downloads/)

### 2.Putty: 

PuTTY is an SSH and telnet client, developed originally by Simon Tatham for the Windows platform. PuTTY is open source software that is available with source code and is developed and supported by a group of volunteers. Here we are using putty for accessing our raspberry pi remotely. You can download PuTTY [ here ](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

### 3.OpenCv: 

OpenCV (Open Source Computer Vision Library) is an open source computer vision and machine learning software library. OpenCV was built to provide a common infrastructure for computer vision applications and to accelerate the use of machine perception in the commercial products. Being a BSD-licensed product, OpenCV makes it easy for businesses to utilize and modify the code. The library has more than 2500 optimized algorithms, which includes a comprehensive set of both classic and state-of-the-art computer vision and machine learning algorithms. These algorithms can be used to detect and recognize faces, identify objects, classify human actions in videos, track camera movements, track moving objects and extract 3D models of objects.

## Step 3: Hardware Used

![](https://cdn.instructables.com/FQ2/P2AV/J97LFVUS/FQ2P2AVJ97LFVUS.MEDIUM.jpg)

![](https://cdn.instructables.com/F61/C41V/J97LFVVE/F61C41VJ97LFVVE.MEDIUM.jpg)

You only need two hardware here:

1) Raspberry Pi

2) USB Cameras

### 1\. Raspberry Pi: 

This is the latest version of raspberry pi. In this we have inbuilt Bluetooth and wi-fi, unlike previously we have to use Wi-Fi dongle in one of its usb port. There are total 40 pins in RPI3. Of the 40 pins, 26 are GPIO pins and the others are power or ground pins (plus two ID EEPROM pins.) There are 4 USB Port and 1 Ethernet slot, one HDMI port, 1 audio output port and 1 micro usb port and also many other things you can see the diagram on right side. And also we have one micro sd card slot wherein we have to installed the recommended Operating system on micro sd card. There are two ways to interact with your raspberry pi. Either you can interact directly through HDMI port by connecting HDMI to VGA cable, and keyboard and mouse or else you can interact from any system through SSH(Secure Shell). (For example in windows you can interact from putty ssh.) Figure is given above.

### 2) USB Cameras

USB Cameras are imaging cameras that use USB 2.0 or USB 3.0 technology to transfer image data. USB Cameras are designed to easily interface with dedicated computer systems by using the same USB technology that is found on most computers. The accessibility of USB technology in computer systems as well as the 480 Mb/s transfer rate of USB 2.0 makes USB Cameras ideal for many imaging applications. An increasing selection of USB 3.0 Cameras is also available with data transfer rates of up to 5 Gb/s.

## Step 4: Installation of OpenCv

![](https://cdn.instructables.com/FB0/JDQ4/J97LFW31/FB0JDQ4J97LFW31.MEDIUM.jpg)

**Here are the Installation steps for Python OpenCv on Raspberry Pi: **  
1) sudo apt-get update

2) sudo apt-get upgrade

3) sudo apt-get install build-essential

4) sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev

5)sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

6) sudo apt-get install python-opencv

7) sudo apt-get install python-matplotlib

## Step 5: Configure and Enable Camera

![](https://cdn.instructables.com/FC9/BQ22/J97LFXMP/FC9BQ22J97LFXMP.MEDIUM.jpg)

![](https://cdn.instructables.com/FJA/0WXE/J97LFXND/FJA0WXEJ97LFXND.SMALL.jpg)

![](https://cdn.instructables.com/FQP/LM5P/J97LFXNG/FQPLM5PJ97LFXNG.SMALL.jpg)

![](https://cdn.instructables.com/FF8/HZQT/J97LFXO2/FF8HZQTJ97LFXO2.SMALL.jpg)

![](https://cdn.instructables.com/F84/6IGG/J97LFXO3/F846IGGJ97LFXO3.SMALL.jpg)

![](https://cdn.instructables.com/FTY/OLSW/J97LFXOQ/FTYOLSWJ97LFXOQ.SMALL.jpg)

## Step 7: 

The whole project description are given in the above video

Congratulations you have successfully finished your project;  
If have any doubt regarding this project feel free to comment us below or you can mail us on info@deligence.com And if you want to learn more about these type of project then feel free to visit our youtube channel : [here ](https://www.youtube.com/channel/UCbCXleygol2xB3Q4siq_6tg)

Thanks & Regards,

Deligence Technologies
