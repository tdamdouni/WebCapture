# Demo 33: Monitor and control ESP32 via IBM Bluemix Watson IoT Platform

_Captured: 2017-10-09 at 21:06 from [www.iotsharing.com](http://www.iotsharing.com/2017/10/monitor-and-control-esp32-via-ibm-bluemix-watson-iot-platform.html?m=1)_

**1\. Introduction**  
In this demo, I will show you how to monitor and control ESP32 via IBM Bluemix Watson IoT Platform.  
IBM Bluemix is a cloud platform that supports many products and services such as: Compute Infrastructure, Compute Services, Storage, Mobile, Wason, Application services, Data and analytics, Internet of Things, ...  
In this demo, we just focus on Internet of Things service of Bluemix.  
In order to use Bluemix, you need to register an account. I registered a free account and it is available in 30 trial days.  
You can sign up [here](https://console.ng.bluemix.net/registration/). It is easy just follow the steps in registration form.  
**2\. Hardware**  
You need a LED or relay as in [Demo 1: Blinky](http://www.iotsharing.com/2017/05/blinky-hello-world-on-arduino-esp32.html)  
**3\. Bluemix setup steps and ESP32 software**  
Here is the Menu of Bluemix services. It is in top-left corner.

![](https://2.bp.blogspot.com/-oEBvAZ1w9iE/WdmmsHo3hYI/AAAAAAAAEUI/qlKlngO6TCIrpXbBSw5cIkL7SDt6TIRUwCLcBGAs/s640/bluemix8.png)

But before using IoT service we need to create a **Space** (where you deploy your IoT application) for it. It is under **Manage - Account - Organizations** tabs.

![](https://1.bp.blogspot.com/-beGfqWD1GEw/Wdms54YPWsI/AAAAAAAAEUY/2eVXjlYtkjAZyfoDE3MaJrWTRyKZ0BZewCLcBGAs/s640/bluemix9.png)

![](https://2.bp.blogspot.com/-KaSiBAUUh1w/Wdmt065J4YI/AAAAAAAAEUk/gQdgfTWb1Lk3ajOgIdQg8UO10KPUpD6PQCLcBGAs/s1600/bluemix11.png)

![](https://2.bp.blogspot.com/-tQ_qUSTfqEI/WdmtdIc7iTI/AAAAAAAAEUg/cdUaauiADrg_irxEvoNfa_0ZMOT-GQDcwCLcBGAs/s640/bluemix10.png)

> _From Menu choose IoT service_

![](https://2.bp.blogspot.com/-KaSiBAUUh1w/Wdmt065J4YI/AAAAAAAAEUk/Ruwm7YIw_yoO-qXpEzAW85EKka08J39CwCEwYBhgL/s640/bluemix11.png)

> _Choose Create IoT Service and Internet of Thins Platform_

![](https://1.bp.blogspot.com/-lgLPlfyvZ34/WdmunBXasAI/AAAAAAAAEUs/eqgSLOCWIJ0lU3NGKKrZpva2JDkEZsmvQCLcBGAs/s640/bluemix12.png)

![](https://1.bp.blogspot.com/-afkeDbZGhQ4/Wdmu7WPvEXI/AAAAAAAAEUw/XcW4BQixChQtKCAS76FNABUvVRNrBjbhwCLcBGAs/s640/bluemix13.png)

> _Edit fields as your expectation and choose Create ... Done_

![](https://2.bp.blogspot.com/-NYsgU6dM0W0/WdmvWbSQxdI/AAAAAAAAEU0/yl25gxIxq1M1aGQrFv3tuRoYlIKnAgtUQCLcBGAs/s640/bluemix14.png)

> _Choose IoT service which you created and choose Launch_

**![](https://4.bp.blogspot.com/-WxwJmBI2OoQ/WdmwfqAhGJI/AAAAAAAAEVA/5OWQ162ovfAikwKtRQuhvnmvtpLi8Jd4wCLcBGAs/s640/bluemix15.png)**

Now you see IBM Watson IoT Platform dashboard with Menu

![](https://4.bp.blogspot.com/-e1d1oy-Z2gY/WdnFFqmnXEI/AAAAAAAAEVQ/3XhVMpzn4hAmCUSmY7hdFDFlSAbcBqKxwCLcBGAs/s640/bluemix16.png)

> _Choose Devices and Add Device_

![](https://3.bp.blogspot.com/-5ZXBFW3xuPk/WdnFeFPaofI/AAAAAAAAEVU/qqsavP4rnakvmp0fm2jDHnZYvMC6cq6mwCLcBGAs/s640/bluemix17.png)

![](https://1.bp.blogspot.com/-l-wi0fSVANU/WdnGTBkw0eI/AAAAAAAAEVc/2UV_J6L3Wl8CEbG3CJWUF3PdVdLejbDhwCLcBGAs/s640/bluemix3.png)

![](https://3.bp.blogspot.com/-u-ydVDMKd34/WdnGeErDnCI/AAAAAAAAEVk/HP8MTRaB6G04kHuu2V37THQfViel26dtgCLcBGAs/s640/bluemex3.png)

![](https://1.bp.blogspot.com/-2S34TXbLh8w/WdnGYmZ-fgI/AAAAAAAAEVg/8ufgGruHmWQBEwXlSCZEtLy6dh1egKsfACEwYBhgL/s640/bluemix4.png)

> _Here you can fill it with expected information or leave them empty (modify them later)._

![](https://4.bp.blogspot.com/-xqblLdeNxN0/WdnJlVY3zdI/AAAAAAAAEVw/YBxHrfCqr0k9pex9RdBymovvtf-IO_2rQCLcBGAs/s640/bluemix5.png)

![](https://1.bp.blogspot.com/-qheEg30Vww4/WdnJzP1RSVI/AAAAAAAAEV4/8K6Jbc-A2EsXWW3xNU8N1wxtKUeX7cYxQCLcBGAs/s640/bluemix6.png)

> _Here, Device ID is MAC address of ESP32. You can use the code below to get MAC address:_

And let authentication token is Auto-generated. Finally, you have:

![](https://1.bp.blogspot.com/-Sqnf6ZdUSKQ/WdnJta6L1bI/AAAAAAAAEV8/0IBuYRPOQ1oI-c2Ry44uXrvJdb-JGDD2wCEwYBhgL/s640/bluemix7.png)

Remember to save this information for future usage.  
**Note: ** **TLS with Token Authentication** is enabled by default. So if your device use TLS you can ignore it. In my demo using ESP32, I do not use TLS so I have to disable it to avoid Authentication error. In order to disable it just chose **Security** from Menu.

![](https://4.bp.blogspot.com/-e1d1oy-Z2gY/WdnFFqmnXEI/AAAAAAAAEVY/5wtTMAr_cYwSsgeBLjUbaPYefCbPEkpbACEwYBhgL/s640/bluemix16.png)

Choose **Connection Security **and then**TLS Optional**.

![](https://2.bp.blogspot.com/-e8yXyMMu5vE/WdnOd8ULXVI/AAAAAAAAEWE/sVcTA9HmAVMe3S4qzA4htde8SUBaxWAqACLcBGAs/s640/bluemix18.png)

Now choose Devices from Menu, you will see a list of devices with Disconnected sign. It is time to connect our devices first time.

![](https://2.bp.blogspot.com/-LUQvvcadxXY/WdnPFJul0BI/AAAAAAAAEWM/dfWUo7bLQ_o_rsWGhGP1uWsUeZd2sKowACLcBGAs/s640/bluemix19.png)

In order to connect to IBM Watson™ IoT Platform, we will use MQTT protocol ([Demo 14](http://www.iotsharing.com/2017/05/how-to-use-mqtt-to-build-smart-home-arduino-esp32.html)). You can refer [document](https://console.bluemix.net/docs/services/IoT/iotplatform_task.html#iotplatform_task) to understand the procedure to connect to it. The Arduino ESP32 code will do the jobs:  
\- Connect to cloud.  
\- Publish a temperature message (generated by using random function). If you have DHT11/DHT22 you can use [Demo 3](http://www.iotsharing.com/2017/05/how-to-arduino-esp32-dht11-dht22-temperature-humidity-sensor.html).  
\- Subscribe the ON/OFF message to control LED.  
**4\. How to monitor and control ESP32**  
We went through steps to setup Bluemix IoT Platform and ESP32. Now we will learn how to develop or setup applications to monitor and control ESP32 Iot device. There are some ways to do that. In this demo, I will use 2 ways: Node-Red (you can refer [Demo 8](http://www.iotsharing.com/2017/05/tcp-udp-ip-with-esp32.html) to know more about Node-RED) and own developed Python application.  
**4.1 Node-Red**  
We will use Bluemix Node-RED Starter.  
From Menu choose **Clound Foundry Apps **and then** Create ******Clound Foundry apps****. From **Filter** box search**** "Node-RED Starter"****.Choose ********"Node-RED Starter"******** and fill expactation information.

**![](https://1.bp.blogspot.com/-NYsgU6dM0W0/WdmvWbSQxdI/AAAAAAAAEU4/d3LLbKNsE7gY1siSwic3apm_LX7x1ilSwCPcBGAYYCw/s640/bluemix14.png)**

Click **Create**

![](https://4.bp.blogspot.com/-kA6QHRV-jL4/WdrttZ3JpHI/AAAAAAAAEWg/F5vSGfHiS7osWFlouSeSnyaM22f9OLGOQCEwYBhgL/s640/bluemix.png)

Waiting until service was deployed ...

![](https://2.bp.blogspot.com/-loDRDHOntSw/WduDccXXU3I/AAAAAAAAEYA/_iO1NHMKqW4fsz6kILB62_I2VYlUtS2_wCLcBGAs/s640/bluemix20.png)

> _Figure: Node-RED service was deployed successfully_

Next, from Menu choose **Dashboard **and you can see "Node-RED" is running. And you can access Node-RED flow editor online by going to the link in **Route **column (it is "[iotsharing.mybluemix.net](https://iotsharing.mybluemix.net/)")

![](https://4.bp.blogspot.com/-5fLFYisQ-D4/WdrvTP2eprI/AAAAAAAAEWo/xQ11acBqzckntSsWpJC7S8xP_nNerBjtACLcBGAs/s640/bluemix1.png)

Now, we need to bind our Node-RED starter with our created Bluemix IoT Platform service. From dashboard and Cloud Foundry Apps table, click the Node-RED row (picture above).

![](https://2.bp.blogspot.com/-suZui3ZKb38/Wdrx1-JpJJI/AAAAAAAAEW4/6cBmfp7WBuAuLs6OSszgN1Fw1IIWWYkuQCLcBGAs/s640/bluemix2.png)

Choose **Connect existing **and choose the Bluemix IoT Platform service which we created in **Section 3 Bluemix setup steps and ESP32 software **(the result is similar to picture above).

![](https://3.bp.blogspot.com/-TmpcLDWaEe0/WduDIxQG2WI/AAAAAAAAEX8/W4dBHhja0Twk_JwopL--ng2G7VRV0iocwCLcBGAs/s640/bluemix21.png)

> _Figure: Bind Node-RED with Bluemix IoT Platform_

**4.1.1 Let 's play with Node-RED **  
We go to the link in **Route **column ("[iotsharing.mybluemix.net](https://iotsharing.mybluemix.net/)").

![](https://3.bp.blogspot.com/-p30BvHOfxQE/WdrzsisQhYI/AAAAAAAAEXE/BNyrgQOi3OoVLtwNV3oBHOGWHb3ZXgKYgCLcBGAs/s640/bluemix3.png)

And choose **Go to your Node-RED flow editor **(you may need to wait a little time to initialize Node-RED flow editor if you see 404 error).  
Finally, it is done.

![](https://3.bp.blogspot.com/-zOMKmV-bfek/Wdr0Ukq4EQI/AAAAAAAAEXM/XSldkINbp-s0mg2n30vd2ZpLSixjUp85gCLcBGAs/s640/bluemix4.png)

Node-RED Starter supports 2 nodes named IBM IoT in/out to connect to Bluemix IoT Platform easily. I created the flow as picture above and Export that flow to JSON format. So you just Import the JSON content into your Flow and change Device Information accordingly to the device which you created in **Section 3 Bluemix setup steps and ESP32 software**. In my Flow there are 2 blocks: 1 subscribe block (upper block; using IBM IoT in) to subscribe the event from ESP32 IoT device and bring to Debug block through Debug tab (Top-Right corner); 1 publish block (lower block; using IBM IoT out) to publish command ON/OFF LED to ESP32 IoT device.

![](https://1.bp.blogspot.com/-VqZf9pOsm0U/Wdr5qFEFaPI/AAAAAAAAEXc/1Cftxo-6Jj0Mby40QlK-bUiYyVx2szMhgCLcBGAs/s640/bluemix5.png)

![](https://1.bp.blogspot.com/-aGsXTcbc67k/Wdr54Hq32RI/AAAAAAAAEXg/napSzmMmbAwyRfbhKmti6Rvrl63PmA0BgCLcBGAs/s640/bluemix6.png)

> _Figure: Import JSON content to Flow_

![](https://4.bp.blogspot.com/-SJIsyTQ6nUc/Wdr66PFCN0I/AAAAAAAAEXs/r9GpyAmJhvYLyUkF3DoAkKNOGLqXMK2cQCLcBGAs/s640/bluemix7.png)

> _Figure: Change Device Type and Device Id to yours_

**![](https://3.bp.blogspot.com/-dU10yaturHc/WduE7eAy1rI/AAAAAAAAEYM/Z3hSMv4pk2UGl__2AcnVsrrGCfZNxArvgCLcBGAs/s640/bluemix22.png)**

![](https://3.bp.blogspot.com/-e1d1oy-Z2gY/WdnFFqmnXEI/AAAAAAAAEVY/lUm2n_G5RZU_ulgP1tlffo1ThO6nCWguwCPcBGAYYCw/s640/bluemix16.png)

![](https://2.bp.blogspot.com/-aUBOGmQ3Cpc/WduKu41TdjI/AAAAAAAAEYg/7u5EmYTBiiYms8fAhdKrClHo8gRKKU9ngCLcBGAs/s640/bluemix25.png)

> _Remember to save this information for future usage._

**4.2.2 Result**

![](https://4.bp.blogspot.com/-8QNXzUKDCSU/WduMD2aOZeI/AAAAAAAAEY0/tdqEsUoS9Y4uCsHRRzZxAAsCyABen8iWACLcBGAs/s640/bluemix26.png)

> _Figure: developed app subscribe temperature event from ESP32 IoT device_
