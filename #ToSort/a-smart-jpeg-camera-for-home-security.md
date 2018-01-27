# A Smart JPEG Camera for Home Security

_Captured: 2017-11-08 at 23:31 from [www.instructables.com](http://www.instructables.com/id/Smart-JPEG-Camera-for-Home-Security/)_

![](https://cdn.instructables.com/FBA/VVHC/IV0AQA67/FBAVVHCIV0AQA67.MEDIUM.jpg)

### Introduction

This instructable will cover the basic steps that you need to follow to get started with open sources such as Watson nodes(Visual Recognition V3, Text To Speech) for IBM Bluemix, Node-RED, OpenCV, MQTT v3.1. MQTT(Message Queueing Telemetry Transport) is a Machine-To-Machine(M2M) or Internet of Things (IoT) connectivity protocol that was designed to be extremely lightweight and useful when low battery power consumption and low network bandwidth is at a premium. It was invented in 1999 by Dr. Andy Stanford-Clark and Arlen Nipper and is now an [Oasis Standard](https://www.oasis-open.org/news/announcements/mqtt-version-3-1-1-becomes-an-oasis-standard).

I've already published an instructable of [the Smart Gas Valve For Safety](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/). In addition, I'm going to communicate between [A Smart JPEG Camera](https://www.instructables.com/id/Smart-JPEG-Camera-for-Home-Security/) and [A Smart Gas Valve](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/) for M2M Communication by MQTT. Specifically, this instructable will cover how to code the Node-RED on Raspberry Pi2 as a MQTT client by connecting to your home wireless network and how to send sensor data. I will be using [A Smart Gas Valve](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/) for M2M communication by MQTT.

\- How to use the Bluemix platform (Docs)

![](https://cdn.instructables.com/FAA/8DLP/IUSLVNCS/FAA8DLPIUSLVNCS.MEDIUM.jpg)

![](https://cdn.instructables.com/FAS/OF5Z/IUSLU40U/FASOF5ZIUSLU40U.MEDIUM.jpg)

![](https://cdn.instructables.com/F80/6OVZ/IV0AR1I1/F806OVZIV0AR1I1.MEDIUM.jpg)

![](https://cdn.instructables.com/FT7/6NJE/IUOI5TYN/FT76NJEIUOI5TYN.MEDIUM.jpg)

![](https://cdn.instructables.com/FT9/8O6E/IUOI5TZ4/FT98O6EIUOI5TZ4.SMALL.jpg)

![](https://cdn.instructables.com/FSA/RU9B/IUOIAKEP/FSARU9BIUOIAKEP.MEDIUM.jpg)

![](https://cdn.instructables.com/FAZ/RAQY/IUOI5UPN/FAZRAQYIUOI5UPN.MEDIUM.jpg)

![](https://cdn.instructables.com/FTA/W9NO/IUOI5URC/FTAW9NOIUOI5URC.MEDIUM.jpg)

![](https://cdn.instructables.com/FDX/XC27/IUOIAK2H/FDXXC27IUOIAK2H.MEDIUM.jpg)

![](https://cdn.instructables.com/FGV/DM60/IV0AQG1S/FGVDM60IV0AQG1S.MEDIUM.jpg)

![](https://cdn.instructables.com/F1W/ACAL/IV0AQFWE/F1WACALIV0AQFWE.MEDIUM.jpg)

# A Smart JPEG Camera for Home Security

## Introduction: A Smart JPEG Camera for Home Security

### Introduction

This instructable will cover the basic steps that you need to follow to get started with open sources such as Watson nodes(Visual Recognition V3, Text To Speech) for IBM Bluemix, Node-RED, OpenCV, MQTT v3.1. MQTT(Message Queueing Telemetry Transport) is a Machine-To-Machine(M2M) or Internet of Things (IoT) connectivity protocol that was designed to be extremely lightweight and useful when low battery power consumption and low network bandwidth is at a premium. It was invented in 1999 by Dr. Andy Stanford-Clark and Arlen Nipper and is now an [Oasis Standard](https://www.oasis-open.org/news/announcements/mqtt-version-3-1-1-becomes-an-oasis-standard).

I've already published an instructable of [the Smart Gas Valve For Safety](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/). In addition, I'm going to communicate between [A Smart JPEG Camera](https://www.instructables.com/id/Smart-JPEG-Camera-for-Home-Security/) and [A Smart Gas Valve](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/) for M2M Communication by MQTT. Specifically, this instructable will cover how to code the Node-RED on Raspberry Pi2 as a MQTT client by connecting to your home wireless network and how to send sensor data. I will be using [A Smart Gas Valve](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/) for M2M communication by MQTT.

\- How to use the Bluemix platform (Docs)

<https://console.ng.bluemix.net/docs/>

## Step 1: Table of Contents

  * Step 0: Introduction
  * Step 1: Table of Contents
  * Step 2: Bill of Materials
  * Step 3: Setting up the Camera & PIR Sensor with Raspberry Pi
  * Step 4: Programming NodeRED on Raspberry Pi2
  * Step 5: Setting up MQTT v3.1 on Raspberry Pi2
  * Step 6: Checking your NodeRED codes with MQTT on Raspberry Pi2
  * Step 7: Programming Python JPEG Camera
  * Step 8: Adding IBM Watson, IBM NoSQL DB, Play-Audio, and Twilio
  * Step 9: Adding autostart files for every boot
  * Step 10: Testing M2M Communication
  * Step 11: (Optional) Using OpenCV
  * Step 12: Download list
  * Step 13: List of references

## Step 2: Bill of Materials

  * **Raspberry Pi2** X 1ea
    * Pi-1,2,3 are Possible.
    * [Installation guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)
    * [Download image files](https://www.raspberrypi.org/downloads/)
    * [Installing VNC](https://learn.adafruit.com/adafruit-raspberry-pi-lesson-7-remote-control-with-vnc/installing-vnc) : You can connect Raspberry Pi2 with Macbook Pro or Windows.

  * ****Pi Camera Board ****X 1ea
    * [Description & Technical details](https://www.adafruit.com/product/1367)

  * **Wifi dongle** X 1ea
    * [Description](https://www.canakit.com/raspberry-pi-wifi.html)
    * If you have Pi-3, it's unnecessary.

  * **PIR motion sensor** X 1ea
    * [Overview](https://learn.adafruit.com/pir-passive-infrared-proximity-motion-sensor/how-pirs-work?view=all)

  * **Android smartphone's portable battery** X 2ea
  * **Nod-RED software** X 1ea
    * Free open source
    * Use the version pre-installed in Raspbian Jessie image since November 2015
    * [Installation guide](http://nodered.org/docs/hardware/raspberrypi)

  * **MQTT v3.1 software** X 1ea
    * Free open source
    * Installation guide includes **at Step 5**

  * **NodeRED's IBM Watson Nodes for Bluemix**
    * Text to speech node X 1ea
    * Visual Recognition X 1ea

  * **Speaker** X 1ea
  * **Minion** X 1ea
    * You can easily buy it from eBay.

  * **Places to buy from? **
    * [Element14](http://www.newark.com/)
    * [Adafruit](https://www.adafruit.com/)
    * [DigiKey](http://www.digikey.com/)
    * [Sparkfun](https://www.sparkfun.com/)
    * [eBay](http://www.ebay.com/)
    * [Amazon](https://www.amazon.com/)

## Step 3: Setting Up the Camera & PIR Sensor With Raspberry Pi

![Picture of Setting Up the  Camera & PIR Sensor With Raspberry Pi](https://cdn.instructables.com/FAA/8DLP/IUSLVNCS/FAA8DLPIUSLVNCS.MEDIUM.jpg)

### Assembly steps for Smart JPEG Camera

(1) Connect the Raspberry Pi2 with a PIR motion sensor as shown above in the circuit diagram.

(2) Connect the PIR motion sensor with Raspberry Pi2.

  * Raspberry Pi2 <\----> PIR motion Sensor  
    * 5V ---------------- VCC
    * GND ------------- GND
    * GPIO 18 -------- OUT

(4) Assemble carefully the Pi camera with Raspberry Pi2.

(5) Connect a portable battery with Raspberry Pi2. (Use any portable battery to connect with the same size connector cable on Raspberry Pi2. )

### Assembly steps for Smart Gas Valve : [here](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/)

## Step 4: Programming NodeRED on Raspberry Pi2

![Picture of Programming NodeRED on Raspberry Pi2](https://cdn.instructables.com/F80/6OVZ/IV0AR1I1/F806OVZIV0AR1I1.MEDIUM.jpg)

How to start Node-RED on web-browser.

(1) Write down command shown below to a terminal window. node-red-start

(2) You can find an IP address as below. 'Once Node-RED has started, point a browser at http://169.254.170.40:1880' (It depends on your IP address)

(3) Open your web browser.

(4) Copy the IP address and paste on the web browser.

(5) It will display a visual editor of Node-RED on the web browser.

(6) You can start coding with visual editor on the web browser.

(7) Try dragging & dropping any node from the left-hand side to right-hand side. It's really easy to code. ( You can conveniently use the visual editor offline as well as online. ) Download the 'SmartGasValve_NodeRED.txt' file. (1) Click the number (1) at the right-hand side corner shown in NodeRED on the web browser.

(2) Click the Import button on the drop down menu.

(3) Open the Clipboard shown in the above 1st picture.

(4) Lastly, paste the given JSON format text of '**SmartJPGCameraNoCredits_NodeRED_ver0.1.txt**' in Import nodes editor.

## Step 5: Setting Up MQTT V3.1 on Raspberry Pi2

![Picture of Setting Up MQTT V3.1 on Raspberry Pi2](https://cdn.instructables.com/FT7/6NJE/IUOI5TYN/FT76NJEIUOI5TYN.MEDIUM.jpg)

### Setting up MQTT v3.1 on Raspberry Pi2

This message broker(Mosquitto) is supported by MQTT v3.1 and it is easily installed on the Raspberry Pi and somewhat less easy to configure. Next, we step through installing and configuring the Mosquitto broker. We are going to install & test the MQTT “mosquitto” on the terminal window.

    
    
    curl -O http://repo.mosquitto.org/debian/mosquitto-repo.gpg.key
    
    
    sudo apt-key add mosquitto-repo.gpg.key
    
    
    rm mosquitto-repo.gpg.key
    
    
    cd /etc/apt/sources.list.d/
    
    
    sudo curl -O http://repo.mosquitto.org/debian/mosquitto-jessie.list
    
    
    sudo apt-get update

Next install the broker and command line clients:

  * **mosquitto** – the MQTT broker (or in other words, a server)
  * **mosquitto-clients** – command line clients, very useful in debugging
  * **python-mosquitto** – the Python language bindings

    
    
    sudo apt-get install mosquitto mosquitto-clients python-mosquitto

As is the case with most packages from Debian, the broker is immediately started. Since we have to configure it first, stop it.

    
    
    sudo /etc/init.d/mosquitto stop

Now that the MQTT broker is installed on the Pi we will add some basic security.  
Create a config file:

    
    
    cd /etc/mosquitto/conf.d/
    
    sudo nano mosquitto.conf

Let's stop anonymous clients connecting to our broker by adding a few lines to your config file. To control client access to the broker we also need to define valid client names and passwords. Add the lines:

    
    
    allow_anonymous false
    
    password_file /etc/mosquitto/conf.d/passwd
    
    require_certificate false

Save and exit your editor (nano in this case).  
From the current /conf.d directory, create an empty password file:

    
    
    sudo touch passwd

We will use the mosquitto_passwd tool to create a password hash for user pi:

    
    
    sudo mosquitto_passwd -c /etc/mosquitto/conf.d/passwd pi

You will be asked to enter your password twice. Enter the password you wish to use for the user you defined.

### Testing Mosquitto on Raspberry Pi

Now that Mosquitto is installed we can perform a local test to see if it is working:  
Open three terminal windows. In one, make sure the Mosquitto broker is running:

    
    
    mosquitto

In the next terminal, run the command line subscriber:

    
    
    mosquitto_sub -v -t 'topic/test'

You should see the first terminal window echo that a new client is connected.  
In the next terminal, run the command line publisher:

    
    
    mosquitto_pub -t 'topic/test' -m 'helloWorld'

You should see another message in the first terminal window saying another client is connected. You should also see this message in the subscriber terminal:

    
    
    topic/test helloWorld

We have shown that Mosquitto is configured correctly and we can both publish and subscribe to a topic.  
When you finish testing all, let's set up below that.

    
    
    sudo /etc/init.d/mosquitto start

## Step 6: Checking Your NodeRED Codes With MQTT on Raspberry Pi2

![Picture of Checking Your NodeRED Codes With MQTT on Raspberry Pi2](https://cdn.instructables.com/FI6/BLTY/IV0AQL3G/FI6BLTYIV0AQL3G.MEDIUM.jpg)

When you have already used the JSON format of the 'SmartGasValve_NodeRED.txt' on Node-RED, it's automatically set up & coded each data. I have already set up the each data in each node.

(1) Click each node.

(2) Check information inside each node has been prefilled.

(3) Please don't change the set data.

(The above can be customized for more advanced users.)

## Step 7: Programming Python JPEG Camera

![Picture of Programming Python JPEG Camera](https://cdn.instructables.com/FAZ/RAQY/IUOI5UPN/FAZRAQYIUOI5UPN.MEDIUM.jpg)

### Programming Python JPEG Camera

First of all, you should test the camera module in the terminal window.

    
    
    raspistill -o test.jpg

You should see the test.jpg in '/home/pi'

    
    
    cd /home/pi 
    
    
    mkdir pythonPir
    
    
    cd pythonPir
    
    
    sudo nano pircameraNodeRED.py

Type the below (the enclosed file) Or Put ‘pircameraNodeRED.py’ file into '/home/pi/pythonPir' folder.

    
    
    import RPi.GPIO as GPIO 
    import time
    import picamera
    import datetime 
    
    timeFormat = 0
    
    GPIO.setmode(GPIO.BCM)
    GPIO.setup(17, GPIO.IN)  # For M2M Communication from Gas Valve signal
    GPIO.setup(18, GPIO.IN)
    camera = picamera.PiCamera()
    
    while True:
            input17 = GPIO.input(17)  #Pin number 17 activates
            input18 = GPIO.input(18)  #Pin number 18 activates
            now = datetime.datetime.now()
            timeFormat = now.strftime("%Y%m%d_%H%M_%S.%s") #To put date and time in images
    
            if input17 == True or input18 == True:  #If PIR Sensor detects something, the Picamera will take.
                    print('Motion_Detected_%s' %timeFormat)
                    camera.capture('image_%s.jpg' %timeFormat) #To take a picture
    
                    time.sleep(1) #sleeping time 1 second

When you finish typing, you should press the keys '**Control**' + '**x**' and press '**y**' to save this file.

### Making an image file server

    
    
    cd /home/pi
    
    
    mkdir camserver
    
    
    sudo nano requirements.txt

Type the below (the enclosed file) Or Put ‘requirements.txt’ file into '/home/pi/camserver' folder.

    
    
    numpy==1.10.1
    websocket-client==0.35.0
    websocket-server==0.4
    ibmiotf==0.2.3
    
    
    pip install --user -r requirements.txt

Execute an image file server in /home/pi/ below.

    
    
    cd /home/pi
    
    
    python -m SimpleHTTPServer 7000

## Step 8: Adding IBM Watson, IBM NoSQL DB, Play-Audio, and Twilio

![Picture of Adding IBM Watson, IBM NoSQL DB, Play-Audio, and Twilio](https://cdn.instructables.com/FH8/0WA4/IV0AKBZ9/FH80WA4IV0AKBZ9.MEDIUM.jpg)

### Searching the Nodes

Node-RED comes with a core set of useful nodes, but there are a growing number of additional nodes available for installing from both the Node-RED project as well as the wider community. You can search for available nodes in the [Node-RED library](http://flows.nodered.org/) or on the [npm repository](https://www.npmjs.com/browse/keyword/node-red).

  * For example, we are going to search Twilio at the npm web. [Click here](https://www.npmjs.com/package/node-red-node-twilio).
  * Then, we are going to install Twilio on Raspberry pi.

### Installing npm packaged node

To add additional nodes you must first install the npm tool, as it is not included in the default installation. The following commands install npm and then upgrade it to the latest 2.x version.

    
    
    sudo apt-get update
    
    
    sudo apt-get install npm
    
    
    sudo npm install -g npm@2.x
    
    
    hash -r
    
    
    cd /home/pi/.node-red

  * For example, 'npm install node-red-{example node name}'
  * Copy the 'npm install node-red-node-twilio' from [the npm web](https://www.npmjs.com/package/node-red-node-twilio). Paste it on a terminal window.
  * Ex: node-red-node-watson, node-red-contrib-play-audio, node-red-dashboard, node-red-node-pidcontrol, and, node-red-node-cf-cloudant.

    
    
    npm install node-red-node-twilio

  * You will need to restart Node-RED for it to pick-up the new nodes.

    
    
    node-red-stop
    
    node-red-start

  * Close your web browser and reopen the web browser.

## Step 9: Adding Autostart Files for Every Boot.

![Picture of Adding Autostart Files for Every Boot.](https://cdn.instructables.com/FDX/XC27/IUOIAK2H/FDXXC27IUOIAK2H.MEDIUM.jpg)

### How to make autostart files at every boot.

  * **Mosquitto  

**

    
    
    cd /etc/xdg/autostart/
    
    
    sudo nano flyMosquitto.desktop

Type the below (this will enclose the file) Or Put ‘flyMosquitto.desktop’ file into autostart folder.

    
    
    [Desktop Entry] 
    Type=Application
    Name=flyMosquitto
    Comment=Fly my mosquitto
    Exec=cd /etc/mosquitto/conf.d/
    Exec=mosquitto

  * **Node-RED**

    
    
    sudo systemctl enable nodered.service

  * **Python JPEG Camera **

    
    
    cd /etc/xdg/autostart/
    
    
    sudo nano pircameraNodeRED.desktop

Type the description below or put the ‘**pircameraNodeRED.desktop**’ file into **/etc/xdg/autostart/** folder.

    
    
    [Desktop Entry]
    Type=Application
    Name=pircameraNodeRED.py
    Comment=Start my security camera
    NoDisplay=false
    Exec=python /home/pi/pythonPir/pircameraNodeRED.py
    NotShowIn=GNOME;KDE;XFCE;
    Name[en_US]=pircamera.py
    

  * **Image file Server  

**

    
    
    cd /etc/xdg/autostart/
    
    
    sudo nano imageFileServer.desktop

Type the description below or put the ‘**imageFileServer.desktop**’ file into **/etc/xdg/autostart/** folder.

    
    
    [Desktop Entry]
    Type=Application 
    Name=imageFileServer 
    Comment=Start an image file server 
    NoDisplay=false 
    Exec=cd /home/pi 
    Exec=python -m SimpleHTTPServer 7000

## Step 10: Testing M2M Communication.

![Picture of Testing M2M Communication.](https://cdn.instructables.com/FGH/U7Z8/IUSLUAYM/FGHU7Z8IUSLUAYM.MEDIUM.jpg)

### Importing the enclosed files in each NodeRED.

(1) [Using a smart JPEG camera](https://www.instructables.com/id/Smart-JPEG-Camera-for-Home-Security/)

Import the '**M2M_SmartJPGCamera.txt**' into the NodeRED of the smart JPEG camera.

(2) [Using a smart gas valve](https://www.instructables.com/id/Smart-Gas-Valve-Checker-for-Home-Safety/)

Import the '**M2M_SmartGasValve.txt**' into the NodeRED of the smart gas valve.

(3) Check an IP address of the smart gas valve in the Raspberry Pi2.

Type 'ifconfig' on a terminal window as shown below.

    
    
    ifconfig

When you see the IP address, copy the IP address in a terminal window.

(4) Put the IP address into the MQTT node in other Raspberry Pi2.

  1. Click the MQTT node.
  2. Put the IP address into Server.

## Step 11: (Optional) Using OpenCV 

![Picture of \(Optional\) Using OpenCV ](https://cdn.instructables.com/FGV/DM60/IV0AQG1S/FGVDM60IV0AQG1S.MEDIUM.jpg)

### Installing & Using OpenCV on Raspberry Pi2

We have already used the IBM Watson Visual Recognition. Watson Visual Recognition is very excellent whereas we can't use it without connecting wifi. OpenCV is possible to use without internet connection but It's not very easy for a beginner to install & code into OpenCV. So, I'm going to install the OpenCV.

  * Download 'opencv-3.1.0.zip from [opecv.org](http://opencv.org/)

### 

  * Install dependencies

    
    
    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev python-dev python-numpy libjpeg-dev libpng-dev libtiff-dev libjasper-dev

  * (Optional) Install OpenCV 2

    
    
    sudo apt-get install python-opencv

  * Install OpenCV 3

    
    
    unzip ~/Downloads/opencv-3.1.0.zip
    cd opencv-3.1.0/
    mkdir build
    cd build/
    cmake -DCMAKE_BUILD_TYPE=Debug -DBUILD_TESTS=NO -DBUILD_PERF_TESTS=NO ..
    make -j3
    sudo make install
    sudo ldconfig

  * Check which version of OpenCV you have in Python

    
    
    python
    import cv2
    cv2.__version__

  * Run the simple face detect sample, and look at its code to see how it works:
  * Before, you should connect an USB-cam with Raspberry Pi2

    
    
    cd /home/pi
    cd opencv-3.1.0
    python ./facedetect.py

## Step 12: Download List

  * ![SmartJPGCameraNoCredits_NodeRED_ver0.1.txt](/intl_static/img/pixel.png)[SmartJPGCameraNoCredits_NodeRED_ver0.1.txt](https://cdn.instructables.com/ORIG/F54/QXJW/IV0AYXLU/F54QXJWIV0AYXLU.txt)

[Download](https://cdn.instructables.com/ORIG/F54/QXJW/IV0AYXLU/F54QXJWIV0AYXLU.txt)

  * ![M2M_SmartGasValve.txt](/intl_static/img/pixel.png)[M2M_SmartGasValve.txt](https://cdn.instructables.com/ORIG/FVE/6CVP/IUSLUZ8L/FVE6CVPIUSLUZ8L.txt)

[Download](https://cdn.instructables.com/ORIG/FVE/6CVP/IUSLUZ8L/FVE6CVPIUSLUZ8L.txt)

  * ![M2M_SmartJPGCamera.txt](/intl_static/img/pixel.png)[M2M_SmartJPGCamera.txt](https://cdn.instructables.com/ORIG/FG8/BXF0/IUSLUZ8N/FG8BXF0IUSLUZ8N.txt)

[Download](https://cdn.instructables.com/ORIG/FG8/BXF0/IUSLUZ8N/FG8BXF0IUSLUZ8N.txt)

  * ![pircameraNodeRED.py](/intl_static/img/pixel.png)[pircameraNodeRED.py](https://cdn.instructables.com/ORIG/FAY/X8UX/IUSLV1OA/FAYX8UXIUSLV1OA.py)

[Download](https://cdn.instructables.com/ORIG/FAY/X8UX/IUSLV1OA/FAYX8UXIUSLV1OA.py)

  * ![requirements.txt](/intl_static/img/pixel.png)[requirements.txt](https://cdn.instructables.com/ORIG/F7H/JBJ4/IUSM0YDA/F7HJBJ4IUSM0YDA.txt)

[Download](https://cdn.instructables.com/ORIG/F7H/JBJ4/IUSM0YDA/F7HJBJ4IUSM0YDA.txt)

  * ![flyMosquitto.desktop](/intl_static/img/pixel.png)[flyMosquitto.desktop](https://cdn.instructables.com/ORIG/FY1/H8L9/IUSM8XWS/FY1H8L9IUSM8XWS.desktop)

[Download](https://cdn.instructables.com/ORIG/FY1/H8L9/IUSM8XWS/FY1H8L9IUSM8XWS.desktop)

  * ![imageFileServer.desktop](/intl_static/img/pixel.png)[imageFileServer.desktop](https://cdn.instructables.com/ORIG/F8P/5ZXQ/IUSM8XY7/F8P5ZXQIUSM8XY7.desktop)

[Download](https://cdn.instructables.com/ORIG/F8P/5ZXQ/IUSM8XY7/F8P5ZXQIUSM8XY7.desktop)

  * ![pircameraNodeRED.desktop](/intl_static/img/pixel.png)[pircameraNodeRED.desktop](https://cdn.instructables.com/ORIG/FKT/LKJJ/IUSM8XYW/FKTLKJJIUSM8XYW.desktop)

[Download](https://cdn.instructables.com/ORIG/FKT/LKJJ/IUSM8XYW/FKTLKJJIUSM8XYW.desktop)

  * ![tightvnc.desktop](/intl_static/img/pixel.png)[tightvnc.desktop](https://cdn.instructables.com/ORIG/F79/CE41/IUSM8XYZ/F79CE41IUSM8XYZ.desktop)

[Download](https://cdn.instructables.com/ORIG/F79/CE41/IUSM8XYZ/F79CE41IUSM8XYZ.desktop)

## Step 13: List of References

  * [A developer's guide to the Internet of Things (IoT) by IBM](https://www.coursera.org/learn/developer-iot/)
  * [How to use IBM Bluemix Platform (Docs)](https://console.ng.bluemix.net/docs/)
  * [MQTT.org: Version 3.1.1 becomes an OASIS Standard](https://www.oasis-open.org/news/announcements/mqtt-version-3-1-1-becomes-an-oasis-standard)
  * [MQTT.org: Documentation](http://mqtt.org/documentation)
  * [Eclipse Paho ](http://www.eclipse.org/paho/)
  * [What is Really Small Message Broker(RSMB)? (IBM)](https://www.ibm.com/developerworks/community/groups/service/html/communityview?communityUuid=d5bedadd-e46f-4c97-af89-22d65ffee070)
  * <http://stanford-clark.com/>
  * [The House That Twitters - Andy Stanford-Clark](http://www.slideshare.net/andysc/the-house-that-twitters)
  * [Node-RED.org: Documentation](http://nodered.org/docs/)
  * [Node-RED: Running on Raspberry Pi](http://nodered.org/docs/hardware/raspberrypi)
  * [Node-RED: Writing Functions](http://nodered.org/docs/writing-functions)
  * [Node-RED: Node-RED Library](https://flows.nodered.org/)
  * [Node-RED: node-red-node-watson](http://flows.nodered.org/node/node-red-node-watson)
  * [Node-RED: Build a face detection app using Watson Visual Recognition v3 service](https://flows.nodered.org/flow/180ef549ecf4ea876c56298668c67fe8)
  * [Node-RED: Build a face detection app usig AlchemyAPI service on Bluemix](https://flows.nodered.org/flow/1af9a0c7fb970dc5e0d7)
  * [Recipes: Internet of Things (IoT) by IBM](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/)
  * [Twilio: Documentation](https://www.twilio.com/docs/)
  * [Raspberrpi.org: Installing oprerating system images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)
  * [Raspberrypi.org: downloads](https://www.raspberrypi.org/downloads/)
  * [IBM developerWorks Recipes: RPi Cam Image Analysis using Visual Recognition method](https://developer.ibm.com/recipes/tutorials/rpi-cam-image-analysis-using-visual-recognition-method/)
  * [IBM Watson: Text to Speech service](https://www.ibm.com/watson/developercloud/doc/text-to-speech/)
  * [IBM Watson: Visual Recognition service](http://www.ibm.com/watson/developercloud/doc/visual-recognition/)
  * [OpenCV: Documentation](http://opencv.org/documentation.html)
