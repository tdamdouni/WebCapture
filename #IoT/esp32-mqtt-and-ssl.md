# ESP32 (28) – MQTT and SSL

_Captured: 2017-12-04 at 13:32 from [www.lucadentella.it](http://www.lucadentella.it/en/2017/12/04/esp32-28-mqtt-e-ssl/)_

Security is a very important aspect for MQTT _brokers_. In [a previous article](http://www.lucadentella.it/en/2016/11/14/mqtt-sicurezza/) you've already learned how to implement **authentication** and **authorization_. _**The weakness in that configuration was that credentials were **transmitted in cleartext**; it was therefore possible, for an attacker who can _sniff_ the network traffic, to read and use them to impersonate a legitimate client.

Today I'll show you how to **encrypt** the communication channel between client and broker using SSL certificates. I'll also explain how to write a program for the **esp32** chip to send data to the broker using the secure channel…

#### SSL certificate

To be able to encrypt the communication, mosquitto requires a **server** certificate.

First generate the private key (RSA with a length at least 2048 bits):
    
    
    openssl genrsa -out mosquitto.key 2048

Then create the **CSR** file:
    
    
    openssl req -new -out mosquitto.csr -key mosquitto.key

type the required information; the most important of which is the **common name** that will identify the server:

![mq-ssl-001](http://www.lucadentella.it/blog/wp-content/uploads/2017/10/mq-ssl-001.jpg)

Now sign the CSR file with [your Certificate Authority](http://www.lucadentella.it/2017/10/26/una-certificate-authority-con-openssl/) (or send it to a public / corporate CA) to generate the certificate:
    
    
    openssl ca -config openssl.cnf -extensions server_cert 
     -notext -in mosquitto.csr -out mosquitto.cer

![mq-ssl-002](http://www.lucadentella.it/blog/wp-content/uploads/2017/10/mq-ssl-002.jpg)

> _Create the ssl subfolder in the folder where you installed mosquitto and copy into that folder the certificate, its private key and the certificate of the CA:_

![mq-ssl-003](http://www.lucadentella.it/blog/wp-content/uploads/2017/10/mq-ssl-003.jpg)

> _Configuration_

Open the **mosquitto.conf** file and add the following lines:

![mq-ssl-004](http://www.lucadentella.it/blog/wp-content/uploads/2017/10/mq-ssl-004.jpg)

The first line changes the TCP port mosquitto is normally listening to (1883) to the _default_ port for SSL connection, **8883**.

The following 3 lines set the path for server and CA certificates and for the private key that corresponds to the server certificate. The last one, which is not compulsory, forces the use of the **TLS v1.2** protocol, the most secure one at the moment of writing.

Once the server has been configured, you can start it (-v is to enable the **verbose** output):
    
    
    mosquitto.exe -c mosquitto.conf -v

To be able to use the mosquitto_pub and mosquitto_sub tools, you now have to add new parameters:
    
    
    mosquitto_sub.exe -p 8883 -t test --cafile .\ssl\ca.cer --insecure
    mosquitto_pub.exe -p 8883 -m 20 -t test --cafile .\ssl\ca.cer --insecure

With **-p** you specify the TCP port of the server, with **-cafile** the path of the CA certificate which signed the server certificate mosquitto uses and finally with **-insecure** you configure the two clients not to verify that the certificate's _common name_ (in my example mymosquitto.local) corresponds to the server name.

You can avoid using the **-insecure** switch if you generate a certificate with a _common name_ the exact name of the server/PC which runs mosquitto or - alternatively - if you add a _DNS alias_ which resolves the _common name _of your certificate with the IP address of the server and run the clients with **-h _commonName_**

#### esp32

[Tuan PM](http://tuanpm.net/) developed a library ([espmqtt](https://github.com/tuanpmt/espmqtt)) for the esp-idf _framework_ that implements a complete MQTT client. Moreover, the library does support **secure connections**, you can therefore use it to connect to an MQTT broker with TLS enabled.

![mq-ssl-005](http://www.lucadentella.it/blog/wp-content/uploads/2017/10/mq-ssl-005.jpg)

Copy the content of the Github repository in the **components** folder of your project and include the library's _header_ file in your source code:
    
    
    #include "mqtt.h"

The MQTT client is configured using the **mqtt_settings **struct:

![mqtt-001](http://www.lucadentella.it/blog/wp-content/uploads/2017/11/mqtt-001.jpg)

> _The most important parameters are:_

  * the server (**host**) that runs the MQTT broker (you can use the IP address or the _DNS name_)
  * the TCP port (**port**) the server is listening to (_default _is 1883 or 8883 if SSL is enabled)
  * **username** and **password** if the server requires authentication
  * one or more _callback_ functions the espmqtt library will call when the corresponding event occurs

the espmqtt library **does not copy** the parameters in an internal struct. It's therefore very important that the mqtt_settings variable has a **global** scope and it's defined outside a specific function.

Your program can interact with the MQTT client implementing its _callback_functions.

For example the connection or disconnection from the MQTT server occurs as follows:

![mqtt-002](http://www.lucadentella.it/blog/wp-content/uploads/2017/11/mqtt-002.jpg)

The **connect_cb** and **disconnect_cb** functions perform the "real" connection and disconnection, while **connected_cb** and **disconnected_cb** functions are executed after the corresponding activity is completed (= the client successfully connected to the server). Your program usually doesn't need to re-implement the main functions, but will implement the ones related to events, to execute actions (for example **subscribe** a topic) when a specific event occurs.

After having configured the client, you can run it with:
    
    
    mqtt_start(&settings);

Once connected to the server (_connected_cb _callback function) you can subscribe or unsubscribe a topic with:
    
    
    void mqtt_subscribe(mqtt_client *client, const char *topic, uint8_t qos);
    void mqtt_unsubscribe(mqtt_client *client, const char *topic);

and publish data to a topic with:
    
    
    void mqtt_publish(mqtt_client* client, const char *topic, 
      const char *data, int len, int qos, int retain);

#### Demo

I prepared an example to show my esp32 devboard sending data to a mosquitto server, with SSL enabled.

I connected to the devboard an HTU21D sensor as explained in a [previous article](http://www.lucadentella.it/en/2017/10/13/esp32-24-i2c-un-esempio-pratico-con-sensore-htu21d/) and my program reads, every 5 seconds, the temperature and humidity values and sends them to the broker. I used a very handy opensource program, [HelloIoT](https://github.com/adrianromero/helloiot), to create a dashboard and display the received data.

The source code of the program and the configuration of the HelloIoT dashboard are available in my [Github repository](https://github.com/lucadentella/esp32-tutorial); here's a short video of the demo:
