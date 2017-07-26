# IoT Testing for the BLE Protocol

_Captured: 2017-05-04 at 11:13 from [dzone.com](https://dzone.com/articles/iot-testing-for-the-ble-protocol)_

In this article, I would like to focus on BLE (Bluetooth Low Energy) devices. The BLE protocol is based on Bluetooth v.4.0. With low power consumption, devices can run on a small battery for five years.

The healthcare and lifestyle market is very advanced in regard to IoT apps. BLE sensors can measure any parameters from any person, showing the data directly on a mobile device, which also analyzes the data and suggests the different actions that need to be taken based on said data.

The application types vary from heartbeat data during sporting activities to the glucose level in diabetes patients. This IoT solution certainly encourages people to play more sports, but it can also improve the quality of life of diabetes patients.

The following figure shows the data flows between an IoT device connected to a person via a mobile app to the backend server.

![IoT Testing for BLE Protocol ](http://blog.perfectomobile.com/wp-content/uploads/2017/04/IOTTestingforBLEProtocol-2.png)

The medical data is collected by the IoT device and sent via BLE to the mobile app. The app aggregates the data and sends it to the server -- and also can control the BLE device by sending BLE requests. The doctors can query their patients' data remotely - almost in real time - and get notifications of critical situations.

### **BLE Protocol**

The BLE protocol is based on GATT **(Generic Attributes)** and defines the way that two Bluetooth Low Energy devices transfer data using the concepts of **Services** and **Characteristics**.

The data is stored in a simple lookup table with an id for each entry. The protocol defines the READ, WRITE, and NOTIFY actions for these entries.

The protocol defines generic characteristics but also allows us to define private characteristics, which require specific code in the BLE device and the monitor app.

### **BLE Pairing**

Like standard Bluetooth protocol, BLE requires pairing. But in this case, it is done automatically.

The BLE device broadcasts its service, and the device that receives the broadcast can ask to connect.

Generic devices accept the connection, whereas other devices will not accept the connection without an authentication handshake mechanism, based on setting predefined private characteristics with a unique key.

After pairing, the devices can exchange data based on the characteristics and the allowed actions using the UUID of the table entries.

### **Data Flows Over BLE Protocol**

The data flow is based on the actions and the characteristics values. For example, here are the heartbeat devices and mobile device data flow (after pairing):

![BLE Protocol](http://blog.perfectomobile.com/wp-content/uploads/2017/04/BLEprotocol.jpg)

## IoT Testing BLE Challenges

There are a large number of challenges to developing and testing IoT mobile applications:

  * Most of the tests have to be done manually and require some form of connection between the IoT device and a real person.
  * The IoT and mobile devices should be in the same location, with a manual interaction to connect between them.
  * It takes more time to develop the IoT HW device, and you cannot parallel the application (SW) and the IoT device's development and testing.
  * The testers cannot control the data sent from the IoT device to the mobile app and set any predefined validation.
  * Health devices and applications require FDA approval. That means large numbers of proven tests on a large number of devices.
  * In the case of offshore testing, it is always a challenge to send and manage the devices at remote sites.

Let's take an example of a heartbeat device connected to a finger and send the heartbeat to a mobile app.

The app/device tests required:

  * Person/tester (With heartbeat and finger, preferably) 
  * Mobile devices
  * IoT device
![IoT Testing For a Heartbeat Device](http://blog.perfectomobile.com/wp-content/uploads/2017/04/IOTTestingforaheartbeatdevice-252x300.png)

This process cannot be automated - it cannot be scaled.

## IoT Testing for BLE

Our solution goals are to:

  * Automate the test process.
  * Access all the mobile devices in the cloud.

The solution is a SW visualization of BLE devices in the cloud.

It allows the user to define and update the characteristics and the services. The services support APIs and are controlled by automation scripts.

At Perfecto, we selected this solution for the following reasons:

  * It is fully controlled by SW - key for automation.
  * It is located in the cloud near the devices.
  * It acknowledges generic characteristics and can be virtually any device
  * Multiple threads
  * Works on real RF channels
  * Allows data to be set by the tester
  * Connects to any automation framework.

### **How Does It Work?**

A new BLE server is added to the lab. This machine contains up to 20 BLE dongles. For each dongle, the machine can set a virtual BLE device. The automation server controls both the IoT and mobile devices and allows us to develop a full scenario in an automation script.

![IoT Testing for BLE Protocol](http://blog.perfectomobile.com/wp-content/uploads/2017/04/IOTTestingforBLEProtocol-300x292.png)

Each BLE service is configured by an external JSON file. The file defines the services. Based on the JSON file, a new visual BLE service started and exposes **BLE** data.

![IoT Testing for BLE Protocol](http://blog.perfectomobile.com/wp-content/uploads/2017/04/IOTTestingforBLEProtocol-1.png)

The mobile device receives the data over the RF channel (standard BLE HW on a phone), and it works like it arrived from real BLE devices.

The last part of the solution is the commands, which are added to the automation system and allow us to start, stop, and change BLE servers and data from the script.

This solution allows the execution of unattended automation from the CI and to test BLE mobile apps.

## **Summary**

BLE devices are one part of the wide topic named IoT. In this article, I described the BLE protocol and the communication layer of the BLE.

I showed how Perfecto virtualization tools overcome the development and testing challenges. In the next article, I will focus on **Amazon Alexa** and **Google Home**. I will describe the **Alexa skills** development and automation processes.

### Like This Article? Read More From DZone
